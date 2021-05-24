---
title: Anzeigen von Seitenanalysedaten
seo-title: Anzeigen von Seitenanalysedaten
description: Verwenden Sie Seitenanalysedaten, um die Wirkung des Seiteninhalts zu messen.
seo-description: Verwenden Sie Seitenanalysedaten, um die Wirkung des Seiteninhalts zu messen.
uuid: 5398a5d5-0239-4194-a403-77f5e6fcd741
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5d192a48-c86f-4803-bb0d-0411ac7470f5
docset: aem65
legacypath: /content/help/en/experience-manager/6-4/help/sites-authoring/pa-using.html
exl-id: 2e406512-47fb-451d-b837-0a3898ae1f08
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 86%

---

# Anzeigen von Seitenanalysedaten{#seeing-page-analytics-data}

Verwenden Sie Seitenanalysedaten, um die Wirkung des Seiteninhalts zu messen.

## In der Konsole sichtbare Analysedaten  {#analytics-visible-from-the-console}

![spad-01](assets/spad-01.png)

Seitenanalysedaten werden in der [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) der Konsole „Sites“ angezeigt. Wenn Seiten im Listenformat angezeigt werden, sind die folgenden Spalten standardmäßig verfügbar:

* Seitenansichten
* Individuelle Besucher
* Zeit auf Seite

Jede Spalte zeigt einen Wert für den aktuellen Berichtszeitraum an und gibt außerdem an, ob der Wert sich seit dem vorherigen Berichtszeitraum erhöht oder verringert hat. Die Daten, die Sie sehen, werden alle 12 Stunden aktualisiert.

>[!NOTE]
>
>Zum Ändern des Aktualisierungszeitraums [konfigurieren Sie das Importintervall](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Öffnen Sie die Konsole **Sites** . zum Beispiel [https://localhost:4502/sites.html/content](https://localhost:4502/sites.html/content)
1. Klicken oder tippen Sie ganz rechts oben in der Symbolleiste auf das Symbol, um **Listenansicht** auszuwählen. (Das angezeigte Symbol ist von der [aktuellen Ansicht](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) abhängig.)

1. Klicken oder tippen Sie wieder ganz rechts oben in der Symbolleiste auf das Symbol und wählen Sie dann **Anzeigeeinstellungen** aus. Das Dialogfeld **Spalten konfigurieren** wird geöffnet. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie den Vorgang mit **Aktualisieren**.

   ![spad-02](assets/spad-02.png)

### Auswählen des Berichtszeitraums {#selecting-the-reporting-period}

Wählen Sie den Berichtszeitraum aus, für den Analysedaten in der Konsole „Sites“ angezeigt werden:

* Daten der  Daten
* Daten der letzten 90 Tage
* Daten aus diesem Jahr

Der aktuelle Berichtszeitraum wird in der Symbolleiste der Konsole „Sites“ (rechts neben der oberen Symbolleiste) angezeigt. Wählen Sie den gewünschten Berichtszeitraum mit dem Dropdown aus.

![aa-05](assets/aa-05.png)

### Konfigurieren der verfügbaren Datenspalten {#configuring-available-data-columns}

Mitglieder der Analyse-Administratorbenutzergruppe können die Konsole „Sites“ so konfigurieren, dass Autoren zusätzliche Analysespalten sehen können.

>[!NOTE]
>
>Wenn eine Struktur von Seiten untergeordnete Elemente enthält, die mit verschiedenen Adobe Analytics-Cloudkonfigurationen verbunden sind, können Sie die verfügbaren Datenspalten für die Seiten nicht konfigurieren.

1. Verwenden Sie in der Listenansicht die Ansichtsauswahl (rechts neben der Symbolleiste), wählen Sie **Ansichtseinstellungen** und dann **Benutzerdefinierte Analytics-Daten hinzufügen**.

   ![spad-03](assets/spad-03.png)

1. Wählen Sie die Metriken aus, die Sie Autoren in der Sites-Konsole bereitstellen möchten, und klicken Sie dann auf **Hinzufügen**.

   Die angezeigten Spalten werden aus Adobe Analytics abgerufen.

   ![aa-16](assets/aa-16.png)

### Öffnen von Inhaltseinblicken mithilfe von Sites {#opening-content-insights-from-sites}

Öffnen Sie [Content Insight](/help/sites-authoring/content-insights.md) in der Sites-Konsole, um die Seiteneffektivität weiter zu untersuchen.

1. Wählen Sie in der Konsole „Sites“ die Seite aus, für die Sie Inhaltseinblicke sehen möchten.
1. Klicken Sie in der Symbolleiste auf das Symbol „Analyse und Empfehlungen“.

   ![](do-not-localize/chlimage_1-14.png)

## Im Seiteneditor sichtbare Analysedaten (Activity Map)  {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden.
>
>Das [ActivityMap-Plugin, das von Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de#activity-map) bereitgestellt wird, sollte jetzt verwendet werden.
