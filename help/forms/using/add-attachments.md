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
exl-id: 82282e2d-63a1-47e9-b2ec-f50a4bd32bd3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 70%

---

# Hinzufügen von Anhängen{#adding-attachments}

## Hinzufügen von Anlagen in Formularen, die mit dem AEM Forms Workflow-Server (AEM Forms on JEE) synchronisiert werden {#adding-annotations}

Mit der AEM Forms-App können Sie Bilder, Notizen und Kommentare zu Ihrem Formular hinzufügen, das mit dem AEM Forms JEE-Server synchronisiert wird. Wenn das Formular von einem AEM Forms Workflow-Server geladen wird, werden die Anlagen zu dem Formular hinzugefügt. Sie können auf die Schaltfläche für Anlagen ![attachments-app](assets/attachments-app.png) tippen, um alle Anlagen in einem Formular zusammen anzuzeigen. Die rote Benachrichtigung gibt die Anzahl von Anlagen im Formular an. Wenn das Formular keine Anlagen enthält, wird die rote Benachrichtigungsschaltfläche nicht angezeigt. Wenn keine Anlagen im Formular vorhanden sind, erhalten Sie beim Tippen auf die Schaltfläche für Anlagen ![Attch](assets/attch.png) Optionen zum Anhängen von Fotos oder Scribbles.

Ihre Optionen sind:

* **Galerie**: Hiermit können Sie ein Bild aus den auf dem Gerät gespeicherten hinzufügen.

* **Kamera**: Hiermit können Sie ein Foto aufnehmen und es zum Formular hinzufügen. 

* **Hinweise**: Hiermit können Sie eine Notiz oder Textanmerkung hinzufügen. Verwenden Sie ![Scribble](assets/scribble.png), um ein Scribble hinzuzufügen, und ![Tastatur](assets/keyboard.png), um eine Textanmerkung hinzuzufügen.

>[!NOTE]
>
>Von einem Benutzer hinzugefügte Anlagen sind für andere Benutzer der AEM Forms-App sichtbar. Andere Benutzer können die Anlagen nicht löschen, die von einem Benutzer hinzugefügt werden.


### Der Bildschirm „Anlagen“{#the-attachments-screen}

Um alle Anlagen an einem Ort anzuzeigen, tippen Sie auf ![attachments-app](assets/attachments-app.png). Hier können Sie Anlagen hinzufügen, umbenennen und löschen.

![Alle Anlagen an einem Ort](assets/attachments-screen.png)

Verwenden Sie die Schaltfläche mit dem **Pluszeichen** (+) im Bildschirm „Anlagen“, um ein weiteres Bild, eine weitere Notiz oder einen weiteren Text anzufügen.

### Hinzufügen eines Fotos {#adding-a-photograph}

Sie können die Kamera Ihres Mobilgeräts oder auf Ihrem Gerät gespeicherte Bilder verwenden, um ein Bild im Formular anzuhängen.

1. Tippen Sie auf die Schaltfläche für Anlagen ![Attch](assets/attch.png) am unteren Rand des Fensters.
1. Tippen Sie auf **Galerie** oder **Kamera** im Popup-Menü, das angezeigt wird.
1. Führen Sie je nach ausgewählter Option einen der folgenden Schritte aus:

   1. Wenn Sie **Kamera** auswählen:

      Nehmen Sie ein Foto auf. Tippen Sie dann auf die Schaltfläche **Verwenden Sie** ![use-pic](assets/use-pic.png).

      Oder tippen Sie auf die Schaltfläche **Retake** ![retake](assets/retake.png) , um das Foto erneut aufzunehmen.

   1. Wenn Sie **Galerie** auswählen:

      Das Dialogfeld für die Bildauswahl wird eingeblendet. In der Bildauswahl Ihres Geräts tippen Sie auf das Bild, das Sie anfügen möchten.

### Hinzufügen einer Notiz {#adding-a-note}

Mit der Option **Notizen** können Sie dem Formular Freihand-Scribbles oder Textanlagen hinzufügen.

1. Tippen Sie auf die Schaltfläche für Anlagen ![Attch](assets/attch.png) am unteren Rand des Fensters.
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

## Anlagen in Formularen, die mit den AEM Forms-Servern ohne AEM Forms Workflow (AEM Forms unter OSGi) synchronisiert werden {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Anlagen für Mobile Forms, die mit AEM Forms OSGi-Servern synchronisiert werden, funktionieren ähnlich wie die AEM Forms JEE-Server.

Anlagen auf Formularebene werden für adaptive Formulare, die in der AEM Forms-App von einem AEM Forms OSGi-Server geladen werden, nicht unterstützt. Um Bilder oder Textanmerkungen hinzuzufügen, aktivieren Sie Anlagen auf Feldebene im Formular, wenn Sie es erstellen. Ziehen Sie die Dateianlagenkomponente aus dem Komponenten-Browser in das Feld.

Bei adaptiven Formularen können Sie die angehängten Dateien im Datensatzdokument (DoR) anzeigen. Siehe [Generierung eines Datensatzdokuments für adaptive Nicht-XFA-Formulare](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
