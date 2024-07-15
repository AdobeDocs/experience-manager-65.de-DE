---
title: Suchfunktion
description: Hinzufügen und Konfigurieren der Suche zu einer Communities-Site
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: e252b0e5-a2f8-468e-ac8c-951a5b0f2e32
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# Suchfunktion {#search-feature}

Die Suchfunktion kann mit verschiedenen anderen Funktionen wie Foren verwendet werden, um die Suche nach Inhalten zu ermöglichen.

Beim Hinzufügen der Möglichkeit, Beiträge von Community-Mitgliedern zu durchsuchen, die als benutzergenerierte Inhalte (UGC) bezeichnet werden, gibt es zwei Komponenten: [Suche](#search) und [Suchergebnisse](#search-results).

Die Seite, die die Komponente `Search Results` enthält, unterstützt sowohl die Suche als auch die Anzeige der Ergebnisse.

Die Seite, die die Komponente `Search` enthält, bietet einen Ort zum Starten einer Suche mit Ergebnissen, die auf der Seite `Search Results` angezeigt werden.

Die Suchfunktion kann mit jeder anderen Funktion verwendet werden, die es Site-Besuchern und Mitgliedern ermöglicht, Inhalte anzuzeigen.

## Suchen {#search-features}

### Hinzufügen einer Suche zu einer Seite {#add-search-to-a-page}

Um eine `Search` -Komponente im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie im Komponenten-Browser nach `Communities / Search` und ziehen Sie sie an die gewünschte Stelle auf einer Seite. Für die Verwendung von `Search` ist eine zweite Seite für die `Search Results.` erforderlich.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die erforderliche clientseitige Bibliothek `cq.social.hbs.search` enthalten ist, wird die Komponente `Search` so angezeigt.

![add-search](assets/add-search.png)

### Konfigurieren der hinzugefügten Suche {#configure-the-added-search}

Wählen Sie die platzierte Komponente `Search` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![config](assets/configure-new.png)

Geben Sie auf der Registerkarte **[!UICONTROL Sucheinstellungen]** an, welche Pfade gesucht werden sollen, wenn ein Besucher eine Abfrage eingibt.

![search-settings](assets/search-settings.png)

* **[!UICONTROL Suchpfade]**
Durch Hinzufügen von Suchpfaden mit der Schaltfläche Element hinzufügen ist die Inhaltssuche eingeschränkt. Um beispielsweise die Suche auf ein bestimmtes Forum zu beschränken, wählen Sie eine Forumskomponente aus, die auf einer Seite platziert wird:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Ergebnisseite]**
Die Ergebnisse werden auf einer separaten Seite angezeigt, die über den Browser angegeben wird, um eine Seite auszuwählen, die die Komponente `Search Results` enthält.

## Suchergebnisse {#search-results}

### Suchergebnisse zu einer Seite hinzufügen {#add-search-results-to-a-page}

Möchten Sie im Autorenmodus einer Seite die Komponente `Search Results` hinzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Search Results`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite. Im Gegensatz zur Suchkomponente ist keine zweite Seite erforderlich, da die Ergebnisse auf derselben Seite angezeigt werden.

Wenn Sie die Suche an einer anderen Stelle auf der Website verwenden, kann diese eine Seite mit `Search Results` so konfiguriert werden, dass sie die `Result Page` für eine oder alle Instanzen von `Search` ist.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die erforderliche clientseitige Bibliothek `cq.social.hbs.search` enthalten ist, wird die Komponente `Search Result` so angezeigt:

![search-result](assets/search-result1.png)

### Konfigurieren des hinzugefügten Suchergebnisses {#configure-the-added-search-result}

Wählen Sie die platzierte Komponente `Search Results` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure](assets/configure-new.png)

Auf der Registerkarte **[!UICONTROL Suchergebniseinstellungen]** können Sie festlegen, welche Pfade bei der Suche einbezogen werden sollen, wenn ein Besucher eine Abfrage eingibt.

![search-result-settings](assets/search-result-settings.png)

* **[!UICONTROL Suchergebnisse pro Seite]**

  Definieren Sie die Anzahl der Themen/Beiträge, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Suchpfade]**

  Durch Hinzufügen von Suchpfaden mit der Schaltfläche Element hinzufügen ist die Inhaltssuche eingeschränkt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Suchgrundlagen](search-implementation.md) .
