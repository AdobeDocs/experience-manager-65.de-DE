---
title: Verwenden von "Gefällt mir"
seo-title: Verwenden von "Gefällt mir"
description: Hinzufügen und Konfigurieren der Komponente "Link"
seo-description: Hinzufügen und Konfigurieren der Komponente "Link"
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
translation-type: tm+mt
source-git-commit: e7268e43620860b7a1f7aa0a1f1a54199dadcf17
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 7%

---


# Verwenden von &quot;Gefällt mir&quot; {#using-liking}

Die `Liking` Komponente ist ein nützliches Werkzeug, mit dem Benutzer eine Meinung zu einem bestimmten Inhalt, wie z.B. einem Kommentar in einem Forum, äußern können. Bei der `Liking` Komponente wählen die Mitglieder das Herzsymbol aus, um eine positive Meinung anzuzeigen.

## Adding Liking to a Page {#adding-liking-to-a-page}

To add a `Liking` component to a page in author mode, use the component browser to locate

* `Communities / Liking`

und ziehen Sie es auf eine Seite, z. B. eine Position relativ zur Funktion, die Benutzern gefällt.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](essentials-liking.md#essentials-for-client-side) are included, this is how the `Liking` component will appear.

![chlimage_1-93](assets/chlimage_1-93.png)

## Konfigurieren von &quot;Gefällt mir&quot; {#configuring-liking}

Select the placed `Liking` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-94](assets/chlimage_1-94.png)

Under the **[!UICONTROL Texts &amp; Labels]** tab, specify the properties used to record likes.

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL Beschriftung für positive Antwort]**

   (*Erforderlich*) Der Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**

   (*Erforderlich*) Der Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Zählername]**

   (*Required*) The internal, identifiable property name for this instance of a voting component.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Mitglieder können jederzeit ihre Art ändern.

### Anonym {#anonymous}

Anonyme &quot;Gefällt mir&quot;-Klicks werden nicht unterstützt. Site-Besucher müssen sich registrieren (Mitglied werden) und sich anmelden, um an &quot;Gefällt mir&quot;-Klicks teilzunehmen.

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Liking Essentials](essentials-liking.md) page for developers.
