---
title: Benennungskonventionen für Assets-Tests
seo-title: Naming conventions for assets
description: Knoten im Repository unterliegen den Benennungskonventionen des Java Content Repository. Adobe Experience Manager schreibt aber weitere Konventionen für den Namen von Asset-Knoten vor.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: bb6a5913-0871-47c7-8641-936e98920ec0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 100%

---

# Benennungskonventionen für Assets-Tests{#naming-conventions-for-assets-testing}

Knoten im Repository unterliegen den Benennungskonventionen des [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Adobe Experience Manager schreibt aber weitere Konventionen für den Namen von Asset-Knoten vor.

## Klassische Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche gibt strengere Einschränkungen vor:

* Prüft den Asset-Namen bei expliziten Knotennamen, wenn:

   * ein Asset-Titel für die Konvertierung in den Knotennamen bereitgestellt wird
   * ein expliziter Knotenname angegeben ist

* Gültige Zeichen (nur diese Zeichen sind tatsächlich gültig, wenn ein Asset in der klassischen Benutzeroberfläche erstellt wird):

   * „a“ bis „z“
   * „A“ bis „Z“
   * „0“ bis „9“
   * _ (Unterstrich)
   * `-` (Strich/Minus)
