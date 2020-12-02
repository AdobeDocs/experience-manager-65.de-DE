---
title: Verwenden von Bewertungen
seo-title: Verwenden von Bewertungen
description: Hinzufügen einer Bewertungskomponente zu einer Seite
seo-description: Hinzufügen einer Bewertungskomponente zu einer Seite
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
translation-type: tm+mt
source-git-commit: 0051791da06d15a48b82cf93164a89b4ea42ce98
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 37%

---


# Verwenden von Bewertungen {#using-ratings}

Die Komponente `Rating` wird eigenständig oder in Verbindung mit anderen Communities-Funktionen verwendet. Diese Komponente ermöglicht es angemeldeten Community-Mitgliedern, ihre Meinung durch Bewertung von Inhalten zu äußern.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-rating-to-a-page}

Um eine `Rating`-Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente `Communities / Rating` und ziehen Sie sie auf eine Seite, z. B. eine Position relativ zur Funktion, die Mitglieder bewerten sollen.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](rating-basics.md#essentials-for-client-side) einbezogen werden, wird die `Rating`-Komponente so angezeigt.

![Bewertung](assets/rating.png)

## Konfigurieren einer Bewertung {#configuring-rating}

Wählen Sie die platzierte Komponente `Rating` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

Legen Sie auf der Registerkarte **[!UICONTROL Texte &amp; Beschriftungen]** die interne ID der Bewertung fest.

![tallyname](assets/tallyname.png)

**[!UICONTROL Tally Name]**
(*Erforderlich*) Ein einfacher Name für die Instanz,  `Rating` die diese Instanz eindeutig identifiziert. Es muss sich um einen gültigen Knotennamen des Verzeichnisses handeln.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Pro Mitglied ist nur eine Bewertung zulässig.  Das Mitglied kann seine Meinung jedoch jederzeit ändern.

### Anonym  {#anonymous}

Das anonyme Posten von Bewertungen wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Rating Essentials](rating-basics.md) für Entwickler.
