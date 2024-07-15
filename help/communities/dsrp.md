---
title: DSRP - Resource Provider für relationale Datenbankspeicher
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
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

# DSRP - Resource Provider für relationale Datenbankspeicher {#dsrp-relational-database-storage-resource-provider}

## Über DSRP {#about-dsrp}

Wenn AEM Communities so konfiguriert ist, dass eine relationale Datenbank als gemeinsamen Speicher verwendet wird, kann von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte (UGC) zugegriffen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

* [MySQL](#mysql-configuration), eine relationale Datenbank.
* [Apache Solr](#solr-configuration), eine Suchplattform.

>[!NOTE]
>
>Die standardmäßige Speicherkonfiguration wird jetzt im conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) anstelle von `etc` path (`/etc/socialconfig/srpc/defaultconfiguration`) gespeichert. Es wird empfohlen, die [Migrationsschritte](#zerodt-migration-steps) zu befolgen, damit die Standardeinstellungen wie erwartet funktionieren.

## Konfiguration der relationalen Datenbank {#relational-database-configuration}

### MySQL-Konfiguration {#mysql-configuration}

Eine MySQL-Installation kann zwischen Aktivierungsfunktionen und einem gemeinsamen Speicher (DSRP) innerhalb desselben Verbindungspools freigegeben werden, indem verschiedene Datenbanknamen (Schema) und auch verschiedene Verbindungen (server:port) verwendet werden.

Informationen zur Installation und Konfiguration finden Sie unter [MySQL-Konfiguration für DSRP](dsrp-mysql.md).

### Solr-Konfiguration {#solr-configuration}

Eine Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Knotenspeicher (Oak) und dem gemeinsamen Speicher (SRP) freigegeben werden.

Wenn sowohl die Oak- als auch die SRP-Kollektionen intensiv verwendet werden, kann aus Leistungsgründen ein zweiter Solr installiert werden.

In Produktionsumgebungen bietet der SolrCloud-Modus eine verbesserte Leistung im Vergleich zum eigenständigen Modus (ein einzelnes lokales Solr-Setup).

Informationen zur Installation und Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### DSRP auswählen {#select-dsrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

Auf der Autoreninstanz, um auf die Speicherkonfigurationskonsole zuzugreifen

* Anmelden mit Administratorrechten
* Aus dem **Hauptmenü**

   * Wählen Sie **[!UICONTROL Tools]** (aus dem linken Bereich) aus.
   * Wählen Sie **[!UICONTROL Communities]** aus
   * Wählen Sie **[!UICONTROL Speicherkonfiguration]**

      * Der resultierende Speicherort lautet beispielsweise: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)

     >[!NOTE]
     >
     >Die standardmäßige Speicherkonfiguration wird jetzt im conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) gespeichert.      anstelle des Pfads `etc` (`/etc/socialconfig/srpc/defaultconfiguration`). Es wird empfohlen, die [Migrationsschritte](#zerodt-migration-steps) zu befolgen, damit die Standardeinstellungen wie erwartet funktionieren.

  ![dsrp-config](assets/dsrp-config.png)

* Wählen Sie **[!UICONTROL Datenbankspeicherressourcenanbieter (DSRP)]** aus.
* **Datenbankkonfiguration**

   * **[!UICONTROL JDBC-Datenquellenname]**

     Der Name der MySQL-Verbindung muss mit dem in der [JDBC OSGi-Konfiguration](dsrp-mysql.md#configurejdbcconnections) eingegebenen Namen übereinstimmen

     *default*: communities

   * **[!UICONTROL Datenbankname]**

     Name, der dem Schema im Skript [init_schema.sql](dsrp-mysql.md#obtain-the-sql-script) übergeben wird

     *default*: communities

* **SolrConfiguration**

   * **[zookeeper](https://solr.apache.org/guide/6_6/using-zookeeper-to-manage-configuration-files.html) host**

     Lassen Sie diesen Wert leer, wenn Solr mit dem internen ZooKeeper ausgeführt wird. Wenn Sie im [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper ausgeführt werden, setzen Sie diesen Wert auf den URI für den ZooKeeper, z. B. *my.server.com:80*

     *default*: *&lt;blank>*

   * **[!UICONTROL Solr-URL]**

     *default*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr Collection]**

     *default*: collection1

* Wählen Sie **[!UICONTROL Absenden]**.

### Migrationsschritte bei Null Ausfallzeiten für Standardwerte {#zerodt-migration-steps}

Gehen Sie wie folgt vor, um sicherzustellen, dass die Standardseite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) erwartungsgemäß funktioniert:

1. Benennen Sie den Pfad bei `/etc/socialconfig` in `/etc/socialconfig_old` um, sodass die Systemkonfiguration auf &quot;jsrp(Standard)&quot;zurückfällt.
1. Navigieren Sie zur Standardseite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), auf der jsrp konfiguriert ist. Klicken Sie auf die Schaltfläche **[!UICONTROL Senden]** , damit der neue standardmäßige Konfigurationsknoten unter `/conf/global/settings/community/srpc` erstellt wird.
1. Löschen Sie die erstellte Standardkonfiguration `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Kopieren Sie die alte Konfiguration `/etc/socialconfig_old/srpc/defaultconfiguration` anstelle des gelöschten Knotens (`/conf/global/settings/community/srpc/defaultconfiguration`) im vorherigen Schritt.
1. Löschen Sie den alten `etc` -Knoten `/etc/socialconfig_old`.

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

DSRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

* Bei Autor:

   * Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]** .
   * Doppelklicken Sie auf **[!UICONTROL Baum aktivieren]**
   * **Startpfad**:

      * Navigieren zu `/etc/socialconfig/srpc/`

   * Stellen Sie sicher, dass `Only Modified` nicht ausgewählt ist.
   * Wählen Sie **[!UICONTROL Aktivieren]** aus.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in die Veröffentlichungsumgebung eingegeben werden, finden Sie unter:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Solr-Neuindizierung für DSRP {#reindexing-solr-for-dsrp}

Um DSRP Solr neu zu indizieren, folgen Sie der Dokumentation für [Neuindizierung von MSRP](msrp.md#msrp-reindex-tool), verwenden Sie jedoch bei der Neuindizierung für DSRP stattdessen diese URL: **/services/social/datastore/rdb/reindex**

Beispielsweise würde ein curl-Befehl zum Neuindizieren von DSRP wie folgt aussehen:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```
