---
title: Integration von AEM 6.5 mit Adobe Campaign
description: Informationen zur Unterstützung von AEM 6.5 für die Integrationen mit Adobe Campaign.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: ab41e540-1d43-4fc2-99d4-621ff2290e77
source-git-commit: dac156251ae48e9d83e84ba6a4685689def9e396
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 72%

---


# Integration von AEM 6.5 mit Adobe Campaign{#integrating-with-adobe-campaign}

Informationen zur Unterstützung von AEM 6.5 für die Integrationen mit Adobe Campaign.

Adobe Campaign ist eine Reihe von Lösungen, mit denen Sie Kampagnen personalisieren und über alle Ihre Online- und Offline-Kanäle hinweg bereitstellen können.

>[!NOTE]
>
>Dieses Dokument beschreibt die Integration von Adobe Campaign mit AEM 6.5, der lokalen oder von AMS gehosteten AEM-Lösung.
>
>Einzelheiten zur Integration von Adobe Campaign in AEM as a Cloud Service, die Cloud-native AEM-Lösung, finden Sie unter [Siehe dieses Dokument.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/integrations/campaign.html?lang=de)

## Integrieren mit Adobe Campaign Classic {#acc}

Es gibt mehrere Versionen von Adobe Campaign Classic (ACC). Die Unterstützung für die Integration mit AEM hängt von der ACC-Version ab, die Sie implementiert haben, und davon, ob AEM lokal auf in Adobe Manager Services (AMS) installiert ist.

| ACC-Version | Integration mit AEM 6.5 <br>Lokal | Integration mit AEM 6.5<br>AMS |
|---|---|---|
| [v7](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de) | Unterstützt | Unterstützt  |
| [v8 Client Console](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=de) | Unterstützt | Unterstützt  |
| [Web-Benutzeroberfläche v8](https://experienceleague.adobe.com/docs/campaign-web/v8/campaign-web-home.html) | Unterstützt | Unterstützt  |

Die folgende Dokumentation beschreibt die Integration von AEM mit Adobe Campaign Classic.

* [Integration mit Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md): Lernen Sie die einzelnen Schritte zum Konfigurieren der Integration kennen.

Die folgende zusätzliche Dokumentation beschreibt die Verwendung der Integration.

* [E-Mail-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/email/introduction.html?lang=de): Erfahren Sie mehr über die Standard-E-Mail-Komponenten, mit denen Sie Campaign-Inhalte in AEM erstellen können.
* [Fehlerbehebung bei der Adobe Campaign Classic-Integration](/help/sites-administering/troubleshooting-campaignintegration.md): Erfahren Sie, wie Sie die häufigsten Probleme bei der AEM-ACC-Integration beheben.


In der folgenden Dokumentation wird beschrieben, wie Sie AEM as a Cloud Service in die Web-Benutzeroberfläche von Adobe Campaign v8 integrieren.

* [Verwalten von Vorlagen mit Adobe Experience Manager as a Cloud Service in der Web-Benutzeroberfläche von Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign-web/v8/integrations/aem-content.html) - Lernen Sie die einzelnen Schritte zur Konfiguration und Verwendung der Integration mit AEM-Vorlagen kennen.
* [Verwalten von Assets mit Adobe Experience Manager as a Cloud Service in der Web-Benutzeroberfläche von Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign-web/v8/integrations/aem-assets.html) - Machen Sie sich mit den schrittweisen Informationen zur Konfiguration und Verwendung der Integration mit AEM Assets vertraut.


## Integration mit Adobe Campaign Standard {#acs}

Die Integration von [Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de) (ACS) mit AEM hängt davon ab, ob AEM vor Ort oder in Adobe Manage Services (AMS) installiert ist.

| Integration mit AEM 6.5 <br>Lokal | Integration mit AEM 6.5<br>AMS |
|---|---|
| Unterstützt | Unterstützt |
| Unterstützt | Unterstützt  |

Die folgende Dokumentation beschreibt die Integration von AEM mit Adobe Campaign Standard.

* [Integration mit Adobe Campaign Standard](/help/sites-administering/campaignstandard.md)

Die folgende zusätzliche Dokumentation beschreibt die Verwendung der Integration.

* [E-Mail-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/email/introduction.html?lang=de)
