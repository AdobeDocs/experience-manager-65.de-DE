---
title: „Anleitung zur Dimensionierung in [!DNL Assets]“
description: Best Practices zur Bestimmung effizienter Metriken zur Schätzung der für die Bereitstellung von  [!DNL Adobe Experience Manager Assets] erforderlichen Infrastruktur und Ressourcen.
contentOwner: AG
role: Architect, Admin
feature: Asset Management
exl-id: fd58ead9-5e18-4f55-8d20-1cf4402fad97
source-git-commit: e24316cb9495a552960ae0620e4198f10a08b691
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 100%

---

# Anleitung zur Dimensionierung in [!DNL Assets] {#assets-sizing-guide}

Beim Dimensionieren der Umgebung für eine [!DNL Adobe Experience Manager Assets]-Implementierung gilt es sicherzustellen, dass hinsichtlich Festplatte, CPU, Arbeitsspeicher, I/O und Netzwerkdurchsatz genügend Ressourcen verfügbar sind. Zur Dimensionierung dieser Ressourcen muss bekannt sein, wie viele Assets in das System geladen werden. Wenn keine bessere Metrik verfügbar ist, können Sie die Größe der vorhandenen Bibliothek durch das Alter der Bibliothek dividieren, um die Rate zu ermitteln, mit der Assets erstellt werden.

## Festplatte {#disk}

### Datenspeicher {#datastore}

Ein häufiger Fehler bei der Dimensionierung des erforderlichen Festplattenspeichers für eine [!DNL Assets]-Implementierung besteht darin, die Berechnungen auf der Größe der in das System aufzunehmenden Rohbilder zu basieren. Standardmäßig erstellt [!DNL Experience Manager] zum Rendern der Benutzeroberflächenelemente von [!DNL Experience Manager] zusätzlich zum Originalbild drei Ausgabedarstellungen. In vorherigen Implementierungen haben sich diese Wiedergaben als doppelt so groß wie die aufgenommenen Assets herausgestellt. 

Die meisten Benutzer definieren benutzerdefinierte Wiedergaben neben den standardmäßig verfügbaren Wiedergaben. Zusätzlich zu den Ausgabedarstellungen können Sie mit [!DNL Assets] Unter-Assets aus gängigen Dateitypen wie [!DNL Adobe InDesign] und [!DNL Adobe Illustrator] extrahieren.

Schließlich sorgen Versionierungsfunktionen in [!DNL Experience Manager] dafür, dass Duplikate der Assets im Versionsverlauf gespeichert werden. Sie können die Versionen so konfigurieren, dass Bereinigungen häufig durchgeführt werden. Jedoch entscheiden sich viele Benutzer für eine längere Aufbewahrung der Versionen im System, wodurch zusätzlicher Speicherplatz belegt wird.

Angesichts dieser Faktoren benötigen Sie eine Methodik für eine ausreichend genaue Berechnung des Speicherplatzes, um Benutzer-Assets aufbewahren zu können.

