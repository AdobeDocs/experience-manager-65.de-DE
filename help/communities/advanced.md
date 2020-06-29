---
title: Erweiterte Bewertung und Abzeichen
seo-title: Erweiterte Bewertung und Abzeichen
description: Einrichten der erweiterten Bewertung
seo-description: Einrichten der erweiterten Bewertung
uuid: 48caca57-43d3-4f2f-adf3-257428ba54d5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: eb3d5c37-8097-46de-8c4f-804ea723f1c5
docset: aem65
translation-type: tm+mt
source-git-commit: 9ea2efb7409ae38c8771815336ae0d9388d923fa
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 1%

---


# Erweiterte Bewertung und Abzeichen{#advanced-scoring-and-badges}

## Überblick {#overview}

Die erweiterte Bewertung ermöglicht die Vergabe von Kennzeichen, um Mitglieder als Experten zu identifizieren. Bei der erweiterten Bewertung werden Punkte basierend auf der Menge *und* Qualität der von einem Mitglied erstellten Inhalte zugewiesen, während bei der grundlegenden Bewertung Punkte nur auf der Grundlage der erstellten Inhaltsmenge zugewiesen werden.

Dieser Unterschied ist auf die Bewertungsmaschine zurückzuführen, die zur Berechnung der Ergebnisse verwendet wird. Die Basis-Scoring-Engine verwendet einfache Mathematik. Die Advanced Scoring Engine ist ein adaptiver Algorithmus, der aktive Mitglieder belohnt, die wertvollen und relevanten Inhalt beisteuern, der durch die natürliche Sprachverarbeitung (Natural Language Processing, NLP) eines Themas abgezogen wird.

Neben der Relevanz von Inhalten berücksichtigen die Bewertungsalgorithmen auch Aktivitäten von Mitgliedern, wie z. B. Abstimmung und Prozentsatz der Antworten. Während die grundlegende Bewertung sie quantitativ umfasst, verwendet die erweiterte Bewertung sie algorithmisch.

