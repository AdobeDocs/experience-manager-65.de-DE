---
title: „[!DNL Assets]-Proxy-Entwicklung“
description: Ein Proxy ist eine [!DNL Experience Manager] -Instanz, die Proxy-Worker verwendet, um Aufträge zu verarbeiten. Erfahren Sie, wie Sie einen  [!DNL Experience Manager] -Proxy konfigurieren und einen benutzerdefinierten Proxy-Worker entwickeln können, und erhalten Sie Informationen zu unterstützten Vorgängen und Proxy-Komponenten.
contentOwner: AG
role: Admin, Architect
exl-id: 42fff236-b4e1-4f42-922c-97da32a933cf
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 95%

---

# [!DNL Assets]-Proxy-Entwicklung {#assets-proxy-development}

[!DNL Adobe Experience Manager Assets] verwendet einen Proxy, um die Verarbeitung bestimmter Aufgaben zu verteilen.

Ein Proxy ist eine bestimmte (und gelegentlich separate) Experience Manager-Instanz, die Proxy-Worker als Prozessoren verwendet, um Aufträge zu bearbeiten und Ergebnisse zu generieren. Ein Proxy-Worker kann für eine Vielzahl von Aufgaben verwendet werden. Wenn eine [!DNL Assets] Proxy, der zum Laden von Assets zum Rendern in Assets verwendet werden kann. Beispielsweise verarbeitet der [IDS-Proxy-Worker](indesign.md) Dateien, die in Assets verwendet werden sollen, mit einem [!DNL Adobe InDesign]-Server.

Wenn der Proxy eine separate [!DNL Experience Manager]-Instanz ist, wird die Last für die [!DNL Experience Manager]-Autorinstanz(en) reduziert. Standardmäßig führt [!DNL Assets] die Aufgaben zur Asset-Verarbeitung in derselben JVM (externalisiert über Proxy) aus, um die Last für die [!DNL Experience Manager]-Autorinstanz zu reduzieren.

## Proxy (HTTP-Zugriff) {#proxy-http-access}

Ein Proxy ist über das HTTP-Servlet verfügbar, wenn es für die Annahme von Verarbeitungsvorgängen konfiguriert ist unter: `/libs/dam/cloud/proxy`. Dieses Servlet erstellt einen Sling-Auftrag aus den geposteten Parametern. Der Auftrag wird dann der Proxy-Auftragswarteschlange hinzugefügt und mit dem entsprechenden Proxy-Worker verbunden.

### Unterstützte Vorgänge {#supported-operations}

* `job`

  **Anforderungen**: Der Parameter `jobevent` muss als serialisierte Wertezuordnung festgelegt werden. Damit wird ein `Event` für einen Auftragsprozessor erstellt.

  **Ergebnis**: Fügt einen neuen Auftrag hinzu. Wenn der Vorgang erfolgreich ist, wird eine eindeutige Auftrags-ID zurückgegeben.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

  **Anforderungen**: Der Parameter `jobid` muss festgelegt werden.

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

### Proxy-Worker {#proxy-worker}

Ein Proxy-Worker ist ein Prozessor, der für die Verarbeitung von Aufträgen und die Generierung von Ergebnissen zuständig ist. Worker befinden sich auf der Proxy-Instanz und müssen [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) implementieren, damit sie als Proxy-Worker erkannt werden.

>[!NOTE]
>
>Worker müssen [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) implementieren, damit sie als Proxy-Worker erkannt werden.

### Client-API {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html) ist als OSGi-Dienst verfügbar, der Methoden zur Erstellung und Entfernung von Aufträgen und dem Abruf von Ergebnissen aus den Aufträgen bereitstellt. Die Standardimplementierung des Service (`JobServiceImpl`) verwendet den HTTP-Client für die Kommunikation mit dem Remote-Proxy-Servlet.

Nachstehend finden Sie ein Beispiel für die API-Verwendung:

