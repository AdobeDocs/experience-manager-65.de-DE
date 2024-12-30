---
title: Kontextbezogene Moderation
description: Erfahren Sie, wie Administratoren und vertrauenswürdige Community-Mitglieder Moderatoraktionen in Adobe Experience Manager Communities durchführen können.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 47b3c19c-5228-4b72-b78c-7ed71b308921
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# Kontextbezogene Moderation {#in-context-moderation}

Für AEM Communities kann die Moderation von Administratoren und vertrauenswürdigen Community-Mitgliedern direkt auf der veröffentlichten Seite durchgeführt werden, auf der die Community-Inhalte veröffentlicht wurden.

Bei Verwendung einer [Moderationskonsole](moderation.md) enthalten die für den Inhalt angezeigten Informationen einen Link zur veröffentlichten Seite, um den Zugriff auf zusätzliche Moderationsaktionen zu ermöglichen, die bei der kontextbezogenen Moderation verfügbar sind.

## Moderationsaktionen {#moderation-actions}

In der Übersicht zur Moderation finden Sie eine Beschreibung [Moderationsaktionen](moderate-ugc.md#moderation-actions).

## Moderations-Benutzeroberfläche {#moderation-ui}

Die Benutzeroberfläche, die dem Moderator auf der Veröffentlichungsinstanz präsentiert wird, ist im Dialogfeld für die Veröffentlichung und Verwaltung von benutzergenerierten Inhalten (User-Generated Content, UGC) enthalten. Die Elemente der Benutzeroberfläche werden durch den Status des Site-Besuchers bestimmt - ob sie…

1. Die Person, die den Inhalt gepostet hat.
1. Ein vertrauenswürdiger Mitglied-Moderator.
1. Ein Administrator.
1. Angemeldet, aber weder Administrator, Moderator noch Autor des Inhalts.
1. Nicht angemeldet.

## Beispiel {#example}

Mithilfe der [Geometrixx Engage](http://localhost:4503/content/sites/engage/en.html)-Site, die bei [Erste Schritte mit AEM Communities](getting-started.md) erstellt wurde, ist es möglich, einen Thread in einem Forum einzurichten, in dem verschiedene Moderationsaktivitäten in der Publish-Umgebung durchgeführt werden können. Siehe unten.

Aaron McDonald (`aaron.mcdonald@mailinator.com`) wurde als vertrauenswürdiges Community-Mitglied identifiziert, indem er bei der Erstellung der Website der Gruppe community-engage-Moderators hinzugefügt wurde.

Rebekah Larsen (`rebekah.larsen@trashymail.com`) kann über die „Mitglieder-Konsole“ als Mitglied der Community[Engage-Members-Gruppe ](members.md) werden.

Weitere Informationen zu Community-Benutzergruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

### Erstellen von Forumsbeiträgen {#create-the-forum-posts}

* Melden Sie sich als Rebekah Larsen an (rebekah.larsen@trashymail.com)

   * Forum auswählen
   * Neuen Beitrag auswählen
   * Betreff eingeben

     Wann der Nektar im Humming Bird Feeder zu ändern ist

   * Geben Sie den Textkörper ein

     Ich hatte keinen großen Erfolg, als ich jedes Jahr einen Kolibrifutter aufhängte. Anscheinend kommen sie ein oder zwei Tage, dann ist das alles. Wenn ich es einmal pro Woche ändere, ist das zu lang? Muss ich das früher ändern?

   * Beitrag auswählen
   * Wählen Sie Abmelden

* Melden Sie sich als Aaron McDonald an (aaron.mcdonald@mailinator.com)

   * Forum auswählen
   * Wählen Sie für das Kolibri-Thema Mehr erfahren .
   * Kommentar für „Antwort posten“ eingeben

     Ich wechsle meinen einmal pro Woche und bekomme sie von Mai bis Oktober.

   * Antwort auswählen
   * Wählen Sie Abmelden

* Melden Sie sich als Andrew Schäffer an (andrew.schaeffer@trashymail.com)

   * Forum auswählen
   * Wählen Sie für das Kolibri-Thema Mehr erfahren .
   * Kommentar für „Antwort posten“ eingeben

     Ich verkaufe Nektar und Feeder - besuchen Sie https://my.viral.url/

   * Antwort auswählen
   * Wählen Sie Abmelden

### Anonymer Site-Besucher (#5) {#anonymous-site-visitor}

Im Folgenden sehen Sie eine Ansicht des Forums, die von einem Site-Besucher gesehen wird, der nicht angemeldet ist (5).

Ein anonymer Site-Besucher darf nur das Forum anzeigen, jedoch keine Inhalte posten und keine Moderationsaktionen durchführen.

![community-forum-visitor](assets/community-forum-visitor.png)

### Neues Mitglied (#4) {#new-member}

Melden Sie sich bei der Autoreninstanz als Administrator an und fügen Sie Boyd Larsen (boyd.larsen@dodgit.com) als neues Mitglied der Gruppe „community-engage-members“ über die [Mitgliederkonsole](members.md) hinzu und melden Sie sich dann ab.

Melden Sie sich bei der Veröffentlichung als Boyd Larsen an und greifen Sie auf den Thread zu, indem Sie `Forum` auswählen, und `Read more` Sie dann auf den Kolibri-Beitrag.

Hinweis:

* Boyd hat nicht am Forum teilgenommen.
* Text kann nichts löschen.
* Text ist angemeldet und kann Inhalte beantworten oder kennzeichnen.

Bitten Sie Boyd Flag auszuwählen, um den von Andrew geposteten Inhalt zu kennzeichnen.

Abmelden

![community-forum-member](assets/community-forum-member.png)

### Administrator (#3) {#administrator}

Melden Sie sich als Administrator (Admin) an und greifen Sie auf den Thread zu, indem Sie Forum und dann Weitere Informationen für einen Beitrag auswählen.

Hinweis:

* Der Administrator kann Kennzeichnen, Löschen, Bearbeiten, Ablehnen, Ausschneiden, Schließen, Anheften, Feature.
* Der Administrator kann Administration auswählen, um auf die Moderationskonsole zuzugreifen.

![community-admin-forum](assets/community-admin-forum.png)

Wählen Sie das Menüelement Administration aus, damit Sie über die Publish[Umgebung auf die ](moderation.md)Moderationskonsole“ zugreifen können.

Beachten Sie, dass für einen Administrator alle moderierbaren Inhalte sichtbar sind, nicht nur Inhalte von der Geometrixx Engage Community-Site.

Der Suchfilter ist ein Seitenbereich, der zwischen Öffnen und Schließen umschaltet.

Abmelden.

![moderation-console-publish](assets/moderation-console-publish.png)

### Community-Moderator (#2) {#community-moderator}

Melden Sie sich als Aaron McDonald (`aaron.mcdonal@mailinator.com`), ein Community-Moderator, an und greifen Sie auf den Thread zu, indem Sie Forum auswählen und dann Mehr lesen für den Kolibri-Beitrag.

Hinweis:

* Aaron kann auf seinen eigenen Beitrag antworten, ihn löschen, bearbeiten oder ablehnen.
* Aaron kann auch andere Inhalte markieren/zulassen, antworten, löschen, bearbeiten, ablehnen.
* Aaron kann das Forum-Thema ausschneiden, um es in ein anderes Forum zu verschieben, für das er moderiert.
* Aaron kann Administration auswählen, um auf die Moderationskonsole zuzugreifen.

![community-forum-moderator](assets/community-forum-moderator.png)

Wählen Sie das Menüelement Administration aus, damit Sie über die Publish[Umgebung auf die ](moderation.md)Moderationskonsole“ zugreifen können.

Beachten Sie, dass für einen Community-Moderator nur moderierbare Inhalte von der Geometrixx Engage-Community-Site sichtbar sind.

Beachten Sie, dass der Community-Moderator dieselben Optionen wie der Administrator hat (das Bild wird mit der Suchseitenleiste umgeschaltet), aber keinen Zugriff auf andere AEM-Konsolen.

Abmelden.

![Moderator-Zugriff](assets/moderator-access.png)

### Inhaltsautor (#1) {#content-author}

Melden Sie sich als Rebekah Larsen (`rebekah.larsen@mailinator.com`) an, ein Community-Mitglied, das den Thread gestartet hat, und greifen Sie auf den Thread zu, indem Sie Forum auswählen und dann mehr für den Kolibri-Post lesen.

Hinweis:

* Rebekah kann ihren eigenen Beitrag löschen oder bearbeiten.
* Rebekah kann auch auf Inhalte reagieren oder andere Inhalte kennzeichnen.
* Rebekah kann nicht auf die Moderationskonsole zugreifen.

![community-forum-author](assets/community-forum-author.png)
