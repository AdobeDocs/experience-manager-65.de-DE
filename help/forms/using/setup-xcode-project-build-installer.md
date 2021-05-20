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
exl-id: 78ce6107-8821-47d6-86ab-7ab968945e7c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 64%

---

# Einrichten des Xcode-Projekts und Erstellen der iOS-App{#set-up-the-xcode-project-and-build-the-ios-app}

In AEM Forms wird der vollständige Quellcode der AEM Forms-App bereitgestellt. Die Quelle enthält alle Komponenten, die für eine benutzerdefinierte AEM Forms-App erforderlich sind. Das Quellcode-Archiv `adobe-lc-mobileworkspace-src-<version>.zip` ist Teil des `adobe-aemfd-forms-app-src-pkg-<version>.zip`-Pakets auf Softwareverteilung.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads suchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den Paketnamen für Ihr Betriebssystem, wählen Sie **[!UICONTROL Endbenutzer-Lizenzbedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Um das Quellcode-Archiv herunterzuladen, öffnen Sie `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in Ihrem Browser.
Das Quellpaket wird auf Ihr Gerät heruntergeladen.

Die folgende Abbildung zeigt den extrahierten Inhalt von `adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content](assets/mws-content.png)

Die folgende Tabelle zeigt den Inhalt des Ordners `adobe-lc-mobileworkspace-src-[version]/ios` .

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

1. Kopieren Sie das Archiv `adobe-lc-mobileworkspace-src-<version>.zip` aus dem Ordner Downloads nach `[User_Home]/Projects/`.
1. Extrahieren Sie das Archiv im Verzeichnis `[User_Home]/Projects/[your-project]`.
1. Navigieren Sie zum Verzeichnis ` [User_Home]/Projects/ `[your-project]`/adobe-lc-mobileworkspace-src-[version]/ios` .
1. Öffnen Sie das Projekt `AEM Forms.xcodeproj` in Xcode.
1. Klicken Sie auf **AEM Forms** und wählen Sie unter **TARGETS****AEM Forms**. Wählen Sie die Registerkarte **Build Settings**, suchen Sie den Abschnitt **Code Signing Entitlement** und führen Sie in den Feldern Debuggen und Freigeben einen der folgenden Schritte aus:

   * Um eine Standard-Mobile Workspace-App zu erstellen, machen Sie keine Angaben in den Feldern
   * Geben Sie die Felder an, wie unter [Erstellen einer sicheren AEM Forms-App für iOS](/help/forms/using/building-secure-mobile-workspace-app.md) beschrieben, um eine sichere AEM Forms-App zu erstellen.

1. Klicken Sie auf der Registerkarte **Build Settings** auf **All** und anschließend auf **Combined**.
1. Erweitern Sie in der Liste **Settings** das Element **Code Signing**.
1. Wählen Sie für **Code Signing Identity** die entsprechende Signatur. Detaillierte Informationen zum Erstellen neuer Signaturen finden Sie unter [Erstellen und Herunterladen von Entwicklungsbereitstellungsprofilen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Achten Sie darauf, dass dieselbe Signatur für die Optionen **Debug**, **Release** und **Any iOS SDK** ausgewählt wird.
1. Ersetzen Sie den folgenden Code in der Datei `AEM Forms-info.plist` :

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

1. Wählen Sie unter **PROJECT** **AEM Forms** und stellen Sie sicher, dass die entsprechende Signatur für **Code Signing Identity**, **Debug**, **Release** und **Any iOS SDK** ausgewählt ist.
1. Verbinden Sie ein provisioniertes iPad mit einem Mac-Computer.
1. Wählen Sie das bereitgestellte Gerät für das Projekt **AEM Forms** aus.

   ![ipad](assets/ipad.png)

   Ein provisioniertes Gerät (iPad Air 2) ist ausgewählt.

1. Wählen Sie **Product** > **Clean**.
1. Wählen Sie **Product** > **Build**.

## Installationsprogramm für die AEM Forms-App erstellen {#build-the-installer-for-the-mobile-workspace-app}

Sie müssen das Xcode-Projekt archivieren, um das Installationsprogramm (eine .ipa-Datei) und eine Eigenschaftslistendatei (eine .plist-Datei) zu erstellen. Die Eigenschaftslistendatei enthält Konfigurationsinformationen der gehosteten internen App, z. B. den Namen und den Hostingort der App. Weitere Informationen zur Eigenschaftslistendatei finden Sie unter [About Information Property List Files](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Verbinden Sie ein provisioniertes iPad mit einem Mac-Computer. Ausführliche Informationen zur Bereitstellung eines iPads finden Sie unter [Erstellen und Herunterladen von Entwicklungsbereitstellungsprofilen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html)
1. Wählen Sie das bereitgestellte Gerät für das Projekt **AEM Forms** aus.

   ![ipad-1](assets/ipad-1.png)

   Ein provisioniertes Gerät (iPad Air 2) ist ausgewählt.

1. Wählen Sie **Product** > **Clean**.
1. Wählen Sie **Product** > **Build**.
1. Wählen Sie **Product** > **Archive**.
1. Wählen Sie in Organizer unter „Archives“ das neueste Archiv Ihres Projekts aus und klicken Sie auf **Distribute**.
1. Wählen Sie die Verteilungsmethode **Save for Enterprise or Ad-Hoc Deployment** und klicken Sie auf **Next**.
1. Wählen Sie die entsprechende Option unter **Code Signing Identity** und klicken Sie auf **Next**. Klicken Sie auf **Allow**, um die Signatur anzuwenden.
1. Geben Sie den Namen der App an und wählen Sie **Save for Enterprise Distribution**.
1. Geben Sie im Feld **Application URL** die URL für die App an. Um beispielsweise die App auf einem CRX-Server zu hosten, geben Sie die URL `https://[LC_host]:'port'/lc/content/distribution/mobileworkspace/APP_NAME.ipa` an.
1. Geben Sie im Feld **Titel** AEM Forms an.
1. Klicken Sie auf **Save** und schließen Sie Xcode.

   Die Installationsprogrammdatei `AEM Forms.ipa` und die Eigenschaftslistendatei `AEM Forms-info.plist` werden am angegebenen Speicherort erstellt.

1. Öffnen Sie die Datei `AEM Forms-info.plist` in einem Editor.
1. Ersetzen Sie alle Leerzeichen in der URL der .ipa-Datei durch %20.
1. Speichern und schließen Sie die Datei `AEM Forms-info.plist`.
