---
title: Versionshinweise zu AEM Sites
description: Spezifische Versionshinweise für Adobe Experience Manager 6.5 Sites
uuid: 676ead61-3d97-4f23-b616-c647d590bc8f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: f82e9bd4-f7b6-492d-8e02-593e74fa1058
docset: aem65
translation-type: tm+mt
source-git-commit: e3f32b526d8a619b8bacfc85e7dce4a7bf5d23a7

---


# Versionshinweise zu AEM Sites{#aem-sites-release-notes}

Im Folgenden sind die Verbesserungen für AEM Sites 6.5 aufgeführt:

## Komponenten- und Vorlagenentwicklung {#component-amp-template-development}

* Maven-Projekt-Archetyp 18+ für neue Projekte, siehe [Versionshinweise zu Github](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* Single-Page-App-Maven-Projekt-Archetyp 1.0.6+ für neue Projekte, siehe [Versionshinweise zu Github](https://github.com/adobe/aem-spa-project-archetype/releases).
* HTL Version 1.4, siehe [Versionshinweise zu GitHub](https://github.com/adobe/htl-spec/releases/tag/1.4).

   * &quot;in&quot;-Operator für Zeichenfolgen, Arrays und Objekte:

      ```
      ${'a' in 'abc’}
       ${100 in myArray}
       ${'a' in myObject}
      ```

   * Variablendeklarationen mit Datensatz:
      `<sly data-sly-set.title="${currentPage.title}"/>${title}`

   * Liste- und Wiederholungskontrollparameter: begin, step, end:
      `<h2 data-sly-repeat="${currentPage.listChildren @ begin = 1, step=2}">${item.title}</h2>`

   * Bezeichner für die datenbasierte Aufhebung:

      ```
      <div data-sly-unwrap.isUnwrapped="${myCondition || myOtherCondition}">
       text <span data-sly-test="${isUnwrapped}>is unwrapped</code>
       </div>
      ```

   * Unterstützung negativer Zahlen

* Kernkomponenten 2.3.2+, siehe [Versionshinweise zu Github](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Rastersystem für Layout-Container, siehe [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Clientlib Manager: Google Closure Compiler standardmäßig auf Minimierung von JavaScript clientlibs festgelegt (früher war Yahoo YUI) und Google Closure Compiler auf Version v20190121 aktualisiert
* Vorlagen-Editor und Richtlinien:

   * Erstellen und bearbeiten Sie Vorlagen für einseitige Apps, die das JS SDK verwenden (auch SPA Editor genannt)

* Referenz-Website We.Retail 4.0, siehe [Versionshinweise zu GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).
* Toolkit to upgrade existing sites to leverage the latest editor capabilities, see [Github repository](https://github.com/adobe/aem-modernize-tools)

>[!CAUTION]
>
>AEM enthält Version 1.12.4 der jQuery-Bibliothek, um eine maximale Kompatibilität mit vorhandenem benutzerdefiniertem Code zu gewährleisten. Adobe hat Änderungen vorgenommen, um bekannte Sicherheitsprobleme zu beheben.

## Site-Administration {#site-administration}

* Die Leiste [Verweis](/help/sites-authoring/author-environment-tools.md#references) enthält einen neuen Abschnitt, in dem interne, auf die ausgewählte Seite verweisende Links aufgelistet werden. Dies ist nützlich, wenn eine Seite offline geschaltet oder gelöscht werden soll. So können Sie sehen, welche Seiten vor der Offlineschaltung angepasst werden müssen.
* Die [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) enthält eine neue Workflowspalte, die den Status anzeigt, wenn sich die Seite aktuell in einem Workflow befindet.
* In den [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) können Sie nun nach vorhandenen Elementen suchen, wenn Sie der Seite eine Miniaturansicht zuweisen (Registerkarte „Miniatur“).

## Seiten-Editor {#page-editor}

* Der Seiten-Editor ermöglicht kontextbezogenes Bearbeiten und Erstellen von Single-Page-Apps-Erlebnissen mit clientseitigen React- und Angular-Komponenten, die das JS-SDK verwenden (auch als SPA-Editor bezeichnet).
* Der Strukturvorlagen-Modus wird nur angezeigt, wenn für die Seite eine Strukturvorlagen-Seite konfiguriert ist.

## Inhaltsfragmente und Editor {#content-fragments-amp-editor}

* Mit der neuen Leiste [Anmerkungen](/help/assets/content-fragments-variations.md#viewing-editing-deleting-annotations) im Inhaltsfragmente-Editor können Sie allgemeine Kommentare erstellen und Kommentare innerhalb des Texts anzeigen (erscheinen ebenfalls in der Leiste „Timeline“).
* Ability to set the default content type of a multi-line text element in a [Content Fragment model](/help/assets/content-fragments-models.md) to simple text, rich text or markdown
* [Kommentare/Anmerkungen](/help/assets/content-fragments-variations.md#annotating-a-content-fragment) können per Textauswahl in RTE (Vollbildansicht) hinzugefügt werden.
* In der Leiste „Verweis“ können Versionen von Inhaltsfragmenten nebeneinander [verglichen](/help/assets/content-fragments-managing.md#comparing-fragment-versions) werden.
* Der heruntergeladene Bericht eines Assets zeigt nun die entsprechenden Inhaltsfragmente an.
* Durch /api.json kann [Unterstützung für Inhaltsfragmente zur Assets-HTTP-API](/help/assets/assets-api-content-fragments.md) hinzugefügt werden. Es sind APIs zum Erstellen, Aktualisieren, Lesen und Löschen von Inhaltsfragmenten vorhanden.

## Experience Fragments {#experience-fragments}

* Die Indizierung von [Experience Fragments](/help/sites-authoring/experience-fragments.md) wurde verbessert, sodass deren Inhalte bei der Suche nach Seiten mit diesen Experience Fragments gefunden werden.
* Mit der Option [In Ziel exportieren](/help/sites-administering/experience-fragments-target.md) können Sie nun das Experience Fragment als JSON (Standard ist HTML) oder beides senden.

## Übersetzung {#translation}

* Übersetzungsprojekte lassen sich durch Projekt-Master einfacher erstellen.
* Vereinfachen Sie die Ausführung von Übersetzungsprojekten, indem Sie Übersetzungsaufträge standardmäßig auf den Status &quot;Genehmigt&quot;setzen.
* Sie können zulassen, dass übersetzte Seiten mit Änderungen aus dem Translation Memory von Drittanbietern aktualisiert werden.
* Übersetzungsaufträge können in das JSON-Format exportiert werden.
* Aktualisierung der Microsoft Translation-Integration für die Verwendung der V3-API

## Multi-Site-Management (MSM) {#multi-site-management-msm}

* Bei Rollout-Konfigurationen, die PushOnModify verwenden, sollten Sie den Vorgang zum Verschieben der Seite besser handhaben, um einen inkonsistenten Status zu vermeiden
* Durch Erstellen einer neuen Seite in der Live Copy-Struktur wird nun standardmäßig eine eigenständige Seite generiert.
* Verwenden Sie MSM-Funktionen in einseitigen Apps, die das JS SDK verwenden (auch SPA Editor genannt)

## Launches {#launches}

* Neben neuer Prüf- und Genehmigungsworkflows für Launches ist es möglich, den Promotion-Schritt auf genehmigte Launch-Seiten zu beschränken.
* In der [UI wurde eine Option zum Löschen des Launch gleich nach dem Promotion-Schritt](/help/sites-authoring/launches-promoting.md#promoting-launch-pages) hinzugefügt.

## Content-Targeting und Simulation {#content-targeting-simulation}

* Die ContextHub-Datenebene und die clientseitige JavaScript-Regel-Engine wurden so aktualisiert, dass standardmäßig jQuery 3 verwendet wird.

## AEM und Adobe Zielgruppe {#aem-amp-adobe-target}

>[!CAUTION]
>
>at.js 2.x wird zum Zeitpunkt der Veröffentlichung von AEM 6.5 nicht in AEM unterstützt. Aktualisieren Sie auf die neueste Version von at.js 1.x.

* Zur Adobe Target-Integration kann nun die Target Standard-API verwendet werden. Frühere Versionen von AEM verwenden die Zielgruppe Classic HTTP API, die jetzt nicht mehr unterstützt wird.
* Adobe Target `mbox.js` version 63 is included. Adobe strongly recommends to switch implementation to `at.js` v1.x.
* `at.js` Version 1.5.0 ist jetzt enthalten. Adobe recommends that you use [Adobe Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) to provision `at.js` v1.x into the site.

## AEM und Adobe Analytics {#aem-amp-adobe-analytics}

* `s_code.js` H.27.5 ist enthalten. Adobe empfiehlt, dass Sie die Implementierung auf `AppMeasurement.js`
* `AppMeasurement.js` Version 1.8.0 ist enthalten. Adobe recommends to use [Adobe Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) to provision AppMeasurement.js into the site.

## AEM und Commerce {#aem-commerce}

Improvements to the Commerce Integration Framework are on a faster release cycle since AEM 6.4. [Learn more here](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/docs.html).

## Communities-Add-on {#communities-add-on}

Weitere Informationen hierzu finden Sie auf der [Seite mit Versionshinweisen für AEM Communities](../release-notes/communities-release-notes.md).

## Screens-Add-on {#screens-add-on}

* Verwenden von Starts zur Planung künftiger Inhaltsänderungen für Signaturinhalte
* Es sind getaktete Wiedergaben in einem Sequenzkanal möglich.
* Sie können Projektstrukturen anhand einer Quelldatei, z. B. einer Excel-Tabelle, automatisch erstellen lassen.

For more details on changes to AEM Screens - see the Release Notes in the [AEM Screens User Guide](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html).
