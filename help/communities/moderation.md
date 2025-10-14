---
title: Moderationskonsole
description: Erfahren Sie, wie Administratoren und Community-Moderatoren mithilfe der Moderationskonsole auf alle benutzergenerierten Inhalte zugreifen können, für die sie die Berechtigung zur Moderation haben.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 829da16a-4083-43c1-857d-f2666b363bfc
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2028'
ht-degree: 2%

---

# Moderationskonsole {#moderation-console}

In AEM Communities ist [&#x200B; Massenmoderation von Community](/help/communities/moderate-ugc.md)Inhalten sowohl in der Authoring- als auch in der Publish-Umgebung durch Administratoren und Community-Moderatoren (als Moderatoren zugewiesene vertrauenswürdige Community-Mitglieder) möglich.

Admins und Community-Moderatoren können auch [In-Context-Moderation](/help/communities/in-context.md) in der Publish-Umgebung durchführen.

Eine Funktion aller [Community-Sites](/help/communities/sites-console.md) ist ein `Administration` Menüelement, das Benutzern zur Verfügung steht, die sich mit Administratorrechten anmelden. Der `Administration`-Link bietet Zugriff auf die Moderationskonsole.

Über die Moderationskonsole haben Admins und Community-Moderatoren Zugriff auf alle benutzergenerierten Inhalte, für die sie die Berechtigung zur Moderation haben. Wenn es erlaubt ist, mehrere Sites zu moderieren, ist es möglich, Beiträge über alle Sites hinweg anzuzeigen oder nach ausgewählten Communities-Sites zu filtern.

Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

Die Moderationskonsole unterstützt:

* Massenverarbeitung von Moderationsaufgaben.
* Suchen von benutzergenerierten Inhalten.
* Anzeigen von UGC-Details.
* Anzeigen von UGC-Autorendetails.

Nur wenn Sie als Administrator oder als Mitglied mit ` [moderator permissions](/help/communities/in-context.md#identifyingtrustedmembers)` angemeldet sind, können Moderationsaufgaben ausgeführt werden.

## Zugriff auf Publish-Umgebung {#publish-environment-access}

Der Zugriff auf die Moderationskonsole von einer veröffentlichten Community-Site erfolgt über einen Link Administration , der angezeigt wird, wenn ein Community-Moderator angemeldet ist.

![publishweretail](assets/publishweretail.png)

Durch Auswahl des Links Administration wird die Konsole Moderation angezeigt:

![moderation-console-publish](assets/moderation-console-publish.png)

## Zugriff auf die Autorenumgebung {#author-environment-access}

Gehen Sie in der Autorenumgebung wie folgt vor, um zur Moderationskonsole zu gelangen

* Wählen Sie in der globalen Navigation **[!UICONTROL Communities]** > **[!UICONTROL Moderation]** aus.

Nur wenn Sie als Administrator oder als Mitglied mit [Moderatorberechtigungen](/help/communities/in-context.md#identifyingtrustedmembers) angemeldet sind, können Moderationsaufgaben durchgeführt werden. Der einzige angezeigte Community-Inhalt ist derjenige, den das angemeldete Mitglied moderieren darf.

>[!NOTE]
>
>UGC aus der Publish-Umgebung ist in der Autoreninstanz nur sichtbar, wenn das ausgewählte SRP einen gemeinsamen Speicher implementiert. Standardmäßig ist der Speicher JSRP, was kein allgemeiner Speicher für Author und Publish ist. Weitere Informationen finden Sie unter [Community-Inhaltsspeicher](/help/communities/working-with-srp.md).

![ModerationConsoleAuthor](assets/moderationconsoleauthor.png)

## Benutzeroberfläche der Moderationskonsole {#moderation-console-ui}

Abgesehen von der linken Navigationsleiste (die auf der Autoreninstanz, aber nicht auf Publish angezeigt wird), umfasst die Benutzeroberfläche für die Moderation die folgenden Hauptbereiche:

* **[Navigationsleiste oben](#top-navigation-bar)**
* **[Symbolleiste](#toolbar)**
* **[Inhaltsbereich](#content-area)**

### Navigationsleiste oben {#top-navigation-bar}

Die obere Navigationsleiste ist für alle Konsolen konstant. Weitere Informationen finden Sie unter [Grundlegende &#x200B;](/help/sites-authoring/basic-handling.md).

### Symbolleiste {#toolbar}

Die Symbolleiste, die sich unter der oberen Navigationsleiste befindet, bietet den folgenden Umschalter auf der linken Seite:

* [Filterleiste](/help/communities/moderation.md#filterrail)
Öffnet eine Leiste, in der Sie eine Reihe von Eigenschaften auswählen können, nach denen der Inhalt gefiltert werden soll.

Die Symbolleiste, die sich unter der oberen Navigationsleiste befindet, bietet den folgenden Umschalter auf der linken Seite:

![toggleswitch](assets/toggleswitch.png)

[Filterleiste](/help/communities/moderation.md#filterrail)
öffnet eine Leiste bei Auswahl von Suchen , in der Sie auswählen können, nach welchen Eigenschaften der Inhalt gefiltert werden soll.

![filterrail](assets/filterrail.png)

### Inhaltsbereich {#content-area}

Der Inhaltsbereich enthält Informationen zu veröffentlichten benutzergenerierten Inhalten:

* UGC veröffentlicht
* Abonnentenname
* Mitglieds-Avatar
* Standort des Dienstpostens
* Wann es veröffentlicht wurde
* Anzahl der Antworten auf den Beitrag
* [Sentiment](/help/communities/moderate-ugc.md#sentiment) mit dem Beitrag verknüpft
* Sofern genehmigt, wird ein Häkchen angezeigt
* Wenn ein Anhang vorhanden ist, wird eine Büroklammer angezeigt

>[!NOTE]
> 
>Der Inhaltsbereich verfügt über einen *unendlichen Bildlauf*, d. h. Sie können so lange weiterscrollen, bis Sie das Ende des Inhalts erreicht haben. Die Symbolleiste verbleibt auch beim Scrollen an einer festen, sichtbaren Position über dem Inhaltsbereich.

### Filterleiste {#ootbfilters}

![open-filterrail](assets/open-filterrail.png)

Das Symbol des Seitenbereichs öffnet die Filterleiste. Die Filterleiste, die links neben dem Inhaltsbereich angezeigt wird, bietet verschiedene Filter, von denen sich jede sofort auf den referenzierten benutzergenerierten Inhalt auswirkt, der im Inhaltsbereich angezeigt wird.

Die Filter innerhalb jeder Kategorie **ODER** zusammen, und die Filter in verschiedenen Kategorien **UND** zusammen.

Wenn Sie beispielsweise sowohl **Frage** als auch **Antwort** überprüfen, sehen Sie Inhalte, die entweder eine **Frage** *oder* eine **Antwort** sind.

Wenn Sie jedoch **Frage** und **Ausstehend** aktivieren, sehen Sie nur Inhalte, die eine **Frage** sind und **Ausstehend**.

>[!NOTE]
>
>Community-Moderatoren können die vordefinierten Filter in der Benutzeroberfläche der Moderationskonsole mit einem Lesezeichen versehen. Da diese Filter am Ende der URL angehängt werden (als Abfragezeichenfolgen-Parameter), können Moderatoren später zu den mit Lesezeichen versehenen Filtern zurückkehren und auch diese Links freigeben.

![searchIcon](assets/searchicon.png)

Wenn die Filterleiste geöffnet ist, wird durch Klicken auf das Suchsymbol der Seitenbereich ein-/ausgeblendet. Um jedoch die Filterleiste zu schließen und nur die benutzergenerierten Inhalte anzuzeigen, klicken Sie auf das Suchsymbol und wählen Sie die Option Nur Inhalt aus.

#### Inhalts-Pfad {#content-path}

Der Inhaltspfad beschränkt den Verweis-UGC, der auf die Beiträge im angegebenen Inhalts-Repository angezeigt wird.

![content-path](assets/content-path.png)

#### Textsuche {#text-search}

Die Textsuche beschränkt den referenzierten UGC auf Beiträge, die den eingegebenen Text enthalten.

![text-search](assets/text-search.png)

#### Site {#site}

Site beschränkt den referenzierten UGC auf Beiträge auf ausgewählte Community-Sites. Wenn keine Sites markiert sind, werden alle Verweise auf UGC angezeigt.

![site-panel](assets/site-panel.png)

>[!NOTE]
>
>Wenn ein Administrator auf die Konsole für die Massenmoderation zugreift, werden alle Verweise auf benutzergenerierten Inhalt angezeigt, einschließlich der Sites, die nicht mit dem Assistenten [Site-Erstellung](/help/communities/sites-console.md) erstellt wurden, z. B. die Geometrixx-Beispiele.
>
>Wenn ein vertrauenswürdiges Community-Mitglied auf die Konsole für die Massenmoderation in Publish zugreift, werden nur Verweise auf UGC angezeigt, die für Community-Sites erstellt wurden, die das Mitglied moderieren darf. Außerdem kann er mit dem Site-Filter gefiltert werden.

#### Inhaltstyp {#content-type}

Content-Typ beschränkt den referenzierten UGC, der auf Beiträge des ausgewählten Ressourcentyps angezeigt wird. Es können einer oder mehrere der folgenden Typen ausgewählt werden. Alle Typen werden angezeigt, wenn keine ausgewählt ist.

* **Kommentar**
* **Forenthema**
* **Forumsantwort**
* **QnA-Frage**
* **QnA-Antwort**
* **Blog-Artikel**
* **Blog-Kommentar**
* **Kalenderereignis**
* **Kalenderkommentar**
* **Dateibibliotheksordner**
* **Dateibibliotheksdokument**
* **Idee**
* **Ideenkommentar**

![content-types](assets/content-types.png)

#### Zusätzliche Inhaltstypen {#additional-content-types}

So fügen Sie zusätzliche Ressourcen zum Filtern hinzu:

* Melden Sie sich bei Ihrer Autoreninstanz als Administrator an.
* Öffnen Sie [Web-Konsole](https://localhost:4502/system/console/configMgr).
* Suchen Sie `AEM Communities Moderation Dashboard Filters`.
* Wählen Sie die Konfiguration aus, damit Sie im Bearbeitungsmodus öffnen können.
* Geben Sie den Ressourcentyp einer Komponente ein, nach der gefiltert werden soll:

   * Um beispielsweise nach enthaltenen Abstimmungskomponenten zu filtern, geben Sie Folgendes ein:

     `Voting=social/tally/components/hbs/voting`

  ![additional-contentType](assets/additional-contenttype.png)

* Wählen Sie „Speichern“ aus.
* Aktualisieren Sie die Communities - Moderationskonsole.

Das Ergebnis ist ein neuer auswählbarer Filter für `Voting` unter der `Content Type` Filtergruppe.

Wenn dieser Filter ausgewählt ist, zeigt der Inhalt des Dashboards benutzergenerierten Inhalt an, der mit einem der eingegebenen Ressourcentypen übereinstimmt.

#### Status {#status}

Der Status beschränkt den referenzierten UGC auf Beiträge mit dem ausgewählten Status, der einen oder mehrere der folgenden Status aufweisen kann: „Ausstehend“, „Genehmigt“, „Abgelehnt“ oder „Geschlossen“, „Entwurf“ oder „Geplant für Blog-Artikel“ und „Beantwortet“ oder „Nicht beantwortet für Fragen zur QnA“. Wenn keine ausgewählt ist, werden alle angezeigt.

>[!NOTE]
>
>Wenn nur der Status Nicht beantwortet ausgewählt ist, sieht der Moderator den gesamten Inhalt (für alle Inhaltstypen) mit Ausnahme der beantworteten Fragen. Der Grund dafür ist, dass die Eigenschaft, die für die beantwortete Frage verantwortlich ist, nicht vorhanden ist, wenn es nicht beantwortete Fragen und andere Inhalte wie Forumsthema, Blog-Artikel oder Kommentare gibt.

![status](assets/statuses.png)

#### Kennzeichnung {#flagging}

Durch Markierung wird der referenzierte benutzergenerierte Inhalt auf Beiträge beschränkt, die markiert oder ausgeblendet sind.

Sobald ein Inhaltselement gekennzeichnet wurde, bleibt es gekennzeichnet, bis Sie das Flag für dieses einzelne Inhaltselement aufheben, indem Sie erneut auf die Schaltfläche **Flag** klicken. Es gibt keine Kennzeichnungsstufen wie „wichtig“ oder „Nachverfolgung“.

![Flag](assets/flagging.png)

#### Mitglieder {#members}

Members beschränkt den referenzierten UGC, der auf den UGC angezeigt wird, der anhand des eingegebenen Members-Namens veröffentlicht wurde.

![Mitglieder](assets/members.png)

#### Veröffentlichungszeitraum {#posted-in-the-last}

Veröffentlicht Im letzten Limit zeigt der referenzierte benutzergenerierte Inhalt Beiträge an, die in der letzten Stunde, dem letzten Tag, der letzten Woche, dem letzten Monat oder dem letzten Jahr veröffentlicht wurden.

![gepostet-last](assets/posted-last.png)

#### Empfindung {#sentiment}

[Sentiment](/help/communities/moderate-ugc.md#sentiment) begrenzt den referenzierten benutzergenerierten Inhalt auf Beiträge mit einem Sentimentwert, der entweder positiv, negativ oder neutral ist.

![Gefühl](assets/sentiment.png)

## Benutzerdefinierte Filter {#custom-filters}

Zusätzlich zu den vordefinierten Filtern in der [Filterleiste](/help/communities/moderation.md#ootbfilters) können der Benutzeroberfläche für die Moderation zusätzliche benutzerdefinierte Filter für Metadaten hinzugefügt werden. Entwickler können den Beispiel-Code in GitHub verwenden, um die vorhandenen Filter der Moderations-Benutzeroberfläche zu erweitern.

![custom-tag-filter](assets/custom-tag-filter.png)

Das [Beispielprojekt](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/main/aem-communities-moderation-filter) auf GitHub implementiert den Tag-Filter, um die UGC-Liste danach zu filtern, ob die spezifischen Tags auf benutzergenerierte Inhalte angewendet werden. Sie können dem Beispiel-Code folgen und analoge Filter für andere ähnliche UGC-Metadatenfelder erstellen.

So installieren Sie das Beispiel für den Tag-Filter:

1. Öffnen Sie die Instanz Package Manager auf AEM-Autoreninstanz (`https://[aem-author]:4502/crx/packmgr/index.jsp`) und AEM Publish-Instanz (`https://[aem-publish]:4503/crx/packmgr/index.jsp`).
1. Erstellen Sie das Paket `com.adobe.social.sample.moderation.filter.ui.apps-1.0-SNAPSHOT.zip` aus GitHub-Code und installieren und aktivieren Sie es.
1. Öffnen Sie die Bundles-Konsole auf der AEM-Autoreninstanz (`https://[aem-author]:4502/system/console/bundles`) und der AEM-Publish-Instanz (`https://[aem-publish]:4503/system/console/bundles`).
1. Erstellen Sie das Paket (`[com](https://sample-moderation-filter.com/).adobe.social.sample.moderation.filter.core-1.0-SNAPSHOT.jar`) von GitHub und installieren und aktivieren Sie es.
1. Wechseln Sie zum Knoten **/apps/social/moderation/facets** in der AEM-Autoreninstanz (`https://[aem-author]:4502/crx/de/index.jsp#/apps/social/moderation/facets`) oder der AEM-Publish-Instanz (`https://[aem-publish]:4502/crx/de/index.jsp#/apps/social/moderation/facets`).
1. Fügen Sie einen technischen Benutzer **community-utility-reader** mit `jcr:read` Berechtigungen hinzu.

So stellen Sie die benutzerdefinierten Filter auf vorhandenen Community-Sites bereit:

1. `Clientlibs` vorhandener `/content/we-retail/us/en/community/moderation/shell3/jcr:content/head/clientlibs.` für die Moderationsseite bearbeiten

   * Neue `cq.social.hbs.moderation.v2.` hinzufügen

1. Wechseln Sie zu `/content/we-retail/us/en/community/moderation/shell3/jcr:content/rails/searchWell/items/filters.`.

   * Auf neue `sling:resourceType = social/moderation/v2/filters.` festlegen

1. Rufen Sie `/content/we-retail/us/en/community/moderation/shell3/jcr:content/views/content/items/modcontainer` auf.

   * Auf neue `sling:resourceType = social/moderation/v2/modcontainer` festlegen.

## Moderationsaktionen {#moderation-actions}

[Moderationsaktionen](/help/communities/moderate-ugc.md#moderation-actions) können für eine oder mehrere Auswahlen im Inhaltsbereich oder beim Anzeigen von Inhaltsdetails ausgeführt werden.

Um die Masse der Beiträge zu moderieren, klicken Sie im Inhaltsbereich auf das Symbol Auswählen (![selecticon](assets/selecticon.png)) auf einem Beitrag, der angezeigt wird, wenn Sie den Mauszeiger darüber bewegen (Desktop) oder einen Finger auf den Beitrag drücken und halten (Mobilgerät). Auf diese Weise können Sie in den Mehrfachauswahl-Modus wechseln und durch einfaches Klicken auf die folgenden Beiträge die Massenmoderation übernehmen. Verwenden Sie die Schaltflächen, die auf der Symbolleiste angezeigt werden, um Moderationsaktionen für die ausgewählten Beiträge durchzuführen. Bei allen Aktionen wird zur Bestätigung aufgefordert.

Um einen einzelnen Beitrag im Inhaltsbereich zu moderieren, halten Sie den Mauszeiger darüber (Desktop) oder drücken und halten Sie einen Finger auf dem Beitrag (Mobile), sodass die Schaltflächen auf dem Beitrag angezeigt werden. Bei der Bearbeitung eines einzelnen Inhaltsdetails wird nur eine Löschaktion zur Bestätigung aufgefordert.

### Moderieren mehrerer Beiträge {#moderating-multiple-posts}

Rufen Sie den Massenauswahlmodus auf, indem Sie auf das `Select` eines Beitrags klicken:

![select-icon](assets/select-icon.png)

Um den Massenauswahlmodus zu beenden, klicken Sie in der Symbolleiste auf das Symbol Abbrechen (x):

Die Moderationsaktionen, die für mehrere Beiträge ausgeführt werden können, sind:

* Ablehnen
* Löschen
* Beiträge schließen/erneut öffnen

Die Symbole, die diese Aktionen ermöglichen, werden nur auf der Symbolleiste angezeigt, wenn mehrere Beiträge ausgewählt sind.

![bulkmoderat](assets/bulkmoderate.png)

### Moderieren eines einzelnen Beitrags {#moderating-a-single-post}

Im Einzelauswahlmodus können Sie:

* Zeigen Sie Benutzerdetails an, indem Sie den Namen des Benutzers auswählen.
* Zeigen Sie den Beitrag im Kontext an, indem Sie den Link zum Beitrag auswählen.
* [Antwort](#reply)
* [Zulassen](#allow)
* [Ablehnen](#deny)
* [Löschen](#delete)
* [Schließen](#close)
* Anzeigen [Moderationsverlauf](#moderation-history)
* [Details anzeigen](#viewdetails)

Auf der Kartenansicht über den Aktionssymbolen für die Moderation ist der Text des Beitrags vorhanden und unten sind Daten, die Folgendes angeben:

* Gibt an, ob Antworten vorliegen, und falls ja, wie viele Antworten zuvor eingegangen sind
* Wenn sie gekennzeichnet wurde
* Wenn er genehmigt wurde
* Wann der UGC veröffentlicht wurde

![singleSelectMode](assets/singleselectmode.png)

#### Antwort {#reply}

![Antwort](assets/reply.png)

Bei der Arbeit mit einem einzelnen Beitrag wird ein Antwortsymbol angezeigt, wenn der UGC-Typ Antworten unterstützt und so konfiguriert ist, dass Antworten zulässig sind.

#### Zulassen {#allow}

![allow](assets/allow.png)

Bei der Arbeit mit einem einzelnen Beitrag wird das Symbol Zulassen angezeigt, wenn der Beitrag entweder gekennzeichnet oder abgelehnt wurde. Wenn Sie auf „Zulassen“ klicken, werden alle Flags gelöscht.

#### Ablehnen {#deny}

![Ablehnen](assets/deny.png)

Die **Verweigern**-Moderationsaktion ist nur für moderierte Inhalte verfügbar und wird nicht für nicht moderierte Inhalte angezeigt, außer im Mehrfachauswahlmodus.

Nicht moderierte Inhalte werden immer genehmigt.

Inhalte, die moderiert werden, werden zunächst in den Status „Ausstehend“ versetzt und können später zur Genehmigung oder Ablehnung geändert werden.

Inhalte, die den Status „Ausstehend“ verlassen, können nie in einen ausstehenden Status zurückkehren. Inhalte, die als genehmigt oder abgelehnt gekennzeichnet sind, können jederzeit in einen anderen Status geändert werden.

#### Löschen {#delete}

![Löschen](assets/delete.png)

Im Einzelauswahl- oder Massenmodus können Sie Elemente auswählen und löschen. Die Löschaktion führt zu einem Bestätigungsdialogfeld. Nach dem Löschen verschwinden diese Elemente sofort aus dem Inhaltsbereich. **Nachdem der benutzergenerierte Inhalt gelöscht wurde, wird er dauerhaft aus dem Repository entfernt und kann später nicht mehr abgerufen werden**.

#### Schließen {#close}

![Schließen](assets/close.png)

Bei der Arbeit mit einem einzelnen Beitrag wird ein Schließen -Symbol angezeigt, wenn der Typ benutzergenerierter Benutzer (UGC) die Möglichkeit unterstützt, weitere Beiträge für diese Ressource zu verhindern.

#### Moderationsverlauf {#moderation-history}

![Moderation](assets/moderation.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, wird ein Symbol „Moderationsverlauf“ angezeigt, wenn Sie den Mauszeiger darüber bewegen. Wenn Sie das Symbol auswählen, wird ein Bereich mit einem Verlauf der Aktionen angezeigt, die in Bezug auf den UGC-Beitrag durchgeführt wurden.

Um zur Inhaltsbereichsanzeige mehrerer benutzergenerierter Beiträge zurückzukehren, wählen Sie das X in der oberen rechten Ecke des Detailbereichs der Ansicht aus.

Zum Beispiel:

![Moderation-History](assets/moderation-history.png)

#### Details anzeigen {#view-detail}

![Ansicht](assets/view.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, können weitere Details angezeigt werden, indem Sie den UGC im Detail-Modus öffnen.

Bewegen Sie dazu den Mauszeiger über den Beitrag, um das `View Detail` anzuzeigen, und wählen Sie ihn aus, um ein Bedienfeld mit weiteren Details zum Beitrag anzuzeigen.

Um zur Inhaltsbereichsanzeige mehrerer benutzergenerierter Beiträge zurückzukehren, wählen Sie das X in der oberen rechten Ecke des Detailbereichs der Ansicht aus.

Zum Beispiel:

![view1](assets/view1.png)
