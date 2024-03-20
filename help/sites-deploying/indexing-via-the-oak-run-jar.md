---
title: Indizierung mithilfe des Oak-run-JAR
description: Erfahren Sie, wie Sie mithilfe des Oak-run-JAR eine Indizierung durchführen.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: dcec8c1b-13cc-486c-b1a4-62e6eb3184ad
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 25%

---

# Indizierung mithilfe des Oak-run-JAR {#indexing-via-the-oak-run-jar}

Oak-run unterstützt alle Indizierungs-Anwendungsfälle über die Befehlszeile, ohne dass der Einsatz von JMX erforderlich ist. Vorteile des Oak-Run-Ansatzes sind:

1. Es ist ein neues Indizierungs-Tool für AEM 6.4
1. Dadurch wird die Zeit bis zur Neuindizierung verkürzt, was sich positiv auf die Neuindizierungszeiten bei größeren Repositorys auswirkt
1. Sie reduziert den Ressourcenverbrauch während der Neuindizierung in AEM, was zu einer besseren Systemleistung für andere AEM-Aktivitäten führt.
1. Oak-run bietet Out-of-Band-Unterstützung: Wenn Sie unter Produktionsbedingungen keine Neuindizierung auf Produktionsinstanzen durchführen lassen, kann eine geklonte Umgebung für die Neuindizierung verwendet werden, um kritische Leistungseinbußen zu vermeiden.

Im Folgenden finden Sie eine Liste von Anwendungsfällen, die bei der Durchführung von Indizierungsvorgängen über die `oak-run` -Tool.

## Prüfung der Indexkonsistenz {#indexconsistencychecks}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Nutzungsszenario 1 - Prüfung der Indexkonsistenz](/help/sites-deploying/oak-run-indexing-usecases.md#usercase1indexconsistencycheck).

* `oak-run.jar`ermittelt schnell, ob Lucene Oak-Indizes beschädigt sind.
* Es kann problemlos auf einer verwendeten AEM-Instanz ausgeführt werden, um die Konsistenz auf den Ebenen 1 und 2 zu prüfen.

![Prüfung der Indexkonsistenz](assets/screen_shot_2017-12-14at135758.png)

## Indexstatistiken {#indexstatistics}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Nutzungsszenario 2 - Indexstatistiken](/help/sites-deploying/oak-run-indexing-usecases.md#usecase2indexstatistics) 

* `oak-run.jar` Gibt alle Indexdefinitionen, wichtigen Indexstatistiken und Indexinhalte für die Offline-Analyse aus.
* Kann problemlos auf einer verwendeten AEM-Instanz ausgeführt werden.

![image2017-12-19_9-47-40](assets/image2017-12-19_9-47-40.png)

## Entscheidungsbaum &quot;Neuindizierungsansatz&quot; {#reindexingapproachdecisiontree}

Dieses Diagramm ist ein Entscheidungsbaum für die Verwendung der verschiedenen Neuindizierungsansätze.

![oak_-_reindexingwithoak-run](assets/oak_-_reindexingwithoak-run.png)

## Neuindizierung von MongoMK/RDMBMK {#reindexingmongomk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Nutzungsszenario 3 - Neuindizierung](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing).

### Textvorextraktion für SegmentNodeStore und DocumentNodeStore {#textpre-extraction}

[Textvorextraktion](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-perform-text-pre-extraction) (eine Funktion, die mit AEM 6.3 vorhanden ist) kann verwendet werden, um die Zeit für die Neuindizierung zu verkürzen. Die Textvorextraktion kann mit allen Neuindizierungsansätzen verwendet werden.

Je nach `oak-run.jar` Indizierungsansatz verwenden, gibt es auf beiden Seiten des Schritts Neuindizierung durchführen im unten stehenden Diagramm verschiedene Schritte.

![Textvorextraktion für SegmentNodeStore und DocumentNodeStore](assets/4.png)

>[!NOTE]
>
>Orange bezeichnet Aktivitäten, bei denen sich AEM in einem Wartungsfenster befinden müssen.

### Online-Neuindizierung für MongoMK oder RDBMK mit oak-run.jar {#onlinere-indexingformongomk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Neuindizieren - DocumentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexdocumentnodestore).

Dies ist die empfohlene Methode für die Neuindizierung von MongoMK (und RDBMK) AEM Installationen. Es sollte keine andere Methode angewendet werden.

Führen Sie diesen Prozess nur für eine einzelne AEM-Instanz im Cluster aus.

![Online-Neuindizierung für MongoMK oder RDBMK mit oak-run.jar](assets/5.png)

## Neuindizierung von TarMK {#re-indexingtarmk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Neuindizieren - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexsegmentnodestore).

* **Überlegungen zu Cold-Standby (TarMK)**

   * Für Cold Standby gibt es keine besonderen Überlegungen. Die Cold Standby-Instanzen synchronisieren Änderungen wie gewohnt.

