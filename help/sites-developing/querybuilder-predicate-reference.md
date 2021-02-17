---
title: Query Builder-Prädikatsreferenz
seo-title: Query Builder-Prädikatsreferenz
description: Vollständiger Eigenschaftsverweis für die Query Builder-API.
seo-description: Vollständiger Eigenschaftsverweis für die Query Builder-API.
uuid: af0e269e-7d52-4032-b22e-801c7b5dccfa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
discoiquuid: 94a05894-743a-4ace-a292-bfee90ba9068
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 60%

---


# Query Builder-Prädikatsreferenz{#query-builder-predicate-reference}

## Allgemein {#general}

* [root](#root)
* [group](#group)
* [orderby](#orderby)

## Prädikate {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [excludepaths ](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [fulltext](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [language](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [mainasset](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [memberOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [nodename](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [path](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [property](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [rangeproperty](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [relativedaterange](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [savedquery](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [similar](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [tag](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [tagid](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagsearch](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [type](/help/sites-developing/querybuilder-predicate-reference.md#type)

### boolproperty {#boolproperty}

Sucht nach JCR BOOLEAN-Eigenschaften. Akzeptiert nur die Werte &quot; `true`&quot;und &quot; `false`&quot;. Im Fall von „`false`“ besteht eine Übereinstimmung, falls die Eigenschaft über den Wert „`false`“ verfügt oder überhaupt nicht vorhanden ist. Dies kann für die Prüfung auf boolesche Flags nützlich sein, die nur festgelegt werden, wenn sie aktiviert sind.

Der übernommene Parameter „`operation`“ hat keine Bedeutung.

Unterstützt die Facettenextraktion. Erstellt für jeden Wert (`true` oder `false`) einen Bucket, aber nur für vorhandene Eigenschaften.

#### Eigenschaften {#properties}

* **Beispiel:**
boolpropertyRelativer Pfad zur Eigenschaft 
`myFeatureEnabled` oder `jcr:content/myFeatureEnabled`

* ****
Wert, für den die Eigenschaft überprüft werden soll: &quot; 
`true`&quot; oder &quot; `false`&quot;

### contentfragment {#contentfragment}

Schränkt das Ergebnis auf Inhaltsfragmente ein.

Filtern wird nicht unterstützt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-1}

* **contentfragment** Kann mit jedem Wert verwendet werden, um auf Inhaltsfragmente zu prüfen.

### dateComparison {#datecomparison}

Vergleicht zwei JCR DATE-Eigenschaften miteinander. Kann testen, ob sie gleich, ungleich, größer oder größer-oder-gleich sind.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

#### Eigenschaften {#properties-2}

* **property1**

   path to first date property

* **property2**

   path to second date property

* **operation**

   &quot; `=`&quot;für exakte Übereinstimmung, &quot; `!=`&quot;für Ungleichheitsvergleich, &quot; `>`&quot;für Eigenschaft1 größer als Eigenschaft2, &quot; `>=`&quot;für Eigenschaft1 größer oder gleich Eigenschaft2. Der Standardwert ist &quot; `=`&quot;.

### daterange {#daterange}

Gleicht JCR DATE-Eigenschaften mit einem Datums-/Zeitintervall ab. Hierbei wird das ISO8601-Format für Daten und Uhrzeiten (`YYYY-MM-DDTHH:mm:ss.SSSZ`) verwendet, wobei auch Teildarstellungen möglich sind, z. B. `YYYY-MM-DD`. Alternativ kann der Zeitstempel als Anzahl von Millisekunden seit 1970 in der Zeitzone UTC angegeben werden. Dies ist das Unix-Zeitformat.

Sie können nach allen Elementen zwischen zwei Zeitstempeln suchen, nach allem, was neuer oder älter als ein jeweiliges Datum ist, und aus inklusiven oder offenen Intervallen auswählen.

Unterstützt die Facettenextraktion. Stellt die Buckets „Heute“, „Diese Woche“, „Dieser Monat“, „Letzte 3 Monate“, „Dieses Jahr“, „Letztes Jahr“ und „Vor letztem Jahr“ zur Verfügung.

Filtern wird nicht unterstützt.

#### Eigenschaften {#properties-3}

* **property**

   relativer Pfad zu einer `DATE`-Eigenschaft, z. B. `jcr:lastModified`

* **lowerBound**

    Untere Datumsgrenze, auf welche die Eigenschaft überprüft werden soll, z. B. `2014-10-01`

* **lowerOperation**

   &quot; `>`&quot; (neuer) oder &quot; `>=`&quot; (ab oder neuer) gilt für das `lowerBound`. Der Standardwert lautet &quot; `>`&quot;.

* **upperBound**

   Obergrenze zur Überprüfung der Eigenschaft, z. B. `2014-10-01T12:15:00`

* **upperOperation**

   &quot; `<`&quot; (älter) oder &quot; `<=`&quot; (oder älter), gilt für das `upperBound`. Der Standardwert lautet &quot; `<`&quot;.

* **timeZone**

   Kennung der Zeitzone, die verwendet werden soll, wenn keine ISO-8601-Datumszeichenfolge angegeben wird. Der Standardwert ist die standardmäßige Zeitzone des Systems.

### excludepaths  {#excludepaths}

Schließt Knoten aus dem Ergebnis aus, wenn ihr Pfad mit einem regulären Ausdruck übereinstimmt.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-4}

* **excludepaths**

   Regulärer Ausdruck, der anhand von Ergebnispfaden ausgewertet wird, wobei übereinstimmende aus dem Ergebnis ausgeschlossen werden.

### fulltext {#fulltext}

Sucht nach Ausdrücken im Volltextindex.

Filtern wird nicht unterstützt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-5}

