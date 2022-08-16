---
title: Tag-Bibliotheken
seo-title: Tag Libraries
description: Die Tag-Bibliotheken von Granite, CQ und Sling verleihen Ihnen Zugriff auf spezifische Funktionen für die Verwendung im JSP-Skript der Vorlagen und Komponenten
seo-description: The Granite, CQ, and Sling tag libraries give you access to specific functions for use in the JSP script of your templates and components
uuid: e622d47b-cfb3-4b4a-b8e3-e1adee294219
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6678e3c3-fb0f-4300-8838-38f23f14db07
exl-id: 50e608d5-951f-4a3f-bed4-9e92ff5d7bd4
source-git-commit: de5eb53f6160991ca0718d61afaeed2078a4fa88
workflow-type: tm+mt
source-wordcount: '2483'
ht-degree: 64%

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

### &lt;ui:includeClientLib> {#ui-includeclientlib}

Die `<ui:includeClientLib>` tag Enthält eine AEM HTML-Client-Bibliothek, bei der es sich um eine JS-, CSS- oder Design-Bibliothek handeln kann. Für mehrere Einschlüsse verschiedener Typen, z. B. js und css, muss dieses Tag mehrmals in der JSP verwendet werden. Dieses Tag ist ein praktischer Wrapper für die Dienstschnittstelle ` [com.adobe.granite.ui.clientlibs.HtmlLibraryManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/ui/clientlibs/HtmlLibraryManager.html)`.

Es weist folgende Attribute auf:

**categories** - Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Dateien und CSS-Bibliotheken für die betreffenden Kategorien mit ein. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeIncludes`

**Design** - Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies beinhaltet alle designbezogenen Bibliotheken (CSS und JS) für die entsprechenden Kategorien. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeThemeInclude`

**js** - Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Bibliotheken für die betreffenden Kategorien mit ein.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeJsInclude`

**css** - Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle CSS-Bibliotheken für die betreffenden Kategorien mit ein.

Entspricht: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeCssInclude`

**themed** - Eine Markierung, die anzeigt, dass nur thematische oder nicht thematische Bibliotheken eingeschlossen werden sollen. Wenn ausgelassen, sind beide Sätze enthalten. Gilt nur, wenn nur JS oder nur CSS enthalten ist (nicht wenn Kategorien oder Designs enthalten sind).

Die `<ui:includeClientLib>` -Tag kann wie folgt in einer JSP verwendet werden:

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
>Wenn die `/libs/foundation/global.jsp` im Skript enthalten ist, wird die Tag-Bibliothek automatisch deklariert.

Wenn Sie das JSP-Skript einer AEM-Komponente entwickeln, sollten Sie folgenden Code am Anfang des Skripts einfügen:

```xml
<%@include file="/libs/foundation/global.jsp"%>
```

