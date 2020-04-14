---
title: Erstellen einer sicheren AEM Forms-App für iOS
seo-title: Erstellen einer sicheren AEM Forms-App für iOS
description: Schritte zum Erstellen einer sicheren AEM Forms-App.
seo-description: Schritte zum Erstellen einer sicheren AEM Forms-App.
uuid: 6c4b160f-4d0c-4976-9609-9196795b6c8e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 90cd8ba5-4f47-4074-bc54-6a7bb8afe256
translation-type: tm+mt
source-git-commit: 49da3dbe590f70b98185a6bc330db6077dc864c0

---


# Erstellen einer sicheren AEM Forms-App für iOS {#building-a-secure-aem-forms-app-for-ios}

Sie müssen das Xcode-Projekt für AEM Forms-App archivieren, um das Installationsprogramm (eine .ipa-Datei) und eine Eigenschaftslistendatei (eine .plist-Datei) zu erstellen. Die Eigenschaftslistendatei enthält Konfigurationsinformationen der gehosteten internen App, z. B. den Namen und den Hostingort der App. Weitere Informationen zur Eigenschaftslistendatei finden Sie unter [About Information Property List Files](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Melden Sie sich bei der folgenden Webseite an:

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Erstellen Sie eine App-ID. Eine detaillierte Beschreibung zur Erstellung einer App-ID finden Sie unter [Erstellen und Konfigurieren von App-IDs](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Um den Bundle-Identifier für die iOS-Anwendung für Ihre App zu konfigurieren, klicken Sie auf **[!UICONTROL Configure App ID]**.
1. Wählen Sie unten auf der Webseite **[!UICONTROL Enable for Data Protection]**. Geben Sie die Datenschutzoptionen ein.

   Klicken Sie auf **[!UICONTROL Fertig]**.

1. Navigieren Sie zu „Provisioning->Distribution“ und erstellen Sie ein neues Profil mit der App-ID, die in Schritt 3 konfiguriert wurde.
1. Laden Sie das Profil für die Bereitstellung herunter und fügen Sie es zum Xcode und iPad hinzu.
1. Melden Sie sich bei Ihrem Mac-Computer an, auf dem Xcode und iOS SDK installiert und konfiguriert sind.
1. Öffnen Sie das Projekt `AEM Forms.xcodeproj` in Xcode.
1. Klicken Sie auf **[!UICONTROL AEM Forms]** und wählen Sie unter **[!UICONTROL TARGETS]****[!UICONTROL AEM Forms]**. Select the **[!UICONTROL Build Settings]** tab, locate the **[!UICONTROL Code Signing Entitlement]** section and in the Entitlements dropdown, select the **[!UICONTROL LC Enterprise]** option.
1. Suchen und öffnen Sie die Datei `LC Enterprise.entitlements` im Xcode zur Bearbeitung. Under the **XCode entitlements**, add the same key-value pair as present in your provisioning profile.
1. Klicken Sie auf der Registerkarte **[!UICONTROL Build Settings]** auf **[!UICONTROL All]** und anschließend auf **[!UICONTROL Combined]**.
1. Erweitern Sie in der Liste **[!UICONTROL Settings]** das Element **[!UICONTROL Code Signing]**.
1. Wählen Sie für **[!UICONTROL Code Signing Identity]** die entsprechende Signatur. Achten Sie darauf, dass dieselbe Signatur für die Optionen **[!UICONTROL Debug]**, **[!UICONTROL Release]** und **[!UICONTROL Any iOS SDK]** ausgewählt wird.
1. Under **[!UICONTROL PROJECT]**, select **[!UICONTROL AEM Forms]** and ensure that the appropriate signature is selected for **[!UICONTROL Code Signing Identity]**, **[!UICONTROL Debug]**, **[!UICONTROL Release]** and **[!UICONTROL Any iOS SDK]**.
1. Erstellen Sie die AEM Forms-App und stellen Sie sie bereit. Detaillierte Anweisungen zur Erstellung und Bereitstellung der AEM Forms-App finden Sie unter [Erstellen des Installationsprogramms für die AEM Forms-App](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app).
