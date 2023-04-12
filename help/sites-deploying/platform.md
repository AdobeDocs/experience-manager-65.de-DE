---
title: Einführung in die AEM-Plattform
seo-title: Introduction to the AEM Platform
description: Dieser Artikel bietet einen allgemeinen Überblick über die AEM Plattform und ihre wichtigsten Komponenten.
seo-description: This article provides a general overview of the AEM platform and its most important components.
uuid: 214d4c49-1f5c-432c-a2c0-c1fbdceee716
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: fccf9a0f-ebab-45ab-8460-84c86b3c4192
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/introduction-to-oak
exl-id: 8ee5f4ff-648d-45ea-a51e-894cd4385e62
source-git-commit: 2981f11565db957fac323f81014af83cab2c0a12
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 45%

---

# Einführung in die AEM-Plattform{#introduction-to-the-aem-platform}

Die AEM-Plattform in AEM 6 basiert auf Apache Jackrabbit Oak.

Apache Jackrabbit Oak implementiert ein skalierbares und leistungsstarkes, hierarchisches Inhalts-Repository, das als Grundlage für moderne, erstklassige Websites und andere anspruchsvolle Inhaltsanwendungen dienen soll.

Es handelt sich hierbei um die Nachfolgeversion von Jackrabbit 2 und die Lösung wird von AEM 6 als Standard-Backend für dessen Inhalts-Repository, CRX, verwendet.

## Designrichtlinien und -ziele {#design-principles-and-goals}

