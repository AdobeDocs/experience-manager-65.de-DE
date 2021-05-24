---
title: Strukturvorlage
seo-title: Strukturvorlage
description: Oftmals muss eine große Zahl von Seiten erstellt werden, die unterschiedliche Inhalte, aber eine einheitliche Struktur aufweisen sollen. Eine Strukturvorlage dient zur Erstellung eines Formulars (einer Struktur), dessen Felder die gewünschte Seitenstruktur bilden. Anhand dieses Formulars können Sie ganz einfach auf dieser Struktur basierende Seiten erstellen.
seo-description: Oftmals muss eine große Zahl von Seiten erstellt werden, die unterschiedliche Inhalte, aber eine einheitliche Struktur aufweisen sollen. Eine Strukturvorlage dient zur Erstellung eines Formulars (einer Struktur), dessen Felder die gewünschte Seitenstruktur bilden. Anhand dieses Formulars können Sie ganz einfach auf dieser Struktur basierende Seiten erstellen.
uuid: 5904abc0-b256-4da4-a7d7-3c17ea299648
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: a63e5732-b1a3-4639-9838-652af401e788
docset: aem65
exl-id: 58e61302-cfb4-4a3d-98d4-3c92baa2ad42
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1502'
ht-degree: 82%

---

# Strukturvorlage{#scaffolding}

Oftmals muss eine große Zahl von Seiten erstellt werden, die unterschiedliche Inhalte, aber eine einheitliche Struktur aufweisen sollen. In der Standard-Benutzeroberfläche von AEM müssten Sie jede Seite neu erstellen, die entsprechenden Komponenten auf die Seiten ziehen und sie jedes Mal einzeln mit Inhalten füllen.

Eine Strukturvorlage dient zur Erstellung eines Formulars (einer Struktur), dessen Felder die gewünschte Seitenstruktur bilden. Anhand dieses Formulars können Sie ganz einfach auf dieser Struktur basierende Seiten erstellen.

