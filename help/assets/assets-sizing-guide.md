---
title: „Anleitung zur Dimensionierung in [!DNL Assets]“
description: Best Practices zur Bestimmung effizienter Metriken zur Schätzung der für die Bereitstellung von  [!DNL Adobe Experience Manager Assets] erforderlichen Infrastruktur und Ressourcen.
contentOwner: AG
role: Architect, Admin
feature: Asset Management
exl-id: fd58ead9-5e18-4f55-8d20-1cf4402fad97
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 54%

---

# Anleitung zur Dimensionierung in [!DNL Assets] {#assets-sizing-guide}

Beim Dimensionieren der Umgebung für eine [!DNL Adobe Experience Manager Assets]-Implementierung gilt es sicherzustellen, dass hinsichtlich Festplatte, CPU, Arbeitsspeicher, I/O und Netzwerkdurchsatz genügend Ressourcen verfügbar sind. Die Größe vieler dieser Ressourcen erfordert ein Verständnis davon, wie viele Assets in das System geladen werden. Wenn keine bessere Metrik verfügbar ist, können Sie die Größe der vorhandenen Bibliothek durch das Alter der Bibliothek dividieren, um die Rate zu ermitteln, mit der Assets erstellt werden.

## Festplatte {#disk}

### DataStore {#datastore}

Ein häufiger Fehler bei der Dimensionierung des erforderlichen Festplattenspeichers für eine [!DNL Assets]-Implementierung besteht darin, die Berechnungen auf der Größe der in das System aufzunehmenden Rohbilder zu basieren. Standardmäßig erstellt [!DNL Experience Manager] zum Rendern der Benutzeroberflächenelemente von [!DNL Experience Manager] zusätzlich zum Originalbild drei Ausgabedarstellungen. In früheren Implementierungen wurde festgestellt, dass diese Ausgabedarstellungen die doppelte Größe der aufgenommenen Assets annehmen.

Die meisten Benutzer definieren benutzerdefinierte Ausgabeformate zusätzlich zu den vordefinierten Ausgabeformaten. Zusätzlich zu den Ausgabedarstellungen können Sie mit [!DNL Assets] Unter-Assets aus gängigen Dateitypen wie [!DNL Adobe InDesign] und [!DNL Adobe Illustrator] extrahieren.

Schließlich sorgen Versionierungsfunktionen in [!DNL Experience Manager] dafür, dass Duplikate der Assets im Versionsverlauf gespeichert werden. Sie können die Versionen so konfigurieren, dass Bereinigungen häufig durchgeführt werden. Viele Benutzer entscheiden sich jedoch dafür, die Versionen lange im System zu behalten, was zusätzlichen Speicherplatz beansprucht.

In Anbetracht dieser Faktoren benötigen Sie eine Methode zur Berechnung eines akzeptabel präzisen Speicherplatzes zum Speichern von Benutzer-Assets.

1. Bestimmen Sie die Größe und Anzahl der Assets, die in das System geladen werden.
1. Beschaffen Sie sich eine repräsentative Stichprobe der Assets, die in [!DNL Experience Manager] hochgeladen werden sollen. Wenn Sie beispielsweise PSD-, JPG-, AI- und PDF-Dateien in das System laden möchten, benötigen Sie mehrere Beispielbilder für jedes Dateiformat. Darüber hinaus sollten diese Muster für die verschiedenen Dateigrößen und Komplexität von Bildern repräsentativ sein.
1. Definieren Sie die zu verwendenden Ausgabedarstellungen.
1. Erstellen Sie die Ausgabedarstellungen in [!DNL Experience Manager] unter Verwendung von [!DNL ImageMagick] oder [!DNL Adobe Creative Cloud]. Erstellen Sie neben den von den Benutzern angegebenen Ausgabedarstellungen sofort einsetzbare Standard-Ausgabedarstellungen. Für Benutzende, die Dynamic Media implementieren, können Sie mithilfe der IC-Binärdatei die in Experience Manager zu speichernden PTIFF-Ausgabedarstellungen generieren.
1. Wenn Sie die Verwendung von Unter-Assets beabsichtigen, generieren Sie diese für die entsprechenden Dateitypen.
1. Vergleichen Sie die Größe der Ausgabebilder, Ausgabedarstellungen und Unter-Assets mit den Originalbildern. Damit können Sie beim Laden des Systems einen erwarteten Wachstumsfaktor generieren. Wenn Sie z. B. Ausgabedarstellungen und Unter-Assets mit einer kombinierten Größe von 3 GB nach der Verarbeitung von 1 GB an Assets erzeugen, lautet der Ausgabedarstellungs-Wachstumsfaktor 3.
1. Legen Sie die maximale Zeit fest, für die Asset-Versionen im System gepflegt werden sollen.
1. Bestimmen Sie, wie oft vorhandene Assets im System geändert werden. Wenn [!DNL Experience Manager] als Collaboration-Hub in kreativen Workflows dient, gibt es viele Änderungen. Wenn nur fertige Assets in das System hochgeladen werden, ist diese Zahl viel niedriger.
1. Bestimmen Sie, wie viele Assets jeden Monat in das System geladen werden. Wenn Sie sich nicht sicher sind, ermitteln Sie die Anzahl der derzeit verfügbaren Assets und teilen Sie die Zahl durch das Alter des ältesten Assets, um eine ungefähre Zahl zu berechnen.

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

