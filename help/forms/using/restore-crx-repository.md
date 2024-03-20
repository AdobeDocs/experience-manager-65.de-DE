---
title: Es ist nicht möglich, ein beschädigtes CRX-Repository, das auf einen JEE-Cluster-Server anwendbar ist, wiederherzustellen.
description: Erfahren Sie, wie Sie ein beschädigtes CRX-Repository wiederherstellen können.
exl-id: 212f61f1-360f-4abe-b874-055ec65454c7
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 87%

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

Diese Lösung gilt für den AEM Forms on JEE-Cluster.
