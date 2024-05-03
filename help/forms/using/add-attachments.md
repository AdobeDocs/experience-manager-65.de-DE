---
title: Hinzufügen von Anhängen
description: Fügen Sie Fotos und Freihandnotizen als Anmerkungen zu Aufgaben in der AEM Forms-App hinzu.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 82282e2d-63a1-47e9-b2ec-f50a4bd32bd3
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 100%

---

# Hinzufügen von Anhängen{#adding-attachments}

## Hinzufügen von Anhängen in Formularen, die mit AEM Forms Workflow-Server (AEM Forms on JEE) synchronisiert werden {#adding-annotations}

Mit der AEM Forms-App können Sie Bilder, Freihandnotizen und Kommentare zu Ihrem Formular hinzufügen, das mit dem AEM Forms-JEE-Server synchronisiert wird. Wenn das Formular von einem AEM Forms Workflow-Server geladen wird, werden die Anhänge zu dem Formular hinzugefügt. Sie können die Schaltfläche für Anhänge ![attachments-app](assets/attachments-app.png) auswählen, um alle Anhänge in einem Formular gemeinsam anzuzeigen. Die rote Benachrichtigung gibt die Anzahl von Anhänge im Formular an. Wenn keine Anhänge im Formular vorhanden sind, wird die rote Benachrichtigungsschaltfläche nicht angezeigt. Falls keine Anhänge im Formular vorhanden sind, erhalten Sie Optionen zum Anhängen von Fotos oder Skizzen, wenn Sie die Schaltfläche für Anhänge ![attach](assets/attch.png) auswählen.

Ihre Optionen sind:

* **Galerie**: Hiermit können Sie ein Bild aus den auf dem Gerät gespeicherten Bildern hinzufügen.

* **Kamera**: Hiermit können Sie ein Foto aufnehmen und es zum Formular hinzufügen. 

* **Hinweise**: Hiermit können Sie eine Notiz oder Textanmerkung hinzufügen. Verwenden Sie ![Freihand](assets/scribble.png), um eine Notiz hinzuzufügen und ![Tastatur](assets/keyboard.png), um einen Textkommentar hinzuzufügen.

>[!NOTE]
>
>Die von einem Benutzer hinzugefügten Anhänge sind für andere Benutzer des Programms AEM Forms sichtbar. Die von einem Benutzer hinzugefügten Bilder können von anderen Benutzern können nicht gelöscht werden.
>

### Der Bildschirm „Anhänge“ {#the-attachments-screen}

Um alle Anhänge zusammen an einem Ort zu sehen, wählen Sie ![attachments-app](assets/attachments-app.png) aus. Hier können Sie Anhänge hinzufügen, umbenennen und löschen.

![Alle Anhänge an einem Ort](assets/attachments-screen.png)

Verwenden Sie die Schaltfläche mit dem **Pluszeichen** (+) im Bildschirm „Anhänge“, um ein weiteres Bild, eine weitere Notiz oder einen weiteren Text anzufügen.

### Hinzufügen eines Fotos {#adding-a-photograph}

Sie können die Kamera Ihres Mobilgeräts oder auf Ihrem Gerät gespeicherte Bilder verwenden, um ein Bild im Formular anzuhängen.

1. Wählen Sie unten im Fenster die Schaltfläche für Anhänge ![attach](assets/attch.png) aus.
1. Wählen Sie im Popup-Menü, das angezeigt wird, die Option **Galerie** oder **Kamera** aus.
1. Führen Sie je nach ausgewählter Option einen der folgenden Schritte aus:

   1. Wenn Sie **Kamera** auswählen:

      Nehmen Sie ein Foto auf. Wählen Sie anschließend die Schaltfläche **Verwenden** ![use-pic](assets/use-pic.png) aus.

      Oder wählen Sie die Schaltfläche **Erneut aufnehmen** ![retake](assets/retake.png) aus, um erneut ein Foto aufzunehmen.

   1. Wenn Sie **Galerie** auswählen:

      Die Bildauswahl des Geräts wird eingeblendet. Wählen Sie in der Bildauswahl des Geräts das Bild aus, das Sie anhängen möchten.

### Hinzufügen einer Notiz {#adding-a-note}

Mit der Option **Notizen** können Sie dem Formular Freihandskizzen oder Textanhänge hinzufügen.

1. Wählen Sie unten im Fenster die Schaltfläche für Anhänge ![attach](assets/attch.png) aus.
1. Wählen Sie im Popup-Menü, das angezeigt wird, die Option **Notizen** aus.
1. Dadurch wird die Benutzeroberfläche „Notizen“ gestartet, auf der Sie Freihandskizzen erfassen können.

   ![Freihand-Benutzeroberfläche](assets/scribble-ui.png)

   Freihandskizzen

   Sie können die folgenden Optionen in der Benutzeroberfläche für Freihandskizzen verwenden:

   * **Löschen**: Löscht den gesamten Bildschirm.
   * **Fertig-Schaltfläche**: Fügt die aktuelle Freihandskizze hinzu.
   * **Abbrechen-Schaltfläche**: Verwirft die aktuelle Freihandskizze und beendet die zugehörige Benutzeroberfläche.
   * ![Tastatur](assets/keyboard.png): Löscht die Skizze und ermöglicht die Eingabe einer Textnotiz.

   ![Tastatur im AEM Forms-Programm Scribble](assets/keyboard-inapp.png)

## Anhänge in Formularen, die mit AEM-Formular-Servern ohne AEM Forms Workflow (AEM Forms on OSGi) synchronisiert werden {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Anhänge für mobile Formulare, die mit AEM Forms OSGi-Servern synchronisiert werden, funktionieren ähnlich wie AEM Forms JEE-Server.

Anhänge auf Formularebene werden für adaptive Formulare, die in der App von einem AEM Forms OSGi-Server geladen werden, nicht unterstützt. Um Bilder oder Kommentare anzuhängen, aktivieren Sie Anhänge auf Feldebene im Formular, wenn Sie es erstellen. Ziehen Sie die Dateianhangskomponente aus dem Komponenten-Browser in das Feld.

Bei adaptiven Formularen können Sie die angehängten Dateien im Datensatzdokument (Document of Record, DoR) anzeigen. Weitere Informationen finden Sie unter [Generierung eines Datensatzdokuments für adaptive Nicht-XFA-Formulare](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
