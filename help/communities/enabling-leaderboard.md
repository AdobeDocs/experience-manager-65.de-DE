---
title: Leaderboard-Funktion
description: Erfahren Sie, wie Sie mit der Leaderboard-Komponente sehen können, wie Mitglieder innerhalb der Community interagieren, indem Sie Mitglieder anhand von Punkten, die Sie gesammelt haben, und Fachwissen einordnen.
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

Die `Leaderboard` -Komponente hilft Ihnen dabei, einen Eindruck davon zu erhalten, wie Mitglieder innerhalb der Community interagieren, indem sie Mitglieder nach Punkten (Grundbewertung) oder ihrer Expertise (fortgeschrittenes Scoring) einstufen.

Bevor Sie die Leaderboard-Komponente auf einer Seite einfügen, müssen Sie [Communities-Scoring und -Abzeichen](/help/communities/implementing-scoring.md).

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der `Leaderboard` -Komponente [Community-Site](/help/communities/overview.md#community-sites).
* Konfigurationseinstellungen für `Leaderboard` -Komponente.

### Hinzufügen eines Leaderboards zu einer Seite {#adding-a-leaderboard-to-a-page}

So fügen Sie eine `Leaderboard` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente

* `Communities / Leaderboard`

Und ziehen Sie es an die gewünschte Stelle auf einer Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Komponente zum ersten Mal auf einer Seite einer Community-Site platziert wird, wird sie wie folgt angezeigt:

![Lederboard](assets/leaderboard.png)

### Leaderboard konfigurieren {#configuring-leaderboard}

Auswählen der platzierten `Leaderboard` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![configure-new](assets/configure-new.png)

![configure-lederboard](assets/configure-leaderboard.png)

#### Registerkarte &quot;Einstellungen&quot; {#settings-tab}

Unter dem **[!UICONTROL Einstellungen]** angeben, welche Informationen zum Mitglied angezeigt werden sollen:

* **Anzeigename**

  Ein beschreibender Name, der für die Pinnwand angezeigt wird und die für die Anzeige von Abzeichen und Bewertungen ausgewählten Regeln widerspiegelt.
Der Standardwert ist `Leaderboard` wenn nichts eingegeben wird.

* **Badge**

  Wenn diese Option aktiviert ist, wird eine Spalte für Badge-Symbole in die Leaderboard eingefügt.
Die Option Standard ist deaktiviert.

* **Badge Name**

  Wenn diese Option aktiviert ist, wird eine Spalte für den Badge-Namen in die Leaderboard aufgenommen.
Die Option Standard ist deaktiviert.

* **Avatar verwenden**

  Wenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds in das Leaderboard eingefügt, neben dem Namen, der mit seinem Mitgliederprofil verknüpft ist.
Die Option Standard ist deaktiviert.

#### Registerkarte &quot;Regeln&quot; {#rules-tab}

Unter dem **Regeln** Registerkarte, der Community-Site und den zugehörigen Scoring- und Badging-Regeln

* **Regelstandort**

  (Erforderlich) Der Speicherort, an dem die Regel Scoring/Badging konfiguriert ist.

* **Bewertungsregel**

  (Erforderlich) Bestimmte Regel, die die anzuzeigenden Werte generiert.

* **Badging-Regel**

  (Erforderlich) Bestimmte Regel, die das anzuzeigende Badge generiert.

* **Anzeigebeschränkung**

  Anzahl der Mitglieder, die pro Seite angezeigt werden sollen Der Standardwert ist 10.

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

   * Regelspeicherort = `/content/sites/<site name>/jcr:content`
   * Scoring Rule = `/libs/settings/community/scoring/rules/forums-scoring`
   * Badging-Regel = `/libs/settings/community/badging/rules//reference-badging`
   * Anzeigelimit = `10`

![Participant Lederboard](assets/participants-leaderboard.png)

### Beispiel: Leaderboard für Experten {#example-experts-leaderboard}

Diese Leaderboard-Berichte resultieren aus der Anwendung erweiterter Scoring-Regeln.

Leaderboard-Komponentenkonfiguration:

* Registerkarte Einstellungen :

   * Anzeigename = `Expertise Board`
   * `checked`:

      * Abzeichen
      * Avatar verwenden

* Registerkarte Regeln :

   * Regelspeicherort = `/content/sites/<site name>/jcr:content`
   * Scoring Rule = `/libs/settings/community/scoring/rules/adv-forums-scoring`
   * Badging-Regel = `/libs/settings/community/badging/rules/adv-forums-badging`
   * Anzeigelimit = `10`

![Expertenvorstand](assets/experts-leaderboard.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Leaderboard-Grundlagen](/help/communities/leaderboard.md) -Seite für Entwickler.

Anweisungen zum Erstellen von Regeln finden Sie im Abschnitt [Communities-Scoring und -Abzeichen](/help/communities/implementing-scoring.md) -Seite für Administratoren.
