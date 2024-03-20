---
title: Single Sign-On und Zeitüberschreitungs-Handler
description: So legen Sie den Wert für das Sitzungs-Timeout für AEM Forms Workspace fest.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 4f824d80-f3f8-4010-9583-5a9ab1151a7b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '189'
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
