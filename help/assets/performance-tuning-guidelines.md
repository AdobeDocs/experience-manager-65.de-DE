---
title: Leistungsoptimierung [!DNL Assets].
description: Empfehlungen und Hinweise zu  [!DNL Experience Manager] -Konfiguration, Änderungen an Hardware-, Software- und Netzwerkkomponenten, um Engpässe zu beseitigen und die Leistung von  [!DNL Experience Manager Assets] zu optimieren.
contentOwner: AG
mini-toc-levels: 1
role: Architect, Admin
feature: Asset Management
exl-id: 1d9388de-f601-42bf-885b-6a7c3236b97e
source-git-commit: e3caa3e3067cf5e29cfcdf4286047eb346aefa23
workflow-type: ht
source-wordcount: '2753'
ht-degree: 100%

---

<!-- TBD: Get reviewed by engineering. -->

# [!DNL Adobe Experience Manager Assets] Anleitung zur Leistungsoptimierung {#assets-performance-tuning-guide}

Das Setup [!DNL Experience Manager Assets] von umfasst eine Reihe von Hardware-, Software- und Netzwerkkomponenten. Je nach Ihrem Bereitstellungsszenario benötigen Sie möglicherweise bestimmte Konfigurationsänderungen an den Hardware-, Software- und Netzwerkkomponenten, um Leistungsengpässe zu vermeiden.

Außerdem schaffen Sie eine solide Grundlage für Ihre [!DNL Experience Manager Assets]-Bereitstellung, mit der Sie alle Anforderungen an Leistung, Skalierbarkeit und Zuverlässigkeit erfüllen, wenn Sie sich an bestimmte Richtlinien zur Optimierung der Hardware und Software halten.

Eine schwache Leistung von [!DNL Experience Manager Assets] kann sich auf die Benutzerfreundlichkeit auswirken und die interaktive Leistung, Asset-Verarbeitung und Download-Geschwindigkeit und andere Bereiche beeinträchtigen.

Daher gehört die Leistungsoptimierung zu den grundlegenden Aufgaben, bevor Sie Zielmetriken für Ihre Projekte erstellen.

In den folgenden Schlüsselbereichen sollten Sie besonders darauf achten, dass Leistungsprobleme erkannt und behoben werden, bevor sie sich auf das Benutzererlebnis auswirken.

## Plattform {#platform}

Experience Manager wird auf einer Reihe von Plattformen unterstützt. Adobe zufolge werden die nativen Tools jedoch unter Linux und Windows besonders gut unterstützt und können dort zur optimalen Leistung und Vereinfachung der Implementierung beitragen. Ein 64-Bit-Betriebssystem ist ideal für die hohen Speicheranforderungen einer [!DNL Experience Manager Assets]-Bereitstellung. Wie bei jeder Experience Manager-Bereitstellung sollten Sie nach Möglichkeit TarMK implementieren. TarMK kann zwar nicht über eine einzelne Autoreninstanz skaliert werden, erzielt jedoch erfahrungsgemäß eine bessere Leistung als MongoMK. Sie können TarMK-Offload-Instanzen hinzufügen, um die Leistung der Workflow-Verarbeitung Ihrer [!DNL Experience Manager Assets]-Bereitstellung zu erhöhen.

### Temporärer Ordner {#temp-folder}

Nutzen Sie einen Hochleistungsspeicher für das temporäre Java-Verzeichnis, um das Hochladen der Assets zu beschleunigen. Unter Linux und Windows können Sie beispielsweise ein RAM- oder SSD-Laufwerk verwenden. In Cloud-basierten Umgebungen kann ein äquivalenter Hochgeschwindigkeitsspeicher verwendet werden. In Amazon EC2 beispielsweise kann ein Laufwerk vom Typ [flüchtiges Laufwerk](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) als temporärer Ordner eingesetzt werden.

Bei einer großen Speicherkapazität des Servers kann ein RAM-Laufwerk konfiguriert werden. Führen Sie unter Linux die folgenden Befehle aus, um ein RAM-Laufwerk von 8 GB zu erstellen:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Unter Windows müssen Sie den Treiber eines Drittanbieters nutzen, um ein RAM-Laufwerk zu erstellen, oder einen Hochleistungsspeicher wie SSD verwenden.

