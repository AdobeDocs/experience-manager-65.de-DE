---
title: '[!DNL Assets] Größenleitfaden'
description: Best Practices zur Ermittlung effizienter Metriken zur Schätzung der Infrastruktur und der Ressourcen, die für die Bereitstellung [!DNL Adobe Experience Manager Assets]erforderlich sind.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 62%

---


# [!DNL Assets] Größenleitfaden {#assets-sizing-guide}

When sizing the environment for an [!DNL Adobe Experience Manager Assets] implementation, it is important to ensure that there are sufficient resources available in terms of disk, CPU, memory, IO, and network throughput. Zur Dimensionierung dieser Ressourcen muss bekannt sein, wie viele Assets in das System geladen werden. Wenn keine bessere Metrik verfügbar ist, können Sie die Größe der vorhandenen Bibliothek durch das Alter der Bibliothek dividieren, um die Rate zu ermitteln, mit der Assets erstellt werden.

## Festplatte {#disk}

### Datenspeicher {#datastore}

A common mistake made when sizing the required disk space for an [!DNL Assets] implementation is to base the calculations on the size of the raw images to be ingested into the system. By default, [!DNL Experience Manager] creates three renditions in addition to the original image for use in rendering the [!DNL Experience Manager] user interface elements. In vorherigen Implementierungen haben sich diese Wiedergaben als doppelt so groß wie die aufgenommenen Assets herausgestellt. 

Die meisten Benutzer definieren benutzerdefinierte Wiedergaben neben den standardmäßig verfügbaren Wiedergaben. In addition to the renditions, [!DNL Assets] lets you extract sub-assets from common file types, such as [!DNL Adobe InDesign] and [!DNL Adobe Illustrator].

Finally, versioning capabilities of [!DNL Experience Manager] store duplicates of the assets in the version history. Sie können die Versionen so konfigurieren, dass Bereinigungen häufig durchgeführt werden. Jedoch entscheiden sich viele Benutzer für eine längere Aufbewahrung der Versionen im System, wodurch zusätzlicher Speicherplatz belegt wird.

Angesichts dieser Faktoren benötigen Sie eine Methodik für eine ausreichend genaue Berechnung des Speicherplatzes, um Benutzer-Assets aufbewahren zu können.

1. Bestimmen Sie die Größe und die Anzahl der Assets, die in das System geladen werden.
1. Get a representative sample of the assets to be uploaded into [!DNL Experience Manager]. Wenn Sie beispielsweise PSD-, JPG-, AI- und PDF-Dateien in das System laden möchten, benötigen Sie mehrere Beispielbilder für jedes Dateiformat. Außerdem sollten diese Stichproben repräsentativ für die verschiedenen Dateigrößen und die Komplexität der Bilder sein.
1. Definieren Sie die zu verwendenden Wiedergaben.
1. Erstellen Sie die Darstellungen in [!DNL Experience Manager] Verwendung [!DNL ImageMagick] oder [!DNL Adobe Creative Cloud] Anwendung. Erstellen Sie neben den von den Benutzern angegebenen Wiedergaben sofort einsetzbare Standardwiedergaben. Für Benutzer, die Scene7 implementieren, können Sie die IC-Binärdatei verwenden, um die PTIFF-Darstellungen zu generieren, die in Experience Manager gespeichert werden sollen.
1. Wenn Sie die Verwendung von Unter-Assets beabsichtigen, generieren Sie diese für die entsprechenden Dateitypen.
1. Vergleichen Sie die Größe der Ausgabebilder, Wiedergaben und Unter-Assets mit den Originalbildern. So können Sie den erwarteten Wachstumsfaktor beim Laden des Systems generieren. Wenn Sie z. B. Wiedergaben und Unter-Assets mit einer kombinierten Größe von 3 GB nach der Verarbeitung von 1 GB an Assets erzeugen, lautet der Wiedergabe-Wachstumsfaktor 3.
1. Ermitteln Sie, wie lange die einzelnen Asset-Versionen maximal im System aufbewahrt werden sollen.
1. Ermitteln Sie, wie oft vorhandene Assets im System geändert werden. If [!DNL Experience Manager] is used as a collaboration hub in creative workflows, the amount of changes are high. Wenn nur fertiggestellte Assets in das System hochgeladen werden, ist diese Zahl wesentlich niedriger.
1. Ermitteln Sie, wie viele Assets jeden Monat in das System geladen werden. Wenn Sie sich nicht sicher sind, bestimmen Sie die Anzahl der aktuell verfügbaren Assets und dividieren Sie diese Zahl durch das Alter des ältesten Assets, um einen ungefähren Wert zu berechnen. 

Mithilfe der obigen Schritte können Sie Folgendes feststellen:

