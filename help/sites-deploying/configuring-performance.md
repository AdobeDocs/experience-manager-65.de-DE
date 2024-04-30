---
title: Leistungsoptimierung
description: Erfahren Sie, wie Sie bestimmte Aspekte von AEM konfigurieren, um die Leistung zu optimieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
feature: Configuring
exl-id: 5b0c9a8c-0f5f-46ee-a455-adb9b9d27270
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '6470'
ht-degree: 100%

---

# Leistungsoptimierung {#performance-optimization}

>[!NOTE]
>
>Allgemeine Richtlinien zur Leistung finden Sie auf der Seite [Leistungsrichtlinien](/help/sites-deploying/performance-guidelines.md).
>
>Weitere Informationen zur Fehlerbehebung und zur Behebung von Leistungsproblemen finden Sie unter [Leistungsstruktur](/help/sites-deploying/performance-tree.md).
>
>Sie können in der Wissensdatenbank auch einen Artikel über [Tipps zur Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=de) lesen.

Ein wichtiger Faktor ist die Zeit, die Ihre Website benötigt, um auf Anfragen durch Besucherinnen und Besucher zu reagieren. Auch wenn dieser Wert für jede Anfrage unterschiedlich ist, kann ein durchschnittlicher Zielwert definiert werden. Sobald sich gezeigt hat, dass dieser Wert sowohl erreichbar als auch verwaltbar ist, kann er verwendet werden, um die Leistung der Website zu überwachen und die Entwicklung potenzieller Probleme anzuzeigen.

Die Antwortzeiten, die Sie anstreben, unterscheiden sich zwischen Authoring- und Publishing-Umgebung und spiegeln die verschiedenen Merkmale der Zielgruppe wider:

## Authoring-Umgebung {#author-environment}

Diese Umgebung wird von Autorinnen und Autoren verwendet, die Inhalte eingeben und aktualisieren. Sie muss einigen Benutzerinnen und Benutzern gerecht werden, die jeweils eine hohe Anzahl leistungsintensiver Anfragen generieren, wenn sie Inhaltsseiten und die einzelnen Elemente auf diesen Seiten aktualisieren.

## Veröffentlichungsumgebung {#publish-environment}

Diese Umgebung enthält Inhalte, die Sie Ihren Benutzerinnen und Benutzern zur Verfügung stellen. Hier ist die Anzahl der Anfragen noch größer und die Geschwindigkeit ist ebenso wichtig. Da die Anfragen jedoch weniger dynamisch sind, können zusätzliche leistungssteigernde Mechanismen angewendet werden, wie das Zwischenspeichern des Inhalts oder der Lastenausgleich.

>[!NOTE]
>
>* Folgen Sie nach der Konfiguration zur Leistungsoptimierung der Anleitung in [Tough Day](/help/sites-developing/tough-day.md), um die Umgebung unter starker Belastung zu testen.
>* Siehe auch [Tipps zur Leistungsoptimierung.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=de)

## Methode zur Leistungsoptimierung {#performance-optimization-methodology}

Eine Methodik zur Leistungsoptimierung für AEM-Projekte lässt sich in fünf einfachen Regeln zusammenfassen, die befolgt werden können, um Leistungsprobleme von Anfang an zu vermeiden:

1. [Zeit für die Optimierung einplanen](#planning-for-optimization)
1. [Reale Situationen simulieren](#simulate-reality)
1. [Konkrete Ziele festlegen](#establish-solid-goals)
1. [Relevante Maßnahmen treffen](#stay-relevant)
1. [Agile Iterationszyklen](#agile-iteration-cycles)

Diese Regeln gelten für Web-Projekte im Allgemeinen und sind für Projektleiterinnen bzw. -leiter und Systemadmins von Bedeutung, um sicherzustellen, dass ihre Projekte nicht vor Leistungsproblemen stehen, wenn der Startzeitpunkt kommt.

### Zeit für die Optimierung einplanen {#planning-for-optimization}

![chlimage_1-3](assets/chlimage_1-3.jpeg)

Planen Sie etwa 10 % der Projektarbeit für die Leistungsoptimierungsphase. Die tatsächlichen Anforderungen an die Leistungsoptimierung hängen von der Komplexität eines Projekts und der Erfahrung des Entwicklungsteams ab. Obwohl Ihr Projekt (letztendlich) wahrscheinlich nicht die zugewiesene Zeit benötigt, empfiehlt es sich, immer die Leistungsoptimierung in der vorgeschlagenen Region zu planen.

Wenn möglich, sollte ein Projekt zunächst probeweise für eine begrenzte Zielgruppe gestartet werden, um Erfahrungen zu sammeln und weitere Optimierungen vorzunehmen. Dadurch wird zusätzlicher Druck vermieden, der mit einer Ankündigung des vollständigen Launches einhergeht.

Nach der Live-Schaltung ist die Leistungsoptimierung noch nicht abgeschlossen. Erst jetzt erfahren Sie die „echte“ Belastung Ihres Systems. Es ist wichtig, zusätzliche Anpassungen nach dem Launch einzuplanen.

Da sich die Systemlast ändert und sich die Leistungsprofile Ihres Systems im Laufe der Zeit verändern, sollte in Intervallen von 6 bis 12 Monaten eine Leistungsoptimierung oder Konsistenzprüfung geplant werden.

### Reale Situationen simulieren {#simulate-reality}

![chlimage_1-4](assets/chlimage_1-4.jpeg)

Wenn Sie eine Website in Betrieb nehmen und nach dem Launch feststellen, dass sie Leistungsprobleme hat, liegt das wahrscheinlich daran, dass Ihre Belastungs- und Leistungstests die Realität nicht genau genug simuliert haben.

Die „Realität“ nachzubilden ist schwierig und wie viel Aufwand Sie dafür betreiben möchten, hängt von der Art Ihres Projekts ab. „Real“ bedeutet nicht nur „echter Code“ und „echter Traffic“, sondern auch „echter Inhalt“, insbesondere in Bezug auf Umfang und Struktur des Inhalts. Ihre Vorlagen verhalten sich je nach Größe und Struktur des Repositorys möglicherweise unterschiedlich.

### Konkrete Ziele festlegen {#establish-solid-goals}

![chlimage_1-5](assets/chlimage_1-5.jpeg)

Die Bedeutung konkreter Leistungsziele sollte nicht unterschätzt werden. Wenn Personen erst einmal bestimmte Leistungsziele festgelegt haben, ist es oft sehr schwer, diese zu ändern, auch wenn sie nur auf vagen Annahmen beruhen.

Die Festlegung guter, solider Leistungsziele ist wirklich einer der schwierigsten Bereiche. Oft ist es am besten, von einer vergleichbaren Website (z. B. dem Vorgänger der neuen Website) reale Protokolle und Benchmarks zu sammeln.

### Relevante Maßnahmen treffen {#stay-relevant}

![chlimage_1-6](assets/chlimage_1-6.jpeg)

Es ist wichtig, jeweils nur einen Engpass gleichzeitig zu optimieren. Wenn Sie versuchen, Dinge parallel zu erledigen, ohne die Auswirkungen der einen Optimierung zu überprüfen, können Sie den Überblick darüber verlieren, welche Optimierungsmaßnahme wirklich geholfen hat.

### Agile Iterationszyklen {#agile-iteration-cycles}

![chlimage_1-7](assets/chlimage_1-7.jpeg)

Im Zuge der Leistungsoptimierung werden Werte immer wieder gemessen, analysiert, optimiert und validiert, bis das Ziel erreicht ist. Deshalb ist es besser, in der Optimierungsphase einen agilen Validierungsprozess einzuführen, anstatt nach jeder Iteration einen schwerfälligeren Testprozess durchzuführen.

Dieser Fokus bedeutet, dass Entwicklerinnen und Entwickler, die die Optimierung implementieren, schnell feststellen können, ob die Optimierung bereits das Ziel erreicht hat. Diese Informationen sind wertvoll, denn wenn das Ziel erreicht ist, ist die Optimierung vorbei.

## Allgemeine Leistungsrichtlinien {#basic-performance-guidelines}

Im Allgemeinen sollten Sie Ihre nicht zwischengespeicherten HTML-Anfragen auf weniger als 100 Millisekunden beschränken. Konkret wird Folgendes empfohlen:

* 70 % der Seitenanfragen sollten in weniger als 100 Millisekunden beantwortet werden.
* 25 % der Seitenanfragen sollten innerhalb von 100 Millisekunden bis 300 Millisekunden beantwortet werden.
* 4 % der Seitenanfragen sollten innerhalb von 300 Millisekunden bis 500 Millisekunden beantwortet werden.
* 1 % der Seitenanfragen sollten innerhalb von 500 Millisekunden bis 1000 Millisekunden beantwortet werden.
* Keine Seite sollte langsamer als 1 Sekunde reagieren.

Die obigen Zahlen gehen von folgenden Bedingungen aus:

* Gemessen in der Veröffentlichungsumgebung (kein zusätzlicher Aufwand wie bei einer Autorenumgebung)
* Gemessen auf dem Server (kein zusätzlicher Netzwerkaufwand)
* Nicht zwischengespeichert (kein AEM-Ausgabe-Cache, kein Dispatcher-Cache)
* Nur für komplexe Objekte mit vielen Abhängigkeiten (HTML, JS, PDF usw.)
* Keine andere Last auf dem System

Es gibt einige Gründe, die häufig zu Leistungsproblemen beitragen, darunter die folgenden:

* Ineffiziente Speicherung im Dispatcher-Cache
* Verwendung von Abfragen in normalen Anzeigevorlagen

Optimierungen auf JVM- und Betriebssystemebene führen in der Regel nicht zu signifikanten Leistungssteigerungen und sollten daher erst ganz am Ende des Optimierungszyklus durchgeführt werden.

Die Art und Weise, wie ein Content-Repository strukturiert ist, kann sich auch auf die Leistung auswirken. Um eine optimale Leistung zu erzielen, sollte die Anzahl der untergeordneten Knoten, die mit einzelnen Knoten in einem Content-Repository verbunden sind, als Faustregel 1.000 nicht überschreiten.

Ihre besten Freunde während einer üblichen Leistungsoptimierungsübung sind:

* Die `request.log`
* Komponentenbasiertes Timing
* Ein Java™-Profiler.

### Leistung beim Laden und Bearbeiten digitaler Assets {#performance-when-loading-and-editing-digital-assets}

Aufgrund der großen Datenmenge, die beim Laden und Bearbeiten digitaler Assets anfällt, kann die Leistung ein Thema werden.

Zwei Dinge wirken sich auf die Leistung aus:

* CPU: mehrere Kerne ermöglichen eine flüssigere Codeumsetzung
* Festplatte: parallele RAID-Festplatten erreichen das gleiche

Beachten Sie Folgendes, um die Leistung zu verbessern:

* Wie viele Assets werden pro Tag hochgeladen? Eine gute Schätzung erhalten Sie mit folgender Formel: 

![chlimage_1-77](assets/chlimage_1-77.png)

* Der Zeitrahmen, in dem Bearbeitungen durchgeführt werden (normalerweise während der Bürozeiten, länger bei internationaler Zusammenarbeit).
* Die durchschnittliche Größe der hochgeladenen Bilder (und die Größe der pro Bild generierten Darstellungen) in Megabyte.
* Bestimmen Sie die durchschnittliche Datenrate: 

![chlimage_1-78](assets/chlimage_1-78.png)

* 80 % aller Bearbeitungen erfolgen in 20 % der Zeit. In Spitzenzeiten beträgt die Datenrate also viermal so viel wie im Durchschnitt. Eine solche Leistung ist Ihr Ziel.

## Performance-Überwachung {#performance-monitoring}

Die Leistung (oder das Fehlen der Leistung) ist eines der ersten Dinge, die Ihre Benutzerinnen und Benutzer bemerken. Wie bei jeder Anwendung mit einer Benutzeroberfläche ist die Leistung von entscheidender Bedeutung. Um die Leistung Ihrer AEM-Installation zu optimieren, müssen Sie verschiedene Attribute der Instanz und ihr Verhalten überwachen.

Weitere Informationen zur Leistungsüberwachung finden Sie unter [Überwachen der Leistung](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance).

Die Probleme, die zu Leistungseinbußen führen, sind oft schwer aufzuspüren, lassen sich oft nur schwer nachvollziehen, selbst wenn ihre Auswirkungen leicht erkennbar sind.

Ein grundlegender Ausgangspunkt ist eine gute Kenntnis Ihres Systems, wenn es normal arbeitet. Wenn Sie nicht wissen, wie Ihre Umgebung bei ordnungsgemäßer Ausführung „aussieht“ und „sich verhält“, ist es schwierig, das Problem zu finden, wenn sich die Leistung verschlechtert. Verbringen Sie Zeit mit der Untersuchung Ihres Systems, wenn es reibungslos läuft, und stellen Sie sicher, dass die Erfassung von Leistungsinformationen eine fortlaufende Aufgabe ist. Dies bietet Ihnen eine Vergleichsgrundlage für den Fall, dass die Leistung beeinträchtigt ist.

Das folgende Diagramm veranschaulicht den möglichen Pfad von AEM-Inhalten, und damit die Anzahl der unterschiedlichen Elemente, die die Leistung beeinflussen können.

![chlimage_1-79](assets/chlimage_1-79.png)

Leistung wird auch durch das Verhältnis zwischen Volumen und Kapazität bestimmt:

* **Volumen**: Die Menge an Ausgabedaten, die vom System verarbeitet und bereitgestellt wird.
* **Kapazität**: Die Fähigkeit des Systems, das Volumen zu liefern

Die Leistung kann an unterschiedlichen Stellen der Web-Kette veranschaulicht werden.

![chlimage_1-80](assets/chlimage_1-80.png)

Es gibt verschiedene Funktionsbereiche, die häufig für eine Leistungsbeeinträchtigung verantwortlich sind:

* Caching
* Anwendungs-Code (Ihr Projekt)
* Suchfunktion

### Grundregeln für die Leistung {#basic-rules-regarding-performance}

Bei der Leistungsoptimierung sollten bestimmte Regeln beachtet werden:

* Leistungsoptimierung *muss* Teil jedes Projekts sein.
* Optimieren Sie nicht frühzeitig im Entwicklungszyklus.
* Die Leistung ist nur so gut wie das schwächste Glied.
* Denken Sie immer an Kapazität im Vergleich zum Volumen.
* Optimieren Sie wichtige Dinge zuerst.
* Optimieren Sie nie ohne *realistische* Ziele.

>[!NOTE]
>
>Beachten Sie, dass der Mechanismus zur Leistungsmessung häufig genau das beeinflusst, was Sie messen möchten. Versuchen Sie, diese Diskrepanzen zu berücksichtigen und so viel ihrer Auswirkungen wie möglich zu beseitigen. Insbesondere sollten Browser-Plug-ins nach Möglichkeit deaktiviert werden.

## Konfiguration zur Leistungsoptimierung {#configuring-for-performance}

Bestimmte Aspekte von AEM (bzw. des zugrunde liegenden Repositorys) können so konfiguriert werden, dass die Leistung optimiert wird. Im Folgenden werden Möglichkeiten und Vorschläge beschrieben. Überprüfen Sie zuerst, ob und wie Sie die beschriebene Funktionalität verwenden können, bevor Sie Änderungen vornehmen.

>[!NOTE]
>
>Siehe [Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=de).

### Suchindizierung {#search-indexing}

Ab AEM 6.0 verwendet Adobe Experience Manager eine Oak-basierte Repository-Architektur.

Die aktualisierten Indizierungsinformationen finden Sie hier:

* [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md)
* [Abfragen und Indizierung](/help/sites-deploying/queries-and-indexing.md)

### Gleichzeitige Verarbeitung von Workflows {#concurrent-workflow-processing}

Um die Leistung zu verbessern, begrenzen Sie die Anzahl der gleichzeitig ausgeführten Workflow-Prozesse. Standardmäßig verarbeitet die Workflow-Engine so viele Workflows parallel, wie dem virtuellen Java™-Computer Prozessoren zur Verfügung stehen. Wenn Workflow-Schritte große Mengen von Verarbeitungsressourcen (RAM oder CPU) erfordern, kann es vorkommen, dass durch das gleichzeitige Ausführen mehrerer dieser Workflows die Serverressourcen stark beansprucht werden.

Wenn beispielsweise Bilder (oder DAM-Assets im Allgemeinen) hochgeladen werden, importieren Workflows die Bilder automatisch in DAM. Bilder haben häufig eine hohe Auflösung und können problemlos Hunderte von MB an Heap für die Verarbeitung verbrauchen. Die parallele Behandlung dieser Bilder stellt eine hohe Belastung für das Speicher-Subsystems und die Speicherbereinigung dar.

Die Workflow-Engine verwendet Apache Sling-Vorgangswarteschlangen für die Verarbeitung und Planung der Arbeitselemente. Die folgenden Auftragswarteschlangendienste wurden standardmäßig in der Apache Sling Job Queue Configuration Service Factory zur Verarbeitung von Workflow-Aufgaben erstellt:

* Granite Workflow-Warteschlange: Für die meisten Workflow-Schritte, wie diejenigen zur Verarbeitung von DAM-Assets, wird der Granite Workflow-Warteschlangendienst verwendet.
* Granite Workflow Auftragswarteschlange für externe Prozesse: Dieser Dienst wird für spezielle externe Workflow-Schritte verwendet, die typischerweise für die Kontaktaufnahme mit einem externen System und die Abfrage von Ergebnissen verwendet werden. Beispielsweise wird der Schritt „InDesign Medien-Extraktionsvorgang“ als externer Prozess implementiert. Die Workflow-Engine verwendet die externe Warteschlange zur Verarbeitung der Abfrage. (Siehe [com.day.cq.workflow.exec.WorkflowExternalProcess](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/workflow/exec/WorkflowExternalProcess.html).)

Konfigurieren Sie diese Dienste, um die maximale Anzahl der parallel ausgeführten Workflow-Prozesse zu beschränken.

>[!NOTE]
>
>Hinweis: Die Konfiguration dieser Auftragswarteschlangen hat Auswirkungen auf alle Workflows, es sei denn, Sie haben eine Auftragswarteschlange für ein bestimmtes Workflow-Modell erstellt (siehe [Konfigurieren einer Warteschlange für ein bestimmtes Workflow-Modell](/help/sites-deploying/configuring-performance.md#configure-the-queue-for-a-specific-workflow) weiter unten).

#### Konfiguration im Repository {#configuration-in-the-repo}

Wenn Sie die Dienste [mithilfe eines sling:OsgiConfig-Knotens](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository) konfigurieren, müssen Sie die PID der vorhandenen Dienste suchen, zum Beispiel: org.apache.sling.event.jobs.QueueConfiguration.370aad73-d01b-4a0b-abe4-20198d85f705. Sie können die PID mithilfe der Web-Konsole ermitteln.

Konfigurieren Sie die Eigenschaft mit dem Namen `queue.maxparallel`.

#### Konfiguration in der Web-Konsole  {#configuration-in-the-web-console}

Um diese Dienste mithilfe [der Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) zu konfigurieren, suchen Sie die vorhandenen Konfigurationselemente unter der Apache Sling Job Queue Configuration Service Factory.

Konfigurieren Sie die Eigenschaft mit dem Namen „Maximum Parallel Jobs“.

### Konfigurieren der Warteschlange für einen spezifischen Workflow {#configure-the-queue-for-a-specific-workflow}

Erstellen Sie eine Vorgangswarteschlange für ein bestimmtes Workflow-Modell, damit Sie die Vorgangsverarbeitung für dieses Workflow-Modell konfigurieren können. Auf diese Weise beeinflussen Ihre Konfigurationen die Verarbeitung für einen bestimmten Workflow, während die Konfiguration der standardmäßigen Granite-Workflow-Warteschlange die Verarbeitung anderer Workflows steuert.

Wenn Workflow-Modelle ausgeführt werden, erstellen sie Sling-Vorgänge für ein bestimmtes Thema. Standardmäßig entspricht das Thema den Themen, die für die allgemeine Granite-Workflow-Warteschlange oder die Granite-Workflow-Warteschlange für externe Prozessvorgänge konfiguriert sind:

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

1. Erstellen Sie für jedes Thema eine Auftragswarteschlange. Um eine Vorgangswarteschlange zu erstellen, erstellen Sie eine Werkskonfiguration für den Factory-Dienst Apache Sling Job Queue.

   Die Werkskonfigurationen sind ähnlich der Granite Workflow-Warteschlange, die in [Gleichzeitige Workflow-Verarbeitung](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing) beschrieben wird, mit der Ausnahme, dass die Themen-Eigenschaft mit dem Thema Ihrer Workflow-Aufträge übereinstimmt.

### AEM DAM Asset-Synchronisierungsdienst {#cq-dam-asset-synchronization-service}

Der `AssetSynchronizationService` dient zur Synchronisation von Assets von gemounteten Repositorys (z. B. LiveLink, Documentum®). Standardmäßig wird hierbei alle 300 Sekunden (5 Minuten) eine Prüfung durchgeführt. Wenn Sie keine gemounteten Repositorys verwenden, können Sie diesen Dienst deaktivieren.

Der Dienst wird deaktiviert, indem man [den OSGi-Dienst](/help/sites-deploying/configuring-osgi.md) **CQ DAM Asset Synchronization Service** so konfiguriert, sodass der **Synchronisationszeitraum** (`scheduler.period`) ein Jahr oder mehr beträgt (definiert in Sekunden).

### Mehrere DAM-Instanzen {#multiple-dam-instances}

Das Bereitstellen mehrerer DAM-Instanzen kann in folgenden Fällen die Leistung steigern: 

* Aufgrund regelmäßiger Uploads zahlreicher Assets in die Authoring-Umgebung entsteht eine hohe Last. In dieser Situation kann eine separate DAM-Instanz speziell für die Inhaltsverarbeitung reserviert werden.
* Sie verfügen über mehrere Teams an weltweiten Standorten (z. B. USA, Europa, Asien).

Zusätzliche Erwägungen sind:

* Trennung von unfertiger Arbeit in der Autorenumgebung von abgeschlossener Arbeit in der Veröffentlichungsumgebung
* Trennung von internen Benutzerinnen und Benutzern auf der Authoring-Seite und externen Personen, die die Publishing-Seite besuchen/benutzen (z. B. Agentinnen und Agenten, Pressemitglieder, Kundinnen und Kunden, Lernende usw.).

## Best Practices zur Qualitätssicherung {#best-practices-for-quality-assurance}

Die Leistung ist für Ihre Publishing-Umgebung von größter Bedeutung. Daher müssen Sie bei der Implementierung Ihres Projekts die Leistungstests für die Publishing-Umgebung sorgfältig planen und analysieren.

In diesem Abschnitt erhalten Sie einen Überblick über Probleme bei der Definition eines Testkonzepts speziell für Leistungstests in Ihrer *Veröffentlichungsumgebung*. Dies ist vor allem für QA-Beauftragte, Projektverantwortliche und Systemadmins von Interesse.

Im Folgenden wird die übliche Vorgehensweise bei der Durchführung von Leistungstests bei einer AEM-Anwendung in der *Veröffentlichungsumgebung* beschrieben. Dieser Leistungstest umfasst die folgenden fünf Phasen:

* [Überprüfung des Wissens](#verification-of-knowledge)
* [Definition des Umfangs ](#scope-definition)
* [Testmethoden](#test-methodologies)
* [Definition von Leistungszielen ](#defining-the-performance-goals)
* [Optimierung](#optimization)

Die Steuerung ist ein zusätzlicher, allumfassender Prozess – notwendig, aber nicht auf Tests beschränkt.

### Überprüfung des Wissens {#verification-of-knowledge}

Ein erster Schritt besteht darin, die grundlegenden Informationen zu dokumentieren, die Sie kennen müssen, bevor Sie mit dem Testen beginnen können:

* Die Architektur Ihrer Testumgebung
* Ein Plan der Anwendung mit einer genauen Angabe der internen Elemente, die getestet werden müssen (sowohl einzeln als auch in Kombination)

#### Testarchitektur {#test-architecture}

Dokumentieren Sie die Architektur der Testumgebung, die für Ihre Leistungstests verwendet wird.

Sie benötigen eine Darstellung Ihrer geplanten Publishing-Umgebung in der Produktion, zusammen mit dem Dispatcher und dem Load Balancer.

#### Anwendungsübersicht {#application-map}

Verschaffen Sie sich einen klaren Überblick, anhand dessen Sie eine Karte der gesamten Anwendung erstellen können (möglicherweise haben Sie diese Karte bereits aus Tests in der Authoring-Umgebung).

Eine Diagrammdarstellung der internen Elemente der Anwendung kann einen Überblick über die Testanforderungen geben. Mit Farbcodierung kann sie auch als Grundlage für das Reporting dienen.

### Definition des Umfangs {#scope-definition}

Eine Anwendung verfügt in der Regel über eine Reihe von Anwendungsfällen. Einige Anwendungsfälle sind wichtig, andere weniger.

Um den Umfang der Leistungstests auf die Veröffentlichung zu konzentrieren, empfiehlt Adobe, Folgendes zu definieren:

* Die wichtigsten Geschäftsanwendungsfälle
* Die wichtigsten technischen Anwendungsfälle

Die Anzahl der Anwendungsfälle ist Ihnen überlassen, sollte jedoch auf eine einfach zu handhabende Zahl beschränkt sein (z. B. zwischen 5 und 10).

Sobald die wichtigsten Anwendungsfälle ausgewählt sind, können für jeden Fall die wichtigsten Leistungsindikatoren (Key Performance Indicators, KPI) und die Tools, mit denen sie gemessen werden, definiert werden. Beispiele für häufig verwendete KPIs:

* End-to-End-Antwortzeit
* Servlet-Reaktionszeit
* Reaktionszeit für eine einzelne Komponente
* Reaktionszeit für die Dienste
* Anzahl der inaktiven Threads im Thread-Pool
* Anzahl freier Verbindungen
* Systemressourcen wie CPU- und E/A-Zugriff

### Testmethoden {#test-methodologies}

Dieses Konzept umfasst vier Szenarien, in denen die Leistungsziele definiert und getestet werden:

* Tests einzelner Komponenten
* Tests kombinierter Komponenten
* Szenario *Live-Schaltung*
* Fehlerszenarien

Basierend auf den folgenden Grundsätzen.

#### Belastungsgrenze der Komponente  {#component-breakpoints}

* Jede Komponente hat eine bestimmte Belastungsgrenze in Bezug auf die Leistung. Das heißt, eine Komponente kann bis zu einem bestimmten Punkt eine gute Leistung aufweisen, woraufhin die Leistung schnell abnimmt.
* Um einen vollständigen Überblick über die Anwendung zu erhalten, müssen Sie zunächst feststellen, wann bei Ihren Komponenten diese Belastungsgrenze erreicht ist.
* Um den Breakpoint zu finden, können Sie einen Lasttest durchführen, bei dem Sie über einen bestimmten Zeitraum die Anzahl der Benutzer bzw. Benutzerinnen erhöhen, um eine steigende Last zu erzeugen. Durch die Überwachung dieser Last und die Beobachtung der Reaktion der Komponenten wird ein spezifisches Leistungsverhalten festgestellt, wenn der Belastungspunkt der Komponente erreicht ist. Der Punkt kann anhand der Anzahl der gleichzeitigen Transaktionen pro Sekunde sowie der Anzahl der gleichzeitigen Benutzer bzw. Benutzerinnen qualifiziert werden (wenn die Komponente auf diese KPI reagiert).
* Diese Informationen können dann als Benchmark für Verbesserungen dienen, die Effizienz der verwendeten Maßnahmen angeben und bei der Definition von Testszenarien helfen.

#### Transaktionen  {#transactions}

* Der Begriff Transaktion wird verwendet, um die Anfrage einer vollständigen Web-Seite einschließlich der Seite selbst und aller nachfolgenden Aufrufe darzustellen. Das heißt die Seitenanfrage, alle AJAX Aufrufe, Bilder und andere Objekte **Drilldown für Anfragen**.
* Um jede Anfrage vollständig zu analysieren, können Sie jedes Element des Aufrufstapels darstellen und dann die durchschnittliche Verarbeitungszeit für jedes Element addieren.

### Leistungsziele definieren {#defining-the-performance-goals}

Nachdem der Umfang und die zugehörigen KPIs definiert wurden, werden die spezifischen Leistungsziele festgelegt. Dieser Prozess umfasst die Entwicklung von Testszenarien zusammen mit Zielwerten.

Testleistung unter Durchschnitts- und Spitzenbelastungsbedingungen. Darüber hinaus benötigen Sie Tests für das Szenario „Live schalten“, um sicherzustellen, dass Sie bei der erstmaligen Bereitstellung der Website für ein erhöhtes Interesse sorgen können.

Alle Erlebnisse oder Statistiken, die Sie möglicherweise auf einer vorhandenen Website gesammelt haben, können auch bei der Bestimmung künftiger Ziele hilfreich sein. Beispiel: Top-Traffic von Ihrer Live-Website.

#### Tests einzelner Komponenten {#single-component-tests}

Kritische Komponenten müssen getestet werden – sowohl unter Durchschnitts- als auch unter Spitzenbelastungsbedingungen.

In beiden Fällen können Sie die erwartete Anzahl von Transaktionen pro Sekunde definieren, wenn eine vordefinierte Anzahl von Benutzern das System verwendet.

| Komponente | Testtyp | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Einzelbenutzer auf der Startseite | Durchschnitt | 1 | 1 |  |  |
|   | Spitze | 1 | 3 |  |  |
| Startseite 100 Benutzer | Durchschnitt | 100 | 3 |  |  |
|   | Spitze | 100 | 3 |  |

#### Tests kombinierter Komponenten {#combined-component-tests}

Durch das Testen der Komponenten in Kombination wird das Anwendungsverhalten besser widergespiegelt. Auch hier müssen die Durchschnitts- und Spitzenbelastungsbedingungen getestet werden.

| Szenario | Komponente | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Durchschnitt gemischt | Homepage | 10 | 1 |  |  |
|   | Suchen | 10 | 1 |  |  |
|   | Nachrichten | 10 | 2 |  |  |
|   | Ereignisse | 10 | 1 |  |  |
|   | Aktivierungen | 10 | 3 |  | Simulation des Autorenverhaltens. |
| Spitzenwert gemischt | Homepage | 100 | 5 |  |  |
|   | Suchen | 50 | 5 |  |  |
|   | Nachrichten | 100 | 10 |  |  |
|   | Ereignisse | 100 | 10 |  |  |
|   | Aktivierungen | 20 | 20 |  | Simulation des Autorenverhaltens. |

#### Live-Schaltungs-Tests {#going-live-tests}

In den ersten Tagen nach der Bereitstellung Ihrer Website können Sie mit einem erhöhten Interesse rechnen. Dieses Szenario ist sogar noch größer als die Spitzenwerte, für die Sie testen. Adobe empfiehlt, Live-Schaltungs-Szenarien zu testen, um sicherzustellen, dass das System diese Situation bewältigen kann.

| Szenario | Testtyp | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Spitzenwert Go-Live | Homepage | 200 | 20 |  |  |
|   | Suchen | 100 | 10 |  |  |
|   | Nachrichten | 200 | 20 |  |  |
|   | Ereignisse | 200 | 20 |  |  |
|   | Aktivierungen | 20 | 20 |  | Simulation des Autorenverhaltens. |

#### Fehlerszenario-Tests {#error-scenario-tests}

Testen Sie Fehlerszenarien, um sicherzustellen, dass das System richtig und angemessen reagiert. Nicht nur in der Art und Weise, wie der Fehler selbst gehandhabt wird, sondern auch in den Auswirkungen, die er auf die Leistung haben kann. Beispiel:

* Was passiert, wenn ein Benutzer einen ungültigen Suchbegriff in das Suchfeld eingibt?
* Was passiert, wenn der Suchbegriff so allgemein ist, dass eine übermäßig große Anzahl an Ergebnissen zurückgegeben wird?

Bei der Konzeption dieser Tests sollte beachtet werden, dass nicht alle Szenarien regelmäßig auftreten. Ihre Auswirkungen auf das gesamte System sind jedoch wichtig.

| Fehlerszenario | Fehlertyp | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Überlastung der Suchkomponente | Suche mit einem globalen Platzhalter (Sternchen) | 10 | 1 |  | Es wird nur nach &amp;ast;&amp;ast;&amp;ast; gesucht. |
|   | Stoppwort | 20 | 2 |  | Suchen nach einem Stoppwort. |
|   | Leere Zeichenfolge | 10 | 1 |  | Suchen nach einer leeren Zeichenfolge. |
|   | Sonderzeichen | 10 | 1 |  | Suchen nach Sonderzeichen. |

#### Belastungstests {#endurance-tests}

Bestimmte Probleme treten erst auf, nachdem das System über einen ununterbrochenen Zeitraum (Stunden oder Tage) ausgeführt wurde. Mit einem Dauertest wird eine konstante durchschnittliche Belastung über einen bestimmten Zeitraum getestet. Jede Leistungsbeeinträchtigung kann dann analysiert werden.

| Szenario | Testtyp | Anzahl der Benutzer | Tx/Sek (erwartet) | Tx/Sek (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Belastungstest (72 Stunden) | Homepage | 10 | 1 |  |  |
|   | Suchen | 10 | 1 |  |  |
|   | Nachrichten | 20 | 2 |  |  |
|   | Ereignisse | 10 | 1 |  |  |
|   | Aktivierungen | 1 | 3 |  | Simulation des Autorenverhaltens. |

### Optimierung {#optimization}

Optimieren Sie die Anwendung in den späteren Phasen der Implementierung, um die Leistungsziele zu erreichen und zu maximieren.

Alle vorgenommenen Optimierungen müssen auf folgende Bedingungen hin getestet werden:

* Sie dürfen die Funktionalität nicht beeinträchtigen.
* Sie wurden vor ihrer Veröffentlichung Belastungstests unterzogen.

Für Lastgenerierung, Leistungsüberwachung und/oder Ergebnisanalyse stehen eine Reihe von Tools zur Verfügung. Einige dieser Tools umfassen Folgendes:

* [JMeter](https://jmeter.apache.org/)
* [Load Runner](https://www.microfocus.com/de-de/portfolio/performance-engineering/overview)
* [InfraRED](https://www.infraredsoftware.com/)
* [Java™ Interactive Profile](https://jiprof.sourceforge.net/)

Führen Sie nach der Optimierung erneut einen Test durch, um die Auswirkung zu bestätigen.

### Reporting {#reporting}

Die fortlaufende Berichterstattung informiert alle über den Status. Wie bereits bei der Farbcodierung erwähnt, kann für diesen Status die Architekturzuordnung verwendet werden.

Nachdem alle Tests abgeschlossen sind, berichten Sie über Folgendes:

* Alle festgestellten kritischen Fehler
* Nicht-kritische Probleme, die noch eingehender untersucht werden müssen
* Etwaige Annahmen während der Tests
* Etwaige Empfehlungen, die sich aus den Tests ergeben

## Leistungsoptimierung bei Verwendung des Dispatchers {#optimizing-performance-when-using-the-dispatcher}

Der [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) ist das Caching- und/oder Lastenausgleichstool von Adobe. Bei Verwendung des Dispatchers sollten Sie Ihre Website hinsichtlich der Cache-Leistung optimieren.

>[!NOTE]
>
>Dispatcher-Versionen sind AEM-unabhängig, die Dispatcher-Dokumentation ist jedoch in die AEM-Dokumentation eingebettet. Verwenden Sie immer die Dispatcher-Dokumentation, die in der Dokumentation für die neueste Version von AEM eingebettet ist.
>
>Sie wurden möglicherweise zu dieser Seite umgeleitet, wenn Sie einem Link zur Dispatcher-Dokumentation gefolgt sind, der in die Dokumentation für eine frühere Version von AEM eingebettet ist.

Der Dispatcher bietet mehrere integrierte Mechanismen, mit denen Sie die Leistung optimieren können, wenn Ihre Website diese nutzt. In diesem Abschnitt erfahren Sie, wie Sie Ihre Website gestalten können, um die Vorteile der Zwischenspeicherung zu maximieren.

>[!NOTE]
>
>Vielleicht erinnern Sie sich daran, dass der Dispatcher den Cache auf einem standardmäßigen Webserver speichert. Wenn Sie diese Informationen kennen, können Sie alles zwischenspeichern, was Sie als Seite speichern und über eine URL abrufen können. Und Sie können keine anderen Daten speichern, wie etwa z. B. Cookies, Sitzungsdaten und Formulardaten.
>
>Allgemein beinhalten viele Caching-Strategien die Auswahl von geeigneten URLs ausgewählt, und sie verlassen sich nicht auf diese zusätzlichen Daten.
>
>Mit Dispatcher Version 4.1.11 können Sie auch Antwort-Header zwischenspeichern; siehe [Caching von HTTP-Antwort-Headern](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#configuring-the-dispatcher-cache-cache).
>

### Berechnen des Dispatcher-Cache-Verhältnisses {#calculating-the-dispatcher-cache-ratio}

Mit der Cache-Verhältnis-Formel wird der ungefähre Prozentsatz der vom Cache gehandhabten Anforderungen verglichen mit der Gesamtzahl der Systemanforderungen berechnet. Zum Berechnen des Cache-Verhältnisses benötigen Sie Folgendes:

* Die Gesamtzahl der Anforderungen. Diese Information können Sie der Apache-Datei `access.log` entnehmen. Weitere Informationen finden Sie in der [offiziellen Apache-Dokumentation](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

* Die Anzahl der Anforderungen, die von der Publishing-Instanz bereitgestellt wurden. Diese Information können Sie der Datei `request.log` der Instanz entnehmen. Weitere Informationen finden Sie unter [Interpretieren der Datei request.log](/help/sites-deploying/monitoring-and-maintaining.md#interpreting-the-request-log) und [Auffinden der Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#finding-the-log-files).

Die Formel zur Berechnung des Cache-Verhältnisses lautet:

* (Die Gesamtzahl der Anfragen **minus** der Anzahl der Anfragen in der Veröffentlichungsumgebung) **geteilt durch** die Gesamtanzahl der Anfragen.

Wenn beispielsweise die Gesamtzahl der Anfragen 129491 und die Anzahl der von der Publishing-Instanz bereitgestellten Anforderungen 58959 beträgt, dann ist das Cache-Verhältnis: **(129491 - 58959)/129491= 54,5 %**.

Wenn Sie keine 1-zu-1-Kopplung zwischen Publisher und Dispatcher haben, fügen Sie Anfragen von allen Dispatchern und Publishern hinzu, um eine genaue Messung zu erhalten. Siehe auch [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md).

>[!NOTE]
>
>Für eine optimale Leistung empfiehlt Adobe ein Cache-Verhältnis von 90 % bis 95 %.

#### Verwenden einer einheitlichen Seitencodierung  {#using-consistent-page-encoding}

Mit der Dispatcher-Version 4.1.11 können Sie Antwort-Header zwischenspeichern. Wenn Sie keine Antwort-Header im Dispatcher cachen, können Probleme auftreten, wenn Sie Informationen zur Seitencodierung im Header speichern. In diesem Fall wird die Standardcodierung des Webservers für die Seite verwendet, wenn der Dispatcher eine Seite aus dem Cache bereitstellt. Es gibt zwei Möglichkeiten, dieses Problem zu vermeiden:

* Wenn Sie nur eine Codierung verwenden, stellen Sie sicher, dass die auf dem Webserver verwendete Codierung mit der Standardcodierung der AEM-Website übereinstimmt.
* Verwenden Sie zum Festlegen der Codierung einen `<META>`-Tag im HTML-`head`-Abschnitt wie im folgenden Beispiel:

```xml
        <META http-equiv="Content-Type" content="text/html; charset=EUC-JP">
```

#### Vermeiden von URL-Parametern {#avoid-url-parameters}

Vermeiden Sie nach Möglichkeit URL-Parameter für Seiten, die Sie zwischenspeichern möchten. Wenn Sie beispielsweise über eine Bildergalerie verfügen, wird die folgende URL nie zwischengespeichert (es sei denn, der Dispatcher ist [entsprechend konfiguriert](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#configuring-the-dispatcher-cache-cache)):

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

Wenn Sie Benutzerinnen und Benutzern erlauben, die Schriftgröße (oder eine andere Layout-Anpassung) zu ändern, stellen Sie sicher, dass die verschiedenen Anpassungen in der URL berücksichtigt werden.

Beispielsweise werden Cookies nicht zwischengespeichert. Wenn Sie die Schriftgröße also in einem Cookie (oder einem ähnlichen Mechanismus) speichern, bleibt die Schriftgröße für die zwischengespeicherte Seite nicht erhalten. Daher gibt der Dispatcher Dokumente mit zufälliger Schriftgröße zurück.

Durch Einbeziehung der Schriftgröße in die URL als Selektor wird dieses Problem vermieden:

```xml
www.myCompany.com/news/main.large.html
```

>[!NOTE]
>
>Bei den meisten Layout-Aspekten ist es auch möglich, Stylesheets, Client-seitige Skripte oder beides zu verwenden. Diese Instrumente funktionieren gut mit Caching.
>
>Dies ist auch für Druckversionen nützlich, für die Sie eine URL verwenden können, wie etwa:
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

Wenn Sie Bilder für die Navigationseinträge verwenden, ist die Methode im Wesentlichen die gleiche wie bei Titeln, aber etwas komplexer. Speichern Sie alle Navigationsbilder mit den Zielseiten. Wenn Sie zwei Bilder für „normal“ und „aktiv“ verwenden, können Sie die folgenden Skripte verwenden:

* Ein Skript, das die Seite wie gewohnt anzeigt.
* Ein Skript, das „.normal“-Anforderungen verarbeitet und das normale Bild zurückgibt.
* Ein Skript, das „.active“-Anfragen verarbeitet und das aktivierte Bild zurückgibt.

Es ist wichtig, dass Sie diese Bilder mit demselben Namens-Handle wie die Seite erstellen, um sicherzustellen, dass durch eine Inhaltsaktualisierung diese Bilder und die Seite gelöscht werden.

Bei Seiten, die nicht geändert werden, bleiben die Bilder im Cache, obwohl die Seiten selbst automatisch ungültig gemacht werden.

#### Personalisierung {#personalization}

Es wird empfohlen, die Personalisierung auf den erforderlichen Bereich zu beschränken. Um zu veranschaulichen, warum:

* Wenn Sie eine frei anpassbare Startseite verwenden, muss diese Seite jedes Mal erstellt werden, wenn eine Benutzerin oder ein Benutzer sie anfordert.
* Wenn Sie dagegen zehn verschiedene Startseiten auswählen, können Sie jede dieser Startseiten zwischenspeichern und so die Leistung verbessern.

>[!TIP]
>Weitere Informationen zum Konfigurieren des Dispatcher-Caches finden Sie im [Tutorial zum AEM Dispatcher Cache](https://experienceleague.adobe.com/docs/experience-manager-learn/dispatcher-tutorial/overview.html?lang=de) und dort im Abschnitt [Caching geschützter Inhalte](https://experienceleague.adobe.com/docs/experience-manager-learn/dispatcher-tutorial/chapter-1.html?lang=de#dispatcher-tips-and-tricks).

Wenn Sie die einzelnen Seiten personalisieren, indem Sie den Namen der Benutzerin oder des Benutzers beispielsweise in die Titelleiste einfügen, wirkt sich dies auf die Leistung aus.

>[!TIP]
>Informationen zum Caching geschützter Inhalte finden Sie unter [Caching geschützter Inhalte](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=de) im Dispatcher-Handbuch.

Bezüglich der Mischung von eingeschränkten und öffentlichen Inhalten auf einer Seite sollten Sie eine Strategie erwägen, bei der Server-seitige Includes im Dispatcher verwendet werden, oder Client-seitige Includes über Ajax im Browser.

>[!TIP]
>
>Informationen zum Umgang mit gemischten öffentlichen und eingeschränkten Inhalten finden Sie unter [Einrichten von Sling Dynamic Include](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-sling-dynamic-include.html?lang=de).

#### Sticky-Verbindungen  {#sticky-connections}

[Sticky-Verbindungen](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de#the-benefits-of-load-balancing) stellen sicher, dass die Dokumente für eine Benutzerin oder einen Benutzer alle auf demselben Server erstellt werden. Wenn eine Benutzerin oder ein Benutzer diesen Ordner verlässt und später zu ihm zurückkehrt, bleibt die Verbindung erhalten. Um alle Dokumente zu speichern, die Sticky-Verbindungen für die Website erfordern, definieren Sie einen Ordner. Dieser sollte keine anderen Dokumente enthalten. Diese Funktion ist wichtig, wenn Sie personalisierte Seiten und Sitzungsdaten verwenden.

#### MIME-Typen {#mime-types}

Es gibt zwei Möglichkeiten, wie ein Browser den Typ einer Datei bestimmen kann:

1. Über ihre Erweiterung (z. B. `.html`, `.gif` und `.jpg`).
1. Über den MIME-Typ, den der Server mit der Datei sendet.

Für die meisten Dateien wird der MIME-Typ durch die Dateierweiterung angegeben Das bedeutet:

1. Über ihre Erweiterung (z. B. `.html`, `.gif` und `.jpg`).
1. Über den MIME-Typ, den der Server mit der Datei sendet.

Wenn der Dateiname keine Erweiterung aufweist, wird er als Nur-Text angezeigt.

Mit der Dispatcher-Version 4.1.11 können Sie Antwort-Header zwischenspeichern. Wenn Sie keine Antwort-Header auf dem Dispatcher zwischenspeichern, ist der MIME-Typ Teil des HTTP-Headers. Wenn Ihre AEM-Anwendung Dateien zurückgibt, deren Dateiendung nicht erkannt wird, sondern bei denen der MIME-Typ verwendet wird, werden diese Dateien möglicherweise nicht korrekt angezeigt.

Um sicherzustellen, dass Dateien ordnungsgemäß zwischengespeichert werden, befolgen Sie die folgenden Richtlinien:

* Stellen Sie sicher, dass Dateien immer die richtige Erweiterung haben.
* Verwenden Sie möglichst keine allgemeinen Dateibereitstellungsskripts mit URLs wie `download.jsp?file=2214`. Um URLs zu verwenden, die die Dateispezifikation enthalten, schreiben Sie das Skript neu. Im vorherigen Beispiel lautet diese Neufassung `download.2214.pdf`.

## Leistung bei der Sicherung {#backup-performance}

In diesem Abschnitt werden mehrere Benchmarks vorgestellt, mit denen die Leistung von AEM-Sicherungen und die Auswirkungen der Sicherungsaktivität auf die Anwendungsleistung bewertet wird. Die AEM-Sicherung stellt eine beträchtliche Belastung des laufenden Betriebs dar. Wir messen diese Belastung ebenso wie die Auswirkungen der Einstellungen der Sicherungsverzögerung, mit denen versucht wird, diese Auswirkungen abzufedern. Ziel ist es, einige Referenzdaten über die erwartete Leistung von Backups in realistischen Konfigurationen und Mengen von Produktionsdaten bereitzustellen und Anleitungen zur Schätzung der Sicherungszeiten für geplante Systeme zu geben.

### Referenzumgebung {#reference-environment}

#### Physikalisches System {#physical-system}

Die in diesem Dokument berichteten Ergebnisse stammen aus Benchmarks, die in einer Referenzumgebung mit der folgenden Konfiguration ausgeführt wurden. Diese Konfiguration ähnelt einer typischen Produktionsumgebung in einem Rechenzentrum:

* HP ProLiant DL380 G6, 8 CPUs x 2,533 GHz
* Serial angeschlossene SCSI-Laufwerke mit 300 GB, 10.000 RPM
* Hardware-RAID-Controller; acht Laufwerke in einem RAID0+5-Array
* VMware Image CPU x 2 Intel Xeon® E5540 mit 2,53 GHz
* Red Hat® Linux® 2.6.18-194.el5; Java™ 1.6.0_29
* Einzelne Authoring-Instanz

Das Festplatten-Subsystem auf diesem Server ist schnell und entspricht einer Hochleistungs-RAID-Konfiguration, die etwa auf einem Produktions-Server verwendet wird. Die Backup-Leistung kann abhängig von der Festplattenleistung sein, und die Ergebnisse in dieser Umgebung spiegeln die Leistung mit einer schnellen RAID-Konfiguration wider. Das VMware-Bild ist so konfiguriert, dass es über ein einzelnes großes Festplattenvolumen verfügt, das sich physisch im lokalen Festplattenspeicher auf dem RAID-Array befindet.

Durch die AEM-Konfiguration werden das Repository und der Datenspeicher auf demselben logischen Datenträger wie das Betriebssystem und die AEM-Software platziert. Das Zielverzeichnis für Backups befindet sich ebenfalls in diesem logischen Dateisystem.

#### Datenvolumen {#data-volumes}

Die folgende Tabelle zeigt die Größe der Datenvolumen, die in den Backup-Benchmarks verwendet werden. Zunächst wird der anfängliche Baseline-Inhalt installiert, dann werden zusätzliche bekannte Datenmengen hinzugefügt, um die Größe des gesicherten Inhalts zu erhöhen. Backups werden in bestimmten Schritten erstellt, um einen starken Inhaltszuwachs und die Menge zu repräsentieren, die an einem Tag produziert wird. Die Verteilung von Inhalten (Seiten, Bilder, Tags) basiert in etwa auf einer realistischen Zusammensetzung von Produktion und Assets. Seiten, Bilder und Tags sind auf maximal 800 untergeordnete Seiten beschränkt. Jede Seite enthält Titel-, Flash-, Text-/Bild-, Video-, Diashow-, Formular-, Tabellen-, Cloud- und Karussellkomponenten. Bilder werden aus einem Pool von 400 Dateien mit einer Größe von 37 KB bis 594 KB hochgeladen.

| Inhalt | Knoten | Seiten | Bilder | Tags |
|---|---|---|---|---|
| Basisinstallation | 69 610 | 562 | 256 | 237 |
| Kleiner Inhalt für inkrementelle Sicherung |  | +100 | +2 | +2 |
| Großer Inhalt für vollständige Sicherung |  | +10 000 | +100 | +100 |

Das Sicherungs-Benchmark wird mit den zusätzlichen Inhalten, die bei jeder Iteration hinzugefügt werden, wiederholt.

#### Benchmark-Szenarios {#benchmark-scenarios}

Die Backup-Benchmarks decken zwei Hauptszenarien ab: Sicherungen, wenn das System stark ausgelastet ist, und Sicherungen, wenn das System inaktiv ist. Obwohl allgemein empfohlen wird, Sicherungen möglichst bei inaktivem AEM-System durchzuführen, gibt es Situationen, in denen die Sicherung bei laufendem Betrieb durchgeführt werden muss.

* **Leerlaufzustand**: Sicherungen werden ohne andere Aktivität auf AEM durchgeführt.
* **Laufender Betrieb**: Sicherungen werden durchgeführt, während das System zu 80 % mit Online-Prozessen ausgelastet ist. Die Sicherungsverzögerung variiert, um die Auswirkung auf die Last zu ermitteln.

Die Sicherungszeiten und die Größe der resultierenden Sicherung können den AEM-Serverprotokollen entnommen werden. Es wird empfohlen, Sicherungen zu Zeiten zu planen, wenn AEM inaktiv ist, z. B. in der Nacht. Dieses Szenario ist für den empfohlenen Ansatz repräsentativ.

Die Last besteht aus erstellten Seiten, gelöschten Seiten, Durchläufen und Abfragen mit der größten Last, die durch Seitendurchläufe und Abfragen verursacht werden. Durch das Hinzufügen und Entfernen zu vieler Seiten wird die Arbeitsbereichsgröße kontinuierlich erhöht und das Abschließen von Backups verhindert. Die Verteilung des Ladevorgangs, den das Skript verwendet, beträgt 75 % Seitendurchläufe, 24 % Abfragen und 1 % Seitenerstellungen (einzelne Ebene ohne verschachtelte Unterseiten). Die größte Anzahl an durchschnittlichen Transaktionen pro Sekunde in einem inaktiven System wird mit vier gleichzeitigen Threads erzielt, wie sie auch beim Testen von Sicherungen unter Last verwendet werden.

Die Auswirkung von Last auf die Sicherungsleistung kann geschätzt werden, indem die Differenz zwischen der Leistung mit Anwendungslast und der Leistung ohne Anwendungslast errechnet wird. Die Auswirkungen der Sicherung auf den Anwendungsdurchsatz werden ermittelt, indem der Szenario-Durchsatz in Transaktionen pro Stunde mit und ohne gleichzeitiges Backup verglichen wird und Backups mit unterschiedlichen Einstellungen für „Backup-Verzögerung“ ausgeführt werden.

* **Verzögerungseinstellung** – In verschiedenen Szenarien wurde die Einstellung für die Sicherungsverzögerung ebenfalls geändert, indem Werte von 10 Millisekunden (Standard), 1 Millisekunden und 0 Millisekunden verwendet wurden, um zu untersuchen, wie sich diese Einstellung auf die Leistung von Backups auswirkte.
* **Backup-Typ**: Alle Backups waren externe Sicherungen des Repositorys in einem Sicherungsverzeichnis ohne Komprimierung, außer in einem Fall, bei dem zu Vergleichszwecken der TAR-Befehl direkt angewendet wurde. Da inkrementelle Sicherungen nicht in eine ZIP-Datei geschrieben werden können oder wenn die vorherige vollständige Sicherung eine ZIP-Datei ist, wird in Produktionssituationen meist die Sicherungsverzeichnismethode verwendet.

### Zusammenfassung der Ergebnisse {#summary-of-results}

#### Sicherungsdauer und Durchsatz {#backup-time-and-throughput}

Als Hauptergebnis dieser Benchmarks kann gezeigt werden, wie die Sicherungsdauer je nach Sicherungstyp und Datenmenge variiert. Die folgende Grafik zeigt die Backup-Zeit unter Verwendung der standardmäßigen Backup-Konfiguration als eine Funktion der Gesamtzahl von Seiten.

![chlimage_1-81](assets/chlimage_1-81.png)

Die Backup-Zeiten in einer inaktiven Instanz sind relativ konsistent und liegen im Durchschnitt bei 0,608 MB pro Sekunde, unabhängig davon, ob es sich um vollständige oder inkrementelle Backups handelt (siehe Diagramm unten). Die Backup-Zeit ist lediglich eine Funktion der Datenmenge, die gesichert wird. Die Zeit für den Abschluss einer vollständigen Sicherung steigt deutlich mit der Gesamtzahl der Seiten. Die Zeit, um ein inkrementelles Backup durchzuführen, steigt ebenfalls mit der Gesamtanzahl der Seiten, jedoch mit einer wesentlich geringeren Geschwindigkeit. Die Dauer der inkrementellen Sicherung ist aufgrund der relativ geringen Menge an zu sichernden Daten viel kürzer.

Die Größe der erzeugten Sicherung ist entscheidend für die Sicherungsdauer. Die folgende Grafik zeigt die benötigte Zeit in Abhängigkeit von der endgültigen Backup-Größe.

![chlimage_1-82](assets/chlimage_1-82.png)

Dieses Diagramm zeigt, dass sowohl inkrementelle als auch vollständige Backups einem einfachen Größe-vs-Zeit-Muster folgen, das von Adobe als Durchsatz gemessen werden kann. Die Backup-Zeiten in einer inaktiven Instanz sind relativ konsistent und erreichen im Durchschnitt 0,61 MB pro Sekunde, unabhängig davon, ob es sich in der Benchmark-Umgebung um vollständige oder inkrementelle Backups handelt.

#### Backup-Verzögerung {#backup-delay}

Der Parameter für die Backup-Verzögerung wird bereitgestellt, um zu begrenzen, in welchem Umfang Backups zu Problemen bei Produktions-Workloads führen können. Der Parameter gibt eine Wartezeit in Millisekunden an, die Datei um Datei in den Backup-Vorgang integriert wird. Der Gesamteffekt hängt zum Teil von der Größe der betroffenen Dateien ab. Die Messung der Backup-Leistung in MB/s bietet eine vernünftige Möglichkeit, die Auswirkungen einer Verzögerung auf das Backup zu vergleichen.

* Das gleichzeitige Ausführen eines Backups mit regulärer Anwendungslast hat negative Auswirkungen auf den Durchsatz bei normaler Auslastung.
* Die Auswirkungen können leicht (bis zu 5 %) oder signifikant sein und einen Rückgang des Durchsatzes von bis zu 75 % verursachen. Dies hängt wahrscheinlich am meisten von der Anwendung ab.
* Die Sicherung stellt keine große Last für die CPU dar. Prozessorintensive Produktionsaufgaben werden deshalb durch die Sicherung weniger stark beeinträchtigt als I/O-intensive Aufgaben.

![chlimage_1-83](assets/chlimage_1-83.png)

Zum Vergleich: der Durchsatz, der mithilfe einer Dateisystemsicherung („TAR“) ermittelt wurde, um dieselben Repository-Dateien zu sichern. Die Leistung des TAR-Backups ist vergleichbar, ist jedoch höher als die Sicherung mit einer Verzögerung von null. Durch die Festlegung einer geringen Verzögerung wird der Backup-Durchsatz erheblich reduziert, und die Standardverzögerung von 10 Millisekunden führt zu einem deutlich geringeren Durchsatz. In Situationen, in denen Sicherungen geplant werden können, wenn die allgemeine Anwendungsnutzung gering ist oder die Anwendung inaktiv sein kann, reduzieren Sie die Verzögerung unter den Standardwert, damit das Backup schneller fortgesetzt werden kann.

Die tatsächlichen Auswirkungen des Durchsatzes einer laufenden Sicherung hängen von den Anwendungs- und Infrastrukturdetails ab. Die Auswahl des Verzögerungswerts sollte durch empirische Analyse der Anwendung erfolgen, sollte jedoch so klein wie möglich sein, damit Backups so schnell wie möglich abgeschlossen werden können. Da es nur eine schwache Korrelation zwischen der Auswahl des Verzögerungswerts und den Auswirkungen auf den Anwendungsdurchsatz gibt, sollte die Wahl der Verzögerung kürzere Backup-Zeiten bevorzugen, um die Gesamtauswirkungen von Backups zu minimieren. Ein Backup, das acht Stunden dauert, aber den Durchsatz um -20 % beeinflusst, hat wahrscheinlich eine größere Gesamtwirkung als ein Backup, das zwei Stunden dauert, aber den Durchsatz um -30 % beeinflusst.

### Verweise {#references}

* [Verwaltung – Sichern und Wiederherstellen](/help/sites-administering/backup-and-restore.md)
* [Verwaltung – Kapazität und Volumen ](/help/managing/best-practices-further-reference.md#capacity-and-volume)
