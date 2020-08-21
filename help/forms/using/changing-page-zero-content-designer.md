---
title: Inhalt auf Seite Null in Designer ändern
seo-title: Inhalt auf Seite Null in Designer ändern
description: Wissen Sie, wie Sie die Meldung ändern können, die auf der Seite Null einer XFA-PDF-Datei angezeigt wird, wenn diese in einem PDF-Viewer angezeigt wird, der nicht von Adobe stammt?
seo-description: Wissen Sie, wie Sie die Meldung ändern können, die auf der Seite Null einer XFA-PDF-Datei angezeigt wird, wenn diese in einem PDF-Viewer angezeigt wird, der nicht von Adobe stammt?
uuid: ac23fb21-3f15-48ea-aeeb-4ecc12b771ac
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 56b6a573-8aba-43e7-acb7-c2da45869d95
docset: aem65
translation-type: tm+mt
source-git-commit: 3cbcd23254e16231a199276aa2f9e70d6ff39b34
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 72%

---


# Inhalt auf Seite Null in Designer ändern {#changing-page-zero-content-in-designer}

Page Zero content is displayed by default when a non-Adobe PDF viewer, such as the default PDF viewer in [!DNL Chrome] or [!DNL Firefox], cannot read the content of the PDF/XFA form. Nachfolgend finden Sie die standardmäßige Meldung auf Seite Null.

![defaultpage0message](assets/defaultpage0message.png)

[!DNL AEM Forms] Version von Designer ermöglicht es Ihnen, die Meldung zu ändern, die auf Seite Null angezeigt wird. Zum Ändern der auf Seite Null angezeigten Meldung müssen Sie folgende Schritte ausführen:

1. Ensure that you have the [!DNL AEM Forms] version of Designer installed. Sie können die Version im Bildschirm „Info“ des Designers überprüfen.

1. Öffnen Sie das Formular, in dem der Inhalt der Seite Null geändert werden soll.

1. Click **[!UICONTROL File]** > **[!UICONTROL Form Properties]**.

1. In the [!UICONTROL Form Properties] dialog, click ![plus](assets/plus.png) (Plus icon) to add a custom property.

1. Legen Sie **_pagezerocontent** als den Namen der Eigenschaft fest.
1. Fügen Sie die Meldung auf Seite Null als Wert im Rich Text-Format hinzu. Beispiel:


   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/acrreader.</p></body>`

1. Speichern Sie das Formular als PDF-Datei.

1. Zeigen Sie das PDF-Formular im Browser an, um sicherzustellen, dass die Meldung aktualisiert wurde. Der obige Beispielwert wird wie folgt angezeigt:

   ![changdmessage](assets/changedmessage.png)

>[!NOTE]
>
>Die gerade von Ihnen erstellte benutzerdefinierte Eigenschaft wird möglicherweise nicht korrekt im Dialogfenster „Formulareigenschaften“ angezeigt, wenn Sie das Formular erneut öffnen. Sie funktioniert jedoch problemlos und das Formular zeigt die aktualisierte Meldung auf Seite Null an.
