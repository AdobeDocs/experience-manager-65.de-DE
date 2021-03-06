---
title: Erstellen Sie die AEM Forms Android-App
seo-title: Build the AEM Forms Android app
description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen der .apk-Datei für die AEM Forms-App für Android
seo-description: Steps to set up the Android Studio project and build the .apk file for the AEM Forms app for Android
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
exl-id: 3fb069cf-d3ed-47b0-b6bf-82e110b3b059
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '723'
ht-degree: 100%

---

# Erstellen Sie die AEM Forms Android-App {#build-the-aem-forms-android-app}

Führen Sie die folgenden Schritte in der empfohlenen Reihenfolge aus, um die Android-App für AEM Forms zu erstellen.

1. [Laden Sie das Quellcode-Paket der AEM Forms-App herunter](#download-android-zip)
1. [Legen Sie die Umgebungsvariable fest.](#set-environment-variable-android)
1. [Standardmäßige AEM Forms-App erstellen](#set-up-the-xcode-project)

## Laden Sie das Quellcode-Paket der AEM Forms-App herunter {#download-android-zip}

Das AEM Forms-App-Quellcodepaket verweist auf das Archiv `adobe-lc-mobileworkspace-src-<version>.zip`. Dieses Archiv enthält den Quellcode, der zum Erstellen einer benutzerdefinierten AEM Forms-App erforderlich ist. Das Archiv wird im Paket `adobe-aemfd-forms-app-src-pkg-<version>.zip` der Software Distribution bereitgestellt.

Führen Sie folgende Schritte aus, um die Datei `adobe-aemfd-forms-app-src-pkg-<version>.zip` herunterzuladen:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den Namen des für Ihr Betriebssystem geeigneten Pakets, wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.
1. Um das Quellcodearchiv herunterzuladen, öffnen Sie **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in Ihrem Browser. Die ZIP-Datei der Android-App wird auf Ihr Gerät heruntergeladen.
1. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner in Ihrem lokalen Dateisystem. Beispiel: *C:\&lt;Folder Structure>\adobe-lc-mobileworkspace-src-2.4.20*

Das folgende Bild zeigt die Struktur des Ordners `adobe-lc-mobileworkspace-src-<version>.zip\android`.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Legen Sie die Umgebungsvariable fest. {#set-environment-variable-android}

Legen Sie die folgenden Umgebungsvariablen fest, bevor Sie den Erstellungsprozess für die AEM Forms-App starten:

* Setzen Sie die Umgebungsvariable JAVA_HOME auf den Speicherort der JDK-Software im lokalen Dateisystem. Beispiel: C:\Programme\Java\jdk1.8.0_181
* Setzen Sie die Systemumgebungsvariable `ANDROID_SDK_ROOT` auf den Speicherort des SDK für Android. Beispiel: C:\Benutzer\&lt;Benutzername>\AppData\Local\Android\Sdk
* Legen Sie die Systemumgebungsvariable `Path` fest, um die Ordner „Plattform-Tools“ und „Tools“ für Android einzubeziehen. Beispiel: C:\Benutzer\&lt;Benutzername>\AppData\Local\Android\Sdk\platform-tools und C:\Benutzer\&lt;Benutzername>\AppData\Local\Android\Sdk\tools.

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

Nachdem Sie die Datei adobe-lc-mobileworkspace-src-&lt;version>.zip im lokalen Dateisystem gespeichert und die Umgebungsvariablen festgelegt haben, erstellen Sie die standardmäßige AEM Forms Android-App mit einer der folgenden Optionen:

* [Erstellen Sie die AEM Forms-App mit Android Studio](#using-android-studio)
* [Generieren Sie die .apk-Datei mit Android Studio](#generate-apk-android-studio)

### Erstellen Sie die AEM Forms-App mit Android Studio {#using-android-studio}

Erstellen Sie die AEM Forms-App mit Android Studio über folgende Schritte:

1. Starten Sie die Android Studio-App auf Ihrem Computer.
1. Klicken Sie auf **Öffnen Sie ein vorhandenes Android Studio-Projekt**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die **android**-Option im linken Fensterbereich angezeigt.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Wählen Sie im linken Bereich **android** und aus klicken Sie auf **Run** > **&#39;android&#39; ausführen**.
1. Wählen Sie das Android-Gerät im Abschnitt „Verbundene Geräte“ im Dialogfeld „Ziel für die Bereitstellung auswählen“ aus und klicken Sie auf „OK“.

   Nachdem Sie die Entwicklungsumgebung erfolgreich erstellt haben, können Sie jetzt Anpassungen für die App vornehmen. Verwenden Sie die folgenden Artikel, um die App anzupassen:

   * [Branding-Anpassung](/help/forms/using/branding-customization.md)
   * [Designanpassung](/help/forms/using/theme-customization.md)
   * [Gestenanpassung](/help/forms/using/gesture-customization.md)

   Nach dem Anwenden entsprechender Anpassungen auf Ihre App können Sie die .apk-Datei für die Verteilung generieren.

### Generieren Sie die .apk-Datei mit Android Studio {#generate-apk-android-studio}

Führen Sie die folgenden Schritte aus, um die APK-Datei mit Android Studio zu generieren:

1. Starten Sie die Android Studio-App auf Ihrem Computer.
1. Wählen Sie **Ein vorhandenes Android Studio-Projekt öffnen**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die android-Option im linken Fensterbereich angezeigt.

1. Wählen Sie **Erstellen** > **APK erstellen**, um die APK-Datei zu generieren.

   Wählen Sie optional **Erstellen** > **Signiertes APK generieren**, um eine [signierte Version](https://developer.android.com/studio/publish/app-signing) der APK-Datei zu generieren.

## Verwenden von Android Debug Bridge {#build-android-debug-bridge}

Sobald die APK-Datei generiert wurde, führen Sie den folgenden Befehl aus, um das Programm mithilfe von [Android Debug Bridge](https://developer.android.com/tools/help/adb.html) auf einem Android-Gerät zu installieren.

**Windows-Benutzer:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Mac-Benutzer:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
