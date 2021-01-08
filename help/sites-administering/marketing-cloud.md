---
title: Integrieren mit Adobe Marketing Cloud
seo-title: Integrieren mit Adobe Marketing Cloud
description: Es wird beschrieben, wie Sie AEM mit Adobe Marketing Cloud integrieren.
seo-description: Es wird beschrieben, wie Sie AEM mit Adobe Marketing Cloud integrieren.
uuid: 36d71dd3-7fb0-4237-99d3-4fbb2e162e7b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: ba496f6a-c9aa-49b5-8207-8633748d2c17
translation-type: tm+mt
source-git-commit: 801d57bbe8a1bede6dcb4bf7884e5f71ddea1e83
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 75%

---


# Integrieren mit Adobe Marketing Cloud{#integrating-with-the-adobe-marketing-cloud}

[Adobe Marketing Cloud](https://www.adobe.com/solutions/digital-marketing.html) enthält leistungsstarke Produkte für die Web-Analyse und Website-Optimierung, die Ihnen verwertbare Echtzeitdaten und Einblicke liefern, damit Sie Online-Initiativen erfolgreich gestalten können. Sie erhalten eine integrierte und offene Plattform für die Optimierung Ihres Online-Business. Die Cloud besteht aus integrierten Anwendungen, mit denen Kundeneinblicke gesammelt werden können, die sehr nützlich sind, um die Kundenakquise, Konversions- und Bindungsmaßnahmen sowie die Erstellung und Verteilung von Inhalten zu optimieren.

Mit Adobe Experience Manager (AEM) können Sie nahtlos in die folgenden Produkte der Adobe Marketing Cloud integrieren:

* Über Adobe Analytics erhalten Marketing-Experten in Echtzeit verwertbare Daten zu Online-Strategien und Marketinginitiativen.
* Mit Adobe Target haben Marketing-Experten die Möglichkeit, die Relevanz ihrer Online-Inhalte für Kunden immer weiter zu erhöhen, und dies führt zu einer größeren Zahl von Konversionen.
* Mithilfe von Adobe Scene7 wird die Medienverwaltung automatisiert, die Webveröffentlichung optimiert und die Weboberfläche erweitert – alles innerhalb einer gehosteten Umgebung.
* Adobe Dynamic Tag Management bietet Marketing-Experten intuitive Tools zum schnellen und einfachen Verwalten einer unbegrenzten Zahl von Adobe- und Drittanbieter-Tags.
* Mit Adobe Search&amp;Promote können Marketing-Experten die Suchergebnisse für ihre Websites steuern und optimieren.
* Mit Adobe Campaign können Sie den Inhalt von E-Mail-Bereitstellungen direkt in Adobe Experience Manager verwalten.

Darüber hinaus können Sie [AEM mit Creative Cloud](/help/assets/aem-cc-folder-sharing-best-practices.md) und mit [Drittanbieterdiensten](/help/sites-administering/third-party-services.md) integrieren.

## Integration mit Adobe Analytics {#integrating-with-adobe-analytics}

[Adobe ](https://www.omniture.com/en/products/analytics/sitecatalyst) Analytics ist die branchenführende Lösung, die E-Marketingexperten eine zentrale Stelle zur Messung, Analyse und Optimierung integrierter Daten aus allen Onlineinitiativen in mehreren Marketing-Kanälen bietet. Die Lösung ermöglicht Marketing-Experten die Web-Analyse in Echtzeit und mit verwertbaren Ergebnissen für digitale Strategien und Marketing-Initiativen. Adobe Analytics unterstützt Marketing-Experten dabei, schnell die profitabelsten Pfade einer Website zu ermitteln, Traffic zu segmentieren, um wertvolle Webbesucher zu identifizieren, herauszufinden, wohin Besucher die Website verlassen, und entscheidende Erfolgsmetriken für Online-Marketing-Kampagnen zu finden.

Sie können Adobe Analytics nutzen, um Daten Ihrer Website zu analysieren.

Durch die Integration mit Adobe Analytics haben Sie folgende Möglichkeiten:

* Aktivieren Sie die Analytics-Benutzerverfolgung.
* Zuweisen von Ausführungsmodi (z. B. Erstellen, Veröffentlichen) zu unterschiedlichen Report Suites
* Übermitteln von Client-Kontextvariablen als Konversionsvariablen oder Traffic-Eigenschaften
* Verwenden von vordefinierten Variablenzuweisungen
* Konfigurieren von gesamten Websiteabschnitten auf einmal
* Nachverfolgen von benutzerdefinierten Ereignissen

Weitere Informationen zur Integration von AEM mit Analytics finden Sie unter [Integrieren mit Adobe Analytics](/help/sites-administering/adobeanalytics.md).

Der [Opt-in-Assistent](/help/sites-administering/opt-in.md) erleichtert die Durchführung der Integration.

## Integrieren mit Adobe Target {#integrating-with-adobe-target}

[Adobe Target wird von Marketing-Experten genutzt, um Online-Tests zu entwerfen und auszuführen, in kurzer Zeit Zielgruppensegmente zu erstellen (anhand des Verhaltens) und das Targeting für Inhalte und Online-Erlebnisse zu automatisieren.](https://www.omniture.com/en/products/conversion/test-and-target)

Die Wünsche der Onlinekunden entwickeln sich ständig weiter und für die Vielzahl von Websites und Inhaltsquellen, die zur Auswahl stehen, werden relevante und auch personalisierte Inhalte erwartet. Um eine Online-Zielgruppe zu erreichen, ist es wichtig, dass Experten für Online-Marketing schnell identifizieren, welche Angebote und Inhalte für ihre Zielgruppen relevant und interessant sind. Basierend auf diesem Wissen müssen Marketing-Experten die Möglichkeit haben, ihre Website ständig weiterzuentwickeln und die entsprechenden Inhalte auf unterschiedliche Zielgruppen auszurichten.

Unter [Integrieren mit Adobe Target](/help/sites-administering/target.md) wird beschrieben, wie Sie Ihre Website mit Target integrieren.

Der [Opt-in-Assistent](/help/sites-administering/opt-in.md) erleichtert die Durchführung der Integration.

## Opt-in für Analytics und Target {#opting-in-to-analytics-and-target}

AEM verfügt über ein einfaches Opt-in-Verfahren für die Integration mit Adobe Analytics und Adobe Target. Wenn Sie sich als Administrator anmelden und zur Projektekonsole navigieren, wird ein Opt-in-Assistent angezeigt.

![chlimage_1-107](assets/chlimage_1-107a.png)

Führen Sie den Opt-in für die Integration mit Analytics bzw. Target durch, um die Nutzung der Funktionen für das Seiten-Tracking und die Analyse sowie für die Personalisierung zu ermöglichen. Für den Opt-in müssen Sie Ihre Benutzerkontoinformationen und die nachverfolgten Seiten angeben.

Weitere Informationen finden Sie unter [Opt-in für Analytics und Target](/help/sites-administering/opt-in.md).

## Integration mit der Adobe Dynamic Media Classic {#integrating-with-scene}

Adobe Dynamic Media Classic ist eine gehostete Lösung zum Veröffentlichen, Verwalten, Erweitern und Bereitstellen von dynamischen Marketing-Assets und Rich-Visual-Merchandising für Web-, Mobil-, E-Mail-, Social Media-, Internet-verbundene Displays und Print-Medien.

In AEM können Sie digitale Assets direkt von AEM nach Dynamic Media Classic veröffentlichen und digitale Assets von Dynamic Media Classic nach AEM veröffentlichen.

Darüber hinaus können Sie in Dynamic Media Classic veröffentlichte Assets in verschiedenen Viewern wie &quot;Einfach vergrößern&quot;und &quot;Einfach&quot;AEM Ansicht ausführen.

Weitere Informationen zur Integration AEM in Dynamic Media Classic finden Sie in der Dokumentation [Integration mit Dynamic Media Classic](/help/sites-administering/scene7.md).

## Integrieren mit Adobe Dynamic Tag Management {#integrating-with-adobe-dynamic-tag-management}

[Adobe Dynamic Tag Management bietet Marketing-Experten intuitive Tools zum schnellen und einfachen Verwalten einer unbegrenzten Zahl von Adobe- und Drittanbieter-Tags. ](https://www.adobe.com/solutions/digital-marketing/dynamic-tag-management.html) Sie haben mehr Kontrolle und Flexibilität, um nahezu alles online zu optimieren – und reduzieren damit gleichzeitig auch Ihre Abhängigkeit von IT-Ressourcen.

[Integrieren Sie Adobe Dynamic Tag Management](/help/sites-administering/dtm.md) mit AEM, sodass Sie Ihre Dynamic Tag Management-Webeigenschaften für das Tracking von AEM Sites verwenden können.

## Integrieren mit Adobe Audience Manager {#integrating-with-adobe-audience-manager}

Die Audience Manager-Integration wurde in AEM 6.3 entfernt.

## Integrieren mit Search&amp;Promote {#integrating-with-search-promote}

[Adobe Search&amp;](https://www.omniture.com/en/products/conversion/search-and-promote) Promote ermöglicht es Marketingexperten, Besucher beim Durchsuchen, Suchen, Vergleichen und Auswählen relevanter Produkte und Inhalte auf Websites und mobilen Sites zu optimieren. Unternehmen können einfach Artikel mit Priorität auf Grundlage von Geschäftszielen und Besucherwünschen bewerben und Merchandising- und Promotion-Aktivitäten mithilfe kennzahlbasierter Trigger oder Metriken automatisieren.

Adobe Search&amp;Promote ist eine zuverlässige und skalierbare gehostete Anwendung für Websitesuchen, die für Online-Unternehmen mit hohen Zugriffszahlen eine Skalierung auf Millionen von Seiten oder Produkten ermöglicht. Die Spanne kann hierbei von Websites von Einzelhändlern bis zu Nachrichtenwebsites reichen. Es wird eine bisher unerreichte Steuerung durch die Marketing-Experten und eine auf Metriken basierende Relevanz erzielt.

Weitere Informationen zur Integration von AEM und Search&amp;Promote finden Sie unter [Integrieren mit Search&amp;Promote](/help/sites-administering/search-and-promote.md).

## Integrieren mit Adobe Campaign  {#integrating-with-adobe-campaign}

Mit [Adobe Campaign](https://www.adobe.com/solutions/campaign-management.html) können Sie den Inhalt von E-Mail-Bereitstellungen direkt in Adobe Experience Manager verwalten.

Informationen zur Integration AEM in Adobe Campaign finden Sie unter [Integration in Adobe Campaign](/help/sites-administering/campaignstandard.md).

## Integrieren mit Livefyre {#integrating-with-livefyre}

Informationen zu AEM und Livefyre:

* [Erste Schritte mit Livefyre](https://answers.livefyre.com/developers/getting-started)

* [Livefyre und AEM](https://answers.livefyre.com/product/livefyre-for-adobe-experience-manager-aem/livefyre-for-adobe-experience-manager/)

