---
title: AEM Developer Tools for Eclipse
seo-title: AEM Developer Tools for Eclipse
description: AEM Developer Tools for Eclipse
seo-description: null
uuid: 566e49f2-6f28-4aa7-bfe0-b5f9675310bf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: a2ae76a8-50b0-4e43-b791-ad3be25b8582
exl-id: 00473769-c447-4966-a71e-117c669e0151
source-git-commit: 71842228dd3cb1ce3b79728912e8333d25fccefc
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 48%

---

# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![](do-not-localize/chlimage_1-9.png)

## Übersicht {#overview}

&quot;AEM Developer Tools&quot;ist ein Eclipse-Plug-in, das auf dem [Eclipse-Plug-in für Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) veröffentlicht unter der Apache-Lizenz 2.

Es bietet mehrere Funktionen, die die AEM-Entwicklung vereinfachen:

* Nahtlose Integration mit AEM-Instanzen über Eclipse Server Connector.
* Synchronisierung für Inhalte und OSGI-Pakete.
* Debugging-Unterstützung mit Code-Hot-Swapping-Funktion.
* Einfacher Bootstrap von AEM über einen spezifischen Assistenten zur Projekterstellung.
* Einfache Bearbeitung von JCR-Eigenschaften.

## Voraussetzungen {#requirements}

Bevor Sie die AEM Developer Tools verwenden, gehen Sie wie folgt vor:

