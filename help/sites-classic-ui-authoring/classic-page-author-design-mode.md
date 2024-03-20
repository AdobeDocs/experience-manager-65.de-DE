---
title: Konfigurieren von Komponenten im Design-Modus
description: Wenn die AEM-Instanz vorkonfiguriert installiert wird, steht im Sidekick sofort eine Auswahl von Komponenten zur Verfügung. Darüber hinaus stehen auch verschiedene weitere Komponenten zur Verfügung. Sie können den Design-Modus verwenden, um diese Komponenten zu aktivieren/deaktivieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: cb2d2d0d-feb4-4b89-8325-80f735816904
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 100%

---

# Konfigurieren von Komponenten im Design-Modus{#configuring-components-in-design-mode}

Wenn die AEM-Instanz vorkonfiguriert installiert wird, steht im Sidekick sofort eine Auswahl von Komponenten zur Verfügung.

Darüber hinaus sind auch verschiedene weitere Komponenten verfügbar. Mit dem [Design-Modus](#enabledisablecomponentsusingdesignmode) können Sie diese Komponenten aktivieren/deaktivieren. Wenn Sie den Design-Modus aktivieren und sich auf der Seite befinden, können Sie damit [Aspekte des Komponenten-Designs konfigurieren](#configuringcomponentsusingdesignmode), indem Sie die Attributparameter bearbeiten.

>[!NOTE]
>
>Bei der Bearbeitung dieser Komponenten ist Vorsicht geboten. Die Designeinstellungen sind häufig ein wesentlicher Bestandteil des Designs der gesamten Website. Daher sollten sie nur von einer Person mit den entsprechenden Berechtigungen (und der erforderlichen Erfahrung) geändert werden (meist ein Administrator oder Entwickler). Weitere Informationen finden Sie unter [Entwicklung von Komponenten](/help/sites-developing/components.md).

Dazu müssen die zulässigen Komponenten im Absatzsystem für die Seite hinzugefügt oder entfernt werden. Das Absatzsystem (`parsys`) ist eine zusammengesetzte Komponente, die alle anderen Absatzkomponenten enthält. Mit dem Absatzsystem können Komponenten unterschiedlicher Typen zu einer Seite hinzugefügt werden, da es alle anderen Absatzkomponenten enthält. Jeder Absatztyp wird als eine Komponente dargestellt.

Beispielsweise kann der Inhalt einer Produktseite ein Absatzsystem enthalten, das Folgendes enthält:

* Ein Bild des Produkts (in Form eines image- oder textimage-Absatzes)
* Die Produktbeschreibung (als text-Absatz)
* Eine Tabelle mit technischen Daten (als table-Absatz)
* Ein Formular, das ausgefüllt werden kann (als forms begin-, forms element- und forms end-Absatz)

>[!NOTE]
>
>Unter [Entwicklung von Komponenten](/help/sites-developing/components.md#paragraphsystem) und [Richtlinien für die Verwendung von Vorlagen und Komponenten](/help/sites-developing/dev-guidelines-bestpractices.md#guidelines-for-using-templates-and-components) finden Sie weitere Informationen zu `parsys`.

## Aktivieren/Deaktivieren von Komponenten {#enable-disable-components}

Im Design-Modus ist der Sidekick minimiert und Sie können die für die Bearbeitung verfügbaren Komponenten konfigurieren:

1. Um in den Design-Modus zu wechseln, öffnen Sie eine Seite zur Bearbeitung und verwenden Sie das Sidekick-Symbol:

   ![Design-Modus](do-not-localize/chlimage_1.png)

1. Klicken Sie im Absatzsystem (**Design von „par“**) auf **Bearbeiten**.

   ![screen_shot_2012-02-08at102726am](assets/screen_shot_2012-02-08at102726am.png)

1. Ein Dialogfeld wird geöffnet, in dem die im Sidekick gezeigten Komponentengruppen zusammen mit den darin enthaltenen individuellen Komponenten aufgeführt sind.

   Wählen Sie die Komponenten, die im Sidekick verfügbar sein sollen, nach Bedarf aus, um sie hinzuzufügen oder zu entfernen.

   ![screen_shot_2012-02-08at103407am](assets/screen_shot_2012-02-08at103407am.png)

1. Der Sidekick wird im Designmodus minimiert. Wenn Sie auf den Pfeil klicken, können Sie den Sidekick maximieren und zum Bearbeitungsmodus zurückkehren:

   ![Sidekick minimiert](do-not-localize/sidekick-collapsed.png)

## Konfigurieren des Designs einer Komponente {#configuring-the-design-of-a-component}

Im Design-Modus können Sie auch Attribute für die einzelnen Komponenten konfigurieren. Jede Komponente verfügt über eigene Parameter. Das folgende Beispiel zeigt die **Bildkomponente**:

1. Um in den Design-Modus zu wechseln, öffnen Sie eine Seite zur Bearbeitung und verwenden Sie das Sidekick-Symbol:

   ![Design-Modus – Sidekick](do-not-localize/chlimage_1-1.png)

1. Sie können das Design von Komponenten konfigurieren.

   Beispiel: Wenn Sie in der Bildkomponente (**Design von „image“**) auf **Bearbeiten** klicken, können Sie die komponentenspezifischen Parameter konfigurieren:

   ![chlimage_1-5](assets/chlimage_1-5.png)

1. Klicken Sie auf **OK**, um die Änderungen zu speichern.

1. Der Sidekick wird im Designmodus minimiert. Wenn Sie auf den Pfeil klicken, können Sie den Sidekick maximieren und zum Bearbeitungsmodus zurückkehren:

   ![Sidekick minimiert](do-not-localize/sidekick-collapsed-1.png)
