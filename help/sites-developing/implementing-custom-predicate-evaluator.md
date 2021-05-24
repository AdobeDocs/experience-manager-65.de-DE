---
title: Implementieren eines benutzerdefinierten Prädikat-Auswerters für den Query Builder
seo-title: Implementieren eines benutzerdefinierten Prädikat-Auswerters für den Query Builder
description: Mit dem Query Builder können Sie problemlos das Inhalts-Repository abfragen.
seo-description: Mit dem Query Builder können Sie problemlos das Inhalts-Repository abfragen.
uuid: e71be518-027c-4792-9e02-06405804d9d2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: ef253905-87da-4fa2-9f6c-778f1b12bd58
docset: aem65
exl-id: 72cbe589-14a1-40f5-a7cb-8960f02e0ebb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 93%

---

# Implementieren eines benutzerdefinierten Prädikat-Auswerters für den Query Builder{#implementing-a-custom-predicate-evaluator-for-the-query-builder}

In diesem Abschnitt ist beschrieben, wie Sie den [Query Builder](/help/sites-developing/querybuilder-api.md) durch Implementieren eines benutzerdefinierten Prädikat-Auswerters erweitern können.

## Überblick {#overview}

Mit dem [Query Builder](/help/sites-developing/querybuilder-api.md) können Sie problemlos das Inhalts-Repository abfragen. Im Lieferumfang sind eine Reihe Prädikat-Auswerter enthalten, die Ihnen den Umgang mit Daten erleichtern.

Sie möchten jedoch vielleicht Abfragen vereinfachen, indem Sie einen benutzerdefinierten Prädikat-Auswerter implementieren, der weniger komplex ist und für eine bessere Semantik sorgt.

Ein benutzerdefiniertes Prädikat ist auch für andere Aufgaben nützlich, die nicht direkt mit XPath ausgeführt werden können, z. B.:

* Suchen nach Daten und Services
* Benutzerdefiniertes Filtern basierend auf Berechnungen

>[!NOTE]
>
>Beim Implementieren eines benutzerdefinierten Prädikats müssen Leistungsaspekte berücksichtigt werden.

>[!NOTE]
>
>Beispiele für Abfragen finden Sie im Abschnitt [Query Builder](/help/sites-developing/querybuilder-api.md).

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt „aem-search-custom-predicate-evaluator“ auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator).
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip) herunter.

### Prädikat-Auswerter im Detail {#predicate-evaluator-in-detail}

Ein Prädikat-Auswerter ist für die Auswertung bestimmter Prädikate zuständig, die eine Abfrage einschränken.

Dabei wird eine allgemeinere Sucheinschränkung (z. B. &quot;width > 200&quot;) einer spezifischen JCR-Abfrage zugeordnet, die mit dem tatsächlichen Inhaltsmodell übereinstimmt (z. B. metadata/@width > 200). Es können auch Knoten manuell gefiltert und deren Einschränkungen überprüft werden.

>[!NOTE]
>
>Weitere Informationen zum `PredicateEvaluator` und dem Paket `com.day.cq.search` finden Sie in der [Java-Dokumentation](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/search/package-summary.html).

### Implementieren eines benutzerdefinierten Prädikat-Auswerters für Replikationsmetadaten {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

In diesem Abschnitt wird anhand eines Beispiels beschrieben, wie Sie einen benutzerdefinierten Prädikat-Auswerter erstellen, der die Verarbeitung von Daten basierend auf Replikationsmetadaten erleichtert:

* `cq:lastReplicated` speichert die Daten der letzten Replikationsaktion.

* `cq:lastReplicatedBy` speichert die ID des Benutzers, der die letzte Replikationsaktion ausgelöst hat.

* `cq:lastReplicationAction` speichert die letzte Replikationsaktion (z. B. Aktivierung, Deaktivierung).

