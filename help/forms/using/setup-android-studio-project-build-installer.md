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
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 61%

---


# Richten Sie das Android-Studioprojekt ein und erstellen Sie eine Android-App {#set-up-the-android-studio-project-and-build-the-android-app}

Dieser Artikel gilt für das Erstellen der AEM Forms App 6.3.1.1 und höheren Versionen. Informationen zum Erstellen einer App aus dem Quellcode des AEM Forms App 6.3 finden Sie unter [Einrichten des Eclipse-Projekts und Erstellen der Android™-App](/help/forms/using/setup-eclipse-project-build-installer.md).

In AEM Forms wird der vollständige Quellcode der AEM Forms-App bereitgestellt. Die Quelle enthält alle Komponenten, die für eine benutzerdefinierte AEM Forms-App erforderlich sind. Das Quellcode-Archiv `adobe-lc-mobileworkspace-src-<version>.zip` ist Teil des `adobe-aemfd-forms-app-src-pkg-<version>.zip`-Pakets zur Softwareverteilung.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Öffnen Sie [Software-Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können die Ergebnisse auch mit der Option **[!UICONTROL Downloads suchen]** filtern.
1. Tippen Sie auf den Paketnamen, der auf Ihr Betriebssystem zutrifft, wählen Sie **[!UICONTROL EULA-Begriffe akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

Die folgende Abbildung zeigt den extrahierten Inhalt von `adobe-lc-mobileworkspace-src-<version>.zip`.

![Extrahierter Inhalt der komprimierten Android™-Quelle](assets/mws-content-1.png)

Die folgende Abbildung zeigt die Ordnerstruktur des Ordners `android`im Ordner `src`an.

![Ordnerstruktur des Android Ordner in src](assets/android-folder.png)

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

1. Führen Sie die folgenden Schritte aus, um ein Projekt in Android™ Studio einzurichten und eine Signing-Identität anzugeben:

   Melden Sie sich bei einem Computer an, auf dem Android™ Studio installiert und konfiguriert ist.

1. Kopieren Sie das heruntergeladene Archiv `adobe-lc-mobileworkspace-src-<version>.zip` nach:

   **MAC-Benutzer**:  `[User_Home]/Projects`

   **Für Windows®-Benutzer**:  `%HOMEPATH%\Projects`

   >[!NOTE]
   >
   >Für Windows® wird empfohlen, das Android-Projekt auf dem Systemlaufwerk zu belassen.

1. Extrahieren Sie das Archiv im folgenden Verzeichnis:

   **MAC-Benutzer**:  `[User_Home]/Projects/[your-project]`

   **Für Windows®-Benutzer**:  `%HOMEPATH%\Projects\[your-project]`

   >[!NOTE]
   >
   >Es wird empfohlen, das extrahierte Android-Projekt auf dem Systemlaufwerk zu belassen, bevor Sie das Projekt in Android Studio importieren.

1. Starten Sie Android™ Studio.

   **MAC-Benutzer**: Aktualisieren Sie die  `local.properties` Datei im  `[User_Home]/Projects/[your-project]/android` Ordner und verweisen Sie auf den  `sdk.dir` Speicherort der  `SDK` Variablen auf dem Desktop.

   **Für Windows®-Benutzer**: Aktualisieren Sie die  `local.properties` Datei im  `%HOMEPATH%\Projects\[your-project]\android` Ordner und verweisen Sie auf den  `sdk.dir` Speicherort der  `SDK` Variablen auf dem Desktop.

1. Klicken Sie auf **[!UICONTROL Fertig stellen]**, um das Projekt zu erstellen.

   Das Projekt ist im ADT Project Explorer verfügbar.

   ![Eclipse-Projekt nach Erstellen der App](assets/eclipsebuildmws.png)

1. Wählen Sie in Android™ Studio **[!UICONTROL Projekt importieren (Eclipse ADT, Gradle, etc.)]**.
1. Wählen Sie im Projektexplorer im Textfeld **Stammordner** den Stammordner des Projekts aus, das Sie erstellen möchten:

   **Für Mac-Benutzer:** [User_Home]/Projects/MobileWorkspace/src/android

   **Windows®-Benutzer:** %HOMEPATH%\Projects\MobileWorkspace\src\android

1. Nachdem das Projekt importiert wurde, erscheint ein Popup mit der Option zum Aktualisieren des Android™ Plugin Gradle. Klicken Sie wie für Ihre Zwecke benötigt auf die entsprechende Schaltfläche.

   ![dontremindemagainrisproject](assets/dontremindmeagainforthisproject.png)

1. Nach dem erfolgreichen Erstellen des Gradle erscheint der folgende Bildschirm. Schließen Sie das entsprechende Gerät oder den Emulator an das System an und klicken Sie auf **[!UICONTROL Android™]** ausführen.

   ![Gradleconsole](assets/gradleconsole.png)

1. Android™ Studio zeigt die verbundenen Geräte und verfügbaren Emulatoren an. Wählen Sie das Gerät, auf dem Sie die Anwendung ausführen wollen, und klicken Sie dann auf **OK**.

   ![connectDevice](assets/connecteddevice.png)

Nachdem Sie das Projekt erstellt haben, haben Sie folgende Möglichkeiten zum Installieren der App mit Android™ Debug Bridge oder Android™ Studio:

### Mit Android™ Debug Bridge {#andriod-debug-bridge}

Sie können die Anwendung über [Android™ Debug Bridge](https://developer.android.com/tools/help/adb.html) mit folgendem Befehl auf einem Android™-Gerät installieren:

**MAC-Benutzer**:  `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`

**Für Windows®-Benutzer**:  `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`
