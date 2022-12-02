---
title: Query Builder-Prädikatsreferenz
seo-title: Query Builder Predicate Reference
description: Vollständiger Prädikatsverweis für die Query Builder-API.
seo-description: Complete predicate reference for the Query Builder API.
uuid: af0e269e-7d52-4032-b22e-801c7b5dccfa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
discoiquuid: 94a05894-743a-4ace-a292-bfee90ba9068
exl-id: 54b942f9-5dd9-4826-9a0a-028f2d7b8e41
source-git-commit: f97eb2e028263016131b0c86be5a0508ae4def9b
workflow-type: tm+mt
source-wordcount: '2371'
ht-degree: 98%

---

# Query Builder-Prädikatsreferenz{#query-builder-predicate-reference}

>[!CAUTION]
>
>Die Informationen auf dieser Seite sind nicht vollständig.
>
>Umfassende Informationen finden Sie in der Liste unter **Verfügbare Prädikate** in der Query Builder-Debugger-Konsole; Beispiel: unter:
>* [http://localhost:4502/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)
>
>Ein Beispiel finden Sie unter:
>
>* [http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29](http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29)


## Allgemein {#general}

* [root](#root)
* [group](#group)
* [orderby](#orderby)

## Prädikate {#predicates}

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
* [Typ](/help/sites-developing/querybuilder-predicate-reference.md#type)

### boolproperty {#boolproperty}

Sucht nach JCR BOOLEAN-Eigenschaften. Akzeptiert nur die Werte „`true`“ und „`false`“. Im Fall von „`false`“ besteht eine Übereinstimmung, falls die Eigenschaft über den Wert „`false`“ verfügt oder überhaupt nicht vorhanden ist. Dies kann für die Prüfung auf boolesche Flags nützlich sein, die nur festgelegt werden, wenn sie aktiviert sind.

Der übernommene Parameter „`operation`“ hat keine Bedeutung.

Unterstützt die Facettenextraktion. Erstellt für jeden Wert (`true` oder `false`) einen Bucket, aber nur für vorhandene Eigenschaften.

#### Eigenschaften {#properties}

* **boolproperty**
relativer Pfad der Eigenschaft, z. B. 
`myFeatureEnabled` oder `jcr:content/myFeatureEnabled`

* **value**
Wert, auf den die Eigenschaft geprüft werden soll, „ 
`true`“ oder „`false`“

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

   Pfad zur Eigenschaft mit dem ersten Datum

* **property2**

   Pfad zur Eigenschaft mit dem zweiten Datum

* **operation**

   „`equals`“ für genaue Übereinstimmung, „`!=`“ für unterschiedliche Werte, „`greater`“, wenn property1 größer ist als property2, „`>=`“, wenn property1 größer oder gleich property2 ist. Der Standardwert lautet „`equals`“.

### daterange {#daterange}

Gleicht JCR DATE-Eigenschaften mit einem Datums-/Zeitintervall ab. Hierbei wird das ISO8601-Format für Daten und Uhrzeiten (`YYYY-MM-DDTHH:mm:ss.SSSZ`) verwendet, wobei auch Teildarstellungen möglich sind, z. B. `YYYY-MM-DD`. Alternativ kann der Zeitstempel als Anzahl von Millisekunden seit 1970 in der Zeitzone UTC angegeben werden. Dies ist das Unix-Zeitformat.

Sie können nach allen Elementen zwischen zwei Zeitstempeln suchen, nach allem, was neuer oder älter als ein jeweiliges Datum ist, und aus inklusiven oder offenen Intervallen auswählen.

Unterstützt die Facettenextraktion. Stellt die Buckets „Heute“, „Diese Woche“, „Dieser Monat“, „Letzte 3 Monate“, „Dieses Jahr“, „Letztes Jahr“ und „Vor letztem Jahr“ zur Verfügung.

Filtern wird nicht unterstützt.

#### Eigenschaften {#properties-3}

* **property**

   Relativer Pfad zu einer `DATE`-Eigenschaft, z. B. `jcr:lastModified`

* **lowerBound**

   Untere Datumsgrenze, auf welche die Eigenschaft überprüft werden soll, z. B. `2014-10-01`

* **lowerOperation**

   „`>`“ (neuer) oder „`>=`“ (gleich alt oder neuer), gilt für `lowerBound`. Der Standardwert lautet „`>`“.

* **upperBound**

   Obere Datumsgrenze, auf welche die Eigenschaft überprüft werden soll, z. B. `2014-10-01T12:15:00`

* **upperOperation**

   „`<`“ (älter) oder „`<=`“ (gleich alt oder älter), gilt für `upperBound`. Der Standardwert lautet „`<`“.

* **timeZone**

   Kennung der Zeitzone, die verwendet werden soll, wenn keine ISO-8601-Datumszeichenfolge angegeben wird. Der Standardwert ist die standardmäßige Zeitzone des Systems.

### excludepaths {#excludepaths}

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

   Die Begriffe für die Volltextsuche

* **relPath**

   Der relative Pfad, der in der Eigenschaft oder dem Teilknoten durchsucht werden soll. Diese Eigenschaft ist optional.

### Gruppe {#group}

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

Hierbei wird nach dem Begriff „**Management**“ innerhalb von Seiten in `/content/geometrixx/en` oder in Assets in `/content/dam/geometrixx` gesucht.

Dies ist konzeptionell `fulltext AND ( (path AND type) OR (path AND type) )`. Beachten Sie, dass solche ODER-Verknüpfungen gute Indizes benötigen, um optimale Leistung zu bieten.

#### Eigenschaften {#properties-6}

* **p.or**

   Ist hierfür „`true`“ festgelegt, muss nur ein Prädikat in der Gruppe übereinstimmen. Standardmäßig ist „`false`“ festgelegt, was bedeutet, dass alle übereinstimmen müssen.

* **p.not**

   Ist hierfür „`true`“ festgelegt, wird die Gruppe nicht beachtet (standardmäßig „`false`“).

* **&lt;predicate>**

   Fügt verschachtelte Prädikate hinzu.

* **N_&lt;predicate>**

   Fügt mehrere verschachtelte Prädikate gleichzeitig hinzu, z. B. `1_property, 2_property, ...`.

### hasPermission {#haspermission}

Beschränkt das Ergebnis auf Elemente, bei denen die aktuelle Sitzung die angegebenen [JCR-Privilegien](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) aufweist.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-7}

* **hasPermission**

   Kommagetrennte JCR, die die aktuelle Benutzersitzung für den jeweiligen Knoten ALLE aufweisen muss, z. B. `jcr:write`, `jcr:modifyAccessControl`.

### language {#language}

Findet CQ-Seiten in einer bestimmten Sprache. Hierbei wird sowohl die Spracheigenschaft der Seite als auch der Seitenpfad betrachtet, der häufig die Sprache oder das Gebietsschema in einer Site-Struktur der höchsten Ebene enthält.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Unterstützt die Facettenextraktion. Stellt Buckets für jeden eindeutigen Sprachcode zur Verfügung.

#### Eigenschaften {#properties-8}

* **language**

   ISO-Sprach-Code, z. B „`de`“

### mainasset {#mainasset}

Prüft, ob ein Knoten ein DAM-Haupt-Asset und kein Unter-Asset ist. Dies ist im Allgemeinen jeder Knoten, der sich nicht in einem subassets-Knoten befindet. Hierbei wird nicht auf den Knotentyp `dam:Asset` geprüft. Legen Sie einfach „`mainasset=true`“ oder „`mainasset=false`“ fest, um dieses Prädikat zu verwenden, es gibt keine weiteren Eigenschaften.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Unterstützt die Facettenextraktion. Stellt zwei Buckets für Haupt- und Unter-Assets bereit.

#### Eigenschaften {#properties-9}

* **mainasset**

   Boolescher Wert, „`true`“ für Haupt-Assets, „`false`“ für Unter-Assets

### memberOf {#memberof}

Sucht Objekte, die Mitglieder einer bestimmten [Sling-Ressourcensammlung](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) sind.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-10}

* **memberOf**

   Pfad der Sling-Ressourcensammlung

### nodename {#nodename}

Sucht nach Namen von JCR-Knoten.

Unterstützt die Facettenextraktion. Stellt Buckets für alle eindeutigen Knotennamen (Dateinamen) zur Verfügung.

#### Eigenschaften {#properties-11}

* **nodename**

   Knotennamenmuster, das Platzhalter ermöglicht: `*` = beliebiges oder kein Zeichen, `?` = beliebiges Zeichen, `[abc]` = nur die Zeichen in den eckigen Klammern.

### notexpired {#notexpired}

Wertet Elemente aus, indem überprüft wird, ob eine JCR DATE-Eigenschaft größer oder gleich der aktuellen Serverzeit ist. Dies kann verwendet werden, um eine Datumseigenschaft wie „`expiresAt`“ zu überprüfen und das Ergebnis auf diejenigen zu beschränken, die noch nicht abgelaufen sind (`notexpired=true`) bzw. bereits abgelaufen sind ( `notexpired=false`).

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat „daterange“.

#### Eigenschaften {#properties-12}

* **notexpired**

   Boolescher Wert, „`true`“ für noch nicht abgelaufen (Datum in der Zukunft oder gleich), „`false`“ für abgelaufen (Datum in der Vergangenheit) (erforderlich)

* **property**

   Relativer Pfad zur zu überprüfenden `DATE`-Eigenschaft (erforderlich)

### orderby {#orderby}

Ermöglicht das Sortieren des Ergebnisses. Wenn nach mehreren Eigenschaften geordnet werden muss, muss dieses Prädikat anhand des Präfix mehrfach hinzugefügt werden, z. B. `1_orderby=first`, `2_oderby=second`.

#### Eigenschaften {#properties-13}

* **orderby**

   Entweder der JCR-Eigenschaftsname, angezeigt durch ein vorangestelltes „@“, z. B. `@jcr:lastModified` bzw. `@jcr:content/jcr:title`, oder ein anderes Prädikat in der Abfrage, z. B. `2_property`, nach dem sortiert werden soll.

* **sortieren**

   Sortierrichtung, entweder „`desc`“ für absteigend oder „`asc`“ für aufsteigend (Standard)

* **case**

    Wird hierfür „`ignore`“ festgelegt, wird die Groß-/Kleinschreibung nicht beachtet, „a“ kommt also vor „B“. Wird dies leer- oder ausgelassen, wird bei der Sortierung die Groß-/Kleinschreibung beachtet, „B“ kommt also vor „a“.

### path {#path}

Sucht innerhalb eines gegebene Pfads.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-14}

* **path**

   Pfadmuster; hängt von „exact“ ab, entweder stimmt eine gesamter Teilbaumstruktur überein (wie wenn in xpath `//*` angehängt wird, wobei dabei der Basispfad nicht mit eingeschlossen wird) (exact=false, Standardwert) oder nur ein exakter Pfad stimmt überein, der Platzhalter („`*`*) enthalten kann. Ist „self“ festgelegt, wird die gesamte Teilbaumstruktur durchsucht.

* **exact**

   Wenn für `exact` „true“ aktiviert ist, muss der exakte Pfad übereinstimmen, darf aber bestimmte einfache Platzhalter (`*`) enthalten, die Namen entsprechen, aber nicht „`/`“. Wenn die Option „false“ ist (Standard), werden alle untergeordneten Elemente berücksichtigt (optional).

* **flat**

   Durchsucht nur die direkt untergeordneten Elemente (wie wenn in xpath „`/*`*“ angehängt wird). Wird nur verwendet, wenn „`exact`“ nicht „true“ ist (optional).

* **self**

   Durchsucht den Teilbaum aber bezieht den als Pfad angegebenen Basisknoten mit ein (keine Platzhalter)

### property {#property}

Sucht nach JCR-Eigenschaften und ihren Werten.

Unterstützt die Facettenextraktion. Stellt für jeden eindeutigen Eigenschaftswert in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#properties-15}

* **property**

   relativer Pfad der Eigenschaft, z. B. `jcr:title`

* **value**

    Wert, auf den die Eigenschaft überprüft werden soll. Verarbeitet Umwandlungen anhand des JCR-Eigenschaftstyps als Zeichenfolgen.

* **N_value**

   Verwenden Sie `1_value`, `2_value`, ..., um auf mehrere Werte zu prüfen (standardmäßig kombiniert mit `OR`, wenn and=„true“, dann mit `AND`) (seit 5.3)

* **und**

   Legen Sie hierfür „true“ fest, um mehrere Werte (`N_value`) mit UND zu kombinieren (seit 5.3)

* **operation**

   „`equals`“ für exakte Übereinstimmung (Standard), „`unequals`“ für unterschiedliche Werte, „`like`“ zur Verwendung der `jcr:like`-xpath-Funktion (optional), „`not`“ für keine Übereinstimmung (z. B. „`not(@prop)`“ in xpath, „value param“ wird ignoriert) oder „`exists`“ für Prüfung der Existenz (Wert kann „true“ sein – Eigenschaft muss vorhanden sein, der Standardwert – oder „false“ – entspricht „`not`“)

* **Tiefe**

   Anzahl der Platzhalterebenen, unter denen die Eigenschaft / der relative Pfad vorhanden sein kann (z. B. `property=size depth=2` überprüft Knoten/Größe, Knoten/&amp;ast;/Größe und Knoten/&amp;ast;/&amp;ast;/Größe).

### rangeproperty {#rangeproperty}

Ordnet eine JCR-Eigenschaft einem Intervall zu. Dies gilt für Eigenschaften mit linearen Typen wie `LONG`, `DOUBLE` und `DECIMAL`. Details zu `DATE` finden Sie im Abschnitt zum Prädikat „daterange“, das für Eingaben im Datumsformat optimiert wurde.

Sie können eine untere Grenze und eine obere Grenze oder nur eine von ihnen definieren. Der Vorgang (z. B. „lesser than“ oder „lesser or equals“) kann auch einzeln für die untere und obere Grenze festgelegt werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-16}

* **property**

   Relativer Pfad zur Eigenschaft

* **lowerBound**

   Untergrenze, auf welche „property“ überprüft werden soll

* **lowerOperation**

   „`>`“ (Standard) oder „`>=`“, gilt für den `lowerValue`

* **upperBound**

   Obergrenze, auf welche „property“ überprüft werden soll

* **upperOperation**

   „`<`“ (Standard) oder „`<=`“, gilt für den `lowerValue`

* **decimal**

    „`true`“, wenn die aktivierte Eigenschaft vom Typ „Decimal“ ist.

### relativedaterange {#relativedaterange}

Gleicht `JCR DATE`-Eigenschaften anhand von Zeit-Offsets, die relativ zur aktuellen Serverzeit sind, mit einem Datums-/Zeitintervall ab. Sie können `lowerBound` und `upperBound` entweder anhand eines Millisekundenwerts oder der bugzilla-Syntax `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) angeben. Mit dem Präfix „`-`“ geben Sie einen negativen Offset vor der aktuellen Zeit an. Wenn Sie nur `lowerBound` oder `upperBound` angeben, wird für die jeweils andere Grenze standardmäßig „0“ festgelegt, was die aktuelle Zeit bedeutet.

Beispiel:

* `upperBound=1h` (und keine `lowerBound`) wählt alles in der folgenden Stunde aus.
* `lowerBound=-1d` (und keine `upperBound`) wählt alles in den vergangenen 24 Stunden aus.
* `lowerBound=-6M` und `upperBound=-3M` wählt alles aus, was zwischen sechs und drei Monaten alt ist.
* `lowerBound=-1500` und `upperBound=5500` wählt alles aus, was im Zeitraum zwischen einschließlich 1500 Millisekunden in der Vergangenheit und einschließlich 5500 Millisekunden in der Zukunft liegt. 
* `lowerBound=1d` und `upperBound=2d` wählt alles am übernächsten Tag aus.

Hinweis: Schaltjahre werden nicht berücksichtigt und alle Monate haben 30 Tage.

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat „daterange“.

#### Eigenschaften {#properties-17}

* **upperBound**

   Obere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) relativ zur aktuellen Serverzeit. Verwenden Sie „-“ für einen negativen Offset.

* **lowerBound**

   Untere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) relativ zur aktuellen Serverzeit. Verwenden Sie „-“ für einen negativen Offset.

### root {#root}

Stammprädikatgruppe. Unterstützt alle Eigenschaften einer Gruppe und ermöglicht das Festlegen globaler Abfrage-Parameter.

Der Name „root“ wird in Abfragen nie verwendet, er ist impliziert.

#### Eigenschaften {#properties-18}

* **p.offset**

    Zahl, die den Anfang der Ergebnisseite anzeigt, d. h. wie viele Elemente übersprungen werden sollen.

* **p.limit**

   Zahl, die die Seitengröße anzeigt.

* **p.guessTotal**

   Empfohlen: Vermeiden Sie die Berechnung des vollständigen Ergebnisses, da dies aufwendig sein kann. Entweder ein Maximalwert, bis zu dem gezählt werden soll (z. B. 1000, eine Zahl, die Benutzern ausreichendes Feedback zur groben Größe und exakte Zahlen bei kleineren Ergebnissen liefert) oder „`true`“, um nur bis zum kleinsten notwendigen `p.offset` + `p.limit` zu zählen.

* **p.excerpt**

   Ist hierfür „`true`“ festgelegt, wird im ein Volltextauszug eingeschlossen.

* **p.hits**

    (nur für das JSON-Servlet) Legt fest, wie Treffer als JSON geschrieben werden. Folgende Standardmethoden stehen zur Auswahl (erweiterbar über den Dienst „ResultHitWriter“):

   * **einfach**:

      Minimale Elemente wie `path`, `title`, `lastmodified`, `excerpt` (falls festgelegt)

   * **vollständig**:

      Sling-JSON-Rendering des Knotens, wobei `jcr:path` den Pfad des Treffers anzeigt: Standardmäßig werden nur die direkten Eigenschaften des Knotens aufgeführt, weiter unten befindliche Teilbäume werden mit `p.nodedepth=N` eingeschlossen, wobei 0 den vollständigen Teilbaum bedeutet. Fügen Sie `p.acls=true` hinzu, um die JCR-Berechtigungen der aktuellen Sitzung für das jeweilige Ergebniselement einzuschließen (Zuordnungen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).

   * **selektiv**:

      Nur in `p.properties` angegebene Eigenschaften. Dies ist eine mit Leerzeichen getrennte (verwenden Sie „+“ in URLs) Liste relativer Pfade. Wenn der relative Pfad eine Tiefe >1 aufweist, werden sie als untergeordnete Elemente angezeigt. Die spezielle Eigenschaft „jcr:path“ umfasst den Pfad des Treffers.

### savedquery {#savedquery}

Fügt alle Prädikate einer beständigen querybuilder-Abfrage der aktuellen Abfrage als Untergruppenprädikat hinzu.

Dabei wird keine zusätzliche Abfrage ausgeführt, sondern die aktuellen Abfrage erweitert.

Abfragen können programmgesteuert anhand von `QueryBuilder#storeQuery()` beibehalten werden. Das Format kann entweder eine String-Eigenschaft mit mehreren Zeilen oder ein `nt:file`-Knoten sein, der die Abfrage als Textdatei im Java-Eigenschaftsformat enthält.

Die Facettenextraktion wird für die Prädikate der gespeicherten Abfrage nicht unterstützt 

#### Eigenschaften {#properties-19}

* **savedquery**

   Pfad zur gespeicherten Abfrage (String-Eigenschaft oder `nt:file`-Knoten)

### similar {#similar}

Ähnlichkeitssuche mithilfe der `rep:similar()` () von JCR XPath.

Filtern wird nicht unterstützt. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-20}

