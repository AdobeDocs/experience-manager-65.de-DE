---
title: Erstellen Sie die AEM Forms Android-App
seo-title: Erstellen Sie die AEM Forms Android-App
description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen der .apk-Datei für die AEM Forms-App für Android
seo-description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen der .apk-Datei für die AEM Forms-App für Android
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Erstellen Sie die AEM Forms Android-App {#build-the-aem-forms-android-app}

Führen Sie die folgenden Schritte in der empfohlenen Reihenfolge aus, um die Android-App für AEM Forms zu erstellen.

1. [Laden Sie das Quellcode-Paket der AEM Forms-App herunter](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-header-277929160)
1. [Legen Sie die Umgebungsvariable fest](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-header-111803610).
1. [Standardmäßige AEM Forms-App erstellen](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-heading-0)

## Laden Sie das Quellcode-Paket der AEM Forms-App herunter {#download-android-zip}

AEM Forms App Source Code Package refers to the `adobe-lc-mobileworkspace-src-<version>.zip` archive. Dieses Archiv enthält den Quellcode, der zum Erstellen einer benutzerdefinierten AEM Forms-App erforderlich ist. The archive is included in the `adobe-aemfd-forms-app-src-pkg-<version>.zip`package available on the package share.

Perform the following steps to download the `adobe-aemfd-forms-app-src-pkg-<version>.zip` file:

1. Log in to the author instance of the [AEM server](http://localhost:4502/) as an administrator and open [package share](http://localhost:4502/crx/packageshare). Zum Anmelden bei der Paketfreigabe benötigen Sie eine Adobe ID.
1. In [AEM package share](http://localhost:4502/crx/packageshare/login.html), search `adobe-aemfd-forms-app-src-pkg-<version>.zip`, click the package applicable to your operating system, and click **Download**. Lesen und akzeptieren Sie die Lizenzvereinbarung und klicken Sie auf **OK**. Der Download wird gestartet. Nachdem der Download abgeschlossen ist, wird das Wort **Heruntergeladen** neben dem Paket angezeigt.
1. Nachdem der Download abgeschlossen ist, klicken Sie auf **Heruntergeladen**. Sie werden zum Paketmanager weitergeleitet. Suchen Sie im Paketmanager das heruntergeladene Paket und klicken Sie auf **Installieren**.
1. To download the source-code archive, open **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in your browser. Die ZIP-Datei der Android-App wird auf Ihr Gerät heruntergeladen.
1. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner in Ihrem lokalen Dateisystem. For example, *C:\&amp;lt;Folder Structure>\adobe-lc-mobileworkspace-src-2.4.20*

The following image displays the structure of the `adobe-lc-mobileworkspace-src-<version>.zip\android`folder.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Legen Sie die Umgebungsvariable fest.{#set-environment-variable-android}

Legen Sie die folgenden Umgebungsvariablen fest, bevor Sie den Erstellungsprozess für die AEM Forms-App starten:

* Setzen Sie die Umgebungsvariable JAVA_HOME auf den Speicherort der JDK-Software im lokalen Dateisystem. Beispiel: C:\Programme\Java\jdk1.8.0_181
* Set the `ANDROID_SDK_ROOT` system environment variable to the SDK location for Android. Beispiel: C:\Users\&amp;lt;Benutzername>\AppData\Local\Android\Sdk
* Legen Sie die Systemumgebungsvariable `Path` fest, um die Ordner „Plattform-Tools“ und „Tools“ für Android einzubeziehen . Beispiel: C:\Users\&amp;lt;Benutzername>\AppData\Local\Android\Sdk\platform-tools and C:\Users\&amp;lt;Benutzername>\AppData\Local\Android\Sdk\tools.

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

Nachdem Sie die Datei &quot;adobe-lc-mobileworkspace-src-&lt;version>.zip&quot;im lokalen Dateisystem gespeichert und die Variablen für die Umgebung festgelegt haben, erstellen Sie die AEM Forms-Android-Standardanwendung mit einer der folgenden Optionen:

* [Erstellen Sie die AEM Forms-App mit Android Studio](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-header-1347434739)
* [Generieren Sie die .apk-Datei mit Android Studio](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-header-0)

### Erstellen Sie die AEM Forms-App mit Android Studio {#using-android-studio}

Erstellen Sie die AEM Forms-App mit Android Studio über folgende Schritte:

1. Starten Sie die Android Studio-App auf Ihrem Computer.
1. Klicken Sie auf **Öffnen Sie ein vorhandenes Android Studio-Projekt**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die **android**-Option im linken Fensterbereich angezeigt.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Select **android** from the left pane and click **Run** > **Run &#39;android&#39;**.
1. Wählen Sie im Dialogfeld &quot;Zielgruppe für Bereitstellung auswählen&quot;im Abschnitt &quot;Angeschlossene Geräte&quot;das Android-Gerät aus und klicken Sie auf &quot;OK&quot;.

   Nachdem Sie die Entwicklungsumgebung erfolgreich erstellt haben, können Sie jetzt Anpassungen für die App vornehmen. Verwenden Sie die folgenden Artikel, um die App anzupassen:

   * [Branding-Anpassung](/help/forms/using/branding-customization.md)
   * [Designanpassung](/help/forms/using/theme-customization.md)
   * [Gestenanpassung](/help/forms/using/gesture-customization.md)
   Nach dem Anwenden entsprechender Anpassungen auf Ihre App können Sie die .apk-Datei für die Verteilung generieren.

### Generieren Sie die .apk-Datei mit Android Studio {#generate-apk-android-studio}

Führen Sie die folgenden Schritte aus, um die APK-Datei mit Android Studio zu generieren:

1. Starten Sie die Android Studio-App auf Ihrem Computer.
1. Select **Open an existing Android Studio project**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die android-Option im linken Fensterbereich angezeigt.

1. Wählen Sie **Erstellen** > **APK erstellen**, um die APK-Datei zu generieren.

   Optionally, Select **Build** > **Generate Signed APK** to generate a [signed version](https://developer.android.com/studio/publish/app-signing) of the .apk file.

## Verwenden von Android Debug Bridge {#build-android-debug-bridge}

Once the .apk file has been generated, execute the following command to install the application on an Android device using the [Android Debug Bridge](https://developer.android.com/tools/help/adb.html).

**Windows-Nutzer:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**MAC-Benutzer:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
