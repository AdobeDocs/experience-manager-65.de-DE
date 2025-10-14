---
title: Leaderboard-Funktion
description: Erfahren Sie, wie Sie mit der Leaderboard-Komponente sehen können, wie Mitglieder innerhalb der Community interagieren, indem Sie ihre Mitglieder nach ihren Punkten und ihrem Fachwissen ordnen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 8b4d56d9-ba73-4eda-9773-3daaa9237abe
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 2%

---

# Leaderboard-Funktion {#leaderboard-feature}

## Einführung {#introduction}

Die `Leaderboard` Komponente hilft Ihnen, ein Gefühl dafür zu bekommen, wie Mitglieder innerhalb der Community interagieren, indem sie die Mitglieder nach den verdienten Punkten (einfache Punktzahl) oder ihrem Fachwissen (erweiterte Punktzahl) ordnen.

Bevor Sie die Leaderboard-Komponente auf einer Seite einfügen, müssen Sie „Community[Punktzahl und Abzeichen“ &#x200B;](/help/communities/implementing-scoring.md).

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der `Leaderboard` zu einer [Community-Site](/help/communities/overview.md#community-sites).
* Konfigurationseinstellungen für die `Leaderboard`.

### Hinzufügen eines Leaderboards zu einer Seite {#adding-a-leaderboard-to-a-page}

Suchen Sie die Komponente, um einer Seite im Autorenmodus eine `Leaderboard` Komponente hinzuzufügen

* `Communities / Leaderboard`

Und ziehen Sie es auf eine Seite.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Komponente zum ersten Mal auf einer Seite einer Community-Site platziert wird, wird sie wie folgt angezeigt:

![Leaderboard](assets/leaderboard.png)

### Leaderboard konfigurieren {#configuring-leaderboard}

Wählen Sie die platzierte `Leaderboard` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![configure-new](assets/configure-new.png)

![configure-leaderboard](assets/configure-leaderboard.png)

#### Registerkarte „Einstellungen“ {#settings-tab}

Geben **[!UICONTROL auf der Registerkarte]** Einstellungen“ an, welche Informationen zum Mitglied angezeigt werden sollen:

* **Anzeigename**

  Ein beschreibender Name, der für die Pinnwand angezeigt wird und die ausgewählten Regeln für die Anzeige von Abzeichen und Bewertungen widerspiegelt.
Der Standardwert wird `Leaderboard`, wenn nichts eingegeben wird.

* **Badge**

  Wenn diese Option aktiviert ist, wird eine Spalte für Badge-Symbole in der Leaderboard eingefügt.
Standard ist deaktiviert.

* **Badge Name**

  Wenn diese Option aktiviert ist, wird eine Spalte für den Badge-Namen in der Rangliste angezeigt.
Standard ist deaktiviert.

* **Verwenden von Avatar**

  Wenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds in der Rangliste neben seinem Namen und dem Link zu seinem Mitgliederprofil angezeigt.
Standard ist deaktiviert.

#### Registerkarte „Regeln“ {#rules-tab}

Auf der Registerkarte **Regeln** die Community-Site und ihre Scoring- und Badging-Regeln

* **Speicherort der Regel**

  (Erforderlich) Speicherort, an dem die Scoring-/Badging-Regel konfiguriert ist.

* **Bewertungsregel**

  (Erforderlich) Spezifische Regel, die die anzuzeigenden Bewertungen generiert.

* **Badging-Regel**

  (Erforderlich) Spezifische Regel, die das anzuzeigende Badge generiert.

* **Anzeigegrenze**

  Anzahl der pro Seite anzuzeigenden Mitglieder. Der Standardwert ist 10.

### Beispiel: Teilnehmer-Leaderboard {#example-participants-leaderboard}

Dieses Leaderboard berichtet über die Anwendung der grundlegenden Bewertungsregeln.

Konfiguration der Leaderboard-Komponente:

* Registerkarte Einstellungen:

   * Anzeigename = `Participation Board`
   * `checked`:

      * Abzeichen
      * Abzeichenname
      * Avatar verwenden

* Registerkarte Regeln :

   * Speicherort der Regel = `/content/sites/<site name>/jcr:content`
   * Scoring-Regel = `/libs/settings/community/scoring/rules/forums-scoring`
   * Badging-Regel = `/libs/settings/community/badging/rules//reference-badging`
   * Anzeigegrenze = `10`

![Participants-Leaderboard](assets/participants-leaderboard.png)

### Beispiel: Experten-Leaderboard {#example-experts-leaderboard}

Dieses Leaderboard berichtet über die Anwendung erweiterter Bewertungsregeln.

Konfiguration der Leaderboard-Komponente:

* Registerkarte Einstellungen:

   * Anzeigename = `Expertise Board`
   * `checked`:

      * Abzeichen
      * Avatar verwenden

* Registerkarte Regeln :

   * Speicherort der Regel = `/content/sites/<site name>/jcr:content`
   * Scoring-Regel = `/libs/settings/community/scoring/rules/adv-forums-scoring`
   * Badging-Regel = `/libs/settings/community/badging/rules/adv-forums-badging`
   * Anzeigegrenze = `10`

![Experts-Leaderboard](assets/experts-leaderboard.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Leaderboard Essentials](/help/communities/leaderboard.md) für Entwickler.

Anweisungen zum Erstellen von Regeln finden Sie auf der Seite [Vergabe von Bewertungen und Abzeichen in Communities](/help/communities/implementing-scoring.md) für Administratoren.
