---
title: AEM DS-Einstellungen konfigurieren
seo-title: Configuring AEM DS settings
description: Sie müssen die Verarbeitungsserver-URL angeben, bevor Sie ein Formular senden.
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 55a6d434-7352-48a8-8387-8a5c1a48fafc
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: a7387bd3-8b31-4bd0-a861-daa8f7cb2d05
docset: aem65
role: Admin
exl-id: c43cab7b-3421-4e1b-a834-b2dd6eb23c1d
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: ht
source-wordcount: '241'
ht-degree: 100%

---

# AEM DS-Einstellungen konfigurieren{#configuring-aem-ds-settings}

Dieser Artikel beschreibt, wie Sie den **AEM DS-Einstellungen-Dienst** konfigurieren. Diese Einstellung kann in mehreren Szenarien verwendet werden, zum Beispiel:

* In Correspondence Management

   * Für die Konfiguration des AEM Forms-Workflow
   * Achten Sie bei der Verwendung von Formularportals für Remote-Verwendung, darauf, dass Sie Entwurf/der Übermittlung speichern

* In den adaptiven Formularen für Fälle, bei denen ein adaptives Formular von der Veröffentlichungsinstanz gesendet wird

Führen Sie die folgenden Schritte aus, um die **[!UICONTROL AEM DS-Einstellungen]** zu konfigurieren:

1. Öffnen Sie den Konfigurations-Manager unter der Veröffentlichungsinstanz mit der URL:\
   *https://localhost:port/system/console/configMgr*.

   ![AEM-Web-Konsolenkonfiguration](assets/web_configuration_console_new.png)

1. Klicken Sie im Fenster **[!UICONTROL Adobe Experience Manager Web-Konsolenkonfiguration]** auf die Option **[!UICONTROL AEM DS-Einstellungen]**.

   ![DS-Einstellungen](assets/ds_settings_new.png)

1. Das Fenster **[!UICONTROL AEM DS-Einstellungendienst]** zeigt die allgemeinen Konfigurationseinstellungen für AEM DS-Komponenten.

   ![DS-Einstellungs-Service](assets/ds_settings_service_new.png)

1. Fügen Sie die folgenden Informationen in die entsprechenden Felder ein:

   **[!UICONTROL Verarbeitungs-Server-URL]**: Der Verarbeitungs-Server ist der Server, auf dem der Forms- oder AEM-Workflow ausgelöst werden muss. Dies kann die gleiche URL wie die der AEM-Autoreninstanz oder die andere Server-URL sein (d. h. http://localhost:port/).

   **[!UICONTROL Verarbeitungs-Server-Benutzername]**: Benutzername des Workflow-Benutzers [basiert auf der verwendeten Server-URL]

   **[!UICONTROL Verarbeitungs-Serverkennwort]**: Das Kennwort des Workflow-Benutzers

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Bei der Verwendung von Formularen oder AEM-Workflows ist es notwendig, den DS-Einstellungendienst zu konfigurieren, bevor Sie eine Übertragung vom Veröffentlichungsserver vornehmen. Andernfalls schlägt die Übermittlung eines Formulars fehlgeschlagen.

