---
title: '„Tutorial: Erstellen von Dokumentfragmenten“'
description: Erstellen von Dokumentfragmenten für die interaktive Kommunikation
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: 81429735-cd52-4621-8dc2-10dd89df3052
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1653'
ht-degree: 100%

---

# Tutorial: Erstellen von Dokumentfragmenten{#tutorial-create-document-fragments}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Adobe empfiehlt, der Reihe chronologisch zu folgen, um den gesamten Anwendungsfall des Tutorials zu verstehen, auszuführen und praktisch zu erleben.

Dokumentfragmente sind wiederverwendbare Komponenten einer Korrespondenz, die zum Erstellen einer interaktiven Kommunikation verwendet werden. Es gibt Dokumentfragmente der folgenden Typen:

* Text: Ein Text-Asset ist eine Inhaltskomponente, die aus einem oder mehreren Textabsätzen besteht. Ein Absatz kann statisch oder dynamisch sein.
* Liste: Eine Liste ist eine Gruppe von Dokumentfragmenten, einschließlich Text, Listen, Bedingungen und Bildern.
* Bedingung: Mithilfe von Bedingungen können Sie festlegen, welche Inhalte in die interaktive Kommunikation aufgenommen werden, und zwar basierend auf den Daten, die vom Formulardatenmodell empfangen werden.

In diesem Tutorial werden Sie durch die einzelnen Schritte geführt, um mehrere Textdokumentfragmente zu erstellen, die auf der Anatomie im Abschnitt [Interaktive Kommunikation planen](/help/forms/using/planning-interactive-communications.md) basieren. Am Ende dieses Tutorials sollten Sie zu Folgendem in der Lage sein:

* Erstellen von Dokumentfragmenten
* Erstellen von Variablen
* Erstellen und Anwenden von Regeln

![text_document_fragments](assets/text_document_fragments.gif)

Im Folgenden finden Sie eine Liste der Dokumentfragmente, die in diesem Tutorial erstellt werden:

