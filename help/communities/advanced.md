---
title: Erweiterte Scoring- und Badges
description: Erfahren Sie, wie Sie erweiterte Bewertungen einrichten, damit Sie Abzeichen verteilen können, um Mitglieder als Experten zu identifizieren.
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

# Erweiterte Scoring- und Badges{#advanced-scoring-and-badges}

## Übersicht {#overview}

Die erweiterte Bewertung ermöglicht die Vergabe von Abzeichen, um Mitglieder als Experten zu identifizieren. Bei der erweiterten Auswertung werden Punkte basierend auf der Menge zugewiesen. *und* Qualität des Inhalts, der von einem Mitglied erstellt wurde, während die grundlegende Auswertung Punkte basierend auf der Menge des erstellten Inhalts zuweist.

Dieser Unterschied beruht auf der Scoring-Engine, die zur Berechnung der Werte verwendet wird. Die grundlegende Scoring-Engine wendet einfache Mathematik an. Die erweiterte Scoring-Engine ist ein adaptiver Algorithmus, der aktive Mitglieder belohnt, die wertvolle und relevante Inhalte beisteuern, die durch die natürliche Sprachverarbeitung (NLP) eines Themas abgeleitet werden.

Zusätzlich zur Inhaltsrelevanz berücksichtigen die Scoring-Algorithmen Mitgliederaktivitäten, wie z. B. Stimmabgabe und Prozentsatz der Antworten. Während die grundlegende Bewertung sie quantitativ beinhaltet, verwendet die erweiterte Auswertung sie algorithmisch.

