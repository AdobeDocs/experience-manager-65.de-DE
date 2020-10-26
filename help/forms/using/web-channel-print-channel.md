---
title: Druckkanal und Webkanal
seo-title: Druckkanal und Webkanal
description: Importieren von Druckkanalvorlagen und Erstellen und Aktivieren von Webkanalvorlagen
seo-description: Importieren von Druckkanalvorlagen und Erstellen und Aktivieren von Webkanalvorlagen
uuid: 2361b1ee-c789-4a5a-9575-8b62b603da1e
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 96d2b1cc-3252-4cc7-8b06-a897cbef8599
docset: aem65
translation-type: tm+mt
source-git-commit: ce64b148ba96cc64670aaf96c1b201bafa282b98
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 63%

---


# Druckkanal und Webkanal{#print-channel-and-web-channel}

Interaktive Kommunikation kann über zwei Kanäle erfolgen: Druck und Web. Der Druckkanal wird zum Erstellen von PDFs und Papierkommunikationen verwendet, z. B. ein gedruckter Brief zur Erinnerung an die Versicherungsprämienzahlung, während der Webkanal für Online-Projekte wie eine Kreditkartenabrechnung auf einer Website verwendet wird.

Autoren interaktiver Kommunikation können Assets wie Dokument- und Bildfragmente wiederverwenden, um sowohl Druck- als auch Webversionen der interaktiven Kommunikation zu erstellen.

One of the prerequisites for [Creating an Interactive Communication](../../forms/using/create-interactive-communication.md) is to have the templates for print and/or web channel available on the server. Während Vorlagenautoren die Webkanalvorlage in AEM selbst erstellen, wird die Druckkanalvorlage XDP in Adobe Forms Designer erstellt und auf den Server hochgeladen.

## Druckkanal {#printchannel}

Print Kanal of an Interactive Communication verwendet XFA-Formularvorlage, XDP. Eine XDP wird mit Adobe Forms Designer entwickelt. For more information on creating print channel templates, see [Layout Design](../../forms/using/layout-design-details.md). Um eine Druckkanalvorlage in Ihrer interaktiven Kommunikation zu verwenden, müssen Sie die Vorlage auf den AEM Forms-Server hochladen.

### Laden Sie die Druckkanalvorlage für die interaktive Kommunikation hoch {#upload-interactive-communication-print-channel-template}

Um die Vorlage hochladen zu können, müssen Sie Mitglied der Gruppe „forms-users“ sein. Führen Sie die folgenden Schritte aus, um die Druckkanalvorlage (XDP) in AEM Forms hochzuladen:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare &amp; Dokumente]**.

1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]**.

   Navigieren Sie zur entsprechenden Druckkanalvorlage (XDP), wählen Sie diese aus und tippen Sie auf **[!UICONTROL Öffnen]**.

## Webkanal {#web-channel}

Vorlagenautoren und Administratoren können Webvorlagen erstellen, bearbeiten und aktivieren. Damit andere Benutzer Webvorlagen erstellen können, müssen Sie ihnen Rechte geben. For more information, see [User, Group and Access Rights Administration](/help/sites-administering/user-group-ac-admin.md).

### Webkanalvorlage bearbeiten {#authoring-web-channel-template}

Um eine Webkanalvorlage zu erstellen, müssen Sie zuerst einen Vorlagenordner erstellen. Nachdem Sie eine Webvorlage in einem Vorlagenordner erstellt haben, müssen Sie die Vorlage aktivieren, damit die Formularbenutzer auf der Grundlage der Vorlage einen Web-Kanal einer interaktiven Kommunikation erstellen können.

Führen Sie die folgenden Schritte aus, um eine Webkanalvorlage zu erstellen:

1. Erstellen Sie einen Ordner &quot;Vorlage&quot;, um Ihre Webvorlagen für interaktive Kommunikation beizubehalten, sofern noch keine Vorlage vorhanden ist. For more information, see Template Folders in [Page Templates - Editable](/help/sites-developing/page-templates-editable.md).

   1. Tap **[!UICONTROL Tools]** ![tools](assets/tools.png) > **[!UICONTROL Configuration Browser]**.
      * See the [Configuration Browser](/help/sites-administering/configurations.md) documentation for more information.
   1. In the Configuration Browser page, tap **[!UICONTROL Create]**.
   1. In the Create Configuration dialog, specify a title for the folder, check **[!UICONTROL Editable Templates]**, and tap **[!UICONTROL Create]**.

      Der Ordner wird erstellt und auf der Seite &quot;Konfigurationsbrowser&quot;aufgelistet.

1. Navigieren Sie zum entsprechenden Vorlagenordner und erstellen Sie eine Webvorlage.

   1. Navigate to the appropriate template folder by selecting **[!UICONTROL Tools]** > **[!UICONTROL Templates]** > **`[Folder]`**.
   1. Tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Select **[!UICONTROL Interactive Communication - Web Channel]** and tap **[!UICONTROL Next]**.
   1. Geben Sie einen Vorlagentitel und eine Beschreibung ein und tippen Sie anschließend auf **[!UICONTROL Erstellen]**.

      Die Vorlage wird erstellt und ein Dialogfeld wird angezeigt.

   1. Tippen Sie auf **[!UICONTROL Öffnen]**, um die Vorlage zu öffnen, die Sie im Vorlageneditor erstellt haben.

      Der Vorlageneditor wird angezeigt.

      ![webchannelTemplate](assets/webchanneltemplate.png)

      Beim Erstellen oder Bearbeiten einer Vorlage kann ein Vorlagenautor diverse Aspekte definieren. Das Erstellen oder Bearbeiten einer Vorlage ähnelt der Seitenerstellung. For more information, see Editing Templates - Template Authors in [Creating Page Templates](/help/sites-authoring/templates.md).

1. Um die Verwendung dieser Vorlage für die Erstellung interaktiver Kommunikation zuzulassen, aktivieren Sie die Vorlage.

   1. Tap **[!UICONTROL Tools]** ![tools](assets/tools.png) > **[!UICONTROL Templates]**.
   1. Navigate to the appropriate template, select it, and tap **[!UICONTROL Enable]** and in the alert message, tap **[!UICONTROL Enable]**.

      Die Vorlage ist aktiviert und ihr Status wird als „Aktiviert“ angezeigt. Jetzt können Sie mit dem Erstellen einer interaktiven Kommunikation fortfahren, in der Sie die neu erstellte Webkanalvorlage verwenden können.

### Druckkanal als Master für Webkanal {#print-channel-as-master-for-web-channel}

Beim Erstellen einer interaktiven Kommunikation können Autoren diese Option auswählen, um den Webkanal synchron mit dem Druckkanal zu erstellen. Die Verwendung des Druckkanals als Master für den Webkanal stellt sicher, dass der Inhalt, die Vererbung und die Datenbindung des Webkanals aus dem Druckkanal abgeleitet werden und dass die im Druckkanal vorgenommenen Änderungen im Webkanal widergespiegelt werden können. Die Autoren der interaktiven Kommunikation dürfen jedoch ggf. die Vererbung für bestimmte Komponenten im Webkanal aufheben.

![Drucken Sie Kanal als Übergeordnet](assets/create_ic_print_master_new.png) ![Web-Kanal mit Druckausgabe-Kanal wie Übergeordnet](assets/create_ic_print_master_web_new.png)

