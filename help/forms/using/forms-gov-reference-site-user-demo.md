---
title: exemplarische Vorgehensweise für die Referenzseite "We.Gov"und "We.Finance"
seo-title: exemplarische Vorgehensweise für die Referenzseite "We.Gov"und "We.Finance"
description: Verwenden Sie fiktive Benutzer und Gruppen, um AEM Forms-Aufgaben mithilfe des Demopakets We.Gov und We.Finance durchzuführen.
seo-description: Verwenden Sie fiktive Benutzer und Gruppen, um AEM Forms-Aufgaben mithilfe des Demopakets We.Gov und We.Finance durchzuführen.
uuid: 797e301a-36ed-4bae-9ea8-ee77285c786d
contentOwner: anujkapo
discoiquuid: ddb3778b-be06-4cde-bc6e-0994efa42b18
docset: aem65
translation-type: tm+mt
source-git-commit: c6b8e184042394d99ceb099c918b81e2cce49497
workflow-type: tm+mt
source-wordcount: '2548'
ht-degree: 1%

---


# Website-Umgehungslösung für We.Gov und We.Finance{#we-gov-reference-site-walkthrough}

## Voraussetzungen {#pre-requisites}

Richten Sie die Referenz-Website ein, wie unter [Einrichten und Konfigurieren von We.Gov- und We.Finance-Referenz-Website](../../forms/using/forms-install-configure-gov-reference-site.md) beschrieben.

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
* Datenquellenintegrationen

### Fiktive Benutzer und Gruppen {#fictitious-users-and-groups}

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

### Übersicht über die Demo-Begriffe legend {#demo-overview-terms-legend}

1. **Identität annehmen**: Definierte Benutzer und Gruppen in AEM Demo.
1. **Schaltfläche**: Farbiges Rechteck oder kreisförmiger Pfeil zum Navigieren.
1. **Klicken Sie auf**: Zum Ausführen einer Aktion im Benutzerverlauf.
1. **Links**: Befindet sich oben im Hauptmenü auf der Website We.Gov.
1. **Benutzeranweisungen**: Eine Reihe numerischer Schritte, die beim Navigieren durch die Benutzergeschichte befolgt werden müssen.
1. **Forms Portal**:  *https://&lt;aemserver>:&lt;port>/content/we-gov/formsportal.html*
1. **Mobil-Ansicht**: Wir.Gov-Benutzer, der eine mobile Ansicht mit einem Browser in der neuen Größe repliziert.
1. **Desktop-Ansicht**: Wir.gov user to Ansicht demo on a Laptop oder desktop.
1. **Formular** vor dem Bildschirm: Formular auf der Startseite der Website We.Gov.
1. **Adaptives Formular**: Antragsformular für die Anmeldung bei We.gov.

   *https://&lt;aemserver>:&lt;port>/content/forms/af/adobe-gov-forms/enrollment-application-for-health-benefits.html*

1. **Website** der Adobe Wir.Gov:  *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. **Adobe-Posteingang**: Befindet sich in der oberen Menüleiste  [Bell-](assets/bell.svg) Symbol AEM Backend.

   *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. **E-Mail-Client**: Bevorzugte Methode zur Ansicht Ihrer E-Mails (Google Mail, Outlook)
1. **CTA**: Aktionsaufruf
1. **Navigieren**: So suchen Sie einen bestimmten Referenzpunkt auf der Browserseite.
1. **AFC**: automated forms conversion

## automated forms conversion (Camila) {#automated-forms-conversion}

**Dieser Abschnitt**: Camila the CX Lead verfügt über ein PDF-basiertes Formular, das als Teil eines papierbasierten Prozesses verwendet wurde. Im Rahmen der Modernisierung möchte sie dieses PDF-Formular verwenden, um automatisch ein neues adaptives Forms zu erstellen.

### automated forms conversion - We.Gov (Camila) {#automated-forms-conversion-wegov}

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. Anmelden mit:
   * **Benutzer**: camila.santos
   * **Kennwort:** password
