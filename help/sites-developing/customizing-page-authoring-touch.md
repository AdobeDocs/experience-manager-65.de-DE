---
title: Anpassung des Seiten-Authorings
seo-title: Anpassung des Seiten-Authorings
description: AEM bietet verschiedene Möglichkeiten zum Anpassen der Funktionsweise des Seiten-Authorings.
seo-description: AEM bietet verschiedene Möglichkeiten zum Anpassen der Funktionsweise des Seiten-Authorings.
uuid: 9dc72d98-c5ff-4a00-b367-688ccf896526
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6825dcd6-fa75-4410-b6b2-e7bd4a391224
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Anpassung des Seiten-Authorings{#customizing-page-authoring}

>[!CAUTION]
>
>In diesem Dokument wird beschrieben, wie Sie das Seiten-Authoring in der modernen Touch-optimierten Benutzeroberfläche anpassen. Es gilt nicht für die klassische Benutzeroberfläche.

AEM bietet verschiedene Möglichkeiten zum Anpassen der Funktionsweise des Seiten-Authorings (und der [Konsolen](/help/sites-developing/customizing-consoles-touch.md)) Ihrer Authoring-Instanz.

* Clientlibs

   Mit clientlibs können Sie die Standardimplementierung erweitern, um neue Funktionen zu realisieren, während Sie die Standardfunktionen, -objekte und -methoden wiederverwenden. Beim Anpassen können Sie Ihre eigene clientlib unter `/apps.` Die neue clientlib muss:

   * die Authoring-clientlib`cq.authoring.editor.sites.page`   als Abhängigkeit aufweisen
   * der entsprechenden `cq.authoring.editor.sites.page.hook`-Kategorie angehören

* Überlagerungen

   Overlays are based on node definitions and allow you to overlay the standard functionality (in `/libs`) with your own customized functionality (in `/apps`). Wenn Sie eine Überlagerung erstellen, ist keine identische Kopie des Originals erforderlich, da [sling resource merger](/help/sites-developing/sling-resource-merger.md) Vererbung ermöglicht.

>[!NOTE]
>
>Weitere Informationen finden Sie in der [JS-Dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/jsdoc/ui-touch/editor-core/index.html).

Diese Funktionen können auf verschiedene Arten verwendet werden, um die Seiten-Authoring-Funktionen in Ihrer AEM-Instanz zu erweitern. Unten behandeln wir allgemein eine Auswahl von Möglichkeiten.

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* Verwenden und Erstellen von [Clientbibliotheken](/help/sites-developing/clientlibs.md).
>* Verwenden und Erstellen von [Überlagerungen](/help/sites-developing/overlays.md).
>* [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html)
>* [Struktur der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-structure.md) für Details zu den strukturellen Bereichen, die beim Seiten-Authoring verwendet werden.
>
>
Dieses Thema wird auch in der [AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html)-Sitzung [Anpassung der Benutzeroberfläche für AEM 6.0](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-user-interface-customization-for-aem6.html) behandelt.

>[!CAUTION]
>
>You ***must*** not change anything in the `/libs` path.
>
>This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may well be overwritten when you apply either a hotfix or feature pack).
>
>Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
>
>1. Recreate the required item (i.e. as it exists in `/libs`) under `/apps`
>1. Make any changes within `/apps`


## Neue Ebene hinzufügen (Modus) {#add-new-layer-mode}

