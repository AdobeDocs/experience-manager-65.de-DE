---
title: Vorschau von Seiten mit ContextHub-Daten
seo-title: Vorschau von Seiten mit ContextHub-Daten
description: In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können Sie mithilfe der Leiste Store-Daten bearbeiten und Inhalte in der Vorschau ansehen.
seo-description: In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können Sie mithilfe der Leiste Store-Daten bearbeiten und Inhalte in der Vorschau ansehen.
uuid: 0150555a-0a92-4692-a706-bbe59fd34d6a
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: f281ef8c-0831-470c-acb7-189f20452a50
exl-id: 78673609-8cbc-4b4b-953e-56c31ea1b4ea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 96%

---

# Vorschau von Seiten mit ContextHub-Daten {#previewing-pages-using-contexthub-data}

In der [ContextHub](/help/sites-developing/contexthub.md)-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können mithilfe der Leiste Store-Daten bearbeitet werden. Die ContextHub-Symbolleiste eignet sich besonders für die Vorschau von Inhalten, die durch Daten im ContextHub Store gesteuert werden.

Diese Symbolleiste besteht aus einer Reihe Benutzeroberflächenmodi, die eines oder mehrere Oberflächenmodule enthalten.

* Benutzeroberflächenmodi werden durch die Symbole links in der Symbolleiste dargestellt. Klicken oder tippen Sie auf ein solches Symbol, zeigt die Symbolleiste die im Modus enthaltenen Benutzeroberflächenmodule an.
* In den Oberflächenmodulen werden Daten aus einem oder mehreren ContextHub Stores dargestellt. Einige Oberflächenmodule ermöglichen die Bearbeitung von Store-Daten.

Es werden verschiedene Benutzeroberflächenmodi und -module von ContextHub installiert. Möglicherweise hat Ihr Administrator [ContextHub so konfiguriert](/help/sites-developing/ch-configuring.md), dass andere Module als die hier gezeigten dargestellt werden.

![screen_shot_2018-03-23at093446](assets/screen_shot_2018-03-23at093446.png)

## Einblenden der ContextHub-Symbolleiste {#revealing-the-contexthub-toolbar}

Die ContextHub-Symbolleiste ist im Vorschaumodus verfügbar. Die Symbolleiste wird nur für Autoreninstanzen angezeigt, wenn diese Funktion zuvor vom Administrator aktiviert wurde.

![screen_shot_2018-03-23at093730](assets/screen_shot_2018-03-23at093730.png)

1. Klicken oder tippen Sie bei zur Bearbeitung geöffneter Seite auf die Vorschauoption.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Klicken oder tippen Sie auf das ContextHub-Symbol, um die Symbolleiste einzublenden.

   ![](do-not-localize/screen_shot_2018-03-23at093621.png)

## Benutzeroberflächenmodul-Funktionen {#ui-module-features}

Jedes Benutzeroberflächenmodul verfügt über eigene Funktionen, es stehen jedoch auch folgende gemeinsam genutzte Funktionen zur Verfügung. Da sich die Benutzeroberflächenmodule erweitern lassen, können Entwickler je nach Wunsch weitere Funktionen einbauen.

### Inhalt der Symbolleiste   {#toolbar-content}

Mit den Benutzeroberflächenmodulen können in der Symbolleiste Daten aus einem oder mehr ContextHub-Stores eingeblendet werden. Benutzeroberflächenmodule lassen sich anhand ihres Symbols oder Titels identifizieren.

![screen_shot_2018-03-23at093936](assets/screen_shot_2018-03-23at093936.png)

### Popup-Inhalt {#popup-content}

In einigen Benutzeroberflächenmodulen wird ein Popup-Overlay angezeigt, wenn darauf geklickt oder getippt wird. In der Regel enthält das Popup zusätzlich zu den in der Symbolleiste verfügbaren Informationen weitere Daten.

![screen_shot_2018-03-23at094003](assets/screen_shot_2018-03-23at094003.png)

### Popup-Formulare {#popup-forms}

In einigen Popup-Overlays der Benutzeroberflächenmodule befinden sich Formularelemente, mit deren Hilfe Sie Daten im ContextHub Store bearbeiten können. Steuern diese Store-Daten Seiteninhalte, können Sie mit dem Formular Änderungen vornehmen, die sich dann in den Seiteninhalten widerspiegeln.

### Vollbildmodus   {#fullscreen-mode}

Die Popup-Überlagerung kann ein Symbol enthalten, auf das Sie klicken oder tippen können, um den Popup-Inhalt so zu erweitern, dass er das gesamte Browser-Fenster oder den Bildschirm einnimmt.

![](do-not-localize/chlimage_1-18.png)
