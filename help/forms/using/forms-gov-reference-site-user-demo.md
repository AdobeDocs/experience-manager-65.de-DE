---
title: Schrittweise Anleitung zur We.Gov-Referenzwebsite
seo-title: Schrittweise Anleitung zur We.Gov-Referenzwebsite
description: Verwenden Sie fiktive Benutzer und Gruppen, um AEM Forms-Aufgaben mithilfe des Demopakets We.Gov durchzuführen.
seo-description: Verwenden Sie fiktive Benutzer und Gruppen, um AEM Forms-Aufgaben mithilfe des Demopakets We.Gov durchzuführen.
uuid: 797e301a-36ed-4bae-9ea8-ee77285c786d
contentOwner: anujkapo
discoiquuid: ddb3778b-be06-4cde-bc6e-0994efa42b18
docset: aem65
translation-type: tm+mt
source-git-commit: d1da42d7274e9a4257b9e8effae2b754e0104aa4
workflow-type: tm+mt
source-wordcount: '2536'
ht-degree: 2%

---


# Schrittweise Anleitung zur We.Gov-Referenz-Site {#we-gov-reference-site-walkthrough}

## Voraussetzungen {#pre-requisites}

Set up the reference site as described in [Set up and configure We.Gov reference site](../../forms/using/forms-install-configure-gov-reference-site.md).

## Benutzergeschichte {#user-story}

* AEM Forms

   * Automatisierte Formularkonvertierung
   * Authoring – 
   * Formulardatenmodelle/Datenquellen

* AEM Forms

   * Datenerfassung
   * (Optional) Datenintegration (MS Dynamics)
   * (Optional) Adobe Sign

* Workflow
* E-Mail-Benachrichtigungen
* (Optional) Kundenkommunikation

   * Druckkanal
   * Webkanal

* Adobe Analytics
* Data Source Integrations

### Fictitious users and groups {#fictitious-users-and-groups}

The We.Gov demo package comes with the following built-in fictitious users:

* **Aya Tan**: Bürger, die für eine Dienstleistung einer Regierungsstelle infrage kommen

![Fictitious user](/help/forms/using/assets/aya_tan_new.png)

* **George Lang**: We.Gov agency Business Analyst

![Fictitious user](/help/forms/using/assets/george_lang.png)

* **Camila Santos**: We.Gov Agency CX Lead

![Fictitious user](/help/forms/using/assets/camila_santos.png)

The following groups are also included:

* **We.Gov Forms Users**

   * George Lang (member)
   * Camila Santos (member)

* **We.Gov Users**

   * George Lang (member)
   * Camila Santos (member)
   * Aya Tan (member)

### Übersicht über die Demobegriffe - Legende {#demo-overview-terms-legend}

1. **Identität annehmen**: Definierte Benutzer und Gruppen in AEM Demo.
1. **Schaltfläche**: Farbiges Rechteck oder kreisförmiger Pfeil zum Navigieren.
1. **Klicken Sie auf**: Zum Ausführen einer Aktion im Benutzerverlauf.
1. **Links**: Befindet sich oben im Hauptmenü auf der Website We.Gov.
1. **Benutzeranweisungen**: Eine Reihe numerischer Schritte, die beim Navigieren durch die Benutzergeschichte befolgt werden müssen.
1. **Forms Portal**: *https://&lt;aemserver>:&lt;port>/content/we-gov/formsportal.html*
1. **Mobil-Ansicht**: Wir.Gov-Benutzer, der eine mobile Ansicht mit einem Browser in der neuen Größe repliziert.
1. **Desktop-Ansicht**: Wir.gov user to Ansicht demo on a Laptop oder desktop.
1. **Formular** vor dem Bildschirm: Formular auf der Startseite der Website We.Gov.
1. **Adaptives Formular**: Antragsformular für die Anmeldung bei We.gov.

   *https://&lt;aemserver>:&lt;port>/content/forms/af/adobe-gov-forms/enrollment-application-for-health-benefits.html*

1. **Website** der Adobe Wir.Gov: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. **Adobe-Posteingang**: Die obere Menüleiste [Glockensymbol](assets/bell.svg) im AEM Backend.

   *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. **E-Mail-Client**: Bevorzugte Methode zur Ansicht Ihrer E-Mails (Google Mail, Outlook)
