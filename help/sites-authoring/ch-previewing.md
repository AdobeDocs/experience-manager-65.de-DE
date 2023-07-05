---
title: Vorschau von Seiten mit ContextHub-Daten
seo-title: Previewing Pages Using ContextHub Data
description: In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können Sie mithilfe der Leiste Store-Daten bearbeiten und Inhalte in der Vorschau ansehen.
seo-description: The ContextHub toolbar displays data from ContextHub stores and enables you to change store data and  is useful for previewing content
uuid: 0150555a-0a92-4692-a706-bbe59fd34d6a
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: f281ef8c-0831-470c-acb7-189f20452a50
exl-id: 78673609-8cbc-4b4b-953e-56c31ea1b4ea
source-git-commit: 75c6bb87bb06c5ac9378ccebf193b5416c080bb1
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 54%

---

# Vorschau von Seiten mit ContextHub-Daten{#previewing-pages-using-contexthub-data}

Die [ContextHub](/help/sites-developing/contexthub.md) in der Symbolleiste werden Daten aus ContextHub-Stores angezeigt und Sie können Store-Daten ändern. Die ContextHub-Symbolleiste ist für die Vorschau von Inhalten nützlich, die durch Daten in einem ContextHub-Store bestimmt werden.

Die Symbolleiste besteht aus einer Reihe von Benutzeroberflächenmodi, die ein oder mehrere Benutzeroberflächenmodule enthalten.

* Benutzeroberflächenmodi sind Symbole, die links in der Symbolleiste angezeigt werden. Wenn Sie auf ein Symbol klicken oder tippen, zeigt die Symbolleiste die darin enthaltenen UI-Module an.
* Benutzeroberflächenmodule zeigen Daten aus einem oder mehreren ContextHub-Stores an. Einige Benutzeroberflächenmodule ermöglichen es Ihnen auch, gespeicherte Daten zu bearbeiten.

Es werden verschiedene Benutzeroberflächenmodi und -module von ContextHub installiert. Möglicherweise hat Ihr Admin [ContextHub so konfiguriert](/help/sites-developing/ch-configuring.md), dass andere Module als die hier gezeigten dargestellt werden.

![screen_shot_2018-03-23at093446](assets/screen_shot_2018-03-23at093446.png)

## Einblenden der ContextHub-Symbolleiste {#revealing-the-contexthub-toolbar}

Die ContextHub-Symbolleiste ist im Vorschaumodus verfügbar. Die Symbolleiste wird nur für Autoreninstanzen angezeigt, wenn diese Funktion zuvor vom Admin aktiviert wurde.

![screen_shot_2018-03-23at093730](assets/screen_shot_2018-03-23at093730.png)

1. Klicken oder tippen Sie bei zur Bearbeitung geöffneter Seite auf die Vorschauoption.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Klicken oder tippen Sie auf das ContextHub-Symbol, um die Symbolleiste einzublenden.

   ![Context-Hub](do-not-localize/screen_shot_2018-03-23at093621.png)

## Benutzeroberflächenmodul-Funktionen {#ui-module-features}

Jedes UI-Modul bietet unterschiedliche Funktionen, die folgenden Arten von Funktionen sind jedoch üblich. Da UI-Module erweiterbar sind, kann Ihr Entwickler nach Bedarf andere Funktionen implementieren.

### Inhalt der Symbolleiste {#toolbar-content}

Mit den Benutzeroberflächenmodulen können in der Symbolleiste Daten aus einem oder mehr ContextHub-Stores eingeblendet werden. Benutzeroberflächenmodule lassen sich anhand ihres Symbols oder Titels identifizieren.

![screen_shot_2018-03-23at093936](assets/screen_shot_2018-03-23at093936.png)

### Popup-Inhalt {#popup-content}

Einige UI-Module zeigen ein Popup-Overlay an, wenn darauf geklickt oder getippt wird. In der Regel enthält das Popup zusätzlich zu den in der Symbolleiste verfügbaren Informationen weitere Daten.

![screen_shot_2018-03-23at094003](assets/screen_shot_2018-03-23at094003.png)

### Popup-Formulare {#popup-forms}

In einigen Popup-Overlays der Benutzeroberflächenmodule befinden sich Formularelemente, mit deren Hilfe Sie Daten im ContextHub Store bearbeiten können. Wenn der Seiteninhalt durch die Speicherdaten bestimmt wird, können Sie das Formular verwenden und Änderungen am Seiteninhalt beobachten.

### Vollbildmodus {#fullscreen-mode}

Die Popup-Überlagerung kann ein Symbol enthalten, auf das Sie klicken oder tippen können, um den Popup-Inhalt so zu erweitern, dass er das gesamte Browser-Fenster oder den Bildschirm einnimmt.

![Vollbild](do-not-localize/chlimage_1-18.png)
