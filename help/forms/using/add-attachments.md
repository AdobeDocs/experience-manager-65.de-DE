---
title: Hinzufügen von Anhängen
seo-title: Adding attachments
description: Fotos und Notizen als Anmerkungen zu Aufgaben in der AEM Forms-App hinzufügen
seo-description: Add photographs and scribble notes as annotations to your task in the AEM Forms app
uuid: 3d2738b4-fd43-44ec-8eaf-a2ad4b7e5af5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: d5976ed2-4482-495c-bf77-6d192379cfef
docset: aem65
exl-id: 82282e2d-63a1-47e9-b2ec-f50a4bd32bd3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 100%

---

# Hinzufügen von Anhängen{#adding-attachments}

## Hinzufügen von Anhängen in Formularen, die mit AEM Forms Workflow-Server (AEM Forms on JEE) synchronisiert werden {#adding-annotations}

Mit der AEM Forms-App können Sie Bilder, Notizen und Kommentare zu Ihrem Formular hinzufügen, das mit dem AEM Forms JEE-Server synchronisiert wird. Wenn das Formular von einem AEM Forms Workflow-Server geladen wird, werden die Anlagen zu dem Formular hinzugefügt. Sie können auf die Schaltfläche für Anhänge ![attachments-app](assets/attachments-app.png) tippen, um alle Anhänge in einem Formular gemeinsam anzuzeigen. Die rote Benachrichtigung gibt die Anzahl von Anhänge im Formular an. Wenn keine Anhänge im Formular vorhanden sind, wird die rote Benachrichtigungsschaltfläche nicht angezeigt. Falls keine Anhänge im Formular vorhanden sind, erhalten Sie Optionen zum Anhängen von Fotos oder Notizen, wenn Sie auf die Schaltfläche für Anhänge ![attch](assets/attch.png) tippen.

Ihre Optionen sind:

* **Galerie**: Hiermit können Sie ein Bild aus den auf dem Gerät gespeicherten Bildern hinzufügen.

* **Kamera**: Hiermit können Sie ein Foto aufnehmen und es zum Formular hinzufügen. 

* **Hinweise**: Hiermit können Sie eine Notiz oder Textanmerkung hinzufügen. Verwenden Sie ![Freihand](assets/scribble.png), um eine Notiz hinzuzufügen und ![Tastatur](assets/keyboard.png), um einen Textkommentar hinzuzufügen.

>[!NOTE]
>
>Die von einem Benutzer hinzugefügten Anhänge sind für andere Benutzer des Programms AEM Forms sichtbar. Die von einem Benutzer hinzugefügten Bilder können von anderen Benutzern können nicht gelöscht werden.

### Der Bildschirm „Anhänge“ {#the-attachments-screen}

Um alle Anhänge zusammen an einem Ort zu sehen, tippen Sie auf ![attachments-app](assets/attachments-app.png). Hier können Sie Anhänge hinzufügen, umbenennen und löschen.

![Alle Anhänge an einem Ort](assets/attachments-screen.png)

Verwenden Sie die Schaltfläche mit dem **Pluszeichen** (+) im Bildschirm „Anhänge“, um ein weiteres Bild, eine weitere Notiz oder einen weiteren Text anzufügen.

### Hinzufügen eines Fotos {#adding-a-photograph}

Sie können die Kamera Ihres Mobilgeräts oder auf Ihrem Gerät gespeicherte Bilder verwenden, um ein Bild im Formular anzuhängen.

1. Tippen Sie am unteren Fensterrand auf die Schaltfläche für Anhänge ![attch](assets/attch.png).
1. Tippen Sie im Popup-Menü, das angezeigt wird, auf **Galerie** oder **Kamera**.
1. Führen Sie je nach ausgewählter Option einen der folgenden Schritte aus:

   1. Wenn Sie **Kamera** auswählen:

      Nehmen Sie ein Foto auf. Tippen Sie anschließend auf die Schaltfläche **Verwenden** ![use-pic](assets/use-pic.png).

      Tippen Sie alternativ auf die Schaltfläche **Erneut aufnehmen** ![retake](assets/retake.png), um erneut ein Foto aufzunehmen.

   1. Wenn Sie **Galerie** auswählen:

      Das Dialogfeld für die Bildauswahl wird eingeblendet. Tippen Sie in der Bildauswahl Ihres Geräts auf das Bild, das Sie anhängen möchten.

### Hinzufügen einer Notiz {#adding-a-note}

Mit der Option **Notizen** können Sie dem Formular Freihandskizzen oder Textanhänge hinzufügen.

1. Tippen Sie am unteren Fensterrand auf die Schaltfläche für Anhänge ![attch](assets/attch.png).
1. Tippen Sie auf **Notizen** im Popup-Menü, das angezeigt wird.
1. Dadurch wird die Benutzeroberfläche „Notizen“ gestartet, auf der Sie ein Freihand-Scribble erfassen können.

   ![Freihand-Benutzeroberfläche](assets/scribble-ui.png)

   Scribble

   Sie können die folgenden Optionen in der Scribble-Benutzeroberfläche verwenden:

   * **Clear**: Löscht den gesamten Bildschirm.
   * **Schaltfläche „Done“**: Fügt das aktuelle Scribble hinzu.
   * **Schaltfläche „Cancel“**: Das aktuelle Scribble wird nicht verwendet und die Scribble-Benutzeroberfläche wird geschlossen.
   * ![Tastatur](assets/keyboard.png): Löscht die Skizze und ermöglicht die Eingabe einer Textnotiz.

   ![Tastatur im AEM Forms-Programm Scribble](assets/keyboard-inapp.png)

## Anlagen in Formularen, die mit AEM Forms-Server ohne AEM Forms Workflow (AEM Forms on OSGi) synchronisiert werden {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Anlagen für Mobile Forms, die mit AEM Forms OSGi-Servern synchronisiert werden, funktionieren ähnlich wie die AEM Forms JEE-Server.

Anlagen auf Formularebene werden für adaptive Formulare, die in der AEM Forms-App von einem AEM Forms OSGi-Server geladen werden, nicht unterstützt. Um Bilder oder Textanmerkungen hinzuzufügen, aktivieren Sie Anlagen auf Feldebene im Formular, wenn Sie es erstellen. Ziehen Sie die Dateianlagenkomponente aus dem Komponenten-Browser in das Feld.

Bei adaptiven Formularen können Sie die angehängten Dateien im Datensatzdokument (DoR) anzeigen. Weitere Informationen finden Sie unter [Generierung eines Datensatzdokuments für adaptive Nicht-XFA-Formulare](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
