---
title: Aktivitätstrends
seo-title: Aktivitätstrends
description: Hinzufügen einer Community-Aktivitätsliste-Komponente zu einer Seite
seo-description: Hinzufügen einer Community-Aktivitätsliste-Komponente zu einer Seite
uuid: 316aabf7-01a5-46da-be59-70c206eb6a3d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 4a0debdd-acb9-4646-80bb-fec66fae4088
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Aktivitätstrends{#activity-trends}

## Einführung {#introduction}

The `Community Activity List` component provides the ability to add trending information regarding posts and views by members as well as posts and views of content.

Das Dokument beschreibt:

* Hinzufügen der `Community Activity List` Komponente zu einer [Community-Site](/help/communities/overview.md#community-sites)

* Konfigurationseinstellungen für die Komponente `Community Activity List`

### Anforderung {#requirement}

Daten für die `Community Activity List` sind nur verfügbar, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

### Adding a Community Activity List to a Page {#adding-a-community-activity-list-to-a-page}

To add a `Community Activity List` component to a page in author mode, locate the component

* `Communities / Community Activity List`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![chlimage_1-54](assets/chlimage_1-54.png)

### Konfigurieren der Community-Aktivitätsliste {#configuring-community-activity-list}

Select the placed `Community Activity List` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-55](assets/chlimage_1-55.png)

Geben Sie unter der Registerkarte **Kommentare **an, ob und wie Kommentare für hochgeladene Dateien angezeigt werden:

![chlimage_1-56](assets/chlimage_1-56.png)

* **Typ**

   Geben Sie an, ob Daten zu Community-Mitgliedern oder benutzergenerierten Inhalten (UGC) angezeigt werden sollen.

   Die folgenden Optionen stehen zur Auswahl

   * `Members`
   * `Content`
   Der Standardwert ist `Members`.

* **Anzeigetitel**

   Ein beschreibender Titel, der über den Daten angezeigt werden soll, z. B. `Trending Content`.
Standardmäßig ist kein Name eingegeben.

* **Anzeigezahl**

   Die Anzahl der anzuzeigenden Elemente.
Der Standardwert ist 10.

* **Aktivitätstyp**

   Wählen Sie eines von

   * `Views`(Seitenbesuche)
   * `Posts`(UGC erstellen)
   * `Follows`
   * `Likes`
   Die Standardeinstellung lautet „Ansichten“.

* **Zeitraum**

   Wählen Sie eines von

   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`
   Der Standardwert ist `Total`.

* **Kontextpfad**

   Bietet die Möglichkeit, die Aktivität auf eine Teilmenge der Site zu beschränken, z. B. auf einen bestimmten Blog.
Standardmäßig ist die Community-Site ausgewählt.

* **Gesammelte Mitgliederzahl**

   Wenn diese Option deaktiviert ist, werden nur Beiträge der obersten Ebene gezählt. For example, if the context is the root page (the default), then an `Activity Type`of `Posts`will never show any activity as there is no ability to post content to the root page. Ist diese Option aktiviert, werden auch die Ergebnisse aller untergeordneten Seiten eingeschlossen.
Diese Option ist standardmäßig aktiviert.

### Beispielseite mit vier Komponenten {#example-page-with-components}

Konfiguration **Wichtigste Besucher** (Top Visitors): Typ = Mitglieder, Aktivitätstyp = Ansichten

**Konfiguration der wichtigsten Mitarbeiter** : Typ = Mitglieder, Aktivitätstyp = Beiträge

**Konfiguration des Hauptinhalts** : Typ = Inhalt, Aktivitätstyp = Ansichten,

**Konfigurieren des Trendinhalts** : Typ = Inhalt, Aktivitätstyp = Beiträge

![chlimage_1-57](assets/chlimage_1-57.png)