1. Bestimmen Sie die Größe und die Anzahl der Assets, die in das System geladen werden.
1. Beschaffen Sie sich eine repräsentative Stichprobe der Assets, die in [!DNL Experience Manager] hochgeladen werden sollen. Wenn Sie beispielsweise PSD-, JPG-, AI- und PDF-Dateien in das System laden möchten, benötigen Sie mehrere Beispielbilder für jedes Dateiformat. Außerdem sollten diese Stichproben repräsentativ für die verschiedenen Dateigrößen und die Komplexität der Bilder sein.
1. Definieren Sie die zu verwendenden Wiedergaben.
1. Erstellen Sie die Ausgabedarstellungen in [!DNL Experience Manager] unter Verwendung von [!DNL ImageMagick] oder [!DNL Adobe Creative Cloud]. Erstellen Sie neben den von den Benutzern angegebenen Ausgabedarstellungen sofort einsetzbare Standard-Ausgabedarstellungen. Für Benutzende, die Dynamic Media implementieren, können Sie mithilfe der IC-Binärdatei die in Experience Manager zu speichernden PTIFF-Ausgabedarstellungen generieren.
1. Wenn Sie die Verwendung von Unter-Assets beabsichtigen, generieren Sie diese für die entsprechenden Dateitypen.
1. Vergleichen Sie die Größe der Ausgabebilder, Ausgabedarstellungen und Unter-Assets mit den Originalbildern. So können Sie den erwarteten Wachstumsfaktor beim Laden des Systems generieren. Wenn Sie z. B. Ausgabedarstellungen und Unter-Assets mit einer kombinierten Größe von 3 GB nach der Verarbeitung von 1 GB an Assets erzeugen, lautet der Ausgabedarstellungs-Wachstumsfaktor 3.
1. Ermitteln Sie, wie lange die einzelnen Asset-Versionen maximal im System aufbewahrt werden sollen.
1. Ermitteln Sie, wie oft vorhandene Assets im System geändert werden. Wenn [!DNL Experience Manager] als Collaboration-Hub in kreativen Workflows dient, gibt es viele Änderungen. Wenn nur fertiggestellte Assets in das System hochgeladen werden, ist diese Zahl wesentlich niedriger.
1. Ermitteln Sie, wie viele Assets jeden Monat in das System geladen werden. Wenn Sie sich nicht sicher sind, bestimmen Sie die Anzahl der aktuell verfügbaren Assets und dividieren Sie diese Zahl durch das Alter des ältesten Assets, um einen ungefähren Wert zu berechnen. 

Mithilfe der oben genannten Schritte können Sie Folgendes ermitteln:

* Rohgröße der zu ladenden Assets.
* Anzahl der zu ladenden Assets.
* Ausgabedarstellungs-Wachstumsfaktor.
* Anzahl der Asset-Änderungen pro Monat.
* Anzahl der Monate für die Aufbewahrung von Asset-Versionen.
* Anzahl der neu geladenen Assets pro Monat.
* Jahre des Wachstums für die Speicherplatzzuweisung.

Sie können diese Zahlen in der Tabelle zur Netzwerkdimensionierung angeben, um den Gesamtspeicherbedarf für den Datenspeicher zu ermitteln. Zudem lässt sich so nützlicherweise feststellen, wie sich die Aufbewahrung von Asset-Versionen oder die Änderung von Assets in [!DNL Experience Manager] auf das Festplattenwachstum auswirkt.

Die in das Tool aufgefüllten Beispieldaten zeigen, wie wichtig die Ausführung der genannten Schritte ist. Wenn Sie den Datenspeicher allein basierend auf dem Ladevorgang der Rohbilder (1 TB) bemessen, ist eine Unterbewertung der Repository-Größe um den Faktor 15 möglich.

[Datei laden](assets/disk_sizing_tool.xlsx)

### Freigegebene Datenspeicher {#shared-datastores}

Für große Datenspeicher können Sie einen freigegebenen Datenspeicher implementieren, und zwar entweder über einen gemeinsam genutzten Dateidatenspeicher auf einem Netzlaufwerk oder über einen Amazon S3-Datenspeicher. In diesem Fall müssen einzelne Instanzen keine Kopie der Binärdateien aufbewahren. Außerdem unterstützt ein freigegebener Datenspeicher Binaryless-Replikationen und reduziert die Bandbreite zum Replizieren von Assets in Veröffentlichungsumgebungen.

#### Anwendungsfälle {#use-cases}

Der Datenspeicher kann gemeinsam von primärer und Standby-Autoreninstanz genutzt werden, um den zeitlichen Aufwand zum Aktualisieren der Standby-Instanz mit Änderungen der primären Instanz zu minimieren. Sie können den Datenspeicher zudem zwischen Autor- und Veröffentlichungsinstanzen freigeben, um den Traffic während der Replikation zu minimieren.

#### Nachteile {#drawbacks}

Aufgrund gewisser Fallstricke wird die Freigabe eines Datenspeichers nicht in allen Fällen empfohlen.

#### Single Point of Failure {#single-point-of-failure}

