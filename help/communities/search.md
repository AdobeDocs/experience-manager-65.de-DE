---
title: Suchfunktion
description: Hinzufügen und Konfigurieren der Suche zu einer Communities-Site
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: e252b0e5-a2f8-468e-ac8c-951a5b0f2e32
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 2%

---

# Suchfunktion {#search-feature}

Die Suchfunktion kann mit verschiedenen anderen Funktionen wie Foren verwendet werden, um die Suche nach Inhalten zu ermöglichen.

Beim Hinzufügen der Möglichkeit, Beiträge von Community-Mitgliedern zu durchsuchen, die als benutzergenerierte Inhalte (UGC) bezeichnet werden, gibt es zwei Komponenten: [Suche](#search) und [Suchergebnisse](#search-results).

Die Seite, die die `Search Results` -Komponente unterstützt sowohl die Suche als auch die Anzeige von Ergebnissen.

Die Seite, die die `Search` -Komponente bietet einen Ort zum Starten einer Suche mit Ergebnissen, die auf der `Search Results` Seite.

Die Suchfunktion kann mit jeder anderen Funktion verwendet werden, die es Site-Besuchern und Mitgliedern ermöglicht, Inhalte anzuzeigen.

## Suchen {#search-features}

### Hinzufügen einer Suche zu einer Seite {#add-search-to-a-page}

So fügen Sie eine `Search` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / Search` und ziehen Sie sie an die gewünschte Stelle auf einer Seite. Verwendung von `Search` erfordert eine zweite Seite für die `Search Results.`

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die erforderliche clientseitige Bibliothek `cq.social.hbs.search`, enthalten ist, wird die `Search` -Komponente angezeigt.

![add-search](assets/add-search.png)

### Konfigurieren der hinzugefügten Suche {#configure-the-added-search}

Auswählen der platzierten `Search` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![config](assets/configure-new.png)

Unter dem **[!UICONTROL Sucheinstellungen]** angeben, wie welche Pfade gesucht werden, wenn ein Besucher eine Abfrage eingibt.

![search-settings](assets/search-settings.png)

* **[!UICONTROL Suchpfade]**
Durch Hinzufügen von Suchpfaden mit der Schaltfläche Element hinzufügen ist die Inhaltssuche eingeschränkt. Um beispielsweise die Suche auf ein bestimmtes Forum zu beschränken, wählen Sie eine Forumskomponente aus, die auf einer Seite platziert wird:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Ergebnisseite]**
Die Ergebnisse werden auf einer separaten Seite angezeigt, die durch Auswahl einer Seite mit dem `Search Results` -Komponente.

## Suchergebnisse {#search-results}

### Suchergebnisse zu einer Seite hinzufügen {#add-search-results-to-a-page}

So fügen Sie eine `Search Results` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Search Results`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite. Im Gegensatz zur Suchkomponente ist keine zweite Seite erforderlich, da die Ergebnisse auf derselben Seite angezeigt werden.

Wenn Sie die Suche an einer anderen Stelle auf der Website verwenden, wird diese eine Seite mit `Search Results` kann so konfiguriert werden, dass `Result Page` für alle Instanzen von `Search`.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die erforderliche clientseitige Bibliothek `cq.social.hbs.search`, enthalten ist, wird die `Search Result` wird angezeigt:

![Suchergebnis](assets/search-result1.png)

### Konfigurieren des hinzugefügten Suchergebnisses {#configure-the-added-search-result}

Auswählen der platzierten `Search Results` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Unter dem **[!UICONTROL Suchergebniseinstellungen]** angegeben, können Sie festlegen, welche Pfade bei der Suche berücksichtigt werden, wenn ein Besucher eine Abfrage eingibt.

![search-result-settings](assets/search-result-settings.png)

* **[!UICONTROL Suchergebnisse pro Seite]**

  Definieren Sie die Anzahl der Themen/Beiträge, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Suchpfade]**

  Durch Hinzufügen von Suchpfaden mit der Schaltfläche Element hinzufügen ist die Inhaltssuche eingeschränkt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Suchgrundlagen](search-implementation.md) -Seite für Entwickler.