Oak implementiert die [JSR-283](https://jcp.org/en/jsr/detail?id=283)-Spezifikation (JCR 2.0). Hauptziele sind:

* Bessere Unterstützung für große Repositorys
* Mehrere verteilte Clusterknoten für hohe Verfügbarkeit
* Bessere Leistung
* Unterstützung für eine Vielzahl von untergeordneten Knoten und Zugriffssteuerungsebenen

## Architekturkonzept {#architecture-concept}

![chlimage_1-84](assets/chlimage_1-84.png)

### Speicherung {#storage}

Die Speicherschicht hat folgenden Zweck:

* Baummodell implementieren
* Speicher als Plug-in einrichten
* Bereitstellung eines Clustering-Mechanismus

### Oak Core {#oak-core}

Der Oak-Kern fügt mehrere Ebenen zur Speicherschicht hinzu:

* Zugriffsstufenkontrollen
* Suche und Indizierung
* Beobachrung

### Oak JCR {#oak-jcr}

Das Hauptziel des Oak-JCR besteht darin, die JCR-Semantik in Strukturvorgängen zu transformieren. Darüber hinaus erfüllt es folgende Zwecke:

* Implementieren der JCR-API
* Enthält Commit-Hooks, die JCR-Einschränkungen implementieren

Darüber hinaus sind jetzt nicht-Java-basierte Implementierungen möglich, die Teil des Oak-JCR-Konzepts bilden.

## Speicherübersicht {#storage-overview}

Die Oak-Speicherschicht bietet eine Abstraktionsebene für die tatsächliche Speicherung des Inhalts.

Derzeit stehen in AEM 6 zwei Speicher zur Verfügung: der **TAR-Speicher** und der **MongoDB-Speicher**.

### Tar-Speicher {#tar-storage}

Der TAR-Speicher nutzt TAR-Dateien. Er speichert Inhalte als unterschiedliche Datensätze innerhalb größerer Segmente. Journale werden verwendet, um den aktuellen Status des Repositorys zu verfolgen.

Es wurden mehrere grundlegende Designprinzipien entwickelt:

* **Unveränderliche Segmente**

Der Inhalt wird in Segmenten gespeichert, die bis zu 256 KB groß sein können. Sie sind unveränderlich, sodass häufig genutzte Segmente problemlos zwischengespeichert und Systemfehler vermieden werden, die das Repository beschädigen können.

Jedes Segment wird durch einen eindeutigen Bezeichner (Unique Identifier, UUID) identifiziert und enthält eine kontinuierliche Teilmenge der Inhaltsstruktur. Darüber hinaus können Segmente andere Inhalte referenzieren. Jedes Segment verwaltet eine Liste von UUIDs anderer referenzierter Segmente.

* **Lokalität**

Verwandte Datensätze wie einen Knoten und seine unmittelbar untergeordneten Elemente werden im selben Segment gespeichert. Dadurch wird die Suche nach dem Repository beschleunigt und die meisten Cache-Fehler für typische Clients vermieden, die auf mehr als einen zugehörigen Knoten pro Sitzung zugreifen.

* **Kompaktheit**

Die Formatierung von Datensätzen ist für die Größe optimiert, um IO-Kosten zu reduzieren und so viel Inhalt wie möglich in Caches zu integrieren.

### Mongo-Speicher {#mongo-storage}

Der MongoDB-Speicher verwendet MongoDB für Sharding und Clustering. Die Repository-Struktur wird in einer MongoDB-Datenbank gespeichert, wobei jeder Knoten ein separates Dokument ist.

Sie weist mehrere Besonderheiten auf:

* Revisionen

Bei jeder Aktualisierung (Commit) von Inhalten wird eine neue Revision erstellt. Eine Revision ist im Grunde eine Zeichenfolge, die aus drei Elementen besteht:

1. Ein Zeitstempel, der von der Systemzeit des Geräts abgeleitet wird, auf dem er generiert wurde
1. Ein Zähler, der Revisionen unterscheidet, die mit demselben Zeitstempel erstellt wurden
1. Die Clusterknoten-ID, unter der die Revision erstellt wurde

* Zweige

Verzweigungen werden unterstützt, die es dem Client ermöglichen, mehrere Änderungen zu testen und sie mit einem einzigen Zusammenführungsaufruf sichtbar zu machen.

* Frühere Dokumente

Der MongoDB-Speicher fügt bei jeder Änderung Daten zu einem Dokument hinzu. Daten werden jedoch nur gelöscht, wenn explizit eine Bereinigung ausgelöst wird. Alte Daten werden verschoben, wenn ein bestimmter Grenzwert erreicht wird. Frühere Dokumente enthalten nur unveränderliche Daten, d. h. sie enthalten nur übergebene und zusammengeführte Revisionen.

* Clusterknotenmetadaten

Daten zu aktiven und inaktiven Clusterknoten werden in der Datenbank gespeichert, um Cluster-Vorgänge zu erleichtern.

Eine typische AEM-Clusterkonfiguration mit MongoDB-Speicher:

![chlimage_1-85](assets/chlimage_1-85.png)

## Was unterscheidet sich von Jackrabbit 2? {#what-is-different-from-jackrabbit}

Da Oak abwärtskompatibel mit dem JCR 1.0-Standard ist, gibt es fast keine Änderungen auf Benutzerebene. Es gibt jedoch einige merkliche Unterschiede, die Sie beim Einrichten einer Oak-basierten AEM-Installation berücksichtigen müssen:

* Indizes in Oak werden nicht automatisch erstellt. Daher müssen bei Bedarf benutzerdefinierte Indizes erstellt werden.
* Im Gegensatz zu Jackrabbit 2, bei dem Sitzungen immer den aktuellen Status des Repositorys angegeben, zeigen Oak-Sitzungen eine unveränderte Ansicht des Repositorys zum Zeitpunkt, an dem die Sitzung erfasst wurde. Der Grund dafür ist das MVCC-Modell, auf dem Oak basiert.
* Same Name Siblings (SNS), d. h. untergeordnete Elemente mit demselben Namen, werden in Oak nicht unterstützt.

## Weitere plattformbezogene Dokumentation {#other-platform-related-documentation}

Weitere Informationen zur AEM Plattform finden Sie in den folgenden Artikeln:

* [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](/help/sites-deploying/data-store-config.md)
* [Oak-Abfragen und Indizierung](/help/sites-deploying/queries-and-indexing.md)
* [Speicherelemente in AEM 6](/help/sites-deploying/storage-elements-in-aem-6.md)
* [AEM mit MongoDB](/help/sites-deploying/aem-with-mongodb.md)
