---
title: Schritte zur Aktualisierung von Installationen auf Anwendungs-Servern
description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über Anwendungsserver bereitgestellt werden.
feature: Upgrading
exl-id: 86dd10ae-7f16-40c8-84b6-91ff2973a523
source-git-commit: c0574b50f3504a4792405d6fcd8aa3a2e8e6c686
workflow-type: ht
source-wordcount: '452'
ht-degree: 100%

---

# Schritte zur Aktualisierung von Installationen auf Anwendungs-Servern{#upgrade-steps-for-application-server-installations}

In diesem Abschnitt wird die Vorgehensweise zum Aktualisieren von AEM für Anwendungsserverinstallationen beschrieben.

In allen Beispielen in diesem Verfahren wird Tomcat als Anwendungs-Server verwendet. Zudem wird vorausgesetzt, dass Sie bereits eine funktionierende AEM-Version installiert haben. In dieser Anleitung wird die Aktualisierung von **AEM 6.4 auf 6.5** beschrieben.

1. Starten Sie zunächst TomCat. In den meisten Fällen können Sie hierzu das Startskript `./catalina.sh` über den folgenden Befehl am Terminal ausführen.

   ```shell
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Wenn AEM 6.4 bereits installiert ist, müssen Sie sicherstellen, dass die Bundles ordnungsgemäß funktionieren, indem Sie Folgendes aufrufen:

   ```shell
   https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Heben Sie als Nächstes über TomCat App Manager (`http://serveraddress:serverport/manager/html`) die Bereitstellung von AEM 6.4 auf.

1. Migrieren Sie das Repository nun mithilfe des crx2oak-Migrations-Tools. Laden Sie dazu die neueste Version von crx2oak von [diesem Speicherort](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/) herunter.

   ```shell
   SLING_HOME= $AEM-HOME/crx-quickstart java -Xmx4096m -jar crx2oak.jar --load-profile segment-fds
   ```

1. Löschen Sie die erforderlichen Eigenschaften in der Datei sling.properties folgendermaßen:

   1. Öffnen Sie die unter `crx-quickstart/launchpad/sling.properties` gespeicherte Datei.
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

   * Entfernen Sie die Datei **sling.options.file**, indem Sie folgenden Befehl ausführen: `find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf`

1. Erstellen Sie nun die Knotenspeicher und Datenspeicher, die mit AEM 6.5 verwendet werden. Sie können zu diesem Zweck zwei Dateien mit den folgenden Namen unter `crx-quickstart\install` erstellen:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`
   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Diese zwei Dateien legen fest, dass AEM einen „TarMK“-Knotenspeicher und einen „File“-Datenspeicher verwendet.

1. Bearbeiten Sie die Konfigurationsdateien, damit sie einsatzbereit sind. Gehen Sie dazu folgendermaßen vor:

   * Fügen Sie die folgende Zeile zu `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` hinzu:

      `customBlobStore=true`

   * Fügen Sie dann die folgenden Zeilen zu `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` hinzu:

      ```
      path=./crx-quickstart/repository/datastore
      minRecordLength=4096
      ```

1. Ändern Sie nun die Ausführungsmodi in der WAR-Datei für AEM 6.5. Erstellen Sie dafür zunächst einen temporären Ordner, in dem die WAR-Datei für AEM 6.5 gespeichert wird. Der Name des Ordners in diesem Beispiel lautet `temp`. Extrahieren Sie nach dem Kopieren der WAR-Datei deren Inhalte im temporären Ordner:

   ```
   jar xvf aem-quickstart-6.5.0.war
   ```

1. Wechseln Sie nach dem Extrahieren der Inhalte zum Ordner **WEB-INF** und bearbeiten Sie die Datei web.xml, um die Ausführungsmodi zu ändern. Suchen Sie nach der Zeichenfolge `sling.run.modes`, um ihre Position in der XML-Datei zu bestimmen. Wenn Sie sie gefunden haben, ändern Sie die Ausführungsmodi in der nächsten Code-Zeile, die standardmäßig auf author gesetzt ist:

   ```bash
   <param-value >author</param-value>
   ```

1. Ändern Sie den oben genannten „author“-Wert und legen Sie die Ausführungsmodi folgendermaßen fest: `author,crx3,crx3tar`. Der endgültige Code-Block sollte wie folgt aussehen:

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. Erstellen Sie die JAR-Datei erneut mit den geänderten Inhalten:

   ```bash
   jar cvf aem65.war
   ```

1. Stellen Sie schließlich die neue war-Datei in TomCat bereit.
