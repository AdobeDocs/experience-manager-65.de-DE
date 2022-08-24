---
title: Dashboards
seo-title: Dashboards
description: Erfahren Sie, wie Sie neue AEM-Dashboards erstellen, konfigurieren und entwickeln können.
seo-description: Learn how to create, configure and develop new AEM dashboards.
uuid: 3eadbba2-0ce1-41be-a9f8-e6cafa109893
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 40560e06-2508-45a4-a648-39629ed54f28
exl-id: 5b934e3a-f554-46ec-a913-8d570abb1503
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 71%

---

# Dashboards{#dashboards}

Bei der Verwendung von AEM können Sie viele Inhalte verschiedener Art (z. B. Seiten, Assets) verwalten. AEM-Dashboards stellen eine benutzerfreundliche, anpassbare Methode dar, Seiten zu definieren, in denen konsolidierte Daten angezeigt werden.

>[!NOTE]
>
>AEM-Dashboards werden benutzerabhängig erstellt. Das bedeutet, dass ein Benutzer nur auf seine eigenen Dashboards zugreifen kann.
>
>Allerdings können [Dashboard-Vorlagen](#creating-a-dashboard-template) für die Freigabe der gemeinsamen Konfiguration und des Dashboard-Layouts verwendet werden.

![chlimage_1-22](assets/chlimage_1-22.jpeg)

## Verwalten von Dashboards {#administering-dashboards}

### Erstellen eines Dashboards {#creating-a-dashboard}

Um ein neues Dashboard zu erstellen, gehen Sie wie folgt vor:

1. Klicken Sie im Bereich **Tools** auf **Konfigurationskonsole**.
1. Doppelklicken Sie in der Struktur auf **Dashboard**.
1. Klicken Sie auf **Dashboard**.
1. Geben Sie den **Titel** (z. B. „Mein Dashboard“) und den **Namen** ein.
1. Klicken Sie auf **Erstellen**.

### Klonen eines Dashboards {#cloning-a-dashboard}

Möglicherweise möchten Sie mehrere Dashboards, um die Informationen zu Ihrem Inhalt aus verschiedenen Perspektiven zu betrachten. Zur Unterstützung der Erstellung eines neuen Dashboards stellt AEM eine Klonfunktion bereit, die Sie zum Duplizieren eines vorhandenen Dashboards verwenden können. Um ein Dashboard zu klonen, gehen Sie wie folgt vor:

1. Klicken Sie im Bereich **Tools** auf **Konfigurationskonsole**.

1. Klicken Sie im Baum auf **Dashboard**.
1. Klicken Sie auf das Dashboard, das Sie klonen möchten.

1. Klicken Sie auf **Klonen**.

1. Geben Sie den **Namen** des neuen Dashboards ein.

### Entfernen von Dashboards {#removing-a-dashboard}

1. Klicken Sie im Bereich **Tools** auf **Konfigurationskonsole**.

1. Klicken Sie im Baum auf **Dashboard**.
1. Klicken Sie auf das Dashboard, das Sie löschen möchten.

1. Klicken Sie auf **Entfernen**.

1. Klicken Sie zur Bestätigung auf **Ja**.

## Dashboard-Komponenten {#dashboard-components}

### Übersicht {#overview}

Dashboard-Komponenten sind nichts anderes als reguläre [AEM-Komponenten](/help/sites-developing/developing-components-samples.md). Dieser Abschnitt beschreibt die Berichtskomponenten, die im Lieferumfang von AEM enthalten sind.

### Berichterstellungskomponenten zur Webanalyse {#web-analytics-reporting-components}

AEM enthält eine Reihe von Komponenten, die mehrere Metriken Ihrer [SiteCatalyst](/help/sites-administering/adobeanalytics.md)-Daten rendern. Diese Komponenten sind im Sidekick im Bereich **Dashboard** aufgeführt.

Jede Berichtskomponente enthält mindestens drei Registerkarten:

* **Allgemein**: Enthält die Hauptkonfiguration.

* **Bericht:** Enthält die spezifische Konfiguration des jeweiligen Berichts.
* **Stil**: enthält Stilkonfigurationen wie Diagrammgröße und Rand.

Die Berichtskomponenten werden mit einer Standardkonfiguration initialisiert, mit der Sie Ihr Dashboard schnell einrichten können.

#### Konfiguration „Allgemein“ {#basic-configuration}

Auf der Registerkarte **Allgemein** wird der Zugriff auf die folgenden Konfigurationseinträge bereitgestellt:

**Titel** Der im Dashboard angezeigte Titel.

**Anfragetyp** Die Art und Weise, wie Daten angefordert werden.

**SiteCatalyst-Konfiguration (optional)** Die Konfiguration, mit der Sie eine Verbindung zu SiteCatalyst herstellen möchten. falls nicht näher erläutert, wird von einer Konfiguration auf der Dashboardseite (über die Seiteneigenschaften) ausgegangen

**Report Suite-ID (optional)** Die SiteCatalyst-Report Suite, die Sie zum Generieren des Diagramms verwenden möchten.

#### Berichtskonfiguration {#report-configuration}

Zur Anzeige der Web-Statistiken müssen Sie den Datenbereich der Daten definieren, die Sie abrufen möchten. Auf der Registerkarte **Bericht** finden Sie zwei Felder, in denen Sie diesen Bereich festlegen können.

>[!NOTE]
>
>Wenn Sie einen großen Datumsbereich festlegen, reagiert das Dashboard unter Umständen nicht mehr so schnell.

**Datum ab** Das absolute oder relative Datum, ab dem die Daten abgerufen werden.

**Datum bis** Absolutes oder relatives Datum, bis zu dem die Daten abgerufen werden.

Jede Komponente definiert außerdem bestimmte Einstellungen.

#### Überstunden-Bericht {#overtime-report}

![chlimage_1-26](assets/chlimage_1-26a.png)

**Datumsgranularität** Zeiteinheit der X-Achse (z. B. Tag, Stunde).

**Metriken** Die Liste der Ereignisse, die angezeigt werden sollen.

**Elemente** Die Liste der Elemente, die die Metrikdaten im Diagramm aufschlüsseln.

#### Bewerteter Listenbericht {#ranked-list-report}

![chlimage_1-27](assets/chlimage_1-27a.png)

**Elemente** Das Element, das die Metrikdaten im Diagramm aufschlüsselt.

**Metriken** Das Ereignis, das angezeigt werden soll.

**Nein. der obersten Elemente** Anzahl der im Bericht angezeigten Elemente.

#### Rangbericht {#ranked-report}

![chlimage_1-28](assets/chlimage_1-28a.png)

**Metriken** Das Ereignis, das angezeigt werden soll.

**Elemente** Das Element, das die Metrikdaten im Diagramm aufschlüsselt.

#### Bericht zu oberem Site-Bereich {#top-site-section-report}

Diese Komponente zeigt ein Diagramm an, das den laut folgender Konfiguration häufiger besuchten Bereich einer Website aufzeigt.

![chlimage_1-29](assets/chlimage_1-29a.png)

**Nein. der obersten Elemente** Anzahl der im Bericht angezeigten Abschnitte.

#### Trendbericht {#trended-report}

![chlimage_1-30](assets/chlimage_1-30a.png)

**Datumsgranularität** Zeiteinheit der X-Achse (z. B. Tag, Stunde).

**Metriken** Das Ereignis, das angezeigt werden soll.

**Elemente** Das Element, das die Metrikdaten im Diagramm aufschlüsselt.

## Erweitern des Dashboards {#extending-dashboard}

### Übersicht {#overview-1}

Dashboards sind normale Seiten (`cq:Page`), deshalb können zum Zusammenstellen von Dashboards beliebige Komponenten verwendet werden.

Es gibt eine standardmäßige Komponentengruppe `Dashboard` enthalten Analytics-Reporting-Komponenten, die standardmäßig in der Vorlage aktiviert sind.

### Erstellen einer Dashboard-Vorlage {#creating-a-dashboard-template}

Eine Vorlage definiert den Standardinhalt eines neuen Dashboards. Sie können mehrere Vorlagen für die Erstellung verschiedener Arten von Dashboards verwenden.

Dashboard-Vorlagen werden wie andere Seitenvorlagen erstellt, allerdings unter `/libs/cq/dashboards/templates/`. Weitere Informationen finden Sie im Abschnitt [Erstellen einer contentpage-Vorlage](/help/sites-developing/website.md#creating-the-contentpage-template).

>[!NOTE]
>
>Dashboard-Vorlagen werden von mehreren Benutzern verwendet.

### Entwickeln einer Dashboard-Komponente {#developing-a-dashboard-component}

Die Entwicklung einer Dashboard-Komponente besteht aus der Erstellung einer regulären AEM-Komponente. In diesem Abschnitt ist ein Beispiel für eine Komponente beschrieben, die die Top 10 der Mitwirkenden anzeigt.

![chlimage_1-31](assets/chlimage_1-31a.png)

Die wichtigsten Autorenkomponenten werden im Repository unter `/apps/geometrixx-outdoors/components/reporting` und setzt sich aus Folgendem zusammen:

1. einer `jsp`-Datei, die jcr-Daten liest und den `html`-Platzhalter definiert

1. einer clientseitigen Bibliothek, die eine `js`-Datei enthält. Diese ruft die Daten ab und gliedert sie und trägt dann den `html`-Platzhalter ein.

![chlimage_1-32](assets/chlimage_1-32a.png)

Die folgende Javascript-Datei wird in der `geout.reporting.topauthors`[-Client-Bibliothek](/help/sites-developing/clientlibs.md) als untergeordnetes Element der Komponente selbst definiert.

Der [QueryBuilder](/help/sites-developing/querybuilder-api.md) wird verwendet, um beim Repository das Lesen der `cq:AuditEvent`-Knoten anzufragen. Das Ergebnis der Abfrage ist ein JSON-Objekt, aus dem Autorenbeiträge extrahiert werden.

#### top_authors.js {#top-authors-js}

```
$.ajax({
  url: "/bin/querybuilder.json",
  cache: false,
  data: {
       "orderby": "cq:time",
       "orderby.sort": "desc",
       "p.hits": "full",
       "p.limit": 100,
       "path": "/var/audit/com.day.cq.wcm.core.page/",
       "type": "cq:AuditEvent"
   },
  dataType: "json"
}).done(function( res ) {
    var authors = {};
    // from JSON to Object
    for(var r in res.hits) {
        var userId = res.hits[r].userId;
        if(userId == undefined) {
            continue;
        }
        var auth = authors[userId] || {userId : userId};
        auth.contrib = (auth.contrib || 0) +1;

        authors[userId] = auth;
    }

    // order by contribution
    var orderedByContrib = [];
    for(var a in authors) {
        orderedByContrib.push(authors[a]);
    }
    orderedByContrib.sort(function(a,b){return b.contrib - a.contrib});

    // produce the list
    for (var i=0, tot=orderedByContrib.length; i < tot; i++) {
        var current = orderedByContrib[i];
        $("<div> #" + (i + 1) +" "+ current.userId + " (" + current.contrib +" contrib.)</div>").appendTo("#authors-list");

    }
});
```

Die `JSP` enthält beide `global.jsp` und `clientlib`.

#### top_authors.jsp {#top-authors-jsp}

```java
<%@page session="false" contentType="text/html; charset=utf-8" %><%
%><%
%><%@include file="/libs/foundation/global.jsp" %><%
%>
<ui:includeClientLib categories="geout.reporting.topauthors" />
<%
String reportletTitle = properties.get("title", "Top Authors");
%>
<html>
     <h3><%=xssAPI.encodeForHTML(reportletTitle) %></h3>
     <div id="authors-list"></div>
</html>
```
