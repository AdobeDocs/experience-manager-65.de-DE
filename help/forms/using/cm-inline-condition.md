---
title: Inline-Bedingung und Wiederholung in der interaktiven Kommunikation und in Briefen
description: Mithilfe von Inline-Bedingungen und Wiederholungen in interaktiven Kommunikationen und Briefen können Sie Nachrichten erstellen, die sehr kontextbezogen und gut strukturiert sind.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: interactive-communications, correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: bc5d6c5b-c833-4849-aace-e07f8a522b32
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1660'
ht-degree: 100%

---

# Inline-Bedingung und Wiederholung in der interaktiven Kommunikation und in Briefen{#inline-condition-and-repeat-in-interactive-communications-and-letters}

## Inline-Bedingungen {#inline-conditions}

Mit AEM Forms können Sie Inline-Bedingungen in Textmodulen verwenden, um das Rendern von Text zu automatisieren, der vom Kontext oder den Daten abhängt, die mit dem Formulardatenmodell (in der interaktiven Kommunikation) oder dem Datenwörterbuch (in Briefen) verknüpft sind. Die Inline-Bedingung zeigt bestimmte Inhalte basierend darauf an, ob die Auswertung der Bedingung „true“ oder „false“ ergibt.

Bedingungen führen Berechnungen zu Datenwerten durch, die vom Formulardatenmodell/Datenwörterbuch oder von Endbenutzenden bereitgestellt werden. Durch die Verwendung von Inline-Bedingungen können Sie Zeit sparen und menschliche Fehler reduzieren und gleichzeitig interaktive Kommunikationen und Briefe erstellen, die stark kontextbezogen und personalisiert sind.

Weitere Informationen finden Sie unter:

* [Erstellen einer interaktiven Kommunikation](../../forms/using/create-interactive-communication.md)
* [Correspondence Management – Zusammenfassung](/help/forms/using/cm-overview.md)
* [Text in interaktiven Kommunikationen](../../forms/using/texts-interactive-communications.md)

### Beispiel: Verwenden von Regeln zum Konditionieren von Inline-Text in der interaktiven Kommunikation {#example-using-rules-to-conditionalize-inline-text-in-interactive-communication}

Um einen Satz, einen Absatz oder eine Zeichenfolge von Text in einer interaktiven Kommunikation mit Bedingungen zu versehen, können Sie eine Regel im entsprechenden Textdokumentfragment erstellen. Im folgenden Beispiel wird eine Regel verwendet, um nur den US-Empfängerinnen und -Empfängern der interaktiven Kommunikation eine gebührenfreie US-Nummer anzuzeigen.

Weitere Informationen finden Sie unter „Regel im Text erstellen“ in [Texte in interaktiven Kommunikationen](../../forms/using/texts-interactive-communications.md).

Sobald Sie das Textfragment in eine interaktive Kommunikation eingefügt haben und der Agent die Benutzeroberfläche des Agenten verwendet, um eine interaktive Kommunikation vorzubereiten, werden die Daten des Formulardatenmodells für die Empfänger ausgewertet, und der Text wird nur für Empfänger in den USA angezeigt.

### Beispiel: Verwenden der Inline-Bedingung in einem Brief zum Rendern der entsprechenden Adresse  {#example-using-inline-condition-in-a-letter-to-render-the-appropriate-address}

Sie können eine Inline-Bedingung in einen Brief einfügen, indem Sie die Inline-Bedingung in das entsprechende Textmodul einfügen. Im folgenden Beispiel werden zwei Bedingungen verwendet, um die entsprechende Anrede, Herr oder Frau, in einem Brief anzuzeigen, der auf dem DD-Element „Geschlecht“ basiert. Mit ähnlichen Schritten können Sie weitere Bedingungen erstellen.

>[!NOTE]
>
>Wenn Ihre vorhandenen Assets alte Bedingungs-/Wiederholungsausdrücke einbeziehen (vor 6.2 SP1 CFP 4), zeigen die Assets die alte Syntax der Bedingung und Wiederholung an. Allerdings funktioniert die Bedingung oder Wiederholung. Die neuen und alten Bedingungs- oder Wiederholungsausdrücke sind miteinander kompatibel, um eine verschachtelte Mischung aus alten und neuen Bedingungs-/Wiederholungsausdrücken erstellen zu können.

1. Wählen Sie im entsprechenden Textmodul den Textteil aus, für den Sie Bedingungen festlegen möchten, und wählen Sie dann **Bedingung** aus.

   ![1_selecttext](assets/1_selecttext.png)

   Das Dialogfeld „Bedingung“ wird mit einer leeren Bedingung angezeigt.

   ![2_condition_dialog](assets/2_conditiondialog.png)

   >[!NOTE]
   >
   >Leerer oder ungültiger Bedingungsausdruck kann nicht gespeichert werden. Damit der Ausdruck gespeichert werden kann, muss `${}` einen gültigen Bedingungsausdruck enthalten.

