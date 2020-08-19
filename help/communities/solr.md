---
title: Solr-Konfiguration für SRP
seo-title: Solr-Konfiguration für SRP
description: Eine Apache Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Node Store (Oak) und dem Common Store (SRP) freigegeben werden
seo-description: Eine Apache Solr-Installation kann mithilfe verschiedener Sammlungen zwischen dem Node Store (Oak) und dem Common Store (SRP) freigegeben werden
uuid: 7356343d-073c-4266-bdcb-c7e999281476
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e228f1db-91ea-4ec3-86da-06d89d74bc72
translation-type: tm+mt
source-git-commit: 7acd89d830b9e758eec1b5a4beb18c22e4d12dcf
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 2%

---


# Solr-Konfiguration für SRP {#solr-configuration-for-srp}

## Solr für AEM Plattform {#solr-for-aem-platform}

Eine [Apache Solr](https://lucene.apache.org/solr/) -Installation kann mithilfe verschiedener Sammlungen zwischen dem [Node Store](../../help/sites-deploying/data-store-config.md) (Oak) und [Common Store](working-with-srp.md) (SRP) freigegeben werden.

Wenn sowohl die Oak- als auch die SRP-Kollektionen intensiv verwendet werden, kann aus Leistungsgründen ein zweiter Solr installiert werden.

Für Produktionsfunktionen bietet der [SolrCloud-Modus](#solrcloud-mode) eine verbesserte Leistung im Vergleich zum Standalone-Modus (ein einzelnes, lokales Solr-Setup).

### Voraussetzungen {#requirements}

Laden Sie Apache Solr herunter und installieren Sie es:

* [Version 4.10](https://archive.apache.org/dist/lucene/solr/4.10.4/) oder [Version 5.x](https://archive.apache.org/dist/lucene/solr/5.5.3/)

* Solr erfordert Java 1.7 oder höher
* Es ist kein Dienst erforderlich
* Auswahl der Ausführungsmodi:

   * Standalone-Modus
   * [SolrCloud-Modus](#solrcloud-mode) (empfohlen für Produktionsumgebungen)

* Auswahl der mehrsprachigen Suche (MLS)

   * [Installieren von Standard MLS](#installing-standard-mls)
   * [Installieren von erweiterten MLS](#installing-advanced-mls)

## SolrCloud-Modus {#solrcloud-mode}

[Der SolrCloud](https://cwiki.apache.org/confluence/display/solr/SolrCloud) -Modus wird für Produktionsumgebungen empfohlen. Bei Ausführung im SolrCloud-Modus muss SolrCloud installiert und konfiguriert werden, bevor die mehrsprachige Suche (MLS) installiert werden kann.

Es wird empfohlen, die Installationsanweisungen der SolrCloud zu befolgen:

* 3 SolrCloud-Knoten auf demselben Server.
* Ein externer Apache ZooKeeper.

Es wird außerdem empfohlen, JVM zu konfigurieren, um die Speicherbelegung und die Garbage Collection einzustellen.

### JVM-Konfigurationsbeispiel {#jvm-configuration-example}

```shell
JVM_OPTS="-server -Xmx2048m -XX:MaxPermSize=768M -XX:+UseConcMarkSweepGC -XX:+CMSClassUnloadingEnabled -Xloggc:../logs/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps -Djava.awt.headless=true"
```

### SolrCloud-Installationsbefehle {#solrcloud-setup-commands}

Bei Ausführung im SolrCloud-Modus ist vor der MLS-Installation die Verwendung und Kenntnis der folgenden SolrCloud-Setupbefehle erforderlich.

#### 1. Eine Konfiguration in ZooKeeper hochladen {#upload-a-configuration-to-zookeeper}

Referenz:
[https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities](https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities)

Nutzung:
sh ./scripts/cloud-scripts/zkcli.sh \
-cmd upconfig \
-zkhost *server:port* \
-confname *myconfig-name *\
-solrhome *solr-home-path* \
-confdir *config-dir*

#### 2. Create a collection {#create-a-collection}

Referenz:
[https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-Create
](https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-Create)

Nutzung:
./bin/solr create \
-c *mycollection-name*\
-d *config-dir* \
-n *myconfig-name* \
-p *Anschluss*\
-s *Anzahl der Schatten* \
-rf *number-of-replicas*

#### 3. Verknüpfen einer Sammlung mit einem Konfigurationssatz {#link-a-collection-to-a-configuration-set}

Verknüpfen Sie eine Sammlung mit einer Konfiguration, die bereits zu ZooKeeper hochgeladen wurde.

Referenz:
[https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities](https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities)

Nutzung:
sh ./scripts/cloud-scripts/zkcli.sh \
-cmd linkconfig \
-zkhost *server:port* \
-collection *mycollection-name* \
-confname *myconfig-name*

### Vergleich von Standard und Advanced MLS {#comparison-of-standard-and-advanced-mls}

Die mehrsprachige Suche (MLS) für AEM Communities wurde für die SOL-Plattform entwickelt, um eine verbesserte Suche in allen unterstützten Sprachen, einschließlich Englisch, zu ermöglichen.

MLS für AEM Communities ist als Standard MLS oder Advanced MLS verfügbar. Standard-MLS enthält nur Solr-Konfigurationseinstellungen und schließt alle Plug-Ins oder Ressourcendateien aus. Erweitertes MLS ist eine umfassendere Lösung und enthält SOAR-Konfigurationseinstellungen sowie Plugins und zugehörige Ressourcen

Standard MLS umfasst Verbesserungen bei der Inhaltssuche in den folgenden Sprachen:

* Englisch: Verbesserter Stil für den Versuch, Wortfolgen zuzuordnen.
* Japanisch: Verbesserte japanische Tokenisierung für Zeichen mit halber Breite.

Erweitertes MLS umfasst Verbesserungen bei der Inhaltssuche in den folgenden Sprachen:

* Englisch: Stift durch Lmmatizer ersetzt.
* Deutsch: Dekomprimierung hinzugefügt.
* Französisch: Bearbeitung von Auslieferungen wurde hinzugefügt.
* Chinesisch (vereinfacht): Es wurde ein intelligenter Tokenizer hinzugefügt.
* Verschiedene Sprachen: Es wurde ein Stier, eine Liste zum Stoppen des Wortes und ein Normalisierer hinzugefügt.

Die folgenden 33 Sprachen werden in Advanced MLS unterstützt.

| Arabisch | Deutsch | norwegisch |
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

#### Vergleich von AEM 6.1 Solr-Suche, Standard MLS und Advanced MLS {#comparison-of-aem-solr-search-standard-mls-and-advanced-mls}

**Hinweis**: AEM 6.1 bezieht sich auf AEM 6.1 Communities FP3 und früher.

![Compar-solr-mls](assets/compare-solr-mls.png)

### Installieren von Standard MLS {#installing-standard-mls}

Für die SRP-Sammlung (entweder MSRP oder DSRP) muss zur Unterstützung der standardmäßigen mehrsprachigen Suche (MLS) zwei der Solr-Konfigurationsdateien geändert werden:

* **schema.xml**
* **solrconfig.xml**

Standard-MLS-Dateien (Schema.xml, solrconfig.xml) für Solr 4.10.

Standard-MLS-Dateien (Schema.xml, solrconfig.xml) für Solr 5.x.

Die Standard-MLS-Dateien werden im AEM Repository gespeichert.

**Hinweis**: Die Solr-Dateien werden zwar im Ordner msrp/ gespeichert, aber auch für DSRP (keine Änderungen erforderlich).

**Download-Anweisungen**: Ersetzen Sie `solrX` durch `solr4` oder `solr5` gegebenenfalls.

1. Suchen Sie mit CRXDE|Lite:

   * `/libs/social/config/datastore/msrp/solrX/schema.xml`
   * `/libs/social/config/datastore/msrp/solrX/solrconfig.xml`

1. Auf lokalen Server herunterladen, auf dem Solr bereitgestellt wird.

   * Suchen Sie die `jcr:content` Eigenschaft des `jcr:data` Knotens.
   * Wählen Sie `view` die Option zum Beginn des Downloads.
   * Stellen Sie sicher, dass die Dateien mit den entsprechenden Namen und der entsprechenden Kodierung (UTF8) gespeichert werden.

1. Befolgen Sie die Installationsanweisungen für den eigenständigen oder den SolrCloud-Modus.

#### SolrCloud-Modus - Standard MLS {#solrcloud-mode-standard-mls}

1. Installieren und konfigurieren Sie Solr im SolrCloud-Modus.
1. Vorbereitung einer neuen Konfiguration:

   1. Erstellen Sie new-config-dir*, z. B. `solr-install-dir*/myconfig/`

   1. Kopieren Sie den Inhalt des vorhandenen SOLR-Konfigurationsordners in *new-config-dir*

      * Für Solr4: copy `solr-install-dir/example/solr/collection1/conf/`
      * Für Solr5: copy `solr-install-dir/server/solr/configsets/data_driven_schema_configs/`
   1. Kopieren Sie die heruntergeladenen Dateien **Schema.xml** und **solrconfig.xml** in *new-config-dir* , um vorhandene Dateien zu überschreiben.


1. [Laden Sie die neue Konfiguration](#upload-a-configuration-to-zookeeper) zu ZooKeeper hoch.
1. [Erstellen Sie eine Sammlung](#create-a-collection) , die die erforderlichen Parameter wie die Anzahl der Shades, die Anzahl der Replikate und den Konfigurationsnamen angibt.
1. Wenn der Konfigurationsname während der Erstellung der Sammlung *nicht *angegeben war, [verknüpfen Sie diese neu erstellte Sammlung](#link-a-collection-to-a-configuration-set) mit der Konfiguration, die in ZooKeeper hochgeladen wurde.

1. Führen Sie für MSRP das [MSRP Reindex Tool](msrp.md#msrp-reindex-tool)aus, es sei denn, es handelt sich um eine Neuinstallation.

#### Eigenständiger Modus - Standard MLS {#standalone-mode-standard-mls}

1. Installieren Sie Solr im eigenständigen Modus.
1. Wenn Sie Solr5 ausführen, erstellen Sie eine Collection1 (ähnlich wie bei Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

1. Backup **Schema.xml** und **solrconfig.xml** im Ordner &quot;Solr config&quot;, z. B.:

   * Für Solr4: `solr-install-dir/example/solr/collection1/conf/`
   * Für Solr5 erstellt: `solr-install-dir/server/solr/collection1/conf/`

1. Kopieren Sie die heruntergeladenen Dateien **Schema.xml** und **solrconfig.xml** in denselben Ordner.

1. Starten Sie Solr neu.
1. Führen Sie für MSRP das [MSRP Reindex Tool](#msrpreindextool)aus, es sei denn, es handelt sich um eine Neuinstallation.

### Installieren von erweiterten MLS {#installing-advanced-mls}

Damit die SRP-Sammlung (MSRP oder DSRP) erweiterte MLS unterstützen kann, sind zusätzlich zu einer benutzerdefinierten Schema- und Solr-Konfiguration neue Solr-Plug-Ins erforderlich. Alle erforderlichen Elemente werden in einer herunterladbaren ZIP-Datei zusammengefasst. Darüber hinaus wird ein Installationsskript zur Verwendung bereitgestellt, wenn Solr im eigenständigen Modus bereitgestellt wird.

Informationen zum Abrufen des erweiterten MLS-Pakets finden Sie unter [AEM Erweitertes MLS](deploy-communities.md#aem-advanced-mls) im Abschnitt &quot;Bereitstellen&quot;der Dokumentation.

Erste Schritte mit der Installation für die SolrCloud oder den eigenständigen Modus:

* Laden Sie AEM-SOLR-MLS ZIP Archiv herunter, um Solr auf dem Server zu hosten.
* Entpacken Sie das Archiv.

#### SolrCloud-Modus - Erweitertes MLS {#solrcloud-mode-advanced-mls}

Installationsanweisungen - Beachten Sie die folgenden Unterschiede für Solr4 und Solr5:

1. Installieren und konfigurieren Sie Solr im SolrCloud-Modus.
1. Extrahieren Sie den Inhalt des erweiterten MLS-Pakets auf die Festplatte. Der Inhalt sollte Folgendes umfassen:

   * **schema.xml**
   * **solrconfig.xml**
   * **Stoppwörter/** Ordner
   * **profile/** Ordner
   * **extra-libs/** folder

1. Vorbereitung einer neuen Konfiguration:

   1. Erstellen eines *new-config-dir*

      * z. B. `solr-install-dir/myconfig/`
      * Erstellen von Unterordnern `stopwords/` und `lang/`
   1. Kopieren Sie den Inhalt des vorhandenen Solr-Konfigurationsdir in *new-config-dir*

      * Für Solr4: Kopieren `solr-install-dir/example/solr/collection1/conf/`
      * Für Solr5: Kopieren `solr-install-dir/server/solr/configsets/data_driven_schema_configs/`
   1. Kopieren Sie die extrahierten Dateien **Schema.xml** und **solrconfig.xml** in *new-config-dir* , um vorhandene Dateien zu überschreiben.
   1. Für Solr5: Kopieren `solr_install_dir/server/solr/configsets/sample_techproducts_configs/conf/lang/*.txt` nach `new-config-dir/lang/`
   1. Kopieren Sie den extrahierten **stopwords/** Ordner in *new-config-dir* , was zu `new-config-dir/stopwords/*.txt`



1. [Hochladen der neuen Konfiguration](#upload-a-configuration-to-zookeeper) in ZooKeeper
1. Kopieren Sie die neuen **Profile/** Ordner ...

   * Für Solr4: In den Ordner &quot;resources/&quot;der einzelnen Knoten kopieren
   * Für Solr5: Kopieren Sie in den Server-/Ressourcen-/Ordner der einzelnen Solr-Installationen. Wenn sich alle Knoten im selben Ordner befinden, wird dieser Schritt nur einmal ausgeführt.

1. Erstellen Sie einen **Ordner &quot;lib/** &quot;im Ordner &quot;solr-home&quot;(enthält &quot;solr.xml&quot;) jedes Knotens in der SolrCloud. Kopieren Sie die JAR-Dateien von den folgenden Speicherorten in den neuen Ordner lib/ auf jedem Knoten:

   * **Extra-libs/** extrahiert aus dem erweiterten MLS-Paket
   * *solr-install-dir/Contrib/Extraktion/lib/*.jar
   * *solr-install-dir/dist/solr-cell*.jar
   * *solr-install-dir/Contrib/clustering/lib/*.jar
   * *solr-install-dir/dist/solr-clustering*.jar
   * *solr-install-dir/Contrib/langid/lib/*.jar
   * *solr-install-dir/dist/solr-langid*.jar
   * *solr-install-dir/Contrib/Velocity/lib/*.jar
   * *solr-install-dir/dist/solr-speed*.jar
   * *solr-install-dir/Contrib/Analyse-extras/lib/*.jar
   * *solr-install-dir/Contrib/Analyse-extras/lucene-libs/*.jar

1. [Erstellen Sie eine Sammlung](#create-a-collection) , die die erforderlichen Parameter wie die Anzahl der Shades, die Anzahl der Replikate und den Konfigurationsnamen angibt.
1. Wenn der Konfigurationsname bei der Erstellung der Sammlung *nicht* angegeben wurde, [verknüpfen Sie diese neu erstellte Sammlung](#link-a-collection-to-a-configuration-set) mit der Konfiguration, die zu ZooKeeper hochgeladen wurde.

1. Führen Sie für MSRP das [MSRP Reindex Tool](#msrpreindextool)aus, es sei denn, es handelt sich um eine Neuinstallation.

#### Eigenständiger Modus - Erweitertes MLS {#standalone-mode-advanced-mls}

Im erweiterten MLS-Paket ist ein Installationsskript enthalten.

Nachdem der Inhalt des Pakets auf den Server, der den eigenständigen Solr-Server hostet, extrahiert wurde, führen Sie einfach das Installationsskript aus, um die erforderlichen Ressourcen und Konfigurationsdateien zu installieren.

* Installieren Sie Solr im eigenständigen Modus.
* Wenn Sie Solr5 ausführen, erstellen Sie eine Collection1 (ähnlich wie bei Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

* Führen Sie das Installationsskript aus: Install [-v 4|5] - [d solrhome] - [c sammlungspfad], bei dem:

   * -d solrhome

      Solr-Installationsordner

   * -c sammlungspath

      Sammlungspfad in Solo

   * --help

      Optionen für Druckbefehle

   * -v [4|5]

      Version für Solo festlegen

* Beispiel für Solr 4.10.4:

   * Install.bat -v 4 -d c:/solr-4.10.4 -c:/solr-4.10.4/example/solr/collection1

* Beispiel für Solr 5.4.0:

   * Install.sh -v 5 -d /tmp/solr-5.4.0 -c /tmp/solr-5.4.0/server/solr/collection1

**Hinweis**:

* Das Installationsskript sichert &quot;Schema.xml&quot;und &quot;solrconfig.xml&quot;, bevor neue Versionen durch Anhängen von &quot;.orig&quot;installiert werden

### Informationen zu solrconfig.xml {#about-solrconfig-xml}

Die Datei &quot; **solrconfig.xml** &quot;steuert das Intervall für die automatische Übertragung und die Sichtbarkeit der Suche und erfordert Tests und Anpassungen.

`<autoCommit>`: Standardmäßig ist das AutoCommit-Intervall, das eine feste Bindung zur stabilen Datenspeicherung ist, auf 15 Sekunden eingestellt. Bei der Sichtbarkeit der Suche wird standardmäßig der Index vor der Übertragung verwendet.

Um die Suche so zu ändern, dass ein Index verwendet wird, der entsprechend den Änderungen aufgrund der Übertragung aktualisiert wird, ändern Sie die enthaltene `openSearcher` in true.

`autoSoftCommit`: Ein &#39;Soft&#39;-Commit stellt sicher, dass Änderungen sichtbar sind (der Index wird aktualisiert), stellt jedoch nicht sicher, dass Änderungen mit einer stabilen Datenspeicherung synchronisiert werden (harte Übertragung). Das Ergebnis ist eine Leistungsverbesserung. Standardmäßig `autoSoftCommit` ist die enthaltene Variable auf -1 `maxTime` gesetzt.
