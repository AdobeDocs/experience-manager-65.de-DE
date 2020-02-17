---
title: Indizieren mit dem Oak-run JAR
seo-title: Indizieren mit dem Oak-run JAR
description: Erfahren Sie, wie Sie die Indizierung mit dem Oak-run JAR durchführen.
seo-description: Erfahren Sie, wie Sie die Indizierung mit dem Oak-run JAR durchführen.
uuid: 09a83ab9-92ec-4b55-8d24-2302f28fc2e4
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: c8a505ab-a075-47da-8007-43645a8c3ce5
translation-type: tm+mt
source-git-commit: 3f53945579eaf5de1ed0b071aa9cce30dded89f1

---


# Indizieren mit dem Oak-run JAR {#indexing-via-the-oak-run-jar}

Oak-run unterstützt alle Indizierungsszenarien über die Befehlszeile und muss nicht auf der JMX-Ebene ausgeführt werden. Vorteile des Oak-run-Ansatzes:

1. Bietet ein neues Toolset für AEM 6.4
1. Verringert die für die Neuindizierung erforderliche Zeit, was bei größeren Repositorys von Vorteil ist
1. Verringert den Ressourcenverbrauch während der Neuindizierung in AEM, was die Systemleistung für andere AEM-Aktivitäten verbessert
1. Oak-run bietet Out-of-Band-Support: Wenn die Produktionsbedingungen keine Ausführung der Neuindizierung auf Produktionsinstanzen erlauben, kann für die Neuindizierung eine geklonte Umgebung genutzt werden, um eine kritische Leistungsbeeinträchtigung zu vermeiden.

Nachstehend finden Sie eine Liste von Anwendungsfällen, die Sie bei der Durchführung von Indizierungen mit dem Tool `oak-run` nutzen können. 

## Prüfung der Indexkonsistenz {#indexconsistencychecks}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Anwendungsfall 1 - Prüfung der Indexkonsistenz](/help/sites-deploying/oak-run-indexing-usecases.md#usercase1indexconsistencycheck).

* `oak-run.jar`ermittelt schnell, ob Lucene Oak-Indizes beschädigt sind.
* Es kann problemlos auf einer verwendeten AEM-Instanz ausgeführt werden, um die Konsistenz auf den Ebenen 1 und 2 zu prüfen.

![screen_shot_2017-12-14at135758](assets/screen_shot_2017-12-14at135758.png)

## Indexstatistiken {#indexstatistics}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Anwendungsfall 2 - Indexstatistiken](/help/sites-deploying/oak-run-indexing-usecases.md#usecase2indexstatistics) 

* `oak-run.jar` sichert alle Indexdefinitionen, wichtige Indexstatistiken und Indexinhalte für Offline-Analysen. 
* Kann problemlos auf einer verwendeten AEM-Instanz ausgeführt werden.

![image2017-12-19_9-47-40](assets/image2017-12-19_9-47-40.png)

## Re-indexing Approach Decision Tree {#reindexingapproachdecisiontree}

Dieses Diagramm ist ein Entscheidungsbaum für die Verwendung der verschiedenen Neuindizierungsansätze.

![oak_-_reindexingwithoak-run](assets/oak_-_reindexingwithoak-run.png)

## Neuindizierung von MongoMK/RDMBMK {#reindexingmongomk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Anwendungsfall 3 - Neuindizierung](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing).

### Textvorextraktion für SegmentNodeStore und DocumentNodeStore {#textpre-extraction}

Die [Textvorextraktion](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-perform-text-pre-extraction) (eine Funktion, die mit AEM 6.3 eingeführt wurde) kann genutzt werden, um die Zeit für die Neuindizierung zu verkürzen. Die Textvorextraktion kann mit allen Neuindizierungsansätzen verwendet werden.

Abhängig vom `oak-run.jar`-Indizierungsansatz, müssen, wie im Diagramm unten dargestellt, auf beiden Seiten des Schrittes zur Durchführung der Neuindizierung verschiedene Schritte ausgeführt werden.

![4](assets/4.png)

>[!NOTE]
>
>Aktivitäten, bei denen sich AEM in einem Wartungsfenster befinden muss, sind orange dargestellt.

### Online-Neuindizierung für MongoMK oder RDBMK mit oak-run.jar {#onlinere-indexingformongomk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Neuindizieren - DocumentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexdocumentnodestore).

Dies ist die empfohlene Methode für die Neuindizierung von AEM-Installationen mit MongoMK (und RDBMK). Wenden Sie keine andere Methode an.

Dieser Vorgang darf nur für eine einzelne AEM-Instanz im Cluster durchgeführt werden.

![5](assets/5.png)

## Neuindizierung von TarMK {#re-indexingtarmk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Neuindizieren - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexsegmentnodestore).

* **Überlegungen zu Cold-Standby (TarMK)**

   * Es gibt keine besonderen Überlegungen zu Cold-Standby. Die Cold-Standby-Instanzen synchronisieren Änderungen wie üblich.

