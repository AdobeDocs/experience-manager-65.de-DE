---
title: Der Bulk Editor
description: Erfahren Sie, wie Sie den Bulk Editor für eine effiziente Bearbeitung verwenden können, wenn der visuelle Seitenkontext nicht benötigt wird.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: c63e044c-4d2a-44d3-853b-8e7337e1ee03
source-git-commit: 06a6d4e0ba2aeaefcfb238233dd98e8bbd6731da
workflow-type: tm+mt
source-wordcount: '1159'
ht-degree: 21%

---


# Der Bulk Editor{#the-bulk-editor}

Der Bulk Editor ermöglicht eine effiziente Bearbeitung, wenn der visuelle Seitenkontext nicht benötigt wird, da Sie mit ihm:

* Inhalte von mehreren Seiten suchen (und anzeigen); dazu wird GQL (Google Query Language) genutzt
* Bearbeiten Sie diesen Inhalt direkt im Bulk Editor
* die Änderungen speichern (in den Originalseiten)
* diese Inhalte in eine tabulatorgetrennte Tabellendatei (.tsv) exportieren

>[!NOTE]
>
>Sie können auch Inhalte in das Repository importieren. Standardmäßig ist dies jedoch für den Bulk Editor deaktiviert, wie im Abschnitt **Instrumente** Konsole.

