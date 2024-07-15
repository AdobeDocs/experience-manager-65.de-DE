---
title: MySQL-Konfiguration für DSRP
description: Herstellen einer Verbindung zum MySQL-Server und Einrichten der UGC-Datenbank
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: eafb60be-2963-4ac9-8618-50fd9bc6fe6c
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 1%

---

# MySQL-Konfiguration für DSRP {#mysql-configuration-for-dsrp}

MySQL ist eine relationale Datenbank, in der benutzergenerierte Inhalte (UGC) gespeichert werden können.

In diesen Anweisungen wird beschrieben, wie Sie eine Verbindung zum MySQL-Server herstellen und die UGC-Datenbank einrichten.

## Voraussetzungen {#requirements}

* [Neueste Communities Feature Pack](deploy-communities.md#latestfeaturepack)
* [JDBC-Treiber für MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Eine relationale Datenbank:

   * [MySQL Server](https://dev.mysql.com/downloads/mysql/) Community-Server, Version 5.6 oder neuer

      * Kann auf demselben Host wie AEM ausgeführt oder remote ausgeführt werden

   * [MySQL-Workbench](https://dev.mysql.com/downloads/tools/workbench/)

## MySQL installieren {#installing-mysql}

[MySQL](https://dev.mysql.com/downloads/mysql/) sollte heruntergeladen und entsprechend den Anweisungen für das Ziel-OS installiert werden.

### Tabellennamen mit Kleinbuchstaben {#lower-case-table-names}

Da bei SQL nicht zwischen Groß- und Kleinschreibung unterschieden wird, müssen bei Betriebssystemen, bei denen zwischen Groß- und Kleinschreibung unterschieden wird, alle Tabellennamen in Kleinbuchstaben geschrieben werden.

So geben Sie beispielsweise alle Tabellennamen mit Kleinbuchstaben unter Linux an:

* Datei bearbeiten `/etc/my.cnf`
* Fügen Sie im Abschnitt `[mysqld]` die folgende Zeile hinzu:

  `lower_case_table_names = 1`

### UTF8-Zeichensatz {#utf-character-set}

Um eine bessere mehrsprachige Unterstützung zu bieten, ist es erforderlich, den UTF8-Zeichensatz zu verwenden.

Ändern Sie MySQL so, dass UTF8 als Zeichensatz verwendet wird:

* mysql > SET NAMES &#39;utf8&#39;;

Ändern Sie die MySQL-Datenbank in UTF8:

* Datei bearbeiten `/etc/my.cnf`
* Fügen Sie im Abschnitt `[client]` die folgende Zeile hinzu:

  `default-character-set=utf8`

* Fügen Sie im Abschnitt `[mysqld]` die folgende Zeile hinzu:

  `character-set-server=utf8`

## Installieren von MySQL Workbench {#installing-mysql-workbench}

MySQL Workbench bietet eine Benutzeroberfläche zum Ausführen von SQL-Skripten, die das Schema und die Anfangsdaten installieren.

MySQL Workbench sollte heruntergeladen und entsprechend den Anweisungen für das Zielbetriebssystem installiert werden.

## Communities-Verbindung {#communities-connection}

Wenn die MySQL Workbench zum ersten Mal gestartet wird, sofern sie nicht bereits für andere Zwecke verwendet wird, werden noch keine Verbindungen angezeigt:

![mysqlconnection](assets/mysqlconnection.png)

### Neue Verbindungseinstellungen {#new-connection-settings}

1. Wählen Sie das Symbol `+` rechts von `MySQL Connections` aus.
1. Geben Sie im Dialogfeld `Setup New Connection` die für Ihre Plattform geeigneten Werte ein.

   Zu Demonstrationszwecken mit der Autoreninstanz AEM MySQL auf demselben Server:

   * Verbindungsname: `Communities`
   * Verbindungsmethode: `Standard (TCP/IP)`
   * Hostname: `127.0.0.1`
   * Benutzername: `root`
   * Passwort: `no password by default`
   * Standardschema: `leave blank`

1. Wählen Sie `Test Connection` aus, um die Verbindung zum ausgeführten MySQL-Dienst zu überprüfen.

**Notizen**:

* Der Standardanschluss ist `3306`
* Der ausgewählte Verbindungsname wird als Datenquellenname in der [JDBC OSGi-Konfiguration](#configurejdbcconnections) angegeben.

#### Neue Communities-Verbindung {#new-communities-connection}

![ community-connection](assets/community-connection.png)

## Datenbankeinrichtung {#database-setup}

Öffnen Sie die Communities-Verbindung, um die Datenbank zu installieren.

![install-database](assets/install-database.png)

### Abrufen des SQL-Skripts {#obtain-the-sql-script}

Das SQL-Skript wird aus dem AEM Repository abgerufen:

1. Zu CRXDE Lite navigieren

   * Beispiel: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Wählen Sie den Ordner /libs/social/config/datastore/dsrp/schema aus.
1. Herunterladen `init-schema.sql`

   ![database-schema-crxde](assets/database-schema-crxde.png)

Eine Methode zum Herunterladen des Schemas ist:

* Wählen Sie den Knoten `jcr:content` für die SQL-Datei aus.
* Beachten Sie, dass der Wert für die Eigenschaft `jcr:data` ein Ansichtslink ist.

* Klicken Sie auf den Ansichtslink, um die Daten in einer lokalen Datei zu speichern.

### DSRP-Datenbank erstellen {#create-the-dsrp-database}

Gehen Sie wie folgt vor, um die Datenbank zu installieren. Der Standardname der Datenbank ist `communities`.

Wenn der Datenbankname im Skript geändert wird, müssen Sie ihn auch in der [JDBC-Konfiguration](#configurejdbcconnections) ändern.

#### Schritt 1: SQL-Datei öffnen {#step-open-sql-file}

In der MySQL Workbench

* Wählen Sie im Pulldown-Menü &quot;Datei&quot;die Option **[!UICONTROL SQL Script öffnen]**
* Wählen Sie das heruntergeladene Skript `init_schema.sql` aus

![select-sql-script](assets/select-sql-script.png)

#### Schritt 2: SQL-Script ausführen {#step-execute-sql-script}

Wählen Sie im Workbench-Fenster für die in Schritt 1 geöffnete Datei die `lightening (flash) icon` aus, um das Skript auszuführen.

In der folgenden Abbildung ist die Datei `init_schema.sql` zur Ausführung bereit:

![execute-sql-script](assets/execute-sql-script.png)

#### Aktualisieren {#refresh}

Nachdem das Skript ausgeführt wurde, muss der Abschnitt &quot;`SCHEMAS`&quot;des Felds &quot;`Navigator`&quot;aktualisiert werden, damit die neue Datenbank angezeigt wird. Verwenden Sie das Aktualisierungssymbol rechts neben &quot;SCHEMAS&quot;:

![refresh-schema](assets/refresh-schema.png)

## JDBC-Verbindung konfigurieren {#configure-jdbc-connection}

Die OSGi-Konfiguration für **Day Commons JDBC Connections Pool** konfiguriert den MySQL JDBC-Treiber.

Alle Veröffentlichungs- und AEM-Instanzen sollten auf denselben MySQL-Server verweisen.

Wenn MySQL auf einem Server ausgeführt wird, der sich von AEM unterscheidet, muss der Hostname des Servers anstelle von &quot;localhost&quot;im JDBC-Connector angegeben werden.

* Auf jeder Autoren- und Veröffentlichungsinstanz AEM.
* Mit Administratorrechten angemeldet.
* Rufen Sie die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) auf.

   * Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Suchen Sie den `Day Commons JDBC Connections Pool`
* Wählen Sie das Symbol `+` aus, um eine Verbindungskonfiguration zu erstellen.

  ![configure-jdbc-connection](assets/configure-jdbc-connection.png)

* Geben Sie die folgenden Werte ein:

   * **[!UICONTROL JDBC-Treiberklasse]**: `com.mysql.jdbc.Driver`
   * **[!UICONTROL JDBC-Verbindungs-URI]**: `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

     Geben Sie den Server anstelle von localhost an, wenn der MySQL-Server nicht derselbe ist wie dieser AEM Server *communities* der Standarddateiname für die Datenbank (Schema) ist.

   * **[!UICONTROL Benutzername]**: `root`

     Oder geben Sie den konfigurierten Benutzernamen für den MySQL-Server ein, falls nicht &quot;root&quot;.

   * **[!UICONTROL Kennwort]**:

     Löschen Sie dieses Feld, wenn kein Kennwort für MySQL festgelegt wurde.

     Geben Sie andernfalls das konfigurierte Kennwort für den MySQL-Benutzernamen ein.

   * **[!UICONTROL Datenquellenname]**: Name, der für die [MySQL-Verbindung](#new-connection-settings) eingegeben wurde, z. B. &quot;communities&quot;.

* Wählen Sie **[!UICONTROL Speichern]** aus
