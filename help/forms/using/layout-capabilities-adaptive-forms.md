---
title: Layout-Möglichkeiten für adaptive Formulare
seo-title: Layout capabilities of adaptive forms
description: Layout und Darstellung adaptiver Formulare auf verschiedenen Geräten unterliegen den Layouteinstellungen. Machen Sie sich mit den verschiedenen Layouts und ihrer Anwendung vertraut.
seo-description: Layout and appearances of adaptive forms on various devices are governed by the layout settings. Understand the various layouts and how to apply them.
uuid: 79022ac2-1aa3-47c5-b094-cbe83334ea62
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 9459c414-eac9-4bd9-a773-cceaeb736c56
docset: aem65
feature: Adaptive Forms
exl-id: 3db623a4-f1ad-4b7f-97e8-0be138aa8b26
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 100%

---

# Layout-Möglichkeiten für adaptive Formulare{#layout-capabilities-of-adaptive-forms}

Mit Adobe Experience Manager (AEM) können Sie benutzerfreundliche adaptive Formulare erstellen, den Endbenutzern eine dynamische Erfahrung bietet. Mit dem Formular-Layout wird gesteuert, wie Elemente bzw. Komponenten auf einem adaptiven Formular angezeigt werden.

## Vorausgesetztes Wissen {#prerequisite-knowledge}

Bevor Sie die verschiedenen Layoutfunktionen adaptiver Formulare kennenlernen, lesen Sie die folgenden Artikel, um mehr über adaptive Formulare zu erfahren.

[Einführung in AEM Forms](../../forms/using/introduction-aem-forms.md)

[Einführung in die Erstellung von Formularen](../../forms/using/introduction-forms-authoring.md)

## Typen von Layouts {#types-of-layouts}

In adaptiven Formularen stehen Ihnen die folgenden Layouttypen zur Verfügung:

**Bereichslayout** Steuert, wie in einem Bereich befindliche Elemente oder Komponenten auf einem Gerät angezeigt werden.

**Layout für Mobilgeräte** Steuert die Navigation eines Formulars auf einem mobilen Gerät. Wenn das Gerät eine Breite von mindestens 768 Pixel aufweist, wird das Layout als Layout für Mobilgeräte betrachtet und für Mobilgeräte optimiert.

**Symbolleisten-Layout** Steuert die Platzierung von Aktionsschaltflächen in der Symbolleiste bzw. in der Bereichssymbolleiste in einem Formular.

Alle diese Bedienfeldlayouts werden in den folgenden Verzeichnissen definiert:

`/libs/fd/af/layouts`.

>[!NOTE]
>
>Um das Layout eines adaptiven Formulars zu ändern, verwenden Sie den Bearbeitungsmodus in AEM.

![Speicherort von Layouts im CRX-Repository](assets/layouts_location_in_crx.png)

## Bereichslayout {#panel-layout}

Formularersteller können jedem Bedienfeld eines adaptiven Formulars ein Layout zuordnen, einschließlich des Stammbedienfelds.

Die Bereichslayouts stehen unter `/libs/fd/af/layouts/panel` zur Verfügung.

![Liste der Bedienfeldlayouts für das Stammbedienfeld eines adaptiven Formulars](assets/layouts.png)

Liste der Bedienfeldlayouts in den adaptiven Formularen

### Responsiv – alles auf einer Seite ohne Navigation {#responsive-everything-on-one-page-without-navigation-br}

Verwenden Sie dieses Bereichslayout, um ein responsives Layout zu erstellen, das sich ohne spezielle Navigation an die Bildschirmgröße Ihres Geräts anpasst.

Mithilfe dieses Layouts können Sie in das Bedienfeld nacheinander mehrere Komponenten für **[!UICONTROL Bedienfelder für adaptive Formulare]** einfügen.

![So sieht ein Formular mit einem responsiven Layout auf einem kleinen Bildschirm aus](assets/responsive_layout_seen_on_small_screen.png)

So sieht ein Formular mit einem responsiven Layout auf einem kleinen Bildschirm aus

![Formular mit einem reaktionsfähigem Layout auf einem großen Bildschirm](assets/responsive_layout_seen_on_large_screen.png)

Formular mit einem reaktionsfähigem Layout auf einem großen Bildschirm

