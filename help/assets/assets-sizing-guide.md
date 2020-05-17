---
title: Handbuch zur Asset-Größenanpassung
description: Best Practices zur Ermittlung effizienter Metriken zur Schätzung der Infrastruktur und der Ressourcen, die für die Bereitstellung von AEM Assets erforderlich sind.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5d66bf75a6751e41170e6297d26116ad33c2df44
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 76%

---


# Assets sizing guide {#assets-sizing-guide}

Beim Dimensionieren der Umgebung für eine Adobe Experience Manager (AEM) Assets-Implementierung gilt es sicherzustellen, dass hinsichtlich Festplatte, CPU, Arbeitsspeicher, I/O und Netzwerkdurchsatz genügend Ressourcen verfügbar sind. Zur Dimensionierung dieser Ressourcen muss bekannt sein, wie viele Assets in das System geladen werden. Wenn keine bessere Metrik verfügbar ist, können Sie die Größe der vorhandenen Bibliothek durch das Alter der Bibliothek dividieren, um die Rate zu ermitteln, mit der Assets erstellt werden.

## Festplatte {#disk}

### Datenspeicher {#datastore}

Ein häufiger Fehler bei der Dimensionierung des erforderlichen Festplattenspeichers für eine Assets-Implementierung besteht darin, die Berechnungen auf der Größe der in das System aufzunehmenden Rohbilder basieren zu lassen. Standardmäßig erstellt AEM zum Rendering der AEM-Benutzeroberflächenelemente drei Wiedergaben zusätzlich zum Originalbild. In vorherigen Implementierungen haben sich diese Wiedergaben als doppelt so groß wie die aufgenommenen Assets herausgestellt. 

Die meisten Benutzer definieren benutzerdefinierte Wiedergaben neben den standardmäßig verfügbaren Wiedergaben. Zusätzlich zu den Wiedergaben können Sie mit AEM Assets Unter-Assets aus gängigen Dateitypen wie InDesign und Illustrator extrahieren.

Und schließlich die Versionierungsfunktionen der AEM Store-Duplikat der Assets im Versionsverlauf. Sie können die Versionen so konfigurieren, dass Bereinigungen häufig durchgeführt werden. Jedoch entscheiden sich viele Benutzer für eine längere Aufbewahrung der Versionen im System, wodurch zusätzlicher Speicherplatz belegt wird.

Angesichts dieser Faktoren benötigen Sie eine Methodik für eine ausreichend genaue Berechnung des Speicherplatzes, um Benutzer-Assets aufbewahren zu können.

1. Bestimmen Sie die Größe und die Anzahl der Assets, die in das System geladen werden.
1. Beschaffen Sie sich eine repräsentative Stichprobe der Assets, die in AEM hochgeladen werden sollen. Wenn Sie beispielsweise PSD-, JPG-, AI- und PDF-Dateien in das System laden möchten, benötigen Sie mehrere Beispielbilder für jedes Dateiformat. Außerdem sollten diese Stichproben repräsentativ für die verschiedenen Dateigrößen und die Komplexität der Bilder sein.
1. Definieren Sie die zu verwendenden Wiedergaben.
1. Erstellen Sie die Wiedergaben in AEM mit ImageMagick oder den Creative Cloud-Anwendungen von Adobe. Erstellen Sie neben den von den Benutzern angegebenen Wiedergaben sofort einsetzbare Standardwiedergaben. Für Benutzer, die Scene7 implementieren, können Sie mithilfe der IC-Binärdatei die in AEM zu speichernden PTIFF-Wiedergaben generieren.
1. Wenn Sie die Verwendung von Unter-Assets beabsichtigen, generieren Sie diese für die entsprechenden Dateitypen.
1. Vergleichen Sie die Größe der Ausgabebilder, Wiedergaben und Unter-Assets mit den Originalbildern. So können Sie den erwarteten Wachstumsfaktor beim Laden des Systems generieren. Wenn Sie z. B. Wiedergaben und Unter-Assets mit einer kombinierten Größe von 3 GB nach der Verarbeitung von 1 GB an Assets erzeugen, lautet der Wiedergabe-Wachstumsfaktor 3.
1. Ermitteln Sie, wie lange die einzelnen Asset-Versionen maximal im System aufbewahrt werden sollen.
1. Ermitteln Sie, wie oft vorhandene Assets im System geändert werden. Wenn AEM als Collaboration-Hub in kreativen Workflows dient, gibt es viele Änderungen. Wenn nur fertiggestellte Assets in das System hochgeladen werden, ist diese Zahl wesentlich niedriger.
1. Ermitteln Sie, wie viele Assets jeden Monat in das System geladen werden. Wenn Sie sich nicht sicher sind, bestimmen Sie die Anzahl der aktuell verfügbaren Assets und dividieren Sie diese Zahl durch das Alter des ältesten Assets, um einen ungefähren Wert zu berechnen. 

