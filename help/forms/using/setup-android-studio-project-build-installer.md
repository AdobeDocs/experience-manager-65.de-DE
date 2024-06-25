---
title: Richten Sie das Android™-Studioprojekt ein und erstellen Sie eine Android™-App
description: Schritte zum Einrichten des Android™ Studio-Projekts und Erstellen des Installationsprogramms für die Adobe Experience Manager (AEM) Forms-App
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: forms-app
exl-id: 47d6af00-34d8-4e5d-8117-86fc1b6f58cb
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: ht
source-wordcount: '584'
ht-degree: 100%

---

# Richten Sie das Android™-Studioprojekt ein und erstellen Sie eine Android™-App {#set-up-the-android-studio-project-and-build-the-android-app}

Dieser Artikel gilt für das Erstellen der AEM Forms-App 6.3.1.1 und höheren Versionen. Zum Erstellen einer App aus dem Quell-Code der AEM Forms App 6.3 siehe [Einrichten des Eclipse-Projekts und Erstellen der Android™-App](/help/forms/using/setup-eclipse-project-build-installer.md).

In AEM Forms wird der vollständige Quell-Code der AEM Forms-App bereitgestellt. Die Quelle enthält alle Komponenten, die für eine benutzerdefinierte AEM Forms-App erforderlich sind. Das Quell-Code-Archiv `adobe-lc-mobileworkspace-src-<version>.zip` ist Bestandteil des Pakets `adobe-aemfd-forms-app-src-pkg-<version>.zip` in Software Distribution.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Wählen Sie im Kopfzeilenmenü **[!UICONTROL Adobe Experience Manager]** aus.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen, dann **[!UICONTROL EULA-Bedingungen akzeptieren]** und dann **[!UICONTROL Herunterladen]** aus.
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

   **Für Mac-Benutzende**: `[User_Home]/Projects`

   **Für Windows®-Benutzende**: `%HOMEPATH%\Projects`

   >[!NOTE]
   >
   >Für Windows® wird empfohlen, das Android™-Projekt auf dem Systemlaufwerk zu belassen.

1. Extrahieren Sie das Archiv im folgenden Verzeichnis:

   **Für Mac-Benutzende:** `[User_Home]/Projects/[your-project]`

   **Für Windows®-Benutzende**: `%HOMEPATH%\Projects\[your-project]`

   >[!NOTE]
   >
   >Es wird empfohlen, das extrahierte Android-Projekt auf dem Systemlaufwerk zu belassen, bevor Sie das Projekt in Android™ Studio importieren.

1. Starten Sie Android™ Studio.

   **Für Mac-Benutzende**: Aktualisieren Sie die Datei `local.properties` im Ordner `[User_Home]/Projects/[your-project]/android` und lassen Sie die Variable `sdk.dir` auf den Speicherort `SDK` auf Ihrem Desktop verweisen.

   **Für Windows®-Benutzer**: Aktualisieren Sie die Datei `local.properties` im Ordner `%HOMEPATH%\Projects\[your-project]\android` und lassen Sie die Variable `sdk.dir` auf den Speicherort `SDK` auf Ihrem Desktop verweisen.

1. Klicken Sie auf **[!UICONTROL Fertig stellen]**, um das Projekt zu erstellen.

   Das Projekt ist im ADT Project Explorer verfügbar.

   ![Eclipse-Projekt nach Erstellen der App](assets/eclipsebuildmws.png)

1. Wählen Sie in Android™ Studio **[!UICONTROL Projekt importieren (Eclipse ADT, Gradle, etc.)]**.
1. Wählen Sie im Project Explorer den Stammordner des zu erstellenden Projekts im Textfeld **Stammordner** aus:

   **Für Mac-Benutzer:** [Benutzer_Home]/Projects/MobileWorkspace/src/android

   **Für Windows®-Benutzer:** %HOMEPATH%\Projects\MobileWorkspace\src\android

1. Nachdem das Projekt importiert wurde, erscheint ein Popup mit der Option zum Aktualisieren des Android™-Plug-ins Gradle. Klicken Sie je nach Ihren Anforderungen auf die entsprechende Schaltfläche.

   ![dontremindmeagainforthisproject](assets/dontremindmeagainforthisproject.png)

1. Nach dem erfolgreichen Erstellen des Gradle erscheint der folgende Bildschirm. Verbinden Sie das entsprechende Gerät oder den entsprechenden Emulator mit dem System und klicken Sie auf **[!UICONTROL Android™ ausführen]**.

   ![gradleconsole](assets/gradleconsole.png)

1. Android™ Studio zeigt die verbundenen Geräte und verfügbaren Emulatoren an. Wählen Sie das Gerät, auf dem Sie die Anwendung ausführen wollen, und klicken Sie dann auf **OK**.

   ![connecteddevice](assets/connecteddevice.png)

Nachdem Sie das Projekt erstellt haben, haben Sie folgende Möglichkeiten zum Installieren der App mit Android™ Debug Bridge oder Android™ Studio:

### Mit Android™ Debug Bridge {#andriod-debug-bridge}

Sie können die Anwendung über [Android™ Debug Bridge](https://developer.android.com/tools/adb) mit folgendem Befehl auf einem Android™-Gerät installieren:

**Für Mac-Benutzende**:`adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`

**Für Windows®-Benutzende**: `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`
