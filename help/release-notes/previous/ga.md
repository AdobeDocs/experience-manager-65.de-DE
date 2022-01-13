---
title: Allgemeine Versionshinweise für [!DNL Adobe Experience Manager] 6,5
description: '[!DNL Adobe Experience Manager]Informationen zu  6.5 mit Versionshinweisen, Angaben zu neuen Funktionen und zur Installation sowie ausführlichen Änderungslisten.'
source-git-commit: 9b15215a68495a800e94a58b523e1b7baa0c0203
workflow-type: tm+mt
source-wordcount: '4696'
ht-degree: 57%

---

# Allgemeine Versionshinweise für [!DNL Adobe Experience Manager] 6,5{#general-release-notes-for-adobe-experience-manager}

## Versionshinweise {#release-information}

| Produkt | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6.5 |
| Typ | Hauptversion |
| Datum der allgemeinen Verfügbarkeit | 8. April 2019 |
| Empfohlene Updates | Siehe [AEM neuesten Aktualisierungen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de). |

### Wissenswertes {#trivia}

Der Versionszyklus für diese Version von [!DNL Adobe Experience Manager] startete am 4. April 2018, durchlief 23 Iterationen zur Qualitätssicherung und Fehlerbehebung und endete am 28. März 2019. Insgesamt wurden in dieser Version 1345 kundenbezogene Probleme behandelt, einschließlich Verbesserungen und neuer Funktionen.

[!DNL Adobe Experience Manager] 6.5 ist seit dem 8. April 2019 allgemein verfügbar.

![AEM 6.5-Anmeldebildschirm](/help/assets/assets/aem65-login-v4.png)

## Neue Funktionen {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 ist eine Upgrade-Version auf die [!DNL Adobe Experience Manager] 6.4-Codebasis. Die Software bietet neue und erweiterte Funktionen, wichtige Kundenkorrekturen, Erweiterungen für Kunden mit hoher Priorität und allgemeine Fehlerbehebungen, die auf die Produktstabilisierung ausgerichtet sind. Er umfasst auch [!DNL Adobe Experience Manager] 6.4 Service Pack veröffentlicht bis zu SP4.

Die nachstehende Liste bietet eine Übersicht, während die nachfolgenden Seiten die vollständigen Details auflisten.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Die Plattform [!DNL Adobe Experience Manager] 6.5 aufbauen auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und des Java Content Repository: Apache Jackrabbit Oak 1.10.2.

Quickstart verwendet Eclipse Jetty 9.4.15 als Servlet-Engine.

#### Java-Unterstützung  {#java-support}

* Neben der bereits unterstützten Java 8-Version wird nun auch Java 11 unterstützt..
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie unter [installieren und aktualisieren](/help/sites-deploying/custom-standalone-install.md) Abschnitt.
* Java 11- und Java 8-Wartungsupdates werden von Adobe für die Kundennutzung in AEM-bezogenen Projekten verteilt, wenn sie nicht über Oracle öffentlich verfügbar sind.

#### Java-Entwicklung {#java-development}

* Es gibt jetzt [zwei Versionen von Uberjar](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), eine empfohlene Version mit öffentlichen Schnittstellen, die nicht für die Einstellung gekennzeichnet sind, sowie eine Version, die Schnittstellen enthält, die für die Einstellung markiert sind.

#### Benutzeroberfläche {#user-interface}

Die Benutzeroberfläche wurde verbessert, um sie effizienter und anwenderfreundlicher zu gestalten.

