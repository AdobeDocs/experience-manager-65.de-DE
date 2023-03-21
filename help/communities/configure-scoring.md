---
title: Grundlagen zu Scoring und Abzeichen
seo-title: Scoring and Badges Essentials
description: Übersicht über die Funktionen Scoring und Badges
seo-description: Scoring and Badges feature overview
uuid: 6e3af071-04e8-4dc1-977a-0da711b72961
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 628b6dcd-8b1c-4166-8fc2-843baa86ac1c
docset: aem65
exl-id: 470a382a-2aa7-449e-bf48-b5a804c5b114
source-git-commit: 4fa868f3ae4778d3a637e90b91f7c5909fe5f8aa
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 2%

---

# Grundlagen zu Scoring und Abzeichen {#scoring-and-badges-essentials}

Mit der AEM Communities-Scoring- und Badges-Funktion werden Community-Mitglieder identifiziert und belohnt.

Die Details zur Einrichtung der Funktion finden Sie unter

* [Communities-Scoring und -Abzeichen](/help/communities/implementing-scoring.md)

Diese Seite enthält zusätzliche technische Details:

* Anleitung [Zeichen anzeigen](#displaying-badges) als Bild oder Text
* So aktivieren Sie umfangreiche [Debug-Protokollierung](#debug-log-for-scoring-and-badging)
* Anleitung [Zugriff auf UGC](#ugc-for-scoring-and-badging) im Zusammenhang mit Scoring und Badging

>[!CAUTION]
>
>Die in CRXDE Lite sichtbare Implementierungsstruktur kann sich ändern.

## Anzeigen von Abzeichen {#displaying-badges}

Ob ein Badge als Text oder Bild angezeigt wird, wird auf der Clientseite in der HBS-Vorlage gesteuert.

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

Wenn &quot;true&quot;, zeigt isAssigned an, dass das Zeichen für eine Rolle zugewiesen wurde und das Zeichen als Text angezeigt werden soll.

Ist der Wert &quot;false&quot;, bedeutet &quot;isAssigned&quot;, dass das Abzeichen für einen Ergebniswert vergeben wurde und das Abzeichen als Bild angezeigt werden soll.

Alle Änderungen an diesem Verhalten sollten in einem benutzerdefinierten Skript vorgenommen werden (entweder Überschreiben oder Überlagerung). Siehe [Clientseitige Anpassung](/help/communities/client-customize.md).

## Debug-Protokoll für Scoring und Badging {#debug-log-for-scoring-and-badging}

Um Scoring und Badging zu debuggen, kann eine benutzerdefinierte Protokolldatei eingerichtet werden. Der Inhalt dieser Protokolldatei kann dann dem Support zur Verfügung gestellt werden, wenn Probleme mit der Funktion auftreten.

Detaillierte Anweisungen finden Sie unter [Benutzerdefinierte Protokolldatei erstellen](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

So richten Sie eine Slinglog-Datei schnell ein:

1. Zugriff auf **Adobe Experience Manager Web Console-Protokollunterstützung** beispielsweise

   * https://localhost:4502/system/console/slinglog

1. Auswählen **Hinzufügen neuer Logger**

   1. Auswählen `DEBUG` für **Protokollebene**

   1. Geben Sie einen Namen für **Protokolldatei** beispielsweise

      * logs/scoring-debug.log
   1. Zwei eingeben **Logger** (class) -Einträge (mithilfe von `+` Symbol)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Wählen Sie **Speichern** aus



![debug-scoring-log](assets/debug-scoring-log.png)

So zeigen Sie Protokolleinträge an:

* Über die Web-Konsole

   * Unter dem **Status** Menü
   * Auswählen **Protokolldateien**
   * Suchen Sie nach dem Namen Ihrer Protokolldatei, z. B. `scoring-debug`

* Auf der lokalen Festplatte des Servers

   * Die Protokolldatei befindet sich unter &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log

   * Beispiel: `.../crx-quickstart/logs/scoring-debug.log`

![scoring-log](assets/scoring-log.png)

## UGC für Scoring und Badging {#ugc-for-scoring-and-badging}

Es ist möglich, die UGC im Zusammenhang mit Scoring und Badging anzuzeigen, wenn das ausgewählte SRP entweder JSRP oder MSRP, aber nicht ASRP ist. (Wenn Sie diese Begriffe nicht kennen, lesen Sie [Community-Inhaltsspeicherung](/help/communities/working-with-srp.md) und [Übersicht über den Speicheranbieter](/help/communities/srp.md).

Die Beschreibungen für den Zugriff auf Scoring- und Badging-Daten verwenden JSRP, da der Zugriff auf die UGC über [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

**JSRP für Autor**: Das Experimentieren in der Autorenumgebung führt zu benutzergenerierten Inhalten, die nur in der Autorenumgebung sichtbar sind.

**JSRP bei Veröffentlichung**: Ebenso ist es bei Tests in der Veröffentlichungsumgebung erforderlich, auf die CRXDE Lite mit Administratorrechten in einer Veröffentlichungsinstanz zuzugreifen. Wenn die Veröffentlichungsinstanz in ausgeführt wird [Produktionsmodus](/help/sites-administering/production-ready.md) (Ausführungsmodus nosamplecontent ), ist es erforderlich, [CRXDE Lite aktivieren](/help/sites-administering/enabling-crxde-lite.md).

Der Basisspeicherort von UGC auf JSRP lautet `/content/usergenerated/asi/jcr/`.

### Scoring- und Badging-APIs {#scoring-and-badging-apis}

Die folgenden APIs stehen zur Verwendung zur Verfügung:

* [com.adobe.cq.social.scoring.api in 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de)
* [com.adobe.cq.social.badging.api in 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de)

Die neuesten Javadocs für das installierte Feature Pack stehen Entwicklern aus dem Adobe-Repository zur Verfügung. Siehe [Verwenden von Maven für Communities : Javadocs](/help/communities/maven.md#javadocs).

**Speicherort und Format der UGC im Repository können ohne Warnung geändert werden**.

### Beispieleinrichtung {#example-setup}

Die Screenshots von Repository-Daten stammen aus der Einrichtung von Scoring und Badging für ein Forum auf zwei verschiedenen AEM Sites :

1. AEM *mit* eine eindeutige ID (Community-Site, die mithilfe des Assistenten erstellt wurde) :

   * Verwenden der Site &quot;Erste Schritte - Tutorial&quot;(Interaktion), die während der [Tutorial zu den ersten Schritten](/help/communities/getting-started.md)
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


1. AEM *without* eine eindeutige ID :

   * Verwenden der [Handbuch zu Community-Komponenten](/help/communities/components-guide.md)
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

   ![Moderator](assets/moderator.png)

>[!NOTE]
>
>Dieses Beispiel folgt nicht den folgenden Best Practices:
>
>* Die Namen von Scoring-Regeln sollten global eindeutig sein. sollten sie nicht mit demselben Namen enden.
>
>  Ein Beispiel für *not* zu tun:
>
>  /libs/settings/community/scoring/rules/site1/forums-scoring
>  /libs/settings/community/scoring/rules/site2/forums-scoring
>
>* Erstellen von Unique Badge-Bildern für verschiedene AEM Sites


### Auf Scoring-UGC zugreifen {#access-scoring-ugc}

Verwendung der [APIs](#scoring-and-badging-apis) wird bevorzugt.

Zu Ermittlungszwecken wird mithilfe von JSRP zum Beispiel der Basisordner mit Bewertungen

* `/content/usergenerated/asi/jcr/scoring`

Der untergeordnete Knoten von `scoring` ist der Name der Scoring-Regel. Daher empfiehlt es sich, dass die Namen von Scoring-Regeln auf einem Server global eindeutig sind.

Für die Geometrixx Engage-Site befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Scoring-Regel, der Site-ID der Community-Site ( `engage-ba81p`), eine eindeutige ID und die ID des Benutzers:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Auf der Guide-Site &quot;Community-Komponenten&quot;befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Scoring-Regel, einer Standard-ID ( `default-site`), eine eindeutige ID und die ID des Benutzers:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Das Ergebnis wird in der -Eigenschaft gespeichert. `scoreValue_tl` , die nur einen Wert enthalten oder indirekt auf einen atomicCounter verweisen können.

![access-scoring-ugc](assets/access-scoring-ugc.png)

### Zugriffsabzeichen-UGC {#access-badging-ugc}

Verwendung der [APIs](#scoring-and-badging-apis) wird bevorzugt.

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

* [Leaderboard-Funktion](/help/communities/functions.md#leaderboard-function) für die Aufnahme in eine Community-Site oder Gruppenvorlage.
* [Leaderboard-Komponente](/help/communities/enabling-leaderboard.md), die Komponente mit Funktionen der Leaderboard-Funktion für die Seitenbearbeitung.