* Rohgröße der zu ladenden Assets.
* Anzahl der zu ladenden Assets.
* Wiedergabe-Wachstumsfaktor.
* Anzahl der Asset-Änderungen pro Monat.
* Anzahl der Monate für die Aufbewahrung von Asset-Versionen.
* Anzahl der neu geladenen Assets pro Monat.
* Wachstumsjahre für die Raumordnung der Datenspeicherung.

Sie können diese Zahlen in der Tabelle zur Netzwerkdimensionierung angeben, um den Gesamtspeicherbedarf für den Datenspeicher zu ermitteln. It is also a useful tool to determine the impact of maintaining asset versions or modifying assets in [!DNL Experience Manager] on disk growth.

Die in das Tool aufgefüllten Beispieldaten zeigen, wie wichtig die Ausführung der genannten Schritte ist. Wenn Sie den Datenspeicher allein basierend auf dem Ladevorgang der Rohbilder (1 TB) bemessen, ist eine Unterbewertung der Repositorygröße um dem Faktor 15 möglich.

[Datei laden](assets/disk_sizing_tool.xlsx)

### Shared datastores {#shared-datastores}

Bei großen Datenspeichern können Sie einen freigegebenen Datenspeicher entweder über einen freigegebenen Dateidatastore auf einem angeschlossenen Laufwerk oder über einen Amazon S3-Datenspeicher implementieren. In diesem Fall müssen einzelne Instanzen keine Kopie der Binärdateien aufbewahren. Darüber hinaus erleichtert ein freigegebener Datenspeicher die Replikation ohne Binärdatei und verringert die Bandbreite, die zum Replizieren von Assets für die Veröffentlichung von Umgebung verwendet wird.

#### Anwendungsfälle   {#use-cases}

Der Datenspeicher kann gemeinsam von primärer und Standby-Autoreninstanz genutzt werden, um den zeitlichen Aufwand zum Aktualisieren der Standby-Instanz mit Änderungen der primären Instanz zu minimieren. Sie können den Datenspeicher zudem zwischen Autor- und Veröffentlichungsinstanzen freigeben, um den Traffic während der Replikation zu minimieren.

#### Nachteile {#drawbacks}

Aufgrund gewisser Fallstricke wird die Freigabe eines Datenspeichers nicht in allen Fällen empfohlen.

#### Single point of failure {#single-point-of-failure}

Mit einem freigegebenen Datenspeicher entsteht ein Single Point of Failure in einer Infrastruktur. Stellen Sie sich ein Szenario vor, bei dem Ihr System eine Autoreninstanz und zwei Veröffentlichungsinstanzen aufweist, jeweils mit einem eigenen Datenspeicher. Stürzt einer der Datenspeicher ab, können die beiden anderen nach wie vor ausgeführt werden. Wenn der Datenspeicher jedoch gemeinsam genutzt wird, kann der Ausfall einer einzigen Festplatte die gesamte Infrastruktur zum Erliegen bringen. Stellen Sie daher sicher, dass Sie eine Sicherung des freigegebenen Datenspeichers aufbewahren, über die Sie den Datenspeicher schnell wiederherstellen können.

Den AWS S3-Dienst für freigegebene Datenspeicher bereitzustellen, wird vorgezogen, weil hierdurch die Wahrscheinlichkeit eines Ausfalls gegenüber normalen Festplattenarchitekturen deutlich reduziert wird.

#### Increased complexity {#increased-complexity}

Freigegebene Datenspeicher erhöhen ebenfalls die Komplexität solcher Vorgänge, etwa der automatischen Speicherbereinigung. Normalerweise kann die automatische Speicherbereinigung für einen Standalone-Datenspeicher mit einem einzigen Klick initiiert werden. Allerdings setzen freigegebene Datenspeicher zusätzlich zu der auf jedem Knoten tatsächlich durchgeführten Bereinigung Mark-Sweep-Vorgänge auf jedem Mitglied voraus, das den Datenspeicher nutzt.

Bei AWS-Operationen kann die Implementierung eines zentralen Standorts (über Amazon S3), anstatt ein RAID-Array mit EBS-Volumes zu erstellen, die Komplexität und die Betriebsrisiken des Systems erheblich ausgleichen.

#### Performance concerns {#performance-concerns}

Bei einem freigegebenen Datenspeicher müssen die Binärdateien auf einem Laufwerk gespeichert werden, das an ein Netzwerk angebunden und für alle Instanzen freigegeben ist. Da der Zugriff auf diese Binärdateien über ein Netzwerk erfolgt, wird die Systemleistung beeinträchtigt. Eine schnelle Netzwerkverbindung zu einem schnellen Festplattenarray kann diesen Effekt teilweise auffangen. Dies ist jedoch eine teure Angelegenheit. Im Falle von AWS-Vorgängen liegen alle Festplatten remote vor, sodass eine Netzwerkanbindung erforderlich ist. Auf flüchtigen Volumes gehen Daten beim Starten und Stoppen von Instanzen verloren.

