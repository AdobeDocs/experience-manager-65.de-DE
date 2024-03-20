---
title: Konfigurieren Sie den Rich-Text-Editor, um barrierefrei zugängliche Web-Seiten und Websites zu erstellen.
description: Konfigurieren Sie den Rich-Text-Editor, um barrierefrei zugängliche Web-Seiten und Websites zu erstellen.
contentOwner: AG
exl-id: d2451710-5abf-4816-8052-57d8f04a228e
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 82%

---

# Konfigurieren des RTE, um barrierefrei zugängliche Web-Seiten und Websites zu erstellen {#configure-rte-for-accessibility}

Adobe Experience Manager unterstützt viele Standardfunktionen für Barrierefreiheit, die den verschiedenen Standards für Barrierefreiheit entsprechen. Darüber hinaus können Entwickler mit Anpassungen und Erweiterungen Funktionen bereitstellen, die die Erstellung barrierefrei zugänglicher Inhalte mithilfe von Experience Manager-Komponenten erleichtern, die den Rich-Text-Editor (RTE) verwenden.

Beim Entwerfen von Web-Seiten und Hinzufügen von Inhalten zu den Seiten können die Inhaltsentwickler und Autoren Funktionen des RTE verwenden, um Informationen im Zusammenhang mit Barrierefreiheit bereitzustellen. Fügen Sie beispielsweise Strukturinformationen mithilfe von Überschriften und Absatzelementen hinzu.

