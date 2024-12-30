---
title: Verwendung von Bewertungen
description: Erfahren Sie, wie Sie einer Seite eine Bewertungskomponente hinzufügen, mit der angemeldete Community-Mitglieder ihre Meinung durch Bewertung von Inhalten ausdrücken können.
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

# Verwendung von Bewertungen {#using-ratings}

Die `Rating`-Komponente wird eigenständig oder mit anderen Communities-Funktionen verwendet. Diese Komponente ermöglicht es angemeldeten Community-Mitgliedern, ihre Meinungen durch die Bewertung von Inhalten auszudrücken.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-rating-to-a-page}

Um einer Seite im Autorenmodus eine `Rating` Komponente hinzuzufügen, suchen Sie die `Communities / Rating` und ziehen Sie sie an die gewünschte Position auf der Seite, z. B. relativ zur Funktion, die Mitglieder bewerten sollen.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderlichen Client-seitigen ](rating-basics.md#essentials-for-client-side) enthalten sind, wird die `Rating` Komponente wie folgt angezeigt.

![rating](assets/rating.png)

## Rating konfigurieren {#configuring-rating}

Wählen Sie die platzierte `Rating` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![configure-new](assets/configure-new.png)

Auf der Registerkarte **[!UICONTROL Texte und Beschriftungen]** geben Sie die interne Kennung für die Bewertung an.

![tallyname](assets/tallyname.png)

**[!UICONTROL Tally-Name]**
(*Erforderlich*) Ein einfacher Name für die `Rating`, der diese Instanz eindeutig identifiziert. Muss ein gültiger Knotenname für das Repository sein.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Pro Mitglied ist nur eine Bewertung zulässig. Das Mitglied kann seine Bewertung jederzeit ändern.

### Anonym {#anonymous}

Die anonyme Veröffentlichung einer Bewertung wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglied werden) und sich anmelden, um teilzunehmen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Rating Essentials](rating-basics.md) für Entwickler.
