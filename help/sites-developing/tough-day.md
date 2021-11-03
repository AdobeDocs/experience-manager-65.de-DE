---
title: Tough Day
seo-title: Tough Day
description: Der „Tough Day“-Test simuliert die tägliche Last von rund 1.000 Autoren in einem Worst-Case-Szenario, bei dem alle Vorgänge gleichzeitig ablaufen.
seo-description: The Tough Day test simulates the daily load of around 1000 authors in a worst-case scenario with all the operations going on at the same time.
topic-tags: testing
content-type: reference
exl-id: ceb9671c-57f9-4d81-94c0-0dbccd4d90a2
source-git-commit: 36c0728908e24a13d08c1eaed4e39542f5b61df5
workflow-type: tm+mt
source-wordcount: '1885'
ht-degree: 53%

---

# Tough Day{#tough-day}

## Was ist Tough Day 2? {#what-is-tough-day}

„Tough Day 2“ ist eine Anwendung, mit der Sie einen Stresstest Ihrer AEM-Instanz durchführen können. Sie können ihn direkt mit der standardmäßigen Test-Suite ausführen oder an Ihre Testanforderungen anpassen. In [dieser Aufnahme](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-toughday2-stress-testing-benchmarking-tool.html) sehen Sie eine Präsentation der Anwendung.

>[!CAUTION]
>
>Tough Day 2 erfordert Java 8.

## Ausführen von Tough Day 2 {#how-to-run-tough-day}

