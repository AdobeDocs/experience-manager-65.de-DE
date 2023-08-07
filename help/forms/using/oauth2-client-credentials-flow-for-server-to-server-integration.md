---
title: Salesforce-Integration mit AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses
seo-title: Salesforce integration with AEM Forms using OAuth 2.0 client credentials flow
description: Schritte zur Integration von Salesforce-Integration mit AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses
seo-description: Steps to integrate Salesforce integration with AEM Forms using OAuth 2.0 client credentials flow
exl-id: 31f2ccf8-1f4f-4d88-8c5f-ef1b7d1bfb4f
source-git-commit: f11bb43d914a43431cab408ca77690b6ba528a06
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 52%

---

# Integration von Salesforce mithilfe des OAuth 2.0-Client-Anmeldedatenflusses {#configure-salesforce-with-ouath-2.0-client-credential}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM 6.5 | Dieser Artikel |

Sie können OAuth 2.0-Client-Anmeldeinformationen verwenden, um AEM Forms in die Salesforce-Anwendung zu integrieren. OAuth 2.0-Client-Anmeldeinformationen sind eine standardmäßige und sichere Methode für die direkte Kommunikation ohne Benutzerbeteiligung.

![Workflow beim Festlegen der Kommunikation zwischen AEM Forms und Salesforce](/help/forms/using/assets/salesforce-workflow.png)

AEM Forms tauscht die in der Salesforce Connect-Anwendung definierten Client-Anmeldeinformationen (Consumer Key und Consumer Secret) aus, um ein Zugriffstoken zu erhalten.

Die Verwendung von OAuth 2.0-Client-Anmeldeinformationen für die Authentifizierung über die Authentifizierung für die Flussauthentifizierung des Autorisierungscodes bietet mehrere Vorteile:

* Die Authentifizierung mit OAuth 2.0-Client-Anmeldeinformationen ermöglicht mehr als fünf Verbindungen pro Benutzer.
* AEM Datenquellenkonfiguration arbeitet weiterhin an der Deaktivierung, Zugriffsänderungen und Kennwortaktualisierung für einen AEM Benutzer.

## Voraussetzungen {#prerequisites}

Bevor Sie die Kommunikation zwischen einer Salesforce-Anwendung und einer AEM Umgebung einrichten:

* Erstellen Sie eine [Salesforce-verbundene App mit OAuth 2.0-Client-Anmeldefluss](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5) und einen reinen API-Benutzer für Ihr Unternehmen erstellen und das Consumer-Schlüssel- und das Consumer-Geheimnis für die App abrufen.

* Stellen Sie sicher, dass Ihre Swagger-Datei entsprechend den APIs Ihres Unternehmens konfiguriert ist. Alternativ können Sie auch [Swagger-Datei erstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=de) von Grund auf neu, auf die Nutzung in Ihrer AEM-Umgebung zugeschnitten.
>[!NOTE]
>
> AEM 6.5 unterstützt nur Swagger 2.0-Dateispezifikationen.

+++

## Schritte zum Konfigurieren von Salesforce mit Client-Anmeldedatenfluss {#steps-to-create-aem-datasource-configuration}

1. Melden Sie sich bei Ihrer Authoring-Instanz an.
1. Wechseln Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Datenquellen]**.
1. Wählen Sie den Konfigurationsordner aus.
1. Klicken Sie auf **[!UICONTROL Erstellen]** und das Bedienfeld **[!UICONTROL Datenquellenkonfiguration erstellen]** erscheint.
1. Geben Sie den **[!UICONTROL Titel]** an und wählen Sie den **[!UICONTROL Diensttyp]** als **[!UICONTROL RESTful-Dienst]**.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie **[!UICONTROL Swagger Source]** als **[!UICONTROL Datei].**
   >[!NOTE]
   >
   > Sobald die Swagger-Datei ausgewählt ist, werden das Schema, der Host-Name und der Basispfad automatisch ausgefüllt.

1. Laden Sie die erstellte Swagger-Datei von Ihrem lokalen Computer hoch, indem Sie auf **[!UICONTROL Durchsuchen]** klicken.
1. Wählen Sie **[!UICONTROL Authentifizierungstyp]** als **[!UICONTROL OAuth 2.0]** und das Bedienfeld **[!UICONTROL Authentifizierungs-Einstellungen]** erscheint.
1. Wählen Sie **[!UICONTROL Grant-Typ]** als **[!UICONTROL Client-Anmeldedaten]**.
1. Geben Sie die **[!UICONTROL Client-ID]** und das **[!UICONTROL Client-Geheimnis]** an, das Sie von der mit Salesforce verbundenen App erhalten haben.
1. Geben Sie die **[!UICONTROL Zugriffstoken-URL]** im folgenden Format an:
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Jede Organisation hat einen eigenen, spezifischen Domain-Namen.

1. Klicken Sie auf **[!UICONTROL Verbindung testen]**.
1. Wenn die Verbindung erfolgreich hergestellt wurde, klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]**.

Jetzt können Sie [Formulardatenmodell erstellen](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html?lang=de) , um die konfigurierte Datenquelle in Ihre adaptive Forms zu integrieren.
