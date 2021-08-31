---
title: Einrichten und Konfigurieren der Referenz-Website We.Gov und We.Finance
seo-title: Set up and configure We.Gov reference site
description: Installieren, konfigurieren und passen Sie ein AEM Forms-Demopaket an.
seo-description: Install, configure, and customize an AEM Forms demo package.
uuid: 0a6ad8f9-0d38-40c3-ad8d-e705edef55f8
contentOwner: anujkapo
discoiquuid: fe5da0aa-d3a8-4b77-a447-9e429fdc2816
docset: aem65
exl-id: 1fee474e-7da5-4ab2-881a-34b8e055aa29
source-git-commit: 1def8ff7bc90e2ab82ce8b50277a97da9709c78c
workflow-type: tm+mt
source-wordcount: '4703'
ht-degree: 4%

---

# Einrichten und Konfigurieren der Referenz-Website We.Gov und We.Finance {#set-up-and-configure-we-gov-reference-site}

## Details zum Demopaket {#demo-package-details}

### Installationsvoraussetzungen {#installation-prerequisites}

Dieses Paket wurde für **AEM Forms 6.4 OSGI Author** erstellt, wurde getestet und wird daher für die folgenden Plattformversionen unterstützt:

| AEM VERSION | AEM Forms-PACKAGE-VERSION | STATUS |
|---|---|---|
| 6.4 | 5,0,86 | **Unterstützt** |
| 6.5 | 6,0,80 | **Unterstützt** |
| 6,5,3 | 6,0,122 | **Unterstützt** |

Dieses Paket enthält eine Cloud-Konfiguration, die die folgenden Plattformversionen unterstützt:

| CLOUD PROVIDER | SERVICE-VERSION | STATUS |
|---|---|---|
| Adobe Sign | v5-API | **Unterstützt** |
| Microsoft Dynamics 365 | 1710 (9.1.0.3020) | **Unterstützt** |
| Adobe Analytics | v1.4 Rest-API | **Unterstützt** |
**Überlegungen zur Paketinstallation:**

* Das Paket wird voraussichtlich auf einem sauberen Server installiert, der frei von anderen Demopaketen oder älteren Demopaketversionen ist
* Das Paket wird voraussichtlich auf einem OSGi-Server installiert und im Autorenmodus ausgeführt

### Was enthält dieses Paket? {#what-does-this-package-include}

Das [AEM Forms We.Gov-Demopaket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/we-gov-forms.pkg.all-2.0.2.zip) (**we-gov-forms.pkg.all-&lt;version>.zip**) wird als Paket bereitgestellt, das mehrere weitere Unterpakete und Dienste enthält. Das Paket enthält die folgenden Module:

* **we-gov-forms.pkg.all-&lt;version>.zip**  -  *Umfassendes Demopaket*

   * **we-gov-forms.ui.apps-&lt;version>.zip** *- Enthält alle Komponenten, Client-Bibliotheken, Beispielbenutzer, Workflow-Modelle usw.*

      * **we-gov-forms.core-&lt;version>.jar**  -  *Enthält alle OSGi-Dienste, die Implementierung benutzerdefinierter Workflow-Schritte usw.*

      * **we-gov-forms.derby&lt;version>.jar**  -  *Enthält alle OSGi-Dienste, Datenbankschemata usw.*

      * **core.wcm.components.all-2.0.4.zip**  -  *Sammlung von WCM-Beispielkomponenten*

      * **grid-aem.ui.apps-1.0-SNAPSHOT.zip**  -  *AEM Sites Grid Layout package for Sites page column control*
   * **we-gov-forms.ui.content-&lt;version>.zip**  -  *Enthält alle Inhalte, Seiten, Bilder, Formulare, interaktiven Kommunikations-Assets usw.*

   * **we-gov-forms.ui.analytics-&lt;version>.zip**  -  *Enthält alle We.Gov Forms Analytics-Daten, die im Repository gespeichert werden sollen.*

   * **we-gov-forms.config.public-&lt;version>.zip**  -  *Enthält alle standardmäßigen Konfigurationsknoten, einschließlich Platzhalter-Cloud-Konfigurationen, um Formulardatenmodelle und Service-Bindungsprobleme zu vermeiden.*


Zu den in diesem Paket enthaltenen Assets gehören:

* AEM von Seiten der Site mit bearbeitbaren Vorlagen
* Adaptives AEM Forms Forms
* Interaktive Kommunikation mit AEM Forms (Druck und Webkanal)
* AEM Forms XDP-Datensatzdokument
* AEM Forms MS Dynamics Forms-Datenmodell
* Adobe Sign-Integration
* AEM Workflow-Modell
* AEM Assets-Beispielbilder
* Beispiel-Apache Derby-Datenbank (im Speicher)
* Apache Derby-Datenquelle (zur Verwendung mit dem Formulardatenmodell)

## Installation des Demopakets {#demo-package-installation}

Dieser Abschnitt enthält Informationen zur Installation des Demopakets.

