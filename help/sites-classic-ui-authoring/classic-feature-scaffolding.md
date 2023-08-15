---
title: Strukturvorlage
description: Manchmal müssen Sie möglicherweise eine große Gruppe von Seiten erstellen, die zwar eine gemeinsame Struktur aufweisen, aber unterschiedliche Inhalte haben. Mit Strukturvorlage können Sie ein Formular (eine Grundlage) mit Feldern erstellen, die die gewünschte Struktur für Ihre Seiten widerspiegeln. Mithilfe dieses Formulars können Sie dann einfach Seiten erstellen, die auf dieser Struktur basieren.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: 58e61302-cfb4-4a3d-98d4-3c92baa2ad42
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '1431'
ht-degree: 59%

---

# Strukturvorlage{#scaffolding}

Manchmal müssen Sie möglicherweise eine große Gruppe von Seiten erstellen, die zwar eine gemeinsame Struktur aufweisen, aber unterschiedliche Inhalte haben. Über die Standard-Benutzeroberfläche von Adobe Experience Manager (AEM) müssten Sie jede Seite erstellen, die entsprechenden Komponenten auf die Seite ziehen und jede einzelne davon einzeln ausfüllen.

Mit Strukturvorlage können Sie ein Formular (eine Grundlage) mit Feldern erstellen, die die gewünschte Struktur für Ihre Seiten widerspiegeln. Mithilfe dieses Formulars können Sie dann einfach Seiten erstellen, die auf dieser Struktur basieren.

