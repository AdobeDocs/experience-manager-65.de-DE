---
title: Service Container
seo-title: Service Container
description: AEM Forms-Dienstleistungen im Container
uuid: 89f2fd3d-63d7-4b70-b335-47314441f3ec
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding, development-tools
discoiquuid: dd9c0ec4-a195-4b78-8992-81d0efcc0a7e
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 2%

---


# Service Container {#service-container}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

AEM Forms-Dienste im Service Container (einschließlich Standarddienste wie Encryption-Dienst, Prozesse mit langer Lebensdauer und Prozesse mit kurzer Lebensdauer) können mit verschiedenen Anbietern wie einem EJB-Anbieter aufgerufen werden. Ein EJB-Anbieter ermöglicht das Aufrufen von AEM Forms-Diensten über RMI/IIOP. Ein Web-Dienstleister stellt Dienste als Webdienste (WSDL Generation) unter Verwendung von Standards wie SOAP/HTTP und SOAP/JMS bereit.

In der folgenden Tabelle werden die verschiedenen Möglichkeiten beschrieben, wie Sie AEM Forms-Dienste programmgesteuert aufrufen können.

<table>
 <thead>
  <tr>
   <th><p>Aufrufmethode</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Remote-Integration</p></td>
   <td><p>Die Remote-Integration bietet Flex-Clients die Möglichkeit, Dienstvorgänge aufzurufen. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting">Aufrufen von AEM Forms mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting</a>.)</p></td>
  </tr>
  <tr>
   <td><p>Java API</p></td>
   <td><p>Eine Java-API kann einen AEM Forms-Dienst aufrufen. Die Java-API ist in Client-Bibliotheken und die Java-Aufrufungs-API unterteilt. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api">Aufrufen von AEM Forms mit der Java-API</a>.)</p></td>
  </tr>
  <tr>
   <td><p>Webdienste</p></td>
   <td><p>AEM Forms unterstützt Webdienststandards wie SOAP/HTTP. Ein Dienst kann als Webdienst bereitgestellt werden, wobei die WSDL den vom W3C definierten Webdienststandards entspricht.</p><p>Ein Dienst kann von jedem Webdienststapel aufgerufen werden, einschließlich .NET Framework und Sun™ Web Services SDK. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services">Aufrufen von AEM Forms mithilfe von Web-Services</a>.)</p></td>
  </tr>
  <tr>
   <td><p>REST-Anforderungen</p></td>
   <td><p>AEM Forms unterstützt REST-Anfragen. Ein Dienst kann direkt von einer HTML-Seite aufgerufen werden. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests">Aufrufen von AEM Forms mit REST-Anfragen</a>.)</p></td>
  </tr>
 </tbody>
</table>

Die folgende Abbildung zeigt die verschiedenen Möglichkeiten, wie AEM Forms-Dienste programmgesteuert aufgerufen werden können.

>[!NOTE]
>
>Zusätzlich zur Verwendung des AEM Forms SDK zum Erstellen von Clientanwendungen, die AEM Forms-Dienste aufrufen können, können Sie auch Komponenten erstellen, die auf dem Service Container bereitgestellt werden können. Sie können beispielsweise eine Bankkomponente erstellen, die benutzerdefinierte Datentypen enthält, die in Prozessen verwendet werden können. Das heißt, Sie können einen Datentyp wie `com.adobe.idp.BankAccount` erstellen. Anschließend können Sie `com.adobe.idp.BankAccount`-Instanzen in Ihren Clientanwendungen erstellen.

Der Dienst-Container bietet folgende Funktionen:

* Ermöglicht das Aufrufen von AEM Forms-Diensten mit verschiedenen Methoden. Sie können einen Dienst konfigurieren, indem Sie Endpunkte festlegen, damit er mit allen folgenden Methoden aufgerufen werden kann: Remoting, die Java-API, Webdienste und REST. (Siehe [Programmatische Verwaltung von Endpunkten](/help/forms/developing/programmatically-endpoints.md#programmatically-managing-endpoints).)
* Konvertiert eine Nachricht in ein normalisiertes Format, das als Aufrufanforderung bezeichnet wird. Eine Aufrufanforderung wird von einer Clientanwendung (oder einem anderen Dienst) an einen Dienst im Service Container gesendet. Eine Aufrufanforderung enthält Informationen wie den Namen des aufzurufenden Dienstes und Datenwerte, die für die Durchführung des Vorgangs erforderlich sind. Viele Dienste benötigen ein Dokument, um einen Vorgang auszuführen. Daher enthält eine Aufrufanforderung in der Regel ein Dokument, bei dem es sich um PDF-Daten, XDP-Daten, XML-Daten usw. handeln kann.
* Sendet Aufrufanforderungen an geeignete Dienste (der Name des aufzurufenden Dienstes ist Teil der Aufrufanforderung).
* Führt Aufgaben durch, z. B. um zu ermitteln, ob der Aufrufer über die Berechtigung zum Aufrufen des angegebenen Dienstvorgangs verfügt. Die Aufrufanforderung muss einen gültigen Benutzernamen und ein gültiges Kennwort für AEM Formulare enthalten.

   Es gibt verschiedene Möglichkeiten, eine Aufrufanforderung an einen Dienst zu senden. Außerdem gibt es verschiedene Möglichkeiten, erforderliche Eingabewerte an den Dienst zu senden. Angenommen, Sie verwenden die Java-API zum Aufrufen eines Dienstes, für den ein PDF-Dokument erforderlich ist. Die entsprechende Java-Methode enthält einen Parameter, der ein PDF-Dokument akzeptiert. In diesem Fall ist der Datentyp des Parameters `com.adobe.idp.Document`. (Siehe [Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

   Wenn Sie einen Dienst mit überwachten Ordnern aufrufen, wird eine Aufrufanforderung gesendet, wenn Sie eine Datei in einem konfigurierten überwachten Ordner ablegen. Wenn Sie einen Dienst per E-Mail aufrufen, wird eine Aufrufanforderung an einen Dienst gesendet, wenn eine E-Mail in einem konfigurierten Posteingang eingeht.

   Der Dienst-Container sendet eine Aufrufantwort zurück, sobald der Vorgang ausgeführt wird. Eine Aufrufantwort enthält Informationen wie die Ergebnisse des Vorgangs. Wenn der Vorgang beispielsweise ein PDF-Dokument ändert, enthält die Aufrufantwort das geänderte PDF-Dokument. Wenn der Vorgang nicht erfolgreich war, enthält die Aufrufantwort eine Fehlermeldung.

   Eine Aufrufantwort kann auf dieselbe Weise abgerufen werden, wie eine Aufrufanforderung gesendet wird. Das heißt, wenn die Aufrufanforderung mit der Java-API gesendet wird, kann eine Aufrufantwort mit der Java-API abgerufen werden. Angenommen, ein Vorgang ändert ein PDF-Dokument. Sie können das geänderte PDF-Dokument abrufen, indem Sie den Rückgabewert der Java-Methode abrufen, die den Dienst aufgerufen hat.

   Wenn ein Prozess mit langer Lebensdauer aufgerufen wird, enthält eine Aufrufantwort einen ID-Wert, der mit der Aufrufanforderung verknüpft ist. Mit diesem Bezeichnerwert können Sie den Status des Prozesses zu einem späteren Zeitpunkt überprüfen. Betrachten Sie zum Beispiel den Dienst Hypothekendarlehen mit langer Lebensdauer. Mithilfe des ID-Werts können Sie prüfen, ob der Prozess erfolgreich abgeschlossen wurde. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

   Das folgende Diagramm zeigt eine Clientanwendung (die die Java-API verwendet), die einen Dienst aufruft.

   Wenn eine Clientanwendung einen Dienst aufruft, treten drei Ereignis auf:

   1. Eine Clientanwendung sendet eine Aufrufanforderung an einen Dienst.
   1. Der Dienst führt den in der Aufrufanforderung angegebenen Vorgang aus.
   1. Der Dienst-Container gibt eine Aufrufantwort an die Clientanwendung zurück.

**Siehe auch**

[Die AEM Forms-Prozesse](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)

[Aufrufen von AEM Forms mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[AEM Forms mit der JavaAPI aufrufen](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[AEM Forms mit Web Services aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)

[An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Aufrufen von AEM Forms mithilfe von REST-Anforderungen](/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests)
