---
title: Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance
seo-title: Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance
description: Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance
uuid: c749a6f7-71f1-4f47-b824-9c7b699072c7
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
discoiquuid: ad450124-49a5-4afb-aac3-ed3733d6504b
docset: aem65
exl-id: b6ded6ac-4fb1-49f9-b272-16774c3e89a3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 38%

---

# Anleitung zur Erneuerung der Kfz-Versicherung auf der Referenz-Site von We.Finance{#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## Szenario für We.Finance-Referenz-Site  {#we-finance-reference-site-scenario}

Die Website We.Finance ist eine Website für Finanzdienstleistungen, die Ihnen dabei hilft, die interaktiven Kommunikationsfunktionen von AEM Forms zu erlernen.

Lesen Sie die ausführliche exemplarische Vorgehensweise des We.Finance Auto Insurance-Anwendungsbeispiels, in dem erläutert wird, wie AEM Formulare und ihre Integration mit Microsoft Dynamics zur Personalisierung des Kundenerlebnisses in einem Finanzdienstleistungsunternehmen beitragen. Die interaktive exemplarische Vorgehensweise soll die Implementierung komplexer digitaler Transaktionen und die Kundenkommunikation in einem Finanzunternehmen erleichtern.

**Das Ganze beginnt mit dem Benutzerszenario:** 

Sarah Rose ist bereits We.Finance-Kundin und hat eine Kfz-Versicherungspolice erworben. Jetzt wird es Zeit für die Erneuerung ihrer Versicherungspolice. Gloria Rios, Versicherungsmitarbeiterin von We.Finance sendet Sarah eine Erinnerung bezüglich der Erneuerung ihrer Versicherungspolice. Sarah folgt den Anweisungen in der E-Mail und schließt den Vorgang erfolgreich ab.

## Anleitung für einen Antrag auf eine Kfz-Versicherung {#auto-insurance-application-walkthrough}

Das Szenario der Anwendung &quot;We.Finance Auto Insurance&quot;ist ein visueller Hinweis für den Benutzer und basiert auf zwei Personen:

* Sarah Rose, einen We.Finance-Kunden
* Gloria Rios, Versicherungsmitarbeiterin, We.Finance

### Gloria sendet eine Mitteilung zur Erneuerung der Versicherungspolice von We.Finance  {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria meldet sich in AEM Instanz an, klickt auf **Erneuerung der Kfz-Versicherung,** und klickt dann auf **Benutzeroberfläche für Agenten öffnen .** Der Klick füllt das Versicherungsdokument mit den Richtliniendetails von Sarah Rose. Gloria klickt auf **Submit** und eine Nachricht wird auf dem Bildschirm &quot;Submission Initiated&quot;und dann in wenigen Sekunden &quot;Submitted Successful&quot;angezeigt.

Sarah erhält eine E-Mail mit dem Betreff &quot;Erneuerung Ihrer Kfz-Versicherung&quot;.

![Agent-Benutzeroberfläche](assets/agent_ui_email_new.png)

#### Sehen Sie selbst{#see-it-yourself} 

Gehen Sie zu **Adobe Experience Manager** > **Forms** > **Forms und Dokumente** > **We.Finance** > **Kfz-Versicherung**. Wählen Sie die Erneuerung der Kfz-Versicherung **interaktive Kommunikation** aus und klicken Sie auf **Benutzeroberfläche für Agenten öffnen**. Die interaktive Kommunikation wird in der Agent UI geöffnet. Geben Sie eine gültige E-Mail-Adresse ein, an die die E-Mail mit dem angehängten Richtliniendokument gesendet werden soll, und klicken Sie auf &quot;Senden&quot;.

Sie können die interaktive Kommunikation zur Erneuerung der Kfz-Versicherung direkt über `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.` aufrufen und überprüfen.

