---
title: Upgrade des JBoss EAP-Clusters von 7.4.10 auf 7.4.23 für AEM Forms on JEE
description: Zusätzliche Schritte zum Upgrade eines JBoss EAP-Clusters von 7.4.10 auf 7.4.23 für AEM Forms on JEE.
exl-id: 2c9e7f41-a8d6-4b03-8e5c-1a4f6d9e0b72
solution: Experience Manager, Experience Manager Forms
feature: AEM Forms on JEE
role: User, Developer
source-git-commit: dffa92539a8205387d21d3873ab9424508182f19
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 1%

---

# Upgrade des JBoss EAP-Clusters von 7.4.10 auf 7.4.23 für AEM Forms on JEE {#upgrade-jboss-eap-cluster-from-7-4-10-to-7-4-23}

## Überblick {#overview}

Wenn Sie einen JBoss EAP-Cluster von Version 7.4.10 auf 7.4.23 für AEM Forms on JEE aktualisieren, ist eine zusätzliche Konfiguration erforderlich, die über die eigenständigen Upgrade-Schritte hinausgeht. Cluster-spezifische Einstellungen wie Cache-Locators, Master-Slave-Authentifizierung, Host-Bindungen und Domain-Controller-Konfiguration müssen bei der neuen JBoss-Installation aktualisiert werden.

## Gilt für {#applies-to}

Dieser Artikel gilt für:

* AEM Forms on JEE läuft auf JBoss EAP 7.4.10 in einer Cluster-Umgebung
* Master-Slave JBoss EAP-Konfigurationen unter Windows und Linux

## Voraussetzungen {#prerequisites}

Führen Sie alle Schritte in [Upgrade von JBoss EAP für AEM Forms on JEE vom 7.4.10 bis 7.4.23 aus](/help/forms/using/upgrade-jboss-eap-from-7-4-10-to-7-4-23.md) aus. Kopieren Sie dabei auch die Verbindungs-URL, den Benutzernamen und das Kennwort aus der bestehenden -Installation in die neuen Konfigurationsdateien.

## Schritte {#steps}

Führen Sie die folgenden zusätzlichen Cluster-spezifischen Schritte aus:

### Aktualisieren der Datei domain.conf.bat {#update-domain-conf-bat}

1. Fügen Sie in Ihrer `domain.conf.bat` die Locators-Informationen aus Ihrer vorhandenen Einrichtung zur neuen Datei hinzu:

   ```text
   set "JAVA_OPTS=%JAVA_OPTS% -Doak.documentMK.maxServerTimeDiffMillis=-1"
   set "JAVA_OPTS=%JAVA_OPTS% -Dadobe.cache.cluster-locators=<ip-address-master>[22345],<ip-address-slave>[22345]"
   set "JAVA_OPTS=%JAVA_OPTS% -DentityExpansionLimit=10000"
   ```

### Master-Slave-Authentifizierung konfigurieren {#configure-master-slave-authentication}

1. Erstellen Sie einen neuen Benutzer für die Master-Slave-Authentifizierung auf dem Master-Knoten.
1. Aktualisieren Sie auf den Slave-Knoten das Benutzerkennwort in `host.xml`:

   ```xml
   <server-identities>
       <secret value="Y2hhbmdlaXQ="/>
   </server-identities>
   ```

### Aktualisieren von IP-Adressen in host.xml {#update-ip-addresses-in-host-xml}

1. Aktualisieren Sie die IP-Adressen für Master- und Slave-Knoten in `host.xml`:

   ```xml
   <interfaces>
       <interface name="management">
           <inet-address value="${jboss.bind.address.management:<ip-address>}"/>
       </interface>
       <interface name="public">
           <inet-address value="${jboss.bind.address:<ip-address>}"/>
       </interface>
   </interfaces>
   ```

### Entfernen von Bereitstellungen aus der Domain-Konfiguration {#remove-deployments-from-domain-configuration}

1. Stellen Sie sicher, dass in der neuen `domain_<db>.xml`-Datei kein `<deployments>` vorhanden ist.
1. Kopieren Sie den folgenden Block nicht aus der vorhandenen Konfiguration:

   ```xml
   <deployments>
       <deployment name="adobe-forms-ivs-jboss.ear" runtime-name="adobe-forms-ivs-jboss.ear"/>
       <deployment name="adobe-livecycle-cq-author.ear" runtime-name="adobe-livecycle-cq-author.ear"/>
       <deployment name="adobe-livecycle-jboss.ear" runtime-name="adobe-livecycle-jboss.ear"/>
       <deployment name="adobe-livecycle-native-jboss-x86_win32.ear" runtime-name="adobe-livecycle-native-jboss-x86_win32.ear"/>
       <deployment name="adobe-livecycle-native-jboss-x86_win64.ear" runtime-name="adobe-livecycle-native-jboss-x86_win64.ear"/>
       <deployment name="adobe-output-ivs-jboss.ear" runtime-name="adobe-output-ivs-jboss.ear"/>
       <deployment name="adobe-workspace-client.ear" runtime-name="adobe-workspace-client.ear"/>
   </deployments>
   ```

### Treiberklasse in der Domain-Konfiguration aktualisieren {#update-driver-class-in-domain-configuration}

1. Aktualisieren Sie den Abschnitt zur Treiberklasse in `domain_<db>.xml` basierend auf Ihrer Datenbank-Engine:

   **MSSQL:**

   ```xml
   <xa-datasource-class>com.microsoft.sqlserver.jdbc.SQLServerXADataSource</xa-datasource-class>
   ```

   **Oracle:**

   ```xml
   <xa-datasource-class>oracle.jdbc.xa.client.OracleXADataSource</xa-datasource-class>
   ```

### Domänencontroller auf Slave-Knoten aktualisieren {#update-domain-controller-on-slave-nodes}

1. Aktualisieren Sie den Domain-Controller-Block auf dem Slave-Knoten in `host.xml` mit der Master-IP-Adresse, Port `9999`, `slave1` und `ManagementRealm`:

   ```xml
   <remote host="<ip-address>" port="9999" username="slave1" realm="ManagementRealm"/>
   ```

### Aktualisieren von jboss-cli.xml {#update-jboss-cli-xml}

1. Aktualisieren Sie den `<host>` in `jboss-cli.xml` sowohl auf dem Master- als auch auf dem Slave-Knoten.
