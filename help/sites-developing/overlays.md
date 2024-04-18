---
title: Überlagerungen
description: Adobe Experience Manager nutzt Überlagerungen, um die Konsolen und andere Funktionen zu erweitern und anzupassen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: e57a6971-6a6f-427b-a8cd-a2f2e8cdf9e2
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 100%

---

# Überlagerungen{#overlays}

Adobe Experience Manager (AEM) – wie zuvor schon CQ – nutzt seit Langem Überlagerungen, um [Konsolen](/help/sites-developing/customizing-consoles-touch.md) und andere Funktionen (beispielsweise die [Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md)) zu erweitern und anzupassen.

Überlagerung ist ein Begriff, der in unterschiedlichen Zusammenhängen verwendet wird. In diesem Zusammenhang (d. h. Erweitern von AEM) ist damit die Übernahme der vordefinierten Funktionen und das Anwenden eigener Definitionen (zum Anpassen der Standardfunktionen) gemeint.

In einer Standardinstanz befinden sich die vordefinierten Funktionen unter `/libs` und es empfiehlt sich, die Überlagerung (Anpassungen) unter der Verzweigung `/apps` zu definieren. AEM verwendet einen Suchpfad, um eine Ressource zu finden, wobei zuerst die Verzweigung `/apps` und dann die Verzweigung `/libs` durchsucht wird ([der Suchpfad kann konfiguriert werden](#configuring-the-search-paths)). Durch diesen Mechanismus hat Ihre Überlagerung (und die dort definierten Anpassungen) Priorität.

Seit Einführung von AEM 6.0 wurden Änderungen an der Implementierung und Verwendung von Überlagerungen vorgenommen:

* Ab AEM 6.0 – für [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)-bezogene Überlagerungen (d. h. die Touch-optimierte Benutzeroberfläche)

   * Methode

      * Rekonstruieren Sie die entsprechende `/libs`-Struktur unter `/apps`.

        Dies erfordert keine 1:1-Kopie, der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) wird verwendet, um die erforderlichen Originaldefinitionen zu vergleichen. Sling Resource Merger stellt Dienste für den Zugriff auf und die Zusammenführung von Ressourcen mittels Diff(Differenzierungs)-Mechanismen bereit.

      * Nehmen Sie etwaige Änderungen unter `/apps` vor.

   * Vorteile

      * Robuster gegenüber Änderungen unter `/libs`.
      * Definieren Sie nur neu, was erforderlich ist.

* Überlagerungen, die nicht aus Granite stammen, und Überlagerungen in Versionen vor AEM 6.0

   * Methode

      * Kopieren der Inhalte von `/libs` nach `/apps`

        Kopieren Sie die gesamte Unterverzweigung, einschließlich Eigenschaften.

      * Nehmen Sie etwaige Änderungen unter `/apps` vor.

   * Nachteile

      * Obwohl Ihre Änderungen nicht verloren gehen, wenn sich etwas unter `/libs` ändert, müssen Sie möglicherweise bestimmte Änderungen in Ihrer Überlagerung unter `/apps` neu erstellen.

>[!CAUTION]
>
>Der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) und die zugehörigen Methoden können nur mit [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) verwendet werden. Das bedeutet, dass die Erstellung einer Überlagerung mit einem Strukturgerüst nur für die standardmäßige Touch-optimierte Benutzeroberfläche geeignet ist.
>
>Bei Überlagerungen für andere Bereiche (einschließlich der klassischen Benutzeroberfläche) werden der entsprechende Knoten sowie die gesamte Unterstruktur kopiert und die erforderlichen Änderungen vorgenommen.

Überlagerungen empfehlen sich für viele Änderungsvorgänge, beispielsweise das [Konfigurieren von Konsolen](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) oder das [Erstellen der Auswahlkategorie für den Asset-Browser im seitlichen Bedienfeld](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (wird bei der Seitenbearbeitung verwendet). Sie sind aus folgenden Gründen erforderlich:

* Sie dürfen ***keine* Änderungen in der Verzweigung `/libs`**vornehmen.
Jegliche Änderungen, die Sie vornehmen, können verloren gehen, da diese Verzweigung in den folgenden Fällen Änderungen unterliegt:

   * Upgrades in Ihrer Instanz
   * Anwendung eines Hotfix
   * Installation eines Feature Pack

* Diese bündeln Ihre Änderungen an einem Speicherort und erleichtern Ihnen so das Nachverfolgen, Migrieren, Sichern oder Debuggen Ihrer Änderungen, falls erforderlich.

## Konfigurieren von Suchpfaden {#configuring-the-search-paths}

Bei Überlagerungen ist die bereitgestellte Ressource ein Aggregat der abgerufenen Ressourcen und Eigenschaften, abhängig von den definierbaren Suchpfaden:

* Der **Suchpfad des Ressourcen-Resolvers** wie in der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für die **Apache Sling-Resource Resolver Factory** definiert

   * Die Reihenfolge der Suchpfade von oben nach unten gibt die jeweiligen Prioritäten an.
   * In einer Standardinstallation sind die primären Standardwerte `/apps`, `/libs`. Der Inhalt von `/apps` hat also eine höhere Priorität als der von `/libs`, (d. h., er *überlagert* diesen).

* Zwei Dienstbenutzer benötigen JCR:READ-Zugriff auf den Speicherort der Skripte. Diese Benutzer sind: „components-search-service“ (verwendet von den com.day.cq.wcm.coreto access/cache-Komponenten) und „sling-scripting“ (verwendet von „org.apache.sling.servlets.resolver“, um Servlets zu finden).
* Die folgende Konfiguration muss außerdem so konfiguriert werden, dass sie dem Speicherort für Ihre Skripte entspricht (in diesem Beispiel unter /etc, /libs oder /apps).

  ```
  PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
  resource.resolver.searchpath=["/etc","/apps","/libs"]
  resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
  ```

* Schließlich muss noch der Servlet-Resolver konfiguriert werden (in diesem Beispiel auch, um „/etc“ hinzuzufügen).

  ```
  PID = org.apache.sling.servlets.resolver.SlingServletResolver
  servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
  ```

## Anwendungsbeispiele {#example-of-usage}

Überlagerungen kommen unter anderem in den folgenden Fällen zur Anwendung:

* [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md)
* [Anpassung des Seiten-Authorings](/help/sites-developing/customizing-page-authoring-touch.md)
