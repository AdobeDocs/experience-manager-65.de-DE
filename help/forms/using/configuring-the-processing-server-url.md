---
title: Konfigurieren der AEM DS-Einstellungen
description: Erfahren Sie, wie Sie die URL des Verarbeitungs-Servers angeben, bevor Sie ein Formular übermitteln.
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
exl-id: c43cab7b-3421-4e1b-a834-b2dd6eb23c1d
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 88%
---
# Konfigurieren der AEM DS-Einstellungen{#configuring-aem-ds-settings}

In diesem Artikel wird beschrieben, wie Sie den **AEM DS-Einstellungsdienst** konfigurieren. Diese Einstellung kann in mehreren Szenarien verwendet werden, zum Beispiel:

* In Correspondence Management

  * zur AEM Forms Workflow-Konfiguration
  * bei Verwendung des Formularportals zur Remote-Speicherung von Entwürfen/Übermittlung

* in adaptiven Formularen für Fälle, in denen ein adaptives Formular aus der Veröffentlichungsinstanz übermittelt wird

Führen Sie die folgenden Schritte aus, um die **[!UICONTROL AEM DS-Einstellungen]** zu konfigurieren:

1. Öffnen Sie den Konfigurations-Manager unter der Veröffentlichungsinstanz mit der URL:\
   *https://localhost:port/system/console/configMgr*

   ![AEM-Web-Konsolenkonfiguration](assets/web_configuration_console_new.png)

1. Klicken Sie im Fenster **[!UICONTROL Adobe Experience Manager Web-Konsolenkonfiguration]** auf die Option **[!UICONTROL AEM DS-Einstellungen]**.

   ![DS-Einstellungen](assets/ds_settings_new.png)

1. Das Fenster **[!UICONTROL AEM DS-Einstellungendienst]** zeigt die allgemeinen Konfigurationseinstellungen für AEM DS-Komponenten.

   ![DS-Einstellungs-Service](assets/ds_settings_service_new.png)

1. Fügen Sie die folgenden Informationen in die entsprechenden Felder ein:

   **[!UICONTROL Processing Server URL]** (Verarbeitungs-Server-URL): Der Verarbeitungs-Server ist der Server, auf dem der Forms- oder AEM-Workflow ausgelöst werden muss. Dabei kann es sich um die gleiche URL wie die der AEM-Autoreninstanz oder die andere Server-URL handeln (d. h. https://localhost:port/).

   **[!UICONTROL Verarbeitungs-Server-Benutzername]**: Benutzername des Workflow-Benutzers [basiert auf der verwendeten Server-URL]

   **[!UICONTROL Verarbeitungs-Server-Kennwort]**: Dies ist das Kennwort der Benutzenden des Workflows.

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Wenn Sie Forms- oder AEM-Workflows verwenden, müssen Sie den DS-Einstellungsdienst konfigurieren, bevor Sie Übermittlungen vom Veröffentlichungs-Server durchführen. Andernfalls schlägt die Formularübermittlung fehl.
   >    
   >