* **fulltext**

   der/die Suchbegriff(e) im Volltext

* **relPath**

   Der relative Pfad, der in der Eigenschaft oder dem Teilknoten durchsucht werden soll. Diese Eigenschaft ist optional.

### group {#group}

Ermöglicht die Erstellung verschachtelter Bedingungen. Gruppen können verschachtelte Gruppen enthalten. Alles in einer querybuilder-Abfrage gehört zu einer root-Gruppe, die auch `p.or`- und `p.not`-Parameter aufweisen kann.

Beispiel für die Zuordnung einer von zwei Eigenschaften anhand eines Werts:

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Dies ist konzeptionell `(1_property` ODER `2_property)`.

Beispiel für verschachtelte Gruppen:

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

Dieser sucht nach dem Begriff &quot;**Management**&quot;innerhalb von Seiten in `/content/geometrixx/en` oder in Assets in `/content/dam/geometrixx`.

Dies ist konzeptionell `fulltext AND ( (path AND type) OR (path AND type) )`. Beachten Sie, dass solche ODER-Verknüpfungen gute Indizes benötigen, um optimale Leistung zu bieten.

#### Eigenschaften {#properties-6}

* **p.or**

   bei Festlegung auf &quot; `true`&quot;muss nur eine Vorhersage in der Gruppe übereinstimmen. Standardmäßig ist „`false`“ festgelegt, was bedeutet, dass alle übereinstimmen müssen.

* **p.not**

   Wenn auf &quot;`true`&quot;gesetzt, wird die Gruppe umgekehrt (standardmäßig auf &quot;`false`&quot;).

* **&lt;predicate>**

   fügt verschachtelte Prädikate hinzu

* **N_&lt;predicate>**

   fügt mehrere verschachtelte Vorhersagen gleichzeitig hinzu, z. B. `1_property, 2_property, ...`

### hasPermission {#haspermission}

Beschränkt das Ergebnis auf Elemente, bei denen die aktuelle Sitzung die angegebenen [JCR-Privilegien](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) aufweist.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-7}

* **hasPermission**

   kommagetrennte JCR-Berechtigungen, die die aktuelle Benutzersitzung ALLE für den betreffenden Knoten haben muss; zum Beispiel `jcr:write`, `jcr:modifyAccessControl`

### language {#language}

Findet CQ-Seiten in einer bestimmten Sprache. Hierbei wird sowohl die Spracheigenschaft der Seite als auch der Seitenpfad betrachtet, der häufig die Sprache oder das Gebietsschema in einer Site-Struktur der höchsten Ebene enthält.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Unterstützt die Facettenextraktion. Stellt Buckets für jeden eindeutigen Sprachcode zur Verfügung.

