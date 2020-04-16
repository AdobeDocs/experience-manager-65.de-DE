---
title: Senden einer Formularsendebestätigung per E-Mail
seo-title: Senden einer Formularsendebestätigung per E-Mail
description: Mit AEM Forms können Sie die E-Mail-Übermittlungsaktion konfigurieren, die eine Bestätigung an einen Benutzer beim Senden des Formulars sendet.
seo-description: Mit AEM Forms können Sie die E-Mail-Übermittlungsaktion konfigurieren, die eine Bestätigung an einen Benutzer beim Senden des Formulars sendet.
uuid: c80b1ef4-8fe3-48e0-8fc6-3032dc022a38
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 574de3d5-69ba-4e2f-a8ab-c59f357e4386
docset: aem65
translation-type: tm+mt
source-git-commit: acc2a3977353386d7e1dfd1344a61d78812fe3fc

---


# Senden einer Formularsendebestätigung per E-Mail {#sending-a-form-submission-acknowledgement-via-email}

## Senden der Daten adaptiver Formulare {#adaptive-form-data-submission}

Adaptive Formulare bieten mehrere standardmäßige [Übermittlungsaktionen](../../forms/using/configuring-submit-actions.md)-Workflows, um die Formulardaten an verschiedene Endpunkte zu senden.

For example, the **[!UICONTROL Send email]** submit action sends an email on successful submission of an adaptive form. Sie kann auch so konfiguriert werden, dass die Formulardaten und die PDF-Datei in der E-Mail gesendet werden.

In diesem Artikel werden die Schritte erläutert, mit denen die E-Mail-Aktion für ein adaptives Formular aktiviert wird, sowie die verschiedenen bereitgestellten Konfigurationen.

>[!NOTE]
>
>You can also use the **[!UICONTROL Send PDF via email]** option to send the completed form by email as a PDF attachment. The configuration options available for this action are the same as the options available for the **[!UICONTROL Send email]** action. Die E-Mail-PDF-Aktion ist nur für XFA-basierte adaptive Formulare verfügbar.

## E-Mail-Aktion senden {#email-action}

Mit der Aktion E-Mail senden kann ein Autor bei erfolgreicher Übermittlung eines adaptiven Formulars automatisch eine E-Mail an einen oder mehrere Empfänger senden.

>[!NOTE]
>
>To use the Send email action, you need to configure the AEM mail service as described in [Configuring the mail service](/help/sites-administering/notification.md#configuring-the-mail-service).

### Enabling Send email action on an adaptive form {#enabling-email-action-on-an-adaptive-form}

1. Open an adaptive form in **[!UICONTROL edit]** mode.

1. Tippen Sie auf der Registerkarte &quot; **[!UICONTROL Inhalt]** &quot;auf **[!UICONTROL Formular-Container]** und dann auf ![Konfigurieren](assets/configure-icon.svg) , um die Eigenschaften des adaptiven Formulars Ansicht.

1. In the **[!UICONTROL Submission]** section, select **[!UICONTROL Send email]** from the **[!UICONTROL Submit Action]** drop-down list.

   ![Übermittlungsaktionen](assets/submission-actions.png)

1. Specify valid email IDs in the **[!UICONTROL To]**, **[!UICONTROL CC]**, and **[!UICONTROL BCC]** fields.

   Specify the subject and the body of the email in the **[!UICONTROL Subject]** and **[!UICONTROL Email Template]** fields, respectively.

   Sie können auch variable Platzhalter in den Feldern angeben. In diesem Fall werden die Feldwerte verarbeitet, wenn das Formular erfolgreich von einem Endbenutzer gesendet wurde. Weitere Informationen finden Sie unter [Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen](../../forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Select **[!UICONTROL Include attachments]** if the form includes file attachments and you want to attach these files in the email.

   >[!NOTE]
   >
   >If you choose the **[!UICONTROL Send PDF via Email]** option, you must select the Include attachments option.

1. Click ![save](assets/save_icon.svg) to save the changes.

### Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Die Feldnamen in einem adaptiven Formular werden als Platzhalter bezeichnet, die durch den Wert dieses Felds ersetzt werden, wenn ein Benutzer das Formular sendet.

In the **[!UICONTROL Send email]** action, you can use placeholders that are processed when the action is performed. It implies that the headers of the email (such as **[!UICONTROL To]**, **[!UICONTROL CC]**, **[!UICONTROL BCC]**, **[!UICONTROL Subject]**) are generated when the user submits the form.

Um einen Platzhalter zu definieren, geben Sie ihn `${<field name>}` in ein Feld ein, nachdem Sie als Übermittlungsaktion &quot;E-Mail **[!UICONTROL senden]** &quot;ausgewählt haben.

For example, if the form contains the **[!UICONTROL Email address]** field, named `email_addr`, for capturing the email ID of a user, you can specify the following in the **[!UICONTROL To]**, **[!UICONTROL CC]**, or **[!UICONTROL BCC]** fields.

`${email_addr}`

Wenn ein Benutzer das Formular sendet, wird eine E-Mail an die E-Mail-Adresse gesendet, die in das Feld `email_addr` des Formulars eingegeben wurde.

>[!NOTE]
>
>Sie finden den Namen eines Feldes im Dialogfeld **[!UICONTROL Bearbeiten]** für das Feld.

Variable placeholders can also be used in the **[!UICONTROL Subject]** and **[!UICONTROL Email Template]** fields.

Beispiel:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Felder in wiederholbaren Bereichen können nicht als variable Platzhalter verwendet werden.

