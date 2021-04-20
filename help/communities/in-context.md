---
title: Kontextbezogene Moderation
seo-title: Kontextbezogene Moderation
description: So führen Sie Moderatoraktionen durch
seo-description: So führen Sie Moderatoraktionen durch
uuid: 282a8bea-2822-4e5c-b9f4-4d9a5380d895
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ee104f6f-123b-4a6e-9031-849fc1318cc5
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 1%

---


# In-Context-Moderation {#in-context-moderation}

Für AEM Communities kann die Moderation von Administratoren und vertrauenswürdigen Community-Mitgliedern direkt auf der veröffentlichten Seite durchgeführt werden, auf der die Community-Inhalte veröffentlicht wurden.

Bei Verwendung einer [Moderationskonsole](moderation.md) enthalten die für den Inhalt angezeigten Informationen einen Link zur veröffentlichten Seite, um Zugriff auf zusätzliche Moderationsaktionen zu gewähren, die bei der Moderation im Kontext verfügbar sind.

## Moderationsaktionen {#moderation-actions}

In der Moderationsübersicht finden Sie eine Beschreibung der [Moderationsaktionen](moderate-ugc.md#moderation-actions).

## Moderations-Benutzeroberfläche {#moderation-ui}

Die Benutzeroberfläche, die dem Moderator auf der Veröffentlichungsinstanz angezeigt wird, ist im Dialogfeld zum Posten und Verwalten benutzergenerierter Inhalte enthalten. Die Elemente der Benutzeroberfläche werden vom Status des Site-Besuchers bestimmt - ob es sich um...

1. Das Mitglied, das den Inhalt veröffentlicht hat.
1. Moderator für vertrauenswürdige Mitglieder.
1. Ein Administrator.
1. Angemeldet, jedoch weder Administrator, Moderator noch Autor des Inhalts.
1. Nicht angemeldet.

## Beispiel {#example}

Mithilfe der Site [Geometrixx Engage](http://localhost:4503/content/sites/engage/en.html), die beim [Erste Schritte mit AEM Communities](getting-started.md) erstellt wurde, ist es möglich, schnell einen Thread in einem Forum einzurichten, auf dem verschiedene Moderationsaktivitäten in der Umgebung &quot;Veröffentlichen&quot;durchgeführt werden können, wie unten dargestellt.

Aaron McDonald (aaron.mcdonald@mailinator.com) wurde als vertrauenswürdiges Community-Mitglied identifiziert, indem er ihn bei der Erstellung der Site zur Community-Interaktions-Moderatorengruppe hinzufügte.

Rebekah Larsen (rebekah.larsen@trashymail.com) kann als Mitglied der Community-Interaktionsgruppe mithilfe der [Members console](members.md) hinzugefügt werden.

Weitere Informationen zu Community-Benutzergruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

### Forumbeiträge {#create-the-forum-posts} erstellen

* Als Rebekah Larsen anmelden (rebekah.larsen@trashymail.com)

   * Forum auswählen
   * Neuen Beitrag auswählen
   * Betreff eingeben

      Wann ändert sich der Nektar in der Humming Bird Feeder

   * Textkörper eingeben

      Ich hatte nicht viel Erfolg, als ich jedes Jahr eine Kolibris-Feeder aufhängte. Es scheint, sie kommen ein oder zwei Tage, dann ist es. Ich ändere es einmal in der Woche ist das zu lang? Muss ich es früher ändern?

   * Beitrag auswählen
   * Abmelden auswählen

* Melden Sie sich als Aaron McDonald an (aaron.mcdonald@mailinator.com)

   * Forum auswählen
   * Wählen Sie für das Hummingbird-Thema Mehr lesen
   * Geben Sie den Kommentar für Antwort auf Beitrag ein

      Ich wechsele meine einmal pro Woche und bekomme sie von Mai bis Oktober.

   * Antwort auswählen
   * Abmelden auswählen

* Melden Sie sich als Andrew Schäffer an (andrew.schaeffer@trashymail.com)

   * Forum auswählen
   * Wählen Sie für das Hummingbird-Thema Mehr lesen
   * Geben Sie den Kommentar für Antwort auf Beitrag ein

      Ich verkaufe Nektar und Feeds - https://my.viral.url/

   * Antwort auswählen
   * Abmelden auswählen

### Anonymer Site-Besucher (#5) {#anonymous-site-visitor}

Im Folgenden finden Sie eine Ansicht des Forums, das von einem Site-Besucher gesehen wird, der nicht angemeldet ist (5).

Ein anonymer Site-Besucher kann nur die Ansicht des Forums durchführen, darf jedoch keine Inhalte veröffentlichen und keine Moderationsaktionen durchführen.

![community-forum-Besucher](assets/community-forum-visitor.png)

### Neues Mitglied (#4) {#new-member}

Melden Sie sich beim Autor als Admin an und fügen Sie Boyd Larsen (boyd.larsen@dodgit.com) als neues Mitglied der Community-Interaktionsmitglieder-Gruppe mit der [Members-Konsole](members.md) hinzu und melden Sie sich dann ab.

Melden Sie sich bei der Veröffentlichung als Boyd Larsen an und greifen Sie auf den Thread zu, indem Sie `Forum` und dann `Read more` für den hummingbird-Beitrag auswählen.

Hinweis:

* Boyd hat nicht am Forum teilgenommen.
* Boyd kann nichts löschen.
* Boyd ist angemeldet und kann Inhalte beantworten oder kennzeichnen.

Lassen Sie Boyd &quot;Flag&quot;auswählen, um die von Andrew veröffentlichten Inhalte zu kennzeichnen.

Abmelden

![community-forum-member](assets/community-forum-member.png)

### Administrator (#3) {#administrator}

Melden Sie sich als Administrator (Admin) an und greifen Sie auf den Thread zu, indem Sie &quot;Forum&quot;auswählen und dann mehr für einen Beitrag lesen.

Hinweis:

* Admin kann Flag, Löschen, Bearbeiten, Ablehnen, Ausschneiden, Schließen, Stecken, Funktion.
* Admin kann Administration auswählen, um auf die Moderationskonsole zuzugreifen.

![community-admin-forum](assets/community-admin-forum.png)

Wählen Sie im Menü &quot;Administration&quot;die Option [Moderationskonsole](moderation.md) aus der Umgebung &quot;publish&quot;aus.

Beachten Sie, dass für einen Administrator alle moderierbaren Inhalte sichtbar sind, nicht nur Inhalte von der Community-Site von Geometrixx Engage.

Der Suchfilter ist ein Sidepanel, das geöffnet oder geschlossen wird.

Abmelden.

![moderation-console-publish](assets/moderation-console-publish.png)

### Community-Moderator (#2) {#community-moderator}

Melden Sie sich als Aaron McDonald (aaron.mcdonal@mailinator.com) an, ein Community-Moderator, und greifen Sie auf den Thread zu, indem Sie Forum auswählen, und lesen Sie mehr für den Beitrag hummingbird.

Hinweis:

* Aaron kann seinen eigenen Beitrag beantworten, löschen, bearbeiten oder ablehnen.
* Aaron kann auch andere Inhalte kennzeichnen/zulassen, beantworten, löschen, bearbeiten, ablehnen.
* Aaron kann das Forenthema ausschneiden, um es in ein anderes Forum zu verschieben, für das er moderiert.
* Aaron kann Administration auswählen, um auf die Moderationskonsole zuzugreifen.

![community-forum-moderator](assets/community-forum-moderator.png)

Wählen Sie im Menü &quot;Administration&quot;die Option [Moderationskonsole](moderation.md) aus der Umgebung &quot;publish&quot;aus.

Beachten Sie, dass für einen Community-Moderator nur moderierbare Inhalte von der Geometrixx Engage Community-Site sichtbar sind.

Beachten Sie, dass der Community-Moderator dieselben Optionen wie der Administrator hat (Bild ist bei geschlossener Suchseitenleiste geschlossen), aber keinen Zugriff auf andere AEM Konsolen hat.

Abmelden.

![moderator-access](assets/moderator-access.png)

### Inhaltsautor (#1) {#content-author}

Melden Sie sich bei Rebekah Larsen (rebekah.larsen@mailinator.com) an, einem Community-Mitglied, das den Thread gestartet hat, und greifen Sie auf den Thread zu, indem Sie Forum auswählen und dann mehr für den Beitrag von hummingbird lesen.

Hinweis:

* Rebekah kann ihren eigenen Beitrag löschen oder bearbeiten.
* Rebekah kann auch andere Inhalte beantworten oder kennzeichnen.
* Rebekah kann nicht auf die Moderationskonsole zugreifen.

![community-forum-author](assets/community-forum-author.png)

