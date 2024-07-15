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

Die Komponente `Voting` ist ein nützliches Tool, mit dem Community-Mitglieder bestimmte Inhalte bewerten können, z. B. eine Antwort innerhalb einer QnA-Komponente. Bei der Komponente `Voting` wählen die Mitglieder Pfeile nach oben oder unten aus, um ihre Meinung anzugeben.

## Hinzufügen von Abstimmungen zu einer Seite {#adding-voting-to-a-page}

Verwenden Sie den Komponenten-Browser, um im Autorenmodus einer Seite die Komponente `Voting` hinzuzufügen. Suchen Sie `Communities / Voting` und ziehen Sie es an die gewünschte Stelle auf einer Seite, z. B. an eine Position relativ zur Funktion, über die Benutzer abstimmen können.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [ erforderlichen clientseitigen Bibliotheken](essentials-voting.md#essentials-for-client-side) enthalten sind, wird die Komponente `Voting` so angezeigt.

![stimmkomponente](assets/voting-component.png)

## Konfigurieren der Abstimmung {#configuring-voting}

Wählen Sie die platzierte Komponente `Voting` aus, damit Sie auf das Symbol `Configure` zugreifen und dieses auswählen können, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure](assets/configure-new.png)

Geben Sie auf der Registerkarte **[!UICONTROL Texte und Beschriftungen]** die Eigenschaften an, die zum Aufzeichnen von Stimmen verwendet werden.

![stimmbeschriftung](assets/voting-label.png)

* **[!UICONTROL Bezeichnung der positiven Antwort]**

  (*Erforderlich*) Der interne Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Bezeichnung der negativen Antwort]**

  (*Erforderlich*) Der interne Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Tally Name]**

  (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Mitglieder dürfen nur einmal abstimmen, können jedoch ihre Stimme jederzeit ändern.

### Anonym {#anonymous}

Anonyme Abstimmungen werden nicht unterstützt. Besucher müssen sich registrieren (Mitglied werden) und sich anmelden, um einmal an der Abstimmung teilzunehmen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Grundlegende Stimmrechte](essentials-voting.md) .
