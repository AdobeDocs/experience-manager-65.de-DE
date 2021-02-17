---
title: Übersicht über den Datenspeicherung Resource Provider
seo-title: Übersicht über den Datenspeicherung Resource Provider
description: Gemeinsame Datenspeicherung für Gemeinschaften
seo-description: Gemeinsame Datenspeicherung für Gemeinschaften
uuid: abdf4e5a-767b-428f-9aa4-0dc06819a26e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 63abeda4-6ea1-4b45-b188-f9c6b44ca0cd
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 2%

---


# Übersicht über den Datenspeicherung Resource Provider{#storage-resource-provider-overview}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden Community-Inhalte, die gemeinhin als benutzergenerierte Inhalte (UGC) bezeichnet werden, in einem gemeinsamen Speicher gespeichert, der von einem [Datenspeicherung Resource Provider](working-with-srp.md) (SRP) bereitgestellt wird.

Es gibt mehrere SRP-Optionen, die alle über eine neue AEM Communities-Schnittstelle auf UGC zugreifen, die [SocialResourceProvider-API](srp-and-ugc.md) (SRP-API), die alle Vorgänge zum Erstellen, Lesen, Aktualisieren und Löschen (CRUD) umfasst.

Alle SCF-Komponenten werden mithilfe der SRP-API implementiert, sodass Code ohne Kenntnis der [zugrunde liegenden Topologie](topologies.md) oder des Standorts von UGC entwickelt werden kann.

***Die SocialResourceProvider-API steht nur lizenzierten Kunden von AEM Communities zur Verfügung.***

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Für lizenzierte Kunden von AEM Communities steht die SRP-API Entwicklern von benutzerdefinierten Komponenten zur Verfügung, um ohne Rücksicht auf die zugrunde liegende Topologie auf UGC zugreifen zu können. Siehe [SRP und UGC Essentials](srp-and-ugc.md).

Siehe auch:

* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Coding-Richtlinien.
* [SocialUtils Refactoring](socialutils.md)  - Zuordnen von nicht mehr unterstützten Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

## Info zum Repository {#about-the-repository}

Um SRP zu verstehen, ist es hilfreich, die Rolle des AEM Repository (OAK) in einer AEM Community-Site zu verstehen.