Für große Datenspeicher können Sie einen freigegebenen Datenspeicher implementieren, und zwar entweder über einen gemeinsam genutzten Dateidatenspeicher auf einem Netzlaufwerk oder über einen Amazon S3-Datenspeicher. In diesem Fall müssen einzelne Instanzen keine Kopie der Binärdateien verwalten. Außerdem unterstützt ein freigegebener Datenspeicher Binaryless-Replikationen und reduziert die Bandbreite zum Replizieren von Assets in Veröffentlichungsumgebungen.

#### Anwendungsfälle {#use-cases}

Der Datenspeicher kann gemeinsam von primärer und Standby-Autoreninstanz genutzt werden, um den zeitlichen Aufwand zum Aktualisieren der Standby-Instanz mit Änderungen der primären Instanz zu minimieren. Sie können den Datenspeicher auch zwischen der Autoren- und der Veröffentlichungsinstanz freigeben, um den Traffic während der Replikation zu minimieren.

#### Nachteile {#drawbacks}

Aufgrund einiger Fallstricke wird die Freigabe eines Datenspeichers nicht in allen Fällen empfohlen.

#### Single Point of Failure {#single-point-of-failure}

Ein freigegebener Datenspeicher führt einen einzelnen Fehlerpunkt in einer Infrastruktur ein. Stellen Sie sich ein Szenario vor, in dem Ihr System über eine Autoren- und zwei Veröffentlichungsinstanzen mit jeweils einem eigenen Datenspeicher verfügt. Wenn einer von ihnen abstürzt, können die beiden anderen weiterhin ausgeführt werden. Wenn der Datenspeicher jedoch freigegeben ist, kann ein einzelner Datenträgerfehler die gesamte Infrastruktur beeinträchtigen. Stellen Sie daher sicher, dass Sie eine Sicherung des freigegebenen Datenspeichers aufbewahren, aus dem Sie den Datenspeicher schnell wiederherstellen können.

Die Bereitstellung des AWS S3-Diensts für freigegebene Datenspeicher wird bevorzugt, da dadurch die Wahrscheinlichkeit eines Fehlschlagens im Vergleich zu normalen Festplattenarchitekturen erheblich verringert wird.

#### Höhere Komplexität {#increased-complexity}

Freigegebene Datenspeicher erhöhen auch die Komplexität von Vorgängen, wie z. B. der Speicherbereinigung. Normalerweise kann die Speicherbereinigung für einen eigenständigen Datenspeicher mit nur einem Klick initiiert werden. Freigegebene Datenspeicher erfordern jedoch zusätzlich zur Ausführung der tatsächlichen Sammlung auf einem einzelnen Knoten auch die Aktion zum Durchsuchen von Markierungen für jedes Element, das den Datenspeicher verwendet.

Im AWS-Betrieb können, wenn statt eines RAID-Arrays mit EBS-Volumes ein zentraler Speicherort (über Amazon S3) implementiert wird, die Komplexität und die Betriebsrisiken auf dem System deutlich kompensiert werden.

#### Leistungsprobleme {#performance-concerns}

Bei einem freigegebenen Datenspeicher müssen die Binärdateien auf einem Laufwerk gespeichert werden, das an ein Netzwerk angebunden und für alle Instanzen freigegeben ist. Da der Zugriff auf diese Binärdateien über ein Netzwerk erfolgt, wird die Systemleistung beeinträchtigt. Eine schnelle Netzwerkverbindung zu einem schnellen Festplattenarray kann diesen Effekt teilweise auffangen. Dies ist jedoch eine teure Angelegenheit. Wenn AWS-Vorgänge ausgeführt werden, sind alle Festplatten remote und benötigen eine Netzwerkverbindung. Bei temporären Volumes gehen Daten verloren, wenn die Instanz gestartet oder angehalten wird.

#### Latenz {#latency}

Die Latenz in S3-Implementierungen wird durch die Schreibthreads im Hintergrund eingeführt. Sicherungsverfahren müssen diese Latenz berücksichtigen. Darüber hinaus können Lucene-Indizes beim Erstellen einer Sicherung unvollständig bleiben. Dies gilt für alle zeitkritischen Dateien, die in den S3-Datenspeicher geschrieben und von einer anderen Instanz aus aufgerufen werden.

### Knotenspeicher oder Dokumentspeicher {#node-store-document-store}

