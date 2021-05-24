---
title: Suchen
seo-title: Suchen
description: Rasches Auffinden Ihrer Inhalte dank umfassender Suchfunktionen
seo-description: Rasches Auffinden Ihrer Inhalte dank umfassender Suchfunktionen
uuid: 21605b96-b467-4d01-9a64-9d0648d539f1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 4ec15013-f7ab-44d6-8053-ed28b14f95e2
docset: aem65
exl-id: dd65b308-c449-4f64-9f46-0797b922910f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 96%

---

# Suchen{#searching}

Die Autorenumgebung von AEM bietet abhängig vom Ressourcentyp verschiedene Möglichkeiten zur Inhaltssuche.

>[!NOTE]
>
>Außerhalb der Autorenumgebung stehen auch andere Verfahren für die Suche zur Verfügung, wie der [Query Builder](/help/sites-developing/querybuilder-api.md) und [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Grundlagen zur Suche {#search-basics}

Die Suchfunktion ist über die obere Symbolleiste verfügbar:

![](do-not-localize/chlimage_1-17.png)

Die Suchleiste bietet Ihnen folgende Möglichkeiten:

* Suchen Sie nach einem bestimmten Keyword, Pfad oder Tag.
* Filtern nach ressourcenspezifischen Kriterien, wie Änderungsdatumsangaben, Seitenstatus, Dateigröße usw.
* Definieren und Verwenden einer [gespeicherten Suche](#saved-searches), die auf den oben genannten Kriterien basiert.

>[!NOTE]
>
>Sie können die Suche auch aufrufen, indem Sie den Hotkey `/` (Schrägstrich) verwenden, wenn die Suchschiene sichtbar ist.

## Suchen und Filtern {#search-and-filter}

So durchsuchen und filtern Sie Ressourcen:

1. Öffnen Sie die Option **Suchen** (mit der Lupe in der Symbolleiste) und geben Sie den Suchbegriff ein. Es werden Empfehlungen angezeigt, die Sie dann auswählen können:

   ![s-01](assets/s-01.png)

   Standardmäßig sind die Suchergebnisse auf Ihre aktuelle Position begrenzt (d. h. Konsolen- und zugehörigen Ressourcentyp):

   ![screen_shot_2018-03-23at101445](assets/screen_shot_2018-03-23at101445.png)

1. Falls erforderlich, können Sie den Positionsfilter entfernen (wählen Sie dazu **X** neben dem Filter aus, den Sie entfernen möchten), um alle Konsolen/Ressourcentypen zu durchsuchen.
1. Die Ergebnisse werden angezeigt, und zwar gruppiert nach Konsole und Ressourcentyp.

   Sie können entweder eine spezifische Ressource (für eine spätere Aktion) oder eine Drilldown-Suche auswählen, indem Sie den erforderlichen Ressourcentyp auswählen, z. B. **Alle Sites anzeigen**:

   ![screen-shot_2019-03-05at101900](assets/screen-shot_2019-03-05at101900.png)

1. Wenn Sie weitere Details anzeigen möchten, wählen Sie das Symbol für die Seitenleiste (oben links) aus, um den Seitenbereich **Filter und Optionen** zu öffnen.

   ![](do-not-localize/screen_shot_2018-03-23at101542.png)

   Je nach Ressourcentyp zeigt die Suche eine vordefinierte Auswahl von Such-/Filterkriterien an.

   Im Seitenbereich können Sie folgende Elemente auswählen:

   * Gespeicherte Suchvorgänge
   * Verzeichnisse, die durchsucht werden sollen
   * Tags
   * Suchkriterien, z. B. Änderungsdatum, Veröffentlichungsstatus, Live Copy-Status. 

   >[!NOTE]
   >
   >Die Suchkriterien können variieren:
   >
   >
   >
   >    * abhängig vom ausgewählten Ressourcentyp – beispielsweise sind die Kriterien „Assets“ und „Communities“ nach Themen spezialisiert.
   >    * je nach Instanz, da die [Suchformulare](/help/sites-administering/search-forms.md) (entsprechend der Stelle in AEM) angepasst werden können.


   ![screen-shot_2019-03-05at102509](assets/screen-shot_2019-03-05at102509.png)

1. Sie können auch zusätzliche Suchbegriffe hinzufügen:

   ![screen-shot_2019-03-05at102613](assets/screen-shot_2019-03-05at102613.png)

1. Schließen Sie die **Suche** mit dem **X** (oben rechts).

>[!NOTE]
>
>Die Suchkriterien werden bei Auswahl eines Elements in den Suchergebnissen beibehalten.
>
>Bei Auswahl eines Elements auf der Seite mit den Suchergebnissen bleiben die Suchkriterien erhalten, wenn Sie über die Zurück-Schaltfläche des Browsers zur Suchseite zurückkehren.

## Gespeicherte Suchvorgänge {#saved-searches}

Sie können nicht nur nach zahlreichen Facetten suchen, sondern auch eine bestimmte Suchkonfiguration speichern, um diese später abzurufen und zu verwenden:

1. Definieren Sie die Suchkriterien und wählen Sie **Speichern**.

   ![screen-shot_2019-03-05at102613-1](assets/screen-shot_2019-03-05at102613-1.png)

1. Weisen Sie einen Namen zu und wählen Sie zur Bestätigung **Speichern** aus:

   ![screen-shot_2019-03-05at102725](assets/screen-shot_2019-03-05at102725.png)

1. Die gespeicherte Suche ist außerdem in der Auswahl verfügbar, wenn Sie das nächste Mal auf den Suchbereich zugreifen:

   ![screen-shot_2019-03-05at102927](assets/screen-shot_2019-03-05at102927.png)

1. Nach dem Speichern können Sie:

   * **x** (für den Namen der gespeicherten Suche) verwenden, um eine neue Abfrage zu starten. Die gespeicherte Suche selbst wird nicht gelöscht.
   * die Option **Gespeicherte Suche bearbeiten** verwenden, die Suchbedingungen ändern und dann erneut auf **Speichern** klicken.

Gespeicherte Suchen können geändert werden, indem Sie die gespeicherte Suche auswählen und unten im Suchfeld auf **Gespeicherte Suche bearbeiten** klicken.

![screen-shot_2019-03-05at103010](assets/screen-shot_2019-03-05at103010.png)
