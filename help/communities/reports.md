---
title: Berichte-Konsole
seo-title: Berichte-Konsole
description: Erfahren Sie, wie Sie auf Berichte zugreifen können
seo-description: Erfahren Sie, wie Sie auf Berichte zugreifen können
uuid: 7bb15a15-077b-4bfb-aaf4-50fddc67f237
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: fde053ff-b671-456b-869c-81f16ea1f1be
docset: aem65
role: Admin
exl-id: 2aff2ffe-ba6f-4cc9-a126-40fc2a1161e2
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 8%

---

# Berichte-Konsole {#reports-console}

## Übersicht {#overview}

Für AEM Communities gibt es verschiedene Berichte, auf die über die Autorenumgebung auf verschiedene Weise zugegriffen werden kann.

Die verschiedenen Berichte sind im Allgemeinen:

* [Zuweisungsbericht](#assignments-report)

   Für eine [Aktivierungs-Community](/help/communities/overview.md#enablement-community) bietet eine Übersicht über den Fortschritt der Lernenden bei ihrer Zuweisung, einschließlich eines zugehörigen Punkts bei der Implementierung des SCORM-Standards.

* [Ansichtsbericht](#views-report)

   Bietet eine Grafik mit den Inhalten von Community-Mitgliedern und Site-Besuchern für jede Community-Site.

* [Post-Bericht](#posts-report)

   Bietet eine Grafik verschiedener Arten von Beiträgen von Community-Mitgliedern zu jeder Community-Site.

Wenn [Adobe Analytics aktiviert ist](/help/communities/sites-console.md#analytics), enthalten Berichte die Anzahl der Ansichten, Wiedergaben, Kommentare und Bewertungen für jede Aktivierungsressource im Zeitverlauf.

Tabellarische Berichte können zur nachfolgenden Verarbeitung im CSV-Format exportiert werden.

## Reporting-Konsolen {#reporting-consoles}

### Berichte für Community-Sites {#reports-for-community-sites}

* Über die globale Navigation: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Berichte]**

* Wählen Sie aus:

   * **[!UICONTROL Zuweisungsbericht]**

      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den ausgewählten Benutzer oder die Gruppe und die Zuweisung.
   * **[!UICONTROL Post-Bericht]**

      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den Inhaltstyp und den Zeitraum.
   * **[!UICONTROL Ansichtsbericht]**

      * einen Bericht für die ausgewählte Community-Site, den Content-Typ und den Zeitraum erstellen.



![Berichte](assets/reports1.png)

### Berichte für Aktivierungsressourcen und Lernpfade {#reports-for-enablement-resources-and-learning-paths}

* Über die globale Navigation: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Ressourcen]**

* Wählen Sie eine vorhandene Aktivierungs-Community-Site aus:

   * Wählen Sie das Symbol **Bericht** aus, um Berichte zu erstellen, die alle Aktivierungsressourcen abdecken.
   * Wählen Sie einen Lernpfad für die Aktivierung aus.
   * Wählen Sie das Symbol **Bericht** aus, um Berichte für Folgendes zu generieren:

      * Die enthaltenen Aktivierungsressourcen.
      * Die dem Lernpfad zugewiesenen Lernenden.

* Diese Berichte bieten Folgendes:

   * Tabellendaten, als CSV heruntergeladen:

      * Identifizieren von Lernenden
      * Ihr Status
      * Ob zugewiesen oder über Katalog aufgerufen
      * Anzahl der abgegebenen Kommentare
      * Sternbewertung

Weitere Informationen finden Sie im Abschnitt [Berichte](/help/communities/resources.md#report) der Ressourcenkonsole.

## Zuweisungsbericht {#assignments-report}

In der Konsole &quot;Zuweisungen&quot;können Berichte nach der Aktivierungs-Community-Site, Benutzern oder Gruppen und der Zuweisung gefiltert werden.

Der Bericht enthält Informationen über ihren Fortschritt sowie etwaige Kommentare oder Bewertungen.

![assignment-report](assets/assignment-report.png)

Wählen Sie die Kriterien für den Bericht aus:

* **Website**

   Wählen Sie eine Aktivierungs-Community-Site aus.

* **Benutzer oder Gruppe**
   * Wählen Sie Benutzer aus, um einen Bericht für einen Lernenden zu erstellen.
   * Wählen Sie Gruppe aus, um einen Bericht für eine Gruppe von Lernenden zu erstellen.

   Der Tunneldienst greift über die Veröffentlichungsumgebung auf Mitglieder und Mitgliedergruppen zu.

* **Zuweisung**

   Wählen Sie aus den Aktivierungsressourcen, die den ausgewählten Lernenden zugewiesen sind.

Wählen Sie **Generate** aus, um den Bericht zu erstellen:

![generate-report](assets/generate-assignment-report.png)

## Ansichtsbericht {#views-report}

Mit der Konsole &quot;Ansichten&quot;können Berichte zu Seitenansichten von Community-Funktionen für einen bestimmten Zeitraum generiert werden.

![view-report](assets/view-report.png)

Wählen Sie die Kriterien für den Bericht aus:

* **[!UICONTROL Website]**

   Wählen Sie eine Community-Site aus.

* **[!UICONTROL Inhaltstyp]**

   Sie können Alle Inhalte auswählen oder eine der auf der Site vorhandenen Funktionen auswählen.

* **[!UICONTROL Zeitrahmen]**

   Wählen Sie eine der folgenden Optionen aus:

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **[!UICONTROL Generate]** aus, um den Bericht zu erstellen.

![generate-views](assets/generate-views.png)

## Post-Bericht {#posts-report}

Die Konsole Beiträge ermöglicht die Erstellung von Berichten über die Anzahl der Beiträge zu Community-Funktionen für einen bestimmten Zeitraum.

![Posts-Bericht](assets/posts-report.png)

Wählen Sie die Kriterien für den Bericht aus:

* **[!UICONTROL Website]**

   Wählen Sie eine Community-Site aus.

* **[!UICONTROL Inhaltstyp]**

   Sie können Alle Inhalte auswählen oder eine der auf der Site vorhandenen Funktionen auswählen.

* **[!UICONTROL Zeitrahmen]**

   Wählen Sie eine der folgenden Optionen aus:

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **[!UICONTROL Generate]** aus, um den Bericht zu erstellen.

![generate-report](assets/generate-posts-report.png)

## Fehlerbehebung {#troubleshooting}

### Keine Community-Sites aufgeführt {#no-community-sites-listed}

Wenn keine Community-Sites aufgelistet sind, stellen Sie sicher, dass Adobe Analytics für eine Site aktiviert wurde. Stellen Sie bei der Auswahl von Berichten zu Zuweisungen sicher, dass sich die Zuweisungsfunktion in der Struktur der Community-Site befindet.

### Berichte werden nicht in der AEM-Autoreninstanz angezeigt {#reports-do-not-show-in-aem-author-instance}

Wenn Berichte nicht in der AEM-Autoreninstanz angezeigt werden, suchen Sie nach den Anpassungen, z. B. nach der URL-Zuordnung in der Veröffentlichungsinstanz. Wenn die URL-Zuordnung nur auf der AEM-Veröffentlichungsinstanz der Communities-Site erfolgt, stellen Sie sicher, dass dasselbe in der AEM-Autoreninstanz in der Konfiguration **Site Trend Report Social Component Factory** konfiguriert wurde.

![URL-Zuordnung in der AEM-Autoreninstanz](assets/sitetrend.png)
