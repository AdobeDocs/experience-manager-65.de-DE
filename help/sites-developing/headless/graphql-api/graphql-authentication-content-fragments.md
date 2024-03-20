---
title: Authentifizierung für Remote Adobe Experience Manager GraphQL-Abfragen zu Inhaltsfragmenten
description: Machen Sie sich mit der Authentifizierung vertraut, die für Adobe Experience Manager-GraphQL-Remote-Abfragen erforderlich ist, um die Bereitstellung von Headless-Inhalten zu sichern.
feature: Content Fragments,GraphQL API
exl-id: 167f3318-7bc7-48fc-aaa9-73da43433f2f
solution: Experience Manager, Experience Manager Sites
role: Developer
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 42%

---

# Authentifizierung für Remote Adobe Experience Manager GraphQL-Abfragen zu Inhaltsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Ein primärer Anwendungsfall für die [Adobe Experience Manager (AEM) GraphQL-API für die Bereitstellung von Inhaltsfragmenten](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) bedeutet, Remote-Abfragen von Drittanbieteranwendungen oder -diensten zu akzeptieren. Diese Remote-Abfragen erfordern möglicherweise einen authentifizierten API-Zugriff, um die Bereitstellung von Headless-Inhalten zu sichern.

>[!NOTE]
>
>Für Tests und Entwicklung können Sie auch direkt über die [GraphiQL-Schnittstelle](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphiql-interface) auf die AEM GraphQL-API zugreifen.

Zur Authentifizierung muss sich der Drittanbieterdienst mit dem Benutzernamen und Kennwort des AEM Kontos authentifizieren.

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