Aufgrund der Ressourcen, die von den folgenden Benutzern benötigt werden, ist es schwierig, präzise Größenangaben für einen NodeStore oder DocumentStore zu erhalten:

* Asset-Metadaten
* Asset-Versionen
* Audit-Protokolle
* Archivierte und aktive Workflows

Da die Binärdateien im Datenspeicher gespeichert werden, belegt jede Binärdatei etwas Platz. Die meisten Repositorys sind kleiner als 100 GB. aber es sind auch größere Repositorys mit bis zu 1 TB möglich. Um eine Offline-Komprimierung durchzuführen, benötigen Sie ausreichend freien Speicherplatz auf dem Volume, um das komprimierte Repository neben der vorab komprimierten Version neu zu schreiben. Eine geeignete Faustregel: Dimensionieren Sie die Festplatte so, dass sie 1,5-mal so groß ist wie die erwartete Repository-Größe.

Setzen Sie für das Repository SSDs oder Festplatten mit einem IOPS-Level von mehr als 3000 ein. Damit im Zuge der IOPS keine Leistungsengpässe entstehen, überwachen Sie die CPU-I/O-Wartelevel auf frühe Problemanzeichen.

[Datei laden](assets/aem_environment_sizingtool.xlsx)

## Netzwerk {#network}

[!DNL Assets] verfügt über mehrere Anwendungsfälle, die die Netzwerkleistung wichtiger machen als bei vielen unserer [!DNL Experience Manager] Projekte. Eine Kundin oder ein Kunde kann zwar über einen schnellen Server verfügen, aber wenn die Netzwerkverbindung nicht für die Auslastung durch die Benutzenden ausreicht, die Assets hochladen und aus dem System herunterladen, scheint der Server nach wie vor langsam zu sein. Eine gute Methodik zum Bestimmen des Drosselpunkts (Choke Point) bei der Netzwerkverbindung von Benutzenden zu [!DNL Experience Manager] finden Sie in den [Assets-Hinweisen zum Benutzererlebnis sowie zur Instanzdimensionierung, Workflow-Bewertung und Netzwerktopologie](/help/assets/assets-network-considerations.md).

## Beschränkungen {#limitations}

Bei der Größenanpassung einer Implementierung müssen die Systembeschränkungen beachtet werden. Wenn die vorgeschlagene Implementierung über diese Beschränkungen hinausgeht, setzen Sie auf kreative Strategien wie die Partitionierung der Assets über mehrere [!DNL Assets]-Implementierungen hinweg.

Die Dateigröße ist nicht der einzige Faktor, der zu OOM-Problemen (Out of Memory) beiträgt. Es hängt auch von den Abmessungen des Bildes ab. Sie können OOM-Probleme durch eine höhere Heap-Größe beim Starten von [!DNL Experience Manager] vermeiden. 

Außerdem können Sie die Eigenschaft für die Schwellenwertgröße der `com.day.cq.dam.commons.handler.StandardImageHandler`-Komponente in Configuration Manager so bearbeiten, dass eine temporäre Zwischendatei größer als null verwendet wird.

## Maximale Anzahl von Assets {#maximum-number-of-assets}

Die Anzahl der Dateien, die in einem Datenspeicher vorhanden sein können, kann aufgrund von Dateisystembeschränkungen auf 2,1 Milliarden begrenzt sein. Es ist wahrscheinlich, dass das Repository aufgrund einer großen Anzahl von Knoten Probleme hat, lange bevor das Datenspeicherlimit erreicht wurde.

Wenn die Ausgabedarstellungen falsch generiert werden, verwenden Sie die Camera Raw Bibliothek. In diesem Fall sollte die längste Seite des Bildes jedoch nicht größer als 65.000 Pixel sein. Außerdem sollte das Bild höchstens 512 MP (512 x 1024 x 1024 Pixel) enthalten. Die Größe des Assets spielt keine Rolle.

Die bei einem bestimmten Heap standardmäßig unterstützte TIFF-Dateigröße für [!DNL Experience Manager] lässt sich nur schwer abschätzen, weil die Verarbeitung durch zusätzliche Faktoren wie die Pixelgröße beeinflusst wird. Es ist möglich, dass [!DNL Experience Manager] eine 255 MB große Datei standardmäßig verarbeiten kann, aber eine 18 MB große Datei nicht, weil letztere gegenüber der ersteren eine ungewöhnlich hohe Anzahl an Pixel aufweist.

## Größe der Assets {#size-of-assets}

Standardmäßig ist [!DNL Experience Manager] ermöglicht das Hochladen von Assets mit einer Dateigröße von bis zu 2 GB. Zum Hochladen sehr großer Assets in [!DNL Experience Manager], lesen Sie [Konfiguration zum Hochladen sehr großer Assets](managing-video-assets.md#configuration-to-upload-assets-that-are-larger-than-gb).
