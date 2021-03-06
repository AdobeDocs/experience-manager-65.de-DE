---
title: Leistungsoptimierung [!DNL Assets].
description: Empfehlungen und Hinweise zu [!DNL Experience Manager] Konfiguration, Änderungen an Hardware-, Software- und Netzwerkkomponenten, um Engpässe zu beseitigen und die Leistung von [!DNL Experience Manager Assets].
contentOwner: AG
mini-toc-levels: 1
role: Architect, Admin
feature: Asset Management
exl-id: 1d9388de-f601-42bf-885b-6a7c3236b97e
source-git-commit: 35639a818f58923ae9ad099752d359e7795be60b
workflow-type: tm+mt
source-wordcount: '2741'
ht-degree: 52%

---

<!-- TBD: Get reviewed by engineering. -->

# [!DNL Adobe Experience Manager Assets] Handbuch zur Leistungsoptimierung {#assets-performance-tuning-guide}

Ein [!DNL Experience Manager Assets] -Setup enthält eine Reihe von Hardware-, Software- und Netzwerkkomponenten. Je nach Ihrem Bereitstellungsszenario benötigen Sie möglicherweise bestimmte Konfigurationsänderungen an den Hardware-, Software- und Netzwerkkomponenten, um Leistungsengpässe zu vermeiden.

Darüber hinaus hilft die Identifizierung und Einhaltung bestimmter Richtlinien zur Hardware- und Softwareoptimierung dabei, eine solide Grundlage zu schaffen, die Ihre [!DNL Experience Manager Assets] Implementierung, um Erwartungen hinsichtlich Leistung, Skalierbarkeit und Zuverlässigkeit zu erfüllen.

Schlechte Leistung in [!DNL Experience Manager Assets] kann sich auf die Benutzererfahrung im Hinblick auf interaktive Leistung, Asset-Verarbeitung, Download-Geschwindigkeit und andere Bereiche auswirken.

Daher gehört die Leistungsoptimierung zu den grundlegenden Aufgaben, bevor Sie Zielmetriken für Ihre Projekte erstellen.

In den folgenden Schlüsselbereichen sollten Sie besonders darauf achten, dass Leistungsprobleme erkannt und behoben werden, bevor sie sich auf das Benutzererlebnis auswirken.

## Plattform {#platform}

Obwohl Experience Manager auf einer Reihe von Plattformen unterstützt wird, hat Adobe die größte Unterstützung für native Tools unter Linux und Windows gefunden, was zu einer optimalen Leistung und einfachen Implementierung beiträgt. Idealerweise sollten Sie ein 64-Bit-Betriebssystem bereitstellen, um die hohen Speicheranforderungen eines [!DNL Experience Manager Assets] Implementierung. Wie bei jeder Experience Manager-Implementierung sollten Sie TarMK möglichst implementieren. TarMK kann zwar nicht über eine einzelne Autoreninstanz skaliert werden, erzielt jedoch erfahrungsgemäß eine bessere Leistung als MongoMK. Sie können TarMK-Ablade-Instanzen hinzufügen, um die Verarbeitungsleistung Ihres Workflows zu erhöhen. [!DNL Experience Manager Assets] Implementierung.

### Temporärer Ordner {#temp-folder}

Verwenden Sie zur Verbesserung der Asset-Upload-Zeit Hochleistungsspeicher für den temporären Java-Ordner. Unter Linux und Windows können Sie beispielsweise ein RAM- oder SSD-Laufwerk verwenden. In Cloud-basierten Umgebungen kann ein äquivalenter Hochgeschwindigkeitsspeicher verwendet werden. In Amazon EC2 beispielsweise wird eine [Kurzfahrwerk](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) -Laufwerk kann für den temporären Ordner verwendet werden.

Bei einer großen Speicherkapazität des Servers kann ein RAM-Laufwerk konfiguriert werden. Führen Sie unter Linux die folgenden Befehle aus, um ein RAM-Laufwerk von 8 GB zu erstellen:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Verwenden Sie unter Windows OS einen Treiber eines Drittanbieters, um ein RAM-Laufwerk zu erstellen, oder verwenden Sie einfach Hochleistungsspeicher wie SSD.

