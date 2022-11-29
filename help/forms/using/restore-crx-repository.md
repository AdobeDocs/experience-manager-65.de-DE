---
title: Das beschädigte CRX-Repository kann nicht wiederhergestellt werden, das auf den JEE-Cluster-Server anwendbar ist
description: Schritte zum Wiederherstellen eines beschädigten CRX-Repositorys
exl-id: 212f61f1-360f-4abe-b874-055ec65454c7
source-git-commit: c4f776b08cb8cc8c6eea78a3757735e063bec20c
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 7%

---

# Beschädigtes CRX-Repository kann nicht wiederhergestellt werden {#unable-to-restore-corrupt-crx-repository}

## Problem {#issue}

Bei AEM Forms on JEE, das eine relationale Datenbank verwendet, sollte die Zeit auf dem Computer, auf dem AEM Forms und die relationale Datenbank gehostet werden, immer in absoluter Synchronisierung sein. Wenn die Zeit auf diesen Computern nicht mehr synchron ist, kann der Zugriff auf das CRX-Repository des AEM Forms on JEE-Servers nicht mehr möglich sein. Er kann beschädigt aussehen und über URL nicht mehr zugänglich sein. Die `AuthenticationsupportService missing` -Fehler protokolliert.

## Voraussetzungen {#prerequisites}

Führen Sie die Sicherung Ihres CRX-Repositorys durch, bevor Sie die unten genannten Schritte durchführen.

## Lösung {#solution}

Führen Sie zur Behebung dieses Problems folgende Schritte durch:
1. Rufen Sie `https://[AEM Forms Server]:[port]/system/console/bundles` auf.

1. Suchen Sie die `oak-core` Bundle erstellen und überprüfen, ob es ausgeführt wird.

1. Starten Sie den `oak-core` Bundle, wenn es nicht ausgeführt wird. Wenn  ![Schaltfläche &quot;Pause&quot;](/help/forms/using/assets/stop.png) -Symbol vor dem `oak-core` Bundle, dann zeigt es an, dass das Bundle im Ausführungsstatus ist.

1. Wenn das Problem weiterhin nicht behoben ist, stellen Sie aus dem CRX-Repository aus dem Backup wieder her oder erstellen Sie das CRX-Repository neu, wenn das Backup nicht verfügbar ist.


## Gilt für {#applies-to}

Diese Lösung gilt für:

* AEM Forms on JEE-Cluster