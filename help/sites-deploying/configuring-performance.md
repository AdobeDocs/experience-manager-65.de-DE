---
title: Leistungsoptimierung
seo-title: Performance Optimization
description: Erfahren Sie, wie Sie bestimmte Aspekte von AEM konfigurieren, um die Leistung zu optimieren.
seo-description: Learn how to configure certain aspects of AEM to optimize performance.
uuid: a4d9fde4-a4c7-4ee5-99b6-29b0ee7dc35b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
discoiquuid: 80118cd1-73e1-4675-bbdf-85d66d150abc
feature: Configuring
exl-id: 5b0c9a8c-0f5f-46ee-a455-adb9b9d27270
source-git-commit: 9defa6d1843007e9375d839f72f6993c691a37c0
workflow-type: tm+mt
source-wordcount: '6503'
ht-degree: 27%

---

# Leistungsoptimierung {#performance-optimization}

>[!NOTE]
>
>Allgemeine Richtlinien zur Leistung finden Sie im Abschnitt [Leistungsrichtlinien](/help/sites-deploying/performance-guidelines.md) Seite.
>
>Weitere Informationen zur Fehlerbehebung und zur Behebung von Leistungsproblemen finden Sie unter [Leistungsstruktur](/help/sites-deploying/performance-tree.md).
>
>Sie können auch einen Knowledge Base-Artikel unter [Tipps zur Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=en).

Ein wichtiges Problem ist die Zeit, die Ihre Website benötigt, um auf Besucheranfragen zu reagieren. Obwohl dieser Wert für jede Anforderung unterschiedlich ist, kann ein durchschnittlicher Zielwert definiert werden. Sobald sich gezeigt hat, dass dieser Wert sowohl erreichbar als auch wartbar ist, kann er verwendet werden, um die Leistung der Website zu überwachen und die Entwicklung potenzieller Probleme anzuzeigen.

Die Antwortzeiten, die Sie anstreben, unterscheiden sich in der Autoren- und Veröffentlichungsumgebung und spiegeln die verschiedenen Merkmale der Zielgruppe wider:

## Autorenumgebung {#author-environment}

Diese Umgebung wird von Autoren verwendet, die Inhalte eingeben und aktualisieren. Es muss einige Benutzer berücksichtigen, die jeweils eine hohe Anzahl leistungsintensiver Anforderungen generieren, wenn sie Inhaltsseiten und die einzelnen Elemente auf diesen Seiten aktualisieren.

## Veröffentlichungsumgebung {#publish-environment}

Diese Umgebung enthält Inhalte, die Sie Ihren Benutzern zur Verfügung stellen. Hier ist die Anzahl der Anfragen noch größer und die Geschwindigkeit ist ebenso wichtig. Da die Anforderungen jedoch weniger dynamisch sind, können zusätzliche leistungssteigernde Mechanismen angewendet werden. wie das Zwischenspeichern des Inhalts oder den Lastenausgleich.

>[!NOTE]
>
>* Folgen Sie nach der Konfiguration zur Leistungsoptimierung der Anleitung in [Tough Day](/help/sites-developing/tough-day.md), um die Umgebung unter starker Belastung zu testen.
>* Siehe auch [Tipps zur Leistungsoptimierung.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=en)


## Methode zur Leistungsoptimierung {#performance-optimization-methodology}

Eine Leistungsoptimierungsmethode für AEM Projekte kann in fünf einfachen Regeln zusammengefasst werden, die zur Vermeidung von Leistungsproblemen von Anfang an befolgt werden können:

