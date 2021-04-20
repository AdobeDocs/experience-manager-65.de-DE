---
title: SRP - Community Content Datenspeicherung
seo-title: SRP - Community Content Datenspeicherung
description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem gemeinsamen Speicher gespeichert, der von einem Datenspeicherung Resource Provider (SRP) bereitgestellt wird
seo-description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem gemeinsamen Speicher gespeichert, der von einem Datenspeicherung Resource Provider (SRP) bereitgestellt wird
uuid: d45e03c4-378b-4510-a6a0-d48c8cb879d9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 6f13b21a-f4ef-4889-9b8e-4da3f846fa35
docset: aem65
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---


# SRP - Community Content Datenspeicherung {#srp-community-content-storage}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem gemeinsamen Speicher gespeichert, der von einem Datenspeicherung Resource Provider (SRP) bereitgestellt wird. Es stehen verschiedene SRP-Optionen zur Auswahl, z. B. ASRP, MSRP und JSRP.

Im Gegensatz zu früheren Versionen gibt es keine Reverse/Forward-Replizierung von UGC über AEM Instanzen hinweg. Stattdessen macht der SRP UGC-Vorgänge für das Erstellen, Lesen, Aktualisieren und Löschen (CRUD) von allen Autoren- und Veröffentlichungsinstanzen mit Ausnahme von JSRP direkt zugänglich.