1. Führen Sie die folgenden Schritte aus, um eine Bedingung zum Auswerten zu erstellen, ob der ausgewählte/bedingte Text im Brief angezeigt wird. Wählen Sie anschließend das Häkchen aus, um den Ausdruck zu speichern:

   Doppeltippen Sie auf ein DD-Element, um es in die Bedingung einzufügen. Fügen Sie den entsprechenden Operator ein und erstellen Sie die folgende Bedingung im Dialogfeld.

   ```javascript
   ${DD_creditcard_Gender=="Male"}
   ```

   Weitere Informationen zum Erstellen eines Ausdrucks finden Sie unter **Erstellen von Ausdrücken und Remote-Funktionen mit dem Ausdrucksgenerator** im [Ausdrucksgenerator](../../forms/using/expression-builder.md). Der im Ausdruck angegebene Wert muss für das Element im Datenwörterbuch unterstützt werden. Weitere Informationen finden Sie unter [Datenwörterbuch](../../forms/using/data-dictionary.md).

   Sobald die Bedingung eingefügt wurde, können Sie den Mauszeiger über den Griff auf der linken Seite der Bedingung bewegen, um die Bedingung anzuzeigen. Sie können den Griff auswählen, um das Popup-Menü der Bedingung anzuzeigen, das es Ihnen ermöglicht, die Bedingung zu bearbeiten oder zu entfernen.

   ![3_hoverhandle](assets/3_hoverhandle.png) ![4_editcondition_removeconditionpopup](assets/4_editconditionremoveconditionpopup.png)

1. Fügen Sie ähnliche Bedingungen ein, indem Sie den Text `Ma'am` auswählen.

   ```javascript
   ${DD_creditcard_Gender == "Female"}
   ```

1. Zeigen Sie eine Vorschau des relevanten Briefs an und beachten Sie, dass der Text gemäß der Inline-Bedingung gerendert wird. Sie können den Wert des DD-Elements „Geschlecht“ wie folgt eingeben:

   * Eine Musterdatei für XML-Daten, die basierend auf dem relevanten Datenwörterbuch erstellt wurde, während der Brief mit Beispieldaten in der Vorschau angezeigt wird.
   * Eine XML-Datendatei, die an das relevante Datenwörterbuch angehängt ist.

   Weitere Informationen finden Sie unter [Datenwörterbuch](../../forms/using/data-dictionary.md).

   ![5_letteroutput](assets/5_letteroutput.png)

## Wiederholen {#repeat}

Sie haben möglicherweise dynamische Daten in Ihren interaktiven Kommunikationen/Briefen, z. B. Transaktionen in einem Kreditkartenauszug, in der Instanz oder Vorkommen, die sich mit jedem erstellten Brief ändern können. Mit der Wiederholungsfunktion können Sie solche dynamische Daten in Ihrem Textdokumentenfragment formatieren und strukturieren.

Außerdem können Sie eine Regel/Bedingung innerhalb des Wiederholungskonstrukts angeben, um die Daten/Einträge mit einer Bedingung zu versehen, die in der interaktiven Kommunikation/im Brief gerendert werden.

### Beispiel: Verwenden der Wiederholungsfunktion in einem Brief, um eine Liste von Kreditkartentransaktionen zu formatieren, strukturieren und anzuzeigen {#example-using-repeat-in-an-interactive-communication-to-format-structure-and-display-a-list-of-credit-card-transactions}

Das folgende Beispiel zeigt die Schritte für die Verwendung der Wiederholungsfunktion, um die Kreditkartentransaktionen in einer interaktiven Kommunikation zu strukturieren und zu rendern.

1. Fügen Sie in ein auf einem Formulardatenmodell basierendes Textdokumentfragment die relevanten Objekte des Formulardatenmodells (und den eingebetteten Text, der für die Beschriftungen erforderlich ist, wie in diesem Beispiel) ein:

   ![1_elementstext](assets/1_elementstext.png)

   >[!NOTE]
   >
   >Der wiederholbare Inhalt muss mindestens eine Eigenschaft des Typs „Sammlung“ enthalten.

1. Wählen Sie den Inhalt aus, auf den die Wiederholung angewendet werden soll.

   ![2_selection](assets/2_selection.png)

1. Wählen Sie „Wiederholen“ aus.

   Das Dialogfeld „Wiederholung“ wird angezeigt.

   ![3_repeatdialog](assets/3_repeatdialog.png)

