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
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 66%

---


# Grundlagen der Ordnerstruktur {#understanding-the-folder-structure}

AEM Forms Workspace-Komponenten basieren auf einer MVC-Architektur mit Backbone. Jede Komponente verfügt über eine Datei für:

* Das Modell, das die Geschäftslogik enthält.
* Die Vorlage als HTML-Datei mit Steuerelementen der Benutzeroberfläche.
* Die Ansicht, die als Steuerungklasse für die Vorlage fungiert.

Die Elemente für alle Komponenten werden in der unten beschriebenen Ordnerstruktur gespeichert. Um auf die Assets zuzugreifen, melden Sie sich bei der CRXDE Lite an und navigieren Sie zu `/libs/ws/js/runtime/`.

**models** Enthält Backbone-Modelle.

**** viewsEnthält Backbone-Ansichten.

**** templatesEnthält nur die HTML-Vorlagen für die Komponenten.

**Routen** Enthält universelle Routen. Der Ordner „templates“ unter „routes“ enthält den HTML-Code und die Verweise auf die Komponenten.

**** servicesEnthält die Dienstschnittstelle zum Aufrufen von Adobe Experience Manager-Server-APIs am REST-Endpunkt.

**** utilEnthält allgemeine Dienstprogramme, die von mehreren Komponenten verwendet werden können.