Daher benötigt die erweiterte Scoring-Engine genügend Daten, um eine aussagekräftige Analyse zu ermöglichen. Der Leistungsschwellenwert für die Expertenausbildung wird ständig neu bewertet, da sich der Algorithmus ständig an die Menge und Qualität der erstellten Inhalte anpasst. Es gibt auch das Konzept des *Verfalls* älterer Posten eines Mitglieds. Wenn ein Expertenmitglied nicht mehr an dem Thema teilnimmt, in dem es einen Expertenstatus erlangt hat, könnte es zu einem bestimmten Zeitpunkt (siehe Konfiguration [der](#configurable-scoring-engine)Bewertungsmaschine) seinen Status als Experte verlieren.

Die Einrichtung einer erweiterten Bewertung ist praktisch identisch mit der eines Basisscorings:

* Grundlegende und erweiterte Scoring- und Kennzeichnungsregeln werden auf Inhalte [auf dieselbe Weise](/help/communities/implementing-scoring.md#apply-rules-to-content) angewendet.

   * Einfache und erweiterte Scoring- und Kennzeichnungsregeln können auf denselben Inhalt angewendet werden.

* [Die Aktivierung von Kennzeichen für Komponenten](/help/communities/implementing-scoring.md#enable-badges-for-component) ist generisch.

Die verschiedenen Regeln für die Bewertung und Kennzeichnung unterscheiden sich:

* Konfigurierbare erweiterte Scoring-Engine
* Erweiterte Bewertungsregeln:

   * `scoringType` setzen auf `advanced`
   * Erfordert `stopwords`

* Erweiterte Kennzeichnungsregeln:

   * `badgingType` setzen auf `advanced`
   * `badgingLevels` auf die **Anzahl der zu vergebenden Expertenstufen**
   * Erfordert ein `badgingPaths` Array von Kennzeichen anstelle von Schwellenwerten für Array-Zuordnungspunkten zu Kennzeichen.

>[!NOTE]
>
>Installieren Sie das [Expert Identification-Paket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg), um erweiterte Scoring- und Auszeichnungsfunktionen zu verwenden.


## Konfigurierbare Scoring-Engine {#configurable-scoring-engine}

Die erweiterte Scoring-Engine bietet eine OSGi-Konfiguration mit Parametern, die sich auf den erweiterten Scoring-Algorithmus auswirken.

![chlimage_1-260](assets/chlimage_1-260.png)

* **Gewichtungen bewerten**

   Geben Sie für ein Thema das Verb an, das bei der Berechnung des Ergebnisses die höchste Priorität erhalten soll. Es können ein oder mehrere Themen eingegeben werden, jedoch nur **ein Verb pro Thema**. Siehe [Themen und Verben](/help/communities/implementing-scoring.md#topics-and-verbs).
Wie `topic,verb` mit Escapezeichen eingegeben. Beispiel:
   `/social/forum/hbs/social/forum\,ADD`
Die Standardeinstellung ist auf das HINZUFÜGEN Verb für QnA- und Forumkomponenten festgelegt.

* **Bewertungsbereich**

   Der Bereich für erweiterte Ergebnisse wird durch diesen Wert (maximal mögliche Punktzahl) und 0 (niedrigstmögliche Punktzahl) definiert.

   Der Standardwert ist 100, sodass der Bewertungsbereich zwischen 0 und 100 liegt.

* **Zeitintervall für Entitätsabbruch**

   Dieser Parameter stellt die Anzahl der Stunden dar, nach denen alle Entitätsbewertungen veraltet sind. Dies ist erforderlich, damit alte Inhalte nicht mehr in Bewertungen für eine Community-Site einbezogen werden.

   Der Standardwert ist 216000 Stunden (~24 Jahre).

* **Bewertung der Wachstumsrate** Dies gibt den Wert zwischen 0 und dem Bewertungsbereich an, ab dem das Wachstum langsamer wird, um die Anzahl der Experten zu begrenzen.

   Der Standardwert ist 50.

## Erweiterte Bewertungsregeln {#advanced-scoring-rules}

In der Grundbewertung ist die Menge, die benötigt wird, um ein Zeichen zu verdienen, bekannt.

Bei der erweiterten Bewertung wird die benötigte Menge ständig an die Menge der Qualitätsdaten innerhalb des Systems angepasst. Die Bewertung wird kontinuierlich auf eine Weise berechnet, die einer Glockenkurve ähnlich ist.

Wenn ein Mitglied ein Expertenabzeichen zu einem Thema erhält, das nicht mehr aktiv ist, besteht die Möglichkeit, dass es aufgrund des Verfalls mit der Zeit sein Abzeichen verliert.

### scoringType {#scoringtype}

Eine Bewertungsregel ist ein Satz von Bewertungsunterregeln, von denen jede die `scoringType`Regeln deklariert.

Um die erweiterte Scoring-Engine aufzurufen, `scoringType`sollte die auf `advanced`.

Siehe [Scoring-Unterregeln](/help/communities/implementing-scoring.md#scoring-sub-rules).

![chlimage_1-261](assets/chlimage_1-261.png)

### Stoppwörter {#stopwords}

Das erweiterte Bewertungspaket installiert einen Konfigurationsordner, der eine stopwords-Datei enthält:

* `/libs/settings/community/scoring/configuration/stopwords`

Der erweiterte Bewertungsalgorithmus verwendet die Liste der Wörter, die in der Stoppwortdatei enthalten sind, um häufig verwendete englische Wörter zu identifizieren, die bei der Inhaltsverarbeitung ignoriert werden.

Es wird nicht erwartet, dass diese Datei geändert wird.

Wenn die stopwords-Datei fehlt, gibt die erweiterte Scoring-Engine einen Fehler aus.

## Erweiterte Abstandsregeln {#advanced-badging-rules}

Die Eigenschaften der erweiterten Kennzeichnungsregel unterscheiden sich von den Eigenschaften der [grundlegenden Kennzeichnungsregel](/help/communities/implementing-scoring.md#badging-rules).

Anstatt Punkte mit einem Abzeichen zu verknüpfen, ist es nur notwendig, die Anzahl der zulässigen Experten und das zu vergebende Abbild zu identifizieren.

![chlimage_1-262](assets/chlimage_1-262.png)

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
   <td><em>(Erforderlich)</em> Eine Zeichenfolge mit mehreren Werten für Abzeichen bis zur Anzahl der badgingLevels. Die Abzeichen-Bildpfade müssen so angeordnet sein, dass der erste dem höchsten Fachmann verliehen wird. Wenn weniger Zeichen vorhanden sind als durch badgingLevels angegeben, füllt das letzte Zeichen im Array den Rest des Arrays aus. Beispieleintrag:<br /> <code>/libs/settings/community/badging/images/expert-badge/jcr:content/expert.png</code></td>
  </tr>
  <tr>
   <td>badgingLevels</td>
   <td>Long</td>
   <td><em>(Optional)</em> Gibt die zu vergebenden Fachkenntnisse an. Wenn es beispielsweise ein <code>expert </code>und ein <code>almost expert</code> (zwei Abzeichen) geben sollte, sollte der Wert auf 2 gesetzt werden. Die badgingLevel-Eigenschaft sollte mit der Anzahl der Kennzeichnungsbilder für Experten übereinstimmen, die für die badgingPath-Eigenschaft aufgelistet sind. Der Standardwert ist 1.</td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>Zeichenfolge</td>
   <td><em>(Erforderlich)</em> Hiermit wird die Scoring-Engine entweder als "grundlegend"oder als "erweitert"gekennzeichnet. Auf "advanced"gesetzt, andernfalls ist der Standard "basic".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>Zeichenfolge[]</td>
   <td><em>(Optional)</em> Eine Zeichenfolge mit mehreren Werten, mit der die Kennzeichnungsregel auf die von der/den aufgeführten Bewertungsregel(n) identifizierten Ereignis beschränkt wird.<br /> Beispieleintrag:<br /> <code>/libs/settings/community/scoring/rules/adv-comments-scoring</code><br /> Standard ist keine Einschränkung.</td>
  </tr>
 </tbody>
</table>

## Einschließlich Regeln und Zeichen {#included-rules-and-badge}

### Einschließlich Badge {#included-badge}

In dieser Beta-Version ist ein auf Belohnung basierendes Expertenabzeichen enthalten:

* `expert`

   `/libs/settings/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

Damit das Expertenkennzeichen als Belohnung für die Aktivität angezeigt wird, müssen Sie sicherstellen, dass:

* `Badges` für die Funktion aktiviert sind, z. B. ein Forum oder eine QnA-Komponente.

* Erweiterte Scoring- und Kennzeichnungsregeln werden auf die Seite (oder den Vorgänger) angewendet, auf der die Komponente platziert wird

Grundlegende Informationen finden Sie unter:

* [Aktivieren der Markierung für eine Komponente](/help/communities/implementing-scoring.md#enableforcomponent)
* [Anwenden von Regeln](/help/communities/implementing-scoring.md#applytopage)

### Einbezogene Bewertungsregeln und Unterregeln {#included-scoring-rules-and-sub-rules}

In der Beta-Version sind zwei erweiterte Bewertungsregeln für die [Forenfunktion](/help/communities/functions.md#forum-function) enthalten (eine für die Foren- und Kommentarkomponenten der Forumsfunktion):

1. `/libs/settings/community/scoring/rules/adv-comments-scoring`

   * `subRules[] =
/libs/settings/community/scoring/rules/sub-rules/adv-comments-rule
/libs/settings/community/scoring/rules/sub-rules/adv-voting-rule-owner
/libs/settings/community/scoring/rules/sub-rules/adv-voting-rule`

1. `/libs/settings/community/scoring/rules/adv-forums-scoring`

   * `subRules[] =
/libs/settings/community/scoring/rules/sub-rules/adv-forums-rule
/libs/settings/community/scoring/rules/sub-rules/adv-comments-rule
/libs/settings/community/scoring/rules/sub-rules/adv-voting-rule-owner`

**Hinweise:**

* Sowohl `rules` als auch `sub-rules` Knoten sind vom Typ `cq:Page`.

* `subRules` ist ein Attribut des Typs String[] auf dem Knoten der Regel `jcr:content` .

* `sub-rules` kann für verschiedene Bewertungsregeln freigegeben werden.

* `rules` sollte sich in einem Repository mit Leserechte für alle befinden.

* Regelnamen müssen unabhängig vom Ort eindeutig sein.

### Einbezogene Kennzeichnungsregeln {#included-badging-rules}

In der Version sind zwei erweiterte Kennzeichnungsregeln enthalten, die den [erweiterten Foren und den Regeln](#included-scoring-rules-and-sub-rules)zur Bewertung von Kommentaren entsprechen.

* `/libs/settings/community/badging/rules/adv-comments-badging`
* `/libs/settings/community/badging/rules/adv-forums-badging`

**Hinweise:**

* `rules` Knoten sind vom Typ cq:Page.
* `rules` sollte sich in einem Repository mit Leserechte für alle befinden.
* Regelnamen müssen unabhängig vom Ort eindeutig sein.

