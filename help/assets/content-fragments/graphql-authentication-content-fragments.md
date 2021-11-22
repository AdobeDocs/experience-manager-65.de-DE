---
title: Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten
description: Machen Sie sich mit der Authentifizierung vertraut, die für Remote-AEM-GraphQL-Abfragen erforderlich ist, um Ihre Headless-Content-Bereitstellung zu sichern.
feature: Content Fragments,GraphQL API
exl-id: 167f3318-7bc7-48fc-aaa9-73da43433f2f
source-git-commit: 9278ba4fe85edca4ab5741f89c0fc0ef2cf2764d
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 61%

---

# Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Ein primärer Anwendungsfall für die [Adobe Experience Manager (AEM) GraphQL-API für die Bereitstellung von Inhaltsfragmenten](/help/assets/content-fragments/graphql-api-content-fragments.md) bedeutet, Remote-Abfragen von Drittanbieteranwendungen oder -diensten zu akzeptieren. Diese Remote-Abfragen erfordern möglicherweise einen authentifizierten API-Zugriff, um die Bereitstellung von Headless-Content zu sichern.

>[!NOTE]
>
>Für Tests und Entwicklung können Sie auch direkt über die [GraphiQL-Schnittstelle](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) auf die AEM-GraphQL-API zugreifen.

Für die Authentifizierung muss sich der Drittanbieterdienst mit dem Benutzernamen und Kennwort des AEM Kontos authentifizieren.

<!-- 6.5.10.0 - does this content/page need to be migrated? -->

<!--
For authentication the third party service needs to [retrieve an Access Token](#retrieving-access-token), that can then be [used in the GraphQL Request](#use-access-token-in-graphql-request).

## Retrieving an Access Token {#retrieving-access-token}

See [Generating Access Tokens for Server Side APIs](/help/sites-developing/generating-access-tokens-for-server-side-apis.md) for full details.

## Using the Access Token in a GraphQL Request {#use-access-token-in-graphql-request}

For a third party service to connect with an AEM instance it needs to have an *Access Token*. The service must then add this token to the `Authorization` header on the POST request. 

For example, a GraphQL Authorization Header:

```xml
Authorization: Bearer <access_token>
```

## Permission Requirements {#permission-requirements}

All requests made using the access token will actually be made *by the user account that generated the token*. 

This means that you need to check that the account has the permissions required to run GraphQL queries. 

You can check this by using GraphiQL on the local instance.
-->
