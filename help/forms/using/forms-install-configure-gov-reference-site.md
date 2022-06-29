---
title: Einrichten und Konfigurieren der Referenz-Website We.Gov und WeFinance
seo-title: Set up and configure We.Gov reference site
description: Installieren und konfigurieren Sie ein AEM Forms-Demopaket und passen Sie es dann an.
seo-description: Install, configure, and customize an AEM Forms demo package.
uuid: 0a6ad8f9-0d38-40c3-ad8d-e705edef55f8
contentOwner: anujkapo
discoiquuid: fe5da0aa-d3a8-4b77-a447-9e429fdc2816
docset: aem65
exl-id: 1fee474e-7da5-4ab2-881a-34b8e055aa29
source-git-commit: 1def8ff7bc90e2ab82ce8b50277a97da9709c78c
workflow-type: ht
source-wordcount: '4703'
ht-degree: 100%

---

# Einrichten und Konfigurieren der Referenz-Website We.Gov und WeFinance {#set-up-and-configure-we-gov-reference-site}

## Details zum Demopaket {#demo-package-details}

### Installationsvoraussetzungen {#installation-prerequisites}

Dieses Paket wurde für **AEM Forms 6.4 OSGI-Autor** erstellt. Es wurde getestet und wird daher in den folgenden Plattformversionen unterstützt:

| AEM-VERSION | AEM FORMS-PAKET-VERSION | STATUS |
|---|---|---|
| 6.4 | 5.0.86 | **Unterstützt** |
| 6.5 | 6.0.80 | **Unterstützt** |
| 6.5.3 | 6.0.122 | **Unterstützt** |

Dieses Paket enthält eine Cloud-Konfiguration, die die folgenden Plattformversionen unterstützt:

| CLOUD-PROVIDER | SERVICE-VERSION | STATUS |
|---|---|---|
| Adobe Sign | v5-API | **Unterstützt** |
| Microsoft Dynamics 365 | 1710 (9.1.0.3020) | **Unterstützt** |
| Adobe Analytics | v1.4-Rest-API | **Unterstützt** |
**Überlegungen zur Paketinstallation:**

* Es wird erwartet, dass das Paket auf einem sauberen Server installiert wird, frei von anderen Demopaketen oder älteren Demopaketversionen
* Es wird erwartet, dass das Paket auf einem OSGI-Server installiert wird, der im Autorenmodus ausgeführt wird

### Was enthält dieses Paket? {#what-does-this-package-include}

Das [AEM Forms-We.Gov-Demopaket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/we-gov-forms.pkg.all-2.0.2.zip) (**we-gov-forms.pkg.all-&lt;version>.zip**) wird als Paket geliefert, das mehrere andere Unterpakete und Services enthält. Das Paket enthält die folgenden Module:

* **we-gov-forms.pkg.all-&lt;version>.zip** – *Vollständiges Demopaket*

   * **we-gov-forms.ui.apps-&lt;version>.zip** *– Enthält alle Komponenten, Client-Bibliotheken, Beispielbenutzer, Workflow-Modelle usw.*

      * **we-gov-forms.core-&lt;version>.jar** – *Enthält alle OSGi-Services, die Implementierung benutzerdefinierter Workflow-Schritte usw.*

      * **we-gov-forms.derby&lt;version>.jar** – *Enthält alle OSGi-Services, Datenbankschemas usw.*

      * **core.wcm.components.all-2.0.4.zip** – *Sammlung von WCM-Beispielkomponenten*

      * **grid-aem.ui.apps-1.0-SNAPSHOT.zip** – *AEM Sites Grid-Layout-Paket für die Seitenspaltensteuerung in Sites*
   * **we-gov-forms.ui.content-&lt;version>.zip** – *Enthält alle Inhalte, Seiten, Bilder, Formulare, interaktiven Kommunikations-Assets usw.*

   * **we-gov-forms.ui.analytics-&lt;version>.zip** – *Enthält alle Forms-Analysedaten zu We.Gov, die im Repository gespeichert werden sollen.*

   * **we-gov-forms.config.public-&lt;version>.zip** – *Enthält alle standardmäßigen Konfigurationsknoten, einschließlich Platzhalter-Cloud-Konfigurationen, um Probleme mit Formulardatenmodellen und Service-Bindung zu vermeiden.*


Zu den in diesem Paket enthaltenen Assets gehören:

* AEM-Website-Seiten mit bearbeitbaren Vorlagen
* Adaptive Formulare in AEM Forms
* Interaktive Kommunikation in AEM Forms (Print- und Web-Kanal)
* Aufzuzeichnendes XDP-Dokument in AEM Forms
* MS Dynamics-Formulardatenmodell in AEM Forms
* Adobe Sign-Integration
* AEM-Workflow-Modell
* AEM Assets-Beispielbilder
* Beispiel-Apache Derby-Datenbank (im Speicher)
* Apache Derby-Datenquelle (zur Verwendung mit dem Formulardatenmodell)

## Installation des Demopakets {#demo-package-installation}

Dieser Abschnitt enthält Informationen zur Installation des Demopakets.

### Von Software Distribution {#from-software-distribution}

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den Paketnamen **we-gov-forms.pkg.all-&lt;version>.zip**, wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   ![WeGov-Formularpaket](assets/wegov_forms_package.jpg)

1. Lassen Sie den Abschluss des Installationsprozesses zu.
1. Gehen Sie zu *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html?wcmmode=disabled*, um sicherzugehen, dass die Installation erfolgreich war.

### Von einer lokalen ZIP-Datei {#from-a-local-zip-file}

1. Laden Sie die Datei **we-gov-forms.pkg.all-&lt;version>.zip** herunter und suchen Sie sie.
1. Gehen Sie zu *https://&lt;aemserver>:&lt;port>/crx/packmgr/index.jsp*.
1. Wählen Sie die Option „Paket hochladen“.

   ![Option „Paket hochladen“](assets/upload_package.jpg)

1. Verwenden Sie den Datei-Browser, um zur heruntergeladenen ZIP-Datei zu gelangen und sie auszuwählen.
1. Klicken Sie zum Hochladen auf „Öffnen“.
1. Wählen Sie nach dem Hochladen die Option „Installieren“, um das Paket zu installieren.

   ![WeGov Forms-Paket installieren](assets/wegov_forms_package-1.jpg)

1. Lassen Sie den Abschluss des Installationsprozesses zu.
1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html?wcmmode=disabled*, um sicherzustellen, dass die Installation erfolgreich war.

### Installieren neuer Paketversionen {#installing-new-package-versions}