Mithilfe der obigen Schritte können Sie Folgendes feststellen:

* Rohgröße der zu ladenden Assets.
* Anzahl der zu ladenden Assets.
* Wiedergabe-Wachstumsfaktor.
* Anzahl der Asset-Änderungen pro Monat.
* Anzahl der Monate für die Aufbewahrung von Asset-Versionen.
* Anzahl der neu geladenen Assets pro Monat.
* Wachstumsjahre für die Raumordnung der Datenspeicherung.

Sie können diese Zahlen in der Tabelle zur Netzwerkdimensionierung angeben, um den Gesamtspeicherbedarf für den Datenspeicher zu ermitteln. Zudem lässt sich so nützlicherweise feststellen, wie sich die Aufbewahrung von Asset-Versionen oder die Änderung von Assets in AEM auf das Festplattenwachstum auswirkt. 

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

Bei AWS-Operationen kann die Implementierung eines zentralen Standorts (über Amazon S3), anstatt ein RAID-Array mit EBS-Volumes zu erstellen, die Komplexität und die operationellen Risiken des Systems erheblich ausgleichen.

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

Für AEM Assets gibt es eine Reihe von Anwendungsbeispielen, in denen die Netzwerkleistung eine größere Bedeutung hat als bei vielen anderen unserer AEM-Projekte. Ein Kunde kann über einen schnellen Server verfügen. Wenn die Netzwerkverbindung jedoch nicht groß genug ist, um die Belastung der Benutzer zu unterstützen, die Assets vom System hochladen und herunterladen, dann scheint sie immer noch langsam zu sein. There is a good methodology for determining the choke point in a user&#39;s network connection to AEM at [AEM Asset considerations for user experience, instance sizing, workflow evaluation, and network topology](/help/assets/assets-network-considerations.md).

## Beschränkungen {#limitations}

Beim Dimensionieren einer Implementierung ist es wichtig, Systembeschränkungen zu bedenken. Wenn die vorgeschlagene Implementierung über diese Beschränkungen hinausgeht, setzen Sie auf kreative Strategien wie die Partitionierung von Assets über mehrere Assets-Implementierungen hinweg.

Die Dateigröße ist nicht der einzige Faktor, der bei OOM-Problemen (Out of Memory, nicht genügend Arbeitsspeicher) eine Rolle spielt. Es kommt auch auf die Bildabmessungen an. Sie können OOM-Probleme durch eine höhere Heap-Größe beim Starten von AEM vermeiden.

In addition, you can edit the threshold size property of the `com.day.cq.dam.commons.handler.StandardImageHandler` component in Configuration Manager to use intermediate temporary file greater than zero.

## Maximale Anzahl von Assets {#maximum-number-of-assets}

Die maximale Anzahl von Dateien in einem Datenspeicher kann sich aufgrund von Dateisystembeschränkungen auf 2,1 Milliarden belaufen. Wahrscheinlich trifft das Repository aufgrund der großen Anzahl von Knoten auf Probleme, lange bevor der Datenspeicher an seine Grenzen stößt.

Wurden die Wiedergaben nicht korrekt generiert, verwenden Sie die Camera Raw-Bibliothek. In diesem Fall sollte jedoch die längste Bildseite nicht größer sein als 65.000 Pixel. Außerdem darf das Bild nicht mehr als 512 MP (512 x 1024 x 1024 Pixel) enthalten. Die Größe des Assets spielt keine Rolle.

Es ist schwierig, die Größe der standardmäßig unterstützten TIFF-Datei mit einem bestimmten Heap für AEM genau zu schätzen, da zusätzliche Faktoren wie die Pixelgröße die Verarbeitung beeinflussen. Es ist möglich, dass AEM eine Datei mit einer Größe von 255 MB standardmäßig verarbeiten kann, eine Dateigröße von 18 MB jedoch nicht verarbeiten kann, da letztere eine ungewöhnlich höhere Pixelzahl im Vergleich zu ersteren aufweist.

## Size of assets {#size-of-assets}

Standardmäßig können Sie mit AEM Assets mit einer Dateigröße von bis zu 2 GB hochladen. Informationen zum Hochladen sehr großer Assets in AEM finden Sie unter [Konfiguration zum Hochladen sehr großer Assets](managing-video-assets.md#configuration-to-upload-assets-that-are-larger-than-gb).
