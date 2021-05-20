---
title: Badges Console
seo-title: Badges Console
description: Mit der Communities Badges-Konsole können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie eine bestimmte Rolle in der Community übernehmen (zugewiesen).
seo-description: Mit der Communities Badges-Konsole können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie eine bestimmte Rolle in der Community übernehmen (zugewiesen).
uuid: 7103b133-ef3f-47d6-a2dc-4e6ff92e8fed
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 135b3077-5343-4888-858d-de5e9b1d4b04
docset: aem65
role: Administrator
exl-id: 50ed9ec4-ff04-4f9d-aefb-0837542a9455
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---

# Badges Console {#badges-console}

## Über Abzeichen {#about-badges}

Die Communities-Badges-Konsole bietet die Möglichkeit, benutzerdefinierte Abzeichen hinzuzufügen, die einem Mitglied angezeigt werden können, wenn es eine bestimmte Rolle in der Community spielt (zugewiesen).

### Badge-Sichtbarkeit {#badge-visibility}

Derzeit werden Abzeichen, die ein Community-Mitglied erhält oder zugewiesen wird, zusammen mit seinem Namen und Avatar an den folgenden Stellen angezeigt:

* Profile
* [Foren](/help/communities/forum.md)
* [Frage und Antwort](/help/communities/working-with-qna.md)
* [Leaderboards](/help/communities/enabling-leaderboard.md)
* [Ideen](/help/communities/ideation-feature.md)

Navigieren Sie in der Autorenumgebung zur Badges-Konsole:

* Über die globale Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Abzeichen]**

In dieser Konsole werden die derzeit verfügbaren Abzeichen und die neuen Abzeichen angezeigt.

![badges-homepage](assets/badges-homepage.png)

## Abzeichen erstellen {#create-badge}

Ein Badge wird durch Hochladen eines entsprechend kleinen Bildes (72 dpi mit einer Höhe von 26-32 Pixel) und Angabe eines Namens erstellt. Das Badge-Bild wird im Repository unter `/libs/settings/community/badging/images` gespeichert und automatisch in die Veröffentlichungsumgebung repliziert.

Wenn die Veröffentlichungsumgebung eine Farm von Herausgebern ist, muss [Benutzersynchronisierung](/help/communities/sync.md) konfiguriert werden.

![create-badge](assets/create-badge.png)

* **Bild hochladen**

   (*Erforderlich*) Ein Badge-Bild mit einer empfohlenen Größe von 32 x 32 Pixel bei 72 dpi im JPEG- oder PNG-Format.

* **Name**

   (*Erforderlich*) Der Badge-Name. Dies ist der standardmäßige `Display Name` sowie der Repository-Knotenname. Wenn `Name` kein gültiger Repository-Knotenname ist, wird er geändert.

* **Anzeigename**

   (*Optional*) Der Name, der für das Zeichen in der Benutzeroberfläche angezeigt werden soll. Der Standardtext ist der unveränderte Text, der für `Name` eingegeben wird.

* **Beschreibung**

   (*Optional*) Eine Beschreibung für das Zeichen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen zum Einrichten von Scoring- und Badging-Regeln finden Sie unter [Scoring und Badges](/help/communities/implementing-scoring.md).

Informationen zum Verwalten von Abzeichen für Mitglieder finden Sie unter [Mitglieder-Konsole](/help/communities/members.md).
