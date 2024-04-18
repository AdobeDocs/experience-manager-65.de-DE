---
title: Dashboards
description: Erfahren Sie, wie Sie neue AEM-Dashboards erstellen, konfigurieren und entwickeln können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 5b934e3a-f554-46ec-a913-8d570abb1503
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 100%

---

# Dashboards{#dashboards}

Wenn Sie AEM verwenden, können Sie eine Vielzahl verschiedener Inhaltstypen verwalten (z. B. Seiten oder Assets). AEM-Dashboards stellen eine benutzerfreundliche und anpassbare Möglichkeit zur Definition von Seiten dar, auf denen zusammengeführte Daten angezeigt werden.

>[!NOTE]
>
>AEM-Dashboards werden benutzerabhängig erstellt. Das bedeutet, dass Benutzende nur auf ihre jeweils eigenen Dashboards zugreifen können.
>
>Allerdings können [Dashboard-Vorlagen](#creating-a-dashboard-template) für die Freigabe der gemeinsamen Konfiguration und des Dashboard-Layouts verwendet werden.

![chlimage_1-22](assets/chlimage_1-22.jpeg)

## Verwalten von Dashboards {#administering-dashboards}

### Erstellen eines Dashboards {#creating-a-dashboard}

1. Klicken Sie im Abschnitt **Tools** auf **Konfigurationskonsole**.
1. Doppelklicken Sie in der Struktur auf **Dashboard**.
1. Klicken Sie auf **Neues Dashboard**.
1. Geben Sie den **Titel** (z. B. „Mein Dashboard“) und den **Namen** ein.
1. Klicken Sie auf **Erstellen**.

### Klonen eines Dashboards {#cloning-a-dashboard}

Unter Umständen möchten Sie mehrere Dashboards nutzen, um schnell Informationen zu Ihren Inhalten in verschiedenen Ansichten anzuzeigen. Um Sie beim Erstellen neuer Dashboards zu unterstützen, bietet AEM eine Klonfunktion, mit der Sie ein bereits vorhandenes Dashboard duplizieren können. Gehen Sie wie folgt vor, um ein Dashboard zu klonen:

1. Klicken Sie im Abschnitt **Tools** auf **Konfigurationskonsole**.

1. Klicken Sie in der Struktur auf **Dashboard**.
1. Klicken Sie auf das Dashboard, das Sie klonen möchten.

1. Klicken Sie auf **Klonen**.

1. Geben Sie den **Namen** des neuen Dashboards ein.

### Entfernen eines Dashboards {#removing-a-dashboard}

1. Klicken Sie im Abschnitt **Tools** auf **Konfigurationskonsole**.

1. Klicken Sie in der Struktur auf **Dashboard**.
1. Klicken Sie auf das Dashboard, das Sie löschen möchten.

1. Klicken Sie auf **Entfernen**.

1. Klicken Sie zur Bestätigung auf **Ja**.

## Dashboard-Komponenten {#dashboard-components}

### Übersicht {#overview}

Dashboard-Komponenten sind nichts anderes als reguläre [AEM-Komponenten](/help/sites-developing/developing-components-samples.md). Dieser Abschnitt beschreibt die Berichtskomponenten, die im Lieferumfang von AEM enthalten sind.

### Reporting-Komponenten zur Web-Analyse {#web-analytics-reporting-components}

AEM enthält eine Reihe von Komponenten, die mehrere Metriken Ihrer [SiteCatalyst](/help/sites-administering/adobeanalytics.md)-Daten rendern. Diese Komponenten sind im Sidekick im Bereich **Dashboard** aufgeführt.

Jede Berichtskomponente enthält mindestens drei Registerkarten:

* **Standard**: enthält die Hauptkonfiguration.

* **Bericht:** Enthält die spezifische Konfiguration des jeweiligen Berichts.
* **Stil**: Enthält Stilkonfigurationen wie die Diagrammgröße und den Rand.

Die Berichtskomponenten werden mit einer Standardkonfiguration initialisiert, mit der Sie Ihr Dashboard schnell einrichten können.

#### Standardkonfiguration {#basic-configuration}

Auf der Registerkarte **Standard** wird der Zugriff auf die folgenden Konfigurationseinträge bereitgestellt:

**Titel**: Der im Dashboard angezeigte Titel.

**Anfrage-Typ**: Die Art und Weise, wie Daten angefragt werden.

**SiteCatalyst-Konfiguration (optional)**: Die Konfiguration, die Sie für die Verbindung mit SiteCatalyst verwenden möchten. Falls nicht näher erläutert, wird von einer Konfiguration auf der Dashboardseite (über die Seiteneigenschaften) ausgegangen.

**Report Suite-ID (optional)**: Die SiteCatalyst-Report Suite, die Sie für die Erstellung des Diagramms verwenden möchten.

#### Konfiguration von Berichten {#report-configuration}

Um Web-Statistiken anzeigen zu können, müssen Sie den Datumsbereich für die Daten festlegen, die erfasst werden sollen. Auf der Registerkarte **Bericht** finden Sie zwei Felder, in denen Sie diesen Bereich festlegen können.

>[!NOTE]
>
>Wenn Sie einen großen Datumsbereich festlegen, reagiert das Dashboard unter Umständen langsamer.

**Ab-Datum** Absolutes oder relatives Datum, ab dem die Daten abgerufen werden.

**Bis-Datum**: Absolutes oder relatives Datum, bis zu dem die Daten abgerufen werden.

Jede Komponente definiert außerdem bestimmte Einstellungen.

#### Zeitverlaufbericht {#overtime-report}

![chlimage_1-26](assets/chlimage_1-26a.png)

**Datumsgranularität**: Zeiteinheit der X-Achse (z. B. Tag, Stunde).

**Metriken**: Die Liste der Ereignisse, die angezeigt werden sollen.

**Elemente**: Die Liste der Elemente, in der die Daten zu den Metriken im Diagramm aufgeschlüsselt sind.

#### Bewerteter Listenbericht {#ranked-list-report}

![chlimage_1-27](assets/chlimage_1-27a.png)

**Elemente**: Das Element, in dem die Daten zu den Metriken im Diagramm aufgeschlüsselt sind.

**Metriken** Das Ereignis, das Sie anzeigen möchten.

**Anzahl von Top-Elementen**: Anzahl der vom Bericht angezeigten Elemente.

#### Rangbericht {#ranked-report}

![chlimage_1-28](assets/chlimage_1-28a.png)

**Metriken** Das Ereignis, das Sie anzeigen möchten.

**Elemente**: Das Element, in dem die Daten zu den Metriken im Diagramm aufgeschlüsselt sind.

#### Bericht zu oberem Site-Bereich {#top-site-section-report}

Diese Komponente zeigt ein Diagramm an, das den laut folgender Konfiguration häufiger besuchten Bereich einer Website aufzeigt.

![chlimage_1-29](assets/chlimage_1-29a.png)

**Anzahl von Top-Elementen**: Anzahl der vom Bericht angezeigten Abschnitte.

#### Trendbericht {#trended-report}

![chlimage_1-30](assets/chlimage_1-30a.png)

**Datumsgranularität**: Zeiteinheit der X-Achse (z. B. Tag, Stunde).

**Metriken** Das Ereignis, das Sie anzeigen möchten.

**Elemente**: Das Element, in dem die Daten zu den Metriken im Diagramm aufgeschlüsselt sind.

## Erweitern des Dashboards {#extending-dashboard}

### Übersicht {#overview-1}

Dashboards sind normale Seiten (`cq:Page`), deshalb können zum Zusammenstellen von Dashboards beliebige Komponenten verwendet werden.

Es gibt die Standardkomponentengruppe `Dashboard`, die Reporting-Komponenten zur Analyse enthält, die standardmäßig in der Vorlage aktiviert sind.

### Erstellen einer Dashboard-Vorlage {#creating-a-dashboard-template}

Eine Vorlage definiert den Standardinhalt eines neuen Dashboards. Sie können mehrere Vorlagen für die Erstellung verschiedener Arten von Dashboards verwenden.

Dashboard-Vorlagen werden auf die gleiche Weise wie andere Seitenvorlagen erstellt, mit dem Unterschied, dass sie unter `/libs/cq/dashboards/templates/` gespeichert werden. Weitere Informationen finden Sie im Abschnitt [Erstellen einer contentpage-Vorlage](/help/sites-developing/website.md#creating-the-contentpage-template).

>[!NOTE]
>
>Dashboard-Vorlagen werden von mehreren Benutzenden verwendet.

### Entwickeln einer Dashboard-Komponente {#developing-a-dashboard-component}

Beim Entwickeln einer Dashboard-Komponente werden herkömmliche AEM-Komponenten erstellt. Dieser Abschnitt beschreibt eine Beispielkomponente, die die 10 Personen mit den meisten Beiträgen anzeigt.

![chlimage_1-31](assets/chlimage_1-31a.png)

Die wichtigsten Autorkomponenten sind im Repository unter `/apps/geometrixx-outdoors/components/reporting` gespeichert und bestehen aus:

1. einer `jsp`-Datei, die jcr-Daten liest und den `html`-Platzhalter definiert

1. einer Client-seitigen Bibliothek, die eine `js`-Datei enthält. Diese ruft die Daten ab und gliedert sie und trägt dann den `html`-Platzhalter ein.

![chlimage_1-32](assets/chlimage_1-32a.png)

Die folgende JavaScript-Datei wird in der `geout.reporting.topauthors`-[Client-Bibliothek](/help/sites-developing/clientlibs.md) als untergeordnetes Element der Komponente selbst definiert.

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

Die `JSP`-Datei enthält sowohl `global.jsp` als auch `clientlib`.

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
