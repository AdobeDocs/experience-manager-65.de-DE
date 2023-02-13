---
title: Konfigurieren von Datenquellen
seo-title: Configure data sources
description: Erfahren Sie, wie Sie verschiedene Arten von Datenquellen konfigurieren und das Erstellen von Formulardatenmodellen nutzen können.
seo-description: Learn how to configure different types of data sources and leverage to create form data models.
uuid: 12360c8c-b596-4f9b-837a-10a8ff5c7448
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9d78a6dc-fc9c-415b-b817-164fe6648b30
docset: aem65
feature: Form Data Model
exl-id: 7a1d9d57-66f4-4f20-91c2-ace5a71a52f2
source-git-commit: e4aaef48ce7d6e49e9a76f78a74b7dea127f6cce
workflow-type: ht
source-wordcount: '2042'
ht-degree: 100%

---

# Konfigurieren von Datenquellen{#configure-data-sources}

![Datenintegration](do-not-localize/data-integeration.png)

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herzustellen. Die folgenden Datenquellen werden standardmäßig unterstützt. Es ist jedoch möglich, mit nur wenigen Anpassungen auch andere Datenquellen zu integrieren.

* Relationale Datenbanken: MySQL, Microsoft SQL Server, IBM DB2, Oracle RDBMS und Sybase
* AEM-Benutzerprofil 
* RESTful-Webservices
* SOAP-basierte Webservices
* OData-Services

Die Datenintegration unterstützt standardmäßig die Authentifizierungstypen OAuth2.0, Standardauthentifizierung sowie API-Schlüssel und ermöglicht die Implementierung benutzerdefinierter Authentifizierung für den Zugriff auf Webservices. RESTful-, SOAP-basierte und OData-Dienste werden in AEM-Cloud-Services, JDBC für relationale Datenbanken und der Connector für AEM-Profile dagegen in der AEM-Webkonsole konfiguriert.

## Konfigurieren relationaler Datenbanken {#configure-relational-database}

Sie können relationale Datenbanken mithilfe der AEM Web Console-Konfiguration konfigurieren. Gehen Sie folgendermaßen vor:

1. Wechseln Sie zur AEM-Web-Konsole unter `https://server:host/system/console/configMgr`.
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
   > 1. Wechseln Sie zu https://&#39;[server]:[port]&#39;/system/console/crypto.
   > 1. Geben Sie im Feld **[!UICONTROL Plain Text]** das Kennwort oder eine beliebige Zeichenfolge zum Verschlüsseln an und tippen Sie auf **[!UICONTROL Protect]**.
   >
   >Der verschlüsselte Text wird im Feld „Protected Text“ angezeigt, das Sie in der Konfiguration angeben können.

1. Aktivieren Sie **[!UICONTROL Test on Borrow]** oder **[!UICONTROL Test on Return]**, um festzulegen, dass die Objekte vor der Entnahme oder bei der Rückgabe aus dem bzw. in den Pool validiert werden sollen.
1. Geben Sie eine SQL SELECT-Abfrage in das Feld **[!UICONTROL Validation Query]** ein, damit Verbindungen aus dem Pool validiert werden. Die Abfrage muss mindestens eine Zeile zurückgeben. Legen Sie die für Ihre Datenbank geeignete Option fest:

   * SELECT 1 (MySQL und MS SQL)
   * SELECT 1 from dual (Oracle)

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

   >[!NOTE]
   >
   > Wenn Ihr Datenmodell in Forms ein Objekt enthält, das ein reserviertes Keyword für Ihre relationale Datenbank ist, kann dies zu Problemen beim Hinzufügen, Aktualisieren oder Abrufen von Daten führen. Vermeiden Sie daher die Verwendung solcher Objekte in Ihrem Formulardatenmodell.

## AEM-Benutzerprofil konfigurieren {#configure-aem-user-profile}

Sie können das AEM-Benutzerprofil mithilfe der User Profile Connector-Konfiguration in der AEM-Webkonsole konfigurieren. Gehen Sie folgendermaßen vor:

