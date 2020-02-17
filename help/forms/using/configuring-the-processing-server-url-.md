---
title: AEM DS-Einstellungen konfigurieren
seo-title: AEM DS-Einstellungen konfigurieren
description: Sie müssen die Verarbeitungsserver-URL angeben, bevor Sie ein Formular senden.
seo-description: Sie müssen die Verarbeitungsserver-URL angeben, bevor Sie ein Formular senden.
uuid: 55a6d434-7352-48a8-8387-8a5c1a48fafc
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: a7387bd3-8b31-4bd0-a861-daa8f7cb2d05
docset: aem65
translation-type: tm+mt
source-git-commit: 413af4ef9bc3652e05da78d622183bcf20a8bee7

---


# AEM DS-Einstellungen konfigurieren{#configuring-aem-ds-settings}

Dieser Artikel beschreibt, wie Sie den **AEM DS-Einstellungen-Dienst** konfigurieren. Diese Einstellung kann in mehreren Szenarien verwendet werden, zum Beispiel:

* In Correspondence Management

   * Für die Konfiguration des AEM Forms-Workflow
   * Achten Sie bei der Verwendung von Formularportals für Remote-Verwendung, darauf, dass Sie Entwurf/der Übermittlung speichern

* In den adaptiven Formularen für Fälle, bei denen ein adaptives Formular von der Veröffentlichungsinstanz gesendet wird

Führen Sie die folgenden Schritte aus, um die **[!UICONTROL AEM DS-Einstellungen]** zu konfigurieren:

1. Öffnen Sie Configuration Manager mithilfe der URL in der Veröffentlichungsinstanz:\
   *https://localhost:port/system/console/configMgr*.

   ![AEM Web Console-Konfiguration](assets/web_configuration_console_new.png)

1. In the **[!UICONTROL Adobe Experience Manager Web Console Configuration]** window, locate and click the **[!UICONTROL AEM DS Settings]** option.

   ![DS-Einstellungen](assets/ds_settings_new.png)

1. Das Fenster **[!UICONTROL AEM DS-Einstellungendienst]** zeigt die allgemeinen Konfigurationseinstellungen für AEM DS-Komponenten.

   ![DS-Einstellungsdienst](assets/ds_settings_service_new.png)

1. Fügen Sie die folgenden Informationen in die entsprechenden Felder ein:

   **[!UICONTROL Verarbeitungsserver-URL]**: Der Verarbeitungsserver ist der Server, auf dem der Forms- oder AEM-Workflow ausgelöst werden muss. Dies kann mit der URL der AEM-Autoreninstanz oder der anderen Server-URL (d. h. https://localhost:port/) identisch sein.

   **[!UICONTROL Verarbeitungsserver-Benutzername]**: Benutzername des Workflow-Benutzers [basierend auf der verwendeten Server-URL]

   **[!UICONTROL Verarbeitungs-Serverkennwort]**: Das Kennwort des Workflow-Benutzers

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Bei der Verwendung von Formularen oder AEM-Workflows ist es notwendig, den DS-Einstellungendienst zu konfigurieren, bevor Sie eine Übertragung vom Veröffentlichungsserver vornehmen. Andernfalls schlägt die Übermittlung eines Formulars fehlgeschlagen.


