---
title: SRP - Community-Inhaltsspeicher
description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte in einem einzigen, gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: e29aae44-67be-43d2-8004-c986412d9e63
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 0%

---

# SRP - Community-Inhaltsspeicher {#srp-community-content-storage}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden benutzergenerierte Inhalte in einem einzigen, gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird. Es gibt mehrere SRP-Optionen, aus denen Sie wählen können, z. B. ASRP, MSRP und JSRP.

Im Gegensatz zu früheren Versionen gibt es keine Rückwärts-/Vorwärtsreplikation von UGC über AEM-Instanzen hinweg. Stattdessen ermöglicht der SRP den direkten Zugriff auf den benutzergenerierten Inhalt für CRUD-Vorgänge (Create, Read, Update, and Delete, Erstellen, Lesen, Aktualisieren und Löschen) von allen Autoren- und Veröffentlichungsinstanzen, mit Ausnahme von JSRP.

Nachstehend sind die [Merkmale jeder SRP-Option](#characteristics-of-srp-options) aufgeführt, die für den Entscheidungsprozess bei der Auswahl des geeigneten SRP und der [&#x200B; Bereitstellung von entscheidender Bedeutung &#x200B;](/help/communities/topologies.md).

Einzelheiten zur Verwendung von SRP für UGC finden Sie unter [Speicherressourcenanbieter - Übersicht](/help/communities/srp.md).

>[!NOTE]
>
>SRP gilt nur für Community-Inhalte. Dies hat keine Auswirkungen darauf, wo Site-Inhalte gespeichert werden [Knotenspeicher](/help/sites-deploying/data-store-config.md) und es hat keine Auswirkungen auf die sichere Handhabung von Benutzerregistrierung, Benutzerprofilen und Benutzergruppen zwischen AEM-Instanzen (siehe auch [Verwalten von Benutzerdaten](#managing-user-data)).

>[!CAUTION]
>
>Ab AEM 6.1 wird [UGC nie repliziert](#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen gemeinsamen Speicher enthält, z. B. die standardmäßige [JSRP](/help/communities/topologies.md#jsrp)-Topologie, ist der benutzergenerierte Inhalt (UGC) nur in der AEM-Veröffentlichungs- oder -Autoreninstanz sichtbar, in der er eingegeben wurde. Nur wenn die Topologie einen Veröffentlichungs-Cluster enthält, ist der UGC in jeder Veröffentlichungsinstanz sichtbar.

## Merkmale der SRP-Optionen {#characteristics-of-srp-options}

[ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)

Mit dieser Option wird der benutzergenerierte Inhalt (UGC) remote in einem Cloud-Service gespeichert, der von Adobe gehostet und verwaltet wird. Sie erfordert eine zusätzliche Lizenz und arbeitet mit einem Kontovertreter zusammen, um das Konto für diese spezifische Lizenz bereitzustellen. ASRP erfordert:

* Ein zugehöriger Cloud-Service, der von Adobe zum Speichern von Community-Inhalten bereitgestellt und unterstützt wird.
* Auswahl eines Rechenzentrums in einer bestimmten Region (USA, EMEA, APAC)

* Der gesamte programmgesteuerte Zugriff auf benutzergenerierte Inhalte kann über die SRP-API erfolgen.

ASRP ist geeignet:

* Für die TarMK-Veröffentlichungsfarm.
* Wenn keine Absicht besteht, in lokalen Speicher zu investieren.

>[!NOTE]
>
>Es gibt eine Grenze für das Hochladen von Anhängen zu Beiträgen (oder Kommentaren) in ASRP, die 50 MB beträgt.

[MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)

Mit dieser Option wird der benutzergenerierte Inhalt (UGC) direkt in einer lokalen MongoDB-Instanz gespeichert.

MSRP erfordert:

* Eine lokale, lizenzierte Installation von MongoDB zum Speichern von Community-Inhalten.
* Eine lokale Installation von Apache Solr.
* Der gesamte programmgesteuerte Zugriff auf benutzergenerierte Inhalte kann über die SRP-API erfolgen.

ASRP ist geeignet:

* Für eine vorhandene TarMK-Veröffentlichungsfarm.
* Für einen MongoMK- oder RdbMK-Cluster.
* Wenn große Mengen an Community-Inhalten erwartet werden.

[DSRP - Relationaler Datenbankspeicher-Ressourcenanbieter](/help/communities/dsrp.md)

Mit dieser Option wird der benutzergenerierte Inhalt (UGC) direkt in einer lokalen MySQL-Datenbankinstanz gespeichert.

DSRP erfordert:

* Eine lokale Installation von MySQL zum Speichern von Community-Inhalten.
* Eine lokale Installation von Apache Solr.
* Der gesamte programmgesteuerte Zugriff auf benutzergenerierte Inhalte kann über die SRP-API erfolgen.

DSRP ist geeignet:

* Für eine vorhandene TarMK-Veröffentlichungsfarm.
* Für einen MongoMK- oder RdbMK-Cluster.
* Wenn große Mengen an Community-Inhalten erwartet werden.

[JSRP - JCR-Speicherressourcenanbieter](/help/communities/jsrp.md)

Bei der Standardoption gibt es keinen gemeinsamen Speicher. Der UGC wird nur im selben JCR-Repository wie die AEM-Instanz beibehalten, in der er eingegeben wurde.

JSRP:

* Speichert Community-Inhalte im JCR-Repository der AEM-Autoren- oder Veröffentlichungsinstanz, an die sie gesendet wurden.
* Erfordert, dass der gesamte programmgesteuerte Zugriff auf den benutzergenerierten Inhalt über die SRP-API erfolgt.
* Erfordert einen Veröffentlichungs-Cluster, wenn mehrere Veröffentlichungsinstanzen bereitgestellt werden (es gibt keinen Replikationsmechanismus zwischen Veröffentlichungsinstanzen in einer TarMK-Farm).
* Die Moderation wird nur in der Veröffentlichungsumgebung durchgeführt (es gibt keinen Reverse-/Forward-Replikationsmechanismus zwischen Autor und Veröffentlichung).
* Optimiert für Entwicklung, Demonstrationen und Schulungen.

## Konfigurieren von SRP {#configuring-srp}

Die Angabe der standardmäßigen Speicheroption basierend auf der zugrunde liegenden Bereitstellung erfolgt über die [Speicherkonfigurationskonsole](/help/communities/srp-config.md).

Konfigurationsdetails der einzelnen Optionen finden Sie unter:

* [ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)
* [MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)
* [DSRP - Relationaler Datenbankspeicher-Ressourcenanbieter](/help/communities/dsrp.md)
* [JSRP - JCR-Speicherressourcenanbieter](/help/communities/jsrp.md)

Wenn keine Speicheroption aktiv ausgewählt ist, ist JSRP standardmäßig aktiviert.

## Zusätzliche Informationen {#additional-information}

### UGC nie repliziert {#ugc-never-replicated}

In der Autorenumgebung erstellt ein Autor Seiteninhalte und repliziert diese in der Veröffentlichungsumgebung. Wenn eine Seite eine interaktive AEM Communities-Funktion enthält, z. B. Kommentare, Reviews, Foren, Blogs oder QnA, führt die Interaktion von Mitgliedern (angemeldeten Site-Besuchern) in einer Veröffentlichungsinstanz dazu, dass benutzergenerierte Inhalte in die Veröffentlichungsumgebung eingegeben werden.

Zuvor wurden diese Community-Inhalte umgekehrt von der Autoreninstanz auf die Veröffentlichungsinstanz und von der Autoreninstanz auf die Veröffentlichungsinstanz repliziert. Es war problematisch, die Konsistenz zwischen AEM-Instanzen bei der Rückwärts- und Vorwärtsreplikation zu gewährleisten.

Ab AEM Communities 6.1 ist die Replikation von benutzergenerierten Inhalten nicht mehr erforderlich, da für benutzergenerierten Inhalt wie oben beschrieben gemeinsam genutzter Speicher verwendet wird.

Während Site-Inhalte repliziert werden, werden benutzergenerierte Inhalte nie repliziert.

### Verwalten von Benutzerdaten {#managing-user-data}

Von Interesse für Communities sind auch [*Benutzer*, *Benutzergruppen* und *Benutzerprofile*](/help/communities/users.md). Wenn diese benutzerbezogenen Daten in der Veröffentlichungsumgebung erstellt und aktualisiert werden, müssen sie für andere Veröffentlichungsinstanzen verfügbar gemacht werden, wenn die Topologie eine [Veröffentlichungsfarm“ &#x200B;](/help/sites-deploying/recommended-deploys.md#tarmk-farm).

Ab AEM Communities 6.1 werden benutzerbezogene Daten mithilfe einer Sling-Verteilung und nicht mithilfe einer Replikation synchronisiert. Weitere Informationen finden Sie unter [Benutzersynchronisierung](/help/communities/sync.md).

### Aktualisieren auf AEM Communities 6.5 {#upgrading-to-aem-communities}

Wenn beim Upgrade auf AEM 6.5 Communities bereits vorhandene benutzergenerierte Inhalte beibehalten werden müssen, sollten Schritte unternommen werden, je nachdem, ob die AEM 5.6.1- oder AEM 6.0-Community Adobe-On-Demand-Speicher oder On-Premise-Speicher von benutzergenerierten Inhalten verwendet hat.

Weitere Informationen finden Sie unter [Aktualisieren auf AEM Communities 6.5](/help/communities/upgrade.md).
