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
translation-type: tm+mt
source-git-commit: 548e19b0fc76ede8685ea938ed871fbdc8c3858f
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---


# Badges-Konsole {#badges-console}

## Info zu Abzeichen {#about-badges}

Die Communities Badges-Konsole bietet die Möglichkeit, benutzerdefinierte Abzeichen hinzuzufügen, die für ein Mitglied angezeigt werden können, wenn es verdient (verliehen) oder eine bestimmte Rolle in der Community übernimmt (zugewiesen).

### Sichtbarkeit der Abzeichen {#badge-visibility}

Derzeit werden Kennzeichen, die ein Community-Mitglied verdient oder zugewiesen wird, zusammen mit ihrem Namen und Avatar an den folgenden Orten angezeigt:

* Profile
* [Foren](/help/communities/forum.md)
* [Frage und Antwort](/help/communities/working-with-qna.md)
* [Leadership-Pinnwände](/help/communities/enabling-leaderboard.md)
* [Ideen](/help/communities/ideation-feature.md)

Navigieren Sie in der Autorenkonsole zur Badges-Umgebung:

* Aus globaler Navigation: **[!UICONTROL Werkzeuge]** > **[!UICONTROL Communities]** > **[!UICONTROL Abzeichen]**

Diese Konsole zeigt die derzeit verfügbaren Abzeichen an, aus denen neue Abzeichen hinzugefügt werden können.

![badges-homepage](assets/badges-homepage.png)

## Abzeichen erstellen {#create-badge}

Eine Markierung wird erstellt, indem ein entsprechend kleines Bild hochgeladen wird (72 dpi mit einer Höhe von 26-32 Pixel) und ein Name angegeben wird. Das Abzeichen wird im Repository gespeichert `/libs/settings/community/badging/images` und automatisch in die Umgebung &quot;Veröffentlichen&quot;repliziert.

Wenn die Umgebung zum Veröffentlichen eine Herausgeberfarm ist, müssen Sie die [Benutzersynchronisierung](/help/communities/sync.md)konfigurieren.

![create-badge](assets/create-badge.png)

* **Bild hochladen**

   (*Erforderlich*) Ein Badge-Bild mit einer empfohlenen Größe von 32 x 32 Pixel bei 72 dpi im JPEG- oder PNG-Format.

* **Name**

   (*Erforderlich*) Der Markenname. Dies ist der Standardname `Display Name` sowie der Repository-Knotenname. Wenn der Knoten kein gültiger Repository-Knotenname `Name` ist, wird er geändert.

* **Anzeigename**

   (*Optional*) Der Name, der für das Zeichen in der Benutzeroberfläche angezeigt wird. &quot;Standard&quot;ist der unveränderte Text, der für die `Name`Variable eingegeben wurde.

* **Beschreibung**

   (*Optional*) Eine Beschreibung des Kennzeichens.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen zum Einrichten von Scoring- und Kennzeichnungsregeln finden Sie unter [Scoring and Badges](/help/communities/implementing-scoring.md).

Informationen zum Verwalten von Abzeichen für Mitglieder finden Sie unter [Mitglieder-Konsole](/help/communities/members.md).
