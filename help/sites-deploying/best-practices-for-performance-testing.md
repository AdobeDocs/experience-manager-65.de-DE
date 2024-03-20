---
title: Best Practices für Leistungstests
description: Erfahren Sie mehr über die allgemeinen Strategien und Methoden, die für Leistungstests verwendet werden, sowie über einige der Tools, die zur Unterstützung des Prozesses verfügbar sind.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: fcac75e1-15c1-4a37-8d43-93c95267b903
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1790'
ht-degree: 98%

---

# Best Practices für Leistungstests{#best-practices-for-performance-testing}

## Einführung {#introduction}

Leistungstests sind ein wichtiger Bestandteil jeder AEM-Implementierung. Je nach Kundenanforderungen können Leistungstests für Publishing-Instanzen, Authoring-Instanzen oder beides durchgeführt werden.

In dieser Dokumentation werden die Gesamtstrategien und Methoden für die Durchführung von Leistungstests sowie einige der Tools beschrieben, die von Adobe zur Prozessunterstützung zur Verfügung gestellt werden. Lesen Sie abschließend eine Analyse der in AEM 6 verfügbaren Tools, um die Leistungsoptimierung zu unterstützen, sowohl aus der Sicht der Code-Analyse als auch der Systemkonfiguration.

### Simulieren der Realität {#simulating-reality}

Stellen Sie bei Leistungstests sicher, dass Sie eine Produktionsumgebung so nah wie möglich imitieren. Obwohl eine solche Aufgabe oft schwierig sein kann, ist es unerlässlich, die Genauigkeit dieser Tests zu gewährleisten. Bei der Erstellung von Leistungstests ist Folgendes zu berücksichtigen:

* Produktionsähnliche Inhalte

Viele Leistungsmessungen in AEM, wie z. B. die Antwortzeit der Abfrage, können durch die Größe des Inhalts im System beeinflusst werden. Es ist wichtig sicherzustellen, dass die Testumgebung so nah wie möglich an einer Kopie der Produktionsdaten liegt.

* Produktions-Code

Die AEM-Version und Hotfixes, die in der Produktion bereitgestellt werden, sollten in der Testumgebung gleich sein. Es ist auch wichtig, die Version des Codes zu testen, der in der Produktion bereitgestellt wird.

* Produktionsähnliche Hardware- und Netzwerkkonfiguration

Die Tests sind ohne eine Umgebung, die der Produktionsumgebung möglichst nahe kommt, sinnlos. Idealerweise sollten die Hardwarespezifikationen, Netzwerkschnittstellen, Lastenausgleich und CDN mit der Produktion in der Testumgebung identisch sein.

* Produktionsauslastung

Viele Leistungsprobleme treten erst auf, wenn das System stark ausgelastet ist. Gute Leistungstests sollten die Auslastung der Produktionssysteme zu Stoßzeiten simulieren.

### Festlegen von Zielen {#setting-goals}

Bevor Sie mit Leistungstests beginnen, müssen Sie nicht funktionale Anforderungen festlegen, um die Lade- und Antwortzeiten anzugeben. Wenn Sie von einem vorhandenen System migrieren, stellen Sie sicher, dass die Antwortzeiten Ihren aktuellen Produktionswerten ähnlich sind. Für die Auslastung ist es am besten, die aktuelle Spitzenlast zu verdoppeln. Dadurch wird sichergestellt, dass die Website auch weiterhin gut funktionieren kann, wenn sie wächst.

### Tools {#tools}

Auf dem Markt ist eine Vielzahl von Tools für Leistungstests erhältlich. Stellen Sie beim Ausführen eines Lastgenerators sicher, dass die Computer, die die Tests durchführen, über ausreichend Netzwerkbrandbreite verfügen. Andernfalls wird keine zusätzliche Belastung in der getesteten Umgebung erzeugt, sobald der Testrechner die Grenzen ihrer Verbindung erreicht.

#### Test-Tools {#testing-tools}

* Das Tool **Tough Day** von Adobe kann verwendet werden, um Auslastung auf AEM-Instanzen zu erzeugen und Leistungsdaten zu sammeln. Das Entwicklungs-Team von Adobe AEM setzt dieses Tool für Belastungstests beim eigentlichen AEM-Produkt ein. Die in Tough Day ausgeführten Skripte werden über Eigenschaftendateien und JMX-XML-Dateien konfiguriert. Weitere Informationen finden Sie unter der [Tough Day-Dokumentation](/help/sites-developing/tough-day.md).

