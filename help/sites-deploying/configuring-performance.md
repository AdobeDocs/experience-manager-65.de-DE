---
title: Leistungsoptimierung
seo-title: Leistungsoptimierung
description: Hier erfahren Sie, wie Sie bestimmte Aspekte von AEM konfigurieren können, um die Leistung zu optimieren.
seo-description: Hier erfahren Sie, wie Sie bestimmte Aspekte von AEM konfigurieren können, um die Leistung zu optimieren.
uuid: a4d9fde4-a4c7-4ee5-99b6-29b0ee7dc35b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
discoiquuid: 80118cd1-73e1-4675-bbdf-85d66d150abc
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# Leistungsoptimierung{#performance-optimization}

>[!NOTE]
>
>Allgemeine Richtlinien zur Leistung finden Sie auf der Seite [Leistungsrichtlinien](/help/sites-deploying/performance-guidelines.md).
>
>Weitere Informationen zur Fehlerbehebung und zur Beseitigung von Leistungsproblemen finden Sie außerdem im [Leistungsbaum](/help/sites-deploying/performance-tree.md).
>
>Zusätzlich ist ein Artikel in der Wissensdatenbank mit [Tipps zur Leistungsoptimierung](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html) verfügbar. 

Ein wichtiger Faktor ist die Zeit, die Ihre Website benötigt, um auf Anforderungen durch Besucher zu reagieren. Obwohl dieser Wert für jede Anforderung anders ist, kann ein durchschnittlicher Zielwert definiert werden. Sobald sich gezeigt hat, dass dieser Wert längerfristig erreichbar ist, kann er verwendet werden, um die Leistung der Website zu überwachen und auf potenzielle Probleme hinzuweisen.

Die von Ihnen angestrebten Antwortzeiten sind aufgrund der unterschiedlichen Zielgruppen in der Autoren- und der Veröffentlichungsumgebung wahrscheinlich unterschiedlich:

## Autorenumgebung {#author-environment}

Diese Umgebung wird von Autoren zur Eingabe und Aktualisierung von Inhalten verwendet. Sie muss für eine kleine Anzahl von Benutzern geeignet sein, von denen jeder zahlreiche leistungsintensive Anforderungen beim Aktualisieren von Inhaltsseiten und einzelnen Elementen auf diesen Seiten erzeugt.

## Veröffentlichungsumgebung {#publish-environment}

Diese Umgebung enthält Inhalte, die Sie Ihren Benutzern zugänglich machen. Hier ist die Anzahl der Anfragen sogar noch größer und die Geschwindigkeit ist ebenso wichtig, aber da die Art der Anfragen weniger dynamisch ist, können zusätzliche leistungssteigernde Mechanismen angewendet werden. wie das Zwischenspeichern des Inhalts oder den Lastenausgleich.

>[!NOTE]
>
>* Folgen Sie nach der Konfiguration zur Leistungsoptimierung der Anleitung in [Tough Day](/help/sites-developing/tough-day.md), um die Umgebung unter starker Belastung zu testen.
>* Siehe auch [Tipps zur Leistungsoptimierung](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html).
>



## Methode zur Leistungsoptimierung {#performance-optimization-methodology}

Beachten Sie diese fünf einfachen Regeln zur Leistungsoptimierung von CQ-Projekten, um Probleme von Anfang an zu vermeiden:

