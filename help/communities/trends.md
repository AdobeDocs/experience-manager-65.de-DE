---
title: Aktivitätstrends
seo-title: Activity Trends
description: Hinzufügen einer Community-Aktivitätslisten-Komponente zu einer Seite
seo-description: Adding a Community Activity List component to a page
uuid: 316aabf7-01a5-46da-be59-70c206eb6a3d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 4a0debdd-acb9-4646-80bb-fec66fae4088
docset: aem65
exl-id: 2a4297e4-2d88-4fa6-8fea-3fea06753605
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 30%

---

# Aktivitätstrends {#activity-trends}

## Einführung    {#introduction}

Die `Community Activity List` -Komponente bietet die Möglichkeit, Trendinformationen zu Beiträgen und Ansichten von Mitgliedern sowie Beiträgen und Ansichten von Inhalten hinzuzufügen.

Das Dokument beschreibt:

* Hinzufügen der `Community Activity List` -Komponente [Community-Site](/help/communities/overview.md#community-sites).

* Konfigurationseinstellungen für `Community Activity List` -Komponente.

### Anforderung {#requirement}

Daten für `Community Activity List` ist nur verfügbar, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

### Hinzufügen einer Community-Aktivitätenliste zu einer Seite {#adding-a-community-activity-list-to-a-page}

So fügen Sie eine `Community Activity List` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente

* `Communities / Community Activity List`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![community-activity](assets/community-activity.png)

### Konfigurieren der Community-Aktivitätenliste  {#configuring-community-activity-list}

Wählen Sie die platzierte `Community Activity List` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

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

   Die Anzahl der aufzulistenden Elemente.
Der Standardwert ist 10.

* **Aktivitätstyp**

   Wählen Sie eine der folgenden Optionen aus:

   * `Views`(Seitenbesuche)
   * `Posts`(Erstellen von benutzergenerierten Inhalten)
   * `Follows`
   * `Likes`

   Die Standardeinstellung lautet „Ansichten“.

* **Zeitraum**

   Wählen Sie eine der folgenden Optionen aus:

   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   Der Standardwert ist `Total`.

* **Kontextpfad**

   Bietet die Möglichkeit, die Aktivität auf eine Teilmenge der Site zu beschränken, z. B. einen bestimmten Blog.
Standardmäßig ist die Community-Site ausgewählt.

* **Gesammelte Mitgliederzahl**

   Wenn diese Option deaktiviert (deaktiviert) ist, werden nur Beiträge der obersten Ebene gezählt. Wenn der Kontext beispielsweise die Stammseite ist (die Standardeinstellung), wird ein `Activity Type` von `Posts` werden nie Aktivitäten angezeigt, da keine Möglichkeit besteht, Inhalte auf der Stammseite zu posten. Ist diese Option aktiviert, werden auch die Ergebnisse aller untergeordneten Seiten eingeschlossen.
Diese Option ist standardmäßig aktiviert.

### Beispielseite mit vier Komponenten {#example-page-with-components}

Konfiguration **Wichtigste Besucher** (Top Visitors): Typ = Mitglieder, Aktivitätstyp = Ansichten

**Wichtigste Mitwirkende** config: Typ = Mitglieder, Aktivitätstyp = Beiträge

**Top-Inhalt** config: Typ = Inhalt, Aktivitätstyp = Ansichten,

**Trendinhalt** config: Typ = Inhalt, Aktivitätstyp = Beiträge

![Komponenten](assets/activity-list-components.png)
