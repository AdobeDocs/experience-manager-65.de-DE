---
title: '"[!DNL Assets] Größenleitfaden"'
description: Best Practices zur Bestimmung effizienter Metriken zur Schätzung der für die Bereitstellung erforderlichen Infrastruktur und Ressourcen [!DNL Adobe Experience Manager Assets].
contentOwner: AG
role: Architect, Admin
feature: Asset Management
exl-id: fd58ead9-5e18-4f55-8d20-1cf4402fad97
source-git-commit: e24316cb9495a552960ae0620e4198f10a08b691
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 62%

---

# [!DNL Assets] Größenleitfaden {#assets-sizing-guide}

Bei der Dimensionierung der Umgebung für eine [!DNL Adobe Experience Manager Assets] -Implementierung müssen Sie sicherstellen, dass ausreichend Ressourcen zur Verfügung stehen, was den Durchsatz von Festplatte, CPU, Speicher, I/O und Netzwerk angeht. Zur Dimensionierung dieser Ressourcen muss bekannt sein, wie viele Assets in das System geladen werden. Wenn keine bessere Metrik verfügbar ist, können Sie die Größe der vorhandenen Bibliothek durch das Alter der Bibliothek dividieren, um die Rate zu ermitteln, mit der Assets erstellt werden.

## Festplatte {#disk}

### Datenspeicher {#datastore}

Ein häufiger Fehler wurde bei der Größe des erforderlichen Festplattenspeichers für eine [!DNL Assets] -Implementierung besteht darin, die Berechnungen auf der Größe der Rohbilder zu basieren, die in das System aufgenommen werden sollen. Standardmäßig [!DNL Experience Manager] erstellt drei Ausgabeformate zusätzlich zum Originalbild zur Verwendung beim Rendern der [!DNL Experience Manager] Elemente der Benutzeroberfläche. In vorherigen Implementierungen haben sich diese Wiedergaben als doppelt so groß wie die aufgenommenen Assets herausgestellt. 

Die meisten Benutzer definieren benutzerdefinierte Wiedergaben neben den standardmäßig verfügbaren Wiedergaben. Zusätzlich zu den Ausgabeformaten [!DNL Assets] Sie können Unter-Assets aus gängigen Dateitypen extrahieren, z. B. [!DNL Adobe InDesign] und [!DNL Adobe Illustrator].

Und schließlich die Versionierungsfunktionen von [!DNL Experience Manager] speichert Duplikate der Assets im Versionsverlauf. Sie können die Versionen so konfigurieren, dass Bereinigungen häufig durchgeführt werden. Jedoch entscheiden sich viele Benutzer für eine längere Aufbewahrung der Versionen im System, wodurch zusätzlicher Speicherplatz belegt wird.

Angesichts dieser Faktoren benötigen Sie eine Methodik für eine ausreichend genaue Berechnung des Speicherplatzes, um Benutzer-Assets aufbewahren zu können.