* AEM bietet vorkonfigurierte Tools, um problematische Abfragen, Anforderungen und Fehlermeldungen schnell anzuzeigen. Weitere Informationen finden Sie im Abschnitt [Diagnose-Tools](/help/sites-administering/operations-dashboard.md#diagnosis-tools) der Dokumentation zum Vorgangs-Dashboard.
* Apache bietet ein Produkt namens **JMeter** an, das Leistungs- und Belastungstests sowie eine Überprüfung des Funktionsverhaltens ermöglicht. Es handelt sich um eine Open-Source-Software, die kostenlos verwendet werden kann, aber eine kleinere Funktion hat als Unternehmensprodukte und eine stärkere Lernkurve aufweist. JMeter können Sie auf der Apache-Website unter [https://jmeter.apache.org/](https://jmeter.apache.org/) herunterladen.

* **Load Runner** ist ein Enterprise-Produkt für Auslastungstests. Eine kostenlose Evaluierungsversion ist verfügbar. Weitere Informationen finden Sie unter [https://www.microfocus.com/de-de/portfolio/performance-engineering/overview](https://www.microfocus.com/de-de/portfolio/performance-engineering/overview).

* Tools zum Laden von Websites, [Vercara](https://vercara.com/website-performance-management) kann auch verwendet werden.
* Beim Testen mobiler oder responsiver Websites muss ein separater Satz von Tools verwendet werden. Diese drosseln die Netzwerkbrandbreite, um langsamere mobile Verbindungen wie 3G oder EDGE zu simulieren. Zu den gängigeren Tools gehören:

   * **[Network Link Conditioner](https://nshipster.com/network-link-conditioner/)** mit einer benutzerfreundlichen Oberfläche und einer relativ niedrigen Ebene im Netzwerk-Stack. Es sind OS X- und iOS-Versionen verfügbar.
   * [**Charles**](https://www.charlesproxy.com/), eine Web-Debugging-Proxy-Anwendung, die u. a. eine Netzwerkdrosselung ermöglicht. Es sind Versionen für Windows, OS X und Linux® verfügbar.

#### Optimierungs-Tools {#optimization-tools}

**Überwachung**

Die Dokumentation [Überwachung der Leistung](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance) liefert zahlreiche Informationen zu Tools und Methoden für die Diagnose von Problemen und Erkennung von Optimierungsbereichen.

**Entwicklermodus in der Touch-Benutzeroberfläche**

Eine der neuen Funktionen der Touch-Benutzeroberfläche von AEM 6 ist der Entwicklermodus. So wie Autoren und Autorinnen zwischen Bearbeitungs- und Vorschaumodi wechseln können, können Entwickelnde in der Autoren-Benutzeroberfläche in den Entwicklermodus wechseln. Auf diese Weise können Sie die Renderzeit für jede Komponente auf der Seite sehen und Stacktraces von Fehlern sehen. Weitere Informationen zum Entwicklermodus finden Sie in dieser [CQ Gems-Präsentation](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html).

**Verwendung von rlog.jar zum Lesen der Anfrageprotokolle**

Für eine eingehendere Analyse der Anforderungsprotokolle auf einem AEM-System können die von AEM erzeugten `request.log`-Dateien mit `rlog.jar` durchsucht und sortiert werden. Diese JAR-Datei ist Teil der AEM-Installation im Ordner `/crx-quickstart/opt/helpers`. Weitere Informationen zum rlog-Tool und zum Anfrageprotokoll im Allgemeinen finden Sie in der Dokumentation [Überwachung und Wartung](/help/sites-deploying/monitoring-and-maintaining.md).

**Das Tool „Abfrage erläutern“**

Mit dem [Tool „Abfrage erläutern“](/help/sites-administering/operations-dashboard.md#explain-query) in ACS AEM-Tools können Sie die beim Ausführen einer Abfrage verwendeten Indizes anzeigen. Dieses Tool ist nützlich bei der Optimierung langsamer Abfragen.

**PageSpeed-Tools**

Die PageSpeed-Tools von Google bieten Website-Analysen zur Einhaltung der Best Practices in Bezug auf die seitenbezogene Leistung sowie ein Plug-in, das zur weiteren Optimierung neben dem Dispatcher in einer Apache-Instanz installiert werden kann.
Siehe die [PageSpeed Tools-Website](https://developers.google.com/speed).

## Autorenumgebung {#author-environment}

### Durchführen von Tests {#performing-tests}

Um Leistungstests für die Authoring-Umgebung durchzuführen, müssen Sie das Erlebnis der Produktionsautoren simulieren. Die Authoring-Installationen müssen also alle Komponenten, OSGi-Bundles, Benutzeroberflächenanpassung, benutzerdefinierten Indizes und sonstigen Ergänzungen für die produktionsbezogenen Authoring-Instanzen umfassen.

Es gibt viele Automatisierungs-Frameworks, die auf Leistungs- und Belastungstests ausgelegt sind. Benutzerdefinierte Skripte können in diesen Tools aufgezeichnet und dann wiedergegeben werden, um eine Spitzenanzahl von Autoren und Autorinnen zu simulieren, die gleichzeitig ähnlichen Inhalt erstellen und Aktivierungen durchführen. Es wird empfohlen, das Tough Day-Tool zu verwenden, um Aktivitäten wie das Hochladen Tausender Assets oder das Aktivieren einer großen Anzahl von Seiten zu simulieren.

Für die Umgebungstypen, für die ein hohes Laden von Assets oder Erstellen von Seiten erforderlich ist, ist es unerlässlich, Tools wie Tough Day zu verwenden. Auf diese Weise wird sichergestellt, dass die Umgebung auch bei Spitzenbelastung effizient arbeitet. [WebDAV](/help/sites-administering/webdav-access.md) ist ein Tool, für das kein Scripting erforderlich ist und mit dem große Mengen an Assets geladen werden können.

#### MongoDB-spezifische Schritte {#mongodb-specific-steps}

Auf Systemen mit MongoDB-Backends stellt AEM mehrere [JMX](/help/sites-administering/jmx-console.md)-MBeans zur Verfügung, die bei Auslastungs- oder Leistungstests überwacht werden müssen:

* Die MBean **Konsolidierte Cache-Statistiken**. Sie können wie folgt direkt darauf zugreifen:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D6%2Cname%3D%22Consolidated+Cache+statistics%22%2Ctype%3D%22ConsolidatedCacheStats%22`

Für den Cache mit der Bezeichnung **Document-Diff** sollte die Trefferrate bei einem Wert von über `.90` liegen. Wenn die Trefferrate unter 90 % fällt, müssen Sie wahrscheinlich die Konfiguration `DocumentNodeStoreService` ändern. Der Produktsupport von Adobe kann Ihnen optimale Einstellungen für Ihre Umgebung empfehlen.

* Die Mbean **Oak-Repository-Statistiken**. Sie können wie folgt direkt darauf zugreifen:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D16%2Cname%3D%22Oak+Repository+Statistics%22%2Ctype%3D%22RepositoryStats%22`

Im Abschnitt **ObservationQueueMaxLength** wird die Anzahl der Ereignisse in der Oak-Beobachtungswarteschlange während der letzten Stunden, Minuten, Sekunden und Wochen angezeigt. Suchen Sie im Abschnitt „per hour“ nach der größten Anzahl von Ereignissen pro Stunde. Vergleichen Sie diese Zahl mit der Einstellung `oak.observation.queue-length`. Wenn die höchste für die Beobachtungswarteschlange angezeigte Anzahl die Einstellung `queue-length` übersteigt:

1. Erstellen Sie eine Datei mit dem Namen `com.adobe.granite.repository.impl.SlingRepositoryManager.cfg`, die den Parameter `oak.observation.queue‐length=50000` enthält.
1. Platzieren Sie sie im Ordner „/crx-­‐quickstart/install“.

>[!NOTE]
>Siehe [AEM 6.x | Tipps zur Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=de)

Die Standardeinstellung ist 10.000, aber für die meisten Bereitstellungen ist eine Anhebung auf 20.000 oder 50.000 erforderlich.

## Veröffentlichungsumgebung {#publish-environment}

### Durchführen von Tests {#performing-tests-1}

Der wichtigste Teil einer Bereitstellung, der Belastungstests unterzogen werden muss, ist die Veröffentlichungs- oder Dispatcher-Umgebung für Endbenutzerinnen und -benutzer.

Die Leistung der Website kann mithilfe automatisierter Test-Tools von Drittanbietern überprüft werden. Über diese Tools können Sie die Schritte aufzeichnen, die Benutzerinnen und Benutzer auf der Website durchführen, und viele dieser Sitzungen gleichzeitig ausführen, um die für eine Produktions-Website typische Auslastung zu simulieren.

Die meisten Produktions-Websites verfügen über Optimierungsfunktionen wie Dispatcher-Caching und ein Netzwerk für die Inhaltsbereitstellung. Stellen Sie beim Testen sicher, dass diese Optimierungen auch für die Testumgebung verfügbar sind. Überwachen Sie nicht nur die Reaktionszeiten der Endbenutzerinnen und -benutzer, sondern behalten Sie auch die Systemmetriken auf den Veröffentlichungs-Servern und Dispatchern im Auge, um sicherzustellen, dass das System nicht durch Hardware-Ressourcen eingeschränkt wird.

Auf einem System, das keine umfassende Personalisierung erfordert, sollte der Dispatcher die meisten Anforderungen zwischenspeichern. Daher sollte die Belastungskurve für die Publishing-Instanz relativ flach bleiben. Wenn ein hohes Maß an Personalisierung erforderlich ist, wird empfohlen, Technologien wie iFrames oder AJAX-Anforderungen für personalisierte Inhalte zu verwenden, um ein Maximum an Dispatcher-Caching zuzulassen.

Für grundlegende Tests kann Apache Bench verwendet werden, um die Antwortzeiten von Webservern zu messen und Lasten für das Messen von Dingen wie etwa Speicherverlusten zu erzeugen. Weitere Informationen liefert Ihnen das Beispiel in der [Dokumentation zur Überwachung](/help/sites-deploying/monitoring-and-maintaining.md#apache-bench).

## Fehlerbehebung von Leistungsproblemen {#troubleshooting-performance-issues}

Nach dem Ausführen von Leistungstests auf der Authoring-Instanz müssen alle festgestellten Probleme untersucht, diagnostiziert und behoben werden. Zur Analyse und Behandlung dieser Probleme können Sie verschiedene Tools und Verfahren anwenden:

* Sie können das [Protokoll zur Anfrageleistung](/help/sites-administering/operations-dashboard.md#request-performance) im Vorgangs-Dashboard einsehen. Mit diesem Tool können Sie langsame Seitenanfragen identifizieren
* Analysieren Sie langsame Abfragen mit dem [Tool „Abfrageleistung“](/help/sites-administering/operations-dashboard.md#query-performance).

* Prüfen Sie das Fehlerprotokoll auf Fehler oder Warnungen. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
* Überwachen Sie die Hardware-Ressourcen des Systems, z. B. Speicher- und CPU-Auslastung oder E/A-Vorgänge von Festplatten bzw. Netzwerk. Diese Ressourcen sind häufig die Ursachen für Leistungsengpässe.
* Optimieren Sie die Architektur der Seiten und ihre Adressierung, um die Verwendung von URL-Parametern zu minimieren, damit ein Höchstmaß an Zwischenspeicherung ermöglicht wird.
* Befolgen Sie die Dokumentationen [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) und [Tipps zur Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=de).

* Wenn beim Bearbeiten bestimmter Seiten oder Komponenten in Authoring-Instanzen Probleme auftreten, sehen Sie sich die fragliche Seite mithilfe des Entwicklermodus der Touch-optimierten Benutzeroberfläche an. Dadurch erhalten Sie eine Aufschlüsselung der einzelnen Inhaltsbereiche auf der Seite und ihrer Ladezeiten.
* Minimieren Sie alle JS- und CSS-Dateien auf der Site. Siehe diesen [Blogpost](https://blogs.adobe.com/foxes/enable-js-and-css-minification/).
* Entfernen Sie eingebettete CSS- und JS-Elemente aus den Komponenten. Sie sollten mit den clientseitigen Bibliotheken eingeschlossen und minimiert werden, um die Anzahl der Anforderungen zu minimieren, die zum Rendern der Seite erforderlich sind.
* Verwenden Sie Browser-Tools wie den Chrome-Tab „Netzwerk“, um die Server-Anfragen zu überprüfen und festzustellen, welche am längsten dauern.

Nach Identifizierung von Problembereichen kann der Anwendungs-Code im Hinblick auf Leistungsoptimierungen untersucht werden. Sollten AEM-Standardfunktionen nicht ordnungsgemäß verwendet werden können, wenden Sie sich an den Adobe-Support, um Unterstützung zu erhalten.