Um eine neue Paketversion zu installieren, führen Sie die in 4.1 und 4.2 definierten Schritte aus. Es ist möglich, eine neuere Paketversion zu installieren, während bereits ein älteres Paket installiert ist. Es wird jedoch empfohlen, die ältere Paketversion zuerst zu deinstallieren. Gehen Sie dazu wie folgt vor.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/crx/packmgr/index.jsp*
1. Suchen Sie die ältere Datei **we-gov-forms.pkg.all-&lt;version>.zip**.
1. Wählen Sie die Option „Mehr“.
1. Wählen Sie im Dropdown-Menü die Option „Deinstallieren“.

   ![WeGov-Paket deinstallieren](assets/uninstall_wegov_forms_package.jpg)

1. Wählen Sie nach der Bestätigung erneut „Deinstallieren“ und warten Sie, bis der Deinstallationsvorgang abgeschlossen ist.

## Konfiguration des Demopakets {#demo-package-configuration}

Dieser Abschnitt enthält Details und Anweisungen zur Konfiguration des Demopakets nach der Implementierung vor der Präsentation.

### Konfigurieren eines fiktiven Benutzers {#fictional-user-configuration}

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/libs/granite/security/content/groupadmin.html*
1. Melden Sie sich als Administrator an, um die unten aufgeführten Aufgaben durchzuführen.
1. Scrollen Sie nach unten zum Ende der Seite, um alle Benutzergruppen zu laden.
1. Suchen Sie nach **workflow**.
1. Wählen Sie die Gruppe **workflow-users** und klicken Sie auf „Eigenschaften“.
1. Navigieren Sie zu der Registerkarte „Mitglieder“.
1. Geben Sie **wegov** in das Feld „Benutzer oder Gruppe wählen“ ein.
1. Wählen Sie aus dem Dropdown-Menü **We.Gov Forms Users**.

   ![Gruppeneinstellungen für Workflow-Benutzer bearbeiten](assets/edit_group_settings.jpg)

1. Klicken Sie in der Menüleiste auf „Speichern und schließen“.
1. Wiederholen Sie die Schritte 2–7, indem Sie nach **Analytics** suchen, die Gruppe **Analytics-Administratoren** auswählen und die Gruppe **We.Gov Forms-Benutzer** als Mitglied hinzufügen.
1. Wiederholen Sie die Schritte 2–7, indem Sie nach **Forms-Benutzer** suchen, die Gruppe **forms-power-users** auswählen und die Gruppe **We.Gov Forms-Benutzer** als Mitglied hinzufügen.
1. Wiederholen Sie die Schritte 2–7, indem Sie nach **Forms-Benutzer** suchen, die Gruppe **forms-users** auswählen und diesmal die Gruppe **We.Gov-Benutzer** als Mitglied hinzufügen.

### Konfiguration des E-Mail-Servers {#email-server-configuration}

1. Lesen Sie die Einrichtungsdokumentation [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md)
1. Melden Sie sich als Administrator an, um diese Aufgabe durchzuführen.
1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/system/console/configMgr*
1. Suchen Sie den Service **Day CQ Mail Service** und klicken Sie darauf, um ihn zu konfigurieren.

   ![Konfigurieren des Day CQ Mail Service](assets/day_cq_mail_service.jpg)

1. Konfigurieren Sie den Service für die Verbindung mit dem gewünschten SMTP-Server:

   1. **Host-Name des SMTP-Servers**: z. B. (smtp.gmail.com)
   1. **Server-Port**: z. B. (465) für Gmail mit SSL
   1. **SMTP-Benutzer:** demo@ &lt;firmenname> .com
   1. **„Von“-Adresse**: aemformsdemo@adobe.com

   ![SMTP konfigurieren](assets/configure_smtp.jpg)

1. Klicken Sie auf „Speichern“, um die Konfiguration zu speichern.

### (Optional) AEM-SSL-Konfiguration {#aemsslconfig}

Dieser Abschnitt enthält Details zur Konfiguration von SSL auf der AEM-Instanz, um die Adobe Sign Cloud-Konfiguration konfigurieren zu können.

**Verweise:**

1. [Die Funktion „SSL By Default“ (SSL als Standard)](/help/sites-administering/ssl-by-default.md)

**Anmerkungen:**

1. Navigieren Sie zu https://&lt;aemserver>:&lt;port>/aem/inbox, wo Sie den im obigen Link zur Referenzdokumentation beschriebenen Vorgang abschließen können.
1. Das Paket `we-gov-forms.pkg.all-[version].zip` enthält einen Beispiel-SSL-Schlüssel und ein Beispiel-Zertifikat, auf die Sie zugreifen können, indem Sie den Ordner `we-gov-forms.pkg.all-[version].zip/ssl` extrahieren, der Teil des Pakets ist.

1. SSL-Zertifikat und Schlüsseldetails:

   1. ausgegeben an „CN=localhost“
   1. Gültigkeit von 10 Jahren
   1. Kennwortwert von „password“
1. Der private Schlüssel ist *localhostprivate.der*.
1. Das Zertifikat ist *localhost.crt*.
1. Klicken Sie auf Weiter.
1. Der HTTPS-Hostname sollte auf *localhost* gesetzt werden.
1. Der Port sollte auf einen Port eingestellt sein, den das System offen gelegt hat.

### (Optional) Cloud-Konfiguration für Adobe Sign {#adobe-sign-cloud-configuration}

Dieser Abschnitt enthält Details und Anweisungen zur Cloud-Konfiguration mit Adobe Sign.

**Verweise:**

1. [Integrieren von Adobe Sign mit AEM Forms](adobe-sign-integration-adaptive-forms.md)

#### Cloud-Konfiguration {#cloud-configuration}

