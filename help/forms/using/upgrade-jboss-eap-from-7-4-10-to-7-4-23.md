---
title: Upgrade von JBoss EAP von 7.4.10 auf 7.4.23 für AEM Forms on JEE
description: Schritte zum Upgrade von JBoss EAP von 7.4.10 auf 7.4.23 für eigenständige Umgebungen in AEM Forms on JEE.
SEO Description: Upgrade JBoss EAP from 7.4.10 to 7.4.23 for AEM Forms on JEE standalone environments.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
exl-id: 8f4c2a91-6b3d-4e7f-9c12-5d8e1f0a2b34
solution: Experience Manager, Experience Manager Forms
feature: AEM Forms Upgrade,AEM Forms on JEE
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 94663796-0ee7-58b9-84f4-b425ebb69e83
    internal-label: AEM Forms on JEE
  - id: d49d6117-dd89-469c-a774-cc96b7eee433
    internal-label: Administration
subfeature_v2:
  - id: b9cdd520-e7a7-4af9-a95f-296f28882b69
    internal-label: AEM Forms upgrade
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 2%
---
# Upgrade von JBoss EAP von 7.4.10 auf 7.4.23 für AEM Forms on JEE {#upgrade-jboss-eap-from-7-4-10-to-7-4-23}

## Überblick {#overview}

Aktualisieren von JBoss EAP von Version 7.4.10 auf 7.4.23 in einer eigenständigen Umgebung von AEM Forms on JEE. Für das Upgrade müssen Konfigurationsdateien, Datenbankanmeldeinformationen und das CRX-Repository in die neue JBoss-Installation migriert und Configuration Manager ausgeführt werden, um das Setup abzuschließen.

## Gilt für {#applies-to}

Dieser Artikel gilt für:

* AEM Forms on JEE, das unter JBoss EAP 7.4.10 in einer eigenständigen Umgebung ausgeführt wird
* Turnkey- und Teilinstallationsmodi unter Windows und Linux

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen:

* Laden Sie das JBoss 7.4.23-Paket vom [Adobe Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fjboss-eap-7.4.23-1.0.17.zip) herunter.
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
