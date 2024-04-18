---
title: Tag-Bibliotheken
description: Die Tag-Bibliotheken von Granite, CQ und Sling bieten Ihnen Zugriff auf bestimmte Funktionen für die Verwendung im JSP-Skript Ihrer Vorlagen und Komponenten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 50e608d5-951f-4a3f-bed4-9e92ff5d7bd4
solution: Experience Manager, Experience Manager Sites
feature: Developing,Tagging
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 96%

---

# Tag-Bibliotheken{#tag-libraries}

Die Tag-Bibliotheken von Granite, CQ und Sling bieten Ihnen Zugriff auf bestimmte Funktionen für die Verwendung im JSP-Skript Ihrer Vorlagen und Komponenten.

## Tag-Bibliothek von Granite {#granite-tag-library}

Die Tag-Bibliothek von Granite enthält hilfreiche Funktionen.

Bei der Entwicklung des JSP-Skripts einer Granite-Benutzeroberflächenkomponente empfiehlt es sich, den folgenden Code oben im Skript einzufügen:

```xml
<%@include file="/libs/granite/ui/global.jsp"%>
```

Die globale Seite deklariert zudem die [Sling-Bibliothek](/help/sites-developing/taglib.md#sling-tag-library).

```xml
<%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling" %>
```

### &lt;ui:includeClientLib> {#ui-includeclientlib}

Das Tag `<ui:includeClientLib>` enthält eine AEM-HTML-Client-Bibliothek, bei der es sich um eine JS-, CSS- oder Design-Bibliothek handeln kann. Für mehrere Einschlüsse verschiedener Typen, z. B. js und css, muss dieses Tag mehrmals in der JSP verwendet werden. Dieses Tag ist ein praktischer Wrapper für die Service-Schnittstelle ` [com.adobe.granite.ui.clientlibs.HtmlLibraryManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/ui/clientlibs/HtmlLibraryManager.html)`.

Es weist folgende Attribute auf:

**categories**: Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Dies schließt alle JavaScript-Dateien und CSS-Bibliotheken für die betreffenden Kategorien ein. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeIncludes`

**theme**: Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Dies schließt alle Design-bezogenen Bibliotheken (CSS und JS) für die betreffenden Kategorien ein. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeThemeInclude`

**js**: Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Dies schließt alle JavaScript-Bibliotheken für die betreffenden Kategorien ein.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeJsInclude`

**css**: Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Dies schließt alle CSS-Bibliotheken für die betreffenden Kategorien ein.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeCssInclude`

**themed**: Ein Flag, das angibt, ob nur designbezogene oder nicht designbezogene Bibliotheken enthalten sein sollen. Wenn ausgelassen, sind beide Sätze enthalten. Gilt nur, wenn nur JS oder nur CSS enthalten ist (nicht wenn Kategorien oder Designs enthalten sind).

Das Tag `<ui:includeClientLib>` kann in einem JSP-Code wie folgt verwendet werden:

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
>Wenn die Datei `/libs/foundation/global.jsp` im Skript enthalten ist, wird die Tag-Bibliothek automatisch deklariert.

Wenn Sie das JSP-Skript einer AEM-Komponente entwickeln, sollten Sie folgenden Code am Anfang des Skripts einfügen:

```xml
<%@include file="/libs/foundation/global.jsp"%>
```

Er deklariert die Tag-Bibliotheken Sling, CQ und JSTL und macht die regelmäßig genutzten Skriptobjekte verfügbar, die durch das Tag [`<cq:defineObjects />`](#amp-lt-cq-defineobjects) definiert sind. Dies verkürzt und vereinfacht den JSP-Code der Komponente.

### &lt;cq:text> {#cq-text}

Bei dem Tag `<cq:text>` handelt es sich um ein Hilfe-Tag, das Komponententext in JSP ausgibt.

Es weist die folgenden optionalen Attribute auf:

**property**: Name der zu verwendenden Eigenschaft. Der Name steht im Bezug zur aktuellen Ressource.

**value**: Der für die Ausgabe zu verwendende Wert. Falls dieses Attribut vorhanden ist, wird die Nutzung des Attributs „property“ außer Kraft gesetzt.

**oldValue**: Der für die diff-Ausgabe zu verwendende Wert. Falls dieses Attribut vorhanden ist, wird die Nutzung des Attributs „property“ außer Kraft gesetzt.

**escapeXml**: Definiert, ob die Zeichen &lt;, >, &amp;, &#39; und &quot; in der daraus entstehenden Zeichenfolge in ihre entsprechenden Zeichenentitäts-Codes umgewandelt werden sollen. Der Standardwert lautet „false“. Der Escape-Vorgang wird nach der optionalen Formatierung angewendet.

**format**: Optionales java.text.Format für die Formatierung des Texts.

**noDiff**: Unterdrückt die Berechnung einer diff-Ausgabe, auch wenn eine diff-Information vorhanden ist.

**tagClass**: CSS-Klassenname eines Elements, das eine nicht leere Ausgabe umgibt. Wenn leer, wird kein Element hinzugefügt.

**tagName**: Name des Elements, das eine nicht leere Ausgabe umgibt. Standardmäßig ist DIV eingestellt.

**placeholder**: Standardwert, der im Bearbeitungsmodus für null oder leeren Text verwendet wird, also der Platzhalter. Die Standardüberprüfung wird nach der optionalen Formatierung und Maskierung durchgeführt, d. h. nach dem Schreibvorgang wird sie unverändert in die Ausgabe geschrieben. Standardwert ist:

`<div><span class="cq-text-placeholder">&para;</span></div>`

**default**: Zu verwendender Standardwert für null oder leeren Text. Die standardmäßige Prüfung wird nach der optionalen Formatierung und dem Escape-Vorgang ausgeführt, d. h., er wird im vorliegenden Format in die Ausgabe geschrieben.

Beispiele einer möglichen Verwendung des Tags `<cq:text>` in JSP:

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

### &lt;cq:setContentBundle> {#cq-setcontentbundle}

Das Tag `<cq:setContentBundle>` erstellt einen i18n-Lokalisierungskontext und speichert ihn in der Konfigurationsvariablen `javax.servlet.jsp.jstl.fmt.localizationContext`.

Es weist folgende Attribute auf:

**language**: Die Sprache des Gebietsschemas, für das das Ressourcenpaket abgerufen werden soll.

**source**: Die Quelle, aus der das Gebietsschema übernommen werden soll. Sie können sie auf einen der folgenden Werte einstellen:

* **static**: Das Gebietsschema wird vom Attribut `language` übernommen, falls verfügbar, andernfalls vom standardmäßigen Server-Gebietsschema.

* **page**: Das Gebietsschema wird von der Sprache der aktuellen Seite oder Ressource übernommen, falls verfügbar, andernfalls vom Attribut `language`, falls verfügbar, oder andernfalls vom standardmäßigen Server-Gebietsschema.

* **request**: Das Gebietsschema wird vom angeforderten Gebietsschema (`request.getLocale()`) übernommen.

* **auto**: Das Gebietsschema wird vom Attribut `language` übernommen, falls verfügbar, andernfalls von der Sprache der aktuellen Seite oder Ressource, falls verfügbar, andernfalls von der Anfrage.

Falls das Attribut `source` nicht festgelegt ist:

* Falls das Attribut `language` festgelegt ist, ist für das Attribut `source` standardmäßig `static` eingestellt.

* Falls das Attribut `language` nicht festgelegt ist, ist für das Attribut `source` standardmäßig `auto` eingestellt.

Das „Inhaltspaket“ kann mit standardmäßigen `<fmt:message>`-JSTL-Tags verwendet werden. Die Suche von Nachrichten anhand von Schlüsseln hat zwei Aspekte:

1. Zunächst werden die JCR-Eigenschaften der zugrunde liegenden Ressource, die gerendert wird, nach Übersetzungen durchsucht. Auf diese Weise können Sie ein einfaches Komponentendialogfeld definieren, um diese Werte zu bearbeiten.
1. Wenn der Knoten keine Eigenschaft mit dem exakt gleichen Namen wie das Schlüsselwort enthält, wird ein Ressourcenpaket aus der Sling-Anforderung (`SlingHttpServletRequest.getResourceBundle(Locale)`) geladen. Die Sprache oder das Gebietsschema für dieses Paket wird von den Sprach- und Quellattributen des Tags `<cq:setContentBundle>` definiert.

Das Tag `<cq:setContentBundle>` kann in einem JSP-Code wie folgt verwendet werden.

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

### &lt;cq:include> {#cq-include}

Das Tag `<cq:include>` fügt eine Ressource in die aktuelle Seite ein.

Es weist folgende Attribute auf:

**flush**

* Ein boolescher Wert, der definiert, ob die Ausgabe geleert werden soll, bevor das Ziel eingeschlossen wird.

**path**

* Der Pfad zum Ressourcenobjekt, das in die aktuelle Anfrageverarbeitung eingeschlossen werden soll. Ein relativer Pfad wird an den Pfad der aktuellen Ressource angehängt, deren Skript die angegebene Ressource einschließt. „path“ und „resourceType“ oder „script“ müssen angegeben werden.

**resourceType**

* Der Ressourcentyp der einzuschließenden Ressource. Wenn der Ressourcentyp festgelegt ist, muss es sich bei dem Pfad um den genauen Pfad zu einem Ressourcenobjekt handeln: In diesem Fall wird das Hinzufügen von Parametern, Selektoren und Erweiterungen zum Pfad nicht unterstützt.
* Falls die einzuschließende Ressource mit dem path-Attribut angegeben ist, das nicht in eine Ressource aufgelöst werden kann, erstellt das Tag möglicherweise ein synthetisches Ressourcenobjekt aus dem Pfad und diesem Ressourcentyp.
* „path“ und „resourceType“ oder „script“ müssen angegeben sein.

**script**

* Das einzuschließende JSP-Skript. „path“ und „resourceType“ oder „script“ müssen angegeben sein.

**ignoreComponentHierarchy**

* Dieser boolesche Wert legt fest, ob die Komponentenhierarchie bei der Skriptauflösung ignoriert werden soll. Bei „true“ werden nur die Suchpfade berücksichtigt.

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

Verwenden Sie `<%@ include file="myScript.jsp" %>` oder `<cq:include script="myScript.jsp" %>`, um ein Skript einzufügen?

* Die Richtlinie `<%@ include file="myScript.jsp" %>` informiert den JSP-Compiler, dass er eine vollständige Datei in die aktuelle Datei einfügen soll. Es ist, als ob die Inhalte der enthaltenen Datei direkt in die Originaldatei eingefügt würden.
* Mit dem Tag `<cq:include script="myScript.jsp">` wird die Datei zur Laufzeit eingebunden.

Sollten Sie `<cq:include>` oder `<sling:include>` verwenden?

* Bei der Entwicklung von AEM-Komponenten empfiehlt Adobe die Verwendung von `<cq:include>`.
* `<cq:include>` ermöglicht das direkte Einfügen von Skriptdateien anhand ihres Namens, wenn Sie das Script-Attribut verwenden. Dabei werden Komponenten- und Ressourcentypvererbung berücksichtigt. Diese ist häufig einfacher als die strikte Einhaltung der Skriptauflösung von Sling mithilfe von Selektoren und Erweiterungen.

### &lt;cq:includeClientLib> {#cq-includeclientlib}

>[!CAUTION]
>
>`<cq:includeClientLib>` ist seit AEM 5.6 veraltet. Stattdessen sollte [`<ui:includeClientLib>`](/help/sites-developing/taglib.md#ui-includeclientlib) verwendet werden.

Das Tag `<cq:includeClientLib>` enthält eine AEM-HTML-Client-Bibliothek, bei der es sich um eine JS-, CSS- oder Design-Bibliothek handeln kann. Für mehrere Einschlüsse verschiedener Typen, z. B. js und css, muss dieses Tag mehrmals in der JSP verwendet werden. Dieses Tag ist ein praktischer Wrapper für die Service-Schnittstelle `com.day.cq.widget.HtmlLibraryManager`.

Es weist folgende Attribute auf:

**categories**: Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Dies schließt alle JavaScript-Dateien und CSS-Bibliotheken für die betreffenden Kategorien ein. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeIncludes`

**theme**: Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Dies schließt alle Design-bezogenen Bibliotheken (CSS und JS) für die betreffenden Kategorien ein. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#`writeThemeInclude

**js**: Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Dies schließt alle JavaScript-Bibliotheken für die betreffenden Kategorien ein.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeJsInclude`

**css**: Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Dies schließt alle CSS-Bibliotheken für die betreffenden Kategorien ein.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeCssInclude`

**themed**: Ein Flag, das angibt, ob nur designbezogene oder nicht designbezogene Bibliotheken enthalten sein sollen. Wenn ausgelassen, sind beide Sätze enthalten. Gilt nur, wenn nur JS oder nur CSS enthalten ist (nicht wenn Kategorien oder Designs enthalten sind).

Das Tag `<cq:includeClientLib>` kann in einem JSP-Code wie folgt verwendet werden:

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

### &lt;cq:defineObjects> {#cq-defineobjects}

Das Tag `<cq:defineObjects>` macht die folgenden, regelmäßig verwendeten Skriptobjekte verfügbar, auf die der Entwickler verweisen kann. Darüber hinaus werden die Objekte verfügbar gemacht, die durch das Tag [`<sling:defineObjects>`](#amp-lt-sling-defineobjects) definiert sind.

**componentContext**

* das aktuelle Komponentenkontextobjekt der Anforderung (com.day.cq.wcm.api.components.Komponentenkontext-Schnittstelle).

**Komponente**

* das aktuelle AEM Komponentenobjekt der aktuellen Ressource (com.day.cq.wcm.api.components.Komponenten-Schnittstelle).

**currentDesign**

* das aktuelle Designobjekt der aktuellen Seite (com.day.cq.wcm.api.designer.Design-Schnittstelle).

**currentPage**

* das aktuelle AEM WCM-Seitenobjekt (Schnittstellecom.day.cq.wcm.api.Seiten-Schnittstelle).

**currentStyle**

* das aktuelle Stilobjekt der aktuellen Zelle (com.day.cq.wcm.api.designer.Style-Schnittstelle).

**Designer**

* das Designer-Objekt, das für den Zugriff auf Design-Informationen verwendet wird (com.day.cq.wcm.api.designer.Designer-Schnittstelle).

**editContext**

* das Bearbeitungskontext-Objekt der AEM-Komponente (com.day.cq.wcm.api.components.EditContext-Schnittstelle).

**pageManager**

* das Seiten-Manager-Objekt für Vorgänge auf Seitenebene (com.day.cq.wcm.api.PageManager-Schnittstelle).

**pageProperties**

* das Seiteneigenschaftenobjekt der aktuellen Seite (org.apache.sling.api.resource.ValueMap).

**Eigenschaften**

* das Seiteneigenschaftenobjekt der aktuellen Ressource (org.apache.sling.api.resource.ValueMap).

**resourceDesign**

* das Design-Objekt der Ressourcenseite (com.day.cq.wcm.api.designer.Design-Schnittstelle).

**resourcePage**

* das Ressourcenseitenobjekt (com.day.cq.wcm.api.Seiten-Schnittstelle).
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
>Wenn die Datei `/libs/foundation/global.jsp` im Skript enthalten ist, wird das Tag `<cq:defineObjects />` automatisch eingefügt.

### &lt;cq:requestURL> {#cq-requesturl}

Das Tag `<cq:requestURL>` schreibt die aktuelle Anforderungs-URL in JspWriter. Die beiden Tags [`<cq:addParam>`](#amp-lt-cq-addparam) und [`<cq:removeParam>`](#amp-lt-cq-removeparam) können innerhalb dieses Tags verwendet werden, um die aktuelle Anforderungs-URL zu bearbeiten, bevor sie geschrieben wird.

Damit können Sie Verknüpfungen zur aktuellen Seite mit unterschiedlichen Parametern erstellen. So können Sie beispielsweise die Anforderung umwandeln:

`mypage.html?mode=view&query=something` in `mypage.html?query=something`.

Mit `addParam` oder `removeParam` wird nur das Auftreten des angegebenen Parameters verändert, alle anderen Parameter sind nicht betroffen.

`<cq:requestURL>` weist kein Attribut auf.

Beispiele:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:addParam> {#cq-addparam}

Das Tag `<cq:addParam>` fügt einen Anfrageparameter mit dem angegebenen Namen und Wert zum umschließenden Tag [`<cq:requestURL>`](#amp-lt-cq-requesturl) hinzu.

Es weist folgende Attribute auf:

**name**

* Name des hinzuzufügenden Parameters

**value**

* Wert des hinzuzufügenden Parameters

**Beispiel:**

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:removeParam> {#cq-removeparam}

Das Tag `<cq:removeParam>` entfernt einen Anfrageparameter mit dem angegebenen Namen und Wert aus dem umschließenden Tag [`<cq:requestURL>`](#amp-lt-cq-requesturl). Wenn kein Wert angegeben wird, werden alle Parameter mit dem angegebenen Namen entfernt.

Es weist folgende Attribute auf:

**name**

* Name des zu entfernenden Parameters

Beispiel:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

## Sling-Tag-Bibliothek {#sling-tag-library}

Die Sling-Tag-Bibliothek enthält hilfreiche Sling-Funktionen.

Wenn Sie die Sling-Tag-Bibliothek in Ihrem Skript verwenden, muss das Skript mit folgendem Code beginnen:

```xml
<%@ taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %>
```

>[!NOTE]
>
>Wenn die Datei `/libs/foundation/global.jsp` im Skript enthalten ist, wird die Tag-Bibliothek von Sling automatisch deklariert.

### &lt;sling:include> {#sling-include}

Das Tag `<sling:include>` fügt eine Ressource in die aktuelle Seite ein.

Es weist folgende Attribute auf:

**flush**

* Ein boolescher Wert, der definiert, ob die Ausgabe geleert werden soll, bevor das Ziel eingeschlossen wird.

**resource**

* Das Ressourcenobjekt, das in die aktuelle Anfrageverarbeitung einbezogen werden soll. resource oder path muss angegeben werden. Wenn beide angegeben sind, hat die Ressource Vorrang.

**path**

* Der Pfad zum Ressourcenobjekt, das in die aktuelle Anfrageverarbeitung eingeschlossen werden soll. Ein relativer Pfad wird an den Pfad der aktuellen Ressource angehängt, deren Skript die angegebene Ressource einschließt. resource oder path muss angegeben werden. Wenn beide angegeben sind, hat die Ressource Vorrang.

**resourceType**

* Der Ressourcentyp der einzuschließenden Ressource. Wenn der Ressourcentyp festgelegt ist, muss es sich bei dem Pfad um den genauen Pfad zu einem Ressourcenobjekt handeln: In diesem Fall wird das Hinzufügen von Parametern, Selektoren und Erweiterungen zum Pfad nicht unterstützt.
* Falls die einzuschließende Ressource mit dem path-Attribut angegeben ist, das nicht in eine Ressource aufgelöst werden kann, erstellt das Tag möglicherweise ein synthetisches Ressourcenobjekt aus dem Pfad und diesem Ressourcentyp.

**replaceSelectors**

* Beim Dispatching werden die Selektoren durch den Wert dieses Attributs ersetzt.

**addSelectors**

* Beim Dispatching wird der Wert dieses Attributs den Selektoren hinzugefügt.

**replaceSuffix**

* Beim Dispatching wird das Suffix durch den Wert dieses Attributs ersetzt.

>[!NOTE]
>
>Die Auflösung der Ressource und des Skripts, das im Tag `<sling:include>` enthalten ist, ist dieselbe wie bei einer normalen URL-Auflösung in Sling. Standardmäßig werden die Selektoren, Erweiterungen usw. aus der aktuellen Anfrage auch für das eingeschlossene Skript verwendet. Sie können über die Tag-Attribute geändert werden: z. B. `replaceSelectors="foo.bar"` können Sie die Selektoren überschreiben.

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

### &lt;sling:defineObjects> {#sling-defineobjects}

Das Tag `<sling:defineObjects>` macht die folgenden, regelmäßig verwendeten Skriptobjekte verfügbar, auf die der Entwickler verweisen kann:

**slingRequest**

* SlingHttpServletRequest-Objekt, das Zugriff auf die Informationen im HTTP-Anfrage-Header bietet. Es erweitert das standardmäßige HttpServletRequest-Objekt und ermöglicht den Abruf Sling-spezifischer Elemente wie Ressourcen, Pfadinformationen und Selektoren.

**slingResponse**

* SlingHttpServletResponse-Objekt, das Zugriff für die vom Server erstellte HTTP-Antwort bietet. Dies entspricht dem HttpServletResponse-Objekt, von dem aus es erweitert wird.**request**
* Das standardmäßige JSP-Anfrageobjekt, bei dem es sich um ein reines HttpServletRequest-Objekt handelt.**Antwort**
* das Standard-JSP-Antwortobjekt, bei dem es sich um ein reines HttpServletResponse-Objekt handelt.

**resourceResolver**

* Das aktuelle ResourceResolver-Objekt. Dies entspricht slingRequest.getResourceResolver().

.**sling**

* Ein SlingScriptHelper-Objekt, das nützliche Hilfsfunktionen für Skripte enthält. In erster Linie sind dies sling.include(&#39;/some/other/resource&#39;) zum Einschließen der Antworten anderer Ressourcen in diese Antwort (z. B. zum Einbetten von Header-HTML-Snippets) und sling.getService(foo.bar.Service.class) zum Abrufen der in Sling verfügbaren OSGi-Dienste (Klassennotation abhängig von der Skriptsprache).

**resource**

* Das derzeit zu bearbeitende Ressourcenobjekt, abhängig von der URL der Anfrage. Dies entspricht slingRequest.getResource().

**currentNode**

* Falls die aktuelle Ressource auf einen JCR-Knoten verweist (was in der Regel bei Sling der Fall ist), ermöglicht dies einen direkten Zugriff auf das Knotenobjekt. Andernfalls ist dieses Objekt nicht definiert.

**log**

* Stellt einen SLF4J-Logger zum Protokollieren im Sling-Protokollsystem aus Skripten heraus bereit, z. B.: log.info(&quot;Executing my script&quot;).

* Es weist folgende Attribute auf:

**requestName**

**responseName**

**nodeName**

**logName resourceResolverName**

**slingName**

**Beispiel:**

```xml
<%@page session="false" %><%
%><%@page import="com.day.cq.wcm.foundation.forms.ValidationHelper"%><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/>
```

## Tag-Bibliothek von JSTL {#jstl-tag-library}

Die [standardmäßige Tag-Bibliothek von JSP (JavaServer Pages)](https://www.oracle.com/java/technologies/java-server-tag-library.html) enthält viele hilfreiche und standardmäßige Tags. Die Kern-, Formatierungs- und Funktions-Tag-Bibliotheken werden anhand von `/libs/foundation/global.jsp` definiert, wie im folgenden Snippet gezeigt.

### Auszug aus /libs/foundation/global.jsp {#extract-of-libs-foundation-global-jsp}

```xml
<%@taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
<%@taglib prefix="fmt" uri="https://java.sun.com/jsp/jstl/fmt" %>
<%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions" %>
```

Nach dem Importieren der Datei `/libs/foundation/global.jsp` wie zuvor beschrieben können Sie die Präfixe `c`, `fmt` und `fn` verwenden, um auf diese Tag-Bibliotheken zuzugreifen. Die offizielle Dokumentation der JSTL ist verfügbar unter [Das Java™ EE 5-Tutorial – JavaServer-Seiten Standard-Tag-Bibliothek](https://docs.oracle.com/javaee/5/tutorial/doc/bnakc.html).