1. Wählen Sie auf der Hauptseite Forms > Forms &amp; Dokumente > AEM Forms We.gov Forms > AFC.
1. Camila lädt die PDF-Datei nach AEM Forms hoch.

   ![Formular hochladen](assets/aftia-upload-form.jpg)

1. Anschließend wählt Camilla das PDF-Formular aus und klickt auf **Beginn Automatisierte Konversion**, um den Konvertierungsprozess Beginn. Wenn Sie das Formular konvertiert haben, müssen Sie möglicherweise auf **Konvertierung überschreiben** klicken.

   >[!NOTE]
   >
   >Beachten Sie, dass die Einstellungen in AFC für den Endbenutzer vorkonfiguriert sind, was bedeutet, dass sie nicht geändert werden sollten.

   * **Optional**: Wenn Sie das Design Accessible Ultramarine verwenden möchten, klicken Sie einfach auf das Design Adaptives Formular angeben und wählen Sie das Thema Accessible-Ultramarine aus, das in der Liste der Optionen angezeigt wird.

   ![Beginn-Umrechnung](assets/aftia-start-conversion.jpg)

   ![Ultramarine-Design](assets/aftia-upload-conversion-settings.jpg)

   Der Status &quot;Prozentsatz abgeschlossen&quot;wird während der Konvertierung angezeigt. Sobald der Status **Konvertiert** angezeigt wird, klicken Sie auf den Ordner **output**, wählen Sie das adaptive Formular aus und klicken Sie auf **Bearbeiten**, um das konvertierte Formular zu öffnen.

1. Camilla prüft dann das Formular und stellt sicher, dass alle Felder vorhanden sind

   ![Umrechnung überprüfen](assets/aftia-review-conversion.jpg)

1. Camilla dann Beginn, um das Formular zu bearbeiten. Sie wählt &quot;Stammfeld&quot;> &quot;Bearbeiten&quot;(Schraubenschlüssel) > &quot;Obere Registerkarten&quot;aus dem Dropdown-Menü &quot;Bedienfeldlayout&quot;aus und wählt das Kontrollkästchen aus.

   ![Eigenschaften überprüfen](assets/aftia-review-properties.jpg)

1. Camilla fügt dann alle notwendigen CSS und Feldveränderungen hinzu, um das Endprodukt zu produzieren.

   ![hinzufügen CSS](assets/aftia-add-css.jpg)

### Formulardatenmodell und Datenquellen (Camila) {#data-sources}

**Dieser Abschnitt**: Nachdem das Dokument konvertiert und ein adaptives Formular erstellt wurde, muss Camila das adaptive Formular mit einer Datenquelle verbinden.