1. Bestimmen Sie die Größe und die Anzahl der Assets, die in das System geladen werden.
1. Abrufen eines repräsentativen Beispiels der Assets, in die hochgeladen werden soll [!DNL Experience Manager]. Wenn Sie beispielsweise PSD-, JPG-, AI- und PDF-Dateien in das System laden möchten, benötigen Sie mehrere Beispielbilder für jedes Dateiformat. Außerdem sollten diese Stichproben repräsentativ für die verschiedenen Dateigrößen und die Komplexität der Bilder sein.
1. Definieren Sie die zu verwendenden Wiedergaben.
1. Erstellen Sie die Ausgabedarstellungen in [!DNL Experience Manager] using [!DNL ImageMagick] oder [!DNL Adobe Creative Cloud] Anwendungen. Erstellen Sie neben den von den Benutzern angegebenen Wiedergaben sofort einsetzbare Standardwiedergaben. Für Benutzer, die Dynamic Media implementieren, können Sie die IC-Binärdatei verwenden, um die PTIFF-Ausgabeformate zu generieren, die in Experience Manager gespeichert werden sollen.
1. Wenn Sie die Verwendung von Unter-Assets beabsichtigen, generieren Sie diese für die entsprechenden Dateitypen.
1. Vergleichen Sie die Größe der Ausgabebilder, Wiedergaben und Unter-Assets mit den Originalbildern. So können Sie den erwarteten Wachstumsfaktor beim Laden des Systems generieren. Wenn Sie z. B. Wiedergaben und Unter-Assets mit einer kombinierten Größe von 3 GB nach der Verarbeitung von 1 GB an Assets erzeugen, lautet der Wiedergabe-Wachstumsfaktor 3.
1. Ermitteln Sie, wie lange die einzelnen Asset-Versionen maximal im System aufbewahrt werden sollen.
1. Ermitteln Sie, wie oft vorhandene Assets im System geändert werden. Wenn [!DNL Experience Manager] wird als Knotenpunkt für die Zusammenarbeit in kreativen Workflows verwendet. Die Anzahl der Änderungen ist hoch. Wenn nur fertiggestellte Assets in das System hochgeladen werden, ist diese Zahl wesentlich niedriger.
1. Ermitteln Sie, wie viele Assets jeden Monat in das System geladen werden. Wenn Sie sich nicht sicher sind, bestimmen Sie die Anzahl der aktuell verfügbaren Assets und dividieren Sie diese Zahl durch das Alter des ältesten Assets, um einen ungefähren Wert zu berechnen. 

Mithilfe der oben genannten Schritte können Sie Folgendes ermitteln:

* Rohgröße der zu ladenden Assets.
* Anzahl der zu ladenden Assets.
* Wiedergabe-Wachstumsfaktor.
* Anzahl der Asset-Änderungen pro Monat.
* Anzahl der Monate für die Aufbewahrung von Asset-Versionen.
* Anzahl der neu geladenen Assets pro Monat.
* Wachstumsjahre für die Speicherplatzzuweisung.

Sie können diese Zahlen in der Tabelle zur Netzwerkdimensionierung angeben, um den Gesamtspeicherbedarf für den Datenspeicher zu ermitteln. Es ist auch ein nützliches Tool, um die Auswirkungen der Wartung von Asset-Versionen oder der Änderung von Assets in zu ermitteln. [!DNL Experience Manager] auf Festplattenwachstum.

Die in das Tool aufgefüllten Beispieldaten zeigen, wie wichtig die Ausführung der genannten Schritte ist. Wenn Sie den Datenspeicher allein basierend auf dem Ladevorgang der Rohbilder (1 TB) bemessen, ist eine Unterbewertung der Repositorygröße um dem Faktor 15 möglich.

[Datei laden](assets/disk_sizing_tool.xlsx)

### Freigegebene Datenspeicher {#shared-datastores}

Bei großen Datenspeichern können Sie einen freigegebenen Datenspeicher entweder über einen freigegebenen Dateidatenspeicher auf einem Netzwerklaufwerk oder über einen Amazon S3-Datenspeicher implementieren. In diesem Fall müssen einzelne Instanzen keine Kopie der Binärdateien aufbewahren. Darüber hinaus erleichtert ein freigegebener Datenspeicher die Binärdatei-lose Replikation und reduziert die Bandbreite, die zur Replikation von Assets in Veröffentlichungsumgebungen verwendet wird.

#### Anwendungsfälle {#use-cases}

Der Datenspeicher kann gemeinsam von primärer und Standby-Autoreninstanz genutzt werden, um den zeitlichen Aufwand zum Aktualisieren der Standby-Instanz mit Änderungen der primären Instanz zu minimieren. Sie können den Datenspeicher zudem zwischen Autor- und Veröffentlichungsinstanzen freigeben, um den Traffic während der Replikation zu minimieren.

#### Nachteile {#drawbacks}

Aufgrund gewisser Fallstricke wird die Freigabe eines Datenspeichers nicht in allen Fällen empfohlen.

#### Einzelner Fehlerpunkt {#single-point-of-failure}

