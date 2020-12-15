---
title: Leader-Funktion
seo-title: Leader-Funktion
description: Hinzufügen einer Leaderboard-Komponente zu einer Seite
seo-description: Hinzufügen einer Leaderboard-Komponente zu einer Seite
uuid: c4633919-75d3-4bc7-830c-ef9c28cc1cba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 9045ce2e-a06d-4da5-9b83-56dd823007bb
docset: aem65
translation-type: tm+mt
source-git-commit: a8b1ad0fcd2ca9c7fe3117dd8bd161da82d13e8a
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 18%

---


# Leaderboard-Funktion {#leaderboard-feature}

## Einführung {#introduction}

Die `Leaderboard`-Komponente bietet die Möglichkeit, sich ein Gefühl dafür zu verschaffen, wie Mitglieder innerhalb der Community interagieren, indem sie Mitglieder nach gewonnenen Punkten (Basissortierung) oder ihrem Fachwissen (fortgeschrittenes Scoring) einstufen.

Bevor Sie die Lederboard-Komponente auf eine Seite setzen, müssen Sie [Communities Scoring and Badges](/help/communities/implementing-scoring.md) konfigurieren.

Dieser Abschnitt der Dokumentation beschreibt:

* Hinzufügen der Komponente `Leaderboard` zu einer [Community-Site](/help/communities/overview.md#community-sites).
* Konfigurationseinstellungen für die Komponente `Leaderboard`.

### Hinzufügen einer Pinnwand zu einer Seite {#adding-a-leaderboard-to-a-page}

Um eine `Leaderboard`-Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente

* `Communities / Leaderboard`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](/help/communities/basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![Lederboard](assets/leaderboard.png)

### Leaderboard {#configuring-leaderboard} konfigurieren

Wählen Sie die platzierte Komponente `Leaderboard` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

![configure-Lederboard](assets/configure-leaderboard.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie unter der Registerkarte **[!UICONTROL Einstellungen]** an, welche Informationen zum Element angezeigt werden sollen:

* **Anzeigename**

   Ein beschreibender Name, der für die Pinnwand angezeigt werden soll und die Regeln zum Anzeigen von Abzeichen und Ergebnissen widerspiegelt.
Der Standardwert ist `Leaderboard`, wenn nichts eingegeben wurde.

* **Abzeichen**

   Wenn diese Option aktiviert ist, wird eine Spalte für Symbole mit Zeichen in die Lederboard aufgenommen.
Diese Option ist standardmäßig deaktiviert.

* **Abzeichenname**

   Wenn diese Option aktiviert ist, wird eine Spalte für den Namen des Kennzeichens in die Lederboard aufgenommen.
Diese Option ist standardmäßig deaktiviert.

* **Avatar verwenden**

   Wenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds neben dem Namen des Mitglieds mit dem Profil des Mitglieds verknüpft.
Diese Option ist standardmäßig deaktiviert.

#### Registerkarte Regeln {#rules-tab}

Auf der Registerkarte **Regeln** finden Sie die Community-Site und die zugehörigen Scoring- und Bading-Regeln

* **Speicherort für Regel**

   (Erforderlich) Speicherort, an dem die Regel für Bewertung/Abzeichen konfiguriert ist.

* **Bewertungsregel**

   (Erforderlich) Spezifische Regel, die die anzuzeigenden Werte generiert.

* **Abzeichenregel**

   (Erforderlich) Spezifische Regel, die das anzuzeigende Zeichen generiert.

* **Anzeigelimit**

   Anzahl der Mitglieder, die pro Seite angezeigt werden sollen. Der Standardwert ist 10.

### Beispiel: Hauptplatine der Teilnehmer {#example-participants-leaderboard}

Dieser Bericht des Lederboards beruht auf der Anwendung grundlegender Bewertungsregeln.

Konfiguration der Leaderboard-Komponente:

* Registerkarte &quot;Einstellungen&quot;:

   * Anzeigename = `Participation Board`
   * `checked`:

      * Abzeichen
      * Abzeichenname
      * Avatar verwenden

* Registerkarte Regeln:

   * Speicherort für Regel = `/content/sites/<site name>/jcr:content`
   * Bewertungsregel = `/libs/settings/community/scoring/rules/forums-scoring`
   * Abzeichenregel = `/libs/settings/community/badging/rules//reference-badging`
   * Anzeigelimit = `10`

![Participant-Lederboard](assets/participants-leaderboard.png)

### Beispiel: Expert Leaderboard {#example-experts-leaderboard}

Dieser Bericht des Lederboards ist das Ergebnis der Anwendung erweiterter Bewertungsregeln.

Konfiguration der Leaderboard-Komponente:

* Registerkarte &quot;Einstellungen&quot;:

   * Anzeigename = `Expertise Board`
   * `checked`:

      * Abzeichen
      * Avatar verwenden

* Registerkarte Regeln:

   * Speicherort für Regel = `/content/sites/<site name>/jcr:content`
   * Bewertungsregel = `/libs/settings/community/scoring/rules/adv-forums-scoring`
   * Abzeichenregel = `/libs/settings/community/badging/rules/adv-forums-badging`
   * Anzeigelimit = `10`

![Expertengremium](assets/experts-leaderboard.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Leaderboard Essentials](/help/communities/leaderboard.md) für Entwickler.

Anweisungen zum Erstellen von Regeln finden Sie auf der Seite [Bewertung und Abzeichen](/help/communities/implementing-scoring.md) für Administratoren.
