---
title: Überlagerungen
seo-title: Überlagerungen
description: AEM nutzt Überlagerungen, um die Konsolen und andere Funktionen zu erweitern und anzupassen.
seo-description: AEM nutzt Überlagerungen, um die Konsolen und andere Funktionen zu erweitern und anzupassen.
uuid: d14c08fe-04c0-4925-8c99-c6644357919d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0470b74c-2c34-4327-afed-b95eefb1d521
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Überlagerungen{#overlays}

AEM (und zuvor CQ) nutzt seit Langem Überlagerungen, um die [Konsolen](/help/sites-developing/customizing-consoles-touch.md) und andere Funktionen (beispielsweise die [Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md)) zu erweitern und anzupassen.

Überlagerung ist ein Begriff, der in unterschiedlichen Zusammenhängen verwendet werden kann. In diesem Zusammenhang (der Erweiterung von AEM) ist damit die Übernahme der vordefinierten Funktionen und das Anwenden eigener Definitionen (zum Anpassen der Standardfunktionen) gemeint.

In a standard instance the predefined functionality is held under `/libs` and it is recommended practice to define your overlay (customizations) under the `/apps` branch. AEM uses a search path to find a resource, searching first the `/apps` branch and then the `/libs` branch (the [search path can be configured](#configuring-the-search-paths)). Durch diesen Mechanismus hat Ihre Überlagerung (und die dort definierten Anpassungen) Priorität.

Seit Einführung von AEM 6.0 wurden Änderungen an der Implementierung und Verwendung von Überlagerungen vorgenommen:

* Ab AEM 6.0 – für [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)-bezogene Überlagerungen (d. h. Touch-optimierte Benutzeroberfläche)

   * Methode

      * Reconstruct the appropriate `/libs` structure under `/apps`.

         Dies erfordert keine 1:1-Kopie, der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) wird verwendet, um die erforderlichen Originaldefinitionen zu vergleichen. Der Sling Resource Merger stellt Dienste für den Zugriff auf und die Zusammenführung von Ressourcen mittels Vergleichsmechanismen bereit.

      * Make any changes under `/apps`.
   * Vorteile

      * Robuster gegenüber Änderungen unter `/libs`.
      * Nur die erforderlichen Aspekte müssen neu definiert werden.


* Überlagerungen, die nicht aus Granite stammen, und Überlagerungen in Versionen vor AEM 6.0 

   * Methode

      * Kopieren Sie den Inhalt von `/libs` in `/apps`

         Sie müssen die gesamte Unterverzweigung einschließlich der Eigenschaften kopieren.

      * Make any changes under `/apps`.
   * Nachteile

      * Although your changes will not be lost when something changes under `/libs`, you might have to recreate certain changes that occur in your overlay under `/apps`.


>[!CAUTION]
>
>Der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) und die zugehörigen Methoden können nur mit [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) verwendet werden. Das bedeutet, dass die Erstellung einer Überlagerung mit einem Strukturgerüst nur für die standardmäßige Touch-optimierte Benutzeroberfläche geeignet ist.
>
>Bei Überlagerungen für andere Bereiche (einschließlich der klassischen Benutzeroberfläche) werden der entsprechende Knoten und die gesamte Unterstruktur kopiert und die erforderlichen Änderungen vorgenommen.

Überlagerungen empfehlen sich für viele Änderungen, beispielsweise das [Konfigurieren von Konsolen](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) oder [Erstellen der Auswahlkategorie für den Asset-Browser im seitlichen Bedienfeld](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (wird bei der Seitenbearbeitung verwendet). Sie sind aus folgenden Gründen erforderlich:

* You ***must not *make changes in the`/libs`branch **Any changes you do make may be lost, because this branch is liable to changes whenever you:

   * Bei Upgrades auf Ihrer Instanz
   * Beim Anwenden eines Hotfix
   * Beim Installieren eines Feature Packs

* Überlagerungen bündeln Ihre Änderungen an zentraler Stelle und erleichtern es Ihnen, Ihre Änderungen zu verfolgen, zu migrieren, zu sichern und/oder zu debuggen.

## Konfigurieren von Suchpfaden {#configuring-the-search-paths}

Bei Überlagerungen ist die bereitgestellte Ressource ein Aggregat der abgerufenen Ressourcen und Eigenschaften, abhängig von den definierbaren Suchpfaden:

* Der **Suchpfad des Ressourcen-Resolvers** wie in der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für die **Apache Sling-ResourceResolverFactory** definiert

   * Die Reihenfolge der Suchpfade von oben nach unten gibt die jeweiligen Prioritäten an.
   * In a standard installation the primary defaults are `/apps`, `/libs` - so the content of `/apps` has a higher priority than that of `/libs` (i.e. it *overlays* it).

* Zwei Dienstbenutzer benötigen JCR:READ-Zugriff auf den Speicherort der Skripten. Diese Benutzer sind: components-search-service (wird von den com.day.cq.wcm.coreTo-Access/cache-Komponenten verwendet) und sling-scripting (wird von org.apache.sling.servlets.resolver verwendet, um Servlets zu finden).
* Die folgende Konfiguration muss auch entsprechend der Stelle konfiguriert werden, an der Sie Ihre Skripte ablegen (in diesem Beispiel unter /etc, /libs oder /apps).

   ```
   PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
   resource.resolver.searchpath=["/etc","/apps","/libs"]
   resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
   ```

* Schließlich muss auch der Servlet-Resolver konfiguriert werden (in diesem Beispiel auch um /etc hinzuzufügen)

   ```
   PID = org.apache.sling.servlets.resolver.SlingServletResolver
   servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
   ```

## Anwendungsbeispiele {#example-of-usage}

Überlagerungen kommen unter anderem in den folgenden Fällen zur Anwendung:

* [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md)
* [Anpassen der Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md)