### Assistent – ein Mehrstufenformular, bei dem jeder einzelne Schritt genau angezeigt wird {#wizard-a-multi-step-form-showing-one-step-at-a-time}

Verwenden Sie dieses Bereichslayout, um innerhalb eines Formulars eine geführte Navigation anzubieten. Beispielsweise können Sie dieses Layout verwenden, wenn Sie in einem Formular obligatorische Informationen erfassen und dabei die Benutzer Schritt für Schritt anleiten möchten.

Verwenden Sie die `Panel adaptive form`-Komponente, um in einem Bedienfeld eine schrittweise Navigation zur Verfügung zu stellen. Wenn Sie dieses Layout verwenden, gehen Benutzer erst dann zum nächsten Schritt über, wenn der aktuelle Schritt abgeschlossen ist.

```javascript
window.guideBridge.validate([], this.panel.navigationContext.currentItem.somExpression)
```

![Ausdruck für das Abschließen von Schritten im Assistentenlayout für ein Mehrstufenformular](assets/layout-sidebar.png)

Ausdruck für das Abschließen von Schritten im Assistentenlayout für ein Mehrstufenformular

![Ein Formular mit dem Assistentenlayout](assets/wizard-layout.png)

Ein Formular, das den Assistenten verwendet

### Layout für Akkordeon-Design {#layout-for-accordion-design}

Mit diesem Layout können Sie die `Panel adaptive form`-Komponente in ein Bedienfeld mit Navigation im Akkordeonstil einfügen. Mit diesem Layout können Sie außerdem wiederholbare Bereiche erstellen. Wiederholbare Bereiche ermöglichen es Ihnen, Bereiche nach Bedarf hinzuzufügen oder zu entfernen. Sie können dabei festlegen, wie oft sich ein Bereich mindestens oder maximal wiederholen darf. Außerdem kann anhand der in den Bereichselementen angegebenen Informationen der Titel des Bereichs dynamisch festgelegt werden.

Ein Zusammenfassungsausdruck kann verwendet werden, um im Titel des minimierten Bereichs die vom Endbenutzer eingegebenen Werte anzuzeigen.

![Wiederholbare Bedienfelder mit Akkordeonlayout in adaptiven Formularen](assets/repeatable_panels_using_accordion_layout.png)

Mit dem Akkordeonlayout erstellte wiederholbare Bedienfelder

### Layout mit Registerkarten – Registerkarten werden auf der linken Seite angezeigt {#tabbed-layout-tabs-appear-on-the-left}

Mithilfe dieses Layouts können Sie die `Panel adaptive form`-Komponente in ein Bedienfeld mit Registerkartennavigation einfügen. Die Registerkarten befinden sich auf der linken Seite der Bereichsinhalte.

![Im Layout mit Registerkarten werden die Registerkarten links angezeigt](assets/tabbed_layout_left.png)

Registerkarten auf der linken Seite eines Bereichs

### Layout mit Registerkarten – Registerkarten werden oben angezeigt {#tabbed-layout-tabs-appear-on-the-top}

Mithilfe dieses Layouts können Sie die `Panel adaptive form`-Komponente in ein Bedienfeld mit Registerkartennavigation einfügen. Die Registerkarten befinden sich oberhalb der Bereichsinhalte.

![Layout mit Registerkarten in adaptiven Formen mit Registerkarten am oberen Rand](assets/tabbed_layout_top.png)

Registerkarten oberhalb des Bedienfelds

## Layouts für Mobilgeräte {#mobile-layouts}

Layouts für Mobilgeräte ermöglichen eine benutzerfreundliche Navigation auf mobilen Geräten mit relativ kleinen Bildschirmen. Bei Layouts für Mobilgeräte werden für die Formularnavigation entweder Registerkarten oder Assistenten verwendet. Durch die Anwendung eines Layouts für Mobilgeräte wird für das gesamte Formular ein einziges Layout zur Verfügung gestellt.

Dieses Layout steuert die Navigation mit einer Navigationsleiste und einem Hauptnavigationsmenü. In der Navigationsleiste befinden sich die Symbole **&lt;** und **>**, um den **nächsten** und den **vorigen** Navigationsschritt im Formular anzuzeigen.

Die Layouts für Mobilgeräte sind unter `/libs/fd/af/layouts/mobile/` verfügbar. Die folgenden Layouts für Mobilgeräte stehen für adaptive Formulare standardmäßig zur Verfügung.