### Aus Softwareverteilung {#from-software-distribution}

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads suchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den Paketnamen **we-gov-forms.pkg.all-&lt;version>.zip**, wählen Sie **[!UICONTROL EULA-Begriffe akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   ![Wir gov Forms-Paket](assets/wegov_forms_package.jpg)

1. Lassen Sie den Installationsprozess abzuschließen.
1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html?wcmmode=disabled*, um sicherzustellen, dass die Installation erfolgreich war.

### Von einer lokalen ZIP-Datei {#from-a-local-zip-file}

1. Laden Sie die Datei **we-gov-forms.pkg.all-&lt;version>.zip** herunter und suchen Sie sie.
1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/crx/packmgr/index.jsp*.
1. Wählen Sie die Option &quot;Paket hochladen&quot;.

   ![Option &quot;Paket hochladen&quot;](assets/upload_package.jpg)

1. Verwenden Sie den Dateibrowser, um zur heruntergeladenen ZIP-Datei zu navigieren und sie auszuwählen.
1. Klicken Sie zum Hochladen auf &quot;Öffnen&quot;.
1. Wählen Sie nach dem Hochladen die Option &quot;Installieren&quot;, um das Paket zu installieren.

   ![Installieren des WeGov Forms-Pakets](assets/wegov_forms_package-1.jpg)

1. Lassen Sie den Installationsprozess abzuschließen.
1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html?wcmmode=disabled*, um sicherzustellen, dass die Installation erfolgreich war.

### Installieren neuer Paketversionen {#installing-new-package-versions}

Um eine neue Paketversion zu installieren, führen Sie die in 4.1 und 4.2 definierten Schritte aus. Es ist möglich, eine neuere Paketversion zu installieren, während bereits ein älteres Paket installiert ist. Es wird jedoch empfohlen, die ältere Paketversion zuerst zu deinstallieren. Gehen Sie dazu wie folgt vor.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/crx/packmgr/index.jsp*
1. Suchen Sie die ältere Datei **we-gov-forms.pkg.all-&lt;version>.zip** .
1. Wählen Sie die Option &quot;Mehr&quot;.
1. Wählen Sie im Dropdown-Menü die Option &quot;Deinstallieren&quot;.

   ![WeGov-Paket deinstallieren](assets/uninstall_wegov_forms_package.jpg)

1. Wählen Sie bei der Bestätigung erneut &quot;Deinstallieren&quot;aus und lassen Sie den Abschluss des Deinstallationsprozesses zu.

## Konfiguration des Demopakets {#demo-package-configuration}

Dieser Abschnitt enthält Details und Anweisungen zur Konfiguration des Demopakets nach der Bereitstellung vor der Präsentation.

### Fakultative Benutzerkonfiguration {#fictional-user-configuration}

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/libs/granite/security/content/groupadmin.html*
1. Melden Sie sich als Administrator an, um die unten aufgeführten Aufgaben durchzuführen.
1. Scrollen Sie nach unten zum Ende der Seite, um alle Benutzergruppen zu laden.
1. Suchen Sie nach &quot;**workflow**&quot;.
1. Wählen Sie die Gruppe &quot;**workflow-users**&quot;aus und klicken Sie auf &quot;Eigenschaften&quot;.
1. Navigieren Sie zur Registerkarte &quot;Mitglieder&quot;.
1. Geben Sie **wegov** in das Feld &quot;Benutzer oder Gruppe auswählen&quot;ein.
1. Wählen Sie aus dem Dropdown-Menü &quot;**We.Gov Forms Users**&quot;aus.

   ![Gruppeneinstellungen für Workflow-Benutzer bearbeiten](assets/edit_group_settings.jpg)

1. Klicken Sie in der Menüleiste auf &quot;Speichern und schließen&quot;.
1. Wiederholen Sie die Schritte 2-7, indem Sie nach &quot;**analytics**&quot;suchen, die Gruppe &quot;**Analytics-Administratoren**&quot;auswählen und die Gruppe &quot;**We.Gov Forms-Benutzer**&quot;als Mitglied hinzufügen.
1. Wiederholen Sie die Schritte 2-7, indem Sie nach &quot;**forms users**&quot;suchen, die Gruppe &quot;**forms-power-users**&quot;auswählen und die Gruppe &quot;**We.Gov Forms Users**&quot;als Mitglied hinzufügen.
1. Wiederholen Sie die Schritte 2-7, indem Sie nach &quot;**forms-users**&quot;suchen, die Gruppe &quot;**forms-users**&quot;auswählen und dieses Mal die Gruppe &quot;**We.Gov Users**&quot;als Mitglied hinzufügen.

### E-Mail-Serverkonfiguration {#email-server-configuration}

1. Überprüfen Sie die Einrichtungsdokumentation [Konfigurieren der E-Mail-Benachrichtigung](/help/sites-administering/notification.md)
1. Melden Sie sich als Administrator an, um diese Aufgabe durchzuführen.
1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/system/console/configMgr*
1. Suchen Sie den Dienst **Day CQ Mail Service** und klicken Sie darauf, um ihn zu konfigurieren.

   ![Konfigurieren des Day CQ Mail Service](assets/day_cq_mail_service.jpg)

1. Konfigurieren Sie den Dienst für die Verbindung mit dem gewünschten SMTP-Server:

   1. **Hostname** des SMTP-Servers: z. B. (smtp.gmail.com)
   1. **Server-Port**: z. B. (465) für Gmail mit SSL
   1. **SMTP User:** demo@  &lt;companyname> .com
   1. **&quot;Von&quot;-Adresse**: aemformsdemo@adobe.com

   ![SMTP konfigurieren](assets/configure_smtp.jpg)

1. Klicken Sie auf &quot;Speichern&quot;, um die Konfiguration zu speichern.

### (Optional) AEM SSL-Konfiguration {#aemsslconfig}

Dieser Abschnitt enthält Details zur Konfiguration von SSL auf der AEM-Instanz, um die Adobe Sign Cloud-Konfiguration konfigurieren zu können.

**Verweise:**

1. [Die Funktion „SSL By Default“ (SSL als Standard)](/help/sites-administering/ssl-by-default.md)

**Anmerkungen:**

1. Navigieren Sie zu https://&lt;aemserver>:&lt;port>/aem/inbox , wo Sie den im obigen Referenzdokumentations-Link erläuterten Prozess abschließen können.
1. Das Paket `we-gov-forms.pkg.all-[version].zip` enthält einen SSL-Beispielschlüssel und ein Zertifikat, auf das Sie zugreifen können, indem Sie den Ordner `we-gov-forms.pkg.all-[version].zip/ssl` extrahieren, der Teil des Pakets ist.

1. SSL-Zertifikat und Schlüsseldetails:

   1. ausgegeben an &quot;CN=localhost&quot;
   1. Gültigkeit von 10 Jahren
   1. Kennwortwert von &quot;password&quot;
1. Der private Schlüssel ist *localhostprivate.der*.
1. Zertifikat ist *localhost.crt*.
1. Klicken Sie auf Weiter.
1. HTTPS-Hostname sollte auf *localhost* gesetzt werden.
1. Der Port sollte auf einen Port eingestellt sein, den das System offen gelegt hat.

### (Optional) Adobe Sign-Cloud-Konfiguration {#adobe-sign-cloud-configuration}

Dieser Abschnitt enthält Details und Anweisungen zur Adobe Sign Cloud-Konfiguration.

**Verweise:**

1. [Integrieren von Adobe Sign mit AEM Forms](adobe-sign-integration-adaptive-forms.md)

#### Cloud-Konfiguration {#cloud-configuration}

1. Überprüfen Sie die Voraussetzungen. Informationen zur erforderlichen SSL-Konfiguration finden Sie unter [AEM SSL-Konfiguration](../../forms/using/forms-install-configure-gov-reference-site.md#aemsslconfig) .
1. Gehen Sie zu:

   *https://&lt;aemserver>:&lt;port>/libs/adobesign/cloudservices/adobesign.html/conf/we-gov*

   >[!NOTE]
   >
   >Die URL, die für den Zugriff auf den AEM-Server verwendet wird, sollte mit der URL übereinstimmen, die im OAuth-Weiterleitungs-URI von Adobe Sign konfiguriert ist, um Konfigurationsprobleme zu vermeiden (z. B. *https://&lt;aemserver>:&lt;port>/mnt/overlay/adobesign/cloudservices/adobesign/properties.html*)

1. Wählen Sie die Konfiguration &quot;We.gov Adobe Sign&quot;aus.
1. Klicken Sie auf &quot;Eigenschaften&quot;.
1. Navigieren Sie zur Registerkarte &quot;Einstellungen&quot;.
1. Geben Sie die oAuth-URL ein, z. B.: [https://secure.na1.echosign.com/public/oauth](https://secure.na1.echosign.com/public/oauth)
1. Geben Sie die konfigurierte Client-ID und das Client-Geheimnis aus der konfigurierten Adobe Sign-Instanz an.
1. Klicken Sie auf &quot;Mit Adobe Sign verbinden&quot;.
1. Klicken Sie nach erfolgreicher Verbindung auf &quot;Speichern und schließen&quot;, um die Integration abzuschließen.

### (Optional) MS Dynamics-Cloud-Konfiguration {#ms-dynamics-cloud-configuration}

Dieser Abschnitt enthält Details und Anweisungen zur MS Dynamics Cloud-Konfiguration.

**Verweise:**

1. [Microsoft Dynamics OData-Konfiguration](https://docs.adobe.com/content/help/en/experience-manager-64/forms/form-data-model/ms-dynamics-odata-configuration.html)
1. [Microsoft Dynamics für AEM Forms konfigurieren](https://helpx.adobe.com/experience-manager/kt/forms/using/config-dynamics-for-aem-forms.html)

#### MS Dynamics OData-Cloud-Dienst {#ms-dynamics-odata-cloud-service}

1. Gehen Sie zu:

   https://&lt;aemserver>:&lt;port>/libs/fd/fdm/gui/components/admin/fdmcloudservice/fdm.html/conf/we-gov

   1. Stellen Sie sicher, dass Sie auf den Server zugreifen, indem Sie dieselbe Umleitungs-URL verwenden, die in der Registrierung der MS Dynamics-Anwendung konfiguriert wurde.

1. Wählen Sie die Konfiguration &quot;Microsoft Dynamics OData Cloud Service&quot;.
1. Klicken Sie auf &quot;Eigenschaften&quot;.

   ![Eigenschaften für Microsoft OData Cloud Service](assets/properties_odata_cloud_service.jpg)

1. Navigieren Sie zur Registerkarte &quot;Authentifizierungseinstellungen&quot;.
1. Geben Sie die folgenden Details ein:

   1. **Dienststamm:** z. B.  `https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/`
   1. **Authentifizierungstyp:** OAuth 2.0
   1. **Authentifizierungseinstellungen**  (siehe  [MS Dynamics-Cloud-Konfigurationseinstellungen ](../../forms/using/forms-install-configure-gov-reference-site.md#dynamicsconfig) zum Erfassen dieser Informationen):

      1. Client-ID - auch als Anwendungs-ID bezeichnet
      1. Client-Geheimnis
      1. OAuth-URL - z. B. [https://login.windows.net/common/oauth2/authorize](https://login.windows.net/common/oauth2/authorize)
      1. Aktualisieren der Token-URL, z. B. [https://login.windows.net/common/oauth2/token](https://login.windows.net/common/oauth2/token)
      1. Zugriffstoken-URL - z. B. [https://login.windows.net/common/oauth2/token](https://login.windows.net/common/oauth2/token)
      1. Autorisierungsbereich - **openid**
      1. Authentifizierungs-Header - **Autorisierungsbearer**
      1. Ressource - z. B. `https://msdynamicsserver.api.crm3.dynamics.com`
   1. Klicken Sie auf &quot;Mit OAuth verbinden&quot;.


1. Klicken Sie nach erfolgreicher Authentifizierung auf &quot;Speichern und schließen&quot;, um die Integration abzuschließen.

#### Cloud-Konfigurationseinstellungen für MS Dynamics {#dynamicsconfig}

Die in diesem Abschnitt beschriebenen Schritte enthalten Hilfe bei der Suche nach der Client-ID, dem Client-Geheimnis und Details aus Ihrer MS Dynamics Cloud-Instanz.

1. Navigieren Sie zu [https://portal.azure.com/](https://portal.azure.com/) und melden Sie sich an.
1. Wählen Sie im Menü links &quot;Alle Dienste&quot; aus.
1. Suchen Sie nach &quot;App-Registrierung&quot;oder navigieren Sie zu &quot;App-Registrierung&quot;.
1. Erstellen oder wählen Sie eine bestehende Anwendungsregistrierung aus.
1. Kopieren Sie die **Anwendungs-ID**, die als OAuth **Client-ID** in der AEM Cloud-Konfiguration verwendet werden soll.
1. Klicken Sie auf &quot;Einstellungen&quot; oder &quot;Manifest&quot;, um die **Antwort-URLs zu konfigurieren.**

   1. Diese URL muss mit der URL übereinstimmen, die für den Zugriff auf Ihren AEM beim Konfigurieren des OData-Dienstes verwendet wird.

1. Klicken Sie in der Einstellungsansicht auf &quot;Schlüssel&quot;, um einen neuen Schlüssel zu erstellen (dieser wird in AEM als Client-Geheimnis verwendet).

   1. Achten Sie darauf, eine Kopie des Schlüssels zu behalten, da Sie ihn später in Azure oder AEM nicht anzeigen können.

1. Um die Ressourcen-URL/Dienststamm-URL zu finden, navigieren Sie zum Dashboard der MS Dynamics-Instanz.
1. Klicken Sie in der oberen Navigationsleiste auf &quot;Verkauf&quot;oder Ihren eigenen Instanztyp und &quot;Einstellungen auswählen&quot;.
1. Klicken Sie unten rechts auf &quot;Anpassungen&quot;und &quot;Entwicklungsressourcen&quot;.
1. Dort finden Sie die Dienststamm-URL: z. B.

   *`https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/`

1. Details zur URL für Aktualisierungs- und Zugriffstoken finden Sie hier:

   *[https://docs.microsoft.com/en-us/rest/api/datacatalog/authenticate-a-client-app](https://docs.microsoft.com/en-us/rest/api/datacatalog/authenticate-a-client-app)*

#### Testen des Forms-Datenmodells (Dynamics) {#testing-the-form-data-model}

Sobald die Cloud-Konfiguration abgeschlossen ist, sollten Sie das Formulardatenmodell testen.

1. Gehen Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments-fdm/we-gov*

1. Wählen Sie &quot;We.gov Microsoft Dynamics CRM FDM&quot;aus und wählen Sie &quot;Eigenschaften&quot;.

   ![Eigenschaften des Dynamics CRM-FDM](assets/properties_dynamics_crm.jpg)

1. Navigieren Sie zur Registerkarte &quot;Quelle aktualisieren&quot;.
1. Stellen Sie sicher, dass die &quot;kontextsensitive Konfiguration&quot;auf &quot;/conf/we-gov&quot;festgelegt ist und dass die konfigurierte Datenquelle &quot;ms-dynamics-odata-cloud-service&quot;lautet.

   ![Datenquelle konfiguriert](assets/configured_data_source.jpg)

1. Bearbeiten Sie das Formulardatenmodell.

1. Testen Sie die Dienste, um sicherzustellen, dass sie erfolgreich eine Verbindung zur konfigurierten Datenquelle herstellen.

   >[!NOTE]
   Klicken Sie nach dem Testen der Dienste auf **Abbrechen**, um sicherzustellen, dass unwillkürliche Änderungen nicht an das Formulardatenmodell weitergeleitet werden.

   >[!NOTE]
   Es wurde berichtet, dass ein AEM Server-Neustart erforderlich war, damit die Datenquelle erfolgreich an das FDM gebunden werden konnte.

#### Testen des Forms-Datenmodells (Derby) {#test-fdm-derby}

Sobald die Cloud-Konfiguration abgeschlossen ist, können Sie das Formulardatenmodell testen.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments-fdm/we-gov*

1. Wählen Sie **We.gov Enrollment FDM** und wählen Sie **Properties** aus.

   ![Eigenschaften des Dynamics CRM-FDM](assets/aftia-enrollment-fdm.jpg)

1. Navigieren Sie zur Registerkarte **Quelle aktualisieren** .

1. Stellen Sie sicher, dass die **Kontextabhängige Konfiguration** auf `/conf/we-gov` gesetzt ist und dass die konfigurierte Datenquelle **We.Gov Derby DS** lautet.

   ![Eigenschaften des Dynamics CRM-FDM](assets/aftia-update-data-source.jpg)

1. Klicken Sie auf **Speichern und schließen**.

1. [Testen Sie die Dienste, ](work-with-form-data-model.md#test-data-model-objects-and-services) um sicherzustellen, dass sie erfolgreich eine Verbindung zur konfigurierten Datenquelle herstellen.

   * Um die Verbindung zu testen, wählen Sie **HOMEMORTGAGEACCOUNT** aus und geben Sie ihr einen get-Dienst. Testen Sie den Dienst und Systemadministratoren können sehen, wie Daten abgerufen werden.

### Adobe Analytics-Konfiguration (optional) {#adobe-analytics-configuration}

Dieser Abschnitt enthält Details und Anweisungen zur Adobe Analytics Cloud-Konfiguration.

**Verweise:**

* [Integration mit Adobe Analytics](../../sites-administering/adobeanalytics.md)

* [Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks](../../sites-administering/adobeanalytics-connect.md)

* [Anzeigen von Seitenanalysedaten](../../sites-authoring/pa-using.md)

* [Konfigurieren von Analytics und Berichten](configure-analytics-forms-documents.md)

* [Anzeigen und Verstehen der Analytics-Berichte in AEM Forms](view-understand-aem-forms-analytics-reports.md)

### Adobe Analytics Cloud Service-Konfiguration {#adobe-analytics-cloud-service-configuration}

Dieses Paket ist für die Verbindung mit Adobe Analytics vorkonfiguriert. Die folgenden Schritte werden bereitgestellt, damit diese Konfiguration aktualisiert werden kann.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/libs/cq/core/content/tools/cloudservices.html*
1. Suchen Sie den Abschnitt Adobe Analytics und wählen Sie den Link &quot;Konfigurationen anzeigen&quot;.
1. Wählen Sie die Konfiguration &quot;We.Gov Adobe Analytics (Analytics-Konfiguration)&quot;aus.

   ![Konfiguration des Analytics Cloud Service](assets/analytics_config.jpg)

1. Klicken Sie auf die Schaltfläche &quot;Bearbeiten&quot;, um die Adobe Analytics-Konfiguration zu aktualisieren (Sie müssen das Shared Secret angeben). Klicken Sie auf &quot;Mit Analytics verbinden&quot;, um eine Verbindung herzustellen, und auf &quot;OK&quot;, um die Verbindung abzuschließen.

   ![We.Gov Adobe Analytics](assets/wegov_adobe_analytics.jpg)

1. Klicken Sie auf derselben Seite auf &quot;We.Gov Adobe Analytics Framework (Analytics Framework)&quot;, wenn Sie die Framework-Konfigurationen aktualisieren möchten (siehe [Aktivieren Sie AEM Authoring](../../forms/using/forms-install-configure-gov-reference-site.md#enableauthoring), um die Bearbeitung zu aktivieren).

#### Adobe Analytics - Suchen von Benutzeranmeldeinformationen {#analytics-locating-user-credentials}

Um die Benutzeranmeldeinformationen für ein Adobe Analytics-Konto zu finden, muss der Kontoadministrator die folgenden Aufgaben ausführen.

1. Navigieren Sie zum Adobe Experience Cloud-Portal.
   * Melden Sie sich mit Ihren Administratorberechtigungen an
1. Wählen Sie im Haupt-Dashboard das Symbol Adobe Analytics aus.
   ![Schnellzugriff](assets/aftia-quick-access.jpg)
1. Navigieren Sie zur Registerkarte Admin und wählen Sie das Element User Management (Legacy) aus.
   ![Berichte](assets/aftia-reports.jpg)
1. Wählen Sie die Registerkarte **Benutzer** aus.
   ![Benutzerverwaltung](assets/aftia-user-management.jpg)
1. Wählen Sie den gewünschten Benutzer aus der Liste der Benutzer aus.
1. Scrollen Sie nach unten auf der Seite, und die Authentifizierungsinformationen für Benutzer werden unten auf der Seite angezeigt.
   ![Zugriff verwalten](assets/aftia-admin-user-access.jpg)
1. Der Benutzername und die gemeinsamen geheimen Informationen werden rechts im Berechtigungsfeld angezeigt.
1. Beachten Sie, dass der Benutzername einen Doppelpunkt im Namen enthält. Alle Informationen links vom Doppelpunkt sind der Benutzername und alle Informationen rechts vom Doppelpunkt sind der Firmenname.
   * Im Folgenden finden Sie ein Beispiel dafür: *Benutzername : Firmenname*

#### Einrichten der Benutzerauthentifizierung in Adobe Analytics {#setup-user-authentication}

Administratoren können Benutzern AEM Analyseberechtigungen erteilen, indem sie die folgenden Aktionen ausführen.

1. Navigieren Sie zur Adobe Admin Console.

1. Klicken Sie auf die Analytics-Instanz, die der Admin Console angezeigt wird.

   * Dies befindet sich auf der Hauptseite der Admin-Seite.

1. Wählen Sie Vollständiger Administratorzugriff für Analytics aus.

1. Fügen Sie einen Benutzer zum Profil hinzu.

   ![Vollständiger Administratorzugriff für Analytics](assets/aftia-full-admin-access.jpg)

1. Klicken Sie auf die Registerkarte Berechtigungen , sobald die Benutzer-ID dem Profil zugeordnet wurde.

1. Stellen Sie sicher, dass alle Berechtigungen dem Profil zugeordnet sind.

   ![Berechtigungen bearbeiten](assets/aftia-admin-access-edit.jpg)

1. Beachten Sie, dass es nach der Zuweisung der Berechtigungen einige Stunden dauern kann, bis sich ein Benutzer anmelden kann.

### Adobe Analytics Reporting {#adobe-analytics-reporting}

#### Anzeigen von Adobe Analytics Sites-Berichten {#view-adobe-analytics-sites-reporting}

>[!NOTE]
AEM Forms Analytics-Daten sind offline oder ohne Adobe Analytics-Cloud-Konfiguration verfügbar, wenn das `we-gov-forms.ui.analytics-<version>.zip`-Paket installiert ist, für AEM Sites-Daten jedoch eine aktive Cloud-Konfiguration erforderlich ist.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Wählen Sie die Site &quot;AEM Forms We.Gov&quot;aus, um die Seiten der Site anzuzeigen.
1. Wählen Sie eine der Seiten der Site aus (z. B. Startseite) und wählen Sie &quot;Analytics und Recommendations&quot;.

   ![Analyse und Recommendations](assets/analytics_recommendations.jpg)

1. Auf dieser Seite werden abgerufene Informationen aus Adobe Analytics angezeigt, die sich auf die AEM Sites-Seite beziehen (Hinweis: Diese Informationen werden regelmäßig von Adobe Analytics aktualisiert und nicht in Echtzeit angezeigt.

   ![AEM Sites-Analyse](assets/sites_analysis.jpg)

1. Zurück auf der Seitenansichtsseite (Zugriff in Schritt 3) können Sie die Seitenansichtsinformationen auch anzeigen, indem Sie die Anzeigeeinstellung ändern und Elemente in der &quot;Listenansicht&quot;anzeigen.
1. Suchen Sie das Dropdown-Menü &quot;Ansicht&quot;und wählen Sie &quot;Listenansicht&quot;.

   ![Listenansicht](assets/list_view.jpg)

1. Wählen Sie im selben Menü &quot;Anzeigeeinstellung&quot;aus und wählen Sie die Spalten, die Sie anzeigen möchten, aus dem Abschnitt &quot;Analytics&quot;aus.

   ![Spalten konfigurieren](assets/configure_columns.jpg)

1. Klicken Sie auf &quot;Aktualisieren&quot;, um die neuen Spalten verfügbar zu machen.

   ![Anzeige neuer Spalten](assets/new_columns_display.jpg)

#### Anzeigen von Adobe Analytics forms-Berichten {#view-adobe-analytics-forms-reporting}

>[!NOTE]
AEM Forms Analytics-Daten sind offline oder ohne Adobe Analytics-Cloud-Konfiguration verfügbar, wenn das `we-gov-forms.ui.analytics-<version>.zip`-Paket installiert ist, für AEM Sites-Daten jedoch eine aktive Cloud-Konfiguration erforderlich ist.

1. Gehen Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Wählen Sie das adaptive Formular &quot;Registrierungsanwendung für Gesundheitsvorteile&quot;und dann die Option &quot;Analysebericht&quot;.

   ![Analytics-Bericht](assets/analytics_report.jpg)

1. Warten Sie, bis die Seite geladen wurde, und zeigen Sie die Daten des Analytics-Berichts an.

   ![Analytics-Berichtsdaten anzeigen](assets/analytics_report_data.jpg)

### Aktivierung der automatischen Forms-Konfiguration für Adobe {#automated-forms-enablement}

Um AEM Forms mit der Adobe Forms zu installieren und zu konfigurieren, müssen Benutzer des Konvertierungs-Tools über Folgendes verfügen.

1. Zugriff auf Adobe I/O.

1. Berechtigung zum Erstellen einer Integration mit dem Adobe Forms Conversion-Dienst.

1. Adobe AEM 6.5 neuestes Service Pack, das als Autor ausgeführt wird.

Lesen Sie vor dem Lesen weiterer Anweisungen Folgendes:

* [Dienst zur automatischen Formularkonvertierung konfigurieren](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/configure-service.html)

#### Erstellen einer IMS-Konfiguration Teil 1 {#creating-ims-config}

Damit der Dienst ordnungsgemäß mit dem Konvertierungs-Tool für Formulare kommunizieren kann, müssen die Benutzer den Identity Management-Systemdienst (IMS) konfigurieren, damit sie sich bei Adobe I/O registrieren können.

1. Navigieren Sie zu https://&lt;aemserver>:&lt;port> > Klicken Sie auf Adobe Experience
Manager oben links > Tools > Sicherheit > Adobe IMS-Konfiguration.

1. Klicken Sie auf Erstellen.

1. Führen Sie die Aktionen im folgenden Bild aus.

   ![Technische Kontokonfiguration für IMS](assets/aftia-technical-account-configuration.jpg)

1. Laden Sie das Zertifikat herunter.

1. Fahren Sie nicht mit dem Rest der Konfiguration fort - siehe Abschnitt [Erstellen einer Integration in Adobe I/O](#create-integration-adobeio)

>[!NOTE]
Das in diesem Abschnitt erstellte Zertifikat wird verwendet, um den Integrationsdienst in Adobe I/O zu erstellen. Sobald Benutzer im Integrationsdienst erstellt haben, können Benutzer diese Informationen aus Adobe I/O verwenden, um die Konfiguration abzuschließen.

#### Erstellen der Integration in Adobe I/O {#create-integration-adobeio}

Stellen Sie sicher, dass Sie die Möglichkeit haben, eine Integration in Ihrer Adobe-Domäne zu erstellen, wenn Sie sich hierzu nicht an Ihren Systemadministrator wenden.

1. Navigieren Sie zur [Adobe I/O Console](https://console.adobe.io/).

1. Klicken Sie auf Integration erstellen.

1. Wählen Sie Auf API zugreifen aus.

1. Vergewissern Sie sich, dass Sie sich in der richtigen Gruppe befinden (Dropdown-Liste oben rechts).

1. Wählen Sie im Bereich Experience Cloud das Forms-Konvertierungstool aus.

1. Klicken Sie auf Weiter.

1. Geben Sie den Namen und die Beschreibung Ihrer Integration ein.

1. Durch Verwendung des öffentlichen Schlüssels aus Abschnitt 2.1 wird dieser in die Integration des Schlüssels eingefügt.

1. Wählen Sie ein Profil für Ihre automated forms conversion aus.

   ![Neue Integration erstellen](assets/aftia-create-new-integration.jpg)

#### Erstellen der IMS-Konfiguration Teil 2 {#create-ims-config-part-next}

Nachdem Sie eine Integration erstellt haben, sollten wir die Installation der IMS-Konfiguration abschließen.

1. Klicken Sie in Adobe I/O auf Ihre Integration, um die Verbindungsdetails anzuzeigen.

1. Navigieren Sie in AEM zu Ihrer IMS-Konfiguration (Tools > Sicherheit > IMS).

1. Klicken Sie im Bildschirm IMS-Konfiguration auf Weiter .

1. Geben Sie den Autorisierungsserver ein (im Screenshot angezeigter Wert).

1. Geben Sie den API-Schlüssel ein.

1. Geben Sie den Client-Geheimnis ein (klicken Sie auf In Adobe I/O verfügbar machen , damit er angezeigt wird).

1. Klicken Sie in Adobe I/O auf die Registerkarte JWT , um die JWT-Payload abzurufen und sie in die Payload der IMS-Konfiguration einzufügen.

   ![Payload-IMS-Konfiguration](assets/aftia-payload-ims-config.jpg)

1. Klicken Sie nach der Erstellung auf die IMS-Konfiguration und wählen Sie Konsistenzprüfung aus. Die Benutzer sollten das folgende Ergebnis sehen.

   ![Konsistenzbestätigung](assets/aftia-health-confirmation.jpg)

#### Konfigurieren der Cloud-Konfiguration (We.Gov-AFC-Produktion) {#configure-cloud-configuration}

Sobald die IMS-Konfiguration abgeschlossen ist, können wir die Cloud-Konfiguration in AEM überprüfen. Wenn die Konfiguration nicht vorhanden ist, führen Sie die folgenden Schritte aus, um die Cloud-Konfiguration in AEM zu erstellen:

1. Öffnen Sie den Browser und navigieren Sie zur System-URL https://&lt;Domänenname>:&lt;Systemport>.

1. Klicken Sie oben links im Bildschirm auf Adobe Experience Manager > Tools > Cloud Services > Konfiguration der automatisierten Forms-Konversation .

1. Wählen Sie den Konfigurationsordner aus, in dem Sie die Konfiguration ablegen möchten.

1. Klicken Sie auf Erstellen.

1. Geben Sie die Informationen im folgenden Screenshot ein.

   ![AFC-Produktion](assets/aftia-afc-production.jpg)

1. Geben Sie der Konfiguration einen Titel und einen Namen.

1. Die Dienst-URL für das System ist auf https://aemformsconversion.adobe.io/ festgelegt.

1. Vorlagen-URL */conf/we-gov/settings/wcm/templates/we-gov-flamingo-template*.

1. Design-URL: */content/dam/formsanddocuments-themes/adobe-gov-forms-themes/we-gov-theme*

1. Klicken Sie auf Weiter.

1. Für diese Konfiguration haben wir die beiden Kontrollkästchenwerte leer gelassen.

   * Weitere Informationen zu diesen Optionen finden Sie unter [Konfigurieren des Cloud-Dienstes](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/configure-service.html#configure-the-cloud-service).

#### Konfigurieren der Cloud-Konfiguration (We.Finance AFC Production) {#configure-cloud-configuration-wefinance}

Sobald die IMS-Konfiguration abgeschlossen ist, können wir mit der Erstellung der Cloud-Konfiguration in AEM fortfahren.

1. Öffnen Sie den Browser und navigieren Sie zur System-URL https://&lt;Domänenname>:&lt;Systemport>.

1. Klicken Sie oben links im Bildschirm auf Adobe Experience Manager > Tools > Cloud Services > Konfiguration der automatisierten Forms-Konversation .

1. Wählen Sie den Konfigurationsordner aus, in dem Sie die Konfiguration ablegen möchten.

1. Klicken Sie auf Erstellen.

1. Geben Sie die Informationen im folgenden Screenshot ein.

   ![We.Finance AFC Production](assets/aftia-wefinance-afc-prod.jpg)

1. Geben Sie der Konfiguration einen Titel und einen Namen.

1. Die Dienst-URL für das System ist auf https://aemformsconversion.adobe.io/ festgelegt.

1. Vorlagen-URL: */conf/we-finance/settings/wcm/templates/we-finance-adaptive-form*

1. Design-URL: */content/dam/formsanddocuments-themes/adobe-finance-forms-themes/we-finance-theme*

1. Klicken Sie auf Weiter.

1. Für diese Konfiguration haben wir die beiden Kontrollkästchenwerte leer gelassen.

   * Weitere Informationen zu diesen Optionen finden Sie unter [Konfigurieren des Cloud-Dienstes](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/configure-service.html#configure-the-cloud-service).

#### Testen der Formularkonvertierung (We.Gov-Registrierungsanwendung) {#test-forms-conversion}

Sobald die Konfiguration eingerichtet ist, können Benutzer sie testen, indem sie ein PDF-Dokument hochladen.

1. Navigieren Sie zum AEM System https://&lt;Domänenname>:&lt;Systemport>.

1. Klicken Sie auf Forms > Forms &amp; Documents > AEM Forms We.gov Forms > AFC.

1. Wählen Sie die PDF-Datei &quot;We.Gov Enrollment Application&quot;aus.

1. Klicken Sie oben rechts auf die Schaltfläche **Automatische Konversion starten** .

1. Benutzer sollten die Option wie unten dargestellt sehen können.

   ![Konvertiertes adaptives Formular](assets/aftia-converted-adaptive-form.jpg)

1. Nachdem die Schaltfläche ausgewählt wurde, werden den Benutzern die folgenden Optionen angezeigt

   * Stellen Sie sicher, dass Benutzer die Konfiguration *We.Gov AFC Production* auswählen.

   ![Konvertierungseinstellungen](assets/aftia-conversion-settings.jpg)

   ![Erweiterte Konvertierungseinstellungen](assets/aftia-conversion-settings-2.jpg)

1. Wählen Sie Konvertierung starten aus, sobald Sie alle Optionen konfiguriert haben, die Sie verwenden möchten.

1. Wenn der Konvertierungsprozess beginnt, sollten die Benutzer den folgenden Bildschirm sehen:

   ![Konvertierungseinstellungen](assets/aftia-conversion-in-progress.jpg)

1. Wenn die Konvertierung abgeschlossen ist, sehen die Benutzer den folgenden Bildschirm:

   ![Konvertiertes adaptives Formular](assets/aftia-converted-adaptive-form-2.jpg)

   Klicken Sie auf den Ordner **Output** , um das generierte adaptive Formular anzuzeigen.

#### Bekannte Probleme und Hinweise {#known-issues-notes}

Der Automated forms conversion-Dienst umfasst bestimmte [Best Practices, bekannte komplexe Muster](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/styles-and-pattern-considerations-and-best-practices.html) und [bekannte Probleme](https://docs.adobe.com/content/help/en/aem-forms-automated-conversion-service/using/known-issues.html). Lesen Sie diese, bevor Sie mit der Verwendung des AEM Forms Automated forms conversion-Dienstes beginnen.

1. Generieren Sie das Formular mit Adaptive(s) Formular(e) erzeugen ohne Datenbindungen aktiviert zu haben, wenn Sie das Formular nach der Konvertierung an einen FDM binden möchten.

1. Stellen Sie sicher, dass im Vorlagenordner die Berechtigung jcr:read für alle aktiviert ist. Andernfalls kann der Dienstbenutzer die Vorlage nicht aus dem Repository lesen, und die Konvertierung schlägt fehl.

## Anpassung von Demopaketen {#demo-package-customizations}

Dieser Abschnitt enthält Anweisungen zur Anpassung der Demo.

### Vorlagenanpassung {#templates-customization}

Bearbeitbare Vorlagen finden Sie unter folgenden Adressen:

*https://&lt;aemserver>:&lt;port>/libs/wcm/core/content/sites/templates.html/conf/we-gov*

Zu diesen Vorlagen gehören die Vorlagen für AEM Site, adaptive Formulare und interaktive Kommunikation, die mit Komponenten erstellt und zusammengestellt wurden, die Sie unter folgenden Adressen finden:

*https://&lt;aemserver>:&lt;port>/crx/de/index.jsp#/apps/we-gov/components*

#### Stilsystem {#customizetemplates}

Auf dieser Website finden Sie auch Client-Bibliotheken, von denen eine Bootstrap 4 ( [https://getbootstrap.com/](https://getbootstrap.com/) ) importiert. Diese Client-Bibliothek ist verfügbar unter

*https://&lt;aemserver>:&lt;port>/crx/de/index.jsp#/apps/we-gov/clientlibs/clientlib-base/css/bootstrap*

Die bearbeitbaren Vorlagen, die in diesem Package enthalten sind, sind auch mit Vorlagen-/Seitenrichtlinien vorkonfiguriert, die die CSS-Klassen von Bootstrap 4 für Paginierung, Stil usw. verwenden. Nicht alle Klassen wurden zu den Vorlagenrichtlinien hinzugefügt, aber jede Klasse, die von Bootstrap 4 unterstützt wird, kann zu den Richtlinien hinzugefügt werden. Eine Liste der verfügbaren Klassen finden Sie auf der Seite Erste Schritte :

[https://getbootstrap.com/docs/4.1/getting-started/introduction/](https://getbootstrap.com/docs/4.1/getting-started/introduction/)

Die in diesem Paket enthaltenen Vorlagen unterstützen auch das Stilsystem:

[Stilsystem](../../sites-authoring/style-system.md)

#### Vorlagen-Logos {#template-logos}

Projekt-DAM-Assets umfassen auch We.Gov-Logos und -Bilder. Diese Assets sind verfügbar unter:

*https://&lt;aemserver>:&lt;port>/assets.html/content/dam/we-gov*

Bei der Bearbeitung der Seiten- und Formularvorlagen können Sie Markenlogos aktualisieren, indem Sie die Komponenten Navigation und Fußzeile bearbeiten. Diese Komponenten bieten ein konfigurierbares Marken- und Logo-Dialogfeld, mit dem Logos aktualisiert werden können:

![Vorlagen-Logos](assets/template_logos.jpg)

Weitere Informationen finden Sie unter Bearbeiten des Seiteninhalts :

[Bearbeiten des Seiteninhalts](../../sites-authoring/editing-content.md)

### Siteseiten-Anpassung {#sites-pages-customization}

Alle Webseiten sind verfügbar unter: *https://&lt;aemserver>:&lt;port>/sites.html/content/we-gov*

Auf diesen Seiten wird auch das AEM Grid-Paket verwendet, um das Layout einiger Komponenten zu steuern.

#### Stilsystem {#style-system}

Die in diesem Paket enthaltenen Seiten unterstützen auch das Stilsystem:

[Stilsystem](../../sites-authoring/style-system.md)

Die Dokumentation zu unterstützten Stilen finden Sie unter [Vorlagenanpassungsstilsystem](../../forms/using/forms-install-configure-gov-reference-site.md#customizetemplates) .

### Anpassung adaptiver Formulare {#adaptive-forms-customization}

Alle adaptiven Formulare sind verfügbar unter:

*https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

Diese Formulare können an bestimmte Anwendungsfälle angepasst werden. Beachten Sie, dass bestimmte Felder und die Übermittlungslogik nicht geändert werden sollten, um sicherzustellen, dass das Formular weiterhin ordnungsgemäß funktioniert. Hierzu gehört Folgendes:

**Registrierungsantrag für Gesundheitsleistungen:**

* contact_id - Ausgeblendetes Feld, das zum Empfangen der MS Dynamics-Kontakt-ID während der Übermittlung verwendet wird
* Senden - Die Logik der Sendeschaltfläche muss angepasst werden, um Rückrufe zu unterstützen. Die Anpassung ist dokumentiert, es war jedoch ein großes Skript erforderlich, um das Formular zu senden, während sowohl eine POST als auch ein GET über das Forms-Datenmodell an MS Dynamics durchgeführt wurde.
* Stammbereich - Das Initialisierungsereignis wird verwendet, um dem AEM Posteingang eine MS Dynamics-Schaltfläche hinzuzufügen, da alle Komponenten der Benutzeroberfläche von Inbox Granite nicht geändert werden können.

#### Adaptive Formularstile {#adaptive-form-styling}

Adaptive Formulare können auch mit dem Stileditor oder dem Design-Editor formatiert werden:

* [Inline-Stile für Komponenten adaptiver Formulare](inline-style-adaptive-forms.md)
* [Erstellen und Verwenden von Designs](themes.md)

### Workflow-Anpassung {#workflow-customization}

Das adaptive Registrierungsformular sendet zur Verarbeitung an einen OSGi-Workflow. Dieser Workflow finden Sie unter *https://&lt;aemserver>:&lt;port>/conf/we-gov/settings/models/we-gov-process.html*.

Aufgrund bestimmter Einschränkungen enthält dieser Workflow mehrere Skripte und benutzerdefinierte OSGi-Workflow-Prozessschritte. Diese Workflow-Schritte wurden als allgemeine Schritte erstellt und nicht mit Konfigurationsdialogfeldern erstellt. Derzeit beruht die Konfiguration der Workflow-Schritte auf Prozessargumenten.

Der gesamte Java-Code für den Workflow-Schritt ist im Bundle **we-gov-forms.core-&lt;version>.jar** enthalten.

## Überlegungen zur Demo und bekannte Probleme {#demo-considerations-and-known-issues}

Dieser Abschnitt enthält Informationen zu Demofunktionen und Designentscheidungen, die während des Demonstrationsprozesses möglicherweise besondere Überlegungen erfordern.

### Überlegungen zur Demo {#demo-considerations}

* Stellen Sie gemäß AGRS-159 sicher, dass der Name (erster, mittlerer und letzter) des Kontakts, der im adaptiven Formular für die Registrierung verwendet wird, eindeutig ist.
* Das adaptive Registrierungsformular sendet die Adobe Sign-E-Mail an die E-Mail, die im E-Mail-Feld des Formulars angegeben ist. Diese E-Mail-Adresse darf nicht dieselbe E-Mail-Adresse sein wie die E-Mail, die zum Konfigurieren der Adobe Sign-Cloud-Konfiguration verwendet wurde.

### Bekannte Probleme {#known-issues}

* (AGRS-120) Die Site-Navigationskomponente unterstützt derzeit keine verschachtelten untergeordneten Seiten, die mehr als zwei Ebenen tief sind.
* (AGRS-159) Das aktuelle MS Dynamics FDM muss zwei Vorgänge ausführen, um zuerst die Daten des adaptiven Formulars für die Registrierung in Dynamics POST und dann den Benutzerdatensatz abzurufen, um die Kontakt-ID abzurufen. Im aktuellen Status schlägt das Abrufen der Kontakt-ID fehl, wenn in Dynamics mehr als zwei Benutzer mit demselben Namen vorhanden sind, was die Übermittlung des adaptiven Registrierungsformulars nicht zulässt.

## Konfigurieren der Barrierefreiheitstests {#configure-accessibility-testing}

### Aktivieren der Barrierefreiheitsprüfung Chrome Add On {#enable-chrome-add-on}

Um Barrierefreiheitstests durchzuführen, müssen Sie zunächst das Chrome-Plug-in installieren. Dies finden Sie hier [hier](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?hl=en).

Laden Sie nach der Installation die Seite, die Sie im Chrome-Browser testen möchten (Hinweis: Wenn mehrere Tabs geöffnet sind, kann sich dies auf Ihre Punktzahl auswirken. Es ist empfehlenswert, nur eine Registerkarte zu öffnen.) Sobald die Seite geladen wurde
**Klicken Sie mit der rechten Maustaste auf** auf der Seite und wählen Sie die Registerkarte **Audits** . Es können Entwickler den Typ der Prüfung auswählen, die vom Plug-in für Barrierefreiheit durchgeführt werden soll. Nachdem alle gewünschten Optionen ausgewählt wurden, kann der Benutzer die Schaltfläche Bericht generieren auswählen. Dadurch wird ein PDF-Dokument generiert, das die Gesamtbewertung der Barrierefreiheit und die Möglichkeiten zur Steigerung der Barrierefreiheit insgesamt anzeigt.

Sobald der Bericht ausgeführt wurde, können die Benutzer Folgendes erwarten:

![Zugänglichkeitsbericht](assets/aftia-accessibility.jpg)

Die Zahl, die vor den Benutzern angezeigt wird, ist die Gesamtbewertung der Barrierefreiheit, die sie erworben haben. Es gibt auch eine Beschreibung, wie diese Berechnung auf der Grundlage des Ergebnisses vorgenommen wurde.

Wenn Benutzer dies exportieren möchten, können sie auf die drei Schaltflächen rechts vom Bildschirm klicken und aus den weiteren Optionen auswählen, die das Plug-in bietet.

![Zugänglichkeitsbericht](assets/aftia-accessibility-report.jpg)

### Ultramarine-Design {#ultramarine-theme}

Das öffentlich verfügbare Ultramarine-Thema, das von der Adobe verwaltet wird, ist in die
`we-gov-forms.pkg.all-<version>.zip` installierbare ZIP-Datei. Sobald dieses Paket mit CRX installiert ist.

Package Manager können Benutzer auf das Ultramarine-Design in AEM Forms zugreifen, indem sie zu **Forms** > **Designs** > **Referenzthemen** > **Ultramarine-Accessible** navigieren.

![Ultramarine-Design](assets/aftia-ultramarine-theme.jpg)

## Konfigurationsoptionen {#configuration-options}

Benutzer haben die Möglichkeit, verschiedene Workflow-Dienstoptionen zu konfigurieren, darunter die folgenden:

1. Microsoft Dynamics-Einstieg
1. Adobe Sign
1. AEM Benutzerdefinierte Kommunikationsverwaltung
1. Adobe Analytics

Um sie so zu konfigurieren, dass sie im Workflow aktiviert werden, müssen Benutzer die folgenden Aufgaben ausführen.

1. Navigieren Sie zu https://&#39;[server]:[port]&#39;/system/console/configMgr.

1. Suchen Sie die *WeGov-Konfigurationen*.

1. Öffnen Sie die Dienstdefinition und aktivieren Sie den Aufruf der ausgewählten Dienste innerhalb des Workflows.

   >[!NOTE]
   Nur weil ein Benutzer den Dienst auf der Seite &quot;Configuration Manager&quot;aktiviert, müssen Benutzer weiterhin eine Dienstkonfiguration einrichten, um mit den angeforderten externen Diensten kommunizieren zu können.

   ![Wir gov Forms-Paket](assets/aftia-configuration-options.jpg)

1. Klicken Sie anschließend auf die Schaltfläche Speichern , um die Einstellungen zu speichern.

## Nächste Schritte {#next-steps}

Jetzt können Sie alle die Referenz-Site &quot;We.Gov&quot;durchsuchen. Weitere Informationen zum Workflow und den Schritten der We.Gov-Referenz-Website finden Sie unter [Schrittweise Anleitung zur We.Gov-Referenz-Website](../../forms/using/forms-gov-reference-site-user-demo.md).