* Neue Benutzeroberfläche für die Berechtigungsverwaltung für Benutzer und Gruppen.
* In Spaltenansichten werden nun auch nur noch die Einträge geladen, die auf dem Bildschirm sichtbar sind. Weitere Einträge werden lediglich geladen, wenn der Anwender einen Bildlauf durchführt. In der Listen- und Kartenansicht wurde so bereits seit Version 6.0 verfahren (verbessert in Version 6.4)..
* Spaltenansichten enthalten jetzt ggf. den Workflow-Status für Seiten/Assets.
* Die [Alle auswählen](/help/sites-authoring/basic-handling.md#select-all) -Aktion ist eine schnelle Möglichkeit, eine Aktion mit allen Seiten/Assets im selben Ordner auszuführen.
* Mit der Aktion [Alle auswählen](/help/sites-authoring/basic-handling.md#select-all) wird versucht, die Aktion für alle Seiten/Assets durchzuführen, nicht nur für die geladenen Elemente. Ein Warndialogfeld wird angezeigt, wenn die Aktion nicht für die Verarbeitung von Massenaktionen aktualisiert wurde.

>[!CAUTION]
>
>Adobe plant keine weiteren Verbesserungen an der klassischen UI. In AEM 6.5 ist die klassische UI integriert und Kunden, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird. [Weitere Informationen](/help/sites-deploying/ui-recommendations.md).

#### Suche und Indizierung {#indexing-and-search}

* Die Suche in Oak unterstützt jetzt dynamische Facetten. Beispielsweise zeigt die Filterleiste bei der Asset-Suche die geschätzte Ergebnismenge an.
* QueryBuilder wurde erweitert, um Ergebnisse mit dynamischen Facetten bereitzustellen.

#### Aktualisierung {#upgrade}

* Kunden mit AEM 6.2, 6.3 und 6.4 können direkt auf AEM 6.5 aktualisieren. Kunden, die 5.x oder 6.0/6.1 verwenden und ein direktes Upgrade durchführen möchten, müssen zunächst auf 6.4 und dann auf 6.5 aktualisieren oder durch eine Übertragung der Inhalte zwischen Instanzen sofort auf AEM 6.5 aktualisieren.
* Das Aktualisierungsverfahren bleibt in 6.5 größtenteils unverändert.
* Wir unterstützen weiterhin die in 6.4 eingeführten Funktionen „Abwärtskompatibilität“, „Bewertung der Aktualisierungskomplexität“ und „Nachhaltige Aktualisierungen“. Für diese Bereiche wurden nach Bedarf versionsspezifische Aktualisierungen durchgeführt.
* Das Pattern Detector-Paket wurde vereinfacht und es gibt ein Paket, das Aktualisierungen auf 6.5 für die verfügbaren Quellversionen bewertet.
* Weitere Informationen zum Upgrade-Verfahren finden Sie unter [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md).

#### Projekte und Workflows {#projects-and-workflows}

* Der in 6.4 eingeführte neue Workflow-Modell-Editor wurde verbessert und umfasst jetzt mehr Vorgänge wie Kopieren und Veröffentlichen, Variablenunterstützung in Workflow-Schritten und erweiterte Funktionen `OR` und `AND` teilt.

#### Repository {#repository}

* Die Foundation-Komponente von Adobe Experience Manager 6.5 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java Content Repository Apache Jackrabbit Oak 1.10.2.
* Einen Überblick über behobene Probleme finden Sie unter [Apache Jackrabbit Oak Jira v. 1.10.0](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.10.1](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) und [Apache Jackrabbit Oak Jira v. 1.10.2](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt).

>[!CAUTION]
>
>Aufgrund der neuen Version von Oak Segment Tar, die mit AEM 6.3 eingeführt wurde, ist eine Repository-Migration erforderlich. Dieser Schritt ist obligatorisch, wenn Sie eine Aktualisierung von einer älteren TarMK-Version durchführen oder von einem anderen Persistenztyp zum neuen Segment-TAR-Format wechseln möchten. Weitere Informationen zu den Vorteilen des neuen Segment-TAR-Formats finden Sie unter [Migration auf Oak-Segment-TAR – Häufig gestellte Fragen (FAQ)](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

#### OSGI {#osgi}

* OSGi Promises- und Converter-Dienstprogrammbibliotheken wurden hinzugefügt.

#### Sicherheit {#security}

* Passwörter von Administratoren laufen nun ab.

#### Webserver {#web-server}

* Die Quickstart-Verteilung verwendet Eclipse Jetty 9.4.15 als Servlet-Engine (AEM 6.4 im Lieferumfang von 9.3.22 enthalten).

### [!DNL Experience Manager] Sites {#experience-manager-sites}

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

#### Screens-Add-on {#screens-add-on}

Sie können Erlebnisse effizient entwickeln, bereitstellen und optimieren, und zwar auf allen digitalen Displays, ob interaktiver Kiosk oder digitale Beschilderung (Digital Signage).

* Vereinheitlichung von Erlebnissen und Inhalten, online und offline, mit verbesserter Wiederverwendung von Inhalten
* Optimierte Erstellungs- und Genehmigungs-/Veröffentlichungsworkflows mit Unterstützung für Launches
* Bearbeitung und Bereitstellung von ansprechenden, interaktiven Erlebnissen mit dem SPA-Editor
* Verwenden von Launches zum Planen künftiger Inhaltsänderungen für Signaturinhalte
* Es sind getaktete Wiedergaben in einem Sequenzkanal möglich.
* Automatische Erstellung einer Projektstruktur mithilfe einer Quelldatei, z. B. einer Excel-Arbeitsmappe
* Erweiterte Medienplayer-Unterstützung für zuverlässigen Online- und Offlinebetrieb (Smart Sync), skalierbar sogar für größte Signage-Netzwerke
* Ortsbezogene Personalisierung oder Konfiguration von datenbasierten Inhalten durch Nutzung dynamischer Platzhalter
* Einheitliche Einblicke durch die Adobe Analytics-Integration in AEM Screens Player

Weitere Informationen zu Änderungen an AEM Screens finden Sie in den Versionshinweisen im Abschnitt [AEM Screens-Benutzerhandbuch](https://docs.adobe.com/content/help/de-DE/experience-manager-screens/user-guide/aem-screens-introduction.html).

#### Komponenten- und Vorlagenentwicklung {#component-amp-template-development}

* Maven-Projekt-Archetyp 18+ für neue Projekte, siehe [Versionshinweise zu Github](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* Single-Page-App-Maven-Projekt-Archetyp 1.0.6+ für neue Projekte, siehe [Versionshinweise zu Github](https://github.com/adobe/aem-spa-project-archetype/releases).
* HTL Version 1.4, siehe [Versionshinweise zu GitHub](https://github.com/adobe/htl-spec/releases/tag/1.4).

   * &quot;in&quot;-Operator für Zeichenfolgen, Arrays und Objekte:

      ```html
      ${'a' in 'abc’}
      ${100 in myArray}
      ${'a' in myObject}
      ```

   * Variablendeklarationen mit data-sly-set :
      `<sly data-sly-set.title="${currentPage.title}"/>${title}`

   * Listen- und Wiederholungsparameter: begin, step, end:
      `<h2 data-sly-repeat="${currentPage.listChildren @ begin = 1, step=2}">${item.title}</h2>`

   * Kennungen für data-sly-unwrap:

      ```html
      <div data-sly-unwrap.isUnwrapped="${myCondition || myOtherCondition}">
      text <span data-sly-test="${isUnwrapped}>is unwrapped</code>
      </div>
      ```

   * Unterstützung negativer Zahlen

* Kernkomponenten 2.3.2+, siehe [Versionshinweise zu Github](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Rastersystem für Layout-Container, siehe [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Clientlib Manager: Google Closure Compiler standardmäßig zur Minimierung von JavaScript-Clientlibs (alter Standard war Yahoo YUI) und Google Closure Compiler zur Version v20190121 aktualisiert
* Vorlagen-Editor und Richtlinien:

   * Erstellen und bearbeiten Sie Vorlagen für Einzelseiten-Apps, die das JS-SDK verwenden (auch als SPA Editor bezeichnet)

* Referenz-Website We.Retail 4.0, siehe [Versionshinweise zu GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).
* Toolkit zum Aktualisieren vorhandener Sites, um die neuesten Editor-Funktionen zu nutzen, siehe [GitHub-Repository](https://github.com/adobe/aem-modernize-tools)

>[!CAUTION]
>
>AEM enthält Version 1.12.4 der jQuery-Bibliothek, um eine maximale Kompatibilität mit vorhandenem benutzerdefiniertem Code zu gewährleisten. Adobe hat Änderungen vorgenommen, um bekannte Sicherheitsprobleme zu beheben.

#### Site-Administration {#site-administration}

* Die Leiste [Verweis](/help/sites-authoring/author-environment-tools.md#references) enthält einen neuen Abschnitt, in dem interne, auf die ausgewählte Seite verweisende Links aufgelistet werden. Dies ist nützlich, wenn eine Seite offline geschaltet oder gelöscht werden soll. So können Sie sehen, welche Seiten vor der Offlineschaltung angepasst werden müssen.
* Die [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) enthält eine neue Workflowspalte, die den Status anzeigt, wenn sich die Seite aktuell in einem Workflow befindet.
* In den [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) können Sie nun nach vorhandenen Elementen suchen, wenn Sie der Seite eine Miniaturansicht zuweisen (Registerkarte „Miniatur“).

#### Seiteneditor {#page-editor}

* Der Seiten-Editor ermöglicht kontextbezogenes Bearbeiten und Erstellen von Single-Page-Apps-Erlebnissen mit clientseitigen React- und Angular-Komponenten, die das JS-SDK verwenden (auch als SPA-Editor bezeichnet).
* Der Strukturvorlagen-Modus wird nur angezeigt, wenn für die Seite eine Strukturvorlagen-Seite konfiguriert ist.

#### Inhaltsfragmente und Editor {#content-fragments-amp-editor}

* Mit der neuen Leiste [Anmerkungen](/help/assets/content-fragments/content-fragments-variations.md#viewing-editing-deleting-annotations) im Inhaltsfragmente-Editor können Sie allgemeine Kommentare erstellen und Kommentare innerhalb des Texts anzeigen (erscheinen ebenfalls in der Leiste „Timeline“).
* Möglichkeit, den Standard-Inhaltstyp eines mehrzeiligen Textelements in einem [Inhaltsfragmentmodell](/help/assets/content-fragments/content-fragments-models.md) zu einfachem Text, Rich-Text oder Markdown
* [Kommentare/Anmerkungen](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment) können per Textauswahl in RTE (Vollbildansicht) hinzugefügt werden.
* In der Leiste „Verweis“ können Versionen von Inhaltsfragmenten nebeneinander [verglichen](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) werden.
* Der heruntergeladene Bericht eines Assets zeigt nun die entsprechenden Inhaltsfragmente an.
* Durch /api.json kann [Unterstützung für Inhaltsfragmente zur Assets-HTTP-API](/help/assets/assets-api-content-fragments.md) hinzugefügt werden. Es sind APIs zum Erstellen, Aktualisieren, Lesen und Löschen von Inhaltsfragmenten vorhanden.

#### Experience Fragments {#experience-fragments}

* Die Indizierung von [Experience Fragments](/help/sites-authoring/experience-fragments.md) wurde verbessert, sodass deren Inhalte bei der Suche nach Seiten mit diesen Experience Fragments gefunden werden.
* Mit der Option [In Ziel exportieren](/help/sites-administering/experience-fragments-target.md) können Sie nun das Experience Fragment als JSON (Standard ist HTML) oder beides senden.

#### Übersetzung {#translation}

* Übersetzungsprojekte lassen sich durch Projekt-Master einfacher erstellen.
* Vereinfachen Sie die Ausführung von Übersetzungsprojekten, indem Sie Übersetzungsaufträge standardmäßig auf den Status &quot;Genehmigt&quot;setzen.
* Sie können zulassen, dass übersetzte Seiten mit Änderungen aus dem Translation Memory von Drittanbietern aktualisiert werden.
* Übersetzungsaufträge können in das JSON-Format exportiert werden.
* Aktualisierung der Microsoft-Übersetzungsintegration für die Verwendung der V3-API

#### Multi-Site-Management (MSM) {#multi-site-management-msm}

* Bei Rollout-Konfigurationen, die PushOnModify verwenden, ist die Handhabung des Seitenverschiebungsvorgangs besser, um inkonsistente Zustände zu vermeiden
* Durch Erstellen einer neuen Seite in der Live Copy-Struktur wird nun standardmäßig eine eigenständige Seite generiert.
* Verwenden Sie MSM-Funktionen in Einzelseiten-Apps, die das JS-SDK verwenden (auch als SPA Editor bezeichnet).

#### Launches {#launches}

* Neben neuer Prüf- und Genehmigungsworkflows für Launches ist es möglich, den Promotion-Schritt auf genehmigte Launch-Seiten zu beschränken.
* In der [UI wurde eine Option zum Löschen des Launch gleich nach dem Promotion-Schritt](/help/sites-authoring/launches-promoting.md#promoting-launch-pages) hinzugefügt.

#### Content-Targeting und Simulation {#content-targeting-simulation}

* Die ContextHub-Datenebene und die clientseitige JavaScript-Regel-Engine wurden so aktualisiert, dass standardmäßig jQuery 3 verwendet wird.

#### AEM und Adobe Target {#aem-amp-adobe-target}

>[!CAUTION]
>
>Aktuell:
>
>* Nur `at.js 1.x` wird unterstützt, wenn Sie Adobe Target als Targeting-Engine in AEM Aktivitätskonsole verwenden.
>
>* Beide `at.js. 1.x` und `at.js 2.x` werden unterstützt, wenn Sie den Experience Fragment-Export in Target verwenden und Aktivitäten in der Target-Konsole ausführen.


* Zur Adobe Target-Integration kann nun die Target Standard-API verwendet werden. Frühere Versionen von AEM verwenden die Target Classic-HTTP-API, die jetzt nicht mehr unterstützt wird.
* Adobe Target `mbox.js` Version 63 ist enthalten. Adobe empfiehlt dringend, die Implementierung auf `at.js` v1.x.
* `at.js` Version 1.5.0 ist jetzt enthalten. Adobe empfiehlt die Verwendung von [Adobe Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) der `at.js` v1.x in die Site ein.

#### AEM und Adobe Analytics {#aem-amp-adobe-analytics}

* `s_code.js` H.27.5 ist enthalten. Adobe empfiehlt, die Implementierung auf `AppMeasurement.js`
* `AppMeasurement.js` Version 1.8.0 ist enthalten. Adobe empfiehlt die Verwendung von [Adobe Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) , um AppMeasurement.js auf der Site bereitzustellen.

#### AEM und Handel {#aem-commerce}

Die Verbesserungen des Commerce Integration Framework befinden sich seit AEM 6.4 in einem schnelleren Versionszyklus. [Weitere Informationen finden Sie hier](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/docs.html).

#### Communities-Add-on {#communities-add-on}

Informationen dazu, wie Sie die neueste Version erhalten, finden Sie in der Dokumentation unter dem Abschnitt zur [Bereitstellung von Communities](/help/communities/deploy-communities.md).

##### Verbesserte Community-Aktivierung {#enhancements-to-community-engagement}

**@Mentions-Unterstützung**
In AEM Communities können registrierte Benutzer jetzt andere registrierte Mitglieder mit Tags versehen (erwähnen), um deren Aufmerksamkeit zu erregen, und zwar in benutzergenerierten Inhalten. Die getaggten (erwähnten) Mitglieder werden dann benachrichtigt, und zwar mit einem Deep-Link zu den entsprechenden anwendergenerierten Inhalten. Die Anwender können allerdings Web- und E-Mail-Benachrichtigungen deaktivieren/aktivieren.

![@Mentions-Unterstützung](/help/release-notes/assets/at-mentions.png)

Community-Anwender müssen nicht nach ihrem Vornamen, Nachnamen oder Anwendernamen suchen, um festzustellen, ob sich jemand an sie gewendet hat oder ein anderer ihre Hilfe braucht. Außerdem können UGC-Autoren Antwort von bestimmten registrierten Anwendern anfordern, die am besten dazu geeignet sind, ein Problem zu lösen und Feedback zu geben.

Die Community-Administratoren müssen **Erwähnung aktivieren** auf Community-Komponenten verwenden, um registrierten Benutzern die Verwendung der Funktionalität für diese Komponenten zu ermöglichen.

**Gruppennachrichten**

Registrierte Community-Mitglieder können nun eine einzige E-Mail verfassen und diese direkt per Massenversand an Gruppen senden, anstatt dieselbe Nachricht einzeln an die jeweiligen Gruppenmitglieder verschicken zu müssen. In [Gruppennachrichten](/help/communities/configure-messaging.md)aktivieren Sie beide Instanzen von [Messaging Operations-Dienst](/help/communities/messaging.md#group-messaging).

![Gruppennachricht](/help/release-notes/assets/group-messaging.png)

##### Verbesserte Massenmoderation {#enhancements-to-bulk-moderation}

Benutzerdefinierte Filter bei der Massenmoderation

[Benutzerdefinierte Filter](/help/communities/moderation.md#custom-filters) kann jetzt entwickelt und der Benutzeroberfläche für die Massenmoderation hinzugefügt werden.

Ein in [Github](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) vorhandenes [Beispielprojekt](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) zeigt das Filtern nach Tags. Dieses Projekt kann als Grundlage zum Entwickeln analoger benutzerdefinierter Filter verwendet werden.

![Benutzerdefinierte Filter](/help/release-notes/assets/custom-tag-filter.png)

**Listenansicht bei Massenmoderation**

Eine neue Listenansicht mit verbesserter UI wurde im Bereich für Massenmoderation bereitgestellt, um Einträge zu anwendergenerierten Inhalten anzuzeigen.

![Massenmoderation in der Listenansicht](/help/release-notes/assets/list-view-moderation.png)

##### Verbesserte Site- und Gruppenverwaltung {#enhancements-to-site-and-group-management}

**Autorseitige Site- und Gruppenadministratoren**

Communities ermöglicht ab AEM 6.5 das dezentrale Verwalten (und Managen) verschiedener Community-Sites und Gruppen/verschachtelter Gruppen. Organisationen, die mehrere Community-Sites und verschachtelte Gruppen hosten, können nun beim Erstellen der Site (Gruppe) autorseitig Mitglieder für Administratorrollen auswählen.

![Site-Administrator](/help/release-notes/assets/site-admin.png)

Site-Administratoren können eine Gruppe auf jeder Hierarchieebene erstellen und zu Standardadministratoren werden. Diese Administratoren können später von anderen Gruppenadministratoren entfernt werden. Gruppenadministratoren können ihre Gruppe G1 verwalten und eine unter G1 verschachtelte Untergruppe erstellen.

##### Verbesserte Aktivierung {#enhancements-to-enablement}

**SCORM 2017.1-Unterstützung**

Die Aktivierungsfunktion von AEM 6.5 Communities unterstützt das Shareable Content Object Reference Model [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) Motor.

* Unterstützung der Tastaturnavigation bei Aktivierungskomponenten
* Aktivierungskomponenten (z. B. Katalog- und Kurswiedergabe, Zuweisungen, Dateibibliothek) in AEM Communities unterstützen die Tastaturnavigation für eine verbesserte Barrierefreiheit.

##### Weitere Verbesserungen {#other-enhancements}

* Unterstützung für Solr 7
* AEM 6.5 Communities unterstützt die Apache Solr 7.0-Version der Suchplattform bei der Einrichtung von MSRP und DSRP.

### [!DNL Experience Manager Assets] {#experience-manager-assets}

AEM 6.5 beinhaltet die folgenden neuen Funktionen und Erweiterungen mit denen AEM-Anwender, DAM-Anwender und Anwender mit entsprechenden Kreativ- sowie Marketingfunktionen ihre Produktivität steigern können.

#### Integration mit [!DNL Adobe Creative Cloud] und kreative Workflows {#integration-with-adobe-creative-cloud-and-creative-workflows}

[!DNL Adobe Experience Manager] bietet verschiedene Möglichkeiten, um zu integrieren und Assets für die Verwendung in Workflows freizugeben, in denen Kreativ-, Marketing- oder Businessteams eng zusammenarbeiten. [!DNL Adobe Creative Cloud] [!DNL Experience Manager] 6.5 ermöglicht eine noch bessere Integration und stärkere Optimierung. Das Ergebnis: mehr Chancen und die Verbesserung vorhandener Methoden.

Erfahren Sie mehr über die spezifischen Funktionen und Integrationen von [!DNL Experience Manager] 6.5, die Sie verwenden können, um Ihre Anwendungsfälle mit hoher Inhaltsgeschwindigkeit optimal zu unterstützen.

##### Adobe Asset Link {#aal}

[!DNL Adobe Asset Link] stärkt die Zusammenarbeit zwischen Kreativen und Marketingexperten bei der Inhaltserstellung. Kreative können auf Inhalte zugreifen, die in gespeichert sind [!DNL Experience Manager Assets], ohne die Apps zu verlassen, mit denen sie am besten vertraut sind. Kreative können Assets über das In-App-Bedienfeld in nahtlos durchsuchen, suchen, auschecken und einchecken. [!DNL Adobe Photoshop], [!DNL Adobe Illustrator]und [!DNL Adobe InDesign] Apps.

[!DNL Adobe Asset Link] ist Teil von [Creative Cloud für Unternehmen](https://www.adobe.com/creativecloud/business/enterprise.html) anbieten. Weitere Informationen dazu, einschließlich der erforderlichen Konfiguration Ihrer [!DNL Experience Manager] Bereitstellung, siehe [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html).

![Suchen nach Assets in Adobe Photoshop](/help/release-notes/assets/asset_search_photoshop.png)

##### [!DNL Adobe Stock] Integration {#stock}

Ihr Unternehmen kann seine [!DNL Adobe Stock] Enterprise-Plan [!DNL Experience Manager Assets] , um sicherzustellen, dass lizenzierte Assets für kreative und Marketing-Projekte allgemein verfügbar sind. Sie können schnell finden, eine Vorschau anzeigen und eine Lizenz [!DNL Adobe Stock] Assets, die in Experience Manager gespeichert werden, unter Verwendung der leistungsstarken DAM-Funktionen von [!DNL Experience Manager].

Der [!DNL Adobe Stock]-Service bietet Designern und Unternehmen Zugang zu Millionen von hochwertigen, kuratierten und gebührenfreien Fotos, Vektorgrafiken, Illustrationen, Videos, Vorlagen und 3D-Assets für sämtliche Kreativprojekte. 

Weitere Informationen finden Sie unter [Verwenden von Adobe Stock-Assets in Experience Manager Assets](/help/assets/aem-assets-adobe-stock.md).

![Adobe Stock-Bild und -Lizenz in Experience Manager Assets in der Vorschau anzeigen](/help/release-notes/assets/stock_image_preview_license_options.png)

*Abbildung: Vorschau [!DNL Adobe Stock] Bild und Lizenz von innerhalb [!DNL Experience Manager Assets].*

![Suchen und Filtern lizenzierter Adobe Stock-Bilder in Experience Manager](/help/release-notes/assets/aem-search-filters2.jpg)

*Abbildung: Lizenzierte Benutzer suchen und filtern [!DNL Adobe Stock] Bilder in [!DNL Experience Manager].*

##### Dynamische Verweise in [!DNL Adobe InDesign] {#dynamic-references-in-indesign}

[!DNL Experience Manager Assets] verwendet in [!DNL Adobe InDesign] -Dateien dynamisch sind. Die Verweise werden automatisch aktualisiert, wenn die referenzierten Assets im Repository verschoben werden. Weitere Informationen finden Sie unter [Verwalten von ebenenübergreifenden Assets](/help/assets/managing-linked-subassets.md).

#### Brand Portal-Funktionen {#brand-portal-capabilities}

[!DNL Experience Manager Assets Brand Portal]Mit können Sie problemlos genehmigte Assets abrufen, diese wirksam kontrollieren und sicher und geräteübergreifend an externe Anbieter/Agenturen und interne Geschäftsanwender verteilen. Brand Portal ermöglicht eine effizientere Asset-Freigabe sowie schnellere Time-to-Market für Assets und verringert das Risiko von Nicht-Compliance und unbefugtem Zugriff.

Weitere Informationen finden Sie unter [Neue Funktionen in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=de).

#### Connected Assets {#connectedassets}

In großen Unternehmen kann die zur Erstellung von Websites erforderliche Infrastruktur verteilt werden. Manchmal befinden sich die Funktionen zur Website-Erstellung und die hierfür benötigten digitalen Assets in unterschiedlichen Silos.

[!DNL Experience Manager Sites] bietet Funktionen zum Erstellen von Webseiten, während das Digital Asset Management (DAM)-System ist, das die für Websites erforderlichen Assets bereitstellt. [!DNL Experience Manager Assets] [!DNL Experience Manager] unterstützt nun dank Integration von [!DNL Sites] und [!DNL Assets] das obige Nutzungsszenario. Siehe [Konfigurieren und Verwenden der Funktion &quot;Connected Assets&quot;](/help/assets/use-assets-across-connected-assets-instances.md).

![Ziehen eines Assets aus einem [!DNL Experience Manager] Implementierung auf einer [!DNL Sites] Seite einer anderen [!DNL Experience Manager] Implementierung](/help/release-notes/assets/connected-assets-drag-and-drop-only.gif)

*Abbildung: Ziehen eines Assets aus einem [!DNL Experience Manager] Implementierung auf einer [!DNL Sites] auf einer anderen Seite [!DNL Experience Manager] Implementierung.*

#### Dynamic Media {#dynamic-media}

[!DNL Dynamic Media] bietet ein verbessertes Rich-Media-Authoring und -Bereitstellen in [!DNL Experience Manager Assets] um hochmoderne Erlebnisse zu fördern, die interaktiv und personalisiert sind. Durch das Hochladen eines einzelnen hochwertigen primären Assets und die Verwendung des erweiterten Cloud-Renderings und Viewers von Adobe können Sie jede Kombination von Ausgabeformaten sofort bereitstellen, um die Medienstrategie Ihres Unternehmens zu unterstützen.

Weitere Informationen zu neuen [!DNL Dynamic Media] Funktionen, siehe [Versionshinweise zu Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/release-notes/s7rn2017.html).

##### 360-Grad-Videounterstützung {#video-support}

Verwalten Sie Ihre 360-Grad-Videodateien direkt in [!DNL Experience Manager] Verwendung der neuesten Viewer zur Bereitstellung von VR-Erlebnissen für Desktops, Mobilgeräte und VR-Headsets. Weitere Informationen finden Sie unter [Verwenden von 360-Grad-Videos](/help/assets/360-video.md).

##### Benutzerdefinierte Videominiaturen {#custom-video-thumbnails}

Sie können nun die Miniaturen für Ihre Video-Assets mithilfe von Frames aus dem Video selbst oder aus anderen im DAM gespeicherten Inhalten anpassen. Weitere Anweisungen finden Sie unter [Über Videominiaturen](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

##### Verbesserte Barrierefreiheit {#accessibility-enhancements}

[!DNL Dynamic Media] Viewer unterstützen jetzt erweiterte Barrierefreiheitsfunktionen wie Aria-Unterstützung, Bildschirmlesehilfen und Alternativtext. Weitere Informationen finden Sie unter [Viewer-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

#### Verbessertes Sucherlebnis {#experience-enhancement-for-searching}

[!DNL Experience Manager] Ab 6.5 können Marketer die gewünschten Assets schneller von der Suchergebnisseite aus finden. Die Suchfacetten werden mit der Anzahl der Assets aktualisiert, noch bevor der Suchfilter angewendet wird. Durch Anzeige der erwarteten Anzahl im Filter können Benutzer effizient durch Suchergebnisse navigieren. Weitere Informationen finden Sie unter [Suchen von Assets in Experience Manager](/help/assets/search-assets.md).

![Anzeigen der Asset-Anzahl ohne Filterung der Suchergebnisse in Suchfacetten](/help/assets/assets/asset_search_results_in_facets_filters.png)

*Abbildung: Anzeigen der Anzahl der Assets ohne Filterung der Suchergebnisse in Suchfacetten.*

#### Größere Anwenderfreundlichkeit {#usability-enhancement}

Sie können jetzt alle geladenen Assets in einem Ordner oder aus einem Suchergebnis in einem Schritt auswählen. Dies ermöglicht eine schnelle Verwaltung aller Assets. Mit dem Kontrollkästchen werden alle Assets ausgewählt, die dem Szenario entsprechen, z. B. ein Suchergebnis, und nicht nur die Assets, die in der [!DNL Experience Manager] -Schnittstelle.

![Verwenden Sie die Option Alle auswählen , um alle geladenen Assets mit einem Klick auszuwählen.](/help/release-notes/assets/select-all-in-aem-assets.gif)

*Abbildung: Verwenden Sie die Option Alle auswählen , um alle geladenen Assets mit einem Klick auszuwählen.*

#### Verbesserte Metadaten {#metadata-enhancements}

[!DNL Assets] können Sie Metadatenschemata für Asset-Ordner erstellen, die das Layout und die Metadaten definieren, die auf den Seiten mit Ordnereigenschaften angezeigt werden. Sie können jetzt ein Ordner-Metadatenschema einem vorhandenen Ordner oder beim Erstellen eines Ordners zuweisen. Weitere Informationen finden Sie unter [Ordner-Metadatenschema](/help/assets/metadata-config.md#folder-metadata-schema).

Beim Festlegen kaskadierender Metadaten können die Optionen zur Laufzeit aus einer JSON-Datei geladen werden, anstatt sie manuell in das Formular einzugeben. Weitere Informationen finden Sie unter [Kaskadierende Metadaten](/help/assets/metadata-schemas.md#cascading-metadata).

#### Verbessertes Reporting {#reporting-enhancements}

Die Inhaltsfragmente und Linkfreigaben sind jetzt im heruntergeladenen Bericht enthalten. Weitere Informationen finden Sie unter [Asset-Berichte](/help/assets/asset-reports.md).

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

Siehe [Zusammenfassung der neuen Funktionen und Verbesserungen in AEM 6.5 Forms](/help/forms/using/whats-new.md) für Informationen zu neuen und verbesserten Funktionen und Dokumentationsressourcen.

### [!DNL Experience Manager Livefyre] {#experience-manager-livefyre}

Livefyre lässt sich in AEM 6.5-Instanzen integrieren. Siehe [Integration von Livefyre in AEM](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/livefyre.html).

### Kundenorientierte Entwicklung nutzen {#leverage-customer-focused-development}

Adobe verwendet ein kundenorientiertes Entwicklungsmodell, das es den Kunden ermöglicht, zu allen Phasen des Entwicklungsprozesses von der Spezifikation bis zur Entwicklung und zum Test beizutragen. Unser Dank geht an alle beteiligten Kunden und Partner in diesem Prozess.

Adobe hält die erforderlichen Vorgehensweisen und Prozesse bereit, um die Erfassung, Priorisierung und Verfolgung kundenorientierter Fehlerbehebungs- und Verbesserungsanforderungsentwicklung zu ermöglichen. Die [Support-Portal für Experience Manager](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=de#support) ist in das Adobe Enhancement and Defect Tracking System integriert. Kundenfragen werden nach Möglichkeit vom Support-Team identifiziert und beantwortet. Bei einer Weiterleitung an Forschung und Entwicklung werden alle Kundeninformationen erfasst und zu Priorisierungs- und Berichterstellungszwecken verwendet. Bei der Entwicklung werden gebührenpflichtiger Support, Garantieprobleme und kundenbezahlte Verbesserungen Priorität eingeräumt.

Dieser Prozess der Priorisierung hat zu mehr als 750 kundenorientierten Änderungen geführt, die in AEM 6.5 vorgenommen wurden.

## Liste der Dateien, die Teil der Version sind {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Eigenständiger Schnellstart: `cq-quickstart-6.5.0.jar`.
* Anwendungsserver-Schnellstart: `cq-quickstart-6.5.0.war`.
* Dispatcher 4.3.2 oder höher für die verschiedenen Webserver und Plattformen. Siehe [Downloadlink](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html)
* Plug-in für Eclipse IDE ([weitere Informationen und Download](/help/sites-developing/aem-eclipse.md))

* Erweiterung für Brackets-Code-Editor ([weitere Informationen und Download](/help/sites-developing/aem-brackets.md))
* Maven/Gradle-Abhängigkeiten ([Download-Link](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.0/))

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

**Formulare**

* [Pakete für AEM Forms-Funktionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
* [AEM Forms OSGi Client SDK](https://repo1.maven.org/maven2/com/adobe/aemfd/aemfd-client-sdk/)

## Sprachen {#languages}

Die Benutzeroberfläche ist in den folgenden Sprachen verfügbar:

* Englisch
* Deutsch
* Französisch
* Spanisch
* Italienisch
* Brasilianisches  Portugiesisch
* Japanisch
* Vereinfachtes Chinesisch
* Traditionelles Chinesisch (begrenzte Unterstützung)
* Koreanisch

[!DNL Experience Manager] 6.5 ist für GB18030-2005 CITS zertifiziert und kann daher den chinesischen Kodierungsstandard verwenden.

## Installieren und Aktualisieren {#install-update}

Informationen zu Einrichtungsanforderungen finden Sie unter [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

Detaillierte Anweisungen finden Sie unter [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md).

## Unterstützte Plattformen {#supported-platforms}

Finden Sie die vollständige Matrix der unterstützten Plattformen, einschließlich der Support-Ebene auf [AEM 6.5 Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Oracle ist auf ein LTS-Modell (Long Term Support) für Oracle-Java SE-Produkte umgestiegen. Java 9 und 10 sind Nicht-LTS-Versionen von Oracle. Siehe [Oracle Java SE-Support-Roadmap](https://www.oracle.com/technetwork/java/eol-135779.html). Adobe unterstützt LTS-Versionen von Java, damit sie nur AEM in der Produktion ausführen können. Java 11 ist die empfohlene Version für AEM 6.5.

## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe prüft kontinuierlich den Bedarf an Funktionen im Produkt und ersetzt ggf. Funktionen durch leistungsstärkere Versionen oder implementiert ausgewählte Teile neu, um besser auf zukünftige Erwartungen oder Erweiterungen vorbereitet zu sein.

Für [!DNL Adobe Experience Manager] 6,5 [Liste veralteter und entfernter Funktionen lesen](/help/release-notes/deprecated-removed-features.md). Die Seite enthält auch Vorankündigungen für Änderungen in nächster Zeit sowie wichtige Hinweise für Kunden, die frühere Versionen aktualisieren.

## Bekannte Probleme {#known-issues}

### Plattform {#platform}

* Es wird ein Problem gemeldet, bei dem CRX-Quickstart und sein Inhalt gelöscht werden.

   Stellen Sie bei jeder dieser Aktionen sicher, dass die -Eigenschaft `htmllibmanager.fileSystemOutputCacheLocation` ist keine leere Zeichenfolge:

   1. Bei einem Aufruf von `/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true`.
   2. Aktualisieren auf AEM 6.5.
   3. &quot;Lazy Content Migration&quot;auf AEM 6.5 ausführen.

   A [Wissensdatenbank](https://helpx.adobe.com/experience-manager/kb/avoid-crx-quickstart-deletion-in-aem-6-5.html) Dieser Artikel ist mit weiteren Details und der Problemumgehung für dieses Problem verfügbar.

* Wenn Sie JDK 11 mit AEM 6.5-Instanz verwenden, werden einige der Seiten nach der Bereitstellung einiger Pakete möglicherweise als leer angezeigt. Die folgende Fehlermeldung wird in der Protokolldatei angezeigt:

   ```java
   *ERROR* [OsgiInstallerImpl] org.apache.sling.scripting.sightly bundle org.apache.sling.scripting.sightly:1.1.2.1_4_0 (558)[org.apache.sling.scripting.sightly.impl.engine.extension.use.JavaUseProvider(3345)] : Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl)
   java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl
   ```

So beheben Sie diesen Fehler:

1. Halten Sie die AEM-Instanz an. Navigieren Sie zu `<aem_server_path_on_server>crx-quickstart\conf` und öffnen Sie die `sling.properties` -Datei. Adobe empfiehlt, eine Sicherungskopie dieser Datei zu erstellen.

1. Suchen Sie nach `org.osgi.framework.bootdelegation=`. Hinzufügen `jdk.internal.reflect,jdk.internal.reflect.*` -Eigenschaften, um das Ergebnis anzuzeigen.

```java
org.osgi.framework.bootdelegation=sun.*,com.sun.*,jdk.internal.reflect,jdk.internal.reflect.*
```

1. Speichern Sie die Datei und starten Sie die AEM-Instanz neu.

## Sites {#sites}

* **Arbeiten mit Seitenversionen**: Wenn eine Seite verschoben wurde, können Sie keine Vorschau mehr für Versionen anzeigen, die vor dem Verschieben vorgenommen wurden.

### Assets {#assets}

* **Suchen:** Die Suche führt nicht zu Rückgaben, wenn die Suchzeichenfolge vorangestellte Leerzeichen enthält ([OAK-4786](https://issues.apache.org/jira/browse/OAK-4786))
* **Ordner-Metadatenschema**: Nach Hinzufügen einer Auswahlschaltfläche entsprechen das ID-Feld und das Wertfeld nicht den Erwartungen und die Löschfunktion kann nicht verwendet werden (CQ-4261144)
* Beim Umbenennen eines Assets ist es nicht möglich, ein Leerzeichen im Asset-Namen zu verwenden (CQ-4266403)

### Formulare {#forms}

* Wenn AEM Forms auf dem Linux-Betriebssystem installiert ist, funktioniert Digital Signature mit Hardware Security Module nicht. (CQ-4266721)
* (Nur AEM Forms auf WebSphere) Die Option **Forms-Workflow**> **Aufgabensuche** gibt kein Ergebnis zurück, wenn Sie nach einem **Administrator** anhand des **Anwendernamens** suchen (CQ-4266457)

* AEM Forms kann TIF- und TIFF-Dateien mit JPEG-Komprimierung nicht in PDF-Dokumente konvertieren. (CQ-4265972)
* Die Optionen **AEM Forms-Asset-Scanner** und **Letter in interaktive Kommunikation – Migration** funktionieren nicht auf der Seite **AEM Forms-Migration** (CQ-4266572)

* (Nur JBoss 7) Wenn Sie von einer früheren Version auf AEM 6.5 Forms aktualisieren und die vorherige Version über Prozesse (.lca) verfügte, die eine Kopie des standardmäßigen Sende- oder Renderprozesses erstellt und verwendet haben, kann HTML5 Forms mit solchen Prozessen (.lca) die erforderlichen Aktionen nicht durchführen. (CQ-4243928)
* Wenn in einem adaptiven Formular ein Formulardatenmodell-Service vom Regel-Editor aufgerufen wird, um die Werte der Bildauswahlkomponente dynamisch zu aktualisieren, werden die Werte der Bildauswahlkomponente nicht aktualisiert (CQ-4254754)
* Das Installationsprogramm für AEM Forms Designer erfordert die 32-Bit-Version von [Visual C++ Redistributable Runtime Package 2012](https://support.microsoft.com/de-de/help/2977003/the-latest-supported-visual-c-downloads) und [Visual C++ Redistributable Runtime Packages 2013](https://support.microsoft.com/de-de/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). Stellen Sie sicher, dass die oben genannten Redistributable Runtime Packages vor Installationsbeginn installiert sind (CQ-4265668)

* PDF Generator unterstützt keine Authentifizierung mit Smart Card.  Wenn ein Administrator die Gruppenrichtlinie aktiviert `Interactive Logon: Require Smart card` auf einem Windows-Server werden alle PDF Generator-Benutzer invalidiert.

* Wenn ein adaptives Formular so konfiguriert ist, dass die Werte einer Komponente dynamisch aktualisiert werden, und auf die Veröffentlichungsinstanz, die das Formular hostet, über den Dispatcher zugegriffen wird, kann die Funktion zum dynamischen Aktualisieren von Feldwerten nicht mehr verwendet werden. Um das Problem zu beheben, öffnen Sie in der Veröffentlichungsinstanz CRXDE, navigieren Sie zu `/libs/fd/af/runtime/clientlibs/guideChartReducer`und erstellen Sie die unten aufgeführte Eigenschaft.

   * Name: allowProxy
   * Typ: Boolean
   * Value: True
   * Protected: False
   * Mandatory: False
   * Multiple: False
   * Automatisch erstellt: False

   Durch diese Eigenschaft können Client-Bibliotheken unter dem Laufzeitordner auf Proxys zugreifen (CQ-4268679)

* Wenn AEM Forms gestartet wird, wird die `SAX Security Manager could not be setup` angezeigt.
* Wenn Sie eine mit AEM Forms Document Security geschützte PDF auf einem Apple iOS oder iPadOS mit Adobe Acrobat Reader-Version 20.10.00 öffnen.
* Fehlerkorrektur – Wenn Sie ein Formular mit einem standardmäßigen HTML-Upload-Feld von einem Apple iOS-Gerät senden, wird der Inhalt der Datei jetzt zuverlässig gesendet. Apple iOS 15.1 bietet eine Korrektur für das Problem.

## Produktdownload und Support (beschränkte Websites) {#product-download-and-support-restricted-sites}

Die folgenden Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe Account Manager.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/).

* Produktaktualisierungen, Patches und Pakete für zusätzliche Funktionen in [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

* [Kundensupport über Admin Console](https://adminconsole.adobe.com/). Weitere Informationen finden Sie unter [Neues Adobe-Supporterlebnis](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