Mit einem freigegebenen Datenspeicher entsteht ein Single Point of Failure in einer Infrastruktur. Stellen Sie sich ein Szenario vor, bei dem Ihr System eine Autoreninstanz und zwei Veröffentlichungsinstanzen aufweist, jeweils mit einem eigenen Datenspeicher. Stürzt einer der Datenspeicher ab, können die beiden anderen nach wie vor ausgeführt werden. Wenn der Datenspeicher jedoch gemeinsam genutzt wird, kann der Ausfall einer einzigen Festplatte die gesamte Infrastruktur zum Erliegen bringen. Stellen Sie daher sicher, dass Sie eine Sicherung des freigegebenen Datenspeichers aufbewahren, über die Sie den Datenspeicher schnell wiederherstellen können.

Den AWS S3-Dienst für freigegebene Datenspeicher bereitzustellen, wird vorgezogen, weil hierdurch die Wahrscheinlichkeit eines Ausfalls gegenüber normalen Festplattenarchitekturen deutlich reduziert wird.

#### Erhöhte Komplexität {#increased-complexity}

Freigegebene Datenspeicher erhöhen ebenfalls die Komplexität solcher Vorgänge, etwa der automatischen Speicherbereinigung. Normalerweise kann die automatische Speicherbereinigung für einen Standalone-Datenspeicher mit einem einzigen Klick initiiert werden. Allerdings setzen freigegebene Datenspeicher zusätzlich zu der auf jedem Knoten tatsächlich durchgeführten Bereinigung Mark-Sweep-Vorgänge auf jedem Mitglied voraus, das den Datenspeicher nutzt.

Bei AWS-Betriebssystemen kann die Implementierung eines einzigen zentralen Standorts (über Amazon S3), anstatt ein RAID-Array mit EBS-Volumes zu erstellen, die Komplexität und die betrieblichen Risiken auf dem System erheblich ausgleichen.

#### Leistungsbedenken {#performance-concerns}

Bei einem freigegebenen Datenspeicher müssen die Binärdateien auf einem Laufwerk gespeichert werden, das an ein Netzwerk angebunden und für alle Instanzen freigegeben ist. Da der Zugriff auf diese Binärdateien über ein Netzwerk erfolgt, wird die Systemleistung beeinträchtigt. Eine schnelle Netzwerkverbindung zu einem schnellen Festplattenarray kann diesen Effekt teilweise auffangen. Dies ist jedoch eine teure Angelegenheit. Im Falle von AWS-Vorgängen liegen alle Festplatten remote vor, sodass eine Netzwerkanbindung erforderlich ist. Auf flüchtigen Volumes gehen Daten beim Starten und Stoppen von Instanzen verloren.

#### Latenz {#latency}

Latenz in S3-Implementierungen ist auf die im Hintergrund durchgeführten Schreibthreads zurückzuführen. Sicherungsverfahren müssen diese Latenz berücksichtigen. Außerdem bleiben Lucene-Indizes möglicherweise unvollständig, wenn eine Sicherung durchgeführt wird. Dies gilt für alle zeitempfindlichen Dateien, die in einen S3-Datenspeicher geschrieben werden und auf die von einer anderen Instanz zugegriffen wird.

### Knotenspeicher oder Dokumentspeicher {#node-store-document-store}

Es ist schwierig, genaue Dimensionierungszahlen für einen Knotenspeicher oder Dokumentspeicher zu ermitteln, da Ressourcen durch Folgendes verbraucht werden:

* Asset-Metadaten
* Asset-Versionen
* Auditprotokolle
* Archivierte und aktive Workflows

Binärdateien in einem Datenspeicher aufzubewahren bedeutet, dass entsprechender Speicherplatz belegt wird. Die meisten Repositorys sind zwar kleiner als 100 GB, Es kann jedoch größere Repositorys mit einer Größe von bis zu 1 TB geben. Zusätzlich zur Offlinekomprimierung muss genügend freier Speicher auf dem Volume vorhanden sein, damit das komprimierte Repository neben der vorab komprimierten Version neu geschrieben werden kann. Eine geeignete Faustregel: Dimensionieren Sie die Festplatte so, dass sie 1,5-mal so groß ist wie die erwartete Repositorygröße.

