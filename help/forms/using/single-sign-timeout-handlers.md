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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Single Sign-On und Zeitüberschreitungshandler {#single-sign-on-and-timeout-handlers}

AEM Forms Workspace ist SSO-fähig. Wenn sich ein Benutzer bei einer AEM Forms-Anwendung wie Forms Manager oder PDF Generator-Benutzeroberfläche angemeldet hat und in derselben Browsersitzung auf AEM Forms Workspace zugreift, wird der Benutzer bei AEM Forms Workspace angemeldet und umgekehrt.

## Das Bearbeiten des Serverzeitlimits in AEM Forms bildet Arbeitsbereich {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Sitzungs-Timeouts für einen Benutzer können in der Administration Console konfiguriert werden.

To set the timeout, login to `https://[server]:[port]/adminui`, navigate to **Settings > User Management > Configuration > Configure Advanced System Attributes**, and make the desired settings.

In AEM Forms Workspace-Timeout wird wie folgt behandelt:

* Session duration for a user is available in response of `initialize` call that initializes user session.
* Ein Popup-Fenster informiert den Benutzer 15 Sekunden im Voraus, dass die Sitzung gleich ablaufen wird.

In diesem Popup-Dialog:

* Klicken Sie auf „OK“, um die Benutzersitzung zu beenden.
* Klicken Sie auf „Abbrechen“, um die Benutzersitzung neu zu initialisieren.

>[!NOTE]
>
>Wenn keine Aktion ausgeführt wird, wird der Benutzer drei Sekunden vor Ablauf der Sitzung automatisch von AEM Forms Workspace abgemeldet.

**[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)**
