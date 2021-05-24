---
title: Konfigurieren Sie den RTE für mehrere Editoren für Bearbeitung im Kontext.
description: Erstellen Sie mehrere integrierte Editoren in Adobe Experience Manager, indem Sie den Rich-Text-Editor konfigurieren.
contentOwner: AG
exl-id: 03030317-8b7d-408a-bdfd-619824d7260c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 26%

---

# Konfigurieren mehrerer Editoren für Bearbeitung im Kontext {#configure-multiple-in-place-editors}

Sie können den Rich-Text-Editor in Adobe Experience Manager so konfigurieren, dass er über mehrere integrierte Editoren verfügt. Nach der Konfiguration können Sie den entsprechenden Inhalt auswählen und den passenden Editor öffnen.

![Ein bestimmter Editor für Bearbeitung im Kontext](assets/rte-inplace-editor.png)

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

1. Definieren Sie im Knoten `cq:inplaceEditing` (vom Typ `cq:InplaceEditingConfig`) die folgenden Eigenschaften:

   * Name:`editorType`
   * Typ: `String`
   * Wert: `hybrid`

1. Erstellen Sie unter diesem Knoten einen Knoten:

   * Name: `cq:ChildEditors`
   * Typ: `nt:unstructured`

1. Erstellen Sie unter dem Knoten `cq:childEditors` einen Knoten für jeden Editor im Kontext:

   * Name: Der Name jedes Knotens ist der Name der Eigenschaft, die er darstellt, wie bei Ablagezielen. Zum Beispiel `image` und `text`.
   * Typ: `cq:ChildEditorConfig`

   >[!NOTE]
   >
   >Es besteht eine Korrelation zwischen den definierten Ablagezielen und den untergeordneten Editoren. Der Name des Knotens `cq:ChildEditorConfig` wird als Ablageziel-ID betrachtet und dient als Parameter für den ausgewählten untergeordneten Editor. Wenn der bearbeitbare Unterbereich keine Ablagezielgruppe hat, z. B. in einer Textkomponente, wird der Name des untergeordneten Editors weiterhin als ID zur Identifizierung des entsprechenden bearbeitbaren Bereichs betrachtet.

1. Definieren Sie auf jedem dieser Knoten (`cq:ChildEditorConfig`) die Eigenschaften:

   * Name: `type`.
   * Wert: den Namen des registrierten Bearbeiters; z. B. `image` und `text`.

   * Name: `title`.
   * Wert: Der Titel, der in der Komponentenauswahlliste der verfügbaren Editoren angezeigt wird. Zum Beispiel `Image` und `Text`.

### Zusätzliche Konfiguration für Rich-Text-Editoren {#additional-configuration-for-rich-text-editors}

Die Konfiguration mehrerer Rich-Text-Editoren unterscheidet sich etwas vom zuvor beschriebenen Verfahren, da Sie jede einzelne RTE-Instanz separat konfigurieren können. Weitere Informationen finden Sie unter [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md). Um mehrere RTE zu verwenden, erstellen Sie eine Konfiguration für jeden integrierten RTE. Adobe empfiehlt, den neuen Konfigurationsknoten unter `cq:InplaceEditingConfig` zu erstellen, da jeder einzelne RTE eine andere Konfiguration aufweisen kann. Erstellen Sie unter dem neuen Knoten jede einzelne RTE-Konfiguration.

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
>Für Rich-Text-Editoren wird jedoch die Eigenschaft `configPath` unterstützt, wenn es nur eine Instanz des Text-Editors (bearbeitbarer Unterbereich) in der Komponente gibt. Diese Verwendung von `configPath` wird bereitgestellt, um die Abwärtskompatibilität mit älteren Dialogfeldern der Benutzeroberfläche der Komponente zu unterstützen.

>[!CAUTION]
>
>Benennen Sie den RTE-Konfigurationsknoten nicht mit `config`. Andernfalls sind die RTE-Konfigurationen nur für die Administratoren und nicht für die Benutzer in der Gruppe `content-author` verfügbar.

## Codebeispiele {#code-samples}

Den Code dieser Seite finden Sie im Projekt [aem-authoring-hybrideditors auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors). Sie können das gesamte Projekt als [ZIP-Archiv](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip) herunterladen.

## Hinzufügen eines Editors für Bearbeitung im Kontext {#add-an-in-place-editor}

Allgemeine Informationen zum Hinzufügen eines Editors für Bearbeitung im Kontext finden Sie im Dokument [Seitenbearbeitung anpassen](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor).

>[!MORELIKETHIS]
>
>* [Konfigurieren des Rich-Text-Editors in Experience Manager](/help/sites-administering/rich-text-editor.md).

