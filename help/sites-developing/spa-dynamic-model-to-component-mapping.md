---
title: Zuordnung dynamischer Modelle zu Komponenten für SPA
seo-title: Zuordnung dynamischer Modelle zu Komponenten für SPA
description: In diesem Artikel wird beschrieben, wie das dynamische Modell zur Komponentenzuordnung im JavaScript SPA SDK für AEM erfolgt.
seo-description: In diesem Artikel wird beschrieben, wie das dynamische Modell zur Komponentenzuordnung im JavaScript SPA SDK für AEM erfolgt.
uuid: 337b8d90-efd7-442e-9fac-66c33cc26212
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 8b4b0afc-8534-4010-8f34-cb10475a8e79
translation-type: tm+mt
source-git-commit: 4c9a0bd73e8d87d3869c6a133f5d1049f8430cd1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 18%

---


# Zuordnung dynamischer Modelle zu Komponenten für SPA{#dynamic-model-to-component-mapping-for-spas}

In diesem Dokument wird beschrieben, wie das dynamische Modell zur Komponentenzuordnung im JavaScript-SPA-SDK für AEM ausgeführt wird.

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, bei denen SPA Framework-basiertes clientseitiges Rendering (z.B. React oder Angular) erforderlich ist.

## ComponentMapping-Modul {#componentmapping-module}

Das `ComponentMapping`-Modul wird dem Frontend-Projekt als NPM-Paket bereitgestellt. Es speichert Front-End-Komponenten und bietet der Einzelseitenanwendung die Möglichkeit, Frontend-Komponenten AEM Ressourcentypen zuzuordnen. Dies ermöglicht beim Parsen des JSON-Modells der Anwendung eine dynamische Auflösung von Komponenten.

Alle im Modell vorhandenen Elemente enthalten ein `:type`-Feld, das einen AEM-Ressourcentyp verfügbar macht. Bei der Implementierung kann sich die Frontend-Komponente mit dem Fragment des Modells, das sie von den zugrunde liegenden Bibliotheken erhalten hat, selbst rendern.

Weitere Informationen zur Modellanalyse und zum Zugriff auf die Front-End-Komponenten finden Sie im Dokument [SPA Blueprint](/help/sites-developing/spa-blueprint.md).

Weitere Informationen finden Sie im npm-Paket: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modellgetriebene Einzelseitenanwendung {#model-driven-single-page-application}

Einzelseitenanwendungen, die das JavaScript SPA SDK für AEM nutzen, werden modellgesteuert:

1. Front-End-Komponenten registrieren sich beim [Component Mapping Store](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Anschließend durchläuft der [Container](/help/sites-developing/spa-blueprint.md#container), sobald er mit einem Modell von [Modellanbieter](/help/sites-developing/spa-blueprint.md#the-model-provider) geliefert wurde, den Modellinhalt ( `:items`).

1. Bei einer Seite erhalten die untergeordneten Elemente ( `:children`) zunächst eine Komponentenklasse von [Komponentenzuordnung](/help/sites-developing/spa-blueprint.md#componentmapping) und instanziieren sie dann.

## App-Initialisierung {#app-initialization}

Jede Komponente wird mit den Funktionen von [ `ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider) erweitert. Die Initialisierung erfolgt daher in folgender allgemeiner Form:

1. Jeder Modellanbieter initialisiert sich selbst und überwacht Änderungen, die an dem Teil des Modells vorgenommen wurden, der seiner inneren Komponente entspricht.
1. [ `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) muss initialisiert werden, wie durch den [Initialisierungsfluss](/help/sites-developing/spa-blueprint.md) dargestellt.

1. Nach dem Speichern gibt der Seitenmodellmanager das vollständige Modell der App zurück.
1. Dieses Modell wird dann an die Front-End-Stammkomponente [Container](/help/sites-developing/spa-blueprint.md#container) der Anwendung übergeben.
1. Teile des Modells werden schließlich auf jede einzelne untergeordnete Komponente übertragen.

![app_model_initialization](assets/app_model_initialization.png)

