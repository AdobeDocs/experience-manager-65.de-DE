---
title: Best Practices für Leistungstests
description: Erfahren Sie mehr über die allgemeinen Strategien und Methoden, die für Leistungstests verwendet werden, sowie über einige der Tools, die zur Unterstützung des Prozesses verfügbar sind.
uuid: ab8720d6-b864-4d00-9e07-2e1699cfe7db
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 669018a0-f6ef-42b2-9c6f-83d7dd5a7095
exl-id: fcac75e1-15c1-4a37-8d43-93c95267b903
source-git-commit: 18f843ed3ffb719d168b67826baaffd926ffd2dd
workflow-type: tm+mt
source-wordcount: '1831'
ht-degree: 16%

---

# Best Practices für Leistungstests{#best-practices-for-performance-testing}

## Einführung {#introduction}

Leistungstests sind ein wichtiger Bestandteil jeder AEM Implementierung. Je nach Kundenanforderungen können Leistungstests für Veröffentlichungsinstanzen, Autoreninstanzen oder beides durchgeführt werden.

In dieser Dokumentation werden die Gesamtstrategien und Methoden für die Durchführung von Leistungstests sowie einige der Tools beschrieben, die von Adobe zur Prozessunterstützung zur Verfügung gestellt werden. Lesen Sie abschließend eine Analyse der in AEM 6 verfügbaren Tools, um die Leistungsoptimierung zu unterstützen, sowohl aus der Sicht der Code-Analyse als auch der Systemkonfiguration.

### Simulieren der Realität {#simulating-reality}

Stellen Sie bei Leistungstests sicher, dass Sie eine Produktionsumgebung so nah wie möglich imitieren. Eine solche Aufgabe kann oft schwierig sein, doch muss unbedingt die Genauigkeit dieser Tests sichergestellt werden. Bei der Erstellung von Leistungstests ist Folgendes zu berücksichtigen:

* Produktionsähnliche Inhalte

Viele Leistungsmessungen in AEM, wie z. B. die Antwortzeit der Abfrage, können durch die Größe des Inhalts im System beeinflusst werden. Es ist wichtig sicherzustellen, dass die Testumgebung so nah wie möglich an einer Kopie der Produktionsdaten liegt.

* Produktionscode

Die AEM und Hotfixes, die in der Produktion bereitgestellt werden, sollten in der Testumgebung gleich sein. Es ist auch wichtig, die Version des Codes zu testen, der in der Produktion bereitgestellt wird.

* Produktionsähnliche Hardware- und Netzwerkkonfiguration

Die Tests sind ohne eine Umgebung ohne Bedeutung, die der Produktionsumgebung so ähnlich wie möglich ist. Idealerweise sollten die Hardwarespezifikationen, Netzwerkschnittstellen, Lastenausgleich und CDN mit der Produktion in der Testumgebung identisch sein.

* Produktionslast

Viele Leistungsprobleme treten erst auf, wenn das System stark ausgelastet ist. Gute Leistungstests sollten die Last simulieren, unter der sich die Produktionssysteme in ihrer Spitze befinden.

### Festlegen von Zielen {#setting-goals}

Bevor Sie mit Leistungstests beginnen, müssen Sie nicht funktionale Anforderungen festlegen, um die Lade- und Antwortzeiten anzugeben. Wenn Sie von einem vorhandenen System migrieren, stellen Sie sicher, dass die Antwortzeiten Ihren aktuellen Produktionswerten ähnlich sind. Für die Last ist es am besten, die aktuelle Spitzenlast zu verdoppeln. Dadurch wird sichergestellt, dass die Website auch weiterhin gut funktionieren kann, wenn sie wächst.

### Tools {#tools}

Auf dem Markt ist eine Vielzahl von Tools für Leistungstests erhältlich. Stellen Sie beim Ausführen eines Lastgenerators sicher, dass die Computer, die die Tests durchführen, über ausreichend Netzwerkbrandbreite verfügen. Andernfalls wird keine zusätzliche Belastung in der getesteten Umgebung erzeugt, sobald die Testmaschine die Grenzen ihrer Verbindung erreicht.

#### Testwerkzeuge {#testing-tools}