In diesem Abschnitt wird beschrieben, wie Sie mit dem Bulk Editor im **Instrumente** Konsole. In der Regel verwenden Administratoren den Bulk Editor, um mehrere Elemente zu suchen und zu bearbeiten. Dazu füllen Sie die Tabelle mit einer GQL-Abfrage aus und wählen dann die zu bearbeitenden Inhaltselemente aus. Autoren verwenden den Bulk Editor im Allgemeinen als Teil einer benutzerdefinierten Bulk Editor-Anwendung, auf die über die [Produktliste](/help/sites-authoring/default-components.md#productlist) -Komponente.

>[!CAUTION]
>
>Mit dem [Einstellung der klassischen Benutzeroberfläche](/help/release-notes/deprecated-removed-features.md) In AEM 6.4 ist der Bulk Editor ebenfalls veraltet und Adobe plant daher keine weitere Verbesserung des Bulk Editors.

## Anwendungsbeispiel für den Bulk Editor {#example-use-case-for-the-bulk-editor}

Wenn Sie beispielsweise alle Namen und E-Mail-Adressen von Benutzern benötigen, die eine bestimmte Umfrage ausgefüllt haben, kann der Bulk Editor diese Informationen bereitstellen und in eine Tabelle exportieren.

Ein Beispiel zur Veranschaulichung eines solchen Anwendungsfalls finden Sie auf der Geometrixx-Website:

1. Navigieren Sie zum **Support** und dann zum **Zufriedenheit des Kundendienstes** Umfrage.
1. **Bearbeiten** die **Formularstart** Absatz. Klicken Sie im Dialogfeld auf die **Erweitert** Registerkarte, erweitern Sie die **Aktionskonfiguration** Klicken Sie auf **Daten anzeigen...**.

   ![Beispiel für eine Umfrage zur Kundenzufriedenheit](assets/custsatsurvey.png)

1. Der Bulk Editor kann vollständig angepasst werden. Im Bulk Editor können Benutzer den Inhalt jedoch nicht bearbeiten, sondern nur exportieren.

   ![Bulk Editor-Konsole](assets/bulkeditor.png)

## Verwenden des Bulk Editors {#how-to-use-the-bulk-editor}

Mit dem Bulk Editor können Sie:

* [basierend auf Abfrageparametern nach Inhalten suchen, festgelegte Eigenschaften der Ergebnisse in Spalten anzeigen, diese Inhalte bearbeiten und die Änderungen speichern](#searching-and-editing-content)
* [diese Inhalte in eine tabulatorgetrennte Tabelle exportieren](#exporting-content)

* [Inhalte aus einer tabulatorgetrennten Tabelle importieren](#importing-content)

### Suchen und Bearbeiten von Inhalten {#searching-and-editing-content}

So bearbeiten Sie mit dem Bulk Editor mehrere Elemente gleichzeitig:

1. Im **Instrumente** klicken Sie auf die **Importtools** Ordner, um ihn zu erweitern.
1. Doppelklicken Sie auf die **Bulk Editor**.
1. Geben Sie Ihre Auswahlanforderungen an:

<table>
 <tbody>
  <tr>
   <td>Feld</td>
   <td>Eigenschaft</td>
  </tr>
  <tr>
   <td>Stammverzeichnis</td>
   <td>Gibt den Stammpfad an, den der Bulk Editor durchsucht.<br /> Beispiel, <code>/content/geometrixx/en</code>. Der Bulk Editor durchsucht alle untergeordneten Knoten.</td>
  </tr>
  <tr>
   <td>Abfrageparameter</td>
   <td>Geben Sie mithilfe der GQL-Parameter die Suchzeichenfolge ein, nach der der Bulk Editor im Repository suchen soll. Beispiel: <code>type:Page</code> sucht nach allen Seiten im Stammpfad, <code>text:professional</code> sucht nach allen Seiten, die das Wort "professionell"enthalten, und <code>"jcr:title":English</code> sucht nach allen Seiten, die "Englisch"als Titel haben. Sie können nur nach Zeichenfolgen suchen.</td>
  </tr>
  <tr>
   <td>Kontrollkästchen „Inhaltsmodus“</td>
   <td>Aktivieren Sie dieses Kontrollkästchen, damit Sie Eigenschaften in der <code>jcr:content</code> Unterknoten der Suchergebnisse, falls vorhanden. Diese Option ist nur für Seiten nutzbar. Eigenschaftsnamen erhalten das Präfix <code>"jcr:content/"</code></td>
  </tr>
  <tr>
   <td>Eigenschaften/Spalten</td>
   <td>Aktivieren Sie die Kontrollkästchen für die Eigenschaften, die der Bulk Editor zurückgeben soll. Die Eigenschaften, die Sie auswählen, sind die Spaltenüberschriften im Ergebnisbereich. Standardmäßig wird der Knotenpfad in den Ergebnissen angezeigt.</td>
  </tr>
  <tr>
   <td>Benutzerdefinierte Eigenschaften/Spalten</td>
   <td>Geben Sie alle anderen Eigenschaften ein, die nicht im Feld <strong>Eigenschaften/Spalten</strong> aufgeführt sind. Diese benutzerdefinierten Eigenschaften werden im Ergebnisbereich angezeigt. Sie können mehrere Eigenschaften mithilfe eines Kommas hinzufügen, um Eigenschaften zu trennen. <i>Hinweis:</i> Wenn Sie eine benutzerdefinierte Eigenschaft hinzufügen, die noch nicht vorhanden ist, zeigt AEM WCM eine leere Zelle an. Wenn Sie die leere Zelle ändern und speichern, wird die Eigenschaft zum Knoten hinzugefügt. Die neu erstellte Eigenschaft muss Einschränkungen des Knotentyps und Eigenschafts-Namespaces berücksichtigen.</td>
  </tr>
 </tbody>
</table>

Beispiel:

![Masseneditor-Filteroptionen](assets/searchfilter.png)

1. Klicken Sie auf **Suchen**. Der Bulk Editor zeigt die Suchergebnisse an.
Im Beispiel oben werden alle Seiten, die Ihren Suchkriterien entsprechen, zurückgegeben und in den geforderten Spalten angezeigt.

   ![Ergebnisse des Bulk Editors](assets/chlimage_1-39.png)

1. Doppelklicken Sie auf eine Zelle, damit Sie Änderungen vornehmen können.

   ![Massenbearbeitung](assets/srchresultedit.png)

1. Klicks **Speichern** um Ihre Änderungen zu speichern (die **Speichern** aktiviert ist, nachdem Sie eine Zelle bearbeitet haben).

   >[!CAUTION]
   >
   >Die hier vorgenommenen Änderungen werden in den Repository-Inhalt geschrieben, z. B. die Seite, auf die unter **Pfad** verwiesen wird.

#### Weitere GQL-Abfrageparameter {#additional-gql-query-parameters}

* **path:** Durchsucht nur Knoten unter diesem Pfad. Wenn Sie mehr als einen Begriff mit einem Pfadpräfix angeben, wird nur der letzte Begriff berücksichtigt.
* **Typ:** gibt nur Knoten des angegebenen Knotentyps zurück. Dies umfasst die Typen &quot;primary&quot;und &quot;mixin&quot;. Sie können mehrere kommagetrennte Knotentypen angeben. GQL gibt Knoten zurück, die einen der angegebenen Typen aufweisen.
* **order:** Sortiert das Ergebnis nach den bestimmten Eigenschaften. Sie können mehrere kommagetrennte Eigenschaftsnamen angeben. Um das Ergebnis in absteigender Reihenfolge anzuordnen, setzen Sie einfach das Präfix des Eigenschaftsnamens auf ein Minuszeichen. Beispiel: order:-name. Durch die Verwendung eines Pluszeichens wird das Ergebnis in aufsteigender Reihenfolge zurückgegeben, was auch der Standardwert ist.
* **limit:** Begrenzt die Anzahl der Ergebnisse mithilfe eines Intervalls. Beispiel: limit:10.20 Das Intervall basiert auf null, der Beginn ist inklusiv und das Ende ist exklusiv. Sie können auch ein offenes Intervall festlegen: :limit:10.. oder limit:..20 Wenn die Punkte weggelassen und nur ein Wert angegeben wird, gibt GQL höchstens diese Anzahl von Ergebnissen zurück. Beispiel: limit:10 (gibt die ersten zehn Ergebnisse zurück).

### Inhalt exportieren {#exporting-content}

Exportieren Sie bei Bedarf Inhalte in eine Excel-Tabelle, um Änderungen vorzunehmen. Sie können beispielsweise eine Mailingliste exportieren und den Bereichscode aller aufgelisteten Telefonnummern direkt in Excel ändern oder zusätzliche Zeilen hinzufügen.

So exportieren Sie Inhalte:

1. Suchen Sie nach Inhalt, wie unter [Suchen und Bearbeiten von Inhalten](#searching-and-editing-content).
1. Klicks **Export** sodass Sie die Änderungen in eine tabulatorgetrennte Excel-Tabelle exportieren können. AEM WCM fragt Sie, wo Sie die Datei herunterladen möchten.

   >[!NOTE]
   >
   >Standardmäßig sind Änderungen in [Windows-1252](https://de.wikipedia.org/wiki/Windows-1252) (auch bekannt als CP-1252). Sie können UTF-8 aktivieren, um die Änderungen in UTF-8 zu exportieren.

   ![Ergebnisse exportieren](assets/srchrsesultexport.png)

1. Wählen Sie den Speicherort aus und bestätigen Sie, dass Sie die Datei herunterladen möchten.
1. Nachdem Sie die Datei heruntergeladen haben, können Sie sie über Ihr Tabellenkalkulationsprogramm öffnen, z. B. Microsoft® Excel. Das Tabellenprogramm importiert die Datei und konvertiert sie in ein Tabellenformat.

   ![Exportierte Ergebnisse in einer Tabelle](assets/exportinexcel.png)

### Inhalt importieren {#importing-content}

Standardmäßig ist die Importfunktion beim Öffnen des Bulk Editors ausgeblendet. Fügen Sie einfach den Parameter hinzu `hib=false` an die URL verweist, zeigt die **Import** auf der Seite &quot;Bulk Editor&quot;angezeigt. Sie können Inhalte aus jeder tabulatorgetrennten Datei (`.tsv`) importieren. Damit der Import ordnungsgemäß funktioniert, müssen die Spaltenüberschriften (erste Zellenzeile) mit den Spaltenüberschriften der Tabelle übereinstimmen, in die Sie importieren.

>[!NOTE]
>
>Wenn Sie Inhalte erneut importieren, löschen Sie alle vorherigen Inhalte für diese Knoten. Achten Sie darauf, wichtige Informationen nicht zu überschreiben.

So importieren Sie Inhalte:

1. Öffnen Sie den Bulk Editor.
1. Hinzufügen `?hib=false` zur URL hinzu, beispielsweise:
   `https://localhost:4502/etc/importers/bulkeditor.html?hib=false`
1. Wählen Sie **Importieren** aus.
1. Wählen Sie die `.tsv`-Datei aus. Die Daten werden in das Repository importiert.
