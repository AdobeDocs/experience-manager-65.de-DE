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
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Berichte-Konsole{#reports-console}

## Überblick {#overview}

Für AEM Communities gibt es verschiedene Berichte, auf die auf verschiedene Weise aus der Autorenumgebung zugegriffen werden kann.

Im Allgemeinen sind die verschiedenen Berichte:

* [Bericht](#assignments-report) &quot;Zuweisungen&quot;- für eine [Community](/help/communities/overview.md#enablement-community), die die Lernenden bei ihren Zuweisungen unterstützt, bietet einen Überblick über den Fortschritt, einschließlich eines zugehörigen Ergebnisses bei der Implementierung des SCORM-Standards
* [Bericht](#views-report) &quot;Ansichten&quot;: Bietet ein Diagramm der Ansichten der Inhalte von Community-Mitgliedern und Site-Besuchern für jede Community-Site
* [Bericht](#posts-report) zu Beiträgen - enthält ein Diagramm der verschiedenen Arten von Beiträgen von Mitgliedern der Community zu jeder Community-Site

Wenn [Adobe Analytics aktiviert](/help/communities/sites-console.md#analytics)ist, enthalten die Berichte die Anzahl der Ansichten, Wiedergaben, Kommentare und Bewertungen für jede Aktivierungsressource im Laufe der Zeit

Tabuläre Berichte können zur anschließenden Verarbeitung im .csv-Format exportiert werden.

## Berichtkonsolen {#reporting-consoles}

### Berichte für Community-Sites {#reports-for-community-sites}

* aus der globalen Navigation: **Navigation**, **Communities, Berichte**

* auswählen aus

   * **Zuweisungsbericht**

      * einen Bericht für die ausgewählte Community-Site, den ausgewählten Benutzer oder die ausgewählte Gruppe und die Zuweisung erstellen

      * **Post-Bericht**

         * einen Bericht für die ausgewählte Community-Site, den Inhaltstyp und den Zeitraum erstellen
      * **Ansichtsbericht**

         * einen Bericht für die ausgewählte Community-Site, den Inhaltstyp und den Zeitraum erstellen


![chlimage_1-236](assets/chlimage_1-236.png)

### Berichte zu Aktivierungsressourcen und Lernpfaden {#reports-for-enablement-resources-and-learning-paths}

* aus der globalen Navigation: **Navigation**, **Communities, Ressourcen**

* eine vorhandene Community-Site für die Aktivierung auswählen

   * Klicken Sie auf das Symbol **Bericht*, um Berichte zu erstellen, die alle Aktivierungsressourcen abdecken.
   * Auswählen eines Lernpfads für die Aktivierung
   * Wählen Sie das Symbol **Bericht **aus, um Berichte zu erstellen für

      * die enthaltenen Aktivierungsressourcen
      * den Lernenden, die dem Lernpfad zugewiesen sind

* Diese Berichte bieten:

   * Tabellendaten als CSV herunterladen

      * identifizieren von Lernenden
      * ihren Status
      * ob zugewiesen oder über Katalog aufgerufen
      * Anzahl der Stellungnahmen
      * Sternbewertung

Weitere Informationen finden Sie im Abschnitt [Berichte](/help/communities/resources.md#report) der Ressourcenkonsole.

## Zuweisungsbericht {#assignments-report}

Die Konsole &quot;Zuweisungen&quot;ermöglicht das Filtern von Berichten nach der Aktivierung der Community-Site, Benutzern oder Gruppen und der Zuweisung.

Der Bericht enthält Informationen über ihre Fortschritte sowie Kommentare und Bewertungen.

![chlimage_1-237](assets/chlimage_1-237.png)

Wählen Sie die Kriterien für den Bericht aus:

* **Website**

   eine Community-Site für die Aktivierung auswählen

* **Benutzer oder Gruppe**
   * Benutzer auswählen, um einen Bericht für einen Lernenden zu erstellen
   * Gruppe auswählen, um einen Bericht für eine Gruppe Lernender zu erstellen
   Der Tunneldienst greift in der Veröffentlichungsumgebung auf Mitglieder und Mitgliedergruppen zu

* **Zuweisung**

   Wählen Sie aus den den den ausgewählten Lernenden zugewiesenen Ressourcen

Wählen Sie **Erstellen** , um den Bericht zu erstellen:

![chlimage_1-238](assets/chlimage_1-238.png)

## Ansichtsbericht {#views-report}

Die Konsole &quot;Ansichten&quot;ermöglicht die Erstellung von Berichten bei Seitenansichten durch Community-Funktionen für einen bestimmten Zeitraum.

![chlimage_1-239](assets/chlimage_1-239.png)

Wählen Sie die Kriterien für den Bericht aus:

* **Website**

   Community-Site auswählen

* **Inhaltstyp**

   kann &quot;Alle Inhalte&quot;auswählen oder eine der Funktionen auf der Site auswählen

* Zeitrahmen

   Wählen Sie eines von

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **Erstellen** , um den Bericht zu erstellen:

![chlimage_1-240](assets/chlimage_1-240.png)

## Post-Bericht {#posts-report}

In der Konsole &quot;Beiträge&quot;können Berichte für die Anzahl der Beiträge zu Community-Funktionen für einen bestimmten Zeitraum generiert werden.

![chlimage_1-241](assets/chlimage_1-241.png)

Wählen Sie die Kriterien für den Bericht aus:

* **Website**

   Community-Site auswählen

* **Inhaltstyp**

   kann &quot;Alle Inhalte&quot;auswählen oder eine der Funktionen auf der Site auswählen

* Zeitrahmen

   Wählen Sie eines von

   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **Erstellen** , um den Bericht zu erstellen:

![chlimage_1-242](assets/chlimage_1-242.png)

## Fehlerbehebung {#troubleshooting}

### Keine Community-Sites aufgelistet {#no-community-sites-listed}

Wenn keine Community-Sites aufgelistet sind, stellen Sie sicher, dass Adobe Analytics für eine Site aktiviert wurde. Wenn Sie Berichte zu Zuweisungen auswählen, stellen Sie sicher, dass sich die Zuweisungsfunktion in der Struktur der Community-Site befindet.

### Berichte werden nicht in der AEM Author-Instanz angezeigt {#reports-do-not-show-in-aem-author-instance}

Wenn Berichte nicht in der AEM Author-Instanz angezeigt werden, prüfen Sie, ob Anpassungen vorgenommen wurden, z. B. die URL-Zuordnung in der Veröffentlichungsinstanz. Wenn die URL-Zuordnung nur auf der AEM Publish-Instanz der Communities-Site erfolgt, stellen Sie sicher, dass dasselbe in der AEM Authoring-Instanz in der Konfiguration **Site-Trendbericht Social-KomponentenFactory **konfiguriert wurde.

![URL-Zuordnung in AEM Authoring](assets/sitetrend.png)