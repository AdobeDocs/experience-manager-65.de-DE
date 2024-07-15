---
title: Salesforce-Integration mit AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses
description: Schritte zur Integration von Salesforce-Integration mit AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses
exl-id: 4c356aa6-ebd4-40b9-89e3-bc4519e4a7c5
solution: Experience Manager, Experience Manager Forms
feature: Form Data Model
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 100%

---

# Integration von Salesforce mithilfe des OAuth 2.0-Client-Anmeldedatenflusses {#configure-salesforce-with-ouath-2.0-client-credential}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Sie können OAuth 2.0-Client-Anmeldeinformationen verwenden, um AEM Forms in die Salesforce-Anwendung zu integrieren. OAuth 2.0-Client-Anmeldeinformationen sind eine standardmäßige und sichere Methode für die direkte Kommunikation ohne Benutzerbeteiligung.

![Workflow beim Festlegen der Kommunikation zwischen AEM Forms und der Salesforce-Anwendung](/help/forms/using/assets/salesforce-workflow.png)

AEM Forms tauscht die in der Salesforce Connect-Anwendung definierten Client-Anmeldeinformationen (Consumer Key und Consumer Secret) aus, um ein Zugriffs-Token zu erhalten.

Die Verwendung von OAuth 2.0-Client-Anmeldeinformationen für die Authentifizierung hat gegenüber Authorization Code Flow mehrere Vorteile:

* Die Authentifizierung mit OAuth 2.0-Client-Anmeldeinformationen ermöglicht mehr als fünf Verbindungen pro Person.
* Die AEM-Datenquellenkonfiguration arbeitet weiterhin an der Deaktivierung, Zugriffsänderungen und Kennwortaktualisierung für AEM-Benutzende.

## Voraussetzungen {#prerequisites}

Tun Sie Folgendes, bevor Sie die Kommunikation zwischen einer Salesforce-Anwendung und einer AEM-Umgebung einrichten:

* Erstellen Sie eine [mit Salesforce verbundene App mit OAuth 2.0 Client Credential Flow](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5) sowie eine reine API-Benutzerin bzw. einen reinen API-Benutzer für Ihre Organisation und rufen Sie Consumer Key und Consumer Secret für die App ab.

* Stellen Sie sicher, dass Ihre Swagger-Datei entsprechend den APIs Ihrer Organisation konfiguriert ist. Sie können auch eine [Swagger-Datei komplett neu erstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=de), die auf die Nutzung in Ihrer AEM-Umgebung zugeschnitten ist.
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

Nun können Sie das [Formulardatenmodell erstellen](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html?lang=de), um die konfigurierte Datenquelle in Ihre adaptiven Formulare zu integrieren.
