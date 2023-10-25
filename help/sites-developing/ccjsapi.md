---
title: ClientContext-JavaScript-API
seo-title: Client Context JavaScript API
description: Erfahren Sie mehr über die JavaScript-API für ClientContext in Adobe Experience Manager.
seo-description: The JavaScript API for Client Context
uuid: be58998c-f23e-4768-8394-1f1ad3994c4c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: a6e5810b-dac5-4137-93cf-5d8d53cacc49
feature: Context Hub
exl-id: 24bdf9fc-71e6-4b99-9dad-0f41a5e36b98
source-git-commit: b703f356f9475eeeafb1d5408c650d9c6971a804
workflow-type: tm+mt
source-wordcount: '3159'
ht-degree: 27%

---

# ClientContext-JavaScript-API{#client-context-javascript-api}

## CQ_Analytics.ClientContextMgr {#cq-analytics-clientcontextmgr}

Das Objekt CQ_Analytics.ClientContextMgr ist ein Singleton, das einen Satz an selbstregistrierten Sitzungsspeichern enthält und Methoden für die Registrierung, Speicherung und Verwaltung der Sitzungsspeicher bereitstellt.

Erweitert CQ_Analytics.PersistedSessionStore.

### Methoden {#methods}

#### getRegisteredStore(name) {#getregisteredstore-name}

