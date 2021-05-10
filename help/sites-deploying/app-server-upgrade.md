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
feature: Aktualisieren
exl-id: 86dd10ae-7f16-40c8-84b6-91ff2973a523
translation-type: tm+mt
source-git-commit: d99f4ce072688f8e7d453199742618f0b2357d07
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 71%

---

# Schritte zur Aktualisierung von Installationen auf Anwendungsservern{#upgrade-steps-for-application-server-installations}

In diesem Abschnitt wird die Vorgehensweise zum Aktualisieren von AEM für Anwendungsserverinstallationen beschrieben.

Alle Beispiele in diesem Vorgang verwenden Tomcat als Anwendungsserver und implizieren, dass Sie bereits eine Arbeitsversion von AEM bereitgestellt haben. In dieser Anleitung wird die Aktualisierung von Version **AEM 6.4 auf 6.5** beschrieben.

1. Zuerst, Beginn TomCat. In den meisten Fällen können Sie dies tun, indem Sie das Startskript `./catalina.sh` des Beginns ausführen, indem Sie den folgenden Befehl aus dem Terminal ausführen:

   ```shell
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Wenn AEM 6.4 bereits bereitgestellt ist, überprüfen Sie, ob die Pakete korrekt funktionieren, indem Sie auf Folgendes zugreifen:

   ```shell
   https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Lösen Sie anschließend AEM 6.4 auf. Dies kann über den TomCat App Manager (`http://serveraddress:serverport/manager/html`) erfolgen.

1. Migrieren Sie das Repository nun mithilfe des crx2oak-Migrationstools. Laden Sie dazu die neueste Version von crx2oak von [dieser Position](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak) herunter.

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

   * Entfernen Sie **sling.options.file** durch Ausführen: `find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf`

1. Erstellen Sie nun die Knotenspeicher und Datenspeicher, die mit AEM 6.5 verwendet werden. Sie können zu diesem Zweck zwei Dateien mit den folgenden Namen unter `crx-quickstart\install` erstellen:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`
   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Diese zwei Dateien legen fest, dass AEM einen „TarMK“-Knotenspeicher und einen „File“-Datenspeicher verwendet.

1. Bearbeiten Sie die Konfigurationsdateien, damit sie einsatzbereit sind. Gehen Sie dazu folgendermaßen vor:

   * hinzufügen Sie die folgende Zeile zu `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`:

      ```customBlobStore=true```

   * Fügen Sie dann `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` die folgenden Zeilen hinzu:

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

1. Ändern Sie den obigen Autorenwert und legen Sie die Ausführungsmodi wie folgt fest: `author,crx3,crx3tar`. Der letzte Codeblock sollte wie folgt aussehen:

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

1. Stellen Sie schließlich die neue Kriegsdatei in TomCat bereit.
