---
title: Rich-Text-Editor
description: Der Rich-Text-Editor ist ein grundlegender Baustein für die Eingabe von Textinhalten in AEM.
uuid: 4bcce45a-e14f-41b7-8c6f-89d1e1bb595c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
discoiquuid: ccc0e434-8847-4e12-8a18-84b55fb2964b
docset: aem65
exl-id: 5623dcf4-bda9-4dee-ace3-5a1f6057e96c
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1835'
ht-degree: 90%

---

# Rich-Text-Editor {#rich-text-editor}

Der Rich-Text-Editor ist ein grundlegender Baustein für die Eingabe von Textinhalten in AEM. Sie können verschiedene Komponenten erstellen, einschließlich:

* Text
* Textbild
* Tabelle

## Rich-Text-Editor {#rich-text-editor-1}

Das Dialogfeld der WYSIWYG-Bearbeitung bietet einen großen Funktionsumfang:

![cq55_rte_basicchars](assets/cq55_rte_basicchars.png)

>[!NOTE]
>
>Welche Funktionen verfügbar sind, richtet sich nach dem jeweiligen Projekt. Ihre spezielle Installation kann also Abweichungen aufweisen.

## Bearbeiten im Kontext {#in-place-editing}

Zusätzlich zu der Bearbeitung in Dialogfeldern durch den Rich-Text-Editor bietet AEM noch die Möglichkeit einer Bearbeitung im Kontext, bei der Sie den Text so bearbeiten, wie er im Layout der Seite erscheint.

Klicken Sie zweimal auf einen Absatz (langsamer Doppelklick), um in den Bearbeitungsmodus für den Kontext zu wechseln (der Komponentenrahmen ist jetzt orange).

Sie können nun den Text direkt auf der Seite bearbeiten, anstatt ein Dialogfenster aufrufen zu müssen. Nehmen Sie einfach Ihre Änderungen vor, und sie werden automatisch gespeichert.

![cq55_rte_inlineediting](assets/cq55_rte_inlineediting.png)

>[!NOTE]
>
>Wenn Sie den Content Finder geöffnet haben, wird oben auf der Registerkarte eine Symbolleiste mit den RTE-Formatierungsoptionen angezeigt (wie oben).
>
>Wenn die Inhaltssuche nicht geöffnet ist, wird die Symbolleiste nicht angezeigt.

Derzeit ist der Kontext-Bearbeitungsmodus für Seitenelemente aktiviert, die von den **Text**- und **Titel**-Komponenten generiert werden.

>[!NOTE]
>
>Die [!UICONTROL Titel]-Komponente wurde konzipiert, um kurzen Text ohne Zeilenumbrüche zu enthalten. Wenn Sie einen Titel im Kontext-Bearbeitungsmodus bearbeiten, wird durch die Eingabe eines Zeilenumbruchs ein neuer **Text** -Komponente unterhalb des Titels.

## Funktionen des Rich-Text-Editors {#features-of-the-rich-text-editor}

Der Rich-Text-Editor bietet verschiedene Funktionen, die [von der Konfiguration](/help/sites-administering/rich-text-editor.md) der einzelnen Komponente abhängen. Die Funktionen sind sowohl für die Touch-optimierte als auch für die klassische Benutzeroberfläche verfügbar.

### Grundlegende Zeichenformate {#basic-character-formats}

![Symbolleiste Zeichenformat](do-not-localize/cq55_rte_basicchars.png)

Hier können Sie die Formatierung auf die von Ihnen ausgewählten Zeichen (hervorgehoben) anwenden; einige Optionen verfügen auch über Tastaturkürzel:

* Fett (Strg+B)
* Kursiv (Strg+I)
* Unterstreichen (Strg+U)
* Tiefgestellt
* Hochgestellt

![cq55_rte_basicchars_use](assets/cq55_rte_basicchars_use.png)

Alle fungieren als Umschalter, sodass bei einer erneuten Auswahl das Format entfernt wird.

### Vordefinierte Stile und Formate {#predefined-styles-and-formats}

![cq55_rte_stylesparagraph](assets/cq55_rte_stylesparagraph.png)

Ihre Installation kann vordefinierte Stile und Formate enthalten. Diese sind mit der Variablen **[!UICONTROL Stil]** und **[!UICONTROL Format]** Dropdown-Listen und können auf den ausgewählten Text angewendet werden.

