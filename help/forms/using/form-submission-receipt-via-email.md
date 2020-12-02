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
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 44%

---


# Senden einer Formularsendebestätigung per E-Mail {#sending-a-form-submission-acknowledgement-via-email}

## Senden der Daten adaptiver Formulare {#adaptive-form-data-submission}

Adaptive Formulare bieten mehrere standardmäßige [Übermittlungsaktionen](../../forms/using/configuring-submit-actions.md)-Workflows, um die Formulardaten an verschiedene Endpunkte zu senden.

Beispielsweise sendet die Übermittlungsaktion **[!UICONTROL E-Mail senden]** eine E-Mail bei erfolgreicher Übermittlung eines adaptiven Formulars. Sie kann auch so konfiguriert werden, dass die Formulardaten und die PDF-Datei in der E-Mail gesendet werden.

In diesem Artikel werden die Schritte erläutert, mit denen die E-Mail-Aktion für ein adaptives Formular aktiviert wird, sowie die verschiedenen bereitgestellten Konfigurationen.

>[!NOTE]
>
>Sie können auch die Option **[!UICONTROL PDF per E-Mail senden]** verwenden, um das ausgefüllte Formular per E-Mail als PDF-Anhang zu senden. Die für diese Aktion verfügbaren Konfigurationsoptionen entsprechen den Optionen für die Aktion **[!UICONTROL E-Mail senden]**. Die E-Mail-PDF-Aktion ist nur für XFA-basierte adaptive Formulare verfügbar.

## E-Mail-Aktion {#email-action} senden

Mit der Aktion E-Mail senden kann ein Autor bei erfolgreicher Übermittlung eines adaptiven Formulars automatisch eine E-Mail an einen oder mehrere Empfänger senden.

>[!NOTE]
>
>Um die Aktion E-Mail senden zu verwenden, müssen Sie den AEM-E-Mail-Dienst konfigurieren, wie unter [Konfigurieren des E-Mail-Diensts](/help/sites-administering/notification.md#configuring-the-mail-service) beschrieben.

### Aktivieren der Aktion &quot;E-Mail senden&quot;in einem adaptiven Formular {#enabling-email-action-on-an-adaptive-form}

1. Öffnen Sie ein adaptives Formular im Modus **[!UICONTROL edit]**.

1. Tippen Sie auf der Registerkarte **[!UICONTROL Content]** auf **[!UICONTROL Form Container]** und dann auf ![configure](assets/configure-icon.svg), um die Eigenschaften des adaptiven Formulars Ansicht.

1. Wählen Sie im Abschnitt **[!UICONTROL Submission]** **[!UICONTROL E-Mail senden]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]**.

   ![Übermittlungsaktionen](assets/submission-actions.png)

1. Geben Sie gültige E-Mail-IDs in den Feldern **[!UICONTROL To]**, **[!UICONTROL CC]** und **[!UICONTROL BCC]** an.

   Geben Sie den Betreff und den Text der E-Mail in den Feldern **[!UICONTROL Betreff]** und **[!UICONTROL E-Mail-Vorlage]** an.

   Sie können auch variable Platzhalter in den Feldern angeben. In diesem Fall werden die Feldwerte verarbeitet, wenn das Formular erfolgreich von einem Endbenutzer gesendet wurde. Weitere Informationen finden Sie unter [Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen](../../forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Wählen Sie **[!UICONTROL Anlagen einschließen]**, wenn das Formular Dateianlagen enthält und Sie diese Dateien in der E-Mail anhängen möchten.

   >[!NOTE]
   >
   >Wenn Sie die Option **[!UICONTROL PDF per E-Mail senden]** wählen, müssen Sie die Option &quot;Anlagen einschließen&quot;aktivieren.

1. Klicken Sie auf ![save](assets/save_icon.svg), um die Änderungen zu speichern.

### Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Die Feldnamen in einem adaptiven Formular werden als Platzhalter bezeichnet, die durch den Wert dieses Felds ersetzt werden, wenn ein Benutzer das Formular sendet.

In der Aktion **[!UICONTROL E-Mail senden]** können Sie Platzhalter verwenden, die verarbeitet werden, wenn die Aktion ausgeführt wird. Dies bedeutet, dass die Kopfzeilen der E-Mail (wie **[!UICONTROL To]**, **[!UICONTROL CC]**, **[!UICONTROL BCC]**, **[!UICONTROL Subject]**) generiert werden, wenn der Benutzer das Formular sendet.

Um einen Platzhalter zu definieren, geben Sie `${<field name>}` in ein Feld ein, nachdem Sie **[!UICONTROL E-Mail senden]** als Übermittlungsaktion ausgewählt haben.

Wenn das Formular beispielsweise das Feld **[!UICONTROL E-Mail-Adresse]** mit dem Namen `email_addr` zur Erfassung der E-Mail-ID eines Benutzers enthält, können Sie Folgendes in den Feldern **[!UICONTROL Bis]**, **[!UICONTROL CC]** oder **[!UICONTROL BCC]** angeben.

`${email_addr}`

Wenn ein Benutzer das Formular sendet, wird eine E-Mail an die E-Mail-Adresse gesendet, die in das Feld `email_addr` des Formulars eingegeben wurde.

>[!NOTE]
>
>Sie finden den Namen eines Feldes im Dialogfeld **[!UICONTROL Bearbeiten]** für das Feld.

Variable Platzhalter können auch in den Feldern **[!UICONTROL Betreff]** und **[!UICONTROL E-Mail-Vorlage]** verwendet werden.

Beispiel:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Felder in wiederholbaren Bereichen können nicht als variable Platzhalter verwendet werden.

