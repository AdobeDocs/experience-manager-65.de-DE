---
title: MySQL-Konfiguration für DSRP
description: Verbindung zum MySQL-Server und Einrichtung der UGC-Datenbank
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

MySQL ist eine relationale Datenbank, die zum Speichern von benutzergenerierten Inhalten (User Generated Content, UGC) verwendet werden kann.

In diesen Anweisungen wird beschrieben, wie Sie eine Verbindung zum MySQL-Server herstellen und die UGC-Datenbank einrichten.

## Voraussetzungen {#requirements}

* [Neuestes Communities Feature Pack](deploy-communities.md#latestfeaturepack)
* [JDBC-Treiber für MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Eine relationale Datenbank:

   * [MySQL Server](https://dev.mysql.com/downloads/mysql/) Community Server Version 5.6 oder höher

      * Kann auf demselben Host wie AEM oder remote ausgeführt werden

   * [MySQL Workbench](https://dev.mysql.com/downloads/tools/workbench/)

## Installieren von MySQL {#installing-mysql}

[MySQL](https://dev.mysql.com/downloads/mysql/) sollte heruntergeladen und gemäß den Anweisungen für das Zielbetriebssystem installiert werden.

### Tabellennamen in Kleinbuchstaben {#lower-case-table-names}

Da SQL bei Betriebssystemen, bei denen zwischen Groß- und Kleinschreibung unterschieden wird, nicht zwischen Groß- und Kleinschreibung unterscheidet, ist es erforderlich, eine Einstellung für alle Tabellennamen in Kleinbuchstaben einzuschließen.

So geben Sie beispielsweise alle Tabellennamen in Kleinbuchstaben unter einem Linux-Betriebssystem an:

* `/etc/my.cnf` bearbeiten
* Fügen Sie im Abschnitt `[mysqld]` die folgende Zeile hinzu:

  `lower_case_table_names = 1`

### UTF8-Zeichensatz {#utf-character-set}

Um eine bessere mehrsprachige Unterstützung zu bieten, ist es erforderlich, den UTF8-Zeichensatz zu verwenden.

Ändern Sie MySQL in UTF8 als Zeichensatz:

* mysql > SET NAMES &#39;UTF8&#39;;

Ändern Sie die MySQL-Datenbank auf den Standardwert UTF8:

* `/etc/my.cnf` bearbeiten
* Fügen Sie im Abschnitt `[client]` die folgende Zeile hinzu:

  `default-character-set=utf8`

* Fügen Sie im Abschnitt `[mysqld]` die folgende Zeile hinzu:

  `character-set-server=utf8`

## Installieren von MySQL Workbench {#installing-mysql-workbench}

MySQL Workbench bietet eine Benutzeroberfläche zum Ausführen von SQL-Skripts, die das Schema und die Anfangsdaten installieren.

MySQL Workbench sollte heruntergeladen und gemäß den Anweisungen für das Zielbetriebssystem installiert werden.

## Communities-Verbindung {#communities-connection}

Wenn MySQL Workbench zum ersten Mal gestartet wird, werden noch keine Verbindungen angezeigt, es sei denn, es wird bereits für andere Zwecke verwendet:

![mysqlconnection](assets/mysqlconnection.png)

### Neue Verbindungseinstellungen {#new-connection-settings}

1. Wählen Sie das `+` rechts von `MySQL Connections` aus.
1. Geben Sie im `Setup New Connection` die für Ihre Plattform geeigneten Werte ein

   Zu Demonstrationszwecken mit der Authoring-AEM-Instanz und MySQL auf demselben Server:

   * Verbindungsname: `Communities`
   * Verbindungsmethode: `Standard (TCP/IP)`
   * Host-Name: `127.0.0.1`
   * Benutzername: `root`
   * Passwort: `no password by default`
   * Standardschema: `leave blank`

1. Wählen Sie `Test Connection` aus, um die Verbindung zum ausgeführten MySQL-Service zu überprüfen

**Hinweise**:

* Der Standard-Port ist `3306`
* Der ausgewählte Verbindungsname wird in der JDBC-OSGi-Konfiguration als [&#x200B; eingegeben](#configurejdbcconnections)

#### Neue Communities-Verbindung {#new-communities-connection}

![Community-Verbindung](assets/community-connection.png)

## Datenbank-Setup {#database-setup}

Öffnen Sie die Communities -Verbindung, um die Datenbank zu installieren.

![install-database](assets/install-database.png)

### Abrufen des SQL-Scripts {#obtain-the-sql-script}

Das SQL-Script wird aus dem AEM-Repository abgerufen:

1. Zum CRXDE Lite navigieren

   * Beispiel: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Wählen Sie den Ordner /libs/social/config/datastore/dsrp/schema aus.
1. `init-schema.sql` herunterladen

   ![database-schema-crxde](assets/database-schema-crxde.png)

Eine Methode zum Herunterladen des Schemas besteht darin:

* `jcr:content` Knoten für die SQL-Datei auswählen
* Beachten Sie, dass der Wert für die Eigenschaft `jcr:data` ein Link zum Anzeigen ist

* Klicken Sie auf den Link Anzeigen , um die Daten in einer lokalen Datei zu speichern

### DSRP-Datenbank erstellen {#create-the-dsrp-database}

Gehen Sie wie folgt vor, um die Datenbank zu installieren. Der Standardname der Datenbank lautet `communities`.

Wenn der Datenbankname im Skript geändert wird, müssen Sie ihn auch in der „JDBC[Konfiguration“ &#x200B;](#configurejdbcconnections).

#### Schritt 1: SQL-Datei öffnen {#step-open-sql-file}

In der MySQL Workbench

* Wählen Sie aus dem Pulldown-Menü Datei die Option **[!UICONTROL SQL-Script öffnen]** aus
* Heruntergeladenes `init_schema.sql` auswählen

![select-sql-script](assets/select-sql-script.png)

#### Schritt 2: SQL-Script ausführen {#step-execute-sql-script}

Wählen Sie im Workbench-Fenster für die in Schritt 1 geöffnete Datei die `lightening (flash) icon` aus, die das Skript ausführen soll.

Im folgenden Bild kann die `init_schema.sql`-Datei ausgeführt werden:

![execute-sql-script](assets/execute-sql-script.png)

#### Aktualisieren {#refresh}

Nachdem das Skript ausgeführt wurde, muss der `SCHEMAS` Abschnitt der `Navigator` aktualisiert werden, um die neue Datenbank anzuzeigen. Verwenden Sie das Aktualisierungssymbol rechts neben „SCHEMAS“:

![refresh-schema](assets/refresh-schema.png)

## JDBC-Verbindung konfigurieren {#configure-jdbc-connection}

Die OSGi-Konfiguration für **Day Commons JDBC Connections Pool** konfiguriert den MySQL JDBC-Treiber.

Alle Veröffentlichungs- und Autoren-AEM-Instanzen sollten auf denselben MySQL-Server verweisen.

Wenn MySQL auf einem anderen Server als AEM ausgeführt wird, muss der Host-Name des Servers im JDBC-Connector anstelle von „localhost“ angegeben werden.

* In jeder Autoren- und Veröffentlichungs-AEM-Instanz.
* Mit Administratorrechten angemeldet.
* Rufen Sie die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) auf.

   * Beispiel: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Suchen des `Day Commons JDBC Connections Pool`
* Wählen Sie das Symbol `+` aus, um eine Verbindungskonfiguration zu erstellen.

  ![configure-jdbc-connection](assets/configure-jdbc-connection.png)

* Geben Sie die folgenden Werte ein:

   * **[!UICONTROL JDBC-Treiberklasse]**: `com.mysql.jdbc.Driver`
   * **[!UICONTROL JDBC-Verbindungs-URI]**: `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

     Geben Sie den Server anstelle von localhost an, wenn der MySQL-Server nicht mit „this“ identisch ist. Der AEM *Server (Communities* ist der Standardname der Datenbank (Schema).

   * **[!UICONTROL Benutzername]**: `root`

     Oder geben Sie den konfigurierten Benutzernamen für den MySQL-Server ein, wenn nicht „root“.

   * **[!UICONTROL Kennwort]**:

     Löschen Sie dieses Feld, wenn kein Kennwort für MySQL festgelegt ist.

     Sonst geben Sie das konfigurierte Passwort für den MySQL-Benutzernamen ein.

   * **[!UICONTROL Datenquellenname]**: Name, der für die [MySQL-Verbindung](#new-connection-settings) eingegeben wurde, z. B. „Communities“.

* Wählen Sie **[!UICONTROL Speichern]** aus
