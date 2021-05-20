---
title: Einrichten von MongoDB für Demo
seo-title: Einrichten von MongoDB für Demo
description: Einrichten von MSRP für eine Autoreninstanz und eine Veröffentlichungsinstanz
seo-description: Einrichten von MSRP für eine Autoreninstanz und eine Veröffentlichungsinstanz
uuid: d2035a9e-f05c-4f90-949d-7cdae9646750
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0b126218-b142-4d33-a28c-a91ab4fe99ac
role: Administrator
exl-id: 7e257b34-a0f5-47db-b1a9-e26333c287d9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 1%

---

# Einrichten von MongoDB für Demo {#how-to-setup-mongodb-for-demo}

## Einführung {#introduction}

In diesem Tutorial wird beschrieben, wie Sie [MSRP](msrp.md) für *eine Autoreninstanz* und *eine Veröffentlichungsinstanz* einrichten.

Bei dieser Konfiguration ist der Community-Inhalt sowohl in der Autoren- als auch in der Veröffentlichungsumgebung verfügbar, ohne dass benutzergenerierte Inhalte weitergeleitet oder umgekehrt repliziert werden müssen.

Diese Konfiguration eignet sich für *Nicht-Produktions*-Umgebungen, z. B. für Entwicklung und/oder Demonstration.

**Eine  ** Produktionsumgebung sollte:**

* Ausführen von MongoDB mit einem Replikatsatz
* SolrCloud verwenden
* Mehrere Herausgeberinstanzen enthalten

## MongoDB {#mongodb}

### Installieren Sie MongoDB {#install-mongodb}

