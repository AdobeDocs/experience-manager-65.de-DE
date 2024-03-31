---
title: Erstellen einer effektiven Landingpage für Newsletter
description: Eine effektive Startseite für Ihren Newsletter hilft Ihnen dabei, so viele Personen wie möglich dazu zu animieren, sich für Ihren Newsletter (oder eine andere E-Mail-Marketing-Kampagne) zu registrieren. Sie können die Informationen nutzen, die Sie aus Ihren Newsletter-Anmeldungen sammeln, um Leads zu gewinnen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: c2fbf858-8815-426e-a2e5-f92bcf909ad0
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 100%

---

# Erstellen einer effektiven Landingpage für Newsletter{#creating-an-effective-newsletter-landing-page}

Eine effektive Startseite für Ihren Newsletter hilft Ihnen dabei, so viele Personen wie möglich dazu zu animieren, sich für Ihren Newsletter (oder eine andere E-Mail-Marketing-Kampagne) zu registrieren. Sie können die Informationen nutzen, die Sie aus Ihren Newsletter-Anmeldungen sammeln, um Leads zu gewinnen.

Um eine effektive Newsletter-Landingpage zu erstellen, müssen Sie Folgendes tun:

1. Erstellen Sie eine Liste für den Newsletter, damit die Leute den Newsletter abonnieren können.
1. Erstellen Sie das Registrierungsformular. Fügen Sie dabei einen Workflow-Schritt hinzu, der die Person, die sich für den Newsletter anmeldet, automatisch zu Ihrer Lead-Liste hinzufügt.
1. Erstellen Sie eine Bestätigungsseite, die den Benutzenden für ihre Anmeldung dankt und ihnen möglicherweise eine Werbeaktion anbietet.
1. Fügen Sie Teaser hinzu.

>[!NOTE]
>
>Adobe plant nicht, diese Funktionen (Lead- und Listenverwaltung) weiter auszubauen.
>Es wird deshalb empfohlen, [Adobe Campaign und dessen Integration mit AEM zu nutzen](/help/sites-administering/campaign.md).

## Erstellen einer Liste für den Newsletter {#creating-a-list-for-the-newsletter}

Erstellen Sie in MCM eine Liste, z. B. **Geometrixx Newsletter**, für den Newsletter, den die Benutzer abonnieren sollten. Das Erstellen von Listen wird unter [Erstellen von Listen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingnewlists) beschrieben.

Nachfolgend sehen Sie ein Beispiel für eine Liste:

![mcm_listcreate](assets/mcm_listcreate.png)

## Erstellen eines Anmeldeformulars {#create-a-sign-up-form}

Erstellen Sie ein Registrierungsformular für den Newsletter, über das Benutzer Tags abonnieren können. Die Beispiel-Website „Geometrixx“ bietet eine Newsletter-Seite in der Geometrixx-Symbolleiste, wo Sie Ihr Formular erstellen können.

Informationen zum Erstellen Ihres eigenen Newsletter-Formulars finden Sie in der [Dokumentation zu Formularen](/help/sites-authoring/default-components.md#form). Der Newsletter verwendet die Tags aus der Tag-Bibliothek. Informationen zum Hinzufügen zusätzlicher Tags finden Sie unter [Tag-Verwaltung](/help/sites-authoring/tags.md#tagadministration).

Die ausgeblendeten Felder in dem folgenden Beispiel enthalten die minimal erforderlichen Informationen (E-Mail); zusätzlich hierzu können Sie später weitere Felder hinzufügen, was jedoch Auswirkungen auf die Konversionsrate hat.

Das folgende Beispiel ist ein Formular, das unter „https://localhost:4502/cf#/content/geometrixx/en/toolbar/newsletter.html“ erstellt wurde.

1. Erstellen Sie das Formular.

   ![mcm_newsletterpage](assets/mcm_newsletterpage.png)

1. Klicken Sie in der Formularkomponente auf **Bearbeiten**, um das Formular so zu konfigurieren, dass der Besucher auf eine Dankeseite (siehe [Erstellen von Dankeseiten](#creating-a-thank-you-page)) geleitet wird.

   ![dc_formstart_thankyou](assets/dc_formstart_thankyou.png)

1. Legen Sie die Formularaktion (die Aktion, die ausgeführt wird, wenn Sie das Formular übermitteln) fest und konfigurieren Sie die Gruppe so, dass registrierte Benutzer der zuvor erstellten Liste (z. B. geometrixx-newsletter) zugewiesen werden.

   ![dc_formstart_thankyouadvanced](assets/dc_formstart_thankyouadvanced.png)

### Erstellen einer Dankeseite {#creating-a-thank-you-page}

Wenn Benutzer auf **Jetzt abonnieren** klicken, soll automatisch eine Dankeseite geöffnet werden. Erstellen Sie die Dankeseite auf der Seite des Geometrixx-Newsletters. Nachdem Sie das Newsletter-Formular erstellt haben, bearbeiten Sie die Formularkomponente und fügen Sie den Pfad zur Dankeseite hinzu.

Nach dem Übermitteln der Anforderung wird der Benutzer zu einer **Danke**-Seite geleitet. Danach erhält er eine E-Mail. Diese Dankeseite wurde unter /content/geometrixx/en/toolbar/newsletter/thank_you erstellt.

![mcm_newsletter_thankyoupage](assets/mcm_newsletter_thankyoupage.png)

### Hinzufügen von Teasern {#adding-teasers}

Fügen Sie [Teaser](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers) hinzu, um bestimmte Zielgruppen anzusprechen. Sie können beispielsweise der Dankeseite und der Newsletter-Anmeldeseite Teaser hinzufügen.

So fügen Sie Teaser hinzu, um eine effektive Newsletter-Landingpage zu erstellen:

1. Erstellen Sie einen Teaser-Absatz für ein Registrierungsgeschenk. Wählen Sie **Erste** als Strategie aus und fügen Sie einen Text hinzu, der Benutzende darüber informiert, welches Geschenk sie erhalten werden.

   ![dc_teaser_thankyou](assets/dc_teaser_thankyou.png)

1. Erstellen Sie einen Teaser-Absatz für die Dankeseite. Wählen Sie **Erste** als die Strategie aus und fügen Sie einen Text ein, der darauf hinweist, dass das Geschenk unterwegs ist.

   ![chlimage_1-103](assets/chlimage_1-103.png)

1. Erstellen Sie eine Kampagne mit zwei Teasern; kennzeichnen Sie einen Teaser als „geschäftlich“ und belassen Sie den anderen ohne Kennzeichnung.

### Pushen von Inhalten zu Abonnentinnen und Abonnenten {#pushing-content-to-subscribers}

Übernehmen Sie alle Änderungen an Seiten über die Newsletter-Funktion in MCM. Anschließend pushen Sie aktualisierte Inhalte zu den Abonnentinnen und Abonnenten.

Siehe [Senden von Newslettern](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters).