Sie deklariert die Sling-, CQ- und JSTL-Taglibs und stellt die regelmäßig verwendeten Skriptobjekte bereit, die von der [ `<cq:defineObjects />`](#amp-lt-cq-defineobjects) -Tag. Dies verkürzt und vereinfacht den JSP-Code der Komponente.

### &lt;cq:text> {#cq-text}

Die `<cq:text>` -Tag ist ein praktisches Tag, das Komponententext in einer JSP ausgibt.

Es weist die folgenden optionalen Attribute auf:

**property** - Name der zu verwendenden Eigenschaft. Der Name steht im Bezug zur aktuellen Ressource.

**value** - Für die Ausgabe zu verwendender Wert. Falls dieses Attribut vorhanden ist, wird die Nutzung des Attributs property außer Kraft gesetzt.

**oldValue** - Wert, der für die Vergleichsausgabe verwendet werden soll. Falls dieses Attribut vorhanden ist, wird die Nutzung des Attributs property außer Kraft gesetzt.

**escapeXml** - Definiert, ob die Zeichen &lt;, >, &amp;, &#39; und &quot; in der resultierenden Zeichenfolge in die entsprechenden Zeichenentitätscodes konvertiert werden sollen. Der Standardwert lautet false. Beachten Sie, dass der Escapevorgang nach der optionalen Formatierung angewendet wird.

**format** - Optionales java.text.Format zur Formatierung des Texts.

**noDiff** - Unterdrückt die Berechnung einer diff-Ausgabe, auch wenn eine diff -Information vorhanden ist.

**tagClass** - CSS-Klassenname eines Elements, das eine nicht leere Ausgabe umgibt. Wenn leer, wird kein Element hinzugefügt.

**tagName** - Name des Elements, das eine nicht leere Ausgabe umgibt. Standardmäßig ist DIV eingestellt.

**Platzhalter** - Standardwert, der für null oder leeren Text im Bearbeitungsmodus, d. h. den Platzhalter, verwendet wird. Beachten Sie, dass nach der optionalen Formatierung und dem Escapevorgang die standardmäßige Prüfung ausgeführt wird, d. h. er wird im vorliegenden Format in die Ausgabe geschrieben. Standardwert ist:

`<div><span class="cq-text-placeholder">&para;</span></div>`

**default** - Standardwert für null oder leeren Text. Beachten Sie, dass nach der optionalen Formatierung und dem Escapevorgang die standardmäßige Prüfung ausgeführt wird, d. h. er wird im vorliegenden Format in die Ausgabe geschrieben.

Einige Beispiele zeigen, wie die `<cq:text>` -Tag kann in einer JSP verwendet werden:

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

Die `<cq:setContentBundle>` -Tag erstellt einen i18n-Lokalisierungskontext und speichert ihn im `javax.servlet.jsp.jstl.fmt.localizationContext` Konfigurationsvariable.

Es weist folgende Attribute auf:

**language** - Die Sprache des Gebietsschemas, für das das Ressourcen-Bundle abgerufen werden soll.

**source** - Die Quelle, aus der das Gebietsschema entnommen werden soll. Sie können sie auf einen der folgenden Werte einstellen:

* **statisch** - das Gebietsschema aus dem `language` -Attribut, falls verfügbar, andernfalls über das Standardgebietsschema des Servers.

* **page** - das Gebietsschema wird aus der Sprache der aktuellen Seite oder Ressource übernommen, sofern verfügbar, andernfalls aus dem `language` -Attribut, falls verfügbar, andernfalls über das Standardgebietsschema des Servers.

* **Anfrage** - Das Gebietsschema wird aus dem Gebietsschema der Anforderung übernommen ( `request.getLocale()`).

* **auto** - das Gebietsschema aus dem `language` Attribut , falls verfügbar, andernfalls aus der Sprache der aktuellen Seite oder Ressource, falls verfügbar, aus der Anforderung.

Falls das `source`-Attribut nicht festgelegt ist:

* Wenn die Variable `language` festgelegt ist, wird die `source` -Attribut standardmäßig auf &quot; `static`.

* Wenn die Variable `language` nicht festgelegt ist, wird die `source` -Attribut standardmäßig `auto`.

Das &quot;Inhaltspaket&quot;kann einfach von Standard-JSTL verwendet werden `<fmt:message>` Tags. Die Suche von Nachrichten anhand von Schlüsselwörtern hat zwei Aspekte:

1. Zunächst werden die JCR-Eigenschaften der zugrunde liegenden Ressource, die derzeit wiedergegeben wird, nach Übersetzungen durchsucht. Auf diese Weise können Sie ein einfaches Komponentendialogfeld definieren, um diese Werte zu bearbeiten.
1. Wenn der Knoten keine Eigenschaft mit dem exakt gleichen Namen wie das Schlüsselwort enthält, wird ein Ressourcenpaket aus der Sling-Anforderung (`SlingHttpServletRequest.getResourceBundle(Locale)`) )) geladen. Die Sprache oder das Gebietsschema für dieses Bundle wird durch die Sprach- und Quellattribute der `<cq:setContentBundle>` -Tag.

