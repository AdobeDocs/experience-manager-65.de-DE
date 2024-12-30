---
title: Erweiterte Bewertung und Abzeichen
description: Erfahren Sie, wie Sie eine erweiterte Bewertung einrichten, damit Sie Abzeichen vergeben können, um Mitglieder als Experten zu identifizieren.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: d3bb6664-6c01-4bcf-840c-072fc491fc99
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 2%

---

# Erweiterte Bewertung und Abzeichen{#advanced-scoring-and-badges}

## Überblick {#overview}

Die erweiterte Bewertung ermöglicht die Vergabe von Abzeichen zur Identifizierung von Mitgliedern als Experten. Die erweiterte Bewertung weist Punkte basierend auf der Menge *und* Qualität des von einem Mitglied erstellten Inhalts zu, während die einfache Bewertung Punkte basierend auf der Menge des erstellten Inhalts zuweist.

Dieser Unterschied ist auf die Bewertungsmaschine zurückzuführen, die zur Berechnung der Bewertungen verwendet wird. Die grundlegende Scoring-Engine wendet einfache Mathematik an. Die erweiterte Scoring-Engine ist ein adaptiver Algorithmus, der aktive Mitglieder belohnt, die wertvolle und relevante Inhalte beitragen, die durch die Verarbeitung natürlicher Sprache (Natural Language Processing, NLP) eines Themas abgeleitet werden.

Zusätzlich zur Inhaltsrelevanz berücksichtigen die Scoring-Algorithmen die Mitgliederaktivitäten, wie z. B. die Stimmabgabe und den Prozentsatz der Antworten. Während die einfache Bewertung sie quantitativ umfasst, werden sie bei der erweiterten Bewertung algorithmisch verwendet.