* Adobe **Tough Day** kann verwendet werden, um die Auslastung AEM Instanzen zu generieren und Leistungsdaten zu erfassen. Das AEM-Technikerteam der Adobe verwendet das Tool tatsächlich, um das AEM selbst zu laden. Die in Tough Day ausgeführten Skripte werden über Eigenschaftendateien und JMX-XML-Dateien konfiguriert. Weitere Informationen finden Sie unter [Tough Day-Dokumentation](/help/sites-developing/tough-day.md).

* AEM bietet vorkonfigurierte Tools, um problematische Abfragen, Anforderungen und Fehlermeldungen schnell anzuzeigen. Weitere Informationen finden Sie unter [Diagnosetools](/help/sites-administering/operations-dashboard.md#diagnosis-tools) Abschnitt der Dokumentation zum Vorgangs-Dashboard.
* Apache bietet ein Produkt mit dem Namen **JMeter** , die für Leistungs- und Belastungstests sowie für funktionelles Verhalten verwendet werden können. Es handelt sich um eine Open-Source-Software, die kostenlos verwendet werden kann, aber eine kleinere Funktion hat als Unternehmensprodukte und eine stärkere Lernkurve. JMeter finden Sie auf der Apache-Website unter [https://jmeter.apache.org/](https://jmeter.apache.org/)

* **Load Runner** ist ein Enterprise-Produkt für Auslastungstests. Eine kostenlose Evaluierungsversion ist verfügbar. Weitere Informationen finden Sie unter [https://www.microfocus.com/en-us/portfolio/performance-engineering/overview](https://www.microfocus.com/en-us/portfolio/performance-engineering/overview)

* Tools zum Laden von Websites, [Vercara](https://vercara.com/website-performance-management) kann auch verwendet werden.
* Beim Testen mobiler oder responsiver Websites muss ein separater Satz von Tools verwendet werden. Sie ermöglichen die Einschränkung der Netzwerkbandbreite und simulieren langsamere mobile Verbindungen wie 3G oder EDGE. Zu den gängigeren Tools gehören:

   * **[Network Link Conditioner](https://nshipster.com/network-link-conditioner/)** mit einer benutzerfreundlichen Oberfläche und einer relativ niedrigen Ebene im Netzwerk-Stack. Es sind OS X- und iOS-Versionen verfügbar.
   * [**Charles**](https://www.charlesproxy.com/), eine Web-Debugging-Proxy-Anwendung, die u. a. eine Netzwerkdrosselung ermöglicht. Versionen werden für Windows, OS X und Linux® bereitgestellt.

#### Optimierungswerkzeuge {#optimization-tools}

**Überwachung**

Die [Überwachung der Leistung](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance) -Dokumentation ist eine gute Ressource für Tools und Methoden, die zur Diagnose von Problemen und zur Bestimmung von Optimierungsbereichen verwendet werden können.

**Entwicklermodus in der Touch-Benutzeroberfläche**

Eine der neuen Funktionen der Touch-Benutzeroberfläche von AEM 6 ist der Entwicklermodus. So wie Autoren zwischen Bearbeitungs- und Vorschaumodi wechseln können, können Entwickler in der Autoren-Benutzeroberfläche in den Entwicklermodus wechseln. Auf diese Weise können Sie die Renderzeit für jede Komponente auf der Seite sehen und Stacktraces von Fehlern sehen. Weitere Informationen zum Entwicklermodus finden Sie in diesem [CQ Gems-Präsentation](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html?lang=en).

**Lesen der Anforderungsprotokolle mithilfe von rlog.jar**

Für eine eingehendere Analyse der Anforderungsprotokolle auf einem AEM-System können die von AEM erzeugten `request.log`-Dateien mit `rlog.jar` durchsucht und sortiert werden. Diese JAR-Datei ist Teil der AEM-Installation im Ordner `/crx-quickstart/opt/helpers`. Weitere Informationen zum rlog-Tool und zum Anforderungsprotokoll im Allgemeinen finden Sie in der [Überwachung und Wartung](/help/sites-deploying/monitoring-and-maintaining.md) Dokumentation.

**Tool &quot;Abfrage erläutern&quot;**

Die [Tool &quot;Abfrage erläutern&quot;](/help/sites-administering/operations-dashboard.md#explain-query) in ACS AEM Tools können verwendet werden, um die Indizes anzuzeigen, die beim Ausführen einer Abfrage verwendet werden. Dieses Tool ist nützlich, wenn langsame Abfragen optimiert werden.

**PageSpeed-Tools**

Die PageSpeed-Tools von Google bieten eine Site-Analyse zur Einhaltung der Best Practices für die Seitenleistung sowie ein Plug-in, das für zusätzliche Optimierungen zusammen mit dem Dispatcher auf einer Apache-Instanz installiert werden kann.
Siehe [PageSpeed Tools-Website](https://developers.google.com/speed).

## Autorenumgebung {#author-environment}

### Durchführen von Tests {#performing-tests}

Um Leistungstests in der Autorenumgebung durchzuführen, müssen Sie das Erlebnis der Produktionsautoren simulieren. Das heißt, die Autoreninstallationen müssen alle Komponenten, OSGi-Bundles, Benutzeroberflächenanpassungen, benutzerdefinierten Indizes und alle anderen Ergänzungen enthalten, die Sie für die Produktionsautorinstanzen eingerichtet haben.

Es gibt viele Automatisierungs-Frameworks, die für Leistungs- und Belastungstests entwickelt wurden. Benutzerdefinierte Skripte können in diesen Tools aufgezeichnet und dann wiedergegeben werden, um eine Spitzenanzahl von Autoren zu simulieren, die gleichzeitig ähnliche Inhaltserstellung und Aktivierungsaktivitäten durchführen. Es wird empfohlen, das Tough Day-Tool zu verwenden, um Aktivitäten wie das Hochladen Tausender Assets oder das Aktivieren einer großen Anzahl von Seiten zu simulieren.

Für die Umgebungstypen, für die ein hohes Laden von Assets oder Erstellen von Seiten erforderlich ist, ist es unerlässlich, Tools wie Tough Day zu verwenden. Dadurch wird sichergestellt, dass die Umgebung unter Spitzenlast effizient arbeitet. [WebDAV](/help/sites-administering/webdav-access.md) ist ein Tool, für das kein Scripting erforderlich ist und mit dem große Mengen an Assets geladen werden können.

#### MongoDB-spezifische Schritte {#mongodb-specific-steps}

Auf Systemen mit MongoDB-Backends stellt AEM mehrere [JMX](/help/sites-administering/jmx-console.md) MBeans, die bei Belastungs- oder Leistungstests überwacht werden müssen:

* Die **Konsolidierte Cache-Statistiken** MBean. Sie können wie folgt direkt darauf zugreifen:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D6%2Cname%3D%22Consolidated+Cache+statistics%22%2Ctype%3D%22ConsolidatedCacheStats%22`

Für den Cache mit der Bezeichnung **Document-Diff** sollte die Trefferrate bei einem Wert von über `.90` liegen. Wenn die Trefferrate unter 90 % fällt, müssen Sie wahrscheinlich Ihre `DocumentNodeStoreService` Konfiguration. Der Produktsupport von Adobe kann optimale Einstellungen für Ihre Umgebung empfehlen.

* Die **Oak-Repository-Statistiken** Mbean. Sie können wie folgt direkt darauf zugreifen:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D16%2Cname%3D%22Oak+Repository+Statistics%22%2Ctype%3D%22RepositoryStats%22`

Die **ObservationQueueMaxLength** zeigt die Anzahl der Ereignisse in der Beobachtungswarteschlange von Oak in den letzten Stunden, Minuten, Sekunden und Wochen an. Die größte Anzahl von Ereignissen finden Sie im Abschnitt &quot;pro Stunde&quot;. Vergleichen Sie diese Zahl mit der `oak.observation.queue-length` -Einstellung. Wenn die höchste für die Beobachtungswarteschlange angezeigte Anzahl die Einstellung `queue-length` übersteigt:

1. Erstellen Sie eine Datei mit dem Namen `com.adobe.granite.repository.impl.SlingRepositoryManager.cfg`, die den Parameter `oak.observation.queue‐length=50000` enthält.
1. Platzieren Sie sie im Ordner „/crx-­‐quickstart/install“.

>[!NOTE]
>Siehe [AEM 6.x | Tipps zur Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=en)

Die Standardeinstellung ist 10.000, aber die meisten Implementierungen müssen sie auf 20.000 oder 50.000 erhöhen.

## Veröffentlichungsumgebung {#publish-environment}

### Durchführen von Tests {#performing-tests-1}

Der wichtigste Teil einer Bereitstellung, der Belastungstests unterzogen werden muss, ist der Endbenutzer, der sich der Veröffentlichungs- oder Dispatcher-Umgebung gegenübersieht.

Automatisierte Testwerkzeuge von Drittanbietern können zum Testen der Leistung der Website verwendet werden. Mit diesen Tools können Sie die Schritte aufzeichnen, die Benutzer auf der Site ausführen, und viele dieser Sitzungen gleichzeitig ausführen, um die für eine Produktionswebsite typische Belastung zu simulieren.

Die meisten Produktions-Websites verfügen über Optimierungen wie Dispatcher-Caching und ein Inhaltsbereitstellungsnetzwerk. Stellen Sie beim Testen sicher, dass diese Optimierungen auch für die Testumgebung verfügbar sind. Überwachen Sie nicht nur die Reaktionszeiten für die Endbenutzer, sondern auch die Systemmetriken auf den Veröffentlichungs-Servern und Dispatchern, um sicherzustellen, dass das System nicht durch Hardware-Ressourcen eingeschränkt wird.

Auf einem System, das keine umfassende Personalisierung erfordert, sollte der Dispatcher die meisten Anforderungen zwischenspeichern. Daher sollte die Belastung der Veröffentlichungsinstanz relativ flach bleiben. Wenn ein hohes Maß an Personalisierung erforderlich ist, wird empfohlen, Technologien wie iFrames oder AJAX Anforderungen für personalisierte Inhalte zu verwenden, um so viel Dispatcher-Caching wie möglich zu ermöglichen.

Für grundlegende Tests kann Apache Bench verwendet werden, um die Antwortzeiten von Webservern zu messen und die Last für die Messung von Dingen wie Speicherlecks zu erzeugen. Siehe Beispiel im [Überwachungsdokumentation](/help/sites-deploying/monitoring-and-maintaining.md#apache-bench).

## Beheben von Leistungsproblemen {#troubleshooting-performance-issues}

Nach dem Ausführen von Leistungstests auf der Autoreninstanz müssen alle Probleme untersucht, diagnostiziert und behoben werden. Sie können bei der Durchführung von Analysen und der Problembehebung verschiedene Tools und Techniken verwenden:

* Sie können die [Protokoll zur Anforderungsleistung](/help/sites-administering/operations-dashboard.md#request-performance) im Vorgangs-Dashboard. Mit diesem Tool können Sie langsame Seitenanforderungen identifizieren
* Analysieren Sie langsame Abfragen mit dem [Tool „Abfrageleistung“](/help/sites-administering/operations-dashboard.md#query-performance).

* Prüfen Sie das Fehlerprotokoll auf Fehler oder Warnungen. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
* Überwachen Sie die Hardware-Ressourcen des Systems, z. B. Speicher- und CPU-Auslastung, Datenträger-E/A oder Netzwerk-I/O. Diese Ressourcen sind häufig die Ursachen für Leistungsengpässe.
* Optimieren Sie die Architektur der Seiten und deren Adressierung, um die Verwendung von URL-Parametern zu minimieren und so viel Zwischenspeicherung wie möglich zu ermöglichen.
* Befolgen Sie die [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) und [Tipps zur Leistungsoptimierung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=en) Dokumentation.

* Wenn beim Bearbeiten bestimmter Seiten oder Komponenten in Autoreninstanzen Probleme auftreten, verwenden Sie den Entwicklermodus der Touch-optimierten Benutzeroberfläche, um die betroffene Seite zu überprüfen. Dadurch erhalten Sie eine Aufschlüsselung der einzelnen Inhaltsbereiche auf der Seite und ihrer Ladezeit.
* Minimieren Sie alle JS- und CSS-Dateien auf der Site. Siehe dies [Blogpost](https://blogs.adobe.com/foxes/enable-js-and-css-minification/).
* Entfernen Sie eingebettetes CSS und JS aus den Komponenten. Diese sollten in den Client-seitigen Bibliotheken enthalten und minimiert sein, um die Anzahl der zum Rendern der Seite benötigten Anforderungen zu minimieren..
* Verwenden Sie Browser-Tools wie die Registerkarte &quot;Netzwerk&quot;von Chrome, um die Serveranforderungen zu überprüfen und festzustellen, welche am längsten dauern.

Nach Identifizierung von Problembereichen kann der Anwendungs-Code im Hinblick auf Leistungsoptimierungen untersucht werden. Sollten AEM-Standardfunktionen nicht ordnungsgemäß verwendet werden können, wenden Sie sich an den Adobe-Support, um Unterstützung zu erhalten.