1. Wählen Sie „Zeilenumbruch“ als Trennzeichen und bei Bedarf „Bedingung hinzufügen“ aus, um eine Regel zu erstellen. Sie können auch Text als Trennzeichen verwenden und die Textzeichen angeben, die als Trennzeichen verwendet werden sollen.

   Das Dialogfeld „Regel erstellen“ wird angezeigt. 

1. Erstellen Sie eine Regel, um die Transaktionen anzuzeigen, die nach dem 28. Februar 2018 datiert sind, damit nur die Transaktionen für den Monat März in die interaktive Kommunikation einbezogen werden.

   >[!NOTE]
   >
   >In diesem Beispiel wird davon ausgegangen, dass der Agent die Anweisung Ende März 2018 erstellt. Andernfalls können Sie eine andere Regel erstellen, um Transaktionen vor dem 01.04.2018 einzubeziehen, damit Transaktionen nach März 2018 ausgeschlossen werden.

   ![4_createrule](assets/4_createrule.png)

1. Speichern Sie die Bedingung/Regel und speichern Sie dann die Wiederholung. Die bedingte Wiederholung wird auf den ausgewählten Inhalt angewendet.

   ![5_onmouseoverconditionrule](assets/5_onmouseoverconditionrule.png)

   Wenn Sie die Maus darüber bewegen, zeigt das Textdokumentfragment die Bedingung und das Trennzeichen an, die in der auf den Inhalt angewendeten Wiederholung verwendet wurden.

1. Speichern Sie das Textdokumentfragment und zeigen Sie eine Vorschau der relevanten interaktiven Kommunikation an. Abhängig von den Daten im Formulardatenmodell werden die Transaktionsdetails durch die Wiederholung, die auf die Elemente angewendet wird, ähnlich wie in der folgenden Vorschau dargestellt:

   ![screen_shot_2018-03-09at155516copy](assets/screen_shot_2018-03-09at155516copy.png)

### Beispiel: Verwenden der Wiederholungsfunktion in einem Brief, um eine Liste von Kreditkartentransaktionen zu formatieren, zu strukturieren und anzuzeigen {#example-using-repeat-in-a-letter-to-format-structure-and-display-a-list-of-credit-card-transactions}

Das folgende Beispiel zeigt die Schritte für die Verwendung der Wiederholungsfunktion, um die Kreditkartentransaktionen in einem Brief zu strukturieren und zu rendern. Mit ähnlichen Schritten können Sie die Wiederholungsfunktion in einem anderen Szenario verwenden.

1. Öffnen Sie (beim Bearbeiten oder Erstellen) ein Textmodul mit DD-Elementen, die wiederholte/dynamische Daten rendern und den erforderlichen Text um die DD-Elemente einbetten. Beispielsweise verfügt ein Textmodul über die folgenden DD-Elemente, um eine Umsatzabrechnung für eine Kreditkarte zu erstellen:

   ```javascript
   {^DD_creditcard_TransactionDate^} {^DD_creditcard_TransactionAmount^}
   {^DD_creditcard_TransactionType^}
   ```

   Diese DD-Elemente rendern eine Liste der Transaktionen, die auf der Kreditkarte vorgenommen wurden, mit den folgenden Informationen:

   Transaktionsdatum, Transaktionsbetrag und Transaktionstyp (Debit oder Kredit)

1. Betten Sie den Text in die DD-Elemente ein, um die Anweisung lesbarer zu machen, z. B.:

   ![1_repeat](assets/1_repeat.png)

   ```javascript
   Date: {^DD_creditcard_TransactionDate^} Amount (USD): {^DD_creditcard_TransactionAmount^} Transaction Type: {^DD_creditcard_TransactionType^}
   ```

   Das Rendern einer gut formatierten Umsatzabrechnung ist jedoch noch nicht abgeschlossen. Wenn Sie einen Brief basierend auf der bisher durchgeführten Arbeit rendern, wird er wie folgt angezeigt:

   ![1_1renderwithoutrepeat](assets/1_1renderwithoutrepeat.png)

   Um den statischen Text zusammen mit den DD-Elementen zu wiederholen, müssen Sie eine Wiederholungsfunktion anwenden, wie in den weiteren Schritten beschrieben.

1. Wählen Sie den statischen Text und die DD-Elemente, die Sie wiederholen möchten, wie unten gezeigt:

   ![2_repeat_selecttext](assets/2_repeat_selecttext.png)

1. Wählen Sie **Wiederholen** aus. Das Dialogfeld „Wiederholung“ wird mit einer leeren Inline-Bedingung angezeigt.

   ![3_repeat_dialog](assets/3_repeat_dialog.png)

