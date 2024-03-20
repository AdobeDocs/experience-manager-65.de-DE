---
title: Erweitern der Ereignisverfolgung
description: Mit AEM Analytics können Sie Benutzerinteraktionen auf Ihrer Website nachverfolgen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: a71d20e6-0321-4afb-95fe-6de8b7b37245
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 98%

---

# Erweitern der Ereignisverfolgung{#extending-event-tracking}

Mit AEM Analytics können Sie Benutzerinteraktionen auf Ihrer Website nachverfolgen. Als Entwicklerin oder Entwickler müssen Sie möglicherweise:

* nachverfolgen, wie Besuchende mit Komponenten interagieren. Hierfür können Sie [benutzerspezifische Ereignisse](#custom-events) verwenden.
* [Zugriff auf Werte im ContextHub](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).
* [Datensatzrückrufe hinzufügen](#adding-record-callbacks).

>[!NOTE]
>
>Diese Informationen sind zwar größtenteils allgemeiner Art, [Adobe Analytics](/help/sites-administering/adobeanalytics.md) wird jedoch für spezifische Beispiele verwendet.
>
>[Allgemeine Informationen zum Entwickeln von Komponenten und Dialogfeldern finden Sie unter ](/help/sites-developing/components.md)Entwickeln von Komponenten.

## Benutzerdefinierte Ereignisse {#custom-events}

Benutzerdefinierte Ereignisse verfolgen alles, was von der Verfügbarkeit einer bestimmten Komponente auf der Seite abhängt. Hierzu gehören auch vorlagenspezifische Ereignisse, da die Seitenkomponente als eine weitere Komponente behandelt wird.

### Nachverfolgen benutzerdefinierter Ereignisse beim Laden einer Seite {#tracking-custom-events-on-page-load}

Dies kann mit dem Pseudo-Attribut `data-tracking` erfolgen (das ältere Datensatzattribut wird weiter unterstützt, um die Abwärtskompatibilität sicherzustellen). Sie können dieses einem beliebigen HTML-Tag hinzufügen.

Die Syntax für `data-tracking` lautet

* `data-tracking="{'event': ['eventName'], 'values': {'key': 'value', 'nextKey': 'nextValue'}, componentPath: 'myapp/component/mycomponent'}"`

Sie können eine beliebige Anzahl von Schlüssel-Wert-Paaren als zweiten Parameter übergeben, der als Payload bezeichnet wird.

Ein mögliches Beispiel:

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

Beim Laden der Seite werden alle `data-tracking`-Attribute erfasst und zum Ereignisabschnitt des ContextHub hinzugefügt, wo sie Adobe Analytics-Ereignissen zugeordnet werden können. Nicht zugeordnete Ereignisse werden von Adobe Analytics nicht verfolgt. Weitere Informationen zum Zuordnen von Ereignissen finden Sie unter [Verbinden mit Adobe Analytics](/help/sites-administering/adobeanalytics.md).

### Verfolgen von benutzerspezifischen Ereignissen nach dem Laden einer Seite {#tracking-custom-events-after-page-load}

Um Ereignisse zu verfolgen, die nach dem Laden einer Seite auftreten (wie z. B. Benutzerinteraktionen), verwenden Sie die JavaScript-Funktion `CQ_Analytics.record`:

* `CQ_Analytics.record({event: 'eventName', values: { valueName: 'VALUE' }, collect: false, options: { obj: this, defaultLinkType: 'X' }, componentPath: '<%=resource.getResourceType()%>'})`

Dabei gilt

* `events` ist entweder eine Zeichenfolge oder ein Zeichenfolgen-Array (bei mehreren Ereignissen).

* `values` enthält alle zu verfolgenden Werte
* `collect` ist optional und gibt ein Array mit den Ereignis- und Objektdaten zurück.
* `options` ist optional und beinhaltet Optionen zur Linkverfolgung, z. B. die HTML-Elemente `obj` und ` [defaultLinkType](https://microsite.omniture.com/t2/help/en_US/sc/implement/index.html#linkType)`.

* `componentPath` ist ein erforderliches Attribut; es wird empfohlen, es auf `<%=resource.getResourceType()%>` festzulegen.

Beispielsweise verursacht bei folgender Definition das Klicken eines Benutzers auf den Link **Jump to top**, dass die beiden Ereignisse `jumptop` und `headlineclick` ausgelöst werden:

```xml
<h1 data-tracking="{event: 'headline', values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'}">
  My Headline <a href="#" onclick="CQ_Analytics.record({event: ['jumptop','headlineclick'],  values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'})">Jump to top</a>
</h1>
```

## Zugreifen auf Werte im ContextHub {#accessing-values-in-the-contexthub}

Die ContextHub-JavaScript-API verfügt über eine `getStore(name)`-Funktion, die ggfs. den angegebenen Speicherabschnitt zurückgibt. Jeder Speicherabschnitt beinhaltet eine Funktion `getItem(key)`, die ggfs. den Wert des angegebenen Schlüssels zurückgibt. Mit dieser Funktion `getKeys()` kann ein Array von definierten Schlüsseln für den jeweiligen Speicherabschnitt abgerufen werden.

Sie können über Wertänderungen in einem Speicherabschnitt benachrichtigt werden, indem Sie eine Funktion mit der Funktion `ContextHub.getStore(name).eventing.on(ContextHub.Constants.EVENT_STORE_UPDATED, handler, selector, triggerForPastEvents)` binden.

Die beste Möglichkeit, über die anfängliche Verfügbarkeit des ContextHub benachrichtigt zu werden, ist die Verwendung der Funktion `ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);`.

**Zusätzliche Ereignisse für ContextHub:**

Alle Speicher bereit:

`ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);`

Speicherspezifisch:

`ContextHub.getStore(store).eventing.on(ContextHub.Constants.EVENT_STORE_READY, handler, selector, triggerForPastEvents)`

>[!NOTE]
>
>Sehen Sie sich auch die vollständige [ContextHub-API-Referenz](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/contexthub-api.html#ContextHubJavascriptAPIReference) an.

## Hinzufügen von Datensatzrückrufen {#adding-record-callbacks}

Rückrufe vor und nach dem Laden werden mit den Funktionen `CQ_Analytics.registerBeforeCallback(callback,rank)` und `CQ_Analytics.registerAfterCallback(callback,rank)` registriert.

Bei beiden Funktionen wird als erstes Argument eine Funktion und als zweites Argument ein Rang verwendet, der die Reihenfolge der auszuführenden Rückrufe angibt.

Falls ein Rückruf den Wert „false“ zurückgibt, werden die darauf folgenden Rückrufe in der Ausführungskette nicht ausgeführt.
