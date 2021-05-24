---
title: 'Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor '
seo-title: 'Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor '
description: Erfahren Sie, wie Sie mit dem Musterdetektor die Komplexität der Aktualisierung bewerten können.
seo-description: Erfahren Sie, wie Sie mit dem Musterdetektor die Komplexität der Aktualisierung bewerten können.
uuid: 84d0add9-3123-4188-9877-758911b1899f
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: b5607343-a13b-4520-a771-f1a555bfcc7b
docset: aem65
feature: Aktualisieren
exl-id: c42373e9-712e-4c11-adbb-4e3626e0b217
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 89%

---

# Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor 

## Überblick {#overview}

Mit dieser Funktion können Sie prüfen, ob vorhandene AEM-Instanzen aktualisiert werden können, indem Sie verwendete Muster ermitteln, die:

1. gegen bestimmte Regeln verstoßen und Bereiche betreffen, die durch das Upgrade überschrieben werden
1. Verwenden Sie eine AEM 6.x-Funktion oder eine API, die mit AEM 6.5 nicht abwärtskompatibel ist und nach dem Upgrade möglicherweise abbrechen kann.

Dies kann als Bewertungsgrundlage für den erforderlichen Entwicklungsaufwand bei der Aktualisierung auf AEM 6.5 dienen.

## Einrichtung {#how-to-set-up}

Der Musterdetektor wird als separates [Paket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/compatpack/pd-all-aem65) veröffentlicht, das mit allen Quell-AEM-Versionen von 6.1 bis 6.5 funktioniert, die auf AEM 6.5 aktualisiert werden sollen. Er kann mit dem [Package Manager](/help/sites-administering/package-manager.md) installiert werden.

## Verwendung {#how-to-use}

>[!NOTE]
>
>Der Musterdetektor kann in jeder beliebigen Umgebung, einschließlich lokaler Entwicklungsinstanzen, ausgeführt werden. Jedoch gilt:
>
>* Um die Erkennungsrate zu erhöhen,
>* vermeiden Sie jede Verlangsamung bei geschäftskritischen Instanzen.

>
>
Gleichzeitig wird die Ausführung in **Staging-Umgebungen** empfohlen, die hinsichtlich Benutzerapplikationen, Inhalt und Konfigurationen den Produktionsumgebungen möglichst stark ähneln.

Sie haben verschiedene Möglichkeiten, das Ergebnis des Musterdetektors zu prüfen: 

* **Über die Felix Inventory-Konsole:** 

1. Navigieren Sie zur AEM Web-Konsole, indem Sie zu *https://serveraddress:serverport/system/console/configMgr* navigieren.
1. Wählen Sie **Status - Musterdetektor** aus, wie im Bild unten dargestellt:

   ![screen-shot-2018-2-5pattern-detektor](assets/screenshot-2018-2-5pattern-detector.png)

* **Über eine auf reaktivem Text basierende oder die reguläre JSON-Schnittstelle** 
* **Über eine reaktive JSON-Zeilen-Oberfläche generiert **das in jeder Zeile ein separates JSON-Dokument.

Beide Methoden werden im Folgenden erläutert:

## Reaktive Schnittstelle  {#reactive-interface}

Mit einer reaktiven Schnittstelle kann der Bericht zu den Verstößen verarbeitet werden, sobald ein Problem erkannt wird.

Die Ausgabe ist zurzeit unter 2 URLs verfügbar:

1. Nur-Text-Schnittstelle 
1. JSON-Schnittstelle

## Handhabung der Nur-Text-Schnittstelle  {#handling-the-plain-text-interface}

Die in der Ausgabe enthaltenen Informationen sind als Serie von Ereigniseinträgen formatiert. Es gibt zwei Kanäle - einen für die Veröffentlichung von Verstößen und einen zweiten für die Veröffentlichung des aktuellen Fortschritts.

Sie können mit den folgenden Befehlen abgerufen werden:

```shell
curl -Nsu 'admin:admin' https://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep SUSPICION
```

Die Ausgabe sieht folgendermaßen aus:

```
2018-02-13T14:18:32.071+01:00 [SUSPICION] The pattern=ECU/extraneous.content.usage was found by detector=ContentAccessDetector with id=a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f message="Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid". More info at=https://www.adobe.com/go/aem6_EC
```

Der Fortschritt kann mit dem Befehl `grep` gefiltert werden:

```shell
curl -Nsu 'admin:admin' https://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep PROGRESS
```

Dies führt zur folgenden Ausgabe:

```
2018-02-13T14:19:26.909+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.5), analysed=45780/16 MB items, found=0 suspicions so far in period=PT5.005S (throughput=34667 items/sec)
2018-02-13T14:19:31.904+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.5), analysed=106050/39 MB items, found=0 suspicions so far in period=PT10S (throughput=23378 items/sec)
2018-02-13T14:19:35.685+01:00 [PROGRESS] Finished in period=PT13.782
```

## Behandlung der JSON-Schnittstelle  {#handling-the-json-interface}

JSON kann auf ähnliche Weise mit dem Tool [jq](https://stedolan.github.io/jq/) verarbeitet werden, sobald die Veröffentlichung erfolgt ist.

```shell
curl -Nsu 'admin:admin' https://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == true)'
```

Mit der Ausgabe:

```
{
  "timestamp": "2018-02-13T14:20:18.894+01:00",
  "suspicion": true,
  "pattern": {
    "code": "ECU",
    "type": "extraneous.content.usage",
    "detective": "ContentAccessDetector",
    "moreInfo": "https://www.adobe.com/go/aem6_ECU"
  },
  "item": {
    "id": "a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f",
    "message": "Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid"
  }
}
```

Der Fortschritt wird alle 5 Sekunden gemeldet und kann unter Ausschluss der anderen, nicht verdächtigen Benachrichtigungen abgerufen werden:

```shell
curl -Nsu 'admin:admin' https://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == false)'
```

Mit der Ausgabe:

```
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:17.279+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.5"
    ]
  },
  "state": {
    "itemsAnalysed": 57209,
    "itemsAnalysedSize": "26 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT5.003S",
    "elapsedTimeMilliseconds": 5003,
    "itemsPerSecond": 36965
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:22.276+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.5"
    ]
  },
  "state": {
    "itemsAnalysed": 113194,
    "itemsAnalysedSize": "46 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT10S",
    "elapsedTimeMilliseconds": 10000,
    "itemsPerSecond": 24092
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:25.762+01:00",
  "type": "FINISHED",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.5"
    ]
  },
  "state": {
    "itemsAnalysed": 140744,
    "itemsAnalysedSize": "63 MB",
    "suspicionsFound": 1
  },
  "progress": {
    "elapsedTime": "PT13.486S",
    "elapsedTimeMilliseconds": 13486,
    "itemsPerSecond": 19907
  }
}
{
  "suspicion": false,
  "type": "SUMMARY",
  "suspicionsFound": 1,
  "totalTime": "PT13.487S"
}
```

>[!NOTE]
>
>Es empfiehlt sich, die gesamte Ausgabe aus Curl in der Datei zu speichern und diese dann über `jq` oder `grep` zu verarbeiten, um einen Informationstyp zu filtern.

## Erkennungsbereich {#scope}

Aktuell bietet der Musterdetektor folgende Überprüfungen:

* Zwischen den Exporten und Importen von OSGi-Bundles kommt es zu Ungleichgewichten.
* Überverwendung von Sling-Ressourcentypen und -Supertypen (mit Überlagerung von Suchpfadinhalten)
* Definitionen von Oak-Indizes (Kompatibilität)
* VLT-Pakete (Überverwendung)
* Kompatibilität von rep:User-Knoten (im Kontext der OAuth-Konfiguration)

>[!NOTE]
>
>Bitte beachten Sie, dass der Musterdetektor versucht, die Warnungen für die Aktualisierung genau vorherzusagen. Allerdings generiert er möglicherweise in einigen Fällen falsche Positivergebnisse.
