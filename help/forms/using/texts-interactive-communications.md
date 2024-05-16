---
title: Texte in interaktiver Kommunikation
description: 'Erstellen und Bearbeiten von Textdokumentfragmenten für interaktive Kommunikationen: Text ist eine der vier Arten von Dokumentfragmenten, die zum Erstellen von interaktive Kommunikationen verwendet werden. Die anderen drei sind Bedingungen, Listen und Layout-Fragmente.  '
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: b8e84c5d-2ec8-4575-9eed-6b37b04e5d66
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '2474'
ht-degree: 100%

---

# Texte in interaktiver Kommunikation{#texts-in-interactive-communications}

## Übersicht {#overview}

Ein Textdokumentfragment besteht aus einem oder mehreren Textabsätzen. Ein Absatz kann statisch oder dynamisch sein. Ein dynamischer Absatz kann Formulardatenmodelleigenschaften und -variablen enthalten. Sie können Regeln auch anwenden und innerhalb eines Textdokumentfragments wiederholen. So könnte beispielsweise der Kundenname in einer Grußformel eine Formulardatenmodell (FDM)-Eigenschaft sein, dessen Wert zur Laufzeit bereitgestellt wird. Durch Änderung dieser Werte können Sie dieselbe interaktive Kommunikation verwenden, um die interaktive Kommunikation für die verschiedenen Kunden mit der Benutzung der Benutzeroberfläche für Agenten vorzubereiten.

Das Textdokumentfragment in der interaktiven Kommunikation unterstützt den folgenden Typ dynamischer Daten:

* **Datenmodellobjekte**: Die Dateneigenschaften verwenden eine Back-End-Datenquelle.
* **Regelbasierter Inhalt**: Teile des Inhalts in einem Text, die basierend auf einer Regel angezeigt oder ausgeblendet werden. Eine Regel könnte auch auf den Eigenschaften und Variablen des Formulardatenmodells basieren.
* **Variablen**: Im Textdokumentfragment sind Variablen nicht an eine Backend-Datenquelle gebunden. Der Agent füllt/wählt Werte in Variablen oder bindet die Variablen an Datenquellen während der Vorbereitung der interaktiven Kommunikation zum Senden an einen Nachbearbeitungsprozess.
* **Wiederholen**: Sie haben eventuell dynamische Informationen in Ihrer interaktiven Kommunikation, z. B. Transaktionen in einem Kreditkartenauszug, deren Anzahl sich mit jeder generierten interaktiven Kommunikation ändern kann. Wenn Sie die Wiederholen-Funktion verwenden, können Sie solche dynamischen Daten formatieren und strukturieren. Weitere Informationen finden Sie unter [Inline-Zustand und Wiederholung](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/cm-inline-condition.html).

## Text erstellen {#createtext}

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Text]**.
1. Geben Sie die folgenden Daten an:

   * **[!UICONTROL Titel]**: (Optional) Geben Sie den Titel für das Textdokumentfragment ein. Titel müssen nicht eindeutig sein und dürfen Sonderzeichen und nicht-englische Zeichen enthalten. Texte werden durch ihren Titel (falls verfügbar) wie etwa in Miniaturen und Eigenschaften referenziert.
   * **[!UICONTROL Name]**: Der eindeutige Name des Texts, in einem Ordner. Es ist nicht möglich, dass zwei Dokumentfragmente (Text, Bedingung oder Liste) mit demselben Namen vorhanden sind, ungeachtet ihres jeweiligen Status. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.

   * **[!UICONTROL Beschreibung]**: Geben Sie eine Beschreibung des Textes ein.
   * **[!UICONTROL Formulardatenmodell]**: Wählen Sie optional das Optionsfeld „Formulardatenmodell“ aus, um den Text basierend auf einem Formulardatenmodell zu erstellen. Wenn Sie das Optionsfeld „Formulardatenmodell“ auswählen, wird das Feld **[!UICONTROL Formulardatenmodell]** angezeigt. Suchen Sie nach einem Formulardatenmodell und wählen Sie es aus. Stellen Sie beim Erstellen des Textes und der Bedingung für eine interaktive Kommunikation sicher, dass Sie dasselbe Datenmodell nutzen, das in der interaktiven Kommunikation verwendet werden soll. Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration](/help/forms/using/data-integration.md).

   * **[!UICONTROL Tags]**: Um optional einen benutzerdefinierten Tag zu erstellen, geben Sie einen Wert in das Textfeld ein und drücken Sie die Eingabetaste. Wenn Sie diesen Text speichern, werden die neu hinzugefügten Tags erstellt.

