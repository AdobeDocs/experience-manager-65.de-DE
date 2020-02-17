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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Integration mit Adobe Sign | Umgang mit Benutzerdaten {#integration-with-adobe-sign-handling-user-data}

AEM Forms lässt sich in Adobe Sign integrieren, um E-Signatur-Workflows in adaptiven Formularen für die Verarbeitung von Formularen oder Vereinbarungen für Rechts-, Verkaufs-, Lohn- und Personalmanagement-Workflows zu ermöglichen. Es ermöglicht das Signieren von Einzel- und Mehrbenutzer-Signaturen, sequenzielle und simultane Signier-Workflows, das Signieren von Formularen als anonymer oder angemeldeter Benutzer und mehrere Möglichkeiten zur Authentifizierung von Benutzern.

Wenn ein Unterzeichner oder mehrere Unterzeichner ein adaptives Formular signieren und übermitteln, wird eine Adobe Sign-Vereinbarung generiert, die Informationen zu den Unterzeichnern enthält.

For more information about AEM Forms integration with Adobe Sign, see [Using Adobe Sign in an adaptive form](/help/forms/using/working-with-adobe-sign.md).

## Benutzerdaten und Datenspeicher {#data}

Das für Adobe Sign aktiviertes adaptives Formular enthält Informationen zu den Unterzeichnern und kann andere Benutzerdaten enthalten, die vom adaptiven Formular erfasst wurden. Der Adobe Sign-Dienst speichert Benutzerdaten mit der Signatur innerhalb der Vereinbarung. Die Vereinbarung wird auf dem Adobe Sign-Server gespeichert, der in den Cloud-Diensten von AEM Forms konfiguriert ist. Wenn das adaptive Formular für die Sendeaktion konfiguriert ist, werden die Vertragsdaten außerdem zusammen mit den Formulardaten im Datenspeicher des Forms-Portals gespeichert.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Benutzerdaten werden innerhalb der Vereinbarung gesammelt, aber nicht in einer der Servicetabellen gespeichert. Mit Adobe Sign können Administratoren ihre eigenen Entscheidungen bei der Verwaltung von Daten treffen, die sie im Dienst steuern. Datenschutzadministratoren im Adobe Sign-Dienst können Vereinbarungen basierend auf der E-Mail-Adresse eines Anforderers auflisten oder entfernen.

Adobe Sign bietet eine Webanwendung, mit der Teilnehmer nach Vereinbarungen suchen und diese gegebenenfalls löschen können. Weitere Informationen finden Sie unter [Adobe Sign - Funktion: Löschen Sie Benutzerinformationen](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

Vereinbarungsdaten für adaptive Formulare, die für die Verwendung der Forms-Portal-Sendeaktion konfiguriert sind, werden ebenfalls im Forms-Portal-Datenspeicher gespeichert. Informationen zum Zugreifen auf und Löschen von Daten aus dem Forms-Portal-Datenspeicher finden Sie unter [Forms-Portal | Umgang mit Benutzerdaten](/help/forms/using/forms-portal-handling-user-data.md).