Mit einem freigegebenen Datenspeicher entsteht ein Single Point of Failure in einer Infrastruktur. Stellen Sie sich ein Szenario vor, bei dem Ihr System eine Autoreninstanz und zwei Veröffentlichungsinstanzen aufweist, jeweils mit einem eigenen Datenspeicher. Stürzt einer der Datenspeicher ab, können die beiden anderen nach wie vor ausgeführt werden. Wenn der Datenspeicher jedoch gemeinsam genutzt wird, kann der Ausfall einer einzigen Festplatte die gesamte Infrastruktur zum Erliegen bringen. Stellen Sie daher sicher, dass Sie eine Sicherung des freigegebenen Datenspeichers aufbewahren, über die Sie den Datenspeicher schnell wiederherstellen können.

Den AWS S3-Dienst für freigegebene Datenspeicher bereitzustellen, wird vorgezogen, weil hierdurch die Wahrscheinlichkeit eines Ausfalls gegenüber normalen Festplattenarchitekturen deutlich reduziert wird.

#### Höhere Komplexität {#increased-complexity}

Freigegebene Datenspeicher erhöhen ebenfalls die Komplexität solcher Vorgänge, etwa der automatischen Speicherbereinigung. Normalerweise kann die automatische Speicherbereinigung für einen Standalone-Datenspeicher mit einem einzigen Klick initiiert werden. Allerdings setzen freigegebene Datenspeicher zusätzlich zu der auf jedem Knoten tatsächlich durchgeführten Bereinigung Mark-Sweep-Vorgänge auf jedem Mitglied voraus, das den Datenspeicher nutzt.

Im AWS-Betrieb können, wenn statt eines RAID-Arrays mit EBS-Volumes ein zentraler Speicherort (über Amazon S3) implementiert wird, die Komplexität und die Betriebsrisiken auf dem System deutlich kompensiert werden.

#### Leistungsprobleme {#performance-concerns}

Bei einem freigegebenen Datenspeicher müssen die Binärdateien auf einem Laufwerk gespeichert werden, das an ein Netzwerk angebunden und für alle Instanzen freigegeben ist. Da der Zugriff auf diese Binärdateien über ein Netzwerk erfolgt, wird die Systemleistung beeinträchtigt. Eine schnelle Netzwerkverbindung zu einem schnellen Festplattenarray kann diesen Effekt teilweise auffangen. Dies ist jedoch eine teure Angelegenheit. Im Falle von AWS-Vorgängen liegen alle Festplatten remote vor, sodass eine Netzwerkanbindung erforderlich ist. Auf flüchtigen Volumes gehen Daten beim Starten und Stoppen von Instanzen verloren.

#### Latenz {#latency}

Latenz in S3-Implementierungen ist auf die im Hintergrund durchgeführten Schreibthreads zurückzuführen. Bei Sicherungsverfahren muss diese Latenz berücksichtigt werden. Außerdem bleiben Lucene-Indizes möglicherweise unvollständig, wenn eine Sicherung durchgeführt wird. Dies gilt für alle zeitempfindlichen Dateien, die in einen S3-Datenspeicher geschrieben werden und auf die von einer anderen Instanz zugegriffen wird.

### Knotenspeicher oder Dokumentspeicher {#node-store-document-store}

Es ist schwierig, genaue Dimensionierungszahlen für einen Knotenspeicher oder Dokumentspeicher zu ermitteln, da Ressourcen durch Folgendes verbraucht werden:

* Asset-Metadaten
* Asset-Versionen
* Auditprotokolle
* Archivierte und aktive Workflows

Binärdateien in einem Datenspeicher aufzubewahren bedeutet, dass entsprechender Speicherplatz belegt wird. Die meisten Repositorys sind zwar kleiner als 100 GB, aber es sind auch größere Repositorys mit bis zu 1 TB möglich. Zusätzlich zur Offlinekomprimierung muss genügend freier Speicher auf dem Volume vorhanden sein, damit das komprimierte Repository neben der vorab komprimierten Version neu geschrieben werden kann. Eine geeignete Faustregel: Dimensionieren Sie die Festplatte so, dass sie 1,5-mal so groß ist wie die erwartete Repository-Größe.

