---
title: Verwenden der Abstimmung
description: Erfahren Sie, wie Sie die Komponente Abstimmung zu einer Seite hinzufügen, auf der angemeldete Community-Mitglieder bestimmte Inhalte bewerten können, z. B. eine Antwort.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: aa90bf1b-6053-4949-b061-232d72b80682
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 1%

---

# Verwenden der Abstimmung {#using-voting}

Die `Voting` -Komponente ist ein nützliches Tool, mit dem Community-Mitglieder einen bestimmten Inhalt bewerten können, z. B. eine Antwort innerhalb einer QnA-Komponente. Mit dem `Voting` -Komponente, wählen die Mitglieder Pfeile nach oben oder unten aus, um ihre Meinung zu äußern.

## Hinzufügen von Abstimmungen zu einer Seite {#adding-voting-to-a-page}

So fügen Sie eine `Voting` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser. Suchen `Communities / Voting` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an eine Position relativ zur Funktion, über die Benutzer abstimmen können.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](essentials-voting.md#essentials-for-client-side) eingeschlossen sind, wird die `Voting` -Komponente angezeigt.

![stimmberechtigte Komponente](assets/voting-component.png)

## Konfigurieren der Abstimmung {#configuring-voting}

Auswählen der platzierten `Voting` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Unter dem **[!UICONTROL Texte und Beschriftungen]** -Registerkarte die Eigenschaften für die Aufzeichnung von Abstimmungen angeben.

![Abstimmungsbezeichnung](assets/voting-label.png)

* **[!UICONTROL Beschriftung für positive Antwort]**

  (*Erforderlich*) Der interne Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Bezeichnung für negative Antworten]**

  (*Erforderlich*) Der interne Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Tally Name]**

  (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Mitglieder dürfen nur einmal abstimmen, können jedoch ihre Stimme jederzeit ändern.

### Anonym {#anonymous}

Anonyme Abstimmungen werden nicht unterstützt. Besucher müssen sich registrieren (Mitglied werden) und sich anmelden, um einmal an der Abstimmung teilzunehmen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Abstimmungsgrundlagen](essentials-voting.md) -Seite für Entwickler.
