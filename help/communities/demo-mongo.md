---
title: Setup von MongoDB für Demo
seo-title: Setup von MongoDB für Demo
description: Einrichten von MSRP für eine Autoreninstanz und eine Veröffentlichungsinstanz
seo-description: Einrichten von MSRP für eine Autoreninstanz und eine Veröffentlichungsinstanz
uuid: d2035a9e-f05c-4f90-949d-7cdae9646750
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0b126218-b142-4d33-a28c-a91ab4fe99ac
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 1%

---


# Setup von MongoDB für Demo {#how-to-setup-mongodb-for-demo}

## Einführung {#introduction}

In diesem Lernprogramm wird beschrieben, wie [MSRP](msrp.md) für *eine Autorinstanz* und *eine Instanz im Veröffentlichungsmodus* eingerichtet wird.

Bei diesem Setup ist der Zugriff auf den Community-Inhalt sowohl von Autoren- als auch von Veröffentlichungsinhalten möglich, ohne dass benutzergenerierte Inhalte weitergeleitet oder umgekehrt repliziert werden müssen.

Diese Konfiguration eignet sich für *Nicht-Produktion*-Umgebung, z. B. für Entwicklungs- und/oder Demonstrationszwecke.

**Eine  ** Produktionsumgebung sollte**

* Ausführen von MongoDB mit einem Replikationssatz
* SolrCloud verwenden
* Mehrere Herausgeberinstanzen enthalten

## MongoDB {#mongodb}

### MongoDB {#install-mongodb} installieren

