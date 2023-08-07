---
title: Hinzufügen von Adobe Analytics-Tracking zu Komponenten
description: Hinzufügen von Adobe Analytics-Tracking zu Komponenten
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: e6c1258c-81d5-48e4-bdf1-90d7cc13a22d
source-git-commit: 260f71acd330167572d817fdf145a018b09cbc65
workflow-type: tm+mt
source-wordcount: '1266'
ht-degree: 90%

---

# Hinzufügen von Adobe Analytics-Tracking zu Komponenten{#adding-adobe-analytics-tracking-to-components}

## Einschließen des Adobe Analytics-Moduls in eine Seitenkomponente {#including-the-adobe-analytics-module-in-a-page-component}

Seitenvorlagenkomponenten (z. B. `head.jsp, body.jsp`) benötigen JSP-Includes, um ContextHub und die Adobe Analytics-Integration (die Teil der Cloud Services ist) zu laden. Beide Includes laden JavaScript-Dateien.

Der ContextHub-Eintrag sollte direkt unter dem `<head>`-Tag erfolgen, während Cloud Services in den `<head>` und vor dem Abschnitt `</body>` aufgenommen werden sollten. Beispiel:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
...
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
...
</head>
<body>
...
    <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
</body>
```

Mit dem `contexthub`-Skript, das Sie nach dem `<head>`-Element einfügen, werden die ContextHub-Funktionen zur Seite hinzugefügt.

Die `cloudservices`-Skripte, die Sie in den Abschnitten `<head>` und `<body>` hinzufügen, gelten für die Cloud Services-Konfigurationen, die der Seite hinzugefügt werden. (Wenn die Seite mehr als eine Cloud Services-Konfiguration verwendet, müssen Sie die ContextHub-JSP und die Cloud Services-JSP nur einmal einschließen.)

Wenn der Seite ein Adobe Analytics-Framework hinzugefügt wird, generieren die `cloudservices`-Skripte Adobe Analytics-bezogenes JavaScript und Verweise auf Client-seitige Bibliotheken, ähnlich wie im folgenden Beispiel:

```xml
<div class="sitecatalyst cloudservice">
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/sitecatalyst.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/util.js"></script>
<script type="text/javascript" src="/content/geometrixx-outdoors/_jcr_content/analytics.sitecatalyst.js"></script>
<script type="text/javascript" src="/etc/clientlibs/mac/mac-sc.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/plugins.js"></script>
<script type="text/javascript">
<!--
CQ_Analytics.Sitecatalyst.frameworkComponents = ['foundation/components/page'];
/**
 * Sets Adobe Analytics variables accordingly to mapped components. If <code>options</code>
 * object is provided only variables matching the options.componentPath are set.
 *
 * @param {Object} options Parameter object from CQ_Analytics.record() call. Optional.
 */
CQ_Analytics.Sitecatalyst.updateEvars = function(options) {
    this.frameworkMappings = [];
 this.frameworkMappings.push({scVar:"pageName",cqVar:"pagedata.title",resourceType:"foundation/components/page"});
    for (var i=0; i<this.frameworkMappings.length; i++){
  var m = this.frameworkMappings[i];
  if (!options || options.compatibility || (options.componentPath == m.resourceType)) {
   CQ_Analytics.Sitecatalyst.setEvar(m);
  }
    }
}

CQ_Analytics.CCM.addListener("storesinitialize", function(e) {
 var collect = true;
    var lte = s.linkTrackEvents;
    s.pageName="content:geometrixx-outdoors:en";
    CQ_Analytics.Sitecatalyst.collect(collect);
    if (collect) {
  CQ_Analytics.Sitecatalyst.updateEvars();
     /************* DO NOT ALTER ANYTHING BELOW THIS LINE ! **************/
     var s_code=s.t();if(s_code)document.write(s_code);
     s.linkTrackEvents = lte;
     if(s.linkTrackVars.indexOf('events')==-1){delete s.events};
     $CQ(document).trigger("sitecatalystAfterCollect");
    }
});
//-->
</script>
<script type="text/javascript">
<!--
if(navigator.appVersion.indexOf('MSIE')>=0)document.write(unescape('%3C')+'\!-'+'-')
//-->
</script>
<noscript><img src="https://daydocumentation.112.2o7.net/b/ss/daydocumentation/1/H.25--NS/1380120772954?cdp=3&gn=content%3Ageometrixx-outdoors%3Aen" height="1" width="1" border="0" alt=""/></noscript>
<span data-tracking="{event:'pageView', values:{}, componentPath:'foundation/components/page'}"></span>
<div id="cq-analytics-texthint" style="background:white; padding:0 10px; display:none;">
 <h3 class="cq-texthint-placeholder">Component clientcontext is missing or misplaced.</h3>
