---
title: Routing SPA
seo-title: Routing SPA
description: Bei Einzelseitenanwendungen in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.
seo-description: Bei Einzelseitenanwendungen in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.
uuid: 93b4f85a-a240-42d4-95e2-e8b790df7723
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: d9f1e24e-51a9-4f28-b2cd-2e97aed63a24
translation-type: tm+mt
source-git-commit: 4ea1bad1fb76142be7f6d564ecf30ed85a6da694
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 8%

---


# Routing des SPA{#spa-model-routing}

Bei Einzelseitenanwendungen in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, bei denen SPA Framework-basiertes clientseitiges Rendering (z.B. React oder Angular) erforderlich ist.

## Project Routing {#project-routing}

Die App ist im Besitz des Routings und wird dann von den Frontend-Entwicklern des Projekts implementiert. Dieses Dokument beschreibt das Routing, das für das vom AEM zurückgegebene Modell spezifisch ist. Die Datenstruktur des Seitenmodells stellt die URL der zugrunde liegenden Ressource dar. Das Front-End-Projekt kann eine benutzerdefinierte Bibliothek oder eine Bibliothek eines Drittanbieters verwenden, die Routing-Funktionen bereitstellt. Wenn eine Route ein Fragment des Modells erwartet, kann ein Aufruf an die Funktion `PageModelManager.getData()` durchgeführt werden. Wenn eine Modellroute geändert wurde, muss ein Ereignis ausgelöst werden, um Listening-Bibliotheken wie den Seiten-Editor zu warnen.

## Architektur {#architecture}

Eine ausführliche Beschreibung finden Sie im Abschnitt [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager) des Dokuments SPA Blueprint.

## ModelRouter {#modelrouter}

Die `ModelRouter` - sofern aktiviert - kapselt die HTML5-Verlauf-API-Funktionen `pushState` und `replaceState`, um sicherzustellen, dass ein bestimmtes Fragment des Modells vorab abgerufen und verfügbar ist. Anschließend benachrichtigt er die registrierte Front-End-Komponente, dass das Modell geändert wurde.

## Manuelles oder automatisches Routing {#manual-vs-automatic-model-routing}

Das `ModelRouter` automatisiert das Abrufen von Fragmenten des Modells. Aber wie jedes automatisierte Werkzeug kommt es mit Einschränkungen. Bei Bedarf kann `ModelRouter` deaktiviert oder so konfiguriert werden, dass Pfade mithilfe von Metaeigenschaften ignoriert werden (siehe Abschnitt &quot;Metaeigenschaften&quot;im Dokument [SPA Seitenkomponente](/help/sites-developing/spa-page-component.md)). Front-End-Entwickler können dann ihre eigene Modellebene implementieren, indem sie `PageModelManager` auffordern, ein bestimmtes Modellfragment mit der Funktion `getData()` zu laden.

>[!NOTE]
>
>Derzeit zeigt das Protokoll-Beispielprojekt &quot;We.Retail&quot;den automatisierten Ansatz, während das Angular-Projekt das manuelle Projekt veranschaulicht. Ein halbautomatisierter Ansatz wäre auch ein gültiger Anwendungsfall.

>[!CAUTION]
>
>Die aktuelle Version von `ModelRouter` unterstützt nur eine Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad von Sling Model-Einstiegspunkten verweisen. Die Verwendung von Vanity-URLs oder Aliasnamen wird nicht unterstützt.

## Routing-Vertrag {#routing-contract}

Die aktuelle Implementierung basiert auf der Annahme, dass das SPA Projekt die HTML5-Verlauf-API zum Routing der verschiedenen Anwendungsseiten verwendet.

### Konfiguration {#configuration}

Das `ModelRouter` unterstützt das Modellkonzept, da es auf `pushState`- und `replaceState`-Aufrufe wartet, um Modellfragmente im Voraus abzurufen. Intern löst sie das `PageModelManager` aus, um das Modell zu laden, das einer angegebenen URL entspricht, und löst ein `cq-pagemodel-route-changed`-Ereignis aus, auf das andere Module lauschen können.

Standardmäßig ist dieses Verhalten automatisch aktiviert. Um es zu deaktivieren, sollte die SPA die folgende Meta-Eigenschaft rendern:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Beachten Sie, dass jede Route der SPA einer barrierefreien Ressource in AEM entsprechen sollte (z.B. &quot; `/content/mysite/mypage"`&quot;), da `PageModelManager` automatisch versucht, das entsprechende Seitenmodell zu laden, sobald die Route ausgewählt ist. Bei Bedarf kann der SPA jedoch auch eine &quot;Blockierungsliste&quot;von Routen definieren, die von `PageModelManager` ignoriert werden sollten:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
