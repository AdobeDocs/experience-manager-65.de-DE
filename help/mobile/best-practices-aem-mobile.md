---
title: Best Practices für AEM Mobile On-demand Services
description: Erfahren Sie mehr über Best Practices und Richtlinien, die kompetenten Adobe Experience Manager (AEM)-Entwicklerinnen und -Entwicklern für Sites helfen, die Mobile-App-Vorlagen und -Komponenten erstellen möchten.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 63ceaba6-b796-4c13-a86d-f0609ec679c9
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 4%

---

# Best Practices {#best-practices}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Das Erstellen einer AEM Mobile On-demand Services-App unterscheidet sich vom Erstellen einer App, die direkt in der Cordova-Shell (oder PhoneGap) ausgeführt wird. Die Entwickler sollten mit den folgenden Themen vertraut sein:

* Standardmäßig unterstützte Plug-ins und Adobe Experience Manager (AEM) Mobile-spezifische Plug-ins.

>[!NOTE]
>
>Ausführliche Informationen zu Plug-ins finden Sie in den folgenden Ressourcen:
>
>* [Verwenden von Cordova-Plug-ins in AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/cordova-api.html)
>* [Verwenden von AEM Mobile-spezifischen Cordova-fähigen Plug-ins](https://helpx.adobe.com/digital-publishing-solution/help/app-runtime-api.html)
>

* Vorlagen, die Plug-in-Funktionen verwenden, sollten so geschrieben werden, dass sie weiterhin im Browser autorisiert werden können, ohne dass die Plug-in-Brücke vorhanden ist.

   * Warten Sie beispielsweise auf die Funktion *deviceReady*, bevor Sie auf die API eines Plug-ins zugreifen.

## Richtlinien für AEM-Entwickler {#guidelines-for-aem-developers}

Die folgenden Richtlinien helfen kompetenten AEM-Entwicklerinnen und -Entwicklern für Sites, die Mobile-App-Vorlagen und -Komponenten erstellen möchten:

**Strukturieren Sie AEM-Site-Vorlagen, um die Wiederverwendung und Erweiterbarkeit zu fördern**

* Mehrere Komponentenskriptdateien sollten einer einzigen monolithischen Skriptdatei vorgezogen werden

   * Es werden mehrere leere Erweiterungspunkte bereitgestellt, z. B. *customheaderlibs.html* und *customfooterlibs.html*, mit denen der Entwickler die Seitenvorlage ändern und dabei so wenig Kern-Code wie möglich duplizieren kann
   * Vorlagen können dann über den Mechanismus „sling:resourceSuperType *von Sling erweitert und* werden

* Sightly/HTL gegenüber JSP als Vorlagensprache bevorzugen

   * Die Verwendung dieser Option fördert die Trennung von Code und Markup, bietet integrierten XSS-Schutz und verfügt über eine vertrautere Syntax

**Für Leistung auf dem Gerät optimieren**

* Artikelspezifisches Skript und Stylesheets sollten mithilfe der Inhaltssynchronisierungsvorlage dps-article in die Artikel-Payload aufgenommen werden
* Skript- und Stylesheets, die von mehr als einem Artikel gemeinsam verwendet werden, sollten über die Vorlage dps-HTMLResources contentSync in gemeinsame Ressourcen aufgenommen werden
* Referenzieren Sie keine externen Skripte, die Render-Blocker sind

>[!NOTE]
>
>Ausführlichere Informationen zum Blockieren externer Skripte für Render finden Sie [hier](https://developers.google.com/speed/docs/insights/BlockingJS).

**Bevorzugen Sie App-spezifische Client-seitige JS- und CSS-Bibliotheken gegenüber Web-spezifischen**

* So vermeiden Sie Overhead in Bibliotheken wie jQuery Mobile für eine große Bandbreite an Geräten und Browsern
* Wenn eine Vorlage in der Webansicht einer App ausgeführt wird, haben Sie die Kontrolle über die Plattformen und Versionen, die die App unterstützen wird, und über das Wissen, dass JavaScript-Unterstützung vorhanden ist. Beispielsweise sollten Sie Ionic (nur CSS) gegenüber jQuery Mobile und Onsen UI gegenüber Bootstrap bevorzugen.

>[!NOTE]
>
>Um mehr über jQuery Mobile zu erfahren, klicken Sie [hier](https://jquerymobile.com/browser-support/1.4/).

**Mikrobibliotheken gegenüber Full-Stack bevorzugen**

* Die Zeit, die benötigt wird, um Ihre Inhalte auf das Glas des Geräts zu bringen, wird von jeder Bibliothek verlangsamt, von der Ihre Artikel abhängen. Diese Verlangsamung wird noch verstärkt, wenn eine neue Web-Ansicht verwendet wird, um jeden Artikel zu rendern, sodass jede Bibliothek von Grund auf neu initialisiert werden muss
* Wenn Ihre Artikel nicht als SPA (Single Page Apps) erstellt wurden, müssen Sie wahrscheinlich keine Full-Stack-Bibliothek wie Angular einfügen
* Bevorzugen Sie kleinere, universelle Bibliotheken, die Ihnen helfen, die Interaktivität hinzuzufügen, die Ihre Seite erfordert, wie [Fastclick](https://github.com/ftlabs/fastclick) oder [Velocity.js](https://velocityjs.org)

**Minimieren der Größe der Artikel-Payload**

* Verwenden Sie möglichst kleine Assets, die effektiv den größten von Ihnen unterstützten Viewport mit einer angemessenen Auflösung abdecken können
* Verwenden Sie ein Tool wie *ImageOptim* auf Ihren Bildern, damit Sie überschüssige Metadaten entfernen können

## Vorwärtskommen {#getting-ahead}

Weitere Informationen zu den beiden anderen Rollen und Zuständigkeiten finden Sie in den folgenden Ressourcen:

* [Administrator](/help/mobile/aem-mobile.md)
* [Author](/help/mobile/aem-mobile-on-demand.md)
