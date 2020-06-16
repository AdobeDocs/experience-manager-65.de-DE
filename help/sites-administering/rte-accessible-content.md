---
title: Rich-Text-Editor konfigurieren, um barrierefreie Webseiten und Sites zu erstellen.
description: Rich-Text-Editor konfigurieren, um barrierefreie Webseiten und Sites zu erstellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: df992fc0204519509c4662a7d4315939af2fc92c
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 45%

---


# RTE konfigurieren, um barrierefreie Webseiten und Websites zu erstellen {#configure-rte-for-accessibility}

Adobe Experience Manager unterstützt viele Standard-Barrierefreiheitsmerkmale in Übereinstimmung mit verschiedenen Barrierefreiheitsstandards. Darüber hinaus können Entwickler die Funktionen anpassen oder erweitern, die die Erstellung barrierefreier Inhalte mithilfe von Experience Manager-Komponenten unterstützen, die den RTE-Editor (RTE) verwenden.

Beim Entwerfen von Webseiten und Hinzufügen von Inhalten zu den Seiten können die Inhaltsentwickler und Autoren Funktionen der RTE verwenden, um barrierefreie Informationen bereitzustellen. Fügen Sie beispielsweise Strukturinformationen über Überschriften und Absatzelemente hinzu.

Um diese Funktionen zu konfigurieren und anzupassen, [konfigurieren Sie die RTE-Zusatzmodule](#configure-the-plugin-features) für die Komponente. For example, the `paraformat` plugin lets you add additional block level semantic elements, including extending the number of heading levels supported beyond the basic `H1`, `H2`, and `H3` provided by default.

Die RTE ist in verschiedenen Komponenten für die Touch-aktivierte Benutzeroberfläche und die Classic-Benutzeroberfläche verfügbar. Die primäre Komponente, die die RTE verwendet, ist jedoch die **Text** -Komponente, die für beide Schnittstellen verfügbar ist. The following images show the RTE with a range of plugins enabled, including `paraformat`:

![Textkomponente (RTE) im Vollbildmodus in der touchfähigen Benutzeroberfläche.](assets/chlimage_1-206.png)

*Abbildung: Die Komponente &quot;Text&quot;in der Touch-fähigen Benutzeroberfläche.*

![Bearbeitungsdialogfeld (RTE) der Textkomponente in der klassischen Benutzeroberfläche](assets/chlimage_1-207.png)

*Abbildung: Die Komponente &quot;Text&quot;in der Benutzeroberfläche &quot;Klassisch&quot;.*

Die Unterschiede zwischen den RTE-Funktionen, die in den verschiedenen Benutzeroberflächen verfügbar sind, finden Sie unter [Plugins und deren Funktionen](/help/sites-administering/rich-text-editor.md#aboutplugins).

## Plug-in-Funktionen konfigurieren {#configure-the-plugin-features}

Eine vollständige Anleitung zum Konfigurieren der RTE finden Sie unter [Konfigurieren der Seite Rich Text Editor](/help/sites-administering/rich-text-editor.md) . Dies deckt alles ab, einschließlich der wichtigen Schritte:

* [Plugins und die Funktionen](/help/sites-administering/rich-text-editor.md#aboutplugins).
* [Konfigurationsspeicherorte](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
* [Aktivieren Sie ein Plugin und konfigurieren Sie die Funktionseigenschaft](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
* [Konfigurieren Sie andere Funktionen der RTE](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).

By configuring a plugin within the appropriate `rtePlugins` sub-branch in CRXDE Lite, you can activate either all or specific features for that plugin.

![Beispiel für ein rtePlugin in CRXDE Lite](assets/chlimage_1-208.png)

### Example - specify paragraph formats available in RTE selection field {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Es können wie folgt neue semantische Blockformate zur Auswahl bereitgestellt werden:

1. Legen Sie den [Konfigurationsort](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations) abhängig von Ihrem RTE fest und navigieren Sie dorthin.
1. [Aktivieren Sie das Absatzauswahlfeld](/help/sites-administering/rich-text-editor.md) durch die [Aktivierung des Plug-ins](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Geben Sie die Formate an, die Sie im Absatzauswahlfeld zur Verfügung haben möchten](/help/sites-administering/rich-text-editor.md).
1. Die Absatzformate sind dann für den Autor der Inhalte aus den Auswahlfeldern im RTE verfügbar. Auf sie kann wie folgt zugegriffen werden:

   * Verwenden des Absatz-Kopfzeilensymbols in der Touch-fähigen Benutzeroberfläche.
   * Using the **Format** field (pop-up selector) in the Classic UI.

Mit Strukturelementen, die im RTE über die Absatzformatoptionen verfügbar sind, stellt AEM eine gute Grundlage für die Entwicklung barrierefreier Inhalte bereit. Inhaltsautoren können den RTE für die Formatierung der Schriftgröße, der Farben oder anderer verwandter Attribute verwenden und dadurch die Erstellung einer Inline-Formatierung verhindern. Stattdessen müssen sie entsprechende Strukturelemente wie Überschriften auswählen und über die Option „Arten“ ausgewählte globale Formatarten verwenden. Dies sorgt für ein sauberes Markup, mehr Optionen für Benutzer, die die Suche mit ihren eigenen Formatvorlagen durchführen, sowie korrekt strukturierte Inhalte.

## Use of the source edit feature {#use-of-the-source-edit-feature}

In einigen Fällen halten Inhaltsautoren es für erforderlich, den mithilfe des RTE erstellten HTML-Quellcode zu untersuchen und anzupassen. So kann beispielsweise ein innerhalb des RTE erstellter Inhalt ein zusätzliches Markup erfordern, um Compliance mit WCAG 2.0 sicherzustellen. Dies lässt sich mit der Option [Quellenbearbeitung](/help/sites-administering/rich-text-editor.md#aboutplugins) des RTE umsetzen. You can specify the [ `sourceedit` feature on the `misctools` plugin](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Use the `sourceedit` feature carefully. Tippfehler und/oder nicht unterstützte Funktionen können zusätzliche Probleme hervorrufen.

## Hinzufügen Unterstützung für weitere HTML-Elemente und -Attribute {#add-support-for-more-html-elements-and-attributes}

Um die Barrierefreiheitsfunktionen von AEM weiter auszubauen, ist es möglich, die vorhandenen Komponenten basierend auf dem RTE (wie die Komponenten **Text** und **Tabelle**) um zusätzliche Elemente und Attribute zu erweitern.

The following procedure illustrates how to extend the **Table** component with a **Caption** element that provides information about a data table to assistive technology users:

### Example - add the caption to the Table Properties dialog {#example-adding-the-caption-to-the-table-properties-dialog}

Fügen Sie im Konstruktor von `TablePropertiesDialog` ein zusätzliches Texteingabefeld hinzu, dass für die Bearbeitung der Beschriftung verwendet wird. Note that `itemId` must be set to `caption` (i.e. the DOM attribute’s name) to automatically handle its content.

In **Table**, set explicitly set or remove the attribute to/from the DOM element. Der Wert wird vom Dialogfeld im `config`-Objekt weitergegeben. Beachten Sie, dass DOM-Attribute mithilfe der entsprechenden `CQ.form.rte.Common`-Methoden (`com` ist kurz für `CQ.form.rte.Common`) festgelegt/entfernt werden sollten, um die üblichen Fallstricke bei Browserimplementierungen zu vermeiden.

>[!NOTE]
>
>Dieses Verfahren ist nur für die klassische Benutzeroberfläche geeignet.

### Beispiel: Barrierefreies HTML erstellen, wenn Hervorhebung in Text verwendet wird {#create-accessible-html-for-text}

RTE kann Tags `strong` und `em` Tags anstelle von `b` und verwenden `i`. Hinzufügen Sie den folgenden Knoten als Geschwister mit den Knoten `uiSettings` und `rtePlugins` Knoten im Dialogfeld.

```HTML
<htmlRules jcr:primaryType="nt:unstructured">
    <docType jcr:primaryType="nt:unstructured">
        <typeConfig jcr:primaryType="nt:unstructured"
                useSemanticMarkup="{Boolean}true">
            <semanticMarkupMap
                    b="strong"
                    i="em"/>
        </typeConfig>
    </docType>
</htmlRules>
```

### Schrittweise Anleitungen {#step-by-step-instructions}

1. Starten Sie CRXDE Lite. Zum Beispiel: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Kopieren:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   wie folgt umzuleiten:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Sie müssen Zwischenordner erstellen, falls diese nicht bereits vorhanden sind.

1. Kopieren:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   wie folgt umzuleiten:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Öffnen Sie die folgende Datei zur Bearbeitung (durch Doppelklicken öffnen):

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. In der `constructor`-Methode, vor dem Lesen der Zeilen:

   ```
   var dialogRef = this;
   ```

   Fügen Sie den folgenden Code hinzu:

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Öffnen Sie die folgende Datei:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`.

1. Add the following code at the end of the `transferConfigToTable` method:

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. Speichern Sie Ihre Änderungen mithilfe von **Alle speichern…**

>[!NOTE]
>
>Ein „Nur Text“-Feld ist die einzige zulässige Eingabeart für den Wert des „caption“-Elements. Sie können jedes beliebige ExtJS-Widget verwenden, das den Wert der Beschriftung über seine `getValue()` Methode bereitstellt.
>
>Um Bearbeitungsfunktionen für weitere Elemente und Attribute hinzuzufügen, stellen Sie sicher, dass sowohl:
>
>* The `itemId` property for each corresponding field is set to the name of the appropriate DOM attribute (`TablePropertiesDialog`).
>* Das Attribut explizit für das DOM-Element festgelegt und/oder entfernt wird (`Table`).


>[!MORELIKETHIS]
>
>* [Kurzanleitung zu WCAG 2.0](/help/managing/qg-wcag.md)
>* [Erstellen von barrierefreiem Inhalt (WCAG 2.0-Konformität)](/help/sites-authoring/creating-accessible-content.md)

