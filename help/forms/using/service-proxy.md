---
title: HTML5 forms Service Proxy
seo-title: HTML5 forms Service Proxy
description: HTML5 forms Service Proxy ist eine Konfiguration, um einen Proxy zum Sendedienst anzumelden. Um Service Proxy zu konfigurieren, geben Sie die URL des Sendedienstes über den Anforderungsparameter „submissionServiceProxy“ ein.
seo-description: HTML5 forms Service Proxy ist eine Konfiguration, um einen Proxy zum Sendedienst anzumelden. Um Service Proxy zu konfigurieren, geben Sie die URL des Sendedienstes über den Anforderungsparameter „submissionServiceProxy“ ein.
uuid: 42d6c1da-3945-469d-b429-c33e563ed70c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 081f7c17-4e5d-4c7e-a5c3-5541a29b9d55
docset: aem65
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 92%

---


# HTML5 forms Service Proxy{#html-forms-service-proxy}

HTML5 forms Service Proxy ist eine Konfiguration, um einen Proxy zum Sendedienst anzumelden. Um Service Proxy zu konfigurieren, geben Sie die URL des Sendedienstes über den Anforderungsparameter *„submissionServiceProxy“* ein.

## Vorteile des Service Proxy {#benefits-of-service-proxy-br}

Der Service Proxy eliminiert Folgendes:

* Der Arbeitsablauf von HTML5-Formularen erfordert Öffnen des Sendedienstes „//content/xfaforms/submission/default“ für HTML5-Formularbenutzer. AEM-Server werden für eine größere Anzahl von Personen unbeabsichtigt bereitgestellt.
* Die Dienst-URL ist in das Laufzeitmodell des Formulars eingebettet. Es ist nicht möglich, den Pfad der Dienst-URL zu ändern.
* Der Sendevorgang geschieht in zwei Schritten. Um die Formulardaten zu senden, sind mindestens zwei Wege zum Server erforderlich. Dadurch wird der Server stärker belastet.
* HTML5-Formulare senden Daten über eine POST-Anforderung statt über eine PDF-Anforderung. Für Arbeitsabläufe, die sowohl PDF- als auch HTML5-Formulare beinhalten, sind zwei unterschiedliche Methoden für die Sendeverarbeitung erforderlich.

### Topologien {#topologies-br}

HTML5-Formulare können folgende Topologien für die Verbindung zum AEM-Server verwenden.

* Eine Topologie, bei der AEM-Server oder HTML5-Formulare Daten über POST an den Server senden.
* Eine Topologie, bei der der Proxy-Server POST-Daten an den Server sendet.

![HTML5 forms Service Proxy-Topologien](assets/topology.png)

HTML5 forms Service Proxy-Topologien

HTML5-Formulare stellen eine Verbindung zu den AEM-Servern her, um serverseitige Skripte, Webdienste und Sendevorgänge auszuführen. Die XFA-Laufzeitumgebung der HTML5-Formulare verwendet Ajax-Aufrufe am Endpunkt „//bin/xfaforms/submitaction“ mit verschiedenen Parametern, um eine Verbindung zu den AEM-Servern herzustellen. HTML5-Formulare stellen eine Verbindung zu den AEM-Servern für folgende Vorgänge her:

#### Ausführen von serverseitigen Skripten und Webdiensten {#execute-server-sided-scripts-and-web-services}

