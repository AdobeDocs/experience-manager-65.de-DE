---
title: Kalenderfunktion
description: Erfahren Sie, wie die Kalenderfunktion Community-Ereignisinformationen in einem Kalenderformat bereitstellt.
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

Die Kalenderfunktion unterstützt die Bereitstellung von Informationen zu Community-Ereignissen in einem Kalenderformat entweder für alle Site-Besucher oder nur für angemeldete Site-Besucher (Community-Mitglieder), während nur autorisierte Mitglieder Ereignisse hinzufügen können.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben

* Hinzufügen der Kalenderfunktion zu einer AEM-Site
* Konfigurationseinstellungen für `Calendar` Komponenten

## Kalender zu einer Seite hinzufügen {#adding-a-calendar-to-a-page}

Um einer Seite im Autorenmodus eine `Calendar` Komponente hinzuzufügen, suchen Sie im Komponenten-Browser nach

* `Communities / Calendar`

und ziehen Sie sie auf eine Seite, z. B. eine Position relativ zur Funktion, die von Benutzenden überprüft werden soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen Client-seitigen ](/help/communities/calendar-basics-for-developers.md#essentials-for-client-side) enthalten sind, wird die `Calendar` Komponente wie folgt angezeigt.

![calendar-component](assets/calendar-component.png)

### Kalender konfigurieren {#configuring-calendar}

Wählen Sie die platzierte `Calendar` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

![configure-calendar](assets/configure-calendar1.png)

#### Registerkarte „Einstellungen“ {#settings-tab}

Geben **auf der Registerkarte** Einstellungen“ an, ob Tags auf Kalendereinträge angewendet werden dürfen.

* **Ereignisse pro Seite**

  Definiert die Anzahl der angezeigten Ereignisse pro Seite. Der Standardwert ist 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss die Veröffentlichung von Kalenderereignissen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Standard ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, wird der Kalender für neue Ereigniseinträge und Kommentare geschlossen. Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Kalenderereignisse und Kommentare mit Markup eingegeben werden. Die Standardeinstellung ist aktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder den Ereignissen, die sie posten, Tag-Kennzeichnungen hinzufügen (siehe **Tag-Feld** Registerkarte). Die Standardeinstellung ist aktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Dateianhänge zu einem Kalenderereignis oder Kommentar hinzugefügt werden. Die Standardeinstellung ist aktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Ereignisse verfolgen, die im Kalender veröffentlicht wurden. Die Standardeinstellung ist aktiviert.

* **max. Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Punkttrennzeichen. Zum Beispiel .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, können die nicht angegebenen nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Max. Größe der angehängten Bilddatei**

  Nur relevant, wenn Datei-Uploads zulassen aktiviert ist. Maximale Anzahl an Byte, die eine hochgeladene Bilddatei aufweisen darf. Der Standardwert lautet 2097152 **&#x200B; ** (2 MB).

* **Zulässige Cover-Bildtypen**

  Eine kommagetrennte Liste von Bilddateierweiterungen mit dem Punkttrennzeichen. Der Standardwert ist `.jpg,.jpeg,.png,.gif,.bmp`.

* **Thread-Antworten zulassen**

  Wenn diese Option aktiviert ist, können Sie Antworten auf Kommentare zulassen, die an das Kalenderereignis gesendet werden. Die Standardeinstellung ist aktiviert.

* **Benutzern das Löschen von Kommentaren und Ereignissen ermöglichen**

  Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Kalenderereignisse löschen, die sie veröffentlicht haben. Die Standardeinstellung ist aktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, wird die Abstimmfunktion in ein Kalenderereignis eingeschlossen. Die Standardeinstellung ist aktiviert.

* **Breadcrumbs anzeigen**

  Breadcrumbs auf Ereignisseite anzeigen. Die Standardeinstellung ist aktiviert.

* **Datumsbereichsfilter**

  Definiert die Anzahl der Tage, die zum aktuellen Datum hinzugefügt werden, um den Wert „An“ des Filters für die Kalenderereignisliste zu berechnen. Die Standardnummer ist 30.

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option aktiviert ist, kann die Idee als [vorgestellter Inhalt“ identifiziert ](/help/communities/featured.md). Standard ist deaktiviert.

Geben **auf der Registerkarte** Benutzermoderation) an, wie die veröffentlichten Themen und Antworten (benutzergenerierte Inhalte) verwaltet werden sollen. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

#### Registerkarte „Benutzermoderation“ {#user-moderation-tab}

* **Beiträge verweigern**

  Wenn diese Option aktiviert ist, dürfen Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Die Standardeinstellung ist aktiviert.