</div>
<script type="text/javascript">
$CQ(function(){
 if( CQ_Analytics &&
  CQ_Analytics.ClientContextMgr &&
  !CQ_Analytics.ClientContextMgr.isConfigLoaded )
  {
   $CQ("#cq-analytics-texthint").show();
  }
});
</script>
</div>
```

Bei allen AEM Beispiel-Sites wie Geometrixx Outdoors ist dieser Code enthalten.

### Das sitecatalystAfterCollect-Ereignis {#the-sitecatalystaftercollect-event}

Das `cloudservices`-Skript löst das `sitecatalystAfterCollect`-Ereignis aus:

```
$CQ(document).trigger("sitecatalystAfterCollect");
```

Dieses Ereignis wird als Bestätigung ausgelöst, sobald die Seitenverfolgung abgeschlossen ist. Wenn Sie auf dieser Seite zusätzliche Tracking-Vorgänge ausführen, müssen Sie einen Listener für dieses Ereignis anstelle der Ereignisse „document load“ oder „document ready“ verwenden. Durch Verwendung des `sitecatalystAfterCollect`-Ereignisses vermeiden Sie Konflikte oder anderes unvorhersehbares Verhalten.

>[!NOTE]
>
>Die `/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js`-Bibliothek enthält den Code aus der Adobe Analytics-`s_code.js` -Datei.

## Implementieren des Adobe Analytics-Trackings für benutzerdefinierte Komponenten {#implementing-adobe-analytics-tracking-for-custom-components}

Aktivieren Sie Ihre AEM-Komponenten für die Interaktion mit dem Adobe Analytics-Framework. Konfigurieren Sie dann das Framework so, dass Adobe Analytics die Komponentendaten verfolgt.

Komponenten, die mit dem Adobe Analytics-Framework interagieren, werden in Sidekick angezeigt, wenn Sie ein Framework bearbeiten. Nachdem Sie die Komponente auf das Framework gezogen haben, werden die Eigenschaften der Komponente angezeigt und Sie können diese den Adobe Analytics-Eigenschaften zuordnen. (Einzelheiten finden Sie unter [Einrichten eines Frameworks für das grundlegende Tracking](/help/sites-administering/adobeanalytics-connect.md#creating-a-adobe-analytics-framework).)

Komponenten können mit dem Adobe Analytics-Framework interagieren, wenn sie einen untergeordneten Knoten `analytics` beinhalten. Der Knoten `analytics` hat folgende Eigenschaften:

* `cq:trackevents`: Identifiziert das von der Komponente angezeigte CQ-Ereignis. (Siehe „Benutzerdefinierte Ereignisse“.)
* `cq:trackvars`: Benennt die den Adobe Analytics-Eigenschaften zugeordneten CQ-Variablen.
* `cq:componentName`: Der Name der Komponente, die in Sidekick angezeigt wird.
* `cq:componentGroup`: Die Gruppe in Sidekick, die die Komponente enthält.

Der Code in der JSP-Komponente fügt der Seite das JavaScript hinzu, das das Tracking auslöst, und definiert die Daten, die nachverfolgt werden. Der Ereignisname und die Datennamen, die im JavaScript verwendet werden, müssen mit den entsprechenden Werten der Eigenschaften im Knoten `analytics` übereinstimmen.

* Verwenden Sie das data-tracking-Attribut, um Ereignisdaten beim Laden einer Seite zu verfolgen. (Siehe [Tracking benutzerspezifischer Ereignisse beim Laden der Seite](/help/sites-developing/extending-analytics.md#tracking-custom-events-on-page-load).)
* Verwenden Sie die Funktion „CQ_Analytics.record“, um Ereignisdaten zu verfolgen, wenn Benutzende mit den Seitenfunktionen interagieren. (Siehe [Tracking benutzerspezifischer Ereignisse nach dem Laden einer Seite](/help/sites-developing/extending-analytics.md#tracking-custom-events-after-page-load).)

Wenn Sie diese Methoden zum Daten-Tracking verwenden, wird Adobe Analytics automatisch vom Adobe Analytics-Integrationsmodul aufgerufen, um Ereignisse und Daten aufzuzeichnen.

### Beispiel: Verfolgen von topnav-Klicks {#example-tracking-topnav-clicks}

Erweitern Sie die Foundation-Komponente „topnav“ so, dass Adobe Analytics Klicks auf Navigations-Links oben auf der Seite verfolgt. Beim Klicken auf einen Navigations-Link zeichnet Adobe Analytics den Link und die Seite auf, auf die geklickt wurde.

Folgende Aufgaben müssen für die unten beschriebenen Verfahren bereits abgeschlossen sein:

* Erstellen einer CQ-Applikation.
* Erstellen einer Adobe Analytics-Konfiguration und eines Adobe Analytics-Frameworks.

#### Kopieren der topnav-Komponente. {#copy-the-topnav-component}

Kopieren Sie der topnav- Komponente in die CQ-Anwendung. Dieses Verfahren setzt voraus, dass Ihre Anwendung in CRXDE Lite eingerichtet ist.

1. Klicken Sie mit der rechten Maustaste auf den Knoten `/libs/foundation/components/topnav` und dann auf „Kopieren“.
1. Klicken Sie mit der rechten Maustaste auf den Ordner „Komponenten“ unter dem Anwendungsordner und dann auf „Einfügen“.
1. Klicken Sie auf „Alle speichern“

#### Integrieren von topnav mit dem Adobe Analytics Framework {#integrating-topnav-with-the-adobe-analytics-framework}

Konfigurieren Sie die topnav-Komponente und bearbeiten Sie die JSP-Datei, um das Verfolgen von Ereignissen und Daten zu definieren.

1. Klicken Sie mit der rechten Maustaste auf den topnav-Knoten und anschließend auf „Erstellen“ > „Knoten erstellen“. Geben Sie folgende Eigenschaftenwerte ein und klicken Sie dann auf „OK“:

   * Name: `analytics`
   * Typ: `nt:unstructured`

1. Fügen Sie dem Knoten analytics die folgende Eigenschaft hinzu, damit Sie das Tracking-Ereignis benennen können:

   * Name: cq:trackevents
   * Typ: String
   * Wert: topnavClick

1. Fügen Sie dem Knoten analytics die folgende Eigenschaft hinzu, damit Sie die Datenvariablen benennen können:

   * Name: cq:trackvars
   * Typ: String
   * Wert: topnavTarget,topnavLocation

1. Fügen Sie die folgende Eigenschaft zum Knoten „analytics“ hinzu, um die Komponente für den Sidekick zu benennen:

   * Name: cq:componentName
   * Typ: String
   * Wert: topnav (tracking)

1. Fügen Sie die folgende Eigenschaft zum Knoten „analytics“ hinzu, um die Komponentengruppe für den Sidekick zu benennen:

   * Name: cq:componentGroup
   * Typ: String
   * Wert: General

1. Klicken Sie auf „Alle speichern“.
1. Öffnen Sie die Datei `topnav.jsp`.
1. Fügen Sie dem Element das folgende Attribut hinzu:

   ```xml
   onclick = "tracknav('<%= child.getPath() %>.html')"
   ```

1. Fügen Sie unten auf der Seite den folgenden JavaScript-Code hinzu:

   ```xml
   <script type="text/javascript">
       function tracknav(target) {
               if (CQ_Analytics.Sitecatalyst) {
                   CQ_Analytics.record({
                       event: 'topnavClick',
                       values: {
                           topnavTarget: target,
                           topnavLocation:'<%=currentPage.getPath() %>.html'
                       },
                       componentPath: '<%=resource.getResourceType()%>'
                   });
               }
       }
   </script>
   ```

1. Klicken Sie auf „Alle speichern“

Der Inhalt der `topnav.jsp`-Datei sollte jetzt wie folgt aussehen:

```xml
<%@page session="false"%><%--
  Copyright 1997-2008 Day Management AG
  Barfuesserplatz 6, 4001 Basel, Switzerland
  All Rights Reserved.

  This software is the confidential and proprietary information of
  Day Management AG, ("Confidential Information"). You shall not
  disclose such Confidential Information and shall use it only in
  accordance with the terms of the license agreement you entered into
  with Day.

  ==============================================================================

  Top Navigation component

  Draws the top navigation

