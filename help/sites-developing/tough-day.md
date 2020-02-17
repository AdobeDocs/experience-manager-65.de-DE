---
title: Tough Day
seo-title: Tough Day
description: Der „Tough Day“-Test simuliert die tägliche Last von rund 1.000 Autoren in einem Worst-Case-Szenario, bei dem alle Vorgänge gleichzeitig ablaufen.
seo-description: Der „Tough Day“-Test simuliert die tägliche Last von rund 1.000 Autoren in einem Worst-Case-Szenario, bei dem alle Vorgänge gleichzeitig ablaufen.
uuid: 1b672182-40f5-4580-b038-2e3c8fbfb8b7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: ea6b40fe-b6e1-495c-b34f-8815a4e2e42e
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Tough Day{#tough-day}

## Was ist Tough Day 2?{#what-is-tough-day}

„Tough Day 2“ ist eine Anwendung, mit der Sie einen Stresstest Ihrer AEM-Instanz durchführen können. Sie können ihn direkt mit der standardmäßigen Test-Suite ausführen oder an Ihre Testanforderungen anpassen. In [dieser Aufnahme](https://docs.adobe.com/ddc/en/gems/Toughday2---A-new-and-improved-stress-testing-and-benchmarking-tool.html) sehen Sie eine Präsentation der Anwendung.

## How to Run Tough Day 2 {#how-to-run-tough-day}

Laden Sie die aktuelle Version von Tough Day 2 aus dem [Adobe-Repository](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/qe/toughday2/) herunter. After you download the application, you can run it out of the box by providing the `host` parameter. In the following example, the AEM instance runs locally so the `localhost` value is used:

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

Um die Suite-Tests auszuführen, installiert Tough Day 2 das Standard-Inhaltspaket. This can be avoided by setting the `installsamplecontent`parameter to `false`, but remember that you should also change the default paths for the tests that you intend to run. If the jar is run without parameters, Tough Day 2 displays the [help information](/help/sites-developing/tough-day.md#getting-help).

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
   <td>Druckt die Testklassen und ihre Beschreibung.</td>
   <td> </td>
  </tr>
  <tr>
   <td>—help_full</td>
   <td>Druckt alle oben genannten Elemente sowie Tests, Herausgeber und Suite-Komponenten.</td>
   <td> </td>
  </tr>
  <tr>
   <td> —help —runmode/publishmode type=&lt;mode&gt;</td>
   <td>Listet Informationen zum angegebenen Ausführungsmodus oder Veröffentlichungsmodus auf.</td>
   <td><p>java -jar toughday2.jar —help —runmode type=conantload</p> <p>java -jar toughday2.jar —help —publishmode type=interval</p> </td>
  </tr>
  <tr>
   <td>—help —suite=&lt;SuiteName&gt;</td>
   <td>Listet alle Tests einer angegebenen Suite und deren jeweilige konfigurierbare Eigenschaften auf.</td>
   <td><br /> java -jar toughday2.jar —help —suite=get_tests</td>
  </tr>
  <tr>
   <td> —help —tag=&lt;Tag&gt;</td>
   <td><br /> Listet alle Elemente mit dem angegebenen Tag auf.</td>
   <td>java -jar toughday2.jar —help —tag=publish</td>
  </tr>
  <tr>
   <td>—help &lt;TestClass/PublisherClass&gt;</td>
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
| `--installsamplecontent=<Val>` | Installieren oder überspringen Sie das Standard-Inhaltspaket für Tag 2. | true | „true“ oder „false“ |
| `--protocol=<Val>` | Das für den Host verwendete Protokoll. | http | http oder https |
| `--host=<Val>` | Der Hostname oder die IP-Adresse, die als Ziel verwendet werden soll. |  |  |
| `--port=<Val>` | Der Anschluss des Hosts. | 4502 |  |
| `--user=<Val>` | Der Benutzername für die Instanz. | admin |  |
| `--password=<Val>` | Kennwort für den angegebenen Benutzer. | admin |  |
| `--duration=<Val>` | Dauer der Tests. Can be expressed in (**s**)econds, (**m**)inutes, (**h**)ours and (**d**)ays. | 1d |  |
| `--timeout=<Val>` | Wie lange ein Test ausgeführt wird, bevor er unterbrochen und als fehlgeschlagen markiert wird. In Sekunden angegeben. | 180 |  |
| `--suite=<Val>` | Der Wert kann eine oder eine Liste (durch Kommas getrennt) vordefinierter Test Suites sein. | toughday |  |
| `--configfile=<Val>` | Die zielgerichtete yaml-Konfigurationsdatei. |  |  |
| `--contextpath=<Val>` | Kontextpfad der Instanz. |  |  |
| `--loglevel=<Val>` | Die Protokollierungsstufe für die Tough Day 2-Engine. | INFO | ALL, DEBUG, INFO, WARN, FEHLER, FATAL, AUS |
| `--dryrun=<Val>` | Wenn &quot;true&quot;, wird die resultierende Konfiguration gedruckt und es werden keine Tests ausgeführt. | false | „true“ oder „false“ |

## Anpassung {#customizing}

Die Anpassung erfolgt wahlweise über Befehlszeilenparameter oder YAML-Konfigurationsdateien. **Konfigurationsdateien werden in der Regel für umfangreiche angepasste Suites verwendet. Sie überschreiben die Standardparameter von Tough Day 2. Befehlszeilenparameter überschreiben sowohl Konfigurationsdateien als auch Standardparameter.**

Die einzige Möglichkeit, eine Testkonfiguration zu speichern, besteht darin, sie in das YAML-Format zu kopieren. For additional details, see this [toughday.yaml](https://repo.adobe.com/nexus/service/local/repositories/releases/content/com/adobe/qe/toughday2/0.2.1/toughday2-0.2.1.yaml) configuration and the yaml configuration examples in the sections below.

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

Wenn Sie eine Testeigenschaft (oder mehrere) ändern müssen, können Sie diese Eigenschaft(en) zur Befehlszeile oder zur YAML-Konfigurationsdatei hinzufügen. To see all the available test properties add the `--help <TestClass/PublisherClass>` parameter to the command line, for example:

```xml
java -jar toughday2.jar --help CreatePageTreeTest
```

Beachten Sie, dass die YAML-Konfigurationsdateien die Standardparameter von Tough Day 2 überschreiben und Befehlszeilenparameter sowohl die Konfigurationsdateien als auch die Standardparameter überschreiben.

The examples below show how to change the `template` property for the `CreatePageTreeTest` test either by using either command line parameters or a yaml configuration file.

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

Existing tests in a given suite can also be reconfigured using the `config`* *parameter. Bitte beachten Sie, dass Sie auch den Namen der Suite und den tatsächlichen Namen des Tests angeben müssen (nicht den Namen der Testklasse). Den Testnamen finden Sie in der Eigenschaft `name` der Testklasse. Weitere Informationen zum Finden von Testeigenschaften finden Sie im Abschnitt [Ändern von Testeigenschaften](/help/sites-developing/tough-day.md#changing-the-test-properties).

In the example below the default asset title for the `CreatePageTreeTest` (named `UploadAsset`) is changed to &quot;NewAsset&quot;.

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

Außerdem können Sie auch Tests aus vordefinierten Suites oder Herausgebern von der Standardkonfiguration entfernen. Dazu dient der Parameter `exclude`. Please note that you must also specify the suite name and the actual name of the test (not the Test C `lass` name). You can find the test name in the `name` property of the test class. In the example below, the `CreatePageTreeTest` (named `UploadAsset`) test is removed from the toughday suite.

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

Tough Day 2 can run in one of the following modes: **normal** and **constant load**.

The **normal** run mode has two parameters:

* `concurrency` - Parallelität stellt die Anzahl der Threads dar, die Tough Day 2 zur Testausführung erstellen wird. Auf diesen Threads werden die Tests ausgeführt, bis entweder die Dauer abgelaufen ist oder es keine weiteren Tests zur Durchführung mehr gibt.

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

The **constant load** run mode differs from the normal run mode by generating a constant number of started test executions, rather than a constant number of threads. Sie können die Last mit dem Parameter run mode mit demselben Namen festlegen.

### Testauswahl {#test-selection}

The test selection process is the same for both run modes and it goes as follows: all tests have a `weight` property, which determines the likelihood of execution in a thread. Wenn es z. B. zwei Tests gibt, einen mit dem „weight“-Wert 5 und einen mit dem „weight“-Wert 10, ist die Wahrscheinlichkeit der Ausführung bei dem Test mit dem Wert 10 doppelt so hoch wie bei dem anderen Test.

Furthermore, tests can have a `count` property, which limits the number of executions to a given number. Wenn diese Anzahl erreicht ist, finden keine weiteren Testausführungen mehr statt. Alle Testinstanzen, die bereits ausgeführt werden, beenden die Ausführung wie konfiguriert. Das folgende Beispiel zeigt, wie Sie diese Parameter mit der Befehlszeile oder mit einer YAML-Konfigurationsdatei hinzufügen.

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest weight=5 --add CreatePageTreeTest weight=10 count=100 --runmode=normal concurrency=20
```

 oder  ermöglichen.

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
>Due to parallel executions, the actual number of test runs will not be exactly the amount configured in the `count` parameter. Expect a deviation proportional to the number of running threads (controlled by the `concurrency parameter`).

### Probelauf {#dry-run}

Ein Probelauf analysiert alle Eingaben (Befehlszeilenparameter oder Konfigurationsdateien), führt sie mit den Standardwerten zusammen und gibt die Ergebnisse aus. Er führt keinen Test durch.

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest --dryrun=true
```

## Ausgabe {#output}

Tough Day 2 gibt Testmetriken und -protokolle aus. Weitere Informationen finden Sie in den folgenden Abschnitten.

### Testmetriken {#test-metrics}

Tough Day 2 meldet derzeit neun Testmetriken, die Sie auswerten können. Metrics with the ***** symbol are reported only after successful runs:

| **Name** | **Beschreibung** |
|---|---|
| Timestamp | Zeitstempel des letzten abgeschlossenen Testlaufs. |
| Bestanden | Anzahl der erfolgreichen Ausführung. |
| Fehlgeschlagen | Anzahl der fehlgeschlagenen Ausführung. |
| Min* | Niedrigste Dauer der Testausführung. |
| Maximal* | Höchstdauer der Testausführung. |
| Median* | Berechnete mittlere Dauer aller Testausführungen. |
| Durchschnitt* | Berechnete durchschnittliche Dauer aller Testausführungen. |
| StdDev* | Die Standardabweichung. |
| 90p* | 90 Perzentil. |
| 99p* | 99 Perzentil. |
| 99.9p* | 99,9 Perzentil. |
| Realer Durchsatz* | Anzahl der Ausführung geteilt durch die verstrichene Ausführungszeit. |

These metrics are written with the help of publishers that can be added with the `add` parameter (similarly to adding tests). Aktuell gibt es zwei Optionen:

* **CSVPublisher** - die Ausgabe ist eine CSV-Datei.
* **ConsolePublisher** : Die Ausgabe wird in der Konsole angezeigt.

Standardmäßig werden beide Herausgeber aktiviert.

Zusätzlich gibt es zwei Modi, bei denen die Metriken gemeldet werden:

* The **simple** publish mode - reports the results from the beginning of the execution up to the point of publishing.
* The **intervals** publish mode - reports the results in a given time frame. You can set the time frame with the **interval** publish mode parameter.

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

Tough Day 2 erstellt einen Protokollordner im selben Verzeichnis, in dem Sie Tough Day 2 ausgeführt haben. Dieser Ordner enthält zwei Arten von Protokollen:

* **toughday.log**: enthält Meldungen zum Anwendungsstatus, Debugging-Informationen und globale Meldungen
* **toughday_&lt;Testname>.log**: Meldungen zum genannten Test

Die Protokolle werden nicht überschrieben. Bei nachfolgenden Testausführungen werden Meldungen an die vorhandenen Protokolle angehängt. The logs have several levels, for more information see the ` [loglevel parameter](/help/sites-developing/tough-day.md#global-parameters)`.

#### Anwendungsbeispiel {#example-usage}

#### Bekannte Probleme {#known-issues}

[Datei laden](assets/toughday-6_1.jar)
