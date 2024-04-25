---
title: Handbuch zur Leistung von Assets
description: Erfahren Sie, wie Sie die optimale Hardware-Dimensionierung für ein neues Digital Asset Management-Setup (DAM) bestimmen und Leistungsprobleme beheben.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
exl-id: fbe15e1b-830b-4752-bd02-0d239a90bc68
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 100%

---

# Handbuch zur Leistung von Assets{#assets-performance-guide}

Digital Asset Management (DAM) wird häufig dort angewendet, wo es auf Leistung ankommt. Das typische DAM-Setup umfasst jedoch verschiedene Hardware- und Software-Komponenten, die sich auf die Leistung auswirken können. Dieses Dokument umfasst Folgendes:

* Informationen für Systemadmins zur Bestimmung der optimalen Hardware-Dimensionierung für ein neues Digital Asset Management-Setup
* Informationen für Software-Entwickelnde zur Fehlerbehebung bei DAM-Instanzen mit Leistungsproblemen

## Leistungsprobleme {#performance-issues}

Eine unzureichende Leistung beim Digital Asset Management kann das Anwendererlebnis in dreierlei Hinsicht beeinflussen: interaktive Leistung, Asset-Verarbeitung und Download-Geschwindigkeit. Um die Leistung zu verbessern, ist es wichtig, die beobachtete Leistung ordnungsgemäß zu messen und Zielmetriken festzulegen.

**1. Interaktive Suche und interaktives Durchsuchen** Wenn Benutzer etwa nach Assets suchen oder den DAM Finder durchsuchen und dann langsame Antwortzeiten oder eine verzögerte Anzeige von Suchergebnissen beklagen, handelt es sich um ein Problem im Zusammenhang mit der interaktiven Leistung.

Die interaktive Leistung wird anhand der Seitenreaktionszeit gemessen. Dies ist die Zeit vom Erhalt der HTTP-Anfrage bis zum Abschließen der HTTP-Antwort, ermittelbar über die Protokolldateien der Anfragen. Als typische Sollleistung gilt eine Seitenantwortzeit von weniger als zwei Sekunden.

**2. Asset-Verarbeitung** Ein Problem mit der Asset-Verarbeitung liegt vor, wenn es beim Hochladen von Assets mehrere Minuten dauert, bis die Assets fertig konvertiert sind und in Adobe Experience Manager (AEM) DAM aufgenommen werden.

Die Leistung bei der Asset-Verarbeitung wird anhand der durchschnittlichen Abschlusszeit des Workflow-Prozesses gemessen. Dies ist die Zeit vom Auslösen bis zum Abschließen des Workflow-Prozesses für Asset-Updates, ermittelbar über die Benutzeroberfläche für Workflow-Berichte. Die typische Sollleistung ist abhängig von Größe und Typ der verarbeiteten Assets sowie von der Anzahl der Ausgabedarstellungen. Mögliche Beispiele für Sollleistungen:

* unter zehn Sekunden für Bilder mit einer Auflösung von weniger als 1280 × 1280 Pixel bei standardmäßigen Ausgabedarstellungen
* unter einer Minute für Bilder mit einer Größe von weniger als 100 MB bei standardmäßigen Ausgabedarstellungen
* unter fünf Minuten für HD-Video-Clips mit einer Länge von weniger als einer Minute

**3. Download-Geschwindigkeiten** Ein Durchsatzproblem liegt vor, wenn ein Download von AEM DAM längere Zeit dauert und Miniaturansichten beim Browsen in DAM Admin oder DAM Finder nicht sofort angezeigt werden.

Die Durchsatzleistung wird anhand der Download-Rate in Kilobit pro Sekunde gemessen. Als typische Sollleistung gelten 300 Kilobit pro Sekunde für 100 gleichzeitige Downloads.

**4. Einflussfaktoren für die Leistung bei der Asset-Verarbeitung**

Um abschätzen zu können, welche Hardware Sie zur Verarbeitung von Assets benötigen, sollten folgende Aspekte berücksichtigt werden:

* Auflösung der Bilder in Pixel
* Heap-Zuweisung zum AEM-Prozess

Die Anzahl der Pixel im Bild bestimmt die Verarbeitungszeit – je höher die Pixelzahl, desto länger dauert die Verarbeitung.
Der Bildtyp, die Komprimierungsrate oder die entsprechende Dateigröße beim Speichern des Bildes wirken sich nicht wesentlich auf die Gesamtleistung aus.

Vielmehr hat sich der Heap als bedeutendster limitierender Faktor herausgestellt. Sobald Assets den verfügbaren freien Speicher überschreiten, ist ein rapider Abfall der Verarbeitungsleistung zu verzeichnen.

Bei großen Mengen können DAM-Prozesse sehr gut parallel durchgeführt werden. Stapelweises Hochladen von Assets und Multicore-Prozessoren senken den absoluten Zeitaufwand pro Asset erheblich.

**5. Einschätzen der Hardware-Anforderungen zur Asset-Verarbeitung**

Zur umfangreichen Verarbeitung digitaler Assets sind optimierte Hardware-Ressourcen erforderlich. Die wichtigsten Faktoren hierbei sind die Bildgröße und der Spitzendurchsatz verarbeiteter Bilder.

Weisen Sie mindestens 16 GB Heap zu und konfigurieren Sie den Workflow [!UICONTROL DAM-Update-Asset] so, dass Rohbilder mit dem [Camera Raw-Paket](/help/assets/camera-raw.md) aufgenommen werden.

## Grundlegendes zum System {#understanding-the-system}

Ein typisches DAM-Setup umfasst Endbenutzende, die per Load-Balancer auf DAM zugreifen. Die DAM-Instanz kann Teil eines Cluster-Setups sein, bei dem jede DAM-Instanz in einem Java™ Virtual Machine-Prozess auf einem physischen Rechner oder einer virtuellen Maschine ausgeführt wird. Bei Setups mit einem Rechner wird DAM-Speicher in Form einer RAID-Festplatte bereitgestellt, im Fall eines Cluster-Setups in Form von Managed NAS (Network Attached Storage).

In der folgenden Legende werden Bereiche mit möglichen Leistungsproblemen samt einer Reihe von ggf. anwendbaren Lösungen beschrieben.

**Netzwerkverbindung zu Endbenutzenden** Eine langsame Netzwerkverbindung kann Durchsatzprobleme verursachen, in seltenen Fällen auch Latenzprobleme. Manchmal erhalten Benutzende eine langsame Verbindung vom Internet-Dienstanbieter (Internet Service Provider, ISP), insbesondere bei Intranets. Dies ist ein Anzeichen für eine falsche Netzwerktopologie.

**Temporäres Dateisystem** Ein langsames lokales Dateisystem kann zu Problemen mit der interaktiven Leistung führen. Dies gilt insbesondere für Suchvorgänge, da Suchindizes auf der lokalen Festplatte gespeichert werden. Zudem können Probleme bei der Asset-Verarbeitung auftreten, sofern der Befehlszeilenprozess verwendet wird.

**AEM-DAM Produktsuche** Probleme mit der interaktiven Leistung, die häufig bei Suchvorgängen auftreten, sind auf eine hohe CPU-Auslastung aufgrund einer zu großen Anzahl gleichzeitiger Benutzender oder andere CPU-intensive Prozesse in derselben Instanz zurückzuführen. Durch den Wechsel von virtuellen Maschinen zu dedizierten Maschinen und das Sicherstellen, dass keine weiteren Dienste auf dem Rechner ausgeführt werden, kann die Leistung verbessert werden. Wenn eine hohe CPU-Last durch Asset-Verarbeitung und viele gleichzeitige Benutzende verursacht wird, empfiehlt Day das Hinzufügen weiterer Cluster-Knoten.

**AEM-DAM Workflow** Lang laufende Workflow-Prozesse während der Asset-Aufnahme führen zu Leistungsproblemen bei der Asset-Verarbeitung. Abhängig vom Typ der verarbeiteten Assets kann dies auf eine Überauslastung der CPU hindeuten. Day empfiehlt, die Anzahl der anderen auf dem System ausgeführten Prozesse zu reduzieren und die Anzahl der verfügbaren CPUs durch Hinzufügen von Cluster-Knoten zu erhöhen.

