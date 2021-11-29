---
title: 'Schnellstartanleitung für Headless: Abrufen und Bereitstellen von Inhaltsfragmenten'
description: Erfahren Sie, wie Sie die AEM Assets-REST-API zum Verwalten von Inhaltsfragmenten und die GraphQL-API für die Headless-Bereitstellung von Inhalten der Inhaltsfragmente verwenden.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
source-git-commit: 6c75af3957c319c38177cd62c90e781a982ba91b
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 88%

---

# Schnellstartanleitung für Headless: Abrufen und Bereitstellen von Inhaltsfragmenten {#accessing-delivering-content-fragments}

Erfahren Sie, wie Sie die AEM Assets-REST-API zum Verwalten von Inhaltsfragmenten und die GraphQL-API für die Headless-Bereitstellung von Inhalten der Inhaltsfragmente verwenden.

## Was sind GraphQL- und Assets-REST-APIs? {#what-are-the-apis}

[Nachdem Sie einige Inhaltsfragmente erstellt haben,](create-content-fragment.md) können Sie die APIs von AEM verwenden, um sie headless bereitzustellen.

* Mit der [GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md) können Sie Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen.
   * Um dies zu verwenden, [Endpunkte müssen in AEM definiert und aktiviert werden](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)und, falls erforderlich, die [Installierte GraphiQL-Oberfläche](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface).
* Mit der [Assets-REST-API](/help/assets/assets-api-content-fragments.md) können Sie Inhaltsfragmente (und andere Assets) erstellen und ändern.

Der Rest dieses Handbuchs konzentriert sich auf den GraphQL-Zugriff und die Bereitstellung von Inhaltsfragmenten.

## Bereitstellen eines Inhaltsfragments mit GraphQL {#how-to-deliver-a-content-fragment}

Informationsarchitekten müssen Abfragen für ihre Kanalendpunkte entwerfen, um Inhalte bereitzustellen. Diese Abfragen müssen in der Regel nur einmal pro Endpunkt und Modell berücksichtigt werden. Für die Zwecke dieser ersten Schritte müssen wir nur eine erstellen.

1. Melden Sie sich bei AEM an und greifen Sie auf die Benutzeroberfläche GraphiQL zu:
   * Beispiel: `https://<host>:<port>/content/graphiql.html`.

1. GraphiQL ist ein In-Browser-Abfrage-Editor für GraphQL. Sie können damit Abfragen zum Abrufen von Inhaltsfragmenten erstellen, um diese als JSON-Datei direkt bereitzustellen.
   * Im linken Bedienfeld können Sie Ihre Abfrage erstellen.
   * Im rechten Bedienfeld werden die Ergebnisse angezeigt.
   * Der Abfrage-Editor bietet Code-Vervollständigung und Hotkeys, um die Abfrage einfach auszuführen.
      ![GraphiQL-Editor](../assets/graphiql.png)

1. Angenommen, das von uns erstellte Modell `person` wurde mit Feldern `firstName`, `lastName` und `position` aufgerufen. Wir können dann eine einfache Abfrage erstellen, um den Inhalt unseres Inhaltsfragments abzurufen.

   ```text
   query 
   {
     personList {
       items {
         _path
         firstName
         lastName
         position
       }
     }
   }
   ```

1. Geben Sie die Abfrage in das linke Bedienfeld ein.
   ![GraphiQL-Abfrage](../assets/graphiql-query.png)

1. Klicken Sie auf die Schaltfläche **Abfrage ausführen** oder verwenden Sie den `Ctrl-Enter`-Hotkey. Die Ergebnisse werden als JSON im rechten Bedienfeld angezeigt.
   ![GraphiQL-Ergebnisse](../assets/graphiql-results.png)

1. Klicken Sie auf:
   * **Dokumente** oben rechts auf der Seite, um kontextbezogene Dokumentation anzuzeigen, mit deren Hilfe Sie Abfragen erstellen können, die sich an Ihre eigenen Modelle anpassen.
   * **Geschichte** in der oberen Symbolleiste, um frühere Abfragen anzuzeigen.
      ![GraphiQL-Dokumentation](../assets/graphiql-documentation.png)

GraphQL ermöglicht strukturierte Abfragen, die nicht nur auf bestimmte Datensätze oder einzelne Datenobjekte abzielen, sondern auch bestimmte Elemente der Objekte und verschachtelte Ergebnisse bereitstellen, Unterstützung für Abfragevariablen bieten und vieles mehr.

GraphQL kann sowohl iterative API-Anfragen als auch Überbereitstellungen vermeiden und ermöglicht stattdessen eine Massenbereitstellung von genau dem, was zum Rendern als Antwort auf eine einzelne API-Abfrage benötigt wird. Das resultierende JSON kann verwendet werden, um Daten in anderen Sites oder Mobile Apps bereitzustellen.

## Nächste Schritte {#next-steps}

Das war´s! Sie haben nun ein grundlegendes Verständnis für das Headless-Content-Management in AEM. Natürlich gibt es viele weitere Ressourcen, mit deren Hilfe Sie sich ein umfassendes Verständnis der verfügbaren Funktionen aneignen können.

* **[Konfigurations-Browser](create-configuration.md)** – Weitere Informationen zum AEM-Konfigurations-Browser
* **[Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)** – Weitere Informationen zum Erstellen und Verwalten von Inhaltsfragmenten
* **[Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/assets-api-content-fragments.md)** – Weitere Informationen zum direkten Zugriff auf AEM-Inhalte über die HTTP-API über CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen)
* **[GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md)** – Weitere Informationen zum Headless-Bereitstellen von Inhaltsfragmenten
