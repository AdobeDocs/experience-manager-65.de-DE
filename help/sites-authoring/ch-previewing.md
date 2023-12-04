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
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 84%

---

# Vorschau von Seiten mit ContextHub-Daten{#previewing-pages-using-contexthub-data}

In der [ContextHub](/help/sites-developing/contexthub.md)-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können mithilfe dieser Leiste Store-Daten bearbeitet werden. Die ContextHub-Symbolleiste ist für die Vorschau von Inhalten nützlich, die durch Daten in einem ContextHub-Store bestimmt werden.

Die Symbolleiste besteht aus einer Reihe von UI-Modi, die ein oder mehrere UI-Module enthalten.

* UI-Modi sind Symbole, die links in der Symbolleiste angezeigt werden. Wenn Sie auf ein Symbol klicken, zeigt die Symbolleiste die darin enthaltenen Benutzeroberflächenmodule an.
* UI-Module zeigen Daten aus einem oder mehreren ContextHub-Stores an. Einige UI-Module ermöglichen es Ihnen auch, Store-Daten zu bearbeiten.

Es werden verschiedene Benutzeroberflächenmodi und -module von ContextHub installiert. Möglicherweise hat Ihr Admin [ContextHub so konfiguriert](/help/sites-developing/ch-configuring.md), dass andere Module als die hier gezeigten dargestellt werden.

![screen_shot_2018-03-23at093446](assets/screen_shot_2018-03-23at093446.png)

## Einblenden der ContextHub-Symbolleiste {#revealing-the-contexthub-toolbar}

Die ContextHub-Symbolleiste ist im Vorschaumodus verfügbar. Die Symbolleiste wird nur für Autoreninstanzen angezeigt, wenn diese Funktion zuvor vom Admin aktiviert wurde.

![screen_shot_2018-03-23at093730](assets/screen_shot_2018-03-23at093730.png)

1. Wenn Ihre Seite zur Bearbeitung geöffnet ist, klicken Sie in der Symbolleiste auf Vorschau.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Um die Symbolleiste anzuzeigen, klicken Sie auf das Symbol ContextHub .

   ![Context-Hub](do-not-localize/screen_shot_2018-03-23at093621.png)

## Benutzeroberflächenmodul-Funktionen {#ui-module-features}

Jedes UI-Modul bietet unterschiedliche Funktionen, die folgenden Arten von Funktionen sind jedoch allgemein üblich. Da sich die UI-Module erweitern lassen, können Entwicklerinnen und Entwickler je nach Wunsch weitere Funktionen implementieren.

### Inhalt der Symbolleiste {#toolbar-content}

Mit den Benutzeroberflächenmodulen können in der Symbolleiste Daten aus einem oder mehr ContextHub-Stores eingeblendet werden. Benutzeroberflächenmodule lassen sich anhand ihres Symbols oder Titels identifizieren.

![screen_shot_2018-03-23at093936](assets/screen_shot_2018-03-23at093936.png)

### Popup-Inhalt {#popup-content}

Einige UI-Module zeigen ein überlagertes Popup an, wenn darauf geklickt oder getippt wird. In der Regel enthält das Popup zusätzlich zu den in der Symbolleiste verfügbaren Informationen weitere Daten.

![screen_shot_2018-03-23at094003](assets/screen_shot_2018-03-23at094003.png)

### Popup-Formulare {#popup-forms}

In einigen Popup-Overlays der Benutzeroberflächenmodule befinden sich Formularelemente, mit deren Hilfe Sie Daten im ContextHub Store bearbeiten können. Wenn Seiteninhalt durch die Store-Daten bestimmt wird, können Sie das Formular verwenden und Änderungen am Seiteninhalt beobachten.

### Vollbildmodus {#fullscreen-mode}

Popup-Überlagerungen können ein Symbol enthalten, auf das Sie klicken, um den Popup-Inhalt so zu erweitern, dass er das gesamte Browser-Fenster oder den gesamten Bildschirm umfasst.

![Vollbild](do-not-localize/chlimage_1-18.png)
