---
title: Speicherressourcenanbieter - Übersicht
description: Erfahren Sie, wie Community-Inhalte, so genannte benutzergenerierte Inhalte (User-Generated Content, UGC), in einem einfachen, gemeinsamen Speicher gespeichert werden, der von einem Speicherressourcenanbieter (Storage Resource Provider, SRP) bereitgestellt wird.
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

# Speicherressourcenanbieter - Übersicht {#storage-resource-provider-overview}

## Einführung {#introduction}

Ab Adobe Experience Manager (AEM) Communities 6.1 werden Community-Inhalte, allgemein als benutzergenerierte Inhalte (User-Generated Content, UGC) bezeichnet, in einem einzigen, gemeinsamen Speicher gespeichert, der von einem [Speicherressourcenanbieter](working-with-srp.md) (SRP) bereitgestellt wird.

Es gibt mehrere SRP-Optionen, die alle über eine neue AEM Communities-Schnittstelle, die [SocialResourceProvider-API](srp-and-ugc.md) (SRP-API), auf UGC zugreifen. Diese umfasst alle CRUD-Vorgänge (Create, Read, Update, and Delete, Erstellen, Lesen, Aktualisieren und Löschen).

Alle SCF-Komponenten werden mithilfe der SRP-API implementiert, sodass der Code ohne Kenntnis der [zugrunde liegenden Topologie) oder ](topologies.md) Speicherort des UGC entwickelt werden kann.

***Die SocialResourceProvider-API steht nur lizenzierten AEM Communities-Kunden zur Verfügung.***

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Für lizenzierte AEM Communities-Kunden steht die SRP-API Entwicklern von benutzerdefinierten Komponenten für den Zugriff auf benutzergenerierte Inhalte unabhängig von der zugrunde liegenden Topologie zur Verfügung. Siehe [SRP und UGC Essentials](srp-and-ugc.md).

Siehe auch:

* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.

## Über das Repository {#about-the-repository}

Zum Verständnis von SRP ist es hilfreich, die Rolle des AEM-Repositorys (Oak) auf einer AEM-Community-Site zu verstehen.

