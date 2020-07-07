---
title: Konfigurieren von Datenquellen
seo-title: Konfigurieren von Datenquellen
description: Erfahren Sie, wie Sie verschiedene Arten von Datenquellen konfigurieren und das Erstellen von Formulardatenmodellen nutzen können.
seo-description: Erfahren Sie, wie Sie verschiedene Arten von Datenquellen konfigurieren und das Erstellen von Formulardatenmodellen nutzen können.
uuid: 12360c8c-b596-4f9b-837a-10a8ff5c7448
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9d78a6dc-fc9c-415b-b817-164fe6648b30
docset: aem65
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '1554'
ht-degree: 55%

---


# Konfigurieren von Datenquellen{#configure-data-sources}

![](do-not-localize/data-integeration.png)

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herzustellen. Die folgenden Datenquellen werden standardmäßig unterstützt. Es ist jedoch möglich, mit nur wenigen Anpassungen auch andere Datenquellen zu integrieren.

* Relationale Datenbanken: MySQL, Microsoft SQL Server, IBM DB2 und Oracle RDBMS
* AEM-Benutzerprofil 
* RESTful Webservices 
* SOAP-basierte Webservices
* OData-Dienstleistungen

Die Datenintegration unterstützt standardmäßig die Authentifizierungstypen OAuth2.0, Basic Authentication und API Key und ermöglicht die Implementierung der benutzerdefinierten Authentifizierung für den Zugriff auf Webdienste. RESTful-, SOAP-basierte und OData-Dienste werden in AEM-Cloud-Services, JDBC für relationale Datenbanken und der Connector für AEM-Profile dagegen in der AEM-Webkonsole konfiguriert.

## Konfigurieren relationaler Datenbanken {#configure-relational-database}

Sie können relationale Datenbanken mithilfe der AEM Web Console-Konfiguration konfigurieren. Gehen Sie folgendermaßen vor:

1. Wechseln Sie zu AEM-Webkonsole unter https://server:host/system/console/configMgr.
1. Suchen Sie die Konfiguration **[!UICONTROL Apache Sling Connection Pooled DataSource]**. Tippen Sie, um die Konfiguration im Bearbeitungsmodus zu öffnen.
1. Geben Sie im Konfigurationsdialogfeld die Details für die Datenbank an, die Sie konfigurieren möchten, z. B.:

   * Name der Datenquelle
   * Datenquellendienst-Eigenschaft, in der der Name der Datenquelle gespeichert wird
   * Java-Klassenname für den JDBC-Treiber
   * JDBC-Verbindungs-URI
   * Benutzername und Kennwort zum Herstellen der Verbindung zum JDBC-Treiber

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie vertrauliche Informationen wie Kennwörter verschlüsseln, bevor Sie die Datenquelle konfigurieren. Gehen Sie zum Verschlüsseln wie folgt vor:
   >
   >    
   >    
   >    1. Go to https://&#39;[server]:[port]&#39;/system/console/crypto.
   >    1. Geben Sie im Feld **[!UICONTROL Plain Text]** das Kennwort bzw. die zu verschlüsselnde Zeichenfolge ein und klicken Sie auf **[!UICONTROL Protect]**.

   >    
   >    
   >    
   >Der verschlüsselte Text wird im Feld Geschützter Text angezeigt, das Sie in der Konfiguration angeben können.

1. Aktivieren Sie **[!UICONTROL Test on Borrow]** oder **[!UICONTROL Test on Return]**, um festzulegen, dass die Objekte vor der Entnahme oder bei der Rückgabe aus dem bzw. in den Pool validiert werden sollen.
1. Geben Sie eine SQL SELECT-Abfrage in das Feld **[!UICONTROL Validation Query]** ein, damit Verbindungen aus dem Pool validiert werden. Die Abfrage muss mindestens eine Zeile zurückgeben. Legen Sie die für Ihre Datenbank geeignete Option fest:

   * SELECT 1 (MySQL und MS SQL)
   * SELECT 1 from dual (Oracle)

1. Tap **[!UICONTROL Save]** to save the configuration.

## AEM-Benutzerprofil konfigurieren {#configure-aem-user-profile}

Sie können das AEM-Benutzerprofil mithilfe der User Profile Connector-Konfiguration in der AEM-Webkonsole konfigurieren. Gehen Sie folgendermaßen vor:

