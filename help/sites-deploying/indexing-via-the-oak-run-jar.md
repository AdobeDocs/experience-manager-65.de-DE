---
title: Indizieren mit dem Oak-run JAR
description: Erfahren Sie, wie Sie die Indizierung mit dem Oak-run JAR durchführen.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: dcec8c1b-13cc-486c-b1a4-62e6eb3184ad
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 100%

---

# Indizieren mit dem Oak-run JAR {#indexing-via-the-oak-run-jar}

Oak-run unterstützt alle Indizierungsszenarien über die Befehlszeile und muss nicht auf der JMX-Ebene ausgeführt werden.  Vorteile des Oak-run-Ansatzes:

1. Bietet ein neues Toolset zur Indizierung für AEM 6.4.
1. Verringert die für die Neuindizierung erforderliche Zeit, was bei größeren Repositorys von Vorteil ist.
1. Verringert den Ressourcenverbrauch während der Neuindizierung in AEM, was die Systemleistung für andere AEM-Aktivitäten verbessert.
1. Oak-run bietet bandexternen Support: Wenn die Produktionsbedingungen keine Ausführung der Neuindizierung auf Produktionsinstanzen erlauben, kann für die Neuindizierung eine geklonte Umgebung genutzt werden, um eine kritische Leistungsbeeinträchtigung zu vermeiden.

Nachstehend finden Sie eine Liste von Anwendungsfällen, die Sie bei der Durchführung von Indizierungen mit dem Tool `oak-run` nutzen können.

## Prüfung der Indexkonsistenz {#indexconsistencychecks}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Nutzungsszenario 1 - Prüfung der Indexkonsistenz](/help/sites-deploying/oak-run-indexing-usecases.md#usercase1indexconsistencycheck).

* `oak-run.jar` ermittelt schnell, ob Lucene Oak-Indizes beschädigt sind.
* Es kann problemlos auf einer verwendeten AEM-Instanz ausgeführt werden, um die Konsistenz auf den Ebenen 1 und 2 zu prüfen.

![Prüfung der Indexkonsistenz](assets/screen_shot_2017-12-14at135758.png)

## Indexstatistiken {#indexstatistics}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Nutzungsszenario 2 - Indexstatistiken](/help/sites-deploying/oak-run-indexing-usecases.md#usecase2indexstatistics) 

* `oak-run.jar` speichert alle Indexdefinitionen, wichtige Indexstatistiken und Indexinhalte für Offline-Analysen.
* Kann problemlos auf einer verwendeten AEM-Instanz ausgeführt werden.

![image2017-12-19_9-47-40](assets/image2017-12-19_9-47-40.png)

## Entscheidungsdiagramm für den Ansatz zur Neuindizierung {#reindexingapproachdecisiontree}

Dieses Diagramm ist eine Entscheidungsbaumstruktur für die Verwendung der verschiedenen Neuindizierungsansätze.

![oak_-_reindexingwithoak-run](assets/oak_-_reindexingwithoak-run.png)

## Neuindizierung von MongoMK/RDMBMK {#reindexingmongomk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Nutzungsszenario 3 - Neuindizierung](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing).

### Textvorextraktion für SegmentNodeStore und DocumentNodeStore {#textpre-extraction}

Die [Textvorextraktion](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-perform-text-pre-extraction) (eine Funktion, die mit AEM 6.3 eingeführt wurde) kann genutzt werden, um die Zeit für die Neuindizierung zu verkürzen. Die Textvorextraktion kann mit allen Neuindizierungsansätzen verwendet werden.

Abhängig vom `oak-run.jar`-Indizierungsansatz, müssen, wie im Diagramm unten dargestellt, auf beiden Seiten des Schrittes zur Durchführung der Neuindizierung verschiedene Schritte ausgeführt werden.

![Textvorextraktion für SegmentNodeStore und DocumentNodeStore](assets/4.png)

>[!NOTE]
>
>Aktivitäten, bei denen sich AEM in einem Wartungsfenster befinden muss, sind orangefarben dargestellt.

### Online-Neuindizierung für MongoMK oder RDBMK mit oak-run.jar {#onlinere-indexingformongomk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Neuindizieren – DocumentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexdocumentnodestore).

Dies ist die empfohlene Methode für die Neuindizierung von AEM-Installationen mit MongoMK (und RDBMK).  Wenden Sie keine andere Methode an.

Führen Sie diesen Prozess nur für eine einzelne AEM-Instanz im Cluster aus.

![Online-Neuindizierung für MongoMK oder RDBMK mit oak-run.jar](assets/5.png)

## Neuindizierung von TarMK {#re-indexingtarmk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Neuindizieren – SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexsegmentnodestore).

* **Überlegungen zu Cold-Standby (TarMK)**

   * Es gibt keine besonderen Überlegungen zum Cold-Standby. Die Cold-Standby-Instanzen synchronisieren Änderungen wie üblich.

* **AEM-Veröffentlichungsfarmen (AEM-Veröffentlichungsfarmen müssen immer TarMK-Veröffentlichungsfarmen sein)**

   * Für eine Veröffentlichungsfarm muss dies für alle Veröffentlichungen ausgeführt werden, ODER die Schritte müssen für eine einzelne Veröffentlichung ausgeführt werden. Klonen Sie anschließend das Setup für andere (unter Berücksichtigung aller üblichen Vorsichtsmaßnahmen beim Klonen von AEM Instanzen; sling.id sollte hier auf etwas verweisen).

