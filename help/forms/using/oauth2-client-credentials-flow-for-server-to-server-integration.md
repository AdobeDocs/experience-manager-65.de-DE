---
title: Salesforce-Integration mit AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses
seo-title: Salesforce integration with AEM Forms using OAuth 2.0 client credentials flow
description: Schritte zur Integration von Salesforce mit AEM Forms mithilfe des Workflows für OAuth 2.0-Client-Anmeldeinformationen
seo-description: Steps to integrate Salesforce integration with AEM Forms using OAuth 2.0 client credentials flow
source-git-commit: cc0375f5b5616f82a73bd983a9da95225c51db99
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---


# Integration von Salesforce mithilfe des OAuth 2.0-Client-Anmeldedatenflusses  {#configure-salesforce-with-ouath-2.0-client-credential}

Zur Integration von AEM Forms in die Salesforce-Anwendung wird der Ablauf der OAuth 2.0-Client-Anmeldeinformationen verwendet. Es handelt sich um eine standardisierte und sichere Methode für die direkte Kommunikation ohne Benutzerbeteiligung. In diesem Ablauf tauscht die Client-Anwendung (AEM Formular) die in der Salesforce Connect-Anwendung definierten Client-Anmeldeinformationen aus, um ein Zugriffstoken zu erhalten. Die erforderlichen Client-Anmeldeinformationen umfassen den Consumer-Schlüssel und das Consumer-Geheimnis.

## Vorteile der Integration von Salesforce mit AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses {#advantages-of-integrating-saleforce-aemforms}

AEM Forms unterstützt die Integration von Salesforce in den Autorisierungscode-Fluss zusätzlich zum OAuth 2.0-Client-Anmeldedatenfluss. Im Ablauf des Autorisierungscodes für OAuth 2.0 erhält die Client-Anwendung (AEM Forms) im Namen eines Salesforce-Benutzers Ressourcenzugriff, der einige Einschränkungen aufweist:

* Es sind maximal fünf Verbindungen pro Benutzer zulässig. Weitere Verbindungen widerrufen automatisch ältere Verbindungen.
* Wenn ein Benutzer deaktiviert ist, den Zugriff verliert oder ein Kennwort aktualisiert, funktioniert die AEM Datenquellenkonfiguration nicht mehr.

## Voraussetzungen {#prerequisites}

Um Daten zwischen Salesforce- und AEM-Umgebungen abzurufen und abzurufen, sind bestimmte Voraussetzungen erforderlich, bevor Sie fortfahren:

+++ **Einrichten einer mit Saleforce verbundenen Anwendung mit Client-Anmeldedaten-Fluss und einem reinen API-Benutzer**

Es ist erforderlich, eine Salesforce-verbundene App mit einem OAuth 2.0-Client-Anmeldedatenfluss und einen Nur-API-Benutzer für Ihre Organisation zu erstellen. Ausführliche Anweisungen finden Sie im Artikel [OAuth 2.0 Client Credentials Flow für Server-zu-Server-Integration](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5). Diese Schritte helfen Ihnen beim Abrufen des Consumer-Schlüssels und des Consumer-Geheimnisses.

>[!NOTE]
>
> Notieren Sie sich bei der Erstellung einer AEM Datenquellenkonfiguration unbedingt den Consumer-Schlüssel und das Consumer-Geheimnis.

+++

+++ **Swagger-Datei erstellen**

Swagger ist ein Open-Source-Satz von Regeln, Spezifikationen und Tools zur Entwicklung und Beschreibung von RESTful-APIs. [Swagger-Datei erstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html) vor der Integration von Salesforce mit AEM Forms.

>[!NOTE]
>
> AEM 6.5 unterstützt nur Swagger 2.0-Dateispezifikationen.

+++

## Schritte zum Konfigurieren von Salesforce mit Client-Anmeldedaten-Fluss {#steps-to-create-aem-datasource-configuration}

1. Melden Sie sich bei Ihrer -Autoreninstanz an.
1. Navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**.
1. Wählen Sie den Konfigurationsordner aus.
1. Klicken **[!UICONTROL Erstellen]** und **[!UICONTROL Erstellen der Datenquellenkonfiguration]** angezeigt.
1. Geben Sie die **[!UICONTROL Titel]** und wählen Sie die **[!UICONTROL Diensttyp]** as **[!UICONTROL RESTful-Dienst]**.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie die **[!UICONTROL Swagger Source]** as **[!UICONTROL Datei].**
   >[!NOTE]
   >
   > Sobald die Swagger-Datei ausgewählt ist, werden das Schema, der Hostname und der Basispfad automatisch ausgefüllt.

1. Laden Sie die erstellte Swagger-Datei von Ihrem lokalen Computer hoch, indem Sie auf **[!UICONTROL Durchsuchen]**.
1. Wählen Sie die **[!UICONTROL Authentifizierungstyp]** as **[!UICONTROL OAuth 2.0]** und **[!UICONTROL Authentifizierungseinstellungen]** angezeigt.
1. Wählen Sie die **[!UICONTROL Fördertyp]** as **[!UICONTROL Client-Anmeldedaten]**.
1. Geben Sie die **[!UICONTROL Client-ID]** und **[!UICONTROL Client Secret]** von der Salesforce Connect-App abgerufen.
1. Geben Sie die **[!UICONTROL Zugriffstoken-URL]** im Format
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Jede Organisation hat einen eigenen spezifischen Domänennamen.

1. Klicken **[!UICONTROL Verbindung testen]**.
1. Wenn die Verbindung erfolgreich hergestellt wurde, klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]** Schaltfläche.

Jetzt können Sie [Formulardatenmodell erstellen](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html?lang=en) , um die konfigurierte Datenquelle in Ihr adaptives Formular zu integrieren.


