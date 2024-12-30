---
title: MSRP - MongoDB Storage Resource Provider
description: Einrichten von AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 799d5ae1-caac-4c92-8835-696ad25de553
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 1%

---

# MSRP - MongoDB Storage Resource Provider {#msrp-mongodb-storage-resource-provider}

## Über MSRP {#about-msrp}

Wenn AEM Communities für die Verwendung von MSRP als gemeinsamen Speicher konfiguriert ist, können Sie von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte zugreifen, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Merkmale von SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Voraussetzungen {#requirements}

* [MongoDB](https://www.mongodb.org/):

   * Version 2.6 oder höher
   * Keine Notwendigkeit, Mongos oder Freigabe zu konfigurieren
   * Es wird dringend empfohlen, einen [Replikatsatz“ zu ](#mongoreplicaset)
   * Kann auf demselben Host wie AEM oder remote ausgeführt werden

* [Apache Solr](https://lucene.apache.org/solr/):

   * Solr-Version 7.0
   * Solr erfordert Java 1.7 oder höher
   * Es ist kein Service erforderlich
   * Auswahl der Ausführungsmodi:
      * Eigenständiger Modus
      * [SolrCloud-Modus](solr.md#solrcloud-mode) (für Produktionsumgebungen empfohlen)
   * Auswahl an mehrsprachiger Suche (MLS):
      * [Installieren von Standard-MLS](solr.md#installing-standard-mls)
      * [Erweiterte MLS installieren](solr.md#installing-advanced-mls)

## MongoDB-Konfiguration {#mongodb-configuration}

### MSRP auswählen {#select-msrp}

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen -Speicherkonfiguration, die angibt, welche Implementierung von SRP verwendet werden soll.

So greifen Sie auf der Autoreninstanz auf die Speicherkonfigurationskonsole zu:

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]**.

![MSRP](assets/msrp.png)

* Wählen Sie **[!UICONTROL MongoDB Storage Resource Provider (MSRP)]**
* **[!UICONTROL mongoDB-Konfiguration]**

   * **[!UICONTROL mongoDB-URI]**

     *default*: mongodb://localhost/?maxPoolSize=10&amp;waitQueueMultiple=5&amp;readPreference=secondaryPreferred

   * **[!UICONTROL mongoDB-Datenbank]**

     *Standard*: Communities

   * **[!UICONTROL mongoDB UGC-Sammlung]**

     *default*: content

   * **[!UICONTROL mongoDB-Anlagensammlung]**

     *Standard*: Anlagen

* **[!UICONTROL SolrConfiguration]**

   * **[ZooKeeper](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files) Host**

     Wenn Sie im [SolrCloud-Modus](solr.md#solrcloud-mode) mit einem externen ZooKeeper ausführen, setzen Sie diesen Wert auf den `HOST:PORT` für den ZooKeeper, z. B. *my.server.com:2181*

     Geben Sie für ein ZooKeeper-Ensemble durch Kommas getrennte `HOST:PORT` ein, z. B. *host1:2181,host2:2181*

     Leer lassen, wenn Solr im Einzelmodus mit dem internen ZooKeeper ausgeführt wird.
     *Standard*: *&lt;blank>*

      * **[!UICONTROL Solr-URL]**
Die URL, die für die Kommunikation mit Solr im eigenständigen Modus verwendet wird.
Leer lassen, wenn im SolrCloud-Modus ausgeführt wird.
        *Standard*: https://127.0.0.1:8983/solr/

      * **[!UICONTROL Solr-Sammlung]**
Der Solr-Sammlungsname.
        *Standard*: collection1

* Klicken Sie auf **[!UICONTROL Übermitteln]**

>[!NOTE]
>
>Die mongoDB-Datenbank, die standardmäßig den Namen `communities` hat, sollte nicht auf den Namen einer Datenbank eingestellt werden, die für [Knotenspeicher oder Datenspeicher (binäre) verwendet ](../../help/sites-deploying/data-store-config.md). Siehe auch [Speicherelemente in AEM 6.5](../../help/sites-deploying/storage-elements-in-aem-6.md).

### MongoDB-Replikat {#mongodb-replica-set}

Für die Produktionsumgebung wird dringend empfohlen, einen Replikationssatz einzurichten, einen Cluster von MongoDB-Servern, der die primäre und sekundäre Replikation und automatisiertes Failover implementiert.

Weitere Informationen zu Replikatsätzen finden Sie in der Dokumentation [Replikation](https://docs.mongodb.org/manual/replication/) von MongoDB.

Informationen zum Arbeiten mit Replikatgruppen und zum Definieren von Verbindungen zwischen Anwendungen und MongoDB-Instanzen finden Sie in der Dokumentation [Connection String URI Format](https://docs.mongodb.org/manual/reference/connection-string/) von MongoDB.

#### Beispiel-URL für das Verbinden mit einem Replikat-Set  {#example-url-for-connecting-to-a-replica-set}

```shell
# Example url for:
# servers "mongoserver1", "mongoserver2", "mongoserver3"
# replica set 'rs0'
# port numbers only necessary if not default port 27017
mongodb://mongoserver1:<mongoport1>,mongoserver2:<mongoport2>,mongoserver3:<mongoport3>/?replicaSet=rs0&maxPoolSize=100&waitQueueMultiple=50&readPreference=secondaryPreferred
```

## Solr-Konfiguration {#solr-configuration}

Eine Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Knotenspeicher (Oak) und dem allgemeinen Speicher (MSRP) gemeinsam genutzt werden.

Wenn sowohl die Oak- als auch die MSRP-Sammlung häufig verwendet werden, kann aus Leistungsgründen eine zweite Solr-Datei installiert werden.

In Produktionsumgebungen bietet [SolrCloud-Modus](solr.md#solrcloud-mode) eine verbesserte Leistung im Vergleich zum eigenständigen Modus (eine einzelne, lokale Solr-Einrichtung).

Weitere Informationen zur Konfiguration finden Sie unter [Solr-Konfiguration für SRP](solr.md).

### Aktualisieren {#upgrading}

Wenn Sie von einer früheren Version aktualisieren, die mit MSRP konfiguriert wurde, müssen Sie:

1. Führen Sie das [Upgrade auf AEM Communities&quot; ](upgrade.md)
1. Installieren neuer Solr-Konfigurationsdateien
   * Für [Standard-MLS](solr.md#installing-standard-mls)
   * Für [erweiterte MLS](solr.md#installing-advanced-mls)
1. MSRP neu indizieren
Siehe Abschnitt [MSRP Reindex Tool](#msrp-reindex-tool)

## Veröffentlichen der Konfiguration {#publishing-the-configuration}

MSRP muss auf allen Autoren- und Veröffentlichungsinstanzen als Common Store identifiziert werden.

Um die identische Konfiguration in der Veröffentlichungsumgebung verfügbar zu machen, melden Sie sich bei Ihrer Autoreninstanz an und führen Sie die folgenden Schritte aus:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**.
* Wählen Sie **[!UICONTROL Baum aktivieren]**
* **[!UICONTROL Startpfad]**:
   * Navigieren zu `/etc/socialconfig/srpc/`
* Wählen Sie **[!UICONTROL Aktivieren]**

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## MSRP-Neuindizierungs-Tool {#msrp-reindex-tool}

Es gibt einen HTTP-Endpunkt für die Neuindizierung von Solr für MSRP, wenn neue Konfigurationsdateien installiert oder ein beschädigter Solr-Index repariert wird.

Mit diesem Tool ist MongoDB die Quelle *Wahrheit* für MSRP. Sicherungen müssen nur von MongoDB durchgeführt werden.

Die gesamte Struktur des benutzergenerierten Inhalts kann neu indiziert werden oder nur eine bestimmte Unterstruktur, wie durch den Datenparameter *path* angegeben.

Dieses Tool kann über die Befehlszeile mit cURL oder einem anderen HTTP-Tool ausgeführt werden.

Bei der Neuindizierung gibt es einen Kompromiss zwischen Speicher und Leistung, der durch den Datenparameter „batchSize“ gesteuert wird, der angibt, wie viele UGC-Datensätze pro Batch neu indiziert werden.

Ein vernünftiger Standardwert ist 5000:

* Wenn der Speicher ein Problem darstellt, geben Sie eine kleinere Zahl an
* Wenn die Geschwindigkeit ein Problem darstellt, geben Sie eine größere Zahl an, um die Geschwindigkeit zu erhöhen

### Ausführen des MSRP-Neuindizierungs-Tools mit dem cURL-Befehl {#running-msrp-reindex-tool-using-curl-command}

Der folgende cURL-Befehl zeigt, was für eine HTTP-Anfrage zur Neuindizierung des in MSRP gespeicherten benutzergenerierten Inhalts erforderlich ist.

Das Grundformat lautet:

cURL -u *signin* -d *data* *reindex-url*

*signin* = Administrator-ID:password
Beispiel: admin:admin

*data* = „batchSize=*size*&amp;path=*path“*

*size* = Anzahl der neu zu indizierenden benutzergenerierten Einträge pro Vorgang
`/content/usergenerated/asi/mongo/`

*path* = der Stammspeicherort der neu zu indizierenden UGC-Baumstruktur

* Um alle benutzergenerierten Inhalte neu zu indizieren, geben Sie den Wert der Eigenschaft `asipath`von) an.
  `/etc/socialconfig/srpc/defaultconfiguration`
* Um den Index auf einige benutzergenerierte Inhalte zu beschränken, geben Sie einen Unterbaum von `asipath` an

*reindex-url* = der Endpunkt für die Neuindizierung von SRP
`http://localhost:4503/services/social/datastore/mongo/reindex`

>[!NOTE]
>
>Wenn Sie [DSRP Solr neu indizieren](dsrp.md) lautet die URL **/services/social/datastore/rdb/reindex**

### Beispiel für MSRP-Neuindizierung {#msrp-reindex-example}

```shell
curl -s -u admin:admin -d 'batchSize=10000&path=/content/usergenerated/asi/mongo/' http://localhost:4503/services/social/datastore/mongo/reindex
```

## Demo von MSRP {#how-to-demo-msrp}

Informationen zum Einrichten von MSRP für eine Demonstrations- oder Entwicklungsumgebung finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

## Fehlerbehebung {#troubleshooting}

### UGC in MongoDB nicht sichtbar {#ugc-not-visible-in-mongodb}

Stellen Sie sicher, dass MSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption überprüfen. Standardmäßig ist der Speicherressourcenanbieter JSRP.

Rufen Sie auf allen Autoren- und Veröffentlichungs-AEM-Instanzen die [Speicherkonfigurationskonsole“ erneut auf ](srp-config.md) überprüfen Sie das AEM-Repository:

* In JCR, wenn [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Enthält keinen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc)-Knoten. Dies bedeutet, dass der Speicheranbieter JSRP ist.
   * Wenn der srpc-Knoten vorhanden ist und den Knoten [defaultConfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der defaultConfiguration festlegen, dass MSRP der Standardanbieter ist.

### UGC verschwindet nach dem Upgrade {#ugc-disappears-after-upgrade}

Bei einem Upgrade von einer bestehenden AEM Communities 6.0-Site müssen alle bereits vorhandenen benutzergenerierten Inhalte nach dem Upgrade auf AEM Communities 6.3 so konvertiert werden, dass sie der Struktur entsprechen, [ für die ](srp.md)-API erforderlich ist.

Zu diesem Zweck steht auf GitHub ein Open-Source-Tool zur Verfügung:

* [AEM Communities UGC-Migrations-Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

Das Migrations-Tool kann so angepasst werden, dass benutzergenerierter Inhalt von früheren Versionen von AEM Social Communities zum Import in AEM Communities 6.1 oder höher exportiert wird.

### Fehler - nicht definiertes Feld „provider_id“ {#error-undefined-field-provider-id}

Wenn der folgende Fehler in den Protokollen angezeigt wird, bedeutet dies, dass die Solr-Schemadatei nicht ordnungsgemäß konfiguriert ist.

#### JsonMappingException: undefiniertes Feld provider_id {#jsonmappingexception-undefined-field-provider-id}

```xml
Caused by: com.fasterxml.jackson.databind.JsonMappingException: undefined field provider_id
at com.fasterxml.jackson.databind.ser.DefaultSerializerProvider.serializeValue(DefaultSerializerProvider.java:129)
at com.fasterxml.jackson.databind.ObjectMapper.writeValue(ObjectMapper.java:1819)
at com.adobe.cq.social.scf.core.BaseSocialComponent.toJSONString(BaseSocialComponent.java:196)
... 124 common frames omitted
```

Um den Fehler zu beheben, stellen Sie bei Befolgung der Anweisungen für [Installieren von Standard-MLS](solr.md#installing-standard-mls) Folgendes sicher:

* Die XML-Konfigurationsdateien wurden an den richtigen Solr-Speicherort kopiert.
* Solr wurde neu gestartet, nachdem die neuen Konfigurationsdateien die vorhandenen ersetzt haben.

### Sichere Verbindung zu MongoDB schlägt fehl {#secure-connection-to-mongodb-fails}

Wenn ein Versuch, eine sichere Verbindung zum MongoDB-Server herzustellen, aufgrund einer fehlenden Klassendefinition fehlschlägt, muss das MongoDB-Treiberpaket, `mongo-java-driver`, aktualisiert werden, das im öffentlichen Maven-Repository verfügbar ist.

1. Laden Sie den Treiber von [https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar](https://search.maven.org/#artifactdetails%7Corg.mongodb%7Cmongo-java-driver%7C2.13.2%7Cjar) (Version 2.13.2 oder höher) herunter.
1. Kopieren Sie das Bundle in den Ordner „crx-quickstart/install“ für eine AEM-Instanz.
1. Starten Sie die AEM-Instanz neu.

## Ressourcen {#resources}

* [AEM mit MongoDB](../../help/sites-deploying/aem-with-mongodb.md)
* [MongoDB-Dokumentation](https://docs.mongodb.org/)
