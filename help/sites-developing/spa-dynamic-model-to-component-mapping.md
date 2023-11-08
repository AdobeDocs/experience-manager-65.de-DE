---
title: Zuordnung dynamischer Modelle zu Komponenten für SPAs
description: Erfahren Sie, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für Adobe Experience Manager erfolgt.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
exl-id: 5b2ccac0-bf1d-4f06-8743-7fce6fb68378
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 77%

---

# Zuordnung dynamischer Modelle zu Komponenten für SPAs{#dynamic-model-to-component-mapping-for-spas}

In diesem Dokument wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für Adobe Experience Manager (AEM) erfolgt.

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, die SPA Framework-basiertes Client-seitiges Rendering erfordern (z. B. React oder Angular).

## ComponentMapping-Modul {#componentmapping-module}

Das `ComponentMapping`-Modul wird dem Frontend-Projekt als NPM-Paket bereitgestellt. Es speichert Frontend-Komponenten und bietet der Single Page Application die Möglichkeit, Frontend-Komponenten AEM-Ressourcentypen zuzuordnen. Dies ermöglicht beim Parsen des JSON-Modells des Programms eine dynamische Auflösung von Komponenten.

Alle im Modell vorhandenen Elemente enthalten ein Feld `:type`, das einen AEM-Ressourcentyp verfügbar macht. Bei der Implementierung kann sich die Frontend-Komponente mit dem Fragment des Modells, das sie von den zugrunde liegenden Bibliotheken erhalten hat, selbst rendern.

Siehe [SPA Blueprint](/help/sites-developing/spa-blueprint.md) Weitere Informationen zum Parsen von Modellen und zum Zugriff der Frontend-Komponenten auf das Modell.

Weitere Informationen finden Sie im npm-Paket: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modellgesteuerte Single Page Application {#model-driven-single-page-application}

Anwendungen mit einzelnen Seiten, die das JavaScript SPA SDK für AEM nutzen, sind modellgesteuert:

1. Frontend-Komponenten registrieren sich im [Komponentenzuordnungs-Store](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Anschließend durchläuft der [Container](/help/sites-developing/spa-blueprint.md#container), sobald ihm ein Modell vom [Modellanbieter](/help/sites-developing/spa-blueprint.md#the-model-provider) zur Verfügung gestellt wurde, seinen Modellinhalt ( `:items`).

1. Wenn es eine Seite gibt, erhalten ihre untergeordneten Elemente (`:children`) zuerst eine Komponentenklasse aus der [Komponentenzuordnung](/help/sites-developing/spa-blueprint.md#componentmapping) und instanziieren sie dann.

## App-Initialisierung {#app-initialization}

Jede Komponente wird um die Funktionen des [`ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider) erweitert. Die Initialisierung hat daher die folgende allgemeine Form:

1. Jeder Modellanbieter initialisiert sich selbst und wartet auf Änderungen, die an dem Modell vorgenommen wurden, das seiner inneren Komponente entspricht.
1. [`PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) muss gemäß dem [Initialisierungsfluss](/help/sites-developing/spa-blueprint.md) initialisiert werden.

1. Nach dem Speichern gibt der Seitenmodell-Manager das vollständige Modell der App zurück.
1. Dieses Modell wird dann an die Frontend-Stamm-[Container](/help/sites-developing/spa-blueprint.md#container)-Komponente der App übergeben.
1. Teile des Modells werden schließlich auf jede einzelne untergeordnete Komponente übertragen.

![app_model_initialization](assets/app_model_initialization.png)
