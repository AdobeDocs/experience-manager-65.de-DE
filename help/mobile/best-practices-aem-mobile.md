---
title: Best Practices für AEM Mobile On-demand Services
description: Erfahren Sie mehr über Best Practices und Richtlinien, die kompetenten Adobe Experience Manager-Entwicklern (AEM) bei Sites helfen, die Vorlagen und Komponenten für mobile Apps erstellen möchten.
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

Das Erstellen einer AEM Mobile On-demand Services-App unterscheidet sich vom Erstellen einer App, die direkt in der Cordova- (oder PhoneGap-)Shell ausgeführt wird. Die Entwickler sollten mit folgenden Themen vertraut sein:

* Plugins, die standardmäßig unterstützt werden, und Adobe Experience Manager (AEM) Mobile-spezifische Plug-ins.

>[!NOTE]
>
>Ausführliche Informationen zu Plug-ins finden Sie in den folgenden Ressourcen:
>
>* [Verwenden von Cordova-Plug-ins in AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/cordova-api.html)
>* [Verwenden von AEM Mobile-spezifischen Cordova-aktivierten Plug-ins](https://helpx.adobe.com/digital-publishing-solution/help/app-runtime-api.html)
>

* Vorlagen, die Plug-in-Funktionen verwenden, sollten so geschrieben werden, dass sie im Browser noch autorisiert werden können, ohne dass die Plug-in-Verbindung vorhanden ist.

   * Achten Sie beispielsweise darauf, auf die *Abflussgetreide* -Funktion, bevor versucht wird, auf die API eines Plug-ins zuzugreifen.

## Richtlinien für AEM Entwickler {#guidelines-for-aem-developers}

Die folgenden Richtlinien helfen zuständigen AEM-Entwicklern bei Sites, die mobile App-Vorlagen und -Komponenten erstellen möchten:

**Strukturieren AEM Sites-Vorlagen zur Förderung der Wiederverwendung und Erweiterbarkeit**

* Mehrere Komponentenskriptdateien über eine einzige monolithische

   * Es werden mehrere leere Erweiterungspunkte bereitgestellt, z. B. *customheaderlibs.html* und *customfooterlibs.html*, die es dem Entwickler ermöglichen, die Seitenvorlage zu ändern und dabei möglichst wenig Kerncode zu duplizieren
   * Vorlagen können dann über die von Sling *sling:resourceSuperType* Mechanismus

* Sightly/HTL über JSP als Vorlagensprache bevorzugen

   * Dadurch wird eine Trennung von Code und Markup gefördert, es bietet integrierten XSS-Schutz und eine vertrautere Syntax

**Optimieren der Leistung auf dem Gerät**

* Artikelspezifische Skript- und Stylesheets sollten in die Artikelnutzlast aufgenommen werden, indem die contentsync-Vorlage dps-article verwendet wird.
* Skript- und Stylesheets, die von mehr als einem Artikel gemeinsam verwendet werden, sollten über die Vorlage &quot;dps-HTMLResources contentsync&quot;in gemeinsam genutzten Ressourcen enthalten sein
* Referenzieren Sie keine externen Skripte, die Render-Blocking sind

>[!NOTE]
>
>Ausführlichere Informationen zu Render-Blocking-externen Skripten [here](https://developers.google.com/speed/docs/insights/BlockingJS).

**App-spezifische clientseitige JS- und CSS-Bibliotheken im Vergleich zu webspezifischen**

* So vermeiden Sie Mehraufwand in Bibliotheken wie jQuery Mobile für die Verarbeitung einer großen Bandbreite von Geräten und Browsern
* Wenn eine Vorlage in der Webansicht einer App ausgeführt wird, haben Sie die Kontrolle über die Plattformen und Versionen, die die App unterstützen wird, sowie über das Wissen, dass JavaScript-Unterstützung vorhanden sein wird. Nehmen wir beispielsweise an, dass Ionic (nur CSS) gegenüber jQuery Mobile und Onsen UI den Vorzug vor Bootstrap hat.

>[!NOTE]
>
>Um mehr über jQuery Mobile zu erfahren, klicken Sie auf [here](https://jquerymobile.com/browser-support/1.4/).

**Mikrobibliotheken über Vollstapel bevorzugen**

* Die Zeit, die benötigt wird, um Ihren Inhalt auf das Glas des Geräts zu bringen, wird von jeder Bibliothek verlangsamt, von der Ihre Artikel abhängen. Diese Verlangsamung wird verstärkt, wenn eine neue Webansicht zum Rendern jedes Artikels verwendet wird. Daher muss jede Bibliothek von Grund auf neu initialisiert werden
* Wenn Ihre Artikel nicht als SPA (Einzelseiten-Apps) erstellt wurden, müssen Sie wahrscheinlich keine Vollstapelbibliothek wie Angular einfügen
* Verwenden Sie kleinere, einzweckige Bibliotheken, die dazu beitragen, die für Ihre Seite erforderliche Interaktivität hinzuzufügen, z. B. [Fastclick](https://github.com/ftlabs/fastclick) oder [Velocity.js](https://velocityjs.org)

**Minimieren der Artikelnutzlast**

* Verwenden Sie die kleinstmöglichen Assets, die mit einer angemessenen Auflösung effektiv den größten unterstützten Viewport abdecken können.
* Verwenden Sie ein Tool wie *ImageOptim* auf Ihren Bildern, damit Sie überschüssige Metadaten entfernen können

## Erste Schritte {#getting-ahead}

Weitere Informationen zu den beiden anderen Rollen und Zuständigkeiten finden Sie in den folgenden Ressourcen:

* [Administrator](/help/mobile/aem-mobile.md)
* [Author](/help/mobile/aem-mobile-on-demand.md)
