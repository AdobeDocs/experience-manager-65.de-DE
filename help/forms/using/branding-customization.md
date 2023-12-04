---
title: Branding-Anpassung
seo-title: Branding Customization
description: Passen Sie das Programmsymbol, den Anwendungsnamen, Startbilder und die Anmeldeseite an, um der AEM Forms-App ein charakteristisches Erscheinungsbild für die Organisation zu verleihen.
seo-description: Customize the application icon, application name, launch images, and login page to provide a distinct organization-specific look and feel to AEM Forms app.
uuid: fece0fa8-c417-45eb-93f1-a91b49835fa0
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: f6440a36-719a-4f89-b7db-1af918a3469a
exl-id: 9333705b-9944-4a74-a30f-7d9ec85fd824
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 50%

---

# Branding-Anpassung {#branding-customization}

Sie können das Symbol und den Namen der Anwendung, Startbilder und die Anmeldeseite anpassen und dadurch ein auf Ihr Unternehmen zugeschnittenes Erscheinungsbild für Ihre Organisation in der AEM Forms-App gestalten. Sie können beispielsweise die Bilder so ändern, dass Logos aus Ihrer Organisation verwendet werden. Die AEM Forms-App unterstützt die folgenden Anpassungen:

* Anpassen des Programmsymbols und der Startbilder
* App-Namen anpassen
* Bilder auf der Anmeldeseite anpassen
* Anpassen des Logos im App-Menü

## Anpassen von Symbol- und Startbildern {#customizing-icon-and-launch-images}

Führen Sie die folgenden Schritte aus, um das standardmäßige App-Symbol und das Startbild der AEM Forms-App anzupassen:

>[!NOTE]
>
>Verwenden Sie für alle Symbole und Bilder das PNG-Format ohne Zeilensprung.

### So passen Sie Symbole und Startbilder an {#to-customize-icon-and-launch-images}

#### Für iOS {#for-ios}

1. Öffnen Sie das Projekt `Capture.xcodeproj` in Xcode.
1. (***Symbol anpassen***) Navigieren Sie in der Navigatoransicht von „Capture“ zu **[!UICONTROL „Capture“ > „Capture“ > „Unterstützende Dateien“ > Capture-info.plist]**. Klicken Sie auf das Dropdown-Menü neben den Symboldateien. Geben Sie den Namen der Symboldatei (.png) an und laden Sie die Datei in **[!UICONTROL „Capture“ > „Capture“ > „Ressourcen“ > „Symbole“]** hoch. Derzeit unterstützte Abmessungen sind: 29 x 29, 50 x 50, 58 x 58, 72 x 72, 100 x 100 und 144 x 144.
1. (***Startbilder anpassen***) Vergewissern Sie sich, dass die Dateinamen Ihrer Startbilder folgendermaßen lauten.

   * Für Hochformat: `Default-Portrait~ipad.png` und `Default-Portrait@2x~ipad.png`
   * Für Querformat: `Default-Landscape~ipad.png` und `Default-Landscape@2x~ipad.png`

   Laden Sie sie in das Projekt Capture hoch, um vorhandene Dateien im Projekt zu ersetzen.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Name und Auflösung des Bildes mit dem Bild übereinstimmen, das Sie im Projekt ersetzen.

1. Erstellen Sie die AEM Forms-App auf einem iOS-Gerät oder einem iOS-Simulator.

#### Für Android {#for-android}

1. Benennen Sie die Anwendungssymboldateien wie folgt:

   `ic_launcher.png`

1. Platzieren Sie die entsprechende Symboldateien in den folgenden Verzeichnissen:

   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-hdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-mdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xhdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xxhdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xxxhdpi`

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Name und Auflösung des Bildes mit dem Bild übereinstimmen, das Sie im Projekt ersetzen.

1. Erstellen Sie die AEM Forms-App neu.

### Für Windows {#for-windows}

1. Ersetzen Sie die Symbole im Pfad:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\res\icons\windows`

