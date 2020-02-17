---
title: Konfigurieren mehrerer Editoren für Bearbeitung im Kontext
seo-title: Konfigurieren mehrerer Editoren für Bearbeitung in Kontext
description: Es ist möglich, eine Komponente so zu konfigurieren, dass sie mehrere Editoren für Bearbeitung in Kontext aufweist.
seo-description: Es ist möglich, eine Komponente so zu konfigurieren, dass sie mehrere Editoren für Bearbeitung in Kontext aufweist.
uuid: 4abbfcd5-fe1b-4c02-b115-97db20e60e1e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 0fac1e4a-f08f-4c46-b070-cb1d5a05b6e0
translation-type: tm+mt
source-git-commit: b3e1493811176271ead54bae55b1cd0cf759fe71

---


# Konfigurieren mehrerer Editoren für Bearbeitung in Kontext{#configuring-multiple-in-place-editors}

Es ist möglich, eine Komponente in der Touch-optimierten Benutzeroberfläche so zu konfigurieren, dass sie mehrere Editoren für Bearbeitung in Kontext aufweist.

Nach der Konfiguration können Sie den entsprechenden Inhalt auswählen und den passenden Editor öffnen. Beispiel:

![chlimage_1-8](assets/chlimage_1-8a.png)

## Konfigurieren mehrerer Editoren {#configuring-multiple-editors}

Um die Verwendung mehrerer Editoren für Bearbeitung in Kontext zu ermöglichen, wurde die Struktur des Knotentyps `cq:InplaceEditingConfig` um die Definition des Knotentyps `cq:ChildEditorConfig` erweitert.

Beispiel:

```
   /**
       * Configures inplace editing of a component.
       *
       * @prop active true to activate inplace editing for the component
       * @prop editorType ID of inplace editor to use
       * @prop cq:childEditors collection of {@link cq:ChildEditorConfig} nodes.
       * @prop configPath path to editor's config (optional)
       * @node config editor's config (used if no configPath is specified; optional)
     */
    [cq:InplaceEditingConfig] > nt:unstructured
      - active (boolean)
      - editorType (string)
      + cq:childEditors (nt:base) = nt:unstructured
      - configPath (string)
      + config (nt:unstructured) = nt:unstructured

    /**
      * Configures one child editor for a subcomponent. The name of the this node will
      * be used as DD id.
      *
      * @prop type type of the inline editor. eg: ["image"]
      * @prop title totle od the inline editor
      * @prop icon icon to represent the inline editor
    */
    [cq:ChildEditorConfig] > nt:unstructured
      orderable
      - type (string)
      - title (string)
```

Gehen Sie wie folgt vor, um mehrere Editoren zu konfigurieren:

1. On the node `cq:inplaceEditing` (of type `cq:InplaceEditingConfig`) define the property:

   * Name:`editorType`
   * Typ: `String`
   * Wert: `hybrid`

1. Erstellen Sie unter diesem Knoten einen neuen Knoten:

   * Name: `cq:ChildEditors`
   * Typ: `nt:unstructured`

1. Erstellen Sie unter dem Knoten `cq:childEditors` für jeden Editor für Bearbeitung in Kontext einen neuen Knoten:

   * Name: Der Name jedes Knotens sollte dem Namen der Eigenschaft entsprechen, die er repräsentiert (wie bei Ablagezielen). Beispiel, `image`, `text`.
   * Typ: cq: `ChildEditorConfig`
   >[!NOTE]
   >
   >Es besteht eine Korrelation zwischen den definierten Ablagezielen und den untergeordneten Editoren. Der Name des Knotens `cq:ChildEditorConfig` wird als ID des Ablageziels für die Verwendung als Parameter für den ausgewählten untergeordneten Editor herangezogen. Wenn der bearbeitbare Unterbereich kein Ablageziel hat (etwa wie bei einer Textkomponente), dann wird der Name des untergeordneten Editors weiterhin als ID zur Identifizierung des entsprechenden bearbeitbaren Bereichs herangezogen.

1. On each of these nodes ( `cq:ChildEditorConfig`) define the properties:

   * Name: `type`
   * Value: name of the registered in-place editor; for example, `image`, `text`

   * Name: `title`
   * Value: the title that you want to display in the components selection list (of available editors); for example, `Image`, `Text`

### Zusätzliche Konfiguration für Rich-Text-Editoren {#additional-configuration-for-rich-text-editors}

Die Konfiguration mehrerer Rich-Text-Editoren unterscheidet sich etwas vom zuvor beschriebenen Verfahren, da Sie jede einzelne RTE-Instanz separat konfigurieren können.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md).

Um mehrere RTEs verwenden zu können, benötigen Sie eine Konfiguration für jeden Rich-Text-Editor für Bearbeitung in Kontext:

* Definieren Sie unter `cq:InplaceEditingConfig` einen `config` Knoten.

   * Definieren Sie unter dem Knoten `config` die einzelnen RTE-Konfigurationen.

```xml
    texttext
        cq:dialog
        cq:editConfig
            cq:inplaceEditing
                cq:childEditors
                    config
                        text1
                            rtePlugins
                        text2
                            rtePlugins
```

>[!NOTE]
>
>Es empfiehlt sich, den Knoten `config` unter `cq:InplaceEditingConfig` zu definieren, da jeder einzelne Rich-Text-Editor eine andere Konfiguration aufweisen kann.
>
>Für Rich-Text-Editoren wird jedoch die Eigenschaft `configPath` unterstützt, wenn es nur eine Instanz des Text-Editors (bearbeitbarer Unterbereich) in der Komponente gibt. Diese Verwendung von `configPath` wird ermöglicht, um die Abwärtskompatibilität mit Dialogfeldern für ältere Benutzeroberflächen der Komponente zu unterstützen.

## Codebeispiele {#code-samples}

**CODE AUF GITHUB**

Den Code dieser Seite finden Sie auf GitHub

* [Open aem-authoring-hybrideditors-Projekt auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip) herunter

## Hinzufügen von Editoren für Bearbeitung in Kontext {#adding-an-in-place-editor}

For general information about adding an in-place editor see the document [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor).
