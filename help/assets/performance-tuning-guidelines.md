---
title: Leistungsoptimierung [!DNL Assets].
description: 'Vorschläge und Anleitungen zur Konfiguration, Änderungen an Hardware, Software und Netzwerkkomponenten, um Engpässe zu beseitigen und die Leistung von [!DNL Experience Manager Assets] zu optimieren. [!DNL Experience Manager] '
contentOwner: AG
mini-toc-levels: 1
role: Architekt, Administrator
translation-type: tm+mt
source-git-commit: ebe7042b931869c3b4b7204e3ce7afa52d56f0ef
workflow-type: tm+mt
source-wordcount: '2743'
ht-degree: 52%

---


<!-- TBD: Get reviewed by engineering. -->

# [!DNL Adobe Experience Manager Assets] Handbuch zur Leistungsoptimierung  {#assets-performance-tuning-guide}

Ein [!DNL Experience Manager Assets]-Setup enthält eine Reihe von Hardware-, Software- und Netzwerkkomponenten. Je nach Ihrem Bereitstellungsszenario benötigen Sie möglicherweise bestimmte Konfigurationsänderungen an den Hardware-, Software- und Netzwerkkomponenten, um Leistungsengpässe zu vermeiden.

Darüber hinaus hilft die Identifizierung und Einhaltung bestimmter Richtlinien zur Hardware- und Softwareoptimierung beim Aufbau einer soliden Grundlage, die es Ihrer [!DNL Experience Manager Assets]-Implementierung ermöglicht, die Erwartungen hinsichtlich Leistung, Skalierbarkeit und Zuverlässigkeit zu erfüllen.

Eine ungenügende Leistung in [!DNL Experience Manager Assets] kann sich auf die Benutzererfahrung in Bezug auf interaktive Leistung, Asset-Verarbeitung, Downloadgeschwindigkeit und anderen Bereichen auswirken.

Daher gehört die Leistungsoptimierung zu den grundlegenden Aufgaben, bevor Sie Zielmetriken für Ihre Projekte erstellen.

In den folgenden Schlüsselbereichen sollten Sie besonders darauf achten, dass Leistungsprobleme erkannt und behoben werden, bevor sie sich auf das Benutzererlebnis auswirken.

## Plattform {#platform}

Obwohl Experience Manager auf verschiedenen Plattformen unterstützt wird, hat Adobe die größte Unterstützung für native Tools unter Linux und Windows gefunden, was zu einer optimalen Performance und einfachen Implementierung beiträgt. Idealerweise sollten Sie ein 64-Bit-Betriebssystem bereitstellen, um die hohen Speicheranforderungen einer [!DNL Experience Manager Assets]-Bereitstellung zu erfüllen. Wie bei jeder Implementierung von Experience Managern sollten Sie TarMK so weit wie möglich implementieren. TarMK kann zwar nicht über eine einzelne Autoreninstanz skaliert werden, erzielt jedoch erfahrungsgemäß eine bessere Leistung als MongoMK. Sie können TarMK-Offload-Instanzen hinzufügen, um die Verarbeitungsleistung Ihrer [!DNL Experience Manager Assets]-Bereitstellung zu erhöhen.

### Temporärer Ordner {#temp-folder}

Um die Upload-Zeit für Assets zu verbessern, verwenden Sie eine Hochleistungs-Datenspeicherung für den temporären Java-Ordner. Unter Linux und Windows können Sie beispielsweise ein RAM- oder SSD-Laufwerk verwenden. In Cloud-basierten Umgebungen kann ein äquivalenter Hochgeschwindigkeitsspeicher verwendet werden. In Amazon EC2 kann beispielsweise ein [temporäres Laufwerk](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) für den temporären Ordner verwendet werden.

Bei einer großen Speicherkapazität des Servers kann ein RAM-Laufwerk konfiguriert werden. Führen Sie unter Linux die folgenden Befehle aus, um ein RAM-Laufwerk von 8 GB zu erstellen:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Unter Windows OS verwenden Sie einen Treiber eines Drittanbieters, um ein RAM-Laufwerk zu erstellen, oder verwenden Sie einfach eine leistungsstarke Datenspeicherung wie SSD.

