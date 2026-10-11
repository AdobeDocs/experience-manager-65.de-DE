---
title: Exportieren in CSV
description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: 18910143-f2f2-4cfe-88b9-651df90d9cb9
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 100%
---
# Exportieren in CSV{#export-to-csv}

Mit **CSV-Bericht erstellen** können Sie Informationen über Ihre Seiten in eine CSV-Datei auf Ihrem lokalen System exportieren.

* Die heruntergeladene Datei erhält den Namen `export.csv`.
* Der Inhalt der Datei hängt davon ab, welche Eigenschaften Sie für den Export auswählen.
* Sie können den Pfad zusammen mit der Tiefe des Exports definieren.

>[!NOTE]
>
>Die Download-Funktion (und der Standard-Zielordner) Ihres Browsers werden verwendet.

Mit dem Assistenten zum **Erstellen eines CSV-Exports** können Sie Folgendes auswählen:

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

Die Option **CSV-Bericht erstellen** ist in der **Sites-Konsole** (in der Listenansicht) verfügbar. Sie finden die Option im Dropdown-Menü **Erstellen**:

![etc-02](assets/etc-02.png)

So erstellen Sie einen CSV-Export:

1. Öffnen Sie die **Sites-Konsole** und navigieren Sie ggf. zum gewünschten Speicherort.
1. Wählen Sie in der Symbolleiste **Erstellen** und dann **CSV-Bericht** aus, um den Assistenten zu öffnen:

   ![etc-03](assets/etc-03.png)

1. Wählen Sie die Eigenschaften aus, die exportiert werden sollen.
1. Wählen Sie **Erstellen**.