1. Ersetzen Sie das Starterbild im Pfad:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\res\screens\windows`

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Name und Auflösung des Bildes mit dem Bild übereinstimmen, das Sie im Projekt ersetzen.

1. Erstellen Sie die AEM Forms-App neu.

## App-Namen anpassen {#customize-the-app-name}

### Für iOS {#for-ios-1}

1. Öffnen Sie das Projekt `Capture.xcodeproj` in Xcode.
1. Gehen Sie in der Navigatoransicht von Capture zu **[!UICONTROL Capture > Capture > Unterstützende Dateien > InfoPlist.strings]**.

   Ändern Sie den Wert für das Attribut `CFBundleDisplayName` auf einen Namen, den Sie für die Anwendung anzeigen möchten.

1. Erstellen Sie die AEM Forms-App auf einem iOS-Gerät oder einem iOS-Simulator.

   Weitere Informationen zum Erstellen der App für iOS finden Sie unter [Einrichten des Xcode-Projekts und Erstellen der iOS-App](/help/forms/using/setup-xcode-project-build-installer.md).

### Für Android {#for-android-1}

1. Öffnen Sie die folgende XML-Datei in einem Text- oder XML-Editor:

   `[User_Home]/Projects/[your-project]/src/android/res/values/strings.xml and android/res/values-en/strings.xml`

1. Aktualisieren Sie den Wert des Schlüssels `app_name`.
1. Erstellen Sie die AEM Forms-App neu.

   Weitere Informationen zum Erstellen der App für Android finden Sie unter [Einrichten des Eclipse-Projekts und Erstellen der Android-App](/help/forms/using/setup-eclipse-project-build-installer.md).

### Für Windows {#for-windows-1}

1. Öffnen Sie die folgende XML-Datei in einem beliebigen Texteditor:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\config.xml`

1. Aktualisieren Sie den Wert im `<name>...</name>`-Tag.
1. Erstellen Sie die AEM Forms-App neu.

   Weitere Informationen zum Erstellen der App für Windows finden Sie unter [Einrichten des Visual Studio-Projekts und Erstellen der Windows-App](/help/forms/using/setup-visual-studio-project-build-installer.md).

## Bilder auf der Anmeldeseite anpassen {#customizing-images-on-the-login-page}

Auf der Anmeldeseite der AEM Forms-App befinden sich Bilder für das Logo und den Hintergrund. Das Logo befindet sich über dem Anmeldungsdialogfeld und das Hintergrundbild befindet sich unter dem Anmeldungsdialogfeld. Führen Sie die folgenden Schritte aus, um das Standardbild auf der Anmeldeseite anzupassen:

**Bevor Sie beginnen**

Stellen Sie sicher, dass Sie die folgenden Bilder haben:

<table>
 <tbody>
  <tr>
   <th><p>Beschreibung</p> </th>
   <th><p>Größe</p> </th>
   <th><p>Dateiname</p> </th>
  </tr>
  <tr>
   <td><p>Logo</p> </td>
   <td><p>72 x 72 Pixel</p> </td>
   <td><p>LC-logo.png</p> </td>
  </tr>
  <tr>
   <td><p>Hintergrundbild (Hochformat)</p> </td>
   <td><p>1280 x 989 Pixel</p> </td>
   <td><p>Landing_bg.jpeg</p> </td>
  </tr>
 </tbody>
</table>

**So passen Sie Bilder auf der Anmeldeseite mit Xcode an**

1. Öffnen Sie das Projekt `Capture.xcodeproj` in Xcode.

1. Navigieren Sie zum Ordner `www/wsmobile/images`. 
1. Um das Logo zu ändern, ersetzen Sie die Standarddatei `LC-logo.png` durch die benutzerdefinierte Datei `LC-logo.png`.
1. Um den Hintergrund zu ändern, ersetzen Sie die standardmäßige Datei `Landing_bg.jpeg` mit der benutzerdefinierten Datei `Landing_bg.jpeg`.
1. Bauen Sie die AEM Forms-App auf einem iOS-Gerät oder einem iOS-Simulator auf und führen Sie sie aus.

