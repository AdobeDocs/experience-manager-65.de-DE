---
title: Texte in interaktiver Kommunikation
description: Erstellen und Bearbeiten von Textdokumentfragmenten zur Verwendung in interaktiver Kommunikation - Text ist einer der vier Arten von Dokumentfragmenten, die zum Erstellen interaktiver Kommunikation verwendet werden. Die anderen drei sind Bedingungen, Listen und Layout-Fragmente.
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: b8e84c5d-2ec8-4575-9eed-6b37b04e5d66
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '2474'
ht-degree: 54%

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

   * **[!UICONTROL Titel]**: (Optional) Geben Sie den Titel für das Textdokumentfragment ein. Titel müssen nicht eindeutig sein und können Sonderzeichen und nichtenglische Zeichen enthalten. Texte werden durch ihren Titel (falls verfügbar) wie etwa in Miniaturen und Eigenschaften referenziert.
   * **[!UICONTROL Name]**: Der eindeutige Name des Texts, in einem Ordner. Es ist nicht möglich, dass zwei Dokumentfragmente (Text, Bedingung oder Liste) mit demselben Namen vorhanden sind, ungeachtet ihres jeweiligen Status. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.

   * **[!UICONTROL Beschreibung]**: Geben Sie eine Beschreibung des Textes ein.
   * **[!UICONTROL Formulardatenmodell]**: Wählen Sie optional das Optionsfeld Formulardatenmodell aus, um den Text basierend auf einem Formulardatenmodell zu erstellen. Wenn Sie das Optionsfeld „Formulardatenmodell“ auswählen, wird das Feld **[!UICONTROL Formulardatenmodell]** angezeigt. Suchen Sie nach einem Formulardatenmodell und wählen Sie es aus. Stellen Sie beim Erstellen von Text und Bedingungen für eine interaktive Kommunikation sicher, dass Sie dasselbe Datenmodell verwenden, das Sie in der interaktiven Kommunikation verwenden möchten. Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration](/help/forms/using/data-integration.md).

   * **[!UICONTROL Tags]**: Um optional einen benutzerdefinierten Tag zu erstellen, geben Sie einen Wert in das Textfeld ein und drücken Sie die Eingabetaste. Wenn Sie diesen Text speichern, werden die neu hinzugefügten Tags erstellt.

1. Wählen Sie **[!UICONTROL Weiter]** aus.

   Die Seite Text erstellen wird angezeigt. Wenn Sie sich dafür entschieden haben, einen auf einem Formulardatenmodell basierenden Text zu erstellen, werden die Eigenschaften des Formulardatenmodells im linken Bereich angezeigt.

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
1. Auswählen **[!UICONTROL Speichern]** und wählen Sie **[!UICONTROL Schließen]**.

## Personalisieren eines Textdokumentfragments mithilfe von Formulardatenmodelleigenschaften {#formdatamodel}

Sie können Textdokumentfragmente personalisieren, indem Sie die Eigenschaften des Formulardatenmodells einfügen. Wenn Sie die Eigenschaften der Formulardaten in Text einfügen, können Sie empfängerspezifische Daten aus der Datenquelle für die Vorschau einer interaktiven Kommunikation abrufen und befüllen. Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

Wenn Sie beim Erstellen eines Texts ein Formulardatenmodell angegeben haben, werden die Eigenschaften im Formulardatenmodell im linken Bereich des Texteditors angezeigt. Das angegebene Formulardatenmodell sollte für das Textdokumentfragment und die interaktive Kommunikation, die es enthält, identisch sein.

![insertfdmelementtext](assets/insertfdmelementtext.png)

* Um eine Formulardatenmodelleigenschaft in Text einzufügen, platzieren Sie den Cursor an die Stelle, an der Sie die Eigenschaft einfügen möchten, und wählen Sie dann die **[A]** Eigenschaft im linken Bereich durch Tippen darauf und wählen Sie **[!UICONTROL [B] Auswahl hinzufügen]**. Sie können die Eigenschaft auch einfach doppelt auswählen, um sie im **[C]** Cursorposition. Die Eigenschaften des Formulardatenmodells werden in einer bräunlichen Hintergrundfarbe hervorgehoben.

Alternativ können Sie die Eigenschaft des Formulardatenmodells mit dem @-Symbol im Texteditor suchen und hinzufügen. Platzieren Sie den Cursor an die Stelle, an der Sie die Eigenschaft einfügen möchten. Geben Sie @ ein, gefolgt von der Suchzeichenfolge. Der Suchvorgang wird für alle Eigenschaften und Variablen des Formulardatenmodells ausgeführt, die im Dokumentfragment verfügbar sind. Die Eigenschaften oder Variablen, die die Suchzeichenfolge enthalten, werden abgerufen und als Dropdown-Liste angezeigt. Navigieren Sie durch die Suchergebnisse und klicken Sie an der Position des Cursors auf die Eigenschaft, die Sie einfügen möchten. Drücken Sie Esc, um die Suchergebnisse auszublenden.

