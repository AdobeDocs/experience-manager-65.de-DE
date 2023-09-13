---
title: Bereitstellen der AEM Forms-App
description: Verwenden Sie Mobile Device Management (MDM) für die Bereitstellung von Apps auf Mobilgeräten im großen Stil.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 375cfa95-ac6f-44c4-a736-f5dd55d24195
source-git-commit: 474a726058b141985f52a0faec6161a34be1e9dc
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 15%

---

# Verteilen der AEM Forms-App {#distribute-aem-forms-app}

Mobile Device Management (MDM) ermöglicht die Bereitstellung von Apps auf Mobilgeräten im großen Stil.

>[!NOTE]
>
>Diese Distribution ist nur für iOS- und Android™-Geräte verfügbar.

## Hauptfunktionen, die von MDM-Lösungen bereitgestellt werden: {#main-features-generally-provided-by-mdm-solutions}

* Aktivieren der Geräte-Einschreibung in der Unternehmensumgebung
* Zulassen der Konfiguration und Aktualisierung von Geräte-Einstellungen
* Erzwingen Sie die Sicherheitskompatibilität.
* Sicherer mobiler Zugriff auf Unternehmensressourcen

Mit einer MDM-Lösung sowie Mobile Application Management können Sie interne, öffentliche und erworbene Apps auf allen Mobilgeräten in Ihrem Unternehmen verwalten.

Der MDM-Administrator kann sowohl IPA- als auch APK-Dateien auf den MDM-Server hochladen und die Benutzer steuern, die auf die IPA- oder APK-Dateien zugreifen können. Der Administrator kann auch die Profileinstellungen für die einzelnen Anwendungen steuern.

## Profileinstellungen mit Auswirkung auf die AEM Forms-App {#profile-settings-affecting-the-aem-forms-app-br}

Die folgenden Profileinstellungen auf Ihrem Gerät wirken sich auf die Funktion der AEM Forms-App auf Ihrem Gerät aus:

* **Verwendung der Kamera zulassen** im **Gerätefunktionalität** Abschnitt

Wenn Sie **Verwendung der Kamera zulassen**, die Kamerafunktion der [Fotoannotation](/help/forms/using/add-attachments.md) funktioniert nicht. Aktivieren Sie diese Option, um die Kamera in der App zu verwenden.

* **Require passcode on device** im Abschnitt &quot;Passcode-Richtlinien&quot;

Aktivieren **Verschlüsselung von Anwendungsdaten** wird empfohlen, die **passcode** auf Ihrem Gerät. Wenn der Passcode nicht auf dem Gerät festgelegt ist, werden die auf dem Gerät gespeicherten Anwendungsdaten nicht verschlüsselt.
