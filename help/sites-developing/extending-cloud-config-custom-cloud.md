---
title: Erstellen eines individuellen Cloud-Service
seo-title: Erstellen eines individuellen Cloud-Service
description: Die standardmäßigen Cloud-Services können durch individuelle Cloud-Services erweitert werden
seo-description: Die standardmäßigen Cloud-Services können durch individuelle Cloud-Services erweitert werden
uuid: b105a0c1-b68c-4f57-8e3b-561c8051a08e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: e48e87c6-43ca-45ba-bd6b-d74c969757cd
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Erstellen eines individuellen Cloud-Service{#creating-a-custom-cloud-service}

Die standardmäßigen Cloud-Services können durch individuelle Cloud-Services erweitert werden. So können Sie auf strukturierte Weise eigenes Markup in die Seite einfügen. Diese Funktion ist hauptsächlich für externe Analyseanbieter hilfreich, z. B. Google Analytics, Chartbeat usw. Cloud-Services werden von übergeordneten Seiten auf untergeordnete Seiten übernommen. Dabei kann die Übernahme auf jeder Ebene unterbrochen werden.

>[!NOTE]
>
>In dieser Schritt-für-Schritt-Anleitung zum Erstellen eines neuen Cloud-Service wird Google Analytics als Beispiel verwendet. Einige Informationen treffen auf Ihren Anwendungsfall möglicherweise nicht zu.

1. Erstellen Sie in CRXDE Lite einen neuen Knoten unter `/apps`:

   * **Name**: `acs`
   * **Typ**: `nt:folder`

1. Create a new node under `/apps/acs`:

   * **Name**: `analytics`
   * **Typ**: `sling:Folder`

1. Create 2 new nodes under `/apps/acs/analytics`:

   * **Name**: components
   * **Typ**: `sling:Folder`
   und

   * **Name**: templates
   * **Typ**: `sling:Folder`


1. Rechtsklick `/apps/acs/analytics/components`. Wählen Sie **Erstellen...** und dann **Komponente erstellen...** aus. Im Dialogfeld, das sich öffnet, können Sie Folgendes angeben:

   * **Beschriftung**: `googleanalyticspage`
   * **Titel**: `Google Analytics Page`
   * **Super Type**: `cq/cloudserviceconfigs/components/configpage`
   * **Gruppe**: `.hidden`

1. Click **Next** twice and specify:

   * **Zugelassene übergeordnete Elemente:** `acs/analytics/templates/googleanalytics`
   Click **Next** twice and click **OK**.

1. Add a property to `googleanalyticspage`:

   * **Name:** `cq:defaultView`
   * **Wert:** `html`

1. Create a new file named `content.jsp` under `/apps/acs/analytics/components/googleanalyticspage`, with the following content:

   ```xml
   <%@page contentType="text/html"
               pageEncoding="utf-8"%><%
   %><%@include file="/libs/foundation/global.jsp"%><div>
   
   <div>
       <h3>Google Analytics Settings</h3>
       <ul>
           <li><div class="li-bullet"><strong>accountID: </strong><br><%= xssAPI.encodeForHTML(properties.get("accountID", "")) %></div></li>
       </ul>
   </div>
   ```

1. Create a new node under `/apps/acs/analytics/components/googleanalyticspage/`:

   * **Name**: `dialog`
   * **Typ**: `cq:Dialog`
   * **Eigenschaften**:

      * **Name**: `title`
      * **Typ**: `String`
      * **Wert**: `Google Analytics Config`
      * **Name**: `xtype`
      * **Typ**: `String`
      * **Wert**: `dialog`

1. Create a new node under `/apps/acs/analytics/components/googleanalyticspage/dialog`:

   * **Name**: `items`
   * **Typ**: `cq:Widget`
   * **Eigenschaften**:

      * **Name**: `xtype`
      * **Typ**: `String`
      * **Wert**: `tabpanel`

1. Create a new node under `/apps/acs/analytics/components/googleanalyticspage/dialog/items`:

   * **Name**: `items`
   * **Typ**: `cq:WidgetCollection`

1. Create a new node under `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items`:

   * **Name**: tab1
   * **Typ**: `cq:Panel`
   * **Eigenschaften**:

      * **Name**: `title`
      * **Typ**: `String`
      * **Wert**: `Config`

1. Create a new node under `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items/tab1`:

   * **Name**: items
   * **Typ**: `nt:unstructured`
   * **Eigenschaften**:

      * **Name**: `fieldLabel`
      * **Typ**: String
      * **Wert**: Account ID

      * **Name**: `fieldDescription`
      * **Typ**: `String`
      * **Wert**: `The account ID assigned by Google. Usually in the form UA-NNNNNN-N`

      * **Name**: `name`
      * **Typ**: `String`
      * **Wert**: `./accountID`
      * **Name**: `validateOnBlur`
      * **Typ**: `String`
      * **Wert**: `true`
      * **Name**: `xtype`
      * **Typ**: `String`
      * **Wert**: `textfield`

1. Copy `/libs/cq/cloudserviceconfigs/components/configpage/body.jsp` to `/apps/acs/analytics/components/googleanalyticspage/body.jsp` and change `libs` to `apps` on line 34 and make the script reference on line 79 a fully qualified path.
1. Create a new template under `/apps/acs/analytics/templates/`:

   * with **Resource Type** = `acs/analytics/components/googleanalyticspage`
   * with **Label** = `googleanalytics`
   * mit **Titel**= `Google Analytics Configuration`
   * with **allowedPath** = `/etc/cloudservices/googleanalytics(/.*)?`
   * with **allowedChildren** = `/apps/acs/analytics/templates/googleanalytics`
   * with **sling:resourceSuperType** = `cq/cloudserviceconfigs/templates/configpage` (on template node, not the jcr:content node)
   * with **cq:designPath** = `/etc/designs/cloudservices/googleanalytics` (on jcr:content)

1. Neue Komponente erstellen: `/apps/acs/analytics/components/googleanalytics`.

   Fügen Sie den folgenden Inhalt zu `googleanalytics.jsp` hinzu:

   ```xml
   <%@page import="org.apache.sling.api.resource.Resource,
                   org.apache.sling.api.resource.ValueMap,
                   org.apache.sling.api.resource.ResourceUtil,
                   com.day.cq.wcm.webservicesupport.Configuration,
                   com.day.cq.wcm.webservicesupport.ConfigurationManager" %>
   <%@include file="/libs/foundation/global.jsp" %><%
   
   String[] services = pageProperties.getInherited("cq:cloudserviceconfigs", new String[]{});
   ConfigurationManager cfgMgr = resource.getResourceResolver().adaptTo(ConfigurationManager.class);
   if(cfgMgr != null) {
       String accountID = null;
       Configuration cfg = cfgMgr.getConfiguration("googleanalytics", services);
       if(cfg != null) {
           accountID = cfg.get("accountID", null);
       }
   
       if(accountID != null) {
       %>
   <script type="text/javascript">
   
     var _gaq = _gaq || [];
     _gaq.push(['_setAccount', '<%= accountID %>']);
     _gaq.push(['_trackPageview']);
   
     (function() {
       var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
       ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
       var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
     })();
   
   </script><%
       }
   }
   %>
   ```

   Dadurch sollte das benutzerdefinierte Markup basierend auf den Konfigurationseigenschaften ausgegeben werden.

1. Navigate to `http://localhost:4502/miscadmin#/etc/cloudservices` and create a new page:

   * **Titel**: `Google Analytics`
   * **Name**: `googleanalytics`
   Go back in CRXDE Lite, and under `/etc/cloudservices/googleanalytics`, add the following property to `jcr:content`:

   * **Name**: `componentReference`
   * **Typ**: `String`
   * **Wert**: `acs/analytics/components/googleanalytics`


1. Navigate to the newly created Service page ( `http://localhost:4502/etc/cloudservices/googleanalytics.html`) and click the **+** to create a new config:

   * **Übergeordnete Konfiguration**: `/etc/cloudservices/googleanalytics`
   * **Titel:**  `My First GA Config`
   Wählen Sie **Google Analytics Configuration** und klicken Sie auf **Erstellen**.

1. Geben Sie eine **Konto-ID** ein, z. B. `AA-11111111-1`. Klicken Sie auf **OK**.
1. Navigieren Sie zu einer Seite und fügen Sie die neu erstellte Konfiguration in den Seiteneigenschaften unter der Registerkarte **Cloud-Services** hinzu.
1. Das benutzerdefinierte Markup wird der Seite hinzugefügt.

