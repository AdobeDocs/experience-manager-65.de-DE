---
title: '„Tutorial: Erstellen von Dokumentfragmenten“'
description: Erstellen von Dokumentfragmenten für die interaktive Kommunikation
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: 81429735-cd52-4621-8dc2-10dd89df3052
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '1674'
ht-degree: 56%

---

# Tutorial: Erstellen von Dokumentfragmenten{#tutorial-create-document-fragments}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Adobe empfiehlt, dass Sie der Reihe in chronologischer Abfolge folgen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, auszuführen und zu demonstrieren.

Dokumentfragmente sind wiederverwendbare Komponenten einer Korrespondenz, die zum Erstellen einer interaktiven Kommunikation verwendet werden. Es gibt Dokumentfragmente der folgenden Typen:

* Text: Ein Text-Asset ist eine Inhaltskomponente, die aus einem oder mehreren Textabsätzen besteht. Ein Absatz kann statisch oder dynamisch sein.
* Liste: Eine Liste ist eine Gruppe von Dokumentfragmenten, einschließlich Text, Listen, Bedingungen und Bildern.
* Bedingung: Mithilfe von Bedingungen können Sie festlegen, welche Inhalte in die interaktive Kommunikation aufgenommen werden, und zwar basierend auf den Daten, die vom Formulardatenmodell empfangen werden.

In diesem Tutorial werden Sie durch die einzelnen Schritte geführt, um mehrere Textdokumentfragmente zu erstellen, die auf der Anatomie im Abschnitt [Interaktive Kommunikation planen](/help/forms/using/planning-interactive-communications.md) basieren. Am Ende dieses Tutorials sollten Sie Folgendes tun können:

* Dokumentfragmente erstellen
* Erstellen von Variablen
* Regeln erstellen und anwenden

![text_document_fragments](assets/text_document_fragments.gif)

Im Folgenden finden Sie eine Liste der Dokumentfragmente, die in diesem Tutorial erstellt werden:

