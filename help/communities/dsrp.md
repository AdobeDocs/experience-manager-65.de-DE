---
title: DSRP - Resource Provider für relationale Datenbankspeicher
seo-title: DSRP - Resource Provider für relationale Datenbankspeicher
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
seo-description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
uuid: f364e7da-ee54-4ab2-a630-7ec9239005ac
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d23acb18-6761-4290-9e7a-a434582791bd
role: Administrator
exl-id: 15b3a594-efde-4702-9233-232ba1c7e5b0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 3%

---

# DSRP - Relativer Datenbankspeicheranbieter {#dsrp-relational-database-storage-resource-provider}

## Über DSRP {#about-dsrp}

Wenn AEM Communities so konfiguriert ist, dass eine relationale Datenbank als gemeinsamen Speicher verwendet wird, kann von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte (UGC) zugegriffen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

* [MySQL](#mysql-configuration), eine relationale Datenbank.
* [Apache Solr](#solr-configuration), eine Suchplattform.

>[!NOTE]
>
>Die standardmäßige Speicherkonfiguration wird jetzt im conf-Pfad (`/conf/global/settings/community/srpc/defaultconfiguration`) anstelle des etc-Pfads (`/etc/socialconfig/srpc/defaultconfiguration`) gespeichert. Es wird empfohlen, die [Migrationsschritte](#zerodt-migration-steps) zu befolgen, damit die Standardeinstellung erwartungsgemäß funktioniert.

## Konfiguration der relationalen Datenbank {#relational-database-configuration}

### MySQL-Konfiguration {#mysql-configuration}

Eine MySQL-Installation kann zwischen Aktivierungsfunktionen und einem gemeinsamen Speicher (DSRP) innerhalb desselben Verbindungspools freigegeben werden, indem verschiedene Datenbanknamen (Schema) und auch verschiedene Verbindungen (server:port) verwendet werden.

Informationen zur Installation und Konfiguration finden Sie unter [MySQL-Konfiguration für DSRP](dsrp-mysql.md).

### Solr-Konfiguration {#solr-configuration}

Eine Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Knotenspeicher (Oak) und dem gemeinsamen Speicher (SRP) freigegeben werden.

Wenn sowohl die Oak- als auch die SRP-Kollektionen intensiv verwendet werden, kann aus Leistungsgründen ein zweiter Solr installiert werden.

In Produktionsumgebungen bietet der SolrCloud-Modus eine verbesserte Leistung im Vergleich zum eigenständigen Modus (ein einzelnes lokales Solr-Setup).

Informationen zur Installation und Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### Wählen Sie DSRP {#select-dsrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

Auf der Autoreninstanz, um auf die Speicherkonfigurationskonsole zuzugreifen

* Anmelden mit Administratorrechten
* Von **Hauptmenü**

   * Wählen Sie **[!UICONTROL Tools]** (aus dem linken Bereich) aus.
   * Wählen Sie **[!UICONTROL Communities]**
   * Wählen Sie **[!UICONTROL Speicherkonfiguration]** aus.

      * Der resultierende Speicherort lautet beispielsweise: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)
      >[!NOTE]
      >
      >Die standardmäßige Speicherkonfiguration wird jetzt im Kontextpfad (`/conf/global/settings/community/srpc/defaultconfiguration`) gespeichert.      anstelle des etc-Pfads (`/etc/socialconfig/srpc/defaultconfiguration`). Es wird empfohlen, die [Migrationsschritte](#zerodt-migration-steps) zu befolgen, damit die Standardeinstellung erwartungsgemäß funktioniert.
   ![dsrp-config](assets/dsrp-config.png)

* Wählen Sie **[!UICONTROL Database Storage Resource Provider (DSRP)]** aus.
* **Datenbankkonfiguration**

   * **[!UICONTROL JDBC-Datenquellenname]**

      Der Name der MySQL-Verbindung muss mit dem in [JDBC OSGi-Konfiguration](dsrp-mysql.md#configurejdbcconnections) eingegebenen Namen übereinstimmen

      *Standard*: communities

   * **[!UICONTROL Datenbankname]**

      Name, der dem Schema im Skript [init_schema.sql](dsrp-mysql.md#obtain-the-sql-script) zugewiesen wird

      *Standard*: communities

* **SolrConfiguration**

   * **[](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files)Zookeeper-Host**

      Lassen Sie diesen Wert leer, wenn Solr mit dem internen ZooKeeper ausgeführt wird. Andernfalls setzen Sie bei Ausführung im [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper diesen Wert auf den URI für den ZooKeeper, z. B. *my.server.com:80*

      *Standard*:  *&lt;blank>*

   * **[!UICONTROL Solr-URL]**

      *Standard*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr-Sammlung]**

      *Standard*: collection1

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

### Migrationsschritte ohne Ausfallzeiten für Standard-RP {#zerodt-migration-steps}

Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die Standardseite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) erwartungsgemäß funktioniert:

1. Benennen Sie den Pfad unter `/etc/socialconfig` in `/etc/socialconfig_old` um, sodass die Systemkonfiguration auf &quot;jsrp(Standard)&quot;zurückfällt.
1. Navigieren Sie zur Standardseite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), auf der jsrp konfiguriert ist. Klicken Sie auf die Schaltfläche **[!UICONTROL submit]** , damit der neue Standardkonfigurationsknoten unter `/conf/global/settings/community/srpc` erstellt wird.
1. Löschen Sie die erstellte Standardkonfiguration `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Kopieren Sie die alte Konfiguration `/etc/socialconfig_old/srpc/defaultconfiguration` anstelle des gelöschten Knotens (`/conf/global/settings/community/srpc/defaultconfiguration`) im vorherigen Schritt.
1. Löschen Sie den alten Knoten etc `/etc/socialconfig_old`.

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

DSRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

* Bei Autor:

   * Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**
   * Doppelklicken Sie auf **[!UICONTROL Tree aktivieren]**
   * **Startpfad**:

      * Navigieren Sie zu `/etc/socialconfig/srpc/`
   * Stellen Sie sicher, dass `Only Modified` nicht ausgewählt ist.
   * Wählen Sie **[!UICONTROL Activate]** aus.


## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Neuindizierung von Solr für DSRP {#reindexing-solr-for-dsrp}

Um DSRP Solr neu zu indizieren, folgen Sie der Dokumentation für [Neuindizierung von MSRP](msrp.md#msrp-reindex-tool). Verwenden Sie jedoch bei der Neuindizierung für DSRP stattdessen diese URL: **/services/social/datastore/rdb/reindex**

Beispielsweise würde ein curl-Befehl zum Neuindizieren von DSRP wie folgt aussehen:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```
