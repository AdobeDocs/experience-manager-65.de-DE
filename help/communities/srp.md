---
title: Übersicht über den Speicher-Ressourcen-Provider
seo-title: Übersicht über den Speicher-Ressourcen-Provider
description: Gemeinsame Lagerhaltung für Gemeinschaften
seo-description: Gemeinsame Lagerhaltung für Gemeinschaften
uuid: abdf4e5a-767b-428f-9aa4-0dc06819a26e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 63abeda4-6ea1-4b45-b188-f9c6b44ca0cd
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Übersicht über den Speicher-Ressourcen-Provider {#storage-resource-provider-overview}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden Community-Inhalte, häufig auch als benutzergenerierte Inhalte bezeichnet, in einem einzigen gemeinsamen Speicher gespeichert, der von einem [Speicherressourcenanbieter](working-with-srp.md) (SRP) bereitgestellt wird.

Es gibt mehrere SRP-Optionen, die alle über eine neue AEM Communities-Schnittstelle auf UGC zugreifen, die [SocialResourceProvider API](srp-and-ugc.md) (SRP API), die alle Vorgänge zum Erstellen, Lesen, Aktualisieren und Löschen (CRUD) umfasst.

Alle SCF-Komponenten werden mithilfe der SRP-API implementiert, sodass Code ohne Kenntnis der [zugrunde liegenden Topologie](topologies.md) oder des Standorts von UGC entwickelt werden kann.

***Die SocialResourceProvider-API steht nur lizenzierten Kunden von AEM Communities zur Verfügung.***

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Für lizenzierte Kunden von AEM Communities steht die SRP-API Entwicklern von benutzerdefinierten Komponenten zum Zugriff auf UGC ohne Rücksicht auf die zugrunde liegende Topologie zur Verfügung. Siehe [SRP und UGC Essentials](srp-and-ugc.md).

Siehe auch:

* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Coding-Richtlinien
* [SocialUtils Refactoring](socialutils.md) - Zuordnen von nicht mehr unterstützten Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden

## Info zum Repository {#about-the-repository}

Zum Verständnis von SRP ist es hilfreich, die Rolle des AEM-Repositorys (OAK) auf einer AEM-Community-Site zu verstehen.

**Java Content Repository (JCR)** Dieser Standard definiert ein Datenmodell und eine Anwendungsprogrammierschnittstelle ([JCR-API](https://jackrabbit.apache.org/jcr/jcr-api.html)) für Content Repositories. Es kombiniert Eigenschaften herkömmlicher Dateisysteme mit denen relationaler Datenbanken und bietet eine Reihe zusätzlicher Funktionen, die Content-Anwendungen oft benötigen.

Eine Implementierung von JCR ist das AEM-Repository, OAK.

**Apache Jackrabbit Oak (OAK)**[OAK](../../help/sites-deploying/platform.md) ist eine Implementierung von JCR 2.0, einem Datenspeichersystem, das speziell für inhaltsorientierte Anwendungen entwickelt wurde. Es handelt sich um eine Art hierarchischer Datenbank, die für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur die benutzerseitigen Inhalte, sondern auch alle durch die Anwendung verwendeten Codes, Vorlagen und internen Daten. Die Benutzeroberfläche für den Zugriff auf Inhalte ist [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Sowohl JCR als auch OAK werden normalerweise verwendet, um auf das AEM-Repository zu verweisen.

Nach der Entwicklung von Site-Inhalten in der privaten Autorenumgebung muss diese in die öffentliche Veröffentlichungsumgebung kopiert werden. Dies geschieht oft durch einen Vorgang, der als *[Replikation](deploy-communities.md#replication-agents-on-author)*bezeichnet wird. Dies geschieht unter der Kontrolle des Autors/Entwicklers/Administrators.

Bei UGC wird der Inhalt von registrierten Site-Besuchern (Community-Mitgliedern) in der öffentlichen Veröffentlichungsumgebung eingegeben. Das passiert zufällig.

Für die Verwaltung und Berichterstellung ist es nützlich, Zugriff auf UGC aus der privaten Autorenumgebung zu haben. Mit SRP ist der Zugriff auf UGC vom Autor konsistenter und leistungsfähiger, da eine umgekehrte Replizierung von der Veröffentlichung zum Autor nicht erforderlich ist.

## Informationen zu SRP {#about-srp}

Wenn UGC im gemeinsamen Speicher gespeichert wird, gibt es eine Instanz von Mitgliederinhalten, auf die in den meisten Bereitstellungen sowohl von der Autor- als auch von der Veröffentlichungsumgebung zugegriffen werden kann. Unabhängig von der SRP-Auswahl (MSRP, ASRP, JSRP) müssen alle programmgesteuert mit der SRP-API aufgerufen werden.

>[!NOTE]
>
>Siehe [SRP und UGC Essentials](srp-and-ugc.md) für Beispielcode und weitere Details.
>
>Unter [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) finden Sie Best Practices für das Kodieren.

### ASRP {#asrp}

Im Fall von ASRP wird UGC nicht in JCR gespeichert, sondern in einem Cloud-Dienst gespeichert, der von Adobe gehostet und verwaltet wird. In ASRP gespeicherte UGC können weder mit CRXDE Lite angezeigt werden noch mit der JCR-API aufgerufen werden.

Siehe [ASRP - Adobe Storage Resource Provider](asrp.md).

Es ist für Entwickler nicht möglich, direkt auf die UGC zuzugreifen.

ASRP nutzt Adobe Cloud für Abfragen.

### MSRP {#msrp}

Bei MSRP wird UGC nicht in JCR gespeichert, sondern in MongoDB. In MSRP gespeicherte UGC können weder mit CRXDE Lite angezeigt werden noch mit der JCR-API auf sie zugegriffen werden.

See [MSRP - MongoDB Storage Resource Provider](msrp.md).

Während MSRP mit ASRP vergleichbar ist, da alle AEM-Serverinstanzen auf dasselbe UGC zugreifen, ist es möglich, allgemeine Tools zu verwenden, um direkt auf die in MongoDB gespeicherte UGC zuzugreifen.

MSRP verwendet Solr für Abfragen.

### JSRP {#jsrp}

JSRP ist der Standardanbieter für den Zugriff auf alle UGC in einer AEM-Instanz. Es bietet die Möglichkeit, AEM Communities 6.1 schnell zu erleben, ohne dass MSRP oder ASRP eingerichtet werden müssen.

Siehe [JSRP - JCR Storage Resource Provider](jsrp.md).

Im Fall von JSRP wird, während UGC in JCR gespeichert ist und sowohl über CRXDE Lite- als auch über die JCR-API auf sie zugegriffen werden kann, dringend empfohlen, dass JCR-API nie dazu verwendet wird. Andernfalls können zukünftige Änderungen den benutzerdefinierten Code betreffen.

Außerdem wird das Repository für die Autor- und Veröffentlichungsumgebung nicht freigegeben. Während ein Cluster aus Instanzen im Veröffentlichungsmodus zu einem Repository im freigegebenen Veröffentlichungsmodus führt, ist beim Autor kein im Veröffentlichungsmodus eingegebener UGC sichtbar, sodass keine Möglichkeit besteht, UGC vom Autor zu verwalten. UGC wird nur im AEM-Repository (JCR) der Instanz beibehalten, in der es eingegeben wurde.

JSRP verwendet die Oak-Indizes für Abfragen.

## Über Schattenknoten in JCR {#about-shadow-nodes-in-jcr}

Shadow-Knoten, die den Pfad zu UGC imitieren, befinden sich im lokalen Repository, um zwei Zwecke zu erfüllen:

1. [Zugriffssteuerung (ACLs](#for-access-control-acls))
1. [Nicht vorhandene Ressourcen (NERs)](#for-non-existing-resources-ners)

Unabhängig von der SRP-Implementierung wird der tatsächliche UGC *nicht *am selben Ort wie der Shadow-Knoten sichtbar sein.

### Für Zugriffssteuerung (ACLs) {#for-access-control-acls}

Einige SRP-Implementierungen wie ASRP und MSRP speichern Community-Inhalte in Datenbanken, die keine ACL-Überprüfung bieten. Shadow-Knoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Bei Verwendung der SRP-API werden alle SRP-Optionen vor allen CRUD-Vorgängen an der Position des Schattens überprüft.

Die ACL-Prüfung verwendet eine Dienstprogrammmethode, die einen Pfad zurückgibt, der zur Überprüfung der Berechtigungen, die auf die UGC der Ressource angewendet werden, geeignet ist.

Beispielcode finden Sie unter [SRP und UGC Essentials](srp-and-ugc.md) .

### Für nicht vorhandene Ressourcen {#for-non-existing-resources-ners}

Einige Communities-Komponenten sind innerhalb eines Skripts inklusiv und benötigen daher einen Sling-adressierbaren Knoten, um Communities-Funktionen zu unterstützen. [Einbezogene Komponenten](scf.md#add-or-include-a-communities-component) werden als nicht vorhandene Ressourcen bezeichnet.

Shadow-Knoten bieten einen adressierbaren Sling-Speicherort im Repository.

>[!CAUTION]
>
>Da der Shadow-Knoten mehrere Verwendungen hat, bedeutet das Vorhandensein eines Shadow-Knotens *nicht* , dass die Komponente ein NER ist.

### Speicherort {#storage-location}

Im Folgenden finden Sie ein Beispiel für einen Shadow-Knoten mit der Komponente [Comments](http://localhost:4502/content/community-components/en/comments.html) im [Community-Komponentenleitfaden](components-guide.md):

* Die Komponente befindet sich im lokalen Repository unter:

   /content/community-components/de/comments/jcr:content/content/einschließlich/comments

* Der entsprechende Shadow-Knoten befindet sich im lokalen Repository unter:

   /content/usergenerated/content/community-components/de/comments/jcr:content/content/einschließlich/comments

Unter dem Schattenknoten wird kein UGC gefunden.

Das Standardverhalten besteht darin, Schattenknoten in einer Veröffentlichungsinstanz einzurichten, wenn auf die relevante Unterstruktur für Lese- oder Schreibvorgänge verwiesen wird.

Angenommen, die Bereitstellung ist [MSRP](msrp.md) mit einer TarMK-Veröffentlichungsfarm.

Wenn ein [Mitglied](users.md) UGC auf pub1 veröffentlicht (in MongoDB gespeichert), werden Schattenknoten in JCR auf pub1 erstellt.

Wenn das UGC zum ersten Mal auf pub2 gelesen wird und nichts eingerichtet ist, wird standardmäßig das Erstellen der Shadow-Knoten verwendet.

Wenn Sie ein anderes als das Standardverhalten wünschen, muss es in der Autoreninstanz eingerichtet und für alle Veröffentlichungsinstanzen weitergeleitet werden, was normalerweise ein manueller Prozess ist.
