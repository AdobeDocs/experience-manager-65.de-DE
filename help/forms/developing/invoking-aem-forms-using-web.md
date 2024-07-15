---
title: AEM Forms mit Web Services aufrufen
description: Rufen Sie AEM Forms-Prozesse mithilfe von Web-Services mit vollständiger Unterstützung für die WSDL-Generierung auf.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
role: Developer
exl-id: 3139564f-9346-4933-8e39-2e1642bff097
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations,AEM Forms on JEE
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '9814'
ht-degree: 100%

---

# AEM Forms mit Web Services aufrufen {#invoking-aem-forms-using-web-services}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Die meisten AEM Forms-Services im Service-Container sind so konfiguriert, dass sie einen Webservice bereitstellen, wobei die Generierung von WSDL (Web Service Definition Language) vollständig unterstützt wird. Das heißt, Sie können Proxy-Objekte erstellen, die den nativen SOAP-Stapel eines AEM Forms-Services verwenden. Daher können AEM Forms-Services die folgenden SOAP-Nachrichten austauschen und verarbeiten:

* **SOAP-Anfrage**: Wird von einem Client-Programm an einen Forms-Service gesendet und fordert eine Aktion an.
* **SOAP-Antwort**: Wird von einem Forms-Service an ein Client-Programm gesendet, nachdem eine SOAP-Anfrage verarbeitet wurde.

Mithilfe von Web-Services können Sie dieselben AEM Forms-Service-Vorgänge ausführen, die Sie auch mithilfe der Java-API ausführen können. Ein Vorteil der Verwendung von Web-Services zum Aufrufen von AEM Forms-Services ist, dass Sie ein Client-Programm in einer Entwicklungsumgebung erstellen können, die SOAP unterstützt. Ein Client-Programm ist nicht an eine bestimmte Entwicklungsumgebung oder Programmiersprache gebunden. Sie können beispielsweise ein Client-Programm mit Microsoft Visual Studio .NET und C# als Programmiersprache erstellen.

