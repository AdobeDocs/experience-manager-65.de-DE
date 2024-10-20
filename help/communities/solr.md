---
title: Solr-Konfiguration für SRP
description: Eine Apache Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Knotenspeicher (Oak) und dem gemeinsamen Speicher (SRP) freigegeben werden
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: a9fc9c06-b9e6-4a5e-ab5e-0930ecd4b51b
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1423'
ht-degree: 2%

---

# Solr-Konfiguration für SRP {#solr-configuration-for-srp}

## Solr für AEM Plattform {#solr-for-aem-platform}

Eine Installation des Typs [Apache Solr](https://solr.apache.org/) kann mithilfe verschiedener Sammlungen zwischen dem Knotenspeicher [3} (Oak) und dem gemeinsamen Speicher [5} (SRP) freigegeben werden.](../../help/sites-deploying/data-store-config.md)](working-with-srp.md)

Wenn sowohl die Oak- als auch die SRP-Kollektionen intensiv verwendet werden, kann aus Leistungsgründen ein zweiter Solr installiert werden.

In Produktionsumgebungen bietet der [SolrCloud-Modus](#solrcloud-mode) eine verbesserte Leistung im Vergleich zum eigenständigen Modus (ein einzelnes lokales Solr-Setup).

### Voraussetzungen {#requirements}

Herunterladen und Installieren von Apache Solr:

* [Version 7.0](https://archive.apache.org/dist/lucene/solr/7.0.0/)

* Solr erfordert Java™ 1.7 oder höher
* Es ist kein Dienst erforderlich
* Auswahl der Ausführungsmodi:

   * Eigenständiger Modus
   * [SolrCloud-Modus](#solrcloud-mode) (empfohlen für Produktionsumgebungen)

* Auswahl der mehrsprachigen Suche (MLS)

   * [Installieren von Standard-MLS](#installing-standard-mls)
   * [Installieren erweiterter MLS](#installing-advanced-mls)

## SolrCloud-Modus {#solrcloud-mode}

Der Modus [SolrCloud](https://solr.apache.org/guide/6_6/solrcloud.html) wird für Produktionsumgebungen empfohlen. Bei Ausführung im SolrCloud-Modus muss SolrCloud vor der Installation der mehrsprachigen Suche (MLS) installiert und konfiguriert werden.

Es wird empfohlen, die SolrCloud-Anweisungen zur Installation zu befolgen:

* 3 SolrCloud-Knoten auf demselben Server.
* Ein externer Apache ZooKeeper.

Es wird außerdem empfohlen, JVM zu konfigurieren, um die Speicherbelegung und die Speicherbereinigung zu optimieren.

### JVM-Konfigurationsbeispiel {#jvm-configuration-example}

```shell
JVM_OPTS="-server -Xmx2048m -XX:+UseConcMarkSweepGC -XX:+CMSClassUnloadingEnabled -Xloggc:../logs/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps -Djava.awt.headless=true"
```

### SolrCloud - Befehle einrichten {#solrcloud-setup-commands}

Bei Ausführung im SolrCloud-Modus ist vor der MLS-Installation die Verwendung und Kenntnis der folgenden SolrCloud-Einrichtungsbefehle erforderlich.

#### 1. Eine Konfiguration in ZooKeeper hochladen {#upload-a-configuration-to-zookeeper}

Referenz:
[https://solr.apache.org/guide/6_6/command-line-utilities.html](https://solr.apache.org/guide/6_6/command-line-utilities.html)

Verwendung:
sh ./scripts/cloud-scripts/zkcli.sh \
-cmd upconfig \
-zkhost *server:port* \
-confname *myconfig-name *\
-solrhome *solr-home-path* \
-confdir *config-dir*

#### 2. Kollektion erstellen {#create-a-collection}

Referenz:
[https://solr.apache.org/guide/6_6/solr-control-script-reference.html#SolrControlScriptReference-Create](https://solr.apache.org/guide/6_6/solr-control-script-reference.html#SolrControlScriptReference-Create)

Verwendung:
./bin/solr create \
-c *mycollection-name*\
-d *config-dir* \
-n *myconfig-name* \
-p *port*\
-s *number-of-shards* \
-rf *number-of-replicas*

#### 3. Verknüpfen einer Sammlung mit einem Konfigurationssatz {#link-a-collection-to-a-configuration-set}

Verknüpfen Sie eine Sammlung mit einer Konfiguration, die bereits in ZooKeeper hochgeladen wurde.

Referenz:
[https://solr.apache.org/guide/6_6/command-line-utilities.html](https://solr.apache.org/guide/6_6/command-line-utilities.html)

Verwendung:
sh ./scripts/cloud-scripts/zkcli.sh \
-cmd linkconfig \
-zkhost *server:port* \
-collection *mycollection-name* \
-confname *myconfig-name*

### Vergleich von Standard- und erweiterten MLS {#comparison-of-standard-and-advanced-mls}

Die mehrsprachige Suche (MLS) für AEM Communities wurde für die Solr-Plattform entwickelt, um eine verbesserte Suche in allen unterstützten Sprachen, einschließlich Englisch, zu ermöglichen.

MLS für AEM Communities ist entweder als Standard-MLS oder als erweitertes MLS verfügbar. Standard-MLS enthält nur Solr-Konfigurationseinstellungen und schließt alle Plug-ins oder Ressourcendateien aus. Erweitertes MLS ist die umfassendere Lösung und umfasst Solr-Konfigurationseinstellungen, Plug-ins und zugehörige Ressourcen

Standard-MLS enthält Verbesserungen bei der Inhaltssuche für die folgenden Sprachen:

* Englisch: Verbesserter Stil für den Versuch, Wortabgeleitungen zuzuordnen.
* Japanisch: Verbesserte japanische Tokenisierung für Zeichen mit halber Breite.

Erweitertes MLS umfasst Verbesserungen bei der Inhaltssuche für die folgenden Sprachen:

* Englisch: Stemmer durch Lmmatizer ersetzt.
* Deutsch: Dekomprimierung hinzugefügt.
* Französisch: Versandverarbeitung hinzugefügt.
* Chinesisch (vereinfacht): Es wurde ein intelligenter Tokenizer hinzugefügt.
* Verschiedene Sprachen: Es wurden ein Stemmer, eine Stoppwortliste und ein Normalisierungsprogramm hinzugefügt.

Insgesamt werden die folgenden 33 Sprachen in Advanced MLS unterstützt.

| Arabisch | Deutsch | Norwegisch |
|---|---|---|
| Bulgarisch | Griechisch | Polnisch |
| Chinesisch (vereinfacht) | Haitianisches Kreol | Portugiesisch |
| Chinesisch (traditionell) | Hebräisch | Rumänisch |
| Tschechisch | Ungarisch | Russisch |
| Dänisch | Indonesisch | Slowakisch |
| Niederländisch | Italienisch | Slowenisch |
| Englisch | Japanisch | Spanisch |
| Estnisch | Koreanisch | Schwedisch |
| Finnisch | Lettisch | Thailändisch |
| Französisch | Litauisch | Türkisch |

#### Vergleich von AEM 6.1 Solr-Suche, Standard-MLS und erweiterten MLS {#comparison-of-aem-solr-search-standard-mls-and-advanced-mls}

**Hinweis**: AEM 6.1 bezieht sich auf AEM 6.1 Communities FP3 und früher.

![compare-solr-mls](assets/compare-solr-mls.png)

### Installieren von Standard-MLS {#installing-standard-mls}

Für die SRP-Sammlung (entweder MSRP oder DSRP) muss zur Unterstützung der standardmäßigen mehrsprachigen Suche (MLS) zwei der Solr-Konfigurationsdateien geändert werden:

* **schema.xml**
* **solrconfig.xml**

Standard-MLS-Dateien (schema.xml, solrconfig.xml) für Solr 4.10.

Standard-MLS-Dateien (schema.xml, solrconfig.xml) für Solr 5.x.

Die Standard-MLS-Dateien werden im AEM-Repository gespeichert.

**Hinweis**: Während die Solr-Dateien im Ordner msrp/ gespeichert sind, sind sie auch für DSRP verfügbar (keine Änderungen erforderlich).

**Download-Anweisungen**: Ersetzen Sie `solrX` entsprechend durch `solr4` oder `solr5`.

1. Suchen Sie mithilfe von CRXDE|Lite nach:

   * `/libs/social/config/datastore/msrp/solrX/schema.xml`
   * `/libs/social/config/datastore/msrp/solrX/solrconfig.xml`

1. Herunterladen auf den lokalen Server, auf dem Solr bereitgestellt wird.

   * Suchen Sie die Eigenschaft `jcr:data` des Knotens `jcr:content` .
   * Um den Download zu starten, wählen Sie `view` aus.
   * Stellen Sie sicher, dass die Dateien mit den entsprechenden Namen und der entsprechenden Kodierung (UTF8) gespeichert werden.

1. Befolgen Sie die Installationsanweisungen für den eigenständigen oder SolrCloud-Modus.

#### SolrCloud-Modus - Standard-MLS {#solrcloud-mode-standard-mls}

1. Installieren und konfigurieren Sie Solr im SolrCloud-Modus.
1. Bereiten Sie eine neue Konfiguration vor:

   1. Erstellen Sie new-config-dir* wie `solr-install-dir*/myconfig/`

   1. Kopieren Sie den Inhalt des vorhandenen Solr-Konfigurationsverzeichnisses in *new-config-dir*

      * Für Solr4: copy `solr-install-dir/example/solr/collection1/conf/`
      * Für Solr5: copy `solr-install-dir/server/solr/configsets/data_driven_schema_configs/`

   1. Kopieren Sie die heruntergeladenen Dateien **schema.xml** und **solrconfig.xml** in *new-config-dir* , um vorhandene Dateien zu überschreiben.

1. [Laden Sie die neue Konfiguration](#upload-a-configuration-to-zookeeper) in ZooKeeper hoch.
1. [Erstellen Sie eine Kollektion](#create-a-collection), die die erforderlichen Parameter angibt, wie z. B. die Anzahl der Shards, die Anzahl der Replikate und den Konfigurationsnamen.
1. Wenn der Konfigurationsname während der Erstellung der Sammlung *nicht *angegeben wurde, verknüpfen [diese neu erstellte Sammlung](#link-a-collection-to-a-configuration-set) mit der Konfiguration, die in den ZooKeeper hochgeladen wurde.

1. Führen Sie für MSRP das Tool [MSRP Reindex Tool](msrp.md#msrp-reindex-tool) aus, es sei denn, diese Installation ist neu.

#### Eigenständiger Modus - Standard-MLS {#standalone-mode-standard-mls}

1. Installieren Sie Solr im eigenständigen Modus.
1. Wenn Sie Solr5 ausführen, erstellen Sie eine Sammlung1 (ähnlich wie bei Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

1. Backup **schema.xml** und **solrconfig.xml** im Solr-Konfigurationsverzeichnis, z. B.:

   * Für Solr4: `solr-install-dir/example/solr/collection1/conf/`
   * Erstellt für Solr5: `solr-install-dir/server/solr/collection1/conf/`

1. Kopieren Sie die heruntergeladenen Dateien **schema.xml** und **solrconfig.xml** in denselben Ordner.

1. Starten Sie Solr neu.
1. Führen Sie für MSRP das Tool [MSRP Reindex Tool](#msrpreindextool) aus, es sei denn, diese Installation ist neu.

### Installieren erweiterter MLS {#installing-advanced-mls}

Damit die SRP-Sammlung (MSRP oder DSRP) erweiterte MLS unterstützen kann, sind zusätzlich zu einem benutzerdefinierten Schema und einer Solr-Konfiguration neue Solr-Plug-ins erforderlich. Alle erforderlichen Elemente werden in einer herunterladbaren ZIP-Datei zusammengefasst. Darüber hinaus ist ein Installationsskript zur Verwendung enthalten, wenn Solr im eigenständigen Modus bereitgestellt wird.

Informationen zum Abrufen des erweiterten MLS-Pakets finden Sie unter [AEM erweitertes MLS](deploy-communities.md#aem-advanced-mls) im Abschnitt &quot;Bereitstellung&quot;der Dokumentation.

Erste Schritte mit der Installation für SolrCloud oder den eigenständigen Modus:

* Laden Sie AEM-SOLR-MLS ZIP-Archiv auf den Server herunter, der Solr hostet.
* Entpacken Sie das Archiv.

#### SolrCloud-Modus - Erweitertes MLS {#solrcloud-mode-advanced-mls}

Installationsanweisungen - beachten Sie die wenigen Unterschiede für Solr4 und Solr5:

1. Installieren und konfigurieren Sie Solr im SolrCloud-Modus.
1. Extrahieren Sie den Inhalt des erweiterten MLS-Pakets auf die Festplatte. Der Inhalt sollte Folgendes enthalten:

   * **schema.xml**
   * **solrconfig.xml**
   * Ordner **stopwords/**
   * Ordner **profiles/**
   * Ordner **extra-libs/**

1. Bereiten Sie eine neue Konfiguration vor:

   1. Erstellen eines *new-config-dir*

      * z. B. `solr-install-dir/myconfig/`
      * Erstellen von Unterordnern `stopwords/` und `lang/`

   1. Kopieren Sie den Inhalt des vorhandenen Solr-Konfigurationsverzeichnisses in *new-config-dir*

      * Für Solr4: Kopieren Sie `solr-install-dir/example/solr/collection1/conf/`
      * Für Solr5: Kopieren Sie `solr-install-dir/server/solr/configsets/data_driven_schema_configs/`

   1. Kopieren Sie die extrahierten Dateien **schema.xml** und **solrconfig.xml** in *new-config-dir* , um vorhandene Dateien zu überschreiben.
   1. Für Solr5: Kopieren Sie `solr_install_dir/server/solr/configsets/sample_techproducts_configs/conf/lang/*.txt` in `new-config-dir/lang/`
   1. Kopieren Sie den extrahierten Ordner **stopwords/** in *new-config-dir* , was zu `new-config-dir/stopwords/*.txt` führt.

1. [Laden Sie die neue Konfiguration](#upload-a-configuration-to-zookeeper) in ZooKeeper hoch.
1. Kopieren Sie den neuen Ordner **profiles/** ...

   * Für Solr4: Kopieren Sie in die Ressourcen/ Ordner jedes Knotens
   * Für Solr5: Kopieren Sie in den Server/Ressourcen/ Ordner jeder Solr-Installation. Wenn sich alle Knoten im selben Solr-Installationsordner befinden, wird dieser Schritt nur einmal ausgeführt.

1. Erstellen Sie einen Ordner **lib/** im Ordner &quot;solr-home&quot;(enthält solr.xml) jedes Knotens in SolrCloud. Kopieren Sie jars aus den folgenden Speicherorten in den neuen Ordner lib/ auf jedem Knoten:

   * **extra-libs/** aus dem erweiterten MLS-Paket extrahiert
   * *solr-install-dir/contributb/extract/lib/*.jar
   * *solr-install-dir/dist/solr-cell*.jar
   * *solr-install-dir/contributb/cluering/lib/*.jar
   * *solr-install-dir/dist/solr-cluering*.jar
   * *solr-install-dir/contributb/langid/lib/*.jar
   * *solr-install-dir/dist/solr-langid*.jar
   * *solr-install-dir/contributb/Velocity/lib/*.jar
   * *solr-install-dir/dist/solr-Velocity*.jar
   * *solr-install-dir/contributb/analysis-extras/lib/*.jar
   * *solr-install-dir/contributb/analysis-extras/lucene-libs/*.jar

1. [Erstellen Sie eine Kollektion](#create-a-collection), die die erforderlichen Parameter angibt, wie z. B. die Anzahl der Shards, die Anzahl der Replikate und den Konfigurationsnamen.
1. Wenn der Konfigurationsname bei der Erstellung der Sammlung *nicht* lautete, verknüpfen [diese neu erstellte Sammlung](#link-a-collection-to-a-configuration-set) mit der Konfiguration, die in den ZooKeeper hochgeladen wurde.

1. Führen Sie für MSRP das Tool [MSRP Reindex Tool](#msrpreindextool) aus, es sei denn, diese Installation ist neu.

#### Eigenständiger Modus - Erweitertes MLS {#standalone-mode-advanced-mls}

Ein Installationsskript ist im erweiterten MLS-Paket enthalten.

Nachdem der Inhalt des Pakets auf den Server extrahiert wurde, der den eigenständigen Solr-Server hostet, führen Sie das Installationsskript aus, um die erforderlichen Ressourcen und Konfigurationsdateien zu installieren.

* Installieren Sie Solr im eigenständigen Modus.
* Wenn Sie Solr5 ausführen, erstellen Sie eine Sammlung1 (ähnlich wie bei Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

* Führen Sie das Installationsskript aus: Installieren Sie [-v 4|5] [-d solrhome] [-c collection path]
wobei:

   * -d solrhome

     Solr-Installationsordner

   * -c collection path

     Sammlungspfad in Solr

   * --help

     Befehlszeilenoptionen drucken

   * -v [4|5]

     Version für Solr festlegen

* Beispiel für Solr 4.10.4:

   * Install.bat -v 4 -d c:/solr-4.10.4 -c:/solr-4.10.4/example/solr/collection1

* Beispiel für Solr 5.4.0:

   * Install.sh -v 5 -d /tmp/solr-5.4.0 -c /tmp/solr-5.4.0/server/solr/collection1

**Hinweis**:

* Das Installationsskript sichert schema.xml und solrconfig.xml, bevor neue Versionen durch Anhängen von &quot;.orig&quot;installiert werden

### Über solrconfig.xml {#about-solrconfig-xml}

Die Datei **solrconfig.xml** steuert das automatische Übertragen-Intervall und die Sichtbarkeit der Suche und erfordert Tests und Anpassungen.

`<autoCommit>`: Standardmäßig ist das AutoCommit-Intervall, bei dem es sich um eine feste Bindung an einen stabilen Speicher handelt, auf 15 Sekunden festgelegt. Die Sichtbarkeit der Suche verwendet standardmäßig den Pre-commit-Index.

Um die Suche zu ändern und einen Index zu verwenden, der aktualisiert wurde, um Änderungen aufgrund des Commit widerzuspiegeln, ändern Sie die enthaltene `openSearcher` in &quot;true&quot;.

`autoSoftCommit`: Ein &quot;Soft&quot;-Commit stellt sicher, dass Änderungen sichtbar sind (der Index wird aktualisiert), stellt jedoch nicht sicher, dass Änderungen mit einem stabilen Speicher (harter Commit) synchronisiert werden. Das Ergebnis ist eine Leistungsverbesserung. Standardmäßig ist `autoSoftCommit` deaktiviert, wobei der enthaltene `maxTime` auf -1 gesetzt ist.