* **AEM Veröffentlichungsfarmen (AEM-Veröffentlichungsfarmen sollten immer TarMK sein)**

   * Für die Veröffentlichungsfarm muss dies für alle ODER die Schritte für eine einzelne Veröffentlichung ausgeführt werden. Dann klonen Sie das Setup für andere (nehmen Sie alle üblichen Vorsichtsmaßnahmen beim Klonen AEM Instanzen; sling.id - sollte hier auf etwas verweisen).

### Online-Neuindizierung für TarMK {#onlinere-indexingfortarmk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestore).

Dies ist die Methode, die vor der Einführung der neuen Indizierungsfunktionen von oak-run.jar angewendet wurde. Dies geschieht durch Festlegen der `reindex=true` -Eigenschaft auf dem Oak-Index.

Dieser Ansatz kann verwendet werden, wenn die Zeit- und Leistungseffekte für den Kunden akzeptabel sind. Dies gilt häufig für kleine und mittlere AEM.

![Online-Neuindizierung für TarMK](assets/6.png)

### Online-Neuindizierung von TarMK mit oak-run.jar {#onlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung - SegmentNodeStore - Die AEM-Instanz wird ausgeführt](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoretheaeminstanceisrunning).

Die Online-Neuindizierung von TarMK mithilfe von oak-run.jar ist schneller als die [Online-Neuindizierung für TarMK](#onlinere-indexingfortarmk) weiter oben beschrieben. Es erfordert jedoch auch die Ausführung während eines Wartungsfensters, mit der Hinweis, dass das Fenster kürzer ist und mehr Schritte erforderlich sind, um die Neuindizierung durchzuführen.

>[!NOTE]
>
>Vorgänge, bei denen sich AEM in einem Wartungsfenster befinden muss, sind orange dargestellt.

![Online-Neuindizierung von TarMK mit oak-run.jar](assets/7.png)

### Offline-Neuindizierung von TarMK mit oak-run.jar {#offlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung - SegmentNodeStore - Die AEM Instanz ist beendet.](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoreaeminstanceisdown).

Die Offline-Neuindizierung von TarMK ist die einfachste `oak-run.jar` basierter Neuindizierungsansatz für TarMK, da er nur eine `oak-run.jar` kommentieren. Dazu muss die AEM Instanz jedoch heruntergefahren werden.

>[!NOTE]
>
>Rot bezeichnet Vorgänge, bei denen AEM heruntergefahren werden müssen.

![Offline-Neuindizierung von TarMK mit oak-run.jar](assets/8.png)

### Out-of-Band-Neuindizierung von TarMK mit oak-run.jar  {#out-of-bandre-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Out-Band-Neuindizierung - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#outofbandreindexsegmentnodestore).

Die Out-of-Band-Neuindizierung minimiert die Auswirkungen der Neuindizierung auf AEM-Instanzen in der Verwendung.

>[!NOTE]
>
>Rot bezeichnet Vorgänge, bei denen AEM abgeschaltet werden können.

![Out-of-Band-Neuindizierung von TarMK mit oak-run.jar](assets/9.png)

## Aktualisieren von Indexdefinitionen {#updatingindexingdefinitions}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Nutzungsszenario 4 - Aktualisieren von Indexdefinitionen](/help/sites-deploying/oak-run-indexing-usecases.md#usecase4updatingindexdefinitions).

### Erstellen und Aktualisieren von Indexdefinitionen auf TarMK mithilfe von ACS Ensure Index {#creatingandupdatingindexdefinitionsontarmkusingacsensureindex}

>[!NOTE]
>
>ACS Ensure Index ist ein von der Community unterstütztes Projekt und wird von der Adobe-Unterstützung nicht unterstützt.

Dies ermöglicht den Versand der Indexdefinition über das Inhaltspaket, was später zu einer Neuindizierung führt, indem das reindex-Flag auf `true`. Dies funktioniert bei kleineren Setups, bei denen die Neuindizierung nicht lange dauert.

Weitere Informationen finden Sie unter [ACS Ensure Index-Dokumentation](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) für Details.

### Erstellen und Aktualisieren von Indexdefinitionen auf TarMK mit oak-run.jar {#creatingandupdatingindexdefinitionsontarmkusingoak-run-jar}

Wenn die Zeit- oder Leistungsauswirkungen der Neuindizierung mit Nicht-Indizierung`oak-run.jar` -Methoden zu hoch ist, lautet die folgende `oak-run.jar` kann zum Importieren und Neuindizieren von Lucene-Index-Definitionen in einer TarMK-basierten AEM verwendet werden.

![Erstellen und Aktualisieren von Indexdefinitionen auf TarMK mit oak-run.jar](assets/10.png)

### Erstellen und Aktualisieren von Indexdefinitionen auf MongoMK mit oak-run.jar {#creatingandupdatingindexdefinitionsonmonogmkusingoak-run-jar}

Wenn die Zeit- oder Leistungsauswirkungen der Neuindizierung mit Nicht-Indizierung`oak-run.jar` -Methoden zu hoch ist, lautet die folgende `oak-run.jar` kann zum Importieren und Neuindizieren von Lucene-Index-Definitionen in MongoMK-basierten AEM verwendet werden.

![Erstellen und Aktualisieren von Indexdefinitionen auf MongoMK mit oak-run.jar](assets/11.png)
