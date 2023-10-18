---
title: Moderationskonsole
description: Erfahren Sie, wie Administratoren und Community-Moderatoren über die Moderationskonsole auf alle benutzergenerierten Inhalte zugreifen können, für die sie über die Berechtigung zum Moderieren verfügen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 829da16a-4083-43c1-857d-f2666b363bfc
source-git-commit: 00b6f2f03470aca7f87717818d0dfcd17ac16bed
workflow-type: tm+mt
source-wordcount: '2038'
ht-degree: 4%

---

# Moderationskonsole {#moderation-console}

In AEM Communities Bulk [Moderation von Community-Inhalten](/help/communities/moderate-ugc.md) ist sowohl in der Autoren- als auch in der Veröffentlichungsumgebung durch Administratoren und Community-Moderatoren möglich (vertrauenswürdige Community-Mitglieder, die als Moderatoren zugewiesen sind).

Administratoren und Community-Moderatoren können auch [kontextbezogene Moderation](/help/communities/in-context.md) in der Veröffentlichungsumgebung.

Eine Funktion von allen [Community-Sites](/help/communities/sites-console.md) ist `Administration` Menüelement, das Benutzern zur Verfügung steht, die sich mit Administratorrechten anmelden. Die `Administration` -Link bietet Zugriff auf die Moderationskonsole.

In der Moderationskonsole haben Administratoren und Community-Moderatoren Zugriff auf alle benutzergenerierten Inhalte (UGC), deren Moderation sie zulassen können. Wenn es zulässig ist, mehrere Sites zu moderieren, können Sie Beiträge auf allen Sites anzeigen oder nach ausgewählten Communities-Sites filtern.

Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

Die Moderationskonsole unterstützt:

* Massenmäßige Durchführung von Moderationsaufgaben.
* Suchen nach benutzergenerierten Inhalten.
* Anzeigen von UGC-Details.
* Anzeigen von UGC-Autorendetails.

Nur bei Anmeldung als Administrator oder als Mitglied mit ` [moderator permissions](/help/communities/in-context.md#identifyingtrustedmembers)`, können Moderationsaufgaben ausgeführt werden.

## Zugriff auf Veröffentlichungsumgebung {#publish-environment-access}

Der Zugriff auf die Moderationskonsole von einer veröffentlichten Community-Site aus erfolgt über einen Link &quot;Administration&quot;, der angezeigt wird, wenn ein Community-Moderator angemeldet ist.

![publishweretail](assets/publishweretail.png)

Über den Link Administration wird die Moderationskonsole angezeigt:

![moderation-console-publish](assets/moderation-console-publish.png)

## Zugriff auf Autorenumgebung {#author-environment-access}

In der Autorenumgebung, um die Moderationskonsole zu erreichen

* Wählen Sie in der globalen Navigation die Option **[!UICONTROL Communities]** > **[!UICONTROL Moderation]**.