**Java Content Repository (JCR)**
 Dieser Standard definiert ein Datenmodell und eine Anwendungsprogrammierschnittstelle ([JCR-API](https://jackrabbit.apache.org/jcr/jcr-api.html)) für Content-Repositorys. Es kombiniert Eigenschaften herkömmlicher Dateisysteme mit denen relationaler Datenbanken und bietet eine Reihe zusätzlicher Funktionen, die Content-Anwendungen oft benötigen.

Eine Implementierung von JCR ist das AEM Repository, OAK.

**Apache Jackrabbit Oak (OAK)**
[](../../help/sites-deploying/platform.md) OAK ist eine Implementierung von JCR 2.0, die ein Datensystem ist, das speziell für inhaltsorientierte Datenspeicherung entwickelt wurde. Es handelt sich um eine Art hierarchischer Datenbank, die für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur die benutzerseitigen Inhalte, sondern auch alle durch die Anwendung verwendeten Codes, Vorlagen und internen Daten. Die Benutzeroberfläche für den Zugriff auf Inhalte ist [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Sowohl JCR als auch OAK werden normalerweise dazu verwendet, auf das AEM Repository zu verweisen.

Nachdem Sie Site-Inhalte in der Umgebung für private Autoren entwickelt haben, müssen Sie sie in die Umgebung für öffentliche Veröffentlichungen kopieren. Dies geschieht oft durch einen Vorgang namens *[Replikation](deploy-communities.md#replication-agents-on-author)*. Dies geschieht unter der Kontrolle des Autors/Entwicklers/Administrators.

Für UGC wird der Inhalt von registrierten Site-Besuchern (Community-Mitgliedern) in der Umgebung zur Veröffentlichung eingegeben. Das passiert zufällig.

Für die Verwaltung und den Berichte ist es nützlich, von der Umgebung des Privatautors Zugriff auf UGC zu haben. Mit SRP ist der Zugriff auf UGC vom Autor konsistenter und leistungsfähiger, da eine umgekehrte Replizierung von der Veröffentlichung zum Autor nicht erforderlich ist.

## Über SRP {#about-srp}

Wenn UGC in einer freigegebenen Datenspeicherung gespeichert wird, gibt es eine Instanz von Mitgliederinhalten, auf die in den meisten Bereitstellungen sowohl von der Autor- als auch von der Veröffentlichungs-Umgebung zugegriffen werden kann. Unabhängig von der SRP-Auswahl (MSRP, ASRP, JSRP) müssen alle programmgesteuert mit der SRP-API aufgerufen werden.

>[!NOTE]
>
>Siehe [SRP und UGC Essentials](srp-and-ugc.md) für Beispielcode und weitere Details.
>
>Unter [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) finden Sie Best Practices beim Kodieren.

### ASRP {#asrp}

Bei ASRP wird UGC nicht in JCR gespeichert, sondern in einem Cloud-Dienst gespeichert, der von der Adobe gehostet und verwaltet wird. In ASRP gespeicherte UGC können weder mit CRXDE Lite angezeigt noch über die JCR-API aufgerufen werden.

Siehe [ASRP - Adobe Datenspeicherung Resource Provider](asrp.md).

Es ist für Entwickler nicht möglich, direkt auf die UGC zuzugreifen.

ASRP verwendet Adobe Cloud für Abfragen.

### MSRP {#msrp}

Bei MSRP wird UGC nicht in JCR gespeichert, sondern in MongoDB. In MSRP gespeicherte UGC können weder mit CRXDE Lite angezeigt noch über die JCR-API aufgerufen werden.

Siehe [MSRP - MongoDB Datenspeicherung Resource Provider](msrp.md).

Während MSRP mit ASRP vergleichbar ist, da alle AEM Serverinstanzen auf dasselbe UGC zugreifen, ist es möglich, allgemeine Tools zu verwenden, um direkt auf die in MongoDB gespeicherte UGC zuzugreifen.

MSRP verwendet Solr für Abfragen.

### JSRP {#jsrp}

JSRP ist der Standardanbieter für den Zugriff auf alle UGC in einer einzigen AEM. Es bietet die Möglichkeit, AEM Communities 6.1 schnell zu erleben, ohne MSRP oder ASRP einrichten zu müssen.

Siehe [JSRP - JCR Datenspeicherung Resource Provider](jsrp.md).

Im Falle von JSRP wird, während UGC in JCR gespeichert ist und sowohl über die CRXDE Lite- als auch über die JCR-API zugänglich ist, dringend empfohlen, dass JCR-API nie dazu verwendet wird. Andernfalls können sich zukünftige Änderungen auf benutzerdefinierten Code auswirken.

Darüber hinaus wird das Repository für die Autor- und Veröffentlichungs-Umgebung nicht freigegeben. Während ein Cluster aus Instanzen im Veröffentlichungsmodus zu einem Repository im freigegebenen Veröffentlichungsmodus führt, ist beim Autor kein im Veröffentlichungsmodus eingegebener UGC sichtbar, sodass keine Möglichkeit besteht, UGC vom Autor zu verwalten. UGC wird nur im AEM Repository (JCR) der Instanz beibehalten, in der es eingegeben wurde.

JSRP verwendet die Oak-Indizes für Abfragen.

## Über Schattenknoten in JCR {#about-shadow-nodes-in-jcr}

Shadow-Knoten, die den Pfad zu UGC imitieren, befinden sich im lokalen Repository, um zwei Zwecke zu erfüllen:

1. [Zugriffskontrolle (ACLs)](#for-access-control-acls)
1. [Nicht vorhandene Ressourcen (NERs)](#for-non-existing-resources-ners)

Unabhängig von der SRP-Implementierung wird der tatsächliche UGC *nicht *am selben Ort wie der Shadow-Knoten sichtbar sein.

### Für Zugriffskontrolle (ACLs) {#for-access-control-acls}

Einige SRP-Implementierungen, wie z. B. ASRP und MSRP, speichern Community-Inhalte in Datenbanken, die keine ACL-Verifizierung bieten. Shadow-Knoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Bei Verwendung der SRP-API werden alle SRP-Optionen vor allen CRUD-Vorgängen an der Position des Schattens überprüft.

Die ACL-Prüfung verwendet eine Dienstprogrammmethode, die einen Pfad zurückgibt, der zur Überprüfung der Berechtigungen, die auf die UGC der Ressource angewendet werden, geeignet ist.

Beispielcode finden Sie unter [SRP und UGC Essentials](srp-and-ugc.md).

### Für nicht vorhandene Ressourcen (NERs) {#for-non-existing-resources-ners}

Einige Communities-Komponenten sind innerhalb eines Skripts inklusiv und benötigen daher einen Sling-adressierbaren Knoten, um Communities-Funktionen zu unterstützen. [Einbezogene ](scf.md#add-or-include-a-communities-component) Komponenten werden als nicht vorhandene Ressourcen bezeichnet.

Shadow-Knoten bieten einen adressierbaren Sling-Speicherort im Repository.

>[!CAUTION]
>
>Da der Shadow-Knoten mehrere Verwendungen hat, impliziert das Vorhandensein eines Shadow-Knotens *nicht*, dass die Komponente ein NER ist.

### Speicherort der Datenspeicherung {#storage-location}

Im Folgenden finden Sie ein Beispiel für einen Schatten-Knoten, bei dem die Komponente [Kommentare](http://localhost:4502/content/community-components/en/comments.html) im [Community-Komponentenleitfaden](components-guide.md) verwendet wird:

* Die Komponente befindet sich im lokalen Repository unter:

   `/content/community-components/en/comments/jcr:content/content/includable/comments`

* Der entsprechende Shadow-Knoten befindet sich im lokalen Repository unter:

   `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

Unter dem Schattenknoten wird kein UGC gefunden.

Das Standardverhalten besteht darin, Schattenknoten in einer Veröffentlichungsinstanz einzurichten, wenn auf die relevante Unterstruktur für Lese- oder Schreibvorgänge verwiesen wird.

Angenommen, die Bereitstellung ist [MSRP](msrp.md) mit einer TarMK-Veröffentlichungsfarm.

Wenn ein [Member](users.md) UGC auf pub1 (in MongoDB gespeichert) postet, werden Schattenknoten in JCR auf pub1 erstellt.

Wenn das UGC zum ersten Mal auf pub2 gelesen wird und nichts eingerichtet ist, wird standardmäßig das Erstellen der Shadow-Knoten verwendet.

Wenn Sie ein anderes als das Standardverhalten wünschen, muss es in der Autoreninstanz eingerichtet und für alle Veröffentlichungsinstanzen weitergeleitet werden. Dies ist in der Regel ein manueller Prozess.