```java
@Reference
 JobService proxyJobService;

 // to create a job
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

### Cloud Service-Konfigurationen {#cloud-service-configurations}

<!-- TBD: Cannot find com.day.cq.dam.api.proxy at https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html which were generated in May 2020. Hiding this broken link for now.
>[!NOTE]
>
>Reference documentation for the proxy API is available under [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/proxy/package-summary.html).
-->

Proxy- und Proxy-Worker-Konfigurationen sind über Cloud-Service-Konfigurationen verfügbar, die in der **Tools**-Konsole von [!DNL Assets] verfügbar sind oder unter `/etc/cloudservices/proxy`. Von jedem Proxy-Worker wird erwartet, dass er einen Knoten unter `/etc/cloudservices/proxy` für Worker-spezifische Konfigurationsdetails (z. B. `/etc/cloudservices/proxy/workername`) hinzufügt.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Konfiguration von InDesign Server Proxy-Worker](indesign.md#configuring-the-proxy-worker-for-indesign-server) und [Cloud Service-Konfiguration](../sites-developing/extending-cloud-config.md).

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

### Entwickeln eines benutzerdefinierten Proxy-Workers {#developing-a-customized-proxy-worker}

Der [IDS-Proxy-Worker](indesign.md) ist ein Beispiel für einen [!DNL Assets]-Proxy-Worker, der vorkonfiguriert bereitgestellt wird, um die Verarbeitung der InDesign-Assets auszulagern.

Sie können auch einen eigenen [!DNL Assets]-Proxy-Worker für entwickeln und konfigurieren. Dieser spezialisierte Worker kann die Verarbeitungsaufgaben von [!DNL Assets] verteilen und auslagern.

Für die Einrichtung eines eigenen benutzerdefinierten Proxy-Workers müssen Sie die folgenden Aufgaben ausführen:

* Einrichten und Implementieren (mit Sling Eventing): 

   * ein Thema für den benutzerdefinierten Auftrag
   * einen Ereignis-Handler für benutzerdefinierte Aufträge

* Verwenden Sie dann die JobService-API, um:

   * benutzerdefinierten Auftrag an Proxy senden
   * Ihren Auftrag zu verwalten

* Wenn Sie den Proxy aus einem Workflow verwenden möchten, müssen Sie einen benutzerdefinierten, externen Schritt mithilfe der WorkflowExternalProcess-API und der JobService-API implementieren.

Das folgende Diagramm und die folgenden Schritte beschreiben den weiteren Ablauf:

![chlimage_1-249](assets/chlimage_1-249.png)

>[!NOTE]
>
>In den folgenden Schritten werden InDesign-Äquivalente als Referenzbeispiele angegeben.

1. Da ein [Sling-Auftrag](https://sling.apache.org/site/eventing-and-jobs.html) verwendet wird, müssen Sie ein Auftragsthema für Ihren Anwendungsfall definieren.

   Als Beispiel dient `IDSJob.IDS_EXTENDSCRIPT_JOB` für den IDS-Proxy-Worker.

1. Mit dem externen Schritt wird das Ereignis ausgelöst, anschließend wird auf den Abschluss gewartet. Hierfür wird die ID abgerufen. Entwickeln Sie Ihren eigenen Schritt, um neue Funktionen zu implementieren.

   Implementieren Sie einen `WorkflowExternalProcess`. Bereiten Sie dann mit der JobService-API und Ihrem Auftragsthema ein Auftragsereignis vor und senden Sie es an den JobService (einen OSGi-Dienst). 

   Als Beispiel dient `INDDMediaExtractProcess`.java für den IDS-Proxy-Worker.

1. Implementieren Sie einen Auftrags-Handler für Ihr Thema. Der Handler muss entwickelt werden, damit er die von Ihnen gewünschte spezifische Aktion ausführt und als Worker-Implementierung betrachtet wird. 

   Als Beispiel dient `IDSJobProcessor.java` für den IDS-Proxy-Worker.

1. Verwenden Sie `ProxyUtil.java` in dam-commons. Damit können Sie Aufträge mit dem dam-Proxy an Worker senden.

>[!NOTE]
>
>Das Proxy-Framework von [!DNL Assets] stellt keinen vorkonfigurierten Pool-Mechanismus bereit.
>
>Die Integration mit [!DNL InDesign] ermöglicht jedoch den Zugriff auf einen Pool von [!DNL InDesign]-Servern (IDSPool). Dieses Pooling ist spezifisch für die [!DNL InDesign]-Integration und ist kein Teil des Proxy-Frameworks von [!DNL Assets].

>[!NOTE]
>
>Synchronisierung der Ergebnisse:
>
>Bei n Instanzen, die denselben Proxy verwenden, bleibt das Verarbeitungsergebnis beim Proxy. Der Client (Experience Manager-Autor) hat die Aufgabe, das Ergebnis anzufordern. Dabei wird dieselbe eindeutige Auftrags-ID verwendet, die dem Client beim Erstellen des Auftrags zugewiesen wurde. Der Proxy erledigt einfach den Auftrag und hält das Ergebnis abrufbereit.
