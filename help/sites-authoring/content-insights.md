---
title: Inhalterkenntnisse
seo-title: Content Insight
description: Inhaltserkenntnisse bieten Informationen über die Leistung der Seite mithilfe von Webanalyse und SEO-Empfehlungen
seo-description: Content Insight provides information about page performance using web analytics and SEO recommendation
uuid: 32f5b37c-2a82-462a-9f0a-c19bed46e198
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 60f980fd-049e-43c1-8b5d-60a8279b357a
exl-id: 187f3cde-a0db-4c02-9e8b-08272987a67d
source-git-commit: 245d501d4124d9aaa3f2b12bdb06a5bdd1661e8c
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 36%

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

* Target: Berichte zur Kampagnenaktivität, für die Ihre Seite Angebote enthält.
* BrightEdge: Berichte zu den Seitenfunktionen, die die Sichtbarkeit der Seite für Suchmaschinen verbessern, und empfiehlt Funktionen, die implementiert werden sollten.

Weitere Informationen finden Sie unter [Öffnen von Analytics und Empfehlungen für eine Seite](/help/sites-authoring/ci-analyze.md#opening-analytics-and-recommendations-for-a-page).

## Berichtszeitraum

Berichte zeigen Daten für einen Zeitraum, den Sie bestimmen. Wenn Sie den Berichtszeitraum anpassen, werden die Berichte automatisch mit Daten für diesen Zeitraum aktualisiert. Visuelle Hinweise geben den Zeitpunkt an, zu dem Seitenversionen geändert wurden, sodass Sie die Leistung der einzelnen Versionen vergleichen können.

>[!NOTE]
>
>Die Timeline für das Content Insight-Dashboard finden Sie unter `GMT`.

Sie können auch die Granularität der gemeldeten Daten festlegen, z. B. tägliche, wöchentliche, monatliche oder jährliche Daten.

Siehe [Ändern des Berichtszeitraums](/help/sites-authoring/ci-analyze.md#changing-the-reporting-period).

>[!NOTE]
>
>Für Berichte des Typs „Inhaltserkenntnisse“ muss Ihre bzw. Ihr Admin AEM mit SiteCatalyst, Target und BrightEdge integriert haben. Weitere Informationen finden Sie unter [Integration mit SightCatalyst](/help/sites-administering/adobeanalytics.md), [Integration mit Adobe Target](/help/sites-administering/target.md) und [Integration mit BrightEdge](/help/sites-administering/brightedge.md).

## Der Ansichtsbericht {#the-views-report}

Der Bericht Ansichten umfasst die folgenden Funktionen zur Bewertung des Seiten-Traffics:

* Die Gesamtzahl der Ansichten für eine Seite im Berichtszeitraum.
* Ein Diagramm zur Anzahl der Ansichten im Berichtszeitraum:

   * Gesamtanzahl der Ansichten.
   * Unique Visitors.

![chlimage_1-312](assets/chlimage_1-312.png)

## Der Bericht &quot;Seitendurchschnitt - Interaktion&quot; {#the-page-average-engaged-report}

Der Bericht &quot;Seitendurchschnitt eingebettet&quot;umfasst die folgenden Funktionen zur Bewertung der Seiteneffektivität:

* Die durchschnittliche Zeit, zu der die Seite während des gesamten Berichtszeitraums geöffnet bleibt.
* Ein Diagramm der durchschnittlichen Länge einer Seitenansicht im Berichtszeitraum.

![chlimage_1-313](assets/chlimage_1-313.png)

## Der Quellenbericht {#the-sources-report}

Der Quellenbericht zeigt an, wie Benutzer zur Seite navigiert sind, z. B. aus Suchmaschinenergebnissen oder mithilfe der bekannten URL.

![chlimage_1-314](assets/chlimage_1-314.png)

## Der Bounces-Bericht {#the-bounces-report}

Der Bericht &quot;Absprünge&quot;enthält ein Diagramm, das die Anzahl der Absprünge anzeigt, die für eine Seite im ausgewählten Berichtszeitraum aufgetreten sind.

![chlimage_1-315](assets/chlimage_1-315.png)

## Der Bericht Kampagnenaktivität {#the-campaign-activity-report}

Für jede Kampagne, für die die Seite aktiv ist, wird ein Bericht mit dem Namen *Kampagnenname* Aktivität. Der Bericht zeigt Seitenimpressionen und Konversionen für jedes Segment, für das ein Angebot bereitgestellt wird.

![chlimage_1-316](assets/chlimage_1-316.png)

## SEO Recommendations-Bericht {#the-seo-recommendations-report}

Der SEO Recommendations-Bericht enthält die Ergebnisse der BrightEdge-Analyse für die Seite. Der Bericht ist eine Checkliste der Seitenfunktionen, die anzeigt, welche Funktionen die Seite für die Maximierung der Auffindbarkeit mithilfe von Suchmaschinen aufweist und nicht enthält.

Mit dem Bericht können Sie Aufgaben erstellen, die zu einer Verbesserung der Auffindbarkeit der Seite führen. Recommendations gibt an, dass Aufgaben für die Implementierung der Empfehlung erstellt wurden. Siehe [Zuweisen von Aufgaben für SEO Recommendations](/help/sites-authoring/ci-analyze.md#assigning-tasks-for-seo-recommendations).

![chlimage_1-317](assets/chlimage_1-317.png)
