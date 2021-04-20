---
title: MSRP - MongoDB Datenspeicherung Resource Provider
seo-title: MSRP - MongoDB Datenspeicherung Resource Provider
description: AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher einrichten
seo-description: AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher einrichten
uuid: 9fc06d4f-a60f-4ce3-8586-bcc836aa7de6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 048f7b30-20c3-4567-bd32-38cf2643cf39
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 3%

---


# MSRP - MongoDB Datenspeicherung Resource Provider {#msrp-mongodb-storage-resource-provider}

## Über MSRP {#about-msrp}

Wenn AEM Communities so konfiguriert ist, dass MSRP als gemeinsamer Speicher verwendet wird, können vom Benutzer generierte Inhalte (UGC) von allen Autor- und Veröffentlichungsinstanzen aus aufgerufen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

* [MongoDB](https://www.mongodb.org/):

   * Version 2.6 oder höher
   * Keine Konfiguration von Mongos oder Freigeben erforderlich
   * Empfehlen Sie dringend die Verwendung eines [Replikationssatzes](#mongoreplicaset)
   * Kann auf demselben Host ausgeführt werden wie AEM oder remote ausgeführt werden

* [Apache Solr](https://lucene.apache.org/solr/):

   * Solr-Version 7.0
   * Solr erfordert Java 1.7 oder höher
   * Es ist kein Dienst erforderlich
   * Auswahl der Ausführungsmodi:
      * Standalone-Modus
      * [SolrCloud-Modus](solr.md#solrcloud-mode)  (empfohlen für Produktionsumgebungen)
   * Auswahl der mehrsprachigen Suche (MLS):
      * [Installieren von Standard MLS](solr.md#installing-standard-mls)
      * [Installieren von erweiterten MLS](solr.md#installing-advanced-mls)

## MongoDB-Konfiguration {#mongodb-configuration}

### Wählen Sie MSRP {#select-msrp}

Die [Datenspeicherung Configuration Console](srp-config.md) ermöglicht die Auswahl der Standardkonfiguration der Datenspeicherung, die die zu verwendende Implementierung von SRP identifiziert.

Wenn Sie Autor sind, können Sie auf die Datenspeicherung Configuration Console zugreifen:

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Datenspeicherung Configuration]**.

![msrp](assets/msrp.png)

* Wählen Sie **[!UICONTROL MongoDB Datenspeicherung Resource Provider (MSRP)]**
* **[!UICONTROL mongoDB-Konfiguration]**

   * **[!UICONTROL mongoDB-URI]**

      *Standard*: mongodb://localhost/?maxPoolSize=10&amp;waitQueueMultiple=5&amp;readPreference=secondaryPreferred

   * **[!UICONTROL mongoDB-Datenbank]**

      *Standard*: Communities

   * **[!UICONTROL mongoDB-UGC-Sammlung]**

      *Standard*: content

   * **[!UICONTROL mongoDB-Anlagensammlung]**

      *Standard*: Anlagen

* **[!UICONTROL SolrConfiguration]**

   * **[](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files)Zookeeper-Host**

      Wenn Sie im [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper ausgeführt werden, stellen Sie diesen Wert für den ZooKeeper auf `HOST:PORT` ein, z. B. *my.server.com:2181*

      Geben Sie für ein ZooKeeper-Ensemble kommagetrennte `HOST:PORT`-Werte ein, z. B. *host1:2181,host2:2181*

      Lassen Sie beim Ausführen von Solr im eigenständigen Modus mit dem internen ZooKeeper leer.
      *Standard*:  *&lt;blank>*

      * **[!UICONTROL Solr]**
URLTdie URL, die für die Kommunikation mit Solr im eigenständigen Modus verwendet wird.
Lassen Sie beim Ausführen im SolrCloud-Modus leer.

         *Standard*: https://127.0.0.1:8983/solr/

      * **[!UICONTROL Solr-]**
SammlungDer Name der Solr-Sammlung.

         *Standard*: collection1

* Klicken Sie auf **[!UICONTROL Übermitteln]**

>[!NOTE]
>
>Die mongoDB-Datenbank, die standardmäßig den Namen `communities` verwendet, sollte nicht auf den Namen einer Datenbank eingestellt werden, die für [Knotenspeicher oder Datenspeicher (Binärspeicher)](../../help/sites-deploying/data-store-config.md) verwendet wird. Siehe auch [Datenspeicherung Elemente in AEM 6.5](../../help/sites-deploying/storage-elements-in-aem-6.md).

### MongoDB Replikat Set {#mongodb-replica-set}

Für die Umgebung der Produktion wird dringend empfohlen, einen Replikationssatz, einen Cluster aus MongoDB-Servern einzurichten, der die primäre und sekundäre Replikation und automatisiertes Failover implementiert.

Weitere Informationen zu Replikationssets finden Sie in der MongoDB-Dokumentation [Replication](https://docs.mongodb.org/manual/replication/).

Informationen zum Arbeiten mit Replikationssets und zum Definieren von Verbindungen zwischen Anwendungen und MongoDB-Instanzen finden Sie in der Dokumentation zu MongoDB [Verbindungszeichenfolgen-URI-Format](https://docs.mongodb.org/manual/reference/connection-string/).

#### Beispiel-URL für die Verbindung mit einem Replikat-Set {#example-url-for-connecting-to-a-replica-set}

```shell
# Example url for:
# servers "mongoserver1", "mongoserver2", "mongoserver3"
# replica set 'rs0'
# port numbers only necessary if not default port 27017
mongodb://mongoserver1:<mongoport1>,mongoserver2:<mongoport2>,mongoserver3:<mongoport3>/?replicaSet=rs0&maxPoolSize=100&waitQueueMultiple=50&readPreference=secondaryPreferred
```

## Solr-Konfiguration {#solr-configuration}

Eine Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Node Store (Oak) und dem Common Store (MSRP) freigegeben werden.

Wenn sowohl die Oak- als auch die MSRP-Kollektionen intensiv verwendet werden, kann aus Leistungsgründen ein zweiter Solr installiert werden.

Bei Produktions-Umgebung bietet [SolrCloud-Modus](solr.md#solrcloud-mode) eine verbesserte Leistung im Standalone-Modus (ein einzelnes, lokales Solr-Setup).

Weitere Informationen zur Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### Aktualisieren {#upgrading}

Wenn Sie von einer früheren Version aktualisieren, die mit MSRP konfiguriert wurde, müssen Sie:

1. Führen Sie das [Upgrade auf AEM Communities](upgrade.md) durch
1. Neue Solr-Konfigurationsdateien installieren
   * Für [Standard-MLS](solr.md#installing-standard-mls)
   * Für [erweiterte MLS](solr.md#installing-advanced-mls)
1. Reindex MSRP
Siehe Abschnitt [MSRP Reindex Tool](#msrp-reindex-tool)

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

MSRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

Um die gleiche Konfiguration in der Umgebung &quot;Veröffentlichen&quot;verfügbar zu machen, melden Sie sich bei Ihrer Autoreninstanz an und führen Sie die folgenden Schritte aus:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**.
* Wählen Sie **[!UICONTROL Baum aktivieren]**
* **[!UICONTROL Startpfad]**:
   * Gehen Sie zu `/etc/socialconfig/srpc/`
* Wählen Sie **[!UICONTROL Aktivieren]**

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzergruppen*, *Benutzergruppen* und *die häufig in die Umgebung &quot;Veröffentlichen&quot;eingegeben wurden, finden Sie unter*

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## MSRP Reindex Tool {#msrp-reindex-tool}

Es gibt einen HTTP-Endpunkt zum erneuten Dekodieren von Solr für MSRP, wenn neue Konfigurationsdateien installiert oder ein beschädigter Solr-Index repariert werden.

Mit diesem Tool ist MongoDB die Quelle von *true* für MSRP; Backups müssen nur von MongoDB durchgeführt werden.

Der gesamte UGC-Baum kann neu definiert werden, oder nur ein bestimmter Unterbaum, wie im *path *data-Parameter angegeben.

Dieses Tool kann über die Befehlszeile mit cURL oder einem anderen HTTP-Tool ausgeführt werden.

Bei der Neudezierung gibt es einen Kompromiss zwischen Speicher und Leistung, der durch den *batchSize *data-Parameter gesteuert wird, der angibt, wie viele UGC-Datensätze pro Stapel neu deklariert werden.

Ein angemessener Standardwert ist 5000:

* Wenn der Speicher ein Problem darstellt, geben Sie eine kleinere Zahl an
* Wenn die Geschwindigkeit ein Problem ist, geben Sie eine größere Zahl an, um die Geschwindigkeit zu erhöhen

### Ausführen des MSRP-Reindex-Tools mit dem cURL-Befehl {#running-msrp-reindex-tool-using-curl-command}

Der folgende cURL-Befehl zeigt, was für eine HTTP-Anforderung erforderlich ist, um UGC neu zu indizieren, die in MSRP gespeichert ist.

Das Basisformat lautet:

cURL -u *Anmelden* -d *data* *reindex-url*

*sign* = administrator-id:password Beispiel: admin:admin

*data* = &quot;batchSize=*size*&amp;path=*path&quot;*

*size* = wie viele UGC-Einträge pro Operation neu indiziert werden 
`/content/usergenerated/asi/mongo/`

*path* = die Stammposition des Baums von UGC zu reindex

* Um alle UGC neu zu indizieren, geben Sie den Wert der `asipath`Eigenschaft von
   `/etc/socialconfig/srpc/defaultconfiguration`
* Um den Index auf einige UGC zu beschränken, geben Sie eine Unterstruktur von `asipath` an

*reindex-url* = Endpunkt für die Wiederverwendung von SRP 
`http://localhost:4503/services/social/datastore/mongo/reindex`

>[!NOTE]
>
>Wenn Sie die DSRP Solr [neu dezimieren, lautet die URL **/services/social/datastore/rdb/reindex**](dsrp.md)

### MSRP Reindex Beispiel {#msrp-reindex-example}

```shell
curl -s -u admin:admin -d 'batchSize=10000&path=/content/usergenerated/asi/mongo/' http://localhost:4503/services/social/datastore/mongo/reindex
```

## Demo von MSRP {#how-to-demo-msrp}

Informationen zum Einrichten von MSRP für eine Demo- oder Development-Umgebung finden Sie unter [Wie Sie MongoDB für Demo](demo-mongo.md) einrichten.

## Fehlerbehebung {#troubleshooting}

### UGC nicht sichtbar in MongoDB {#ugc-not-visible-in-mongodb}

Vergewissern Sie sich, dass MSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfigurationsoption der Datenspeicherung überprüfen. Standardmäßig ist der Datenspeicherung Resource Provider JSRP.

Rufen Sie auf allen Instanzen im Autoren- und Veröffentlichungsmodus AEM [Datenspeicherung Configuration Console](srp-config.md) erneut auf oder überprüfen Sie das AEM Repository:

* In JCR, wenn [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Enthält keinen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc)-Knoten, bedeutet dies, dass der Datenspeicherung-Provider JSRP ist.
   * Wenn der Knoten srpc vorhanden ist und den Knoten [defaultConfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der Standardkonfiguration MSRP als Standardanbieter definieren.

### UGC verschwindet nach der Aktualisierung {#ugc-disappears-after-upgrade}

Bei der Aktualisierung von einer bestehenden AEM Communities 6.0-Site müssen alle bereits vorhandenen UGC konvertiert werden, um der für die [SRP](srp.md)-API nach der Aktualisierung auf AEM Communities 6.3 erforderlichen Struktur zu entsprechen.

Zu diesem Zweck steht auf GitHub ein Open-Source-Tool zur Verfügung:

* [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

Das Migrationswerkzeug kann angepasst werden, um UGC aus früheren Versionen AEM Social Communities für den Import in AEM Communities 6.1 oder höher zu exportieren.

### Fehler - undefiniertes Feld provider_id {#error-undefined-field-provider-id}

Wenn der folgende Fehler in den Protokollen angezeigt wird, deutet dies darauf hin, dass die SOR-Schema-Datei nicht richtig konfiguriert ist.

#### JsonMappingException: undefined field provider_id {#jsonmappingexception-undefined-field-provider-id}

```xml
Caused by: com.fasterxml.jackson.databind.JsonMappingException: undefined field provider_id
at com.fasterxml.jackson.databind.ser.DefaultSerializerProvider.serializeValue(DefaultSerializerProvider.java:129)
at com.fasterxml.jackson.databind.ObjectMapper.writeValue(ObjectMapper.java:1819)
at com.adobe.cq.social.scf.core.BaseSocialComponent.toJSONString(BaseSocialComponent.java:196)
... 124 common frames omitted
```

Um den Fehler zu beheben, stellen Sie Folgendes sicher, wenn Sie die Anweisungen für [Installieren von Standard MLS](solr.md#installing-standard-mls) befolgen:

* Die XML-Konfigurationsdateien wurden in den richtigen Speicherort für Solr kopiert.
* Solr wurde neu gestartet, nachdem die neuen Konfigurationsdateien die vorhandenen ersetzt haben.

### Sichere Verbindung zu MongoDB fehlschlägt {#secure-connection-to-mongodb-fails}

Wenn ein Versuch, eine gesicherte Verbindung zum MongoDB-Server herzustellen aufgrund einer fehlenden Klassendefinition fehlschlägt, ist es notwendig, das MongoDB-Treiberpaket `mongo-java-driver` zu aktualisieren, das im öffentlichen Repository verfügbar ist.

1. Laden Sie den Treiber von [https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar](https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar) (Version 2.13.2 oder höher) herunter.
1. Kopieren Sie das Bundle für eine AEM Instanz in den Ordner &quot;crx-quickstart/install&quot;.
1. Starten Sie die AEM-Instanz neu.

## Ressourcen {#resources}

* [AEM mit MongoDB](../../help/sites-deploying/aem-with-mongodb.md)
* [MongoDB-Dokumentation](https://docs.mongodb.org/)

