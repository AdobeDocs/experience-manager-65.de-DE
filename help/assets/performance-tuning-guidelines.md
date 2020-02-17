---
title: Handbuch zur Leistungsoptimierung von Assets
description: Vorschläge und Anleitungen zur AEM-Konfiguration, Änderungen an Hardware, Software und Netzwerkkomponenten, um Engpässe zu beseitigen und die Leistung von AEM Assets zu optimieren.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


<!-- TBD: Formatting using backticks. Add UICONTROL tag. Redundant info as reviewed by engineering. -->

# Assets performance tuning guide {#assets-performance-tuning-guide}

Ein Adobe Experience Manager (AEM) Assets-Setup enthält eine Reihe von Hardware-, Software- und Netzwerkkomponenten. Je nach Ihrem Bereitstellungsszenario benötigen Sie möglicherweise bestimmte Konfigurationsänderungen an den Hardware-, Software- und Netzwerkkomponenten, um Leistungsengpässe zu vermeiden.

Wenn Sie sich darüber hinaus an bestimmte Richtlinien zur Optimierung der Hardware und Software halten, schaffen Sie eine solide Grundlage für Ihre AEM Assets-Bereitstellung, mit der Sie alle Anforderungen an Leistung, Skalierbarkeit und Zuverlässigkeit erfüllen.

Eine schwache Leistung von AEM Assets kann sich auf die Benutzerfreundlichkeit auswirken und die interaktive Leistung, Asset-Verarbeitung und Download-Geschwindigkeit und andere Bereiche beeinträchtigen.

Die Leistungsoptimierung ist eine grundlegende Aufgabe, die Sie ausführen, bevor Sie Zielmetriken für ein Projekt festlegen.

In den folgenden Schlüsselbereichen sollten Sie besonders darauf achten, dass Leistungsprobleme erkannt und behoben werden, bevor sie sich auf die Benutzererfahrung auswirken.

## Plattform {#platform}

Obwohl AEM auf einer Reihe von Plattformen unterstützt wird, hat Adobe die größte Unterstützung für native Werkzeuge unter Linux und Windows gefunden, was zu einer optimalen Leistung und einfachen Implementierung beiträgt. Ein 64-Bit-Betriebssystem ist ideal für die hohen Speicheranforderungen einer AEM Asset-Bereitstellung. Wie bei jeder AEM-Bereitstellung sollten Sie nach Möglichkeit TarMK implementieren. TarMK kann zwar nicht über eine einzelne Autoreninstanz skaliert werden, erzielt jedoch erfahrungsgemäß eine bessere Leistung als MongoMK. Sie können TarMK-Offload-Instanzen hinzufügen, um die Leistung der Workflow-Verarbeitung Ihrer AEM Assets-Bereitstellung zu erhöhen.

### Temporärer Ordner {#temp-folder}