1. Wechseln Sie zur AEM-Web-Console unter https://&#39;[server]:[port]&#39;system/console/configMgr.
1. Suchen Sie nach **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** und tippen Sie darauf, um die Konfiguration im Bearbeitungsmodus zu öffnen.
1. Im Dialogfeld für die Benutzerprofil-Connector-Konfiguration können Sie Benutzerprofileigenschaften hinzufügen, entfernen oder aktualisieren. Die angegebenen Eigenschaften sind zur Verwendung im Formulardatenmodell verfügbar. Verwenden Sie das folgende Format, um Benutzerprofileigenschaften festzulegen:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Beispiele:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >Der **&#42;** im obigen Beispiel bezeichnet alle Knoten unter dem Knoten `profile/empLocation/` im AEM-Benutzerprofil in der CRXDE-Struktur. Das bedeutet, dass das Formulardatenmodell auf die Eigenschaft `city` des Typs `string` in jedem Knoten unter dem `profile/empLocation/`-Knoten zugreifen kann. Die Knoten, die die angegebene Eigenschaft enthalten, müssen jedoch einer einheitlichen Struktur entsprechen.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

## Einstellen des Ordners für Cloud-Service-Konfigurationen {#cloud-folder}

>[!NOTE]
>
>Die Konfiguration des Cloud Services-Ordners ist erforderlich, um Cloud Services für RESTful-, SOAP- und OData-Services zu konfigurieren.

Alle Cloud-Service-Konfigurationen in AEM werden im Ordner `/conf` im AEM-Repository zusammengefasst. Standardmäßig enthält der Ordner `conf` den Ordner `global`, in dem Sie Cloud Service-Konfigurationen erstellen können. Sie müssen ihn jedoch manuell für Cloud-Konfigurationen aktivieren. Sie können auch zusätzliche Ordner in `conf` erstellen, um Cloud Service-Konfigurationen zu erstellen und zu organisieren.

Konfigurieren des Ordners für Cloud Service-Konfigurationen:

1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.

   1. Wählen Sie im **[!UICONTROL Konfigurationsbrowser]** den Ordner `global` aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.

   1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.

   1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Tippen Sie im **[!UICONTROL Konfigurationsbrowser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den für Cloud Service-Konfigurationen aktivierten Ordner zu erstellen.

## Konfigurieren von RESTful-Webservices {#configure-restful-web-services}

Der RESTful-Webservice kann mithilfe von [Swagger-Spezifikationen](https://swagger.io/specification/) im JSON- oder YAML-Format in einer -Definitionsdatei beschrieben werden. Um den RESTful-Webservice in den AEM-Cloud-Services zu konfigurieren, müssen Sie entweder über die Swagger-Datei auf Ihrem Dateisystem verfügen oder über die URL, unter der die Datei gehostet wird.

Gehen Sie wie folgt vor, um RESTful-Services zu konfigurieren:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](../../forms/using/configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den RESTful-Service an:

   * Wählen Sie „URL“ oder „Datei“ aus der Dropdown-Liste der Swagger-Quelle aus und geben Sie dementsprechend die URL zur Swagger-Definitionsdatei an oder laden Sie die Swagger-Datei aus Ihrem lokalen Dateisystem hoch.
   * Auf Grundlage der Eingabe der Swagger-Quelle werden folgende Felder mit Werten vorbefüllt:

      * Schema: Die von der REST-API verwendeten Übertragungsprotokolle. Die Anzahl der in der Dropdown-Liste angezeigten Schematypen hängt von den Schemas ab, die in der Swagger-Quelle definiert wurden.
      * Host: Der Domain-Name oder die IP-Adresse des Hosts, der die REST-API bereitstellt. Dies ist ein Pflichtfeld.
      * Basispfad: Das URL-Präfix für alle API-Pfade. Dies ist ein optionales Feld.\

         Bearbeiten Sie bei Bedarf die vorbefüllten Werte für diese Felder.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0, Standardauthentifizierung, API-Schlüssel, benutzerdefinierte Authentifizierung oder gegenseitige Authentifizierung – für den Zugriff auf den RESTful-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   Wenn Sie **[!UICONTROL Gegenseitige Authentifizierung]** als Authentifizierungstyp angeben, lesen Sie [Zertifikatbasierte gegenseitige Authentifizierung für RESTful- und SOAP-Web-Services](#mutual-authentication).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Service zu erstellen.

### HTTP-Client-Konfiguration des Formulardatenmodells zur Leistungsoptimierung {#fdm-http-client-configuration}

Das Formulardatenmodell von [!DNL Experience Manager Forms] bei der Integration mit RESTful-Web-Services als Datenquelle umfasst HTTP-Client-Konfigurationen zur Leistungsoptimierung.
Führen Sie die folgenden Schritte aus, um den HTTP-Client des Formulardatenmodells zu konfigurieren:

1. Melden Sie sich bei der [!DNL Experience Manager Forms]-Autoreninstanz als Administrator an und wechseln Sie zu den [!DNL Experience Manager]-Webkonsolen-Paketen. Die Standard-URL lautet [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).

1. Tippen Sie auf **[!UICONTROL HTTP-Client-Konfiguration des Formulardatenmodells für REST-Datenquelle]**.

1. Im Dialogfeld [!UICONTROL HTTP-Client-Konfiguration des Formulardatenmodells für REST-Datenquelle]:

   * Geben Sie im Feld **[!UICONTROL Verbindungsgrenze insgesamt]** die maximal zulässige Anzahl von Verbindungen zwischen dem Formulardatenmodell und RESTful-Web-Services ein. Der Standardwert ist 20 Verbindungen.

   * Geben Sie die maximal zulässige Anzahl von Verbindungen für jede Route im Feld **[!UICONTROL Verbindungslimit pro Route]** an. Der Standardwert ist 2 Verbindungen.

   * Geben Sie die Dauer, für die eine persistente HTTP-Verbindung aufrechterhalten wird, im Feld **[!UICONTROL Aufrechterhalten]** an. Der Standardwert ist 15 Sekunden.

   * Geben Sie im Feld **[!UICONTROL Verbindungs-Zeitüberschreitung]** die Dauer an, für die der [!DNL Experience Manager Forms]-Server auf eine Verbindung wartet. Der Standardwert ist 10 Sekunden.

   * Geben Sie im Feld **[!UICONTROL Socket-Zeitüberschreitung]** den maximalen Zeitraum für die Inaktivität zwischen zwei Datenpaketen an. Der Standardwert ist 30 Sekunden.

## SOAP-Webservices konfigurieren {#configure-soap-web-services}

SOAP-basierte Webservices werden mithilfe von [WSDL-Spezifikationen (Web Services Description Language)](https://www.w3.org/TR/wsdl) beschrieben. Um den SOAP-basierten Web-dienst in den AEM-Cloud-Services zu konfigurieren, benötigen Sie die WSDL-URL für den Webdienst. Gehen Sie dann wie folgt vor:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](../../forms/using/configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL SOAP-Webservice]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie Folgendes für den SOAP-Webservice an:

   * WSDL-URL für den Webservice.
   * Service-Endpunkt. Geben Sie in diesem Feld einen Wert ein, um den in WSDL erwähnten Service-Endpunkt zu überschreiben.
   * Wählen Sie den Authentifizierungstyp – Keine, OAuth2.0, Standardauthentifizierung, benutzerdefinierte Authentifizierung, X509-Token oder gegenseitige Authentifizierung – für den Zugriff auf den SOAP-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

      Wenn Sie **[!UICONTROL X509-Token]** als Authentifizierungstyp verwenden, konfigurieren Sie das X509-Zertifikat. Weitere Informationen finden Sie unter [Einrichten von Zertifikaten](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Geben Sie im Feld **[!UICONTROL Schlüssel-Alias]** den KeyStore-Alias für das X509-Zertifikat an. Geben Sie im Feld **[!UICONTROL Gültigkeitsdauer]** die Zeit in Sekunden an, während der die Authentifizierungsanfrage gültig bleibt. Optional können Sie den Nachrichtentext oder die Kopfzeile des Zeitstempels oder beides signieren.

      Wenn Sie **[!UICONTROL Gegenseitige Authentifizierung]** als Authentifizierungstyp angeben, lesen Sie [Zertifikatbasierte gegenseitige Authentifizierung für RESTful- und SOAP-Web-Services](#mutual-authentication).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den SOAP-Webservice zu erstellen.

## Konfigurieren von OData-Services {#config-odata}

Ein OData-Service wird anhand seiner Service-Stamm-URL identifiziert. Stellen Sie zum Konfigurieren eines OData-Dienstes in AEM-Cloud-Services sicher, dass Sie die Dienststamm-URL für den Service haben, und gehen Sie folgendermaßen vor:

>[!NOTE]
>
>Das Formulardatenmodell unterstützt [OData Version 4](https://www.odata.org/documentation/).
>Eine schrittweise Anleitung zum Konfigurieren von Microsoft Dynamics 365, online oder On-Premise, finden Sie unter [Microsoft Dynamics OData-Konfiguration](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Datenquellen]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](../../forms/using/configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL OData-Service]** aus der **[!UICONTROL Dropdown-Liste „Service-Typ“]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den OData-Service an:

   * Service-Stamm-URL für den zu konfigurierenden OData-Service.
   * Wählen Sie den Authentifizierungstyp – Keine, OAuth2.0, Standardauthentifizierung oder benutzerdefinierte Authentifizierung – für den Zugriff auf den OData-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   >[!NOTE]
   >
   >Sie müssen den OAuth 2.0-Authentifizierungstyp auswählen, um eine Verbindung mit Microsoft Dynamics-Diensten herzustellen, die den OData-Endpunkt als Dienststamm nutzen.

1. Tippen Sie auf **Erstellen**, um die Cloudkonfiguration für den OData-Dienst zu erstellen.

## Zertifikatbasierte gegenseitige Authentifizierung für RESTful- und SOAP-Web-Services {#mutual-authentication}

Wenn Sie die gegenseitige Authentifizierung für das Formulardatenmodell aktivieren, authentifizieren sowohl die Datenquelle als auch der AEM-Server, der das Formulardatenmodell ausführt, die Identität des jeweils anderen, bevor Daten freigegeben werden. Sie können die gegenseitige Authentifizierung für REST- und SOAP-basierte Verbindungen (Datenquellen) verwenden. So konfigurieren Sie die gegenseitige Authentifizierung für ein Formulardatenmodell in Ihrer AEM Forms-Umgebung:

1. Laden Sie den privaten Schlüssel (Zertifikat) auf den [!DNL AEM Forms]-Server hoch. So laden Sie den privaten Schlüssel hoch:
   1. Melden Sie sich bei Ihrem [!DNL AEM Forms]-Server als Administrator an.
   1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**. Wählen Sie den `fd-cloudservice`-Benutzer und tippen Sie auf **[!UICONTROL Eigenschaften]**.
   1. Öffnen Sie die Registerkarte **[!UICONTROL Keystore]**, erweitern Sie die Option **[!UICONTROL Privaten Schlüssel aus KeyStore-Datei hinzufügen]**, laden Sie die KeyStore-Datei hoch, geben Sie die Aliasnamen und Kennwörter an und tippen Sie auf **[!UICONTROL Senden]**. Das Zertifikat wird hochgeladen.  Der Alias für den privaten Schlüssel wird im Zertifikat erwähnt und beim Erstellen des Zertifikats festgelegt.
1. Laden Sie das Vertrauenszertifikat in den Global Trust Store hoch. Hochladen des Zertifikats:
   1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Trust Store]**.
   1. Erweitern Sie die Option **[!UICONTROL Zertifikat aus CER-Datei hinzufügen]**, tippen Sie auf **[!UICONTROL Zertifikatsdatei auswählen]**, laden Sie das Zertifikat hoch und tippen Sie auf **[!UICONTROL Senden]**.
1. Konfigurieren Sie [SOAP](#configure-soap-web-services)- oder [RESTful](#configure-restful-web-services)-Web-Services als Datenquelle und wählen Sie als Authentifizierungstyp **[!UICONTROL Gegenseitige Authentifizierung]**. Wenn Sie mehrere selbstsignierte Zertifikate für `fd-cloudservice`-Benutzer konfigurieren, geben Sie den Schlüsselaliasnamen für das Zertifikat an.

## Nächste Schritte {#next-steps}

Sie haben die Datenquellen konfiguriert. Als Nächstes können Sie ein Formulardatenmodell erstellen oder, falls Sie bereits ein Formulardatenmodell ohne eine Datenquelle erstellt haben, können Sie es den schon konfigurierten Datenquellen zuordnen. Weitere Informationen finden Sie unter [Erstellen eines Formulardatenmodells](/help/forms/using/create-form-data-models.md).