1. **CTA**: Aktionsaufruf
1. **Navigieren**: So suchen Sie einen bestimmten Referenzpunkt auf der Browserseite.
1. **AFC**: Automatisierte Forms-Konvertierung

## Automatisierte Forms-Konvertierung (Camila) {#automated-forms-conversion}

**Dieser Abschnitt**: Camila the CX Lead verfügt über ein PDF-basiertes Formular, das als Teil eines papierbasierten Prozesses verwendet wurde. Im Rahmen der Modernisierung möchte sie dieses PDF-Formular verwenden, um automatisch ein neues adaptives Forms zu erstellen.

### Automatisierte Forms-Umrechnung - We.Gov (Camila) {#automated-forms-conversion-wegov}

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. Anmelden mit:
   * **Benutzer**: camila.santos
   * **Kennwort:** password
1. Wählen Sie auf der Hauptseite Forms > Forms &amp; Dokumente > AEM Forms We.gov Forms > AFC.
1. Camila lädt die PDF-Datei nach AEM Forms hoch.

   ![Formular hochladen](assets/aftia-upload-form.jpg)

1. Camilla wählt dann das PDF-Formular aus und klickt auf **Beginn Automatisierte Konvertierung** , um den Konvertierungsprozess Beginn. You may need to click **Overwrite conversion** if you have converted the form.

   >[!NOTE]
   >
   >Beachten Sie, dass die Einstellungen in AFC für den Endbenutzer vorkonfiguriert sind, was bedeutet, dass sie nicht geändert werden sollten.

   * **Optional**: If you wish to use the Accessible Ultramarine theme, simply click on the Specify an adaptive form theme and select the Accessible-Ultramarine theme that appears in the list of options.

   ![Start conversion](assets/aftia-start-conversion.jpg)

   ![Ultramarine-Design](assets/aftia-upload-conversion-settings.jpg)

   The percentage complete status displays during conversion. Once the status displays **Converted**, click the **output** folder, select the adaptive form and click **Edit** to open the converted form.

1. Camilla then reviews the form and makes certain that all fields are present

   ![Review conversion](assets/aftia-review-conversion.jpg)

1. Camilla then starts to edit the form. She selects Root Panel > Edit (the wrench) > selects Tabs on Top from the Panel Layout dropdown menu > selects the Check box.

   ![Review properties](assets/aftia-review-properties.jpg)

1. Camilla then adds all the necessary CSS and field alterations to produce the final product.

   ![Add CSS](assets/aftia-add-css.jpg)

### Form Data Model &amp; Data Sources (Camila) {#data-sources}

**Dieser Abschnitt**: Nachdem das Dokument konvertiert und ein adaptives Formular erstellt wurde, muss Camila das adaptive Formular mit einer Datenquelle verbinden.

