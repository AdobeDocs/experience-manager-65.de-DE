---
title: Erstellen benutzerspezifischer Erweiterungen
seo-title: Erstellen benutzerspezifischer Erweiterungen
description: Sie können Ihren benutzerdefinierten Code in Adobe Campaign aus AEM oder aus AEM nach Adobe Campaign aufrufen
seo-description: Sie können Ihren benutzerdefinierten Code in Adobe Campaign aus AEM oder aus AEM nach Adobe Campaign aufrufen
uuid: 8392aa0d-06cd-4b37-bb20-f67e6a0550b1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: f536bcc1-7744-4f05-ac6a-4cec94a1ffb6
exl-id: 0702858e-5e46-451f-9ac3-40a4fec68ca0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 81%

---

# Erstellen benutzerspezifischer Erweiterungen{#creating-custom-extensions}

Im Allgemeinen verwenden Sie beim Implementieren eines Projekts benutzerdefinierten Code in AEM und Adobe Campaign. Mit der vorhandenen API können Sie Ihren benutzerdefinierten Code in Adobe Campaign aus AEM oder aus AEM nach Adobe Campaign aufrufen. Dieses Dokument beschreibt, wie das geht.

## Voraussetzungen {#prerequisites}

Sie müssen Folgendes installiert haben:

* Adobe Experience Manager
* Adobe Campaign 6.1

Weitere Informationen finden Sie unter [Integrieren von AEM mit Adobe Campaign 6.1](/help/sites-administering/campaignonpremise.md).

## Beispiel 1: AEM nach Adobe Campaign {#example-aem-to-adobe-campaign}

Die Standardintegration zwischen AEM und Campaign basiert auf JSON und JSSP (JavaScript Server Page). Diese JSSP-Dateien befinden sich in der Campaign-Konsole und beginnen alle mit **amc** (Adobe Marketing Cloud).

![chlimage_1-15](assets/chlimage_1-15a.png)

>[!NOTE]
>
>[Für dieses Beispiel lesen Sie bitte Geometrixx](/help/sites-developing/we-retail.md), das in Package Share verfügbar ist.

In diesem Beispiel erstellen wir eine neue benutzerdefinierte JSSP-Datei und rufen diese in AEM ab, um das Ergebnis zu erhalten. So können Sie beispielsweise Daten von Adobe Campaign abrufen oder Daten in Adobe Campaign speichern.

1. Um in Adobe Campaign eine neue JSSP-Datei zu erstellen, klicken Sie auf das Symbol **Neu**.

   ![](do-not-localize/chlimage_1-4a.png)

1. Geben Sie den Namen dieser JSSP-Datei ein. In diesem Beispiel verwenden wir **cus:custom.jssp** (d. h. es befindet sich im Namespace **cus** ).

   ![chlimage_1-16](assets/chlimage_1-16a.png)

1. Fügen Sie den folgenden Code in die jssp-Datei ein:

   ```
   <%
   var origin = request.getParameter("origin");
   document.write("Hello from Adobe Campaign, origin : " + origin);
   %>
   ```

1. Speichern Sie Ihre Arbeit. Die verbleibende Arbeit erfolgt in AEM.
1. Erstellen Sie ein einfaches Servlet in AEM, um dieses JSSP aufzurufen. In diesem Beispiel nehmen wir Folgendes an:

   * Sie haben eine funktionierende Verbindung zwischen AEM und Campaign
   * Der Campaign-Cloud-Service ist auf **/content/geometrixx-outdoor** konfiguriert

   Das wichtigste Objekt in diesem Beispiel ist der **GenericCampaignConnector**, mit dem Sie JSSP-Dateien auf der Adobe Campaign-Seite aufrufen (abrufen und posten) können.

   Es folgt ein kleines Code-Snippet:

   ```
   @Reference
   private GenericCampaignConnector campaignConnector;
   ...
   Map<String, String> params = new HashMap<String, String>();
   params.put("origin", "AEM");
   CallResults results = campaignConnector.callGeneric("/jssp/cus/custom.jssp", params, credentials);
   return results.bodyAsString();
   ```

1. Wie Sie in diesem Beispiel sehen, müssen Sie die Anmeldeinformationen in den Aufruf eingeben. Sie können dies über die getCredentials()-Methode abrufen, bei der Sie eine Seite übergeben, auf der der Campaign-Cloud-Dienst konfiguriert ist.

   ```xml
   // page containing the cloudservice for Adobe Campaign
   Configuration config = campaignConnector.getWebserviceConfig(page.getContentResource().getParent());
   CampaignCredentials credentials = campaignConnector.retrieveCredentials(config);
   ```