* Laden Sie MongoDB von [https://www.mongodb.org/](https://www.mongodb.org/) herunter.

   * Wahl des Betriebssystems:

      * Linux
      * Mac 10.8
      * Windows 7
   * Wahl der Version:

      * Verwenden Sie mindestens Version 2.6


* Grundkonfiguration

   * Folgen Sie den Installationsanweisungen für MongoDB.
   * Konfigurieren für Mongod:

      * Es ist nicht erforderlich, Mongos oder das Freigeben zu konfigurieren.
   * Der installierte MongoDB-Ordner wird als &lt;mongo-install> bezeichnet.
   * Der definierte Datenordnerpfad wird als &lt;mongo-dbpath> bezeichnet.


* MongoDB kann auf demselben Host wie AEM ausgeführt oder remote ausgeführt werden.

### Beginn MongoDB {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath  &lt;mongo-dbpath>

Dadurch wird ein MongoDB-Server mit dem Standardanschluss 27017 Beginn.

* Für Mac sollten Sie ulimit mit dem Beginn arg &#39;ulimit -n 2048&#39; erhöhen.

>[!NOTE]
>
>Wenn MongoDB nach *AEM gestartet wird,**starten Sie**alle **AEM**-Instanzen neu, damit sie ordnungsgemäß eine Verbindung zu MongoDB herstellen.*

### Demoproduktionsoption: Setup MongoDB Replikat Set {#demo-production-option-setup-mongodb-replica-set}

Die folgenden Befehle sind ein Beispiel für die Einrichtung eines Replikationssatzes mit 3 Knoten auf localhost:

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

### Installieren von Solr {#install-solr}

* Laden Sie Solr von [Apache Lucene](https://archive.apache.org/dist/lucene/solr/) herunter:

   * Geeignet für jedes Betriebssystem.
   * Solr Version 7.0.
   * Solr erfordert Java 1.7 oder höher.

* Grundkonfiguration

   * Folgen Sie dem Setup von &#39;example&#39; Solr.
   * Es ist kein Dienst erforderlich.
   * Der installierte Solr-Ordner wird als &lt;solr-install> bezeichnet.

### Konfigurieren von Solr für AEM Communities {#configure-solr-for-aem-communities}

Um eine SOLR-Sammlung für MSRP für Demo zu konfigurieren, müssen zwei Entscheidungen getroffen werden (siehe die Links zur Hauptdokumentation):

1. Führen Sie Solr im eigenständigen oder [SolrCloud-Modus](msrp.md#solrcloudmode) aus.
1. Installieren Sie [standard](msrp.md#installingstandardmls) oder [advanced](msrp.md#installingadvancedmls) multilinguale Suche (MLS).

### Eigenständiger Solr {#standalone-solr}

Die Methode zum Ausführen von Solr kann je nach Version und Installationsart unterschiedlich sein. Die [Solr-Referenzhandbuch](https://archive.apache.org/dist/lucene/solr/ref-guide/) ist die maßgebliche Dokumentation.

Aus Gründen der Einfachheit ist Beginn Solr im eigenständigen Modus mit Version 4.10 als Beispiel zu verwenden:

* cd bis &lt;solrinstall>/example
* java -jar Beginn.jar

Dadurch wird ein Solr-HTTP-Server mit dem Standardanschluss 8983 Beginn. Sie können zur Solr-Konsole navigieren, um eine Solr-Konsole zum Testen zu erhalten.

* Standard-Solr-Konsole: [http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Wenn Solr Console nicht verfügbar ist, überprüfen Sie die Protokolle unter &lt;solrinstall>/example/logs. Achten Sie darauf, ob SOLR versucht, sich an einen bestimmten Hostnamen zu binden, der nicht aufgelöst werden kann (z.B. &quot;user-macbook-pro&quot;).
Wenn ja, aktualisieren Sie die Datei etc/hosts mit einem neuen Eintrag für diesen Hostnamen (z.B. 127.0.0.1 user-macbook-pro) und Solr wird ordnungsgemäß Beginn.

### SolrCloud {#solrcloud}

Um eine sehr einfache (nicht produktive) solrCloud-Einrichtung auszuführen, führen Sie Beginn-Solr mit:

* `java -Dbootstrap_confdir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar start.jar`

## Identifizieren Sie MongoDB als Common Store {#identify-mongodb-as-common-store}.

Starten Sie bei Bedarf die Instanz im Autorenmodus und veröffentlichen Sie AEM.

Wenn AEM vor dem Start von MongoDB ausgeführt wurde, müssen die AEM Instanzen neu gestartet werden.

Befolgen Sie die Anweisungen auf der Hauptseite der Dokumentation: [MSRP - MongoDB Common Store](msrp.md)

## Test {#test}

Um den MongoDB-Stammspeicher zu testen und zu überprüfen, veröffentlichen Sie einen Kommentar zur Veröffentlichungsinstanz und Ansicht auf der Autoreninstanz sowie die Ansicht des UGC in MongoDB und Solr:

1. Navigieren Sie auf der Seite &quot;Veröffentlichungsinstanz&quot;zur Seite [Community-Komponentenhandbuch](http://localhost:4503/content/community-components/en/comments.html) und wählen Sie die Komponente &quot;Kommentare&quot;aus.
1. Melden Sie sich an, um einen Kommentar zu posten:
1. Geben Sie Text in das Kommentartexteingabefeld ein und klicken Sie auf **[!UICONTROL Post]**

   ![post-comment](assets/post-comment.png)

1. Ansicht Sie einfach den Kommentar auf der [Autoreninstanz](http://localhost:4502/content/community-components/en/comments.html) (wahrscheinlich noch als Admin/Admin angemeldet).

   ![Ansicht-Kommentar](assets/view-comment.png)

   Hinweis: Während sich unter dem Autorenordner *asipath* JCR-Knoten befinden, gelten diese für das SCF-Framework. Die eigentliche UGC ist nicht in JCR, sondern in der MongoDB.

1. Ansicht des UGC in mongodb **[!UICONTROL Communities]** > **[!UICONTROL Kollektionen]** > **[!UICONTROL Content]**

   ![ugc-content](assets/ugc-content.png)

1. Ansicht des UGC in Solr:

   * Zu Solr-Dashboard navigieren: [http://localhost:8983/solr/](http://localhost:8983/solr/).
   * Benutzer `core selector`, um `collection1` auszuwählen.
   * Wählen Sie nun eine der folgenden Optionen aus `Query`.
   * Wählen Sie nun eine der folgenden Optionen aus `Execute Query`.

   ![ugc-solr](assets/ugc-solr.png)

## Fehlerbehebung {#troubleshooting}

### Kein UGC wird angezeigt {#no-ugc-appears}

1. Vergewissern Sie sich, dass MongoDB ordnungsgemäß installiert ist und ausgeführt wird.

1. Stellen Sie sicher, dass MSRP als Standardanbieter konfiguriert wurde:

   * Rufen Sie auf allen Instanzen im Autoren- und Veröffentlichungsmodus AEM [Datenspeicherung Configuration Console](srp-config.md) erneut auf oder überprüfen Sie das AEM Repository:

   * Wenn [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/) keinen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc)-Knoten enthält, bedeutet dies, dass der Datenspeicherung-Provider JSRP ist.
   * Wenn der Knoten srpc vorhanden ist und den Knoten [defaultConfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der Standardkonfiguration MSRP als Standardanbieter definieren.

1. Stellen Sie sicher, dass AEM nach Auswahl von MSRP neu gestartet wurde.