1. Überprüfen Sie die Voraussetzungen. Siehe [AEM-SSL-Konfiguration](../../forms/using/forms-install-configure-gov-reference-site.md#aemsslconfig) für die erforderliche SSL-Konfiguration.
1. Gehen Sie zu:

   *https://&lt;aemserver>:&lt;port>/libs/adobesign/cloudservices/adobesign.html/conf/we-gov*

   >[!NOTE]
   >
   >Die URL, die für den Zugriff auf den AEM-Server verwendet wird, sollte mit der URL übereinstimmen, die im OAuth-Weiterleitungs-URI von Adobe Sign konfiguriert ist, um Konfigurationsprobleme zu vermeiden (z. B. *https://&lt;aemserver>:&lt;port>/mnt/overlay/adobesign/cloudservices/adobesign/properties.html*)

1. Wählen Sie die Konfiguration „We.gov Adobe Sign“ aus.
1. Klicken Sie auf „Eigenschaften“.
1. Navigieren Sie zur Registerkarte „Einstellungen“.
1. Geben Sie die oAuth-URL ein, z. B.: [https://secure.na1.echosign.com/public/oauth](https://secure.na1.echosign.com/public/oauth)
1. Geben Sie die konfigurierte Client-ID und das Client-Geheimnis aus der konfigurierten Adobe Sign-Instanz an.
1. Klicken Sie auf „Verbindung zu Adobe Sign herstellen“.
1. Klicken Sie nach erfolgreicher Verbindung auf „Speichern und schließen“, um die Integration abzuschließen.

### (Optional) MS Dynamics-Cloud-Konfiguration {#ms-dynamics-cloud-configuration}

Dieser Abschnitt enthält Details und Anweisungen zur MS Dynamics-Cloud-Konfiguration.

**Verweise:**

1. [Microsoft Dynamics OData-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-64/forms/form-data-model/ms-dynamics-odata-configuration.html?lang=de)
1. [Konfigurieren von Microsoft Dynamics für AEM Forms](https://helpx.adobe.com/de/experience-manager/kt/forms/using/config-dynamics-for-aem-forms.html)

#### MS Dynamics OData-Cloud-Service {#ms-dynamics-odata-cloud-service}

1. Gehen Sie zu:

   https://&lt;aemserver>:&lt;port>/libs/fd/fdm/gui/components/admin/fdmcloudservice/fdm.html/conf/we-gov

   1. Stellen Sie sicher, dass Sie auf den Server zugreifen, indem Sie dieselbe Umleitungs-URL verwenden, die in der Registrierung des MS Dynamics-Programms konfiguriert wurde.

1. Wählen Sie die Konfiguration „Microsoft Dynamics OData Cloud Service“.
1. Klicken Sie auf „Eigenschaften“.

   ![Eigenschaften für den Microsoft OData-Cloud-Service](assets/properties_odata_cloud_service.jpg)

1. Navigieren Sie zur Registerkarte „Authentifizierungseinstellungen“.
1. Geben Sie die folgenden Details ein:

   1. **Service-Stamm**: z. B. `https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/`
   1. **Authentifizierungstyp**: OAuth 2.0
   1. **Authentifizierungseinstellungen** (siehe [Cloud-Konfigurationseinstellungen für MS Dynamics](../../forms/using/forms-install-configure-gov-reference-site.md#dynamicsconfig) um diese Informationen zu sammeln):

      1. Client-ID – auch als Programm-ID bezeichnet
      1. Client-Geheimnis
      1. OAuth-URL – z. B. [https://login.windows.net/common/oauth2/authorize](https://login.windows.net/common/oauth2/authorize)
      1. Aktualisieren der Token-URL – z. B. [https://login.windows.net/common/oauth2/token](https://login.windows.net/common/oauth2/token)
      1. Zugriffstoken-URL – z. B. [https://login.windows.net/common/oauth2/token](https://login.windows.net/common/oauth2/token)
      1. Genehmigungsumfang – **openid**
      1. Authentifizierungs-Header – **Autorisierungsanbieter**
      1. Ressource – z. B. `https://msdynamicsserver.api.crm3.dynamics.com`
   1. Klicken Sie auf „Verbindung zu OAuth herstellen“.


1. Klicken Sie nach erfolgreicher Authentifizierung auf „Speichern und schließen“, um die Integration abzuschließen.

#### Cloud-Konfigurationseinstellungen für MS Dynamics {#dynamicsconfig}

Die in diesem Abschnitt beschriebenen Schritte bieten Hilfe bei der Suche nach der Client-ID, dem Client-Geheimnis und Details aus Ihrer MS Dynamics Cloud-Instanz.

1. Navigieren Sie zu [https://portal.azure.com/](https://portal.azure.com/) und melden Sie sich an.
1. Wählen Sie im Menü links „Alle Services“ aus.
1. Suchen Sie nach „App-Registrierung“ oder navigieren Sie dorthin.
1. Erstellen oder wählen Sie eine bestehende Programmregistrierung aus.
1. Kopieren Sie die **Programm-ID** zur Verwendung als OAuth-**Client-ID** in der AEM Cloud-Konfiguration
1. Klicken Sie auf „Einstellungen“ oder „Manifest“, um die **Antwort-URLs** zu konfigurieren.

   1. Diese URL muss mit der URL übereinstimmen, die für den Zugriff auf Ihren AEM-Server beim Konfigurieren des OData-Services verwendet wird.

1. Klicken Sie in der Einstellungsansicht auf „Schlüssel“, um einen neuen Schlüssel zu erstellen (dieser wird in AEM als Client-Geheimnis verwendet).

   1. Achten Sie darauf, eine Kopie des Schlüssels zu behalten, da Sie ihn später in Azure oder AEM nicht anzeigen können.

1. Um die Ressourcen-URL/Service-Stamm-URL zu finden, navigieren Sie zum Dashboard der MS Dynamics-Instanz.
1. Klicken Sie in der oberen Navigationsleiste auf „Verkauf“ oder Ihren eigenen Instanztyp und „Einstellungen auswählen“.
1. Klicken Sie unten rechts auf „Anpassungen“ und „Entwicklungsressourcen“.
1. Dort finden Sie die Service-Stamm-URL: z. B.

   *`https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/`

1. Details zur URL für Aktualisierungs- und Zugriffs-Token finden Sie hier:

   *[https://docs.microsoft.com/de-de/rest/api/datacatalog/authenticate-a-client-app](https://docs.microsoft.com/de-de/rest/api/datacatalog/authenticate-a-client-app)*

#### Testen des Formulardatenmodells (Dynamics) {#testing-the-form-data-model}

Sobald die Cloud-Konfiguration abgeschlossen ist, sollten Sie das Formulardatenmodell testen.

1. Gehen Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments-fdm/we-gov*

1. Wählen Sie „Microsoft Dynamics CRM FDM“ aus und klicken Sie auf „Eigenschaften“.

   ![Eigenschaften des Dynamics CRM-FDM](assets/properties_dynamics_crm.jpg)

1. Navigieren Sie zur Registerkarte „Quelle aktualisieren“.
1. Stellen Sie sicher, dass die „kontextsensitive Konfiguration“ auf „/conf/we-gov“ festgelegt ist und dass die konfigurierte Datenquelle „ms-dynamics-odata-cloud-service“ lautet.

   ![Datenquelle konfiguriert](assets/configured_data_source.jpg)

1. Bearbeiten Sie das Formulardatenmodell.

1. Testen Sie die Services, um sicherzustellen, dass sie erfolgreich eine Verbindung zur konfigurierten Datenquelle herstellen.

   >[!NOTE]
   Klicken Sie nach dem Testen der Services auf **Abbrechen** um sicherzustellen, dass unfreiwillige Änderungen nicht an das Formulardatenmodell weitergegeben werden.

   >[!NOTE]
   Es wurde berichtet, dass ein AEM Server-Neustart erforderlich war, damit die Datenquelle erfolgreich an das FDM gebunden werden konnte.

#### Testen des Formulardatenmodells (Derby) {#test-fdm-derby}

Sobald die Cloud-Konfiguration abgeschlossen ist, können Sie das Formulardatenmodell testen.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments-fdm/we-gov*

1. Wählen Sie die **We.gov Enrollment FDM** und wählen Sie **Eigenschaften**.

   ![Eigenschaften des Dynamics CRM-FDM](assets/aftia-enrollment-fdm.jpg)

1. Navigieren Sie zur Registerkarte **Quelle aktualisieren**.

1. Stellen Sie sicher, dass die **Kontextabhängige Konfiguration** auf `/conf/we-gov` gesetzt ist und dass die konfigurierte Datenquelle **We.Gov Derby DS** ist.

   ![Eigenschaften des Dynamics CRM-FDM](assets/aftia-update-data-source.jpg)

1. Klicken Sie auf **Speichern und schließen**.

1. [Testen der Services](work-with-form-data-model.md#test-data-model-objects-and-services), um sicherzustellen, dass sie sich erfolgreich mit der konfigurierten Datenquelle verbinden

   * Um die Verbindung zu testen, wählen Sie das **HOMEMORTGAGEACCOUNT** und geben Sie ihm einen GET-Service. Wenn Sie den Service testen, können Systemadministratoren sehen, wie die Daten abgerufen werden.

### Adobe Analytics-Konfiguration (optional) {#adobe-analytics-configuration}

Dieser Abschnitt enthält Details und Anweisungen zur Adobe Analytics Cloud-Konfiguration.

**Verweise:**

* [Integration mit Adobe Analytics](../../sites-administering/adobeanalytics.md)

* [Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks](../../sites-administering/adobeanalytics-connect.md)

* [Anzeigen von Seitenanalysedaten](../../sites-authoring/pa-using.md)

* [Konfigurieren von Analytics und Berichten](configure-analytics-forms-documents.md)

* [Anzeigen und Verstehen der Analytics-Berichte in AEM Forms](view-understand-aem-forms-analytics-reports.md)

### Adobe Analytics Cloud Service-Konfiguration {#adobe-analytics-cloud-service-configuration}

Dieses Paket ist für die Verbindung mit Adobe Analytics vorkonfiguriert. Die folgenden Schritte werden bereitgestellt, damit diese Konfiguration aktualisiert werden kann.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/libs/cq/core/content/tools/cloudservices.html*
1. Suchen Sie den Abschnitt „Adobe Analytics“ und wählen Sie den Link „Konfigurationen anzeigen“.
1. Wählen Sie die Konfiguration „We.Gov Adobe Analytics (Analytics-Konfiguration)“ aus.

   ![Analytics Cloud-Service-Konfiguration](assets/analytics_config.jpg)

1. Klicken Sie auf die Schaltfläche „Bearbeiten“, um die Adobe Analytics-Konfiguration zu aktualisieren (Sie müssen den gemeinsamen geheimen Schlüssel angeben). Klicken Sie auf „Mit Analytics verbinden“, um eine Verbindung herzustellen, und auf „OK“, um den Vorgang abzuschließen.

   ![We.Gov Adobe Analytics](assets/wegov_adobe_analytics.jpg)

1. Klicken Sie auf derselben Seite auf „We.Gov Adobe Analytics Framework (Analytics Framework)“, wenn Sie die Framework-Konfigurationen aktualisieren möchten (siehe [Aktivieren von AEM-Authoring](../../forms/using/forms-install-configure-gov-reference-site.md#enableauthoring), um das Authoring zu aktivieren).

#### Adobe Analytics – Suchen von Benutzeranmeldeinformationen {#analytics-locating-user-credentials}

Um die Benutzeranmeldeinformationen für ein Adobe Analytics-Konto zu finden, muss der Kontoadministrator die folgenden Aufgaben ausführen.

1. Navigieren Sie zum Adobe Experience Cloud-Portal.
   * Melden Sie sich mit Ihren Administrator-Anmeldeinformationen an.
1. Wählen Sie im Haupt-Dashboard das Adobe Analytics-Symbol aus.
   ![Schnellzugriff](assets/aftia-quick-access.jpg)
1. Navigieren Sie zur Registerkarte „Admin“ und wählen Sie das Element „User Management (Legacy)“ aus.
   ![Berichte](assets/aftia-reports.jpg)
1. Wählen Sie die Registerkarte **Benutzer** aus.
   ![Benutzerverwaltung](assets/aftia-user-management.jpg)
1. Wählen Sie den gewünschten Benutzer aus der Liste der Benutzer aus.
1. Scrollen Sie nach unten auf der Seite, und die Authentifizierungsinformationen des Benutzers werden unten auf der Seite angezeigt.
   ![Zugriff verwalten](assets/aftia-admin-user-access.jpg)
1. Der Benutzername und die Informationen zum gemeinsamen geheimen Schlüssel werden rechts im Berechtigungsfeld angezeigt.
1. Beachten Sie, dass der Benutzername einen Doppelpunkt im Namen enthält. Alle Informationen links vom Doppelpunkt sind der Benutzername und alle Informationen rechts vom Doppelpunkt sind der Firmenname.
   * Im Folgenden finden Sie ein Beispiel dafür: *Benutzername : Firmenname*

#### Einrichten der Benutzerauthentifizierung in Adobe Analytics {#setup-user-authentication}

Administratoren können Benutzern AEM Analytics-Berechtigungen erteilen, indem sie die folgenden Aktionen ausführen.

1. Navigieren Sie zur Adobe Admin Console.

1. Klicken Sie auf die Analytics-Instanz, die in der Admin Console angezeigt wird.

   * Diese befindet sich auf der Hauptseite der Admin-Seite.

1. Wählen Sie den vollständigen Administratorzugriff für Analytics aus.

1. Fügen Sie einen Benutzer zum Profil hinzu.

   ![Vollständiger Administratorzugriff für Analytics](assets/aftia-full-admin-access.jpg)

1. Klicken Sie auf die Registerkarte „Berechtigungen“, sobald die Benutzer-ID dem Profil zugeordnet wurde.

1. Stellen Sie sicher, dass alle Berechtigungen dem Profil zugeordnet sind.

   ![Bearbeiten von Berechtigungen](assets/aftia-admin-access-edit.jpg)

1. Beachten Sie, dass es nach der Zuweisung der Berechtigungen einige Stunden dauern kann, bis sich ein Benutzer anmelden kann.

### Adobe Analytics-Berichte {#adobe-analytics-reporting}

#### Anzeigen von Adobe Analytics Sites-Berichten {#view-adobe-analytics-sites-reporting}

>[!NOTE]
AEM Forms-Analytics-Daten sind offline oder ohne Adobe Analytics-Cloud-Konfiguration verfügbar, wenn das Paket `we-gov-forms.ui.analytics-<version>.zip` installiert ist, für AEM Sites-Daten ist jedoch eine aktive Cloud-Konfiguration erforderlich.

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Wählen Sie die „AEM Forms We.Gov Site“ aus, um die Seiten der Site anzuzeigen.
1. Wählen Sie eine der Seiten der Site aus (z. B. die Startseite) und klicken Sie auf „Analytics &amp; Recommendations“.

   ![Analyse und Recommendations](assets/analytics_recommendations.jpg)

1. Auf dieser Seite werden abgerufene Informationen aus Adobe Analytics angezeigt, die sich auf die AEM Sites-Seite beziehen (Hinweis: Diese Informationen werden regelmäßig von Adobe Analytics aktualisiert und nicht in Echtzeit angezeigt.)

   ![AEM Sites-Analyse](assets/sites_analysis.jpg)

1. Zurück auf der Seitenansichtsseite (aufgerufen in Schritt 3) können Sie die Seitenansichtsinformationen auch anzeigen, indem Sie die Anzeigeeinstellung ändern und Elemente in der „Listenansicht“ anzeigen.
1. Suchen Sie das Dropdown-Menü „Ansicht“ und wählen Sie „Listenansicht“.

   ![Listenansicht](assets/list_view.jpg)

1. Wählen Sie im selben Menü „Anzeigeeinstellungen“ aus und wählen Sie die Spalten, die Sie anzeigen möchten, aus dem Abschnitt „Analytics“ aus.

   ![Konfigurieren der Spalten](assets/configure_columns.jpg)

1. Klicken Sie auf „Aktualisieren“, um die neuen Spalten verfügbar zu machen.

   ![Anzeige neuer Spalten](assets/new_columns_display.jpg)

#### Anzeigen von Adobe Analytics-Formularberichten {#view-adobe-analytics-forms-reporting}

>[!NOTE]
AEM Forms-Analytics-Daten sind offline oder ohne Adobe Analytics-Cloud-Konfiguration verfügbar, wenn das Paket `we-gov-forms.ui.analytics-<version>.zip` installiert ist, für AEM Sites-Daten ist jedoch eine aktive Cloud-Konfiguration erforderlich.

1. Gehen Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Wählen Sie das adaptive Formular „Enrollment Application For Health Benefits“ und dann die Option „Analytics-Bericht“.

   ![Analytics-Bericht](assets/analytics_report.jpg)

1. Warten Sie, bis die Seite geladen wurde, und zeigen Sie die Daten des Analytics-Berichts an.

   ![Anzeigen von Analytics-Berichtsdaten](assets/analytics_report_data.jpg)

### Aktivierung der automatisierten Konfiguration von Adobe-Formularen {#automated-forms-enablement}

Um AEM Forms mit dem Adobe Forms-Konvertierungs-Tool zu installieren und zu konfigurieren, müssen Benutzer über Folgendes verfügen.

1. Zugriff auf Adobe I/O.

1. Berechtigung zum Erstellen einer Integration mit dem Adobe Forms-Konvertierungs-Service.

1. Neuestes Service Pack von Adobe AEM 6.5, das als Autor ausgeführt wird.

Bitte gehen Sie die folgenden Punkte durch, bevor Sie weitere Anweisungen lesen:

* [Dienst zur automatischen Formularkonvertierung konfigurieren](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html?lang=de)

#### Erstellen einer IMS-Konfiguration, Teil 1 {#creating-ims-config}

Damit der Service ordnungsgemäß mit dem Konvertierungs-Tool für Formulare kommunizieren kann, müssen die Benutzer den Identity Management-System-Service (IMS) konfigurieren, damit sie sich bei Adobe I/O registrieren können.

1. Navigieren Sie zu https://&lt;aemserver>:&lt;port> und klicken Sie links oben auf „Adobe Experience Manager“ > „Tools“ > „Sicherheit“ > „Adobe IMS-Konfiguration“.

1. Klicken Sie auf „Erstellen“.

1. Führen Sie die Aktionen im folgenden Bild aus.

   ![Konfiguration des technischen IMS-Kontos](assets/aftia-technical-account-configuration.jpg)

1. Stellen Sie sicher, dass Sie das Zertifikat herunterladen.

1. Fahren Sie nicht mit dem Rest der Konfiguration fort, sondern lesen Sie den Abschnitt [Erstellen der Integration in Adobe I/O](#create-integration-adobeio)

>[!NOTE]
Das in diesem Abschnitt erstellte Zertifikat wird verwendet, um den Integrations-Service in Adobe I/O zu erstellen. Sobald Benutzer den Integrations-Service erstellt haben, können Benutzer diese Informationen aus Adobe I/O verwenden, um die Konfiguration abzuschließen.

#### Erstellen der Integration in Adobe I/O {#create-integration-adobeio}

Vergewissern Sie sich, dass Sie die Möglichkeit haben, eine Integration in Ihrer Adobe-Domain zu erstellen. Wenn nicht, wenden Sie sich an Ihren Systemadministrator, damit er dies tun kann.

1. Navigieren Sie zur [Adobe I/O-Konsole](https://console.adobe.io/).

1. Klicken Sie auf Integration erstellen.

1. Wählen Sie „Auf eine API zugreifen“ aus.

1. Vergewissern Sie sich, dass Sie sich in der richtigen Gruppe befinden (Dropdown-Liste oben rechts).

1. Wählen Sie im Bereich „Experience Cloud“ das Forms-Konvertierungs-Tool aus.

1. Klicken Sie auf Weiter.

1. Geben Sie den Namen und die Beschreibung Ihrer Integration ein.

1. Durch Verwendung des öffentlichen Schlüssels aus Abschnitt 2.1 wird dieser in die Integration des Schlüssels eingefügt.

1. Wählen Sie ein Profil für Ihre automatische Formularkonvertierung aus.

   ![Erstellen einer neuen Integration](assets/aftia-create-new-integration.jpg)

#### Erstellen der IMS-Konfiguration, Teil 2 {#create-ims-config-part-next}

Nachdem Sie eine Integration erstellt haben, können Sie die Installation der IMS-Konfiguration abschließen.

1. Klicken Sie in Adobe I/O auf Ihre Integration, um die Verbindungsdetails anzuzeigen.

1. Navigieren Sie in AEM zu Ihrer IMS-Konfiguration („Tools“ > „Sicherheit“ > „IMS“)

1. Klicken Sie im Bildschirm „IMS-Konfiguration“ auf „Weiter“.

1. Geben Sie den Autorisierungs-Server ein (im Screenshot angezeigter Wert).

1. Geben Sie den API-Schlüssel ein.

1. Geben Sie das Client-Geheimnis ein (Sie müssen in der Integration in Adobe I/O auf die Option zum Offenlegen klicken, damit es angezeigt wird).

1. Klicken Sie in Adobe I/O auf die Registerkarte „JWT“, um die JWT-Payload abzurufen und sie in die Payload der IMS-Konfiguration einzufügen.

   ![Payload-IMS-Konfiguration](assets/aftia-payload-ims-config.jpg)

1. Klicken Sie nach der Erstellung auf die IMS-Konfiguration und wählen Sie „Konsistenzprüfung“ aus. Die Benutzer sollten das folgende Ergebnis sehen.

   ![Statusbestätigung](assets/aftia-health-confirmation.jpg)

#### Konfigurieren der Cloud-Konfiguration (We.Gov AFC Production) {#configure-cloud-configuration}

Sobald die IMS-Konfiguration abgeschlossen ist, können wir die Cloud-Konfiguration in AEM überprüfen. Wenn die Konfiguration nicht vorhanden ist, führen Sie die folgenden Schritte aus, um die Cloud-Konfiguration in AEM zu erstellen:

1. Öffnen Sie den Browser und navigieren Sie zur System-URL https://&lt;domain_name>:&lt;system_port>

1. Klicken Sie oben links im Bildschirm auf „Adobe Experience Manager“ > „Tools“ > „Cloud Services“ > „Konfiguration der automatisierten Formularkonvertierung“.

1. Wählen Sie den Konfigurationsordner aus, in dem Sie die Konfiguration ablegen möchten.

1. Klicken Sie auf „Erstellen“.

1. Geben Sie die Informationen im folgenden Screenshot ein.

   ![AFC-Produktion](assets/aftia-afc-production.jpg)

1. Geben Sie der Konfiguration einen Titel und einen Namen.

1. Die Service-URL für das System ist auf https://aemformsconversion.adobe.io/ festgelegt.

1. Vorlagen-URL */conf/we-gov/settings/wcm/templates/we-gov-flamingo-template*.

1. Design-URL: */content/dam/formsanddocuments-themes/adobe-gov-forms-themes/we-gov-theme*

1. Klicken Sie auf Weiter.

1. Für diese Konfiguration haben wir die beiden Kontrollkästchenwerte leer gelassen.

   * Weitere Informationen zu diesen Optionen finden Sie unter [Konfigurieren von Cloud Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html?lang=de#configure-the-cloud-service).

#### Konfigurieren der Cloud-Konfiguration (We.Finance AFC Production) {#configure-cloud-configuration-wefinance}

Sobald die IMS-Konfiguration abgeschlossen ist, können wir mit der Erstellung der Cloud-Konfiguration in AEM fortfahren.

1. Öffnen Sie den Browser und navigieren Sie zur System-URL https://&lt;domain_name>:&lt;system_port>

1. Klicken Sie oben links im Bildschirm auf „Adobe Experience Manager“ > „Tools“ > „Cloud Services“ > „Konfiguration der automatisierten Formularkonvertierung“.

1. Wählen Sie den Konfigurationsordner aus, in dem Sie die Konfiguration ablegen möchten.

1. Klicken Sie auf „Erstellen“.

1. Geben Sie die Informationen im folgenden Screenshot ein.

   ![We.Finance AFC-Produktion](assets/aftia-wefinance-afc-prod.jpg)

1. Geben Sie der Konfiguration einen Titel und einen Namen.

1. Die Service-URL für das System ist auf https://aemformsconversion.adobe.io/ festgelegt.

1. Vorlagen-URL: */conf/we-finance/settings/wcm/templates/we-finance-adaptive-form*

1. Design-URL: */content/dam/formsanddocuments-themes/adobe-finance-forms-themes/we-finance-theme*

1. Klicken Sie auf Weiter.

1. Für diese Konfiguration haben wir die beiden Kontrollkästchenwerte leer gelassen.

   * Weitere Informationen zu diesen Optionen finden Sie unter [Konfigurieren des Cloud-Services](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html?lang=de#configure-the-cloud-service).

#### Testen der Formularkonvertierung (We.Gov-Registrierungsprogramm) {#test-forms-conversion}

Nach dem Einrichten der Konfiguration können Benutzer sie testen, indem sie ein PDF-Dokument hochladen.

1. Navigieren Sie zum AEM-System https://&lt;domain_name>:&lt;system_port>

1. Klicken Sie auf „Formulare“ > „Formulare und Dokumente“ > „AEM Forms We.gov-Formulare“ > „AFC“.

1. Wählen Sie die PDF der We.Gov Enrollment Application aus.

1. Klicken Sie auf **Automatische Konvertierung starten** in der rechten oberen Ecke.

1. Benutzer sollten die Option wie unten dargestellt sehen können.

   ![Konvertiertes adaptives Formular](assets/aftia-converted-adaptive-form.jpg)

1. Nachdem die Schaltfläche ausgewählt wurde, werden den Benutzern die folgenden Optionen angezeigt

   * Stellen Sie sicher, dass die Benutzer die Konfiguration *We.Gov AFC Production* auswählen.

   ![Konvertierungseinstellungen](assets/aftia-conversion-settings.jpg)

   ![Erweiterte Konvertierungseinstellungen](assets/aftia-conversion-settings-2.jpg)

1. Wählen Sie „Konvertierung starten“ aus, sobald Sie alle Optionen konfiguriert haben, die Sie verwenden möchten.

1. Wenn der Konvertierungsprozess beginnt, sollten die Benutzer den folgenden Bildschirm sehen:

   ![Konvertierungseinstellungen](assets/aftia-conversion-in-progress.jpg)

1. Wenn die Konvertierung abgeschlossen ist, sehen die Benutzer den folgenden Bildschirm:

   ![Konvertiertes adaptives Formular](assets/aftia-converted-adaptive-form-2.jpg)

   Klicken Sie auf den Ordner **Ausgabe**, um das generierte adaptive Formular anzuzeigen.

#### Bekannte Probleme und Hinweise {#known-issues-notes}

Zum Service der automatischen Formularkonvertierung gehören bestimmte [Best Practices, bekannte komplexe Muster](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/styles-and-pattern-considerations-and-best-practices.html?lang=de) und [bekannte Probleme](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/known-issues.html?lang=de). Lesen Sie diese zuerst, bevor Sie mit der Verwendung des Services der automatischen Formularkonvertierung von AEM Forms beginnen.

1. Erzeugen Sie das Formular mit aktivierter Option „Adaptive(s) Formular(e) ohne Datenbindung generieren“, wenn Sie das Formular nach der Konvertierung an einen FDM binden möchten.

1. Stellen Sie sicher, dass im Vorlagenordner die Berechtigung „jcr:read“ für alle aktiviert ist. Andernfalls kann der Benutzer des Services die Vorlage nicht aus dem Repository lesen, und die Konvertierung schlägt fehl.

## Anpassung von Demopaketen {#demo-package-customizations}

Dieser Abschnitt enthält Anweisungen zur Anpassung der Demo.

### Anpassung von Vorlagen {#templates-customization}

Bearbeitbare Vorlagen sind am folgenden Ort zu finden:

*https://&lt;aemserver>:&lt;port>/libs/wcm/core/content/sites/templates.html/conf/we-gov*

Zu diesen Vorlagen gehören die Vorlagen für AEM-Sites, adaptive Formulare und interaktive Kommunikation, die mit Komponenten erstellt und zusammengestellt wurden, welche unter folgender Adresse zu finden sind:

*https://&lt;aemserver>:&lt;port>/crx/de/index.jsp#/apps/we-gov/components*

#### Stilsystem {#customizetemplates}

Auf dieser Site finden Sie auch Client-Bibliotheken, von denen eine Bootstrap 4 importiert ([https://getbootstrap.com/](https://getbootstrap.com/)). Diese Client-Bibliothek ist verfügbar unter

*https://&lt;aemserver>:&lt;port>/crx/de/index.jsp#/apps/we-gov/clientlibs/clientlib-base/css/bootstrap*

Die bearbeitbaren Vorlagen, die in diesem Paket enthalten sind, sind auch mit Vorlagen-/Seitenrichtlinien vorkonfiguriert, die die CSS-Klassen von Bootstrap 4 für Paginierung, Stil usw. verwenden. Nicht alle Klassen wurden zu den Vorlagenrichtlinien hinzugefügt, aber jede Klasse, die von Bootstrap 4 unterstützt wird, kann zu den Richtlinien hinzugefügt werden. Eine Liste der verfügbaren Klassen finden Sie auf der Einführungsseite:

[https://getbootstrap.com/docs/4.1/getting-started/introduction/](https://getbootstrap.com/docs/4.1/getting-started/introduction/)

Die in diesem Paket enthaltenen Vorlagen unterstützen auch das Stilsystem:

[Stilsystem](../../sites-authoring/style-system.md)

#### Vorlagen-Logos {#template-logos}

Projekt-DAM-Assets umfassen auch Logos und Bilder zu We.Gov. Diese Assets sind verfügbar unter:

*https://&lt;aemserver>:&lt;port>/assets.html/content/dam/we-gov*

Bei der Bearbeitung der Seiten- und Formularvorlagen können Sie Markenlogos aktualisieren, indem Sie die Komponenten „Navigation“ und „Fußzeile“ bearbeiten. Diese Komponenten bieten ein konfigurierbares Dialogfeld für Marken und Logos, mit dem Logos aktualisiert werden können:

![Vorlagen-Logos](assets/template_logos.jpg)

Weitere Informationen hierzu finden Sie unter „Bearbeiten von Seiteninhalten“:

[Bearbeiten des Seiteninhalts](../../sites-authoring/editing-content.md)

### Anpassung von Sites-Seiten {#sites-pages-customization}

Alle Sites-Seiten sind verfügbar unter: *https://&lt;aemserver>:&lt;port>/sites.html/content/we-gov*

Auf diesen Seiten wird auch das AEM Grid-Paket verwendet, um das Layout einiger Komponenten zu steuern.

#### Stilsystem {#style-system}

Die in diesem Paket enthaltenen Seiten unterstützen auch das Stilsystem:

[Stilsystem](../../sites-authoring/style-system.md)

Weitere Informationen finden Sie unter [Stilsystem für die Vorlagenanpassung](../../forms/using/forms-install-configure-gov-reference-site.md#customizetemplates) für die Dokumentation zu unterstützten Stilen.

### Anpassung adaptiver Formulare {#adaptive-forms-customization}

Alle adaptiven Formulare sind verfügbar unter:

*https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

Diese Formulare können an bestimmte Anwendungsfälle angepasst werden. Beachten Sie, dass bestimmte Felder und die Übermittlungslogik nicht geändert werden sollten, um sicherzustellen, dass das Formular weiterhin ordnungsgemäß funktioniert. Hierzu gehört Folgendes:

**Anmeldeformular für Gesundheitsleistungen:**

* contact_id – Verstecktes Feld, das zum Empfangen der MS Dynamics-Kontakt-ID während der Übermittlung verwendet wird
* Senden - Die Logik der Schaltfläche „Senden“ muss angepasst werden, um Rückrufe zu unterstützen. Die Anpassung ist dokumentiert, aber es war ein umfangreiches Skript erforderlich, um das Formular zu übermitteln und dabei sowohl einen POST- als auch einen GET-Vorgang über das Forms Data Model an MS Dynamics durchzuführen.
* Das Ereignis „Root Panel - Initialize“ wird verwendet, um eine MS Dynamics-Schaltfläche zum AEM-Posteingang hinzuzufügen, und zwar auf die am wenigsten aufdringliche Weise, da alle AEM-Posteingang-Granite-UI-Komponenten nicht veränderbar sind.

#### Adaptives Formular-Styling {#adaptive-form-styling}

Adaptive Formulare können auch mit dem Stil-Editor oder dem Design-Editor formatiert werden:

* [Inline-Stile für Komponenten adaptiver Formulare](inline-style-adaptive-forms.md)
* [Erstellen und Verwenden von Designs](themes.md)

### Anpassung des Workflows {#workflow-customization}

Das adaptive Anmeldungsformular sendet zur Verarbeitung an einen OSGi-Workflow. Diesen Workflow finden Sie unter *https://&lt;aemserver>:&lt;port>/conf/we-gov/settings/models/we-gov-process.html*.

Aufgrund bestimmter Einschränkungen enthält dieser Workflow mehrere Skripte und benutzerdefinierte OSGi-Workflow-Prozessschritte. Diese Workflow-Schritte wurden als generische Schritte und nicht mit Konfigurationsdialogen erstellt. Derzeit beruht die Konfiguration der Workflow-Schritte auf Prozessargumenten.

Der gesamte Java-Code der Workflow-Schritte ist im Paket **we-gov-forms.core-&lt;version>.jar** enthalten.

## Überlegungen zur Demo und bekannte Probleme {#demo-considerations-and-known-issues}

Dieser Abschnitt enthält Informationen zu Demo-Funktionen und Design-Entscheidungen, die während des Demonstrationsprozesses möglicherweise besondere Überlegungen erfordern.

### Überlegungen zur Demo {#demo-considerations}

* Stellen Sie gemäß AGRS-159 sicher, dass der Name (Vor-, Mittel- und Nachname) des Kontakts, der im adaptiven Anmeldungsformular verwendet wird, einzigartig ist.
* Das adaptive Anmeldungsformular sendet die Adobe Sign-E-Mail an die E-Mail, die im E-Mail-Feld des Formulars angegeben ist. Diese E-Mail-Adresse darf nicht dieselbe E-Mail-Adresse sein wie die E-Mail, die zum Konfigurieren der Adobe Sign-Cloud-Konfiguration verwendet wurde.

### Bekannte Probleme {#known-issues}

* (AGRS-120) Die Site-Navigationskomponente unterstützt derzeit keine verschachtelten untergeordneten Seiten, die mehr als zwei Ebenen tief sind.
* (AGRS-159) Der aktuelle MS Dynamics FDM muss zwei Vorgänge ausführen, um zunächst die Daten des adaptiven Anmeldungsformulars an Dynamics zu POSTEN und dann den Anwender-Datensatz abzurufen, um die Kontakt-ID abzurufen. Im aktuellen Zustand schlägt das Abrufen der Kontakt-ID fehl, wenn in Dynamics mehr als zwei Anwender mit demselben Namen vorhanden sind, wodurch die Übermittlung des adaptiven Anmeldungsformulars nicht zugelassen wird.

## Konfigurieren von Zugänglichkeitstests {#configure-accessibility-testing}

### Aktivieren des Chrome-Add-ons für Zugänglichkeitstests {#enable-chrome-add-on}

Um Zugänglichkeitstests durchzuführen, müssen Sie zunächst das Chrome-Plug-in installieren, das Sie [hier](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?hl=de) finden.

Laden Sie nach der Installation die Seite, die Sie im Chrome-Browser testen möchten (Hinweis: Wenn mehrere Tabs geöffnet sind, kann sich dies auf Ihr Scoring auswirken. Es ist empfehlenswert, nur eine Registerkarte zu öffnen.) Sobald die Seite geladen ist, klicken Sie mit der 
**rechten Maustaste** auf die Seite und wählen Sie die Registerkarte **Prüfungen**. Dort können Entwickler die Art der Prüfung auswählen, die vom Zugänglichkeits-Plug-in durchgeführt werden soll. Nachdem alle gewünschten Optionen ausgewählt wurden, kann der Anwender die Schaltfläche „Bericht erstellen“ auswählen. Hierdurch wird ein PDF-Dokument generiert, das die allgemeine Zugänglichkeitsbewertung zeigt und verwendet werden kann, um die Zugänglichkeitsbewertung insgesamt zu verbessern.

Sobald der Bericht ausgeführt wurde, können Anwender Folgendes erwarten:

![Zugänglichkeitsbericht](assets/aftia-accessibility.jpg)

Bei der Zahl, die vor den Anwendern angezeigt wird, handelt es sich um die allgemeine Zugänglichkeitsbewertung, die sie erhalten haben. Im Anschluss an die Bewertung wird auch beschrieben, wie diese berechnet wurde.

Wenn Anwender diese exportieren möchten, können sie auf die drei Schaltflächen auf der rechten Seite des Bildschirms klicken und aus den weiteren Optionen wählen, die das Plug-in bietet.

![Zugänglichkeitsbericht](assets/aftia-accessibility-report.jpg)

### Ultramarine-Design {#ultramarine-theme}

Das öffentlich verfügbare Ultramarine-Design, das von Adobe gepflegt wird, ist in die
`we-gov-forms.pkg.all-<version>.zip` installierbare ZIP-Datei integriert. Sobald dieses Paket mit CRX installiert ist.

Package Manager, Anwender können auf das Ultramarine-Design in AEM Forms zugreifen, indem sie zu **Forms** > **Designs** > **Referenz-Designs** > **Ultramarine-zugänglich** navigieren.

![Ultramarine-Design](assets/aftia-ultramarine-theme.jpg)

## Konfigurationsoptionen {#configuration-options}

Anwender haben die Möglichkeit, verschiedene Workflow-Service-Optionen zu konfigurieren, darunter die folgenden:

1. Microsoft Dynamics-Eintrag
1. Adobe Sign
1. AEM Custom Communication Management
1. Adobe Analytics

Um sie so zu konfigurieren, dass sie im Workflow aktiviert werden, müssen Benutzer die folgenden Aufgaben ausführen.

1. Gehen Sie zu https://&#39;[server]:[port]&#39;/system/console/configMgr.

1. Suchen Sie die *WeGov-Konfigurationen*.

1. Öffnen Sie die Service-Definition und aktivieren Sie den Aufruf der ausgewählten Services innerhalb des Workflows.

   >[!NOTE]
   Auch wenn ein Benutzer den Service auf der Seite „Configuration Manager“ aktiviert, muss er dennoch eine Service-Konfiguration einrichten, um mit den angefragten externen Services kommunizieren zu können.

   ![WeGov-Formular-Paket](assets/aftia-configuration-options.jpg)

1. Klicken Sie abschließend auf die Schaltfläche „Speichern“, um die Einstellungen zu speichern.

## Nächste Schritte {#next-steps}

Jetzt können Sie die WeGov-Referenz-Website erkunden. Weitere Informationen zum Workflow und den Schritten der WeGov-Referenz-Website finden Sie unter [Schrittweise Anleitung zur WeGov-Referenz-Website](../../forms/using/forms-gov-reference-site-user-demo.md).