1. Go to AEM web console at https://&#39;[server]:[port]&#39;system/console/configMgr.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and tap to open the configuration in edit mode.
1. Im Dialogfeld für die Benutzerprofil-Connector-Konfiguration können Sie Benutzerprofileigenschaften hinzufügen, entfernen oder aktualisieren. Die angegebenen Eigenschaften sind zur Verwendung im Formulardatenmodell verfügbar. Verwenden Sie das folgende Format, um Benutzerprofileigenschaften festzulegen:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Beispiele:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The ***** in the above example denotes all nodes under the `profile/empLocation/` node in AEM user profile in CRXDE structure. It means that the form data model can access the `city` property of type `string` present in any node under the `profile/empLocation/` node. Die Knoten, die die angegebene Eigenschaft enthalten, müssen jedoch einer einheitlichen Struktur entsprechen.

1. Tap **[!UICONTROL Save]** to save the configuration.

## Ordner für Cloud-Dienstkonfigurationen konfigurieren {#cloud-folder}

>[!NOTE]
Zum Konfigurieren von Cloud-Diensten für RESTful-, SOAP- und OData-Dienste ist eine Konfiguration des Ordners für Cloud-Dienste erforderlich.

All cloud service configurations in AEM are consolidated in the `/conf` folder in AEM repository. Standardmäßig enthält der Ordner `conf` den Ordner `global`, in dem Sie Cloud-Dienst-Konfigurationen erstellen können. Sie müssen ihn jedoch manuell für Cloud-Konfigurationen aktivieren. Sie können auch zusätzliche Ordner in `conf` erstellen, um Cloud-Dienstkonfigurationen zu erstellen und zu organisieren.

Konfigurieren des Ordners für Cloud-Dienstkonfigurationen:

1. Go to **[!UICONTROL Tools > General > Configuration Browser]**.
1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud-Dienstkonfigurationen zu erstellen und zu konfigurieren.

   1. Wählen Sie im **[!UICONTROL Konfigurationsbrowser]** den Ordner `global`und tippen Sie auf **[!UICONTROL Eigenschaften]**.

   1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.

   1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Tippen Sie im **[!UICONTROL Konfigurationsbrowser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
1. Tap **[!UICONTROL Create]** to create the folder enabled for cloud service configurations.

## RESTful-Webdienste konfigurieren {#configure-restful-web-services}

RESTful web service can be described using [Swagger specifications](https://swagger.io/specification/) in JSON or YAML format in a Swagger definition file. Um RESTful-Webdienst in AEM cloud services zu konfigurieren, stellen Sie sicher, dass die Swagger-Datei im Dateisystem oder die URL, unter der die Datei gehostet wird, vorhanden ist.

Gehen Sie wie folgt vor, um RESTful-Dienste zu konfigurieren:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud-Dienste > Datenquellen]**. Tippen Sie auf , um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   See [Configure folder for cloud service configurations](../../forms/using/configure-data-sources.md#cloud-folder) for information about creating and configuring a folder for cloud service configurations.

1. Tap **[!UICONTROL Create]** to open the **[!UICONTROL Create Data Source Configuration wizard]**. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Dienst]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]**, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie die folgenden Details für den RESTful-Dienst an:

   * Wählen Sie in der Dropdown-Liste &quot;Swagger-Quelle&quot;die Option &quot;URL&quot;oder &quot;Datei&quot;und geben Sie entsprechend die Swagger-URL zur Swagger-Definitionsdatei an oder laden Sie die Swagger-Datei aus Ihrem lokalen Dateisystem hoch.
   * Basierend auf der Swagger-Quelleingabe werden die folgenden Felder mit Werten vorausgefüllt:

      * Regelung: Die von der REST-API verwendeten Übertragungsprotokolle. Die Anzahl der in der Dropdown-Liste angezeigten Schematypen hängt von den in der Swagger-Quelle definierten Schemata ab.
      * Host: Der Domänenname oder die IP-Adresse des Hosts, der die REST-API bereitstellt. Dies ist ein Pflichtfeld.
      * Basispfad: Das URL-Präfix für alle API-Pfade. Dies ist ein optionales Feld.\
         Bearbeiten Sie bei Bedarf die vorausgefüllten Werte für diese Felder.
   * Wählen Sie den Authentifizierungstyp aus — Keine, OAuth2.0, einfache Authentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung — , um auf den RESTful-Dienst zuzugreifen und dementsprechend Details zur Authentifizierung anzugeben.

   Wenn Sie als Authentifizierungstyp &quot; **[!UICONTROL API-Schlüssel]** &quot;auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungsheader oder als Abfrage-Parameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste &quot; **[!UICONTROL Position]** &quot;und geben Sie den Namen der Kopfzeile bzw. des Abfrage-Parameters im Feld **[!UICONTROL Parametername]** entsprechend an.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Dienst zu erstellen.