1. Camila öffnet die Eigenschaften auf dem Formular, das in [Automated forms conversion - We.Gov](#automated-forms-conversion-wegov) konvertiert wurde.

1. Camila wählt dann Formularmodell > Wählt Formulardatenmodell aus der Dropdown-Liste Auswahl aus > Wählt Web.gov-Registrierungs-FDM aus der Liste der Option aus.

1. Klicken Sie auf die Schaltfläche Speichern und Schließen.

   ![FDM-Auswahl](assets/aftia-select-fdm.jpg)

1. Camila klickt auf den Ordner **output**, wählt das adaptive Formular aus und klickt auf **Bearbeiten**, um das ausgefüllte We.Gov-Formular zu öffnen.
1. Camila wählt ein Feld für ein adaptives Formular aus und klickt auf ![Symbol konfigurieren](assets/configure-icon.svg). Sie erstellt mithilfe des Felds **Bindungsreferenz** eine Bindung mit den Formulardatenmodellentitäten. Sie wiederholt diesen Schritt für alle Felder im adaptiven Formular.

### Barrierefreiheitstest für Formulare (Camila) {#form-accessibility-testing}

Camila überprüft auch, ob die erstellten Inhalte korrekt und vollständig zugänglich gemäß den Unternehmensstandards erstellt wurden.

1. Camila klickt auf den Ordner **output**, wählt das adaptive Formular aus und klickt auf **Vorschau**, um das ausgefüllte We.Gov-Formular zu öffnen.

1. Öffnet die Registerkarte &quot;Prüfung&quot;im Chrome Developer Tool.

1. Führt eine Barrierefreiheitsprüfung durch, um das adaptive Formular zu validieren.

   ![Barrierefreiheitsprüfung](assets/aftia-accessibility.jpg)

## Demo zur mobilen Ansicht für adaptive Formulare (Aya) {#mobile-view-demo}

**Dieser Abschnitt muss vor der Demonstration durchgeführt werden.**

**Benutzeranweisungen:**

1. Navigieren Sie zu: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Anmelden mit:

   1. **Benutzer**: aya.tan
   1. **Kennwort:** password

1. Ändern Sie die Größe des Browser-Fensters oder verwenden Sie den Emulator des Browsers, um die Größe eines Mobilgeräts zu replizieren.

### We.Gov-Website (Aya) {#aya-user-story-we-gov-website}

![Schlaue Benutzer](/help/forms/using/assets/aya_tan_new-1.png)

**Dieser Abschnitt**: Aya ist ein Bürger. Sie hört von einer Freundin, dass sie möglicherweise berechtigt ist, eine Dienstleistung von einer Regierungsbehörde zu erhalten. Aya navigiert von ihrem Handy zur Website We.Gov, um mehr über Dienste zu erfahren, für die sie berechtigt ist.

### We.Gov Pre-Screener (AY) {#aya-user-story-we-gov-pre-screener}

Aya beantwortet einige Fragen, um ihre Berechtigung zu bestätigen, indem sie ein kurzes adaptives Formular auf ihrem Handy ausfüllt.

**Benutzeranweisungen:**

1. Wählen Sie in jedem Dropdown-Feld eine Auswahl aus.

   >[!NOTE]
   >
   >Wenn der Benutzer mehr als 200.000 USD pro Jahr verdient, sind die Benutzer nicht berechtigt.

1. Klicken Sie auf &quot;**Bin ich berechtigt?**” button.
1. Klicken Sie auf die Schaltfläche &quot;**Jetzt anwenden**&quot;, um fortzufahren.

   ![Jetzt anwenden](/help/forms/using/assets/apply_now_link.png)

### We.Gov Adaptive Form (Aya) {#aya-user-story-we-gov-adaptive-form}

Aya stellt fest, dass sie berechtigt ist, und beginnt, ihren Antrag auszufüllen, um einen Service auf ihrem Mobilgerät anzufordern.

Aya muss einige Dokumente zu Hause überprüfen, bevor sie die Serviceanfrage abschließen kann. Sie speichert und verlässt die Anwendung von ihrem Mobilgerät.

**Benutzeranweisungen:**

1. Füllen Sie die Felder Grundlegende Informationen aus, die folgenden Felder sind Pflichtfelder und Dropdown-Listen:

   1. Grundlegende Informationen

      1. Vorname
      1. Nachname
      1. DOB
      1. E-Mail

1. Verwenden Sie die folgende **dynamische Logik**, um eine dynamische Funktion mithilfe der Dropdownliste **Familienstand** zu demonstrieren:

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

**Dieser Abschnitt:** Zurück zu Hause, Aya hat die Informationen, die sie brauchte, gefunden und setzt die Anwendung von ihrem Desktop. Aya navigiert zum Online-Formularportal, um ihre Anwendung wiederaufzunehmen. Durch eine einfache Anpassung können Agenturen auch automatisch einen Link erstellen und per E-Mail versenden, um die Anwendung wiederaufzunehmen.

### Kontinuierliches adaptives Formular (Aya) {#aya-user-story-continued-adaptive-form}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Klicken Sie in der Navigationsleiste auf &quot;**Online-Dienste**&quot;.
1. Wählen Sie im Bedienfeld &quot;Entwurf des Forms&quot;die bestehende &quot;Registrierungsanwendung für Gesundheitsleistungen&quot;aus.

   ![Anmeldung für Gesundheitsleistungen](/help/forms/using/assets/enrollment_application.png)

   Das Erscheinungsbild ist gleich, und sie muss keine Daten erneut eingeben.

   **Benutzeranweisungen:**

1. Klicken Sie auf die rechte Circle CTA, um zum nächsten Abschnitt zu wechseln.

   ![RIght Kreis CTA](/help/forms/using/assets/right_circle_cta_new.png)

   Das Formular wird bis zum letzten Eintrag von Aya ausgefüllt. Aya hat alle ihre Informationen eingegeben und ist bereit zu übermitteln.

   ![Senden des adaptiven Formulars](/help/forms/using/assets/submit_adaptive_form.png)

   >[!NOTE]
   >
   >Wenn Aya das Telefonnummernfeld ausfüllt, muss sie es als durchgehende 11-stellige Zahl ohne Bindestriche, Leerzeichen oder Bindestriche ausfüllen.

   Nach dem Senden erhält Aya eine Dankeseite. Optional erhält sie auch eine E-Mail, die sie öffnen kann, um das Dokument der Aufzeichnung elektronisch mit Adobe Sign zu unterzeichnen.

### Optional: Adobe Sign (Aya) {#adobe-sign}

**Benutzeranweisungen:**

1. Navigieren Sie zu Ihrem E-Mail-Client und suchen Sie die Adobe Sign-E-Mail.
1. Klicken Sie auf den Link zu Adobe Sign.

   ![Link zum Adoben-Zeichen](/help/forms/using/assets/adobe_sign_link.png)

**Benutzeranweisungen:**

1. Markieren Sie das Feld &quot;**Ich stimme zu**&quot;.
1. Klicken Sie auf &quot;**Accept**&quot;.
1. Blättern Sie zum unteren Rand des überprüften Dokuments.
1. Klicken Sie auf die hervorgehobene gelbe Registerkarte, um das Dokument zu signieren.

   ![Signieren Sie das ](/help/forms/using/assets/sign_document_new.png) ![DokumentSignieren Sie das Test-Dokument](/help/forms/using/assets/sign_test_document.png)

## Regierungsvertreter (George) {#government-agent-george}

![Regierungsagent George](/help/forms/using/assets/george_lang-1.png)

**Dieser Abschnitt:** George ist ein Geschäftsanalyst der Regierung Agentur Aya ist eine Anfrage von einem Dienst. George hat ein einziges Dashboard, in dem er alle Serviceanforderungsanträge sehen kann, die ihm zur Überprüfung zugewiesen wurden.

### AEM Posteingang (George) {#george-user-story-aem-inbox}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klicken Sie auf das Benutzersymbol (obere rechte Ecke) und verwenden Sie die Menüoption &quot;**Abmelden**&quot;oder &quot;**Identität annehmen als**&quot;, wenn Sie derzeit bei einem Administrator angemeldet sind.

   1. Anmelden mit:

      1. **Benutzer:** george.lang
      1. **Kennwort:** password
   1. Oder imitieren Sie:

      1. Geben Sie &quot;**George**&quot;in das Feld &quot;**Identität annehmen als**&quot;ein.

      1. Klicken Sie auf OK, um sich zu imitieren.


1. Klicken Sie in der oberen rechten Ecke auf das Benachrichtigungssymbol (Glockensymbol).
1. Klicken Sie auf &quot;**Ansicht All**&quot;, um zum Posteingang zu navigieren.
1. Öffnen Sie im Posteingang die neueste Aufgabe &quot;**Health Benefits Application Review**&quot;.

   ![Antragsüberprüfung für Gesundheitsvorteile](/help/forms/using/assets/health_benefits.png)

### Optional: AEM Inbox &amp; MS Dynamics (George) {#george-user-story-aem-inbox-and-ms-dynamics}

Dank Datenintegrationen und automatisierter Workflows erscheint die Anwendung von Aya zusammen mit einem CRM-Datensatz, der beim Senden der Daten automatisch generiert wurde.

**Benutzeranweisungen:**

1. Öffnen und überprüfen Sie das schreibgeschützte adaptive Formular.
1. Klicken Sie auf die Schaltfläche &quot;**MS Dynamics öffnen**&quot;, um den MS Dynamics Datensatz in einem neuen Fenster zu öffnen.
1. Im CRM können Sie alle Informationen sehen, die aktualisiert werden können

   1. Fügen Sie optional einige Review-Notizen direkt in Dynamics hinzu.

1. Schließen Sie den Posteingang und kehren Sie zu AEM Posteingang zurück.

   ![MS Dynamics Record](/help/forms/using/assets/ms_dynamics.png)

### Zurück zum AEM Posteingang (George) {#george-user-story-back-to-aem-inbox}

George genehmigt den Antrag von Aya und dank eines bereits vorhandenen automatisierten Workflows wird auch eine Bestätigungs-E-Mail an Aya gesendet.

**Benutzeranweisungen:**

1. Navigieren Sie zur oberen linken Ecke und klicken Sie auf &quot;**Genehmigen**&quot;, um den Antrag zu genehmigen.
1. Im Modal können Sie eine Nachricht für den CX-Lead hinterlassen.
1. Klicken Sie auf Fertig.
1. (Citizen role) Öffnen Sie Ihren E-Mail-Client, um die an Aya gesendete E-Mail Ansicht.

   ![Ansicht der an Aya gesendeten E-Mail](/help/forms/using/assets/email_client.png)

## CX-Blei (Camila) {#cx-lead-camila}

![Camila (CX-Lead)](/help/forms/using/assets/camila_santos-1.png)

**Dieser Abschnitt:** Camila der CX Lead richtet einen Begrüßungs-Telefonanruf mit Aya ein, um zu erklären, wie man die staatlichen Dienste, für die sie genehmigt wurde, nutzen kann.

### (Optional) AEM Inbox &amp; MS Dynamics {#camila-user-story-aem-inbox-ms-dynamics}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klicken Sie auf das Benutzersymbol (obere rechte Ecke) und verwenden Sie die Menüoption &quot;**Abmelden**&quot;oder &quot;**Identität annehmen als**&quot;, wenn Sie derzeit bei einem Administrator angemeldet sind.

   1. Anmelden mit:

      1. **Benutzer**: camila.santos
      1. **Kennwort:** password
   1. Oder imitieren Sie:

      1. Geben Sie &quot;**Camila**&quot;in das Feld &quot;**Identität annehmen als**&quot;ein.

      1. Klicken Sie auf OK, um sich zu imitieren.


1. Klicken Sie in der oberen rechten Ecke auf das Symbol Benachrichtigung (Glocke).
1. Klicken Sie auf &quot;**Ansicht All**&quot;, um zum Posteingang zu navigieren.
1. Öffnen Sie im Posteingang die neueste Aufgabe &quot;**Neue Kontaktgenehmigung**&quot;.

![Neue Kontaktgenehmigung](/help/forms/using/assets/new_contact_approval.png)

**(Optional) Benutzeranweisungen:**

1. Öffnen und überprüfen Sie das schreibgeschützte adaptive Formular.
1. Klicken Sie auf die Schaltfläche &quot;**MS Dynamics öffnen**&quot;, um den MS Dynamics Datensatz in einem neuen Fenster zu öffnen.
1. Im CRM können Sie alle Informationen sehen, die aktualisiert werden können

   1. Fügen Sie optional eine neue Call-Aktivität direkt in Dynamics hinzu.
   1. Öffnen Sie den Abschnitt &quot;**Aktivitäten**&quot;.
   1. Klicken Sie auf die Option &quot;**Neuer Telefonaufruf**&quot;.
   1. hinzufügen Telefonnummer.
   1. Speichern und schließen Sie das Fenster.

1. Zurück in AEM, navigieren Sie zur oberen linken Ecke und klicken Sie auf &quot;**Senden**&quot;, um den Antrag zu senden.
1. Im Modal können Sie eine Nachricht hinterlassen.
1. Klicken Sie auf Fertig.

   ![Aktivitäten, ](/help/forms/using/assets/activities_tab.png) ![RegisterkarteNeuen Kontakt bestätigen](/help/forms/using/assets/confirm_new_contact.png)

## (Optional) Begrüßungs-Kit Bürger (Aya) {#welcome-kit-citizen-aya}

**Dieser Abschnitt:** Aya erhält eine E-Mail mit einem Link zu einer interaktiven Kommunikation, die ihre Vorteile zusammenfasst und außerdem Formularfelder zum Ausfüllen enthält. PDF-Vorteilsauszüge angehängt und Link zum interaktiven Kommunikationsbrief in der E-Mail (mit demselben Thema/demselben Branding wie die interaktive Kommunikation).

### E-Mail-Client-Benachrichtigung (Aya) {#aya-user-story-email-client}

**Benutzeranweisungen:**

1. Suchen Sie die Begrüßungs-Kit-E-Mail und öffnen Sie sie.
1. Blättern Sie zum PDF-Anhang unten auf der Seite.
1. Klicken Sie auf , um die PDF-Anlage zu öffnen.
1. Blättern Sie im E-Mail-Client nach oben und klicken Sie auf &quot;**Ansicht Begrüßungs-Kit online**&quot;.

   1. Dadurch wird die Web-Kanal-Version desselben Dokuments geöffnet.

1. Eine kurze Referenz zu PDF direkt:

   *https://&lt;aemserver>:&lt;port>/aem/formdetails.html/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook*

1. Für einen kurzen Hinweis auf IC direkt:

   *https://&lt;aemserver>:&lt;port>/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook/jcr:content?Kanal=web&amp;mode=Vorschau&amp;wcmmode=disabled*

   ![Willkommen - ](/help/forms/using/assets/welcome_benefits_handbook.png) ![HandbuchInteraktiver Kommunikationslink](/help/forms/using/assets/interactive_communication.png)

## Erneuerbare Erinnerung Bürger (Aya) {#renewal-reminder-citizen-aya}

**Dieser Abschnitt:** Camila plant auch eine Erinnerung an die Kommunikation ein Jahr später. (Workflow-Schritt, der automatisiert/ausgeführt und E-Mail versendet).

### E-Mail-Client-Benachrichtigung (Aya) {#aya-user-story-email-client-updated}

**Benutzeranweisungen:**

1. Navigieren Sie zu Ihrem E-Mail-Client.
1. Suchen Sie die E-Mail zur Erinnerung an die Verlängerung und öffnen Sie sie.
1. Klicken Sie auf die Schaltfläche &quot;**Neue Anwendung senden**&quot;, um das adaptive Formular zu öffnen.

   1. Dieser Abschnitt wird absichtlich leer gelassen, um die Vorfüllung von Daten in Phase 2 zu unterstützen.

   ![E-Mail zur Erinnerung](/help/forms/using/assets/renewal_reminder_email.png)

## (Optional) Formulardatenmodell (Camila) {#form-data-model}

**Dieser Abschnitt**: Camila navigiert zu AEM Forms Data Integrations, wo sie einen schnellen Test durchführen kann, um zu sehen, dass die über die Integration des Formulardatenmodells an die externe Datenquelle gesendeten Informationen tatsächlich vorhanden sind.

### Formulardatenmodell (Camila) {#form-data-model-camila}

**Dieser Abschnitt**: Camila navigiert zur Seite &quot;Datenquellen&quot;, um die Daten zu überprüfen, die der Server in der Derby-Datenbank repliziert hat.

1. Sobald die Benutzererfahrung abgeschlossen ist und die Benutzereingabe abgeschlossen ist, navigiert Camila zur Registerkarte &quot;Datenquellen&quot;in AEM Forms (**Forms** > **Datenintegrationen**)

1. Camila wählt dann AEM Forms **We.gov FDM** und bearbeitet dann die **We.gov-Registrierung FDM**.

1. Camila wählt dann **Kontakt** > **Read Service** aus, der getestet werden soll.

   ![Kontaktlesehilfen-Dienst](assets/aftia-contact-read-service.jpg)

1. Camila stellt dann dem Testdienst eine Kontakt-ID zur Verfügung und klickt dann auf die Schaltfläche Test. Beispiel: 1 oder 2, wenn Sie das Formular gesendet haben. Wenn Sie das Formular nicht gesendet haben, werden keine Daten zurückgegeben.

   ![Kontaktlesehilfen-Dienst](assets/aftia-test-service.jpg)

1. Camila kann dann überprüfen, ob die Daten erfolgreich in die Datenquelle eingefügt wurden.

   * Die Daten innerhalb des Derby DS entsprechen dem folgenden Format:

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

**Dieser Abschnitt:** Camila navigiert zu einem Dashboard, in dem sie über die KPIs der Agentur hinweg sehen kann, wie z. B. % der Beginn, die ein Serviceanforderungsformular ausfüllen und abbrechen, die durchschnittliche Zeitspanne von der Antragstellung bis zur Genehmigung/Ablehnung der Antwort und Interaktionsstatistiken für die Leistungshandbücher, die sie an die Bürger gesendet hat.

### Adobe Analytics Sites Berichte (Camila) {#camila-reviews-sites-reporting-we-gov-adobe-analytics}

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Wählen Sie die Site &quot;**AEM Forms We.Gov Site**&quot;, um die Seiten der Site Ansicht.
1. Wählen Sie eine der Siteseiten (z. B. &quot;Home&quot;) und wählen Sie &quot;**Analytics &amp; Recommendations**&quot;.

   ![Analytics und Empfehlung](/help/forms/using/assets/analytics_recommendation.jpg)

1. Auf dieser Seite finden Sie Informationen von Adobe Analytics, die zur Seite AEM Sites gehören (HINWEIS: Diese Informationen werden von Adobe Analytics regelmäßig aktualisiert und nicht in Echtzeit angezeigt.

   ![Adobe Analytics-Schlüsselmetriken](/help/forms/using/assets/analytics_key_metrics.jpg)

1. Zurück auf der Seite &quot;Ansicht&quot;(Zugriff in Schritt 3) können Sie die Seiteninformationen auch durch Ändern der Anzeigeeinstellung in &quot;Ansicht&quot;-Elemente in der Ansicht &quot;**Liste**&quot; Ansicht der Seiteninformationen hinzufügen.
1. Suchen Sie im Dropdown-Menü &quot;**Ansicht**&quot;die Option &quot;**Liste-Ansicht**&quot;.

   ![Ansicht der Liste im Dropdown-Menü &quot;Ansicht&quot;](/help/forms/using/assets/list_view_view_dropdown.jpg)

1. Wählen Sie im gleichen Menü &quot;**Ansicht-Einstellung**&quot;und wählen Sie die anzuzeigenden Spalten im Abschnitt &quot;**Analytics**&quot;aus.

   ![Spaltenanzeige konfigurieren](/help/forms/using/assets/view_setting_analytics.jpg)

1. Klicken Sie auf &quot;**Update**&quot;, um die neuen Spalten verfügbar zu machen.

   ![Neue Spalten verfügbar machen](/help/forms/using/assets/new_columns_available.jpg)

### Adobe Analytics Forms Berichte (Camila) {#camila-reviews-forms-reporting-we-gov-adobe-analytics}

1. Navigieren Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Wählen Sie das adaptive Formular &quot;**Registrierungsanwendung für Gesundheitsleistungen**&quot;und wählen Sie die Option &quot;**Analytics-Bericht**&quot;aus.

   ![Anmeldung für Gesundheitsleistungen](/help/forms/using/assets/analytics_report_benefits.jpg)

1. Warten Sie, bis die Seite geladen wurde, und Ansicht der Analytics-Berichtsdaten.

   ![Analytics-Berichtsdaten](/help/forms/using/assets/analytics_report_data_updated.jpg)

