---
title: Analysieren der Seitenleistung
description: Verwenden Sie die Seite „Inhaltseinblick“, um die Leistung der Seite zu analysieren, die Sie erstellen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: 14484a90-4e44-4c85-9411-b78ed11dc70d
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 100%

---

# Analysieren der Seitenleistung{#analyzing-page-performance}

Öffnen Sie den [Inhaltseinblick](/help/sites-authoring/content-insights.md), um die Leistung der Seite zu analysieren, die Sie erstellen. Konfigurieren Sie den Berichtszeitraum, um Ihre Analyse zu fokussieren.

## Öffnen von Analysen und Empfehlungen für eine Seite {#opening-analytics-and-recommendations-for-a-page}

Gehen Sie wie folgt vor, um die Analysen und Empfehlungen für eine Seite anzuzeigen:

1. Navigieren Sie zu der Seite, die Sie analysieren möchten.
1. Klicken Sie in der Symbolleiste auf **Analysen und Empfehlungen**.

   >[!NOTE]
   >
   >Analysen und Empfehlungen für eine Seite werden nur dann angezeigt, wenn AEM zur [Integration mit Adobe Analytics](/help/sites-administering/adobeanalytics-connect.md) konfiguriert wurde.

   ![screen-shot_2019-03-05at115319](assets/screen-shot_2019-03-05at115319.png)

### Auswählen des Berichtszeitraums {#changing-the-reporting-period}

Ändern Sie die folgenden zeitbezogenen Aspekte der Analyseberichte:

* Der Zeitraum, über den berichtet werden soll.
* Die Granularität der Daten.

Die Tools zum Ändern der zeitbezogenen Aspekte der Berichte werden oben auf der Inhaltseinblick-Seite angezeigt. ![chlimage_1-126](assets/chlimage_1-126.png)

#### Auswählen des Berichtszeitraums {#changing-the-reporting-period-1}

Ändern Sie den Berichtszeitraum der Seite „Inhaltseinblick“, um die Analyse der Seitenaktivität auf einen bestimmten Zeitraum zu konzentrieren. Wenn Sie den Berichtszeitraum ändern, wird der Bericht automatisch aktualisiert. Der schattierte Bereich im Zeitrahmen stellt den Berichtszeitraum dar. Die Daten im Zeitrahmen erhöhen sich von links nach rechts.

![chlimage_1-127](assets/chlimage_1-127.png)

So ändern Sie den Berichtszeitraum einer Inhaltseinblick-Seite:

1. Wenn der Zeitrahmen nicht oben auf der Seite angezeigt wird, klicken Sie auf das Symbol „Zeitrahmen umschalten“.

   ![Zeitrahmen ein/aus](do-not-localize/chlimage_1-22.png)

1. Um das Anfangsdatum des Berichtszeitraums zu ändern, ziehen Sie den Kreis, der links neben dem schattierten Bereich angezeigt wird, zum gewünschten Startdatum.

   Wenn Sie die linke Seite des schattierten Bereichs nicht sehen können, verwenden Sie die Bildlaufleiste, um ihn anzuzeigen.

1. Um das Enddatum des Berichtszeitraums zu ändern, ziehen Sie den Kreis, der rechts neben dem schattierten Bereich angezeigt wird, zum gewünschten Enddatum.

#### Ändern der Granularität des Berichtszeitraums {#changing-the-granularity-of-the-reporting-period}

Ändern Sie die Zeitdauer, die jeder Datenpunkt in einem Bericht umfasst. Wenn beispielsweise die Granularität „Woche“ ausgewählt ist, stellt jeder Datenpunkt im Bericht „Ansichten“ die Anzahl der Ansichten für eine Woche dar.

![screen_shot_2017-11-29at141001](assets/screen_shot_2017-11-29at141001.png)

Die Granularität wirkt sich auf die Berichte aus, die Daten in Bezug auf die Zeit darstellen, z. B. die Berichte „Ansichten“ und „Durchschnittliche Aufenthaltsdauer auf der Seite in Minuten“. Die Granularität wirkt sich auch auf den Maßstab des Zeitrahmens aus.

1. Wenn das Steuerelement für die Granularität nicht angezeigt wird, klicken Sie auf das Symbol „Granularität umschalten“.

   ![chlimage_1-128](assets/chlimage_1-128.png)

1. Klicken Sie auf die gewünschte Granularität. Nach der Auswahl wird der Bericht automatisch entsprechend der Granularität aktualisiert.

### Zuweisen von Aufgaben für SEO-Empfehlungen {#assigning-tasks-for-seo-recommendations}

Verwenden Sie den Bericht „SEO-Empfehlungen“, um Aufgaben zur Verbesserung der Sichtbarkeit von Seiten für Suchmaschinen zu erstellen. Für jede Empfehlung im Bericht, für die kein Häkchen angebracht ist, können Sie eine Aufgabe erstellen, die Sie einem Benutzer zuweisen, um die erforderliche Arbeit durchzuführen.

![chlimage_1-129](assets/chlimage_1-129.png)

Der Status der SEO-Empfehlung gibt an, wenn die Aufgabe erstellt, aber noch nicht abgeschlossen ist.

![chlimage_1-130](assets/chlimage_1-130.png)

Wenn sie erstellt wurde, wird die Aufgabe in der Aufgabenliste des Benutzers angezeigt. Weitere Informationen zu Aufgaben finden Sie unter [Arbeiten mit Aufgaben](/help/sites-authoring/task-content.md).

Gehen Sie wie folgt vor, um eine Aufgabe für eine SEO-Empfehlung zu erstellen.

1. Klicken Sie auf das Informationssymbol für die SEO-Empfehlung.

   ![Informationssymbol](do-not-localize/chlimage_1-23.png)

1. Klicken Sie auf das umkreiste Dreieckssymbol, das neben dem Informationssymbol angezeigt wird.

   ![chlimage_1-131](assets/chlimage_1-131.png)

1. Füllen Sie die angezeigten Formularfelder aus und wählen Sie „Erstellen“ aus:

   * Projekt: Wählen Sie das Projekt aus, in dem die Aufgabe erstellt werden soll.
   * Name: Der Name, der die Aufgabe identifiziert. Der Standardname ist der Titel der SEO-Empfehlung.
   * Zuweisen zu: Wählen Sie den Benutzer aus, dem die Aufgabe zugewiesen werden soll. Geben Sie den Namen der Benutzerin bzw. des Benutzers ein, um die Liste zu filtern.
   * Beschreibung: Eine Beschreibung der Aktivität, die erforderlich ist, um die Aufgabe abzuschließen. Die Standardbeschreibung ist die Information, die der SEO-Empfehlung beigefügt ist.
   * Aufgabenpriorität: Die Priorität der Aufgabe.
   * Fälligkeitsdatum: Das Datum, bis zu dem die Aufgabe abgeschlossen sein soll.

   **Hinweis:** Die Aufgabe, die erstellt wird, enthält den Pfad zu der Seite, für die die SEO-Empfehlung gilt.

1. Klicken Sie auf „Fertig“, um die Meldung „Aufgabe erstellt“ zu schließen.
