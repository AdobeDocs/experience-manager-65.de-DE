---
title: Einführung in die AEM-Plattform
description: Erfahren Sie mehr über die AEM-Plattform und ihre wichtigsten Komponenten, einschließlich der Installation und Bereitstellung von Adobe Experience Manager 6.5 und der zugehörigen Architektur sowie der Cloud-Implementierung mit Adobe Managed Services.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/introduction-to-oak
exl-id: 8ee5f4ff-648d-45ea-a51e-894cd4385e62
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 100%

---


# Einführung in die AEM-Plattform{#introduction-to-the-aem-platform}

Die AEM-Plattform in AEM 6 basiert auf Apache Jackrabbit Oak.

Apache Jackrabbit Oak implementiert ein skalierbares und leistungsstarkes, hierarchisches Inhalts-Repository, das als Grundlage für moderne, erstklassige Websites und andere anspruchsvolle Inhaltsanwendungen dienen soll.

Es handelt sich hierbei um die Nachfolgeversion von Jackrabbit 2 und die Lösung wird von AEM 6 als Standard-Backend für dessen Inhalts-Repository, CRX, verwendet.

## Designrichtlinien und -ziele {#design-principles-and-goals}

Oak implementiert die [JSR-283](https://jcp.org/en/jsr/detail?id=283)-Spezifikation (JCR 2.0). Die Hauptziele des Designs sind:

* Bessere Unterstützung für große Repositorys
* Mehrere verteilte Cluster-Knoten für hohe Verfügbarkeit
* Bessere Leistung
* Unterstützung für eine Vielzahl von untergeordneten Knoten und Zugriffssteuerungsebenen

## Architekturkonzept {#architecture-concept}

![chlimage_1-84](assets/chlimage_1-84.png)

### Speicherung {#storage}

Die Speicherschicht hat folgenden Zweck:

* Implementieren des Baumstrukturmodells
* Möglichkeit, Speicher anzuschließen
* Bereitstellung eines Clustering-Mechanismus

### Oak Core {#oak-core}

Der Oak Core fügt mehrere Ebenen zur Speicherschicht hinzu:

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

Es gibt mehrere wichtige Design-Prinzipien, um die herum das System aufgebaut wurde:

* **Unveränderliche Segmente**

Der Inhalt wird in Segmenten gespeichert, die bis zu 256 KB groß sein können. Sie sind unveränderlich, sodass häufig genutzte Segmente problemlos zwischengespeichert und Systemfehler vermieden werden, die das Repository beschädigen können.

Jedes Segment wird durch einen eindeutigen Bezeichner (Unique Identifier, UUID) identifiziert und enthält eine kontinuierliche Teilmenge der Inhaltsstruktur. Darüber hinaus können Segmente andere Inhalte referenzieren. Jedes Segment verwaltet eine Liste von UUIDs anderer referenzierter Segmente.

* **Lokalität**

Verwandte Datensätze wie etwa ein Knoten und dessen unmittelbare, untergeordnete Elemente werden normalerweise im selben Segment gespeichert. Dadurch wird die Suche nach dem Repository beschleunigt, und es werden die meisten Cache-Fehler für typische Clients vermieden, die auf mehr als einen zugehörigen Knoten pro Sitzung zugreifen.

* **Kompaktheit**

Die Formatierung von Datensätzen ist für die Größe optimiert, um E/A-Kosten zu reduzieren und so viel Inhalt wie möglich in Caches zu integrieren.

### Mongo-Speicher {#mongo-storage}

Der MongoDB-Speicher nutzt MongoDB für Sharding und Clustering. Die Repository-Struktur wird in einer MongoDB-Datenbank gespeichert, wobei jeder Knoten ein separates Dokument ist.

Sie weist mehrere Besonderheiten auf:

* Revisionen

Bei jeder Aktualisierung (Commit) von Inhalten wird eine neue Revision erstellt. Eine Revision ist im Grunde eine Zeichenfolge, die aus drei Elementen besteht:

1. Ein Zeitstempel, der von der Systemzeit des Geräts abgeleitet wird, auf dem er generiert wurde
1. Ein Zähler, der Revisionen unterscheidet, die mit demselben Zeitstempel erstellt wurden
1. Die ID des Clusterknotens, unter dem die Revision erstellt wurde

* Verzweigungen

Verzweigungen werden unterstützt, was es dem Client ermöglicht, mehrfache Änderungen zu testen und sie mit einem einzigen Zusammenführungsaufruf sichtbar zu machen.

* Frühere Dokumente

Der MongoDB-Speicher fügt bei jeder Änderung Daten zu einem Dokument hinzu. Daten werden jedoch nur gelöscht, wenn explizit eine Bereinigung ausgelöst wird. Alte Daten werden verschoben, wenn ein bestimmter Grenzwert erreicht wird. Frühere Dokumente enthalten nur unveränderliche Daten, d. h. sie enthalten nur übergebene und zusammengeführte Revisionen.

* Metadaten des Cluster-Knotens

Daten zu aktiven und inaktiven Cluster-Knoten werden in der Datenbank gespeichert, um Cluster-Vorgänge zu erleichtern.

Eine typische AEM-Clusterkonfiguration mit MongoDB-Speicher:

![chlimage_1-85](assets/chlimage_1-85.png)

## Was unterscheidet sich von Jackrabbit 2? {#what-is-different-from-jackrabbit}

Da Oak abwärtskompatibel mit dem JCR 1.0-Standard ist, gibt es auf Benutzerebene fast keine Änderungen. Es gibt jedoch einige merkliche Unterschiede, die Sie beim Einrichten einer Oak-basierten AEM-Installation berücksichtigen müssen:

* Indizes in Oak werden nicht automatisch erstellt. Daher müssen bei Bedarf benutzerdefinierte Indizes erstellt werden.
* Im Gegensatz zu Jackrabbit 2, wo Sitzungen immer den aktuellen Status des Repositorys angegeben, zeigen Oak-Sitzungen eine unveränderte Ansicht des Repositorys zum Zeitpunkt, an dem die Sitzung erfasst wurde. Der Grund dafür ist das MVCC-Modell, auf dem Oak basiert.
* Same Name Siblings (SNS), d. h. untergeordnete Elemente mit demselben Namen, werden in Oak nicht unterstützt.

## Weitere plattformbezogene Dokumentation {#other-platform-related-documentation}

Weitere Informationen zur AEM-Plattform finden Sie in den folgenden Artikeln:

* [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](/help/sites-deploying/data-store-config.md)
* [Oak-Abfragen und Indizierung](/help/sites-deploying/queries-and-indexing.md)
* [Speicherelemente in AEM 6](/help/sites-deploying/storage-elements-in-aem-6.md)
* [AEM mit MongoDB](/help/sites-deploying/aem-with-mongodb.md)