* **similar** Absoluter Pfad zum Knoten, für den ähnliche Knoten gefunden werden sollen.

* **local**
ein relativer Pfad zu einem untergeordneten Knoten oder 
`.` für den aktuellen Knoten (optional, Standard ist „`.`“)

### Tag {#tag}

Sucht nach Inhalten mit Tags, indem Tag-Titelpfade angegeben werden.

Unterstützt die Facettenextraktion. Stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils der aktuelle Tag-Titelpfad verwendet.

#### Eigenschaften {#properties-21}

* **tag**

    Tag-Titelpfad, nach dem gesucht werden soll, z. B. „Asset-Eigenschaften: Ausrichtung/Querformat“

* **N_value**

   Verwenden Sie `1_value`, `2_value`, ..., um auf mehrere Tags zu prüfen (standardmäßig kombiniert mit `OR`, wenn and=„true“, dann mit `AND`) (seit 5.6)

* **property**

   Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die betrachtet werden soll (Standard: „`cq:tags`“)

### tagid {#tagid}

Sucht nach Inhalten mit Tags, indem Tag-IDs angegeben werden.

Unterstützt die Facettenextraktion. Stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils der aktuelle Tag-ID verwendet.

#### Eigenschaften {#properties-22}

* **tagid**

   Tag-ID, nach der gesucht werden soll, z. B. „`properties:orientation/landscape`“

