---
title: HTML5 Forms-Service-Proxy
description: HTML5 forms Service Proxy ist eine Konfiguration, um einen Proxy zum Sendedienst anzumelden. Um den Dienst-Proxy zu konfigurieren, geben Sie die URL des Übermittlungsdienstes über den Anfrageparameter „submissionServiceProxy“ an.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms
exl-id: 8f9b10ae-1600-49c2-a061-153a2a89c67e
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 100%

---

# HTML5 Forms-Service-Proxy{#html-forms-service-proxy}

HTML5 forms Service Proxy ist eine Konfiguration, um einen Proxy zum Sendedienst anzumelden. Um den Dienst-Proxy zu konfigurieren, geben Sie die URL des Übermittlungsdienstes über den Anfrageparameter *submissionServiceProxy* an.

## Vorteile des Service Proxy {#benefits-of-service-proxy-br}

Der Service Proxy eliminiert Folgendes:

* Der Arbeitsablauf von HTML5-Formularen erfordert Öffnen des Sendedienstes „//content/xfaforms/submission/default“ für HTML5-Formularbenutzer. Hierdurch werden AEM-Server einem breiteren, unbeabsichtigten Publikum zugänglich gemacht.
* Die Dienst-URL ist in das Laufzeitmodell des Formulars eingebettet. Der Pfad der Dienst-URL kann nicht geändert werden.
* Die Übermittlung erfolgt in zwei Schritten. Zur Übermittlung der Formulardaten sind mindestens zwei Übermittlungen zum Server erforderlich. Dadurch erhöht sich die Server-Auslastung.
* HTML5-Formulare senden Daten über eine POST-Anforderung statt über eine PDF-Anforderung. Für Arbeitsabläufe, die sowohl PDF- als auch HTML5-Formulare beinhalten, sind zwei unterschiedliche Methoden für die Sendeverarbeitung erforderlich.

### Topologien {#topologies-br}

HTML5-Formulare können die folgenden Topologien verwenden, um eine Verbindung zu den AEM-Servern herzustellen.

* Eine Topologie, bei der AEM Server oder HTML5-Formulare Daten per POST an den Server senden.
* Eine Topologie, bei der der Proxy-Server POST-Daten an den Server sendet.

![HTML5 forms Service Proxy-Topologien](assets/topology.png)

HTML5 Forms-Service-Proxy-Topologien

HTML5-Formulare stellen eine Verbindung zu den AEM-Servern her, um serverseitige Skripte, Webdienste und Sendevorgänge auszuführen. Die XFA-Laufzeitumgebung der HTML5-Formulare verwendet Ajax-Aufrufe am Endpunkt „//bin/xfaforms/submitaction“ mit verschiedenen Parametern, um eine Verbindung zu den AEM-Servern herzustellen. HTML5-Formulare verbinden AEM-Server, um die folgenden Vorgänge auszuführen:

#### Ausführen von Server-seitigen Skripten und Web-Diensten {#execute-server-sided-scripts-and-web-services}

Die zur Ausführung auf dem Server markierten Skripte werden als Server-seitige Skripte bezeichnet. Die folgende Tabelle listet alle Parameter auf, die in serverseitigen Skripten und Web-Diensten verwendet werden.

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>Aktivität</p> </td>
   <td><p>Aktivität enthält die Ereignisse, die die Anfrage auslösen. Zum Beispiel Klicken, Beenden oder Ändern</p> </td>
  </tr>
  <tr>
   <td><p>contextSom</p> </td>
   <td><p>contextSom enthält den SOM-Ausdruck des Objekts, in dem Ereignisse ausgeführt werden.</p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>Template enthält die Vorlage, die zum Rendern des Formulars verwendet wird.</p> </td>
  </tr>
  <tr>
   <td><p>contentRoot</p> </td>
   <td><p>contentRoot enthält das Stammverzeichnis der Vorlage, die zum Rendern des Formulars verwendet wird.</p> </td>
  </tr>
  <tr>
   <td><p>Daten</p> </td>
   <td><p>Data enthält Bata-Bytes, die zum Rendern des Formulars verwendet werden.</p> </td>
  </tr>
  <tr>
   <td><p>formDom</p> </td>
   <td><p>formDom enthält DOM des HTML5-Formulars im JSON-Format.</p> </td>
  </tr>
  <tr>
   <td><p>packet</p> </td>
   <td><p>packet wird als Formular angegeben.</p> </td>
  </tr>
  <tr>
   <td><p>debugDir</p> </td>
   <td><p>debugDir enthält das Debugging-Verzeichnis, das zum Rendern des Formulars verwendet wird.</p> </td>
  </tr>
 </tbody>
