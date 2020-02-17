---
title: Query Builder-Eigenschaftsverweis
seo-title: Query Builder-Eigenschaftsverweis
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

---


# Query Builder-Eigenschaftsverweis{#query-builder-predicate-reference}

## Allgemein {#general}

* [root](#root)
* [group](#group)
* [orderby](#orderby)

## Eigenschaften {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [excludepaths](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
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

Sucht nach JCR BOOLEAN-Eigenschaften. Only accepts the values &quot; `true`&quot; and &quot; `false`&quot;. Im Fall von „`false`“ besteht eine Übereinstimmung, falls die Eigenschaft über den Wert „`false`“ verfügt oder überhaupt nicht vorhanden ist. Dies kann für die Prüfung auf boolesche Flags nützlich sein, die nur festgelegt werden, wenn sie aktiviert sind.

Der übernommene Parameter „`operation`“ hat keine Bedeutung.

Unterstützt die Facettenextraktion. Erstellt für jeden Wert (`true` oder `false`) einen Bucket, aber nur für vorhandene Eigenschaften.

#### Eigenschaften {#properties}

* **boolproperty** relative path to property, z. B. `myFeatureEnabled` oder `jcr:content/myFeatureEnabled`

* **Wert**, für den die Eigenschaft &quot;, `true`&quot;oder &quot; `false`&quot; überprüft werden soll

### contentfragment {#contentfragment}

Schränkt das Ergebnis auf Inhaltsfragmente ein.

Filtern wird nicht unterstützt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-1}

* **contentfragment** Kann mit jedem Wert verwendet werden, um auf Inhaltsfragmente zu prüfen.

### dateComparison {#datecomparison}

Vergleicht zwei JCR DATE-Eigenschaften miteinander. Kann testen, ob sie gleich, ungleich, größer oder größer-oder-gleich sind.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

#### Eigenschaften {#properties-2}

* **property1**

   path to first date property

* **property2**

   path to second date property

* **operation**

   &quot; `=`&quot; for exact match, &quot; `!=`&quot; for unequality comparison, &quot; `>`&quot; for property1 greater than property2, &quot; `>=`&quot; for property1 greater than or equal to property2. Der Standardwert ist &quot; `=`&quot;.

### daterange {#daterange}

Gleicht JCR DATE-Eigenschaften mit einem Datums-/Zeitintervall ab. This uses the ISO8601
format for dates and times ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) and allows also partial representations, like `YYYY-MM-DD`. Alternativ kann der Zeitstempel als Anzahl von Millisekunden seit 1970 in der Zeitzone UTC angegeben werden. Dies ist das Unix-Zeitformat.

Sie können nach allen Elementen zwischen zwei Zeitstempeln suchen, nach allem, was neuer oder älter als ein jeweiliges Datum ist, und aus inklusiven oder offenen Intervallen auswählen.

Unterstützt die Facettenextraktion. Stellt die Buckets „Heute“, „Diese Woche“, „Dieser Monat“, „Letzte 3 Monate“, „Dieses Jahr“, „Letztes Jahr“ und „Vor letztem Jahr“ zur Verfügung.

Filtern wird nicht unterstützt.

#### Eigenschaften {#properties-3}

* **property**

   relative path to a `DATE` property, for example `jcr:lastModified`

* **lowerBound**

   lower date bound to check property for, for example `2014-10-01`

* **lowerOperation**

   &quot; `>`&quot; (newer) or &quot; `>=`&quot; (at or newer), applies to the `lowerBound`. Der Standardwert lautet &quot; `>`&quot;.

* **upperBound**

   upper bound to check property for, for example `2014-10-01T12:15:00`

* **upperOperation**

   &quot; `<`&quot; (older) or &quot; `<=`&quot; (at or older), applies to the `upperBound`. Der Standardwert lautet &quot; `<`&quot;.

* **timeZone**

   Kennung der Zeitzone, die verwendet werden soll, wenn keine ISO-8601-Datumszeichenfolge angegeben wird. Der Standardwert ist die standardmäßige Zeitzone des Systems.

### excludepaths {#excludepaths}

Schließt Knoten aus dem Ergebnis aus, wenn ihr Pfad mit einem regulären Ausdruck übereinstimmt.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

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

   der/die Volltextsuchbegriff(e)

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

This is conceptually `(1_property` OR `2_property)`.

Beispiel für verschachtelte Gruppen:

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

This searches for the term &quot;**Management**&quot; within pages in `/content/geometrixx/en` or in assets in `/content/dam/geometrixx`.

Das ist konzeptionell `fulltext AND ( (path AND type) OR (path AND type) )`. Beachten Sie, dass solche ODER-Verknüpfungen gute Indizes benötigen, um optimale Leistung zu bieten.

#### Eigenschaften {#properties-6}

* **p.or**

   if set to &quot; `true`&quot;, only one predicate in the group must match. Standardmäßig ist „`false`“ festgelegt, was bedeutet, dass alle übereinstimmen müssen.

* **p.not**

   if set to &quot; `true`&quot;, it negates the group (defaults to &quot; `false`&quot;)

* **&lt;preate>**

   fügt verschachtelte Prädikate hinzu

* **N_&lt;Vorhersage>**

   adds multiple nested predicates of the same time, like `1_property, 2_property, ...`

### hasPermission {#haspermission}

Beschränkt das Ergebnis auf Elemente, bei denen die aktuelle Sitzung die angegebenen [JCR-Privilegien](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) aufweist.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-7}