Um die Upload-Zeit für Assets zu verbessern, verwenden Sie Hochleistungs-Speicher für den temporären Java-Ordner. Unter Linux und Windows können Sie beispielsweise ein RAM- oder SSD-Laufwerk verwenden. In Cloud-basierten Umgebungen kann ein äquivalenter Hochgeschwindigkeitsspeicher verwendet werden. For example in Amazon EC2, an [&#39;ephemeral drive&#39;](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) drive can be used for the temporary folder.

Bei einer großen Speicherkapazität des Servers kann ein RAM-Laufwerk konfiguriert werden. Führen Sie unter Linux die folgenden Befehle aus, um ein RAM-Laufwerk von 8 GB zu erstellen:

```
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Unter Windows OS verwenden Sie einen Treiber eines Drittanbieters, um ein RAM-Laufwerk zu erstellen, oder verwenden Sie einfach Hochleistungs-Speicher wie SSD.

Once the high performance temporary volume is ready, set the JVM parameter `-Djava.io.tmpdir`. For example, you could add the JVM parameter below to the `CQ_JVM_OPTS` variable in the `bin/start` script of AEM:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-Konfiguration {#java-configuration}

### Java-Version {#java-version}

Adobe empfiehlt die Bereitstellung von AEM Assets auf Java 8, um eine optimale Leistung zu erzielen.

>[!NOTE]
>
>Oracle hat die Veröffentlichung von Updates für Java 7 ab April 2015 eingestellt.

### JVM-Parameter {#jvm-parameters}

Legen Sie die folgenden JVM-Parameter fest:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Datenspeicher- und Arbeitsspeicherkonfiguration {#data-store-and-memory-configuration}

### Dateidatenspeicherkonfiguration {#file-data-store-configuration}

Allen Benutzern von AEM Assets wird angeraten, Datenspeicher und Segmentspeicher zu trennen. Außerdem kann die Leistung durch die Konfiguration der Parameter `maxCachedBinarySize` und `cacheSizeInMB` maximiert werden. Set `maxCachedBinarySize` to the smallest file size that can be held in the cache. Specify the size of the in-memory cache to use for the datastore within `cacheSizeInMB`. Adobe empfiehlt, diesen Wert auf 2–10 Prozent der gesamten Heap-Größe einzustellen. Mithilfe von Last-/Leistungstests lässt sich die ideale Einstellung herausfinden.

### Konfigurieren der Maximalgröße des gepufferten Bildercaches {#configure-the-maximum-size-of-the-buffered-image-cache}

Wenn Sie große Mengen von Assets in Adobe Experience Manager hochladen, verringern Sie die konfigurierte maximale Größe des gepufferten Bild-Cache, um unerwartete Spitzen im Arbeitsspeicherverbrauch zu ermöglichen und JVM-Fehler mit OutOfMemory-Fehlern zu verhindern. Consider an example that you have a system with a maximum heap (- `Xmx`param) of 5 GB, an Oak BlobCache set at 1 GB, and document cache set at 2 GB. In diesem Fall würde der gepufferte Cache das Maximum von 1,25 GB Speicher in Anspruch nehmen, wodurch nur 0,75 GB Speicher für unerwartete Spitzen verblieben.

Konfigurieren Sie die Größe des gepufferten Cache in der OSGi-Webkonsole. Legen Sie `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`die Eigenschaft `cq.dam.image.cache.max.memory` in Byte fest. 1073741824 entspricht beispielsweise 1 GB (1024 x 1024 x 1024 = 1 GB).

Wenn Sie über AEM 6.1 SP1 einen `sling:osgiConfig`-Knoten zur Konfiguration dieser Eigenschaft verwenden, stellen Sie sicher, dass Sie diesen Datentyp auf „Long“ einstellen. Weitere Details finden Sie unter [CQBufferedImageCache belegt beim Asset-Upload den Heap](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Gemeinsame Datenspeicher {#shared-data-stores}

Mit der Implementierung eines S3 oder Shared File Datastore sparen Sie Speicherplatz auf der Festplatte und erhöhen den Netzwerkdurchsatz in großen Implementierungen. For more information on the pros and cons of using a shared datastore, see [Assets Sizing Guide](/help/assets/assets-sizing-guide.md).

### S3-Datenspeicher {#s-data-store}

Mit der folgenden Konfiguration des S-Datenspeichers (`org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`3) konnte Adobe binäre große Objekte (BLOBs) mit einer Größe von 12,8 TB von einem vorhandenen Dateidatenspeicher in einen S3-Datenspeicher am Standort eines Kunden extrahieren:

```
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Netzwerkoptimierung {#network-optimization}

Adobe empfiehlt die Aktivierung von HTTPS, da viele Unternehmen über Firewalls verfügen, die den HTTP-Verkehr überprüfen und sich dadurch negativ auf Uploads auswirken und Dateien beschädigen. Stellen Sie bei großen Datei-Uploads sicher, dass Benutzer über eine Kabelverbindung zum Netzwerk verfügen, da ein WiFi-Netzwerk schnell gesättigt wird. For guidelines on identifying network bottlenecks, see [Assets Sizing Guide](/help/assets/assets-sizing-guide.md). To assess network performance by analyzing network topology, see [Assets Network Considerations](/help/assets/assets-network-considerations.md).

Welche Strategie der Netzwerkoptimierung Sie verwenden, hängt in erster Linie von der verfügbaren Bandbreite und der Last auf Ihrer AEM-Instanz ab. Allgemeine Konfigurationsoptionen, einschließlich Firewalls oder Proxys, können zur Verbesserung der Netzwerkleistung beitragen. Die folgenden Aspekte sollten berücksichtigt werden:

* Stellen Sie je nach Instanztyp (klein, mittel, groß) sicher, dass die Netzwerkbandbreite für Ihre AEM-Instanz ausreichend ist. Dies ist besonders wichtig, wenn AEM auf AWS gehostet wird.
* Wird Ihre AEM-Instanz auf AWS gehostet, können Sie von einer flexiblen Skalierung profitieren. Vergrößern Sie die Instanz, wenn Benutzer eine hohe Belastung erwarten. Verkleinern Sie die Instanz, wenn nur eine mäßige/geringe Belastung erwartet wird.
* HTTPS: Die meisten Benutzer verwenden Firewalls zur Überwachung des HTTP-Verkehrs. Sie können den Prozess des Hochladens beeinträchtigen oder Dateien beim Hochladen beschädigen.
* Upload großer Dateien: Die Benutzer benötigen Kabelverbindungen zum Netzwerk (WLAN-Verbindungen sind schnell gesättigt).

## Workflows {#workflows}

### Verlaufs-Workflows {#transient-workflows}

Stellen Sie den Workflow „DAM-Update-Asset“ nach Möglichkeit auf „Übergang“ ein. Die Einstellung trägt zu einer erheblichen Reduzierung des Overheads bei, der für die Verarbeitung der Workflows benötigt wird, da die Workflows in diesem Fall nicht die normalen Tracking- und Archivierungsprozesse durchlaufen.

>[!NOTE]
>
>Standardmäßig wird der Workflow DAM-Update-Asset in AEM 6.3 auf „Übergang“ eingestellt. In diesem Fall können Sie das folgende Verfahren überspringen.

1. Navigieren Sie zu `/miscadmin` in der AEM-Instanz unter `https://[aem_server]:[port]/miscadmin`.
1. Erweitern Sie **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL dam]**.
1. Open **[!UICONTROL DAM Update Asset]**. Wechseln Sie im unverankerten Tool-Fenster auf die Registerkarte **[!UICONTROL Seite]** und klicken Sie auf **[!UICONTROL Seiteneigenschaften]**.
1. Select **[!UICONTROL Transient Workflow]** and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Einige Funktionen unterstützen keine Verlaufs-Workflows. Wenn diese Funktionen in Ihrer AEM Asset-Bereitstellung benötigt werden, konfigurieren Sie keine Verlaufs-Workflows.

Wenn keine Verlaufs-Workflows verwendet werden können, führen Sie regelmäßig Workflow-Bereinigungen durch, um archivierte DAM-Update-Asset-Workflows zu löschen. So verhindern Sie eine Beeinträchtigung der Systemleistung.

Führen Sie die Bereinigungs-Workflows normalerweise wöchentlich aus. In ressourcenintensiven Szenarien, z. B. während der umfangreichen Asset-Erfassung, können Sie diese jedoch häufiger ausführen.

Um die Workflow-Bereinigung zu konfigurieren, fügen Sie in der OSGi-Konsole eine neue Adobe Granite-Workflow-Bereinigungskonfiguration hinzu. Konfigurieren und planen Sie im nächsten Schritt den Workflow als Teil des wöchentlichen Wartungsfensters.

Dauert die Bereinigung zu lange, kommt es zu einem Timeout. Daher sollten Sie sicherstellen, dass die Bereinigungsaufträge abgeschlossen sind. So vermeiden Sie, dass Bereinigungs-Workflows aufgrund der hohen Zahl an Workflows nicht abgeschlossen werden können.

For example, after executing numerous non-transient workflows (that creates workflow instance nodes), you can run [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) on an ad-hoc basis. Es entfernt redundante, abgeschlossene Workflow-Instanzen sofort, ohne dass Sie auf die Ausführung des Adobe Granite Workflow Purge Scheduler warten müssen.

### Maximal parallel ausführbare Aufträge {#maximum-parallel-jobs}

Standardmäßig kann AEM maximal so viele Aufträge parallel ausführen wie Prozessoren auf dem Server vorhanden sind. In Zeiten hoher Auslastung ist diese Einstellung jedoch problematisch, da alle Prozessoren von den DAM-Update-Asset-Workflows beansprucht werden und dadurch die Reaktionsfähigkeit der Benutzeroberfläche verlangsamt wird und AEM andere Prozesse zum Schutz von Serverleistung und -stabilität nicht ausführen kann. Es hat sich bewährt, diese Einstellung so zu wählen, dass nur die Hälfte der auf dem Server verfügbaren Prozessoren verwendet wird:

1. Wechseln Sie unter AEM Author zu `https://[aem_server]:[port]/system/console/slingevent`.
1. Click **[!UICONTROL Edit]** on each workflow queue that is relevant to your implementation, for example **[!UICONTROL Granite Transient Workflow Queue]**.
1. Update the value of **[!UICONTROL Maximum Parallel Jobs]** and click **[!UICONTROL Save]**.

Diese Einstellung des Werts auf die Hälfte der verfügbaren Prozesse ist für den Anfang eine praktikable Lösung. Unter Umständen müssen Sie diese Zahl jedoch nach oben oder unten anpassen, um den maximalen Durchsatz zu erreichen, und auch an die spezifische Umgebung anpassen. Es gibt separate Warteschlangen für Verlaufs- und Nicht-Verlaufs-Workflows sowie für andere Prozesse wie beispielsweise externe Workflows. Sind mehrere Warteschlangen, die auf 50 % der Prozessoren gesetzt sind, gleichzeitig aktiv, kann es schnell zu einer Überlastung des Systems kommen. Welche Warteschlangen stark ausgelastet sind, hängt in hohem Maße von den Benutzerimplementierungen ab. Sie müssen daher sorgfältig und mit Bedacht konfiguriert werden, um maximale Effizienz zu erreichen, die nicht zu Lasten der Serverstabilität geht.

### Konfiguration von DAM-Update-Asset {#dam-update-asset-configuration}

Der DAM-Update-Asset-Workflow enthält eine vollständige Suite an für Aufgaben konfigurierten Schritten, beispielsweise Scene7 PTIFF-Generierung und InDesign Server-Integration. Die meisten Benutzer benötigen jedoch nicht alle diese Schritte. Adobe empfiehlt die Erstellung einer benutzerdefinierten Kopie des DAM-Update-Asset-Workflow-Modells, in der alle unnötigen Schritte entfernt wurden. Aktualisieren Sie dann die Launcher für DAM-Update-Asset so, dass sie auf das neue Modell zeigen.

Wenn Sie den Workflow „DAM-Update-Asset“ häufig ausführen, kann hierdurch die Größe Ihres Dateidatenspeichers deutlich ansteigen. Entsprechende Tests von Adobe haben gezeigt, dass die Datenspeichergröße um ca. 400 GB ansteigt, wenn innerhalb von 8 Stunden 5.500 Workflows ausgeführt werden.

Hierbei handelt es sich um einen vorübergehenden Anstieg. Nach Ausführung der Aufgabe zur Speicherbereinigung weist der Datenspeicher wieder seine ursprüngliche Größe auf.

In der Regel wird die Speicherbereinigung wöchentlich gemeinsam mit anderen geplanten Wartungsaufgaben ausgeführt.

Wenn Sie nur über eingeschränkten Speicherplatz verfügen und den Workflow „DAM-Update-Asset“ häufig ausführen, sollten Sie die Speicherbereinigung öfter planen.

#### Ausgabegenerierung zur Laufzeit {#runtime-rendition-generation}

Kunden verwenden Bilder unterschiedlicher Größen und Formate auf ihrer Website oder zur Weiterleitung an die Geschäftspartner. Da jede Darstellung den Footprint der Assets im Repository vergrößert, empfiehlt Adobe die umsichtige Verwendung dieser Funktion. Um die Menge der Ressourcen zu reduzieren, die für die Verarbeitung und Speicherung von Bildern benötigt wird, können Sie die Bilder statt als Ausgabeformate bei der Erfassung auch zur Laufzeit generieren.

Viele Kunden der Website implementieren ein Bild-Servlet, das Bilder zum Zeitpunkt ihrer Anforderung skaliert und beschneidet und der Veröffentlichungsinstanz damit eine zusätzliche Belastung auferlegt. Wenn diese Bilder zwischengespeichert werden können, lässt sich dieses Problem abmildern.

Ein alternativer Ansatz ist die Scene7-Technologie, mit der sich die Bildbearbeitung vollständig abgeben lässt. Darüber hinaus können Sie Brand Portal bereitstellen, das nicht nur die Verantwortung für die Generierung von Wiedergaben von der AEM-Infrastruktur übernimmt, sondern auch die gesamte Veröffentlichungsebene.

#### ImageMagick {#imagemagick}

If you customize the DAM Update Asset workflow to generate renditions using ImageMagick, Adobe recommends you modify the `policy.xml` file at `/etc/ImageMagick/`. Standardmäßig beansprucht ImageMagick den gesamten verfügbaren Speicherplatz auf dem Betriebssystem-Volume sowie den verfügbaren Arbeitsspeicher. Make the following configuration changes within the `policymap` section of `policy.xml` to limit these resources.

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

Stellen Sie darüber hinaus in der Datei `configure.xml` (alternativ in der Umgebungsvariable `MAGIC_TEMPORARY_PATH`) den Pfad zum temporären Ordner von ImageMagick auf eine Festplattenpartition ein, die über ausreichend Speicherplatz und IOPS verfügt.

>[!CAUTION]
>
>Eine falsche Konfiguration kann den Server instabil machen, wenn ImageMagick sämtlichen verfügbaren Festplattenspeicher verwendet.
>
>Die Regeländerungen, die zum Verarbeiten großer Dateien mit ImageMagick erforderlich sind, können sich auf die Leistung von AEM auswirken. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

>[!NOTE]
>
>Die ImageMagick- `policy.xml` und `configure.xml` -Dateien stehen `/usr/lib64/ImageMagick-&#42;/config/` anstelle von `/etc/ImageMagick/`zur Verfügung. Informationen zum Speicherort der Konfigurationsdateien finden Sie in der [ImageMagick-Dokumentation](https://www.imagemagick.org/script/resources.php) .

>[!TIP]
>
>Wenn Sie Experience Manager unter Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Adobe-Support, wenn Sie viele große PSD- oder PSB-Dateien verarbeiten möchten. Wenden Sie sich an den Kundenbetreuer von Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Werkzeuge und Modelle für die proprietären Formate von Adobe auszuwählen.

### XMP-Writeback {#xmp-writeback}

XMP-Writeback aktualisiert das Original-Asset, sobald Metadaten in AEM geändert werden. Folgende Änderungen werden vorgenommen:

* Das Asset selbst wird geändert.
* Eine Version des Assets wird erstellt.
* DAM-Update-Asset wird für das Asset ausgeführt.

Die aufgeführten Ergebnisse beanspruchen umfangreiche Ressourcen. Daher empfiehlt Adobe, [XMP-Writeback zu deaktivieren](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html), wenn es nicht benötigt wird.

Wenn Sie eine große Menge an Metadaten importieren, kann es zu ressourcenintensiven XMP-Writeback-Aktivitäten kommen, falls das Flag für laufende Workflows gesetzt ist. Planen Sie einen solchen Import während Zeiten geringer Servernutzung, damit die Leistung anderer Benutzer nicht beeinträchtigt wird.

## Replikation {#replication}

Wenn Sie Assets in einer große Menge an veröffentlichten Instanzen replizieren (beispielsweise in einer Sites-Implementierung), empfiehlt Adobe die Kettenreplikation. In diesem Fall wird die Autorinstanz in eine einzelne Veröffentlichungsinstanz repliziert, die wiederum in die anderen Veröffentlichungsinstanzen repliziert wird und so die Autorinstanz freihält.

### Konfiguration der Kettenreplikation {#configure-chain-replication}

1. Wählen Sie aus, welche Instanz im Veröffentlichungsmodus Sie zum Verketten der zu
1. Fügen Sie dieser Veröffentlichungsinstanz Agenten hinzu, die auf die anderen Veröffentlichungsinstanzen verweisen.
1. Aktivieren Sie für alle anderen Replikationsagenten die Option „Bei Empfang“ auf der Registerkarte „Auslöser“.

>[!NOTE]
>
>Adobe rät von der automatischen Aktivierung von Assets ab. Falls jedoch notwendig, sollte dies der letzte Schritt in einem Workflow, normalerweise „DAM-Update-Asset“, sein.

## Suchindizes {#search-indexes}

Vergewissern Sie sich, dass Sie die neuesten Service Packs und leistungsabhängigen Hotfixes implementiert haben, da sie häufig Aktualisierungen der Systemindizes enthalten. Einige Indexoptimierungen finden Sie unter Tipps zur [Leistungsoptimierung](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) .

Erstellen Sie eigene Indizes für Abfragen, die Sie häufig ausführen. Weitere Informationen finden Sie unter [Methoden zur Analyse von langsamen Abfragen](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) und [Erstellen benutzerdefinierter Indizes](/help/sites-deploying/queries-and-indexing.md). Weitere Einblicke in Best Practices bezüglich Abfragen und Indizes finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-Indexkonfigurationen {#lucene-index-configurations}

Für die Oak-Indexkonfigurationen können Optimierungen vorgenommen werden, mit denen sich die Leistung von AEM Assets verbessern lässt. Aktualisieren Sie die Indexkonfigurationen, um die Neuindizierungszeit zu verbessern:

1. Open CRXDe `/crx/de/index.jsp` and log in as an administrative user
1. Navigieren zu `/oak:index/lucene`
1. Fügen Sie eine String[] -Eigenschaft `excludedPaths` mit Werten `/var`, `/etc/workflow/instances`und `/etc/replication`hinzu.
1. Gehen Sie zu `/oak:index/damAssetLucene`. Fügen Sie eine `String[]` Eigenschaft `includedPaths` mit Wert hinzu `/content/dam`.
1. Speichern Sie.

(Nur AEM 6.1 und 6.2) Aktualisieren Sie den Index ntBaseLucene, um die Leistung des Assets beim Löschen und Verschieben zu verbessern:

1. Navigieren zu `/oak:index/ntBaseLucene/indexRules/nt:base/properties`
1. Hinzufügen von zwei nt:unstrukturierten Knoten `slingResource` und `damResolvedPath` darunter `/oak:index/ntBaseLucene/indexRules/nt:base/properties`
1. Legen Sie die folgenden Eigenschaften auf den Knoten fest (wobei `ordered` und `propertyIndex` Eigenschaften vom Typ sind `Boolean`:

   ```
   slingResource
   name="sling:resource"
   ordered=false
   propertyIndex= true
   type="String"
   damResolvedPath
   name="dam:resolvedPath"
   ordered=false
   propertyIndex=true
   type="String"
   ```

1. On the `/oak:index/ntBaseLucene` node, set the property `reindex=true`. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Monitor the error.log to see when indexing is completed:
Reindexing completed for indexes: [/oak:index/ntBaseLucene]
1. Den Abschluss der Indizierung können Sie auch nachverfolgen, indem Sie „/oak:index/ntBaseLucene“ in CRXDe aktualisieren. Die Eigenschaft für die Neuindizierung würde auf „false“ zurückgesetzt werden.
1. Gehen Sie nach Abschluss der Indizierung zurück zu CRXDe und stellen Sie die Eigenschaft „Typ“ auf den beiden Indizes auf „deaktiviert“ ein.

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Klicken Sie auf „Alle speichern“.

Lucene-Text-Extraktion deaktivieren:

Wenn Ihre Benutzer nicht nach dem Inhalt von Assets suchen müssen, beispielsweise nach Texten, die in PDF-Dokumenten enthalten sind, können Sie diese Funktion deaktivieren und damit die Indexleistung verbessern.

1. Gehen Sie zum AEM-Paketmanager „/crx/packmgr/index.jsp“.
1. Laden Sie das folgende Paket herunter und installieren Sie es.

[Datei laden](assets/disable_indexingbinarytextextraction-10.zip)

### guessTotal {#guess-total}

Verwenden Sie beim Erstellen von Abfragen mit großen Ergebnismengen den Parameter `guessTotal`, um eine übermäßige Belastung des Arbeitsspeichers bei der Ausführung zu vermeiden.

## Bekannte Probleme {#known-issues}

### Große Dateien {#large-files}

Es gibt zwei wichtige bekannte Probleme im Zusammenhang mit großen Dateien in AEM. Bei Dateien, die größer als 2 GB sind, kann eine kalte Standby-Synchronisierung zu einem Speicherengpass führen. In einigen Fällen wird die Ausführung der Standby-Synchronisierung verhindert. In anderen Fällen stürzt die primäre Instanz ab. Dieses Szenario gilt für alle Dateien in AEM, die größer als 2 GB sind, darunter auch Inhaltspakete.

Entsprechend kann es bei Dateien, die in einem gemeinsamen S3-Datenspeicher eine Größe von 2 GB erreichen, einige Zeit dauern, bis die Datei vollständig aus dem Cache in das Dateisystem gespeichert werden kann. Wenn Sie die Binaryless-Replikation verwenden, kann es passieren, dass die binären Daten vor dem Abschluss der Replikation nicht dauerhaft gespeichert werden. Diese Situation kann zu Problemen führen, insbesondere wenn die Verfügbarkeit von Daten wichtig ist.

## Leistungstests {#performance-testing}

Erstellen Sie für jede AEM-Bereitstellung ein Regime für Leistungstests, die Engpässe schnell identifizieren und beseitigen können. Konzentrieren Sie sich dabei auf die folgenden Schlüsselaspekte.

### Netzwerktests {#network-testing}

Führen Sie für alle Aspekte, die die für Kunden relevante Netzwerkleistung betreffen, die folgenden Aufgaben aus:

* Testen Sie die Netzwerkleistung im Netzwerk des Kunden.
* Testen Sie die Netzwerkleistung im Adobe-Netzwerk. Arbeiten Sie bei AMS-Kunden mit CSE, um Tests innerhalb des Adobe-Netzwerks durchzuführen.
* Testen Sie die Netzwerkleistung an anderen Zugriffspunkten.
* Testen Sie unter Verwendung eines Benchmark-Tools für Netzwerke.
* Testen Sie mit dem Dispatcher.

### AEM-Instanztests {#aem-instance-testing}

Um Latenzzeiten zu minimieren und durch effiziente CPU-Auslastung und Lastenverteilung einen hohen Durchsatz zu erzielen, sollten Sie die Leistung Ihrer AEM-Instanz regelmäßig überwachen. Führen Sie insbesondere die folgenden Aufgaben aus:

* Führen Sie Lasttests für die AEM-Instanz aus.
* Überwachen Sie die Upload-Leistung und die Reaktionsfähigkeit der Benutzeroberfläche.

## AEM Assets-Leistungscheckliste   und Auswirkungen von Asset-Management-Aufgaben {#checklist}

* Aktivieren Sie „HTTPS“, um alle vom Unternehmen installierten Sniffer für HTTP-Verkehr zu umgehen.
* Verwenden Sie eine Kabelverbindung, um umfangreiche Assets hochzuladen
* Implementieren Sie die Bereitstellung unter Java 8.
* Stellen Sie optimale JVM-Parameter ein.
* Konfigurieren Sie einen Dateisystem-DataStore oder einen S3-DataStore.
* Aktivieren Sie Verlaufs-Workflows.
* Stimmen Sie die Granit-Workflow-Warteschlangen ab, um gleichzeitige Aufträge einzuschränken.
* Konfigurieren Sie ImageMagick, um den Ressourcenverbrauch einzuschränken.
* Entfernen Sie unnötige Schritte aus dem DAM-Update-Asset-Workflow.
* Konfigurieren Sie Workflow- und Versionsbereinigung.
* Optimieren Sie die Indizes mit den neuesten Service Packs und Hotfixes. Fragen Sie den Adobe-Support nach verfügbaren zusätzlichen Indexoptimierungen.
* Optimieren Sie die Abfrageleistung mit guessTotal.
* Wenn Sie AEM so konfigurieren, dass Dateitypen aus dem Inhalt der Dateien erkannt werden (durch Aktivierung des **[!UICONTROL Day CQ DAM Mime Type Service]** in der **[!UICONTROL AEM-Web-Konsole]**), sollten Sie außerhalb der Spitzenzeiten größere Mengen an Dateien in Batches hochladen, da dieser Vorgang ressourcenintensiv ist.