Daher benötigt die erweiterte Scoring-Engine genügend Daten, um die Analyse sinnvoll zu gestalten. Die Erfolgsschwelle für die Expertenaktivität wird ständig neu bewertet, da sich der Algorithmus kontinuierlich an die Menge und Qualität der erstellten Inhalte anpasst. Es gibt auch ein Konzept von *Abfall* der älteren Beiträge eines Mitglieds. Wenn ein Expertenmitglied nicht mehr an dem Gegenstand teilnimmt, in dem es einen Sachverständigenstatus erlangt hat, zu einem bestimmten Zeitpunkt (siehe [Konfiguration der Scoring-Engine](#configurable-scoring-engine)) könnten sie ihren Status als Experte verlieren.

Die Einrichtung der erweiterten Auswertung ist praktisch identisch mit der grundlegenden Auswertung:

* Grundlegende und erweiterte Scoring- und Badging-Regeln sind [auf Inhalt angewendet](/help/communities/implementing-scoring.md#apply-rules-to-content) auf die gleiche Weise.

   * Einfache und erweiterte Scoring- und Badging-Regeln können auf denselben Inhalt angewendet werden.

* [Aktivieren von Abzeichen für Komponenten](/help/communities/implementing-scoring.md#enable-badges-for-component) ist generisch.

Bei der Einrichtung der Scoring- und Badging-Regeln gibt es folgende Unterschiede:

* Konfigurierbare erweiterte Scoring-Engine
* Erweiterte Scoring-Regeln:

   * `scoringType` ist auf `advanced` festgelegt
   * Erfordert `stopwords`

* Erweiterte Badging-Regeln:

   * `badgingType` ist auf `advanced` festgelegt
   * `badgingLevels` auf **Anzahl der zu vergebenden Expertenstufen**
   * Erfordert `badgingPaths` Array von Badges anstelle von Schwellenwerten Array-Mapping Punkte auf Badges.

>[!NOTE]
>
>Installieren Sie die [Expertenerkennungspaket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq610%2Fsocial%2Ffeaturepack%2Fcq-social-expert-identification-pkg).

## Konfigurierbare Scoring-Engine {#configurable-scoring-engine}

Die erweiterte Scoring-Engine bietet eine OSGi-Konfiguration mit Parametern, die sich auf den erweiterten Scoring-Algorithmus auswirken.

![advanced-scoring-engine](assets/advanced-scoring-engine.png)

* **Scoring-Gewichtungen**

  Geben Sie für ein Thema das Verb an, dem bei der Berechnung des Ergebnisses die höchste Priorität eingeräumt werden soll. Ein oder mehrere Themen können eingegeben werden, jedoch auf **ein Verb pro Thema**. Siehe [Themen und Verben](/help/communities/implementing-scoring.md#topics-and-verbs).
Eingestiegen als `topic,verb` mit Escapezeichen. Zum Beispiel:
  `/social/forum/hbs/social/forum\,ADD`
Standardmäßig ist das ADD-Verb für QnA- und Forenkomponenten festgelegt.

* **Scoring-Bereich**

  Der Bereich für erweiterte Bewertungen wird durch diesen Wert (Höchstwert) und 0 (kleinstmögliche Punktzahl) definiert.

  Der Standardwert ist 100, sodass der Scoring-Bereich zwischen 0 und 100 liegt.

* **Zeitintervall für Entitätsverfall**

  Dieser Parameter stellt die Anzahl der Stunden dar, nach denen alle Entitätsbewertungen veraltet sind. Dies ist erforderlich, um alte Inhalte nicht mehr in Bewertungen für eine Community-Site aufzunehmen.

  Der Standardwert ist 216000 Stunden (~24 Jahre).

* **Scoring-Wachstumsrate**
Dies gibt den Wert zwischen dem 0-Scoring-Bereich an, über den das Wachstum hinausgeht und die Anzahl der Experten begrenzt.

  Der Standardwert ist 50.

## Erweiterte Scoring-Regeln {#advanced-scoring-rules}

Bei der grundlegenden Bewertung ist die zum Verdienen eines Abzeichens erforderliche Menge bekannt.

Bei der erweiterten Auswertung wird die benötigte Menge ständig angepasst, basierend auf der Menge an Qualitätsdaten innerhalb des Systems. Die Auswertung wird kontinuierlich so berechnet, dass sie einer Glockenkurve ähnelt.

Wenn ein Mitglied ein Expertenabzeichen für ein Thema erhält, das nicht mehr aktiv ist, besteht die Möglichkeit, dass es aufgrund des Verfalls im Laufe der Zeit sein Abzeichen verliert.

### scoringType {#scoringtype}

Eine Scoring-Regel ist ein Satz von Scoring-Unterregeln, von denen jede die `scoringType`.

Um die erweiterte Scoring-Engine aufzurufen, muss die `scoringType`sollte auf `advanced`.

Siehe [Scoring-Unterregeln](/help/communities/implementing-scoring.md#scoring-sub-rules).

![advanced-scoring-type](assets/advanced-scoring-type.png)

### Stoppwörter {#stopwords}

Das erweiterte Scoring-Paket installiert einen Konfigurationsordner, der eine stopwords -Datei enthält:

* `/libs/settings/community/scoring/configuration/stopwords`

Der erweiterte Scoring-Algorithmus verwendet die Liste der in der Stoppwörter-Datei enthaltenen Wörter, um häufig verwendete englische Wörter zu identifizieren, die bei der Inhaltsverarbeitung ignoriert werden.

Es ist nicht zu erwarten, dass diese Datei geändert wird.

Wenn die Stoppwortdatei fehlt, erzeugt die erweiterte Scoring-Engine einen Fehler.

## Erweiterte Badging-Regeln {#advanced-badging-rules}

Die Eigenschaften der erweiterten Badging-Regel unterscheiden sich von der [Grundlegende Eigenschaften von Badging-Regeln](/help/communities/implementing-scoring.md#badging-rules).

Anstatt Punkte mit einem Badge-Bild zu verknüpfen, ist es nur erforderlich, die Anzahl der zulässigen Experten und das zu vergebende Badge-Bild zu identifizieren.

![advanced-badging-rules](assets/advanced-badging-rules.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Typ</th>
   <th>Wertbeschreibung</th>
  </tr>
  <tr>
   <td>badgingPath</td>
   <td>Zeichenfolge[]</td>
   <td><em>(Erforderlich)</em> Eine mehrwertige Zeichenfolge von Badge-Bildern bis zur Anzahl der badgingLevels. Die Badge-Bildpfade müssen so angeordnet sein, dass der erste an den höchsten Fachmann vergeben wird. Wenn weniger Abzeichen vorhanden sind, als durch badgingLevels angegeben, füllt das letzte Abzeichen im Array den Rest des Arrays aus. Beispieleintrag:<br /> <code>/libs/settings/community/badging/images/expert-badge/jcr:content/expert.png</code></td>
  </tr>
  <tr>
   <td>badgingLevels</td>
   <td>Long</td>
   <td><em>(Optional)</em> Gibt den Umfang des zu vergebenden Fachwissens an. Wenn beispielsweise eine <code>expert </code>und <code>almost expert</code> (zwei Abzeichen), sollte der Wert auf 2 gesetzt werden. BadgingLevel sollte mit der Anzahl der von Experten verwendeten Badge-Bilder übereinstimmen, die für die badgingPath -Eigenschaft aufgelistet sind. Der Standardwert ist 1.</td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>Zeichenfolge</td>
   <td><em>(Erforderlich)</em> Identifiziert die Scoring-Engine entweder als "Standard"oder als "erweitert". Auf "Erweitert"gesetzt, andernfalls ist der Standardwert "Einfach".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>Zeichenfolge[]</td>
   <td><em>(Optional)</em> Eine Zeichenfolge mit mehreren Werten, um die Badging-Regel auf die Auswertung von Ereignissen zu beschränken, die von einer oder mehreren aufgelisteten Scoring-Regeln identifiziert wurden.<br /> Beispieleintrag:<br /> <code>/libs/settings/community/scoring/rules/adv-comments-scoring</code><br /> Der Standardwert ist keine Einschränkung.</td>
  </tr>
 </tbody>
</table>

## Einbezogene Regeln und Zeichen {#included-rules-and-badge}

### Include Badge {#included-badge}

Diese Beta-Version beinhaltet ein belohnungsbasiertes Expertenabzeichen:

* `expert`

  `/libs/settings/community/badging/images/expert-badge/jcr:content/expert.png`

![expert-badge](assets/included-badge.png)

Damit das Expertenabzeichen als Belohnung für Aktivitäten angezeigt wird, stellen Sie Folgendes sicher:

* `Badges` für die Funktion aktiviert sind, z. B. eine Forum- oder QnA-Komponente.

* Erweiterte Scoring- und Badging-Regeln werden auf die Seite (oder den Vorgänger) angewendet, auf der die Komponente platziert wird

Siehe Grundlegende Informationen für:

* [Aktivieren von Abzeichen für eine Komponente](/help/communities/implementing-scoring.md#enableforcomponent)
* [Regeln anwenden](/help/communities/implementing-scoring.md#applytopage)

### Einbezogene Scoring-Regeln und Unterregeln {#included-scoring-rules-and-sub-rules}

In der Beta-Version sind zwei erweiterte Scoring-Regeln für die [Forumsfunktion](/help/communities/functions.md#forum-function) (jeweils eine für die Foren- und Kommentarkomponenten der Forumsfunktion):

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

* Beide `rules` und `sub-rules` Knoten sind vom Typ `cq:Page`.
* `subRules` ist ein Attribut des Typs String`[]` zur Regel `jcr:content` Knoten.
* `sub-rules` kann für verschiedene Scoring-Regeln freigegeben werden.
* `rules` sollte sich in einem Repository-Speicherort mit Leserechte für alle befinden.
* Regelnamen müssen unabhängig vom Speicherort eindeutig sein.

### Einbezogene Badging-Regeln {#included-badging-rules}

In der Version sind zwei erweiterte Badging-Regeln enthalten, die dem [erweiterte Foren und Regeln zur Kommentarbewertung](#included-scoring-rules-and-sub-rules).

* `/libs/settings/community/badging/rules/adv-comments-badging`
* `/libs/settings/community/badging/rules/adv-forums-badging`

**Anmerkungen:**

* `rules` -Knoten sind vom Typ cq:Page.
* `rules` sollte sich in einem Repository-Speicherort mit Leserechte für alle befinden.
* Regelnamen müssen unabhängig vom Speicherort eindeutig sein.