Zum Konfigurieren und Anpassen dieser Funktionen [konfigurieren Sie die RTE-Plug-ins](#configure-the-plugin-features) für die Komponente. Zum Beispiel ermöglicht Ihnen das Plug-in `paraformat` das Hinzufügen von semantischen Blockebenenelementen, einschließlich der Erweiterung der Zahl von Überschriftenebenen, die über die standardmäßigen Ebenen `H1`, `H2` und `H3` hinausgeht.

Der RTE ist in einer Vielzahl von Komponenten für die Touch-optimierte Benutzeroberfläche und die klassische Benutzeroberfläche verfügbar. Die primäre Komponente, die den RTE verwendet, ist jedoch die Komponente **Text**, die für beide Benutzeroberflächen verfügbar ist. Auf den folgenden Bildern wird der RTE mit einer Reihe von Plug-ins aktiviert, einschließlich `paraformat`:

![Textkomponente (RTE) im Vollbildmodus in der Touch-optimierten Benutzeroberfläche.](assets/chlimage_1-206.png)

*Abbildung: Die Textkomponente in der Touch-optimierten Benutzeroberfläche.*

![Bearbeitungsdialogfeld (RTE) der Textkomponente in der klassischen Benutzeroberfläche.](assets/chlimage_1-207.png)

*Abbildung: Die Textkomponente in der klassischen Benutzeroberfläche.*

Die Unterschiede zwischen den in den verschiedenen Benutzeroberflächen verfügbaren RTE-Funktionen finden Sie unter [Plug-ins und ihre Funktionen](/help/sites-administering/rich-text-editor.md#aboutplugins).

## Konfigurieren der Plug-in-Funktionen {#configure-the-plugin-features}

Alle Anweisungen zum Konfigurieren von RTE finden Sie auf der Seite [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md). Dies deckt alles ab, einschließlich der wichtigen Schritte:

* [Plug-ins und die Funktionen](/help/sites-administering/rich-text-editor.md#aboutplugins).
* [Konfigurationsspeicherorte](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
* [Aktivieren eines Plug-ins und Konfigurieren der features-Eigenschaft](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
* [Konfigurieren anderer RTE-Funktionen](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).

Durch das Konfigurieren eines Plug-ins innerhalb des entsprechenden `rtePlugins`-Unterzweigs in CRXDE Lite können Sie entweder alle oder bestimmte Funktionen für das Plug-in aktivieren.

![Beispiel für ein rtePlugin in CRXDE Lite](assets/chlimage_1-208.png)

### Beispiel – Angeben von im RTE-Auswahlfeld verfügbaren Absatzformaten {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Neue semantische Blockformate können wie folgt zur Auswahl bereitgestellt werden:

1. Legen Sie den [Konfigurationsspeicherort](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations) abhängig von Ihrem RTE fest und navigieren Sie dorthin.
1. [Absatzauswahlfeld aktivieren](/help/sites-administering/rich-text-editor.md)durch [Aktivieren des Plug-ins](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Geben Sie die Formate an, die im Absatzauswahlfeld verfügbar sein sollen](/help/sites-administering/rich-text-editor.md).
1. Die Absatzformate sind dann für den Autor der Inhalte aus den Auswahlfeldern im RTE verfügbar. Auf sie kann wie folgt zugegriffen werden:

   * Mithilfe des Absatzzeichens (Pilcrow-Symbol) in der Touch-optimierten Benutzeroberfläche.
   * Mithilfe des Feldes **Format** (Popup-Auswahl) in der klassischen Benutzeroberfläche.

Mit Strukturelementen, die im RTE über die Absatzformatoptionen verfügbar sind, bietet AEM eine gute Grundlage für die Entwicklung barrierefreier Inhalte. Inhaltsautoren können den RTE für die Formatierung der Schriftgröße, der Farben oder anderer verwandter Attribute verwenden und dadurch die Erstellung einer Inline-Formatierung verhindern. Stattdessen müssen sie die entsprechenden Strukturelemente wie Überschriften auswählen und globale Stile verwenden, die über die Option Stile ausgewählt wurden. Dadurch wird das Markup bereinigt, Benutzer, die mit ihren eigenen Stylesheets navigieren, erhalten bessere Optionen und korrekt strukturierte Inhalte.

## Verwenden der Funktion „Quellenbearbeitung“ {#use-of-the-source-edit-feature}

In einigen Fällen halten Inhaltsautoren es für erforderlich, den mithilfe des RTE erstellten HTML-Quell-Code zu untersuchen und anzupassen. Beispielsweise kann ein innerhalb des RTE erstellter Inhalt zusätzliches Markup erfordern, um die Einhaltung von WCAG 2.0 sicherzustellen. Dies kann mit der [Quellbearbeitung](/help/sites-administering/rich-text-editor.md#aboutplugins) -Option des RTE. Sie können die Funktion [`sourceedit` im Plug-in `misctools` angeben](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Gehen Sie beim Verwenden der Funktion `sourceedit` sorgfältig vor. Tippfehler und/oder nicht unterstützte Funktionen können zusätzliche Probleme hervorrufen.

## Hinzufügen von Unterstützung für weitere HTML-Elemente und -Attribute {#add-support-for-more-html-elements-and-attributes}

Um die Barrierefreiheitsfunktionen von AEM weiter auszubauen, ist es möglich, die vorhandenen Komponenten basierend auf dem RTE (wie die Komponenten **Text** und **Tabelle**) um zusätzliche Elemente und Attribute zu erweitern.

Die folgende Vorgehensweise stellt dar, wie die Komponente **Tabelle** mit einem Element **Beschriftung** erweitert werden kann, das Informationen zu einer Datentabelle für Benutzer von Hilfstechnologie bereitstellt:

### Beispiel – Hinzufügen der Beschriftung zum Dialogfeld „Tabelleneigenschaften“ {#example-adding-the-caption-to-the-table-properties-dialog}

Fügen Sie im Konstruktor von `TablePropertiesDialog` ein zusätzliches Texteingabefeld hinzu, dass für die Bearbeitung der Beschriftung verwendet wird. Beachten Sie Folgendes: `itemId` muss auf `caption` (d. h. der Name des DOM-Attributs), um seinen Inhalt automatisch zu verarbeiten.

Unter **Tabelle** müssen Sie das Attribut explizit zum/vom DOM-Element festlegen/entfernen. Der Wert wird vom Dialogfeld im `config`-Objekt weitergegeben. Beachten Sie, dass DOM-Attribute mithilfe der entsprechenden `CQ.form.rte.Common`-Methoden (`com` ist kurz für `CQ.form.rte.Common`) festgelegt/entfernt werden sollten, um die üblichen Fallstricke bei Browser-Implementierungen zu vermeiden.

>[!NOTE]
>
>Dieses Verfahren eignet sich nur für die klassische Benutzeroberfläche.

### Beispiel – Erstellen von barrierefrei zugänglichem HTML-Code, wenn Hervorhebungen im Text verwendet werden {#create-accessible-html-for-text}

RTE kann `strong`- und `em`-Tags anstelle von `b` und `i` verwenden. Fügen Sie den folgenden Knoten als gleichrangiges Element zum `uiSettings` und `rtePlugins` -Knoten im Dialogfeld.

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

1. Starten Sie CRXDE Lite. Beispiel: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Kopieren Sie:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   in:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Sie müssen Zwischenordner erstellen, falls diese nicht bereits vorhanden sind.

1. Kopieren Sie:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   in:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js` möglich.

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

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js` möglich.

1. Fügen Sie den folgenden Code am Ende der `transferConfigToTable`-Methode hinzu:

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
>Ein „Nur Text“-Feld ist die einzige zulässige Eingabeart für den Wert des „caption“-Elements. Sie können jedes ExtJS-Widget verwenden, das den Wert der Beschriftung mit der `getValue()`-Methode angibt.
>
>Um Bearbeitungsfunktionen für weitere Elemente und Attribute hinzuzufügen, stellen Sie sicher, dass sowohl:
>
>* Die `itemId`-Eigenschaft zu jedem entsprechenden Feld auf den Namen des entsprechenden DOM-Attributs (`TablePropertiesDialog`) eingestellt ist.
>* Das Attribut explizit für das DOM-Element festgelegt und/oder entfernt wird (`Table`).

>[!MORELIKETHIS]
>
>* [Kurzanleitung zu WCAG 2.0](/help/managing/qg-wcag.md)
>* [Erstellen barrierefreier Inhalte (gemäß WCAG 2.0)](/help/sites-authoring/creating-accessible-content.md)
