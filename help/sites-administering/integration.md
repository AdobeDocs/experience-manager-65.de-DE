---
title: Lösungsintegration
description: Erfahren Sie mehr über die Integration von Adobe Experience Manager (AEM) in andere Adobe- oder Drittanbieterdienste.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: ee5e8ebb-773f-4aa6-9c3e-2cc3bf4a3bbd
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: 243139ec-8e41-5296-a287-31343ab1bc0f
    internal-label: Integration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 81%
---
# Lösungsintegration{#solutions-integration}

* [Integrieren mit Adobe Experience Cloud](/help/sites-administering/marketing-cloud.md)
* [Integrieren mit Services von Dritten](/help/sites-administering/third-party-services.md)
* [Analyse mit externen Anbietern](/help/sites-administering/external-providers.md)
* [Catalog Producer](/help/sites-administering/catalog-producer.md)
* [Verstehen, Anwenden und Kuratieren von Smart-Tags](/help/assets/enhanced-smart-tags.md)

Die folgenden Informationen zur Integration von AEM in andere Adobe- oder Drittanbieterdienste sind verfügbar:

>[!NOTE]
>
>Wenn Sie bei Ihrer Integration auch eine benutzerdefinierte Proxy-Konfiguration verwenden, müssen Sie beide HTTP-Client-Proxy-Konfigurationen konfigurieren, da einige Funktionen von AEM die APIs der Version 3.x und andere die APIs der Version 4.x verwenden:
>
>* 3.x wird mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient konfiguriert](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wird mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator konfiguriert](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>
