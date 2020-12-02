---
title: 'Bearbeiter               '
seo-title: 'Bearbeiter               '
description: Erfahren Sie, wie Sie zurück zum klassischen Benutzeroberflächen-Editor wechseln.
seo-description: Erfahren Sie, wie Sie zurück zum klassischen Benutzeroberflächen-Editor wechseln.
uuid: ca8b07e7-014f-428e-82bd-87f3aae12f6e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 54903f3a-1e7e-4083-a2c9-b2ea4555d7fc
docset: aem65
translation-type: tm+mt
source-git-commit: 954c1d5b06b54d59f523483ce5c1af36c2083a76
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 90%

---


# Bearbeiter               {#editor}

Standardmäßig ist die Möglichkeit, zum klassischen Benutzeroberflächen-Editor zu wechseln, deaktiviert.

Gehen Sie wie folgt vor, um im Menü **Seiteninformationen** die Option **In klassischer Benutzeroberfläche öffnen** wieder zu aktivieren.

1. Suchen Sie mithilfe von CRXDE Lite den folgenden Knoten:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Beispiel

   ` [https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui)`

1. Erstellen Sie eine Überlagerung mit der Option **Überlagerungsknoten**. Beispiel:

   * **Pfad**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Pfad für Überlagerung**: `/apps/`
   * **Übereinstimmungstypen abgleichen**: aktiv (Kontrollkästchen aktivieren)

1. Fügen Sie die folgende Multiwert-Texteigenschaft zum überlagerten Knoten hinzu:

   `sling:hideProperties = ["granite:hidden"]`

1. Die Option **In klassischer Benutzeroberfläche öffnen** steht nun wieder beim Bearbeiten von Seiten im Menü **Seiteninformationen** zur Verfügung.

   ![](assets/syui-03-2019-02-27-15-19-48.png)