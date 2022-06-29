---
title: Single Sign-On und Zeitüberschreitungshandler
seo-title: Single Sign On and timeout handlers
description: Gehen Sie wie folgt vor, um einen Sitzungs-Timeout-Wert für AEM Forms festzulegen.
seo-description: How-to set the session timeout value for AEM Forms workspace.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
exl-id: 4f824d80-f3f8-4010-9583-5a9ab1151a7b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '189'
ht-degree: 100%

---

# Single Sign-On und Zeitüberschreitungshandler {#single-sign-on-and-timeout-handlers}

AEM Forms Workspace ist SSO-fähig. Wenn sich ein Benutzer bei einer AEM Forms-Anwendung wie Forms Manager, der PDF Generator-Benutzeroberfläche oder AEM Forms-Arbeitsbereich angemeldet hat und in derselben Browsersitzung auf AEM Forms-Arbeitsbereich zugreift, wird der Benutzer bei AEM Forms-Arbeitsbereich angemeldet und umgekehrt.

## Das Bearbeiten des Serverzeitlimits in AEM Forms bildet Arbeitsbereich {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Sitzungs-Timeouts für einen Benutzer können in der Administration Console konfiguriert werden.

Um den Timeout festzulegen, melden Sie sich bei `https://'[server]:[port]'/adminui` an, navigieren zu **Einstellungen > Benutzerverwaltung > Konfiguration > Erweiterte Systemattribute konfigurieren** und nehmen die gewünschten Einstellungen vor.

In AEM Forms wird die Zeitüberschreitung im Arbeitsbereich wie folgt behandelt:

* Die Sitzungsdauer für einen Benutzer ist in der Antwort auf den Aufruf `initialize` verfügbar, der die Benutzersitzung initialisiert.
* Ein Popup-Fenster informiert den Benutzer 15 Sekunden im Voraus, dass die Sitzung gleich ablaufen wird.

In diesem Popup-Dialog:

* Klicken Sie auf „OK“, um die Benutzersitzung zu beenden.
* Klicken Sie auf „Abbrechen“, um die Benutzersitzung neu zu initialisieren.

>[!NOTE]
>
>Wird keine Aktion ausgeführt, wird der Benutzer drei Sekunden vor Ablauf der Sitzung automatisch vom AEM Forms-Arbeitsbereich abgemeldet.