Nur bei Anmeldung als Administrator oder als Mitglied mit [Moderatorberechtigungen](/help/communities/in-context.md#identifyingtrustedmembers), können Moderationsaufgaben ausgeführt werden. Der einzige angezeigte Community-Inhalt ist derjenige, den das angemeldete Mitglied moderieren darf.

>[!NOTE]
>
>UGC aus der Veröffentlichungsumgebung ist nur in der Autoreninstanz sichtbar, wenn das ausgewählte SRP einen gemeinsamen Speicher implementiert. Beispielsweise ist der Speicher standardmäßig JSRP, der kein gängiger Speicher für die Autoren- und Veröffentlichungsinstanz ist. Weitere Informationen finden Sie unter [Community-Inhaltsspeicher](/help/communities/working-with-srp.md).

![moderationconsoleauthor](assets/moderationconsoleauthor.png)

## Benutzeroberfläche der Moderationskonsole {#moderation-console-ui}

Wenn Sie die linke Navigationsleiste (die auf der Autoreninstanz, aber nicht auf der Veröffentlichungsinstanz angezeigt wird) beiseite lassen, hat die Moderationsbenutzeroberfläche die folgenden Hauptbereiche:

* **[Navigationsleiste oben](#top-navigation-bar)**
* **[Symbolleiste](#toolbar)**
* **[Inhaltsbereich](#content-area)**

### Navigationsleiste oben {#top-navigation-bar}

Die Navigationsleiste am oberen Bildschirmrand ist für alle Konsolen konstant. Weitere Informationen finden Sie unter [Grundlegende Handhabung](/help/sites-authoring/basic-handling.md).

### Symbolleiste {#toolbar}

Die Symbolleiste, die sich unter der oberen Navigationsleiste befindet, stellt den folgenden Umschalter auf der linken Seite bereit:

* [Filterleiste](/help/communities/moderation.md#filterrail)
öffnet eine Leiste, in der die Eigenschaften zum Filtern des Inhalts ausgewählt werden können.

Die Symbolleiste, die sich unter der oberen Navigationsleiste befindet, stellt den folgenden Umschalter auf der linken Seite bereit:

![toggleswitch](assets/toggleswitch.png)

[Filterleiste](/help/communities/moderation.md#filterrail)
öffnet bei Auswahl von Suche eine Leiste, in der die Eigenschaften zum Filtern des Inhalts ausgewählt werden können.

![Filterleiste](assets/filterrail.png)

### Inhaltsbereich {#content-area}

Der Inhaltsbereich enthält Informationen für veröffentlichte UGC:

* UGC veröffentlicht
* Name des Mitglieds
* Mitglied Avatar
* Position des Beitrags
* Zeitpunkt der Veröffentlichung
* Anzahl der Antworten auf den Beitrag
* [Sentiment](/help/communities/moderate-ugc.md#sentiment) mit dem Beitrag verknüpft ist
* Bei Genehmigung wird ein Häkchen angezeigt
* Wenn eine Anlage vorhanden ist, wird eine Papierklammer angezeigt

>[!NOTE]
> 
>Der Inhaltsbereich verfügt über eine *unendlicher Bildlauf*, sodass Sie mit dem Scrollen fortfahren können, bis Sie das Ende des Inhalts erreicht haben. Die Symbolleiste bleibt auch beim Scrollen an einer festen, sichtbaren Position über dem Inhaltsbereich.

### Filterleiste {#ootbfilters}

![open-filterrail](assets/open-filterrail.png)

Das Symbol für das seitliche Bedienfeld öffnet die Filterleiste. Die Filterleiste, die links neben dem Inhaltsbereich angezeigt wird, bietet verschiedene Filter, von denen jeder unmittelbare Auswirkungen auf die referenzierte benutzergenerierte Inhalte hat, die im Inhaltsbereich angezeigt werden.

Die Filter in jeder Kategorie sind **ODER**&quot;d zusammen&quot;und die Filter in verschiedenen Kategorien sind **UND** Ich würde zusammen gehen.

Wenn Sie beispielsweise beide **Frage** und **Antwort**, sehen Sie Inhalt, der entweder **Frage** *oder* ein **Antwort**.

Wenn Sie jedoch **Frage** und **Ausstehend**, sehen Sie nur Inhalte, die **Frage** und **Ausstehend**.

>[!NOTE]
>
>Community-Moderatoren können die vordefinierten Filter in der Benutzeroberfläche der Moderationskonsole mit einem Lesezeichen versehen. Da diese Filter an das Ende der URL angehängt werden (als Abfragezeichenfolgenparameter), können Moderatoren später zu den mit Lesezeichen versehenen Filtern zurückkehren und diese Links auch freigeben.

![searchicon](assets/searchicon.png)

Wenn die Filterleiste geöffnet ist, wird das seitliche Bedienfeld durch das Symbol Suchen geschlossen. Um jedoch die Filterleiste zu schließen und nur den benutzergenerierten Inhalt anzuzeigen, klicken Sie auf das Symbol Suchen und wählen Sie die Option Nur Inhalt .

#### Inhalts-Pfad {#content-path}

Der Inhaltspfad beschränkt die angezeigte Referenz-UGC auf die im angegebenen Inhalts-Repository platzierten Beiträge.

![content-path](assets/content-path.png)

#### Textsuche {#text-search}

Die Textsuche beschränkt die Anzeige des referenzierten benutzergenerierten Inhalts auf Beiträge, die den eingegebenen Text enthalten.

![text-search](assets/text-search.png)

#### Site {#site}

Die Site beschränkt die Anzeige des referenzierten benutzergenerierten Inhalts auf Beiträge auf ausgewählten Community-Sites. Wenn keine Sites aktiviert sind, werden alle Verweise auf UGC angezeigt.

![site-panel](assets/site-panel.png)

>[!NOTE]
>
>Wenn ein Administrator auf die Massen-Moderationskonsole zugreift, werden alle Verweise auf UGC angezeigt, einschließlich der Sites, die nicht mit der [Assistent zur Site-Erstellung](/help/communities/sites-console.md), z. B. die Geometrixx-Beispiele.
>
>Wenn ein Mitglied der vertrauenswürdigen Community auf die Massen-Moderationskonsole auf Veröffentlichen zugreift, werden nur Verweise auf UGC angezeigt, die für Community-Sites erstellt wurden, die das Mitglied moderieren darf. Außerdem kann er mit dem Site-Filter gefiltert werden.

#### Inhaltstyp {#content-type}

Der Content-Typ beschränkt die angezeigte referenzierte benutzergenerierte Inhaltsanzeige auf Beiträge des ausgewählten Ressourcentyps. Es können ein oder mehrere der folgenden Typen ausgewählt werden. Alle Typen werden angezeigt, wenn keine ausgewählt sind.

* **Kommentar**
* **Forenthema**
* **Forumsantwort**
* **Frage**
* **Antwort**
* **Blog-Artikel**
* **Blog-Kommentar**
* **Kalenderereignis**
* **Kalenderkommentar**
* **Ordner in Dateibibliothek**
* **Dokument in Dateibibliothek**
* **Idee**
* **Ideen-Kommentar**

![content-types](assets/content-types.png)

#### Weitere Content-Typen {#additional-content-types}

So fügen Sie zusätzliche Ressourcen zum Filtern hinzu:

* Melden Sie sich bei Ihrer Authoring-Instanz als Admin 
* Öffnen [Web-Konsole](https://localhost:4502/system/console/configMgr).
* Suchen `AEM Communities Moderation Dashboard Filters`.
* Wählen Sie die Konfiguration aus, damit Sie sie im Bearbeitungsmodus öffnen können.
* Geben Sie den Ressourcentyp einer Komponente ein, nach der gefiltert werden soll:

   * Um beispielsweise nach eingeschlossenen Abstimmungskomponenten zu filtern, geben Sie Folgendes ein:

     `Voting=social/tally/components/hbs/voting`

  ![additional-contenttype](assets/additional-contenttype.png)

* Wählen Sie Speichern aus.
* Aktualisieren Sie die Konsole Communities - Moderation .

Das Ergebnis ist ein neuer, auswählbarer Filter für `Voting` unter `Content Type` Filtergruppe.

Wenn dieser Filter ausgewählt ist, zeigt der Inhalt des Dashboards benutzergenerierte Inhalte an, die mit einem der eingegebenen Ressourcentypen übereinstimmen.

#### Status {#status}

Der Status beschränkt die Anzeige des referenzierten benutzergenerierten Inhalts auf Beiträge mit dem ausgewählten Status, bei denen es sich um einen oder mehrere Beiträge mit dem Status Ausstehend, Genehmigt, Verweigert oder Geschlossen sowie Entwurf oder Geplant für Blog-Artikel und Beantwortet oder Nicht beantwortet für Fragen zur Fragen zur Fragen der Prüfung handeln kann. Wenn keine ausgewählt ist, werden alle angezeigt.

>[!NOTE]
>
>Wenn nur der Status Nicht beantwortet ausgewählt ist, sieht der Moderator den gesamten Inhalt (für alle Inhaltstypen) mit Ausnahme der beantworteten Fragen. Dies liegt daran, dass die Eigenschaft, die für die beantwortet Frage verantwortlich ist, nicht vorhanden ist, wenn nicht beantwortete Fragen und andere Inhalte wie Forenthema, Blog-Artikel oder Kommentare vorliegen.

![status](assets/statuses.png)

#### Kennzeichnung {#flagging}

Durch die Kennzeichnung wird der referenzierte benutzergenerierte Inhalt auf Beiträge beschränkt, die als markiert oder ausgeblendet gekennzeichnet sind.

Sobald ein Inhaltselement gekennzeichnet ist, bleibt es so lange gekennzeichnet, bis Sie die Kennzeichnung für dieses Inhaltselement aufheben, indem Sie die Option **Markierung** erneut. Es gibt keine Kennzeichnungsebenen, z. B. wichtig oder Follow-up.

![Flaggen](assets/flagging.png)

#### Mitglieder {#members}

Mitglieder beschränken die referenzierte UGC, die für UGC angezeigt wird, die durch den eingegebenen Mitgliedsnamen veröffentlicht wurde.

![Mitglieder](assets/members.png)

#### Veröffentlichungszeitraum {#posted-in-the-last}

Posted In Last beschränkt die Anzeige des referenzierten benutzergenerierten Inhalts auf Beiträge, die in der letzten Stunde, am letzten Tag, in der Woche, im Monat oder im letzten Jahr veröffentlicht wurden.

![postal-last](assets/posted-last.png)

#### Empfindung {#sentiment}

[Sentiment](/help/communities/moderate-ugc.md#sentiment) begrenzt die angezeigte referenzierte benutzergenerierte Anzeige auf Beiträge mit einem Sentimentwert, der entweder positiv, negativ oder neutral ist.

![sentiment](assets/sentiment.png)

## Benutzerdefinierte Filter {#custom-filters}

Abgesehen von den vordefinierten Filtern in [Filterleiste](/help/communities/moderation.md#ootbfilters)können der Moderations-Benutzeroberfläche zusätzliche benutzerdefinierte Filter für Metadaten hinzugefügt werden. Entwickler können den Beispielcode in GitHub verwenden, um die vorhandenen Filter der Moderations-UI zu erweitern.

![custom-tag-filter](assets/custom-tag-filter.png)

Die [Beispielprojekt](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/main/aem-communities-moderation-filter) bei GitHub implementiert den Tag-Filter, um die UGC-Liste danach zu filtern, ob die spezifischen Tags auf benutzergenerierte Inhalte angewendet werden. Sie können dem Beispielcode folgen und analoge Filter für andere ähnliche UGC-Metadatenfelder erstellen.

So installieren Sie das Beispiel für den Filter Tags :

1. Öffnen Sie den Package Manager in AEM Author (`https://[aem-author]:4502/crx/packmgr/index.jsp`) Instanz und AEM Veröffentlichen (`https://[aem-publish]:4503/crx/packmgr/index.jsp`).
1. Paket erstellen `com.adobe.social.sample.moderation.filter.ui.apps-1.0-SNAPSHOT.zip` aus dem GitHub-Code, installieren und aktivieren Sie denselben.
1. Öffnen Sie die Bundles-Konsole in AEM Author ( `https://[aem-author]:4502/system/console/bundles`) Instanz und AEM Veröffentlichen ( `https://[aem-publish]:4503/system/console/bundles`).
1. Erstellen Sie das Paket (`[com](https://sample-moderation-filter.com/).adobe.social.sample.moderation.filter.core-1.0-SNAPSHOT.jar`) von GitHub aus und installieren und aktivieren Sie dasselbe.
1. Navigieren Sie zu **/apps/social/moderation/facets** Knoten in AEM Author (`https://[aem-author]:4502/crx/de/index.jsp#/apps/social/moderation/facets`) und AEM Veröffentlichen (`https://[aem-publish]:4502/crx/de/index.jsp#/apps/social/moderation/facets`).
1. Technischen Benutzer hinzufügen **communities-utility-reader** mit `jcr:read` Berechtigungen.

So stellen Sie die benutzerdefinierten Filter auf bestehenden Community-Sites bereit:

1. Bearbeiten `Clientlibs` der vorhandenen Moderationsseite `/content/we-retail/us/en/community/moderation/shell3/jcr:content/head/clientlibs.`

   * Neue Kategorie hinzufügen `cq.social.hbs.moderation.v2.`

1. Wechseln Sie zu `/content/we-retail/us/en/community/moderation/shell3/jcr:content/rails/searchWell/items/filters.`.

   * Auf neue Komponente festlegen `sling:resourceType = social/moderation/v2/filters.`

1. Rufen Sie `/content/we-retail/us/en/community/moderation/shell3/jcr:content/views/content/items/modcontainer` auf.

   * Auf neue Komponente festlegen `sling:resourceType = social/moderation/v2/modcontainer`.

## Moderationsaktionen {#moderation-actions}

[Moderationsaktionen](/help/communities/moderate-ugc.md#moderation-actions) kann für eine oder mehrere Auswahlen durchgeführt werden, die im Inhaltsbereich oder beim Anzeigen von Inhaltsdetails vorgenommen werden.

Um die Beiträge stapelweise zu moderieren, klicken Sie im Inhaltsbereich auf die Schaltfläche Auswählen (![selecticon](assets/selecticon.png)) auf einem Beitrag, der angezeigt wird, wenn Sie mit der Maus (Desktop) darauf zeigen oder mit dem Finger auf den Beitrag drücken (Mobil). Auf diese Weise können Sie den Mehrfachauswahlmodus aufrufen und jetzt die nachfolgenden Beiträge auswählen, die in der Massenmoderierung berücksichtigt werden sollen, indem Sie einfach darauf klicken. Verwenden Sie die in der Symbolleiste angezeigten Schaltflächen, damit Sie Moderationsaktionen für die ausgewählten Beiträge durchführen können. Alle Aktionsaufforderungen zur Bestätigung.

Um einen einzelnen Beitrag im Inhaltsbereich zu moderieren, bewegen Sie den Mauszeiger (Desktop) darauf oder drücken Sie die Eingabetaste und halten Sie den Finger auf den Beitrag (Mobil), sodass Schaltflächen auf dem Beitrag erscheinen. Bei der Bearbeitung einzelner Inhaltsdetails wird nur eine Löschaktion zur Bestätigung aufgefordert.

### Moderieren mehrerer Beiträge {#moderating-multiple-posts}

Rufen Sie den Massenauswahlmodus auf, indem Sie auf die `Select` Symbol in einem Beitrag:

![select-icon](assets/select-icon.png)

Um den Massenauswahlmodus zu beenden, wählen Sie in der Symbolleiste das Symbol Abbrechen (x) aus:

Moderationsaktionen, die an mehreren Beiträgen durchgeführt werden können:

* Ablehnen
* Löschen
* Beiträge schließen/erneut öffnen

Die Symbole für diese Aktionen werden nur dann in der Symbolleiste angezeigt, wenn mehrere Beiträge ausgewählt sind.

![bulkmoderat](assets/bulkmoderate.png)

### Moderieren eines einzelnen Beitrags {#moderating-a-single-post}

Im Einzelauswahlmodus ist es möglich:

* Zeigen Sie die Benutzerdetails an, indem Sie den Namen des Benutzers auswählen.
* Zeigen Sie den Beitrag im Kontext an, indem Sie den Link zum Beitrag auswählen.
* [Antwort](#reply)
* [Zulassen](#allow)
* [Ablehnen](#deny)
* [Löschen](#delete)
* [Schließen](#close)
* Ansicht [Moderationsverlauf](#moderation-history)
* [Details anzeigen](#viewdetails)

In der Kartenansicht über den Symbolen für Moderationsaktionen ist der Text des Beitrags vorhanden und darunter sind die Daten, die angeben:

* Wenn Antworten vorliegen und wenn ja, vor der Anzahl der Antworten
* Wenn es gekennzeichnet wurde
* Wenn die Genehmigung erteilt wurde
* Zeitpunkt der Veröffentlichung der UGC

![singleselektmode](assets/singleselectmode.png)

#### Antwort {#reply}

![Antwort](assets/reply.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, wird das Symbol Antworten angezeigt, wenn der UGC-Typ Antworten unterstützt und so konfiguriert ist, dass Antworten zulässig sind.

#### Zulassen {#allow}

![zulassen](assets/allow.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, wird das Symbol Zulassen angezeigt, wenn der Beitrag entweder gekennzeichnet oder abgelehnt wurde. Wenn die Option Zulassen aktiviert ist, werden alle Flags gelöscht.

#### Ablehnen {#deny}

![ablehnen](assets/deny.png)

Die **Ablehnen** Die Moderationsaktion ist nur für moderierte Inhalte verfügbar und wird nur im Mehrfachauswahlmodus bei nicht moderierten Inhalten angezeigt.

Nicht moderierte Inhalte werden immer genehmigt.

Inhalte, die zunächst moderiert werden, werden in den Status &quot;Ausstehend&quot;versetzt und können später zur Genehmigung oder Ablehnung geändert werden.

Inhalt, der den Status &quot;Ausstehend&quot;verlässt, kann nie in den Status &quot;Ausstehend&quot;zurückkehren. Inhalte, die als genehmigt oder abgelehnt markiert sind, können jederzeit in einen anderen Status geändert werden.

#### Löschen {#delete}

![löschen](assets/delete.png)

Im Einzelauswahl- oder Massenmodus können Sie Elemente auswählen und löschen. Die Löschaktion führt zu einem Bestätigungsdialogfeld. Nach dem Löschen werden diese Elemente sofort aus dem Inhaltsbereich entfernt. **Sobald UGC gelöscht wurde, wird es dauerhaft aus dem Repository entfernt und kann später nicht mehr abgerufen werden**.

#### Schließen {#close}

![schließen](assets/close.png)

Beim Arbeiten mit einem einzelnen Beitrag wird ein Symbol Schließen angezeigt, wenn der UGC-Typ die Möglichkeit unterstützt, weitere Beiträge für diese Ressource zu verhindern.

#### Moderationsverlauf {#moderation-history}

![Moderation](assets/moderation.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, wird beim Bewegen des Mauszeigers über diesen ein Symbol für den Moderationsverlauf angezeigt. Wenn Sie das Symbol auswählen, wird ein Bereich mit einem Verlauf der Aktionen angezeigt, die bezüglich des UGC-Beitrags durchgeführt wurden.

Um zum Inhaltsbereich zurückzukehren und mehrere UGC-Beiträge anzuzeigen, wählen Sie das X in der oberen rechten Ecke des Detailbereichs der Ansicht aus.

Beispiel:

![moderation-history](assets/moderation-history.png)

#### Details anzeigen {#view-detail}

![Ansicht](assets/view.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, können Sie weitere Details anzeigen, indem Sie die UGC im Detailmodus öffnen.

Bewegen Sie dazu den Mauszeiger über den Beitrag, um die `View Detail` und wählen Sie es aus, um ein Bedienfeld mit weiteren Details zum Beitrag anzuzeigen.

Um zum Inhaltsbereich zurückzukehren und mehrere UGC-Beiträge anzuzeigen, wählen Sie das X in der oberen rechten Ecke des Detailbereichs der Ansicht aus.

Beispiel:

![view1](assets/view1.png)
