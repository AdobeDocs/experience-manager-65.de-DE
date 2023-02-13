---
title: Handbuch zur Leistung von Assets
seo-title: Assets Performance Guide
description: Erfahren Sie, wie Sie die optimale Hardwaredimensionierung für eine neue Digital Asset Management(DAM)-Einrichtung bestimmen und wie Sie Leistungsprobleme beheben.
seo-description: Learn how to determine the optimal hardware sizing for a new Digital Asset Management (DAM) setup and how to troubleshoot performance issues
uuid: 8291c5b9-c543-41cf-8754-445826200930
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
discoiquuid: a79839e2-be39-418b-a3bd-f5457e555172
exl-id: fbe15e1b-830b-4752-bd02-0d239a90bc68
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1222'
ht-degree: 100%

---

# Handbuch zur Leistung von Assets{#assets-performance-guide}

Digital Asset Management wird häufig dort angewendet, wo es auf Leistung ankommt. Das typische DAM-Setup enthält jedoch eine Reihe von Hardware- und Software-Komponenten, die sich auf die Leistung auswirken können. Dieses Dokument umfasst Folgendes:

* Informationen für Systemadministratoren zur Bestimmung der optimalen Hardwaredimensionierung für eine neue Digital-Asset-Management-Einrichtung
* Informationen für Softwareentwickler zur Fehlerbehebung bei DAM-Instanzen mit Leistungsproblemen

## Leistungsprobleme {#performance-issues}

Eine unzureichende Leistung beim Digital Asset Management kann das Benutzererlebnis in dreierlei Hinsicht beeinflussen: interaktive Leistung, Asset-Verarbeitung und Downloadgeschwindigkeit. Um die Leistung zu verbessern, ist es wichtig, die beobachtete Leistung ordnungsgemäß zu messen und Zielmetriken festzulegen.

**1. Interaktive Suche und interaktives Durchsuchen** Wenn Benutzer etwa nach Assets suchen oder den DAM Finder durchsuchen und dann langsame Antwortzeiten oder eine verzögerte Anzeige von Suchergebnissen beklagen, handelt es sich um ein Problem im Zusammenhang mit der interaktiven Leistung.

Die interaktive Leistung wird anhand der Seitenantwortzeit gemessen. Dies ist die Zeit vom Erhalt der HTTP-Anfrage bis zum Abschließen der HTTP-Antwort, ermittelbar über die Log-Dateien der Anfragen. Als typische Sollleistung gilt eine Seitenantwortzeit von weniger als 2 Sekunden.

**2. Asset-Verarbeitung** Ein Problem mit der Asset-Verarbeitung liegt vor, wenn beim es beim Hochladen von Assets mehrere Minuten dauert, bis die Assets fertig konvertiert sind und in AEM DAM übernommen werden.

Die Leistung bei der Asset-Verarbeitung wird anhand der durchschnittlichen Abschlusszeit des Workflowprozesses gemessen. Dies ist die Zeit vom Auslösen bis zum Abschließen des Workflowprozesses für Asset-Updates, ermittelbar über die Benutzeroberfläche für Workflowberichte. Die typische Sollleistung ist abhängig von Größe und Typ der verarbeiteten Assets sowie von der Anzahl der Ausgabedarstellungen. Mögliche Beispiele für Sollleistungen:

* unter zehn Sekunden für Bilder mit einer Auflösung von weniger als 1280 x 1280 Pixel bei Standardwiedergaben
* unter einer Minute für Bilder mit einer Größe von weniger als 100 MB bei Standardwiedergaben
* unter fünf Minuten für HD-Videoclips mit einer Länge von weniger als einer Minute

**3. Download-Geschwindigkeiten** Ein Durchsatzproblem liegt vor, wenn ein Download von AEM DAM längere Zeit dauert und Miniaturansichten beim Browsen in DAM Admin oder DAM Finder nicht sofort angezeigt werden.

Die Durchsatzleistung wird anhand der Downloadrate in Kilobit pro Sekunde gemessen. Als typische Sollleistung gelten 300 Kilobit pro Sekunde für 100 gleichzeitige Downloads.

**4. Einflussfaktoren für die Leistung bei der Asset-Verarbeitung**

