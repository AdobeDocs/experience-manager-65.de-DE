---
title: Erstellen einer sicheren AEM Forms-App für iOS
description: Erfahren Sie, wie Sie eine sichere AEM Forms-App für iOS erstellen, indem Sie das Xcode-Projekt archivieren. Dadurch werden das Installationsprogramm (eine .ipa-Datei) und die Eigenschaftenliste (eine .plist-Datei) erstellt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 12cc2027-ae94-40c3-a7d1-553469426114
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 49%

---

# Erstellen einer sicheren AEM Forms-App für iOS {#building-a-secure-aem-forms-app-for-ios}

Sie müssen das Xcode-Projekt für die AEM Forms-App archivieren, um das Installationsprogramm (eine .ipa-Datei) und eine Eigenschaftenlistendatei (eine .plist-Datei) zu erstellen. Die Eigenschaftenlistendatei enthält Konfigurationsinformationen der gehosteten internen App, z. B. den Namen und den Hosting-Speicherort der App. Weitere Informationen zur Eigenschaftslistendatei finden Sie unter [Informationen zu Listen-Dateien für Eigenschaften](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Melden Sie sich bei der folgenden Website an:

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Erstellen Sie eine App-ID. Detaillierte Schritte zum Erstellen einer App-ID finden Sie unter [Erstellen und Konfigurieren von App-IDs](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Um die Bundle-ID für die iOS-Anwendung für Ihre App zu konfigurieren, klicken Sie auf **[!UICONTROL App-ID konfigurieren]**.
1. Wählen Sie unten auf der Webseite die Option **[!UICONTROL Aktivieren für den Datenschutz]**. Legen Sie die Datenschutzoptionen fest.

   Klicken Sie auf **[!UICONTROL Fertig]**.

1. Navigieren Sie zu Bereitstellung > Verteilung und erstellen Sie ein neues Profil mit der in Schritt 3 konfigurierten App-ID.
1. Laden Sie das Profil für die Bereitstellung herunter und fügen Sie es zum Xcode und iPad hinzu.
1. Melden Sie sich bei Ihrem Mac-Computer an, auf dem Xcode und iOS SDK installiert und konfiguriert sind.
1. Öffnen Sie das Projekt `AEM Forms.xcodeproj` in Xcode.
1. Klicken Sie auf **[!UICONTROL AEM Forms]** und wählen Sie unter **[!UICONTROL TARGETS]** die Option **[!UICONTROL AEM Forms]**. Wählen Sie die Registerkarte **[!UICONTROL Build-Einstellungen]**, suchen Sie den Abschnitt **[!UICONTROL Code Signing- Berechtigung]** und wählen Sie in der Dropdown-Liste „Berechtigungen“ die Option **[!UICONTROL LC Enterprise]**.
1. Suchen und öffnen Sie die Datei `LC Enterprise.entitlements` im Xcode zur Bearbeitung. Fügen Sie unter **XCode-Berechtigungen** dasselbe Schlüssel-/Wert-Paar hinzu, das in Ihrem Bereitstellungsprofil vorhanden ist.
1. Im **[!UICONTROL Build-Einstellungen]** Registerkarte, klicken **[!UICONTROL Alle]** und klicken Sie anschließend auf **[!UICONTROL Kombiniert]**.
1. Aus dem **[!UICONTROL Einstellungen]** Liste, erweitern **[!UICONTROL Code-Signierung]**.
1. Wählen Sie für **[!UICONTROL Code Signing Identity]** die entsprechende Signatur. Achten Sie darauf, dass dieselbe Signatur für die Optionen **[!UICONTROL Debug]**, **[!UICONTROL Release]** und **[!UICONTROL Any iOS SDK]** ausgewählt wird.
1. Wählen Sie unter **[!UICONTROL PROJEKT]** die Option **[!UICONTROL AEM Forms]** und stellen Sie sicher, dass die entsprechende Signatur für **[!UICONTROL Code Signing Identity]**, **[!UICONTROL Debug]**, **[!UICONTROL Release]** und **[!UICONTROL Any iOS SDK]** ausgewählt ist.
1. Erstellen Sie die AEM Forms-App und stellen Sie sie bereit. Detaillierte Anweisungen zur Erstellung und Bereitstellung der AEM Forms-App finden Sie unter [Erstellen des Installationsprogramms für die AEM Forms-App](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app).
