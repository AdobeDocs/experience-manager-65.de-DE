---
title: Hinzufügen von Anhängen
description: Fotos und Notizen als Anmerkungen zu Ihrer Aufgabe in der AEM Forms-App hinzufügen
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 82282e2d-63a1-47e9-b2ec-f50a4bd32bd3
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 34%

---

# Hinzufügen von Anhängen{#adding-attachments}

## Hinzufügen von Anhängen in Formularen, die mit AEM Forms Workflow-Server (AEM Forms on JEE) synchronisiert werden {#adding-annotations}

Mit der AEM Forms-App können Sie Bilder, Notizen und Textanmerkungen an das mit dem AEM Forms JEE-Server synchronisierte Formular anhängen. Wenn Ihr Formular von einem AEM Forms Workflow-Server geladen wird, werden Ihre Anhänge zum Formular hinzugefügt. Sie können die Schaltfläche für Anlagen auswählen ![attachments-app](assets/attachments-app.png) , um alle Anlagen in einem Formular zusammen anzuzeigen. Die rote Benachrichtigung gibt die Anzahl von Anhänge im Formular an. Wenn keine Anhänge im Formular vorhanden sind, wird die rote Benachrichtigungsschaltfläche nicht angezeigt. Wenn keine Anlagen im Formular vorhanden sind, wenn Sie die Schaltfläche &quot;Anlagen&quot;auswählen ![attch](assets/attch.png), erhalten Sie Optionen zum Anhängen von Fotos oder Scribbles.

Ihre Optionen sind:

* **Galerie**: Hiermit können Sie ein Bild aus den auf dem Gerät gespeicherten Bildern hinzufügen.

* **Kamera**: Hiermit können Sie ein Foto aufnehmen und es zum Formular hinzufügen. 

* **Hinweise**: Hiermit können Sie eine Notiz oder Textanmerkung hinzufügen. Verwenden Sie ![Freihand](assets/scribble.png), um eine Notiz hinzuzufügen und ![Tastatur](assets/keyboard.png), um einen Textkommentar hinzuzufügen.

>[!NOTE]
>
>Die von einem Benutzer hinzugefügten Anhänge sind für andere Benutzer des Programms AEM Forms sichtbar. Die von einem Benutzer hinzugefügten Bilder können von anderen Benutzern können nicht gelöscht werden.
>

### Der Bildschirm „Anhänge“ {#the-attachments-screen}

Um alle Anlagen an einer Stelle anzuzeigen, wählen Sie ![attachments-app](assets/attachments-app.png). Hier können Sie Anhänge hinzufügen, umbenennen und löschen.

![Alle Anhänge an einem Ort](assets/attachments-screen.png)

Verwenden Sie die Schaltfläche mit dem **Pluszeichen** (+) im Bildschirm „Anhänge“, um ein weiteres Bild, eine weitere Notiz oder einen weiteren Text anzufügen.

### Hinzufügen eines Fotos {#adding-a-photograph}

Sie können die Kamera Ihres Mobilgeräts oder gespeicherte Bilder auf Ihrem Gerät verwenden, um ein Bild im Formular anzuhängen.

1. Schaltfläche &quot;Anlage auswählen&quot; ![attch](assets/attch.png) unten im Fenster.
1. Auswählen **Galerie** oder **Kamera** im angezeigten Popup-Fenster.
1. Führen Sie je nach ausgewählter Option Folgendes aus:

   1. Wenn Sie **Kamera**.

      Machen Sie ein Foto. Wählen Sie dann die **Verwendung** ![use-pic](assets/use-pic.png) Schaltfläche.

      Oder wählen Sie die **Wiederholen** ![retake](assets/retake.png) -Schaltfläche, um das Foto erneut aufzunehmen.

   1. Wenn Sie **Galerie**.

      Der Bildbrowser des Geräts wird angezeigt. Wählen Sie im Bildbrowser Ihres Geräts das Bild aus, das Sie anhängen möchten.

### Hinzufügen einer Notiz {#adding-a-note}

Mit der Option **Notizen** können Sie dem Formular Freihandskizzen oder Textanhänge hinzufügen.

1. Schaltfläche &quot;Anlage auswählen&quot; ![attch](assets/attch.png) unten im Fenster.
1. Auswählen **Hinweise** im angezeigten Popup-Fenster.
1. Erfassen Sie in der Benutzeroberfläche &quot;Notizen&quot;, die gestartet wird, ein Freihand-Scribble.

   ![Freihand-Benutzeroberfläche](assets/scribble-ui.png)

   Scribble

   Sie können die folgenden Optionen in der Scribble-Benutzeroberfläche verwenden:

   * **Löschen**: Löscht den Bildschirm.
   * **Schaltfläche Fertig**: Fügt das aktuelle Scribble hinzu.
   * **Schaltfläche &quot;Abbrechen&quot;**: Verwirft das aktuelle Scribble und beendet die Scribble-Benutzeroberfläche.
   * ![Tastatur](assets/keyboard.png): Löscht die Skizze und ermöglicht die Eingabe einer Textnotiz.

   ![Tastatur im AEM Forms-Programm Scribble](assets/keyboard-inapp.png)

## Anlagen in Formularen, die mit den AEM Forms-Servern ohne AEM Forms Workflow (AEM Forms unter OSGi) synchronisiert werden {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Anlagen für mobile Formulare, die mit AEM Forms OSGi-Servern synchronisiert werden, funktionieren ähnlich wie die AEM Forms JEE-Server.

Anlagen auf Formularebene werden nicht für adaptive Formulare unterstützt, die in der App von einem AEM Forms OSGi-Server geladen werden. Um Bilder oder Textanmerkungen anzuhängen, aktivieren Sie Anlagen auf Feldebene im Formular, wenn Sie es erstellen. Ziehen Sie die Dateianlagenkomponente aus dem Komponenten-Browser in das Feld.

Wenn adaptive Formulare vorhanden sind, können Sie die angehängten Dateien im Datensatzdokument (DoR) anzeigen. Weitere Informationen finden Sie unter [Generierung eines Datensatzdokuments für adaptive Nicht-XFA-Formulare](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
