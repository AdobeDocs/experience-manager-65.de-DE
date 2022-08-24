---
title: Schrittweise Anleitung zur We.Gov- und We.Finance-Referenz-Website
seo-title: We.Gov and We.Finance reference site walkthrough
description: Verwenden Sie fiktive Benutzer und Gruppen, um AEM Forms-Aufgaben mithilfe des Demopakets We.Gov und We.Finance durchzuführen.
seo-description: Use fictitious users and groups to perform AEM Forms tasks using We.Gov and We.Finance demo package.
uuid: 797e301a-36ed-4bae-9ea8-ee77285c786d
contentOwner: anujkapo
discoiquuid: ddb3778b-be06-4cde-bc6e-0994efa42b18
docset: aem65
exl-id: 288d5459-bc69-4328-b6c9-4b4960bf4977
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '2526'
ht-degree: 85%

---

# Schrittweise Anleitung zur We.Gov- und We.Finance-Referenz-Website {#we-gov-reference-site-walkthrough}

## Voraussetzungen {#pre-requisites}

Richten Sie die Referenz-Website ein, wie unter [Einrichten und Konfigurieren der Referenz-Website We.Gov und We.Finance](../../forms/using/forms-install-configure-gov-reference-site.md) beschrieben.

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

Das Demopaket We.Gov enthält die folgenden integrierten fiktiven Benutzer:

* **Aya Tan**: Bürgerin, die für eine Dienstleistung von einer Regierungsstelle in Betracht kommt.

![Fiktiver Benutzer](/help/forms/using/assets/aya_tan_new.png)

* **George Lang**: We.Gov Agency Business Analyst

![Fiktiver Benutzer](/help/forms/using/assets/george_lang.png)

* **Camila Santos**: We.Gov Agency CX Lead

![Fiktiver Benutzer](/help/forms/using/assets/camila_santos.png)

Die folgenden Gruppen sind ebenfalls enthalten:

* **We.Gov Forms-Benutzer**

   * George Lang (Mitglied)
   * Camila Santos (Mitglied)

* **We.Gov-Benutzer**

   * George Lang (Mitglied)
   * Camila Santos (Mitglied)
   * Aya Tan (Mitglied)

### Legende zu Demoübersichtsbegriffen {#demo-overview-terms-legend}

1. **Stellvertretend agieren**: Definierte Benutzer und Gruppen in AEM Demo.
1. **Schaltfläche**: Farbige Rechtecke oder umkreiste Pfeile für die Navigation.
1. **Klicken**: So führen Sie eine Aktion in der Benutzergeschichte aus.
1. **Links**: Befinden sich oben im Hauptmenü auf der We.Gov-Seite.
1. **Benutzeranweisungen**: Eine Reihe numerischer Schritte, die beim Navigieren durch die Benutzergeschichte ausgeführt werden müssen.
1. **Forms Portal**: *https://&lt;aemserver>:&lt;port>/content/we-gov/formsportal.html*
1. **Mobilansicht**: We.Gov-Benutzer, um eine Mobilansicht mit einem Browser zu replizieren, der die Größe angepasst hat.
1. **Desktop-Ansicht**: We.gov-Benutzer, um Demo auf einem Laptop oder Desktop anzuzeigen.
1. **Formular für Vorbildschirme**: Formular auf der Startseite der Seite We.Gov.
1. **Adaptives Formular**: Antragsformular für die Anmeldung für die Demo We.gov.

   *https://&lt;aemserver>:&lt;port>/content/forms/af/adobe-gov-forms/enrollment-application-for-health-benefits.html*

1. **Adobe-We.Gov-Seite**: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. **Adobe-Posteingang**: Ausgewählte obere Menüleiste [Glockensymbol](assets/bell.svg) in AEM Backend.

   *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. **Email-Client**: Bevorzugte Methode zum Anzeigen von E-Mails (Gmail, Outlook)
1. **CTA**: Aktionsaufruf
1. **Navigieren**: Suchen eines bestimmten Referenzpunkts auf der Browser-Seite.
1. **AFC**: automatische Forms-Konversion

## Automatische Forms-Konversion (Camila) {#automated-forms-conversion}

