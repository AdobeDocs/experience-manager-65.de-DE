---
title: Aufbauen der AEM Forms Android-App
description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen der APK-Datei für die AEM Forms-App für Android
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 3fb069cf-d3ed-47b0-b6bf-82e110b3b059
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 100%

---

# Erstellen Sie die AEM Forms Android-App {#build-the-aem-forms-android-app}

Um die AEM Forms-App für Android zu erstellen, führen Sie die folgenden Schritte in der empfohlenen Reihenfolge aus.

1. [Laden Sie das Quellcode-Paket der AEM Forms-App herunter](#download-android-zip)
1. [Legen Sie die Umgebungsvariable fest.](#set-environment-variable-android)
1. [Erstellen einer standardmäßigen AEM Forms-App](#set-up-the-xcode-project)

## Laden Sie das Quellcode-Paket der AEM Forms-App herunter {#download-android-zip}

Das AEM Forms-App-Quellcodepaket verweist auf das Archiv `adobe-lc-mobileworkspace-src-<version>.zip`. Dieses Archiv enthält den Quellcode, der zum Erstellen einer benutzerdefinierten AEM Forms-App erforderlich ist. Das Archiv wird im Paket `adobe-aemfd-forms-app-src-pkg-<version>.zip` der Software Distribution bereitgestellt.

Führen Sie die folgenden Schritte aus, um die Datei `adobe-aemfd-forms-app-src-pkg-<version>.zip` herunterzuladen:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Wählen Sie im Kopfzeilenmenü **[!UICONTROL Adobe Experience Manager]** aus.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen, dann **[!UICONTROL EULA-Bedingungen akzeptieren]** und dann **[!UICONTROL Herunterladen]** aus.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.
1. Um das Quellcodearchiv herunterzuladen, öffnen Sie **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in Ihrem Browser. Die ZIP-Datei der Android-App wird auf Ihr Gerät heruntergeladen.
1. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner in Ihrem lokalen Dateisystem. Beispiel: *C:\&lt;Folder Structure>\adobe-lc-mobileworkspace-src-2.4.20*

Das folgende Bild zeigt die Struktur des Ordners `adobe-lc-mobileworkspace-src-<version>.zip\android`.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Festlegen der Umgebungsvariablen {#set-environment-variable-android}

Legen Sie die folgenden Umgebungsvariablen fest, bevor Sie den Build-Prozess für die AEM Forms-Anwendung starten:

* Legen Sie die Umgebungsvariable JAVA_HOME auf den Speicherort der JDK-Software im lokalen Dateisystem fest. Beispiel: C:\Program Files\Java\jdk1.8.0_181
* Setzen Sie die Systemumgebungsvariable `ANDROID_SDK_ROOT` auf den Speicherort des SDK für Android. Beispiel: C:\Benutzer\&lt;Benutzername>\AppData\Local\Android\Sdk
* Legen Sie die Systemumgebungsvariable `Path` fest, um die Ordner „Plattform-Tools“ und „Tools“ für Android einzubeziehen. Beispiel: C:\Benutzer\&lt;Benutzername>\AppData\Local\Android\Sdk\platform-tools und C:\Benutzer\&lt;Benutzername>\AppData\Local\Android\Sdk\tools.

## Erstellen einer standardmäßigen AEM Forms-App {#set-up-the-xcode-project}

Wenn Sie die Datei „adobe-lc-mobileworkspace-src-&lt;version>.zip“ im lokalen Dateisystem gespeichert und die Umgebungsvariablen festgelegt haben, erstellen Sie die standardmäßige AEM Forms Android-Anwendung mithilfe einer der folgenden Optionen:

* [Erstellen Sie die AEM Forms-App mit Android Studio](#using-android-studio)
* [Generieren Sie die .apk-Datei mit Android Studio](#generate-apk-android-studio)

### Aufbauen der AEM Forms-App mit Android Studio {#using-android-studio}

Um eine AEM Forms-Anwendung mit Android Studio zu erstellen, führen Sie die folgenden Schritte aus:

1. Starten Sie die Android Studio-Anwendung auf Ihrem Computer.
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

   Nachdem Sie die entsprechenden Anpassungen in Ihrer Anwendung vorgenommen haben, können Sie die .apk-Datei für die Verteilung generieren.

### Generieren der .apk-Datei mit Android Studio {#generate-apk-android-studio}

Gehen Sie wie folgt vor, um die .apk-Datei mit Android Studio zu generieren:

1. Starten Sie die Android Studio-Anwendung auf Ihrem Computer.
1. Wählen Sie **Ein vorhandenes Android Studio-Projekt öffnen**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die android-Option im linken Fensterbereich angezeigt.

1. Wählen Sie **Build** > **APK erstellen** aus, um die .apk-Datei zu generieren.

   Wählen Sie optional **Erstellen** > **Signiertes APK generieren**, um eine [signierte Version](https://developer.android.com/studio/publish/app-signing) der APK-Datei zu generieren.

## Verwenden von Android Debug Bridge {#build-android-debug-bridge}

Sobald die APK-Datei generiert wurde, führen Sie den folgenden Befehl aus, um das Programm mithilfe von [Android Debug Bridge](https://developer.android.com/tools/adb) auf einem Android-Gerät zu installieren.

**Windows-Benutzer:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Mac-Benutzende:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
