---
title: Integration mit Adobe Sign | Umgang mit Benutzerdaten
description: Erfahren Sie mehr über die Integration von AEM Forms mit Adobe Sign für E-Signaturen in adaptiven Formularen. Es unterstützt mehrere Signaturoptionen für verschiedene Workflows.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Acrobat Sign
role: Admin, User, Developer
exl-id: b43ed9b7-b1ef-4878-ae3b-643b558eed7b
solution: Experience Manager, Experience Manager Forms
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: a16aea24-4e85-528d-9377-cd80bb039c1d
    internal-label: Acrobat Sign
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 100%
---
# Integration mit Adobe Sign | Umgang mit Benutzerdaten {#integration-with-adobe-sign-handling-user-data}

[!DNL AEM Forms] lässt sich in integrieren, um E-Signatur-Workflows in adaptiven Formularen für die Verarbeitung von Formularen oder Vereinbarungen für Rechts-, Verkaufs-, Lohn- und Personalmanagement-Workflows zu ermöglichen. [!DNL  Adobe Sign] Es ermöglicht das Signieren von Einzel- und Mehrbenutzer-Signaturen, sequenzielle und simultane Signier-Workflows, das Signieren von Formularen als anonymer oder angemeldeter Benutzer und mehrere Möglichkeiten zur Authentifizierung von Benutzern.

Wenn ein Signierer oder mehrere Signierer ein adaptives Formular signieren und übermitteln, wird eine [!DNL Adobe Sign]-Vereinbarung generiert, die Informationen zu den Signierern enthält.

Weitere Informationen zur Integration von [!DNL AEM Forms] mit [!DNL Adobe Sign] finden Sie unter [Verwenden von Adobe Sign in einem adaptiven Formular](/help/forms/using/working-with-adobe-sign.md).

## Benutzerdaten und Datenspeicher {#data}

Das [!DNL Adobe Sign] für aktiviertes adaptives Formular enthält Informationen zu den Unterzeichnern und kann andere Benutzerdaten enthalten, die vom adaptiven Formular erfasst wurden. Der [!DNL Adobe Sign]-Service speichert Benutzerdaten mit der Signatur innerhalb der Vereinbarung. Die Vereinbarung wird auf einem [!DNL Adobe Sign]-Server gespeichert, der in den Cloud-Diensten von [!DNL AEM Forms] konfiguriert ist. Wenn das adaptive Formular für die Sendeaktion des Formularportals konfiguriert ist, werden die Vertragsdaten außerdem zusammen mit den Formulardaten im Datenspeicher des Formularportals gespeichert.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Benutzerdaten werden innerhalb der Vereinbarung gesammelt, aber nicht in einer der Service-Tabellen gespeichert. Mit [!DNL Adobe Sign] können Admins ihre eigenen Entscheidungen bei der Verwaltung von Daten treffen, die sie in dem Dienst steuern. Datenschutzadmins im [!DNL Adobe Sign]-Dienst können Vereinbarungen basierend auf der E-Mail-Adresse einer anfordernden Person auflisten oder entfernen.

[!DNL Adobe Sign] bietet eine Web-Anwendung, mit der Teilnehmerinnen und Teilnehmer nach Vereinbarungen suchen und diese gegebenenfalls löschen können. Weitere Informationen finden Sie unter [Adobe Sign – Funktion: Benutzerinformationen löschen](https://helpx.adobe.com/de/sign/help/adobesign_gdpr_user_deletion.html).

Vereinbarungsdaten für adaptive Formulare, die für die Verwendung der Formularportal-Sendeaktion konfiguriert sind, werden ebenfalls im Formularportal-Datenspeicher gespeichert. Informationen zum Zugreifen auf und Löschen von Daten aus dem Formularportal-Datenspeicher finden Sie unter [Formularportal | Umgang mit Benutzerdaten](/help/forms/using/forms-portal-handling-user-data.md).
