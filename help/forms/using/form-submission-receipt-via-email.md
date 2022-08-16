---
title: Senden einer Formularsendebestätigung per E-Mail
seo-title: Sending a form submission acknowledgement via email
description: Mit AEM Forms können Sie die E-Mail-Übermittlungsaktion konfigurieren, die eine Bestätigung an einen Benutzer beim Senden des Formulars sendet.
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: c80b1ef4-8fe3-48e0-8fc6-3032dc022a38
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 574de3d5-69ba-4e2f-a8ab-c59f357e4386
docset: aem65
exl-id: bca4044a-18a9-4b97-92de-eff1e9a840f9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 100%

---

# Senden einer Formularsendebestätigung per E-Mail {#sending-a-form-submission-acknowledgement-via-email}

## Senden der Daten adaptiver Formulare {#adaptive-form-data-submission}

Adaptive Formulare bieten mehrere standardmäßige [Übermittlungsaktionen](../../forms/using/configuring-submit-actions.md)-Workflows, um die Formulardaten an verschiedene Endpunkte zu senden.

Zum Beispiel wird bei der Übermittlungsaktion **[!UICONTROL E-Mail senden]** eine E-Mail bei erfolgreicher Übermittlung eines adaptiven Formulars gesendet. Sie kann auch so konfiguriert werden, dass die Formulardaten und die PDF-Datei in die E-Mail eingefügt werden.

In diesem Artikel werden die Schritte erläutert, mit denen die E-Mail-Aktion für ein adaptives Formular aktiviert wird, sowie die verschiedenen bereitgestellten Konfigurationen.

>[!NOTE]
>
>Sie können auch die Option **[!UICONTROL PDF per E-Mail senden]** verwenden, um das ausgefüllte Formular per E-Mail als PDF-Anlage zu senden. Die Konfigurationsoptionen für diese Aktion sind mit den Optionen identisch, die für die Aktion **[!UICONTROL E-Mail senden]** verfügbar sind. Die E-Mail-PDF-Aktion ist nur für XFA-basierte adaptive Formulare verfügbar.

## Aktion „E-Mail senden“  {#email-action}

Mit der Aktion „E-Mail senden“ kann ein Autor automatisch eine E-Mail an einen oder mehrere Empfänger senden lassen, wenn das adaptive Formular erfolgreich übermittelt wurde.

>[!NOTE]
>
>Um die Aktion „E-Mail senden“ verwenden zu können, müssen Sie dem AEM-E-Mail-Service konfigurieren, wie in [Konfigurieren des E-Mail-Services](/help/sites-administering/notification.md#configuring-the-mail-service) beschrieben.

### Aktivieren der Aktion „E-Mail senden“ in einem adaptiven Formular {#enabling-email-action-on-an-adaptive-form}

1. Öffnen Sie ein adaptives Formular im **[!UICONTROL Bearbeitungsmodus]**.

1. Tippen Sie auf der Registerkarte **[!UICONTROL Inhalt]** auf **[!UICONTROL Formular-Container]** und dann auf ![Konfigurieren](assets/configure-icon.svg), um die Eigenschaften des adaptiven Formulars anzuzeigen.

1. Wählen Sie im Abschnitt **[!UICONTROL Übermittlung]** die Option **[!UICONTROL E-Mail senden]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]**.

   ![Übermittlungsaktionen](assets/submission-actions.png)

1. Geben Sie gültige E-Mail-IDs in den Feldern **[!UICONTROL An]**, **[!UICONTROL CC]** und **[!UICONTROL BCC]** an.

   Geben Sie den Betreff und den Text der E-Mail in den Feldern **[!UICONTROL Betreff]** bzw. **[!UICONTROL E-Mail-Vorlage]** an.

   Sie können auch variable Platzhalter in den Feldern angeben. In diesem Fall werden die Feldwerte verarbeitet, wenn das Formular erfolgreich von einem Endbenutzer gesendet wurde. Weitere Informationen finden Sie unter [Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen](../../forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Aktivieren Sie **[!UICONTROL Anhänge einschließen]**, wenn das Formular Dateianhänge enthält und Sie diese Dateien in der E-Mail anhängen möchten.

   >[!NOTE]
   >
   >Wenn Sie die Option **[!UICONTROL PDF mittels E-Mail senden]** auswählen, müssen Sie die Option „Anlagen einschließen“ aktivieren.

1. Klicken Sie auf ![Speichern](assets/save_icon.svg), um die Änderungen zu speichern.

### Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Die Feldnamen in einem adaptiven Formular werden als Platzhalter bezeichnet, die durch den Wert dieses Felds ersetzt werden, wenn ein Benutzer das Formular sendet.

In der Aktion **[!UICONTROL E-Mail senden]** können Sie Platzhalter verwenden, die verarbeitet werden, wenn die Aktion ausgeführt wird. Das bedeutet, dass die Header der E-Mail (**[!UICONTROL An]**, **[!UICONTROL CC]**, **[!UICONTROL BCC]**, **[!UICONTROL Betreff]**) dann erstellt werden, wenn der Benutzer das Formular sendet.

Um einen Platzhalter zu definieren, geben Sie `${<field name>}` in ein Feld ein, nachdem Sie **[!UICONTROL E-Mail senden]** als Übermittlungsaktion ausgewählt haben.

Beispiel: Wenn das Formular das Feld **[!UICONTROL E-Mail-Adresse]** mit dem Namen `email_addr` zur Abfrage der E-Mail-ID eines Benutzers enthält, können Sie Folgendes in den Feldern **[!UICONTROL An]**, **[!UICONTROL CC]** oder **[!UICONTROL BCC]** angeben.

`${email_addr}`

Wenn ein Benutzer das Formular sendet, wird eine E-Mail an die E-Mail-Adresse gesendet, die in das Feld `email_addr` des Formulars eingegeben wurde.

>[!NOTE]
>
>Sie finden den Namen eines Felds im Dialogfeld **[!UICONTROL Bearbeiten]** für das Feld.

Variable Platzhalter können auch in den Feldern **[!UICONTROL Betreff]** und **[!UICONTROL E-Mail-Vorlage]** verwendet werden.

Beispiel:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Felder in wiederholbaren Bereichen können nicht als variable Platzhalter verwendet werden.