### Sarah erhält von We.Finance eine Mitteilung zur Erneuerung der Kfz-Versicherung und entscheidet sich für eine Erneuerung.{#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah erhält eine E-Mail mit einer Anlage von We.Finance, die sie daran erinnert, dass ihre Kfz-Versicherungspolice bald abläuft. Der Anhang ist die Druckversion ihres Kfz-Versicherungsbriefs.

Sarah klickt auf **Jetzt erneuern** und wird zur Webversion ihres Kfz-Versicherungsbriefs weitergeleitet. Zusätzlich zu diesem Brief findet Sarah noch eine Anzahl von Tagen, bis ihre Richtlinie abläuft. Die Seite bietet Sarah einen grundlegenden Überblick über ihre Details zur Versicherungspolice, wie z. B. die Versicherungsnummer, den fälligen Betrag und andere Informationen wie Rabattangebote und Treuebelohnungen. Sarah klickt erneut auf **Jetzt erneuern** am Ende der Richtlinie.

![ref1](assets/ref1.png)

#### Funktionsweise {#how-it-works}

Die Web- und Druckausgabe Ihres Kfz-Versicherungsbriefs wird mithilfe der kanalübergreifenden Funktionen der interaktiven Kommunikation erstellt.

Die Schaltfläche „Jetzt erneuern“ in der E-Mail ist mit der Anwendung „Kfz-Versicherung erneuern“ verknüpft, die eine interaktive Kommunikation auf einer Veröffentlichungsinstanz ist.

#### Sehen Sie selbst  {#see-it-yourself-1}

Sie müssen eine E-Mail mit einem angehängten PDF-Dokument erhalten haben. Die PDF ist eine Druckversion Ihres Kfz-Versicherungsbriefs. Klicken Sie auf **Jetzt erneuern** , um zur Webversion der Richtlinie zu gelangen. Überprüfen Sie Ihre persönlichen Informationen und Richtliniendetails und klicken Sie auf **Jetzt erneuern** , um zu einer anderen interaktiven Kommunikation zu gelangen.

Die Schaltfläche **Jetzt erneuern** in der E-Mail leitet Sarah zur Webversion der Richtlinie weiter. Sie können folgende URL aufrufen:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

Sie können die detaillierte Zusammenfassung Ihrer Erneuerung der Kfz-Versicherung überprüfen und unten auf der Seite auf **Jetzt erneuern** klicken.

### Sarah wird auf die Zahlungsseite geleitet.{#sarah-reaches-the-payment-page}

We.Finance leitet Sarah zur Zahlungsseite. Sarah überprüft ihre Policennummer und ihr Ablaufdatum mit ihren Datensätzen. Auf der rechten Seite der Seite prüft sie die Zahlungszusammenfassung ihrer Verlängerung mit einem Prämienrabatt von 10 % auf den Gesamtbetrag.

#### Funktionsweise {#how-it-works-1}

Über die Schaltfläche Jetzt erneuern gelangt Sarah zur Zahlungsseite. Die Zahlungsseite ist ein adaptives Formular.

#### Sehen Sie selbst{#see-it-yourself-2} 

Klicken Sie auf **Jetzt erneuern**, um zur Zahlungsseite zu gelangen. Geben Sie Ihre Kreditkarteninformationen ein und klicken Sie auf **Zahlung vornehmen**.

Sie können die Zahlungsseite in der Authoring-Instanz erreichen unter

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah nimmt die Zahlung vor und schließt den Prozess ab.{#sarah-makes-the-payment-and-completes-the-process}

Sarah gibt ihre Kreditkartendetails ein und klickt auf **Zahlung ausführen**.

#### Funktionsweise {#how-it-works-2}

Wenn Sarah die Kreditkartendaten eingibt und auf „Senden“ klickt, wird ihre Kreditkartenzahlung verarbeitet und auf dem Bildschirm erscheint eine Dankesnachricht, die im adaptiven Formular konfiguriert wurde.

#### Sehen Sie selbst  {#see-it-yourself-3}

Sie können die Bestätigungsmeldung anzeigen, nachdem Sie auf „Zahlung ausführen“ geklickt haben

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
