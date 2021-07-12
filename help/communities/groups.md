---
title: Konsole für Community-Gruppen
seo-title: Konsole für Community-Gruppen
description: Gruppenkonsole ermöglicht die Erstellung von Community-Gruppen
seo-description: Gruppenkonsole ermöglicht die Erstellung von Community-Gruppen
uuid: 21e2bde3-7354-4193-bcb3-c672c6342252
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d381ea40-fe49-4d32-bfad-1379c7a02aba
docset: aem65
pagetitle: Community Groups Console
role: Admin
exl-id: ef371ff8-6b4f-4e5a-98fb-d7c274927c46
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '1678'
ht-degree: 3%

---

# Konsole für Community-Gruppen {#community-groups-console}

Die Gruppenkonsole bietet Zugriff auf das Erstellen von Community-Gruppen, wenn die [Vorlagenstruktur](/help/communities/sites-console.md#step1) einer Community-Site die [Gruppenfunktion](/help/communities/functions.md#groups-function) enthält.

* AEM Communities unterstützt die Verschachtelung von Gruppen innerhalb anderer Gruppen. Gruppenverschachtelung ist möglich, wenn die [Struktur der neuen Gruppe](/help/communities/tools-groups.md) die Gruppenfunktion enthält.
* Nur für die Autorenumgebung gibt es einen Gruppenerstellungsassistenten, der dem Erstellungsassistenten für die Site ähnelt.
* Ob Mitglieder Gruppen in der Veröffentlichungsumgebung erstellen können (oder nicht), ist beim Hinzufügen einer Gruppenfunktion zu einer Community-Site-Struktur oder einer Community-Gruppenstruktur konfigurierbar.

Von den drei enthaltenen Gruppenvorlagen enthält nur die Vorlage `Reference Group` eine Gruppenfunktion in ihrer Struktur.

Die verschiedenen Facetten von Community-Gruppen sind:

* **Erstellung**: neue Gruppen können auf der Autoren- und optional auf der Veröffentlichungsinstanz erstellt werden.
* **Kontrolle**: -Gruppe kann offen oder geheim sein.
* **Verschachtelung**: -Gruppe kann null oder mehr Gruppen enthalten.

<!-- This is a 404 on helpx. Please update or remove.
>[!NOTE]
>
>Community groups, created in the publish environment before the [existence of the Community Groups console](/help/communities/version-history.md#featurepack1fp1), will not be listed in the Community Groups console, and thus, are not modifiable using the console.
-->

>[!NOTE]
>
>Diese Gruppenkonsole, auf die nur über die Communities Sites-Konsole zugegriffen werden kann, ist nicht mit dem Mitglied [Gruppenkonsole](/help/communities/members.md) für die Verwaltung von Mitgliedergruppen zu verwechseln.
>
>Mitgliedergruppen sind Benutzergruppen, die in der Veröffentlichungsumgebung registriert sind und über die Autorenumgebung mit dem [Tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author) aufgerufen werden.

## Gruppenerstellung {#group-creation}

So greifen Sie auf die Gruppenkonsole zu:

* Beim Autor können Sie sich mit Administratorrechten anmelden.
* Über die globale Navigation: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.
* Wählen Sie einen vorhandenen Community-Site-Ordner aus, um ihn zu öffnen.
* Wählen Sie eine Instanz einer Community-Site im Ordner aus.

   * Die Struktur der Community-Site muss eine Gruppenfunktion enthalten.
   * Diese Screenshots stammen aus dem Tutorial Erste Schritte nach [Erstellen von Gruppen bei der Veröffentlichung](/help/communities/published-site.md).

   ![create-group](assets/create-group.png)

* Wählen Sie den Ordner **Gruppen** aus, um ihn zu öffnen.

   Beim Öffnen werden alle vorhandenen Gruppen angezeigt, unabhängig davon, ob sie im Autor- oder Veröffentlichungsmodus erstellt wurden.

   In dieser Gruppenkonsole ist es möglich, neue Gruppen zu erstellen.

   ![create-new-group](assets/create-new-group.png)

* Wählen Sie die Schaltfläche **Gruppe erstellen** aus.

### Schritt 1: Community-Gruppenvorlage {#step-community-group-template}

![Mehrsprachige Community-Gruppen](assets/multi-lingual-group.png)

* **Community-Gruppenname**

   Ein Anzeigetitel für die Gruppe.
Der Titel wird auf der veröffentlichten Site für die Gruppe angezeigt.

* **Community-Gruppenbeschreibung**

   Eine Beschreibung der Gruppe.

* **Community-Gruppen-Stammverzeichnis**

   Der Stammpfad zur Gruppe.
Der Standardstamm ist die übergeordnete Site, der Stammordner kann jedoch an einen beliebigen Speicherort auf der Website verschoben werden. Es wird nicht empfohlen, sie zu ändern.

* **** Menü &quot;Zusätzliche verfügbare Community-Gruppensprachen&quot;

   Wählen Sie in der Dropdown-Liste die verfügbaren Gemeinschaftsgruppensprachen aus. Im Menü werden alle Sprachen angezeigt, in denen die übergeordnete Community-Site erstellt wird. Benutzer können in diesem Schritt unter diesen Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.

* **Community-Gruppenname**

   Der Name der Stammseite der Gruppe, der in der URL angezeigt wird.

   * Überprüfen Sie den Namen, da er nach der Erstellung der Gruppe nicht einfach geändert werden kann.
   * Die Basis-URL wird unter `Community Group Name` angezeigt.
   * Hängen Sie für eine gültige URL &quot;.html&quot;an.
      *z. B.*  `https://localhost:4502/content/sites/mysight/en/mygroup.html`.

* **Community-Gruppenvorlagen-** Menü

   Verwenden Sie das Dropdown-Menü, um eine verfügbare [Community-Gruppenvorlage](/help/communities/tools.md) auszuwählen.

### Schritt 2: Design {#step-design}

### GEMEINSCHAFTSGRUPPENTHEMEN {#community-group-theme}

![communityGrouptheme](assets/communitygrouptheme.png)

Das Framework verwendet [Twitter Bootstrap](https://twitterbootstrap.org/), um ein responsives, flexibles Design auf die Site zu bringen. Es kann eines der vielen vorab geladenen Bootstrap-Designs ausgewählt werden, um die ausgewählte Community-Gruppenvorlage zu formatieren, oder ein Bootstrap-Design kann hochgeladen werden.

Wenn diese Option aktiviert ist, wird das Design mit einem undurchsichtigen blauen Häkchen überlagert.

Es ist möglich, ein Design auszuwählen, das sich vom Design der übergeordneten Site unterscheidet.

Nachdem die Community-Site veröffentlicht wurde, können Sie [die Eigenschaften](#modifyinggroupproperties) bearbeiten und ein anderes Design auswählen.

### GEMEINSCHAFTSGRUPPENBRANCHE {#community-group-branding}

![community-group-branding](assets/community-group-branding.png)

Community-Site-Branding ist ein Bild, das oben auf jeder Seite als Kopfzeile angezeigt wird. Es ist möglich, ein Banner für die Gruppe anzuzeigen, das sich von anderen Seiten der Site unterscheidet.

Die Bildgröße sollte der erwarteten Anzeige der Seite im Browser und einer Höhe von 120 Pixel entsprechen.

Beachten Sie beim Erstellen oder Auswählen eines Bildes Folgendes:

* Die Bildhöhe wird vom oberen Rand des Bildes auf 120 Pixel zugeschnitten
* Das Bild wird am linken Rand des Browser-Fensters fixiert
* Die Größe des Bildes wird nicht geändert, d. h. wenn die Bildbreite beträgt:

   * Weniger breit als der Browser, wird das Bild horizontal wiederholt.
   * Größer als die Breite des Browsers, wird das Bild scheinbar zugeschnitten.

### Schritt 3: Einstellungen {#step-settings}

**MODERATION**

![Community-Gruppenmitglieder auswählen](assets/group-admin.png)

**Community-Gruppenmoderatoren**

Standardmäßig wird die Liste der Moderatoren der übergeordneten Community-Site übernommen.

Es ist möglich, für die Gruppe spezifische Moderatoren hinzuzufügen. Suchen Sie nach Mitgliedern (aus der Veröffentlichungsumgebung), um sie als Moderatoren hinzuzufügen.

**Gruppenadministratoren**

Standardmäßig ist auch der Administrator der übergeordneten Community-Site der Administrator für Gruppen.

Es ist jedoch möglich, unabhängige Gruppenadministratoren zuzuweisen. Gruppenadministratoren können ihre Gruppe verwalten (z. B. G1) und eine Untergruppe erstellen, die unter G1 verschachtelt ist. Sie können weitere verschiedene Administratoren für die Untergruppe zuweisen.

Ein Benutzer U1 kann daher ein Administrator in einer Gruppe G1 und ein regulärer Benutzer in der verschachtelten Gruppe G2 sein.

**MITGLIEDSCHAFT**

Die Mitgliedschaftseinstellung ermöglicht die Auswahl einer der drei Möglichkeiten, eine Community-Gruppe zu sichern.

![community-group-membership](assets/community-group-membership.png)

* **Optionale Mitgliedschaft**

   Wenn diese Option ausgewählt ist, ist die Community-Gruppe eine öffentliche Gruppe. Mitglieder der Site können an der Gruppe teilnehmen und Beiträge posten, ohne sich explizit der Gruppe anzuschließen. Diese Option ist standardmäßig ausgewählt.

* **Erforderliche Mitgliedschaft**

   Wenn diese Option ausgewählt ist, ist die Community-Gruppe eine offene Gruppe. Community-Site-Mitglieder können den Inhalt der Gruppe anzeigen, müssen jedoch der Gruppe beitreten, um Inhalte zu posten. Mitglieder werden durch Auswahl der Schaltfläche `Join` in der Veröffentlichungsumgebung hinzugefügt. Die Option Standard ist nicht ausgewählt.

* **Eingeschränkte Mitgliedschaft**

   Wenn diese Option ausgewählt ist, ist die Community-Gruppe eine geheime Gruppe. Die Mitglieder der Gemeinschaft müssen ausdrücklich eingeladen werden. Eingeladene Mitglieder werden in das Suchfeld eingegeben. Mitglieder können später mithilfe der [Mitglieder und Gruppen-Konsolen](/help/communities/members.md) der Autorenumgebung hinzugefügt werden. Die Option Standard ist nicht ausgewählt.

**MINIATUR**

![community-group-thumbnail](assets/community-group-thumbnail.png)

Die Miniaturansicht ist ein Bild, das für die Gruppe bei der Autoren- und Veröffentlichungsinstanz angezeigt wird.

Die optimale Größe für ein Gruppenbild beträgt 170 x 90 Pixel in einem unterstützten Bildformat (z. B. JPG oder PNG).

Wenn kein Bild hinzugefügt wird, wird ein Standardbild angezeigt.

![thumbnail-image](assets/thumbnail-image.png)

### Schritt 4: Gruppe erstellen {#step-create-group}

![community-create-group](assets/community-create-group.png)

Wenn Anpassungen erforderlich sind, verwenden Sie die Schaltfläche **Zurück** , um sie vorzunehmen.

Nachdem **Create** ausgewählt und gestartet wurde, kann der Prozess zur Erstellung der Gruppe nicht mehr unterbrochen werden.

Nach Abschluss des Vorgangs wird die Karte für die neue Unter-Community-Site (Gruppe) in der Communities Sites-Gruppen-Konsole angezeigt, über die Autoren Seiteninhalte hinzufügen können oder Administratoren die Eigenschaften der Site ändern können.

![Community-Gruppe erstellen](assets/create-community-groups.png)

>[!NOTE]
>
>Die Gruppe wird in allen Sprachen erstellt, wie in [Schritt 1 beschrieben: Community-Gruppenvorlage](/help/communities/groups.md#step-community-group-template) in Zusätzliche verfügbare Community-Gruppensprachen in der Community-Gruppenkonsole der jeweiligen Community-Sites.

## Inhalt der Autorengruppe {#author-group-content}

![open-site](assets/open-site.png)

Der Seiteninhalt einer Gruppe kann mit denselben Tools wie jede andere AEM erstellt werden. Um die Gruppe für die Bearbeitung zu öffnen, wählen Sie das Symbol Site öffnen aus, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen.

## Gruppeneigenschaften ändern {#modify-group-properties}

Die Eigenschaften einer vorhandenen Unter-Community-Site, die während des Erstellungsprozesses einer Community-Gruppe angegeben wird, können geändert werden, indem Sie das Symbol Site bearbeiten auswählen, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen:

![edit-site](assets/edit-site.png)

Die Details der folgenden Eigenschaften entsprechen den Beschreibungen, die im Abschnitt [Gruppenerstellung](#group-creation) beschrieben werden. Jede verschachtelte Gruppe kann geändert werden, unabhängig davon, ob sie in der Veröffentlichungsumgebung oder in der Autorenumgebung erstellt wurde.

![community-group-basic](assets/community-group-basic.png)

### Standard ändern {#modify-basic}

Das BASIC-Bedienfeld ermöglicht die Änderung von

* Community-Gruppenname
* Community-Gruppenbeschreibung

Der Community-Gruppenname darf nicht geändert werden.

Die Auswahl einer anderen Community-Gruppenvorlage hätte keine Auswirkungen auf eine bestehende Community-Gruppensite, da keine Verbindung zwischen Vorlagen und Sites besteht.

Stattdessen kann die [STRUKTUR](#modify-structure) der Unter-Community geändert werden.

### Struktur ändern {#modify-structure}

Das Bedienfeld STRUKTUR ermöglicht die Änderung der Struktur, die ursprünglich aus der Community-Gruppenvorlage erstellt wurde, die beim Erstellen der Unter-Community-Site aus der Autoren- oder Veröffentlichungsumgebung ausgewählt wurde. Im Bedienfeld haben Sie folgende Möglichkeiten:

* Ziehen Sie zusätzliche [Community-Funktionen](/help/communities/functions.md) per Drag-and-Drop in die Site-Struktur.
* Auf einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`Gear icon`**
Einstellungen bearbeiten, einschließlich Anzeigentitel, URL und  [privilegierten Mitgliedergruppen](/help/communities/users.md#privilegedmembersgroups).

   * **`Trashcan icon`**
Entfernen (Löschen) von Funktionen aus der Site-Struktur.

   * **`Grid icon`**
Ändern Sie die Reihenfolge der Funktionen, wie sie in der Navigationsleiste auf oberster Ebene der Site angezeigt werden.

>[!CAUTION]
>
>Der Anzeigentitel kann ohne Nebenwirkungen geändert werden. Es wird jedoch nicht empfohlen, den URL-Namen einer Community-Funktion zu bearbeiten, die zu einer Community-Site gehört.
>
>Wenn Sie beispielsweise die URL umbenennen, werden vorhandene UGC nicht verschoben, sodass der UGC-Wert &quot;verloren&quot;wird.

>[!CAUTION]
>
>Die Gruppenfunktion muss *nicht* die *erste und nicht die einzige* Funktion in der Site-Struktur sein.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](/help/communities/functions.md#page-function), muss zuerst eingeschlossen und aufgelistet werden.

**Beispiel: Hinzufügen einer Kalenderfunktion zu einer SubCommunity-Struktur (Gruppe)**

![community-group-add-calendar](assets/community-group-add-calendar.png)

### Design ändern {#modify-design}

Das DESIGN-Bedienfeld ermöglicht die Änderung des Designs:

* [Community-Gruppen-Design](#community-group-theme)
* [Community-Gruppen-Branding](#community-group-branding)

   * Scrollen Sie zum unteren Rand des Bedienfelds, um das Markenbild zu ändern.

### Einstellungen ändern {#modify-settings}

Das Bedienfeld EINSTELLUNGEN bietet die Möglichkeit, Community [Moderatoren](#moderation) hinzuzufügen.

### Mitgliedschaft ändern {#modify-membership}

Das Bedienfeld [MEMBERSHIP](#membership) ist nur informativ. Es ist nicht möglich, die Art der festgelegten Gruppenmitgliedschaft zu ändern, unabhängig davon, ob sie optional, erforderlich oder eingeschränkt ist.

### Miniaturansicht ändern {#modify-thumbnail}

Das Bedienfeld [MINIATURANSICHT](#thumbnail) ermöglicht das Hochladen eines Bildes, das die Community-Gruppe für Site-Besucher in der Veröffentlichungsumgebung sowie in der Gruppenkonsole der Communities-Site in der Autorenumgebung darstellt.

## Gruppe veröffentlichen {#publish-the-group}

![publish-site](assets/publish-site.png)

Nachdem eine Community-Gruppe neu erstellt oder geändert wurde, kann sie durch Auswahl des Symbols `Publish Site` veröffentlicht (aktiviert) werden.

Nachdem die Gruppe erfolgreich veröffentlicht wurde, wird eine Meldung angezeigt:

![group-publish](assets/group-published.png)

>[!CAUTION]
>
>Die übergeordnete Community-Site und die übergeordneten Gruppen sollten bereits veröffentlicht worden sein.
>
>Die Community-Site und verschachtelte Gruppen sollten von oben nach unten veröffentlicht werden.

## Gruppe löschen {#delete-the-group}

![Löschsymbol](assets/deleteicon.png)

Löschen Sie eine Gruppe aus der Community-Gruppenkonsole, indem Sie auf das Symbol Gruppe löschen klicken, das beim Bewegen der Maus über die Gruppe angezeigt wird.

Dadurch werden alle mit der Gruppe verknüpften Elemente entfernt, z. B. der gesamte Inhalt der Gruppe wird dauerhaft gelöscht und die Benutzermitgliedschaften werden aus dem System entfernt.
