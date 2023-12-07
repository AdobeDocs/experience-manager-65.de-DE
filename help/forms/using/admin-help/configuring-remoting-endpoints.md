---
title: Konfigurieren der Remoting-Endpunkte
description: Erfahren Sie, wie Sie Remoting-Endpunkte konfigurieren. In diesem Dokument wird erläutert, wie Sie mit Flex erstellte Anwendungen aktivieren, um den Dienst mithilfe des AEM Forms Remoting aufzurufen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 891d7d75-555a-46c6-a8a0-d5238b48bc79
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 36%

---

# Konfigurieren der Remoting-Endpunkte {#configuring-remoting-endpoints}

Ein Remoting-Endpunkt ermöglicht es einer mit Flex erstellten Anwendung, den Dienst mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting aufzurufen. Für jeden aktivierten Dienst wird automatisch ein Remoting-Endpunkt erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt. Flex-Clients können Remote-Objekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Dienst aufzurufen.

## Remoting-Endpunkteinstellungen {#remoting-endpoint-settings}

**Flex-Client-Authentifizierungsmethode**: Bestimmt den Typ der Antwort, die der Server zum Client zurücksendet, wenn die Sicherheit für den aufgerufenen Service aktiviert ist, der Vorgang keine anonymen Aufrufe unterstützt und der Client keine oder ungültige Anmeldeinformationen übergibt.
