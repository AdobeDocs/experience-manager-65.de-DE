---
title: Badges-Konsole
description: In der Konsole „Community-Abzeichen“ können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie verdient (verliehen) wurden oder eine bestimmte Rolle in der Community einnehmen (zugewiesen)
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 50ed9ec4-ff04-4f9d-aefb-0837542a9455
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 4%

---

# Badges-Konsole {#badges-console}

## Über Abzeichen {#about-badges}

In der Konsole „Community-Abzeichen“ können Sie benutzerdefinierte Abzeichen hinzufügen, die einem Mitglied angezeigt werden können, wenn es eine bestimmte Rolle in der Community (zugewiesen) oder verdient (verliehen) hat.

### Sichtbarkeit des Abzeichens {#badge-visibility}

Derzeit werden Abzeichen, die ein Community-Mitglied erhält oder zugewiesen wird, zusammen mit ihrem Namen und Avatar an den folgenden Stellen angezeigt:

* Profile
* [Foren](/help/communities/forum.md)
* [Fragen und Antworten](/help/communities/working-with-qna.md)
* [Leaderboards](/help/communities/enabling-leaderboard.md)
* [Ideen](/help/communities/ideation-feature.md)

Navigieren Sie in der Autorenumgebung zur Konsole „Badges“:

* Über die globale Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Badges]**

Diese Konsole zeigt die derzeit verfügbaren Abzeichen an, aus denen neue Abzeichen hinzugefügt werden können.

![badges-homepage](assets/badges-homepage.png)

## Abzeichen erstellen {#create-badge}

Ein Badge wird erstellt, indem ein entsprechend kleines Bild (72 dpi mit einer Höhe zwischen 26 und 32 Pixel) hochgeladen und ein Name angegeben wird. Das Badge-Bild wird im Repository unter `/libs/settings/community/badging/images` gespeichert und automatisch in der Veröffentlichungsumgebung repliziert.

Wenn die Veröffentlichungsumgebung eine Farm von Herausgebern ist, müssen Sie &quot;[&quot; &#x200B;](/help/communities/sync.md).

![create-badge](assets/create-badge.png)

* **Bild hochladen**

  (*Erforderlich*) Ein Badge-Bild mit einer empfohlenen Größe von 32 x 32 Pixel bei 72 dpi im JPEG- oder PNG-Format.

* **Name**

  (*Erforderlich*) Der Badge-Name. Es handelt sich um die `Display Name` und den Repository-Knotennamen. Wenn der `Name` kein gültiger Repository-Knotenname ist, wird er geändert.

* **Anzeigename**

  (*Optional*) Der Name, der für das Badge in der Benutzeroberfläche angezeigt werden soll. Der Standardwert ist der unveränderte Text, der für die `Name` eingegeben wurde.

* **Beschreibung**

  (*Optional*) Eine Beschreibung für das Abzeichen.

## Zusätzliche Informationen {#additional-information}

Einzelheiten zum Einrichten von Regeln für Bewertung und Badging finden Sie unter [Bewertung und Badges](/help/communities/implementing-scoring.md).

Informationen zum Verwalten von Abzeichen für Mitglieder finden Sie unter [Mitgliederkonsole](/help/communities/members.md).
