---
title: Verwenden einer Abstimmung
seo-title: Verwenden einer Abstimmung
description: Hinzufügen der Komponente "Abstimmung"zu einer Seite
seo-description: Hinzufügen der Komponente "Abstimmung"zu einer Seite
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Verwenden einer Abstimmung {#using-voting}

The `Voting` component is a useful tool that allows community members to rate a particular piece of content, such as an answer within a QnA component. With the `Voting` component, members select up or down arrows to indicate their opinion.

## Hinzufügen einer Abstimmung zu einer Seite {#adding-voting-to-a-page}

Wenn Sie einer Seite im Autorenmodus eine `Voting` Komponente hinzufügen möchten, verwenden Sie den Komponenten-Browser, um sie zu suchen `Communities / Voting` und an ihre Position auf einer Seite zu ziehen, z. B. eine Position relativ zur Funktion, über die Benutzer abstimmen müssen.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](essentials-voting.md#essentials-for-client-side) are included, this is how the `Voting` component will appear.

![chlimage_1-307](assets/chlimage_1-307.png)

## Konfigurieren einer Abstimmung {#configuring-voting}

Select the placed `Voting` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-308](assets/chlimage_1-308.png)

Under the **[!UICONTROL Texts &amp; Labels]** tab, specify the properties used to record votes.

![chlimage_1-309](assets/chlimage_1-309.png)

* **[!UICONTROL Bezeichnung]** für positive Antwort (*Erforderlich*) Der interne Eigenschaftenname für eine positive Antwort.

* **[!UICONTROL Negative Response Label]**(*Erforderlich*) Der interne Eigenschaftenname für eine negative Antwort.

* **[!UICONTROL Tally Name]**(*Erforderlich*) Der interne, identifizierbare Eigenschaftenname für diese Instanz einer stimmberechtigten Komponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Mitglieder dürfen nur einmal abstimmen, können ihre Meinung jedoch jederzeit ändern.

### Anonym {#anonymous}

Eine anonyme Abstimmung wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um selbst abstimmen zu können.

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Voting Essentials](essentials-voting.md) page for developers.
