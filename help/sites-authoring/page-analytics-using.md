---
title: Anzeigen von Seitenanalysedaten zur Messung der Effektivität des Seiteninhalts
seo-title: Seeing Page Analytics Data
description: Verwenden Sie Seitenanalysedaten, um die Effektivität des Seiteninhalts zu messen.
seo-description: Use page analytics data to gauge the effectiveness of their page content
uuid: 5398a5d5-0239-4194-a403-77f5e6fcd741
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5d192a48-c86f-4803-bb0d-0411ac7470f5
docset: aem65
legacypath: /content/help/en/experience-manager/6-4/help/sites-authoring/pa-using.html
exl-id: 2e406512-47fb-451d-b837-0a3898ae1f08
source-git-commit: 75c6bb87bb06c5ac9378ccebf193b5416c080bb1
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 99%

---

# Anzeigen von Seitenanalysedaten{#seeing-page-analytics-data}

Verwenden Sie Seitenanalysedaten, um die Effektivität des Seiteninhalts zu messen.

## In der Konsole sichtbare Analysen {#analytics-visible-from-the-console}

![spad-01](assets/spad-01.png)

Seitenanalysedaten werden in der [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) der Sites-Konsole angezeigt. Wenn die Seiten im Listenformat angezeigt werden, sind die folgenden Spalten standardmäßig verfügbar:

* Seitenansichten
* Unique Visitors
* Zeit auf Seite

Jede Spalte zeigt einen Wert für den aktuellen Berichtszeitraum an und zeigt dazu an, ob der Wert seit dem vorherigen Berichtszeitraum gestiegen oder gesunken ist. Die angezeigten Daten werden alle 12 Stunden aktualisiert.

>[!NOTE]
>
>Um den Aktualisierungszeitraum zu ändern, [konfigurieren Sie das Importintervall](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Öffnen Sie die **Sites**-Konsole, z. B. [https://localhost:4502/sites.html/content](https://localhost:4502/sites.html/content).
1. Klicken oder tippen Sie ganz rechts oben in der Symbolleiste auf das Symbol, um **Listenansicht** auszuwählen. (Das angezeigte Symbol ist von der [aktuellen Ansicht](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) abhängig.)

1. Klicken oder tippen Sie oben rechts in der Symbolleiste auf das Symbol und wählen Sie **Anzeigeeinstellungen** aus. Der Dialog **Spalten konfigurieren** wird geöffnet. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie den Vorgang mit **Aktualisieren**.

   ![spad-02](assets/spad-02.png)

### Auswählen des Berichtszeitraums {#selecting-the-reporting-period}

Wählen Sie den Berichtszeitraum aus, für den Analytics-Daten in der Sites-Konsole angezeigt werden:

* Daten der letzten 30   Daten
* Daten der letzten 90 Tage
* Daten aus diesem Jahr

Der aktuelle Berichtszeitraum wird in der Symbolleiste der Konsole „Sites“ (rechts neben der oberen Symbolleiste) angezeigt. Wählen Sie den gewünschten Berichtszeitraum mit dem Dropdown aus.

![aa-05](assets/aa-05.png)

### Konfigurieren der verfügbaren Datenspalten {#configuring-available-data-columns}

Mitglieder der Benutzergruppe „Analytics-Administratoren“ können die Sites-Konsole konfigurieren, damit Autorinnen und Autoren zusätzliche Analytics-Spalten sehen können.

>[!NOTE]
>
>Wenn ein Seitenbaum untergeordnete Elemente enthält, die verschiedenen Cloud-Konfigurationen von Adobe Analytics zugeordnet sind, können Sie die verfügbaren Datenspalten für die Seiten nicht konfigurieren.

1. Verwenden Sie in der Listenansicht die Ansichtsselektoren (rechts neben der Symbolleiste) und wählen Sie **Anzeigeeinstellungen** und anschließend **Benutzerdefinierte Analysedaten hinzufügen** aus.

   ![spad-03](assets/spad-03.png)

1. Wählen Sie die Metriken aus, die Sie Autoren in der Sites-Konsole bereitstellen möchten, und klicken Sie dann auf **Hinzufügen**.

   Die angezeigten Spalten werden aus Adobe Analytics abgerufen.

   ![aa-16](assets/aa-16.png)

### Öffnen von Inhaltseinblicken mithilfe von Sites {#opening-content-insights-from-sites}

Öffnen Sie [Inhaltseinsicht](/help/sites-authoring/content-insights.md) von der Konsole „Sites“ aus, um die Seiteneffektivität weiter zu untersuchen.

1. Wählen Sie in der Sites-Konsole die Seite aus, für die Sie Inhaltseinblicke anzeigen möchten.
1. Klicken Sie in der Symbolleiste auf das Symbol „Analysen und Empfehlungen“.

   ![Symbol &quot;Analytics and Recommendations&quot;](do-not-localize/chlimage_1-14.png)

## Im Seiten-Editor sichtbare Analysen (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden.
>
>Ab jetzt sollte das [über Adobe Analytics bereitgestellte Activity Map-Plug-in](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de) verwendet werden.
