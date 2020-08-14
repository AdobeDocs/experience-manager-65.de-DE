---
title: Set up and configure We.Gov reference site
seo-title: Set up and configure We.Gov reference site
description: Install, configure, and customize an AEM Forms demo package.
seo-description: Install, configure, and customize an AEM Forms demo package.
uuid: 0a6ad8f9-0d38-40c3-ad8d-e705edef55f8
contentOwner: anujkapo
discoiquuid: fe5da0aa-d3a8-4b77-a447-9e429fdc2816
docset: aem65
translation-type: tm+mt
source-git-commit: 4c42e5e5274c41469824f12b228698a77bf5d4a6
workflow-type: tm+mt
source-wordcount: '4738'
ht-degree: 4%

---


# Set up and configure We.Gov reference site {#set-up-and-configure-we-gov-reference-site}

## Demo package details {#demo-package-details}

### Installation Prerequisites {#installation-prerequisites}

This package was created for **AEM Forms 6.4 OSGI Author**, has been tested, and is therefore supported on the following platform versions:

| AEM VERSION | AEM FORMS PACKAGE VERSION | STATUS |
|---|---|---|
| 6.4 | 5.0.86 | **Unterstützt** |
| 6.5 | 6.0.80 | **Unterstützt** |
| 6.5.3 | 6.0.122 | **Unterstützt** |

This package contains cloud configuration which support the following platform versions:

| CLOUD PROVIDER | SERVICE VERSION | STATUS |
|---|---|---|
| Adobe Sign | v5 API | **Unterstützt** |
| Microsoft Dynamics 365 | 1710 (9.1.0.3020) | **Unterstützt** |
| Adobe Analytics | v1.4 Rest API | **Unterstützt** |
**Überlegungen zur Paketinstallation:**

* The package is expected to be installed on a clean server, free of other demo packages or older demo package versions
* The package is expected to be installed on an OSGI server, running in Author mode

### What does this package include {#what-does-this-package-include}

The [AEM Forms We.Gov demo package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/we-gov-forms.pkg.all-2.0.2.zip) (**we-gov-forms.pkg.all-&lt;version>.zip**) comes as a package which includes several other subpackages and services. The package includes the following modules:

* **we-gov-forms.pkg.all-&lt;version>.zip** - *Complete demo package*

   * **we-gov-forms.ui.apps-&lt;version>.zip** *- Contains all components, client libraries, samples users, workflow models, etc.*

      * **we-gov-forms.core-&lt;version>.jar** - *Contains all OSGI services, custom workflow step implementation, etc.*

      * **we-gov-forms.derby&lt;version>.jar** - *Contains all OSGI services, database schema, etc.*

      * **core.wcm.components.all-2.0.4.zip** - *Collection of sample WCM components*

      * **grid-aem.ui.apps-1.0-SNAPSHOT.zip** - *AEM Sites Grid layout package for Sites page column control*
   * **we-gov-forms.ui.content-&lt;version>.zip** - *Contains all of the content, pages, images, forms, interactive communication assets, etc.*

   * **we-gov-forms.ui.analytics-&lt;version>.zip** - *Contains all We.Gov Forms Analytics data to be stored within the repository.*

   * **we-gov-forms.config.public-&lt;version>.zip** - *Enthält alle Standardkonfigurationsknoten einschließlich Platzhalter-Cloud-Konfigurationen, um Formulardatenmodelle und Service-Bindungsprobleme zu vermeiden.*


The assets included in this package include:

* AEM Site Pages with Editable Templates
* AEM Forms Adaptives Forms
* AEM Forms Interactive Communications (Print and Web Kanal)
* AEM Forms XDP Document of Record
* AEM Forms MS Dynamics Forms Data Model
* Adobe Sign-Integration
* AEM Workflow-Modell
* AEM Assets Sample Images
* Sample (In-Memory) Apache Derby Database
* Apache Derby Data Source (for use with Form Data Model)

## Demo package installation {#demo-package-installation}

This section contains information on installing the demo package.

### From Software Distribution {#from-software-distribution}