![Liste der Layouts für Mobilgeräte in adaptiven Formularen](assets/mobile-navigation.png)

Liste der Layouts für Mobilgeräte in adaptiven Formularen

Bei einem Layout für Mobilgeräte ist das Formularmenü (über das auf verschiedene Formularbereiche zugegriffen werden kann) per Klick auf das Symbol ![aem6forms_form_menu](assets/aem6forms_form_menu.png) verfügbar.

### Layout mit Bereichstiteln in der Formularkopfzeile {#layout-with-panel-titles-in-the-form-header}

Wie der Name schon sagt, werden bei diesem Layout neben dem Navigationsmenü und der Navigationsleiste Bedienfeldtitel angezeigt. Außerdem enthält dieses Layout Symbole für „Nächste“ und „Vorherige“ zur Navigation.

![Layouts für Mobilgeräte mit Bereichstiteln in den Formularkopfzeilen](assets/mobile_layout_with.png)

Layouts für Mobilgeräte mit Bereichstiteln in den Formularkopfzeilen

### Layout ohne Bereichstitel in der Formularkopfzeile {#layout-without-panel-titles-in-the-form-header}

Wie der Name schon sagt, werden bei diesem Layout nur das Navigationsmenü und die Navigationsleiste ohne Bedienfeldtitel angezeigt. Außerdem enthält dieses Layout Symbole für „Nächste“ und „Vorherige“ zur Navigation.

![Layouts für Mobilgeräte ohne Bereichstitel in den Formularkopfzeilen](assets/mobile_layout_without.png)

Layouts für Mobilgeräte ohne Bereichstitel in den Formularkopfzeilen

## Symbolleistenlayouts {#toolbar-layouts}

Mit einem Symbolleistenlayout werden Positionierung und Anzeige aller Aktionsschaltflächen gesteuert, die Sie Ihren adaptiven Formularen hinzufügen. Das Layout kann auf Formular- oder Bedienfeldebene hinzugefügt werden.

![Liste der Symbolleistenlayouts in adaptiven Formularen zur Steuerung des Schaltflächenlayouts](assets/toolbar-layouts.png)

Liste der Symbolleistenlayouts in adaptiven Formularen

Die Symbolleistenlayouts befinden sich unter `/libs/fd/af/layouts/toolbar`. Adaptive Formulare stehen in den folgenden Symbolleistenlayouts standardmäßig zur Verfügung.

### Standardlayout für Symbolleiste {#default-layout-for-toolbar}

Dieses Layout wird als Standardlayout ausgewählt, wenn Sie einem adaptiven Formular Aktionsschaltflächen hinzufügen. Bei Auswahl dieses Layouts wird sowohl bei Desktop- als auch bei Mobilgeräten dasselbe Layout angezeigt.

Außerdem können Sie mehrere Symbolleisten mit Aktionsschaltflächen hinzufügen, die mit diesem Layout konfiguriert wurden. Eine Aktionsschaltfläche ist mit einem Formularsteuerelement verknüpft. Sie können die Werkzeugleisten so konfigurieren, dass sie sich vor oder nach einem Bedienfeld befinden.

![Standardansicht für Symbolleiste](assets/toolbar_layout_default.png)

Standardansicht für Symbolleiste

### Festes Layout für Mobilgeräte für Symbolleiste {#mobile-fixed-layout-for-toolbar}

Wählen Sie dieses Layout aus, um für Desktop- und Mobilgeräte alternative Layouts zur Verfügung zu stellen.

Für das Desktoplayout können Sie mithilfe bestimmter Beschriftungen Aktionsschaltflächen hinzufügen. Mit diesem Layout kann nur eine Symbolleiste konfiguriert werden. Wenn mit diesem Layout mehr als eine Symbolleiste konfiguriert wird, gibt es bei mobilen Geräten Überlagerungen und es ist nur eine Symbolleiste sichtbar. Sie können beispielsweise eine Symbolleiste am oberen oder unteren Rand des Formulars oder vor oder nach den Bedienfeldern im Formular einfügen.

Beim Layout für Mobilgeräte können Sie mithilfe von Symbolen Aktionsschaltflächen hinzufügen.

![Festes Layout für Mobilgeräte für Symbolleiste](assets/toolbar_layout_mobile_fixed.png)

Festes Layout für Mobilgeräte für Symbolleiste
