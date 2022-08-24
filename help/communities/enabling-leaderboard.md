---
title: Leaderboard-Funktion
seo-title: Leaderboard Feature
description: Hinzufügen einer Leaderboard-Komponente zu einer Seite
seo-description: Adding a Leaderboard component to a page
uuid: c4633919-75d3-4bc7-830c-ef9c28cc1cba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 9045ce2e-a06d-4da5-9b83-56dd823007bb
docset: aem65
exl-id: 8b4d56d9-ba73-4eda-9773-3daaa9237abe
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 18%

---

# Leaderboard-Funktion {#leaderboard-feature}

## Einführung    {#introduction}

Die `Leaderboard` -Komponente bietet die Möglichkeit, ein Gefühl dafür zu erhalten, wie Mitglieder innerhalb der Community interagieren, indem sie Mitglieder nach erworbenen Punkten (Basis-Scoring) oder ihrem Fachwissen (fortgeschrittenes Scoring) einstuft.

Bevor Sie die Leaderboard-Komponente auf einer Seite einfügen, müssen Sie [Communities-Scoring und -Abzeichen](/help/communities/implementing-scoring.md).

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der `Leaderboard` -Komponente [Community-Site](/help/communities/overview.md#community-sites).
* Konfigurationseinstellungen für `Leaderboard` -Komponente.

### Hinzufügen eines Leaderboards zu einer Seite {#adding-a-leaderboard-to-a-page}

So fügen Sie eine `Leaderboard` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente

* `Communities / Leaderboard`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![Lederboard](assets/leaderboard.png)

### Leaderboard konfigurieren {#configuring-leaderboard}

Wählen Sie die platzierte `Leaderboard` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![configure-new](assets/configure-new.png)

![configure-lederboard](assets/configure-leaderboard.png)

#### Registerkarte „Settings“ {#settings-tab}

Unter dem **[!UICONTROL Einstellungen]** angeben, welche Informationen zum Mitglied angezeigt werden sollen:

* **Anzeigename**

   Ein beschreibender Name, der für die Pinnwand angezeigt wird und die für die Anzeige von Abzeichen und Bewertungen ausgewählten Regeln widerspiegelt.
Der Standardwert ist `Leaderboard`, wenn nichts eingegeben wurde.

* **Abzeichen**

   Wenn diese Option aktiviert ist, wird eine Spalte für Badge-Symbole in die Leaderboard eingefügt.
Diese Option ist standardmäßig deaktiviert.

* **Abzeichenname**

   Wenn diese Option aktiviert ist, wird eine Spalte für den Badge-Namen in die Leaderboard aufgenommen.
Diese Option ist standardmäßig deaktiviert.

* **Avatar verwenden**

   Wenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds in das Leaderboard eingefügt, neben dem Namen, der mit seinem Mitgliederprofil verknüpft ist.
Diese Option ist standardmäßig deaktiviert.

#### Registerkarte Regeln {#rules-tab}

Unter dem **Regeln** Registerkarte, der Community-Site und den zugehörigen Scoring- und Badging-Regeln

* **Speicherort für Regel**

   (Erforderlich) Der Speicherort, an dem die Regel Scoring/Badging konfiguriert ist.

* **Bewertungsregel**

   (Erforderlich) Bestimmte Regel, die die anzuzeigenden Werte generiert.

* **Abzeichenregel**

   (Erforderlich) Bestimmte Regel, die das anzuzeigende Badge generiert.

* **Anzeigelimit**

   Anzahl der Mitglieder, die pro Seite angezeigt werden sollen. Der Standardwert ist 10.

### Beispiel: Teilnehmer-Leaderboard {#example-participants-leaderboard}

Diese Leaderboard-Berichte resultieren aus der Anwendung grundlegender Scoring-Regeln.

Leaderboard-Komponentenkonfiguration:

* Registerkarte Einstellungen :

   * Anzeigename = `Participation Board`
   * `checked`:

      * Abzeichen
      * Abzeichenname
      * Avatar verwenden

* Registerkarte Regeln :

   * Speicherort für Regel = `/content/sites/<site name>/jcr:content`
   * Bewertungsregel = `/libs/settings/community/scoring/rules/forums-scoring`
   * Abzeichenregel = `/libs/settings/community/badging/rules//reference-badging`
   * Anzeigelimit = `10`

![Participant Lederboard](assets/participants-leaderboard.png)

### Beispiel: Expertenvorstand {#example-experts-leaderboard}

Diese Leaderboard-Berichte resultieren aus der Anwendung erweiterter Scoring-Regeln.

Leaderboard-Komponentenkonfiguration:

* Registerkarte Einstellungen :

   * Anzeigename = `Expertise Board`
   * `checked`:

      * Abzeichen
      * Avatar verwenden

* Registerkarte Regeln :

   * Speicherort für Regel = `/content/sites/<site name>/jcr:content`
   * Bewertungsregel = `/libs/settings/community/scoring/rules/adv-forums-scoring`
   * Abzeichenregel = `/libs/settings/community/badging/rules/adv-forums-badging`
   * Anzeigelimit = `10`

![Expertenvorstand](assets/experts-leaderboard.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Leaderboard-Grundlagen](/help/communities/leaderboard.md) für Entwickler.

Anweisungen zum Erstellen von Regeln finden Sie im Abschnitt [Communities-Scoring und -Abzeichen](/help/communities/implementing-scoring.md) für Administratoren.
