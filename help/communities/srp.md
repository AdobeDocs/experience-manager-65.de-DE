---
title: Übersicht über den Speicheranbieter
seo-title: Übersicht über den Speicheranbieter
description: Gemeinsame Speicherung für Communities
seo-description: Gemeinsame Speicherung für Communities
uuid: abdf4e5a-767b-428f-9aa4-0dc06819a26e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 63abeda4-6ea1-4b45-b188-f9c6b44ca0cd
exl-id: 5f313274-1a2a-4e83-9289-60a4729b99b4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 2%

---

# Übersicht über den Speicheranbieter {#storage-resource-provider-overview}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden Community-Inhalte, häufig als benutzergenerierte Inhalte (UGC) bezeichnet, in einem einzigen, gemeinsamen Speicher gespeichert, der von einem [Speicherressourcenanbieter](working-with-srp.md) (SRP) bereitgestellt wird.

Es gibt mehrere SRP-Optionen, die alle über eine neue AEM Communities-Schnittstelle auf UGC zugreifen, die [SocialResourceProvider-API](srp-and-ugc.md) (SRP-API), die alle Vorgänge zum Erstellen, Lesen, Aktualisieren und Löschen (CRUD) umfasst.

Alle SCF-Komponenten werden mithilfe der SRP-API implementiert, sodass Code ohne Kenntnis der [zugrunde liegenden Topologie](topologies.md) oder des Standorts der UGC entwickelt werden kann.

***Die SocialResourceProvider-API steht nur lizenzierten Kunden von AEM Communities zur Verfügung.***

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Für lizenzierte Kunden von AEM Communities ist die SRP-API für Entwickler von benutzerdefinierten Komponenten verfügbar, um ungeachtet der zugrunde liegenden Topologie auf UGC zugreifen zu können. Siehe [SRP und UGC Essentials](srp-and-ugc.md).

Siehe auch:

* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md)  - Coding Guidelines.
* [SocialUtils-Refaktorierung](socialutils.md)  - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

## Über das Repository {#about-the-repository}

Um SRP zu verstehen, ist es hilfreich, die Rolle des AEM-Repositorys (OAK) auf einer AEM Community-Site zu verstehen.