**NAS Connectivity** Eine unzureichende Netzwerkkonnektivität zum NAS verursacht Probleme mit der interaktiven Leistung, weil der Zugriff auf neue Knoten während der Asset-Verarbeitung aufgrund der Netzwerklatenz verlangsamt wird. Außerdem wirkt sich ein langsamer Netzwerkdurchsatz nicht nur negativ auf den Durchsatz aus, sondern auch auf die Leistung bei der Asset-Verarbeitung, denn Ausgabedarstellungen werden langsamer geladen und gespeichert.

Ursachen für eine schlechte Latenz und unzureichenden Durchsatz in einem NAS sind gewöhnlich die Netzwerktopologie oder eine NAS-Überauslastung durch andere Dienste.

**Network Attached Storage (NAS)** Überbeanspruchte NAS-Systeme können zu einer Vielzahl von Problemen führen:

* Geringer Festplattenspeicher ist ein häufig auftretendes Problem, das durch eine ordnungsgemäße Dimensionierung von DAM-Projekten verhindert werden kann.
* Eine hohe Festplattenlatenz führt zu langsamen Zugriffszeiten für CRX und kann Probleme mit der interaktiven Leistung verursachen.
* Ein geringer Datenträgerdurchsatz kann Leistungseinbußen für CQ5 DAM zur Folge haben.

## Testen auf Leistung {#testing-for-performance}

Achten Sie bei jedem DAM-Projekt darauf, Leistungstests durchzuführen, um Engpässe schnell zu erkennen und zu beseitigen. Berücksichtigen Sie dazu die folgenden Checkpoints:

1. Simulieren Sie im Rahmen von End-to-End-Leistungstests mit JMeter eine beispielhafte Such- und Browsing-Sitzung, um Probleme mit der interaktiven Leistung zu erkennen.
1. Führen Sie mit JMeter Durchsatz- und Latenztests auf einem Client-Computer durch, um topologiebezogene Probleme auszuschließen.
1. Nehmen Sie im Rahmen standardisierter Tests zur Asset-Verarbeitung einige Beispiel-Assets auf und messen Sie den Zeitaufwand. Prozesse zur externen Workflow-Integration sollten dabei eingeschlossen sei.
1. Überwachen Sie die CPU-, Datenträger- und Speicherauslastung von jedem Cluster-Knoten.
1. Diagnostizieren Sie die CRX-Lese- und -Schreibleistung, um Probleme zu identifizieren, die nicht mit Verarbeitungsvorgängen im Zusammenhang stehen.
1. Überwachen Sie die Netzwerklatenz und den Durchsatz vom DAM-Cluster zu Ihrem NAS.
1. Testen Sie die Lese- und Schreibleistung sowie die Festplattenlatenz direkt auf dem NAS, sofern möglich.

## Optimieren im Falle von Engpässen {#tweaking-bottlenecks}

Die folgenden Leistungsoptimierungen wurden bisher in Projekten angewendet:

* Generieren selektiver Ausgabedarstellungen: Generieren Sie nur die von Ihnen benötigten Ausgabedarstellungen, indem Sie dem Workflow für die Asset-Verarbeitung Bedingungen hinzufügen, damit aufwendigere Ausgabedarstellungen nur für ausgewählte Assets erzeugt werden.
* Zwischen Instanzen freigegebener Datenspeicher: Wenn nicht genügend Festplattenspeicher vorhanden ist, kann sich hierdurch die Menge des benötigten Speicherplatzes deutlich reduzieren. Dies ist allerdings mit einem höheren Konfigurationsaufwand und dem Verlust der automatischen Datenspeicherbereinigung verbunden.

## Weiterführende Literatur {#further-reading}

* [Analysieren von langsamen und blockierten Prozessen](https://helpx.adobe.com/de/experience-manager/kb/AnalyzeSlowAndBlockedProcesses.html)
