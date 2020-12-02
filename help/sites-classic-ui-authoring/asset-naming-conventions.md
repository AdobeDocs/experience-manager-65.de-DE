---
title: Benennungskonventionen für Assets-Tests
seo-title: Benennungskonventionen für Assets
description: Knoten im Repository unterliegen Benennungskonventionen des Java Content Repository. Adobe Experience Manager schreibt aber weitere Konventionen für den Namen von Asset-Knoten vor.
seo-description: Knoten im Repository unterliegen Benennungskonventionen des Java Content Repository. Adobe Experience Manager schreibt aber weitere Konventionen für den Namen von Asset-Knoten vor.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 99%

---


# Benennungskonventionen für Assets testing{#naming-conventions-for-assets-testing}

Knoten im Repository unterliegen den Benennungskonventionen des [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Adobe Experience Manager schreibt aber weitere Konventionen für den Namen von Asset-Knoten vor.

## Klassische Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche weist stärkere Einschränkungen auf:

* Prüft den Asset-Namen bei expliziten Knotennamen, wenn:

   * ein Asset-Titel für die Konvertierung in den Knotennamen bereitgestellt wird
   * ein expliziter Knotenname angegeben wird

* Gültige Zeichen (nur diese Zeichen sind tatsächlich gültig, wenn ein Asset in der klassischen Benutzeroberfläche erstellt wird):

   * „a“ bis „z“
   * „A“ bis „Z“
   * „0“ bis „9“
   * _ (Unterstrich)
   * `-` (Strich/Minus)

