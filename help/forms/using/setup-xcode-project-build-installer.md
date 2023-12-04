---
title: Einrichten des Xcode-Projekts und Erstellen der iOS-App
seo-title: Set up the Xcode project and build the iOS app
description: Erklärt, wie Sie eine standardmäßige AEM Forms-App für iOS erstellen.
seo-description: Explains how to build standard AEM Forms app for iOS.
uuid: 29779bbb-06b4-4ece-9f29-786afab59eaf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 88555db2-712f-4ef9-bf47-76c7ba83d964
docset: aem65
exl-id: 78ce6107-8821-47d6-86ab-7ab968945e7c
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 70%

---

# Einrichten des Xcode-Projekts und Erstellen der iOS-App{#set-up-the-xcode-project-and-build-the-ios-app}

In AEM Forms wird der vollständige Quellcode der AEM Forms-App bereitgestellt. Die Quelle enthält alle Komponenten zum Erstellen einer benutzerdefinierten AEM Forms-App. Das Quell-Code-Archiv `adobe-lc-mobileworkspace-src-<version>.zip` ist Bestandteil des `adobe-aemfd-forms-app-src-pkg-<version>.zip`-Pakets auf Software Distribution.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Auswählen **[!UICONTROL Adobe Experience Manager]** im Kopfzeilenmenü verfügbar.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen aus und wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und wählen Sie **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

1. Öffnen Sie `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in Ihrem Browser, um das Quell-Code-Archiv herunterzuladen.
Das Quellpaket wird auf Ihr Gerät heruntergeladen.

Die folgende Abbildung zeigt den extrahierten Inhalt von `adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content](assets/mws-content.png)

Die folgende Tabelle zeigt Details zum Inhalt des Ordners „`adobe-lc-mobileworkspace-src-[version]/ios`“ an.

<table>
 <tbody>
  <tr>
   <th><p>Verzeichnis</p> </th>
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

1. Kopieren Sie das Archiv `adobe-lc-mobileworkspace-src-<version>.zip` aus dem Downloads-Ordner nach `[User_Home]/Projects/`.
1. Extrahieren Sie das Archiv im Verzeichnis `[User_Home]/Projects/[your-project]`.
1. Navigieren Sie zum Verzeichnis ` [User_Home]/Projects/ `[Ihr Projekt]`/adobe-lc-mobileworkspace-src-[version]/ios`.
1. Öffnen Sie das Projekt `AEM Forms.xcodeproj` in Xcode.
1. Klicken Sie auf **AEM Forms** und wählen Sie unter **TARGETS** die Option **AEM Forms**. Wählen Sie die Registerkarte **Build-Einstellungen**, suchen Sie den Abschnitt **Code Signing-Berechtigung** und führen Sie in den Feldern „Debugging“ und „Freigeben“ einen der folgenden Schritte aus:

   * Um eine Standard-Mobile Workspace-App zu erstellen, machen Sie keine Angaben in den Feldern
   * Um ein sicheres AEM Forms-Programm zu erstellen, füllen Sie die Felder aus wie unter [Erstellen eines sicheren AEM Forms-Programms für iOS](/help/forms/using/building-secure-mobile-workspace-app.md) beschrieben.

1. Im **Build-Einstellungen** Registerkarte, klicken **Alle** und klicken Sie anschließend auf **Kombiniert**.
1. Aus dem **Einstellungen** Liste, erweitern **Code-Signierung**.
1. Wählen Sie für **Code Signing Identity** die entsprechende Signatur. Weitere Informationen zum Erstellen neuer Signaturen erhalten Sie unter [Erstellen und Herunterladen von Entwicklungsbereitstellungsprofilen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Achten Sie darauf, dass dieselbe Signatur für die Optionen **Debug**, **Release** und **Any iOS SDK** ausgewählt wird.
1. Ersetzen Sie den folgenden Code in der Datei `AEM Forms-info.plist`: 

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
   >Dieser Schritt ist nur erforderlich, wenn das AEM Forms-Programm eine Verbindung zu einem Server herstellen muss, der nicht den App Transport Security-Anforderungen entspricht.

1. Wählen Sie unter **PROJEKT** die Option **AEM Forms** aus und vergewissern Sie sich, dass die entsprechende Signatur für **Code Signing Identity**, **Debugging**, **Freigabe** und **Alle iOS-SDKs** ausgewählt ist.
1. Verbinden Sie ein provisioniertes iPad mit einem Mac-Computer.
1. Wählen Sie das provisionierte Gerät für das **AEM Forms**-Projekt.

   ![iPad](assets/ipad.png)

   Ein provisioniertes Gerät, iPad Air 2, ist ausgewählt.

1. Auswählen **Produkt** > **Clean**.
1. Auswählen **Produkt** > **Build**.

## Installationsprogramm für die AEM Forms-App erstellen {#build-the-installer-for-the-mobile-workspace-app}

Sie müssen das Xcode-Projekt archivieren, um das Installationsprogramm (eine .ipa-Datei) und eine Eigenschaftenlistendatei (eine .plist-Datei) zu erstellen. Die Eigenschaftenlistendatei enthält Konfigurationsinformationen der gehosteten internen App, z. B. den Namen und den Hosting-Speicherort der App. Weitere Informationen zur Eigenschaftslistendatei finden Sie unter [Informationen zu Listen-Dateien für Eigenschaften](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Verbinden Sie ein provisioniertes iPad mit einem Mac-Computer. Ausführliche Informationen für die Bereitstellung eines iPads finden Sie unter [Erstellen und Herunterladen von Entwicklungsbereitstellungsprofilen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Wählen Sie das provisionierte Gerät für das **AEM Forms**-Projekt.

   ![iPad-1](assets/ipad-1.png)

   Ein provisioniertes Gerät, iPad Air 2, ist ausgewählt.

1. Auswählen **Produkt** > **Clean**.
1. Auswählen **Produkt** > **Build**.
1. Auswählen **Produkt** > **Archivieren**.
1. Wählen Sie in Organizer - Archives das neueste Archiv Ihres Projekts aus und klicken Sie auf **Verteilen**.
1. Auswählen **Für Enterprise- oder Ad-hoc-Bereitstellung speichern** als Verteilungsmethode und klicken Sie auf **Nächste**.
1. Wählen Sie die entsprechende **Code Signing Identity** und klicken **Nächste**. Klicks **Zulassen** , um die Signatur anzuwenden.
1. Geben Sie den Namen der App an und wählen Sie **Save for Enterprise Distribution**.
1. Stellen Sie die **Anwendungs-URL** für die App. Um beispielsweise das Programm auf einem CRX-Server zu hosten, geben Sie die URL `https://[LC_host]:'port'/lc/content/distribution/mobileworkspace/APP_NAME.ipa` an.
1. Im **Titel** -Feld, geben Sie AEM Forms an.
1. Klicks **Speichern** und schließen Sie Xcode.

   Die Installationsprogrammdatei `AEM Forms.ipa` und die Eigenschaftslistendatei `AEM Forms-info.plist` werden am angegebenen Speicherort erstellt.

1. Öffnen Sie die Datei `AEM Forms-info.plist` in einem Editor.
1. Ersetzen Sie alle Leerzeichen in der URL der .ipa-Datei durch %20.
1. Speichern und schließen Sie die Datei `AEM Forms-info.plist`.
