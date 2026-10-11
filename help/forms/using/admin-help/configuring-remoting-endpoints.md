---
title: Konfigurieren der Remoting-Endpunkte
description: Erfahren Sie, wie Sie Remoting-Endpunkte konfigurieren. In diesem Dokument wird erläutert, wie Sie eine Anwendung aktivieren, die mit Flex erstellt wurde, um den Dienst mithilfe von AEM Forms Remoting aufzurufen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 891d7d75-555a-46c6-a8a0-d5238b48bc79
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
source-wordcount: '139'
ht-degree: 100%
---
# Konfigurieren der Remoting-Endpunkte {#configuring-remoting-endpoints}

Ein Remoting-Endpunkt aktiviert eine Anwendung, die mit Flex erstellt wurde, um den Dienst mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt) aufzurufen. Ein Remoting-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt, und Flex-Kundinnen und -Kunden können Remote-Objekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Service aufzurufen.

## Remoting-Endpunkteinstellungen {#remoting-endpoint-settings}

**Flex-Client-Authentifizierungsmethode**: Bestimmt den Typ der Antwort, die der Server zum Client zurücksendet, wenn die Sicherheit für den aufgerufenen Service aktiviert ist, der Vorgang keine anonymen Aufrufe unterstützt und der Client keine oder ungültige Anmeldeinformationen übergibt.