* **N_value**

   Verwenden Sie `1_value`, `2_value`, ..., um auf mehrere tagid zu prüfen (standardmäßig kombiniert mit `OR`, wenn and=„true“, dann mit `AND`) (seit 5.6)

* **property**

   Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die betrachtet werden soll (Standard: „`cq:tags`“)

### tagsearch {#tagsearch}

Sucht nach Inhalten mit Tags, indem Suchbegriffe angegeben werden. Hierbei wird zunächst nach Tags gesucht, die diese Suchbegriffe in ihrem Titel enthalten, worauf das Ergebnis auf Elemente mit diesen Tags eingeschränkt wird.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#Properties-1}

* **tagsearch**

   Suchbegriff, nach dem in Tag-Titeln gesucht werden soll

* **property**

   Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die betrachtet werden soll (Standard: „`cq:tags`“)

* **lang**

   Zum Suchen in einem bestimmten lokalisierten Tag-Titel (z. B. „`de`“)

* **all**

   (bool) den gesamten Tag-Volltext durchsuchen, d. h. alle Titel, Beschreibungen usw. (hat Priorität vor „l `ang`“).

### Typ {#type}

Schränkt Ergebnisse auf einen bestimmten JCR-Knotentyp ein, sowohl den primären Knotentyp als auch den Mixin-Typ. Hierbei werden auch Untertypen dieses Knotentyps gefunden. Zur effizienten Ausführung müssen Repository-Suchindizes die Knotentypen enthalten.

Unterstützt die Facettenextraktion. Stellt für jeden einzigartigen Typ in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#Properties-2}

* **Typ**

   Knotentyp bzw. Mixin-Name, nach dem gesucht werden soll, z. B. `cq:Page`
