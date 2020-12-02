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
source-git-commit: c9fa5624a59f4b9a6f970628b03bbd8b7a277a73
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 6%

---


# Verwenden von &quot;Gefällt mir&quot;-Klicks {#using-liking}

Die `Liking`-Komponente ist ein nützliches Tool, mit dem Benutzer eine Meinung zu einem bestimmten Inhalt, z. B. zu einem Kommentar in einem Forum, äußern können. Bei der Komponente `Liking` wählen die Mitglieder das Herzsymbol aus, um eine positive Meinung anzuzeigen.

## Hinzufügen von &quot;Link&quot;zu einer Seite {#adding-liking-to-a-page}

Um einer Seite im Autorenmodus eine `Liking`-Komponente hinzuzufügen, suchen Sie im Komponentenbrowser nach

* `Communities / Liking`

und ziehen Sie es auf eine Seite, z. B. eine Position relativ zur Funktion, die Benutzern gefällt.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-liking.md#essentials-for-client-side) einbezogen werden, wird die `Liking`-Komponente so angezeigt.

![liking-component](assets/liking-component.png)

## Konfigurieren von &quot;Gefällt mir&quot;-Klicks {#configuring-liking}

Wählen Sie die platzierte Komponente `Liking` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

Geben Sie auf der Registerkarte **[!UICONTROL Texte und Bezeichnungen]** die Eigenschaften an, mit denen Sie &quot;Gefällt mir&quot;aufzeichnen.

![configure-like](assets/configure-liking.png)

* **[!UICONTROL Beschriftung für positive Antwort]**

   (*Erforderlich*) Der Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**

   (*Erforderlich*) Der Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Zählername]**

   (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer stimmberechtigten Komponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Mitglieder können jederzeit ihre Art ändern.

### Anonym {#anonymous}

Anonyme &quot;Gefällt mir&quot;-Klicks werden nicht unterstützt. Site-Besucher müssen sich registrieren (Mitglied werden) und sich anmelden, um an &quot;Gefällt mir&quot;-Klicks teilzunehmen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Liking Essentials](essentials-liking.md) für Entwickler.