Um die Hardwareanforderungen zum Verarbeiten von Assets einschätzen zu können, müssen Sie die folgenden Aspekte berücksichtigen:

* Auflösung der Bilder in Pixel
* Heap-Zuweisung zum AEM-Prozess

Die Anzahl der Pixel im Bild bestimmt die Verarbeitungszeit – je höher die Pixelzahl, desto länger dauert die Verarbeitung.
Der Bildtyp, die Komprimierungsrate oder die entsprechende Dateigröße beim Speichern des Bildes wirken sich nicht wesentlich auf die Gesamtleistung aus.

Vielmehr hat sich der Heap als bedeutendster limitierender Faktor herausgestellt. Sobald Assets den verfügbaren freien Speicher überschreiten, ist ein rapider Abfall der Verarbeitungsleistung zu verzeichnen.

Im Falle großer Mengen können DAM-Prozesse sehr gut parallel durchgeführt werden. Stapelweises Hochladen von Assets und Multicore-Prozessoren senken den absoluten Zeitaufwand pro Asset erheblich.

**5. Einschätzen der Hardwareanforderungen zur Asset-Verarbeitung**

Zur umfangreichen Verarbeitung digitaler Assets sind optimierte Hardwareressourcen erforderlich; die wichtigsten Faktoren hierbei sind die Bildgröße und der Spitzendurchsatz verarbeiteter Bilder.

Weisen Sie mindestens 16 GB Heap zu und konfigurieren Sie den Workflow [!UICONTROL DAM-Update-Asset] so, dass Rohbilder mit dem [Camera Raw-Paket](/help/assets/camera-raw.md) aufgenommen werden.

## Wissenswertes über das System {#understanding-the-system}

Eine typische DAM-Einrichtung umfasst Endbenutzer, die per Lastenausgleichsmodul auf DAM zugreifen. Die DAM-Instanz kann Teil einer Clustereinrichtung sein, bei der jede DAM-Instanz in einem Java Virtual Machine-Prozess auf einem physischen Rechner oder einer virtuellen Maschine ausgeführt wird. Bei Einrichtungen mit einem Rechner wird DAM-Speicher in Form einer RAID-Festplatte bereitgestellt, im Fall einer Clustereinrichtung in Form von Managed NAS (Network Attached Storage).

In der folgenden Legende werden Bereiche mit möglichen Leistungsproblemen samt einer Reihe von ggf. anwendbaren Lösungen beschrieben.

**Netzwerkverbindung zum Endbenutzer** Eine langsame Netzwerkverbindung kann Durchsatzprobleme verursachen, in seltenen Fällen auch Latenzprobleme. Manchmal erhalten Benutzer eine langsame Verbindung vom Internetdienstanbieter (Internet Service Provider, ISP), insbesondere bei Intranets. Dies ist ein Anzeichen für eine unsachgemäße Netzwerktopologie.

**Temporäres Dateisystem** Ein langsames lokales Dateisystem kann zu Problemen mit der interaktiven Leistung führen. Dies gilt insbesondere für Suchvorgänge, da Suchindizes auf der lokalen Festplatte gespeichert werden. Darüber hinaus können Probleme bei der Asset-Verarbeitung auftreten, sofern der Befehlszeilenprozess verwendet wird.

**AEM-DAM Produktsuche** Probleme mit der interaktiven Leistung, die häufig bei Suchvorgängen auftreten, sind auf eine hohe CPU-Auslastung aufgrund einer zu großen Anzahl gleichzeitiger Benutzender oder andere CPU-intensive Prozesse in derselben Instanz zurückzuführen. Durch den Wechsel von virtuellen Maschinen zu dedizierten Maschinen und die Sicherstellung, dass keine weiteren Dienste auf dem Rechner ausgeführt werden, kann die Leistung verbessert werden. Wenn eine hohe CPU-Last durch eine Asset-Verarbeitung und viele gleichzeitige Benutzer verursacht wird, empfiehlt Day das Hinzufügen weiterer Clusterknoten.

