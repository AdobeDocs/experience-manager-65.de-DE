---
title: AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten
description: Erfahren Sie, wie Sie Inhaltsfragmente in Adobe Experience Manager (AEM) mit der AEM GraphQL-API für die Headless-Bereitstellung von Inhalten verwenden.
feature: Content Fragments,GraphQL API
exl-id: beae1f1f-0a76-4186-9e58-9cab8de4236d
source-git-commit: 312e2477bb6a7cccab74cd4637d6a402f61052d7
workflow-type: tm+mt
source-wordcount: '4708'
ht-degree: 96%

---

# AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten {#graphql-api-for-use-with-content-fragments}

Erfahren Sie, wie Sie Inhaltsfragmente in Adobe Experience Manager (AEM) mit der AEM GraphQL-API für die Headless-Bereitstellung von Inhalten verwenden.

Die mit Inhaltsfragmenten verwendete GraphQL-API von AEM basiert weitgehend auf der standardmäßigen Open-Source-GraphQL-API.

Die Verwendung der GraphQL-API in AEM ermöglicht die effiziente Bereitstellung von Inhaltsfragmenten an JavaScript-Clients in Headless CMS-Implementierungen:

* Vermeiden von iterativen API-Anfragen wie bei REST,
* Sicherstellen, dass die Bereitstellung auf die spezifischen Anforderungen beschränkt ist,
* Ermöglichen der Massenbereitstellung von genau dem, was zum Rendern als Antwort auf eine einzelne API-Anfrage benötigt wird.

>[!NOTE]
>
>GraphQL wird in zwei (separaten) Szenarios in Adobe Experience Manager (AEM) verwendet:
>
>* [AEM Commerce nutzt Daten von einer Commerce-Plattform über GraphQL](/help/commerce/cif/integrating/magento.md).
>* AEM-Inhaltsfragmente stellen in Kombination mit der AEM-GraphQL-API (einer auf GraphQL basierenden benutzerdefinierten Implementierung) strukturierte Inhalte für die Verwendung in Ihren Programmen bereit.

## Voraussetzungen {#prerequisites}