* **AEM-Veröffentlichungsfarmen (AEM-Veröffentlichungsfarmen müssen immer TarMK-Veröffentlichungsfarmen sein)**

   * Bei einer Veröffentlichungsfarm muss dies für alle Veröffentlichungen ausgeführt werden ODER die Schritte werden auf einer einzigen Veröffentlichung durchgeführt und das Setup wird dann für die anderen geklont (mit den üblichen Vorsichtsmaßnahmen für das Klonen von AEM-Instanzen. sling.id muss hier auf etwas verweisen)

### Online-Neuindizierung für TarMK {#onlinere-indexingfortarmk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestore).

Dies ist die Methode, die vor der Einführung der neuen Indizierungsfunktionen von oak-run.jar angewendet wurde. Sie kann verwendet werden, indem für den Oak-Index die Eigenschaft `reindex=true` festlegt wird.

Dieser Ansatz kann verwendet werden, wenn die Auswirkungen auf die Dauer und die Performance für den Kunden akzeptabel sind. Dies ist häufig bei kleinen und mittleren AEM-Installationen der Fall.

![6](assets/6.png)

### Online-Neuindizierung von TarMK mit oak-run.jar {#onlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung - SegmentNodeStore - Die AEM-Instanz wird ausgeführt](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoretheaeminstanceisrunning).

Die Online-Neuindizierung von TarMK mit oak-run.jar ist schneller als die oben beschriebene Online-Neuindizierung für TarMK. Sie muss jedoch ebenfalls während eines Wartungsfensters ausgeführt werden, wobei das Fenster kürzer ist und für die Neuindizierung mehr Schritte erforderlich sind.

>[!NOTE]
>
>Vorgänge, bei denen sich AEM in einem Wartungsfenster befinden muss, sind orange dargestellt.

![7](assets/7.png)

### Offline-Neuindizierung von TarMK mit oak-run.jar {#offlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung - SegmentNodeStore - Die AEM-Instanz muss ausgeschaltet sein](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoreaeminstanceisdown).

Die Offline-Neuindizierung von TarMK ist der einfachste auf `oak-run.jar` basierende Neuindizierung sansatz für TarMK, da nur ein einziger `oak-run.jar`-Befehl erforderlich ist. Die AEM-Instanz muss jedoch heruntergefahren werden.

>[!NOTE]
>
>Vorgänge, bei denen AEM heruntergefahren sein muss, sind rot dargestellt.

![8](assets/8.png)

### Out-of-Band-Neuindizierung von TarMK mit oak-run.jar  {#out-of-bandre-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Out-of-Band-Neuindizierung - SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#outofbandreindexsegmentnodestore).

Die Out-of-Band-Neuindizierung minimiert die Auswirkung der Neuindizierung auf verwendete AEM-Instanzen.

>[!NOTE]
>
>Vorgänge, bei denen AEM heruntergefahren sein muss, sind rot dargestellt.

![9](assets/9.png)

## Aktualisieren von Indexdefinitionen {#updatingindexingdefinitions}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Anwendungsfall 4 - Aktualisieren von Indexdefinitionen](/help/sites-deploying/oak-run-indexing-usecases.md#usecase4updatingindexdefinitions).

### Erstellen und Aktualisieren von Indexdefinitionen auf TarMK mit ACS Ensure Index {#creatingandupdatingindexdefinitionsontarmkusingacsensureindex}

>[!NOTE]
>
>ACS Ensure Index ist ein Community-Projekt, das nicht vom Adobe-Support unterstützt wird.

Es ermöglicht das Versenden der Indexdefinition über ein Inhaltspaket, das später zu einer Neuindizierung führt, indem für das Neuindizierungs-Flag `true` festgelegt wird. Dies funktioniert für kleinere Setups, bei denen die Neuindizierung nicht viel Zeit in Anspruch nimmt.

Weitere Informationen finden Sie in der [Dokumentation zu ACS Ensure Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html).

### Erstellen und Aktualisieren von Indexdefinitionen auf TarMK mit oak-run.jar {#creatingandupdatingindexdefinitionsontarmkusingoak-run-jar}

Wenn die Dauer der Neuindizierung oder die Auswirkung auf die Performance bei Nicht-`oak-run.jar`-Methoden zu hoch ist, kann der folgende auf `oak-run.jar` basierende Ansatz genutzt werden, um Lucene-Indexdefinitionen in eine TarMK-basierte AEM-Installation zu importieren und neu zu indizieren.

![10](assets/10.png)

### Erstellen und Aktualisieren von Indexdefinitionen auf MongoMK mit oak-run.jar {#creatingandupdatingindexdefinitionsonmonogmkusingoak-run-jar}

Wenn die Dauer der Neuindizierung oder die Auswirkung auf die Performance bei Nicht-`oak-run.jar`-Methoden zu hoch ist, kann der folgende auf `oak-run.jar` basierende Ansatz genutzt werden, um Lucene-Indexdefinitionen in eine MongoMK-basierte AEM-Installation zu importieren und neu zu indizieren.

![11](assets/11.png)

