---
title: Anzeigen von Seitenanalysedaten
seo-title: Anzeigen von Seitenanalysedaten
description: Verwenden Sie Seitenanalysedaten, um die Wirkung des Seiteninhalts zu messen.
seo-description: Verwenden Sie Seitenanalysedaten, um die Wirkung des Seiteninhalts zu messen.
uuid: 8dda89be-13e3-4a13-9a44-0213ca66ed9c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 42d2195a-1327-45c0-a14c-1cf5ca196cfc
exl-id: 554b10c2-6157-4821-a6a7-f2fb6666cdff
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 93%

---

# Anzeigen von Seitenanalysedaten{#seeing-page-analytics-data}

Verwenden Sie Seitenanalysedaten, um die Wirkung des Seiteninhalts zu messen.

## In der Konsole sichtbare Analysedaten  {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

Seitenanalysedaten werden in der [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) der Konsole „Sites“ angezeigt. Wenn Seiten im Listenformat angezeigt werden, sind die folgenden Spalten standardmäßig verfügbar:

* Seitenansichten
* Individuelle Besucher
* Zeit auf Seite

Jede Spalte zeigt einen Wert für den aktuellen Berichtszeitraum an und gibt außerdem an, ob der Wert sich seit dem vorherigen Berichtszeitraum erhöht oder verringert hat. Die Daten, die Sie sehen, werden alle 12 Stunden aktualisiert.

>[!NOTE]
>
>Zum Ändern des Aktualisierungszeitraums [konfigurieren Sie das Importintervall](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Öffnen Sie die Konsole **Sites**, z. B. [ http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content).
1. Klicken oder tippen Sie ganz rechts oben in der Symbolleiste auf das Symbol, um **Listenansicht** auszuwählen. (Das angezeigte Symbol ist von der [aktuellen Ansicht](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) abhängig.)

1. Klicken oder tippen Sie wieder ganz rechts oben in der Symbolleiste auf das Symbol und wählen Sie dann **Anzeigeeinstellungen** aus. Das Dialogfeld **Spalten konfigurieren** wird geöffnet. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie den Vorgang mit **Aktualisieren**.

   ![aa-04](assets/aa-04.png)

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

   ![aa-15](assets/aa-15.png)

1. Wählen Sie die Metriken aus, die Sie Autoren in der Sites-Konsole bereitstellen möchten, und klicken Sie dann auf **Hinzufügen**.

   Die angezeigten Spalten werden aus Adobe Analytics abgerufen.

   ![aa-16](assets/aa-16.png)

### Öffnen von Inhaltseinblicken mithilfe von Sites {#opening-content-insights-from-sites}

Öffnen Sie [Content Insight](/help/sites-authoring/content-insights.md) in der Sites-Konsole, um die Seiteneffektivität weiter zu untersuchen.

1. Wählen Sie in der Konsole „Sites“ die Seite aus, für die Sie Inhaltseinblicke sehen möchten.
1. Klicken Sie in der Symbolleiste auf das Symbol „Analyse und Empfehlungen“.

   ![](do-not-localize/chlimage_1-16a.png)

## Im Seiteneditor sichtbare Analysedaten (Activity Map)  {#analytics-visible-from-the-page-editor-activity-map}

>[!NOTE]
>
>Dies wird angezeigt, wenn die [Activity Map für Ihre Website konfiguriert](/help/sites-administering/adobeanalytics-connect.md#configuring-for-the-activity-map) wurde.

>[!NOTE]
>
>Daten für die Activity Map werden aus Adobe Analytics übernommen.

Wenn Ihre Website für [Adobe Analytics konfiguriert](/help/sites-administering/adobeanalytics-connect.md) wurde, können Sie den Modus [Activity Map](/help/sites-authoring/author-environment-tools.md#page-modes) verwenden, um relevante Daten anzuzeigen. Beispiel:

![aa-07](assets/aa-07.png)

### Zugriff auf die Activity Map {#accessing-the-activity-map}

Nachdem Sie den Modus [Activity Map ](/help/sites-authoring/author-environment-tools.md#page-modes) ausgewählt haben, müssen Sie Ihre Anmeldedaten für Adobe Analytics eingeben.  

![aa-03](assets/aa-03.png)

Die bewegliche Symbolleiste von **Analytics** wird angezeigt. Hier haben Sie folgende Möglichkeiten:

* Ändern des Formats der Symbolleiste mit den doppelten Pfeilschaltflächen (**>>**)
* Ein- oder Ausblenden der Seitendetails (Augensymbol)
* Einstellungen der Activity Map konfigurieren (Zahnradsymbol)
* Anzuzeigende Analysedaten auswählen (verschiedene Dropdown-Selektoren)
* Activity Map beenden und Symbolleiste schließen (x)

![aa-09](assets/aa-09.png)

### Auswahl der anzuzeigenden Analysedaten {#selecting-the-analytics-to-show}

Mithilfe der folgenden Kriterien können Sie auswählen, welche Analysedaten angezeigt werden sollen und wie sie angezeigt werden sollen:

* **Standard**/**Live**

* Ereignistyp
* Benutzergruppe
* **Blasen**/**Verlauf**/**Gewinner und Verlierer**/**Aus**

* Anzuzeigender Zeitraum

![aa-13](assets/aa-13.png)

### Konfigurieren der Activity Map {#configuring-the-activity-map}

Verwenden Sie das Symbol **Einstellungen anzeigen**, um das Dialogfeld **Einstellungen für Activity Map** zu öffnen.    

![aa-04-1](assets/aa-04-1.png)

Das Dialogfeld **Einstellungen für Activity Map** bietet auf drei Registerkarten eine Reihe von Optionen:  

![aa-06](assets/aa-06.png)

* Allgemein

   * Report Suite
   * Seitenname
   * Sprache
   * Overlays bezeichnen als
   * Schriftgröße Beschriftung
   * Verlaufsfarbe
   * Blasenfarbe
   * Farbverlauf auf Grundlage von
   * Verlaufstransparenz

* Standard

   * Anzeige (Typ und Anzahl der Links)
   * Übergänge für Links ausblenden, die keine Treffer erhalten haben

* Live

   * Anzeige oben (Gewinner und Verlierer)
   * Unterste ausschließen %
   * Automatische Aktualisierung (Datum und Zeitraum)