>[!NOTE]
>
>Bei Strukturvorlagen (auf der klassischen Benutzeroberfläche) [wird die MSM-Vererbung berücksichtigt](#scaffolding-with-msm-inheritance).

## Funktionsweise von Strukturvorlagen {#how-scaffolding-works}

Strukturvorlagen sind über die **Tools**-Konsole des SiteAdmin-Bereichs verfügbar.

* Öffnen Sie die **Instrumente** und klicken Sie auf **Strukturvorlage für Standardseite**.
* Klicken Sie unter diesem Link auf **Geometrixx**.
* under **Geometrixx**, finden Sie *Strukturseite* aufgerufen **Nachrichten**. Doppelklicken Sie, um diese Seite zu öffnen.

![howscaffolds_work](assets/howscaffolds_work.png)

Die Strukturvorlage besteht aus einem Formular mit einem Feld für jedes Inhaltselement, mit dem die zu erstellende Seite gefüllt werden soll. Außerdem wird das Aussehen der Seite durch vier wichtige Parameter bestimmt, die in den **Seiteneigenschaften** der Strukturvorlagenseite festgelegt werden.

![pageprops](assets/pageprops.png)

Die Eigenschaften der Strukturvorlagen-Seite sind:

* **Titeltext**: Dies ist der Name dieser Strukturvorlagen-Seite selbst. In diesem Beispiel heißt es &quot;News&quot;.
* **Beschreibung**: Dies wird unter dem Titel auf der Strukturvorlagen-Seite angezeigt.
* **Zielvorlage**: Dies ist die Vorlage, die diese Grundlage beim Erstellen einer Seite verwenden wird. In diesem Beispiel handelt es sich um eine *Geometrixx-Inhaltsseite* Vorlage.
* **Zielpfad**: Dies ist der Pfad der übergeordneten Seite, unter der diese Grundlage Seiten erstellt. In diesem Beispiel lautet der Pfad */content/geometrixx/en/news*.

Der Textkörper der Strukturvorlage ist das Formular. Wenn ein Benutzer eine Seite mithilfe der Strukturvorlage erstellen möchte, füllt er das Formular aus und klickt unten auf *Erstellen*. Im Beispiel **Nachrichten** oben weist das Formular die folgenden Felder auf:

* **Titel**: Dies ist der Name der zu erstellenden Seite. Dieses Feld ist immer auf jeder Struktur vorhanden.
* **Text**: Dieses Feld korrespondiert zu einer Textkomponente auf der resultierenden Seite.
* **Bild**: Dieses Feld stellt eine Bildkomponente für die zu erstellende Seite dar.
* **Bild/Erweitert**: **Titel**: Der Titel des Bildes.
* **Bild/Erweitert**: **Alternativtext**: Der Alternativtext für das Bild.
* **Bild/Erweitert**: **Beschreibung**: Die Beschreibung des Bildes.
* **Bild/Erweitert**: **Größe**: Die Größe des Bildes.
* **Tags/Keywords**: Metadaten, die dieser Seite zugewiesen werden sollen. Dieses Feld ist immer auf jeder Struktur vorhanden.

### Erstellen einer Strukturvorlage {#creating-a-scaffold}

Um eine neue Grundlage zu erstellen, navigieren Sie zum **Instrumente** Console, dann **Strukturvorlage für Standardseite** und erstellen Sie eine Seite. Ein einseitiger Vorlagentyp ist verfügbar. *Strukturvorlage.*

Navigieren Sie zu **Seiteneigenschaften** und legen Sie die *Titeltext*, *Beschreibung*, *Zielvorlage*, und *Zielpfad*, wie oben beschrieben.

Als nächstes müssen Sie die Struktur der Seite festlegen, die mithilfe der Strukturvorlage erstellt wird. Gehen Sie dazu in **[Designmodus](/help/sites-authoring/page-authoring.md#sidekick)** auf der Strukturvorlagenseite. Es wird ein Link angezeigt, mit dessen Hilfe Sie die Strukturvorlage im **Dialog-Editor** bearbeiten können.

![cq5_dialog_editor](assets/cq5_dialog_editor.png)

Im Dialog-Editor legen Sie die Eigenschaften fest, die bei jeder Erstellung einer neuen Seite mithilfe dieser Grundlage erstellt werden.

Die Dialogdefinition für eine Strukturvorlage funktioniert ähnlich wie bei einer Komponente (siehe [Komponenten](/help/sites-developing/components.md)). Es gibt jedoch einige wichtige Unterschiede:

* Komponenten-Dialogfelddefinitionen werden als normale Dialogfelder gerendert (wie z. B. im mittleren Bereich des Dialogfeldeditors angezeigt), während Dialogfelddefinitionen von Strukturvorlagen zwar als normale Dialogfelder im Dialogfeldeditor angezeigt werden, aber auf der Strukturvorlagen-Seite als Strukturvorlagenformular wiedergegeben werden (wie in der **Nachrichten**-Strukturvorlage oben).
* Komponentendialogfelder enthalten nur Felder für die Werte, die zum Definieren des Inhalts einer einzelnen bestimmten Komponente erforderlich sind. Ein Dialogfeld einer Strukturvorlage muss Felder für jede Eigenschaft in jedem Absatz der zu erstellenden Seite enthalten.
* Bei Dialogfeldern für Komponenten ist die Komponente, die für das Rendern des angegebenen Inhalts verwendet wird, implizit, und daher wird die Eigenschaft `sling:resourceType` eines Absatzes automatisch bei dessen Erstellung eingefügt. Bei einer Strukturvorlage müssen alle Informationen, die sowohl den Inhalt als auch die zugewiesene Komponente für einen bestimmten Absatz definieren, vom Dialogfeld selbst bereitgestellt werden. In Dialogfeldern von Strukturvorlagen müssen diese Informationen bereitgestellt werden, indem Sie *ausgeblendete* Felder verwenden, um diese Informationen bei der Seitenerstellung zu übermitteln.

Ein Blick auf die Beispiel-Strukturvorlage **Nachrichten** im Dialog-Editor hilft zu erklären, wie dies funktioniert. Wechseln Sie in den Designmodus auf der Strukturvorlagen-Seite und klicken Sie auf den Link des Dialogfeldeditors.

Klicken Sie jetzt auf das Dialogfeld **Dialogfeld > Registerkartenfeld > Text > Text**, wie folgt:

![textedit](assets/textedit.png)

Die Eigenschaftsliste für dieses Feld wird rechts im Dialogfeldeditor wie folgt angezeigt:

![list_of_properties](assets/list_of_properties.png)

Beachten Sie die Eigenschaft „Name“ für dieses Feld. Sie hat den Wert

`./jcr:content/par/text/text`

Dies ist der Name der Eigenschaft, in die der Inhalt dieses Feldes geschrieben wird, wenn die Grundlage für die Erstellung einer neuen Seite verwendet wird. Die Eigenschaft wird als relativer Pfad zu dem Knoten angegeben, der die zu erstellende Seite repräsentiert. Sie gibt den Eigenschaftstext unter dem Knotentext an, der sich unter dem par-Knoten befindet, der wiederum ein untergeordnetes Element des Knotens jcr:content unter dem Seitenknoten ist.

Dies definiert den Speicherort des Inhaltsspeichers für den Text, der in dieses Feld eingegeben wird. Für diesen Inhalt müssen jedoch zwei weitere Eigenschaften angegeben werden:

* Die Tatsache, dass die hier gespeicherte Zeichenfolge als *Rich-Text* interpretiert werden muss, und
* welche Komponente zum Rendern dieses Inhalts auf der resultierenden Seite verwendet werden soll.

In einem normalen Komponentendialogfeld müssen Sie diese Informationen nicht angeben, da dies dadurch impliziert wird, dass das Dialogfeld bereits an eine bestimmte Komponente gebunden ist.

Um diese beiden Informationen anzugeben, verwenden Sie ausgeblendete Felder. Klicken Sie auf das erste ausgeblendete Feld **Dialogfeld > Registerkartenfeld > Text > Ausgeblendet**, wie folgt:

![hidden](assets/hidden.png)

Dieses ausgeblendete Feld weist folgende Eigenschaften auf:

![hidden_list_props](assets/hidden_list_props.png)

Die Namenseigenschaft dieses ausgeblendeten Felds lautet:

`./jcr:content/par/text/textIsRich`

Hierbei handelt es sich um eine boolesche Eigenschaft für die Auswertung der Textzeichenfolge, die unter `./jcr:content/par/text/text` gespeichert ist.

Da wir wissen, dass der Text als Rich-Text interpretiert werden soll, legen wir die `value` Eigenschaft dieses Felds als `true`.

>[!CAUTION]
>
>Der Dialog-Editor ermöglicht die Änderung der Werte *bestehender* Eigenschaften in der Dialogdefinition. Um eine neue Eigenschaft hinzuzufügen, muss die Benutzerin oder der Benutzer [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) verwenden. Wenn beispielsweise ein neues ausgeblendetes Feld zu einer Dialogfelddefinition mit dem Dialogfeldeditor hinzugefügt wird, verfügt es über keine *value* -Eigenschaft (d. h. eine Eigenschaft mit dem Namen &quot;value&quot;). Wenn für das betreffende ausgeblendete Feld eine Standardwerteigenschaft festgelegt werden muss, muss diese Eigenschaft manuell mit einem der CRX-Tools hinzugefügt werden. Der Wert kann nicht mit dem Dialogfeldeditor selbst hinzugefügt werden. Sobald die Eigenschaft jedoch vorhanden ist, kann ihr Wert mit dem Dialogfeldeditor bearbeitet werden.

Das zweite ausgeblendete Feld kann durch Klicken wie folgt angezeigt werden:

![hidden2](assets/hidden2.png)

Dieses ausgeblendete Feld weist folgende Eigenschaften auf:

![hidden_list_props2](assets/hidden_list_props2.png)

Die Namenseigenschaft dieses ausgeblendeten Felds lautet:

`./jcr:content/par/text/sling:resourceType`

Der für diese Eigenschaft angegebene feste Wert lautet

`foundation/components/textimage`

 Dadurch wird festgelegt, dass die für das Rendern des Textinhalts verwendete Komponente vom Typ *Textbild* ist. Zusammen mit dem booleschen Wert `isRichText` in dem anderen ausgeblendeten Feld kann die Komponente die eigentliche unter `./jcr:content/par/text/text` gespeicherte Textzeichenfolgen wie gewünscht rendern.

### Strukturvorlagen mit MSM-Vererbung {#scaffolding-with-msm-inheritance}

Auf der klassischen Benutzeroberfläche sind Strukturvorlagen vollständig in die MSM-Vererbung integriert (sofern verfügbar).

Wenn Sie eine Seite im **Strukturvorlagenmodus** öffnen (über das Symbol im unteren Sidekick-Bereich), werden alle Komponenten, für die Vererbung gilt, folgendermaßen gekennzeichnet:

* ein Sperrsymbol (für die meisten Komponenten, z. B. Text und Titel)
* eine Maske mit dem Text **Klicken Sie, um die Vererbung abzubrechen** (für Bildkomponenten)

Diese zeigen, dass die Komponente erst bearbeitet werden kann, wenn die Vererbung abgebrochen wurde.

![chlimage_1](assets/chlimage_1.jpeg)

>[!NOTE]
>
>Dies ist vergleichbar mit [geerbten Komponenten beim Bearbeiten des Seiteninhalts](/help/sites-authoring/editing-content.md#inheritedcomponentsclassicui).

Durch Klicken auf das Sperrsymbol oder das Bildsymbol können Sie die Vererbung unterbrechen:

* das Symbol wird in ein geöffnetes Vorhängeschloss geändert.
* Nach erfolgter Entsperrung können Sie den Inhalt bearbeiten.

![chlimage_1-1](assets/chlimage_1-1.jpeg)

Nach dem Entsperren können Sie die Vererbung wiederherstellen, indem Sie auf das Entsperrte Vorhängeschloss-Symbol klicken. Dadurch gehen alle von Ihnen vorgenommenen Änderungen verloren.

>[!NOTE]
>
>Wenn die Vererbung auf Seitenebene abgebrochen wird (über die Registerkarte Live Copy der Seiteneigenschaften), sind alle Komponenten in **Strukturvorlage** -Modus (sie werden im entsperrten Status angezeigt).
