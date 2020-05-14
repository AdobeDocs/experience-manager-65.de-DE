---
title: Stilsystem
seo-title: Stilsystem
description: Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.
seo-description: Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.
uuid: 0d857650-8738-49e6-b431-f69c088be74f
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: e3ccddb6-be5e-4e5f-a017-0eed263555ce
translation-type: tm+mt
source-git-commit: 0985ba24f7430381fccc40faf3a316d3abd85a30
workflow-type: tm+mt
source-wordcount: '1365'
ht-degree: 69%

---


# Stilsystem{#style-system}

Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, wodurch die Komponente flexibler wird.

So muss nicht eigens für jeden Stil eine benutzerdefinierte Komponente entwickelt oder der Komponentendialog angepasst werden, um eine derartige Stilfunktionalität zu ermöglichen. Das Resultat sind mehr wiederverwendbare Komponenten, die schnell und einfach an die Bedürfnisse von Inhaltsautoren angepasst werden können, ohne dass eine AEM-Back-End-Entwicklung erforderlich ist.

## Nutzungsszenario   {#use-case}

Vorlagenautoren müssen nicht nur die Funktionsweise der Komponenten für die Inhaltsautoren konfigurieren können, sondern auch eine Reihe alternativer visueller Varianten einer Komponente.

Genauso müssen Inhaltsautoren ihre Inhalte nicht nur strukturieren und anordnen können. Sie müssen auch auswählen können, wie der Inhalt visuell präsentiert wird.

Das Stilsystem bietet eine einheitliche Lösung für die Anforderungen sowohl des Vorlagenautors als auch des Inhaltsautors:

* Vorlagenautoren können in den Inhaltsrichtlinien für Komponenten Stilklassen festlegen.
* Inhaltsautoren können diese Klassen später aus einem Dropdown-Menü auswählen, wenn sie die Komponente auf einer Seite bearbeiten, um die jeweiligen Stile darauf anzuwenden.

Die Stilklasse wird daraufhin in das Decoration-Wrapper-Element der Komponente eingefügt, sodass sich der Komponentenentwickler nicht mit der Handhabung der Stile über die Bereitstellung der CSS-Regeln hinaus befassen muss.

## Übersicht {#overview}

Die Verwendung des Stilsystems nimmt im Allgemeinen folgende Form an.

1. Der Webdesigner erstellt unterschiedliche visuelle Varianten einer Komponente.

1. Dem HTML-Entwickler werden die HTML-Ausgabe der Komponenten sowie die zu implementierenden visuellen Varianten zur Verfügung übermittelt.

1. Der HTML-Entwickler definiert die CSS-Klassen, die der jeweiligen visuellen Variante entsprechen und die in das Wrapper-Element der Komponenten eingefügt werden sollen.

1. Der HTML-Entwickler implementiert den entsprechenden CSS-Code (und optional JS-Code) für die einzelnen visuellen Varianten, damit diese wie definiert angezeigt werden.

1. Der AEM-Entwickler legt den bereitgestellten CSS-Code (und optional JS-Code) in einer [Client-Bibliothek](/help/sites-developing/clientlibs.md) ab und stellt ihn bereit.

1. Der AEM-Entwickler oder der Vorlagenautor konfiguriert die Seitenvorlagen und bearbeitet die Richtlinien für die formatierten Komponenten mit den definierten CSS-Klassen. Dabei legt er benutzerfreundliche Namen für die einzelnen Stile fest und definiert, welche Stile kombiniert werden können.

1. Der AEM-Seitenautor kann die entworfenen Stile daraufhin über das Stilmenü in der Symbolleiste einer Komponente im Seiten-Editor auswählen.

Beachten Sie, dass nur die letzten drei Schritte direkt in AEM ausgeführt werden. Das bedeutet, dass die gesamte erforderliche CSS- und JavaScript-Entwicklung ohne AEM durchgeführt werden kann.

Für die eigentliche Implementierung der Stile ist nur die Bereitstellung in AEM sowie die Auswahl innerhalb der Komponenten der gewünschten Vorlagen erforderlich.