Laden Sie die aktuelle Version von Tough Day 2 aus dem [Adobe-Repository](https://repo1.maven.org/maven2/com/adobe/qe/toughday2/) herunter. Nachdem Sie die Anwendung heruntergeladen haben, können Sie sie standardmäßig ausführen, indem Sie die `host` Parameter. Im folgenden Beispiel wird die AEM-Instanz lokal ausgeführt, sodass die `localhost` verwendet wird:

```xml
java -jar toughday2.jar --host=localhost
```

Die Standard-Suite, die nach dem Hinzufügen des Parameters ausgeführt wird, heißt `toughday`. Sie enthält die folgenden Anwendungsfälle:

* Erstellen von Seiten und zugehörigen Live Copies (einschließlich Rollouts)
* Abrufen der Homepage
* Ausführen von Abfragen in QueryBuilder
* Erstellen von Asset-Hierarchien
* Löschen von Assets

Die Suite enthält 15 Prozent Schreibaktionen und 85 Prozent Leseaktionen.

Um die Suite-Tests auszuführen, installiert Tough Day 2 das Standard-Inhaltspaket. Dies lässt sich vermeiden, indem Sie die `installsamplecontent`Parameter auf `false`, aber beachten Sie, dass Sie auch die Standardpfade für die Tests ändern sollten, die Sie ausführen möchten. Wenn die JAR ohne Parameter ausgeführt wird, zeigt Tough Day 2 die [Hilfeinformationen](/help/sites-developing/tough-day.md#getting-help).

Als allgemeine Regel können Sie die Anwendung verwenden, indem Sie diesem Muster folgen:

```xml
java -jar toughday2.jar [--help | --help_full | --help_tests | --help_publish]  [<global arguments> | <actions> | --runmode | --publishmode]
```

>[!NOTE]
>
>Bei Tough Day 2 gibt es keinen Bereinigungsschritt. Wir empfehlen daher, Tough Day 2 auf einer geklonten Staging-Instanz auszuführen, nicht auf der Hauptproduktionsinstanz. Die Staging-Instanz sollte nach den Tests nicht mehr genutzt werden.

### Hilfe {#getting-help}

Tough Day 2 bietet zahlreiche Hilfeoptionen, auf die Sie über die Befehlszeile zugreifen können. Beispiel:

```xml
java -jar toughday2.jar --help_full
```

In der nachfolgenden Tabelle finden Sie die relevanten Hilfeparameter.

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Beispiel</strong></td>
  </tr>
  <tr>
   <td>--help</td>
   <td>Druckt globale Informationen aus, z. B.: die verfügbaren Aktionen, vordefinierten Suites, Ausführungsmodi und globalen Parameter.</td>
   <td> </td>
  </tr>
  <tr>
   <td>—help_publish</td>
   <td>Druckt alle verfügbaren Herausgeber aus.</td>
   <td> </td>
  </tr>
  <tr>
   <td>—help_tests</td>
   <td>Druckt die Testklassen und deren Beschreibung.</td>
   <td> </td>
  </tr>
  <tr>
   <td>—help_full</td>
   <td>Druckt alle oben genannten Funktionen sowie Tests, Herausgeber und Suite-Komponenten.</td>
   <td> </td>
  </tr>
  <tr>
   <td> —help —runmode/publishmode type=&lt;mode&gt;</td>
   <td>Listet Informationen zum angegebenen Ausführungs- oder Veröffentlichungsmodus auf.</td>
   <td><p>java -jar toughday2.jar —help —runmode type=conantload</p> <p>java -jar toughday2.jar —help —publishmode type=interval</p> </td>
  </tr>
  <tr>
   <td>—help —suite=&lt;suitename&gt;</td>
   <td>Listet alle Tests einer bestimmten Suite und ihre jeweiligen konfigurierbaren Eigenschaften auf.</td>
   <td><br /> java -jar toughday2.jar —help —suite=get_tests</td>
  </tr>
  <tr>
   <td> —help —tag=&lt;tag&gt;</td>
   <td><br /> Listet alle Elemente mit dem angegebenen Tag auf.</td>
   <td>java -jar toughday2.jar —help —tag=publish</td>
  </tr>
  <tr>
   <td>—help &lt;testclass publisherclass=""&gt;</td>
   <td><br /> Listet alle konfigurierbaren Eigenschaften für den jeweiligen Test oder Herausgeber auf.</td>
   <td><p>java -jar toughday2.jar —help UploadPDFTest</p> <p>java -jar toughday2.jar —help CSVPublisher</p> </td>
  </tr>
 </tbody>
</table>

### Globale Parameter {#global-parameters}

Tough Day 2 bietet globale Parameter, die die Testumgebung festlegen oder ändern. Dazu gehören der Ziel-Host, die Portnummer, das verwendete Protokoll, Benutzer und Kennwort für die Instanz usw. Beispiel:

```xml
java -jar toughday2.jar --host=host --protocol=https --port=4502 --duration=30m --dryrun=true
```

Nachfolgend finden Sie alle relevanten Parameter:

| **Parameter** | **Beschreibung** | **Standardwert** | **Mögliche Werte** |
|---|---|---|---|
| `--installsamplecontent=<Val>` | Das standardmäßige Inhaltspaket Tough Day 2 wird entweder installiert oder übersprungen. | Ja | „true“ oder „false“ |
| `--protocol=<Val>` | Das für den Host verwendete Protokoll. | http | http oder https |
| `--host=<Val>` | Der Hostname oder die IP-Adresse, die als Ziel ausgewählt wird. |  |  |
| `--port=<Val>` | Der Anschluss des Hosts. | 4502 |  |
| `--user=<Val>` | Der Benutzername für die Instanz. | admin |  |
| `--password=<Val>` | Kennwort für den angegebenen Benutzer. | admin |  |
| `--duration=<Val>` | Dauer der Tests. Kann in (**s**)Sekunden, (**m**)Minuten, (**h**) unsere und (**d**)ays. | 1d |  |
| `--timeout=<Val>` | Gibt an, wie lange ein Test ausgeführt wird, bevor er unterbrochen und als fehlgeschlagen markiert wird. In Sekunden angegeben. | 180 |  |
| `--suite=<Val>` | Der Wert kann eine oder eine Liste (durch Kommas getrennt) vordefinierter Test-Suites sein. | touchday |  |
| `--configfile=<Val>` | Die zielgerichtete YAML-Konfigurationsdatei. |  |  |
| `--contextpath=<Val>` | Kontextpfad der Instanz. |  |  |
| `--loglevel=<Val>` | Die Protokollebene für die Tough Day 2-Engine. | INFO | ALL, DEBUG, INFO, WARN, FEHLER, FATAL, OFF |
| `--dryrun=<Val>` | Wenn &quot;true&quot;, wird die resultierende Konfiguration gedruckt und es werden keine Tests ausgeführt. | Nein | „true“ oder „false“ |

## Anpassung {#customizing}

Die Anpassung erfolgt wahlweise über Befehlszeilenparameter oder YAML-Konfigurationsdateien. **Konfigurationsdateien werden in der Regel für umfangreiche angepasste Suites verwendet. Sie überschreiben die Standardparameter von Tough Day 2. Befehlszeilenparameter überschreiben sowohl Konfigurationsdateien als auch Standardparameter.**

Die einzige Möglichkeit, eine Testkonfiguration zu speichern, besteht darin, sie in das YAML-Format zu kopieren. Weitere Informationen finden Sie in diesem [toughday.yaml](https://repo.adobe.com/nexus/service/local/repositories/releases/content/com/adobe/qe/toughday2/0.2.1/toughday2-0.2.1.yaml) Konfiguration und Beispiele für die YAML-Konfiguration in den folgenden Abschnitten.

### Hinzufügen eines neuen Tests {#adding-a-new-test}

Wenn Sie die standardmäßige `toughday`-Suite nicht verwenden möchten, können Sie mit dem Parameter `add` einen Test Ihrer Wahl hinzufügen. Die folgenden Beispiele zeigen, wie Sie den Test `CreateAssetTreeTest` mit Befehlszeilenparametern oder mit einer YAML-Konfigurationsdatei hinzufügen.

Mit Befehlszeilenparametern:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest
```

Mit einer YAML-Konfigurationsdatei:

```xml
globals:
  host : localhost
tests:
  - add : CreateAssetTreeTest
```

### Hinzufügen von mehreren Instanzen desselben Tests  {#adding-multiple-instances-of-the-same-test}

Sie können auch mehrere Instanzen desselben Tests hinzufügen und ausführen. Dabei muss jedoch jede Instanz einen eindeutigen Namen aufweisen. Die folgenden Beispiele zeigen, wie Sie zwei Instanzen desselben Tests mit Befehlszeilenparametern oder mit einer YAML-Konfigurationsdatei hinzufügen.

Mit Befehlszeilenparametern:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest name=FirstAssetTree --add CreateAssetTreeTest name=SecondAssetTree
```

Mit einer YAML-Konfigurationsdatei:

```xml
globals:
  host : localhost
tests:
  - add : CreateAssetTreeTest
    properties:
      name : FirstAssetTree
  - add : CreateAssetTreeTest
    properties:
      name : SecondAssetTree
```

### Ändern der Testeigenschaften {#changing-the-test-properties}

Wenn Sie eine Testeigenschaft (oder mehrere) ändern müssen, können Sie diese Eigenschaft(en) zur Befehlszeile oder zur YAML-Konfigurationsdatei hinzufügen. Um alle verfügbaren Testeigenschaften anzuzeigen, fügen Sie die `--help <TestClass/PublisherClass>` Parameter an die Befehlszeile an, z. B.:

```xml
java -jar toughday2.jar --help CreatePageTreeTest
```

Beachten Sie, dass die YAML-Konfigurationsdateien die Standardparameter von Tough Day 2 überschreiben und Befehlszeilenparameter sowohl die Konfigurationsdateien als auch die Standardparameter überschreiben.

Die folgenden Beispiele zeigen, wie Sie die `template` -Eigenschaft für `CreatePageTreeTest` Testen Sie entweder mithilfe von Befehlszeilenparametern oder einer YAML-Konfigurationsdatei.

Mit Befehlszeilenparametern:

```xml
java -jar toughday2.jar --host=localhost --add CreatePageTreeTest template=/conf/toughday-templates/settings/wcm/templates/toughday-template
```

Mit einer YAML-Konfigurationsdatei:

```xml
globals:
  host : localhost
tests:
  - add : CreatePageTreeTest
    properties:
      template : /conf/toughday-templates/settings/wcm/templates/toughday-template
```

### Arbeiten mit vordefinierten Test-Suites {#working-with-predefined-test-suites}

Die folgenden Beispiele zeigen, wie Sie einen Test zu einer vordefinierten Suite hinzufügen und einen vorhandenen Test neu konfigurieren und aus einer vordefinierten Suite ausschließen.

Um einen neuen Test zu einer vordefinierten Suite hinzuzufügen, verwenden Sie den Parameter `add` und geben die gewünschte Suite an.

Mit Befehlszeilenparametern:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest
```

Mit einer YAML-Konfigurationsdatei:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - add : CreatePageTreeTest
```

Bestehende Tests in einer bestimmten Suite können auch mit der `config`* *Parameter. Beachten Sie, dass Sie auch den Suite-Namen und den tatsächlichen Namen des Tests angeben müssen (nicht den Namen der Testklasse). Den Testnamen finden Sie in der Eigenschaft `name` der Testklasse. Weitere Informationen zum Finden von Testeigenschaften finden Sie im Abschnitt [Ändern von Testeigenschaften](/help/sites-developing/tough-day.md#changing-the-test-properties).

Im Beispiel unten der standardmäßige Asset-Titel für die `CreatePageTreeTest` (benannt `UploadAsset`) in &quot;NewAsset&quot;geändert.

Mit Befehlszeilenparametern:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --config UploadAsset title=NewAsset
```

Mit einer YAML-Konfigurationsdatei:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - config : UploadAsset
    properties :
      title : NewAsset
```

Außerdem können Sie auch Tests aus vordefinierten Suites oder Herausgebern von der Standardkonfiguration entfernen. Dazu dient der Parameter `exclude`. Bitte beachten Sie, dass Sie auch den Suite-Namen und den tatsächlichen Namen des Tests (nicht den Test C) angeben müssen. `lass` name). Sie finden den Testnamen im `name` -Eigenschaft der Testklasse. Im folgenden Beispiel wird die Variable `CreatePageTreeTest` (benannt `UploadAsset`) wird der Test aus der Toughday Suite entfernt.

Mit Befehlszeilenparametern:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --exclude UploadAsset
```

Mit einer YAML-Konfigurationsdatei:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - exclude : UploadAsset
```

### Ausführungsmodi {#run-modes}

Tough Day 2 kann in einem der folgenden Modi ausgeführt werden: **normal** und **konstante Belastung**.

Die **normal** Der Ausführungsmodus verfügt über zwei Parameter:

* `concurrency` - &quot;concurrency&quot;stellt die Anzahl der Threads dar, die Tough Day 2 für die Testausführung erstellt. Auf diesen Threads werden die Tests ausgeführt, bis entweder die Dauer abgelaufen ist oder es keine weiteren Tests zur Durchführung mehr gibt.

* `waittime` – Dieser Parameter legt die Wartezeit zwischen zwei aufeinanderfolgenden Testausführungen auf demselben Thread fest. Der Wert muss in Millisekunden angegeben werden.

Das folgende Beispiel zeigt, wie Sie die Parameter hinzufügen – mit der Befehlszeile:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest --runmode=normal concurrency=20
```

oder mit einer YAML-Konfigurationsdatei:

```xml
runmode:
  type : normal
  waittime : 300
  concurrency : 200
```

Die **konstante Belastung** Der Ausführungsmodus unterscheidet sich vom normalen Ausführungsmodus, indem eine konstante Anzahl von gestarteten Testausführungen und nicht eine konstante Anzahl von Threads generiert wird. Sie können die Last mithilfe des Parameters Ausführungsmodus mit demselben Namen festlegen.

### Testauswahl {#test-selection}

Der Testauswahlprozess ist für beide Ausführungsmodi identisch und läuft wie folgt ab: alle Tests `weight` -Eigenschaft, die die Wahrscheinlichkeit der Ausführung in einem Thread bestimmt. Wenn es z. B. zwei Tests gibt, einen mit dem „weight“-Wert 5 und einen mit dem „weight“-Wert 10, ist die Wahrscheinlichkeit der Ausführung bei dem Test mit dem Wert 10 doppelt so hoch wie bei dem anderen Test.

Darüber hinaus können Tests eine `count` -Eigenschaft, die die Anzahl der Ausführungen auf eine bestimmte Zahl begrenzt. Wenn diese Anzahl erreicht ist, finden keine weiteren Testausführungen mehr statt. Alle Testinstanzen, die bereits ausgeführt werden, beenden die Ausführung wie konfiguriert. Das folgende Beispiel zeigt, wie Sie diese Parameter mit der Befehlszeile oder mit einer YAML-Konfigurationsdatei hinzufügen.

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest weight=5 --add CreatePageTreeTest weight=10 count=100 --runmode=normal concurrency=20
```

oder

```xml
- add : CreateAssetTreeTest
    properties :
      name : UploadAsset
      weight : 5
      base : 3
      foldertitle : IAmAFolder
      assettitle : IAmAnAsset
      count : 100
```

>[!NOTE]
>
>Aufgrund paralleler Ausführungen entspricht die tatsächliche Anzahl der Testläufe nicht genau dem in der Variablen `count` Parameter. Erwarten Sie eine Abweichung, die proportional zur Anzahl der laufenden Threads ist (gesteuert durch die Variable `concurrency parameter`).

### Probelauf {#dry-run}

Ein Probelauf analysiert alle Eingaben (Befehlszeilenparameter oder Konfigurationsdateien), führt sie mit den Standardwerten zusammen und gibt die Ergebnisse aus. Er führt keinen Test durch.

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest --dryrun=true
```

## Ausgabe {#output}

Tough Day 2 gibt Testmetriken und -protokolle aus. Weitere Informationen finden Sie in den folgenden Abschnitten.

### Testmetriken {#test-metrics}

Tough Day 2 meldet derzeit neun Testmetriken, die Sie auswerten können. Metriken mit der ***** -Symbol wird erst nach erfolgreichen Ausführungen gemeldet:

| **Name** | **Beschreibung** |
|---|---|
| Timestamp | Zeitstempel des letzten abgeschlossenen Testlaufs. |
| Bestanden | Anzahl erfolgreicher Ausführungen. |
| Fehlgeschlagen | Anzahl fehlgeschlagener Ausführungen. |
| Min* | Niedrigste Dauer der Testausführung. |
| Maximal* | Höchste Dauer der Testausführung. |
| Median* | Berechnete mittlere Dauer aller Testausführungen. |
| Durchschnitt* | Berechnete durchschnittliche Dauer aller Testausführungen. |
| StdDev* | Die Standardabweichung. |
| 90p* | 90. Perzentil. |
| 99p* | 99. Perzentil. |
| 99.9p* | 99,9 Perzentil. |
| Tatsächlicher Durchsatz* | Anzahl der Ausführungen dividiert durch die verstrichene Ausführungszeit. |

Diese Metriken werden mithilfe von Herausgebern geschrieben, die mit dem `add` -Parameter (ähnlich wie beim Hinzufügen von Tests). Aktuell gibt es zwei Optionen:

* **CSVPublisher** - die Ausgabe eine CSV-Datei ist.
* **ConsolePublisher** - die Ausgabe wird in der Konsole angezeigt.

Standardmäßig werden beide Herausgeber aktiviert.

Zusätzlich gibt es zwei Modi, bei denen die Metriken gemeldet werden:

* Die **einfach** Veröffentlichungsmodus - meldet die Ergebnisse vom Beginn der Ausführung bis zum Zeitpunkt der Veröffentlichung.
* Die **Intervalle** Veröffentlichungsmodus - meldet die Ergebnisse in einem bestimmten Zeitraum. Sie können den Zeitrahmen mit dem **interval** Veröffentlichungsmodus-Parameter.

Das folgende Beispiel zeigt, wie Sie den Parameter `intervals` mit der Befehlszeile oder mit einer YAML-Konfigurationsdatei konfigurieren.

Mit Befehlszeilenparametern:

```xml
java -jar toughday2.jar --host=localhost --add CreatePageTreeTest --publishmode type=intervals interval=10s
```

Mit einer YAML-Konfigurationsdatei:

```xml
publishmode:
     type : intervals
     interval : 10s
     tests:
        -add : CreatePageTreeTest
```

### Protokollierung {#logging}

Tough Day 2 erstellt einen Protokollordner in demselben Ordner, in dem Sie Tough Day 2 ausgeführt haben. Dieser Ordner enthält zwei Arten von Protokollen:

* **toughday.log**: enthält Meldungen zum Anwendungsstatus, Debugging-Informationen und globale Meldungen
* **toughday_&lt;Testname>.log**: Meldungen zum genannten Test

Die Protokolle werden nicht überschrieben. Bei nachfolgenden Testausführungen werden Meldungen an die vorhandenen Protokolle angehängt. Die Protokolle haben mehrere Ebenen. Weitere Informationen finden Sie unter ` [loglevel parameter](/help/sites-developing/tough-day.md#global-parameters)`.

#### Anwendungsbeispiel {#example-usage}

#### Bekannte Probleme {#known-issues}

[Datei laden](assets/toughday-6_1.jar)
