---
title: Inhalt auf Seite Null in Designer ändern
seo-title: Changing Page Zero content in Designer
description: Wissen Sie, wie Sie die auf Seite Null einer XFA-PDF angezeigte Nachricht ändern können, wenn Sie sie in einem Nicht-Adobe PDF-Viewer anzeigen?
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: ac23fb21-3f15-48ea-aeeb-4ecc12b771ac
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 56b6a573-8aba-43e7-acb7-c2da45869d95
docset: aem65
feature: Adaptive Forms
exl-id: 466b7e85-a2f8-4e1e-8afc-1566b0ccb84c
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 60%

---

# Ändern des Inhalts auf Seite null im Designer {#changing-page-zero-content-in-designer}

Der Inhalt auf Seite Null wird standardmäßig angezeigt, wenn ein PDF-Viewer, der nicht von Adobe stammt (z. B. der standardmäßige PDF-Viewer in [!DNL Chrome] oder [!DNL Firefox]), den Inhalt des PDF-/XFA-Formulars nicht lesen kann. Nachfolgend finden Sie die standardmäßige Meldung auf Seite Null.

![defaultpage0message](assets/defaultpage0message.png)

[!DNL AEM Forms] In der Designer-Version können Sie die Meldung ändern, die auf Seite 0 angezeigt wird. Zum Ändern der auf Seite Null angezeigten Meldung müssen Sie folgende Schritte ausführen:

1. Stellen Sie sicher, dass die Version [!DNL AEM Forms] von Designer auf Ihrem Computer installiert ist. Sie können die Version im Bildschirm „Info“ des Designers überprüfen.

1. Öffnen Sie das Formular, in dem der Inhalt auf Seite Null geändert werden soll.

1. Klicken Sie auf **[!UICONTROL Datei]** > **[!UICONTROL Formulareigenschaften]**.

1. Klicken Sie im Dialog [!UICONTROL Formulareigenschaften] auf ![plus](assets/plus.png) (Plussymbol), um eine benutzerdefinierte Eigenschaft hinzuzufügen.

1. Angeben **_pagezerocontent** als Name der Eigenschaft.
1. Fügen Sie die neue Meldung &quot;Seite Null&quot;im Rich-Text-Format als Wert hinzu. Beispiel:


   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/acrreader.</p></body>`

1. Speichern Sie das Formular als PDF-Datei.

1. Zeigen Sie das PDF-Formular im Browser an, um sicherzustellen, dass die Meldung aktualisiert wurde. Der obige Beispielwert wird wie folgt angezeigt:

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>Die von Ihnen erstellte benutzerdefinierte Eigenschaft wird möglicherweise nicht ordnungsgemäß im Dialogfeld &quot;Formulareigenschaften&quot;angezeigt, wenn Sie das Formular erneut öffnen. Es funktioniert jedoch einwandfrei und das Formular zeigt die aktualisierte Meldung auf Seite Null an.
