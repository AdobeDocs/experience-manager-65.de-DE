---
title: Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten
description: Machen Sie sich mit der Authentifizierung vertraut, die für Remote-AEM-GraphQL-Abfragen erforderlich ist, um Ihre Headless-Content-Bereitstellung zu sichern.
feature: Content Fragments,GraphQL API
source-git-commit: 2f647fc640d3809dc684bce397831ab37fb94b07
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 87%

---

# Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Ein primäres Nutzungsszenario für die [Adobe Experience Manager (AEM) GraphQL-API für Inhaltsfragmentbereitstellung](/help/assets/content-fragments/graphql-api-content-fragments.md) besteht darin, Remote-Abfragen von Drittanbieteranwendungen oder -diensten zu akzeptieren. Diese Remote-Abfragen erfordern möglicherweise einen authentifizierten API-Zugriff, um die Bereitstellung von Headless-Content zu sichern.

>[!NOTE]
>
>Für Tests und Entwicklung können Sie auch direkt über die [GraphiQL-Schnittstelle](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) auf die AEM-GraphQL-API zugreifen.

Zur Authentifizierung muss der Drittanbieter-Service ein [Zugriffs-Token](#retrieving-access-token) abrufen, das dann [in der GraphQL-Anfrage](#use-access-token-in-graphql-request) verwendet werden kann.

## Abrufen eines Zugriffs-Tokens {#retrieving-access-token}

<!-- 6.5.10.0 - does this page need to be migrated? -->

<!--
See [Generating Access Tokens for Server Side APIs](/help/sites-developing/generating-access-tokens-for-server-side-apis.md) for full details.
-->

## Verwenden des Zugriffs-Tokens in einer GraphQL-Anfrage {#use-access-token-in-graphql-request}

Damit ein Drittanbieter-Service eine Verbindung mit einer AEM-Instanz herstellen kann, benötigt er ein *Zugriffs-Token*. Der Service muss dieses Token dann der `Authorization`-Kopfzeile in der POST-Anfrage hinzufügen.

Ein Beispiel für eine GraphQL-Autorisierungskopfzeile:

```xml
Authorization: Bearer <access_token>
```

## Berechtigungsanforderungen {#permission-requirements}

Alle Anfragen, die mit dem Zugriffs-Token durchgeführt werden, werden tatsächlich *von dem Benutzerkonto ausgeführt, das das Token generiert hat*

Dies bedeutet, dass Sie überprüfen müssen, ob das Konto über die erforderlichen Berechtigungen zum Ausführen von GraphQL-Abfragen verfügt.

Sie können dies überprüfen, indem Sie GraphiQL auf der lokalen Instanz verwenden.
