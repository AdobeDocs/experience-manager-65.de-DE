---
title: MSRP - MongoDB Storage Resource Provider
seo-title: MSRP - MongoDB Storage Resource Provider
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
seo-description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
uuid: 9fc06d4f-a60f-4ce3-8586-bcc836aa7de6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 048f7b30-20c3-4567-bd32-38cf2643cf39
role: Admin
exl-id: 799d5ae1-caac-4c92-8835-696ad25de553
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 3%

---

# MSRP - MongoDB Storage Resource Provider {#msrp-mongodb-storage-resource-provider}

## Über MSRP {#about-msrp}

Wenn AEM Communities so konfiguriert ist, dass MSRP als gemeinsamer Speicher verwendet wird, kann von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte (UGC) zugegriffen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

* [MongoDB](https://www.mongodb.org/):

   * Version 2.6 oder höher
   * Keine Konfiguration von Mongos oder Freigabe erforderlich
   * Die Verwendung eines [Replikatsatzes](#mongoreplicaset) wird dringend empfohlen
   * Kann auf demselben Host wie AEM ausgeführt oder remote ausgeführt werden

* [Apache Solr](https://lucene.apache.org/solr/):

   * Solr-Version 7.0
   * Solr erfordert Java 1.7 oder höher
   * Es ist kein Dienst erforderlich
   * Auswahl der Ausführungsmodi:
      * Standalone-Modus
      * [SolrCloud-Modus](solr.md#solrcloud-mode)  (empfohlen für Produktionsumgebungen)
   * Auswahl der mehrsprachigen Suche (MLS):
      * [Installieren von Standard-MLS](solr.md#installing-standard-mls)
      * [Installieren erweiterter MLS](solr.md#installing-advanced-mls)

## MongoDB-Konfiguration {#mongodb-configuration}

### MSRP auswählen {#select-msrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

Auf der Autoreninstanz, um auf die Konsole Speicherkonfiguration zuzugreifen:

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]** aus.

![msrp](assets/msrp.png)

* Wählen Sie **[!UICONTROL MongoDB Storage Resource Provider (MSRP)]** aus.
* **[!UICONTROL mongoDB-Konfiguration]**

   * **[!UICONTROL mongoDB-URI]**

      *Standard*: mongodb://localhost/?maxPoolSize=10&amp;waitQueueMultiple=5&amp;readPreference=secondaryPreferred

   * **[!UICONTROL mongoDB-Datenbank]**

      *Standard*: communities

   * **[!UICONTROL mongoDB-UGC-Sammlung]**

      *Standard*: content

   * **[!UICONTROL mongoDB-Anlagensammlung]**

      *Standard*: Anlagen

* **[!UICONTROL SolrConfiguration]**

   * **[](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files)Zookeeper-Host**

      Legen Sie bei Ausführung im [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper diesen Wert auf `HOST:PORT` für den ZooKeeper fest, z. B. *my.server.com:2181*

      Geben Sie für ein ZooKeeper-Ensemble durch Kommas getrennte `HOST:PORT`-Werte ein, z. B. *host1:2181,host2:2181*

      Lassen Sie bei Ausführung von Solr im eigenständigen Modus mit dem internen ZooKeeper leer.
      *Standard*:  *&lt;blank>*

      * **[!UICONTROL Solr]**
URLTDie URL, die für die Kommunikation mit Solr im eigenständigen Modus verwendet wird.
Lassen Sie bei Ausführung im SolrCloud-Modus leer.

         *Standard*: https://127.0.0.1:8983/solr/

      * **[!UICONTROL Solr]**
CollectionDer Solr-Sammlungsname.

         *Standard*: collection1

* Klicken Sie auf **[!UICONTROL Übermitteln]**

>[!NOTE]
>
>Die mongoDB-Datenbank, die standardmäßig den Namen `communities` trägt, sollte nicht auf den Namen einer Datenbank gesetzt werden, die für [Knotenspeicher oder (binäre) Datenspeicher](../../help/sites-deploying/data-store-config.md) verwendet wird. Siehe auch [Speicherelemente in AEM 6.5](../../help/sites-deploying/storage-elements-in-aem-6.md).

### MongoDB-Replikat-Set {#mongodb-replica-set}

Für die Produktionsumgebung wird dringend empfohlen, einen Replikatsatz einzurichten, einen Cluster von MongoDB-Servern, der die primäre sekundäre Replikation und automatisiertes Failover implementiert.

Weitere Informationen zu Replikationssets finden Sie in der Dokumentation zu MongoDB [Replikation](https://docs.mongodb.org/manual/replication/).

Informationen zum Arbeiten mit Replikatsätzen und zum Definieren von Verbindungen zwischen Anwendungen und MongoDB-Instanzen finden Sie in der Dokumentation zu MongoDB [Connection String URI Format](https://docs.mongodb.org/manual/reference/connection-string/).

#### Beispiel-URL für die Verbindung zu einem Replikat-Set  {#example-url-for-connecting-to-a-replica-set}

```shell
# Example url for:
# servers "mongoserver1", "mongoserver2", "mongoserver3"
# replica set 'rs0'
# port numbers only necessary if not default port 27017
mongodb://mongoserver1:<mongoport1>,mongoserver2:<mongoport2>,mongoserver3:<mongoport3>/?replicaSet=rs0&maxPoolSize=100&waitQueueMultiple=50&readPreference=secondaryPreferred
```

## Solr-Konfiguration {#solr-configuration}

Eine Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Knotenspeicher (Oak) und dem allgemeinen Speicher (MSRP) freigegeben werden.

Wenn sowohl die Oak- als auch die MSRP-Kollektionen intensiv verwendet werden, kann aus Leistungsgründen ein zweiter Solr installiert werden.

Für Produktionsumgebungen bietet der [SolrCloud-Modus](solr.md#solrcloud-mode) eine verbesserte Leistung im Vergleich zum eigenständigen Modus (ein einzelnes lokales Solr-Setup).

Weitere Informationen zur Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### Aktualisieren {#upgrading}

Wenn Sie von einer früheren Version aktualisieren, die mit MSRP konfiguriert wurde, müssen Sie:

1. Führen Sie das [Upgrade auf AEM Communities](upgrade.md) durch.
1. Installieren neuer Solr-Konfigurationsdateien
   * Für [Standard-MLS](solr.md#installing-standard-mls)
   * Für [erweiterte MLS](solr.md#installing-advanced-mls)
1. Reindex MSRP
Siehe Abschnitt [MSRP Reindex Tool](#msrp-reindex-tool)

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

MSRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

Um die identische Konfiguration in der Veröffentlichungsumgebung verfügbar zu machen, melden Sie sich bei Ihrer Autoreninstanz an und führen Sie die folgenden Schritte aus:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**.
* Wählen Sie **[!UICONTROL Baum aktivieren]**
* **[!UICONTROL Startpfad]**:
   * Navigieren Sie zu `/etc/socialconfig/srpc/`
* Wählen Sie **[!UICONTROL Activate]**

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## MSRP-Reindex-Tool {#msrp-reindex-tool}

Es gibt einen HTTP-Endpunkt für die Neuindizierung von Solr für MSRP bei der Installation neuer Konfigurationsdateien oder der Reparatur eines beschädigten Solr-Index.

Mit diesem Tool ist MongoDB die Quelle von *Truth* für MSRP. Sicherungen müssen nur von MongoDB vorgenommen werden.

Die gesamte UGC-Struktur kann neu indiziert werden oder nur eine bestimmte Unterstruktur, wie durch den Parameter *path *data angegeben.

Dieses Tool kann über die Befehlszeile mit cURL oder einem anderen HTTP-Tool ausgeführt werden.

Bei der Neuindizierung gibt es einen Kompromiss zwischen Speicher und Leistung, der durch den *batchSize *data -Parameter gesteuert wird, der angibt, wie viele UGC-Datensätze pro Batch neu indiziert werden.

Der angemessene Standardwert ist 5000:

* Wenn der Speicher ein Problem darstellt, geben Sie eine kleinere Zahl an
* Wenn die Geschwindigkeit ein Problem darstellt, geben Sie eine größere Zahl an, um die Geschwindigkeit zu erhöhen

### Ausführen des MSRP-Reindex-Tools mithilfe des cURL-Befehls {#running-msrp-reindex-tool-using-curl-command}

Der folgende cURL-Befehl zeigt, was erforderlich ist, damit eine HTTP-Anforderung UGC neu indiziert, die in MSRP gespeichert ist.

Das Standardformat lautet:

cURL -u *signin* -d *data* *reindex-url*

*signin* = administrator-id:password Beispiel: admin:admin

*data* = &quot;batchSize=*size*&amp;path=*path&quot;*

*size*  = wie viele UGC-Einträge pro Vorgang neu indiziert werden sollen 
`/content/usergenerated/asi/mongo/`

*path*  = der Stammspeicherort des Baums der zu neu indizierten UGC

* Um alle benutzergenerierten Inhalte neu zu indizieren, geben Sie den Wert der `asipath`Eigenschaft von
   `/etc/socialconfig/srpc/defaultconfiguration`
* Um den Index auf einige UGC zu beschränken, geben Sie eine Unterstruktur von `asipath` an

*reindex-url*  = Endpunkt für die Neuindizierung von SRP 
`http://localhost:4503/services/social/datastore/mongo/reindex`

>[!NOTE]
>
>Wenn Sie [die Neuindizierung von DSRP Solr](dsrp.md) durchführen, lautet die URL **/services/social/datastore/rdb/reindex**

### MSRP-Neuindizierungsbeispiel {#msrp-reindex-example}

```shell
curl -s -u admin:admin -d 'batchSize=10000&path=/content/usergenerated/asi/mongo/' http://localhost:4503/services/social/datastore/mongo/reindex
```

## Demo von MSRP {#how-to-demo-msrp}

Informationen zum Einrichten von MSRP für eine Demonstrations- oder Entwicklungsumgebung finden Sie unter [So richten Sie MongoDB für Demo](demo-mongo.md) ein.

## Fehlerbehebung {#troubleshooting}

### UGC nicht in MongoDB sichtbar {#ugc-not-visible-in-mongodb}

Stellen Sie sicher, dass MSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption aktivieren. Standardmäßig ist der Speicher-Ressourcenanbieter JSRP.

Rufen Sie auf allen Autoren- und Veröffentlichungsinstanzen AEM [Speicherkonfigurationskonsole](srp-config.md) erneut auf oder überprüfen Sie das AEM Repository:

* In JCR, wenn [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Enthält keinen Knoten [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc), bedeutet dies, dass der Speicheranbieter JSRP ist.
   * Wenn der Knoten srpc vorhanden ist und den Knoten [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der Standardkonfiguration MSRP als Standardanbieter definieren.

### UGC verschwindet nach der Aktualisierung {#ugc-disappears-after-upgrade}

Beim Upgrade von einer vorhandenen AEM Communities 6.0-Site müssen alle bereits vorhandenen UGC so konvertiert werden, dass sie der für die API [SRP](srp.md) nach der Aktualisierung auf AEM Communities 6.3 erforderlichen Struktur entsprechen.

Zu diesem Zweck steht auf GitHub ein Open-Source-Tool zur Verfügung:

* [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

Das Migrationswerkzeug kann angepasst werden, um benutzergenerierte Inhalte aus früheren Versionen AEM Social Communities für den Import in AEM Communities 6.1 oder höher zu exportieren.

### Fehler - nicht definiertes Feld provider_id {#error-undefined-field-provider-id}

Wenn der folgende Fehler in den Protokollen angezeigt wird, weist er darauf hin, dass die Solr-Schemadatei nicht ordnungsgemäß konfiguriert ist.

#### JsonMappingException: undefined field provider_id {#jsonmappingexception-undefined-field-provider-id}

```xml
Caused by: com.fasterxml.jackson.databind.JsonMappingException: undefined field provider_id
at com.fasterxml.jackson.databind.ser.DefaultSerializerProvider.serializeValue(DefaultSerializerProvider.java:129)
at com.fasterxml.jackson.databind.ObjectMapper.writeValue(ObjectMapper.java:1819)
at com.adobe.cq.social.scf.core.BaseSocialComponent.toJSONString(BaseSocialComponent.java:196)
... 124 common frames omitted
```

Um den Fehler zu beheben, stellen Sie beim Befolgen der Anweisungen für [Installieren von Standard-MLS](solr.md#installing-standard-mls) Folgendes sicher:

* Die XML-Konfigurationsdateien wurden an den richtigen Solr-Speicherort kopiert.
* Solr wurde neu gestartet, nachdem die neuen Konfigurationsdateien die vorhandenen ersetzt haben.

### Sichere Verbindung zu MongoDB schlägt fehl {#secure-connection-to-mongodb-fails}

Wenn ein Versuch, eine gesicherte Verbindung zum MongoDB-Server herzustellen, aufgrund einer fehlenden Klassendefinition fehlschlägt, ist es erforderlich, das MongoDB-Treiberpaket `mongo-java-driver` zu aktualisieren, das über das öffentliche Maven-Repository verfügbar ist.

1. Laden Sie den Treiber von [https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar](https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar) (Version 2.13.2 oder höher) herunter.
1. Kopieren Sie das Bundle in den Ordner &quot;crx-quickstart/install&quot;für eine AEM Instanz.
1. Starten Sie die AEM-Instanz neu.

## Ressourcen {#resources}

* [AEM mit MongoDB](../../help/sites-deploying/aem-with-mongodb.md)
* [MongoDB-Dokumentation](https://docs.mongodb.org/)