* So können die Agenten den Wert einer Formulardatenmodelleigenschaft in der Benutzeroberfläche für Agenten bearbeiten, während [Interaktive Kommunikation vorbereiten und senden](/help/forms/using/prepare-send-interactive-communication.md) Wählen Sie mithilfe der Benutzeroberfläche für Agenten die **[D]** Sperrsymbol für diese Eigenschaft und stellen Sie sicher, dass sie sich in einem entsperrten Status befindet. Der Standardstatus der Eigenschaft ist gesperrt und ein Agent kann die Eigenschaft in der Benutzeroberfläche für Agenten nicht bearbeiten.

Sie können auch Eigenschaften des Formulardatenmodells verwenden, um Regeln zum Anzeigen oder Ausblenden von Inhaltsbereichen zu erstellen. Weitere Informationen finden Sie unter [Erstellen von Regeln im Text](#rules).

## Erstellen und Verwenden von Variablen in einem Textdokumentfragment {#variables}

Variablen sind Platzhalter, die beim Erstellen einer interaktiven Kommunikation gebunden werden können. Variablen können an eine Formulardatenmodelleigenschaft oder ein Textfragment gebunden werden. Variablen können auch für den Agenten zum Ausfüllen übrig bleiben.

Sie können Variablen anstelle von Formulardatenmodelleigenschaften verwenden, wenn:

* Ein Textdokumentfragment wird in mehreren interaktiven Kommunikationen verwendet, wobei die Bindung für verschiedene interaktive Kommunikation unterschiedlich sein muss.
* Textdokumentfragmente verfügen zum Zeitpunkt ihrer Erstellung über kein Formulardatenmodell. Sie können Variablen einfügen und später zum Zeitpunkt der Erstellung der interaktiven Kommunikation an die Eigenschaften des Formulardatenmodells binden.
* Sie müssen Text aus einem Textdokumentfragment binden und abrufen. Nur diese Textdokumentfragmente können an Variablen gebunden werden, die keine Variablen enthalten dürfen.

Beim Erstellen oder Bearbeiten eines Textdokumentfragments können Sie Variablen erstellen und einfügen. Die von Ihnen erstellten Variablen werden auf der Registerkarte Daten der Benutzeroberfläche für Agenten angezeigt. Der Agent gibt die Werte für die Variablen an, während [Vorbereiten und Senden der interaktiven Kommunikation über die Benutzeroberfläche des Agenten](/help/forms/using/prepare-send-interactive-communication.md) läuft.

### Variablen erstellen {#createvariables}

1. Wählen Sie im linken Bereich die Option **[!UICONTROL Variablen]**.

   Der Variablenbereich wird angezeigt.

   ![variablespanel](assets/variablespane.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   Der Bereich Variablen erstellen wird angezeigt.

1. Geben Sie die folgenden Informationen ein und wählen Sie **[!UICONTROL Erstellen]**:

   * **[!UICONTROL Name]**: Name der Variablen.
   * **[!UICONTROL Beschreibung]**: Geben Sie optional eine Beschreibung der Variablen ein.
   * **[!UICONTROL Typ]**: Wählen Sie einen Typ der Variablen: Zeichenfolge, Zahl, Boolesch oder Datum.
   * **[!UICONTROL Nur bestimmte Werte zulassen]**: Bei Zeichenfolge- und Zahl-Variablen können Sie sicherstellen, dass der Agent aus einem bestimmten Satz von Werten für einen Platzhalter in der Agent-UI auswählt. Um den Wertesatz anzugeben, wählen Sie diese Option aus und geben Sie dann durch Komma getrennte Werte an, die im Feld **[!UICONTROL Werte]** zulässig sind.

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   Die Variable wird erstellt und im Bereich „Variablen“ aufgelistet.

1. Um eine Variable in den Text einzufügen, platzieren Sie den Cursor an der richtigen Stelle, wählen Sie die Variable aus und wählen Sie **[!UICONTROL Auswahl hinzufügen]**.

   ![variableinserted](assets/variableinserted.png)

   Variablen werden in hellblauer Hintergrundfarbe hervorgehoben, während Formulardatenmodelleigenschaften in einer bräunlichen Farbe hervorgehoben werden.

   Alternativ können Sie Variablen mithilfe des @-Symbols im Texteditor suchen und hinzufügen. Platzieren Sie den Cursor an die Stelle, an der die Variable eingefügt werden soll. Geben Sie @ ein, gefolgt von der Suchzeichenfolge. Der Suchvorgang wird für alle Eigenschaften und Variablen des Formulardatenmodells ausgeführt, die im Dokumentfragment verfügbar sind. Die Eigenschaften und Variablen, die den Suchbegriff enthalten, werden abgerufen und als Dropdown-Liste angezeigt. Navigieren Sie durch die Suchergebnisse und klicken Sie an der Cursorposition auf die Variable, die Sie einfügen möchten. Drücken Sie Esc, um die Suchergebnisse auszublenden.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

## Erstellen von Regeln im Text {#rules}

Mit dem Regeleditor in einem Text können Sie Regeln erstellen, um Textzeichenfolgen oder Inhaltselemente, die auf **voreingestellte Bedingungen**. Diese Bedingungen können wie folgt konfiguriert werden:

* Zeichenfolgen
* Zahlen
* Mathematischer Ausdruck
* Datumsangaben
* Eigenschaften des zugehörigen Formulardatenmodells
* Alle Variablen, die Sie möglicherweise im Text erstellt haben

### Erstellen von Regeln im Text {#create-rules-in-text}

1. Wählen Sie beim Erstellen oder Bearbeiten eines Textes die Textzeichenfolge, den Absatz oder den Inhalt aus, die bzw. den Sie mithilfe der Regel konditionalisieren möchten.

   ![selectcontentapplyrule](assets/selectcontentapplyrule.png)

1. Auswählen **[!UICONTROL Regel erstellen]**.

   Das Dialogfeld „Regel erstellen“ wird angezeigt. Zusätzlich zu Zeichenfolge, Zahl, mathematischem Ausdruck und Datum stehen im Regeleditor auch folgende Elemente zum Erstellen von Anweisungen der Regeln zur Verfügung:

   * Eigenschaften des zugehörigen Formulardatenmodells
   * Eventuell von Ihnen erstellte Variablen

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

   * Beim Erstellen oder Bearbeiten einer Regel können Sie auch ![icon_resize](assets/icon_resize.png) (Größe ändern), um das Dialogfeld Regel erstellen/Regel bearbeiten zu erweitern. Im erweiterten Vollbilddialogfeld können Sie Eigenschaften und Variablen des Formulardatenmodells per Drag-and-Drop verschieben, um Regeln zu erstellen. Wählen Sie erneut Größe ändern aus, um zum Dialogfeld Regel erstellen zurückzukehren.
   * Sie können auch mehrere Bedingungen in einer Regel erstellen.
   * Sie können auch überlappende Regeln erstellen, in denen eine Regel auf einen Teil eines Inhalts angewendet wird, auf den bereits eine Regel angewendet wurde.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

   Die Regel wird angewendet. Der Text oder Inhalt, auf den die Regel angewendet wird, wird grün hervorgehoben. Wenn Sie den Mauszeiger über den linken Ziehpunkt der Hervorhebung bewegen, wird die angewendete Regel angezeigt.

   ![appliedruletext](assets/appliedruletext.png)

   Wenn Sie auf den linken Handler der angewendeten Regel klicken, erhalten Sie die Optionen zum Bearbeiten oder Entfernen der Regel.

## Text formatieren {#formatting}

Beim Erstellen oder Bearbeiten von Text ändert sich die Symbolleiste je nach Art der Änderungen, die Sie vornehmen: Absatz, Ausrichtung oder Auflistung:

![Symbolleistentyp auswählen](do-not-localize/toolbarselection.png)

Wählen Sie den Typ der Symbolleiste aus: Absatz, Ausrichtung oder Auflistung

![Symbolleiste zum Bearbeiten der Schriftart](do-not-localize/paragraphtoolbar.png)

Symbolleiste zum Bearbeiten der Schriftart

![Ausrichtungs-Symbolleiste](assets/alignmenttoolbar.png)

Ausrichtungs-Symbolleiste

![Auflistungs-Symbolleiste](do-not-localize/listingtoolbar.png)

Auflistungs-Symbolleiste

### Teile von Text hervorheben/hervorheben {#highlight}

Um Textteile in einem bearbeitbaren Dokumentfragment hervorzuheben bzw. hervorzuheben, wählen Sie den Text aus und wählen Sie die Option Hervorhebungsfarbe aus.

![textbackgroundcolorapplied-1](assets/textbackgroundcolorapplied-1.png)

Sie können entweder eine Grundfarbe direkt auswählen `**[A]**` in der Palette &quot;Grundfarben&quot;angezeigt werden, oder wählen Sie **Auswählen** nach Verwendung des Reglers `**[B]**` , um die gewünschte Farbschattierung auszuwählen.

Optional können Sie auch auf der Registerkarte Erweitert die gewünschte Farbe, Helligkeit und Sättigung auswählen `**[C]**` , um die genaue Farbe zu erstellen, und wählen Sie dann Auswählen `**[D]**` , um die Farbe anzuwenden und den Text hervorzuheben.

![textbackgroundcolor-2](assets/textbackgroundcolor-2.png)

### Einfügen von formatiertem Text {#paste}

Um einen oder mehrere Textabsätze wiederzuverwenden, die in einer anderen Anwendung vorhanden sind, z. B. von Microsoft® Word- oder HTML-Seiten, kopieren Sie den Text und fügen Sie ihn in den Texteditor ein. Die Formatierung des kopierten Texts wird im Texteditor beibehalten.

Sie können einen oder mehrere Textabsätze in ein bearbeitbares Textdokumentfragment kopieren und einfügen. Sie können beispielsweise ein Microsoft® Word-Dokument mit einer Liste mit Aufzählungszeichen für zulässige Aufenthaltsnachweise wie folgt erstellen:

![pastetextmsword-2](assets/pastetextmsword-2.png)

Sie können den Text direkt aus dem Microsoft® Word-Dokument in ein bearbeitbares Textdokumentfragment kopieren und einfügen. Die Formatierung wie Liste mit Aufzählungszeichen, Schriftart und Textfarbe wird im Textdokumentfragment beibehalten.

![pastetexteditablemodule-1](assets/pastetexteditablemodule-1.png)

>[!NOTE]
>
>Die Formatierung des eingefügten Textes hat jedoch einige[ Einschränkungen](https://helpx.adobe.com/de/aem-forms/kb/cm-copy-paste-text-limitations.html).

## Sonderzeichen in Text einfügen {#special}

Fügen Sie bei Bedarf Sonderzeichen in das Dokumentfragment ein. Beispielsweise können Sie über die Sonderzeichenpalette die folgenden Zeichen einfügen:

* Währungssymbole wie €,￥ und £
* Mathematische Symbole wie ∑, √, ∂ und ^
* Satzzeichen wie „ und “

![specialcharacters-2](assets/specialcharacters-2.png)

Texteditor enthält integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann die [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen](/help/forms/using/custom-special-characters.md).

## Text suchen und ersetzen {#searching}

Bei der Arbeit mit Textdokumentfragmenten, die eine große Menge an Text enthalten, müssen Sie nach einer bestimmten Textzeichenfolge suchen. Möglicherweise müssen Sie auch eine bestimmte Textfolge durch eine alternative Zeichenfolge ersetzen.

Mit der Funktion &quot;Suchen und Ersetzen&quot;können Sie nach einer beliebigen Textzeichenfolge in einem Textdokumentfragment suchen (und diese ersetzen). Die Funktion umfasst außerdem eine leistungsstarke Suche nach regulären Ausdrücken.

1. Öffnen Sie ein Textdokumentenfragment zur [Bearbeitung](#edittext).
1. Auswählen **[!UICONTROL Suchen und Ersetzen]**.

1. Geben Sie den zu suchenden Text in die **[!UICONTROL Suchen]** und den neuen Text (Ersatztext) im **[!UICONTROL Ersetzen]** Textfeld und wählen Sie **[!UICONTROL Ersetzen]**.

1. Wenn der gesuchte Text gefunden wird, wird der Text durch den Ersatztext ersetzt.

   * Wenn eine andere Instanz des Suchtextes gefunden wird, wird diese Instanz im Textdokumentfragment hervorgehoben. Wenn Sie **[!UICONTROL Ersetzen]** erneut wird die hervorgehobene Instanz ersetzt und der Cursor bewegt sich weiter, wenn eine dritte Instanz gefunden wird.
   * Wenn keine andere Instanz gefunden wird, wird im Dialogfeld Suchen und Ersetzen eine Meldung angezeigt: Das Modulende erreicht.

   Sie können auch Alle ersetzen auswählen, um alle Übereinstimmungen in einem Schritt zu ersetzen.

   Die Funktion umfasst außerdem eine leistungsstarke Suche nach regulären Ausdrücken. Um Regex in Ihrer Suche zu verwenden, wählen Sie **[!UICONTROL Reg ex]** und wählen Sie **[!UICONTROL Suchen]** oder **[!UICONTROL Ersetzen]**.