Kunden und Kundinnen, die GraphQL verwenden, sollten das AEM-Inhaltsfragment mit GraphQL Index Package 1.0.5 installieren. Siehe [Versionshinweise](/help/release-notes/release-notes.md#install-aem-graphql-index-add-on-package) für weitere Informationen.

## Die GraphQL-API {#graphql-api}

GraphQL ist:

* „*...eine Abfragesprache für APIs und eine Laufzeitumgebung zur Erfüllung dieser Abfragen mit Ihren vorhandenen Daten. GraphQL bietet eine vollständige und verständliche Beschreibung der Daten in Ihrer API. Es gibt den Kundinnen und Kunden die Möglichkeit, genau das anzufordern, was sie brauchen, und nicht mehr, es erleichtert die Weiterentwicklung von APIs im Laufe der Zeit und ermöglicht leistungsstarke Entwickler-Tools.*“.

  Weitere Informationen finden Sie unter [GraphQL.org](https://graphql.org)

* „*...eine offene Spezifikation für eine flexible API-Schicht. Legen Sie GraphQL über Ihre bestehenden Back-Ends, um Produkte schneller als je zuvor zu erstellen...*“.

  Weitere Informationen finden Sie unter [GraphQL entdecken](https://graphql.com/).

* *„... eine Datenabfragesprache und -spezifikation, die 2012 intern von Facebook entwickelt wurde, bevor sie 2015 öffentlich als Open Source zur Verfügung gestellt wurde. Sie bietet eine Alternative zu REST-basierten Architekturen mit dem Ziel, die Produktivität von Entwicklern zu erhöhen und die Menge der übertragenen Daten zu minimieren. GraphQL wird von Hunderten von Unternehmen aller Größenordnungen in der Produktion eingesetzt ...“*

  Siehe [GraphQL Foundation](https://graphql.org/foundation).

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world all the tools they need to understand and adopt GraphQL.*". 
-->

Weitere Informationen zur GraphQL-API finden Sie in den folgenden Abschnitten (neben vielen anderen Ressourcen):

* Unter [graphql.org](https://graphql.org):

   * [Einführung in GraphQL](https://graphql.org/learn)

   * [GraphQL-Spezifikation](https://spec.graphql.org/)

* Unter [graphql.com](https://graphql.com):

   * [Tutorials](https://graphql.com/tutorials/)


Die Implementierung von GraphQL für AEM basiert auf der standardmäßigen GraphQL-Java™-Bibliothek. Siehe:

* [graphQL.org – Java](https://graphql.org/code/#java)

* [GraphQL-Java™ auf GitHub](https://github.com/graphql-java)

### GraphQL-Terminologie {#graphql-terminology}

GraphQL verwendet Folgendes:

* **[Abfragen](https://graphql.org/learn/queries/)**

* **[Schemata und Typen](https://graphql.org/learn/schema/)**:

   * Schemata werden von AEM basierend auf den Inhaltsfragmentmodellen generiert.
   * GraphQL stellt mithilfe Ihrer Schemata die Typen und Vorgänge dar, die für die GraphQL-Implementierung für AEM zulässig sind.

* **[Felder](https://graphql.org/learn/queries/#fields)**

* **[GraphQL-Endpunkt](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#graphql-aem-endpoint)**
   * Der Pfad in AEM, der auf GraphQL-Abfragen antwortet und Zugriff auf die GraphQL-Schemata bietet.

   * Weitere Informationen finden Sie unter [Aktivieren des GraphQL-Endpunkts](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#enabling-graphql-endpoint).

In der [(GraphQL.org) Einführung in GraphQL](https://graphql.org/learn/) finden Sie ausführliche Informationen, einschließlich der [Best Practices](https://graphql.org/learn/best-practices/).

### GraphQL-Abfragetypen {#graphql-query-types}

Mit GraphQL können Sie Abfragen für Folgendes durchführen:

* Einen **einzelnen Eintrag**

* Eine **[Liste von Einträgen](https://graphql.org/learn/schema/#lists-and-non-null)**

AEM bietet Funktionen zum Konvertieren von Abfragen (beide Typen) in [persistierte Abfragen](/help/sites-developing/headless/graphql-api/persisted-queries.md), die vom Dispatcher und CDN zwischengespeichert werden.

### Best Practices für GraphQL-Abfragen (Dispatcher und CDN) {#graphql-query-best-practices}

[Persistierte Abfragen](/help/sites-developing/headless/graphql-api/persisted-queries.md) sind die empfohlene Methode für Veröffentlichungsinstanzen, da:

* sie zwischengespeichert werden
* sie zentral von AEM verwaltet werden

<!-- is this fully accurate? -->
>[!NOTE]
>
>Normalerweise gibt es keinen Dispatcher/kein CDN auf der Authoring-Instanz, sodass die Verwendung persistierter Abfragen dort keinen Leistungsgewinn bringt, außer dass sie getestet werden können.

GraphQL-Abfragen über POST werden nicht empfohlen, da sie nicht zwischengespeichert werden. Daher ist der Dispatcher auf einer Standardinstanz so konfiguriert, dass er solche Abfragen blockiert.

GraphQL unterstützt zwar auch GET-Anfragen, aber diese Anfragen können Einschränkungen (z. B. die Länge der URL) erreichen, die durch persistente Abfragen vermieden werden können.

Weitere Informationen finden Sie unter [Aktivieren der Caching-Funktion für persistierte Abfragen](#enable-caching-persisted-queries).

>[!NOTE]
>
>Die Möglichkeit, direkte Abfragen durchzuführen, könnte irgendwann in der Zukunft entfernt werden.

## GraphiQL-Schnittstelle {#graphiql-interface}

Eine Implementierung der [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql)-Standardschnittstelle steht zur Verwendung mit AEM-GraphQL zur Verfügung.

>[!NOTE]
>
>GraphiQL ist in allen AEM-Umgebungen enthalten (ist aber nur zugänglich/sichtbar, wenn Sie Ihre Endpunkte konfigurieren).
>
>In früheren Versionen brauchten Sie ein Paket, um die GraphiQL-IDE zu installieren. Sollten Sie ein solches Paket installiert haben, kann es jetzt entfernt werden.

Über diese Schnittstelle können Sie Abfragen direkt eingeben und testen.

Beispiel:

* `http://localhost:4502/content/graphiql.html`

Dies bietet Funktionen wie Syntaxhervorhebung, automatische Vervollständigung, automatische Vorschläge sowie einen Verlauf und eine Online-Dokumentation:

![GraphiQL-Oberfläche](assets/cfm-graphiql-interface.png "GraphiQL-Oberfläche")

>[!NOTE]
>
>Siehe [Verwenden der GraphiQL-IDE](/help/sites-developing/headless/graphql-api/graphiql-ide.md).

## Anwendungsfälle für Autoren- und Veröffentlichungsumgebungen {#use-cases-author-publish-environments}

Die Anwendungsfälle können vom Typ der AEM-Umgebung abhängen:

* Veröffentlichungsumgebung; wird verwendet, um:
   * Daten für das JS-Programm (Standardanwendungsfall) abzufragen

* Autorenumgebung; wird verwendet, um:
   * Daten für „Content-Management-Zwecke“ abzufragen:
      * GraphQL in AEM ist eine schreibgeschützte API.
      * Die REST-API kann für CR(u)D-Vorgänge verwendet werden.

## Berechtigungen {#permission}

Die Berechtigungen sind für den Zugriff auf Assets erforderlich.

GraphQL-Abfragen werden mit der Berechtigung der AEM-Benutzenden der zugrunde liegenden Anfrage ausgeführt. Wenn die Benutzenden auf einige (als Assets gespeicherte) Fragmente keinen Lesezugriff haben, werden diese nicht Teil der Ergebnismenge.

Außerdem benötigen die Benutzenden Zugriff auf einen GraphQL-Endpunkt, um GraphQL-Abfragen ausführen zu können.

## Schema-Generierung {#schema-generation}

GraphQL ist eine typisierte API, was bedeutet, dass die Daten klar strukturiert und nach Typ geordnet sein müssen.

Die GraphQL-Spezifikation enthält eine Reihe von Richtlinien zum Erstellen einer robusten API zum Abfragen von Daten in einer bestimmten Instanz. Um diese Richtlinien zu vervollständigen, muss ein Client das [Schema](#schema-generation) abrufen, das alle für eine Abfrage erforderlichen Typen enthält.

Bei Inhaltsfragmenten basieren die GraphQL-Schemata (Struktur und Typen) auf **aktivierten** [Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) und deren Datentypen.

>[!CAUTION]
>
>Alle GraphQL-Schemata (abgeleitet von Inhaltsfragmentmodellen, die **aktiviert** wurden) können über den GraphQL-Endpunkt gelesen werden.
>
>Diese Fähigkeit bedeutet, dass Sie sicherstellen müssen, dass keine sensiblen Daten verfügbar sind, da sie auf diese Weise durchsickern könnten. Dazu gehören zum Beispiel Informationen, die in der Modelldefinition als Feldnamen vorhanden sein könnten.

Wenn Benutzende beispielsweise ein Inhaltsfragmentmodell mit dem Namen `Article` erstellen, generiert AEM den GraphQL-Typ `ArticleModel`. Die Felder dieses Typs entsprechen den im Modell definierten Feldern und Datentypen. Außerdem werden einige Einstiegspunkte für Abfragen erstellt, die für diesen Typ gelten, z. B. `articleByPath` oder `articleList`.

1. Ein Inhaltsfragmentmodell:

   ![Inhaltsfragmentmodell zur Verwendung mit GraphQL](assets/cfm-graphqlapi-01.png "Inhaltsfragmentmodell zur Verwendung mit GraphQL")

1. Das entsprechende GraphQL-Schema (Ausgabe aus der automatischen GraphiQL-Dokumentation):
   ![GraphQL-Schema basierend auf Inhaltsfragmentmodell](assets/cfm-graphqlapi-02.png "GraphQL-Schema basierend auf Inhaltsfragmentmodell")

   Dieses Bild zeigt, dass der generierte Typ `ArticleModel` mehrere [Felder](#fields) enthält.

   * Drei von ihnen wurden auf Benutzerseite kontrolliert: `author`, `main`, und `referencearticle`.

   * Die anderen Felder wurden von AEM automatisch hinzugefügt und stellen hilfreiche Methoden zur Bereitstellung von Informationen zu einem bestimmten Inhaltsfragment dar. In diesem Beispiel (die Variable [Helper-Felder](#helper-fields)) `_path`, `_metadata`, `_variations`.

1. Nachdem ein Benutzer ein Inhaltsfragment basierend auf dem Modell „Article“ erstellt hat, kann es über GraphQL abgefragt werden. Beispiele finden Sie in den [Beispielabfragen](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#graphql-sample-queries) (basierend auf einer [Beispielstruktur für Inhaltsfragmente zur Verwendung mit GraphQL](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#content-fragment-structure-graphql)).

In GraphQL für AEM ist das Schema flexibel. Diese Flexibilität bedeutet, dass es jedes Mal, wenn ein Inhaltsfragmentmodell erstellt, aktualisiert oder gelöscht wird, automatisch generiert wird. Die Datenschema-Caches werden auch aktualisiert, wenn Sie ein Inhaltsfragmentmodell aktualisieren.

Der Sites GraphQL-Service überwacht (im Hintergrund) alle Änderungen, die an einem Inhaltsfragmentmodell vorgenommen werden. Wenn Aktualisierungen erkannt werden, wird nur dieser Teil des Schemas neu generiert. Diese Optimierung spart Zeit und sorgt für Stabilität.

Wenn Sie zum Beispiel:

1. ein Paket installieren, das `Content-Fragment-Model-1` und `Content-Fragment-Model-2` enthält:

   1. GraphQL-Typen werden für `Model-1` und `Model-2` generiert.

1. Ändern Sie anschließend `Content-Fragment-Model-2`:

   1. Nur der GraphQL-Typ `Model-2` wird aktualisiert.

   1. `Model-1` hingegen bleibt unverändert.

>[!NOTE]
>
>Dieses Detail ist wichtig für den Fall, dass Sie Massenaktualisierungen von Inhaltsfragmentmodellen über die REST-API oder anderweitig vornehmen möchten.

Das Schema wird über denselben Endpunkt wie die GraphQL-Abfragen bereitgestellt, wobei der Client die Tatsache behandelt, dass das Schema mit der `GQLschema`-Erweiterung aufgerufen wird. Die Durchführung einer einfachen `GET`-Anfrage auf `/content/cq:graphql/global/endpoint.GQLschema` führt beispielsweise zur Ausgabe des Schemas mit dem Inhaltstyp: `text/x-graphql-schema;charset=iso-8859-1`.

### Schemagenerierung – Nicht veröffentlichte Modelle {#schema-generation-unpublished-models}

Wenn Inhaltsfragmente verschachtelt sind, kann es vorkommen, dass ein übergeordnetes Inhaltsfragmentmodell veröffentlicht wird, ein referenziertes Modell jedoch nicht.

>[!NOTE]
>
>Die AEM-Benutzeroberfläche verhindert dies zwar, aber wenn die Veröffentlichung programmgesteuert oder mit Inhaltspaketen erfolgt, kann es trotzdem passieren.

Wenn dies geschieht, generiert AEM ein *unvollständiges* Schema für das übergeordnete Inhaltsfragmentmodell. Das bedeutet, dass die Fragmentreferenz, die von dem unveröffentlichten Modell abhängt, aus dem Schema entfernt wird.

## Felder {#fields}

Innerhalb des Schemas gibt es einzelne Felder, die zwei grundlegenden Kategorien angehören:

* Von Ihnen generierte Felder.

  Eine Auswahl von [Datentypen](#data-types) wird verwendet, um Felder basierend auf der Konfiguration Ihres Inhaltsfragmentmodells zu erstellen. Die Feldnamen werden aus dem Feld **Eigenschaftsname** des **Datentyps** entnommen.

   * Auch die Einstellung **Rendern als** ist zu beachten, da Benutzende bestimmte Datentypen konfigurieren können. Beispielsweise kann ein einzeiliges Textfeld so konfiguriert werden, dass es mehrere einzeilige Texte enthält, indem `multifield` aus dem Dropdown-Menü ausgewählt wird.

* GraphQL für AEM generiert auch eine Reihe von [Hilfsfeldern](#helper-fields).

  Diese Felder werden verwendet, um ein Inhaltsfragment zu identifizieren oder um weitere Informationen zu einem Inhaltsfragment abzurufen.

### Datentypen {#data-types}

GraphQL für AEM unterstützt eine Liste von Typen. Alle unterstützten Datentypen für Inhaltsfragmentmodelle und die entsprechenden GraphQL-Typen werden dargestellt:

| Datentyp für Inhaltsfragmentmodelle | GraphQL-Typ | Beschreibung |
|--- |--- |--- |
| Einzeiliger Text | `String`, `[String]` |  Wird für einfache Zeichenfolgen wie Autorennamen, Ortsnamen usw. verwendet. |
| Mehrzeiliger Text | `String` |  Wird für die Ausgabe von Text verwendet, z. B. für den Textkörper eines Artikels |
| Zahl |  `Float`, `[Float]` | Wird für die Anzeige von Gleitkommazahlen und regulären Zahlen verwendet |
| Boolesch |  `Boolean` |  Wird für die Anzeige von Kontrollkästchen → einfachen Wahr/Falsch-Aussagen verwendet |
| Datum und Uhrzeit | `Calendar` |  Wird verwendet, um Datum und Uhrzeit in einem ISO 8086-Format anzuzeigen. Je nach ausgewähltem Typ gibt es drei Varianten, die in AEM-GraphQL verwendet werden können: `onlyDate`, `onlyTime`, `dateTime` |
| Aufzählung |  `String` |  Wird verwendet, um eine Option aus einer Liste von Optionen anzuzeigen, die bei der Modellerstellung definiert wurde |
|  Tags |  `[String]` |  Wird verwendet, um eine Liste von Zeichenfolgen anzuzeigen, die in AEM verwendete Tags darstellen |
| Inhaltsreferenz |  `String` |  Wird verwendet, um den Pfad zu einem anderen Asset in AEM anzuzeigen |
| Fragmentreferenz |  *Ein Modelltyp* <br><br>Einzelnes Feld: `Model` - Modelltyp, direkt referenziert <br><br>Multifield mit einem referenzierten Typ: `[Model]` - Array des Typs `Model`, die direkt aus dem Array referenziert wird <br><br>Multifield mit mehreren referenzierten Typen: `[AllFragmentModels]` - Array aller Modelltypen, referenziert aus Array mit Vereinigungstyp |  Wird verwendet, um auf ein oder mehrere Inhaltsfragmente bestimmter Modelltypen zu verweisen, die beim Erstellen des Modells definiert wurden |

{style="table-layout:auto"}

### Hilfsfelder {#helper-fields}

Zusätzlich zu den Datentypen für benutzergenerierte Felder generiert GraphQL für AEM auch mehrere *Hilfsfelder*, um ein Inhaltsfragment zu identifizieren oder zusätzliche Informationen über ein Inhaltsfragment bereitzustellen.

Diese [Hilfsfelder](#helper-fields) sind durch ein vorangestelltes `_` gekennzeichnet, um zu unterscheiden, was vom Benutzer bzw. von der Benutzerin definiert und was automatisch generiert wurde.

#### Pfad  {#path}

Das Pfadfeld wird in AEM GraphQL als Kennung verwendet. Es stellt den Pfad des Inhaltsfragment-Assets im AEM Repository dar. Dieser Pfad wird als Kennung eines Inhaltsfragments gewählt, da er:

* innerhalb von AEM eindeutig ist,
* leicht abgerufen werden kann.

Der folgende Code zeigt die Pfade aller Inhaltsfragmente an, die auf der Grundlage des Inhaltsfragmentmodells `Person` erstellt wurden.

```graphql
{
  personList {
    items {
      _path
    }
  }
}
```

Um ein einzelnes Inhaltsfragment eines bestimmten Typs abzurufen, müssen Sie zunächst auch dessen Pfad bestimmen. Beispiel:

```graphql
{
  authorByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      firstName
      name
    }
  }
}
```

Siehe [Beispielabfrage – ein Einzelstadtfragment](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-single-specific-city-fragment).

#### Metadaten {#metadata}

Mit GraphQL stellt AEM auch die Metadaten eines Inhaltsfragments zur Verfügung. Metadaten sind Informationen, die ein Inhaltsfragment beschreiben, z. B.:

* der Titel eines Inhaltsfragments
* den Miniaturansichtspfad
* die Beschreibung eines Inhaltsfragments
* und das Erstellungsdatum, unter anderem.

Da Metadaten über den Schema-Editor generiert werden und daher keine bestimmte Struktur haben, wurde der GraphQL-Typ `TypedMetaData` implementiert, um die Metadaten eines Inhaltsfragments anzuzeigen. Die `TypedMetaData` gibt die nach den folgenden Skalartypen gruppierten Informationen preis:

| Feld |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!`  |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

Jeder Skalartyp repräsentiert entweder ein einzelnes Name-Wert-Paar oder ein Array von Name-Wert-Paaren, wobei der Wert dieses Paares dem Typ entspricht, in dem er gruppiert wurde.

Wenn Sie zum Beispiel den Titel eines Inhaltsfragments abrufen möchten, ist diese Eigenschaft eine Zeichenfolgeneigenschaft, sodass Sie alle Zeichenfolgen-Metadaten abfragen würden:

Abfragen von Metadaten:

```graphql
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      _metadata {
        stringMetadata {
          name
          value
        }
      }
    }
  }
}
```

Sie können alle GraphQL-Typen für Metadaten anzeigen, wenn Sie das generierte GraphQL-Schema anzeigen. Alle Modelltypen haben dieselben `TypedMetaData`.

>[!NOTE]
>
>**Unterschied zwischen normalen und Array-Metadaten**
>Beachten Sie, dass sich `StringMetadata` und `StringArrayMetadata` beide auf das beziehen, was im Repository gespeichert ist, und nicht darauf, wie Sie sie abrufen.
>
>Wenn Sie beispielsweise das Feld `stringMetadata` aufrufen, erhalten Sie ein Array mit allen im Repository gespeicherten Metadaten als `String`. Und wenn Sie `stringArrayMetadata` aufrufen, erhalten Sie ein Array aller im Repository gespeicherten Metadaten als `String[]`.

Weitere Informationen finden Sie unter [Beispielabfrage für Metadaten – Liste der Metadaten für Auszeichnungen mit dem Titel „GB“](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-metadata-awards-gb).

#### Varianten {#variations}

Das Feld `_variations` wurde implementiert, um die Abfrage der Varianten eines Inhaltsfragments zu vereinfachen. Beispiel:

```graphql
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _variations
    }
  }
}
```

>[!NOTE]
>
>Das Feld `_variations` enthält keine `master`-Varianten, weil die Originaldaten (in der Benutzeroberfläche als *Master* referenziert) technisch gesehen nicht als explizite Varianten betrachtet werden.

Weitere Informationen finden Sie unter [Beispielabfrage – Alle Städte mit einer gegebenen Variante](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-cities-named-variation).

>[!NOTE]
>
>Wenn die angegebene Variante für ein Inhaltsfragment nicht vorhanden ist, werden die Originaldaten (auch bekannt als primäre Variante) als Standard (Ersatz) zurückgegeben.

<!--
## Security Considerations {#security-considerations}
-->

## GraphQL-Variablen {#graphql-variables}

Mit GraphQL können Variablen in die Abfrage eingefügt werden. Weitere Informationen finden Sie in der [GraphQL-Dokumentation für Variablen](https://graphql.org/learn/queries/#variables).

Um beispielsweise alle Inhaltsfragmente vom Typ `Article` abzurufen, die eine bestimmte Variante aufweisen, können Sie die Variable `variation` in GraphiQL angeben.

![GraphQL-Variablen](assets/cfm-graphqlapi-03.png "GraphQL-Variablen")

```graphql
### query
query GetArticlesByVariation($variation: String!) {
    articleList(variation: $variation) {
        items {
            _path
            author
            _variations
        }
    }
}
 
### in query variables
{
    "variation": "uk"
}
```

## GraphQL-Anweisungen {#graphql-directives}

In GraphQL besteht die Möglichkeit, die Abfrage basierend auf Variablen zu ändern, die als GraphQL-Anweisungen bezeichnet werden.

Sie können beispielsweise das Feld `adventurePrice` basierend auf einer Variablen `includePrice` in eine Abfrage für alle `AdventureModels` einfügen.

![GraphQL-Anweisungen](assets/cfm-graphqlapi-04.png "GraphQL-Anweisungen")

```graphql
### query
query GetAdventureByType($includePrice: Boolean!) {
  adventureList {
    items {
      adventureTitle
      adventurePrice @include(if: $includePrice)
    }
  }
}
 
### in query variables
{
    "includePrice": true
}
```

## Filtern {#filtering}

Sie können auch Filterung in Ihren GraphQL-Abfragen verwenden, um bestimmte Daten zurückzugeben.

Beim Filtern wird eine Syntax verwendet, die auf logischen Operatoren und Ausdrücken basiert.

Der kleinste Teil ist ein einzelner Ausdruck, der auf den Inhalt eines bestimmten Felds angewendet werden kann. Er vergleicht den Inhalt des Felds mit einem gegebenen konstanten Wert.

Der folgende Ausdruck würde zum Beispiel den Inhalt des Feldes mit dem Wert `some text` vergleichen und wäre erfolgreich, wenn der Inhalt dem Wert entspricht. Andernfalls schlägt der Ausdruck fehl:

```graphql
{
  value: "some text"
  _op: EQUALS
}
```

Die folgenden Operatoren können verwendet werden, um Felder mit einem bestimmten Wert zu vergleichen:

| Operator | Typen | Der Ausdruck ist erfolgreich, wenn ... |
|--- |--- |--- |
| `EQUALS` | `String`, `ID`, `Boolean` | ... der Wert ist derselbe wie der Inhalt des Feldes |
| `EQUALS_NOT` | `String`, `ID` | ... der Wert *nicht* identisch mit dem Inhalt des Felds ist |
| `CONTAINS` | `String` | … der Inhalt des Feldes den Wert enthält (`{ value: "mas", _op: CONTAINS }` entspricht `Christmas`, `Xmas`, `master`, …) |
| `CONTAINS_NOT` | `String` | … der Inhalt des Felds *nicht* den Wert enthält |
| `STARTS_WITH` | `ID` | … die ID mit einem bestimmten Wert beginnt (`{ value: "/content/dam/", _op: STARTS_WITH` entspricht `/content/dam/path/to/fragment`, aber nicht `/namespace/content/dam/something`) |
| `EQUAL` | `Int`, `Float` | ... der Wert ist derselbe wie der Inhalt des Feldes |
| `UNEQUAL` | `Int`, `Float` | ... der Wert *nicht* identisch mit dem Inhalt des Felds ist |
| `GREATER` | `Int`, `Float` | ... der Inhalt des Felds größer als der Wert ist |
| `GREATER_EQUAL` | `Int`, `Float` | ... der Inhalt des Felds größer oder gleich dem Wert ist |
| `LOWER` | `Int`, `Float` | ... der Inhalt des Felds kleiner als der Wert ist |
| `LOWER_EQUAL` | `Int`, `Float` | ... der Inhalt des Felds kleiner oder gleich dem Wert ist |
| `AT` | `Calendar`, `Date`, `Time` | ... der Inhalt des Feldes ist derselbe wie der Wert (einschließlich der Zeitzoneneinstellung) |
| `NOT_AT` | `Calendar`, `Date`, `Time` | ... der Inhalt des Felds *nicht* identisch mit dem Wert ist |
| `BEFORE` | `Calendar`, `Date`, `Time` | ... der durch den Wert angegebene Zeitpunkt vor dem durch den Feldinhalt angegebenen Zeitpunkt liegt |
| `AT_OR_BEFORE` | `Calendar`, `Date`, `Time` | ... der durch den Wert angegebene Zeitpunkt vor oder am selben durch den Feldinhalt angegebenen Zeitpunkt liegt |
| `AFTER` | `Calendar`, `Date`, `Time` | ... der durch den Wert angegebene Zeitpunkt nach dem durch den Feldinhalt angegebenen Zeitpunkt liegt |
| `AT_OR_AFTER` | `Calendar`, `Date`, `Time` | ... der durch den Wert angegebene Zeitpunkt nach oder am selben durch den Feldinhalt angegebenen Zeitpunkt liegt |

Bei einigen Typen können Sie auch zusätzliche Optionen angeben, mithilfe derer die Auswertung eines Ausdrucks geändert werden kann:

| Option | Typen | Beschreibung |
|--- |--- |--- |
| `_ignoreCase` | `String` | Ignoriert die Groß- und Kleinschreibung einer Zeichenkette, ein Wert von `time` entspricht z. B. `TIME`, `time`, `tImE`, ... |
| `_sensitiveness` | `Float` | Ermöglicht eine bestimmte Spanne für `float`-Werte, die als identisch betrachtet werden (um technische Einschränkungen aufgrund der internen Darstellung von `float`-Werten zu umgehen; sollte vermieden werden, da diese Option negative Auswirkungen auf die Leistung haben kann |

Ausdrücke können mithilfe eines logischen Operators (`_logOp`) zu einer Gruppe kombiniert werden:

* `OR` – die Ausdrucksgruppe ist erfolgreich, wenn mindestens ein Ausdruck erfolgreich ist
* `AND` – die Ausdrucksgruppe ist erfolgreich, wenn alle Ausdrücke erfolgreich sind (Standard)

Jedes Feld kann anhand einer eigenen Ausdrucksgruppe gefiltert werden. Die Ausdrucksgruppen aller im Filterargument erwähnten Felder werden schließlich durch einen eigenen logischen Operator kombiniert.

Eine Filterdefinition (als das `filter`-Argument an eine Abfrage übergeben) enthält:

* Eine Unterdefinition für jedes Feld (auf das Feld kann über seinen Namen zugegriffen werden, z. B. gibt es ein `lastName`-Feld im Filter für das `lastName`-Feld im Daten(feld)typ)
* Jede Unterdefinition enthält das `_expressions`-Array, das die Ausdrucksgruppe bereitstellt, und das `_logOp`-Feld, das den logischen Operator definiert, mit dem die Ausdrücke kombiniert werden sollten
* Jeder Ausdruck wird durch den Wert (`value`-Feld) und den Operator (`_operator`-Feld) definiert, mit dem der Inhalt eines Felds verglichen werden soll

Sie können `_logOp` weglassen, wenn Sie Elemente mit `AND` kombinieren wollen, und `_operator`, wenn Sie auf Gleichheit prüfen wollen, da diese Werte Standardwerte sind.

Das folgende Beispiel zeigt eine vollständige Abfrage, die alle Personen filtert, die über eine `lastName` von `Provo` verfügen oder `sjö` enthalten, ohne die Groß-/Kleinschreibung zu beachten:

```graphql
{
  authorList(filter: {
    lastname: {
      _logOp: OR
      _expressions: [
        {
          value: "sjö",
          _operator: CONTAINS,
          _ignoreCase: true
        },
        {
          value: "Provo"
        }
      ]
    }
  }) {
    items {
      lastName
      firstName
    }
  }
}
```

Sie können zwar auch nach verschachtelten Feldern filtern, dies wird jedoch nicht empfohlen, da es zu Leistungsproblemen führen kann.

Weitere Beispiele finden Sie unter:

* Details zu den [Erweiterungen von GraphQL für AEM](#graphql-extensions)

* [Beispielabfragen unter Verwendung dieses Beispielinhalts und dieser Beispielstruktur](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

   * Und [Beispielinhalt und -struktur](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#content-fragment-structure-graphql) speziell für die Verwendung in Beispielabfragen

* [Beispielabfragen basierend auf dem WKND-Projekt](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## Sortieren {#sorting}

>[!NOTE]
>
>Für optimale Leistung sollten Sie [Ihre Inhaltsfragmente für Paging und Sortierung in der GraphQL-Filterung](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md) aktualisieren.

Mit dieser Funktion können Sie die Abfrageergebnisse entsprechend einem bestimmten Feld sortieren.

Die Sortierkriterien:

* ist eine durch Kommas getrennte Liste von Werten, die den Feldpfad darstellen
   * das erste Feld in der Liste definiert die primäre Sortierreihenfolge
      * das zweite Feld wird verwendet, wenn zwei Werte des primären Sortierkriteriums gleich sind
      * das dritte Feld wird verwendet, wenn die ersten beiden Kriterien gleich sind, usw.
   * gepunktete Notation, also `field1.subfield.subfield`usw.
* mit optionaler Sortierrichtung
   * ASC (aufsteigend) oder DESC (absteigend); standardmäßig wird ASC angewendet
   * die Richtung kann pro Feld angegeben werden. Diese Fähigkeit bedeutet, dass Sie ein Feld in aufsteigender Reihenfolge sortieren können, ein anderes in absteigender Reihenfolge (name, firstName DESC)

Beispiel:

```graphql
query {
  authorList(sort: "lastName, firstName") {
    items {
      firstName
      lastName
    }
  }
}
```

Ein weiteres Beispiel:

```graphql
{
  authorList(sort: "lastName DESC, firstName DESC") {
    items {
        lastName
        firstName
    }
  }
}
```

Sie können auch ein Feld innerhalb eines verschachtelten Fragments mithilfe des Formats `nestedFragmentname.fieldname` sortieren.

>[!NOTE]
>
>Dieses Format kann sich negativ auf die Leistung auswirken.

Beispiel:

```graphql
query {
  articleList(sort: "authorFragment.lastName")  {
    items {
      title
      authorFragment {
        firstName
        lastName
        birthDay
      }
      slug
    }
  }
}
```

## Paging {#paging}

>[!NOTE]
>
>Für optimale Leistung sollten Sie [Ihre Inhaltsfragmente für Paging und Sortierung in der GraphQL-Filterung](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md) aktualisieren.

Mit dieser Funktion können Sie Paging für Abfragetypen durchführen, was eine Liste zurückgibt. Es werden zwei Methoden bereitgestellt:

* `offset` und `limit` in einer `List`-Abfrage
* `first` und `after` in einer `Paginated`-Abfrage

### Listenabfrage – Versatz und Limit {#list-offset-limit}

In einer `...List`-Abfrage können Sie `offset` und `limit` verwenden, um eine bestimmte Teilmenge der Ergebnisse zurückzugeben:

* `offset`: Gibt den ersten zurückzugebenden Datensatz an
* `limit`: Gibt die maximale Anzahl an zurückzugebenden Datensätzen an

Beispiel für die Ausgabe der Ergebnisseite, die bis zu fünf Artikel enthält, beginnend mit dem fünften Artikel aus der *vollständigen* Ergebnisliste:

```graphql
query {
   articleList(offset: 5, limit: 5) {
    items {
      authorFragment {
        lastName
        firstName
      }
    }
  }
}
```

<!-- When available link to BP and replace "JCR query level" with a more neutral term. -->

<!-- When available link to BP and replace "JCR query result set" with a more neutral term. -->

>[!NOTE]
>
>* Für das Paging ist eine stabile Sortierreihenfolge erforderlich, damit es bei mehreren Abfragen, die verschiedene Seiten desselben Ergebnisses anfordern, korrekt funktioniert. Standardmäßig wird der Repository-Pfad jedes Elements des Ergebnissatzes verwendet, um sicherzustellen, dass die Reihenfolge immer gleich ist. Wenn eine andere Sortierreihenfolge verwendet wird und diese Sortierung nicht auf JCR-Abfrageebene durchgeführt werden kann, hat dies negative Auswirkungen auf die Leistung. Der Grund dafür ist, dass der gesamte Ergebnissatz in den Speicher geladen werden muss, bevor die Seiten bestimmt werden.
>
>* Je höher der Versatz, desto länger dauert es, die Elemente aus der vollständigen JCR-Abfrageergebnismenge zu überspringen. Eine alternative Lösung für große Ergebnissätze ist die Verwendung der paginierten Abfrage mit der `first`- und `after`-Methode.

### Paginiete Abfrage – „first“ und „after“ {#paginated-first-after}

Der Abfragetyp `...Paginated` verwendet die meisten `...List`-Abfragetypfunktionen (Filtern, Sortieren), verwendet jedoch anstelle von `offset`/`limit`-Argumenten die `first`/`after`-Argumente gemäß der Definition in der [GraphQL-Cursor-Verbindungsspezifikation](https://relay.dev/graphql/connections.htm). Eine weniger formale Einführung finden Sie in der [Einführung in GraphQL](https://graphql.org/learn/pagination/#pagination-and-edges).

* `first`: Die `n` ersten zurückzugebenden Elemente.
Der Standardwert lautet `50`.
Der Maximalwert ist `100`.
* `after`: Der Cursor, der den Anfang der angeforderten Seite bestimmt. Das durch den Cursor dargestellte Element ist nicht in der Ergebnismenge enthalten. Der Cursor einer Position wird durch das Feld `cursor` der Struktur `edges` bestimmt.

Ein Beispiel für die Ausgabe einer Ergebnisseite mit bis zu fünf Abenteuern, beginnend mit dem angegebenen Cursor-Element in der *vollständigen* Ergebnisliste:

```graphql
query {
    adventurePaginated(first: 5, after: "ODg1MmMyMmEtZTAzMy00MTNjLThiMzMtZGQyMzY5ZTNjN2M1") {
        edges {
          cursor
          node {
            title
          }
        }
        pageInfo {
          endCursor
          hasNextPage
        }
    }
}
```

<!-- When available link to BP -->
<!-- Due to internal technical constraints, performance will degrade if sorting and filtering is applied on nested fields. Therefore it is recommended to use filter/sort fields stored at root level. For more information, see the [Best Practices document](link). -->

>[!NOTE]
>
>* Standardmäßig verwendet Paging die UUID des Repository-Knotens, der das Sortierungsfragment darstellt, um sicherzustellen, dass die Reihenfolge der Ergebnisse immer gleich ist. Wenn `sort` verwendet wird, wird die UUID implizit genutzt, um eine eindeutige Sortierung sicherzustellen, auch für zwei Elemente mit identischen Sortierschlüsseln.
>
>* Aufgrund interner technischer Einschränkungen wird die Leistung beeinträchtigt, wenn die Sortierung und Filterung auf verschachtelte Felder angewendet wird. Verwenden Sie daher Filter-/Sortierfelder, die auf der Stammebene gespeichert sind. Diese Technik ist auch die empfohlene Methode, um große paginierte Ergebnismengen abzufragen.

## Persistierte GraphQL-Abfragen – Aktivieren der Caching-Funktion im Dispatcher {#graphql-persisted-queries-enabling-caching-dispatcher}

>[!CAUTION]
>
>Wenn die Caching-Funktion im Dispatcher aktiviert ist, wird der [CORS-Filter](#cors-filter) nicht benötigt, sodass dieser Abschnitt ignoriert werden kann.

Das Caching persistierter Abfragen ist im Dispatcher standardmäßig nicht aktiviert. Eine Standardaktivierung ist nicht möglich, da Kundinnen und Kunden, die CORS (Cross-Origin Resource Sharing) mit mehreren Ursprüngen verwenden, ihre Dispatcher-Konfiguration überprüfen und möglicherweise aktualisieren müssen.

>[!NOTE]
>
>Der Dispatcher speichert den `Vary`-Header nicht zwischen.
>
>Das Caching anderer CORS-bezogener Header kann im Dispatcher aktiviert werden, reicht jedoch möglicherweise nicht aus, wenn mehrere CORS-Quellen vorhanden sind.

### Aktivieren der Caching-Funktion für persistierte Abfragen {#enable-caching-persisted-queries}

Um das Zwischenspeichern persistenter Abfragen zu aktivieren, sind folgende Aktualisierungen an den Dispatcher-Konfigurationsdateien erforderlich:

* `<conf.d/rewrites/base_rewrite.rules>`

  ```xml
  # Allow the dispatcher to be able to cache persisted queries - they need an extension for the cache file
  RewriteCond %{REQUEST_URI} ^/graphql/execute.json
  RewriteRule ^/(.*)$ /$1;.json [PT] 
  ```

  >[!NOTE]
  >
  >Der Dispatcher fügt das Suffix hinzu `.json` an alle gespeicherten Abfrage-URLs, damit das Ergebnis zwischengespeichert werden kann.
  >
  >Dadurch wird sichergestellt, dass die Abfrage den Anforderungen des Dispatchers für Dokumente entspricht, die zwischengespeichert werden können. Weitere Informationen finden Sie unter [Wie werden die Dispatcher-Rückgabedokumente zurückgegeben?](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/troubleshooting/dispatcher-faq.html?lang=de#how-does-the-dispatcher-return-documents%3F)

* `<conf.dispatcher.d/filters/ams_publish_filters.any>`

  ```xml
  # Allow GraphQL Persisted Queries & preflight requests
  /0110 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
  ```

### CORS-Konfiguration im Dispatcher {#cors-configuration-in-dispatcher}

Kundinnen und Kunden, die CORS-Anfragen verwenden, müssen möglicherweise ihre CORS-Konfiguration im Dispatcher überprüfen und aktualisieren.

* Die `Origin`-Kopfzeile darf nicht über den Dispatcher an AEM Publish weitergeben werden:
   * Überprüfen Sie die `clientheaders.any`-Datei.
* Stattdessen müssen CORS-Anfragen auf Dispatcher-Ebene im Hinblick auf zulässige Ursprünge ausgewertet werden. Dieser Ansatz stellt außerdem sicher, dass CORS-bezogene Kopfzeilen in allen Fällen korrekt an einem Ort festgelegt werden.
   * Eine solche Konfiguration sollte der `vhost`-Datei hinzugefügt werden. Nachfolgend finden Sie eine Beispielkonfiguration. Zur Vereinfachung ist nur der CORS-bezogene Teil angegeben. Sie können sie an Ihre spezifischen Anwendungsfälle anpassen.

  ```xml
  <VirtualHost *:80>
     ServerName "publish"
  
     # ...
  
     <IfModule mod_headers.c>
         Header add X-Vhost "publish"
  
          ################## Start of the CORS specific configuration ##################
  
          SetEnvIfExpr "req_novary('Origin') == ''"  CORSType=none CORSProcessing=false
          SetEnvIfExpr "req_novary('Origin') != ''"  CORSType=cors CORSProcessing=true CORSTrusted=false
  
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') == '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=invalidpreflight CORSProcessing=false
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') != '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=preflight CORSProcessing=true CORSTrusted=false
          SetEnvIfExpr "req_novary('Origin') -strcmatch 'https://%{HTTP_HOST}*'"  CORSType=samedomain CORSProcessing=false
  
          # For requests that require CORS processing, check if the Origin can be trusted
          SetEnvIfExpr "%{HTTP_HOST} =~ /(.*)/ " ParsedHost=$1
  
          ################## Adapt the regex to match CORS origin for your environment
          SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*.your-domain.tld(:\d+)?$)#" CORSTrusted=true
  
          # Extract the Origin header 
          SetEnvIfNoCase ^Origin$ ^https://(.*)$ CORSTrustedOrigin=https://$1
  
          # Flush If already set
          Header unset Access-Control-Allow-Origin
          Header unset Access-Control-Allow-Credentials
  
          # Trusted
          Header always set Access-Control-Allow-Credentials "true" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Origin "%{CORSTrustedOrigin}e" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Methods "GET" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Max-Age 1800 "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Headers "Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers" "expr=reqenv('CORSTrusted') == 'true'"
  
          # Non-CORS or Not Trusted
          Header unset Access-Control-Allow-Credentials "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Origin "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Methods "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Max-Age "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
  
          # Always vary on origin, even if its not there.
          Header merge Vary Origin
  
          # CORS - send 204 for CORS requests which are not trusted
          RewriteCond expr "reqenv('CORSProcessing') == 'true' && reqenv('CORSTrusted') == 'false'"
          RewriteRule "^(.*)" - [R=204,L]
  
          ################## End of the CORS specific configuration ##################
  
     </IfModule>
  
     <Directory />
  
         # ...
  
     </Directory>
  
     # ...
  
  </VirtualHost>
  ```

## GraphQL für AEM – Zusammenfassung der Erweiterungen {#graphql-extensions}

Die grundlegende Funktionsweise von Abfragen mit GraphQL für AEM entspricht der Standard-GraphQL-Spezifikation. Für GraphQL-Abfragen mit AEM gibt es einige Erweiterungen:

* Wenn Sie ein einzelnes Ergebnis benötigen:
   * Verwenden Sie den Modellnamen; z. B. Stadt

* Wenn Sie eine Ergebnisliste erwarten:
   * Fügen Sie `List` zum Modellnamen hinzu, z. B. `cityList`
   * Siehe [Beispielabfrage – Alle Informationen zu allen Städten](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-information-all-cities)

  Sie haben dann folgende Möglichkeiten:

   * [Ergebnisse sortieren](#sorting)

      * `ASC`: Aufsteigend
      * `DESC`: Absteigend

   * Ergebnisseite zurückgeben mit einer der folgenden Möglichkeiten:

      * [einer Listenabfrage mit Versatz und Limit](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#list-offset-limit)
      * [einer paginierten Abfrage mit „zuerst“ und „danach“](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#paginated-first-after)
   * Siehe [Beispielabfrage – Alle Informationen zu allen Städten](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-information-all-cities)

* Der Filter `includeVariations` ist im `List`-Abfragetyp enthalten. Um Inhaltsfragmentvarianten in den Abfrageergebnissen abzurufen, muss der Filter `includeVariations` auf `true` gesetzt werden.

  >[!CAUTION]
  >Der Filter `includeVariations` kann nicht zusammen mit dem systemgenerierten Feld `_variation` verwendet werden.

* Wenn Sie ein logisches ODER verwenden möchten:
   * Verwenden Sie ` _logOp: OR`
   * [Beispielabfrage – Alle Personen mit dem Namen „Jobs“ oder „Smith“](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-persons-jobs-smith)

* Es gibt ebenfalls ein logisches UND, es ist aber (oft) implizit.

* Sie können Feldnamen abfragen, die den Feldern im Inhaltsfragmentmodell entsprechen.
   * [Beispielabfrage – Vollständige Details über den CEO und die Mitarbeiter eines Unternehmens](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-full-details-company-ceos-employees)

* Zusätzlich zu den Feldern aus Ihrem Modell gibt es einige vom System generierte Felder (denen ein Unterstrich vorangestellt ist):

   * Für Inhalte:

      * `_locale`: Anzeigen der Sprache; basierend auf Language Manager
         * Siehe [Beispielabfrage für mehrere Inhaltsfragmente eines bestimmten Gebietsschemas](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-multiple-fragments-given-locale)

      * `_metadata`: Anzeigen von Metadaten für Ihr Fragment
         * Siehe [Beispielabfrage für Metadaten – Liste der Metadaten für Auszeichnungen mit dem Titel „GB“](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-metadata-awards-gb)

      * `_model`: Zulassen von Abfragen nach einem Inhaltsfragmentmodell (Pfad und Titel)
         * Siehe [Beispielabfrage für ein Inhaltsfragmentmodell anhand eines Modells](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-content-fragment-model-from-model)

      * `_path`: Der Pfad zu Ihrem Inhaltsfragment im Repository
         * Siehe [Beispielabfrage – ein Einzelstadtfragment](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)

      * `_reference`: Anzeigen von Verweisen; einschließlich Inline-Verweisen im Rich-Text-Editor
         * Siehe [Beispielabfrage für mehrere Inhaltsfragmente mit vorab abgerufenen Verweisen](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-multiple-fragments-prefetched-references)

      * `_variation`: Anzeige bestimmter Varianten in Ihrem Inhaltsfragment

        >[!NOTE]
        >
        >Wenn die angegebene Variante für ein Inhaltsfragment nicht vorhanden, wird standardmäßig die primäre Variante (als Ersatz) zurückgegeben.

        >[!CAUTION]
        >Das systemgenerierte Feld `_variation` kann nicht zusammen mit dem Filter `includeVariations` verwendet werden.

         * Weitere Informationen finden Sie unter [Beispielabfrage – Alle Städte mit einer gegebenen Variante](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-cities-named-variation)

      * `_tags`: um die IDs von Inhaltsfragmenten oder Varianten anzuzeigen, die Tags enthalten; diese Liste ist ein Array von `cq:tags`-Kennungen.

         * Siehe [Beispielabfrage – Namen aller Städte, die als Städtereisen markiert sind](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-names-all-cities-tagged-city-breaks)
         * Siehe [Beispielabfrage für Inhaltsfragmentvarianten eines bestimmten Modells, an die ein bestimmtes Tag angehängt ist](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-fragment-variations-given-model-specific-tag)

        >[!NOTE]
        >
        >Tags können auch durch Auflisten der Metadaten eines Inhaltsfragments abgefragt werden.

   * Und Operationen:

      * `_operator` : Anwendung spezifischer Operatoren; `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`, `STARTS_WITH`
         * Siehe [Beispielabfrage – Alle Personen, die nicht den Namen „Jobs“ haben](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-persons-not-jobs)
         * Siehe [Beispielabfrage – Alle Abenteuer, bei denen `_path` mit einem bestimmten Präfix beginnt](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-all-adventures-cycling-path-filter)

      * `_apply`: bestimmte Bedingungen anwenden; zum Beispiel `AT_LEAST_ONCE`
         * Siehe [Beispielabfrage – Filtern eines Arrays nach einem Element, das mindestens einmal vorkommen muss](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-array-item-occur-at-least-once)

      * `_ignoreCase`: Groß-/Kleinschreibung bei der Abfrage ignorieren
         * Siehe [Beispielabfrage – Alle Städte mit SAN im Namen, unabhängig von der Groß-/Kleinschreibung](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-all-cities-san-ignore-case)

* GraphQL-Vereinigungstypen werden unterstützt:

   * Verwenden Sie `... on`
      * Siehe [Beispielabfrage für ein Inhaltsfragment eines bestimmten Modells mit einer Inhaltsreferenz](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-wknd-fragment-specific-model-content-reference)

* Fallback bei der Abfrage verschachtelter Fragmente:

   * Wenn die angeforderte Variante nicht in einem verschachtelten Fragment vorhanden ist, wird die **primäre Variante** ausgegeben.

### CORS-Filter {#cors-filter}

>[!CAUTION]
>
>Wenn [die Zwischenspeicherung im Dispatcher aktiviert wurde](#graphql-persisted-queries-enabling-caching-dispatcher), ist der CORS-Filter nicht erforderlich und dieser Abschnitt kann ignoriert werden.

>[!NOTE]
>
>Einen detaillierten Überblick über die CORS-Richtlinie zur gemeinsamen Nutzung von Ressourcen in AEM finden Sie unter [Verstehen von Cross-Origin Resource Sharing (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=de#understand-cross-origin-resource-sharing-(cors)).

Um auf den GraphQL-Endpunkt zuzugreifen, konfigurieren Sie eine CORS-Richtlinie im Git-Repository der Kundin bzw. des Kunden. Diese Konfiguration erfolgt durch Hinzufügen einer entsprechenden OSGi-CORS-Konfigurationsdatei für einen oder mehrere gewünschte Endpunkte.

Diese Konfiguration muss eine vertrauenswürdige Website-Herkunft `alloworigin` oder `alloworiginregexp` angeben, für die der Zugriff gewährt werden muss.

Um beispielsweise den Zugriff auf den GraphQL-Endpunkt und den Persistenzabfrage-Endpunkt für `https://my.domain` zu gewähren, können Sie Folgendes verwenden:

```xml
{
  "supportscredentials":true,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/_cq_graphql/global/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

Wenn Sie einen Vanity-Pfad für den Endpunkt konfiguriert haben, können Sie ihn auch in `allowedpaths` verwenden.

### Referrer-Filter {#referrer-filter}

Zusätzlich zur CORS-Konfiguration muss ein Referrer-Filter konfiguriert werden, um den Zugriff von Drittanbieter-Hosts zu ermöglichen.

Dieser Filter wird durch Hinzufügen einer entsprechenden OSGi Referrer-Filter-Konfigurationsdatei erstellt, die:

* einen vertrauenswürdigen Website-Hostnamen angibt (entweder `allow.hosts` oder `allow.hosts.regexp`),
* Zugriff auf diesen Hostnamen gewährt.

Um beispielsweise Zugriff auf Anfragen mit dem Referrer `my.domain` zu gewähren, können Sie:

```xml
{
    "allow.empty":false,
    "allow.hosts":[
      "my.domain"
    ],
    "allow.hosts.regexp":[
      ""
    ],
    "filter.methods":[
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp":[
      ""
    ]
}
```

>[!CAUTION]
>
>Der Kunde ist für Folgendes verantwortlich:
>
>* Nur Zugriff auf vertrauenswürdige Domains gewähren
>* Sicherstellen, dass keine vertraulichen Informationen offengelegt werden
>* Keine Platzhalter-Syntax [*] verwenden; diese Funktionalität deaktiviert den authentifizierten Zugriff auf den GraphQL-Endpunkt und macht ihn außerdem für die ganze Welt zugänglich.

>[!CAUTION]
>
>Alle GraphQL-[Schemata](#schema-generation) (abgeleitet von Inhaltsfragmentmodellen, die **aktiviert** wurden) können über den GraphQL-Endpunkt gelesen werden.
>
>Diese Funktion bedeutet, dass Sie sicherstellen müssen, dass keine sensiblen Daten verfügbar sind, da sie auf diese Weise weitergeleitet werden könnten. Dazu gehören zum Beispiel Informationen, die in der Modelldefinition als Feldnamen vorhanden sein könnten.

## Authentifizierung {#authentication}

Siehe [Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten](/help/sites-developing/headless/graphql-api/graphql-authentication-content-fragments.md).

## Häufig gestellte Fragen {#faqs}

Es wurden folgende Fragen aufgeworfen:

1. **F**: „*Wie unterscheidet sich die GraphQL-API für AEM von der Query Builder-API?*“

   * **A**:
„*Die AEM-GraphQL-API bietet vollständige Kontrolle über die JSON-Ausgabe und ist ein Industriestandard für die Abfrage von Inhalten.
In Zukunft plant AEM, in die AEM GraphQL-API zu investieren.*“

## Tutorial – Erste Schritte mit AEM Headless und GraphQL {#tutorial}

Suchen Sie nach einem praktischen Tutorial? Lesen Sie das umfassende Tutorial [Erste Schritte mit AEM Headless und GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de), in dem veranschaulicht wird, wie Inhalte mithilfe der GraphQL-APIs von AEM erstellt und verfügbar gemacht und von einer externen App in einem Headless CMS-Szenario verwendet werden.