Die `<cq:setContentBundle>` -Tag kann wie folgt in einer JSP verwendet werden.

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

Die `<cq:include>` -Tag eine Ressource in die aktuelle Seite ein.

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

Sollten Sie `<%@ include file="myScript.jsp" %>` oder `<cq:include script="myScript.jsp" %>` um ein Skript einzubeziehen?

* Die `<%@ include file="myScript.jsp" %>` weist den JSP-Compiler an, eine vollständige Datei in die aktuelle Datei aufzunehmen. Es ist, als ob die Inhalte der enthaltenen Datei direkt in die Originaldatei eingefügt würden.
* Mit dem `<cq:include script="myScript.jsp">` -Tag, wird die Datei zur Laufzeit eingeschlossen.

Sollten Sie `<cq:include>` oder `<sling:include>`?

* Bei der Entwicklung von AEM-Komponenten empfiehlt Adobe die Verwendung von `<cq:include>`.
* `<cq:include>` ermöglicht das direkte Einfügen von Skriptdateien anhand ihres Namens, wenn Sie das script-Attribut verwenden. Dabei werden Komponenten- und Ressourcentypvererbung berücksichtigt. Diese ist häufig einfacher als die strikte Einhaltung der Skriptauflösung von Sling mithilfe von Selektoren und Erweiterungen.

### &lt;cq:includeClientLib> {#cq-includeclientlib}

