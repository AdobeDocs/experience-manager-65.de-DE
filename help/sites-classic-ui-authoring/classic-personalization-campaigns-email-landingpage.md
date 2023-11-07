---
title: Erstellen einer effektiven Landingpage für Newsletter
seo-title: Creating an Effective Newsletter Landing Page
description: Eine effektive Startseite für Ihren Newsletter hilft Ihnen dabei, so viele Personen wie möglich dazu zu animieren, sich für Ihren Newsletter (oder eine andere E-Mail-Marketing-Kampagne) zu registrieren. Sie können die Informationen verwenden, die Sie aus Ihren Newsletter-Anmeldungen erfassen, um Leads zu erhalten.
seo-description: An effective newsletter landing page helps you get as many people as possible to sign up for your newsletter (or other email marketing campaign). You can use the information you gather from your newsletter sign ups to get leads.
uuid: 0799b954-076b-4e95-8724-3661ae8fddb6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: b41de64a-7d27-4633-a8d5-ac91d47eb1bb
docset: aem65
exl-id: c2fbf858-8815-426e-a2e5-f92bcf909ad0
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 55%

---

# Erstellen einer effektiven Landingpage für Newsletter{#creating-an-effective-newsletter-landing-page}

Eine effektive Startseite für Ihren Newsletter hilft Ihnen dabei, so viele Personen wie möglich dazu zu animieren, sich für Ihren Newsletter (oder eine andere E-Mail-Marketing-Kampagne) zu registrieren. Sie können die Informationen verwenden, die Sie aus Ihren Newsletter-Anmeldungen erfassen, um Leads zu erhalten.

Gehen Sie wie folgt vor, um eine effektive Newsletter-Landingpage zu erstellen:

1. Erstellen Sie eine Liste für den Newsletter, damit sich Benutzer für den Newsletter anmelden können.
1. Erstellen Sie das Registrierungsformular. Fügen Sie in diesem Fall einen Workflow-Schritt hinzu, der automatisch die Person, die sich für den Newsletter anmeldet, zu Ihrer Lead-Liste hinzufügt.
1. Erstellen Sie eine Bestätigungsseite, auf der die Benutzer für die Anmeldung gedankt und ihnen möglicherweise eine Promotion bereitgestellt wird.
1. Teaser hinzufügen.

>[!NOTE]
>
>Adobe plant nicht, diese Funktionen (Lead- und Listenverwaltung) weiter auszubauen.
>Es wird empfohlen [Adobe Campaign und Integration in AEM](/help/sites-administering/campaign.md).

## Erstellen einer Liste für den Newsletter {#creating-a-list-for-the-newsletter}

Erstellen Sie in MCM eine Liste, z. B. **Geometrixx Newsletter**, für den Newsletter, den die Benutzer abonnieren sollten. Das Erstellen von Listen wird unter [Erstellen von Listen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingnewlists) beschrieben.

Nachfolgend sehen Sie ein Beispiel für eine Liste:

![mcm_listcreate](assets/mcm_listcreate.png)

## Erstellen eines Anmeldeformulars {#create-a-sign-up-form}

Erstellen Sie ein Registrierungsformular für den Newsletter, über das Benutzer Tags abonnieren können. Die Beispiel-Geometrixx-Website bietet eine Newsletter-Seite in der Geometrixx-Symbolleiste, auf der Sie Ihr Formular erstellen können.

Informationen zum Erstellen eines eigenen Newsletter-Formulars finden Sie unter Informationen zum Erstellen von Formularen in der [Forms-Dokumentation](/help/sites-authoring/default-components.md#form). Der Newsletter verwendet die Tags aus der Tag-Bibliothek. Informationen zum Hinzufügen zusätzlicher Tags finden Sie unter [Tag-Verwaltung](/help/sites-authoring/tags.md#tagadministration).

Die ausgeblendeten Felder in dem folgenden Beispiel enthalten die minimal erforderlichen Informationen (E-Mail); zusätzlich hierzu können Sie später weitere Felder hinzufügen, was jedoch Auswirkungen auf die Konversionsrate hat.

Das folgende Beispiel ist ein Formular, das unter „https://localhost:4502/cf#/content/geometrixx/en/toolbar/newsletter.html“ erstellt wurde.

1. Erstellen Sie das Formular.

   ![mcm_newsletterpage](assets/mcm_newsletterpage.png)

1. Klicken Sie in der Formularkomponente auf **Bearbeiten**, um das Formular so zu konfigurieren, dass der Besucher auf eine Dankeseite (siehe [Erstellen von Dankeseiten](#creating-a-thank-you-page)) geleitet wird.

   ![dc_formstart_thankyou](assets/dc_formstart_thankyou.png)

1. Legen Sie die Formularaktion (die Aktion, die ausgeführt wird, wenn Sie das Formular übermitteln) fest und konfigurieren Sie die Gruppe so, dass registrierte Benutzer der zuvor erstellten Liste (z. B. geometrixx-newsletter) zugewiesen werden.

   ![dc_formstart_thankyouadvanced](assets/dc_formstart_thankyouadvanced.png)

### Erstellen einer Dankeseite {#creating-a-thank-you-page}

Wenn Benutzer auf **Jetzt abonnieren** klicken, soll automatisch eine Dankeseite geöffnet werden. Erstellen Sie die Dankeseite auf der Seite des Geometrixx-Newsletters. Bearbeiten Sie nach der Erstellung des Newsletter-Formulars die Formular-Komponente und fügen Sie den Pfad zur Dankeseite hinzu.

Nach dem Übermitteln der Anforderung wird der Benutzer zu einer **Danke**-Seite geleitet. Danach erhält er eine E-Mail. Diese Dankeseite wurde unter /content/geometrixx/en/toolbar/newsletter/thank_you erstellt.

![mcm_newsletter_thankyoupage](assets/mcm_newsletter_thankyoupage.png)

### Hinzufügen von Teasern {#adding-teasers}

Fügen Sie [Teaser](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers) hinzu, um bestimmte Zielgruppen anzusprechen. Beispielsweise können Sie der Dankeseite und der Newsletter-Anmeldeseite Teaser hinzufügen.

So fügen Sie Teaser hinzu, um eine effektive Newsletter-Landingpage zu erstellen:

1. Erstellen Sie einen Teaser-Absatz für ein Registrierungsgeschenk. Auswählen **Erste** als Strategie verwenden und Text einschließen, der ihnen mitteilt, welches Geschenk sie erhalten.

   ![dc_teaser_thankyou](assets/dc_teaser_thankyou.png)

1. Erstellen Sie einen Teaser-Absatz für die Dankeseite. Auswählen **Erste** als Strategie verwenden und Text einschließen, der anzeigt, dass das Geschenk unterwegs ist.

   ![chlimage_1-103](assets/chlimage_1-103.png)

1. Erstellen Sie eine Kampagne mit zwei Teasern; kennzeichnen Sie einen Teaser als „geschäftlich“ und belassen Sie den anderen ohne Kennzeichnung.

### Übermitteln von Inhalten an Abonnenten {#pushing-content-to-subscribers}

Übernehmen Sie alle Änderungen an Seiten über die Newsletter-Funktion in MCM. Anschließend senden Sie aktualisierte Inhalte an Abonnenten.

Siehe [Newsletter senden](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters).
