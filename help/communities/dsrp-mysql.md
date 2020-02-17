---
title: MySQL-Konfiguration für DSRP
seo-title: MySQL-Konfiguration für DSRP
description: Verbindung zum MySQL-Server herstellen und die UGC-Datenbank einrichten
seo-description: Verbindung zum MySQL-Server herstellen und die UGC-Datenbank einrichten
uuid: c058cc88-7ca2-4aed-9a36-b080e603f886
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: edc3043c-7ec4-4e4a-b008-95f1784f012e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# MySQL-Konfiguration für DSRP {#mysql-configuration-for-dsrp}

MySQL ist eine relationale Datenbank, mit der benutzergenerierte Inhalte (UGC) gespeichert werden können.

Diese Anweisungen beschreiben, wie eine Verbindung zum MySQL-Server hergestellt und die UGC-Datenbank eingerichtet wird.

## Voraussetzungen {#requirements}

* [neueste Communities Feature Pack](deploy-communities.md#latestfeaturepack)
* [JDBC-Treiber für MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Eine relationale Datenbank:

   * [MySQL Server](https://dev.mysql.com/downloads/mysql/) Community Server Version 5.6 oder höher

      * Kann auf demselben Host wie AEM ausgeführt oder remote ausgeführt werden
   * [MySQL-Workbench](https://dev.mysql.com/downloads/tools/workbench/)


## MySQL installieren {#installing-mysql}

[MySQL](https://dev.mysql.com/downloads/mysql/) sollte gemäß den Anweisungen für das Zielbetriebssystem heruntergeladen und installiert werden.

### Tabellennamen in Kleinbuchstaben {#lower-case-table-names}

Da bei SQL nicht zwischen Groß- und Kleinschreibung unterschieden wird, müssen bei Betriebssystemen, bei denen die Groß-/Kleinschreibung beachtet wird, alle Tabellennamen in Kleinbuchstaben eingestellt werden.

So geben Sie beispielsweise alle Tabellennamen in Kleinbuchstaben unter Linux an:

* Datei bearbeiten `/etc/my.cnf`
* Fügen Sie im `[mysqld]` Abschnitt die folgende Zeile hinzu:

   `lower_case_table_names = 1`

### UTF8-Zeichensatz {#utf-character-set}

Um eine bessere mehrsprachige Unterstützung zu bieten, muss der UTF8-Zeichensatz verwendet werden.

Ändern Sie MySQL so, dass UTF8 als Zeichensatz verwendet wird:

* mysql> SET NAMES &#39;utf8&#39;;

Ändern Sie die MySQL-Datenbank in UTF8:

* Datei bearbeiten `/etc/my.cnf`
* Fügen Sie im `[client]` Abschnitt die folgende Zeile hinzu:

   `default-character-set=utf8`

* Fügen Sie im `[mysqld]` Abschnitt die folgende Zeile hinzu:

   `character-set-server=utf8`

## MySQL Workbench installieren {#installing-mysql-workbench}

MySQL Workbench bietet eine Benutzeroberfläche zum Ausführen von SQL-Skripten, die das Schema und die Ausgangsdaten installieren.

MySQL Workbench sollte gemäß den Anweisungen für das Zielbetriebssystem heruntergeladen und installiert werden.

## Communities-Verbindung {#communities-connection}

Wenn MySQL Workbench zum ersten Mal gestartet wird, werden, sofern sie nicht bereits für andere Zwecke verwendet werden, noch keine Verbindungen angezeigt:

![chlimage_1-104](assets/chlimage_1-104.png)

### Neue Verbindungseinstellungen {#new-connection-settings}

1. Wählen Sie das `+` Symbol rechts neben `MySQL Connections`.
1. Geben Sie im Dialogfeld `Setup New Connection`die für Ihre Plattform geeigneten Werte ein

   Zu Demonstrationszwecken mit dem Autor AEM-Instanz und MySQL auf demselben Server:

   * Verbindungsname: `Communities`
   * Verbindungsmethode: `Standard (TCP/IP)`
   * Hostname: `127.0.0.1`
   * Benutzername: `root`
   * Kennwort: `no password by default`
   * Standardschema: `leave blank`

1. Wählen Sie `Test Connection` zur Überprüfung der Verbindung mit dem ausgeführten MySQL-Dienst

**Hinweise**:

* Der Standardanschluss ist `3306`
* Der ausgewählte Verbindungsname wird als Datenquellenname in der [JDBC OSGi-Konfiguration eingegeben](#configurejdbcconnections)

#### Neue Communities-Verbindung {#new-communities-connection}

![chlimage_1-105](assets/chlimage_1-105.png)

## Datenbank einrichten {#database-setup}

Öffnen Sie die Communities-Verbindung, um die Datenbank zu installieren.

![chlimage_1-106](assets/chlimage_1-106.png)

### SQL-Skript abrufen {#obtain-the-sql-script}

Das SQL-Skript wird vom AEM-Repository abgerufen:

1. Zu CRXDE Lite navigieren

   * For example, [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Wählen Sie den Ordner /libs/social/config/datastore/dsrp/schema
1. Download `init-schema.sql`

![chlimage_1-107](assets/chlimage_1-107.png)

Eine Methode zum Herunterladen des Schemas ist

* Wählen Sie den `jcr:content`Knoten für die SQL-Datei aus
* Beachten Sie, dass der Wert für die `jcr:data`Eigenschaft ein Ansichtslink ist

* Link &quot;Ansicht&quot;auswählen, um die Daten in einer lokalen Datei zu speichern

### DSRP-Datenbank erstellen {#create-the-dsrp-database}

Gehen Sie wie folgt vor, um die Datenbank zu installieren. Der Standardname der Datenbank ist `communities`.

Wenn der Datenbankname im Skript geändert wird, müssen Sie ihn auch in der [JDBC-Konfiguration](#configurejdbcconnections)ändern.

#### Schritt 1: SQL-Datei öffnen {#step-open-sql-file}

In der MySQL-Workbench

* Über das Pulldown-Menü Datei
* Wählen Sie die heruntergeladene `init_schema.sql`

![chlimage_1-108](assets/chlimage_1-108.png)

#### Schritt 2: SQL Script ausführen {#step-execute-sql-script}

Wählen Sie im Workbench-Fenster für die in Schritt 1 geöffnete Datei das Skript `lightening (flash) icon` aus.

In der folgenden Abbildung steht die `init_schema.sql` Datei zur Ausführung bereit:

![chlimage_1-109](assets/chlimage_1-109.png)

#### Aktualisieren {#refresh}

Nach Ausführung des Skripts muss der `SCHEMAS`Abschnitt des Skripts aktualisiert werden, `Navigator` damit die neue Datenbank angezeigt wird. Verwenden Sie das Aktualisierungssymbol rechts neben &quot;SCHEMAS&quot;:

![chlimage_1-110](assets/chlimage_1-110.png)

## JDBC-Verbindung konfigurieren {#configure-jdbc-connection}

Der JDBC Connections Pool **von OSGi für** Day Commons konfiguriert den MySQL JDBC-Treiber.

Alle Veröffentlichungs- und Autoreninstanzen von AEM sollten auf denselben MySQL-Server verweisen.

Wenn MySQL auf einem Server ausgeführt wird, der sich von AEM unterscheidet, muss der Hostname des Servers anstelle von &quot;localhost&quot;im JDBC-Connector angegeben werden.

* Auf jeder Autoren- und Veröffentlichungsinstanz von AEM
* Mit Administratorrechten angemeldet
* Access the [web console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Suchen Sie die `Day Commons JDBC Connections Pool`
* Wählen Sie das `+` Symbol, um eine neue Verbindungskonfiguration zu erstellen.

![chlimage_1-111](assets/chlimage_1-111.png)

* Geben Sie die folgenden Werte ein:

   * **[!UICONTROL JDBC-Treiberklasse]**: `com.mysql.jdbc.Driver`
   * **[!UICONTROL JDBC-Verbindungs-URI]**: `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

      Server anstelle von localhost angeben, wenn der MySQL-Server nicht mit dem AEM-Server &quot;this&quot;identisch ist

      *Communities* ist der standardmäßige Datenbankname (Schema)

   * **[!UICONTROL Benutzername]**: `root`

      Oder geben Sie den konfigurierten Benutzernamen für den MySQL-Server ein, wenn nicht &quot;root&quot;

   * **[!UICONTROL Kennwort]**:

      Löschen Sie dieses Feld, wenn für MySQL kein Kennwort festgelegt wurde,

      andernfalls geben Sie das konfigurierte Kennwort für den MySQL-Benutzernamen ein
   * **[!UICONTROL Name]** der Datenquelle: Name, der für die [MySQL-Verbindung](#new-connection-settings)eingegeben wurde, z. B. &quot;Communities&quot;

* Wählen Sie **[!UICONTROL Speichern]**

