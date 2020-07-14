---
title: Verwenden von Sling-Adaptern
seo-title: Verwenden von Sling-Adaptern
description: Mit Sling wird ein Adaptermuster zum bequemen Übersetzen von Objekten bereitgestellt, die zum Implementieren der Adaptable-Schnittstelle verwendet werden.
seo-description: Mit Sling wird ein Adaptermuster zum bequemen Übersetzen von Objekten bereitgestellt, die zum Implementieren der Adaptable-Schnittstelle verwendet werden.
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
translation-type: tm+mt
source-git-commit: 4949eeb190f26850f80e1ad107f2057c661ed23d
workflow-type: tm+mt
source-wordcount: '2100'
ht-degree: 42%

---


# Verwenden von Sling-Adaptern{#using-sling-adapters}

Mit [Sling](https://sling.apache.org) wird ein [Adaptermuster](https://sling.apache.org/site/adapters.html) zum bequemen Übersetzen von Objekten bereitgestellt, die zum Implementieren der [Adaptable](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29)-Schnittstelle verwendet werden. This interface provides a generic [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) method that will translate the object to the class type being passed as the argument.

Sie können beispielsweise einfach wie folgt vorgehen, um ein Ressourcenobjekt in das entsprechende Node-Objekt zu übersetzen:

```java
Node node = resource.adaptTo(Node.class);
```

## Nutzungsszenarien {#use-cases}

Es gibt die folgenden Nutzungsszenarien:

* Rufen Sie spezifische Objekte für die Implementierung ab.

   For example, a JCR-based implementation of the generic [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) interface provides access to the underlying JCR [`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).`

* Erstellung von direkten Verknüpfungen für Objekte, für die interne Kontextobjekte übergeben werden müssen.

   For example, the JCR-based [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) holds a reference to the request&#39;s [`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html), which in turn is needed for many objects that will work based on that request session, such as the [`PageManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) or [`UserManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* Direkte Verknüpfung mit Diensten.

   A rare case - `sling.getService()` is simple as well.

### NULL-Rückgabewert {#null-return-value}

`adaptTo()` kann null zurückgeben.

Hierfür gibt es verschiedene Gründe, z. B.:

* Die Implementierung unterstützt den Zieltyp nicht.
* Eine Adapter-Factory zur Verarbeitung dieses Falls ist nicht aktiv (z. B. aufgrund von fehlenden Dienstverweisen)
* Fehler für interne Bedingung
* Dienst ist nicht verfügbar

Es ist wichtig, dass Sie den NULL-Fall ordnungsgemäß verarbeiten. Für das JSP-Rendering kann es zulässig sein, dass für JSP ein Fehler auftritt, wenn dies zu einem leeren Inhaltselement führt.

### Caching {#caching}

To improve performance, implementations are free to cache the object returned from a `obj.adaptTo()` call. Wenn das `obj`-Element gleich ist, ist auch das zurückgegebene Objekt dasselbe.

Diese Zwischenspeicherung wird für alle auf `AdapterFactory` basierenden Fälle durchgeführt.

Es gibt aber keine allgemeine Regel. Bei dem Objekt kann es sich entweder um eine neue oder eine vorhandene Instanz handeln. Dies bedeutet, dass Sie sich nicht auf eines der Verhalten verlassen können. Es ist – vor allem innerhalb von `AdapterFactory` – also wichtig, dass Objekte bei diesem Szenario wiederverwendet werden können.

### Funktionsweise {#how-it-works}

There are various ways that `Adaptable.adaptTo()` can be implemented:

* Über das Objekt selbst. Die eigentliche Methode wird implementiert und dann erfolgt die Zuordnung zu bestimmten Objekten.
* By an [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)`, which can map arbitrary objects.

    Die Objekte müssen trotzdem noch die `Adaptable`-Schnittstelle implementieren und [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (übergibt den `adaptTo`-Aufruf an einen zentralen Adapter-Manager) erweitern.

    Dies ermöglicht die Verwendung von Hooks für den `adaptTo`-Mechanismus für vorhandene Klassen, z. B. `Resource`.

* Eine Kombination beider Vorgehensweisen.

Im ersten Fall kann über javadocs angegeben werden, welche `adaptTo-targets` möglich sind. Für bestimmte Unterklassen, z. B. die JCR-basierte Resource-Klasse, ist dies häufig nicht möglich. Da Implementierungen von `AdapterFactory` im letzteren Fall normalerweise Teil der privaten Klassen eines Bundles sind, werden sie nicht per Client-API verfügbar gemacht und auch nicht in javadocs aufgeführt. Theoretisch wäre es möglich, auf alle `AdapterFactory`-Implementierungen über die [OSGi](/help/sites-deploying/configuring-osgi.md)-Dienstlaufzeit zuzugreifen und sich die Konfigurationen der „adaptierbaren Elemente“ (Quellen und Ziele) anzusehen, diese aber nicht einander zuzuordnen. Dies hängt letztendlich von der internen Logik ab, die dokumentiert werden muss. Dies ist der Grund für diesen Verweis.

## Verweis {#reference}

### Sling {#sling}

Adaptierung von [**Resource **](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html)für:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knoten</a></td>
   <td>Wenn es sich hierbei um eine JCR-Node-basierte Ressource oder eine JCR-Eigenschaft handelt, die auf einen Knoten verweist.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Eigenschaft</a></td>
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
   <td>Gibt eine benutzerfreundliche Zuordnung der Eigenschaften zurück, wenn dies eine auf einem JCR-Knoten basierende Ressource ist (oder eine andere Ressource, die Wertzuordnungen unterstützt). Can also be achieved (more simply) by using<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (handles null case, etc.).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Extension of <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> which allows the hierarchy of resources to be taken into account when looking for properties.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModizableValueMap</a></td>
   <td>Eine Erweiterung der <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, mit der Sie Eigenschaften auf diesem Knoten ändern können.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Returns the binary content of a file resource (if this is a JCR-node-based resource and the node type is <code>nt:file</code> or <code>nt:resource</code>; if this is a bundle resource; file content if this is a file system resource) or the data of a binary JCR property resource.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Gibt eine URL für die Ressource zurück (Repository-URL dieses Knotens, wenn es eine auf einem JCR-Knoten basierende Ressource ist, eine jar-Bundle-URL, wenn es eine Bundle-Ressource ist, oder eine file-URL, wenn es eine Dateisystemressource ist).</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html">Datei</a></td>
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
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html">Asset-</a></td>
   <td>Wenn es eine dam:Asset-Knotenressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Rendition.html">Rendition</a></td>
   <td>Wenn dies eine dam:Asset-Darstellung ist (nt:file im Ausgabeordner eines dam:Assert)</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Basiert auf der JCR-Sitzung, wenn es eine JCR-basierte Ressource ist und der Benutzer über Berechtigungen zum Zugreifen auf den UserManager verfügt.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Autorisierter</a></td>
   <td>Die Authorizable-Funktion ist die allgemeine Basisschnittstelle für Benutzer und Gruppe.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a></td>
   <td>Benutzer ist ein spezieller Autorisierbarer Benutzer, der authentifiziert und imitiert werden kann.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Sucht unter der Ressource (oder es wird setSearchIn() genutzt), wenn es eine JCR-basierte Ressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Workflowstatus für den jeweiligen Seiten-/Workflow-Nutzlast-Knoten.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Replikationsstatus für die jeweilige Ressource oder dem zugehörigen Unterknoten „jcr:content“ (wird zuerst geprüft).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Gibt eine angepasste Connector-Ressource für bestimmte Typen zurück, wenn es eine auf einem JCR-Knoten basierende Ressource ist.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>If this is a <code>cq:ContentSyncConfig</code> node resource.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>If this is below a <code>cq:ContentSyncConfig</code> node resource.</td>
  </tr>
 </tbody>
</table>

[**ResourceResolver **](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html)passt sich an:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sitzung</a></td>
   <td>Die JCR-Sitzung der Anforderung, wenn es sich um einen JCR-basierten Ressourcenauflöser handelt (Standard).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Basierend auf der JCR-Sitzung, wenn es sich um einen JCR-basierten Ressourcenauflöser handelt.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>Der UserManager bietet Zugriff auf autorisierbare Objekte, d. h. Benutzer und Gruppen, und ermöglicht deren Pflege. Der UserManager ist an eine bestimmte Sitzung gebunden.
   </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Autorisierter</a> </td>
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
   <td>Für das Externalisieren von absoluten URLs, auch ohne das Anforderungsobjekt.<br /> </td>
  </tr>
 </tbody>
</table>

Adaptierung von [**SlingHttpServletRequest **](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html)für:

Es sind noch keine Ziele vorhanden, aber „Adaptable“ wird implementiert und kann als Quelle in einer benutzerdefinierten „AdapterFactory“ verwendet werden.

Adaptierung von [**SlingHttpServletResponse **](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html)für:

<table>
 <tbody>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>Wenn dies eine Sling Rewriter-Antwort ist.</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

Adaptierung von **Page** für:

<table>
 <tbody>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Ressource</a><br /> </td>
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
   <td>Alles, woran die Ressource der Seite angepasst werden kann.</td>
  </tr>
 </tbody>
</table>

Adaptierung von **Component** für:

| [Ressource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource der Komponente. |
|---|---|
| [LabeledResource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Bezeichnete Ressource (== this). |
| [Knoten](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten der Komponente. |
| ... | Alles, woran die Ressource der Komponente angepasst werden kann. |

Adaptierung von **Template** für:

<table>
 <tbody>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Ressource</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
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
   <td>Alles, an das die Vorlagenressource angepasst werden kann.</td>
  </tr>
 </tbody>
</table>

#### Sicherheit {#security}

Adaptierung von **Authorizable**, **User** und **Group** für:

| [Knoten](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Gibt den Stammknoten des Benutzers/der Gruppe zurück. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Gibt den Replizierungsstatus für den Stammknoten des Benutzers/der Gruppe zurück. |

#### DAM {#dam}

**Asset** passt sich an:

| [Ressource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource des Assets. |
|---|---|
| [Knoten](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten des Assets. |
| ... | Alles, woran die Ressource des Assets angepasst werden kann. |

#### Tagging {#tagging}

**Tag** passt sich an:

| [Ressource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource des Tags. |
|---|---|
| [Knoten](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten des Tags. |
| ... | Alles, woran die Ressource des Tags angepasst werden kann. |

#### Andere {#other}

Über Sling/JCR/OCM wird außerdem eine ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` für benutzerdefinierte OCM-Objekte ([Object Content Mapping](https://jackrabbit.apache.org/object-content-mapping.html)) bereitgestellt.