### Online-Neuindizierung für TarMK {#onlinere-indexingfortarmk}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung – SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestore).

Dies ist die Methode, die vor der Einführung der neuen Indizierungsfunktionen von oak-run.jar angewendet wurde. Sie kann verwendet werden, indem für den Oak-Index die Eigenschaft `reindex=true` festlegt wird.

Dieser Ansatz kann verwendet werden, wenn die Auswirkungen auf die Dauer und die Performance für die Kundin bzw. den Kunden akzeptabel sind.  Dies ist häufig bei kleinen und mittleren AEM-Installationen der Fall.

![Online-Neuindizierung für TarMK](assets/6.png)

### Online-Neuindizierung von TarMK mit oak-run.jar {#onlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung - SegmentNodeStore - Die AEM-Instanz wird ausgeführt](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoretheaeminstanceisrunning).

Die Online-Neuindizierung von TarMK mithilfe von oak-run.jar ist schneller als die oben beschriebene [Online-Neuindizierung für TarMK](#onlinere-indexingfortarmk). Sie muss jedoch ebenfalls während eines Wartungsfensters ausgeführt werden, wobei das Zeitfenster kleiner ist und für die Neuindizierung mehr Schritte erforderlich sind.

>[!NOTE]
>
>Vorgänge, bei denen sich AEM in einem Wartungsfenster befinden muss, sind orange dargestellt.

![Online-Neuindizierung von TarMK mit oak-run.jar](assets/7.png)

### Offline-Neuindizierung von TarMK mit oak-run.jar {#offlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Online-Neuindizierung – SegmentNodeStore – Die AEM-Instanz ist heruntergefahren](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoreaeminstanceisdown).

Die Offline-Neuindizierung von TarMK ist der einfachste auf `oak-run.jar` basierende Neuindizierungsansatz für TarMK, da nur ein einziger `oak-run.jar`-Befehl erforderlich ist. Die AEM-Instanz muss jedoch heruntergefahren werden.

>[!NOTE]
>
>Vorgänge, bei denen AEM heruntergefahren sein muss, sind rot dargestellt.

![Offline-Neuindizierung von TarMK mit oak-run.jar](assets/8.png)

### Out-of-Band-Neuindizierung von TarMK mit oak-run.jar  {#out-of-bandre-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Bandexterne Neuindizierung – SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#outofbandreindexsegmentnodestore).

Die Out-of-Band-Neuindizierung minimiert die Auswirkung der Neuindizierung auf verwendete AEM-Instanzen.

>[!NOTE]
>
>Vorgänge, bei denen AEM heruntergefahren sein muss, sind rot dargestellt.

![Out-of-Band-Neuindizierung von TarMK mit oak-run.jar](assets/9.png)

## Aktualisieren von Indexdefinitionen {#updatingindexingdefinitions}

>[!NOTE]
>
>Weitere Informationen zu diesem Szenario finden Sie unter [Nutzungsszenario 4 - Aktualisieren von Indexdefinitionen](/help/sites-deploying/oak-run-indexing-usecases.md#usecase4updatingindexdefinitions).

### Erstellen und Aktualisieren von Indexdefinitionen auf TarMK mit ACS Ensure Index {#creatingandupdatingindexdefinitionsontarmkusingacsensureindex}

>[!NOTE]
>
>ACS Ensure Index ist ein Community-Projekt, das nicht vom Adobe-Support unterstützt wird.

Es ermöglicht das Versenden der Indexdefinition über ein Inhaltspaket, das später zu einer Neuindizierung führt, indem für das Neuindizierungs-Flag der Wert `true` festgelegt wird. Dies funktioniert für kleinere Setups, bei denen die Neuindizierung nicht viel Zeit in Anspruch nimmt.

Weitere Informationen finden Sie in der [Dokumentation zu ACS Ensure Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html).

### Erstellen und Aktualisieren von Indexdefinitionen auf TarMK mit oak-run.jar {#creatingandupdatingindexdefinitionsontarmkusingoak-run-jar}

Wenn die Dauer der Neuindizierung oder die Auswirkung auf die Performance bei Nicht-`oak-run.jar`-Methoden zu hoch ist, kann der folgende auf `oak-run.jar` basierende Ansatz genutzt werden, um Lucene-Indexdefinitionen in eine TarMK-basierte AEM-Installation zu importieren und neu zu indizieren.

![Erstellen und Aktualisieren von Indexdefinitionen auf TarMK mit oak-run.jar](assets/10.png)

### Erstellen und Aktualisieren von Indexdefinitionen auf MongoMK mit oak-run.jar {#creatingandupdatingindexdefinitionsonmonogmkusingoak-run-jar}

Wenn die Dauer der Neuindizierung oder die Auswirkung auf die Performance bei Nicht-`oak-run.jar`-Methoden zu hoch ist, kann der folgende auf `oak-run.jar` basierende Ansatz genutzt werden, um Lucene-Indexdefinitionen in MongoMK-basierte AEM-Installationen zu importieren und neu zu indizieren.

![Erstellen und Aktualisieren von Indexdefinitionen auf MongoMK mit oak-run.jar](assets/11.png)
