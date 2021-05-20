---
title: Erweitern des Asset-Editors
description: Erfahren Sie, wie sich die Funktionen des Asset-Editors mithilfe von benutzerdefinierten Komponenten erweitern lassen.
contentOwner: AG
role: Business Practitioner, Administrator
feature: Entwickler-Tools
exl-id: de1c63c1-a0e5-470b-8d83-b594513a5dbd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 85%

---

# Erweitern des Asset-Editors {#extending-asset-editor}

Beim Asset-Editor handelt es sich um die Seite, die geöffnet wird, wenn auf ein über die Asset-Freigabe gefundenes Asset geklickt wird. Er ermöglicht dem Benutzer das Bearbeiten von Aspekten des Assets wie Metadaten, Miniatur, Titel und Tags.

Die Konfiguration des Editors mit den vordefinierten Bearbeitungskomponenten wird in [Erstellen und Konfigurieren einer Asset-Editor-Seite](assets-finder-editor.md#creating-and-configuring-an-asset-editor-page) behandelt.

Neben der Verwendung bereits vorhandener Editor-Komponenten können [!DNL Adobe Experience Manager]-Entwickler auch eigene Komponenten erstellen.

## Erstellen einer Asset-Editor-Vorlage {#creating-an-asset-editor-template}

Die folgenden Beispielseiten sind in Geometrixx enthalten:

* Geometrixx-Beispielseite: `/content/geometrixx/en/press/asseteditor.html`
* Beispielvorlage: `/apps/geometrixx/templates/asseteditor`
* Beispielseitenkomponente: `/apps/geometrixx/components/asseteditor`

### Clientlib konfigurieren {#configuring-clientlib}

[!DNL Assets] -Komponenten verwenden eine Erweiterung der WCM-clientlib zum Bearbeiten. Die clientlibs werden normalerweise in `init.jsp` geladen.

Im Vergleich zum standardmäßigen Laden der clientlib (im Kernelement `init.jsp`) muss eine [!DNL Assets] -Vorlage Folgendes aufweisen:

* Die Vorlage muss die clientlib `cq.dam.edit` (anstelle von `cq.wcm.edit`) enthalten.

* Die clientlib muss auch im deaktivierten WCM-Modus (z. B. beim **Veröffentlichen** geladen) verfügbar sein, um die Eigenschaften, Aktionen und Linsen darzustellen.

In den meisten Fällen sollten diese Erfordernisse erfüllt sein, wenn das vorhandene Muster `init.jsp` (`/apps/geometrixx/components/asseteditor/init.jsp`) kopiert wird.

### JS-Aktionen konfigurieren {#configuring-js-actions}

Einige der [!DNL Assets]-Komponenten erfordern JS-Funktionen, die in `component.js` definiert sind. Kopieren Sie diese Datei in Ihr Komponentenverzeichnis und verknüpfen Sie sie.

```javascript
<script type="text/javascript" src="<%= component.getPath() %>/component.js"></script>
```

Das Beispiel lädt diese JavaScript-Quelle in `head.jsp`(`/apps/geometrixx/components/asseteditor/head.jsp`).

### Zusätzliche Stylesheets {#additional-style-sheets}

Einige der [!DNL Assets] -Komponenten verwenden die Widget-Bibliothek. Damit sie im Inhaltskontext ordnungsgemäß gerendert werden, muss ein zusätzliches Stylesheet geladen werden. Die Tag-Aktionskomponente erfordert ein weiteres zusätzliches Stylesheet.

```css
<link href="/etc/designs/geometrixx/ui.widgets.css" rel="stylesheet" type="text/css">
```

### Geometrixx-Stylesheet     {#geometrixx-style-sheet}

Die Komponenten der Beispielseite erfordern, dass alle Selektoren mit `.asseteditor` von `static.css` (`/etc/designs/geometrixx/static.css`) beginnen. Best Practice: Kopieren Sie alle `.asseteditor`-Selektoren in Ihr Stylesheet und passen Sie bei Bedarf die Regeln an.

### FormChooser: Anpassungen für eventuell geladene Ressourcen {#formchooser-adjustments-for-eventually-loaded-resources}

Der Asset-Editor verwendet die Formularauswahl, mit der Sie Ressourcen – in diesem Fall Assets – auf derselben Formularseite bearbeiten können, indem Sie der URL des Assets einfach einen Formularselektor und den Pfad des Formulars hinzufügen.

Beispiel:

* Einfache Formularseite: [http://localhost:4502/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/geometrixx/en/press/asseteditor.html)
* In der Formularseite geladenes Asset: [http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html)

Die Beispiel-Handles in `head.jsp` (`/apps/geometrixx/components/asseteditor/head.jsp`) führen Folgendes aus:

* Sie erkennen, wenn ein Asset geladen wird oder wenn das einfache Formular angezeigt werden muss.
* Wenn ein Asset geladen wird, deaktivieren sie den WCM-Modus, da ParSys nur auf einer einfachen Formularseite bearbeitet werden kann.
* Wenn ein Asset geladen wird, verwenden sie dessen Titel anstelle des Titels auf der Formularseite.

```javascript
 List<Resource> resources = FormsHelper.getFormEditResources(slingRequest);
    if (resources != null) {
        if (resources.size() == 1) {
            // single resource
            FormsHelper.setFormLoadResource(slingRequest, resources.get(0));
        } else if (resources.size() > 1) {
            // multiple resources
            // not supported by CQ 5.3
        }
    }
    Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
    String title;
    if (loadResource != null) {
        // an asset is loaded: disable WCM
        WCMMode.DISABLED.toRequest(request);

        String path = loadResource.getPath();
        Asset asset = loadResource.adaptTo(Asset.class);
        try {
            // it might happen that the adobe xmp lib creates an array
            Object titleObj = asset.getMetadata("dc:title");
            if (titleObj instanceof Object[]) {
                Object[] titleArray = (Object[]) titleObj;
                title = (titleArray.length > 0) ? titleArray[0].toString() : "";
            } else {
                title = titleObj.toString();
            }
        }
        catch (NullPointerException e) {
            title = path.substring(path.lastIndexOf("/") + 1);
        }
    }
    else {
        title = currentPage.getTitle() == null ? currentPage.getName() : currentPage.getTitle();
    }
```

Verwenden Sie im HTML-Teil den vorhergehenden festgelegten Titel (entweder Asset- oder Seitentitel):

```html
<title><%= title %></title>
```

## Erstellen einer einfachen Formularfeldkomponente {#creating-a-simple-form-field-component}

In diesem Beispiel wird das Erstellen einer Komponente beschrieben, die die Metadaten eines geladenen Assets anzeigt.

1. Erstellen Sie in Ihrem Projektverzeichnis einen Komponentenordner, z. B. `/apps/geometrixx/components/samplemeta`.
1. Fügen Sie `content.xml` mit dem folgenden Snippet hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Dimension"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Asset Editor"/>
   ```

1. Fügen Sie `samplemeta.jsp` mit dem folgenden Snippet hinzu:

   ```javascript
   <%--
   
     Sample metadata field component
   
   --%><%@ page import="com.day.cq.dam.api.Asset,
                    java.security.AccessControlException" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       String value = "";
       String name = "dam:sampleMetadata";
       boolean readOnly = false;
   
       // If the form page is requested for an asset loadResource will be the asset.
       Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
   
       if (loadResource != null) {
   
           // Determine if the loaded asset is read only.
           Session session = slingRequest.getResourceResolver().adaptTo(Session.class);
           try {
               session.checkPermission(loadResource.getPath(), "set_property");
               readOnly = false;
           }
           catch (AccessControlException ace) {
               // checkPermission throws exception if asset is read only
               readOnly = true;
           }
           catch (RepositoryException re) {}
   
           // Get the value of the metadata.
           Asset asset = loadResource.adaptTo(Asset.class);
           try {
               value = asset.getMetadata(name).toString();
           }
           catch (NullPointerException npe) {
               // no metadata dc:description available
           }
       }
   %>
   <div class="form_row">
       <div class="form_leftcol">
           <div class="form_leftcollabel">Sample Metadata</div>
       </div>
       <div class="form_rightcol">
           <%
           if (readOnly) {
               %><c:out value="<%= value %>"/><%
           }
           else {
               %><input class="text" type="text" name="./jcr:content/metadata/<%= name %>" value="<c:out value="<%= value %>" />"><%
           }%>
       </div>
   </div>
   ```

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeitbar zu machen, fügen Sie in CRXDE Lite den Knoten `cq:editConfig` (primärer Typ `cq:EditConfig`) hinzu. Um Absätze entfernen zu können, fügen Sie eine `cq:actions`-Mehrwerteigenschaft mit `DELETE` als einzigem Wert hinzu.

1. Navigieren Sie zu Ihrem Browser, wechseln Sie auf Ihrer Beispielseite (z. B.`asseteditor.html`) in den Design-Modus und aktivieren Sie Ihre neue Komponente für das Absatzsystem.

1. Im **Bearbeitungsmodus** ist die neue Komponente (z. B. **Beispielmetadaten**) jetzt im Sidekick (in der Gruppe **Asset-Editor**) verfügbar. Fügen Sie die Komponente ein. Um die Metadaten speichern zu können, müssen sie dem Metadatenformular hinzugefügt werden.

## Ändern von Metadatenoptionen {#modifying-metadata-options}

Sie können die im [Metadatenformular](assets-finder-editor.md#metadata-form-and-text-field-configuring-the-view-metadata-component) verfügbaren Namespaces ändern.

Aktuell verfügbare Metadaten sind in `/libs/dam/options/metadata` definiert:

* Die erste Ebene innerhalb dieses Verzeichnisses enthält die Namespaces.
* Die Elemente in den einzelnen Namespaces stellen Metadaten dar, beispielsweise Ergebnisse in einem lokalen Teilelement.
* Die Metadaten enthalten die Informationen für den Typ und die Optionen mit mehreren Werten.

Die Optionen können in `/apps/dam/options/metadata` überschrieben werden:

1. Kopieren Sie das Verzeichnis von `/libs` nach `/apps`.

1. Sie können Elemente entfernen, ändern und hinzufügen.

>[!NOTE]
>
>Wenn Sie neue Namespaces hinzufügen, müssen diese in Ihrem Repository/CRX registriert sein. Andernfalls tritt beim Übermitteln des Metadatenformulars ein Fehler auf.