#### Eigenschaften {#properties-8}

* **language**

   ISO-Sprachcode, z. B. &quot; `de`&quot;

### mainasset {#mainasset}

Prüft, ob ein Knoten ein DAM-Haupt-Asset und kein Unter-Asset ist. Dies ist im Allgemeinen jeder Knoten, der sich nicht in einem subassets-Knoten befindet. Hierbei wird nicht auf den Knotentyp `dam:Asset` geprüft. Um diese Prognose zu verwenden, stellen Sie einfach &quot; `mainasset=true`&quot;oder &quot; `mainasset=false`&quot;ein, es gibt keine weiteren Eigenschaften.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Unterstützt die Facettenextraktion. Stellt zwei Buckets für Haupt- und Unter-Assets bereit.

#### Eigenschaften {#properties-9}

* **mainasset**

   boolean, &quot; `true`&quot;für Hauptelemente, &quot; `false`&quot;für Teilassets

### memberOf {#memberof}

Sucht Objekte, die Mitglieder einer bestimmten [Sling-Ressourcensammlung](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) sind.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-10}

* **memberOf**

   Pfad zur Sling-Ressourcensammlung

### nodename {#nodename}

Sucht nach Namen von JCR-Knoten.

Unterstützt die Facettenextraktion. Stellt Buckets für alle eindeutigen Knotennamen (Dateinamen) zur Verfügung.

#### Eigenschaften {#properties-11}

* **nodename**

   Knotennamenmuster, das Platzhalter zulässt: `*` = beliebige oder keine Zeichen, `?` = beliebige Zeichen, `[abc]` = nur Zeichen in Klammern

### notexpired {#notexpired}

Wertet Elemente aus, indem überprüft wird, ob eine JCR DATE-Eigenschaft größer oder gleich der aktuellen Serverzeit ist. Dies kann verwendet werden, um eine Datumseigenschaft wie „`expiresAt`“ zu überprüfen und das Ergebnis auf diejenigen zu beschränken, die noch nicht abgelaufen sind (`notexpired=true`) bzw. bereits abgelaufen sind ( `notexpired=false`).

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie die Eigenschaft „daterange“.

#### Eigenschaften {#properties-12}

* **notexpired**

   Boolescher Wert, „`true`“ für noch nicht abgelaufen (Datum in der Zukunft oder gleich), „`false`“ für abgelaufen (Datum in der Vergangenheit) (erforderlich)

* **property**

   relativer Pfad zur zu überprüfenden `DATE`-Eigenschaft (erforderlich)

### orderby {#orderby}

Ermöglicht das Sortieren des Ergebnisses. Wenn nach mehreren Eigenschaften geordnet werden muss, muss dieses Prädikat anhand des Präfix mehrfach hinzugefügt werden, z. B. `1_orderby=first`, `2_oderby=second`.

#### Eigenschaften {#properties-13}

* **orderby**

   entweder der Name der JCR-Eigenschaft, der durch ein vorangestelltes @ angegeben wird, z. B. `@jcr:lastModified` oder `@jcr:content/jcr:title`, oder eine andere Vorhersage in der Abfrage, z. B. `2_property`, nach der sortiert werden soll

* **sortieren**

   Sortierrichtung, entweder &quot; `desc`&quot;für absteigend oder &quot; `asc`&quot;für aufsteigend (Standard)

* **case**

    Wird hierfür „`ignore`“ festgelegt, wird die Groß-/Kleinschreibung nicht beachtet, „a“ kommt also vor „B“. Wird dies leer- oder ausgelassen, wird bei der Sortierung die Groß-/Kleinschreibung beachtet, „B“ kommt also vor „a“.

### path {#path}

Sucht innerhalb eines gegebene Pfads.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-14}

* **path**

   Pfadmuster; je nach Genauigkeit wird entweder der gesamte Unterbaum übereinstimmen (z. B. `//*` in xpath anhängen, aber beachten Sie, dass dies nicht den Basispfad enthält) (exact=false, default) oder nur exakte Pfadübereinstimmungen, die Platzhalter enthalten können ( `*`). Wenn self festgelegt ist, wird die gesamte Unterstruktur einschließlich des Basisknotens durchsucht