Ein Stil kann auf eine bestimmte Zeichenfolge angewendet werden (ein Stil ist CSS-basiert):

![cq55_rte_styles_use](assets/cq55_rte_styles_use.png)

Ein Format hingegen wird auf einen gesamten Textabsatz angewendet (Formate sind HTML-basiert):

![cq55_rte_paragraph_use](assets/cq55_rte_paragraph_use.png)

Ein bestimmtes Format kann nur geändert werden (die Standardeinstellung ist **[!UICONTROL Absatz]**).

Ein Stil kann entfernt werden. Platzieren Sie den Cursor in dem Text, auf den der Stil angewendet wurde, und klicken Sie auf das Symbol „Entfernen“:

>[!CAUTION]
>
>Wählen Sie keinen Text erneut aus, auf den der Stil angewendet wurde, da dadurch das Symbol deaktiviert wird.

### Ausschneiden, Kopieren, Einfügen {#cut-copy-paste}

![Symbolleiste Ausschneiden, Kopieren, Einfügen](do-not-localize/cq55_rte_cutcopypaste.png)

Es sind die Standardfunktionen **[!UICONTROL Ausschneiden]** und **[!UICONTROL Kopieren]** verfügbar. Verschiedene Variationen von **[!UICONTROL Einfügen]** sind verfügbar, die sich für unterschiedliche Formate eignen.

* Ausschneiden (Strg+X)
* Kopieren (Strg-C)
* Einfügen
Dies ist das Standard-Einfügeverfahren (Strg+V) für die Komponente. Für Standardinstallationen ist [!UICONTROL Aus Word einfügen] festgelegt.

* Als Text einfügen: Hierbei werden alle Stile und Formatierungen entfernt und der Inhalt wird als reiner Text eingefügt.

* Aus Word einfügen: Hierbei wird der Inhalt im HTML-Format (mit einigen erforderlichen Umformatierungen) eingefügt.

### Rückgängig, Wiederholen {#undo-redo}

![Symbolleiste „Rückgängig machen, Wiederholen“](do-not-localize/cq55_rte_undoredo.png)

AEM speichert die jeweils letzten 50 Aktionen in der aktuellen Komponente in chronologischer Reihenfolge. Diese Aktionen können bei Bedarf rückgängig gemacht (und dann wiederholt) werden, aber nur in der Reihenfolge ihrer Durchführung.

>[!CAUTION]
>
>Der Bearbeitungsverlauf wird nur für die aktuelle Bearbeitungssitzung beibehalten. Er wird jedes Mal neu gestartet, wenn Sie die Komponente zur Bearbeitung öffnen.

>[!NOTE]
>
>Standardmäßig werden fünfzig Aktionen berücksichtigt. Dies kann für Ihre Installation anders sein.

### Ausrichtung {#alignment}

![Ausrichtungs-Symbolleiste](do-not-localize/cq55_rte_alignment.png)

Ihr Text kann entweder links, zentriert oder rechts ausgerichtet sein.

![cq55_rte_align_use](assets/cq55_rte_alignment_use.png)

### Einzug {#indentation}

![Einzugssymbolleiste](do-not-localize/cq55_rte_indent.png)

Der Einzug eines Absatzes kann erhöht oder verringert werden. Der ausgewählte Absatz wird eingerückt, und jeder neu eingegebene Text behält den aktuellen Einzug bei.

![cq55_rte_indent_use](assets/cq55_rte_indent_use.png)

### Listen {#lists}

![Listensymbolleiste](do-not-localize/cq55_rte_lists.png)

In Ihrem Text können Sie sowohl Aufzählungslisten als auch nummerierte Listen erstellen. Wählen Sie entweder den Listentyp aus und beginnen Sie mit der Eingabe oder markieren Sie den zu konvertierenden Text. In beiden Fällen startet ein Zeilen-Feed ein neues Listenelement.

Verschachtelte Listen können durch Einrücken eines oder mehrerer Listenelemente erreicht werden.

Der Stil der Liste kann einfach dadurch geändert werden, dass Sie den Cursor innerhalb der Liste platzieren und einen anderen Stil wählen. Eine Unterliste kann auch einen anderen Stil haben als die übergeordnete Liste. Dies kann angewendet werden, sobald die Unterliste (durch den Einzug) erstellt wurde.

