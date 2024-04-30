---
title: Tough Day
description: Der „Tough Day“-Test simuliert die tägliche Last von rund 1.000 Autorinnen und Autoren in einem Worst-Case-Szenario, bei dem alle Vorgänge gleichzeitig ablaufen.
topic-tags: testing
content-type: reference
exl-id: ceb9671c-57f9-4d81-94c0-0dbccd4d90a2
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1825'
ht-degree: 100%

---

# Tough Day{#tough-day}

## Was ist Tough Day 2? {#what-is-tough-day}

„Tough Day 2“ ist eine Anwendung, mit der Sie einen Stresstest Ihrer AEM-Instanz durchführen können. Sie können diesen direkt mit der standardmäßigen Test-Suite ausführen oder an Ihre Testanforderungen anpassen. In [dieser Aufnahme](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2017/aem-toughday2-stress-testing-benchmarking-tool.html?lang=de) sehen Sie eine Präsentation der Anwendung.

>[!CAUTION]
>
>Tough Day 2 erfordert Java™ 8.

## Ausführen von Tough Day 2 {#how-to-run-tough-day}

Laden Sie die aktuelle Version von Tough Day 2 aus dem [Adobe-Repository](https://repo1.maven.org/maven2/com/adobe/qe/toughday2/) herunter. Nach dem Download können Sie die Anwendung direkt ausführen. Sie müssen lediglich den Parameter `host` angeben. Beim folgenden Beispiel wird die AEM-Instanz lokal ausgeführt. Daher wird der Wert `localhost` verwendet:

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

Um die Suite-Tests auszuführen, installiert Tough Day 2 das Standard-Inhaltspaket. Um dies zu vermeiden, können Sie den Parameter `installsamplecontent` auf `false` festlegen. Denken Sie aber daran, auch die Standardpfade für die Tests zu ändern, die Sie ausführen möchten. Wenn die JAR ohne Parameter ausgeführt wird, zeigt Tough Day 2 die [Hilfe-Informationen](/help/sites-developing/tough-day.md#getting-help) an.

In der Regel können Sie die Anwendung verwenden, indem Sie diesem Muster folgen:

```xml
java -jar toughday2.jar [--help | --help_full | --help_tests | --help_publish]  [<global arguments> | <actions> | --runmode | --publishmode]
```

>[!NOTE]
>
>Bei Tough Day 2 gibt es keinen Bereinigungsschritt. Wir empfehlen daher, Tough Day 2 auf einer geklonten Staging-Instanz auszuführen, nicht auf der Hauptproduktionsinstanz. Die Staging-Instanz sollte nach den Tests nicht mehr genutzt werden.
>

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
   <td>Druckt globale Informationen aus, z. B.: die verfügbaren Aktionen, vordefinierte Suites, Ausführungsmodi und globale Parameter.</td>
   <td> </td>
  </tr>
  <tr>
   <td>--help_publish</td>
   <td>Druckt alle verfügbaren Publisher aus.</td>
   <td> </td>
  </tr>
  <tr>
   <td>--help_tests</td>
   <td>Druckt die Testklassen und deren Beschreibung.</td>
   <td> </td>
  </tr>
  <tr>
   <td>--help_full</td>
   <td>Druckt alle oben genannten Funktionen sowie Tests, Publisher und Suite-Komponenten.</td>
   <td> </td>
  </tr>
  <tr>
   <td> --help --runmode/publishmode type=&lt;Mode&gt;</td>
   <td>Listet Informationen zum angegebenen Ausführungs- oder Veröffentlichungsmodus auf.</td>
   <td><p>Java™ -jar toughday2.jar --help --runmode type=constantload</p> <p>Java™ -jar toughday2.jar --help --publishmode type=intervals</p> </td>
  </tr>
  <tr>
   <td>--help --suite=&lt;SuiteName&gt;</td>
   <td>Listet alle Tests einer bestimmten Suite und ihre jeweiligen konfigurierbaren Eigenschaften auf.</td>
   <td><br /> Java™ -jar toughday2.jar --help --suite=get_tests</td>
  </tr>
  <tr>
   <td> --help --tag=&lt;Tag&gt;</td>
   <td><br /> Listet alle Elemente mit dem angegebenen Tag auf.</td>
   <td>Java™ -jar toughday2.jar --help --tag=publish</td>
  </tr>
  <tr>
   <td>--help &lt;TestClass/PublisherClass&gt;</td>
   <td><br /> Listet alle konfigurierbaren Eigenschaften für den jeweiligen Test oder Publisher auf.</td>
   <td><p>Java™ -jar toughday2.jar --help UploadPDFTest</p> <p>Java™ -jar toughday2.jar --help CSVPublisher</p> </td>
  </tr>
 </tbody>
</table>

### Globale Parameter {#global-parameters}

Tough Day 2 bietet globale Parameter, die die Umgebung für die Tests festlegen oder ändern. Dazu gehören der Ziel-Host, die Port-Nummer, das verwendete Protokoll, Benutzername und Kennwort für die Instanz usw. Beispiel:

```xml
java -jar toughday2.jar --host=host --protocol=https --port=4502 --duration=30m --dryrun=true
```

Die relevanten Parameter finden Sie in der folgenden Liste:

| **Parameter** | **Beschreibung** | **Standardwert** | **Mögliche Werte** |
|---|---|---|---|
| `--installsamplecontent=<Val>` | Das standardmäßige Inhaltspaket „Tough Day 2“ wird entweder installiert oder übersprungen. | Ja | „true“ oder „false“ |
| `--protocol=<Val>` | Das für den Host verwendete Protokoll. | http | http oder https |
| `--host=<Val>` | Der Hostname oder die IP-Adresse, die als Ziel ausgewählt wird. |  |  |
| `--port=<Val>` | Der Port des Hosts. | 4502 |  |
| `--user=<Val>` | Der Benutzername für die Instanz. | admin |  |
| `--password=<Val>` | Kennwort für den angegebenen Benutzer. | admin |  |
| `--duration=<Val>` | Die Dauer der Tests. Kann in Sekunden (**s**), Minuten (**m**), Stunden (**h**) und Tagen (**d**) angegeben werden. | 1d |  |
| `--timeout=<Val>` | Gibt an, wie lange ein Test ausgeführt wird, bevor er unterbrochen und als fehlgeschlagen markiert wird. In Sekunden angegeben. | 180 |  |
| `--suite=<Val>` | Der Wert kann eine oder eine Liste (durch Kommas getrennt) von vordefinierter Test-Suites sein. | toughday |  |
| `--configfile=<Val>` | Die angesprochene yaml-Konfigurationsdatei. |  |  |
| `--contextpath=<Val>` | Kontextpfad der Instanz. |  |  |
| `--loglevel=<Val>` | Die Protokollebene für die Tough Day 2-Engine. | INFO | ALL, DEBUG, INFO, WARN, ERROR, FATAL, OFF |
| `--dryrun=<Val>` | Wenn „true“, wird die resultierende Konfiguration gedruckt und es werden keine Tests ausgeführt. | Nein | „true“ oder „false“ |

## Anpassung {#customizing}

Die Anpassung kann auf zwei Arten erfolgen: durch Befehlszeilenparameter oder YAML-Konfigurationsdateien. **Konfigurationsdateien werden für große, benutzerdefinierte Suites verwendet und überschreiben die Standardparameter von Tough Day 2. Befehlszeilenparameter überschreiben sowohl Konfigurationsdateien als auch die Standardparameter.**

Die einzige Möglichkeit, eine Testkonfiguration zu speichern, besteht darin, sie in das YAML-Format zu kopieren.

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

### Hinzufügen mehrerer Instanzen desselben Tests  {#adding-multiple-instances-of-the-same-test}

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

Wenn Sie eine Testeigenschaft (oder mehrere) ändern müssen, können Sie diese Eigenschaft(en) zur Befehlszeile oder zur YAML-Konfigurationsdatei hinzufügen. Um alle verfügbaren Testeigenschaften anzuzeigen, fügen Sie den Parameter `--help <TestClass/PublisherClass>` zur Befehlszeile hinzu, z. B.:

```xml
java -jar toughday2.jar --help CreatePageTreeTest
```

Beachten Sie, dass die YAML-Konfigurationsdateien die Standardparameter von Tough Day 2 überschreiben und Befehlszeilenparameter sowohl die Konfigurationsdateien als auch die Standardparameter überschreiben.

Die folgenden Beispiele zeigen, wie Sie die Eigenschaft `template` für den Test `CreatePageTreeTest` mit Befehlszeilenparametern oder einer YAML-Konfigurationsdatei ändern.

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

Sie können vorhandene Tests in einer bestimmten Suite mit dem Parameter* *`config` auch neu konfigurieren. Geben Sie außerdem den Namen der Suite und den tatsächlichen Namen des Tests (nicht den Namen der Testklasse) an. Den Testnamen finden Sie in der Eigenschaft `name` der Testklasse. Weitere Informationen zum Finden von Testeigenschaften finden Sie im Abschnitt [Ändern von Testeigenschaften](/help/sites-developing/tough-day.md#changing-the-test-properties).

Im nachfolgenden Beispiel wird der Standardtitel des Assets für den Test `CreatePageTreeTest` (namens `UploadAsset`) in „NewAsset“ geändert.

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

Außerdem können Sie auch Tests aus vordefinierten Suites oder Herausgebern von der Standardkonfiguration entfernen. Dazu dient der Parameter `exclude`. Geben Sie außerdem den Namen der Suite und den tatsächlichen Namen des Tests (nicht den Namen der Testk`lass`e) an. Den Testnamen finden Sie in der Eigenschaft `name` der Testklasse. Im nachfolgenden Beispiel wird der Test `CreatePageTreeTest` (namens `UploadAsset`) von der Tough Day-Suite entfernt.

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

Bei Tough Day 2 stehen zwei Ausführungsmodi zur Verfügung: **normal** und **constant load**.

Für den Ausführungsmodus **normal** gibt es zwei Parameter:

* `concurrency` – Gleichzeitigkeit repräsentiert die Anzahl an Threads, die Tough Day 2 für die Testausführung erstellt. Auf diesen Threads werden die Tests ausgeführt, bis entweder die Dauer abgelaufen ist oder es keine weiteren Tests zur Durchführung mehr gibt.

* `waittime` – Dieser Parameter legt die Wartezeit zwischen zwei aufeinanderfolgenden Testausführungen auf demselben Thread fest. Der Wert muss in Millisekunden angegeben werden.

Das folgende Beispiel zeigt, wie Sie die Parameter über die Befehlszeile hinzufügen:

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

Der Ausführungsmodus **constant load** unterscheidet sich vom normalen Ausführungsmodus dadurch, dass er eine konstante Anzahl an gestarteten Testausführungen erzeugt statt einer konstanten Zahl an Threads. Sie können die Last über den Ausführungsmodus-Parameter „load“ festlegen.

### Testauswahl {#test-selection}

Der Testauswahlvorgang ist bei beiden Ausführungsmodi gleich und läuft wie folgt ab: Alle Tests verfügen über die Eigenschaft `weight`, die die Wahrscheinlichkeit der Ausführung in einem Thread bestimmt. Wenn es z. B. zwei Tests gibt, einen mit dem „weight“-Wert 5 und einen mit dem „weight“-Wert 10, ist die Wahrscheinlichkeit der Ausführung bei dem Test mit dem Wert 10 doppelt so hoch wie bei dem anderen Test.

Außerdem können Tests die Eigenschaft `count` aufweisen, die die Anzahl an Ausführungen auf eine bestimmte Zahl einschränkt. Wenn diese Anzahl erreicht ist, finden keine weiteren Testausführungen mehr statt. Alle Testinstanzen, die bereits ausgeführt werden, beenden ihre Ausführung wie konfiguriert. Das folgende Beispiel zeigt, wie Sie diese Parameter mit der Befehlszeile oder mit einer YAML-Konfigurationsdatei hinzufügen.

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
>Wegen parallel stattfindender Ausführungen entspricht die tatsächliche Anzahl an Testausführungen nicht exakt der Anzahl, die mit dem Parameter `count` konfiguriert wurde. Rechnen Sie daher mit einer Abweichung, die proportional zur Anzahl der ausgeführten Threads ausfällt (gesteuert durch den `concurrency parameter`).

### Probelauf {#dry-run}

Ein Probelauf analysiert alle Eingaben (Befehlszeilenparameter oder Konfigurationsdateien), führt sie mit den Standardwerten zusammen und gibt die Ergebnisse aus. Er führt keinen Test durch.

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest --dryrun=true
```

## Ausgabe {#output}

Tough Day 2 gibt Testmetriken und -protokolle aus. Weitere Informationen finden Sie in den folgenden Abschnitten.

### Testmetriken {#test-metrics}

Tough Day 2 meldet derzeit neun Testmetriken, die Sie auswerten können. Mit dem Symbol **&#42;** gekennzeichnete Metriken werden nur nach erfolgreichen Ausführungen gemeldet:

| **Name** | **Beschreibung** |
|---|---|
| Timestamp | Zeitstempel des letzten abgeschlossenen Testlaufs. |
| Bestanden | Anzahl erfolgreicher Ausführungen. |
| Fehlgeschlagen | Anzahl fehlgeschlagener Ausführungen. |
| Min&#42; | Kürzeste Dauer der Testausführung. |
| Maximal&#42; | Längste Dauer der Testausführung. |
| Median&#42; | Berechnete mittlere Dauer aller Testausführungen. |
| Durchschnitt&#42; | Berechnete durchschnittliche Dauer aller Testausführungen. |
| StdDev&#42; | Die Standardabweichung. |
| 90p&#42; | 90 Perzentil. |
| 99p&#42; | 99 Perzentil. |
| 99.9p&#42; | 99,9 Perzentil. |
| Tatsächlicher Durchsatz&#42; | Anzahl an Ausführungen geteilt durch die verstrichene Ausführungszeit |

Diese Metriken werden mithilfe von Publishern geschrieben, die mit dem Parameter `add` hinzugefügt werden können (ähnlich wie beim Hinzufügen von Tests). Aktuell gibt es zwei Optionen:

* **CSVPublisher**: Die Ausgabe ist eine CSV-Datei.
* **ConsolePublisher**: Die Ausgabe wird in der Konsole angezeigt.

Standardmäßig werden beide Herausgeber aktiviert.

Zusätzlich gibt es zwei Modi, bei denen die Metriken gemeldet werden:

* Der Veröffentlichungsmodus **simple** meldet die Ergebnisse von Beginn der Ausführung bis zum Zeitpunkt der Veröffentlichung.
* Der Veröffentlichungsmodus **intervals** meldet die Ergebnisse in einem bestimmten Zeitrahmen. Den Zeitrahmen können Sie mit dem Parameter **interval** des Veröffentlichungsmodus festlegen.

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

Tough Day 2 erstellt einen Protokollordner im selben Verzeichnis, in dem Sie Tough Day 2 ausgeführt haben. Dieser Ordner enthält zwei Arten von Protokollen:

* **toughday.log**: enthält Meldungen zum Anwendungsstatus, Debugging-Informationen und globale Meldungen
* **toughday_&lt;testname>.log**: Meldungen zum genannten Test

Die Protokolle werden nicht überschrieben. Bei nachfolgenden Testausführungen werden Meldungen an die vorhandenen Protokolle angehängt. Für die Protokolle gibt es mehrere Ebenen. Weitere Informationen hierzu finden Sie unter dem Parameter [loglevel](#global-parameters).

<!--
#### Example Usage {#example-usage}

#### Known Issues {#known-issues}

[Get File](assets/toughday-6_1.jar)
-->
