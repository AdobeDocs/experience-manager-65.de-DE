---
title: Überlagerungen
seo-title: Überlagerungen
description: AEM nutzt das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen zu erweitern und anzupassen.
seo-description: AEM nutzt das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen zu erweitern und anzupassen.
uuid: d14c08fe-04c0-4925-8c99-c6644357919d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0470b74c-2c34-4327-afed-b95eefb1d521
exl-id: e57a6971-6a6f-427b-a8cd-a2f2e8cdf9e2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 67%

---

# Überlagerungen{#overlays}

AEM (und zuvor CQ) nutzt seit Langem Überlagerungen, um die [Konsolen](/help/sites-developing/customizing-consoles-touch.md) und andere Funktionen (beispielsweise die [Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md)) zu erweitern und anzupassen.

Der Begriff „Überlagerung“ kann in unterschiedlichen Zusammenhängen verwendet werden. In diesem Zusammenhang (der Erweiterung von AEM) ist damit die Übernahme der vordefinierten Funktionen und das Anwenden eigener Definitionen (zum Anpassen der Standardfunktionen) gemeint.

In einer Standardinstanz befindet sich die vordefinierte Funktion unter `/libs`. Es wird empfohlen, Ihre Überlagerung (Anpassungen) unter der Verzweigung `/apps` zu definieren. AEM verwendet einen Suchpfad, um eine Ressource zu finden, indem zuerst die Verzweigung `/apps` und dann die Verzweigung `/libs` gesucht wird (der Suchpfad [kann konfiguriert werden](#configuring-the-search-paths)). Durch diesen Mechanismus hat Ihre Überlagerung  (und die dort definierten Anpassungen) Priorität.

Seit Einführung von AEM 6.0 wurden Änderungen an der Implementierung und Verwendung von Überlagerungen vorgenommen:

* Ab AEM 6.0 – für [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)-bezogene Überlagerungen (d. h. Touch-optimierte Benutzeroberfläche)

   * Methode

      * Rekonstruieren Sie die entsprechende `/libs`-Struktur unter `/apps`.

         Dies erfordert keine 1:1-Kopie, der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) wird verwendet, um die erforderlichen Originaldefinitionen zu vergleichen. Der Sling Resource Merger stellt Dienste für den Zugriff auf und die Zusammenführung von Ressourcen mittels Vergleichsmechanismen bereit.

      * Nehmen Sie beliebige Änderungen unter `/apps` vor.
   * Vorteile

      * Robuster gegenüber Änderungen unter `/libs`.
      * Nur die erforderlichen Aspekte müssen neu definiert werden.


* Überlagerungen, die nicht aus Granite stammen, und Überlagerungen in Versionen vor AEM 6.0 

   * Methode

      * Kopieren Sie den Inhalt von `/libs` in `/apps` .

         Sie müssen die gesamte Unterverzweigung einschließlich der Eigenschaften kopieren.

      * Nehmen Sie beliebige Änderungen unter `/apps` vor.
   * Nachteile

      * Obwohl Ihre Änderungen nicht verloren gehen, wenn sich etwas unter `/libs` ändert, müssen Sie möglicherweise bestimmte Änderungen neu erstellen, die in Ihrer Überlagerung unter `/apps` auftreten.


>[!CAUTION]
>
>Der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) und die zugehörigen Methoden können nur mit [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) verwendet werden. Das bedeutet, dass die Erstellung einer Überlagerung mit einem Strukturgerüst nur für die standardmäßige Touch-optimierte Benutzeroberfläche geeignet ist.
>
>Bei Überlagerungen für andere Bereiche (einschließlich der klassischen Benutzeroberfläche) werden der entsprechende Knoten und die gesamte Unterstruktur kopiert und die erforderlichen Änderungen vorgenommen.

Überlagerungen empfehlen sich für viele Änderungen, beispielsweise das [Konfigurieren von Konsolen](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) oder [Erstellen der Auswahlkategorie für den Asset-Browser im seitlichen Bedienfeld](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (wird bei der Seitenbearbeitung verwendet). Sie sind aus folgenden Gründen erforderlich:

* Sie ***dürfen nicht* Änderungen in der Verzweigung `/libs` vornehmen **Alle Änderungen, die Sie vornehmen, können verloren gehen, da sich diese Verzweigung ändern kann, wenn Sie:

   * Bei Upgrades auf Ihrer Instanz
   * Beim Anwenden eines Hotfix
   * Beim Installieren eines Feature Packs

* Überlagerungen bündeln Ihre Änderungen an zentraler Stelle und erleichtern es Ihnen, Ihre Änderungen zu verfolgen, zu migrieren, zu sichern und/oder zu debuggen.

## Konfigurieren von Suchpfaden  {#configuring-the-search-paths}

Bei Überlagerungen ist die bereitgestellte Ressource ein Aggregat der abgerufenen Ressourcen und Eigenschaften, abhängig von den definierbaren Suchpfaden:

* Der **Suchpfad des Ressourcen-Resolvers** wie in der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für die **Apache Sling-ResourceResolverFactory** definiert

   * Die Reihenfolge der Suchpfade von oben nach unten gibt die jeweiligen Prioritäten an.
   * In einer Standardinstallation sind die Hauptstandardwerte `/apps`, `/libs` - daher hat der Inhalt von `/apps` eine höhere Priorität als der von `/libs` (d. h. *Überlagerungen*).

* Zwei Dienstbenutzer benötigen JCR:READ-Zugriff auf den Speicherort der Skripte. Diese Benutzer sind: components-search-service (verwendet von den com.day.cq.wcm.coreto access/cache-Komponenten) und sling-scripting (verwendet von org.apache.sling.servlets.resolver, um Servlets zu finden).
* Die folgende Konfiguration muss auch entsprechend der Stelle konfiguriert werden, an der Sie Ihre Skripte platzieren (in diesem Beispiel unter /etc, /libs oder /apps).

   ```
   PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
   resource.resolver.searchpath=["/etc","/apps","/libs"]
   resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
   ```

* Schließlich muss auch der Servlet-Resolver konfiguriert werden (in diesem Beispiel auch um /etc hinzuzufügen).

   ```
   PID = org.apache.sling.servlets.resolver.SlingServletResolver
   servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
   ```

## Anwendungsbeispiele {#example-of-usage}

Überlagerungen kommen unter anderem in den folgenden Fällen zur Anwendung:

* [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md)
* [Anpassung des Seiten-Authorings](/help/sites-developing/customizing-page-authoring-touch.md)