* **genau**

   Wenn `exact` &quot;true/on&quot;ist, muss der genaue Pfad übereinstimmen, er kann jedoch einfache Platzhalter ( `*`) enthalten, die mit Namen übereinstimmen, jedoch nicht &quot; `/`&quot;; Wenn er &quot;false&quot;ist (Standard), werden alle untergeordneten Elemente einbezogen (optional)

* **flach**

   durchsucht nur die direkten untergeordneten Elemente (z. B. &quot;`/*`&quot;in xpath) (nur verwendet, wenn &quot;`exact`&quot;nicht true ist, optional)

* **self**

   Durchsucht den Teilbaum aber bezieht den als Pfad angegebenen Basisknoten mit ein (keine Platzhalter)

### property {#property}

Sucht nach JCR-Eigenschaften und ihren Werten.

Unterstützt die Facettenextraktion. Stellt für jeden eindeutigen Eigenschaftswert in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#properties-15}

* **property**

   relativer Pfad zur Eigenschaft, z. B. `jcr:title`

* **value**

    Wert, auf den die Eigenschaft überprüft werden soll. Verarbeitet Umwandlungen anhand des JCR-Eigenschaftstyps als Zeichenfolgen.

* **N_value**

   use `1_value`, `2_value`, ... , um nach mehreren Werten zu suchen (standardmäßig mit `OR` und `AND` if und=true) (seit 5.3)

* **und**

   auf &quot;true&quot;gesetzt, wenn mehrere Werte ( `N_value`) mit AND (seit 5.3) kombiniert werden

* **operation**

   &quot; `equals`&quot;für exakte Übereinstimmung (Standard), &quot; `unequals`&quot;für Ungleichheitsvergleich, &quot; `like`&quot;für die Verwendung der `jcr:like` xpath-Funktion (optional), &quot; `not`&quot;für keine Übereinstimmung (z. B. &quot; `not(@prop)`&quot;in xpath wird value param ignoriert) oder &quot; `exists`&quot;für die Überprüfung der Existenz (Wert kann true sein - Eigenschaft muss vorhanden sein, der Standardwert - oder false - identisch mit &quot; `not`&quot;

* **depth**

   Anzahl der Platzhalterebenen, unter denen die Eigenschaft/der relative Pfad vorhanden sein kann (z. B. überprüft `property=size depth=2` Node/Größe, Node/&amp;ast;/Größe und Node/&amp;ast;/&amp;ast;/Größe))

### rangeproperty {#rangeproperty}

Ordnet eine JCR-Eigenschaft einem Intervall zu. Dies gilt für Eigenschaften mit linearen Typen wie `LONG`, `DOUBLE` und `DECIMAL`. Details zu `DATE` finden Sie im Abschnitt zur Eigenschaft „daterange“, die für Eingaben im Datumsformat optimiert wurde.

Sie können eine untere Grenze und eine obere Grenze oder nur eine von ihnen definieren. Der Vorgang (z. B. „lesser than“ oder „lesser or equals“) kann auch einzeln für die untere und obere Grenze festgelegt werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-16}

* **property**

   relativer Pfad zur Eigenschaft

* **lowerBound**

   lower bound to check-Eigenschaft für

* **lowerOperation**

   &quot; `>`&quot; (Standard) oder &quot; `>=`&quot;, gilt für das `lowerValue`

* **upperBound**

   Obergrenze für Prüfeigenschaft

* **upperOperation**

   &quot; `<`&quot; (Standard) oder &quot; `<=`&quot;, gilt für das `lowerValue`

* **decimal**

   &quot; `true`&quot;, wenn die überprüfte Eigenschaft vom Typ Decimal ist

### relativedaterange {#relativedaterange}

