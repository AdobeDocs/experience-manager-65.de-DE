---
title: Berichtkonsole
description: Erfahren Sie, wie Sie verschiedene Berichte verwenden, auf die Sie in der Adobe Experience Manager-Autorenumgebung auf verschiedene Weise zugreifen können.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 2aff2ffe-ba6f-4cc9-a126-40fc2a1161e2
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 6%

---

# Berichtkonsole {#reports-console}

## Überblick {#overview}

Für AEM Communities gibt es verschiedene Berichte, auf die über die Autorenumgebung auf verschiedene Weise zugegriffen werden kann.

Die verschiedenen Berichte sind im Allgemeinen:

* [Bericht &quot;Ansichten&quot;](#views-report)

  Bietet eine Grafik mit den Inhalten von Community-Mitgliedern und Site-Besuchern für jede Community-Site.

* [Bericht zu Beiträgen](#posts-report)

  Bietet eine Grafik verschiedener Arten von Beiträgen von Community-Mitgliedern zu jeder Community-Site.

Tabellarische Berichte können zur nachfolgenden Verarbeitung im CSV-Format exportiert werden.

## Reporting-Konsolen {#reporting-consoles}

### Berichte für Community-Sites {#reports-for-community-sites}

* Von der globalen Navigation: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Berichte]**

* Wählen Sie aus:

   * **[!UICONTROL Zuweisungsbericht]**

      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den ausgewählten Benutzer oder die Gruppe und die Zuweisung.

   * **[!UICONTROL Bericht zu Beiträgen]**

      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den Inhaltstyp und den Zeitraum.

   * **[!UICONTROL Bericht &quot;Ansichten&quot;]**

      * einen Bericht für die ausgewählte Community-Site, den Content-Typ und den Zeitraum erstellen.

![reports](assets/reports1.png)

## Ansichtsbericht {#views-report}

Mit der Konsole &quot;Ansichten&quot;können Berichte von Community-Funktionen für einen bestimmten Zeitraum bei Seitenansichten generiert werden.

![view-report](assets/view-report.png)

Wählen Sie die Berichtskriterien aus:

* **[!UICONTROL Site]**

  Wählen Sie eine Community-Site aus.

* **[!UICONTROL Content-Typ]**

  Sie können Alle Inhalte auswählen oder eine der Funktionen auswählen, die auf der Site vorhanden sind.

* **[!UICONTROL Zeitrahmen]**

  Wählen Sie eine der folgenden Optionen aus:

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **[!UICONTROL Erzeugen]** aus, um den Bericht zu erstellen.

![generate-views](assets/generate-views.png)

## Post-Bericht {#posts-report}

Die Konsole Beiträge ermöglicht die Erstellung von Berichten über die Anzahl der Beiträge zu Community-Funktionen für einen bestimmten Zeitraum.

![post-report](assets/posts-report.png)

Wählen Sie die Berichtskriterien aus:

* **[!UICONTROL Site]**

  Wählen Sie eine Community-Site aus.

* **[!UICONTROL Content-Typ]**

  Sie können Alle Inhalte auswählen oder eine der Funktionen auswählen, die auf der Site vorhanden sind.

* **[!UICONTROL Zeitrahmen]**

  Wählen Sie eine der folgenden Optionen aus:

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **[!UICONTROL Erzeugen]** aus, um den Bericht zu erstellen.

![generate-report](assets/generate-posts-report.png)

## Fehlerbehebung {#troubleshooting}

### Keine Community-Sites aufgeführt {#no-community-sites-listed}

Wenn keine Community-Sites aufgelistet sind, stellen Sie sicher, dass Adobe Analytics für eine Site aktiviert wurde. Stellen Sie bei der Auswahl von Berichten zu Zuweisungen sicher, dass sich die Zuweisungsfunktion in der Struktur der Community-Site befindet.

### Berichte werden in AEM Autoreninstanz nicht angezeigt {#reports-do-not-show-in-aem-author-instance}

Wenn Berichte nicht in der AEM-Autoreninstanz angezeigt werden, suchen Sie nach den Anpassungen, z. B. nach der URL-Zuordnung in der Publish-Instanz. Wenn die URL-Zuordnung nur auf der AEM Publish-Instanz der Communities-Site erfolgt, stellen Sie sicher, dass dasselbe in der AEM-Autoreninstanz in der Konfiguration **Site-Trend-Bericht Social Component Factory** konfiguriert wurde.

![URL-Zuordnung in AEM Autoreninstanz](assets/sitetrend.png)
