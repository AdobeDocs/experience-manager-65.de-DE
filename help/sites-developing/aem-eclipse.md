---
title: AEM Developer Tools for Eclipse
description: Erfahren Sie mehr über die Entwicklertools von Adobe Experience Manager für Eclipse.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 00473769-c447-4966-a71e-117c669e0151
source-git-commit: b703f356f9475eeeafb1d5408c650d9c6971a804
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 98%

---

# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![Zirkuläres Bildmotiv für AEM-Entwickler-Tools für Eclipse.](do-not-localize/chlimage_1-9.png)

## Übersicht {#overview}

„AEM Developer Tools“ ist ein Eclipse-Plug-in, das auf dem [Eclipse-Plug-in für Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) basiert, das unter der Apache-Lizenz 2 veröffentlicht wurde.

Es bietet mehrere Funktionen, die die AEM-Entwicklung vereinfachen:

* Nahtlose Integration mit AEM-Instanzen über Eclipse Server Connector.
* Synchronisierung für Inhalte und OSGI-Pakete.
* Debugging-Unterstützung mit Code-Hot-Swapping-Funktion.
* Einfaches Bootstrap von AEM-Projekten über einen speziellen Projekterstellungsassistenten.
* Einfache Bearbeitung von JCR-Eigenschaften.

## Voraussetzungen {#requirements}

Bevor Sie die AEM Developer Tools verwenden, gehen Sie wie folgt vor:

* Laden Sie [Eclipse IDE for Java™ EE Developers](https://www.eclipse.org/downloads/packages/release/luna/r/eclipse-ide-java-ee-developers) herunter und installieren Sie es. AEM Developer Tools unterstützt derzeit Eclipse Kepler oder höher.

* Kann mit AEM Version 5.6.1 oder höher verwendet werden.
* Konfigurieren Sie Ihre Eclipse-Installation, um sicherzustellen, dass Sie mindestens 1 GB an Heap-Speicher haben, indem Sie Ihre Konfigurationsdatei `eclipse.ini` bearbeiten, wie in den [Eclipse-FAQ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F) beschrieben.

>[!NOTE]
>
>Klicken Sie unter macOS mit der rechten Maustaste auf **Eclipse.app** und wählen Sie **Paketinhalt anzeigen**, um Ihre `eclipse.ini` zu finden.

## So installieren Sie die AEM Developer Tools for Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Sobald Sie die oben genannten [Voraussetzungen](#requirements) erfüllt haben, können Sie das Plug-in wie folgt installieren:

1. Durchsuchen Sie die Website **AEM Developer Tools** unter `https://eclipse.adobe.com/aem/dev-tools/`.

1. Kopieren Sie den **Installations-Link**.

   Beachten Sie, dass Sie alternativ auch ein Archiv herunterladen können, anstatt den Installations-Link zu verwenden. Dies ermöglicht eine Offline-Installation, doch Ihnen entgehen die automatischen Aktualisierungsbenachrichtigungen.

1. Öffnen Sie in Eclipse das Menü **Hilfe**.
1. Klicken Sie auf **Neue Software installieren**.
1. Klicken Sie auf **Hinzufügen...**.
1. Geben Sie als **Namen** „AEM Developer Tools“ ein.
1. Unter **Standort** kopieren Sie die Installations-URL.
1. Klicken Sie auf **OK**.
1. Überprüfen Sie die beiden Plug-ins für **AEM** und **Sling**.
1. Klicken Sie auf **Weiter**.
1. Klicken Sie auf **Weiter**.
1. Akzeptieren Sie die Lizenzvereinbarungen und klicken Sie auf **Beenden**.
1. Klicken Sie auf **Ja**, um Eclipse neu zu starten.

## Anleitung zum Importieren vorhandener Projekte {#how-to-import-existing-projects}

>[!NOTE]
>
>Siehe [So arbeiten Sie mit einem Bundle in Eclipse, wenn es von AEM heruntergeladen wurde](https://stackoverflow.com/questions/29699726/how-to-work-with-a-bundle-in-eclipse-when-it-was-downloaded-from-aem/29705407#29705407).

## Die AEM-Perspektive {#the-aem-perspective}

AEM Development Tools for Eclipse enthält eine Perspektive, die Ihnen die volle Kontrolle über Ihre AEM-Projekte und -Instanzen bietet.

![chlimage_1-2](assets/chlimage_1-2a.jpeg)

## Multi-Modul-Beispielprojekt {#sample-multi-module-project}

AEM Developer Tools enthält ein Beispielprojekt mit mehreren Modulen, durch das Sie sich schnell mit der Projekteinrichtung in Eclipse vertraut machen können. Es dient auch als Best-Practice-Leitfaden für verschiedene AEM-Funktionen. [Erfahren Sie mehr über den Projektarchetyp](https://github.com/adobe/aem-project-archetype).

Führen Sie die folgenden Schritte aus, um das Beispielprojekt zu erstellen:

1. Gehen Sie im Menü **Datei** > **Neu** > **Projekt** zum Abschnitt **AEM** und wählen Sie **AEM-Multi-Modul-Beispielprojekt** aus.

   ![chlimage_1-69](assets/chlimage_1-69a.png)

1. Klicken Sie auf **Weiter**.

   >[!NOTE]
   >
   >Dieser Schritt kann einige Zeit in Anspruch nehmen, da m2eclipse die Archetypkataloge scannen muss.

   ![chlimage_1-70](assets/chlimage_1-70a.png)

1. Wählen Sie **com.adobe.granite.archetypes: sample-project-archetype: (höchste Zahl)** aus dem Menü aus und klicken Sie auf **Weiter**.

   ![chlimage_1-71](assets/chlimage_1-71a.png)

1. Geben Sie einen **Namen**, eine **Gruppen-ID** und eine **Artefakt-ID** für das Beispielprojekt ein. Sie haben auch die Möglichkeit, mehrere erweiterte Eigenschaften festzulegen.

   ![chlimage_1-72](assets/chlimage_1-72a.png)

1. Konfigurieren Sie nun einen AEM-Server, zu dem Eclipse eine Verbindung herstellen kann.

   Um die Debugger-Funktion zu verwenden, müssen Sie AEM im Debug-Modus starten. Dies kann z. B. erreicht werden, indem Sie Folgendes zur Befehlszeile hinzufügen:

   ```
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![chlimage_1-73](assets/chlimage_1-73a.png)

1. Klicken Sie auf **Beenden**. Die Projektstruktur wird erstellt.

   >[!NOTE]
   >
   >Bei einer Neuinstallation (genauer gesagt: wenn die Abhängigkeiten von Maven noch nie heruntergeladen wurden) wird das Projekt möglicherweise mit Fehlern erstellt. Folgen Sie in diesem Fall den Anweisungen unter [Beheben einer ungültigen Projektdefinition](#resolving-invalid-project-definition).

## Fehlerbehebung {#troubleshooting}

### Ungültige Projektdefinition beheben {#resolving-invalid-project-definition}

Um ungültige Abhängigkeiten und Projektdefinitionen aufzulösen, gehen Sie wie folgt vor:

1. Wählen Sie alle erstellten Projekte.
1. Klicken Sie mit der rechten Maustaste. Wählen Sie im Menü **Maven** die Option **Projekte aktualisieren** aus.
1. Aktivieren Sie **Aktualisierungen von Snapshots/Releases erzwingen**.
1. Klicken Sie auf **OK**. Eclipse versucht, die erforderlichen Abhängigkeiten herunterzuladen.

### Aktivieren der automatischen Vervollständigung von Tag-Bibliotheken in JSP-Dateien {#enabling-tag-library-autocompletion-in-jsp-files}

Die automatische Vervollständigung der Tag-Bibliothek funktioniert sofort, da die richtigen Abhängigkeiten zum Projekt hinzugefügt werden. Es gibt ein bekanntes Problem bei der Verwendung von AEM Uber Jar, das nicht die erforderlichen tld- und TagExtraInfo-Dateien enthält.

Stellen Sie sicher, dass das Artefakt org.apache.sling.scripting.jsp.taglib im Klassenpfad vor AEM Uber Jar liegt, um das Problem zu umgehen. Platzieren Sie für Maven-Projekte die folgende Abhängigkeit in der pom.xml vor dem UberJar.

```xml
<dependency>
  <groupId>org.apache.sling</groupId>
  <artifactId>org.apache.sling.scripting.jsp.taglib</artifactId>
  <scope>provided</scope>
</dependency>
```

Stellen Sie sicher, dass Sie die korrekte Version für Ihre Bereitstellung von AEM hinzuzufügen.

## Weitere Informationen {#more-information}

Die offizielle Website „Apache Sling IDE tooling for Eclipse“ bietet Ihnen nützliche Informationen:

* Das Benutzerhandbuch](https://sling.apache.org/documentation/development/ide-tooling.html) zu [**Apache Sling IDE-Tooling für Eclipse** führt Sie durch die allgemeinen Konzepte, Server-Integrationen und Bereitstellungsfunktionen, die von AEM Developer Tools unterstützt werden.
* Der [Abschnitt zur Fehlerbehebung](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* Die [Liste der bekannten Probleme](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

Die folgende offizielle [Eclipse](https://www.eclipse.org/)-Dokumentation kann dabei helfen, Ihre Umgebung einzurichten:

* [Erste Schritte mit Eclipse](https://eclipseide.org/getting-started/)
* [Eclipse Luna-Hilfesystem](https://help.eclipse.org/latest/index.jsp)
* [Maven-Integration (m2eclipse)](https://www.eclipse.org/m2e/)
