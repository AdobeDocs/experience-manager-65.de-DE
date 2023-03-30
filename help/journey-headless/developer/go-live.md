---
title: Live-Schalten Ihres Headless-Programms
description: In diesem Teil der AEM Headless-Entwickler-Tour erfahren Sie, wie Sie eine Headless-Anwendung live schalten.
exl-id: ec3356ef-9e60-4151-984d-3ebdab593b96
source-git-commit: 71842228dd3cb1ce3b79728912e8333d25fccefc
workflow-type: tm+mt
source-wordcount: '1846'
ht-degree: 62%

---

# Live-Schalten Ihres Headless-Programms {#go-live}

In diesem Teil der [AEM Headless-Entwickler-Tour](overview.md) erfahren Sie, wie Sie eine Headless-Anwendung live schalten.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument zur AEM Headless-Entwickler-Tour [Aktualisieren Ihres Inhalts über AEM Assets-APIs](update-your-content.md) haben Sie erfahren, wie Sie Ihren vorhandenen Headless-Content in AEM über die API aktualisieren können. Nun verfügen Sie über folgende Kenntnisse:

* Grundlegendes zur AEM Assets-HTTP-API

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie Ihr eigenes AEM Headless-Projekt für die Live-Schaltung vorbereiten können.

## Ziel {#objective}

In diesem Dokument erhalten Sie Informationen zur AEM Headless-Veröffentlichungs-Pipeline und zu den Leistungsaspekten, die Sie vor der Live-Schaltung Ihres Programms beachten müssen.

* Erfahren Sie mehr über das AEM-SDK und die erforderlichen Entwicklungs-Tools.
* Richten Sie eine lokale Entwicklungslaufzeit ein, um Ihre Inhalte vor der Live-Schaltung zu simulieren.
* Machen Sie sich mit den Grundlagen zur AEM-Inhaltsreplikation und -Zwischenspeicherung vertraut.
* Sichern und skalieren Sie Ihr Programm vor dem Launch.
* Überwachen Sie Performance- und Debugging-Probleme.

## Das AEM-SDK {#the-aem-sdk}

Das AEM-SDK wird zum Erstellen und Bereitstellen von anwenderdefiniertem Code verwendet. Es ist das Hauptwerkzeug, das Sie vor der Live-Schaltung entwickeln und testen müssen. Es enthält die folgenden Artefakte:

* Die Quickstart-JAR-Datei: eine ausführbare JAR-Datei, die sowohl zum Einrichten einer Autoren- als auch einer Veröffentlichungsinstanz verwendet werden kann
* Dispatcher Tools - das Dispatcher-Modul und seine Abhängigkeiten für Windows- und UNIX-basierte Systeme
* Java™-API-JAR-Datei: die Java™-JAR-/Maven-Abhängigkeit, die alle zulässigen Java™-APIs verfügbar macht, die zur Entwicklung für AEM verwendet werden können
* Javadoc-JAR: die Javadocs für die Java™-API-JAR-Datei

## Weitere Entwicklungs-Tools {#additional-development-tools}

Zusätzlich zum AEM SDK benötigen Sie zusätzliche Tools, die die lokale Entwicklung und Prüfung von Code und Inhalt erleichtern:

* Java™
* Git
* Apache Maven
* Die Node.js-Bibliothek
* Die IDE Ihrer Wahl

Da AEM eine Java™-Anwendung ist, müssen Sie Java™ und das Java™ SDK installieren, um die Entwicklung von AEM as a Cloud Service zu unterstützen.

Git wird für die Versionskontrolle verwendet sowie dazu, die Änderungen in Cloud Manager einzuchecken und sie dann in einer Produktionsinstanz bereitzustellen.

AEM verwendet Apache Maven zum Erstellen von Projekten, die aus dem AEM-Maven-Projektarchetyp generiert wurden. Alle wichtigen IDEs bieten Integrationsunterstützung für Maven.

Node.js ist eine JavaScript-Laufzeitumgebung, die zum Arbeiten mit den Frontend-Assets der AEM verwendet wird. `ui.frontend` Unterprojekt. Node.js wird mit npm bereitgestellt, dem De-facto-Package-Manager von Node.js, der zum Verwalten von JavaScript-Abhängigkeiten verwendet wird.

## Komponenten eines AEM-Systems auf einen Blick {#components-of-an-aem-system-at-a-glance}

Als Nächstes sehen wir uns die Bestandteile einer AEM-Umgebung an.

