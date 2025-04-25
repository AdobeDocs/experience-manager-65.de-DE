---
title: Vergabe von Bewertungen und Abzeichen in Communities
description: Mit AEM Communities-Bewertungen und -Abzeichen können Sie Community-Mitglieder identifizieren und belohnen
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
tagskeywords: scoring, badging, badges, gamification
role: Admin
exl-id: 4aa857f7-d111-4548-8f03-f6d6c27acf51
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2856'
ht-degree: 3%

---

# Vergabe von Bewertungen und Abzeichen in Communities {#communities-scoring-and-badges}

## Überblick {#overview}

Die AEM Communities-Funktion für Scoring und Abzeichen bietet die Möglichkeit, Community-Mitglieder zu identifizieren und zu belohnen.

Die Hauptaspekte der Bewertung und Abzeichen sind:

* [Abzeichen zuweisen](#assign-and-revoke-badges) um die Rolle eines Mitglieds in der Community zu identifizieren.

* [Grundlegende Vergabe von Abzeichen](#enable-scoring) an Mitglieder zur Förderung ihrer Teilnahme (Menge der erstellten Inhalte).

* [Erweiterte Vergabe von Abzeichen](/help/communities/advanced.md) um Mitglieder als Experten zu identifizieren (Qualität der erstellten Inhalte).

**Hinweis** dass die Vergabe von Abzeichen [nicht standardmäßig aktiviert) ](/help/communities/implementing-scoring.md#main-pars-text-237875536).

>[!CAUTION]
>
>Die in CRXDE Lite sichtbare Implementierungsstruktur kann sich ändern, sobald die Benutzeroberfläche verfügbar wird.

## Zeichen {#badges}

Abzeichen werden unter dem Namen eines Mitglieds platziert, um entweder seine Rolle oder sein Ansehen in der Community anzugeben. Abzeichen können entweder als Bild oder als Name angezeigt werden. Wenn der Name als Bild angezeigt wird, wird er als Alternativtext für Barrierefreiheit eingefügt.

Standardmäßig befinden sich Badges im Repository unter:

* `/libs/settings/community/badging/images`

Wenn sie an einem anderen Speicherort gespeichert sind, sollten sie von jedem gelesen und zugänglich sein.

Bei UGC wird unterschieden, ob die Abzeichen gemäß den Regeln zugewiesen wurden oder erworben wurden. Derzeit werden zugewiesene Abzeichen als Text und Earned Badges als Bild angezeigt.

### Benutzeroberfläche für die Badge-Verwaltung {#badge-management-ui}

Mit der [Badges-Konsole](/help/communities/badges.md) von Communities können Sie benutzerdefinierte Abzeichen hinzufügen, die für ein Mitglied angezeigt werden können, wenn es verdient (verliehen) wurde oder wenn es eine bestimmte Rolle in der Community übernimmt (zugewiesen).

### Zugewiesene Abzeichen {#assigned-badges}

Rollenbasierte Abzeichen werden von einem Administrator den Community-Mitgliedern auf Grundlage ihrer Rolle in der Community zugewiesen.

Zugewiesene (und vergebene) Abzeichen werden im ausgewählten ([) gespeichert ](/help/communities/srp.md) sind nicht direkt zugänglich. Bis eine grafische Benutzeroberfläche verfügbar ist, können rollenbasierte Abzeichen nur über Code oder cURL zugewiesen werden. cURL-Anweisungen finden Sie im Abschnitt mit dem Titel [Abzeichen zuweisen und widerrufen](#assign-and-revoke-badges).

In der Version sind drei rollenbasierte Abzeichen enthalten:

* **Moderator**
  `/libs/settings/community/badging/images/moderator/jcr:content/moderator.png`

* **Gruppenleiter**
  `/libs/settings/community/badging/images/group-manager/jcr:content/group-manager.png`

* **privilegiertes Mitglied**
  `/libs/settings/community/badging/images/privileged-member/jcr:content/privileged-member.png`

  ![assigned-badges](assets/assigned-badges.png)

### Erhaltene Abzeichen {#awarded-badges}

Belohnungsbasierte Abzeichen werden vom Scoring-Service an Community-Mitglieder auf der Grundlage von Regeln vergeben, die auf ihre Aktivität in der Community angewendet werden.

Damit Abzeichen als Belohnung für Aktivitäten angezeigt werden, müssen zwei Dinge passieren:

* Das Badging muss [aktiviert](#enableforcomponent) für die Funktionskomponente sein.
* Auf die Seite (oder den Vorgänger[ auf der sich die Komponente befindet](#applytopage) müssen Bewertungs- und Badging-Regeln angewendet werden.

In der Version sind drei Belohnungs-Abzeichen enthalten:

* **Gold**
  `/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

* **silber**
  `/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

* **Bronze**
  `/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

  ![[!BADGE Award-S]](assets/awarded-badges.png)

>[!NOTE]
>
>Scoring-Regeln können so konfiguriert werden, dass negative Punkte für als unangemessen gekennzeichnete Posts zugewiesen werden, was sich auf den Score-Wert auswirkt. Sobald ein Abzeichen erworben wurde, wird es jedoch aufgrund der Reduzierung der Scoring-Punkte oder von Änderungen der Scoring-Regeln nicht automatisch entfernt.
>
>Erhaltene Abzeichen können auf die gleiche Weise wie zugewiesene Abzeichen widerrufen werden. Siehe den Abschnitt [Zuweisen und Widerrufen ](#assign-and-revoke-badges) Abzeichen“. Zukünftige Verbesserungen werden eine Benutzeroberfläche zur Verwaltung der Abzeichen von Mitgliedern umfassen.

### Benutzerdefinierte Abzeichen {#custom-badges}

Benutzerdefinierte Badges können über die [Badges-Konsole“ installiert ](/help/communities/badges.md) oder in Badging-Regeln zugewiesen werden.

Bei der Installation über die Konsole „Badges“ werden benutzerdefinierte Badges automatisch in die Veröffentlichungsumgebung repliziert.

## Scoring aktivieren {#enable-scoring}

Die Bewertung ist standardmäßig nicht aktiviert. Die grundlegenden Schritte zum Einrichten und Ermöglichen der Bewertung und Vergabe von Abzeichen sind:

* Identifizieren Sie Regeln für das Sammeln von Punkten [Scoring-Regeln](#scoring-rules).
* Weisen Sie den Punkten, die pro Bewertungsregeln gesammelt wurden, [Badges](#badges) ([Badging-Regeln](#badging-rules)) zu.

* [Wenden Sie die Bewertungs- und Badging-Regeln auf eine Community-Site an](#apply-rules-to-content).
* [Aktivieren Sie das Badging für Community-Funktionen](#enable-badges-for-component).

Siehe den Abschnitt [Schnelltest](#quick-test), um die Bewertung für eine Community-Site mithilfe der standardmäßigen Scoring- und Badging-Regeln für Foren und Kommentare zu aktivieren.

### Regeln auf Inhalte anwenden {#apply-rules-to-content}

Um die Bewertung und die Abzeichen zu aktivieren, fügen Sie die Eigenschaften `scoringRules` und `badgingRules` zu einem beliebigen Knoten in der Inhaltsstruktur für die Site hinzu.

Wenn die Site bereits veröffentlicht ist, veröffentlichen Sie die Site erneut, nachdem Sie alle Regeln angewendet und Komponenten aktiviert haben.

Für eine Badging-fähige Komponente gelten die Regeln für den aktuellen Knoten oder dessen Vorgänger.

Wenn der Knoten vom Typ `cq:Page` ist (empfohlen), fügen Sie mithilfe von CRXDE|Lite die Eigenschaften zu seinem `jcr:content` Knoten hinzu.

| **Eigenschaft** | **Typ** | **Beschreibung** |
|---|---|---|
| BadgingRules | Zeichenfolge | Eine Array-Liste von [Badging-Regeln](#badging-rules) |
| ScoringRules | Zeichenfolge | Eine Array-Liste [Bewertungsregeln](#scoring-rules) |

>[!NOTE]
>
>Wenn eine Bewertungsregel keine Auswirkungen auf die Vergabe von Abzeichen zu haben scheint, stellen Sie sicher, dass die Bewertungsregel nicht durch die Eigenschaft „scoringRules“ der Badging-Regel blockiert wurde. Siehe Abschnitt mit dem Titel [Badging-Regeln](#badging-rules).

### Aktivieren von Abzeichen für Komponenten {#enable-badges-for-component}

Die Scoring- und Badging-Regeln sind nur für Instanzen von Komponenten wirksam, die das Badging aktiviert haben, indem die Komponentenkonfiguration im [Authoring-Modus) ](/help/communities/author-communities.md) wird.

Eine boolesche Eigenschaft `allowBadges` aktiviert/deaktiviert die Anzeige von Badges für eine Komponenteninstanz. Sie kann im [Dialogfeld „Komponente bearbeiten](/help/communities/author-communities.md) für Forum-, QnA- und Kommentar-Komponenten über ein Kontrollkästchen mit der Bezeichnung **Badges anzeigen** konfiguriert werden.

#### Beispiel : allowBadges für die Instanz der Forumkomponente {#example-allowbadges-for-forum-component-instance}

![enable-badges-component](assets/enable-badges-component.png)

>[!NOTE]
>
>Jede Komponente kann überlagert werden, um Abzeichen anzuzeigen, wobei der HBS-Code verwendet wird, der in Foren, QnA und Kommentaren als Beispiel zu finden ist.

## Bewertungsregeln {#scoring-rules}

Bewertungsregeln sind die Grundlage für die Bewertung von Abzeichen.

Jede Bewertungsregel ist eine Liste aus einer oder mehreren Unterregeln. Auf den Inhalt der Community-Site werden Bewertungsregeln angewendet, um die Regeln zu identifizieren, die bei aktivierten Abzeichen anzuwenden sind.

Bewertungsregeln werden vererbt, sind aber nicht additiv. Zum Beispiel:

* Wenn Seite2 die Bewertungsregel2 und ihre Vorgängerseite1 die Bewertungsregel1 enthält.
* Eine Aktion in einer „page2“-Komponente ruft „rule1“ und „rule2“ auf.
* Wenn beide Regeln anwendbare Unterregeln für dieselbe `topic/verb` enthalten:

   * Nur die Unterregel aus Regel2 wirkt sich auf die Bewertung aus.
   * Die Punktzahlen aus beiden Unterregeln werden nicht hinzugefügt.

Wenn es mehr als eine Bewertungsregel gibt, werden die Bewertungen für jede Regel separat verwaltet.

Scoring-Regeln sind Knoten des Typs `cq:Page` mit Eigenschaften auf ihrem `jcr:content` Knoten, die die Liste der Unterregeln angeben, die sie definieren.

Scores werden in SRP gespeichert.

>[!NOTE]
>
>Best Practice: Benennen Sie jede Bewertungsregel eindeutig.
>
>Bewertungsregelnamen sollten global eindeutig sein und nicht mit demselben Namen enden.
>
>Ein Beispiel dafür *was* tun:
>
>/libs/settings/community/scoring/rules/site1/forums-scoring
>/libs/settings/community/scoring/rules/site2/forums-scoring

### Unterregeln für die Bewertung {#scoring-sub-rules}

Die Scoring-Unterregeln enthalten die Eigenschaften mit Details zu den Werten für die Teilnahme an der Community.

Jede Scoring-Unterregel identifiziert:

* Welche Aktivitäten werden verfolgt?
* Welche spezielle Funktion der Gemeinschaft ist betroffen?
* Wie viele Punkte werden vergeben?

Standardmäßig werden Punkte an das Mitglied vergeben, das eine Aktion durchführt, es sei denn, die Unterregel gibt den Eigentümer des Inhalts als Empfänger der Punkte an ( `forOwner`).

Jede Unterregel kann in einer oder mehreren Bewertungsregeln enthalten sein.

Der Name der Unterregel folgt normalerweise dem Muster der Verwendung eines *Subjekt*, *Objekt* und *Verb*. Zum Beispiel:

* member-comment-create
* member-receive-vote

Unterregeln sind Knoten des Typs `cq:Page` mit Eigenschaften auf ihrem `jcr:content`Knoten, die die [Verben und Themen) ](#topics-and-verbs).

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Typ</th>
   <th> Beschreibung des Werts</th>
  </tr>
  <tr>
   <td><i><code>VERB</code></i></td>
   <td>Long</td>
   <td>
    <ul>
     <li>Erforderlich; das Verb entspricht einer Ereignisaktion</li>
     <li>Es muss mindestens eine Verbeigenschaft vorhanden sein</li>
     <li>Das Verb muss in Großbuchstaben geschrieben werden</li>
     <li>Es kann mehrere Verbeigenschaften, aber keine Duplikate geben</li>
     <li>Der Wert ist der Score, der für dieses Ereignis angewendet werden soll</li>
     <li>Der Wert kann positiv oder negativ sein</li>
     <li>Eine Liste der in der Version unterstützten Verben finden Sie im Abschnitt <a href="#topics-and-verbs">Themen und </a>"</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>topics</code></td>
   <td>Zeichenfolge</td>
   <td>
    <ul>
     <li>Optional; beschränkt Unterregel auf Community-Komponenten, die durch Ereignisthemen identifiziert wurden</li>
     <li>Wenn angegeben : Der Wert ist eine mehrwertige Zeichenfolge von Ereignisthemen</li>
     <li>Eine Liste der Themen der Version finden Sie im Abschnitt <a href="#topics-and-verbs">Themen und Verben</a></li>
     <li>Die Standardeinstellung gilt für alle Themen, die mit den Verben verknüpft sind</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>forOwner</code></td>
   <td>Boolesch</td>
   <td>
    <ul>
     <li>Optional; nicht relevant, wenn ein Mitglied Inhalte bearbeitet, deren Eigentümer es ist</li>
     <li>Wenn „true“, wird die Bewertung auf den Eigentümer des Inhalts angewendet, für den eine Aktion durchgeführt wird</li>
     <li>Falls „false“, Bewertung auf Mitglied anwenden, das eine Aktion durchführt</li>
     <li>Standardwert ist „false“</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>scoringType</code></td>
   <td>Zeichenfolge</td>
   <td>
    <ul>
     <li>Optional; identifiziert die Scoring-Engine</li>
     <li>Wenn „Einfach“, spezifiziert das Scoring-Modul basierend auf der Menge
      <ul>
       <li>In der Version enthalten</li>
      </ul> </li>
     <li>Wenn „Erweitert“, spezifiziert die Scoring-Engine auf der Grundlage von Qualität und Menge
      <ul>
       <li>Erfordert ein <a href="/help/communities/advanced.md">zusätzliches Paket</a></li>
      </ul> </li>
     <li>Der Standardwert lautet „Standard“</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Eingeschlossene Bewertungsregeln und Unterregeln {#included-scoring-rules-and-sub-rules}

In dieser Version sind zwei Bewertungsregeln für die Funktion [Forum](/help/communities/functions.md#forum-function) enthalten (jeweils eine für die Komponente Forum und Kommentare der Funktion Forum ):

1. /libs/settings/community/scoring/rules/comments-scoring

   * subRules[] =
/libs/settings/community/scoring/rules/sub-rules/member-comment-create
/libs/settings/community/scoring/rules/sub-rules/member-receive-vote
/libs/settings/community/scoring/rules/sub-rules/member-Give-vote
/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

1. /libs/settings/community/scoring/rules/forums-scoring

   * subRules[] =
/libs/settings/community/scoring/rules/sub-rules/member-forum-create
/libs/settings/community/scoring/rules/sub-rules/member-receive-vote
/libs/settings/community/scoring/rules/sub-rules/member-Give-vote
/libs/settings/community/scoring/rules/sub-rules/member-is-moderated

**Anmerkungen:**

* Sowohl `rules`- als auch `sub-rules`-Knoten sind vom Typ cq:Page.

* `subRules` ist ein Attribut vom Typ Zeichenfolge[] auf dem `jcr:content` Knoten der Regel.

* `sub-rules` können unter verschiedenen Bewertungsregeln aufgeteilt werden.
* `rules` sollten sich an einem Repository-Speicherort mit Leseberechtigung für alle befinden.

   * Regelnamen müssen unabhängig vom Speicherort eindeutig sein.

### Aktivieren benutzerdefinierter Bewertungsregeln {#activating-custom-scoring-rules}

Alle Änderungen oder Ergänzungen an Bewertungsregeln oder Unterregeln, die in der Autorenumgebung vorgenommen wurden, müssen bei der Veröffentlichung installiert werden.

## Badging-Regeln {#badging-rules}

Badging-Regeln verknüpfen Bewertungsregeln mit Abzeichen, indem Folgendes angegeben wird:

* Bewertungsregel
* Punktzahl, die für die Vergabe eines bestimmten Abzeichens erforderlich ist

Badging-Regeln sind Knoten vom Typ `cq:Page` mit Eigenschaften auf ihrem `jcr:content` Knoten, die Bewertungsregeln mit Bewertungen und Abzeichen korrelieren.

Die Badging-Regeln bestehen aus einer obligatorischen `thresholds`-Eigenschaft, die eine geordnete Liste von Werten ist, die Abzeichen zugeordnet sind. Die Punktzahlen müssen in aufsteigender Reihenfolge sortiert werden. Zum Beispiel:

* `1|/libs/settings/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Ein Bronze-Abzeichen wird für den Gewinn eines Punktes vergeben.

* `60|/libs/settings/community/badging/images/silver-badge/jcr:content/silver.png`

   * Ein silbernes Abzeichen wird verliehen, wenn 60 Punkte gesammelt wurden.

* `80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png`

   * Ein Gold-Abzeichen wird verliehen, wenn 80 Punkte gesammelt wurden.

Badging-Regeln sind mit Bewertungsregeln gepaart, die bestimmen, wie Punkte gesammelt werden. Siehe den Abschnitt [Anwenden von Regeln auf Inhalte](#apply-rules-to-content).

Die `scoringRules` Eigenschaft einer Badging-Regel beschränkt einfach, welche Bewertungsregeln mit dieser bestimmten Badging-Regel gepaart werden können.

>[!NOTE]
>
>Best Practice : Erstellen Sie für jede AEM-Site eindeutige Abzeichenbilder.

![badging-rule-configuration](assets/badging-rule-configuration.png)

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Typ</th>
   <th>Beschreibung des Werts</th>
  </tr>
  <tr>
   <td>Schwellenwerte</td>
   <td>Zeichenfolge</td>
   <td><em>(erforderlich)</em> Eine Zeichenfolge mit mehreren Werten in der Form „number|path“
    <ul>
     <li>Zahl = Score</li>
     <li>| = das vertikale Liniendiagramm (U+007C)</li>
     <li>path = vollständiger Pfad zur Badge-Bildressource</li>
    </ul> Die Zeichenfolgen müssen so sortiert werden, dass die Zahlen im Wert ansteigen und zwischen der Zahl und dem Pfad kein Leerzeichen angezeigt werden sollte.<br /> Beispieleintrag :<br /> <code>80|/libs/settings/community/badging/images/gold-badge/jcr:content/gold.png</code></td>
  </tr>
  <tr>
   <td>badgingType</td>
   <td>Zeichenfolge</td>
   <td><em>(optional)</em> Gibt die Scoring-Engine entweder als „Standard“ oder „Erweitert“ an. Wenn Sie die erweiterte Scoring-Engine wünschen, finden Sie weitere Informationen unter <a href="/help/communities/advanced.md">Erweiterte Scoring-Funktionen und Abzeichen</a>. Der Standardwert lautet „basic“.</td>
  </tr>
  <tr>
   <td>ScoringRules</td>
   <td>Zeichenfolge</td>
   <td>(<em>optional</em>) Eine Zeichenfolge mit mehreren Werten, um die Badging-Regel auf die von den Bewertungsregeln identifizierten Bewertungsereignisse zu beschränken</td>
  </tr>
 </tbody>
</table>

### Enthaltene Badging-Regeln {#included-badging-rules}

In dieser Version sind zwei Badging-Regeln enthalten, die den [Bewertungsregeln für Foren und Kommentare](#includedscoringrules) entsprechen.

* `/libs/settings/community/badging/rules/comments-badging`

* `/libs/settings/community/badging/rules/forums-badging`

**Anmerkungen:**

* `rules` Knoten sind vom Typ cq:Page.
* `rules` sollten sich an einem Repository-Speicherort mit Leseberechtigung für alle befinden.

   * Regelnamen müssen unabhängig vom Speicherort eindeutig sein.

### Aktivieren benutzerdefinierter Badging-Regeln {#activating-custom-badging-rules}

Alle Änderungen oder Ergänzungen an Badging-Regeln oder Bildern, die in der Autorenumgebung vorgenommen wurden, müssen bei der Veröffentlichung installiert werden.

## Zuteilen und Entziehen von Abzeichen {#assign-and-revoke-badges}

Abzeichen können Mitgliedern entweder über die [Mitgliederkonsole“ oder ](/help/communities/members.md#badges-tab) cURL-Befehlen zugewiesen werden.

Die folgenden cURL-Befehle zeigen, was für eine HTTP-Anfrage zum Zuweisen und Widerrufen von Badges erforderlich ist. Das Grundformat lautet:

cURL -i -X POST -H *Header* -u *signin* -F *operation* -F *badge* *member-profile-url*

*header* = „Accept:Application/json“
Benutzerdefinierte Kopfzeile, die an den Server übergeben wird (erforderlich)

*signin* = Administrator-ID:password
Beispiel: admin:admin

*operation* = &quot;:operation=social:assignBadge“ ODER &quot;:operation=social:deleteBadge“

*badge* = „badgeContentPath=*badge-image-file*&quot;

*badge-image-file* = Speicherort der Badge-Grafikdatei im Repository
Beispiel: /libs/settings/community/badging/images/moderator/jcr:content/moderator.png

*member-profile-url* = Endpunkt für das Profil des Nutzers bei der Veröffentlichung
Beispiel: https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>Die *member-profile-url*:
>
>* Kann auf eine Autoreninstanz verweisen, wenn der [Tunneldienst](/help/communities/users.md#tunnel-service) aktiviert ist.
>* Kann ein unklarer, zufälliger Name sein - siehe [Sicherheitscheckliste](/help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) in Bezug auf autorisierbare ID.

### Beispiele: {#examples}

#### Moderator-Badge zuweisen {#assign-a-moderator-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/libs/settings/community/badging/images/moderator/jcr:content/moderator.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

#### Widerrufen eines zugewiesenen silbernen Abzeichens {#revoke-an-assigned-silver-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:deleteBadge" -F "badgeContentPath=/libs/settings/community/badging/images/silver/jcr:content/silver.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

>[!NOTE]
>
>Die Verwendung von cURL zum Zuweisen und Widerrufen von Abzeichen funktioniert für jedes Abzeichenbild, aber wenn sie zugewiesen anstelle von erworben werden, werden sie als zugewiesene Abzeichen gekennzeichnet und entsprechend gehandhabt.

## Bewertung und Abzeichen für benutzerdefinierte Komponenten {#scoring-and-badges-for-custom-components}

Bewertungs- und Badging-Regeln können für benutzerdefinierte Komponenten erstellt werden, indem die für die Komponente erstellten Ereignisthemen mit Verben verknüpft werden.

## Themen und Verben {#topics-and-verbs}

Wenn Mitglieder mit Communities-Funktionen interagieren, werden Ereignisse gesendet, die asynchrone Listener zum Trigger bringen können, z. B. Benachrichtigungen und Bewertung.

Die SocialEvent-Instanz einer Komponente zeichnet die Ereignisse als `actions` auf, die bei einem `topic` auftreten. SocialEvent enthält eine Methode zum Zurückgeben eines der Aktion zugeordneten `verb`. Es besteht eine *n-1*-Beziehung zwischen `actions` und `verbs`.

Für die bereitgestellten Communitys-Komponenten beschreiben die folgenden Tabellen die `verbs`, die für jede `topic` definiert wurden, die in (Scoring[Unterregeln) ](#scoring-sub-rules) werden kann.

>[!NOTE]
>
>Die neue boolesche Eigenschaft `allowBadges` aktiviert/deaktiviert die Anzeige von Badges für eine Komponenteninstanz. Sie kann in aktualisierten Dialogfeldern für [Komponentenbearbeitung](/help/communities/author-communities.md) über ein Kontrollkästchen mit der Bezeichnung **Abzeichen anzeigen** konfiguriert werden.

**[Kalenderkomponente](/help/communities/calendar.md)**
SocialEvent `topic`= com/adobe/cq/social/calendar

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt ein Kalenderereignis |
| HINZUFÜGEN | Mitgliederkommentare zu einem Kalenderereignis |
| AKTUALISIEREN | Kalenderereignis oder -kommentar des Nutzers wird bearbeitet |
| LÖSCHEN | Kalenderereignis oder Kommentar des Nutzers wird gelöscht |

**[Komponente „Kommentare](/help/communities/comments.md)**
SocialEvent `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Kommentar |
| HINZUFÜGEN | Antworten des Mitglieds auf den Kommentar |
| AKTUALISIEREN | Kommentar des Nutzers wird bearbeitet |
| LÖSCHEN | Kommentar des Nutzers wird gelöscht |

**[Dateibibliothekskomponente](/help/communities/file-library.md)**
SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Ordner |
| ANHÄNGEN | Mitglied lädt eine Datei hoch |
| AKTUALISIEREN | Mitglied aktualisiert Ordner oder Dateien |
| LÖSCHEN | Mitglied löscht einen Ordner oder eine Datei |

**[Forenkomponente](/help/communities/forum.md)**
SocialEvent `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Forumsthema |
| HINZUFÜGEN | Antworten der Mitglieder auf das Forumsthema |
| AKTUALISIEREN | Das Forumsthema oder die Antwort des Mitglieds wurde bearbeitet |
| LÖSCHEN | Das Forumsthema oder die Antwort des Mitglieds wird gelöscht |

**[Journalkomponente](/help/communities/blog-feature.md)**
SocialEvent `topic`= com/adobe/cq/social/journal

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Blog-Artikel |
| HINZUFÜGEN | Mitgliederkommentare zu einem Blog-Artikel |
| AKTUALISIEREN | Artikel oder Kommentar des Nutzers im Blog bearbeitet |
| LÖSCHEN | Blog-Artikel oder Kommentar des Nutzers wird gelöscht |

**[QnA-Komponente](/help/communities/working-with-qna.md)**
SocialEvent `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschreibung** |
|---|---|
| POST | Abonnent erstellt eine QnA-Frage |
| HINZUFÜGEN | member erstellt eine QnA-Antwort |
| AKTUALISIEREN | Eine Frage oder Antwort eines Mitglieds wird bearbeitet |
| AUSWÄHLEN | Antwort des Nutzers ist ausgewählt |
| UNSELECT | Die Antwort des Nutzers wurde deaktiviert |
| LÖSCHEN | Eine Frage oder Antwort eines Mitglieds wird gelöscht |

**[Reviews-Komponente](/help/communities/reviews.md)**
SocialEvent `topic`= com/adobe/cq/social/review

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Überprüfung |
| AKTUALISIEREN | Mitgliederüberprüfung wird bearbeitet |
| LÖSCHEN | Mitgliederbewertung wird gelöscht |

**[Bewertungskomponente](/help/communities/rating.md)**
SocialEvent `topic`= com/adobe/cq/social/tally/rating

| **Verb** | **Beschreibung** |
|---|---|
| BEWERTUNG HINZUFÜGEN | Der Inhalt des Abonnenten wurde aktualisiert |
| WERTUNG ENTFERNEN | Der Inhalt des Abonnenten wurde als unzureichend bewertet |

**[Abstimmungskomponente](/help/communities/voting.md)**
SocialEvent `topic`= com/adobe/cq/social/tally/vote

| **Verb** | **Beschreibung** |
|---|---|
| ABSTIMMUNG HINZUFÜGEN | Der Inhalt des Mitglieds wurde zur Abstimmung gestellt |
| ABSTIMMUNG ENTFERNEN | Der Inhalt des Mitglieds wurde abgelehnt |

**Moderationsfähige Komponenten**
SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschreibung** |
|---|---|
| ABLEHNEN | Der Inhalt des Nutzers wird abgelehnt |
| ALS UNGEEIGNET MARKIEREN | Der Inhalt des Nutzers ist gekennzeichnet |
| UNFLAG-AS-INPROPRIATE | Der Inhalt des Nutzers ist nicht gekennzeichnet |
| AKZEPTIEREN | Der Inhalt des Nutzers wird vom Moderator genehmigt |
| SCHLIESSEN | Mitglied schließt Kommentar zu Bearbeitungen und Antworten |
| ÖFFNEN | Mitglied öffnet Kommentar erneut |

### Benutzerdefinierte Komponentenereignisse {#custom-component-events}

Bei einer benutzerdefinierten Komponente wird ein SocialEvent instanziiert, um die Ereignisse der Komponente als `actions` aufzuzeichnen, die bei einem `topic` auftreten.

Um die Bewertung zu unterstützen, muss SocialEvent die Methode `getVerb()` überschreiben, damit für jede `action` ein entsprechender `verb` zurückgegeben wird. Die für eine Aktion zurückgegebene `verb` kann eine häufig verwendete (z. B. `POST`) oder eine für die Komponente spezialisierte (z. B. `ADD RATING`) sein. Es besteht eine *n-1*-Beziehung zwischen `actions` und `verbs`.

## Fehlerbehebung {#troubleshooting}

### Abzeichen werden nicht angezeigt {#badges-are-not-appearing}

Wenn Bewertungs- und Badging-Regeln auf den Inhalt der Website angewendet wurden, für keine Aktivität jedoch Badges vergeben werden, stellen Sie sicher, dass die Badges für die Instanz dieser Komponente aktiviert wurden.

Siehe [Aktivieren von Abzeichen für Komponente](#enable-badges-for-component).

### Bewertungsregel hat keine Wirkung {#scoring-rule-has-no-effect}

Wenn Bewertungs- und Badging-Regeln auf den Inhalt der Website angewendet wurden und für einige Aktionen Abzeichen vergeben werden, aber nicht für andere, überprüfen Sie, ob die Badging-Regel die Bewertungsregeln, für die sie gilt, nicht eingeschränkt hat.

Siehe die `scoringRules`-Eigenschaft von [Badging-Regeln](#badging-rules).

### Schreibweise unter Berücksichtigung der Groß-/Kleinschreibung {#case-sensitive-typo}

Bei den meisten Eigenschaften und Werten, insbesondere bei den Verben, wird zwischen Groß- und Kleinschreibung unterschieden. Verben müssen in einer Scoring-Unterregel vollständig GROSSGESCHRIEBEN sein.

Wenn die Funktion nicht erwartungsgemäß funktioniert, stellen Sie sicher, dass die Daten korrekt eingegeben wurden.

## Schnelltest {#quick-test}

Sie können schnell Scoring und Badging ausprobieren, indem Sie die Seite [Erste Schritte-Tutorial](/help/communities/getting-started.md) (Engage) verwenden:

* Zugriff auf CRXDE Lite in der Autoreninstanz.
* Navigieren Sie zur Basisseite:

   * /content/sites/engage/en/jcr:content

* Fügen Sie die badgingRules-Eigenschaft hinzu:

   * **Name**: `badgingRules`
   * **Typ**: `String`
   * Wählen Sie **Multi**
   * Wählen Sie **Hinzufügen** aus
   * Geben Sie `/libs/settings/community/badging/rules/forums-badging` ein
   * **+** auswählen
   * Geben Sie `/libs/settings/community/badging/rules/comments-badging` ein
   * Wählen Sie **OK** aus.

* Fügen Sie die ScoringRules-Eigenschaft hinzu:

   * **Name**: `scoringRules`
   * **Typ**: `String`
   * Wählen Sie **Multi**
   * Wählen Sie **Hinzufügen** aus
   * Geben Sie `/libs/settings/community/scoring/rules/forums-scoring` ein
   * **+** auswählen
   * Geben Sie `/libs/settings/community/scoring/rules/comments-scoring` ein
   * Wählen Sie **OK** aus.

* Klicken Sie auf **Alle speichern**.

![test-scoring-badging](assets/test-scoring-badging.png)

Stellen Sie als Nächstes sicher, dass die Komponenten Forum und Kommentare die Anzeige von Abzeichen zulassen:

* Erneut mit CRXDE Lite.
* Navigieren Sie zur Forenkomponente

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Fügen Sie bei Bedarf die boolesche Eigenschaft allowBadges hinzu und stellen Sie sicher, dass sie wahr ist.

   * **Name**: `allowBadges`
   * **Typ**: `Boolean`
   * **Wert**: `true`

![test-forum-component](assets/test-forum-component.png)

Veröffentlichen [ als Nächstes ](/help/communities/sites-console.md#publishing-the-site) Community-Site erneut.

Schließlich

* Navigieren Sie zur Komponente in der Veröffentlichungsinstanz.
* Melden Sie sich als Community-Mitglied an (z. B. weston.mccall@dodgit.com / password).
* Posten eines neuen Forumsthemas.
* Die Seite muss aktualisiert werden, damit das Abzeichen angezeigt wird.

   * Melden Sie sich ab und melden Sie sich als anderes Community-Mitglied an (z. B.: aaron.mcdonald@mailinator.com/password).

* Wählen Sie das Forum aus.

Dadurch sollte das Community-Mitglied über ein Bronze-Abzeichen verfügen, das mit seinem Forumsbeitrag sichtbar ist, da der erste Schwellenwert der ersten Foren-Badging-Regel ein Score von 1 ist.

![Bronzebadge](assets/bronzebadge.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Grundlagen zu Bewertungen und Abzeichen](/help/communities/configure-scoring.md) für Entwickler.

Weitere Informationen zur erweiterten Scoring-Engine finden Sie unter [Erweiterte Scoring und Abzeichen](/help/communities/advanced.md).

Die konfigurierbare Leaderboard[Komponente](/help/communities/enabling-leaderboard.md) und [Funktion](/help/communities/functions.md#leaderboard-function) vereinfacht die Anzeige von Mitgliedern und deren Bewertungen auf einer Community-Site.
