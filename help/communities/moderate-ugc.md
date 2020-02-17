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
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Moderieren von Community-Inhalten{#moderating-community-content}

## Überblick {#overview}

Community-Inhalte, auch als benutzergenerierte Inhalte (UGC) bezeichnet, werden erstellt, wenn ein Mitglied (der Besucher der Site ist angemeldet) Inhalte von einer veröffentlichten Community-Site durch Interaktion mit einer der folgenden Community-Komponenten veröffentlicht:

* [blog](/help/communities/blog-feature.md) : Mitglieder posten Blog-Artikel oder -Kommentare
* [Kalender](/help/communities/calendar.md) : Mitglieder posten ein Kalenderereignis oder einen Kommentar
* [Kommentare](/help/communities/comments.md) : Mitglieder einen Kommentar oder eine Antwort auf einen Kommentar

* [Forum](/help/communities/forum.md) : Mitglieder posten ein neues Thema oder Antworten auf ein Thema
* [Idee](/help/communities/ideation-feature.md) : Mitglieder posten eine Idee oder einen Kommentar
* [QnA](/help/communities/working-with-qna.md) : Mitglieder erstellen eine Frage oder beantworten eine Frage
* [Überprüfungen](/help/communities/reviews.md) : Mitglieder posten einen Kommentar, wenn sie ein Element bewerten

Die Moderation von UGC ist nützlich, um positive Beiträge zu erkennen und negative zu begrenzen (wie Spam und missbräuchliche Sprache). UGC kann aus verschiedenen Umgebungen moderiert werden: [](/help/communities/working-with-srp.md)

* [Massenmoderationskonsole](/help/communities/moderation.md)Die Moderationskonsole ist sowohl für Administratoren und [Community-Moderatoren](/help/communities/users.md) in der öffentlichen Umgebung als auch für Administratoren in der Autorenumgebung zugänglich. Dies ist möglich, wenn Community-Inhalte in einem [gemeinsamen Store](/help/communities/working-with-srp.md)gespeichert werden.

* [Die kontextbezogene Moderation](/help/communities/in-context.md)in der Veröffentlichungsumgebung kann von Administratoren und Community-Moderatoren direkt auf der Seite durchgeführt werden, auf der der Inhalt veröffentlicht wurde.

## Moderationsaktionen {#moderation-actions}

Die Aktionen, die an veröffentlichten Inhalten (UGC) durchgeführt werden können, hängen von der Benutzeridentität und der Umgebung ab. Die folgende Tabelle verwendet die folgende Terminologie, um die verschiedenen Rollen entsprechend der Benutzeridentität zu beschreiben:

* `Admin`
ein Benutzer, der Mitglied der [Community-Administratoren](/help/communities/users.md) -Gruppe ist

* `Moderator`
Mitglied einer Gruppe von [Moderatoren](/help/communities/users.md#publishenvironmentusersandgroups) in einer Community (hat [Moderatorenberechtigungen](/help/communities/in-context.md#moderatorpermissions))

* `Creator`
dem Benutzer, der den Inhalt veröffentlicht hat

* `Member`
einem angemeldeten Benutzer ohne besondere Berechtigungen

* `Visitor`
ein anonymer Benutzer

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><strong>Admin</strong></td>
   <td><strong>Moderator</strong></td>
   <td><strong>Ersteller</strong></td>
   <td><strong>Mitglied</strong></td>
   <td><strong>Besucher</strong></td>
   <td><strong>Ereignis<br /> ausgelöst</strong></td>
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
   <td><strong>Markierung/<br /> Markierung entfernen</strong></td>
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

![cutugc](assets/cutugc.png) ![putbackugc](assets/putbackugc.png)

Wenn an der anderen Stelle Inhalte in der Zwischenablage vorhanden sind, wird neben &quot;Neuer Beitrag&quot;eine Schaltfläche &quot;Einfügen&quot;angezeigt, mit der die Anzahl der eingefügten Beiträge angegeben wird. Die Schaltfläche &quot;Einfügen&quot;enthält eine Option zum Löschen der Zwischenablage, anstatt sie einzufügen.

![chlimage_1-28](assets/chlimage_1-28.png) ![chlimage_1-29](assets/chlimage_1-29.png)

### Ablehnen {#deny}

Ein Moderator kann verhindern, dass UGC auf der veröffentlichten Site sichtbar bleibt. Für Administratoren und Community-Moderatoren ist der Beitrag weiterhin verfügbar und wird als Spam bezeichnet.

### Schließen/Neu öffnen {#close-reopen}

Die Aktion &quot;Schließen&quot;wirkt sich auf den gesamten Diskussionstraum aus (ein Forenthema oder der erste Kommentar) und enthält alle nachfolgenden Beiträge oder Antworten.

Wenn geschlossen, sind nicht nur keine weiteren Antworten möglich, auch keine Moderationsaktionen sind zulässig.

Um Vorgänge auszuführen, muss das Thema oder der Kommentar erneut geöffnet werden.

Die Aktion &quot;Schließen/Neu öffnen&quot;kann von Administratoren oder Moderatoren der Community durchgeführt werden.

### Markierung/Markierung entfernen {#flag-unflag}

Die Kennzeichnung ist eine Möglichkeit für alle angemeldeten Mitglieder, mit Ausnahme des Verfassers des Inhalts, anzugeben, dass ein Problem mit dem Inhalt eines Beitrags vorliegt. Nach der Markierung wird ein Unmarkiert-Symbol angezeigt, mit dem das gleiche Mitglied die Kennzeichnung des Inhalts aufheben kann.

Die kontextbezogene Moderation kann so konfiguriert werden, dass Mitglieder beim Kennzeichnen eines Beitrags einen Grund auswählen können. Die Liste der auswählbaren Flag-Gründe ist konfigurierbar, auch ob ein benutzerdefinierter Grund eingegeben werden kann. Der Flag-Grund wird mit dem UGC gespeichert, der Grund löst jedoch keine bestimmte Aktion aus. Nur die Anzahl der Flags löst eine Benachrichtigung aus. Gekennzeichnete Inhalte werden als solche kommentiert, sodass Moderatoren entsprechend handeln können.

Das System verfolgt alle Flaggen, die markiert wurden, und den Flag-Grund und sendet ein Ereignis, wenn der Schwellenwert erreicht wurde. Wenn die UGC von einem Community-Moderator zugelassen wird, werden diese Flags archiviert. Nach der Erlaubnis und Archivierung, wenn es nachfolgende Flaggings gibt, würden sie archiviert, als wäre es keine vorherigen Flaggings.

### Gastzugang {#allow}

Die Aktion &quot;Zulassen&quot;ist eine Option für UGC, die in einem vormoderierten System markiert, verweigert oder nicht genehmigt wurde. Mit der Aktion Zulassen werden alle gekennzeichneten oder abgelehnten/Spam-Status gelöscht und alle gekennzeichneten Daten archiviert.

## Allgemeine Moderationskonzepte {#common-moderation-concepts}

### Vormoderation {#premoderation}

Wenn UGC vormoderiert ist, wird der Beitrag erst auf der veröffentlichten Site angezeigt, nachdem er durch eine Moderationsaktion genehmigt wurde. Während der Erstellung einer [Community-Site](/help/communities/sites-console.md)`[Content is Premoderated](/help/communities/sites-console.md#moderation)` wird durch Aktivieren des Kontrollkästchens die Vormoderation für die gesamte Site aktiviert. Sobald Komponenten auf einer Seite platziert wurden, können Komponenten, die Moderation unterstützen, mithilfe einer Einstellung im Bearbeitungsdialogfeld für die Vormoderation konfiguriert werden:

* [Kommentare](/help/communities/comments.md) und [Rezensionen](/help/communities/reviews.md)auf der Registerkarte &quot; **Benutzermoderation** &quot;aktivieren Sie &quot; **Vormoderation&quot;.**
* [forum](/help/communities/forum.md), [ideation](/help/communities/ideation-feature.md), [QnA](/help/communities/working-with-qna.md)und [Kalender](/help/communities/calendar.md)auf der Registerkarte **Einstellungen** , aktivieren Sie **Moderiert**

### Spam-Erkennung {#spam-detection}

Die Spam-Erkennung ist eine Funktion der automatischen Moderation, die unerwünschte Teile von vom Benutzer erstellten Inhalten durch Kennzeichnung als Spam herausfiltert. Nach der Aktivierung wird anhand einer vorkonfigurierten Sammlung von Spam-Wörtern ermittelt, ob es sich bei einem vom Benutzer erstellten Inhalt um Spam handelt. Die standardmäßigen Spam-Wörter finden Sie unter

`/libs/settings/community/sites/moderation/spamdetector-conf/profiles/spam_words.txt`.

Um die standardmäßigen Spam-Wörter anzupassen oder zu erweitern, erstellen Sie jedoch einen Satz Wörter im Verzeichnis /apps, die der Struktur der standardmäßigen Spam-Wörter durch [Überlagerung](/help/communities/overlay-comments.md)folgen.

Ein benutzergenerierter Beitrag (über alle Inhaltstypen hinweg, z. B. Blogs, Foren und Kommentare), der Spam-Wörter enthält, wird mit dem Text &quot;Dieser Beitrag wurde als Spam klassifiziert&quot;über dem Beitrag markiert.

Moderator können einen solchen Beitrag sehen und denselben markieren, um die Anzeige auf der Site zu ermöglichen oder zu verweigern. Moderationsaktionen für diese Beiträge können entweder im Kontext oder über die Benutzeroberfläche für Massenmoderation durchgeführt werden.

![Spamerkennung](assets/spamdetection.png)

Gehen Sie wie folgt vor, um die Spam-Erkennung zu aktivieren:

1. Öffnen Sie [Web Console](https://localhost:4502/system/console/configMgr), indem Sie zu /system/console/configMgr navigieren.

1. Suchen Sie die Konfiguration für die automatische Moderation **in** AEM Communities und bearbeiten Sie sie.
1. Fügen Sie den Eintrag &quot;SpamProcess&quot;hinzu.

![spamprocess](assets/spamprocess.png)

>[!NOTE]
>
>Die Spam-Erkennung ist nur für das englische Gebietsschema implementiert.

### Empfindung {#sentiment}

Das Sentiment wird basierend auf der Anzahl positiver und negativer Suchbegriffe ([Watchwords](#configuringwatchwords)) in einem Beitrag (UGC) berechnet.

Die Sentimentanalyse verwendet einen Satz vorkonfigurierter Regeln und berechnet das Sentiment der UGC. Die Standardregeln befinden sich unter `/libs/cq/workflow/components/workflow/social/sentiments/rules.`

Der Wert, den die Regeln erzeugen, liegt zwischen 1 (alle negativen, keine positiven Wörter) und 10 (alle positiven, keine negativen Wörter). Der Sentimentwert 5 ist ein neutrales Sentiment und der Standardwert.

Die in der /libs-Komponente definierten Regeln lauten:

* Artikel 1: den Wert auf 1 setzen, wenn keine positiven Wörter und mindestens ein negatives Wort vorhanden sind
* Artikel 2: den Wert auf 10 setzen, wenn keine negativen Wörter vorhanden sind und mindestens ein positives Wort
* Artikel 3: Wert 3 einstellen, wenn es mehr negative Wörter als positive Wörter gibt
* Artikel 4: Wert auf 8 setzen, wenn positivere Wörter als negative Wörter vorhanden sind

Um Regeln zu überschreiben oder hinzuzufügen, erstellen Sie einen Regelsatz im Ordner /apps, der der Struktur der Standardregeln folgt. Bearbeiten Sie die Sentimentkonfiguration, um den Speicherort der Regeln zu identifizieren.

Nach der Analyse wird das Sentiment mit dem UGC gespeichert.

In der [Massen-Moderationskonsole](/help/communities/moderation.md)ist es möglich, UGC basierend darauf zu filtern und anzuzeigen, ob das Sentiment negativ, neutral oder positiv ist.

#### Watchwords {#watchwords}

AEM Communities bietet einen *watchword-Analyzer *als einen Schritt im Prozess zur Bewertung des [Sentiments](#sentiment). Der Beitrag zum Sentimentwert der Watchwords beruht auf einem Vergleich von negativen und positiven Watchwords, die im veröffentlichten Inhalt verwendet werden, sowie verbotenen Wörtern.

#### Sentiment und Watchwords konfigurieren {#configure-sentiment-and-watchwords}

Die Liste der positiven und negativen Suchbegriffe kann wie die Sentimentregeln angepasst werden.

Die Standardliste der Watchwords kann als Eigenschaften einer Node in der jeweiligen Liste eingegeben werden, ähnlich wie die Standardeinstellung, oder durch Außerkraftsetzen der Standardeinstellung, indem der OSGi-Dienst `sentimentprocess.name`mit der Wortliste konfiguriert wird.

Die Datei **sentimentprocess.name** kann auch geändert werden, um auf den Speicherort eines benutzerdefinierten Satzes von Sentimentregeln zu verweisen.

So konfigurieren Sie das Sentiment und die Watchwords:

* in einer Autoreninstanz
* anmelden als Administrator
* open [Web Console](https://localhost:4502/system/console/configMgr)
* suchen `sentimentprocess.name`
* Wählen Sie die Konfiguration aus, die im Bearbeitungsmodus geöffnet werden soll

![sentimentprocess](assets/sentimentprocess.png)

* **Positive Watchwords** Eine kommagetrennte Liste von Wörtern, die zu einem positiven Sentiment beitragen, das die Standardwerte außer Kraft setzt. Standard ist eine leere Liste.

* **Negative Watchwords** Eine kommagetrennte Liste von Wörtern, die zu einem negativen Sentiment beitragen, das die Standardwerte außer Kraft setzt. Standard ist eine leere Liste.

* **Expliziter Pfad zum Watchwords-Knoten** Der Repository-Speicherort eines Knotens, der Standard- `positive` und `negative` -Eigenschaften enthält, die die standardmäßigen Watchwords angeben. Der Standardwert ist `/libs/settings/community/watchwords/default`.

* **Sentimentregeln** Der Speicherort der Regeln für die Berechnung des Sentiments anhand positiver und negativer Watchwords im Repository. Der Standardwert ist `/libs/cq/workflow/components/workflow/social/sentiments/rules` (es ist jedoch kein Workflow mehr beteiligt).

Im Folgenden finden Sie ein Beispiel für einen benutzerdefinierten Eintrag für die standardmäßigen Watchwords, wenn `Explicit Path to Watchwords Node` auf `/libs/settings/community/watchwords/default`.

![crxde](assets/crxde.png)

### Moderatorberechtigungen {#moderator-permissions}

Die folgenden Berechtigungen werden zusammen als **`moderator permissions`** bezeichnet, wenn sie derselben Ressource zugewiesen sind:

* `Read`
* **`Modify`**
* `Create`
* `Delete`
* `Replicate`