* **Ereignisse schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder ein Ereignis schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und auch ein Ereignis erneut öffnen. Die Standardeinstellung ist aktiviert.

* **Flag-Posts**

  Wenn diese Option aktiviert ist, können Mitglieder die Ereignisse oder Kommentare anderer Benutzer als unangemessen kennzeichnen. Die Standardeinstellung ist aktiviert.

* **Verursacherliste kennzeichnen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund für das Kennzeichnen eines Ereignisses oder Kommentars als unangemessen auswählen. Standard ist deaktiviert.

* **Grund für benutzerdefinierte Markierung**

  Wenn diese Option aktiviert ist, können Mitglieder ihren eigenen Grund für das Kennzeichnen eines Ereignisses oder Kommentars als unangemessen eingeben. Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft ein Ereignis oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungsgrenze**

  Geben Sie an, wie oft ein Ereignis oder Kommentar gekennzeichnet werden muss, bevor es/er aus der öffentlichen Ansicht ausgeblendet wird. Wenn auf -1 festgelegt, wird das markierte Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für die Mäßigung sein. Der Standardwert ist 5.

#### Registerkarte „Tag-Feld“ {#tag-field-tab}

Auf der Registerkarte **Tag** sind die Tags, die angewendet werden können, wenn dies auf der Registerkarte **Einstellungen** zulässig ist, entsprechend den ausgewählten Namespaces begrenzt.

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die Tags, die angewendet werden können, sind auf die innerhalb der geprüften Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst „Standard-Tags“ (den Standard-Namespace) und „Alle Tags einschließen“. Standardmäßig ist „Keine“ aktiviert, was bedeutet, dass alle Namespaces zulässig sind.

* **Vorschlagslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht. Der Standardwert ist **-**&#x200B;1 (keine Beschränkungen).

>[!NOTE]
>
>Unter [Verwalten von Tags](/help/sites-administering/tags.md) erfahren Sie, wie Sie einen Tag-Namespace (Taxonomie) hinzufügen.

#### Registerkarte „Übersetzung“ {#translation-tab}

Wenn die Übersetzung für die Community **Site auf der Registerkarte Übersetzung** aktiviert ist, kann die Übersetzung so eingestellt werden, dass der gesamte Thread (Ereignis und Kommentare) anstelle spezifischer Beiträge übersetzt wird.

* **Alle übersetzen**

  Wenn diese Option aktiviert ist, werden das Ereignis und die Kommentare in die bevorzugte Sprache des Benutzers übersetzt. Die Standardeinstellung ist aktiviert.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung zeigt die Kalenderfunktion ein Suchfeld mit einem standardmäßigen Datumsbereich und alle Kalenderereignisse an, die in diesen Bereich fallen.

Wenn Sie ein Kalenderereignis auswählen, werden die Kalenderereignisdetails, die Beschreibung und Kommentare angezeigt.

Andere Funktionen hängen davon ab, ob der Site-Besucher ein Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Benutzer ist.

### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorrechte verfügt, kann er [Moderationsaufgaben](/help/communities/moderate-ugc.md) (gemäß der Konfiguration der Komponente) für alle Kalenderereignisse und -kommentare ausführen, die an ein Ereignis gesendet werden.

![Moderatoren-Ansicht](assets/moderators-view.png)

#### Mitglieder {#members}

Wenn der angemeldete Benutzer Community-Mitglied oder [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) ist (je nach Konfiguration), kann er `New Event` auswählen, um ein neues Kalenderereignis zu erstellen und zu posten.

Insbesondere können sie:

* Erstellen eines Kalenderereignisses
* Kommentar zu einem Kalenderereignis posten
* Bearbeiten eines eigenen Kalenderereignisses oder Kommentars
* Löschen eines eigenen Kalenderereignisses oder Kommentars
* Kennzeichnen von Kalenderereignissen oder Kommentaren anderer Benutzer

![create-event](assets/configure-calendar2.png)

![event-post](assets/configure-calendar3.png)

#### Anonym {#anonymous}

Besuchende der Website, die nicht angemeldet sind, dürfen nur gepostete Kalenderereignisse lesen, diese übersetzen, falls sie unterstützt werden, aber kein Ereignis oder Kommentar hinzufügen oder die Ereignisse oder Kommentare anderer kennzeichnen.

![anonymous-user-view](assets/anonymous-user-view1.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Calendar Essentials](/help/communities/calendar-basics-for-developers.md) für Entwickler.

Informationen zur Moderation von Kalenderereignissen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von Kalenderereignissen und Kommentaren finden Sie unter [Tagging von benutzergenerierten Inhalten](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von Kalenderereignissen und Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
