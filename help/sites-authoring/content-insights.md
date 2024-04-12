---
title: Inhalterkenntnisse
description: Inhaltserkenntnisse bieten Informationen über die Leistung der Seite mithilfe von Webanalyse und SEO-Empfehlungen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 187f3cde-a0db-4c02-9e8b-08272987a67d
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 100%

---

# Inhalterkenntnisse{#content-insight}

Inhaltserkenntnisse bieten Informationen über die Leistung der Seite mithilfe von Web-Analyse und SEO-Empfehlungen. Verwenden Sie Inhaltserkenntnisse, um Entscheidungen darüber zu treffen, wie Sie Seiten ändern, oder um zu erfahren, wie frühere Entscheidungen die Leistung geändert haben. Für jede Seite, die Sie bearbeiten, können Sie Inhaltserkenntnisse öffnen, um die Seite zu analysieren.

![chlimage_1-311](assets/chlimage_1-311.png)

Das Layout der Seite „Inhaltserkenntnisse“ ändert sich je nach Bildschirmabmessungen und Ausrichtung des Geräts, das Sie verwenden.

## Berichtsdaten

Die Seite „Inhaltserkenntnisse“ enthält Berichte, die Adobe SiteCatalyst-, Adobe Target-, Adobe Social- und BrightEdge-Daten verwenden:

* SiteCatalyst: Berichte für die folgenden Metriken sind verfügbar:

   * Seitenansichten
   * Durchschnittliche Besuchszeit pro Seite
   * Quellen

* Target: Berichte über Kampagnenaktivität, für die Ihre Seite Angebote enthält.
* BrightEdge: Berichte über die Seitenfunktionen, die die Sichtbarkeit der Seite für Suchmaschinen verbessern, mit Empfehlungen für Funktionen, die implementiert werden sollten.

Weitere Informationen finden Sie unter [Öffnen von Analytics und Empfehlungen für eine Seite](/help/sites-authoring/ci-analyze.md#opening-analytics-and-recommendations-for-a-page).

## Berichtszeitraum

Berichte zeigen Daten für einen Zeitraum, den Sie bestimmen. Wenn Sie den Berichtszeitraum anpassen, werden die Berichte automatisch mit Daten für diesen Zeitraum aktualisiert. Visuelle Hinweise geben die Zeit an, zu der Seitenversionen geändert wurden, damit Sie die Leistung jeder Version vergleichen können.

>[!NOTE]
>
>Die Timeline für das Content Insight-Dashboard finden Sie unter `GMT`.

Sie können außerdem die Granularität der berichteten Daten angeben, z. B. können Sie tägliche, wöchentliche, monatliche oder jährliche Daten sehen.

Weitere Informationen finden Sie unter [Ändern des Berichtszeitraums](/help/sites-authoring/ci-analyze.md#changing-the-reporting-period).

>[!NOTE]
>
>Für Berichte des Typs „Inhaltserkenntnisse“ muss Ihre bzw. Ihr Admin AEM mit SiteCatalyst, Target und BrightEdge integriert haben. Weitere Informationen finden Sie unter [Integration mit SightCatalyst](/help/sites-administering/adobeanalytics.md), [Integration mit Adobe Target](/help/sites-administering/target.md) und [Integration mit BrightEdge](/help/sites-administering/brightedge.md).

## Der Ansichtsbericht {#the-views-report}

Der Ansichtsbericht umfasst die folgenden Funktionen für die Bewertung des Traffics auf der Seite:

* Die Gesamtzahl der Ansichten für eine Seite während des Berichtszeitraums.
* Ein Diagramm der Anzahl der Ansichten während des Berichtszeitraums:

   * Gesamtzahl der Ansichten
   * Unique Visitors.

![chlimage_1-312](assets/chlimage_1-312.png)

## Der Bericht über die durchschnittliche Aufenthaltsdauer auf der Seite {#the-page-average-engaged-report}

Der Bericht über die durchschnittliche Aufenthaltsdauer auf der Seite umfasst die folgenden Funktionen für die Bewertung der Seiteneffektivität:

* Die durchschnittliche Besuchszeit, während der die Seite geöffnet bleibt, für den gesamten Berichtzeitraum.
* Ein Graph der durchschnittlichen Dauer einer Seitenansicht während des Berichtszeitraums.

![chlimage_1-313](assets/chlimage_1-313.png)

## Der Quellenbericht {#the-sources-report}

Der Quellenbericht gibt an, wie Benutzende zur Seite gekommen sind, zum Beispiel von Suchmaschinen-Ergebnissen aus oder mithilfe der bekannten URL.

![chlimage_1-314](assets/chlimage_1-314.png)

## Der Absprungbericht {#the-bounces-report}

Der Absprungbericht umfasst ein Diagramm, das die Anzahl der Absprünge anzeigt, die über den ausgewählten Berichtszeitraum für eine Seite aufgetreten sind.

![chlimage_1-315](assets/chlimage_1-315.png)

## Der Kampagnenaktivitätsbericht {#the-campaign-activity-report}

Für jede Kampagne, für die die Seite aktiv ist, wird ein Bericht namens *Kampagnennamenaktivität* angezeigt. Der Bericht zeigt Seitenimpressionen und Konversionen für jedes Segment, für das ein Angebot bereitgestellt wird.

![chlimage_1-316](assets/chlimage_1-316.png)

## Der SEO-Empfehlungsbericht {#the-seo-recommendations-report}

Der SEO-Empfehlungsbericht enthält die Ergebnisse der BrightEdge-Analyse für die Seite. Der Bericht ist eine Checkliste der Seitenfunktionen, die angibt, welche Funktionen die Seite enthält bzw. nicht enthält, um die Auffindbarkeit mithilfe von Suchmaschinen zu maximieren.

Mit dem Bericht können Sie Aufgaben erstellen, die zu einer Verbesserung der Auffindbarkeit der Seite führen. Empfehlungen weisen darauf hin, dass Aufgaben zur Implementierung der Empfehlung erstellt wurden. Weitere Informationen finden Sie unter [Zuweisen von Aufgaben für SEO-Empfehlungen](/help/sites-authoring/ci-analyze.md#assigning-tasks-for-seo-recommendations).

![chlimage_1-317](assets/chlimage_1-317.png)
