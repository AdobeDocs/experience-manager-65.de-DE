---
title: Bereitstellen der AEM Forms-App
seo-title: Distribute AEM Forms app
description: Mobile Device Management (MDM) ermöglicht die Bereitstellung von Apps für mobile Geräte im großen Stil.
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: 375cfa95-ac6f-44c4-a736-f5dd55d24195
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '243'
ht-degree: 100%

---

# Bereitstellen der AEM Forms-App {#distribute-aem-forms-app}

Mobile Device Management (MDM) ermöglicht die Bereitstellung von Apps für mobile Geräte im großen Stil.

>[!NOTE]
>
>Die Bereitstellung ist nur für iOS- und Android-Geräte möglich.

## Die folgenden Hauptmerkmale werden im Allgemeinen durch MDM-Lösungen bereitgestellt: {#main-features-generally-provided-by-mdm-solutions}

* Aktivieren der Geräte-Einschreibung in der Unternehmensumgebung
* Zulassen der Konfiguration und Aktualisierung von Geräte-Einstellungen
* Erzwingen Sie die Sicherheitskompatibilität.
* Sicherer mobiler Zugriff auf Unternehmensressourcen

Eine MDM-Lösung ermöglicht Ihnen zusammen mit Mobile Application Management, interne, öffentliche und erworbene Apps auf den mobilen Geräten in Ihrem Unternehmen zu verwalten.

Der MDM-Administrator kann IPA- und APK-Dateien auf den MDM-Server hochladen und steuern, welche Benutzer auf die IPA- bzw. APK-Dateien zugreifen können. Der Administrator kann auch die Profileinstellung für die einzelnen Anwendungen steuern.

## Profileinstellungen mit Auswirkung auf die AEM Forms-App {#profile-settings-affecting-the-aem-forms-app-br}

Die folgenden Profileinstellungen auf Ihrem Gerät wirken sich auf die Funktion der Mobile App von AEM Forms auf dem Gerät aus:

* **Allow use of camera** im Abschnitt **Device functionality**

Wenn Sie die Option **Allow use of camera** deaktivieren, funktioniert die Kamera für [Photograph annotation](/help/forms/using/add-attachments.md) nicht. Sie müssen diese Option aktivieren, um die Kamera in der App verwenden zu können.

* **Require passcode on device** im Abschnitt „Passcode policies“

Um die **Verschlüsselung von Anwendungsdaten** zu aktivieren, sollten Sie die **Code-Sperre** auf dem Gerät aktivieren. Wenn auf dem Gerät keine Code-Sperre festgelegt ist, werden auf dem Gerät gespeicherte Anwendungsdaten nicht verschlüsselt.
