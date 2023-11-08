---
title: Verwenden der GraphiQL-IDE in AEM
description: Erfahren Sie, wie Sie die GraphiQL IDE in Adobe Experience Manager verwenden.
exl-id: d4b01485-658b-4245-b2e6-04be8abc8ecf
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 92%

---

# Verwenden der GraphiQL-IDE {#graphiql-ide}

Eine Implementierung der standardmäßigen [GraphQL](https://graphql.org/learn/serving-over-http/#graphiql)-IDE zur Verwendung mit der GraphQL-API von Adobe Experience Manager (AEM) ist verfügbar.

>[!NOTE]
>
>GraphiQL ist in allen Umgebungen von AEM enthalten (kann jedoch nur bei der Konfiguration Ihrer Endpunkte aufgerufen/angezeigt werden).
>
>In früheren Versionen war ein Paket erforderlich, um die GraphiQL-IDE zu installieren. Sollten Sie ein solches Paket installiert haben, kann es jetzt entfernt werden.

>[!NOTE]
>Sie müssen [Ihre Endpunkte](/help/sites-developing/headless/graphql-api/graphql-endpoint.md) im [Konfigurationsbrowser konfiguriert](/help/assets/content-fragments/content-fragments-configuration-browser.md) haben, bevor Sie die GraphiQL-IDE verwenden.

Die **GraphiQL** Mit diesem Tool können Sie Ihre GraphQL-Abfragen testen und debuggen, indem Sie:

* Auswahl des **Endpunkts**, der der Sites-Konfiguration entspricht, die Sie für Ihre Abfragen verwenden möchten
* Direkte Eingabe neuer Abfragen
* Erstellen und Zugreifen auf **[Persistente Abfragen](/help/sites-developing/headless/graphql-api/persisted-queries.md)**
* Führen Sie Ihre Abfragen aus, um die Ergebnisse sofort anzuzeigen
* Verwalten von **Abfragevariablen**
* Speichern und Verwalten von **Persistenten Abfragen**
* Veröffentlichen oder Aufheben der Veröffentlichung von **Persistenten Abfragen** (z. B. nach/von `dev-publish`)
* Anzeige des **Verlaufs** der vorherigen Abfragen
* Verwenden des **Dokumentations-Explorers**, um auf die Dokumentation zuzugreifen; hilft Ihnen zu lernen und zu verstehen, welche Methoden verfügbar sind.

Sie können auf den Abfrage-Editor wie folgt zugreifen:

* **Instrumente** > **Allgemein** > **GraphQL Query Editor**
* Direkt, zum Beispiel: `http://localhost:4502/aem/graphiql.html`

![GraphiQL-Oberfläche](assets/cfm-graphiql-interface.png "GraphiQL-Oberfläche")

Sie können GraphiQL auf Ihrem System verwenden, damit Abfragen von Ihrer Client-Anwendung über GET-Anfragen durchgeführt werden können, und um Abfragen zu veröffentlichen. Zur Verwendung in der Produktion müssen Sie dann [Ihre Abfragen in Ihre Produktionsumgebung verschieben](/help/sites-developing/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production). Zunächst an den Produktionsautor, um die neu erstellten Inhalte mit den Abfragen zu validieren, und schließlich an die Produktionsveröffentlichung für die Live-Nutzung.

## Auswahl des Endpunkts {#selecting-endpoint}

In einem ersten Schritt müssen Sie den **[Endpunkt](/help/sites-developing/headless/graphql-api/graphql-endpoint.md)** auswählen, den Sie für die Abfragen verwenden möchten. Der Endpunkt ist für die Sites-Konfiguration geeignet, die Sie für Ihre Abfragen verwenden möchten.

Diese ist in der Dropdown-Liste oben rechts verfügbar.

## Erstellen und Beibehalten einer neuen Abfrage {#creating-new-query}

Sie können Ihre neue Abfrage im Editor eingeben, der sich im Bereich links in der Mitte, direkt unter dem GraphiQL-Logo befindet.

>[!NOTE]
>
>Wenn Sie bereits eine gespeicherte Abfrage ausgewählt haben, die im Editorbereich angezeigt wird, wählen Sie `+` (neben **Persistente Abfragen**), um den Editor für Ihre neue Abfrage zu leeren.

Fangen Sie einfach an zu tippen, im Editor ist auch folgendes möglich:

* verwenden von Mouse-over, um zusätzliche Informationen über Elemente anzuzeigen
* bietet Funktionen wie Syntax-Hervorhebung, Autovervollständigung, Auto-Vorschlag

>[!NOTE]
>
>GraphQL-Abfragen beginnen normalerweise mit dem Zeichen `{`.
>
>Zeilen, die mit einem `#` beginnen, werden ignoriert.

Verwenden Sie **Speichern unter**, um Ihre neue Abfrage beizubehalten.

## Aktualisieren einer persistenten Abfrage {#updating-persisted-query}

Wählen Sie die Abfrage, die Sie aktualisieren möchten, aus der Liste im Bereich **[Persistente Abfragen](/help/sites-developing/headless/graphql-api/persisted-queries.md)** (ganz links).

Die Abfrage wird im Editor-Panel angezeigt. Nehmen Sie die gewünschten Änderungen vor, und verwenden Sie dann **Speichern**, um die Aktualisierungen in der persistenten Abfrage zu speichern.

## Ausführen von Abfragen {#running-queries}

Sie können eine neue Abfrage sofort ausführen oder eine persistente Abfrage laden und ausführen. Um eine persistierte Abfrage zu laden, wählen Sie sie aus der Liste aus – die Abfrage wird im Editor-Panel angezeigt.

In beiden Fällen ist die Abfrage, die im Editor-Bereich angezeigt wird, die Abfrage, die ausgeführt wird, wenn Sie entweder:

* auf das Symbol **Abfrage ausführen** klicken/tippen oder
* die Tastaturkombination `Control-Enter` verwenden.

## Abfragevariablen {#query-variables}

<!-- more details needed here? -->

Mit der GraphiQL-IDE können Sie auch Ihre [Abfragevariablen](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphql-variables).

Beispiel:

![GraphQL-Variablen](assets/cfm-graphqlapi-03.png "GraphQL-Variablen")

<!--
## Managing cache for your persisted queries {#managing-cache}

[Persisted queries](/help/headless/graphql-api/persisted-queries.md) are recommended as they can be cached at the dispatcher and CDN layers, ultimately improving the performance of the requesting client application. By default AEM will invalidate the Content Delivery Network (CDN) cache based on a default Time To Live (TTL).

>[!NOTE]
>
>Custom rewrite rules on the Dispatcher might override defaults from AEM publish. 
>
>In the case that you are sending TTL-based cache-control headers from the dispatcher, based on a location match pattern then, if necessary, you might want to exclude `/graphql/execute.json/*` from the matches.

Using GraphQL you can configure the HTTP Cache Headers  to control these parameters for your individual persisted query.

1. The **Headers** option is accessible via the three vertical dots to the right of the persisted query name (far left panel):

   ![Persisted Query HTTP Cache Headers](assets/cfm-graphqlapi-headers-01.png "Persisted Query HTTP Cache Headers")

1. Selecting this opens the **Cache Configuration** dialog box:

   ![Persisted Query HTTP Cache Header Settings](assets/cfm-graphqlapi-headers-02.png "Persisted Query HTTP Cache Header Settings")

1. Select the appropriate parameter, then adjust the value as required:

   * **cache-control** - **max-age**
     Caches can store this content for specified number of seconds. Typically this is the browser TTL (Time To Live).
   * **surrogate-control** - **s-maxage**
     Same as max-age but applies specifically to proxy caches.
   * **surrogate-control** - **stale-while-revalidate**
     Caches may continue to serve a cached response after it becomes stale, for up to the specified number of seconds.
   * **surrogate-control** - **stale-if-error**
     Caches may continue to serve a cached response if there is an origin error, for up to the specified number of seconds.

1. Select **Save** to persist the changes.
-->

## Veröffentlichen persistenter Abfragen {#publishing-persisted-queries}

Wenn Sie Ihre [persistierte Abfrage](/help/sites-developing/headless/graphql-api/persisted-queries.md) aus der Liste (linker Bereich) ausgewählt haben, können Sie die Aktionen **Veröffentlichen** und **Veröffentlichung aufheben** verwenden. Dadurch werden die Abfragen in Ihrer Publishing-Umgebung (z. B. `dev-publish`) aktiviert, damit Ihre Anwendungen beim Testen leicht darauf zugreifen können.

>[!NOTE]
>
>Für den Cache `Time To Live` der persistenten Abfrage {&quot;cache-control&quot;:&quot;parameter&quot;:value} ist der Standardwert von 2 Stunden (7.200 Sekunden) definiert.

## Kopieren der URL, um direkt auf die Abfrage zuzugreifen {#copy-url}

Die **URL kopieren** -Option können Sie eine Abfrage simulieren, indem Sie die URL kopieren, die zum direkten Zugriff auf die beibehaltene Abfrage verwendet wird, und die Ergebnisse anzeigen. Diese kann dann zu Testzwecken verwendet werden, z. B. durch Zugriff in einem Browser:

<!--
  >[!NOTE]
  >
  >The URL will need [encoding before using programmatically](/help/headless/graphql-api/persisted-queries.md#encoding-query-url).
  >
  >The target environment might need adjusting, depending on your requirements.
-->

Beispiel:

`http://localhost:4502/graphql/execute.json/global/article-list-01`

Wenn Sie diese URL in einem Browser verwenden, können Sie die Ergebnisse bestätigen:

![GraphiQL – URL kopieren](assets/cfm-graphiql-copy-url.png "GraphiQL – URL kopieren")

Die Option **URL kopieren** ist über die drei vertikalen Punkte rechts neben dem Namen der persistenten Abfrage zugänglich (Bereich ganz links):

![GraphiQL – URL kopieren](assets/cfm-graphiql-persisted-query-options.png "GraphiQL – URL kopieren")

## Löschen persistenter Abfragen {#deleting-persisted-queries}

Die Option **Löschen** ist auch über die drei vertikalen Punkte rechts neben dem Namen der persistenten Abfrage (Bereich ganz links) zugänglich.

<!-- what happens if you try to delete something that is still published? -->


## Installieren der persistenten Abfrage in der Produktion {#installing-persisted-query-production}

Nachdem Sie Ihre persistente Abfrage mit GraphiQL entwickelt und getestet haben, ist das letzte Ziel, sie in [Ihre Produktionsumgebung zu übertragen](/help/sites-developing/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production), damit sie von Ihren Anwendungen verwendet werden kann.

## Tastaturbefehle {#keyboard-shortcuts}

Es gibt eine Auswahl von Tastaturbefehlen, die direkten Zugriff auf Aktionssymbole in der IDE bieten:

* Abfrage schön machen:  `Shift-Control-P`
* Abfrage fusionieren:  `Shift-Control-M`
* Abfrage ausführen:  `Control-Enter`
* Automatisch vervollständigen:  `Control-Space`

>[!NOTE]
>
>Auf manchen Tastaturen ist die Taste `Control` mit `Ctrl` beschriftet.
