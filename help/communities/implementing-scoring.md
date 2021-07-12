---
title: Communities-Scoring und -Abzeichen
seo-title: Communities-Scoring und -Abzeichen
description: Mit AEM Communities-Scoring und -Abzeichen können Sie Community-Mitglieder identifizieren und belohnen
seo-description: Mit AEM Communities-Scoring und -Abzeichen können Sie Community-Mitglieder identifizieren und belohnen
uuid: d73683df-a413-4b3c-869c-67568bfdfcf6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ea033bb9-cb92-4c93-855f-8c902999378c
docset: aem65
tagskeywords: scoring, badging, badges, gamification
role: Admin
exl-id: 4aa857f7-d111-4548-8f03-f6d6c27acf51
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '2884'
ht-degree: 3%

---

# Communities-Scoring und -Abzeichen {#communities-scoring-and-badges}

## Übersicht {#overview}

Die AEM Communities-Scoring- und -Badges-Funktion bietet die Möglichkeit, Community-Mitglieder zu identifizieren und zu belohnen.

Die wichtigsten Aspekte von Scoring und Badges sind:

* [Weisen Sie ](#assign-and-revoke-badges) Badgesten zu, um die Rolle eines Mitglieds in der Community zu identifizieren.

* [Grundlegende Vergabe von ](#enable-scoring) Badgesto-Mitgliedern, um ihre Teilnahme zu fördern (Menge der erstellten Inhalte).

* [Fortgeschrittene Vergabe von ](/help/communities/advanced.md) Badgesto identifizieren Mitglieder als Experten (Qualität der Inhalte erstellt).

**** Beachten Sie, dass die Vergabe von Badges  [nicht standardmäßig](/help/communities/implementing-scoring.md#main-pars-text-237875536) aktiviert ist.

>[!CAUTION]
>
>Die in CRXDE Lite sichtbare Implementierungsstruktur kann sich ändern, sobald die Benutzeroberfläche verfügbar ist.

## Zeichen {#badges}

Abzeichen werden unter dem Namen eines Mitglieds platziert, um entweder ihre Rolle oder ihre Stellung in der Community anzugeben. Abzeichen können entweder als Bild oder als Name angezeigt werden. Wenn der Name als Bild angezeigt wird, wird er als alternativer Text für die Barrierefreiheit eingefügt.

Standardmäßig befinden sich Abzeichen im Repository unter

* `/libs/settings/community/badging/images`

Wenn sie an einem anderen Speicherort gespeichert sind, sollten sie für alle lesbar sein.

Abzeichen werden in UGC dahingehend unterschieden, ob sie gemäß den Regeln zugewiesen wurden oder verdient wurden. Derzeit werden zugewiesene Abzeichen als Text und Earned Abzeichen als Bild angezeigt.

### Benutzeroberfläche der Badge-Verwaltung {#badge-management-ui}

Die Communities [Badges-Konsole](/help/communities/badges.md) bietet die Möglichkeit, benutzerdefinierte Abzeichen hinzuzufügen, die für ein Mitglied angezeigt werden können, wenn es eine bestimmte Rolle in der Community spielt (zugewiesen).

### Zugewiesene Abzeichen {#assigned-badges}

Rollenbasierte Abzeichen werden von einem Administrator den Community-Mitgliedern basierend auf ihrer Rolle in der Community zugewiesen.

Zugewiesene (und erwartete) Zeichen werden im ausgewählten [SRP](/help/communities/srp.md) gespeichert und sind nicht direkt zugänglich. Solange keine grafische Benutzeroberfläche verfügbar ist, können rollenbasierte Abzeichen nur mit Code oder cURL zugewiesen werden. Anweisungen zu cURL finden Sie im Abschnitt [Zuweisen und Sperren von Abzeichen](#assign-and-revoke-badges).

In der Version sind drei rollenbasierte Abzeichen enthalten:

* **Moderator**

   `/libs/settings/community/badging/images/moderator/jcr:content/moderator.png`

* **Gruppenmanager**

   `/libs/settings/community/badging/images/group-manager/jcr:content/group-manager.png`

* **privilegiertes Mitglied**

   `/libs/settings/community/badging/images/privileged-member/jcr:content/privileged-member.png`

   ![assigned-badges](assets/assigned-badges.png)

### Ausgezeichnete Abzeichen {#awarded-badges}

Belohnungsbasierte Abzeichen werden vom Scoring-Dienst an Community-Mitglieder vergeben, basierend auf Regeln, die auf ihre Aktivität in der Community angewendet werden.

Damit Abzeichen als Belohnung für Aktivitäten angezeigt werden, müssen zwei Dinge geschehen:

* Die Abzeichen müssen für die Funktionskomponente [enabled](#enableforcomponent) sein.
* Scoring- und Badging-Regeln müssen [angewendet](#applytopage) auf die Seite (oder den Vorgänger) angewendet werden, auf der die Komponente platziert wird.

In der Version sind drei belohnungsbasierte Abzeichen enthalten:

* **Gold**

   `/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

* **silber**

   `/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

* **Bronze**

   `/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

   ![Auszeichnung](assets/awarded-badges.png)

>[!NOTE]
>
>Scoring-Regeln können so konfiguriert werden, dass negative Punkte für Beiträge zugewiesen werden, die als unangemessen gekennzeichnet sind und sich daher auf den Punktwert auswirken. Nachdem ein Badge jedoch verdient wurde, wird es aufgrund von Scoring-Punktreduzierung oder Änderungen der Scoring-Regel nicht automatisch entfernt.
>
>Zugewiesene Abzeichen können wie zugewiesene Abzeichen widerrufen werden. Siehe Abschnitt [Kennzeichen zuweisen und Sperren](#assign-and-revoke-badges) . Zukünftige Verbesserungen umfassen eine Benutzeroberfläche zur Verwaltung der Abzeichen von Mitgliedern.

### Benutzerdefinierte Abzeichen {#custom-badges}

Benutzerdefinierte Badges können mit der [Badges-Konsole](/help/communities/badges.md) installiert und in Badging-Regeln zugewiesen oder angegeben werden.

Bei der Installation über die Badges-Konsole werden benutzerdefinierte Abzeichen automatisch in die Veröffentlichungsumgebung repliziert.

## Scoring aktivieren {#enable-scoring}

Die Auswertung ist standardmäßig nicht aktiviert. Die grundlegenden Schritte zum Einrichten und Aktivieren der Auswertung und Verleihung von Abzeichen sind:

* Identifizieren Sie Regeln für Ertragspunkte ([Scoring-Regeln](#scoring-rules)).
* Für Punkte, die nach Scoring-Regeln gesammelt wurden, weisen Sie [Badges](#badges) ([Badging-Regeln](#badging-rules)) zu.

* [Wenden Sie die Scoring- und Badging-Regeln auf eine Community-Site](#apply-rules-to-content) an.
* [Aktivieren Sie Badging für Community-Funktionen](#enable-badges-for-component).

Lesen Sie den Abschnitt [Schnelltest](#quick-test) , um die Auswertung für eine Community-Site mithilfe der standardmäßigen Scoring- und Badging-Regeln für Foren und Kommentare zu aktivieren.

### Regeln auf Inhalt anwenden {#apply-rules-to-content}

Um Scoring und Badges zu aktivieren, fügen Sie die Eigenschaften `scoringRules` und `badgingRules` zu einem beliebigen Knoten in der Inhaltsstruktur für die Site hinzu.

Wenn die Site bereits veröffentlicht wurde, veröffentlichen Sie die Site erneut, nachdem Sie alle Regeln angewendet und Komponenten aktiviert haben.

Regeln, die für eine Badging-fähige Komponente gelten, sind diejenigen für den aktuellen Knoten oder dessen Vorgänger.

Wenn der Knoten vom Typ `cq:Page` (empfohlen) ist, fügen Sie mithilfe von CRXDE|Lite die Eigenschaften seinem Knoten `jcr:content` hinzu.

| **Eigenschaft** | **Typ** | **Beschreibung** |
|---|---|---|
| badgingRules | Zeichenfolge | eine Array-Liste von [Badging-Regeln](#badging-rules) |
| scoringRules | Zeichenfolge | eine Array-Liste von [Scoring-Regeln](#scoring-rules) |

>[!NOTE]
>
>Wenn eine Scoring-Regel anscheinend keine Auswirkungen auf das Verteilen von Abzeichen hat, stellen Sie sicher, dass die Scoring-Regel nicht von der Eigenschaft scoringRules der Badging-Regel blockiert wurde. Siehe Abschnitt [Badging Rules](#badging-rules).

### Aktivieren von Abzeichen für Komponenten {#enable-badges-for-component}

Die Scoring- und Bading-Regeln gelten nur für Instanzen von Komponenten, die das Badging durch Bearbeiten der Komponentenkonfiguration im [Authoring-Modus](/help/communities/author-communities.md) aktiviert haben.

Eine boolesche Eigenschaft `allowBadges` aktiviert/deaktiviert die Anzeige von Abzeichen für eine Komponenteninstanz. Sie kann im [Dialogfeld zur Komponentenbearbeitung](/help/communities/author-communities.md) für Forum-, QnA- und Kommentarkomponenten über ein Kontrollkästchen mit der Bezeichnung **Anzeigemarken** konfiguriert werden.

#### Beispiel : allowBadges für die Instanz der Forum-Komponente {#example-allowbadges-for-forum-component-instance}

![enable-badges-component](assets/enable-badges-component.png)

>[!NOTE]
>
>Jede Komponente kann überlagert werden, um Abzeichen anhand des in Foren, Fragen und Antworten sowie Kommentaren enthaltenen HBS-Codes anzuzeigen.

## Scoring-Regeln {#scoring-rules}

Scoring-Regeln sind die Grundlage für die Bewertung zum Zweck der Vergabe von Badges.

Jede Scoring-Regel ist ganz einfach eine Liste mit einer oder mehreren Unterregeln. Scoring-Regeln werden auf den Community-Site-Inhalt angewendet, um die Regeln zu identifizieren, die bei der Aktivierung von Badges angewendet werden sollen.

Scoring-Regeln werden vererbt, sind jedoch nicht additiv. Beispiel:

* Wenn Seite 2 die Scoring-Regel2 enthält und ihr Vorgänger Seite 1 die Scoring-Regel 1 enthält.
* Eine Aktion auf einer Komponente &quot;Seite 2&quot;ruft sowohl Regel1 als auch Regel2 auf.
* Wenn beide Regeln anwendbare Unterregeln für dasselbe `topic/verb` enthalten:

   * Nur die Unterregel aus Regel 2 wirkt sich auf das Ergebnis aus.
   * Die Bewertungen aus beiden Unterregeln werden nicht zusammen hinzugefügt.

Wenn es mehr als eine Scoring-Regel gibt, werden die Werte für jede Regel separat beibehalten.

Scoring-Regeln sind Knoten des Typs `cq:Page` mit Eigenschaften auf dem Knoten `jcr:content` , die die Liste der Unterregeln angeben, die sie definieren.

Die Bewertungen werden im SRP gespeichert.

>[!NOTE]
>
>Best Practice: Benennen Sie jede Scoring-Regel eindeutig.
>
>Die Namen von Scoring-Regeln sollten global eindeutig sein. sollten sie nicht mit demselben Namen enden.
>
>Ein Beispiel dafür, was *not* zu tun hat:
>
>/libs/settings/community/scoring/rules/site1/forums-scoring
>/libs/settings/community/scoring/rules/site2/forums-scoring

### Scoring-Unterregeln {#scoring-sub-rules}

Die Scoring-Unterregeln enthalten die Eigenschaften, die die Werte für die Teilnahme an der Community detailliert beschreiben.

Jede Scoring-Unterregel identifiziert:

* Welche Aktivitäten werden verfolgt?
* Welche speziellen Community-Funktionen sind betroffen?
* Wie viele Punkte werden vergeben?

Standardmäßig werden Punkte an das Mitglied vergeben, das eine Aktion durchführt, es sei denn, die Unterregel gibt den Eigentümer des Inhalts an, der die Punkte erhält ( `forOwner`).

Jede Unterregel kann in einer oder mehreren Scoring-Regeln enthalten sein.

Der Name der Unterregel folgt normalerweise dem Muster der Verwendung eines *Betreffs* , *Objekts* und *Verb*. Beispiel:

* member-comment-create
* member-receive-Votum

Unterregeln sind Knoten des Typs `cq:Page` mit Eigenschaften auf dem Knoten `jcr:content`, die die [Verben und Themen](#topics-and-verbs) angeben.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Typ</th>
   <th> Wert Beschreibung</th>
  </tr>
  <tr>
   <td><i><code>VERB</code></i></td>
   <td>Long</td>
   <td>
    <ul>
     <li>erforderlich; das Verb entspricht einer Ereignisaktion</li>
     <li>Es muss mindestens eine Verb-Eigenschaft vorhanden sein.</li>
     <li>Das Verb muss in allen GROSSBUCHSTABEN angegeben werden.</li>
     <li>Es kann mehrere Verb-Eigenschaften geben, aber keine Duplikate.</li>
     <li>der Wert ist der Wert, der für dieses Ereignis gelten soll</li>
     <li>der Wert kann positiv oder negativ sein</li>
     <li>Eine Liste der Verben, die in der Version unterstützt werden, finden Sie im Abschnitt <a href="#topics-and-verbs">Themen und Verben</a> .</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>topics</code></td>
   <td>Zeichenfolge</td>
   <td>
    <ul>
     <li>fakultativ; beschränkt die Unterregel auf Community-Komponenten, die nach Ereignisthemen identifiziert werden</li>
     <li>sofern angegeben: Wert ist mehrwertige Zeichenfolge von Ereignisthemen</li>
     <li>Eine Liste der Themen in der Version finden Sie im Abschnitt <a href="#topics-and-verbs">Themen und Verben</a> .</li>
     <li>Die Standardeinstellung ist, auf alle Themen anzuwenden, die mit den Verb(en) verknüpft sind</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>forOwner</code></td>
   <td>Boolesch</td>
   <td>
    <ul>
     <li>fakultativ; ist nicht relevant, wenn ein Mitglied mit eigenen Inhalten handelt</li>
     <li>Wenn "true", Bewertung auf den Eigentümer des Inhalts anwenden, auf den reagiert wird</li>
     <li>Wenn false, Punktzahl auf Teilnehmer anwenden, die eine Aktion durchführen</li>
     <li>default is false</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>scoringType</code></td>
   <td>Zeichenfolge</td>
   <td>
    <ul>
     <li>fakultativ; identifiziert die Scoring-Engine</li>
     <li>if "basic", gibt die Scoring-Engine auf Basis der Menge an
      <ul>
       <li>in der Version enthalten</li>
      </ul> </li>
     <li>Wenn "erweitert", gibt die Scoring-Engine basierend auf Qualität und Menge an
      <ul>
       <li>erfordert ein <a href="/help/communities/advanced.md">zusätzliches Paket</a></li>
      </ul> </li>
     <li>Standardwert ist "basic"</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Einbezogene Scoring-Regeln und Unterregeln {#included-scoring-rules-and-sub-rules}

In der Version sind zwei Scoring-Regeln für die [Forumfunktion](/help/communities/functions.md#forum-function) enthalten (jeweils eine für die Forum- und Kommentarkomponenten der Forumsfunktion):

1. /libs/settings/community/scoring/rules/comments-scoring

   * subRules[] =
/libs/settings/community/scoring/rules/sub-rules/member-comment-create
/libs/settings/community/scoring/rules/sub-rules/member-receive-voice
/libs/settings/community/scoring/rules/sub-rules/member-given-Votum
/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

1. /libs/settings/community/scoring/rules/forums-scoring

   * subRules[] =
/libs/settings/community/scoring/rules/sub-rules/member-forum-create
/libs/settings/community/scoring/rules/sub-rules/member-receive-voice
/libs/settings/community/scoring/rules/sub-rules/member-given-Votum
/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

**Anmerkungen:**

* Die Knoten `rules` und `sub-rules` weisen den Typ cq:Page auf.

* `subRules` ist ein Attribut vom Typ [] String im  `jcr:content` Knoten der Regel.

* `sub-rules` kann für verschiedene Scoring-Regeln freigegeben werden.
* `rules` sollte sich in einem Repository-Speicherort mit Leseberechtigung für alle befinden.

   * Regelnamen müssen unabhängig vom Speicherort eindeutig sein.

### Aktivieren benutzerdefinierter Scoring-Regeln {#activating-custom-scoring-rules}

Änderungen oder Ergänzungen an Scoring-Regeln oder Unterregeln, die in der Autorenumgebung vorgenommen werden, müssen in der Veröffentlichungsumgebung installiert werden.

## Badging-Regeln {#badging-rules}

Badging-Regeln verknüpfen Scoring-Regeln mit Abzeichen, indem Folgendes angegeben wird:

* Scoring-Regel
* Für ein bestimmtes Zeichen erforderliche Punktzahl

Badging-Regeln sind Knoten des Typs `cq:Page` mit Eigenschaften auf dem Knoten `jcr:content` , die Scoring-Regeln mit Bewertungen und Abzeichen korrelieren.

Die Badging-Regeln bestehen aus einer obligatorischen `thresholds`-Eigenschaft, bei der es sich um eine geordnete Liste von Bewertungen handelt, die Abzeichen zugeordnet sind. Die Werte müssen in zunehmendem Wert geordnet werden. Beispiel:

* `1|/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Ein Bronze-Badge wird für 1 Punkt erwartet.

* `60|/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

   * Wenn 60 Punkte gesammelt wurden, wird ein Silberabzeichen vergeben.

* `80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

   * Wenn 80 Punkte gesammelt wurden, wird ein Goldabzeichen erwartet.

Badging-Regeln werden mit Scoring-Regeln gepaart, die bestimmen, wie Punkte gesammelt werden. Siehe Abschnitt [Regeln auf Inhalt anwenden](#apply-rules-to-content).

Die `scoringRules`-Eigenschaft einer Badging-Regel beschränkt einfach, welche Scoring-Regeln mit dieser Badging-Regel gepaart werden können.

>[!NOTE]
>
>Best Practice : Badge-Bilder erstellen, die für jede AEM Site eindeutig sind.

![badging-rule-configuration](assets/badging-rule-configuration.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Typ</th>
   <th>Wert Beschreibung</th>
  </tr>
  <tr>
   <td>Schwellenwerte</td>
   <td>Zeichenfolge</td>
   <td><em>(erforderlich)</em> Eine mehrwertige Zeichenfolge des Formulars 'number|path'
    <ul>
     <li>number = Wert</li>
     <li>| = die vertikale Linie char (U+007C)</li>
     <li>path = vollständiger Pfad zur Badge-Bild-Ressource</li>
    </ul> Die Zeichenfolgen müssen so angeordnet sein, dass die Zahlen an Wert zunehmen und zwischen der Zahl und dem Pfad kein Leerzeichen angezeigt wird.<br /> Beispieleintrag :<br /> <code>80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png</code></td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>Zeichenfolge</td>
   <td><em>(optional)</em> Identifiziert die Scoring-Engine als "Basis"oder "Erweitert". Wenn die erweiterte Scoring-Engine gewünscht wird, finden Sie weitere Informationen unter <a href="/help/communities/advanced.md">Erweiterte Scoring- und Badges</a>. Die Standardeinstellung ist "Standard".</td>
  </tr>
  <tr>
   <td>scoringRules</td>
   <td>Zeichenfolge</td>
   <td>(<em>optional</em>) Eine mehrwertige Zeichenfolge, die die Badging-Regel auf die von den Scoring-Regeln identifizierten Scoring-Ereignisse beschränkt</td>
  </tr>
 </tbody>
</table>

### Einbezogene Badging-Regeln {#included-badging-rules}

In der Version sind zwei Badging-Regeln enthalten, die den [Foren und Kommentar-Scoring-Regeln](#includedscoringrules) entsprechen.

* `/libs/settings/community/badging/rules/comments-badging`

* `/libs/settings/community/badging/rules/forums-badging`

**Anmerkungen:**

* `rules` -Knoten sind vom Typ cq:Page.
* `rules` sollte sich in einem Repository-Speicherort mit Leseberechtigung für alle befinden.

   * Regelnamen müssen unabhängig vom Speicherort eindeutig sein.

### Aktivieren benutzerdefinierter Badging-Regeln {#activating-custom-badging-rules}

Änderungen oder Ergänzungen an Badging-Regeln oder Bildern, die in der Autorenumgebung vorgenommen werden, müssen in der Veröffentlichungsumgebung installiert werden.

## Zuteilen und Entziehen von Abzeichen {#assign-and-revoke-badges}

Kennzeichen können Mitgliedern entweder über die [Mitgliederkonsole](/help/communities/members.md#badges-tab) oder programmgesteuert über cURL-Befehle zugewiesen werden.

Die folgenden cURL-Befehle zeigen, was für eine HTTP-Anfrage zum Zuweisen und Sperren von Badges erforderlich ist. Das Standardformat lautet:

cURL -i -X POST -H *header* -u *signin* -F *operation* -F *badge* *member-profile-url*

*header*  = &quot;Accept:application/json&quot; benutzerdefinierte Kopfzeile zum Übergeben an den Server (erforderlich)

*signin* = administrator-id:password zum Beispiel : admin:admin

*operation* = &quot;:operation=social:assignBadge&quot; OR &quot;:operation=social:deleteBadge&quot;

*badge* = &quot;badgeContentPath=*badge-image-file*&quot;

*badge-image-file*  = der Speicherort der Badge-Bilddatei im Repository, z. B. : /libs/settings/community/badging/images/moderator/jcr:content/moderator.png

*member-profile-url*  = Endpunkt für das Profil des Mitglieds in der Veröffentlichungsinstanz, z. B. : https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>Die *member-profile-url*:
>
>* Kann auf eine Autoreninstanz verweisen, wenn der [Tunnel-Dienst](/help/communities/users.md#tunnel-service) aktiviert ist.
>* Kann ein undurchsichtiger, zufälliger Name sein - siehe [Sicherheits-Checkliste](/help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) bezüglich der autorisierbaren ID.


### Beispiele: {#examples}

#### Moderatorzeichen zuweisen {#assign-a-moderator-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/libs/settings/community/badging/images/moderator/jcr:content/moderator.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

#### Verknüpftes Silber-Zeichen sperren {#revoke-an-assigned-silver-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:deleteBadge" -F "badgeContentPath=/libs/settings/community/badging/images/silver/jcr:content/silver.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

>[!NOTE]
>
>Die Verwendung von cURL zum Zuweisen und Widerrufen von Badges funktioniert für jedes Badge-Bild. Bei der Zuweisung von Badge anstelle von Earned, werden diese als zugewiesene Badges markiert und entsprechend verarbeitet.

## Scoring und Abzeichen für benutzerdefinierte Komponenten {#scoring-and-badges-for-custom-components}

Scoring- und Badging-Regeln können für benutzerdefinierte Komponenten erstellt werden, indem die für die Komponente erstellten Ereignisthemen Verben zugeordnet werden.

## Themen und Verben {#topics-and-verbs}

Wenn Mitglieder mit Communities-Funktionen interagieren, werden Ereignisse gesendet, die asynchrone Listener wie Benachrichtigungen und Scoring Trigger werden können.

Die SocialEvent-Instanz einer Komponente zeichnet die Ereignisse als `actions` auf, die für `topic` auftreten. Das SocialEvent enthält eine Methode, mit der eine mit der Aktion verknüpfte `verb` zurückgegeben wird. Es gibt eine *n-1*-Beziehung zwischen `actions` und `verbs`.

Für die bereitgestellten Communities-Komponenten beschreiben die folgenden Tabellen die `verbs`, die für jeden `topic` definiert sind, der zur Verwendung in [Scoring-Unterregeln](#scoring-sub-rules) verfügbar ist.

>[!NOTE]
>
>Eine neue boolesche Eigenschaft `allowBadges` aktiviert/deaktiviert die Anzeige von Abzeichen für eine Komponenteninstanz. Sie kann in aktualisierten [Dialogfeldern zur Komponentenbearbeitung](/help/communities/author-communities.md) über ein Kontrollkästchen mit der Bezeichnung **Anzeigemarken** konfiguriert werden.

**[Calendar](/help/communities/calendar.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/calendar

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt ein Kalenderereignis |
| HINZUFÜGEN | Mitgliederkommentare für ein Kalenderereignis |
| UPDATE | Kalenderereignis oder -kommentar eines Mitglieds wird bearbeitet |
| DELETE | Kalenderereignis oder -kommentar eines Mitglieds wird gelöscht |

**[Kommentare](/help/communities/comments.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Kommentar |
| HINZUFÜGEN | Mitglied antwortet auf Kommentar |
| AKTUALISIEREN | Der Kommentar des Mitglieds wird bearbeitet |
| DELETE | Kommentar des Mitglieds wird gelöscht |

**[File Library](/help/communities/file-library.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Ordner |
| ANHÄNGEN | Mitglied lädt eine Datei hoch |
| AKTUALISIEREN | Mitglied aktualisiert Ordner oder Dateien |
| DELETE | Mitglied löscht Ordner oder Dateien |

**[Forum](/help/communities/forum.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Forumthema |
| HINZUFÜGEN | Mitgliederantworten zum Forumthema |
| AKTUALISIEREN | Forenthema oder Antwort des Mitglieds wird bearbeitet |
| DELETE | Forenthema oder Antwort des Mitglieds wurde gelöscht |

**[Journal](/help/communities/blog-feature.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/journal

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Blogartikel |
| HINZUFÜGEN | Kommentare zu Mitgliedern in einem Blogartikel |
| AKTUALISIEREN | Blogartikel oder Kommentar eines Mitglieds wird bearbeitet |
| DELETE | Blogartikel oder Kommentar eines Mitglieds wird gelöscht |

**[QnA](/help/communities/working-with-qna.md)**
ComponentSocialEvent  `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt eine Frage zur Frage der Fragen |
| HINZUFÜGEN | Mitglied erstellt eine Antwort auf Fragen und Antworten |
| AKTUALISIEREN | Frage oder Antwort des Mitglieds wird bearbeitet |
| SELECT | Antwort des Mitglieds ist ausgewählt |
| UNSELECT | Die Antwort des Mitglieds ist deaktiviert. |
| DELETE | Frage oder Antwort des Mitglieds wird gelöscht |

**[Reviews](/help/communities/reviews.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/review

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Überprüfung |
| AKTUALISIEREN | Die Überprüfung des Mitglieds wird bearbeitet |
| DELETE | Überprüfung durch das Mitglied wird gestrichen |

**[Bewertung](/help/communities/rating.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally/rating

| **Verb** | **Beschreibung** |
|---|---|
| RATE HINZUFÜGEN | Der Inhalt des Mitglieds wurde bewertet. |
| RATE ENTFERNEN | der Inhalt des Mitglieds wurde heruntergestuft |

**[Voting](/help/communities/voting.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally/stimmte

| **Verb** | **Beschreibung** |
|---|---|
| ABSTIMMUNG HINZUFÜGEN | Der Inhalt des Mitglieds wurde abgestimmt |
| ABSTIMMUNG ENTFERNEN | Der Inhalt des Mitglieds wurde abgelehnt |

**Moderationsfähige**
KomponentenSocialEvent  `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschreibung** |
|---|---|
| DENY | Inhalt des Mitglieds wird verweigert |
| FLAG-AS-INAPPROPRIATE | Inhalt des Mitglieds wird markiert |
| UNFLAG-AS-INAPPROPRIATE | Inhalt des Mitglieds ist unmarkiert |
| AKZEPT | Der Inhalt des Mitglieds wird vom Moderator genehmigt |
| SCHLIESSEN | Mitglied schließt Kommentar zu Bearbeitungen und Antworten |
| ÖFFNEN | Mitglied öffnet Kommentar erneut |

### Benutzerdefinierte Komponentenereignisse {#custom-component-events}

Bei einer benutzerdefinierten Komponente wird ein SocialEvent instanziiert, um die Ereignisse der Komponente als `actions` aufzuzeichnen, die für ein `topic` auftreten.

Um die Auswertung zu unterstützen, muss das SocialEvent die Methode `getVerb()` überschreiben, damit für jedes `action` ein entsprechendes `verb` zurückgegeben wird. Das für eine Aktion zurückgegebene `verb` kann eine häufig verwendete (z. B. `POST`) oder für die Komponente spezialisierte (z. B. `ADD RATING`) sein. Es gibt eine *n-1*-Beziehung zwischen `actions` und `verbs`.

## Fehlerbehebung {#troubleshooting}

### Abzeichen werden nicht angezeigt {#badges-are-not-appearing}

Wenn Scoring- und Badging-Regeln auf den Inhalt der Website angewendet wurden, Abzeichen jedoch für keine Aktivität erwartet werden, stellen Sie sicher, dass Abzeichen für die Instanz dieser Komponente aktiviert wurden.

Siehe [Enable Badges for Component](#enable-badges-for-component).

### Scoring-Regel hat keine Auswirkung {#scoring-rule-has-no-effect}

Wenn Scoring- und Badging-Regeln auf den Inhalt der Website angewendet wurden und Abzeichen für einige Aktionen, aber nicht für andere zugewiesen werden, überprüfen Sie, ob die Badging-Regel die Scoring-Regeln, für die sie gilt, nicht eingeschränkt hat.

Siehe die `scoringRules`-Eigenschaft von [Badging Rules](#badging-rules).

### Groß-/Kleinschreibung {#case-sensitive-typo}

Bei den meisten Eigenschaften und Werten, insbesondere den Verben, wird zwischen Groß- und Kleinschreibung unterschieden. Verben müssen bei Verwendung in einer Scoring-Unterregel alle UPPERCASE sein.

Wenn die Funktion nicht wie erwartet funktioniert, stellen Sie sicher, dass die Daten korrekt eingegeben wurden.

## Schnelltest {#quick-test}

Mit der Website [Erste Schritte-Tutorial](/help/communities/getting-started.md) (Interagieren) können Sie schnell Scoring und Badging ausprobieren:

* Zugriff auf die CRXDE Lite auf der Autoreninstanz.
* Navigieren Sie zur Basisseite:

   * /content/sites/engage/en/jcr:content

* Fügen Sie die Eigenschaft badgingRules hinzu:

   * **Name**: `badgingRules`
   * **Typ**: `String`
   * Wählen Sie **Multi**
   * Wählen Sie **Hinzufügen**
   * Geben Sie `/libs/settings/community/badging/rules/forums-badging` ein
   * Wählen Sie nun eine der folgenden Optionen aus **+**
   * Geben Sie `/libs/settings/community/badging/rules/comments-badging` ein
   * Wählen Sie **OK** aus

* Fügen Sie die Eigenschaft scoringRules hinzu:

   * **Name**:  `scoringRules`
   * **Typ**: `String`
   * Wählen Sie **Multi**
   * Wählen Sie **Hinzufügen**
   * Geben Sie `/libs/settings/community/scoring/rules/forums-scoring` ein
   * Wählen Sie nun eine der folgenden Optionen aus **+**
   * Geben Sie `/libs/settings/community/scoring/rules/comments-scoring` ein
   * Wählen Sie **OK** aus

* Wählen Sie **Alle speichern** aus.

![test-scoring-badging](assets/test-scoring-badging.png)

Stellen Sie als Nächstes sicher, dass die Forum- und Kommentarkomponenten die Anzeige von Abzeichen zulassen:

* Wieder mit CRXDE Lite.
* Navigieren Sie zur Forumkomponente .

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Fügen Sie ggf. die boolesche Eigenschaft allowBadges hinzu und stellen Sie sicher, dass sie wahr ist.

   * **Name**:  `allowBadges`
   * **Typ**: `Boolean`
   * **Wert**: `true`

![test-forum-component](assets/test-forum-component.png)

Als Nächstes [republish](/help/communities/sites-console.md#publishing-the-site) die Community-Site.

Abschließend,

* Navigieren Sie zur Komponente in der Veröffentlichungsinstanz.
* Melden Sie sich als Community-Mitglied an (z. B. : weston.mccall@dodgit.com / password).
* Posten Sie ein neues Forumthema.
* Die Seite muss aktualisiert werden, damit der Badge angezeigt wird.

   * Melden Sie sich ab und melden Sie sich als anderes Community-Mitglied an (z. B.: aaron.mcdonald@mailinator.com/password).

* Wählen Sie das Forum aus.

Dies sollte dem Community-Mitglied ein Bronzesymbol mit seinem Forumsbeitrag vermitteln, da der erste Schwellenwert der Regel für Forumsabzeichen 1 beträgt.

![Bronzebadge](assets/bronzebadge.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Scoring- und Badges-Grundlagen](/help/communities/configure-scoring.md) für Entwickler.

Informationen zur erweiterten Scoring-Engine finden Sie unter [Erweiterte Scoring- und Badges](/help/communities/advanced.md).

Das konfigurierbare Leaderboard [component](/help/communities/enabling-leaderboard.md) und [function](/help/communities/functions.md#leaderboard-function) vereinfacht die Anzeige von Mitgliedern und deren Ergebnissen auf einer Community-Site.
