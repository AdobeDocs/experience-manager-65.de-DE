---
title: Richten Sie das Android-Studioprojekt ein und erstellen Sie eine Android-App
seo-title: Set up the Android studio project and build the Android app
description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen des Installationsprogramms für die AEM Forms-App
seo-description: Steps to set up the Android Studio project and build the installer for the AEM Forms app
uuid: 4c966cdc-d0f5-4b5b-b21f-f11e8a35ec8a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: forms-app
discoiquuid: fabc981e-0c9e-4157-b0a1-0c13717fb6cd
exl-id: 47d6af00-34d8-4e5d-8117-86fc1b6f58cb
source-git-commit: 63f066013c34a5994e2c6a534d88db0c464cc905
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 100%

---

# Richten Sie das Android-Studioprojekt ein und erstellen Sie eine Android-App {#set-up-the-android-studio-project-and-build-the-android-app}

Dieser Artikel gilt für das Erstellen der AEM Forms App 6.3.1.1 und höheren Versionen. Zum Erstellen einer Mobile App aus dem Quell-Code der Mobile App 6.3 von AEM Forms, siehe [Einrichten des Eclipse-Projekts und Erstellen der Android™-App](/help/forms/using/setup-eclipse-project-build-installer.md).

In AEM Forms wird der vollständige Quellcode der AEM Forms-App bereitgestellt. Die Quelle enthält alle Komponenten, die für eine benutzerdefinierte AEM Forms-App erforderlich sind. Das Quell-Code-Archiv `adobe-lc-mobileworkspace-src-<version>.zip` ist Bestandteil des Pakets `adobe-aemfd-forms-app-src-pkg-<version>.zip` in Software Distribution.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den für Ihr Betriebssystem zutreffenden Paketnamen, wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

Die folgende Abbildung zeigt den extrahierten Inhalt von `adobe-lc-mobileworkspace-src-<version>.zip`.

![Extrahierter Inhalt der komprimierten Android™-Quelle](assets/mws-content-1.png)

Die folgende Abbildung zeigt die Verzeichnisstruktur des Ordners `android` im Ordner `src` an.

![Ordnerstruktur des Android Ordner in src](assets/android-folder.png)

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

1. Führen Sie die folgenden Schritte aus, um ein Projekt in Android™ Studio einzurichten und eine Signing-Identität anzugeben:

   Melden Sie sich bei einem Computer an, auf dem Android™ Studio installiert und konfiguriert ist.

1. Kopieren Sie das heruntergeladene Archiv `adobe-lc-mobileworkspace-src-<version>.zip` zu:

   **Für MAC-Benutzer**: `[User_Home]/Projects`

   **Für Windows®-Benutzer**: `%HOMEPATH%\Projects`

   >[!NOTE]
   >
   >Für Windows® wird empfohlen, das Android-Projekt auf dem Systemlaufwerk zu belassen.

1. Extrahieren Sie das Archiv im folgenden Verzeichnis:

   **Für MAC-Benutzer**: `[User_Home]/Projects/[your-project]`

   **Für Windows®-Benutzer**: `%HOMEPATH%\Projects\[your-project]`

   >[!NOTE]
   >
   >Es wird empfohlen, das extrahierte Android-Projekt auf dem Systemlaufwerk zu belassen, bevor Sie das Projekt in Android Studio importieren.

1. Starten Sie Android™ Studio.

   **Für MAC-Benutzer**: Aktualisieren Sie die Datei `local.properties` im Ordner `[User_Home]/Projects/[your-project]/android` und lassen Sie die Variable `sdk.dir` auf den Speicherort `SDK` auf Ihrem Desktop verweisen.

   **Für Windows®-Benutzer**: Aktualisieren Sie die Datei `local.properties` im Ordner `%HOMEPATH%\Projects\[your-project]\android` und lassen Sie die Variable `sdk.dir` auf den Speicherort `SDK` auf Ihrem Desktop verweisen.

1. Klicken Sie auf **[!UICONTROL Fertig stellen]**, um das Projekt zu erstellen.

   Das Projekt ist im ADT Project Explorer verfügbar.

   ![Eclipse-Projekt nach Erstellen der App](assets/eclipsebuildmws.png)

1. Wählen Sie in Android™ Studio **[!UICONTROL Projekt importieren (Eclipse ADT, Gradle, etc.)]**.
1. Wählen Sie im Project Explorer den Stammordner des zu erstellenden Projekts im Textfeld **Stammordner** aus:

   **Für Mac-Benutzer:** [Benutzer_Home]/Projects/MobileWorkspace/src/android

   **Für Windows®-Benutzer:** %HOMEPATH%\Projects\MobileWorkspace\src\android

1. Nachdem das Projekt importiert wurde, erscheint ein Popup mit der Option zum Aktualisieren des Android™ Plugin Gradle. Klicken Sie wie für Ihre Zwecke benötigt auf die entsprechende Schaltfläche.

   ![dontremindmeagainforthisproject](assets/dontremindmeagainforthisproject.png)

1. Nach dem erfolgreichen Erstellen des Gradle erscheint der folgende Bildschirm. Verbinden Sie das entsprechende Gerät oder den entsprechenden Emulator mit dem System und klicken Sie auf **[!UICONTROL Android™ ausführen]**.

   ![gradleconsole](assets/gradleconsole.png)

1. Android™ Studio zeigt die verbundenen Geräte und verfügbaren Emulatoren an. Wählen Sie das Gerät, auf dem Sie die Anwendung ausführen wollen, und klicken Sie dann auf **OK**.

   ![connecteddevice](assets/connecteddevice.png)

Nachdem Sie das Projekt erstellt haben, haben Sie folgende Möglichkeiten zum Installieren der App mit Android™ Debug Bridge oder Android™ Studio:

### Mit Android™ Debug Bridge {#andriod-debug-bridge}

Sie können die Anwendung über [Android™ Debug Bridge](https://developer.android.com/tools/help/adb.html) mit folgendem Befehl auf einem Android™-Gerät installieren:

**Für MAC-Benutzer**: `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`

**Für Windows®-Benutzer**: `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`
