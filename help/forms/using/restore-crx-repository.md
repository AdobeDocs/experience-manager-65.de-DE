---
title: Das beschädigte CRX-Repository kann nicht wiederhergestellt werden, das auf den JEE-Cluster-Server anwendbar ist
description: Schritte zum Wiederherstellen eines beschädigten CRX-Repositorys
source-git-commit: a7d125503b0bd3c52cb3a959e2f0dde1a69cbe2b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 8%

---

# Beschädigtes CRX-Repository kann nicht wiederhergestellt werden {#unable-to-restore-corrupt-crx-repository}

## Problem {#issue}

Für AEM Forms, das auf JEE mit RDB-Persistenz bereitgestellt wird, ist es erforderlich, dass AEM Forms-Hostcomputer und Datenbankcomputer in absoluter Zeitsynchronisierung synchronisiert werden. Wenn die Uhren jedoch aus irgendeinem Grund nicht mehr synchronisiert werden, wird das CRX-Repository beschädigt und die URLs werden nicht mehr zugänglich. Der Fehler als `AuthenticationsupportService missing` tritt in Protokolldateien auf.

## Lösung {#solution}

Führen Sie zur Behebung dieses Problems folgende Schritte durch:
1. Navigieren Sie zu  [https://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

1. Suchen Sie die `oak-core` Bundle erstellen und überprüfen, ob es ausgeführt wird.

1. Starten Sie den `oak-core` Bundle, wenn es nicht ausgeführt wird. Wenn die Schaltfläche &quot;Pause&quot;vor dem `oak-core` Bundle, dann zeigt es an, dass das Bundle im Ausführungsstatus ist.

1. Wenn das Problem weiterhin nicht behoben ist, stellen Sie aus dem CRX-Repository aus der Sicherung wieder her oder erstellen Sie das CRX-Repository neu, wenn keine Sicherung verfügbar ist.

   >[!NOTE]
   >
   >Führen Sie die Sicherung Ihres CRX-Repositorys durch, bevor Sie die oben genannten Schritte durchführen.

## Gilt für {#applies-to}

Diese Lösung gilt für:

* AEM Forms on JEE Cluster Server