* **hasPermission**

   comma-separated JCR privileges that the current user session must ALL have for the node in question; for example `jcr:write`, `jcr:modifyAccessControl`

### language {#language}

Findet CQ-Seiten in einer bestimmten Sprache. Hierbei wird sowohl die Spracheigenschaft der Seite als auch der Seitenpfad betrachtet, der häufig die Sprache oder das Gebietsschema in einer Site-Struktur der höchsten Ebene enthält.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

Unterstützt die Facettenextraktion. Stellt Buckets für jeden eindeutigen Sprachcode zur Verfügung.

#### Eigenschaften {#properties-8}

* **language**

   ISO language code, for example &quot; `de`&quot;

### mainasset {#mainasset}

Prüft, ob ein Knoten ein DAM-Haupt-Asset und kein Unter-Asset ist. Dies ist im Allgemeinen jeder Knoten, der sich nicht in einem subassets-Knoten befindet. Hierbei wird nicht auf den Knotentyp `dam:Asset` geprüft. To use this predicate, simply set &quot; `mainasset=true`&quot; or &quot; `mainasset=false`&quot;, there are no further properties.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

Unterstützt die Facettenextraktion. Stellt zwei Buckets für Haupt- und Unter-Assets bereit.

#### Eigenschaften {#properties-9}

* **mainasset**

   boolean, &quot; `true`&quot; for main assets, &quot; `false`&quot; for sub assets

### memberOf {#memberof}

Sucht Objekte, die Mitglieder einer bestimmten [Sling-Ressourcensammlung](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) sind.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-10}

* **memberOf**

   Pfad zur Sling-Ressourcensammlung

### nodename {#nodename}

Sucht nach Namen von JCR-Knoten.

Unterstützt die Facettenextraktion. Stellt Buckets für alle eindeutigen Knotennamen (Dateinamen) zur Verfügung.

#### Eigenschaften {#properties-11}

* **nodename**

   node name pattern that allows wildcards: `*` = any or no char, `?` = any char, `[abc]` = only chars in brackets

### notexpired {#notexpired}

Wertet Elemente aus, indem überprüft wird, ob eine JCR DATE-Eigenschaft größer oder gleich der aktuellen Serverzeit ist. Dies kann verwendet werden, um eine Datumseigenschaft wie „`expiresAt`“ zu überprüfen und das Ergebnis auf diejenigen zu beschränken, die noch nicht abgelaufen sind (`notexpired=true`) bzw. bereits abgelaufen sind ( `notexpired=false`).

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie die Eigenschaft „daterange“.

#### Eigenschaften {#properties-12}