Sobald das temporäre Hochleistungs-Volume bereit ist, stellen Sie den JVM-Parameter `-Djava.io.tmpdir` ein. Sie können beispielsweise den JVM-Parameter unter der Variablen `CQ_JVM_OPTS` im Skript `bin/start` von [!DNL Experience Manager] einfügen:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-Konfiguration {#java-configuration}

### Java-Version {#java-version}

Adobe empfiehlt die Bereitstellung von [!DNL Experience Manager Assets] auf Java 8, um die Leistung zu optimieren.

<!-- TBD: Link to the latest official word around Java.
-->

### JVM-Parameter  {#jvm-parameters}

Legen Sie die folgenden JVM Parameter fest:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Datenspeicher- und Arbeitsspeicherkonfiguration {#data-store-and-memory-configuration}

### Dateidatenspeicherkonfiguration {#file-data-store-configuration}

Allen [!DNL Experience Manager Assets]-Benutzern von wird angeraten, Datenspeicher und Segmentspeicher zu trennen. Außerdem kann die Leistung durch die Konfiguration der Parameter `maxCachedBinarySize` und `cacheSizeInMB` maximiert werden. Stellen Sie `maxCachedBinarySize` auf die kleinste im Cache unterstützte Dateigröße ein. Geben Sie die Größe des Arbeitsspeicher-Cache für den Datenspeicher in `cacheSizeInMB` ein. Adobe empfiehlt, diesen Wert auf 2–10 Prozent der gesamten Heap-Größe einzustellen. Mithilfe von Last-/Leistungstests lässt sich die ideale Einstellung herausfinden.

### Konfigurieren der Maximalgröße des gepufferten Bilder-Caches   {#configure-the-maximum-size-of-the-buffered-image-cache}

Verringern Sie beim Hochladen großer Mengen an Assets in [!DNL Adobe Experience Manager] zur Berücksichtigung unerwarteter Spitzen bei der Speichernutzung und zur Verhinderung von JVM-Fehlern mit OutOfMemoryErrors die konfigurierte Maximalgröße des gepufferten Bilder-Caches. Betrachten wir ein Beispiel mit einem System, das über eine maximale Heap-Größe (-`Xmx`param) von 5 GB verfügt und bei dem der Oak-Blob-Cache auf 1 GB und der Dokumenten-Cache auf 2 GB eingestellt ist. In diesem Fall würde der gepufferte Cache das Maximum von 1,25 GB Speicher in Anspruch nehmen, wodurch nur 0,75 GB Speicher für unerwartete Spitzen verblieben.

Konfigurieren Sie die Größe des gepufferten Cache in der OSGi-Webkonsole. Legen Sie bei `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache` die Eigenschaft `cq.dam.image.cache.max.memory` in Byte fest. 1073741824 entspricht beispielsweise 1 GB (1024 x 1024 x 1024 = 1 GB).

Wenn Sie über Experience Manager 6.1 SP1 einen `sling:osgiConfig`-Knoten zur Konfiguration dieser Eigenschaft verwenden, stellen Sie sicher, dass Sie diesen Datentyp auf „Long“ einstellen. Weitere Details finden Sie unter [CQBufferedImageCache belegt beim Asset-Upload den Heap](https://helpx.adobe.com/de/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Gemeinsame Datenspeicher   {#shared-data-stores}

Mit der Implementierung eines S3-Datenspeichers oder Shared File Datastore sparen Sie Speicherplatz auf der Festplatte und erhöhen den Netzwerkdurchsatz in großen Implementierungen. Weitere Informationen zu den Vor- und Nachteilen des gemeinsamen Datenspeichers finden Sie in der [Anleitung zur Größenänderung von Assets](/help/assets/assets-sizing-guide.md).

### S3-Datenspeicher {#s-data-store}

Mit der folgenden Konfiguration des S3-Datenspeichers (`org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) konnte Adobe binäre große Objekte (BLOBs) mit einer Größe von 12,8 TB von einem vorhandenen Dateidatenspeicher in einen S3-Datenspeicher am Standort eines Kunden extrahieren:

```conf
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

Adobe empfiehlt die Aktivierung von HTTPS, da viele Unternehmen über Firewalls verfügen, die den HTTP-Verkehr überprüfen und sich dadurch negativ auf Uploads auswirken und Dateien beschädigen. Stellen Sie bei großen Datei-Uploads sicher, dass Benutzer über Kabelverbindungen zum Netzwerk verfügen, da ein WLAN-Netzwerk schnell überfordert ist. Richtlinien zur Ermittlung von Engpässen im Netzwerk finden Sie in der [Anleitung zur Größenänderung von Assets](/help/assets/assets-sizing-guide.md). Informationen zur Beurteilung der Netzwerkleistung mit einer Analyse der Netzwerktopologie finden Sie unter [Überlegungen zum Assets-Netzwerk](/help/assets/assets-network-considerations.md).

Welche Strategie der Netzwerkoptimierung Sie verwenden, hängt in erster Linie von der verfügbaren Bandbreite und der Last auf Ihrer [!DNL Experience Manager]-Instanz ab. Allgemeine Konfigurationsoptionen, einschließlich Firewalls oder Proxys, können zur Verbesserung der Netzwerkleistung beitragen. Die folgenden Aspekte sollten berücksichtigt werden:

* Stellen Sie je nach Instanztyp (klein, mittel, groß) sicher, dass die Netzwerkbandbreite für Ihre Experience Manager-Instanz ausreichend ist. Dies ist besonders wichtig, wenn [!DNL Experience Manager] auf AWS gehostet wird.
* Wird Ihre [!DNL Experience Manager]-Instanz auf AWS gehostet, können Sie von einer flexiblen Skalierung profitieren. Vergrößern Sie die Instanz, wenn Benutzer eine hohe Belastung erwarten. Verkleinern Sie die Instanz, wenn nur eine mäßige/geringe Belastung erwartet wird.
* HTTPS: Die meisten Benutzer verwenden Firewalls zur Überwachung des HTTP-Verkehrs. Sie können den Prozess des Hochladens beeinträchtigen oder Dateien beim Hochladen beschädigen.
* Upload großer Dateien: Die Benutzer benötigen Kabelverbindungen zum Netzwerk (WLAN-Verbindungen sind schnell gesättigt).

## Workflows {#workflows}

### Übergangs-Workflows {#transient-workflows}

Stellen Sie den Workflow [!UICONTROL DAM-Update-Asset] nach Möglichkeit auf „Übergang“ ein. Die Einstellung trägt zu einer erheblichen Reduzierung des Overheads bei, der für die Verarbeitung der Workflows benötigt wird, da die Workflows in diesem Fall nicht die normalen Tracking- und Archivierungsprozesse durchlaufen.

1. Navigieren Sie zu `/miscadmin` in der [!DNL Experience Manager]-Bereitstellung unter `https://[aem_server]:[port]/miscadmin`.

1. Erweitern Sie **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL dam]**.

1. Öffnen Sie **[!UICONTROL DAM-Update-Asset]**. Wechseln Sie im unverankerten Tool-Fenster auf die Registerkarte **[!UICONTROL Seite]** und klicken Sie auf **[!UICONTROL Seiteneigenschaften]**.

1. Wählen Sie **[!UICONTROL Übergangs-Workflow]** und klicken Sie dann auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Einige Funktionen unterstützen keine Übergangs-Workflows. Wenn diese Funktionen in Ihrer [!DNL Assets]-Bereitstellung benötigt werden, konfigurieren Sie keine Übergangs-Workflows.

Wenn keine Übergangs-Workflows verwendet werden können, führen Sie regelmäßig Workflow-Bereinigungen durch, um archivierte [!UICONTROL DAM-Update-Asset]-Workflows zu löschen. So verhindern Sie eine Beeinträchtigung der Systemleistung.

Führen Sie die Bereinigungs-Workflows normalerweise wöchentlich aus. In ressourcenintensiven Szenarien wie z. B. einer umfangreichen Asset-Erfassung kann die Bereinigung auch häufiger ausgeführt werden.

Um die Workflow-Bereinigung zu konfigurieren, fügen Sie in der OSGi-Konsole eine neue Adobe Granite-Workflow-Bereinigungskonfiguration hinzu. Konfigurieren und planen Sie im nächsten Schritt den Workflow als Teil des wöchentlichen Wartungsfensters.

Dauert die Bereinigung zu lange, kommt es zu einem Timeout. Daher sollten Sie sicherstellen, dass die Bereinigungsaufträge abgeschlossen sind. So vermeiden Sie, dass Bereinigungs-Workflows aufgrund der hohen Zahl an Workflows nicht abgeschlossen werden können.

Wenn Sie zahlreiche Nicht-Übergangs-Workflows ausgeführt haben, die Workflow-Instanzknoten erstellen, können Sie das Tool [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) auf Ad-hoc-Basis ausführen. Es entfernt redundante, abgeschlossene Workflow-Instanzen sofort, ohne dass Sie auf die Ausführung des Adobe Granite-Workflow-Bereinigungsplaners warten müssen.

### Maximal parallel ausführbare Aufträge   {#maximum-parallel-jobs}

Standardmäßig kann [!DNL Experience Manager] maximal so viele Aufträge parallel ausführen wie Prozessoren auf dem Server vorhanden sind. In Zeiten hoher Auslastung ist diese Einstellung jedoch problematisch, da alle Prozessoren von den [!UICONTROL DAM-Update-Asset]-Workflows beansprucht werden und dadurch die Reaktionsfähigkeit der Benutzeroberfläche verlangsamt wird und [!DNL Experience Manager] andere Prozesse zum Schutz von Serverleistung und -stabilität nicht ausführen kann. Es hat sich bewährt, diese Einstellung so zu wählen, dass nur die Hälfte der auf dem Server verfügbaren Prozessoren verwendet wird:

1. Greifen Sie in der [!DNL Experience Manager]-Autoreninstanz auf `https://[aem_server]:[port]/system/console/slingevent` zu.

1. Klicken Sie für jede für Ihre Implementierung relevante Workflow-Warteschlange, z. B. für die **[!UICONTROL Ganite-Übergangs-Workflows-Warteschlange]**, auf **[!UICONTROL Bearbeiten]**.

1. Ändern Sie den Wert der **[!UICONTROL maximal parallel ausführbaren Aufträge]** und klicken Sie auf **[!UICONTROL Speichern]**.

Diese Einstellung des Werts auf die Hälfte der verfügbaren Prozesse ist für den Anfang eine praktikable Lösung. Unter Umständen müssen Sie diese Zahl jedoch nach oben oder unten anpassen, um den maximalen Durchsatz zu erreichen, und auch an die spezifische Umgebung anpassen. Es gibt separate Warteschlangen für Übergangs- und Nicht-Übergangs-Workflows sowie für andere Prozesse wie beispielsweise externe Workflows. Sind mehrere Warteschlangen, die auf 50 % der Prozessoren gesetzt sind, gleichzeitig aktiv, kann es schnell zu einer Überlastung des Systems kommen. Welche Warteschlangen stark ausgelastet sind, hängt in hohem Maße von den Benutzerimplementierungen ab. Sie müssen daher sorgfältig und mit Bedacht konfiguriert werden, um maximale Effizienz zu erreichen, die nicht zu Lasten der Serverstabilität geht.

### Konfiguration von DAM-Update-Asset {#dam-update-asset-configuration}

Der [!UICONTROL DAM-Update-Asset]-Workflow enthält eine vollständige Suite an für Aufgaben konfigurierten Schritten, beispielsweise Dynamic Media PTIFF-Generierung und [!DNL Adobe InDesign Server]-Integration. Die meisten Benutzer benötigen jedoch nicht alle diese Schritte. Adobe empfiehlt die Erstellung einer benutzerdefinierten Kopie des [!UICONTROL DAM-Update-Asset]-Workflow-Modells, in der alle unnötigen Schritte entfernt wurden. Ändern Sie dann die Launcher für [!UICONTROL DAM-Update-Asset] so, dass sie auf das neue Modell zeigen.

Wenn Sie den Workflow [!UICONTROL DAM-Update-Asset] häufig ausführen, kann hierdurch die Größe Ihres Dateidatenspeichers deutlich ansteigen. Entsprechende Tests von Adobe haben gezeigt, dass die Datenspeichergröße um ca. 400 GB ansteigt, wenn innerhalb von 8 Stunden 5.500 Workflows ausgeführt werden.

Hierbei handelt es sich um einen vorübergehenden Anstieg. Nach Ausführung der Aufgabe zur Speicherbereinigung weist der Datenspeicher wieder seine ursprüngliche Größe auf.

In der Regel wird die Speicherbereinigung wöchentlich gemeinsam mit anderen geplanten Wartungsaufgaben ausgeführt.

Wenn Sie nur über eingeschränkten Speicherplatz verfügen und den Workflow [!UICONTROL DAM-Update-Asset] häufig ausführen, sollten Sie die Speicherbereinigung öfter planen.

#### Ausgabegenerierung zur Laufzeit {#runtime-rendition-generation}

Kunden verwenden Bilder unterschiedlicher Größen und Formate auf ihrer Website oder zur Weiterleitung an die Geschäftspartner. Da jede Darstellung den Footprint der Assets im Repository vergrößert, empfiehlt Adobe die umsichtige Verwendung dieser Funktion. Um die Menge der Ressourcen zu reduzieren, die für die Verarbeitung und Speicherung von Bildern benötigt wird, können Sie die Bilder statt als Ausgabeformate bei der Erfassung auch zur Laufzeit generieren.

Viele Kunden der Website implementieren ein Bild-Servlet, das Bilder zum Zeitpunkt ihrer Anforderung skaliert und beschneidet und der Veröffentlichungsinstanz damit eine zusätzliche Belastung auferlegt. Wenn diese Bilder zwischengespeichert werden können, lässt sich dieses Problem abmildern.

Ein alternativer Ansatz besteht darin, die Dynamic Media-Technologie zu verwenden, um die Bildbearbeitung vollständig abzugeben. Darüber hinaus können Sie Brand Portal bereitstellen, das nicht nur die Verantwortung für die Generierung von Ausgabedarstellungen von der [!DNL Experience Manager]-Infrastruktur übernimmt, sondern auch die gesamte Veröffentlichungsebene.

#### ImageMagick {#imagemagick}

Wenn Sie den Workflow [!UICONTROL DAM-Update-Asset] so anpassen, dass Ausgabeformate mit ImageMagick generiert werden, empfiehlt Adobe die Bearbeitung der Datei `policy.xml` unter `/etc/ImageMagick/`. Standardmäßig beansprucht ImageMagick den gesamten verfügbaren Speicherplatz auf dem Betriebssystem-Volume sowie den verfügbaren Arbeitsspeicher. Nehmen Sie im Abschnitt `policymap` der Datei `policy.xml` die folgenden Konfigurationsänderungen vor, um diese Ressourcen zu beschränken.

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

Stellen Sie darüber hinaus in der Datei `configure.xml` (alternativ in der Umgebungsvariable `MAGICK_TEMPORARY_PATH`) den Pfad zum temporären Ordner von ImageMagick auf eine Festplattenpartition ein, die über ausreichend Speicherplatz und IOPS verfügt.

>[!CAUTION]
>
>Eine falsche Konfiguration kann den Server instabil machen, wenn ImageMagick sämtlichen verfügbaren Festplattenspeicher verwendet. Die Regeländerungen, die zum Verarbeiten großer Dateien mit ImageMagick erforderlich sind, können sich auf die Leistung von [!DNL Experience Manager] auswirken. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

>[!NOTE]
>
>Die Dateien `policy.xml` und `configure.xml` von ImageMagick sind unter `/usr/lib64/ImageMagick-&#42;/config/` verfügbar, anstelle von `/etc/ImageMagick/`. In der [Dokumentation zu ImageMagick](https://www.imagemagick.org/script/resources.php) finden Sie den Speicherort der Konfigurationsdateien.

Wenn Sie [!DNL Experience Manager] in Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Adobe Support, wenn Sie viele große PSD- oder PSB-Dateien verarbeiten möchten. Wenden Sie sich an den Support-Mitarbeiter von Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Tools und Modelle für die proprietären Formate von Adobe auszuwählen. [!DNL Experience Manager] kann keine sehr hochauflösenden PSB-Dateien verarbeiten, die mehr als 30000 x 23000 Pixel groß sind.

### XMP-Writeback {#xmp-writeback}

XMP-Writeback aktualisiert das Original-Asset, sobald Metadaten in [!DNL Experience Manager] geändert werden. Folgende Änderungen werden vorgenommen:

* Das Asset selbst wird geändert.
* Eine Version des Assets wird erstellt.
* [!UICONTROL DAM-Update-Asset wird für das Asset ausgeführt.]

Die aufgeführten Ergebnisse beanspruchen umfangreiche Ressourcen. Adobe empfiehlt daher, die XMP Writeback zu deaktivieren, wenn sie nicht erforderlich ist. Weitere Informationen finden Sie unter [XMP Writeback](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/xmp-writeback.html?lang=de).

Wenn Sie eine große Menge an Metadaten importieren, kann es zu ressourcenintensiven XMP-Writeback-Aktivitäten kommen, falls das Flag für laufende Workflows gesetzt ist. Planen Sie einen solchen Import während Zeiten geringer Servernutzung, damit die Leistung anderer Benutzer nicht beeinträchtigt wird.

## Replikation {#replication}

Wenn Sie Assets in einer große Menge an veröffentlichten Instanzen replizieren (beispielsweise in einer Sites-Implementierung), empfiehlt Adobe die Kettenreplikation. In diesem Fall wird die Autorinstanz in eine einzelne Veröffentlichungsinstanz repliziert, die wiederum in die anderen Veröffentlichungsinstanzen repliziert wird und so die Autorinstanz freihält.

### Konfiguration der Kettenreplikation   {#configure-chain-replication}

1. Wählen Sie die Veröffentlichungsinstanz, mit der Sie die Replikationen verketten möchten.
1. Fügen Sie dieser Veröffentlichungsinstanz Agenten hinzu, die auf die anderen Veröffentlichungsinstanzen verweisen.
1. Aktivieren Sie für alle anderen Replikationsagenten die Option „Bei Empfang“ auf der Registerkarte „Auslöser“.

>[!NOTE]
>
>Adobe rät von der automatischen Aktivierung von Assets ab. Falls jedoch notwendig, sollte dies der letzte Schritt in einem Workflow, normalerweise „DAM-Update-Asset“, sein.

## Durchsuchen von Indizes   {#search-indexes}

Installieren Sie [die neuesten Service Packs](/help/release-notes/release-notes.md) und leistungsbezogene Hotfixes, da diese häufig Aktualisierungen von Systemindizes enthalten. Informationen zur Indexoptimierung finden Sie unter [Tipps zur Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html?lang=de).

Erstellen Sie eigene Indizes für Abfragen, die Sie häufig ausführen. Weitere Informationen finden Sie unter [Methoden zur Analyse von langsamen Abfragen](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) und [Erstellen benutzerdefinierter Indizes](/help/sites-deploying/queries-and-indexing.md). Weitere Einblicke in Best Practices bezüglich Abfragen und Indizes finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-Indexkonfigurationen {#lucene-index-configurations}

Für die Oak-Indexkonfigurationen können Optimierungen vorgenommen werden, mit denen sich die Leistung von [!DNL Experience Manager Assets] verbessern lässt. Aktualisieren Sie die Indexkonfigurationen, um die Neuindizierungszeit zu verbessern:

1. Öffnen Sie CRXDE `/crx/de/index.jsp` und melden Sie sich als Benutzer mit Administratorrechten an.
1. Navigieren Sie zu `/oak:index/lucene`.
1. Fügen Sie eine `String[]`-Eigenschaft `excludedPaths` mit den Werten `/var`, `/etc/workflow/instances` und `/etc/replication` hinzu.
1. Navigieren Sie zu `/oak:index/damAssetLucene`. Fügen Sie eine `String[]`-Eigenschaft `includedPaths` mit dem Wert `/content/dam` hinzu. Speichern Sie die Änderungen.

Wenn Ihre Benutzer keine Volltextsuche nach Assets durchführen müssen, z. B. durch die Textsuche in PDF-Dokumenten, deaktivieren Sie sie. Sie verbessern die Indexleistung, indem Sie die Volltextindizierung deaktivieren. Um die [!DNL Apache Lucene]-Textextraktion zu deaktivieren, führen Sie die folgenden Schritte aus:

1. Greifen Sie in der [!DNL Experience Manager]-Benutzeroberfläche auf [!UICONTROL Package Manager] zu.
1. Laden Sie das Paket hoch und installieren Sie es unter [disable_indexingbinarytextextraktion-10.zip](assets/disable_indexingbinarytextextraction-10.zip).

### guessTotal {#guess-total}

Verwenden Sie beim Erstellen von Abfragen mit großen Ergebnismengen den Parameter `guessTotal`, um eine übermäßige Belastung des Arbeitsspeichers bei der Ausführung zu vermeiden.

## Bekannte Probleme {#known-issues}

### Große Dateien {#large-files}

Zwei bekannte Probleme beziehen sich auf große Dateien in [!DNL Experience Manager]. Bei Dateien, die größer als 2 GB sind, kann eine kalte Standby-Synchronisierung zu einem Speicherengpass führen. In einigen Fällen wird die Ausführung der Standby-Synchronisierung verhindert. In anderen Fällen stürzt die primäre Instanz ab. Dieses Szenario gilt für alle Dateien in [!DNL Experience Manager], die größer als 2 GB sind, darunter auch Inhaltspakete.

Entsprechend kann es bei Dateien, die in einem gemeinsamen S3-Datenspeicher eine Größe von 2 GB erreichen, einige Zeit dauern, bis die Datei vollständig aus dem Cache in das Dateisystem gespeichert werden kann. Wenn Sie die Binaryless-Replikation verwenden, kann es passieren, dass die binären Daten vor dem Abschluss der Replikation nicht dauerhaft gespeichert werden. Diese Situation kann zu Problemen führen, insbesondere wenn es auf hohe Datenverfügbarkeit ankommt.

## Leistungstests {#performance-testing}

Erstellen Sie für jede [!DNL Experience Manager]-Implementierung einen Plan für Leistungstests, der Engpässe schnell identifizieren und beseitigen kann. Konzentrieren Sie sich dabei auf die folgenden Schlüsselaspekte.

### Netzwerktests   {#network-testing}

Führen Sie für alle Aspekte, die die für Kunden relevante Netzwerkleistung betreffen, die folgenden Aufgaben aus:

* Testen Sie die Netzwerkleistung im Netzwerk des Kunden.
* Testen Sie die Netzwerkleistung im Adobe-Netzwerk. Arbeiten Sie bei AMS-Kunden mit CSE, um Tests innerhalb des Adobe-Netzwerks durchzuführen.
* Testen Sie die Netzwerkleistung an anderen Zugriffspunkten.
* Testen Sie unter Verwendung eines Benchmark-Tools für Netzwerke.
* Testen Sie mit dem Dispatcher.

### [!DNL Experience Manager]-Bereitstellungstests {#aem-deployment-testing}

Überwachen Sie die Leistung Ihrer [!DNL Experience Manager]-Bereitstellung regelmäßig, um die Latenz zu reduzieren und mithilfe von effizienter CPU-Auslastung und -Freigabe einen hohen Durchsatz zu erzielen. Führen Sie insbesondere die folgenden Aufgaben aus:

* Führen Sie Belastungstests für die [!DNL Experience Manager]-Bereitstellung durch.
* Überwachen Sie die Upload-Leistung und die Reaktionsfähigkeit der Benutzeroberfläche.

## [!DNL Experience Manager Assets]-Leistungsprüfliste und Auswirkung von Asset-Management-Aufgaben {#checklist}

* Aktivieren Sie „HTTPS“, um alle vom Unternehmen installierten Sniffer für HTTP-Traffic zu umgehen.
* Verwenden Sie eine Kabelverbindung, um umfangreiche Assets hochzuladen.
* Implementieren Sie die Bereitstellung unter Java 8.
* Stellen Sie optimale JVM-Parameter ein..
* Konfigurieren Sie einen Dateisystem-DataStore oder einen S3-DataStore.
* Deaktivieren Sie das Erzeugen von Unter-Assets. Ist diese Option aktiviert, erstellt der Workflow in AEM für jede Seite eines mehrseitigen Assets ein separates Asset. Jede dieser Seiten ist selbst Asset, das zusätzlichen Speicherplatz belegt sowie Versionierung und zusätzliche Workflow-Verarbeitung erfordert. Wenn Sie keine separaten Seiten benötigen, deaktivieren Sie das Erzeugen von Unter-Assets und die Seitenextraktion.
* Aktivieren Sie Übergangs-Workflows.
* Stimmen Sie die Granit-Workflow-Warteschlangen ab, um gleichzeitige Aufträge einzuschränken.
* Konfigurieren Sie [!DNL ImageMagick] so, dass der Ressourcenverbrauch eingeschränkt ist. 
* Entfernen Sie unnötige Schritte aus dem [!UICONTROL DAM-Update-Asset]-Workflow.
* Konfigurieren Sie Workflow- und Versionsbereinigung.
* Optimieren Sie die Indizes mit den neuesten Service Packs und Hotfixes. Fragen Sie den Adobe-Kunden-Support nach verfügbaren zusätzlichen Indexoptimierungen.
* Optimieren Sie die Abfrageleistung mit guessTotal.
* Wenn Sie [!DNL Experience Manager] so konfigurieren, dass Dateitypen aus dem Inhalt der Dateien erkannt werden (durch Aktivierung des **[!UICONTROL Day CQ DAM Mime Type Service]** in der **[!UICONTROL AEM-Web-Konsole]**), sollten Sie außerhalb der Spitzenzeiten größere Mengen an Dateien in Batches hochladen, da dieser Vorgang ressourcenintensiv ist.
