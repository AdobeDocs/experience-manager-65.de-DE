---
title: Es ist nicht möglich, ein beschädigtes CRX-Repository, das auf einen JEE-Cluster-Server anwendbar ist, wiederherzustellen.
description: Erfahren Sie, wie Sie ein beschädigtes CRX-Repository wiederherstellen können.
exl-id: 212f61f1-360f-4abe-b874-055ec65454c7
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 100%
---
# Beschädigtes CRX-Repository kann nicht wiederhergestellt werden {#unable-to-restore-corrupt-crx-repository}

## Problem {#issue}

Bei AEM Forms on JEE, das eine relationale Datenbank verwendet, sollten die Zeit auf dem Computer, der AEM Forms hostet, und die relationale Datenbank immer absolut synchron sein. Wenn die Zeit auf diesen Computern nicht mehr synchronisiert ist, kann das CRX-Repository von AEM Forms auf dem JEE-Server unzugänglich werden. Es kann beschädigt erscheinen und nicht mehr über die URL zugänglich sein. Die Fehler `AuthenticationsupportService missing` wird protokolliert.

## Voraussetzungen {#prerequisites}

Erstellen Sie eine Sicherungskopie Ihres CRX-Repositorys, bevor Sie die unten genannten Schritte durchführen.

## Lösung {#solution}

1. Rufen Sie `https://[AEM Forms Server]:[port]/system/console/bundles` auf.

1. Suchen Sie das `oak-core`-Paket und überprüfen Sie, ob es ausgeführt wird.

1. Starten Sie das `oak-core`-Paket neu, wenn es nicht ausgeführt wird. Wenn das Symbol ![Schaltfläche „Pause“](/help/forms/using/assets/stop.png) vor dem `oak-core`-Paket angezeigt wird, ist dies ein Anzeichen dafür, dass das Paket ausgeführt wird.

1. Wenn das Problem immer noch nicht behoben ist, stellen Sie das CRX-Repository aus der Sicherungskopie wieder her oder erstellen Sie das CRX-Repository neu, wenn keine Sicherungskopie verfügbar ist.


## Gilt für {#applies-to}

Diese Lösung gilt für den AEM Forms auf JEE-Cluster.
