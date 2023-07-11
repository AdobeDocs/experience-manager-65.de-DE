---
title: Schrittweise Anleitung zum Einrichten einer Referenz-Website für Mitarbeiterrekrutierung
description: Auf der AEM Forms-Referenz-Website wird erläutert, wie Unternehmen AEM Forms-Funktionen zur Implementierung eines Workflows für die Mitarbeiterrekrutierung verwenden können.
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: bdfc0a20-1e98-47f9-a1d1-5af5b3ef15db
source-git-commit: b9c164321baa3ed82ae87a97a325fcf0ad2f6ca0
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 20%

---

# Schrittweise Anleitung zum Einrichten einer Referenz-Website für Mitarbeiterrekrutierung {#employee-recruitment-reference-site-walkthrough}

## Übersicht {#overview}

We.Finance ist eine Organisation, die es Bewerbern ermöglicht, sich über das Referenz-Website-Portal um eine Stelle zu bewerben. Die Organisation nutzt das Portal auch, um die Termine für Vorstellungsgespräche, die Liste der engeren Auswahl und die interne Kommunikation zu verwalten. Die Site verwaltet Folgendes:

* Bewerber, die nach Arbeitsplätzen suchen und sich bewerben
* Auswahl der Kandidaten
* Ablauf der Vorstellungsgespräche 
* Sammlung von Kandidatendetails
* Hintergrundprüfung der Kandidaten
* Rollout von Angeboten für ausgewählte Bewerber

>[!NOTE]
>
>Anwendungsfälle für die Mitarbeiterrekrutierung sind sowohl auf We.Finance- als auch auf We.Gov-Referenzseiten verfügbar. Die in den exemplarischen Vorgehensweisen verwendeten Beispiele, Bilder und Beschreibungen verwenden die We.Finance-Referenz-Website. Sie können diese Anwendungsfälle jedoch auch ausführen und Artefakte mit We.Gov überprüfen. Ersetzen Sie dazu **we-finance** mit **we-gov** in den genannten URLs.

### Beteiligte Workflow-Modelle {#workflow-models-involved}

Der Anwendungsfall der Mitarbeiterrekrutierung umfasst zwei Workflows:

* Vor dem Vorstellungsgespräch – Workflow „We Finance-Mitarbeiterrekrutierung“
* Nach dem Vorstellungsgespräch – Workflow „We Finance-Mitarbeiterrekrutierung nach dem Vorstellungsgespräch“

Diese Workflows werden in AEM erstellt und sind verfügbar unter:

`https://[authorHost]:[authorPort]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models/`

#### Workflow zur Mitarbeiterrekrutierung für We Finance {#we-finance-employee-recruiting-workflow}

Im Folgenden finden Sie das Modell des Workflows We Finance-Mitarbeiterrekrutierung , der in diesem Dokument verwendet wird.

![we-finance-employee-recruiting-workflow](assets/we-finance-employee-recruiting-workflow.png)

#### Workflow &quot;We Finance-Mitarbeiterrekrutierung nach dem Interview&quot; {#we-finance-employee-recruiting-post-interview-workflow}

Im Folgenden finden Sie das Modell des Workflows We Finance Employee Post Interview Recruiting , der in diesem Dokument folgt.

![we-finance-employee-recruiting-post-interview-workflow](assets/we-finance-employee-recruiting-post-interview-workflow.png)

### Personas {#personas}

Das Szenario schließt folgende Personen ein:

* Sarah Rose, die Antragstellerin, die eine Stelle in der Organisation beantragt
* John Jacobs, Rekrutierer
* Gloria Rios, Personalverantwortliche
* John Doe, HR-Mitarbeiter

## Sarah beantragt eine Stelle {#sarah-applies-for-a-job}

Sarah Rose sucht nach einer Jobmöglichkeit in der Organisation. Sie besucht ihr Webportal und erkundet die Stellenangebote auf der Karriereseite. Sie findet eine passende Stellenausschreibung und beantragt sie.

![home-page](assets/home-page.png)

Startseite von We.Finance

![career-page](assets/career-page.png)

We.Finance-Karriereseite

Sarah klickt auf Beantragen bei einer Stellenausschreibung. Das Bewerbungsformular wird geöffnet. Sie füllt alle Details des Antrags aus und sendet ihn.