* [Rechnungsdetails](../../forms/using/create-document-fragments.md#step-create-bill-details-text-document-fragment)
* [Kundendetails](../../forms/using/create-document-fragments.md#step-create-customer-details-text-document-fragment)
* [Rechnungszusammenfassung](../../forms/using/create-document-fragments.md#step-create-bill-summary-text-document-fragment)
* [Zusammenfassung der Gebühren](../../forms/using/create-document-fragments.md#step-create-summary-of-charges-text-document-fragment)

Jedes Dokumentfragment enthält Felder mit statischem Text, Daten, die vom Formulardatenmodell empfangen wurden, und Daten, die über die Benutzeroberfläche für Agenten eingegeben wurden. Alle diese Felder werden im Abschnitt [Interaktive Kommunikation planen](/help/forms/using/planning-interactive-communications.md) dargestellt.

Beim Erstellen von Dokumentfragmenten in diesem Tutorial werden Variablen für Felder erstellt, die Daten über die Agentenbenutzeroberfläche empfangen.

Verwenden Sie **FDM_Create_First_IC** wie im Abschnitt [Formulardatenmodell erstellen](../../forms/using/create-form-data-model0.md) beschrieben, als Formulardatenmodell, um in diesem Tutorial Dokumentfragmente zu erstellen.

## Schritt 1: Erstellen des Textdokuments &quot;Rechnungsdetails&quot; {#step-create-bill-details-text-document-fragment}

Das Dokumentfragment &quot;Rechnungsdetails&quot;enthält die folgenden Felder:

| Feld | Datenquelle |
|---|---|
| Rechnungsnummer | Agent-Benutzeroberfläche |
| Rechnungszeitraum | Agent-Benutzeroberfläche |
| Rechnungsdatum | Agent-Benutzeroberfläche |
| Ihr Plan | Formulardatenmodell |

Gehen Sie wie folgt vor, um Variablen für Felder mit der Benutzeroberfläche für Agenten als Datenquelle zu erstellen, statischen Text zu erstellen und Formulardatenmodellelemente im Dokumentfragment zu verwenden:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.

1. Wählen Sie **Erstellen** > **Text**.
1. Geben Sie die folgenden Daten an:

   1. Geben Sie **bill_details_first_ic** als Name im Feld **Titel** ein. Der Titel wird automatisch im **Name** -Feld.

   1. Auswählen **Formulardatenmodell** aus dem **Datenmodell** Abschnitt.

   1. Auswählen **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Auswählen**.

   1. Tippen Sie auf **Weiter**.

1. Wählen Sie die **Variablen** Registerkarte im linken Bereich und tippen Sie auf **Erstellen**.
1. Im **Variable erstellen** Abschnitt:

   1. Eingabe **Rechnungsnummer** als Namen der Variablen.
   1. Auswählen **Zeichenfolge** als Typ.
   1. Tippen Sie auf **Erstellen**.

   ![Variable vom Typ String erstellen](assets/variable_create_string_new.png)

   Wiederholen Sie die Schritte 4 und 5, um die folgenden Variablen zu erstellen:

   * Billperiod: String-Typ
   * BillDate: Datumstyp

   ![Rechnungsdetails](assets/variable_bill_details_new.png)

1. Erstellen Sie statischen Text für die folgenden Felder mithilfe des rechten Bereichs:

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

1. Klicks **Speichern** , um das Textdokumentfragment Rechnungsdetails zu erstellen.

## Schritt 2: Erstellen eines Textdokumentfragments mit Kundendetails {#step-create-customer-details-text-document-fragment}

Das Dokumentfragment &quot;Kundendetails&quot;enthält die folgenden Felder:

| Feld | Datenquelle |
|---|---|
| Kundenname | Formulardatenmodell |
| Adresse | Formulardatenmodell |
| Ort der Lieferung | Agent-Benutzeroberfläche |
| Statuscode | Agent-Benutzeroberfläche |
| Mobiltelefonnummer | Formulardatenmodell |
| Alternative Kontaktnummer | Formulardatenmodell |
| Beziehungsnummer | Formulardatenmodell |
| Anzahl der Verbindungen | Agent-Benutzeroberfläche |

Gehen Sie wie folgt vor, um Variablen für Felder mit der Benutzeroberfläche für Agenten als Datenquelle zu erstellen, statischen Text zu erstellen und Formulardatenmodellelemente im Dokumentfragment zu verwenden:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **Erstellen** > **Text**.
1. Geben Sie die folgenden Daten an:

   1. Geben Sie **customer_details_first_ic** als Name im Feld **Titel** ein. Der Titel wird automatisch im **Name** -Feld.

   1. Auswählen **Formulardatenmodell** aus dem **Datenmodell** Abschnitt.

   1. Auswählen **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Auswählen**.

   1. Tippen Sie auf **Weiter**.

1. Wählen Sie die **Variablen** Registerkarte im linken Bereich und tippen Sie auf **Erstellen**.
1. Im **Variable erstellen** Abschnitt:

   1. Geben Sie als Name der Variablen **Placesupply** ein.
   1. Auswählen **Zeichenfolge** als Typ.
   1. Tippen Sie auf **Erstellen**.

   Wiederholen Sie die Schritte 4 und 5, um die folgenden Variablen zu erstellen:

   * Statecode: Zahlentyp
   * Numberconnections: Nummerntyp

1. Wählen Sie im linken Fensterbereich die Registerkarte **Datenmodellobjekte** aus, bewegen Sie den Cursor in den rechten Fensterbereich und doppelklicken Sie auf die Eigenschaft **Kunde** > **Name**.
1. Drücken Sie die Eingabetaste, um den Cursor in die nächste Zeile zu bewegen, und doppelklicken Sie auf die Eigenschaft **Kunde** > **Adresse**.
1. Erstellen Sie statischen Text für die folgenden Felder mithilfe des rechten Bereichs:

   * Mobiltelefonnummer
   * Alternative Kontaktnummer
   * Ort der Lieferung
   * Beziehungsnummer
   * Statuscode
   * Anzahl der Verbindungen

   ![Statischer Text für Kundendetails](assets/customer_details_static_text_new.png)

1. Setzen Sie den Cursor neben das Feld **Mobilfunknummer** und doppelklicken Sie auf die Eigenschaft **Kunde** > **mobilenum**.
1. Setzen Sie den Cursor neben das Feld **Alternative Kontaktnummer** und doppelklicken Sie auf die Eigenschaft **Kunde** > **alternatemobilenumber**.
1. Setzen Sie den Cursor neben das Feld **Verhältnis-Nummer** und doppelklicken Sie auf die Eigenschaft **Kunde** > **relationshipnumber**.
1. Wählen Sie die Registerkarte **Variablen** und setzen Sie den Cursor neben dem Feld **Ort der Lieferung** und doppelklicken Sie auf die Variable **Placesupply**.
1. Setzen Sie den Cursor neben das Feld **Status-Code** und doppelklicken Sie auf die Variable **Statecode**.
1. Setzen Sie den Cursor neben das Feld **Anzahl der Verbindungen** und doppelklicken Sie auf die Variable **Numberconnections**.

   ![Kundendetails](assets/customer_details_df2_new.png)

1. Klicks **Speichern** , um das Textdokumentfragment Kundendetails zu erstellen.

## Schritt 3: Erstellen des Textdokuments &quot;Rechnungszusammenfassung&quot; {#step-create-bill-summary-text-document-fragment}

Das Dokumentfragment &quot;Rechnungszusammenfassung&quot;enthält die folgenden Felder:

| Feld | Datenquelle |
|---|---|
| Vorheriger Saldo | Agent-Benutzeroberfläche |
| Zahlungen | Agent-Benutzeroberfläche |
| Anpassungen | Agent-Benutzeroberfläche |
| Gebühren für den laufenden Rechnungszeitraum | Formulardatenmodell |
| Fälliger Betrag | Agent-Benutzeroberfläche |
| Fälligkeitsdatum | Agent-Benutzeroberfläche |

Gehen Sie wie folgt vor, um Variablen für Felder mit der Benutzeroberfläche für Agenten als Datenquelle zu erstellen, statischen Text zu erstellen und Formulardatenmodellelemente im Dokumentfragment zu verwenden:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **Erstellen** > **Text**.
1. Geben Sie die folgenden Daten an:

   1. Geben Sie **bill_summary_first_ic** als Name in das Feld **Titel** ein. Der Titel wird automatisch im **Name** -Feld.

   1. Auswählen **Formulardatenmodell** aus dem **Datenmodell** Abschnitt.

   1. Auswählen **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Auswählen**.

   1. Tippen Sie auf **Weiter**.

1. Wählen Sie die **Variablen** Registerkarte im linken Bereich und tippen Sie auf **Erstellen**.
1. Im **Variable erstellen** Abschnitt:

   1. Geben Sie als Name der Variablen **Previousbalance** ein.
   1. Wählen Sie als Typ **Zahl**.
   1. Tippen Sie auf **Erstellen**.

   Wiederholen Sie die Schritte 4 und 5, um die folgenden Variablen zu erstellen:

   * Zahlungen: Zahlentyp
   * Anpassungen: Zahlentyp
   * Betrag: Zahlentyp
   * Datum: Typ

1. Erstellen Sie statischen Text für die folgenden Felder mithilfe des rechten Bereichs:

   * Vorheriger Saldo
   * Zahlungen
   * Anpassungen
   * Gebühren für den laufenden Rechnungszeitraum
   * Fälliger Betrag
   * Fälligkeitsdatum
   * Verspätete Gebühren nach Fälligkeitsdatum sind 20 $

   ![Statistischer Text zur Rechnungszusammenfassung](assets/bill_summary_static_new.png)

1. Setzen Sie den Cursor neben das Feld **Vorheriger Saldo** und doppelklicken Sie auf die Variable **Previousbalance**.
1. Setzen Sie den Cursor neben das Feld **Zahlungen** und doppelklicken Sie auf die Variable **Payments**.
1. Setzen Sie den Cursor neben das Feld **Anpassungen** und doppelklicken Sie auf die Variable **Adjustments**.
1. Setzen Sie den Cursor neben das Feld **Fälliger Betrag** und doppelklicken Sie auf die Variable **Amountdue**.
1. Setzen Sie den Cursor neben das Feld **Fälligkeitsdatum** und doppelklicken Sie auf die Variable **Duedate**.
1. Wählen Sie die Registerkarte **Datenmodellobjekte** im linken Bereich, platzieren Sie den Cursor in den rechten Bereich neben dem Feld **Gebühren für aktuelle Rechnungsperiode** und doppelklicken Sie auf die Eigenschaft **bills** > **usagecharges**.

   ![Rechnungszusammenfassung](assets/bill_summary_static_variables_new.png)

1. Klicks **Speichern** , um das Textdokumentfragment Kundendetails zu erstellen.

## Schritt 4: Erstellen Sie die Zusammenfassung der Gebühren im Textfragment {#step-create-summary-of-charges-text-document-fragment}

Die Zusammenfassung der Gebühren im Dokumentfragment umfasst die folgenden Felder:

| Feld | Datenquelle |
|---|---|
| Anrufgebühren | Formulardatenmodell |
| Gebühren für Konferenzanrufe | Formulardatenmodell |
| SMS-Gebühren | Formulardatenmodell |
| Gebühren für das mobile Internet | Formulardatenmodell |
| Nationale Roaming-Gebühren | Formulardatenmodell |
| Internationale Roaming-Gebühren | Formulardatenmodell |
| Mehrwert - Service-Gebühren | Formulardatenmodell |
| Gesamtkosten | Formulardatenmodell |
| GESAMTZAHLBARER ZUSCHUSS | Formulardatenmodell |

Gehen Sie wie folgt vor, um statischen Text zu erstellen und Formulardatenmodellelemente im Dokumentfragment zu verwenden:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Dokumentfragmente]**.
1. Wählen Sie **Erstellen** > **Text**.
1. Geben Sie die folgenden Daten an:

   1. Geben Sie **summary_charges_first_ic** als Name im Feld **Titel** ein. Der Titel wird automatisch in das Feld „Name“ eingetragen.

   1. Auswählen **Formulardatenmodell** aus dem **Datenmodell** Abschnitt.

   1. Auswählen **FDM_Create_First_IC** als Formulardatenmodell und tippen Sie auf **Auswählen**.

   1. Tippen Sie auf **Weiter**.

1. Erstellen Sie statischen Text für die folgenden Felder mithilfe des rechten Bereichs:

   * Anrufgebühren
   * Gebühren für Konferenzanrufe
   * SMS-Gebühren
   * Gebühren für das mobile Internet
   * Nationale Roaming-Gebühren
   * Internationale Roaming-Gebühren
   * Mehrwert - Service-Gebühren
   * Gesamtkosten
   * GESAMTZAHLBARER ZUSCHUSS

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

1. Wählen Sie den Text in der Zeile **Mehrwert - Service-Gebühren** aus und tippen Sie auf **Regel erstellen**, um eine Bedingung zu erstellen, auf deren Grundlage die Zeile in der interaktiven Kommunikation angezeigt wird:
1. Im **Regel erstellen** Popup-Fenster:

   1. Auswählen **Datenmodelle und -variablen** und dann **Rechnungen** > **callcharges**.

   1. Auswählen **kleiner als** als Operator.
   1. Auswählen **Zahl** und geben Sie den Wert als **60**.

   Basierend auf dieser Bedingung wird die Zeile Mehrwert-Services-Gebühren nur angezeigt, wenn der Wert für das Feld Anrufkosten unter 60 liegt.

   ![create_rules_caption](assets/create_rules_caption.gif)

1. Klicks **Speichern** , um die Zusammenfassung der Gebühren zu erstellen.