* Laden Sie MongoDB von [https://www.mongodb.org/](https://www.mongodb.org/) herunter.

   * Wahl des Betriebssystems:

      * Linux
      * Mac 10.8
      * Windows 7
   * Wahl der Version:

      * Verwenden Sie mindestens Version 2.6


* Grundkonfiguration

   * Befolgen Sie die MongoDB-Installationsanweisungen.
   * Für mongod konfigurieren:

      * Es ist nicht erforderlich, Mongos oder die Freigabe zu konfigurieren.
   * Der installierte Ordner MongoDB wird als &lt;mongo-install> bezeichnet.
   * Der definierte Datenordnerpfad wird als &lt;mongo-dbpath> bezeichnet.


* MongoDB kann auf demselben Host wie AEM ausgeführt oder remote ausgeführt werden.

### Start MongoDB {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath  &lt;mongo-dbpath>

Dadurch wird ein MongoDB-Server mit dem Standardanschluss 27017 gestartet.

* Für Mac erhöhen Sie ulimit mit dem Startarg &#39;ulimit -n 2048&#39;.

>[!NOTE]
>
>Wenn MongoDB gestartet wird *nach* AEM, **Neustart** alle **AEM**-Instanzen, damit sie ordnungsgemäß eine Verbindung zu MongoDB herstellen.

### Demoproduktionsoption: Einrichten des MongoDB-Replikat-Sets {#demo-production-option-setup-mongodb-replica-set}

Die folgenden Befehle sind ein Beispiel für die Einrichtung einer Replikatgruppe mit 3 Knoten auf localhost:

* `bin/mongod --port 27017 --dbpath data --replSet rs0&`
* `bin/mongo`

   * `cfg = {"_id": "rs0","version": 1,"members": [{"_id": 0,"host": "127.0.0.1:27017"}]}`
   * `rs.initiate(cfg)`

* `bin/mongod --port 27018 --dbpath data1 --replSet rs0&`
* `bin/mongod --port 27019 --dbpath data2 --replSet rs0&`
* `bin/mongo`

   * `rs.add("127.0.0.1:27018")`
   * `rs.add("127.0.0.1:27019")`
   * `rs.status()`

## Solr {#solr}

### Installieren Sie Solr {#install-solr}

* Laden Sie Solr von [Apache Lucene](https://archive.apache.org/dist/lucene/solr/) herunter:

   * Für jedes Betriebssystem geeignet.
   * Solr Version 7.0.
   * Solr erfordert Java 1.7 oder höher.

* Grundkonfiguration

   * Folgen Sie dem Solr-Setup &quot;example&quot;.
   * Es ist kein Dienst erforderlich.
   * Der installierte Solr-Ordner wird als &lt;solr-install> bezeichnet.

### Solr für AEM Communities konfigurieren {#configure-solr-for-aem-communities}

Um eine Solr-Sammlung für MSRP für Demos zu konfigurieren, müssen zwei Entscheidungen getroffen werden (unter den Links zur Hauptdokumentation finden Sie weitere Informationen):

1. Führen Sie Solr im eigenständigen oder [SolrCloud-Modus](msrp.md#solrcloudmode) aus.
1. Installieren Sie [standard](msrp.md#installingstandardmls) oder [advanced](msrp.md#installingadvancedmls) mehrsprachige Suche (MLS).

### Eigenständige Solr {#standalone-solr}

Die Methode zum Ausführen von Solr kann je nach Version und Art der Installation unterschiedlich sein. Das [Solr-Referenzhandbuch](https://archive.apache.org/dist/lucene/solr/ref-guide/) ist die maßgebliche Dokumentation.

Zur Vereinfachung und zur Verwendung von Version 4.10 als Beispiel starten Sie Solr im eigenständigen Modus:

* cd bis &lt;solrinstall>/example
* java -jar start.jar

Dadurch wird ein Solr-HTTP-Server mit dem Standardanschluss 8983 gestartet. Sie können zur Solr-Konsole navigieren, um eine Solr-Konsole zum Testen zu erhalten.

* Standard-Solr-Konsole: [http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Wenn die Solr-Konsole nicht verfügbar ist, überprüfen Sie die Protokolle unter &lt;solrinstall>/example/logs. Überprüfen Sie, ob SOLR versucht, an einen bestimmten Hostnamen zu binden, der nicht aufgelöst werden kann (z. B. &quot;user-macbook-pro&quot;).
Falls ja, aktualisieren Sie die Datei etc/hosts mit einem neuen Eintrag für diesen Hostnamen (z.B. 127.0.0.1 user-macbook-pro) und Solr wird ordnungsgemäß gestartet.

### SolrCloud {#solrcloud}

Um ein sehr einfaches SolrCloud-Setup (nicht die Produktion) auszuführen, starten Sie solr mit:

* `java -Dbootstrap_confdir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar start.jar`

## MongoDB als Common Store identifizieren {#identify-mongodb-as-common-store}

Starten Sie bei Bedarf die Autoren- und Veröffentlichungsinstanzen AEM.

Wenn AEM vor dem Start von MongoDB ausgeführt wurde, müssen die AEM Instanzen neu gestartet werden.

Befolgen Sie die Anweisungen auf der Hauptseite der Dokumentation: [MSRP - MongoDB Common Store](msrp.md)

## Testen {#test}

Um den gemeinsamen MongoDB-Speicher zu testen und zu überprüfen, posten Sie einen Kommentar in der Veröffentlichungsinstanz, zeigen Sie ihn in der Autoreninstanz an und zeigen Sie die UGC in MongoDB und Solr an:

1. Navigieren Sie auf der Veröffentlichungsinstanz zur Seite [Community Components Guide](http://localhost:4503/content/community-components/en/comments.html) und wählen Sie die Komponente Kommentare aus.
1. Melden Sie sich an, um einen Kommentar zu posten:
1. Geben Sie Text in das Textfeld für Kommentare ein und klicken Sie auf **[!UICONTROL Post]**

   ![post-comment](assets/post-comment.png)

1. Sehen Sie sich einfach den Kommentar für die [Autoreninstanz](http://localhost:4502/content/community-components/en/comments.html) an (wahrscheinlich noch als Administrator/Admin angemeldet).

   ![view-comment](assets/view-comment.png)

   Hinweis: Während es unter *asipath* auf der Autoreninstanz JCR-Knoten gibt, gelten diese für das SCF-Framework. Die tatsächliche UGC befindet sich nicht in JCR, sondern in der MongoDB.

1. Zeigen Sie die benutzergenerierten Inhalte in mongodb **[!UICONTROL Communities]** > **[!UICONTROL Sammlungen]** > **[!UICONTROL Inhalt]** an.

   ![ugc-content](assets/ugc-content.png)

1. Zeigen Sie den benutzergenerierten Inhalt in Solr an:

   * Navigieren Sie zum Solr-Dashboard: [http://localhost:8983/solr/](http://localhost:8983/solr/).
   * Benutzer `core selector` zum Auswählen von `collection1`.
   * Wählen Sie nun eine der folgenden Optionen aus `Query`.
   * Wählen Sie nun eine der folgenden Optionen aus `Execute Query`.

   ![ugc-solr](assets/ugc-solr.png)

## Fehlerbehebung {#troubleshooting}

### Kein UGC wird {#no-ugc-appears} angezeigt

1. Stellen Sie sicher, dass MongoDB ordnungsgemäß installiert und ausgeführt wird.

1. Stellen Sie sicher, dass MSRP als Standardanbieter konfiguriert wurde:

   * Rufen Sie auf allen Autoren- und Veröffentlichungsinstanzen AEM [Speicherkonfigurationskonsole](srp-config.md) erneut auf oder überprüfen Sie das AEM Repository:

   * Wenn in JCR [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/) keinen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) -Knoten enthält, bedeutet dies, dass der Speicheranbieter JSRP ist.
   * Wenn der Knoten srpc vorhanden ist und den Knoten [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der Standardkonfiguration MSRP als Standardanbieter definieren.

1. Stellen Sie sicher, dass AEM nach Auswahl von MSRP neu gestartet wurde.