1. [Zeit für die Optimierung einplanen](#planning-for-optimization) 
1. [Reale Situationen simulieren](#simulate-reality) 
1. [Konkrete Ziele festlegen](#establish-solid-goals) 
1. [Relevante Maßnahmen treffen](#stay-relevant) 
1. [Agile Iterationszyklen](#agile-iteration-cycles) 

Diese Regeln gelten weitgehend für Webprojekte im Allgemeinen und sind für Projektmanager und Systemadministratoren relevant, um sicherzustellen, dass ihre Projekte nicht vor Leistungsproblemen stehen, wenn die Startzeit eintritt.

### Zeit für die Optimierung einplanen {#planning-for-optimization}

![chlimage_1-3](assets/chlimage_1-3.jpeg)

Ca. 10 % der Projektarbeit sollten für die Leistungsoptimierung reserviert werden. Natürlich hängen die tatsächlichen Anforderungen an die Leistungsoptimierung von der Komplexität eines Projekts und der Erfahrung des Entwicklerteams ab. Auch wenn Ihr Projekt nicht die gesamte einkalkulierte Zeit beanspruchen sollte, ist es empfehlenswert, bei der Leistungsoptimierung die vorgeschlagene Zeit zu berücksichtigen.

Wenn möglich, sollte ein Projekt zunächst weich auf eine begrenzte Audience gestartet werden, um echte Erfahrungen zu sammeln und weitere Optimierungen durchzuführen, ohne den zusätzlichen Druck zu erhöhen, der auf eine vollständige Ankündigung folgt.

Doch auch nach dem Launch muss die Projektoptimierung fortgesetzt werden. Der Lauch ist der Moment, in dem Ihr System einer „echten“ Belastung ausgesetzt wird. Deshalb sollten nach dem Launch zusätzliche Anpassungen eingeplant werden.

Da die Systembelastung variiert und sich die Leistungsprofile Ihres Systems im Laufe der Zeit verändern, sollte alle sechs bis zwölf Monate eine Leistungsanpassung oder eine Systemüberprüfung vorgenommen werden.

### Reale Situationen simulieren {#simulate-reality}

![chlimage_1-4](assets/chlimage_1-4.jpeg)

Wenn Sie nach dem Launch einer Website feststellen, dass Leistungsprobleme auftreten, gibt es nur einen Grund dafür: In Ihren Belastungs- und Leistungstests wurde die Realität nicht gut genug simuliert.

Die Simulation der Realität ist schwierig, und wie viel Mühe Sie vernünftigerweise investieren wollen, um &quot;real&quot; zu werden, hängt von der Natur Ihres Projekts ab. „Real“ bedeutet nicht nur „realer Code“ und „realer Traffic“, sondern auch „realer Inhalt“, insbesondere was die Inhaltsgröße und Struktur anbelangt. Ihre Vorlagen können sich nämlich je nach Größe und Struktur des Repositorys völlig anders verhalten.

### Konkrete Ziele festlegen {#establish-solid-goals}

![chlimage_1-5](assets/chlimage_1-5.jpeg)

Die Bedeutung einer ordnungsgemäßen Festlegung von Leistungszielen ist nicht zu unterschätzen. Oft ist es, sobald Menschen sich auf bestimmte Leistungsziele konzentrieren, sehr schwierig, diese Ziele nachträglich zu ändern, auch wenn sie auf wilden Annahmen beruhen.

Das Festlegen guter, konkreter Leistungsziele ist eine der schwierigsten Aufgaben. Oft empfiehlt es sich, echte Protokolle und Benchmarks von einer vergleichbaren Website heranzuziehen (z. B. vom Vorgänger der neuen Website).

### Relevante Maßnahmen treffen {#stay-relevant}

![chlimage_1-6](assets/chlimage_1-6.jpeg)

Es ist wichtig, immer jeweils einen Engpass nach dem anderen zu optimieren. Wenn Sie mehrere Maßnahmen gleichzeitig treffen, ohne die Auswirkungen der einzelnen Optimierungen zu überprüfen, wissen Sie nicht, welche Optimierungsmaßnahme tatsächlich erfolgreich war.

### Agile Iterationszyklen {#agile-iteration-cycles}

![chlimage_1-7](assets/chlimage_1-7.jpeg)

Im Zuge der Leistungsanpassung werden Werte immer wieder gemessen, analysiert, optimiert und validiert, bis der Zielwert erreicht ist. Um diesem Aspekt gebührend Rechnung zu tragen, implementieren Sie nach jeder Iteration einen agilen Validierungsprozess in der Optimierungsphase und nicht einen aufwändigeren Testprozess, der eine größere Gewichtung ermöglicht.

Der Entwickler, der die Optimierung durchführt, sollte rasch erkennen können, ob mit einer Optimierung der Zielwert erreicht wurde. Dies ist eine wertvolle Information, denn sobald der Zielwert erreicht ist, ist die Optimierung abgeschlossen.

## Allgemeine Leistungsrichtlinien {#basic-performance-guidelines}

Im Allgemeinen sollten nicht gecachte HTML-Anforderungen weniger als 100 ms benötigen. Konkret wird Folgendes empfohlen:

* 70 % der Seitenanforderungen sollten in weniger als 100 ms beantwortet werden.
* 25 % der Seitenanforderungen sollten innerhalb von 100 ms bis 300 ms beantwortet werden.
* 4 % der Seitenanforderungen sollten innerhalb von 300 ms bis 500 ms beantwortet werden.
* 1 % der Seitenanforderungen sollten innerhalb von 500 ms bis 1000 ms beantwortet werden.
* Keine Seitenanforderung sollte länger als 1 Sekunde dauern.

Bei den obigen Zahlen gelten die folgenden Bedingungen:

* Gemessen in der Veröffentlichungsumgebung (keine zusätzliche Last durch die Autorenumgebung)
* Gemessen auf dem Server (keine zusätzliche Last durch das Netzwerk)
* Nicht gecacht (kein CQ-Ausgabe-Cache, kein Dispatcher-Cache)
* Nur für komplexe Objekte mit vielen Abhängigkeiten (HTML, JS, PDF usw.)
* Keine andere Last auf dem System

Häufige Ursachen für einen Leistungsabfall sind vor allem:

* Ineffiziente Speicherung im Dispatcher-Cache
* Verwendung von Abfragen in normalen Anzeigevorlagen

Anpassungen auf JVM- und Betriebssystemebene bedingen normalerweise keine großen Leistungssprünge und sollten deshalb ganz am Ende des Optimierungszyklus ausgeführt werden.

Die Struktur des Inhaltsrepositorys kann sich ebenfalls auf die Leistung auswirken. Die beste Leistung wird erzielt, wenn die Anzahl der untergeordneten Knoten in einem Inhaltsrepository 1.000 nicht übersteigt (allgemeine Regel).

Besonders wichtig in einem herkömmlichen Leistungsoptimierungsschritt sind:

* the `request.log`
* komponentenbasiertes Timing;
* ein Java Profiler.

### Leistung beim Laden und Bearbeiten von digitalen Assets {#performance-when-loading-and-editing-digital-assets}

Aufgrund des großen Datenvolumens beim Laden und Bearbeiten von digitalen Assets können Leistungsprobleme auftreten.

Die Leistung hängt dabei von zwei Faktoren ab:

* CPU - mehrere Kerne sorgen bei der Transkodierung für mehr Effizienz
* Festplatte: parallele RAID-Festplatten bewirken dasselbe

Stellen Sie zur Leistungssteigerung die folgenden Überlegungen an:

* Wie viele Assets werden pro Tag hochgeladen? Eine gute Schätzung erhalten Sie mit folgender Formel: 

![chlimage_1-77](assets/chlimage_1-77.png)

* Der Zeitraum, in dem Bearbeitungen durchgeführt werden (normalerweise während der Büroöffnungszeiten, länger bei internationalen Vorgängen).
* Die durchschnittliche Größe der hochgeladenen Bilder (und die Größe der pro Bild generierten Darstellungen) in Megabyte.
* Bestimmen Sie die durchschnittliche Datenrate: 

![chlimage_1-78](assets/chlimage_1-78.png)

* 80 % aller Bearbeitungen werden in 20 % der Zeit durchgeführt, weshalb zu Spitzenzeiten viermal die durchschnittliche Datenrate anfällt. Dies ist Ihr Leistungsziel.

## Leistungsüberwachung {#performance-monitoring}

Leistung (oder fehlende Leistung) ist das Erste, was Ihre Benutzer bemerken. Deshalb ist die Leistung wie bei jeder Anwendung mit einer Benutzeroberfläche von größter Bedeutung. Um die Leistung Ihrer CQ-Installation zu optimieren, müssen Sie verschiedene Attribute der Instanz und ihr Verhalten überwachen.

For information about how to perform performance monitoring, see [Monitoring Performance](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance).

Die Faktoren, die Leistungsprobleme verursachen, sind oft schwer zu erkennen, selbst wenn ihre Auswirkungen offenkundig sind.

Eine gute Basis ist die umfassende Kenntnis Ihres Systems bei Normalbetrieb. Wenn Sie nicht wissen, wie Ihre Umgebung im Normalbetrieb „aussieht“ und sich „verhält“, ist es schwierig, die Ursache eines Leistungsabfalls zu ermitteln. Deshalb sollten Sie sich Ihr System während des reibungslosen Betriebs genau ansehen und laufend Leistungsinformationen erfassen. Dies bietet Ihnen eine Vergleichsbasis, falls sich die Leistung verschlechtert.

Das folgende Diagramm veranschaulicht den möglichen Pfad einer CQ-Inhaltsanforderung – und damit die Anzahl der unterschiedlichen Elemente, die die Leistung beeinträchtigen können.

![chlimage_1-79](assets/chlimage_1-79.png)

Leistung wird auch durch das Verhältnis zwischen Volumen und Kapazität bestimmt:

**Volumen** Die Menge der Ausgabe, die vom System verarbeitet und bereitgestellt wird.

**Kapazität** Das System kann die Lautstärke bereitstellen.

Dies kann an unterschiedlichen Stellen des Web-Pfads veranschaulicht werden.

![chlimage_1-80](assets/chlimage_1-80.png)

Es gibt einige Funktionsbereiche, die häufig für eine Leistungsminderung verantwortlich sind:

* Caching
* Code der Anwendung (Ihres Projekts)
* Suchfunktion

### Grundregeln für die Leistung {#basic-rules-regarding-performance}

Gewisse Regeln sollten bei der Leistungsoptimierung beachtet werden:

* Die Leistungsanpassung *muss* Teil eines jeden Projekts sein.
* Führen Sie die Optimierung nicht in einer frühen Phase des Entwicklungszyklus durch.
* Die Leistung ist nur so gut wie das schwächste Glied.
* Achten Sie immer auf das Verhältnis zwischen Kapazität und Volumen.
* Optimieren Sie wichtige Dinge zuerst.
* Führen Sie nie Optimierungen ohne *realistische* Ziele durch.

>[!NOTE]
>
>Bedenken Sie, dass der zur Leistungsmessung verwendete Mechanismus häufig genau das beeinflusst, was Sie messen möchten. Sie sollten diese Aspekte stets berücksichtigen und dafür sorgen, dass ihre Auswirkungen möglichst gering gehalten werden. Insbesondere sollten Browser-Plug-ins deaktiviert werden.

## Konfiguration zur Leistungsoptimierung {#configuring-for-performance}

Gewisse Aspekte von CQ (und/oder des zugrunde liegenden CRX) können so konfiguriert werden, dass die Leistung optimiert wird. Im Folgenden werden Möglichkeiten und Vorschläge beschrieben. Überprüfen Sie zuerst, ob und wie Sie die beschriebene Funktionalität verwenden können, bevor Sie Änderungen vornehmen. 

>[!NOTE]
>
>Weitere Informationen finden Sie im [Artikel in der Wissensdatenbank](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html). 

### Suchindizierung {#search-indexing}

Ab AEM 6.0 wird eine Oak-basierte Repository-Architektur verwendet.

Hier finden Sie die aktuellen Indizierungsinformationen:

* [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md)
* [Anforderungen und Indizierung](/help/sites-deploying/queries-and-indexing.md) 

### Gleichzeitige Verarbeitung von Workflows {#concurrent-workflow-processing}

Begrenzen Sie die Anzahl der parallel ausgeführten Workflow-Prozesse, um die Leistung zu verbessern. Standardmäßig entspricht die Anzahl der gleichzeitig von der Workflow-Engine verarbeiteten Workflows der Anzahl der für die Java VM verfügbaren Prozessoren. Wenn Workflow-Schritte große Mengen von Verarbeitungsressourcen (RAM oder CPU) erfordern, kann es vorkommen, dass durch das gleichzeitige Ausführen mehrerer dieser Workflows die Serverressourcen stark beansprucht werden.

Wenn beispielsweise Bilder (oder DAM-Assets im Allgemeinen) hochgeladen werden, importieren Workflows diese Bilder automatisch in DAM. Bilder besitzen häufig eine hohe Auslösung, wodurch oft hunderte von MB in Heap-Speichern zur Verarbeitung beansprucht werden. Die gleichzeitige Verarbeitung solcher Bilder bedeutet eine hohe Last für das Speicher-Subsystem und den Garbage Collector.

Die Workflow-Engine verwendet Apache Sling-Auftragswarteschlangen zur Handhabung und Planung der Verarbeitung der Arbeitselemente. Die folgenden Auftragswarteschlangendienste wurden standardmäßig aus der Konfigurationsdienstfactory des Apache Sling Job Queue für die Verarbeitung von Workflow-Aufträgen erstellt:

* Granite-Workflow-Warteschlange: Die meisten Arbeitsablaufschritte, z. B. die, die DAM-Assets verarbeiten, verwenden den Granite Workflow Queue-Dienst.
* Externe Prozessauftragswarteschlange für Granite-Workflow: Dieser Dienst wird für spezielle externe Arbeitsablaufschritte verwendet, die normalerweise zur Kontaktaufnahme mit einem externen System und zum Abruf von Ergebnissen verwendet werden. Beispielsweise wird der Schritt „InDesign Media Extraction Process“ als externer Prozess implementiert. Die Workflow-Engine verwendet die externe Warteschlange zur Verarbeitung der Abfrage. (See [com.day.cq.workflow.exec.WorkflowExternalProcess](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/WorkflowExternalProcess.html).)

Konfigurieren Sie diese Dienste, um die maximale Anzahl der parallel ausgeführten Workflow-Prozesse zu beschränken.

**Hinweis:** Das Konfigurieren dieser Auftragswarteschlangen wirkt sich auf alle Workflows aus, es sei denn, Sie haben eine Auftragswarteschlange für ein bestimmtes Workflow-Modell erstellt (siehe Warteschlange für ein bestimmtes Workflow-Modell [konfigurieren](/help/sites-deploying/configuring-performance.md#configure-the-queue-for-a-specific-workflow) unten).

**Konfiguration im Repository**

If you are configuring the services [using a sling:OsgiConfig node](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository), you need to find the PID of the existing services, for example: org.apache.sling.event.jobs.QueueConfiguration.370aad73-d01b-4a0b-abe4-20198d85f705. Sie können den PID mithilfe der Webkonsole ermitteln.

Sie müssen die Eigenschaft queue.maxparallel konfigurieren.

**Konfiguration in der Web-Konsole** 

To configure these services [using the Web Console](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console), locate the existing configuration items below the Apache Sling Job Queue Configuration service factory.

Sie müssen die Eigenschaft Maximum Parallel Jobs konfigurieren.

### Konfigurieren der Warteschlange für einen spezifischen Workflow {#configure-the-queue-for-a-specific-workflow}

Erstellen Sie eine Auftragswarteschlange für ein bestimmtes Workflow-Modell, sodass Sie die Auftragsabwicklung für dieses Workflow-Modell konfigurieren können. Dadurch wird die Verarbeitung dieses Workflows durch Ihre Konfigurationen gesteuert, während die Verarbeitung anderer Workflows durch die Konfiguration der standardmäßigen Granite Workflow Queue gesteuert wird.

Wenn Workflow-Modelle ausgeführt werden, erstellen sie Sling-Aufträge für ein bestimmtes Thema. Standardmäßig entspricht das Thema den Themen, die für die allgemeine Granite Workflow Queue oder die Granite Workflow External Process Job Queue konfiguriert werden:

* com/adobe/granite/workflow/job&amp;ast;
* com/adobe/granite/workflow/external/job&amp;ast;

Die von Workflow-Modellen erstellten Auftragsthemen enthalten modellspezifische Suffixe. For example, the [!UICONTROL DAM Update Asset] workflow model generates jobs with the following topic:

com/adobe/granite/workflow/job/etc/workflow/models/dam/update_asset/jcr_content/model

Daher können Sie eine Auftragswarteschlange für das Thema erstellen, das dem Auftragsthema Ihres Workflow-Modells entspricht. Die Konfiguration der Leistungseigenschaften der Warteschlange wirkt sich nur auf das Workflow-Modell aus, das die Aufträge generiert, die dem Warteschlangenthema entsprechen.

The following procedure creates a job queue for a workflow, using the [!UICONTROL DAM Update Asset] workflow as an example.

1. Führen Sie das Workflow-Modell aus, für das Sie die Auftragswarteschlange erstellen möchten, sodass Themenstatistiken generiert werden. For example, add an image to Assets to execute the [!UICONTROL DAM Update Asset] workflow.
1. Öffnen Sie die Sling Jobs-Konsole. ([http://localhost:4502/system/console/slingevent](http://localhost:4502/system/console/slingevent))
1. Suchen Sie die Workflow-Themen in der Konsole. Für „DAM-Update-Asset“ werden die folgenden Themen gefunden:

   * com/adobe/granite/workflow/external/job/etc/workflow/models/dam/update_asset/jcr_content/model
   * com/adobe/granite/workflow/job/etc/workflow/models/dam/update_asset/jcr_content/model
   * com/adobe/granite/workflow/job/etc/workflow/models/dam-xmp-writeback/jcr_content/model

1. Erstellen Sie für jedes Thema eine Auftragswarteschlange. Erstellen Sie zu diesem Zweck eine Werkskonfiguration für den Apache Sling Job Queue Factory Service.

   The factory configurations are similar to the Granite Workflow Queue described in [Concurrent Workflow Processing](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing), except the Topics property matches the topic of your workflow jobs.

### CQ5 DAM Asset Synchronization Service {#cq-dam-asset-synchronization-service}

`AssetSynchronizationService` dient zur Synchronisation von Assets von gemounteten Repositorys (z. B. LiveLink, Documentum). Standardmäßig wird hierbei alle 300 Sekunden (5 Minuten) eine Prüfung durchgeführt. Wenn Sie keine installierten Repositorys verwenden, können Sie diesen Dienst deaktivieren.

[Konfigurieren Sie dazu den OSGi-Dienst](/help/sites-deploying/configuring-osgi.md) **CQ DAM Asset Synchronization Service**, sodass der **Synchronisationszeitraum** (`scheduler.period`)(mindestens) 1 Jahr beträgt (definiert in Sekunden). 

### Mehrere DAM-Instanzen {#multiple-dam-instances}

Das Bereitstellen mehrerer DAM-Instanzen kann in folgenden Fällen die Leistung steigern: 

* Aufgrund regelmäßiger Uploads zahlreicher Assets in die Autorenumgebung entsteht eine hohe Last. In dieser Situation kann eine separate DAM-Instanz speziell für die Inhaltsverarbeitung reserviert werden.
* Sie haben mehrere Teams an Standorten auf der ganzen Welt (z. B. USA, Europa und Asien).

Zusätzliche Erwägungen sind:

* Trennung von unfertiger Arbeit in der Autorenumgebung von abgeschlossener Arbeit in der Veröffentlichungsumgebung
* Trennung von internen Benutzern in der Autorenumgebung von externen Besuchern/Benutzern in der Veröffentlichungsumgebung (z. B. Agenten, Pressevertreter, Kunden, Auszubildende usw.).

## Best Practices zur Qualitätssicherung {#best-practices-for-quality-assurance}

Leistung ist von größter Bedeutung für Ihre Veröffentlichungsumgebung. Deshalb müssen Sie die Leistungstests für die Veröffentlichungsumgebung während der Implementierung Ihres Projekts sorgfältig planen und analysieren.

In diesem Abschnitt erhalten Sie einen Überblick über Probleme bei der Definition eines Testkonzepts speziell für Leistungstests in der *Veröffentlichungsumgebung*. Dies ist vor allem für QA-Beauftragte, Projektleiter und Systemadministratoren von Interesse.

Im Folgenden wird die übliche Vorgehensweise bei der Durchführung von Leistungstests bei einer CQ-Anwendung in der *Veröffentlichungsumgebung* beschrieben. Diese umfasst die folgenden fünf Phasen:

* [Überprüfung des Wissens](#verification-of-knowledge) 
* [Definition des Umfangs](#scope-definition) 
* [Testmethoden](#test-methodologies) 
* [Definition von Leistungszielen](#defining-the-performance-goals) 
* [Optimierung](#optimization)

Die Kontrolle ist ein zusätzlicher, alles umfassender Prozess, der nötig ist, sich aber nicht auf Tests beschränkt.

### Überprüfung des Wissens {#verification-of-knowledge}

Der erste Schritt besteht darin, die grundlegenden für Tests erforderlichen Informationen zu dokumentieren:

* Die Architektur Ihrer Testumgebung
* Ein Plan der Anwendung mit einer genauen Angabe der internen Elemente, die getestet werden müssen (sowohl einzeln als auch in Kombination)

#### Testarchitektur {#test-architecture}

Sie sollten die Architektur der für die Leistungstests verwendeten Testumgebung genau dokumentieren.

Sie benötigen eine Reproduktion Ihrer geplanten Produktions-Veröffentlichungsumgebung gemeinsam mit dem Dispatcher und Load Balancer.

#### Anwendungsdiagramm {#application-map}

Um einen Überblick zu erhalten, können Sie ein Diagramm von der Anwendung erstellen (möglicherweise können Sie ein Diagramm von Tests in der Autorenumgebung verwenden).

Durch die Darstellung der internen Elemente der Anwendung erhalten Sie einen Überblick über die Testanforderungen. Wenn Sie Farbkodierung verwenden, können Sie dieses Diagramm auch für einen Bericht verwenden.

### Definition des Umfangs {#scope-definition}

Eine Anwendung kann in der Regel auf vielfältige Weise eingesetzt werden. Oft sind dabei manche Anwendungsfälle wichtiger als andere.

Um den Umfang des Leistungstests speziell auf die Veröffentlichungsumgebung anzupassen, empfehlen wir Ihnen die Definition folgender Punkte:

* Die wichtigsten Anwendungsfälle für Ihr Unternehmen
* Die wichtigsten technischen Anwendungsfälle

Sie können die Anzahl von Anwendungsfällen frei wählen, sie sollte aber auf einen Wert beschränkt sein, der einfach zu handhaben ist (z. B. fünf bis zehn).

Nach der Auswahl der wichtigsten Anwendungsfälle können die KPIs (Key Performance Indicators) und die Werkzeuge für ihre Messung definiert werden. Beispiele für häufige KPIs sind:

* End-to-end-Antwortzeit
* Servlet-Antwortzeit
* Reaktionszeit für eine einzelne Komponente
* Reaktionszeit für die Dienste
* Anzahl der inaktiven Threads im Thread-Pool
* Anzahl der freien Verbindungen
* Systemressourcen wie CPU und I/O-Zugriff

### Testmethoden {#test-methodologies}

Im Folgenden werden vier Szenarien für das Definieren und Testen der Leistungsziele beschrieben:

* Tests einzelner Komponenten
* Tests kombinierter Komponenten
* *Going Live*-Szenario
* Fehlerszenarien

Es gelten die folgenden Prinzipien:

**Belastungsgrenze der Komponente** 

* Jede Komponente hat eine bestimmte Belastungsgrenze in Bezug auf die Leistung. Dies bedeutet, dass eine Komponente bis zu einem gewissen Punkt eine gute Leistung erbringt, diese ab diesem Punkt aber rapide nachlässt.
* Um einen vollständigen Überblick über die Anwendung zu erhalten, müssen Sie zunächst feststellen, wann bei Ihren Komponenten diese Belastungsgrenze erreicht ist.
* Um die Belastungsgrenze festzustellen, können Sie einen Belastungstest durchführen, bei dem Sie über einen gewissen Zeitraum die Anzahl der Benutzer erhöhen und so die Last steigern. Durch die Überwachung dieser Last und der Antwort der Komponenten erkennen Sie ein spezifisches Leistungsverhalten, wenn die Belastungsgrenze der Komponente erreicht ist. Diese Grenze kann durch die Anzahl gleichzeitiger Transaktionen pro Sekunde zusammen mit der Anzahl gleichzeitiger Benutzer angegeben werden (sofern die Komponente von diesem KPI beeinflusst wird).
* Diese Information kann dann als Vergleichswert für Verbesserungen herangezogen werden und Ihnen helfen, die Effizienz der ergriffenen Maßnahmen zu beurteilen und Testszenarien zu definieren.

**Transaktionen** 

* Der Ausdruck „Transaktion“ bezieht sich auf die Anforderung einer kompletten Webseite, einschließlich der Seite selbst und aller darauf folgenden Aufrufe, d. h. auf die Seitenanforderung, etwaige AJAX-Aufrufe, Bilder und andere Objekte.**Anforderungsanalyse**
* Um jede Anforderung vollständig zu analysieren, können Sie jedes Element des Aufrufstapels abbilden und dann aus der durchschnittlichen Verarbeitungszeit eines jeden Elements die Summe berechnen.

### Leistungsziele definieren {#defining-the-performance-goals}

Nachdem der Umfang und die zugehörigen KPIs definiert wurden, können die spezifischen Leistungsziele festgelegt werden. Dies umfasst das Konzipieren von Testszenarien und Zielwerten.

Die Leistung muss bei durchschnittlicher Belastung und unter Spitzenlast getestet werden. Darüber hinaus müssen Sie Tests für „Going Live“-Szenarien durchführen, um zu gewährleisten, dass Ihre Website auch dem stärkeren Andrang unmittelbar nach dem Launch gewachsen ist.

Beim Festlegen künftiger Ziele können alle Erfahrungen und Statistiken von einer vorhandenen Website hilfreich sein, z. B. der maximale Datenverkehr auf Ihrer Live-Website.

#### Tests einzelner Komponenten {#single-component-tests}

Schlüsselkomponenten müssen bei durchschnittlicher Belastung und unter Spitzenlast getestet werden.

In beiden Fällen können Sie die erwartete Anzahl von Transaktionen pro Sekunde definieren, wenn eine vordefinierte Anzahl von Benutzern das System verwendet.

| Komponente | Testtyp | #Benutzer | Tx/s (erwartet) | Tx/s (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Homepage Einzelbenutzer | Durchschnitt | 1 | 1 |  |  |
|  | Spitze | 1 | 3 |  |  |
| Homepage 100 Benutzer | Durchschnitt | 100 | 3 |  |  |
|  | Spitze | 100 | 3 |  |

#### Tests kombinierter Komponenten {#combined-component-tests}

Durch das Testen der kombinierten Komponenten erhalten Sie eine genauere Darstellung des Verhaltens der Anwendung. Wiederum müssen Tests bei durchschnittlicher Belastung und unter Spitzenlast durchgeführt werden.

| Szenario | Komponente | #Benutzer | Tx/s (erwartet) | Tx/s (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Gemischter Durchschnitt | Homepage | 10 | 1 |  |  |
|  | Suchen | 10 | 1 |  |  |
|  | Nachrichten | 10 | 2 |  |  |
|  | Ereignisse | 10 | 1 |  |  |
|  | Aktivierungen | 10 | 3 |  | Simulation des Autorenverhaltens. |
| Gemischter Spitzenwert | Homepage | 100 | 5 |  |  |
|  | Suchen | 50 | 5 |  |  |
|  | Nachrichten | 100 | 10 |  |  |
|  | Ereignisse | 100 | 10 |  |  |
|  | Aktivierungen | 20 | 20 |  | Simulation des Autorenverhaltens. |

#### „Going Live“-Tests{#going-live-tests}

In den ersten Tagen nach dem Launch Ihrer Website ist mit erhöhtem Interesse zu rechnen. Dieses übersteigt wahrscheinlich die von Ihnen getesteten Spitzenwerte. Es wird dringend empfohlen, „Going Live“-Szenarien zu testen, um sicherzustellen, dass Ihr System einer solchen Situation gewachsen ist.

| Szenario | Testtyp | #Benutzer | Tx/s (erwartet) | Tx/s (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Live-Spitzenwert | Homepage | 200 | 20 |  |  |
|  | Suchen | 100 | 10 |  |  |
|  | Nachrichten | 200 | 20 |  |  |
|  | Ereignisse | 200 | 20 |  |  |
|  | Aktivierungen | 20 | 20 |  | Simulation des Autorenverhaltens. |

#### Tests von Fehlerszenarien {#error-scenario-tests}

Fehlerszenarien müssen auch getestet werden, um sicherzustellen, dass das System ordnungsgemäß reagiert. Dies umfasst nicht nur die Handhabung eines Fehlers selbst, sondern auch die möglichen Auswirkungen eines Fehlers auf die Leistung. Beispiel:

* Was passiert, wenn ein Benutzer einen ungültigen Begriff in das Suchfeld eingibt?
* Was passiert, wenn der Suchbegriff so allgemein ist, dass eine übermäßig große Anzahl an Ergebnissen zurückgegeben wird?

Bei der Planung dieser Tests sollten Sie bedenken, dass nicht alle Szenarien regelmäßig auftreten. Dennoch ist ihre Auswirkung auf das gesamte System wichtig.

| Fehlerszenario | Fehlertyp | #Benutzer | Tx/s (erwartet) | Tx/s (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Überladung der Suchkomponente | Suche nach globalen Platzhaltern (Sternchen) | 10 | 1 |  | Nur &amp;ast;&amp;ast;&amp;ast; durchsucht werden. |
|  | Wort anhalten | 20 | 2 |  | Suchen nach einem Stoppwort. |
|  | Leere Zeichenfolge | 10 | 1 |  | Suchen nach einer leeren Zeichenfolge. |
|  | Sonderzeichen | 10 | 1 |  | Suchen nach Sonderzeichen |

#### Belastungstests {#endurance-tests}

Gewisse Probleme treten erst auf, wenn das System über einen längeren Zeitraum hinweg aktiv war. Das können Stunden oder sogar Tage sein. Mit einem Belastungstest wird eine konstante durchschnittliche Belastung während eines bestimmten Zeitraums getestet. Danach kann ein etwaiger Leistungsabfall untersucht werden.

| Szenario | Testtyp | #Benutzer | Tx/s (erwartet) | Tx/s (getestet) | Beschreibung |
|---|---|---|---|---|---|
| Dauerprüfung (72 Stunden) | Homepage | 10 | 1 |  |  |
|  | Suchen | 10 | 1 |  |  |
|  | Nachrichten | 20 | 2 |  |  |
|  | Ereignisse | 10 | 1 |  |  |
|  | Aktivierungen | 1 | 3 |  | Simulation des Autorenverhaltens. |

### Optimierung {#optimization}

In den späteren Implementierungsphasen werden Sie die Anwendung optimieren müssen, um die Leistungsziele zu erreichen bzw. zu maximieren.

Alle vorgenommenen Optimierungen müssen auf folgende Bedingungen hin getestet werden:

* hat keine Auswirkungen auf die Funktionalität
* Sie wurden vor ihrer Veröffentlichung Belastungstests unterzogen.

Für die Lastgenerierung, Leistungsüberwachung und/oder Ergebnisanalyse steht eine Reihe von Tools zur Verfügung:

* [JMeter](https://jakarta.apache.org/jmeter/)
* [Load Runner](https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview)
* [Determyne](https://www.determyne.com/) InsideApps
* [InfraRED](https://www.infraredsoftware.com/)
* [Java Interactive Profile](https://jiprof.sourceforge.net/)
* Viele weitere...

Nach der Optimierung müssen Sie einen erneuten Test durchführen, um die Auswirkungen zu überprüfen.

### Berichterstellung {#reporting}

Um alle Beteiligten über den jeweiligen Stand auf dem Laufenden zu halten, ist eine kontinuierliche Berichterstellung erforderlich. Wie bereits gesagt, kann hierfür ein Anwendungsdiagramm mit Farbkodierung verwendet werden.

Nachdem alle Tests abgeschlossen sind, können Sie Berichte über folgende Bereiche erstellen:

* Alle festgestellten kritischen Fehler
* Nicht kritische Probleme, die noch weiter untersucht werden müssen
* Etwaige Annahmen während der Tests
* Etwaige Empfehlungen, die sich aus den Tests ergeben

## Optimieren der Leistung durch den Einsatz des Dispatchers {#optimizing-performance-when-using-the-dispatcher}

Der [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) ist das Caching- und/oder Lastausgleichs-Tool von Adobe. Bei Verwendung des Dispatchers sollten Sie Ihre Website hinsichtlich der Cache-Leistung optimieren. 

>[!NOTE]
>
>Dispatcher-Versionen sind unabhängig von AEM, die Dispatcher-Dokumentation ist jedoch in die AEM-Dokumentation eingebettet. Verwenden Sie immer die Dispatcher-Dokumentation, die in der Dokumentation für die neueste Version von AEM eingebettet ist.
>
>Möglicherweise wurden Sie von der Dispatcher-Dokumentation zu einer früheren AEM-Version zu dieser Seite weitergeleitet.

Der Dispatcher bietet verschiedene integrierte Mechanismen zur Optimierung der Leistung Ihrer Website. In diesem Abschnitt erfahren Sie, wie Sie Ihre Website einrichten, um die Vorteile der Zwischenspeicherung zu maximieren.

>[!NOTE]
>
>Beachten Sie dabei, dass der Dispatcher den Cache auf einem Standardwebserver speichert. Dies bedeutet, dass Sie:
>
>* alle Daten zwischenspeichern können, die als Seite gespeichert und mit einer URL abgerufen werden können
>* keine anderen Daten speichern können, z. B. Cookies, Sitzungsdaten und Formulardaten
>
>
Allgemein müssen für viele Caching-Strategien geeignete URLs ausgewählt werden, damit diese zusätzlichen Daten nicht benötigt werden.
>
>With Dispatcher version 4.1.11 you can also cache response headers, see [Caching HTTP Response Headers](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache).


### Dispatcher-Cache-Verhältnis berechnen {#calculating-the-dispatcher-cache-ratio}

Mit der Cache-Verhältnis-Formel wird der ungefähre Prozentsatz der vom Cache gehandhabten Anforderungen verglichen mit der Gesamtzahl der Systemanforderungen berechnet. Zur Berechnung des Cache-Verhältnisses benötigen Sie Folgendes:

* Die Gesamtzahl der Anforderungen. Diese Information können Sie der Apache-Datei `access.log` entnehmen. Weitere Informationen finden Sie in der [offiziellen Apache-Dokumentation](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

* Die Anzahl der von der Veröffentlichungsinstanz gehandhabten Anforderungen. This information is available in the `request.log` of the instance. For further details, see [Interpreting the request.log](/help/sites-deploying/monitoring-and-maintaining.md#interpreting-the-request-log) and [Finding the log Files](/help/sites-deploying/monitoring-and-maintaining.md#finding-the-log-files).

Die Formel zur Berechnung des Cache-Verhältnisses lautet:

* (The total number of requests **minus** the number of requests on Publish) **divided** by the total number of requests.

Beispiel: Die Gesamtzahl der Anforderungen ist 129491 und die Anzahl der von der Veröffentlichungsinstanz gehandhabten Anforderungen ist 58959. Das Cache-Verhältnis beträgt daher: **(129491 - 58959) : 129491 = 54,5 %**.

Wenn es keine direkte Entsprechung zwischen Publisher und Dispatcher gibt, müssen Sie die Anforderungen von allen Dispatchern und Publishern addieren, um eine korrekte Messung zu erhalten. Siehe auch [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md).

>[!NOTE]
>
>Für eine optimale Leistung empfiehlt Adobe ein Cache-Verhältnis von 90 % bis 95 %.

#### Verwenden einer einheitlichen Seitencodierung  {#using-consistent-page-encoding}

Mit der Dispatcher-Version 4.1.11 können Sie Antwort-Header cachen. Wenn Sie keine Antwort-Header im Dispatcher cachen, können Probleme auftreten, wenn Sie in der Kopfzeile Seitenkodierungsinformationen speichern. Wenn der Dispatcher in diesem Fall eine Seite aus dem Cache bereitstellt, wird die Standardkodierung des Webservers für die Seite verwendet. Es gibt zwei Möglichkeiten, um dieses Problem zu vermeiden:

* Wenn Sie nur eine Kodierung verwenden, achten Sie darauf, dass die auf dem Webserver verwendete Kodierung der Standardkodierung der AEM-Website entspricht.
* Verwenden Sie ein `<META>`-Tag im HTML-Abschnitt `head`, um die Codierung festzulegen. Beispiel:

```xml
        <META http-equiv="Content-Type" content="text/html; charset=EUC-JP">
```

#### Vermeiden von URL-Parametern {#avoid-url-parameters}

Vermeiden Sie, wenn möglich, URL-Parameter für Seiten, die Sie zwischenspeichern möchten. Wenn Sie beispielsweise eine Bildergalerie betrachten, wird die folgende URL nie zwischengespeichert (es sei denn, der Dispatcher wurde [entsprechend konfiguriert](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache)):

```xml
www.myCompany.com/pictures/gallery.html?event=christmas&amp;page=1
```

Sie können diese Parameter allerdings in der URL der Seite platzieren:

```xml
www.myCompany.com/pictures/gallery.christmas.1.html
```

>[!NOTE]
>
>Diese URL ruft dieselbe Seite und Vorlage auf wie „gallery.html“. In der Vorlagendefinition können Sie angeben, welches Skript die Seite rendern soll, oder Sie können ein Skript für alle Seiten verwenden.

#### Anpassen nach URL  {#customize-by-url}

Wenn Sie Benutzern die Möglichkeit geben, die Schriftgröße zu ändern (oder andere Layoutanpassungen vorzunehmen), stellen Sie sicher, dass die verschiedenen Anpassungen in der URL repräsentiert werden.

Beispielsweise werden Cookies nicht zwischengespeichert. Wenn Sie also die Schriftgröße in einem Cookie (oder einem ähnlichen Mechanismus) speichern, bleibt die Schriftgröße für die zwischengespeicherte Seite nicht erhalten. Daher gibt der Dispatcher Dokumente mit beliebiger Schriftgröße nach dem Zufallsprinzip zurück.

Wenn Sie die Schriftgröße in der URL als Selektor einschließen, wird dieses Problem vermieden:

```xml
www.myCompany.com/news/main.large.html
```

>[!NOTE]
>
>Bei den meisten Layoutkomponenten können auch Stylesheets und/oder clientseitige Skripts verwendet werden. Diese funktionieren normalerweise gut mit dem Zwischenspeichern.
>
>Dies ist auch für Druckversionen nützlich, für die Sie eine URL wie in diesem Beispiel erstellen können:
>
>`www.myCompany.com/news/main.print.html`
>
>Unter Verwendung des Skript-Globbings der Vorlagendefinition können Sie ein anderes Skript festlegen, das die Seiten für das Drucken anzeigt.

#### Invalidierung von als Titel verwendeten Bilddateien  {#invalidating-image-files-used-as-titles}

Wenn Sie Seitentitel oder anderen Text als Grafik rendern, sollten Sie die Dateien speichern, damit sie nach einer Inhaltsaktualisierung auf der Seite gelöscht werden:

1. Platzieren Sie die Bilddatei im selben Verzeichnis wie die Seite.
1. Verwenden Sie das folgende Namensformat für die Bilddatei:

   `<page file name>.<image file name>`

Beispielsweise können Sie den Titel der Seite „myPage.html“ in der Datei „myPage.title.gif“ speichern. Diese Datei wird automatisch gelöscht, wenn die Seite aktualisiert wird. Alle Änderungen des Seitentitels werden daher automatisch im Cache übernommen.

>[!NOTE]
>
>Die Bilddatei ist nicht unbedingt tatsächlich in der AEM-Instanz vorhanden. Sie können ein Skript verwenden, das die Bilddatei dynamisch erstellt. Der Dispatcher speichert die Datei dann auf dem Webserver.

#### Invalidierung von Bilddateien für die Navigation  {#invalidating-image-files-used-for-navigation}

Wenn Sie Bilder als Navigationseinträge verwenden, gehen Sie im Prinzip wie bei Titeln vor, das Verfahren ist nur etwas komplexer. Speichern Sie alle Navigationsgrafiken mit den Zielseiten. Wenn Sie zwei Bilder für den normalen und aktiven Status verwenden, können Sie die folgenden Skripts verwenden:

* Ein Skript, das die Seite normal anzeigt.
* Ein Skript, das „.normal“-Anforderungen verarbeitet und das normale Bild zurückgibt.
* Ein Skript, das „.active“ verarbeitet und das aktivierte Bild zurückgibt.

Sie müssen diese Grafiken mit demselben Namenhandle wie die Seite erstellen, um sicherzustellen, dass bei einer Inhaltsaktualisierung diese Bilder sowie die Seite gelöscht werden.

Bei Seiten, die nicht geändert werden, bleiben die Bilder im Cache, auch wenn die Seiten selbst normalerweise automatisch ungültig gemacht werden.

#### Personalisierung  {#personalization}

Der Dispatcher kann keine personalisierten Daten zwischenspeichern. Sie sollten die Personalisierung daher nur bei Bedarf verwenden. Dies hat folgende Gründe:

* Wenn Sie eine frei anpassbare Startseite verwenden, muss diese Seite jedes Mal erstellt werden, wenn ein Benutzer sie anfordert.
* Wenn Sie stattdessen eine Auswahl von 10 verschiedenen Startseiten anbieten, können Sie diese zwischenspeichern und so die Leistung verbessern.

>[!NOTE]
>
>Wenn Sie jede Seite personalisieren (zum Beispiel durch Einfügen des Benutzernamens in der Titelleiste), können Sie sie nicht zwischenspeichern. Dies kann die Leistung erheblich beeinträchtigen.
>
>Wenn dies jedoch erforderlich ist, haben Sie folgende Möglichkeiten:
>
>* Sie können die Seite mit iFrames aufteilen in einen Teil, der für alle Benutzer gleich ist, und einen Teil, der bei allen Seiten eines Benutzers gleich ist. Diese beiden Teile können dann zwischengespeichert werden.
>* Sie können mit clientseitigem JavaScript personalisierte Informationen anzeigen. Sie müssen jedoch sicherstellen, dass die Seite weiterhin richtig angezeigt wird, wenn ein Benutzer JavaScript deaktiviert.
>



#### Sticky-Verbindungen  {#sticky-connections}

[Sticky-Verbindungen](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html#the-benefits-of-load-balancing) stellen sicher, dass alle Dokumente für einen Benutzer auf demselben Server erstellt werden. Wenn ein Benutzer dieses Verzeichnis verlässt und später zurückkehrt, bleibt die Verbindung erhalten. Definieren Sie einen Ordner für alle Dokumente, die Sticky-Verbindungen für die Website benötigen. Speichern Sie möglichst keine anderen Dokumente in diesem Ordner. Dies wirkt sich auf den Lastenausgleich aus, wenn Sie personalisierte Seiten und Sitzungsdaten verwenden.

#### MIME-Typen  {#mime-types}

Es gibt zwei Möglichkeiten, wie ein Browser den Typ einer Datei bestimmen kann:

1. Durch die Erweiterung (z. B. .html, .gif, .jpg)
1. Durch den MIME-Typ, den der Server mit der Datei sendet.

Für die meisten Dateien wird der MIME-Typ durch die Dateierweiterung angegeben :

1. Durch die Erweiterung (z. B. .html, .gif, .jpg)
1. Durch den MIME-Typ, den der Server mit der Datei sendet.

Wenn der Dateiname keine Erweiterung aufweist, wird er als einfacher Text dargestellt.

Mit der Dispatcher-Version 4.1.11 können Sie Antwort-Header cachen. Wenn Sie keine Antwort-Header im Dispatcher cachen, beachten Sie, dass der Mime-Typ Bestandteil der HTTP-Kopfzeile ist. Wenn Ihre AEM-Anwendung daher Dateien zurückgibt, deren Dateiende nicht erkannt wurde und die stattdessen den MIME-Typ verwenden, werden diese Dateien möglicherweise falsch angezeigt.

Um sicherzustellen, dass Dateien richtig zwischengespeichert werden, halten Sie sich an die folgenden Richtlinien.

* Stellen Sie sicher, dass Dateien immer die richtige Erweiterung aufweisen.
* Verwenden Sie möglichst keine allgemeinen Dateibereitstellungsskripts mit URLs wie „download.jsp?file=2214“. Schreiben Sie das Skript so um, dass die URLs die Dateispezifikation enthalten. Im obigen Beispiel wäre dies „download.2214.pdf“.

## Leistung bei der Sicherung {#backup-performance}

In diesem Abschnitt werden mehrere Benchmarks vorgestellt, mit denen die Leistung von CQ-Sicherungen und die Auswirkungen der Sicherungsaktivität auf die Anwendungsleistung bewertet wird. Die CQ-Sicherung stellt eine beträchtliche Belastung des laufenden Betriebs dar. Wir messen diese Belastung ebenso wie die Auswirkungen der Sicherungsverzögerungseinstellungen, mit denen versucht wird, diese Auswirkungen abzufedern. Ziel dabei ist es, Referenzdaten zur erwarteten Sicherungsleistung bei realistischen Konfigurationen und Produktionsdatenmengen zu erhalten. Außerdem soll eine Orientierungshilfe zur Schätzung der Sicherungsdauer in geplanten Systemen geboten werden.

### Referenzumgebung {#reference-environment}

#### Physisches System {#physical-system}

Die in diesem Dokument genannten Ergebnisse stammen von Benchmarks, die in einer Referenzumgebung ausgeführt wurden und die folgende Konfiguration aufweisen. Diese Konfiguration ähnelt einer typischen Produktionsumgebung in einem Rechenzentrum:

* H-P ProLiant DL380 G6, 8 CPUs x 2.533 GHz
* Seriell angeschlossene SCSI-Laufwerke mit 300 GB, 10.000 RPM
* Hardware-RAID-Controller; 8 Festplatten in einer „RAID 0+5“-Anordnung
* VMware-Image-CPU x 2 Intel Xeon E5540 @ 2,53 GHz
* RedHat Linux 2.6.18-194.el5; Java 1.6.0_29
* Einzelne Autoreninstanz mit CQ 5.5 GM.

Das Plattensubsystem auf diesem Server ist relativ schnell und entspricht einer leistungsstarken RAID-Konfiguration, die auf einem Produktionsserver verwendet werden könnte. Die Leistung bei der Sicherung hängt von der Leistung der Festplatten ab und die Ergebnisse in dieser Umgebung spiegeln die Leistung einer extrem schnellen RAID-Konfiguration wider. Das VMWare-Abbild wird als ein einziger großer Datenträger konfiguriert, der sich physisch im lokalen Plattenspeicher im RAID-Array befindet.

Durch die CQ-Konfiguration werden das Repository und der Datenspeicher auf denselben logischen Datenträger wie das Betriebssystem und die CQ-Software platziert. Auch das Zielverzeichnis für Sicherungen befindet sich in diesem logischen Dateisystem.

#### Datenmengen {#data-volumes}

In der folgenden Tabelle werden die für die Sicherungs-Benchmarks verwendeten Datenmengen dargestellt. Zunächst wird der ursprüngliche Inhalt installiert, danach werden weitere bekannte Datenmengen hinzugefügt, um die Größe des gesicherten Inhalts zu steigern. Sicherungen werden in Inkrementen erstellt, um einen starken Inhaltszuwachs und die produzierte Tagesmenge nachzubilden. Die Verteilung der Inhalte (Seiten, Bilder, Tags) entspricht in etwa einer realistischen Asset-Zusammensetzung. Seiten, Bilder und Tags sind auf maximal 800 untergeordnete Seiten beschränkt. Jede Seite enthält Titel-, Flash-, Text/Bild-, Video-, Diashow-, Formular-, Tabellen-, Cloud- und Karussellkomponenten. Bilder werden aus einem Pool von 400 Dateien hochgeladen, deren Größe von 37 KB bis 594 KB reicht.

<table>
 <tbody>
  <tr>
   <td><strong>Inhalt</strong></td>
   <td><strong>Knoten</strong></td>
   <td><strong>Seiten</strong></td>
   <td><strong>Bilder</strong></td>
   <td><strong>Tags</strong></td>
  </tr>
  <tr>
   <td>Basisinstallation</td>
   <td>69,610</td>
   <td>562</td>
   <td>256</td>
   <td>237</td>
  </tr>
  <tr>
   <td>Kleine Inhalte für die inkrementelle Sicherung</td>
   <td><br type="_moz" /> </td>
   <td>+100</td>
   <td>+2</td>
   <td>+2</td>
  </tr>
  <tr>
   <td>Große Inhalte für vollständige Sicherung</td>
   <td><br type="_moz" /> </td>
   <td>+10,000</td>
   <td>+100</td>
   <td>+100</td>
  </tr>
 </tbody>
</table>

Das Sicherungs-Benchmark wird mit den zusätzlichen Inhalten wiederholt, die bei jeder Iteration hinzugefügt werden.

#### Benchmark-Szenarien {#benchmark-scenarios}

Die Sicherungs-Benchmarks beziehen sich auf zwei Hauptszenarien: Sicherungen bei hoher Anwendungslast und Sicherungen bei inaktivem System. Obwohl allgemein empfohlen wird, Sicherungen möglichst bei inaktivem CQ-System durchzuführen, gibt es Situationen, in denen die Sicherung bei laufendem Betrieb durchgeführt werden muss.

**Sicherungen im Leerlaufzustand** werden ohne weitere Aktivität auf CQ durchgeführt.

**Unter &quot;Datensicherungen laden** &quot;werden ausgeführt, während das System zu 80 % aus Online-Prozessen geladen wird. Die Sicherungsverzögerung variiert, um die Auswirkung auf die Last zu ermitteln.

Die Sicherungszeiten und die Größe der resultierenden Sicherung können den CQ-Serverprotokollen entnommen werden. Es wird empfohlen, Sicherungen zu Zeiten zu planen, wenn CQ inaktiv ist, z. B. in der Nacht. Dieses Szenario entspricht der empfohlenen Vorgehensweise.

Die Last besteht aus Seitenerstellungen/-löschungen, Traversierungen und Anforderungen, wobei der Großteil der Last von Traversierungen und Anforderungen stammt. Wenn laufend zu viele Seiten hinzugefügt und entfernt werden, wird die Größe des Arbeitsbereichs erhöht und Sicherungen können nicht durchgeführt werden. Die vom Skript verwendete Lastverteilung besteht aus 75 % Traversierungen, 24 % Anforderungen und 1 % Seitenerstellung (nur eine Ebene ohne verschachtelte Unterseiten). Die größte Anzahl an durchschnittlichen Transaktionen pro Sekunde in einem inaktiven System wird mit vier gleichzeitigen Threads erzielt, wie sie auch beim Testen von Sicherungen unter Last verwendet werden.

Die Auswirkung von Last auf die Sicherungsleistung kann geschätzt werden, indem die Differenz zwischen der Leistung mit Anwendungslast und der Leistung ohne Anwendungslast errechnet wird. Die Auswirkung der Sicherung auf den Anwendungsdurchsatz können Sie ermitteln, indem Sie den Durchsatz des Szenarios in Transaktionen pro Stunde mit und ohne gleichzeitige Sicherung mit Sicherungen vergleichen, die mit unterschiedlichen Verzögerungseinstellungen ausgeführt werden.

**Verzögerungseinstellung** In verschiedenen Szenarien änderten wir auch die Einstellung für die Backup-Verzögerung, wobei Werte von 10 ms (Standard), 1 ms und 0 ms verwendet wurden, um zu untersuchen, wie diese Einstellung die Leistung von Backups beeinflusste.

**Sicherungsart** Alle Sicherungen waren externe Sicherungen des Repositorys, die ohne Erstellung einer ZIP-Datei in einem Backup-Verzeichnis durchgeführt wurden, außer in einem Fall, in dem der Befehl &quot;tar&quot;direkt verwendet wurde. Da inkrementelle Sicherungen nicht in eine ZIP-Datei geschrieben werden können oder wenn die vorherige vollständige Sicherung eine ZIP-Datei ist, wird in Produktionssituationen meist die Sicherungsverzeichnismethode verwendet.

### Zusammenfassung der Ergebnisse {#summary-of-results}

#### Sicherungsdauer und Durchsatz {#backup-time-and-troughput}

Als Hauptergebnis dieser Benchmarks kann gezeigt werden, wie die Sicherungsdauer je nach Sicherungstyp und Datenmenge variiert. Das folgende Diagramm zeigt die erfasste Sicherungsdauer bei der Standard-Sicherungskonfiguration als eine Funktion der Seitenzahl.

![chlimage_1-81](assets/chlimage_1-81.png)

Die Sicherungsdauer in einer inaktiven Instanz ist relativ konstant und beträgt im Schnitt 0,608 MB/s unabhängig davon, ob es sich um eine vollständige oder inkrementelle Sicherung handelt (siehe Diagramm unten). Die Sicherungsdauer ist einfach eine Funktion der gesicherten Datenmenge. Die Dauer einer vollständigen Sicherung nimmt eindeutig mit der Seitenzahl zu. Auch die Dauer einer inkrementellen Sicherung nimmt mit der Seitenzahl zu, aber in einem wesentlich geringeren Ausmaß. Die Dauer einer inkrementellen Sicherung ist aufgrund der relativ kleinen Datenmenge wesentlich kürzer.

Die Größe der erzeugten Sicherung ist entscheidend für die Sicherungsdauer. Das folgende Diagramm zeigt die Dauer als Funktion der Sicherungsgröße.

![chlimage_1-82](assets/chlimage_1-82.png)

Dieses Diagramm zeigt, dass sowohl inkrementelle als auch vollständige Sicherungen einem einfachen Größe-Dauer-Verhältnis folgen, das wir als Durchsatz messen können. Die Sicherungsdauer in einer inaktiven Instanz ist relativ konstant und beträgt im Schnitt 0,61 MB/s unabhängig davon, ob es sich um eine vollständige oder inkrementelle Sicherung in der Benchmark-Umgebung handelt.

#### Sicherungsverzögerung {#backup-delay}

Mit dem Sicherungsverzögerungsparameter können Sie das Ausmaß beschränken, bis zu dem Produktionsaufgaben durch Sicherungen beeinträchtigt werden. Der Parameter gibt eine Wartezeit in Millisekunden an, die für jede Datei beim Sicherungsvorgang eingefügt wird. Die Wirkung hängt zum Teil von der Größe der jeweiligen Dateien ab. Durch das Messen der Sicherungsleistung in MB/s können die Auswirkungen der Verzögerung auf den Sicherungsvorgang verglichen werden.

* Die gleichzeitige Durchführung einer Sicherung während der regulären Anwendung wirkt sich negativ auf den Durchsatz der normalen Last aus.
* Diese Auswirkung kann nur geringfügig sein (5 % Durchsatzverminderung) oder sehr groß (75 %) Dies hängt zum Großteil von der jeweiligen Anwendung ab.
* Die Sicherung stellt keine große Last für die CPU dar. Prozessorintensive Produktionsaufgaben werden deshalb durch die Sicherung weniger stark beeinträchtigt als I/O-intensive Aufgaben.

![chlimage_1-83](assets/chlimage_1-83.png)

Zum Vergleich wurde der Durchsatz bei der Sicherung derselben Repository-Dateien mit einer Dateisystemsicherung (mit „tar“) geprüft. Die Leistung mit dem tar-Befehl ist vergleichbar, aber etwas höher als die Sicherung mit der mit null festgelegten Verzögerung. Wenn auch nur eine geringe Verzögerung ausgewählt wird, wird der Sicherungsdurchsatz stark reduziert. Die Standardverzögerung von 10 ms ergibt einen deutlich verringerten Durchsatz. Wenn eine Sicherung zu Zeiten geplant werden kann, in denen die Anwendung wenig ausgelastet oder völlig inaktiv ist, ist es empfehlenswert, die Verzögerung unter den Standardwert zu senken, damit die Sicherung schneller durchgeführt werden kann.

Die tatsächliche Auswirkung des Anwendungsdurchsatzes auf eine aktive Sicherung hängt von der Anwendung und der Infrastruktur ab. Die Auswahl des Verzögerungswerts sollte auf der Basis einer empirischen Analyse der Anwendung erfolgen, er sollte aber möglichst gering sein, damit Sicherungen so schnell wie möglich durchgeführt werden können. Da es nur eine schwache Korrelation zwischen der Wahl des Verzögerungswerts und der Auswirkung auf den Anwendungsdurchsatz gibt, sollte bei der Auswahl der Verzögerung eine kürzere Sicherungsdauer bevorzugt werden, um die Auswirkungen einer Sicherung zu minimieren. Eine Sicherung, die acht Stunden dauert, aber den Durchsatz um 20 % verringert, wirkt sich wahrscheinlich insgesamt stärker aus als eine Sicherung, die zwei Stunden dauert, aber den Durchsatz um 30 % verringert.

### Verweise {#references}

* [Administration – Sichern und Wiederherstellen](/help/sites-administering/backup-and-restore.md) 
* [Verwaltung – Kapazität und Volumen](/help/managing/best-practices-further-reference.md#capacity-and-volume) 

