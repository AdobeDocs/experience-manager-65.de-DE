---
title: Konsole für Community-Gruppen
seo-title: Konsole für Community-Gruppen
description: In der Gruppenkonsole können Sie Community-Gruppen erstellen
seo-description: In der Gruppenkonsole können Sie Community-Gruppen erstellen
uuid: 21e2bde3-7354-4193-bcb3-c672c6342252
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d381ea40-fe49-4d32-bfad-1379c7a02aba
docset: aem65
pagetitle: Community Groups Console
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1679'
ht-degree: 3%

---


# Konsole für Community-Gruppen {#community-groups-console}

Die Konsole &quot;Gruppen&quot;bietet Zugriff auf das Erstellen von Community-Gruppen, wenn die [Vorlagenstruktur](/help/communities/sites-console.md#step1) einer Community-Site die [groups-Funktion](/help/communities/functions.md#groups-function) enthält.

* AEM Communities unterstützt das Verschachteln von Gruppen innerhalb anderer Gruppen. Gruppenverschachtelung ist möglich, wenn die [Struktur der neuen Gruppe](/help/communities/tools-groups.md) die Funktion groups enthält.
* Nur für die Umgebung des Autors gibt es einen Assistenten zum Erstellen von Gruppen, der dem Assistenten zum Erstellen der Site ähnelt.
* Ob (oder nicht) Mitglieder in der Umgebung &quot;Veröffentlichen&quot;Gruppen erstellen können, ist beim Hinzufügen einer Gruppenfunktion zu einer Community-Site- oder Community-Gruppenstruktur konfigurierbar.

Von den drei enthaltenen Gruppenvorlagen enthält nur die `Reference Group`-Vorlage eine Gruppenfunktion in ihrer Struktur.

Die verschiedenen Facetten von Gemeinschaftsgruppen sind:

* **Erstellung**: Neue Gruppe kann im Autorenmodus und optional in der Veröffentlichungsinstanz erstellt werden.
* **Kontrolle**: kann offen oder geheim sein.
* **Verschachtelung**: Gruppe kann null oder mehr Gruppen enthalten.

<!-- This is a 404 on helpx. Please update or remove.
>[!NOTE]
>
>Community groups, created in the publish environment before the [existence of the Community Groups console](/help/communities/version-history.md#featurepack1fp1), will not be listed in the Community Groups console, and thus, are not modifiable using the console.
-->

>[!NOTE]
>
>Diese Gruppenkonsole, die nur über die Communities Sites-Konsole zugänglich ist, ist nicht mit dem Mitglied [Groups console](/help/communities/members.md) für die Verwaltung von Mitgliedsgruppen zu verwechseln.
>
>Mitgliedergruppen sind Benutzergruppen, die in der Umgebung &quot;Veröffentlichen&quot;registriert sind und von der Autorengruppe aus über den [Tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author) aufgerufen werden können.

## Gruppenerstellung {#group-creation}

So greifen Sie auf die Konsole &quot;Gruppen&quot;zu:

* Melden Sie sich beim Autor mit Administratorrechten an.
* Aus globaler Navigation: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.
* Wählen Sie einen vorhandenen Community-Site-Ordner aus, um ihn zu öffnen.
* Wählen Sie eine Instanz einer Community-Site im Ordner aus.

   * Die Struktur der Community-Site muss eine Gruppenfunktion enthalten.
   * Diese Screenshots stammen aus dem Tutorial &quot;Erste Schritte&quot;, nach dem [Erstellen von Gruppen im Veröffentlichungsmodus](/help/communities/published-site.md).

   ![create-group](assets/create-group.png)

* Wählen Sie den Ordner **Gruppen** aus, um ihn zu öffnen.

   Beim Öffnen werden alle vorhandenen Gruppen angezeigt, unabhängig davon, ob sie beim Autor oder beim Veröffentlichen erstellt wurden.

   In dieser Konsole &quot;Gruppen&quot;können neue Gruppen erstellt werden.

   ![create-new-group](assets/create-new-group.png)

* Klicken Sie auf die Schaltfläche **Gruppe erstellen**.

### Schritt 1: Community-Gruppenvorlage {#step-community-group-template}

![Mehrsprachige Community-Gruppen](assets/multi-lingual-group.png)

* **Community-Gruppenname**

   Ein Anzeigentitel für die Gruppe.
Der Titel wird auf der veröffentlichten Site für die Gruppe angezeigt.

* **Community-Gruppenbeschreibung**

   Eine Beschreibung der Gruppe.

* **Community-Gruppen-Stammverzeichnis**

   Der Stammpfad zur Gruppe.
Der Standardstamm ist die übergeordnete Site, der Stammordner kann jedoch an einen beliebigen Speicherort innerhalb der Website verschoben werden. Es wird nicht empfohlen, es zu ändern.

* **Menü &quot;Zusätzliche verfügbare Sprachen** der Community&quot;

   Verwenden Sie die Dropdownliste, um die verfügbaren Gemeinschaftsgruppensprachen auszuwählen. Das Menü zeigt alle Sprachen an, in denen die übergeordnete Community-Site erstellt wurde. Benutzer können in diesem Schritt eine der folgenden Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Konsole &quot;Gruppen&quot;der jeweiligen Community-Sites erstellt.

* **Community-Gruppenname**

   Der Name der Stammseite der Gruppe, die in der URL angezeigt wird.

   * Überprüfen Sie den Dublette-Namen, da er nach dem Erstellen der Gruppe nicht so leicht geändert werden kann.
   * Die Basis-URL wird unter dem `Community Group Name` angezeigt.
   * Für eine gültige URL hängen Sie &quot;.html&quot;an
      *zum Beispiel*:  `https://localhost:4502/content/sites/mysight/en/mygroup.html`.

* **Community-** Gruppenvorlage

   Verwenden Sie die Dropdownliste, um eine verfügbare [Community-Gruppenvorlage](/help/communities/tools.md) auszuwählen.

### Schritt 2: Design {#step-design}

### GEMEINSCHAFTSGRUPPENTHEMEN {#community-group-theme}

![communityGrouptheme](assets/communitygrouptheme.png)

Das Framework verwendet [Twitter-Bootstrap](https://twitterbootstrap.org/), um ein reaktionsfähiges, flexibles Design auf die Site zu bringen. Eines der vielen vorab geladenen Bootstrap-Themen kann ausgewählt werden, um die ausgewählte Community-Gruppenvorlage zu gestalten, oder ein Bootstrap-Design kann hochgeladen werden.

Wenn diese Option aktiviert ist, wird das Design mit einem undurchsichtigen blauen Häkchen überlagert.

Es ist möglich, ein Design auszuwählen, das sich vom Design der übergeordneten Site unterscheidet.

Nach der Veröffentlichung der Community-Site ist es möglich, die Eigenschaften [zu bearbeiten und ein anderes Design auszuwählen.](#modifyinggroupproperties)

### GEMEINSCHAFTSGRUPPENBRANCHE {#community-group-branding}

![community-group-branding](assets/community-group-branding.png)

Das Branding einer Community-Site ist ein Bild, das als Kopfzeile am oberen Rand jeder Seite angezeigt wird. Es ist möglich, ein Banner für die Gruppe anzuzeigen, das sich von anderen Seiten der Site unterscheidet.

Das Bild sollte so groß sein, dass es im Browser wie erwartet angezeigt wird, und 120 Pixel hoch.

Beachten Sie beim Erstellen oder Auswählen eines Bildes Folgendes:

* Die Bildhöhe wird auf 120 Pixel abgeschnitten, gemessen von der oberen Kante des Bilds
* Das Bild wird am linken Rand des Browserfensters fixiert
* Die Bildgröße ändert sich nicht, d. h. wenn die Bildbreite wie folgt ist:

   * Wenn die Breite des Browsers geringer ist, wird das Bild horizontal wiederholt.
   * Größer als die Breite des Browsers, scheint das Bild beschnitten zu sein.

### Schritt 3: Einstellungen {#step-settings}

**MODERATION**

![Community-Gruppenmitglieder auswählen](assets/group-admin.png)

**Community-Gruppenmoderatoren**

Standardmäßig wird die Liste der Moderatoren auf der übergeordneten Community-Site geerbt.

Es ist möglich, für die Gruppe spezifische Moderatoren hinzuzufügen. Nach Mitgliedern suchen (aus der Umgebung der Veröffentlichung), um sie als Moderatoren hinzuzufügen

**Gruppenadministratoren**

Standardmäßig ist der Administrator der übergeordneten Community-Site auch der Administrator für Gruppen.

Es ist jedoch möglich, unabhängige Gruppenadministratoren zuzuweisen. Gruppenadministratoren können ihre Gruppe (z. B. G1) verwalten und eine Untergruppe erstellen, die unter G1 verschachtelt ist. Sie können der Untergruppe weitere Administratoren zuweisen.

Ein Benutzer U1 kann daher Administrator in einer Gruppe G1 und ein regulärer Benutzer in der verschachtelten Gruppe G2 sein.

**MITGLIEDSCHAFT**

Die Mitgliedschaftseinstellung ermöglicht die Auswahl einer der drei Möglichkeiten, eine Community-Gruppe zu sichern.

![community-group-mitgliedschaft](assets/community-group-membership.png)

* **Optionale Mitgliedschaft**

   Bei Auswahl dieser Option ist die Community-Gruppe eine öffentliche Gruppe. Site-Mitglieder können an der Gruppe und an Beiträgen teilnehmen, ohne explizit der Gruppe beizutreten. Diese Option ist standardmäßig ausgewählt.

* **Erforderliche Mitgliedschaft**

   Bei Auswahl dieser Option ist die Community-Gruppe eine offene Gruppe. Mitglieder der Community-Site können den Gruppeninhalt Ansicht, müssen sich jedoch der Gruppe anschließen, um Inhalte zu veröffentlichen. Mitglieder werden durch Klicken auf die Schaltfläche `Join` in der Umgebung zum Veröffentlichen hinzugefügt. &quot;Standard&quot;ist nicht ausgewählt.

* **Eingeschränkte Mitgliedschaft**

   Bei Auswahl dieser Option ist die Community-Gruppe eine geheime Gruppe. Die Mitglieder der Gemeinschaft müssen ausdrücklich eingeladen werden. Eingeladene Mitglieder werden in das Suchfeld eingegeben. Mitglieder können später mit der Umgebung [Mitglieder und Gruppen hinzugefügt werden. ](/help/communities/members.md) &quot;Standard&quot;ist nicht ausgewählt.

**MINIATUR**

![community-group-thumbnail](assets/community-group-thumbnail.png)

Die Miniaturansicht ist ein Bild, das bei Autor und Veröffentlichung für die Gruppe angezeigt wird.

Die optimale Größe für ein Gruppenbild beträgt 170 x 90 Pixel in einem unterstützten Bildformat (z. B. JPG oder PNG).

Wenn kein Bild hinzugefügt wird, wird ein Standardbild angezeigt.

![thumbnail-image](assets/thumbnail-image.png)

### Schritt 4: Gruppe erstellen {#step-create-group}

![community-create-group](assets/community-create-group.png)

Wenn Anpassungen erforderlich sind, verwenden Sie die Schaltfläche **Zurück**, um sie vorzunehmen.

Wenn **Create** ausgewählt und gestartet wurde, kann der Vorgang zum Erstellen der Gruppe nicht unterbrochen werden.

Nach Abschluss des Vorgangs wird die Karte für die neue Subcommunity-Site (Gruppe) in der Communities Sites Groups-Konsole angezeigt, über die Autoren Seiteninhalte hinzufügen können oder Administratoren die Eigenschaften der Site ändern können.

![Community-Gruppe erstellen](assets/create-community-groups.png)

>[!NOTE]
>
>Die Gruppe wird in allen Sprachen erstellt, wie in [Schritt 1 angegeben: Community-Gruppenvorlage](/help/communities/groups.md#step-community-group-template) in &quot;Zusätzliche verfügbare Community-Gruppensprachen&quot;in der Community-Gruppenkonsole der jeweiligen Community-Sites.

## Inhalt der Autorengruppe {#author-group-content}

![open-site](assets/open-site.png)

Der Seiteninhalt einer Gruppe kann mit denselben Werkzeugen wie jede andere AEM erstellt werden. Um die Gruppe zum Authoring zu öffnen, wählen Sie das Symbol &quot;Site öffnen&quot;, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen.

## Gruppeneigenschaften {#modify-group-properties} ändern

Die Eigenschaften einer bestehenden Subcommunity-Site, die während des Community-Gruppenerstellungsprozesses angegeben wurde, können durch Auswahl des Symbols &quot;Site bearbeiten&quot;geändert werden, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen:

![edit-site](assets/edit-site.png)

Die Details der folgenden Eigenschaften stimmen mit den Beschreibungen im Abschnitt [Gruppenerstellung](#group-creation) überein. Verschachtelte Gruppen können bearbeitet werden, unabhängig davon, ob sie in der Umgebung &quot;Veröffentlichen&quot;oder in der Umgebung &quot;Autor&quot;erstellt wurden.

![community-group-basic](assets/community-group-basic.png)

### Basic {#modify-basic} ändern

Das BASIC-Bedienfeld ermöglicht die Änderung von

* Community-Gruppenname
* Community-Gruppenbeschreibung

Der Community-Gruppenname darf nicht geändert werden.

Die Auswahl einer anderen Community-Gruppenvorlage hätte keine Auswirkungen auf eine bestehende Community-Gruppensite, da keine Verbindung zwischen Vorlagen und Sites bestehen bleibt.

Stattdessen kann die [STRUKTUR](#modify-structure) der Untergemeinschaft geändert werden.

### Struktur ändern {#modify-structure}

Das STRUKTURbedienfeld ermöglicht die Änderung der Struktur, die ursprünglich aus der Community-Gruppenvorlage erstellt wurde, die beim Erstellen der Unter-Community-Site entweder aus der Autor- oder der Veröffentlichungs-Umgebung ausgewählt wurde. Über den Bereich können Sie:

* Ziehen Sie weitere [Community-Funktionen](/help/communities/functions.md) per Drag &amp; Drop in die Site-Struktur.
* Auf einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`Gear icon`**
Bearbeiten Sie Einstellungen, einschließlich Anzeigentitel, URL und  [privilegierte Mitgliedergruppen](/help/communities/users.md#privilegedmembersgroups).

   * **`Trashcan icon`**
Entfernen (Löschen) von Funktionen aus der Site-Struktur.

   * **`Grid icon`**
Ändern Sie die Reihenfolge der Funktionen, die in der Navigationsleiste auf der obersten Navigationsebene der Site angezeigt werden.

>[!CAUTION]
>
>Der Anzeigentitel kann zwar ohne Nebenwirkungen geändert werden, es wird jedoch nicht empfohlen, den URL-Namen einer Community-Funktion zu bearbeiten, die zu einer Community-Site gehört.
>
>Wenn Sie beispielsweise die URL umbenennen, wird die vorhandene UGC nicht verschoben, sodass die UGC verliert wird.

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;darf weder die Funktion *first noch die Funktion* in der Sitestruktur sein.**
>
>Jede andere Funktion, wie z. B. die Funktion [page](/help/communities/functions.md#page-function), muss eingeschlossen und zuerst aufgelistet werden.

**Beispiel: Hinzufügen einer Kalenderfunktion zu einer UnterCommunity-(Gruppen-)Struktur**

![community-group-add-calendar](assets/community-group-add-calendar.png)

### Design ändern {#modify-design}

Das DESIGN-Bedienfeld ermöglicht die Änderung des Designs:

* [Community-Gruppen-Design](#community-group-theme)
* [Community-Gruppen-Branding](#community-group-branding)

   * Blättern Sie nach unten im Bedienfeld, um das Markenbild zu ändern.

### Einstellungen ändern {#modify-settings}

Das Bedienfeld &quot;EINSTELLUNGEN&quot;ermöglicht es, Community [Moderatoren](#moderation) hinzuzufügen.

### Mitgliedschaft ändern {#modify-membership}

Das Fenster [MEMBERSHIP](#membership) enthält nur Informationen. Es ist nicht möglich, die Art der Gruppenmitgliedschaft zu ändern, unabhängig davon, ob sie freiwillig, erforderlich oder eingeschränkt ist.

### Miniaturansicht ändern {#modify-thumbnail}

Das Bedienfeld [THUMBNAIL](#thumbnail) ermöglicht es, ein Bild hochzuladen, das die Community-Gruppe für Site-Besucher in der Veröffentlichungs-Umgebung sowie in der Communities Site-Gruppenkonsole in der Autor-Umgebung darstellt.

## Veröffentlichen Sie die Gruppe {#publish-the-group}

![publish-site](assets/publish-site.png)

Nachdem eine Community-Gruppe neu erstellt oder geändert wurde, kann die Gruppe durch Auswahl des Symbols `Publish Site` veröffentlicht (aktiviert) werden.

Nachdem die Gruppe erfolgreich veröffentlicht wurde, wird eine Meldung angezeigt:

![group-published](assets/group-published.png)

>[!CAUTION]
>
>Die übergeordnete Community-Site und die übergeordneten Gruppen hätten bereits veröffentlicht werden sollen.
>
>Die Community-Site und verschachtelte Gruppen sollten von oben nach unten veröffentlicht werden.

## Löschen Sie die Gruppe {#delete-the-group}

![Löschsymbol](assets/deleteicon.png)

Löschen Sie eine Gruppe aus der Community-Gruppenkonsole, indem Sie auf das Symbol &quot;Gruppe löschen&quot;klicken, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppe halten.

Dadurch werden alle mit der Gruppe verknüpften Elemente entfernt, zum Beispiel wird der gesamte Inhalt der Gruppe dauerhaft gelöscht und die Benutzermitgliedschaften werden aus dem System entfernt.
