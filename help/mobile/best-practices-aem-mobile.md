---
title: Best Practices
seo-title: Best Practices
description: Auf dieser Seite lernen Sie bewährte Verfahren und Richtlinien kennen, die erfahrenen AEM-Entwicklern bei Sites helfen, die Vorlagen und Komponenten für mobile Apps erstellen möchten.
seo-description: Auf dieser Seite lernen Sie bewährte Verfahren und Richtlinien kennen, die erfahrenen AEM-Entwicklern bei Sites helfen, die Vorlagen und Komponenten für mobile Apps erstellen möchten.
uuid: 7733c8b1-a88c-455c-8080-f7add4205b92
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a0647696-72c3-409b-85ba-9275d8f99cff
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Best Practices {#best-practices}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Das Erstellen einer AEM Mobile-On-Demand-Dienste-App unterscheidet sich vom Erstellen einer App, die direkt in der Cordova-Shell (oder PhoneGap) ausgeführt wird. Die Entwickler sollten mit Folgendem vertraut sein:

* Plugins, die standardmäßig unterstützt werden, sowie AEM Mobile-spezifische Plugins.

>[!NOTE]
>
>Ausführliche Informationen zu Plugins finden Sie in den folgenden Ressourcen:
>
>* [Verwenden von Cordova-Zusatzmodulen in AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/cordova-api.html)
>* [Verwenden von AEM Mobile-spezifischen Cordova-kompatiblen Zusatzmodulen](https://helpx.adobe.com/digital-publishing-solution/help/app-runtime-api.html)
>



* Vorlagen, die Plugin-Funktionen verwenden, sollten so geschrieben werden, dass sie im Browser immer noch autorisiert werden können, ohne dass die Plugin-Brücke vorhanden ist.

   * Achten Sie beispielsweise darauf, auf die Funktion &quot; *deviceready* &quot;zu warten, bevor Sie versuchen, auf die API eines Plugins zuzugreifen.

## Richtlinien für AEM-Entwickler {#guidelines-for-aem-developers}

Die folgenden Richtlinien helfen erfahrenen AEM-Entwicklern bei Sites, die Vorlagen und Komponenten für mobile Apps erstellen möchten:

**Strukturieren von AEM-Sitevorlagen zur Förderung der Wiederverwendung und Erweiterbarkeit**

* Mehrere Komponentenskriptdateien über eine einzige monolithische

   * Es stehen eine Reihe leerer Erweiterungspunkte zur Verfügung, z. B. *customheaderlibs.html* und *customfooterlibs.html*, mit denen Entwickler die Seitenvorlage ändern und dabei möglichst wenig Kerncode duplizieren können
   * Vorlagen können dann über den Sling-Mechanismus *sling:resourceSuperType* erweitert und angepasst werden

* Sightly/HTL über JSP als Vorlagensprache

   * Dies fördert die Trennung von Code und Markup, bietet integrierten XSS-Schutz und hat eine vertrautere Syntax

**Optimieren Sie die Leistung auf dem Gerät.**

* Artikelspezifische Skript- und Stylesheets sollten mithilfe der ContentSync-Vorlage für den Artikel in die Artikelnutzlast einbezogen werden
* Skript- und Stylesheets, die von mehr als einem Artikel gemeinsam verwendet werden, sollten über die Vorlage &quot;dps-HTMLResources contentsync&quot;in gemeinsam genutzten Ressourcen enthalten sein
* Kein Verweis auf externe Skripte, die render-locking sind

>[!NOTE]
>
>Ausführlichere Informationen zum Render-Blockieren externer Skripte finden Sie [hier](https://developers.google.com/speed/docs/insights/BlockingJS).

**Stellen Sie anwendungsspezifische clientseitige JS- und CSS-Bibliotheken über webspezifische**

* Vermeidung von Mehraufwand in Bibliotheken wie jQuery Mobile für die Handhabung einer großen Bandbreite von Geräten und Browsern
* Wenn eine Vorlage in der Webansicht einer App ausgeführt wird, haben Sie die Kontrolle über die Plattformen und Versionen, die von der App unterstützt werden, sowie das Wissen, dass JavaScript-Unterstützung vorhanden sein wird. Nehmen wir beispielsweise an, dass Sie Ionic (vielleicht nur CSS) gegenüber jQuery Mobile und Onsen UI anstelle von Bootstrap bevorzugen.

>[!NOTE]
>
>Weitere Informationen zu jQuery Mobile erhalten Sie [hier](https://jquerymobile.com/browser-support/1.4/).

**Mikrobibliotheken über Vollstapel bevorzugen**

* Die Zeit, die benötigt wird, um Ihre Inhalte auf das Glas des Geräts zu bringen, wird durch jede Bibliothek, von der Ihre Artikel abhängen, verlangsamt. Diese Verlangsamung wird noch verstärkt, wenn ein neuer Webview zum Rendern jedes Artikels verwendet wird. Daher muss jede Bibliothek erneut von Grund auf initialisiert werden
* Wenn Ihre Artikel nicht als SPAs (Einzelseitenanwendungen) erstellt wurden, müssen Sie wahrscheinlich keine vollständige Stapelbibliothek wie Angular einschließen
* Verwenden Sie kleinere Bibliotheken mit einem Verwendungszweck, um die Interaktivität hinzuzufügen, die Ihre Seite benötigt, wie [Fastclick](https://github.com/ftlabs/fastclick) oder [Velocity.js](https://velocityjs.org)

**Größe der Artikelnutzlast minimieren**

* Verwenden Sie die kleinstmöglichen Assets, die effektiv den größten Viewport abdecken können, den Sie unterstützen werden, mit einer angemessenen Auflösung
* Verwenden Sie ein Werkzeug wie *ImageOptim* auf Ihren Bildern, um überschüssige Metadaten zu entfernen

## Vorwärts {#getting-ahead}

Weitere Informationen zu den beiden anderen Rollen und Verantwortlichkeiten finden Sie in den folgenden Ressourcen:

* [Administrator](/help/mobile/aem-mobile.md)
* [Autor](/help/mobile/aem-mobile-on-demand.md)
