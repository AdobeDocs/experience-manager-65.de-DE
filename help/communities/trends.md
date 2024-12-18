---
title: Aktivitätstrends
description: Hinzufügen einer Community-Aktivitätslisten-Komponente zu einer Seite
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

Mit der Komponente `Community Activity List` können Sie Trendinformationen über Beiträge und Ansichten von Mitgliedern sowie Beiträge und Ansichten von Inhalten hinzufügen.

Das Dokument beschreibt:

* Hinzufügen der Komponente `Community Activity List` zu einer [Community-Site](/help/communities/overview.md#community-sites).

* Konfigurationseinstellungen für die Komponente `Community Activity List` .

### Anforderung {#requirement}

Daten für die `Community Activity List` sind nur verfügbar, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

### Hinzufügen einer Community-Aktivitätenliste zu einer Seite {#adding-a-community-activity-list-to-a-page}

Um eine `Community Activity List` -Komponente im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie die Komponente `Communities / Community Activity List` und ziehen Sie sie an die gewünschte Stelle auf einer Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die Komponente zum ersten Mal auf einer Seite einer Community-Site platziert wird, wird sie wie folgt angezeigt:

![community-activity](assets/community-activity.png)

### Konfigurieren der Community-Aktivitätenliste  {#configuring-community-activity-list}

Wählen Sie die platzierte Komponente `Community Activity List` und dann das Symbol `Configure` aus, damit Sie das Dialogfeld &quot;Bearbeiten&quot;öffnen können.

![configure](assets/configure-new.png)

Geben Sie auf der Registerkarte **Kommentare** an, ob und wie Kommentare für hochgeladene Dateien angezeigt werden sollen:

![Eigenschaften](assets/activity-list-properties.png)

* **Typ**

  Geben Sie an, ob Daten zu Community-Mitgliedern oder benutzergenerierten Inhalten angezeigt werden sollen.

  Die folgenden Optionen stehen zur Auswahl:

   * `Members`
   * `Content`

  Der Standardwert ist `Members`.

* **Titel anzeigen**

  Ein beschreibender Titel, der über den Daten angezeigt werden soll, z. B. `Trending Content`.
Standardmäßig ist kein Titel angegeben.

* **Anzahl der Anzeigen**

  Die Anzahl der aufzulistenden Elemente.
Der Standardwert lautet 10.

* **Aktivitätstyp**

  Wählen Sie eine der folgenden Optionen aus:

   * `Views`(Seitenbesuche)
   * `Posts`(Erstellen von UGC)
   * `Follows`
   * `Likes`

  Die Standardeinstellung ist &quot;Ansichten&quot;.

* **Zeitraum**

  Wählen Sie eine der folgenden Optionen aus:

   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1)`
   * `Total`

  Der Standardwert ist `Total`.

* **Kontextpfad**

  Auf diese Weise können Sie die Aktivität auf eine Teilmenge der Site einschränken, z. B. einen bestimmten Blog.
Der Standardwert ist die gesamte Community-Site.

* **Aggregation der Mitgliederzahl**

  Wenn diese Option deaktiviert (deaktiviert) ist, werden nur Beiträge der obersten Ebene gezählt. Wenn der Kontext beispielsweise die Stammseite ist (die Standardeinstellung), zeigt ein `Activity Type` von `Posts` nie eine Aktivität an, da keine Möglichkeit besteht, Inhalte auf der Stammseite zu posten. Wenn diese Option aktiviert ist, werden die Zählungen auf allen untergeordneten Seiten einbezogen.
Die Option Standard ist aktiviert.

### Beispielseite mit vier Komponenten {#example-page-with-components}

**Top Visitors** config: Typ = Member, Aktivitätstyp = Ansichten

**Top Contributors** config: Typ = Mitglieder, Aktivitätstyp = Beiträge

**Top Content** config: type = content, activity type = views,

**Trending Content** config: Typ = Inhalt, Aktivitätstyp = Beiträge

![Komponenten](assets/activity-list-components.png)
