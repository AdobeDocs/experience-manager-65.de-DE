---
title: Übersicht über den Speicheranbieter
description: Erfahren Sie, wie Community-Inhalte, auch als benutzergenerierte Inhalte (UGC) bezeichnet, in einem einfachen, gemeinsamen Speicher gespeichert werden, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 5f313274-1a2a-4e83-9289-60a4729b99b4
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 0%

---

# Übersicht über den Speicheranbieter {#storage-resource-provider-overview}

## Einführung {#introduction}

Ab Adobe Experience Manager (AEM) Communities 6.1 werden Community-Inhalte, häufig als benutzergenerierte Inhalte bezeichnet, in einem einzigen, gemeinsamen Speicher gespeichert, der von einem [Speicherressourcenanbieter](working-with-srp.md) (SRP).

Es gibt mehrere SRP-Optionen, die alle über eine neue AEM Communities-Oberfläche auf UGC zugreifen: [SocialResourceProvider-API](srp-and-ugc.md) (SRP-API), die alle CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) umfasst.

Alle SCF-Komponenten werden mithilfe der SRP-API implementiert, sodass Code ohne Kenntnis der [zugrunde liegende Topologie](topologies.md) oder Standort der UGC.

***Die SocialResourceProvider-API steht nur lizenzierten Kunden von AEM Communities zur Verfügung.***

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Für lizenzierte Kunden von AEM Communities steht die SRP-API Entwicklern benutzerdefinierter Komponenten für den Zugriff auf UGC zur Verfügung, unabhängig von der zugrunde liegenden Topologie. Siehe [Grundlagen zu SRP und UGC](srp-and-ugc.md).

Siehe auch:

* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Kodierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

## Über das Repository {#about-the-repository}

Um SRP zu verstehen, ist es hilfreich, die Rolle des AEM-Repositorys (Oak) auf einer AEM Community-Site zu verstehen.

