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
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Schrittweise Anleitung zur We.Gov-Referenz-Site{#we-gov-reference-site-walkthrough}

## Voraussetzungen {#pre-requisites}

Set up the reference site as described in [Set up and configure We.Gov reference site](../../forms/using/forms-install-configure-gov-reference-site.md).

## Benutzergeschichte {#user-story}

* AEM Forms

   * Datenerfassung
   * Datenintegration (MS Dynamics)
   * Adobe Sign

* Workflow
* Kundenkommunikation

   * Druckkanal
   * Webkanal

* Adobe Analytics

### Fictitious users and groups {#fictitious-users-and-groups}

Das Demo-Paket &quot;We.Gov&quot;enthält die folgenden integrierten fiktiven Benutzer:

* **Aya Tan**: Bürger, die für eine Dienstleistung einer Regierungsstelle infrage kommen

![Schlaue Benutzer](/help/forms/using/assets/aya_tan_new.png)

* **George Lang**: We.Gov agency Business Analyst

![Schlaue Benutzer](/help/forms/using/assets/george_lang.png)

* **Camila Santos**: We.Gov Agency CX Lead

![Schlaue Benutzer](/help/forms/using/assets/camila_santos.png)

Die folgenden Gruppen sind ebenfalls enthalten:

* **We.Gov Forms-Benutzer**

   * George Lang (Mitglied)
   * Camila Santos (Mitglied)

* **We.Gov-Benutzer**

   * George Lang (Mitglied)
   * Camila Santos (Mitglied)
   * Aya Tan (Mitglied)

### Übersicht über die Demobegriffe - Legende {#demo-overview-terms-legend}

1. **Identität annehmen**: Definierte Benutzer und Gruppen in AEM-Demo.
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

1. **Adobe Web.Gov-Site**: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. **Adobe Inbox**: Befindet sich in der oberen Menüleiste [Glockensymbol](assets/bell.svg) im AEM-Backend.

   *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. **E-Mail-Client**: Bevorzugte Methode zur Ansicht Ihrer E-Mails (Google Mail, Outlook)
1. **CTA**: Aktionsaufruf
1. **Navigieren**: So suchen Sie einen bestimmten Referenzpunkt auf der Browserseite.

## Demo zur mobilen Ansicht {#mobile-view-demo}

**Dieser Abschnitt muss vor der Demonstration durchgeführt werden.**

**Benutzeranweisungen:**

1. Navigieren Sie zu: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Anmelden mit:

   1. **Benutzer**: aya.tan
   1. **Kennwort:** password

1. Ändern Sie die Größe des Browser-Fensters oder verwenden Sie den Emulator des Browsers, um die Größe eines Mobilgeräts zu replizieren.

### Aya User Story (Website &quot;We.Gov&quot;) {#aya-user-story-we-gov-website}

![Schlaue Benutzer](/help/forms/using/assets/aya_tan_new-1.png)

**Dieser Abschnitt**: Aya ist ein Bürger. Sie hört von einer Freundin, dass sie möglicherweise berechtigt ist, eine Dienstleistung von einer Regierungsbehörde zu erhalten. Aya navigiert von ihrem Handy zur Website We.Gov, um mehr über Dienste zu erfahren, für die sie berechtigt ist.

### Aya User Story (We.Gov-Vorbildner) {#aya-user-story-we-gov-pre-screener}

Aya beantwortet einige Fragen, um ihre Berechtigung zu bestätigen, indem sie ein kurzes adaptives Formular auf ihrem Handy ausfüllt.

**Benutzeranweisungen:**

1. Wählen Sie in jedem Dropdown-Feld eine Auswahl aus.

   >[!NOTE]
   >
   >Wenn der Benutzer mehr als 200.000 USD pro Jahr verdient, sind die Benutzer nicht berechtigt.

1. Klicken Sie auf &quot;**Bin ich berechtigt?**” button.
1. Klicken Sie auf die Schaltfläche &quot;Jetzt **anwenden**&quot;, um fortzufahren.

   ![Jetzt anwenden](/help/forms/using/assets/apply_now_link.png)

### Aya-Benutzergeschichte (adaptives Web.Gov-Formular) {#aya-user-story-we-gov-adaptive-form}

Aya stellt fest, dass sie berechtigt ist, und beginnt, ihren Antrag auszufüllen, um einen Service auf ihrem Mobilgerät anzufordern.

Aya muss einige Dokumente zu Hause überprüfen, bevor sie die Serviceanfrage abschließen kann. Sie speichert und beendet den Antrag.

**Benutzeranweisungen:**

1. Füllen Sie die Felder Grundlegende Informationen aus, die folgenden Felder sind Pflichtfelder und Dropdown-Listen:

   1. Grundlegende Informationen

      1. Vorname
      1. Weitere Vornamen
      1. Nachname
      1. Bevorzugter Name
      1. DOB
      1. Geschlecht
   1. Kontaktangaben

      1. Straße &amp; Hausnr. 
      1. Ort
      1. Telefonnummer
      1. Postleitzahl
      1. E-Mail
      1. Bundesland/Kanton
   1. Kampfstatus

      1. Familienstand



1. Verwenden Sie die folgende **dynamische Logik** , um dynamische Funktionen mithilfe der Dropdownliste **Familienstand** zu demonstrieren:

   1. **Einfach**: Nächstes Bedienfeld für Skins anzeigen
   1. **Verheiratet**: Bereich &quot;eheliche abhängigen Bereich&quot;anzeigen
   1. **Scheidung**: Nächstes Bedienfeld für Skins anzeigen
   1. **Absatzkontrolle**: Nächstes Bedienfeld für Skins anzeigen
   1. **Haben Sie Kinder?**: (Ja/Nein), um untergeordnete Bedienfelder anzuzeigen.

      1. (Hinzufügen/Entfernen), um mehrere untergeordnete Bereiche hinzuzufügen/zu entfernen.

1. Klicken Sie in der grauen Menüleiste auf den Pfeil nach rechts.
1. Klicken Sie unten auf die Schaltfläche Speichern.

   ![Details zu adaptiven Formularen](/help/forms/using/assets/adaptive_form.png)

## Desktop-Demo {#desktop-demo}

**Dieser Abschnitt:** Zurück zu Hause hat Aya die benötigten Informationen gefunden und setzt die Anwendung von ihrem Desktop fort. Aya navigiert zum Online-Formularportal, um ihre Anwendung wiederaufzunehmen. Durch eine einfache Anpassung können Agenturen auch automatisch einen Link erstellen und per E-Mail versenden, um die Anwendung wiederaufzunehmen.

### Aya-Benutzergeschichte (fortgesetztes adaptives Formular) {#aya-user-story-continued-adaptive-form}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Klicken Sie in der Navigationsleiste auf &quot;**Online-Dienste**&quot;.
1. Wählen Sie im Bedienfeld &quot;Entwürfe von Formularen&quot;die vorhandene Option &quot;Anmeldung für Gesundheitsleistungen&quot;aus.

   ![Anmeldung für Gesundheitsleistungen](/help/forms/using/assets/enrollment_application.png)

   Das Erscheinungsbild ist gleich, und sie muss keine Daten erneut eingeben.

   **Benutzeranweisungen:**

1. Klicken Sie auf die rechte Circle CTA, um zum nächsten Abschnitt zu wechseln.

   ![RIght Kreis CTA](/help/forms/using/assets/right_circle_cta_new.png)

   Das Formular wird bis zum letzten Eintrag von Aya ausgefüllt. Aya hat alle ihre Informationen eingegeben und ist bereit zu übermitteln.

   ![Senden des adaptiven Formulars](/help/forms/using/assets/submit_adaptive_form.png)

   Nach dem Senden erhält Aya eine E-Mail, die sie öffnet und kann mit Adobe Sign elektronisch signiert werden.

**Benutzeranweisungen:**

1. Nach dem Senden wird eine Dankeseite angezeigt.
1. Navigieren Sie zu Ihrem E-Mail-Client und suchen Sie die Adobe Sign-E-Mail.
1. Klicken Sie auf den Link zu Adobe Sign.

   ![Adobe-Link](/help/forms/using/assets/adobe_sign_link.png)

**Benutzeranweisungen:**

1. Markieren Sie das Kästchen &quot;**Ich bin einverstanden**&quot;.
1. Klicken Sie auf &quot;**Akzeptieren**&quot;.
1. Blättern Sie zum unteren Rand des überprüften Dokuments.
1. Klicken Sie auf die hervorgehobene gelbe Registerkarte, um das Dokument zu signieren.

   ![Dokument](/help/forms/using/assets/sign_document_new.png) signieren ![Signieren Sie das Dokument Test](/help/forms/using/assets/sign_test_document.png)

## Regierungsvertreter (George) {#government-agent-george}

![Regierungsagent George](/help/forms/using/assets/george_lang-1.png)

**Dieser Abschnitt:** George ist ein Geschäftsanalyst der Regierung Agentur Aya ist ein Antrag auf einen Dienst von. George hat ein einziges Dashboard, in dem er alle Serviceanforderungsanträge sehen kann, die ihm zur Überprüfung zugewiesen wurden.

### George User Story (AEM-Posteingang) {#george-user-story-aem-inbox}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klicken Sie auf das Benutzersymbol (obere rechte Ecke) und verwenden Sie die Menüoption &quot;**Abmelden**&quot;oder &quot;**Identität annehmen als**&quot;, wenn Sie derzeit bei einem Administrator angemeldet sind.

   1. Anmelden mit:

      1. **Benutzer:** george.lang
      1. **Kennwort:** password
   1. Oder imitieren Sie:

      1. Geben Sie &quot;**George**&quot;in das Feld &quot;**Impersonate as**&quot;ein.

      1. Klicken Sie auf OK, um sich zu imitieren.


1. Klicken Sie in der oberen rechten Ecke auf das Benachrichtigungssymbol (Glockensymbol).
1. Klicken Sie auf &quot;**Ansicht alle**&quot;, um zum Posteingang zu navigieren.
1. Öffnen Sie im Posteingang die neueste Aufgabe &quot;**Health Benefits Application Review**&quot;.

   ![Antragsüberprüfung für Gesundheitsvorteile](/help/forms/using/assets/health_benefits.png)

### George User Story (AEM-Posteingang und MS Dynamics) {#george-user-story-aem-inbox-and-ms-dynamics}

Dank Datenintegrationen und automatisierter Workflows erscheint die Anwendung von Aya zusammen mit einem CRM-Datensatz, der beim Senden der Daten automatisch generiert wurde.

**Benutzeranweisungen:**

1. Öffnen und überprüfen Sie das schreibgeschützte adaptive Formular.
1. Klicken Sie auf die Schaltfläche &quot;**Open MS Dynamics**&quot;, um den MS Dynamics Datensatz in einem neuen Fenster zu öffnen.
1. Im CRM können Sie alle Informationen sehen, die aktualisiert werden können

   1. Fügen Sie optional einige Review-Notizen direkt in Dynamics hinzu.

1. Schließen Sie den AEM-Posteingang und kehren Sie zu ihm zurück.

   ![MS Dynamics Record](/help/forms/using/assets/ms_dynamics.png)

### George User Story (zurück zum AEM-Posteingang) {#george-user-story-back-to-aem-inbox}

George genehmigt den Antrag von Aya und dank eines bereits vorhandenen automatisierten Workflows wird auch eine Bestätigungs-E-Mail an Aya gesendet.

**Benutzeranweisungen:**

1. Navigieren Sie zur oberen linken Ecke und klicken Sie auf &quot;**Genehmigen**&quot;, um den Antrag zu genehmigen.
1. Im Modal können Sie eine Nachricht für den CX-Lead hinterlassen.
1. Klicken Sie auf Fertig.
1. (Citizen role) Öffnen Sie Ihren E-Mail-Client, um die an Aya gesendete E-Mail Ansicht.

   ![Ansicht der an Aya gesendeten E-Mail](/help/forms/using/assets/email_client.png)

## CX-Blei (Camila) {#cx-lead-camila}

![Camila (CX-Lead)](/help/forms/using/assets/camila_santos-1.png)

**Dieser Abschnitt:** Camila der CX Lead richtet mit Aya einen Begrüßungs-Telefonanruf ein, um zu erklären, wie die von ihr genehmigten Regierungsdienste genutzt werden können.

### Camila User Story (AEM inbox &amp; MS Dynamics) {#camila-user-story-aem-inbox-ms-dynamics}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klicken Sie auf das Benutzersymbol (obere rechte Ecke) und verwenden Sie die Menüoption &quot;**Abmelden**&quot;oder &quot;**Identität annehmen als**&quot;, wenn Sie derzeit bei einem Administrator angemeldet sind.

   1. Anmelden mit:

      1. **Benutzer**: camila.santos
      1. **Kennwort:** password
   1. Oder imitieren Sie:

      1. Geben Sie &quot;**Camila**&quot;in das Feld &quot;**Impersonate as**&quot;ein.

      1. Klicken Sie auf OK, um sich zu imitieren.


1. Klicken Sie in der oberen rechten Ecke auf das Symbol Benachrichtigung (Glocke).
1. Klicken Sie auf &quot;**Ansicht alle**&quot;, um zum Posteingang zu navigieren.
1. Öffnen Sie im Posteingang die neueste Aufgabe &quot;**Neue Kontaktgenehmigung**&quot;.

   ![Neue Kontaktgenehmigung](/help/forms/using/assets/new_contact_approval.png)

   **Benutzeranweisungen:**

1. Öffnen und überprüfen Sie das schreibgeschützte adaptive Formular.
1. Klicken Sie auf die Schaltfläche &quot;**Open MS Dynamics**&quot;, um den MS Dynamics Datensatz in einem neuen Fenster zu öffnen.
1. Im CRM können Sie alle Informationen sehen, die aktualisiert werden können

   1. Fügen Sie optional eine neue Call-Aktivität direkt in Dynamics hinzu.
   1. Öffnen Sie den Abschnitt &quot;**Aktivitäten**&quot;.
   1. Klicken Sie auf die Option &quot;**Neuer Telefonanruf**&quot;.
   1. Hinzufügen Telefonnummer.
   1. Speichern und schließen Sie das Fenster.

1. Zurück in AEM navigieren Sie zur oberen linken Ecke und klicken Sie auf &quot;**Senden**&quot;, um die Anwendung zu senden.
1. Im Modal können Sie eine Nachricht hinterlassen.
1. Klicken Sie auf Fertig.

   ![Registerkarte](/help/forms/using/assets/activities_tab.png) &quot;Aktivitäten&quot; ![Neuen Kontakt bestätigen](/help/forms/using/assets/confirm_new_contact.png)

## Willkommen-Kit-Bürger (Aya) {#welcome-kit-citizen-aya}

**Dieser Abschnitt:** Aya erhält eine E-Mail mit einem Link zu einer interaktiven Kommunikation, die ihre Vorteile zusammenfasst und auch Formularfelder zum Ausfüllen enthält. PDF-Vorteilsauszüge angehängt und Link zum interaktiven Kommunikationsbrief in der E-Mail (mit demselben Thema/demselben Branding wie die interaktive Kommunikation).

### Aya-Benutzergeschichte (E-Mail-Client) {#aya-user-story-email-client}

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

### Aya-Benutzergeschichte (E-Mail-Client) {#aya-user-story-email-client-1}

**Benutzeranweisungen:**

1. Navigieren Sie zu Ihrem E-Mail-Client.
1. Suchen Sie die E-Mail zur Erinnerung an die Verlängerung und öffnen Sie sie.
1. Klicken Sie auf die Schaltfläche &quot;Neue Anwendung **senden**&quot;, um das adaptive Formular zu öffnen.

   1. Dieser Abschnitt wird absichtlich leer gelassen, um die Vorfüllung von Daten in Phase 2 zu unterstützen.
   ![E-Mail zur Erinnerung](/help/forms/using/assets/renewal_reminder_email.png)

## Analytics CX-Lead (Camila) {#analytics-cx-lead-camila}

**Dieser Abschnitt:** Camila navigiert zu einem Dashboard, in dem sie über die KPIs der Agentur hinweg sehen kann, wie z. B. % der Beginn, die ein Serviceanfrageformular ausfüllen und abbrechen, die durchschnittliche Dauer von der Antragstellung bis zur Genehmigung/Ablehnung und Interaktionsstatistiken für die von ihr an die Bürger gesendeten Vorteilshandbücher.

### Camila prüft Sites Berichte (We.Gov Adobe Analytics) {#camila-reviews-sites-reporting-we-gov-adobe-analytics}

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Wählen Sie die &quot;**AEM Forms We.Gov-Site**&quot;, um die Seiten der Site Ansicht.
1. Wählen Sie eine der Siteseiten (z.B. Startseite) und wählen Sie &quot;**Analytics &amp; Recommendations**&quot;.

   ![Analytics und Empfehlung](/help/forms/using/assets/analytics_recommendation.jpg)

1. Auf dieser Seite sehen Sie die abgerufenen Informationen aus Adobe Analytics, die sich auf die Seite AEM-Sites beziehen (HINWEIS: Diese Informationen werden regelmäßig von Adobe Analytics aktualisiert und nicht in Echtzeit angezeigt.

   ![Adobe Analytics-Schlüsselmetriken](/help/forms/using/assets/analytics_key_metrics.jpg)

1. Zurück auf der Seite &quot;Ansicht&quot;(Zugriff in Schritt 3) können Sie die Seiteninformationen auch durch Ändern der Anzeigeeinstellung in Ansicht der Elemente in der &quot;Ansicht der **Liste**&quot; Ansicht der Ansicht ändern.
1. Suchen Sie das Dropdown-Menü &quot;**Ansicht**&quot;und wählen Sie &quot;**Liste Ansicht**&quot;.

   ![Ansicht der Liste im Dropdown-Menü &quot;Ansicht&quot;](/help/forms/using/assets/list_view_view_dropdown.jpg)

1. Wählen Sie im gleichen Menü die Option &quot;**Ansicht einstellen**&quot;und wählen Sie die anzuzeigenden Spalten im Abschnitt &quot;**Analytics**&quot;aus.

   ![Spaltenanzeige konfigurieren](/help/forms/using/assets/view_setting_analytics.jpg)

1. Klicken Sie auf &quot;**Aktualisieren**&quot;, um die neuen Spalten verfügbar zu machen.

   ![Neue Spalten verfügbar machen](/help/forms/using/assets/new_columns_available.jpg)

### Camila prüft Forms Berichte (We.Gov Adobe Analytics) {#camila-reviews-forms-reporting-we-gov-adobe-analytics}

1. Navigieren Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Wählen Sie das adaptive Formular &quot;**Registrierungsantrag für Gesundheitsvorteile**&quot;und wählen Sie die Option &quot;**Analysebericht**&quot;aus.

   ![Anmeldung für Gesundheitsleistungen](/help/forms/using/assets/analytics_report_benefits.jpg)

1. Warten Sie, bis die Seite geladen wurde, und Ansicht der Analytics-Berichtsdaten.

   ![Analytics-Berichtsdaten](/help/forms/using/assets/analytics_report_data_updated.jpg)

