---
title: Druckkanal und Web-Kanal
description: Importieren von Druckkanalvorlagen und Erstellen und Aktivieren von Webkanalvorlagen
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: cd7dbdac-dc76-4a1f-b850-0a9f47ae08de
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 44%

---

# Druckkanal und Web-Kanal{#print-channel-and-web-channel}

Interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: Druck und Web. Der Druckkanal wird verwendet, um PDF- und Papiernachrichten zu erstellen, z. B. einen gedruckten Brief als Erinnerung an Versicherungsprämie-Zahlungen, während der Webkanal zur Bereitstellung von Online-Erlebnissen wie einem Kreditkartenauszug auf einer Website verwendet wird.

Autoren der Vorlage für die interaktive Kommunikation können Elemente wie Dokumentfragmente und Bilder verwenden, um die Druck- bzw. Netzversionen der Vorlage für die interaktive Kommunikation zu erstellen.

Eine der Voraussetzungen für das [Erstellen einer interaktiver Kommunikation](../../forms/using/create-interactive-communication.md) ist, dass die Vorlagen für den Druck- und/oder Webkanal auf dem Server verfügbar sind. Während Vorlagenautoren die Webkanalvorlage in AEM selbst erstellen, wird die Druckkanalvorlage XDP in Adobe Forms Designer erstellt und auf den Server hochgeladen.

## Druckkanal {#printchannel}

Der Druckkanal einer interaktiven Kommunikation verwendet die XFA-Formularvorlage XDP. Eine XDP wird mit Adobe Forms Designer entwickelt. Weitere Informationen zum Erstellen von Druckkanalvorlagen finden Sie unter [Layout-Design](../../forms/using/layout-design-details.md). Um eine Druckkanalvorlage in Ihrer interaktiven Kommunikation zu verwenden, müssen Sie die Vorlage auf den AEM Forms-Server hochladen.

### Druckkanalvorlage für die interaktive Kommunikation hochladen {#upload-interactive-communication-print-channel-template}

Um die Vorlage hochzuladen, müssen Sie Mitglied der Gruppe &quot;forms-user&quot;sein. Führen Sie die folgenden Schritte aus, um die Druckkanalvorlage (XDP) in AEM Forms hochzuladen:

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare &amp; Dokumente]**.

1. Auswählen **[!UICONTROL Erstellen]** > **[!UICONTROL Datei-Upload]**.

   Navigieren Sie zur entsprechenden Druckkanalvorlage (XDP), wählen Sie sie aus und wählen Sie **[!UICONTROL Öffnen]**.

## Webkanal {#web-channel}

Vorlagenautoren und -administratoren können Webvorlagen erstellen, bearbeiten und aktivieren. Damit andere Benutzer Webvorlagen erstellen können, müssen Sie ihnen Berechtigungen erteilen. Weitere Informationen finden Sie unter [Verwalten von Benutzer-, Gruppen- und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md).

### Authoring einer Webkanalvorlage {#authoring-web-channel-template}

Um eine Webkanalvorlage zu erstellen, müssen Sie zunächst einen Vorlagenordner erstellen. Sobald Sie eine Webvorlage in einem Vorlagenordner erstellt haben, müssen Sie die Vorlage aktivieren, damit die Formularbenutzer den Webkanal einer interaktiven Kommunikation basierend auf der Vorlage erstellen können.

Führen Sie die folgenden Schritte aus, um eine Webkanalvorlage zu erstellen:

1. Erstellen Sie einen Vorlagenordner, um Ihre Webvorlagen für interaktive Kommunikation zu speichern, falls noch kein entsprechender Ordner eingerichtet ist. Weitere Informationen finden Sie unter „Vorlagenordner“ in [Seitenvorlagen – Bearbeitbar](/help/sites-developing/page-templates-editable.md).

   1. Auswählen **[!UICONTROL Instrumente]** ![tools](assets/tools.png) > **[!UICONTROL Konfigurationsbrowser]**.
      * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
   1. Wählen Sie auf der Seite &quot;Konfigurationsbrowser&quot;die Option **[!UICONTROL Erstellen]**.
   1. Geben Sie im Dialogfeld &quot;Konfiguration erstellen&quot;einen Titel für den Ordner an und prüfen Sie **[!UICONTROL Bearbeitbare Vorlagen]** und wählen Sie **[!UICONTROL Erstellen]**.

      Der Ordner wird erstellt und auf der Seite „Konfigurationsbrowser“ aufgelistet.

1. Navigieren Sie zum entsprechenden Vorlagenordner und erstellen Sie eine Webvorlage.

   1. Navigieren Sie zum entsprechenden Vorlagenordner, indem Sie **[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorlagen]** > **`[Folder]`** wählen.
   1. Wählen Sie **[!UICONTROL Erstellen]** aus.
   1. Auswählen **[!UICONTROL Interaktive Kommunikation - Webkanal]** und wählen **[!UICONTROL Nächste]**.
   1. Geben Sie einen Vorlagentitel und eine Beschreibung ein und wählen Sie **[!UICONTROL Erstellen]**.

      Die Vorlage wird erstellt und ein Dialogfeld wird angezeigt.

   1. Auswählen **[!UICONTROL Öffnen]** , um die von Ihnen erstellte Vorlage im Vorlageneditor zu öffnen.

      Der Vorlagen-Editor wird angezeigt.

      ![webchanneltemplate](assets/webchanneltemplate.png)

      Beim Erstellen oder Bearbeiten einer Vorlage kann ein Vorlagenautor verschiedene Aspekte definieren. Das Erstellen oder Bearbeiten einer Vorlage ähnelt dem Erstellen von Seiten. Weitere Informationen finden Sie unter „Bearbeiten von Vorlagen – Vorlagenautoren“ in [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md).

1. Aktivieren Sie die Vorlage, um ihre Verwendung für die Erstellung interaktiver Kommunikation zu ermöglichen.

   1. Auswählen **[!UICONTROL Instrumente]** ![tools](assets/tools.png) > **[!UICONTROL Vorlagen]**.
   1. Navigieren Sie zur entsprechenden Vorlage, wählen Sie sie aus und klicken Sie auf **[!UICONTROL Aktivieren]** und wählen Sie in der Warnmeldung **[!UICONTROL Aktivieren]**.

      Die Vorlage ist aktiviert und ihr Status wird als Aktiviert angezeigt. Jetzt können Sie mit der Erstellung einer interaktiven Kommunikation fortfahren, in der Sie die neu erstellte Webkanalvorlage verwenden können.

### Druckkanal als Master für Webkanal {#print-channel-as-master-for-web-channel}

Beim Erstellen einer interaktiven Kommunikation können Autoren diese Option auswählen, um den Webkanal synchron mit dem Druckkanal zu erstellen. Die Verwendung des Druckkanals als Master für den Webkanal stellt sicher, dass der Inhalt, die Vererbung und die Datenbindung des Webkanals vom Druckkanal abgeleitet werden und die im Druckkanal vorgenommenen Änderungen im Webkanal übernommen werden können. Die Autoren der interaktiven Kommunikation können jedoch bei Bedarf die Vererbung für bestimmte Komponenten im Webkanal unterbrechen.

![Druckkanal als Master](assets/create_ic_print_master_new.png) ![Webkanal mit Druckkanal als Master](assets/create_ic_print_master_web_new.png)