--%><%@include file="/libs/foundation/global.jsp"%><%
%><%@ page import="java.util.Iterator,
        com.day.text.Text,
        com.day.cq.wcm.api.PageFilter,
        com.day.cq.wcm.api.Page,
        com.day.cq.commons.Doctype,
        org.apache.commons.lang3.StringEscapeUtils" %><%

    // get starting point of navigation
    long absParent = currentStyle.get("absParent", 2L);
    String navstart = Text.getAbsoluteParent(currentPage.getPath(), (int) absParent);

    //if not deep enough take current node
    if (navstart.equals("")) navstart=currentPage.getPath();

    Resource rootRes = slingRequest.getResourceResolver().getResource(navstart);
    Page rootPage = rootRes == null ? null : rootRes.adaptTo(Page.class);
    String xs = Doctype.isXHTML(request) ? "/" : "";
    if (rootPage != null) {
        Iterator<Page> children = rootPage.listChildren(new PageFilter(request));
        while (children.hasNext()) {
            Page child = children.next();
            %><a onclick = "tracknav('<%= child.getPath() %>.html')"  href="<%= child.getPath() %>.html"><%
            %><img alt="<%= StringEscapeUtils.escapeXml(child.getTitle()) %>" src="<%= child.getPath() %>.navimage.png"<%= xs %>></a><%
        }
    }
