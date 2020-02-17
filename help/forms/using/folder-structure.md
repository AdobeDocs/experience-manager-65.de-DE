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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Grundlagen der Ordnerstruktur {#understanding-the-folder-structure}

AEM Forms Workspace-Komponenten basieren auf einer MVC-Architektur mit Backbone. Jede Komponente verfügt über eine Datei für:

* Das Modell, das die Geschäftslogik enthält.
* Die Vorlage als HTML-Datei mit Steuerelementen der Benutzeroberfläche.
* Die Ansicht, die als Steuerungklasse für die Vorlage fungiert.

Die Elemente für alle Komponenten werden in der unten beschriebenen Ordnerstruktur gespeichert. To access the assets, log in to CRXDE Lite and browse to `/libs/ws/js/runtime/`.

**models** Enthält Backbone-Modelle.

**Ansichten** Enthält Backbone-Ansichten.

**templates** Enthält nur die HTML-Vorlagen für die Komponenten.

**Routen** Enthält universelle Routen. Der Ordner „templates“ unter „routes“ enthält den HTML-Code und die Verweise auf die Komponenten.

**services** Enthält die Dienstschnittstelle zum Aufrufen von Adobe Experience Manager Server-APIs für REST-Endpunkte.

**util** Enthält allgemeine Dienstprogramme, die von mehreren Komponenten verwendet werden können.

**[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)**
