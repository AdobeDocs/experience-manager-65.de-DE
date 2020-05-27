---
title: Asset Proxy-Entwicklung
description: Ein Proxy ist eine Experience Manager-Instanz, die Proxyarbeiter zur Verarbeitung von Aufträgen verwendet. Erfahren Sie, wie Sie einen Experience Manager-Proxy konfigurieren, unterstützte Vorgänge, Proxykomponenten und einen benutzerdefinierten Proxy-Worker entwickeln.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 56%

---


# Assets proxy development {#assets-proxy-development}

Adobe Experience Manager Assets verwendet einen Proxy, um die Verarbeitung für bestimmte Aufgaben zu verteilen.

Bei einem Proxy handelt es sich um eine spezifische (und manchmal auch separate) Experience Manager-Instanz, bei der Proxyarbeiter als Prozessoren verwendet werden, die für die Verarbeitung eines Auftrags und das Erstellen eines Ergebnisses zuständig sind. Ein Proxy Worker kann für eine Vielzahl von Aufgaben verwendet werden. Bei einem Assets-Proxy kann dies zum Laden von Assets zum Rendern in Assets verwendet werden. For example, the [IDS proxy worker](indesign.md) uses an [!DNL Adobe InDesign] Server to process files for use in Assets.

Wenn der Proxy eine separate Experience Manager-Instanz ist, wird dadurch die Belastung der Experience Manager-Authoring-Instanz(en) verringert. Standardmäßig führt Assets die Asset-Verarbeitungs-Aufgaben in derselben JVM aus (über Proxy extern übertragen), um die Belastung der Experience Manager-Authoring-Instanz zu verringern.

## Proxy (HTTP-Zugriff) {#proxy-http-access}

Proxys, deren Konfiguration Verarbeitungsaufträge zulässt, sind über das HTTP-Servlet verfügbar: `/libs/dam/cloud/proxy`. Dieses Servlet erstellt einen Sling-Auftrag aus den geposteten Parametern. Der Auftrag wird dann der Proxy-Auftragswarteschlange hinzugefügt und mit dem entsprechenden Proxy Worker verbunden.

### Unterstützte Vorgänge {#supported-operations}

* `job`

   **Anforderungen**: Der Parameter `jobevent` muss als serialisierte Wertezuordnung festgelegt werden. This is used to create an `Event` for a job processor.

   **Ergebnis**: Fügt einen neuen Auftrag hinzu. Wenn der Vorgang erfolgreich ist, wird eine eindeutige Auftrags-ID zurückgegeben.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **Anforderungen**: der Parameter `jobid` muss eingestellt werden.

   **Ergebnis:** Gibt die JSON-Darstellung des Ergebnisknotens zurück, wie er durch den Auftragsprozessor erstellt wurde.

```shell
curl -u admin:admin -F":operation=result" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502   /libs/dam/cloud/proxy
```

* `resource`

   **Anforderungen**: Der Parameter „jobid“ must festgelegt sein.

   **Ergebnis**: Gibt eine Ressource zurück, die dem jeweiligen Auftrag zugeordnet ist.

```shell
curl -u admin:admin -F":operation=resource" -F"jobid=xxxxxxxxxxxx"
    -F"resourcePath=something.pdf" http://localhost:4502/libs/dam/cloud/proxy
```

* `remove`

   **Anforderungen**: Der Parameter „jobid“ must festgelegt sein.

   **Ergebnisse:**: Entfernt einen gefundenen Auftrag.

```shell
curl -u admin:admin -F":operation=remove" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502/libs/dam/cloud/proxy
```

### Proxy Worker {#proxy-worker}

Ein Proxy Worker ist ein Prozessor, der für die Verarbeitung von Aufträgen und die Generierung von Ergebnissen zuständig ist. Worker befinden sich auf der Proxy-Instanz und müssen [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) implementieren, damit sie als Proxy Worker erkannt werden.

>[!NOTE]
>
>Worker müssen [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) implementieren, damit sie als Proxy Worker erkannt werden.

### Client-API {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html) ist als OSGi-Dienst verfügbar, der Methoden zur Erstellung und Entfernung von Aufträgen und dem Abruf von Ergebnissen aus den Aufträgen bereitstellt. Die Standardimplementierung des Dienstes (`JobServiceImpl`) verwendet den HTTP-Client für die Kommunikation mit dem Remote-Proxy-Servlet.

Nachstehend finden Sie ein Beispiel für die API-Verwendung:

```java
@Reference
 JobService proxyJobService;

 // to create a new job
 final Hashtable props = new Hashtable();
 props.put("someproperty", "some value");
 props.put(JobUtil.PROPERTY_JOB_TOPIC, "myworker/job"); // this is an identifier of the worker
 final String jobId = proxyJobService.addJob(props, new Asset[]{asset});

 // to check status (returns JobService.STATUS_FINISHED or JobService.STATUS_INPROGRESS)
 int status = proxyJobService.getStatus(jobId)

 // to get the result
 final String jsonString = proxyJobService.getResult(jobId);

 // to remove job and cleanup
 proxyJobService.removeJob(jobId);
```

