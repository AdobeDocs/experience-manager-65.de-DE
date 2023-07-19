---
title: Erweitern der Suchfunktion
description: Erweitern Sie die Suchfunktionen von  [!DNL Adobe Experience Manager Assets]  über die Standardwerte hinaus.
contentOwner: AG
role: Developer
feature: Search
exl-id: 9e33d1c0-232b-458a-ad6a-f595aa541a5a
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 88%

---

# Erweitern der Asset-Suche {#extending-assets-search}

Sie können die Suchfunktionen von [!DNL Adobe Experience Manager Assets] erweitern. Standardmäßig sucht [!DNL Experience Manager Assets] anhand von Zeichenfolgen nach Assets.

Die Suchfunktion wird über die QueryBuilder-Schnittstelle durchgeführt und lässt sich mit mehreren Eigenschaften anpassen. Sie können den Standardsatz der Eigenschaften im folgenden Verzeichnis überlagern: `/apps/dam/content/search/searchpanel/facets`.

Sie können dem Admin-Bedienfeld von [!DNL Assets] auch zusätzliche Registerkarten hinzufügen.

>[!CAUTION]
>
>Seit Einführung von [!DNL Experience Manager] 6.4 ist die klassische Benutzeroberfläche veraltet. Adobe empfiehlt die Verwendung der Touch-optimierten Benutzeroberfläche. Informationen zur Anpassung finden Sie unter [Suchfacetten](/help/assets/search-facets.md).

## Überlagerung {#overlaying}

