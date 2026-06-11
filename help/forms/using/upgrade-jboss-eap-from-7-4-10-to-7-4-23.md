---
title: Upgrade von JBoss EAP von 7.4.10 auf 7.4.23 für AEM Forms on JEE
description: Schritte zum Upgrade von JBoss EAP von 7.4.10 auf 7.4.23 für eigenständige Umgebungen in AEM Forms on JEE.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
exl-id: 8f4c2a91-6b3d-4e7f-9c12-5d8e1f0a2b34
solution: Experience Manager, Experience Manager Forms
feature: AEM Forms Upgrade,AEM Forms on JEE
role: User, Developer
source-git-commit: 652162941dd716ae797ce50709e91757dad99054
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 4%

---

# Upgrade von JBoss EAP von 7.4.10 auf 7.4.23 für AEM Forms on JEE {#upgrade-jboss-eap-from-7-4-10-to-7-4-23}

## Überblick {#overview}

Aktualisieren von JBoss EAP von Version 7.4.10 auf 7.4.23 in einer eigenständigen Umgebung von AEM Forms on JEE. Für das Upgrade müssen Konfigurationsdateien, Datenbankanmeldeinformationen und das CRX-Repository in die neue JBoss-Installation migriert und Configuration Manager ausgeführt werden, um das Setup abzuschließen.

## Gilt für {#applies-to}

Dieser Artikel gilt für:

* AEM Forms on JEE, das unter JBoss EAP 7.4.10 in einer eigenständigen Umgebung ausgeführt wird
* Turnkey- und Teilinstallationsmodi unter Windows und Linux

>[!NOTE]
>
> Wenn Sie ein Upgrade einer JBoss-Cluster-Umgebung durchführen, führen Sie zuerst die Schritte in diesem Artikel und dann die zusätzlichen Schritte in [Upgrade von JBoss EAP-Cluster von 7.4.10 auf 7.4.23 für AEM Forms on JEE](/help/forms/using/upgrade-jboss-eap-cluster-from-7-4-10-to-7-4-23.md) aus.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen:

* Laden Sie das JBoss 7.4.23-Paket vom [Adobe Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aem.html) herunter.
* Stellen Sie sicher, dass Sie administrativen Zugriff auf die Zielumgebung haben.
* Erstellen Sie eine vollständige Sicherung der vorhandenen JBoss-Installation.

## Schritte {#steps}

Führen Sie die folgenden Schritte aus, um JBoss EAP von 7.4.10 auf 7.4.23 zu aktualisieren:

### Herunterladen und Extrahieren von JBoss {#download-and-extract-jboss}

1. Laden Sie das ZIP-Paket JBoss 7.4.23 vom Adobe Software Distribution-Portal herunter.
1. Extrahieren Sie die ZIP-Datei in ein lokales Verzeichnis.
1. Benennen Sie den extrahierten JBoss-Ordner um, damit er genau dem Namen des vorhandenen JBoss-Installationsverzeichnisses entspricht.

### Vorhandene Installation sichern {#back-up-the-existing-installation}

1. Erstellen Sie eine vollständige Sicherung des aktuellen JBoss-Installationsverzeichnisses.
1. Stellen Sie sicher, dass das Backup alle Konfigurationsdateien und Anpassungen enthält.

### Datenbankdateien konfigurieren {#configure-database-files}

1. Navigieren Sie zum Konfigurationsverzeichnis:

   * Windows: `<JBoss_Home>\standalone\configuration`
   * Linux: `<JBoss_Home>/standalone/configuration`

1. Konfigurieren Sie die Datenbankdateien entsprechend Ihrem Installationsmodus:

   **Turnkey-Modus:**

   1. Benennen Sie `lc_mysql.xml` in `lc_turnkey.xml` um.
   1. Löschen Sie die folgenden Dateien:

      * `lc_oracle.xml`
      * `lc_mssql.xml`

   **Teilweise Turnkey-Modus:**

   1. Behalten Sie nur die `lc_db.xml` Datei, die Ihrer Datenbank-Engine entspricht.
   1. Löschen Sie die anderen beiden `lc_db.xml` Konfigurationsdateien.

### Aktualisieren von Datenbankanmeldeinformationen {#update-database-credentials}

1. Öffnen Sie die `lc_turnkey.xml`-Datei aus der gesicherten JBoss-Installation.
1. Kopieren Sie die folgenden Werte:

   * Datenquellen-URL
   * Benutzername der Datenbank
   * Datenbankkennwort

1. Aktualisieren Sie die entsprechenden Einträge in der neuen `lc_turnkey.xml`.

### Migrieren des CRX-Repositorys {#migrate-crx-repository}

1. Navigieren Sie in der alten JBoss-Installation zum folgenden Verzeichnis:

   `<old_jboss>\bin\`

1. Kopieren Sie den Ordner `crx-quickstart`:
1. Fügen Sie den Ordner ein in:

   `<new_jboss>\bin\`

### Configuration Manager ausführen {#run-configuration-manager}

1. Starten Sie die aktualisierte JBoss-Umgebung.
1. LiveCycle Configuration Manager (LCM) starten.
1. Führen Sie den vollständigen End-to-End-Workflow von Configuration Manager aus.
1. Stellen Sie sicher, dass alle Konfigurationsaufgaben erfolgreich abgeschlossen wurden.

### Validierung nach einem Upgrade {#post-upgrade-validation}

Bestätigen Sie nach dem Upgrade Folgendes:

* Alle Services wurden gestartet.
* Die Datenbankkonnektivität ist verifiziert.
* Die Anwendungsfunktionalität wird validiert.
