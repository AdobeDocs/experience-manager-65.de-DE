---
title: Badges-Konsole
seo-title: Badges-Konsole
description: Mit der Konsole "Communities-Badges"können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie eine bestimmte Rolle in der Community übernehmen (zugewiesen)
seo-description: Mit der Konsole "Communities-Badges"können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie eine bestimmte Rolle in der Community übernehmen (zugewiesen)
uuid: 7103b133-ef3f-47d6-a2dc-4e6ff92e8fed
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 135b3077-5343-4888-858d-de5e9b1d4b04
docset: aem65
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 4%

---


# Badges-Konsole {#badges-console}

## Info zu Kennzeichen {#about-badges}

Die Communities Badges-Konsole bietet die Möglichkeit, benutzerdefinierte Abzeichen hinzuzufügen, die für ein Mitglied angezeigt werden können, wenn es verdient (verliehen) oder eine bestimmte Rolle in der Community übernimmt (zugewiesen).

### Badge-Sichtbarkeit {#badge-visibility}

Derzeit werden Kennzeichen, die ein Community-Mitglied verdient oder zugewiesen wird, zusammen mit ihrem Namen und Avatar an den folgenden Orten angezeigt:

* Profile
* [Foren](/help/communities/forum.md)
* [Frage und Antwort](/help/communities/working-with-qna.md)
* [Leadership-Pinnwände](/help/communities/enabling-leaderboard.md)
* [Ideen](/help/communities/ideation-feature.md)

Navigieren Sie in der Autorenkonsole zur Badges-Umgebung:

* Aus globaler Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Abzeichen]**

Diese Konsole zeigt die derzeit verfügbaren Abzeichen an, aus denen neue Abzeichen hinzugefügt werden können.

![badges-homepage](assets/badges-homepage.png)

## Abzeichen erstellen {#create-badge}

Eine Markierung wird erstellt, indem ein entsprechend kleines Bild hochgeladen wird (72 dpi mit einer Höhe von 26-32 Pixel) und ein Name angegeben wird. Das Abzeichen wird im Repository unter `/libs/settings/community/badging/images` gespeichert und automatisch in die Umgebung &quot;publish&quot;repliziert.

Wenn die Veröffentlichungs-Umgebung eine Herausgeberfarm ist, müssen Sie [Benutzersynchronisierung](/help/communities/sync.md) konfigurieren.

![create-badge](assets/create-badge.png)

* **Bild hochladen**

   (*Erforderlich*) Ein Abzeichen mit einer empfohlenen Größe von 32 x 32 Pixel bei 72 dpi im JPEG- oder PNG-Format.

* **Name**

   (*Erforderlich*) Der Markenname. Es handelt sich um den standardmäßigen `Display Name`- sowie den Repository-Knotennamen. Wenn `Name` kein gültiger Repository-Knotenname ist, wird er geändert.

* **Anzeigename**

   (*Optional*) Der Name, der für das Zeichen in der Benutzeroberfläche angezeigt werden soll. Standard ist der unveränderte Text, der für `Name` eingegeben wird.

* **Beschreibung**

   (*Optional*) Eine Beschreibung für das Zeichen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen zum Einrichten von Scoring- und Badging-Regeln finden Sie unter [Scoring and Badges](/help/communities/implementing-scoring.md).

Informationen zum Verwalten von Abzeichen für Mitglieder finden Sie unter [Mitgliederkonsole](/help/communities/members.md).
