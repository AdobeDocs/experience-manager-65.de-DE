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
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 59%

---


# Erstellen Sie die AEM Forms Android-App {#build-the-aem-forms-android-app}

Führen Sie die folgenden Schritte in der empfohlenen Reihenfolge aus, um die Android-App für AEM Forms zu erstellen.

1. [Laden Sie das Quellcode-Paket der AEM Forms-App herunter](#download-android-zip)
1. [Legen Sie die Umgebungsvariable fest](#set-environment-variable-android).
1. [Standardmäßige AEM Forms-App erstellen](#set-up-the-xcode-project)

## Laden Sie das Quellcode-Paket der AEM Forms-App herunter {#download-android-zip}

AEM Forms App Source Code Package bezieht sich auf das `adobe-lc-mobileworkspace-src-<version>.zip`-Archiv. Dieses Archiv enthält den Quellcode, der zum Erstellen einer benutzerdefinierten AEM Forms-App erforderlich ist. Das Archiv ist im `adobe-aemfd-forms-app-src-pkg-<version>.zip`Paket enthalten, das in der Softwareverteilung verfügbar ist.

Führen Sie die folgenden Schritte aus, um die Datei `adobe-aemfd-forms-app-src-pkg-<version>.zip` herunterzuladen:

1. Öffnen Sie [Software-Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können die Ergebnisse auch mit der Option **[!UICONTROL Downloads suchen]** filtern.
1. Tippen Sie auf den Paketnamen, der auf Ihr Betriebssystem zutrifft, wählen Sie **[!UICONTROL EULA-Begriffe akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.
1. Um das Quellcode-Archiv herunterzuladen, öffnen Sie **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in Ihrem Browser. Die ZIP-Datei der Android-App wird auf Ihr Gerät heruntergeladen.
1. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner in Ihrem lokalen Dateisystem. Beispiel: *C:\&lt;Ordnerstruktur>\adobe-lc-mobileworkspace-src-2.4.20*

Die folgende Abbildung zeigt die Struktur des Ordners `adobe-lc-mobileworkspace-src-<version>.zip\android`an.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Legen Sie die Umgebungsvariable fest.{#set-environment-variable-android}

Legen Sie die folgenden Umgebungsvariablen fest, bevor Sie den Erstellungsprozess für die AEM Forms-App starten:

* Setzen Sie die Umgebungsvariable JAVA_HOME auf den Speicherort der JDK-Software im lokalen Dateisystem. Beispiel: C:\Programme\Java\jdk1.8.0_181
* Legen Sie die Systemvariable `ANDROID_SDK_ROOT` auf den SDK-Speicherort für Android fest. Beispiel: C:\Users\&amp;lt;Benutzername>\AppData\Local\Android\Sdk
* Legen Sie die Systemumgebungsvariable `Path` fest, um die Ordner „Plattform-Tools“ und „Tools“ für Android einzubeziehen . Beispiel: C:\Users\&amp;lt;Benutzername>\AppData\Local\Android\Sdk\platform-tools and C:\Users\&amp;lt;Benutzername>\AppData\Local\Android\Sdk\tools.

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

Nachdem Sie die Datei &quot;adobe-lc-mobileworkspace-src-&lt;version>.zip&quot;im lokalen Dateisystem gespeichert und die Variablen für die Umgebung festgelegt haben, erstellen Sie die AEM Forms Android-Standardanwendung mit einer der folgenden Optionen:

* [Erstellen Sie die AEM Forms-App mit Android Studio](#using-android-studio)
* [Generieren Sie die .apk-Datei mit Android Studio](#generate-apk-android-studio)

### Erstellen Sie die AEM Forms-App mit Android Studio  {#using-android-studio}

Erstellen Sie die AEM Forms-App mit Android Studio über folgende Schritte:

1. Starten Sie die Android Studio-App auf Ihrem Computer.
1. Klicken Sie auf **Öffnen Sie ein vorhandenes Android Studio-Projekt**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die **android**-Option im linken Fensterbereich angezeigt.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Wählen Sie **android** aus dem linken Bereich und klicken Sie auf **Ausführen** > **Ausführen von &#39;android&#39;**.
1. Wählen Sie im Dialogfeld &quot;Zielgruppe für Bereitstellung auswählen&quot;im Abschnitt &quot;Angeschlossene Geräte&quot;das Android-Gerät aus und klicken Sie auf &quot;OK&quot;.

   Nachdem Sie die Entwicklungsumgebung erfolgreich erstellt haben, können Sie jetzt Anpassungen für die App vornehmen. Verwenden Sie die folgenden Artikel, um die App anzupassen:

   * [Branding-Anpassung](/help/forms/using/branding-customization.md)
   * [Designanpassung](/help/forms/using/theme-customization.md)
   * [Gestenanpassung](/help/forms/using/gesture-customization.md)

   Nach dem Anwenden entsprechender Anpassungen auf Ihre App können Sie die .apk-Datei für die Verteilung generieren.

### Generieren Sie die .apk-Datei mit Android Studio  {#generate-apk-android-studio}

Führen Sie die folgenden Schritte aus, um die APK-Datei mit Android Studio zu generieren:

1. Starten Sie die Android Studio-App auf Ihrem Computer.
1. Wählen Sie **Öffnen Sie ein vorhandenes Android Studio-Projekt**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die android-Option im linken Fensterbereich angezeigt.

1. Wählen Sie **Erstellen** > **APK erstellen**, um die APK-Datei zu generieren.

   Optional können Sie **Build** > **Signierte APK erstellen** auswählen, um eine [signierte Version](https://developer.android.com/studio/publish/app-signing) der APK-Datei zu generieren.

## Verwenden von Android Debug Bridge {#build-android-debug-bridge}

Nachdem die APK-Datei generiert wurde, führen Sie den folgenden Befehl aus, um die Anwendung mit [Android Debug Bridge](https://developer.android.com/tools/help/adb.html) auf einem Android-Gerät zu installieren.

**Windows-Nutzer:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**MAC-Benutzer:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
