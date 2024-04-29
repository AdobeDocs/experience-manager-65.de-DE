---
title: Druckkanal und Web-Kanal
description: Importieren von Druckkanalvorlagen und Erstellen und Aktivieren von Web-Kanalvorlagen
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: cd7dbdac-dc76-4a1f-b850-0a9f47ae08de
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '696'
ht-degree: 100%

---

# Druckkanal und Web-Kanal{#print-channel-and-web-channel}

Eine interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: den Druckkanal und den Web-Kanal. Der Druckkanal wird zum Erstellen von PDFs und Papierkommunikationen verwendet, z. B. für gedruckte Briefe, um an die Zahlung von Versicherungsprämien zu erinnern. Der Web-Kanal wird hingegen für Online-Erlebnisse verwendet, z. B. Kreditkartenabrechnungen auf einer Website.

Autoren der Vorlage für die interaktive Kommunikation können Elemente wie Dokumentfragmente und Bilder verwenden, um die Druck- bzw. Netzversionen der Vorlage für die interaktive Kommunikation zu erstellen.

Eine der Voraussetzungen für das [Erstellen einer interaktiver Kommunikation](../../forms/using/create-interactive-communication.md) ist, dass die Vorlagen für den Druck- und/oder Webkanal auf dem Server verfügbar sind. Während Vorlagenautoren die Webkanalvorlage in AEM selbst erstellen, wird die Druckkanalvorlage XDP in Adobe Forms Designer erstellt und auf den Server hochgeladen.

## Druckkanal {#printchannel}

Der Druckkanal einer interaktiven Kommunikation verwendet die XFA-Formularvorlage XDP. Eine XDP wird mit Adobe Forms Designer entwickelt. Weitere Informationen zum Erstellen von Druckkanalvorlagen finden Sie unter [Layout-Design](../../forms/using/layout-design-details.md). Um eine Druckkanalvorlage in Ihrer interaktiven Kommunikation zu verwenden, müssen Sie die Vorlage auf den AEM Forms-Server hochladen.

### Hochladen einer Druckkanalvorlage für eine interaktive Kommunikation {#upload-interactive-communication-print-channel-template}

Um die Vorlage hochladen zu können, müssen Sie Mitglied der Gruppe „forms-users“ sein. Führen Sie die folgenden Schritte aus, um die Druckkanalvorlage (XDP) in AEM Forms hochzuladen:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]** aus.

   Navigieren Sie zur entsprechenden Druckkanalvorlage (XDP) und wählen Sie diese und dann **[!UICONTROL Öffnen]** aus.

## Web-Kanal {#web-channel}

Autorinnen und Autoren von Vorlagen sowie Admins können Web-Vorlagen erstellen, bearbeiten und aktivieren. Damit andere Benutzende Web-Vorlagen erstellen können, müssen Sie ihnen Rechte geben. Weitere Informationen finden Sie unter [Verwalten von Benutzer-, Gruppen- und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md).

### Erstellen einer Web-Kanalvorlage {#authoring-web-channel-template}

Um eine Web-Kanalvorlage zu erstellen, müssen Sie zuerst einen Vorlagenordner erstellen. Sobald Sie eine Webvorlage in einem Vorlagenordner erstellt haben, müssen Sie die Vorlage aktivieren, damit die Formularbenutzer den Webkanal einer interaktiven Kommunikation basierend auf der Vorlage erstellen können.

Führen Sie die folgenden Schritte aus, um eine Webkanalvorlage zu erstellen:

1. Erstellen Sie einen Vorlagenordner, um Ihre Webvorlagen für interaktive Kommunikation zu speichern, falls noch kein entsprechender Ordner eingerichtet ist. Weitere Informationen finden Sie unter „Vorlagenordner“ in [Seitenvorlagen – Bearbeitbar](/help/sites-developing/page-templates-editable.md).

   1. Wählen Sie **[!UICONTROL Tools]** ![Tools](assets/tools.png) > **[!UICONTROL Konfigurations-Browser]** aus.
      * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser](/help/sites-administering/configurations.md).
   1. Wählen Sie auf der Seite „Konfigurations-Browser“ die Option **[!UICONTROL Erstellen]** aus.
   1. Legen Sie im Dialogfeld „Konfiguration erstellen“ einen Titel für den Ordner fest, aktivieren Sie **[!UICONTROL Bearbeitbare Vorlagen]** und wählen Sie **[!UICONTROL Erstellen]** aus.

      Der Ordner wird erstellt und auf der Seite „Konfigurationsbrowser“ aufgelistet.

1. Navigieren Sie zum entsprechenden Vorlagenordner und erstellen Sie eine Webvorlage.

   1. Navigieren Sie zum entsprechenden Vorlagenordner, indem Sie **[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorlagen]** > **`[Folder]`** wählen.
   1. Wählen Sie **[!UICONTROL Erstellen]** aus.
   1. Wählen Sie **[!UICONTROL Webkanal für interaktive Kommunikationl]** und dann **[!UICONTROL Weiter]** aus.
   1. Geben Sie einen Vorlagentitel sowie eine Beschreibung ein und wählen Sie anschließend **[!UICONTROL Erstellen]** aus.

      Die Vorlage wird erstellt und ein Dialogfeld wird angezeigt.

   1. Wählen Sie **[!UICONTROL Öffnen]** aus, um die im Vorlageneditor erstellte Vorlage zu öffnen.

      Der Vorlageneditor wird angezeigt.

      ![webchanneltemplate](assets/webchanneltemplate.png)

      Beim Erstellen oder Bearbeiten einer Vorlage kann eine Vorlagenautorin oder ein Vorlagenautor verschiedene Aspekte definieren. Das Erstellen oder Bearbeiten einer Vorlage ähnelt der Seitenerstellung. Weitere Informationen finden Sie unter „Bearbeiten von Vorlagen – Vorlagenautoren“ in [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md).

1. Aktivieren Sie die Vorlage, um ihre Verwendung für die Erstellung interaktiver Kommunikation zu ermöglichen.

   1. Wählen Sie **[!UICONTROL Tools]** ![Tools](assets/tools.png) > **[!UICONTROL Vorlagen]** aus.
   1. Navigieren Sie zu der entsprechenden Vorlage, wählen Sie sie und dann die Option **[!UICONTROL Aktivieren]** aus. Wählen Sie anschließend in der Warnmeldung **[!UICONTROL Aktivieren]** aus.

      Die Vorlage wird aktiviert und ihr Status als „Aktiviert“ angezeigt. Nun können Sie mit der Erstellung einer interaktiven Kommunikation fortfahren. Darin können Sie die neu erstellte Web-Kanalvorlage verwenden.

### Druckkanal als Primärkanal für den Web-Kanal {#print-channel-as-master-for-web-channel}

Beim Erstellen einer interaktiven Kommunikation können Autorinnen und Autoren diese Möglichkeit nutzen, um den Web-Kanal synchron mit dem Druckkanal zu erstellen. Die Verwendung des Druckkanals als Primärkanal für den Web-Kanal stellt sicher, dass der Inhalt, die Vererbung und die Datenbindung des Web-Kanals vom Druckkanal abgeleitet werden und dass die im Druckkanal vorgenommenen Änderungen im Web-Kanal widergespiegelt werden können. Die Autorinnen und Autoren einer interaktiven Kommunikation dürfen jedoch die Vererbung für Komponenten im Web-Kanal aufheben, falls nötig.

![Druckkanal als Master](assets/create_ic_print_master_new.png) ![Webkanal mit Druckkanal als Master](assets/create_ic_print_master_web_new.png)