* Herunterladen und installieren [Eclipse IDE für Java™ EE-Entwickler](https://www.eclipse.org/downloads/packages/release/luna/r/eclipse-ide-java-ee-developers). AEM Developer Tools unterstützt derzeit Eclipse Kepler oder höher.

* Kann mit AEM Version 5.6.1 oder höher verwendet werden.
* Konfigurieren Sie Ihre Eclipse-Installation, um sicherzustellen, dass Sie mindestens 1 GB Heap-Speicher haben, indem Sie Ihre `eclipse.ini` Konfigurationsdatei wie im Abschnitt [Häufig gestellte Fragen zu Eclipse](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F).

>[!NOTE]
>
>Klicken Sie in macOS mit der rechten Maustaste auf **Eclipse.app** und wählen Sie **Paketinhalt anzeigen** um `eclipse.ini`.

## So installieren Sie die AEM Developer Tools for Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Sobald Sie die oben genannten [Voraussetzungen](#requirements) erfüllt haben, können Sie das Plug-in wie folgt installieren:

1. Durchsuchen Sie die **AEM Developer Tools** Website unter `https://eclipse.adobe.com/aem/dev-tools/`.

1. Kopieren Sie den **Installations-Link**.

   Alternativ können Sie ein Archiv herunterladen, anstatt den Installationslink zu verwenden. Dies ermöglicht eine Offline-Installation, aber Sie verpassen automatische Aktualisierungsbenachrichtigungen.

1. Öffnen Sie in Eclipse die **Hilfe** Menü.
1. Klicken **Neue Software installieren**.
1. Klicken Sie auf **Hinzufügen...**.
1. In **Name** Geben Sie AEM Entwicklertools ein.
1. Unter **Standort** kopieren Sie die Installations-URL.
1. Klicken Sie auf **OK**.
1. Überprüfen Sie beide **AEM** und **Sling** Plug-ins.
1. Klicken Sie auf **Weiter**.
1. Klicken Sie auf **Weiter**.
1. Akzeptieren Sie die Lizenzvereinbarungen und klicken Sie auf **Beenden**.
1. Klicken **Ja** um Eclipse neu zu starten.

## Anleitung zum Importieren vorhandener Projekte {#how-to-import-existing-projects}

>[!NOTE]
>
>Siehe [So arbeiten Sie mit einem Bundle in Eclipse, wenn es von AEM heruntergeladen wurde](https://stackoverflow.com/questions/29699726/how-to-work-with-a-bundle-in-eclipse-when-it-was-downloaded-from-aem/29705407#29705407).

## Die AEM-Perspektive {#the-aem-perspective}

Die AEM Entwicklungs-Tools für Eclipse verfügen über eine Perspektive, die Ihnen die volle Kontrolle über Ihre AEM Projekte und Instanzen bietet.

![chlimage_1-2](assets/chlimage_1-2a.jpeg)

## Multi-Modul-Beispielprojekt {#sample-multi-module-project}

&quot;AEM Developer Tools&quot;enthalten ein Beispielprojekt mit mehreren Modulen, mit dem Sie sich schnell mit der Projekteinrichtung in Eclipse vertraut machen können. Es dient auch als Best-Practice-Leitfaden für verschiedene AEM Funktionen. [Erfahren Sie mehr über den Projektarchetyp](https://github.com/adobe/aem-project-archetype).

Führen Sie die folgenden Schritte aus, um das Beispielprojekt zu erstellen:

1. Im **Datei** > **Neu** > **Projekt** Menü, navigieren Sie zum **AEM** und wählen Sie **AEM Beispiel für ein Projekt mit mehreren Modulen**.

   ![chlimage_1-69](assets/chlimage_1-69a.png)

1. Klicken Sie auf **Weiter**.

   >[!NOTE]
   >
   >Dieser Schritt kann eine Weile dauern, da m2eclipse die Archetypkataloge scannen muss.

   ![chlimage_1-70](assets/chlimage_1-70a.png)

1. Wählen Sie **com.adobe.granite.archetypes: sample-project-archetype: (höchste Zahl)** aus dem Menü aus und klicken Sie auf **Weiter**.

   ![chlimage_1-71](assets/chlimage_1-71a.png)

1. Füllen Sie einen **Name**, **Gruppen-ID** und ein **Artefakt-ID** für das Beispielprojekt. Sie haben auch die Möglichkeit, mehrere erweiterte Eigenschaften festzulegen.

   ![chlimage_1-72](assets/chlimage_1-72a.png)

1. Konfigurieren Sie nun einen AEM Server, zu dem Eclipse eine Verbindung herstellen kann.

   Um die Debugger-Funktion zu verwenden, müssen Sie AEM Debugmodus starten. Dies kann durch Hinzufügen der folgenden Informationen zur Befehlszeile erreicht werden:

   ```
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![chlimage_1-73](assets/chlimage_1-73a.png)

1. Klicken Sie auf **Beenden**. Die Projektstruktur wird erstellt.

   >[!NOTE]
   >
   >Bei einer Neuinstallation (genauer gesagt: wenn die Abhängigkeiten von Maven noch nie heruntergeladen wurden) wird das Projekt möglicherweise mit Fehlern erstellt. Gehen Sie in diesem Fall wie folgt vor: [Beheben einer ungültigen Projektdefinition](#resolving-invalid-project-definition).

## Fehlerbehebung {#troubleshooting}

### Ungültige Projektdefinition beheben {#resolving-invalid-project-definition}

Um ungültige Abhängigkeiten und Projektdefinitionen aufzulösen, gehen Sie wie folgt vor:

1. Wählen Sie alle erstellten Projekte.
1. Klicken Sie mit der rechten Maustaste. Im Menü **Maven** auswählen **Projekte aktualisieren**.
1. Aktivieren Sie **Aktualisierungen von Snapshots/Releases erzwingen**.
1. Klicken Sie auf **OK**. Eclipse versucht, die erforderlichen Abhängigkeiten herunterzuladen.

### Automatische Vervollständigung von Tag-Bibliotheken in JSP-Dateien aktivieren {#enabling-tag-library-autocompletion-in-jsp-files}

Die automatische Vervollständigung der Tag-Bibliothek funktioniert sofort, da die richtigen Abhängigkeiten zum Projekt hinzugefügt werden. Es gibt ein bekanntes Problem bei der Verwendung des AEM Uber Jar, das nicht die erforderlichen tld- und TagExtraInfo-Dateien enthält.

Um dies zu umgehen, stellen Sie sicher, dass sich das Artefakt org.apache.sling.scripting.jsp.taglib im Klassenpfad vor dem AEM Uber Jar befindet. Platzieren Sie für Maven-Projekte die folgende Abhängigkeit in der pom.xml vor dem UberJar.

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

* Die [**Apache Sling IDE-Tools für Eclipse** Benutzerhandbuch](https://sling.apache.org/documentation/development/ide-tooling.html)enthält, führt Sie diese Dokumentation durch die allgemeinen Konzepte, Serverintegration und Bereitstellungsfunktionen, die von den AEM Entwicklungs-Tools unterstützt werden.
* Der [Abschnitt zur Fehlerbehebung](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* Die [Liste der bekannten Probleme](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

Die folgende offizielle [Eclipse](https://www.eclipse.org/)-Dokumentation kann dabei helfen, Ihre Umgebung einzurichten:

* [Erste Schritte mit Eclipse](https://www.eclipse.org/getting-started/)
* [Eclipse Luna-Hilfesystem](https://help.eclipse.org/latest/index.jsp)
* [Maven-Integration (m2eclipse)](https://www.eclipse.org/m2e/)