Eine vollständige AEM-Umgebung besteht aus einer Autoren-, Veröffentlichungs- und Dispatcher-Komponente. Dieselben Komponenten werden in der lokalen Entwicklungslaufzeit bereitgestellt, damit Sie Ihre Code- und Inhaltsvorschau vor der Live-Schaltung einfacher anzeigen können.

* **Der Autoren-Service**, mit dem interne Anwender Inhalte erstellen, verwalten und in der Vorschau anzeigen.

* **Der Veröffentlichungsdienst** wird als &quot;Live&quot;-Umgebung betrachtet und ist in der Regel das, mit dem Endbenutzer interagieren. Inhalte werden nach der Bearbeitung und Genehmigung im Autoren-Service an den Veröffentlichungs-Service weitergeleitet (repliziert). Das häufigste Bereitstellungsmuster bei AEM Headless-Programmen besteht darin, die Produktionsversion des Programms mit dem Veröffentlichungs-Service von AEM zu verbinden.

* **Der Dispatcher** ist ein statischer Webserver, der durch das AEM Dispatcher-Modul erweitert wird. Er speichert durch die Veröffentlichungsinstanz generierte Web-Seiten zwischen, um die Leistung zu verbessern.

## Workflow für die lokale Entwicklung {#the-local-development-workflow}

Das Projekt für die lokale Entwicklung basiert auf Apache Maven und verwendet Git für die Quell-Code-Verwaltung. Um das Projekt zu aktualisieren, können Entwickler unter anderem ihre bevorzugte integrierte Entwicklungsumgebung wie Eclipse, Visual Studio Code oder IntelliJ verwenden.

Um Code- oder Inhaltsaktualisierungen zu testen, die von Ihrer Headless-Anwendung erfasst werden, stellen Sie die Aktualisierungen zur lokalen AEM-Laufzeit bereit. Dazu gehören lokale Instanzen der AEM-Autoren- und Veröffentlichungsdienste.

Achten Sie auf die Unterschiede zwischen den einzelnen Komponenten in der lokalen AEM-Laufzeit, da Sie Ihre Updates unbedingt dort testen sollten, wo sie am relevantesten sind. Testen Sie beispielsweise Inhaltsaktualisierungen in der Autoreninstanz, bzw. neuen Code in der Veröffentlichungsinstanz.

In einem Produktionssystem befinden sich Dispatcher und ein Apache-HTTP-Server immer vor der AEM-Veröffentlichungsinstanz. Sie stellen Caching- und Sicherheits-Services für das AEM-System bereit, daher ist es von größter Bedeutung, Code- und Inhaltsaktualisierungen auch in Richtung Dispatcher zu testen.

## Lokale Vorschau Ihres Codes und Ihrer Inhalte mit der lokalen Entwicklungsumgebung {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Um Ihr AEM Headless-Projekt auf den Start vorzubereiten, stellen Sie sicher, dass alle Bestandteile Ihres Projekts gut funktionieren.

Dazu müssen Sie alles zusammenfassen: Code, Inhalt und Konfiguration verwenden und in einer lokalen Entwicklungsumgebung testen, um Live-Bereitschaft zu gewährleisten.

Das lokale Entwicklungsumfeld umfasst drei Hauptbereiche:

1. Das AEM-Projekt - enthält den gesamten benutzerdefinierten Code, die Konfiguration und den Inhalt, an dem die AEM-Entwickler arbeiten werden
1. Die lokale AEM-Laufzeit: Dies sind lokale Versionen der Autoren- und Veröffentlichungs-Services von AEM, die zum Bereitstellen von Code aus dem AEM-Projekt verwendet werden.
1. Die lokale Dispatcher-Laufzeit: Dies ist eine lokale Version des Apache-HTTP-Servers („httpd“), die das Dispatcher-Modul enthält.

Nachdem die lokale Entwicklungsumgebung eingerichtet wurde, können Sie die Bereitstellung von Inhalten für die React-App simulieren, indem Sie lokal einen statischen Knotenserver bereitstellen.

Einen detaillierteren Überblick über das Einrichten einer lokalen Entwicklungsumgebung und alle Abhängigkeiten, die für die Inhaltsvorschau erforderlich sind, erhalten Sie unter [Dokumentation zur Produktionsbereitstellung](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/overview.html?lang=en).

## Vorbereiten Ihres AEM Headless-Programms für die Live-Schaltung {#prepare-your-aem-headless-application-for-golive}

<!-- Start of CDN Review -->

Jetzt sollten Sie Ihr AEM Headless-Programm für den Launch vorbereiten, indem Sie die nachfolgend beschriebenen Best Practices umsetzen.

### Sichern Ihres Headless-Programms vor dem Launch {#secure-and-scale-before-launch}

