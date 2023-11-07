---
title: Query Builder-Prädikatsreferenz
description: Vollständiger Prädikatsverweis für die Query Builder-API.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
exl-id: 54b942f9-5dd9-4826-9a0a-028f2d7b8e41
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '2347'
ht-degree: 32%

---

# Query Builder-Prädikatsreferenz{#query-builder-predicate-reference}

>[!CAUTION]
>
>Die Informationen auf dieser Seite erheben keinen Anspruch auf Vollständigkeit.
>
>Umfassende Informationen finden Sie in der Liste unter **Verfügbare Eigenschaften** in der Debugger-Konsole von Query Builder, zum Beispiel unter:
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

Sucht nach JCR BOOLEAN-Eigenschaften. Akzeptiert nur die Werte „`true`“ und „`false`“. Wenn `false`&quot;, stimmt sie überein, wenn die Eigenschaft den Wert &quot; `false`&quot; oder wenn es überhaupt nicht existiert. Dies kann für die Prüfung auf boolesche Flags nützlich sein, die nur festgelegt werden, wenn sie aktiviert sind.

Der übernommene Parameter „`operation`“ hat keine Bedeutung.

Unterstützt die Facettenextraktion. Enthält Behälter für jeden `true` oder `false` -Wert, jedoch nur für vorhandene Eigenschaften.

#### Eigenschaften {#properties}

* **boolproperty**
Relativer Pfad zur Eigenschaft, z. B. `myFeatureEnabled` oder `jcr:content/myFeatureEnabled`.

* **value**
Wert, für den die Eigenschaft geprüft werden soll: &quot; `true`&quot; oder &quot; `false`&quot;.

### contentfragment {#contentfragment}

Beschränkt das Ergebnis auf Inhaltsfragmente.

Filterung wird nicht unterstützt.

unterstützt keine Facettenextraktion.

#### Eigenschaften {#properties-1}

* **contentfragment** Kann mit jedem Wert verwendet werden, um auf Inhaltsfragmente zu prüfen.

### dateComparison {#datecomparison}

Vergleicht zwei JCR DATE-Eigenschaften miteinander. Sie können testen, ob sie gleich, ungleich, größer oder größer/gleich sind.

Dies ist ein reines Filterprädikat und kann keinen Suchindex verwenden.

#### Eigenschaften {#properties-2}

* **property1**

  Pfad zur ersten Datumseigenschaft

* **property2**

  Pfad zur zweiten Datumseigenschaft

* **operation**

  „`equals`“ für genaue Übereinstimmung, „`!=`“ für unterschiedliche Werte, „`greater`“, wenn property1 größer ist als property2, „`>=`“, wenn property1 größer oder gleich property2 ist. Der Standardwert lautet „`equals`“.

### daterange {#daterange}

Entspricht den JCR DATE-Eigenschaften einem Datums-/Uhrzeitintervall. Hierbei wird das ISO8601-Format für Daten und Uhrzeiten (`YYYY-MM-DDTHH:mm:ss.SSSZ`) verwendet, wobei auch Teildarstellungen möglich sind, z. B. `YYYY-MM-DD`. Alternativ kann der Zeitstempel als Anzahl von Millisekunden seit 1970 in der UTC-Zeitzone, dem UNIX®-Zeitformat, angegeben werden.

Sie können nach allen Elementen zwischen zwei Zeitstempeln suchen, nach allem, was neuer oder älter als ein jeweiliges Datum ist, und aus inklusiven oder offenen Intervallen auswählen.

Unterstützt die Facettenextraktion. Stellt die Behälter &quot;Heute&quot;, &quot;Diese Woche&quot;, &quot;diesen Monat&quot;, &quot;Letzte 3 Monate&quot;, &quot;Dieses Jahr&quot;, &quot;Letztes Jahr&quot;und &quot;Vor dem letzten Jahr&quot;bereit.

Filterung wird nicht unterstützt.

#### Eigenschaften {#properties-3}

* **property**

  Relativer Pfad zu einem `DATE` -Eigenschaft, beispielsweise `jcr:lastModified`.

* **lowerBound**

  Untere Datumsgrenze, für die die Eigenschaft geprüft werden soll, beispielsweise `2014-10-01`.

