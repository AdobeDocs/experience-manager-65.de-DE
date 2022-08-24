---
title: Integration mit Adobe Sign | Umgang mit Benutzerdaten
seo-title: Integration with Adobe Sign | Handling user data
description: Integration mit Adobe Sign | Umgang mit Benutzerdaten
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Adobe Sign
role: Admin
exl-id: b43ed9b7-b1ef-4878-ae3b-643b558eed7b
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 100%

---

# Integration mit Adobe Sign | Umgang mit Benutzerdaten {#integration-with-adobe-sign-handling-user-data}

[!DNL AEM Forms] lässt sich in integrieren, um E-Signatur-Workflows in adaptiven Formularen für die Verarbeitung von Formularen oder Vereinbarungen für Rechts-, Verkaufs-, Lohn- und Personalmanagement-Workflows zu ermöglichen. [!DNL  Adobe Sign] Es ermöglicht das Signieren von Einzel- und Mehrbenutzer-Signaturen, sequenzielle und simultane Signier-Workflows, das Signieren von Formularen als anonymer oder angemeldeter Benutzer und mehrere Möglichkeiten zur Authentifizierung von Benutzern.

Wenn ein Signierer oder mehrere Signierer ein adaptives Formular signieren und übermitteln, wird eine [!DNL Adobe Sign]-Vereinbarung generiert, die Informationen zu den Signierern enthält.

Weitere Informationen zur Integration von [!DNL AEM Forms] mit [!DNL Adobe Sign] finden Sie unter [Verwenden von Adobe Sign in einem adaptiven Formular](/help/forms/using/working-with-adobe-sign.md).

## Benutzerdaten und Datenspeicher {#data}

Das [!DNL Adobe Sign] für aktiviertes adaptives Formular enthält Informationen zu den Unterzeichnern und kann andere Benutzerdaten enthalten, die vom adaptiven Formular erfasst wurden. Der [!DNL Adobe Sign]-Service speichert Benutzerdaten mit der Signatur innerhalb der Vereinbarung. Die Vereinbarung wird auf dem [!DNL Adobe Sign]-Server gespeichert, der in den Cloud-Services von [!DNL AEM Forms] konfiguriert ist. Wenn das adaptive Formular für die Sendeaktion konfiguriert ist, werden die Vertragsdaten außerdem zusammen mit den Formulardaten im Datenspeicher des Forms-Portals gespeichert.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Benutzerdaten werden innerhalb der Vereinbarung gesammelt, aber nicht in einer der Servicetabellen gespeichert. [!DNL Adobe Sign]Mit können Administratoren ihre eigenen Entscheidungen bei der Verwaltung von Daten treffen, die sie im Dienst steuern. Datenschutzadministratoren im [!DNL Adobe Sign]-Service können Vereinbarungen basierend auf der E-Mail-Adresse eines Anforderers auflisten oder entfernen.

[!DNL Adobe Sign] bietet eine Webanwendung, mit der Teilnehmer nach Vereinbarungen suchen und diese gegebenenfalls löschen können. Weitere Informationen finden Sie unter [Adobe Sign – Funktion: Benutzerinformationen löschen](https://helpx.adobe.com/de/sign/help/adobesign_gdpr_user_deletion.html).

Vereinbarungsdaten für adaptive Formulare, die für die Verwendung der Forms-Portal-Sendeaktion konfiguriert sind, werden ebenfalls im Forms-Portal-Datenspeicher gespeichert. Informationen zum Zugreifen auf und Löschen von Daten aus dem Forms-Portal-Datenspeicher finden Sie unter [Forms-Portal | Umgang mit Benutzerdaten](/help/forms/using/forms-portal-handling-user-data.md).
