---
title: Fehler beim Sichern der Datenbank beim Upgrade auf 6.5.12.0 für MySQL.
description: Wenn ein Benutzer ein Upgrade auf Experience Manager 6.5.12.0 vornimmt und auf „MySQL aktualisieren“ klickt, kann der Konfigurations-Manager die vorherige Experience Manager Forms-Datenbank nicht sichern.
exl-id: 1af000fa-439b-4ffd-8b5a-3ba45f0c524c
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 94663796-0ee7-58b9-84f4-b425ebb69e83
    internal-label: AEM Forms on JEE
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
source-wordcount: '102'
ht-degree: 15%
---
# Fehlschlagen des Datenbank-Backups beim Upgrade auf 6.5.12.0 für MySQL {#issue}

Wenn ein Benutzer auf Experience Manager 6.5.12.0 aktualisiert und auf „MySQL aktualisieren“ klickt, kann der Konfigurations-Manager die vorherige Experience Manager Forms-Datenbank nicht sichern. Es wird der Fehler angezeigt:

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Gilt für {#applies-to}

* Experience Manager 6.5 Forms

## Lösung {#solution}

Um das Problem zu beheben, erhöhen Sie die max_package_size der Datenbank auf 100 M oder nach Bedarf in der Datei my.ini unter {AEM_HOME}/mysql.