* **lowerOperation**

  „`>`“ (neuer) oder „`>=`“ (gleich alt oder neuer), gilt für `lowerBound`. Der Standardwert lautet „`>`“.

* **upperBound**

  Obere Grenze, für die die Eigenschaft geprüft werden soll, beispielsweise `2014-10-01T12:15:00`.

* **upperOperation**

  „`<`“ (älter) oder „`<=`“ (gleich alt oder älter), gilt für `upperBound`. Der Standardwert lautet „`<`“.

* **timeZone**

  Kennung der Zeitzone, die verwendet werden soll, wenn keine ISO-8601-Datumszeichenfolge angegeben wird. Der Standardwert ist die standardmäßige Zeitzone des Systems.

### excludepaths {#excludepaths}

Schließt Knoten aus dem Ergebnis aus, deren Pfad mit einem regulären Ausdruck übereinstimmt.

Dies ist ein reines Filterprädikat und kann keinen Suchindex verwenden.

unterstützt keine Facettenextraktion.

#### Eigenschaften {#properties-4}

* **excludepaths**

  Regulärer Ausdruck, der mit Ergebnispfaden abgeglichen wird, ohne übereinstimmende aus dem Ergebnis.

### fulltext {#fulltext}

Sucht nach Ausdrücken im Volltextindex.

Filterung wird nicht unterstützt.

unterstützt keine Facettenextraktion.

#### Eigenschaften {#properties-5}

* **fulltext**

  Die Volltext-Suchbegriffe.

* **relPath**

  Der relative Pfad, der in der Eigenschaft oder dem Unterknoten durchsucht werden soll. Diese Eigenschaft ist optional.

### group {#group}

Ermöglicht die Erstellung verschachtelter Bedingungen. Gruppen können verschachtelte Gruppen enthalten. Alle Elemente in einer Abfrage von Query Builder befinden sich implizit in einer Stammgruppe, die `p.or` und `p.not` -Parameter.

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

Dies ist konzeptionell `fulltext AND ( (path AND type) OR (path AND type) )`. Solche ODER-Verknüpfungen benötigen gute Indizes für die Leistung.

#### Eigenschaften {#properties-6}

* **p.or**

  Wenn auf &quot; `true`&quot;, muss nur ein Prädikat in der Gruppe übereinstimmen. Standardmäßig ist „`false`“ festgelegt, was bedeutet, dass alle übereinstimmen müssen.

* **p.not**

  Wenn auf &quot; `true`&quot;, wird die Gruppe umgekehrt (standardmäßig &quot; `false`&quot;).

* **&lt;predicate>**

  Fügt verschachtelte Eigenschaften hinzu.

* **N_&lt;predicate>**

  Fügt mehrere verschachtelte Eigenschaften gleichzeitig hinzu, z. B. `1_property, 2_property, ...`.

### hasPermission {#haspermission}

Beschränkt das Ergebnis auf Elemente, bei denen die aktuelle Sitzung die angegebenen [JCR-Privilegien](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) aufweist.

Dies ist ein reines Filterprädikat und kann keinen Suchindex verwenden. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-7}

* **hasPermission**

  Kommagetrennte JCR-Berechtigungen, die die aktuelle Benutzersitzung ALLE über den betreffenden Knoten verfügen muss. Beispiel, `jcr:write`, `jcr:modifyAccessControl`.

### language {#language}

Findet CQ-Seiten in einer bestimmten Sprache. Dabei werden sowohl die Spracheigenschaft der Seite als auch der Seitenpfad untersucht, der häufig die Sprache oder das Gebietsschema in einer Site-Struktur der obersten Ebene enthält.

Dies ist ein reines Filterprädikat und kann keinen Suchindex verwenden.

Unterstützt die Facettenextraktion. Enthält Behälter für jeden eindeutigen Sprachcode.

#### Eigenschaften {#properties-8}

* **language**

  ISO-Sprachcode, z. B. &quot;`de`&quot;

### mainasset {#mainasset}

Überprüft, ob ein Knoten ein DAM-Haupt-Asset und kein Teil-Asset ist. Dies ist im Grunde jeder Knoten, der sich nicht in einem &quot;subassets&quot;-Knoten befindet. Dadurch wird nicht auf die `dam:Asset` Knotentyp. Um diese Eigenschaft zu verwenden, setzen Sie &quot; `mainasset=true`&quot; oder &quot; `mainasset=false`&quot;, gibt es keine weiteren Eigenschaften.

