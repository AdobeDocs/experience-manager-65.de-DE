---
title: Dienst-Container
description: AEM Forms-Dienste im Dienst-Container
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding, development-tools
role: Developer
exl-id: 6abf2401-5a87-4f72-9028-74580df5b9de
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '923'
ht-degree: 100%

---

# Dienst-Container {#service-container}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

AEM Forms-Dienste im Dienst-Container (einschließlich Standarddiensten wie dem Encryption-Dienst, langlebigen und kurzlebigen Prozessen) können mit verschiedenen Anbietern, z. B. einem EJB-Anbieter, aufgerufen werden. Ein EJB-Anbieter ermöglicht den Aufruf von AEM Forms-Services über RMI/IIOP. Ein Webservice-Anbieter stellt Services als Web-Services (WSDL-Generierung) unter Verwendung von Standards wie SOAP/HTTP und SOAP/JMS bereit.

In der folgenden Tabelle werden die verschiedenen Methoden zum programmgesteuerten Aufrufen von AEM Forms-Services beschrieben.

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
   <td><p>Die Remote-Integration bietet Flex-Clients die Möglichkeit, Service-Vorgänge aufzurufen. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting">Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM-Formulare nicht mehr unterstützt)</a>.)</p></td>
  </tr>
  <tr>
   <td><p>Java-API</p></td>
   <td><p>Eine Java-API kann einen AEM Forms-Service aufrufen. Die Java-API ist in Client-Bibliotheken und die Java-Aufruf-API unterteilt. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api">Aufrufen von AEM Forms mithilfe der Java-API</a>.)</p></td>
  </tr>
  <tr>
   <td><p>Web-Services</p></td>
   <td><p>AEM Forms unterstützt Webservice-Standards wie SOAP/HTTP. Ein Service kann als Webservice verfügbar gemacht werden, wobei die WSDL den vom W3C definierten Webservice-Standards entspricht.</p><p>Ein Service kann von jedem Webservice-Stapel aus aufgerufen werden, einschließlich .NET Framework und Sun™ Web Services SDK. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services">Aufrufen von AEM Forms mithilfe von Web-Services</a>.)</p></td>
  </tr>
  <tr>
   <td><p>REST-Anfragen</p></td>
   <td><p>AEM Forms unterstützt REST-Anfragen. Ein Service kann direkt von einer HTML-Seite aus aufgerufen werden. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests">Aufrufen von AEM Forms mithilfe von REST-Anfragen</a>.)</p></td>
  </tr>
 </tbody>
</table>

Die folgende Abbildung zeigt die verschiedenen Möglichkeiten, wie AEM Forms-Services programmgesteuert aufgerufen werden können.

>[!NOTE]
>
>Sie können das AEM Forms-SDK nicht nur zum Erstellen von Client-Programmen verwenden, die AEM Forms-Services aufrufen können, sondern auch zum Erstellen von Komponenten, die im Service-Container bereitgestellt werden können. Sie können beispielsweise eine Bankkomponente erstellen, die benutzerdefinierte Datentypen enthält, die in Prozessen verwendet werden können. Das heißt, Sie können einen Datentyp wie `com.adobe.idp.BankAccount` erstellen. Anschließend können Sie `com.adobe.idp.BankAccount`-Instanzen in Ihren Client-Programmen erstellen.

Der Service-Container bietet die folgenden Funktionen:

* Ermöglicht den Aufruf von AEM Forms-Services mit verschiedenen Methoden. Sie können einen Service konfigurieren, indem Sie Endpunkte festlegen, damit er mit allen Methoden aufgerufen werden kann: Remoting, die Java-API, Web-Services und REST. (Siehe [Programmgesteuertes Verwalten von Endpunkten](/help/forms/developing/programmatically-endpoints.md#programmatically-managing-endpoints).)
* Konvertiert eine Nachricht in ein normalisiertes Format, das als Aufrufanfrage bezeichnet wird. Eine Aufrufanfrage wird von einer Client-Anwendung (oder einem anderen Dienst) an einen Dienst im Dienst-Container gesendet. Eine Aufrufanfrage enthält Informationen wie den Namen des aufzurufenden Services und Datenwerte, die zur Durchführung des Vorgangs erforderlich sind. Viele Services benötigen ein Dokument, um einen Vorgang auszuführen. Daher enthält eine Aufrufanfrage normalerweise ein Dokument, bei dem es sich um PDF-Daten, XDP-Daten, XML-Daten usw. handeln kann.
* Sendet Aufrufanfragen an entsprechende Services (der Name des aufzurufenden Services ist Teil der Aufrufanfrage).
* Führt Aufgaben durch wie die Bestimmung, ob der Aufrufer berechtigt ist, den angegebenen Service-Vorgang aufzurufen. Die Aufrufanfrage muss einen gültigen Benutzernamen und ein gültiges Kennwort für AEM Forms enthalten.

  Es gibt verschiedene Möglichkeiten, eine Aufrufanfrage an einen Service zu senden. Außerdem gibt es verschiedene Möglichkeiten, erforderliche Eingabewerte an den Service zu senden. Angenommen, Sie verwenden die Java-API zum Aufrufen eines Services, für den ein PDF-Dokument erforderlich ist. Die entsprechende Java-Methode enthält einen Parameter, der ein PDF-Dokument akzeptiert. In diesem Fall lautet der Datentyp des Parameters `com.adobe.idp.Document`. (Siehe [Übergeben von Daten an AEM Forms-Services mithilfe der Java-API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

  Wenn Sie einen Service mithilfe von überwachten Ordnern aufrufen, wird eine Aufrufanfrage gesendet, sobald Sie eine Datei in einem konfigurierten überwachten Ordner platzieren. Wenn Sie einen Service per E-Mail aufrufen, wird eine Aufrufanfrage an einen Service gesendet, sobald eine E-Mail-Nachricht in einem konfigurierten Posteingang eingeht.

  Der Service-Container sendet nach Durchführung des Vorgangs eine Aufrufantwort zurück. Eine Aufrufantwort enthält Informationen wie die Vorgangsergebnisse. Wenn der Vorgang beispielsweise ein PDF-Dokument ändert, enthält die Aufrufantwort das geänderte PDF-Dokument. Wenn der Vorgang nicht erfolgreich war, enthält die Aufrufantwort eine Fehlermeldung.

  Eine Aufrufantwort kann auf dieselbe Weise abgerufen werden wie eine Aufrufanfrage. Das heißt, wenn die Aufrufanfrage mit der Java-API gesendet wird, kann mit der Java-API eine Aufrufantwort abgerufen werden. Angenommen, ein Vorgang ändert ein PDF-Dokument. Sie können das geänderte PDF-Dokument abrufen, indem Sie den Rückgabewert der Java-Methode abrufen, die den Service aufgerufen hat.

  Wenn ein langlebiger Prozess aufgerufen wird, enthält eine Aufrufantwort einen Kennungswert, der mit der Aufrufanfrage verknüpft ist. Mithilfe dieses Kennungswerts können Sie den Status des Prozesses zu einem späteren Zeitpunkt überprüfen. Nehmen wir zum Beispiel den langlebigen Service MortgageLoan. Mithilfe des Kennungswerts können Sie überprüfen, ob der Prozess erfolgreich abgeschlossen wurde. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

  Das folgende Diagramm zeigt ein Client-Programm (das die Java-API verwendet), das einen Service aufruft.

  Wenn ein Client-Programm einen Service aufruft, treten drei Ereignisse auf:

   1. Ein Client-Programm sendet eine Aufrufanfrage an einen Service.
   1. Der Service führt den in der Aufrufanfrage angegebenen Vorgang aus.
   1. Der Service-Container gibt eine Aufrufantwort an das Client-Programm zurück.

**Siehe auch**

[Grundlagen zu AEM Forms-Prozessen](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)

[Aufrufen von AEM Forms mithilfe von AEM Forms Remoting (für AEM Forms nicht mehr unterstützt)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[AEM Forms mit der JavaAPI aufrufen](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[AEM Forms mit Web Services aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)

[An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Aufrufen von AEM Forms mithilfe von REST-Anforderungen](/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests)
