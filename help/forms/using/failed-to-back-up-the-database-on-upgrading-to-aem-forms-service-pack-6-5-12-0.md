---
title: Fehlschlagen des Datenbank-Backups beim Upgrade auf 6.5.12.0 für MySQL.
description: Wenn Benutzende ein Upgrade auf Experience Manager 6.5.12.0 durchführen und auf „MySQL aktualisieren“ klicken, kann der Konfigurations-Manager die vorherige Experience Manager Forms-Datenbank nicht sichern.
exl-id: 1af000fa-439b-4ffd-8b5a-3ba45f0c524c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '105'
ht-degree: 100%

---

# Fehlschlagen des Datenbank-Backups beim Upgrade auf 6.5.12.0 für MySQL {#issue}

Wenn Benutzende ein Upgrade auf Experience Manager 6.5.12.0 durchführen und auf „MySQL aktualisieren“ klicken, kann der Konfigurations-Mnager die vorherige Experience Manager Forms-Datenbank nicht sichern. Es wird folgender Fehler angezeigt:

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Gilt für {#applies-to}

* Experience Manager 6.5 Forms

## Lösung {#solution}

Um das Problem zu beheben, erhöhen Sie den max_packet_size-Wert der Datenbank auf 100 MB oder wie in der Datei „my.ini“ unter {AEM_HOME}/mysql erforderlich.
