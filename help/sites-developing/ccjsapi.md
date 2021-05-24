---
title: ClientContext-JavaScript-API
seo-title: ClientContext-JavaScript-API
description: Die JavaScript-API für ClientContext
seo-description: Die JavaScript-API für ClientContext
uuid: be58998c-f23e-4768-8394-1f1ad3994c4c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: a6e5810b-dac5-4137-93cf-5d8d53cacc49
feature: Context-Hub
exl-id: 24bdf9fc-71e6-4b99-9dad-0f41a5e36b98
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3165'
ht-degree: 91%

---

# ClientContext-JavaScript-API{#client-context-javascript-api}

## CQ_Analytics.ClientContextMgr {#cq-analytics-clientcontextmgr}

Das Objekt CQ_Analytics.ClientContextMgr ist ein Singleton, das eine Reihe selbstregistrierter Sitzungsspeicher enthält und Methoden zum Registrieren, Beibehalten und Verwalten der Sitzungsspeicher bereitstellt.

Es erweitert CQ_Analytics.PersistedSessionStore.

### Methoden {#methods}

#### getRegisteredStore(name)  {#getregisteredstore-name}

Gibt einen Sitzungsspeicher eines festgelegten Namens zurück. Siehe auch [Zugreifen auf einen Sitzungsspeicher](/help/sites-developing/client-context.md#accessing-session-stores).

**Parameter**

* name: String. Der Name des Sitzungsspeichers.

**Rückgabe**

Ein CQ_Analytics.SessionStore-Objekt, das den Sitzungsspeicher des angegebenen Namens repräsentiert. Gibt `null` zurück, wenn kein Speicher mit dem angegebenen Namen vorhanden ist.

#### register(sessionstore) {#register-sessionstore}

Registriert einen Sitzungsspeicher mit ClientContext. Löst die storeregister- und storeupdate-Ereignisse nach Fertigstellung aus.

**Parameter**

* sessionstore: CQ_Analytics.SessionStore. Das zu registrierende Sitzungsspeicher-Objekt.

**Rückgabe**

Kein zurückgegebener Wert

## CQ_Analytics.ClientContextUtils  {#cq-analytics-clientcontextutils}

Stellt Methoden für die Überwachung bereit, um die Aktivierung und Registrierung von Sitzungsspeicher zu erkennen. Siehe auch [Überprüfen, ob ein Sitzungsspeicher definiert und initialisiert ist](/help/sites-developing/client-context.md#checking-that-a-session-store-is-defined-and-initialized).

### Methoden {#methods-1}

#### onStoreInitialized(storeName, callback, delay) {#onstoreinitialized-storename-callback-delay}

Registriert eine Callback-Funktion, wenn ein Sitzungsspeicher initialisiert wird. Legen Sie für Speicher, die mehrmals initialisiert werden, eine Callback-Verzögerung fest, damit die Callback-Funktion nur einmal aufgerufen wird:

* Wenn der Speicher während des Verzögerungszeitraums der vorherigen Initialisierung erneut initialisiert wird, wird der vorherige Funktionsaufruf abgebrochen und die Funktion wird erneut für die aktuelle Initialisierung aufgerufen.
* Wenn der Verzögerungszeitraum vorbei ist, bevor eine nachfolgende Initialisierung stattfindet, wird die Callback-Funktion zweimal ausgeführt.

Beispiel: Ein Sitzungsspeicher basiert auf einem JSON-Objekt und wird über eine JSON-Anfrage abgerufen. Die folgenden Initialisierungsszenarien sind möglich:

* Die Anfrage wird ausgeführt, die Daten werden abgerufen und in den Speicher geladen. In diesem Fall erfolgt die Initialisierung einmalig.
* Die Anfrage schlägt fehl (Zeitüberschreitung). In diesem Fall erfolgt die Initialisierung nicht und es werden keine Daten in den Speicher geladen.
* Der Speicher wird vorab mit Standardwerten (init-Eigenschaften) gefüllt, aber die Anforderung schlägt fehl (Zeitüberschreitung). Es erfolgt nur eine Initialisierung mit Standardwerten.
* Der Speicher wird vorab gefüllt.

Wenn die Verzögerung auf `true` oder eine Anzahl von Millisekunden festgelegt ist, wartet die Methode, bevor die Callback-Methode aufgerufen wird. Wenn ein anderes Initialisierungsereignis ausgelöst wird, bevor der Verzögerungszeitraum abgelaufen ist, wartet die Methode, bis der Verzögerungszeitraum ohne Initialisierungsereignis überschritten ist. So ist es möglich, zu warten, bis ein zweites Initialisierungsereignis ausgelöst wird, um die Callback-Funktion im Optimalfall aufzurufen.

**Parameter**

* storeName: String. Der Name des Sitzungsspeichers, der zum Listener hinzugefügt werden soll.
* callback: Funktion. Die Funktion, die bei der Speicherinitialisierung aufgerufen werden soll.
* delay: boolescher Wert oder Zahl. Die Zeit, für deren Dauer der Aufruf der Callback-Funktion verzögert werden soll, in Millisekunden. Der boolesche Wert `true` verwendet die Standardverzögerung von `200 ms`. Beim booleschen Wert`false` oder einer negativen Zahl wird keine Verzögerung eingesetzt.

**Rückgabe**

Kein zurückgegebener Wert

#### onStoreRegistered(storeName, callback)  {#onstoreregistered-storename-callback}

Registriert eine Callback-Funktion, wenn ein Sitzungsspeicher registriert wird. Das Registrierungsereignis tritt auf, wenn ein Store unter [CQ_Analytics.ClientContextMgr](#cq-analytics-clientcontextmgr) registriert wird.

**Parameter**

* storeName: Zeichenfolge. Der Name des Sitzungsspeichers, der zum Listener hinzugefügt werden soll.
* callback: Funktion. Die Funktion, die bei der Speicherinitialisierung aufgerufen werden soll.

**Rückgabe**

Kein zurückgegebener Wert

## CQ_Analytics.JSONPStore  {#cq-analytics-jsonpstore}

Ein nicht beständiger Sitzungsspeicher, der JSON-Daten enthält. Die Daten werden von einem externen JSONP-Dienst abgerufen. Mit der Methode `getInstance` oder `getRegisteredInstance` können Sie eine Instanz dieser Klasse erstellen.

Erweitert CQ_Analytics.JSONStore.

### Eigenschaften {#properties}

Informationen zu den geerbten Eigenschaften finden Sie unter CQ_Analytics.JSONStore und CQ_Analytics.SessionStore.

### Methoden  {#methods-2}

Informationen zu den geerbten Methoden finden Sie ebenfalls unter CQ_Analytics.JSONStore und CQ_Analytics.SessionStore.

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback)  {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback}

Erstellt ein CQ_Analytics.JSONPStore-Objekt.

**Parameter**

* storeName: Zeichenfolge. Der Name, der als STORENAME-Eigenschaft genutzt werden soll. Der Wert der STOREKEY-Eigenschaft wird auf storeName mit ausschließlich Großbuchstaben festgelegt. Wenn kein storeName angegeben wird, gibt die Methode „null“ zurück.
* serviceURL: String. Die URL des JSONP-Dienstes.
* dynamicData: (optional) Objekt. JSON-Daten, die an die Initialisierungsdaten des Speichers angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* deferLoading: (optional) boolescher Wert. Der Wert „true“ verhindert, dass der JSONP-Dienst bei der Objekterstellung aufgerufen wird. Bei „false“ wird der JSONP-Dienst aufgerufen.
* loadingCallback: (Optional) Zeichenfolge. Der Name der Funktion, die für die Verarbeitung des JSONP-Objekts aufgerufen werden soll, das der JSONP-Dienst zurückgibt. Die Callback-Funktion muss einen einzigen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Das neue CQ_Analytics.JSONPStore-Objekt oder null , wenn storeName null ist.

#### getServiceURL() {#getserviceurl}

Ruft die URL des JSONP-Dienstes ab, mit dem dieses Objekt JSON-Daten abruft.

**Parameter**

Kein.

**Rückgabe**

Ein String, der die Dienst-URL repräsentiert, oder „null“, wenn keine Dienst-URL konfiguriert wurde.

#### load(serviceURL, dynamicData, callback)  {#load-serviceurl-dynamicdata-callback}

Ruft den JSONP-Dienst auf. Die JSONP-URL ist die Dienst-URL, der ein Callback-Funktionsname vorangestellt wird.

**Parameter**

* serviceURL: (optional) String. Der JSONP-Dienst, der aufgerufen werden soll. Beim Wert „null“ wird die bereits konfigurierte Dienst-URL verwendet. Ein anderer Wert als „null“ legt den JSONP-Dienst fest, der für dieses Objekt verwendet werden soll. (Siehe setServiceURL.)
* dynamicData: (optional) Objekt. JSON-Daten, die an die Initialisierungsdaten des Speichers angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* callback: (optional) String. Der Name der Funktion, die für die Verarbeitung des JSONP-Objekts aufgerufen werden soll, das der JSONP-Dienst zurückgibt. Die Callback-Funktion muss einen einzigen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Kein zurückgegebener Wert

#### registerNewInstance(storeName, serviceURL, dynamicData, callback)  {#registernewinstance-storename-serviceurl-dynamicdata-callback}

Erstellt ein CQ_Analytics.JSONPStore-Objekt und registriert den Store bei ClientContext.

**Parameter**

* storeName: Zeichenfolge. Der Name, der als STORENAME-Eigenschaft genutzt werden soll. Der Wert der STOREKEY-Eigenschaft wird auf storeName mit ausschließlich Großbuchstaben festgelegt. Wenn kein storeName angegeben wird, gibt die Methode „null“ zurück.
* serviceURL: (optional) String. Die URL des JSONP-Dienstes.
* dynamicData: (optional) Objekt. JSON-Daten, die an die Initialisierungsdaten des Speichers angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* callback: (optional) String. Der Name der Funktion, die für die Verarbeitung des JSONP-Objekts aufgerufen werden soll, das der JSONP-Dienst zurückgibt. Die Callback-Funktion muss einen einzigen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Das registrierte CQ_Analytics.JSONPStore-Objekt

#### setServiceURL(serviceURL)  {#setserviceurl-serviceurl}

Legt die URL des JSONP-Dienstes fest, der zum Abrufen der JSON-Daten genutzt werden soll.

**Parameter**

* serviceURL: Zeichenfolge. Die URL des JSONP-Dienstes, der JSON-Daten bereitstellt.

**Rückgabe**

Kein zurückgegebener Wert

## CQ_Analytics.JSONStore  {#cq-analytics-jsonstore}

Ein Container für ein JSON-Objekt. Erstellen Sie eine Instanz dieser Klasse, um einen nicht beständigen Sitzungsspeicher zu erstellen, der JSON-Daten enthält:

`myjsonstore = new CQ_Analytics.JSONStore`

Sie können eine Reihe von Daten definieren, die den Speicher nach der Initialisierung befüllen.

Erweitert CQ_Analytics.SessionStore.

### Eigenschaften {#properties-1}

#### STOREKEY {#storekey}

Der Schlüssel, der den Speicher identifiziert. Mit der Methode `getInstance` können Sie diesen Wert abrufen.

#### STORENAME {#storename}

Der Name des Stores. Mit der Methode `getInstance` können Sie diesen Wert abrufen.

### Methoden {#methods-3}

Informationen zu geerbten Methoden finden Sie unter CQ_Analytics.SessionStore.

#### clear() {#clear}

Löscht die Sitzungsspeicherdaten und alle Initialisierungseigenschaften.

**Parameter**

Kein.

**Rückgabe**

Kein zurückgegebener Wert

#### getInstance(storeName, jsonData)  {#getinstance-storename-jsondata}

Erstellt ein CQ_Analytics.JSONStore-Objekt mit einem angegebenen Namen, das mit den angegebenen JSON-Daten initialisiert wird (ruft die initJSON-Methode auf).

**Parameter**

* storeName: Zeichenfolge. Der Name, der als STORENAME-Eigenschaft genutzt werden soll. Der Wert der STOREKEY-Eigenschaft wird auf storeName mit ausschließlich Großbuchstaben festgelegt.
* jsonData: Objekt. Ein Objekt, das JSON-Daten enthält.

**Rückgabe**

Das CQ_Analytics.JSONStore-Objekt.

#### getJSON() {#getjson}

Ruft die Daten des Sitzungsspeichers im JSON-Format ab.

**Parameter**

Kein.

**Rückgabe**

Ein Objekt, das die Speicherdaten im JSON-Format repräsentiert.

#### init() {#init}

Löscht den Sitzungsspeicher und initialisiert ihn mit der Initialisierungseigenschaft. Legt das Initialisierungsflag auf `true` fest und löst dann die Ereignisse `initialize` und `update` aus.

**Parameter**

Kein.

**Rückgabe**

Keine zurückgegebenen Daten

#### initJSON(jsonData, doNotClear)  {#initjson-jsondata-donotclear}

Erstellt Initialisierungseigenschaften von den Daten in einem JSON-Objekt. Sie können optional alle vorhandenen Initialisierungseigenschaften entfernen.

Die Namen der Eigenschaften werden aus der Hierarchie der Daten im JSON-Objekt abgeleitet. Der folgende Beispielcode repräsentiert ein JSON-Objekt:

```xml
{
A: "valueA",
B: {
     B1: "valueBB1"
    }
}
```

Für dieses Beispiel werden die folgenden Eigenschaften im Speicher erstellt:

```xml
A: "valueA"
B/B1: "valueBB1"
```

**Parameter**

* jsonData: ein JSON-Objekt, das die zu speichernden Daten enthält
* doNotClear: Der Wert true behält die vorhandenen Initialisierungseigenschaften bei und fügt die vom JSON-Objekt abgeleiteten hinzu. Der Wert false entfernt vorhandene Initialisierungseigenschaften, bevor die vom JSON-Objekt abgeleiteten Eigenschaften hinzugefügt werden.

**Rückgabe**

Kein zurückgegebener Wert

#### registerNewInstance(storeName, jsonData)  {#registernewinstance-storename-jsondata}

Erstellt ein CQ_Analytics.JSONStore-Objekt mit einem angegebenen Namen, das mit den angegebenen JSON-Daten initialisiert wird (ruft die initJSON-Methode auf). Das neue Objekt wird automatisch mit dem Clickstream Cloud Manager registriert.

**Parameter**

* storeName: Zeichenfolge. Der Name, der als STORENAME-Eigenschaft genutzt werden soll. Der Wert der STOREKEY-Eigenschaft wird auf storeName mit ausschließlich Großbuchstaben festgelegt.
* jsonData: Objekt. Ein Objekt, das JSON-Daten enthält.

**Rückgabe**

Das CQ_Analytics.JSONStore-Objekt.

## CQ_Analytics.Observable  {#cq-analytics-observable}

Löst Ereignisse aus und ermöglicht es, dass andere Objekte auf diese Ereignisse warten und auf sie reagieren. Klassen, die diese Klasse erweitern, können Ereignisse auslösen, die zum Aufrufen von Listenern führen.

### Methoden  {#methods-4}

#### addListener(event, fct, scope) {#addlistener-event-fct-scope}

Registriert einen Listener für ein Ereignis. Siehe auch [Erstellen eines Listeners, der auf eine Aktualisierung des Sitzungsspeichers reagiert](/help/sites-developing/client-context.md#creating-a-listener-to-react-to-a-session-store-update).

**Parameter**

* event: String. Der Name des Ereignisses, auf das gewartet werden soll.
* fct: Funktion. Die Funktion, die aufgerufen wird, wenn das Ereignis eintritt.
* Umfang: (Optional) Objekt. Der Umfang, in dem die Handler-Funktion ausgeführt werden soll. Der „this“-Kontext der Handler-Funktion.

**Rückgabe**

Kein zurückgegebener Wert

#### removeListener(event, fct)  {#removelistener-event-fct}

Entfernt den angegeben Ereignis-Handler für ein Ereignis.

**Parameter**

* event: Zeichenfolge. Der Name des Ereignisses.
* fct: Funktion. Der Ereignis-Handler.

**Rückgabe**

Kein zurückgegebener Wert

## CQ_Analyics.PersistedJSONPStore  {#cq-analyics-persistedjsonpstore}

Ein beständiger Container eines JSON-Objekts, der von einem Remote-JSONP-Dienst abgerufen wird.

Erweitert CQ_Analytics.PersistedJSONStore.

### Methoden  {#methods-5}

Informationen zu geerbten Methoden finden Sie auch unter CQ_Analytics.PersistedJSONStore.

#### getInstance(storeName, serviceURL, dynamicData, deferLoading, loadingCallback)  {#getinstance-storename-serviceurl-dynamicdata-deferloading-loadingcallback-1}

Erstellt ein CQ_Analytics.PersistedJSONPStore-Objekt.

**Parameter**

* storeName: Zeichenfolge. Der Name, der als STORENAME-Eigenschaft genutzt werden soll. Der Wert der STOREKEY-Eigenschaft wird auf storeName mit ausschließlich Großbuchstaben festgelegt. Wenn kein storeName angegeben wird, gibt die Methode „null“ zurück.
* serviceURL: Zeichenfolge. Die URL des JSONP-Dienstes.
* dynamicData: (optional) Objekt. JSON-Daten, die an die Initialisierungsdaten des Speichers angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* deferLoading: (optional) boolescher Wert. Der Wert „true“ verhindert, dass der JSONP-Dienst bei der Objekterstellung aufgerufen wird. Bei „false“ wird der JSONP-Dienst aufgerufen.
* loadingCallback: (Optional) Zeichenfolge. Der Name der Funktion, die für die Verarbeitung des JSONP-Objekts aufgerufen werden soll, das der JSONP-Dienst zurückgibt. Die Callback-Funktion muss einen einzigen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Das neue CQ_Analytics.PersistedJSONPStore-Objekt oder null , wenn storeName null ist.

#### getServiceURL() {#getserviceurl-1}

Ruft die URL des JSONP-Dienstes ab, mit dem dieses Objekt JSON-Daten abruft.

**Parameter**

Kein.

**Rückgabe**

Ein String, der die Dienst-URL repräsentiert, oder „null“, wenn keine Dienst-URL konfiguriert wurde.

#### load(serviceURL, dynamicData, callback)  {#load-serviceurl-dynamicdata-callback-1}

Ruft den JSONP-Dienst auf. Die JSONP-URL ist die Dienst-URL, der ein Callback-Funktionsname vorangestellt wird.

**Parameter**

* serviceURL: (optional) String. Der JSONP-Dienst, der aufgerufen werden soll. Beim Wert „null“ wird die bereits konfigurierte Dienst-URL verwendet. Ein anderer Wert als „null“ legt den JSONP-Dienst fest, der für dieses Objekt verwendet werden soll. (Siehe setServiceURL.)
* dynamicData: (optional) Objekt. JSON-Daten, die an die Initialisierungsdaten des Speichers angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* callback: (optional) String. Der Name der Funktion, die für die Verarbeitung des JSONP-Objekts aufgerufen werden soll, das der JSONP-Dienst zurückgibt. Die Callback-Funktion muss einen einzigen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Kein zurückgegebener Wert

#### registerNewInstance(storeName, serviceURL, dynamicData, callback)  {#registernewinstance-storename-serviceurl-dynamicdata-callback-1}

Erstellt ein CQ_Analytics.PersistedJSONPStore-Objekt und registriert den Store bei ClientContext.

**Parameter**

* storeName: Zeichenfolge. Der Name, der als STORENAME-Eigenschaft genutzt werden soll. Der Wert der STOREKEY-Eigenschaft wird auf storeName mit ausschließlich Großbuchstaben festgelegt. Wenn kein storeName angegeben wird, gibt die Methode „null“ zurück.
* serviceURL: (optional) String. Die URL des JSONP-Dienstes.
* dynamicData: (optional) Objekt. JSON-Daten, die an die Initialisierungsdaten des Speichers angehängt werden sollen, bevor die Callback-Funktion aufgerufen wird.
* callback: (optional) String. Der Name der Funktion, die für die Verarbeitung des JSONP-Objekts aufgerufen werden soll, das der JSONP-Dienst zurückgibt. Die Callback-Funktion muss einen einzigen Parameter definieren, der ein CQ_Analytics.JSONPStore-Objekt ist.

**Rückgabe**

Das registrierte CQ_Analytics.PersistedJSONPStore-Objekt

#### setServiceURL(serviceURL)  {#setserviceurl-serviceurl-1}

Legt die URL des JSONP-Dienstes fest, der zum Abrufen der JSON-Daten genutzt werden soll.

**Parameter**

* serviceURL: Zeichenfolge. Die URL des JSONP-Dienstes, der JSON-Daten bereitstellt.

**Rückgabe**

Kein zurückgegebener Wert

## CQ_Analytics.PersistedJSONStore  {#cq-analytics-persistedjsonstore}

Ein beständiger Container eines JSON-Objekts.

Erweitert `CQ_Analytics.PersistedSessionStore`.

### Eigenschaften {#properties-2}

#### STOREKEY {#storekey-1}

Der Schlüssel, der den Speicher identifiziert. Mit der Methode `getInstance` können Sie diesen Wert abrufen.

#### STORENAME {#storename-1}

Der Name des Stores. Mit der Methode `getInstance` können Sie diesen Wert abrufen.

### Methoden {#methods-6}

Informationen zu geerbten Methoden finden Sie auch unter CQ_Analytics.PersistedSessionStore.

#### getInstance(storeName, jsonData)  {#getinstance-storename-jsondata-1}

Erstellt ein CQ_Analytics.PersistedJSONStore-Objekt mit einem angegebenen Namen, das mit den angegebenen JSON-Daten initialisiert wird (ruft die initJSON-Methode auf).

**Parameter**

* storeName: Zeichenfolge. Der Name, der als STORENAME-Eigenschaft genutzt werden soll. Der Wert der STOREKEY-Eigenschaft wird auf storeName mit ausschließlich Großbuchstaben festgelegt.
* jsonData: Objekt. Ein Objekt, das JSON-Daten enthält.

**Rückgabe**

Das CQ_Analytics.PersistedJSONStore-Objekt.

#### getJSON()  {#getjson-1}

Ruft die Daten des Sitzungsspeichers im JSON-Format ab.

**Parameter**

Kein.

**Rückgabe**

Ein Objekt, das die Speicherdaten im JSON-Format repräsentiert.

#### initJSON(jsonData, doNotClear)  {#initjson-jsondata-donotclear-1}

Erstellt Initialisierungseigenschaften von den Daten in einem JSON-Objekt. Sie können optional alle vorhandenen Initialisierungseigenschaften entfernen.

Die Namen der Eigenschaften werden aus der Hierarchie der Daten im JSON-Objekt abgeleitet. Der folgende Beispielcode repräsentiert ein JSON-Objekt:

```xml
{
A: "valueA",
B: {
     B1: "valueBB1"
    }
}
```

Für dieses Beispiel werden die folgenden Eigenschaften im Speicher erstellt:

```xml
A: "valueA"
B/B1: "valueBB1"
```

**Parameter**

* jsonData: ein JSON-Objekt, das die zu speichernden Daten enthält
* doNotClear: Der Wert true behält die vorhandenen Initialisierungseigenschaften bei und fügt die vom JSON-Objekt abgeleiteten hinzu. Der Wert false entfernt vorhandene Initialisierungseigenschaften, bevor die vom JSON-Objekt abgeleiteten Eigenschaften hinzugefügt werden.

**Rückgabe**

Kein zurückgegebener Wert

#### registerNewInstance(storeName, jsonData)  {#registernewinstance-storename-jsondata-1}

Erstellt ein CQ_Analytics.PersistedJSONStore-Objekt mit einem angegebenen Namen, das mit den angegebenen JSON-Daten initialisiert wird (ruft die initJSON-Methode auf). Das neue Objekt wird automatisch mit dem ClientContext-Manager registriert.

**Parameter**

* storeName: Zeichenfolge. Der Name, der als STORENAME-Eigenschaft genutzt werden soll. Der Wert der STOREKEY-Eigenschaft wird auf storeName mit ausschließlich Großbuchstaben festgelegt.
* jsonData: Objekt. Ein Objekt, das JSON-Daten enthält.

**Rückgabe**

Das CQ_Analytics.PersistedJSONStore-Objekt.

## CQ_Analytics.PersistedSessionStore  {#cq-analytics-persistedsessionstore}

Ein Container mit Eigenschaften und Werten. Die Daten werden mit CQ_Analytics.SessionPersistence gespeichert. Erstellen Sie eine Instanz dieser Klasse, um einen beständigen Sitzungsspeicher zu erstellen:

`mypersistedstore = new CQ_Analytics.PersistedSessionStore`

Erweitert CQ_Analytics.SessionStore.

### Eigenschaften {#properties-3}

#### STOREKEY {#storekey-2}

Der Standardwert ist `key`.

### Methoden {#methods-7}

Informationen zu geerbten Methoden finden Sie unter CQ_Analytics.SessionStore.

Wenn die geerbten Methoden `clear`, `setProperty`, `setProperties`, `removeProperty` zum Ändern der Speicherdaten verwendet werden, werden die Änderungen automatisch beibehalten, es sei denn, die geänderten Eigenschaften werden als nicht beständig gekennzeichnet.

#### getStoreKey() {#getstorekey}

Ruft die Eigenschaft `STOREKEY` ab.

**Parameter**

Kein

**Rückgabe**

Der Wert der Eigenschaft `STOREKEY`.

#### isPersisted(name) {#ispersisted-name}

Bestimmt, ob eine Dateneigenschaft gespeichert wird.

**Parameter**

* name: Zeichenfolge. Der Name der Eigenschaft.

**Rückgabe**

Der boolesche Wert `true`, wenn die Eigenschaft gespeichert wird, und der Wert `false`, wenn der Wert keine beständige Eigenschaft ist

#### persist() {#persist}

Behält den Sitzungsspeicher bei. Der standardmäßige Persistenzmodus verwendet den Browser `localStorage` mit `ClientSidePersistence` als Namen ( `window.localStorage.set("ClientSidePersistance", store);`).

Wenn localStorage nicht verfügbar oder nicht beschreibbar ist, wird der Speicher als Eigenschaft des Fensters gespeichert.

Löst nach Abschluss das Ereignis `persist` aus.

**Parameter**

Kein

**Rückgabe**

Kein zurückgegebener Wert

#### reset(deferEvent)  {#reset-deferevent}

Entfernt alle Dateneigenschaften aus dem Speicher und behält den Speicher bei. Das `udpate`-Ereignis wird optional nicht nach Abschluss ausgelöst.

**Parameter**

* deferEvent: Beim Wert „true“ wird das Ereignis `update` nicht ausgelöst. Beim Wert `false` wird das update-Ereignis ausgelöst.

**Rückgabe**

Kein zurückgegebener Wert

#### setNonPersisted(name)  {#setnonpersisted-name}

Markiert eine Dateneigenschaft als nicht beständig.

**Parameter**

* name: Zeichenfolge. Der Name der Eigenschaft, die nicht gespeichert werden soll.

**Rückgabe**

Kein Rückgabewert

## CQ_Analytics.SessionStore  {#cq-analytics-sessionstore}

CQ_Analytics.SessionStore repräsentiert einen Sitzungsspeicher. Erstellen Sie eine Instanz dieser Klasse, um einen Sitzungsspeicher zu erstellen:

`mystore = new CQ_Analytics.SessionStore`

Erweitert CQ_Analytics.Observable.

### Eigenschaften {#properties-4}

#### STORENAME {#storename-2}

Der Name des Sitzungsspeichers. Mit getName können Sie den Wert dieser Eigenschaft abrufen.

### Methoden  {#methods-8}

#### addInitProperty(name, value) {#addinitproperty-name-value}

Fügt eine Eigenschaft und einen Wert zu den Initialisierungsdaten des Sitzungsspeichers hinzu.

Mit loadInitProperties können Sie die Initialisierungswerte zu den Sitzungsspeicherdaten hinzufügen.

**Parameter**

* name: Zeichenfolge. Der Name der Eigenschaft, die hinzugefügt werden soll.
* Wert: String. Der Wert der Eigenschaft, die hinzugefügt werden soll.

**Rückgabe**

Kein zurückgegebener Wert

#### clear()  {#clear-1}

Entfernt alle Dateneigenschaften aus dem Speicher.

**Parameter**

Kein.

**Rückgabe**

Kein Rückgabewert

#### getData(excluded)  {#getdata-excluded}

Gibt die Speicherdaten zurück. Schließt optional Namenseigenschaften aus den Daten aus. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

excluded: (optional) ein Array von Eigenschaftsnamen, die aus den zurückgegebenen Daten ausgeschlossen werden sollen

**Rückgabe**

Ein Objekt von Eigenschaften und deren Werten

#### getInitProperty(name)  {#getinitproperty-name}

Ruft den Wert einer Dateneigenschaft ab.

**Parameter**

* name: Zeichenfolge. Der Name der Dateneigenschaft, die abgerufen werden soll.

**Rückgabe**

Der Wert der Dateneigenschaft. Gibt `null` zurück, wenn der Sitzungsspeicher keine Eigenschaft des angegebenen Namens enthält.

#### getName() {#getname}

Gibt den Namen des Sitzungsspeichers zurück.

**Parameter**

Kein.

**Rückgabe**

Ein Stringwert, der den Speichernamen repräsentiert

#### getProperty(name, raw)  {#getproperty-name-raw}

Gibt den Wert einer Eigenschaft zurück. Der Wert wird als Roheigenschaft oder XSS-gefilterter Wert zurückgegeben. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

* name: Zeichenfolge. Der Name der Dateneigenschaft, die abgerufen werden soll.
* raw: boolescher Wert. Beim Wert „true“ wird der Rohwert der Eigenschaft zurückgegeben. Bei „false“ wird der zurückgegebene Wert XSS-gefiltert.

**Rückgabe**

Der Wert der Dateneigenschaft.

#### getPropertyNames(excluded)  {#getpropertynames-excluded}

Gibt die Namen der Eigenschaften zurück, die der Sitzungsspeicher enthält. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

excluded: (optional) ein Array von Eigenschaftsnamen, die bei den Ergebnissen weggelassen werden sollen

**Rückgabe**

Ein Array von Stringwerten, die die Namen der Sitzungseigenschaften repräsentieren

#### getSessionStore() {#getsessionstore}

Gibt den Sitzungsspeicher zurück, der dem aktuellen Objekt angehängt ist.

**Parameter**

Kein.

**Rückgabe**

this

#### init()  {#init-1}

Markiert den Speicher als initialisiert und löst das `initialize`-Ereignis aus.

**Parameter**

Kein.

**Rückgabe**

Kein zurückgegebener Wert

#### isInitialized() {#isinitialized}

Gibt an, ob der Sitzungsspeicher initialisiert wurde.

**Parameter**

Kein.

**Rückgabe**

Der Wert `true`, wenn der Speicher initialisiert wurde, und der Wert `false`, wenn der Speicher nicht initialisiert wurde

#### loadInitProperties(obj, setValues) {#loadinitproperties-obj-setvalues}

Fügt die Eigenschaften eines angegebenen Objekts zu den Initialisierungsdaten des Sitzungsspeichers hinzu. Optional werden die Objektdaten auch zu den Speicherdaten hinzugefügt.

**Parameter**

* obj: ein Objekt, das aufzählbare Eigenschaften enthält
* setValues: Bei „true“ werden die obj-Eigenschaften zu den Sitzungsspeicherdaten hinzugefügt, wenn die Speicherdaten nicht bereits eine Eigenschaft desselben Namens enthalten. Bei „false“ werden keine Daten zu den Sitzungsspeicherdaten hinzugefügt.

**Rückgabe**

Kein zurückgegebener Wert

#### removeProperty(name)  {#removeproperty-name}

Entfernt eine Eigenschaft vom Sitzungsspeicher. Löst nach Abschluss das Ereignis `update` aus. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

* name: Zeichenfolge. Der Name der Dateneigenschaft, die entfernt werden soll.

**Rückgabe**

Kein zurückgegebener Wert

#### Zurücksetzen() {#reset}

Stellt die ursprünglichen Werte des Datenspeichers wieder her. Die Standardimplementierung entfernt einfach alle Daten. Löst nach Abschluss das Ereignis `update` aus.

**Parameter**

Kein.

**Rückgabe**

Kein zurückgegebener Wert

#### setProperties(properties)  {#setproperties-properties}

Legt die Werte mehrerer Eigenschaften fest. Löst nach Abschluss das Ereignis `update` aus. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

* Properties: Objekt. Ein Objekt, das aufzählbare Eigenschaften enthält. Jeder Eigenschaftsname und -wert wird zum Speicher hinzugefügt.

**Rückgabe**

Kein zurückgegebener Wert

#### setProperty(name, value)  {#setproperty-name-value}

Legt den Wert einer Eigenschaft fest. Löst nach Abschluss das Ereignis `update` aus. Ruft die `init`-Methode auf, wenn die Dateneigenschaft des Speichers nicht vorhanden ist.

**Parameter**

* name: Zeichenfolge. Der Name der Eigenschaft.
* Wert: String. Eigenschaftenwert.

**Rückgabe**

Kein zurückgegebener Wert
