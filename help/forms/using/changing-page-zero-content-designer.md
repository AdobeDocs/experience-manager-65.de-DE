---
title: Inhalt auf Seite Null in Designer ändern
description: Wissen Sie, wie Sie die Meldung ändern können, die auf der Seite Null einer XFA-PDF-Datei angezeigt wird, wenn diese in einem PDF-Viewer angezeigt wird, der nicht von Adobe stammt?
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms,Forms Designer,Designer
exl-id: 466b7e85-a2f8-4e1e-8afc-1566b0ccb84c
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 100%

---

# Ändern des Inhalts auf Seite null im Designer {#changing-page-zero-content-in-designer}

Der Inhalt auf Seite Null wird standardmäßig angezeigt, wenn ein PDF-Viewer, der nicht von Adobe stammt (z. B. der standardmäßige PDF-Viewer in [!DNL Chrome] oder [!DNL Firefox]), den Inhalt des PDF-/XFA-Formulars nicht lesen kann. Nachfolgend finden Sie die standardmäßige Meldung auf Seite Null.

![defaultpage0message](assets/defaultpage0message.png)

Mit der Version [!DNL AEM Forms] von Designer können Sie die auf Seite Null angezeigte Meldung ändern. Zum Ändern der auf Seite Null angezeigten Meldung müssen Sie folgende Schritte ausführen:

1. Stellen Sie sicher, dass die Version [!DNL AEM Forms] von Designer auf Ihrem Computer installiert ist. Sie können die Version im Bildschirm „Info“ des Designers überprüfen.

1. Öffnen Sie das Formular, in dem der Inhalt auf Seite Null geändert werden soll.

1. Klicken Sie auf **[!UICONTROL Datei]** > **[!UICONTROL Formulareigenschaften]**.

1. Klicken Sie im Dialog [!UICONTROL Formulareigenschaften] auf ![plus](assets/plus.png) (Plussymbol), um eine benutzerdefinierte Eigenschaft hinzuzufügen.

1. Geben Sie **_pagezerocontent** als Name der Eigenschaft an.
1. Fügen Sie die neue Meldung auf Seite Null als Wert im Rich Text-Format hinzu. Zum Beispiel:


   `<body xmlns="http://www.w3.org/1999/xhtml" xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Speichern Sie das Formular als PDF-Datei.

1. Zeigen Sie das PDF-Formular im Browser an, um sicherzustellen, dass die Meldung aktualisiert wurde. Der obige Beispielwert wird wie folgt angezeigt:

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>Die von Ihnen erstellte benutzerdefinierte Eigenschaft wird möglicherweise nicht korrekt im Dialogfeld „Formulareigenschaften“ angezeigt, wenn Sie das Formular erneut öffnen. Sie funktioniert jedoch problemlos und das Formular zeigt die aktualisierte Meldung auf Seite Null an.
