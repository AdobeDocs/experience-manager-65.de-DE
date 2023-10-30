---
title: Integration mit Adobe Sign | Umgang mit Benutzerdaten
description: AEM Forms integriert Adobe Sign für e-Signaturen in adaptive Formulare. Es unterstützt mehrere Signaturoptionen für verschiedene Workflows.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Acrobat Sign
role: Admin
exl-id: b43ed9b7-b1ef-4878-ae3b-643b558eed7b
source-git-commit: 20b0d0db54dc30285c056a10032f02ba45f8baca
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 54%

---

# Integration mit Adobe Sign | Umgang mit Benutzerdaten {#integration-with-adobe-sign-handling-user-data}

[!DNL AEM Forms] lässt sich in integrieren, um E-Signatur-Workflows in adaptiven Formularen für die Verarbeitung von Formularen oder Vereinbarungen für Rechts-, Verkaufs-, Lohn- und Personalmanagement-Workflows zu ermöglichen. [!DNL  Adobe Sign] Es ermöglicht das Signieren von Einzel- und Mehrbenutzer-Signaturen, sequenzielle und simultane Signier-Workflows, das Signieren von Formularen als anonymer oder angemeldeter Benutzer und mehrere Möglichkeiten zur Authentifizierung von Benutzern.

Wenn ein Signierer oder mehrere Signierer ein adaptives Formular signieren und übermitteln, wird eine [!DNL Adobe Sign]-Vereinbarung generiert, die Informationen zu den Signierern enthält.

Weitere Informationen zur Integration von [!DNL AEM Forms] mit [!DNL Adobe Sign] finden Sie unter [Verwenden von Adobe Sign in einem adaptiven Formular](/help/forms/using/working-with-adobe-sign.md).

## Benutzerdaten und Datenspeicher {#data}

Das [!DNL Adobe Sign] für aktiviertes adaptives Formular enthält Informationen zu den Unterzeichnern und kann andere Benutzerdaten enthalten, die vom adaptiven Formular erfasst wurden. Der [!DNL Adobe Sign]-Service speichert Benutzerdaten mit der Signatur innerhalb der Vereinbarung. Die Vereinbarung wird auf einer [!DNL Adobe Sign] Server konfiguriert in [!DNL AEM Forms] Cloud-Services. Wenn das adaptive Formular für die Verwendung der Übermittlungsaktion für Forms Portal konfiguriert ist, werden die Vertragsdaten zusammen mit den Formulardaten im Forms Portal-Datenspeicher gespeichert.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Benutzerdaten werden innerhalb der Vereinbarung erfasst, aber nicht in einer der Service-Tabellen gespeichert. [!DNL Adobe Sign] ermöglicht es Administratoren, eigene Entscheidungen zur Verwaltung der Daten zu treffen, die sie im Dienst steuern. Datenschutzadministratoren im [!DNL Adobe Sign]-Service können Vereinbarungen basierend auf der E-Mail-Adresse eines Anforderers auflisten oder entfernen.

[!DNL Adobe Sign] bietet eine Web-Anwendung, die das Durchsuchen von Vereinbarungen durch Teilnehmer ermöglicht und diese bei Bedarf löscht. Weitere Informationen finden Sie unter [Adobe Sign – Funktion: Benutzerinformationen löschen](https://helpx.adobe.com/de/sign/help/adobesign_gdpr_user_deletion.html).

Vereinbarungsdaten für adaptive Formulare, die für die Verwendung der Übermittlungsaktion für Forms Portal konfiguriert sind, werden ebenfalls im Forms Portal-Datenspeicher gespeichert. Informationen zum Zugreifen auf und Löschen von Daten aus dem Forms Portal-Datenspeicher finden Sie unter [Forms Portal | Umgang mit Benutzerdaten](/help/forms/using/forms-portal-handling-user-data.md).
