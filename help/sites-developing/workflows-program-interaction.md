---
title: Programmgesteuerte Interaktion mit Workflows
seo-title: Programmgesteuerte Interaktion mit Workflows
description: 'null'
seo-description: 'null'
uuid: a0f19fc6-b9bd-4b98-9c0e-fbf4f7383026
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: cb621332-a149-4f8d-9425-fd815b033c38
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Programmgesteuerte Interaktion mit Workflows{#interacting-with-workflows-programmatically}

Während Sie [Ihre Workflows anpassen und erweitern](/help/sites-developing/workflows-customizing-extending.md), können Sie auf Workflow-Objekte zugreifen:

* [Verwendung der Workflow-Java-API](#using-the-workflow-java-api)
* [Abrufen von Workflow-Objekten in ECMA-Skripten](#obtaining-workflow-objects-in-ecma-scripts)
* [Verwendung der Workflow-REST-API](#using-the-workflow-rest-api)

## Verwendung der Workflow-Java-API {#using-the-workflow-java-api}

Die Workflow-Java-API besteht aus dem Paket [`com.adobe.granite.workflow`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/package-summary.html) und mehreren Unterpaketen. Der wichtigste Bestandteil der API ist die `com.adobe.granite.workflow.WorkflowSession`-Klasse. Die `WorkflowSession`-Klasse ermöglicht Zugriff auf Workflow-Objekte während des Designs und während der Laufzeit:

* Workflow-Modelle
* Arbeitselemente
* Workflow-Instanzen
* Workflow-Daten
* Elemente im Posteingang

Die Klasse bietet außerdem mehrere Methoden zum Eingreifen in Workflow-Lebenszyklen.

Die folgende Tabelle enthält Links zur Referenzdokumentation verschiedener wichtiger Java-Objekte, die bei der programmgesteuerten Interaktion mit Workflows verwendet werden. Die folgenden Beispiele veranschaulichen, wie Sie die Klassenobjekte im Code abrufen und verwenden.

<table>
 <tbody>
  <tr>
   <th>Funktionen<a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html"></a></th>
   <th>Objekte<br /> </th>
  </tr>
  <tr>
   <td>Zugriff auf einen Workflow<br /> </td>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html"><code>WorkflowSession</code></a><br /> </td>
  </tr>
  <tr>
   <td>Ausführung und Abfrage einer Workflow-Instanz<br /> </td>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/Workflow.html"><code>Workflow</code></a><br /> <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkItem.html"><code>WorkItem</code></a><br /> <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkflowData.html"><code>WorkflowData</code></a><br /> </td>
  </tr>
  <tr>
   <td>Verwaltung eines Workflow-Modells<br /> </td>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowModel.html"><code>WorkflowModel</code></a><br /> <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowNode.html"><code>WorkflowNode</code></a><br /> <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowTransition.html"><code>WorkflowTransition</code></a><br /> </td>
  </tr>
  <tr>
   <td>Informationen für einen Knoten, der sich im Workflow befindet (oder nicht) </td>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html"><code>WorkflowStatus</code></a></td>
  </tr>
 </tbody>
</table>

## Abrufen von Workflow-Objekten in ECMA-Skripten {#obtaining-workflow-objects-in-ecma-scripts}

Wie unter [Auffinden des Skripts](/help/sites-developing/the-basics.md#locating-the-script) beschrieben, stellt AEM (über Apache Sling) eine ECMA-Skript-Engine zur Verfügung, die serverseitige ECMA-Skripte ausführt. Die [`org.apache.sling.scripting.core.ScriptHelper`](https://sling.apache.org/apidocs/sling5/org/apache/sling/scripting/core/ScriptHelper.html)-Klasse ist für Ihre Skripte sofort als `sling`-Variable verfügbar.

Die `ScriptHelper`-Klasse bietet Zugriff auf `SlingHttpServletRequest`, das Sie später verwenden können, um das Objekt `WorkflowSession` abzurufen. Beispiel:

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

## Verwenden der Workflow-REST-API {#using-the-workflow-rest-api}

Die Workflow-Konsole verwendet die REST-API in hohem Maße. so beschreibt diese Seite die REST-API für Workflows.

>[!NOTE]
>
>Mit dem Befehlszeilenwerkzeug &quot;curl&quot;können Sie die REST-API des Workflows verwenden, um auf Workflow-Objekte zuzugreifen und Instanzlebenszyklen zu verwalten. Die Beispiele auf dieser Seite zeigen die Verwendung der REST-API über das Kommandozeilen-Tool „curl“.

Die folgenden Aktionen werden von der REST-API unterstützt:

* Starten oder Anhalten eines Workflow-Services
* Erstellen, Aktualisieren oder Löschen von Workflow-Modellen
* [Starten, Pausieren, Fortsetzen oder Beenden von Workflow-Instanzen](/help/sites-administering/workflows.md#workflow-status-and-actions)
* Abschließen oder Delegieren von Arbeitselementen

>[!NOTE]
>
>Mit Firebug, einer Firefox-Erweiterung für die Webentwicklung, können Sie den HTTP-Traffic verfolgen, während die Konsole in Betrieb ist. Sie können beispielsweise mit einer `POST`-Anfrage die Parameter und Werte prüfen, die an den AEM-Server gesendet werden.

In this page it is assumed that AEM runs on localhost at port `4502` and that the installation context is &quot; `/`&quot; (root). Wenn dies nicht auf Ihre Installation zutrifft, müssen die URIs für die HTTP-Anfragen entsprechend angepasst werden.

Als Rendering-Methode wird für `GET`-Anfragen JSON-Rendering unterstützt. The URLs for `GET` should have the `.json` extension, for example:

`http://localhost:4502/etc/workflow.json`

### Verwaltung von Workflow-Instanzen {#managing-workflow-instances}

Die folgenden HTTP-Anfragemethoden gelten für:

`http://localhost:4502/etc/workflow/instances`

<table>
 <tbody>
  <tr>
   <td>HTTP-Anforderungsmethode</td>
   <td>Aktionen</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Listet die verfügbaren Workflow-Instanzen auf.</td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td><p>Erstellt eine neue Workflow-Instanz. <br /> Die Parameter sind: - <code>model</code>: die ID (URI) des jeweiligen Workflow-Modells<br /> - <code>payloadType</code>: enthält den Nutzlasttyp (z. B. <code>JCR_PATH</code> oder URL).<br /> Die Nutzlast wird als Parameter gesendet <code>payload</code>. A <code>201</code> (<code>CREATED</code>) response is sent back with a location header containing the URL of the new workflow instance resource.</p> </td>
  </tr>
 </tbody>
</table>

#### Verwaltung einer Workflow-Instanz nach Status {#managing-a-workflow-instance-by-its-state}

Die folgenden HTTP-Anfragemethoden gelten für:

`http://localhost:4502/etc/workflow/instances.{state}`

| HTTP-Anforderungsmethode | Aktionen |
|---|---|
| `GET` | Listet die verfügbaren Workflow-Instanzen und deren Status auf ( `RUNNING`, `SUSPENDED``ABORTED` oder `COMPLETED`) |

#### Verwaltung einer Workflow-Instanz nach ID {#managing-a-workflow-instance-by-its-id}

Die folgenden HTTP-Anfragemethoden gelten für:

`http://localhost:4502/etc/workflow/instances/{id}`

<table>
 <tbody>
  <tr>
   <td>HTTP-Anforderungsmethode</td>
   <td>Aktionen</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Ruft die Instanzdaten (Definition und Metadaten) einschließlich der Verknüpfung zum jeweiligen Workflow-Modell ab.</td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td>Ändert den Status der Instanz. Der neue Status wird als Parameter gesendet <code>state</code> und muss einen der folgenden Werte aufweisen: <code>RUNNING</code>, <code>SUSPENDED</code>oder <code>ABORTED</code>.<br /> Wenn der neue Status nicht erreichbar ist (z. B. beim Aussetzen einer beendeten Instanz), wird eine <code>409</code> (<code>CONFLICT</code>) Antwort an den Client zurückgesendet.</td>
  </tr>
 </tbody>
</table>

### Verwaltung von Workflow-Modellen {#managing-workflow-models}

Die folgenden HTTP-Anfragemethoden gelten für:

`http://localhost:4502/etc/workflow/models`

<table>
 <tbody>
  <tr>
   <td>HTTP-Anforderungsmethode</td>
   <td>Aktionen</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Listet die verfügbaren Workflow-Modelle auf.</td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td>Erstellt ein neues Workflow-Modell. If the parameter <code>title</code> is sent, a new model is created with the specified title. Attaching a JSON model definition as parameter <code>model</code> creates a new workflow model according to the provided definition.<br /> Eine <code>201</code> Antwort (<code>CREATED</code>) wird mit einer Kopfzeile mit der URL der neuen Ressource des Workflow-Modells zurückgesendet.<br /> Dasselbe passiert, wenn eine Modelldefinition als Dateiparameter namens <code>modelfile</code>.<br /> Sowohl bei den Parametern <code>model</code> als auch bei den <code>modelfile</code> Parametern ist ein zusätzlicher Parameter erforderlich, der aufgerufen <code>type</code> wird, um das Serialisierungsformat zu definieren. Neue Serialisierungsformate können mithilfe der OSGi-API integriert werden. Ein Standard-JSON-Serializer wird mit der Workflow-Engine bereitgestellt. Er weist den Typ JSON auf. Unten sehen Sie ein Beispiel für das Format.</td>
  </tr>
 </tbody>
</table>

Example: in the browser, a request to `http://localhost:4502/etc/workflow/models.json` generates a json response similar to the following:

```
[
    {"uri":"/var/workflow/models/activationmodel"}
    ,{"uri":"/var/workflow/models/dam/adddamsize"}
    ,{"uri":"/var/workflow/models/cloudconfigs/dtm-reactor/library-download"}
    ,{"uri":"/var/workflow/models/ac-newsletter-workflow-simple"}
    ,{"uri":"/var/workflow/models/dam/dam-create-language-copy"}
    ,{"uri":"/var/workflow/models/dam/dam-create-and-translate-language-copy"}
    ,{"uri":"/var/workflow/models/dam-indesign-proxy"}
    ,{"uri":"/var/workflow/models/dam-xmp-writeback"}
    ,{"uri":"/var/workflow/models/dam-parse-word-documents"}
    ,{"uri":"/var/workflow/models/dam/process_subasset"}
    ,{"uri":"/var/workflow/models/dam/dam_set_last_modified"}
    ,{"uri":"/var/workflow/models/dam/dam-autotag-assets"}
    ,{"uri":"/var/workflow/models/dam/update_asset"}
    ,{"uri":"/var/workflow/models/dam/update_asset_offloading"}
    ,{"uri":"/var/workflow/models/dam/dam-update-language-copy"}
    ,{"uri":"/var/workflow/models/dam/update_from_lightbox"}
    ,{"uri":"/var/workflow/models/cloudservices/DTM_bundle_download"}
    ,{"uri":"/var/workflow/models/dam/dam_download_asset"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-encode-video"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-thumbnail-replacement"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail"}
    ,{"uri":"/var/workflow/models/newsletter_bounce_check"}
    ,{"uri":"/var/workflow/models/projects/photo_shoot_submission"}
    ,{"uri":"/var/workflow/models/projects/product_photo_shoot"}
    ,{"uri":"/var/workflow/models/projects/approval_workflow"}
    ,{"uri":"/var/workflow/models/prototype-01"}
    ,{"uri":"/var/workflow/models/publish_example"}
    ,{"uri":"/var/workflow/models/publish_to_campaign"}
    ,{"uri":"/var/workflow/models/screens/publish_to_author_bin"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_publish_to_youtube"}
    ,{"uri":"/var/workflow/models/projects/request_copy"}
    ,{"uri":"/var/workflow/models/projects/request_email"}
    ,{"uri":"/var/workflow/models/projects/request_landing_page"}
    ,{"uri":"/var/workflow/models/projects/request_launch"}
    ,{"uri":"/var/workflow/models/request_for_activation"}
    ,{"uri":"/var/workflow/models/request_for_deactivation"}
    ,{"uri":"/var/workflow/models/request_for_deletion"}
    ,{"uri":"/var/workflow/models/request_for_deletion_without_deactivation"}
    ,{"uri":"/var/workflow/models/request_to_complete_move_operation"}
    ,{"uri":"/var/workflow/models/reverse_replication"}
    ,{"uri":"/var/workflow/models/salesforce-com-export"}
    ,{"uri":"/var/workflow/models/scene7"}
    ,{"uri":"/var/workflow/models/scheduled_activation"}
    ,{"uri":"/var/workflow/models/scheduled_deactivation"}
    ,{"uri":"/var/workflow/models/screens/screens-update-asset"}
    ,{"uri":"/var/workflow/models/translation"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_remove_from_youtube"}
    ,{"uri":"/var/workflow/models/wcm-translation/create_language_copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/prepare_translation_project"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-i18n-dictionary"}
    ,{"uri":"/var/workflow/models/wcm-translation/sync_translation_job"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-language-copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/update_language_copy"}
]
```

#### Verwaltung eines bestimmten Workflow-Modells {#managing-a-specific-workflow-model}

Die folgenden HTTP-Anfragemethoden gelten für:

`http://localhost:4502*{uri}*`

Where `*{uri}*` is the path to the model node in the repository.

<table>
 <tbody>
  <tr>
   <td>HTTP-Anforderungsmethode</td>
   <td>Aktionen</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Ruft die <code>HEAD</code> Version des Modells ab (Definition und Metadaten).</td>
  </tr>
  <tr>
   <td><code>PUT</code></td>
   <td>Aktualisiert die <code>HEAD</code> Version des Modells (erstellt eine neue Version).<br /> Die vollständige Modelldefinition für die neue Version des Modells muss als Parameter namens <code>model</code>. Additionally a <code>type</code> parameter is needed as when creating new models and needs to have the value <code>JSON</code>.<br /> </td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td>Das gleiche Verhalten wie bei PUT. Needed because AEM widgets do not support <code>PUT</code> operations.</td>
  </tr>
  <tr>
   <td><code>DELETE</code></td>
   <td>Löscht das Modell. Um Firewall-/Proxy-Probleme zu lösen, wird ein <code>POST</code> mit einem <code>X-HTTP-Method-Override</code> Header-Eintrag mit Wert <code>DELETE</code> auch als <code>DELETE</code> Anfrage akzeptiert.</td>
  </tr>
 </tbody>
</table>

Example: in the browser, a request to `http://localhost:4502/var/workflow/models/publish_example.json` returns a `json` response that is similar to the following code:

```shell
{
  "id":"/var/workflow/models/publish_example",
  "title":"Publish Example",
  "version":"1.0",
  "description":"This example shows a simple review and publish process.",
  "metaData":
  {
    "multiResourceSupport":"true",
    "tags":"wcm,publish"
  },
  "nodes":
  [{
    "id":"node0",
    "type":"START",
    "title":"Start",
    "description":"The start node of the workflow.",
    "metaData":
    {
    }
  },
  {
    "id":"node1",
    "type":"PARTICIPANT",
    "title":"Validate Content",
    "description":"Validate the modified content.",
    "metaData":
    {
      "PARTICIPANT":"admin"
    }
  },
  {
    "id":"node2",
    "type":"PROCESS",
    "title":"Publish Content",
    "description":"Publish the modified content.",
    "metaData":
    {
      "PROCESS_AUTO_ADVANCE":"true",
      "PROCESS":"com.day.cq.wcm.workflow.process.ActivatePageProcess"
    }
  },
  {
    "id":"node3",
    "type":"END",
    "title":"End",
    "description":"The end node of the workflow.",
    "metaData":
    {
    }
  }],
  "transitions":
  [{
    "from":"node0",
    "to":"node1",
    "metaData":
    {
    }
  },
  {
    "from":"node1",
    "to":"node2",
    "metaData":
    {
    }
  },
  {
    "from":"node2",
    "to":"node3",
    "metaData":
    {
    }
  }
]}
```

#### Verwaltung eines Workflow-Modells nach Version {#managing-a-workflow-model-by-its-version}

Die folgenden HTTP-Anfragemethoden gelten für:

`http://localhost:4502/etc/workflow/models/{id}.{version}`

| HTTP-Anforderungsmethode | Aktionen |
|---|---|
| `GET` | Ruft die Daten des Modells in der angegebenen Version ab (sofern vorhanden). |

### Verwaltung von (Benutzer-)Posteingängen {#managing-user-inboxes}

Die folgenden HTTP-Anfragemethoden gelten für:

`http://localhost:4502/bin/workflow/inbox`

<table>
 <tbody>
  <tr>
   <td>HTTP-Anforderungsmethode</td>
   <td>Aktionen</td>
  </tr>
  <tr>
   <td><code>GET</code></td>
   <td>Listet die Arbeitselemente auf, die sich im Posteingang des Benutzers befinden, der durch die HTTP-Authentifizierungskopfzeilen identifiziert wird.</td>
  </tr>
  <tr>
   <td><code>POST</code></td>
   <td>Schließt das Arbeitselement ab, dessen URI als Parameter gesendet wird, <code>item</code> und leitet die entsprechende Workflow-Instanz an den nächsten Knoten weiter, der bzw. die vom Parameter definiert wird <code>route</code> oder <code>backroute</code> bei einem Schritt zurück.<br /> Wenn der Parameter gesendet <code>delegatee</code> <code>item</code> wird, wird das vom Parameter identifizierte Arbeitselement an den angegebenen Teilnehmer delegiert.</td>
  </tr>
 </tbody>
</table>

#### Verwaltung eines (Benutzer-) Posteingangs nach WorkItem-ID {#managing-a-user-inbox-by-the-workitem-id}

Die folgenden HTTP-Anfragemethoden gelten für:

`http://localhost:4502/bin/workflow/inbox/{id}`

| HTTP-Anforderungsmethode | Aktionen |
|---|---|
| `GET` | Ruft die Daten (Definition und Metadaten) des Posteingangs ab, der durch seine ID `WorkItem` identifiziert wird. |

## Beispiele {#examples}

### Abrufen einer Liste aller laufenden Workflows mit IDs {#how-to-get-a-list-of-all-running-workflows-with-their-ids}

Um eine Liste aller laufenden Workflows zu erhalten, führen Sie eine GET-Anfrage an folgende Adresse durch:

`http://localhost:4502/etc/workflow/instances.RUNNING.json`

#### Abrufen einer Liste aller laufenden Workflows mit IDs – REST mit curl {#how-to-get-a-list-of-all-running-workflows-with-their-ids-rest-using-curl}

Beispiel mit curl:

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/instances.RUNNING.json
```

The `uri` displayed in the results can be used as the instance `id` in other commands; for example:

```shell
[
    {"uri":"/etc/workflow/instances/server0/2017-03-08/request_for_activation_1"}
]
```

>[!NOTE]
>
>This `curl` command can be used with any [workflow status](/help/sites-administering/workflows.md#workflow-status-and-actions) in place of `RUNNING`.

### Ändern des Workflow-Titels {#how-to-change-the-workflow-title}

Um den **Workflow-Titel** zu ändern, der auf der Registerkarte **Instanzen** der Workflow-Konsole angezeigt wird, senden Sie einen `POST`-Befehl:

* in: `http://localhost:4502/etc/workflow/instances/{id}`

* mit den folgenden Parametern:

   * `action`: sein Wert muss: `UPDATE`
   * `workflowTitle`: der Workflow-Titel

#### Ändern des Workflow-Titels – REST mit curl {#how-to-change-the-workflow-title-rest-using-curl}

Beispiel mit curl:

```shell
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/{id}

# for example
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
```

### Auflisten aller Workflow-Modelle {#how-to-list-all-workflow-models}

Um eine Liste aller verfügbaren Workflow-Modelle zu erhalten, führen Sie eine GET-Anfrage an folgende Adresse durch:

`http://localhost:4502/etc/workflow/models.json`

#### Auflisten aller Workflow-Modelle – REST mit curl {#how-to-list-all-workflow-models-rest-using-curl}

Beispiel mit curl:

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/models.json
```

>[!NOTE]
>
>See also [Managing Workflow Models](#managing-workflow-models).

### Abrufen eines WorkflowSession-Objekts {#obtaining-a-workflowsession-object}

The `com.adobe.granite.workflow.WorkflowSession` class is adaptable from a `javax.jcr.Session` object or a `org.apache.sling.api.resource.ResourceResolver` object.

#### Abrufen eines WorkflowSession-Objekts – Java {#obtaining-a-workflowsession-object-java}

Verwenden Sie in einem JSP-Skript (oder Java-Code für eine Servlet-Klasse) das HTTP-Anfrageobjekt, um ein `SlingHttpServletRequest`-Objekt abzurufen. Dieses Objekt gewährt Ihnen Zugriff auf ein `ResourceResolver`-Objekt. Passen Sie das `ResourceResolver` Objekt an `WorkflowSession`.

```java
<%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false"
    import="com.adobe.granite.workflow.WorkflowSession,
  org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
%>
```

#### Abrufen eines WorkflowSession Objekts – ECMA-Skript {#obtaining-a-workflowsession-object-ecma-script}

Use the `sling` variable to obtain the `SlingHttpServletRequest` object that you use to obtain a `ResourceResolver` object. Adapt the `ResourceResolver` object to the `WorkflowSession` object.

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

### Erstellen, Lesen oder Löschen von Workflow-Modellen {#creating-reading-or-deleting-workflow-models}

Die folgenden Beispiele zeigen, wie Sie auf Workflow-Modelle zugreifen können:

* Der Code für die Java- und ECMA-Skripte verwendet die Methode `WorkflowSession.createNewModel`.
* Der curl-Befehl greift direkt anhand der URL auf das Modell zu.

Verwendete Beispiele:

1. Erstellen Sie ein Modell (mit der ID `/var/workflow/models/mymodel/jcr:content/model`).
1. Löschen Sie das Modell.

>[!NOTE]
>
>Deleting the model sets the `deleted` property of the model&#39;s `metaData` child node to `true`.
>
>Durch das Löschen wird der Modellknoten nicht entfernt.

Wenn ein neues Modell erstellt wird:

* The workflow model editor requires that models use a specific node structure below `/var/workflow/models`. The parent node of the model must be of the type `cq:Page` having a `jcr:content` node with the following property values:

   * `sling:resourceType`: `cq/workflow/components/pages/model`
   * `cq:template`: `/libs/cq/workflow/templates/model`
   Wenn Sie ein Modell erstellen, müssen Sie zunächst diesen `cq:Page`-Knoten erstellen und seinen `jcr:content`-Knoten als übergeordneten Knoten des Modellknotens verwenden.

* The `id` argument that some methods require for identifying the model is the absolute path of the model node in the repository:

   `/var/workflow/models/<*model_name>*/jcr:content/model`

   >[!NOTE]
   >
   >See [How to List all Workflow Models](#how-to-list-all-workflow-models).

#### Erstellen, Lesen oder Löschen von Workflow-Modellen – Java {#creating-reading-or-deleting-workflow-models-java}

```java
<%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" import="com.adobe.granite.workflow.WorkflowSession,
                 com.adobe.granite.workflow.model.WorkflowModel,
             org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
/* Create the parent page */
String modelRepo = new String("/var/workflow/models");
String modelTemplate = new String ("/libs/cq/workflow/templates/model");
String modelName = new String("mymodel");
Page modelParent = pageManager.create(modelRepo, modelName, modelTemplate, "My workflow model");

/* create the model */
String modelId = new String(modelParent.getPath()+"/jcr:content/model")
WorkflowModel model = wfSession.createNewModel("Made using Java",modelId);

/* delete the model */
wfSession.deleteModel(modelId);
%>
```

#### Erstellen, Lesen oder Löschen von Workflow-Modellen – ECMA-Skript {#creating-reading-or-deleting-workflow-models-ecma-script}

```
var resolver = sling.getRequest().getResource().getResourceResolver();
var wfSession = resolver.adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
var pageManager = resolver.adaptTo(Packages.com.day.cq.wcm.api.PageManager);

//create the parent page node
var workflowPage = pageManager.create("/var/workflow/models", "mymodel", "/libs/cq/workflow/templates/model", "Created via ECMA Script");
var modelId = workflowPage.getPath()+ "/jcr:content/model";
//create the model
var model = wfSession.createNewModel("My Model", modelId);
//delete the model
var model = wfSession.deleteModel(modelId);
```

#### Löschen eines Workflow-Modells – REST mit curl {#deleting-a-workflow-model-rest-using-curl}

```shell
# deleting the model by its id
curl -u admin:admin -X DELETE http://localhost:4502/etc/workflow/models/{id}
```

>[!NOTE]
>
>Aufgrund der erforderlichen Detailmenge gilt curl nicht als praktikabel für das Erstellen und/oder Lesen eines Modells.

### Herausfiltern von System-Workflows beim Prüfen des Workflow-Status {#filtering-out-system-workflows-when-checking-workflow-status}

You can use the [WorkflowStatus API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html) to retrieve information about the workflow status of a node.

Verschiedene Methoden haben den Parameter:

`excludeSystemWorkflows`

Sie können diesen Parameter auf `true` setzen, damit System-Workflows aus den Suchergebnissen ausgeschlossen werden.

You [can update the OSGi configuration](/help/sites-deploying/configuring-osgi.md) **Adobe Granite Workflow PayloadMapCache** that specifies the workflow `Models` to be considered as system workflows. Es gibt standardmäßig folgende (Laufzeit-) Workflow-Modelle:

* `/var/workflow/models/scheduled_activation/jcr:content/model`
* `/var/workflow/models/scheduled_deactivation/jcr:content/model`

### Automatisches Fortführen eines Teilnehmerschritts nach Zeitüberschreitung {#auto-advance-participant-step-after-a-timeout}

Wenn Sie einen **Teilnehmer**-Schritt fortführen müssen, der innerhalb eines festgelegten Zeitraums nicht abgeschlossen wurde, stehen Ihnen folgende Möglichkeiten zur Verfügung:

1. Implementieren Sie einen OSGI-Ereignis-Listener für die Erstellung und Bearbeitung von Aufgaben.
1. Geben Sie ein Zeitlimit an (Deadline) und erstellen Sie anschließend einen geplanten Sling-Auftrag, der zu diesem Zeitpunkt ausgelöst wird.
1. Erstellen Sie einen Auftrags-Handler, der benachrichtigt wird, wenn das Zeitlimit abgelaufen ist, und den Auftrag auslöst.

    Dieser Handler führt die erforderlichen Handlungen zum Auftrag durch, wenn dieser noch nicht abgeschlossen ist.

>[!NOTE]
>
>Die durchzuführende Handlung muss eindeutig definiert sein, damit diese Vorgehensweise möglich ist.

### Interaktion mit Workflow-Instanzen {#interacting-with-workflow-instances}

Hier sind einige grundlegende Beispiele, wie Sie (programmgesteuert) mit Workflow-Instanzen interagieren.

#### Interaktion mit Workflow-Instanzen – Java {#interacting-with-workflow-instances-java}

```java
// starting a workflow
WorkflowModel model = wfSession.getModel(workflowId);
WorkflowData wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
Workflow[] workflows workflows = wfSession.getAllWorkflows();
Workflow workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### Interaktion mit Workflow-Instanzen – ECMA-Skript {#interacting-with-workflow-instances-ecma-script}

```
// starting a workflow
var model = wfSession.getModel(workflowId);
var wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
var workflows = wfSession.getWorkflows(“RUNNING“);
var workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### Interaktion mit Workflow-Instanzen – REST mit curl {#interacting-with-workflow-instances-rest-using-curl}

* **Starten eines Workflows**

   ```shell
   # starting a workflow
   curl -d "model={id}&payloadType={type}&payload={payload}" http://localhost:4502/etc/workflow/instances
   
   # for example:
   curl -u admin:admin -d "model=/var/workflow/models/request_for_activation/jcr:content/model&payloadType=JCR_PATH&payload=/content/we-retail/us/en/products" http://localhost:4502/etc/workflow/instances
   ```

* **Auflisten der Instanzen**

   ```shell
   # listing the instances
   curl -u admin:admin http://localhost:4502/etc/workflow/instances.json
   ```

   Hierdurch werden alle Instanzen aufgelistet. Beispiel:

   ```shell
   [
       {"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_1"}
       ,{"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_2"}
   ]
   ```

   >[!NOTE]
   >
   >See [How to get a List of all Running Workflows](#how-to-get-a-list-of-all-running-workflows-with-their-ids) with their IDs for listing instances with a specific status.

* **Pausieren eines Workflows**

   ```shell
   # suspending a workflow
   curl -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **Fortsetzen eines Workflows**

   ```shell
   # resuming a workflow
   curl -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **Beenden einer Workflow-Instanz**

   ```shell
   # terminating a workflow
   curl -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

### Interaktion mit Arbeitselementen {#interacting-with-work-items}

Hier sind einige grundlegende Beispiele, wie Sie (programmgesteuert) mit Arbeitselementen interagieren.

#### Interaktion mit Arbeitselementen – Java {#interacting-with-work-items-java}

```java
// querying work items
WorkItem[] workItems = wfSession.getActiveWorkItems();
WorkItem workItem = wfSession.getWorkItem(id);

// getting routes
List<Route> routes = wfSession.getRoutes(workItem);

// delegating
Iterator<Participant> delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### Interaktion mit Arbeitselementen – ECMA-Skript {#interacting-with-work-items-ecma-script}

```
// querying work items
var workItems = wfSession.getActiveWorkItems();
var workItem = wfSession.getWorkItem(id);

// getting routes
var routes = wfSession.getRoutes(workItem);

// delegating
var delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### Interaktion mit Arbeitselementen – REST mit curl {#interacting-with-work-items-rest-using-curl}

* **Auflisten von Arbeitselementen aus dem Posteingang**

   ```shell
   # listing the work items
   curl -u admin:admin http://localhost:4502/bin/workflow/inbox
   ```

   Details zu Arbeitselementen, die sich derzeit im Posteingang befinden, werden aufgelistet. Beispiel:

   ```shell
   [{
       "uri_xss": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "uri": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "currentAssignee_xss": "workflow-administrators",
       "currentAssignee": "workflow-administrators",
       "startTime": 1519656289274,
       "payloadType_xss": "JCR_PATH",
       "payloadType": "JCR_PATH",
       "payload_xss": "/content/we-retail/es/es",
       "payload": "/content/we-retail/es/es",
       "comment_xss": "Process resource is null",
       "comment": "Process resource is null",
       "type_xss": "WorkItem",
       "type": "WorkItem"
     },{
       "uri_xss": "configuration/configure_analyticstargeting",
       "uri": "configuration/configure_analyticstargeting",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/securitychecklist",
       "uri": "configuration/securitychecklist",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/enable_collectionofanonymoususagedata",
       "uri": "configuration/enable_collectionofanonymoususagedata",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/configuressl",
       "uri": "configuration/configuressl",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     }
   ```

* **Delegieren von Arbeitselementen**

   ```xml
   # delegating
   curl -d "item={item}&delegatee={delegatee}" http://localhost:4502/bin/workflow/inbox
   
   # for example:
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_act_1&delegatee=administrators" http://localhost:4502/bin/workflow/inbox
   ```

   >[!NOTE]
   >
   >The `delegatee` must be a valid option for the workflow step.

* **Abschließen oder Fortführen von Arbeitselementen zum nächsten Schritt**

   ```xml
   # retrieve the list of routes; the results will be similar to {"results":1,"routes":[{"rid":"233123169","label":"End","label_xss":"End"}]}
   http://localhost:4502/etc/workflow/instances/<path-to-the-workitem>.routes.json
   
   # completing or advancing to the next step; use the appropriate route ID (rid value) from the above list
   curl -d "item={item}&route={route}" http://localhost:4502/bin/workflow/inbox
   
   # for example:
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_activation_1&route=233123169" http://localhost:4502/bin/workflow/inbox
   ```

### Warten auf Workflow-Ereignisse {#listening-for-workflow-events}

Verwenden Sie das OSGi-Ereignis-Framework, um auf Ereignisse zu warten, die die Klasse [`com.adobe.granite.workflow.event.WorkflowEvent`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/event/WorkflowEvent.html) definiert. Diese Klasse bietet auch einige nützliche Methoden zum Abrufen von Informationen über das Thema des Ereignisses. Beispielsweise gibt die Methode `getWorkItem` das `WorkItem`-Objekt für das Arbeitselement, das am Ereignis beteiligt ist, zurück.

Der folgende Beispielcode definiert einen Dienst, der auf Workflow-Ereignisse wartet und je nach Art des Ereignisses Aufgaben ausführt.

```java
package com.adobe.example.workflow.listeners;

import org.apache.sling.event.jobs.JobProcessor;
import org.apache.sling.event.jobs.JobUtil;

import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;

import com.adobe.granite.workflow.event.WorkflowEvent;
import com.adobe.granite.workflow.exec.WorkItem;

/**
 * The <code>WorkflowEventCatcher</code> class listens to workflow events.
 */
@Component(metatype=false, immediate=true)
@Service(value=org.osgi.service.event.EventHandler.class)
public class WorkflowEventCatcher implements EventHandler, JobProcessor {

 @Property(value=com.adobe.granite.workflow.event.WorkflowEvent.EVENT_TOPIC)
 static final String EVENT_TOPICS = "event.topics";

 private static final Logger logger = LoggerFactory.getLogger(WorkflowEventCatcher.class);

 public void handleEvent(Event event) {
  JobUtil.processJob(event, this);
 }

 public boolean process(Event event) {
  logger.info("Received event of topic: " + event.getTopic());
  String topic = event.getTopic();

  try {
   if (topic.equals(WorkflowEvent.EVENT_TOPIC)) {
    WorkflowEvent wfevent = (WorkflowEvent)event;
    String eventType = wfevent.getEventType();
    String instanceId = wfevent.getWorkflowInstanceId();

    if (instanceId != null) {
     //workflow instance events
     if (eventType.equals(WorkflowEvent.WORKFLOW_STARTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_RESUMED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_SUSPENDED_EVENT)) {
      // your code comes here...
     } else if (
       eventType.equals(WorkflowEvent.WORKFLOW_ABORTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_COMPLETED_EVENT)) {
      // your code comes here...
     }
     // workflow node event
     if (eventType.equals(WorkflowEvent.NODE_TRANSITION_EVENT)) {
      WorkItem currentItem = (WorkItem) event.getProperty(WorkflowEvent.WORK_ITEM);
      // your code comes here...
     }
    }
   }
  } catch(Exception e){
   logger.debug(e.getMessage());
   e.printStackTrace();
  }
  return true;
 }
}
```

