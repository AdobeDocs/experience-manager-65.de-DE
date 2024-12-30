---
title: Abstimmung verwenden
description: Erfahren Sie, wie Sie die Abstimmungskomponente zu einer Seite hinzufügen, auf der angemeldete Community-Mitglieder einen bestimmten Inhalt, z. B. eine Antwort, bewerten können.
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

# Abstimmung verwenden {#using-voting}

Die `Voting` ist ein nützliches Tool, mit dem Community-Mitglieder ein bestimmtes Inhaltselement bewerten können, z. B. eine Antwort innerhalb einer QnA-Komponente. Bei der Komponente `Voting` wählen die Mitglieder nach oben oder unten, um ihre Meinung anzugeben.

## Hinzufügen von Abstimmungen zu einer Seite {#adding-voting-to-a-page}

Um einer Seite im Autorenmodus eine `Voting` Komponente hinzuzufügen, verwenden Sie den Komponenten-Browser. Suchen Sie `Communities / Voting` und ziehen Sie es an eine Position auf einer Seite, z. B. eine Position relativ zur Funktion, über die Benutzer abstimmen können.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderlichen Client-seitigen ](essentials-voting.md#essentials-for-client-side) enthalten sind, wird die `Voting` Komponente wie folgt angezeigt.

![Abstimmungskomponente](assets/voting-component.png)

## Abstimmung konfigurieren {#configuring-voting}

Wählen Sie die platzierte `Voting` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

Geben Sie auf **[!UICONTROL Registerkarte]** Texte und Beschriftungen“ die Eigenschaften an, die zum Aufzeichnen der Abstimmungen verwendet werden sollen.

![Voting-label](assets/voting-label.png)

* **[!UICONTROL Positive Response Label]**

  (*Erforderlich*) Der interne Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**

  (*Erforderlich*) Der interne Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Tally-Name]**

  (*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Abgeordneten können nur einmal abstimmen, können aber ihre Stimme jederzeit ändern.

### Anonym {#anonymous}

Anonyme Abstimmung wird nicht unterstützt. Besuchende der Website müssen sich registrieren (Mitglied werden) und sich einmalig zur Teilnahme an der Abstimmung anmelden.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Voting Essentials](essentials-voting.md) für Entwickler.
