---
title: Exportieren in CSV
description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: 18910143-f2f2-4cfe-88b9-651df90d9cb9
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 77%

---

# Exportieren in CSV{#export-to-csv}

Mit **CSV-Bericht erstellen** können Sie Informationen über Ihre Seiten in eine CSV-Datei auf Ihrem lokalen System exportieren.

* Die heruntergeladene Datei erhält den Namen `export.csv`.
* Der Inhalt der Datei hängt davon ab, welche Eigenschaften Sie für den Export auswählen.
* Sie können den Pfad zusammen mit der Tiefe des Exports definieren.

>[!NOTE]
>
>Die Download-Funktion (und der Standard-Zielordner) Ihres Browsers werden verwendet.

Die **CSV-Export erstellen** -Assistent ermöglicht die Auswahl von:

* Zu exportierende Eigenschaften
   * Metadaten
      * Name
      * Geändert
      * Veröffentlicht
      * Vorlage
      * Workflow
   * Übersetzung
      * Übersetzt
   * Analyse
      * Seitenansichten
      * Unique Visitors
      * Zeit auf Seite
* Tiefe
   * Übergeordneter Pfad
   * Nur direkte untergeordnete Elemente
   * Zusätzliche Ebenen von untergeordneten Elementen
   * Ebenen

Die resultierende Datei `export.csv` kann in Excel (oder einer anderen kompatiblen Anwendung) geöffnet werden.

![etc-01](assets/etc-01.png)

Die Erstellung **CSV-Bericht** ist beim Durchsuchen der **Sites** console (in der Listenansicht): ist eine Option der **Erstellen** Dropdown-Menü:

![etc-02](assets/etc-02.png)

So erstellen Sie einen CSV-Export:

1. Öffnen Sie die **Sites** Navigieren Sie bei Bedarf zum gewünschten Speicherort.
1. Wählen Sie in der Symbolleiste **Erstellen** und dann **CSV-Bericht** aus, um den Assistenten zu öffnen:

   ![etc-03](assets/etc-03.png)

1. Wählen Sie die zu exportierenden Eigenschaften aus.
1. Wählen Sie **Erstellen**.
