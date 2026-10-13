---
title: Benennungskonventionen für das Testen von Assets
description: Knoten im Repository unterliegen den Benennungskonventionen des Java Content Repository. Adobe Experience Manager schreibt jedoch weitere Konventionen für den Namen von Asset-Knoten vor.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
exl-id: bb6a5913-0871-47c7-8641-936e98920ec0
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 100%
---
# Benennungskonventionen für das Testen von Assets{#naming-conventions-for-assets-testing}

Knoten im Repository unterliegen den Benennungskonventionen des [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Adobe Experience Manager schreibt aber weitere Konventionen für den Namen von Asset-Knoten vor.

## Klassische Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche weist stärkere Einschränkungen auf:

* Prüft den Asset-Namen bei expliziten Knotennamen, wenn:

  * ein Asset-Titel für die Konvertierung in den Knotennamen bereitgestellt wird
  * ein expliziter Knotenname angegeben ist

* Gültige Zeichen (nur diese Zeichen sind tatsächlich gültig, wenn ein Asset in der klassischen Benutzeroberfläche erstellt wird):

  * „a“ bis „z“
  * „A“ bis „Z“
  * „0“ bis „9“
  * _ (Unterstrich)
  * `-` (Strich/Minus)