**Dieser Abschnitt**: Camila, der CX Lead, verfügt über ein bereits existierendes PDF-basiertes Formular, das im Rahmen eines papierbasierten Prozesses verwendet wurde. Im Rahmen eines Modernisierungsprozesses möchte sie dieses PDF-Formular verwenden, um automatisch ein neues modernes adaptives Forms zu erstellen.

### Automatische Forms-Konversion - We.Gov (Camila) {#automated-forms-conversion-wegov}

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. Anmelden mit:
   * **Benutzer**: camila.santos
   * **Kennwort:** password
1. Wählen Sie auf der Hauptseite Forms > Forms &amp; Documents > AEM Forms We.gov Forms > AFC aus.
1. Camila lädt das PDF auf AEM Forms hoch.

   ![Formular hochladen](assets/aftia-upload-form.jpg)

1. Camilla wählt dann das PDF-Formular aus und klickt auf **Automatische Konversion starten**, um den Konvertierungsprozess zu starten. Möglicherweise müssen Sie auf **Konvertierung überschreiben** klicken, wenn Sie das Formular konvertiert haben.

   >[!NOTE]
   >
   >Beachten Sie, dass die Einstellungen in AFC für den Endbenutzer vorkonfiguriert sind, was bedeutet, dass sie nicht geändert werden sollten.

   * **Optional**: Wenn Sie das Thema Accessible Ultramarine verwenden möchten, klicken Sie einfach auf das Thema adaptives Formular angeben und wählen Sie das Thema Accessible-Ultramarine aus, das in der Liste der Optionen angezeigt wird.

   ![Konvertierung starten](assets/aftia-start-conversion.jpg)

   ![Ultramarine-Design](assets/aftia-upload-conversion-settings.jpg)

   Der prozentuale Abschlussstatus wird während der Konvertierung angezeigt. Sobald der Status **Konvertiert** anzeigt, klicken Sie auf den **Ausgabe**-Ordner, wählen Sie das adaptive Formular aus und klicken Sie auf **Bearbeiten**, um das konvertierte Formular zu öffnen.

1. Camilla prüft dann das Formular und stellt sicher, dass alle Felder vorhanden sind

   ![Konvertierung prüfen](assets/aftia-review-conversion.jpg)

1. Camilla beginnt dann mit der Bearbeitung des Formulars. Sie wählt im Dropdown-Menü Bedienfeldlayout die Option Stammbereich > Bearbeiten (der Schraubenschlüssel) > in der Registerkarten oben aus und markiert das Kontrollkästchen.

   ![Eigenschaften überprüfen](assets/aftia-review-properties.jpg)

1. Camilla fügt dann alle notwendigen CSS- und Feldänderungen hinzu, um das Endprodukt zu produzieren.

   ![CSS hinzufügen](assets/aftia-add-css.jpg)

### Formulardatenmodell und Datenquellen (Camila) {#data-sources}

**Dieser Abschnitt**: Nachdem das Dokument konvertiert und in einem adaptiven Formular erstellt wurde, muss Camila das adaptive Formular mit einer Datenquelle verbinden.

