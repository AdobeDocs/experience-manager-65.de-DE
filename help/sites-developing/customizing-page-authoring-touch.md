---
title: Anpassung des Seiten-Authorings
description: Adobe Experience Manager (AEM) bietet verschiedene Mechanismen, mit denen Sie die Seitenbearbeitungsfunktionen anpassen können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 90594588-db8e-4d4c-a208-22c1c6ea2a2d
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 50%

---

# Anpassung des Seiten-Authorings{#customizing-page-authoring}

>[!CAUTION]
>
>In diesem Dokument wird beschrieben, wie Sie die Seitenbearbeitung in der modernen, Touch-optimierten Benutzeroberfläche anpassen. Es gilt nicht für die klassische Benutzeroberfläche.

Adobe Experience Manager (AEM) bietet verschiedene Mechanismen, mit denen Sie die Seitenbearbeitungsfunktion (und die [Konsolen](/help/sites-developing/customizing-consoles-touch.md)) Ihrer Authoring-Instanz.

* Clientbibliotheken

  Mit Clientlibs können Sie die Standardimplementierung erweitern, um neue Funktionen zu realisieren und gleichzeitig die Standardfunktionen, -objekte und -methoden wiederzuverwenden. Bei der Anpassung können Sie unter `/apps.` Ihre eigene Clientbibliothek erstellen. Die neue Clientbibliothek muss:

   * die Authoring-clientlib `cq.authoring.editor.sites.page` als Abhängigkeit aufweisen
   * der entsprechenden `cq.authoring.editor.sites.page.hook`-Kategorie angehören

