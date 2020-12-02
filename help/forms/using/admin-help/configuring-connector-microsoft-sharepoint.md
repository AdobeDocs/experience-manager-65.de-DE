---
title: Connector für Microsoft SharePoint konfigurieren
seo-title: Connector für Microsoft SharePoint konfigurieren
description: Konfigurieren Sie Connector für Microsoft SharePoint, um die Kommunikation zwischen AEM Forms und Microsoft SharePoint zu aktualisieren.
seo-description: Konfigurieren Sie Connector für Microsoft SharePoint, um die Kommunikation zwischen AEM Forms und Microsoft SharePoint zu aktualisieren.
uuid: f1561b41-da20-4220-b13a-e78472a9449f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 0ec881c9-8dcc-4847-9edf-24d9e6c4a7ea
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 63%

---


# Connector für Microsoft SharePoint konfigurieren {#configuring-connector-for-microsoft-sharepoint}

Connector für Microsoft SharePoint aktiviert die Kommunikation zwischen AEM Forms und Microsoft SharePoint. Weitere Hintergrundinformationen finden Sie im Abschnitt über Connectors für ECM in [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63).

1. Wählen Sie in Administration Console „Dienste“ > „Connector für Microsoft SharePoint“.
1. Geben Sie die folgenden Einstellungen für Ihren SharePoint-Server an:

   **Hostname des SharePoint-Servers:** Die Anschlussnummer des Hostnamens der Webanwendung auf dem SharePoint-Server im Format  `[hostname]:'port'`.

   **Benutzername:** Das Benutzerkonto, mit dem eine Verbindung zum SharePoint-Server hergestellt wird.

   **Kennwort:** Kennwort für das Benutzerkonto, mit dem eine Verbindung zum SharePoint-Server hergestellt wird

   **Domänenname:** Domäne, auf der sich der SharePoint-Server befindet.

1. Klicken Sie auf Speichern.

## Microsoft SharePoint-Konfigurationsdienst {#microsoft-sharepoint-configuration-service}

Mit dem Microsoft SharePoint-Konfigurationsdienst `(MSSharePointConfigService)` können Sie Anmeldeinformationen für den AEM Forms-Benutzer angeben, der über die Berechtigung zum Identitätswechsel verfügt. Weitere Informationen zu Berechtigungen zum Identitätswechsel finden Sie unter [Connector für Microsoft SharePoint konfigurieren](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). Führen Sie folgende Schritte aus, um die Einstellungen für `MSSharePointConfigService` anzugeben:

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Durchlaufen Sie die Liste der Dienste und klicken Sie auf `MSSharePointConfigService`.
1. Geben Sie auf der Seite „Konfiguration“ folgende Einstellungen an:

   * Benutzername für einen Benutzer mit Berechtigungen zum Identitätswechsel
   * Kennwort für den oben genannten Benutzer

1. Klicken Sie auf Speichern.