![job-application-form](assets/job-application-form.png)

### Funktionsweise {#how-it-works}

Die Startseite von We.Finance und die Jobseite sind AEM Sites-Seiten. Die Karriereseite bettet ein adaptives Formular ein, das mithilfe eines wiederholbaren Bereichs Stellenangebote mithilfe eines Dienstes abruft und auf der Seite auflistet. Sie können das adaptive Formular unter `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/recruitment/jobs.html` überprüfen.

### Sehen Sie selbst {#see-it-yourself}

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en.html` und klicken Sie auf **[!UICONTROL Career]** (Jobs). Klicken **[!UICONTROL Suche]** , sodass Sie die Auftragsliste ausfüllen, und klicken Sie auf **[!UICONTROL Anwenden]** für einen Job. Füllen Sie das Formular aus und reichen Sie den Antrag ein.

Stellen Sie sicher, dass Sie eine gültige E-Mail-ID in der Anwendung angeben, da jede Kommunikation im Rahmen dieser exemplarischen Vorgehensweise an die angegebene E-Mail-ID gesendet wird.

## John Jacobs wählt Sarah Roses Profil für das Screening des Personalverantwortlichen aus {#john-jacobs-shortlists-sarah-rose-s-profile-for-the-hiring-manager-s-screening}

Das Unternehmen erhält den von Sarah eingereichten Bewerbungsantrag. John Jacobs, ein Rekrutierer, wird die Aufgabe zugewiesen, Sarahs Profil zu überprüfen. John überprüft die Aufgabe in seinem AEM Posteingang, findet das Profil, das der Auftragsanforderung entspricht, und klickt auf &quot;Shortlist&quot;. Sarahs Profil wird zur Genehmigung an Gloria Rios, die Personalverantwortliche, weitergeleitet.

![jjacobs-inbox-1](assets/jjacobs-inbox-1.png)

Johns AEM-Posteingang

![candidate-shortlist](assets/candidate-shortlist.png)

John Jacobs wählt Sarah Roses Profil für das Screening des Personalverantwortlichen aus

**Funktionsweise**

Die Übermittlungsaktion im Antragsformular &quot;Auftrag&quot;Trigger einen Workflow, der eine Aufgabe im Posteingang von John Jacob erstellt, um den Antrag zu prüfen. Wenn John den Antrag prüft und in die engere Wahl kommt, erstellt der Workflow eine Aufgabe im Posteingang von Gloria, dem Personalverantwortlichen.

### Sehen Sie selbst {#see-it-yourself-1}

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` und melden Sie sich mit „jjacobs“ und „password“ als Benutzername/Kennwort für John Jacobs an. Öffnen Sie die Aufgabe zur Überprüfung des Bewerberprofils und nehmen Sie den Bewerber in die Vorauswahl auf.

## Gloria prüft den Antrag und genehmigt den Antragsteller für ein Gespräch {#gloria-reviews-the-application-and-approves-the-applicant-for-an-interview}

Gloria, die Personalverantwortliche, erhält das in die engere Wahl kommende Profil als Aufgabe in ihrem AEM Posteingang. Sie überprüft es und genehmigt die Kandidatin, Sarah Rose, für das Interview.

![gloriainbox](assets/gloriainbox.png)

Glorias AEM Posteingang

![gloriaschedulesinterview](assets/gloriaschedulesinterview.png)

Gloria genehmigt Sarah Rose für ein Interview

**Funktionsweise**

Wenn Gloria den Kandidaten für ein Interview genehmigt, erstellt der Workflow eine Aufgabe im AEM Posteingang von John Doe, der ein Rekrutierer für We.Finance ist.