1. Vorbereiten der [Authentifizierung](/help/sites-developing/headless/graphql-api/graphql-authentication-content-fragments.md) für Ihre GraphQL-Anfragen

### Modellstruktur und GraphQL-Ausgabe im Vergleich {#structure-vs-output}

* Erstellen Sie keine Abfragen, die mehr als 15 KB JSON ausgeben (gzip-komprimiert). Die Analyse großer JSON-Dateien ist für Client-Programme ressourcenintensiv.
* Vermeiden Sie mehr als fünf verschachtelte Ebenen in Fragmenthierarchien. Zusätzliche Ebenen erschweren es Inhaltsautoren, die Auswirkungen ihrer Änderungen zu berücksichtigen.
* Verwenden Sie Abfragen mit mehreren Objekten, anstatt Abfragen mit Abhängigkeitshierarchien innerhalb der Modelle zu modellieren. Dies ermöglicht eine langfristige Flexibilität bei der Neustrukturierung der JSON-Ausgabe, ohne dass viele Inhaltsänderungen erforderlich sind.

### Maximieren der CDN-Cache-Trefferquote {#maximize-cdn}

* Verwenden Sie keine direkten GraphQL-Abfragen, es sei denn, Sie fordern Live-Inhalte von der Oberfläche an.
   * Verwenden Sie nach Möglichkeit persistente Abfragen.
   * Stellen Sie CDN-TTL über 600 Sekunden bereit, damit das CDN sie zwischenspeichern kann.
   * AEM kann die Auswirkungen einer Modelländerung auf vorhandene Abfragen berechnen.
* Teilen Sie JSON-Dateien/GraphQL-Abfragen zwischen niedriger und hoher Inhaltsänderungsrate auf, um den Client-Traffic zu CDN zu reduzieren und eine höhere TTL zuzuweisen. Dadurch wird das CDN, das die JSON-Datei mit dem Herkunftsserver erneut validiert, minimiert.
* Verwenden Sie &quot;Soft Purge&quot;, um Inhalte aus dem CDN aktiv ungültig zu machen. Dadurch kann das CDN den Inhalt erneut herunterladen, ohne dass ein Cache fehlschlägt.

