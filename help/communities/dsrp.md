---
title: DSRP - Relationaler Datenbankspeicher-Ressourcenanbieter
description: Einrichten von AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 15b3a594-efde-4702-9233-232ba1c7e5b0
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 1%

---

# DSRP - Relationaler Datenbankspeicher-Ressourcenanbieter {#dsrp-relational-database-storage-resource-provider}

## Über DSRP {#about-dsrp}

Wenn AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher konfiguriert ist, können Sie von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte zugreifen, ohne dass Synchronisierung oder Replikation erforderlich sind.

Siehe auch [Merkmale von SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

* [MySQL](#mysql-configuration), eine relationale Datenbank.
* [Apache Solr](#solr-configuration), eine Suchplattform.

>[!NOTE]
>
>Die standardmäßige Speicherkonfiguration wird jetzt in conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) anstelle `etc` path (`/etc/socialconfig/srpc/defaultconfiguration`) gespeichert. Es wird empfohlen, die [Migrationsschritte“ zu befolgen](#zerodt-migration-steps) damit defaultsrp erwartungsgemäß funktioniert.

## Konfiguration relationaler Datenbanken {#relational-database-configuration}

### MySQL-Konfiguration {#mysql-configuration}

Eine MySQL-Installation kann von Aktivierungsfunktionen und Common Store (DSRP) innerhalb desselben Verbindungspools gemeinsam genutzt werden, indem verschiedene Datenbank-(Schema-)Namen sowie verschiedene Verbindungen (server:port) verwendet werden.

Informationen zur Installation und Konfiguration finden Sie unter [MySQL-Konfiguration für DSRP](dsrp-mysql.md).

### Solr-Konfiguration {#solr-configuration}

Eine Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Knotenspeicher (Oak) und dem gemeinsamen Speicher (SRP) freigegeben werden.

Wenn sowohl die Oak- als auch die SRP-Sammlungen intensiv verwendet werden, kann aus Leistungsgründen eine zweite Solr-Instanz installiert werden.

In Produktionsumgebungen bietet SolrCloud-Modus eine verbesserte Leistung im Vergleich zum eigenständigen Modus (eine einzelne, lokale Solr-Einrichtung).

Informationen zur Installation und Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### DSRP auswählen {#select-dsrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen -Speicherkonfiguration, die angibt, welche Implementierung von SRP verwendet werden soll.

So greifen Sie auf der Autoreninstanz auf die Speicherkonfigurationskonsole zu

* Mit Administratorrechten anmelden
* Vom **Hauptmenü**

   * Wählen Sie **[!UICONTROL Tools]** aus (im linken Bereich)
   * Select **[!UICONTROL Communities]**
   * Wählen Sie **[!UICONTROL Speicherkonfiguration]**

      * Der resultierende Speicherort ist beispielsweise: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)

     >[!NOTE]
     >
     >Die standardmäßige Speicherkonfiguration wird jetzt unter conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) gespeichert      anstelle `etc` Pfads (`/etc/socialconfig/srpc/defaultconfiguration`). Es wird empfohlen, die [Migrationsschritte“ zu befolgen](#zerodt-migration-steps) damit defaultsrp erwartungsgemäß funktioniert.

  ![dsrp-config](assets/dsrp-config.png)

* Wählen Sie **[!UICONTROL Database Storage Resource Provider (DSRP)]**
* **Datenbankkonfiguration**

   * **[!UICONTROL JDBC-Datenquellenname]**

     Der Name der MySQL-Verbindung muss mit dem in der JDBC-OSGi[Konfiguration angegebenen Namen übereinstimmen](dsrp-mysql.md#configurejdbcconnections)

     *Standard*: Communities

   * **[!UICONTROL Datenbankname]**

     Name des Schemas im Skript [init_schema.sql](dsrp-mysql.md#obtain-the-sql-script)

     *Standard*: Communities

* **SolrConfiguration**

   * **[ZooKeeper](https://solr.apache.org/guide/6_6/using-zookeeper-to-manage-configuration-files.html) Host**

     Lassen Sie diesen Wert leer, wenn Sie Solr mit dem internen ZooKeeper ausführen. Andernfalls müssen Sie bei der Ausführung [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper diesen Wert auf den URI für den ZooKeeper festlegen, z. B. *my.server.com:80*

     *Standard*: *&lt;blank>*

   * **[!UICONTROL Solr-URL]**

     *default*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr-Sammlung]**

     *Standard*: collection1

* Wählen Sie **[!UICONTROL Absenden]**.

### Keine Ausfallzeiten bei der Migration für Standardschritte {#zerodt-migration-steps}

Um sicherzustellen, dass die standardmäßige srp-Seite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) erwartungsgemäß funktioniert, führen Sie die folgenden Schritte aus:

1. Benennen Sie den Pfad unter `/etc/socialconfig` in `/etc/socialconfig_old` um, damit die Systemkonfiguration auf „jsrp“ (Standard) zurückgesetzt wird.
1. Wechseln Sie zur Seite „defaultsrp“ [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), auf der JSRP konfiguriert ist. Klicken Sie auf **[!UICONTROL Senden]**, damit `/conf/global/settings/community/srpc` ein neuer Standardkonfigurationsknoten erstellt wird.
1. Löschen Sie die erstellte `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Kopieren Sie im vorherigen Schritt die alte `/etc/socialconfig_old/srpc/defaultconfiguration` anstelle des gelöschten Knotens (`/conf/global/settings/community/srpc/defaultconfiguration`).
1. Löschen Sie den alten `etc` Knoten `/etc/socialconfig_old`.

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

DSRP muss auf allen Autoren- und Veröffentlichungsinstanzen als Common Store identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

* In der Autoreninstanz:

   * Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**
   * Doppelklicken Sie auf **[!UICONTROL Baum aktivieren]**
   * **Startpfad**:

      * Navigieren zu `/etc/socialconfig/srpc/`

   * Stellen Sie sicher, dass `Only Modified` nicht ausgewählt ist.
   * Wählen Sie **[!UICONTROL Aktivieren]** aus.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Neuindizierung von Solr für DSRP {#reindexing-solr-for-dsrp}

Befolgen Sie zur Neuindizierung von DSRP Solr die Dokumentation für [Neuindizierung von MSRP](msrp.md#msrp-reindex-tool). Wenn Sie jedoch für DSRP neu indizieren, verwenden Sie stattdessen diese URL: **/services/social/datastore/rdb/reindex**

Ein curl-Befehl zur Neuindizierung von DSRP würde beispielsweise wie folgt aussehen:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```
