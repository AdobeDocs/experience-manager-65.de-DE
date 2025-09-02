---
title: Beheben von Sicherheitslücken im Spring Framework für AEM Forms auf JEE
description: Beheben von Sicherheitslücken im Spring Framework für AEM Forms auf JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: f704b58a-7bd8-401e-8d7e-2cc3b580c570
source-git-commit: d2ae4817720cae92b038789804124e0c2465f9c8
workflow-type: ht
source-wordcount: '563'
ht-degree: 100%

---

# Beheben von Spring Framework-Schwachstellen für AEM Forms on JEE

Dieses Dokument enthält Anweisungen zum Beheben von zwei kritischen Sicherheitslücken im Spring Framework, die sich auf AEM Forms auf JEE auswirken:

- **[CVE-2024-38819](https://spring.io/security/cve-2024-38819)**: Sicherheitslücke beim Durchlaufen von Pfaden in funktionalen Web-Frameworks
- **[CVE-2024-38820](https://spring.io/security/cve-2024-38820)**: Spring Framework DataBinder – Ausnahme bei Übereinstimmung unter Berücksichtigung von Groß-/Kleinschreibung

## Betroffene Versionen

- Adobe Experience Manager 6.5 Forms auf JEE
- Versionen AEM 6.5 Forms GA bis 6.5.22.0

## Auflösung

### Versionsspezifische Lösungen

| AEM Forms-Version | Erforderliche Aktion |
|-------------------|-----------------|
| 6.5.22.0 | &#x200B;1. [Laden Sie den Hotfix für Ihre Umgebung herunter](/help/release-notes/aem-forms-hotfix.md). </br> 2. Um diesen Fix zu installieren, folgen Sie den Anweisungen unter [Installieren des Service Packs auf AEM Forms auf JEE](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). |
| 6.5.17.0–6.5.21.0 | [Verwenden Sie manuelle Abhilfemaßnahmen](#manual-mitigation-steps). |
| 6,5 – 6.5.16.0 | &#x200B;1. [Installieren Sie das neueste Service Pack](/help/release-notes/release-notes.md)<br>2. [Implementieren Sie die geeignete Lösung](#version-specific-solutions) basierend auf Ihrer aktualisierten Version. |

> **Hinweis**: AEM Forms unterstützt offiziell nur die sechs neuesten Service Packs. Wer ältere Versionen benutzt, sollte zunächst ein Upgrade auf das neueste Service Pack durchführen und dann den erforderlichen Hotfix implementieren.

## Überlegungen zur Bereitstellung

### Für geclusterte Umgebungen

Beim Arbeiten mit einer geclusterten Bereitstellung:

- Wenden Sie JAR-Dateiersetzungen (Schritt 4) auf **alle Knoten** im Cluster an
- Gewährleisten Sie die Konsistenz durch Verwendung identischer JAR-Versionen auf allen Servern
- Schließen Sie die Aktualisierungen auf allen Knoten ab, bevor ein Service-Neustart gestartet wird
- Implementieren Sie eine Strategie der koordinierten Neustarts, um Systemausfallzeiten zu minimieren

### Für Umgebungen mit einem Knoten

Bei der Arbeit mit einer eigenständigen Bereitstellung:

- Folgen Sie einem vereinfachten Verfahren, da keine zu verwaltenden Locator-Server vorhanden sind
- Lassen Sie alle Schritte im Zusammenhang mit der Konfiguration oder dem Start von Locator-Servern aus
- Führen Sie alle anderen angegebenen Schritte aus, insbesondere JAR-Ersetzungen und Manifest-Aktualisierungen.
- Starten Sie den Anwendungs-Server neu, nachdem Sie alle Änderungen implementiert haben

## Manuelle Schritte zur Risikominderung

1. Stoppen Sie die Anwendungs-Server.
1. Stoppen Sie alle Locator-Server.
1. So entfernen Sie Spring JARs aus Core EAR:
   1. Navigieren Sie zu `[Adobe_Experience_Manager_Forms installation directory]/deploy`.
   1. Öffnen Sie die Datei `adobe-core-<appserver>.ear` mit einem Archivierungs-Manager-Tool. Dabei kann `<appserver>` je nach Umgebung JBoss, WebLogic oder WebSphere sein:
   - **Für JBoss**: Navigieren Sie zum Ordner `ear/lib` und löschen Sie die folgenden JAR-Dateien:
– `spring-core-<version>.jar`
– `spring-web-<version>.jar`

   - **Für WebLogic oder WebSphere** Löschen Sie die folgenden JAR-Dateien aus dem Stamm der EAR:
– `spring-core-<version>.jar`
– `spring-web-<version>.jar`

   - **Für alle Anwendungs-Server:** Öffnen Sie auf der Stammebene von `adobe-core-<appserver>.ear` die Datei `adobe-dscf.jar` und bearbeiten Sie die Datei `META-INF/MANIFEST.MF`, um alle Verweise auf die folgenden JAR-Dateien zu entfernen:
– `spring-core-<version>.jar`
– `spring-web-<version>.jar`

1. So ersetzen Sie JAR-Dateien aus der Geode-Verteilung:
   1. Navigieren Sie zu `<Adobe_Experience_Manager_Forms>/lib/caching/lib`
   1. Ersetzen Sie die vorhandenen JAR-Dateien durch die aktualisierten Versionen:
   - `spring-context-<version>.jar` → `spring-context-6.1.14.jar`
   - `spring-beans-<version>.jar` → `spring-beans-6.1.14.jar`
   - `spring-core-<version>.jar` → `spring-core-6.1.14.jar`
   - `spring-jcl-<version>.jar` → `spring-jcl-6.1.14.jar`
   - `spring-web-<version>.jar` → `spring-web-6.1.14.jar`

   Um die neueren JAR-Dateien abzurufen, laden Sie die Datei „spring-6.1.14-jars.zip“ von der [Adobe-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/spring-6.1.14-jars.zip) herunter und extrahieren Sie die ZIP-Datei, um auf die aktualisierten JAR-Dateien des Spring-Frameworks zuzugreifen.

   1. Aktualisieren Sie die Dateien MANIFEST.MF in den folgenden JAR-Dateien:
   - `geode-server-all-<version>.jar`
   - `gfsh-dependencies.jar`

   Für jede JAR tun Sie Folgendes:
   - Öffnen Sie die JAR-Datei mit einem Archivierungs-Manager-Tool
   - Suchen und Extrahieren Sie die Datei `META-INF/MANIFEST.MF`
   - Öffnen Sie die Datei „MANIFEST.MF“ in einem Texteditor.
   - Suchen Sie den Abschnitt „Class-Path“ und aktualisieren Sie alle Spring Framework-Verweise:
      - `spring-core-<version>.jar` in `spring-core-6.1.14.jar`
      - `spring-web-<version>.jar` in `spring-web-6.1.14.jar`
      - `spring-context-<version>.jar` in `spring-context-6.1.14.jar`
      - `spring-beans-<version>.jar` in `spring-beans-6.1.14.jar`
      - `spring-jcl-<version>.jar` in `spring-jcl-6.1.14.jar`
   - Speichern Sie die resultierende Datei „MANIFEST.MF“
   - Ersetzen Sie die ursprüngliche Datei „MANIFEST.MF“ in der JAR durch Ihre aktualisierte Version
   - Speichern Sie die JAR-Datei.

   1. Häufige Probleme, auf die Sie achten sollten:
      - Stellen Sie sicher, dass keine doppelten Einträge im Manifest vorhanden sind
      - Behalten Sie ordnungsgemäße Zeilenenden bei
      - Überprüfen Sie, ob alle referenzierten JARs an den angegebenen Speicherorten vorhanden sind

   1. Überprüfungsschritte:
      - Überprüfen Sie, ob das Manifest ordnungsgemäß aktualisiert wurde
      - Überprüfen Sie, ob alle Federabhängigkeiten korrekt referenziert werden
      - Stellen Sie sicher, dass keine alten Versionsverweise verbleiben
      - Testen Sie die Anwendung, um sicherzustellen, dass keine Probleme beim Laden von Klassen auftreten

1. Führen Sie den Konfigurations-Manager aus. 

1. Starten Sie die Server neu:
   - Starten Sie die Locator-Server mit JDK 17
   - Starten Sie die Anwendungs-Server mit derselben JDK-Version (JDK 8 oder JDK 11), die zuvor verwendet wurde.
