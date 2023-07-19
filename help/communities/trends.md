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
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 7%

---

# Aktivitätstrends {#activity-trends}

## Einführung {#introduction}

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

und ziehen Sie sie an die gewünschte Stelle auf einer Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Komponente zum ersten Mal auf einer Seite einer Community-Site platziert wird, wird sie wie folgt angezeigt:

![community-activity](assets/community-activity.png)

### Konfigurieren der Community-Aktivitätenliste  {#configuring-community-activity-list}

Wählen Sie die platzierte `Community Activity List` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Unter dem **Kommentare** -Registerkarte angeben, ob und wie Kommentare für hochgeladene Dateien angezeigt werden:

![Eigenschaften](assets/activity-list-properties.png)

* **Typ**

  Geben Sie an, ob Daten zu Community-Mitgliedern oder benutzergenerierten Inhalten (UGC) angezeigt werden sollen.

  Die folgenden Optionen stehen zur Auswahl:

   * `Members`
   * `Content`

  Der Standardwert ist `Members`.

* **Anzeigetitel**

  Ein beschreibender Titel, der über den Daten angezeigt werden soll, z. B. `Trending Content`.
Standardmäßig ist kein Titel angegeben.

* **Anzeigezahl**

  Die Anzahl der aufzulistenden Elemente.
Der Standardwert ist 10.

* **Aktivitätstyp**

  Wählen Sie eine der folgenden Optionen aus:

   * `Views`(Seitenbesuche)
   * `Posts`(Erstellen von benutzergenerierten Inhalten)
   * `Follows`
   * `Likes`

  Der Standardwert ist &quot;Ansichten&quot;.

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
Der Standardwert ist die gesamte Community-Site.

* **Gesammelte Mitgliederzahl**

  Wenn diese Option deaktiviert (deaktiviert) ist, werden nur Beiträge der obersten Ebene gezählt. Wenn der Kontext beispielsweise die Stammseite ist (die Standardeinstellung), wird ein `Activity Type` von `Posts` werden nie Aktivitäten angezeigt, da keine Möglichkeit besteht, Inhalte auf der Stammseite zu posten. Wenn diese Option aktiviert ist, werden die Zählungen auf allen untergeordneten Seiten einbezogen.
Die Option Standard ist aktiviert.

### Beispielseite mit 4 Komponenten {#example-page-with-components}

**Top-Besucher** config: Typ = Mitglieder, Aktivitätstyp = Ansichten

**Wichtigste Mitwirkende** config: Typ = Mitglieder, Aktivitätstyp = Beiträge

**Top-Inhalt** config: Typ = Inhalt, Aktivitätstyp = Ansichten,

**Trendinhalt** config: Typ = Inhalt, Aktivitätstyp = Beiträge

![Komponenten](assets/activity-list-components.png)