**AEM-DAM Workflow** Lang laufende Workflow-Prozesse während der Asset-Aufnahme führen zu Leistungsproblemen bei der Asset-Verarbeitung. Abhängig vom Typ der verarbeiteten Assets kann dies auf eine Überauslastung der CPU hindeuten. Day empfiehlt, die Anzahl der anderen im System ausgeführten Prozesse zu reduzieren und die Anzahl der verfügbaren CPUs durch Hinzufügen von Clusterknoten zu erhöhen.

**NAS Connectivity** Eine unzureichende Netzwerkkonnektivität zum NAS verursacht Probleme mit der interaktiven Leistung, weil der Zugriff auf neue Knoten während der Asset-Verarbeitung aufgrund der Netzwerklatenz verlangsamt wird. Außerdem wirkt sich ein langsamer Netzwerkdurchsatz nicht nur negativ auf den Durchsatz aus, sondern auch auf die Leistung bei der Asset-Verarbeitung, denn Wiedergaben werden langsamer geladen und gespeichert.

Ursachen für eine schlechte Latenz und unzureichenden Durchsatz in einem NAS sind gewöhnlich die Netzwerktopologie oder eine NAS-Überauslastung durch andere Dienste.

**Network Attached Storage (NAS)** Überbeanspruchte NAS-Systeme können zu einer Vielzahl von Problemen führen:

* Geringer Festplattenspeicher ist ein häufig auftretendes Problem, das durch eine ordnungsgemäße Dimensionierung von DAM-Projekten verhindert werden kann.
* Eine hohe Festplattenlatenz führt zu langsamen Zugriffszeiten für CRX und kann Probleme mit der interaktiven Leistung verursachen.
* Ein geringer Datenträgerdurchsatz kann Leistungseinbußen für CQ5 DAM zur Folge haben.

## Testen auf Leistung {#testing-for-performance}

Achten Sie bei jedem DAM-Projekt darauf, Leistungstests durchzuführen, um Engpässe schnell zu erkennen und zu beseitigen. Berücksichtigen Sie dazu die folgenden Checkpoints:

1. Simulieren Sie im Rahmen von End-to-End-Leistungstests mit JMeter eine beispielhafte Such- und Browsingsitzung, um Probleme mit der interaktiven Leistung zu erkennen.
1. Führen Sie mit JMeter Durchsatz- und Latenztests auf einem Clientcomputer durch, um topologiebezogene Probleme auszuschließen.
1. Nehmen Sie im Rahmen standardisierter Tests zur Asset-Verarbeitung eine geringe Anzahl von Beispiel-Assets auf und messen Sie den Zeitaufwand. Prozesse zur externen Workflowintegration sollten dabei eingeschlossen sein.
1. Überwachen Sie die CPU-, Datenträger- und Speicherauslastung von jedem Clusterknoten.
1. Diagnostizieren Sie die CRX-Lese-/-Schreibleistung, um Probleme zu identifizieren, die nicht mit Verarbeitungsvorgängen im Zusammenhang stehen.
1. Überwachen Sie die Netzwerklatenz und den Durchsatz vom DAM-Cluster zu Ihrem NAS.
1. Testen Sie die Lese- und Schreibleistung sowie die Festplattenlatenz direkt auf dem NAS, sofern möglich.

## Optimieren im Falle von Engpässen {#tweaking-bottlenecks}

Die folgenden Leistungsoptimierungen wurden bisher in Projekten angewendet:

* Generieren selektiver Wiedergaben: Generieren Sie nur die von Ihnen benötigten Wiedergaben, indem Sie dem Workflow für die Asset-Verarbeitung Bedingungen hinzufügen, damit aufwandsintensivere Wiedergaben nur für ausgewählte Assets erzeugt werden.
* Zwischen Instanzen freigegebener Datenspeicher: Wenn nicht genügend Festplattenspeicher vorhanden ist, kann sich hierdurch die Menge des benötigten Speicherplatzes deutlich reduzieren – allerdings verbunden mit einem höheren Konfigurationsaufwand und dem Verlust der automatischen Datenspeicherbereinigung.

## Weiterführende Literatur {#further-reading}

* [Analysieren von langsamen und blockierten Prozessen](https://helpx.adobe.com/de/experience-manager/kb/AnalyzeSlowAndBlockedProcesses.html)
