---
title: AEM Developer Tools for Eclipse
seo-title: AEM Entwicklertools für Eclipse
description: AEM Entwicklertools für Eclipse
seo-description: 'null'
uuid: 566e49f2-6f28-4aa7-bfe0-b5f9675310bf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: a2ae76a8-50b0-4e43-b791-ad3be25b8582
exl-id: 00473769-c447-4966-a71e-117c669e0151
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 93%

---

# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![](do-not-localize/chlimage_1-9.png)

## Überblick {#overview}

AEM Developer Tools for Eclipse ist ein Eclipse-Plug-in, das auf dem [Eclipse-Plug-in für Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) basiert, das unter der Apache-Lizenz 2 veröffentlicht wurde.

Es bietet mehrere Funktionen, die die AEM-Entwicklung vereinfachen:

* Nahtlose Integration mit AEM-Instanzen über Eclipse Server Connector.
* Synchronisierung für Inhalte und OSGI-Pakete.
* Debugging-Unterstützung mit Code-Hot-Swapping-Funktion.
* Einfacher Bootstrap von AEM-Projekten über einen speziellen Projekterstellungsassistenten.
* Einfache Bearbeitung von JCR-Eigenschaften.

## Voraussetzungen {#requirements}

Bevor Sie die AEM Developer Tools verwenden, müssen Sie Folgendes tun:

