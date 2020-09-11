---
title: Zuordnung dynamischer Modelle zu Komponenten für SPAs
seo-title: Zuordnung dynamischer Modelle zu Komponenten für SPAs
description: In diesem Artikel wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript-SPA-SDK für AEM erfolgt.
seo-description: In diesem Artikel wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript-SPA-SDK für AEM erfolgt.
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
ht-degree: 0%

---


# Zuordnung dynamischer Modelle zu Komponenten für SPAs{#dynamic-model-to-component-mapping-for-spas}

In diesem Dokument wird beschrieben, wie das dynamische Modell zur Komponentenzuordnung im JavaScript-SPA-SDK für AEM ausgeführt wird.

>[!NOTE]
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen clientseitiges Rendering (z.B. React oder Angular) durch das SPA-Framework erforderlich ist.

## ComponentMapping-Modul {#componentmapping-module}

The `ComponentMapping` module is provided as an NPM package to the front-end project. Es speichert Front-End-Komponenten und bietet der Einzelseitenanwendung die Möglichkeit, Frontend-Komponenten AEM Ressourcentypen zuzuordnen. Dies ermöglicht eine dynamische Auflösung von Komponenten beim Parsen des JSON-Modells der Anwendung.

Alle im Modell vorhandenen Elemente enthalten ein `:type` Feld, das einen AEM Ressourcentyp verfügbar macht. Bei der Bereitstellung kann sich die Front-End-Komponente mit dem Fragment des Modells wiedergeben, das sie von den zugrunde liegenden Bibliotheken erhalten hat.

Weitere Informationen zur Modellanalyse und zum Zugriff auf die Front-End-Komponenten finden Sie im Dokument [SPA Blueprint](/help/sites-developing/spa-blueprint.md) .

Weitere Informationen finden Sie im npm-Paket: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modellgesteuerte Einzelseitenanwendung {#model-driven-single-page-application}

Einzelseitenanwendungen, die das JavaScript-SPA-SDK für AEM nutzen, werden modellgesteuert:

1. Front-End-Komponenten registrieren sich im [Component Mapping Store](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Anschließend durchläuft der [Container](/help/sites-developing/spa-blueprint.md#container), sobald ihm ein Modell vom [Modellanbieter](/help/sites-developing/spa-blueprint.md#the-model-provider)zur Verfügung gestellt wurde, seinen Modellinhalt ( `:items`).

1. Bei einer Seite erhält deren untergeordnete Elemente ( `:children`) zunächst eine Komponentenklasse aus der [Komponentenzuordnung](/help/sites-developing/spa-blueprint.md#componentmapping) und instanziieren sie dann.

## App-Initialisierung {#app-initialization}

Jede Komponente wird mit den Funktionen des [`ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider)erweitert. Die Initialisierung erfolgt daher in folgender allgemeiner Form:

1. Jeder Modellanbieter initialisiert sich selbst und überwacht Änderungen, die an dem Teil des Modells vorgenommen wurden, der seiner inneren Komponente entspricht.
1. Die [ Initialisierung `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) muss entsprechend dem [Initialisierungsfluss](/help/sites-developing/spa-blueprint.md)erfolgen.

1. Nach dem Speichern gibt der Seitenmodellmanager das vollständige Modell der App zurück.
1. Dieses Modell wird dann an die Front-End-Stamm- [Container](/help/sites-developing/spa-blueprint.md#container) -Komponente der Anwendung übergeben.
1. Teile des Modells werden schließlich auf jede einzelne untergeordnete Komponente übertragen.

![app_model_initialization](assets/app_model_initialization.png)

