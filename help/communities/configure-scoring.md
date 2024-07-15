---
title: Grundlagen zu Scoring und Abzeichen
description: Erfahren Sie, wie mit der Funktion für die Bewertung und Abzeichen in Adobe Experience Manager Communities Community-Mitglieder identifiziert und belohnt werden.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 470a382a-2aa7-449e-bf48-b5a804c5b114
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# Grundlagen zu Scoring und Abzeichen {#scoring-and-badges-essentials}

Mit der AEM Communities-Scoring- und Badges-Funktion werden Community-Mitglieder identifiziert und belohnt.

Die Details zur Einrichtung der Funktion finden Sie unter

* [Communities-Scoring und -Abzeichen](/help/communities/implementing-scoring.md)

Diese Seite enthält zusätzliche technische Details:

* Anzeigen eines Zeichens](#displaying-badges) als Bild oder Text in [
* Aktivieren der umfangreichen [Debug-Protokollierung](#debug-log-for-scoring-and-badging)
* Zugriff auf UGC](#ugc-for-scoring-and-badging) im Zusammenhang mit Scoring und Badging durch [

>[!CAUTION]
>
>Die in CRXDE Lite sichtbare Implementierungsstruktur kann sich ändern.

## Anzeigen von Abzeichen {#displaying-badges}

Ob ein Badge als Text oder Bild angezeigt wird, wird auf der Clientseite in der HBS-Vorlage gesteuert.

Suchen Sie beispielsweise in `/libs/social/forum/components/hbs/topic/list-item.hbs` nach `this.isAssigned`:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

Wenn &quot;true&quot;, zeigt `isAssigned` an, dass das Zeichen für eine Rolle zugewiesen wurde und das Zeichen als Text angezeigt werden sollte.

Wenn &quot;false&quot;, zeigt `isAssigned` an, dass der Badge für einen Gewinn zuerkannt wurde und der Badge als Bild angezeigt werden sollte.

Alle Änderungen an diesem Verhalten sollten in einem benutzerdefinierten Skript vorgenommen werden (entweder Überschreiben oder Überlagerung). Siehe [Clientseitige Anpassung](/help/communities/client-customize.md).

## Debug-Protokoll für Scoring und Badging {#debug-log-for-scoring-and-badging}

Um Scoring und Badging zu debuggen, kann eine benutzerdefinierte Protokolldatei eingerichtet werden. Der Inhalt dieser Protokolldatei kann dann dem Support zur Verfügung gestellt werden, wenn Probleme mit der Funktion auftreten.

Detaillierte Anweisungen finden Sie unter [Benutzerdefinierte Protokolldatei erstellen](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

So richten Sie schnell eine Slinglog-Datei ein:

1. Zugriff auf die **Adobe Experience Manager Web Console Log Support**, z. B.

   * https://localhost:4502/system/console/slinglog

1. Wählen Sie **Neuen Logger hinzufügen** aus.

   1. Wählen Sie `DEBUG` für **Protokollebene** aus

   1. Geben Sie einen Namen für **Protokolldatei** ein, beispielsweise

      * logs/scoring-debug.log

   1. Geben Sie zwei **Logger** (class)-Einträge ein (mit dem Symbol `+` ).

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`

   1. Wählen Sie **Speichern** aus

![debug-scoring-log](assets/debug-scoring-log.png)

So zeigen Sie Protokolleinträge an:

* Über die Web-Konsole

   * Unter dem Menü **Status**
   * Wählen Sie **Protokolldateien**
   * Suchen Sie nach dem Namen Ihrer Protokolldatei, z. B. `scoring-debug`.

* Auf der lokalen Festplatte des Servers

   * Die Protokolldatei befindet sich unter &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log

   * Zum Beispiel: `.../crx-quickstart/logs/scoring-debug.log`

![scoring-log](assets/scoring-log.png)

## UGC für Scoring und Badging {#ugc-for-scoring-and-badging}

Es ist möglich, die UGC im Zusammenhang mit Scoring und Badging anzuzeigen, wenn das ausgewählte SRP entweder JSRP oder MSRP, aber nicht ASRP ist. (Wenn Sie diese Begriffe nicht kennen, finden Sie weitere Informationen unter [Community-Inhaltsspeicherung](/help/communities/working-with-srp.md) und [Übersicht über den Speicher-Ressourcenanbieter](/help/communities/srp.md).)

Die Beschreibungen für den Zugriff auf Scoring- und Badging-Daten verwenden JSRP, da der Zugriff auf die UGC über [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) leicht möglich ist.

**JSRP für Autor**: Beim Experimentieren in der Autorenumgebung wird UGC angezeigt, der nur in der Autorenumgebung sichtbar ist.

**JSRP bei Veröffentlichung**: Ebenso ist es beim Testen in der Veröffentlichungsumgebung erforderlich, auf CRXDE Lite mit Administratorrechten auf einer Veröffentlichungsinstanz zuzugreifen. Wenn die Veröffentlichungsinstanz im [Produktionsmodus](/help/sites-administering/production-ready.md) ausgeführt wird (Ausführungsmodus nosamplecontent), muss CRXDE Lite](/help/sites-administering/enabling-crxde-lite.md) aktiviert werden.[

Der Basisspeicherort von UGC auf JSRP ist `/content/usergenerated/asi/jcr/`.

### Scoring- und Badging-APIs {#scoring-and-badging-apis}

Die folgenden APIs stehen zur Verwendung bereit:

* [com.adobe.cq.social.scoring.api in 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de)
* [com.adobe.cq.social.badging.api in 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de)

Die neuesten Javadocs für das installierte Feature Pack stehen Entwicklern aus dem Adobe-Repository zur Verfügung. Siehe [Verwenden von Maven für Communities: Javadocs](/help/communities/maven.md#javadocs).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

### Beispieleinrichtung {#example-setup}

Die Screenshots von Repository-Daten stammen aus der Einrichtung von Scoring und Badging für ein Forum auf zwei verschiedenen AEM Sites :

1. Eine AEM Site *mit* einer eindeutigen ID (Community-Site, die mithilfe des Assistenten erstellt wurde) :

   * Verwenden der Site &quot;Erste Schritte - Tutorial&quot;(Interaktion), die während des [Erste Schritte-Tutorials](/help/communities/getting-started.md) erstellt wurde
   * Suchen Sie den Knoten der Forumsseite .

     `/content/sites/engage/en/forum/jcr:content`

   * Hinzufügen von Scoring- und Badging-Eigenschaften

   ```
   scoringRules = [/libs/settings/community/scoring/rules/comments-scoring,
   /libs/settings/community/scoring/rules/forums-scoring]
   ```

   ```
   badgingRules =[/libs/settings/community/badging/rules/comments-scoring,
   /libs/settings/community/badging/rules/forums-scoring]
   ```

   * Suchen Sie den Knoten der Forumkomponente .

     `/content/sites/engage/en/forum/jcr:content/content/primary/forum`
( `sling:resourceType = social/forum/components/hbs/forum`)

   * Um Badges anzuzeigen, fügen Sie eine Eigenschaft hinzu

     `allowBadges = true`

   * Ein Benutzer meldet sich an, erstellt ein Forenthema und erhält ein Bronze-Zeichen

1. Eine AEM Site *ohne* eindeutige ID :

   * Verwenden des Leitfadens [Community-Komponenten](/help/communities/components-guide.md)
   * Suchen Sie den Knoten der Forumsseite .

     `/content/community-components/en/forum/jcr:content`

   * Hinzufügen von Scoring- und Badging-Eigenschaften

   ```
   scoringRules = [/libs/settings/community/scoring/rules/comments-scoring,
   /libs/settings/community/scoring/rules/forums-scoring]
   ```

   ```
   badgingRules =[/libs/settings/community/badging/rules/comments-badging,
   /libs/settings/community/badging/rules/forums-badging]
   ```

   * Suchen Sie den Knoten der Forumkomponente .

     `/content/community-components/en/forum/jcr:content/content/forum`
( `sling:resourceType = social/forum/components/hbs/forum`)

   * Um Badges anzuzeigen, fügen Sie eine Eigenschaft hinzu

     `allowBadges = true`

   * Ein Benutzer meldet sich an, erstellt ein Forenthema und erhält ein Bronze-Zeichen

1. Benutzern wird über cURL ein Moderatorzeichen zugewiesen:

   ```shell
   curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/libs/settings/community/badging/images/moderator/jcr:content/moderator.png" https://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
   ```

   Da ein Benutzer zwei Bronze-Abzeichen gesammelt und ein Moderatorenabzeichen erhalten hat, wird der Benutzer mit seinem Forumseintrag wie folgt angezeigt:

   ![moderator](assets/moderator.png)

>[!NOTE]
>
>Dieses Beispiel folgt nicht den folgenden Best Practices:
>
>* Scoring-Regelnamen sollten global eindeutig sein. Sie sollten nicht mit demselben Namen enden.
>
>  Ein Beispiel dafür, was *nicht* zu tun hat:
>
>  /libs/settings/community/scoring/rules/site1/forums-scoring
>  /libs/settings/community/scoring/rules/site2/forums-scoring
>
>* Erstellen von Unique Badge-Bildern für verschiedene AEM Sites

### Auf Scoring-UGC zugreifen {#access-scoring-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird empfohlen.

Zu Ermittlungszwecken wird mithilfe von JSRP zum Beispiel der Basisordner mit Bewertungen

* `/content/usergenerated/asi/jcr/scoring`

Der untergeordnete Knoten von `scoring` ist der Name der Scoring-Regel. Daher empfiehlt es sich, dass die Namen von Scoring-Regeln auf einem Server global eindeutig sind.

Für die Geometrixx Engage-Site befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Scoring-Regel, der Site-ID der Community-Site ( `engage-ba81p`), einer eindeutigen ID und der ID des Benutzers konstruiert wurde:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Auf der Guide-Site &quot;Community-Komponenten&quot;befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Scoring-Regel, einer Standard-ID ( `default-site`), einer eindeutigen ID und der ID des Benutzers konstruiert wurde:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Die Punktzahl wird in der Eigenschaft `scoreValue_tl` gespeichert, die nur einen Wert enthalten oder indirekt auf einen atomicCounter verweisen kann.

![access-scoring-ugc](assets/access-scoring-ugc.png)

### Zugriffsabzeichen-UGC {#access-badging-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird empfohlen.

Zu Untersuchungszwecken wird mithilfe von JSRP beispielsweise der Basisordner mit Informationen zu zugewiesenen oder vergebenen Abzeichen wie folgt angezeigt:

* `/content/usergenerated/asi/jcr`

gefolgt von dem Pfad zum Profil des Benutzers, der in einen Badges-Ordner endet, z. B.:

* `/home/users/community/w271OOup2Z4DjnOQrviv/profile/badges`

#### Ausgezeichnetes Zeichen {#awarded-badge}

![delivered-badging-ugc](assets/access-badging-ugc.png)

#### Zugewiesenes Zeichen {#assigned-badge}

![assigned-badge](assets/assigned-badge.png)

## Zusätzliche Informationen {#additional-information}

So zeigen Sie eine sortierte Liste von Mitgliedern basierend auf Punkten an:

* [Leaderboard-Funktion](/help/communities/functions.md#leaderboard-function) zur Aufnahme in eine Community-Site oder Gruppenvorlage.
* [Leaderboard-Komponente](/help/communities/enabling-leaderboard.md), die Komponente mit Funktionen für Leaderboard, zum Erstellen von Seiten.