### Cloud-Service-Konfigurationen {#cloud-service-configurations}

>[!NOTE]
>
>Die Referenzdokumentation für die Proxy-API ist unter [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/proxy/package-summary.html) verfügbar.

Both proxy and proxy worker configurations are available via cloud services configurations as accessible from the Assets **Tools** console or under `/etc/cloudservices/proxy`. Es wird erwartet, dass jeder Proxy-Worker einen Knoten `/etc/cloudservices/proxy` für arbeitnehmerspezifische Konfigurationsdetails (z. B. `/etc/cloudservices/proxy/workername`) hinzufügt.

>[!NOTE]
>
>See [InDesign Server Proxy Worker configuration](indesign.md#configuring-the-proxy-worker-for-indesign-server) and [Cloud Services configuration](../sites-developing/extending-cloud-config.md) for more information.

Nachstehend finden Sie ein Beispiel für die API-Verwendung:

```java
@Reference(policy = ReferencePolicy.STATIC)
 ProxyConfig proxyConfig;

 // to get proxy config
 Configuration cloudConfig = proxyConfig.getConfiguration();
 final String value = cloudConfig.get("someProperty", "defaultValue");

 // to get worker config
 Configuration cloudConfig = proxyConfig.getConfiguration("workername");
 final String value = cloudConfig.get("someProperty", "defaultValue");
```

### Entwickeln eines benutzerdefinierten Proxy Workers {#developing-a-customized-proxy-worker}

The [IDS proxy worker](indesign.md) is an example of a Assets proxy worker that is already provided out-of-the-box to outsource the processing of InDesign assets.

Sie können auch Ihren eigenen Assets-Proxy-Mitarbeiter entwickeln und konfigurieren, um einen spezialisierten Mitarbeiter zum Dispatch und Outsourcing Ihrer Assets-Verarbeitungs-Aufgaben zu erstellen.

Für die Einrichtung eines eigenen benutzerdefinierten Proxy Workers müssen Sie die folgenden Aufgaben ausführen:

* Einrichten und Implementieren (mit Sling Eventing): 

   * benutzerdefiniertes Auftragsthema
   * benutzerdefinierter Auftrags-Ereignishandler

* Führen Sie mit der JobService-API die folgenden Aufgaben aus:

   * benutzerdefinierten Auftrag an Proxy senden
   * Auftrag verwalten

* Wenn Sie den Proxy aus einem Workflow verwenden möchten, müssen Sie einen externen benutzerdefinierten Schritt implementieren. Verwenden Sie dafür die WorkflowExternalProcess-API und die JobService-API.

Die Vorgehensweise wird im folgenden Diagramm erläutert:

![chlimage_1-249](assets/chlimage_1-249.png)

>[!NOTE]
>
>In den folgenden Schritten werden InDesign-Entsprechungen als Referenzbeispiele angezeigt.

1. Da ein [Sling-Auftrag](https://sling.apache.org/site/eventing-and-jobs.html) verwendet wird, müssen Sie ein Auftragsthema für Ihren Anwendungsfall definieren.

   Als Beispiel dient `IDSJob.IDS_EXTENDSCRIPT_JOB` für den IDS Proxy Worker.

1. Mit dem externen Schritt wird das Ereignis ausgelöst, anschließend wird auf den Abschluss gewartet. Hierfür wird die ID abgerufen. Sie müssen einen eigenen Schritt entwickeln, um eine neue Funktionalität zu implementieren. 

   Implementieren Sie einen `WorkflowExternalProcess`. Bereiten Sie dann mit der JobService-API und Ihrem Auftragsthema ein Auftragsereignis vor und senden Sie es an den JobService (einen OSGi-Dienst). 

   Als Beispiel dient `INDDMediaExtractProcess` für den IDS Proxy Worker.

1. Implementieren Sie einen Auftrags-Handler für Ihr Thema. Der Handler muss entwickelt werden, damit er die von Ihnen gewünschte spezifische Aktion ausführt und als Worker-Implementierung betrachtet wird. 

   Als Beispiel dient `IDSJobProcessor.java` für den IDS Proxy Worker.

1. Verwenden Sie `ProxyUtil.java` in dam-commons. Damit können Sie Aufträge mit dem dam-Proxy an Worker senden.

>[!NOTE]
>
>Was das Assets-Proxy-Framework nicht standardmäßig bereitstellt, ist der Poolmechanismus.
>
>The [!DNL InDesign] integration allows the access of a pool of [!DNL InDesign] servers (IDSPool). This pooling is specific to [!DNL InDesign] integration and not part of the [!DNL Assets] proxy framework.

>[!NOTE]
>
>Synchronisierung der Ergebnisse:
>
>Bei n Instanzen, die denselben Proxy verwenden, bleibt das Verarbeitungsergebnis beim Proxy. Es ist Aufgabe des Clients (Experience Manager Author), das Ergebnis mit derselben eindeutigen Job-ID anzufordern, die dem Client bei der Auftragserstellung gegeben wird. Der Proxy erledigt einfach den Auftrag und hält das Ergebnis abrufbereit.
