---
title: Best Practices für Leistungstests
seo-title: Best Practices for Performance Testing
description: In diesem Artikel werden die allgemeinen Strategien und Methoden für Leistungstests sowie einige der verfügbaren Tools zur Unterstützung des Prozesses beschrieben.
seo-description: This article outlines the overall strategies and methodologies used for performance testing as well as some of the tools that are available to assist in the process.
uuid: ab8720d6-b864-4d00-9e07-2e1699cfe7db
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 669018a0-f6ef-42b2-9c6f-83d7dd5a7095
exl-id: fcac75e1-15c1-4a37-8d43-93c95267b903
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '1898'
ht-degree: 26%

---

# Best Practices für Leistungstests{#best-practices-for-performance-testing}

## Einführung {#introduction}

Leistungstests sind ein wichtiger Bestandteil jeder AEM Implementierung. Je nach Kundenanforderungen können Leistungstests für Veröffentlichungsinstanzen, Autoreninstanzen oder beides durchgeführt werden.

In dieser Dokumentation werden die allgemeinen Strategien und Methoden für die Durchführung von Leistungstests sowie einige der Tools beschrieben, die von Adobe zur Prozessunterstützung zur Verfügung gestellt werden. Schließlich werden wir einige der in AEM 6 verfügbaren Tools analysieren, um die Leistungsoptimierung zu unterstützen, sowohl aus der Sicht der Code-Analyse als auch der Systemkonfiguration.

### Simulieren der Realität {#simulating-reality}

Wichtig bei der Durchführung von Leistungstests ist, sicherzustellen, dass Sie eine Produktionsumgebung so gut wie möglich nachahmen. Dies kann zwar oft schwierig sein, es ist jedoch unerlässlich, die Genauigkeit dieser Tests sicherzustellen. Bei der Erstellung von Leistungstests ist Folgendes zu berücksichtigen:

* Produktionsähnliche Inhalte

Viele Leistungsmessungen in AEM, wie z. B. die Antwortzeit der Abfrage, können durch die Größe des Inhalts im System beeinflusst werden. Es ist wichtig sicherzustellen, dass die Testumgebung so nah wie möglich an einer Kopie der Produktionsdaten liegt.

* Produktionscode

Die AEM und Hotfixes, die in der Produktion bereitgestellt werden, sollten in der Testumgebung gleich sein. Es ist auch wichtig, die Version des Codes zu testen, der in der Produktion bereitgestellt wird.

* Produktionsähnliche Hardware- und Netzwerkkonfiguration

Die Tests sind ohne eine Umgebung ohne Bedeutung, die der Produktionsumgebung so ähnlich wie möglich ist. Idealerweise sollten die Hardwarespezifikationen, Netzwerkschnittstellen, Lastverteiler und CDN mit der Produktion in der Testumgebung identisch sein.

* Produktionslast

Viele Leistungsprobleme treten erst auf, wenn das System stark ausgelastet ist. Gute Leistungstests sollten die Last simulieren, unter der die Produktionssysteme zu ihrem Spitzenwert liegen.

### Festlegen von Zielen {#setting-goals}

Bevor Sie mit Leistungstests beginnen, müssen Sie nicht funktionale Anforderungen festlegen, um die Lade- und Antwortzeiten anzugeben. Wenn Sie von einem vorhandenen System migrieren, stellen Sie sicher, dass die Antwortzeit Ihren aktuellen Produktionswerten ähnlich ist. Für die Last ist es am besten, die aktuelle Spitzenlast zu verdoppeln. Dadurch wird sichergestellt, dass die Website auch weiterhin gut funktionieren kann, wenn sie wächst.

### Tools {#tools}

Auf dem Markt ist eine Vielzahl von Tools für Leistungstests erhältlich. Stellen Sie beim Ausführen eines Lastgenerators sicher, dass die Computer, die die Tests durchführen, über ausreichend Netzwerkbrandbreite verfügen. Andernfalls wird keine zusätzliche Belastung in der getesteten Umgebung erzeugt, sobald die Testmaschine die Grenzen ihrer Verbindung erreicht.

#### Testwerkzeuge {#testing-tools}

* Adobe **Tough Day** kann verwendet werden, um die Auslastung AEM Instanzen zu generieren und Leistungsdaten zu erfassen. Das AEM-Technikerteam der Adobe verwendet das Tool tatsächlich, um das AEM selbst zu laden. Die in Tough Day ausgeführten Skripte werden über Eigenschaftendateien und JMX-XML-Dateien konfiguriert. Weitere Informationen finden Sie unter [Tough Day-Dokumentation](/help/sites-developing/tough-day.md).