1. Falls erforderlich, fügen Sie eine Bedingung ein, um Transaktionen selektiv zu rendern, zum Beispiel um Transaktionsbeträge größer als 50 Cent zu rendern:

   ```javascript
   ${DD_creditcard_TransactionAmount > 0.5}
   ```

   Andernfalls, wenn Sie die Informationen (hier Transaktionen) nicht selektiv rendern müssen, lassen Sie die Bedingung leer, indem Sie im Dialogfeld Folgendes löschen: `${}`. Das Speichern eines Wiederholungsausdrucks wird aktiviert, wenn das Fenster für den Wiederholungsausdruck leer ist (ohne ${}, wenn keine Wiederholung erforderlich ist) oder wenn es eine gültige Bedingung für die Wiederholung enthält.

1. Wählen Sie ein Trennzeichen zur Formatierung von dynamischem Text aus und wählen Sie zum Speichern das Häkchen aus:

   * **Zeilenumbruch**: Fügt nach jedem Transaktionseintrag im Ausgabebrief einen Zeilenumbruch ein.
   * **Text**: Fügt das angegebene Textzeichen nach jedem Transaktionseintrag im Ausgabebrief ein.

   Sobald die Bedingung eingefügt wurde, wird der Text mit Wiederholung rot hervorgehoben und links wird ein Ziehpunkt angezeigt. Sie können den Mauszeiger über den Griff auf der linken Seite der Wiederholung bewegen, um das Wiederholungskonstrukt anzuzeigen.

   ![4_repeat_hoverdetail](assets/4_repeat_hoverdetail.png)

   Sie können den Griff auswählen, um das Popup-Menü der Wiederholung anzuzeigen, das es Ihnen ermöglicht, das Wiederholungskonstrukt zu bearbeiten oder zu entfernen.

   ![5_repeateditremove](assets/5_repeateditremove.png)

1. Sehen Sie sich den relevanten Brief in der Vorschau an und beachten Sie, dass der Text der Wiederholung entsprechend gerendert wird. Sie können den Wert von DD-Elementen wie folgt eingeben:

   * Eine Musterdatei für XML-Daten, die basierend auf dem relevanten Datenwörterbuch erstellt wurde, während der Brief mit Beispieldaten in der Vorschau angezeigt wird.
   * Eine XML-Datendatei, die an das relevante Datenwörterbuch angehängt ist.

   Weitere Informationen finden Sie unter [Datenwörterbuch](https://helpx.adobe.com/de/aem-forms/6-2/data-dictionary.html).

   ![6_repeatoutputpreview](assets/6_repeatoutputpreview.png)

   Die statischen Textwiederholungen mit den Transaktionsdetails. Das Wiederholen von statischem Text wird durch die Wiederholung, die auf den Text in diesem Prozess angewendet wird, erleichtert. Die Bedingung ${DD_creditcard_TransactionAmount > 0.5} stellt sicher, dass die Transaktionen unter 0,5 USD im Brief nicht gerendert werden.

   >[!NOTE]
   >
   >Sie können Bedingungen einfügen und nur wiederholen, während Sie das jeweilige Textmodul erstellen oder bearbeiten. Bei der Vorschau des Briefs können Sie zwar Änderungen am Textmodul vornehmen, jedoch keine Bedingung oder Wiederholung einfügen.

## Verwenden von Inline-Bedingung und Wiederholung – einige Anwendungsfälle  {#using-inline-condition-and-repeat-some-use-cases}

### Wiederholen innerhalb der Bedingung {#repeat-within-condition}

Unter Umständen müssen Sie die Wiederholung innerhalb einer Bedingung verwenden. Mit dem Correspondence Management können Sie die Wiederholung innerhalb eines Inline-Bedingungskonstrukts verwenden.

Folgendes ist beispielsweise eine Wiederholung (rot formatiert) innerhalb einer Bedingung (grün formatiert).

Während die Wiederholung die Kreditkartentransaktionen rendert, stellt die Bedingung ${DD_creditcard_nooftransactions > 0} sicher, dass das Wiederholungskonstrukt nur dann wiedergegeben wird, wenn es mindestens eine Transaktion gibt.

![repeatwitincondition](assets/repeatwitincondition.png)

Entsprechend Ihren Anforderungen können Sie Folgendes erstellen:

* Eine oder mehrere Bedingungen innerhalb einer Bedingung
* Eine oder mehrere Bedingungen innerhalb einer Wiederholung
* Kombination von Bedingungen und Wiederholung innerhalb einer Bedingung oder Wiederholung

### Leere Inline-Bedingung {#empty-inline-condition}

Möglicherweise müssen Sie später leere Inline-Bedingungen einfügen und Text und DD-Elemente einbetten. Das Correspondence Management ermöglicht Ihnen dies.

![emptycondition](assets/emptycondition.png)

Es wird jedoch empfohlen, dass Sie, wenn möglich, den Text und die DD-Elemente zuerst in das Textmodul mit der beabsichtigten Formatierung einfügen, wie Aufzählungspunkte, und danach eine Inline-Bedingung anwenden.