* [Rechnungsdetails](../../forms/using/create-document-fragments.md#step-create-bill-details-text-document-fragment)
* [Kundendetails](../../forms/using/create-document-fragments.md#step-create-customer-details-text-document-fragment)
* [Rechnungszusammenfassung](../../forms/using/create-document-fragments.md#step-create-bill-summary-text-document-fragment)
* [Zusammenfassung der Gebühren](../../forms/using/create-document-fragments.md#step-create-summary-of-charges-text-document-fragment)

Jedes Dokumentfragment enthält Felder mit statischem Text, Daten, die vom Formulardatenmodell empfangen wurden, und Daten, die über die Agentenbenutzeroberfläche eingegeben wurden. Alle diese Felder werden im Abschnitt [Interaktive Kommunikation planen](/help/forms/using/planning-interactive-communications.md) dargestellt.

Beim Erstellen von Dokumentfragmenten in diesem Tutorial werden Variablen für Felder erstellt, die Daten über die Agentenbenutzeroberfläche empfangen.

Verwenden Sie **FDM_Create_First_IC** wie im Abschnitt [Formulardatenmodell erstellen](../../forms/using/create-form-data-model0.md) beschrieben, als Formulardatenmodell, um in diesem Tutorial Dokumentfragmente zu erstellen.

## Schritt 1: Erstellen eines Textdokumentfragments für die Rechnungsdetails {#step-create-bill-details-text-document-fragment}

Das Dokumentfragment „Rechnungsdetails“ enthält die folgenden Felder:

| Feld | Datenquelle |
|---|---|
| Rechnungsnummer | Agent-Benutzeroberfläche |
| Rechnungszeitraum | Agent-Benutzeroberfläche |
| Rechnungsdatum | Agent-Benutzeroberfläche |
| Ihr Plan | Formulardatenmodell |

Gehen Sie wie folgt vor, um Variablen für Felder mit der Agentenbenutzeroberfläche als Datenquelle zu erstellen, statischen Text zu erstellen und Formulardatenmodellelemente im Dokumentfragment zu verwenden:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.

1. Wählen Sie **Erstellen** > **Text**.
1. Geben Sie die folgenden Daten an:

   1. Geben Sie **bill_details_first_ic** als Name im Feld **Titel** ein. Der Titel wird automatisch in das Feld **Name** eingetragen.

   1. Wählen Sie im Abschnitt **Datenmodell** die Option **Formulardatenmodell** aus.

   1. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell aus und wählen Sie dann **Auswählen**.

   1. Wählen Sie **Weiter** aus.

1. Wählen Sie im linken Bereich die Registerkarte **Variablen** und dann **Erstellen** aus.
1. Gehen Sie im Abschnitt **Variable erstellen** wie folgt vor:

   1. Geben Sie **Rechnungsnummer** als Namen der Variablen ein.
   1. Wählen Sie unter „Typ“ die Option **Zeichenfolge** aus.
   1. Wählen Sie **Erstellen** aus.

   ![Variable vom Typ „Zeichenfolge“ erstellen](assets/variable_create_string_new.png)

   Wiederholen Sie die Schritte 4 und 5, um die folgenden Variablen zu erstellen:

   * Rechnungszeitraum: Typ „Zeichenfolge“
   * Rechnungsdatum: Typ „Datum“

   ![Rechnungsdetails](assets/variable_bill_details_new.png)

1. Erstellen Sie über den rechten Bereich statischen Text für die folgenden Felder:

   * Rechnungsnummer
   * Rechnungszeitraum
   * Rechnungsdatum
   * Ihr Plan

   ![Statischer Text](assets/variable_bill_details_static_text_new.png)

1. Setzen Sie den Cursor neben das Feld **Rechnungsnr.** und doppelklicken Sie auf der Registerkarte **Variablen** im linken Fensterbereich auf die Variable **InvoiceNumber**.
1. Setzen Sie den Cursor neben das Feld **Rechnungszeitraum** und doppelklicken Sie auf die Variable **Billperiod**.
1. Setzen Sie den Cursor neben das Feld **Rechnungsdatum** und doppelklicken Sie auf die Variable **Bill Date**.
1. Wählen Sie die Registerkarte **Datenmodellobjekte** im linken Fensterbereich aus.
1. Setzen Sie den Cursor neben das Feld **Ihr Plan** und doppelklicken Sie auf die Eigenschaft **Kunde** > **Kundenplan**.

   ![bill_details_customerplan_fdm](assets/bill_details_customerplan_fdm.png)

1. Klicken Sie auf **Speichern**, um das Textdokumentfragment „Rechnungsdetails“ zu erstellen.

## Schritt 2: Erstellen eines Textdokumentfragments für die Kundendetails {#step-create-customer-details-text-document-fragment}

Das Dokumentfragment „Kundendetails“ enthält die folgenden Felder:

| Feld | Datenquelle |
|---|---|
| Kundenname | Formulardatenmodell |
| Adresse | Formulardatenmodell |
| Ort der Lieferung | Agent-Benutzeroberfläche |
| Statuscode | Agent-Benutzeroberfläche |
| Mobilfunknummer | Formulardatenmodell |
| Alternative Kontaktnummer | Formulardatenmodell |
| Beziehungsnummer | Formulardatenmodell |
| Anzahl von Verbindungen | Agent-Benutzeroberfläche |

Gehen Sie wie folgt vor, um Variablen für Felder mit der Agentenbenutzeroberfläche als Datenquelle zu erstellen, statischen Text zu erstellen und Formulardatenmodellelemente im Dokumentfragment zu verwenden:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **Erstellen** > **Text**.
1. Geben Sie die folgenden Daten an:

   1. Geben Sie **customer_details_first_ic** als Name im Feld **Titel** ein. Der Titel wird automatisch in das Feld **Name** eingetragen.

   1. Wählen Sie im Abschnitt **Datenmodell** die Option **Formulardatenmodell** aus.

   1. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell aus und wählen Sie dann **Auswählen**.

   1. Wählen Sie **Weiter** aus.

1. Wählen Sie im linken Bereich die Registerkarte **Variablen** und dann **Erstellen** aus.
1. Gehen Sie im Abschnitt **Variable erstellen** wie folgt vor:

   1. Geben Sie als Name der Variablen **Placesupply** ein.
   1. Wählen Sie unter „Typ“ die Option **Zeichenfolge** aus.
   1. Wählen Sie **Erstellen** aus.

   Wiederholen Sie die Schritte 4 und 5, um die folgenden Variablen zu erstellen:

   * Statuscode: Typ „Zahl“
   * Anzahlverbindungen: Typ „Zahl“

1. Wählen Sie im linken Fensterbereich die Registerkarte **Datenmodellobjekte** aus, bewegen Sie den Cursor in den rechten Fensterbereich und doppelklicken Sie auf die Eigenschaft **Kunde** > **Name**.
1. Drücken Sie die Eingabetaste, um den Cursor in die nächste Zeile zu bewegen, und doppelklicken Sie auf die Eigenschaft **Kunde** > **Adresse**.
1. Erstellen Sie über den rechten Bereich statischen Text für die folgenden Felder:

   * Mobilfunknummer
   * Alternative Kontaktnummer
   * Ort der Lieferung
   * Beziehungsnummer
   * Statuscode
   * Anzahl von Verbindungen

   ![Statischer Text für Kundendetails](assets/customer_details_static_text_new.png)

1. Setzen Sie den Cursor neben das Feld **Mobilfunknummer** und doppelklicken Sie auf die Eigenschaft **Kunde** > **mobilenum**.
1. Setzen Sie den Cursor neben das Feld **Alternative Kontaktnummer** und doppelklicken Sie auf die Eigenschaft **Kunde** > **alternatemobilenumber**.
1. Setzen Sie den Cursor neben das Feld **Verhältnis-Nummer** und doppelklicken Sie auf die Eigenschaft **Kunde** > **relationshipnumber**.
1. Wählen Sie die Registerkarte **Variablen** und setzen Sie den Cursor neben dem Feld **Ort der Lieferung** und doppelklicken Sie auf die Variable **Placesupply**.
1. Setzen Sie den Cursor neben das Feld **Status-Code** und doppelklicken Sie auf die Variable **Statecode**.
1. Setzen Sie den Cursor neben das Feld **Anzahl der Verbindungen** und doppelklicken Sie auf die Variable **Numberconnections**.

   ![Kundendetails](assets/customer_details_df2_new.png)

1. Klicken Sie auf **Speichern**, um das Textdokumentfragment „Kundendetails“ zu erstellen.

## Schritt 3: Erstellen eines Textdokumentfragments für die Rechnungsübersicht {#step-create-bill-summary-text-document-fragment}

Das Dokumentfragment „Rechnungsübersicht“ enthält die folgenden Felder:

| Feld | Datenquelle |
|---|---|
| Vorheriger Saldo | Agent-Benutzeroberfläche |
| Zahlungen | Agent-Benutzeroberfläche |
| Anpassungen | Agent-Benutzeroberfläche |
| Gebühren des aktuellen Rechnungszeitraums | Formulardatenmodell |
| Fälliger Betrag | Agent-Benutzeroberfläche |
| Fälligkeitsdatum | Agent-Benutzeroberfläche |

Gehen Sie wie folgt vor, um Variablen für Felder mit der Agentenbenutzeroberfläche als Datenquelle zu erstellen, statischen Text zu erstellen und Formulardatenmodellelemente im Dokumentfragment zu verwenden:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **Erstellen** > **Text**.
1. Geben Sie die folgenden Daten an:

   1. Geben Sie **bill_summary_first_ic** als Name in das Feld **Titel** ein. Der Titel wird automatisch in das Feld **Name** eingetragen.

   1. Wählen Sie im Abschnitt **Datenmodell** die Option **Formulardatenmodell** aus.

   1. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell aus und wählen Sie dann **Auswählen**.

   1. Wählen Sie **Weiter** aus.

1. Wählen Sie im linken Bereich die Registerkarte **Variablen** und dann **Erstellen** aus.
1. Gehen Sie im Abschnitt **Variable erstellen** wie folgt vor:

   1. Geben Sie als Name der Variablen **Previousbalance** ein.
   1. Wählen Sie als Typ **Zahl**.
   1. Wählen Sie **Erstellen** aus.

   Wiederholen Sie die Schritte 4 und 5, um die folgenden Variablen zu erstellen:

   * Zahlungen: Typ „Zahl“
   * Anpassungen: Typ „Zahl“
   * Fälligerbetrag: Typ „Zahl“
   * Fälligkeitsdatum: Typ „Datum“

1. Erstellen Sie über den rechten Bereich statischen Text für die folgenden Felder:

   * Vorheriger Saldo
   * Zahlungen
   * Anpassungen
   * Gebühren des aktuellen Rechnungszeitraums
   * Fälliger Betrag
   * Fälligkeitsdatum
   * Gebühren für verspätete Zahlungen nach Fälligkeitsdatum betragen $ 20

   ![Statistischer Text zur Rechnungszusammenfassung](assets/bill_summary_static_new.png)

1. Setzen Sie den Cursor neben das Feld **Vorheriger Saldo** und doppelklicken Sie auf die Variable **Previousbalance**.
1. Setzen Sie den Cursor neben das Feld **Zahlungen** und doppelklicken Sie auf die Variable **Payments**.
1. Setzen Sie den Cursor neben das Feld **Anpassungen** und doppelklicken Sie auf die Variable **Adjustments**.
1. Setzen Sie den Cursor neben das Feld **Fälliger Betrag** und doppelklicken Sie auf die Variable **Amountdue**.
1. Setzen Sie den Cursor neben das Feld **Fälligkeitsdatum** und doppelklicken Sie auf die Variable **Duedate**.
1. Wählen Sie die Registerkarte **Datenmodellobjekte** im linken Bereich, platzieren Sie den Cursor in den rechten Bereich neben dem Feld **Gebühren für aktuelle Rechnungsperiode** und doppelklicken Sie auf die Eigenschaft **bills** > **usagecharges**.

   ![Rechnungszusammenfassung](assets/bill_summary_static_variables_new.png)

1. Klicken Sie auf **Speichern**, um das Textdokumentfragment „Kundendetails“ zu erstellen.

## Schritt 4: Erstellen eines Textdokumentfragments für die Gebührenübersicht {#step-create-summary-of-charges-text-document-fragment}

Das Dokumentfragment „Gebührenübersicht“ enthält die folgenden Felder:

| Feld | Datenquelle |
|---|---|
| Anrufgebühren | Formulardatenmodell |
| Gebühren für Telefonkonferenz | Formulardatenmodell |
| SMS-Gebühren | Formulardatenmodell |
| Mobile Internetgebühren | Formulardatenmodell |
| Nationale Roaming-Gebühren | Formulardatenmodell |
| Internationale Roaming-Gebühren | Formulardatenmodell |
| Mehrwert-Service-Gebühren | Formulardatenmodell |
| Gesamtgebühren | Formulardatenmodell |
| GESAMT ZAHLBAR | Formulardatenmodell |

Gehen Sie wie folgt vor, um statischen Text zu erstellen und Formulardatenmodellelemente im Dokumentfragment zu verwenden:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **Erstellen** > **Text**.
1. Geben Sie die folgenden Daten an:

   1. Geben Sie **summary_charges_first_ic** als Name im Feld **Titel** ein. Der Titel wird automatisch in das Feld „Name“ eingetragen.

   1. Wählen Sie im Abschnitt **Datenmodell** die Option **Formulardatenmodell** aus.

   1. Wählen Sie **FDM_Create_First_IC** als Formulardatenmodell aus und wählen Sie dann **Auswählen**.

   1. Wählen Sie **Weiter** aus.

1. Erstellen Sie über den rechten Bereich statischen Text für die folgenden Felder:

   * Anrufgebühren
   * Gebühren für Telefonkonferenz
   * SMS-Gebühren
   * Mobile Internetgebühren
   * Nationale Roaming-Gebühren
   * Internationale Roaming-Gebühren
   * Mehrwert-Service-Gebühren
   * Gesamtgebühren
   * GESAMT ZAHLBAR

   ![Zusammenfassungsgebühren](assets/summary_charges_static_new.png)

1. Wählen Sie die Registerkarte **Datenmodellobjekte**.
1. Setzen Sie den Cursor neben das Feld **Anrufgebühren** und doppelklicken Sie auf die Eigenschaft **bills** > **callcharges**.
1. Setzen Sie den Cursor neben das Feld **Konferenzanrufgebühren** und doppelklicken Sie auf die Eigenschaft **bills** > **confcallcharges**.
1. Setzen Sie den Cursor neben das Feld **SMS-Gebühren** und doppelklicken Sie auf die Eigenschaft **bills** > **smscharges**.
1. Setzen Sie den Cursor neben das Feld **Mobile Internetgebühren** und doppelklicken Sie auf die Eigenschaft **bills** > **internetcharges**.
1. Setzen Sie den Cursor neben das Feld **Nationale Roaming-Gebühren** und doppelklicken Sie auf die Eigenschaft **bills** > **roamingnational**.
1. Setzen Sie den Cursor neben das Feld **Internationale Roaming-Gebühren** und doppelklicken Sie auf die Eigenschaft **bills** > **roamingintnl**.
1. Setzen Sie den Cursor neben das Feld **Mehrwert - Service-Gebühren** und doppelklicken Sie auf die Eigenschaft **bills** > **vas**.
1. Setzen Sie den Cursor neben das Feld **Gebühren insgesamt** und doppelklicken Sie auf die Eigenschaft **bills** > **usagecharges**.
1. Setzen Sie den Cursor neben das Feld **GESAMT ZAHLBAR** und doppelklicken Sie auf die Eigenschaft **bills** > **usagecharges**. 

   ![Zusammenfassung der Gebühren](assets/summary_charges_static_fdm_new.png)

1. Wählen Sie den Text in der Zeile **Mehrwert-Service-Gebühren** und dann **Regel erstellen** aus, um eine Bedingung zu erstellen, auf deren Grundlage die Zeile in der interaktiven Kommunikation angezeigt wird:
1. Gehen Sie im Popup-Fenster **Regel erstellen** wie folgt vor:

   1. Wählen Sie **Datenmodelle und Variablen** aus und dann **Rechnungen** > **Anrufgebühren**.

   1. Wählen Sie den Operator **ist kleiner als** aus.
   1. Wählen Sie **Zahl** aus und geben Sie als Wert **60** ein.

   Basierend auf dieser Bedingung wird die Zeile „Mehrwert-Service-Gebühren“ nur angezeigt, wenn der Wert für das Feld „Anrufgebühren“ unter 60 liegt.

   ![create_rules_caption](assets/create_rules_caption.gif)

1. Klicken Sie auf **Speichern**, um das Textdokumentfragment „Gebührenübersicht“ zu erstellen.
