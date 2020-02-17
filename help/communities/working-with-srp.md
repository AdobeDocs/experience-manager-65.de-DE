---
title: SRP - Gemeinschaftlicher Inhaltsspeicher
seo-title: SRP - Gemeinschaftlicher Inhaltsspeicher
description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem einzigen gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird
seo-description: Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem einzigen gemeinsamen Speicher gespeichert, der von einem Speicherressourcenanbieter (SRP) bereitgestellt wird
uuid: d45e03c4-378b-4510-a6a0-d48c8cb879d9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 6f13b21a-f4ef-4889-9b8e-4da3f846fa35
docset: aem65
translation-type: tm+mt
source-git-commit: 70e6f2d8366456e5091b7b775dc40914948921ab

---


# SRP - Gemeinschaftlicher Inhaltsspeicher{#srp-community-content-storage}

## Einführung {#introduction}

Ab AEM Communities 6.1 werden benutzergenerierte Inhalte (UGC) in einem einzigen, von einem Speicherressourcenanbieter (SRP) bereitgestellten gemeinsamen Speicher gespeichert. Es stehen verschiedene SRP-Optionen zur Auswahl, z. B. ASRP, MSRP und JSRP.

Im Gegensatz zu früheren Versionen gibt es keine Reverse/Forward-Replizierung von UGC in AEM-Instanzen. Stattdessen macht der SRP UGC-Vorgänge für das Erstellen, Lesen, Aktualisieren und Löschen (CRUD) von allen Autoren- und Veröffentlichungsinstanzen mit Ausnahme von JSRP direkt zugänglich.