Daher benötigt die erweiterte Scoring-Engine genügend Daten, um die Analyse aussagekräftig zu machen. Die Erfolgsschwelle für das Erlangen des Expertenstatus wird ständig neu bewertet, da sich der Algorithmus kontinuierlich an das Volumen und die Qualität der erstellten Inhalte anpasst. Es gibt auch ein Konzept *Verfall* der älteren Posten eines Mitglieds. Wenn ein Expertenmitglied an dem Thema, zu dem es den Expertenstatus erlangt hat, nicht mehr teilnimmt, kann es an einem vorab festgelegten Punkt (siehe [Konfiguration der Bewertungsmaschine](#configurable-scoring-engine)) seinen Status als Experte verlieren.

Die Einrichtung der erweiterten Bewertung ist praktisch identisch mit der grundlegenden Bewertung:

* Grundlegende und erweiterte Scoring- und Badging[Regeln werden auf dieselbe Weise auf ](/help/communities/implementing-scoring.md#apply-rules-to-content) angewendet.

   * Auf denselben Inhalt können einfache und erweiterte Scoring- und Badging-Regeln angewendet werden.

* [Aktivieren von Abzeichen für Komponenten](/help/communities/implementing-scoring.md#enable-badges-for-component) ist generisch.

Die Unterschiede bei der Einrichtung der Scoring- und Badging-Regeln sind:

* Konfigurierbare erweiterte Scoring-Engine
* Erweiterte Bewertungsregeln:

   * `scoringType` ist auf `advanced` festgelegt
   * Erfordert `stopwords`

* Erweiterte Badging-Regeln:

   * `badgingType` ist auf `advanced` festgelegt
   * `badgingLevels` auf **Anzahl der zu vergebenden Expertenebenen**
   * Erfordert `badgingPaths` Array von Badges anstelle von Schwellenwerten für die Array-Zuordnung von Punkten zu Badges.

>[!NOTE]
>
>Um erweiterte Scoring- und Badging-Funktionen zu verwenden, installieren Sie das Paket [Expertenidentifizierung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq610%2Fsocial%2Ffeaturepack%2Fcq-social-expert-identification-pkg).

## Konfigurierbare Bewertungsmaschine {#configurable-scoring-engine}

Die erweiterte Scoring-Engine stellt eine OSGi-Konfiguration mit Parametern bereit, die sich auf den erweiterten Scoring-Algorithmus auswirken.

![Advanced-Scoring-Engine](assets/advanced-scoring-engine.png)

* **Bewertungsgewichte**

  Geben Sie für ein Thema das Verb an, dem bei der Berechnung der Punktzahl die höchste Priorität zugewiesen werden soll. Es können ein oder mehrere Themen eingegeben werden, die jedoch auf **ein Verb pro Thema** beschränkt sind. Siehe [Themen und Verben](/help/communities/implementing-scoring.md#topics-and-verbs).
Als `topic,verb` mit Escape-Komma eingegeben. Zum Beispiel:
  `/social/forum/hbs/social/forum\,ADD`
Als Standard ist das Verb „HINZUFÜGEN“ für die Komponenten „QA“ und „Forum“ festgelegt.

* **Bewertungsbereich**

  Der Bereich für erweiterte Scores wird durch diesen Wert (Maximalwert) und 0 (niedrigstmöglicher Wert) definiert.

  Der Standardwert ist 100, sodass der Scoring-Bereich 0-100 beträgt.

* **Zeitintervall für Entitätsabfall**

  Dieser Parameter gibt die Anzahl der Stunden an, nach denen alle Entitätsbewertungen veraltet sind. Dies ist erforderlich, um alte Inhalte nicht mehr in die Bewertungen für eine Community-Site einzuschließen.

  Der Standardwert ist 216000 Stunden (~24 Jahre).

* **Scoring-Wachstumsrate**
Dies legt den Wert zwischen dem Bewertungsbereich 0 fest, bei dessen Überschreitung das Wachstum die Anzahl der Experten einschränkt.

  Der Standardwert ist 50.

## Erweiterte Bewertungsregeln {#advanced-scoring-rules}

Bei der einfachen Bewertung ist die Menge bekannt, die zum Erlangen eines Abzeichens benötigt wird.

Bei der erweiterten Bewertung wird die benötigte Menge ständig auf der Grundlage der Menge der Qualitätsdaten im System angepasst. Die Bewertung wird kontinuierlich ähnlich einer Glockenkurve berechnet.

Wenn ein Mitglied ein Expertenabzeichen für ein Thema erworben hat, das nicht mehr aktiv ist, besteht die Möglichkeit, dass es sein Abzeichen aufgrund von Zerfall im Laufe der Zeit verliert.

### scoringType {#scoringtype}

Eine Scoring-Regel ist eine Reihe von Scoring-Unterregeln, von denen jede die `scoringType` deklariert.

Um die erweiterte Scoring-Engine aufzurufen`scoringType` sollte auf `advanced` gesetzt werden.

Siehe [Bewerten von Unterregeln](/help/communities/implementing-scoring.md#scoring-sub-rules).

![Advanced-Scoring-Type](assets/advanced-scoring-type.png)

### Stoppwörter {#stopwords}

Das Paket für die erweiterte Bewertung installiert einen Konfigurationsordner, der eine Stoppwörter-Datei enthält:

* `/libs/settings/community/scoring/configuration/stopwords`

Der erweiterte Scoring-Algorithmus verwendet die Liste der in der Stoppwörter-Datei enthaltenen Wörter, um häufig verwendete englische Wörter zu identifizieren, die bei der Inhaltsverarbeitung ignoriert werden.

Es ist nicht zu erwarten, dass diese Datei geändert wird.

Wenn die Stoppwörter-Datei fehlt, gibt die erweiterte Scoring-Engine einen Fehler aus.

## Erweiterte Badging-Regeln {#advanced-badging-rules}

Die Eigenschaften der erweiterten Badging-Regel unterscheiden sich von [einfachen Eigenschaften der Badging-Regel](/help/communities/implementing-scoring.md#badging-rules).

Anstatt Punkte mit einem Abzeichenbild zu verknüpfen, müssen nur die Anzahl der zugelassenen Experten und das Abzeichenbild identifiziert werden, die vergeben werden sollen.

![Advanced-badging-rules](assets/advanced-badging-rules.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Typ</th>
   <th>Beschreibung des Werts</th>
  </tr>
  <tr>
   <td>badgingPath</td>
   <td>Zeichenfolge[]</td>
   <td><em>(Erforderlich)</em> Eine Zeichenfolge mit mehreren Werten aus Badge-Bildern bis zur Anzahl der badgingLevels. Die Abzeichen-Bildpfade müssen bestellt werden, damit der erste an den höchsten Experten vergeben wird. Wenn es weniger Badges gibt als durch badgingLevels angegeben, füllt das letzte Badge im Array den Rest des Arrays aus. Beispieleintrag:<br /> <code>/libs/settings/community/badging/images/expert-badge/jcr:content/expert.png</code></td>
  </tr>
  <tr>
   <td>BadgingLevels</td>
   <td>Long</td>
   <td><em>(Optional)</em> Gibt den Grad des Fachwissens an, das verliehen werden soll. Wenn beispielsweise ein (<code>expert </code> und ein <code>almost expert</code> (zwei Badges) vorhanden sein sollen, sollte der Wert auf 2 gesetzt werden. Die BadgingLevel sollte mit der Anzahl der fachkundigen Badge-Bilder übereinstimmen, die für die badgingPath-Eigenschaft aufgeführt sind. Der Standardwert ist 1.</td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>Zeichenfolge</td>
   <td><em>(Erforderlich)</em> Gibt die Scoring-Engine als „Standard“ oder „Erweitert“ an. Auf „Erweitert“ gesetzt, andernfalls ist der Standard „Einfach“.</td>
  </tr>
  <tr>
   <td>ScoringRules</td>
   <td>Zeichenfolge[]</td>
   <td><em>(Optional)</em> Eine Zeichenfolge mit mehreren Werten, um die Badging-Regel auf die Bewertung von Ereignissen zu beschränken, die durch eine oder mehrere der aufgeführten Bewertungsregeln identifiziert wurden.<br /> Beispieleintrag: <br /> <code>/libs/settings/community/scoring/rules/adv-comments-scoring</code><br /> Standard ist keine Einschränkung.</td>
  </tr>
 </tbody>
</table>

## Enthaltene Regeln und Abzeichen {#included-rules-and-badge}

### Enthaltene Abzeichen {#included-badge}

In dieser Beta-Version ist ein belohnungsbasiertes Expertenabzeichen enthalten:

* `expert`

  `/libs/settings/community/badging/images/expert-badge/jcr:content/expert.png`

![Expert-Badge](assets/included-badge.png)

Damit das Expertenabzeichen als Belohnung für Aktivitäten angezeigt wird, müssen Sie Folgendes sicherstellen:

* `Badges` sind für die Funktion aktiviert, z. B. eine Forum- oder QnA-Komponente.

* Erweiterte Scoring- und Badging-Regeln werden auf die Seite (oder den Vorgänger) angewendet, auf der sich die Komponente befindet

Siehe die grundlegenden Informationen für:

* [Aktivieren des Badging für eine Komponente](/help/communities/implementing-scoring.md#enableforcomponent)
* [Regeln werden angewendet](/help/communities/implementing-scoring.md#applytopage)

### Eingeschlossene Bewertungsregeln und Unterregeln {#included-scoring-rules-and-sub-rules}

In der Beta-Version sind zwei erweiterte Bewertungsregeln für die Funktion [Forum](/help/communities/functions.md#forum-function) enthalten (je eine für die Komponente Forum und Kommentare der Forenfunktion):

1. `/libs/settings/community/scoring/rules/adv-comments-scoring`

   ```
   subRules[] =
   /libs/settings/community/scoring/rules/sub-rules/adv-comments-rule
   /libs/settings/community/scoring/rules/sub-rules/adv-voting-rule-owner
   /libs/settings/community/scoring/rules/sub-rules/adv-voting-rule
   ```

1. `/libs/settings/community/scoring/rules/adv-forums-scoring`

   ```
   subRules[] =
   /libs/settings/community/scoring/rules/sub-rules/adv-forums-rule
   /libs/settings/community/scoring/rules/sub-rules/adv-comments-rule
   /libs/settings/community/scoring/rules/sub-rules/adv-voting-rule-owner
   ```

**Anmerkungen:**

* Sowohl `rules`- als auch `sub-rules`-Knoten sind vom Typ `cq:Page`.
* `subRules` ist ein Attribut vom Typ Zeichenfolge`[]` auf dem `jcr:content` Knoten der Regel.
* `sub-rules` können unter verschiedenen Bewertungsregeln aufgeteilt werden.
* `rules` sollten sich an einem Repository-Speicherort mit Leseberechtigung für alle befinden.
* Regelnamen müssen unabhängig vom Speicherort eindeutig sein.

### Enthaltene Badging-Regeln {#included-badging-rules}

In der Version sind zwei erweiterte Badging-Regeln enthalten, die den Bewertungsregeln für [erweiterte Foren und Kommentare](#included-scoring-rules-and-sub-rules) entsprechen.

* `/libs/settings/community/badging/rules/adv-comments-badging`
* `/libs/settings/community/badging/rules/adv-forums-badging`

**Anmerkungen:**

* `rules` Knoten sind vom Typ cq:Page.
* `rules` sollten sich an einem Repository-Speicherort mit Leseberechtigung für alle befinden.
* Regelnamen müssen unabhängig vom Speicherort eindeutig sein.
