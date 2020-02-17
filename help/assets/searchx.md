---
title: Erweiterung der Suchfunktion von AEM Assets
description: Erweitern Sie die Suchfunktionen von AEM Assets über die Standardwerte hinaus.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Suche nach Assets erweitern {#extending-assets-search}

Sie können die Suchfunktionen von Adobe Experience Manager (AEM) Assets erweitern. Standardmäßig sucht AEM Assets anhand von Zeichenfolgen nach Assets.

Die Suchfunktion wird über die QueryBuilder-Schnittstelle durchgeführt und lässt sich mit mehreren Eigenschaften anpassen. You can overlay the default set of predicates in the following directory: `/apps/dam/content/search/searchpanel/facets`.

Sie können dem AEM Assets-Admin-Bedienfeld auch weitere Registerkarten hinzufügen.

>[!CAUTION]
>
>Seit Einführung von AEM 6.4 wird die klassische Benutzeroberfläche nicht mehr unterstützt. For announcement, see [Deprecated and removed features](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/deprecated-removed-features.html). Es empfiehlt sich, die Touch-optimierte Benutzeroberfläche zu verwenden. For customization, see [Search Facets](/help/assets/search-facets.md).

## Überlagerung {#overlaying}

Um die vorkonfigurierten Voreinstellungen zu überlagern, kopieren Sie den `facets` Knoten von `/libs/dam/content/search/searchpanel` in eine andere `/apps/dam/content/search/searchpanel/` Eigenschaft in der `facetURL` Konfiguration (standardmäßig `searchpanel``/libs/dam/content/search/searchpanel/facets.overlay.infinity.json` ).

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>Standardmäßig ist die Verzeichnisstruktur unter /`apps` nicht vorhanden und muss erstellt werden. Stellen Sie sicher, dass die Knotentypen den Typen unter /`libs` entsprechen.


## Hinzufügen von Registerkarten {#adding-tabs}

Sie können weitere Suchregisterkarten hinzufügen, indem Sie sie im AEM Assets-Admin konfigurieren. So erstellen Sie weitere Registerkarten:

1. Create the folder structure `/apps/wcm/core/content/damadmin/tabs,`if it does not already exist, and copy the `tabs` node from `/libs/wcm/core/content/damadmin` and paste it.
1. Erstellen und konfigurieren Sie die zweite Registerkarte wie gewünscht.

   >[!NOTE]
   >
   >When you create a second `siteadminsearchpanel`, be sure to set an `id` property in order to prevent form conflicts.

## Erstellen benutzerdefinierter Prädikate {#creating-custom-predicates}

AEM Assets verfügt über eine Reihe vordefinierter Prädikate, die zum Anpassen einer Seite zum Teilen von Assets verwendet werden können. Diese Art der Anpassung einer Asset-Freigabe wird unter [Erstellen und Konfigurieren einer Asset-Freigaben-Seite](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page) beschrieben.

AEM-Entwickler können neben den bereits vorhandenen Eigenschaften auch eigene Prädikate erstellen. Hierfür können sie die [QueryBuilder-API](/help/sites-developing/querybuilder-api.md) verwenden.

Um benutzerdefinierte Eigenschaften erstellen zu können, benötigen Sie Grundlagenkenntnisse über das [Widget-Framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html). 

Als Best Practice hat es sich erwiesen, eine vorhandene Eigenschaft zu kopieren und anzupassen. Beispiel-Eigenschaften befinden sich unter **/libs/cq/search/components/predicates**.

### Beispiel: Einfaches Eigenschaftsprädikat erstellen {#example-build-a-simple-property-predicate}

So erstellen Sie ein Eigenschaftsprädikat:

1. Erstellen Sie einen Komponentenordner in Ihrem Projektverzeichnis, z. B.**/ apps/geometrixx/components/titlepredicate**.
1. Fügen Sie **content.xml** hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Fügen Sie `titlepredicate.jsp`.

   ```xml
   <%--
   
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
       });
   </script>
   ```

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeitbar zu machen, fügen Sie in CRXDE einen Knoten **cq:editConfig** des primären Typs **cq:EditConfig** hinzu. Um Absätze entfernen zu können, fügen Sie eine **cq:actions**-Mehrwerteigenschaft mit **DELETE** als einzigem Wert hinzu.
1. Navigieren Sie zu Ihrem Browser und wechseln Sie auf Ihrer Beispielseite (z. B. **press.html**) in den Designmodus. Aktivieren Sie Ihre neue Komponente für das Eigenschaften-Absatzsystem (z. B. **links**).

1. Im Modus **Bearbeiten** ist die neue Komponente jetzt im Sidekick verfügbar (in der **Suchgruppe**). Fügen Sie die Komponente in die Spalte **Eigenschaften** ein, geben Sie einen Suchbegriff – z. B. **Raute** – ein und klicken Sie auf das Lupensymbol, um die Suche zu starten.

   >[!NOTE]
   >
   >Stellen Sie beim Suchen sicher, dass der Begriff korrekt eingegeben wird und auch die Groß-/Kleinschreibung stimmt. 

### Beispiel: Einfache Gruppeneigenschaft erstellen {#example-build-a-simple-group-predicate}

So erstellen Sie eine Gruppeneigenschaft:

1. Erstellen Sie einen Komponentenordner in Ihrem Projektverzeichnis, z. B. **/apps/geometrixx/components/picspredicate**.
1. Fügen Sie **content.xml** hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Fügen Sie **titlepredicate.jsp** hinzu:

   ```xml
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
       });
   ```

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeitbar zu machen, fügen Sie in CRXDE einen Knoten **cq:editConfig** des primären Typs **cq:EditConfig** hinzu. Um Absätze entfernen zu können, fügen Sie eine **cq:actions**-Mehrwerteigenschaft mit **DELETE** als einzigem Wert hinzu.
1. Navigieren Sie zu Ihrem Browser und wechseln Sie auf Ihrer Beispielseite (z. B. **press.html**) in den Designmodus. Aktivieren Sie Ihre neue Komponente für das Eigenschaften-Absatzsystem (z. B. **links**).
1. Im Modus **Bearbeiten** ist die neue Komponente jetzt im Sidekick verfügbar (in der **Suchgruppe**). Fügen Sie die Komponente in die Spalte **Eigenschaften** ein.

## Installierte Eigenschaften-Widgets {#installed-predicate-widgets}

Die folgenden Prognosen sind als vorkonfigurierte ExtJS-Widgets verfügbar.

### FulltextPredicate {#fulltextpredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| calculateName | Zeichenfolge | Name der Vorhersage. Standardwert ist `fulltext` |
| searchCallback | Funktion | Rückruf zum Auslösen der Suche nach Ereignis `keyup`. Standardwert ist `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| calculateName | Zeichenfolge | Name der Vorhersage. Standardwert ist `property` |
| propertyName | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:title` |
| defaultValue | Zeichenfolge | Vorgegebener Standardwert. |

### PathPredicate {#pathpredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| calculateName | Zeichenfolge | Name der Vorhersage. Standardwert ist `path` |
| rootPath | Zeichenfolge | Stammpfad der Vorhersage. Standardwert ist `/content/dam` |
| pathFieldPredicateName | Zeichenfolge | Standardwert ist `folder` |
| showFlatOption | Boolesch  | Markieren, um Kontrollkästchen anzuzeigen `search in subfolders`. Der Standardwert ist „true“. |

### DatePredicate {#datepredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| calculateName | Zeichenfolge | Name der Vorhersage. Standardwert ist `daterange` |
| propertyname | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:content/jcr:lastModified` |
| defaultValue | Zeichenfolge | Vorgegebener Standardwert |

### OptionsPredicate {#optionspredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| Titels | Zeichenfolge | Fügt einen zusätzlichen Top-Titel hinzu |
| calculateName | Zeichenfolge | Name der Vorhersage. Standardwert ist `daterange` |
| propertyname | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:content/metadata/cq:tags` |
| reduzieren | Zeichenfolge | Ebene reduzieren. Standardwert ist `level1` |
| triggerSearch | Boolesch  | Flag zum Auslösen der Suche beim Scheck. Standard ist false |
| searchCallback | Funktion | Rückruf zum Auslösen der Suche. Standardwert ist `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Nummer | Timeout, bevor searchCallback ausgelöst wird. Der Standardwert ist 800 ms. |

## Suchergebnisse anpassen {#customizing-search-results}

Die Darstellung von Suchergebnissen in einer Asset-Freigaben-Seite wird durch die ausgewählte Linse geregelt. AEM Assets umfasst einen Satz vordefinierter Linsen, mit denen Sie eine Asset-Freigaben-Seite anpassen können. Diese Art der Anpassung einer Asset-Freigabe wird unter [Erstellen und Konfigurieren einer Asset-Freigaben-Seite](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page) beschrieben.

Zusätzlich zu den bereits vorhandenen Linsen können AEM-Entwickler auch eigene Linsen erstellen.
