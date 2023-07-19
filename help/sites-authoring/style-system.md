---
title: Stilsystem
seo-title: Style System
description: Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.
seo-description: The Style System allows a template author to define style classes in the content policy of a component so that a content author is able to select them when editing the component on a page. These styles can be alternative visual variations of a component, making it more flexible.
uuid: 0d857650-8738-49e6-b431-f69c088be74f
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: e3ccddb6-be5e-4e5f-a017-0eed263555ce
exl-id: 1772368a-f5c9-440c-a92a-0f1d34cc4bf8
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 67%

---

# Stilsystem{#style-system}

Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um die Komponente flexibler zu gestalten.

Dadurch entfällt die Notwendigkeit, eine benutzerdefinierte Komponente für jeden Stil zu entwickeln oder das Komponentendialogfeld anzupassen, um eine solche Stilfunktion zu aktivieren. Das Resultat sind mehr wiederverwendbare Komponenten, die schnell und einfach an die Bedürfnisse von Inhaltsautoren angepasst werden können, ohne dass eine AEM-Backend-Entwicklung erforderlich ist.

## Nutzungsszenario {#use-case}

Vorlagenautoren benötigen nicht nur die Möglichkeit, die Funktionsweise von Komponenten für Inhaltsautoren zu konfigurieren, sondern auch eine Reihe alternativer visueller Varianten einer Komponente zu konfigurieren.

Ebenso müssen Inhaltsautoren nicht nur die Möglichkeit haben, ihren Inhalt zu strukturieren und anzuordnen, sondern auch auswählen können, wie er visuell dargestellt wird.

Das Stilsystem bietet eine einheitliche Lösung für die Anforderungen des Vorlagenautors und des Inhaltsautors:

* Vorlagenautoren können in der Inhaltsrichtlinie von Komponenten Stilklassen definieren.
* Inhaltsautoren können diese Klassen dann in einer Dropdown-Liste auswählen, wenn sie die Komponente auf einer Seite bearbeiten, um die entsprechenden Stile anzuwenden.

Die Stilklasse wird dann in das Decoration-Wrapper-Element der Komponente eingefügt, damit der Komponentenentwickler nicht über die Bereitstellung seiner CSS-Regeln hinaus mit der Verarbeitung der Stile befasst sein muss.

## Übersicht {#overview}

Die allgemeine Verwendung des Stilsystems sieht wie folgt aus.

1. Der Webdesigner erstellt unterschiedliche visuelle Varianten einer Komponente.

1. Dem HTML-Entwickler werden die HTML-Ausgabe der Komponenten sowie die zu implementierenden visuellen Varianten zur Verfügung übermittelt.

1. Der HTML-Entwickler definiert die CSS-Klassen, die der jeweiligen visuellen Variante entsprechen und die in das Wrapper-Element der Komponenten eingefügt werden sollen.

1. Der HTML-Entwickler implementiert den entsprechenden CSS-Code (und optional JS-Code) für die einzelnen visuellen Varianten, damit diese wie definiert angezeigt werden.

1. Der AEM-Entwickler legt den bereitgestellten CSS-Code (und optional JS-Code) in einer [Client-Bibliothek](/help/sites-developing/clientlibs.md) ab und stellt ihn bereit.

1. Der AEM-Entwickler oder der Vorlagenautor konfiguriert die Seitenvorlagen und bearbeitet die Richtlinien für die formatierten Komponenten mit den definierten CSS-Klassen. Dabei legt er benutzerfreundliche Namen für die einzelnen Stile fest und definiert, welche Stile kombiniert werden können.

1. Der AEM-Seitenautor kann die entworfenen Stile daraufhin über das Stilmenü in der Symbolleiste einer Komponente im Seiteneditor auswählen.

Beachten Sie, dass nur die letzten drei Schritte in AEM ausgeführt werden. Dies bedeutet, dass die gesamte Entwicklung des erforderlichen CSS und JavaScript ohne AEM durchgeführt werden kann.

Für die eigentliche Bereitstellung der Stile ist nur die Bereitstellung in AEM sowie die Auswahl innerhalb der Komponenten der gewünschten Vorlagen erforderlich.