### So passen Sie Bilder auf den Anmeldeseiten mit Eclipse an {#to-customize-images-on-the-login-pages-using-eclipse}

1. Öffnen Sie das Android-Projekt in Eclipse.

1. Navigieren Sie zum Ordner `assets/www/wsmobile/images`. 
1. Um das Logo zu ändern, ersetzen Sie die Standarddatei `LC-logo.png` durch die benutzerdefinierte Datei `LC-logo.png`.
1. Um den Hintergrund zu ändern, ersetzen Sie die standardmäßige Datei `Landing_bg.jpeg` mit der benutzerdefinierten Datei `Landing_bg.jpeg`.
1. Erstellen Sie die AEM Forms-App auf einem Android-Gerät und führen Sie sie aus.

### So passen Sie Bilder auf den Anmeldeseiten mit Visual Studio an {#to-customize-images-on-the-login-pages-using-visual-studio}

1. Öffnen Sie das `MWSWindows.sln`-Projekt in Visual Studio.

1. Navigieren Sie zum Ordner `MWSWindows\www\wsmobile\images`. 
1. Um das Logo zu ändern, ersetzen Sie die Standarddatei `LC-logo.png` durch die benutzerdefinierte Datei `LC-logo.png`.
1. Um den Hintergrund zu ändern, ersetzen Sie die standardmäßige Datei `Landing_bg.jpeg` mit der benutzerdefinierten Datei `Landing_bg.jpeg`.
1. Bauen Sie die AEM Forms-App auf einem Windows-Gerät auf und führen Sie sie aus.

## Anpassen des Logos im App-Menü {#customizing_images_on_the_login_page-1}

Nachdem Sie sich bei der AEM Forms-App angemeldet und auf die Menüschaltfläche geklickt haben, wird das Logo über dem Menü angezeigt. Führen Sie die folgenden Schritte aus, um das Standardlogo anzupassen:

**Bevor Sie beginnen**

Stellen Sie sicher, dass Sie das folgende Bild haben:

<table>
 <tbody>
  <tr>
   <th><p>Beschreibung</p> </th>
   <th><p>Größe</p> </th>
   <th><p>Dateiname</p> </th>
  </tr>
  <tr>
   <td><p>Logo</p> </td>
   <td><p>72 x 72 Pixel</p> </td>
   <td><p>aem_icon.png</p> </td>
  </tr>
 </tbody>
</table>

**So passen Sie Bilder auf der Anmeldeseite mit Xcode an**

1. Öffnen Sie das Projekt `Capture.xcodeproj` in Xcode.

1. Navigieren Sie zum Ordner `www/wsmobile/images`. 
1. Um das Logo zu ändern, ersetzen Sie die standardmäßige Datei `aem_icon.png` durch die benutzerdefinierte Datei `aem_icon.png`.
1. Bauen Sie die AEM Forms-App auf einem iOS-Gerät oder einem iOS-Simulator auf und führen Sie sie aus.

### So passen Sie Bilder auf den Anmeldeseiten mit Eclipse an {#to-customize-images-on-the-login-pages-using-eclipse-1}

1. Öffnen Sie das Android-Projekt in Eclipse.

1. Navigieren Sie zum Ordner `assets/www/wsmobile/images`. 
1. Um das Logo zu ändern, ersetzen Sie die standardmäßige Datei `aem_icon.png` durch die benutzerdefinierte Datei `aem_icon.png`.
1. Erstellen Sie die AEM Forms-App auf einem Android-Gerät und führen Sie sie aus.

### So passen Sie Bilder auf den Anmeldeseiten mit Visual Studio an {#to-customize-images-on-the-login-pages-using-visual-studio-1}

1. Öffnen Sie das `MWSWindows.sln`-Projekt in Visual Studio.

1. Navigieren Sie zum Ordner `MWSWindows\www\wsmobile\images`. 
1. Um das Logo zu ändern, ersetzen Sie die standardmäßige Datei `aem_icon.png` durch die benutzerdefinierte Datei `aem_icon.png`.
1. Erstellen und wählen Sie „AEM Forms App“ auf dem Windows-Gerät.