1. Open [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tap **[!UICONTROL Adobe Experience Manager]** available in the header menu.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. You can also use the **[!UICONTROL Search Downloads]** option to filter the results.
1. Tap the **we-gov-forms.pkg.all-&lt;version>.zip** package name, select **[!UICONTROL Accept EULA Terms]**, and tap **[!UICONTROL Download]**.
1. Open [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html)  and click **[!UICONTROL Upload Package]** to upload the package.
1. Select the package and click **[!UICONTROL Install]**.

   ![we gov forms package](assets/wegov_forms_package.jpg)

1. Allow the installation process to complete.
1. Navigate to *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html?wcmmode=disabled* to ensure the installation was successful.

### From a local ZIP file {#from-a-local-zip-file}

1. Download and locate the **we-gov-forms.pkg.all-&lt;version>.zip** file.
1. Navigate to *https://&lt;aemserver>:&lt;port>/crx/packmgr/index.jsp*.
1. Select the “Upload Package” option.

   ![Upload Package Option](assets/upload_package.jpg)

1. Use the file browser to navigate to and select the downloaded ZIP file.
1. Click “Open” to upload.
1. Once uploaded, select the “Install” option to install the package.

   ![Install WeGov Forms package](assets/wegov_forms_package-1.jpg)

1. Allow the installation process to complete.
1. Navigate to *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html?wcmmode=disabled* to ensure the installation was successful.

### Installing new package versions {#installing-new-package-versions}

To install new package version, follow the steps defined in 4.1 and 4.2. Installing a newer package version while another older package is already installed is possible, but it is recommended to uninstall the older package version first. To do so, follow the steps below.

1. Navigate to *https://&lt;aemserver>:&lt;port>/crx/packmgr/index.jsp*
1. Locate the older **we-gov-forms.pkg.all-&lt;version>.zip** file.
1. Wählen Sie die Option &quot;Mehr&quot;.
1. From the dropdown, select the “Uninstall” option.

   ![Uninstall WeGov package](assets/uninstall_wegov_forms_package.jpg)

1. On confirmation, select “Uninstall” again, and allow the uninstallation process to complete.

## Demo package configuration {#demo-package-configuration}

This section contains details and instructions on the post-deployment configuration of the demo package before presentation.

### Fictional user configuration {#fictional-user-configuration}

1. Navigate to *https://&lt;aemserver>:&lt;port>/libs/granite/security/content/groupadmin.html*
1. Login as an administrator in order to perform the tasks below.
1. Scroll down to the end of the page to load all user groups.
1. Search for “**workflow**”.
1. Select the “**workflow-users**” group and click on “Properties”.
1. Navigieren Sie zur Registerkarte &quot;Mitglieder&quot;.
1. Type in **wegov** in “Select User or Group” field.
1. Select from the dropdown “**We.Gov Forms Users**”.

   ![Editing group settings for workflow users](assets/edit_group_settings.jpg)

1. Click “Save &amp; Close” in the menu bar.
1. Repeat steps 2-7 by searching for “**analytics**”, selecting the “**Analytics Administrators**” group, and adding the “**We.Gov Forms Users**” group as a member.
1. Repeat steps 2-7 by searching for “**forms users**”, selecting the “**forms-power-users**” group, and adding the “**We.Gov Forms Users**” group as a member.
1. Repeat steps 2-7 by searching for “**forms-users**”, selecting the “**forms-users**” group, and this time adding the “**We.Gov Users**” group as a member.

### Email server configuration {#email-server-configuration}

1. Review setup documentation [Configuring Email Notification](/help/sites-administering/notification.md)
1. Login as administrator to perform this task.
1. Navigate to *https://&lt;aemserver>:&lt;port>/system/console/configMgr*
1. Locate and click on the **Day CQ Mail Service** service to configure.

   ![Konfigurieren des Day CQ Mail Service](assets/day_cq_mail_service.jpg)

1. Configure the service to connect to the SMTP server of your choice:

   1. **SMTP Server hostname**: e.g (smtp.gmail.com)
   1. **Server Port**: e.g (465) for gmail using SSL
   1. **SMTP User:** demo@ &lt;companyname> .com
   1. **“From” Address**: aemformsdemo@adobe.com

   ![Configure SMTP](assets/configure_smtp.jpg)

1. Klicken Sie auf &quot;Speichern&quot;, um die Konfiguration zu speichern.

### (Optional) AEM SSL Configuration {#aemsslconfig}

Dieser Abschnitt enthält Details zum Konfigurieren von SSL auf der AEM Instanz, um die Adobe Sign Cloud-Konfiguration konfigurieren zu können.

**Verweise:**

1. [Die Funktion „SSL By Default“ (SSL als Standard)](/help/sites-administering/ssl-by-default.md)

**Hinweise:**

1. Navigate to https://&lt;aemserver>:&lt;port>/aem/inbox where you will be able to complete the process explained in the reference documentation link above.
1. The `we-gov-forms.pkg.all-[version].zip` package includes a sample SSL key and certificate that can be accessed by extracting the `we-gov-forms.pkg.all-[version].zip/ssl` folder that is part of the package.

1. SSL certificate and key details:

   1. issued to “CN=localhost”
   1. 10yr validity
   1. password value of “password”
1. Private key is the *localhostprivate.der*.
1. Certificate is the *localhost.crt*.
1. Klicken Sie auf Weiter.
1. HTTPS Hostname should be set to *localhost*.
1. Port should be set to a port that the system has exposed.

### (Optional) Adobe Sign cloud configuration {#adobe-sign-cloud-configuration}

This section contains details and instructions on the Adobe Sign Cloud Configuration.

**Verweise:**

1. [Integrieren von Adobe Sign mit AEM Forms](adobe-sign-integration-adaptive-forms.md)

#### Cloud configuration {#cloud-configuration}

1. Review the prerequisites. See [AEM SSL Configuration](../../forms/using/forms-install-configure-gov-reference-site.md#aemsslconfig) for required SSL configuration.
1. Navigieren Sie zu:

   *https://&lt;aemserver>:&lt;port>/libs/adobesign/cloudservices/adobesign.html/conf/we-gov*

   >[!NOTE]
   >
   >The URL used to access the AEM server should match the URL configured in the Adobe Sign OAuth Redirect URI to avoid configuration issues (e.g. *https://&lt;aemserver>:&lt;port>/mnt/overlay/adobesign/cloudservices/adobesign/properties.html*)

1. Select the “We.gov Adobe Sign” configuration.
1. Click on “Properties”.
1. Navigieren Sie zur Registerkarte &quot;Einstellungen&quot;.
1. Enter the oAuth URL e.g.: [https://secure.na1.echosign.com/public/oauth](https://secure.na1.echosign.com/public/oauth)
1. Provide the configured Client Id and Client Secret from the configured Adobe Sign instance.
1. Klicken Sie auf &quot;Mit Adobe Sign verbinden&quot;.
1. After successful connection, click “Save &amp; Close” to complete the integration.

### (Optional) MS Dynamics cloud configuration {#ms-dynamics-cloud-configuration}

This section contains details and instructions on the MS Dynamics Cloud Configuration.

**Verweise:**

1. [Microsoft Dynamics OData-Konfiguration](https://docs.adobe.com/content/help/en/experience-manager-64/forms/form-data-model/ms-dynamics-odata-configuration.html)
1. [Configuring Microsoft Dynamics for AEM Forms](https://helpx.adobe.com/experience-manager/kt/forms/using/config-dynamics-for-aem-forms.html)

#### MS Dynamics OData cloud service {#ms-dynamics-odata-cloud-service}

1. Navigieren Sie zu:

   https://&lt;aemserver>:&lt;port>/libs/fd/fdm/gui/components/admin/fdmcloudservice/fdm.html/conf/we-gov

   1. Ensure that you are accessing the server using the same redirect URL as configured in the MS Dynamics application registration.

1. Select the “Microsoft Dynamics OData Cloud Service” configuration.
1. Klicken Sie auf &quot;Eigenschaften&quot;.

   ![Properties for Microsoft OData Cloud Service](assets/properties_odata_cloud_service.jpg)

1. Navigate to the “Authentication Settings” tab.
1. Geben Sie die folgenden Details ein:

   1. **Service Root:** e.g https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/
   1. **Authentifizierungstyp:** OAuth 2.0
   1. **Authentication Settings** (see [MS Dynamics cloud configuration settings](../../forms/using/forms-install-configure-gov-reference-site.md#dynamicsconfig) to collect this information):

      1. Client Id - also referred to as Application ID
      1. Client-Geheimnis
      1. OAuth URL - e.g. [https://login.windows.net/common/oauth2/authorize](https://login.windows.net/common/oauth2/authorize)
      1. Refresh Token URL - e.g. [https://login.windows.net/common/oauth2/token](https://login.windows.net/common/oauth2/token)
      1. Access Token URL - e.g. [https://login.windows.net/common/oauth2/token](https://login.windows.net/common/oauth2/token)
      1. Authorization Scope - **openid**
      1. Authentifizierungskopfzeile - **Autorisierungsanbieter**
      1. Resource - e.g [https://msdynamicsserver.api.crm3.dynamics.com](https://msdynamicsserver.api.crm3.dynamics.com)
   1. Klicken Sie auf &quot;Mit OAuth verbinden&quot;.


1. After successful authentication, click “Save &amp; Close” to complete the integration.

#### Konfigurationseinstellungen für MS Dynamics {#dynamicsconfig}

The steps detailed in this section are included to help you locate the Client Id, Client Secret and details from your MS Dynamics Cloud instance.

1. Navigate to [https://portal.azure.com/](https://portal.azure.com/) and login.
1. From the left hand menu select “All Services”.
1. Search for or navigate to “App Registration”.
1. Create, or select an existing application registration.
1. Copy the **Application ID** to be used as the OAuth **Client Id** in the AEM cloud configuration
1. Click on “Settings” or “Manifest” to configure the **Reply URLs.**

   1. This URL must match the URL used to access your AEM server when configuring the OData service.

1. From the Setting view, click “Keys” to view create new key (this is used as the Client Secret in AEM ).

   1. Make sure to keep a copy of the key as you will not be able to view it later in Azure or AEM.

1. To locate the Resource URL/Service Root URL, navigate to the MS Dynamics instance dashboard.
1. In the top navigation bar, click “Sales” or your own instance type and “Select Settings”.
1. Klicken Sie unten rechts auf &quot;Anpassungen&quot; und &quot;Entwicklerressourcen&quot;.
1. There you’ll find the Service Root URL: e.g

   *[https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/](https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/)*

1. Details on the Refresh and Access Token URL are available here:

   *[https://docs.microsoft.com/en-us/rest/api/datacatalog/authenticate-a-client-app](https://docs.microsoft.com/en-us/rest/api/datacatalog/authenticate-a-client-app)*

#### Testing the Forms Data Model (Dynamics) {#testing-the-form-data-model}

Once the cloud configuration is complete, you may want to test the form data model.

1. Navigieren Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments-fdm/we-gov*

1. Select the “We.gov Microsoft Dynamics CRM FDM” and select “Properties”.

   ![Properties of Dynamics CRM FDM](assets/properties_dynamics_crm.jpg)

1. Navigate to the “Update Source” tab.
1. Ensure that the “Context-Aware Configuration” is set to “/conf/we-gov” and that the configured data source is “ms-dynamics-odata-cloud-service”.

   ![Configured data source](assets/configured_data_source.jpg)

1. Edit the Form Data Model.

1. Test the services to ensure they successfully connect to the configured Data Source.

   >[!NOTE]
   After testing the services, click **Cancel** to ensure that involuntary changes are not propagated to the Form Data Model.

   >[!NOTE]
   Es wurde berichtet, dass ein Neustart AEM Servers erforderlich war, damit die Datenquelle erfolgreich an den FDM gebunden werden konnte.

#### Testing the Forms Data Model (Derby) {#test-fdm-derby}

Once the cloud configuration is complete, you may want to test the forms data model.

1. Navigate to *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments-fdm/we-gov*

1. Select the **We.gov Enrollment FDM** and select **Properties**.

   ![Properties of Dynamics CRM FDM](assets/aftia-enrollment-fdm.jpg)

1. Navigate to the **Update Source** tab.

1. Ensure that the **Context-Aware Configuration** is set to `/conf/we-gov` and that the configured data source is **We.Gov Derby DS**.

   ![Properties of Dynamics CRM FDM](assets/aftia-update-data-source.jpg)

1. Click on **Save and Close**.

1. [Test the services](work-with-form-data-model.md#test-data-model-objects-and-services) to ensure they successfully connect to the configured Data Source

   * To test the connection select the **HOMEMORTGAGEACCOUNT** and give it a get service. Test the service and system administrators can see data being retrieved.

### Adobe Analytics-Konfiguration (optional) {#adobe-analytics-configuration}

This section contains details and instructions on the Adobe Analytics Cloud Configuration.

**Verweise:**

* [Integrieren mit Adobe Analytics](../../sites-administering/adobeanalytics.md)

* [Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks](../../sites-administering/adobeanalytics-connect.md)

* [Anzeigen von Seitenanalysedaten](../../sites-authoring/pa-using.md)

* [Konfigurieren von Analysen und Berichten](configure-analytics-forms-documents.md)

* [Anzeigen und Verstehen der Analytics-Berichte in AEM Forms](view-understand-aem-forms-analytics-reports.md)

### Adobe Analytics cloud service configuration {#adobe-analytics-cloud-service-configuration}

This package comes pre-configured to connect to Adobe Analytics. The steps below are provided to allow this configuration to be updated.

1. Navigate to *https://&lt;aemserver>:&lt;port>/libs/cq/core/content/tools/cloudservices.html*
1. Locate the Adobe Analytics section, and select “Show Configurations” link.
1. Select the “We.Gov Adobe Analytics (Analytics Configuration)” configuration.

   ![Konfiguration des Analytics-Cloud-Dienstes](assets/analytics_config.jpg)

1. Click on the “Edit” button to update the Adobe Analytics configuration (you will need to provide the Shared Secret). Click on “Connect to Analytics” to connect, and “OK” to complete.

   ![We.Gov Adobe Analytics](assets/wegov_adobe_analytics.jpg)

1. From the same page, click “We.Gov Adobe Analytics Framework (Analytics Framework)” if you wish to update the framework configurations (see [Enable AEM authoring](../../forms/using/forms-install-configure-gov-reference-site.md#enableauthoring) to enable Authoring).

#### Adobe Analytics Locating User Credentials {#analytics-locating-user-credentials}

In order to locate the user credentials for a Adobe Analytics account the account administrator must perform the following tasks.

1. Navigate to the Adobe Experience Cloud portal.
   * Login with your administrator credentials
1. Select the Adobe Analytics icon in the main dashboard.
   ![Schnellzugriff](assets/aftia-quick-access.jpg)
1. Navigate to the Admin tab and select the User Management (Legacy) item
   ![Berichte](assets/aftia-reports.jpg)
1. Select the **Users** tab.
   ![Benutzerverwaltung](assets/aftia-user-management.jpg)
1. Select the desired user from the list of users.
1. Scroll to the bottom of the page and the users authentication information will appear at the bottom of the page.
   ![Zugriff verwalten](assets/aftia-admin-user-access.jpg)
1. The username and shared secret information will appear on the right side of the permissions box.
1. Beachten Sie, dass der Benutzername einen Doppelpunkt im Namen enthält. Alle Informationen links vom Doppelpunkt sind der Benutzername und alle Informationen rechts vom Doppelpunkt sind der Name der Firma.
   * Hier ein Beispiel: *Benutzername: Name der Firma*

#### Einrichten der Benutzerauthentifizierung in Adobe Analytics {#setup-user-authentication}

Administratoren können Benutzern AEM Analyseberechtigungen erteilen, indem sie die folgenden Aktionen ausführen.

1. Navigieren Sie zum Adobe Admin Console.

1. Klicken Sie auf die Analytics-Instanz, die der Admin-Konsole angezeigt wird.

   * This is located on the main page of the admin page.

1. Wählen Sie Analytics mit vollem Administratorzugriff.

1. hinzufügen einem Benutzer zum Profil.

   ![Vollständiger Admin-Zugriff in Analytics](assets/aftia-full-admin-access.jpg)

1. Klicken Sie auf die Registerkarte &quot;Berechtigungen&quot;, nachdem die Benutzer-ID dem Profil zugeordnet wurde.

1. Vergewissern Sie sich, dass dem Profil alle Berechtigungen zugeordnet sind.

   ![Berechtigungen bearbeiten](assets/aftia-admin-access-edit.jpg)

1. Beachten Sie, dass es nach der Zuordnung der Berechtigungen einige Stunden dauern kann, bis ein Benutzer sich anmelden kann.

### Adobe Analytics Berichte {#adobe-analytics-reporting}

#### Ansicht Adobe Analytics Sites Berichte {#view-adobe-analytics-sites-reporting}

>[!NOTE]
AEM Forms Analytics-Daten sind im Offlinemodus oder ohne Adobe Analytics Cloud-Konfiguration verfügbar, wenn das `we-gov-forms.ui.analytics-<version>.zip` Paket installiert ist. Für AEM Sites-Daten ist jedoch eine aktive Cloud-Konfiguration erforderlich.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Wählen Sie die &quot;AEM Forms We.Gov Site&quot;, um die Seiten der Website Ansicht.
1. Wählen Sie eine der Siteseiten (z.B. Home) und wählen Sie &quot;Analytics &amp; Recommendations&quot;.

   ![Analyse und Recommendations](assets/analytics_recommendations.jpg)

1. Auf dieser Seite sehen Sie Informationen aus Adobe Analytics, die zur Seite AEM Sites gehören (Hinweis: Diese Informationen werden von Adobe Analytics regelmäßig aktualisiert und nicht in Echtzeit angezeigt.

   ![AEM Sites analysis](assets/sites_analysis.jpg)

1. Zurück auf der Seite &quot;Ansicht&quot;(Zugriff in Schritt 3) können Sie die Seiteninformationen auch durch Ändern der Anzeigeeinstellung in &quot;Ansicht&quot;-Elemente in der Ansicht &quot;Liste&quot; Ansicht der Ansicht ändern.
1. Locate the “View” dropdown menu and select “List View”.

   ![Listenansicht](assets/list_view.jpg)

1. From the same menu, select “View Setting” and select the columns you wish to display from the “Analytics” section.

   ![Spalten konfigurieren](assets/configure_columns.jpg)

1. Click “Update” to make the new columns available.

   ![Display of new columns](assets/new_columns_display.jpg)

#### Ansicht Adobe Analytics Forms Berichte {#view-adobe-analytics-forms-reporting}

>[!NOTE]
AEM Forms Analytics-Daten sind im Offlinemodus oder ohne Adobe Analytics Cloud-Konfiguration verfügbar, wenn das `we-gov-forms.ui.analytics-<version>.zip` Paket installiert ist. Für AEM Sites-Daten ist jedoch eine aktive Cloud-Konfiguration erforderlich.

1. Navigieren Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Select the “Enrollment Application For Health Benefits” adaptive form and select the “Analytics Report” option.

   ![Analytics Report](assets/analytics_report.jpg)

1. Wait for the page to load, and view the Analytics Report data.

   ![View Analytics report data](assets/analytics_report_data.jpg)

### Adobe Automated Forms Configuration Enablement {#automated-forms-enablement}

Um AEM Forms mit der Adobe Forms zu installieren und zu konfigurieren, müssen die Benutzer des Umrechnungstools über Folgendes verfügen.

1. Zugriff auf Adobe IO.

1. Berechtigung zum Erstellen einer Integration mit dem Forms Conversion-Dienst der Adobe.

1. Adobe AEM 6.5 Service Pack, das als Autor ausgeführt wird.

Bitte lesen Sie die folgenden Hinweise, bevor Sie weitere Anweisungen lesen:

* [Dienst zur automatischen Formularkonvertierung konfigurieren](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/configure-service.html)

#### Erstellen einer IMS-Konfiguration Teil 1 {#creating-ims-config}

Um den Dienst für eine korrekte Kommunikation mit dem Formular-Konvertierungstool zu konfigurieren, müssen die Benutzer den Identity Management-Systemdienst (IMS) so konfigurieren, dass sie sich bei der Adobe I/O registrieren können.

1. Navigieren Sie zu https://&lt;aemserver>: > Klicken Sie links oben auf Adobe ExperienceManager > Tools > Security > Adobe IMS Configuration.

1. Klicken Sie auf Erstellen.

1. Führen Sie die Aktionen in der Abbildung unten durch.

   ![Konfiguration des technischen IMS-Kontos](assets/aftia-technical-account-configuration.jpg)

1. Make sure to download the certificate.

1. Do not proceed with the remainder of the configuration - review section [Creating Integration in Adobe I/O](#create-integration-adobeio)

>[!NOTE]
The certificate created in this section is going to be used to create the integration service in Adobe I/O. Once users have created in the integration service users can use that information from Adobe I/O to finish the configuration.

#### Creating Integration in Adobe I/O {#create-integration-adobeio}

Vergewissern Sie sich, dass Sie die Möglichkeit haben, eine Integration in Ihrer Adobe-Domäne zu erstellen, wenn Sie sich hierzu nicht an Ihren Systemadministrator wenden.

1. Navigieren Sie zur [Adobe-E/A-Konsole](https://console.adobe.io/).

1. Klicken Sie auf Integration erstellen.

1. Wählen Sie Zugriff auf eine API.

1. Vergewissern Sie sich, dass Sie sich in der richtigen Liste befinden (Dropdown-Liste oben rechts).

1. Wählen Sie im Bereich Experience Cloud das Forms-Konvertierungstool.

1. Klicken Sie auf Weiter.

1. Enter the name and description of your integration.

1. Mit dem öffentlichen Schlüssel aus Abschnitt 2.1 fügen Sie ihn in die Integration des Schlüssels ein.

1. Wählen Sie ein Profil für Ihre automatisierte Formularkonvertierung aus.

   ![Neue Integration erstellen](assets/aftia-create-new-integration.jpg)

#### Erstellen der IMS-Konfiguration Teil 2 {#create-ims-config-part-next}

Nachdem Sie eine Integration erstellt haben, können wir die Installation der IMS-Konfiguration abschließen.

1. Klicken Sie auf Ihre Integration innerhalb der Adobe I/O, um die Verbindungsdetails anzuzeigen.

1. Navigieren Sie zu Ihrer IMS-Konfiguration in AEM (&quot;Tools&quot;> &quot;Sicherheit&quot;> &quot;IMS&quot;)

1. Klicken Sie im Bildschirm &quot;IMS-Konfiguration&quot;auf Weiter.

1. Geben Sie den Autorisierungsserver ein (im Screenshot angezeigter Wert).

1. Geben Sie den API-Schlüssel ein.

1. Geben Sie den geheimen Clientschlüssel ein (muss in der Adobe I/O auf &quot;Integration verfügbar machen&quot;klicken, damit er angezeigt wird).

1. Klicken Sie auf die JWT-Registerkarte in Adobe I/O, um die JWT-Nutzlast abzurufen und in die Nutzlast der IMS-Konfiguration einzufügen.

   ![Payload-IMS-Konfiguration](assets/aftia-payload-ims-config.jpg)

1. Nach der Erstellung klicken Sie auf die IMS-Konfiguration und wählen Sie Health Check aus. Benutzer sollten das folgende Ergebnis sehen.

   ![Gesundheitsbestätigung](assets/aftia-health-confirmation.jpg)

#### Konfigurieren der Cloud-Konfiguration (We.Gov AFC Production) {#configure-cloud-configuration}

Sobald die IMS-Konfiguration abgeschlossen ist, können wir die Cloud-Konfiguration in AEM überprüfen. Wenn die Konfiguration nicht vorhanden ist, führen Sie die folgenden Schritte aus, um die Cloud-Konfiguration in AEM zu erstellen:

1. Öffnen Sie den Browser und navigieren Sie zur System-URL https://&lt;domain_name>:&lt;system_port>

1. Klicken Sie in der oberen linken Ecke des Bildschirms auf Adobe Experience Manager > Extras > Cloud Services > Automatisierte Forms-Konversationskonfiguration.

1. Wählen Sie den Konfigurationsordner aus, in dem Sie die Konfiguration ablegen möchten.

1. Klicken Sie auf Erstellen.

1. Geben Sie die Informationen in den Screenshot unten ein.

   ![AFC-Produktion](assets/aftia-afc-production.jpg)

1. Geben Sie der Konfiguration einen Titel und einen Namen ein.

1. Die Dienst-URL für das System ist auf https://aemformsconversion.adobe.io/ eingestellt.

1. Vorlagen-URL */conf/we-gov/settings/wcm/templates/we-gov-flamingo-template*.

1. Theme URL: */content/dam/formsanddocuments-themes/adobe-gov-forms-themes/we-gov-theme*

1. Klicken Sie auf Weiter.

1. For this configuration, we left the two checkbox values empty.

   * To understand more about these options, see [Configure the cloud service](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/configure-service.html#configure-the-cloud-service).

#### Configure Cloud Configuration (We.Finance AFC Production) {#configure-cloud-configuration-wefinance}

Once the IMS configuration is complete then we can proceed to create the cloud configuration in AEM.

1. Öffnen Sie den Browser und navigieren Sie zur System-URL https://&lt;domain_name>:&lt;system_port>

1. Klicken Sie in der oberen linken Ecke des Bildschirms auf Adobe Experience Manager > Extras > Cloud Services > Automatisierte Forms-Konversationskonfiguration.

1. Wählen Sie den Konfigurationsordner aus, in dem Sie die Konfiguration ablegen möchten.

1. Klicken Sie auf Erstellen.

1. Enter the information in the screenshot below.

   ![We.Finance AFC Production](assets/aftia-wefinance-afc-prod.jpg)

1. Provide the configuration with a Title and a Name.

1. The service URL for the system is set to https://aemformsconversion.adobe.io/

1. Template URL: */conf/we-finance/settings/wcm/templates/we-finance-adaptive-form*

1. Design-URL: */content/dam/formsanddocuments-Themen/adobe-finance-forms-Themen/we-finance-theme*

1. Klicken Sie auf Weiter.

1. Für diese Konfiguration bleiben die beiden Kontrollkästchenwerte leer.

   * Weitere Informationen zu diesen Optionen finden Sie unter Cloud-Dienst [konfigurieren](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/configure-service.html#configure-the-cloud-service).

#### Testen der Formularumrechnung (We.Gov-Registrierungsanwendung) {#test-forms-conversion}

Sobald die Konfiguration eingerichtet ist, können Benutzer sie testen, indem sie ein PDF-Dokument hochladen.

1. Navigieren Sie zum AEM System https://&lt;domain_name>:&lt;system_port>

1. Klicken Sie auf Forms > Forms &amp; Dokumente > AEM Forms We.gov Forms > AFC.

1. Wählen Sie die PDF-Datei &quot;We.Gov Enrollment Application&quot;.

1. Click on the **Start Automated Conversion** button in the top right corner.

1. Users should be able to see the option as shown below.

   ![Converted adaptive form](assets/aftia-converted-adaptive-form.jpg)

1. Once the button has been selected then users will be presented with the following options

   * Stellen Sie sicher, dass die Benutzer die *Konfiguration We.Gov AFC Production* auswählen

   ![Conversion settings](assets/aftia-conversion-settings.jpg)

   ![Erweiterte Konvertierungseinstellungen](assets/aftia-conversion-settings-2.jpg)

1. Wählen Sie die Konvertierung des Beginns aus, nachdem Sie alle gewünschten Optionen konfiguriert haben.

1. As the conversion process begins then users should see the following screen:

   ![Conversion settings](assets/aftia-conversion-in-progress.jpg)

1. When the conversion is complete then users will see the following screen:

   ![Converted adaptive form](assets/aftia-converted-adaptive-form-2.jpg)

   Klicken Sie auf den Ordner **Output** , um das erstellte adaptive Formular Ansicht.

#### Known Issues &amp; Notes {#known-issues-notes}

The Automated Forms Conversion service includes certain [best practices, known complex patterns](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/styles-and-pattern-considerations-and-best-practices.html), and [known issues](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/known-issues.html). Überprüfen Sie diese, bevor Sie mit der Verwendung des AEM Forms Automated Forms Conversion-Dienstes beginnen.

1. Generate the Form with Generate adaptive form(s) without data bindings enabled if you would like to bind the form to an FDM after conversion.

1. Make sure the template folder has jcr:read for everyone permission enabled or else the service user will not be able to read the template from the repository and the conversion will fail.

## Demo package customizations {#demo-package-customizations}

This section includes instructions on customization of the demo.

### Templates customization {#templates-customization}

Editable Templates can be found at the following location:

*https://&lt;aemserver>:&lt;port>/libs/wcm/core/content/sites/templates.html/conf/we-gov*

These templates include the AEM Site, Adaptive Form, and Interactive Communications templates, created and assembled with components that can be found at:

*https://&lt;aemserver>:&lt;port>/crx/de/index.jsp#/apps/we-gov/components*

#### Style system {#customizetemplates}

This site also features client-libraries, one of which imports Bootstrap 4 ( [https://getbootstrap.com/](https://getbootstrap.com/) ). This client library is available at

*https://&lt;aemserver>:&lt;port>/crx/de/index.jsp#/apps/we-gov/clientlibs/clientlib-base/css/bootstrap*

The editable templates included in this package also come preconfigured with template/page policies that use the Bootstrap 4 CSS classes for pagination, styling, etc. Not all classes have been added to the template policies, but any class that is supported by Bootstrap 4 can be added to the policies. See the getting started page for a list of available classes:

[https://getbootstrap.com/docs/4.1/getting-started/introduction/](https://getbootstrap.com/docs/4.1/getting-started/introduction/)

Die in diesem Paket enthaltenen Vorlagen unterstützen auch das Stilsystem:

[Stilsystem](../../sites-authoring/style-system.md)

#### Template logos {#template-logos}

Project DAM Assets also include We.Gov logos and images. These assets are available at:

*https://&lt;aemserver>:&lt;port>/assets.html/content/dam/we-gov*

When editing the Page and Form Templates, one may choose to update brand logos by editing the Navigation and Footer components. These components offer a configurable brand and logo dialog that can be used to update logos:

![Template Logos](assets/template_logos.jpg)

See Editing Page Content for more information:

[Bearbeiten des Seiteninhalts](../../sites-authoring/editing-content.md)

### Sites pages customization {#sites-pages-customization}

All site pages are available from: *https://&lt;aemserver>:&lt;port>/sites.html/content/we-gov*

These site pages also make use of the AEM Grid package to control the layout of a few components.

#### Style system {#style-system}

Pages included in this package also support the Style System:

[Stilsystem](../../sites-authoring/style-system.md)

You can also refer to [Templates customization style system](../../forms/using/forms-install-configure-gov-reference-site.md#customizetemplates) for documentation on supported styles.

### Adaptive forms customization {#adaptive-forms-customization}

All adaptive forms are available from:

*https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

These forms can be customized to fit certain use cases. Note that certain fields, and submission logic should not be modified to ensure that the form continues to function correctly. Hierzu gehört Folgendes:

**Enrollment Application For Health Benefits:**

* contact_id - Hidden field used to receive the MS Dynamics contact ID during submission
* Submit - Submit button logic required customization to support callbacks. Customization is documented, but a large script was required to submit the form while performing both a POST and GET operation to MS Dynamics via the Forms Data Model.
* Root Panel - Initialize event is used to add an MS Dynamics button to the AEM Inbox in the least intrusive way possible since all AEM Inbox Granite UI components are non-modifiable.

#### Adaptive form styling {#adaptive-form-styling}

Adaptive forms can also be styled using the Style Editor or Theme editor:

* [Inline-Stile für Komponenten adaptiver Formulare](inline-style-adaptive-forms.md)
* [Erstellen und Verwenden von Designs](themes.md)

### Workflow customization {#workflow-customization}

The Enrollment Adaptive Form submit to an OSGI workflow for processing. This workflow can be found at *https://&lt;aemserver>:&lt;port>/conf/we-gov/settings/models/we-gov-process.html*.

Due to certain limitations, this workflow contains several scripts and custom OSGI workflow process steps. These workflow steps were created as generic steps and have not been created with configuration dialogues. At this time, configuration of the workflow steps relies on process arguments.

All workflow step Java code is contained in the **we-gov-forms.core-&lt;version>.jar** bundle.

## Demo considerations and known issues {#demo-considerations-and-known-issues}

This section contains information on demo features and design decisions that may require special considerations during the demonstration process.

### Demo considerations {#demo-considerations}

* As per AGRS-159, ensure that the name (first, middle, and last) of the contact used in the Enrollment Adaptive Form is unique.
* The enrollment adaptive form will send the Adobe Sign email to the email specified in the form’s email field. Diese E-Mail-Adresse darf nicht mit der E-Mail-Adresse übereinstimmen, mit der die Adobe Sign-Cloud-Konfiguration konfiguriert wurde.

### Bekannte Probleme {#known-issues}

* (AGRS-120) The Site Navigation component currently does not support nested child pages that are more than 2 levels deep.
* (AGRS-159) The current MS Dynamics FDM needs to perform 2 operations to first, POST the Enrollment Adaptive Form data to Dynamics, and then fetch the user record in order to retrieve the Contact ID. In ihrem aktuellen Zustand schlägt das Abrufen der Kontakt-ID fehl, wenn in Dynamics mehr als zwei Benutzer mit demselben Namen vorhanden sind. Dies verhindert, dass das adaptive Registrierungsformular gesendet werden kann.

## Configuring Accessibility Testing {#configure-accessibility-testing}

### Enabling Accessibility Testing Chrome Add On {#enable-chrome-add-on}

In order to perform accessibility testing first you need to install the Chrome plugin, this can be found [here](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?hl=en).

Once it is installed, load the page that you wish to test within the Chrome Browser (Note: Having multiple tabs open may affect your score, it is preferable to only have one tab open). Once the page is loaded
**right click** on the page and select **Audits** tab . There developers can select the type of audit to be performed by the Accessibility plugin. Once all the desired options have been selected then the user can select the Generate Report button. This will generate a PDF document that shows the overall accessibility rating and what can be used to increase accessibility rating overall.

Once the report has been executed users can expect to see the following:

![Accessibility report](assets/aftia-accessibility.jpg)

The number displayed in front of users is the overall accessibility rating that they have acquired. There is also a description of how this was calculated following the score.

If users wish to export this they can click on the three buttons on the right of the screen and select from the further options that the plugin offers.

![Accessibility report](assets/aftia-accessibility-report.jpg)

### Ultramarine Theme {#ultramarine-theme}

The publicly available Ultramarine theme maintained by Adobe is built into the
`we-gov-forms.pkg.all-<version>.zip` installable ZIP file. Once this package is installed using CRX.

Package Manager, users can access the Ultramarine theme in AEM Forms by navigating to **Forms** > **Themes** > **Reference Themes** > **Ultramarine-Accessible**.

![Ultramarine-Design](assets/aftia-ultramarine-theme.jpg)

## Konfigurationsoptionen {#configuration-options}

Users have the ability to configure various workflow service options which include the following:

1. Microsoft Dynamics Entry
1. Adobe Sign
1. AEM Custom Communication Management
1. Adobe Analytics

In order to configure them to be enabled within the Workflow users need to perform the following tasks.

1. Navigate to https://&#39;[server]:[port]&#39;/system/console/configMgr.

1. Locate the *WeGov Configurations*.

1. Open the service definition and enable the selected services to be invoked within the workflow.

>[!NOTE]
Just because a user enables the service within the Configuration Manager page, users are still required to setup a service configuration in order to communicate with the external services requested.

![we gov forms package](assets/aftia-configuration-options.jpg)

1. Once completed click on the Save button in order to save the settings.

## Nächste Schritte {#next-steps}

Jetzt sind Sie alle bereit, die Web.Gov Referenz-Website zu erkunden. For more information about We.Gov reference site workflow and steps, see [We.Gov reference site walkthrough](../../forms/using/forms-gov-reference-site-user-demo.md).
