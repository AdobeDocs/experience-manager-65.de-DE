---
title: Einrichten des Xcode-Projekts und Erstellen der iOS-App
seo-title: Einrichten des Xcode-Projekts und Erstellen der iOS-App
description: Erklärt das Erstellen einer standardmäßigen AEM Forms-App für iOS.
seo-description: Erklärt das Erstellen einer standardmäßigen AEM Forms-App für iOS.
uuid: 29779bbb-06b4-4ece-9f29-786afab59eaf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 88555db2-712f-4ef9-bf47-76c7ba83d964
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 57%

---


# Einrichten des Xcode-Projekts und Erstellen der iOS-App{#set-up-the-xcode-project-and-build-the-ios-app}

In AEM Forms wird der vollständige Quellcode der AEM Forms-App bereitgestellt. Die Quelle enthält alle Komponenten, die für eine benutzerdefinierte AEM Forms-App erforderlich sind. Das Quellcode-Archiv `adobe-lc-mobileworkspace-src-<version>.zip` ist Teil des `adobe-aemfd-forms-app-src-pkg-<version>.zip` Pakets zur Softwareverteilung.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Open [Software Distribution](https://experience.adobe.com/downloads). Sie benötigen eine Adobe ID, um sich bei der Softwareverteilung anzumelden.
1. Tippen Sie auf **[!UICONTROL Adobe Experience Manager]** , der im Kopfzeilenmenü verfügbar ist.
1. In the **[!UICONTROL Filters]** section:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** .
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können die Ergebnisse auch mit der Option **[!UICONTROL Downloads]** suchen filtern.
1. Tippen Sie auf den Paketnamen, der auf Ihr Betriebssystem zutrifft, wählen Sie &quot;Endbenutzer-Lizenzbedingungen **[!UICONTROL akzeptieren&quot;]** und klicken Sie auf &quot; **[!UICONTROL Herunterladen]**&quot;.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf Paket **[!UICONTROL hochladen]** , um das Paket hochzuladen.
1. Select the package and click **[!UICONTROL Install]**.

1. Um das Quellcode-Archiv herunterzuladen, öffnen Sie `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` den Browser.
Das Quellpaket wird auf Ihr Gerät heruntergeladen.

The following image displays the extracted contents of the `adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content](assets/mws-content.png)

The following table details contents of the `adobe-lc-mobileworkspace-src-[version]/ios` folder.

<table>
 <tbody>
  <tr>
   <th><p>Ordner</p> </th>
   <th><p>Inhalt</p> </th>
  </tr>
  <tr>
   <td><p><code>CordovaLib</code></p> </td>
   <td><p>PhoneGap SDK 6.4.0</p> </td>
  </tr>
  <tr>
   <td><p><code>AEM Forms</code></p> </td>
   <td><p>Ressourcen, PhoneGap-Plug-Ins und das Hauptmodul der Anwendung</p> </td>
  </tr>
  <tr>
   <td><p><code>AEM Forms.xcodeproj</code></p> </td>
   <td><p>Xcode-Projekt für AEM Forms-App</p> </td>
  </tr>
  <tr>
   <td><p><code>www</code></p> </td>
   <td><p>HTML, CSS, Bilder und JavaScript-Dateien für das AEM Forms-App-Projekt</p> </td>
  </tr>
 </tbody>
</table>

Weitere Informationen zu Codesignaturen und zum Hinzufügen von Geräten im iOS Provisioning Portal finden Sie unter [iOS Code Signing Setup, Process, and Troubleshooting](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html).

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

1. Führen Sie die folgenden Schritte aus, um ein Projekt in Xcode einzurichten und eine signierende Identität anzugeben:

   Melden Sie sich bei Ihrem Mac-Computer an, auf dem Xcode und iOS SDK installiert und konfiguriert sind.

1. Copy the `adobe-lc-mobileworkspace-src-<version>.zip` archive from the downloads folder to `[User_Home]/Projects/`.
1. Extract the archive in the `[User_Home]/Projects/[your-project]`directory.
1. Navigieren Sie zum Ordner ` [User_Home]/Projects/ `[Ihres Projekts]`/adobe-lc-mobileworkspace-src-[version]/ios` .
1. Öffnen Sie das Projekt `AEM Forms.xcodeproj` in Xcode.
1. Klicken Sie auf **AEM Forms** und wählen Sie unter **TARGETS****AEM Forms**. Select the **Build Settings** tab, locate the **Code Signing Entitlement** section, and in Debug and Release fields do one of the following:

   * Um eine Standard-Mobile Workspace-App zu erstellen, machen Sie keine Angaben in den Feldern
   * Specify the fields to as explained in [Building a Secure AEM Forms app for iOS](/help/forms/using/building-secure-mobile-workspace-app.md) to build a secure AEM Forms app.

1. Klicken Sie auf der Registerkarte **Build Settings** auf **All** und anschließend auf **Combined**.
1. Erweitern Sie in der Liste **Settings** das Element **Code Signing**.
1. Wählen Sie für **Code Signing Identity** die entsprechende Signatur. For detailed information about, creating new signatures, see [Creating and Downloading Development Provisioning Profiles](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Achten Sie darauf, dass dieselbe Signatur für die Optionen **Debug**, **Release** und **Any iOS SDK** ausgewählt wird.
1. Replace the following code in the `AEM Forms-info.plist` file:

   ```xml
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSAllowsArbitraryLoads</key>
   <true/>
   </dict>
   ```

   durch den folgenden, wenn Sie `yourserver.com` durch den entsprechenden Hostnamen für Ihren Server ersetzen.

   ```xml
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSExceptionDomains</key>
   <dict>
   <key>yourserver.com</key>
   <dict>
   <!-Include to allow subdomains->
   <key>NSIncludesSubdomains</key>
   <true/>
   <!-Include to allow HTTP requests->
   <key>NSTemporaryExceptionAllowsInsecureHTTPLoads</key>
   <true/>
   <!-Include to support forward secrecy->
   <key>NSExceptionRequiresForwardSecrecy</key>
   <false/>
   <!-Include to specify minimum TLS version->
   <key>NSTemporaryExceptionMinimumTLSVersion</key>
   <string>TLSv1.1</string>
   </dict>
   </dict>
   </dict>
   ```

   >[!NOTE]
   >
   >Dieser Schritt ist nur erforderlich, wenn die AEM Forms-App eine Verbindung zu einem Server herstellen muss, der nicht den App Transport Security-Anforderungen entspricht.

1. Under **PROJECT**, select **AEM Forms** and ensure that the appropriate signature is selected for **Code Signing Identity**, **Debug**, **Release** and **Any iOS SDK**.
1. Verbinden Sie ein provisioniertes iPad mit einem Mac-Computer.
1. Select the provisioned device for the **AEM Forms** project.

   ![ipad](assets/ipad.png)

   Ein provisioniertes Gerät (iPad Air 2) ist ausgewählt.

1. Wählen Sie **Product** > **Clean**.
1. Wählen Sie **Product** > **Build**.

## Installationsprogramm für die AEM Forms-App erstellen {#build-the-installer-for-the-mobile-workspace-app}

Sie müssen das Xcode-Projekt archivieren, um das Installationsprogramm (eine .ipa-Datei) und eine Eigenschaftslistendatei (eine .plist-Datei) zu erstellen. Die Eigenschaftslistendatei enthält Konfigurationsinformationen der gehosteten internen App, z. B. den Namen und den Hostingort der App. Weitere Informationen zur Eigenschaftslistendatei finden Sie unter [About Information Property List Files](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Verbinden Sie ein provisioniertes iPad mit einem Mac-Computer. For detailed information about provisioning an iPad, see [Creating and Downloading Development Provisioning Profiles](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html)
1. Select the provisioned device for the **AEM Forms** project.

   ![ipad-1](assets/ipad-1.png)

   Ein provisioniertes Gerät (iPad Air 2) ist ausgewählt.

1. Wählen Sie **Product** > **Clean**.
1. Wählen Sie **Product** > **Build**.
1. Wählen Sie **Product** > **Archive**.
1. Wählen Sie in Organizer unter „Archives“ das neueste Archiv Ihres Projekts aus und klicken Sie auf **Distribute**.
1. Wählen Sie die Verteilungsmethode **Save for Enterprise or Ad-Hoc Deployment** und klicken Sie auf **Next**.
1. Wählen Sie die entsprechende Option unter **Code Signing Identity** und klicken Sie auf **Next**. Klicken Sie auf **Allow**, um die Signatur anzuwenden.
1. Geben Sie den Namen der App an und wählen Sie **Save for Enterprise Distribution**.
1. Geben Sie im Feld **Application URL** die URL für die App an. Um die App beispielsweise auf einem CRX-Server zu hosten, geben Sie die URL an `https://[LC_host]:'port'/lc/content/distribution/mobileworkspace/APP_NAME.ipa`.
1. Geben Sie im Feld **Titel** AEM Forms an.
1. Klicken Sie auf **Save** und schließen Sie Xcode.

   Die Installationsprogrammdatei `AEM Forms.ipa` und die Eigenschaftslistendatei `AEM Forms-info.plist` werden am angegebenen Speicherort erstellt.

1. Öffnen Sie die `AEM Forms-info.plist` Datei in einem Editor.
1. Ersetzen Sie alle Leerzeichen in der URL der .ipa-Datei durch %20.
1. Save and close the `AEM Forms-info.plist` file.