### Sehen Sie selbst {#see-it-yourself-2}

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` und melden Sie sich mit „jjacobs“ und „password“ als Benutzername/Kennwort für John Jacobs an. Öffnen Sie die Aufgabe zur Überprüfung des Bewerberprofils und nehmen Sie den Bewerber in die Vorauswahl auf.

Navigieren Sie zu `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` und melden Sie sich mit „grios“ und „password“ als Benutzername/Kennwort für Gloria Rios an. Öffnen Sie die Aufgabe Profilprüfung für Kandidaten und klicken Sie auf Interview planen .

## John Doe plant ein Interview {#john-doe-schedules-an-interview}

John Doe erhält die Aufgabe, ein Interview in seinem Posteingang zu planen. John Doe wählt die Aufgabe aus und öffnet sie und setzt Datum und Uhrzeit, Ort und den für das Interview verantwortlichen HR-Mitarbeiter als John Jacob fest. John Doe klickt auf Einladungs-E-Mail senden . Sarah wird eine E-Mail gesendet und Gloria, der Personalverantwortlichen, wird eine Aufgabe zugewiesen, um Sarah zu interviewen.

![johnjacobsaeminbox](assets/johnjacobsaeminbox.png)

John Does AEM-Posteingang

![johndoescheduleinterview](assets/johndoescheduleinterview.png)

John Doe plant das Interview und sendet die Details an Sarah Rose

## Sarah Rose erhält die E-Mail mit dem Zeitplan für das Vorstellungsgespräch {#sarah-rose-receives-the-email-with-interview-schedule}

Sarah Rose erhält die E-Mail mit Interviewplan, Veranstaltungsort und anderen Details. Sarah klickt auf Annehmen , um anzugeben, dass sie mit dem Zeitplan und dem Ort des Vorstellungsgesprächs einverstanden ist. Anhand der genauen Informationen gelangt Sarah zu den Interviews.

![sarahroseinterviewemail](assets/sarahroseinterviewemail.png)

Sarah Rose erhält den Zeitplan für das Vorstellungsgespräch

## Nach den Interviews wählt die Personalverantwortliche Sarah Rose aus. {#after-the-interviews-the-hiring-manager-shortlists-sarah-rose}

Nachdem Sarah Rose die Interviews durchläuft und sie gelöscht hat, öffnet Gloria Rios, die Personalverantwortliche, die Aufgabe zur Auswahl von Kandidaten aus ihrem Posteingang und klickt auf Auswählen . Gloria Rios Entscheidung wird dem HR-Mitarbeiter John Doe zur weiteren Bearbeitung übermittelt.

![gloriariosinboxoffer](assets/gloriariosinboxoffer.png)

Glorias AEM Posteingang

![gloriariosselectcandidate](assets/gloriariosselectcandidate.png)

Gloria Rios wählt Sarah Rose nach den Interviews aus

## John Doe fordert weitere Informationen an {#john-doe-requests-more-information}

Bevor Sie einen Kandidaten auffordern, der Organisation beizutreten, muss Sarahs Hintergrund überprüft werden. John Doe öffnet und überprüft die Details des ausgewählten Antragstellers und stellt fest, dass einige ihrer Beschäftigungs- und Bildungsdetails noch nicht ausgefüllt sind. John Doe klickt auf &quot;Weitere Informationen benötigen&quot;.

![johndoeinbox](assets/johndoeinbox.png) ![johndoeneedmoreinformation](assets/johndoeneedmoreinformation.png)

John Doe fordert weitere Informationen von Sarah Rose über ihre Ausbildung und Berufserfahrung an

## Sarah Rose erhält eine E-Mail mit der Aufforderung zu weiteren Informationen {#sarah-rose-receives-an-email-requesting-further-information}

Sarah Rose erhält eine E-Mail, in der sie darüber informiert wird, dass weitere Informationen zur Bearbeitung ihres Antrags auf Erwerbstätigkeit erforderlich sind. Die E-Mail enthält einen Link zum Formular zum Ausfüllen der erforderlichen Informationen.

![sarahroseemailmoredetails](assets/sarahroseemailmoredetails.png)

Sarah Rose erhält eine E-Mail, in der sie darauf hingewiesen wird, dass für die Bearbeitung ihres Arbeitsantrags weitere Informationen erforderlich sind

Sarah klickt in der E-Mail auf den Link Details angeben . Ein Formular wird angezeigt. Sarah füllt die von John Doe geforderten Angaben zu Ausbildung und Beschäftigung aus und klickt auf &quot;Senden&quot;.

![additionalinformation1](assets/additionalinformation1.png)

Sarah öffnet das Formular für zusätzliche Informationen, indem sie auf den Link in der E-Mail klickt.

![additionalinformation2](assets/additionalinformation2.png)

Sarah füllt zusätzliche Informationen aus, wie von John Doe angefordert, und klickt auf &quot;Senden&quot;

## John Doe überprüft das ausgewählte Bewerberprofil auf die zusätzlichen Informationen, die bereitgestellt werden {#john-doe-reviews-the-selected-candidate-profile-for-the-additional-information-provided}

John Doe wählt die Kandidatenüberprüfungsanforderung aus und öffnet sie. John Doe stellt fest, dass Sarah alle erforderlichen Informationen ausgefüllt hat. Nach Überprüfung des Antrags klickt John Doe auf Genehmigen. Nach Genehmigung durch John Doe wird die Anfrage, eine Hintergrundprüfung an Sarah Rose durchzuführen, an John Jacobs weitergeleitet.

![johndoeadditionainformationinbox](assets/johndoeadditionainformationinbox.png)

John Does AEM-Posteingang

![johndoeadditionalinformationreview-copy](assets/johndoeadditionalinformationreview-copy.png)

John Doe prüft die von Sarah bereitgestellten zusätzlichen Informationen und genehmigt sie

## John Jacobs erhält eine Hintergrundprüfungsanforderung {#john-jacobs-receives-a-background-check-request}

John Jacobs sieht die Hintergrundprüfungsanforderung in seinem Posteingang. John Jacobs öffnet die Aufgabe und überprüft die von Sarah Rose bereitgestellten Informationen. Nach einer Hintergrundprüfung klickt John Jacobs auf &quot;Go Ahead&quot;, um anzuzeigen, dass die Hintergrundprüfung erfolgreich war.

![johnjacobsbackgroundcheckinbox](assets/johnjacobsbackgroundcheckinbox.png)

John Jacobs AEM Posteingang

![johnjacobsbackgroundcheckgoahead](assets/johnjacobsbackgroundcheckgoahead.png)

Nach der Hintergrundprüfung klickt John Jacobs auf &quot;Go Ahead&quot;

## John Doe sendet das Anstellungsschreiben an Sarah Rose {#john-doe-sends-out-the-joining-letter-to-sarah-rose}

John Doe erhält in seinem AEM Posteingang eine Anfrage zum Senden des Anstellungsschreibens. John öffnet die Anfrage und zeigt die Details an. John Doe hängt den Anstellungsbrief PDF an und klickt dann auf &quot;Attach &amp; Send Joining Letter&quot;.

![johndoejoiningletterinbox](assets/johndoejoiningletterinbox.png)

John Does AEM-Posteingang

![johndoejoiningletterattachandsend](assets/johndoejoiningletterattachandsend.png)

John Doe sendet das Anstellungsschreiben zum Unterschreiben aus

## Sarah Rose erhält und unterzeichnet das Anstellungsschreiben {#sarah-rose-receives-and-signs-the-joining-letter}

Sarah Rose erhält das Anstellungsschreiben zur Unterschrift. Sarah klickt auf „Click Here To Review And Sign Joining Letter“ (Hier klicken, um Anstellungsschreiben anzuzeigen und zu unterschreiben). Die PDF-Datei mit dem Anstellungsschreiben wird geöffnet und enthält ein Feld für die Unterschrift.

![sarahrosejoiningletteremail](assets/sarahrosejoiningletteremail.png)

Sarah Rose erhält das Anstellungsschreiben zur Unterschrift

Sarah kann entweder eintippen, Zeichnen zum Schreiben verwenden, ein Bild der Signatur einfügen oder den Touchscreen ihres Mobiltelefons verwenden, um ihre Signatur zu zeichnen. Sarah gibt ihren Namen ein, klickt auf &quot;Click To Sign&quot;und lädt die signierte Kopie des Anstellungsschreibens herunter.

![sarahrosejoininglettersign](assets/sarahrosejoininglettersign.png)

Sarah tippt ihren Namen ein, um das Anstellungsschreiben zu unterzeichnen

![sarahrosejoininglettersign2](assets/sarahrosejoininglettersign2.png)

Sarah klickt auf „Click To Sign“, um die Unterzeichnung des Anstellungsschreibens abzuschließen
