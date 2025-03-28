---
title: Beheben von Schwachstellen im Spring Framework für AEM Forms on JEE
description: Beheben von Schwachstellen im Spring Framework für AEM Forms on JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 61cce7cd8290156bec6dcc351a59093f545a4ec7
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 2%

---


# Beheben von Schwachstellen im Spring Framework für AEM Forms on JEE

Dieses Dokument enthält Anleitungen zum Beheben von zwei kritischen Spring Framework-Schwachstellen, die AEM Forms on JEE betreffen:

- **[CVE-2024-38819](https://spring.io/security/cve-2024-38819)**: Schwachstelle beim Durchlaufen von Pfaden in funktionalen Web-Frameworks
- **[CVE-2024-38820](https://spring.io/security/cve-2024-38820)**: Spring Framework DataBinder Ausnahme bei Übereinstimmung unter Berücksichtigung von Groß-/Kleinschreibung

## Betroffene Versionen

- Adobe Experience Manager 6.5 Forms on JEE
- Versionen AEM 6.5 Forms GA bis 6.5.22.0

## Auflösung

### Versionsspezifische Lösungen

| AEM Forms-Version | Erforderliche Aktion |
|-------------------|-----------------|
| 6.5.22.0 | 1. [Laden Sie den Hotfix für Ihre Umgebung herunter](/help/release-notes/aem-forms-hotfix.md). </br> 2. Um diesen Fix zu installieren, folgen Sie den Anweisungen unter [Installieren des Service Packs auf einem AEM Form on JEE](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). |
| 6.5.17.0 – 6.5.21.0 | [Anwenden manueller Schritte zur Risikominderung](#manual-mitigation-steps). |
| 6,5 - 6.5.16.0 | 1. [Installieren Sie das neueste Service Pack.](/help/release-notes/release-notes.md)<br>. [Implementieren Sie basierend ](#version-specific-solutions) Ihrer aktualisierten Version die entsprechende Lösung. |

> **Hinweis**: AEM Forms unterstützt offiziell nur die sechs neuesten Service Packs. Benutzer älterer Versionen sollten zunächst ein Upgrade auf das neueste Service Pack durchführen und dann den erforderlichen Hotfix installieren.

## Überlegungen zur Bereitstellung

### Für Cluster-Umgebungen

Beim Arbeiten mit einer Clusterbereitstellung:

- Anwenden von JAR-Dateiersetzungen (Schritt #4) auf **alle Knoten** im Cluster
- Gewährleistung der Konsistenz durch Verwendung identischer JAR-Versionen auf allen Servern
- Aktualisierungen auf allen Knoten abschließen, bevor ein Service-Neustart gestartet wird
- Koordinierte Neustart-Strategie implementieren, um Systemausfallzeiten zu minimieren

### Für Umgebungen mit einem Knoten

Bei der Arbeit mit einer eigenständigen Bereitstellung:

- Vereinfachtes Verfahren, da keine zu verwaltenden Locator-Server vorhanden sind
- Auslassen aller Schritte im Zusammenhang mit der Konfiguration oder dem Start des Locator-Servers
- Führen Sie alle anderen angegebenen Schritte aus, insbesondere JAR-Ersetzungen und Manifest-Aktualisierungen.
- Starten Sie den Anwendungsserver neu, nachdem Sie alle Änderungen implementiert haben

## Manuelle Schritte zur Risikominderung

1. Beenden Sie die Anwendungs-Server.
1. Stopp- und Locator-Server.
1. Entfernen Sie Spring JARs aus Core EAR:
   1. Navigieren Sie zu `[Adobe_Experience_Manager_Forms installation directory]/deploy`.
   1. Öffnen Sie die `adobe-core-<appserver>.ear`-Datei mit einem Archivierungs-Manager-Tool. Dabei kann `<appserver>` je nach Umgebung JBoss, WebLogic oder WebSphere sein:
   - **Für JBoss**: Navigieren Sie zum `ear/lib` Ordner und löschen Sie die folgenden JAR-Dateien:
- `spring-core-<version>.jar`
- `spring-web-<version>.jar`

   - **Für WebLogic oder WebSphere** Löschen Sie die folgenden JAR-Dateien aus dem Stamm der EAR:
- `spring-core-<version>.jar`
- `spring-web-<version>.jar`

   - **Für alle Anwendungs-Server:** Öffnen Sie auf der Stammebene der `adobe-core-<appserver>.ear` die `adobe-dscf.jar`-Datei und bearbeiten Sie die `META-INF/MANIFEST.MF`-Datei, um alle Verweise auf die folgenden JAR-Dateien zu entfernen:
- `spring-core-<version>.jar`
- `spring-web-<version>.jar`

1. Ersetzen Sie JAR-Dateien aus der Geode-Verteilung:
   1. Navigieren Sie zu `<Adobe_Experience_Manager_Forms>/lib/caching/lib`
   1. Ersetzen Sie die vorhandenen JAR-Dateien durch die aktualisierten Versionen:
   - `spring-context-<version>.jar` → `spring-context-6.1.14.jar`
   - `spring-beans-<version>.jar` → `spring-beans-6.1.14.jar`
   - `spring-core-<version>.jar` → `spring-core-6.1.14.jar`
   - `spring-jcl-<version>.jar` → `spring-jcl-6.1.14.jar`
   - `spring-web-<version>.jar` → `spring-web-6.1.14.jar`

   Um die neueren JAR-Dateien abzurufen, laden Sie die Datei „spring-6.1.14-jars.zip“ von [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/spring-6.1.14-jars.zip) herunter und extrahieren Sie die ZIP-Datei, um auf die aktualisierten JAR-Dateien des Spring-Frameworks zuzugreifen.

   1. Aktualisieren Sie die Dateien MANIFEST.MF in den folgenden JAR-Dateien:
   - `geode-server-all-<version>.jar`
   - `gfsh-dependencies.jar`

   Für jede JAR:
   - Öffnen Sie die JAR-Datei mit einem Archivierungs-Manager-Tool
   - Suchen und Extrahieren der `META-INF/MANIFEST.MF`
   - Bearbeiten der Datei MANIFEST.MF in einem Texteditor
   - Suchen Sie den Abschnitt „Class-Path“ und aktualisieren Sie alle Spring Framework-Verweise:
      - `spring-core-<version>.jar` in `spring-core-6.1.14.jar`
      - `spring-web-<version>.jar` in `spring-web-6.1.14.jar`
      - `spring-context-<version>.jar` in `spring-context-6.1.14.jar`
      - `spring-beans-<version>.jar` in `spring-beans-6.1.14.jar`
      - `spring-jcl-<version>.jar` in `spring-jcl-6.1.14.jar`
   - Speichern Sie die geänderte Datei MANIFEST.MF
   - Ersetzen Sie die ursprüngliche MANIFEST.MF in der JAR durch Ihre aktualisierte Version
   - Speichern der JAR-Datei

   1. Häufige Probleme, auf die Sie achten sollten:
      - Keine doppelten Einträge im Manifest sicherstellen
      - Ordnungsgemäße Zeilenenden beibehalten
      - Überprüfen, ob alle referenzierten JARs an den angegebenen Speicherorten vorhanden sind

   1. Überprüfungsschritte:
      - Überprüfen, ob das Manifest ordnungsgemäß aktualisiert wurde
      - Überprüfen, ob alle Federabhängigkeiten korrekt referenziert werden
      - Sicherstellen, dass keine alten Versionsverweise verbleiben
      - Testen der Anwendung, um sicherzustellen, dass keine Probleme beim Laden der Klasse auftreten

1. Führen Sie den Configuration Manager aus.

1. Neustarten von Servern:
   - Starten Sie die Locator-Server mit JDK 17
   - Starten Sie die Anwendungs-Server mit derselben JDK-Version (JDK 8 oder JDK 11), die zuvor verwendet wurde.
