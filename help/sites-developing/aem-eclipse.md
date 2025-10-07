---
title: AEM Developer Tools for Eclipse
description: Erfahren Sie mehr über die Entwickler-Tools von Adobe Experience Manager für Eclipse.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 00473769-c447-4966-a71e-117c669e0151
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 5bd621b14e3bcd21431c1df5629fe4669b14052c
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 47%

---


# AEM Developer Tools for Eclipse {#aem-developer-tools-for-eclipse}

![Experience Manager Developer Tools for Eclipse-Logo](assets/eclipse-logo.png)

## Überblick {#overview}

_Experience Manager Developer Tools for Eclipse_ ist ein Eclipse-Plug-in, das auf dem [Eclipse-Plug-in für Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) basiert und unter der Apache-Lizenz 2 veröffentlicht wurde.

Es bietet mehrere Funktionen, die die AEM-Entwicklung vereinfachen:

* Nahtlose Integration mit AEM-Instanzen über Eclipse Server Connector
* Synchronisierung für Inhalte und OSGI-Bundles
* Debugging-Unterstützung mit Code-Hot-Swapping-Funktion
* Einfacher Bootstrap von AEM-Projekten über einen speziellen Projekterstellungsassistenten
* Einfache Bearbeitung von JCR-Eigenschaften

## Voraussetzungen {#requirements}

Bevor Sie die AEM Developer Tools verwenden, müssen Sie Folgendes tun:

* Herunterladen und Installieren von [Eclipse IDE for Enterprise Java and Web Developers.](https://www.eclipse.org/downloads/packages/)
   * Die Version 1.4.0 von AEM Developer Tools for Eclipse ist mit Eclipse 2022-12 (4.26) oder höher kompatibel und erfordert die Ausführung von Java 17 oder höher.
* Konfigurieren Sie Ihre Eclipse-Installation, um sicherzustellen, dass Sie mindestens 1 GB Heap-Speicher haben, indem Sie Ihre `eclipse.ini` Konfigurationsdatei bearbeiten, wie in den häufig gestellten Fragen zu [&#x200B; beschrieben](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F)

>[!NOTE]
>
>In macOS müssen Sie mit der rechten Maustaste auf **Eclipse.app** klicken und dann **Paketinhalt anzeigen** auswählen, um Ihre `eclipse.ini` zu finden.

## Installieren der AEM Developer Tools for Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Wenn Sie die oben genannten [Anforderungen](#requirements) erfüllt haben, können Sie das Plug-in für Entwickler-Tools wie folgt installieren:

1. Durchsuchen Sie die [AEM Developer Tools-Website](https://eclipse.adobe.com/).

1. Kopieren Sie den **Installations-Link**.

   * Alternativ können Sie ein Archiv herunterladen, anstatt den Installations-Link zu verwenden.
   * Diese Methode ermöglicht eine Offline-Installation, Sie erhalten jedoch keine automatischen Aktualisierungsbenachrichtigungen.

1. Öffnen Sie in Eclipse das Menü **Hilfe**.
1. Klicken Sie auf **Neue Software installieren**.
1. Klicken Sie auf **Hinzufügen...**.
1. In das Feld **Name** geben Sie `AEM Developer Tools` ein.
1. Kopieren Sie in das Feld **Speicherort** die Installations-URL.
1. Klicken Sie auf **Hinzufügen**.
1. Prüfen Sie die beiden Plug-ins für **AEM** und **Sling**.
1. Klicken Sie auf **Weiter**.
1. Überprüfen Sie im Fenster **Installationsdetails** die zu installierenden Elemente und klicken Sie erneut **Weiter**.
1. Akzeptieren Sie die Lizenzvereinbarungen und klicken Sie auf **Beenden**.
1. Wählen Sie **angezeigten Dialogfeld** Trust Authorities“ die `https://eclipse.adobe.com` Behörde/Site aus und klicken Sie auf **Trust Selected**.
1. Wählen Sie im **Trust Artifacts** angezeigten Dialogfeld die Code-Unterzeichner aus und klicken Sie auf **Trust Selected**.
1. Klicken Sie auf **Jetzt neu starten**, um Eclipse neu zu starten.

## Die AEM-Perspektive {#the-aem-perspective}

In Eclipse bestimmt **Perspektive** die innerhalb eines Fensters verfügbaren Aktionen und Ansichten und ermöglicht eine aufgabenorientierte Interaktion mit Ressourcen in Eclipse. Weitere Informationen zu Perspektiven finden Sie in der [Eclipse-Dokumentation.](https://help.eclipse.org/latest/index.jsp).

Die _Experience Manager-Entwicklungs-Tools für Eclipse_ bieten eine AEM-Perspektive, die Ihnen volle Kontrolle über Ihre AEM-Projekte und -Instanzen bietet. So öffnen Sie die AEM-Perspektive:

1. Wählen Sie in der Eclipse-Menüleiste **Fenster** > **Perspektive** > **Perspektive öffnen** > **Andere** aus.
1. Wählen Sie im Dialogfeld **AEM** aus und klicken Sie auf **Öffnen**.

![Die AEM-Perspektive in Eclipse](assets/eclipse-aem-perspective.png)

## Multi-Modul-Beispielprojekt {#sample-multi-module-project}

Die _Experience Manager Developer Tools for Eclipse_ enthalten ein Beispielprojekt mit mehreren Modulen, das Ihnen den Einstieg in das Projekt-Setup von Eclipse erleichtert. Es dient auch als Best-Practice-Leitfaden für mehrere AEM-Funktionen, die den [AEM-Projektarchetyp nutzen.](https://github.com/adobe/aem-project-archetype)

Führen Sie die folgenden Schritte aus, um das Beispielprojekt zu erstellen:

1. Suchen Sie im Menü **Datei** > **Neu** > **Projekt** den Abschnitt **AEM** und wählen Sie **AEM-Multi-Modul-Beispielprojekt**.

   ![AEM-Multi-Modul-Beispielprojekt](assets/aem-sample-project.png)

1. Klicken Sie auf **Weiter**.

   >[!NOTE]
   >
   >Dieser Schritt kann einen Moment dauern, da [m2eclipse](https://eclipse.dev/m2e/) die Archetypkataloge scannen muss.

1. `com.adobe.aem : aem-project-archetype : <highest-number>` sollte automatisch in der Dropdown-Liste **Archetyp** ausgewählt werden. Wählen Sie bei Bedarf eine frühere Version aus. Klicken Sie auf **Weiter**.

   ![Auswählen der Archetypversion &#x200B;](assets/select-archetype.png)

1. Geben Sie in die folgenden Felder Daten für das Beispielprojekt ein:

   * **Name**
   * **Gruppen-ID**
   * **Artefakt-ID**
   * **appID** – Sie müssen die Optionen unter **Erweitert** erweitern, um diesen Wert festzulegen.
   * **appTitle** – Sie müssen ggf. die Optionen unter **Erweitert** erweitern, um diesen Wert festzulegen.
   * **Package** – Sie müssen die Optionen unter **Erweitert** erweitern, um diesen Wert festzulegen.

   ![Definieren von Archetypeigenschaften](assets/archetype-properties.png)

1. Klicken Sie auf **Weiter**.

1. Konfigurieren Sie einen AEM-Server, mit dem sich Eclipse verbindet, indem Sie **Neuen Server einrichten** auswählen und einen Servernamen und die erforderlichen Verbindungsdetails angeben.

   ![Herstellen einer Verbindung zum AEM-Server](assets/connect-server.png)

   * Um die Debugger-Funktion verwenden zu können, müssen Sie AEM im Debugging-Modus starten, indem Sie den `-agentlib` angeben, z. B.:

   ```text
   $ java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 -jar aem-author-p4502.jar
   ```

   >[!TIP]
   >
   >Weitere Informationen zum Debugging Ihres auf einer lokalen AEM-SDK ausgeführten Projekts finden Sie im Dokument [Remote-Debugging der AEM-SDK.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-sdk/remote-debugging)

1. Klicken Sie auf **Beenden**.

Die Projektstruktur wird erstellt. Es kann einen Moment dauern, bis die erforderlichen Artefakte zum Projekt heruntergeladen sind.

>[!NOTE]
>
>Bei einer Neuinstallation oder wenn die Maven-Abhängigkeiten noch nicht heruntergeladen wurden, meldet Eclipse möglicherweise, dass das Projekt mit Fehlern erstellt wurde. Folgen Sie in diesem Fall den Anweisungen im Abschnitt [Beheben einer ungültigen Projektdefinition.](#resolving-invalid-project-definition)

## Importieren vorhandener Projekte {#how-to-import-existing-projects}

Verwenden Sie die Funktion **Neues Projekt**, um die grundlegende Projektstruktur zu erstellen.

1. Befolgen Sie die Anweisungen, um ein [Multi-Modul-Beispielprojekt“ zu erstellen](#sample-multi-module-project) das eine grundlegende Projektstruktur mit einer sinnvollen Trennung der Belange erstellt:

   * `PROJECT.ui.apps` für `/apps`- und `/etc`-Inhalte
   * `PROJECT.ui.content` für `/content`, der erstellt wird
   * `PROJECT.core` für Java-Bundles
   * `PROJECT.it.launcher` und `PROJECT.it.tests` für Integrationstests

1. Ersetzen Sie den Inhalt Ihres `PROJECT.ui.apps`-Projekts durch die Ordner `apps` und `etc` Ihres Pakets:

   1. Erweitern Sie im **Projekt** Explorer-Bedienfeld `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Klicken Sie mit der rechten Maustaste auf den Ordner `apps` und wählen Sie **Anzeigen in** > **System-Explorer** aus.
   1. Löschen Sie die `apps` und `etc` dort.
   1. Platzieren Sie die `apps` und `etc` Ordner Ihres Inhaltspakets am selben Speicherort.
   1. Klicken Sie in Eclipse mit der rechten Maustaste auf das Projekt `PROJECT.ui.apps` und wählen Sie **Aktualisieren** aus.

1. Führen Sie dann dasselbe für `PROJECT.ui.content` aus und ersetzen Sie den Inhaltsordner durch den Ordner aus Ihren Paketen:

   1. Erweitern Sie im **Projekt** Explorer-Bedienfeld `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Klicken Sie mit der rechten Maustaste auf den unteren Inhaltsordner und wählen Sie **Anzeigen in** > **System-Explorer** aus.
   1. Löschen Sie den Inhaltsordner dort.
   1. Platzieren Sie den Inhaltsordner Ihres Inhaltspakets am selben Speicherort.
   1. Klicken Sie in Eclipse mit der rechten Maustaste auf das Projekt `PROJECT.ui.content` und wählen Sie **Aktualisieren** aus.

1. Aktualisieren Sie die `filter.xml` dieser beiden Projekte entsprechend dem Inhalt Ihres Inhaltspakets, indem Sie die `META-INF/vault/filter.xml` Datei Ihres Inhaltspakets in einem separaten Text-/Code-Editor öffnen.

   * Dies ist ein Beispiel dafür, wie Ihre Datei `filter.xml`aussehen kann:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       <filter root="/apps/foo"/>
       <filter root="/apps/foundation/components/bar"/>
       <filter root="/etc/designs/foo"/>
       <filter root="/content/foo"/>
       <filter root="/content/dam/foo"/>
       <filter root="/content/usergenerated/content/foo"/>
   </workspaceFilter>
   ```

1. Für den Inhalt Ihres Pakets, der in zwei Projekte aufgeteilt wurde, müssen Sie diese Filterregeln ebenfalls in zwei Teile aufteilen und die `filter.xml` der beiden Projekte entsprechend aktualisieren.

   1. Öffnen Sie in Eclipse `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. Ersetzen Sie den Inhalt des `<workspaceFilter>`-Elements durch die Regeln Ihres Pakets, die mit `/apps` und `/etc` beginnen.
      * Zum Beispiel:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/apps/foo"/>
           <filter root="/apps/foundation/components/bar"/>
           <filter root="/etc/designs/foo"/>
        </workspaceFilter>
        ```

   1. Öffnen Sie dann `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. Ersetzen Sie die Regeln durch die Ihres Pakets, die mit `/content` beginnen.
      * Zum Beispiel:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/content/foo"/>
           <filter root="/content/dam/foo"/>
           <filter root="/content/usergenerated/content/foo"/>
        </workspaceFilter>
        ```

1. Denken Sie daran, alle Änderungen zu speichern. Sie können diesen neuen Inhalt jetzt mit Ihrer AEM-Instanz synchronisieren.

1. Vergewissern Sie **Bedienfeld** Server“, dass Ihre Verbindung gestartet wurde. Falls nicht, starten Sie sie.

1. Klicken Sie auf das Symbol **Bereinigen und veröffentlichen**.

Danach sollte Ihr Paket auf Ihrer Instanz ausgeführt werden. Beim Speichern werden alle Änderungen automatisch mit der Instanz synchronisiert.

Wenn Sie ein Paket aus Ihrem Projekt neu erstellen möchten, klicken Sie mit der rechten Maustaste auf `PROJECT.ui.apps` oder `PROJECT.ui.content` und wählen Sie **Ausführen als** > **Maven-Installation** aus.

Jetzt verfügen Sie über einen Zielordner, der Ihr Paket enthält (z. B. mit dem Namen `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Fehlerbehebung {#troubleshooting}

### Ungültige Projektdefinition beheben {#resolving-invalid-project-definition}

Um ungültige Abhängigkeiten und Projektdefinitionen aufzulösen, gehen Sie wie folgt vor:

1. Wählen Sie alle erstellten Projekte.
1. Klicken Sie mit der rechten Maustaste.
1. Wählen Sie im Kontextmenü **Maven** > **Projekte aktualisieren** aus.
1. Aktivieren Sie **Aktualisierungen von Snapshots/Releases erzwingen**.
1. Klicken Sie auf **OK**.

Eclipse lädt die erforderlichen Abhängigkeiten herunter. Das kann einen Moment dauern.

## Weitere Informationen {#more-information}

Die offizielle Website Apache Sling IDE tooling for Eclipse bietet nützliche zusätzliche Informationen:

* Das [**Benutzerhandbuch zu Apache Sling IDE-Tooling** Eclipse](https://sling.apache.org/documentation/development/ide-tooling.html) führt Sie durch die allgemeinen Konzepte, die Server-Integration und die von den AEM-Entwicklungs-Tools unterstützten Bereitstellungsfunktionen.
* [Fehlerbehebung für Apache Sling-IDE-Tools](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting)
* [Liste der bekannten Probleme](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues)

Die folgende offizielle [Eclipse](https://www.eclipse.org/)-Dokumentation kann dabei helfen, Ihre Umgebung einzurichten:

* [Erste Schritte mit Eclipse](https://eclipseide.org/getting-started/)
* [Eclipse Luna-Hilfesystem](https://help.eclipse.org/latest/index.jsp)
* [Maven-Integration (m2eclipse)](https://www.eclipse.org/m2e/)
