---
title: SPA-Modell-Routing
description: Bei Single Page Applications in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
exl-id: eaef65ec-2e4d-490f-8158-d48d738e3409
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 93%

---

# SPA-Modell-Routing {#spa-model-routing}

Bei Single Page Applications in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, die SPA Framework-basiertes Client-seitiges Rendering erfordern (z. B. React oder Angular).

## Projekt-Routing {#project-routing}

Die App ist für das Routing verantwortlich und wird dann von den Frontend-Entwicklern des Projekts implementiert. In diesem Dokument wird das Routing für das vom AEM-Server zurückgegebene Modell beschrieben. Die Datenstruktur des Seitenmodells legt die URL der zugrunde liegenden Ressource offen. Das Frontend-Projekt kann eine benutzerdefinierte Bibliothek oder die Bibliothek eines Drittanbieters verwenden, die Routing-Funktionen bereitstellt. Sobald eine Route ein Modellfragment erwartet, kann die `PageModelManager.getData()`-Funktion aufgerufen werden. Wenn sich eine Modellroute geändert hat, muss ein Ereignis ausgelöst werden, um überwachende Bibliotheken wie den Seiteneditor zu warnen.

## Architektur {#architecture}

Eine ausführliche Beschreibung finden Sie im Abschnitt [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager) Abschnitt des SPA Blueprint-Dokuments.

## ModelRouter {#modelrouter}

`ModelRouter` – sofern aktiviert – kapselt die HTML5 History-API-Funktionen `pushState` und `replaceState`, um sicherzustellen, dass ein bestimmtes Modellfragment vorab abgerufen und zugänglich ist. Anschließend benachrichtigt er die registrierte Frontend-Komponente, dass das Modell geändert wurde.

## Vergleich von manuellem und automatischem Routing {#manual-vs-automatic-model-routing}

`ModelRouter` automatisiert das Abrufen von Modellfragmenten. Aber wie jedes automatisierte Tool ist es mit Einschränkungen verbunden. Bei Bedarf kann `ModelRouter` deaktiviert oder so konfiguriert werden, dass Pfade mit Meta-Eigenschaften ignoriert werden (siehe Abschnitt „Meta-Eigenschaften“ im Dokument [SPA-Seitenkomponente](/help/sites-developing/spa-page-component.md)). Frontend-Entwickler können dann ihre eigene Modell-Routing-Schicht implementieren, indem sie `PageModelManager` auffordern, ein bestimmtes Modellfragment mithilfe der `getData()`-Funktion zu laden.

>[!NOTE]
>
>Das Beispielprojekt von React, [We.Retail Journal](https://github.com/adobe/aem-sample-we-retail-journal), veranschaulicht den automatisierten Ansatz, während das Angular-Projekt den manuellen Ansatz veranschaulicht. Ein halbautomatisierter Ansatz wäre auch ein gültiger Anwendungsfall.

>[!CAUTION]
>
>Die aktuelle Version von `ModelRouter` unterstützt nur die Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad der Einstiegspunkte des Sling-Modells verweisen. Die Verwendung von Vanity-URLs oder Aliasnamen wird nicht unterstützt.

## Routing-Vertrag {#routing-contract}

Die aktuelle Implementierung basiert auf der Annahme, dass das SPA-Projekt die HTML5 History-API für das Routing zu den verschiedenen Anwendungsseiten verwendet.

### Konfiguration {#configuration}

`ModelRouter` unterstützt das Konzept des Modell-Routings, da es auf `pushState`- und `replaceState`-Aufrufe wartet, um Modellfragmente vorab abzurufen. Intern triggert es den `PageModelManager`, das Modell zu laden, das einer bestimmten URL entspricht, und löst ein `cq-pagemodel-route-changed`-Ereignis aus, das andere Module überwachen können.

Standardmäßig ist dieses Verhalten automatisch aktiviert. Um es zu deaktivieren, sollte die SPA die folgende Meta-Eigenschaft rendern:

```
<meta property="cq:pagemodel_router" content="disabled"\>
```

Beachten Sie, das jede Route der SPA einer zugänglichen Ressource in AEM entsprechen sollte (z. B. &quot;`/content/mysite/mypage"`), da der `PageModelManager` automatisch versucht, das entsprechende Seitenmodell zu laden, wenn die Route ausgewählt wird. Bei Bedarf kann die SPA jedoch auch eine „Blockierungsliste“ mit Routen definieren, die der `PageModelManager` ignorieren soll:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