1. [Zeit für die Optimierung einplanen](#planning-for-optimization)
1. [Reale Situationen simulieren](#simulate-reality)
1. [Konkrete Ziele festlegen](#establish-solid-goals)
1. [Relevante Maßnahmen treffen](#stay-relevant)
1. [Agile Iterationszyklen](#agile-iteration-cycles)

Diese Regeln gelten für Webprojekte im Allgemeinen und sind für Projekt-Manager und Systemadministratoren relevant, um sicherzustellen, dass ihre Projekte bei Einführungszeiten nicht mit Leistungsproblemen konfrontiert werden.

### Zeit für die Optimierung einplanen {#planning-for-optimization}

![chlimage_1-3](assets/chlimage_1-3.jpeg)

Planen Sie etwa 10 % der Projektarbeit für die Leistungsoptimierungsphase. Die tatsächlichen Anforderungen an die Leistungsoptimierung hängen von der Komplexität eines Projekts und der Erfahrung des Entwicklungsteams ab. Obwohl Ihr Projekt (letztendlich) möglicherweise nicht die zugewiesene Zeit benötigt, empfiehlt es sich, immer die Leistungsoptimierung in der vorgeschlagenen Region zu planen.

Wenn möglich, sollte ein Projekt zunächst für eine begrenzte Zielgruppe sanft gestartet werden, um reale Erlebnisse zu sammeln und weitere Optimierungen durchzuführen, ohne dass ein zusätzlicher Druck entsteht, der auf eine vollständige Ankündigung folgt.

Nach der Live-Schaltung ist die Leistungsoptimierung noch nicht abgeschlossen. Jetzt kommt es zu einer &quot;echten&quot;Belastung Ihres Systems. Es ist wichtig, nach dem Start zusätzliche Anpassungen zu planen.

Da sich die Systemlast ändert und sich die Leistungsprofile Ihres Systems im Laufe der Zeit verändern, sollte in Intervallen von 6 bis 12 Monaten eine Leistungsoptimierung oder Konsistenzprüfung geplant werden.

### Reale Situationen simulieren {#simulate-reality}

![chlimage_1-4](assets/chlimage_1-4.jpeg)

Wenn Sie mit einer Website live gehen und nach dem Launch feststellen, dass Leistungsprobleme auftreten, liegt dies wahrscheinlich daran, dass Ihre Leistungs- und Leistungstests die Realität nicht ausreichend simulieren.

Die Simulation der Realität ist schwierig, und wie viel Aufwand Sie investieren wollen, um &quot;real&quot;zu werden, hängt von der Art Ihres Projekts ab. &quot;Real&quot;bedeutet nicht nur &quot;echter Code&quot;und &quot;echter Traffic&quot;, sondern auch &quot;realer Inhalt&quot;, insbesondere in Bezug auf Inhaltsgröße und -struktur. Ihre Vorlagen verhalten sich je nach Größe und Struktur des Repositorys möglicherweise unterschiedlich.

### Konkrete Ziele festlegen {#establish-solid-goals}

![chlimage_1-5](assets/chlimage_1-5.jpeg)

Die Bedeutung konkreter Leistungsziele sollte nicht unterschätzt werden. Oft ist es schwierig, diese Ziele zu ändern, nachdem Menschen sich auf bestimmte Leistungsziele konzentriert haben, selbst wenn sie auf Annahmen beruhen.

Die Festlegung guter, solider Leistungsziele ist wirklich einer der schwierigsten Bereiche. Oft ist es am besten, von einer vergleichbaren Website (z. B. dem Vorgänger der neuen Website) reale Lebensprotokolle und Benchmarks zu sammeln.

### Relevante Maßnahmen treffen {#stay-relevant}

![chlimage_1-6](assets/chlimage_1-6.jpeg)

Es ist wichtig, jeweils einen Engpass zu optimieren. Wenn Sie versuchen, Dinge parallel zu erledigen, ohne die Auswirkungen der einen Optimierung zu überprüfen, können Sie die Frage verlieren, welche Optimierungsmaßnahme hilfreich war.

### Agile Iterationszyklen {#agile-iteration-cycles}

![chlimage_1-7](assets/chlimage_1-7.jpeg)

Die Leistungsoptimierung ist ein iterativer Prozess, der Messung, Analyse, Optimierung und Validierung umfasst, bis das Ziel erreicht ist. Um diesen Aspekt zu berücksichtigen, implementieren Sie nach jeder Iteration einen agilen Validierungsprozess in der Optimierungsphase und nicht einen schwereren Testprozess.

Dieser Fokus bedeutet, dass der Entwickler, der die Optimierung implementiert, schnell feststellen kann, ob die Optimierung bereits das Ziel erreicht hat. Diese Informationen sind nützlich, da die Optimierung bei Erreichen des Ziels vorbei ist.

## Allgemeine Leistungsrichtlinien {#basic-performance-guidelines}

Im Allgemeinen sollten nicht gecachte HTML-Anforderungen weniger als 100 ms benötigen. Konkret wird Folgendes empfohlen:

* 70 % der Seitenanfragen sollten in weniger als 100 ms beantwortet werden.
* 25 % der Seitenanforderungen sollten innerhalb von 100 ms bis 300 ms beantwortet werden.
* 4 % der Seitenanforderungen sollten innerhalb von 300 ms bis 500 ms beantwortet werden.
* 1 % der Seitenanforderungen sollten innerhalb von 500 ms bis 1000 ms beantwortet werden.
* Keine Seite sollte langsamer als 1 Sekunde reagieren.

Die obigen Zahlen gehen von folgenden Bedingungen aus:

* Gemessen in der Veröffentlichungsumgebung (kein zusätzlicher Aufwand wie bei einer Autorenumgebung)
* Gemessen auf dem Server (kein zusätzlicher Netzwerkaufwand)
* Nicht zwischengespeichert (kein AEM-Ausgabe-Cache, kein Dispatcher-Cache)
* Nur für komplexe Objekte mit vielen Abhängigkeiten (HTML, JS, PDF usw.)
* Keine andere Last auf dem System

Es gibt einige Probleme, die häufig zu Leistungsproblemen beitragen, darunter die folgenden:

* Ineffiziente Speicherung im Dispatcher-Cache
* Verwendung von Abfragen in normalen Anzeigevorlagen

JVM- und Betriebssystemebenen-Optimierungen führen in der Regel nicht zu signifikanten Leistungssteigerungen und sollten daher am Ende des Optimierungszyklus durchgeführt werden.

Die Art und Weise, wie ein Content-Repository strukturiert ist, kann sich auch auf die Leistung auswirken. Für eine optimale Leistung sollte die Anzahl der untergeordneten Knoten, die an einzelne Knoten in einem Inhalts-Repository angehängt werden, 1.000 nicht überschreiten (in der Regel).

Ihre besten Freunde während einer üblichen Leistungsoptimierungsübung sind:

* Die `request.log`
* Komponentenbasiertes Timing
* Ein Java™ Profiler.

### Leistung beim Laden und Bearbeiten digitaler Assets {#performance-when-loading-and-editing-digital-assets}

Aufgrund der großen Datenmenge, die beim Laden und Bearbeiten digitaler Assets benötigt wird, kann die Leistung zu einem Problem werden.

Zwei Dinge wirken sich auf die Leistung aus:

* CPU: mehrere Kerne ermöglichen eine flüssigere Codeumsetzung
* Festplatte - parallele RAID-Festplatten erreichen dasselbe

Beachten Sie Folgendes, um die Leistung zu verbessern:

* Wie viele Assets werden pro Tag hochgeladen? Eine gute Schätzung erhalten Sie mit folgender Formel: 

![chlimage_1-77](assets/chlimage_1-77.png)

* Der Zeitraum, in dem Änderungen vorgenommen werden (normalerweise die Dauer des Arbeitstags, mehr für internationale Vorgänge).
* Die durchschnittliche Größe der hochgeladenen Bilder (und die Größe der pro Bild generierten Darstellungen) in Megabyte.
* Bestimmen Sie die durchschnittliche Datenrate: 

![chlimage_1-78](assets/chlimage_1-78.png)

* 80 % aller Bearbeitungen erfolgen in 20 % der Zeit. In Spitzenzeiten beträgt die Datenrate also viermal so viel wie im Durchschnitt. Eine solche Leistung ist Ihr Ziel.

## Performance-Überwachung {#performance-monitoring}

Die Leistung (oder das Fehlen) ist eines der ersten Dinge, die Ihre Benutzer bemerken. Wie bei jeder Anwendung mit einer Benutzeroberfläche ist die Leistung von entscheidender Bedeutung. Um die Leistung Ihrer AEM zu optimieren, überwachen Sie verschiedene Attribute der Instanz und deren Verhalten.

Weitere Informationen zur Leistungsüberwachung finden Sie unter [Überwachen der Leistung](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance).

Die Probleme, die Leistungsprobleme verursachen, lassen sich oft nur schwer nachvollziehen, selbst wenn ihre Auswirkungen leicht erkennbar sind.

Ein grundlegender Ausgangspunkt ist ein gutes Wissen über Ihr System, wenn es normal arbeitet. Wenn Sie nicht wissen, wie Ihre Umgebung bei ordnungsgemäßer Ausführung &quot;aussieht&quot;und &quot;sich&quot;verhält, ist es schwierig, das Problem zu finden, wenn sich die Leistung verschlechtert. Verbringen Sie Zeit mit der Untersuchung Ihres Systems, wenn es reibungslos läuft, und stellen Sie sicher, dass die Erfassung von Leistungsinformationen eine fortlaufende Aufgabe ist. Dies bietet Ihnen eine Vergleichsgrundlage für den Fall, dass die Leistung beeinträchtigt wird.

Das folgende Diagramm veranschaulicht den möglichen Pfad von AEM-Inhalten, und damit die Anzahl der unterschiedlichen Elemente, die die Leistung beeinflussen können.

![chlimage_1-79](assets/chlimage_1-79.png)

Leistung wird auch durch das Verhältnis zwischen Volumen und Kapazität bestimmt:

* **Volumen**: Die Menge an Ausgabedaten, die vom System verarbeitet und bereitgestellt wird.
* **Kapazität** - die Fähigkeit des Systems, das Volumen bereitzustellen.

Die Leistung kann an verschiedenen Stellen der gesamten Webkette veranschaulicht werden.

![chlimage_1-80](assets/chlimage_1-80.png)

Es gibt verschiedene Funktionsbereiche, die häufig für die Leistungsbeeinträchtigung verantwortlich sind:

* Caching
* Anwendungs-Code (Ihr Projekt)
* Suchfunktion

### Grundregeln für die Leistung {#basic-rules-regarding-performance}

Bei der Leistungsoptimierung sollten bestimmte Regeln beachtet werden:

* Leistungsoptimierung *must* Teil jedes Projekts sein.
* Optimieren Sie nicht frühzeitig im Entwicklungszyklus.
* Die Leistung ist nur so gut wie das schwächste Glied.
* Denken Sie immer an Kapazität und Volumen.
* Optimieren Sie wichtige Dinge zuerst.
* Optimieren Sie nie ohne *realistisch* Ziele.

>[!NOTE]
>
>Beachten Sie, dass der Mechanismus zur Leistungsmessung häufig genau das beeinflusst, was Sie messen möchten. Versuchen Sie, diese Diskrepanzen zu berücksichtigen und so viel ihrer Auswirkungen wie möglich zu beseitigen. insbesondere Browser-Plug-ins nach Möglichkeit deaktiviert werden sollten.

## Konfiguration zur Leistungsoptimierung {#configuring-for-performance}

Bestimmte Aspekte von AEM (bzw. des zugrunde liegenden Repositorys) können so konfiguriert werden, dass die Leistung optimiert wird. Im Folgenden finden Sie Möglichkeiten und Vorschläge. Sie müssen sich vor der Änderung sicher sein, ob und wie Sie die betreffende Funktion verwenden.

>[!NOTE]
>
>Siehe [Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=en).

### Suchindizierung {#search-indexing}

Ab AEM 6.0 verwendet Adobe Experience Manager eine Oak-basierte Repository-Architektur.

Die aktualisierten Indizierungsinformationen finden Sie hier:

* [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md)
* [Abfragen und Indizierung](/help/sites-deploying/queries-and-indexing.md)

### Gleichzeitige Verarbeitung von Workflows {#concurrent-workflow-processing}

Um die Leistung zu verbessern, begrenzen Sie die Anzahl der gleichzeitig ausgeführten Workflow-Prozesse. Standardmäßig verarbeitet die Workflow-Engine so viele Workflows parallel wie Prozessoren, die für die Java™-VM verfügbar sind. Wenn Workflow-Schritte große Mengen von Verarbeitungsressourcen (RAM oder CPU) erfordern, kann es vorkommen, dass durch das gleichzeitige Ausführen mehrerer dieser Workflows die Serverressourcen stark beansprucht werden.

Wenn beispielsweise Bilder (oder DAM-Assets im Allgemeinen) hochgeladen werden, importieren Workflows die Bilder automatisch in DAM. Bilder sind häufig mit hoher Auflösung und können problemlos Hunderte von MB Heap für die Verarbeitung verbrauchen. Die parallele Handhabung dieser Bilder stellt eine hohe Belastung des Speicher-Subsystems und des Speicherbereinigers dar.

Die Workflow-Engine verwendet Apache Sling-Auftragswarteschlangen für die Verarbeitung und Planung der Verarbeitung von Arbeitselementen. Die folgenden Auftragswarteschlangendienste wurden standardmäßig in der Apache Sling Job Queue Configuration Service Factory zur Verarbeitung von Workflow-Aufgaben erstellt:

* Granite Workflow-Warteschlange: Für die meisten Workflow-Schritte, wie diejenigen zur Verarbeitung von DAM-Assets, wird der Granite Workflow-Warteschlangendienst verwendet.
* Granite Workflow Auftragswarteschlange für externe Prozesse: Dieser Dienst wird für spezielle externe Workflow-Schritte verwendet, die typischerweise für die Kontaktaufnahme mit einem externen System und die Abfrage von Ergebnissen verwendet werden. Beispielsweise wird der Schritt zum Extrahieren von InDesign-Medien als externer Prozess implementiert. Die Workflow-Engine verwendet die externe Warteschlange zur Verarbeitung der Abfrage. (Siehe [com.day.cq.workflow.exec.WorkflowExternalProcess](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/workflow/exec/WorkflowExternalProcess.html).)

Konfigurieren Sie diese Dienste, um die maximale Anzahl der parallel ausgeführten Workflow-Prozesse zu beschränken.

>[!NOTE]
>
>Hinweis: Die Konfiguration dieser Auftragswarteschlangen hat Auswirkungen auf alle Workflows, es sei denn, Sie haben eine Auftragswarteschlange für ein bestimmtes Workflow-Modell erstellt (siehe [Konfigurieren einer Warteschlange für ein bestimmtes Workflow-Modell](/help/sites-deploying/configuring-performance.md#configure-the-queue-for-a-specific-workflow) weiter unten).

#### Konfiguration im Repository {#configuration-in-the-repo}

Wenn Sie die Dienste konfigurieren [Verwenden eines sling:OsgiConfig -Knotens](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository)müssen Sie die PID der vorhandenen Dienste finden, z. B.: org.apache.sling.event.jobs.QueueConfiguration.370aad73-d01b-4a0b-abe4-20198d85f705. Sie können den PID mithilfe der Webkonsole ermitteln.

Konfigurieren Sie die Eigenschaft mit dem Namen `queue.maxparallel`.

#### Konfiguration in der Web-Konsole  {#configuration-in-the-web-console}

Um diese Dienste mithilfe [der Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) zu konfigurieren, suchen Sie die vorhandenen Konfigurationselemente unter der Apache Sling Job Queue Configuration Service Factory.

Konfigurieren Sie die Eigenschaft &quot;Maximum Parallel Jobs&quot;.

### Konfigurieren der Warteschlange für einen spezifischen Workflow {#configure-the-queue-for-a-specific-workflow}

Erstellen Sie eine Auftragswarteschlange für ein bestimmtes Workflow-Modell, damit Sie die Auftragsverarbeitung für dieses Workflow-Modell konfigurieren können. Auf diese Weise beeinflussen Ihre Konfigurationen die Verarbeitung für einen bestimmten Workflow, während die Konfiguration der standardmäßigen Granite-Workflow-Warteschlange die Verarbeitung anderer Workflows steuert.

Wenn Workflow-Modelle ausgeführt werden, erstellen sie Sling-Aufträge für ein bestimmtes Thema. Standardmäßig stimmt das Thema mit den Themen überein, die für die allgemeine Granite-Workflow-Warteschlange oder die Granite-Workflow-Warteschlange für externe Prozessaufträge konfiguriert sind:

* `com/adobe/granite/workflow/job*`
* `com/adobe/granite/workflow/external/job*`

Die tatsächlich von Workflow-Modellen erstellten Auftragsthemen enthalten modellspezifische Suffixe. Beispielsweise erzeugt das Workflow-Modell **DAM Update Asset** Aufträge mit folgendem Thema:

`com/adobe/granite/workflow/job/etc/workflow/models/dam/update_asset/jcr_content/model`

Daher können Sie eine Auftragswarteschlange für das Thema erstellen, das dem Auftragsthema Ihres Workflow-Modells entspricht. Die Konfiguration der Leistungseigenschaften der Warteschlange wirkt sich nur auf das Workflow-Modell aus, das die Aufträge generiert, die dem Warteschlangenthema entsprechen.

Im Folgenden wird ein Workflow **DAM Update Asset** als Beispiel verwendet, um eine Auftragswarteschlange für einen Workflow zu erstellen.

1. Führen Sie das Workflow-Modell aus, für das Sie die Auftragswarteschlange erstellen möchten, sodass Themenstatistiken generiert werden. Fügen Sie beispielsweise ein Bild zu Assets hinzu, um den Workflow **DAM-Update-Asset** auszuführen.
1. Öffnen Sie die Sling Jobs-Konsole (`https://<host>:<port>/system/console/slingevent`).
1. Erfahren Sie mehr über die Workflow-bezogenen Themen in der Konsole. Für DAM Update Asset werden die folgenden Themen gefunden:

   * `com/adobe/granite/workflow/external/job/etc/workflow/models/dam/update_asset/jcr_content/model`
   * `com/adobe/granite/workflow/job/etc/workflow/models/dam/update_asset/jcr_content/model`
   * `com/adobe/granite/workflow/job/etc/workflow/models/dam-xmp-writeback/jcr_content/model`

1. Erstellen Sie für jedes Thema eine Auftragswarteschlange. Um eine Auftragswarteschlange zu erstellen, erstellen Sie eine Werkskonfiguration für den Factory-Dienst Apache Sling Job Queue .

   Die Werkskonfigurationen sind ähnlich der Granite Workflow-Warteschlange, die in [Gleichzeitige Workflow-Verarbeitung](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing) beschrieben wird, mit der Ausnahme, dass die Themen-Eigenschaft mit dem Thema Ihrer Workflow-Aufträge übereinstimmt.

### AEM DAM Asset-Synchronisierungsdienst {#cq-dam-asset-synchronization-service}

Die `AssetSynchronizationService` wird verwendet, um Assets aus bereitgestellten Repositorys zu synchronisieren (unter anderem LiveLink, Documentum®). Standardmäßig führt diese Synchronisation alle 300 Sekunden (5 Minuten) eine regelmäßige Prüfung durch. Wenn Sie also keine bereitgestellten Repositorys verwenden, können Sie diesen Dienst deaktivieren.

Die Deaktivierung des Dienstes erfolgt durch [Konfigurieren des OSGi-Dienstes](/help/sites-deploying/configuring-osgi.md) **CQ DAM Asset Synchronization Service** , um **Synchronisierungszeitraum** ( `scheduler.period`) auf (mindestens) ein Jahr (definiert in Sekunden).

### Mehrere DAM-Instanzen {#multiple-dam-instances}

Das Bereitstellen mehrerer DAM-Instanzen kann in folgenden Fällen die Leistung steigern: 

* Sie haben eine hohe Belastung durch das regelmäßige Hochladen vieler Assets für die Autorenumgebung. Hier kann eine separate DAM-Instanz für den Service-Autor bereitgestellt werden.
* Sie verfügen über mehrere Teams an weltweiten Standorten (z. B. USA, Europa, Asien).

Zusätzliche Erwägungen sind:

* Trennung von unfertiger Arbeit in der Autorenumgebung von abgeschlossener Arbeit in der Veröffentlichungsumgebung
* Trennen von internen Benutzern auf der Autoreninstanz von externen Besuchern/Benutzern auf der Veröffentlichungsinstanz (z. B. Agenten, Pressevertreter, Kunden und Studenten).

## Best Practices zur Qualitätssicherung {#best-practices-for-quality-assurance}

Die Leistung ist für Ihre Veröffentlichungsumgebung von größter Bedeutung. Daher müssen Sie bei der Implementierung Ihres Projekts die Leistungstests für die Veröffentlichungsumgebung sorgfältig planen und analysieren.

In diesem Abschnitt erhalten Sie einen Überblick über Probleme bei der Definition eines Testkonzepts speziell für Leistungstests in der *Veröffentlichungsumgebung*. Diese Informationen sind in erster Linie für QA-Techniker, Projektmanager und Systemadministratoren von Interesse.

Im Folgenden wird die übliche Vorgehensweise bei der Durchführung von Leistungstests bei einer AEM-Anwendung in der *Veröffentlichungsumgebung* beschrieben. Dieser Leistungstest umfasst die folgenden fünf Phasen:

* [Überprüfung des Wissens](#verification-of-knowledge)
* [Definition des Umfangs ](#scope-definition)
* [Testmethoden](#test-methodologies)
* [Definition von Leistungszielen ](#defining-the-performance-goals)
* [Optimierung](#optimization)

Die Steuerung ist ein zusätzlicher, allumfassender Prozess - notwendig, aber nicht auf Tests beschränkt.

### Überprüfung des Wissens {#verification-of-knowledge}

Ein erster Schritt besteht darin, die grundlegenden Informationen zu dokumentieren, die Sie kennen müssen, bevor Sie mit dem Testen beginnen können:

* Die Architektur Ihrer Testumgebung
* Eine Anwendungszuordnung mit den internen Elementen, die getestet werden müssen (sowohl in Isolation als auch in Kombination)

#### Testarchitektur {#test-architecture}

Dokumentieren Sie die Architektur der Testumgebung, die für Ihre Leistungstests verwendet wird.

Sie benötigen eine Wiedergabe Ihrer geplanten Veröffentlichungsumgebung in der Produktion, zusammen mit dem Dispatcher und dem Load Balancer.

#### App Map {#application-map}

Verschaffen Sie sich einen klaren Überblick, aus dem Sie eine Karte der gesamten Anwendung erstellen können (diese Karte kann bereits aus Tests in der Autorenumgebung stammen).

Eine Diagrammdarstellung der internen Elemente der Anwendung kann einen Überblick über die Prüfanforderungen geben. mit Farbkodierung kann es auch als Grundlage für die Berichterstellung dienen.

### Definition des Umfangs {#scope-definition}

Eine Anwendung verfügt in der Regel über eine Reihe von Anwendungsfällen. Einige Anwendungsfälle sind wichtig, andere weniger.

Um den Umfang der Leistungstests auf die Veröffentlichung zu konzentrieren, empfiehlt Adobe, Folgendes zu definieren:

* Die wichtigsten Geschäftsanwendungsfälle
* Die wichtigsten technischen Anwendungsfälle

Die Anzahl der Anwendungsfälle liegt bei Ihnen, sollte jedoch auf eine einfach zu handhabende Zahl beschränkt sein (z. B. zwischen 5 und 10).

Sobald die wichtigsten Anwendungsfälle ausgewählt sind, können die wichtigsten Leistungsindikatoren (Key Performance Indicators, KPI) und die Tools, mit denen sie gemessen werden, für jeden Fall definiert werden. Beispiele für häufig verwendete KPIs:

* Ende der Antwortzeit
* Servlet-Reaktionszeit
* Reaktionszeit für eine einzelne Komponente
* Reaktionszeit für die Dienste
* Anzahl der inaktiven Threads im Thread-Pool
* Anzahl freier Verbindungen
* Systemressourcen wie CPU- und I/O-Zugriff

### Testmethoden {#test-methodologies}

Dieses Konzept umfasst vier Szenarien, in denen die Leistungsziele definiert und getestet werden:

* Einzelkomponenten-Tests
* Kombinierte Komponententests
* *Wird live geschaltet* scenario
* Fehlerszenarien

Basierend auf den folgenden Grundsätzen.

#### Belastungsgrenze der Komponente  {#component-breakpoints}

* Jede Komponente hat eine bestimmte Belastungsgrenze in Bezug auf die Leistung. Das heißt, eine Komponente kann zeigen, dass eine gute Leistung bis zu einem bestimmten Punkt erreicht ist, woraufhin die Leistung schnell abnimmt.
* Um einen vollständigen Überblick über die Anwendung zu erhalten, müssen Sie zunächst feststellen, wann bei Ihren Komponenten diese Belastungsgrenze erreicht ist.
* Um den Breakpoint zu finden, den Sie für einen Belastungstest durchführen können, bei dem Sie über einen Zeitraum die Anzahl der Benutzer erhöhen, um eine zunehmende Belastung zu erzeugen. Durch die Überwachung dieser Last und der Antwort der Komponenten wird ein spezifisches Leistungsverhalten festgestellt, wenn der Belastungspunkt der Komponente erreicht ist. Der Punkt kann anhand der Anzahl der gleichzeitigen Transaktionen pro Sekunde sowie der Anzahl der gleichzeitigen Benutzer qualifiziert werden (wenn die Komponente auf diese KPI reagiert).
* Diese Informationen können dann als Benchmark für Verbesserungen dienen, die Effizienz der verwendeten Maßnahmen angeben und bei der Definition von Testszenarien helfen.

#### Transaktionen  {#transactions}

* Der Begriff Transaktion wird verwendet, um die Anforderung einer vollständigen Webseite einschließlich der Seite selbst und aller nachfolgenden Aufrufe darzustellen. Das heißt die Seitenanforderung, alle AJAX Aufrufe, Bilder und andere Objekte **Drilldown für Anfragen**.
* Um jede Anforderung vollständig zu analysieren, können Sie jedes Element des Aufrufstapels darstellen und dann die durchschnittliche Verarbeitungszeit für jedes Element addieren.

### Leistungsziele definieren {#defining-the-performance-goals}

Nachdem der Umfang und die zugehörigen KPIs definiert wurden, werden die spezifischen Leistungsziele festgelegt. Dieser Prozess umfasst die Entwicklung von Testszenarien zusammen mit Zielwerten.

Testleistung unter Durchschnitts- und Spitzenbedingungen. Darüber hinaus benötigen Sie &quot;Going Live&quot;-Szenario-Tests, um sicherzustellen, dass Sie bei der erstmaligen Bereitstellung der Website für ein erhöhtes Interesse sorgen können.

Alle Erlebnisse oder Statistiken, die Sie möglicherweise auf einer vorhandenen Website gesammelt haben, können auch bei der Bestimmung künftiger Ziele hilfreich sein. Beispiel: Top-Traffic von Ihrer Live-Website.

#### Tests einzelner Komponenten {#single-component-tests}

Kritische Komponenten müssen getestet werden - sowohl unter durchschnittlichen als auch unter Spitzenbedingungen.

In beiden Fällen können Sie die erwartete Anzahl von Transaktionen pro Sekunde definieren, wenn eine vordefinierte Anzahl von Benutzern das System verwendet.

| Komponente | Testtyp | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Einzelbenutzer auf der Startseite | Durchschnitt | 1 | 1 |  |  |
|  | Spitze | 1 | 3 |  |  |
| Startseite 100 Benutzer | Durchschnitt | 100 | 3 |  |  |
|  | Spitze | 100 | 3 |  |

#### Kombinierte Komponententests {#combined-component-tests}

Durch das Testen der Komponenten in Kombination wird das Anwendungsverhalten besser widergespiegelt. Auch hier müssen die durchschnittlichen und Spitzenbedingungen getestet werden.

| Szenario | Komponente | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Durchschnitt gemischt | Homepage | 10 | 1 |  |  |
|  | Suchen | 10 | 1 |  |  |
|  | Nachrichten | 10 | 2 |  |  |
|  | Ereignisse | 10 | 1 |  |  |
|  | Aktivierungen | 10 | 3 |  | Simulation des Autorenverhaltens. |
| Spitzenwert gemischt | Homepage | 100 | 5 |  |  |
|  | Suchen | 50 | 5 |  |  |
|  | Nachrichten | 100 | 10 |  |  |
|  | Ereignisse | 100 | 10 |  |  |
|  | Aktivierungen | 20 | 20 |  | Simulation des Autorenverhaltens. |

#### Ausführen von Live-Tests {#going-live-tests}

In den ersten Tagen nach der Bereitstellung Ihrer Website können Sie mit einem erhöhten Interesse rechnen. Dieses Szenario ist sogar noch größer als die Spitzenwerte, auf die Sie testen. Adobe empfiehlt, laufende Live-Szenarien zu testen, um sicherzustellen, dass das System diese Situation bewältigen kann.

| Szenario | Testtyp | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Spitzenwert Go-Live | Homepage | 200 | 20 |  |  |
|  | Suchen | 100 | 10 |  |  |
|  | Nachrichten | 200 | 20 |  |  |
|  | Ereignisse | 200 | 20 |  |  |
|  | Aktivierungen | 20 | 20 |  | Simulation des Autorenverhaltens. |

#### Fehlerszenario-Tests {#error-scenario-tests}

Testen Sie Fehlerszenarien, um sicherzustellen, dass das System richtig und angemessen reagiert. Nicht nur in der Art und Weise, wie der Fehler selbst gehandhabt wird, sondern auch in den Auswirkungen, die er auf die Leistung haben kann. Beispiel:

* Was passiert, wenn ein Benutzer einen ungültigen Suchbegriff in das Suchfeld eingibt?
* Was passiert, wenn der Suchbegriff so allgemein ist, dass eine übermäßig große Anzahl an Ergebnissen zurückgegeben wird?

Bei der Konzeption dieser Tests sollte beachtet werden, dass nicht alle Szenarien regelmäßig auftreten. Ihre Auswirkungen auf das gesamte System sind jedoch wichtig.

| Fehlerszenario | Fehlertyp | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Überlastung der Suchkomponente | Suche mit einem globalen Platzhalter (Sternchen) | 10 | 1 |  | Es wird nur nach &amp;ast;&amp;ast;&amp;ast; gesucht. |
|  | Stoppwort | 20 | 2 |  | Suchen nach einem Stoppwort. |
|  | Leere Zeichenfolge | 10 | 1 |  | Suchen nach einer leeren Zeichenfolge. |
|  | Sonderzeichen | 10 | 1 |  | Suchen nach Sonderzeichen. |

#### Belastungstests {#endurance-tests}

Bestimmte Probleme treten erst auf, nachdem das System über einen ununterbrochenen Zeitraum (Stunden oder Tage) ausgeführt wurde. Mit einem Dauertest wird eine konstante durchschnittliche Belastung über einen bestimmten Zeitraum getestet. Jede Leistungsbeeinträchtigung kann dann analysiert werden.

| Szenario | Testtyp | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Belastungstest (72 Stunden) | Homepage | 10 | 1 |  |  |
|  | Suchen | 10 | 1 |  |  |
|  | Nachrichten | 20 | 2 |  |  |
|  | Ereignisse | 10 | 1 |  |  |
|  | Aktivierungen | 1 | 3 |  | Simulation des Autorenverhaltens. |

### Optimierung {#optimization}

Optimieren Sie die Anwendung in den späteren Phasen der Implementierung, um die Leistungsziele zu erreichen und zu maximieren.

Alle vorgenommenen Optimierungen müssen auf folgende Bedingungen hin getestet werden:

* Sie dürfen die Funktionalität nicht beeinträchtigen.
* Sie wurden vor ihrer Veröffentlichung Belastungstests unterzogen.

Für die Lastgenerierung, Leistungsüberwachung und/oder Ergebnisanalyse steht eine Reihe von Tools zur Verfügung:

* [JMeter](https://jmeter.apache.org/)
* [Load Runner](https://www.microfocus.com/en-us/portfolio/performance-engineering/overview)
* [Determyne](https://www.determyne.com/) InsideApps
* [InfraRED](https://www.infraredsoftware.com/)
* [Java™ Interactive Profile](https://jiprof.sourceforge.net/)
* viele weitere ...

Führen Sie nach der Optimierung erneut einen Test durch, um die Auswirkung zu bestätigen.

### Reporting {#reporting}

Die fortlaufende Berichterstattung informiert alle über den Status. Wie bereits bei der Farbcodierung erwähnt, kann für diesen Status die Architekturzuordnung verwendet werden.

Nachdem alle Tests abgeschlossen sind, melden Sie Folgendes:

* Alle festgestellten kritischen Fehler
* Nichtkritische Fragen, die noch eingehender untersucht werden müssen
* Etwaige Annahmen während der Tests
* Etwaige Empfehlungen, die sich aus den Tests ergeben

## Leistungsoptimierung bei Verwendung des Dispatchers {#optimizing-performance-when-using-the-dispatcher}

Die [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) ist das Caching- und/oder Lastenausgleichstool der Adobe. Wenn Sie den Dispatcher verwenden, sollten Sie erwägen, Ihre Website auf die Cache-Leistung zu optimieren.

>[!NOTE]
>
>Dispatcher-Versionen sind AEM unabhängig, die Dispatcher-Dokumentation ist jedoch in die AEM-Dokumentation eingebettet. Verwenden Sie immer die Dispatcher-Dokumentation, die in der Dokumentation für die neueste Version der AEM eingebettet ist.
>
>Sie wurden möglicherweise zu dieser Seite umgeleitet, wenn Sie einen Link zur Dispatcher-Dokumentation befolgt haben, die in die Dokumentation für eine frühere Version von AEM eingebettet ist.

Der Dispatcher bietet mehrere integrierte Mechanismen, mit denen Sie die Leistung optimieren können, wenn Ihre Website diese nutzt. In diesem Abschnitt erfahren Sie, wie Sie Ihre Website entwerfen, um die Vorteile der Zwischenspeicherung zu maximieren.

>[!NOTE]
>
>Es kann Ihnen helfen, sich zu merken, dass der Dispatcher den Cache auf einem Standard-Webserver speichert. Wenn Sie diese Informationen kennen, können Sie alles zwischenspeichern, das Sie als Seite speichern und über eine URL anfordern können. Außerdem können Sie keine anderen Elemente wie Cookies, Sitzungsdaten und Formulardaten speichern.
>
>Im Allgemeinen umfassen zahlreiche Caching-Strategien die Auswahl guter URLs und die Nichtverwendung dieser zusätzlichen Daten.
>
>Mit Dispatcher Version 4.1.11 können Sie auch Antwort-Header zwischenspeichern; siehe [Caching von HTTP-Antwort-Headern](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#configuring-the-dispatcher-cache-cache).

### Berechnung des Dispatcher-Cache-Verhältnisses {#calculating-the-dispatcher-cache-ratio}

Mit der Cache-Verhältnis-Formel wird der ungefähre Prozentsatz der vom Cache gehandhabten Anforderungen verglichen mit der Gesamtzahl der Systemanforderungen berechnet. Um das Cache-Verhältnis zu berechnen, benötigen Sie Folgendes:

* Die Gesamtzahl der Anforderungen. Diese Information können Sie der Apache-Datei `access.log` entnehmen. Weitere Informationen finden Sie unter [offizielle Apache-Dokumentation](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

* Die Anzahl der Anforderungen, die von der Veröffentlichungsinstanz bereitgestellt wurden. Diese Information können Sie der Datei `request.log` der Instanz entnehmen. Weitere Informationen finden Sie unter [Interpretieren der Datei request.log](/help/sites-deploying/monitoring-and-maintaining.md#interpreting-the-request-log) und [Auffinden der Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#finding-the-log-files).

Die Formel zur Berechnung des Cache-Verhältnisses lautet:

* (Die Gesamtzahl der Anfragen **minus** der Anzahl der Anfragen in der Veröffentlichungsumgebung) **geteilt durch** die Gesamtanzahl der Anfragen.

Wenn beispielsweise die Gesamtzahl der Anfragen 129491 und die Anzahl der von der Veröffentlichungsinstanz bereitgestellten Anforderungen 58959 beträgt, beträgt das Cache-Verhältnis: **(129491 - 58959)/129491= 54,5%**.

Wenn Sie keine 1-zu-1-Kopplung zwischen Publisher und Dispatcher haben, fügen Sie Anforderungen von allen Dispatchern und Herausgebern hinzu, um eine genaue Messung zu erhalten. Siehe auch [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md).

>[!NOTE]
>
>Für eine optimale Leistung empfiehlt Adobe ein Cache-Verhältnis von 90 % bis 95 %.

#### Verwenden einer einheitlichen Seitencodierung  {#using-consistent-page-encoding}

Mit der Dispatcher-Version 4.1.11 können Sie Antwortheader zwischenspeichern. Wenn Sie keine Antwortheader im Dispatcher zwischenspeichern, können Probleme auftreten, wenn Sie die Seitenkodierungsinformationen in der Kopfzeile speichern. In diesem Fall wird die Standardkodierung des Webservers für die Seite verwendet, wenn der Dispatcher eine Seite aus dem Cache bereitstellt. Es gibt zwei Möglichkeiten, dieses Problem zu vermeiden:

* Wenn Sie nur eine Kodierung verwenden, stellen Sie sicher, dass die auf dem Webserver verwendete Kodierung mit der Standardkodierung der AEM Website übereinstimmt.
* Verwenden Sie zum Festlegen der Kodierung einen `<META>` -Tag im HTML `head` wie im folgenden Beispiel:

```xml
        <META http-equiv="Content-Type" content="text/html; charset=EUC-JP">
```

#### Vermeiden von URL-Parametern {#avoid-url-parameters}

Vermeiden Sie nach Möglichkeit URL-Parameter für Seiten, die Sie zwischenspeichern möchten. Wenn Sie beispielsweise über eine Bildergalerie verfügen, wird die folgende URL nie zwischengespeichert (es sei denn, der Dispatcher ist [konfiguriert](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#configuring-the-dispatcher-cache-cache)):

```xml
www.myCompany.com/pictures/gallery.html?event=christmas&amp;page=1
```

Sie können diese Parameter jedoch wie folgt in die Seiten-URL einfügen:

```xml
www.myCompany.com/pictures/gallery.christmas.1.html
```

>[!NOTE]
>
>Diese URL ruft dieselbe Seite und Vorlage auf wie `gallery.html`. In der Vorlagendefinition können Sie angeben, welches Skript die Seite rendert, oder Sie können dasselbe Skript für alle Seiten verwenden.

#### Anpassen nach URL  {#customize-by-url}

Wenn Sie Benutzern erlauben, die Schriftgröße (oder eine andere Layoutanpassung) zu ändern, stellen Sie sicher, dass die verschiedenen Anpassungen in der URL berücksichtigt werden.

Beispielsweise werden Cookies nicht zwischengespeichert. Wenn Sie die Schriftgröße also in einem Cookie (oder einem ähnlichen Mechanismus) speichern, bleibt die Schriftgröße für die zwischengespeicherte Seite nicht erhalten. Daher gibt der Dispatcher Dokumente jeder Schriftgröße zufällig zurück.

Durch Einbeziehung der Schriftgröße in die URL als Selektor wird dieses Problem vermieden:

```xml
www.myCompany.com/news/main.large.html
```

>[!NOTE]
>
>Bei den meisten Layoutaspekten ist es auch möglich, Stylesheets, clientseitige Skripte oder beides zu verwenden. Diese Instrumente funktionieren gut mit Caching.
>
>Diese Strategie ist auch für Druckversionen nützlich, bei denen Sie eine URL wie die folgenden verwenden können:
>
>`www.myCompany.com/news/main.print.html`
>
>Mithilfe des Skript-Globbings der Vorlagendefinition können Sie ein separates Skript angeben, das die Druckseiten rendert.

#### Invalidierung von als Titel verwendeten Bilddateien  {#invalidating-image-files-used-as-titles}

Wenn Sie Seitentitel oder anderen Text als Bilder rendern, wird empfohlen, die Dateien so zu speichern, dass sie bei einer Inhaltsaktualisierung auf der Seite gelöscht werden:

1. Platzieren Sie die Bilddatei im selben Ordner wie die Seite.
1. Verwenden Sie das folgende Namensformat für die Bilddatei:

   `<page file name>.<image file name>`

Beispielsweise können Sie den Titel der Seite `myPage.html` in der Datei `file myPage.title.gif` speichern. Diese Datei wird automatisch gelöscht, wenn die Seite aktualisiert wird, sodass jede Änderung am Seitentitel automatisch im Cache angezeigt wird.

>[!NOTE]
>
>Die Bilddatei ist nicht unbedingt physisch auf der AEM-Instanz vorhanden. Sie können ein Skript verwenden, das die Bilddatei dynamisch erstellt. Der Dispatcher speichert die Datei dann auf dem Webserver.

#### Invalidierung von Bilddateien für die Navigation  {#invalidating-image-files-used-for-navigation}

Wenn Sie Bilder für die Navigationseinträge verwenden, ist die Methode im Wesentlichen die gleiche wie bei Titeln, aber etwas komplexer. Speichern Sie alle Navigationsbilder mit den Zielseiten. Wenn Sie zwei Bilder für normal und aktiv verwenden, können Sie die folgenden Skripte verwenden:

* Ein Skript, das die Seite wie gewohnt anzeigt.
* Ein Skript, das &quot;.normal&quot;-Anforderungen verarbeitet und das normale Bild zurückgibt.
* Ein Skript, das &quot;.active&quot;-Anfragen verarbeitet und das aktivierte Bild zurückgibt.

Es ist wichtig, dass Sie diese Bilder mit demselben Namensschild wie die Seite erstellen, um sicherzustellen, dass durch eine Inhaltsaktualisierung diese Bilder und die Seite gelöscht werden.

Bei Seiten, die nicht geändert werden, bleiben die Bilder im Cache, obwohl die Seiten selbst automatisch ungültig gemacht werden.

#### Personalisierung {#personalization}

Es wird empfohlen, die Personalisierung auf den erforderlichen Bereich zu beschränken. Um zu veranschaulichen, warum:

* Wenn Sie eine frei anpassbare Startseite verwenden, muss diese Seite jedes Mal erstellt werden, wenn ein Benutzer sie anfordert.
* Wenn Sie dagegen zehn verschiedene Startseiten auswählen, können Sie jede dieser Startseiten zwischenspeichern und so die Leistung verbessern.

>[!TIP]
>Weitere Informationen zum Konfigurieren des Dispatcher-Caches finden Sie im [Tutorial zum AEM Dispatcher Cache](https://experienceleague.adobe.com/docs/experience-manager-learn/dispatcher-tutorial/overview.html?lang=de) und dort im Abschnitt [Caching geschützter Inhalte](https://experienceleague.adobe.com/docs/experience-manager-learn/dispatcher-tutorial/chapter-1.html?lang=de#dispatcher-tips-and-tricks).

Wenn Sie die einzelnen Seiten personalisieren, indem Sie den Namen des Benutzers in die Titelleiste (z. B.) einfügen, wirkt sich dies auf die Leistung aus.

>[!TIP]
>Informationen zum Zwischenspeichern geschützter Inhalte finden Sie unter [Zwischenspeichern von geschützten Inhalten](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=de) im Dispatcher-Handbuch.

Bezüglich der Mischung von beschränktem und öffentlichem Inhalt auf einer Seite sollten Sie eine Strategie erwägen, bei der serverseitige Includes im Dispatcher verwendet werden, oder clientseitige Includes über Ajax im Browser.

>[!TIP]
>
>Informationen zum Umgang mit gemischten öffentlichen und eingeschränkten Inhalten finden Sie unter [Einrichten von Sling Dynamic Include](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-sling-dynamic-include.html?lang=de).

#### Sticky-Verbindungen  {#sticky-connections}

[Sticky-Verbindungen](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=en#the-benefits-of-load-balancing) stellen sicher, dass die Dokumente für einen Benutzer alle auf demselben Server erstellt werden. Wenn ein Benutzer diesen Ordner verlässt und später zu ihm zurückkehrt, bleibt die Verbindung erhalten. Um alle Dokumente zu speichern, die Sticky-Verbindungen für die Website erfordern, definieren Sie einen Ordner. Versuchen Sie, keine anderen Dokumente darin zu haben. Dieses Szenario wirkt sich auf den Lastenausgleich aus, wenn Sie personalisierte Seiten und Sitzungsdaten verwenden.

#### MIME-Typen {#mime-types}

Es gibt zwei Möglichkeiten, wie ein Browser den Dateityp bestimmen kann:

1. Durch seine Erweiterung (z. B. `.html`, `.gif`und `.jpg`).
1. Nach dem MIME-Typ, den der Server mit der Datei sendet.

Für die meisten Dateien wird der MIME-Typ durch die Dateierweiterung angegeben Das heißt,

1. Durch seine Erweiterung (z. B. `.html`, `.gif`und `.jpg`).
1. Nach dem MIME-Typ, den der Server mit der Datei sendet.

Wenn der Dateiname keine Erweiterung aufweist, wird er als Nur-Text angezeigt.

Mit der Dispatcher-Version 4.1.11 können Sie Antwortheader zwischenspeichern. Wenn Sie keine Antwortheader auf dem Dispatcher zwischenspeichern, ist der MIME-Typ Teil des HTTP-Headers. Wenn Ihre AEM-Anwendung Dateien zurückgibt, deren Dateiendung nicht erkannt wird, sondern bei denen der MIME-Typ verwendet wird, werden diese Dateien möglicherweise nicht korrekt angezeigt.

Um sicherzustellen, dass Dateien ordnungsgemäß zwischengespeichert werden, befolgen Sie die folgenden Richtlinien:

* Stellen Sie sicher, dass Dateien immer die richtige Erweiterung aufweisen.
* Verwenden Sie möglichst keine allgemeinen Dateibereitstellungsskripts mit URLs wie `download.jsp?file=2214`. Um URLs zu verwenden, die die Dateispezifikation enthalten, schreiben Sie das Skript neu. Im vorherigen Beispiel lautet diese Neufassung `download.2214.pdf`.

## Leistung bei der Sicherung {#backup-performance}

In diesem Abschnitt werden mehrere Benchmarks vorgestellt, mit denen die Leistung von AEM-Sicherungen und die Auswirkungen der Sicherungsaktivität auf die Anwendungsleistung bewertet wird. AEM Backups stellen während der Ausführung eine erhebliche Belastung des Systems dar, und Adobe misst diese Auswirkung sowie die Auswirkungen der Backup-Verzögerungseinstellungen, die versuchen, diese Auswirkungen zu modulieren. Ziel ist es, einige Referenzdaten über die erwartete Leistung von Backups in realistischen Konfigurationen und Mengen von Produktionsdaten bereitzustellen und Anleitungen zur Schätzung der Sicherungszeiten für geplante Systeme bereitzustellen.

### Referenzumgebung {#reference-environment}

#### Physikalisches System {#physical-system}

Die in diesem Dokument berichteten Ergebnisse stammen aus Benchmarks, die in einer Referenzumgebung mit der folgenden Konfiguration ausgeführt wurden. Diese Konfiguration ähnelt einer typischen Produktionsumgebung in einem Rechenzentrum:

* HP ProLiant DL380 G6, 8 CPUs x 2,533 GHz
* Serial angeschlossene SCSI-Laufwerke mit 300 GB, 10.000 RPM
* Hardware-RAID-Controller; acht Laufwerke in einem RAID0+5-Array
* VMware Image CPU x 2 Intel Xeon® E5540 @ 2,53 GHz
* Red Hat® Linux® 2.6.18-194.el5; Java™ 1.6.0_29
* Einzelne Autoreninstanz

Das Festplatten-Subsystem auf diesem Server ist schnell, repräsentativ für eine Hochleistungs-RAID-Konfiguration, die möglicherweise auf einem Produktionsserver verwendet wird. Die Backup-Leistung kann abhängig von der Festplattenleistung sein, und die Ergebnisse in dieser Umgebung spiegeln die Leistung bei einer schnellen RAID-Konfiguration wider. Das VMWare-Bild ist so konfiguriert, dass es über ein einzelnes großes Festplattenvolumen verfügt, das sich physisch im lokalen Festplattenspeicher auf dem RAID-Array befindet.

Die AEM-Konfiguration platziert das Repository und den Datenspeicher auf demselben logischen Volume neben dem Betriebssystem und der AEM. Das Zielverzeichnis für Backups befindet sich ebenfalls in diesem logischen Dateisystem.

#### Datenvolumen {#data-volumes}

Die folgende Tabelle zeigt die Größe der Datenvolumen, die in den Backup-Benchmarks verwendet werden. Zunächst wird der anfängliche Grundlinieninhalt installiert, dann werden zusätzliche bekannte Datenmengen hinzugefügt, um die Größe des gesicherten Inhalts zu erhöhen. Sicherungen werden in bestimmten Schritten erstellt, um einen starken Inhaltszuwachs und eine tägliche Erstellung zu gewährleisten. Die Verteilung von Inhalten (Seiten, Bilder, Tags) basiert in etwa auf einer realistischen Produktions-Asset-Komposition. Seiten, Bilder und Tags sind auf maximal 800 untergeordnete Seiten beschränkt. Jede Seite enthält Titel-, Flash-, Text-/Bild-, Video-, Diashow-, Formular-, Tabellen-, Cloud- und Karussellkomponenten. Bilder werden aus einem Pool von 400 Dateien mit einer Größe von 37 KB in 594 KB hochgeladen.

| Inhalt | Knoten | Seiten | Bilder | Tags |
|---|---|---|---|---|
| Basisinstallation | 69 610 | 562 | 256 | 237 |
| Kleiner Inhalt für inkrementelle Sicherung |  | +100 | +2 | +2 |
| Großer Inhalt für vollständige Sicherung |  | +10 000 | +100 | +100 |

Das Sicherungs-Benchmark wird mit den zusätzlichen Inhalten, die bei jeder Iteration hinzugefügt werden, wiederholt.

#### Benchmarkszenarios {#benchmark-scenarios}

Die Sicherungs-Benchmarks decken zwei Hauptszenarien ab: Sicherungen, wenn das System stark ausgelastet ist, und Sicherungen, wenn das System inaktiv ist. Obwohl allgemein empfohlen wird, Sicherungen möglichst bei inaktivem AEM-System durchzuführen, gibt es Situationen, in denen die Sicherung bei laufendem Betrieb durchgeführt werden muss.

* **Leerlaufzustand**: Sicherungen werden ohne andere Aktivität auf AEM durchgeführt.
* **Laufender Betrieb**: Sicherungen werden durchgeführt, während das System zu 80 % mit Online-Prozessen ausgelastet ist. Die Sicherungsverzögerung variiert, um die Auswirkung auf die Last zu ermitteln.

Die Sicherungszeiten und die Größe der resultierenden Sicherung können den AEM-Serverprotokollen entnommen werden. Es wird empfohlen, Sicherungen zu Zeiten zu planen, wenn AEM inaktiv ist, z. B. in der Nacht. Dieses Szenario ist für den empfohlenen Ansatz repräsentativ.

Die Last besteht aus erstellten Seiten, gelöschten Seiten, Durchläufen und Abfragen mit der größten Last, die durch Seitendurchläufe und Abfragen verursacht werden. Durch das Hinzufügen und Entfernen zu vieler Seiten wird die Arbeitsbereichsgröße kontinuierlich erhöht und das Abschließen von Sicherungen verhindert. Die Verteilung des Ladevorgangs, den das Skript verwendet, beträgt 75 % Seitendurchläufe, 24 % Abfragen und 1 % Seitenerstellungen (einzelne Ebene ohne verschachtelte Unterseiten). Die durchschnittlichen Spitzentransaktionen pro Sekunde in einem inaktiven System werden mit vier gleichzeitigen Threads erreicht, die beim Testen von Backups unter Last verwendet werden.

Die Auswirkung von Last auf die Sicherungsleistung kann geschätzt werden, indem die Differenz zwischen der Leistung mit Anwendungslast und der Leistung ohne Anwendungslast errechnet wird. Die Auswirkungen der Sicherung auf den Anwendungsdurchsatz werden ermittelt, indem der Szenario-Durchsatz in Transaktionen pro Stunde mit und ohne gleichzeitige Sicherung verglichen wird und Backups mit unterschiedlichen Einstellungen für &quot;Backup Delay&quot; ausgeführt werden.

* **Verzögerungseinstellung** - In verschiedenen Szenarien wurde die Einstellung für die Sicherungsverzögerung ebenfalls geändert, indem Werte von 10 ms (Standard), 1 ms und 0 ms verwendet wurden, um zu untersuchen, wie diese Einstellung die Leistung von Backups beeinflusst hat.
* **Sicherungstyp** - Alle Sicherungen waren externe Sicherungen des Repositorys, die in einem Backup-Verzeichnis durchgeführt wurden, ohne eine ZIP-Datei zu erstellen, außer in einem Fall zum Vergleich, in dem der tar-Befehl direkt verwendet wurde. Da inkrementelle Sicherungen nicht in eine ZIP-Datei geschrieben werden können oder wenn die vorherige vollständige Sicherung eine ZIP-Datei ist, wird in Produktionssituationen meist die Sicherungsverzeichnismethode verwendet.

### Zusammenfassung der Ergebnisse {#summary-of-results}

#### Sicherungsdauer und Durchsatz {#backup-time-and-throughput}

Als Hauptergebnis dieser Benchmarks kann gezeigt werden, wie die Sicherungsdauer je nach Sicherungstyp und Datenmenge variiert. Die folgende Grafik zeigt die unter Verwendung der standardmäßigen Backup-Konfiguration erhaltene Sicherungsdauer in Abhängigkeit von der Gesamtzahl der Seiten.

![chlimage_1-81](assets/chlimage_1-81.png)

Die Sicherungszeiten in einer inaktiven Instanz sind relativ konsistent und liegen im Durchschnitt bei 0,608 MB pro Sekunde, unabhängig von vollständigen oder inkrementellen Backups (siehe Diagramm unten). Die Sicherungsdauer ist lediglich eine Funktion der Datenmenge, die gesichert wird. Die Zeit für den Abschluss einer vollständigen Sicherung steigt deutlich mit der Gesamtzahl der Seiten. Die Zeit, um eine inkrementelle Sicherung durchzuführen, steigt ebenfalls mit der Gesamtanzahl der Seiten, jedoch mit einer wesentlich geringeren Geschwindigkeit. Die Dauer der inkrementellen Sicherung ist aufgrund der relativ geringen Menge an zu sichernden Daten viel kürzer.

Die Größe der erzeugten Sicherung ist entscheidend für die Sicherungsdauer. Die folgende Grafik zeigt die benötigte Zeit in Abhängigkeit von der endgültigen Backup-Größe.

![chlimage_1-82](assets/chlimage_1-82.png)

Dieses Diagramm zeigt, dass sowohl inkrementelle als auch vollständige Sicherungen einem einfachen Größen- als auch einem Zeitmuster entsprechen, das von Adobe als Durchsatz gemessen werden kann. Die Sicherungszeiten in einer inaktiven Instanz sind relativ konsistent und erreichen im Durchschnitt 0,61 MB pro Sekunde, unabhängig von vollständigen oder inkrementellen Backups in der Benchmark-Umgebung.

#### Sicherungsverzögerung {#backup-delay}

Der Parameter für die Sicherungsverzögerung wird bereitgestellt, um zu begrenzen, in welchem Umfang Backups zu Problemen bei Produktions-Workloads führen können. Der Parameter gibt eine Wartezeit in Millisekunden an, die in den Sicherungsvorgang Datei für Datei integriert wird. Der Gesamteffekt hängt zum Teil von der Größe der betroffenen Dateien ab. Die Messung der Backup-Leistung in MB/s bietet eine vernünftige Möglichkeit, die Auswirkungen einer Verzögerung auf das Backup zu vergleichen.

* Das gleichzeitige Ausführen einer Sicherung mit regulärer Anwendungslast hat negative Auswirkungen auf den Durchsatz der normalen Auslastung.
* Die Auswirkungen können leicht (bis zu 5 %) oder signifikant sein und bis zu 75 % zu einem Rückgang des Durchsatzes führen. Dies hängt wahrscheinlich am meisten von der Anwendung ab.
* Die Sicherung stellt keine große Last für die CPU dar. Prozessorintensive Produktionsaufgaben werden deshalb durch die Sicherung weniger stark beeinträchtigt als I/O-intensive Aufgaben.

![chlimage_1-83](assets/chlimage_1-83.png)

Zum Vergleich: der Durchsatz, der mithilfe einer Dateisystemsicherung (&#39;tar&#39;) ermittelt wurde, um dieselben Repository-Dateien zu sichern. Die Leistung des Tars ist vergleichbar, aber etwas höher als die Sicherung mit einer Verzögerung von null. Durch die Festlegung einer geringen Verzögerung wird der Backup-Durchsatz erheblich reduziert, und die Standardverzögerung von 10 ms führt zu einem deutlich geringeren Durchsatz. In Situationen, in denen Sicherungen geplant werden können, wenn die allgemeine Anwendungsnutzung gering ist oder die Anwendung inaktiv sein kann, reduzieren Sie die Verzögerung unter den Standardwert, damit die Sicherung schneller fortgesetzt werden kann.

Die tatsächlichen Auswirkungen des Durchsatzes einer laufenden Sicherung hängen von der Anwendungs- und Infrastrukturdetails ab. Die Auswahl des Verzögerungswerts sollte durch empirische Analyse der Anwendung erfolgen, sollte jedoch so klein wie möglich sein, damit Backups so schnell wie möglich abgeschlossen werden können. Da es nur eine schwache Korrelation zwischen der Auswahl des Verzögerungswerts und den Auswirkungen auf den Anwendungsdurchsatz gibt, sollte die Wahl der Verzögerung kürzere Backup-Zeiten bevorzugen, um die Gesamtauswirkungen von Backups zu minimieren. Ein Backup, das acht Stunden dauert, aber den Durchsatz um -20 % beeinflusst, hat wahrscheinlich eine größere Gesamtwirkung als ein Backup, das zwei Stunden dauert, aber den Durchsatz um -30 % beeinflusst.

### Verweise {#references}

* [Administration - Sichern und Wiederherstellen](/help/sites-administering/backup-and-restore.md)
* [Verwaltung – Kapazität und Volumen ](/help/managing/best-practices-further-reference.md#capacity-and-volume)
