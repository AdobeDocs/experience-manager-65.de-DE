---
title: Integrieren mit Adobe Analytics
seo-title: Integration mit Adobe Analytics
description: Hier erfahren Sie, wie Sie AEM mit Adobe Analytics integrieren.
seo-description: Hier erfahren Sie, wie Sie AEM mit Adobe Analytics integrieren.
uuid: d8548263-6ac5-45fb-8c70-52ecd4161bbb
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 444c522e-2f33-4f41-846c-8d317e799659
docset: aem65
translation-type: tm+mt
source-git-commit: ca25e66b280db479f69c487753a557b0240233da
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 100%

---


# Integration mit Adobe Analytics{#integrating-with-adobe-analytics}

Die Integration von Adobe Analytics und AEM ermöglicht es Ihnen, Webseitenaktivität zu erfassen:

* Eine Adobe Analytics-Konfiguration ermöglicht AEM die Authentifizierung mit Adobe Analytics.
* Ein Framework identifiziert die Daten, die an die Adobe Analytics-Report Suite übermittelt werden.

Die Daten umfassen Seiten- und Benutzerdaten, z. B.:

* Daten, die von AEM-Komponenten erfasst werden
* Link-Klicks
* Videonutzungsdaten
* die Anzahl von Seitenbesuchen aus Adobe Analytics

Die folgenden Seiten helfen Ihnen beim Konfigurieren der Integration:

* [Herstellen einer Verbindung mit Adobe Analytics und Erstellen von Frameworks](/help/sites-administering/adobeanalytics-connect.md)
* [Konfigurieren des Linktrackings für Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Zuordnen von Komponentendaten mit Adobe Analytics-Eigenschaften](/help/sites-administering/adobeanalytics-mapping.md)
* [Konfigurieren von Videotracking für Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)
* [Adobe Classifications](/help/sites-administering/adobeanalytics-classifications.md)

Der [Opt-in-Assistent](/help/sites-administering/opt-in.md) erleichtert die Durchführung der Integration.

>[!NOTE]
>
>Weitere Informationen finden Sie im Artikel [Integrieren von AEM mit Adobe Target und Adobe Analytics mithilfe von DTM](https://helpx.adobe.com/de/experience-manager/using/integrate-digital-marketing-solutions.html).

## Weiterführende Informationen {#further-information}

Siehe:

* [Erweitern der Adobe Analytics-Integration](/help/sites-developing/extending-analytics.md), um Informationen zur Entwicklung von Komponenten zu erhalten, die Benutzerdaten erfassen, und zur Anpassung des Adobe Analytics-Frameworks.
* den Knowledgebase-Artikel [Adobe Analytics-Integration – Problembehebung](https://helpx.adobe.com/de/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), um Information zur Behebung von Problemen mit der Adobe Analytics-Integration zu erhalten.

>[!NOTE]
>
>Wenn Sie Adobe Analytics mit einer benutzerdefinierten Proxykonfiguration verwenden, müssen Sie zwei OSGi-Pakete[ (z. B. mit der Web Console) ](/help/sites-deploying/configuring-osgi.md)konfigurieren, die für die **Apache HTTP Client**-Proxykonfigurationen erforderlich sind. Beide sind erforderlich, da einige Funktionen von AEM die 3.x-APIs verwenden, während andere die 4.x-APIs verwenden. Konfigurieren:
>
>* **Day Commons HTTP Client 3.1** zum Konfigurieren der 3.x-API;
>  Beispiel: [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP Components Proxy Configuration** zum Konfigurieren der 4.x-API;
>  Beispiel: [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



