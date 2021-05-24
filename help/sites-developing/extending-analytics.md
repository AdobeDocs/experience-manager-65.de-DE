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
exl-id: a71d20e6-0321-4afb-95fe-6de8b7b37245
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 53%

---

# Erweitern der Ereignisverfolgung{#extending-event-tracking}

Mit AEM Analytics können Sie Benutzerinteraktionen auf Ihrer Website verfolgen. Als Entwickler müssen Sie möglicherweise:

* verfolgen, wie Besucher mit Ihren Komponenten interagieren. Dies kann mit [benutzerdefinierten Ereignissen erfolgen.](#custom-events)
* [Auf Werte in ContextHub zugreifen](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).
* [Datensatzrückrufe hinzufügen](#adding-record-callbacks).

>[!NOTE]
>
>Diese Informationen sind im Wesentlichen generisch, werden aber für bestimmte Beispiele [Adobe Analytics](/help/sites-administering/adobeanalytics.md) verwendet.
>
>[Allgemeine Informationen zum Entwickeln von Komponenten und Dialogfeldern finden Sie unter ](/help/sites-developing/components.md)Entwickeln von Komponenten.

## Benutzerspezifische Ereignisse {#custom-events}

Benutzerspezifische Ereignisse verfolgen alles, was von der Verfügbarkeit einer bestimmten Komponente auf der Seite abhängt. Hierzu gehören auch vorlagenspezifische Ereignisse, da die Seitenkomponente als eine weitere Komponente behandelt wird.

### Verfolgen von benutzerspezifischen Ereignissen beim Laden einer Seite  {#tracking-custom-events-on-page-load}

Dies kann mithilfe des Pseudo-Attributs `data-tracking` erfolgen (das ältere Datensatzattribut wird aus Gründen der Abwärtskompatibilität weiterhin unterstützt). Sie können dieses einem beliebigen HTML-Tag hinzufügen.

Die Syntax für `data-tracking` lautet

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

Beim Laden der Seite werden alle `data-tracking`-Attribute erfasst und zum Ereignisspeicher des ContextHub hinzugefügt, wo sie Adobe Analytics-Ereignissen zugeordnet werden können. Ereignisse, die nicht zugeordnet sind, werden von Adobe Analytics nicht verfolgt. Weitere Informationen zur Zuordnung von Ereignissen finden Sie unter [Herstellen einer Verbindung zu Adobe Analytics](/help/sites-administering/adobeanalytics.md) .

### Verfolgen von benutzerspezifischen Ereignissen nach dem Laden einer Seite {#tracking-custom-events-after-page-load}

Um Ereignisse zu verfolgen, die nach dem Laden einer Seite auftreten (wie z. B. Benutzerinteraktionen), verwenden Sie die JavaScript-Funktion `CQ_Analytics.record`:

* `CQ_Analytics.record({event: 'eventName', values: { valueName: 'VALUE' }, collect: false, options: { obj: this, defaultLinkType: 'X' }, componentPath: '<%=resource.getResourceType()%>'})`

wobei

* `events` ist entweder eine Zeichenfolge oder ein Zeichenfolgen-Array (bei mehreren Ereignissen).

* `values` enthält alle zu verfolgenden Werte.
* `collect` ist optional und gibt ein Array mit den Ereignis- und Objektdaten zurück.
* `options` ist optional und enthält Linktracking-Optionen wie HTML-Element  `obj` und  ` [defaultLinkType](https://microsite.omniture.com/t2/help/en_US/sc/implement/index.html#linkType)`.

* `componentPath` ist ein erforderliches Attribut und es wird empfohlen,  `<%=resource.getResourceType()%>`

Beispielsweise verursacht bei folgender Definition das Klicken eines Benutzers auf den Link **Jump to top**, dass die beiden Ereignisse `jumptop` und `headlineclick` ausgelöst werden:

```xml
<h1 data-tracking="{event: 'headline', values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'}">
  My Headline <a href="#" onclick="CQ_Analytics.record({event: ['jumptop','headlineclick'],  values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'})">Jump to top</a>
</h1>
```

## Zugreifen auf Werte in ContextHub {#accessing-values-in-the-contexthub}

Die ContextHub-JavaScript-API verfügt über eine `getStore(name)`-Funktion, die den angegebenen Store zurückgibt, sofern verfügbar. Der Store verfügt über eine `getItem(key)` -Funktion, die den Wert des angegebenen Schlüssels zurückgibt, sofern verfügbar. Mithilfe der Funktion `getKeys()` können Sie ein Array definierter Schlüssel für den spezifischen Store abrufen.

Sie können über Wertänderungen in einem Store benachrichtigt werden, indem Sie eine Funktion mithilfe der Funktion `ContextHub.getStore(name).eventing.on(ContextHub.Constants.EVENT_STORE_UPDATED, handler, selector, triggerForPastEvents)` binden.

Die beste Möglichkeit, über die anfängliche Verfügbarkeit von ContextHub informiert zu werden, besteht in der Verwendung der Funktion `ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);` .

**Zusätzliche Ereignisse für ContextHub:**

Alle Speicher bereit:

`ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);`

Speicherspezifisch:

`ContextHub.getStore(store).eventing.on(ContextHub.Constants.EVENT_STORE_READY, handler, selector, triggerForPastEvents)`

>[!NOTE]
>
>Weitere Informationen finden Sie in der vollständigen [ContextHub-API-Referenz](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/contexthub-api.html#ContextHubJavascriptAPIReference)

## Hinzufügen von Datensatzrückrufen {#adding-record-callbacks}

Vor und nach Rückrufen werden mit den Funktionen `CQ_Analytics.registerBeforeCallback(callback,rank)` und `CQ_Analytics.registerAfterCallback(callback,rank)` registriert.

Bei beiden Funktionen wird als erstes Argument eine Funktion und als zweites Argument ein Rang verwendet, der die Reihenfolge der auszuführenden Rückrufe angibt.

Falls ein Rückruf den Wert „false“ zurückgibt, werden die darauf folgenden Rückrufe in der Ausführungskette nicht ausgeführt.
