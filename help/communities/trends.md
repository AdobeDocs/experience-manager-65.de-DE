---
title: Aktivitätstrends
description: Hinzufügen einer Community-Aktivitätslisten-Komponente zu einer Seite
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2a4297e4-2d88-4fa6-8fea-3fea06753605
source-git-commit: 518207a0d8a95ef17b0972855a58f124fb215c85
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 4%

---

# Aktivitätstrends {#activity-trends}

## Einführung {#introduction}

Die `Community Activity List` -Komponente können Sie Trendinformationen über Beiträge und Ansichten von Mitgliedern sowie Beiträge und Ansichten von Inhalten hinzufügen.

Das Dokument beschreibt:

* Hinzufügen der `Community Activity List` -Komponente [Community-Site](/help/communities/overview.md#community-sites).

* Konfigurationseinstellungen für `Community Activity List` -Komponente.

### Anforderung {#requirement}

Daten für `Community Activity List` ist nur verfügbar, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

### Hinzufügen einer Community-Aktivitätenliste zu einer Seite {#adding-a-community-activity-list-to-a-page}

So fügen Sie eine `Community Activity List` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente `Communities / Community Activity List` und ziehen Sie sie an die gewünschte Stelle auf einer Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Komponente zum ersten Mal auf einer Seite einer Community-Site platziert wird, wird sie wie folgt angezeigt:

![community-activity](assets/community-activity.png)

### Konfigurieren der Community-Aktivitätenliste  {#configuring-community-activity-list}

Auswählen der platzierten `Community Activity List` -Komponente und wählen Sie dann die `Configure` -Symbol, damit Sie das Dialogfeld &quot;Bearbeiten&quot;öffnen können.

![konfigurieren](assets/configure-new.png)

Unter dem **Kommentare** -Registerkarte angeben, ob und wie Kommentare für hochgeladene Dateien angezeigt werden:

![Eigenschaften](assets/activity-list-properties.png)

* **Typ**

  Geben Sie an, ob Daten zu Community-Mitgliedern oder benutzergenerierten Inhalten angezeigt werden sollen.

  Die folgenden Optionen stehen zur Auswahl:

   * `Members`
   * `Content`

  Der Standardwert ist `Members`.

* **Titel anzeigen**

  einen beschreibenden Titel, der über den Daten angezeigt werden soll, z. B. `Trending Content`.
Standardmäßig ist kein Titel angegeben.

* **Anzahl der Anzeigen**

  Die Anzahl der aufzulistenden Elemente.
Der Standardwert lautet 10.

* **Aktivitätstyp**

  Wählen Sie eine der folgenden Optionen aus:

   * `Views`(Seitenbesuche)
   * `Posts`(Erstellen von benutzergenerierten Inhalten)
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

* **Zusammenrechnung der Mitgliederzahl**

  Wenn diese Option deaktiviert (deaktiviert) ist, werden nur Beiträge der obersten Ebene gezählt. Wenn der Kontext beispielsweise die Stammseite ist (die Standardeinstellung), wird ein `Activity Type` von `Posts` zeigt nie eine Aktivität an, da keine Möglichkeit besteht, Inhalte auf der Stammseite zu posten. Wenn diese Option aktiviert ist, werden die Zählungen auf allen untergeordneten Seiten einbezogen.
Die Option Standard ist aktiviert.

### Beispielseite mit vier Komponenten {#example-page-with-components}

**Top-Besucher** config: Typ = Mitglieder, Aktivitätstyp = Ansichten

**Wichtigste Mitarbeiter** config: Typ = Mitglieder, Aktivitätstyp = Beiträge

**Top-Inhalt** config: Typ = Inhalt, Aktivitätstyp = Ansichten,

**Trendinhalt** config: Typ = Inhalt, Aktivitätstyp = Beiträge

![Komponenten](assets/activity-list-components.png)
