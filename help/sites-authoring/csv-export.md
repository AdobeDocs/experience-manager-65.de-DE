---
title: Exportieren in CSV
seo-title: Exportieren in CSV
description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
seo-description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
uuid: 6eee607b-3510-4f6a-ba82-b27480a4fbe1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 7be506fb-f5c4-48dd-bec2-a3ea3ea19397
docset: aem65
translation-type: tm+mt
source-git-commit: 2d7492cdee9f7f730dfa6ad2ffae396b3a737b15

---


# Exportieren in CSV{#export-to-csv}

Mit **CSV-Export erstellen** können Sie Informationen über Ihre Seiten in eine CSV-Datei auf Ihrem lokalen System exportieren.

* Die heruntergeladene Datei erhält den Namen `export.csv`
* Der Inhalt der Datei hängt davon ab, welche Eigenschaften Sie für den Export auswählen.
* Sie können den Pfad zusammen mit der Tiefe des Exports definieren.

>[!NOTE]
>
>Die Download-Funktion (und der Standard-Zielordner) Ihres Browsers werden verwendet.

**** Der Assistent zum Erstellen von CSV-Exporten bietet Ihnen folgende Auswahlmöglichkeiten:

* Zu exportierende Eigenschaften
   * Metadaten
      * Name
      * Geändert
      * Veröffentlicht
      * Vorlage
      * Workflow
   * Übersetzung
      * Übersetzt
   * Analytik
      * Seitenansichten
      * Individuelle Besucher
      * Zeit auf Seite
* Depth
   * Übergeordneter Pfad
   * Nur direkte untergeordnete Elemente
   * Zusätzliche Ebenen von untergeordneten Elementen
   * Levels

Die resultierende Datei `export.csv` kann in Excel (oder einer anderen kompatiblen Anwendung) geöffnet werden.

![]() ![etc-01](assets/etc-01.png)

The create **CSV Report** option is available when browsing the **Sites** console (in List view): it is an option of the **Create** drop down menu:

![etc-02](assets/etc-02.png)

So erstellen Sie einen CSV-Export: 

1. Öffnen Sie die **Sites-Konsole** und gehen Sie zum gewünschten Verzeichnis, falls erforderlich.
1. From the toolbar, select **Create** then **CSV Report** to open the wizard:

   ![etc-03](assets/etc-03.png)

1. Wählen Sie die gewünschten Eigenschaften aus, die Sie exportieren möchten.
1. Klicken Sie auf **Erstellen**.
