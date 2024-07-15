---
title: Verwenden von Bewertungen
description: Erfahren Sie, wie Sie eine Bewertungskomponente zu einer Seite hinzufügen, über die angemeldete Community-Mitglieder ihre Meinung durch Inhaltsbewertung äußern können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 7534ad5d-b408-4b09-bd3d-da7ab009d55b
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 1%

---

# Verwenden von Bewertungen {#using-ratings}

Die Komponente `Rating` wird eigenständig oder mit anderen Communities-Funktionen verwendet. Diese Komponente ermöglicht es angemeldeten Community-Mitgliedern, ihre Meinung durch Bewertung von Inhalten zu äußern.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-rating-to-a-page}

Um eine `Rating` -Komponente im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie die Komponente `Communities / Rating` und ziehen Sie sie auf eine Seite, z. B. eine Position relativ zur Funktion, die Mitglieder bewerten sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [ erforderlichen clientseitigen Bibliotheken](rating-basics.md#essentials-for-client-side) enthalten sind, wird die Komponente `Rating` so angezeigt.

![rating](assets/rating.png)

## Konfigurieren der Bewertung {#configuring-rating}

Wählen Sie die platzierte Komponente `Rating` aus, damit Sie auf das Symbol `Configure` zugreifen und dieses auswählen können, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

Auf der Registerkarte **[!UICONTROL Texte und Beschriftungen]** geben Sie die interne Kennung für die Bewertung an.

![tallyname](assets/tallyname.png)

**[!UICONTROL Tally Name]**
(*Erforderlich*) Ein einfacher Name für die `Rating`, der diese Instanz eindeutig identifiziert. Muss ein gültiger Knotenname für das Repository sein.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Pro Mitglied ist nur eine Bewertung zulässig. Das Mitglied kann sein Rating jederzeit ändern.

### Anonym {#anonymous}

Das anonyme Posten einer Bewertung wird nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um teilnehmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Bewertungsgrundlagen](rating-basics.md) .