Die Skripte, die für eine Ausführung auf dem Server markiert sind, werden als serverseitige Skripte bezeichnet. In der folgenden Tabelle werden alle in serverseitigen Skripten und Webdiensten verwendeten Parameter Liste.

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>activity</p> </td>
   <td><p>Activity enthält Ereignisse, die eine Anforderung auslösen. Z. B. „Click“, „Exit“ oder „Change“</p> </td>
  </tr>
  <tr>
   <td><p>contextSom</p> </td>
   <td><p>contextSom enthält SOM-Ausdruck des Objekts für das Ereignisse ausgeführt werden.</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>„Template“ enthält eine Vorlage zum Rendern des Formulars. </p> </td>
  </tr>
  <tr>
   <td><p>contentRoot</p> </td>
   <td><p>„contentRoot“ enthält den Vorlagen-Stammordner zum Rendern des Formulars. </p> </td>
  </tr>
  <tr>
   <td><p>Daten</p> </td>
   <td><p>„Data“ enthält Datenbytes zum Rendern des Formulars. </p> </td>
  </tr>
  <tr>
   <td><p>formDom</p> </td>
   <td><p>„formDom“ enthält DOM von HTML5-Formularen im JSON-Format. </p> </td>
  </tr>
  <tr>
   <td><p>packet</p> </td>
   <td><p>packet wird als Formular angegeben.</p> </td>
  </tr>
  <tr>
   <td><p>debugDir</p> </td>
   <td><p>debugDir enthält das Debug-Ordner zum Rendern des Formulars.</p> </td>
  </tr>
 </tbody>
</table>

#### Daten senden  {#submit-data}

Wenn auf die Schaltfläche „Senden“ geklickt wird, senden HTML5-Formulare Daten zum Server. Die folgende Tabelle listet alle Parameter auf, die HTML5-Formulare an den Server senden.

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>Vorlage zum Rendern des Formulars.</p> </td>
  </tr>
  <tr>
   <td><p>contentRoot</p> </td>
   <td><p>Vorlagen-Stammordner zum Rendern des Formulars.</p> </td>
  </tr>
  <tr>
   <td><p>Daten</p> </td>
   <td><p>Datenbytes zum Rendern des Formulars.</p> </td>
  </tr>
  <tr>
   <td><p>formDom</p> </td>
   <td><p>DOM des HTML5-Formulars im JSON-Format.</p> </td>
  </tr>
  <tr>
   <td><p>submitUrl</p> </td>
   <td><p>URL, an die die XML-Daten gesendet werden.</p> </td>
  </tr>
  <tr>
   <td><p>debugDir</p> </td>
   <td><p>Debug-Ordner zum Rendern des Formulars.</p> </td>
  </tr>
 </tbody>
</table>

#### Wie funktioniert der Sende-Proxy?  {#how-nbsp-the-nbsp-submit-proxy-works}

Der Sendedienst-Proxy fungiert als Pass-Through, wenn die submitUrl nicht in den Anforderungsparametern enthalten ist. Er fungiert als Pass-Through. Er sendet die Anforderung zum Endpunkt „//bin/xfaforms/submitaction“ und die Antwort zur XFA-Laufzeitumgebung.

Der Sendedienst-Proxy wählt eine Topologie, wenn die submitUrl in den Anforderungsparametern enthalten ist.

* Wenn AEM-Server Daten senden, dient der Proxy-Dienst als Pass-Through. Er sendet die Anforderung zum Endpunkt „//bin/xfaforms/submitaction“ und die Antwort zur XFA-Laufzeitumgebung.
* Wenn der Proxy die Daten sendet, übergibt der Proxy-Dienst alle Parameter außer submitUrl an den Endpunkt */bin/xfaforms/submitaction* und empfängt XML-Bytes im Antwortstream. Dann sendet der Proxy-Dienst die XML-Datenbytes an die submitUrl zur Verarbeitung.

* Vor dem Versenden der Daten (POST-Anforderung) an einen Server prüfen HTML5-Formulare die Verbindung und Verfügbarkeit des Servers. Um die Verbindung und Verfügbarkeit zu prüfen, senden HTML-Formulare eine leere HEAD-Anforderung an den Server. Wenn der Server verfügbar ist, sendet das HTML5-Formular Daten (POST-Anforderung) an den Server. Wenn der Server nicht verfügbar ist, wird eine Fehlermeldung angezeigt: *Keine Verbindung mit dem Server möglich,*. Durch die erweiterte Erkennung müssen Benutzer das Formular nicht stets von Neuem ausfüllen. Das Proxy-Servlet verarbeitet HEAD-Anforderungen und löst keine Ausnahme aus.
