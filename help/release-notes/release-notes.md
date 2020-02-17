---
title: Allgemeine Versionshinweise zu Adobe Experience Manager 6.5
description: Informationen zu Adobe Experience Manager 6.5 mit Versionshinweisen, Angaben zu neuen Funktionen und zur Installation sowie ausführlichen Änderungslisten.
uuid: b916624e-9486-4391-8c6f-cb4045e78490
contentOwner: chuesler
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 7d3ceccb-4f00-4e11-9c9f-6de46a455e02
docset: aem65
translation-type: tm+mt
source-git-commit: 57bad4e74b2dfd9e389643bfe58ef25564c5c545

---


# Allgemeine Versionshinweise zu Adobe Experience Manager 6.5{#general-release-notes-for-adobe-experience-manager}

## Versionshinweise {#release-information}

<table>
 <tbody>
  <tr>
   <th>Produkt</th>
   <td>Adobe Experience Manager<br /> </td>
  </tr>
  <tr>
   <th>Version</th>
   <td>6.5</td>
  </tr>
  <tr>
   <th>Typ</th>
   <td>Hauptversion</td>
  </tr>
  <tr>
   <th>Datum der allgemeinen Verfügbarkeit</th>
   <td>8. April 2019<br /> </td>
  </tr>
  <tr>
   <th>Empfohlene Updates</th>
   <td>See <a href="https://helpx.adobe.com/experience-manager/aem-releases-updates.html">AEM Releases and Updates</a></td>
  </tr>
 </tbody>
</table>

### Wissenswertes {#trivia}

Der Veröffentlichungszyklus für diese Version von Adobe Experience Manager startete am 4. April 2018, durchlief 23 Iterationen zur Qualitätssicherung und Fehlerbehebung und endete am 28. März 2019. Insgesamt wurden in dieser Version 1345 kundenbezogene Probleme behandelt, einschließlich Verbesserungen und neuer Funktionen.

Adobe Experience Manager 6.5 ist seit dem 8. April 2019 allgemein verfügbar.

![AEM 6.5-Anmeldebildschirm](/help/assets/assets/aem65-login-v4.png)

## Neuerungen {#what-s-new}

Adobe Experience Manager 6.5 ist eine Upgradeversion für die Codebasis von Adobe Experience Manager 6.4. Die Software bietet neue und erweiterte Funktionen, wichtige Kundenkorrekturen, Erweiterungen für Kunden mit hoher Priorität und allgemeine Fehlerbehebungen, die auf die Produktstabilisierung ausgerichtet sind. Darüber hinaus enthält Adobe Experience Manager 6.4 Service Pack-Versionen bis SP4.

Die nachstehende Liste bietet eine Übersicht - während die nachfolgenden Seiten die vollständigen Details auflisten.

### Experience Manager Foundation {#experience-manager-foundation}

Vollständige Liste der Änderungen in [AEM Foundation](/help/release-notes/wcm-platform.md).

Die Plattform von Adobe Experience Manager 6.5 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java Content Repository Apache Jackrabbit Oak 1.10.2.

Quickstart verwendet Eclipse Jetty 9.4.15 als Servlet-Engine.

#### Java-Unterstützung  {#java-support}

* Neben der bereits unterstützten Java 8-Version wird nun auch Java 11 unterstützt.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Java 11- und Java 8-Wartungsupdates werden Kunden von Adobe zur Nutzung in AEM-bezogenen Projekten bereitgestellt, sofern diese nicht bei Oracle öffentlich zugänglich sind.

#### Java-Entwicklung {#java-development}

* There are now [two versions of the Uberjar](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), a recommended version with public interfaces that are not marked for deprecation, as well as a version that includes interfaces marked for deprecation.

#### Benutzeroberfläche {#user-interface}

Die Benutzeroberfläche wurde verbessert, um sie effizienter und anwenderfreundlicher zu gestalten.