#### Latenz {#latency}

Latenz in S3-Implementierungen ist auf die im Hintergrund durchgeführten Schreibthreads zurückzuführen. Sicherungsverfahren müssen diese Latenz berücksichtigen. Außerdem bleiben Lucene-Indizes möglicherweise unvollständig, wenn eine Sicherung durchgeführt wird. Dies gilt für alle zeitempfindlichen Dateien, die in einen S3-Datenspeicher geschrieben werden und auf die von einer anderen Instanz zugegriffen wird.

### Node store or document store {#node-store-document-store}

Es ist schwierig, genaue Dimensionierungszahlen für einen Knotenspeicher oder Dokumentspeicher zu ermitteln, da Ressourcen durch Folgendes verbraucht werden:

* Asset-Metadaten
* Asset-Versionen
* Auditprotokolle
* Archivierte und aktive Workflows

Binärdateien in einem Datenspeicher aufzubewahren bedeutet, dass entsprechender Speicherplatz belegt wird. Die meisten Repositorys sind zwar kleiner als 100 GB, Es kann jedoch auch größere Repositorys mit einer Größe von bis zu 1 TB geben. Zusätzlich zur Offlinekomprimierung muss genügend freier Speicher auf dem Volume vorhanden sein, damit das komprimierte Repository neben der vorab komprimierten Version neu geschrieben werden kann. Eine geeignete Faustregel: Dimensionieren Sie die Festplatte so, dass sie 1,5-mal so groß ist wie die erwartete Repositorygröße.

Verwenden Sie für das Repository SSDs oder Festplatten mit einem IOPS-Level über 3000. Damit im Zuge der IOPS keine Leistungsengpässe entstehen, überwachen Sie die CPU-I/O-Wartelevel auf frühe Problemanzeichen.

[Datei laden](assets/aem_environment_sizingtool.xlsx)

## Netzwerk {#network}

[!DNL Assets] hat eine Reihe von Anwendungsfällen, die die Netzwerkleistung wichtiger machen als bei vielen unserer [!DNL Experience Manager] Projekte. Ein Kunde kann über einen schnellen Server verfügen. Wenn die Netzwerkverbindung jedoch nicht groß genug ist, um die Belastung der Benutzer zu unterstützen, die Assets vom System hochladen und herunterladen, dann scheint sie immer noch langsam zu sein. There is a good methodology for determining the choke point in a user&#39;s network connection to [!DNL Experience Manager] at [Assets considerations for user experience, instance sizing, workflow evaluation, and network topology](/help/assets/assets-network-considerations.md).

## Beschränkungen {#limitations}

Beim Dimensionieren einer Implementierung ist es wichtig, Systembeschränkungen zu bedenken. If the proposed implementation exceeds these limitations, employ creative strategies, such as partitioning the assets across multiple [!DNL Assets] implementations.

Die Dateigröße ist nicht der einzige Faktor, der bei OOM-Problemen (Out of Memory, nicht genügend Arbeitsspeicher) eine Rolle spielt. Es kommt auch auf die Bildabmessungen an. You can avoid OOM issues by providing a higher heap size when you start [!DNL Experience Manager].

In addition, you can edit the threshold size property of the `com.day.cq.dam.commons.handler.StandardImageHandler` component in Configuration Manager to use intermediate temporary file greater than zero.

## Maximale Anzahl von Assets {#maximum-number-of-assets}

Die maximale Anzahl von Dateien in einem Datenspeicher kann sich aufgrund von Dateisystembeschränkungen auf 2,1 Milliarden belaufen. Wahrscheinlich trifft das Repository aufgrund der großen Anzahl von Knoten auf Probleme, lange bevor der Datenspeicher an seine Grenzen stößt.

Wurden die Wiedergaben nicht korrekt generiert, verwenden Sie die Camera Raw-Bibliothek. In diesem Fall sollte jedoch die längste Bildseite nicht größer sein als 65.000 Pixel. Außerdem darf das Bild nicht mehr als 512 MP (512 x 1024 x 1024 Pixel) enthalten. Die Größe des Assets spielt keine Rolle.

It is difficult to accurately estimate the size of the TIFF file supported out-of-the-box with a specific heap for [!DNL Experience Manager] because additional factors, such as pixel size influence processing. It is possible that [!DNL Experience Manager] can process a file of size of 255 MB out-of-the-box, but cannot process a file size of 18 MB because the latter comprises of an unusually higher number pixels compared to the former.

## Size of assets {#size-of-assets}

Standardmäßig [!DNL Experience Manager] können Sie Assets mit einer Dateigröße von bis zu 2 GB hochladen. Informationen zum Hochladen sehr großer Assets [!DNL Experience Manager]finden Sie unter [Konfiguration zum Hochladen sehr großer Assets](managing-video-assets.md#configuration-to-upload-assets-that-are-larger-than-gb).
