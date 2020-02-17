---
title: Tag-Bibliotheken
seo-title: Tag-Bibliotheken
description: Die Tag-Bibliotheken von Granite, CQ und Sling verleihen Ihnen Zugriff auf spezifische Funktionen für die Verwendung im JSP-Skript der Vorlagen und Komponenten
seo-description: Die Tag-Bibliotheken von Granite, CQ und Sling verleihen Ihnen Zugriff auf spezifische Funktionen für die Verwendung im JSP-Skript der Vorlagen und Komponenten
uuid: e622d47b-cfb3-4b4a-b8e3-e1adee294219
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6678e3c3-fb0f-4300-8838-38f23f14db07
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Tag-Bibliotheken{#tag-libraries}

Die Tag-Bibliotheken von Granite, CQ und Sling verleihen Ihnen Zugriff auf spezifische Funktionen für die Verwendung im JSP-Skript der Vorlagen und Komponenten.

## Die Tag-Bibliothek von Granite {#granite-tag-library}

Die Tag-Bibliothek von Granite enthält hilfreiche Funktionen.

Bei der Entwicklung des JSP-Skripts einer Granite-UI-Komponente empfiehlt es sich, den folgenden Code oben im Skript einzufügen:

```xml
<%@include file="/libs/granite/ui/global.jsp"%>
```

Das globale Objekt deklariert zudem die [Sling-Bibliothek](/help/sites-developing/taglib.md#sling-tag-library).

```xml
<%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling" %>
```

### <ui:includeClientLib> {#ui-includeclientlib}

The `<ui:includeClientLib>` tag Includes a AEM html client library, which can be a js, a css, or a theme library. Für mehrere Inklusionen verschiedener Typen, z. B. js und css, muss dieses Tag mehrmals in der jsp-Datei verwendet werden. Dieses Tag ist ein praktischer Wrapper für die Dienstschnittstelle ` [com.adobe.granite.ui.clientlibs.HtmlLibraryManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/ui/clientlibs/HtmlLibraryManager.html)`.

Es weist folgende Attribute auf:

**categories** - Eine Liste der durch Kommas getrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Dateien und CSS-Bibliotheken für die betreffenden Kategorien mit ein. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeIncludes`

**theme** - Eine Liste von durch Kommas getrennten Client-Bibliothekskategorien. Dies beinhaltet alle designbezogenen Bibliotheken (CSS und JS) für die entsprechenden Kategorien. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeThemeInclude`

**js** - Eine Liste von durch Kommas getrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Bibliotheken für die betreffenden Kategorien mit ein.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeJsInclude`

**css** - Eine Liste mit durch Kommas getrennten Client-Bibliothekskategorien. Dies bezieht alle CSS-Bibliotheken für die betreffenden Kategorien mit ein.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeCssInclude`

**themed** - Ein Flag, das nur die Bibliotheken mit oder ohne Designs anzeigt, sollte einbezogen werden. Wenn ausgelassen, sind beide Sätze enthalten. Gilt nur, wenn nur JS oder nur CSS enthalten ist (nicht wenn Kategorien oder Designs enthalten sind).

The `<ui:includeClientLib>` tag can be used as follows in a jsp:

```xml
<%-- all: js + theme (theme-js + css) --%>
<ui:includeClientLib categories="cq.wcm.edit" />

<%-- only js libs --%>
<ui:includeClientLib js="cq.collab.calendar, cq.security" />

<%-- theme only (theme-js + css) --%>
<ui:includeClientLib theme="cq.collab.calendar, cq.security" />

<%-- css only --%>
<ui:includeClientLib css="cq.collab.calendar, cq.security" />
```

## Tag-Bibliothek von CQ {#cq-tag-library}

Die Tag-Bibliothek von CQ enthält hilfreiche Funktionen.

Das Skript muss mit dem folgenden Code beginnen, damit Sie die Tag-Bibliothek von CQ im Skript verwenden können:

```xml
<%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %>
```

>[!NOTE]
>
>When the `/libs/foundation/global.jsp` file is included in the script, the taglib is automatically declared.

Wenn Sie das JSP-Skript einer AEM-Komponente entwickeln, sollten Sie folgenden Code am Anfang des Skripts einfügen:

```xml
<%@include file="/libs/foundation/global.jsp"%>
```

It declares the sling, CQ, and jstl taglibs and exposes the regularly used scripting objects defined by the [ `<cq:defineObjects />`](#amp-lt-cq-defineobjects) tag. Dies verkürzt und vereinfacht den JSP-Code der Komponente.

### <cq:text> {#cq-text}

The `<cq:text>` tag is a convenience tag that outputs component text in a JSP.

Es weist die folgenden optionalen Attribute auf:

**property** - Name der zu verwendenden Eigenschaft. Der Name steht im Bezug zur aktuellen Ressource.

**value** - Wert, der für die Ausgabe verwendet wird. Falls dieses Attribut vorhanden ist, wird die Nutzung des Attributs property außer Kraft gesetzt.

**oldValue** - Wert, der für die Diff-Ausgabe verwendet wird. Falls dieses Attribut vorhanden ist, wird die Nutzung des Attributs property außer Kraft gesetzt.

**escapeXml** - Definiert, ob die Zeichen &lt;, >, &amp;, &#39; und &quot; in der resultierenden Zeichenfolge in die entsprechenden Zeichenentitäts-Codes konvertiert werden sollen. Der Standardwert lautet false. Beachten Sie, dass der Escapevorgang nach der optionalen Formatierung angewendet wird.

**format** - Optionales java.text.Format für die Formatierung des Textes.

**noDiff** - Unterdrückt die Berechnung einer Diff-Ausgabe, auch wenn eine Diff-Info vorhanden ist.

**tagClass** - CSS-Klassenname eines Elements, das eine nicht leere Ausgabe umgibt. Wenn leer, wird kein Element hinzugefügt.

**tagName** - Name des Elements, das eine nicht leere Ausgabe umgibt. Standardmäßig ist DIV eingestellt.

**placeholder** - Standardwert, der im Bearbeitungsmodus für null oder leeren Text, d. h. den Platzhalter, verwendet wird. Beachten Sie, dass nach der optionalen Formatierung und dem Escapevorgang die standardmäßige Prüfung ausgeführt wird, d. h. er wird im vorliegenden Format in die Ausgabe geschrieben. Standardwert ist:

`<div><span class="cq-text-placeholder">&para;</span></div>`

**default** - Standardwert für null oder leeren Text. Beachten Sie, dass nach der optionalen Formatierung und dem Escapevorgang die standardmäßige Prüfung ausgeführt wird, d. h. er wird im vorliegenden Format in die Ausgabe geschrieben.

Some examples how the `<cq:text>` tag can be used in a JSP:

```xml
<cq:text property="jcr:title" tagName="h2"/>
<cq:text property="jcr:description" tagName="p"/>

<cq:text value="<%= listItem.getTitle() %>" tagName="h4" placeholder="" />
<cq:text value="<%= listItem.getDescription() %>" tagName="p" placeholder=""/>

<cq:text property="jcr:title" value="<%= title %>" tagName="h3"/><%
    } else if (type.equals("link")) {
        %><cq:text property="jcr:title" value="<%= "\u00bb " + title %>" tagName="p" tagClass="link"/><%
    } else if (type.equals("extralarge")) {
        %><cq:text property="jcr:title" value="<%= title %>" tagName="h1"/><%
    } else {
        %><cq:text property="jcr:title" value="<%= title %>" tagName="h2"/><%

<cq:text property="jcr:description" placeholder="" tagName="small"/>

<cq:text property="tableData"
               escapeXml="false"
               placeholder="<img src=\"/libs/cq/ui/resources/0.gif\" class=\"cq-table-placeholder\" alt=\"\">"
    />

<cq:text property="text"/>

<cq:text property="image/jcr:description" placeholder="" tagName="small"/>
<cq:text property="text" tagClass="text"/>
```

### <cq:setContentBundle> {#cq-setcontentbundle}

The `<cq:setContentBundle>` tag creates an i18n localization context and stores it in the `javax.servlet.jsp.jstl.fmt.localizationContext` configuration variable.

Es weist folgende Attribute auf:

**language** - Die Sprache des Gebietsschemas, für das das Ressourcen-Bundle abgerufen werden soll.

**source** - Die Quelle, aus der das Gebietsschema entnommen werden soll. Sie können sie auf einen der folgenden Werte einstellen:

* **static** - das Gebietsschema wird, falls verfügbar, aus dem `language` Attribut übernommen, andernfalls aus dem Standardgebietsschema des Servers.

* **page** : Das Gebietsschema wird aus der Sprache der aktuellen Seite oder Ressource, sofern verfügbar, entfernt. Andernfalls wird das `language` Attribut, falls verfügbar, aus dem Standardgebietsschema des Servers übernommen.

* **request** - Das Gebietsschema wird vom Anforderungsgebietsschema ( `request.getLocale()`) übernommen.

* **auto** : Das Gebietsschema wird aus dem `language` Attribut entnommen, falls verfügbar, andernfalls aus der Sprache der aktuellen Seite oder Ressource, falls verfügbar, aus der Anforderung.

Falls das `source`-Attribut nicht festgelegt ist:

* If the `language` attribute is set, the `source` attribute defaults to `` `static`.

* If the `language` attribute is not set, the `source` attribute defaults to `auto`.

The &quot;content bundle&quot; can be simply used by standard JSTL `<fmt:message>` tags. Die Suche von Nachrichten anhand von Schlüsselwörtern hat zwei Aspekte:

1. Zunächst werden die JCR-Eigenschaften der zugrunde liegenden Ressource, die derzeit wiedergegeben wird, nach Übersetzungen durchsucht. Auf diese Weise können Sie ein einfaches Komponentendialogfeld definieren, um diese Werte zu bearbeiten.
1. Wenn der Knoten keine Eigenschaft mit dem exakt gleichen Namen wie das Schlüsselwort enthält, wird ein Ressourcenpaket aus der Sling-Anforderung (`SlingHttpServletRequest.getResourceBundle(Locale)`) )) geladen. The language or locale for this bundle is defined by the language and source attributes of the `<cq:setContentBundle>` tag.

The `<cq:setContentBundle>` tag can be used as follows in a jsp.

Für Seiten, die ihre Sprache definieren:

```xml
... %><cq:setContentBundle source="page"/><%  %>
<div class="error"><fmt:message key="Hello"/>
</div> ...
```

Für von Benutzern personalisierte Seiten:

```xml
... %><cq:setContentBundle scope="request"/><% %>
<div class="error"><fmt:message key="Hello"/>
</div> ...
```

### <cq:include> {#cq-include}

The `<cq:include>` tag includes a resource into the current page.

Es weist folgende Attribute auf:

**flush**

* Ein boolescher Wert, der definiert, ob die Ausgabe geleert werden soll, bevor das Ziel eingefügt wird.

**path**

* Der Pfad zum Ressourcenobjekt, das in die aktuelle Anforderungsverarbeitung eingefügt werden soll. Ein relativer Pfad wird an den Pfad der aktuellen Ressource angehängt, deren Skript die angegebene Ressource enthält. path und resourceType oder script müssen angegeben sein.

**resourceType**

* Der Ressourcentypen der Ressource, die hinzugefügt werden soll. Wenn der Ressourcentyp festgelegt ist, muss der Pfad der genaue Pfad zu einem Ressourcenobjekt sein: in diesem Fall wird das Hinzufügen von Parametern, Selektoren und Erweiterungen zum Pfad nicht unterstützt.
* Falls die einzufügende Ressource mit dem path-Attribut angegeben ist, das nicht in eine Ressource aufgelöst werden kann, erstellt das Tag möglicherweise ein synthetisches Ressourcenobjekt aus dem Pfad und diesem Ressourcentyp.
* path und resourceType oder script müssen angegeben sein.

**script**

* Das JSP-Skript, das einbezogen werden soll. path und resourceType oder script müssen angegeben sein.

**ignoreComponentHierarchy**

* Eine boolesches Element, das steuert, ob die Komponentenhierarchie für die Skriptauflösung ignoriert werden soll. Bei „true“ werden nur die Suchpfade berücksichtigt.

**Beispiel:**

```xml
<%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
%><div class="center">
    <cq:include path="trail" resourceType="foundation/components/breadcrumb" />
    <cq:include path="title" resourceType="foundation/components/title" />
    <cq:include script="redirect.jsp"/>
    <cq:include path="par" resourceType="foundation/components/parsys" />
</div>
```

Should you use `<%@ include file="myScript.jsp" %>` or `<cq:include script="myScript.jsp" %>` to include a script?

* The `<%@ include file="myScript.jsp" %>` directive informs the JSP compiler to include a complete file into the current file. Es ist, als ob die Inhalte der enthaltenen Datei direkt in die Originaldatei eingefügt würden.
* With the `<cq:include script="myScript.jsp">` tag, the file is included at runtime.

Should you use `<cq:include>` or `<sling:include>`?

* Bei der Entwicklung von AEM-Komponenten empfiehlt Adobe die Verwendung von `<cq:include>`.
* `<cq:include>` ermöglicht das direkte Einfügen von Skriptdateien anhand ihres Namens, wenn Sie das script-Attribut verwenden. Dabei werden Komponenten- und Ressourcentypvererbung berücksichtigt. Diese ist häufig einfacher als die strikte Einhaltung der Skriptauflösung von Sling mithilfe von Selektoren und Erweiterungen.

### <cq:includeClientLib> {#cq-includeclientlib}

>[!CAUTION]
>
>`<cq:includeClientLib>` ist seit AEM 5.6 veraltet. Stattdessen [ `<ui:includeClientLib>`](/help/sites-developing/taglib.md#ui-includeclientlib) sollte es verwendet werden.

The `<cq:includeClientLib>` tag Includes a AEM html client library, which can be a js, a css or a theme library. Für mehrere Inklusionen verschiedener Typen, z. B. js und css, muss dieses Tag mehrmals in der jsp-Datei verwendet werden. Dieses Tag ist ein praktischer Wrapper für die Dienstschnittstelle `com.day.cq.widget.HtmlLibraryManager`.

Es weist folgende Attribute auf:

**categories** - Eine Liste der durch Kommas getrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Dateien und CSS-Bibliotheken für die betreffenden Kategorien mit ein. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeIncludes`

**theme** - Eine Liste von durch Kommas getrennten Client-Bibliothekskategorien. Dies beinhaltet alle designbezogenen Bibliotheken (CSS und JS) für die entsprechenden Kategorien. Der Designname wird aus der Abfrage extrahiert.

Equivalent to: `com.day.cq.widget.HtmlLibraryManager#`writeThemeInclude

**js** - Eine Liste von durch Kommas getrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Bibliotheken für die betreffenden Kategorien mit ein.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeJsInclude`

**css** - Eine Liste mit durch Kommas getrennten Client-Bibliothekskategorien. Dies bezieht alle CSS-Bibliotheken für die betreffenden Kategorien mit ein.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeCssInclude`

**themed** - Ein Flag, das nur die Bibliotheken mit oder ohne Designs anzeigt, sollte einbezogen werden. Wenn ausgelassen, sind beide Sätze enthalten. Gilt nur, wenn nur JS oder nur CSS enthalten ist (nicht wenn Kategorien oder Designs enthalten sind).

The `<cq:includeClientLib>` tag can be used as follows in a jsp:

```xml
<%-- all: js + theme (theme-js + css) --%>
<cq:includeClientLib categories="cq.wcm.edit" />

<%-- only js libs --%>
<cq:includeClientLib js="cq.collab.calendar, cq.security" />

<%-- theme only (theme-js + css) --%>
<cq:includeClientLib theme="cq.collab.calendar, cq.security" />

<%-- css only --%>
<cq:includeClientLib css="cq.collab.calendar, cq.security" />
```

### <cq:defineObjects> {#cq-defineobjects}

The `<cq:defineObjects>` tag exposes the following, regularly used, scripting objects which can be referenced by the developer. It also exposes the objects defined by the [ `<sling:defineObjects>`](#amp-lt-sling-defineobjects) tag.

**componentContext**

* das aktuelle Komponentenkontextobjekt der Anfrage (com.day.cq.wcm.api.components.ComponentContext-Schnittstelle).

**component**

* das aktuelle AEM-Komponentenobjekt der aktuellen Ressource (com.day.cq.wcm.api.components.Component-Schnittstelle).

**currentDesign**

* das aktuelle Entwurfsobjekt der aktuellen Seite (com.day.cq.wcm.api.designer.Design-Schnittstelle).

**currentPage**

* das aktuelle AEM WCM-Seitenobjekt (com.day.cq.wcm.api.Page-Schnittstelle).

**currentStyle**

* das aktuelle Stilobjekt der aktuellen Zelle (com.day.cq.wcm.api.designer.Style-Schnittstelle).

**designer**

* das designer-Objekt für den Zugriff auf Entwurfsinformationen (com.day.cq.wcm.api.designer.Designer-Schnittstelle).

**editContext**

* das Bearbeitungskontext-Objekt der AEM-Komponente (com.day.cq.wcm.api.components.EditContext-Schnittstelle).

**pageManager**

* das Seitenmanager-Objekt für Vorgänge auf Seitenebene (com.day.cq.wcm.api.PageManager-Schnittstelle).

**pageProperties**

* das Seiteneigenschaftenobjekt der aktuellen Seite (org.apache.sling.api.resource.ValueMap).

**properties**

* das Eigenschaftenobjekt der aktuellen Ressource (org.apache.sling.api.resource.ValueMap).

**resourceDesign**

* das Entwurfsobjekt der Ressourcenseite (com.day.cq.wcm.api.designer.Design-Schnittstelle).

**resourcePage**

* das Ressourcenseitenobjekt (com.day.cq.wcm.api.Page-Schnittstelle).
* Es weist folgende Attribute auf:

**requestName**

* von Sling geerbt

**responseName**

* von Sling geerbt

**resourceName**

* von Sling geerbt

**nodeName**

* von Sling geerbt

**logName**

* von Sling geerbt

**resourceResolverName**

* von Sling geerbt

**slingName**

* von Sling geerbt

**componentContextName**

* spezifisch für wcm

**editContextName**

* spezifisch für wcm

**propertiesName**

* spezifisch für wcm

**pageManagerName**

* spezifisch für wcm

**currentPageName**

* spezifisch für wcm

**resourcePageName**

* spezifisch für wcm

**pagePropertiesName**

* spezifisch für wcm

**componentName**

* spezifisch für wcm

**designerName**

* spezifisch für wcm

**currentDesignName**

* spezifisch für wcm

**resourceDesignName**

* spezifisch für wcm

**currentStyleName**

* spezifisch für wcm

**Beispiel**

```xml
<%@page session="false" contentType="text/html; charset=utf-8" %><%
%><%@ page import="com.day.cq.wcm.api.WCMMode" %><%
%><%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
%><cq:defineObjects/>
```

>[!NOTE]
>
>When the `/libs/foundation/global.jsp` file is included in the script, the `<cq:defineObjects />` tag is automatically included.

### <cq:requestURL> {#cq-requesturl}

The `<cq:requestURL>` tag writes the current request URL to the JspWriter. The two tags [ `<cq:addParam>`](#amp-lt-cq-addparam) and [ `<cq:removeParam>`](#amp-lt-cq-removeparam) and may be used inside the body of this tag to modify the current request URL before it is written.

Sie können Links zur aktuellen Seite mit variierenden Parametern erstellen. Beispielsweise können Sie die Anforderung umwandeln:

`mypage.html?mode=view&query=something` in `mypage.html?query=something`.

The use of `addParam` or `removeParam` only changes the occurrence of the given parameter, all other parameters are unaffected.

`<cq:requestURL>` hat kein Attribut.

Beispiele:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### <cq:addParam> {#cq-addparam}

The `<cq:addParam>` tag adds a request parameter with the given name and value to the enclosing [ `<cq:requestURL>`](#amp-lt-cq-requesturl) tag.

Es weist folgende Attribute auf:

**name**

* Name des Parameters, der hinzugefügt werden soll

**value**

* Wert des Parameters, der hinzugefügt werden soll

**Beispiel:**

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### <cq:removeParam> {#cq-removeparam}

The `<cq:removeParam>` tag removes a request parameter with the given name and value from the enclosing [ `<cq:requestURL>`](#amp-lt-cq-requesturl) tag. Wenn kein Wert angegeben wird, werden alle Parameter mit dem jeweiligen Namen entfernt.

Es weist folgende Attribute auf:

**name**

* Name des Parameters, der entfernt werden soll

Beispiel:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

## Tag-Bibliothek von Sling {#sling-tag-library}

Die Tag-Bibliothek von Sling enthält hilfreiche Sling-Funktionen.

Wenn Sie die Tag-Bibliothek von Sling in Ihrem Skript verwenden, muss das Skript mit dem folgenden Code beginnen:

```xml
<%@ taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %>
```

>[!NOTE]
>
>When the `/libs/foundation/global.jsp` file is included in the script, the sling taglib is automatically declared.

### <sling:include> {#sling-include}

The `<sling:include>` tag includes a resource into the current page.

Es weist folgende Attribute auf:

**flush**

* Ein boolescher Wert, der definiert, ob die Ausgabe geleert werden soll, bevor das Ziel eingefügt wird.

**Ressource**

* Das Ressourcenobjekt, das in die aktuelle Anforderungsverarbeitung eingefügt werden soll. resource oder path muss angegeben werden. Wenn beide angegeben sind, hat resource Vorrang.

**path**

* Der Pfad zum Ressourcenobjekt, das in die aktuelle Anforderungsverarbeitung eingefügt werden soll. Ein relativer Pfad wird an den Pfad der aktuellen Ressource angehängt, deren Skript die angegebene Ressource enthält. resource oder path muss angegeben werden. Wenn beide angegeben sind, hat resource Vorrang.

**resourceType**

* Der Ressourcentypen der Ressource, die hinzugefügt werden soll. Wenn der Ressourcentyp festgelegt ist, muss der Pfad der genaue Pfad zu einem Ressourcenobjekt sein: in diesem Fall wird das Hinzufügen von Parametern, Selektoren und Erweiterungen zum Pfad nicht unterstützt.
* Falls die einzufügende Ressource mit dem path-Attribut angegeben ist, das nicht in eine Ressource aufgelöst werden kann, erstellt das Tag möglicherweise ein synthetisches Ressourcenobjekt aus dem Pfad und diesem Ressourcentyp.

**replaceSelectors**

* Beim Versenden werden die Selektoren durch den Wert dieses Attributs ersetzt.

**addSelectors**

* Beim Versenden wird der Wert dieses Attributs den Selektoren hinzugefügt.

**replaceSuffix**

* Beim Versenden wird das Suffix durch den Wert dieses Attributs ersetzt.

>[!NOTE]
>
>The resolution of the resource and the script that are included with the `<sling:include>` tag is the same as for a normal sling URL resolution. Standardmäßig werden die Selektoren, die Erweiterung usw. der aktuellen Anforderung auch für das enthaltene Skript verwendet. They can be modified through the tag attributes: for example `replaceSelectors="foo.bar"` allows you to overwrite the selectors.

Beispiele:

```xml
<div class="item"><sling:include path="<%= pathtoinclude %>"/></div>
```

```xml
<sling:include resource="<%= par %>"/>
```

```xml
<sling:include addSelectors="spool"/>
```

```xml
<sling:include resource="<%= par %>" resourceType="<%= newType %>"/>
```

```xml
<sling:include resource="<%= par %>" resourceType="<%= newType %>"/>
```

```xml
<sling:include replaceSelectors="content" />
```

### <sling:defineObjects> {#sling-defineobjects}

The `<sling:defineObjects>` tag exposes the following, regularly used, scripting objects which can be referenced by the developer:

**slingRequest**

* SlingHttpServletRequest-Objekt, bietet Zugriff auf die Informationen der HTTP-Anforderungskopfzeile – erweitert die standardmäßige HttpServletRequest – und auf Sling-spezifische Dinge wie Ressource, Pfadinformationen, Selektor usw.

**slingResponse**

* SlingHttpServletResponse-Objekt, bietet Zugriff für die HTTP-Antwort, die vom Server erstellt wird. Dies ist derzeit dieselbe wie die HttpServletResponse, von der aus sie erweitert wird.**request**
* das Standard-JSP-Anforderungsobjekt, bei dem es sich um eine reine HttpServletRequest handelt.**response**
* das Standard-JSP-Antwortobjekt, bei dem es sich um ein reines HttpServletResponse-Objekt handelt.

**resourceResolver**

* das aktuelle ResourceResolver-Objekt. Entspricht slingRequest.getResourceResolver()

.**sling**

* ein SlingScriptHelper-Objekt, das komfortable Methoden für Skripte enthält, hauptsächlich sling.include(&#39;/some/other/resource&#39;) zum Einfügen der Antworten anderer Ressourcen innerhalb dieser Antwort (z. B. Einbetten von Kopfzeilen-HTML-Snippets) und sling.getService(foo.bar.Service.class) zum Abrufen der verfügbaren OSGi-Dienste in Sling (Klassennotation abhängig von Skriptingsprache).

**Ressource**

* das derzeit zu bearbeitende Ressourcenobjekt, abhängig von der URL der Anforderung. Entspricht slingRequest.getResource().

**currentNode**

* Falls die aktuelle Ressource auf einen JCR-Knoten verweist (was in der Regel bei Sling der Fall ist), verleiht dies dem Knotenobjekt direkten Zugriff. Andernfalls ist dieses Objekt nicht definiert.

**log**

* Stellt einen SLF4J Logger zum Protokollieren des Sling-Protokollsystems in Skripten bereit, z. B. log.info(&quot;Executing my script&quot;).

* Es weist folgende Attribute auf:

**requestName**

**responseName**

**nodeName**

l **ogName resourceResolverName**

**slingName**

**Beispiel:**

```xml
<%@page session="false" %><%
%><%@page import="com.day.cq.wcm.foundation.forms.ValidationHelper"%><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/>
```

## Tag-Bibliothek von JSTL {#jstl-tag-library}

The [JavaServer Pages Standard Tag Library](https://www.oracle.com/technetwork/java/index-jsp-135995.html) contains a lot of useful and standard tags. The core, formatting and functions taglibs are defined by the `/libs/foundation/global.jsp` as shown in the following snippet.

### Auszug aus /libs/foundation/global.jsp {#extract-of-libs-foundation-global-jsp}

```xml
<%@taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
<%@taglib prefix="fmt" uri="https://java.sun.com/jsp/jstl/fmt" %>
<%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions" %>
```

After importing the `/libs/foundation/global.jsp` file as described before, you can use the `c`, `fmt` and `fn` prefixes to access to those taglibs. Die offizielle Dokumentation der JSTL ist verfügbar unter [Das Java EE 5-Tutorial – standardmäßige Tag-Bibliothek JavaServer-Seiten](https://docs.oracle.com/javaee/5/tutorial/doc/bnakc.html).