Dies ist ein reines Filterprädikat und kann keinen Suchindex verwenden.

Unterstützt die Facettenextraktion und bietet zwei Behälter für Haupt- und Unter-Assets.

#### Eigenschaften {#properties-9}

* **mainasset**

  Boolean, &quot; `true`&quot; für Haupt-Assets, &quot; `false`&quot; für Teil-Assets.

### memberOf {#memberof}

Findet Elemente, die Mitglied eines bestimmten [Sling-Ressourcenkollektion](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/org/apache/sling/resource/collection/ResourceCollection.html).

Dies ist ein reines Filterprädikat und kann keinen Suchindex verwenden. unterstützt keine Facettenextraktion.

#### Eigenschaften {#properties-10}

* **memberOf**

  Pfad der Sling-Ressourcenerfassung.

### nodename {#nodename}

Sucht nach JCR-Knotennamen.

Unterstützt die Facettenextraktion. Stellt Behälter für jeden eindeutigen Knotennamen (Dateinamen) bereit.

#### Eigenschaften {#properties-11}

* **nodename**

  Knotennamenmuster, das Platzhalter ermöglicht: `*` = beliebiges oder kein Zeichen, `?` = beliebige Zeichen, `[abc]` = nur Zeichen in Klammern.

### notexpired {#notexpired}

Sucht nach Elementen, indem überprüft wird, ob eine JCR DATE-Eigenschaft größer oder gleich der aktuellen Serverzeit ist. Dies kann verwendet werden, um eine Datumseigenschaft wie „`expiresAt`“ zu überprüfen und das Ergebnis auf diejenigen zu beschränken, die noch nicht abgelaufen sind (`notexpired=true`) bzw. bereits abgelaufen sind ( `notexpired=false`).

Filterung wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat „daterange“.

#### Eigenschaften {#properties-12}

* **notexpired**

  Boolean, &quot; `true`&quot; für noch nicht abgelaufen (Datum in der Zukunft oder gleich), &quot; `false`&quot;für abgelaufen (Datum in der Vergangenheit) (erforderlich).

* **property**

  Relativer Pfad zum `DATE` zu prüfende Eigenschaft (erforderlich).

### orderby {#orderby}

Die Ergebnisse können sortiert werden. Wenn nach mehreren Eigenschaften sortiert werden muss, muss dieses Prädikat unter Verwendung des numerischen Präfixes mehrfach hinzugefügt werden, z. B. `1_orderby=first`, `2_oderby=second`.

#### Eigenschaften {#properties-13}

* **orderby**

  Entweder der Name der JCR-Eigenschaft, der durch ein vorangestelltes @ angegeben wird, z. B. `@jcr:lastModified` oder `@jcr:content/jcr:title`oder einer anderen Eigenschaft in der Abfrage, z. B. `2_property`, nach dem sortiert werden soll.

* **sortieren**

  Sortierrichtung, entweder &quot; `desc`&quot; für absteigende oder &quot; `asc`&quot; für aufsteigende Werte (Standard).

* **case**

  Wenn auf `ignore`, wird bei der Sortierung nicht zwischen Groß- und Kleinschreibung unterschieden, d. h. &quot;a&quot;kommt vor &quot;B&quot;. Wenn leer oder ausgeschlossen, wird bei der Sortierung zwischen Groß- und Kleinschreibung unterschieden, d. h. &quot;B&quot;kommt vor &quot;a&quot;

### path {#path}

Sucht innerhalb eines angegebenen Pfads.

unterstützt keine Facettenextraktion.

#### Eigenschaften {#properties-14}

