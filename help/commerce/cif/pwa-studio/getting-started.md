---
title: Erste Schritte mit der AEM-Erweiterung für PWA Studio
description: Erfahren Sie, wie Sie mit PWA Studio ein AEM Headless Content and Commerce-Projekt bereitstellen.
topics: Commerce
feature: Commerce Integration Framework
thumbnail: 37843.jpg
exl-id: de7b8f05-b6b7-4105-84a5-940c16ebf2b4
source-git-commit: e05f6cd7cf17f4420176cf76f28cb469bcee4a0a
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 68%

---

# Erste Schritte mit der AEM-Erweiterung für PWA Studio {#getting-started-pwa}

Standardmäßig lässt sich PWA Studio über GraphQL nahtlos mit Adobe Commerce integrieren und bietet unbegrenzte Möglichkeiten zur Erstellung innovativer und ansprechender Storefronts und anderer digitaler Erlebnisse.

Inhaltsfragmente sind Teile von Inhalten mit einer vordefinierten Struktur, die es ermöglicht, sie mit GraphQL als API in verschiedenen Formaten (z. B. JSON, Markdown) „headless“ zu nutzen und unabhängig zu rendern. Inhaltsfragmente enthalten alle für GraphQL erforderlichen Datentypen und -felder, um sicherzustellen, dass Ihre Anwendung nur das anfordert, was verfügbar ist, und das erhält, was erwartet wird. Die Flexibilität ihrer Struktur macht sie perfekt für die Verwendung an mehreren Stellen und über mehrere Kanäle.

Mit dem Inhaltsfragmentmodell-Editor in Adobe Experience Manager können Sie die benötigte Struktur einfach entwerfen. Die Hauptaufgabe bei der Integration von Adobe Experience Manager-Inhaltsfragmenten (oder anderen Daten) in Ihre PWA Studio-Anwendung besteht darin, Daten von mehreren GraphQL-Endpunkten abzurufen. Der Grund dafür ist, dass PWA Studio standardmäßig mit einem einzelnen Adobe Commerce GraphQL-Endpunkt arbeitet.

## Architektur {#architecture}

![PWA-Headless-Architektur](/help/commerce/cif/assets/pwa-studio/PWA-Studio_Architecture.png)

## Einrichten von PWA Studio {#setup-pwa}

