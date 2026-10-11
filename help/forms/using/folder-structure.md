---
title: Grundlagen der Ordnerstruktur
description: Grundlegendes zur Ordnerstruktur des Quell-Codes von AEM Forms Workspace zur Anpassung.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: a4c1d3d8-477e-4edf-9dde-4ef9c766be5a
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%
---
# Grundlagen der Ordnerstruktur {#understanding-the-folder-structure}

AEM Forms Workspace-Komponenten basieren auf der MVC-Architektur mit Backbone. Jede Komponente verfügt über eine Datei für:

* ein Modell, das die Business-Logik enthält.
* eine Vorlage, hier eine HTML-Datei, die Steuerelemente für die Benutzeroberfläche enthält.
* eine Ansicht, die als Controller-Klasse für die Vorlage fungiert.

Die Assets für alle Komponenten werden in der unten beschriebenen Ordnerstruktur platziert. Um auf die Elemente zuzugreifen, melden Sie sich bei CRXDE Lite an und navigieren Sie zu `/libs/ws/js/runtime/`.

**models** Enthält Backbone-Modelle.

**views** Enthält Backbone-Ansichten.

**templates** Enthält nur die HTML-Vorlagen für die Komponenten.

**routes** Enthält universelle Routen. Der Ordner „templates“ unter „routes“ enthält den HTML-Code und die Verweise auf die Komponenten.

**services** Enthält die Serviceschnittstelle zum Aufrufen von Adobe Experience Manager-Server-APIs am REST-Endpunkt.

**util** Enthält generische Serviceprogramme, die von mehreren Komponenten verwendet werden können.