Gibt einen Sitzungsspeicher mit einem angegebenen Namen zurück. Siehe auch [Zugreifen auf einen Sitzungsspeicher](/help/sites-developing/client-context.md#accessing-session-stores).

**Parameter**

* name: Zeichenfolge. Der Name des Sitzungsspeichers.

**Rückgabe**

Ein CQ_Analytics.SessionStore -Objekt, das den Sitzungsspeicher des angegebenen Namens darstellt. Gibt `null` zurück, wenn kein Speicher mit dem angegebenen Namen vorhanden ist.

#### register(sessionstore) {#register-sessionstore}

Registriert einen Sitzungsspeicher bei ClientContext. Löst nach Abschluss die Speicherregister- und StoreUpdate-Ereignisse aus.

**Parameter**

* sessionstore: CQ_Analytics.SessionStore. Das zu registrierende Sitzungsspeicherobjekt.

**Rückgabe**

Kein zurückgegebener Wert.

## CQ_Analytics.ClientContextUtils {#cq-analytics-clientcontextutils}

Stellt Methoden für die Überwachung bereit, um die Aktivierung und Registrierung von Sitzungsspeicher zu erkennen. Siehe auch [Überprüfen der Definition und Initialisierung eines Sitzungsspeichers](/help/sites-developing/client-context.md#checking-that-a-session-store-is-defined-and-initialized).

### Methoden {#methods-1}

#### onStoreInitialized(storeName, callback, delay) {#onstoreinitialized-storename-callback-delay}

Registriert eine Callback-Funktion, die aufgerufen wird, wenn ein Sitzungsspeicher initialisiert wird. Geben Sie für Stores, die mehrmals initialisiert werden, eine Callback-Verzögerung an, damit die Callback-Funktion nur einmal aufgerufen wird:

* Wenn der Speicher während der Verzögerungszeit einer vorherigen Initialisierung initialisiert wird, wird der vorherige Funktionsaufruf abgebrochen und die Funktion für die aktuelle Initialisierung erneut aufgerufen.
* Wenn der Verzögerungszeitraum vor einer nachfolgenden Initialisierung verfällt, wird die Callback-Funktion zweimal ausgeführt.

Beispielsweise basiert ein Sitzungsspeicher auf einem JSON-Objekt und wird über eine JSON-Anfrage abgerufen. Die folgenden Initialisierungsszenarien sind möglich:

* Die Anfrage ist abgeschlossen, Daten werden abgerufen und in den Store geladen. In diesem Fall erfolgt die Initialisierung einmal.
* Die Anfrage schlägt fehl (Zeitüberschreitung). In diesem Fall erfolgt keine Initialisierung und es sind keine Daten im Store vorhanden.
* Der Speicher wird mit Standardwerten vorbelegt (init-Eigenschaften), die Anfrage schlägt jedoch fehl (Zeitüberschreitung). Es gibt nur eine Initialisierung mit Standardwerten.
* Der Speicher ist vorbelegt.

Wenn die Verzögerung auf `true` oder eine Anzahl an Millisekunden festgelegt ist, wartet die Methode, bevor sie die Callback-Methode aufruft. Wenn ein weiteres Initialisierungsereignis ausgelöst wird, bevor die Verzögerung übergeben wird, wartet es, bis die Verzögerungszeit ohne Initialisierungsereignis überschritten wird. Dadurch kann gewartet werden, bis ein zweites Initialisierungsereignis ausgelöst wird, und die Callback-Funktion wird im optimalen Fall aufgerufen.

**Parameter**

* storeName: String. Der Name des Sitzungsspeichers, dem der Listener hinzugefügt werden soll.
* callback: Funktion. Die Funktion, die bei der Speicherinitialisierung aufgerufen werden soll.
* delay: Boolesch oder Zahl. Die Zeitdauer, die den Aufruf der Callback-Funktion verzögert, in Millisekunden. Der boolesche Wert `true` nutzt den Standardwert `200 ms`. Beim booleschen Wert `false` oder einer negativen Zahl wird keine Verzögerung eingesetzt.

**Rückgabe**

Kein zurückgegebener Wert.

#### onStoreRegistered(storeName, callback) {#onstoreregistered-storename-callback}

Registriert eine Callback-Funktion, wenn ein Sitzungsspeicher registriert wird. Das Registrierungsereignis tritt auf, wenn ein Speicher bei [CQ_Analytics.ClientContextMgr](#cq-analytics-clientcontextmgr) registriert wird.

**Parameter**

* storeName: String. Der Name des Sitzungsspeichers, dem der Listener hinzugefügt werden soll.
* callback: Funktion. Die Funktion, die bei der Speicherinitialisierung aufgerufen werden soll.

**Rückgabe**

Kein zurückgegebener Wert.

## CQ_Analytics.JSONPStore {#cq-analytics-jsonpstore}

Ein nicht persistenter Sitzungsspeicher, der JSON-Daten enthält. Die Daten werden von einem externen JSONP-Dienst abgerufen. Mit der Methode `getInstance` oder `getRegisteredInstance` können Sie eine Instanz dieser Klasse erstellen.

Erweitert CQ_Analytics.JSONStore.

### Eigenschaften {#properties}

Informationen zu geerbten Eigenschaften finden Sie unter CQ_Analytics.JSONStore und CQ_Analytics.SessionStore .

### Methoden {#methods-2}

Weitere Informationen zu geerbten Methoden finden Sie unter CQ_Analytics.JSONStore und CQ_Analytics.SessionStore .

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback) {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback}

Erstellt ein CQ_Analytics.JSONPStore-Objekt.

**Parameter**

* storeName: String. Der Name, der als STORENAME-Eigenschaft verwendet werden soll. Der Wert der STOREKEY-Eigenschaft ist auf storeName mit allen Großbuchstaben eingestellt. Wenn kein storeName angegeben ist, gibt die Methode null zurück.
* serviceURL: String. Die URL des JSONP-Dienstes
* dynamicData: (Optionales) Objekt. JSON-Daten, die an die Initialisierungsdaten des Stores angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* deferLoading: (Optional) Boolesch. Der Wert true verhindert, dass der JSONP-Dienst bei der Objekterstellung aufgerufen wird. Der Wert false bewirkt, dass der JSONP-Dienst aufgerufen wird.
* loadingCallback: (optional) Zeichenfolge. Der Name der Funktion, die für die Verarbeitung des vom JSONP-Dienst zurückgegebenen JSONP-Objekts aufgerufen werden soll. Die Rückruffunktion muss einen einzelnen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Das neue CQ_Analytics.JSONPStore-Objekt oder „null“, wenn storeName „null“ ist

#### getServiceURL() {#getserviceurl}

Ruft die URL des JSONP-Dienstes ab, den dieses Objekt zum Abrufen von JSON-Daten verwendet.

**Parameter**

Ohne.

**Rückgabe**

Ein String, der die Dienst-URL darstellt, oder null, wenn keine Dienst-URL konfiguriert wurde.

#### load(serviceURL, dynamicData, callback) {#load-serviceurl-dynamicdata-callback}

Ruft den JSONP-Dienst auf. Die JSONP-URL ist die Dienst-URL, der ein Callback-Funktionsname vorangestellt wird.

**Parameter**

* serviceURL: (Optional) Zeichenfolge. Der JSONP-Dienst, der aufgerufen werden soll. Der Wert null bewirkt, dass die bereits konfigurierte Dienst-URL verwendet wird. Ein Wert ungleich null legt den JSONP-Dienst fest, der für dieses Objekt verwendet werden soll. (Siehe setServiceURL.)
* dynamicData: (Optionales) Objekt. JSON-Daten, die an die Initialisierungsdaten des Stores angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* callback: (Optional) Zeichenfolge. Der Name der Funktion, die für die Verarbeitung des vom JSONP-Dienst zurückgegebenen JSONP-Objekts aufgerufen werden soll. Die Rückruffunktion muss einen einzelnen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Kein zurückgegebener Wert.

#### registerNewInstance(storeName, serviceURL, dynamicData, callback) {#registernewinstance-storename-serviceurl-dynamicdata-callback}

Erstellt ein CQ_Analytics.JSONPStore-Objekt und registriert den Speicher bei ClientContext.

**Parameter**

* storeName: String. Der Name, der als STORENAME-Eigenschaft verwendet werden soll. Der Wert der STOREKEY-Eigenschaft ist auf storeName mit allen Großbuchstaben eingestellt. Wenn kein storeName angegeben ist, gibt die Methode null zurück.
* serviceURL: (Optional) Zeichenfolge. Die URL des JSONP-Dienstes.
* dynamicData: (Optionales) Objekt. JSON-Daten, die an die Initialisierungsdaten des Stores angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* callback: (Optional) Zeichenfolge. Der Name der Funktion, die für die Verarbeitung des vom JSONP-Dienst zurückgegebenen JSONP-Objekts aufgerufen werden soll. Die Rückruffunktion muss einen einzelnen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Das registrierte CQ_Analytics.JSONPStore-Objekt.

#### setServiceURL(serviceURL) {#setserviceurl-serviceurl}

Legt die URL des JSONP-Dienstes fest, der zum Abrufen von JSON-Daten verwendet werden soll.

**Parameter**

* serviceURL: String. Die URL des JSONP-Dienstes, der JSON-Daten bereitstellt

**Rückgabe**

Kein zurückgegebener Wert.

## CQ_Analytics.JSONStore {#cq-analytics-jsonstore}

Ein Container für ein JSON-Objekt. Erstellen Sie eine Instanz dieser Klasse, um einen nicht beständigen Sitzungsspeicher zu erstellen, der JSON-Daten enthält:

`myjsonstore = new CQ_Analytics.JSONStore`

Sie können einen Datensatz definieren, der den Store bei der Initialisierung füllt.

Erweitert CQ_Analytics.SessionStore.

### Eigenschaften {#properties-1}

#### STOREKEY {#storekey}

Der Schlüssel, der den Store identifiziert. Mit der Methode `getInstance` können Sie diesen Wert abrufen.

#### STORENAME {#storename}

Der Name des Speichers. Mit der Methode `getInstance` können Sie diesen Wert abrufen.

### Methoden {#methods-3}

Weitere Informationen zu geerbten Methoden finden Sie unter CQ_Analytics.SessionStore .

#### löschen() {#clear}

Entfernt die Sitzungsspeicherdaten und entfernt alle Initialisierungseigenschaften.

**Parameter**

Ohne.

**Rückgabe**

Kein zurückgegebener Wert.

#### getInstance(storeName, jsonData) {#getinstance-storename-jsondata}

Erstellt ein CQ_Analytics.JSONStore-Objekt mit einem angegebenen Namen, das mit den angegebenen JSON-Daten initialisiert wird (ruft die initJSON-Methode auf).

**Parameter**

* storeName: String. Der Name, der als STORENAME-Eigenschaft verwendet werden soll. Der Wert der STOREKEY-Eigenschaft ist auf storeName mit allen Großbuchstaben eingestellt.
* jsonData: Objekt. Ein Objekt, das JSON-Daten enthält.

**Rückgabe**

Das CQ_Analytics.JSONStore-Objekt.

#### getJSON() {#getjson}

Ruft die Daten des Sitzungsspeichers im JSON-Format ab.

**Parameter**

Ohne.

**Rückgabe**

Ein Objekt, das die Speicherdaten im JSON-Format darstellt.

#### init() {#init}

Löscht den Sitzungsspeicher und initialisiert ihn mit der Initialisierungseigenschaft. Legt die Initialisierungsmarkierung auf `true` fest und löst dann die Ereignisse `initialize` und `update` aus.

**Parameter**

Ohne.

**Rückgabe**

Keine zurückgegebenen Daten.

#### initJSON(jsonData, doNotClear) {#initjson-jsondata-donotclear}

Erstellt Initialisierungseigenschaften aus den Daten in einem JSON-Objekt. Optional können Sie alle vorhandenen Initialisierungseigenschaften entfernen.

Die Namen der Eigenschaften werden aus der Hierarchie der Daten im JSON-Objekt abgeleitet. Der folgende Beispielcode stellt ein JSON-Objekt dar:

```xml
{
A: "valueA",
B: {
     B1: "valueBB1"
    }
}
```

Für dieses Beispiel werden die folgenden Eigenschaften im Store erstellt:

```xml
A: "valueA"
B/B1: "valueBB1"
```

**Parameter**

* jsonData: Ein JSON-Objekt, das die zu speichernden Daten enthält.
* doNotClear: Beim Wert „true“ werden die vorhandenen Initialisierungseigenschaften beibehalten und die vom JSON-Objekt abgeleiteten Eigenschaften werden hinzugefügt. Bei „false“ werden die vorhandenen Initialisierungseigenschaften entfernt, bevor die vom JSON-Objekt abgeleiteten Eigenschaften hinzugefügt werden.

**Rückgabe**

Kein zurückgegebener Wert.

#### registerNewInstance(storeName, jsonData) {#registernewinstance-storename-jsondata}

Erstellt ein CQ_Analytics.JSONStore-Objekt mit einem angegebenen Namen, das mit den angegebenen JSON-Daten initialisiert wird (ruft die initJSON-Methode auf). Das neue Objekt wird automatisch bei Clickstream Cloud Manager registriert.

**Parameter**

* storeName: String. Der Name, der als STORENAME-Eigenschaft verwendet werden soll. Der Wert der STOREKEY-Eigenschaft ist auf storeName mit allen Großbuchstaben eingestellt.
* jsonData: Objekt. Ein Objekt, das JSON-Daten enthält.

**Rückgabe**

Das CQ_Analytics.JSONStore-Objekt.

## CQ_Analytics.Observable {#cq-analytics-observable}

Löst Ereignisse aus und ermöglicht es anderen Objekten, auf diese Ereignisse zu warten und zu reagieren. Klassen, die diese Klasse erweitern, können Ereignisse auslösen, die dazu führen, dass Listener aufgerufen werden.

### Methoden {#methods-4}

#### addListener(event, fct, scope) {#addlistener-event-fct-scope}

Registriert einen Listener für ein Ereignis. Siehe auch [Erstellen eines Listeners für die Reaktion auf eine Sitzungsspeicheraktualisierung](/help/sites-developing/client-context.md#creating-a-listener-to-react-to-a-session-store-update).

**Parameter**

* event: String. Der Name des Ereignisses, das überwacht werden soll.
* fct: Funktion. Die Funktion, die aufgerufen wird, wenn das Ereignis auftritt.
* scope: (optional) Objekt. Der Bereich, in dem die Handler-Funktion ausgeführt werden soll. Der &quot;this&quot;-Kontext der Handler-Funktion.

**Rückgabe**

Kein zurückgegebener Wert.

#### removeListener(event, fct) {#removelistener-event-fct}

Entfernt den angegebenen Ereignis-Handler für ein Ereignis.

**Parameter**

* event: String. Der Name des Ereignisses.
* fct: Funktion. Der Ereignishandler.

**Rückgabe**

Kein zurückgegebener Wert.

## CQ_Analytics.PersistedJSONPStore {#cq-analyics-persistedjsonpstore}

Ein persistenter Container eines JSON-Objekts, der von einem Remote-JSONP-Dienst abgerufen wird.

Erweitert CQ_Analytics.PersistedJSONStore.

### Methoden {#methods-5}

Weitere Informationen zu geerbten Methoden finden Sie unter CQ_Analytics.PersistedJSONStore .

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback) {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback-1}

Erstellt ein CQ_Analytics.PersistedJSONPStore-Objekt.

**Parameter**

* storeName: String. Der Name, der als STORENAME-Eigenschaft verwendet werden soll. Der Wert der STOREKEY-Eigenschaft ist auf storeName mit allen Großbuchstaben eingestellt. Wenn kein storeName angegeben ist, gibt die Methode null zurück.
* serviceURL: String. Die URL des JSONP-Dienstes
* dynamicData: (Optionales) Objekt. JSON-Daten, die an die Initialisierungsdaten des Stores angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* deferLoading: (Optional) Boolesch. Der Wert true verhindert, dass der JSONP-Dienst bei der Objekterstellung aufgerufen wird. Der Wert false bewirkt, dass der JSONP-Dienst aufgerufen wird.
* loadingCallback: (optional) Zeichenfolge. Der Name der Funktion, die für die Verarbeitung des vom JSONP-Dienst zurückgegebenen JSONP-Objekts aufgerufen werden soll. Die Rückruffunktion muss einen einzelnen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Das neue CQ_Analytics.PersistedJSONPStore-Objekt oder „null“, wenn storeName „null“ ist.

#### getServiceURL() {#getserviceurl-1}

Ruft die URL des JSONP-Dienstes ab, den dieses Objekt zum Abrufen von JSON-Daten verwendet.

**Parameter**

Ohne.

**Rückgabe**

Ein String, der die Dienst-URL darstellt, oder null, wenn keine Dienst-URL konfiguriert wurde.

#### load(serviceURL, dynamicData, callback) {#load-serviceurl-dynamicdata-callback-1}

Ruft den JSONP-Dienst auf. Die JSONP-URL ist die Dienst-URL, der ein Callback-Funktionsname vorangestellt wird.

**Parameter**

* serviceURL: (Optional) Zeichenfolge. Der JSONP-Dienst, der aufgerufen werden soll. Der Wert null bewirkt, dass die bereits konfigurierte Dienst-URL verwendet wird. Ein Wert ungleich null legt den JSONP-Dienst fest, der für dieses Objekt verwendet werden soll. (Siehe setServiceURL.)
* dynamicData: (Optionales) Objekt. JSON-Daten, die an die Initialisierungsdaten des Stores angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* callback: (Optional) Zeichenfolge. Der Name der Funktion, die für die Verarbeitung des vom JSONP-Dienst zurückgegebenen JSONP-Objekts aufgerufen werden soll. Die Rückruffunktion muss einen einzelnen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Kein zurückgegebener Wert.

#### registerNewInstance(storeName, serviceURL, dynamicData, callback) {#registernewinstance-storename-serviceurl-dynamicdata-callback-1}

Erstellt ein CQ_Analytics.PersistedJSONPStore-Objekt und registriert den Speicher bei ClientContext.

**Parameter**

* storeName: String. Der Name, der als STORENAME-Eigenschaft verwendet werden soll. Der Wert der STOREKEY-Eigenschaft ist auf storeName mit allen Großbuchstaben eingestellt. Wenn kein storeName angegeben ist, gibt die Methode null zurück.
* serviceURL: (Optional) Zeichenfolge. Die URL des JSONP-Dienstes.
* dynamicData: (Optionales) Objekt. JSON-Daten, die an die Initialisierungsdaten des Stores angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* callback: (Optional) Zeichenfolge. Der Name der Funktion, die für die Verarbeitung des vom JSONP-Dienst zurückgegebenen JSONP-Objekts aufgerufen werden soll. Die Rückruffunktion muss einen einzelnen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Das registrierte CQ_Analytics.PersistedJSONPStore-Objekt.

#### setServiceURL(serviceURL) {#setserviceurl-serviceurl-1}

Legt die URL des JSONP-Dienstes fest, der zum Abrufen von JSON-Daten verwendet werden soll.

**Parameter**

* serviceURL: String. Die URL des JSONP-Dienstes, der JSON-Daten bereitstellt

**Rückgabe**

Kein zurückgegebener Wert.

## CQ_Analytics.PersistedJSONStore {#cq-analytics-persistedjsonstore}

Ein persistenter Container eines JSON-Objekts.

Erweitert `CQ_Analytics.PersistedSessionStore`.

### Eigenschaften {#properties-2}

#### STOREKEY {#storekey-1}

Der Schlüssel, der den Store identifiziert. Mit der Methode `getInstance` können Sie diesen Wert abrufen.

#### STORENAME {#storename-1}

Der Name des Speichers. Mit der Methode `getInstance` können Sie diesen Wert abrufen.

### Methoden {#methods-6}

Weitere Informationen zu geerbten Methoden finden Sie unter CQ_Analytics.PersistedSessionStore .

#### getInstance(storeName, jsonData) {#getinstance-storename-jsondata-1}

Erstellt ein CQ_Analytics.PersistedJSONStore-Objekt mit einem angegebenen Namen, das mit den angegebenen JSON-Daten initialisiert wird (ruft die initJSON-Methode auf).

**Parameter**

* storeName: String. Der Name, der als STORENAME-Eigenschaft verwendet werden soll. Der Wert der STOREKEY-Eigenschaft ist auf storeName mit allen Großbuchstaben eingestellt.
* jsonData: Objekt. Ein Objekt, das JSON-Daten enthält.

**Rückgabe**

Das CQ_Analytics.PersistedJSONStore-Objekt.

#### getJSON() {#getjson-1}

Ruft die Daten des Sitzungsspeichers im JSON-Format ab.

**Parameter**

Ohne.

**Rückgabe**

Ein Objekt, das die Speicherdaten im JSON-Format darstellt.

#### initJSON(jsonData, doNotClear) {#initjson-jsondata-donotclear-1}

Erstellt Initialisierungseigenschaften aus den Daten in einem JSON-Objekt. Optional können Sie alle vorhandenen Initialisierungseigenschaften entfernen.

Die Namen der Eigenschaften werden aus der Hierarchie der Daten im JSON-Objekt abgeleitet. Der folgende Beispielcode stellt ein JSON-Objekt dar:

```xml
{
A: "valueA",
B: {
     B1: "valueBB1"
    }
}
```

Für dieses Beispiel werden die folgenden Eigenschaften im Store erstellt:

```xml
A: "valueA"
B/B1: "valueBB1"
```

**Parameter**

* jsonData: Ein JSON-Objekt, das die zu speichernden Daten enthält.
* doNotClear: Beim Wert „true“ werden die vorhandenen Initialisierungseigenschaften beibehalten und die vom JSON-Objekt abgeleiteten Eigenschaften werden hinzugefügt. Bei „false“ werden die vorhandenen Initialisierungseigenschaften entfernt, bevor die vom JSON-Objekt abgeleiteten Eigenschaften hinzugefügt werden.

**Rückgabe**

Kein zurückgegebener Wert.

#### registerNewInstance(storeName, jsonData) {#registernewinstance-storename-jsondata-1}

Erstellt ein CQ_Analytics.PersistedJSONStore-Objekt mit einem angegebenen Namen, das mit den angegebenen JSON-Daten initialisiert wird (ruft die initJSON-Methode auf). Das neue Objekt wird automatisch beim ClientContext-Manager registriert.

**Parameter**

* storeName: String. Der Name, der als STORENAME-Eigenschaft verwendet werden soll. Der Wert der STOREKEY-Eigenschaft ist auf storeName mit allen Großbuchstaben eingestellt.
* jsonData: Objekt. Ein Objekt, das JSON-Daten enthält.

**Rückgabe**

Das CQ_Analytics.PersistedJSONStore-Objekt.

## CQ_Analytics.PersistedSessionStore {#cq-analytics-persistedsessionstore}

Ein Container mit Eigenschaften und Werten. Die Daten werden mit CQ_Analytics.SessionPersistence gespeichert. Erstellen Sie eine Instanz dieser Klasse, um einen beständigen Sitzungsspeicher zu erstellen:

`mypersistedstore = new CQ_Analytics.PersistedSessionStore`

Erweitert CQ_Analytics.SessionStore.

### Eigenschaften {#properties-3}

#### STOREKEY {#storekey-2}

Der Standardwert ist `key`.

### Methoden {#methods-7}

Vererbte Methoden finden Sie unter CQ_Analytics.SessionStore .

Wenn die geerbten Methoden `clear`, `setProperty`, `setProperties`, `removeProperty` zum Ändern der Speicherdaten genutzt werden, werden die Änderungen automatisch gespeichert, es sei denn, die geänderten Eigenschaften werden als „nicht beständig“ markiert.

#### getStoreKey() {#getstorekey}

Ruft die Eigenschaft `STOREKEY` ab.

**Parameter**

Ohne

**Rückgabe**

Der Wert der Eigenschaft `STOREKEY`.

#### isPersisted(name) {#ispersisted-name}

Bestimmt, ob eine Dateneigenschaft beibehalten wird.

**Parameter**

* name: Zeichenfolge. Der Name der Eigenschaft.

**Rückgabe**

Der boolesche Wert `true`, wenn die Eigenschaft gespeichert wird, und der Wert `false`, wenn der Wert keine beständige Eigenschaft ist.

#### persist() {#persist}

Behält den Sitzungsspeicher bei. Der standardmäßige Persistenzmodus nutzt den Browser `localStorage` mit `ClientSidePersistence` als Name (`window.localStorage.set("ClientSidePersistance", store);`)

Wenn localStorage nicht verfügbar oder nicht beschreibbar ist, wird der Speicher als Eigenschaft des Fensters gespeichert.

Löst nach Abschluss das Ereignis `persist` aus.

**Parameter**

Ohne

**Rückgabe**

Kein zurückgegebener Wert.

#### reset(deferEvent) {#reset-deferevent}

Entfernt alle Dateneigenschaften aus dem Store und behält den Speicher bei. Löst optional nach Abschluss kein `udpate`-Ereignis aus.

**Parameter**

* deferEvent: Beim Wert „true“ wird das Ereignis `update` nicht ausgelöst. Beim Wert `false` wird das update-Ereignis ausgelöst.

**Rückgabe**

Kein zurückgegebener Wert.

#### setNonPersisted(name) {#setnonpersisted-name}

Kennzeichnet eine Dateneigenschaft als nicht persistent.

**Parameter**

* name: Zeichenfolge. Der Name der Eigenschaft, die nicht beibehalten werden soll.

**Rückgabe**

Kein Rückgabewert.

## CQ_Analytics.SessionStore {#cq-analytics-sessionstore}

CQ_Analytics.SessionStore stellt einen Sitzungsspeicher dar. Erstellen Sie eine Instanz dieser Klasse, um einen Sitzungsspeicher zu erstellen:

`mystore = new CQ_Analytics.SessionStore`

Erweitert CQ_Analytics.Observable.

### Eigenschaften {#properties-4}

#### STORENAME {#storename-2}

Der Name des Sitzungsspeichers. Verwenden Sie getName , um den Wert dieser Eigenschaft abzurufen.

### Methoden {#methods-8}

#### addInitProperty(name, value) {#addinitproperty-name-value}

Fügt den Initialisierungsdaten des Sitzungsspeichers eine Eigenschaft und einen Wert hinzu.

Verwenden Sie loadInitProperties , um die Sitzungsspeicherdaten mit den Initialisierungswerten zu füllen.

**Parameter**

* name: Zeichenfolge. Der Name der hinzuzufügenden Eigenschaft.
* value: String. Der -Wert der hinzuzufügenden Eigenschaft.

**Rückgabe**

Kein zurückgegebener Wert.

#### löschen() {#clear-1}

Entfernt alle Dateneigenschaften aus dem Store.

**Parameter**

Ohne.

**Rückgabe**

Kein Rückgabewert.

#### getData(excluded) {#getdata-excluded}

Gibt die Speicherdaten zurück. Schließt optional Namenseigenschaften aus den Daten aus. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

excluded: (Optional) Ein Array von Eigenschaftsnamen, die aus den zurückgegebenen Daten ausgeschlossen werden sollen.

**Rückgabe**

Ein Objekt von Eigenschaften und ihren Werten.

#### getInitProperty(name) {#getinitproperty-name}

Ruft den Wert einer Dateneigenschaft ab.

**Parameter**

* name: Zeichenfolge. Der Name der abzurufenden Dateneigenschaft.

**Rückgabe**

Der -Wert der data -Eigenschaft. Gibt `null` zurück, wenn der Sitzungsspeicher keine Eigenschaft des angegebenen Namens enthält.

#### getName() {#getname}

Gibt den Namen des Sitzungsspeichers zurück.

**Parameter**

Ohne.

**Rückgabe**

Ein String -Wert, der den Store-Namen darstellt.

#### getProperty(name, raw) {#getproperty-name-raw}

Gibt den Wert einer Eigenschaft zurück. Der Wert wird als Roheigenschaft oder XSS-gefilterter Wert zurückgegeben. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

* name: Zeichenfolge. Der Name der abzurufenden Dateneigenschaft.
* raw: Boolesch. Der Wert true bewirkt, dass der Rohwert der Eigenschaft zurückgegeben wird. Der Wert false bewirkt, dass der zurückgegebene Wert XSS-gefiltert wird.

**Rückgabe**

Der -Wert der data -Eigenschaft.

#### getPropertyNames(excluded) {#getpropertynames-excluded}

Gibt die Namen der Eigenschaften zurück, die der Sitzungsspeicher enthält. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

excluded: (Optional) Ein Array von Eigenschaftsnamen, die aus den Ergebnissen weggelassen werden sollen.

**Rückgabe**

Ein Array von String -Werten, die die Namen der Sitzungs-Eigenschaften darstellen.

#### getSessionStore() {#getsessionstore}

Gibt den Sitzungsspeicher zurück, der an das aktuelle Objekt angehängt ist.

**Parameter**

Ohne.

**Rückgabe**

this

#### init() {#init-1}

Markiert den Speicher als initialisiert und löst das `initialize`-Ereignis aus.

**Parameter**

Ohne.

**Rückgabe**

Kein zurückgegebener Wert.

#### isInitialized() {#isinitialized}

Gibt an, ob der Sitzungsspeicher initialisiert wurde.

**Parameter**

Ohne.

**Rückgabe**

Der Wert `true`, wenn der Speicher initialisiert wurde, und der Wert `false`, wenn der Speicher nicht initialisiert wurde.

#### loadInitProperties(obj, setValues) {#loadinitproperties-obj-setvalues}

Fügt die Eigenschaften eines bestimmten Objekts zu den Initialisierungsdaten des Sitzungsspeichers hinzu. Optional werden die Objektdaten auch zu den Store-Daten hinzugefügt.

**Parameter**

* obj: Ein Objekt, das Auflistungseigenschaften enthält.
* setValues: Wenn &quot;true&quot;, werden die obj-Eigenschaften den Sitzungsspeicherdaten hinzugefügt, wenn die Speicherdaten nicht bereits eine Eigenschaft desselben Namens enthalten. Bei &quot;false&quot;werden den Sitzungsspeicherdaten keine Daten hinzugefügt.

**Rückgabe**

Kein zurückgegebener Wert.

#### removeProperty(name) {#removeproperty-name}

Entfernt eine Eigenschaft aus dem Sitzungsspeicher. Löst nach Abschluss das Ereignis `update` aus. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

* name: Zeichenfolge. Der Name der zu entfernenden Eigenschaft.

**Rückgabe**

Kein zurückgegebener Wert.

#### Zurücksetzen() {#reset}

Stellt die Anfangswerte des Datenspeichers wieder her. Die Standardimplementierung entfernt einfach alle Daten. Löst nach Abschluss das Ereignis `update` aus.

**Parameter**

Ohne.

**Rückgabe**

Kein zurückgegebener Wert.

#### setProperties(properties) {#setproperties-properties}

Legt die Werte mehrerer Eigenschaften fest. Löst nach Abschluss das Ereignis `update` aus. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

* Eigenschaften: Objekt. Ein Objekt, das Auflistungseigenschaften enthält. Jeder Eigenschaftsname und -wert wird dem Store hinzugefügt.

**Rückgabe**

Kein zurückgegebener Wert.

#### setProperty(name, value) {#setproperty-name-value}

Legt den Wert einer Eigenschaft fest. Löst nach Abschluss das Ereignis `update` aus. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

* name: Zeichenfolge. Der Name der Eigenschaft.
* value: String. Eigenschaftswert.

**Rückgabe**

Kein zurückgegebener Wert.