Um Ihre PWA Studio App einzurichten, befolgen Sie die Adobe Commerce [Dokumentation zu PWA Studios](https://developer.adobe.com/commerce/pwa-studio/tutorials/).

Um PWA Studio mit dem GraphQL-Endpunkt von AEM zu verbinden, können Sie die [AEM-Erweiterung für PWA Studio](https://github.com/adobe/aem-pwa-studio-extensions) verwenden.

1. Überprüfen des Repositorys

1. Fügen Sie in Ihrer PWA Studio-Anwendung die Erweiterung als Entwicklungsabhängigkeit hinzu.

   ```javascript
   yarn add --dev file:{path-to-extension}/extension
   ```

1. Fügen Sie den Apollo Link-Wrapper zu Ihrer PWA Studio-Anwendung hinzu. Nehmen Sie in pwa-root/src/index.js die folgenden Änderungen vor:

   ```javascript
     import { linkWrapper } from '@adobe/pwa-studio-aem-cfm-blog-extension';
   
   // ...
   
   <Adapter apiBase={apiBase} apollo={{ link: linkWrapper(apolloLink) }} store={store}>
   ```

   Weitere Informationen zur Anpassung des Apollo-Clients finden Sie in [linkWrapper.js](https://github.com/adobe/aem-pwa-studio-extensions/blob/master/aem-cfm-blog-extension/extension/src/linkWrapper.js).

1. Um die Navigationskomponente mit einem Blog-Eintrag zu erweitern, fügen Sie die folgenden Anpassungen zu pwa-root/local-intercept.js hinzu:

   ```javascript
   const addBlogToNavigation = require('@adobe/pwa-studio-aem-cfm-blog-extension/src/addBlogToNavigation');
   
   function localIntercept(targets) {
       addBlogToNavigation(targets);
   }    
   ```

   Weitere Informationen zur Anpassung der Navigationskomponente finden Sie in [addBlogToNavigation.js](https://github.com/adobe/aem-pwa-studio-extensions/blob/master/aem-cfm-blog-extension/extension/src/addBlogToNavigation.js) und in der Dokumentation zum [Erweiterbarkeits-Framework](https://developer.adobe.com/commerce/pwa-studio/guides/general-concepts/extensibility/) von PWA Studio.

1. Der Apollo-Client erwartet den AEM GraphQL-Endpunkt unter `<https://pwa-studio/endpoint.js>`. Um den Endpunkt diesem Speicherort zuzuordnen, passen Sie die UPWARD-Konfiguration Ihrer PWA Studio-App an: a. nach `pwa-root/.env`Fügen Sie die Variable AEM_CFM_GRAPHQL hinzu und passen Sie sie an, um auf Ihren GraphQL-Endpunkt AEM Inhaltsfragmente zu verweisen.

   Beispiel: AEM_CFM_GRAPHQL=<http://localhost:4503/content/graphql/global>

   b. Fügen Sie Ihrer UPWARD-Konfiguration einen Proxy-Resolver hinzu. Eine Beispiel-UPWARD-Konfiguration könnte wie folgt aussehen:

```json
   response:
     resolver: conditional
     when:
       - matches: request.url.pathname
         pattern: ^/endpoint.json(/|$)
         use: aemProxy
     default: veniaResponse

   aemProxy:
     resolver: proxy
     target: env.AEM_CFM_GRAPHQL
     ignoreSSLErrors: true

   status: response.status
   headers: response.headers
   body: response.body
```

## Einrichten von AEM {#setup-aem}

In der AEM Dokumentation zu Inhaltsfragmenten finden Sie Informationen zum Einrichten eines GraphQL-Endpunkts für Ihr AEM Projekt. Fügen Sie außerdem in Ihrem AEM -Projekt die folgenden Konfigurationen hinzu, damit Ihre PWA Studio-Anwendung auf den GraphQL-Endpunkt zugreifen kann:

* Adobe Granite Cross-Origin Resource Sharing Policy (com.adobe.granite.cors.impl.CORSPolicyImpl)

   Legen Sie die `allowedorigin` -Eigenschaft auf den vollständigen Hostnamen Ihrer PWA-Anwendung.

   Beispiel: `<https://pwa-studio-test-vflyn.local.pwadev:9366>`

* Apache Sling Referrer Filter (org.apache.sling.security.impl.ReferrerFilter.cfg.json)

   Setzen Sie die Eigenschaft „allow.hosts“ auf den Hostnamen Ihrer PWA-Anwendung.

   Beispiel: pwa-studio-test-vflyn.local.pwadev

Die vollständigen Beispiele für beide Konfigurationen finden Sie hier: <https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cfm-blog-extension/aem/config/src/main/content/jcr_root/apps/blog-demo/config>.

Um den GraphQL-Endpunkt zu präsentieren, vorbereitete Adobe einige Beispiel-Inhaltsfragmentmodelle und -daten mithilfe eines Inhaltspakets. Diese Teile arbeiten mit den React-Komponenten zusammen, die mit der PWA Studio-Erweiterung bereitgestellt werden.

## Verwendung {#how-to-use}

Diese Erweiterung gilt als Beispielimplementierung der Verbindung einer PWA Studio-Anwendung mit AEM zum Abrufen und Rendern von Inhalten über GraphQL.

Je nach Anwendungsfall sollten Sie eigene benutzerdefinierte Inhaltsfragmentmodelle erstellen, die zu einem benutzerdefinierten GraphQL-Schema führen, das dann von Ihren eigenen React-Komponenten genutzt werden kann.

Produktions-Setups können verschiedene Aspekte aufweisen.

* Sie können über einen einzigen Federated GraphQL-Endpunkt verfügen, der AEM und Adobe Commerce GraphQL-Daten kombiniert, anstatt den Apollo-Client anzupassen.
* Ihre PWA Studio-Anwendung könnte die AEM GraphQL-Endpunkt-URL direkt verwenden, ohne dass ein Proxy mit UPWARD vorhanden ist. Der Proxy kann auch in eine andere Ebene verschoben werden (z. B. CDN).
* Der Ansatz eignet sich am besten für Sie und hängt auch stark davon ab, wie Sie die PWA Studio-Anwendung an den Endbenutzer bereitstellen.

Diese Erweiterung enthält zwei Beispiele.

### Blog {#blog}

Zeigt Blog-Beiträge basierend auf einigen Inhaltsfragmentmodellen an. Darüber hinaus enthält es Beispiele dafür, wie der Apollo-Client für die Verwendung mit dem AEM GraphQL-Endpunkt konfiguriert und wie die Navigationskomponente in PWA Studio erweitert wird. Weitere Informationen finden Sie unter [GitHub](https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cfm-blog-extension).

### PDP-Anreicherung {#pdp-enrichment}

Ermöglicht es Marketern, PDPs einfach mit zusätzlichen Inhalten anzureichern, die als Inhaltsfragmente verwaltet werden. Weitere Informationen finden Sie unter [GitHub](https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cif-product-page-extension).