Das folgende Diagramm veranschaulicht die Architektur des Stilsystems.

![aem-style-system](assets/aem-style-system.png)

## Verwenden Sie {#use}

Zur Veranschaulichung der Funktion werden wir die [WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de)-Implementierung der Komponente [Titel](https://www.adobe.com/go/aem_cmp_title_v2_de) der Kernkomponente als Beispiel verwenden.

In den folgenden Abschnitten [Als Inhaltsautor](#as-a-content-author) und [Als Vorlagenautor](#as-a-template-author) wird beschrieben, wie Sie die Funktionalität des Stilsystems mit dem WKND-Stilsystem testen können.

Wenn Sie das Stilsystem für Ihre eigenen Komponenten verwenden möchten, gehen Sie wie folgt vor:

1. Installieren Sie die CSS als Client-Bibliotheken, wie im Abschnitt beschrieben [Übersicht](#overview).
1. Konfigurieren Sie die CSS-Klassen, die Sie Ihren Inhaltsautoren zur Verfügung stellen möchten, wie im Abschnitt beschrieben. [Als Vorlagenautor](#as-a-template-author).
1. Inhaltsautoren können dann die Stile wie im Abschnitt beschrieben verwenden [Als Inhaltsautor](#as-a-content-author).

### Als Inhaltsautor {#as-a-content-author}

1. Gehen Sie nach der Installation des WKND-Projekts zur englischsprachigen Primär-Homepage von WKND unter `http://<host>:<port>/sites.html/content/wknd/language-masters/en` und bearbeiten Sie die Seite.
1. Wählen Sie weiter unten auf der Seite eine Komponente **Titel** aus

   ![Stilsystem für den Autor](assets/style-system-author.png)

1. Tippen oder klicken Sie auf die Schaltfläche **Stile** in der Symbolleiste der Komponente **Liste**, um das Stilmenü zu öffnen und das Erscheinungsbild der Komponente zu bearbeiten.

   ![Auswählen von Stilen](assets/style-system-author2.png)

   >[!NOTE]
   >
   >In diesem Beispiel schließen sich die **Farbstile** (**Schwarz**, **Weiß** und **Grau**) gegenseitig aus, während die **Stiloptionen** (**Unterstrichen**, **Rechtsbündig ausrichten** und **Mini-Abstand**) kombiniert werden können. Dies kann [vom Vorlagenautor in der Vorlage konfiguriert werden](#as-a-template-author).

### Als Vorlagenautor {#as-a-template-author}

1. Bei der Bearbeitung der englischsprachigen Primär-Homepage von WKND unter `http://<host>:<port>/sites.html/content/wknd/language-masters/en` können Sie die Vorlage der Seite über **Seiteninformationen > Vorlage bearbeiten** anpassen.

   ![Vorlage bearbeiten](assets/style-system-edit-template.png)

1. Bearbeiten Sie die Richtlinien für die Komponente **Titel**, indem Sie auf die Schaltfläche **Richtlinie** der Komponente klicken.

   ![Richtlinie bearbeiten](assets/style-system-edit-policy.png)

1. Auf der Registerkarte „Stile“ in den Eigenschaften können Sie sehen, wie die Stile konfiguriert wurden.

   ![Eigenschaften bearbeiten](assets/style-system-properties.png)

   * **Gruppenname:** Stile können im Stilmenü gruppiert werden, das dem Inhaltsautor angezeigt wird, während er den Stil einer Komponente konfiguriert.
   * **Stile können kombiniert werden:** Ermöglicht die gleichzeitige Auswahl mehrerer Stile innerhalb dieser Gruppe.
   * **Stilname:** Die Beschreibung des Stils, der dem Inhaltsautor beim Konfigurieren des Komponentenstils angezeigt wird.
   * **CSS-Klassen:** Der tatsächliche Name der CSS-Klasse, die mit dem Stil verknüpft ist.

   Verwenden Sie die Ziehpunkte, um die Reihenfolge der Gruppen und Stile innerhalb der Gruppen anzuordnen. Verwenden Sie die Symbole zum Hinzufügen oder Löschen, um Gruppen oder Stile innerhalb der Gruppen hinzuzufügen oder zu entfernen.

>[!CAUTION]
>
>Die als Stil-Eigenschaften einer Komponentenrichtlinie konfigurierten CSS-Klassen (sowie das erforderliche JavaScript) müssen als [Client-Bibliotheken](/help/sites-developing/clientlibs.md) um zu arbeiten.

## Einrichtung {#setup}

Die Kernkomponenten ab Version 2 können die Vorteile des Stilsystems voll nutzen und erfordern keine zusätzliche Konfiguration.

Die folgenden Schritte sind nur erforderlich, um das Stilsystem für Ihre eigenen benutzerdefinierten Komponenten zu aktivieren oder um die [optionale Registerkarte „Stile“ im Dialogfeld „Bearbeiten“ zu aktivieren](#enable-styles-tab-edit).

### Aktivieren der Registerkarte „Stil“ im Dialogfeld „Design“ {#enable-styles-tab-design}

Damit eine Komponente mit dem Stilsystem von AEM verwendet werden kann und die Registerkarte „Stil“ im Dialogfeld „Design“ angezeigt wird, muss der Komponentenentwickler die Registerkarte „Stil“ mit den folgenden Einstellungen für die Komponente miteinbeziehen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

Wenn die Komponente konfiguriert ist, werden die von den Seitenautoren konfigurierten Stile automatisch von AEM in das Decoration-Element eingefügt, das AEM automatisch um jede bearbeitbare Komponente umschließt. Dafür ist keine weitere Aktion der Komponente erforderlich.

### Aktivieren der Registerkarte „Stile“ im Dialogfeld „Bearbeiten“ {#enable-styles-tab-edit}

Ab AEM-Version 6.5.3.0 ist jetzt eine optionale Registerkarte „Stile“ im Dialogfeld „Bearbeiten“ verfügbar. Im Gegensatz zur Registerkarte im Dialogfeld „Design“ ist die Registerkarte im Dialogfeld „Bearbeiten“ für die Funktion des Stilsystems nicht unbedingt erforderlich. Sie stellt jedoch eine optionale alternative Oberfläche dar, über die ein Inhaltsautor Stile festlegen kann.

Die Registerkarte für das Bearbeitungsdialogfeld kann auf ähnliche Weise wie die Registerkarte für das Dialogfeld „Design“ eingebunden werden:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_edit/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>
>Die Registerkarte „Stile“ im Dialogfeld „Bearbeiten“ ist standardmäßig nicht aktiviert.

### Stile mit Elementnamen {#styles-with-element-names}

Mit der String-Array-Eigenschaft `cq:styleElements` können Entwickler auch eine Liste der zulässigen Elementnamen für Stile in der Komponente konfigurieren. Anschließend kann der Vorlagenautor auf der Registerkarte &quot;Stile&quot;der Richtlinie im Dialogfeld &quot;Design&quot;auch einen Elementnamen auswählen, der für jeden Stil festgelegt werden soll. Dadurch wird der Elementname des Wrapper-Elements festgelegt.

Diese Eigenschaft wird auf dem Knoten `cq:Component` festgelegt. Beispiel:

* `/apps/<yoursite>/components/content/list@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Vermeiden Sie das Definieren von Elementnamen für Stile, die kombiniert werden können. Wenn mehrere Elementnamen definiert sind, lautet die Priorität:
>
>1. HTL hat stets den Vorrang: `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Danach wird unter mehreren aktiven Stilen der erste Stil in der Liste der in der Komponentenrichtlinie konfigurierten Stile ausgewählt.
>1. Die Werte `cq:htmlTag`/ `cq:tagName` der Komponente werden schließlich als Ausweichwert verwendet.
>

Die Fähigkeit, Stilnamen zu definieren, ist bei sehr generischen Komponenten wie dem Layout-Container oder der Inhaltsfragmentkomponente hilfreich, um diesen eine zusätzliche Bedeutung zu verleihen.

Zum Beispiel können einem Layout-Container so Semantik-Elemente wie `<main>`, `<aside>`, `<nav>` usw. zugewiesen werden.
