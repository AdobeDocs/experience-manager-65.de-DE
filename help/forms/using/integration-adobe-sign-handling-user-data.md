---
title: Integration mit Adobe Sign | Umgang mit Benutzerdaten
seo-title: Integration mit Adobe Sign | Umgang mit Benutzerdaten
description: 'null'
seo-description: 'null'
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
translation-type: tm+mt
source-git-commit: 4e0709031aca030e50840811a9b3717f3cb20340
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 69%

---


# Integration mit Adobe Sign | Umgang mit Benutzerdaten {#integration-with-adobe-sign-handling-user-data}

[!DNL AEM Forms] lässt sich in integrieren, um E-Signatur-Workflows in adaptiven Formularen für die Verarbeitung von Formularen oder Vereinbarungen für Rechts-, Verkaufs-, Lohn- und Personalmanagement-Workflows zu ermöglichen. [!DNL  Adobe Sign] Es ermöglicht das Signieren von Einzel- und Mehrbenutzer-Signaturen, sequenzielle und simultane Signier-Workflows, das Signieren von Formularen als anonymer oder angemeldeter Benutzer und mehrere Möglichkeiten zur Authentifizierung von Benutzern.

When a signer or multiple signers sign and submit an adaptive form, an [!DNL Adobe Sign] agreement is generated that includes information about the signers.

For more information about [!DNL AEM Forms] integration with [!DNL Adobe Sign], see [Using Adobe Sign in an adaptive form](/help/forms/using/working-with-adobe-sign.md).

## Benutzerdaten und Datenspeicher {#data}

[!DNL Adobe Sign]Das für aktiviertes adaptives Formular enthält Informationen zu den Unterzeichnern und kann andere Benutzerdaten enthalten, die vom adaptiven Formular erfasst wurden. The [!DNL Adobe Sign] service saves user data with the signature within the agreement. The agreement is saved on [!DNL Adobe Sign] server configured in [!DNL AEM Forms] cloud services. Wenn das adaptive Formular für die Sendeaktion konfiguriert ist, werden die Vertragsdaten außerdem zusammen mit den Formulardaten im Datenspeicher des Forms-Portals gespeichert.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Benutzerdaten werden innerhalb der Vereinbarung gesammelt, aber nicht in einer der Servicetabellen gespeichert. [!DNL Adobe Sign]Mit können Administratoren ihre eigenen Entscheidungen bei der Verwaltung von Daten treffen, die sie im Dienst steuern. Privacy administrators on the [!DNL Adobe Sign] service can list or remove agreements based on the email address of a requestor.

[!DNL Adobe Sign] bietet eine Webanwendung, mit der Teilnehmer nach Vereinbarungen suchen und diese gegebenenfalls löschen können. Weitere Informationen finden Sie unter [Adobe Sign - Funktion: Löschen Sie Benutzerinformationen](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

Vereinbarungsdaten für adaptive Formulare, die für die Verwendung der Forms-Portal-Sendeaktion konfiguriert sind, werden ebenfalls im Forms-Portal-Datenspeicher gespeichert. Informationen zum Zugreifen auf und Löschen von Daten aus dem Forms-Portal-Datenspeicher finden Sie unter [Forms-Portal | Umgang mit Benutzerdaten](/help/forms/using/forms-portal-handling-user-data.md).