Sobald das temporäre Volume mit hoher Leistung fertig ist, stellen Sie den JVM-Parameter `-Djava.io.tmpdir` ein. Sie könnten beispielsweise den JVM-Parameter unten zur Variablen `CQ_JVM_OPTS` im Skript `bin/start` von [!DNL Experience Manager] hinzufügen:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-Konfiguration {#java-configuration}

### Java-Version {#java-version}

Adobe empfiehlt die Bereitstellung von [!DNL Experience Manager Assets] unter Java 8, um eine optimale Leistung zu erzielen.

<!-- TBD: Link to the latest official word around Java.
-->

### JVM-Parameter   {#jvm-parameters}

Legen Sie die folgenden JVM-Parameter fest:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Datenspeicher- und Arbeitsspeicherkonfiguration {#data-store-and-memory-configuration}

### Dateidatenspeicherkonfiguration {#file-data-store-configuration}

Für alle [!DNL Experience Manager Assets]-Benutzer wird empfohlen, den Datenspeicher vom Segmentspeicher zu trennen. Außerdem kann die Leistung durch die Konfiguration der Parameter `maxCachedBinarySize` und `cacheSizeInMB` maximiert werden. Stellen Sie `maxCachedBinarySize` auf die kleinste im Cache unterstützte Dateigröße ein. Geben Sie die Größe des Arbeitsspeicher-Cache für den Datenspeicher in `cacheSizeInMB` ein. Adobe empfiehlt, diesen Wert auf 2–10 Prozent der gesamten Heap-Größe einzustellen. Mithilfe von Last-/Leistungstests lässt sich die ideale Einstellung herausfinden.

### Konfigurieren der Maximalgröße des gepufferten Bilder-Caches    {#configure-the-maximum-size-of-the-buffered-image-cache}

Wenn Sie große Mengen von Assets auf [!DNL Adobe Experience Manager] hochladen, um unerwartete Spitzen beim Speicherverbrauch zu ermöglichen und um zu verhindern, dass JVM mit OutOfMemoryErrors fehlschlägt, reduzieren Sie die konfigurierte maximale Größe des gepufferten Bild-Cache. Betrachten wir ein Beispiel mit einem System, das über eine maximale Heap-Größe (-`Xmx`param) von 5 GB verfügt und bei dem der Oak-Blob-Cache auf 1 GB und der Dokumenten-Cache auf 2 GB eingestellt ist. In diesem Fall würde der gepufferte Cache das Maximum von 1,25 GB Speicher in Anspruch nehmen, wodurch nur 0,75 GB Speicher für unerwartete Spitzen verblieben.

Konfigurieren Sie die Größe des gepufferten Cache in der OSGi-Webkonsole. Legen Sie bei `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache` die Eigenschaft `cq.dam.image.cache.max.memory` in Byte fest. 1073741824 entspricht beispielsweise 1 GB (1024 x 1024 x 1024 = 1 GB).

Wenn Sie in Experience Manager 6.1 SP1 einen `sling:osgiConfig`-Knoten zum Konfigurieren dieser Eigenschaft verwenden, stellen Sie sicher, dass der Datentyp auf &quot;Lang&quot;eingestellt ist. Weitere Details finden Sie unter [CQBufferedImageCache belegt beim Asset-Upload den Heap](https://helpx.adobe.com/de/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Gemeinsame Datenspeicher    {#shared-data-stores}

Mit der Implementierung eines S3-Datenspeichers oder Shared File Datastore sparen Sie Speicherplatz auf der Festplatte und erhöhen den Netzwerkdurchsatz in großen Implementierungen. Weitere Informationen zu den Vor- und Nachteile der Verwendung eines gemeinsamen Datenspeichers finden Sie unter [Handbuch zur Asset-Größenanpassung](/help/assets/assets-sizing-guide.md).

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

Adobe empfiehlt die Aktivierung von HTTPS, da viele Unternehmen über Firewalls verfügen, die den HTTP-Verkehr überprüfen und sich dadurch negativ auf Uploads auswirken und Dateien beschädigen. Stellen Sie bei großen Datei-Uploads sicher, dass Benutzer über Kabelverbindungen zum Netzwerk verfügen, da ein WLAN-Netzwerk schnell überfordert ist. Richtlinien zum Identifizieren von Netzwerkengpässen finden Sie unter [Handbuch zur Asset-Größenanpassung](/help/assets/assets-sizing-guide.md). Informationen zur Bewertung der Netzwerkleistung durch Analyse der Netzwerktopologie finden Sie unter [Überlegungen zum Asset-Netzwerk](/help/assets/assets-network-considerations.md).

Ihre Netzwerkoptimierungsstrategie hängt in erster Linie von der verfügbaren Bandbreite und der Belastung Ihrer [!DNL Experience Manager]-Instanz ab. Allgemeine Konfigurationsoptionen, einschließlich Firewalls oder Proxys, können zur Verbesserung der Netzwerkleistung beitragen. Die folgenden Aspekte sollten berücksichtigt werden:

* Stellen Sie je nach Instanztyp (klein, mittel, groß) sicher, dass Sie über ausreichend Netzwerkbandbreite für Ihre Experience Manager-Instanz verfügen. Eine angemessene Bandbreitenzuordnung ist besonders wichtig, wenn [!DNL Experience Manager] auf AWS gehostet wird.
* Wenn Ihre [!DNL Experience Manager]-Instanz auf AWS gehostet wird, können Sie von einer vielseitigen Skalierungsrichtlinie profitieren. Vergrößern Sie die Instanz, wenn Benutzer eine hohe Belastung erwarten. Verkleinern Sie die Instanz, wenn nur eine mäßige/geringe Belastung erwartet wird.
* HTTPS: Die meisten Benutzer verwenden Firewalls zur Überwachung des HTTP-Verkehrs. Sie können den Prozess des Hochladens beeinträchtigen oder Dateien beim Hochladen beschädigen.
* Upload großer Dateien: Die Benutzer benötigen Kabelverbindungen zum Netzwerk (WLAN-Verbindungen sind schnell gesättigt).

## Workflows {#workflows}

### Verlaufs-Workflows {#transient-workflows}

Stellen Sie nach Möglichkeit den Workflow [!UICONTROL DAM Update Asset] auf Transient ein. Die Einstellung trägt zu einer erheblichen Reduzierung des Overheads bei, der für die Verarbeitung der Workflows benötigt wird, da die Workflows in diesem Fall nicht die normalen Tracking- und Archivierungsprozesse durchlaufen.

1. Navigieren Sie zu `/miscadmin` in der [!DNL Experience Manager]-Bereitstellung unter `https://[aem_server]:[port]/miscadmin`.

1. Erweitern Sie **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL dam]**.

1. Öffnen Sie **[!UICONTROL DAM Update Asset]**. Wechseln Sie im unverankerten Tool-Fenster auf die Registerkarte **[!UICONTROL Seite]** und klicken Sie auf **[!UICONTROL Seiteneigenschaften]**.

1. Wählen Sie **[!UICONTROL Übergangsarbeitsablauf]** und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Einige Funktionen unterstützen keine Verlaufs-Workflows. Wenn für Ihre [!DNL Assets]-Bereitstellung diese Funktionen erforderlich sind, konfigurieren Sie keine vorübergehenden Workflows.

Wenn transiente Workflows nicht verwendet werden können, führen Sie das Workflow-Bereinigen regelmäßig aus, um archivierte [!UICONTROL DAM Update Asset] zu löschen. Workflows stellen Sie sicher, dass die Systemleistung nicht beeinträchtigt wird.

Normalerweise führen Sie die Workflows wöchentlich aus. In ressourcenintensiven Szenarien, z. B. während der umfangreichen Asset-Erfassung, können Sie diese jedoch häufiger ausführen.

Um die Workflow-Bereinigung zu konfigurieren, fügen Sie in der OSGi-Konsole eine neue Adobe Granite-Workflow-Bereinigungskonfiguration hinzu. Konfigurieren und planen Sie im nächsten Schritt den Workflow als Teil des wöchentlichen Wartungsfensters.

Dauert die Bereinigung zu lange, kommt es zu einem Timeout. Daher sollten Sie sicherstellen, dass die Bereinigungsaufträge abgeschlossen sind. So vermeiden Sie, dass Bereinigungs-Workflows aufgrund der hohen Zahl an Workflows nicht abgeschlossen werden können.

Nach dem Ausführen zahlreicher nicht-transienter Workflows (die Workflow-Instanzknoten erstellen) können Sie beispielsweise [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) auf Ad-hoc-Basis ausführen. Es entfernt redundante, abgeschlossene Workflow-Instanzen sofort, ohne dass Sie auf die Ausführung des Adobe Granite-Workflow-Bereinigungsplaners warten müssen.

### Maximal parallel ausführbare Aufträge    {#maximum-parallel-jobs}

Standardmäßig führt [!DNL Experience Manager] maximal parallele Aufträge aus, die der Anzahl der Prozessoren auf dem Server entsprechen. Das Problem bei dieser Einstellung besteht darin, dass während einer hohen Auslastung alle Prozessoren von [!UICONTROL DAM Update Asset] Workflows belegt werden, was die Reaktionsgeschwindigkeit der Benutzeroberfläche verlangsamt und verhindert, dass [!DNL Experience Manager] andere Prozesse ausgeführt werden, die die Serverleistung und -stabilität sichern. Es hat sich bewährt, diese Einstellung so zu wählen, dass nur die Hälfte der auf dem Server verfügbaren Prozessoren verwendet wird:

1. Zugriff auf [!DNL Experience Manager] Autor `https://[aem_server]:[port]/system/console/slingevent`.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]** in jeder Workflow-Warteschlange, die für Ihre Implementierung relevant ist, z. B. **[!UICONTROL Granite Transient Workflow Queue]**.

1. Aktualisieren Sie den Wert von **[!UICONTROL Maximale Anzahl paralleler Aufträge]** und klicken Sie auf **[!UICONTROL Speichern]**.

Diese Einstellung des Werts auf die Hälfte der verfügbaren Prozesse ist für den Anfang eine praktikable Lösung. Unter Umständen müssen Sie diese Zahl jedoch nach oben oder unten anpassen, um den maximalen Durchsatz zu erreichen, und auch an die spezifische Umgebung anpassen. Es gibt separate Warteschlangen für Verlaufs- und Nicht-Verlaufs-Workflows sowie für andere Prozesse wie beispielsweise externe Workflows. Sind mehrere Warteschlangen, die auf 50 % der Prozessoren gesetzt sind, gleichzeitig aktiv, kann es schnell zu einer Überlastung des Systems kommen. Welche Warteschlangen stark ausgelastet sind, hängt in hohem Maße von den Benutzerimplementierungen ab. Sie müssen daher sorgfältig und mit Bedacht konfiguriert werden, um maximale Effizienz zu erreichen, die nicht zu Lasten der Serverstabilität geht.

### Konfiguration von DAM-Update-Asset {#dam-update-asset-configuration}

Der Arbeitsablauf [!UICONTROL DAM-Update-Asset] enthält eine vollständige Reihe von Schritten, die für Aufgaben wie die Dynamic Media-PTIFF-Generierung und [!DNL Adobe InDesign Server]-Integration konfiguriert sind. Die meisten Benutzer benötigen jedoch nicht alle diese Schritte. Adobe empfiehlt, eine benutzerdefinierte Kopie des Workflow-Modells [!UICONTROL DAM Update Asset] zu erstellen und alle unnötigen Schritte zu entfernen. Aktualisieren Sie in diesem Fall die Starter für [!UICONTROL DAM Update Asset], um auf das neue Modell zu verweisen.

Wenn Sie den Arbeitsablauf [!UICONTROL DAM-Update-Asset] intensiv ausführen, kann die Größe Ihres Dateidatatastors stark erhöht werden. Entsprechende Tests von Adobe haben gezeigt, dass die Datenspeichergröße um ca. 400 GB ansteigt, wenn innerhalb von 8 Stunden 5.500 Workflows ausgeführt werden.

Hierbei handelt es sich um einen vorübergehenden Anstieg. Nach Ausführung der Aufgabe zur Speicherbereinigung weist der Datenspeicher wieder seine ursprüngliche Größe auf.

In der Regel wird die Speicherbereinigung wöchentlich gemeinsam mit anderen geplanten Wartungsaufgaben ausgeführt.

Wenn Sie über einen begrenzten Speicherplatz verfügen und [!UICONTROL DAM Update Asset] intensiv Workflows, sollten Sie die Garbage Collection-Aufgabe häufiger planen.

#### Ausgabegenerierung zur Laufzeit {#runtime-rendition-generation}

Kunden verwenden Bilder unterschiedlicher Größen und Formate auf ihrer Website oder zur Weiterleitung an die Geschäftspartner. Da jede Darstellung den Footprint der Assets im Repository vergrößert, empfiehlt Adobe die umsichtige Verwendung dieser Funktion. Um die Menge der Ressourcen zu reduzieren, die für die Verarbeitung und Speicherung von Bildern benötigt wird, können Sie die Bilder statt als Ausgabeformate bei der Erfassung auch zur Laufzeit generieren.

Viele Kunden der Website implementieren ein Bild-Servlet, das Bilder zum Zeitpunkt ihrer Anforderung skaliert und beschneidet und der Veröffentlichungsinstanz damit eine zusätzliche Belastung auferlegt. Wenn diese Bilder zwischengespeichert werden können, lässt sich dieses Problem abmildern.

Eine Alternative besteht darin, die Dynamic Media-Technologie zur gänzlichen Hand-aus-Bild-Manipulation einzusetzen. Darüber hinaus können Sie Markenportal bereitstellen, das nicht nur Verantwortung für die Generierung von Darstellungen aus der [!DNL Experience Manager]-Infrastruktur übernimmt, sondern auch die gesamte Veröffentlichungsstufe.

#### ImageMagick {#imagemagick}

Wenn Sie den Workflow [!UICONTROL DAM Update Asset] anpassen, um Darstellungen mit ImageMagick zu generieren, empfiehlt Adobe, die `policy.xml`-Datei unter `/etc/ImageMagick/` zu ändern. Standardmäßig beansprucht ImageMagick den gesamten verfügbaren Speicherplatz auf dem Betriebssystem-Volume sowie den verfügbaren Arbeitsspeicher. Nehmen Sie die folgenden Konfigurationsänderungen im Abschnitt `policymap` von `policy.xml` vor, um diese Ressourcen zu beschränken.

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
>Eine falsche Konfiguration kann den Server instabil machen, wenn ImageMagick sämtlichen verfügbaren Festplattenspeicher verwendet. Die zur Verarbeitung großer Dateien mit ImageMagick erforderlichen Richtlinienänderungen können sich auf die Leistung von [!DNL Experience Manager] auswirken. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

>[!NOTE]
>
>Die ImageMagick-Dateien `policy.xml` und `configure.xml` stehen unter `/usr/lib64/ImageMagick-&#42;/config/` anstelle von `/etc/ImageMagick/` zur Verfügung. Informationen zum Speicherort der Konfigurationsdateien finden Sie in der [ImageMagick-Dokumentation](https://www.imagemagick.org/script/resources.php).

Wenn Sie [!DNL Experience Manager] unter Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Kundendienst, wenn Sie eine große Anzahl von PSD- oder PSB-Dateien verarbeiten möchten. Wenden Sie sich an den Kundenbetreuer der Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Tools und Modelle für die proprietären Formate der Adobe auszuwählen. [!DNL Experience Manager] kann keine sehr hochauflösenden PSB-Dateien mit mehr als 30000 x 23000 Pixel verarbeiten.

### XMP-Writeback {#xmp-writeback}

Durch XMP Schreibback wird das ursprüngliche Asset bei jeder Änderung der Metadaten in [!DNL Experience Manager] aktualisiert. Dies führt zu Folgendem:

* Das Asset selbst wird geändert.
* Eine Version des Assets wird erstellt.
* [!UICONTROL DAM-Update-Asset wird für das Asset ausgeführt.]

Die aufgeführten Ergebnisse beanspruchen umfangreiche Ressourcen. Daher empfiehlt Adobe, [XMP-Writeback zu deaktivieren](https://helpx.adobe.com/de/experience-manager/kb/disable-xmp-writeback.html), wenn es nicht benötigt wird.

Wenn Sie eine große Menge an Metadaten importieren, kann es zu ressourcenintensiven XMP-Writeback-Aktivitäten kommen, falls das Flag für laufende Workflows gesetzt ist. Planen Sie einen solchen Import während Zeiten geringer Servernutzung, damit die Leistung anderer Benutzer nicht beeinträchtigt wird.

## Replikation {#replication}

Wenn Sie Assets in einer große Menge an veröffentlichten Instanzen replizieren (beispielsweise in einer Sites-Implementierung), empfiehlt Adobe die Kettenreplikation. In diesem Fall wird die Autorinstanz in eine einzelne Veröffentlichungsinstanz repliziert, die wiederum in die anderen Veröffentlichungsinstanzen repliziert wird und so die Autorinstanz freihält.

### Konfiguration der Kettenreplikation    {#configure-chain-replication}

1. Wählen Sie die Veröffentlichungsinstanz, mit der Sie die Replikationen verketten möchten.
1. Fügen Sie dieser Veröffentlichungsinstanz Agenten hinzu, die auf die anderen Veröffentlichungsinstanzen verweisen.
1. Aktivieren Sie für alle anderen Replikationsagenten die Option „Bei Empfang“ auf der Registerkarte „Auslöser“.

>[!NOTE]
>
>Adobe rät von der automatischen Aktivierung von Assets ab. Falls jedoch notwendig, sollte dies der letzte Schritt in einem Workflow, normalerweise „DAM-Update-Asset“, sein.

## Durchsuchen von Indizes    {#search-indexes}

Installieren Sie [die neuesten Service Packs](/help/release-notes/sp-release-notes.md) und leistungsbezogene Hotfixes, da diese häufig Aktualisierungen von Systemindizes beinhalten. Einige Indexoptimierungen finden Sie unter [Tipps zur Leistungsoptimierung](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html).

Erstellen Sie eigene Indizes für Abfragen, die Sie häufig ausführen. Weitere Informationen finden Sie unter [Methoden zur Analyse von langsamen Abfragen](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) und [Erstellen benutzerdefinierter Indizes](/help/sites-deploying/queries-and-indexing.md). Weitere Einblicke in Best Practices bezüglich Abfragen und Indizes finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-Indexkonfigurationen {#lucene-index-configurations}

Einige Optimierungen können mit den Oak Index Konfigurationen durchgeführt werden, die die Leistung von [!DNL Experience Manager Assets] verbessern können. Aktualisieren Sie die Indexkonfigurationen, um die Neuindizierungszeit zu verbessern:

1. Öffnen Sie CRXDe `/crx/de/index.jsp` und melden Sie sich als Administrator an.
1. Gehen Sie zu `/oak:index/lucene`.
1. hinzufügen einer `String[]`-Eigenschaft `excludedPaths` mit den Werten `/var`, `/etc/workflow/instances` und `/etc/replication`.
1. Gehen Sie zu `/oak:index/damAssetLucene`. hinzufügen einer `String[]`-Eigenschaft `includedPaths` mit dem Wert `/content/dam`. Speichern Sie die Änderungen.

Wenn Ihre Benutzer keine Volltextsuche von Assets durchführen müssen, z. B. durch Durchsuchen von Text in PDF-Dokumenten, deaktivieren Sie diese Option. Sie verbessern die Indexleistung, indem Sie die Indexierung im Volltext deaktivieren. Gehen Sie wie folgt vor, um die [!DNL Apache Lucene]-Extraktion zu deaktivieren:

1. Rufen Sie in der [!DNL Experience Manager]-Schnittstelle [!UICONTROL Package Manager] auf.
1. Laden Sie das Paket hoch und installieren Sie es unter [disable_indexingbinarytextraktion-10.zip](assets/disable_indexingbinarytextextraction-10.zip).

### guessTotal {#guess-total}

Verwenden Sie beim Erstellen von Abfragen mit großen Ergebnismengen den Parameter `guessTotal`, um eine übermäßige Belastung des Arbeitsspeichers bei der Ausführung zu vermeiden.

## Bekannte Probleme {#known-issues}

### Große Dateien {#large-files}

Zwei bekannte Probleme beziehen sich auf große Dateien in [!DNL Experience Manager]. Bei Dateien, die größer als 2 GB sind, kann eine kalte Standby-Synchronisierung zu einem Speicherengpass führen. In einigen Fällen wird die Ausführung der Standby-Synchronisierung verhindert. In anderen Fällen stürzt die primäre Instanz ab. Dieses Szenario gilt für alle Dateien in [!DNL Experience Manager], die größer als 2 GB sind, einschließlich Inhaltspakete.

Genauso kann es bei Dateien mit einer Größe von 2 GB bei Verwendung eines freigegebenen S3-Datenspeichers einige Zeit dauern, bis die Datei vollständig vom Cache zum Dateisystem beibehalten wird. Wenn Sie die Binaryless-Replikation verwenden, kann es passieren, dass die binären Daten vor dem Abschluss der Replikation nicht dauerhaft gespeichert werden. Diese Situation kann zu Problemen führen, insbesondere wenn es auf hohe Datenverfügbarkeit ankommt.

## Leistungstests {#performance-testing}

Für jede [!DNL Experience Manager]-Bereitstellung richten Sie ein Leistungstestsystem ein, das Engpässe schnell erkennen und beheben kann. Konzentrieren Sie sich dabei auf die folgenden Schlüsselaspekte.

### Netzwerktests    {#network-testing}

Führen Sie für alle Aspekte, die die für Kunden relevante Netzwerkleistung betreffen, die folgenden Aufgaben aus:

* Testen Sie die Netzwerkleistung im Netzwerk des Kunden.
* Testen Sie die Netzwerkleistung im Adobe-Netzwerk. Arbeiten Sie bei AMS-Kunden mit CSE, um Tests innerhalb des Adobe-Netzwerks durchzuführen.
* Testen Sie die Netzwerkleistung an anderen Zugriffspunkten.
* Testen Sie unter Verwendung eines Benchmark-Tools für Netzwerke.
* Testen Sie mit dem Dispatcher.

### [!DNL Experience Manager] Bereitstellungstests  {#aem-deployment-testing}

Um Latenzzeiten zu minimieren und durch effiziente CPU-Auslastung und Lastenverteilung einen hohen Durchsatz zu erzielen, sollten Sie die Leistung Ihrer [!DNL Experience Manager]-Bereitstellung regelmäßig überwachen. Führen Sie insbesondere die folgenden Aufgaben aus:

* Führen Sie Lastentests für die [!DNL Experience Manager]-Bereitstellung durch.
* Überwachen Sie die Upload-Leistung und die Reaktionsgeschwindigkeit der Benutzeroberfläche.

## [!DNL Experience Manager Assets] Leistungs-Checkliste und Auswirkungen der Asset-Management-Aufgaben  {#checklist}

* Aktivieren Sie HTTPS, um alle Unternehmens-HTTP-Traffic-Sniffer zu umgehen.
* Verwenden Sie eine Kabelverbindung, um umfangreiche Assets hochzuladen.
* Implementieren Sie die Bereitstellung unter Java 8.
* Stellen Sie optimale JVM-Parameter ein..
* Konfigurieren Sie einen Filesystem DataStore oder einen S3-Datenspeicher.
* Deaktivieren Sie die Erzeugung von Teilassets. Ist sie aktiviert, erstellt AEM Workflow für jede Seite eines mehrseitigen Assets ein separates Asset. Jede dieser Seiten ist ein einzelnes Asset, das zusätzlichen Speicherplatz auf der Festplatte benötigt, eine Versionsverwaltung und eine zusätzliche Workflow-Verarbeitung erfordert. Wenn Sie keine separaten Seiten benötigen, deaktivieren Sie die Aktivitäten für die Generierung und Extraktion von Teilassets.
* Aktivieren Sie transiente Workflows.
* Passen Sie die Granite-Workflow-Warteschlangen an, um gleichzeitige Aufträge zu begrenzen.
* Konfigurieren Sie [!DNL ImageMagick], um den Ressourcenverbrauch zu begrenzen.
* Entfernen Sie unnötige Schritte aus dem Arbeitsablauf [!UICONTROL DAM-Update-Asset].
* Konfigurieren des Arbeitsablaufs und der Versionsbereinigung.
* Optimieren Sie Indizes mit den neuesten Service Packs und Hotfixes. Wenden Sie sich an den Kundendienst von Adobe, um weitere verfügbare Indexoptimierungen zu erhalten.
* Optimieren Sie die Abfrageleistung mit guessTotal.
* Wenn Sie [!DNL Experience Manager] so konfigurieren, dass Dateitypen aus dem Inhalt der Dateien erkannt werden (indem Sie **[!UICONTROL Day CQ DAM Mime Type Service]** in der **[!UICONTROL AEM Web Console]** aktivieren), laden Sie viele Dateien während der Nicht-Spitzenzeiten stapelweise hoch, da sie ressourcenintensiv sind.