%><script type="text/javascript">
    function tracknav(target) {
            if (CQ_Analytics.Sitecatalyst) {
                CQ_Analytics.record({
                    event: 'topnavClick',
                    values: {
                        topnavTarget:target,
                        topnavLocation:'<%=currentPage.getPath() %>.html'
                    },
                    componentPath: '<%=resource.getResourceType()%>'
                });
            }
    }
</script>
```

>[!NOTE]
>
>Oft ist es erwünscht, Daten aus dem ContextHub zu verfolgen. Weitere Informationen zur Verwendung von JavaScript zum Abrufen von Informationen finden Sie unter [Zugriff auf Werte im ContextHub](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).

#### Hinzufügen der Verfolgungskomponente zu Sidekick {#adding-the-tracking-component-to-sidekick}

Fügen Sie Komponenten, die für das Tracking mit Adobe Analytics aktiviert sind, zu Sidekick hinzu, um sie dem Framework hinzuzufügen.

1. Öffnen Sie das Adobe Analytics-Framework über Ihre Adobe Analytics-Konfiguration. ([http://localhost:4502/etc/cloudservices/sitecatalyst.html](http://localhost:4502/etc/cloudservices/sitecatalyst.html))
1. Klicken Sie im Sidekick auf die Schaltfläche „Design“.

   ![Die Schaltfläche „Design“ mit einem rechten Winkel in einem Quadrat.](assets/chlimage_1a.png)

1. Klicken Sie im Konfigurationsbereich für das Linktracking auf „Vererbung konfigurieren“.

   ![chlimage_1](assets/chlimage_1aa.png)

1. Wählen Sie aus der Liste „Zugelassene Komponenten“ im Abschnitt „Allgemein“ den Eintrag „topnav (tracking)“ aus und klicken Sie dann auf „OK“.
1. Erweitern Sie den Sidekick, um in den Bearbeitungsmodus zu wechseln. Die Komponente ist jetzt in der Gruppe „Allgemein“ verfügbar.

#### Hinzufügen der topnav-Komponente zum Framework {#adding-the-topnav-component-to-your-framework}

Ziehen Sie die topnav-Komponente zu Ihrem Adobe Analytics-Framework und ordnen Sie die Variablen und Ereignisse den Adobe Analytics-Variablen und -Ereignissen zu. (Einzelheiten finden Sie unter [Einrichten eines Frameworks für das grundlegende Tracking](/help/sites-administering/adobeanalytics-connect.md).)

![chlimage_1-1](assets/chlimage_1-1a.png)

Die topnav-Komponente ist jetzt mit dem Adobe Analytics-Framework integriert. Wenn Sie die Komponente in eine Seite einfügen, werden beim Klicken auf die Elemente in der oberen Navigationsleiste Tracking-Daten an Adobe Analytics gesendet.

### Senden von s.products-Daten an Adobe Analytics {#sending-s-products-data-to-adobe-analytics}

Komponenten können Daten für die s.products-Variable erzeugen, die an Adobe Analytics gesendet werden. Entwerfen Sie Komponenten, die Daten für die s.products-Variable erzeugen:

* Zeichnen Sie einen Wert `product` mit einer spezifischen Struktur auf.
* Zeigen Sie die Daten-Member des `product`-Werts an, sodass sie Adobe Analytics-Variablen im Adobe Analytics-Framework zugeordnet werden können.

Die s.products-Variable von Adobe Analytics verwendet die folgende Syntax:

```
s.products="category;product;quantity;price;eventY={value}|eventZ={value};evarA={value}|evarB={value}"
```

Das Adobe Analytics-Integrationsmodul erstellt die `s.products`-Variable anhand der `product`-Werte, die von den AEM-Komponenten erzeugt werden. Der von den AEM-Komponenten in JavaScript erzeugte `product`-Wert ist ein Array von Werten mit folgender Struktur:

```
"product": [{
    "category": "",
    "sku"     : "path to product node",
    "quantity": quantity,
    "price"   : price,
    "events   : {
      "eventName1": "eventValue1",
      "eventName_n": "eventValue_n"
    }
    "evars"   : {
      "eVarName1": "eVarValue1",
      "eVarName_n": "eVarValue_n"
    }
}]
```

Wenn ein Datenelement im `product`-Wert ausgelassen wird, wird es als leere Zeichenfolge in s.products gesendet.

>[!NOTE]
>
>Wenn einem s.product-Wert kein Ereignis zugeordnet ist, verwendet Adobe Analytics standardmäßig das `prodView`-Ereignis.

Der Knoten `analytics` der Komponente muss die Namen der Variablen anzeigen, die die `cq:trackvars`-Eigenschaft verwenden:

* product.category
* product.sku
* product.quantity
* product.price
* product.events.eventName1
* product.events.eventName_n
* product.evars.eVarName1
* product.evars.eVarName_n

Das E-Commerce-Modul stellt mehrere Komponenten bereit, die Daten für die Variable „s.products“ generieren. Beispiel: die `submitorder` component ([http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp](http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp)) generiert JavaScript, das dem folgenden Beispiel ähnelt:

```
<script type="text/javascript">
    function trackCartPurchase() {
        if (CQ_Analytics.Sitecatalyst) {
            CQ_Analytics.record({
                "event": ["productsCartPurchase"],
                "values": {
                    "product": [
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/1",
                            "quantity": 3,
                            "price"   : 179.7,
                            "evars"   : {
                                "childSku": "/path/to/prod/1/green/xs",
                                "size"    : "XS"
                            }
                        },
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/2",
                            "quantity": 10,
                            "price"   : 150,
                            "evars"   : {
                                "childSku": "/path/to/prod/2",
                                "size"    : ""
                            }
                        },
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/3",
                            "quantity": 2,
                            "price"   : 102,
                            "evars"   : {
                                "childSku": "/path/to/prod/3/m",
                                "size"    : "M"
                            }
                        }
                    ]
                },
                "componentPath": "commerce/components/submitorder"
            });
            CQ_Analytics.record({
                "event": ["discountRedemption"],
                "values": {
                    "discount": "/path/to/discount/1 - /path/to/discount/2",
                    "product" : [{
                        "category": "",
                        "sku"     : "Promotional Discount",
                        "events"  : {"discountRedemption": 20.00}
                    }]
                },
                "componentPath": "commerce/components/submitorder"
            });
            CQ_Analytics.record({
                "event": ["cartPurchase"],
                "values": {
                    "orderId"       : "00e40e2d-13a2-4a00-a8ee-01a9ebb0bf68",
                    "shippingMethod": "overnight",
                    "paymentMethod" : "Amex",
                    "billingState"  : "NY",
                    "billingZip"    : "10458",
                    "product"       : [{"category": "", "sku": "", "quantity": "", "price": ""}]
                },
                "componentPath": "commerce/components/submitorder"
            });
        }
        return true;
    }
</script>
```

#### Begrenzen der Größe von Tracking-Aufrufen {#limiting-the-size-of-tracking-calls}

Im Allgemeinen beschränken Webbrowser die Größe von GET-Anfragen. Da CQ-Produkt- und SKU-Werte Repository-Pfade sind, können Produkt-Arrays, die mehrere Werte enthalten, die Anfragegrößenbeschränkung überschreiten. Daher sollten die Komponenten die Anzahl der Elemente im `product`-Array jeder `CQ_Analytics.record function` beschränken. Erstellen Sie mehrere Funktionen, wenn die Anzahl der Elemente, die Sie verfolgen müssen, die Grenze überschreiten kann.

Zum Beispiel der eCommerce `submitorder` -Komponente begrenzt die Anzahl der `product` -Elemente in einem -Aufruf von vier. Wenn der Warenkorb mehr als vier Produkte enthält, erzeugt sie mehrere `CQ_Analytics.record`-Funktionen.
