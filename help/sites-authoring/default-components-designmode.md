---
title: Konfigurieren von Standardkomponenten im Design-Modus
description: Konfigurieren von Komponenten im Design-Modus
uuid: b9c9792d-4398-446d-8767-44d4e7ce9a2e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8ae6817a-16d3-4740-b67a-498e75adf350
exl-id: 5e232886-75c1-4f0f-b359-4739ae035fd3
source-git-commit: e85aacd45a2bbc38f10d03915e68286f0a55364e
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 99%

---

# Konfigurieren von Standardkomponenten im Design-Modus{#configuring-components-in-design-mode}

Wenn die AEM-Instanz direkt installiert wird, ist im Komponenten-Browser sofort eine Auswahl von Komponenten verfügbar.

Darüber hinaus sind auch verschiedene weitere Komponenten verfügbar. Mithilfe des [Design-Modus](#enable-disable-components) können Sie diese Komponenten aktivieren bzw. deaktivieren. Wenn Sie den Design-Modus aktivieren und sich auf der Seite befinden, können Sie damit [Aspekte des Komponenten-Designs konfigurieren](#configuring-the-design-of-a-component), indem Sie die Attributparameter bearbeiten.

>[!NOTE]
>
>Bei der Bearbeitung dieser Komponenten ist Vorsicht geboten. Die Designeinstellungen sind häufig ein wesentlicher Bestandteil des Designs der gesamten Website. Daher sollten sie nur von einer Person mit den entsprechenden Berechtigungen (und der erforderlichen Erfahrung) geändert werden (meist ein Administrator oder Entwickler). Weitere Informationen finden Sie unter [Entwicklung von Komponenten](/help/sites-developing/components.md).

>[!NOTE]
>
>Der Design-Modus steht nur für statische Vorlagen zur Verfügung. Vorlagen, die mit bearbeitbaren Vorlagen erstellt wurden, sollten mit dem [Vorlageneditor](/help/sites-authoring/templates.md) bearbeitet werden.

>[!NOTE]
>
>Der Design-Modus ist nur für Design-Konfigurationen verfügbar, die als Inhalt unter ( `/etc`) gespeichert sind.
>
>Ab AEM 6.4 wird empfohlen, Designs als Konfigurationsdaten unter `/apps` zu speichern, um kontinuierliche Bereitstellungsszenarien zu unterstützen. Unter `/apps` gespeicherte Designs können nicht zur Laufzeit bearbeitet werden. Außerdem steht der Design-Modus in Bezug auf diese Vorlagen ausschließlich Admins zur Verfügung.

Dazu müssen die zulässigen Komponenten im Absatzsystem für die Seite hinzugefügt oder entfernt werden. Das Absatzsystem (`parsys`) ist eine zusammengesetzte Komponente, die alle anderen Absatzkomponenten enthält. Mit dem Absatzsystem können Komponenten unterschiedlicher Typen zu einer Seite hinzugefügt werden, da es alle anderen Absatzkomponenten enthält. Jeder Absatztyp wird als eine Komponente dargestellt.

Beispielsweise kann der Inhalt einer Produktseite ein Absatzsystem enthalten, das Folgendes enthält:

* Ein Bild des Produkts (in Form eines image- oder textimage-Absatzes)
* Die Produktbeschreibung (als text-Absatz)
* Eine Tabelle mit technischen Daten (als table-Absatz)
* Ein Formular, das ausgefüllt werden kann (als forms begin-, forms element- und forms end-Absatz)

>[!NOTE]
>
>Unter [Entwicklung von Komponenten](/help/sites-developing/components.md) und [Richtlinien für die Verwendung von Vorlagen und Komponenten](/help/sites-developing/dev-guidelines-bestpractices.md#guidelines-for-using-templates-and-components) finden Sie weitere Informationen zu `parsys`.

>[!CAUTION]
>
>Bearbeiten des Designs im Design-Modus wie in diesem Artikel beschrieben ist die empfohlene Vorgehensweise zum Definieren von Designs statischer Vorlagen
>
>Das Ändern von Designs in CRX DE ist beispielsweise nicht ratsam und die Anwendung derartiger Designs kann von erwarteten Verhaltensweisen abweichen. Weitere Informationen finden Sie im Entwicklerdokument [Seitenvorlagen – statisch](/help/sites-developing/page-templates-static.md#how-template-designs-are-applied).

## Aktivieren/Deaktivieren von Komponenten {#enable-disable-components}

So aktivieren oder deaktivieren Sie eine Komponente:

1. Wechseln Sie in den **Design-Modus**.

   ![screen_shot_2018-03-22at103113](assets/screen_shot_2018-03-22at103113.png)

1. Tippen oder klicken Sie auf eine Komponente. Diese Komponente wird mit einem blauen Rahmen versehen, wenn sie ausgewählt wird.

   ![screen_shot_2018-03-22at103204](assets/screen_shot_2018-03-22at103204.png)

1. Klicken oder tippen Sie auf das Symbol **Übergeordnetes Element**.

   ![Übergeordnetes Element](do-not-localize/screen_shot_2018-03-22at103204.png)

   Dadurch wird das Absatzsystem mit der aktuellen Komponente ausgewählt.

1. Das Symbol **Konfigurieren** für das Absatzsystem wird in der Aktionsleiste für das übergeordnete Element angezeigt.

   ![Konfigurieren](do-not-localize/screen_shot_2018-03-22at103256.png)

   Wählen Sie dieses Symbol, um das Dialogfeld anzuzeigen.

1. Legen Sie in diesem Dialogfeld fest, welche Komponenten im Komponenten-Browser verfügbar sein sollen, wenn die aktuelle Seite bearbeitet wird.

   ![screen_shot_2018-03-22at103329](assets/screen_shot_2018-03-22at103329.png)

   Das Dialogfeld enthält zwei Registerkarten:

   * Zugelassene Komponenten
   * Einstellungen

   **Zugelassene Komponenten**

   Auf der Registerkarte **Zugelassene Komponenten** legen Sie fest, welche Komponenten für das ParSys verfügbar sein sollen.

   * Die Komponenten werden nach Komponentengruppen gruppiert, die sich erweitern und reduzieren lassen.
   * Es kann eine ganze Gruppe ausgewählt werden, indem das Kontrollkästchen für den Gruppennamen aktiviert wird. Um die Auswahl aller Elemente wieder aufzuheben, deaktivieren Sie das Kontrollkästchen.
   * Ein Minuszeichen zeigt an, dass mindestens eines, aber nicht alle Elemente in einer Gruppe ausgewählt sind.
   * Es steht eine Suchfunktion zur Verfügung, um nach einer Komponente anhand ihres Namens zu filtern.
   * Die rechts neben dem Namen der Komponentengruppe aufgeführten Zahlen geben die Gesamtzahl der ausgewählten Komponenten in diesen Gruppen an, unabhängig vom Filter.

   Die Konfiguration wird pro Seitenkomponente definiert. Wenn untergeordnete Seiten dieselbe Vorlage und/oder Seitenkomponente verwenden (normalerweise ausgerichtet), wird dieselbe Konfiguration auf das zugehörige Absatzsystem angewendet.

   >[!NOTE]
   >
   >Adaptive Formularkomponenten sind für die Verwendung im Container für adaptive Formulare konzipiert, um das Forms-Ökosystem zu nutzen. Entsprechend dürfen diese Komponenten nur im Editor für adaptive Formulare verwendet werden und funktionieren nicht im Seiten-Editor von Sites.

   **Einstellungen**

   Auf der Registerkarte **Einstellungen** können Sie zusätzliche Optionen festlegen und beispielsweise für jede Komponente einen Anker zeichnen oder den Zellenabstand für die einzelnen Container definieren.

1. Wählen Sie **Fertig** aus, um die Konfiguration zu speichern.

## Konfigurieren des Entwurfs einer Komponente {#configuring-the-design-of-a-component}

1. Wechseln Sie in den **Design-Modus**.

   ![screen_shot_2018-03-22at103113-1](assets/screen_shot_2018-03-22at103113-1.png)

1. Tippen oder klicken Sie auf eine Komponente mit einem blauen Rahmen In diesem Beispiel wird eine Hero-Bildkomponente ausgewählt.

   ![screen_shot_2018-03-22at103434](assets/screen_shot_2018-03-22at103434.png)

1. Öffnen Sie das Dialogfeld, indem Sie das Symbol **Konfigurieren** verwenden.

   ![Konfigurationssymbol](do-not-localize/screen_shot_2018-03-22at103256-1.png)

   Im Dialogfeld für den Entwurf können Sie die Komponente entsprechend den verfügbaren Designparametern konfigurieren.

   ![screen_shot_2018-03-22at103530](assets/screen_shot_2018-03-22at103530.png)

   Das Dialogfeld enthält drei Registerkarten:

   * Allgemein
   * Funktionen
   * Stile

   **Eigenschaften**

   Auf der Registerkarte **Eigenschaften** können Sie die wichtigsten Design-Parameter der Komponente konfigurieren. Beispielsweise können Sie für eine Bildkomponente die maximal und minimal zulässige Größe des Bildes festlegen.

   **Funktionen**

   Auf der Registerkarte **Funktionen** können Sie zusätzliche Funktionen der Komponente aktivieren oder deaktivieren. Beispielsweise können Sie für eine Bildkomponente die Ausrichtung des Bildes und die verfügbaren Zuschneideoptionen definieren und festlegen, ob ein Bild hochgeladen werden kann.

   **Stile**

   Auf der Registerkarte **Stile** können Sie die CSS-Klassen und -Stile definieren, die mit der Komponente verwendet werden sollen.

   ![screen_shot_2018-03-22at103741](assets/screen_shot_2018-03-22at103741.png)

   Mit der Schaltfläche **Hinzufügen** können Sie zusätzliche Einträge zu einer Dialogfeldliste mit mehreren Einträgen hinzufügen.

   ![Zusätzlichen Eintrag hinzufügen](assets/chlimage_1-94.png)

   Verwenden Sie das Symbol **Löschen**, um einen Eintrag aus einer Dialogfeldliste mit mehreren Einträgen zu entfernen.

   ![Löschen](do-not-localize/screen_shot_2018-03-22at103809.png)

   Verwenden Sie das Symbol **Verschieben**, um in einer Dialogfeldliste mit mehreren Einträgen die Reihenfolge der Einträge zu ändern.

   ![Verschieben](do-not-localize/screen_shot_2018-03-22at103816.png)

1. Klicken oder tippen Sie auf das Symbol **Fertig**, um Ihre Änderungen zu speichern und das Dialogfeld zu schließen.
