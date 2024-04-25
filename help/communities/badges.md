---
title: Badges Console
description: Mit der Communities Badges-Konsole können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie eine bestimmte Rolle in der Community übernehmen (zugewiesen).
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

# Badges Console {#badges-console}

## Über Abzeichen {#about-badges}

Mit der Communities Badges-Konsole können Sie benutzerdefinierte Abzeichen hinzufügen, die für ein Mitglied angezeigt werden können, wenn es eine bestimmte Rolle in der Community spielt (zugewiesen).

### Badge-Sichtbarkeit {#badge-visibility}

Derzeit werden Abzeichen, die ein Community-Mitglied erhält oder zugewiesen wird, zusammen mit seinem Namen und Avatar an den folgenden Stellen angezeigt:

* Profile
* [Foren](/help/communities/forum.md)
* [Fragen und Antworten](/help/communities/working-with-qna.md)
* [Leaderboards](/help/communities/enabling-leaderboard.md)
* [Ideen](/help/communities/ideation-feature.md)

Navigieren Sie in der Autorenumgebung zur Badges-Konsole:

* Über die globale Navigation: **[!UICONTROL Instrumente]** > **[!UICONTROL Communities]** > **[!UICONTROL Abzeichen]**

In dieser Konsole werden die derzeit verfügbaren Abzeichen und die neuen Abzeichen angezeigt.

![badges-homepage](assets/badges-homepage.png)

## Abzeichen erstellen {#create-badge}

Ein Badge wird durch Hochladen eines entsprechend kleinen Bildes (72 dpi mit einer Höhe von 26-32 Pixel) und Angabe eines Namens erstellt. Das Badge-Bild wird im Repository unter `/libs/settings/community/badging/images` und wird automatisch in die Veröffentlichungsumgebung repliziert.

Wenn es sich bei der Veröffentlichungsumgebung um eine Farm von Herausgebern handelt, müssen Sie [Benutzersynchronisierung](/help/communities/sync.md).

![create-badge](assets/create-badge.png)

* **Bild hochladen**

  (*Erforderlich*) Ein Badge mit einer empfohlenen Größe von 32 x 32 Pixel bei 72 dpi im JPEG- oder PNG-Format.

* **Name**

  (*Erforderlich*) Der Badge-Name. Dies ist die Standardeinstellung `Display Name` und den Repository-Knotennamen. Wenn die Variable `Name` kein gültiger Repository-Knotenname ist, wird er geändert.

* **Anzeigename**

  (*Optional*) Der Name, der für das Zeichen in der Benutzeroberfläche angezeigt werden soll. Die Standardeinstellung ist der unveränderte Text, der für die `Name`.

* **Beschreibung**

  (*Optional*) Eine Beschreibung für das Zeichen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen zum Einrichten von Scoring- und Badging-Regeln finden Sie unter [Scoring und Abzeichen](/help/communities/implementing-scoring.md).

Informationen zum Verwalten von Abzeichen für Mitglieder finden Sie unter [Mitgliederkonsole](/help/communities/members.md).
