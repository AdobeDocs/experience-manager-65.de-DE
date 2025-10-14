---
title: Grundlagen zu Bewertungen und Abzeichen
description: Erfahren Sie, wie die Adobe Experience Manager Communities-Funktion Bewertung und Abzeichen Community-Mitglieder identifiziert und belohnt.
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

# Grundlagen zu Bewertungen und Abzeichen {#scoring-and-badges-essentials}

Die AEM Communities-Funktion mit Scoring- und Abzeichen identifiziert und belohnt Community-Mitglieder.

Einzelheiten zur Einrichtung der Funktion finden Sie unter

* [Vergabe von Bewertungen und Abzeichen in Communities](/help/communities/implementing-scoring.md)

Diese Seite enthält zusätzliche technische Details :

* So zeigen [&#x200B; ein Badge &#x200B;](#displaying-badges) Bild oder Text an
* Anleitung zum Aktivieren der umfangreichen [Debug-Protokollierung](#debug-log-for-scoring-and-badging)
* Wie Sie [UGC) zugreifen](#ugc-for-scoring-and-badging) im Zusammenhang mit der Bewertung und dem Badging

>[!CAUTION]
>
>Die in CRXDE Lite sichtbare Implementierungsstruktur kann sich ändern.

## Anzeigen von Abzeichen {#displaying-badges}

Ob ein Badge als Text oder Bild angezeigt wird, wird Client-seitig in der HBS-Vorlage gesteuert.

Suchen Sie beispielsweise nach `this.isAssigned` in `/libs/social/forum/components/hbs/topic/list-item.hbs`:

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

Wenn „true“, zeigt `isAssigned` an, dass das Abzeichen für eine Rolle zugewiesen wurde und als Text angezeigt werden soll.

Wenn „false“, zeigt `isAssigned` an, dass das Abzeichen für einen erreichten Wert vergeben wurde und als Bild angezeigt werden sollte.

Alle Änderungen an diesem Verhalten sollten in einem benutzerdefinierten Skript vorgenommen werden (entweder überschreiben oder überlagern). Siehe [Client-seitige Anpassung](/help/communities/client-customize.md).

## Debug-Protokoll für Bewertung und Badging {#debug-log-for-scoring-and-badging}

Um die Fehlerbehebung bei der Bewertung und dem Badging zu erleichtern, kann eine benutzerdefinierte Protokolldatei eingerichtet werden. Der Inhalt dieser Protokolldatei kann dann dem Support bereitgestellt werden, wenn bei der Funktion Probleme auftreten.

Detaillierte Anweisungen finden Sie unter [Erstellen einer benutzerdefinierten Protokolldatei](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

So richten Sie schnell eine Slinglog-Datei ein:

1. Greifen Sie auf die Protokollunterstützung für die **Adobe Experience Manager Web Console zu** z. B.

   * https://localhost:4502/system/console/slinglog

1. Wählen Sie **Neue Protokollierung hinzufügen**

   1. Wählen Sie `DEBUG` für **Protokollebene**

   1. Geben Sie einen Namen für **Protokolldatei** ein, z. B.

      * logs/scoring-debug.log

   1. Geben Sie zwei **Logger**-Einträge (Klasse) ein (mit `+` Symbol)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`

   1. Wählen Sie **Speichern** aus

![debug-scoring-log](assets/debug-scoring-log.png)

So zeigen Sie Protokolleinträge an:

* Über die Web-Konsole

   * Im Menü **Status**
   * Wählen Sie **Protokolldateien**
   * Suchen Sie nach Ihrem Protokolldateinamen, z. B. `scoring-debug`

* Auf der lokalen Festplatte des Servers

   * Die Protokolldatei befindet sich unter &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log

   * Zum Beispiel: `.../crx-quickstart/logs/scoring-debug.log`

![scoring-log](assets/scoring-log.png)

## UGC für Bewertung und Badging {#ugc-for-scoring-and-badging}

Der UGC für die Bewertung und das Badging kann angezeigt werden, wenn das ausgewählte SRP entweder JSRP oder MSRP, aber nicht ASRP ist. (Wenn Sie mit diesen Begriffen nicht vertraut sind, finden Sie weitere Informationen unter [Community-](/help/communities/working-with-srp.md) und [Speicherressourcenanbieter - Übersicht](/help/communities/srp.md).)

Die Beschreibungen für den Zugriff auf Scoring- und Badging-Daten verwenden JSRP, da der UGC über [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) leicht zugänglich ist.

**JSRP auf Author**: Experimentieren in der Authoring-Umgebung führt zu UGC, der nur in der Authoring-Umgebung sichtbar ist.

**JSRP bei der Veröffentlichung**: Entsprechend ist es beim Testen in der Veröffentlichungsumgebung erforderlich, auf CRXDE Lite mit Administratorrechten in einer Veröffentlichungsinstanz zuzugreifen. Wenn die Veröffentlichungsinstanz im [Produktionsmodus) ausgeführt wird &#x200B;](/help/sites-administering/production-ready.md)Ausführungsmodus „nosamplecontent„), müssen Sie [CRXDE Lite aktivieren](/help/sites-administering/enabling-crxde-lite.md).

Der Basisspeicherort von UGC auf JSRP ist `/content/usergenerated/asi/jcr/`.

### Scoring- und Badging-APIs {#scoring-and-badging-apis}

Die folgenden APIs sind zur Verwendung verfügbar:

* [com.adobe.cq.social.scoring.api in 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de)
* [com.adobe.cq.social.badging.api in 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de)

Die neuesten Javadocs für das installierte Feature Pack stehen Entwicklern im Adobe-Repository zur Verfügung. Siehe [Verwenden von Maven für Communities : Javadocs](/help/communities/maven.md#javadocs).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

### Beispiel-Setup {#example-setup}

Die Screenshots von Repository-Daten stammen vom Einrichten einer Bewertung für ein Forum auf zwei verschiedenen AEM-Sites :

1. Eine AEM-Site *mit* einer eindeutigen ID (Community-Site, die mithilfe des Assistenten erstellt wurde) :

   * Verwenden der Website „Erste Schritte-Tutorial (Engage)“, die während des Tutorials [Erste Schritte“ erstellt wurde](/help/communities/getting-started.md)
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

   * Suchen Sie den Komponentenknoten Forum .

     `/content/sites/engage/en/forum/jcr:content/content/primary/forum`
( `sling:resourceType = social/forum/components/hbs/forum`)

   * Um Abzeichen anzuzeigen, fügen Sie die Eigenschaft hinzu

     `allowBadges = true`

   * Ein Benutzer meldet sich an, erstellt ein Forumsthema und erhält ein Bronze-Abzeichen

1. Eine AEM-Site *ohne* eindeutige ID :

   * Verwenden des [Community-Komponentenhandbuchs](/help/communities/components-guide.md)
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

   * Suchen Sie den Komponentenknoten Forum .

     `/content/community-components/en/forum/jcr:content/content/forum`
( `sling:resourceType = social/forum/components/hbs/forum`)

   * Um Abzeichen anzuzeigen, fügen Sie die Eigenschaft hinzu

     `allowBadges = true`

   * Ein Benutzer meldet sich an, erstellt ein Forumsthema und erhält ein Bronze-Abzeichen

1. Einem Benutzer wird mithilfe von cURL ein Moderator-Badge zugewiesen:

   ```shell
   curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/libs/settings/community/badging/images/moderator/jcr:content/moderator.png" https://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
   ```

   Da ein Benutzer zwei Bronze-Abzeichen verdient hat und ein Moderator-Abzeichen erhalten hat, erscheint der Benutzer mit seinem Forumseintrag wie folgt:

   ![Moderator](assets/moderator.png)

>[!NOTE]
>
>Dieses Beispiel folgt nicht den folgenden Best Practices:
>
>* Bewertungsregelnamen sollten global eindeutig sein und nicht mit demselben Namen enden.
>
>  Ein Beispiel dafür *was* tun:
>
>  /libs/settings/community/scoring/rules/site1/forums-scoring
>  /libs/settings/community/scoring/rules/site2/forums-scoring
>
>* Erstellen eindeutiger Badge-Bilder für verschiedene AEM-Sites

### Zugriff auf Bewertungsbenutzeroberfläche {#access-scoring-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird bevorzugt.

Zu Ermittlungszwecken wird im Beispiel mit JSRP der Basisordner mit Scores verwendet

* `/content/usergenerated/asi/jcr/scoring`

Der untergeordnete Knoten von `scoring` ist der Name der Bewertungsregel. Daher empfiehlt es sich, die Namen von Bewertungsregeln auf einem Server global eindeutig zu definieren.

Für die Geometrixx Engage-Site befinden sich die Benutzerin bzw. der Benutzer und deren Wert in einem Pfad, der mit dem Namen der Bewertungsregel, der Site-ID der Community-Site (`engage-ba81p`), einer eindeutigen ID und der Benutzer-ID erstellt wurde:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Auf der Website für das Handbuch der Community-Komponenten befinden sich der Benutzer und sein Score in einem Pfad, der aus dem Namen der Bewertungsregel, einer Standard-ID (`default-site`), einer eindeutigen ID und der Benutzer-ID besteht:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Der Wert wird in der Eigenschaft `scoreValue_tl` gespeichert, die nur einen Wert enthalten oder indirekt auf einen atomischen Zähler verweisen kann.

![access-scoring-ugc](assets/access-scoring-ugc.png)

### Zugriff auf Badging-UGC {#access-badging-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird bevorzugt.

Zu Untersuchungszwecken wird beispielsweise JSRP verwendet. Der Basisordner mit Informationen zu zugewiesenen oder zugewiesenen Abzeichen ist

* `/content/usergenerated/asi/jcr`

gefolgt vom Pfad zum Profil des Benutzers, der in einem Abzeichenordner endet, z. B.:

* `/home/users/community/w271OOup2Z4DjnOQrviv/profile/badges`

#### Ausgezeichnetes Abzeichen {#awarded-badge}

![award-badging-ugc](assets/access-badging-ugc.png)

#### Zugewiesene Abzeichen {#assigned-badge}

![assigned-badge](assets/assigned-badge.png)

## Zusätzliche Informationen {#additional-information}

So zeigen Sie eine sortierte Liste von Elementen basierend auf Punkten an:

* [Leaderboardfunktion](/help/communities/functions.md#leaderboard-function) zur Aufnahme in eine Community-Site oder Gruppenvorlage.
* [Leaderboardkomponente](/help/communities/enabling-leaderboard.md), die vorgestellte Komponente der Funktion Leaderboard für die Seitenbearbeitung.
