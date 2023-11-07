---
title: Client-Kontext im Detail
description: ClientContext stellt eine dynamisch zusammengestellte Sammlung von Benutzerdaten dar.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
feature: Context Hub
exl-id: 38b9a795-1c83-406c-ab13-b4456da938dd
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '3000'
ht-degree: 90%

---

# Client-Kontext im Detail{#client-context-in-detail}

>[!NOTE]
>
>ClientContext wurde durch ContextHub abgelöst. Siehe [zugehörige Dokumentation](/help/sites-developing/contexthub.md) für Details.

ClientContext stellt eine dynamisch zusammengestellte Sammlung von Benutzerdaten dar. Mithilfe der Daten können Sie bestimmen, welcher Inhalt auf einer Web-Seite in einer bestimmten Situation angezeigt werden soll (Content-Targeting). Die Daten stehen auch für die Website-Analyse und für JavaScript auf der Seite zur Verfügung.

ClientContext umfasst im Wesentlichen die folgenden Aspekte:

* Der Sitzungsspeicher, der die Benutzerdaten enthält.
* Die Benutzeroberfläche, die die Benutzerdaten anzeigt und Tools zur Simulation des Benutzererlebnisses bietet.
* Eine [JavaScript-API](/help/sites-developing/ccjsapi.md) für die Interaktion mit Sitzungsspeichern.

So erstellen Sie einen eigenständigen Sitzungsspeicher und fügen ihn zu ClientContext hinzu oder erstellen einen Sitzungsspeicher, der mit einer Kontextspeicherkomponente verknüpft ist. Adobe Experience Manager (AEM) installiert mehrere Kontextspeicherkomponenten, die Sie sofort verwenden können. Nutzen Sie diese Komponenten einfach als Grundlage für Ihre eigenen Komponenten.

Weitere Informationen zum Öffnen von ClientContext, zum Konfigurieren der angezeigten Inhalte und zur Simulation des Benutzererlebnisses finden Sie unter [ClientContext](/help/sites-administering/client-context.md).

## Sitzungsspeicher {#session-stores}

ClientContext umfasst verschiedene Sitzungsspeicher, die Benutzerdaten enthalten. Speicherdaten stammen aus den folgenden Quellen:

