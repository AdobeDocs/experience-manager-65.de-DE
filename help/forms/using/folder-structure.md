---
title: Grundlagen der Ordnerstruktur
description: Grundlegendes zur Ordnerstruktur des Quell-Codes von AEM Forms Workspace zur Anpassung.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: a4c1d3d8-477e-4edf-9dde-4ef9c766be5a
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
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
