---
title: Fehlgeschlagene Sicherung der vorherigen Datenbank in AEM Forms 6.5.12.0.
description: Wenn ein Benutzer auf Experience Manager 6.5.12.0 aktualisiert und auf "MySQL aktualisieren"klickt, kann der Konfigurationsmanager die vorherige Experience Manager Forms-Datenbank nicht sichern.
source-git-commit: d232bfdad7b8413eb015f6fe5dd3442cebf1001d
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 7%

---

# Problem (#issue)

Wenn ein Benutzer ein Upgrade auf Experience Manager 6.5.12.0 durchführt und auf &quot;MySQL aktualisieren&quot;klickt, kann der Konfigurationsmanager die vorherige Experience Manager Forms-Datenbank nicht sichern, wird der Fehler angezeigt:

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Gilt für {#applies-to}

* Experience Manager 6.5 Forms

## Lösung {#solution}

Um das Problem zu beheben, erhöhen Sie die Größe max_packet_size der Datenbank auf 100 M oder wie in der Datei my.ini unter {AEM_HOME}/mysql.