AEM Forms-Services werden über das SOAP-Protokoll bereitgestellt und sind mit WSI Basic Profile 1.1 kompatibel. Web Services Interoperability (WSI) ist eine Organisation mit offenen Standards, die die Interoperabilität von Web-Services plattformübergreifend fördert. Weitere Informationen finden Sie unter [https://www.ws-i.org/](https://www.ws-i.org).

AEM Forms unterstützt die folgenden Webservice-Standards:

* **Codierung**: Unterstützt nur Dokumenten- und Literalcodierung (die gemäß WSI Basic Profile die bevorzugte Codierung ist). (Siehe [Aufrufen von AEM Forms mithilfe von Base64-Codierung](#invoking-aem-forms-using-base64-encoding).)
* **MTOM**: Stellt eine Möglichkeit dar, Anlagen mit SOAP-Anforderungen zu codieren. (Siehe [Aufrufen von AEM Forms mithilfe von MTOM](#invoking-aem-forms-using-mtom).)
* **SwaRef**: Stellt eine andere Möglichkeit dar, Anlagen mit SOAP-Anforderungen zu codieren. (Siehe [Aufrufen von AEM Forms mithilfe von SwaRef](#invoking-aem-forms-using-swaref).)
* **SOAP mit Anlagen**: Unterstützt sowohl MIME als auch DIME (Direct Internet Message Encapulation). Diese Protokolle sind Standardmethoden zum Senden von Anhängen über SOAP. Microsoft Visual Studio .NET-Programme verwenden DIME. (Siehe [Aufrufen von AEM Forms mithilfe von Base64-Codierung](#invoking-aem-forms-using-base64-encoding).)
* **WS-Sicherheit**: Unterstützt ein Token-Profil für Benutzernamen und Kennwort, das eine Standardmethode zum Senden von Benutzernamen und Kennwörtern als Teil der SOAP-Kopfzeile von WS Security ist. AEM Forms unterstützt auch die HTTP-Standardauthentifizierung.  Sek.

Um AEM Forms-Services über einen Webservice aufzurufen, erstellen Sie in der Regel eine Proxy-Bibliothek, die die WSDL des Services verwendet. Der Abschnitt *Aufrufen von AEM Forms mithilfe von Web Services* verwendet JAX-WS, um Java-Proxy-Klassen zum Aufrufen von Services zu erstellen. (Siehe [Erstellen von Java-Proxy-Klassen mithilfe von JAX-WS](#creating-java-proxy-classes-using-jax-ws).)

Sie können eine Service-WSDL abrufen, indem Sie die folgende URL-Definition angeben (Elemente in Klammern sind optional):

```java
 https://<your_serverhost>:<your_port>/soap/services/<service_name>?wsdl[&version=<version>][&async=true|false][lc_version=<lc_version>]
```

Hierbei gilt:

* *your_serverhost* stellt die IP-Adresse des J2EE-Programm-Servers dar, auf dem AEM Forms gehostet wird.
* *your_port* stellt den HTTP-Anschluss dar, den der J2EE-Programm-Server verwendet.
* *service_name* stellt den Namen des Services dar.
* *version* stellt die Zielversion eines Services dar (standardmäßig wird die neueste Version des Services verwendet).
* `async` gibt den Wert `true` an, um zusätzliche Vorgänge für den asynchronen Aufruf zu aktivieren (standardmäßig `false`).
* *lc_version* stellt die Version von AEM Forms dar, die Sie aufrufen möchten.

In der folgenden Tabelle sind die WSDL-Definitionen des Services aufgeführt (unter der Annahme, dass AEM Forms auf dem lokalen Host bereitgestellt wird und der Port 8080 ist).

<table>
 <thead>
  <tr>
   <th><p>Service</p></th>
   <th><p>WSDL-Definition</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Assembler</p></td>
   <td><p><code>http://localhost:8080/soap/services/ AssemblerService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Sichern und Wiederherstellen</p></td>
   <td><p><code>http://localhost:8080/soap/services/BackupService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Barcoded Forms</p></td>
   <td><p><code>http://localhost:8080/soap/services/ BarcodedFormsService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Convert PDF</p></td>
   <td><p><code>http://localhost:8080/soap/services/ ConvertPDFService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Distiller</p></td>
   <td><p><code>http://localhost:8080/soap/services/ DistillerService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>DocConverter </p></td>
   <td><p><code>http://localhost:8080/soap/services/DocConverterService?WSDL</code></p></td>
  </tr>
  <tr>
   <td><p>DocumentManagement</p></td>
   <td><p><code>http://localhost:8080/soap/services/DocumentManagementService?WSDL</code></p></td>
  </tr>
  <tr>
   <td><p>Encryption-Dienst </p></td>
   <td><p><code>http://localhost:8080/soap/services/EncryptionService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Formulare</p></td>
   <td><p><code>http://localhost:8080/soap/services/FormsService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Form Data Integration</p></td>
   <td><p><code>http://localhost:8080/soap/services/FormDataIntegration?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Generate PDF</p></td>
   <td><p><code>http://localhost:8080/soap/services/ GeneratePDFService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>3D-PDF generieren</p></td>
   <td><p><code>http://localhost:8080/soap/services/Generate3dPDFService?WSDL</code></p></td>
  </tr>
  <tr>
   <td><p>Ausgabe</p></td>
   <td><p><code>http://localhost:8080/soap/services/ OutputService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>PDF Utilities </p></td>
   <td><p><code>http://localhost:8080/soap/services/ PDFUtilityService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Acrobat Reader DC Extensions</p></td>
   <td><p><code>http://localhost:8080/soap/services/ ReaderExtensionsService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Repository</p></td>
   <td><p><code>http://localhost:8080/soap/services/ RepositoryService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Rights Management </p></td>
   <td><p><code>http://localhost:8080/soap/services/ RightsManagementService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Signatur </p></td>
   <td><p><code>http://localhost:8080/soap/services/ SignatureService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>XMP Utilities</p></td>
   <td><p><code>http://localhost:8080/soap/services/ XMPUtilityService?wsdl</code></p></td>
  </tr>
 </tbody>
</table>

**WSDL-Definitionen für AEM Forms-Prozesse**

Geben Sie den Anwendungsnamen und den Prozessnamen in der WSDL-Definition an, um auf eine WSDL zugreifen zu können, die zu einem in Workbench erstellten Prozess gehört. Angenommen, der Name des Programms lautet `MyApplication` und der Name des Prozesses lautet `EncryptDocument`. Geben Sie in diesem Fall die folgende WSDL-Definition an:

```java
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?wsdl
```

>[!NOTE]
>
>Informationen zum Beispiel für den kurzlebigen Prozess `MyApplication/EncryptDocument` finden Sie unter [Beispiel für kurzlebige Prozesse](/help/forms/developing/aem-forms-processes.md).

>[!NOTE]
>
>Ein Programm kann Ordner enthalten. Geben Sie in diesem Fall den/die Ordnernamen in der WSDL-Definition an:

```java
 http://localhost:8080/soap/services/MyApplication/[<folderA>/.../<folderZ>/]EncryptDocument?wsdl
```

**Zugriff auf neue Funktionen mithilfe von Web-Services**

Auf neue Service-Funktionen in AEM Forms kann mithilfe von Web-Services zugegriffen werden. In AEM Forms wird beispielsweise die Möglichkeit eingeführt, Anhänge mithilfe von MTOM zu codieren. (Siehe [Aufrufen von AEM Forms mithilfe von MTOM](#invoking-aem-forms-using-mtom).)

Um auf die in AEM Forms eingeführten neuen Funktionen zuzugreifen, geben Sie in der WSDL-Definition das Attribut `lc_version` an. Um beispielsweise auf neue Service-Funktionen (einschließlich MTOM-Unterstützung) zuzugreifen, geben Sie die folgende WSDL-Definition an:

```java
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?wsdl&lc_version=9.0.1
```

>[!NOTE]
>
>Achten Sie beim Festlegen des Attributs `lc_version` darauf, dass Sie drei Ziffern verwenden. Beispielsweise entspricht 9.0.1 der Version 9.0.

**Webservice-BLOB-Datentyp**

Die WSDLs der AEM Forms-Services definieren viele Datentypen. Einer der wichtigsten Datentypen, die in einem Webservice verfügbar gemacht werden, ist ein `BLOB`-Typ. Dieser Datentyp wird beim Arbeiten mit AEM Forms-Java-APIs der Klasse `com.adobe.idp.Document` zugeordnet. (Siehe [Übergeben von Daten an AEM Forms-Services mithilfe der Java-API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)).

Ein `BLOB`-Objekt sendet Binärdaten (z. B. PDF-Dateien, XML-Daten usw.) an AEM Forms-Services und ruft sie von ihnen ab. Der `BLOB`-Typ wird in einer Service-WSDL wie folgt definiert:

```xml
 <complexType name="BLOB">
     <sequence>
         <element maxOccurs="1" minOccurs="0" name="contentType"
             type="xsd:string"/>
         <element maxOccurs="1" minOccurs="0" name="binaryData"
             type="xsd:base64Binary"/>
         <element maxOccurs="1" minOccurs="0" name="attachmentID"
             type="xsd:string"/>
         <element maxOccurs="1" minOccurs="0" name="remoteURL"
             type="xsd:string"/>
         <element maxOccurs="1" minOccurs="0" name="MTOM"
             type="xsd:base64Binary"
             xmime:expectedContentTypes="*/*"
             xmlns:xmime="https://www.w3.org/2005/05/xmlmime"/>
         <element maxOccurs="1" minOccurs="0" name="swaRef"
             type="tns1:swaRef"/>
         <element maxOccurs="1" minOccurs="0" name="attributes"
             type="impl:MyMapOf_xsd_string_To_xsd_anyType"/>
     </sequence>
 </complexType>
```

Die Felder `MTOM` und `swaRef` werden nur in AEM Forms unterstützt. Sie können diese neuen Felder nur verwenden, wenn Sie eine URL angeben, die die Eigenschaft `lc_version` enthält.

**Bereitstellen von BLOB-Objekten in Service-Anforderungen**

Wenn ein Service-Vorgang von AEM Forms einen `BLOB`-Typ als Eingabewert erfordert, erstellen Sie in Ihrer Anwendungslogik eine Instanz des `BLOB`-Typs. (Viele der Webservice-Schnellstartanleitungen unter *Programmieren mit AEM Forms* zeigen, wie Sie mit einem BLOB-Datentyp arbeiten).

Weisen Sie den Feldern, die zur `BLOB`-Instanz gehören, wie folgt Werte zu:

* **Base64**: Um Daten als im Base64-Format kodierten Text zu übergeben, legen Sie die Daten im Feld `BLOB.binaryData` und den Datentyp im MIME-Format (beispielsweise `application/pdf`) im Feld `BLOB.contentType` fest. (Siehe [Aufrufen von AEM Forms mit Base64-Kodierung](#invoking-aem-forms-using-base64-encoding).)
* **MTOM**: Um Binärdaten in einer MTOM-Anlage zu übergeben, geben Sie die Daten im Feld `BLOB.MTOM` ein. Mit dieser Einstellung werden die Daten über das Java JAX-WS-Framework oder die native API des SOAP-Frameworks an die SOAP-Anfrage angehängt. (Siehe [Aufruf von AEM Forms mit MTOM](#invoking-aem-forms-using-mtom).)
* **SwaRef**: Um Binärdaten in einem WS-I SwaRef-Anhang zu übergeben, geben Sie die Daten im `BLOB.swaRef`-Feld ein. Mit dieser Einstellung werden die Daten unter Verwendung des Java JAX-WS-Frameworks an die SOAP-Anfrage angehängt. (Siehe [Aufruf von AEM Forms mit SwaRef](#invoking-aem-forms-using-swaref).)
* **MIME- oder DIME-Anlage**: Um Daten in einer MIME- oder DIME-Anlage zu übergeben, fügen Sie die Daten mithilfe der nativen API des SOAP-Frameworks der SOAP-Anfrage hinzu. Legen Sie die Anlagenkennung im `BLOB.attachmentID`-Feld fest. (Siehe [Aufruf von AEM Forms mit Base64-Kodierung](#invoking-aem-forms-using-base64-encoding).)
* **Remote URL**: Wenn die Daten auf einem Webserver gehostet werden und über eine HTTP-URL zugänglich sind, geben Sie die HTTP-URL in das Feld `BLOB.remoteURL` ein. (Siehe [Aufruf von AEM Forms mit BLOB-Daten über HTTP](#invoking-aem-forms-using-blob-data-over-http).)

**Zugriff auf Daten in BLOB-Objekten, die von Diensten zurückgegeben werden**

Das Übermittlungsprotokoll für zurückgesendete `BLOB`-Objekte hängt von mehreren Faktoren ab, die in der folgenden Reihenfolge berücksichtigt werden und das bei Erfüllung der Hauptbedingung beendet wird:

1. **Ziel-URL legt Übertragungsprotokoll fest**. Wenn die Ziel-URL, die beim SOAP-Aufruf angegeben wurde, den Parameter `blob="`*BLOB_TYPE*“ enthält, dann bestimmt *BLOB_TYPE* das Übertragungsprotokoll. *BLOB_TYPE* ist ein Platzhalter für base64, dime, mime, http, mtom oder slagerf.
1. **SOAP-Endpunkt des Dienstes ist Smart**. Wenn die folgenden Bedingungen erfüllt sind, werden die Ausgabedokumente unter Verwendung des gleichen Übertragungsprotokolls wie die Eingabedokumente zurückgegeben:

   * Der SOAP-Endpunktparameter des Standardprotokoll-Dienstes für Ausgabe-Blob-Objekte ist auf Smart gesetzt.

     Für jeden Dienst mit einem SOAP-Endpunkt können Sie in der Administrationskonsole das Übertragungsprotokoll für alle zurückgegebenen Blobs festlegen. (Siehe [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63_de).)

   * Der AEM Forms-Dienst akzeptiert ein oder mehrere Dokumente als Eingabe.

1. **Service SOAP-Endpunkt ist nicht Smart**. Das konfigurierte Protokoll bestimmt das Dokumentübertragungsprotokoll, und die Daten werden im entsprechenden `BLOB`-Feld zurückgegeben. Wenn der SOAP-Endpunkt beispielsweise auf DIME gesetzt ist, befindet sich der zurückgegebene Blob im `blob.attachmentID`-Feld, unabhängig vom Übertragungsprotokoll eines beliebigen Eingabedokuments.
1. **Andernfalls**. Wenn ein Dienst den Dokumenttyp nicht als Eingabe verwendet, werden die Ausgabedokumente im `BLOB.remoteURL` -Feld über das HTTP-Protokoll zurückgegeben.

Wie in der ersten Bedingung beschrieben, können Sie den Übertragungstyp für alle zurückgegebenen Dokumente sicherstellen, indem Sie die SOAP-Endpunkt-URL wie folgt um ein Suffix erweitern:

```java
     https://<your_serverhost>:<your_port>/soap/services/<service
     name>?blob=base64|dime|mime|http|mtom|swaref
```

Im Folgenden wird der Zusammenhang zwischen den Übertragungsarten und dem Feld, aus dem Sie die Daten beziehen, erläutert:

* **Base64-Format**: Setzen Sie das `blob`-Suffix auf `base64`, um die Daten im `BLOB.binaryData`-Feld zurückzugeben.
* **MIME- oder DIME-Anhang**: Setzen Sie das `blob`-Suffix auf `DIME` oder `MIME`, um die Daten als einen entsprechenden Anlagetyp mit der im Feld `BLOB.attachmentID` zurückgegebenen Anlagekennung zurückzugeben. Verwenden Sie die proprietäre API des SOAP-Frameworks, um die Daten aus der Anlage zu lesen.
* **Remote URL**: Setzen Sie das `blob`-Suffix auf `http`, um die Daten auf dem Anwendungsserver zu speichern und die URL zurückzugeben, die auf die Daten im `BLOB.remoteURL`-Feld verweist.
* **MTOM oder SwaRef**: Setzen Sie das `blob`-Suffix auf `mtom` oder `swaref`, um die Daten als entsprechenden Anlagentyp mit der in den Feldern `BLOB.MTOM` oder `BLOB.swaRef` zurückgegebenen Anlagenkennung zurückzugeben. Verwenden Sie die native API des SOAP-Frameworks, um die Daten aus der Anlage zu lesen.

>[!NOTE]
>
>Es wird empfohlen, dass Sie 30 MB nicht überschreiten, wenn Sie ein `BLOB`-Objekt durch Aufruf seiner `setBinaryData`-Methode befüllen. Andernfalls besteht die Möglichkeit, dass eine `OutOfMemory`-Ausnahme auftritt.

>[!NOTE]
>
>JAX WS-basierte Anwendungen, die das MTOM-Übertragungsprotokoll verwenden, sind auf 25 MB an gesendeten und empfangenen Daten beschränkt. Diese Begrenzung ist auf einen Fehler in JAX-WS zurückzuführen. Wenn die Gesamtgröße der gesendeten und empfangenen Dateien 25 MB überschreitet, verwenden Sie das SwaRef-Übertragungsprotokoll anstelle des MTOM-Protokolls. Andernfalls besteht die Möglichkeit einer `OutOfMemory`-Ausnahme.

**MTOM-Übertragung von base64-kodierten Byte-Arrays**

Zusätzlich zum `BLOB`-Objekt unterstützt das MTOM-Protokoll sämtliche Byte-Array-Parameter oder Byte-Array-Felder eines komplexen Typs. Dies bedeutet, dass Client-SOAP-Frameworks, die MTOM unterstützen, jedes `xsd:base64Binary`-Element als MTOM-Anlage senden können (anstelle eines base64-kodierten Textes). AEM Forms SOAP-Endpunkte können diesen Typ der Byte-Array-Kodierung lesen. Der AEM Forms-Dienst gibt jedoch immer einen Byte-Array-Typ als base64-kodierten Text zurück. Die Parameter für die Ausgabe von Byte-Arrays unterstützen kein MTOM.

AEM Forms-Dienste, die eine große Menge an Binärdaten zurückgeben, verwenden den Typ Dokument/BLOB anstelle des Typs Byte-Array. Der Dokumententyp ist wesentlich effizienter für die Übertragung großer Datenmengen.

## Webdienst-Datentypen {#web-service-data-types}

In der folgenden Tabelle sind die Java-Datentypen mit dem entsprechenden Webdienst-Datentyp aufgeführt.

<table>
 <thead>
  <tr>
   <th><p>Java-Datentyp</p></th>
   <th><p>Webdienst-Datentyp</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p><code>java.lang.byte[]</code></p></td>
   <td><p><code>xsd:base64Binary</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Boolean</code></p></td>
   <td><p><code>xsd:boolean</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.util.Date</code></p></td>
   <td><p>Der <code>DATE</code>-Typ, der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;complexType name="DATE"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="date" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="calendar" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Wenn ein AEM Forms-Dienstvorgang einen <code>java.util.Date</code>-Wert als Eingabe verwendet, muss die SOAP-Client-Anwendung das Datum im Feld <code>DATE.date</code> übergeben. Das Setzen des <code>DATE.calendar</code>-Feldes führt in diesem Fall zu einer Laufzeitausnahme. Wenn der Dienst ein <code>java.util.Date</code> zurückgibt, wird das Datum in das Feld <code>DATE.date</code> zurückgegeben.</p></td>
  </tr>
  <tr>
   <td><p><code>java.util.Calendar</code></p></td>
   <td><p>Der <code>DATE</code>-Typ, der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;complexType name="DATE"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="date" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="calendar" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Wenn ein AEM Forms-Dienstvorgang einen <code>java.util.Calendar</code>-Wert als Eingabe verwendet, muss die SOAP-Client-Anwendung das Datum im <code>DATE.caledendar</code>-Feld übergeben. Das Setzen des <code>DATE.date</code>-Feldes führt in diesem Fall zu einer Laufzeitausnahme. Wenn der Dienst ein <code>java.util.Calendar</code> zurückgibt, wird das Datum im <code>DATE.calendar</code>-Feld zurückgegeben. </p></td>
  </tr>
  <tr>
   <td><p><code>java.math.BigDecimal</code></p></td>
   <td><p><code>xsd:decimal</code></p></td>
  </tr>
  <tr>
   <td><p><code>com.adobe.idp.Document</code></p></td>
   <td><p><code>BLOB</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Double</code></p></td>
   <td><p><code>xsd:double</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Float</code></p></td>
   <td><p><code>xsd:float</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Integer</code></p></td>
   <td><p><code>xsd:int</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.util.List</code></p></td>
   <td><p><code>MyArrayOf_xsd_anyType</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Long</code></p></td>
   <td><p><code>xsd:long</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.util.Map</code></p></td>
   <td><p>Die <code>apachesoap:Map</code>, die in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;schema elementFormDefault="qualified" targetNamespace="https://xml.apache.org/xml-soap" xmlns="https://www.w3.org/2001/XMLSchema"&gt;</code></p><p><code>&lt;complexType name="mapItem"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element name="key" nillable="true" type="xsd:anyType"/&gt;</code></p><p><code>&lt;element name="value" nillable="true" type="xsd:anyType"/&gt;</code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p><code>&lt;complexType name="Map"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="unbounded" minOccurs="0" name="item" </code><code>type="apachesoap:mapItem"/&gt;</code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p><code>&lt;/schema&gt;</code></p><p>Die Map wird als Sequenz von Schlüssel/Wert-Paaren dargestellt.</p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Object</code></p></td>
   <td><p><code>$1</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Short</code></p></td>
   <td><p><code>xsd:short</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.String</code></p></td>
   <td><p><code>xsd:string</code></p></td>
  </tr>
  <tr>
   <td><p><code>org.w3c.dom.Document</code></p></td>
   <td><p>Der XML-Typ, der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;complexType name="XML"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="document" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="element" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Wenn ein AEM Forms-Dienstvorgang einen <code>org.w3c.dom.Document</code>-Wert annimmt, übergeben Sie die XML-Daten im <code>XML.document</code>-Feld.</p><p>Das Setzen des <code>XML.element</code>-Feldes führt zu einer Laufzeitausnahme. Wenn der Dienst ein <code>org.w3c.dom.Document</code> zurückgibt, dann werden die XML-Daten im <code>XML.document</code> -Feld zurückgegeben.</p></td>
  </tr>
  <tr>
   <td><p><code>org.w3c.dom.Element</code></p></td>
   <td><p>Der XML-Typ, der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;complexType name="XML"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="document" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="element" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Wenn ein AEM Forms-Dienstvorgang ein <code>org.w3c.dom.Element</code> als Eingabe benötigt, übergeben Sie die XML-Daten in das <code>XML.element</code>-Feld.</p><p>Das Setzen des Feldes <code>XML.document</code> führt zu einer Laufzeitausnahme. Wenn der Dienst ein <code>org.w3c.dom.Element</code> zurückgibt, werden die XML-Daten im <code>XML.element</code>-Feld zurückgegeben.</p></td>
  </tr>
 </tbody>
</table>

## Erstellen von Java-Proxy-Klassen mit JAX-WS {#creating-java-proxy-classes-using-jax-ws}

Sie können JAX-WS verwenden, um eine Forms-Dienst-WSDL in Java-Proxy-Klassen zu konvertieren. Diese Klassen ermöglichen es Ihnen, AEM Forms-Dienstvorgänge aufzurufen. Mit Apache Ant können Sie ein Build-Skript erstellen, das Java-Proxy-Klassen durch Verweisen auf eine AEM Forms-Dienst-WSDL, generiert. Sie können JAX-WS-Proxy-Dateien generieren, indem Sie die folgenden Schritte ausführen:

1. Installieren Sie Apache Ant auf dem Client-Computer. (Siehe [https://ant.apache.org/de/bindownload.cgi](https://ant.apache.org/bindownload.cgi).)

   * Fügen Sie den Ordner „bin“ zu Ihrem Klassenpfad hinzu.
   * Setzen Sie die `ANT_HOME`-Umgebungsvariable auf den Ordner, in dem Sie Ant installiert haben.

1. Installieren Sie JDK 1.6 oder höher.

   * Fügen Sie den JDK-Bin-Ordner zu Ihrem Klassenpfad hinzu.
   * Fügen Sie den JRE-Bin-Ordner zu Ihrem Klassenpfad hinzu. Dieses Bin befindet sich im Verzeichnis `[JDK_INSTALL_LOCATION]/jre`.
   * Setzen Sie die `JAVA_HOME`-Umgebungsvariable auf den Ordner, in dem Sie das JDK installiert haben.

   JDK 1.6 enthält das in der Datei „build.xml“ verwendete Programm wsimport. JDK 1.5 enthält dieses Programm nicht.

1. Installieren Sie JAX-WS auf dem Client-Computer. (Siehe [Java-API für XML-Webdienste](https://jax-ws.dev.java.net/jax-ws-ea3/docs/mtom-swaref.html).)
1. Verwenden Sie JAX-WS und Apache Ant, um Java-Proxy-Klassen zu generieren. Erstellen Sie ein Ant-Build-Skript, um diese Aufgabe durchzuführen. Das folgende Skript ist ein Beispiel für ein Ant-Build-Skript mit dem Namen „build.xml“:

   ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    
    <project basedir="." default="compile">
    
    <property name="port" value="8080" />
    <property name="host" value="localhost" />
    <property name="username" value="administrator" />
    <property name="password" value="password" />
    <property name="tests" value="all" />
    
    <target name="clean" >
           <delete dir="classes" />
    </target>
    
    <target name="wsdl" depends="clean">
           <mkdir dir="classes"/>
           <exec executable="wsimport" failifexecutionfails="false" failonerror="true" resultproperty="foundWSIMPORT">
               <arg line="-keep -d classes https://${host}:${port}/soap/services/EncryptionService?wsdl&lc_version=9.0.1"/>
           </exec>
           <fail unless="foundWSIMPORT">
              !!! Failed to execute JDK's wsimport tool. Make sure that JDK 1.6 (or later) is on your PATH !!!
           </fail>
    </target>
    
    <target name="compile" depends="clean, wsdl" >
         <javac destdir="./classes" fork="true" debug="true">
            <src path="./src"/>
         </javac>
    </target>
    
    <target name="run">
         <java classname="Client" fork="yes" failonerror="true" maxmemory="200M">
            <classpath>
              <pathelement location="./classes"/>
            </classpath>
            <arg value="${port}"/>
            <arg value="${host}"/>
            <arg value="${username}"/>
            <arg value="${password}"/>
            <arg value="${tests}"/>
         </java>
    </target>
    </project>
   ```

   Beachten Sie in diesem Ant-Build-Skript, dass die `url`-Eigenschaft so eingestellt ist, dass sie auf den Verschlüsselungsdienst WSDL verweist, der auf localhost läuft. Die Eigenschaften `username` und `password` müssen auf einen gültigen AEM Forms-Benutzernamen und ein -Kennwort festgelegt sein. Beachten Sie, dass die URL das `lc_version`-Attribut beinhaltet. Ohne Angabe der `lc_version`-Option können Sie keine neuen AEM Forms-Dienstvorgänge aufrufen.

   >[!NOTE]
   >
   >Ersetzen Sie `EncryptionService`mit dem AEM Forms-Dienstnamen, den Sie mit den Java-Proxy-Klassen aufrufen möchten. Um beispielsweise Java-Proxy-Klassen für den Rights Management-Dienst zu erstellen, geben Sie Folgendes an:

   ```java
    http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1
   ```

1. Erstellen Sie eine BAT-Datei, um das Ant-Build-Skript auszuführen. Der folgende Befehl befindet sich in einer BAT-Datei, die für die Ausführung des Ant-Build-Skripts zuständig ist:

   ```java
    ant -buildfile "build.xml" wsdl
   ```

   Speichern Sie das ANT-Build-Skript im Ordner „C:\Program Files\Java\jaxws-ri\bin“. Das Skript schreibt die JAVA-Dateien in denOrdner „./classes“. Das Skript generiert JAVA-Dateien, die den Service aufrufen können.

1. Verpacken Sie die JAVA-Dateien in einer JAR-Datei. Wenn Sie auf Eclipse arbeiten, führen Sie die folgenden Schritte aus:

   * Erstellen Sie ein Java-Projekt, das zum Verpacken der JAVA-Proxy-Dateien in eine JAR-Datei verwendet wird.
   * Erstellen Sie einen Quellordner im Projekt.
   * Erstellen Sie ein `com.adobe.idp.services`-Paket im Quellordner.
   * Wählen Sie das `com.adobe.idp.services`-Paket und importieren Sie dann die JAVA-Dateien aus dem Ordner „adobe/idp/services“ in das Paket.
   * Erstellen Sie bei Bedarf ein `org/apache/xml/xmlsoap`-Paket im Quellordner.
   * Wählen Sie den Quellordner aus und importieren Sie dann die JAVA-Dateien aus dem Ordner „org/apache/xml/xmlsoap“.
   * Setzen Sie die Konformitätsstufe des Java-Compilers auf 5.0 oder höher.
   * Erstellen Sie das Projekt.
   * Exportieren Sie das Projekt als JAR-Datei.
   * Importieren Sie diese JAR-Datei in den Klassenpfad eines Client-Projekts. Importieren Sie außerdem alle JAR-Dateien in „&lt;Installationsverzeichnis>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty“.

   >[!NOTE]
   >
   >In allen Schnellstarts für Java-Web-Dienste (mit Ausnahme des Forms-Dienstes), die sich unter „Programmieren mit AEM Forms“ befinden, werden Java-Proxy-Dateien mit JAX-WS erstellt. Darüber hinaus verwenden alle Kurzanleitungen für Java-Webservices SwaRef. (Siehe [Aufrufen von AEM Forms mithilfe von SwaRef](#invoking-aem-forms-using-swaref).)

**Siehe auch**

[Erstellen von Java-Proxy-Klassen mithilfe von Apache Axis](#creating-java-proxy-classes-using-apache-axis)

[Aufrufen von AEM Forms mit Base64-Kodierung](#invoking-aem-forms-using-base64-encoding)

[Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](#invoking-aem-forms-using-blob-data-over-http)

[Aufrufen von AEM Forms mithilfe von SwaRef](#invoking-aem-forms-using-swaref)

## Erstellen von Java-Proxy-Klassen mithilfe von Apache Axis {#creating-java-proxy-classes-using-apache-axis}

Sie können das Apache Axis WSDL2Java-Tool verwenden, um einen Forms-Service in Java-Proxy-Klassen zu konvertieren. Diese Klassen ermöglichen es Ihnen, Vorgänge von Forms-Services aufzurufen. Mit Apache Ant können Sie Bibliotheksdateien für Axis aus einer Service-WSDL generieren. Sie können Apache Axis unter der URL [https://ws.apache.org/axis/](https://ws.apache.org/axis/) herunterladen.

>[!NOTE]
>
>In den Kurzanleitungen der Web-Services, die mit dem Forms-Service verbunden sind, werden Java-Proxy-Klassen verwendet, die mit Apache Axis erstellt wurden. In den Kurzanleitungen zum Forms Webservice wird außerdem Base64 als Codierungstyp verwendet. (Siehe [Kurzanleitungen zu Forms-Service-APIs](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts).)

Sie können Java-Bibliotheksdateien für Axis generieren, indem Sie die folgenden Schritte ausführen:

1. Installieren Sie Apache Ant auf dem Client-Computer. Es ist unter [https://ant.apache.org/bindownload.cgi](https://ant.apache.org/bindownload.cgi) verfügbar.

   * Fügen Sie den Ordner „bin“ zu Ihrem Klassenpfad hinzu.
   * Legen Sie die Umgebungsvariable `ANT_HOME` auf das Verzeichnis fest, in dem Sie Ant installiert haben.

1. Installieren Sie Apache Axis 1.4 auf dem Client-Computer. Es ist unter [https://ws.apache.org/axis/](https://ws.apache.org/axis/) verfügbar.
1. Richten Sie den Klassenpfad so ein, dass er die Axis-JAR-Dateien in Ihrem Webservice-Client zu verwendet, wie in den Installationsanweisungen zu Axis unter [https://ws.apache.org/axis/java/install.html](https://ws.apache.org/axis/java/install.html) beschrieben.
1. Verwenden Sie das Apache WSDL2Java-Tool in Axis, um Java-Proxy-Klassen zu generieren. Erstellen Sie ein Ant-Build-Skript, um diese Aufgabe durchzuführen. Das folgende Skript ist ein Beispiel für ein Ant-Build-Skript mit dem Namen „build.xml“:

   ```java
    <?xml version="1.0"?>
    <project name="axis-wsdl2java">
    
    <path id="axis.classpath">
    <fileset dir="C:\axis-1_4\lib" >
        <include name="**/*.jar" />
    </fileset>
    </path>
    
    <taskdef resource="axis-tasks.properties" classpathref="axis.classpath" />
    
    <target name="encryption-wsdl2java-client" description="task">
    <axis-wsdl2java
        output="C:\JavaFiles"
        testcase="false"
        serverside="false"
        verbose="true"
        username="administrator"
        password="password"
        url="http://localhost:8080/soap/services/EncryptionService?wsdl&lc_version=9.0.1" >
    </axis-wsdl2java>
    </target>
    
    </project>
   ```

   Beachten Sie in diesem Ant-Build-Skript, dass die Eigenschaft `url` so eingestellt ist, dass sie auf die WSDL des Verschlüsselungs-Services verweist, der auf localhost läuft. Die Eigenschaften `username` und `password` müssen auf einen gültigen Benutzernamen und Kennwort für AEM Forms festgelegt werden.

1. Erstellen Sie eine BAT-Datei, um das Ant-Build-Skript auszuführen. Der folgende Befehl ist in einer BAT-Datei zu finden, die für die Ausführung des Ant-Build-Skripts zuständig ist:

   ```java
    ant -buildfile "build.xml" encryption-wsdl2java-client
   ```

   Die JAVA-Dateien werden in den Ordner „C:\JavaFiles“ geschrieben, wie in der Eigenschaft `output` angegeben. Um den Forms-Service erfolgreich aufzurufen, importieren Sie diese JAVA-Dateien in Ihren Klassenpfad.

   Standardmäßig gehören diese Dateien zu einem Java-Paket mit dem Namen `com.adobe.idp.services`. Es wird empfohlen, diese JAVA-Dateien in einer JAR-Datei zu platzieren. Importieren Sie dann die JAR-Datei in den Klassenpfad Ihres Client-Programms.

   >[!NOTE]
   >
   >Es gibt verschiedene Möglichkeiten, .JAVA-Dateien in ein JAR zu packen. Eine Möglichkeit ist die Verwendung einer Java-IDE wie Eclipse. Legen Sie ein Java-Projekt an und erstellen Sie ein `com.adobe.idp.services`-Paket (alle .JAVA-Dateien gehören zu diesem Paket). Importieren Sie anschließend alle JAVA-Dateien in das Paket. Exportieren Sie das Projekt schließlich als JAR-Datei.

1. Ändern Sie die URL in der `EncryptionServiceLocator`-Klasse, um den Kodierungstyp anzugeben. Um beispielsweise base64 zu verwenden, geben Sie `?blob=base64` an, um sicherzustellen, dass das `BLOB`-Objekt Binärdaten zurückgibt. Das heißt, suchen Sie in der `EncryptionServiceLocator`-Klasse die folgende Codezeile:

   ```java
    http://localhost:8080/soap/services/EncryptionService;
   ```

   und ändern Sie sie in:

   ```java
    http://localhost:8080/soap/services/EncryptionService?blob=base64;
   ```

1. Fügen Sie die folgenden Axis-JAR-Dateien zum Klassenpfad Ihres Java-Projekts hinzu:

   * activation.jar
   * axis.jar
   * commons-codec-1.3.jar
   * commons-collections-3.1.jar
   * commons-discovery.jar
   * commons-logging.jar
   * dom3-xml-apis-2.5.0.jar
   * jai_imageio.jar
   * jaxen-1.1-beta-9.jar
   * jaxrpc.jar
   * log4j.jar
   * mail.jar
   * saaj.jar
   * wsdl4j.jar
   * xalan.jar
   * xbean.jar
   * xercesImpl.jar

   Diese JAR-Dateien befinden sich im `[install directory]/Adobe/Adobe Experience Manager Forms/sdk/lib/thirdparty`-Ordner.

**Siehe auch**

[Erstellen von Java-Proxy-Klassen mit JAX-WS](#creating-java-proxy-classes-using-jax-ws)

[Aufrufen von AEM Forms mit Base64-Kodierung](#invoking-aem-forms-using-base64-encoding)

[Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](#invoking-aem-forms-using-blob-data-over-http)

## Aufrufen von AEM Forms mit Base64-Kodierung {#invoking-aem-forms-using-base64-encoding}

Sie können einen AEM Forms-Dienst mit Base64-Kodierung aufrufen. Die Base64-Kodierung kodiert Anlagen, die mit einer Webdienst-Aufrufanforderung gesendet werden. Das heißt, `BLOB`-Daten sind Base64-kodiert, nicht die gesamte SOAP-Nachricht.

In „Aufrufen von AEM Forms mit Base64-Kodierung“ wird das Aufrufen des folgenden kurzlebigen AEM Forms-Prozesses namens `MyApplication/EncryptDocument` mit Base64-Kodierung beschrieben.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

### Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet {#creating-a-net-client-assembly-that-uses-base64-encoding}

Sie können eine .NET-Client-Assembly erstellen, um einen Forms-Dienst aus einem Microsoft Visual Studio .NET-Projekt heraus aufzurufen. Um eine .NET-Client-Assembly zu erstellen, die base64-Kodierung verwendet, führen Sie die folgenden Schritte aus:

1. Erstellen Sie eine Proxyklasse, die auf einer AEM Forms-Aufruf-URL basiert.
1. Erstellen Sie ein Microsoft Visual Studio .NET-Projekt, das die .NET-Client-Assembly erzeugt.

**Proxy-Klasse erstellen**

Sie können mithilfe eines Werkzeuges, das zu Microsoft Visual Studio gehört, eine Proxyklasse zur Erstellung der .NET-Client-Assembly erstellen. Dieses Tool trägt den Namen „wsdl.exe“ und befindet sich im Installationsordner von Microsoft Visual Studio. Um eine Proxy-Klasse zu erstellen, öffnen Sie die Eingabeaufforderung und navigieren Sie zu dem Ordner, der die Datei „wsdl.exe“ enthält. Weitere Informationen zum Tool „wsdl.exe“ finden Sie in der *MSDN-Hilfe*.

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:

```java
 wsdl https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
```

Standardmäßig erstellt dieses Tool eine CS-Datei im selben Ordner, der auf dem Namen der WSDL basiert. In diesem Fall wird eine CS-Datei mit dem Namen *EncryptDocumentService.cs* erstellt. Mit dieser CS-Datei erstellen Sie ein Proxy-Objekt, mit dem Sie den Service aufrufen können, der in der Aufruf-URL angegeben wurde.

Ändern Sie die URL in der Proxy-Klasse so, dass sie `?blob=base64` enthält, um sicherzustellen, dass das `BLOB`-Objekt binäre Daten zurückgibt. Suchen Sie in der Proxy-Klasse die folgende Code-Zeile:

```java
 "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument";
```

und ändern Sie sie in:

```java
 "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64";
```

Der Abschnitt *Aufrufen von AEM Forms mit Base64-Codierung* verwendet `MyApplication/EncryptDocument` als Beispiel. Wenn Sie eine .NET-Client-Assembly für einen anderen Forms-Service erstellen, stellen Sie sicher, dass Sie `MyApplication/EncryptDocument` durch den Namen des Services ersetzen.

**Entwickeln der .NET-Client-Assembly**

Erstellen Sie ein Visual Studio-Klassenbibliotheksprojekt, das eine .NET-Client-Assembly erzeugt. Die CS-Datei, die Sie mithilfe von „wsdl.exe“ erstellt haben, kann in dieses Projekt importiert werden. Dieses Projekt erzeugt eine DLL-Datei (die .NET-Client-Assembly), die Sie in anderen Visual Studio .NET-Projekten zum Aufrufen eines Services verwenden können.

1. Starten Sie Microsoft Visual Studio .NET.
1. Erstellen Sie ein Klassenbibliotheksprojekt und nennen Sie es DocumentService.
1. Importieren Sie die CS-Datei, die Sie mit „wsdl.exe“ erstellt haben.
1. Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen**.
1. Wählen Sie im Dialogfeld „Verweis hinzufügen“ die Option **System.Web.Services.dll**.
1. Klicken Sie auf **Auswählen** und dann auf **OK**.
1. Kompilieren und erstellen Sie das Projekt.

>[!NOTE]
>
>Durch dieses Verfahren wird eine .NET-Client-Assembly mit dem Namen „DocumentService.dll“ erstellt, mit der Sie SOAP-Anforderungen an den `MyApplication/EncryptDocument`-Service senden können.

>[!NOTE]
>
>Vergewissern Sie sich, dass Sie `?blob=base64` zur URL in der Proxy-Klasse hinzugefügt haben, die zur Erstellung der .NET-Client-Assembly verwendet wird. Andernfalls können Sie keine Binärdaten aus dem `BLOB`-Objekt abrufen.

**Referenzieren der .NET-Client-Assembly**

Platzieren Sie die neu erstellte .NET-Client-Assembly auf dem Computer, auf dem Sie Ihr Client-Programm entwickeln. Nachdem Sie die .NET-Client-Assembly in einem Verzeichnis platziert haben, können Sie sie von einem Projekt aus referenzieren. Verweisen Sie auch auf die `System.Web.Services`-Bibliothek aus Ihrem Projekt. Wenn Sie diese Bibliothek nicht referenzieren, können Sie die .NET-Client-Assembly nicht zum Aufrufen eines Dienstes verwenden.

1. Wählen Sie im **Projekt**-Menü **Verweis hinzufügen**.
1. Klicken Sie auf die Registerkarte **.NET**.
1. Klicken Sie auf **Durchsuchen** und suchen Sie die Datei „DocumentService.dll“.
1. Klicken Sie auf **Auswählen** und dann auf **OK**.

**Aufrufen eines Services mithilfe einer .NET-Client-Assembly, die die Base64-Codierung verwendet**

Sie können den Service `MyApplication/EncryptDocument` (der in Workbench erstellt wurde) mithilfe einer .NET-Client-Assembly aufrufen, die die Base64-Codierung verwendet. Um den Service `MyApplication/EncryptDocument` aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL des Services `MyApplication/EncryptDocument` verwendet.
1. Erstellen Sie ein Microsoft .NET-Client-Projekt. Verweisen Sie im Client-Projekt auf die Microsoft .NET-Client-Assembly. Verweisen Sie auch auf `System.Web.Services`.
1. Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `MyApplication_EncryptDocumentService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.
1. Legen Sie die Eigenschaft `Credentials` des `MyApplication_EncryptDocumentService`-Objekts mit einem `System.Net.NetworkCredential`-Objekt fest. Geben Sie im `System.Net.NetworkCredential`-Konstruktor einen AEM Forms-Benutzernamen und das entsprechende Kennwort an. Legen Sie Authentifizierungswerte fest, damit Ihre .NET-Client-Anwendung erfolgreich SOAP-Nachrichten mit AEM Forms austauschen kann.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um ein PDF-Dokument zu speichern, das an den Prozess `MyApplication/EncryptDocument` übergeben wird.
1. Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Dokuments und den Modus angibt, in dem die Datei geöffnet werden soll.
1. Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
1. Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
1. Füllen Sie das `BLOB`-Objekt durch Zuweisen seiner `binaryData`-Eigenschaft mit dem Inhalt des Byte-Arrays.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die Methode `invoke` des `MyApplication_EncryptDocumentService`-Objekts aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB`-Objekts zurück.
1. Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie dessen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des kennwortverschlüsselten Dokuments darstellt.
1. Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `invoke` des `MyApplicationEncryptDocumentService`-Objekts zurückgegeben wird. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `binaryData` des `BLOB`-Objekts abrufen.
1. Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
1. Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

### Aufrufen eines Service mit Java-Proxy-Klassen und Base64-Codierung {#invoking-a-service-using-java-proxy-classes-and-base64-encoding}

Sie können einen AEM Forms-Service mithilfe von Java-Proxy-Klassen und Base64 aufrufen. Um den `MyApplication/EncryptDocument`-Service mit Java-Proxy-Klassen aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie Java-Proxy-Klassen mit JAX-WS, welche die WSDL des `MyApplication/EncryptDocument`-Dienstes verwenden. Verwenden Sie den folgenden WSDL-Endpunkt:

   `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1`

   >[!NOTE]
   >
   >Ersetzen Sie `hiro-xp` *durch die IP-Adresse des J2EE-Anwendungsservers, der als Host für AEM Forms dient.*

1. Packen Sie die mit JAX-WS erstellten Java-Proxy-Klassen in eine JAR-Datei.
1. Schließen Sie die Java-Proxy-JAR-Datei und die JAR-Dateien im folgenden Pfad ein:

   &lt;Installationsverzeichnis>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in den Klassenpfad Ihres Java-Client-Projekts ein.

1. Erstellen Sie ein `MyApplicationEncryptDocumentService`-Objekt, indem Sie den Konstruktor verwenden.
1. Erstellen Sie ein `MyApplicationEncryptDocument`-Objekt, indem Sie die Methode `getEncryptDocument` des `MyApplicationEncryptDocumentService`-Objekts aufrufen.
1. Legen Sie die zum Aufrufen von AEM Forms erforderlichen Verbindungswerte fest, indem Sie den folgenden Datenelementen Werte zuweisen:

   * Weisen Sie den WSDL-Endpunkt und den Kodierungstyp dem Feld `ENDPOINT_ADDRESS_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts zu. Um den `MyApplication/EncryptDocument`-Service mit Base64-Kodierung aufzurufen, geben Sie den folgenden URL-Wert an:

     `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64`

   * Weisen Sie die Benutzerin bzw. den Benutzer von AEM Forms dem Feld `USERNAME_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts zu.
   * Weisen Sie dem Feld `PASSWORD_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts den entsprechenden Kennwortwert zu.

   Das folgende Code-Beispiel zeigt diese Programmlogik:

   ```java
    //Set connection values required to invoke AEM Forms
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64";
    String username = "administrator";
    String password = "password";
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Rufen Sie das PDF-Dokument ab, das an den `MyApplication/EncryptDocument`-Prozess gesendet werden soll, indem Sie ein `java.io.FileInputStream`-Objekt mithilfe seines Konstruktors erstellen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
1. Erstellen Sie ein Byte-Array und füllen Sie es mit dem Inhalt des `java.io.FileInputStream`-Objekts.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
1. Füllen Sie das `BLOB`-Objekt durch Aufrufen von dessen `setBinaryData`-Methode und Übergeben des Byte-Arrays. `setBinaryData` des `BLOB`-Objekts ist die Methode, die bei Verwendung der Base64-Kodierung aufzurufen ist. Siehe „Bereitstellen von BLOB-Objekten in Service-Anforderungen“.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die Methode `invoke` des `MyApplicationEncryptDocument`-Objekts aufrufen. Übergeben Sie das `BLOB`-Objekt, das das PDF-Dokument enthält. Die invoke-Methode gibt ein `BLOB`-Objekt zurück, das das verschlüsselte PDF-Dokument enthält.
1. Erstellen Sie ein Byte-Array, das das verschlüsselte PDF-Dokument enthält, indem Sie die Methode `getBinaryData` des `BLOB`-Objekts aufrufen.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei. Schreiben Sie das Byte-Array in eine Datei.

**Siehe auch**

[Schnellstart: Aufrufen eines Services mithilfe von Java-Proxy-Dateien und Base64-Codierung](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-java-proxy-files-and-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](#creating-a-net-client-assembly-that-uses-base64-encoding)

## AEM Forms mithilfe von MTOM aufrufen {#invoking-aem-forms-using-mtom}

Sie können AEM Forms-Services mithilfe des Webservice-Standards MTOM aufrufen. Dieser Standard definiert, wie binäre Daten, z. B. ein PDF-Dokument, über das Internet oder Intranet übertragen werden. Eine Funktion von MTOM ist die Verwendung des `XOP:Include`-Elements. Dieses Element ist in der XOP-Spezifikation (XML-binary Optimized Packaging) definiert, um auf die binären Anhänge einer SOAP-Nachricht zu verweisen.

In dieser Diskussion geht es um die Verwendung von MTOM, um den folgenden kurzlebigen AEM Forms-Prozess namens `MyApplication/EncryptDocument` aufzurufen.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

>[!NOTE]
>
>MTOM-Unterstützung wurde in AEM Forms, Version 9, hinzugefügt.

>[!NOTE]
>
>JAX WS-basierte Anwendungen, die das MTOM-Übertragungsprotokoll verwenden, sind auf 25 MB an gesendeten und empfangenen Daten beschränkt. Diese Begrenzung ist auf einen Fehler in JAX-WS zurückzuführen. Wenn die Gesamtgröße der gesendeten und empfangenen Dateien 25 MB überschreitet, verwenden Sie das SwaRef-Übertragungsprotokoll anstelle des MTOM-Protokolls. Andernfalls besteht die Möglichkeit einer `OutOfMemory` Ausnahme.

Hier geht es um die Verwendung von MTOM innerhalb eines Microsoft .NET-Projekts zum Aufrufen von AEM Forms-Diensten. Das verwendete .NET-Framework ist 3.5 und die Entwicklungsumgebung ist Visual Studio 2008. Wenn Sie auf Ihrem Entwicklungscomputer Web Service Enhancements (WSE) installiert haben, entfernen sie. Das .NET 3.5-Framework unterstützt ein SOAP-Framework namens Windows Communication Foundation (WCF). Wenn Sie AEM Forms mithilfe von MTOM aufrufen, wird nur WCF (nicht WSE) unterstützt.

### Erstellen eines .NET-Projekts, das einen Dienst mit MTOM aufruft {#creating-a-net-project-that-invokes-a-service-using-mtom}

Sie können ein Microsoft .NET-Projekt erstellen, das einen AEM Forms-Dienst mittels Webdienste aufrufen kann. Erstellen Sie zunächst ein Microsoft .NET-Projekt mit Visual Studio 2008. Um einen AEM Forms-Dienst aufzurufen, erstellen Sie einen Dienstverweis zum AEM Forms-Dienst, den Sie in Ihrem Projekt aufrufen möchten. Wenn Sie einen Dienstverweis erstellen, geben Sie eine URL für den AEM Forms-Dienst an:

```java
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
```

Ersetzen Sie `localhost` mit der IP-Adresse des J2EE-Anwendungsservers, auf dem AEM Forms gehostet wird. Ersetzen Sie `MyApplication/EncryptDocument` mit dem Namen des aufzurufenden AEM Forms-Dienstes. Um beispielsweise einen Rights Management-Vorgang aufzurufen, geben Sie Folgendes an:

`http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`

Die Option `lc_version` stellt sicher, dass AEM Forms-Funktionen, wie beispielsweise MTOM, verfügbar sind. Ohne Angabe der `lc_version`-Option können Sie AEM Forms nicht über MTOM aufrufen.

Nachdem Sie einen Dienstverweis erstellt haben, sind mit dem AEM Forms-Dienst verknüpfte Datentypen für die Verwendung in Ihrem .NET-Projekt verfügbar. Um ein .NET-Projekt zu erstellen, das einen AEM Forms-Dienst aufruft, führen Sie die folgenden Schritte aus:

1. Erstellen Sie ein .NET-Projekt mit Microsoft Visual Studio 2008.
1. Wählen Sie im **Projekt** Menü **Dienstverweis hinzufügen**.
1. Geben Sie im Dialogfeld **Adresse** die WSDL für den AEM Forms-Dienst an. Beispiel:

   ```java
    http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

1. Klicken Sie auf **Los** und dann auf **OK**.

### Aufrufen eines Dienstes mit MTOM in einem .NET-Projekt {#invoking-a-service-using-mtom-in-a-net-project}

Beachten Sie den `MyApplication/EncryptDocument`-Prozess, der ein ungesichertes PDF-Dokument akzeptiert und ein kennwortverschlüsseltes PDF-Dokument zurückgibt. Um den `MyApplication/EncryptDocument`Prozess (der in Workbench erstellt wurde) mithilfe von MTOM aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie ein Microsoft .NET-Projekt.
1. Erstellen Sie ein `MyApplication_EncryptDocumentClient`-Objekt mithilfe seines Standardkonstruktors.
1. Erstellen Sie ein `MyApplication_EncryptDocumentClient.Endpoint.Address`-Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der dem AEM Forms-Service die WSDL und den Typ der Codierung angibt:

   ```java
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=mtom
   ```

   Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Stellen Sie jedoch sicher, dass Sie `?blob=mtom` angeben.

   >[!NOTE]
   >
   >Ersetzen `hiro-xp` *mit der IP-Adresse des J2EE-Anwendungsservers, auf dem AEM Forms gehostet wird.*

1. Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `EncryptDocumentClient.Endpoint.Binding`-Datenelements abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
1. Legen Sie das Datenelement `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
1. Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

   * Weisen Sie den AEM Forms-Benutzernamen dem Datenelement `MyApplication_EncryptDocumentClient.ClientCredentials.UserName.UserName` zu.
   * Weisen Sie dem Datenelement `MyApplication_EncryptDocumentClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
   * Weisen Sie den Konstantenwert `HttpClientCredentialType.Basic` zum Datenelement `BasicHttpBindingSecurity.Transport.ClientCredentialType` zu.
   * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zum Datenelement `BasicHttpBindingSecurity.Security.Mode` zu.

   Das folgende Code-Beispiel zeigt diese Aufgaben.

   ```java
    //Enable BASIC HTTP authentication
    encryptProcess.ClientCredentials.UserName.UserName = "administrator";
    encryptProcess.ClientCredentials.UserName.Password = "password";
    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
    b.MaxReceivedMessageSize = 4000000;
    b.MaxBufferSize = 4000000;
    b.ReaderQuotas.MaxArrayLength = 4000000;
   ```

1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um ein PDF-Dokument zu speichern, das an den Prozess `MyApplication/EncryptDocument` übergeben wird.
1. Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Dokuments und den Modus angibt, in dem die Datei geöffnet werden soll.
1. Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
1. Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
1. Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Datenelement den Inhalt des Byte-Arrays zuweisen.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die Methode `invoke` des `MyApplication_EncryptDocumentClient`-Objekts aufrufen. Übergeben Sie das `BLOB`-Objekt, welches das PDF-Dokument enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB`-Objekts zurück.
1. Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgewert übergeben, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
1. Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `invoke` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
1. Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
1. Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

>[!NOTE]
>
>Die meisten AEM Forms-Dienstvorgänge haben einen MTOM-Schnellstart. Sie können sich diese Schnellstarts im entsprechenden Schnellstart-Abschnitt eines Dienstes ansehen. Den Abschnitt „Ausgabe-Schnellstart“ finden Sie beispielsweise unter [Ausgabedienst-API-Schnellstarts](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap).

**Siehe auch**

[Kurzanleitung: Aufrufen eines Services mithilfe von MTOM in einem .NET-Projekt](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-mtom-in-a-net-project)

[Zugreifen auf mehrere Dienste mithilfe von Webdiensten](#accessing-multiple-services-using-web-services)

[Erstellen einer ASP.NET-Webanwendung, die einen langlebigen, am Menschen orientierten Prozess aufruft](/help/forms/developing/invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

## Aufrufen von AEM Forms mithilfe von SwaRef {#invoking-aem-forms-using-swaref}

Sie können AEM Forms-Dienste mit SwaRef aufrufen. Der Inhalt des `wsi:swaRef`-XML-Elements wird als Anlage innerhalb eines SOAP-Bodys gesendet, der den Verweis auf die Anlage speichert. Wenn Sie einen Forms-Dienst mit SwaRef aufrufen, erstellen Sie Java-Proxy-Klassen unter Verwendung der Java-API für XML-Webdienste (JAX-WS). (Siehe [Java-API für XML-Webdienste](https://jax-ws.dev.java.net/jax-ws-ea3/docs/mtom-swaref.html).)

Hier geht es um den Aufruf des folgenden kurzlebigen Forms-Prozesses namens `MyApplication/EncryptDocument` unter Verwendung von SwaRef.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

>[!NOTE]
>
>SwaRef-Unterstützung in AEM Forms hinzugefügt

Im Folgenden wird erörtert, wie Forms-Dienste mithilfe von SwaRef innerhalb einer Java-Client-Anwendung aufgerufen werden können. Die Java-Anwendung verwendet Proxy-Klassen, die mithilfe von JAX-WS erstellt wurden.

### Aufrufen eines Dienstes mit JAX-WS-Bibliotheksdateien, die SwaRef verwenden {#invoke-a-service-using-jax-ws-library-files-that-use-swaref}

Um den `MyApplication/EncryptDocument`-Prozess mithilfe von Java-Proxy-Dateien aufzurufen, die mit JAX-WS und SwaRef erstellt wurden, führen Sie die folgenden Schritte aus:

1. Erstellen Sie Java-Proxy-Klassen mit JAX-WS, welche die WSDL des `MyApplication/EncryptDocument`-Dienstes verwenden. Verwenden Sie den folgenden WSDL-Endpunkt:

   ```java
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

   Weitere Informationen finden Sie unter [Erstellen von Java-Proxy-Klassen mit von JAX-WS](#creating-java-proxy-classes-using-jax-ws).

   >[!NOTE]
   >
   >Ersetzen `hiro-xp` *mit der IP-Adresse des J2EE-Anwendungsservers, auf dem AEM Forms gehostet wird.*

1. Packen Sie die mit JAX-WS erstellten Java-Proxy-Klassen in eine JAR-Datei.
1. Schließen Sie die Java-Proxy-JAR-Datei und die JAR-Dateien im folgenden Pfad ein:

   &lt;Installationsverzeichnis>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in den Klassenpfad Ihres Java-Client-Projekts ein.

1. Erstellen Sie ein `MyApplicationEncryptDocumentService`-Objekt, indem Sie den Konstruktor verwenden.
1. Erstellen Sie ein `MyApplicationEncryptDocument`-Objekt, indem Sie die Methode `getEncryptDocument` des `MyApplicationEncryptDocumentService`-Objekts aufrufen.
1. Legen Sie die zum Aufrufen von AEM Forms erforderlichen Verbindungswerte fest, indem Sie den folgenden Datenelementen Werte zuweisen:

   * Weisen Sie den WSDL-Endpunkt und den Codierungstyp dem Feld `ENDPOINT_ADDRESS_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts zu. Um den `MyApplication/EncryptDocument`-Dienst mit SwaRef-Kodierung aufzurufen, geben Sie den folgenden URL-Wert an:

     ` https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=swaref`

   * Weisen Sie die Benutzerin bzw. den Benutzer von AEM Forms dem Feld `USERNAME_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts zu.
   * Weisen Sie dem Feld `PASSWORD_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts den entsprechenden Kennwortwert zu.

   Das folgende Code-Beispiel zeigt diese Programmlogik:

   ```java
    //Set connection values required to invoke AEM Forms
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=swaref";
    String username = "administrator";
    String password = "password";
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Rufen Sie das PDF-Dokument ab, das an den `MyApplication/EncryptDocument`-Prozess gesendet werden soll, indem Sie ein `java.io.File`-Objekt mithilfe seines Konstruktors erstellen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
1. Erstellen Sie ein `javax.activation.DataSource`-Objekt mithilfe des `FileDataSource`-Konstruktors. Übergeben Sie das `java.io.File`-Objekt.
1. Erstellen Sie ein `javax.activation.DataHandler`-Objekt, indem Sie seinen Konstruktor verwenden und das `javax.activation.DataSource`-Objekt übergeben.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
1. Füllen Sie das `BLOB`-Objekt durch Aufrufen seiner `setSwaRef`-Methode und Übergabe des `javax.activation.DataHandler`-Objekts.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die Methode `invoke` des `MyApplicationEncryptDocument`-Objekts aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument enthält. Die Aufrufmethode gibt ein `BLOB`-Objekt zurück, das ein verschlüsseltes PDF-Dokument enthält.
1. Füllen Sie ein `javax.activation.DataHandler`-Objekt auf, indem Sie die Methode `getSwaRef` des `BLOB`-Objekts aufrufen.
1. Konvertieren Sie das `javax.activation.DataHandler`-Objekt in eine `java.io.InputSteam`-Instanz, indem Sie die Methode `getInputStream` des `javax.activation.DataHandler`-Objekts aufrufen.
1. Schreiben Sie die `java.io.InputSteam`-Instanz in eine PDF-Datei, die das verschlüsselte PDF-Dokument darstellt.

>[!NOTE]
>
>Die meisten AEM Forms-Dienstvorgänge haben einen SwaRef-Schnellstart. Sie können sich diese Schnellstarts im entsprechenden Schnellstart-Abschnitt eines Dienstes ansehen. Den Abschnitt „Ausgabe-Schnellstart“ finden Sie beispielsweise unter [Ausgabedienst-API-Schnellstarts](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap).

**Siehe auch**

[Kurzanleitung: Aufrufen eines Services mit SwaRef in einem Java-Projekt](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-swaref-in-a-java-project)

## Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP {#invoking-aem-forms-using-blob-data-over-http}

Sie können AEM Forms-Dienste über Webdienste aufrufen und BLOB-Daten über HTTP übergeben. Die Übergabe von BLOB-Daten über HTTP ist eine alternative Technik, statt der Verwendung von base64-Kodierung, DIME oder MIME. Beispielsweise können Sie Daten über HTTP in einem Microsoft .NET-Projekt übergeben, das Web Service Enhancement 3.0 verwendet, das DIME oder MIME nicht unterstützt. Bei der Verwendung von BLOB-Daten über HTTP werden die Eingabedaten hochgeladen, bevor der AEM Forms-Dienst aufgerufen wird.

„Aufrufen von AEM Forms mit BLOB-Daten über HTTP“ beschreibt das Aufrufen des folgenden kurzlebigen AEM Forms-Prozesses mit dem Namen `MyApplication/EncryptDocument` durch Übergabe von BLOB-Daten über HTTP.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

>[!NOTE]
>
>Es wird empfohlen, dass Sie mit dem Aufrufen von AEM Forms mithilfe von SOAP vertraut sind. (Siehe [Aufruf von AEM Forms über Webdienste](#invoking-aem-forms-using-web-services)).

### Erstellen einer .NET-Client-Assembly, die Daten über HTTP verwendet {#creating-a-net-client-assembly-that-uses-data-over-http}

Um eine Client-Assembly zu erstellen, die Daten über HTTP verwendet, folgen Sie dem unter [Aufrufen von AEM Forms mit Base64-Kodierung](#invoking-aem-forms-using-base64-encoding) beschriebenen Prozess. Ändern Sie jedoch die URL in der Proxy-Klasse so, dass sie `?blob=http` anstelle von `?blob=base64` enthält. Diese Aktion stellt sicher, dass Daten über HTTP übergeben werden. Suchen Sie in der Proxy-Klasse die folgende Code-Zeile:

```java
 "http://localhost:8080/soap/services/MyApplication/EncryptDocument";
```

und ändern Sie sie in:

```java
 "http://localhost:8080/soap/services/MyApplication/EncryptDocument?blob=http";
```

**Referenzieren der .NET clienMyApplication/EncryptDocument-Assembly**

Platzieren Sie die neue .NET-Client-Assembly auf dem Computer, auf dem Sie Ihre Client-Anwendung entwickeln. Nachdem Sie die .NET-Client-Assembly in einem Verzeichnis platziert haben, können Sie sie von einem Projekt aus referenzieren. Verweisen Sie auf die `System.Web.Services`-Bibliothek aus Ihrem Projekt. Wenn Sie diese Bibliothek nicht referenzieren, können Sie die .NET-Client-Assembly nicht zum Aufrufen eines Dienstes verwenden.

1. Wählen Sie im **Projekt**-Menü **Verweis hinzufügen**.
1. Klicken Sie auf die Registerkarte **.NET**.
1. Klicken Sie auf **Durchsuchen** und suchen Sie die Datei „DocumentService.dll“.
1. Klicken Sie auf **Auswählen** und dann auf **OK**.

**Aufrufen eines Dienstes mit einer .NET-Client-Assembly, die BLOB-Daten über HTTP verwendet**

Sie können den `MyApplication/EncryptDocument`-Dienst (der in Workbench erstellt wurde) mit einer .NET-Client-Assembly, die Daten über HTTP verwendet, aufrufen. Um den `MyApplication/EncryptDocument`-Dienst aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie die .NET-Client-Assembly.
1. Referenzieren Sie die Microsoft .NET-Client-Assembly. Erstellen Sie ein Microsoft .NET-Client-Projekt. Verweisen Sie im Client-Projekt auf die Microsoft .NET-Client-Assembly. Verweisen Sie auch auf `System.Web.Services`.
1. Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `MyApplication_EncryptDocumentService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.
1. Legen Sie die Eigenschaft `Credentials` des `MyApplication_EncryptDocumentService`-Objekts mit einem `System.Net.NetworkCredential`-Objekt fest. Geben Sie im `System.Net.NetworkCredential`-Konstruktor einen AEM Forms-Benutzernamen und das entsprechende Kennwort an. Legen Sie Authentifizierungswerte fest, damit Ihre .NET-Client-Anwendung erfolgreich SOAP-Nachrichten mit AEM Forms austauschen kann.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um Daten an den `MyApplication/EncryptDocument`-Prozess zu übergeben.
1. Weisen Sie dem Datenelement `remoteURL` des `BLOB`-Objekts einen String-Wert zu, der den URI-Speicherort eines PDF-Dokuments angibt, das an den `MyApplication/EncryptDocument`-Dienst übergeben werden soll.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die Methode `invoke` des `MyApplication_EncryptDocumentService`-Objekts aufrufen und das `BLOB`-Objekt übergeben. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB`-Objekts zurück.
1. Erstellen Sie ein `System.UriBuilder`-Objekt, indem Sie seinen Konstruktor verwenden und den Wert des Datenelements `remoteURL` des zurückgegebenen `BLOB`-Objekts übergeben.
1. Konvertieren Sie das `System.UriBuilder`-Objekt zu einem `System.IO.Stream`-Objekt. (Der C#-Schnellstart, der dieser Liste folgt, veranschaulicht, wie diese Aufgabe ausgeführt wird).
1. Erstellen Sie ein Byte-Array und füllen Sie es mit den Daten aus dem `System.IO.Stream`-Objekt auf.
1. Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
1. Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

### Aufrufen eines Dienstes mit Java-Proxy-Klassen und BLOB-Daten über HTTP {#invoking-a-service-using-java-proxy-classes-and-blob-data-over-http}

Sie können einen AEM Forms-Dienst mit Java-Proxy-Klassen und BLOB-Daten über HTTP aufrufen. Um den `MyApplication/EncryptDocument`-Dienst mit Java-Proxy-Klassen aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie Java-Proxy-Klassen mit JAX-WS, welche die WSDL des `MyApplication/EncryptDocument`-Dienstes verwenden. Verwenden Sie den folgenden WSDL-Endpunkt:

   ```java
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

   Weitere Informationen finden Sie unter [Erstellen von Java-Proxy-Klassen mit von JAX-WS](#creating-java-proxy-classes-using-jax-ws).

   >[!NOTE]
   >
   >Ersetzen `hiro-xp` *mit der IP-Adresse des J2EE-Anwendungsservers, auf dem AEM Forms gehostet wird.*

1. Packen Sie die mit JAX-WS erstellten Java-Proxy-Klassen in eine JAR-Datei.
1. Schließen Sie die Java-Proxy-JAR-Datei und die JAR-Dateien im folgenden Pfad ein:

   &lt;Installationsverzeichnis>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in den Klassenpfad Ihres Java-Client-Projekts ein.

1. Erstellen Sie ein `MyApplicationEncryptDocumentService`-Objekt, indem Sie den Konstruktor verwenden.
1. Erstellen Sie ein `MyApplicationEncryptDocument`-Objekt, indem Sie die Methode `getEncryptDocument` des `MyApplicationEncryptDocumentService`-Objekts aufrufen.
1. Legen Sie die zum Aufrufen von AEM Forms erforderlichen Verbindungswerte fest, indem Sie den folgenden Datenelementen Werte zuweisen:

   * Weisen Sie den WSDL-Endpunkt und den Kodierungstyp dem Feld `ENDPOINT_ADDRESS_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts zu. Um den Dienst `MyApplication/EncryptDocument` mit BLOB über HTTP-Kodierung aufzurufen, geben Sie den folgenden URL-Wert an:

     `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=http`

   * Weisen Sie die Benutzerin bzw. den Benutzer von AEM Forms dem Feld `USERNAME_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts zu.
   * Weisen Sie dem Feld `PASSWORD_PROPERTY` des `javax.xml.ws.BindingProvider`-Objekts den entsprechenden Kennwortwert zu.

   Das folgende Code-Beispiel zeigt diese Programmlogik:

   ```java
    //Set connection values required to invoke AEM Forms
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=http";
    String username = "administrator";
    String password = "password";
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
1. Befüllen Sie das `BLOB`-Objekt, indem Sie seine `setRemoteURL`-Methode aufrufen. Übergeben Sie einen Zeichenfolgewert, der den URI-Speicherort eines PDF-Dokuments angibt, das an den `MyApplication/EncryptDocument`-Dienst übergeben werden soll.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die Methode `invoke` des `MyApplicationEncryptDocument`-Objekts aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB`-Objekts zurück.
1. Erstellen Sie ein Byte-Array, um den Daten-Stream zu speichern, der das verschlüsselte PDF-Dokument darstellt. Rufen Sie die Methode `getRemoteURL` des `BLOB`-Objekts auf (verwenden Sie das `BLOB`-Objekt, das von der Methode `invoke` zurückgegeben wird).
1. Erstellen Sie ein Objekt `java.io.File`, indem Sie den Konstruktor verwenden. Dieses Objekt stellt das verschlüsselte PDF-Dokument dar.
1. Erstellen Sie ein `java.io.FileOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.File`-Objekt übergeben.
1. Rufen Sie die Methode `write` des `java.io.FileOutputStream`-Objekts auf. Übergeben Sie das Byte-Array, das den Daten-Stream enthält, der das verschlüsselte PDF-Dokument darstellt.

## Aufrufen von AEM Forms mithilfe von DIME {#invoking-aem-forms-using-dime}

Sie können AEM Forms-Services mithilfe von SOAP mit Anhängen aufrufen. AEM Forms unterstützt sowohl MIME- als auch DIME-Webservice-Standards. Mit DIME können Sie binäre Anhänge, wie z. B. PDF-Dokumente, zusammen mit Aufrufanforderungen senden, anstatt den Anhang zu codieren. Der Abschnitt *Aufrufen von AEM Forms mithilfe von DIME* erläutert das Aufrufen des folgenden kurzlebigen AEM Forms-Prozesses namens `MyApplication/EncryptDocument` mithilfe von DIME.

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um den Code-Beispielen folgen zu können, erstellen Sie mithilfe von Workbench einen Prozess mit dem Namen `MyApplication/EncryptDocument`. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).)

>[!NOTE]
>
>Der Aufruf von AEM Forms-Service-Vorgängen mithilfe von DIME wird nicht mehr unterstützt. Es wird empfohlen, MTOM zu verwenden. (Siehe [Aufrufen von AEM Forms mithilfe von MTOM](#invoking-aem-forms-using-mtom).)

### Erstellen eines .NET-Projekts, das DIME verwendet {#creating-a-net-project-that-uses-dime}

Führen Sie die folgenden Aufgaben aus, um ein .NET-Projekt zu erstellen, das einen Forms-Service mithilfe von DIME aufrufen kann:

* Installieren Sie Web Services Enhancements 2.0 auf Ihrem Entwicklungs-Computer.
* Erstellen Sie in Ihrem .NET-Projekt einen Web-Verweis zum AEM Forms-Service.

**Installation von Web Services Enhancements 2.0**

Installieren Sie Web Services Enhancements 2.0 auf Ihrem Entwicklungs-Computer und integrieren Sie es in Microsoft Visual Studio .NET. Sie können Web Services Enhancements 2.0 aus dem [Microsoft-Download-Center](https://www.microsoft.com/downloads/search.aspx) herunterladen.

Suchen Sie auf dieser Web-Seite nach Web Services Enhancements 2.0 und laden Sie es auf Ihren Entwicklungs-Computer herunter. Durch diesen Download wird eine Datei mit dem Namen „Microsoft WSE 2.0 SPI.msi“ auf Ihrem Computer platziert. Führen Sie das Installationsprogramm aus und folgen Sie den Online-Anweisungen.

>[!NOTE]
>
>Web Services Enhancements 2.0 unterstützt DIME. Die unterstützte Version von Microsoft Visual Studio ist 2003, wenn Sie mit Web Services Enhancements 2.0 arbeiten. Web Services Enhancements 3.0 unterstützt DIME nicht, dafür aber MTOM.

**Erstellen eines Web-Verweises auf einen AEM Forms-Service**

Nachdem Sie Web Services Enhancements 2.0 auf Ihrem Entwicklungs-Computer installiert und ein Microsoft .NET-Projekt erstellt haben, erstellen Sie einen Web-Verweis auf den Forms-Service. Um beispielsweise einen Web-Verweis auf den Prozess `MyApplication/EncryptDocument` zu erstellen, und unter der Annahme, dass Forms auf dem lokalen Computer installiert ist, geben Sie die folgende URL an:

```java
     http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL
```

Nachdem Sie einen Web-Verweis erstellt haben, stehen Ihnen die beiden folgenden Proxy-Datentypen zur Verfügung, die Sie in Ihrem .NET-Projekt verwenden können: `EncryptDocumentService` und `EncryptDocumentServiceWse`. Um den Prozess `MyApplication/EncryptDocument` mithilfe von DIME aufzurufen, verwenden Sie den Typ `EncryptDocumentServiceWse`.

>[!NOTE]
>
>Bevor Sie einen Web-Verweis für den Forms-Service erstellen, vergewissern Sie sich, dass Sie in Ihrem Projekt auf Web Services Enhancements 2.0 verweisen. (Siehe „Installation von Web Services Enhancements 2.0“.)

**Referenzieren der WSE-Bibliothek**

1. Wählen Sie im Menü „Projekt“ die Option „Verweis hinzufügen“ aus.
1. Wählen Sie im Dialogfeld „Verweis hinzufügen“ die Option „Microsoft.Web.Services2.dll“ aus.
1. Wählen Sie „System.Web.Services.dll“ aus.
1. Klicken Sie auf „Auswählen“ und dann auf „OK“.

**Erstellen eines Web-Verweises auf einen Forms-Service**

1. Wählen Sie im Projektmenü die Option „Webverwei hinzufügen“.
1. Geben Sie im Dialogfeld „URL“ die URL zum Forms-Dienst an.
1. Klicken Sie auf „Los“ und dann auf „Verweis hinzufügen“.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie Ihr .NET-Projekt für die Verwendung der WSE-Bibliothek aktivieren. Klicken Sie im Projekt-Explorer mit der rechten Maustaste auf den Projektnamen und wählen Sie „WSE 2.0 aktivieren“. Stellen Sie sicher, dass das Kontrollkästchen im angezeigten Dialogfeld aktiviert ist.

**Aufrufen eines Dienstes mit DIME in einem .NET-Projekt**

Sie können einen Forms-Dienst mit DIME aufrufen. Beachten Sie den `MyApplication/EncryptDocument`-Prozess, der ein ungesichertes PDF-Dokument akzeptiert und ein kennwortverschlüsseltes PDF-Dokument zurückgibt. Um den `MyApplication/EncryptDocument`-Prozess mit DIME aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie ein Microsoft .NET-Projekt, mit dem Sie einen Forms-Dienst mit DIME aufrufen können. Stellen Sie sicher, dass Sie Web Services Enhancements 2.0 einbeziehen und einen Webverweis auf den AEM Forms-Dienst erstellen.
1. Nachdem Sie einen Webverweis auf den `MyApplication/EncryptDocument`-Prozess gesetzt haben, erstellen Sie ein `EncryptDocumentServiceWse`-Objekt, indem Sie dessen Standardkonstruktor verwenden.
1. Legen Sie für das Datenelement `Credentials` des `EncryptDocumentServiceWse`-Objekts einen `System.Net.NetworkCredential`-Wert fest, der den Wert von AEM Forms-Benutzernamen und Kennwort angibt.
1. Erstellen Sie ein `Microsoft.Web.Services2.Dime.DimeAttachment`-Objekt, indem Sie seinen Konstruktor verwenden und die folgenden Werte übergeben:

   * Ein Zeichenfolgewert, der einen GUID-Wert angibt. Sie können einen GUID-Wert abrufen, indem Sie die `System.Guid.NewGuid.ToString`-Methode aufrufen.
   * Ein Zeichenfolgewert, der den Inhaltstyp angibt. Da für diesen Vorgang ein PDF-Dokument erforderlich ist, geben Sie `application/pdf` an.
   * Ein `TypeFormat`-Auflistungswert. Geben Sie `TypeFormat.MediaType`.
   * Ein Zeichenfolgewert, der den Speicherort des PDF-Dokuments angibt, das an den AEM Forms-Prozess übergeben wird.

1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
1. Fügen Sie die DIME-Anlage zum `BLOB`-Objekt hinzu, indem Sie den Datenelementwert `Id` des `Microsoft.Web.Services2.Dime.DimeAttachment`-Objekts dem Datenelement `attachmentID` des `BLOB`-Objekts zuweisen.
1. Rufen Sie die Methode `EncryptDocumentServiceWse.RequestSoapContext.Attachments.Add` auf und übergeben Sie das `Microsoft.Web.Services2.Dime.DimeAttachment`-Objekt.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die Methode `invoke` des `EncryptDocumentServiceWse`-Objekts aufrufen und das `BLOB`-Objekt übergeben, das den DIME-Anhang enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB`-Objekts zurück.
1. Ermitteln Sie den Anlagenkennungswert, indem Sie den Wert des Datenelements `attachmentID` des zurückgegebenen `BLOB`-Objekts abrufen.
1. Iterieren Sie durch die Anlagen unter `EncryptDocumentServiceWse.ResponseSoapContext.Attachments` und verwenden Sie den Anlagenkennungswert, um das verschlüsselte PDF-Dokument abzurufen.
1. Erhalten Sie ein `System.IO.Stream`-Objekt, indem Sie den Wert des Datenelements `Stream` des `Attachment`-Objekts abrufen.
1. Erstellen Sie ein Byte-Array und übergeben Sie dieses Byte-Array an die Methode `Read` des `System.IO.Stream`-Objekts. Diese Methode füllt das Byte-Array mit einem Datenstrom, der das verschlüsselte PDF-Dokument darstellt.
1. Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der einen Speicherort der PDF-Datei darstellt. Dieses Objekt stellt das verschlüsselte PDF-Dokument dar.
1. Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.
1. Schreiben Sie den Inhalt des Byte-Arrays in die PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

### Erstellen von Apache Axis Java-Proxy-Klassen, die DIME verwenden {#creating-apache-axis-java-proxy-classes-that-use-dime}

Sie können das Apache Axis WSDL2Java-Tool verwenden, um eine Dienst-WSDL in Java-Proxyklassen zu konvertieren, damit Sie Dienstvorgänge aufrufen können. Mithilfe von Apache Ant können Sie Bibliotheksdateien für Axis aus einer AEM Forms-Dienst-WSDL generieren, mit der Sie den Dienst aufrufen können. (Siehe [Erstellen von Java-Proxy-Klassen mit Apache Axis](#creating-java-proxy-classes-using-apache-axis).)

Das Apache Axis WSDL2Java-Tool generiert JAVA-Dateien, die Methoden enthalten, die zum Senden von SOAP-Anforderungen an einen Dienst verwendet werden. SOAP-Anforderungen, die von einem Dienst empfangen werden, werden von den von Axis generierten Bibliotheken dekodiert und in die Methoden und Argumente zurückumgewandelt.

Zum Aufrufen des `MyApplication/EncryptDocument`-Dienstes (der in Workbench erstellt wurde) mit Axis-generierten Bibliotheksdateien und DIME, führen Sie die folgenden Schritte durch:

1. Erstellen Sie Java-Proxy-Klassen, die die `MyApplication/EncryptDocument`-Dienst-WSDL mit Apache Axis nutzen. (Siehe [Erstellen von Java-Proxy-Klassen mit Apache Axis](#creating-java-proxy-classes-using-apache-axis).)
1. Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.
1. Erstellen Sie ein Objekt `MyApplicationEncryptDocumentServiceLocator`, indem Sie den Konstruktor verwenden.
1. Erstellen Sie ein `URL`-Objekt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der die WSDL-Definition des AEM Forms-Dienstes angibt. Stellen Sie sicher, dass Sie `?blob=dime` am Ende der SOAP-Endpunkt-URL angeben. Beispiele

   ```java
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=dime.
   ```

1. Erstellen Sie ein `EncryptDocumentSoapBindingStub`-Objekt durch Aufrufen des Konstruktors und Übergeben des `MyApplicationEncryptDocumentServiceLocator`-Objekts und des `URL`-Objekts.
1. Legen Sie den Benutzernamen und das Kennwort für AEM Forms fest, indem Sie die Methoden `setUsername` und `setPassword` des `EncryptDocumentSoapBindingStub`-Objekts aufrufen.

   ```java
    encryptionClientStub.setUsername("administrator");
    encryptionClientStub.setPassword("password");
   ```

1. Rufen Sie das PDF-Dokument, das an den `MyApplication/EncryptDocument`-Dienst gesendet werden soll, durch Erstellen eines `java.io.File`-Objekts ab. Übergeben Sie einen Zeichenfolgewert, der den Speicherort des PDF-Dokuments angibt.
1. Erstellen Sie ein `javax.activation.DataHandler`-Objekt, indem Sie seinen Konstruktor verwenden und das `javax.activation.FileDataSource`-Objekt übergeben. Das `javax.activation.FileDataSource`-Objekt kann mithilfe seines Konstruktors und der Übergabe des `java.io.File`-Objekts, welches das PDF-Dokument darstellt, erstellt werden.
1. Erstellen Sie ein `org.apache.axis.attachments.AttachmentPart`-Objekt, indem Sie seinen Konstruktor verwenden und das `javax.activation.DataHandler`-Objekt übergeben.
1. Hängen Sie die Anlage an, indem Sie die Methode `addAttachment` des `EncryptDocumentSoapBindingStub`-Objekts aufrufen und das `org.apache.axis.attachments.AttachmentPart`-Objekt übergeben.
1. Erstellen Sie ein `BLOB`-Objekt, indem Sie seinen Konstruktor verwenden. Füllen Sie das `BLOB`-Objekt mit dem Anlagenkennungswert, indem Sie die Methode `setAttachmentID` des `BLOB`-Objekts aufrufen und den Anlagenkennungswert übergeben. Dieser Wert kann durch Aufrufen der Methode `getContentId` des `org.apache.axis.attachments.AttachmentPart`-Objekts ermittelt werden.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die Methode `invoke` des `EncryptDocumentSoapBindingStub`-Objekts aufrufen. Übergeben Sie das `BLOB`-Objekt, das die DIME-Anlage enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB`-Objekt zurück.
1. Ermitteln Sie den Wert der Anlagenkennung, indem Sie die Methode `getAttachmentID` des zurückgegebenen `BLOB`-Objekts aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Kennungswert der zurückgegebenen Anlage darstellt.
1. Rufen Sie die Anlagen ab, indem Sie die Methode `getAttachments` des `EncryptDocumentSoapBindingStub`-Objekts aufrufen. Diese Methode gibt ein Array von `Objects`, das die Anlagen darstellt, zurück.
1. Iterieren Sie durch die Anlagen (das `Object`-Array) und verwenden Sie den Anlagenkennungswert, um das verschlüsselte PDF-Dokument abzurufen. Jedes Element ist ein `org.apache.axis.attachments.AttachmentPart` -Objekt.
1. Erhalten Sie das `javax.activation.DataHandler`-Objekt, das mit dem Anhang verbunden ist, indem Sie die Methode `getDataHandler` des `org.apache.axis.attachments.AttachmentPart`-Objekts aufrufen.
1. Erhalten Sie ein `java.io.FileStream`-Objekt, indem Sie die Methode `getInputStream` des `javax.activation.DataHandler`-Objekts aufrufen.
1. Erstellen Sie ein Byte-Array und übergeben Sie dieses Byte-Array an die Methode `read` des `java.io.FileStream`-Objekts. Diese Methode füllt das Byte-Array mit einem Datenstrom, der das verschlüsselte PDF-Dokument darstellt.
1. Erstellen Sie ein Objekt `java.io.File`, indem Sie den Konstruktor verwenden. Dieses Objekt stellt das verschlüsselte PDF-Dokument dar.
1. Erstellen Sie ein `java.io.FileOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.File`-Objekt übergeben.
1. Rufen Sie die Methode `write` des `java.io.FileOutputStream`-Objekts auf und übergeben Sie das Byte-Array, das den Datenstrom enthält, der das verschlüsselte PDF-Dokument darstellt.

**Siehe auch**

[Kurzanleitung: Aufrufen eines Services mithilfe von DIME in einem Java-Projekt](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-dime-in-a-java-project)

## Verwenden der SAML-basierten Authentifizierung {#using-saml-based-authentication}

AEM Forms unterstützt beim Aufrufen von Services verschiedene Authentifizierungsmodi für Web-Services. Ein Authentifizierungsmodus ist die Angabe eines Benutzernamens und eines Kennworts mit Hilfe einer einfachen Autorisierungskopfzeile im Aufruf des Web-Services. AEM Forms unterstützt auch die Authentifizierung, die auf einer SAML-Bestätigung basiert. Wenn ein Client-Programm einen AEM Forms-Service mithilfe eines Web-Services aufruft, kann das Client-Programm Authentifizierungsinformationen auf eine der folgenden Arten bereitstellen:

* Übergeben von Anmeldeinformationen als Teil der grundlegenden Autorisierung
* Übergeben des Benutzernamen-Tokens als Teil der WS-Security-Kopfzeile
* Übergeben einer SAML-Bestätigung als Teil der WS-Security-Kopfzeile
* Übergeben eines Kerberos-Tokens als Teil der WS-Security-Kopfzeile

AEM Forms unterstützt keine standardmäßige zertifikatbasierte Authentifizierung, unterstützt jedoch die zertifikatbasierte Authentifizierung in einer anderen Form.

>[!NOTE]
>
>In den Kurzanleitungen für Web-Services in „Programmieren mit AEM Forms“ werden Werte für Benutzernamen und Kennwort angegeben, um die Autorisierung durchzuführen.

Die Identität von AEM Forms-Benutzern kann durch eine SAML-Bestätigung dargestellt werden, die mithilfe eines geheimen Schlüssels signiert wird. Der folgende XML-Code zeigt ein Beispiel für eine SAML-Bestätigung.

```xml
 <Assertion xmlns="urn:oasis:names:tc:SAML:1.0:assertion"
     xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion"
     xmlns:samlp="urn:oasis:names:tc:SAML:1.0:protocol"
     AssertionID="fd4bd0c87302780e0d9bbfa8726d5bc0" IssueInstant="2008-04-17T13:47:00.720Z" Issuer="LiveCycle"
     MajorVersion="1" MinorVersion="1">
     <Conditions NotBefore="2008-04-17T13:47:00.720Z" NotOnOrAfter="2008-04-17T15:47:00.720Z">
     </Conditions>
     <AuthenticationStatement
         AuthenticationInstant="2008-04-17T13:47:00.720Z"
         AuthenticationMethod="urn:oasis:names:tc:SAML:1.0:am:unspecified">
         <Subject>
             <NameIdentifier NameQualifier="DefaultDom">administrator</NameIdentifier>
             <SubjectConfirmation>
                 <ConfirmationMethod>urn:oasis:names:tc:SAML:1.0:cm:sender-vouches</ConfirmationMethod>
             </SubjectConfirmation>
         </Subject>
     </AuthenticationStatement>
     <ds:Signature >
         <ds:SignedInfo>
             <ds:CanonicalizationMethod Algorithm="https://www.w3.org/2001/10/xml-exc-c14n#"></ds:CanonicalizationMethod>
             <ds:SignatureMethod    Algorithm="https://www.w3.org/2000/09/xmldsig#hmac-sha1"></ds:SignatureMethod>
             <ds:Reference URI="#fd4bd0c87302780e0d9bbfa8726d5bc0">
                 <ds:Transforms>
                     <ds:Transform Algorithm="https://www.w3.org/2000/09/xmldsig#enveloped-signature"></ds:Transform>
                     <ds:Transform Algorithm="https://www.w3.org/2001/10/xml-exc-c14n#">
                         <ec:InclusiveNamespaces
                             PrefixList="code ds kind rw saml samlp typens #default">
                         </ec:InclusiveNamespaces>
                     </ds:Transform>
                 </ds:Transforms>
                 <ds:DigestMethod Algorithm="https://www.w3.org/2000/09/xmldsig#sha1"></ds:DigestMethod>
                 <ds:DigestValue>hVrtqjWr+VzaVUIpQx0YI9lIjaY=</ds:DigestValue>
             </ds:Reference>
         </ds:SignedInfo>
         <ds:SignatureValue>UMbBb+cUcPtcWDCIhXes4n4FxfU=</ds:SignatureValue>
     </ds:Signature>
 </Assertion>
```

Diese Beispiel-Bestätigung wird für einen Administrator-Benutzer ausgestellt. Diese Bestätigung enthält die folgenden bemerkenswerten Elemente:

* Sie gilt für eine bestimmte Dauer.
* Sie wird für einen bestimmten Benutzer ausgestellt.
* Sie ist digital signiert. Jede daran vorgenommene Änderung würde also die Signatur beschädigen.
* Sie kann für AEM Forms als Token der Benutzeridentität ähnlich wie Benutzername und Kennwort angezeigt werden.

Ein Client-Programm kann die Bestätigung von jeder AuthenticationManager-API in AEM Forms abrufen, die ein `AuthResult`-Objekt zurückgibt. Sie können eine `AuthResult`-Instanz erhalten, indem Sie eine der beiden folgenden Methoden durchführen:

* Authentifizieren des Benutzers mithilfe einer der Authentifizierungsmethoden, die von der AuthenticationManager-API verfügbar gemacht werden. Normalerweise würden der Benutzername und das Kennwort verwendet. Sie können jedoch auch die Zertifikatauthentifizierung verwenden.
* Mithilfe der Methode `AuthenticationManager.getAuthResultOnBehalfOfUser`. Mithilfe dieser Methode kann ein Client-Programm für einen beliebigen AEM Forms-Benutzer ein `AuthResult`-Objekt abrufen.

AEM Forms-Benutzende können mithilfe eines SAML-Tokens authentifiziert werden, das abgerufen wird. Diese SAML-Bestätigung (XML-Fragment) kann als Teil der WS-Security-Kopfzeile mit dem Aufruf des Web-Services zur Benutzerauthentifizierung gesendet werden. In der Regel hat ein Client-Programm einen Benutzer authentifiziert, aber die Anmeldeinformationen des Benutzers nicht gespeichert. (Oder der Benutzer hat sich bei diesem Client über einen anderen Mechanismus als die Verwendung eines Benutzernamens und Kennworts angemeldet.) In dieser Situation muss das Client-Programm AEM Forms aufrufen und einen bestimmten Benutzer verkörpern, der berechtigt ist, AEM Forms aufzurufen.

Um einen bestimmten Benutzer zu verkörpern, rufen Sie die Methode `AuthenticationManager.getAuthResultOnBehalfOfUser` mithilfe eines Web-Services auf. Diese Methode gibt eine `AuthResult`-Instanz zurück, die die SAML-Bestätigung für diesen Benutzer enthält.

Verwenden Sie anschließend diese SAML-Bestätigung, um alle Services aufzurufen, für die eine Authentifizierung erforderlich ist. Diese Aktion umfasst das Senden der Bestätigung als Teil der SOAP-Kopfzeile. Wenn mit dieser Bestätigung ein Aufruf eines Web-Services erfolgt, identifiziert AEM Forms den Benutzer als den Benutzer, der durch diese Bestätigung dargestellt wird. Das heißt, der in der Bestätigung angegebene Benutzer ist der Benutzer, der den Service aufruft.

### Verwenden von Apache Axis-Klassen und SAML-basierter Authentifizierung {#using-apache-axis-classes-and-saml-based-authentication}

Sie können einen AEM Forms-Service über Java-Proxy-Klassen aufrufen, die mithilfe der Axis-Bibliothek erstellt wurden. (Siehe [Erstellen von Java-Proxy-Klassen mithilfe von Apache Axis](#creating-java-proxy-classes-using-apache-axis).)

Wenn Sie AXIS verwenden, das SAML-basierte Authentifizierung verwendet, registrieren Sie den Anfrage- und Antwort-Handler bei Axis. Apache Axis ruft den Handler auf, bevor eine Aufrufanforderung an AEM Forms gesendet wird. Um einen Handler zu registrieren, erstellen Sie eine Java-Klasse, die `org.apache.axis.handlers.BasicHandler` erweitert.

**Erstellen eines AssertionHandlers mit Axis**

Die folgende Java-Klasse mit dem Namen `AssertionHandler.java` zeigt ein Beispiel einer Java-Klasse, die `org.apache.axis.handlers.BasicHandler` erweitert.

```java
 public class AssertionHandler extends BasicHandler {
        public void invoke(MessageContext ctx) throws AxisFault {
            String assertion = (String) ctx.getProperty(LC_ASSERTION);
 
            //no assertion hence nothing to insert
            if(assertion == null) return;
 
            try {
                MessageElement samlElement = new MessageElement(convertToXML(assertion));
                SOAPHeader header = (SOAPHeader) ctx.getRequestMessage().getSOAPHeader();
                //Create the wsse:Security element which would contain the SAML element
                SOAPElement wsseHeader = header.addChildElement("Security", "wsse", WSSE_NS);
                wsseHeader.appendChild(samlElement);
                //remove the actor attribute as in LC we do not specify any actor. This would not remove the actor attribute though
                //it would only remove it from the soapenv namespace
                wsseHeader.getAttributes().removeNamedItem("actor");
            } catch (SOAPException e) {
                throw new AxisFault("Error occured while adding the assertion to the SOAP Header",e);
            }
        }
 }
```

**Registrieren des Handlers**

Um einen Handler bei Axis zu registrieren, erstellen Sie eine Datei „client-config.wsdd“. Standardmäßig sucht Axis nach einer Datei mit diesem Namen. Der folgende XML-Code ist ein Beispiel für eine Datei „client-config.wsdd“. Weitere Informationen finden Sie in der Dokumentation zu Axis.

```xml
 <deployment xmlns="https://xml.apache.org/axis/wsdd/" xmlns:java="https://xml.apache.org/axis/wsdd/providers/java">
     <transport name="http" pivot="java:org.apache.axis.transport.http.HTTPSender"/>
      <globalConfiguration >
       <requestFlow >
        <handler type="java:com.adobe.idp.um.example.AssertionHandler" />
       </requestFlow >
      </globalConfiguration >
 </deployment>
 
```

**Aufrufen eines AEM Forms-Service**

Im folgenden Code-Beispiel wird ein AEM Forms-Service mit SAML-basierter Authentifizierung aufgerufen.

```java
 public class ImpersonationExample {
        . . .
        public void  authenticateOnBehalf(String superUsername,String password,
                String canonicalName,String domainName) throws UMException, RemoteException{
            ((org.apache.axis.client.Stub) authenticationManager).setUsername(superUsername);
            ((org.apache.axis.client.Stub) authenticationManager).setPassword(password);
 
            //Step 1 - Invoke the Auth manager api to get an assertion for the user to be impersonated
            AuthResult ar = authenticationManager.getAuthResultOnBehalfOfUser(canonicalName, domainName, null);
            String assertion = ar.getAssertion();
            //Step 2 - Setting the assertion here to be picked later by the AssertionHandler. Note that stubs are not threadSafe
            //hence should not be reused. For this simple example we have made them instance variable but care should be taken
            //regarding the thread safety
            ((javax.xml.rpc.Stub) authorizationManager)._setProperty(AssertionHandler.LC_ASSERTION, assertion);
        }
 
        public Role findRole(String roleId) throws UMException, RemoteException{
            //This api would be invoked under bob's user rights
            return authorizationManager.findRole(roleId);
        }
 
        public static void main(String[] args) throws Exception {
            ImpersonationExample ie = new ImpersonationExample("http://localhost:5555");
            //Get the SAML assertion for the user to impersonate and store it in stub
            ie.authenticateOnBehalf(
                    "administrator", //The Super user which has the required impersonation permission
                    "password", // Password of the super user as referred above
                    "bob", //Cannonical name of the user to impersonate
                    "testdomain" //Domain of the user to impersonate
                    );
 
            Role r = ie.findRole("BASIC_ROLE_ADMINISTRATOR");
            System.out.println("Role "+r.getName());
        }
 }
```

### Verwenden einer .NET-Client-Assembly und einer SAML-basierten Authentifizierung {#using-a-net-client-assembly-and-saml-based-authentication}

Sie können einen Forms-Service mithilfe einer .NET-Client-Assembly und einer SAML-basierten Authentifizierung aufrufen. Dazu müssen Sie Web Service Enhancements 3.0 (WSE) verwenden. Informationen zum Erstellen einer .NET-Client-Assembly, die WSE verwendet, finden Sie unter [Erstellen eines .NET-Projekts, das DIME verwendet](#creating-a-net-project-that-uses-dime).

>[!NOTE]
>
>Im DIME-Abschnitt wird WSE 2.0 verwendet. Um eine SAML-basierte Authentifizierung zu verwenden, folgen Sie den Anweisungen, die im DIME-Thema angegeben sind. Ersetzen Sie jedoch WSE 2.0 durch WSE 3.0. Installieren Sie Web Services Enhancements 3.0 auf Ihrem Entwicklungscomputer und integrieren Sie es in Microsoft Visual Studio .NET. Sie können Web Services Enhancements 3.0 aus dem [Microsoft-Download-Center](https://www.microsoft.com/downloads/search.aspx) herunterladen.

Die WSE-Architektur verwendet die Datentypen Richtlinien, Assertionen und SecurityToken. Für einen Webservice-Aufruf geben Sie eine Richtlinie an. Eine Richtlinie kann über mehrere Assertionen verfügen. Jede Assertion kann Filter enthalten. Ein Filter wird in bestimmten Phasen eines Webservice-Aufrufs aufgerufen und kann zu diesem Zeitpunkt die SOAP-Anforderung ändern. Ausführliche Informationen finden Sie in der Dokumentation zu Web Service Enhancements 3.0.

**Erstellen von Assertion und Filter**

Im folgenden C#-Code-Beispiel werden Filter- und Assertionsklassen erstellt. In diesem Code-Beispiel wird ein SamlAssertionOutputFilter erstellt. Dieser Filter wird vom WSE-Framework aufgerufen, bevor die SOAP-Anforderung an AEM Forms gesendet wird.

```java
 class LCSamlPolicyAssertion : Microsoft.Web.ServicES4.Design.PolicyAssertion
 {
        public override Microsoft.Web.ServicES4.SoapFilter CreateClientOutputFilter(FilterCreationContext context)
        {
           return new SamlAssertionOutputFilter();
        }
        . . .
 }
 
 
 class SamlAssertionOutputFilter : SendSecurityFilter
 {
        public override void SecureMessage(SoapEnvelope envelope, Security security)
        {
           // Get the SamlToken from the SessionState
           SamlToken samlToken = envelope.Context.Credentials.UltimateReceiver.GetClientToken<SamlToken>();
           security.Tokens.Add(samlToken);
        }
 }
```

**Erstellen des SAML-Tokens**

Erstellen Sie eine Klasse, die die SAML-Assertion darstellt. Die Hauptaufgabe dieser Klasse besteht darin, Datenwerte aus der Zeichenfolge in XML zu konvertieren und Leerzeichen beizubehalten. Diese Assertions-XML wird später in die SOAP-Anforderung importiert.

```java
 class SamlToken : SecurityToken
 {
        public const string SAMLAssertion = "https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1";
        private XmlElement _assertionElement;
 
        public SamlToken(string assertion)
             : base(SAMLAssertion)
        {
           XmlDocument xmlDoc = new XmlDocument();
           //The white space has to be preserved else the digital signature would get broken
           xmlDoc.PreserveWhitespace = true;
           xmlDoc.LoadXml(assertion);
           _assertionElement = xmlDoc.DocumentElement;
         }
 
         public override XmlElement GetXml(XmlDocument document)
         {
            return (XmlElement)document.ImportNode(_assertionElement, true);
         }
        . . .
 }
```

**Aufrufen eines AEM Forms-Service**

Im folgenden C#-Code-Beispiel wird ein Forms-Service mithilfe der SAML-basierten Authentifizierung aufgerufen.

```java
 public class ImpersonationExample
 {
        . . .
        public void AuthenticateOnBehalf(string superUsername, string password, string canonicalName, string domainName)
        {
            //Create a policy for UsernamePassword Token
            Policy usernamePasswordPolicy = new Policy();
            usernamePasswordPolicy.Assertions.Add(new UsernameOverTransportAssertion());
 
            UsernameToken token = new UsernameToken(superUsername, password, PasswordOption.SendPlainText);
            authenticationManager.SetClientCredential(token);
            authenticationManager.SetPolicy(usernamePasswordPolicy);
 
            //Get the SAML assertion for impersonated user
            AuthClient.AuthenticationManagerService.AuthResult ar
                = authenticationManager.getAuthResultOnBehalfOfUser(canonicalName, domainName, null);
            System.Console.WriteLine("Received assertion " + ar.assertion);
 
            //Create a policy for inserting SAML assertion
            Policy samlPolicy = new Policy();
            samlPolicy.Assertions.Add(new LCSamlPolicyAssertion());
            authorizationManager.SetPolicy(samlPolicy);
            //Set the SAML assertion obtained previously as the token
            authorizationManager.SetClientCredential(new SamlToken(ar.assertion));
        }
 
        public Role findRole(string roleId)
        {
            return authorizationManager.findRole(roleId);
        }
 
        static void Main(string[] args)
        {
            ImpersonationExample ie = new ImpersonationExample("http://localhost:5555");
            ie.AuthenticateOnBehalf(
                 "administrator", //The Super user which has the required impersonation permission
                 "password", // Password of the super user as referred above
                 "bob", //Cannonical name of the user to impersonate
                 "testdomain" //Domain of the user to impersonate
                 );
 
         Role r = ie.findRole("BASIC_ROLE_ADMINISTRATOR");
            System.Console.WriteLine("Role "+r.name);
     }
 }
```

## Überlegungen zur Verwendung von Webservices {#related-considerations-when-using-web-services}

Manchmal treten Probleme beim Aufrufen bestimmter AEM Forms-Service-Vorgänge über Webservices auf. Ziel dieser Diskussion ist es, diese Probleme zu ermitteln und eine Lösung anzubieten, sofern eine Lösung verfügbar ist.

### Asynchrones Aufrufen von Service-Vorgängen {#invoking-service-operations-asynchronously}

Wenn Sie versuchen, einen AEM Forms-Dienstvorgang asynchron aufzurufen, z. B. den `htmlToPDF`-Vorgang von Generate PDF, tritt eine `SoapFaultException` auf. Um dieses Problem zu beheben, erstellen Sie eine XML-Datei mit benutzerdefinierter Bindung, die das `ExportPDF_Result`-Element und andere Elemente in verschiedenen Klassen zuordnet. Die folgende XML-Datei stellt eine benutzerdefinierte Bindungsdatei dar.

```xml
 <bindings
        xmlns:xsd="https://www.w3.org/2001/XMLSchema"
        xmlns:jxb="https://java.sun.com/xml/ns/jaxb" jxb:version="1.0"
        xmlns:wsdl="https://schemas.xmlsoap.org/wsdl/"
      wsdlLocation="http://localhost:8080/soap/services/GeneratePDFService?wsdl&async=true&lc_version=9.0.0"
        xmlns="https://java.sun.com/xml/ns/jaxws">
        <enableAsyncMapping>false</enableAsyncMapping>
        <package name="external_customize.client"/>
        <enableWrapperStyle>true</enableWrapperStyle>
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='ExportPDF_Result']">
            <jxb:class name="ExportPDFAsyncResult">
            </jxb:class>
        </bindings>
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='CreatePDF_Result']">
            <jxb:class name="CreatePDFAsyncResult">
            </jxb:class>
        </bindings>
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='HtmlToPDF_Result']">
            <jxb:class name="HtmlToPDFAsyncResult">
            </jxb:class>
        </bindings>
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='OptimizePDF_Result']">
            <jxb:class name="OptimizePDFAsyncResult">
            </jxb:class>
        </bindings>
        <!--bindings node="//wsdl:portType[@name='GeneratePDFService']/wsdl:operation[@name='HtmlToPDF_Result']">
            <jxb:class name="HtmlToPDFAsyncResult"/>
        </bindings-->
 </bindings>
```

Verwenden Sie diese XML-Datei beim Erstellen von Java-Proxy-Dateien mithilfe von JAX-WS. (Siehe [Erstellen von Java-Proxy-Klassen mithilfe von JAX-WS](#creating-java-proxy-classes-using-jax-ws).)

Referenzieren Sie diese XML-Datei beim Ausführen des JAX-WS-Tools („wsimport.exe“) mithilfe der Befehlszeilenoption „- `b`“. Aktualisieren Sie das `wsdlLocation`-Element in der Bindungs-XML-Datei, um die URL von AEM Forms anzugeben.

Um sicherzustellen, dass der asynchrone Aufruf funktioniert, ändern Sie den Endpunkt-URL-Wert und geben Sie `async=true` an. Geben Sie beispielsweise für Java-Proxy-Dateien, die mit JAX-WS erstellt werden, Folgendes für `BindingProvider.ENDPOINT_ADDRESS_PROPERTY` an.

`https://server:port/soap/services/ServiceName?wsdl&async=true&lc_version=9.0.0`

Die folgende Liste gibt andere Services an, die eine benutzerdefinierte Bindungsdatei benötigen, wenn sie asynchron aufgerufen werden:

* PDFG3D
* Task Manager
* Application Manager
* Directory Manager
* Distiller
* Rights Management
* Document Management

### Unterschiede bei J2EE-Anwendungsservern {#differences-in-j2ee-application-servers}

Manchmal ruft eine Proxy-Bibliothek, die mit einem bestimmten J2EE-Programm-Server erstellt wurde, nicht erfolgreich AEM Forms auf, das auf einem anderen J2EE-Programm-Server gehostet wird. Stellen Sie sich eine Proxy-Bibliothek vor, die mit AEM Forms generiert wird, das auf WebSphere bereitgestellt wird. Diese Proxy-Bibliothek kann AEM Forms-Services, die auf dem JBoss-Programm-Server bereitgestellt werden, nicht erfolgreich aufrufen.

Einige komplexe AEM Forms-Datentypen, z. B. `PrincipalReference`, werden bei der Bereitstellung von AEM Forms auf WebSphere im Vergleich zum JBoss-Programm-Server anders definiert. Der Grund für die Unterschiede in den WSDL-Definitionen liegt in den unterschiedlichen JDKs, die von den verschiedenen J2EE-Programm-Services verwendet werden. Verwenden Sie daher Proxy-Bibliotheken, die vom selben J2EE-Programm-Server generiert werden.

### Zugreifen auf mehrere Dienste mithilfe von Webdiensten {#accessing-multiple-services-using-web-services}

Aufgrund von Namespace-Konflikten können Datenobjekte nicht für mehrere Service-WSDLs freigegeben werden. Verschiedene Services können Datentypen gemeinsam nutzen. Daher nutzen die Services die Definition dieser Typen in den WSDLs gemeinsam. Sie können beispielsweise nicht zwei .NET-Client-Assemblys, die einen `BLOB`-Datentyp enthalten, zum selben .NET-Client-Projekt hinzufügen. Wenn Sie dies versuchen, tritt ein Kompilierungsfehler auf.

In der folgenden Liste sind Datentypen aufgeführt, die nicht von mehreren Service-WSDLs gemeinsam genutzt werden können:

* `User`
* `Principals`
* `PrincipalReference`
* `Groups`
* `Roles`
* `BLOB`

Um dieses Problem zu vermeiden, wird empfohlen, die Datentypen vollständig zu qualifizieren.  Betrachten Sie zum Beispiel ein .NET-Programm, das sowohl auf den Forms-Service als auch auf den Signature-Service mit einem Service-Verweis verweist. Beide Service-Verweise enthalten eine `BLOB`-Klasse. Um eine `BLOB`-Instanz verwenden zu können, müssen Sie das `BLOB`-Objekt bei der Deklaration vollständig qualifizieren. Dieser Ansatz wird im folgenden Code-Beispiel veranschaulicht. Informationen zu diesem Code-Beispiel finden Sie unter [Digitales Signieren von interaktiven Formularen](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-interactive-forms).

Im folgenden C#-Code-Beispiel wird ein interaktives Formular signiert, das vom Forms-Service gerendert wird. Das Client-Programm hat zwei Service-Verweise. Die `BLOB`-Instanz, die mit dem Forms-Service verbunden ist, gehört zum Namespace `SignInteractiveForm.ServiceReference2`. Analog dazu gehört die `BLOB`-Instanz, die mit dem Signature-Service verbunden ist, zum Namespace `SignInteractiveForm.ServiceReference1`. Das signierte interaktive Formular wird als PDF-Datei mit dem Namen *LoanXFASigned.pdf* gespeichert.

```csharp
 ???/**
     * Ensure that you create a .NET project that uses
     * MS Visual Studio 2008 and version 3.5 of the .NET
     * framework. This is required to invoke a
     * AEM Forms service using MTOM.
     *
     * For information, see "Invoking AEM Forms using MTOM" in Programming with AEM forms
     */
 using System;
 using System.Collections.Generic;
 using System.Linq;
 using System.Text;
 using System.ServiceModel;
 using System.IO;
 
 //A reference to the Signature service
 using SignInteractiveForm.ServiceReference1;
 
 //A reference to the Forms service
 using SignInteractiveForm.ServiceReference2;
 
 namespace SignInteractiveForm
 {
        class Program
        {
            static void Main(string[] args)
            {
                try
                {
                    //Because BLOB objects are used in both service references
                    //it is necessary to fully qualify the BLOB objects
 
                    //Retrieve the form -- invoke the Forms service
                    SignInteractiveForm.ServiceReference2.BLOB formData = GetForm();
 
                    //Create a BLOB object associated with the Signature service
                    SignInteractiveForm.ServiceReference1.BLOB sigData = new SignInteractiveForm.ServiceReference1.BLOB();
 
                    //Transfer the byte stream from one Forms BLOB object to the
                    //Signature BLOB object
                    sigData.MTOM = formData.MTOM;
 
                    //Sign the Form -- invoke the Signature service
                    SignForm(sigData);
                }
                catch (Exception ee)
                {
                    Console.WriteLine(ee.Message);
                }
            }
 
            //Creates an interactive PDF form based on a XFA form - invoke the Forms service
            private static SignInteractiveForm.ServiceReference2.BLOB GetForm()
            {
 
                try
                {
                    //Create a FormsServiceClient object
                    FormsServiceClient formsClient = new FormsServiceClient();
                    formsClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/FormsService?blob=mtom");
 
                    //Enable BASIC HTTP authentication
                    BasicHttpBinding b = (BasicHttpBinding)formsClient.Endpoint.Binding;
                    b.MessageEncoding = WSMessageEncoding.Mtom;
                    formsClient.ClientCredentials.UserName.UserName = "administrator";
                    formsClient.ClientCredentials.UserName.Password = "password";
                    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
                    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
                    b.MaxReceivedMessageSize = 2000000;
                    b.MaxBufferSize = 2000000;
                    b.ReaderQuotas.MaxArrayLength = 2000000;
 
                    //Create a BLOB to store form data
                    SignInteractiveForm.ServiceReference2.BLOB formData = new SignInteractiveForm.ServiceReference2.BLOB();
                    SignInteractiveForm.ServiceReference2.BLOB pdfForm = new SignInteractiveForm.ServiceReference2.BLOB();
 
                    //Specify an XML form data
                    string path = "C:\\Adobe\Loan.xml";
                    FileStream fs = new FileStream(path, FileMode.Open);
 
                    //Get the length of the file stream
                    int len = (int)fs.Length;
                    byte[] ByteArray = new byte[len];
 
                    fs.Read(ByteArray, 0, len);
                    formData.MTOM = ByteArray;
 
                    //Specify an XML form data
                    string path2 = "C:\\Adobe\LoanSigXFA.pdf";
                    FileStream fs2 = new FileStream(path2, FileMode.Open);
 
                    //Get the length of the file stream
                    int len2 = (int)fs2.Length;
                    byte[] ByteArray2 = new byte[len2];
 
                    fs2.Read(ByteArray2, 0, len2);
                    pdfForm.MTOM = ByteArray2;
 
                    PDFFormRenderSpec renderSpec = new PDFFormRenderSpec();
                    renderSpec.generateServerAppearance = true;
 
                    //Set out parameter values
                    long pageCount = 1;
                    String localValue = "en_US";
                    FormsResult result = new FormsResult();
 
                    //Render an interactive PDF form
                    formsClient.renderPDFForm2(
                        pdfForm,
                        formData,
                        renderSpec,
                        null,
                        null,
                        out pageCount,
                        out localValue,
                        out result);
 
                    //Write the data stream to the BLOB object
                    SignInteractiveForm.ServiceReference2.BLOB outForm = result.outputContent;
                    return outForm;
                }
                catch (Exception ee)
                {
                    Console.WriteLine(ee.Message);
                }
                return null;
            }
 
            //Sign the form -- invoke the Signature service
            private static void SignForm(SignInteractiveForm.ServiceReference1.BLOB inDoc)
            {
 
                try
                {
                    //Create a SignatureServiceClient object
                    SignatureServiceClient signatureClient = new SignatureServiceClient();
                    signatureClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/SignatureService?blob=mtom");
 
                    //Enable BASIC HTTP authentication
                    BasicHttpBinding b = (BasicHttpBinding)signatureClient.Endpoint.Binding;
                    b.MessageEncoding = WSMessageEncoding.Mtom;
                    signatureClient.ClientCredentials.UserName.UserName = "administrator";
                    signatureClient.ClientCredentials.UserName.Password = "password";
                    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
                    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
                    b.MaxReceivedMessageSize = 2000000;
                    b.MaxBufferSize = 2000000;
                    b.ReaderQuotas.MaxArrayLength = 2000000;
 
                    //Specify the name of the signature field
                    string fieldName = "form1[0].grantApplication[0].page1[0].SignatureField1[0]";
 
                    //Create a Credential object
                    Credential myCred = new Credential();
                    myCred.alias = "secure";
 
                    //Specify the reason to sign the document
                    string reason = "The document was reviewed";
 
                    //Specify the location of the signer
                    string location = "New York HQ";
 
                    //Specify contact information
                    string contactInfo = "Tony Blue";
 
                    //Create a PDFSignatureAppearanceOptions object
                    //and show date information
                    PDFSignatureAppearanceOptionSpec appear = new PDFSignatureAppearanceOptionSpec();
                    appear.showDate = true;
 
                    //Sign the PDF document
                    SignInteractiveForm.ServiceReference1.BLOB signedDoc = signatureClient.sign(
                        inDoc,
                        fieldName,
                        myCred,
                        HashAlgorithm.SHA1,
                        reason,
                        location,
                        contactInfo,
                        appear,
                        true,
                        null,
                        null,
                        null);
 
                    //Populate a byte array with BLOB data that represents the signed form
                    byte[] outByteArray = signedDoc.MTOM;
 
                    //Save the signed PDF document
                    string fileName = "C:\\Adobe\LoanXFASigned.pdf";
                    FileStream fs2 = new FileStream(fileName, FileMode.OpenOrCreate);
 
                    //Create a BinaryWriter object
                    BinaryWriter w = new BinaryWriter(fs2);
                    w.Write(outByteArray);
                    w.Close();
                    fs2.Close();
                }
 
                catch (Exception ee)
                {
                    Console.WriteLine(ee.Message);
                }
            }
        }
 }
 
 
```

### Services, die mit dem Buchstaben I beginnen, erzeugen ungültige Proxy-Dateien {#services-starting-with-the-letter-i-produce-invalid-proxy-files}

Die Namen einiger von AEM Forms generierter Proxyklassen sind bei Verwendung von Microsoft .Net 3.5 und WCF falsch. Dieses Problem tritt auf, wenn für den IBMFilenetContentRepositoryConnector, IDPSchedulerService oder einen anderen Dienst, dessen Name mit dem Buchstaben I beginnt, Proxy-Klassen erstellt werden. Beispielsweise lautet der Name des generierten Clients im Fall von IBMFileNetContentRepositoryConnector `BMFileNetContentRepositoryConnectorClient`. Der Buchstabe I fehlt in der generierten Proxy-Klasse.
