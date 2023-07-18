---
title: Überlagerungen
description: Adobe Experience Manager verwendet das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen zu erweitern und anzupassen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: e57a6971-6a6f-427b-a8cd-a2f2e8cdf9e2
source-git-commit: 26c0411d6cc16f4361cfa9e6b563eba0bfafab1e
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 37%

---

# Überlagerungen{#overlays}

Adobe Experience Manager (AEM) - und davor CQ - verwendet seit langem das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die [Konsolen](/help/sites-developing/customizing-consoles-touch.md) und anderen Funktionen (z. B. [Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md)).

Überlagerung ist ein Begriff, der in vielen Kontexten verwendet wird. In diesem Kontext (AEM erweitern) bedeutet eine Überlagerung, die vordefinierten Funktionen zu übernehmen und eigene Definitionen darüber aufzuerlegen (um die Standardfunktionalität anzupassen).

In einer Standardinstanz wird die vordefinierte Funktion unter `/libs` Es wird empfohlen, Ihre Überlagerung (Anpassungen) unter der `/apps` -Verzweigung. AEM verwendet einen Suchpfad, um eine Ressource zu finden, wobei zuerst die Verzweigung `/apps` und dann die Verzweigung `/libs` durchsucht wird ([der Suchpfad kann konfiguriert werden](#configuring-the-search-paths)). Dieser Mechanismus bedeutet, dass Ihre Überlagerung (und die dort definierten Anpassungen) Priorität hat.

Seit AEM 6.0 wurden Änderungen an der Implementierung und Verwendung von Überlagerungen vorgenommen:

* AEM 6.0 und höher - für [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)-zugehörige Überlagerungen (d. h. die Touch-optimierte Benutzeroberfläche)

   * Methode

      * Rekonstruieren Sie die entsprechende `/libs`-Struktur unter `/apps`.

        Dies erfordert keine 1:1-Kopie, der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) wird verwendet, um die erforderlichen Originaldefinitionen zu vergleichen. Der Sling Resource Merger bietet Dienste für den Zugriff auf und die Zusammenführung von Ressourcen mit Vergleichsmechanismen (Differenzierungsmechanismen).

      * under `/apps`, nehmen Sie alle Änderungen vor.

   * Vorteile

      * Robuster gegenüber Änderungen unter `/libs`.
      * Definieren Sie nur das Erforderliche neu.

* Überlagerungen und Überlagerungen außerhalb von Granite vor AEM 6.0

   * Methode

      * Kopieren der Inhalte von `/libs` nach `/apps`

        Kopieren Sie die gesamte Unterverzweigung, einschließlich Eigenschaften.

      * under `/apps`, nehmen Sie alle Änderungen vor.

   * Nachteile

      * Obwohl Ihre Änderungen nicht verloren gehen, wenn sich etwas unter `/libs` ändert, müssen Sie möglicherweise bestimmte Änderungen in Ihrer Überlagerung unter `/apps` neu erstellen.

>[!CAUTION]
>
>Der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) und die zugehörigen Methoden können nur mit [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) verwendet werden. Das bedeutet, dass die Erstellung einer Überlagerung mit einem Strukturgerüst nur für die standardmäßige Touch-optimierte Benutzeroberfläche geeignet ist.
>
>Überlagerungen für andere Bereiche (einschließlich der klassischen Benutzeroberfläche) umfassen das Kopieren des entsprechenden Knotens und der gesamten Unterstruktur und dann die erforderlichen Änderungen.

Überlagerungen sind die empfohlene Methode für viele Änderungen, z. B. [Konfigurieren der Konsolen](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) oder [Erstellen der Auswahlkategorie für den Asset-Browser im Seitenbereich](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (wird beim Erstellen von Seiten verwendet). Sie sind aus folgenden Gründen erforderlich:

* ***Nicht* Änderungen in `/libs` Verzweigung **Alle Änderungen, die Sie vornehmen, können verloren gehen, da sich diese Verzweigung ändern kann, wenn Sie:

   * Aktualisierung auf Ihrer Instanz
   * Hotfix anwenden
   * Feature Pack installieren

* Sie konzentrieren Ihre Änderungen an einem Ort. Dies erleichtert es Ihnen, Ihre Änderungen bei Bedarf zu verfolgen, zu migrieren, zu sichern oder zu debuggen.

## Konfigurieren der Suchpfade {#configuring-the-search-paths}

Bei Überlagerungen handelt es sich bei der bereitgestellten Ressource um ein Aggregat der abgerufenen Ressourcen und Eigenschaften, je nach den zu definierenden Suchpfaden:

* Der **Suchpfad des Ressourcen-Resolvers** wie in der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für die **Apache Sling-Resource Resolver Factory** definiert

   * Die von oben nach unten sortierte Reihenfolge der Suchpfade gibt die jeweiligen Prioritäten an.
   * Bei einer Standardinstallation sind die Hauptstandardwerte: `/apps`, `/libs` - der Inhalt der `/apps` hat eine höhere Priorität als die von `/libs` (d. h. es *Overlays* ).

* Zwei Dienstbenutzer benötigen JCR:READ-Zugriff auf den Speicherort der Skripte. Diese Benutzer sind: „components-search-service“ (verwendet von den com.day.cq.wcm.coreto access/cache-Komponenten) und „sling-scripting“ (verwendet von „org.apache.sling.servlets.resolver“, um Servlets zu finden).
* Die folgende Konfiguration muss außerdem so konfiguriert werden, dass sie dem Speicherort für Ihre Skripte entspricht (in diesem Beispiel unter /etc, /libs oder /apps).

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

## Anwendungsbeispiel {#example-of-usage}

Einige Beispiele werden behandelt, wenn:

* [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md)
* [Anpassung des Seiten-Authorings](/help/sites-developing/customizing-page-authoring-touch.md)