Im Folgenden sind die [Merkmale jeder einzelnen SRP-Option](#characteristics-of-srp-options)aufgeführt, die für den Entscheidungsprozess bei der Auswahl des geeigneten SRP und der [zugrunde liegenden Bereitstellung](/help/communities/topologies.md)von entscheidender Bedeutung ist.

Weitere Informationen zur Verwendung von SRP für UGC finden Sie unter Übersicht über den [Speicherressourcen-Provider](/help/communities/srp.md).

>[!NOTE]
>
>SRP gilt nur für Community-Inhalte. Sie hat keine Auswirkungen auf den Speicherort des Site-Inhalts ([Knotenspeicher](/help/sites-deploying/data-store-config.md)) und hat keine Auswirkungen auf die sichere Verarbeitung von Benutzerregistrierung, Benutzerprofilen und Benutzergruppen zwischen AEM-Instanzen (siehe auch [Verwalten von Benutzerdaten](#managing-user-data)).

>[!CAUTION]
>
>Ab AEM 6.1 wird [UGC nie repliziert](#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen gemeinsamen Store enthält, z. B. die standardmäßige [JSRP](/help/communities/topologies.md#jsrp) -Topologie, ist UGC nur auf der AEM-Veröffentlichungs- oder Autoreninstanz sichtbar, auf der sie eingegeben wurde. Nur wenn die Topologie einen Veröffentlichungscluster enthält, ist das UGC in jeder Veröffentlichungsinstanz sichtbar.

## Merkmale der SRP-Optionen {#characteristics-of-srp-options}

[ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)Mit dieser Option wird der UGC remote in einem Cloud-Dienst, der von Adobe gehostet und verwaltet wird, beibehalten. Es erfordert eine zusätzliche Lizenz und arbeitet mit einem Kundenbetreuer zusammen, um das Konto für diese spezifische Lizenz bereitzustellen. ASRP erfordert:

* Ein dazugehöriger Cloud-Dienst, der von Adobe bereitgestellt und unterstützt wird, um Community-Inhalte zu speichern.
* Auswahl eines Rechenzentrums in einer bestimmten geografischen Region (USA, EMEA, APAC).

* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

ASRP ist geeignet:

* für TarMK publish farm.
* wenn keine Absicht besteht, in lokalen Speicher zu investieren.

>[!NOTE]
>
>Das Hochladen von Anlagen zu Beiträgen (oder Kommentaren) in ASRP ist auf 50 MB beschränkt.

[MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)Mit dieser Option wird der UGC direkt in einer lokalen MongoDB-Instanz beibehalten.

MSRP erfordert:

* Eine lokale, lizenzierte Installation von MongoDB zum Speichern von Community-Inhalten.
* Eine lokale Installation von Apache Solr.
* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

ASRP ist geeignet:

* Für eine vorhandene TarMK-Veröffentlichungsfarm.
* Für einen MongoMK- oder RdbMK-Cluster.
* Wenn Sie große Mengen an Community-Inhalten erwarten.

[DSRP - Relational Database Storage Resource Provider](/help/communities/dsrp.md)Mit dieser Option wird der UGC direkt in einer lokalen MySQL-Datenbankinstanz beibehalten.

DSRP erfordert:

* Eine lokale Installation von MySQL zum Speichern von Community-Inhalten.
* Eine lokale Installation von Apache Solr.
* Der gesamte programmatische Zugriff auf UGC erfolgt über die SRP-API.

DSRP ist geeignet:

* Für eine vorhandene TarMK-Veröffentlichungsfarm.
* Für einen MongoMK- oder RdbMK-Cluster.
* Wenn Sie große Mengen an Community-Inhalten erwarten.

[JSRP - JCR Storage Resource Provider](/help/communities/jsrp.md)Bei der Standardoption gibt es keinen gemeinsamen Speicher. Der UGC wird nur im selben JCR-Repository wie die AEM-Instanz, in der er eingegeben wurde, beibehalten.

JSRP:

* Speichert Community-Inhalte im JCR-Repository der AEM-Autor- oder Veröffentlichungsinstanz, in der sie veröffentlicht wurden.
* Erfordert den gesamten programmatischen Zugriff auf UGC über die SRP-API.
* Erfordert ein Veröffentlichungscluster, wenn mehr als eine Instanz im Veröffentlichungsmodus bereitgestellt wird (es gibt keinen Replikationsmechanismus unter den Instanzen im Veröffentlichungsmodus in einer TarMK-Farm).
* Die Moderation wird nur in der Veröffentlichungsumgebung durchgeführt (zwischen Autor und Veröffentlichung gibt es keinen Mechanismus für die umgekehrte/weiterführende Replizierung).
* Ist am besten für Entwicklung, Demonstrationen und Ausbildung.

## Konfigurieren von SRP {#configuring-srp}

Die Standardspeicheroption wird basierend auf der zugrunde liegenden Bereitstellung über die [Speicherkonfigurationskonsole](/help/communities/srp-config.md)festgelegt.

Konfigurationsdetails zu den einzelnen Optionen finden Sie unter:

* [ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)
* [MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)
* [DSRP - Ressourcenanbieter für den relationalen Datenbankspeicher](/help/communities/dsrp.md)
* [JSRP - JCR Storage Resource Provider](/help/communities/jsrp.md)

Wenn keine Speicheroption aktiv ausgewählt ist, ist JSRP standardmäßig aktiviert.

## Zusätzliche Informationen {#additional-information}

### UGC nie repliziert {#ugc-never-replicated}

In der Autorenumgebung erstellt ein Autor Seiteninhalte und repliziert sie in der Veröffentlichungsumgebung. Wenn eine Seite eine interaktive AEM Communities-Funktion wie Kommentare, Rezensionen, Forum, Blog oder QnA enthält, führt die Interaktion von Mitgliedern (die bei Site-Besuchern angemeldet sind) mit einer Veröffentlichungsinstanz dazu, dass benutzergenerierte Inhalte (UGC) in die Veröffentlichungsumgebung eingegeben werden.

Bisher wurde dieser Community-Inhalt umgekehrt in Autoreninstanzen repliziert und vom Autor in Veröffentlichungsinstanzen repliziert. Es war problematisch, die Konsistenz zwischen AEM-Instanzen mit der umgekehrten und weiterleitenden Replizierung aufrechtzuerhalten.

Ab AEM Communities 6.1 wurde die Notwendigkeit für die Replikation von UGC durch die Verwendung von freigegebenem Speicher für UGC wie oben beschrieben beseitigt.

Obwohl Site-Inhalte repliziert werden, wird UGC nie repliziert.

### Verwalten von Benutzerdaten {#managing-user-data}

Außerdem sind [*Benutzer *,* Benutzergruppen *und* Benutzerprofile *](/help/communities/users.md)von Interesse für CommunitiesIes. Wenn diese benutzerbezogenen Daten in der Veröffentlichungsumgebung erstellt und aktualisiert werden, müssen sie anderen Instanzen im Veröffentlichungsmodus zur Verfügung gestellt werden, wenn die Topologie eine[Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm)ist.

Ab AEM Communities 6.1 werden benutzerbezogene Daten mit der Sling-Distribution und nicht mit der Replikation synchronisiert. Weitere Informationen finden Sie unter [Benutzersynchronisierung](/help/communities/sync.md).

### Upgrading to AEM Communities 6.5 {#upgrading-to-aem-communities}

Wenn bei der Aktualisierung auf AEM 6.5 Communities bereits vorhandene UGC beibehalten werden müssen, sollten Schritte unternommen werden, je nachdem, ob die AEM 5.6.1- oder AEM 6.0-Community Adobe-On-Demand-Speicher oder lokalen Speicher von UGC verwendet hat.

Weitere Informationen finden Sie unter [Aktualisieren auf AEM Communities 6.5](/help/communities/upgrade.md).
