---
title: Aktivitätstrends
seo-title: Aktivitätstrends
description: Hinzufügen einer Liste zur Community-Aktivität zu einer Seite
seo-description: Hinzufügen einer Liste zur Community-Aktivität zu einer Seite
uuid: 316aabf7-01a5-46da-be59-70c206eb6a3d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 4a0debdd-acb9-4646-80bb-fec66fae4088
docset: aem65
translation-type: tm+mt
source-git-commit: c190d5f223c85f6c49fea1391d8a3d2baff20192
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 29%

---


# Aktivitätstrends {#activity-trends}

## Einführung {#introduction}

The `Community Activity List` component provides the ability to add trending information regarding posts and views by members as well as posts and views of content.

Das Dokument beschreibt:

* Hinzufügen der `Community Activity List` Komponente zu einer [Community-Site](/help/communities/overview.md#community-sites).

* Configuration settings for the `Community Activity List` component.

### Anforderung {#requirement}

Daten für die `Community Activity List` sind nur verfügbar, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

### Adding a Community Activity List to a Page {#adding-a-community-activity-list-to-a-page}

To add a `Community Activity List` component to a page in author mode, locate the component

* `Communities / Community Activity List`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![community-Aktivität](assets/community-activity.png)

### Liste der Community-Aktivität konfigurieren  {#configuring-community-activity-list}

Select the placed `Community Activity List` component to access and select the `Configure` icon which opens the edit dialog.

![konfigurieren](assets/configure-new.png)

Legen Sie auf der Registerkarte **Kommentare** fest, ob und wie Kommentare zu hochgeladenen Dateien angezeigt werden:

![Eigenschaften](assets/activity-list-properties.png)

* **Typ**

   Geben Sie an, ob Daten zu Community-Mitgliedern oder benutzergenerierten Inhalten (UGC) angezeigt werden sollen.

   Die folgenden Optionen stehen zur Auswahl:

   * `Members`
   * `Content`

   Der Standardwert ist `Members`.

* **Anzeigetitel**

   Ein beschreibender Titel, der über den Daten angezeigt werden soll, z. B. `Trending Content`.
Standardmäßig ist kein Name eingegeben.

* **Anzeigezahl**

   Die Anzahl der zu Liste Elemente.
Der Standardwert ist 10.

* **Aktivitätstyp**

   Wählen Sie eine der folgenden Optionen:

   * `Views`(Seitenbesuche)
   * `Posts`(Erstellen von UGC)
   * `Follows`
   * `Likes`

   Die Standardeinstellung lautet „Ansichten“.

* **Zeitraum**

   Wählen Sie eine der folgenden Optionen:

   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   Der Standardwert ist `Total`.

* **Kontextpfad**

   Bietet die Möglichkeit, die Aktivität auf eine Untergruppe der Site, z. B. einen bestimmten Blog, zu erweitern.
Standardmäßig ist die Community-Site ausgewählt.

* **Gesammelte Mitgliederzahl**

   Wenn diese Option deaktiviert ist, werden nur Beiträge der obersten Ebene gezählt. For example, if the context is the root page (the default), then an `Activity Type` of `Posts` will never show any activity as there is no ability to post content to the root page. Ist diese Option aktiviert, werden auch die Ergebnisse aller untergeordneten Seiten eingeschlossen.
Diese Option ist standardmäßig aktiviert.

### Beispielseite mit vier Komponenten {#example-page-with-components}

Konfiguration **Wichtigste Besucher** (Top Visitors): Typ = Mitglieder, Aktivitätstyp = Ansichten

**Konfiguration der wichtigsten Mitarbeiter** : Typ = Member, Aktivität type = Beiträge

**Konfiguration des Hauptinhalts** : Typ = Aktivität, Typ = Ansichten,

**Konfigurieren des Trendinhalts** : Typ = Aktivität, Typ = Beiträge

![components](assets/activity-list-components.png)

