---
title: Verwenden von Bewertungen
seo-title: Using Ratings
description: Hinzufügen einer Bewertungskomponente zu einer Seite
seo-description: Adding a Rating component to a page
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
exl-id: 7534ad5d-b408-4b09-bd3d-da7ab009d55b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 37%

---

# Verwenden von Bewertungen {#using-ratings}

Die `Rating` -Komponente wird eigenständig oder in Verbindung mit anderen Communities-Funktionen verwendet. Diese Komponente ermöglicht es angemeldeten Community-Mitgliedern, ihre Meinung durch Bewertung von Inhalten zu äußern.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-rating-to-a-page}

So fügen Sie eine `Rating` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente `Communities / Rating` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position relativ zur Funktion, die Mitglieder bewerten sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](rating-basics.md#essentials-for-client-side) eingeschlossen sind, wird die `Rating` wird angezeigt.

![Bewertung](assets/rating.png)

## Konfigurieren einer Bewertung {#configuring-rating}

Wählen Sie die platzierte `Rating` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![configure-new](assets/configure-new.png)

Legen Sie auf der Registerkarte **[!UICONTROL Texte &amp; Beschriftungen]** die interne ID der Bewertung fest.

![tallyname](assets/tallyname.png)

**[!UICONTROL Tally Name]**
(*Erforderlich*) Ein einfacher Name für `Rating` die diese Instanz eindeutig identifiziert. Es muss sich um einen gültigen Knotennamen des Verzeichnisses handeln.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Pro Mitglied ist nur eine Bewertung zulässig.  Das Mitglied kann seine Meinung jedoch jederzeit ändern.

### Anonym {#anonymous}

Das anonyme Posten von Bewertungen wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Bewertungsgrundlagen](rating-basics.md) für Entwickler.
