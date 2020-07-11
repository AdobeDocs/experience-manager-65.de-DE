---
title: Einrichten des Visual Studio-Projekts und Erstellen der Windows-App
seo-title: Einrichten des Visual Studio-Projekts und Erstellen der Windows-App
description: Erfahren Sie, wie Sie ein Visual Studio-Projekt einrichten können, um die AEM Forms-App für Windows-Mobilgeräte zu erstellen.
seo-description: Erfahren Sie, wie Sie ein Visual Studio-Projekt einrichten können, um die AEM Forms-App für Windows-Mobilgeräte zu erstellen.
uuid: 9559e584-2a40-4740-a29a-d7ad66220224
topic-tags: forms-app
discoiquuid: c71c2a17-54f9-4c95-a90a-3c89d6d45721
docset: aem65
translation-type: tm+mt
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 67%

---


# Einrichten des Visual Studio-Projekts und Erstellen der Windows-App{#set-up-the-visual-studio-project-and-build-the-windows-app}

In AEM Forms wird der vollständige Quellcode der AEM Forms-App bereitgestellt. Die Quelle enthält alle Komponenten, die für eine benutzerdefinierte Workspace-Anwendung erforderlich sind. Das Quellcode-Archiv `adobe-lc-mobileworkspace-src-<version>.zip`ist Teil des `adobe-aemfd-forms-app-src-pkg-<version>.zip` Pakets zur Softwareverteilung.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Open [Software Distribution](https://experience.adobe.com/downloads). Sie benötigen eine Adobe ID, um sich bei der Softwareverteilung anzumelden.
1. Tippen Sie auf **[!UICONTROL Adobe Experience Manager]** , der im Kopfzeilenmenü verfügbar ist.
1. In the **[!UICONTROL Filters]** section:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** .
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können die Ergebnisse auch mit der Option **[!UICONTROL Downloads]** suchen filtern.
1. Tippen Sie auf den Paketnamen, der auf Ihr Betriebssystem zutrifft, wählen Sie &quot;Endbenutzer-Lizenzbedingungen **[!UICONTROL akzeptieren&quot;]** und klicken Sie auf &quot; **[!UICONTROL Herunterladen]**&quot;.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf Paket **[!UICONTROL hochladen]** , um das Paket hochzuladen.
1. Select the package and click **[!UICONTROL Install]**.

1. Um das Quellcode-Archiv herunterzuladen, öffnen Sie `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` den Browser.\
   Das Quellpaket wird auf Ihr Gerät heruntergeladen.

The following image displays the extracted contents of the `adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content-1](assets/mws-content-1.png)

The following image displays the directory structure of the `windows` folder in the `src` folder.

![win-dir](assets/win-dir.png)

## Einrichten der Umgebung {#setting-up-the-environment}

Für Windows-Geräte benötigen Sie Folgendes:

* Microsoft Windows 8.1 oder Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio-Tools für Apache Cordova

## Einrichten des Visual Studio-Projekts für die AEM Forms-App {#setting-up-visual-studio-project-for-aem-forms-app}

Führen Sie folgende Schritte durch, um das AEM Forms-App-Projekt in Visual Studio einzurichten:

1. Copy the `adobe-lc-mobileworkspace-src-<version>.zip` archive to `%HOMEPATH%\Projects` folder in the Windows 8.1 or Windows 10 device with Visual Studio 2015 installed and configured.
1. Extract the archive in the `%HOMEPATH%\Projects\MobileWorkspace` directory.
1. Navigate to the `%HOMEPATH%\Projects\MobileWorkspace\adobe-lc-mobileworkspace-src-[versionsrc]\windows` directory.
1. Öffnen Sie die Datei `CordovaApp.sln` in Visual Studio 2015 und erstellen Sie die AEM Forms-App.

## Erstellen der AEM Forms-App {#build-aem-forms-app}

Führen Sie die folgenden Schritte zum Erstellen und Bereitstellen der AEM Forms-App durch:

>[!NOTE]
>
>Im Windows-Dateisystem für die AEM Forms-App gespeicherte Daten werden nicht verschlüsselt. Es wird empfohlen, zum Verschlüsseln von Festplattendaten ein Drittanbieter-Tool wie die Windows BitLocker Drive Encryption zu verwenden.

1. In the Visual Studio Standard Toolbar, select **Release** from the drop-down for build mode.

1. Wählen Sie je nach Ihrer Plattform Windows-AnyCPU, Windows-x64 oder Windows-x86. Empfohlen wird Windows-AnyCPU.
1. In the Visual Studio Solution Explorer, right-click the project **CordovaApp.Windows** and select **Store > Create AppPackages**.

   ![createapppackages](assets/createapppackages.png)

   Der Assistent zum Erstellen der App-Pakete wird angezeigt.

   Die Installationsprogrammdatei CordovaApp.Windows_3.0.2.0_anycpu.appx wird im Ordner platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test erstellt.

   If you encounter the error `Retarget to windows 8.1 required`, right-click the error and in the pop-up menu, select **Retarget To Windows 8.1**.

   ![retarget-solution](assets/retarget-solution.png)

1. Wählen Sie im Assistenten zum Erstellen von App-Paketen, ob Sie Ihre App in den Windows Store hochladen möchten, und klicken Sie dann auf **Weiter**.

   ![createapppackageswizard1](assets/createapppackageswizard1.png)

1. Nehmen Sie Änderungen an den Parameter wie der Version und dem Ausgabespeicherort des App-Builds vor wie benötigt.

   ![createapppackageswizard2](assets/createapppackageswizard2.png)

1. Nach Erstellung des Projekts können Sie die App mit folgenden Programmen installieren:

   * Windows PowerShell
   * Visual Studio

   The `.appx` package requires the following items to install successfully:

   1. WinJS-Bibliothek
   1. Stellen Sie sicher, dass das Paket mit einem selbstsignierten Zertifikat oder einem von einer vertrauenswürdigen Stelle signierten öffentlichen Zertifikat, wie etwa VeriSign, geliefert wird.
   1. Entwicklerlizenz

   Der Ordner Platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test enthält die vier Hauptkomponenten:

   1. `.appx` file
   1. Zertifikat (derzeit ein selbstsigniertes Zertifikat von Apache Cordova)
   1. Abhängigkeitsordner
   1. PowerShell-Datei (.ps1-Erweiterung)



## Bereitstellen einer App mit Windows PowerShell {#deploying-an-app-using-windows-powershell}

Es gibt zwei Möglichkeiten zum Installieren der Anwendung auf einem Windows-Gerät.

### Erwerb der Entwicklerlizenz {#by-acquiring-the-developer-license}

1. Right-click on the PowerShell file ( `Add-AppDevPackage.ps1)`, and choose **Run with PowerShell**.

1. Bei der Einrichtung werden Sie dazu aufgefordert, eine Entwicklerlizenz zu erwerben. Verwenden Sie die Microsoft-Kontoanmeldeinformationen zum Erwerben der Entwicklerlizenz.\
   Diese Lizenz ist für 30 Tage gültig, und Sie können Sie kostenlos verlängern.
1. Wenn Sie die Entwicklerlizenz erwerben, installiert das Setupprogramm das selbstsignierte Zertifikat auf dem System und die Anwendung wird erfolgreich installiert.

### Verwenden von unternehmenseigenen Geräten {#by-using-enterprise-owned-devices}

Für unternehmenseigene Geräte, die in die Unternehmensdomäne eingebunden sind, ist der Erwerb einer Entwicklerlizenz nicht erforderlich.

Unternehmenseigene Geräte verwenden die Professional und Enterprise Edition von Windows.

Microsoft empfiehlt das Installieren eines von einer vertrauenswürdigen Stelle ausgestellten öffentlichen Zertifikats, wie etwa VeriSign.

So stellen Sei die App bereit:

* Stellen Sie sicher, dass das Gerät in die Unternehmensdomäne eingebunden ist.
* Aktivieren Sie die Gruppenrichtlinien-Einstellung.

**So aktivieren Sie die Gruppenrichtlinien-Einstellung:**

1. In your device, run `gpedit.msc`.
1. Navigieren Sie zu **Computerkonfiguration > Administrative Vorlagen > Windows-Komponente > Bereitstellung von App-Paketen**.
1. Klicken Sie mit der rechten Maustaste auf **Installation aller vertrauenswürdigen Apps zulassen**.
1. Klicken Sie auf **Bearbeiten** und wählen Sie **Aktiviert**.

1. Klicken Sie auf **OK**.

Bearbeiten Sie das von Visual Studio generierte PowerShell-Skript, um zu verhindern, dass eine Entwicklerlizenz erworben wird.

In the PowerShell script, set the variable: `$NeedDeveloperLicense = $false`.

Für Geräte, die nicht in die Domäne eingebunden sind, ist ein Querladen des Produktaktivierungsschlüssels erforderlich. Diesen können Sie von einem Windows-Händler erwerben.

Für die Windows 8.1 Home Edition gibt es keine Gruppenrichtlinie, ein Querladen innerhalb des Unternehmens ist nicht zulässig und Sie können sie nicht in die Unternehmensdomäne einbinden. Stellen Sie die App mithilfe der Entwicklerlizenz auf einem Gerät mit Windows 8.1 Home Edition bereit.

Klicken Sie [hier](https://blogs.msdn.com/b/mvpawardprogram/archive/2014/03/24/side-loading-deployment-of-windows-store-apps-in-enterprises-step-by-step.aspx), um weitere Informationen zu erhalten.

## Bereitstellen einer App mit Visual Studio {#deploying-an-app-using-visual-studio}

So installieren Sie die App mit Visual Studio unter Windows:

1. Verbinden Sie das Gerät mithilfe von Remotedebugger.\
   For more information, see [Run Windows Store apps on a remote machine](https://docs.microsoft.com/en-us/visualstudio/debugger/run-windows-store-apps-on-a-remote-machine).

1. Wählen Sie, während Sie die App in Visual Studio geöffnet haben, in der Liste der Lösungsplattformen Windows-x64, Windows-x86 oder Windows-AnyCPU und wählen Sie anschließend **Remotecomputer**.
1. Ihre App wird auf dem Remotecomputer bereitgestellt.