Verwenden Sie für das Repository SSDs oder Festplatten mit einem IOPS-Level größer als 3000. Damit im Zuge der IOPS keine Leistungsengpässe entstehen, überwachen Sie die CPU-I/O-Wartelevel auf frühe Problemanzeichen.

[Datei laden](assets/aem_environment_sizingtool.xlsx)

## Netzwerk {#network}

[!DNL Assets] verfügt über eine Reihe von Anwendungsfällen, die die Netzwerkleistung wichtiger machen als bei vielen unserer [!DNL Experience Manager] Projekte. Ein Kunde kann über einen schnellen Server verfügen. Wenn die Netzwerkverbindung jedoch nicht groß genug ist, um die Last der Benutzer zu unterstützen, die Assets vom System hochladen und herunterladen, scheint sie dennoch langsam zu sein. Es gibt eine gute Methode, um den Schokoladpunkt in der Netzverbindung eines Benutzers zu [!DNL Experience Manager] at [Überlegungen zu Assets für das Benutzererlebnis, die Größe von Instanzen, die Auswertung von Workflows und die Netzwerktopologie](/help/assets/assets-network-considerations.md).

## Beschränkungen {#limitations}

Beim Dimensionieren einer Implementierung ist es wichtig, Systembeschränkungen zu bedenken. Wenn die vorgeschlagene Implementierung diese Einschränkungen überschreitet, setzen Sie kreative Strategien ein, z. B. das Partitionieren der Assets über mehrere [!DNL Assets] -Implementierungen.

Die Dateigröße ist nicht der einzige Faktor, der bei OOM-Problemen (Out of Memory, nicht genügend Arbeitsspeicher) eine Rolle spielt. Es kommt auch auf die Bildabmessungen an. Sie können OOM-Probleme vermeiden, indem Sie beim Start eine höhere Heap-Größe festlegen [!DNL Experience Manager].

Darüber hinaus können Sie die Eigenschaft für die Schwellengröße der Variablen `com.day.cq.dam.commons.handler.StandardImageHandler` -Komponente in Configuration Manager verwenden, um temporäre Zwischendatei größer als null zu verwenden.

## Maximale Anzahl von Assets {#maximum-number-of-assets}

Die maximale Anzahl von Dateien in einem Datenspeicher kann sich aufgrund von Dateisystembeschränkungen auf 2,1 Milliarden belaufen. Wahrscheinlich trifft das Repository aufgrund der großen Anzahl von Knoten auf Probleme, lange bevor der Datenspeicher an seine Grenzen stößt.

Wurden die Wiedergaben nicht korrekt generiert, verwenden Sie die Camera Raw-Bibliothek. In diesem Fall sollte jedoch die längste Bildseite nicht größer sein als 65.000 Pixel. Darüber hinaus sollte das Bild nicht mehr als 512 MP (512 x 1024 x 1024 Pixel) enthalten. Die Größe des Assets spielt keine Rolle.

Es ist schwierig, die Größe der standardmäßig unterstützten TIFF-Datei mit einem bestimmten Heap für [!DNL Experience Manager] weil zusätzliche Faktoren wie die Pixelgröße die Verarbeitung beeinflussen. Es ist möglich, dass [!DNL Experience Manager] kann standardmäßig eine Datei mit einer Größe von 255 MB verarbeiten, kann jedoch keine Dateigröße von 18 MB verarbeiten, da letztere eine ungewöhnlich höhere Anzahl von Pixel im Vergleich zu ersteren aufweist.

## Größe der Assets {#size-of-assets}

Standardmäßig [!DNL Experience Manager] ermöglicht das Hochladen von Assets mit einer Dateigröße von bis zu 2 GB. Hochladen sehr großer Assets in [!DNL Experience Manager], siehe [Konfiguration zum Hochladen sehr großer Assets](managing-video-assets.md#configuration-to-upload-assets-that-are-larger-than-gb).
