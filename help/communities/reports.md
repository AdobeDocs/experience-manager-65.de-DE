---
title: Berichtskonsole
description: Erfahren Sie, wie Sie verschiedene Berichte verwenden, auf die Sie über die Adobe Experience Manager-Autorenumgebung auf verschiedene Arten zugreifen können.
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

# Berichtskonsole {#reports-console}

## Überblick {#overview}

Für AEM Communities gibt es verschiedene Berichte, auf die in der Autorenumgebung auf verschiedene Arten zugegriffen werden kann.

Im Allgemeinen lauten die verschiedenen Berichte:

* [Ansichtsbericht](#views-report)

  Stellt ein Diagramm mit Ansichten von Inhalten bereit, die von Community-Mitgliedern und Site-Besuchern für eine Community-Site erstellt wurden.

* [Beitragsbericht](#posts-report)

  Bietet ein Diagramm mit verschiedenen Arten von Beiträgen von Community-Mitgliedern zu einer beliebigen Community-Site.

Tabellarische Berichte können zur nachfolgenden Verarbeitung im CSV-Format exportiert werden.

## Berichterstellungskonsolen {#reporting-consoles}

### Berichte für Community-Sites {#reports-for-community-sites}

* Von der globalen Navigation: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Berichte]**

* Wählen Sie aus:

   * **[!UICONTROL Zuweisungsbericht]**

      * Erstellen eines Berichts für die ausgewählte Community-Site, den ausgewählten Benutzer oder die ausgewählte Gruppe und die ausgewählte Zuweisung

   * **[!UICONTROL Beitragsbericht]**

      * Generieren eines Berichts für die ausgewählte Community-Site, den Inhaltstyp und den Zeitraum.

   * **[!UICONTROL Ansichtsbericht]**

      * Bericht für ausgewählte Community-Site, Inhaltstyp und Zeitraum generieren.

![Berichte](assets/reports1.png)

## Ansichtsbericht {#views-report}

Die Konsole „Ansichten“ ermöglicht die Erstellung von Berichten über Seitenansichten durch Community-Funktionen für einen bestimmten Zeitraum.

![view-report](assets/view-report.png)

Kriterien für den Bericht auswählen:

* **[!UICONTROL Site]**

  Community-Site auswählen.

* **[!UICONTROL Content-Typ]**

  Sie können entweder Alle Inhalte oder eine der auf der Site vorhandenen Funktionen auswählen.

* **[!UICONTROL Zeitrahmen]**

  Eine der folgenden Optionen auswählen:

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **[!UICONTROL Generieren]**, um den Bericht zu erstellen.

![generate-views](assets/generate-views.png)

## Post-Bericht {#posts-report}

Die Posts-Konsole ermöglicht die Erstellung von Berichten über die Anzahl der Posts zu Community-Funktionen für einen bestimmten Zeitraum.

![post-report](assets/posts-report.png)

Kriterien für den Bericht auswählen:

* **[!UICONTROL Site]**

  Community-Site auswählen.

* **[!UICONTROL Content-Typ]**

  Sie können entweder Alle Inhalte oder eine der auf der Site vorhandenen Funktionen auswählen.

* **[!UICONTROL Zeitrahmen]**

  Eine der folgenden Optionen auswählen:

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **[!UICONTROL Generieren]**, um den Bericht zu erstellen.

![generate-report](assets/generate-posts-report.png)

## Fehlerbehebung {#troubleshooting}

### Keine Community-Sites aufgelistet {#no-community-sites-listed}

Wenn keine Community-Sites aufgelistet sind, stellen Sie sicher, dass Adobe Analytics für eine Site aktiviert wurde. Wenn Sie Berichte zu Zuweisungen auswählen, stellen Sie sicher, dass die Zuweisungsfunktion in der Struktur der Community-Site vorhanden ist.

### Berichte werden nicht in der AEM-Autoreninstanz angezeigt {#reports-do-not-show-in-aem-author-instance}

Wenn in der AEM-Autoreninstanz keine Berichte angezeigt werden, überprüfen Sie die Anpassungen, z. B. die URL-Zuordnung in der Publish-Instanz. Wenn die URL-Zuordnung nur auf der AEM-Publish-Instanz der Communities-Site durchgeführt wird, stellen Sie sicher, dass dieselbe in der AEM-Autoreninstanz in der Konfiguration „Site-Trend **Bericht Social Component Factory** konfiguriert wurde.

![URL-Zuordnung in der AEM-Autoreninstanz](assets/sitetrend.png)
