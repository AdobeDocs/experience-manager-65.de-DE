---
title: Aktivitätstrends
description: Hinzufügen einer Community-Aktivitätenlisten-Komponente zu einer Seite
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2a4297e4-2d88-4fa6-8fea-3fea06753605
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 4%

---

# Aktivitätstrends {#activity-trends}

## Einführung {#introduction}

Mit der Komponente `Community Activity List` können Sie Trendinformationen zu Beiträgen und Ansichten von Mitgliedern und Beiträgen sowie Ansichten von Inhalten hinzufügen.

In dem Dokument wird Folgendes beschrieben:

* Hinzufügen der `Community Activity List` zu einer [Community-Site](/help/communities/overview.md#community-sites).

* Konfigurationseinstellungen für die `Community Activity List`.

### Anforderung {#requirement}

Daten für die `Community Activity List` sind nur verfügbar, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-](/help/communities/analytics.md).

### Hinzufügen einer Community-Aktivitätenliste zu einer Seite {#adding-a-community-activity-list-to-a-page}

Um einer Seite im Autorenmodus eine `Community Activity List` Komponente hinzuzufügen, suchen Sie die `Communities / Community Activity List` und ziehen Sie sie auf eine Seite.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Komponente zum ersten Mal auf einer Seite einer Community-Site platziert wird, wird sie wie folgt angezeigt:

![Community-Aktivität](assets/community-activity.png)

### Konfigurieren der Community-Aktivitätenliste  {#configuring-community-activity-list}

Wählen Sie die platzierte `Community Activity List` aus und klicken Sie auf das Symbol `Configure` , um das Dialogfeld „Bearbeiten“ zu öffnen.

![Konfigurieren](assets/configure-new.png)

Geben Sie auf **Registerkarte** Kommentare“ an, ob und wie Kommentare für hochgeladene Dateien angezeigt werden sollen:

![Eigenschaften](assets/activity-list-properties.png)

* **Typ**

  Geben Sie an, ob Daten zu Community-Mitgliedern oder benutzergenerierten Inhalten (UGC) angezeigt werden sollen.

  Die folgenden Optionen stehen zur Auswahl:

   * `Members`
   * `Content`

  Der Standardwert ist `Members`.

* **Titel anzeigen**

  Ein beschreibender Titel, der über den Daten angezeigt werden soll, z. B. `Trending Content`.
Standard ist kein Titel.

* **Anzahl anzeigen**

  Die Anzahl der aufzulistenden Elemente.
Der Standardwert lautet 10.

* **Aktivitätstyp**

  Eine der folgenden Optionen auswählen:

   * `Views`(Seitenbesuche)
   * `Posts`(Erstellen von benutzergenerierten Inhalten)
   * `Follows`
   * `Likes`

  Der Standardwert ist Ansichten.

* **Zeitraum**

  Eine der folgenden Optionen auswählen:

   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1)`
   * `Total`

  Der Standardwert ist `Total`.

* **Kontextpfad**

  Auf diese Weise können Sie die Aktivität auf eine Untergruppe der Site beschränken, z. B. auf einen bestimmten Blog.
Die Standardeinstellung ist die gesamte Community-Site.

* **Aggregation der Mitgliederzahl**

  Wenn diese Option deaktiviert (deaktiviert) ist, werden nur Beiträge der obersten Ebene gezählt. Wenn der Kontext beispielsweise die Stammseite ist (Standard), zeigt ein `Activity Type` von `Posts` keine Aktivität an, da keine Möglichkeit besteht, Inhalte auf der Stammseite zu posten. Wenn diese Option aktiviert ist, werden alle Zählungen für alle untergeordneten Seiten einbezogen.
Die Standardeinstellung ist aktiviert.

### Beispielseite mit vier Komponenten {#example-page-with-components}

**Top-Besucher** Konfiguration: Typ = Mitglieder, Aktivitätstyp = Ansichten

**Top Mitwirkende** Konfiguration: Typ = Mitglieder, Aktivitätstyp = Beiträge

**Top Content** config: type = Content, Activity type = Views,

**Trend-Inhalt** Konfiguration: Typ = Inhalt, Aktivitätstyp = Beiträge

![Komponenten](assets/activity-list-components.png)
