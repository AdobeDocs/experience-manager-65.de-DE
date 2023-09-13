---
title: Berichtkonsole
description: Erfahren Sie, wie Sie auf verschiedene Berichte zugreifen können, auf die Sie auf verschiedene Weise über die Adobe Experience Manager-Autorenumgebung zugreifen können.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 2aff2ffe-ba6f-4cc9-a126-40fc2a1161e2
source-git-commit: 5af420c8e95fed88a8516cce27b8bbc7d3974e75
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 9%

---

# Berichtkonsole {#reports-console}

## Übersicht {#overview}

Für AEM Communities gibt es verschiedene Berichte, auf die über die Autorenumgebung auf verschiedene Weise zugegriffen werden kann.

Die verschiedenen Berichte sind im Allgemeinen:

* [Ansichtsbericht](#views-report)

  Bietet eine Grafik mit den Inhalten von Community-Mitgliedern und Site-Besuchern für jede Community-Site.

* [Post-Bericht](#posts-report)

  Bietet eine Grafik verschiedener Arten von Beiträgen von Community-Mitgliedern zu jeder Community-Site.

Tabellarische Berichte können zur nachfolgenden Verarbeitung im CSV-Format exportiert werden.

## Reporting-Konsolen {#reporting-consoles}

### Berichte für Community-Sites {#reports-for-community-sites}

* Über die globale Navigation: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** >  **[!UICONTROL Berichte]**

* Wählen Sie aus:

   * **[!UICONTROL Zuweisungsbericht]**

      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den ausgewählten Benutzer oder die Gruppe und die Zuweisung.

   * **[!UICONTROL Post-Bericht]**

      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den Inhaltstyp und den Zeitraum.

   * **[!UICONTROL Ansichtsbericht]**

      * einen Bericht für die ausgewählte Community-Site, den Content-Typ und den Zeitraum erstellen.

![Berichte](assets/reports1.png)

## Ansichtsbericht {#views-report}

Mit der Konsole &quot;Ansichten&quot;können Berichte von Community-Funktionen für einen bestimmten Zeitraum bei Seitenansichten generiert werden.

![view-report](assets/view-report.png)

Wählen Sie die Berichtskriterien aus:

* **[!UICONTROL Site]**

  Wählen Sie eine Community-Site aus.

* **[!UICONTROL Inhaltstyp]**

  Sie können Alle Inhalte auswählen oder eine der Funktionen auswählen, die auf der Site vorhanden sind.

* **[!UICONTROL Zeitrahmen]**

  Wählen Sie eine der folgenden Optionen aus:

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Auswählen **[!UICONTROL Erzeugen]** , um den Bericht zu erstellen.

![generate-views](assets/generate-views.png)

## Post-Bericht {#posts-report}

Die Konsole Beiträge ermöglicht die Erstellung von Berichten über die Anzahl der Beiträge zu Community-Funktionen für einen bestimmten Zeitraum.

![Posts-Bericht](assets/posts-report.png)

Wählen Sie die Berichtskriterien aus:

* **[!UICONTROL Site]**

  Wählen Sie eine Community-Site aus.

* **[!UICONTROL Inhaltstyp]**

  Sie können Alle Inhalte auswählen oder eine der Funktionen auswählen, die auf der Site vorhanden sind.

* **[!UICONTROL Zeitrahmen]**

  Wählen Sie eine der folgenden Optionen aus:

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Auswählen **[!UICONTROL Erzeugen]** , um den Bericht zu erstellen.

![generate-report](assets/generate-posts-report.png)

## Fehlerbehebung {#troubleshooting}

### Keine Community-Sites aufgeführt {#no-community-sites-listed}

Wenn keine Community-Sites aufgelistet sind, stellen Sie sicher, dass Adobe Analytics für eine Site aktiviert wurde. Stellen Sie bei der Auswahl von Berichten zu Zuweisungen sicher, dass sich die Zuweisungsfunktion in der Struktur der Community-Site befindet.

### Berichte werden in AEM Autoreninstanz nicht angezeigt {#reports-do-not-show-in-aem-author-instance}

Wenn Berichte nicht in der AEM-Autoreninstanz angezeigt werden, suchen Sie nach den Anpassungen, z. B. nach der URL-Zuordnung in der Veröffentlichungsinstanz. Wenn die URL-Zuordnung nur auf der AEM Veröffentlichungsinstanz der Communities-Site erfolgt, stellen Sie sicher, dass dasselbe in der AEM-Autoreninstanz in **Site-Trend-Bericht - Social-KomponentenFactory** Konfiguration.

![URL-Zuordnung in AEM Author](assets/sitetrend.png)
