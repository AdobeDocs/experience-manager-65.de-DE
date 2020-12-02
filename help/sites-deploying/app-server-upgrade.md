---
title: Schritte zur Aktualisierung von Installationen auf Anwendungsservern
seo-title: Schritte zur Aktualisierung von Installationen auf Anwendungsservern
description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über Anwendungsserver bereitgestellt werden.
seo-description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über Anwendungsserver bereitgestellt werden.
uuid: e4020966-737c-40ea-bfaa-c63ab9a29cee
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 1876d8d6-bffa-4a1c-99c0-f6001acea825
docset: aem65
translation-type: tm+mt
source-git-commit: 38ef8fc8d80009c8ca79aca9e45cf10bd70e1f1e
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 96%

---


# Schritte zur Aktualisierung von Installationen auf Anwendungsservern{#upgrade-steps-for-application-server-installations}

In diesem Abschnitt wird die Vorgehensweise zum Aktualisieren von AEM für Anwendungsserverinstallationen beschrieben.

In allen Beispielen in diesem Verfahren wird JBoss als Anwendungsserver verwendet. Zudem wird angenommen, dass Sie bereits eine funktionierende AEM-Version installiert haben. In dieser Anleitung wird die Aktualisierung von Version **AEM 5.6 auf 6.3** beschrieben.

1. Starten Sie zunächst JBoss. In den meisten Fällen können Sie hierzu das Startskript `standalone.sh` und den folgenden Befehl am Terminal ausführen.

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. Wenn AEM 5.6 bereits installiert ist, müssen Sie sicherstellen, dass die Bundles ordnungsgemäß funktionieren, indem Sie Folgendes ausführen:

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Machen Sie als Nächstes die Bereitstellung von AEM 5.6 rückgängig:

   ```shell
   rm jboss-install-folder/standalone/deployments/cq.war
   ```

1. Beenden Sie JBoss.

1. Migrieren Sie das Repository nun mithilfe des CRX2OAK-Migrationstools.

   ```shell
   java -jar crx2oak.jar crx-quickstart/repository/ crx-quickstart/oak-repository
   ```

   >[!NOTE]
   >
   >In diesem Beispiel ist oak-repository das temporäre Verzeichnis, in dem sich das neu konvertierte Repository befindet. Vergewissern Sie sich vor diesem Schritt, dass Sie über die neueste crx2oak.jar-Version verfügen.

1. Löschen Sie die erforderlichen Eigenschaften in der Datei sling.properties folgendermaßen:

   1. Öffnen Sie die Datei unter `crx-quickstart/launchpad/sling.properties`
   1. Entfernen Sie die folgenden Eigenschaften und speichern Sie die Datei:

      1. `sling.installer.dir`

      1. `felix.cm.dir`

      1. `granite.product.version`

      1. `org.osgi.framework.system.packages`

      1. `osgi-core-packages`

      1. `osgi-compendium-services`

      1. `jre-*`

      1. `sling.run.mode.install.options`

1. Entfernen Sie die nicht mehr benötigten Dateien und Ordner. Insbesondere müssen Sie diese Elemente entfernen:

   * Den Ordner **launchpad/startup**. Sie können ihn löschen, indem Sie am Terminal den folgenden Befehl ausführen: `rm -rf crx-quickstart/launchpad/startup`

   * Die Datei **base.jar**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`

   * Die Datei **BootstrapCommandFile_timestamp.txt**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. Kopieren Sie den neu migrierten Segmentspeicher an den entsprechenden Speicherort:

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. Kopieren Sie auch den Datenspeicher:

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. Als Nächstes müssen Sie den Ordner für die OSGi-Konfigurationen erstellen, die für die neue aktualisierte Instanz verwendet werden. Genauer gesagt muss ein Ordner mit dem Namen install unter **crx-quickstart** erstellt werden.

1. Erstellen Sie nun die Knotenspeicher und Datenspeicher, die mit AEM 6.3 verwendet werden. Sie können zu diesem Zweck zwei Dateien mit den folgenden Namen unter **crx-quickstart\install** erstellen:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Diese zwei Dateien legen fest, dass AEM einen „TarMK“-Knotenspeicher und einen „File“-Datenspeicher verwendet.

1. Bearbeiten Sie die Konfigurationsdateien, damit sie einsatzbereit sind. Gehen Sie dazu folgendermaßen vor:

   * hinzufügen Sie die folgende Zeile in **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:\
      `customBlobStore=true`

   * Fügen Sie dann die folgenden Zeilen zu **org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config** hinzu:

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. Entfernen Sie den CRX2-Ausführungsmodus, indem Sie Folgendes ausführen:

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. Sie müssen nun die Ausführungsmodi in der WAR-Datei für AEM 6.3 ändern. Erstellen Sie dafür zunächst einen temporären Ordner, in dem die WAR-Datei für AEM 6.3 gespeichert wird. Der Name des Ordners in diesem Beispiel lautet **temp**. Extrahieren Sie nach dem Kopieren der WAR-Datei deren Inhalte im Ordner temp:

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. Wechseln Sie nach dem Extrahieren der Inhalte zum Ordner **WEB-INF** und bearbeiten Sie die Datei `web.xml`, um die Ausführungsmodi zu ändern. Suchen Sie nach der Zeichenfolge `sling.run.modes`, um ihre Position in der XML-Datei zu bestimmen. Wenn Sie sie gefunden haben, ändern Sie die Ausführungsmodi in der nächsten Codezeile, die standardmäßig auf author gesetzt ist:

   ```shell
   <param-value >author</param-value>
   ```

1. Ändern Sie den oben genannten „author“-Wert und legen Sie die Ausführungsmodi folgendermaßen fest: author,crx3,crx3tar. Der endgültige Codeblock sollte wie folgt aussehen:

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. Erstellen Sie die JAR-Datei erneut mit den geänderten Inhalten:

   ```shell
   jar cvf aem62.war
   ```

1. Stellen Sie die neue WAR-Datei abschließend neu bereit:

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```

