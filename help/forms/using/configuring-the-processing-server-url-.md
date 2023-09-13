---
title: Konfigurieren der AEM DS-Einstellungen
description: Erfahren Sie, wie Sie die URL des Verarbeitungsservers angeben, bevor Sie ein Formular senden.
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin
exl-id: c43cab7b-3421-4e1b-a834-b2dd6eb23c1d
source-git-commit: 5af420c8e95fed88a8516cce27b8bbc7d3974e75
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 37%

---

# Konfigurieren der AEM DS-Einstellungen{#configuring-aem-ds-settings}

In diesem Artikel wird beschrieben, wie Sie die **AEM DS Settings Service**. Diese Einstellung kann in mehreren Szenarien verwendet werden, z. B.:

* In Correspondence Management

   * Konfigurieren des AEM Forms-Workflows
   * Beim Verwenden von Forms Portal zum Remote-Speichern von Entwürfen/Übermittlungen

* In adaptiven Formularen, für Fälle, in denen ein adaptives Formular von der Veröffentlichungsinstanz gesendet wird

Im Folgenden werden die Schritte zum Konfigurieren der **[!UICONTROL AEM DS-Einstellungen]**:

1. Öffnen Sie den Konfigurations-Manager unter der Veröffentlichungsinstanz mit der URL:\
   *https://localhost:port/system/console/configMgr*.

   ![AEM-Web-Konsolenkonfiguration](assets/web_configuration_console_new.png)

1. Klicken Sie im Fenster **[!UICONTROL Adobe Experience Manager Web-Konsolenkonfiguration]** auf die Option **[!UICONTROL AEM DS-Einstellungen]**.

   ![DS-Einstellungen](assets/ds_settings_new.png)

1. Das Fenster **[!UICONTROL AEM DS-Einstellungendienst]** zeigt die allgemeinen Konfigurationseinstellungen für AEM DS-Komponenten.

   ![DS-Einstellungs-Service](assets/ds_settings_service_new.png)

1. Fügen Sie die folgenden Informationen in die entsprechenden Felder ein:

   **[!UICONTROL Verarbeitungsserver-URL]**: Der Verarbeitungsserver ist der Server, auf dem der Forms- oder AEM-Workflow ausgelöst werden muss. Dies kann mit der URL der AEM Autoreninstanz oder der anderen Server-URL (d. h. https://localhost:port/) übereinstimmen.

   **[!UICONTROL Verarbeitungs-Server-Benutzername]**: Benutzername des Workflow-Benutzers [basiert auf der verwendeten Server-URL]

   **[!UICONTROL Verarbeitungsserver-Kennwort]**: Kennwort des Workflow-Benutzers

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Bei Verwendung von Forms- oder AEM-Workflows ist es vor der Übermittlung durch den Veröffentlichungsserver erforderlich, den DS-Einstellungsdienst zu konfigurieren. Andernfalls schlägt die Übermittlung des Formulars fehl.
   >    
   >