#### Abfragen von Replikationsmetadaten mit Standard-Prädikat-Auswertern {#querying-replication-metadata-with-default-predicate-evaluators}

Mit folgender Abfrage wird die Liste der Knoten im Zweig `/content`abgerufen, die vom Benutzer `admin` seit Jahresanfang aktiviert wurden.

```xml
path=/content

1_property=cq:lastReplicatedBy
1_property.value=admin

2_property=cq:lastReplicationAction
2_property.value=Activate

daterange.property=cq:lastReplicated
daterange.lowerBound=2013-01-01T00:00:00.000+01:00
daterange.lowerOperation=>=
```

Diese Abfrage ist zwar gültig, jedoch schwer zu lesen. Außerdem wird die Beziehung zwischen den drei Replikationseigenschaften nicht hervorgehoben. Das Implementieren eines benutzerdefinierten Prädikat-Auswerters reduziert die Komplexität und verbessert die Semantik dieser Abfrage.

#### Ziele {#objectives}

Ziel des `ReplicationPredicateEvaluator` ist die Unterstützung der obigen Abfrage durch folgende Syntax:

```xml
path=/content

replic.by=admin
replic.since=2013-01-01T00:00:00.000+01:00
replic.action=Activate
```

Das Gruppieren von Metadatenprädikaten einer Replikation mit einem benutzerdefinierten Prädikat-Auswerter erleichtert das Erstellen einer aussagekräftigen Abfrage.

#### Aktualisieren von Maven-Abhängigkeiten {#updating-maven-dependencies}

>[!NOTE]
>
>Informationen zum Einrichten neuer AEM-Projekte mit Maven finden Sie in der Dokumentation [Erstellen von AEM-Projekten mit Apache Maven](/help/sites-developing/ht-projects-maven.md).

Sie müssen zunächst die Maven-Abhängigkeiten Ihres Projekts aktualisieren. `PredicateEvaluator` ist Teil des `cq-search`-Artefakts und muss zur POM-Datei von Maven hinzugefügt werden.

>[!NOTE]
>
>Für den Bereich der Abhängigkeit `cq-search` ist `provided` festgelegt, da `cq-search` vom `OSGi`-Container bereitgestellt wird.

pom.xml

Das folgende Snippet zeigt die Unterschiede im [einheitlichen Diff-Format](https://de.wikipedia.org/wiki/Diff#Unified_format)

```
@@ -120,6 +120,12 @@
             <scope>provided</scope>
         <dependency>
+            <groupid>com.day.cq</groupid>
+            <artifactid>cq-search</artifactid>
+            <version>5.6.4</version>
+            <scope>provided</scope>
+        </dependency>
+        <dependency>
             <groupid>junit</groupid>
             <artifactid>junit</artifactid>
             <version>3.8.1</version></dependency>
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)-  [pom.xml](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/7aed6b35b4c8dd3655296e1b10cf40c0dd1eaa61/pom.xml)

#### Schreiben des Prädikat-Auswerters für eine Replikation {#writing-the-replicationpredicateevaluator}

Das `cq-search`-Projekt beinhaltet die abstrakte Klasse `AbstractPredicateEvaluator`. Diese kann in wenigen Schritten mit einem benutzerdefinierten Prädikat-Auswerter `(PredicateEvaluator`) erweitert werden.

>[!NOTE]
>
>Im folgenden Abschnitt wird erläutert, wie Sie einen `Xpath`-Ausdruck zum Filtern von Daten erstellen. Eine andere Option ist das Implementieren einer `includes`-Methode, bei der Daten auf Zeilenbasis ausgewählt werden. Weitere Informationen finden Sie in der [Java-Dokumentation](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html#includes28comdaycqsearchpredicatejavaxjcrqueryrowcomdaycqsearchevalevaluationcontext29).

1. Erstellen Sie eine neue Java-Klasse zum Erweitern von `com.day.cq.search.eval.AbstractPredicateEvaluator`
1. Kommentieren Sie Ihre Klasse mit einem `@Component` wie dem folgenden

   src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

   Das folgende Snippet zeigt die Unterschiede im [einheitlichen Diff-Format](https://en.wikipedia.org/wiki/Diff#Unified_format)

```
@@ -19,8 +19,11 @@
  */
 package com.adobe.aem.docs.search;

+import org.apache.felix.scr.annotations.Component;
+
 import com.day.cq.search.eval.AbstractPredicateEvaluator;

+@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")
 public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

 }
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator) -  [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/ec70fac35fbd0d132e00c6066a204804e9cbe70f/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)

