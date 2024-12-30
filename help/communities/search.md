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

Die Suchfunktion arbeitet mit verschiedenen anderen Funktionen wie Foren zusammen, um die Suche nach Inhalten zu ermöglichen.

Beim Hinzufügen der Möglichkeit, Beiträge zu durchsuchen, die von Community-Mitgliedern eingegeben wurden (als benutzergenerierte Inhalte (User Generated Content, UGC) bezeichnet), gibt es zwei Komponenten: [Suche](#search) und [Suchergebnisse](#search-results).

Die Seite, die die `Search Results`-Komponente enthält, unterstützt sowohl die Suche als auch die Anzeige von Ergebnissen.

Die Seite, die die `Search` enthält, bietet einen Ort, an dem Sie eine Suche starten können, bei der die Ergebnisse auf der `Search Results` Seite angezeigt werden.

Die Suchfunktion kann mit jeder anderen Funktion verwendet werden, die es Besuchern und Mitgliedern der Site ermöglicht, Inhalte anzuzeigen.

## Suchen {#search-features}

### Hinzufügen einer Suche zu einer Seite {#add-search-to-a-page}

Um einer Seite im Autorenmodus eine `Search` Komponente hinzuzufügen, verwenden Sie den Komponenten-Browser, um `Communities / Search` zu suchen und sie auf einer Seite abzulegen. Die Verwendung von `Search` erfordert eine zweite Seite für die `Search Results.`

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die erforderliche Client-seitige Bibliothek `cq.social.hbs.search` enthalten ist, wird die `Search` Komponente wie folgt angezeigt.

![add-search](assets/add-search.png)

### Konfigurieren der hinzugefügten Suche {#configure-the-added-search}

Wählen Sie die platzierte `Search` aus, auf die Sie zugreifen möchten, und wählen Sie das `Configure` aus, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

Geben **[!UICONTROL auf der Registerkarte]** Sucheinstellungen“ an, welche Pfade durchsucht werden sollen, wenn eine Abfrage von einem Besucher eingegeben wird.

![search-settings](assets/search-settings.png)

* **[!UICONTROL Suchpfade]**
Durch Hinzufügen von Suchpfaden mit der Schaltfläche Element hinzufügen wird die Inhaltssuche eingeschränkt. Um die Suche beispielsweise auf ein bestimmtes Forum zu beschränken, wählen Sie eine Forenkomponente aus, die in einer Seite platziert wird:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Ergebnisseite]**
Die Ergebnisse werden auf einer separaten Seite angezeigt, die mithilfe des Browsers angegeben wird, um eine Seite auszuwählen, die die `Search Results` enthält.

## Suchergebnisse {#search-results}

### Suchergebnisse zu einer Seite hinzufügen {#add-search-results-to-a-page}

Um einer Seite im Autorenmodus eine `Search Results` Komponente hinzuzufügen, suchen Sie im Komponenten-Browser nach

* `Communities / Search Results`

und ziehen Sie sie auf eine Seite. Im Gegensatz zur Such-Komponente ist keine zweite Seite erforderlich, da die Ergebnisse auf derselben Seite angezeigt werden.

Wenn Sie die Suche an einer anderen Stelle auf der Website verwenden, kann diese eine Seite mit `Search Results` so konfiguriert werden, dass sie die `Result Page` für alle oder alle Instanzen von `Search` ist.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die erforderliche Client-seitige Bibliothek `cq.social.hbs.search` enthalten ist, wird die `Search Result` Komponente wie folgt angezeigt:

![search-result](assets/search-result1.png)

### Konfigurieren des hinzugefügten Suchergebnisses {#configure-the-added-search-result}

Wählen Sie die platzierte `Search Results` aus, auf die Sie zugreifen möchten, und wählen Sie das `Configure` aus, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

Auf der Registerkarte **[!UICONTROL Suchergebniseinstellungen]** können Sie angeben, welche Pfade in die Suche einbezogen werden sollen, wenn eine Abfrage von einem Besucher eingegeben wird.

![search-result-settings](assets/search-result-settings.png)

* **[!UICONTROL Suchergebnisse pro Seite]**

  Anzahl der angezeigten Themen/Beiträge pro Seite definieren. Der Standardwert ist 10.

* **[!UICONTROL Suchpfade]**

  Durch Hinzufügen von Suchpfaden mit der Schaltfläche Element hinzufügen wird die Inhaltssuche eingeschränkt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Search Essentials](search-implementation.md) für Entwickler.
