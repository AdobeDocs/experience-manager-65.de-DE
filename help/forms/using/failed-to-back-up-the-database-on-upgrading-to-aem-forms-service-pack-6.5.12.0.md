---
title: Fehlschlagen der Sicherung der Datenbank während der Aktualisierung auf 6.5.12.0 für MySQL.
description: Wenn ein Benutzer auf Experience Manager 6.5.12.0 aktualisiert und auf "MySQL aktualisieren"klickt, kann der Konfigurationsmanager die vorherige Experience Manager Forms-Datenbank nicht sichern.
source-git-commit: a6b1e97fd694f0fa1396697c42d84daaa9a6ac68
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 6%

---

# Fehlschlagen der Sicherung der Datenbank während der Aktualisierung auf 6.5.12.0 für MySQL {#issue}

Wenn ein Benutzer ein Upgrade auf Experience Manager 6.5.12.0 durchführt und auf &quot;MySQL aktualisieren&quot;klickt, kann der Konfigurationsmanager die vorherige Experience Manager Forms-Datenbank nicht sichern, wird der Fehler angezeigt:

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Gilt für {#applies-to}

* Experience Manager 6.5 Forms

## Lösung {#solution}

Um das Problem zu beheben, erhöhen Sie die Größe max_packet_size der Datenbank auf 100 M oder wie in der Datei my.ini unter {AEM_HOME}/mysql.
