---
title: DSRP - Resource Provider für relationale Datenbankspeicher
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 15b3a594-efde-4702-9233-232ba1c7e5b0
source-git-commit: f0dd1ac3ab9c17a8b331f5048d84ec97dd23924f
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 3%

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
>Die standardmäßige Speicherkonfiguration wird jetzt im conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) anstelle von `etc` path (`/etc/socialconfig/srpc/defaultconfiguration`). Es wird empfohlen, dem [Migrationsschritte](#zerodt-migration-steps) , damit defaultsrp erwartungsgemäß funktioniert.

## Konfiguration der relationalen Datenbank {#relational-database-configuration}

### MySQL-Konfiguration {#mysql-configuration}

Eine MySQL-Installation kann zwischen Aktivierungsfunktionen und einem gemeinsamen Speicher (DSRP) innerhalb desselben Verbindungspools freigegeben werden, indem verschiedene Datenbanknamen (Schema) und auch verschiedene Verbindungen (server:port) verwendet werden.

Weitere Informationen zur Installation und Konfiguration finden Sie unter [MySQL-Konfiguration für DSRP](dsrp-mysql.md).

### Solr-Konfiguration {#solr-configuration}

Eine Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Knotenspeicher (Oak) und dem gemeinsamen Speicher (SRP) freigegeben werden.

Wenn sowohl die Oak- als auch die SRP-Kollektionen intensiv verwendet werden, kann aus Leistungsgründen ein zweiter Solr installiert werden.

In Produktionsumgebungen bietet der SolrCloud-Modus eine verbesserte Leistung im Vergleich zum eigenständigen Modus (ein einzelnes lokales Solr-Setup).

Weitere Informationen zur Installation und Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### DSRP auswählen {#select-dsrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

Auf der Autoreninstanz, um auf die Speicherkonfigurationskonsole zuzugreifen

* Anmelden mit Administratorrechten
* Aus dem **Hauptmenü**

   * Auswählen **[!UICONTROL Instrumente]** (aus dem linken Bereich)
   * Auswählen **[!UICONTROL Communities]**
   * Auswählen **[!UICONTROL Speicherkonfiguration]**

      * Der resultierende Speicherort lautet beispielsweise: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)

     >[!NOTE]
     >
     >Die standardmäßige Speicherkonfiguration wird jetzt im conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) anstelle von `etc` path (`/etc/socialconfig/srpc/defaultconfiguration`). Es wird empfohlen, dem [Migrationsschritte](#zerodt-migration-steps) , damit defaultsrp erwartungsgemäß funktioniert.

  ![dsrp-config](assets/dsrp-config.png)

* Auswählen **[!UICONTROL Datenbankspeicheranbieter (DSRP)]**
* **Datenbankkonfiguration**

   * **[!UICONTROL JDBC-Datenquellenname]**

     Der Name der MySQL-Verbindung muss mit dem in [JDBC OSGi-Konfiguration](dsrp-mysql.md#configurejdbcconnections)

     *default*: communities

   * **[!UICONTROL Datenbankname]**

     Name, der dem Schema in [init_schema.sql](dsrp-mysql.md#obtain-the-sql-script) script

     *default*: communities

* **SolrConfiguration**

   * **[](https://solr.apache.org/guide/6_6/using-zookeeper-to-manage-configuration-files.html)Zookeeper-Host**

     Lassen Sie diesen Wert leer, wenn Solr mit dem internen ZooKeeper ausgeführt wird. Andernfalls beim Ausführen in [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper diesen Wert auf den URI für den ZooKeeper festlegen, z. B. *my.server.com:80*

     *default*: *&lt;blank>*

   * **[!UICONTROL Solr-URL]**

     *default*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr-Sammlung]**

     *default*: collection1

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

### Migrationsschritte bei Null Ausfallzeiten für Standardwerte {#zerodt-migration-steps}

So stellen Sie sicher, dass die Standardseite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) wie erwartet funktioniert, führen Sie die folgenden Schritte aus:

1. Benennen Sie den Pfad unter `/etc/socialconfig` nach `/etc/socialconfig_old`, sodass die Systemkonfiguration auf jsrp (Standard) zurückgesetzt wird.
1. Navigieren zur Standardseite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), wobei jsrp konfiguriert ist. Klicken Sie auf **[!UICONTROL submit]** -Schaltfläche, damit der neue Standardkonfigurationsknoten unter `/conf/global/settings/community/srpc`.
1. Löschen der erstellten Standardkonfiguration `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Kopieren Sie die alte Konfiguration `/etc/socialconfig_old/srpc/defaultconfiguration` anstelle des gelöschten Knotens (`/conf/global/settings/community/srpc/defaultconfiguration`) im vorherigen Schritt.
1. Löschen des alten `etc` Knoten `/etc/socialconfig_old`.

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

DSRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

* Bei Autor:

   * Navigieren Sie vom Hauptmenü zu **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Replikation]**
   * Doppelklicken **[!UICONTROL Baum aktivieren]**
   * **Startpfad**:

      * Navigieren Sie zu `/etc/socialconfig/srpc/`

   * Sichern `Only Modified` nicht ausgewählt ist.
   * Auswählen **[!UICONTROL Aktivieren]**.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen über *Benutzer*, *Benutzerprofile* und *Benutzergruppen*, die häufig in die Veröffentlichungsumgebung eingegeben werden, besuchen Sie:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Solr-Neuindizierung für DSRP {#reindexing-solr-for-dsrp}

Um DSRP Solr neu zu indizieren, befolgen Sie die Dokumentation für [Neuindizierung von MSRP](msrp.md#msrp-reindex-tool)verwenden Sie jedoch bei der Neuindizierung für DSRP stattdessen diese URL: **/services/social/datastore/rdb/reindex**

Beispielsweise würde ein curl-Befehl zum Neuindizieren von DSRP wie folgt aussehen:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```