>[!NOTE]
>
>Weitere Informationen über CDN und Caching finden Sie unter [Zusätzliche Ressourcen](#additional-resources).

### Verkürzen der Download-Zeit für Headless-Content {#improve-download-time}

* Stellen Sie sicher, dass HTTP-Clients HTTP/2 verwenden.
* Stellen Sie sicher, dass HTTP-Clients Header-Anfragen für gzip akzeptieren.
* Minimieren Sie die Anzahl der Domains, die zum Hosten von JSON und referenzierten Artefakten verwendet werden.
* Verwendung `Last-modified-since` , um Ressourcen zu aktualisieren.
* Verwenden Sie die `_reference`-Ausgabe in der JSON-Datei, um mit dem Herunterladen von Assets zu beginnen, ohne vollständige JSON-Dateien analysieren zu müssen.

<!-- End of CDN Review -->

## Bereitstellung für Produktion {#deploy-to-production}

Die Bereitstellung in der Produktion kann davon abhängen, ob Sie über eine *traditionelle* AEM-Instanz verfügen, die mithilfe von Maven bereitgestellt wird oder ob Sie sich in Adobe Managed Services (AMS) befinden und daher Cloud Manager verwenden.

## Bereitstellen in der Produktion mit Maven {#deploy-to-production-maven}

Für *traditionell* Implementierung (Nicht-AMS) mit Maven, siehe [WKND-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html?lang=de#build) für einen Überblick.

## Bereitstellen in der Produktion mit Cloud Manager {#deploy-to-production-cloud-manager}

Wenn Sie ein AMS-Kunde sind, der Cloud Manager verwendet, können Sie, nachdem Sie sichergestellt haben, dass alles getestet und ordnungsgemäß funktioniert, Ihre Code-Aktualisierungen an eine [zentralisiertes Git-Repository in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/git-integration.html).

Nachdem die Aktualisierungen in Cloud Manager hochgeladen wurden, stellen Sie sie AEM mithilfe von bereit. [CI/CD-Pipeline von Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-deployment.html).

<!-- Can't find a parallel link -->
<!--
You can start deploying your code by leveraging the Cloud Manager CI/CD pipeline, which is covered extensively [here](/help/implementing/deploying/overview.md).
-->

## Performance-Überwachung {#performance-monitoring}

Damit Benutzerinnen und Benutzern bei der Nutzung des AEM Headless-Programms das bestmögliche Erlebnis geboten wird, müssen Sie die wichtigsten Performance-Metriken überwachen, wie nachfolgend beschrieben:

* Validieren der Vorschau- und Produktionsversionen des Programms
* Prüfen der AEM-Statusseiten auf den aktuellen Status der Service-Verfügbarkeit
* Abrufen von Performance-Berichten
   * Bereitstellungs-Performance
      * Urspungs-Server – Anzahl der Aufrufe, Fehlerquoten, CPU-Auslastung, Payload-Traffic
   * Authoring-Performance
      * Anzahl der Benutzer, Anforderungen und Ladevorgänge überprüfen
* Abrufen programm- und speicherplatzspezifischer Performance-Berichte
   * Prüfen, ob die allgemeinen Metriken grün/orange/rot gekennzeichnet sind, sobald der Server hochgefahren ist, um anschließend spezifische Programmprobleme zu identifizieren
   * Öffnen der oben genannten Berichte, jedoch gefiltert nach Programm oder Speicherplatz. (z. B. Desktop-Version von Photoshop, Paywall)
   * Verwenden von Splunk-Protokoll-APIs, um Performance-Berichte zu Services und Programmen abzurufen
   * Wenden Sie sich an den Support, falls weitere Probleme auftreten.

## Fehlerbehebung {#troubleshooting}

### Debugging {#debugging}

Befolgen Sie die folgenden Best Practices als allgemeinen Debugging-Ansatz:

* Validieren der Funktionalität und Performance mit der Vorschauversion des Programms
* Validieren der Funktionalität und Performance mit der Produktionsversion des Programms
* Validieren mit der JSON-Vorschau des Inhaltsfragment-Editors
* Prüfen Sie die JSON-Datei in der Clientanwendung, um festzustellen, ob es zu Problemen mit der Clientanwendung oder dem Versand kommt.
* Um zu überprüfen, ob Probleme im Zusammenhang mit zwischengespeicherten Inhalten oder AEM vorliegen, überprüfen Sie die JSON mit GraphQL.

### Protokollieren eines Fehlers beim Support {#logging-a-bug-with-support}

Führen Sie die folgenden Schritte aus, um einen Fehler beim Support effizient zu protokollieren, falls Sie weitere Unterstützung benötigen:

* Erstellen Sie ggf. Screenshots zum Problem.
* Dokumentieren Sie eine Methode, das Problem zu reproduzieren.
* Dokumentieren Sie, mit welchen Inhalten sich das Problem reproduzieren lässt.
* Protokollieren Sie das Problem über das AEM-Support-Portal mit der entsprechenden Priorität.

## Die Tour ist (fast) zu Ende {#journey-ends}

Herzlichen Glückwunsch! Sie haben die AEM Headless-Entwickler-Tour abgeschlossen! Sie sollten jetzt mit Folgendem vertraut sein:

* Unterschied zwischen Headless- und Headful-Inhaltsbereitstellung
* AEM Headless-Funktionen
* Organisieren eines AEM-Headless-Projekts
* Erstellen von Headless-Inhalten in AEM
* Abrufen und Aktualisieren von Headless-Inhalten in AEM
* Live-Schaltung mit einem AEM Headless-Projekt
* Was zu tun ist, nachdem die Live-Schaltung abgeschlossen ist?

Sie haben entweder bereits Ihr erstes AEM Headless-Projekt gestartet oder verfügen nun über das entsprechende Wissen. Gute Arbeit!

### Erkunden von Single Page Applications {#explore-spa}

Es ist jedoch nicht notwendig, die Headless-Stores in AEM zu stoppen. Im [Erste Schritte im Journey](getting-started.md#integration-levels), wurde erläutert, wie AEM nicht nur Headless-Bereitstellung und herkömmliche Full-Stack-Modelle unterstützt, sondern auch Hybridmodelle unterstützt, die die Vorteile beider Modelle kombinieren.

Wenn Sie diese Flexibilität für Ihr Projekt benötigen, setzen Sie sich mit dem optionalen, zusätzlichen Teil der Journey fort. [So erstellen Sie Einzelseiten-Apps (SPA) mit AEM.](create-spa.md)

## Zusätzliche Ressourcen {#additional-resources}

* [AEM-Entwicklerhandbuch](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/the-basics.html?lang=de)

* [WKND-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de)

* [Cloud Manager für AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=en)

* CDN-Cache

   * [Steuern eines CDN-Cache](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de#controlling-a-cdn-cache)

   * Konfigurieren des [CDN Rewriters](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html?lang=de) (*suchen Sie nach CDN Rewriter*)
