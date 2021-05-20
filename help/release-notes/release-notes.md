---
title: Allgemeine Versionshinweise für  [!DNL Adobe Experience Manager] 6.5
description: '[!DNL Adobe Experience Manager]Informationen zu  6.5 mit Versionshinweisen, Angaben zu neuen Funktionen und zur Installation sowie ausführlichen Änderungslisten.'
exl-id: 0288aa12-8d9d-4cec-9a91-7a4194dd280a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2150'
ht-degree: 66%

---

# Allgemeine Versionshinweise für [!DNL Adobe Experience Manager] 6.5{#general-release-notes-for-adobe-experience-manager}

## Versionshinweise {#release-information}

| Produkt | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6.5 |
| Typ | Hauptversion |
| Datum der allgemeinen Verfügbarkeit | 8. April 2019 |
| Empfohlene Updates | Siehe [AEM aktuelle Updates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de). |

### Wissenswertes {#trivia}

Der Veröffentlichungszyklus für diese Version von [!DNL Adobe Experience Manager] begann am 4. April 2018, durchlief 23 Iterationen zur Qualitätssicherung und Fehlerbehebung und endete am 28. März 2019. Insgesamt wurden in dieser Version 1345 kundenbezogene Probleme behandelt, einschließlich Verbesserungen und neuer Funktionen.

[!DNL Adobe Experience Manager] 6.5 ist seit dem 8. April 2019 allgemein verfügbar.

![AEM 6.5-Anmeldebildschirm](/help/assets/assets/aem65-login-v4.png)

## Neue Funktionen {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 ist eine Upgrade-Version für die Codebasis von  [!DNL Adobe Experience Manager] 6.4. Die Software bietet neue und erweiterte Funktionen, wichtige Kundenkorrekturen, Erweiterungen für Kunden mit hoher Priorität und allgemeine Fehlerbehebungen, die auf die Produktstabilisierung ausgerichtet sind. Es enthält auch [!DNL Adobe Experience Manager] 6.4 Service Pack-Versionen bis SP4.

Die nachstehende Liste bietet eine Übersicht, während die nachfolgenden Seiten die vollständigen Details auflisten.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Vollständige Liste der Änderungen in [AEM Foundation](/help/release-notes/wcm-platform.md).

Die Plattform von [!DNL Adobe Experience Manager] 6.5 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java Content Repository: Apache Jackrabbit Oak 1.10.2.

Quickstart verwendet Eclipse Jetty 9.4.15 als Servlet-Engine.

#### Java-Unterstützung  {#java-support}

* Neue Unterstützung für Java 11 sowie für bereits unterstützte Java 8.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md) .
* Java 11- und Java 8-Wartungsupdates werden von Adobe für die Kundennutzung in AEM-bezogenen Projekten verteilt, wenn sie nicht über Oracle öffentlich verfügbar sind.

#### Java-Entwicklung {#java-development}

* Es gibt jetzt [zwei Versionen von Uberjar](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), eine empfohlene Version mit öffentlichen Schnittstellen, die nicht für die Einstellung markiert sind, sowie eine Version, die Schnittstellen enthält, die für die Einstellung markiert sind.

#### Benutzeroberfläche {#user-interface}

Die Benutzeroberfläche wurde verbessert, um sie effizienter und anwenderfreundlicher zu gestalten.