1. Camila öffnet die Eigenschaften für das Formular, das in [automatische Formular-Konvertierung - We.Gov](#automated-forms-conversion-wegov) konvertiert wurde.

1. Camila wählt dann Formularmodell > Wählt das Formulardatenmodell aus dem Dropdown-Menü > Wählt We.gov Enrollment FDM aus der Liste der Optionen aus.

1. Sie klickt auf die Schaltfläche Speichern und Schließen.

   ![FDM-Auswahl](assets/aftia-select-fdm.jpg)

1. Camila klickt auf den **Ausgabe**-Ordner, wählt das adaptive Formular aus und klickt auf **Bearbeiten**, um das ausgefüllte We.Gov-Formular zu öffnen.
1. Camila wählt ein Feld im adaptiven Formular aus und klickt auf ![Symbol konfigurieren](assets/configure-icon.svg). Sie erstellt eine Bindung mit den Entitäten des Formulardatenmodells mithilfe des **Bindungsverweis**-Felds. Sie wiederholt diesen Schritt für alle Felder im adaptiven Formular.

### Prüfung der Barrierefreiheit von Formularen (Camila) {#form-accessibility-testing}

Camila überprüft auch, ob die erstellten Inhalte korrekt erstellt wurden und gemäß den Unternehmensstandards vollständig zugänglich sind.

1. Camila klickt auf den **Ausgabe**-Ordner, wählt das adaptive Formular aus und klickt auf **Vorschau**, um das ausgefüllte We.Gov-Formular zu öffnen.

1. Sie öffnet die Registerkarte Audit im Chrome Developer Tool.

1. Sie führt eine Barrierefreiheitsprüfung durch, um das adaptive Formular zu überprüfen.

   ![Prüfung der Zugänglichkeit](assets/aftia-accessibility.jpg)

## Demo zur mobilen Ansicht des adaptiven Formulars (Aya) {#mobile-view-demo}

**Dieser Abschnitt muss vor der Demonstration durchgeführt werden.**

**Benutzeranweisungen:**

1. Navigieren Sie zu: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Anmelden mit:

   1. **Benutzer**: aya.tan
   1. **Kennwort:** password

1. Ändern Sie die Größe des Browser-Fensters oder verwenden Sie den Emulator des Browsers, um eine Mobilgerätegröße zu replizieren.

### We.Gov-Website (Aya) {#aya-user-story-we-gov-website}

![Fiktiver Benutzer](/help/forms/using/assets/aya_tan_new-1.png)

**Dieser Abschnitt**: Aya ist eine Bürgerin. Sie hört von einer Freundin, dass sie möglicherweise berechtigt ist, einen Dienst von einer Regierungsstelle zu erhalten. Aya navigiert von ihrem Mobiltelefon zur We.Gov-Website, um mehr über Dienste zu erfahren, für die sie berechtigt ist.

### We.Gov Pre-Screener (Aya) {#aya-user-story-we-gov-pre-screener}

Aya beantwortet einige Fragen, um ihre Eignung zu bestätigen, indem sie ein kurzes adaptives Formular auf ihrem Mobiltelefon ausfüllt.

**Benutzeranweisungen:**

1. Treffen Sie in jedem Dropdown-Feld eine Auswahl.

   >[!NOTE]
   >
   >Wenn der Benutzer mehr als 200.000 USD pro Jahr verdient, ist er nicht berechtigt.

1. Klicken Sie auf &quot;**Bin ich berechtigt?**&quot; Schaltfläche.
1. Klicken Sie auf &quot;**Jetzt anwenden**&quot;, um fortzufahren.

   ![Jetzt anwenden](/help/forms/using/assets/apply_now_link.png)

### Adaptives Formular von We.Gov (Aya) {#aya-user-story-we-gov-adaptive-form}

Aya stellt fest, dass sie berechtigt ist, und beginnt mit dem Ausfüllen ihres Antrags auf ihrem Mobilgerät, um einen Service anzufordern.

Aya muss einige Dokumente zu Hause überprüfen, bevor sie den Antrag auf die Service-Anfrage ausführen kann. Sie speichert und beendet das Programm auf ihrem mobilen Gerät.

**Benutzeranweisungen:**

1. Füllen Sie die Felder „Grundlegende Informationen“ aus. Die folgenden Felder und Dropdown-Listen sind obligatorisch:

   1. Grundlegende Informationen

      1. Vorname
      1. Nachname
      1. Geburtsdatum
      1. E-Mail

1. Verwenden Sie die folgende **dynamische Logik**, um die dynamische Funktion mithilfe der Dropdown-Liste **Familienstatus** zu demonstrieren:

   1. **Einzel**: Bedienfeld für nächste Angehörige anzeigen
   1. **Verheiratet**: Bedienfeld für ehelich abhängige Personen anzeigen
   1. **Geschieden**: Bedienfeld für nächste Angehörige anzeigen
   1. **Verwitwet**: Bedienfeld für nächste Angehörige anzeigen
   1. **Haben Sie Kinder?**: (Ja/Nein) Optionsfeld für die Anzeige des Bedienfelds für unterhaltsberechtigte Kinder.

      1. (Hinzufügen/Entfernen)-Schaltfläche zum Hinzufügen/Entfernen mehrerer Bedienfelder für unterhaltsberechtigte Kinder.

1. Klicken Sie in der grauen Menüleiste auf den Pfeil nach rechts.
1. Klicken Sie unten auf die Schaltfläche „Speichern“.

   ![Details von adaptiven Formularen](/help/forms/using/assets/adaptive_form.png)

## Desktop-Demo {#desktop-demo}

**Dieser Abschnitt**: Zurück zu Hause hat Aya die benötigten Informationen gefunden und setzt das Programm von ihrem Desktop aus fort. Aya navigiert zum Online-Formularportal, um ihren Antrag wiederaufzunehmen. Mit einer einfachen Anpassung können Agenturen auch automatisch einen Link generieren und per E-Mail versenden, um das Programm wiederaufzunehmen.

### Fortsetzung des adaptiven Formulars (Aya) {#aya-user-story-continued-adaptive-form}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Klicken Sie in der Navigationsleiste auf &quot;**Online-Dienste**&quot;.
1. Wählen Sie im Bedienfeld &quot;Forms-Entwurf&quot;die vorhandene &quot;Registrierungsanwendung für Gesundheitsvorteile&quot;aus.

   ![Registrierungsantrag für Gesundheitsleistungen](/help/forms/using/assets/enrollment_application.png)

   Das Erscheinungsbild ist identisch, und sie muss keine Daten erneut eingeben.

   **Benutzeranweisungen:**

1. Klicken Sie auf den CTA im rechten Kreis, um zum nächsten Abschnitt zu wechseln.

   ![CTA im rechten Kreis](/help/forms/using/assets/right_circle_cta_new.png)

   Das Formular wird bis zum letzten Eintrag von Aya vorausgefüllt. Aya hat alle ihre Informationen eingegeben und ist bereit zum Senden.

   ![Senden des adaptiven Formulars](/help/forms/using/assets/submit_adaptive_form.png)

   >[!NOTE]
   >
   >Wenn Aya das Telefonnummernfeld ausfüllt, muss sie die Nummer als fortlaufende 11-stellige Zahl ohne Leerzeichen oder Bindestriche angeben.

   Nach dem Senden erhält Aya eine Dankeseite. Optional erhält sie auch eine E-Mail, die sie zur elektronischen Unterzeichnung des Datensatzdokuments mit Adobe Sign öffnen kann.

### Optional: Adobe Sign (Aya) {#adobe-sign}

**Benutzeranweisungen:**

1. Navigieren Sie zu Ihrem E-Mail-Client und suchen Sie die E-Mail von Adobe Sign.
1. Klicken Sie auf den Link zu Adobe Sign.

   ![Link zu Adobe Sign](/help/forms/using/assets/adobe_sign_link.png)

**Benutzeranweisungen:**

1. Überprüfen Sie die **Ich stimme zu**&quot;.
1. Klicken Sie auf &quot;**Accept**&quot;.
1. Blättern Sie bis zum Ende des überprüften Dokuments.
1. Klicken Sie auf die gelb markierte Registerkarte, um das Dokument zu unterzeichnen.

   ![Dokument unterschreiben](/help/forms/using/assets/sign_document_new.png) ![Testdokument unterschreiben](/help/forms/using/assets/sign_test_document.png)

## Regierungsbeamter (George) {#government-agent-george}

![Regierungsbeamter George](/help/forms/using/assets/george_lang-1.png)

**Dieser Abschnitt:** George ist ein Unternehmensanalyst bei der Regierungsbehörde, bei der Aya eine Dienstleistung beantragt. George hat ein einzelnes Dashboard, in dem er alle Anträge auf Serviceleistungen sehen kann, die ihm zur Überprüfung zugewiesen wurden.

### AEM-Posteingang (George) {#george-user-story-aem-inbox}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klicken Sie auf das Benutzersymbol (oben rechts) und verwenden Sie die **Abmelden**&quot; oder &quot;**Identität annehmen als**&quot;, wenn Sie derzeit mit einem Administrator angemeldet sind.

   1. Anmelden mit:

      1. **Benutzer:** george.lang
      1. **Kennwort:** password
   1. Oder stellvertretend agieren:

      1. Typ &quot;**George**&quot; in der &quot;**Identität annehmen als**&quot;.

      1. Klicken Sie auf „OK“, um stellvertretend zu agieren.


1. Klicken Sie oben rechts auf das Symbol „Benachrichtigung“ (Glocke).
1. Klicken Sie auf &quot;**Alle anzeigen**&quot;, um zum Posteingang zu navigieren.
1. Öffnen Sie im Posteingang die neueste **Antragsüberprüfung für gesundheitliche Vorteile**&quot;.

   ![Überprüfung des Antrags auf Gesundheitsleistungen](/help/forms/using/assets/health_benefits.png)

### Optional: AEM-Posteingang &amp; MS Dynamics (George) {#george-user-story-aem-inbox-and-ms-dynamics}

Dank der Datenintegration und der automatisierten Workflows wird der Antrag von Aya zusammen mit einem CRM-Datensatz angezeigt, der bei der Übermittlung der Daten automatisch erstellt wurde.

**Benutzeranweisungen:**

1. Öffnen Sie das schreibgeschützte adaptive Formular und prüfen Sie es.
1. Klicken Sie auf &quot;**Open MS Dynamics**&quot;-Schaltfläche, um den MS Dynamics-Datensatz in einem neuen Fenster zu öffnen.
1. Im CRM können Sie sehen, dass alle Informationen aktualisiert werden können

   1. Optional können Sie einige Prüfungsnotizen direkt in Dynamics hinzufügen.

1. Schließen Sie es und kehren Sie zum AEM-Posteingang zurück.

   ![MS Dynamics-Datensatz](/help/forms/using/assets/ms_dynamics.png)

### Zurück zum AEM-Posteingang (George) {#george-user-story-back-to-aem-inbox}

George genehmigt Ayas Antrag, und dank eines bestehenden automatisierten Workflows wird auch eine Bestätigungs-E-Mail an Aya gesendet.

**Benutzeranweisungen:**

1. Navigieren Sie zur oberen linken Ecke und klicken Sie auf &quot;**Genehmigen**&quot;, um den Antrag zu genehmigen.
1. In dem Modal können Sie eine Nachricht für den CX-Lead hinterlassen.
1. Klicken Sie auf Fertig.
1. (Bürgerrolle) Öffnen Sie Ihren E-Mail-Client, um die an Aya gesendete E-Mail anzuzeigen.

   ![Anzeigen der an Aya gesendeten E-Mail](/help/forms/using/assets/email_client.png)

## CX-Lead (Camila) {#cx-lead-camila}

![Camila (CX-Lead)](/help/forms/using/assets/camila_santos-1.png)

**Dieser Abschnitt:** Camila, der CX-Lead, führt ein Begrüßungstelefonat mit Aya, um ihr zu erklären, wie sie die staatlichen Dienstleistungen nutzen kann, die ihr genehmigt wurden.

### (Optional) AEM-Posteingang &amp; MS Dynamics {#camila-user-story-aem-inbox-ms-dynamics}

**Benutzeranweisungen:**

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klicken Sie auf das Benutzersymbol (oben rechts) und verwenden Sie die **Abmelden**&quot; oder &quot;**Identität annehmen als**&quot;, wenn Sie derzeit mit einem Administrator angemeldet sind.

   1. Anmelden mit:

      1. **Benutzer**: camila.santos
      1. **Kennwort:** password
   1. Oder stellvertretend agieren:

      1. Typ &quot;**Camila**&quot; in der &quot;**Identität annehmen als**&quot;.

      1. Klicken Sie auf „OK“, um stellvertretend zu agieren.


1. Klicken Sie oben rechts auf das Symbol „Benachrichtigung“ (Glocke).
1. Klicken Sie auf &quot;**Alle anzeigen**&quot;, um zum Posteingang zu navigieren.
1. Öffnen Sie im Posteingang die neueste **Neue Kontaktgenehmigung**&quot;.

![Neue Kontaktgenehmigung](/help/forms/using/assets/new_contact_approval.png)

**(Optional) Benutzeranweisungen:**

1. Öffnen Sie das schreibgeschützte adaptive Formular und prüfen Sie es.
1. Klicken Sie auf &quot;**Open MS Dynamics**&quot;-Schaltfläche, um den MS Dynamics-Datensatz in einem neuen Fenster zu öffnen.
1. Im CRM können Sie sehen, dass alle Informationen aktualisiert werden können

   1. Fügen Sie optional eine neue Aufruffaktivität direkt in Dynamics hinzu.
   1. Öffnen Sie &quot;**Tätigkeiten**&quot;.
   1. Klicken Sie auf &quot;**Neuer Telefonaufruf**&quot;.
   1. Fügen Sie Telefonanrufdetails hinzu.
   1. Speichern und schließen Sie das Fenster.

1. Navigieren Sie in AEM oberen linken Ecke zu und klicken Sie auf &quot;**Einsenden**&quot;, um den Antrag zu übermitteln.
1. Im Modal können Sie eine Nachricht hinterlassen.
1. Klicken Sie auf Fertig.

   ![Registerkarte Aktivitäten](/help/forms/using/assets/activities_tab.png) ![Neuen Kontakt bestätigen](/help/forms/using/assets/confirm_new_contact.png)

## (Optional) Willkommenspaket Bürgerin (Aya) {#welcome-kit-citizen-aya}

**Dieser Abschnitt:** Aya erhält eine E-Mail mit einem Link zu einer interaktiven Mitteilung, in der ihre Leistungen zusammengefasst sind und die auch Formularfelder zum Ausfüllen enthält. Mit einer beigefügten PDF-Leistungsübersicht und einem Link zur interaktiven Mitteilung, die per Post verschickt wird (mit demselben Thema/Branding wie die interaktive Mitteilung).

### E-Mail-Client-Benachrichtigung (Aya) {#aya-user-story-email-client}

**Benutzeranweisungen:**

1. Suchen und öffnen Sie die E-Mail mit dem Willkommenspaket.
1. Scrollen Sie zur PDF-Anlage am Seitenende.
1. Klicken Sie darauf, um die PDF-Anlage zu öffnen.
1. Scrollen Sie in Ihrem E-Mail-Client nach oben und klicken Sie auf &quot;**Willkommenskit online anzeigen**&quot;.

   1. Dadurch wird die Webkanalversion desselben Dokuments geöffnet.

1. Für einen Kurzverweis direkt auf das PDF:

   *https://&lt;aemserver>:&lt;port>/aem/formdetails.html/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook*

1. Für einen Kurzverweis direkt auf IC:

   *https://&lt;aemserver>:&lt;port>/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook/jcr:content?channel=web&amp;mode=preview&amp;wcmmode=disabled*

   ![Handbuch der Willkommensvorteile](/help/forms/using/assets/welcome_benefits_handbook.png) ![Interaktive Kommunikationsverbindung](/help/forms/using/assets/interactive_communication.png)

## Verlängerungserinnerung Bürgerin (Aya) {#renewal-reminder-citizen-aya}

**Dieser Abschnitt:** Camila plant auch eine Erinnerungsmitteilung für ein Jahr später. (Workflow-Schritt, der automatisiert/ausgeführt wird und E-Mail).

### E-Mail-Client-Benachrichtigung (Aya) {#aya-user-story-email-client-updated}

**Benutzeranweisungen:**

1. Navigieren Sie zu Ihrem E-Mail-Client.
1. Suchen und öffnen Sie die E-Mail mit der Verlängerungserinnerung.
1. Klicken Sie auf &quot;**Neue Anwendung einreichen**&quot;, um das adaptive Formular zu öffnen.

   1. Dieser Abschnitt ist absichtlich leer gelassen, um die Datenvorerfassung in Phase 2 zu unterstützen.

   ![Verlängerungserinnerungs-E-Mail](/help/forms/using/assets/renewal_reminder_email.png)

## (Optional) Formulardatenmodell (Camila) {#form-data-model}

**Dieser Abschnitt**: Camila navigiert zu AEM Forms Data Integrations, wo sie einen schnellen Test durchführen kann, um zu sehen, ob die Informationen, die über die Formulardatenmodellintegration an die externe Datenquelle gesendet werden, tatsächlich vorhanden sind.

### Formulardatenmodell (Camila) {#form-data-model-camila}

**Dieser Abschnitt**: Camila navigiert zur Seite „Datenquellen“, um die Daten zu überprüfen, die der Server in der Derby-Datenbank repliziert hat.

1. Sobald das Benutzererlebnis abgeschlossen ist und die Benutzereingabe abgeschlossen wurde, navigiert Camila zur Registerkarte „Datenquellen“ in AEM Forms (**Formulare** > **Datenintegrationen**)

1. Camila wählt dann AEM Forms aus **We.gov FDM** und bearbeitet dann die **We.gov-Registrierungs-FDM**.

1. Camila wählt dann den zu testenden **Kontakt** > **Dienst auslesen** aus.

   ![Kontakt Lesedienst](assets/aftia-contact-read-service.jpg)

1. Camila gibt dem Testdienst eine Kontakt-ID und klickt dann auf die Schaltfläche „Test“. Zum Beispiel 1 oder 2, wenn Sie das Formular abgeschickt haben. Wenn Sie das Formular nicht gesendet haben, werden keine Daten zurückgegeben.

   ![Kontaktieren des Lese-Services](assets/aftia-test-service.jpg)

1. Camila kann dann überprüfen, ob die Daten erfolgreich in die Datenquelle eingefügt wurden.

   * Die Daten im Derby DS ähneln dem folgenden Format:

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

**Dieser Abschnitt**: Camila navigiert zu einem Dashboard, in dem sie die KPIs der Agentur sehen kann, z. B. die Prozentzahl der Bürger, die mit dem Ausfüllen eines Antragsformulars für den Service begonnen und den Vorgang abgebrochen haben, die durchschnittliche Zeitdauer von der Antragseinsendung bis zur Genehmigung/Ablehnung und Interaktionsstatistiken für die Nutzenhandbücher, die sie an Bürger gesendet hat.

### Sites-Reporting mit Adobe Analytics (Camila) {#camila-reviews-sites-reporting-we-gov-adobe-analytics}

1. Navigieren Sie zu *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Wählen Sie &quot;**AEM Forms We.Gov-Site**&quot;, um die Seiten der Site anzuzeigen.
1. Wählen Sie eine der Seiten der Site aus (z. B. Startseite) und wählen Sie &quot;**Analytics und Recommendations**&quot;.

   ![Analysen und Empfehlungen](/help/forms/using/assets/analytics_recommendation.jpg)

1. Auf dieser Seite werden abgerufene Informationen aus Adobe Analytics angezeigt, die sich auf die AEM Sites-Seite beziehen (HINWEIS: Diese Informationen werden regelmäßig von Adobe Analytics aktualisiert und nicht in Echtzeit angezeigt).

   ![Schlüsselmetriken von Adobe Analytics](/help/forms/using/assets/analytics_key_metrics.jpg)

1. Zurück auf der Seitenansichtsseite (Zugriff in Schritt 3) können Sie die Seitenansichtsinformationen auch anzeigen, indem Sie die Anzeigeeinstellung ändern und Elemente in der **Listenansicht**&quot;.
1. Suchen Sie nach &quot;**Ansicht**&quot;Dropdown-Menü und wählen Sie &quot;**Listenansicht**&quot;.

   ![Listenansicht im Dropdown-Menü „Ansicht“](/help/forms/using/assets/list_view_view_dropdown.jpg)

1. Wählen Sie im selben Menü &quot;**Anzeigeeinstellung**&quot; und wählen Sie die Spalten aus, die Sie anzeigen möchten.**Analytics**&quot;.

   ![Konfigurieren der Spaltenanzeige](/help/forms/using/assets/view_setting_analytics.jpg)

1. Klicken Sie auf &quot;**Aktualisieren**&quot;, um die neuen Spalten verfügbar zu machen.

   ![Verfügbar machen neuer Spalten](/help/forms/using/assets/new_columns_available.jpg)

### Forms-Reporting mit Adobe Analytics (Camila) {#camila-reviews-forms-reporting-we-gov-adobe-analytics}

1. Gehen Sie zu

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Wählen Sie &quot;**Registrierungsantrag für Gesundheitsleistungen**&quot;adaptives Formular&quot;und wählen Sie die **Analytics-Bericht**&quot;.

   ![Registrierungsantrag für Gesundheitsleistungen](/help/forms/using/assets/analytics_report_benefits.jpg)

1. Warten Sie, bis die Seite geladen wurde, und zeigen Sie die Daten des Analytics-Berichts an.

   ![Daten des Analytics-Berichts](/help/forms/using/assets/analytics_report_data_updated.jpg)
