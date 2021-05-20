---
title: Dienstcontainer
seo-title: Dienstcontainer
description: AEM Forms-Dienste im Dienstcontainer
uuid: 89f2fd3d-63d7-4b70-b335-47314441f3ec
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding, development-tools
discoiquuid: dd9c0ec4-a195-4b78-8992-81d0efcc0a7e
role: Developer
exl-id: 6abf2401-5a87-4f72-9028-74580df5b9de
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 2%

---

# Dienstcontainer {#service-container}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

AEM Forms-Dienste, die sich im Dienstcontainer befinden (einschließlich Standarddiensten wie dem Encryption-Dienst, langlebigen und kurzlebigen Prozessen), können mit verschiedenen Anbietern aufgerufen werden, z. B. einem EJB-Anbieter. Ein EJB-Anbieter ermöglicht den Aufruf von AEM Forms-Diensten über RMI/IIOP. Ein Webdienstanbieter stellt Dienste als Webdienste (WSDL Generation) unter Verwendung von Standards wie SOAP/HTTP und SOAP/JMS bereit.

In der folgenden Tabelle werden die verschiedenen Methoden zum programmgesteuerten Aufrufen von AEM Forms-Diensten beschrieben.

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
   <td><p>Java-API</p></td>
   <td><p>Eine Java-API kann einen AEM Forms-Dienst aufrufen. Die Java-API ist in Client-Bibliotheken und die Java-Aufruf-API unterteilt. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api">AEM Forms mithilfe der Java-API aufrufen</a>.)</p></td>
  </tr>
  <tr>
   <td><p>Webdienste</p></td>
   <td><p>AEM Forms unterstützt Webdienststandards wie SOAP/HTTP. Ein Dienst kann als Webdienst verfügbar gemacht werden, wobei die WSDL den vom W3C definierten Webdienststandards entspricht.</p><p>Ein Dienst kann von jedem Webdienststapel aus aufgerufen werden, einschließlich .NET Framework und Sun™ Web Services SDK. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services">Aufrufen von AEM Forms mithilfe von Web Services</a>.)</p></td>
  </tr>
  <tr>
   <td><p>REST-Anforderungen</p></td>
   <td><p>AEM Forms unterstützt REST-Anfragen. Ein Dienst kann direkt von einer HTML-Seite aus aufgerufen werden. (Siehe <a href="/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests">Aufrufen von AEM Forms mithilfe von REST Requests</a>.)</p></td>
  </tr>
 </tbody>
</table>

Die folgende Abbildung zeigt die verschiedenen Möglichkeiten, wie AEM Forms-Dienste programmgesteuert aufgerufen werden können.

>[!NOTE]
>
>Zusätzlich zur Verwendung des AEM Forms SDK zum Erstellen von Clientanwendungen, die AEM Forms-Dienste aufrufen können, können Sie auch Komponenten erstellen, die im Dienstcontainer bereitgestellt werden können. Sie können beispielsweise eine Bankkomponente erstellen, die benutzerdefinierte Datentypen enthält, die in Prozessen verwendet werden können. Das heißt, Sie können einen Datentyp wie `com.adobe.idp.BankAccount` erstellen. Anschließend können Sie `com.adobe.idp.BankAccount`-Instanzen in Ihren Clientanwendungen erstellen.

Der Dienstcontainer bietet die folgenden Funktionen:

* Ermöglicht den Aufruf von AEM Forms-Diensten mit verschiedenen Methoden. Sie können einen Dienst konfigurieren, indem Sie Endpunkte festlegen, damit er mit allen Methoden aufgerufen werden kann: Remoting, die Java-API, Webdienste und REST. (Siehe [Programmgesteuerte Verwaltung von Endpunkten](/help/forms/developing/programmatically-endpoints.md#programmatically-managing-endpoints).)
* Konvertiert eine Nachricht in ein normalisiertes Format, das als Aufrufanforderung bezeichnet wird. Eine Aufrufanforderung wird von einer Client-Anwendung (oder einem anderen Dienst) an einen Dienst gesendet, der sich im Dienstcontainer befindet. Eine Aufrufanforderung enthält Informationen wie den Namen des aufzurufenden Dienstes und Datenwerte, die für die Durchführung des Vorgangs erforderlich sind. Viele Dienste benötigen ein Dokument, um einen Vorgang auszuführen. Daher enthält eine Aufrufanforderung normalerweise ein Dokument, bei dem es sich um PDF-Daten, XDP-Daten, XML-Daten usw. handeln kann.
* Sendet Aufrufanforderungen an entsprechende Dienste (der Name des aufzurufenden Dienstes ist Teil der Aufrufanforderung).
* Führt Aufgaben wie die Bestimmung durch, ob der Aufrufer berechtigt ist, den angegebenen Dienstvorgang aufzurufen. Die Aufrufanforderung muss einen gültigen Benutzernamen und ein gültiges Kennwort für AEM Formulare enthalten.

   Es gibt verschiedene Möglichkeiten, eine Aufrufanforderung an einen Dienst zu senden. Außerdem gibt es verschiedene Möglichkeiten, erforderliche Eingabewerte an den Dienst zu senden. Angenommen, Sie verwenden die Java-API zum Aufrufen eines Dienstes, für den ein PDF-Dokument erforderlich ist. Die entsprechende Java-Methode enthält einen Parameter, der ein PDF-Dokument akzeptiert. In diesem Fall ist der Datentyp des Parameters `com.adobe.idp.Document`. (Siehe [Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

   Wenn Sie einen Dienst mit überwachten Ordnern aufrufen, wird eine Aufrufanforderung gesendet, wenn Sie eine Datei in einem konfigurierten überwachten Ordner platzieren. Wenn Sie einen Dienst per E-Mail aufrufen, wird eine Aufrufanforderung an einen Dienst gesendet, wenn eine E-Mail-Nachricht in einem konfigurierten Posteingang eingeht.

   Der Dienstcontainer sendet nach Ausführung des Vorgangs eine Aufrufantwort zurück. Eine Aufrufantwort enthält Informationen wie die Vorgangsergebnisse. Wenn der Vorgang beispielsweise ein PDF-Dokument ändert, enthält die Aufrufantwort das geänderte PDF-Dokument. Wenn der Vorgang nicht erfolgreich war, enthält die Aufrufantwort eine Fehlermeldung.

   Eine Aufrufantwort kann auf dieselbe Weise abgerufen werden wie eine Aufrufanforderung. Das heißt, wenn die Aufrufanforderung mit der Java-API gesendet wird, kann mit der Java-API eine Aufrufantwort abgerufen werden. Angenommen, ein Vorgang ändert ein PDF-Dokument. Sie können das geänderte PDF-Dokument abrufen, indem Sie den Rückgabewert der Java-Methode abrufen, die den Dienst aufgerufen hat.

   Wenn ein langlebiger Prozess aufgerufen wird, enthält eine Aufrufantwort einen Identifikationswert, der mit der Aufrufanforderung verknüpft ist. Mithilfe dieses Bezeichnerwerts können Sie den Status des Prozesses zu einem späteren Zeitpunkt überprüfen. Betrachten Sie beispielsweise den Dienst MortgageLoan mit langer Lebensdauer. Mithilfe des Bezeichnerwerts können Sie überprüfen, ob der Prozess erfolgreich abgeschlossen wurde. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

   Das folgende Diagramm zeigt eine Client-Anwendung (die die Java-API verwendet), die einen Dienst aufruft.

   Wenn eine Client-Anwendung einen Dienst aufruft, treten drei Ereignisse auf:

   1. Eine Clientanwendung sendet eine Aufrufanforderung an einen Dienst.
   1. Der Dienst führt den in der Aufrufanforderung angegebenen Vorgang aus.
   1. Der Dienstcontainer gibt eine Aufrufantwort an die Clientanwendung zurück.

**Siehe auch**

[Grundlagen zu AEM Forms-Prozessen](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)

[Aufrufen von AEM Forms mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[AEM Forms mit der JavaAPI aufrufen](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[AEM Forms mit Web Services aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)

[An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Aufrufen von AEM Forms mithilfe von REST-Anforderungen](/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests)
