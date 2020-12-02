---
title: Single Sign-On und Zeitüberschreitungshandler
seo-title: Single Sign-On und Zeitüberschreitungshandler
description: Gehen Sie wie folgt vor, um einen Sitzungs-Timeout-Wert für AEM Forms festzulegen.
seo-description: Gehen Sie wie folgt vor, um einen Sitzungs-Timeout-Wert für AEM Forms festzulegen.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 47%

---


# Single Sign-On und Zeitüberschreitungshandler {#single-sign-on-and-timeout-handlers}

AEM Forms Workspace ist SSO-fähig. Wenn sich ein Benutzer bei einer AEM Forms-Anwendung wie Forms Manager oder PDF Generator-Benutzeroberfläche angemeldet hat und in derselben Browsersitzung auf AEM Forms Workspace zugreift, wird der Benutzer bei AEM Forms Workspace angemeldet und umgekehrt.

## Das Bearbeiten des Serverzeitlimits in AEM Forms bildet Arbeitsbereich {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Sitzungs-Timeouts für einen Benutzer können in der Administration Console konfiguriert werden.

Um den Timeout festzulegen, melden Sie sich bei `https://'[server]:[port]'/adminui` an, navigieren Sie zu **Einstellungen > User Management > Konfiguration > Erweiterte Systemattribute konfigurieren** und nehmen Sie die gewünschten Einstellungen vor.

In AEM Forms Workspace wird Timeout wie folgt verarbeitet:

* Die Sitzungsdauer für einen Benutzer ist als Antwort auf einen `initialize`-Aufruf verfügbar, der die Benutzersitzung initialisiert.
* Ein Popup-Fenster informiert den Benutzer 15 Sekunden im Voraus, dass die Sitzung gleich ablaufen wird.

In diesem Popup-Dialog:

* Klicken Sie auf „OK“, um die Benutzersitzung zu beenden.
* Klicken Sie auf „Abbrechen“, um die Benutzersitzung neu zu initialisieren.

>[!NOTE]
>
>Wenn keine Aktion ausgeführt wird, wird der Benutzer drei Sekunden vor Ablauf der Sitzung automatisch aus AEM Forms Workspace abgemeldet.