* AEM bietet vorkonfigurierte Tools, um problematische Abfragen, Anfragen und Fehlermeldungen schnell anzuzeigen. Weitere Informationen finden Sie unter [Diagnosetools](/help/sites-administering/operations-dashboard.md#diagnosis-tools) Abschnitt der Dokumentation zum Vorgangs-Dashboard.
* Apache bietet ein Produkt mit dem Namen **JMeter** die für Leistungs- und Belastungstests sowie für funktionelles Verhalten verwendet werden können. Es handelt sich um Open-Source-Software und ist kostenlos zu verwenden, hat aber einen kleineren Funktionsumfang als Unternehmensprodukte und eine stärkere Lernkurve. JMeter finden Sie auf der Apache-Website unter [https://jmeter.apache.org/](https://jmeter.apache.org/)

* **Load Runner** ist ein Enterprise-Produkt für Auslastungstests. Eine kostenlose Evaluierungsversion ist verfügbar. Weitere Informationen finden Sie unter [https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview](https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview).

* Cloud-basierte Tools zum Testen von Lasten, wie [Neustar](https://www.neustar.biz/services/web-performance/load-testing) kann auch verwendet werden.
* Beim Testen mobiler oder responsiver Websites muss ein separater Satz von Tools verwendet werden. Sie ermöglichen die Einschränkung der Netzwerkbandbreite und simulieren langsamere mobile Verbindungen wie 3G oder EDGE. Zu den gängigsten Tools gehören:

   * **[Network Link Conditioner](https://nshipster.com/network-link-conditioner/)** mit einer benutzerfreundlichen Oberfläche und einer relativ niedrigen Ebene im Netzwerk-Stack. Es sind OS X- und iOS-Versionen verfügbar.
   * [**Charles**](https://www.charlesproxy.com/), eine Web-Debugging-Proxy-Anwendung, die u. a. eine Netzwerkdrosselung ermöglicht. Es sind Windows-, OS X- und Linux-Versionen verfügbar.

#### Optimierungswerkzeuge {#optimization-tools}

**Überwachung**

Die [Überwachung der Leistung](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance) -Dokumentation ist eine gute Ressource für Tools und Methoden, die zur Diagnose von Problemen und zur Bestimmung von Optimierungsbereichen verwendet werden können.

**Entwicklermodus in der Touch-Benutzeroberfläche**

Eine der neuen Funktionen der Touch-Benutzeroberfläche von AEM 6 ist der Entwicklermodus. So wie Autoren zwischen Bearbeitungs- und Vorschaumodi wechseln können, können Entwickler in der Autoren-Benutzeroberfläche in den Entwicklermodus wechseln, um die Renderzeit für jede Komponente auf der Seite anzuzeigen und Stacktraces von Fehlern zu sehen. Weitere Informationen zum Entwicklermodus finden Sie in diesem [CQ Gems-Präsentation](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html?lang=en).

**Lesen der Anforderungsprotokolle mithilfe von rlog.jar**

Für eine eingehendere Analyse der Anforderungsprotokolle auf einem AEM-System können die von AEM erzeugten `request.log`-Dateien mit `rlog.jar` durchsucht und sortiert werden. Diese JAR-Datei ist Teil der AEM-Installation im Ordner `/crx-quickstart/opt/helpers`. Weitere Informationen zum rlog-Tool und zum Anforderungsprotokoll im Allgemeinen finden Sie in der [Überwachung und Wartung](/help/sites-deploying/monitoring-and-maintaining.md) Dokumentation.

**Tool &quot;Abfrage erläutern&quot;**

Die [Tool &quot;Abfrage erläutern&quot;](/help/sites-administering/operations-dashboard.md#explain-query) in ACS AEM Tools können verwendet werden, um die Indizes anzuzeigen, die beim Ausführen einer Abfrage verwendet werden. Dies kann sehr nützlich sein, wenn langsame Abfragen optimiert werden.

**PageSpeed-Tools**

Die PageSpeed-Tools von Google bieten eine Site-Analyse zur Einhaltung der Best Practices für die Seitenleistung sowie ein Plug-in, das zusammen mit dem Dispatcher auf einer Apache-Instanz installiert werden kann, um zusätzliche Optimierungen zu ermöglichen. Weitere Informationen finden Sie auf der [PageSpeed-Tools-Website](https://developers.google.com/speed/pagespeed/).

## Autorenumgebung {#author-environment}

### Durchführen von Tests {#performing-tests}

Um Leistungstests für die Autorenumgebung durchzuführen, müssen Sie das Erlebnis der Produktionsautoren simulieren. Die Autoreninstallationen müssen also alle Komponenten, OSGi-Bundles, UI-Anpassungen, benutzerdefinierten Indizes und sonstigen Ergänzungen für die produktionsbezogenen Autoreninstanzen umfassen.

Es gibt viele Automatisierungs-Frameworks, die für Leistungs- und Belastungstests entwickelt wurden. Benutzerdefinierte Skripte können in diesen Tools aufgezeichnet und dann wiedergegeben werden, um eine Spitzenanzahl von Autoren zu simulieren, die gleichzeitig ähnliche Inhaltserstellung und Aktivierungsaktivitäten durchführen. Es wird empfohlen, das Tough Day-Tool zu verwenden, um Aktivitäten wie das Hochladen Tausender Assets oder das Aktivieren einer großen Anzahl von Seiten zu simulieren.

Für Umgebungen mit hohen Anforderungen an Asset-Ladevorgänge oder Seitenbearbeitung ist es unerlässlich, Tools wie Tough Day zu verwenden, um sicherzustellen, dass die Umgebung unter Spitzenlast effizient arbeitet. [WebDAV](/help/sites-administering/webdav-access.md) ist ein Tool, für das kein Scripting erforderlich ist und mit dem große Mengen an Assets geladen werden können.

#### MongoDB-spezifische Schritte {#mongodb-specific-steps}

Auf Systemen mit MongoDB-Backends stellt AEM mehrere [JMX](/help/sites-administering/jmx-console.md) MBeans, die bei Belastungs- oder Leistungstests überwacht werden müssen:

* Die **Konsolidierte Cache-Statistiken** MBean. Sie können wie folgt direkt darauf zugreifen:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D6%2Cname%3D%22Consolidated+Cache+statistics%22%2Ctype%3D%22ConsolidatedCacheStats%22`

Für den Cache mit der Bezeichnung **Document-Diff** sollte die Trefferrate bei einem Wert von über `.90` liegen. Wenn die Trefferrate unter 90 % fällt, müssen Sie wahrscheinlich die `DocumentNodeStoreService`-Konfiguration ändern. Der Produktsupport von Adobe kann optimale Einstellungen für Ihre Umgebung empfehlen.

* Die **Oak-Repository-Statistiken** Mbean. Sie können wie folgt direkt darauf zugreifen:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D16%2Cname%3D%22Oak+Repository+Statistics%22%2Ctype%3D%22RepositoryStats%22`

Die **ObservationQueueMaxLength** zeigt die Anzahl der Ereignisse in der Beobachtungswarteschlange von Oak in den letzten Stunden, Minuten, Sekunden und Wochen an. Die größte Anzahl von Ereignissen finden Sie im Abschnitt &quot;pro Stunde&quot;. Diese Zahl muss mit der Einstellung `oak.observation.queue-length` verglichen werden. Wenn die höchste für die Beobachtungswarteschlange angezeigte Anzahl die Einstellung `queue-length` übersteigt:

1. Erstellen Sie eine Datei mit dem Namen `com.adobe.granite.repository.impl.SlingRepositoryManager.cfg`, die den Parameter `oak.observation.queue‐length=50000` enthält.
1. Platzieren Sie sie im Ordner „/crx-­‐quickstart/install“.

>[!NOTE]
>Siehe auch den KB-Artikel zu [AEM 6.x | Tipps zur Leistungsoptimierung](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html)

Die Standardeinstellung ist 10.000, aber für die meisten Bereitstellungen ist normalerweise eine Anhebung auf 20.000 oder 50.000 erforderlich.

## Veröffentlichungsumgebung {#publish-environment}

### Durchführen von Tests {#performing-tests-1}

Der wichtigste Teil einer Bereitstellung, der Belastungstests unterzogen werden muss, ist der Endbenutzer, der sich der Veröffentlichungs- oder Dispatcher-Umgebung gegenübersieht.

Automatisierte Testwerkzeuge von Drittanbietern können zum Testen der Leistung der Website verwendet werden. Über diese Tools können Sie die Schritte aufzeichnen, die Benutzer auf der Website durchführen, und viele dieser Sitzungen gleichzeitig ausführen, um die für eine Produktionswebsite typische Last zu simulieren.

Die meisten Produktions-Websites verfügen über Optimierungen wie Dispatcher-Caching und ein Inhaltsbereitstellungsnetzwerk. Beim Testen müssen Sie sicherstellen, dass diese Optimierungen auch für die Testumgebung verfügbar sind. Zusätzlich zur Überwachung der Antwortzeiten für die Endbenutzer müssen Sie auch die Systemmetriken auf den Veröffentlichungs-Servern und Dispatchern überwachen, um sicherzustellen, dass das System nicht durch Hardware-Ressourcen eingeschränkt wird.

Auf einem System, das keine umfassende Personalisierung erfordert, sollte der Dispatcher die meisten Anforderungen zwischenspeichern. Daher sollte die Belastung der Veröffentlichungsinstanz relativ flach bleiben. Wenn ein hohes Maß an Personalisierung erforderlich ist, wird empfohlen, Technologien wie iFrames oder AJAX Anforderungen für den personalisierten Inhalt zu verwenden, um so viel Dispatcher-Caching wie möglich zu ermöglichen.

Für grundlegende Tests kann Apache Bench verwendet werden, um die Antwortzeiten von Webservern zu messen und die Last für die Messung von Dingen wie Speicherlecks zu erzeugen. Weitere Informationen finden Sie im Beispiel im [Überwachungsdokumentation](/help/sites-deploying/monitoring-and-maintaining.md#apache-bench).

## Beheben von Leistungsproblemen {#troubleshooting-performance-issues}

Nach dem Ausführen von Leistungstests auf der Autoreninstanz müssen alle Probleme untersucht, diagnostiziert und behoben werden. Sie können bei der Durchführung von Analysen und der Problembehebung verschiedene Tools und Techniken verwenden:

* Sie können die [Protokoll zur Anforderungsleistung](/help/sites-administering/operations-dashboard.md#request-performance) im Vorgangs-Dashboard. Mit diesem Tool können Sie langsame Seitenanforderungen identifizieren
* Analysieren Sie langsame Abfragen mit dem [Tool „Abfrageleistung“](/help/sites-administering/operations-dashboard.md#query-performance).

* Achten Sie auf die Fehlermeldung auf Fehler oder Warnungen. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md)
* Überwachen Sie die Hardware-Ressourcen des Systems, z. B. Speicher- und CPU-Auslastung, Datenträger-E/A oder Netzwerk-I/O. Diese Ressourcen sind häufig die Ursachen für Leistungsengpässe
* Optimieren Sie die Architektur der Seiten und deren Adressierung, um die Verwendung von URL-Parametern zu minimieren und so viel Zwischenspeicherung wie möglich zu ermöglichen.
* Befolgen Sie die [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) und [Tipps zur Leistungsoptimierung](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html) Dokumentation

* Wenn beim Bearbeiten bestimmter Seiten oder Komponenten in Autoreninstanzen Probleme auftreten, verwenden Sie den Entwicklermodus der Touch-optimierten Benutzeroberfläche, um die betroffene Seite zu überprüfen. Dadurch erhalten Sie eine Aufschlüsselung der einzelnen Inhaltsbereiche auf der Seite sowie ihrer Ladezeit.
* Minimieren Sie alle JS- und CSS-Dateien auf der Site. Weitere Informationen hierzu finden Sie in diesem [Blogpost](https://blogs.adobe.com/foxes/enable-js-and-css-minification/).
* Entfernen Sie eingebettetes CSS und JS aus den Komponenten. Diese sollten in den Client-seitigen Bibliotheken enthalten und minimiert sein, um die Anzahl der zum Rendern der Seite benötigten Anforderungen zu minimieren.
* Verwenden Sie Browser-Tools wie die Registerkarte &quot;Netzwerk&quot;von Chrome, um die Server-Anforderungen zu untersuchen und zu sehen, welche die längsten benötigen.

Nach Identifizierung von Problembereichen kann der Anwendungs-Code im Hinblick auf Leistungsoptimierungen untersucht werden. Sollten AEM-Standardfunktionen nicht ordnungsgemäß verwendet werden können, wenden Sie sich an den Adobe-Support, um Unterstützung zu erhalten.
