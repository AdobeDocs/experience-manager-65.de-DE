---
title: Best Practices für Leistungstests
seo-title: Best Practices for Performance Testing
description: In diesem Artikel werden Gesamtstrategien und Methoden für Leistungstests sowie verschiedene hierfür verfügbare Tools beschrieben.
seo-description: This article outlines the overall strategies and methodologies used for performance testing as well as some of the tools that are available to assist in the process.
uuid: ab8720d6-b864-4d00-9e07-2e1699cfe7db
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 669018a0-f6ef-42b2-9c6f-83d7dd5a7095
exl-id: fcac75e1-15c1-4a37-8d43-93c95267b903
source-git-commit: b6de561422bc3533eef153b13d2c65b4cb7e0387
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 92%

---

# Best Practices für Leistungstests{#best-practices-for-performance-testing}

## Einführung {#introduction}

Leistungstests stellen einen wichtigen Teil von AEM-Bereitstellungen dar. Je nach Kundenanforderungen können Leistungstests in Veröffentlichungsinstanzen und/oder Autoreninstanzen durchgeführt werden.

In diesem Dokument werden Gesamtstrategien und Methoden zum Durchführen von Leistungstests sowie verschiedene Tools beschrieben, die von Adobe zur Unterstützung dieses Vorgangs bereitgestellt werden. Schließlich analysieren wir einige der Tools, die in AEM 6 zur Leistungsoptimierung verfügbar sind, und zwar sowohl im Hinblick auf eine Codeanalyse als auch in Bezug auf die Systemkonfiguration.

### Simulieren der Realität {#simulating-reality}

Am wichtigsten bei Leistungstests: Sie müssen darauf achten, Ihre Produktionsumgebung so genau wie möglich nachzuahmen. Auch wenn dies häufig schwierig ist, ist dies unumgänglich, um die Genauigkeit dieser Tests sicherzustellen. Beim Konzipieren von Leistungstests müssen die folgenden Punkte berücksichtig werden:

* Produktionsähnlicher Inhalt

Viele Leistungsmessungen in AEM, etwa der Antwortzeiten von Abfragen, können durch den Umfang des auf dem System vorhandenen Inhalts beeinflusst werden. Es ist wichtig sicherzustellen, dass die Testumgebung über eine möglichst genaue Kopie der Produktionsdaten verfügt.

* Produktionscode

In der Produktions- und Testumgebung sollten die gleichen AEM-Versionen und -Hotfixes bereitgestellt sein. Die Tests müssen zudem mit der Codeversion der Produktionsumgebung erfolgen.

* Produktionsähnliche Hardware- und Netzwerkkonfiguration

Die Tests sind ohne eine Umgebung, die möglichst genau den Produktionsbedingungen entspricht, bedeutungslos. Im Idealfall sollten Hardwarespezifikationen, Netzwerkschnittstellen, Lastenausgleichsmodule und CDN in der Produktions- und Testumgebung identisch sein.

* Produktionsauslastung

Viele Leistungsprobleme treten erst dann zum Vorschein, wenn das System eine hohe Auslastung aufweist. Gute Leistungstests sollten die Auslastung der Produktionssysteme zu Stoßzeiten simulieren.

### Festlegen von Zielen {#setting-goals}

Vor Leistungstests müssen nicht funktionsbezogene Anforderungen zur Angabe der Last und Antwortzeiten festgelegt werden. Achten Sie beim Migrieren von einem vorhandenen System darauf, dass Antwortzeiten mit denen Ihrer aktuellen Produktionswerte vergleichbar sind. Was die Auslastung angeht, sollte am besten die Spitzenlast verdoppelt werden. Auf diese Weise wird sichergestellt, dass die Website auch bei Wachstum weiterhin leistungsfähig ist.

### Tools {#tools}

Auf dem Markt ist eine Vielzahl von Tools für Leistungstests erhältlich. Stellen Sie beim Ausführen eines Lastgenerators sicher, dass die Computer, die die Tests durchführen, über ausreichend Netzwerkbrandbreite verfügen. Andernfalls wird, sobald der Testrechner an seine Verbindungsgrenzen stößt, keine zusätzliche Last in der getesteten Umgebung erzeugt.

#### Testtools {#testing-tools}

