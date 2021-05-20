---
title: Grundlagen der Ordnerstruktur
seo-title: Grundlagen der Ordnerstruktur
description: Grundlegendes zur Ordnerstruktur von AEM Forms Workspace-Quellcode zur Anpassung.
seo-description: Grundlegendes zur Ordnerstruktur von AEM Forms Workspace-Quellcode zur Anpassung.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: a4c1d3d8-477e-4edf-9dde-4ef9c766be5a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 66%

---

# Grundlagen der Ordnerstruktur {#understanding-the-folder-structure}

AEM Forms Workspace-Komponenten basieren auf einer MVC-Architektur mit Backbone. Jede Komponente verfügt über eine Datei für:

* Das Modell, das die Geschäftslogik enthält.
* Die Vorlage als HTML-Datei mit Steuerelementen der Benutzeroberfläche.
* Die Ansicht, die als Steuerungklasse für die Vorlage fungiert.

Die Elemente für alle Komponenten werden in der unten beschriebenen Ordnerstruktur gespeichert. Um auf die Assets zuzugreifen, melden Sie sich bei CRXDE Lite an und navigieren Sie zu `/libs/ws/js/runtime/`.

**** modelsEnthält Backbone-Modelle.

**** viewsEnthält Backbone-Ansichten.

**** templatesEnthält nur die HTML-Vorlagen für die Komponenten.

**** routesEnthält universelle Routen. Der Ordner „templates“ unter „routes“ enthält den HTML-Code und die Verweise auf die Komponenten.

**** servicesEnthält die Dienstschnittstelle zum Aufrufen von Adobe Experience Manager-Server-APIs am REST-Endpunkt.

**** utilEnthält allgemeine Dienstprogramme, die von mehreren Komponenten verwendet werden können.
