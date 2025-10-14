---
title: Solr-Konfiguration für SRP
description: Eine Apache Solr-Installation kann zwischen dem Node Store (Oak) und dem Common Store (SRP) mithilfe verschiedener Sammlungen gemeinsam genutzt werden
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

## Solr für AEM Platform {#solr-for-aem-platform}

Eine [Apache Solr](https://solr.apache.org/)-Installation kann zwischen dem [Knotenspeicher](../../help/sites-deploying/data-store-config.md) (Oak) und [Common Store](working-with-srp.md) (SRP) mithilfe verschiedener Sammlungen gemeinsam genutzt werden.

Wenn sowohl die Oak- als auch die SRP-Sammlungen intensiv verwendet werden, kann aus Leistungsgründen eine zweite Solr-Instanz installiert werden.

In Produktionsumgebungen bietet [SolrCloud-Modus](#solrcloud-mode) eine verbesserte Leistung im Vergleich zum eigenständigen Modus (eine einzelne, lokale Solr-Einrichtung).

### Voraussetzungen {#requirements}

Herunterladen und Installieren von Apache Solr:

* [Version 7.0](https://archive.apache.org/dist/lucene/solr/7.0.0/)

* Solr erfordert Java™ 1.7 oder höher
* Es ist kein Service erforderlich
* Auswahl der Ausführungsmodi:

   * Eigenständiger Modus
   * [SolrCloud-Modus](#solrcloud-mode) (für Produktionsumgebungen empfohlen)

* Auswahl an mehrsprachiger Suche (MLS)

   * [Installieren von Standard-MLS](#installing-standard-mls)
   * [Erweiterte MLS installieren](#installing-advanced-mls)

## Solr-Cloud-Modus {#solrcloud-mode}

[SolrCloud](https://solr.apache.org/guide/6_6/solrcloud.html)-Modus wird für Produktionsumgebungen empfohlen. Wenn SolrCloud im SolrCloud-Modus ausgeführt wird, muss SolrCloud vor der Installation von Multilingual Search (MLS) installiert und konfiguriert werden.

Es wird empfohlen, zur Installation die SolrCloud-Anweisungen zu befolgen:

* 3 SolrCloud-Knoten auf demselben Server.
* Ein externer Apache ZooKeeper.

Es wird außerdem empfohlen, JVM so zu konfigurieren, dass die Speichernutzung und die Speicherbereinigung optimiert werden.

### JVM-Konfigurationsbeispiel {#jvm-configuration-example}

```shell
JVM_OPTS="-server -Xmx2048m -XX:+UseConcMarkSweepGC -XX:+CMSClassUnloadingEnabled -Xloggc:../logs/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps -Djava.awt.headless=true"
```

### SolrCloud-Einrichtungsbefehle {#solrcloud-setup-commands}

Wenn Sie im SolrCloud-Modus ausführen, sind vor der Installation von MLS die Verwendung und Kenntnisse der folgenden SolrCloud-Einrichtungsbefehle erforderlich.

#### 1. Hochladen einer Konfiguration in ZooKeeper {#upload-a-configuration-to-zookeeper}

Referenz:
[https://solr.apache.org/guide/6_6/command-line-utilities.html](https://solr.apache.org/guide/6_6/command-line-utilities.html)

Verwendung:
sh ./scripts/cloud-scripts/zkcli.sh \
-cmd upconfig \
-zkhost *server:port* \
-configName *myconfig-name *\
-solrhome *solr-home-path* \
-confdir *config-dir*

#### 2. Erstellen einer Sammlung {#create-a-collection}

Referenz:
[https://solr.apache.org/guide/6_6/solr-control-script-reference.html#SolrControlScriptReference-Create](https://solr.apache.org/guide/6_6/solr-control-script-reference.html#SolrControlScriptReference-Create)

Verwendung:
./bin/solr create \
-c *mycollection-name*\
-d *config-dir* \
-n *myconfig-name* \
-p *port*\
-s *Anzahl der Shards* \
-rf *number-of-replicas*

#### 3. Verknüpfen einer Sammlung mit einem Konfigurationssatz {#link-a-collection-to-a-configuration-set}

Verknüpfen einer Sammlung mit einer bereits auf ZooKeeper hochgeladenen Konfiguration

Referenz:
[https://solr.apache.org/guide/6_6/command-line-utilities.html](https://solr.apache.org/guide/6_6/command-line-utilities.html)

Verwendung:
sh ./scripts/cloud-scripts/zkcli.sh \
-cmd linkconfig \
-zkhost *server:port* \
-collection *mycollection-name* \
-confname *myconfig-name*

### Vergleich von Standard und Advanced MLS {#comparison-of-standard-and-advanced-mls}

Die mehrsprachige Suche (MLS) für AEM Communities wurde für die Solr-Plattform entwickelt, um eine verbesserte Suche in allen unterstützten Sprachen, einschließlich Englisch, zu ermöglichen.

MLS für AEM Communities ist entweder als Standard-MLS oder als erweitertes MLS verfügbar. Standard-MLS enthält nur Solr-Konfigurationseinstellungen und schließt alle Plug-ins oder Ressourcendateien aus. Advanced MLS ist die umfassendere Lösung und umfasst Solr-Konfigurationseinstellungen und Plug-ins sowie zugehörige Ressourcen

Standard-MLS enthält Verbesserungen bei der Inhaltssuche für die folgenden Sprachen:

* Englisch: Verbesserter Stemmer für den Versuch, Wortableitungen abzugleichen.
* Japanisch: Verbesserte japanische Tokenisierung für Zeichen mit halber Breite.

Das erweiterte MLS enthält Verbesserungen bei der Inhaltssuche für die folgenden Sprachen:

* Englisch: Stemmer durch Lemmatizer ersetzt.
* Deutsch: Zersetzer hinzugefügt.
* Französisch: Elizion-Handhabung hinzugefügt.
* Chinesisch (vereinfacht): Ein intelligenter Tokenizer wurde hinzugefügt.
* Verschiedene Sprachen: Es wurde ein Wortstamm, eine Stoppwortliste und ein Normalisierer hinzugefügt.

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

#### Vergleich von AEM 6.1 Solr-Suche, Standard-MLS und erweitertem MLS {#comparison-of-aem-solr-search-standard-mls-and-advanced-mls}

**Hinweis**: AEM 6.1 bezieht sich auf AEM 6.1 Communities FP3 und früher.

![compare-solr-mls](assets/compare-solr-mls.png)

### Installieren von Standard-MLS {#installing-standard-mls}

Für die SRP-Erfassung (entweder MSRP oder DSRP) ist es notwendig, zwei der Solr-Konfigurationsdateien zu ändern, um die standardmäßige mehrsprachige Suche (Standard Multilingual Search, MLS) zu unterstützen:

* **schema.xml**
* **solrconfig.xml**

Standard-MLS-Dateien (schema.xml, solrconfig.xml) für Solr 4.10.

Standard-MLS-Dateien (schema.xml, solrconfig.xml) für Solr 5.x.

Die Standard-MLS-Dateien werden im AEM-Repository gespeichert.

**Hinweis**: Solr-Dateien werden zwar im Ordner „msrp/&quot; gespeichert, sind aber auch für DSRP (keine Änderungen erforderlich).

**Download-Anweisungen**: Ersetzen Sie `solrX` je nach Bedarf durch `solr4` oder `solr5`.

1. Suchen Sie mithilfe von CRXDE|Lite nach:

   * `/libs/social/config/datastore/msrp/solrX/schema.xml`
   * `/libs/social/config/datastore/msrp/solrX/solrconfig.xml`

1. Herunterladen auf den lokalen Server, auf dem Solr bereitgestellt wird.

   * Suchen Sie die `jcr:data`-Eigenschaft des `jcr:content`.
   * Um den Download zu starten, wählen Sie `view` aus.
   * Stellen Sie sicher, dass die Dateien mit den entsprechenden Namen und der entsprechenden Codierung (UTF8) gespeichert werden.

1. Befolgen Sie die Installationsanweisungen für den eigenständigen oder SolrCloud-Modus.

#### Solr-Cloud-Modus - Standard-MLS {#solrcloud-mode-standard-mls}

1. Installieren und konfigurieren Sie Solr im Solr-Cloud-Modus.
1. Bereiten Sie eine neue Konfiguration vor:

   1. Erstellen Sie new-config-dir* wie `solr-install-dir*/myconfig/`

   1. Kopieren Sie den Inhalt des vorhandenen Solr-Konfigurationsverzeichnisses nach *new-config-dir*

      * Für Solr4: `solr-install-dir/example/solr/collection1/conf/` kopieren
      * Für Solr5: `solr-install-dir/server/solr/configsets/data_driven_schema_configs/` kopieren

   1. Kopieren Sie die heruntergeladenen **schema.xml** und **solrconfig.xml** nach *new-config-dir*, um vorhandene Dateien zu überschreiben.

1. [Laden Sie die neue Konfiguration &#x200B;](#upload-a-configuration-to-zookeeper) ZooKeeper hoch.
1. [Erstellen Sie eine Sammlung](#create-a-collection) und geben Sie die erforderlichen Parameter an, z. B. die Anzahl der Shards, die Anzahl der Replikate und den Konfigurationsnamen.
1. Wenn der Konfigurationsname bei der Erstellung der Sammlung *nicht* angegeben wurde, [verknüpfen Sie diese neu erstellte Sammlung](#link-a-collection-to-a-configuration-set) mit der auf ZooKeeper hochgeladenen Konfiguration.

1. Führen Sie für MSRP [MSRP Reindex Tool](msrp.md#msrp-reindex-tool) aus, es sei denn, diese Installation ist neu.

#### Eigenständiger Modus - Standard-MLS {#standalone-mode-standard-mls}

1. Installieren Sie Solr im Standalone-Modus.
1. Wenn Sie Solr5 ausführen, erstellen Sie eine Collection1 (ähnlich wie Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

1. Sichern Sie **schema.**) und **solrconfig.xml** im Solr-Konfigurationsverzeichnis, z. B.:

   * Für Solr4: `solr-install-dir/example/solr/collection1/conf/`
   * Erstellt für Solr5: `solr-install-dir/server/solr/collection1/conf/`

1. Kopieren Sie die heruntergeladenen **schema.xml** und **solrconfig.xml** in dasselbe Verzeichnis.

1. Starten Sie Solr neu.
1. Führen Sie für MSRP [MSRP Reindex Tool](#msrpreindextool) aus, es sei denn, diese Installation ist neu.

### Erweiterte MLS installieren {#installing-advanced-mls}

Damit die SRP-Erfassung (MSRP oder DSRP) erweiterte MLS unterstützt, sind zusätzlich zu einem benutzerdefinierten Schema und einer Solr-Konfiguration neue Solr-Plug-ins erforderlich. Alle erforderlichen Elemente werden in eine herunterladbare ZIP-Datei gepackt. Darüber hinaus ist ein Installationsskript für die Verwendung bei der Bereitstellung von Solr im eigenständigen Modus enthalten.

Informationen zum Abrufen des erweiterten MLS-Pakets finden Sie unter [AEM Advanced MLS](deploy-communities.md#aem-advanced-mls) im Abschnitt Bereitstellen der Dokumentation.

So beginnen Sie mit der Installation für SolrCloud oder den eigenständigen Modus:

* Laden Sie das ZIP-Archiv AEM-SOLR-MLS auf den Server herunter, auf dem Solr gehostet wird.
* Entpacken Sie das Archiv.

#### Solr-Cloud-Modus - Erweitertes MLS {#solrcloud-mode-advanced-mls}

Installationsanweisungen - Beachten Sie die Unterschiede für Solr4 und Solr5:

1. Installieren und konfigurieren Sie Solr im Solr-Cloud-Modus.
1. Extrahieren Sie den Inhalt des erweiterten MLS-Pakets auf die Festplatte. Der Inhalt sollte Folgendes enthalten:

   * **schema.xml**
   * **solrconfig.xml**
   * Ordner **Stoppwörter/**
   * **Ordner Profile/**
   * Ordner **extra-libs/**

1. Bereiten Sie eine neue Konfiguration vor:

   1. Erstellen Sie ein *new-config-dir*

      * Beispielsweise `solr-install-dir/myconfig/`
      * Erstellen von Unterordnern `stopwords/` und `lang/`

   1. Kopieren Sie den Inhalt des vorhandenen Solr-Konfigurationsordners nach *new-config-dir*

      * Für Solr4: `solr-install-dir/example/solr/collection1/conf/` kopieren
      * Für Solr5: `solr-install-dir/server/solr/configsets/data_driven_schema_configs/` kopieren

   1. Kopieren Sie die extrahierten **schema.xml** und **solrconfig.xml** nach *new-config-dir*, um vorhandene Dateien zu überschreiben.
   1. Für Solr5: Kopieren Sie `solr_install_dir/server/solr/configsets/sample_techproducts_configs/conf/lang/*.txt` nach `new-config-dir/lang/`
   1. Kopieren Sie den extrahierten **Stoppwörter/**-Ordner nach *new-config-dir* was zu `new-config-dir/stopwords/*.txt` führt

1. [Laden Sie die neue Konfiguration &#x200B;](#upload-a-configuration-to-zookeeper) ZooKeeper hoch.
1. Kopieren Sie den neuen **Ordner Profile/** …

   * Für Solr4: Kopieren Sie in die Ressourcen/Ordner jedes Knotens
   * Für Solr5: Kopieren Sie in die Server/Ressourcen/Ordner jeder Solr-Installation. Wenn sich alle Knoten im selben Solr-Installationsverzeichnis befinden, wird dieser Schritt nur einmal ausgeführt.

1. Erstellen Sie **Ordner „lib/**&quot; im solr-Basisverzeichnis (enthält solr.xml) jedes Knotens in SolrCloud. Kopieren Sie JARs von den folgenden Speicherorten in die neue Bibliothek/den neuen Ordner auf jedem Knoten:

   * **extra-libs/** aus dem erweiterten MLS-Paket extrahiert
   * *solr-install-dir/Contrib/extract/lib/*.jar
   * *solr-install-dir/dist/solr-cell*.jar
   * *solr-install-dir/Contrib/Clustering/lib/*.jar
   * *solr-install-dir/dist/solr-cludering*.jar
   * *solr-install-dir/contributb/langid/lib/*.jar
   * *solr-install-dir/dist/solr-langid*.jar
   * *solr-install-dir/Contrib/velocity/lib/*.jar
   * *solr-install-dir/dist/solr-velocity*.jar
   * *solr-install-dir/contributb/analysis-extras/lib/*.jar
   * *solr-install-dir/contributb/analysis-extras/lucene-libs/*.jar

1. [Erstellen Sie eine Sammlung](#create-a-collection) und geben Sie die erforderlichen Parameter an, z. B. die Anzahl der Shards, die Anzahl der Replikate und den Konfigurationsnamen.
1. Wenn der Konfigurationsname bei *Erstellung der Sammlung* angegeben wurde, verknüpfen [&#x200B; diese neu erstellte Sammlung &#x200B;](#link-a-collection-to-a-configuration-set) der Konfiguration, die in ZooKeeper hochgeladen wurde.

1. Führen Sie für MSRP [MSRP Reindex Tool](#msrpreindextool) aus, es sei denn, diese Installation ist neu.

#### Eigenständiger Modus - erweiterter MLS {#standalone-mode-advanced-mls}

Ein Installationsskript ist im Paket Advanced MLS enthalten.

Nachdem der Inhalt des Pakets auf den Server extrahiert wurde, auf dem der eigenständige Solr-Server gehostet wird, führen Sie das Installationsskript aus, um die erforderlichen Ressourcen und Konfigurationsdateien zu installieren.

* Installieren Sie Solr im Standalone-Modus.
* Wenn Sie Solr5 ausführen, erstellen Sie eine Collection1 (ähnlich wie Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

* Führen Sie das Installationsskript aus: Installieren Sie [-v 4|5] [-d solrhome] [-c collectionPath]
Dabei gilt:

   * -d solrhome

     Solr-Installationsverzeichnis

   * -c collectionPath

     Sammlungspfad in Solr

   * --help

     Befehlszeilenoptionen drucken

   * -v [4|5]

     Version für Solr festlegen

* Beispiel für Solr 4.10.4:

   * install.bat -v 4 -d c:/solr-4.10.4 -c c:/solr-4.10.4/example/solr/collection1

* Beispiel für Solr 5.4.0:

   * install.sh -v 5 -d /tmp/solr-5.4.0 -c /tmp/solr-5.4.0/server/solr/collection1

**Hinweis**:

* Das Installationsskript sichert schema.xml und solrconfig.xml, bevor neue Versionen installiert werden, indem &quot;.org“ angehängt wird

### Über solrconfig.xml {#about-solrconfig-xml}

Die Datei **solrconfig.xml** steuert das Intervall für die automatische Bestätigung und die Sichtbarkeit der Suche und erfordert Tests und Optimierungen.

`<autoCommit>`: Standardmäßig ist das AutoCommit-Intervall, das ein harter Commit für den stabilen Speicher ist, auf 15 Sekunden festgelegt. Standardmäßig wird für die Sichtbarkeit der Suche der Index vor dem Commit verwendet.

Um die Suche zu ändern und einen Index zu verwenden, der aktualisiert wird, um die durch den Commit bedingten Änderungen widerzuspiegeln, ändern Sie die enthaltene `openSearcher` in „true“.

`autoSoftCommit`: Ein „Soft“-Commit stellt sicher, dass Änderungen sichtbar sind (der Index wird aktualisiert), aber nicht, dass Änderungen mit dem stabilen Speicher synchronisiert werden (Hard Commit). Das Ergebnis ist eine Leistungsverbesserung. Standardmäßig ist `autoSoftCommit` deaktiviert, wobei die enthaltene `maxTime` auf -1 eingestellt ist.