* Neue Benutzeroberfläche zur Verwaltung von Berechtigungen für Benutzer und Gruppen
* In Spaltenansichten werden nun auch nur noch die Einträge geladen, die auf dem Bildschirm sichtbar sind. Weitere Einträge werden lediglich geladen, wenn der Anwender einen Bildlauf durchführt. In der Listen- und Kartenansicht wurde so bereits seit Version 6.0 verfahren (verbessert in Version 6.4).
* Spaltenansichten enthalten nun ggf. den Workflowstatus für Seiten/Assets.
* Die Aktion [Alle auswählen](/help/sites-authoring/basic-handling.md#select-all) ist eine schnelle Möglichkeit, eine Aktion mit allen Seiten/Assets im selben Ordner auszuführen.
* Mit der Aktion [Alle auswählen](/help/sites-authoring/basic-handling.md#select-all) wird versucht, die Aktion für alle Seiten/Assets durchzuführen, nicht nur für die geladenen Elemente. Es wird ein Warndialogfeld angezeigt, wenn die Aktion nicht für Massenaktionen aktualisiert wurde.

>[!CAUTION]
>
>Adobe plant keine weiteren Verbesserungen an der klassischen UI. In AEM 6.5 ist die klassische UI integriert und Kunden, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird. [Weitere Informationen](/help/sites-deploying/ui-recommendations.md).

#### Suche und Indizierung {#search-indexing}

* Die Suche in Oak unterstützt jetzt dynamische Facetten. Beispielsweise zeigt die Filterleiste in der Elementsuche die geschätzte Ergebnismenge an.
* QueryBuilder wurde erweitert und liefert nun Ergebnisse mit dynamischen Facetten.

#### Aktualisierung {#upgrade}

* Kunden mit AEM 6.2, 6.3 und 6.4 können direkt auf AEM 6.5 aktualisieren. Kunden, die 5.x oder 6.0/6.1 verwenden und ein direktes Upgrade durchführen möchten, müssen zunächst auf 6.4 und dann auf 6.5 aktualisieren oder durch eine Übertragung der Inhalte zwischen Instanzen sofort auf AEM 6.5 aktualisieren.

#### Projekte und Workflows {#projects-and-workflows}

* Der neue in Version 6.4 eingeführte Workflow-Modell-Editor wurde verbessert. Neben einer größeren Anzahl von Vorgängen wie Kopieren und Veröffentlichen werden nun Variablen in Workflowschritten unterstützt. Außerdem wurden ODER- und UND-Teilungen optimiert.

### Experience Manager Sites {#experience-manager-sites}

Vollständige Liste der Änderungen in [AEM Sites und Add-ons](/help/release-notes/sites.md).

#### Managed-Single-Page-Apps {#managed-single-page-apps}

Der Seiten-Editor ermöglicht nun kontextbezogene Inhaltsbearbeitungen und Erstell-/Layoutvorgänge in clientseitig gerenderter Erlebnissen (auch als [SPA-Editor](/help/sites-developing/spa-architecture.md) bekannt). Vorhandene Single-Page-Apps, die auf dem JavaScript-Framework React oder Angular basieren, können mit AEM SJ SDK erweitert werden, damit sie von Experten bearbeitet werden können.

Die zunächst als Teil von AEM 6.4 SP2 bereitgestellte SPA-Unterstützung bietet in AEM 6.5 folgende Funktionen:

* Bearbeiten und Konfigurieren der bearbeitbaren AEM-Teile der SPA mit dem Vorlagen-Editor
* Verwenden Sie Multi-Site-Management, um SPA-Erlebnisse mit Land-, Franchise- oder White-Label zu erstellen.

#### Headless-Content-Management {#headless-content-management}

Mit AEM können Inhalte in verschiedenen Formaten und aus verschiedenen Ebenen des Stapels bereitgestellt werden. Einige von ihnen sind durch das [Sling GET-](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) und [POST-Servlet](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) bereits seit 2008 verfügbar. Content Services ([Sling Model Exporter](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/sling-model-exporter-tutorial-develop.html)) wurden in AEM 6.3 eingeführt und sind die von AEM SJ SDK eingesetzte Hydrationsmethode für Single-Page-Apps. Die [HTTP-API für Assets](/help/assets/mac-api-assets.md) ist eine für AEM 6.5 erweiterte CRUD-API. 

Neue Funktionen der HTTP-API:

* Neuerdings [Unterstützung von Inhaltsfragmenten in der HTTP-API für Assets](/help/assets/assets-api-content-fragments.md) zum Erstellen, Aktualisieren, Lesen und Löschen von Fragmenten
* Offenlegung von Inhaltsfragmentlisten über Content Services mit der [Kernkomponenten-Inhaltsfragmentliste](https://opensource.adobe.com/aem-core-wcm-components/library/content-fragment-list.html)
* [Kernkomponentenbibliothek](https://opensource.adobe.com/aem-core-wcm-components/library.html) zur Anzeige der Content Services-JSON-Standardausgabe für jede Komponente

#### Screens-Add-on {#screens-add-on}

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

For more details on changes to AEM Screens - see the Release Notes in the [AEM Screens User Guide](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html).

### Experience Manager Assets {#experience-manager-assets}

Full list of changes in [AEM 6.5 Assets release notes](/help/release-notes/assets.md).

AEM 6.5 beinhaltet die folgenden neuen Funktionen und Erweiterungen mit denen AEM-Anwender, DAM-Anwender und Anwender mit entsprechenden Kreativ- sowie Marketingfunktionen ihre Produktivität steigern können.

#### Integrieren in Adobe Creative Cloud {#integration-with-adobe-creative-cloud}

Neu hinzugekommen ist [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html). Damit profitieren kreative Anwender, die mit Adobe Creative Cloud-Anwendungen wie Photoshop, Illustrator und InDesign arbeiten, von In-App-Erlebnissen – für eine optimierte Zusammenarbeit zwischen Kreativen und Marketern bei der Inhaltserstellung. Die AEM-Desktop-App unterstützt weiterhin die Anforderungen von Benutzern, die mit Assets von AEM auf dem Desktop arbeiten und dabei beliebige Dateitypen und Desktopanwendungen verwenden.

Darüber hinaus ist AEM in Adobe Stock integriert und ermöglicht so die Suche, Vorschau, Lizenzierung und Speicherung von Adobe Stock-Assets direkt über die AEM-Web-UI.

![Bedienfeld „Asset-Link“ in Photoshop](/help/assets/assets/aem65-assetlink-photoshop.png)

#### Connected Assets {#connected-assets}

Die Funktion &quot;Connected Assets&quot;ist auf größere Bereitstellungen mit einer Reihe von AEM-Sites ausgerichtet, bei denen Assets von einer zentralen AEM Assets DAM-Bereitstellung genutzt werden müssen. Dadurch wird nicht nur die Governance im Zusammenhang mit zentral verwalteten Assets verbessert, sondern auch eine hocheffiziente Bereitstellung von Assets für verschiedene Sites-Implementierungen ermöglicht.

### Dynamic Media {#dynamic-media}

Dynamic Media bietet eine erweiterte Rich-Media-Erstellung und -Bereitstellung in AEM Assets für beeindruckend intensive, personalisierte Erlebnisse. Mit einem einzigen hochwertigen Master-Asset können Sie unsere erweiterte Cloudrendering-Funktion „Smartes Zuschneiden“ sowie marktführende Viewer nutzen, um faszinierende Erlebnisse mit branchenführender Leistung zu erzielen.

Zu den neuen Funktionen zählen:

* Unterstützung für 360°-Videos und VR-Headsets
* Benutzerdefinierte Videominiaturen
* Verbesserte Unterstützung für Barrierefreiheit
* Schutz vor Verknüpfung

#### Anwendererlebnis und Suche {#user-experience-and-search}

Wichtige Verbesserungen ermöglichen hier zweierlei: eine schnellere Asset-Suche durch dynamische Suchfacetten und eine effizientere Verwaltung mehrerer Assets durch gleichzeitige Auswahl aller Assets aus beliebigen Ordnern oder Suchergebnissen.

### Adobe Experience Manager Forms {#experience-manager-forms}

AEM 6.5 wurde um zahlreiche neue Funktionen und Erweiterungen ergänzt. Hier einige der Highlights:

* Transaktionsberichte zur Verfolgung der Anzahl gesendeter Formulare, verarbeiteter Dokumente und gerenderter Dokumente
* Verbesserte Nutzung interaktiver Kommunikation
* Cloudbasierte digitale Signaturen in adaptiven Formularen
* Integration adaptiver Formulare und interaktiver Kommunikation in eine AEM Sites-Single-Page-App (SPA).
* Unterstützung für Variablen in AEM-Workflows
* Unterstützung von Datenanzeigemustern bei interaktiver Kommunikation
* Sortierung adaptiver Formulare und interaktiver Kommunikationstabellen
* Automatische Validierung von Eingabedaten in Formulardatenmodellen

See the [Summary of new features and enhancements in AEM 6.5 Forms](/help/forms/using/whats-new.md) for information about new and improved features and documentation resources.

### Experience Manager Communities {#communitiesreleasenotes}

AEM 6.5 bietet verschiedene neue Funktionen und Erweiterungen für Communities. Highlights dieser Version:

* Unterstützung beim Tagging registrierter Mitglieder (@mention) während der Erstellung anwendergenerierter Inhalte
* Unterstützung direkter Massennachrichten an Mitgliedergruppen
* Benutzerdefinierte Filter, entwickelt und hinzugefügt zur UI für Massenmoderation; A [sample project](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) demonstrating filtering by tags can be used as a base to develop analogous custom filters.
* Neue Listenansicht mit verbesserter UI für die Massenmoderation
* Möglichkeit zur Zuweisung verschiedener Administratoren für unterschiedliche Community-Sites und verschachtelte Gruppen (statt eines einzigen Community-Administrators)
* Enablement functionality of AEM 6.5 Communities supports [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) engine.
* Verbesserte Barrierefreiheit durch unterstützte Tastaturnavigation bei Aktivierungskomponenten
* Apache Solr 7.0-Unterstützung beim Einrichten von MSRP und DSRP

For detailed list of changes, see [AEM 6.5 Communities release notes](/help/release-notes/communities-release-notes.md).

### Experience Manager Livefyre {#experience-manager-livefyre}

Livefyre lässt sich in AEM 6.5-Instanzen integrieren. Weitere Informationen zur Integration von Livefyre in AEM finden Sie auf den folgenden Seiten:

* [Livefyre-Integration](https://helpx.adobe.com/experience-manager/6-4/help/sites-administering/livefyre.html)

### Kundenorientierte Entwicklung nutzen {#leverage-customer-focused-development}

Adobe verwendet ein kundenorientiertes Entwicklungsmodell, das es den Kunden ermöglicht, zu allen Phasen des Entwicklungsprozesses von der Spezifikation bis zur Entwicklung und zum Test beizutragen. Unser Dank geht an alle beteiligten Kunden und Partner in diesem Prozess.

Adobe hält die erforderlichen Vorgehensweisen und Prozesse bereit, um die Erfassung, Priorisierung und Verfolgung kundenorientierter Fehlerbehebungs- und Verbesserungsanforderungsentwicklung zu ermöglichen. The [Adobe Marketing Cloud Support Portal](https://helpx.adobe.com/marketing-cloud/contact-support.html) is integrated with the Adobe Enhancement &amp; Defect Tracking System. Kundenprobleme werden, wenn möglich, gemeinsam mit dem Kundendienst identifiziert und gelöst. Bei einer Weiterleitung an Forschung und Entwicklung werden alle Kundeninformationen erfasst und zu Priorisierungs- und Berichterstellungszwecken verwendet. Bei der Entwicklung haben bezahlte Support- und Garantieprobleme sowie bezahlte Kundenerweiterungen Priorität.

Dieser Prozess der Priorisierung hat zu mehr als 750 kundenorientierten Änderungen geführt, die in AEM 6.5 vorgenommen wurden.

## Liste der Dateien, die Teil der Version sind {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Standalone-Quickstart: cq-quickstart-6.5.0.jar
* Anwendungsserver-Schnellstart: cq-quickstart-6.5.0.war
* Dispatcher 4.3.2 oder höher für verschiedene Webserver und Plattformen ([Downloadlink](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html))
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

   * [Deutsch](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spanisch](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italienisch](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Französisch](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-fr)

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

Experience Manager 6.5 ist für GB18030-2005 CITS zertifiziert und kann daher den chinesischen Kodierungsstandard verwenden.

## Installieren und Aktualisieren {#install-update}

Setup-Anforderungen finden Sie in den [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

Detaillierte Anweisungen finden Sie in der [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md).

## Unterstützte Plattformen {#supported-platforms}

Sie finden die gesamte Matrix für unterstützte Plattformen einschließlich Informationen zur Unterstützungsebene finden unter [Technische Anforderungen für AEM 6.5](/help/sites-deploying/technical-requirements.md).

Oak MicroKernel for Oak MicroKernel for

>[!NOTE]
>
>Oracle ist auf ein LTS-Modell (Long Term Support) für Oracle Java SE-Produkte umgestiegen. Java 9 and 10 are non-LTS releases by Oracle (see [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe unterstützt nur LTS-Releases von Java beim Ausführen von AEM in einer Produktionsumgebung. Daher ist Java 11 die empfohlene Version für AEM 6.5.

## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe prüft kontinuierlich den Bedarf an Funktionen im Produkt und ersetzt ggf. Funktionen durch leistungsstärkere Versionen oder implementiert ausgewählte Teile neu, um besser auf zukünftige Erwartungen oder Erweiterungen vorbereitet zu sein.

Für Adobe Experience Manager 6.5 sollten Sie die [Liste veralteter und entfernter Funktionen lesen](/help/release-notes/deprecated-removed-features.md). Die Seite enthält auch Vorankündigungen für Änderungen in nächster Zeit sowie wichtige Hinweise für Kunden, die frühere Versionen aktualisieren.

## Bekannte Probleme {#known-issues}

[Liste der bekannten Probleme](/help/release-notes/known-issues.md)

### Produktdownload und Support (beschränkte Websites) {#product-download-and-support-restricted-sites}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [](https://daycare.day.com) [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)

* [Kundensupport unter daycare.day.com](https://daycare.day.com)