**Java Content Repository (JCR)**
Dieser Standard definiert ein Datenmodell und eine Anwendungsprogrammierschnittstelle ([JCR-API](https://jackrabbit.apache.org/jcr/jcr-api.html)) für Inhalts-Repositorys. Es kombiniert die Eigenschaften herkömmlicher Dateisysteme mit denen relationaler Datenbanken und bietet eine Reihe zusätzlicher Funktionen, die Content-Anwendungen häufig benötigen.

Eine Implementierung von JCR ist das AEM Repository, OAK.

**Apache Jackrabbit Oak (OAK)**
[](../../help/sites-deploying/platform.md)  OAK ist eine Implementierung von JCR 2.0, einem Datenspeichersystem, das speziell für inhaltsorientierte Anwendungen entwickelt wurde. Es handelt sich um eine hierarchische Datenbank, die für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur die benutzerseitigen Inhalte, sondern auch alle durch die Anwendung verwendeten Codes, Vorlagen und internen Daten. Die Benutzeroberfläche für den Zugriff auf Inhalte ist [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Sowohl JCR als auch OAK werden normalerweise verwendet, um auf das AEM Repository zu verweisen.

Nachdem Sie Site-Inhalte in der privaten Autorenumgebung entwickelt haben, müssen Sie sie durch Kopieren in die öffentliche Veröffentlichungsumgebung kopieren. Dies geschieht oft durch einen Vorgang namens *[replication](deploy-communities.md#replication-agents-on-author)*. Dies geschieht unter der Kontrolle des Autors/Entwicklers/Administrators.

Für UGC wird der Inhalt von registrierten Site-Besuchern (Community-Mitgliedern) in der öffentlichen Veröffentlichungsumgebung eingegeben. Dies geschieht zufällig.

Für die Verwaltung und Berichterstellung ist es nützlich, von der privaten Autorenumgebung aus Zugriff auf UGC zu haben. Mit SRP ist der Zugriff auf UGC vom Autor konsistenter und leistungsfähiger, da die Rückwärtsreplikation von der Veröffentlichung zum Autor nicht erforderlich ist.

## Über SRP {#about-srp}

Wenn UGC im freigegebenen Speicher gespeichert wird, gibt es eine einzelne Instanz von Mitgliederinhalten, auf die in den meisten Bereitstellungen sowohl von der Autoren- als auch der Veröffentlichungsumgebung aus zugegriffen werden kann. Unabhängig von der SRP-Auswahl (MSRP, ASRP, JSRP) muss über die SRP-API programmgesteuert auf alle zugegriffen werden.

>[!NOTE]
>
>Unter [SRP und UGC Essentials](srp-and-ugc.md) finden Sie Beispielcode und weitere Details.
>
>Best Practices für die Kodierung finden Sie unter [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) .

### ASRP {#asrp}

Im Falle von ASRP wird UGC nicht in JCR gespeichert, sondern in einem Cloud-Service gespeichert, der von Adobe gehostet und verwaltet wird. In ASRP gespeicherte benutzergenerierte Inhalte können weder mit CRXDE Lite angezeigt noch mit der JCR-API aufgerufen werden.

Siehe [ASRP - Adobe Storage Resource Provider](asrp.md).

Entwickler können nicht direkt auf die UGC zugreifen.

ASRP verwendet Adobe Cloud für Abfragen.

### MSRP {#msrp}

Bei MSRP wird UGC nicht in JCR gespeichert, sondern in MongoDB. In MSRP gespeicherte benutzergenerierte Inhalte können weder mit CRXDE Lite angezeigt noch mit der JCR-API aufgerufen werden.

Siehe [MSRP - MongoDB Storage Resource Provider](msrp.md).

MSRP ist zwar mit ASRP vergleichbar, da alle AEM Serverinstanzen auf dieselbe UGC zugreifen, es ist jedoch möglich, allgemeine Tools zu verwenden, um direkt auf die in MongoDB gespeicherte UGC zuzugreifen.

MSRP verwendet Solr für Abfragen.

### JSRP {#jsrp}

JSRP ist der Standardanbieter für den Zugriff auf alle benutzergenerierten Inhalte auf einer einzigen AEM. Es bietet die Möglichkeit, AEM Communities 6.1 schnell zu erleben, ohne dass MSRP oder ASRP eingerichtet werden muss.

Siehe [JSRP - JCR Storage Resource Provider](jsrp.md).

Im Falle von JSRP wird während UGC in JCR gespeichert ist und sowohl über die CRXDE Lite- als auch die JCR-API zugänglich ist, dringend empfohlen, dafür niemals die JCR-API zu verwenden. Andernfalls können sich zukünftige Änderungen auf benutzerdefinierten Code auswirken.

Außerdem wird das Repository für die Autoren- und Veröffentlichungsumgebungen nicht freigegeben. Während ein Cluster von Veröffentlichungsinstanzen zu einem freigegebenen Veröffentlichungs-Repository führt, ist in der Veröffentlichungsinstanz eingegebener UGC nicht in der Autoreninstanz sichtbar, sodass keine Möglichkeit besteht, benutzergenerierte Inhalte von der Autoreninstanz aus zu verwalten. UGC wird nur im AEM-Repository (JCR) der Instanz beibehalten, in der es eingegeben wurde.

JSRP verwendet die Oak-Indizes für Abfragen.

## Über Shadow-Knoten in JCR {#about-shadow-nodes-in-jcr}

Shadow-Knoten, die den Pfad zu UGC imitieren, sind im lokalen Repository vorhanden und dienen zwei Zwecken:

1. [Zugriffskontrolle (ACLs)](#for-access-control-acls)
1. [Nicht vorhandene Ressourcen (NERs)](#for-non-existing-resources-ners)

Unabhängig von der SRP-Implementierung ist der tatsächliche UGC *nicht *am selben Speicherort wie der Shadow-Knoten sichtbar.

### Für Zugriffskontrolle (ACLs) {#for-access-control-acls}

Einige SRP-Implementierungen wie ASRP und MSRP speichern Community-Inhalte in Datenbanken, die keine ACL-Verifizierung bieten. Shadow-Knoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Mithilfe der SRP-API führen alle SRP-Optionen vor allen CRUD-Vorgängen dieselbe Prüfung der Shadow-Position durch.

Die ACL-Prüfung verwendet eine Dienstprogrammmethode, die einen Pfad zurückgibt, der zum Überprüfen der auf die UGC der Ressource angewendeten Berechtigungen geeignet ist.

Beispielcode finden Sie unter [SRP und UGC Essentials](srp-and-ugc.md) .

### Für nicht vorhandene Ressourcen (NERs) {#for-non-existing-resources-ners}

Einige Communities-Komponenten sind in einem Skript enthalten und erfordern daher einen adressierbaren Sling-Knoten, um Communities-Funktionen zu unterstützen. [Einbezogene ](scf.md#add-or-include-a-communities-component) Komponenten werden als nicht vorhandene Ressourcen (NERs) bezeichnet.

Shadow-Knoten bieten einen adressierbaren Sling-Speicherort im Repository.

>[!CAUTION]
>
>Da der Shadow-Knoten mehrere Verwendungen hat, impliziert das Vorhandensein eines Shadow-Knotens *nicht*, dass die Komponente ein NER ist.

### Speicherort {#storage-location}

Im Folgenden finden Sie ein Beispiel für einen Shadow-Knoten, der die [Kommentarkomponente](http://localhost:4502/content/community-components/en/comments.html) im [Community Components Guide](components-guide.md) verwendet:

* Die Komponente befindet sich im lokalen Repository unter:

   `/content/community-components/en/comments/jcr:content/content/includable/comments`

* Der entsprechende Shadow-Knoten existiert im lokalen Repository unter:

   `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

Unter dem Shadow-Knoten wird kein UGC gefunden.

Das Standardverhalten besteht darin, Shadow-Knoten in einer Veröffentlichungsinstanz einzurichten, wenn die relevante Unterstruktur für Lese- oder Schreibvorgänge referenziert wird.

Angenommen, die Bereitstellung ist [MSRP](msrp.md) mit einer TarMK-Veröffentlichungsfarm.

Wenn ein [member](users.md) UGC auf pub1 post (gespeichert in MongoDB), werden Shadow-Knoten in JCR auf pub1 erstellt.

Wenn das UGC zum ersten Mal in pub2 gelesen wird und nichts eingerichtet ist, besteht das Standardverhalten darin, die Shadow-Knoten zu erstellen.

Wenn andere als das Standardverhalten gewünscht werden, muss es in der Autoreninstanz eingerichtet und an alle Veröffentlichungsinstanzen weitergeleitet werden, was normalerweise ein manueller Prozess ist.
