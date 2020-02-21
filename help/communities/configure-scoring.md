---
title: Grundlagen zu Bewertung und Abzeichen
seo-title: Grundlagen zu Bewertung und Abzeichen
description: Übersicht über die Funktionen "Bewertung und Abzeichen"
seo-description: Übersicht über die Funktionen "Bewertung und Abzeichen"
uuid: 6e3af071-04e8-4dc1-977a-0da711b72961
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 628b6dcd-8b1c-4166-8fc2-843baa86ac1c
docset: aem65
translation-type: tm+mt
source-git-commit: d522c5ec6c72a9fd391d021f2fac37f88c686bd9

---


# Grundlagen zu Bewertung und Abzeichen{#scoring-and-badges-essentials}

Die Funktion für die Bewertung und Abzeichen von AEM Communities bietet die Möglichkeit, Community-Mitglieder zu identifizieren und zu belohnen.

Die Details zur Einrichtung der Funktion finden Sie unter

* [Communities - Bewertung und Abzeichen](/help/communities/implementing-scoring.md)

Diese Seite enthält weitere technische Details:

* wie eine Markierung[ als Bild oder Text ](#displaying-badges)angezeigt wird
* So aktivieren Sie die umfassende [Debug-Protokollierung](#debug-log-for-scoring-and-badging)
* wie Sie [auf UGC](#ugc-for-scoring-and-badging) im Zusammenhang mit Scoring und Abzeichen zugreifen können

>[!CAUTION]
>
>Die in CRXDE Lite sichtbare Implementierungsstruktur kann geändert werden.

## Anzeigen von Abzeichen {#displaying-badges}

Ob ein Zeichen als Text oder Bild angezeigt wird, wird auf der Clientseite in der HBS-Vorlage gesteuert.

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

Wenn &quot;true&quot;, zeigt isAssigned an, dass das Zeichen für eine Rolle zugewiesen wurde und das Zeichen als Text angezeigt werden sollte.

Wenn &quot;false&quot;festgelegt ist, zeigt Zugewiesen an, dass das Abzeichen für eine Ergebnisbewertung vergeben wurde und das Abzeichen als Bild angezeigt werden sollte.

Änderungen an diesem Verhalten sollten in einem benutzerdefinierten Skript vorgenommen werden (entweder Überschreiben oder Überlagerung). Siehe [clientseitige Anpassung](/help/communities/client-customize.md).

## Debug-Protokoll für Bewertung und Abzeichen {#debug-log-for-scoring-and-badging}

Um das Debugging von Bewertung und Markierung zu unterstützen, kann eine benutzerdefinierte Protokolldatei eingerichtet werden. Der Inhalt dieser Protokolldatei kann dann dem Kundensupport zur Verfügung gestellt werden, wenn Probleme mit der Funktion auftreten.

Ausführliche Anweisungen finden Sie unter [Erstellen einer benutzerdefinierten Protokolldatei](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

So richten Sie schnell eine Slinglog-Datei ein:

1. Zugriff auf die **Adobe Experience Manager Web Console-Protokollunterstützung**, z. B.

   * https://localhost:4502/system/console/slinglog

1. Neue Protokollfunktion **hinzufügen**

   1. Wählen Sie `DEBUG`für **Protokollebene**

   1. Geben Sie beispielsweise einen Namen für die **Protokolldatei** ein.

      * logs/scoring-debug.log
   1. Geben Sie zwei **Logger **(class) Einträge ein (über `+` das Symbol)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Wählen Sie **Save** aus.



![chlimage_1-193](assets/chlimage_1-193.png)

So zeigen Sie Protokolleinträge an

* aus der Web-Konsole

   * unter dem Menü **Status **Menü
   * Protokolldateien auswählen ****
   * nach dem Namen der Protokolldatei suchen, z. B. `scoring-debug`

* auf dem lokalen Datenträger des Servers

   * Die Protokolldatei befindet sich unter &lt;*Server-Installationsdir*>/crx-quickstart/logs/&lt;*log-file-name*>.log

   * for example, `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-194](assets/chlimage_1-194.png)

## UGC für Scoring und Bading {#ugc-for-scoring-and-badging}

Es ist möglich, die UGC im Zusammenhang mit Scoring und Abzeichen anzuzeigen, wenn die ausgewählte SRP entweder JSRP oder MSRP, aber nicht ASRP ist. (Wenn Sie mit diesen Begriffen nicht vertraut sind, finden Sie weitere Informationen unter Übersicht über den [Community-Content-Speicher](/help/communities/working-with-srp.md) und den [Speicher-Ressourcenanbieter](/help/communities/srp.md).)

Die Beschreibungen für den Zugriff auf Scoring- und Abzeichen-Daten verwenden JSRP, da die UGC mit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)leicht zugänglich ist.

**JSRP zum Autor** : Das Experimentieren in der Autorenumgebung führt zu einer UGC, die nur in der Autorenumgebung sichtbar ist.

**JSRP zur Veröffentlichung** : Ebenso ist es bei Tests in der Veröffentlichungsumgebung erforderlich, auf CRXDE Lite mit Administratorrechten auf einer Veröffentlichungsinstanz zuzugreifen. Wenn die Instanz im Veröffentlichungsmodus im [Produktionsmodus](/help/sites-administering/production-ready.md) ausgeführt wird (nicht im Ausführungsmodus zum Abrufen von Inhalten), muss CRXDE Lite [aktiviert werden](/help/sites-administering/enabling-crxde-lite.md).

Der Basisort von UGC auf JSRP ist `/content/usergenerated/asi/jcr/`.

### Scoring- und Badging-APIs {#scoring-and-badging-apis}

Die folgenden APIs stehen zur Verwendung zur Verfügung:

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

Die neuesten Javadocs für das installierte Feature Pack stehen Entwicklern aus dem Adobe-Repository zur Verfügung. Siehe [Verwenden von Maven für Communities: Javadocs](/help/communities/maven.md#javadocs).

**Speicherort und Format des UGC im Repository können ohne Warnung** geändert werden.

### Beispieleinrichtung {#example-setup}

Die Screenshots der Repository-Daten stammen aus der Einrichtung von Scoring und Abzeichen für ein Forum auf zwei verschiedenen AEM-Sites:

1. Eine AEM-Site *mit* einer eindeutigen ID (Community-Site, die mithilfe des Assistenten erstellt wurde):

* Verwendung der Website &quot;Erste Schritte - Tutorial&quot;(Einsatz), die während der [Übungen für die ersten Schritte erstellt wurde](/help/communities/getting-started.md)
* den Knoten der Forumseite suchen

   * `/content/sites/engage/en/forum/jcr:content`

* Eigenschaften für Bewertung und Markierung hinzufügen

   ```
   scoringRules = [/etc/community/scoring/rules/comments-scoring,
   /etc/community/scoring/rules/forums-scoring]
   ```

   ```
   badgingRules =[/etc/community/badging/rules/comments-scoring,
   /etc/community/badging/rules/forums-scoring]
   ```

* den Knoten der Forumkomponente suchen

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`
( `sling:resourceType = social/forum/components/hbs/forum`)

* Eigenschaft hinzufügen, um Abzeichen anzuzeigen

   * `allowBadges = true`

* ein Benutzer anmelden, ein Forenthema erstellen und ein Bronze-Abzeichen erhalten

1. Eine AEM-Site *ohne* eine eindeutige ID:

* Verwenden des Handbuchs &quot; [Community-Komponenten&quot;](/help/communities/components-guide.md)
* den Knoten der Forumseite suchen

   * `/content/community-components/en/forum/jcr:content`

* Eigenschaften für Bewertung und Markierung hinzufügen

   ```
   scoringRules = [/etc/community/scoring/rules/comments-scoring,
   /etc/community/scoring/rules/forums-scoring]
   ```

   ```
   badgingRules =[/etc/community/badging/rules/comments-scoring,
   /etc/community/badging/rules/forums-scoring]
   ```

* den Knoten der Forumkomponente suchen

   * `/content/community-components/en/forum/jcr:content/content/forum`
( `sling:resourceType = social/forum/components/hbs/forum`)

* Eigenschaft hinzufügen, um Abzeichen anzuzeigen

   * `allowBadges = true`

* ein Benutzer anmelden, ein Forenthema erstellen und ein Bronze-Abzeichen erhalten

1. einem Benutzer mit cURL ein Moderator-Abzeichen zugewiesen wird:

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" https://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

Da ein Benutzer zwei Bronze-Abzeichen erhalten hat und ein Moderator-Abzeichen erhalten hat, wird der Benutzer mit seinem Foreneintrag wie folgt angezeigt:

![chlimage_1-195](assets/chlimage_1-195.png)

>[!NOTE]
>
>Dieses Beispiel folgt nicht den folgenden bewährten Verfahren:
>
>* Die Namen von Bewertungsregeln sollten global eindeutig sein. sie sollten nicht mit demselben Namen enden.
   >  Ein Beispiel dafür, was *nicht *zu tun ist:
   >  /etc/community/scoring/rules/site1/forums-scoring
   >  /etc/community/scoring/rules/site2/forums-scoring
   >
   >
* Erstellen von eindeutigen Abzeichen-Bildern für verschiedene AEM-Sites
>



### Zugriff auf Scoring-UGC {#access-scoring-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird bevorzugt.

Zu Ermittlungszwecken ist der Basisordner, der Ergebnisse enthält, z. B. mithilfe von JSRP

* `/content/usergenerated/asi/jcr/scoring`

Der untergeordnete Knoten von `scoring`ist der Name der Bewertungsregel. Eine Best Practice ist daher, dass die Namen von Bewertungsregeln auf einem Server global eindeutig sind.

Für die Geometrixx-Engage-Site befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Bewertungsregel, der Community-Site-ID ( `engage-ba81p`), einer eindeutigen ID und der Benutzer-ID verknüpft ist:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Auf der Guide-Site &quot;Community-Komponenten&quot;befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Bewertungsregel, einer Standard-ID ( `default-site`), einer eindeutigen ID und der ID des Benutzers erstellt wird:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Das Ergebnis wird in der Eigenschaft gespeichert, `scoreValue_tl` die direkt einen Wert enthält oder indirekt auf einen atomicCounter verweist.

![chlimage_1-196](assets/chlimage_1-196.png)

### UGC für Zugriffsabzeichen {#access-badging-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird bevorzugt.

Zu Ermittlungszwecken wird beispielsweise mithilfe von JSRP der Basisordner mit Informationen über zugewiesene oder zugewiesene Kennzeichen wie folgt angezeigt:

* /content/usergenerated/asi/jcr

Nach dem Pfad zum Benutzerprofil, der in einem Ablagenordner endet, z. B.

* /home/users/community/w271OOup2Z4DjnOQrviv/profile/badges

#### Auszeichnung {#awarded-badge}

![chlimage_1-197](assets/chlimage_1-197.png)

#### zugewiesene Markierung {#assigned-badge}

![chlimage_1-198](assets/chlimage_1-198.png)

## Zusätzliche Informationen {#additional-information}

So zeigen Sie eine sortierte Liste der Mitglieder basierend auf Punkten an:

* [Leaderboard-Funktion](/help/communities/functions.md#leaderboard-function) zur Einbindung in eine Community-Site- oder Gruppenvorlage.
* [Komponente](/help/communities/enabling-leaderboard.md)&quot;Leaderboard&quot;, die spezielle Komponente der Funktion &quot;Leaderboard&quot;, zum Erstellen von Seiten.

