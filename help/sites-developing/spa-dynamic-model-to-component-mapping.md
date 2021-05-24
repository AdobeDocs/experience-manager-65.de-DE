---
title: Zuordnung dynamischer Modelle zu Komponenten für SPAs
seo-title: Zuordnung dynamischer Modelle zu Komponenten für SPAs
description: In diesem Artikel wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für AEM erfolgt.
seo-description: In diesem Artikel wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für AEM erfolgt.
uuid: 337b8d90-efd7-442e-9fac-66c33cc26212
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 8b4b0afc-8534-4010-8f34-cb10475a8e79
exl-id: 5b2ccac0-bf1d-4f06-8743-7fce6fb68378
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 85%

---

# Zuordnung dynamischer Modelle zu Komponenten für SPAs{#dynamic-model-to-component-mapping-for-spas}

In diesem Dokument wird beschrieben, wie die Zuordnung des dynamischen Modells zu Komponenten im JavaScript SPA SDK für AEM erfolgt.

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, die SPA Framework-basiertes Client-seitiges Rendering erfordern (z. B. React oder Angular).

## ComponentMapping-Modul {#componentmapping-module}

Das `ComponentMapping`-Modul wird dem Frontend-Projekt als NPM-Paket bereitgestellt. Es speichert Frontend-Komponenten und bietet der Single Page Application die Möglichkeit, Frontend-Komponenten AEM-Ressourcentypen zuzuordnen. Dies ermöglicht eine dynamische Auflösung von Komponenten beim Parsen des JSON-Modells der Anwendung.

Alle im Modell vorhandenen Elemente enthalten ein Feld `:type`, das einen AEM-Ressourcentyp verfügbar macht. Bei der Implementierung kann sich die Frontend-Komponente selbst unter Verwendung des Modellfragments rendern, das sie von den zugrunde liegenden Bibliotheken erhalten hat.

Weitere Informationen zum Parsen von Modellen und zum Zugriff der Frontend-Komponenten auf das Modell finden Sie im Dokument [SPA-Blueprint](/help/sites-developing/spa-blueprint.md).

Weitere Informationen finden Sie im npm-Paket: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modellgesteuerte Single Page Application {#model-driven-single-page-application}

Single Page Applications, die das JavaScript SPA SDK für AEM nutzen, sind modellgesteuert:

1. Frontend-Komponenten registrieren sich im [Komponentenzuordnungs-Store](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Anschließend durchläuft der [Container](/help/sites-developing/spa-blueprint.md#container), sobald ihm ein Modell vom [Modellanbieter](/help/sites-developing/spa-blueprint.md#the-model-provider) zur Verfügung gestellt wurde, seinen Modellinhalt ( `:items`).

1. Im Fall einer Seite erhalten die untergeordneten Elemente (`:children`) zunächst eine Komponentenklasse aus der [Komponentenzuordnung](/help/sites-developing/spa-blueprint.md#componentmapping) und instanziieren sie dann.

## App-Initialisierung {#app-initialization}

Jede Komponente wird mit den Funktionen von [ `ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider) erweitert. Die Initialisierung hat daher die folgende allgemeine Form:

1. Jeder Modellanbieter initialisiert sich selbst und wartet auf Änderungen, die an dem Modell vorgenommen wurden, das seiner inneren Komponente entspricht.
1. Der [ `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) muss entsprechend dem [Initialisierungsfluss](/help/sites-developing/spa-blueprint.md) initialisiert werden.

1. Nach dem Speichern gibt der Seitenmodell-Manager das vollständige Modell der App zurück.
1. Dieses Modell wird dann an die Frontend-Stamm-[Container](/help/sites-developing/spa-blueprint.md#container)-Komponente der App übergeben.
1. Teile des Modells werden schließlich auf jede einzelne untergeordnete Komponente übertragen.

![app_model_initialization](assets/app_model_initialization.png)
