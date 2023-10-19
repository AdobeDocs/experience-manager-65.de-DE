---
title: Verwenden von Bewertungen
description: Erfahren Sie, wie Sie eine Bewertungskomponente zu einer Seite hinzufügen, über die angemeldete Community-Mitglieder ihre Meinung durch Inhaltsbewertung äußern können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 7534ad5d-b408-4b09-bd3d-da7ab009d55b
source-git-commit: 62d4a8b3af5031ccc539d78f7d06a8cd1fec7af1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 2%

---

# Verwenden von Bewertungen {#using-ratings}

Die `Rating` -Komponente wird eigenständig oder mit anderen Communities-Funktionen verwendet. Diese Komponente ermöglicht es angemeldeten Community-Mitgliedern, ihre Meinung durch Bewertung von Inhalten zu äußern.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-rating-to-a-page}

So fügen Sie eine `Rating` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente `Communities / Rating` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position relativ zur Funktion, die Mitglieder bewerten sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](rating-basics.md#essentials-for-client-side) eingeschlossen sind, wird die `Rating` -Komponente angezeigt.

![Bewertung](assets/rating.png)

## Konfigurieren der Bewertung {#configuring-rating}

Auswählen der platzierten `Rating` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![configure-new](assets/configure-new.png)

Unter dem **[!UICONTROL Texte und Beschriftungen]** -Registerkarte die interne Kennung für die Bewertung angeben.

![tallyname](assets/tallyname.png)

**[!UICONTROL Tally Name]**
(*Erforderlich*) Ein einfacher Name für die `Rating` , die diese Instanz eindeutig identifiziert. Muss ein gültiger Knotenname für das Repository sein.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Pro Mitglied ist nur eine Bewertung zulässig. Das Mitglied kann sein Rating jederzeit ändern.

### Anonym {#anonymous}

Das anonyme Posten einer Bewertung wird nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um teilnehmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Bewertungsgrundlagen](rating-basics.md) -Seite für Entwickler.