>[!NOTE]
>
>Bei Strukturvorlagen (auf der klassischen Benutzeroberfläche) [wird die MSM-Vererbung berücksichtigt](#scaffolding-with-msm-inheritance).

## Funktionsweise von Strukturvorlagen {#how-scaffolding-works}

Strukturvorlagen sind über die **Tools-Konsole** des SiteAdmin-Bereichs verfügbar.

* Öffnen Sie die **Tools-Konsole** und klicken Sie auf **Standardseiten-Strukturvorlage**.
* Klicken Sie darunter auf **geometrixx**.
* Unter **geometrixx** sollte eine *Grundlagenseite* mit dem Namen **News** verfügbar sein. Doppelklicken Sie auf die Seite, um sie zu öffnen.

![howscaffolds_work](assets/howscaffolds_work.png)

Die Grundlage besteht aus einem Formular mit einem Feld für jedes Inhaltselement, aus dem die zu erstellende Seite besteht, und vier wichtigen Parametern, auf die über die Seite **Seiteneigenschaften** der Strukturseite zugegriffen wird.

![pageprops](assets/pageprops.png)

Es handelt sich dabei um die folgenden Eigenschaften:

* **Titeltext**: Dies ist der Name der Strukturvorlagen-Seite selbst. In diesem Beispiel lautet der Name „Nachrichten“.
* **Beschreibung**: Dieser Text wird unterhalb des Titels der Stukturvorlagen-Seite angezeigt.
* **Target-Vorlage**: Diese Vorlage wird von der Grundlage für die Erstellung einer neuen Seite verwendet. In diesem Beispiel ist das die Vorlage *Geometrixx-Inhaltsseite*.
* **Zielpfad**: Dies ist der Pfad der übergeordneten Seite, unterhalb derer die Grundlage neue Seiten anlegt. In diesem Beispiel lautet der Pfad */content/geometrixx/en/news*.

Der Textkörper der Grundlage ist das Formular. Wenn ein Benutzer eine Seite mithilfe der Grundlage erstellen möchte, füllt er das Formular aus und klickt unten auf *Erstellen.* In der Beispielgrundlage **Nachrichten** weist das Formular die folgenden Felder auf:

* **Titel**: Dies ist der Name der zu erstellenden Seite. Dieses Feld ist für jede Grundlage vorhanden.
* **Text**: Dieses Feld stellt eine Text-Komponente für die zu erstellende Seite dar.
* **Bild**: Dieses Feld entspricht einer Bildkomponente auf der resultierenden Seite.
* **Bild/erweitert**: **Titel**: Der Titel des Bildes.
* **Bild/erweitert**: **ALT-Text**: Der Alt-Text des Bildes.
* **Bild/Erweitert**:  **Beschreibung**: Die Beschreibung des Bildes.
* **Bild/erweitert**: **Größe**: Die Größe des Bildes.
* **Tags/Keywords**: Metadaten, die der jeweiligen Seite zugeordnet werden sollen. Dieses Feld ist für jede Grundlage vorhanden.

### Erstellen von Grundlagen  {#creating-a-scaffold}

Um eine neue Grundlage zu erstellen, wechseln Sie zur Konsole **Tools**, dann zu **Standardseiten-Strukturvorlage** und erstellen Sie eine neue Seite. Ein einseitiger Vorlagentyp ist verfügbar, die *Strukturvorlagen-Vorlage.*

Wechseln Sie zu **Seiteneigenschaften** der neuen Seite und legen Sie *Titeltext*, *Beschreibung*, *Zielvorlage* und *Zielpfad* wie oben beschrieben fest.

Als nächstes müssen Sie die Struktur der Seite festlegen, die mithilfe der Grundlage erstellt wird. Gehen Sie dazu in den **[Designmodus](/help/sites-authoring/page-authoring.md#sidekick)** auf der Strukturvorlagenseite. Es wird ein Link angezeigt, mit dessen Hilfe Sie die Grundlage im **Dialog-Editor** bearbeiten können.

![cq5_dialog_editor](assets/cq5_dialog_editor.png)

Im Dialog-Editor legen Sie die Eigenschaften fest, die für jede Seite gelten, die mithilfe der Grundlage erstellt wird.

Die Dialogdefinition einer Strukturvorlage wird ähnlich wie bei einer Komponente durchgeführt (siehe [Komponenten](/help/sites-developing/components.md)). Es gibt allerdings einige wichtige Unterschiede:

* Dialogdefinition von Komponenten werden als normale Dialogfelder angezeigt (wie beispielsweise im mittleren Fenster des Dialog-Editors gezeigt), während Dialogdefinitionen von Grundlagen zwar als normale Dialogfelder im Dialog-Editor erscheinen, auf der Grundlagenseite aber als Grundlagenformular angezeigt werden (wie in der Grundlage **Nachrichten** oben).
* In Dialogfeldern für Komponenten sind nur solche Werte enthalten, die für die Definition des Inhalts einer bestimmten einzelnen Komponente erforderlich sind. Im Dialogfeld für eine Grundlage sind Felder für alle Eigenschaften in allen Absätzen der zu erstellenden Seite enthalten.
* Bei Dialogfeldern für Komponenten ist die Komponente, die für das Rendern des angegebenen Inhalts verwendet wird, implizit, und daher wird die Eigenschaft `sling:resourceType` eines Absatzes automatisch bei dessen Erstellung eingefügt. Bei der Arbeit mit Grundlagen müssen alle Informationen bezüglich des Inhalts und der zugewiesenen Komponente für einen bestimmten Absatz explizit im Dialogfeld selbst angegeben werden. In müssen diese Informationen durch Felder des Typs *Ausgeblendet* angegeben werden, um bei der Erstellung einer Seite wirksam zu werden.

Ein Blick auf das für **Nachrichten** im Dialog-Editor hilft bei der Erläuterung dieser Vorgehensweise. Wechseln Sie auf der Grundlagenseite in den Designmodus und klicken Sie auf den Link für den Dialog-Editor.

Klicken Sie nun auf das Dialogfeld **Dialogfeld > Registerkartenfeld > Text > Text**, wie in diesem Beispiel:

![textedit](assets/textedit.png)

Daraufhin wird die Eigenschaftenliste für dieses Feld auf der rechten Seite des Dialog-Editors wie folgt angezeigt:

![list_of_properties](assets/list_of_properties.png)

Beachten Sie die Eigenschaft „Name“ für dieses Feld. Sie weist folgenden Wert auf:

`./jcr:content/par/text/text`

Dies ist der Name der Eigenschaft, in die der Inhalt dieses Feldes geschrieben wird, wenn die Grundlage für die Erstellung einer neuen Seite verwendet wird. Diese Eigenschaft wird als relativer Pfad in Bezug auf den Knoten der die zu erstellende Seite darstellt, angegeben. Sie gibt die Eigenschaft „text“ unterhalb des Knotens „text“ an, der unterhalb des Knotens „par“ liegt, der wiederum ein untergeordnetes Element des Knotens „jcr:content“ unterhalb des Seitenknotens darstellt.

Dadurch wird der Speicherort für den Inhalt festgelegt, der in dieses Feld eingegeben wird. Allerdings sind noch zwei weitere Eigenschaften für die Charakterisierung des Inhalts erforderlich:

* Zum einen muss angegeben werden, dass die hier gespeicherte Zeichenfolge als *Rich-Text* zu interpretieren ist,
* zum anderen muss die Komponente festgelegt werden, die für das Rendern des Inhalts auf der Seite verwendet wird.

Beachten Sie, dass Sie diese Informationen in einem normalen Komponentendialogfeld nicht angeben müssen, weil sie durch die Tatsache, dass das Dialogfeld an eine bestimmte Komponente gebunden ist, bereits vorgegeben sind.

Zur Angabe dieser beiden Informationen verwenden Sie ausgeblendete Felder. Klicken Sie auf das erste ausgeblendete Feld **Dialogfeld > Registerkartenfeld > Text > Ausgeblendet** wie folgt:

![hidden](assets/hidden.png)

Dieses ausgeblendete Feld weist folgende Eigenschaften auf:

![hidden_list_props](assets/hidden_list_props.png)

Die Namenseigenschaft dieses ausgeblendeten Felds lautet:

`./jcr:content/par/text/textIsRich`

Dies ist eine boolesche Eigenschaft, mit der die unter `./jcr:content/par/text/text` gespeicherte Textzeichenfolge interpretiert wird.

Da wir wissen, dass der Text als Rich-Text ausgewertet werden soll, setzen wir die Eigenschaft `value` dieses Felds auf `true`.

>[!CAUTION]
>
>Der Dialog-Editor ermöglicht es dem Benutzer, die Werte von *vorhandenen* Eigenschaften in der Dialogfelddefinition zu ändern. Um eine neue Eigenschaft hinzuzufügen, muss der Benutzer [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) verwenden. Wird beispielsweise einer Dialogdefinition mit dem Dialog-Editor ein neues ausgeblendetes Feld hinzugefügt, weist dieses keine Eigenschaft *value* auf (d. h. keine Eigenschaft mit diesem Namen). Wenn für das betreffende ausgeblendete Feld standardmäßig eine Eigenschaft *value* festgelegt werden muss, kann dies nur manuell mithilfe eines der CRX-Werkzeuge erfolgen. Der Wert kann nicht im Dialog-Editor selbst hinzugefügt werden. Sobald allerdings die Eigenschaft vorhanden ist, kann der Wert im Dialog-Editor geändert werden.

Das zweite ausgeblendete Feld kann angezeigt werden, indem Sie wie folgt darauf klicken:

![hidden2](assets/hidden2.png)

Dieses ausgeblendete Feld weist folgende Eigenschaften auf:

![hidden_list_props2](assets/hidden_list_props2.png)

Die Namenseigenschaft dieses ausgeblendeten Felds lautet:

`./jcr:content/par/text/sling:resourceType`

Der feste Wert für diese Eigenschaft lautet:

`foundation/components/textimage`

 Dadurch wird festgelegt, dass die für das Rendern des Textinhalts verwendete Komponente vom Typ *Textbild* ist. Mit dem booleschen Wert `isRichText`, der im anderen ausgeblendeten Feld angegeben ist, kann die Komponente die unter `./jcr:content/par/text/text` gespeicherte tatsächliche Textzeichenfolge auf die gewünschte Weise rendern.

### Scaffolding with MSM Inheritance {#scaffolding-with-msm-inheritance}

Auf der klassischen Benutzeroberfläche sind Strukturvorlagen vollständig in die MSM-Vererbung integriert (sofern verfügbar).

Wenn Sie eine Seite im **Strukturvorlagenmodus** öffnen (über das Symbol im unteren Sidekick-Bereich), werden alle Komponenten, für die Vererbung gilt, folgendermaßen gekennzeichnet:

* ein Vorhängeschloss-Symbol (für die meisten Komponenten, z. B. Text und Titel)
* eine Maske mit dem Text **Klicken Sie, um die Vererbung abzubrechen** (für Bildkomponenten)

Diese zeigen an, dass die Komponente erst bearbeitet werden kann, wenn die Vererbung abgebrochen wird.

![chlimage_1](assets/chlimage_1.jpeg)

>[!NOTE]
>
>Dies ist mit [vererbten Komponenten bei der Bearbeitung von Seiteninhalten vergleichbar](/help/sites-authoring/editing-content.md#inheritedcomponentsclassicui).

Durch Klicken auf das Vorhängeschloss-Symbol oder auf das Bildsymbol können Sie die Vererbung aufheben:

* Das Symbol ändert sich in ein geöffnetes Vorhängeschloss.
* Nach erfolgter Entsperrung können Sie den Inhalt bearbeiten.

![chlimage_1-1](assets/chlimage_1-1.jpeg)

Nach dem Entsperren können Sie die Vererbung wiederherstellen, indem Sie auf das Symbol des geöffneten Vorhängeschlosses klicken. Dabei gehen jedoch alle vorgenommenen Änderungen verloren.

>[!NOTE]
>
>Wenn die Vererbung auf Seitenebene abgebrochen wird (über die Registerkarte Live Copy der Seiteneigenschaften), sind alle Komponenten im Modus **Strukturvorlage** bearbeitbar (sie werden im entsperrten Status angezeigt).