* Downloaden und installieren Sie [Eclipse IDE für Java EE Entwickler](https://eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/lunar). AEM Entwicklertools unterstützen derzeit Eclipse Kepler oder höher

* Kann mit AEM Version 5.6.1 oder neuer verwendet werden
* Konfigurieren Sie Ihre Eclipse-Installation, um sicherzustellen, dass Sie mindestens 1 GB an Heap-Speicher haben, indem Sie Ihre Konfigurationsdatei `eclipse.ini` bearbeiten, wie in den [Eclipse-FAQ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F) beschrieben.

>[!NOTE]
>
>Unter Mac OS X müssen Sie mit der rechten Maustaste auf **Eclipse.app** klicken und dann **Paketinhalt anzeigen** auswählen, um Ihre `eclipse.ini`**zu finden.**

## So installieren Sie die AEM Developer Tools for Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Sobald Sie die oben genannten [Voraussetzungen](#requirements) erfüllt haben, können Sie das Plug-in wie folgt installieren:

1. Durchsuchen Sie die [**AEM** Developer Tools-Website](https://eclipse.adobe.com/aem/dev-tools/).

1. Kopieren Sie den **Installations-Link**.

   Beachten Sie, dass Sie alternativ ein Archiv herunterladen können, anstatt den Installations-Link zu verwenden. Dies ermöglicht Offlineinstallation, aber Sie werden auf diese Weise automatische Update-Benachrichtigungen verpassen.

1. Öffnen Sie in Eclipse das Menü **Hilfe**.
1. Klicken Sie auf **Neue Software installieren**.
1. Klicken Sie auf **Hinzufügen...**.
1. Unter **Namen** geben Sie „AEM Developer Tools“ ein.
1. Unter **Standort** kopieren Sie die Installations-URL.
1. Klicken Sie auf **OK**.
1. Überprüfen Sie **AEM**- und **Sling**-Plug-ins.
1. Klicken Sie auf **Weiter**.
1. Klicken Sie auf **Weiter**.
1. Akzeptieren Sie die Lizenzvereinbarungen und klicken Sie auf **Beenden**.
1. Klicken Sie auf **Ja**, um Eclipse neu zu starten.

## Anleitung zum Importieren vorhandener Projekte {#how-to-import-existing-projects}

>[!NOTE]
>
>Siehe [Arbeiten mit einem Bundle in Eclipse, wenn es von AEM](https://stackoverflow.com/questions/29699726/how-to-work-with-a-bundle-in-eclipse-when-it-was-downloaded-from-aem/29705407#29705407) heruntergeladen wurde.

## Die AEM-Perspektive {#the-aem-perspective}

Die AEM Development Tools for Eclipse enthalten eine Perspektive, die Ihnen die volle Kontrolle über Ihre AEM-Projekte und -Instanzen bietet.

![chlimage_1-2](assets/chlimage_1-2a.jpeg)

## Multi-Modul-Beispielprojekt {#sample-multi-module-project}

Die AEM Developer Tools for Eclipse werden mit einem Beispielprojekt mit mehreren Modulen geliefert, mit dem Sie schnell mit der Projektkonfiguration in Eclipse vertraut werden und das als Best Practice-Leitfaden für mehrere AEM-Funktionen dienen kann. [Erfahren Sie mehr über den Projektarchetyp](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

Führen Sie folgende Schritte aus, um das Beispielprojekt zu erstellen:

1. Im Menü **Datei** > **Neu** > **Projekt** navigieren Sie zum **AEM**-Bereich und wählen Sie **AEM Beispiel-Multi-Modul Projekt**.

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

1. Sie sollten dann einen AEM-Server konfigurieren, zu dem Eclipse eine Verbindung herstellen wird.

   Um das Debugger-Feature zu verwenden, müssen Sie AEM im Debug-Modus starten. Dies kann z. B. erreicht werden, indem Sie Folgendes zur Befehlszeile hinzufügen:

   ```
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![chlimage_1-73](assets/chlimage_1-73a.png)

1. Klicken Sie auf **Beenden**. Die Projektstruktur wird erstellt.

   >[!NOTE]
   >
   >Bei einer Neuinstallation (genauer gesagt: wenn die Abhängigkeiten von Maven noch nie heruntergeladen wurden) wird das Projekt möglicherweise mit Fehlern erstellt. In diesem Fall folgen Sie den Anweisungen unter [Ungültige Projektdefinition beheben](#resolving-invalid-project-definition).

## Fehlerbehebung {#troubleshooting}

### Ungültige Projektdefinition beheben {#resolving-invalid-project-definition}

Um ungültige Abhängigkeiten und Projektdefinitionen aufzulösen, gehen Sie wie folgt vor:

1. Wählen Sie alle erstellten Projekte.
1. Klicken Sie mit der rechten Maustaste. Im Menü **Maven** wählen Sie **Projekte aktualisieren**.
1. Aktivieren Sie **Aktualisierungen von Snapshots/Releases erzwingen**.
1. Klicken Sie auf **OK**. Eclipse versucht, die erforderlichen Abhängigkeiten herunterzuladen.

### Aktivieren der automatischen Vervollständigung von Tag-Bibliotheken in JSP-Dateien {#enabling-tag-library-autocompletion-in-jsp-files}

Die automatische Vervollständigung der Tag-Bibliothek funktioniert sofort, da die richtigen Abhängigkeiten zum Projekt hinzugefügt werden. Es gibt ein bekanntes Problem bei der Verwendung von AEM-UberJar, das die erforderlichen tld- und TagExtraInfo-Dateien nicht enthält.

Stellen Sie sicher, dass das org.apache.sling.scripting.jsp.taglib-Artefakt im Klassenpfad vor dem AEM-UberJar liegt, um es zu umgehen. Platzieren Sie für Maven-Projekte die folgende Abhängigkeit in der pom.xml vor dem UberJar.

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

* Das Handbuch zu [**Apache Sling IDE tooling for Eclipse**](https://sling.apache.org/documentation/development/ide-tooling.html) führt Sie durch die von den AEM-Entwicklungstools unterstützten Konzepte, Serverintegrationen und Implementierungsfunktionen.
* Der [Abschnitt zur Fehlerbehebung](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* Die [Liste der bekannten Probleme](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

Die folgende offizielle [Eclipse](https://eclipse.org/)-Dokumentation kann dabei helfen, Ihre Umgebung einzurichten:

* [Erste Schritte mit Eclipse](https://eclipse.org/users/)
* [Eclipse Luna-Hilfesystem](https://help.eclipse.org/luna/index.jsp)
* [Maven-Integration (m2eclipse)](https://www.eclipse.org/m2e/)