![cq55_rte_lists_use](assets/cq55_rte_lists_use.png)

### Links {#links}

![Links-Symbolleiste](do-not-localize/cq55_rte_links.png)

Ein Link zu einer URL (entweder innerhalb der Website oder zu einer externen Adresse) wird dadurch erstellt, dass Sie den gewünschten Text markieren und dann auf das Hyperlink-Symbol klicken:

![Hyperlink-Symbol](do-not-localize/chlimage_1-9.png)

In einem Dialogfeld können Sie die Ziel-URL angeben sowie festlegen, ob sie in einem neuen Fenster geöffnet werden soll.

![cq55_rte_link_use](assets/cq55_rte_link_use.png)

Sie haben folgende Möglichkeiten:

* Direkte Eingabe eines URI
* Verwendung der Sitemap zur Auswahl einer Seite innerhalb der Website
* Geben Sie den URI ein und hängen Sie dann den Ziel-Anker an, z. B. `www.TargetUri.org#AnchorName`
* Eingabe eines reinen Ankers (zum Verweis auf die aktuelle Seite), z. B. `#anchor`
* Suche nach einer Seite im Content Finder, deren Seitensymbol dann per Drag-and-Drop in das Dialogfeld „Hyperlink“ gezogen wird

>[!NOTE]
>
>Der URI kann jedes der Protokolle vorangestellt werden, die für die jeweilige Installation konfiguriert sind. Bei einer Standardinstallation sind dies `https://`, `ftp://` und `mailto:`. Protokolle, die nicht für Ihre Installation konfiguriert sind, werden zurückgewiesen und als ungültig markiert.

Um den Hyperlink zu entfernen, klicken Sie auf eine beliebige Stelle innerhalb des Link-Texts und klicken Sie auf das Symbol [!UICONTROL Verknüpfung aufheben]:

![Symbol „Verknüpfung aufheben“](do-not-localize/chlimage_1-10.png)

### Anker {#anchors}

![Anker-Symbolleiste](do-not-localize/cq55_rte_anchor.png)

Ein Anker kann an einer beliebigen Stelle innerhalb des Textes erstellt werden, indem Sie entweder den Cursor platzieren oder Text auswählen. Klicken Sie dann auf das Symbol **Anker**, um das Dialogfeld zu öffnen.

Geben Sie den Namen des Ankers ein und klicken Sie auf **OK**, um die Änderung zu speichern.

![cq55_rte_anchor_use](assets/cq55_rte_anchor_use.png)

Der Anker wird beim Bearbeiten der Komponente angezeigt und kann nun als Sprungziel für Links verwendet werden.

![chlimage_1-104](assets/chlimage_1-104.png)

### Suchen und Ersetzen {#find-and-replace}

![Symbolleiste „Suchen und Ersetzen“](do-not-localize/cq55_rte_findreplace.png)

AEM enthält die Funktion **Suchen** und die Funktion **Ersetzen** („Suchen und Ersetzen“).

Bei beiden Funktionen ermöglicht die Schaltfläche **Weitersuchen** die Suche nach dem angegebenen Text innerhalb der geöffneten Komponente. Sie können außerdem angeben, ob Groß-/Kleinschreibung beachtet werden soll.

Die Suche beginnt immer an der aktuellen Cursor-Position im Text. Wenn das Ende der Komponente erreicht ist, werden Sie in einer Meldung darüber informiert, dass der nächste Suchvorgang von oben gestartet wird.

![cq55_rte_find_use](assets/cq55_rte_find_use.png)

Die **Ersetzen** -Option **Suchen**, dann **Ersetzen** einer einzelnen Instanz mit dem angegebenen Text oder **Alle ersetzen** Instanzen in der aktuellen Komponente.

![cq55_rte_findreplace_use](assets/cq55_rte_findreplace_use.png)

### Bilder {#images}

Bilder können aus der Inhaltssuche gezogen werden, um sie zum Text hinzuzufügen.

![cq55_rte_image_use](assets/cq55_rte_image_use.png)

>[!NOTE]
>
>AEM bietet auch spezielle Komponenten für eine detailliertere Bildkonfiguration. Beispiel: die **Bild** und **Textbild** -Komponenten verfügbar sind.

### Rechtschreibprüfung {#spelling-checker}