* Client-Webbrowser
* Server (Informationen zum Speichern von Daten aus den Quellen Dritter finden Sie unter [JSONP-Store](/help/sites-administering/client-context.md#main-pars-variable-8))

Das Client Context-Framework bietet eine [JavaScript-API](/help/sites-developing/ccjsapi.md), mit der Sie mit Sitzungsspeichern interagieren können, um Benutzerdaten zu lesen und zu schreiben und auf Speicherereignisse zu hören und zu reagieren. Sie können auch Sitzungsspeicher für Benutzerdaten erstellen, die Sie für Content-Targeting oder andere Zwecke verwenden.

Sitzungsspeicherdaten verbleiben auf dem Client. Der Client-Kontext schreibt keine Daten an den Server zurück. Verwenden Sie zum Übermitteln von Daten an den Server ein Formular oder schreiben Sie einen benutzerdefinierten JavaScript-Code.

Jeder Sitzungsspeicher besteht aus Eigenschaft-Wert-Paaren. Der Sitzungsspeicher stellt eine Sammlung von Daten (beliebiger Art) dar, deren konzeptionelle Bedeutung vom Designer, Entwickler oder beidem bestimmt werden kann. Der folgende JavaScript-Beispiel-Code definiert ein Objekt, das die Profildaten darstellt, die der Sitzungsspeicher unter Umständen enthält:

```
{
  age: 20,
  authorizableId: "aparker@geometrixx.info",
  birthday: "27 Feb 1992",
  email: "aparker@geometrixx.info",
  formattedName: "Alison Parker",
  gender: "female",
  path: "/home/users/geometrixx/aparker@geometrixx.info/profile"
}
```

Ein Sitzungsspeicher kann über mehrere Browser-Sitzungen hinweg oder nur für die Sitzung, in der er erstellt wurde, beibehalten werden.

>[!NOTE]
>
>Für die Beibehaltung wird der Browser-Speicher oder Cookies verwendet (das `SessionPersistence`-Cookie). Der Browser-Speicher ist hierbei die gängigere Option.
>
>Wenn der Browser geschlossen und erneut geöffnet wird, kann ein Sitzungsspeicher mit den Werten aus einem persistierten Speicher geladen werden. Das Löschen des Browser-Caches ist erforderlich, um die alten Werte zu entfernen.

### Kontextspeicherkomponenten {#context-store-components}

Eine Kontextspeicherkomponente ist eine CQ-Komponente, die Client Context hinzugefügt werden kann. In der Regel zeigen Kontextspeicherkomponenten Daten aus einem Sitzungsspeicher an, mit dem sie verknüpft sind. Die Informationen, die Kontextspeicherkomponenten anzeigen, sind jedoch nicht auf Sitzungsspeicherdaten beschränkt.

Kontextspeicherkomponenten können die folgenden Elemente enthalten:

* JSP-Skripte, die das Erscheinungsbild in ClientContext definieren.
* Eigenschaften zum Auflisten der Komponente in Sidekick.
* Bearbeitungsdialogfelder zum Konfigurieren von Komponenteninstanzen.
* JavaScript, das den Sitzungsspeicher initialisiert.

Eine Beschreibung der installierten Kontextspeicherkomponenten, die Sie zum Kontextspeicher hinzufügen können, finden Sie unter [Verfügbare Client Context-Komponenten](/help/sites-administering/client-context.md#available-client-context-components).

>[!NOTE]
>
>Die Seitendaten sind keine Standardkomponenten in ClientContext mehr. Sie können sie ggf. hinzufügen, indem Sie ClientContext bearbeiten, die Komponente **Generische Store-Eigenschaften** hinzufügen und dann eine entsprechende Konfiguration durchführen, um den **Store** als `pagedata` zu definieren.

### Gezielte Inhaltsbereitstellung {#targeted-content-delivery}

Profilinformationen werden ebenfalls zur Bereitstellung [zielgerichteter Inhalte](/help/sites-authoring/content-targeting-touch.md) verwendet.

![clientcontext_targetedcontentdelivery](assets/clientcontext_targetedcontentdelivery.png) ![clientcontext_targetedcontentdeliverydetail](assets/clientcontext_targetedcontentdeliverydetail.png)

## Hinzufügen von Client Context zu einer Seite {#adding-client-context-to-a-page}

Schließen Sie die Client Context-Komponente in den Hauptteil Ihrer Web-Seiten ein, um Client Context zu aktivieren. Der Pfad für den ClientContext-Komponentenknoten lautet `/libs/cq/personalization/components/clientcontext`. Um die Komponente aufzunehmen, fügen Sie der JSP-Datei Ihrer Seitenkomponente, die Sie direkt unterhalb des `body`-Elements finden, den folgenden Code hinzu:

```java
<cq:include path="clientcontext" resourceType="cq/personalization/components/clientcontext"/>
```

Durch die ClientContext-Komponente lädt die Seite die Client-Bibliotheken, die Client Context implementieren:

* Die Client Context-JavaScript-API.
* Das ClientContext-Framework, das Sitzungsspeicher, Ereignisverwaltung usw. unterstützt.
* Segmente, die definiert sind.
* Die init.js-Skripte, die für jede Kontextspeicherkomponente generiert werden, die zu Client Context hinzugefügt wurde.
* (Nur Authoring-Instanz) Die Client Context-Benutzeroberfläche.

Die Client Context-Benutzeroberfläche ist nur in der Authoring-Instanz verfügbar.

## Erweitern von Client Context {#extending-client-context}

Um Client Context zu erweitern, erstellen Sie einen Sitzungsspeicher und zeigen Sie optional die Speicherdaten an:

* Erstellen Sie einen Sitzungsspeicher für die Benutzerdaten, die Sie für Content-Targeting und Web-Analyse benötigen.
* Erstellen Sie eine Kontextspeicherkomponente, damit Admins den zugehörigen Sitzungsspeicher konfigurieren und Speicherdaten in Client Context zu Testzwecken anzeigen können.

>[!NOTE]
>
>Bei der Auswahl (bzw. beim Erstellen) eines `JSONP`-Dienstes für die Bereitstellung der Daten können Sie einfach die `JSONP`-Kontextspeicherkomponente verwenden und dem JSONP-Dienst zuweisen. Dadurch wird der Sitzungsspeicher verarbeitet.

### Erstellen eines Sitzungsspeichers {#creating-a-session-store}

Erstellen Sie einen Sitzungsspeicher für die Daten, die Sie zu ClientContext hinzufügen und von diesem abrufen müssen. Im Allgemeinen verwenden Sie das folgende Verfahren, um einen Sitzungsspeicher zu erstellen:

1. Erstellen Sie einen Client-Bibliotheksordner mit dem Eigenschaftswert `categories` für `personalization.stores.kernel`. ClientContext lädt automatisch die Client-Bibliotheken für diese Kategorie.

1. Konfigurieren Sie den Client-Bibliotheksordner so, dass er eine Abhängigkeit vom Client-Bibliotheksordner `personalization.core.kernel` aufweist. Der Client-Bibliotheksordner `personalization.core.kernel` enthält die Client Context-JavaScript-API.

1. Fügen Sie den JavaScript-Code hinzu, der den Sitzungsspeicher erstellt und initialisiert.

Wenn Sie das JavaScript in die Client-Bibliothek „personalization.stores.kernel“ aufnehmen, wird der Store beim Laden des Client Context-Frameworks erstellt.

>[!NOTE]
>
>Wenn Sie einen Sitzungsspeicher als Teil einer Kontextspeicherkomponente erstellen, können Sie den JavaScript-Code alternativ in die Datei „init.js.jsp“ der Komponente einfügen. In diesem Fall wird der Sitzungsspeicher nur erstellt, wenn die Komponente zu Client Context hinzugefügt wird.

#### Sitzungsspeichertypen {#types-of-session-stores}

Sitzungsspeicher werden entweder während einer Browser-Sitzung erstellt und verfügbar gemacht oder im Browser-Speicher oder in Cookies persistiert. Die JavaScript-API für Client Context definiert mehrere Klassen, die beide Arten von Datenspeichern darstellen:

* ` [CQ_Analytics.SessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore)`: Diese Objekte befinden sich nur im Seiten-DOM. Die Daten werden erstellt und während der gesamten Lebensdauer der Seite beibehalten.
* ` [CQ_Analytics.PerstistedSessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-persistedsessionstore)`: Diese Objekte befinden sich im Seiten-DOM und werden entweder im Browser-Speicher oder in Cookies gespeichert. Die Daten sind seiten- und sitzungsübergreifend verfügbar.

Die API bietet außerdem Erweiterungen der Klassen, die sich speziell zum Speichern von JSON- oder JSONP-Daten eignen:

* Sitzungsgebundene Objekte: [CQ_Analytics.JSONStore](/help/sites-developing/ccjsapi.md#cq-analytics-jsonstore) und [CQ_Analytics.JSONPStore](/help/sites-developing/ccjsapi.md#cq-analytics-jsonpstore).

* Persistierte Objekte: [CQ_Analytics.PersistedJSONStore](/help/sites-developing/ccjsapi.md#cq-analytics-persistedjsonstore) und [CQ_Analytics.PersistedJSONPStore](/help/sites-developing/ccjsapi.md#cq-analyics-persistedjsonpstore).

#### Erstellen des Sitzungsspeicherobjekts {#creating-the-session-store-object}

Der JavaScript-Code Ihres Client-Bibliotheksordners erstellt und initialisiert den Sitzungsspeicher. Der Sitzungsspeicher muss mit dem Context Store Manager registriert werden. Im folgenden Beispiel wird ein [CQ_Analytics.SessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore)-Objekt erstellt und registriert.

```
//Create the session store
if (!CQ_Analytics.MyStore) {
    CQ_Analytics.MyStore = new CQ_Analytics.SessionStore();
    CQ_Analytics.MyStore.STOREKEY = "MYSTORE";
    CQ_Analytics.MyStore.STORENAME = "mystore";
    CQ_Analytics.MyStore.data={};
}
//register the session store
if (CQ_Analytics.ClientContextMgr){
    CQ_Analytics.ClientContextMgr.register(CQ_Analytics.MyStore)
}
```

In diesem Beispiel wird ein [CQ_Analytics.JSONStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore)-Objekt für die Speicherung von JSON-Daten erstellt und registriert.

```
if (!CQ_Analytics.myJSONStore) {
    CQ_Analytics.myJSONStore = CQ_Analytics.JSONStore.registerNewInstance("myjsonstore",{});
}
```

### Erstellen einer Kontextspeicherkomponente {#creating-a-context-store-component}

Erstellen Sie eine Kontextspeicherkomponente zum Rendern von Sitzungsspeicherdaten in Client Context. Nach der Erstellung können Sie Ihre Kontextspeicherkomponente auf Client Context ziehen, um Daten aus einem Sitzungsspeicher zu rendern. Kontextspeicherkomponenten bestehen aus den folgenden Elementen:

* JSP-Skript zum Rendern der Daten.
* Ein Bearbeitungsdialogfeld.
* Ein JSP-Skript zum Initialisieren des Sitzungsspeichers.
* (Optional) Ein Client-Bibliotheksordner, der den Sitzungsspeicher erstellt. Es ist nicht erforderlich, den Client-Bibliotheksordner einzubinden, wenn die Komponente einen vorhandenen Sitzungsspeicher verwendet.

#### Erweitern der bereitgestellten Kontextspeicherkomponenten {#extending-the-provided-context-store-components}

AEM stellt die Kontextspeicherkomponenten „genericstore“ und „genericstoreproperties“ bereit, die Sie erweitern können. Die Struktur der Speicherdaten bestimmt die Komponente, die erweitert wird:

* Eigenschaft-Wert-Paare: `GenericStoreProperties`-Komponente erweitern. Diese Komponente rendert automatisch die Speicher von Eigenschaft-Wert-Paaren. Es werden mehrere Interaktionspunkte bereitgestellt:

   * `prolog.jsp` und `epilog.jsp`: Komponenteninteraktion, mit der Sie serverseitige Logik vor oder nach dem Komponenten-Rendering hinzufügen können.

* Komplexe Daten: `GenericStore`-Komponente erweitern. Ihr Sitzungsspeicher benötigt eine &quot;Renderer&quot;-Methode, die jedes Mal aufgerufen wird, wenn die Komponente gerendert werden muss. Die Rendering-Funktion wird mit zwei Parametern aufgerufen:

   * `@param {String} store`
Der zu rendernde Speicher

   * `@param {String} divId`
Die ID des div-Elements, in das der Speicher gerendert werden muss.

>[!NOTE]
>
>Alle ClientContext-Komponenten sind Erweiterungen der Komponenten „Generischer Store“ oder „Generische Store-Eigenschaften“. Einige Beispiele sind im Ordner `/libs/cq/personalization/components/contextstores` installiert.

#### Konfigurieren des Erscheinungsbilds in Sidekick {#configuring-the-appearance-in-sidekick}

Bei der Bearbeitung von Client Context werden Kontextspeicherkomponenten in Sidekick angezeigt. Wie bei allen Komponenten bestimmen die Eigenschaften `componentGroup` und `jcr:title` der ClientContext-Komponente Gruppe und Namen der Komponente.

Alle Komponenten mit dem `componentGroup`-Eigenschaftswert `Client Context` werden standardmäßig im Sidekick angezeigt. Wenn Sie einen anderen Eigenschaftswert für `componentGroup` verwenden, muss die entsprechende Komponente im Designmodus manuell zum Sidekick hinzugefügt werden.

#### Instanzen der Kontextspeicherkomponenten {#context-store-component-instances}

Wenn Sie ClientContext eine Kontextspeicherkomponente hinzufügen, wird unter `/etc/clientcontext/default/content/jcr:content/stores` ein Knoten erstellt, der die Komponenteninstanz darstellt. Dieser Knoten enthält die Eigenschaftswerte, die mithilfe des Bearbeitungsdialogfelds der Komponente konfiguriert werden.

Wenn Client Context initialisiert wird, werden diese Knoten verarbeitet.

#### Initialisieren des zugehörigen Sitzungsspeichers {#initializing-the-associated-session-store}

Fügen Sie Ihrer Komponente eine init.js.jsp-Datei hinzu, um JavaScript-Code zu generieren, der den Sitzungsspeicher für Ihre Kontextspeicherkomponente initialisiert. Verwenden Sie beispielsweise das Initialisierungsskript, um die Konfigurationseigenschaften der Komponente abzurufen und in den Sitzungsspeicher einzuspeisen.

Der generierte JavaScript-Code wird der Seite hinzugefügt, wenn Client Context beim Laden der Seite sowohl auf der Authoring- als auch auf der Publishing-Instanz initialisiert wird. Diese JSP wird ausgeführt, bevor die Instanz der Kontextspeicherkomponente geladen und gerendert wird.

Im Code muss der MIME-Typ der Datei auf `text/javascript` festgelegt sein, andernfalls wird er nicht ausgeführt.

>[!CAUTION]
>
>Das Skript „init.js.jsp“ wird auf der Authoring- und Publishing-Instanz ausgeführt, jedoch nur, wenn die Kontextspeicherkomponente zu Client Context hinzugefügt wird.

Im folgenden Verfahren wird die Skriptdatei „init.js.jsp“ erstellt und der Code hinzugefügt, der den richtigen MIME-Typ festlegt. Der Code für die Speicherinitialisierung würde danach folgen.

1. Klicken Sie mit der rechten Maustaste auf den Knoten der Kontextspeicherkomponente und anschließend auf „Erstellen“ > „Datei erstellen“.
1. Geben Sie im Namensfeld `init.js.jsp` ein und klicken Sie dann auf „OK“.
1. Geben Sie oben auf der Seite den folgenden Code ein und klicken Sie dann auf „Alle speichern“.

   ```java
   <%@page contentType="text/javascript" %>
   ```

### Rendern von Sitzungsspeicherdaten für Genericstoreproperties-Komponenten {#rendering-session-store-data-for-genericstoreproperties-components}

Zeigen Sie Sitzungsspeicherdaten in Client Context in einem konsistenten Format an.

#### Anzeigen von Eigenschaftsdaten {#displaying-property-data}

In der Tag-Bibliothek (taglib) für die Personalisierung steht das Tag `personalization:storePropertyTag` zur Verfügung. Dieses Tag zeigt den Wert einer Eigenschaft aus dem Sitzungsspeicher an. Um das Tag zu verwenden, fügen Sie die folgende Codezeile in Ihre JSP-Datei ein:

```xml
<%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
```

Das Tag weist folgendes Format auf:

```xml
<personalization:storePropertyTag propertyName="property_name" store="session_store_name"/>
```

Das Attribut `propertyName` ist der Name der Speichereigenschaft, die angezeigt wird. Das Attribut `store` ist der Name des registrierten Speichers. Im folgenden Beispiel-Tag wird der Wert der Eigenschaft `authorizableId` des Speichers `profile` angezeigt:

```xml
<personalization:storePropertyTag propertyName="authorizableId" store="profile"/>
```

#### HTML-Struktur {#html-structure}

Der Client-Bibliotheksordner „personalization.ui“ (/etc/clientlibs/foundation/personalization/ui/themes/default) stellt die CSS-Stile bereit, die Client Context zum Formatieren des HTML-Codes verwendet. Im folgenden Code wird die empfohlene Struktur für die Anzeige von Speicherdaten dargestellt:

```xml
<div class="cq-cc-store">
   <div class="cq-cc-thumbnail">
      <div class="cq-cc-store-property">
           <!-- personalization:storePropertyTag for the store thumbnail image goes here -->
      </div>
   </div>
   <div class="cq-cc-content">
       <div class="cq-cc-store-property cq-cc-store-property-level0">
           <!-- personalization:storePropertyTag for a store property goes here -->
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level1">
           <!-- personalization:storePropertyTag for a store property goes here -->
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level2">
           <!-- personalization:storePropertyTag for a store property goes here -->
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level3">
           <!-- personalization:storePropertyTag for a store property goes here -->
       </div>
   </div>
   <div class="cq-cc-clear"></div>
</div>
```

Die Kontextspeicherkomponente `/libs/cq/personalization/components/contextstores/profiledata` wendet diese Struktur für die Anzeige von Daten aus dem Profilsitzungsspeicher an. Die Klasse `cq-cc-thumbnail` platziert das Miniaturbild. Die Klassen `cq-cc-store-property-level*x*` formatieren die alphanumerischen Daten:

* „level0“, „level1“ und „level2“ werden vertikal verteilt und verwenden weiße Schrift.
* „level3“ und alle weiteren Ebenen werden horizontal verteilt und verwenden weiße Schrift mit dunklerem Hintergrund.

![chlimage_1-4](assets/chlimage_1-4.png)

### Rendern von Sitzungsspeicherdaten für genericstore-Komponenten {#rendering-session-store-data-for-genericstore-components}

Gehen Sie wie folgt vor, um Store-Daten mithilfe einer genericstore-Komponente zu rendern:

* der JSP-Skriptkomponete das Tag personalization:storeRendererTag hinzufügen, um den Namen des Sitzungsspeichers zu identifizieren.
* eine Rendering-Methode für die Sitzungsspeicherklasse implementieren.

#### Ermitteln des genericstore-Sitzungsspeichers {#identifying-the-genericstore-session-store}

In der Tag-Bibliothek (taglib) für die Personalisierung steht das Tag `personalization:storePropertyTag` zur Verfügung. Dieses Tag zeigt den Wert einer Eigenschaft aus dem Sitzungsspeicher an. Um das Tag zu verwenden, fügen Sie die folgende Codezeile in Ihre JSP-Datei ein:

```xml
<%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
```

Das Tag weist folgendes Format auf:

```java
<personalization:storeRendererTag store="store_name"/>
```

#### Implementieren der Rendering-Methode für den Sitzungsspeicher {#implementing-the-session-store-renderer-method}

Ihr Sitzungsspeicher benötigt eine &quot;Renderer&quot;-Methode, die jedes Mal aufgerufen wird, wenn die Komponente gerendert werden muss. Die Rendering-Funktion wird mit zwei Parametern aufgerufen:

* @param {String} store
Der zu rendernde Speicher
* @param {String} divId
Die ID des div-Elements, in das der Speicher gerendert werden muss.

## Interagieren mit Sitzungsspeichern {#interacting-with-session-stores}

Verwenden Sie JavaScript, um mit Sitzungsspeichern zu interagieren.

### Zugreifen auf Sitzungsspeicher {#accessing-session-stores}

Rufen Sie ein Sitzungsspeicherobjekt ab, um Daten in den Speicher zu lesen oder zu schreiben. [CQ_Analytics.ClientContextMgr](/help/sites-developing/ccjsapi.md#cq-analytics-clientcontextmgr) bietet basierend auf den Speichernamen Speicherzugriff. Sobald Sie Zugriff haben, verwenden Sie die Methode [CQ_Analytics.SessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore) oder [CQ_Analytics.PersistedSessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-persistedsessionstore) für die Interaktion mit den Speicherdaten.

Im folgenden Beispiel wird der Speicher `profile` und anschließend die Eigenschaft `formattedName` daraus abgerufen.

```
function getName(){
   var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
   if(profilestore){
      return profilestore.getProperty("formattedName", false);
   } else {
      return null;
   }
}
```

### Erstellen eines Listeners für die Reaktion auf Aktualisierungen des Sitzungsspeichers {#creating-a-listener-to-react-to-a-session-store-update}

Sitzungsspeicher lösen Ereignisse aus, sodass es möglich ist, Listener hinzuzufügen und Ereignisse auf der Grundlage dieser Ereignisse zu triggern.

Die Sitzungsspeicher werden nach dem Muster `Observable` erstellt. Sie erweitern [`CQ_Analytics.Observable`](/help/sites-developing/ccjsapi.md#cq-analytics-observable), das die Methode ` [addListener](/help/sites-developing/ccjsapi.md#addlistener-event-fct-scope)` zur Verfügung stellt.

Im folgenden Beispiel wird dem Ereignis `update` ein Listener des Sitzungsspeichers `profile` hinzugefügt.

```
var profileStore = ClientContextMgr.getRegisteredStore("profile");
if( profileStore ) {
  //callback execution context
  var executionContext = this;

  //add "update" event listener to store
  profileStore.addListener("update",function(store, property) {
    //do something on store update

  },executionContext);
}
```

### Überprüfen der Definition und der Initialisierung eines Sitzungsspeichers {#checking-that-a-session-store-is-defined-and-initialized}

Sitzungsspeicher sind erst verfügbar, wenn sie geladen und mit Daten initialisiert wurden. Die folgenden Faktoren können den Zeitpunkt der Verfügbarkeit von Sitzungsspeichern beeinflussen:

* Laden der Seite
* Laden von JavaScript
* Ausführungszeit von JavaScript
* Antwortzeiten auf XHR-Anfragen
* Dynamische Änderungen am Sitzungsspeicher

Verwenden Sie die Methoden [onStoreRegistered](/help/sites-developing/ccjsapi.md#onstoreregistered-storename-callback) und [onStoreInitialized](/help/sites-developing/ccjsapi.md#onstoreinitialized-storename-callback-delay) für [CQ_Analytics.ClientContextUtils](/help/sites-developing/ccjsapi.md#cq-analytics-clientcontextutils)-Objekte, um auf Sitzungsspeicher nur dann zuzugreifen, wenn diese verfügbar sind. Mit diesen Methoden können Sie Ereignis-Listener registrieren, die auf die Sitzungsregistrierung und die Initialisierungsereignisse reagieren.

>[!CAUTION]
>
>Wenn Sie von einem anderen Store abhängig sind, müssen Sie den Fall berücksichtigen, dass der Store nie registriert wird.

Im folgenden Beispiel wird das Ereignis `onStoreRegistered` des Sitzungsspeichers `profile` verwendet. Wenn der Speicher registriert ist, wird dem Ereignis `update` des Sitzungsspeichers ein Listener hinzugefügt. Beim Aktualisieren des Speichers wird der Inhalt des Elements `<div class="welcome">` auf der Seite mit dem Namen des Speichers `profile` aktualisiert.

```
//listen for the store registration
CQ_Analytics.ClientContextUtils.onStoreRegistered("profile", listen);

//listen for the store's update event
function listen(){
 var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
    profilestore.addListener("update",insertName);
}

//insert the welcome message
function insertName(){
 $("div.welcome").text("Welcome "+getName());
}

//obtain the name from the profile store
function getName(){
 var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
 if(profilestore){
  return profilestore.getProperty("formattedName", false);
    } else {
        return null;
    }
}
```

### Ausschließen einer Eigenschaft aus dem sessionpersistence-Cookie {#excluding-a-property-from-the-sessionpersistence-cookie}

So verhindern Sie eine -Eigenschaft von `PersistedSessionStore` aus der Persistenz ausgeschlossen werden (d. h. schließen Sie sie aus der `sessionpersistence` -Cookie), fügen Sie die -Eigenschaft zur nicht persistenten Eigenschaftsliste des beibehaltenen Sitzungsspeichers hinzu.

Siehe ` [CQ_Analytics.PersistedSessionStore.setNonPersisted(propertyName)](/help/sites-developing/ccjsapi.md#setnonpersisted-name)`

```
CQ_Analytics.ClientContextUtils.onStoreRegistered("surferinfo", function(store) {
  //this will exclude the browser, OS and resolution properties of the surferinfo session store from the
  store.setNonPersisted("browser");
  store.setNonPersisted("OS");
  store.setNonPersisted("resolution");
});
```

## Konfigurieren des Gerätereglers {#configuring-the-device-slider}

### Bedingungen {#conditions}

Für die aktuelle Seite ist eine entsprechende Mobilversion erforderlich. Dafür muss für die Seite eine mit einer mobilen Rollout-Konfiguration eingerichtete Live Copy verfügbar sein (`rolloutconfig.path.toLowerCase` enthält `mobile`).

#### Konfiguration {#configuration}

Beim Wechseln von der Desktop-Seite zur mobilen Ansicht:

* Das DOM der mobilen Seite wird geladen.
* Das `div`-Hauptelement (erforderlich) mit dem Inhalt wird extrahiert und in die aktuelle Desktop-Seite eingefügt.

* Die CSS- und Textklassen, die geladen werden, müssen manuell konfiguriert werden.

Beispiel:

```
window.CQMobileSlider["geometrixx-outdoors"] = {
  //CSS used by desktop that need to be removed when mobile
  DESKTOP_CSS: [
    "/etc/designs/${app}/clientlibs_desktop_v1.css"
  ],

  //CSS used by mobile that need to be removed when desktop
  MOBILE_CSS: [
    "/etc/designs/${app}/clientlibs_mobile_v1.css"
  ],

  //id of the content that needs to be removed when mobile
  DESKTOP_MAIN_ID: "main",

  //id of the content that needs to be removed when desktop
  MOBILE_MAIN_ID: "main",

  //body classes used by desktop that need to be removed when mobile
  DESKTOP_BODY_CLASS: [
    "page"
  ],

  //body classes used by mobile that need to be removed when desktop
  MOBILE_BODY_CLASS: [
    "page-mobile"
  ]
};
```

## Beispiel: Erstellen einer benutzerdefinierten Kontextspeicherkomponente {#example-creating-a-custom-context-store-component}

In diesem Beispiel erstellen Sie eine Kontextspeicherkomponente, die Daten von einem externen Dienst abruft und im Sitzungsspeicher speichert:

* Erweitert die Komponente „genericstoreproperties“.
* Initialisiert einen Speicher mithilfe des JavaScript-Objekts „CQ_Analytics.JSONPStore“.
* Ruft über einen JSONP-Dienst Daten ab und speist diese in den Speicher ein.
* Rendert die Daten in Client Context.

### Hinzufügen der Geoloc-Komponente {#add-the-geoloc-component}

Erstellen Sie eine CQ-Anwendung und fügen Sie die Geoloc-Komponente hinzu.

1. Öffnen Sie CRXDE Lite in Ihrem Webbrowser ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Klicken Sie mit der rechten Maustaste auf den Ordner `/apps` und klicken Sie auf „Erstellen“ > „Ordner erstellen“. Geben Sie für `myapp` einen Namen ein und klicken Sie auf „OK“.
1. Erstellen Sie auch unter `myapp` einen Ordner mit dem Namen `contextstores`. ``
1. Klicken Sie mit der rechten Maustaste auf den Ordner `/apps/myapp/contextstores` und klicken Sie auf „Erstellen“ > „Komponente erstellen“. Geben Sie folgende Eigenschaftswerte an und klicken Sie auf „Weiter“:

   * Titel: Geoloc
   * Titel: Standortspeicher
   * Supertyp: cq/personalization/components/contextstores/genericstoreproperties
   * Gruppe: Client Context

1. Klicken Sie im Dialogfeld „Komponente erstellen“ auf jeder Seite auf „Weiter“, bis die Schaltfläche „OK“ aktiviert ist, und klicken Sie dann auf „OK“.
1. Klicken Sie auf „Alle speichern“.

### Erstellen des Dialogfelds „Geoloc-Bearbeitung“ {#create-the-geoloc-edit-dialog}

Für die Kontextspeicherkomponente ist ein Bearbeitungsdialogfeld erforderlich. Das Dialogfeld &quot;Geoloc-Bearbeitung&quot;enthält eine statische Meldung, die anzeigt, dass keine Eigenschaften zum Konfigurieren vorhanden sind.

1. Klicken Sie mit der rechten Maustaste auf den Knoten `/libs/cq/personalization/components/contextstores/genericstoreproperties/dialog` und klicken Sie auf „Kopieren“.
1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/myapp/contextstores/geoloc` und klicken Sie auf „Einfügen“.
1. Löschen Sie alle untergeordneten Knoten unter dem Knoten /apps/myapp/contextstores/geoloc/dialog/items/items/tab1/items :

   * store
   * properties
   * Miniaturansicht

1. Klicken Sie mit der rechten Maustaste auf den Knoten `/apps/myapp/contextstores/geoloc/dialog/items/items/tab1/items` und klicken Sie auf „Erstellen“ > „Knoten erstellen“. Geben Sie folgende Eigenschaftswerte an und klicken Sie auf „OK“:

   * Name: statisch
   * Typ: cq:Widget

1. Fügen Sie dem Knoten folgende Eigenschaften hinzu:

   | Name | Typ | Wert |
   |---|---|---|
   | cls | Zeichenfolge | x-form-fieldset-description |
   | text | Zeichenfolge | Die geoloc-Komponente erfordert keine Konfiguration. |
   | xtype | Zeichenfolge | static |

1. Klicken Sie auf „Alle speichern“.

   ![chlimage_1-5](assets/chlimage_1-5.png)

### Erstellen des Initialisierungsskripts {#create-the-initialization-script}

Fügen Sie der Geoloc-Komponente eine init.js.jsp-Datei hinzu und erstellen Sie damit den Sitzungsspeicher. Rufen Sie die Standortinformationen ab und speisen Sie diese in den Speicher ein.

Die Datei „init.js.jsp“ wird ausgeführt, wenn Client Context von der Seite geladen wird. Bis zu diesem Zeitpunkt wird die JavaScript-API von Client Context geladen und steht für Ihr Skript zur Verfügung.

1. Klicken Sie mit der rechten Maustaste auf den Knoten „/apps/myapp/contextstores/geoloc“ und klicken Sie auf „Erstellen“ > „Datei erstellen“. Geben Sie für init.js.jsp einen Namen ein und klicken Sie auf „OK“.
1. Fügen Sie oben auf der Seite folgenden Code ein und klicken Sie dann auf „Alle speichern“.

   ```java
   <%@page contentType="text/javascript;charset=utf-8" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   log.info("***** initializing geolocstore ****");
   String store = "locstore";
   String jsonpurl = "https://api.wipmania.com/jsonp?callback=${callback}";
   
   %>
   var locstore = CQ_Analytics.StoreRegistry.getStore("<%= store %>");
   if(!locstore){
    locstore = CQ_Analytics.JSONPStore.registerNewInstance("<%= store %>", "<%= jsonpurl %>",{});
   }
   <% log.info(" ***** done initializing geoloc ************"); %>
   ```

### Rendern der Geoloc-Sitzungsspeicherdaten {#render-the-geoloc-session-store-data}

Fügen Sie der JSP-Datei der Geoloc-Komponente den Code hinzu, um die Speicherdaten in Client Context zu rendern.

![chlimage_1-6](assets/chlimage_1-6.png)

1. Öffnen Sie in CRXDE Lite die Datei `/apps/myapp/contextstores/geoloc/geoloc.jsp`.
1. Fügen Sie folgenden HTML-Code unterhalb des Stub-Codes ein:

   ```xml
   <%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
   <div class="cq-cc-store">
      <div class="cq-cc-content">
          <div class="cq-cc-store-property cq-cc-store-property-level0">
              Continent: <personalization:storePropertyTag propertyName="address/continent" store="locstore"/>
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level1">
              Country: <personalization:storePropertyTag propertyName="address/country" store="locstore"/>
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level2">
              City: <personalization:storePropertyTag propertyName="address/city" store="locstore"/>
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level3">
              Latitude: <personalization:storePropertyTag propertyName="latitude" store="locstore"/>
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level4">
              Longitude: <personalization:storePropertyTag propertyName="longitude" store="locstore"/>
          </div>
      </div>
       <div class="cq-cc-clear"></div>
   </div>
   ```

1. Klicken Sie auf „Alle speichern“.

### Hinzufügen der Komponente zu Client Context {#add-the-component-to-client-context}

Fügen Sie die Standortspeicher-Komponente zu Client Context hinzu, damit sie beim Laden der Seite initialisiert wird.

1. Öffnen Sie die Geometrixx Outdoors-Homepage auf der Autoreninstanz ([https://localhost:4502/content/geometrixx-outdoors/en.html](https://localhost:4502/content/geometrixx-outdoors/en.html)).
1. Betätigen Sie Tastenkombination Strg+Alt+C (Windows) oder Ctrl+Wahl+C (Mac), um ClientContext zu öffnen.
1. Klicken Sie auf das Bearbeitungssymbol oben in Client Context, um Client Context-Designer zu öffnen.

   ![Bearbeitungssymbol, gekennzeichnet durch einen Bleistift in einem Quadrat.](do-not-localize/chlimage_1.png)

1. Ziehen Sie die Standortspeicher-Komponente in Client Context.

### Anzeigen der Standortinformationen in Client Context {#see-the-location-information-in-client-context}

Öffnen Sie die Geometrixx Outdoors-Homepage im Bearbeitungsmodus und dann Client Context, um die Daten aus der Standortspeicherkomponente anzuzeigen.

1. Öffnen Sie die englische Version der Geometrixx Outdoors-Site. ([https://localhost:4502/content/geometrixx-outdoors/en.html](https://localhost:4502/content/geometrixx-outdoors/en.html))
1. Drücken Sie zum Öffnen von ClientContext die Tastenkombination Strg+Alt+C (Windows) oder Ctrl+Wahl+C (Mac).

## Erstellen eines benutzerdefinierten Client Context {#creating-a-customized-client-context}

Um einen zweiten Client-Kontext zu erstellen, duplizieren Sie die Verzweigung:

`/etc/clientcontext/default`

* Der Unterordner:
  `/content`
enthält den Inhalt des angepassten Client-Kontexts.

* Der Ordner:
  `/contextstores`
ermöglicht die Definition verschiedener Konfigurationen für die Kontextspeicher.

Um Ihren benutzerdefinierten ClientContext zu verwenden, bearbeiten Sie die Eigenschaft
`path`
im Designstil der ClientContext-Komponente, wie in der Seitenvorlage enthalten. Beispielsweise als Standardspeicherort von:
`/libs/cq/personalization/components/clientcontext/design_dialog/items/path`
