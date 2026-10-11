---
title: 'Schnellstartanleitung für Headless: Abrufen und Bereitstellen von Inhaltsfragmenten'
description: Erfahren Sie, wie Sie die AEM Assets-REST-API zum Verwalten von Inhaltsfragmenten und die GraphQL-API für die Headless-Bereitstellung von Inhalten der Inhaltsfragmente verwenden.
exl-id: 4664b3a4-4873-4f42-b59d-aadbfaa6072f
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: bfd4bc52-c397-5127-8f86-8953ba9fc0a3
    internal-label: Headless
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
  - id: d429a63e-ade4-4117-b04e-9b996d1c94ef
    internal-label: Integrations
  - id: c124fa01-25c5-42ec-adf6-21d1c114058b
    internal-label: Developer tools
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
  - id: a02b73a7-bdfc-4225-bdfd-69f7891ab55e
    internal-label: GraphQL
  - id: d781bc8f-52af-43f6-84d0-b73e59a130d5
    internal-label: Persisted queries
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 100%
---
# Schnellstartanleitung für Headless: Abrufen und Bereitstellen von Inhaltsfragmenten {#accessing-delivering-content-fragments}

Erfahren Sie, wie Sie die AEM Assets-REST-API zum Verwalten von Inhaltsfragmenten und die GraphQL-API für die Headless-Bereitstellung von Inhalten der Inhaltsfragmente verwenden.

## Was sind GraphQL- und Assets-REST-APIs? {#what-are-the-apis}

[Nachdem Sie einige Inhaltsfragmente erstellt haben,](create-content-fragment.md) können Sie die APIs von AEM verwenden, um sie headless bereitzustellen.

* Mit der [GraphQL-API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) können Sie Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen.
  * Um sie verwenden zu können, [müssen Endpunkte in AEM definiert und aktiviert werden](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#enabling-graphql-endpoint) und, falls erforderlich, muss die [GraphiQL-Oberfläche installiert werden](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#installing-graphiql-interface).
* Mit der [Assets-REST-API](/help/assets/assets-api-content-fragments.md) können Sie Inhaltsfragmente (und andere Assets) erstellen und ändern.

Der Rest dieses Handbuchs konzentriert sich auf den GraphQL-Zugriff und die Bereitstellung von Inhaltsfragmenten.

## Bereitstellen eines Inhaltsfragments mit GraphQL {#how-to-deliver-a-content-fragment}

Informationsarchitektinnen und -architekten müssen Abfragen für ihre Kanalendpunkte entwerfen, um Inhalte bereitzustellen. Berücksichtigen Sie diese Abfragen nur einmal pro Endpunkt und Modell. Erstellen Sie für dieses Erste-Schritte-Handbuch nur eine.

1. Melden Sie sich bei AEM an und rufen Sie die [GraphiQL-Oberfläche](/help/sites-developing/headless/graphql-api/graphiql-ide.md) auf:
   * Beispiel: `http://<host>:<port>/aem/graphiql.html`.

1. GraphiQL ist ein In-Browser-Abfrage-Editor für GraphQL. Sie können damit Abfragen zum Abrufen von Inhaltsfragmenten erstellen, um diese als JSON-Datei „headless“ bereitzustellen.
   * Im linken Bedienfeld können Sie Ihre Abfrage erstellen.
   * Im rechten Bedienfeld werden die Ergebnisse angezeigt.
   * Der Abfrage-Editor bietet Code-Vervollständigung und Hotkeys, um die Abfrage einfach auszuführen.
     ![GraphiQL-Editor](assets/graphiql.png)

1. Angenommen, das von uns erstellte Modell `person` wurde mit den Feldern `firstName`, `lastName` und `position` aufgerufen. Wir können dann eine einfache Abfrage erstellen, um den Inhalt unseres Inhaltsfragments abzurufen.

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
<!--
   ![GraphiQL query](assets/graphiql-query.png)
-->

1. Klicken Sie auf das Symbol **Abfrage ausführen** (Pfeil nach rechts) oder verwenden Sie das Tastaturkürzel `Ctrl-Enter`. Die Ergebnisse werden als JSON im rechten Bedienfeld angezeigt.
   ![GraphiQL-Ergebnisse](assets/graphiql-results.png)

1. Klicken Sie auf:
   * **Dokumente** oben rechts auf der Seite, um eine kontextbezogene Dokumentation anzuzeigen, die Sie bei der Erstellung Ihrer Abfragen unterstützt und sich an Ihre eigenen Modelle anpasst.
   * **Verlauf** in der oberen Symbolleiste, um frühere Abfragen anzuzeigen.
   * Wählen Sie **Speichern unter** und **Speichern**, um Ihre Abfragen zu speichern. Danach können Sie sie im Bedienfeld **Persistierte Abfragen** auflisten, abrufen und **veröffentlichen**.
     ![GraphiQL-Dokumentation](assets/graphiql-documentation.png)

GraphQL ermöglicht strukturierte Abfragen, die nicht nur auf bestimmte Datensätze oder einzelne Datenobjekte abzielen, sondern auch bestimmte Elemente der Objekte und verschachtelte Ergebnisse bereitstellen, Unterstützung für Abfragevariablen bieten und vieles mehr.

GraphQL kann iterative API-Anfragen und zu häufige Bereitstellungen vermeiden. Stattdessen ermöglicht es Massenbereitstellung von genau dem, was zum Rendern als Antwort auf eine einzelne API-Abfrage benötigt wird. Das resultierende JSON kann verwendet werden, um Daten in anderen Sites oder Mobile Apps bereitzustellen.

## Nächste Schritte {#next-steps}

Das war´s! Sie haben nun ein grundlegendes Verständnis für das Headless-Content-Management in AEM. Es gibt viele weitere Ressourcen, mit deren Hilfe Sie sich ein umfassendes Verständnis der verfügbaren Funktionen aneignen können.

* **[Konfigurations-Browser](create-configuration.md)** – Weitere Informationen zum AEM-Konfigurations-Browser
* **[Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)** – Weitere Informationen zum Erstellen und Verwalten von Inhaltsfragmenten
* Siehe **[GraphiQL-IDE](/help/sites-developing/headless/graphql-api/graphiql-ide.md)** für weitere Informationen zur Verwendung der GraphiQL-IDE
* Siehe **[Persistierte Abfragen](/help/sites-developing/headless/graphql-api/persisted-queries.md)** für weitere Informationen zu persistierten Abfragen
* **[Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/assets-api-content-fragments.md)** – Weitere Informationen zum direkten Zugriff auf AEM-Inhalte über die HTTP-API über CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen)
* **[GraphQL-API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)** – Weitere Informationen zum Headless-Bereitstellen von Inhaltsfragmenten
