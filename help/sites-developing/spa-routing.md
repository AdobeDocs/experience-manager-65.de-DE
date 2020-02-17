---
title: SPA-Modell-Routing
seo-title: SPA-Modell-Routing
description: Bei Einzelseitenanwendungen in AEM ist die App für die Weiterleitung zuständig. In diesem Dokument werden der Routingmechanismus, der Vertrag und die verfügbaren Optionen beschrieben.
seo-description: Bei Einzelseitenanwendungen in AEM ist die App für die Weiterleitung zuständig. In diesem Dokument werden der Routingmechanismus, der Vertrag und die verfügbaren Optionen beschrieben.
uuid: 93b4f85a-a240-42d4-95e2-e8b790df7723
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: d9f1e24e-51a9-4f28-b2cd-2e97aed63a24
translation-type: tm+mt
source-git-commit: 2dad220d6593ed542816f8a97b0d4b44f0d57876

---


# SPA-Modell-Routing{#spa-model-routing}

Bei Einzelseitenanwendungen in AEM ist die App für die Weiterleitung zuständig. In diesem Dokument werden der Routingmechanismus, der Vertrag und die verfügbaren Optionen beschrieben.

>[!NOTE]
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen clientseitiges Rendering (z.B. React oder Angular) durch das SPA-Framework erforderlich ist.

## Projektaufteilung {#project-routing}

Die App ist Eigentümer der Routingfunktion und wird dann von den Frontend-Entwicklern des Projekts implementiert. In diesem Dokument wird die für das vom AEM-Server zurückgegebene Modell spezifische Weiterleitung beschrieben. Die Datenstruktur des Seitenmodells stellt die URL der zugrunde liegenden Ressource dar. Das Front-End-Projekt kann jede benutzerdefinierte Bibliothek oder Bibliothek eines Drittanbieters verwenden, die Routingfunktionen bereitstellt. Sobald eine Route ein Fragment des Modells erwartet, kann ein Aufruf an die `PageModelManager.getData()` Funktion durchgeführt werden. Wenn eine Modellroute geändert wurde, muss ein Ereignis ausgelöst werden, um Listening-Bibliotheken wie den Seiten-Editor zu warnen.

## Architektur {#architecture}

Eine ausführliche Beschreibung finden Sie im Abschnitt [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager) des SPA-Blueprint-Dokuments.

## ModelRouter {#modelrouter}

Die `ModelRouter` - sofern aktiviert - kapselt die HTML5-Verlauf-API-Funktionen `pushState` und `replaceState` gewährleistet, dass ein bestimmtes Modellfragment vorab abgerufen und verfügbar ist. Anschließend benachrichtigt er die registrierte Front-End-Komponente, dass das Modell geändert wurde.

## Manuelle und automatische Modellverfolgung {#manual-vs-automatic-model-routing}

Das `ModelRouter` automatisiert das Abrufen von Fragmenten des Modells. Aber wie jedes automatisierte Werkzeug kommt es mit Einschränkungen. Bei Bedarf `ModelRouter` kann das Element deaktiviert oder so konfiguriert werden, dass Pfade mithilfe von Metaeigenschaften ignoriert werden (siehe Abschnitt &quot;Metaeigenschaften&quot;des Dokuments &quot; [SPA-Seitenkomponente](/help/sites-developing/spa-page-component.md) &quot;). Front-End-Entwickler können dann ihre eigene Modell-Routing-Ebene implementieren, indem sie die Anforderung stellen, ein beliebiges Fragment des Modells mit der `PageModelManager` `getData()` Funktion zu laden.

>[!NOTE]
>
>Derzeit zeigt das Projekt We.Retail Journal sample React den automatisierten Ansatz, während das Angular-Projekt das manuelle. Ein halbautomatisierter Ansatz wäre auch ein gültiger Anwendungsfall.

>[!CAUTION]
>
>Die aktuelle Version der `ModelRouter` einzigen Version unterstützt die Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad von Sling Model-Einstiegspunkten zeigen. Die Verwendung von Vanity-URLs oder Aliasnamen wird nicht unterstützt.

## Routing-Vertrag {#routing-contract}

Die aktuelle Implementierung basiert auf der Annahme, dass das SPA-Projekt die HTML5-Verlauf-API für die Weiterleitung zu den verschiedenen Anwendungsseiten verwendet.

### Konfiguration{#configuration}

Das `ModelRouter` unterstützt das Konzept der Modellweiterleitung, da es auf Modellfragmente wartet `pushState` und diese `replaceState` aufruft. Intern löst sie das Laden des Modells aus, das einer bestimmten URL entspricht, und löst ein Ereignis aus, auf das andere Module lauschen können. `PageModelManager` `cq-pagemodel-route-changed`

Standardmäßig ist dieses Verhalten automatisch aktiviert. Um es zu deaktivieren, sollte die SPA die folgende Meta-Eigenschaft rendern:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Note that every route of the SPA should correspond to an accessible resource in AEM (e.g., &quot; `/content/mysite/mypage"`) since the `PageModelManager` will automatically try to load the corresponding page model once the route is selected. Though, if needed, the SPA can also define a &quot;black list&quot; of routes that should be ignored by the `PageModelManager`:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