Um die vorkonfigurierten Eigenschaften zu überlagern, kopieren Sie den `facets`-Knoten aus `/libs/dam/content/search/searchpanel` nach `/apps/dam/content/search/searchpanel/` oder geben Sie  eine weitere `facetURL`-Eigenschaft in `searchpanel` der Konfiguration des Suchfensters an (standardmäßig `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>Standardmäßig ist die Verzeichnisstruktur unter `/apps` nicht vorhanden und muss erstellt werden. Stellen Sie sicher, dass die Knotentypen den Typen unter `/libs` entsprechen.

## Hinzufügen von Registerkarten {#adding-tabs}

Sie können zusätzliche Suchregisterkarten hinzufügen, indem Sie sie in der Admin-Benutzeroberfläche von [!DNL Assets] konfigurieren. So erstellen Sie weitere Registerkarten:

1. Erstellen Sie die Ordnerstruktur `/apps/wcm/core/content/damadmin/tabs,`, falls noch nicht vorhanden, kopieren Sie den Knoten `tabs` aus `/libs/wcm/core/content/damadmin` und fügen Sie ihn ein.
1. Erstellen und konfigurieren Sie die zweite Registerkarte wie gewünscht.

   >[!NOTE]
   >
   >Achten Sie bei Erstellung eines zweiten `siteadminsearchpanel` auf die Festlegung einer `id`-Eigenschaft, um Formularkonflikte zu vermeiden.

## Erstellen benutzerdefinierter Eigenschaften {#creating-custom-predicates}

[!DNL Assets] umfasst einen Satz vordefinierter Eigenschaften, mit denen eine Asset-Freigaben-Seite angepasst werden kann. Das Anpassen einer Asset-Freigabe auf diese Weise wird unter [Erstellen und Konfigurieren einer Asset-Freigaben-Seite](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page) beschrieben.

[!DNL Experience Manager]-Entwicklerinnen und -Entwickler können neben den bereits vorhandenen Prädikaten auch eigene Prädikate erstellen. Hierfür können sie die [QueryBuilder-API](/help/sites-developing/querybuilder-api.md) verwenden.

Um benutzerdefinierte Eigenschaften erstellen zu können, benötigen Sie Grundlagenkenntnisse über das [Widget-Framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?lang=de).

Es empfiehlt sich, ein vorhandenes Prädikat zu kopieren und anzupassen. Beispielprädikate finden Sie unter **/libs/cq/search/components/predicates**.

### Beispiel: Einfaches Eigenschaftsprädikat erstellen   {#example-build-a-simple-property-predicate}

So erstellen Sie ein Eigenschaftsprädikat:

1. Erstellen Sie einen Komponentenordner in Ihrem Projektverzeichnis, z. B.**/apps/weretail/components/titlepredicate**.
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

1. Fügen Sie `titlepredicate.jsp` hinzu.

   ```java
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

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeiten zu können, fügen Sie in CRXDE den Knoten **cq:editConfig** des primären Typs **cq:EditConfig** hinzu. Damit Sie Absätze entfernen können, fügen Sie die Eigenschaft **cq:actions** mit mehreren Werten mit dem einzelnen Wert **LÖSCHEN** hinzu.
1. Navigieren Sie zu Ihrem Browser und auf Ihrer Beispielseite (z. B. **press.html**) in den Designmodus wechseln und Ihre neue Komponente für das Prädikat-Absatzsystem aktivieren (z. B. **left**).

1. Im Modus **Bearbeiten** ist die neue Komponente jetzt im Sidekick verfügbar (in der **Suchgruppe**). Fügen Sie die Komponente in die Spalte **Eigenschaften** ein, geben Sie einen Suchbegriff – z. B. **Raute** – ein und klicken Sie auf das Lupensymbol, um die Suche zu starten.

   >[!NOTE]
   >
   >Stellen Sie beim Suchen sicher, dass der Begriff korrekt eingegeben wird und auch die Groß-/Kleinschreibung stimmt.

### Beispiel: Einfache Gruppeneigenschaft erstellen {#example-build-a-simple-group-predicate}

So erstellen Sie eine Gruppeneigenschaft:

1. Erstellen Sie einen Komponentenordner in Ihrem Projektverzeichnis, z. B. **/apps/weretail/components/picspredicate**.
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

1. Hinzufügen **titlepredicate.jsp**:

   ```java
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
   
           // Create a unique group ID; will return for example, "1_group".
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

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeiten zu können, fügen Sie in CRXDE den Knoten **cq:editConfig** des primären Typs **cq:EditConfig** hinzu. Damit Sie Absätze entfernen können, fügen Sie die Eigenschaft **cq:actions** mit mehreren Werten mit dem einzelnen Wert **LÖSCHEN** hinzu.
1. Navigieren Sie zu Ihrem Browser und auf Ihrer Beispielseite (z. B. **press.html**) in den Designmodus wechseln und Ihre neue Komponente für das Prädikat-Absatzsystem aktivieren (z. B. **left**).
1. Im Modus **Bearbeiten** ist die neue Komponente jetzt im Sidekick verfügbar (in der **Suchgruppe**). Fügen Sie die Komponente in die Spalte **Eigenschaften** ein.

## Installierte Eigenschaften-Widgets {#installed-predicate-widgets}

Die folgenden Prädikate sind als vorkonfigurierte ExtJS-Widgets verfügbar.

### FulltextPredicate   {#fulltextpredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `fulltext` |
| searchCallback | Funktion | Callback zum Auslösen der Suche bei Ereignis `keyup`. Standardwert ist `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `property` |
| propertyName | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:title` |
| defaultValue | Zeichenfolge | Vorgegebener Standardwert. |

### PathPredicate {#pathpredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `path` |
| rootPath | Zeichenfolge | Stammpfad der Eigenschaft. Standardwert ist `/content/dam` |
| pathFieldPredicateName | Zeichenfolge | Standardwert ist `folder` |
| showFlatOption | Boolesch | Markierung zum Anzeigen des Kontrollkästchen `search in subfolders`. Standardwert ist „true“. |

### DatePredicate {#datepredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `daterange` |
| propertyname | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:content/jcr:lastModified` |
| defaultValue | Zeichenfolge | Vorgegebener Standardwert |

### OptionsPredicate {#optionspredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| title | Zeichenfolge | Fügt einen zusätzlichen oberen Titel hinzu |
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `daterange` |
| propertyname | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:content/metadata/cq:tags` |
| collapse | Zeichenfolge | Ebene der Reduzierung. Standardwert ist `level1` |
| triggerSearch | Boolesch | Markierung zum Auslösen der Suche nach Aktivierung. Standardwert ist „false“ |
| searchCallback | Funktion | Callback zum Auslösen der Suche. Standardwert ist `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Nummer | Zeitlimit, nach dem searchCallback ausgelöst wird. Standardwert ist 800 ms. |

## Anpassen der Suchergebnisse {#customizing-search-results}

Die Darstellung von Suchergebnissen in einer Asset-Freigaben-Seite wird durch die ausgewählte Linse geregelt. [!DNL Experience Manager Assets] umfasst einen Satz vordefinierter Linsen, mit denen Sie eine Asset-Freigaben-Seite anpassen können. Diese Art der Anpassung einer Asset-Freigabe wird unter [Erstellen und Konfigurieren einer Asset-Freigaben-Seite](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page) beschrieben.

Zusätzlich zu den bereits vorhandenen Linsen können [!DNL Experience Manager]-Entwicklerinnen und -Entwickler auch eigene Linsen erstellen.