Wenn Sie eine Seite bearbeiten, gibt es verschiedene verfügbare [Modi](/help/sites-authoring/author-environment-tools.md#page-modes). Diese Modi werden mithilfe von [Ebenen](/help/sites-developing/touch-ui-structure.md#layer) implementiert. Sie ermöglichen Zugriff auf verschiedene Funktionen für denselben Seiteninhalt. Die Standardebenen sind: Bearbeiten, Vorschau, Anmerken, Entwickler und Targeting.

### Ebenenbeispiel: Live Copy-Status {#layer-example-live-copy-status}

Eine Standard-AEM-Instanz stellt die MSM-Ebene bereit. Diese Ebene greift auf Daten für [Multi-Site-Management](/help/sites-administering/msm.md) zu und hebt sie in der Ebene hervor.

To see it in action you may edit any [We.Retail language copy](/help/sites-developing/we-retail-globalized-site-structure.md) page (or any other live copy page) and select the **Live Copy Status** mode.

Sie finden die MSM-Ebenendefinition (als Referenz) in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codebeispiel {#code-sample}

Dies ist ein Beispielpaket, das die Erstellung einer neuen Ebene (Modus) zeigt. Hier ist es eine neue Ebene zur MSM-Ansicht.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Open aem-authoring-new-layer-mode project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode/archive/master.zip) herunter

## Hinzufügen einer neuen Auswahl-Kategorie zum Asset-Browser {#add-new-selection-category-to-asset-browser}

Der Asset-Browser zeigt Assets verschiedener Arten und Kategorien (z. B. Bilder, Dokumente usw.). Die Assets können auch anhand dieser Asset-Kategorien gefiltert werden.

### Codebeispiel {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` ist ein Beispielpaket, das das Hinzufügen einer neuen Gruppe zur Asset-Suche demonstriert. Dieses Beispiel verbindet sich mit dem öffentlichen Stream von [Flickr](https://www.flickr.com) und zeigt ihn im Seitenbereich.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Open aem-authoring-extension-assetfinder-flickr project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr/archive/master.zip) herunter

## Filtern von Ressourcen {#filtering-resources}

Beim Authoring von Seiten muss der Benutzer oft aus verschiedenen Ressourcen (z. B. Seiten, Komponenten, Assets usw.) auswählen. Dabei kann beispielsweise eine Liste verwendet werden, aus der der Autor ein Element auswählen muss.

Um die Größe der Liste (auf die relevanten Einsatzszenarios) zu beschränken, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Wenn z. B. der Benutzer durch die [`pathbrowser`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)[-Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui)-Komponente den Pfad zu einer bestimmten Ressource auswählen kann, können die gezeigten Pfade auf folgende Art gefiltert werden:

* Implement the custom predicate by implementing [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/predicate/package-summary.html) interface.
* Geben Sie einen Namen für die Eigenschaft an und verwenden Sie diesen Namen, wenn Sie `pathbrowser` verwenden.

Weitere Details zum Erstellen einer benutzerdefinierten Eigenschaft finden Sie in [diesem Artikel](/help/sites-developing/implementing-custom-predicate-evaluator.md).

>[!NOTE]
>
>Die Implementierung einer benutzerdefinierten Eigenschaft durch die Implementierung der Schnittstelle `com.day.cq.commons.predicate.AbstractNodePredicate` funktioniert auch in der klassischen Benutzeroberfläche.
>
>In diesem [Knowledge Base-Artikel](https://helpx.adobe.com/experience-manager/using/creating-custom-cq-tree.html) finden Sie ein Beispiel für die Implementierung einer benutzerdefinierten Eigenschaft in der klassischen Benutzeroberfläche.

## Hinzufügen neuer Aktionen zu Komponenten-Symbolleisten {#add-new-action-to-a-component-toolbar}

Jede Komponente hat (in der Regel) eine Symbolleiste, die Zugriff auf eine Reihe von Aktionen bietet, die mit dieser Komponente durchgeführt werden können.

### Codebeispiel {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` ist ein Beispielpaket, das die Erstellung einer benutzerdefinierten Symbolleistenaktion zum Rendern von Komponenten demonstriert.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Öffnen Sie das Projekt aem-authoring-extension-toolbar-screenshot auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot/archive/master.zip) herunter

## Hinzufügen eines neuen Editors für Bearbeitung im Kontext {#add-new-in-place-editor}

### Standardmäßiger Editor für Bearbeitung im Kontext {#standard-in-place-editor}

Bei der Standardinstallation von AEM:

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js`

   Enthält Definitionen der verschiedenen verfügbaren Editoren.

1. Es gibt eine Verknüpfung zwischen dem Editor und den einzelnen Ressourcenarten (wie Komponenten), die ihn verwenden können:

   * `cq:inplaceEditing`

      Beispiel:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * property: `editorType`

            Defines the type of inline editor that will be used when the in-place editing is triggered for that component; e.g. `text`, `textimage`, `image`, `title`.

1. Weitere Einstellungen des Editors können mit einem `config`-Knoten, der Konfigurationen enthält, sowie einem weiteren `plugin`-Knoten mit notwendigen Plug-in-Konfigurationsdetails konfiguriert werden.

   Das folgende Beispiel zeigt die Definition von Seitenverhältnissen für das Bildbeschneidungs-Plug-in der image-Komponente. Beachten Sie, dass aufgrund der Möglichkeit von begrenzten Bildschirmgrößen die Beschneidungsverhältnisse in den Vollbild-Editor verlegt wurden und nur dort sichtbar sind.

   ```xml
   <cq:inplaceEditing
           jcr:primaryType="cq:InplaceEditingConfig"
           active="{Boolean}true"
           editorType="image">
           <config jcr:primaryType="nt:unstructured">
               <plugins jcr:primaryType="nt:unstructured">
                   <crop jcr:primaryType="nt:unstructured">
                       <aspectRatios jcr:primaryType="nt:unstructured">
                           <_x0031_6-10
                               jcr:primaryType="nt:unstructured"
                               name="16 : 10"
                               ratio="0.625"/>
                       </aspectRatios>
                   </crop>
               </plugins>
           </config>
   </cq:inplaceEditing>
   ```

   >[!CAUTION]
   >
   >Beachten Sie, dass Beschneidungsverhältnisse, die durch die Eigenschaft `ratio` definiert werden, in AEM als **Höhe/Breite** definiert sind. Dies unterscheidet sich von der herkömmlichen Definition der Breite/Höhe und ist auf Kompatibilität mit Altsystemen zurückzuführen. Die Benutzer, die die Seite erstellen, bemerken keinen Unterschied, vorausgesetzt, dass Sie die Eigenschaft `name` klar definieren, da diese auf der Benutzeroberfläche angezeigt wird.

#### Erstellen eines neuen integrierten Editors {#creating-a-new-in-place-editor}

So erstellen Sie einen neuen integrierten Editor (innerhalb Ihrer clientlib):

>[!NOTE]
>
>Ein Beispiel finden Sie unter:
>`/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js`

1. Implementierung:

   * `setUp`
   * `tearDown`

1. Registrieren Sie den Editor (einschließlich des Konstruktors):

   * `editor.register`

1. Geben Sie die Verknüpfung zwischen dem Editor und jedem Ressourcentyp an (wie in der Komponente), der ihn verwenden kann.

#### Codebeispiel zum Erstellen eines neuen integrierten Editors {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` ist ein Beispielpaket, das zeigt, wie Sie einen neuen ersetzenden Editor in AEM erstellen.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Open aem-authoring-extension-place-editor project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor/archive/master.zip) herunter

#### Konfigurieren mehrerer Editoren für Bearbeitung im Kontext {#configuring-multiple-in-place-editors}

Es ist möglich, eine Komponente so zu konfigurieren, dass sie über mehrere integrierte Editoren verfügt. Wenn mehrere integrierte Editoren konfiguriert sind, können Sie den entsprechenden Inhalt auswählen und den entsprechenden Editor öffnen. See the [Configuring Multiple In-Place Editors](/help/sites-developing/multiple-inplace-editors.md) documentation for more information.

## Hinzufügen einer neuen Seitenaktion {#add-a-new-page-action}

So fügen Sie eine neue Aktion zur Seitensymbolleiste hinzu, z. B. eine Aktion **Zurück zu Sites** (Konsole).

### Codebeispiel {#code-sample-3}

`aem-authoring-extension-header-backtosites` ist ein Beispielpaket, das die Erstellung einer benutzerdefinierten Kopfzeilenleistenaktion demonstriert, mit der der Benutzer zurück zur Sites-Konsole springt.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Open aem-authoring-extension-header-backtosites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites/archive/master.zip) herunter

## Anpassen des Aktivierungsanfrage-Workflows {#customizing-the-request-for-activation-workflow}

Der standardmäßige Workflow **Aktivierungsanfrage** wird automatisch ausgelöst, wenn ein Inhaltsautor nicht über die erforderlichen Replikationsrechte verfügt.

To have customized behavior upon such activation you can overlay the **Request for Activation** workflow:

1. In `/apps` Overlay wird der **Sites** -Assistent ausgeführt:

   `/libs/wcm/core/content/common/managepublicationwizard`

   >[!NOTE]
   >
   >Dadurch wird die folgende common-Instanz überlagert:
   >
   >`/libs/cq/gui/content/common/managepublicationwizard`

1. Update the [workflow model](/help/sites-developing/workflows-models.md) and related configurations/scripts as required.
1. Remove the right to the [ `replicate` action](/help/sites-administering/security.md#actions) from all appropriate users for all relevant pages; to have this workflow triggered as a default action when any of the users try to publish (or replicate) a page.