* Überlagerungen

  Überlagerungen basieren auf Knotendefinitionen und ermöglichen das Überlagern der Standardfunktionen (in `/libs`) mit Ihrer eigenen benutzerdefinierten Funktionalität (in `/apps`). Wenn Sie eine Überlagerung erstellen, ist keine 1:1-Kopie des Originals erforderlich, da die [Sling-Ressourcenzusammenführung](/help/sites-developing/sling-resource-merger.md) das Vererben zulässt.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [JS-Dokumentationssatz](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

Diese können auf viele Arten verwendet werden, um die Seitenbearbeitungsfunktion in Ihrer AEM zu erweitern. Eine Auswahl wird im Folgenden behandelt (auf hoher Ebene).

>[!NOTE]
>
>Weitere Informationen finden Sie unter folgenden Themen:
>
>* Verwenden und Erstellen [clientlibs](/help/sites-developing/clientlibs.md).
>* Verwenden und Erstellen [Overlays](/help/sites-developing/overlays.md).
>* [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)
>* [Struktur der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-structure.md) für Details zu den strukturellen Bereichen, die beim Seiten-Authoring verwendet werden.
>


>[!CAUTION]
>
>****** Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.
>
>Der Grund dafür ist, dass der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren (und möglicherweise auch überschrieben werden, wenn Sie einen Hotfix oder ein Feature Pack anwenden).
>
>Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
>
>1. Erstellen Sie das erforderliche Element (d. h., wie es in `/libs`) unter `/apps`
>1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.

## Neue Ebene hinzufügen (Modus) {#add-new-layer-mode}

Beim Bearbeiten einer Seite gibt es verschiedene [Modi](/help/sites-authoring/author-environment-tools.md#page-modes) verfügbar. Diese Modi werden mithilfe von [Ebenen](/help/sites-developing/touch-ui-structure.md#layer). Diese ermöglichen den Zugriff auf verschiedene Funktionstypen für denselben Seiteninhalt. Die Standardebenen sind: Bearbeiten, Vorschau, Anmerkungen, Entwickler und Targeting.

### Ebenenbeispiel: Live Copy-Status {#layer-example-live-copy-status}

Eine standardmäßige AEM-Instanz stellt die MSM-Ebene bereit. Auf Daten im Zusammenhang mit [Multisite-Management](/help/sites-administering/msm.md) und hebt sie in der Ebene hervor.

Um ihn in Aktion zu sehen, können Sie [We.Retail-Sprachkopie](/help/sites-developing/we-retail-globalized-site-structure.md) Seite (oder einer anderen Live Copy-Seite) und wählen Sie die **Live Copy-Status** -Modus.

Sie finden die MSM-Ebenendefinition (als Referenz) in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codebeispiel {#code-sample}

Dies ist ein Beispielpaket, das zeigt, wie eine Ebene (Modus) erstellt wird, die eine neue Ebene für die MSM-Ansicht ist.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-authoring-new-layer-mode in GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode/archive/master.zip) herunter.

## Neue Auswahlkategorie zum Asset-Browser hinzufügen {#add-new-selection-category-to-asset-browser}

Der Asset-Browser zeigt Assets verschiedener Typen/Kategorien an (z. B. Bilder und Dokumente). Die Assets können auch anhand dieser Asset-Kategorien gefiltert werden.

### Codebeispiel {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` ist ein Beispielpaket, das zeigt, wie eine Gruppe zur Asset-Suche hinzugefügt wird. Dieses Beispiel verbindet mit [Flickr](https://www.flickr.com)ist der öffentliche Stream und zeigt sie im Seitenbereich an.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-authoring-extension-assetfinder-flickr in GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr/archive/master.zip) herunter.

## Ressourcen filtern {#filtering-resources}

Beim Erstellen von Seiten muss der Benutzer häufig aus Ressourcen auswählen (z. B. Seiten, Komponenten und Assets). Dies kann in Form einer Liste erfolgen, aus der der Autor beispielsweise ein Element auswählen muss.

Um die Liste in einer angemessenen Größe und auch für den Anwendungsfall relevant zu halten, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Wenn z. B. der Benutzer durch die [`pathbrowser`](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)-[Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui)-Komponente den Pfad zu einer bestimmten Ressource auswählen kann, können die gezeigten Pfade auf folgende Art gefiltert werden:

* Implementieren Sie das benutzerdefinierte Prädikat, indem Sie die Schnittstelle [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/predicate/package-summary.html) implementieren.
* Geben Sie einen Namen für die Eigenschaft an und verwenden Sie diesen Namen, wenn Sie `pathbrowser` verwenden.

Weitere Details zum Erstellen einer benutzerdefinierten Eigenschaft finden Sie in [diesem Artikel](/help/sites-developing/implementing-custom-predicate-evaluator.md).

>[!NOTE]
>
>Die Implementierung einer benutzerdefinierten Eigenschaft durch die Implementierung der Schnittstelle `com.day.cq.commons.predicate.AbstractNodePredicate` funktioniert auch in der klassischen Benutzeroberfläche.
>
>Siehe [dieser Knowledge Base-Artikel](https://helpx.adobe.com/experience-manager/using/creating-custom-cq-tree.html) ein Beispiel für die Implementierung eines benutzerdefinierten Prädikats in der klassischen Benutzeroberfläche.

## Hinzufügen einer neuen Aktion zu einer Komponenten-Symbolleiste {#add-new-action-to-a-component-toolbar}

Jede Komponente verfügt (in der Regel) über eine Symbolleiste, die Zugriff auf eine Reihe von Aktionen bietet, die für diese Komponente durchgeführt werden können.

### Codebeispiel {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` ist ein Beispielpaket, das die Erstellung einer benutzerdefinierten Symbolleistenaktion zum Rendern von Komponenten demonstriert.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-authoring-extension-toolbar-screenshot in GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot/archive/master.zip) herunter.

## Neuen Editor für Bearbeitung im Kontext hinzufügen {#add-new-in-place-editor}

### Standard-Editor für Bearbeitung im Kontext {#standard-in-place-editor}

Bei der Standardinstallation von AEM:

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js`

   Enthält Definitionen der verschiedenen verfügbaren Editoren.

1. Es besteht eine Verbindung zwischen dem Editor und jedem Ressourcentyp (wie in der Komponente), der ihn verwenden kann:

   * `cq:inplaceEditing`

     Beispiel:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * property: `editorType`

           Definiert den Typ des Inline-Editors, der verwendet wird, wenn die Bearbeitung im Kontext für diese Komponente ausgelöst wird. Beispiel: `text`, `textimage`, `image`, `title`.

1. Zusätzliche Konfigurationsdetails des Editors können mit einer `config` Knoten, der Konfigurationen enthält, und ein `plugin` -Knoten, der die erforderlichen Konfigurationsdetails des Plug-ins enthält.

   Das folgende Beispiel zeigt die Definition von Seitenverhältnissen für das Bildbeschneidungs-Plug-in der image-Komponente. Aufgrund der eingeschränkten Bildschirmgröße wurden die Seitenverhältnisse des Zuschnitts in den Vollbild-Editor verschoben und können nur dort angezeigt werden.

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
   >AEM Anbauverhältnisse, wie durch die `ratio` -Eigenschaft, definiert als **height/width**. Dies unterscheidet sich von der herkömmlichen Definition als Breite/Höhe und erfolgt aus Gründen der Legacy-Kompatibilität. Die Benutzer, die die Seite erstellen, bemerken keinen Unterschied, vorausgesetzt, dass Sie die Eigenschaft `name` klar definieren, da diese auf der Benutzeroberfläche angezeigt wird.

#### Erstellen eines neuen Editors für Bearbeitung im Kontext {#creating-a-new-in-place-editor}

So erstellen Sie einen neuen Editor für Bearbeitung im Kontext (innerhalb Ihrer clientlib):

>[!NOTE]
>
>Ein Beispiel finden Sie unter:
>`/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js`

1. Implementierung:

   * `setUp`
   * `tearDown`

1. Registrieren Sie den Editor (einschließlich des Konstruktors):

   * `editor.register`

1. Stellen Sie die Verbindung zwischen dem Editor und jedem Ressourcentyp (wie in der Komponente) bereit, der ihn verwenden kann.

#### Codebeispiel zum Erstellen eines neuen Editors für Bearbeitung im Kontext {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` ist ein Beispielpaket, das zeigt, wie ein Editor für die Bearbeitung im Kontext in AEM erstellt wird.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-authoring-extension-inplace-editor in GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor/archive/master.zip) herunter.

#### Konfigurieren mehrerer Editierender für Bearbeitung im Kontext {#configuring-multiple-in-place-editors}

Es ist möglich, eine Komponente so zu konfigurieren, dass sie über mehrere Editoren für Bearbeitung im Kontext verfügt. Wenn mehrere Editoren für Bearbeitung im Kontext konfiguriert sind, können Sie den entsprechenden Inhalt auswählen und den entsprechenden Editor öffnen. In der Dokumentation zur [Konfigurieren mehrerer Editoren für Bearbeitung im Kontext](/help/sites-developing/multiple-inplace-editors.md) finden Sie weitere Informationen.

## Hinzufügen einer neuen Seitenaktion {#add-a-new-page-action}

So fügen Sie der Seitensymbolleiste eine neue Seitenaktion hinzu, z. B. eine **Zurück zu Sites** Aktion (Konsole).

### Codebeispiel {#code-sample-3}

`aem-authoring-extension-header-backtosites` ist ein Beispielpaket, das die Erstellung einer benutzerdefinierten Kopfzeilenleistenaktion demonstriert, mit der der Benutzer zurück zur Sites-Konsole springt.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-authoring-extension-header-backtosites in GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites/archive/master.zip) herunter.

## Anpassen des Aktivierungsanfrage-Workflows {#customizing-the-request-for-activation-workflow}

Der vorkonfigurierte Workflow, **Aktivierungsanfrage**:

* Wird automatisch im entsprechenden Menü angezeigt, wenn ein Inhaltsautor **nicht** über die entsprechenden Replikationsrechte verfügt, jedoch eine Mitgliedschaft von DAM-Benutzern und Autoren **hat**.

* Andernfalls wird nichts angezeigt, da die Replikationsrechte entfernt wurden.

Um bei dieser Aktivierung ein benutzerdefiniertes Verhalten zu erzielen, können Sie die **Aktivierungsanfrage** workflow:

1. Überlagern Sie in `/apps` den **Sites**-Assistenten:

   `/libs/wcm/core/content/common/managepublicationwizard`

   >[!NOTE]
   >
   >Dadurch wird die folgende gemeinsame Instanz überlagert:
   >
   >`/libs/cq/gui/content/common/managepublicationwizard`

1. Aktualisieren Sie das [Workflow-Modell](/help/sites-developing/workflows-models.md) und je nach Bedarf relevante Konfigurationen/Skripte.
1. Entziehen Sie allen entsprechenden Benutzern für alle relevanten Seiten das Recht zur [`replicate`-Aktion](/help/sites-administering/security.md#actions), damit dieser Workflow standardmäßig ausgelöst wird, wenn ein Benutzer versucht, eine Seite zu veröffentlichen (oder zu replizieren).