**Java™ Content Repository (JCR)**
Dieser Standard definiert ein Datenmodell und eine Anwendungsprogrammierschnittstelle ([JCR-API](https://jackrabbit.apache.org/jcr/jcr-api.html)) für Inhalts-Repositorys. Es kombiniert die Eigenschaften herkömmlicher Dateisysteme mit denen von relationalen Datenbanken und fügt einige zusätzliche Funktionen hinzu, die Content-Anwendungen häufig benötigen.

Eine Implementierung von JCR ist das AEM Repository, Oak.

**Apache Jackrabbit Oak**
[Oak](../../help/sites-deploying/platform.md) ist eine Implementierung von JCR 2.0, einem Datenspeichersystem für inhaltsorientierte Anwendungen. Es handelt sich um eine hierarchische Datenbank, die für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur den für den Benutzer sichtbaren Inhalt, sondern auch alle von der Anwendung verwendeten Code, Vorlagen und internen Daten. Die Benutzeroberfläche für den Zugriff auf Inhalte lautet [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Sowohl JCR als auch Oak werden normalerweise verwendet, um auf das AEM Repository zu verweisen.

Nachdem Sie Site-Inhalte in der privaten Autorenumgebung entwickelt haben, müssen Sie sie in die öffentliche Veröffentlichungsumgebung kopieren. Dies geschieht oft durch einen Vorgang namens *[Replikation](deploy-communities.md#replication-agents-on-author)*. Dies geschieht unter der Kontrolle des Autors/Entwicklers/Administrators.

Für UGC wird der Inhalt von registrierten Site-Besuchern (Community-Mitgliedern) in der öffentlichen Veröffentlichungsumgebung eingegeben. Dies geschieht zufällig.

Für die Verwaltung und Berichterstellung ist es nützlich, von der privaten Autorenumgebung aus Zugriff auf UGC zu haben. Mit SRP ist der Zugriff auf UGC aus der Autoreninstanz konsistenter und leistungsfähiger, da die Rückwärtsreplikation von der Veröffentlichungs- zur Autoreninstanz nicht erforderlich ist.

## Über SRP {#about-srp}

Wenn UGC im freigegebenen Speicher gespeichert wird, gibt es eine einzelne Instanz von Mitgliederinhalten, auf die in den meisten Bereitstellungen sowohl von der Autoren- als auch der Veröffentlichungsumgebung aus zugegriffen werden kann. Unabhängig von der SRP-Auswahl (MSRP, ASRP, JSRP) muss über die SRP-API programmgesteuert auf alle zugegriffen werden.

>[!NOTE]
>
>Siehe [Grundlagen zu SRP und UGC](srp-and-ugc.md) für Beispielcode und zusätzliche Details.
>
>Siehe [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) für Best Practices beim Programmieren.

### ASRP {#asrp}

Wenn ASRP vorhanden ist, wird UGC nicht in JCR gespeichert, sondern in einem Cloud-Service gespeichert, der von Adobe gehostet und verwaltet wird. In ASRP gespeicherte benutzergenerierte Inhalte können unter Umständen nicht mit CRXDE Lite angezeigt oder mit der JCR-API aufgerufen werden.

Siehe [ASRP - Adobe Storage Resource Provider](asrp.md).

Entwickler können nicht direkt auf die UGC zugreifen.

ASRP verwendet Adobe-Cloud für Abfragen.

### MSRP {#msrp}

Wenn dies der Fall ist, wird MSRP, UGC nicht in JCR gespeichert, sondern in MongoDB gespeichert. In MSRP gespeicherte benutzergenerierte Inhalte können unter Umständen nicht mit CRXDE Lite angezeigt oder mit der JCR-API aufgerufen werden.

Siehe [MSRP - MongoDB Storage Resource Provider](msrp.md).

MSRP ist zwar mit ASRP vergleichbar, da alle AEM Serverinstanzen auf dieselbe UGC zugreifen, es ist jedoch möglich, allgemeine Tools zu verwenden, um direkt auf die in MongoDB gespeicherte UGC zuzugreifen.

MSRP verwendet Solr für Abfragen.

### JSRP {#jsrp}

JSRP ist der Standardanbieter für den Zugriff auf alle benutzergenerierten Inhalte auf einer einzigen AEM. Dadurch können Sie AEM Communities 6.1 schnell erleben, ohne MSRP oder ASRP einrichten zu müssen.

Siehe [JSRP - JCR Storage Resource Provider](jsrp.md).

Wenn JSRP vorhanden ist, während UGC in JCR gespeichert ist und er in der CRXDE Lite- und JCR-API verfügbar ist, empfiehlt Adobe, dazu niemals die JCR-API zu verwenden. Wenn Sie dies tun, können sich zukünftige Änderungen auf benutzerdefinierten Code auswirken.

Außerdem wird das Repository für die Autoren- und Veröffentlichungsumgebung nicht freigegeben. Während ein Cluster von Veröffentlichungsinstanzen zu einem freigegebenen Veröffentlichungs-Repository führt, ist in der Veröffentlichungsinstanz eingegebener benutzergenerierter Inhalt in der Autoreninstanz nicht sichtbar, sodass keine Möglichkeit besteht, benutzergenerierte Inhalte von der Autoreninstanz aus zu verwalten. UGC wird nur im AEM-Repository (JCR) der Instanz beibehalten, in der es eingegeben wurde.

JSRP verwendet die Oak-Indizes für Abfragen.

## Über Shadow-Knoten in JCR {#about-shadow-nodes-in-jcr}

Shadow-Knoten, die den Pfad zu UGC imitieren, sind im lokalen Repository vorhanden und dienen zwei Zwecken:

1. [Zugriffskontrolle (ACLs)](#for-access-control-acls)
1. [Nicht vorhandene Ressourcen (NERs)](#for-non-existing-resources-ners)

Unabhängig von der SRP-Implementierung lautet die tatsächliche UGC *not* an derselben Stelle wie der Shadow-Knoten angezeigt.

### Für Zugriffskontrolle (ACLs) {#for-access-control-acls}

Einige SRP-Implementierungen wie ASRP und MSRP speichern Community-Inhalte in Datenbanken, die keine ACL-Verifizierung bieten. Shadow-Knoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Mithilfe der SRP-API führen alle SRP-Optionen dieselbe Prüfung der Shadow-Position vor allen CRUD-Vorgängen durch.

Die ACL-Prüfung verwendet eine Dienstprogrammmethode, die einen Pfad zurückgibt, der zum Überprüfen der auf die UGC der Ressource angewendeten Berechtigungen geeignet ist.

Siehe [Grundlagen zu SRP und UGC](srp-and-ugc.md) für Beispielcode.

### Für nicht vorhandene Ressourcen (NER) {#for-non-existing-resources-ners}

Einige Communities-Komponenten sind in einem Skript enthalten und erfordern daher einen adressierbaren Sling-Knoten, um Communities-Funktionen zu unterstützen. [Enthaltene Komponenten](scf.md#add-or-include-a-communities-component) werden als nicht vorhandene Ressourcen (NER) bezeichnet.

Shadow-Knoten bieten einen adressierbaren Sling-Speicherort im Repository.

>[!CAUTION]
>
>Da der Shadow-Knoten mehrere Verwendungen hat, bewirkt das Vorhandensein eines Shadow-Knotens, dass *not* bedeutet, dass die Komponente ein NER ist.

### Speicherort {#storage-location}

Im Folgenden finden Sie ein Beispiel für einen Shadow-Knoten mit der [Kommentarkomponente](http://localhost:4502/content/community-components/en/comments.html) im [Handbuch zu Community-Komponenten](components-guide.md):

* Die Komponente befindet sich im lokalen Repository unter:

  `/content/community-components/en/comments/jcr:content/content/includable/comments`

* Der entsprechende Shadow-Knoten existiert im lokalen Repository unter:

  `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

Unter dem Shadow-Knoten wird kein UGC gefunden.

Das Standardverhalten besteht darin, Shadow-Knoten in einer Veröffentlichungsinstanz einzurichten, wenn die relevante Unterstruktur für Lese- oder Schreibvorgänge referenziert wird.

Angenommen, die Bereitstellung lautet [MSRP](msrp.md) mit einer TarMK-Veröffentlichungsfarm.

Wenn eine [Mitglied](users.md) postet UGC auf pub1 (gespeichert in MongoDB), werden Shadow-Knoten in JCR auf pub1 erstellt.

Wenn das UGC zum ersten Mal in pub2 gelesen wird und nichts eingerichtet ist, besteht das Standardverhalten darin, die Shadow-Knoten zu erstellen.

Wenn andere als das Standardverhalten gewünscht werden, muss es in der Autoreninstanz eingerichtet und an alle Veröffentlichungsinstanzen weitergeleitet werden, was normalerweise ein manueller Prozess ist.
