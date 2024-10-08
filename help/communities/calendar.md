---
title: Kalenderfunktion
description: Erfahren Sie, wie die Kalenderfunktion Informationen zu Community-Ereignissen in einem Kalenderformat bereitstellt.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: c9b34b00-525d-4ca3-bd18-11bb7ce66787
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 1%

---

# Kalenderfunktion {#calendar-feature}

## Einführung {#introduction}

Die Kalenderfunktion unterstützt die Bereitstellung von Community-Ereignisinformationen im Kalenderformat entweder für alle Site-Besucher oder nur für angemeldete Site-Besucher (Community-Mitglieder), während nur autorisierte Mitglieder Ereignisse hinzufügen können.

In diesem Abschnitt der Dokumentation wird

* Hinzufügen der Kalenderfunktion zu einer AEM Site
* Konfigurationseinstellungen für `Calendar` -Komponenten

## Hinzufügen eines Kalenders zu einer Seite {#adding-a-calendar-to-a-page}

Möchten Sie im Autorenmodus einer Seite die Komponente `Calendar` hinzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Calendar`

Ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position in Bezug auf die Funktion, die Benutzer überprüfen können.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die [ erforderlichen clientseitigen Bibliotheken](/help/communities/calendar-basics-for-developers.md#essentials-for-client-side) enthalten sind, wird die Komponente `Calendar` so angezeigt.

![calendar-component](assets/calendar-component.png)

### Kalender konfigurieren {#configuring-calendar}

Wählen Sie die platzierte Komponente `Calendar` aus, damit Sie auf das Symbol `Configure` zugreifen und dieses auswählen können, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure](assets/configure-new.png)

![configure-calendar](assets/configure-calendar1.png)

#### Registerkarte &quot;Einstellungen&quot; {#settings-tab}

Geben Sie auf der Registerkarte **Einstellungen** an, ob Tags auf Kalendereinträge angewendet werden dürfen.

* **Ereignisse pro Seite**

  Definiert die Anzahl der pro Seite angezeigten Ereignisse. Der Standardwert ist 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss die Veröffentlichung von Kalenderereignissen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Die Option Standard ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, ist der Kalender für neue Ereigniseinträge und -kommentare gesperrt. Die Option Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Kalenderereignisse und Kommentare mit Markup eingegeben werden. Die Option Standard ist aktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder den von ihnen geposteten Ereignissen Tag-Beschriftungen hinzufügen (siehe Registerkarte **Tag-Feld** ). Die Option Standard ist aktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Sie zulassen, dass Dateianlagen zu einem Kalenderereignis oder Kommentar hinzugefügt werden. Die Option Standard ist aktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Ereignisse verfolgen, die in den Kalender veröffentlicht wurden. Die Option Standard ist aktiviert.

* **Maximale Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, können nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Max. Größe der Bilddatei anhängen**

  Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Maximale Anzahl der Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152** **(2 MB).

* **Zulässige Abdeckung für Bildtypen**

  Eine kommagetrennte Liste von Bilddateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Der Standardwert ist `.jpg,.jpeg,.png,.gif,.bmp`.

* **Ermöglichen von gefilterten Antworten**

  Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die zum Kalenderereignis veröffentlicht wurden. Die Option Standard ist aktiviert.

* **Benutzern das Löschen von Kommentaren und Ereignissen ermöglichen**

  Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Kalenderereignisse löschen. Die Option Standard ist aktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, nehmen Sie die Abstimmungsfunktion in ein Kalenderereignis auf. Die Option Standard ist aktiviert.

* **Breadcrumbs anzeigen**

  Breadcrumbs auf der Ereignisseite anzeigen. Die Option Standard ist aktiviert.

* **Datumsbereichfilter**

  Definiert die Anzahl der Tage, die zum aktuellen Datum hinzugefügt werden, um den &quot;An&quot;-Wert des Seitenfilters für die Auflistung von Kalenderereignissen zu berechnen. Die Standardnummer ist 30.

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, kann die Idee als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert werden. Die Option Standard ist deaktiviert.

Geben Sie auf der Registerkarte **Benutzermoderation** an, wie die veröffentlichten Themen und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

* **Posts verweigern**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Die Option Standard ist aktiviert.

* **Ereignisse schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder ein Ereignis schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Ereignis auch erneut öffnen. Die Option Standard ist aktiviert.

* **Posts kennzeichnen**

  Ist diese Option aktiviert, können Mitglieder Ereignisse oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist aktiviert.

* **Liste mit Kennzeichnungsgründen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Ereignisse oder Kommentare als unangemessen gekennzeichnet werden. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

  Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Ereignisses oder Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft ein Ereignis oder Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **Kennzeichnungslimit**

  Geben Sie an, wie oft ein Ereignis oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 festgelegt ist, wird das gekennzeichnete Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für Moderation sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Auf der Registerkarte **Tag-Feld** sind die Tags, die angewendet werden können, sofern sie auf der Registerkarte **Einstellungen** zulässig sind, entsprechend den ausgewählten Namespaces beschränkt.

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) und &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **Empfehlungslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Standardwert ist **-**1 (keine Beschränkungen).

>[!NOTE]
>
>Besuchen Sie [Verwalten von Tags](/help/sites-administering/tags.md) , wo Sie erfahren können, wie Sie einen Tag-Namespace (Taxonomie) hinzufügen.

#### Tab &quot;Übersetzung&quot; {#translation-tab}

Wenn auf der Registerkarte **Übersetzung** die Übersetzung für die Community-Site aktiviert ist, kann die Übersetzung so eingestellt werden, dass anstelle bestimmter Beiträge der gesamte Thread (Ereignis und Kommentare) übersetzt wird.

* **Alle übersetzen**

  Wenn diese Option aktiviert ist, werden Ereignis und Kommentare in die bevorzugte Sprache des Benutzers übersetzt. Die Option Standard ist aktiviert.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung zeigt die Kalenderfunktion ein Suchfeld mit einem Standarddatumsbereich sowie alle Kalenderereignisse an, die in diesen Bereich fallen.

Wenn ein Kalenderereignis ausgewählt wird, werden Details, Beschreibung und Kommentare zum Kalenderereignis angezeigt.

Andere Möglichkeiten hängen davon ab, ob der Besucher der Site Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonym ist.

### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorberechtigungen verfügt, kann er für alle Kalenderereignisse und Kommentare, die für ein Ereignis veröffentlicht werden, [Moderationsaufgaben](/help/communities/moderate-ugc.md) ausführen (wie es durch die Konfiguration der Komponente zulässig ist).

![moderators-view](assets/moderators-view.png)

#### Mitglieder {#members}

Wenn der angemeldete Benutzer Community-Mitglied oder [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) ist (je nach Konfiguration), kann er `New Event` auswählen, um ein neues Kalenderereignis zu erstellen und zu posten.

Insbesondere können sie:

* Kalenderereignisse erstellen
* Post einen Kommentar zu einem Kalenderereignis
* Bearbeiten von eigenen Kalenderereignissen oder Kommentaren
* Löschen eines eigenen Kalenderereignisses oder Kommentars
* Kalenderereignisse oder Kommentare anderer kennzeichnen

![create-event](assets/configure-calendar2.png)

![event-post](assets/configure-calendar3.png)

#### Anonym {#anonymous}

Besucher der Website, die nicht angemeldet sind, dürfen veröffentlichte Kalenderereignisse nur lesen, übersetzen, sofern sie unterstützt werden. Sie dürfen jedoch keine Ereignisse oder Kommentare hinzufügen oder die Ereignisse oder Kommentare anderer Benutzer kennzeichnen.

![anonymous-user-view](assets/anonymous-user-view1.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Kalendergrundlagen](/help/communities/calendar-basics-for-developers.md) .

Informationen zur Moderation von Kalenderereignissen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von Kalenderereignissen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von Kalenderereignissen und Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
