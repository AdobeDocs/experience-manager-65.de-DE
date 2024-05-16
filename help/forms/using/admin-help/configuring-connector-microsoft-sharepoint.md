---
title: Konfigurieren des Connectors für Microsoft SharePoint
description: Konfigurieren Sie Connector für Microsoft SharePoint, um die Kommunikation zwischen AEM Forms und Microsoft SharePoint zu ermöglichen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: a8be58f1-1961-4bf5-aaad-feb4489fb389
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '202'
ht-degree: 100%

---

# Connector für Microsoft SharePoint konfigurieren {#configuring-connector-for-microsoft-sharepoint}

Connector für Microsoft SharePoint ermöglicht die Kommunikation zwischen AEM Forms und Microsoft SharePoint. Weitere Hintergrundinformationen finden Sie unter „Connector-Dienste für ECM“ in der [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für Microsoft SharePoint“.
1. Geben Sie die folgenden Einstellungen für Ihren SharePoint-Server an:

   **Hostname des SharePoint-Servers:** Die Hostnamen-Anschlussnummer der Webanwendung auf dem SharePoint-Server im Format `[hostname]:'port'`.

   **Benutzername:** Das Benutzerkonto, das zum Herstellen einer Verbindung mit dem SharePoint-Server verwendet wird.

   **Kennwort:** Das Kennwort für das Benutzerkonto, das zum Herstellen einer Verbindung mit dem SharePoint-Server verwendet wird.

   **Domain-Name:** Die Domain, in der sich der SharePoint-Server befindet.

1. Klicken Sie auf Speichern.

## Microsoft SharePoint-Konfigurationsdienst {#microsoft-sharepoint-configuration-service}

Mit dem Microsoft SharePoint-Konfigurations-Service (`(MSSharePointConfigService)`) können Sie Anmeldedaten für den AEM Forms-Benutzer angeben, der über die Berechtigung zum Identitätswechsel verfügt. Weitere Informationen zu Berechtigungen zum Identitätswechsel finden Sie unter [Connector für Microsoft SharePoint konfigurieren](https://help.adobe.com/de_DE/AEMForms/6.1/SharePointConfig/index.html). Führen Sie folgende Schritte aus, um die Einstellungen für `MSSharePointConfigService` anzugeben:

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Durchlaufen Sie die Liste der Dienste und klicken Sie auf `MSSharePointConfigService`.
1. Geben Sie auf der Seite „Konfiguration“ die folgenden Einstellungen an:

   * Benutzername für Benutzer mit Berechtigungen zum Identitätswechsel
   * Kennwort für oben genannten Benutzer

1. Klicken Sie auf Speichern.
