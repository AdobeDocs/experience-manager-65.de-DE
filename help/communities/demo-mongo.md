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
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Setup von MongoDB für Demo {#how-to-setup-mongodb-for-demo}

## Einführung {#introduction}

In diesem Lernprogramm wird beschrieben, wie Sie [MSRP](msrp.md) für *eine Autoreninstanz* und *eine Veröffentlichungsinstanz* einrichten.

Bei diesem Setup ist der Zugriff auf den Community-Inhalt sowohl von Autoren- als auch von Veröffentlichungsumgebungen aus möglich, ohne dass benutzerdefinierte Inhalte weitergeleitet oder umgekehrt repliziert werden müssen.

Diese Konfiguration eignet sich für *Nicht-Produktionsumgebungen* wie Entwicklung und/oder Demonstration.

**Eine *Produktionsumgebung*sollte**

* Ausführen von MongoDB mit einem Replikationssatz
* SolrCloud verwenden
* Mehrere Herausgeberinstanzen enthalten

## MongoDB {#mongodb}

### MongoDB installieren {#install-mongodb}

* Herunterladen von MongoDB von [https://www.mongodb.org/](https://www.mongodb.org/)

   * Wahl des Betriebssystems:

      * Linux
      * Mac 10.8
      * Windows 7
   * Wahl der Version:

      * Verwenden Sie mindestens Version 2.6


* Grundkonfiguration

   * Befolgen Sie die Installationsanweisungen für MongoDB
   * Konfigurieren für Mongod

      * Keine Konfiguration von Mongos oder Freigeben erforderlich
   * Der installierte MongoDB-Ordner wird als &lt;mongo-install> bezeichnet
   * Der definierte Datenordnerpfad wird als &lt;mongo-dbpath> bezeichnet


* MongoDB kann auf demselben Host wie AEM ausgeführt oder remote ausgeführt werden

### MongoDB starten {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath &lt;mongo-dbpath>

Dadurch wird ein MongoDB-Server mit dem Standardanschluss 27017 gestartet.

* Für Mac erhöhen Sie ulimit mit start arg &#39;ulimit -n 2048&#39;

>[!NOTE]
>
>Wenn MongoDB *nach *AEM gestartet wird, **starten Sie **alle **AEM **Instanzen neu, damit sie ordnungsgemäß eine Verbindung zu MongoDB herstellen.

### Demoproduktionsoption: Setup MongoDB Replica Set {#demo-production-option-setup-mongodb-replica-set}

Die folgenden Befehle sind ein Beispiel für die Einrichtung eines Replikationssatzes mit 3 Knoten auf localhost:

* bin/mongod —port 27017 —dbpath data —replSet rs0&amp;
* bin/mongo

   * cfg = {&quot;_id&quot;: &quot;rs0&quot;,&quot;version&quot;: 1, &quot;Mitglieder&quot;: [{&quot;_id&quot;: 0,&quot;Host&quot;: &quot;127.0.0.1:27017&quot;}]}
   * rs.initiate(cfg)

* bin/mongod —port 27018 —dbpath data1 —replSet rs0&amp;
* bin/mongod —port 27019 —dbpath data2 —replSet rs0&amp;
* bin/mongo

   * rs.add(&quot;127.0.0.1:27018&quot;)
   * rs.add(&quot;127.0.0.1:27019&quot;)
   * rs.status()

## Solr {#solr}

### Installationsordner {#install-solr}

* Download Solr von [Apache Lucene](https://archive.apache.org/dist/lucene/solr/):

   * Eignet sich für jedes Betriebssystem
   * Version 4.10 oder Version 5 verwenden
   * Solr erfordert Java 1.7 oder höher

* Grundkonfiguration

   * Führen Sie das Setup von &#39;example&#39; Solr aus
   * Kein Dienst erforderlich
   * Der installierte Solr-Ordner wird als &lt;solr-install> bezeichnet

### Konfigurieren von SOL für AEM Communities {#configure-solr-for-aem-communities}

Um eine SOLR-Sammlung für MSRP für Demo zu konfigurieren, müssen zwei Entscheidungen getroffen werden (siehe die Links zur Hauptdokumentation):

1. Führen Sie Solr im eigenständigen oder im [SolrCloud-Modus aus](msrp.md#solrcloudmode)
1. Installieren von [Standard](msrp.md#installingstandardmls) - oder [erweiterten](msrp.md#installingadvancedmls) mehrsprachigen Suchvorgängen (MLS)

### Eigenständiger Solr {#standalone-solr}

Die Methode zum Ausführen von Solr kann je nach Version und Installationsart unterschiedlich sein. Der [SOLR Referenzhandbuch](https://archive.apache.org/dist/lucene/solr/ref-guide/) ist die maßgebliche Dokumentation.

Aus Gründen der Einfachheit sollten Sie mit Version 4.10 als Beispiel Solr im eigenständigen Modus starten:

* cd bis &lt;solrinstall>/example
* java -jar start.jar

Dadurch wird ein Solr-HTTP-Server mit dem Standardanschluss 8983 gestartet. Sie können zur Solr-Konsole navigieren, um eine Solr-Konsole zum Testen zu erhalten.

* Standard-Solr-Konsole: [http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Wenn Solr Console nicht verfügbar ist, überprüfen Sie die Protokolle unter &lt;solrinstall>/example/logs. Achten Sie darauf, ob SOLR versucht, sich an einen bestimmten Hostnamen zu binden, der nicht aufgelöst werden kann (z. &quot;user-macbook-pro&quot;).
Falls ja, aktualisieren Sie die Datei etc/hosts mit einem neuen Eintrag für diesen Hostnamen (z.B. 127.0.0.1 user-macbook-pro) und Solr wird ordnungsgemäß gestartet.

### SolrCloud {#solrcloud}

Starten Sie Solr mit folgenden Schritten, um ein sehr einfaches Setup (nicht die Produktion) der solrCloud auszuführen:

* java -Dbootstrap_condir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar start.jar

## Identifizieren Sie MongoDB als gemeinsamen Store. {#identify-mongodb-as-common-store}

Starten Sie den Autor und veröffentlichen Sie bei Bedarf AEM-Instanzen.

Wenn AEM vor dem Start von MongoDB ausgeführt wurde, müssen die AEM-Instanzen neu gestartet werden.

Befolgen Sie die Anweisungen auf der Hauptseite der Dokumentation: [MSRP - MongoDB Common Store](msrp.md)

## Test {#test}

Um den MongoDB Common Store zu testen und zu überprüfen, veröffentlichen Sie einen Kommentar in der Veröffentlichungsinstanz und sehen Sie ihn auf der Autorinstanz an. Zeigen Sie die UGC in MongoDB und Solr an:

1. Navigieren Sie in der Veröffentlichungsinstanz zur Seite &quot; [Community-Komponenten-Handbuch](http://localhost:4503/content/community-components/en/comments.html) &quot;und wählen Sie die Komponente &quot;Kommentare&quot;aus.
1. Melden Sie sich an, um einen Kommentar zu posten:
1. Geben Sie Text in das Kommentartexteingabefeld ein und klicken Sie auf **[!UICONTROL Beitrag]**

   ![chlimage_1-191](assets/chlimage_1-191.png)

1. Zeigen Sie einfach den Kommentar auf der [Autoreninstanz](http://localhost:4502/content/community-components/en/comments.html) an (wahrscheinlich noch als Admin/Admin angemeldet).

   ![chlimage_1-192](assets/chlimage_1-192.png)

   Hinweis: während es JCR-Knoten unter dem *asipath* auf author gibt, gelten diese für das SCF-Framework. Die eigentliche UGC ist nicht in JCR, sondern in der MongoDB.

1. Zeigen Sie die Benutzeroberfläche in &quot;mongodb **[!UICONTROL Communities&quot;> &quot;Sammlungen&quot;> &quot;Inhalt&quot;an]**

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. UGC in Solr anzeigen:

   * Zum Solr-Dashboard navigieren: [http://localhost:8983/solr/](http://localhost:8983/solr/)
   * Benutzer `core selector` auswählen `collection1`
   * Wählen Sie nun eine der folgenden Optionen aus `Query`
   * Wählen Sie nun eine der folgenden Optionen aus `Execute Query`
   ![chlimage_1-194](assets/chlimage_1-194.png)

## Fehlerbehebung {#troubleshooting}

### Kein UGC angezeigt {#no-ugc-appears}

1. Vergewissern Sie sich, dass MongoDB ordnungsgemäß installiert und ausgeführt wird.

1. Stellen Sie sicher, dass MSRP als Standardanbieter konfiguriert wurde:

   * Besuchen Sie bei allen Autoren- und Veröffentlichungsinstanzen von AEM erneut die [Speicherkonfigurationskonsole](srp-config.md)
   oder überprüfen Sie das AEM-Repository:

   * In JCR, if [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

      * Enthält keinen [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) -Knoten, d. h. der Speicheranbieter ist JSRP
      * Wenn der Knoten srpc vorhanden ist und die Node- [Standardkonfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)enthält, sollten die Eigenschaften der Standardkonfiguration MSRP als Standardanbieter definieren


1. Vergewissern Sie sich, dass AEM nach Auswahl von MSRP neu gestartet wurde.
