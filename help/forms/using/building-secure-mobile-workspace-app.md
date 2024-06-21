---
title: Erstellen einer sicheren AEM Forms-App für iOS
description: Erfahren Sie, wie Sie durch Archivieren des Xcode-Projekts eine sichere AEM Forms-App für iOS erstellen. Dadurch werden ein Installationsprogramm (eine .ipa-Datei) und eine Eigenschaftslistendatei (eine .plist-Datei) erstellt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 12cc2027-ae94-40c3-a7d1-553469426114
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 100%

---

# Erstellen einer sicheren AEM Forms-App für iOS {#building-a-secure-aem-forms-app-for-ios}

Sie müssen das Xcode-Projekt für die AEM Forms-App archivieren, um das Installationsprogramm (eine .ipa-Datei) und eine Eigenschaftslistendatei (eine .plist-Datei) zu erstellen. Die Eigenschaftslistendatei enthält Konfigurationsinformationen der gehosteten internen App, wie den Namen und den Hosting-Speicherort der App. Weitere Informationen zur Eigenschaftslistendatei finden Sie unter [Informationen zu Eigenschaftslistendateien](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Melden Sie sich bei der folgenden Website an:

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Erstellen Sie eine App-ID. Ausführliche Schritte zum Erstellen einer App-ID finden Sie unter [Erstellen und Konfigurieren von App-IDs](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Um die Bundle-Kennung für die iOS-Anwendung für Ihre App zu konfigurieren, klicken Sie auf **[!UICONTROL App-ID konfigurieren]**.
1. Wählen Sie unten auf der Web-Seite **[!UICONTROL Für Datenschutz aktivieren]** aus. Geben Sie die Datenschutzoptionen an.

   Klicken Sie auf **[!UICONTROL Fertig]**.

1. Navigieren Sie zu „Bereitstellung“ > „Verteilung“ und erstellen Sie ein neues Profil mit der in Schritt 3 konfigurierten App-ID.
1. Laden Sie das Profil für die Bereitstellung herunter und fügen Sie es zum Xcode und iPad hinzu.
1. Melden Sie sich bei Ihrem Mac-Computer an, auf dem Xcode und iOS SDK installiert und konfiguriert sind.
1. Öffnen Sie das Projekt `AEM Forms.xcodeproj` in Xcode.
1. Klicken Sie auf **[!UICONTROL AEM Forms]** und wählen Sie unter **[!UICONTROL TARGETS]** die Option **[!UICONTROL AEM Forms]**. Wählen Sie die Registerkarte **[!UICONTROL Build-Einstellungen]**, suchen Sie den Abschnitt **[!UICONTROL Code Signing- Berechtigung]** und wählen Sie in der Dropdown-Liste „Berechtigungen“ die Option **[!UICONTROL LC Enterprise]**.
1. Suchen und öffnen Sie die Datei `LC Enterprise.entitlements` im Xcode zur Bearbeitung. Fügen Sie unter **XCode-Berechtigungen** dasselbe Schlüssel-/Wert-Paar hinzu, das in Ihrem Bereitstellungsprofil vorhanden ist.
1. Klicken Sie auf der Registerkarte **[!UICONTROL Build-Einstellungen]** auf **[!UICONTROL Alle]** und dann auf **[!UICONTROL Kombiniert]**.
1. Erweitern Sie auf der Liste **[!UICONTROL Einstellungen]** die Option **[!UICONTROL Code-Signierung]**.
1. Wählen Sie für **[!UICONTROL Code Signing Identity]** die entsprechende Signatur. Achten Sie darauf, dass dieselbe Signatur für die Optionen **[!UICONTROL Debug]**, **[!UICONTROL Release]** und **[!UICONTROL Any iOS SDK]** ausgewählt wird.
1. Wählen Sie unter **[!UICONTROL PROJEKT]** die Option **[!UICONTROL AEM Forms]** und stellen Sie sicher, dass die entsprechende Signatur für **[!UICONTROL Code Signing Identity]**, **[!UICONTROL Debug]**, **[!UICONTROL Release]** und **[!UICONTROL Any iOS SDK]** ausgewählt ist.
1. Erstellen Sie die AEM Forms-App und stellen Sie sie bereit. Detaillierte Anweisungen zur Erstellung und Bereitstellung der AEM Forms-App finden Sie unter [Erstellen des Installationsprogramms für die AEM Forms-App](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app).
