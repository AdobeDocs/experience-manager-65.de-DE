---
title: Moderieren von Community-Inhalten
seo-title: Moderieren von Community-Inhalten
description: Moderationskonzepte und -aktionen
seo-description: Moderationskonzepte und -aktionen
uuid: 5c991d3a-0037-4d78-8f91-bb62e44441fa
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 6866d209-5789-4ef9-bc3c-d644d4fb4b1c
docset: aem65
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 3%

---


# Moderieren von Community-Inhalten {#moderating-community-content}

## Überblick {#overview}

Community-Inhalte, auch als benutzergenerierte Inhalte (UGC) bezeichnet, werden erstellt, wenn ein Mitglied (der in Site-Besucher angemeldet ist) Inhalte von einer veröffentlichten Community-Site durch Interaktion mit einer der folgenden Community-Komponenten veröffentlicht:

* [Blog](/help/communities/blog-feature.md): Mitglieder veröffentlichen einen Blog-Artikel oder -Kommentar.
* [Kalender](/help/communities/calendar.md): -Mitglieder ein Ereignis oder einen Kommentar im Kalender veröffentlichen.
* [Kommentare](/help/communities/comments.md): -Mitglieder einen Kommentar oder eine Antwort auf einen Kommentar posten.

* [Forum](/help/communities/forum.md): Mitglieder posten ein neues Thema oder beantworten ein Thema.
* [Idee](/help/communities/ideation-feature.md): -Mitglieder eine Idee oder einen Kommentar posten.
* [QnA](/help/communities/working-with-qna.md): erstellen oder eine Frage beantworten.
* [Überprüfungen](/help/communities/reviews.md): -Mitglieder einen Kommentar bei der Bewertung eines Elements posten.

Die Moderation von UGC ist nützlich, um positive Beiträge zu erkennen und negative zu begrenzen (wie Spam und missbräuchliche Sprache). UGC kann aus verschiedenen Umgebung moderiert werden:

* [Community-Inhaltsspeicher](working-with-srp.md)

* [Massenmoderationskonsole](moderation.md)

   Die Moderationskonsole ist sowohl für Administratoren und [Community-Moderatoren](/help/communities/users.md) in der öffentlichen Umgebung als auch für Administratoren in der Authoring-Umgebung verfügbar. Dies ist möglich, wenn Community-Inhalte in einem [common store](/help/communities/working-with-srp.md) gespeichert werden.

* [Kontextbezogene Moderation](in-context.md)

   Die Moderation in der Umgebung &quot;Veröffentlichen&quot;kann von Administratoren und Community-Moderatoren direkt auf der Seite durchgeführt werden, auf der die Inhalte veröffentlicht wurden.

## Moderationsaktionen {#moderation-actions}

Die Aktionen, die für gepostete Inhalte (UGC) durchgeführt werden können, hängen von der Benutzeridentität und der Umgebung ab. Die folgende Tabelle verwendet die folgende Terminologie, um die verschiedenen Rollen entsprechend der Benutzeridentität zu beschreiben:

* `Admin`

   Ein Benutzer, der Mitglied der Gruppe [community-administrators](users.md) ist.

