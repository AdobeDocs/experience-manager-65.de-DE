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

Die Komponente `Community Activity List` bietet die Möglichkeit, Trendinformationen über Beiträge und Ansichten von Mitgliedern sowie Beiträge und Ansichten von Inhalten hinzuzufügen.

Das Dokument beschreibt:

* Hinzufügen der Komponente `Community Activity List` zu einer [Community-Site](/help/communities/overview.md#community-sites).

* Konfigurationseinstellungen für die Komponente `Community Activity List`.

### Anforderung {#requirement}

Daten für das `Community Activity List` stehen nur zur Verfügung, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

### Hinzufügen einer Community-Aktivität-Liste zu einer Seite {#adding-a-community-activity-list-to-a-page}

Um eine `Community Activity List`-Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente

* `Communities / Community Activity List`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](/help/communities/basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![community-Aktivität](assets/community-activity.png)

### Konfigurieren der Community-Aktivität-Liste {#configuring-community-activity-list}

Wählen Sie die platzierte Komponente `Community Activity List` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

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
   * `Posts`(UGC erstellen)
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

   Wenn diese Option deaktiviert (deaktiviert) ist, werden nur Beiträge der obersten Ebene gezählt. Wenn der Kontext z. B. die Stammseite ist (Standard), zeigt `Activity Type` von `Posts` keine Aktivität an, da es nicht möglich ist, Inhalte auf der Stammseite zu posten. Ist diese Option aktiviert, werden auch die Ergebnisse aller untergeordneten Seiten eingeschlossen.
Diese Option ist standardmäßig aktiviert.

### Beispielseite mit vier Komponenten {#example-page-with-components}

Konfiguration **Wichtigste Besucher** (Top Visitors): Typ = Mitglieder, Aktivitätstyp = Ansichten

**Top-** Mitarbeiter-Konfiguration: Typ = Member, Aktivität type = Beiträge

**Top-** ContentConfig: Typ = Aktivität, Typ = Ansichten,

**Trending** ContentConfig: Typ = Aktivität, Typ = Beiträge

![components](assets/activity-list-components.png)

