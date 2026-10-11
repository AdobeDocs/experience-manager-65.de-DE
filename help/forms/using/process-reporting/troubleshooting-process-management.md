---
title: Fehlerbehebung bei Process Reporting
description: Fehlerbehebung bei Problemen in Process Reporting von AEM Forms on JEE
page-status-flag: de-activated
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 165d4c69-d7ca-45f8-a9de-764cb8ecab7e
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
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 100%
---
# Fehlerbehebung bei Process Reporting {#troubleshooting-process-reporting}

## Probleme beim Erstellen von Filtern in Internet Explorer 9 unter Microsoft Windows 7 {#issues-faced-in-creating-filters-on-internet-explorer-on-microsoft-windows}

Wenn Sie Filter für vordefinierte Berichte erstellen, treten bei **Internet Explorer 9** in einer **Microsoft Windows 7**-Umgebung gelegentlich die folgenden Probleme auf:

* In der Dropdown-Liste im Feld „Wert“ werden eindeutige Kennungen anstelle der Werte angezeigt.
* Das Kalendersteuerelement im Feld „Wert“ zeigt japanische Zeichen an.
* Das Feld „Bedingung“ wird nicht angezeigt.
* Das Kalendersteuerelement im Feld „Wert“ wird nicht angezeigt.

### Auflösung {#resolution}

Tun Sie Folgendes, während Sie noch bei Process Reporting angemeldet sind:

1. Löschen Sie den Browsercache.
1. Aktualisieren Sie das Browser-Fenster.