Gleicht `JCR DATE`-Eigenschaften anhand von Zeit-Offsets, die relativ zur aktuellen Serverzeit sind, mit einem Datums-/Zeitintervall ab. Sie können `lowerBound` und `upperBound` entweder einen Millisekunden-Wert oder die Bugzilla-Syntax `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) angeben. Präfix mit &quot; `-`&quot;, um einen negativen Offset vor der aktuellen Zeit anzugeben. Wenn Sie nur `lowerBound` oder `upperBound` angeben, wird für die jeweils andere Grenze standardmäßig „0“ festgelegt, was die aktuelle Zeit bedeutet.

Beispiel:

* `upperBound=1h` (und nein  `lowerBound`) würde in der nächsten Stunde irgendetwas auswählen
* `lowerBound=-1d` (und nein  `upperBound`) würde in den letzten 24 Stunden etwas auswählen
* `lowerBound=-6M` und  `upperBound=-3M` wählen Sie alle sechs Monate bis drei Monate aus.
* `lowerBound=-1500` und `upperBound=5500` wählt alles aus, was im Zeitraum zwischen einschließlich 1500 Millisekunden in der Vergangenheit und einschließlich 5500 Millisekunden in der Zukunft liegt. 
* `lowerBound=1d` und  `upperBound=2d` wählen übermorgen alles aus

Hinweis: Schaltjahre werden nicht berücksichtigt und alle Monate haben 30 Tage.

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie die Eigenschaft „daterange“.

#### Eigenschaften {#properties-17}

* **upperBound**

   Oberes Datum in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) im Verhältnis zur aktuellen Serverzeit, verwenden Sie &quot;-&quot;für negativen Offset

* **lowerBound**

   untere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) im Verhältnis zur aktuellen Serverzeit verwenden Sie &quot;-&quot;für einen negativen Offset

### root {#root}

Stammeigenschaftsgruppe. Unterstützt alle Eigenschaften einer Gruppe und ermöglicht das Festlegen globaler Abfrage-Parameter.

Der Name „root“ wird in Abfragen nie verwendet, er ist impliziert.

#### Eigenschaften {#properties-18}

* **p.offset**

    Zahl, die den Anfang der Ergebnisseite anzeigt, d. h. wie viele Elemente übersprungen werden sollen.

* **p.limit**

   Zahl, die das Seitenformat angibt

* **p.rateTotal**

   empfohlen: Vermeidung der Berechnung des Gesamtergebnisses, das kostspielig sein kann; entweder eine Zahl, die die maximal zu zählende Summe angibt (z. B. 1000, eine Zahl, die den Benutzern genügend Feedback zur Rohgröße und exakten Zahlen für kleinere Ergebnisse gibt) oder &quot; `true`&quot;, um nur bis zum notwendigen Minimum `p.offset` + `p.limit` zu zählen

* **p.excerpt**

   Wenn auf &quot;`true`&quot;eingestellt, geben Sie den Volltextsausschnitt in das Ergebnis ein

* **p.hits**

    (nur für das JSON-Servlet) Legt fest, wie Treffer als JSON geschrieben werden. Folgende Standardmethoden stehen zur Auswahl (erweiterbar über den Dienst „ResultHitWriter“):

   * **einfach**:

      Minimale Elemente wie `path`, `title`, `lastmodified`, `excerpt` (falls festgelegt)

   * **vollständig**:

      Sling JSON-Rendering des Knotens, wobei `jcr:path` den Pfad des Treffers angibt: standardmäßig nur Listen der direkten Eigenschaften des Knotens, fügen Sie einen tieferen Baum mit `p.nodedepth=N` ein, wobei 0 die gesamte, unendliche Unterstruktur bedeutet; Fügen Sie `p.acls=true` hinzu, um die JCR-Berechtigungen der aktuellen Sitzung für das angegebene Ergebniselement (Zuordnungen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`)

   * **selektiv**:

      nur Eigenschaften, die in der Liste relativer Pfade angegeben sind (mit &quot;+&quot;in URLs); Wenn der relative Pfad eine Tiefe > 1 aufweist, werden diese als untergeordnete Objekte dargestellt. Die Eigenschaft &quot;jcr:path&quot;enthält den Pfad des Treffers`p.properties`

### savedquery {#savedquery}

Fügt alle Eigenschaften einer beständigen querybuilder-Abfrage der aktuellen Abfrage als Untergruppeneigenschaft hinzu.

