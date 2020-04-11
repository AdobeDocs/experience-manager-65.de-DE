---
title: Hinzufügen von Anhängen
seo-title: Hinzufügen von Anhängen
description: Fotos und Notizen als Anmerkungen zu Aufgaben in der AEM Forms-App hinzufügen
seo-description: Fotos und Notizen als Anmerkungen zu Aufgaben in der AEM Forms-App hinzufügen
uuid: 3d2738b4-fd43-44ec-8eaf-a2ad4b7e5af5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: d5976ed2-4482-495c-bf77-6d192379cfef
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Hinzufügen von Anhängen{#adding-attachments}

## Adding attachments in forms synced with AEM Forms Workflow server (AEM Forms on JEE) {#adding-annotations}

Mit der AEM Forms-App können Sie Bilder, Notizen und Kommentare zu Ihrem Formular hinzufügen, das mit dem AEM Forms JEE-Server synchronisiert wird. Wenn das Formular von einem AEM Forms Workflow-Server geladen wird, werden die Anlagen zu dem Formular hinzugefügt. You can tap the attachment button ![attachments-app](assets/attachments-app.png) to see all the attachments in a form together. Die rote Benachrichtigung gibt die Anzahl von Anlagen im Formular an. Wenn keine Anlagen im Formular vorhanden sind, wird die rote Benachrichtigungsschaltfläche nicht angezeigt. If there are no attachments in the form, when you tap the attachments button ![attch](assets/attch.png), you get options to attach photos or scribbles.

Ihre Optionen sind:

* **Galerie**: Hiermit können Sie ein Bild aus den auf dem Gerät gespeicherten hinzufügen.

* **Kamera**: Hiermit können Sie ein Foto aufnehmen und es zum Formular hinzufügen. 

* **Hinweise**: Hiermit können Sie eine Notiz oder Textanmerkung hinzufügen. Use ![scribble](assets/scribble.png) to add a scribble, and ![keyboard](assets/keyboard.png) to add a text note.

>[!NOTE]
>
>Von einem Benutzer hinzugefügte Anlagen sind für andere Benutzer der AEM Forms-App sichtbar. Andere Benutzer können die Anlagen nicht löschen, die von einem Benutzer hinzugefügt werden.


### Der Bildschirm „Anlagen“{#the-attachments-screen}

To see all the attachments in a place, tap ![attachments-app](assets/attachments-app.png). Hier können Sie Anlagen hinzufügen, umbenennen und löschen.

![Alle Anlagen an einem Ort](assets/attachments-screen.png)

Verwenden Sie die Schaltfläche mit dem **Pluszeichen** (+) im Bildschirm „Anlagen“, um ein weiteres Bild, eine weitere Notiz oder einen weiteren Text anzufügen.

### Hinzufügen eines Fotos {#adding-a-photograph}

Sie können die Kamera Ihres Mobilgeräts oder auf Ihrem Gerät gespeicherte Bilder verwenden, um ein Bild im Formular anzuhängen.

1. Tap the attachment button ![attch](assets/attch.png) at the bottom of the window.
1. Tippen Sie auf **Galerie** oder **Kamera** im Popup-Menü, das angezeigt wird.
1. Führen Sie je nach ausgewählter Option einen der folgenden Schritte aus:

   1. Wenn Sie **Kamera** auswählen:

      Nehmen Sie ein Foto auf. Then tap the **Use** ![use-pic](assets/use-pic.png) button.

      Or tap the **Retake** ![retake](assets/retake.png) button to retake the photograph.

   1. Wenn Sie **Galerie** auswählen:

      Das Dialogfeld für die Bildauswahl wird eingeblendet. In der Bildauswahl Ihres Geräts tippen Sie auf das Bild, das Sie anfügen möchten.

### Hinzufügen einer Notiz {#adding-a-note}

Mit der Option **Notizen** können Sie dem Formular Freihand-Scribbles oder Textanlagen hinzufügen.

1. Tap the attachment button ![attch](assets/attch.png) at the bottom of the window.
1. Tippen Sie auf **Notizen** im Popup-Menü, das angezeigt wird.
1. Dadurch wird die Benutzeroberfläche „Notizen“ gestartet, auf der Sie ein Freihand-Scribble erfassen können.

   ![Scribble-Benutzeroberfläche](assets/scribble-ui.png)

   Scribble

   Sie können die folgenden Optionen in der Scribble-Benutzeroberfläche verwenden:

   * **Clear**: Löscht den gesamten Bildschirm.
   * **Schaltfläche „Done“**: Fügt das aktuelle Scribble hinzu.
   * **Schaltfläche „Cancel“**: Das aktuelle Scribble wird nicht verwendet und die Scribble-Benutzeroberfläche wird geschlossen.
   * ![Tastatur](assets/keyboard.png): Löscht das Scribble und ermöglicht das Hinzufügen einer Textanmerkung.
   ![Tastatur in AEM Forms-App-Scribble](assets/keyboard-inapp.png)

## Attachments in forms synced with the AEM Forms servers without AEM Forms Workflow (AEM Forms on OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Anlagen für Mobile Forms, die mit AEM Forms OSGi-Servern synchronisiert werden, funktionieren ähnlich wie die AEM Forms JEE-Server.

Anlagen auf Formularebene werden für adaptive Formulare, die in der AEM Forms-App von einem AEM Forms OSGi-Server geladen werden, nicht unterstützt. Um Bilder oder Textanmerkungen hinzuzufügen, aktivieren Sie Anlagen auf Feldebene im Formular, wenn Sie es erstellen. Ziehen Sie die Dateianlagenkomponente aus dem Komponenten-Browser in das Feld.

Bei adaptiven Formularen können Sie die angehängten Dateien im Datensatzdokument (DoR) anzeigen. Siehe [Generierung eines Datensatzdokuments für adaptive Nicht-XFA-Formulare](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
