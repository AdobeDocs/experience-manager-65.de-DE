---
title: Suchfunktion
seo-title: Suchfunktion
description: Hinzufügen und Konfigurieren der Suche zu einer Communities-Site
seo-description: Hinzufügen und Konfigurieren der Suche zu einer Communities-Site
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
translation-type: tm+mt
source-git-commit: 6ab91667ad668abf80ccf1710966169b3a187928
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 31%

---


# Suchfunktion {#search-feature}

Die Suchfunktion kann für zahlreiche andere Funktionen wie beispielsweise Foren eingesetzt werden und bietet somit die Möglichkeit, bestimmte Inhalte aufzufinden.

Wird die Funktion zum Durchsuchen der von Community-Mitgliedern veröffentlichten Beiträge – hier „user generated content“ (UGC, benutzergenerierter Inhalt) genannt – hinzugefügt, stehen zwei Komponenten zur Verfügung: [Suche](#search) und [Suchergebnisse](#search-results).

The page that includes the `Search Results` component supports both searching and the display of results.

The page that includes the `Search` component provides a place to launch a search with results appearing on the `Search Results` page.

Die Suchfunktion kann gemeinsam mit anderen Funktionen verwendet werden, sodass Site-Besucher und Mitglieder in der Lage sind, Inhalte einzusehen.

## Suche {#search-features}

### Hinzufügen einer Suche zu einer Seite {#add-search-to-a-page}

Um einer Seite im Autorenmodus eine `Search` Komponente hinzuzufügen, verwenden Sie den Komponenten-Browser, um sie zu suchen `Communities / Search` und auf eine Seite zu ziehen. Die Verwendung `Search` erfordert eine zweite Seite für die Variable `Search Results.`

For necessary information, visit [Communities Components Basics](basics.md).

When the required client-side library, `cq.social.hbs.search`, is included, this is how the `Search` component will appear.

![add-search](assets/add-search.png)

### Konfigurieren der hinzugefügten Suche {#configure-the-added-search}

Select the placed `Search` component to access and select the `Configure` icon which opens the edit dialog.

![Konfirue](assets/configure-new.png)

Under the **[!UICONTROL Search Settings]** tab, specify how what paths are are search when a query is entered by a visitor.

![search-settings](assets/search-settings.png)

* **[!UICONTROL Suchpfade]** Durch Hinzufügen von Suchpfaden mithilfe der Schaltfläche „Element hinzufügen“ wird die Elementsuche eingeschränkt. As an example, to limit the search to a specific forum, select a forum component placed within a page:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Ergebnisseite]** Die Ergebnisse werden auf einer separaten Seite angezeigt, die durch Auswahl einer Seite mit der Variablen 
`Search Results` component.

## Search Results {#search-results}

### Hinzufügen von Suchergebnissen zu einer Seite {#add-search-results-to-a-page}

To add a `Search Results` component to a page in author mode, use the component browser to locate

* `Communities / Search Results`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite. Im Gegensatz zur Komponente „Suche“ wird hier keine zweite Seite benötigt, da die Suchergebnisse auf der gleichen Seite angezeigt werden können.

If using Search elsewhere within the website, this one page with `Search Results` may be configured to be the `Result Page` for any or all instances of `Search`.

For necessary information, visit [Communities Components Basics](basics.md).

When the required client-side library, `cq.social.hbs.search`, is included, this is how the `Search Result` component will appear:

![search-result](assets/search-result1.png)

### Konfigurieren hinzugefügter Suchergebnisse {#configure-the-added-search-result}

Select the placed `Search Results` component to access and select the `Configure` icon which opens the edit dialog.

![configure](assets/configure-new.png)

Under the **[!UICONTROL Search Result Settings]** tab, it is possible to specify what paths are included in the search when a query is entered by a visitor.

![search-result-settings](assets/search-result-settings.png)

* **[!UICONTROL Suchergebnisse pro Seite]**

   Definieren Sie die Anzahl der Themen/Beiträge pro Seite. Der Standardwert ist 10.

* **[!UICONTROL Suchpfade]**

   Durch Hinzufügen von Suchpfaden mit der Schaltfläche &quot;Hinzufügen Element&quot;ist die Inhaltssuche eingeschränkt.

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Search Essentials](search-implementation.md) page for developers.
