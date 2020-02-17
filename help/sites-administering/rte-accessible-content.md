---
title: Konfigurieren von RTE für die Erstellung zugriffsbereiter Sites
description: Erfahren Sie, wie Sie den Rich-Text-Editor von AEM konfigurieren können, um barrierefreie Sites zu erstellen.
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/SITES
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
translation-type: tm+mt
source-git-commit: 07c1a4102539ba4678c55dee3a4882101e39864f

---


# Konfigurieren von RTE für die Erstellung zugriffsbereiter Sites {#configuring-rte-for-producing-accessible-sites}

AEM unterstützt beides:

* Standardmäßige Funktionen zur Barrierefreiheit, einschließlich Alternativtext für Bilder
* sowie zusätzliche Funktionen, auf die bei der Erstellung von Inhalt mit Komponenten zugegriffen werden kann, die den Rich-Text-Editor (RTE) verwenden.

Inhaltsautoren können Funktionen von RTE verwenden, um beim Hinzufügen von Inhalten zu einer Seite Informationen zur Barrierefreiheit bereitzustellen. Dies kann das Hinzufügen struktureller Informationen durch Überschriften und Absatzelemente umfassen.

Sie können [diese Funktionen durch die Konfiguration von RTE-Plug-ins zur Komponente konfigurieren und anpassen](#configuring-the-plugin-features). For example, the `paraformat` plugin allows you to add additional block level semantic elements, including extending the number of heading levels supported beyond the basic `H1`, `H2` and `H3` provided by default.

Die RTE ist in verschiedenen Komponenten der touchfähigen und der klassischen Benutzeroberfläche verfügbar. Die primäre Komponente zur Verwendung von RTE ist die **Textkomponente**.

The **Text** component in AEM is available for both the touch-enabled and the classic UIs. Auf den folgenden Bildern wird der Rich-Text-Editor mit einer Reihe von Plug-ins aktiviert, einschließlich `paraformat`:

* The **Text** component in the touch-enabled UI:

   ![Textkomponente (RTE) im Vollbildmodus in der touchfähigen Benutzeroberfläche.](assets/chlimage_1-206.png)

* Die **Textkomponente** in der klassischen Benutzeroberfläche:

   ![Bearbeitungsdialogfeld (RTE) der Textkomponente in der klassischen Benutzeroberfläche](assets/chlimage_1-207.png)

>[!NOTE]
>
>Es gibt Unterschiede zwischen den RTE-Funktionen der klassischen Benutzeroberfläche und der touchfähigen Benutzeroberfläche. Weitere Informationen finden Sie unter
>
>* [Plug-ins und ihre Funktionen](/help/sites-administering/rich-text-editor.md#aboutplugins)
>* [Plugins und zugehörige Funktionen - Touch-fähige Benutzeroberfläche](/help/sites-administering/rich-text-editor.md#aboutplugins)
>



## Konfigurieren der Plug-in-Funktionen {#configuring-the-plugin-features}

Die vollständigen Anweisungen zum Konfigurieren des RTE sind auf der Seite [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md) verfügbar. Dies deckt alles ab, einschließlich der wichtigen Schritte:

* [Plug-ins und ihre Funktionen](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [Konfigurationsspeicherorte](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Aktivieren eines Plug-ins und Konfigurieren der features-Eigenschaft](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Konfigurieren anderer RTE-Funktionen](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

Durch das Konfigurieren eines Plug-ins innerhalb des entsprechenden `rtePlugins`-Unterzweigs in CRXDE Lite (siehe folgendes Bild) können Sie entweder alle oder spezifische Funktionen für das Plug-in aktivieren.

![Beispiel für ein rtePlugin in CRXDE Lite](assets/chlimage_1-208.png)

### Beispiel – Angeben von im RTE-Auswahlfeld verfügbaren Absatzformaten {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Es können wie folgt neue semantische Blockformate zur Auswahl bereitgestellt werden:

1. Legen Sie den [Konfigurationsort](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations) abhängig von Ihrem RTE fest und navigieren Sie dorthin.
1. [Aktivieren Sie das Absatzauswahlfeld](/help/sites-administering/rich-text-editor.md) durch die [Aktivierung des Plug-ins](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Geben Sie die Formate an, die Sie im Absatzauswahlfeld zur Verfügung haben möchten](/help/sites-administering/rich-text-editor.md).
1. Die Absatzformate sind dann für den Autor der Inhalte aus den Auswahlfeldern im RTE verfügbar. Auf sie kann wie folgt zugegriffen werden:

   * Verwenden des Absatz-Kopfzeilensymbols in der Touch-fähigen Benutzeroberfläche.
   * Using the **Format** field (pop-up selector) in the Classic UI.

Mit Strukturelementen, die im RTE über die Absatzformatoptionen verfügbar sind, stellt AEM eine gute Grundlage für die Entwicklung barrierefreier Inhalte bereit. Inhaltsautoren können den RTE für die Formatierung der Schriftgröße, der Farben oder anderer verwandter Attribute verwenden und dadurch die Erstellung einer Inline-Formatierung verhindern. Stattdessen müssen sie entsprechende Strukturelemente wie Überschriften auswählen und über die Option „Arten“ ausgewählte globale Formatarten verwenden. Dies sorgt für ein sauberes Markup, mehr Optionen für Benutzer, die die Suche mit ihren eigenen Formatvorlagen durchführen, sowie korrekt strukturierte Inhalte.

## Verwenden der Funktion „Quellenbearbeitung“ {#use-of-the-source-edit-feature}

In einigen Fällen halten Inhaltsautoren es für erforderlich, den mithilfe des RTE erstellten HTML-Quellcode zu untersuchen und anzupassen. So kann beispielsweise ein innerhalb des RTE erstellter Inhalt ein zusätzliches Markup erfordern, um Compliance mit WCAG 2.0 sicherzustellen. Dies lässt sich mit der Option [Quellenbearbeitung](/help/sites-administering/rich-text-editor.md#aboutplugins) des RTE umsetzen. You can specify the [ `sourceedit` feature on the `misctools` plugin](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Use the `sourceedit` feature carefully. Tippfehler und/oder nicht unterstützte Funktionen können zusätzliche Probleme hervorrufen.

## Hinzufügen von Unterstützung für zusätzliche HTML-Elemente und -Attribute {#adding-support-for-additional-html-elements-and-attributes}

Um die Barrierefreiheitsfunktionen von AEM weiter auszubauen, ist es möglich, die vorhandenen Komponenten basierend auf dem RTE (wie die Komponenten **Text** und **Tabelle**) um zusätzliche Elemente und Attribute zu erweitern.

The following procedure illustrates how to extend the **Table** component with a **Caption** element that provides information about a data table to assistive technology users:

### Beispiel – Hinzufügen der Beschriftung zum Dialogfeld „Tabelleneigenschaften“{#example-adding-the-caption-to-the-table-properties-dialog}

Fügen Sie im Konstruktor von `TablePropertiesDialog` ein zusätzliches Texteingabefeld hinzu, dass für die Bearbeitung der Beschriftung verwendet wird. Note that `itemId` must be set to `caption` (i.e. the DOM attribute’s name) to automatically handle its content.

Unter **Tabelle** müssen Sie das Attribut explizit zum/vom DOM-Element festlegen/entfernen. Der Wert wird vom Dialogfeld im `config`-Objekt weitergegeben. Beachten Sie, dass DOM-Attribute mithilfe der entsprechenden `CQ.form.rte.Common`-Methoden (`com` ist kurz für `CQ.form.rte.Common`) festgelegt/entfernt werden sollten, um die üblichen Fallstricke bei Browserimplementierungen zu vermeiden.

>[!NOTE]
>
>Dieses Verfahren eignet sich nur für die klassische Benutzeroberfläche.

### Schritt-für-Schritt-Anweisungen {#step-by-step-instructions}

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
>Ein „Nur Text“-Feld ist die einzige zulässige Eingabeart für den Wert des „caption“-Elements. Any ExtJS widget, that provides the caption’s value through its `getValue()` method, could be used.
>
>Um Bearbeitungsfunktionen für weitere Elemente und Attribute hinzuzufügen, stellen Sie sicher, dass sowohl:
>
>* The `itemId` property for each corresponding field is set to the name of the appropriate DOM attribute (`TablePropertiesDialog`).
>* Das Attribut explizit für das DOM-Element festgelegt und/oder entfernt wird (`Table`).


>[!MORELIKETHIS]
>
>* [Kurzanleitung zu WCAG 2.0](/help/managing/qg-wcag.md)
>* [Erstellen barrierefreier Inhalte (gemäß WCAG 2.0)](/help/sites-authoring/creating-accessible-content.md)