* **notexpired**

   Boolescher Wert, „`true`“ für noch nicht abgelaufen (Datum in der Zukunft oder gleich), „`false`“ für abgelaufen (Datum in der Vergangenheit) (erforderlich)

* **property**

   relative path to the `DATE` property to check (required)

### orderby {#orderby}

Ermöglicht das Sortieren des Ergebnisses. If ordering by multiple properties is required, this predicate needs to be added multiple times using the number prefix, such as `1_orderby=first`, `2_oderby=second`.

#### Eigenschaften {#properties-13}

* **orderby**

   either JCR property name indicated by a leading @, for example `@jcr:lastModified` or `@jcr:content/jcr:title`, or another predicate in the query, for example `2_property`, on which to sort

* **sortieren**

   sort direction, either &quot; `desc`&quot; for descending or &quot; `asc`&quot; for ascending (default)

* **case**

    Wird hierfür „`ignore`“ festgelegt, wird die Groß-/Kleinschreibung nicht beachtet, „a“ kommt also vor „B“. Wird dies leer- oder ausgelassen, wird bei der Sortierung die Groß-/Kleinschreibung beachtet, „B“ kommt also vor „a“.

### path {#path}

Sucht innerhalb eines gegebene Pfads.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-14}

* **path**

   path pattern; depending on exact, either the entire subtree will match (like appending `//*` in xpath, but note that this does not include the base path) (exact=false, default) or only an exact path matches, which can include wildcards ( `*`); if self is set, the entire subtree including the base node will be searched

* **genau**

   if `exact` is true/on, the exact path must match, but it can contain simple wildcards ( `*`), that match names, but not &quot; `/`&quot;; if it is false (default) all descendents are included (optional)

