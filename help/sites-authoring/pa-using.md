---
title: Anzeigen von Seitenanalysedaten zur Messung der Effektivität des Seiteninhalts
description: Verwenden Sie Seitenanalysedaten, um die Effektivität des Seiteninhalts zu messen.
uuid: 8dda89be-13e3-4a13-9a44-0213ca66ed9c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 42d2195a-1327-45c0-a14c-1cf5ca196cfc
exl-id: 554b10c2-6157-4821-a6a7-f2fb6666cdff
source-git-commit: 75c6bb87bb06c5ac9378ccebf193b5416c080bb1
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 99%

---

# Anzeigen von Seitenanalysedaten{#seeing-page-analytics-data}

Verwenden Sie Seitenanalysedaten, um die Effektivität des Seiteninhalts zu messen.

## In der Konsole sichtbare Analysen {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

Seitenanalysedaten werden in der [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) der Sites-Konsole angezeigt. Wenn die Seiten im Listenformat angezeigt werden, sind die folgenden Spalten standardmäßig verfügbar:

* Seitenansichten
* Unique Visitors
* Zeit auf Seite

Jede Spalte zeigt einen Wert für den aktuellen Berichtszeitraum an und zeigt dazu an, ob der Wert seit dem vorherigen Berichtszeitraum gestiegen oder gesunken ist. Die angezeigten Daten werden alle 12 Stunden aktualisiert.

>[!NOTE]
>
>Um den Aktualisierungszeitraum zu ändern, [konfigurieren Sie das Importintervall](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Öffnen Sie die Konsole **Sites**, z. B. [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content).
1. Klicken oder tippen Sie ganz rechts oben in der Symbolleiste auf das Symbol, um **Listenansicht** auszuwählen. (Das angezeigte Symbol ist von der [aktuellen Ansicht](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) abhängig.)

1. Klicken oder tippen Sie oben rechts in der Symbolleiste auf das Symbol und wählen Sie **Anzeigeeinstellungen** aus. Der Dialog **Spalten konfigurieren** wird geöffnet. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie den Vorgang mit **Aktualisieren**.

   ![aa-04](assets/aa-04.png)

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

1. Verwenden Sie in der Listenansicht die Ansichtsselektoren (rechts neben der Symbolleiste), wählen Sie **Ansichts-Einstellungen** und anschließend **Benutzerdefinierte Analysedaten hinzufügen**.

   ![aa-15](assets/aa-15.png)

1. Wählen Sie die Metriken aus, die Sie Autoren in der Sites-Konsole bereitstellen möchten, und klicken Sie dann auf **Hinzufügen**.

   Die angezeigten Spalten werden aus Adobe Analytics abgerufen.

   ![aa-16](assets/aa-16.png)

### Öffnen von Inhaltseinblicken mithilfe von Sites {#opening-content-insights-from-sites}

Öffnen Sie [Inhaltseinsicht](/help/sites-authoring/content-insights.md) von der Konsole „Sites“ aus, um die Seiteneffektivität weiter zu untersuchen.

1. Wählen Sie in der Sites-Konsole die Seite aus, für die Sie Inhaltseinblicke anzeigen möchten.
1. Klicken Sie in der Symbolleiste auf das Symbol „Analysen und Empfehlungen“.

   ![Symbol &quot;Analytics and Recommendations&quot;](do-not-localize/chlimage_1-16a.png)

## Im Seiten-Editor sichtbare Analysen (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!NOTE]
>
>Dies wird angezeigt, wenn die [Activity Map für Ihre Website konfiguriert](/help/sites-administering/adobeanalytics-connect.md#configuring-for-the-activity-map) wurde.

>[!NOTE]
>
>Daten für die Activity Map werden aus Adobe Analytics übernommen.

Wenn Ihre Website für [Adobe Analytics konfiguriert](/help/sites-administering/adobeanalytics-connect.md) wurde, können Sie den Modus [Activity Map](/help/sites-authoring/author-environment-tools.md#page-modes) verwenden, um relevante Daten anzuzeigen. Beispiel:

![aa-07](assets/aa-07.png)

### Zugriff auf die Activity Map {#accessing-the-activity-map}

Nachdem Sie den Modus [Activity Map](/help/sites-authoring/author-environment-tools.md#page-modes) ausgewählt haben, müssen Sie Ihre Anmeldedaten für Adobe Analytics eingeben.  

![aa-03](assets/aa-03.png)

Die schwebende Symbolleiste **Analyse** wird angezeigt. Hier können Sie:

* das Symbolleistenformat mit den doppelten Pfeilen (**>>**) ändern
* Ein- oder Ausblenden der Seitendetails (Augensymbol)
* Einstellungen der Activity Map konfigurieren (Zahnradsymbol)
* Anzuzeigende Analysedaten auswählen (verschiedene Dropdown-Selektoren)
* Activity Map beenden und Symbolleiste schließen (x)

![aa-09](assets/aa-09.png)

### Auswahl der anzuzeigenden Analysen {#selecting-the-analytics-to-show}

Sie können anhand der verschiedenen Kriterien auswählen, welche Analysedaten angezeigt werden sollen und wie sie angezeigt werden sollen:

* **Standard**/**Live**

* Ereignistyp
* Benutzergruppe
* **Blasen**/**Verlauf**/**Gewinner und Verlierer**/**Aus**

* Anzuzeigender Zeitraum

![aa-13](assets/aa-13.png)

### Konfigurieren der Activity Map {#configuring-the-activity-map}

Verwenden Sie das Symbol **Einstellungen anzeigen** zum Öffnen des Dialogs **Activity Map-Einstellungen**.

![aa-04-1](assets/aa-04-1.png)

Das Dialogfeld **Einstellungen für Activity Map** bietet auf drei Registerkarten eine Reihe von Optionen:  

![aa-06](assets/aa-06.png)

* Allgemein

   * Report Suite
   * Seitenname
   * Sprache
   * Kennzeichnen von Überlagerungen mit
   * Schriftgröße der Kennzeichnung
   * Verlaufsfarbe
   * Blasenfarbe
   * Farbverlauf basierend auf
   * Verlaufstransparenz

* Standard

   * Anzeige (Typ und Anzahl der Links)
   * Überlagerungen für Links ausblenden, die keine Treffer erhalten haben

* Live

   * Stärkste Gewinner oder Verlierer anzeigen
   * Unterste % ausschließen
   * Automatische Aktualisierung (Daten und Zeitraum)