Das folgende Diagramm zeigt die Architektur des Stilsystems.

![aem-style-system](assets/aem-style-system.png)

## Verwenden Sie {#use}

Zur Veranschaulichung der Funktion wird die Implementierung der [Titelkomponente](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)der Kernkomponente [durch](https://www.adobe.com/go/aem_cmp_title_v2) WKNDs verwendet.

The following sections [As a Content Author](#as-a-content-author) and [As a Template Author](#as-a-template-author) describe how to test the functionality of the Style System using the Style System of WKND.

Wenn Sie das Stilsystem für Ihre eigenen Komponenten verwenden möchten, führen Sie folgende Schritte aus:

1. Installieren Sie den CSS-Code als Client-Bibliotheken, wie im Abschnitt [Überblick](#overview) erklärt.
1. Konfigurieren Sie die CSS-Klassen, die Sie Ihren Inhaltsautoren zur Verfügung stellen möchten, wie im Abschnitt [Als Vorlagenautor](#as-a-template-author) beschrieben.
1. Inhaltsautoren können die Stile daraufhin wie im Abschnitt [Als Inhaltsautor](#as-a-content-author) beschrieben verwenden.

### Als Inhaltsautor   {#as-a-content-author}

1. Nach der Installation des WKND-Projekts navigieren Sie zur englischsprachigen Masterseite von WKND `http://<host>:<port>/sites.html/content/wknd/language-masters/en` und bearbeiten Sie die Startseite.
1. Wählen Sie eine **Titel** -Komponente weiter unten auf der Seite

   ![Stilsystem für den Autor](assets/style-system-author.png)

1. Tippen oder klicken Sie auf die Schaltfläche **Stile** in der Symbolleiste der Komponente **Liste**, um das Stilmenü zu öffnen und das Erscheinungsbild der Komponente zu bearbeiten.

   ![Auswählen von Stilen](assets/style-system-author2.png)

   >[!NOTE]
   >
   >In diesem Beispiel schließen sich die **Farbstile** (**Schwarz**, **Weiß** und **Grau**) gegenseitig aus, während die **Stiloptionen**************(,Align RightundMini Spacing) kombiniert werden können. Dies kann [als Vorlagenautor in der Vorlage konfiguriert werden](#as-a-template-author).

### Als Vorlagenautor   {#as-a-template-author}

1. While editing WKND&#39;s English language master home page at `http://<host>:<port>/sites.html/content/wknd/language-masters/en`, edit the template of the page via **Page Information -> Edit Template**.

   ![Vorlage bearbeiten](assets/style-system-edit-template.png)

1. Edit the policy of the **Title** component by tapping or clicking the **Policy** button of the component.

   ![Richtlinie bearbeiten](assets/style-system-edit-policy.png)

1. Auf der Registerkarte „Stile“ in den Eigenschaften können Sie sehen, wie die Stile konfiguriert wurden.

   ![Eigenschaften bearbeiten](assets/style-system-properties.png)

   * **Gruppenname:** Stile können im Stilmenü gruppiert werden, das dem Inhaltsautor angezeigt wird, während er den Stil einer Komponente konfiguriert.
   * **Stile können kombiniert werden:** Legt fest, dass mehrere Stile innerhalb einer Gruppe gleichzeitig ausgewählt werden können.
   * **Stilname:** Die Beschreibung des Stils, der dem Inhaltsautor bei der Konfiguration des Stils der Komponente angezeigt wird.
   * **CSS-Klassen:** Der tatsächliche Name der dem Stil zugeordneten CSS-Klasse.
   Ordnen Sie die Gruppen und die Stile innerhalb der Gruppen mit den Ziehpunkten. Nutzen Sie die Symbole „Hinzufügen“ oder „Löschen“, um Gruppen bzw. Stile innerhalb der Gruppen hinzuzufügen oder zu entfernen.

>[!CAUTION]
>
>The CSS classes (as well as any necessary Javascript) configured as style properties of a component&#39;s policy must be deployed as [Client Libraries](/help/sites-developing/clientlibs.md) in order to work.

## Einrichtung {#setup}

Die Core-Komponenten Version 2 und höher sind vollständig aktiviert, um das Style-System nutzen zu können und erfordern keine zusätzliche Konfiguration.

Die folgenden Schritte sind nur erforderlich, um das Stilsystem für Ihre eigenen benutzerdefinierten Komponenten zu aktivieren oder die optionale Registerkarte &quot;Stile&quot;im Dialogfeld &quot;Bearbeiten&quot;zu [aktivieren.](#enable-styles-tab-edit)

### Registerkarte &quot;Stil&quot;im Dialogfeld &quot;Design&quot;aktivieren {#enable-styles-tab-design}

Damit eine Komponente mit dem AEM-Stilsystem funktioniert und die Stilregisterkarte im Designdialogfeld angezeigt wird, muss der Komponentenentwickler die Stilregisterkarte mit den folgenden Einstellungen für die Komponente einschließen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

Ist die Komponente entsprechend konfiguriert, fügt AEM die von den Seitenautoren festgelegten Stile automatisch in den Decoration-Element-Wrapper ein, der automatisch auf alle bearbeitbaren Komponenten angewendet wird. Dafür ist keine weitere Aktion der Komponente erforderlich.

### Registerkarte &quot;Stile&quot;im Dialogfeld &quot;Bearbeiten&quot;aktivieren {#enable-styles-tab-edit}

Ab AEM Version 6.5.3.0 ist jetzt eine optionale Registerkarte &quot;Stile&quot;im Dialogfeld &quot;Bearbeiten&quot;verfügbar. Anders als bei der Registerkarte &quot;Designdialog&quot;ist die Registerkarte im Dialogfeld &quot;Bearbeiten&quot;nicht unbedingt erforderlich, damit das Stilsystem funktioniert, sondern eine optionale alternative Schnittstelle, über die ein Inhaltsersteller Stile festlegen kann.

Die Registerkarte &quot;Dialogfeld bearbeiten&quot;kann ähnlich wie die Registerkarte &quot;Designdialogfeld&quot;eingefügt werden:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_edit/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>
>Die Registerkarte &quot;Stile&quot;im Dialogfeld &quot;Bearbeiten&quot;ist standardmäßig nicht aktiviert.

### Stile mit Elementnamen   {#styles-with-element-names}

Mit der String-Array-Eigenschaft `cq:styleElements` können Entwickler auch eine Liste der zulässigen Elementnamen für Stile in der Komponente konfigurieren. In der Registerkarte „Stile“ für die Richtlinie im Dialogfeld „Design“ kann der Vorlagenautor außerdem Elementnamen auswählen, die für die einzelnen Stile festgelegt werden sollen. Dadurch wird der Elementname des Wrapper-Elements definiert.

Diese Eigenschaft wird auf dem Knoten `cq:Component` festgelegt. Beispiel:

* `/apps/<yoursite>/components/content/list@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Definieren Sie keine Elementnamen für Stile, die kombiniert werden können. Wenn mehrere Elementnamen definiert werden, gilt die folgende Prioritätsreihenfolge:
>
>1. HTL hat stets den Vorrang: `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Danach wird unter mehreren aktiven Stilen der erste Stil in der Liste der in der Komponentenrichtlinie konfigurierten Stile ausgewählt.
>1. Die Werte `cq:htmlTag`/ `cq:tagName` der Komponente werden schließlich als Ausweichwert verwendet.
>



Die Fähigkeit, Stilnamen zu definieren, ist bei sehr generischen Komponenten wie dem Layout-Container oder der Inhaltsfragmentkomponente hilfreich, um diesen eine zusätzliche Bedeutung zu verleihen.

Zum Beispiel können einem Layout-Container so Semantik-Elemente wie `<main>`, `<aside>`, `<nav>` usw. zugewiesen werden.