* Mit dem **Tough Day**-Tool von Adobe können Lasten auf AEM-Instanzen erzeugt und Leistungsdaten erfasst werden. Das Entwicklungsteam von Adobe setzt dieses Tool für Auslastungstests beim eigentlichen AEM-Produkt ein. Die in Tough Day ausgeführten Skripts werden über Eigenschaftendateien und JMX-XML-Dateien konfiguriert. Weitere Informationen finden Sie in der [Tough Day-Dokumentation](/help/sites-developing/tough-day.md).

* AEM stellt sofort einsatzfähige Tools bereit, um problematische Abfragen, Anforderungen und Fehlermeldungen schnell erkennen zu können. Weitere Informationen finden Sie im Abschnitt [Diagnose-Tools](/help/sites-administering/operations-dashboard.md#diagnosis-tools) des Dokuments zu Vorgangs-Dashboards.
* Apache bietet ein Produkt namens **JMeter** an, das Leistungs- und Auslastungstests sowie eine Überprüfung des Funktionsverhaltens ermöglicht. Es handelt sich um kostenlose Open-Source-Software, die im Vergleich zu Enterprise-Produkten zwar einen geringeren Funktionsumfang hat, dafür aber eine steilere Lernkurve. JMeter finden Sie auf der Apache-Website unter [https://jmeter.apache.org/](https://jmeter.apache.org/)

* **Load Runner** ist ein Produkt für Belastungstests auf Unternehmensniveau. Eine kostenlose Testversion ist verfügbar. Weitere Informationen finden Sie unter [https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview](https://www.microfocus.com/en-us/products/loadrunner-load-testing/overview)

* Cloudbasierte Tools für Auslastungstests wie [Neustar](https://www.neustar.biz/services/web-performance/load-testing) können ebenfalls verwendet werden.
* Zum Testen von mobilen Websites oder responsiven Webdesigns sind andere Tools erforderlich. Diese drosseln die Netzwerkbrandbreite, um langsamere mobile Verbindungen wie 3G oder EDGE zu simulieren. Zu den gängigsten Tools gehören:

   * **[Network Link Conditioner](https://nshipster.com/network-link-conditioner/)** mit einer benutzerfreundlichen Oberfläche und einer relativ niedrigen Ebene im Netzwerk-Stack. Es sind OS X- und iOS-Versionen verfügbar.
   * [**Charles**](https://www.charlesproxy.com/), eine Webdebugging-Proxyanwendung, die u. a. eine Netzwerkdrosselung ermöglicht. Es sind Windows-, OS X- und Linux-Versionen verfügbar.

#### Optimierungstools {#optimization-tools}

**Überwachung**

Das Dokument [Überwachen der Leistung](/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance) liefert zahlreiche Informationen zu Tools und Methoden für die Diagnose von Problemen und Erkennung von Optimierungsbereichen.

**Entwicklermodus in der Touch-Benutzeroberfläche**

Eine der neuen Funktionen in der Touch-Benutzeroberfläche von AEM 6 ist der Entwicklermodus. So wie Autoren zwischen Bearbeitungs- und Vorschaumodi wechseln können, können Entwickler den Entwicklermodus in der Autor-Benutzeroberfläche aufrufen, um die Renderzeit für jede Komponente auf der Seite sowie Stapelnachverfolgungen von Fehlern anzuzeigen. Weitere Informationen zum Entwicklermodus finden Sie in dieser [CQ Gems-Präsentation](https://docs.adobe.com/content/ddc/en/gems/aem-6-0-developer-mode.html).

**Lesen von Anforderungsprotokollen mit rlog.jar**

Für eine eingehendere Analyse der Anforderungsprotokolle auf einem AEM-System können die von AEM erzeugten `rlog.jar`-Dateien mit `request.log` durchsucht und sortiert werden. Diese JAR-Datei ist mit einer AEM Installation im `/crx-quickstart/opt/helpers` Ordner. Weitere Informationen zum rlog-Tool und Anforderungsprotokoll im Allgemeinen finden Sie im Dokument [Überwachen und Verwalten](/help/sites-deploying/monitoring-and-maintaining.md).

**Tool „Abfrage erläutern“**

Mit dem [Tool „Abfrage erläutern“](/help/sites-administering/operations-dashboard.md#explain-query) in ACS AEM-Tools können Sie die beim Ausführen einer Abfrage verwendeten Indizes anzeigen. Dies kann sehr nützlich bei der Optimierung langsamer Abfragen sein.

**PageSpeed-Tools**

Die PageSpeed-Tools von Google bieten Website-Analysen zur Einhaltung der Best Practices in Bezug auf die seitenbezogene Leistung sowie ein Plug-in, das zur weiteren Optimierung neben dem Dispatcher in einer Apache-Instanz installiert werden kann. Weitere Informationen finden Sie auf der [PageSpeed-Tools-Website](https://developers.google.com/speed/pagespeed/).

## Autorenumgebung {#author-environment}

### Durchführen von Tests {#performing-tests}

Um Leistungstests für die Autorenumgebung durchzuführen, müssen Sie das Erlebnis der Produktionsautoren simulieren. Die Autorinstallationen müssen also sämtliche Komponenten, OSGi-Bundles, UI-Anpassungen, benutzerdefinierten Indizes und sonstigen Ergänzungen für die produktionsbezogenen Autoreninstanzen umfassen.

Es gibt eine Vielzahl von Automatisierungsframeworks, die auf Leistungs- und Auslastungstests ausgelegt sind. Benutzerdefinierte Skripts können in diesen Tools aufgezeichnet und dann wiedergegeben werden, um eine Höchstanzahl von Autoren zu simulieren, die gleichzeitig ähnlichen Inhalt erstellen und Aktivierungen durchführen. Sie sollten auf das Tough Day-Tool zum Simulieren von Aktivitäten wie Hochladen Tausender von Assets oder Aktivieren einer großen Anzahl von Seiten zurückgreifen.

In Umgebungen, in denen sehr viele Assets geladen bzw. viele Seiten erstellt werden müssen, sind Tools wie Tough Day unverzichtbar, um unter Spitzenlast einen effizienten Betrieb der Umgebung sicherzustellen. [WebDAV](/help/sites-administering/webdav-access.md) ist ein Tool, für das kein Scripting erforderlich ist und mit dem große Mengen an Assets geladen werden können.

#### MongoDB-spezifische Schritte {#mongodb-specific-steps}

Auf Systemen mit MongoDB-Backends stellt AEM mehrere [JMX](/help/sites-administering/jmx-console.md)-MBeans zur Verfügung, die bei Auslastungs- oder Leistungstests überwacht werden müssen:

* MBean **Consolidated Cache Statistics**. Sie können wie folgt direkt darauf zugreifen:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D6%2Cname%3D%22Consolidated+Cache+statistics%22%2Ctype%3D%22ConsolidatedCacheStats%22`

Für den Cache mit dem Namen **Document-Diff**, sollte die Trefferrate vorüber sein. `.90`. Wenn die Trefferrate unter 90 % fällt, müssen Sie wahrscheinlich die `DocumentNodeStoreService`-Konfiguration ändern. Der Produktsupport von Adobe kann Ihnen optimale Einstellungen für Ihre Umgebung empfehlen.

* MBean **Oak Repository Statistics**. Sie können wie folgt direkt darauf zugreifen:

`https://server:port/system/console/jmx/org.apache.jackrabbit.oak%3Aid%3D16%2Cname%3D%22Oak+Repository+Statistics%22%2Ctype%3D%22RepositoryStats%22`

Im Abschnitt **ObservationQueueMaxLength** wird die Anzahl der Ereignisse in der Oak-Überwachungswarteschlange während der letzten Stunden, Minuten, Sekunden und Wochen angezeigt. Suchen Sie im Abschnitt „per hour“ nach der größten Anzahl von Ereignissen. Diese Zahl muss mit der `oak.observation.queue-length` -Einstellung. Wenn die höchste für die Beobachtungswarteschlange angezeigte Zahl die `queue-length` Einstellung:

1. Erstellen Sie eine Datei mit dem Namen: `com.adobe.granite.repository.impl.SlingRepositoryManager.cfg` enthält den Parameter `oak.observation.queue‐length=50000`
1. Platzieren Sie sie im Ordner /crx-quickstart/install .

>[!NOTE]
>Siehe auch den KB-Artikel unter [AEM 6.x | Tipps zur Leistungsoptimierung](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html)

Die Standardeinstellung ist 10,000, aber für die meisten Bereitstellungen ist normalerweise eine Anhebung auf 20.000 oder 50.000 erforderlich.

## Veröffentlichungsumgebung {#publish-environment}

### Durchführen von Tests {#performing-tests-1}

Der wichtigste Teil einer Bereitstellung, der Auslastungstests unterzogen werden muss, ist die Veröffentlichungs- oder Dispatcherumgebung für Endbenutzer.

Die Leistung der Website kann mithilfe automatisierter Testtools von Drittanbietern überprüft werden. Über diese Tools können Sie die Schritte aufzeichnen, die Benutzer auf der Website durchführen, und viele dieser Sitzungen gleichzeitig ausführen, um die für eine Produktionswebsite typische Last zu simulieren.

Die meisten Produktionswebsites besitzen Optimierungsfunktionen wie Dispatcher-Caching und ein Netzwerk für die Inhaltsbereitstellung. Sie müssen beim Testen sicherstellen, dass diese Optimierungen auch für die Testumgebung verfügbar sind. Abgesehen von der Überwachung der Antwortzeiten für Endbenutzer müssen Sie auch die Systemmetriken auf den Veröffentlichungsservern und Dispatchern im Auge behalten, um Einschränkungen des Systems aufgrund der Hardwareressourcen auszuschließen.

Auf einem System ohne hohen Personalisierungsbedarf sollte der Dispatcher die meisten Anforderungen im Cache speichern. Daher sollte die Belastungskurve für die Veröffentlichungsinstanz relativ flach verlaufen. Wenn ein hohes Maß an Personalisierung erforderlich ist, werden Technologien wie iFrame oder AJAX-Anforderungen für den personalisierten Inhalt empfohlen, um ein Maximum an Dispatcher-Caching zuzulassen.

Für grundlegende Tests können mit Apache Bench die Antwortzeit der Webserver gemessen und Lasten für Messungen, etwa von Speicherverlusten, generiert werden. Weitere Informationen liefert Ihnen das Beispiel in der [Dokumentation zur Überwachung](/help/sites-deploying/monitoring-and-maintaining.md#apache-bench).

## Fehlerbehebung von Leistungsproblemen {#troubleshooting-performance-issues}

Im Anschluss an die Leistungstests der Autoreninstanz müssen alle festgestellten Probleme untersucht, diagnostiziert und behoben werden. Zur Analyse und Behandlung dieser Probleme können Sie verschiedene Tools und Verfahren anwenden:

* Sie können das [Protokoll für die Anforderungsleistung](/help/sites-administering/operations-dashboard.md#request-performance) im Vorgangs-Dashboard einsehen. Mit diesem Tool können Sie langsame Seitenanforderungen identifizieren.
* Analysieren Sie langsame Abfragen mit dem [Tool „Abfrageleistung“](/help/sites-administering/operations-dashboard.md#query-performance).

* Überprüfen Sie das Fehlerprotokoll auf Fehler oder Warnungen. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
* Überwachen Sie die Hardwareressourcen des Systems wie den Arbeitsspeicher und die CPU oder I/O-Vorgänge von Festplatte bzw. Netzwerk. Diese Ressourcen sind häufig die Ursache für Leistungsengpässe.
* Optimieren Sie die Architektur der Seiten und ihre Adressierung, um die Nutzung von URL-Parametern zu minimieren, damit ein Höchstmaß an Caching ermöglicht wird.
* Folgen Sie der Dokumentation zur [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) und den [Tipps zur Leistungsoptimierung](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html).

* Wenn es Probleme beim Bearbeiten bestimmter Seiten oder Komponenten in Autoreninstanzen gibt, sehen Sie sich die fragliche Seite mithilfe des Entwicklermodus der Touch-optimierten Benutzeroberfläche an. Dabei wird jeder Inhaltsbereich auf der Seite samt Ladezeit aufgeschlüsselt.
* Führen Sie eine vollständige JS- und CSS-Minimierung auf der Website durch. Weitere Informationen dazu finden Sie in diesem [Blogpost](https://blogs.adobe.com/foxes/enable-js-and-css-minification/).
* Beseitigen Sie eingebettete CSS- und JS-Elemente aus den Komponenten. Diese sollten in den clientseitigen Bibliotheken enthalten und minimiert sein, um die Anzahl der zum Rendern der Seite benötigten Anforderungen zu minimieren.
* Verwenden Sie Browsertools wie die Chrome-Registerkarte „Netzwerk“, um Serveranforderungen zu untersuchen und die Anforderungen mit der längsten Dauer zu ermitteln.

Nach Identifizierung von Problembereichen kann der Anwendungscode im Hinblick auf Leistungsoptimierungen untersucht werden. Sollten AEM-Standardfunktionen nicht ordnungsgemäß verwendet werden können, wenden Sie sich an den Adobe-Support, um Unterstützung zu erhalten.
