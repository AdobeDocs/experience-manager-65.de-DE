---
title: MSRP - MongoDB Storage Resource Provider
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 799d5ae1-caac-4c92-8835-696ad25de553
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 1%

---

# MSRP - MongoDB Storage Resource Provider {#msrp-mongodb-storage-resource-provider}

## Über MSRP {#about-msrp}

Wenn AEM Communities so konfiguriert ist, dass MSRP als gemeinsamer Speicher verwendet wird, kann von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte (UGC) zugegriffen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

* [MongoDB](https://www.mongodb.org/):

   * Version 2.6 oder höher
   * Keine Konfiguration von Mongos oder Freigabe erforderlich
   * empfiehlt dringend die Verwendung eines [Replikationssatz](#mongoreplicaset)
   * Kann auf demselben Host wie AEM ausgeführt oder remote ausgeführt werden

* [Apache Solr](https://lucene.apache.org/solr/):

   * Solr-Version 7.0
   * Solr erfordert Java 1.7 oder höher
   * Es ist kein Dienst erforderlich
   * Auswahl der Ausführungsmodi:
      * Standalone-Modus
      * [SolrCloud-Modus](solr.md#solrcloud-mode) (empfohlen für Produktionsumgebungen)
   * Auswahl der mehrsprachigen Suche (MLS):
      * [Installieren von Standard-MLS](solr.md#installing-standard-mls)
      * [Installieren erweiterter MLS](solr.md#installing-advanced-mls)

## MongoDB-Konfiguration {#mongodb-configuration}

### MSRP auswählen {#select-msrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

Auf der Autoreninstanz, um auf die Konsole Speicherkonfiguration zuzugreifen:

* Wählen Sie in der globalen Navigation die Option **[!UICONTROL Instrumente]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]**.

![msrp](assets/msrp.png)

* Auswählen **[!UICONTROL MongoDB Storage Resource Provider (MSRP)]**
* **[!UICONTROL mongoDB-Konfiguration]**

   * **[!UICONTROL mongoDB URI]**

     *default*: mongodb://localhost/?maxPoolSize=10&amp;waitQueueMultiple=5&amp;readPreference=secondaryPreferred

   * **[!UICONTROL mongoDB-Datenbank]**

     *default*: communities

   * **[!UICONTROL mongoDB UGC Collection]**

     *default*: content

   * **[!UICONTROL mongoDB Attachment Collection]**

     *default*: Anlagen

* **[!UICONTROL SolrConfiguration]**

   * **[Zookeeper](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files) Host**

     Bei Ausführung in [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper festlegen, setzen Sie diesen Wert auf `HOST:PORT` für den ZooKeeper, beispielsweise *my.server.com:2181*

     Für ein ZooKeeper-Ensemble geben Sie durch Kommas getrennt ein. `HOST:PORT` -Werte, z. B. *Host1:2181,Host2:2181*

     Lassen Sie bei Ausführung von Solr im eigenständigen Modus mit dem internen ZooKeeper leer.
     *Standard*: *&lt;blank>*

      * **[!UICONTROL Solr-URL]**
Die URL, die zur Kommunikation mit Solr im eigenständigen Modus verwendet wird.
Lassen Sie bei Ausführung im SolrCloud-Modus leer.
        *Standard*: https://127.0.0.1:8983/solr/

      * **[!UICONTROL Solr-Sammlung]**
Der Solr-Sammlungsname.
        *Standard*: collection1

* Klicken Sie auf **[!UICONTROL Übermitteln]**

>[!NOTE]
>
>Die mongoDB-Datenbank, die standardmäßig auf den Namen `communities`darf nicht auf den Namen einer Datenbank gesetzt werden, für die [Knotenspeicher oder (binäre) Datenspeicher](../../help/sites-deploying/data-store-config.md). Siehe auch [Speicherelemente in AEM 6.5](../../help/sites-deploying/storage-elements-in-aem-6.md).

### MongoDB-Replikat-Set {#mongodb-replica-set}

Für die Produktionsumgebung wird dringend empfohlen, einen Replikatsatz einzurichten, einen Cluster von MongoDB-Servern, der die primäre sekundäre Replikation und automatisiertes Failover implementiert.

Weitere Informationen zu Replikationssets finden Sie in den [Replikation](https://docs.mongodb.org/manual/replication/) Dokumentation.

Um mit Replikatsätzen zu arbeiten und zu erfahren, wie Sie Verbindungen zwischen Anwendungen und MongoDB-Instanzen definieren, besuchen Sie MongoDB&#39;s [Verbindungszeichenfolge-URI-Format](https://docs.mongodb.org/manual/reference/connection-string/) Dokumentation.

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

Für Produktionsumgebungen: [SolrCloud-Modus](solr.md#solrcloud-mode) bietet eine verbesserte Leistung gegenüber dem eigenständigen Modus (ein einzelnes lokales Solr-Setup).

Weitere Informationen zur Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### Upgrade {#upgrading}

Wenn Sie von einer früheren Version aktualisieren, die mit MSRP konfiguriert wurde, müssen Sie:

1. Führen Sie die [Upgrade auf AEM Communities](upgrade.md)
1. Installieren neuer Solr-Konfigurationsdateien
   * Für [Standard-MLS](solr.md#installing-standard-mls)
   * Für [erweiterte MLS](solr.md#installing-advanced-mls)
1. Neuindizieren von MSRP Siehe Abschnitt [MSRP-Neuindizierungs-Tool](#msrp-reindex-tool)

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

MSRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

Um die identische Konfiguration in der Veröffentlichungsumgebung verfügbar zu machen, melden Sie sich bei Ihrer Autoreninstanz an und führen Sie die folgenden Schritte aus:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Replikation]**.
* Auswählen **[!UICONTROL Baum aktivieren]**
* **[!UICONTROL Startpfad]**:
   * Navigieren Sie zu `/etc/socialconfig/srpc/`
* Auswählen **[!UICONTROL Aktivieren]**

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen über *Benutzer*, *Benutzerprofile* und *Benutzergruppen*, häufig in die Veröffentlichungsumgebung eingegeben, Besuch

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## MSRP-Neuindizierungs-Tool {#msrp-reindex-tool}

Es gibt einen HTTP-Endpunkt für die Neuindizierung von Solr für MSRP bei der Installation neuer Konfigurationsdateien oder der Reparatur eines beschädigten Solr-Index.

Mit diesem Tool ist MongoDB die Quelle von *Wahrheit* für MSRP; Sicherungen müssen nur von MongoDB vorgenommen werden.

Die gesamte UGC-Struktur kann neu indiziert werden oder nur eine bestimmte Unterstruktur, wie durch den Parameter *path *data angegeben.

Dieses Tool kann über die Befehlszeile mit cURL oder einem anderen HTTP-Tool ausgeführt werden.

Bei der Neuindizierung gibt es einen Kompromiss zwischen Speicher und Leistung, der durch den *batchSize *data -Parameter gesteuert wird, der angibt, wie viele UGC-Datensätze pro Batch neu indiziert werden.

Der angemessene Standardwert ist 5000:

* Wenn der Speicher ein Problem darstellt, geben Sie eine kleinere Zahl an
* Wenn die Geschwindigkeit ein Problem darstellt, geben Sie eine größere Zahl an, um die Geschwindigkeit zu erhöhen

### Ausführen des MSRP-Reindex-Tools mithilfe des cURL-Befehls {#running-msrp-reindex-tool-using-curl-command}

Der folgende cURL-Befehl zeigt, was erforderlich ist, damit eine HTTP-Anforderung UGC neu indiziert, die in MSRP gespeichert ist.

Das Standardformat lautet:

cURL -u *Anmelden* -d *data* *reindex-url*

*Anmelden* = administrator-id:password Beispiel: admin:admin

*data* = &quot;batchSize=*size*&amp;path=*path&quot;*

*size* = wie viele UGC-Einträge pro Vorgang neu indiziert werden sollen
`/content/usergenerated/asi/mongo/`

*path* = der Stammspeicherort des Baums der zu neu indizierten UGC

* Um alle benutzergenerierten Inhalte neu zu indizieren, geben Sie den Wert der `asipath`Eigenschaft von
  `/etc/socialconfig/srpc/defaultconfiguration`
* Um den Index auf einige UGC zu beschränken, geben Sie eine Unterstruktur von `asipath`

*reindex-url* = Endpunkt für die Neuindizierung von SRP
`http://localhost:4503/services/social/datastore/mongo/reindex`

>[!NOTE]
>
>Wenn Sie [Neuindizierung von DSRP Solr](dsrp.md), lautet die URL . **/services/social/datastore/rdb/reindex**

### MSRP-Neuindizierungsbeispiel {#msrp-reindex-example}

```shell
curl -s -u admin:admin -d 'batchSize=10000&path=/content/usergenerated/asi/mongo/' http://localhost:4503/services/social/datastore/mongo/reindex
```

## Demo von MSRP {#how-to-demo-msrp}

Informationen zum Einrichten von MSRP für eine Demonstrations- oder Entwicklungsumgebung finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

## Fehlerbehebung {#troubleshooting}

### UGC nicht in MongoDB sichtbar {#ugc-not-visible-in-mongodb}

Stellen Sie sicher, dass MSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption aktivieren. Standardmäßig ist der Speicher-Ressourcenanbieter JSRP.

Rufen Sie auf allen Autoren- und Veröffentlichungsinstanzen AEM erneut die [Speicherkonfigurationskonsole](srp-config.md) oder überprüfen Sie das AEM-Repository:

* Wenn in JCR [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Enthält keine [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) -Knoten bedeutet, dass der Speicheranbieter JSRP ist.
   * Wenn der Knoten srpc vorhanden ist und den Knoten enthält [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), sollten die Eigenschaften der Standardkonfiguration MSRP als Standardanbieter definieren.

### UGC verschwindet nach der Aktualisierung {#ugc-disappears-after-upgrade}

Bei der Aktualisierung von einer vorhandenen AEM Communities 6.0-Site müssen alle bereits vorhandenen benutzergenerierten Inhalte so konvertiert werden, dass sie der für die [SRP](srp.md) API nach der Aktualisierung auf AEM Communities 6.3.

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

So beheben Sie den Fehler, wenn Sie die Anweisungen für [Installieren von Standard-MLS](solr.md#installing-standard-mls)sicherstellen, dass

* Die XML-Konfigurationsdateien wurden an den richtigen Solr-Speicherort kopiert.
* Solr wurde neu gestartet, nachdem die neuen Konfigurationsdateien die vorhandenen ersetzt haben.

### Sichere Verbindung zu MongoDB schlägt fehl {#secure-connection-to-mongodb-fails}

Wenn ein Versuch, eine gesicherte Verbindung zum MongoDB-Server herzustellen, aufgrund einer fehlenden Klassendefinition fehlschlägt, ist es erforderlich, das MongoDB-Treiberpaket zu aktualisieren. `mongo-java-driver`, verfügbar über das öffentliche Maven-Repository.

1. Laden Sie den Treiber von herunter. [https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar](https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar) (Version 2.13.2 oder höher).
1. Kopieren Sie das Bundle in den Ordner &quot;crx-quickstart/install&quot;für eine AEM Instanz.
1. Starten Sie die AEM-Instanz neu.

## Ressourcen {#resources}

* [AEM mit MongoDB](../../help/sites-deploying/aem-with-mongodb.md)
* [MongoDB-Dokumentation](https://docs.mongodb.org/)
