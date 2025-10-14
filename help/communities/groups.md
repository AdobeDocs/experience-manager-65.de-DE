---
title: Konsole für Community-Gruppen
description: Erfahren Sie mehr über die Konsole „Community-Gruppen“, mit der Sie Community-Gruppen erstellen können, wenn die Vorlagenstruktur einer Community-Site die Funktion „Gruppen“ enthält.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
pagetitle: Community Groups Console
role: Admin
exl-id: ef371ff8-6b4f-4e5a-98fb-d7c274927c46
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 1%

---

# Konsole für Community-Gruppen {#community-groups-console}

Die Gruppen -Konsole bietet Zugriff auf das Erstellen von Community-Gruppen, wenn die [Vorlagenstruktur](/help/communities/sites-console.md#step1) einer Community-Site die Funktion [Gruppen](/help/communities/functions.md#groups-function) enthält.

* AEM Communities unterstützt die Verschachtelung von Gruppen in anderen Gruppen. Die Gruppenverschachtelung ist möglich, wenn die [Struktur der neuen Gruppe](/help/communities/tools-groups.md) die Gruppenfunktion enthält.
* Nur für die Autorenumgebung gibt es einen Assistenten für die Gruppenerstellung, der dem Assistenten für die Site-Erstellung ähnelt.
* Ob Mitglieder in der Veröffentlichungsumgebung Gruppen erstellen können oder nicht, ist beim Hinzufügen einer Gruppenfunktion zu einer Community-Site- oder Community-Gruppenstruktur konfigurierbar.

Von den drei enthaltenen Gruppenvorlagen enthält nur die `Reference Group` eine Gruppenfunktion in ihrer Struktur.

Die verschiedenen Facetten von Community-Gruppen sind:

* **Erstellung**: Neue Gruppe kann in der Autoreninstanz und optional in der Veröffentlichungsinstanz erstellt werden.
* **Kontrolle**: Gruppe kann offen oder geheim sein.
* **Verschachtelung**: Gruppe kann null oder mehr Gruppen enthalten.

<!-- This is a 404 on helpx. Update or remove.
>[!NOTE]
>
>Community groups, created in the publish environment before the [existence of the Community Groups console](/help/communities/version-history.md#featurepack1fp1), is not listed in the Community Groups console, and thus, are not modifiable using the console.
-->

>[!NOTE]
>
>Diese Gruppen -Konsole, auf die nur über die Communities-Sites -Konsole zugegriffen werden kann, ist nicht mit der Mitglieds-(Gruppen[Konsole) &#x200B;](/help/communities/members.md) die Verwaltung von Mitgliedergruppen zu verwechseln.
>
>Mitgliedsgruppen sind Benutzergruppen, die in der Veröffentlichungsumgebung registriert sind und über die Autorenumgebung mithilfe des [Tunnelservice](/help/communities/deploy-communities.md#tunnel-service-on-author) aufgerufen werden.

## Gruppenerstellung {#group-creation}

So greifen Sie auf die Gruppenkonsole zu:

* Melden Sie sich in der Autoreninstanz mit Administratorrechten an.
* Von der globalen Navigation: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.
* Wählen Sie einen vorhandenen Community-Site-Ordner aus, damit Sie ihn öffnen können.
* Wählen Sie eine Instanz einer Community-Site im Ordner aus.

   * Die Struktur der Community-Site muss eine Gruppenfunktion enthalten.
   * Diese Screenshots stammen aus dem Tutorial Erste Schritte nach [Erstellen von Gruppen in der &#x200B;](/help/communities/published-site.md)).

  ![create-group](assets/create-group.png)

* Wählen Sie den **Ordner „Gruppen** aus, damit Sie ihn öffnen können.

  Wenn sie geöffnet wird, werden alle vorhandenen Gruppen angezeigt, unabhängig davon, ob sie in der Autoreninstanz oder in Publish erstellt wurden.

  In dieser Gruppen -Konsole ist es möglich, neue Gruppen zu erstellen.

  ![create-new-group](assets/create-new-group.png)

* Klicken Sie auf **Schaltfläche Gruppe** .

### Schritt 1: Community-Gruppenvorlage {#step-community-group-template}

![Mehrsprachige Community-Gruppen](assets/multi-lingual-group.png)

* **Community-Gruppentitel**

  Ein Anzeigetitel für die Gruppe.
Der Titel wird für die Gruppe auf der veröffentlichten Site angezeigt.

* **Community-Gruppenbeschreibung**

  Eine Beschreibung der Gruppe.

* **Community-Gruppenstamm**

  Der Stammpfad zur Gruppe.
Der Standardstamm ist die übergeordnete Website, der Stamm kann jedoch an eine beliebige Stelle innerhalb der Website verschoben werden. Es wird nicht empfohlen, sie zu ändern.

* **Weitere verfügbare Community-Gruppensprachen** Menü

  Wählen Sie über die Dropdown-Liste die verfügbaren Community-Gruppensprachen aus. Das Menü zeigt alle Sprachen an, in denen die übergeordnete Community-Site erstellt wird. Benutzer können in diesem Schritt eine dieser Sprachen auswählen, um Gruppen in mehreren Gebietsschemata zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.

* **Community-Gruppenname**

  Der Name der Stammseite der Gruppe, der in der URL angezeigt wird. Vermeiden Sie Unterstriche (_) und Schlüsselwörter wie Ressourcen und Konfiguration im Gruppennamen.

   * Überprüfen Sie den Namen, da er nach der Erstellung der Gruppe nicht einfach geändert werden kann.
   * Die Basis-URL wird unter dem `Community Group Name` angezeigt.
   * Hängen Sie für eine gültige URL &quot;.html“ an

     *zum*, `https://localhost:4502/content/sites/mysight/en/mygroup.html`.

* **Community-Gruppenvorlage** Menü

  Wählen Sie über die Dropdown-Liste eine verfügbare [Community-Gruppenvorlage](/help/communities/tools.md) aus.

### Schritt 2: Entwurf {#step-design}

### COMMUNITY-GRUPPEN-DESIGN {#community-group-theme}

![communityGroupTheme](assets/communitygrouptheme.png)

Das Framework verwendet `Twitter Bootstrap`, um der Site ein responsives, flexibles Design zu verleihen. Eines der vielen vorab geladenen Bootstrap-Designs kann ausgewählt werden, um die ausgewählte Community-Gruppenvorlage zu gestalten, oder ein Bootstrap-Design kann hochgeladen werden.

Wenn diese Option aktiviert ist, wird das Design mit einem opaken blauen Häkchen überlagert.

Es ist möglich, ein Design auszuwählen, das sich vom Design der übergeordneten Site unterscheidet.

Nachdem die Community-Site veröffentlicht wurde, können Sie [die Eigenschaften bearbeiten](#modifyinggroupproperties) und ein anderes Design auswählen.

### COMMUNITY-BRANDING {#community-group-branding}

![Community-Group-Branding](assets/community-group-branding.png)

Das Community-Website-Branding ist ein Bild, das als Kopfzeile am oberen Rand jeder Seite angezeigt wird. Es ist möglich, ein Banner für die Gruppe anzuzeigen, das sich von anderen Seiten der Site unterscheidet.

Das Bild sollte so breit wie die erwartete Anzeige der Seite im Browser und 120 Pixel hoch sein.

Beachten Sie beim Erstellen oder Auswählen eines Bildes Folgendes:

* Die Bildhöhe wird auf 120 Pixel abgeschnitten, gemessen vom oberen Rand des Bildes
* Das Bild wird an den linken Rand des Browser-Fensters angeheftet
* Es gibt keine Größenanpassung des Bildes, sodass wenn die Bildbreite:

   * Das Bild wird horizontal wiederholt, wenn es weniger breit ist als der Browser.
   * Größer als die Breite des Browsers wird das Bild abgeschnitten.

### Schritt 3: Einstellungen {#step-settings}

**MODERATION**

![Community-Gruppenmitgliedsrollen auswählen](assets/group-admin.png)

**Community-Gruppenmoderatoren**

Standardmäßig wird die Moderatorenliste der übergeordneten Community-Site übernommen.

Es ist möglich, Moderatoren speziell zur Gruppe hinzuzufügen. Mitglieder suchen (aus der Veröffentlichungsumgebung), um sie als Moderatoren hinzuzufügen

**Gruppenadministratoren**

Standardmäßig ist der Administrator der übergeordneten Community-Site auch der Administrator für Gruppen.

Es ist jedoch möglich, unabhängige Gruppenadministratoren zuzuweisen. Gruppenadministratoren können ihre Gruppe verwalten (z. B. G1) und eine Untergruppe erstellen, die unter G1 verschachtelt ist. Sie können außerdem verschiedene Administratoren für die Untergruppe zuweisen.

Ein Benutzer U1 kann daher Administrator in einer Gruppe G1 und regulärer Benutzer in seiner verschachtelten Gruppe G2 sein.

**MITGLIEDSCHAFT**

Die Mitgliedschaftseinstellung ermöglicht die Auswahl einer der drei Möglichkeiten, eine Community-Gruppe zu sichern.

![community-group-membership](assets/community-group-membership.png)

* **Optionale Mitgliedschaft**

  Wenn diese Option aktiviert ist, ist die Community-Gruppe eine öffentliche Gruppe. Site-Mitglieder können an der Gruppe teilnehmen und Beiträge veröffentlichen, ohne explizit der Gruppe beizutreten. Standard ist ausgewählt.

* **Erforderliche Mitgliedschaft**

  Wenn diese Option aktiviert ist, ist die Community-Gruppe eine offene Gruppe. Community-Site-Mitglieder können die Inhalte der Gruppe anzeigen, müssen sich jedoch der Gruppe anschließen, um Inhalte zu veröffentlichen. Mitglieder treten bei, indem sie in der Veröffentlichungsumgebung auf die Schaltfläche `Join` klicken. Standard ist nicht ausgewählt.

* **Eingeschränkte Mitgliedschaft**

  Wenn diese Option aktiviert ist, ist die Community-Gruppe eine geheime Gruppe. Community-Mitglieder müssen ausdrücklich eingeladen werden. Eingeladene Mitglieder werden in das Suchfeld eingegeben. Mitglieder können später über die Konsolen [Mitglieder und Gruppen“ in &#x200B;](/help/communities/members.md) Autorenumgebung hinzugefügt werden. Standard ist nicht ausgewählt.

**MINIATURANSICHT**

![community-group-thumbnail](assets/community-group-thumbnail.png)

Die Miniaturansicht ist ein Bild, das für die Gruppe in der Autoren- und Veröffentlichungsinstanz angezeigt wird.

Die optimale Größe für ein Gruppenbild ist 170 x 90 Pixel in einem unterstützten Bildformat (z. B. JPG oder PNG).

Wenn kein Bild hinzugefügt wird, wird ein Standardbild angezeigt.

![thumbnail-image](assets/thumbnail-image.png)

### Schritt 4: Gruppe erstellen {#step-create-group}

![community-create-group](assets/community-create-group.png)

Wenn Anpassungen erforderlich sind, verwenden Sie die Schaltfläche **Zurück**, um diese vorzunehmen.

Sobald **Erstellen** ausgewählt und gestartet wurde, kann der Prozess der Erstellung der Gruppe nicht mehr unterbrochen werden.

Wenn der Prozess abgeschlossen ist, wird die Karte für die neue Subcommunity-Site (Gruppe) in der Communities Sites-Gruppen-Konsole angezeigt, wo Autoren Seiteninhalte hinzufügen können oder Administratoren die Eigenschaften der Site ändern können.

![Community-Gruppe erstellen](assets/create-community-groups.png)

>[!NOTE]
>
>Die Gruppe wird in allen Sprachen erstellt, wie in [Schritt 1: Community-Gruppenvorlage](/help/communities/groups.md#step-community-group-template) in Zusätzliche verfügbare Community-Gruppensprachen in der Community-Gruppenkonsole der jeweiligen Community-Sites angegeben.

## Authoring von Gruppeninhalten {#author-group-content}

![open-site](assets/open-site.png)

Der Seiteninhalt einer Gruppe kann mit denselben Tools wie jede andere AEM-Seite erstellt werden. Um die Gruppe für das Authoring zu öffnen, wählen Sie das Symbol Site öffnen aus, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen.

## Gruppeneigenschaften ändern {#modify-group-properties}

Die Eigenschaften einer bestehenden Subcommunity-Site, die während des Erstellungsprozesses einer Community-Gruppe festgelegt wurde, können geändert werden, indem Sie das Symbol Site bearbeiten auswählen, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen:

![edit-site](assets/edit-site.png)

Die Details der folgenden Eigenschaften entsprechen den Beschreibungen im Abschnitt [Gruppenerstellung](#group-creation) . Jede verschachtelte Gruppe kann geändert werden, unabhängig davon, ob sie in der Veröffentlichungsumgebung oder der Autorenumgebung erstellt wurde.

![community-group-basic](assets/community-group-basic.png)

### Einfach ändern {#modify-basic}

Das Bedienfeld „STANDARD“ ermöglicht die Änderung von

* Community-Gruppenname
* Community-Gruppenbeschreibung

Der Community-Gruppenname darf nicht geändert werden.

Die Auswahl einer anderen Community-Gruppenvorlage hätte keine Auswirkungen auf eine vorhandene Community-Gruppenwebsite, da keine Verbindung zwischen Vorlagen und Websites mehr besteht.

Stattdessen kann die [STRUKTUR](#modify-structure) der Untergemeinschaft geändert werden.

### Struktur ändern {#modify-structure}

Das Bedienfeld STRUKTUR ermöglicht das Ändern der Struktur, die ursprünglich aus der Community-Gruppenvorlage erstellt wurde, die beim Erstellen der Subcommunity-Site aus der Autoren- oder Veröffentlichungsumgebung ausgewählt wurde. Im Bedienfeld können Sie Folgendes tun:

* Ziehen Sie zusätzliche [Community-Funktionen](/help/communities/functions.md) per Drag-and-Drop in die Site-Struktur.
* Bei einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`Gear icon`**
Bearbeiten Sie Einstellungen, einschließlich Anzeigetitel, URL und [Gruppen privilegierter Mitglieder](/help/communities/users.md#privilegedmembersgroups).

   * **`Trashcan icon`**
Entfernen (Löschen) von Funktionen aus der Site-Struktur.

   * **`Grid icon`**
Ändern Sie die Reihenfolge der Funktionen, wie sie in der Navigationsleiste der obersten Ebene der Site angezeigt wird.

>[!CAUTION]
>
>Während der Anzeigetitel ohne Nebenwirkungen geändert werden kann, wird nicht empfohlen, den URL-Namen einer Community-Funktion zu bearbeiten, die zu einer Community-Site gehört.
>
>Durch das Umbenennen der URL werden beispielsweise vorhandene benutzergenerierte Inhalte nicht verschoben, daher wird der benutzergenerierte Inhalt „verloren“.

>[!CAUTION]
>
>Die Gruppenfunktion darf *nicht* die (*- oder einzige* Funktion in der Site-Struktur sein.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](/help/communities/functions.md#page-function), muss eingeschlossen und zuerst aufgeführt werden.

**Beispiel: Hinzufügen einer Kalenderfunktion zu einer Struktur einer Untergemeinschaft (Gruppe)**

![community-group-add-calendar](assets/community-group-add-calendar.png)

### Entwurf ändern {#modify-design}

Das Bedienfeld DESIGN ermöglicht die Änderung des Designs:

* [Community-Gruppen-Design](#community-group-theme)
* [Community-Gruppen-Branding](#community-group-branding)

   * Scrollen Sie zum unteren Rand des Bedienfelds, um das Markenbild zu ändern.

### Einstellungen ändern {#modify-settings}

Das Bedienfeld EINSTELLUNGEN ermöglicht das Hinzufügen von Community[Moderatoren](#moderation).

### Mitgliedschaft ändern {#modify-membership}

Das Bedienfeld [MITGLIEDSCHAFT](#membership) dient nur zu Informationszwecken. Es ist nicht möglich, die Art der eingerichteten Gruppenmitgliedschaft zu ändern, unabhängig davon, ob sie optional, erforderlich oder eingeschränkt ist.

### Miniaturansicht ändern {#modify-thumbnail}

Das [MINIATUR](#thumbnail)-Bedienfeld ermöglicht den Upload eines Bildes, das die Community-Gruppe für Site-Besucher in der Publish-Umgebung darstellt, und in die Communities-Site-Gruppenkonsole in der Autorenumgebung.

## Publish - die Gruppe {#publish-the-group}

![publish-site](assets/publish-site.png)

Nachdem eine Community-Gruppe neu erstellt oder geändert wurde, können Sie die Gruppe veröffentlichen (aktivieren), indem Sie auf das Symbol `Publish Site` klicken.

Nach erfolgreicher Veröffentlichung der Gruppe wird die folgende Meldung angezeigt:

![group-published](assets/group-published.png)

>[!CAUTION]
>
>Die übergeordnete Community-Site und die übergeordneten Gruppen sollten bereits veröffentlicht worden sein.
>
>Die Community-Site und verschachtelte Gruppen sollten nach einem Top-Down-Ansatz veröffentlicht werden.

## Gruppe löschen {#delete-the-group}

![Löschsymbol](assets/deleteicon.png)

Löschen Sie eine Gruppe aus der Community-Gruppenkonsole, indem Sie das Symbol Gruppe löschen auswählen, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppe bewegen.

Dadurch werden alle mit der Gruppe verbundenen Elemente entfernt, z. B. wird der gesamte Inhalt der Gruppe dauerhaft gelöscht und Benutzermitgliedschaften werden aus dem System entfernt.
