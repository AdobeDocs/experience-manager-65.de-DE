---
title: DSRP - Ressourcenanbieter für relationale Datenspeicherung
seo-title: DSRP - Ressourcenanbieter für relationale Datenspeicherung
description: AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher einrichten
seo-description: AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher einrichten
uuid: f364e7da-ee54-4ab2-a630-7ec9239005ac
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d23acb18-6761-4290-9e7a-a434582791bd
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 4%

---


# DSRP - Resource Provider für relationale Datenspeicherung {#dsrp-relational-database-storage-resource-provider}

## Über DSRP {#about-dsrp}

Wenn AEM Communities so konfiguriert ist, dass eine relationale Datenbank als gemeinsamer Speicher verwendet wird, können vom Benutzer generierte Inhalte (UGC) von allen Autor- und Veröffentlichungsinstanzen aus aufgerufen werden, ohne dass Synchronisierung oder Replikation erforderlich sind.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

* [MySQL](#mysql-configuration), eine relationale Datenbank.
* [Apache Solr](#solr-configuration), eine Suchplattform.

>[!NOTE]
>
>Die Standardkonfiguration der Datenspeicherung wird jetzt im conf path(`/conf/global/settings/community/srpc/defaultconfiguration`) anstelle von etc path (`/etc/socialconfig/srpc/defaultconfiguration`) gespeichert. Es wird empfohlen, die [Migrationsschritte](#zerodt-migration-steps) auszuführen, damit die Standardeinstellung erwartungsgemäß funktioniert.

## Relative Datenbankkonfiguration {#relational-database-configuration}

### MySQL-Konfiguration {#mysql-configuration}

Eine MySQL-Installation kann unter Verwendung verschiedener Datenbanknamen (Schema) und verschiedener Verbindungen (server:port) zwischen Aktivierungsfunktionen und einem gemeinsamen Speicher (DSRP) innerhalb desselben Verbindungspools freigegeben werden.

Einzelheiten zur Installation und Konfiguration finden Sie unter [MySQL-Konfiguration für DSRP](dsrp-mysql.md).

### Solr-Konfiguration {#solr-configuration}

Eine Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Node Store (Oak) und dem Common Store (SRP) freigegeben werden.

Wenn sowohl die Oak- als auch die SRP-Kollektionen intensiv verwendet werden, kann aus Leistungsgründen ein zweiter Solr installiert werden.

Bei Produktionsfunktionen bietet der SolrCloud-Umgebung eine verbesserte Leistung im Standalone-Modus (ein einzelnes, lokales Solr-Setup).

Informationen zur Installation und Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### Wählen Sie DSRP {#select-dsrp}

Die [Datenspeicherung Configuration Console](srp-config.md) ermöglicht die Auswahl der Standardkonfiguration der Datenspeicherung, die die zu verwendende Implementierung von SRP identifiziert.

Wenn Sie Autor sind, können Sie auf die Datenspeicherung Configuration Console zugreifen

* Anmelden mit Administratorberechtigungen
* Von **Hauptmenü**

   * Wählen Sie **[!UICONTROL Tools]** (aus dem linken Bereich)
   * Wählen Sie **[!UICONTROL Communities]**
   * Wählen Sie **[!UICONTROL Datenspeicherung Configuration]**

      * Der resultierende Speicherort lautet beispielsweise: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)
      >[!NOTE]
      >
      >Die Standardkonfiguration der Datenspeicherung wird jetzt im conf-Pfad(`/conf/global/settings/community/srpc/defaultconfiguration`) gespeichert.      anstelle von etc Pfad (`/etc/socialconfig/srpc/defaultconfiguration`). Es wird empfohlen, die [Migrationsschritte](#zerodt-migration-steps) auszuführen, damit die Standardeinstellung erwartungsgemäß funktioniert.
   ![dsrp-config](assets/dsrp-config.png)

* Wählen Sie **[!UICONTROL Database Datenspeicherung Resource Provider (DSRP)]**
* **Datenbankkonfiguration**

   * **[!UICONTROL JDBC-Datenquellenname]**

      Der Name der MySQL-Verbindung muss mit dem in [JDBC OSGi-Konfiguration](dsrp-mysql.md#configurejdbcconnections)

      *Standard*: Communities

   * **[!UICONTROL Datenbankname]**

      Name, der dem Schema im Skript [init_Schema.sql](dsrp-mysql.md#obtain-the-sql-script) zugewiesen wird

      *Standard*: Communities

* **SolrConfiguration**

   * **[](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files)Zookeeper-Host**

      Lassen Sie diesen Wert leer, wenn Solr mit dem internen ZooKeeper ausgeführt wird. Andernfalls legen Sie bei Ausführung im [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper diesen Wert auf den URI für den ZooKeeper fest, z. B. *my.server.com:80*

      *Standard*:  *&lt;blank>*

   * **[!UICONTROL Solr-URL]**

      *Standard*: https://127.0.0.1:8983/solr/

   * **[!UICONTROL Solr-Sammlung]**

      *Standard*: collection1

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

### Null Schritte zur Migration von Ausfallzeiten für Standard {#zerodt-migration-steps}

Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die Standardseite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) erwartungsgemäß funktioniert:

1. Benennen Sie den Pfad unter `/etc/socialconfig` in `/etc/socialconfig_old` um, sodass die Systemkonfiguration auf &quot;jsrp(default)&quot;zurückfällt.
1. Gehen Sie zur Standardseite [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), auf der jsrp konfiguriert ist. Klicken Sie auf die Schaltfläche **[!UICONTROL submit]**, damit ein neuer Standardkonfigurationsknoten unter `/conf/global/settings/community/srpc` erstellt wird.
1. Löschen Sie die erstellte Standardkonfiguration `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Kopieren Sie die alte Konfiguration `/etc/socialconfig_old/srpc/defaultconfiguration` anstelle des gelöschten Knotens (`/conf/global/settings/community/srpc/defaultconfiguration`) im vorherigen Schritt.
1. Löschen Sie den alten etc-Knoten `/etc/socialconfig_old`.

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

DSRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die gleiche Konfiguration in der Umgebung &quot;Veröffentlichen&quot;zur Verfügung:

* Beim Autor:

   * Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**
   * Doppelklicken Sie auf **[!UICONTROL Tree aktivieren]**
   * **Startpfad**:

      * Gehen Sie zu `/etc/socialconfig/srpc/`
   * Vergewissern Sie sich, dass `Only Modified` nicht ausgewählt ist.
   * Wählen Sie **[!UICONTROL Aktivieren]**.


## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzergruppen*, *Benutzergruppen* und *die häufig in die Umgebung &quot;Veröffentlichen&quot;eingegeben werden, finden Sie unter*

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Solr für die Neudeaktivierung für DSRP {#reindexing-solr-for-dsrp}

Um DSRP Solr neu zu indizieren, befolgen Sie die Dokumentation für [MSRP](msrp.md#msrp-reindex-tool) neu zu dezieren. Verwenden Sie jedoch bei der Neudezierung für DSRP die folgende URL: **/services/social/datastore/rdb/reindex**

Beispielsweise würde ein Befehl zum erneuten Indexieren von DSRP wie folgt aussehen:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```