* Neue Benutzeroberfläche für die Berechtigungsverwaltung für Benutzer und Gruppen.
* In Spaltenansichten werden nun auch nur noch die Einträge geladen, die auf dem Bildschirm sichtbar sind. Weitere Einträge werden lediglich geladen, wenn der Anwender einen Bildlauf durchführt. In der Listen- und Kartenansicht wurde so bereits seit Version 6.0 verfahren (verbessert in Version 6.4)..
* Spaltenansichten enthalten jetzt ggf. den Workflow-Status für Seiten/Assets.
* Die Aktion [Alle auswählen](/help/sites-authoring/basic-handling.md#select-all) ist eine schnelle Möglichkeit, eine Aktion mit allen Seiten/Assets im selben Ordner auszuführen.
* Mit der Aktion [Alle auswählen](/help/sites-authoring/basic-handling.md#select-all) wird versucht, die Aktion für alle Seiten/Assets durchzuführen, nicht nur für die geladenen Elemente. Ein Warndialogfeld wird angezeigt, wenn die Aktion nicht für die Verarbeitung von Massenaktionen aktualisiert wurde.

>[!CAUTION]
>
>Adobe plant keine weiteren Verbesserungen an der klassischen UI. In AEM 6.5 ist die klassische UI integriert und Kunden, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird. [Weitere Informationen](/help/sites-deploying/ui-recommendations.md).

#### Suche und Indizierung {#indexing-and-search}

* Die Suche in Oak unterstützt jetzt dynamische Facetten. Beispielsweise zeigt die Filterleiste bei der Asset-Suche die geschätzte Ergebnismenge an.
* QueryBuilder wurde erweitert, um Ergebnisse mit dynamischen Facetten bereitzustellen.

#### Aktualisierung {#upgrade}

* Kunden mit AEM 6.2, 6.3 und 6.4 können direkt auf AEM 6.5 aktualisieren. Kunden, die 5.x oder 6.0/6.1 verwenden und ein direktes Upgrade durchführen möchten, müssen zunächst auf 6.4 und dann auf 6.5 aktualisieren oder durch eine Übertragung der Inhalte zwischen Instanzen sofort auf AEM 6.5 aktualisieren.

#### Projekte und Workflows {#projects-and-workflows}

* Der neue in Version 6.4 eingeführte Workflow-Modell-Editor wurde verbessert. Neben einer größeren Anzahl von Vorgängen wie Kopieren und Veröffentlichen werden nun Variablen in Workflowschritten unterstützt. Außerdem wurden ODER- und UND-Teilungen optimiert.

### [!DNL Experience Manager] Sites {#experience-manager-sites}

Vollständige Liste der Änderungen in [AEM Sites und Add-ons](/help/release-notes/sites.md).

#### Managed-Single-Page-Apps {#managed-single-page-apps}

Der Seiten-Editor ermöglicht nun kontextbezogene Inhaltsbearbeitungen und Erstell-/Layoutvorgänge in clientseitig gerenderter Erlebnissen (auch als [SPA-Editor](/help/sites-developing/spa-architecture.md) bekannt). Vorhandene Single-Page-Apps, die auf dem JavaScript-Framework React oder Angular basieren, können mit AEM SJ SDK erweitert werden, damit sie von Experten bearbeitet werden können.

Die zunächst als Teil von AEM 6.4 SP2 bereitgestellte SPA-Unterstützung bietet in AEM 6.5 folgende Funktionen:

* Bearbeiten und Konfigurieren der bearbeitbaren AEM-Teile der SPA mit dem Vorlagen-Editor
* Verwenden Sie Multi-Site-Management, um länderspezifische, Franchise- oder White-Label-SPA zu erstellen.

#### Headless-Content-Management {#headless-content-management}

Mit AEM können Inhalte in verschiedenen Formaten und aus verschiedenen Ebenen des Stapels bereitgestellt werden. Einige von ihnen sind durch das [Sling GET-](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) und [POST-Servlet](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) bereits seit 2008 verfügbar. Content Services ([Sling Model Exporter](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/foundation/development/develop-sling-model-exporter.html)) wurden in AEM 6.3 eingeführt und sind die von AEM SJ SDK eingesetzte Hydrationsmethode für Single-Page-Apps. Die [HTTP-API für Assets](/help/assets/mac-api-assets.md) ist eine für AEM 6.5 erweiterte CRUD-API. 

Neue HTTP-API-Funktionen:

* Neuerdings [Unterstützung von Inhaltsfragmenten in der HTTP-API für Assets](/help/assets/assets-api-content-fragments.md) zum Erstellen, Aktualisieren, Lesen und Löschen von Fragmenten
* Offenlegung von Inhaltsfragmentlisten über Content Services mit der [Kernkomponenten-Inhaltsfragmentliste](https://opensource.adobe.com/aem-core-wcm-components/library/content-fragment-list.html)
* [Kernkomponentenbibliothek](https://opensource.adobe.com/aem-core-wcm-components/library.html) zur Anzeige der Content Services-JSON-Standardausgabe für jede Komponente

#### Screens-Add-on  {#screens-add-on}

Sie können Erlebnisse effizient entwickeln, bereitstellen und optimieren, und zwar auf allen digitalen Displays, ob interaktiver Kiosk oder digitale Beschilderung (Digital Signage).

**Design**

* Vereinheitlichung von Erlebnissen und Inhalten, online und offline, mit verbesserter Wiederverwendung von Inhalten
* Optimierte Erstellungs- und Genehmigungs-/Veröffentlichungsworkflows mit Unterstützung für Launches
* Bearbeitung und Bereitstellung von ansprechenden, interaktiven Erlebnissen mit dem SPA-Editor

**Bereitstellung**

* Erweiterte Medienplayer-Unterstützung für zuverlässigen Online- und Offlinebetrieb (Smart Sync), skalierbar sogar für größte Signage-Netzwerke

**Optimierung**

* Ortsbezogene Personalisierung oder Konfiguration von datenbasierten Inhalten durch Nutzung dynamischer Platzhalter
* Einheitliche Einblicke durch die Adobe Analytics-Integration in AEM Screens Player

Weitere Informationen zu Änderungen an AEM Screens finden Sie in den Versionshinweisen im [AEM Screens-Benutzerhandbuch](https://docs.adobe.com/content/help/de-DE/experience-manager-screens/user-guide/aem-screens-introduction.html).

### [!DNL Experience Manager Assets] {#experience-manager-assets}

Vollständige Liste der Änderungen in den [AEM 6.5 Assets-Versionshinweisen](/help/release-notes/assets.md).

AEM 6.5 beinhaltet die folgenden neuen Funktionen und Erweiterungen mit denen AEM-Anwender, DAM-Anwender und Anwender mit entsprechenden Kreativ- sowie Marketingfunktionen ihre Produktivität steigern können.

#### Integrieren in Adobe Creative Cloud  {#integration-with-adobe-creative-cloud}

Neu hinzugekommen ist [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html). Damit profitieren kreative Anwender, die mit Adobe Creative Cloud-Anwendungen wie Photoshop, Illustrator und InDesign arbeiten, von In-App-Erlebnissen – für eine optimierte Zusammenarbeit zwischen Kreativen und Marketern bei der Inhaltserstellung. AEM Desktop-Programm unterstützt weiterhin die Anforderungen von Benutzern, die mit Assets von AEM auf dem Desktop arbeiten, wobei jeder Dateityp und jedes Desktop-Programm verwendet werden.

Darüber hinaus ist AEM in Adobe Stock integriert und ermöglicht so die Suche, Vorschau, Lizenzierung und Speicherung von Adobe Stock-Assets direkt über die AEM-Web-UI.

![Bedienfeld „Asset-Link“ in Photoshop](/help/assets/assets/aem65-assetlink-photoshop.png)

#### Connected Assets {#connected-assets}

Die Funktion &quot;Connected Assets&quot;ist auf größere Bereitstellungen mit einer Reihe von AEM Sites-Bereitstellungen ausgerichtet, die Assets aus einer zentralen AEM Assets DAM-Bereitstellung nutzen müssen. Dadurch wird nicht nur die Governance im Zusammenhang mit zentral verwalteten Assets verbessert, sondern auch eine hocheffiziente Bereitstellung von Assets für verschiedene Sites-Implementierungen ermöglicht.

### Dynamic Media {#dynamic-media}

Dynamic Media bietet eine erweiterte Rich-Media-Erstellung und -Bereitstellung in AEM Assets für beeindruckend intensive, personalisierte Erlebnisse. Mit einem einzigen hochwertigen Master-Asset können Sie unsere erweiterte Cloudrendering-Funktion „Smartes Zuschneiden“ sowie marktführende Viewer nutzen, um faszinierende Erlebnisse mit branchenführender Leistung zu erzielen.

Zu den neuen Funktionen zählen:

* Unterstützung für 360-Grad-Video- und VR-Headsets
* Benutzerdefinierte Videominiaturen
* Verbesserte Unterstützung für Barrierefreiheit
* Schutz gegen Hotlinking

#### Anwendererlebnis und Suche {#user-experience-and-search}

Wichtige Verbesserungen ermöglichen hier zweierlei: eine schnellere Asset-Suche durch dynamische Suchfacetten und eine effizientere Verwaltung mehrerer Assets durch gleichzeitige Auswahl aller Assets aus beliebigen Ordnern oder Suchergebnissen.

### [!DNL Adobe Experience Manager Forms] {#experience-manager-forms}

AEM 6.5 wurde um zahlreiche neue Funktionen und Erweiterungen ergänzt. Hier einige der Highlights:

* Transaktionsberichte zur Verfolgung der Anzahl gesendeter Formulare, verarbeiteter Dokumente und gerenderter Dokumente
* Verbesserte Nutzung interaktiver Kommunikation
* Cloudbasierte digitale Signaturen in adaptiven Formularen
* Integration adaptiver Formulare und interaktiver Kommunikation in eine AEM Sites-Single-Page-App (SPA).
* Unterstützung für Variablen in AEM-Workflows
* Unterstützung von Datenanzeigemustern bei interaktiver Kommunikation
* Sortierung adaptiver Formulare und interaktiver Kommunikationstabellen
* Automatische Validierung von Eingabedaten in Formulardatenmodellen

Weitere Informationen zu neuen und verbesserten Funktionen und Dokumentationsressourcen finden Sie in der [Zusammenfassung der neuen Funktionen und Verbesserungen in AEM 6.5 Forms](/help/forms/using/whats-new.md) .

### [!DNL Experience Manager Communities] {#communitiesreleasenotes}

AEM 6.5 bietet verschiedene neue Funktionen und Erweiterungen für Communities. Highlights dieser Version:

* Unterstützung beim Tagging registrierter Mitglieder (@mention) während der Erstellung anwendergenerierter Inhalte
* Unterstützung direkter Massennachrichten an Mitgliedergruppen
* Benutzerdefinierte Filter, entwickelt und hinzugefügt zur UI für Massenmoderation; Ein [Beispielprojekt](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter), das die Filterung nach Tags demonstriert, kann als Grundlage für die Entwicklung analoger benutzerdefinierter Filter verwendet werden.
* Neue Listenansicht mit verbesserter UI für die Massenmoderation
* Möglichkeit zur Zuweisung verschiedener Administratoren für unterschiedliche Community-Sites und verschachtelte Gruppen (statt eines einzigen Community-Administrators)
* Die Aktivierungsfunktion von AEM 6.5 Communities unterstützt die Engine [ (SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/).
* Verbesserte Barrierefreiheit durch unterstützte Tastaturnavigation bei Aktivierungskomponenten
* Apache Solr 7.0-Unterstützung beim Einrichten von MSRP und DSRP

Eine detaillierte Liste der Änderungen finden Sie unter [AEM 6.5 Communities Versionshinweise](/help/release-notes/communities-release-notes.md).

### [!DNL Experience Manager Livefyre] {#experience-manager-livefyre}

Livefyre lässt sich in AEM 6.5-Instanzen integrieren. Siehe [Wie man Livefyre mit AEM](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html) integriert.

### Kundenorientierte Entwicklung nutzen {#leverage-customer-focused-development}

Adobe verwendet ein kundenorientiertes Entwicklungsmodell, das es den Kunden ermöglicht, zu allen Phasen des Entwicklungsprozesses von der Spezifikation bis zur Entwicklung und zum Test beizutragen. Unser Dank geht an alle beteiligten Kunden und Partner in diesem Prozess.

Adobe hält die erforderlichen Vorgehensweisen und Prozesse bereit, um die Erfassung, Priorisierung und Verfolgung kundenorientierter Fehlerbehebungs- und Verbesserungsanforderungsentwicklung zu ermöglichen. Das [Adobe Marketing Cloud Support Portal](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) ist in das Adobe Enhancement and Defect Tracking System integriert. Kundenprobleme werden, wenn möglich, gemeinsam mit dem Kundendienst identifiziert und gelöst. Bei einer Weiterleitung an Forschung und Entwicklung werden alle Kundeninformationen erfasst und zu Priorisierungs- und Berichterstellungszwecken verwendet. Bei der Entwicklung werden gebührenpflichtiger Support, Garantieprobleme und kundenbezahlte Verbesserungen Priorität eingeräumt.

Dieser Prozess der Priorisierung hat zu mehr als 750 kundenorientierten Änderungen geführt, die in AEM 6.5 vorgenommen wurden.

## Liste der Dateien, die Teil der Version sind {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Eigenständiger Schnellstart: `cq-quickstart-6.5.0.jar`.
* Anwendungsserver-Schnellstart: `cq-quickstart-6.5.0.war`.
* Dispatcher 4.3.2 oder höher für die verschiedenen Webserver und Plattformen. Siehe [Downloadlink](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)
* Plug-in für Eclipse IDE ([weitere Informationen und Download](/help/sites-developing/aem-eclipse.md))

* Erweiterung für Brackets-Code-Editor ([weitere Informationen und Download](/help/sites-developing/aem-brackets.md))
* Maven/Gradle-Abhängigkeiten ([Download-Link](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.5.0/))

**Sites**

* Kernkomponenten ([GitHub-Projekt](https://github.com/adobe/aem-core-wcm-components))
* We.Retail-Referenzimplementierung ([weitere Informationen](/help/sites-developing/we-retail.md))
* Maven-Projekt-Archetypen:

   * Für Full-Stack-Sites: [GitHub-Projekt](https://github.com/adobe/aem-project-archetype)
   * Für Single-Page-Apps mit React/Angular: [GitHub-Projekt](https://github.com/adobe/aem-spa-project-archetype)

* AEM Screens-Player für verschiedene Zielplattformen ([Download](https://download.macromedia.com/screens/))

* Smart Content-Sprachmodelle. Englisch ist vorinstalliert, weitere Sprachen können heruntergeladen werden.

   * [Deutsch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spanisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italienisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Französisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* AEM Modernize Tools Suite, z. B. Dialog Conversion Tool (Dialogfeldkonvertierungs-Tool) ([GitHub-Projekt](https://github.com/adobe/aem-modernize-tools))

**Assets**

* Paket zum Hinzufügen der erweiterten PDF Rasterizer-Bibliothek ([weitere Informationen](/help/assets/aem-pdf-rasterizer.md))
* Paket zum Hinzufügen von erweiterter Rohbildunterstützung ([weitere Informationen](/help/assets/camera-raw.md))

**Forms**

* [Pakete für AEM Forms-Funktionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)
* [AEM Forms OSGi Client SDK](https://repo.adobe.com/nexus/content/repositories/public/com/adobe/aemfd/aemfd-client-sdk/6.0.80/)

## Sprachen {#languages}

Die Benutzeroberfläche ist in den folgenden Sprachen verfügbar:

* Englisch
* Deutsch
* Französisch
* Spanisch
* Italienisch
* Brasilianisches Portugiesisch
* Japanisch
* Vereinfachtes Chinesisch
* Traditionelles Chinesisch (begrenzte Unterstützung)
* Koreanisch

[!DNL Experience Manager] 6.5 ist für GB18030-2005 CITS zertifiziert und kann daher den chinesischen Kodierungsstandard verwenden.

## Installieren und Aktualisieren von {#install-update}

Informationen zu Einrichtungsanforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

Detaillierte Anweisungen finden Sie unter [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md).

## Unterstützte Plattformen {#supported-platforms}

Finden Sie die vollständige Matrix der unterstützten Plattformen einschließlich Support-Level unter [AEM 6.5 Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Oracle ist auf ein LTS-Modell (Long Term Support) für Oracle-Java SE-Produkte umgestiegen. Java 9 und 10 sind Nicht-LTS-Versionen von Oracle. Siehe [Oracle Java SE-Support-Roadmap](https://www.oracle.com/technetwork/java/eol-135779.html). Adobe unterstützt LTS-Versionen von Java, damit sie nur AEM in der Produktion ausführen können. Java 11 ist die empfohlene Version für AEM 6.5.

## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe prüft kontinuierlich den Bedarf an Funktionen im Produkt und ersetzt ggf. Funktionen durch leistungsstärkere Versionen oder implementiert ausgewählte Teile neu, um besser auf zukünftige Erwartungen oder Erweiterungen vorbereitet zu sein.

Für [!DNL Adobe Experience Manager] 6.5, [lesen Sie die Liste veralteter und entfernter Funktionen](/help/release-notes/deprecated-removed-features.md). Die Seite enthält auch Vorankündigungen für Änderungen in nächster Zeit sowie wichtige Hinweise für Kunden, die frühere Versionen aktualisieren.

## Bekannte Probleme {#known-issues}

[Liste der bekannten Probleme](/help/release-notes/known-issues.md)

### Produktdownload und Support (beschränkte Websites) {#product-download-and-support-restricted-sites}

Die folgenden Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/).

* Produktaktualisierungen, Patches und Pakete für zusätzliche Funktionen auf [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

* [Kundensupport über Admin Console](https://adminconsole.adobe.com/). Weitere Informationen finden Sie unter [Neues Kundenunterstützungs-Erlebnis für Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