1. Camila opens the Properties on the form that was converted in [Automated Forms Conversion - We.Gov](#automated-forms-conversion-wegov).

1. Camila then selects Form Model > Selects Form Data Model from Select From dropdown > Selects We.gov Enrollment FDM from the list of option.

1. Klicken Sie auf die Schaltfläche Speichern und Schließen.

   ![FDM-Auswahl](assets/aftia-select-fdm.jpg)

1. Camila klickt auf den **Ordner &quot;output** &quot;, wählt das adaptive Formular aus und klickt auf **Bearbeiten** , um das ausgefüllte We.Gov-Formular zu öffnen.
1. Camila wählt ein Feld für ein adaptives Formular aus und klickt auf das Symbol ![Konfigurieren](assets/configure-icon.svg). Sie erstellt mithilfe des Felds &quot; **Bindungsverweis** &quot;eine Bindung mit den Formulardatenmodellentitäten. Sie wiederholt diesen Schritt für alle Felder im adaptiven Formular.

### Barrierefreiheitstest für Formulare (Camila) {#form-accessibility-testing}

Camila überprüft auch, ob die erstellten Inhalte korrekt und vollständig zugänglich gemäß den Unternehmensstandards erstellt wurden.

1. Camila klickt auf den **Ausgabeordner** , wählt das adaptive Formular aus und klickt auf **Vorschau** , um das ausgefüllte We.Gov-Formular zu öffnen.

1. Öffnet die Registerkarte &quot;Prüfung&quot;im Chrome Developer Tool.

1. Führt eine Barrierefreiheitsprüfung durch, um das adaptive Formular zu validieren.

   ![Barrierefreiheitsprüfung](assets/aftia-accessibility.jpg)

## Demo zur mobilen Ansicht für adaptive Formulare (Aya) {#mobile-view-demo}

**Dieser Abschnitt muss vor der Demonstration durchgeführt werden.**

**Benutzeranweisungen:**

1. Navigate to: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Login with:

   1. **User**: aya.tan
   1. **Kennwort:** password

1. Re-size the browser window or use the browser’s emulator to replicate a mobile device size.

### We.Gov Website (Aya) {#aya-user-story-we-gov-website}

![Fictitious user](/help/forms/using/assets/aya_tan_new-1.png)

**This section**: Aya is a citizen. She hears from a friend that she may be eligible to receive a Service from a government agency. Aya navigates to the We.Gov website from her mobile phone to learn more about services she is eligible for.

### We.Gov Pre-Screener (Aya) {#aya-user-story-we-gov-pre-screener}

Aya answers a few questions to confirm her eligibility by filling out a short adaptive form on her mobile phone.

**User Instructions:**

1. Make a selection in each dropdown field.

   >[!NOTE]
   >
   >If the user earns more than $200,000/yr, they aren’t eligible.

1. Click the “**Am I Eligible?**” button.
1. Klicken Sie auf die Schaltfläche &quot;Jetzt **anwenden**&quot;, um fortzufahren.

   ![Jetzt anwenden](/help/forms/using/assets/apply_now_link.png)

### we.gov Adaptive Form (AY) {#aya-user-story-we-gov-adaptive-form}

Aya stellt fest, dass sie berechtigt ist, und beginnt, ihren Antrag auszufüllen, um einen Service auf ihrem Mobilgerät anzufordern.

Aya needs to review some documents at home before she can complete the service request application. She saves and exits the application from her mobile device.

**User Instructions:**

1. Fill out the Basic information fields, the following are required fields and dropdowns:

   1. Grundlegende Informationen

      1. Vorname
      1. Nachname
      1. DOB
      1. E-Mail

1. Use the following **dynamic logic** to demonstrate dynamic feature using the **Family Status** dropdown:

   1. **Single**: Show next of kin panel
   1. **Married**: Show marital dependant panel
   1. **Divorced**: Show next of kin panel
   1. **Widowed**: Show next of kin panel
   1. **Do you have Children?**: (Yes/No) radio button to show child dependant panel.

      1. (Add/Remove) button to add/remove multiple child dependant panels.

1. Click the right arrow in the gray menu bar.
1. Click the Save button at the bottom.

   ![Adaptive Form details](/help/forms/using/assets/adaptive_form.png)

## Desktop demo {#desktop-demo}

**Dieser Abschnitt:** Zurück zu Hause hat Aya die benötigten Informationen gefunden und setzt die Anwendung von ihrem Desktop fort. Aya navigates to the online forms portal to resume her application. Durch eine einfache Anpassung können Agenturen auch automatisch einen Link erstellen und per E-Mail versenden, um die Anwendung wiederaufzunehmen.

### Continued Adaptive Form (Aya) {#aya-user-story-continued-adaptive-form}

**User Instructions:**

1. Navigate to *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. From the navigation bar, select click on “**Online Services**”.
1. From the “Draft Forms” panel, select the existing “Enrollment Application For Health Benefits&quot;.

   ![Anmeldung für Gesundheitsleistungen](/help/forms/using/assets/enrollment_application.png)

   The look and feel are the same, and she does not need to re-enter any data.

   **Benutzeranweisungen:**

1. Click right Circle CTA to move to the next section.

   ![RIght circle CTA](/help/forms/using/assets/right_circle_cta_new.png)

   The form is populated up to the point of Aya’s last entry. Aya has entered all her information and is ready to submit.

   ![Submit the adaptive form](/help/forms/using/assets/submit_adaptive_form.png)

   >[!NOTE]
   >
   >When Aya fills out the phone number field she must fill it as a continuous 11 digit number with no dashes, spaces or hyphens.

   After submitting Aya receives a Thank You page. Optionally she will also receive an email that she can open to sign the document of record electronically with Adobe Sign.

### Optional: Adobe Sign (Aya) {#adobe-sign}

**User Instructions:**

1. Navigate to your Email Client and find the Adobe Sign email.
1. Click on the link to Adobe Sign.

   ![Adobe sign link](/help/forms/using/assets/adobe_sign_link.png)

**User Instructions:**

1. Check the “**I agree**” box.
1. Click “**Accept**”.
1. Scroll to the bottom of the reviewed document.
1. Click on the highlighted yellow tab to sign the document.

   ![Sign the document](/help/forms/using/assets/sign_document_new.png) ![Sign the test document](/help/forms/using/assets/sign_test_document.png)

## Government agent (George) {#government-agent-george}

![Government Agent George](/help/forms/using/assets/george_lang-1.png)

**This section:** George is a business analyst at the government agency Aya is a requesting a service from. George has a single dashboard where he can see all service request applications that have been assigned to him for review.

### AEM Inbox (George) {#george-user-story-aem-inbox}

**User Instructions:**

1. Navigate to *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Click on the user icon (top right-hand corner) and use the “**Sign Out**”, or the “**Impersonate as**” menu option if you are currently logged in with an administrative user.

   1. Login with:

      1. **User:** george.lang
      1. **Kennwort:** password
   1. Or Impersonate:

      1. Geben Sie &quot;**George**&quot;in das Feld &quot;**Impersonate as**&quot;ein.

      1. Click okay to impersonate.


1. From the top right corner, click the Notification (bell) Icon.
1. Click “**View All**” to navigate to the Inbox.
1. Öffnen Sie im Posteingang die neueste Aufgabe &quot;**Health Benefits Application Review**&quot;.

   ![Health Benefits Application Review](/help/forms/using/assets/health_benefits.png)

### Optional: AEM Inbox &amp; MS Dynamics (George) {#george-user-story-aem-inbox-and-ms-dynamics}

Thanks to data integrations and automated workflows, Aya’s application appears, along with a CRM record that has automatically been generated when the data was submitted.

**User Instructions:**

1. Open and inspect the read-only adaptive form.
1. Click on the “**Open MS Dynamics**” button to open the MS Dynamics record in a new window.
1. In the CRM you can see all information can be updated

   1. Optionally, add some review notes directly in Dynamics.

1. Close and return to AEM Inbox.

   ![MS Dynamics record](/help/forms/using/assets/ms_dynamics.png)

### Back to AEM Inbox (George) {#george-user-story-back-to-aem-inbox}

George approves Aya’s application, and thanks to an existing automated workflow a confirmation email is also sent to Aya.

**User Instructions:**

1. Navigate to the top left corner and click “**Approve**” to approve the application.
1. In the modal, you can leave a message for the CX lead.
1. Klicken Sie auf Fertig.
1. (Citizen role) Open up your email client to view the email sent to Aya.

   ![View the email sent to Aya](/help/forms/using/assets/email_client.png)

## CX-Blei (Camila) {#cx-lead-camila}

![Camila (CX lead)](/help/forms/using/assets/camila_santos-1.png)

**This section:** Camila the CX Lead sets up a welcome phone call with Aya to explain how to make use of the government services she has been approved for.

### (Optional) AEM Inbox &amp; MS Dynamics {#camila-user-story-aem-inbox-ms-dynamics}

**User Instructions:**

1. Navigate to *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Click on the user icon (top right-hand corner) and use the “**Sign Out**”, or the “**Impersonate as**” menu option if you are currently logged in with an administrative user.

   1. Login with:

      1. **User**: camila.santos
      1. **Kennwort:** password
   1. Or Impersonate:

      1. Type “**Camila**” in the “**Impersonate as**” field.

      1. Click okay to impersonate.


1. From the top right corner, click the Notification (bell) icon.
1. Click “**View All**” to navigate to the Inbox.
1. From the Inbox, open the latest “**New Contact Approval**” task.

![New Contact Approval](/help/forms/using/assets/new_contact_approval.png)

**(Optional) User Instructions:**

1. Open and inspect the read-only adaptive form.
1. Click on the “**Open MS Dynamics**” button to open the MS Dynamics record in a new window.
1. In the CRM you can see all information can be updated

   1. Optionally, add a new call activity directly in Dynamics.
   1. Open the “**Activities**” section.
   1. Click on the “**New Phone Call**” option.
   1. Add phone call details.
   1. Save and close the window.

1. Back in AEM, navigate to the top left corner and click “**Submit**” to submit the application.
1. In the modal, you can leave a message.
1. Klicken Sie auf Fertig.

   ![Activities tab](/help/forms/using/assets/activities_tab.png) ![Confirm New Contact](/help/forms/using/assets/confirm_new_contact.png)

## (Optional) Welcome Kit Citizen (Aya) {#welcome-kit-citizen-aya}

**This section:** Aya receives an email contains a link to an interactive communication which summarizes her benefits and also includes form fields to fill. With PDF benefits statement attached and link to interactive communication letter in the mail (with the same theme/branding as the interactive communication).

### E-Mail-Client-Benachrichtigung (Aya) {#aya-user-story-email-client}

**Benutzeranweisungen:**

1. Suchen Sie die Begrüßungs-Kit-E-Mail und öffnen Sie sie.
1. Blättern Sie zum PDF-Anhang unten auf der Seite.
1. Klicken Sie auf , um die PDF-Anlage zu öffnen.
1. Blättern Sie in Ihrem E-Mail-Client nach oben und klicken Sie auf &quot;**Ansicht Begrüßungs-Kit online**&quot;.

   1. Dadurch wird die Web-Kanal-Version desselben Dokuments geöffnet.

1. Eine kurze Referenz zu PDF direkt:

   *https://&lt;aemserver>:&lt;port>/aem/formdetails.html/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook*

1. Für einen kurzen Hinweis auf IC direkt:

   *https://&lt;aemserver>:&lt;port>/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook/jcr:content?Kanal=web&amp;mode=Vorschau&amp;wcmmode=disabled*

   ![Willkommen-Vorteile-Handbuch](/help/forms/using/assets/welcome_benefits_handbook.png) ![Interaktiver Kommunikationslink](/help/forms/using/assets/interactive_communication.png)

## Erneuerbare Erinnerung Bürger (Aya) {#renewal-reminder-citizen-aya}

**Dieser Abschnitt:** Camila plant auch eine Erinnerung an die Kommunikation ein Jahr später. (Workflow-Schritt, der automatisiert/ausgeführt und E-Mail versendet).

### E-Mail-Client-Benachrichtigung (Aya) {#aya-user-story-email-client-updated}

**Benutzeranweisungen:**

1. Navigieren Sie zu Ihrem E-Mail-Client.
1. Suchen Sie die E-Mail zur Erinnerung an die Verlängerung und öffnen Sie sie.
1. Klicken Sie auf die Schaltfläche &quot;Neue Anwendung **senden**&quot;, um das adaptive Formular zu öffnen.

   1. Dieser Abschnitt wird absichtlich leer gelassen, um die Vorfüllung von Daten in Phase 2 zu unterstützen.

   ![E-Mail zur Erinnerung](/help/forms/using/assets/renewal_reminder_email.png)

## (Optional) Formulardatenmodell (Camila) {#form-data-model}

**Dieser Abschnitt**: Camila navigiert zu AEM Forms Data Integrations, wo sie einen schnellen Test durchführen kann, um zu sehen, dass die über die Integration des Formulardatenmodells an die externe Datenquelle gesendeten Informationen tatsächlich vorhanden sind.

### Formulardatenmodell (Camila) {#form-data-model-camila}

**Dieser Abschnitt**: Camila navigiert zur Seite &quot;Datenquellen&quot;, um die Daten zu überprüfen, die der Server in der Derby-Datenbank repliziert hat.

1. Sobald die Benutzererfahrung abgeschlossen ist und die Benutzereingabe abgeschlossen ist, navigiert Camila zur Registerkarte &quot;Datenquellen&quot;in AEM Forms (**Forms** > **Datenintegrationen**).

1. Camila wählt dann AEM Forms **We.gov FDM** aus und bearbeitet dann den **We.gov-Registrierungs-FDM**.

1. Camila wählt dann den zu testenden **Kontakt** > **Lesedienst** aus.

   ![Kontaktlesehilfen-Dienst](assets/aftia-contact-read-service.jpg)

1. Camila stellt dann dem Testdienst eine Kontakt-ID zur Verfügung und klickt dann auf die Schaltfläche Test. Beispiel: 1 oder 2, wenn Sie das Formular gesendet haben. If you have not submitted the form, no data is returned.

   ![Contact read service](assets/aftia-test-service.jpg)

1. Camila can then validate that the data has successfully been inserted into the datasource.

   * The data within the Derby DS resembles the following format:

   ```xml
      [
         {
         "ADDRESS_COUNTRY": "USA",
         "LAST_NAME": "Tan",
         "ADDRESS_CITY": "New York",
         "FIRST_NAME": "Aya",
         "ADDRESS_STATE": "AL",
         "ADDRESS_LINE1": "123 Street crescent",
         "GENDER_CODE": "2",
         "ADDRESS_LINE2": "123 Street crescent",
         "ADDRESS_POSTAL_CODE": "90210",
         "BIRTH_DATE": "1991-12-12",
         "CONTACT_ID": 1,
         "MIDDLE_NAME": "M",
         "HAS_CHILDREN_CODE": "0"
         }
   ]
   ```

## (Optional) Analytics (Camila) {#analytics-cx-lead-camila}

**This section:** Camila navigates to a dashboard where she can see across the agency KPI’s such as % of citizens who start filling a service request form and abandon, the average length of time from request submission to approval/denial response, and engagement statistics for the benefits handbooks she has sent to citizens.

### Adobe Analytics Sites Reporting (Camila) {#camila-reviews-sites-reporting-we-gov-adobe-analytics}

1. Navigate to *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Select the “**AEM Forms We.Gov Site**” to view the site pages.
1. Select one of the site page (e.g. Home), and choose “**Analytics &amp; Recommendations**”.

   ![Analytics and Recommendation](/help/forms/using/assets/analytics_recommendation.jpg)

1. On this page, you will see fetched information from Adobe Analytics which pertains to the AEM Sites page (NOTE: by design this information is periodically refreshed from Adobe Analytics and is not displayed in real-time).

   ![Adobe Analytics key metrics](/help/forms/using/assets/analytics_key_metrics.jpg)

1. Back on the page view page (accessed in step 3.), you can also view the page view information by changing the display setting to view items in the “**List View**”.
1. Locate the “**View**” dropdown menu and select “**List View**”.

   ![Ansicht der Liste im Dropdown-Menü &quot;Ansicht&quot;](/help/forms/using/assets/list_view_view_dropdown.jpg)

1. Wählen Sie im gleichen Menü die Option &quot;**Ansicht einstellen**&quot;und wählen Sie die anzuzeigenden Spalten im Abschnitt &quot;**Analytics**&quot;aus.

   ![Spaltenanzeige konfigurieren](/help/forms/using/assets/view_setting_analytics.jpg)

1. Klicken Sie auf &quot;**Aktualisieren**&quot;, um die neuen Spalten verfügbar zu machen.

   ![Neue Spalten verfügbar machen](/help/forms/using/assets/new_columns_available.jpg)

### Adobe Analytics Forms Berichte (Camila) {#camila-reviews-forms-reporting-we-gov-adobe-analytics}

1. Navigieren Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Wählen Sie das adaptive Formular &quot;**Registrierungsantrag für Gesundheitsvorteile**&quot;und wählen Sie die Option &quot;**Analysebericht**&quot;aus.

   ![Anmeldung für Gesundheitsleistungen](/help/forms/using/assets/analytics_report_benefits.jpg)

1. Warten Sie, bis die Seite geladen wurde, und Ansicht der Analytics-Berichtsdaten.

   ![Analytics-Berichtsdaten](/help/forms/using/assets/analytics_report_data_updated.jpg)

