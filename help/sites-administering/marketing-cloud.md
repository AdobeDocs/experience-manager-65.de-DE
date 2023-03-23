---
title: Integration mit Adobe Experience Cloud
description: Erfahren Sie, wie Sie Adobe Experience Manager mit Adobe Experience Cloud integrieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: ba518290-dd82-44dc-ae7c-c8152df89179
source-git-commit: a51a863a4edf7e8b951a8361c5c7f0517b09f12a
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 44%

---

# Integration mit Adobe Experience Cloud{#integrating-with-the-adobe-marketing-cloud}

Die [Adobe Experience Cloud](https://business.adobe.com/products/marketing-cloud/main.html)enthält leistungsstarke Produkte zur Webanalyse- und Website-Optimierung, die umsetzbare Echtzeitdaten und Einblicke liefern, um erfolgreiche Online-Initiativen zu fördern. Es bietet eine integrierte und offene Plattform für die Online-Geschäftsoptimierung. Die Cloud besteht aus integrierten Anwendungen, mit denen Kundeneinblicke gesammelt und freigesetzt werden können, um die Akquise, Konvertierung und Bindung von Kunden sowie die Erstellung und Verteilung von Inhalten zu optimieren.

Mit Adobe Experience Manager (AEM) können Sie nahtlos in die folgenden Adobe Experience Cloud-Produkte integrieren:

* Über Adobe Analytics erhalten Marketing-Experten in Echtzeit verwertbare Daten zu Online-Strategien und Marketing-Initiativen.
* Mit Adobe Target haben Marketing-Experten die Möglichkeit, die Relevanz ihrer Online-Inhalte für Kunden immer weiter zu erhöhen, und dies führt zu einer größeren Zahl von Konversionen.
* Mithilfe von Adobe Dynamic Media Classic wird die Medienverwaltung automatisiert, die Webveröffentlichung optimiert und die Weboberfläche erweitert – alles innerhalb einer gehosteten Umgebung.
* Adobe Dynamic Tag Management bietet Marketing-Experten intuitive Tools zum schnellen und einfachen Verwalten einer unbegrenzten Zahl von Adobe- und Drittanbieter-Tags.
<!-- Search&Promote is end of life as of September 1, 2022 * Adobe Search&Promote gives marketers the ability to control and optimize the search results on their sites. -->
* Mit Adobe Campaign können Sie den Inhalt von E-Mail-Bereitstellungen direkt in Adobe Experience Manager verwalten.

[Außerdem können Sie AEM mit Creative Cloud](/help/assets/aem-cc-integration-best-practices.md) und mit [Drittanbieterdiensten](/help/sites-administering/third-party-services.md) integrieren.

## Integration mit Adobe Analytics {#integrating-with-adobe-analytics}

[Adobe Analytics](https://business.adobe.com/products/analytics/adobe-analytics.html) ist eine branchenführende Lösung, mit der Experten für Digital Marketing integrierte Daten aller Online-Initiativen über mehrere Marketing-Kanäle hinweg messen, analysieren und optimieren können. Es bietet Marketing-Experten umsetzbare Echtzeit-Web-Analysedaten zu digitalen Strategien und Marketinginitiativen. Mit Adobe Analytics können Marketingexperten schnell die profitabelsten Pfade durch eine Website identifizieren, den Traffic segmentieren, um hochwertige Webbesucher zu erkennen, zu ermitteln, wo Besucher von der Site weg navigieren, und wichtige Erfolgsmetriken für Online-Marketingkampagnen identifizieren.

Sie können Adobe Analytics verwenden, um Daten aus Ihren Sites zu analysieren.

Die Integration mit Adobe Analytics bietet Ihnen folgende Möglichkeiten:

* Aktivieren von Analytics-Benutzer-Tracking
* Ordnen Sie Ihre Ausführungsmodi (z. B. Autor, Veröffentlichung) verschiedenen Report Suites zu.
* Senden Sie ClientContext-Variablen als Konversionsvariablen oder Traffic-Eigenschaften.
* Verwenden Sie vordefinierte Variablenzuordnungen.
* Konfigurieren Sie vollständige Sitebereiche gleichzeitig.
* Verfolgen Sie benutzerdefinierte Ereignisse.

Informationen zur Integration von AEM in Analytics finden Sie unter [Integration mit Adobe Analytics](/help/sites-administering/adobeanalytics.md).

Der [Opt-in-Assistent](/help/sites-administering/opt-in.md) erleichtert die Durchführung der Integration.

## Integrieren mit Adobe Target {#integrating-with-adobe-target}

[Adobe Target wird von Marketing-Experten genutzt, um Online-Tests zu entwerfen und auszuführen, in kurzer Zeit Zielgruppensegmente zu erstellen (anhand des Verhaltens) und das Targeting für Inhalte und Online-Erlebnisse zu automatisieren.](https://business.adobe.com/products/target/adobe-target.html)

Online-Verbraucher haben heutzutage ständig wachsende Anforderungen und erwarten relevante, sogar personalisierte Inhalte von den verschiedensten Sites und Inhaltsquellen, aus denen sie wählen können. Um eine Online-Zielgruppe zu erreichen, müssen Online-Marketing-Experten schnell ermitteln, welche Angebote und Inhalte für ihre Zielgruppen relevant und überzeugend sind. Mit diesem Wissen können Marketingexperten ihre Sites kontinuierlich weiterentwickeln und die entsprechenden Inhalte auf verschiedene Zielgruppen ausrichten.

[Integration mit Adobe Target](/help/sites-administering/target.md) erläutert, wie Sie Ihre Site in Target integrieren.

Der [Opt-in-Assistent](/help/sites-administering/opt-in.md) erleichtert die Durchführung der Integration.

## Opt-in für Analytics und Target {#opting-in-to-analytics-and-target}

AEM bietet ein einfaches Opt-in-Verfahren zur Integration in Adobe Analytics und Adobe Target. Wenn Sie sich als Administrator anmelden und die Projektekonsole aufrufen, wird Ihnen ein Opt-in-Assistent angezeigt.

![chlimage_1-107](assets/chlimage_1-107a.png)

Nutzen Sie die Integration in Analytics und/oder Target , um die Verwendung der Tracking- und Analysefunktionen sowie der Personalisierungsfunktionen ihrer Seiten zu ermöglichen. Wenn Sie sich anmelden, geben Sie Ihre Benutzerkontoinformationen an und geben Sie die verfolgten Seiten an.

Weitere Informationen finden Sie unter [Opt-in für Adobe Analytics und Target](/help/sites-administering/opt-in.md).

## Integration mit Adobe Dynamic Media Classic {#integrating-with-scene}

Adobe Dynamic Media Classic ist eine gehostete Lösung für die Veröffentlichung, Verwaltung, Erweiterung und Bereitstellung dynamischer Marketing-Assets und visueller Rich-Visual-Merchandising im Web, auf Mobilgeräten, in E-Mails, sozialen Medien, mit dem Internet verbundenen Anzeigen und zum Drucken.

In Adobe Experience Manager können Sie digitale Assets direkt aus Adobe Experience Manager in Dynamic Media Classic veröffentlichen und umgekehrt.

Darüber hinaus können Sie in Dynamic Media Classic veröffentlichte Adobe Experience Manager-Assets in verschiedenen Viewern anzeigen, z. B. Basic Zoom und Video.

Weitere Informationen zur Integration von Adobe Experience Manager mit Dynamic Media Classic finden Sie in der Dokumentation [Integration mit Dynamic Media Classic](/help/sites-administering/scene7.md).

## Integrieren mit Adobe Dynamic Tag Management {#integrating-with-adobe-dynamic-tag-management}

[Adobe Dynamic Tag Management bietet Marketing-Experten intuitive Tools zum schnellen und einfachen Verwalten einer unbegrenzten Zahl von Adobe- und Drittanbieter-Tags. ](https://business.adobe.com/products/experience-platform/adobe-experience-platform.html) Sie haben mehr Kontrolle und Flexibilität, um praktisch alles online zu optimieren und gleichzeitig die Abhängigkeit von IT-Ressourcen zu reduzieren.

[Integrieren Sie Adobe Dynamic Tag Management](/help/sites-administering/dtm.md) mit AEM, sodass Sie Ihre Dynamic Tag Management-Webeigenschaften für das Tracking von AEM Sites verwenden können.

## Integration mit Adobe Audience Manager {#integrating-with-adobe-audience-manager}

Die Audience Manager-Integration wurde in AEM 6.3 entfernt.

<!-- Search&Promote is end of life as of September 1, 2022 ## Integrating with Search&Promote {#integrating-with-search-promote} -->

<!-- Search&Promote is end of life as of September 1, 2022 Adobe Search&Promote enables marketers to optimizehow visitors browse, find, compare, and select relevant products and content on web and mobile sites. Businesses can easily promote priority items based on business objectives and visitor intent, as well as automate merchandising and promotions activity via KPI-based triggers or metrics. -->

<!-- Search&Promote is end of life as of September 1, 2022 Adobe Search&Promote is a reliable and scalable hosted site search application, capable of scaling to millions of pages or products, for heavily visited online businesses ranging from retail to news sites. It offers unprecedented levels of marketer control and metrics-based relevance. -->

<!-- Search&Promote is end of life as of September 1, 2022 For information about integrating AEM and Search&Promote, see [Integrating with Adobe Search&Promote](/help/sites-administering/search-and-promote.md). -->

## Integrieren mit Adobe Campaign {#integrating-with-adobe-campaign}

Mit [Adobe Campaign](https://business.adobe.com/products/campaign/adobe-campaign.html) können Sie den Inhalt von E-Mail-Bereitstellungen direkt in Adobe Experience Manager verwalten.

Weitere Informationen zur Integration von AEM mit Adobe Campaign finden Sie unter [Integrieren mit Adobe Campaign](/help/sites-administering/campaignstandard.md).