---
title: RTE für mehrere ersetzende Editoren konfigurieren.
description: Erstellen Sie mehrere ersetzende Editoren in Adobe Experience Manager, indem Sie Rich Text Editor konfigurieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: e49411a99a80e91c983afc103a8ea826e75569b8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Mehrere ersetzende Editoren konfigurieren {#configure-multiple-in-place-editors}

Sie können den Rich-Text-Editor in Adobe Experience Manager so konfigurieren, dass mehrere ersetzende Editoren vorhanden sind. Nach der Konfiguration können Sie den entsprechenden Inhalt auswählen und den passenden Editor öffnen.

![Ein spezifischer ersetzender Editor](assets/rte-inplace-editor.png)

## Mehrere Editoren konfigurieren {#configure-multiple-editors}

Um die Verwendung mehrerer Editoren für Bearbeitung in Kontext zu ermöglichen, wurde die Struktur des Knotentyps `cq:InplaceEditingConfig` um die Definition des Knotentyps `cq:ChildEditorConfig` erweitert.

Beispiel:

```js
   /**
       * Configures in-place editing of a component.
       *
       * @prop active true to activate in-place editing for the component.
       * @prop editorType ID of in-place editor to use.
       * @prop cq:childEditors collection of {@link cq:ChildEditorConfig} nodes.
       * @prop configPath path to editor's config (optional).
       * @node config editor's config (used if no configPath is specified; optional).
     */
    [cq:InplaceEditingConfig] > nt:unstructured
      - active (boolean)
      - editorType (string)
      + cq:childEditors (nt:base) = nt:unstructured
      - configPath (string)
      + config (nt:unstructured) = nt:unstructured

    /**
      * Configures one child editor for a sub-component. The name of the this node is
      * used as DD ID.
      *
      * @prop type type of the inline editor. For example, ["image"].
      * @prop title Title of the inline editor.
      * @prop icon Icon to represent the inline editor.
    */
    [cq:ChildEditorConfig] > nt:unstructured
      orderable
      - type (string)
      - title (string)
```

Gehen Sie wie folgt vor, um mehrere Editoren zu konfigurieren:

1. Definieren Sie auf der Node `cq:inplaceEditing` (vom Typ `cq:InplaceEditingConfig`) die folgenden Eigenschaften:

   * Name:`editorType`
   * Typ: `String`
   * Wert: `hybrid`

1. Erstellen Sie unter diesem Knoten einen Knoten:

   * Name: `cq:ChildEditors`
   * Typ: `nt:unstructured`

1. Under `cq:childEditors` node, create a node for each in-place editor:

   * Name: Der Name jeder Node ist der Name der Eigenschaft, die sie darstellt, wie bei Drop-Zielgruppen. Zum Beispiel `image` und `text`.
   * Typ: `cq:ChildEditorConfig`

   >[!NOTE]
   >
   >Es besteht eine Korrelation zwischen den definierten Ablagezielen und den untergeordneten Editoren. The name of the `cq:ChildEditorConfig` node is considered as the drop target ID, for use as a parameter to the selected child editor. Wenn der bearbeitbare Unterbereich z. B. keine Dropdown-Zielgruppe in einer Textkomponente enthält, wird der Name des untergeordneten Editors weiterhin als ID zur Identifizierung des entsprechenden bearbeitbaren Bereichs betrachtet.

1. On each of these nodes (`cq:ChildEditorConfig`) define the properties:

   * Name: `type`.
   * Value: The name of the registered in-place editor; for example, `image` and `text`.

   * Name: `title`.
   * Wert: Der Titel, der in der Liste der Komponentenauswahl der verfügbaren Editoren angezeigt wird. Zum Beispiel `Image` und `Text`.

### Additional configuration for Rich Text Editors {#additional-configuration-for-rich-text-editors}

Die Konfiguration mehrerer Rich-Text-Editoren unterscheidet sich etwas vom zuvor beschriebenen Verfahren, da Sie jede einzelne RTE-Instanz separat konfigurieren können. Weitere Informationen finden Sie unter Rich-Text-Editor [konfigurieren](/help/sites-administering/rich-text-editor.md). Um mehrere RTE zu haben, erstellen Sie eine Konfiguration für jede ersetzende RTE. Adobe empfiehlt die Erstellung des neuen Konfigurationsknotens unter `cq:InplaceEditingConfig` dem jeder RTE eine andere Konfiguration aufweisen kann. Erstellen Sie unter dem neuen Knoten jede einzelne RTE-Konfiguration.

```xml
    texttext
        cq:dialog
        cq:editConfig
            cq:inplaceEditing
                cq:childEditors
                    someconfig
                        text1
                            rtePlugins
                        text2
                            rtePlugins
```

>[!NOTE]
>
>Für Rich-Text-Editoren wird jedoch die Eigenschaft `configPath` unterstützt, wenn es nur eine Instanz des Text-Editors (bearbeitbarer Unterbereich) in der Komponente gibt. This use of `configPath` is provided to support backwards compatibility with older user interface dialogs of the component.

>[!CAUTION]
>
>Benennen Sie den RTE-Konfigurationsknoten nicht mit `config`. Otherwise, the RTE configurations are available for only the administrators and not for the users in the group `content-author`.

## Code samples {#code-samples}

Den Code dieser Seite finden Sie im Projekt [aem-authoring-hybrideditors auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors). Sie können das gesamte Projekt als [ZIP-Archiv](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip)herunterladen.

## Hinzufügen eines ersetzenden Editors {#add-an-in-place-editor}

For general information about adding an in-place editor see the document [customize page authoring](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor).

>[!MORELIKETHIS]
>
>* [Rich-Text-Editor in Experience Manager](/help/sites-administering/rich-text-editor.md)konfigurieren.

