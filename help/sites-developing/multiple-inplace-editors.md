---
title: RTE für mehrere ersetzende Editoren konfigurieren.
description: Erstellen Sie mehrere ersetzende Editoren in Adobe Experience Manager, indem Sie Rich Text Editor konfigurieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: e49411a99a80e91c983afc103a8ea826e75569b8
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 26%

---


# Mehrere ersetzende Editoren {#configure-multiple-in-place-editors} konfigurieren

Sie können den Rich-Text-Editor in Adobe Experience Manager so konfigurieren, dass er mehrere ersetzende Editoren enthält. Nach der Konfiguration können Sie den entsprechenden Inhalt auswählen und den passenden Editor öffnen.

![Ein spezifischer ersetzender Editor](assets/rte-inplace-editor.png)

## Konfigurieren mehrerer Editoren {#configure-multiple-editors}

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

1. Definieren Sie auf dem Knoten `cq:inplaceEditing` (vom Typ `cq:InplaceEditingConfig`) die folgenden Eigenschaften:

   * Name:`editorType`
   * Typ: `String`
   * Wert: `hybrid`

1. Erstellen Sie unter diesem Knoten einen Knoten:

   * Name: `cq:ChildEditors`
   * Typ: `nt:unstructured`

1. Erstellen Sie unter dem Knoten `cq:childEditors` einen Knoten für jeden ersetzenden Editor:

   * Name: Der Name jeder Node ist der Name der Eigenschaft, die sie darstellt, wie bei Drop-Zielgruppen. Zum Beispiel `image` und `text`.
   * Typ: `cq:ChildEditorConfig`

   >[!NOTE]
   >
   >Es besteht eine Korrelation zwischen den definierten Ablagezielen und den untergeordneten Editoren. Der Name des Knotens `cq:ChildEditorConfig` wird als Drop-Zielgruppen-ID betrachtet und dient als Parameter für den ausgewählten untergeordneten Editor. Wenn der bearbeitbare Unterbereich z. B. keine Dropdown-Zielgruppe in einer Textkomponente enthält, wird der Name des untergeordneten Editors weiterhin als ID zur Identifizierung des entsprechenden bearbeitbaren Bereichs betrachtet.

1. Definieren Sie auf jedem dieser Knoten (`cq:ChildEditorConfig`) die Eigenschaften:

   * Name: `type`.
   * Wert: Name des registrierten ersetzenden Editors; zum Beispiel `image` und `text`.

   * Name: `title`.
   * Wert: Der Titel, der in der Liste der Komponentenauswahl der verfügbaren Editoren angezeigt wird. Zum Beispiel `Image` und `Text`.

### Zusätzliche Konfiguration für Rich Text Editors {#additional-configuration-for-rich-text-editors}

Die Konfiguration mehrerer Rich-Text-Editoren unterscheidet sich etwas vom zuvor beschriebenen Verfahren, da Sie jede einzelne RTE-Instanz separat konfigurieren können. Weitere Informationen finden Sie unter [Rich-Text-Editor konfigurieren](/help/sites-administering/rich-text-editor.md). Um mehrere RTE zu haben, erstellen Sie eine Konfiguration für jede ersetzende RTE. Adobe empfiehlt, den neuen Konfigurationsknoten unter `cq:InplaceEditingConfig` zu erstellen, da jede einzelne RTE eine andere Konfiguration aufweisen kann. Erstellen Sie unter dem neuen Knoten jede einzelne RTE-Konfiguration.

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
>Für Rich-Text-Editoren wird jedoch die Eigenschaft `configPath` unterstützt, wenn es nur eine Instanz des Text-Editors (bearbeitbarer Unterbereich) in der Komponente gibt. Diese Verwendung von `configPath` wird bereitgestellt, um die Abwärtskompatibilität mit älteren Benutzeroberflächendialogen der Komponente zu unterstützen.

>[!CAUTION]
>
>Benennen Sie den RTE-Konfigurationsknoten nicht mit `config`. Andernfalls sind die RTE-Konfigurationen nur für die Administratoren und nicht für die Benutzer in der Gruppe `content-author` verfügbar.

## Codebeispiele {#code-samples}

Den Code dieser Seite finden Sie im Projekt [aem-authoring-hybrideditors auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors). Sie können das gesamte Projekt als [ZIP-Archiv](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip) herunterladen.

## hinzufügen eines ersetzenden Editors {#add-an-in-place-editor}

Allgemeine Informationen zum Hinzufügen eines ersetzenden Editors finden Sie im Dokument [Seiten-Authoring anpassen](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor).

>[!MORELIKETHIS]
>
>* [Rich-Text-Editor in Experience Manager](/help/sites-administering/rich-text-editor.md) konfigurieren.