![Rechtschreibprüfung](do-not-localize/cq55_rte_spellchecker.png)

Die Rechtschreibprüfung überprüft den gesamten Text innerhalb der aktuellen Komponente.

Alle falschen Schreibweisen werden hervorgehoben:

![cq55_rte_spellchecker_use](assets/cq55_rte_spellchecker_use.png)

>[!NOTE]
>
>Die Rechtschreibprüfung erfolgt in der Sprache der Website. Dazu wird entweder die Spracheigenschaft der Unterstruktur übernommen oder die Sprache aus der URL extrahiert. Beispiel: die `en` -Zweig wird auf Englisch überprüft, und die `de` Niederlassung für Deutsch.

### Tabellen {#tables}

Tabellen können auf zwei Arten eingefügt werden:

* Als Komponente **Tabelle**

  ![Tabellenkomponente](assets/chlimage_1-105.png)

* Innerhalb der Komponente **Text**

  ![Text-Symbolleiste](do-not-localize/chlimage_1-11.png)

  >[!NOTE]
  >
  >Obwohl im RTE keine Tabellen verfügbar sind, empfiehlt es sich, beim Erstellen von Tabellen die Komponente **Tabelle** zu verwenden.

Sowohl in der Komponente **Text** als auch in der Komponente **Tabelle** sind die Tabellenoptionen über das Kontextmenü verfügbar, das in der Regel durch Klicken mit der rechten Maustaste auf die Tabelle aufgerufen wird. Beispiel:

![cq55_rte_tablemenu](assets/cq55_rte_tablemenu.png)

>[!NOTE]
>
>In der Komponente **Tabelle** ist außerdem eine spezielle Symbolleiste verfügbar, die neben den Standard-Funktionen für die Bearbeitung von Rich-Text auch eine Untergruppe tabellenspezifischer Funktionen enthält.

Die tabellenspezifischen Funktionen sind:

* [Tabelleneigenschaften](#table-properties)
* [Zelleneigenschaften](#cell-properties)
* [Zeilen hinzufügen oder löschen](#add-or-delete-rows)
* [Spalten hinzufügen oder löschen](#add-or-delete-columns)
* [Ganze Zeilen oder Spalten auswählen](#selecting-entire-rows-or-columns)
* [Zellen verbinden](#merge-cells)
* [Zellen teilen](#split-cells)
* [Verschachtelte Tabellen](#creating-nested-tables)
* [Tabelle entfernen](#remove-table)

#### Tabelleneigenschaften {#table-properties}

![cq55_rte_tableproperties_icon](assets/cq55_rte_tableproperties_icon.png)

Sie können die grundlegenden Eigenschaften der Tabelle angeben und dann auf **OK** klicken, um die Angaben zu speichern:

![cq55_rte_tableproperties_dialog](assets/cq55_rte_tableproperties_dialog.png)

* **Breite**: Die Gesamtbreite der Tabelle.

* **Höhe**: Die Gesamthöhe der Tabelle.

* **Rahmen**: Die Rahmenbreite der Tabelle.

* **Textabstand**: Die Breite des Leerraums zwischen Zelleninhalt und Rahmen.

* **Zellenabstand**: Der Abstand zwischen den Zellen.

>[!NOTE]
>
>Einige Zelleneigenschaften wie Breite und Höhe können als Pixel oder Prozentwerte definiert werden.

>[!CAUTION]
>
>Adobe empfiehlt, eine Breite für die Tabelle anzugeben.

#### Zelleneigenschaften {#cell-properties}

![cq55_rte_cellproperties_icon](assets/cq55_rte_cellproperties_icon.png)

Die Eigenschaften einer Zelle bzw. einer Reihe von Zellen können konfiguriert werden:

![cq55_rte_cellproperties_dialog](assets/cq55_rte_cellproperties_dialog.png)

* **Breite**
* **Höhe**
* **Horizontale Ausrichtung**: Links, Mitte oder rechts
* **Vertikale Ausrichtung**: Oben, Mitte, unten oder Grundlinie
* **Zellentyp**: Daten oder Kopfzeile
* **Anwenden auf**: Einzelne Zelle, gesamte Zeile, gesamte Spalte

#### Zeilen hinzufügen oder löschen {#add-or-delete-rows}

![cq55_rte_rows](assets/cq55_rte_rows.png)

Zeilen können entweder über oder unter der aktuellen Zeile hinzugefügt werden.

Die aktuelle Zeile kann außerdem gelöscht werden.

#### Hinzufügen oder Löschen von Spalten {#add-or-delete-columns}

![cq55_rte_columns](assets/cq55_rte_columns.png)

Spalten können entweder links oder rechts von der aktuellen Spalte hinzugefügt werden.

Die aktuelle Spalte kann außerdem gelöscht werden.

#### Auswählen ganzer Zeilen oder Spalten {#selecting-entire-rows-or-columns}

![chlimage_1-106](assets/chlimage_1-106.png)

Dadurch wird die gesamte Zeile bzw. Spalte ausgewählt. Anschließend sind bestimmte Aktionen verfügbar (z. B. Zusammenführen).

#### Zusammenführen von Zellen {#merge-cells}

![cq55_rte_cellmerge](assets/cq55_rte_cellmerge.png) ![cq55_rte_cellmerge-1](assets/cq55_rte_cellmerge-1.png)

* Wenn Sie eine Gruppe von Zellen ausgewählt haben, können Sie sie zu einer einzigen Zelle fusionieren.
* Wenn Sie nur eine Zelle ausgewählt haben, können Sie diese Zelle mit der Zelle rechts davon oder der Zelle unterhalb davon fusionieren.

#### Teilen von Zellen {#split-cells}

![cq55_rte_cellsplit](assets/cq55_rte_cellsplit.png)

Auswählen einer einzelnen Zelle, um sie zu teilen:

* Wenn Sie eine Zelle horizontal teilen, wird eine neue Zelle rechts neben der aktuellen Zelle in der aktuellen Spalte generiert.
* Wenn Sie eine Zelle vertikal teilen, wird eine neue Zelle unter der aktuellen Zelle, jedoch innerhalb der aktuellen Zeile generiert.

#### Erstellen verschachtelter Tabellen {#creating-nested-tables}

![chlimage_1-107](assets/chlimage_1-107.png)

Beim Erstellen einer verschachtelten Tabelle wird eine eigenständige Tabelle innerhalb der aktuellen Zelle erstellt.

>[!NOTE]
>
>Bestimmte zusätzliche Verhaltensweisen sind vom Browser abhängig:
>
>* Windows IE: Verwenden Sie Strg+primäre Maustaste (normalerweise linke Maustaste), um mehrere Zellen auszuwählen.
>* Firefox: Ziehen Sie den Mauszeiger, um einen Zellenbereich auszuwählen.

#### Tabelle entfernen {#remove-table}

![cq55_rte_removtable](assets/cq55_rte_removetable.png)

Verwenden Sie die Option, um die Tabelle aus der Komponente **[!UICONTROL Text]** zu entfernen.

### Sonderzeichen {#special-characters}

![Symbolleiste für Sonderzeichen](do-not-localize/cq55_rte_specialchars.png)

Sonderzeichen können Ihrem Rich-Text-Editor zur Verfügung gestellt werden. Diese können je nach Installation variieren.

![cq55_rte_specialchars_use](assets/cq55_rte_specialchars_use.png)

Verwenden Sie den Mauszeiger, um eine vergrößerte Version des Zeichens anzuzeigen, und klicken Sie dann darauf, um es an der aktuellen Position in Ihrem Text einzufügen.

### Quellbearbeitungsmodus {#source-editing-mode}

![Symbolleiste des Quellbearbeitungsmodus](do-not-localize/cq55_rte_sourceedit.png)

Im Quellbearbeitungsmodus können Sie die zugrunde liegende HTML der Komponente anzeigen und bearbeiten.

Der Text:

![cq55_rte_sourcemode_1](assets/cq55_rte_sourcemode_1.png)

Im Quellmodus hat dieser Text folgende Gestalt (oft ist der HTML-Quelltext wesentlich länger und Sie müssen einen Bildlauf durchführen):

![cq55_rte_sourcemode_2](assets/cq55_rte_sourcemode_2.png)

>[!CAUTION]
>
>Beim Verlassen des Quellmodus führt AEM bestimmte Prüfungen durch (z. B. ob der Text ordnungsgemäß in Blöcken enthalten bzw. verschachtelt ist). Dies kann zu Änderungen an Ihren Bearbeitungen führen.