>[!NOTE]
>
>`factory` muss eine eindeutige Zeichenfolge sein, die mit `com.day.cq.search.eval.PredicateEvaluator/` beginnt und mit dem Namen des benutzerdefinierten `PredicateEvaluator` endet.

>[!NOTE]
>
>Der Name des `PredicateEvaluator` ist der Name des Prädikats, das zum Erstellen von Abfragen verwendet wird.

1. Überschreiben:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   Bei der Überschreibmethode erstellen Sie einen `Xpath`-Ausdruck basierend auf dem im Argument angegebenen `Predicate`.

### Beispiel für einen benutzerdefinierten Prädikat-Auswerter für Replikationsmetadaten {#example-of-a-custom-predicate-evalutor-for-replication-metadata}

Die vollständige Implementierung dieses `PredicateEvaluator` kann der folgenden Klasse ähnlich sein.

src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

```
/*
 * #%L
 * aem-docs-custom-predicate-evaluator
 * %%
 * Copyright (C) 2013 Adobe Research
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */

package com.adobe.aem.docs.search;

import org.apache.felix.scr.annotations.Component;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.search.Predicate;
import com.day.cq.search.eval.AbstractPredicateEvaluator;
import com.day.cq.search.eval.EvaluationContext;

@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")

public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

    static final String PE_NAME = "replic";


    static final String PN_LAST_REPLICATED_BY = "cq:lastReplicatedBy";
    static final String PN_LAST_REPLICATED = "cq:lastReplicated";
    static final String PN_LAST_REPLICATED_ACTION = "cq:lastReplicationAction";

    static final String PREDICATE_BY = "by";
    static final String PREDICATE_SINCE = "since";
    static final String PREDICATE_SINCE_OP = " >= ";
    static final String PREDICATE_ACTION = "action";

    Logger log = LoggerFactory.getLogger(getClass());

    /**
     * Returns a XPath expression filtering by replication metadata.
     *
     * @see com.day.cq.search.eval.AbstractPredicateEvaluator#getXPathExpression(com.day.cq.search.Predicate,
     *      com.day.cq.search.eval.EvaluationContext)
     */

    @Override

    public String getXPathExpression(Predicate predicate,
            EvaluationContext context) {

        log.debug("predicate {}", predicate);

        String date = predicate.get(PREDICATE_SINCE);
        String user = predicate.get(PREDICATE_BY);
        String action = predicate.get(PREDICATE_ACTION);

        StringBuilder sb = new StringBuilder();

        if (date != null) {

            sb.append(PN_LAST_REPLICATED).append(PREDICATE_SINCE_OP);
            sb.append("xs:dateTime('").append(date).append("')");

        }

        if (user != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_BY);
            sb.append("='").append(user).append("'");

        }

        if (action != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_ACTION);
            sb.append("='").append(action).append("'");

        }

        String xpath = sb.toString();

        log.debug("xpath **{}**", xpath);

        return xpath;

    }

    /**
     * Add an and operator if the builder is not empty.
     *
     * @param sb a {@link StringBuilder} containing the query under construction
     */

    private void addAndOperator(StringBuilder sb) {

        if (sb.length() != 0) {

            sb.append(" and ");

        }

    }

}
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator) -  [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/blob/master/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)
