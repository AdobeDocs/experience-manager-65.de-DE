---
title: Richten Sie das Android-Studioprojekt ein und erstellen Sie eine Android-App
seo-title: Richten Sie das Android-Studioprojekt ein und erstellen Sie eine Android-App
description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen des Installationsprogramms für die AEM Forms-App
seo-description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen des Installationsprogramms für die AEM Forms-App
uuid: 4c966cdc-d0f5-4b5b-b21f-f11e8a35ec8a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: forms-app
discoiquuid: fabc981e-0c9e-4157-b0a1-0c13717fb6cd
translation-type: tm+mt
source-git-commit: 4a0f3f64095b4726f295a0c1857a1e999353f5f5

---


# Richten Sie das Android-Studioprojekt ein und erstellen Sie eine Android-App {#set-up-the-android-studio-project-and-build-the-android-app}

Dieser Artikel gilt für das Erstellen der AEM Forms App 6.3.1.1 und höheren Versionen. For building an app from source code of source code of the AEM Forms App 6.3, see [Set up the Eclipse project and build the Android™ app](/help/forms/using/setup-eclipse-project-build-installer.md).

In AEM Forms wird der vollständige Quellcode der AEM Forms-App bereitgestellt. Die Quelle enthält alle Komponenten, die für eine benutzerdefinierte AEM Forms-App erforderlich sind. The source code archive, `adobe-lc-mobileworkspace-src-<version>.zip` is a part of the `adobe-aemfd-forms-app-src-pkg-<version>.zip` package on package share.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Zu Package Share navigieren

   URL: `https://<server>:<port>/crx/packageshare`.

1. Laden Sie das Quellpaket herunter. Wenn Sie das Paket herunterladen, wird es in Ihrem AEM Forms Package Manager hinzugefügt.
1. Nach dem Herunterladen navigieren Sie zu: und `https://<server>:<port>/crx/packmgr/index.jsp`installieren `adobe-aemfd-forms-app-src-pkg-<version>.zip`.

1. Um das Quellcode-Archiv herunterzuladen, öffnen Sie `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` den Browser.

   Das Quellpaket wird auf Ihr Gerät heruntergeladen.

The following image displays the extracted contents of the `adobe-lc-mobileworkspace-src-<version>.zip`.

![Extrahierter Inhalt der komprimierten Android™-Quelle](assets/mws-content-1.png)

The following image displays the directory structure of the `android`folder in the `src`folder.

![Ordnerstruktur des Android Ordner in src](assets/android-folder.png)

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

1. Führen Sie die folgenden Schritte aus, um ein Projekt in Android™ Studio einzurichten und eine Signing-Identität anzugeben:

   Melden Sie sich bei einem Computer an, auf dem Android™ Studio installiert und konfiguriert ist.

1. Copy the downloaded `adobe-lc-mobileworkspace-src-<version>.zip` archive to:

   **MAC-Benutzer**: `[User_Home]/Projects`

   **Für Windows®-Benutzer**: `%HOMEPATH%\Projects`

   >[!NOTE]
   >
   >Für Windows® wird empfohlen, das Android-Projekt auf dem Systemlaufwerk zu belassen.

1. Extrahieren Sie das Archiv im folgenden Verzeichnis:

   **MAC-Benutzer**: `[User_Home]/Projects/[your-project]`

   **Für Windows®-Benutzer**: `%HOMEPATH%\Projects\[your-project]`

   >[!NOTE]
   >
   >Es wird empfohlen, das extrahierte Android-Projekt auf dem Systemlaufwerk zu belassen, bevor Sie das Projekt in Android Studio importieren.

1. Starten Sie Android™ Studio.

   **MAC-Benutzer**: Aktualisieren Sie die `local.properties` Datei im `[User_Home]/Projects/[your-project]/android` Ordner und verweisen Sie mit der `sdk.dir` `SDK` Variablen auf den Speicherort auf Ihrem Desktop.

   **Für Windows®-Benutzer**: Aktualisieren Sie die `local.properties` Datei im `%HOMEPATH%\Projects\[your-project]\android` Ordner und verweisen Sie mit der `sdk.dir` `SDK` Variablen auf den Speicherort auf Ihrem Desktop.

1. Klicken Sie auf **[!UICONTROL Fertig stellen]**, um das Projekt zu erstellen.

   Das Projekt ist im ADT Project Explorer verfügbar.

   ![Eclipse-Projekt nach Erstellen der App](assets/eclipsebuildmws.png)

1. Wählen Sie in Android™ Studio **[!UICONTROL Projekt importieren (Eclipse ADT, Gradle, etc.)]**.
1. In the project explorer, select the root directory of the project that you want to build in the **Root Directory** text box:

   **** Mac-Benutzer: [Benutzerstammordner]/Projekte/MobileWorkspace/src/android

   **** Für Windows®-Nutzer: %HOMEPATH%\Projects\MobileWorkspace\src\android

1. Nachdem das Projekt importiert wurde, erscheint ein Popup mit der Option zum Aktualisieren des Android™ Plugin Gradle. Klicken Sie wie für Ihre Zwecke benötigt auf die entsprechende Schaltfläche.

   ![dontremindemagainrisproject](assets/dontremindmeagainforthisproject.png)

1. Nach dem erfolgreichen Erstellen des Gradle erscheint der folgende Bildschirm. Connect the appropriate device or emulator with the system and click **[!UICONTROL Run Android™]**.

   ![Gradleconsole](assets/gradleconsole.png)

1. Android™ Studio zeigt die verbundenen Geräte und verfügbaren Emulatoren an. Wählen Sie das Gerät, auf dem Sie die Anwendung ausführen wollen, und klicken Sie dann auf **OK**.

   ![connectionDevice](assets/connecteddevice.png)

Nachdem Sie das Projekt erstellt haben, haben Sie folgende Möglichkeiten zum Installieren der App mit Android™ Debug Bridge oder Android™ Studio:

### Mit Android™ Debug Bridge {#andriod-debug-bridge}

Sie können die Anwendung über [Android™ Debug Bridge](https://developer.android.com/tools/help/adb.html) mit folgendem Befehl auf einem Android™-Gerät installieren:

**MAC-Benutzer**: `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`

**Für Windows®-Benutzer**: `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)**