Setzen Sie für das Repository SSDs oder Festplatten mit einem IOPS-Level von mehr als 3000 ein. Damit im Zuge der IOPS keine Leistungsengpässe entstehen, überwachen Sie die CPU-I/O-Wartelevel auf frühe Problemanzeichen.

[Datei laden](assets/aem_environment_sizingtool.xlsx)

## Netzwerk {#network}

Für [!DNL Assets] gibt es eine Reihe von Anwendungsbeispielen, in denen die Netzwerkleistung eine größere Bedeutung hat als bei vielen anderen unserer [!DNL Experience Manager]-Projekte. Eine Kundin oder ein Kunde kann zwar über einen schnellen Server verfügen, aber wenn die Netzwerkverbindung nicht für die Auslastung durch die Benutzenden ausreicht, die Assets hochladen und aus dem System herunterladen, scheint der Server nach wie vor langsam zu sein. Eine gute Methodik zum Bestimmen des Drosselpunkts (Choke Point) bei der Netzwerkverbindung von Benutzenden zu [!DNL Experience Manager] finden Sie in den [Assets-Hinweisen zum Benutzererlebnis sowie zur Instanzdimensionierung, Workflow-Bewertung und Netzwerktopologie](/help/assets/assets-network-considerations.md).

## Beschränkungen {#limitations}

Beim Dimensionieren einer Implementierung ist es wichtig, Systembeschränkungen zu bedenken. Wenn die vorgeschlagene Implementierung über diese Beschränkungen hinausgeht, setzen Sie auf kreative Strategien wie die Partitionierung der Assets über mehrere [!DNL Assets]-Implementierungen hinweg.

Die Dateigröße ist nicht der einzige Faktor, der bei OOM-Problemen (Out of Memory, nicht genügend Arbeitsspeicher) eine Rolle spielt. Es kommt auch auf die Bildabmessungen an. Sie können OOM-Probleme durch eine höhere Heap-Größe beim Starten von [!DNL Experience Manager] vermeiden. 

Außerdem können Sie die Eigenschaft für die Schwellenwertgröße der `com.day.cq.dam.commons.handler.StandardImageHandler`-Komponente in Configuration Manager so bearbeiten, dass eine temporäre Zwischendatei größer als null verwendet wird.

## Maximale Anzahl von Assets {#maximum-number-of-assets}

Die maximale Anzahl von Dateien in einem Datenspeicher kann sich aufgrund von Dateisystembeschränkungen auf 2,1 Milliarden belaufen. Wahrscheinlich trifft das Repository aufgrund der großen Anzahl von Knoten auf Probleme, lange bevor der Datenspeicher an seine Grenzen stößt.

Wurden die Wiedergaben nicht korrekt generiert, verwenden Sie die Camera Raw-Bibliothek. In diesem Fall sollte jedoch die längste Bildseite nicht größer sein als 65.000 Pixel. Außerdem sollte das Bild höchstens 512 MP (512 x 1024 x 1024 Pixel) enthalten. Die Größe des Assets spielt keine Rolle.

Die bei einem bestimmten Heap standardmäßig unterstützte TIFF-Dateigröße für [!DNL Experience Manager] lässt sich nur schwer abschätzen, weil die Verarbeitung durch zusätzliche Faktoren wie die Pixelgröße beeinflusst wird. Es ist möglich, dass [!DNL Experience Manager] eine 255 MB große Datei standardmäßig verarbeiten kann, aber eine 18 MB große Datei nicht, weil letztere gegenüber der ersteren eine ungewöhnlich hohe Anzahl an Pixel aufweist.

## Größe der Assets {#size-of-assets}

Standardmäßig ermöglicht [!DNL Experience Manager] das Hochladen von Assets mit einer Dateigröße von bis zu 2 GB. Zum Hochladen sehr großer Assets in [!DNL Experience Manager], lesen Sie [Konfiguration zum Hochladen sehr großer Assets](managing-video-assets.md#configuration-to-upload-assets-that-are-larger-than-gb).