## SOAP-Webdienste konfigurieren {#configure-soap-web-services}

SOAP-basierte Webdienste werden mithilfe von [WSDL-Spezifikationen (Web Services Description Language)](https://www.w3.org/TR/wsdl) beschrieben. Um den SOAP-basiertenWebdienst in den AEM-Cloud-Services zu konfigurieren, benötigen Sie die WSDL-URL für den Webdienst. Gehen Sie dann wie folgt vor:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud-Dienste > Datenquellen]**. Tippen Sie auf , um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   See [Configure folder for cloud service configurations](../../forms/using/configure-data-sources.md#cloud-folder) for information about creating and configuring a folder for cloud service configurations.

1. Tap **[!UICONTROL Create]** to open the **[!UICONTROL Create Data Source Configuration wizard]**. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL SOAP Web-Dienst]** aus der **[!UICONTROL Dropdown-Liste Service-Typ]**, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie Folgendes für den SOAP-Webdienst an:

   * WSDL-URL für den Webdienst.
   * Dienstendpunkt. Geben Sie in diesem Feld einen Wert ein, um den in WSDL erwähnten Dienstendpunkt zu überschreiben.
   * Wählen Sie den Authentifizierungstyp aus — Keine, OAuth2.0, einfache Authentifizierung, benutzerdefinierte Authentifizierung oder X509-Token — , um auf den SOAP-Dienst zuzugreifen und die Details zur Authentifizierung anzugeben.

      Wenn Sie als Authentifizierungstyp &quot;X509-Token&quot;auswählen, konfigurieren Sie das X509-Zertifikat. Weitere Informationen finden Sie unter [Einrichten von Zertifikaten](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Geben Sie den KeyStore-Alias für das X509-Zertifikat im Feld **[!UICONTROL Key Alias]** an. Geben Sie im Feld &quot; **[!UICONTROL Zeit bis zum Live]** &quot;die Zeit in Sekunden an, bis die Authentifizierungsanforderung gültig bleibt. Optional können Sie den Nachrichtentext oder die Zeitstempelüberschrift oder beides signieren.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den SOAP-Webdienst zu erstellen.

## OData-Dienste konfigurieren {#config-odata}

Ein OData-Dienst wird anhand seiner Dienststamm-URL identifiziert. Stellen Sie zum Konfigurieren eines OData-Dienstes in AEM-Cloud-Services sicher, dass Sie die Dienststamm-URL für den Service haben, und gehen Sie folgendermaßen vor:

>[!NOTE]
Eine schrittweise Anleitung zum Konfigurieren von Microsoft Dynamics 365, online oder On-Premise, finden Sie unter [Microsoft Dynamics OData-Konfiguration ](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud-Dienste > Datenquellen]**. Tippen Sie auf , um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   See [Configure folder for cloud service configurations](../../forms/using/configure-data-sources.md#cloud-folder) for information about creating and configuring a folder for cloud service configurations.

1. Tap **[!UICONTROL Create]** to open the **[!UICONTROL Create Data Source Configuration wizard]**. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL OData-Dienst]** aus der **[!UICONTROL Dropdown-Liste Service-Typ]**, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie die folgenden Details für den OData-Dienst an:

   * Dienststamm-URL für den zu konfigurierenden OData-Dienst.
   * Wählen Sie den Authentifizierungstyp aus — Keine, OAuth2.0, einfache Authentifizierung oder benutzerdefinierte Authentifizierung — , um auf den OData-Dienst zuzugreifen und die Details zur Authentifizierung anzugeben.

   >[!NOTE]
   Sie müssen den OAuth 2.0-Authentifizierungstyp auswählen, um eine Verbindung mit Microsoft Dynamics-Diensten herzustellen, die den OData-Endpunkt als Dienststamm nutzen.

1. Tap **Create** to create the cloud configuration for the OData service.

## Nächste Schritte {#next-steps}

Sie haben die Datenquellen konfiguriert. Als Nächstes können Sie ein Formulardatenmodell erstellen oder, falls Sie bereits ein Formulardatenmodell ohne Datenquelle erstellt haben, können Sie es den soeben konfigurierten Datenquellen zuordnen. See [Create form data model](/help/forms/using/create-form-data-models.md) for details.
