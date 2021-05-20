---
title: SRP - Community-Inhaltsspeicherung
seo-title: SRP - Community-Inhaltsspeicherung
description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte in einem einzigen, gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird
seo-description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte in einem einzigen, gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird
uuid: d45e03c4-378b-4510-a6a0-d48c8cb879d9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 6f13b21a-f4ef-4889-9b8e-4da3f846fa35
docset: aem65
role: Administrator
exl-id: e29aae44-67be-43d2-8004-c986412d9e63
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# SRP - Community-Inhaltsspeicher {#srp-community-content-storage}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem einzigen, gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird. Es gibt verschiedene SRP-Optionen, aus denen Sie wählen können, z. B. ASRP, MSRP und JSRP.

Im Gegensatz zu früheren Versionen gibt es keine Reverse/Forward-Replikation von UGC über AEM Instanzen hinweg. Stattdessen ermöglicht das SRP die direkte Zugänglichkeit von UGC für CRUD-Vorgänge (Create, Read, Update, Delete, Erstellen, Aktualisieren und Löschen) in allen Autoren- und Veröffentlichungsinstanzen, mit Ausnahme von JSRP.

Im Folgenden finden Sie die [Eigenschaften jeder SRP-Option](#characteristics-of-srp-options), die für den Entscheidungsprozess bei der Auswahl des geeigneten SRP und [zugrunde liegenden Bereitstellung](/help/communities/topologies.md) von entscheidender Bedeutung ist.

Weitere Informationen zur Verwendung von SRP für UGC finden Sie unter [Übersicht über den Speicheranbieter](/help/communities/srp.md).

>[!NOTE]
>
>SRP gilt nur für Community-Inhalte. Sie hat keine Auswirkungen auf den Speicherort des Site-Inhalts ([Knotenspeicher](/help/sites-deploying/data-store-config.md)) und hat keine Auswirkungen auf die sichere Verarbeitung von Benutzerregistrierung, Benutzerprofilen und Benutzergruppen zwischen AEM Instanzen (siehe auch [Verwalten von Benutzerdaten](#managing-user-data)).

>[!CAUTION]
>
>Ab AEM 6.1 wird [UGC nie repliziert](#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen gemeinsamen Speicher enthält, z. B. die standardmäßige Topologie [JSRP](/help/communities/topologies.md#jsrp), ist UGC nur in der AEM- oder Autoreninstanz sichtbar, in der sie eingegeben wurde. Nur wenn die Topologie einen Veröffentlichungs-Cluster enthält, ist der UGC in jeder Veröffentlichungsinstanz sichtbar.

## Eigenschaften der SRP-Optionen {#characteristics-of-srp-options}

[ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)

Mit dieser Option wird der benutzergenerierte Inhalt remote in einem von Adobe gehosteten und verwalteten Cloud-Service persistiert. Es erfordert eine zusätzliche Lizenz und die Zusammenarbeit mit einem Kundenbetreuer, um das Konto für diese spezifische Lizenz bereitzustellen. ASRP erfordert:

* Ein verknüpfter Cloud-Service, der von Adobe bereitgestellt und unterstützt wird, um Community-Inhalte zu speichern.
* Auswahl eines Rechenzentrums in einer bestimmten geografischen Region (USA, EMEA, APAC).

* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

ASRP ist geeignet:

* Für die TarMK-Veröffentlichungsfarm.
* Wenn keine Absicht besteht, in lokale Datenspeicherung zu investieren.

>[!NOTE]
>
>Das Hochladen von Anhängen zu Beiträgen (oder Kommentaren) in ASRP ist auf 50 MB beschränkt.

[MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)

Mit dieser Option wird der benutzergenerierte Inhalt direkt in einer lokalen MongoDB-Instanz beibehalten.

MSRP erfordert:

* Eine lokale, lizenzierte Installation von MongoDB zum Speichern von Community-Inhalten.
* Eine lokale Installation von Apache Solr.
* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

ASRP ist geeignet:

* Für eine vorhandene TarMK-Veröffentlichungsfarm.
* Für einen MongoMK- oder RdbMK-Cluster.
* Wenn große Mengen von Community-Inhalten erwartet werden.

[DSRP - Resource Provider für relationale Datenbankspeicher](/help/communities/dsrp.md)

Mit dieser Option wird der benutzergenerierte Inhalt direkt in einer lokalen MySQL-Datenbankinstanz beibehalten.

DSRP erfordert:

* Eine lokale Installation von MySQL zum Speichern von Community-Inhalten.
* Eine lokale Installation von Apache Solr.
* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

DSRP ist geeignet:

* Für eine vorhandene TarMK-Veröffentlichungsfarm.
* Für einen MongoMK- oder RdbMK-Cluster.
* Wenn große Mengen von Community-Inhalten erwartet werden.

[JSRP - JCR Storage Resource Provider](/help/communities/jsrp.md)

Mit der Standardoption gibt es keinen gemeinsamen Speicher. Der UGC wird nur im selben JCR-Repository beibehalten wie die AEM Instanz, in der er eingegeben wurde.

JSRP:

* Speichert Community-Inhalte im JCR-Repository der AEM Autoren- oder Veröffentlichungsinstanz, in der sie veröffentlicht wurde.
* Erfordert den gesamten programmatischen Zugriff auf UGC über die SRP-API.
* Erfordert einen Veröffentlichungscluster, wenn mehr als eine Veröffentlichungsinstanz bereitgestellt wird (es gibt keinen Replikationsmechanismus zwischen Veröffentlichungsinstanzen in einer TarMK-Farm).
* Die Moderation erfolgt nur in der Veröffentlichungsumgebung (es gibt keinen Rückwärts-/Vorwärts-Replikationsmechanismus zwischen Autor und Veröffentlichung).
* Ist am besten für Entwicklung, Demonstrationen und Schulung.

## Konfigurieren von SRP {#configuring-srp}

Die Angabe der standardmäßigen Speicheroption, basierend auf der zugrunde liegenden Bereitstellung, erfolgt über die [Speicherkonfigurationskonsole](/help/communities/srp-config.md).

Informationen zur Konfiguration der einzelnen Optionen finden Sie unter:

* [ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)
* [MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)
* [DSRP - Resource Provider für relationale Datenbankspeicher](/help/communities/dsrp.md)
* [JSRP - JCR Storage Resource Provider](/help/communities/jsrp.md)

Wenn keine Speicheroption aktiv ausgewählt ist, ist JSRP standardmäßig aktiviert.

## Zusätzliche Informationen {#additional-information}

### UGC nie repliziert {#ugc-never-replicated}

In der Autorenumgebung erstellt ein Autor Seiteninhalte und repliziert sie in der Veröffentlichungsumgebung. Wenn eine Seite eine interaktive AEM Communities-Funktion enthält, z. B. Kommentare, Rezensionen, Foren, Blog oder Fragen und Antworten, führt die Interaktion von Mitgliedern (die bei Site-Besuchern angemeldet sind) mit einer Veröffentlichungsinstanz dazu, dass benutzergenerierte Inhalte (UGC) in die Veröffentlichungsumgebung eingegeben werden.

Zuvor wurde dieser Community-Inhalt rückwärts auf Autoreninstanzen repliziert und von der Autoreninstanz auf Veröffentlichungsinstanzen repliziert. Es war problematisch, die Konsistenz zwischen AEM Instanzen mit der Rückwärts- und Vorwärtsreplikation zu wahren.

Ab AEM Communities 6.1 entfällt die Notwendigkeit der Replikation von benutzergenerierten Inhalten durch die Verwendung von freigegebenem Speicher für benutzergenerierte Inhalte (wie oben beschrieben).

Während Site-Inhalte repliziert werden, werden benutzergenerierte Inhalte nie repliziert.

### Verwalten von Benutzerdaten {#managing-user-data}

Auch für CommunitIes sind [*Benutzer*, *Benutzergruppen* und *Benutzerprofile*](/help/communities/users.md) von Interesse. Diese benutzerbezogenen Daten, die in der Veröffentlichungsumgebung erstellt und aktualisiert werden, müssen anderen Veröffentlichungsinstanzen zur Verfügung gestellt werden, wenn die Topologie eine [Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm) ist.

Ab AEM Communities 6.1 werden benutzerbezogene Daten mithilfe der Sling-Verteilung anstatt der Replikation synchronisiert. Weitere Informationen finden Sie unter [Benutzersynchronisierung](/help/communities/sync.md).

### Upgrade auf AEM Communities 6.5 {#upgrading-to-aem-communities}

Wenn bei der Aktualisierung auf AEM 6.5 Communities bereits vorhandene benutzergenerierte Inhalte beibehalten werden müssen, sollten Schritte unternommen werden, je nachdem, ob die Community von AEM 5.6.1 oder AEM 6.0 die On-Demand-Adobe oder die On-Premise-Speicherung von benutzergenerierten Inhalten verwendet hat.

Weitere Informationen finden Sie unter [Aktualisierung auf AEM Communities 6.5](/help/communities/upgrade.md).
