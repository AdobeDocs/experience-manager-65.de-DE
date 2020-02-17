---
title: Erweitern der Ereignisverfolgung
seo-title: Erweitern der Ereignisverfolgung
description: Mit AEM Analytics können Sie Benutzerinteraktionen auf Ihrer Website verfolgen.
seo-description: Mit AEM Analytics können Sie Benutzerinteraktionen auf Ihrer Website verfolgen.
uuid: 722798ac-4043-4918-a6df-9eda2c85020b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: e0372f4a-fe7b-4526-8391-5bb345b51d70
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Erweitern der Ereignisverfolgung{#extending-event-tracking}

Mit AEM Analytics können Sie Benutzerinteraktionen auf Ihrer Website verfolgen. Als Entwickler müssen Sie möglicherweise:

* verfolgen, wie Besucher mit Ihren Komponenten interagieren. This can be done with [Custom events.](#custom-events)
* [Greifen Sie auf Werte im ContextHub](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub)zu.
* [Datensatzrückrufe hinzufügen](#adding-record-callbacks).

>[!NOTE]
>
>This information is basically generic, but it uses [Adobe Analytics](/help/sites-administering/adobeanalytics.md) for specific examples.
>
>[Allgemeine Informationen zum Entwickeln von Komponenten und Dialogfeldern finden Sie unter ](/help/sites-developing/components.md)Entwickeln von Komponenten.

## Benutzerspezifische Ereignisse {#custom-events}

Benutzerspezifische Ereignisse verfolgen alles, was von der Verfügbarkeit einer bestimmten Komponente auf der Seite abhängt. Hierzu gehören auch vorlagenspezifische Ereignisse, da die Seitenkomponente als eine weitere Komponente behandelt wird.

### Verfolgen von benutzerspezifischen Ereignissen beim Laden einer Seite {#tracking-custom-events-on-page-load}

This can be done using the pseudo-attribute `data-tracking` (the older record attribute is still supported for backwards compatibility). Sie können dieses einem beliebigen HTML-Tag hinzufügen.

The syntax for `data-tracking` is

* `data-tracking="{'event': ['eventName'], 'values': {'key': 'value', 'nextKey': 'nextValue'}, componentPath: 'myapp/component/mycomponent'}"`

Sie können eine beliebige Anzahl von Schlüssel-Wert-Paaren als zweiten Parameter übergeben, der als Nutzlast bezeichnet wird.

Ein Beispiel kann wie folgt aussehen:

```xml
<span data-tracking="{event:'blogEntryView',
                                values:{
                                   'blogEntryContentType': 'blog',
                                   'blogEntryUniqueID': '<%= xssAPI.encodeForJSString(entry.getId()) %>',
                                   'blogEntryTitle': '<%= xssAPI.encodeForJSString(entry.getTitle()) %>',
                                   'blogEntryAuthor':'<%= xssAPI.encodeForJSString(entry.getAuthor()) %>',
                                   'blogEntryPageLanguage':'<%= currentPage.getLanguage(true) %>'
                                },
                                componentPath:'myapp/component/mycomponent'}">
</span>
```

At page load, all `data-tracking` attributes will be collected and added to the event store of the ContextHub, where they can be mapped to Adobe Analytics events. Ereignisse, die nicht zugeordnet sind, werden von Adobe Analytics nicht verfolgt. See [Connecting to Adobe Analytics](/help/sites-administering/adobeanalytics.md) for more details about mapping events.

### Verfolgen von benutzerspezifischen Ereignissen nach dem Laden einer Seite {#tracking-custom-events-after-page-load}

Um Ereignisse zu verfolgen, die nach dem Laden einer Seite auftreten (wie z. B. Benutzerinteraktionen), verwenden Sie die JavaScript-Funktion `CQ_Analytics.record`:

* `CQ_Analytics.record({event: 'eventName', values: { valueName: 'VALUE' }, collect: false, options: { obj: this, defaultLinkType: 'X' }, componentPath: '<%=resource.getResourceType()%>'})`

wobei

* `events` ist entweder eine Zeichenfolge oder ein Zeichenfolgen-Array (bei mehreren Ereignissen).

* `values` enthält alle zu verfolgenden Werte.
* `collect` ist optional und gibt ein Array mit den Ereignis- und Objektdaten zurück.
* `options` ist optional und enthält Linkverfolgungsoptionen wie HTML-Elemente `obj` und ` [defaultLinkType](https://microsite.omniture.com/t2/help/en_US/sc/implement/index.html#linkType)`.

* `componentPath` ist ein notwendiges Attribut und es wird empfohlen, `<%=resource.getResourceType()%>`

Beispielsweise verursacht bei folgender Definition das Klicken eines Benutzers auf den Link **Jump to top**, dass die beiden Ereignisse `jumptop` und `headlineclick` ausgelöst werden:

```xml
<h1 data-tracking="{event: 'headline', values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'}">
  My Headline <a href="#" onclick="CQ_Analytics.record({event: ['jumptop','headlineclick'],  values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'})">Jump to top</a>
</h1>
```

## Zugriff auf Werte in ContextHub {#accessing-values-in-the-contexthub}

Die ContextHub JavaScript-API verfügt über eine `getStore(name)` Funktion, die den angegebenen Store zurückgibt, sofern verfügbar. The store has a `getItem(key)` function that returns the value of the specified key, if available. Mithilfe der `getKeys()` Funktion kann ein Array mit definierten Schlüsseln für den jeweiligen Store abgerufen werden.

Sie können über Werteänderungen in einem Speicher benachrichtigt werden, indem Sie eine Funktion mit der `ContextHub.getStore(name).eventing.on(ContextHub.Constants.EVENT_STORE_UPDATED, handler, selector, triggerForPastEvents)` Funktion binden.

The best way to be notified of initial availability of the ContextHub is to use the `ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);` function.

**Zusätzliche Ereignisse für ContextHub:**

Alle Speicher bereit:

`ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);`

Speicherspezifisch:

`ContextHub.getStore(store).eventing.on(ContextHub.Constants.EVENT_STORE_READY, handler, selector, triggerForPastEvents)`

>[!NOTE]
>
>Lesen Sie auch die vollständige [ContextHub-API-Referenz](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/contexthub-api.html#ContextHubJavascriptAPIReference)

## Hinzufügen von Datensatzrückrufen {#adding-record-callbacks}

Before and after callbacks are registered using the functions `CQ_Analytics.registerBeforeCallback(callback,rank)` and `CQ_Analytics.registerAfterCallback(callback,rank)`.

Bei beiden Funktionen wird als erstes Argument eine Funktion und als zweites Argument ein Rang verwendet, der die Reihenfolge der auszuführenden Rückrufe angibt.

Falls ein Rückruf den Wert „false“ zurückgibt, werden die darauf folgenden Rückrufe in der Ausführungskette nicht ausgeführt.