* **path**

  Pfadmuster. Je nach genauem Ergebnis stimmt entweder die gesamte Unterstruktur überein (z. B. anhängen `//*` in xpath, aber beachten Sie, dass dies nicht den Basispfad enthält (exact=false, Standard) oder nur eine exakte Pfadübereinstimmung, die Platzhalter ( `*`); wenn &quot;self&quot;festgelegt ist, wird die gesamte Unterstruktur einschließlich des Basisknotens durchsucht.

* **exact**

  Wenn `exact` auf &quot;true/on&quot;festgelegt ist, muss der genaue Pfad übereinstimmen, er kann jedoch einfache Platzhalterzeichen ( `*`), die mit Namen übereinstimmen, aber nicht &quot; `/`&quot;; wenn false (Standard) ist, werden alle untergeordneten Elemente einbezogen (optional).

* **flat**

  Sucht nur die direkten untergeordneten Elemente (wie angehängt &quot; `/*`&quot; in xpath (nur verwendet, wenn &quot;) `exact`&quot; ist nicht wahr, optional).

* **self**

  Durchsucht die Unterstruktur, enthält jedoch den als Pfad angegebenen Basisknoten (keine Platzhalter).

### property {#property}

Sucht nach JCR-Eigenschaften und deren Werten.

Unterstützt die Facettenextraktion. Stellt Behälter für jeden eindeutigen Eigenschaftswert in den Ergebnissen bereit.

#### Eigenschaften {#properties-15}

* **property**

  Relativer Pfad zur Eigenschaft, z. B. `jcr:title`.

* **value**

  Wert, für den die Eigenschaft überprüft werden soll; folgt dem JCR-Eigenschaftstyp Zeichenfolgenkonvertierungen.

* **N_value**

  Verwendung `1_value`, `2_value`, um zu überprüfen, ob mehrere Werte vorliegen (kombiniert mit `OR` standardmäßig mit `AND` if und=true) (seit 5.3).

* **und**

  Auf true gesetzt für die Kombination mehrerer Werte ( `N_value`) mit UND (seit 5.3).

* **operation**

  &quot;`equals`&quot; für exakte Übereinstimmung (Standard), &quot; `unequals`&quot; für den Vergleich der Ungleichheit &quot; `like`&quot; zur Verwendung der `jcr:like` xpath-Funktion (optional), &quot; `not`&quot;für keine Übereinstimmung (z. B. &quot;`not(@prop)`&quot; in xpath, value param is ignoriert) oder &quot; `exists`&quot; für Prüfung der Existenz (Wert kann wahr sein - Eigenschaft muss vorhanden sein, der Standardwert - oder false - entspricht &quot; `not`&quot;).

* **Tiefe**

  Anzahl der Platzhalterebenen, unter denen die Eigenschaft/der relative Pfad vorhanden sein kann (z. B. `property=size depth=2` prüft Knoten/Größe, Knoten/&amp;ast;/Größe und Knoten/&amp;ast;/&amp;ast;/size).

### rangeproperty {#rangeproperty}

Entspricht einer JCR-Eigenschaft einem Intervall. Dies gilt für Eigenschaften mit linearen Typen wie `LONG`, `DOUBLE`, und `DECIMAL`. Für `DATE`, sehen Sie sich die Eigenschaft daterange an, die eine optimierte Eingabe des Datumsformats aufweist.

Sie können eine untere und eine obere Grenze oder nur eine davon definieren. Der Vorgang (z. B. &quot;kleiner als&quot;oder &quot;kleiner oder gleich&quot;) kann auch einzeln für die untere und obere Grenze angegeben werden.

unterstützt keine Facettenextraktion.

#### Eigenschaften {#properties-16}

* **property**

  Relativer Pfad zur Eigenschaft.

* **lowerBound**

  Untergrenze, auf die die Eigenschaft überprüft werden soll.

* **lowerOperation**

  „`>`“ (Standard) oder „`>=`“, gilt für den `lowerValue`

* **upperBound**

  Obergebunden zur Überprüfung der Eigenschaft.

* **upperOperation**

  „`<`“ (Standard) oder „`<=`“, gilt für den `lowerValue`

* **decimal**

   „`true`“, wenn die aktivierte Eigenschaft vom Typ „Decimal“ ist.

### relativedaterange {#relativedaterange}

Gleicht `JCR DATE`-Eigenschaften anhand von Zeit-Offsets, die relativ zur aktuellen Serverzeit sind, mit einem Datums-/Zeitintervall ab. Sie können `lowerBound` und `upperBound` entweder anhand eines Millisekundenwerts oder der bugzilla-Syntax `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) angeben. Mit dem Präfix „`-`“ geben Sie einen negativen Offset vor der aktuellen Zeit an. Wenn Sie nur `lowerBound` oder `upperBound`, der andere Standardwert ist 0, was die aktuelle Zeit bedeutet.

Beispiel:

* `upperBound=1h` (und keine `lowerBound`) wählt alles in der folgenden Stunde aus.
* `lowerBound=-1d` (und keine `upperBound`) wählt alles in den vergangenen 24 Stunden aus.
* `lowerBound=-6M` und `upperBound=-3M` wählt alles aus, was zwischen sechs und drei Monaten alt ist.
* `lowerBound=-1500` und `upperBound=5500` wählt alles aus, was im Zeitraum zwischen einschließlich 1500 Millisekunden in der Vergangenheit und einschließlich 5500 Millisekunden in der Zukunft liegt. 
* `lowerBound=1d` und `upperBound=2d` wählt alles am übernächsten Tag aus.

Schaltjahre werden nicht berücksichtigt, und alle Monate haben 30 Tage.

Filterung wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat „daterange“.

#### Eigenschaften {#properties-17}

* **upperBound**

  Obergrenze des Datums in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) im Vergleich zur aktuellen Serverzeit verwenden Sie &quot;-&quot;für einen negativen Versatz.

* **lowerBound**

  Untere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) im Vergleich zur aktuellen Serverzeit verwenden Sie &quot;-&quot;für einen negativen Versatz.

### root {#root}

Stammprädikatgruppe. Unterstützt alle Funktionen einer Gruppe und ermöglicht das Festlegen globaler Abfrageparameter.

Der Name „root“ wird in Abfragen nie verwendet, er ist impliziert.

#### Eigenschaften {#properties-18}

* **p.offset**

  Die Zahl, die den Anfang der Ergebnisseite angibt, d. h. wie viele Elemente übersprungen werden sollen.

* **p.limit**

  Die Zahl, die die Seitengröße angibt.

* **p.guessTotal**

  Empfohlen: Vermeiden Sie die Berechnung der vollständigen Ergebnissumme, die kostspielig sein kann. Entweder eine Zahl, die die maximal zu zählende Summe angibt (z. B. 1000, eine Zahl, die Benutzern genügend Feedback zur groben Größe und genauen Zahlen für kleinere Ergebnisse gibt) oder &quot; `true`&quot; nur bis zu dem erforderlichen Minimum zählen. `p.offset` + `p.limit`.

* **p.excerpt**

  Wenn auf &quot; `true`&quot;, fügen Sie einen Volltextextextrakt in das Ergebnis ein.

* **p.hits**

   (nur für das JSON-Servlet) Legt fest, wie Treffer als JSON geschrieben werden. Folgende Standardmethoden stehen zur Auswahl (erweiterbar über den Dienst „ResultHitWriter“):

   * **einfach**:

     Minimale Elemente wie `path`, `title`, `lastmodified`, `excerpt` (sofern festgelegt).

   * **vollständig**:

     Sling JSON-Rendering des Knotens mit `jcr:path` den Pfad des Treffers angeben: Standardmäßig werden nur die direkten Eigenschaften des Knotens aufgelistet. Schließen Sie einen tieferen Baum mit `p.nodedepth=N`, wobei 0 für die gesamte, unendliche Unterstruktur steht, hinzugefügt wird; `p.acls=true` , um die JCR-Berechtigungen der aktuellen Sitzung für das angegebene Ergebniselement (Zuordnungen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).

   * **selektiv**:

     Nur Eigenschaften, die in `p.properties`, wobei es sich um eine durch Leerzeichen getrennte Liste relativer Pfade handelt (verwenden Sie &quot;+&quot;in URLs). Wenn der relative Pfad eine Tiefe von > 1 aufweist, werden diese als untergeordnete Objekte dargestellt. Die spezielle Eigenschaft jcr:path enthält den Pfad des Treffers

### savedquery {#savedquery}

Enthält alle Eigenschaften einer persistenten Query Builder-Abfrage in die aktuelle Abfrage als Untergruppeneigenschaft.

Dadurch wird keine zusätzliche Abfrage ausgeführt, sondern die aktuelle Abfrage erweitert.

Abfragen können programmgesteuert anhand von `QueryBuilder#storeQuery()` beibehalten werden. Das Format kann entweder eine mehrzeilige String-Eigenschaft oder eine `nt:file` -Knoten, der die Abfrage als Textdatei im Java™-Eigenschaftenformat enthält.

Die Facettenextraktion wird für die Prädikate der gespeicherten Abfrage nicht unterstützt 

#### Eigenschaften {#properties-19}

* **savedquery**

  Pfad zur gespeicherten Abfrage (String-Eigenschaft oder `nt:file` Knoten).

### similar {#similar}

Ähnlichkeitssuche mithilfe der `rep:similar()` () von JCR XPath.

Filterung wird nicht unterstützt. unterstützt keine Facettenextraktion.

#### Eigenschaften {#properties-20}

* **similar**
Absoluter Pfad zum Knoten, für den ähnliche Knoten gefunden werden sollen.

* **lokal**
Ein relativer Pfad zu einem untergeordneten Knoten oder `.` für den aktuellen Knoten (optional, Standard ist &quot; `.`&quot;).

### tag {#tag}

Sucht nach Inhalten, die mit einem oder mehreren Tags getaggt sind, indem Tag-Titelpfade angegeben werden.

Unterstützt die Facettenextraktion. Stellt Behälter für jedes eindeutige Tag bereit, wobei der aktuelle Tag-Titelpfad verwendet wird.

#### Eigenschaften {#properties-21}

* **tag**

  Tag-Titelpfad, der nach z. B. &quot;Asset-Eigenschaften: Ausrichtung/Querformat&quot;sucht.

* **N_value**

  Verwendung `1_value`, `2_value`, ... , um nach mehreren Tags zu suchen (kombiniert mit `OR` standardmäßig mit `AND` if und=true) (seit 5.6).

* **property**

  Eigenschaft (oder relativer Pfad zur Eigenschaft), die angezeigt werden soll (Standard &quot; `cq:tags`&quot;)

### tagid {#tagid}

Sucht nach Inhalten, die mit einem oder mehreren Tags versehen sind, indem Tag-IDs angegeben werden.

Unterstützt die Facettenextraktion. Stellt Behälter für jedes eindeutige Tag bereit, wobei die aktuelle Tag-ID verwendet wird.

#### Eigenschaften {#properties-22}

* **tagid**

  Tag-ID , damit Sie z. B. nach &quot; `properties:orientation/landscape`&quot;.

* **N_value**

  Verwendung `1_value`, `2_value`, ... , um nach mehreren Tags zu suchen (kombiniert mit `OR` standardmäßig mit `AND` if und=true) (seit 5.6).

* **property**

  Eigenschaft (oder relativer Pfad zur Eigenschaft), die angezeigt werden soll (Standard &quot; `cq:tags`&quot;).

### tagsearch {#tagsearch}

Sucht nach Inhalten, die mit einem oder mehreren Tags versehen sind, indem Suchbegriffe angegeben werden. Hierbei wird zuerst nach Tags gesucht, die diese Keywords in ihren Titeln enthalten, dann wird das Ergebnis auf Elemente beschränkt, die mit diesen Keywords getaggt sind.

unterstützt keine Facettenextraktion.

#### Eigenschaften {#Properties-1}

* **tagsearch**

  Keyword, nach dem in Tag-Titeln gesucht werden soll

* **property**

  Eigenschaft (oder relativer Pfad zur Eigenschaft), die angezeigt werden soll (Standard) `cq:tags`).

* **lang**

  So suchen Sie nur in einem bestimmten lokalisierten Tag-Titel (z. B. `de`).

* **all**

  (bool) Suchen Sie den gesamten Tag-Volltext, d. h. alle Titel, Beschreibungen usw. (hat Vorrang vor &quot;l&quot;. `ang`&quot;).

### Typ {#type}

Beschränkt die Ergebnisse auf einen bestimmten JCR-Knotentyp, sowohl den primären Knotentyp als auch den Mixin-Typ. Dadurch werden auch Untertypen dieses Knotentyps gefunden. Die Indizes der Repository-Suche müssen die Knotentypen abdecken, um eine effiziente Ausführung zu gewährleisten.

Unterstützt die Facettenextraktion. Stellt Behälter für jeden eindeutigen Typ in den Ergebnissen bereit.

#### Eigenschaften {#Properties-2}

* **Typ**

  Knotentyp oder Mixin-Name, nach dem gesucht werden soll, beispielsweise `cq:Page`.