Im Folgenden finden Sie die [Eigenschaften jeder SRP-Option](#characteristics-of-srp-options), die für den Entscheidungsprozess bei der Auswahl des entsprechenden SRP und [zugrunde liegenden Bereitstellung](/help/communities/topologies.md) entscheidende Informationen sind.

Weitere Informationen zur Verwendung von SRP für UGC finden Sie unter [Übersicht über den Ressourcenanbieter der Datenspeicherung](/help/communities/srp.md).

>[!NOTE]
>
>SRP gilt nur für Community-Inhalte. Sie hat keine Auswirkungen auf die Speicherorte von Site-Inhalten ([node store](/help/sites-deploying/data-store-config.md)) und hat keine Auswirkungen auf die sichere Verarbeitung von Benutzerregistrierung, Profilen und Benutzergruppen zwischen AEM Instanzen (siehe auch [Verwalten von Benutzerdaten](#managing-user-data)).

>[!CAUTION]
>
>Ab AEM 6.1 wird [UGC nie repliziert](#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen gemeinsamen Speicher enthält, z. B. die Standardtopologie [JSRP](/help/communities/topologies.md#jsrp), ist UGC nur in der AEM- oder Autoreninstanz sichtbar, in der sie eingegeben wurde. Nur wenn die Topologie einen Veröffentlichungscluster enthält, ist das UGC in jeder Veröffentlichungsinstanz sichtbar.

## Merkmale der SRP-Optionen {#characteristics-of-srp-options}

[ASRP - Adobe Datenspeicherung Resource Provider](/help/communities/asrp.md)

Bei dieser Option wird der UGC remote in einem Cloud-Dienst, der von der Adobe gehostet und verwaltet wird, beibehalten. Es erfordert eine zusätzliche Lizenz und arbeitet mit einem Kundenbetreuer zusammen, um das Konto für diese spezifische Lizenz bereitzustellen. ASRP erfordert:

* Ein dazugehöriger Cloud-Dienst, der von der Adobe zum Speichern von Community-Inhalten bereitgestellt und unterstützt wird.
* Auswahl eines Rechenzentrums in einer bestimmten geografischen Region (USA, EMEA, APAC).

* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

ASRP ist geeignet:

* Für TarMK Veröffentlichungsfarm.
* Wenn es keine Absicht gibt, in die lokale Datenspeicherung zu investieren.

>[!NOTE]
>
>Das Hochladen von Anlagen zu Beiträgen (oder Kommentaren) in ASRP ist auf 50 MB beschränkt.

[MSRP - MongoDB Datenspeicherung Resource Provider](/help/communities/msrp.md)

Mit dieser Option wird der UGC direkt in einer lokalen MongoDB-Instanz beibehalten.

MSRP erfordert:

* Eine lokale, lizenzierte Installation von MongoDB zum Speichern von Community-Inhalten.
* Eine lokale Installation von Apache Solr.
* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

ASRP ist geeignet:

* Für eine vorhandene TarMK-Veröffentlichungsfarm.
* Für einen MongoMK- oder RdbMK-Cluster.
* Wenn Sie große Mengen an Community-Inhalten erwarten.

[DSRP - Ressourcenanbieter für relationale Datenspeicherung](/help/communities/dsrp.md)

Mit dieser Option wird der UGC direkt in einer lokalen MySQL-Datenbankinstanz beibehalten.

DSRP erfordert:

* Eine lokale Installation von MySQL zum Speichern von Community-Inhalten.
* Eine lokale Installation von Apache Solr.
* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

DSRP ist geeignet:

* Für eine vorhandene TarMK-Veröffentlichungsfarm.
* Für einen MongoMK- oder RdbMK-Cluster.
* Wenn Sie große Mengen an Community-Inhalten erwarten.

[JSRP - JCR Datenspeicherung Resource Provider](/help/communities/jsrp.md)

Bei der Standardoption gibt es keinen gemeinsamen Speicher. Die UGC wird nur im selben JCR-Repository wie die AEM Instanz, in der sie eingegeben wurde, beibehalten.

JSRP:

* Speichert Community-Inhalte im JCR-Repository der AEM Autoren- oder Veröffentlichungsinstanz, in der sie veröffentlicht wurden.
* Erfordert den gesamten programmatischen Zugriff auf UGC über die SRP-API.
* Erfordert ein Veröffentlichungscluster, wenn mehr als eine Instanz im Veröffentlichungsmodus bereitgestellt wird (es gibt keinen Replikationsmechanismus unter den Instanzen im Veröffentlichungsmodus in einer TarMK-Farm).
* Die Moderation wird nur in der Umgebung &quot;Veröffentlichen&quot;durchgeführt (zwischen Autor und Veröffentlichung gibt es keinen Mechanismus für die umgekehrte/weiterführende Replizierung).
* Ist am besten für Entwicklung, Demonstrationen und Ausbildung.

## Konfigurieren von SRP {#configuring-srp}

Die Standardoption für die Datenspeicherung wird basierend auf der zugrunde liegenden Bereitstellung über die [Datenspeicherung Configuration Console](/help/communities/srp-config.md) festgelegt.

Konfigurationsdetails zu den einzelnen Optionen finden Sie unter:

* [ASRP - Adobe Datenspeicherung Resource Provider](/help/communities/asrp.md)
* [MSRP - MongoDB Datenspeicherung Resource Provider](/help/communities/msrp.md)
* [DSRP - Ressourcenanbieter für relationale Datenspeicherung](/help/communities/dsrp.md)
* [JSRP - JCR Datenspeicherung Resource Provider](/help/communities/jsrp.md)

Wenn keine Option &quot;Datenspeicherung&quot;aktiv ausgewählt ist, ist JSRP standardmäßig aktiviert.

## Zusätzliche Informationen {#additional-information}

### UGC nie repliziert {#ugc-never-replicated}

In der Umgebung &quot;Autor&quot;erstellt ein Autor Seiteninhalte und repliziert sie in der Umgebung &quot;Veröffentlichen&quot;. Wenn eine Seite eine interaktive AEM Communities-Funktion wie Kommentare, Rezensionen, Foren, Blog oder QnA enthält, führt die Interaktion (bei Site-Besuchern angemeldet) mit einer Veröffentlichungsinstanz dazu, dass benutzergenerierte Inhalte (UGC) in die Umgebung &quot;Veröffentlichen&quot;eingegeben werden.

Bisher wurde dieser Community-Inhalt umgekehrt in Autoreninstanzen repliziert und vom Autor in Veröffentlichungsinstanzen repliziert. Es war problematisch, die Konsistenz zwischen AEM Instanzen mit der umgekehrten und weiterleitenden Replizierung aufrechtzuerhalten.

Ab AEM Communities 6.1 entfällt die Notwendigkeit für die Replikation von UGC durch die Verwendung von freigegebener Datenspeicherung für UGC, wie oben beschrieben.

Obwohl Site-Inhalte repliziert werden, wird UGC nie repliziert.

### Verwalten von Benutzerdaten {#managing-user-data}

Für Communities sind außerdem [*user*, *user groups* und *user Profils*](/help/communities/users.md) von Interesse. Wenn diese benutzerbezogenen Daten in der Umgebung &quot;Veröffentlichen&quot;erstellt und aktualisiert werden, müssen sie anderen Instanzen im Veröffentlichungsmodus zur Verfügung gestellt werden, wenn die Topologie eine [Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm) ist.

Ab AEM Communities 6.1 werden benutzerbezogene Daten mit der Sling-Distribution und nicht mit der Replikation synchronisiert. Weitere Informationen finden Sie unter [Benutzersynchronisierung](/help/communities/sync.md).

### Upgrade auf AEM Communities 6.5 {#upgrading-to-aem-communities}

Bei der Aktualisierung auf AEM 6.5 Communities, bei der bereits vorhandene UGC beibehalten werden müssen, sollten Schritte unternommen werden, je nachdem, ob die AEM 5.6.1- oder AEM 6.0-Community die On-Demand-Datenspeicherung der Adobe oder die lokale Datenspeicherung von UGC verwendet hat.

Weitere Informationen finden Sie unter [Upgrade auf AEM Communities 6.5](/help/communities/upgrade.md).
