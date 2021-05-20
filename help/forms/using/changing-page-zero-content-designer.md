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
feature: Adaptive Formulare
exl-id: 466b7e85-a2f8-4e1e-8afc-1566b0ccb84c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 72%

---

# Inhalt auf Seite Null in Designer ändern {#changing-page-zero-content-in-designer}

Der Inhalt von Seite Null wird standardmäßig angezeigt, wenn ein Nicht-Adobe PDF-Viewer, z. B. der standardmäßige PDF-Viewer in [!DNL Chrome] oder [!DNL Firefox], den Inhalt des PDF/XFA-Formulars nicht lesen kann. Nachfolgend finden Sie die standardmäßige Meldung auf Seite Null.

![defaultpage0message](assets/defaultpage0message.png)

[!DNL AEM Forms] Mit der Designer-Version können Sie die Meldung ändern, die auf Seite Null angezeigt wird. Zum Ändern der auf Seite Null angezeigten Meldung müssen Sie folgende Schritte ausführen:

1. Stellen Sie sicher, dass die [!DNL AEM Forms]-Version von Designer installiert ist. Sie können die Version im Bildschirm „Info“ des Designers überprüfen.

1. Öffnen Sie das Formular, in dem der Inhalt der Seite Null geändert werden soll.

1. Klicken Sie auf **[!UICONTROL Datei]** > **[!UICONTROL Formulareigenschaften]**.

1. Klicken Sie im Dialogfeld [!UICONTROL Formulareigenschaften] auf ![plus](assets/plus.png) (Plus-Symbol), um eine benutzerdefinierte Eigenschaft hinzuzufügen.

1. Legen Sie **_pagezerocontent** als den Namen der Eigenschaft fest.
1. Fügen Sie die Meldung auf Seite Null als Wert im Rich Text-Format hinzu. Beispiel:


   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/acrreader.</p></body>`

1. Speichern Sie das Formular als PDF-Datei.

1. Zeigen Sie das PDF-Formular im Browser an, um sicherzustellen, dass die Meldung aktualisiert wurde. Der obige Beispielwert wird wie folgt angezeigt:

   ![changeMessage](assets/changedmessage.png)

>[!NOTE]
>
>Die gerade von Ihnen erstellte benutzerdefinierte Eigenschaft wird möglicherweise nicht korrekt im Dialogfenster „Formulareigenschaften“ angezeigt, wenn Sie das Formular erneut öffnen. Sie funktioniert jedoch problemlos und das Formular zeigt die aktualisierte Meldung auf Seite Null an.
