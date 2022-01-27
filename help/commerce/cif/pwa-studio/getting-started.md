---
title: Erste Schritte mit der AEM-Erweiterung für PWA Studio
description: Erfahren Sie, wie Sie mit PWA Studio ein AEM Headless Content and Commerce-Projekt bereitstellen.
topics: Commerce
feature: Commerce Integration Framework
thumbnail: 37843.jpg
exl-id: de7b8f05-b6b7-4105-84a5-940c16ebf2b4
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 95%

---

# Erste Schritte mit der AEM-Erweiterung für PWA Studio {#getting-started-pwa}

Standardmäßig lässt sich PWA Studio über GraphQL nahtlos mit Adobe Commerce integrieren und bietet unbegrenzte Möglichkeiten zur Erstellung innovativer und ansprechender Storefronts und anderer digitaler Erlebnisse.

Inhaltsfragmente sind Teile von Inhalten mit einer vordefinierten Struktur, die es ermöglicht, sie mit GraphQL als API in verschiedenen Formaten (z. B. JSON, Markdown) headless zu nutzen und unabhängig zu rendern. Inhaltsfragmente enthalten alle für GraphQL erforderlichen Datentypen und -felder, um sicherzustellen, dass Ihre Anwendung nur das anfordert, was verfügbar ist, und das erhält, was erwartet wird. Die Flexibilität ihrer Struktur macht sie perfekt für die Verwendung an mehreren Stellen und über mehrere Kanäle.

Mit dem Inhaltsfragmentmodell-Editor in Adobe Experience Manager können Sie die benötigte Struktur einfach entwerfen. Die Hauptaufgabe bei der Integration von Adobe Experience Manager-Inhaltsfragmenten (oder anderen Daten) in Ihre PWA Studio-Anwendung besteht darin, Daten von mehreren GraphQL-Endpunkten abzurufen. Dies liegt daran, dass PWA Studio standardmäßig mit einem einzigen Adobe Commerce-GraphQL-Endpunkt arbeitet.

## Architektur {#architecture}

![PWA-Headless-Architektur](/help/commerce/cif/assets/pwa-studio/PWA-Studio_Architecture.png)

## Einrichten von PWA Studio {#setup-pwa}

Folgen Sie der [PWA Studio-Dokumentation](https://developer.adobe.com/commerce/pwa-studio/tutorials/) von Adobe Commerce, um Ihre PWA Studio-Anwendung einzurichten.

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

   Weitere Informationen zur Anpassung des Apollo-Clients finden Sie unter [linkWrapper.js](https://github.com/adobe/aem-pwa-studio-extensions/blob/master/aem-cfm-blog-extension/extension/src/linkWrapper.js).

1. Um die Navigationskomponente mit einem Blog-Eintrag zu erweitern, fügen Sie die folgenden Anpassungen zu pwa-root/local-intercept.js hinzu:

   ```javascript
   const addBlogToNavigation = require('@adobe/pwa-studio-aem-cfm-blog-extension/src/addBlogToNavigation');
   
   function localIntercept(targets) {
       addBlogToNavigation(targets);
   }    
   ```

   Weitere Informationen zur Anpassung der Navigationskomponente finden Sie in [addBlogToNavigation.js](https://github.com/adobe/aem-pwa-studio-extensions/blob/master/aem-cfm-blog-extension/extension/src/addBlogToNavigation.js) und in der Dokumentation zum [Erweiterbarkeits-Framework](https://developer.adobe.com/commerce/pwa-studio/guides/general-concepts/extensibility/) von PWA Studio.

1. Der Apollo-Client erwartet den AEM GraphQL-Endpunkt auf <https://pwa-studio/endpoint.js>. Um den Endpunkt diesem Speicherort zuzuordnen, müssen Sie die UPWARD-Konfiguration Ihrer PWA Studio-Anwendung anpassen:
a. Fügen Sie die Variable AEM_CFM_GRAPHQL zu pwa-root/.env hinzu und passen Sie sie an, sodass sie auf Ihren GraphQL-Endpunkt für AEM Inhaltsfragmente verweist.

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

Folgen Sie der Dokumention zu AEM-Inhaltsfragmenten, um einen GraphQL-Endpunkt für Ihr AEM-Projekt einzurichten. Fügen Sie in Ihrem AEM-Projekt außerdem die folgenden Konfigurationen hinzu, damit Ihre PWA Studio-Anwendung auf den GraphQL-Endpunkt zugreifen kann:

* Adobe Granite Cross-Origin Resource Sharing Policy (com.adobe.granite.cors.impl.CORSPolicyImpl)

   Legen Sie die Eigenschaft „allowedorigin“ auf den vollständigen Host-Namen Ihrer PWA-Anwendung fest.

   Beispiel: <https://pwa-studio-test-vflyn.local.pwadev:9366>

* Apache Sling Referrer Filter (org.apache.sling.security.impl.ReferrerFilter.cfg.json)

   Setzen Sie die Eigenschaft „allow.hosts“ auf den Hostnamen Ihrer PWA-Anwendung.

   Beispiel: pwa-studio-test-vflyn.local.pwadev

Die vollständigen Beispiele für beide Konfigurationen finden Sie hier: <https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cfm-blog-extension/aem/config/src/main/content/jcr_root/apps/blog-demo/config>.

Um den GraphQL-Endpunkt zu präsentieren, haben wir einige Beispiel-Inhaltsfragmentmodelle und -daten über ein Inhaltspaket vorbereitet. Diese funktionieren gut zusammen mit den React-Komponenten, die mit der PWA Studio-Erweiterung bereitgestellt werden.

## Verwendung {#how-to-use}

Diese Erweiterung gilt als Beispielimplementierung der Verbindung einer PWA Studio-Anwendung mit AEM zum Abrufen und Rendern von Inhalten über GraphQL.

Je nach Anwendungsfall sollten Sie eigene benutzerdefinierte Inhaltsfragmentmodelle erstellen, die zu einem benutzerdefinierten GraphQL-Schema führen, das dann von Ihren eigenen React-Komponenten genutzt werden kann.

Produktions-Setups können verschiedene Aspekte aufweisen.

* Sie können über einen einzigen zusammengeführten GraphQL-Endpunkt verfügen, der AEM und Adobe Commerce-GraphQL-Daten kombiniert, anstatt den Apollo-Client anzupassen.
* Ihre PWA Studio-Anwendung könnte die AEM GraphQL-Endpunkt-URL direkt verwenden, ohne dass ein Proxy mit UPWARD vorhanden ist. Der Proxy kann auch auf eine andere Ebene verschoben werden (z. B. CDN).
* Welcher Ansatz für Sie am besten geeignet ist, hängt auch stark davon ab, wie Sie die PWA Studio-Anwendung an den Endbenutzer bereitstellen.

Diese Erweiterung enthält zwei Beispiele.

### Blog {#blog}

Zeigt Blog-Beiträge basierend auf einigen Inhaltsfragmentmodellen an. Darüber hinaus enthält es Beispiele dazu, wie man den Apollo-Client so konfiguriert, dass er mit dem AEM GraphQL-Endpunkt zusammenarbeitet und wie die Navigationskomponente in PWA Studio erweitert wird. Weitere Informationen finden Sie unter [GitHub](https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cfm-blog-extension).

### PDP-Anreicherung {#pdp-enrichment}

Ermöglicht es Marketern, PDPs einfach mit zusätzlichen Inhalten anzureichern, die als Inhaltsfragmente verwaltet werden.  Weitere Informationen finden Sie unter [GitHub](https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cif-product-page-extension).