Dabei wird keine zusätzliche Abfrage ausgeführt, sondern die aktuellen Abfrage erweitert.

Abfragen können programmgesteuert anhand von `QueryBuilder#storeQuery()` beibehalten werden. Das Format kann entweder eine String-Eigenschaft mit mehreren Zeilen oder ein `nt:file`-Knoten sein, der die Abfrage als Textdatei im Java-Eigenschaftsformat enthält.

Die Facettenextraktion wird für die Eigenschaften der gespeicherten Abfrage nicht unterstützt 

#### Eigenschaften {#properties-19}

* **gespeicherte Abfrage**

   Pfad zur gespeicherten Abfrage (String-Eigenschaft oder `nt:file`-Knoten)

### similar {#similar}

Ähnlichkeitssuche mit dem JCR XPath `rep:similar()`.

Filtern wird nicht unterstützt. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-20}

* **similar** Absoluter Pfad zum Knoten, für den ähnliche Knoten gefunden werden sollen.

* ****
locala relativer Pfad zu einem untergeordneten Knoten oder 
`.` für die aktuelle Node (optional) (Standard ist &quot;  `.`&quot;)

### tag {#tag}

Sucht nach Inhalten mit Tags, indem Tag-Titelpfade angegeben werden.

Unterstützt die Facettenextraktion. Stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils der aktuelle Tag-Titelpfad verwendet.

#### Eigenschaften {#properties-21}

* **tag**

    Tag-Titelpfad, nach dem gesucht werden soll, z. B. „Asset-Eigenschaften: Ausrichtung/Querformat“

* **N_value**

   use `1_value`, `2_value`, ... , um nach mehreren Tags zu suchen (standardmäßig mit `OR` und `AND` if und=true) (seit 5.6)

* **property**

   Eigenschaft (oder relativer Pfad zur Eigenschaft), die angezeigt werden soll (Standard &quot; `cq:tags`&quot;)

### tagid {#tagid}

Sucht nach Inhalten mit Tags, indem Tag-IDs angegeben werden.

Unterstützt die Facettenextraktion. Stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils der aktuelle Tag-ID verwendet.

#### Eigenschaften {#properties-22}

* **tagid**

   Tag-ID, nach der gesucht werden soll, z. B. &quot; `properties:orientation/landscape`&quot;

* **N_value**

   use `1_value`, `2_value`, ... , um nach mehreren Tagids zu suchen (standardmäßig mit `OR` und `AND` if und=true) (seit 5.6)

* **property**

   Eigenschaft (oder relativer Pfad zur Eigenschaft), die angezeigt werden soll (Standard &quot; `cq:tags`&quot;)

### tagsearch {#tagsearch}

Sucht nach Inhalten mit Tags, indem Suchbegriffe angegeben werden. Hierbei wird zunächst nach Tags gesucht, die diese Suchbegriffe in ihrem Titel enthalten, worauf das Ergebnis auf Elemente mit diesen Tags eingeschränkt wird.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#Properties-1}

* **tagsearch**

   Suchbegriff, nach dem in Tag-Titeln gesucht werden soll

* **property**

   Eigenschaft (oder relativer Pfad zur Eigenschaft), die angezeigt werden soll (Standard &quot; `cq:tags`&quot;)

* **lang**

   um nur in einem bestimmten lokalisierten Tag-Titel zu suchen (z. &quot; `de`&quot;)

* **all**

   (bool) den gesamten Tag Volltext durchsuchen, d.h. alle Titel, Beschreibung usw. (hat Vorrang vor &quot;l `ang`&quot;)

### type {#type}

Schränkt Ergebnisse auf einen bestimmten JCR-Knotentyp ein, sowohl den primären Knotentyp als auch den Mixin-Typ. Hierbei werden auch Untertypen dieses Knotentyps gefunden. Zur effizienten Ausführung müssen Repository-Suchindizes die Knotentypen enthalten.

Unterstützt die Facettenextraktion. Stellt für jeden einzigartigen Typ in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#Properties-2}

* **type**

   Node-Typ oder Name der Mischung, nach der gesucht werden soll, z. B. `cq:Page`