**Java™ Content Repository (JCR)**
Dieser Standard definiert ein Datenmodell und eine Anwendungsprogrammierschnittstelle ([JCR-API](https://jackrabbit.apache.org/jcr/jcr-api.html)) für Inhalts-Repositorys. Es kombiniert die Eigenschaften herkömmlicher Dateisysteme mit denen relationaler Datenbanken und fügt einige zusätzliche Funktionen hinzu, die Content-Anwendungen häufig benötigen.

Eine Implementierung von JCR ist das AEM-Repository Oak.

**Apache Jackrabbit Oak**
[Oak](../../help/sites-deploying/platform.md) ist eine Implementierung von JCR 2.0, einem Datenspeicherungssystem, das für inhaltsorientierte Anwendungen entwickelt wurde. Es handelt sich dabei um eine Art hierarchischer Datenbank, die für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur den für den Benutzer sichtbaren Inhalt, sondern auch den gesamten Code, die Vorlagen und die internen Daten, die von der Anwendung verwendet werden. Die Benutzeroberfläche für den Zugriff auf Inhalte lautet [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Sowohl JCR als auch Oak werden normalerweise verwendet, um auf das AEM-Repository zu verweisen.

Nachdem Sie Site-Inhalte in der privaten Autorenumgebung entwickelt haben, müssen sie in die öffentliche Veröffentlichungsumgebung kopiert werden. Dies geschieht oft durch einen Vorgang namens *[Replikation](deploy-communities.md#replication-agents-on-author)*. Dies geschieht unter der Kontrolle des Autors/Entwicklers/Administrators.

Bei benutzergenerierten Inhalten wird der Inhalt von registrierten Site-Besuchern (Community-Mitgliedern) in der öffentlichen Veröffentlichungsumgebung eingegeben. Das passiert zufällig.

Für die Verwaltung und das Reporting ist es nützlich, von der privaten Autorenumgebung aus Zugriff auf den benutzergenerierten Inhalt zu haben. Mit SRP ist der Zugriff auf den benutzergenerierten Inhalt von der Autoreninstanz konsistenter und leistungsfähiger, da keine Rückwärtsreplikation von der Publish zur Autoreninstanz erforderlich ist.

## Über SRP {#about-srp}

Wenn benutzergenerierter Inhalt im freigegebenen Speicher gespeichert wird, gibt es eine einzige Instanz von Mitgliederinhalten, auf die in den meisten Bereitstellungen sowohl in der Autoren- als auch in der Veröffentlichungsumgebung zugegriffen werden kann. Unabhängig von der SRP-Auswahl (MSRP, ASRP, JSRP) muss über die SRP-API programmgesteuert auf alle zugegriffen werden.

>[!NOTE]
>
>Unter [SRP und UGC Essentials](srp-and-ugc.md) finden Sie Beispiel-Code und weitere Details.
>
>Best [ für die Programmierung finden Sie unter ](accessing-ugc-with-srp.md)Zugriff auf benutzergenerierten Inhalt mit SRP) .

### ASRP {#asrp}

Wenn ein ASRP vorhanden ist, wird der benutzergenerierte Inhalt (UGC) nicht im JCR gespeichert, sondern in einem Cloud-Service, der von Adobe gehostet und verwaltet wird. In ASRP gespeicherte benutzergenerierte Inhalte können möglicherweise nicht per CRXDE Lite angezeigt oder über die JCR-API aufgerufen werden.

Siehe [ASRP - Adobe Storage Resource Provider](asrp.md).

Entwickler können nicht direkt auf den benutzergenerierten Inhalt zugreifen.

ASRP verwendet Adobe-Cloud für Abfragen.

### MSRP {#msrp}

Ist dies der Fall, wird MSRP, UGC nicht in JCR gespeichert, sondern in MongoDB. In MSRP gespeicherte benutzergenerierte Inhalte können möglicherweise nicht per CRXDE Lite angezeigt oder über die JCR-API aufgerufen werden.

Siehe [MSRP - MongoDB Storage Resource Provider](msrp.md).

MSRP ist zwar mit ASRP vergleichbar, da alle AEM-Serverinstanzen auf denselben UGC zugreifen, es ist jedoch möglich, gängige Tools zu verwenden, um direkt auf den in MongoDB gespeicherten UGC zuzugreifen.

MSRP verwendet Solr für Abfragen.

### JSRP {#jsrp}

JSRP ist der Standardanbieter für den Zugriff auf alle benutzergenerierten Inhalte auf einer einzelnen AEM-Instanz. Dadurch können Sie AEM Communities 6.1 schnell erleben, ohne dass MSRP oder ASRP eingerichtet werden müssen.

Siehe [JSRP - JCR Storage Resource Provider](jsrp.md).

Wenn JSRP vorhanden ist, während UGC in JCR gespeichert ist, und auf ihn über die CRXDE Lite- und JCR-API zugegriffen werden kann, empfiehlt Adobe, niemals die JCR-API zu verwenden. In diesem Fall können zukünftige Änderungen benutzerdefinierten Code betreffen.

Außerdem wird das Repository für die Authoring- und Publish-Umgebungen nicht freigegeben. Während ein Cluster von Veröffentlichungsinstanzen zu einem gemeinsam genutzten Veröffentlichungs-Repository führt, ist der in Publish eingegebene benutzergenerierte Inhalt in der Autoreninstanz nicht sichtbar, sodass der benutzergenerierte Inhalt von der Autoreninstanz aus nicht verwaltet werden kann. UGC wird nur im AEM-Repository (JCR) der Instanz beibehalten, in der er eingegeben wurde.

JSRP verwendet die Oak-Indizes für Abfragen.

## Über Shadow-Knoten in JCR {#about-shadow-nodes-in-jcr}

Shadow-Knoten, die den Pfad zum UGC imitieren, existieren im lokalen Repository und dienen zwei Zwecken:

1. [Zugriffssteuerung (ACLs)](#for-access-control-acls)
1. [Nicht vorhandene Ressourcen (NER)](#for-non-existing-resources-ners)

Unabhängig von der SRP-Implementierung ist der eigentliche UGC *nicht* am selben Speicherort wie der Shadow-Knoten sichtbar.

### Für Zugriffssteuerung (ACLs) {#for-access-control-acls}

Einige SRP-Implementierungen wie ASRP und MSRP speichern Community-Inhalte in Datenbanken, die keine ACL-Verifizierung bieten. Schattenknoten bieten einen Speicherort im lokalen Repository, auf den ACLs angewendet werden können.

Mithilfe der SRP-API führen alle SRP-Optionen vor allen CRUD-Vorgängen dieselbe Prüfung des Shadow-Speicherorts durch.

Die ACL-Prüfung verwendet eine Dienstprogrammmethode, die einen Pfad zurückgibt, der zum Überprüfen der auf den UGC der Ressource angewendeten Berechtigungen geeignet ist.

Siehe [SRP und UGC ](srp-and-ugc.md) für Beispiel-Code.

### Für nicht vorhandene Ressourcen (NER) {#for-non-existing-resources-ners}

Einige Communities-Komponenten sind in einem Skript enthalten und erfordern daher einen Sling-adressierbaren Knoten, um Communities-Funktionen zu unterstützen. [Enthaltene Komponenten](scf.md#add-or-include-a-communities-component) werden als nicht vorhandene Ressourcen (NER) bezeichnet.

Shadow-Knoten bieten einen Sling-adressierbaren Speicherort im Repository.

>[!CAUTION]
>
>Da der Schattenknoten mehrmals verwendet wird, bedeutet das Vorhandensein eines Schattenknotens *nicht* dass die Komponente ein NER ist.

### Speicherort {#storage-location}

Im Folgenden finden Sie ein Beispiel für einen Shadow-Knoten unter Verwendung der [Comments](http://localhost:4502/content/community-components/en/comments.html)-Komponente [Community-Komponentenhandbuch](components-guide.md):

* Die Komponente ist im lokalen Repository unter folgender Adresse vorhanden:

  `/content/community-components/en/comments/jcr:content/content/includable/comments`

* Der entsprechende Shadow-Knoten ist im lokalen Repository unter vorhanden:

  `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

Unter dem Shadow-Knoten wurde kein benutzergenerierter Inhalt (UGC) gefunden.

Das Standardverhalten ist das Einrichten von Shadow-Knoten in einer Veröffentlichungsinstanz, wenn für einen Lese- oder Schreibvorgang auf den relevanten Unterbaum verwiesen wird.

Angenommen, die Bereitstellung erfolgt [MSRP](msrp.md) mit einer TarMK-Veröffentlichungsfarm.

Wenn ein [Mitglied](users.md) UGC auf pub1 (gespeichert in MongoDB) postet, werden in JCR auf pub1 Schattenknoten erstellt.

Wenn der UGC zum ersten Mal auf pub2 gelesen wird und nichts eingerichtet ist, besteht das Standardverhalten darin, die Shadow-Knoten zu erstellen.

Wenn ein anderes als das Standardverhalten gewünscht wird, muss es auf der Autoreninstanz eingerichtet und an alle Veröffentlichungsinstanzen weitergeleitet werden, was in der Regel ein manueller Prozess ist.
