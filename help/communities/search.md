---
title: Suchfunktion
seo-title: Search Feature
description: Hinzufügen und Konfigurieren der Suche zu einer Communities-Site
seo-description: Adding and configuring Search to a Communities site
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
exl-id: e252b0e5-a2f8-468e-ac8c-951a5b0f2e32
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 31%

---

# Suchfunktion {#search-feature}

Die Suchfunktion kann für zahlreiche andere Funktionen wie beispielsweise Foren eingesetzt werden und bietet somit die Möglichkeit, bestimmte Inhalte aufzufinden.

Wird die Funktion zum Durchsuchen der von Community-Mitgliedern veröffentlichten Beiträge – hier „user generated content“ (UGC, benutzergenerierter Inhalt) genannt – hinzugefügt, stehen zwei Komponenten zur Verfügung: [Suche](#search) und [Suchergebnisse](#search-results).

Die Seite, die die `Search Results` -Komponente unterstützt sowohl die Suche als auch die Anzeige von Ergebnissen.

Die Seite, die die `Search` -Komponente bietet einen Ort zum Starten einer Suche mit Ergebnissen, die auf der `Search Results` Seite.

Die Suchfunktion kann gemeinsam mit anderen Funktionen verwendet werden, sodass Site-Besucher und Mitglieder in der Lage sind, Inhalte einzusehen.

## Suchen {#search-features}

### Hinzufügen einer Suche zu einer Seite {#add-search-to-a-page}

So fügen Sie eine `Search` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / Search` und ziehen Sie sie an die gewünschte Stelle auf einer Seite. Verwendung von `Search` eine zweite Seite für die `Search Results.`

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die erforderliche clientseitige Bibliothek `cq.social.hbs.search`, enthalten ist, wird die `Search` wird angezeigt.

![add-search](assets/add-search.png)

### Konfigurieren der hinzugefügten Suche {#configure-the-added-search}

Wählen Sie die platzierte `Search` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![config](assets/configure-new.png)

Unter dem **[!UICONTROL Sucheinstellungen]** angeben, wie die Pfade bei der Eingabe einer Abfrage durch einen Besucher durchsucht werden sollen.

![search-settings](assets/search-settings.png)

* **[!UICONTROL Suchpfade]** Durch Hinzufügen von Suchpfaden mithilfe der Schaltfläche „Element hinzufügen“ wird die Elementsuche eingeschränkt. Um beispielsweise die Suche auf ein bestimmtes Forum zu beschränken, wählen Sie eine Forumskomponente aus, die auf einer Seite platziert wird:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Ergebnisseite]**
Die Ergebnisse werden auf einer separaten Seite angezeigt, die mithilfe des Browsers angegeben wird, um eine Seite auszuwählen, die die 
`Search Results` component.

## Suchergebnisse {#search-results}

### Hinzufügen von Suchergebnissen zu einer Seite {#add-search-results-to-a-page}

So fügen Sie eine `Search Results` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Search Results`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite. Im Gegensatz zur Komponente „Suche“ wird hier keine zweite Seite benötigt, da die Suchergebnisse auf der gleichen Seite angezeigt werden können.

Wenn Sie die Suche an einer anderen Stelle auf der Website verwenden, wird diese eine Seite mit `Search Results` kann so konfiguriert werden, dass `Result Page` für alle oder alle Instanzen von `Search`.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die erforderliche clientseitige Bibliothek `cq.social.hbs.search`, enthalten ist, wird die `Search Result` wird angezeigt:

![Suchergebnis](assets/search-result1.png)

### Konfigurieren hinzugefügter Suchergebnisse {#configure-the-added-search-result}

Wählen Sie die platzierte `Search Results` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Unter dem **[!UICONTROL Suchergebniseinstellungen]** -Registerkarte können Sie festlegen, welche Pfade bei der Suche einbezogen werden sollen, wenn ein Besucher eine Abfrage eingibt.

![search-result-settings](assets/search-result-settings.png)

* **[!UICONTROL Suchergebnisse pro Seite]**

   Definieren Sie die Anzahl der Themen/Beiträge, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Suchpfade]**

   Durch Hinzufügen von Suchpfaden mit der Schaltfläche Element hinzufügen ist die Inhaltssuche eingeschränkt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Suchgrundlagen](search-implementation.md) für Entwickler.
