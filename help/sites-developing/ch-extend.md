---
title: Erweitern von ContextHub
seo-title: Erweitern von ContextHub
description: Definieren Sie neue Typen von ContextHub-Stores und -Modulen, wenn die bereitgestellten Typen nicht Ihren Lösungsanforderungen entsprechen.
seo-description: Definieren Sie neue Typen von ContextHub-Stores und -Modulen, wenn die bereitgestellten Typen nicht Ihren Lösungsanforderungen entsprechen.
uuid: 1d80c01d-ec5d-4e76-849d-bec0e1c3941a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 13a908ae-6965-4438-96d0-93516b500884
translation-type: tm+mt
source-git-commit: ed34f2200f4ff4f407f7b92165685af390f5f7e3

---


# Erweitern von ContextHub{#extending-contexthub}

Definieren Sie neue Typen von ContextHub-Stores und -Modulen, wenn die bereitgestellten Typen nicht Ihren Lösungsanforderungen entsprechen.

## Erstellen benutzerdefinierter Store-Kandidaten {#creating-custom-store-candidates}

ContextHub-Stores werden aus registrierten Store-Kandidaten erstellt. Um einen benutzerdefinierten Store zu erstellen, müssen Sie einen Store-Kandidaten erstellen und registrieren.

Die JavaScript-Datei mit dem Code zum Erstellen und Registrieren des Store-Kandidaten muss in einem [Client-Bibliotheksordner](/help/sites-developing/clientlibs.md#creating-client-library-folders) enthalten sein. Die Ordnerkategorie muss dem folgenden Muster entsprechen:

```xml
contexthub.store.[storeType]
```

The `[storeType]` part of the category is the `storeType` with which the store candidate is registered. (Siehe [Registrieren von ContextHub-Store-Kandidaten](/help/sites-developing/ch-extend.md#registering-a-contexthub-store-candidate).) Beispielsweise muss für den Store-Typ `contexthub.mystore` die Kategorie des Client-Bibliotheksordners `contexthub.store.contexthub.mystore` lauten.

### Erstellen von ContextHub-Store-Kandidaten {#creating-a-contexthub-store-candidate}

To create a store candidate, you use the [`ContextHub.Utils.inheritance.inherit`](/help/sites-developing/contexthub-api.md#inherit-child-parent) function to extend one of the base stores:

* [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [`ContextHub.Store.SessionStore`](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [`ContextHub.Store.JSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-jsonpstore)
* [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)

Note that each base store extends the [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) store.

Im folgenden Beispiel wird erst die einfachste Erweiterung des Store-Kandidaten `ContextHub.Store.PersistedStore` erstellt:

```
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

In der Praxis werden mit Ihren benutzerdefinierten Store-Kandidaten wohl zusätzliche Funktionen definiert oder die ursprüngliche Konfiguration des Stores überschrieben. Several [sample store candidates](/help/sites-developing/ch-samplestores.md) are installed in the repository below `/libs/granite/contexthub/components/stores`. Verwenden Sie CRXDE Lite, um die JavaScript-Dateien zu öffnen und sich diese Beispiele genauer anzusehen.

### Registrieren von ContextHub-Store-Kandidaten {#registering-a-contexthub-store-candidate}

Registrieren Sie einen Store-Kandidaten, um ihn mit dem ContextHub-Framework zu integrieren und Stores zu aktivieren, die auf Grundlage des Kandidaten erstellt werden sollen. Um einen Store-Kandidaten zu registrieren, verwenden Sie die Funktion [`registerStoreCandidate`](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) der Klasse `ContextHub.Utils.storeCandidates`.

Wenn Sie einen Store-Kandidaten registrieren, geben Sie einen Namen für den Store-Typ ein. Beim Erstellen eines Stores auf Grundlage des Kandidaten identifizieren Sie über den Store-Typ den zugrunde liegenden Kandidaten.

Geben Sie beim Registrieren eines Store-Kandidaten dessen Priorität an. Wird ein Store-Kandidat mit demselben Store-Typ wie ein bereits registrierter Store-Kandidat registriert, wird der Kandidat mit der höheren Priorität verwendet. Daher können Sie vorhandene Store-Kandidaten durch neue Implementierungen überschreiben.

```
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

In den meisten Fällen ist nur ein Kandidat erforderlich und die Priorität kann auf `0`, aber wenn Sie interessiert sind, können Sie über [fortgeschrittene Registrierungen erfahren,](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) die es ermöglicht, eine von wenigen Stores-Implementierungen auf Basis von JavaScript-Bedingung (`applies`) und Kandidatenpriorität auszuwählen.

## Erstellen von Typen von ContextHub-Benutzeroberflächenmodulen {#creating-contexthub-ui-module-types}

Erstellen Sie benutzerdefinierte Typen eines Benutzeroberflächenmoduls, wenn die [mit ContextHub installierten Typen](/help/sites-developing/ch-samplemodules.md) nicht Ihren Anforderungen entsprechen. Erstellen Sie dazu einen neuen Benutzeroberflächenmodul-Renderer, indem Sie die `ContextHub.UI.BaseModuleRenderer`-Klasse erweitern und sie dann mit `ContextHub.UI` registrieren.

Erstellen Sie zum Erstellen eines Benutzeroberflächenmodul-Renderers ein `Class`-Objekt, das die Logik enthält, die das Benutzeroberflächenmodul rendert. Ihre Klasse muss mindestens die folgenden Aktionen durchführen:

* Extend the `ContextHub.UI.BaseModuleRenderer` class. Bei dieser Klasse handelt es sich um die Basisimplementierung für alle Benutzeroberflächenmodul-Renderer. Das `Class`-Objekt definiert eine Eigenschaft namens `extend`, mit der Sie diese Klasse als diejenige benennen, die erweitert wird.

* Bereitstellen einer Standardkonfiguration. Create a `defaultConfig` property. Diese Eigenschaft ist ein Objekt, das die Eigenschaften enthält, die für das Benutzeroberflächenmodul [`contexthub.base`](/help/sites-developing/ch-samplemodules.md#contexthub-base-ui-module-type) definiert sind, sowie alle anderen Eigenschaften, die Sie benötigen.

The source for `ContextHub.UI.BaseModuleRenderer` is located at /libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js.  Verwenden Sie zum Registrieren des Renderers die Methode [`registerRenderer`](/help/sites-developing/contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) der `ContextHub.UI`-Klasse. Sie müssen einen Namen für den Modultyp angeben. Wenn Administratoren ein Benutzeroberflächenmodul auf Grundlage dieses Renderers anlegen, geben sie diesen Namen an.

Erstellen und registrieren Sie die Renderer-Klasse in einer selbstausführenden anonymen Funktion. Das folgende Beispiel basiert auf dem Quellcode des Benutzeroberflächenmoduls „contexthub.browserinfo“. Dieses Benutzeroberflächenmodul ist eine einfache Erweiterung der `ContextHub.UI.BaseModuleRenderer`-Klasse.

```xml
;(function() {

    var SurferinfoRenderer = new Class({
        extend: ContextHub.UI.BaseModuleRenderer,

        defaultConfig: {
            icon: 'coral-Icon--globe',
            title: 'Browser/OS Information',

            storeMapping: {
                surferinfo: 'surferinfo'
            },

            template:
                '<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p>' +
                '<p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>'
        }
    });

    ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());

}());
```

The javascript file that includes the code that creates and registers the renderer must be included in a [client library folder](/help/sites-developing/clientlibs.md#creating-client-library-folders). Die Ordnerkategorie muss dem folgenden Muster entsprechen:

```xml
contexthub.module.[moduleType]
```

The `[moduleType]` part of the category is the `moduleType` with which the module renderer is registered. For example, for the `moduleType` of `contexthub.browserinfo`, the category of the client library folder must be `contexthub.module.contexthub.browserinfo`.