* **flach**

   searches only the direct children (like appending &quot; `/*`&quot; in xpath) (only used if &#39; `exact`&#39; is not true, optional)

* **self**

   Durchsucht den Teilbaum aber bezieht den als Pfad angegebenen Basisknoten mit ein (keine Platzhalter)

### property {#property}

Sucht nach JCR-Eigenschaften und ihren Werten.

Unterstützt die Facettenextraktion. Stellt für jeden eindeutigen Eigenschaftswert in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#properties-15}

* **property**

   relative path to property, for example `jcr:title`

* **value**

    Wert, auf den die Eigenschaft überprüft werden soll. Verarbeitet Umwandlungen anhand des JCR-Eigenschaftstyps als Zeichenfolgen.

* **N_value**

   use `1_value`, `2_value`, ... to check for multiple values (combined with `OR` by default, with `AND` if and=true) (since 5.3)

* **und**

   set to true for combining multiple values ( `N_value`) with AND (since 5.3)

* **operation**

   &quot; `equals`&quot;für exakte Übereinstimmung (Standard), &quot; `unequals`&quot;für Ungleichheitsvergleich, &quot; `like`&quot;für die Verwendung der `jcr:like` xpath-Funktion (optional), &quot; `not`&quot;für keine Übereinstimmung (z. B. &quot; `not(@prop)`&quot;in xpath wird value param ignoriert) oder &quot; `exists`&quot;für die Prüfung der Existenz (Wert kann true sein - Eigenschaft muss vorhanden sein, Standard - oder false - identisch mit &quot; `not`&quot;

* **depth**

   Anzahl der Platzhalterebenen, unter denen die Eigenschaft/der relative Pfad vorhanden sein kann (z. B. `property=size depth=2` überprüft Node/Größe, Node/&amp;ast;/size und node/&amp;ast;/&amp;ast;/size)

### rangeproperty {#rangeproperty}

Ordnet eine JCR-Eigenschaft einem Intervall zu. This applies to properties with linear types such as `LONG`, `DOUBLE` and `DECIMAL`. Details zu `DATE` finden Sie im Abschnitt zur Eigenschaft „daterange“, die für Eingaben im Datumsformat optimiert wurde.

Sie können eine untere Grenze und eine obere Grenze oder nur eine von ihnen definieren. Der Vorgang (z. B. „lesser than“ oder „lesser or equals“) kann auch einzeln für die untere und obere Grenze festgelegt werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-16}

* **property**

   relativer Pfad zur Eigenschaft

* **lowerBound**

   lower bound to check-Eigenschaft für

* **lowerOperation**

   &quot; `>`&quot; (default) or &quot; `>=`&quot;, applies to the `lowerValue`

* **upperBound**

   Obergrenze für Prüfeigenschaft

* **upperOperation**

   &quot; `<`&quot; (default) or &quot; `<=`&quot;, applies to the `lowerValue`

* **decimal**

   &quot; `true`&quot; if the checked property is of type Decimal

### relativedaterange {#relativedaterange}

Gleicht `JCR DATE`-Eigenschaften anhand von Zeit-Offsets, die relativ zur aktuellen Serverzeit sind, mit einem Datums-/Zeitintervall ab. You can specify `lowerBound` and `upperBound` using either a millisecond value or the bugzilla syntax `1s 2m 3h 4d 5w 6M 7y` (one second, two minutes, three hours, four days, five weeks, six months, seven years). Prefix with &quot; `-`&quot; to indicate a negative offset before the current time. Wenn Sie nur `lowerBound` oder `upperBound` angeben, wird für die jeweils andere Grenze standardmäßig „0“ festgelegt, was die aktuelle Zeit bedeutet.

Beispiel:

* `upperBound=1h` (und nein `lowerBound`) würde in der nächsten Stunde etwas auswählen
* `lowerBound=-1d` (und keine `upperBound`) würde in den letzten 24 Stunden etwas auswählen
* `lowerBound=-6M` und `upperBound=-3M` wählen Sie alle 6 Monate bis 3 Monate aus
* `lowerBound=-1500` und `upperBound=5500` wählt alles aus, was im Zeitraum zwischen einschließlich 1500 Millisekunden in der Vergangenheit und einschließlich 5500 Millisekunden in der Zukunft liegt. 
* `lowerBound=1d` und `upperBound=2d` wählen übermorgen alles aus

Hinweis: Schaltjahre werden nicht berücksichtigt und alle Monate haben 30 Tage.

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie die Eigenschaft „daterange“.

#### Eigenschaften {#properties-17}

* **upperBound**

   upper date bound in milliseconds or `1s 2m 3h 4d 5w 6M 7y` (one second, two minutes, three hours, four days, five weeks, six months, seven years) relative to current server time, use &quot;-&quot; for negative offset

* **lowerBound**

   lower date bound in milliseconds or `1s 2m 3h 4d 5w 6M 7y` (one second, two minutes, three hours, four days, five weeks, six months, seven years) relative to current server time, use &quot;-&quot; for negative offset

### root {#root}

Stammeigenschaftsgruppe. Unterstützt alle Eigenschaften einer Gruppe und ermöglicht das Festlegen globaler Abfrage-Parameter.

Der Name „root“ wird in Abfragen nie verwendet, er ist impliziert.

#### Eigenschaften {#properties-18}

* **p.offset**

    Zahl, die den Anfang der Ergebnisseite anzeigt, d. h. wie viele Elemente übersprungen werden sollen.

* **p.limit**

   Zahl zur Angabe der Seitengröße

* **p.rateTotal**

   recommended: avoid calculating the full result total which can be costly; either a number indicating the maximum total to count up to (for example 1000, a number that gives users enough feedback on the rough size and exact numbers for smaller results) or &quot; `true`&quot; to count only up to the minimum necessary `p.offset` + `p.limit`

* **p.excerpt**

   if set to &quot; `true`&quot;, include full text excerpt in the result

* **p.hits**

    (nur für das JSON-Servlet) Legt fest, wie Treffer als JSON geschrieben werden. Folgende Standardmethoden stehen zur Auswahl (erweiterbar über den Dienst „ResultHitWriter“):

   * **einfach**:

      Minimale Elemente wie `path`, `title`, `lastmodified`, `excerpt` (falls festgelegt)

   * **vollständig**:

      sling JSON rendering of the node, with `jcr:path` indicating the path of the hit: by default just lists the direct properties of the node, include a deeper tree with `p.nodedepth=N`, with 0 meaning the entire, infinite subtree; add `p.acls=true` to include the JCR permissions of the current session on the given result item (mappings: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`)

   * **selektiv**:

      only properties specified in `p.properties`, which is a space separated (use &quot;+&quot; in URLs) list of relative paths; if the relative path has a depth > 1 these will be represented as child objects; the special jcr:path property includes the path of the hit

### savedquery {#savedquery}

Fügt alle Eigenschaften einer beständigen querybuilder-Abfrage der aktuellen Abfrage als Untergruppeneigenschaft hinzu.

Dabei wird keine Extra-Abfrage ausgeführt, sondern die aktuellen Query erweitert.

Queries can be persisted programmatically using `QueryBuilder#storeQuery()`. Das Format kann entweder eine String-Eigenschaft mit mehreren Zeilen oder ein `nt:file`-Knoten sein, der die Abfrage als Textdatei im Java-Eigenschaftsformat enthält.

Die Facettenextraktion wird für die Eigenschaften der gespeicherten Abfrage nicht unterstützt 

#### Eigenschaften {#properties-19}

* **savedquery**

   path to the saved query (String property or `nt:file` node)

### similar {#similar}

Similarity search using JCR XPath&#39;s `rep:similar()`.

Filtern wird nicht unterstützt. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-20}

* **similar** Absoluter Pfad zum Knoten, für den ähnliche Knoten gefunden werden sollen.

* **lokal** ein relativer Pfad zu einem untergeordneten Knoten oder `.` für den aktuellen Knoten (optional, Standard ist `.`&quot;)

### tag {#tag}

Sucht nach Inhalten mit Tags, indem Tag-Titelpfade angegeben werden.

Unterstützt die Facettenextraktion. Stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils der aktuelle Tag-Titelpfad verwendet.

#### Eigenschaften {#properties-21}

* **tag**

    Tag-Titelpfad, nach dem gesucht werden soll, z. B. „Asset-Eigenschaften: Ausrichtung/Querformat“

* **N_value**

   use `1_value`, `2_value`, ... to check for multiple tags (combined with `OR` by default, with `AND` if and=true) (since 5.6)

* **property**

   property (or relative path to property) to look at (default &quot; `cq:tags`&quot;)

### tagid {#tagid}

Sucht nach Inhalten mit Tags, indem Tag-IDs angegeben werden.

Unterstützt die Facettenextraktion. Stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils der aktuelle Tag-ID verwendet.

#### Eigenschaften {#properties-22}

* **tagid**

   tag id to look for, for example &quot; `properties:orientation/landscape`&quot;

* **N_value**

   use `1_value`, `2_value`, ... to check for multiple tagids (combined with `OR` by default, with `AND` if and=true) (since 5.6)

* **property**

   property (or relative path to property) to look at (default &quot; `cq:tags`&quot;)

### tagsearch {#tagsearch}

Sucht nach Inhalten mit Tags, indem Suchbegriffe angegeben werden. Hierbei wird zunächst nach Tags gesucht, die diese Suchbegriffe in ihrem Titel enthalten, worauf das Ergebnis auf Elemente mit diesen Tags eingeschränkt wird.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#Properties-1}

* **tagsearch**

   Suchbegriff, nach dem in Tag-Titeln gesucht werden soll

* **property**

   property (or relative path to property) to look at (default &quot; `cq:tags`&quot;)

* **lang**

   to search in a certain localized tag title only (e.g. &quot; `de`&quot;)

* **all**

   (bool) den gesamten Tag Volltext durchsuchen, d.h. alle Titel, Beschreibung usw. (hat Vorrang vor &quot;l `ang`&quot;)

### Typ {#type}

Schränkt Ergebnisse auf einen bestimmten JCR-Knotentyp ein, sowohl den primären Knotentyp als auch den Mixin-Typ. Hierbei werden auch Untertypen dieses Knotentyps gefunden. Zur effizienten Ausführung müssen Repository-Suchindizes die Knotentypen enthalten.

Unterstützt die Facettenextraktion. Stellt für jeden einzigartigen Typ in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#Properties-2}

* **type**

   node type or mixin name to search for, for example `cq:Page`