Der vollständige Code lautet wie folgt:

```java
import java.io.IOException;
import java.io.PrintWriter;
import java.util.HashMap;
import java.util.Map;

import javax.servlet.ServletException;

import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.sling.SlingServlet;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.servlets.SlingSafeMethodsServlet;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.mcm.campaign.CallResults;
import com.day.cq.mcm.campaign.CampaignCredentials;
import com.day.cq.mcm.campaign.GenericCampaignConnector;
import com.day.cq.wcm.api.Page;
import com.day.cq.wcm.api.PageManager;
import com.day.cq.wcm.api.PageManagerFactory;
import com.day.cq.wcm.webservicesupport.Configuration;

@SlingServlet(paths="/bin/campaign", methods="GET")
public class CustomServlet extends SlingSafeMethodsServlet {

 private final Logger log = LoggerFactory.getLogger(this.getClass());

 @Reference
 private GenericCampaignConnector campaignConnector;

 @Reference
 private PageManagerFactory pageManagerFactory;

 @Override
 protected void doGet(SlingHttpServletRequest request,
   SlingHttpServletResponse response) throws ServletException,
   IOException {

  PageManager pm = pageManagerFactory.getPageManager(request.getResourceResolver());

  Page page = pm.getPage("/content/geometrixx-outdoors");

  String result = null;
  if ( page != null) {
   result = callCustomFunction(page);
  }
  if ( result != null ) {
   PrintWriter pw = response.getWriter();
   pw.print(result);
  }
 }

 private String callCustomFunction(Page page ) {
  try {
   Configuration config = campaignConnector.getWebserviceConfig(page.getContentResource().getParent());
   CampaignCredentials credentials = campaignConnector.retrieveCredentials(config);

   Map<String, String> params = new HashMap<String, String>();
   params.put("origin", "AEM");
   CallResults results = campaignConnector.callGeneric("/jssp/cus/custom.jssp", params, credentials);
   return results.bodyAsString();
  } catch (Exception e ) {
   log.error("Something went wrong during the connection", e);
  }
  return null;

 }

}
```

## Beispiel 2: Adobe Campaign nach AEM  {#example-adobe-campaign-to-aem}

AEM bietet betriebsbereite APIs zum Abrufen der Objekte, die in der siteadmin-Exploreransicht verfügbar sind.

![chlimage_1-17](assets/chlimage_1-17a.png)

>[!NOTE]
>
>[Für dieses Beispiel lesen Sie bitte Geometrixx](/help/sites-developing/we-retail.md), das in Package Share verfügbar ist.

Für jeden Knoten im Explorer gibt es eine API, die mit ihm verknüpft ist. Beispiel für den Knoten :

* [http://localhost:4502/siteadmin#/content/campaigns/geometrixx/scott-recommends](http://localhost:4502/siteadmin#/content/campaigns/geometrixx/scott-recommends)

ist die API:

* [http://localhost:4502/content/campaigns/geometrixx/scott-recommends.1.json](http://localhost:4502/content/campaigns/geometrixx/scott-recommends.2.json)

Das Ende der URL **.1.json** kann durch **.2.json**, **.3.json** ersetzt werden, je nachdem wie viele Unterebenen Sie erhalten möchten. Um alle zu erhalten, kann das Schlüsselwort **infinity** verwendet werden:

* [http://localhost:4502/content/campaigns/geometrixx/scott-recommends.infinity.json](http://localhost:4502/content/campaigns/geometrixx/scott-recommends.2.json)

Um die API zu nutzen, müssen wir wissen, dass AEM standardmäßig die Standardauthentifizierung verwendet.

Eine JS-Bibliothek mit dem Namen **amcIntegration.js** ist in 6.1.1 (Build 8624 und höher) verfügbar und implementiert diese Logik unter mehreren anderen.

### AEM-API-Aufruf  {#aem-api-call}

```java
loadLibrary("nms:amcIntegration.js");

var cmsAccountId = sqlGetInt("select iExtAccountId from NmsExtAccount where sName=$(sz)","aemInstance")
var cmsAccount = nms.extAccount.load(String(cmsAccountId));
var cmsServer = cmsAccount.server;

var request = new HttpClientRequest(cmsServer+"/content/campaigns/geometrixx.infinity.json")
aemAddBasicAuthentication(cmsAccount, request);
request.method = "GET"
request.header["Content-Type"] = "application/json; charset=UTF-8";
request.execute();
var response = request.response;
```
