---
title: Single Sign-On und Zeitüberschreitungs-Handler
seo-title: Single Sign On and timeout handlers
description: So legen Sie den Wert für das Sitzungs-Timeout für AEM Forms Workspace fest.
seo-description: How-to set the session timeout value for AEM Forms workspace.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
exl-id: 4f824d80-f3f8-4010-9583-5a9ab1151a7b
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 40%

---

# Single Sign-On und Zeitüberschreitungs-Handler {#single-sign-on-and-timeout-handlers}

AEM Forms Workspace ist SSO-aktiviert. Wenn sich ein Benutzer bei einer AEM Forms-Anwendung wie Forms Manager oder der PDF Generator-Benutzeroberfläche angemeldet hat und in derselben Browsersitzung auf AEM Forms Workspace zugreift, wird der Benutzer in AEM Forms Workspace angemeldet und umgekehrt.

## Umgang mit Server-Timeouts in AEM Forms Workspace {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Sitzungs-Timeout für einen Benutzer kann in der Administration Console konfiguriert werden.

Um den Timeout festzulegen, melden Sie sich bei `https://'[server]:[port]'/adminui` an, navigieren zu **Einstellungen > Benutzerverwaltung > Konfiguration > Erweiterte Systemattribute konfigurieren** und nehmen die gewünschten Einstellungen vor.

In AEM Forms wird die Zeitüberschreitung im Arbeitsbereich wie folgt behandelt:

* Die Sitzungsdauer für einen Benutzer ist in der Antwort auf den Aufruf `initialize` verfügbar, der die Benutzersitzung initialisiert.
* Ein Popup-Dialogfeld benachrichtigt den Benutzer 15 Sekunden vor Ablauf der Sitzung über den bevorstehenden Ablauf der Sitzung.

In diesem Popup-Dialogfeld:

* Klicken Sie auf OK , um die Benutzersitzung zu beenden.
* Klicken Sie auf Abbrechen , um die Benutzersitzung erneut zu initialisieren.

>[!NOTE]
>
>Wird keine Aktion ausgeführt, wird der Benutzer drei Sekunden vor Ablauf der Sitzung automatisch vom AEM Forms-Arbeitsbereich abgemeldet.
