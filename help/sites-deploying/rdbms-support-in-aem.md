---
title: RDBMS-Unterstützung in AEM 6.4
description: Erfahren Sie mehr über die Unterstützung der Persistenz von relationalen Datenbanken in AEM 6.4 und die verfügbaren Konfigurationsoptionen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
feature: Configuring
exl-id: 1e34c5ca-9e08-4b2a-901c-ab28aeb4a807
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 72%

---

# RDBMS-Unterstützung in AEM 6.4{#rdbms-support-in-aem}

## Überblick {#overview}

Die Unterstützung der relativen Datenbankpersistenz in AEM wird mithilfe des Document Microkernel implementiert. Der Document Microkernel ist die Grundlage, die auch für die Implementierung der MongoDB-Persistenz verwendet wird.

Er umfasst eine Java-API, die auf der Mongo-Java-API basiert. Eine BlobStore-API wird ebenfalls implementiert. Standardmäßig werden Blobs in der Datenbank gespeichert.

Weitere Informationen zu den Implementierungsdetails finden Sie unter [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) und [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) Dokumentation.

>[!NOTE]
>
>Unterstützung für **PostgreSQL 9.4** wird ebenfalls bereitgestellt, jedoch nur zu Demozwecken. Sie ist nicht für Produktionsumgebungen verfügbar.

## Unterstützte Datenbanken {#supported-databases}

Weitere Informationen zur Unterstützung der Relationalen Datenbank in AEM finden Sie im Abschnitt [Seite &quot;Technische Anforderungen&quot;](/help/sites-deploying/technical-requirements.md).

## Konfigurationsschritte {#configuration-steps}

Das Repository wird durch Konfigurieren des OSGi-Dienstes `DocumentNodeStoreService` erstellt. Es wurde erweitert, um neben MongoDB auch die Persistenz der relationalen Datenbank zu unterstützen.

Um diese nutzen zu können, muss eine Datenquelle mithilfe von AEM konfiguriert werden. Dies geschieht über die Datei `org.apache.sling.datasource.DataSourceFactory.config`. Die JDBC-Treiber für die jeweilige Datenbank müssen separat als OSGi-Bundles in der lokalen Konfiguration bereitgestellt werden.

Anweisungen zum Erstellen von OSGi-Bundles für JDBC-Treiber finden Sie in diesem [Dokumentation](https://sling.apache.org/documentation/bundles/datasource-providers.html#convert-driver-jars-to-bundle) auf der Apache Sling-Website.

Sobald die Bundles eingerichtet sind, führen Sie die folgenden Schritte aus, um AEM mit RDB-Persistenz zu konfigurieren:

1. Stellen Sie sicher, dass der Datenbank-Daemon gestartet ist und eine aktive Datenbank für die Verwendung mit AEM vorhanden ist.
1. Kopieren Sie die AEM 6.3-JAR-Datei in das Installationsverzeichnis.
1. Erstellen Sie im Installationsverzeichnis einen Ordner namens `crx-quickstart\install`.
1. Konfigurieren Sie den Document-Knotenspeicher, indem Sie eine Konfigurationsdatei mit dem folgenden Namen im Verzeichnis `crx-quickstart\install` erstellen:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Erstellen Sie eine weitere Konfigurationsdatei mit dem folgenden Namen im Ordner `crx-quickstart\install`, um die Datenquelle und die JDBC-Parameter zu konfigurieren:

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`

   >[!NOTE]
   >
   >Detaillierte Informationen zur Datenquellenkonfiguration für die einzelnen unterstützten Datenbanken finden Sie unter [Konfigurationsoptionen für die Datenquelle](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. Bereiten Sie dann die JDBC-OSGi-Bundles für die Verwendung mit AEM vor:

   1. Erstellen Sie im Ordner `crx-quickstart/install` einen Ordner namens `9`.

   1. Platzieren Sie die JDBC-JAR-Datei im neuen Ordner.

1. Starten Sie abschließend AEM mit den Ausführungsmodi `crx3` und `crx3rdb`:

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## Konfigurationsoptionen für die Datenquelle {#data-source-configuration-options}

Die OSGi-Konfiguration `org.apache.sling.datasource.DataSourceFactory-oak.config` dient zum Konfigurieren der erforderlichen Parameter für die Kommunikation zwischen AEM und der Datenbank-Persistenz-Schicht.

Folgende Konfigurationsoptionen sind verfügbar:

* `datasource.name:` Der Name der Datenquelle. Der Standardwert lautet `oak`.

* `url:` Die URL-Zeichenfolge der Datenbank, die mit JDBC verwendet werden muss. Jeder Datenbanktyp hat ein eigenes Format für die URL-Zeichenfolge. Weitere Informationen finden Sie nachfolgend unter [URL-Zeichenfolgenformate](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats).

* `driverClassName:` Der Name der JDBC-Treiberklasse. Dieser variiert je nach der zu verwendenden Datenbank und dem Treiber, der für die Verbindung mit derselben benötigt wird. Nachfolgend finden Sie die Klassennamen aller von AEM unterstützten Datenbanken:

   * `org.postgresql.Driver` für PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` für DB2;
   * `oracle.jdbc.OracleDriver` für Oracle;
   * `com.mysql.jdbc.Driver` für MySQL und MariaDB (experimentell)
   * c`om.microsoft.sqlserver.jdbc.SQLServerDriver` für Microsoft SQL Server (experimentell)

* `username:` Der Benutzername, unter dem die Datenbank ausgeführt wird.

* `password:` Das Datenbankkennwort.

### URL-Zeichenfolgenformate {#url-string-formats}

Je nach dem zu verwendenden Datenbanktyp wird ein unterschiedliches URL-Zeichenfolgenformat in der Datenquellenkonfiguration verwendet. Nachstehend finden Sie eine Liste der Formate für die Datenbanken, die derzeit AEM unterstützt:

* `jdbc:postgresql:databasename` für PostgreSQL;
* `jdbc:db2://localhost:port/databasename` für DB2;
* `jdbc:oracle:thin:localhost:port:SID` für Oracle;
* `jdbc:mysql://localhost:3306/databasename` für MySQL und MariaDB (experimentell)
* `jdbc:sqlserver://localhost:1453;databaseName=name` für Microsoft SQL Server (experimentell)

## Bekannte Einschränkungen {#known-limitations}

Die gleichzeitige Verwendung mehrerer AEM Instanzen mit einer einzigen Datenbank wird zwar durch die RDBMS-Persistenz unterstützt, gleichzeitige Installationen jedoch nicht.

Um dieses Problem zu umgehen, führen Sie zuerst die Installation mit nur einer Instanz aus und fügen Sie dann nach Abschluss derselben weitere hinzu.
