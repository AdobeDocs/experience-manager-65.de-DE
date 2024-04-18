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
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 100%

---

# Lösungsintegration{#solutions-integration}

* [Integrieren mit Adobe Experience Cloud](/help/sites-administering/marketing-cloud.md)
* [Integrieren mit Services von Dritten](/help/sites-administering/third-party-services.md)
* [Analyse mit externen Anbietern](/help/sites-administering/external-providers.md)
* [Catalog Producer](/help/sites-administering/catalog-producer.md)
* [Verstehen, Anwenden und Kuratieren von Smart Tags](/help/assets/enhanced-smart-tags.md)

Die folgenden Informationen zur Integration von AEM in andere Adobe- oder Drittanbieterdienste sind verfügbar:

>[!NOTE]
>
>Wenn Sie bei Ihrer Integration auch eine benutzerdefinierte Proxy-Konfiguration verwenden, müssen Sie beide HTTP-Client-Proxy-Konfigurationen konfigurieren, da einige Funktionen von AEM die APIs der Version 3.x und andere die APIs der Version 4.x verwenden:
>
>* 3.x wird mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert.
>* 4.x wird mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.
>