1. Wählen Sie **[!UICONTROL Weiter]** aus.

   Die Seite „Text erstellen“ wird angezeigt. Wenn Sie sich entschieden haben, einen formulardatenmodellbasierten Text zu erstellen, werden die Eigenschaften des Formulardatenmodells im linken Bereich angezeigt.

1. Geben Sie den Text ein und verwenden Sie die folgenden Optionen zum Formatieren, Konditionalisieren und Einfügen von Formulardatenmodelleigenschaften und -variablen in Ihren Text:

   * [Formulardatenmodell](#formdatamodel)
   * [Variablen](#variables)
   * [Regeleditor](#rules)
   * [Formatierungsoptionen](#formatting)

      * [Formatierten Text aus anderen Anwendungen kopieren/einfügen](#paste)

      * [Teile des Textes markieren](#highlight)

   * [Wiederholen](/help/forms/using/cm-inline-condition.md)
   * [Sonderzeichen](#special)
   * [Text suchen und ersetzen](#searching)
   * [Tastaturbefehle](/help/forms/using/keyboard-shortcuts.md)

   >[!NOTE]
   >
   >Sie können Formulardatenmodellelemente, Datenwörterbuchelemente und Variablen mithilfe des @-Symbols im Texteditor hinzufügen. Wenn Sie eine Zeichenfolge eingeben, der im Texteditor ein „@“ vorangestellt ist, werden alle Datenmodellelemente, Datenwörterbuchelemente und Variablen durchsucht und die Elemente oder Variablen, die die gesuchte Zeichenfolge enthalten, werden angezeigt. Sie können durch die Suchergebnisse navigieren und ein Element oder eine Variable auswählen. Wenn kein übereinstimmendes Ergebnis vorliegt, wird die Nachricht *Keine übereinstimmenden Ergebnisse gefunden* angezeigt.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   Der Text wird erstellt. Jetzt können Sie den Text als Baustein beim Erstellen einer interaktiven Kommunikation verwenden.

## Text bearbeiten {#edittext}

Sie können ein vorhandenes Textdokumentfragment wie folgt bearbeiten: Sie können auch ein Textdokumentfragment innerhalb eines interaktiven Kommunikationseditor bearbeiten.

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Navigieren Sie zu einem Textdokumentfragment und wählen Sie es aus.
1. Wählen Sie **[!UICONTROL Bearbeiten]** aus.
1. Nehmen Sie die erforderlichen Änderungen vor. Weitere Informationen zu Optionen im Text finden Sie unter [Text erstellen](#createtext).
1. Wählen Sie **[!UICONTROL Speichern]** und dann **[!UICONTROL Schließen]** aus.

## Personalisieren eines Textdokumentfragments mithilfe der Eigenschaften des Formulardatenmodells {#formdatamodel}

Sie können Textdokumentfragmente personalisieren, indem Sie die Eigenschaften des Formulardatenmodells einfügen. Wenn Sie die Eigenschaften der Formulardaten in Text einfügen, können Sie empfängerspezifische Daten aus der Datenquelle für die Vorschau einer interaktiven Kommunikation abrufen und befüllen. Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

Wenn Sie beim Erstellen eines Texts ein Formulardatenmodell angegeben haben, werden die Eigenschaften im Formulardatenmodell im linken Bereich des Texteditors angezeigt. Das angegebene Formulardatenmodell sollte für das Textdokumentfragment sowie für die interaktive Kommunikation, die es enthält, identisch sein.

![insertfdmelementtext](assets/insertfdmelementtext.png)

* Um eine Formulardatenmodell-Eigenschaft in Text einzufügen, platzieren Sie den Cursor an die Stelle, an der Sie die Eigenschaft einfügen möchten. Wählen Sie dann im linken Bereich die Eigenschaft **[A]** aus, indem Sie darauf tippen, und wählen Sie **[!UICONTROL [B] Ausgewählte hinzufügen]**. Sie können auch einfach die Eigenschaft doppelt auswählen, um sie an der Cursor-Position **[C]** einzufügen. Die Eigenschaften des Formulardatenmodells werden in einer bräunlichen Hintergrundfarbe hervorgehoben.

Alternativ können Sie die Eigenschaft des Formulardatenmodells mit dem @-Symbol im Texteditor suchen und hinzufügen. Platzieren Sie den Cursor an die Stelle, an der Sie die Eigenschaft einfügen möchten. Geben Sie @ ein, gefolgt von der Suchzeichenfolge. Der Suchvorgang wird für alle Eigenschaften und Variablen des Formulardatenmodells ausgeführt, die im Dokumentfragment verfügbar sind. Die Eigenschaften oder Variablen, die die Suchzeichenfolge enthalten, werden abgerufen und als Dropdown-Liste angezeigt. Navigieren Sie durch die Suchergebnisse und klicken Sie an der Position des Cursors auf die Eigenschaft, die Sie einfügen möchten. Drücken Sie Esc, um die Suchergebnisse auszublenden.

* Damit die Agenten einen Eigenschaftswert eines Formulardatenmodells in der Agent-Benutzeroberfläche bearbeiten können, während Sie mithilfe der Agent-Benutzeroberfläche eine [interaktive Kommunikation vorbereiten und senden](/help/forms/using/prepare-send-interactive-communication.md), wählen Sie das **[D]** Schloss-Symbol für diese Eigenschaft aus und stellen Sie sicher, dass es entsperrt ist. Der Standardstatus der Eigenschaft ist gesperrt und ein Agent kann die Eigenschaft in der Benutzeroberfläche für Agenten nicht bearbeiten.

Sie können die Eigenschaften des Formulardatenmodells auch verwenden, um Regeln zum Anzeigen oder Ausblenden von Inhaltsbereichen zu erstellen. Weitere Informationen finden Sie unter [Erstellen von Regeln im Text](#rules).

## Erstellen und Verwenden von Variablen in einem Textdokumentfragment {#variables}

Variablen sind Platzhalter, die beim Erstellen einer interaktiven Kommunikation gebunden werden können. Variablen können an eine Eigenschaft des Formulardatenmodells oder an ein Textfragment gebunden werden. Sie können Variablen auch vom Agenten ausfüllen lassen.

Sie können Variablen anstelle von Eigenschaften des Formulardatenmodells verwenden, wenn Folgendes gilt:

* Ein Textdokumentfragment wird in mehreren interaktiven Kommunikationen verwendet, wobei die Bindung für verschiedene interaktive Kommunikationen unterschiedlich sein muss.
* Das Textdokumentfragment hat zum Zeitpunkt seiner Erstellung kein Formulardatenmodell. Sie können Variablen einfügen und später beim Erstellen der interaktiven Kommunikation an die Eigenschaften des Formulardatenmodells binden.
* Sie müssen Text aus einem Textdokumentfragment binden und abrufen. Nur diejenigen Textdokumentfragmente können an Variablen gebunden werden, die keine Variablen enthalten.

Beim Erstellen oder Bearbeiten eines Textdokumentfragments können Sie Variablen erstellen und einfügen. Die von Ihnen erstellten Variablen werden auf der Registerkarte „Daten“ der Agenten-Benutzeroberfläche angezeigt. Der Agent gibt die Werte für die Variablen an, während [Vorbereiten und Senden der interaktiven Kommunikation über die Benutzeroberfläche des Agenten](/help/forms/using/prepare-send-interactive-communication.md) läuft.

### Variablen erstellen {#createvariables}

1. Wählen Sie im linken Bereich **[!UICONTROL Variablen]** aus.

   Der Variablenbereich wird angezeigt.

   ![variablespanel](assets/variablespane.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   Der Bereich „Variablen erstellen“ wird angezeigt.

1. Geben Sie die folgenden Informationen ein und wählen Sie **[!UICONTROL Erstellen]** aus:

   * **[!UICONTROL Name]**: Name der Variablen.
   * **[!UICONTROL Beschreibung]**: Geben Sie optional eine Beschreibung der Variablen ein.
   * **[!UICONTROL Typ]**: Wählen Sie einen Typ der Variablen: Zeichenfolge, Zahl, Boolesch oder Datum.
   * **[!UICONTROL Nur bestimmte Werte zulassen]**: Bei Zeichenfolge- und Zahl-Variablen können Sie sicherstellen, dass der Agent aus einem bestimmten Satz von Werten für einen Platzhalter in der Agent-UI auswählt. Um den Wertesatz anzugeben, wählen Sie diese Option aus und geben Sie dann durch Komma getrennte Werte an, die im Feld **[!UICONTROL Werte]** zulässig sind.

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   Die Variable wird erstellt und im Bereich „Variablen“ aufgelistet.

1. Um eine Variable in den Text einzufügen, platzieren Sie den Cursor an der entsprechenden Stelle, wählen Sie die Variable aus und wählen Sie **[!UICONTROL Ausgewählte hinzufügen]** aus.

   ![variableinserted](assets/variableinserted.png)

   Variablen werden in hellblauer Hintergrundfarbe hervorgehoben, während Formulardatenmodelleigenschaften in einer bräunlichen Farbe hervorgehoben werden.

   Alternativ können Sie Variablen mithilfe des @-Symbols im Texteditor suchen und hinzufügen. Platzieren Sie den Cursor an die Stelle, an der die Variable eingefügt werden soll. Geben Sie @ ein, gefolgt von der Suchzeichenfolge. Der Suchvorgang wird für alle Eigenschaften und Variablen des Formulardatenmodells ausgeführt, die im Dokumentfragment verfügbar sind. Die Eigenschaften und Variablen, die den Suchbegriff enthalten, werden abgerufen und als Dropdown-Liste angezeigt. Navigieren Sie durch die Suchergebnisse und klicken Sie an der Cursorposition auf die Variable, die Sie einfügen möchten. Drücken Sie Esc, um die Suchergebnisse auszublenden.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

## Erstellen von Regeln im Text {#rules}

Durch Anwendung des Regeleditors in einem Text können Sie Regeln erstellen, um Textzeichenfolgen oder Teile des Inhalts, die auf **Vorgabebedingungen** basieren, ein- oder auszublenden. Diese Bedingungen können basierend auf Folgendem erstellt werden:

* Zeichenfolgen
* Zahlen
* mathematischen Ausdrücken
* Datumswerten
* Eigenschaften des zugeordneten Formulardatenmodells
* ggf. im Text erstellten Variablen

### Erstellen von Regeln im Text {#create-rules-in-text}

1. Wählen Sie beim Erstellen oder Bearbeiten eines Textes die Textzeichenfolge, den Absatz oder den Inhalt aus, die bzw. der mit der Regel konditioniert werden soll.

   ![selectcontentapplyrule](assets/selectcontentapplyrule.png)

1. Wählen Sie **[!UICONTROL Regel erstellen]** aus.

   Das Dialogfeld „Regel erstellen“ wird angezeigt. Zusätzlich zu Zeichenfolge, Zahl, mathematischem Ausdruck und Datum steht im Regeleditor Folgendes zum Erstellen der Regelanweisungen zur Verfügung:

   * Eigenschaften des zugeordneten Formulardatenmodells
   * ggf. von Ihnen erstellte Variablen

   Wählen Sie die geeignete Option aus, die ausgewertet werden soll.

   ![ruleeditor](assets/ruleeditor.png) ![ruleeditorfdm](assets/ruleeditorfdm.png)

   >[!NOTE]
   >
   >Die Sammlungseigenschaft wird nicht zum Erstellen von Regeln unterstützt, mit denen Text angezeigt wird und Bedingungen festgelegt werden.

1. Wählen Sie den entsprechenden Operator aus, um die Regel auszuwerten, z. B. Gleich ist, Enthält und Beginnt mit.

   ![ruleeditorfdm-1](assets/ruleeditorfdm-1.png)

1. Fügen Sie den auswertenden Ausdruck, den Wert, die Datenmodelleigenschaft oder die Variable ein.

   ![Regel, um den ausgewählten Text anzuzeigen, wenn der Standort des Empfängers gemäß den Quelldaten von FDM US ist](assets/ruleeditorfdm-1-1.png)

   Regel, um den ausgewählten Text anzuzeigen, wenn der Standort des Empfängers gemäß den Quelldaten von FDM US ist

   * Beim Erstellen oder Bearbeiten einer Regel können Sie auch ![icon_resize](assets/icon_resize.png) (Größe ändern) auswählen, um das Dialogfeld „Regel erstellen/Regel bearbeiten“ zu erweitern. Der erweiterte Vollbilddialog ermöglicht Ihnen, Eigenschaften des Formulardatenmodells und Variablen mittels Drag-and-Drop einzufügen, um Regeln zu erstellen. Wählen Sie erneut „Größe ändern“ aus, um zum Dialogfeld „Regel erstellen“ zurückzukehren.
   * Sie können auch mehrere Bedingungen in einer Regel erstellen.
   * Sie können auch überlappende Regeln erstellen, in denen eine Regel auf einen Teil eines Inhalts angewendet wird, auf den bereits eine Regel angewendet wurde.

1. Wählen Sie **[!UICONTROL Fertig]**.

   Die Regel wird angewendet. Der Text oder Inhalt, auf den die Regel angewendet wird, wird grün hervorgehoben. Wenn Sie den Mauszeiger über den linken Ziehpunkt der Hervorhebung bewegen, wird die angewendete Regel angezeigt.

   ![appliedruletext](assets/appliedruletext.png)

   Wenn Sie auf den linken Handler der angewendeten Regel klicken, erhalten Sie die Optionen zum Bearbeiten oder Entfernen der Regel.

## Formatieren von Text {#formatting}

Beim Erstellen oder Bearbeiten von Text ändert sich die Symbolleiste je nach dem Typ der Bearbeitung, die Sie wählen: Absatz, Ausrichtung oder Auflistung:

![Symbolleistentyp auswählen](do-not-localize/toolbarselection.png)

Wählen Sie den Typ der Symbolleiste aus: Absatz, Ausrichtung oder Auflistung

![Symbolleiste zum Bearbeiten der Schriftart](do-not-localize/paragraphtoolbar.png)

Symbolleiste zum Bearbeiten der Schriftart

![Ausrichtungs-Symbolleiste](assets/alignmenttoolbar.png)

Ausrichtungs-Symbolleiste

![Auflistungs-Symbolleiste](do-not-localize/listingtoolbar.png)

Auflistungs-Symbolleiste

### Hervorheben von Teilen des Textes {#highlight}

Um Teile eines Textes in einem bearbeitbaren Dokumentfragment hervorzuheben, wählen Sie den Text und dann „Hervorhebungsfarbe“ aus.

![textbackgroundcolorapplied-1](assets/textbackgroundcolorapplied-1.png)

Sie können entweder direkt eine Grundfarbe `**[A]**` in der Grundfarbenpalette auswählen oder auf **Auswählen** klicken, nachdem Sie den Regler `**[B]**` verwendet haben, um den entsprechenden Farbton der Farbe festzulegen.

Sie können auch auf der Registerkarte „Erweitert“ die gewünschten Werte für Farbton, Helligkeit und Sättigung `**[C]**` auswählen, um die Farbe präzise festzulegen, und dann „Auswählen“ `**[D]**` wählen, um die Farbe zum Hervorheben des Textes anzuwenden.

![textbackgroundcolor-2](assets/textbackgroundcolor-2.png)

### Einfügen von formatiertem Text {#paste}

Um Textabsätze wiederzuverwenden, die in einer anderen Anwendung vorhanden sind, z. B. auf Microsoft® Word- oder HTML-Seiten, kopieren Sie den Text in den Texteditor. Die Formatierung des kopierten Texts wird im Texteditor beibehalten.

Sie können Textabsätze in ein bearbeitbares Textdokumentfragment kopieren. Beispielsweise haben Sie ein Microsoft® Word-Dokument mit einer Aufzählung von akzeptablen Aufenthaltsnachweisen:

![pastetextmsword-2](assets/pastetextmsword-2.png)

Sie können den Text direkt aus dem Microsoft® Word-Dokument in ein bearbeitbares Textdokumentfragment kopieren. Die Formatierung wie Aufzählungsliste, Schriftart oder Textfarbe bleibt im Textdokumentfragment erhalten.

![pastetexteditablemodule-1](assets/pastetexteditablemodule-1.png)

>[!NOTE]
>
>Die Formatierung des eingefügten Textes hat jedoch einige[ Einschränkungen](https://helpx.adobe.com/de/aem-forms/kb/cm-copy-paste-text-limitations.html).

## Einfügen von Sonderzeichen in Text {#special}

Fügen Sie bei Bedarf Sonderzeichen in das Dokumentfragment ein. Beispielsweise können Sie über die Sonderzeichenpalette die folgenden Zeichen einfügen:

* Währungssymbole wie €,￥ und £
* Mathematische Symbole wie ∑, √, ∂ und ^
* Satzzeichen wie „ und “

![specialcharacters-2](assets/specialcharacters-2.png)

Texteditor enthält integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann die [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen](/help/forms/using/custom-special-characters.md).

## Text suchen und ersetzen {#searching}

Bei der Arbeit mit Textdokumentfragmenten, die eine große Menge an Text enthalten, müssen Sie nach einer bestimmten Textzeichenfolge suchen. Möglicherweise müssen Sie auch eine bestimmte Textfolge durch eine alternative Zeichenfolge ersetzen.

Mithilfe der Funktion „Suchen und Ersetzen“ können Sie nach jeder beliebigen Textzeichenfolge in einem Textdokumentfragment suchen (und diese ersetzen). Die Funktion umfasst außerdem eine leistungsstarke Suche nach regulären Ausdrücken.

1. Öffnen Sie ein Textdokumentenfragment zur [Bearbeitung](#edittext).
1. Wählen Sie **[!UICONTROL Suchen und Ersetzen]** aus:

1. Geben Sie den zu suchenden Text in das Textfeld **[!UICONTROL Suchen]** und den neuen Text (Ersatztext) in das Textfeld **[!UICONTROL Ersetzen]** ein und wählen Sie **[!UICONTROL Ersetzen]**.

1. Wenn der zu suchende Text gefunden wird, wird der Text durch den Ersetzungstext ersetzt.

   * Wenn eine andere Instanz des gesuchten Textes gefunden wird, wird diese Instanz im Textdokumentfragment hervorgehoben. Wenn Sie **[!UICONTROL Ersetzen]** erneut auswählen, wird die hervorgehobene Instanz ersetzt und der Cursor bewegt sich weiter, falls eine dritte Instanz gefunden wird.
   * Wenn keine andere Instanz gefunden wird, wird im Dialogfeld „Suchen und Ersetzen“ folgende Meldung angezeigt: „Ende des Moduls wurde erreicht“.

   Sie können auch „Alle ersetzen“ auswählen, um alle Übereinstimmungen auf einmal zu ersetzen.

   Die Funktion „Suchen und Ersetzen“ umfasst außerdem eine leistungsstarke Suche nach regulären Ausdrücken (Regex). Um Regex in Ihrer Suche zu verwenden, wählen Sie **[!UICONTROL Regex]** und dann **[!UICONTROL Suchen]** bzw. **[!UICONTROL Ersetzen]** aus.
