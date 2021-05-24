---
title: Verwenden von Sling-Adaptern
seo-title: Verwenden von Sling-Adaptern
description: Mit Sling wird ein Adaptermuster zum bequemen Übersetzen von Objekten bereitgestellt, die zum Implementieren der Adaptable-Schnittstelle verwendet werden
seo-description: Mit Sling wird ein Adaptermuster zum bequemen Übersetzen von Objekten bereitgestellt, die zum Implementieren der Adaptable-Schnittstelle verwendet werden
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 6465e2c4-28e5-4fc8-8cca-7b632f10ba5a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2350'
ht-degree: 96%

---

# Verwenden von Sling-Adaptern {#using-sling-adapters}

Mit [Sling](https://sling.apache.org) wird ein [Adaptermuster](https://sling.apache.org/site/adapters.html) zum bequemen Übersetzen von Objekten bereitgestellt, die zum Implementieren der [Adaptable](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29)-Schnittstelle verwendet werden. Diese Schnittstelle stellt eine generische [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29)-Methode bereit, mit der das Objekt in den Klassentyp übersetzt wird, der als Argument übergeben wird.

Sie können beispielsweise einfach wie folgt vorgehen, um ein Ressourcenobjekt in das entsprechende Knotenbjekt zu übersetzen:

```java
Node node = resource.adaptTo(Node.class);
```

## Nutzungsszenarien {#use-cases}

Es gibt die folgenden Nutzungsszenarien:

* Rufen Sie spezifische Objekte für die Implementierung ab.

   Eine JCR-basierte Implementierung der generischen [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html)-Schnittstelle ermöglicht beispielsweise Zugriff auf das zugrunde liegende JCR-[`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html)-Element.

* Erstellung von direkten Verknüpfungen für Objekte, für die interne Kontextobjekte übergeben werden müssen.

   Der JCR-basierte [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) enthält beispielsweise einen Verweis auf die [`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html) der Anfrage, die wiederum für viele Objekte benötigt wird, deren Ausführung von dieser Anfragesitzung abhängig ist, z. B. [`PageManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) oder [`UserManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* Direkte Verknüpfung mit Services.

   Dies ist ein seltener Fall, da `sling.getService()` bereits eine einfache Möglichkeit darstellt.

### NULL-Rückgabewert {#null-return-value}

`adaptTo()` kann NULL zurückgeben.

Hierfür gibt es verschiedene Gründe, z. B.:

* Die Implementierung unterstützt den Zieltyp nicht.
* Eine Adapter-Factory zur Verarbeitung dieses Falls ist nicht aktiv (z. B. aufgrund von fehlenden Service-Verweisen)
* Fehler für interne Bedingung
* Service ist nicht verfügbar

Es ist wichtig, dass Sie den NULL-Fall ordnungsgemäß verarbeiten. Für das JSP-Rendering kann es zulässig sein, dass für JSP ein Fehler auftritt, wenn dies zu einem leeren Inhaltselement führt.

### Caching {#caching}

Zur Verbesserung der Leistung dürfen Implementierungen das Objekt zwischenspeichern, das über einen `obj.adaptTo()`-Aufruf zurückgegeben wird. Wenn das `obj` gleich ist, ist auch das zurückgegebene Objekt dasselbe.

Diese Zwischenspeicherung wird für alle auf `AdapterFactory` basierenden Fälle durchgeführt.

Es gibt aber keine allgemeine Regel. Bei dem Objekt kann es sich entweder um eine neue oder eine vorhandene Instanz handeln. Dies bedeutet, dass Sie sich nicht auf eines der Verhalten verlassen können. Es ist also – vor allem innerhalb von `AdapterFactory` – wichtig, dass Objekte bei diesem Szenario wiederverwendet werden können.

### Funktionsweise {#how-it-works}

Es gibt verschiedene Möglichkeiten, `Adaptable.adaptTo()` zu implementieren:

* Über das Objekt selbst. Die eigentliche Methode wird implementiert. Anschließend erfolgt die Zuordnung zu bestimmten Objekten.
* Über ein [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), mit dem zufällige Objekte zugeordnet werden können.

   Die Objekte müssen trotzdem noch die `Adaptable`-Schnittstelle implementieren und [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (übergibt den `adaptTo`-Aufruf an einen zentralen Adapter-Manager) erweitern.

   Dies ermöglicht die Verwendung von Hooks für den `adaptTo`-Mechanismus für vorhandene Klassen, z. B. `Resource`.

* Eine Kombination beider Vorgehensweisen.

Im ersten Fall kann über javadocs angegeben werden, welche `adaptTo-targets` möglich sind. Für bestimmte Unterklassen, z. B. die JCR-basierte Resource-Klasse, ist dies häufig nicht möglich. Da Implementierungen von `AdapterFactory` im letzteren Fall normalerweise Teil der privaten Klassen eines Pakets sind, werden sie nicht per Client-API verfügbar gemacht und auch nicht in javadocs aufgeführt. Theoretisch wäre es möglich, auf alle `AdapterFactory`-Implementierungen über die [OSGi](/help/sites-deploying/configuring-osgi.md)-Service-Laufzeit zuzugreifen und sich die Konfigurationen der „adaptierbaren Elemente“ (Quellen und Ziele) anzusehen, diese aber nicht einander zuzuordnen. Dies hängt letztendlich von der internen Logik ab, die dokumentiert werden muss. Dies ist der Grund für diesen Verweis.

## Verweis  {#reference}

### Sling {#sling}

Adaptierung von [**Resource**](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td>
   <td>Wenn dies eine auf einem JCR-Knoten basierende Ressource oder eine JCR-Eigenschaft mit Verweis auf einen Knoten ist.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Property</a></td>
   <td>Wenn dies eine auf einer JCR-Eigenschaft basierende Ressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Item</a></td>
   <td>Wenn dies eine JCR-basierte Ressource ist (Knoten oder Eigenschaft).</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">Map</a></td>
   <td>Gibt eine Zuordnung der Eigenschaften zurück, wenn dies eine auf einem JCR-Knoten basierende Ressource ist (oder eine andere Ressource, die Wertzuordnungen unterstützt).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Gibt eine benutzerfreundliche Zuordnung der Eigenschaften zurück, wenn dies eine auf einem JCR-Knoten basierende Ressource ist (oder eine andere Ressource, die Wertzuordnungen unterstützt). Dies kann (auf einfachere Weise) auch per <br /><code><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (zur Verarbeitung von NULL-Fällen usw.) erreicht werden.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Erweiterung von <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, mit der beim Suchen nach Eigenschaften die Hierarchie der Ressourcen berücksichtigt werden kann.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModifiableValueMap</a></td>
   <td>Eine Erweiterung der <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, mit der Sie Eigenschaften auf diesem Knoten ändern können.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Gibt den binären Inhalt einer Datei-Ressource (wenn es eine auf einem JCR-Knoten basierende Ressource ist und der Knotentyp <code>nt:file</code> oder <code>nt:resource</code> lautet; wenn es eine Paket-Ressource ist; Datei-Inhalt, wenn es eine Dateisystemressource ist) oder die Daten einer binären JCR-Eigenschaftsressource zurück.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Gibt eine URL für die Ressource zurück (Repository-URL dieses Knotens, wenn es eine auf einem JCR-Knoten basierende Ressource ist, eine jar-Paket-URL, wenn es eine Paket-Ressource ist, oder eine Datei-URL, wenn es eine Dateisystemressource ist).</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html">File</a></td>
   <td>Wenn es eine Dateisystemressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Wenn diese Ressource ein Skript ist (z. B. eine JSP-Datei), für das ein Skriptmodul bei Sling registriert ist.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/products/servlet/2.2/javadoc/javax/servlet/Servlet.html">Servlet</a></td>
   <td>Wenn diese Ressource ein Skript ist (z. B. eine JSP-Datei), für das ein Skriptmodul bei Sling registriert ist, oder wenn es eine Servlet-Ressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html">String</a><br /><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Boolean.html"> Boolean</a><br /><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Long.html"> Long</a><br /><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Double.html"> Double</a><br /><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/util/Calendar.html"> Calendar</a><br /><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html"> Value</a><br /><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html"> String[]</a><br /><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Boolean.html"> Boolean[]</a><br /><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Long.html"> Long[]</a><br /><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/util/Calendar.html"> Calendar[]</a><br /><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html"> Value[]</a></td>
   <td>Gibt den bzw. die Werte zurück, wenn es eine auf einer JCR-Eigenschaft basierende Ressource ist (und der Wert passt).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Wenn es eine auf einem JCR-Knoten basierende Ressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html">Seite</a></td>
   <td>Wenn es eine auf einem JCR-Knoten basierende Ressource ist und der Knoten den Typ <code>cq:Page</code> (oder <code>cq:PseudoPage</code>) hat.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html">Komponente</a></td>
   <td>Wenn es eine <code>cq:Component</code>-Knotenressource ist.</td>
  </tr>  
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Design.html">Design</a></td>
   <td>Wenn es ein Design-Knoten ist (<code>cq:Page</code>).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html">Vorlage</a></td>
   <td>Wenn es eine <code>cq:Template</code>-Knotenressource ist.</td>
  </tr>  
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Blueprint</a></td>
   <td>Wenn es eine <code>cq:Template</code>-Knotenressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html">Asset</a></td>
   <td>Wenn es eine dam:Asset-Knotenressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Rendition.html">Rendition</a></td>
   <td>Wenn es eine dam:Asset-Ausgabedarstellung ist (nt:file unter dem Ordner „rendition“ eines dam:Asset-Elements).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html">Tag</a></td>
   <td>Wenn es eine <code>cq:Tag</code>-Knotenressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Basiert auf der JCR-Sitzung, wenn es eine JCR-basierte Ressource ist und der Benutzer über Berechtigungen zum Zugreifen auf den UserManager verfügt.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a></td>
   <td>Die Authorizable-Funktion ist die allgemeine Basisschnittstelle für Benutzer und Gruppe.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a></td>
   <td>User ist ein spezieller Fall von Authorizable, der authentifiziert und personifiziert werden kann.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Sucht unter der Ressource (oder es wird setSearchIn() genutzt), wenn es eine JCR-basierte Ressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Workflow-Status für den jeweiligen Seiten-/Workflow-Payload-Knoten.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Replikationsstatus für die jeweilige Ressource oder den zugehörigen Unterknoten „jcr:content“ (wird zuerst geprüft).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Gibt eine angepasste Connector-Ressource für bestimmte Typen zurück, wenn es eine auf einem JCR-Knoten basierende Ressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>Wenn es eine <code>cq:ContentSyncConfig</code>-Knotenressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>Wenn das Element unter einer <code>cq:ContentSyncConfig</code>-Knotenressource angeordnet ist.</td>
  </tr>
 </tbody>
</table>

Adaption von [**ResourceResolver**](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Session</a></td>
   <td>Die JCR-Sitzung der Anfrage, wenn es sich um einen JCR-basierten Ressourcenauflöser handelt (Standard).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Basierend auf der JCR-Sitzung, wenn es sich um einen JCR-basierten Ressourcenauflöser handelt.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>Basierend auf der JCR-Sitzung, wenn es sich um einen JCR-basierten Ressourcenauflöser handelt.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>Der UserManager bietet Zugriff auf autorisierbare Objekte, d. h. Benutzer und Gruppen, und ermöglicht deren Pflege. Der UserManager ist an eine bestimmte Sitzung gebunden.
   </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a> </td>
   <td>Der aktuelle Benutzer.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a><br /> </td>
   <td>Der aktuelle Benutzer.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">Externalizer</a></td>
   <td>Für das Externalisieren von absoluten URLs, auch ohne das Anfrageobjekt.<br /> </td>
  </tr>
 </tbody>
</table>

Adaptierung von [**SlingHttpServletRequest**](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) für:

Es sind noch keine Ziele vorhanden, aber „Adaptable“ wird implementiert und kann als Quelle in einer benutzerdefinierten „AdapterFactory“ verwendet werden.

Adaptierung von [**SlingHttpServletResponse**](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>Wenn dies eine Sling Rewriter-Antwort ist.</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

Adaption von **[Page](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html)** für:

<table>
 <tbody>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td>
   <td>Ressource der Seite.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Bezeichnete Ressource (== this).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knoten</a></td>
   <td>Knoten der Seite.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alle Elemente, für die die Ressource der Seite adaptiert werden kann.</td>
  </tr>
 </tbody>
</table>

Adaption von **[Component](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html)** für:

| [Ressource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource der Komponente. |
|---|---|
| [LabeledResource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Bezeichnete Ressource (== this). |
| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten der Komponente. |
| ... | Alle Elemente, für die die Ressource der Komponente adaptiert werden kann. |

Adaption von **[Template](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html)** für:

<table>
 <tbody>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Ressource der Vorlage.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Bezeichnete Ressource (== this).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knoten</a></td>
   <td>Knoten dieser Vorlage.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alle Elemente, für die die Ressource der Vorlage adaptiert werden kann.</td>
  </tr>
 </tbody>
</table>

#### Sicherheit {#security}

Adaption von **Authorizable**, **User** und **Group** für:

| [Knoten](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Gibt den Stammknoten des Benutzers/der Gruppe zurück. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Gibt den Replizierungsstatus für den Stammknoten des Benutzers/der Gruppe zurück. |

#### DAM {#dam}

Adaption von **Asset** für:

| [Ressource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource des Assets. |
|---|---|
| [Knoten](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten des Assets. |
| ... | Alle Elemente, für die die Ressource des Assets adaptiert werden kann. |

#### Tagging {#tagging}

Adaption von **Tag** für:

| [Ressource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource des Tags. |
|---|---|
| [Knoten](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten des Tags. |
| ... | Alle Elemente, für die die Ressource des Tags adaptiert werden kann. |

#### Andere {#other}

Über Sling/JCR/OCM wird außerdem eine ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` für benutzerdefinierte OCM-Objekte ([Object Content Mapping](https://jackrabbit.apache.org/object-content-mapping.html)) bereitgestellt.