>[!CAUTION]
>
>`<cq:includeClientLib>` ist seit AEM 5.6 veraltet. [ `<ui:includeClientLib>`](/help/sites-developing/taglib.md#ui-includeclientlib) verwendet werden.

Die `<cq:includeClientLib>` tag Enthält eine AEM HTML-Client-Bibliothek, bei der es sich um eine JS-, CSS- oder Design-Bibliothek handeln kann. Für mehrere Einschlüsse verschiedener Typen, z. B. js und css, muss dieses Tag mehrmals in der JSP verwendet werden. Dieses Tag ist ein praktischer Wrapper für die Dienstschnittstelle `com.day.cq.widget.HtmlLibraryManager`.

Es weist folgende Attribute auf:

**categories** - Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Dateien und CSS-Bibliotheken für die betreffenden Kategorien mit ein. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeIncludes`

**Design** - Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies beinhaltet alle designbezogenen Bibliotheken (CSS und JS) für die entsprechenden Kategorien. Der Designname wird aus der Abfrage extrahiert.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#`writeThemeInclude

**js** - Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Bibliotheken für die betreffenden Kategorien mit ein.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeJsInclude`

**css** - Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle CSS-Bibliotheken für die betreffenden Kategorien mit ein.

Entspricht: `com.day.cq.widget.HtmlLibraryManager#writeCssInclude`

**themed** - Eine Markierung, die anzeigt, dass nur thematische oder nicht thematische Bibliotheken eingeschlossen werden sollen. Wenn ausgelassen, sind beide Sätze enthalten. Gilt nur, wenn nur JS oder nur CSS enthalten ist (nicht wenn Kategorien oder Designs enthalten sind).

Die `<cq:includeClientLib>` -Tag kann wie folgt in einer JSP verwendet werden:

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

Die `<cq:defineObjects>` -Tag stellt die folgenden, regelmäßig verwendeten Skriptobjekte bereit, auf die der Entwickler verweisen kann. Außerdem werden die Objekte bereitgestellt, die durch die [ `<sling:defineObjects>`](#amp-lt-sling-defineobjects) -Tag.

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

**Eigenschaften**

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
>Wenn die `/libs/foundation/global.jsp` im Skript enthalten ist, wird die `<cq:defineObjects />` -Tag automatisch eingeschlossen.

### &lt;cq:requestURL> {#cq-requesturl}

Die `<cq:requestURL>` -Tag schreibt die aktuelle Anfrage-URL in den JspWriter. Die beiden Tags [ `<cq:addParam>`](#amp-lt-cq-addparam) und [ `<cq:removeParam>`](#amp-lt-cq-removeparam) und kann innerhalb des Hauptteils dieses Tags verwendet werden, um die aktuelle Anfrage-URL zu ändern, bevor sie geschrieben wird.

Sie können Links zur aktuellen Seite mit variierenden Parametern erstellen. Beispielsweise können Sie die Anforderung umwandeln:

`mypage.html?mode=view&query=something` in `mypage.html?query=something`.

Die Verwendung von `addParam` oder `removeParam` nur das Vorkommen des angegebenen Parameters ändert, sind alle anderen Parameter nicht betroffen.

`<cq:requestURL>` hat kein -Attribut.

Beispiele:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:addParam> {#cq-addparam}

Die `<cq:addParam>` -Tag fügt einen Anforderungsparameter mit dem angegebenen Namen und Wert zum einschließenden [ `<cq:requestURL>`](#amp-lt-cq-requesturl) -Tag.

Es weist folgende Attribute auf:

**name**

* Name des Parameters, der hinzugefügt werden soll

**value**

* Wert des Parameters, der hinzugefügt werden soll

**Beispiel:**

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:removeParam> {#cq-removeparam}

Die `<cq:removeParam>` -Tag entfernt einen Anforderungsparameter mit dem angegebenen Namen und Wert aus dem einschließenden [ `<cq:requestURL>`](#amp-lt-cq-requesturl) -Tag. Wenn kein Wert angegeben wird, werden alle Parameter mit dem jeweiligen Namen entfernt.

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
>Wenn die `/libs/foundation/global.jsp` im Skript enthalten ist, wird die Sling-Tag-Bibliothek automatisch deklariert.

### &lt;sling:include> {#sling-include}

Die `<sling:include>` -Tag eine Ressource in die aktuelle Seite ein.

Es weist folgende Attribute auf:

**flush**

* Ein boolescher Wert, der definiert, ob die Ausgabe geleert werden soll, bevor das Ziel eingefügt wird.

**resource**

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
>Die Auflösung der Ressource und des Skripts, die im `<sling:include>` -Tag entspricht der normalen Sling-URL-Auflösung. Standardmäßig werden die Selektoren, die Erweiterung usw. der aktuellen Anforderung auch für das enthaltene Skript verwendet. Sie können über die Tag-Attribute geändert werden: Beispiel `replaceSelectors="foo.bar"` ermöglicht es Ihnen, die Selektoren zu überschreiben.

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

Die `<sling:defineObjects>` -Tag stellt die folgenden, regelmäßig verwendeten Skriptobjekte bereit, auf die der Entwickler verweisen kann:

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

**resource**

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

Die [JavaServer-Seiten Standard-Tag-Bibliothek](https://www.oracle.com/technetwork/java/index-jsp-135995.html) enthält viele nützliche und standardmäßige Tags. Die Taglibs für Kern, Formatierung und Funktionen werden durch die Variable `/libs/foundation/global.jsp` wie im folgenden Snippet gezeigt.

### Auszug aus /libs/foundation/global.jsp {#extract-of-libs-foundation-global-jsp}

```xml
<%@taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
<%@taglib prefix="fmt" uri="https://java.sun.com/jsp/jstl/fmt" %>
<%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions" %>
```

Nach dem Import der `/libs/foundation/global.jsp` wie zuvor beschrieben, können Sie die `c`, `fmt` und `fn` -Präfixe für den Zugriff auf diese Taglibs. Die offizielle Dokumentation der JSTL ist verfügbar unter [Das Java EE 5-Tutorial – standardmäßige Tag-Bibliothek JavaServer-Seiten](https://docs.oracle.com/javaee/5/tutorial/doc/bnakc.html).
