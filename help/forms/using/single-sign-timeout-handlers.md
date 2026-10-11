---
title: Single Sign-On und Zeitüberschreitungs-Handler
description: Gehen Sie wie folgt vor, um einen Sitzungs-Zeitüberschreitungswert für AEM Forms Workspace festzulegen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 4f824d80-f3f8-4010-9583-5a9ab1151a7b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%
---
# Single Sign-On und Zeitüberschreitungs-Handler {#single-sign-on-and-timeout-handlers}

AEM Forms Workspace ist SSO-fähig. Wenn Sie sich bei einer AEM Forms-Anwendung wie Forms Manager oder der PDF Generator-Benutzeroberfläche angemeldet haben und in derselben Browser-Sitzung auf AEM Forms Workspace zugreifen, werden Sie bei AEM Forms Workspace angemeldet und umgekehrt.

## Die Handhabung der Server-Zeitüberschreitung in AEM Forms Workspace {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Sitzungs-Zeitüberschreitungen für Benutzende können in der Administrationskonsole konfiguriert werden.

Um den Timeout festzulegen, melden Sie sich bei `https://'[server]:[port]'/adminui` an, navigieren zu **Einstellungen > Benutzerverwaltung > Konfiguration > Erweiterte Systemattribute konfigurieren** und nehmen die gewünschten Einstellungen vor.

In AEM Forms wird die Zeitüberschreitung im Arbeitsbereich wie folgt behandelt:

* Die Sitzungsdauer für einen Benutzer ist in der Antwort auf den Aufruf `initialize` verfügbar, der die Benutzersitzung initialisiert.
* Ein Popup-Dialogfeld informiert Benutzende 15 Sekunden im Voraus, dass die Sitzung gleich ablaufen wird.

In diesem Popup-Dialogfeld:

* Klicken Sie auf „OK“, um die Benutzersitzung zu beenden.
* Klicken Sie auf „Abbrechen“, um die Benutzersitzung neu zu initialisieren.

>[!NOTE]
>
>Wird keine Aktion ausgeführt, wird der Benutzer drei Sekunden vor Ablauf der Sitzung automatisch vom AEM Forms-Arbeitsbereich abgemeldet.