* `Moderator`

   Ein Mitglied einer [Community-Moderatoren](users.md#publishenvironmentusersandgroups)-Gruppe (hat [Moderatorberechtigungen](in-context.md#moderatorpermissions)).

* `Creator`

   Der Benutzer, der den Inhalt veröffentlicht hat.

* `Member`

   Ein angemeldeter Benutzer ohne besondere Berechtigungen.

* `Visitor`

   Ein anonymer Benutzer.

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><strong>Admin</strong></td>
   <td><strong>Moderator</strong></td>
   <td><strong>Ersteller</strong></td>
   <td><strong>Mitglied</strong></td>
   <td><strong>Besucher</strong></td>
   <td><strong>Ereignis<br /> Ausgelöst</strong></td>
   <td><strong>Vormoderiert</strong></td>
  </tr>
  <tr>
   <td><strong>Bearbeiten/<br /> Löschen</strong></td>
   <td>X</td>
   <td>X</td>
   <td>X</td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Ausschneiden</strong></td>
   <td>X</td>
   <td>X</td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Ablehnen</strong></td>
   <td>X</td>
   <td>X</td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td>X</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Schließen/<br /> Neu öffnen</strong></td>
   <td>X</td>
   <td>X</td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td>X</td>
   <td>X<br /> </td>
  </tr>
  <tr>
   <td><strong>Flag/<br /> Flag entfernen</strong></td>
   <td>X</td>
   <td>X</td>
   <td> </td>
   <td>X</td>
   <td> </td>
   <td>X</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Gastzugang</strong></td>
   <td>X</td>
   <td>X</td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td>X</td>
   <td>X</td>
  </tr>
 </tbody>
</table>

### Bearbeiten/Löschen {#edit-delete}

Nachdem ein Beitrag erstellt wurde, kann er vom Ersteller, Administrator oder Community-Moderator bearbeitet oder gelöscht werden.

Wenn UGC gelöscht wird, wird es aus dem Repository entfernt und möglicherweise nicht wiederhergestellt.

### Ausschneiden {#cut}

Administratoren oder Community-Moderatoren können ein oder mehrere Foren- oder QnA-Fragen von einem Ort zum anderen verschieben. Dies schließt von einer Community-Site zu einer anderen Community-Site ein, sofern dasselbe Mitglied auf beiden Seiten über Moderationsberechtigungen verfügt.

Durch Auswahl der Aktion &quot;Ausschneiden&quot;wird der Inhalt in die Zwischenablage kopiert. Es können mehrere Beiträge kopiert und als Gruppe an den neuen Speicherort verschoben werden.

![cutugc](assets/cutugc.png)

![putbackugc](assets/putbackugc.png)

Wenn an der anderen Stelle Inhalte in der Zwischenablage vorhanden sind, wird neben &quot;Neuer Beitrag&quot;eine Schaltfläche &quot;Einfügen&quot;angezeigt, mit der die Anzahl der eingefügten Beiträge angegeben wird. Die Schaltfläche &quot;Einfügen&quot;enthält eine Option zum Löschen der Zwischenablage, anstatt sie einzufügen.

![pasteugc](assets/pasteugc.png)

![pasteugc1](assets/pasteugc1.png)

### Ablehnen {#deny}

Ein Moderator kann verhindern, dass UGC auf der veröffentlichten Site sichtbar bleibt. Für Administratoren und Community-Moderatoren ist der Beitrag weiterhin verfügbar und wird als Spam bezeichnet.

### Schließen/Neu öffnen {#close-reopen}

Die Aktion &quot;Schließen&quot;wirkt sich auf den gesamten Diskussionstraum aus (ein Forenthema oder der erste Kommentar) und enthält alle nachfolgenden Beiträge oder Antworten.

Wenn geschlossen, sind nicht nur keine weiteren Antworten möglich, auch keine Moderationsaktionen sind zulässig.

Um Vorgänge auszuführen, muss das Thema oder der Kommentar erneut geöffnet werden.

Die Aktion &quot;Schließen/Neu öffnen&quot;kann von Administratoren oder Moderatoren der Community durchgeführt werden.

### Flag/Markierung entfernen {#flag-unflag}

Die Kennzeichnung ist eine Möglichkeit für alle angemeldeten Mitglieder, mit Ausnahme des Verfassers des Inhalts, anzugeben, dass ein Problem mit dem Inhalt eines Beitrags vorliegt. Nach der Markierung wird ein Unmarkiert-Symbol angezeigt, mit dem das gleiche Mitglied die Kennzeichnung des Inhalts aufheben kann.

Die kontextbezogene Moderation kann so konfiguriert werden, dass Mitglieder beim Kennzeichnen eines Beitrags einen Grund auswählen können. Die Liste der auswählbaren Flag-Gründe ist konfigurierbar, auch ob ein benutzerdefinierter Grund eingegeben werden kann. Der Flag-Grund wird mit dem UGC gespeichert, der Grund Trigger jedoch keine bestimmte Aktion. Nur die Anzahl der Flags Trigger eine Benachrichtigung. Gekennzeichnete Inhalte werden als solche kommentiert, sodass Moderatoren entsprechend handeln können.

Das System verfolgt alle Flaggen, die markiert wurden, und den Flaggengrund und sendet ein Ereignis, wenn der Schwellenwert erreicht wurde. Wenn die UGC von einem Community-Moderator zugelassen wird, werden diese Flags archiviert. Nach der Erlaubnis und Archivierung, wenn es nachfolgende Flaggings gibt, würden sie archiviert, als wäre es keine vorherigen Flaggings.

### Gastzugang {#allow}

Die Aktion &quot;Zulassen&quot;ist eine Option für UGC, die in einem vormoderierten System markiert, verweigert oder nicht genehmigt wurde. Mit der Aktion Zulassen werden alle gekennzeichneten oder abgelehnten/Spam-Status gelöscht und alle gekennzeichneten Daten archiviert.

## Allgemeine Moderationskonzepte {#common-moderation-concepts}

### Vormoderation {#premoderation}

Wenn UGC vormoderiert ist, wird der Beitrag erst auf der veröffentlichten Site angezeigt, nachdem er durch eine Moderationsaktion genehmigt wurde. Während der Erstellung einer [Community-Site](/help/communities/sites-console.md) aktivieren Sie das Kontrollkästchen [Inhalt ist vormoderiert](sites-console.md#moderation), um die Vormoderation für die gesamte Site zu aktivieren. Sobald Komponenten auf einer Seite platziert wurden, können Komponenten, die Moderation unterstützen, mithilfe einer Einstellung im Bearbeitungsdialogfeld für die Vormoderation konfiguriert werden:

* [](comments.md) Kommentare und  [](reviews.md)
Reviews in  **[!UICONTROL Benutzermoderation]** >  **[!UICONTROL Vormoderation]**.

* [Forum](/help/communities/forum.md),  [Ideation](/help/communities/ideation-feature.md),  [QnA](/help/communities/working-with-qna.md) und  [](/help/communities/calendar.md)
calendarin  **[!UICONTROL Einstellungen]** >  **[!UICONTROL Moderiert]**.

### Spam-Erkennung {#spam-detection}

Bei der Spam-Erkennung handelt es sich um eine Funktion der automatischen Moderation, mit der Filter unerwünschte Teile von vom Benutzer erstellten Inhalten durch Kennzeichnung als Spam löschen. Nach der Aktivierung wird anhand einer vorkonfigurierten Sammlung von Spam-Wörtern ermittelt, ob es sich bei einem vom Benutzer erstellten Inhalt um Spam handelt. Die standardmäßigen Spam-Wörter finden Sie unter

`/libs/settings/community/sites/moderation/spamdetector-conf/profiles/spam_words.txt`.

Um die standardmäßigen Spam-Wörter anzupassen oder zu erweitern, erstellen Sie jedoch einen Satz Wörter im Verzeichnis &quot;/apps&quot;entsprechend der Struktur der standardmäßigen Spam-Wörter mit [overlay](/help/communities/overlay-comments.md).

Ein benutzergenerierter Beitrag (über alle Inhaltstypen hinweg, z. B. Blogs, Foren und Kommentare), der Spam-Wörter enthält, wird mit dem Text &quot;Dieser Beitrag wurde als Spam klassifiziert&quot;über dem Beitrag markiert.

Moderator können einen solchen Beitrag sehen und denselben markieren, um die Anzeige auf der Site zu ermöglichen oder zu verweigern. Moderationsaktionen für diese Beiträge können entweder im Kontext oder über die Benutzeroberfläche für Massenmoderation durchgeführt werden.

![Spamerkennung](assets/spamdetection.png)

Gehen Sie wie folgt vor, um die Spam-Erkennungs-Engine zu aktivieren:

1. Öffnen Sie [Webkonsole](https://localhost:4502/system/console/configMgr), indem Sie `/system/console/configMgr` aufrufen.

1. Suchen Sie nach der Konfiguration **AEM Communities Auto Moderation** und bearbeiten Sie sie.
1. hinzufügen Sie den Eintrag **[!UICONTROL SpamProcess]**.

![spamprocess](assets/spamprocess.png)

>[!NOTE]
>
>Die Spam-Erkennung ist nur für das englische Gebietsschema implementiert.

### Empfindung {#sentiment}

Das Sentiment wird basierend auf der Anzahl positiver und negativer Suchbegriffe ([Watchwords](#configuringwatchwords)) in einem Beitrag (UGC) berechnet.

Die Sentiment-Analyse verwendet einen Satz vorkonfigurierter Regeln und berechnet das Sentiment der UGC. Die Standardregeln befinden sich unter: `/libs/cq/workflow/components/workflow/social/sentiments/rules.`

Der Wert, den die Regeln erzeugen, liegt zwischen 1 (alle negativen, keine positiven Wörter) und 10 (alle positiven, keine negativen Wörter). Der Sentimentwert 5 ist ein neutrales Sentiment und der Standardwert.

Die in der /libs-Komponente definierten Regeln lauten:

* Regel 1: den Wert 1 einstellen, wenn keine positiven Wörter und mindestens ein negatives Wort vorhanden sind.
* Regel 2: den Wert auf 10 setzen, wenn keine negativen Wörter vorhanden sind und mindestens ein positives Wort.
* Regel 3: den Wert 3 einstellen, wenn es mehr negative Wörter als positive Wörter gibt.
* Regel 4: den Wert 8 einstellen, wenn es mehr positive Wörter als negative Wörter gibt.

Um Regeln zu überschreiben oder hinzuzufügen, erstellen Sie einen Regelsatz im Ordner /apps, der der Struktur der Standardregeln folgt. Bearbeiten Sie die Sentimentkonfiguration, um den Speicherort der Regeln zu identifizieren.

Nach der Analyse wird das Sentiment mit dem UGC gespeichert.

In der [Massenmoderationskonsole](/help/communities/moderation.md) ist es möglich, UGC basierend darauf zu filtern und Ansicht, ob das Sentiment negativ, neutral oder positiv ist.

#### Watchwords {#watchwords}

AEM Communities stellen einen *Watchword-Analyzer* als einen Schritt im Prozess zur Bewertung von [sentiment](#sentiment) bereit. Der Beitrag zum Sentimentwert der Watchwords beruht auf einem Vergleich von negativen und positiven Watchwords, die im veröffentlichten Inhalt verwendet werden, sowie verbotenen Wörtern.

#### Sentiment und Watchwords {#configure-sentiment-and-watchwords} konfigurieren

Die Liste positiver und negativer Suchbegriffe kann wie die Sentimentregeln angepasst werden.

Die standardmäßige Liste von Watchwords kann als Eigenschaften eines Knotens in der jeweiligen Instanz eingegeben werden, ähnlich wie die Standardeinstellung oder durch Außerkraftsetzen des Standarddienstes, indem der OSGi-Dienst `sentimentprocess.name` mit der Liste von Wörtern konfiguriert wird.

Die Variable **sentimentprocess.name** kann auch geändert werden, um auf den Speicherort eines benutzerdefinierten Satzes von Sentimentregeln zu verweisen.

So konfigurieren Sie das Sentiment und die Watchwords:

* Melden Sie sich bei Ihrer Autoreninstanz als Administrator an.
* Öffnen Sie [Webkonsole](https://localhost:4502/system/console/configMgr).
* Suchen Sie nach `sentimentprocess.name`.
* Wählen Sie die Konfiguration aus, die im Bearbeitungsmodus geöffnet werden soll.

![sentimentprocess](assets/sentimentprocess.png)

* **Positive Watchwords**

   Eine kommagetrennte Liste von Wörtern, die zu einem positiven Sentiment beitragen, das die Standardwerte außer Kraft setzt. Der Standardwert ist eine leere Liste.

* **Negative Watchwords**

   Eine kommagetrennte Liste von Wörtern, die zu einem negativen Sentiment beitragen, das die Standardwerte außer Kraft setzt. Der Standardwert ist eine leere Liste.

* **Expliziter Pfad zum Watchwords-Knoten**

   Der Repository-Speicherort eines Knotens, der die standardmäßigen `positive`- und `negative`-Eigenschaften enthält, die die standardmäßigen Watchwords angeben. Der Standardwert ist `/libs/settings/community/watchwords/default`.

* **Sentimentregeln**

   Der Speicherort der Regeln zur Berechnung des Sentiments anhand positiver und negativer Watchwords. Der Standardwert ist `/libs/cq/workflow/components/workflow/social/sentiments/rules` (es ist jedoch kein Workflow mehr involviert).

Im Folgenden finden Sie ein Beispiel für einen benutzerdefinierten Eintrag für die standardmäßigen Watchwords, wenn `Explicit Path to Watchwords Node` auf `/libs/settings/community/watchwords/default` eingestellt ist.

![crxde](assets/crxde.png)

### Moderatorberechtigungen {#moderator-permissions}

Die folgenden Berechtigungen werden, wenn sie derselben Ressource zugewiesen sind, kollektiv als `moderator permissions` bezeichnet:

* `Read`
* `Modify`
* `Create`
* `Delete`
* `Replicate`

