---
title: Schritte zur Aktualisierung von Installationen auf Anwendungsservern
description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über Anwendungsserver bereitgestellt werden.
feature: Upgrading
exl-id: 86dd10ae-7f16-40c8-84b6-91ff2973a523
source-git-commit: 5e875e0420540ca209e7d677046e8d010ae4e145
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 67%

---

# Schritte zur Aktualisierung von Installationen auf Anwendungsservern{#upgrade-steps-for-application-server-installations}

In diesem Abschnitt wird die Vorgehensweise zum Aktualisieren von AEM für Anwendungsserverinstallationen beschrieben.

In allen Beispielen in diesem Verfahren wird Tomcat als Anwendungsserver verwendet, was bedeutet, dass Sie bereits über eine funktionierende Version von AEM verfügen. In dieser Anleitung wird die Aktualisierung von Version **AEM 6.4 auf 6.5** beschrieben.

1. Beginne zuerst TomCat. In den meisten Fällen können Sie dies tun, indem Sie die `./catalina.sh` Starten Sie das Startskript, indem Sie diesen Befehl über das Terminal ausführen:

   ```shell
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Wenn AEM 6.4 bereits bereitgestellt ist, überprüfen Sie, ob die Bundles ordnungsgemäß funktionieren, indem Sie auf Folgendes zugreifen:

   ```shell
   https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Lösen Sie als Nächstes AEM 6.4 die Bereitstellung auf. Dies kann über den TomCat App Manager (`http://serveraddress:serverport/manager/html`)

1. Migrieren Sie das Repository nun mithilfe des crx2oak-Migrationstools. Laden Sie dazu die neueste Version von crx2oak herunter von [dieser Speicherort](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/).

   ```shell
   SLING_HOME= $AEM-HOME/crx-quickstart java -Xmx4096m -XX:MaxPermSize=2048M -jar crx2oak.jar --load-profile segment-fds
   ```

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

   * Entfernen **sling.options.file** durch Ausführen: `find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf`

1. Erstellen Sie nun die Knotenspeicher und Datenspeicher, die mit AEM 6.5 verwendet werden. Sie können zu diesem Zweck zwei Dateien mit den folgenden Namen unter `crx-quickstart\install` erstellen:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`
   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Diese zwei Dateien legen fest, dass AEM einen „TarMK“-Knotenspeicher und einen „File“-Datenspeicher verwendet.

1. Bearbeiten Sie die Konfigurationsdateien, damit sie einsatzbereit sind. Gehen Sie dazu folgendermaßen vor:

   * Fügen Sie die folgende Zeile zu `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`:

      `customBlobStore=true`

   * Fügen Sie dann die folgenden Zeilen zu `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`:

      ```
      path=./crx-quickstart/repository/datastore
      minRecordLength=4096
      ```

1. Ändern Sie nun die Ausführungsmodi in der WAR-Datei für AEM 6.5. Erstellen Sie dafür zunächst einen temporären Ordner, in dem die WAR-Datei für AEM 6.5 gespeichert wird. Der Name des Ordners in diesem Beispiel lautet `temp`. Extrahieren Sie nach dem Kopieren der WAR-Datei deren Inhalte im Ordner temp:

   ```
   jar xvf aem-quickstart-6.5.0.war
   ```

1. Wechseln Sie nach dem Extrahieren der Inhalte zum Ordner **WEB-INF** und bearbeiten Sie die Datei web.xml, um die Ausführungsmodi zu ändern. Suchen Sie nach der Zeichenfolge `sling.run.modes`, um ihre Position in der XML-Datei zu bestimmen. Wenn Sie sie gefunden haben, ändern Sie die Ausführungsmodi in der nächsten Codezeile, die standardmäßig auf author gesetzt ist:

   ```bash
   <param-value >author</param-value>
   ```

1. Ändern Sie den obigen Autorenwert und legen Sie die Ausführungsmodi auf Folgendes fest: `author,crx3,crx3tar`. Der endgültige Codeblock sollte wie folgt aussehen:

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

1. Stellen Sie schließlich die neue War-Datei in TomCat bereit.