Sobald das temporäre Hochleistungs-Volume bereit ist, legen Sie den JVM-Parameter fest. `-Djava.io.tmpdir`. Beispielsweise können Sie den JVM-Parameter unten zum `CQ_JVM_OPTS` in der Variablen `bin/start` Skript von [!DNL Experience Manager]:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-Konfiguration {#java-configuration}

### Java-Version {#java-version}

Adobe empfiehlt die Bereitstellung [!DNL Experience Manager Assets] auf Java 8 für optimale Leistung.

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

Es wird empfohlen, den Datenspeicher vom Segmentspeicher zu trennen. [!DNL Experience Manager Assets] Benutzer. Außerdem kann die Leistung durch die Konfiguration der Parameter `maxCachedBinarySize` und `cacheSizeInMB` maximiert werden. Stellen Sie `maxCachedBinarySize` auf die kleinste im Cache unterstützte Dateigröße ein. Geben Sie die Größe des Arbeitsspeicher-Cache für den Datenspeicher in `cacheSizeInMB` ein. Adobe empfiehlt, diesen Wert auf 2–10 Prozent der gesamten Heap-Größe einzustellen. Mithilfe von Last-/Leistungstests lässt sich die ideale Einstellung herausfinden.

### Konfigurieren der Maximalgröße des gepufferten Bilder-Caches   {#configure-the-maximum-size-of-the-buffered-image-cache}

Beim Hochladen großer Mengen von Assets in [!DNL Adobe Experience Manager], um unerwartete Spitzen bei der Speicherbelegung zu ermöglichen und zu verhindern, dass JVM mit OutOfMemoryErrors fehlschlägt, reduzieren Sie die konfigurierte Maximalgröße des gepufferten Bild-Caches. Betrachten wir ein Beispiel mit einem System, das über eine maximale Heap-Größe (-`Xmx`param) von 5 GB verfügt und bei dem der Oak-Blob-Cache auf 1 GB und der Dokumenten-Cache auf 2 GB eingestellt ist. In diesem Fall würde der gepufferte Cache das Maximum von 1,25 GB Speicher in Anspruch nehmen, wodurch nur 0,75 GB Speicher für unerwartete Spitzen verblieben.

Konfigurieren Sie die Größe des gepufferten Cache in der OSGi-Webkonsole. Legen Sie bei `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache` die Eigenschaft `cq.dam.image.cache.max.memory` in Byte fest. 1073741824 entspricht beispielsweise 1 GB (1024 x 1024 x 1024 = 1 GB).

Ab Experience Manager 6.1 SP1, wenn Sie eine `sling:osgiConfig` -Knoten für die Konfiguration dieser Eigenschaft verwenden, stellen Sie sicher, dass Sie den Datentyp auf &quot;Long&quot;einstellen. Weitere Details finden Sie unter [CQBufferedImageCache belegt beim Asset-Upload den Heap](https://helpx.adobe.com/de/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Gemeinsame Datenspeicher   {#shared-data-stores}

Mit der Implementierung eines S3-Datenspeichers oder Shared File Datastore sparen Sie Speicherplatz auf der Festplatte und erhöhen den Netzwerkdurchsatz in großen Implementierungen. Weitere Informationen zu den Vor- und Nachteilen der Verwendung eines gemeinsamen Datenspeichers finden Sie unter [Handbuch zur Dimensionierung von Assets](/help/assets/assets-sizing-guide.md).

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

Adobe empfiehlt die Aktivierung von HTTPS, da viele Unternehmen über Firewalls verfügen, die den HTTP-Verkehr überprüfen und sich dadurch negativ auf Uploads auswirken und Dateien beschädigen. Stellen Sie bei großen Datei-Uploads sicher, dass Benutzer über Kabelverbindungen zum Netzwerk verfügen, da ein WLAN-Netzwerk schnell überfordert ist. Richtlinien zur Ermittlung von Netzwerkengpässen finden Sie unter [Handbuch zur Dimensionierung von Assets](/help/assets/assets-sizing-guide.md). Informationen zur Bewertung der Netzwerkleistung durch Analyse der Netzwerktopologie finden Sie unter [Überlegungen zum Assets-Netzwerk](/help/assets/assets-network-considerations.md).

In erster Linie hängt Ihre Netzwerkoptimierungsstrategie von der verfügbaren Bandbreite und der Belastung Ihrer [!DNL Experience Manager] -Instanz. Allgemeine Konfigurationsoptionen, einschließlich Firewalls oder Proxys, können zur Verbesserung der Netzwerkleistung beitragen. Die folgenden Aspekte sollten berücksichtigt werden:

* Stellen Sie je nach Instanztyp (klein, mittel, groß) sicher, dass Sie über ausreichend Netzwerkbandbreite für Ihre Experience Manager-Instanz verfügen. Eine angemessene Bandbreitenzuordnung ist besonders wichtig, wenn [!DNL Experience Manager] wird auf AWS gehostet.
* Wenn [!DNL Experience Manager] -Instanz auf AWS gehostet wird, können Sie von einer flexiblen Skalierungsrichtlinie profitieren. Vergrößern Sie die Instanz, wenn Benutzer eine hohe Belastung erwarten. Verkleinern Sie die Instanz, wenn nur eine mäßige/geringe Belastung erwartet wird.
* HTTPS: Die meisten Benutzer verwenden Firewalls zur Überwachung des HTTP-Verkehrs. Sie können den Prozess des Hochladens beeinträchtigen oder Dateien beim Hochladen beschädigen.
* Upload großer Dateien: Die Benutzer benötigen Kabelverbindungen zum Netzwerk (WLAN-Verbindungen sind schnell gesättigt).

## Workflows   {#workflows}

### Verlaufs-Workflows {#transient-workflows}

Legen Sie nach Möglichkeit die [!UICONTROL DAM-Update-Asset] Workflow auf Übergangs. Die Einstellung trägt zu einer erheblichen Reduzierung des Overheads bei, der für die Verarbeitung der Workflows benötigt wird, da die Workflows in diesem Fall nicht die normalen Tracking- und Archivierungsprozesse durchlaufen.

1. Navigieren Sie zu `/miscadmin` im [!DNL Experience Manager] Bereitstellung unter `https://[aem_server]:[port]/miscadmin`.

1. Erweitern **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL dam]**.

1. Öffnen **[!UICONTROL DAM-Update-Asset]**. Wechseln Sie im unverankerten Tool-Fenster auf die Registerkarte **[!UICONTROL Seite]** und klicken Sie auf **[!UICONTROL Seiteneigenschaften]**.

1. Auswählen **[!UICONTROL Übergangs-Workflow]** und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Einige Funktionen unterstützen keine Verlaufs-Workflows. Wenn [!DNL Assets] Die Implementierung erfordert diese Funktionen, konfigurieren Sie keine Übergangs-Workflows.

In Fällen, in denen keine Verlaufs-Workflows verwendet werden können, führen Sie regelmäßig die Workflow-Bereinigung durch, um archivierte Workflows zu löschen [!UICONTROL DAM-Update-Asset] Workflows, um sicherzustellen, dass die Systemleistung nicht beeinträchtigt wird.

Führen Sie die Bereinigungs-Workflows normalerweise wöchentlich aus. In ressourcenintensiven Szenarien wie der umfangreichen Asset-Erfassung können Sie diese jedoch häufiger ausführen.

Um die Workflow-Bereinigung zu konfigurieren, fügen Sie in der OSGi-Konsole eine neue Adobe Granite-Workflow-Bereinigungskonfiguration hinzu. Konfigurieren und planen Sie im nächsten Schritt den Workflow als Teil des wöchentlichen Wartungsfensters.

Dauert die Bereinigung zu lange, kommt es zu einem Timeout. Daher sollten Sie sicherstellen, dass die Bereinigungsaufträge abgeschlossen sind. So vermeiden Sie, dass Bereinigungs-Workflows aufgrund der hohen Zahl an Workflows nicht abgeschlossen werden können.

Nach Ausführung zahlreicher nicht transienter Workflows (die Workflow-Instanzknoten erstellen) können Sie beispielsweise Folgendes ausführen: [Workflow-Remover von ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) auf Ad-hoc-Basis. Es entfernt redundante, abgeschlossene Workflow-Instanzen sofort, ohne dass Sie auf die Ausführung des Adobe Granite-Workflow-Bereinigungsplaners warten müssen.

### Maximal parallel ausführbare Aufträge   {#maximum-parallel-jobs}

Standardmäßig [!DNL Experience Manager] führt eine maximale Anzahl paralleler Aufträge aus, die der Anzahl der Prozessoren auf dem Server entspricht. Das Problem bei dieser Einstellung besteht darin, dass in Zeiten hoher Auslastung alle Prozessoren von [!UICONTROL DAM-Update-Asset] Workflows, die Reaktionsfähigkeit der Benutzeroberfläche verlangsamen und verhindern [!DNL Experience Manager] andere Prozesse ausführen, die die Serverleistung und -stabilität schützen. Es hat sich bewährt, diese Einstellung so zu wählen, dass nur die Hälfte der auf dem Server verfügbaren Prozessoren verwendet wird:

1. on [!DNL Experience Manager] Autor, Zugriff `https://[aem_server]:[port]/system/console/slingevent`.

1. Klicken **[!UICONTROL Bearbeiten]** für jede Workflow-Warteschlange, die für Ihre Implementierung relevant ist, z. B. **[!UICONTROL Granite-Verlaufs-Workflow-Warteschlange]**.

1. Aktualisieren Sie den Wert von **[!UICONTROL Maximale Anzahl paralleler Aufträge]** und klicken Sie auf **[!UICONTROL Speichern]**.

Diese Einstellung des Werts auf die Hälfte der verfügbaren Prozesse ist für den Anfang eine praktikable Lösung. Unter Umständen müssen Sie diese Zahl jedoch nach oben oder unten anpassen, um den maximalen Durchsatz zu erreichen, und auch an die spezifische Umgebung anpassen. Es gibt separate Warteschlangen für Verlaufs- und Nicht-Verlaufs-Workflows sowie für andere Prozesse wie beispielsweise externe Workflows. Sind mehrere Warteschlangen, die auf 50 % der Prozessoren gesetzt sind, gleichzeitig aktiv, kann es schnell zu einer Überlastung des Systems kommen. Welche Warteschlangen stark ausgelastet sind, hängt in hohem Maße von den Benutzerimplementierungen ab. Sie müssen daher sorgfältig und mit Bedacht konfiguriert werden, um maximale Effizienz zu erreichen, die nicht zu Lasten der Serverstabilität geht.

### Konfiguration von DAM-Update-Asset {#dam-update-asset-configuration}

Die [!UICONTROL DAM-Update-Asset] Der Workflow enthält eine vollständige Suite von Schritten, die für Aufgaben wie die Dynamic Media-PTIFF-Generierung und [!DNL Adobe InDesign Server] Integration. Die meisten Benutzer benötigen jedoch nicht alle diese Schritte. Adobe empfiehlt, eine benutzerdefinierte Kopie der [!UICONTROL DAM-Update-Asset] Workflow-Modell verwenden und alle unnötigen Schritte entfernen. Aktualisieren Sie in diesem Fall die Starter für [!UICONTROL DAM-Update-Asset] , um auf das neue Modell zu verweisen.

Ausführen der [!UICONTROL DAM-Update-Asset] Arbeitsabläufe können die Größe Ihres Dateidatenspeichers stark erhöhen. Entsprechende Tests von Adobe haben gezeigt, dass die Datenspeichergröße um ca. 400 GB ansteigt, wenn innerhalb von 8 Stunden 5.500 Workflows ausgeführt werden.

Hierbei handelt es sich um einen vorübergehenden Anstieg. Nach Ausführung der Aufgabe zur Speicherbereinigung weist der Datenspeicher wieder seine ursprüngliche Größe auf.

In der Regel wird die Speicherbereinigung wöchentlich gemeinsam mit anderen geplanten Wartungsaufgaben ausgeführt.

Wenn Sie eingeschränkten Speicherplatz haben und [!UICONTROL DAM-Update-Asset] Überlegen Sie bei intensiven Workflows, die Speicherbereinigung häufiger zu planen.

#### Ausgabegenerierung zur Laufzeit {#runtime-rendition-generation}

Kunden verwenden Bilder unterschiedlicher Größen und Formate auf ihrer Website oder zur Weiterleitung an die Geschäftspartner. Da jede Darstellung den Footprint der Assets im Repository vergrößert, empfiehlt Adobe die umsichtige Verwendung dieser Funktion. Um die Menge der Ressourcen zu reduzieren, die für die Verarbeitung und Speicherung von Bildern benötigt wird, können Sie die Bilder statt als Ausgabeformate bei der Erfassung auch zur Laufzeit generieren.

Viele Kunden der Website implementieren ein Bild-Servlet, das Bilder zum Zeitpunkt ihrer Anforderung skaliert und beschneidet und der Veröffentlichungsinstanz damit eine zusätzliche Belastung auferlegt. Wenn diese Bilder zwischengespeichert werden können, lässt sich dieses Problem abmildern.

Ein alternativer Ansatz besteht darin, die Dynamic Media-Technologie zu verwenden, um die Bildbearbeitung vollständig abzugeben. Darüber hinaus können Sie Brand Portal bereitstellen, das nicht nur die Verantwortung für die Generierung von Ausgabedarstellungen vom [!DNL Experience Manager] Infrastruktur, aber auch die gesamte Veröffentlichungsstufe.

#### ImageMagick {#imagemagick}

Wenn Sie die [!UICONTROL DAM-Update-Asset] Workflow zum Generieren von Ausgabeformaten mit ImageMagick, empfiehlt Adobe, die `policy.xml` Datei unter `/etc/ImageMagick/`. Standardmäßig beansprucht ImageMagick den gesamten verfügbaren Speicherplatz auf dem Betriebssystem-Volume sowie den verfügbaren Arbeitsspeicher. Nehmen Sie die folgenden Konfigurationsänderungen in der `policymap` Abschnitt `policy.xml` um diese Ressourcen zu beschränken.

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
>Eine falsche Konfiguration kann den Server instabil machen, wenn ImageMagick sämtlichen verfügbaren Festplattenspeicher verwendet. Die Richtlinienänderungen, die zur Verarbeitung großer Dateien mit ImageMagick erforderlich sind, können sich auf die [!DNL Experience Manager] Leistung. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

>[!NOTE]
>
>ImageMagick `policy.xml` und `configure.xml` Dateien sind verfügbar unter `/usr/lib64/ImageMagick-&#42;/config/` anstelle von `/etc/ImageMagick/`.Siehe [ImageMagick-Dokumentation](https://www.imagemagick.org/script/resources.php) für den Speicherort der Konfigurationsdateien.

Wenn Sie [!DNL Experience Manager] Wenden Sie sich in Adobe Managed Services (AMS) an den Kundensupport von Adobe, wenn Sie eine Vielzahl großer PSD- oder PSB-Dateien verarbeiten möchten. Wenden Sie sich an den Support-Mitarbeiter von Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Tools und Modelle für die proprietären Formate von Adobe auszuwählen. [!DNL Experience Manager] kann keine sehr hochauflösenden PSB-Dateien verarbeiten, die mehr als 30000 x 23000 Pixel sind.

### XMP-Writeback {#xmp-writeback}

XMP Writeback aktualisiert das ursprüngliche Asset, sobald die Metadaten in [!DNL Experience Manager], was zu Folgendem führt:

* Das Asset selbst wird geändert.
* Eine Version des Assets wird erstellt.
* [!UICONTROL DAM-Update-Asset wird für das Asset ausgeführt.]

Die aufgeführten Ergebnisse beanspruchen umfangreiche Ressourcen. Daher empfiehlt Adobe, [XMP-Writeback zu deaktivieren](https://helpx.adobe.com/de/experience-manager/kb/disable-xmp-writeback.html), wenn es nicht benötigt wird.

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

Installieren [die neuesten Service Packs](/help/release-notes/release-notes.md) und leistungsbezogene Hotfixes, da diese häufig Aktualisierungen von Systemindizes enthalten. Siehe [Tipps zur Leistungsoptimierung](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html) für einige Indexoptimierungen.

Erstellen Sie eigene Indizes für Abfragen, die Sie häufig ausführen. Weitere Informationen finden Sie unter [Methoden zur Analyse von langsamen Abfragen](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) und [Erstellen benutzerdefinierter Indizes](/help/sites-deploying/queries-and-indexing.md). Weitere Einblicke in Best Practices bezüglich Abfragen und Indizes finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-Indexkonfigurationen {#lucene-index-configurations}

Einige Optimierungen können an den Oak-Indexkonfigurationen vorgenommen werden, die zur Verbesserung beitragen können [!DNL Experience Manager Assets] Leistung. Aktualisieren Sie die Indexkonfigurationen, um die Neuindizierungszeit zu verbessern:

1. CRXDe öffnen `/crx/de/index.jsp` und melden Sie sich als Administrator an.
1. Navigieren Sie zu `/oak:index/lucene`.
1. Hinzufügen einer `String[]` property `excludedPaths` mit Werten `/var`, `/etc/workflow/instances`und `/etc/replication`.
1. Navigieren Sie zu `/oak:index/damAssetLucene`. Hinzufügen einer `String[]` property `includedPaths` mit Wert `/content/dam`. Speichern Sie die Änderungen.

Wenn Ihre Benutzer keine Volltextsuche nach Assets durchführen müssen, z. B. durch die Textsuche in PDF-Dokumenten, deaktivieren Sie sie. Sie verbessern die Indexleistung, indem Sie die Volltextindizierung deaktivieren. So deaktivieren Sie [!DNL Apache Lucene] Textextraktion, führen Sie die folgenden Schritte aus:

1. In [!DNL Experience Manager] Benutzeroberfläche, Zugriff [!UICONTROL Package Manager].
1. Laden Sie das Paket hoch und installieren Sie es unter [disable_indexingbinarytextextraktion-10.zip](assets/disable_indexingbinarytextextraction-10.zip).

### guessTotal {#guess-total}

Verwenden Sie beim Erstellen von Abfragen mit großen Ergebnismengen den Parameter `guessTotal`, um eine übermäßige Belastung des Arbeitsspeichers bei der Ausführung zu vermeiden.

## Bekannte Probleme {#known-issues}

### Große Dateien {#large-files}

Zwei bekannte Probleme beziehen sich auf große Dateien in [!DNL Experience Manager]. Bei Dateien, die größer als 2 GB sind, kann eine kalte Standby-Synchronisierung zu einem Speicherengpass führen. In einigen Fällen wird die Ausführung der Standby-Synchronisierung verhindert. In anderen Fällen stürzt die primäre Instanz ab. Dieses Szenario gilt für alle Dateien in [!DNL Experience Manager] , die größer als 2 GB ist, einschließlich Inhaltspaketen.

Wenn Dateien bei Verwendung eines freigegebenen S3-Datenspeichers eine Größe von 2 GB erreichen, kann es auch einige Zeit dauern, bis die Datei vollständig aus dem Cache in das Dateisystem persistiert wird. Wenn Sie die Binaryless-Replikation verwenden, kann es passieren, dass die binären Daten vor dem Abschluss der Replikation nicht dauerhaft gespeichert werden. Diese Situation kann zu Problemen führen, insbesondere wenn es auf hohe Datenverfügbarkeit ankommt.

## Leistungstests {#performance-testing}

Für jeden [!DNL Experience Manager] Einführung eines Leistungstestsystems, das Engpässe schnell erkennen und beheben kann. Konzentrieren Sie sich dabei auf die folgenden Schlüsselaspekte.

### Netzwerktests   {#network-testing}

Führen Sie für alle Aspekte, die die für Kunden relevante Netzwerkleistung betreffen, die folgenden Aufgaben aus:

* Testen Sie die Netzwerkleistung im Netzwerk des Kunden.
* Testen Sie die Netzwerkleistung im Adobe-Netzwerk. Arbeiten Sie bei AMS-Kunden mit CSE, um Tests innerhalb des Adobe-Netzwerks durchzuführen.
* Testen Sie die Netzwerkleistung an anderen Zugriffspunkten.
* Testen Sie unter Verwendung eines Benchmark-Tools für Netzwerke.
* Testen Sie mit dem Dispatcher.

### [!DNL Experience Manager] Bereitstellungstests {#aem-deployment-testing}

Um Latenzzeiten zu minimieren und durch effiziente CPU-Auslastung und Lastverteilung einen hohen Durchsatz zu erzielen, überwachen Sie die Leistung Ihrer [!DNL Experience Manager] regelmäßig implementieren. Führen Sie insbesondere die folgenden Aufgaben aus:

* Führen Sie Belastungstests für die [!DNL Experience Manager] Implementierung.
* Überwachen Sie die Upload-Leistung und die Reaktionsfähigkeit der Benutzeroberfläche.

## [!DNL Experience Manager Assets] Leistungsprüfliste und Auswirkung von Asset-Management-Aufgaben {#checklist}

* Aktivieren Sie HTTPS, um alle geschäftlichen HTTP-Traffic-Sniffer zu umgehen.
* Verwenden Sie eine Kabelverbindung, um umfangreiche Assets hochzuladen.
* Implementieren Sie die Bereitstellung unter Java 8.
* Stellen Sie optimale JVM-Parameter ein..
* Konfigurieren Sie einen Dateisystem-DataStore oder einen S3-Datenspeicher.
* Die Erstellung von Unter-Assets deaktivieren. Ist diese Option aktiviert, erstellt AEM Workflow für jede Seite eines mehrseitigen Assets ein separates Asset. Jede dieser Seiten ist ein einzelnes Asset, das zusätzlichen Speicherplatz beansprucht, Versionierung und zusätzliche Workflow-Verarbeitung erfordert. Wenn Sie keine separaten Seiten benötigen, deaktivieren Sie die Aktivitäten zum Generieren von Unter-Assets und zum Extrahieren von Seiten.
* Aktivieren Sie Übergangs-Workflows.
* Passen Sie die Granite-Workflow-Warteschlangen an, um gleichzeitige Aufträge zu begrenzen.
* Konfigurieren [!DNL ImageMagick] , um den Ressourcenverbrauch zu begrenzen.
* Entfernen Sie unnötige Schritte aus dem [!UICONTROL DAM-Update-Asset] Arbeitsablauf.
* Konfigurieren Sie den Workflow und die Versionsbereinigung.
* Optimieren Sie Indizes mit den neuesten Service Packs und Hotfixes. Wenden Sie sich an die Adobe-Kundenunterstützung , um weitere verfügbare Indexoptimierungen zu erhalten.
* Optimieren Sie die Abfrageleistung mit guessTotal.
* Wenn Sie [!DNL Experience Manager] zur Erkennung von Dateitypen aus dem Inhalt der Dateien (durch Aktivierung der **[!UICONTROL Day CQ DAM Mime Type Service]** im **[!UICONTROL AEM Web-Konsole]**), laden Sie viele Dateien außerhalb der Spitzenzeiten stapelweise hoch, da dies ressourcenintensiv ist.