</table>

#### Absenden von Daten {#submit-data}

Wenn auf die Schaltfläche „Senden“ geklickt wird, senden HTML5-Formulare Daten zum Server. In der folgenden Tabelle sind alle Parameter aufgeführt, die HTML5-Formulare an den Server senden.

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>Vorlage</p> </td>
   <td><p>Vorlage, die zum Rendern des Formulars verwendet wird.</p> </td>
  </tr>
  <tr>
   <td><p>contentRoot</p> </td>
   <td><p>Stammverzeichnis der Vorlage, die zum Rendern des Formulars verwendet wird.</p> </td>
  </tr>
  <tr>
   <td><p>Daten</p> </td>
   <td><p>Bata-Bytes, die zum Rendern des Formulars verwendet werden.</p> </td>
  </tr>
  <tr>
   <td><p>formDom</p> </td>
   <td><p>DOM des HTML5-Formulars im JSON-Format.</p> </td>
  </tr>
  <tr>
   <td><p>submiturl</p> </td>
   <td><p>Die URL, unter der XML-Daten gepostet werden.</p> </td>
  </tr>
  <tr>
   <td><p>debugDir</p> </td>
   <td><p>Das Debugging-Verzeichnis, das zum Rendern des Formulars verwendet wird.</p> </td>
  </tr>
 </tbody>
</table>

#### Wie funktioniert der Sende-Proxy? {#how-nbsp-the-nbsp-submit-proxy-works}

Der Sendedienst-Proxy fungiert als Durchleitung, wenn die submiturl nicht im Anfrageparameter vorhanden ist. Er fungiert als Durchleitung. Er sendet die Anforderung zum Endpunkt „/bin/xfaforms/submitaction“ und die Antwort zur XFA-Laufzeitumgebung.

Der Sendedienst-Proxy wählt eine Topologie aus, wenn die submiturl im Anfrageparameter vorhanden ist.

* Wenn AEM-Server Daten senden, dient der Proxy-Dienst als Pass-Through. Er sendet die Anforderung zum Endpunkt „//bin/xfaforms/submitaction“ und die Antwort zur XFA-Laufzeitumgebung.
* Wenn der Proxy die Daten sendet, reicht der Proxy-Service alle Parameter außer submitUrl an den Endpunkt */bin/xfaforms/submitaction* weiter und empfängt XML-Bytes als Antwort-Stream. Dann sendet der Proxy-Dienst die XML-Datenbytes an die submitUrl zur Verarbeitung.

* Vor dem Versenden der Daten (POST-Anforderung) an einen Server prüfen HTML5-Formulare die Verbindung und Verfügbarkeit des Servers. Um die Verbindung und Verfügbarkeit zu prüfen, senden HTML-Formulare eine leere HEAD-Anforderung an den Server. Wenn der Server verfügbar ist, sendet das HTML5-Formular Daten (POST-Anforderung) an den Server. Wenn der Server nicht verfügbar ist, wird die Fehlermeldung *Keine Verbindung zum Server* angezeigt. Durch die erweiterte Erkennung müssen Benutzer das Formular nicht stets von Neuem ausfüllen. Das Proxy-Servlet verarbeitet HEAD-Anforderungen und löst keine Ausnahme aus.
