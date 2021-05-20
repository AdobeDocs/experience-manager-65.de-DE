---
title: AEM Forms mit Web Services aufrufen
seo-title: AEM Forms mit Web Services aufrufen
description: Rufen Sie AEM Forms-Prozesse mithilfe von Webdiensten mit vollständiger Unterstützung für die WSDL-Generierung auf.
seo-description: Rufen Sie AEM Forms-Prozesse mithilfe von Webdiensten mit vollständiger Unterstützung für die WSDL-Generierung auf.
uuid: 66bcd010-c476-4b66-831d-a48307d8d67a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: d5722281-bea9-4fc7-abdc-e678899e0a15
role: Developer
exl-id: 3139564f-9346-4933-8e39-2e1642bff097
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '10004'
ht-degree: 6%

---

# AEM Forms mit Web Services aufrufen {#invoking-aem-forms-using-web-services}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Die meisten AEM Forms-Dienste im Dienstcontainer sind so konfiguriert, dass sie einen Webdienst bereitstellen, mit voller Unterstützung für die WSDL-Generierung (Web Service Definition Language). Das heißt, Sie können Proxy-Objekte erstellen, die den nativen SOAP-Stapel eines AEM Forms-Dienstes verwenden. Daher können AEM Forms-Dienste die folgenden SOAP-Nachrichten austauschen und verarbeiten:

* **SOAP-Anforderung**: Wird von einer Client-Anwendung, die eine Aktion anfordert, an einen Forms-Dienst gesendet.
* **SOAP-Antwort**: Wird von einem Forms-Dienst an eine Clientanwendung gesendet, nachdem eine SOAP-Anforderung verarbeitet wurde.

Mithilfe von Webdiensten können Sie dieselben AEM Forms-Dienstvorgänge ausführen, die Sie auch über die Java-API ausführen können. Der Vorteil der Verwendung von Webdiensten zum Aufrufen von AEM Forms-Diensten besteht darin, dass Sie eine Clientanwendung in einer Entwicklungsumgebung erstellen können, die SOAP unterstützt. Eine Clientanwendung ist nicht an eine bestimmte Entwicklungsumgebung oder Programmiersprache gebunden. Sie können beispielsweise eine Clientanwendung mit Microsoft Visual Studio .NET und C# als Programmiersprache erstellen.

AEM Forms-Dienste werden über das SOAP-Protokoll bereitgestellt und sind mit WSI Basic Profile 1.1 kompatibel. Web Services Interoperability (WSI) ist eine offene Organisation, die die Interoperabilität von Webdiensten plattformübergreifend fördert. Weitere Informationen finden Sie unter [https://www.ws-i.org/](https://www.ws-i.org).

AEM Forms unterstützt die folgenden Webdienststandards:

* **Kodierung**: Unterstützt nur Dokumenten- und Literalkodierung (die gemäß WSI Basic Profile die bevorzugte Kodierung ist). (Siehe [AEM Forms mit Base64-Codierung aufrufen](#invoking-aem-forms-using-base64-encoding).)
* **MTOM**: Stellt eine Möglichkeit dar, Anlagen mit SOAP-Anforderungen zu kodieren. (Siehe [AEM Forms mit MTOM](#invoking-aem-forms-using-mtom) aufrufen.)
* **SwaRef**: Stellt eine andere Möglichkeit dar, Anlagen mit SOAP-Anforderungen zu kodieren. (Siehe [AEM Forms mithilfe von SwaRef](#invoking-aem-forms-using-swaref) aufrufen.)
* **SOAP mit Anhängen**: Unterstützt sowohl MIME als auch DIME (Direct Internet Message Encapulation). Diese Protokolle sind Standardmethoden zum Senden von Anhängen über SOAP. Microsoft Visual Studio .NET-Anwendungen verwenden DIME. (Siehe [AEM Forms mit Base64-Codierung aufrufen](#invoking-aem-forms-using-base64-encoding).)
* **WS-Sicherheit**: Unterstützt ein Benutzernamenkennwort-Token-Profil, das eine Standardmethode zum Senden von Benutzernamen und Passwörtern als Teil der SOAP-Kopfzeile von WS-Sicherheit darstellt. AEM Forms unterstützt auch die einfache HTTP-Authentifizierung. (Siehe [Übergeben von Anmeldeinformationen mithilfe von WS-Security-Headern](https://www.adobe.com/devnet/livecycle/articles/passing_credentials.html).)

Um AEM Forms-Dienste mit einem Webdienst aufzurufen, erstellen Sie normalerweise eine Proxy-Bibliothek, die die Dienst-WSDL verwendet. Der Abschnitt *AEM Forms mit Web Services* aufrufen verwendet JAX-WS, um Java-Proxyklassen zum Aufrufen von Diensten zu erstellen. (Siehe [Erstellen von Java-Proxy-Klassen mit JAX-WS](#creating-java-proxy-classes-using-jax-ws).)

Sie können einen Dienst-WDSL abrufen, indem Sie die folgende URL-Definition angeben (Elemente in Klammern sind optional):

```java
 https://<your_serverhost>:<your_port>/soap/services/<service_name>?wsdl[&version=<version>][&async=true|false][lc_version=<lc_version>]
```

hierbei gilt:

* *your_* serverhostrestellt die IP-Adresse des J2EE-Anwendungsservers dar, auf dem AEM Forms gehostet wird.
* *Ihr_* stellt den HTTP-Anschluss dar, den der J2EE-Anwendungsserver verwendet.
* *service_* name stellt den Dienstnamen dar.
* ** versionsteht für die Zielversion eines Dienstes (standardmäßig wird die neueste Dienstversion verwendet).
* `async` gibt den Wert an,  `true` um zusätzliche Vorgänge für asynchronen Aufruf zu aktivieren ( `false` standardmäßig ).
* *lc_* versionstellt die Version von AEM Forms dar, die Sie aufrufen möchten.

In der folgenden Tabelle sind die WSDL-Definitionen des Dienstes aufgeführt (vorausgesetzt, AEM Forms wird auf dem lokalen Host bereitgestellt und der Beitrag ist 8080).

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
   <td><p>Zurück und Wiederherstellen</p></td>
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

Sie müssen den Anwendungsnamen und den Prozessnamen in der WSDL-Definition angeben, um auf eine WSDL zuzugreifen, die zu einem in Workbench erstellten Prozess gehört. Angenommen, der Name der Anwendung ist `MyApplication` und der Name des Prozesses ist `EncryptDocument`. Geben Sie in diesem Fall die folgende WSDL-Definition an:

```java
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?wsdl
```

>[!NOTE]
>
>Weitere Informationen zum Beispiel für einen kurzlebigen Prozess `MyApplication/EncryptDocument` finden Sie unter [Beispiel für einen kurzlebigen Prozess](/help/forms/developing/aem-forms-processes.md).

>[!NOTE]
>
>Eine Anwendung kann Ordner enthalten. Geben Sie in diesem Fall die Ordnernamen in der WSDL-Definition an:

```java
 http://localhost:8080/soap/services/MyApplication/[<folderA>/.../<folderZ>/]EncryptDocument?wsdl
```

**Zugriff auf neue Funktionen mithilfe von Webdiensten**

Auf neue AEM Forms-Dienstfunktionen kann über Webdienste zugegriffen werden. In AEM Forms wird beispielsweise die Möglichkeit eingeführt, Anhänge mit MTOM zu kodieren. (Siehe [AEM Forms mit MTOM](#invoking-aem-forms-using-mtom) aufrufen.)

Um auf neue Funktionen zuzugreifen, die in AEM Forms eingeführt wurden, geben Sie in der WSDL-Definition das Attribut `lc_version` an. Um beispielsweise auf neue Dienstfunktionen (einschließlich MTOM-Unterstützung) zuzugreifen, geben Sie die folgende WSDL-Definition an:

```java
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?wsdl&lc_version=9.0.1
```

>[!NOTE]
>
>Stellen Sie beim Festlegen des Attributs `lc_version` sicher, dass Sie drei Stellen verwenden. Beispielsweise entspricht 9.0.1 Version 9.0.

**Webdienst-BLOB-Datentyp**

AEM Forms-Dienst-WSDLs definieren viele Datentypen. Einer der wichtigsten Datentypen, die in einem Webdienst verfügbar gemacht werden, ist der Typ `BLOB` . Dieser Datentyp wird bei der Arbeit mit AEM Forms Java-APIs der Klasse `com.adobe.idp.Document` zugeordnet. (Siehe [Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

Ein `BLOB` -Objekt sendet und ruft Binärdaten (z. B. PDF-Dateien, XML-Daten usw.) an und von AEM Forms-Diensten ab. Der Typ `BLOB` wird in einer Dienst-WSDL wie folgt definiert:

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

**Bereitstellen von BLOB-Objekten in Dienstanforderungen**

Wenn für einen AEM Forms-Dienstvorgang der Typ `BLOB` als Eingabewert erforderlich ist, erstellen Sie in Ihrer Anwendungslogik eine Instanz des Typs `BLOB` . (Viele der Schnellstarts des Webdienstes befinden sich unter *Programmieren mit AEM Formularen* und zeigen, wie mit einem BLOB-Datentyp gearbeitet wird.)

Weisen Sie den Feldern, die zur `BLOB`-Instanz gehören, wie folgt Werte zu:

* **Base64**: Um Daten als Text in einem Base64-Format zu übergeben, legen Sie die Daten im  `BLOB.binaryData` Feld fest und legen Sie den Datentyp im MIME-Format (z. B.  `application/pdf`) im  `BLOB.contentType` Feld fest. (Siehe [AEM Forms mit Base64-Codierung aufrufen](#invoking-aem-forms-using-base64-encoding).)
* **MTOM**: Um Binärdaten in einem MTOM-Anhang zu übergeben, legen Sie die Daten im  `BLOB.MTOM` Feld fest. Diese Einstellung hängt die Daten mithilfe des Java JAX-WS-Frameworks oder der nativen API des SOAP-Frameworks an die SOAP-Anfrage an. (Siehe [AEM Forms mit MTOM](#invoking-aem-forms-using-mtom) aufrufen.)
* **SwaRef**: Um Binärdaten in einem WS-I SwaRef-Anhang zu übergeben, legen Sie die Daten im  `BLOB.swaRef` Feld fest. Diese Einstellung hängt die Daten mithilfe des Java JAX-WS-Frameworks an die SOAP-Anforderung an. (Siehe [AEM Forms mithilfe von SwaRef](#invoking-aem-forms-using-swaref) aufrufen.)
* **MIME- oder DIME-Anlage**: Um Daten in einer MIME- oder DIME-Anlage zu übergeben, hängen Sie die Daten mithilfe der nativen API des SOAP-Frameworks an die SOAP-Anfrage an. Legen Sie die Anlagenkennung im Feld `BLOB.attachmentID` fest. (Siehe [AEM Forms mit Base64-Codierung aufrufen](#invoking-aem-forms-using-base64-encoding).)
* **Remote URL**: Wenn Daten auf einem Webserver gehostet werden und über eine HTTP-URL aufgerufen werden können, legen Sie die HTTP-URL im  `BLOB.remoteURL` Feld fest. (Siehe [Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](#invoking-aem-forms-using-blob-data-over-http).)

**Zugreifen auf Daten in BLOB-Objekten, die von Diensten zurückgegeben werden**

Das Übertragungsprotokoll für zurückgegebene `BLOB`-Objekte hängt von mehreren Faktoren ab, die in der folgenden Reihenfolge berücksichtigt werden und angehalten werden, wenn die Hauptbedingung erfüllt ist:

1. **Ziel-URL gibt das Übertragungsprotokoll** an. Wenn die beim SOAP-Aufruf angegebene Ziel-URL den Parameter `blob="`*BLOB_TYPE*&quot;enthält, bestimmt *BLOB_TYPE* das Übertragungsprotokoll. *BLOB_* TYPE ist ein Platzhalter für base64, dime, mime, http, mtom oder slagerf.
1. **Der SOAP-Endpunkt des Dienstes ist intelligent**. Wenn die folgenden Bedingungen erfüllt sind, werden die Ausgabedokumente unter Verwendung des gleichen Übertragungsprotokolls wie die Eingabedokumente zurückgegeben:

   * Der SOAP-Endpunktparameter des Diensts Standardprotokoll für Output Blob-Objekte ist auf Smart gesetzt.

      Für jeden Dienst mit einem SOAP-Endpunkt können Sie in der Administration Console das Übertragungsprotokoll für alle zurückgegebenen Blobs angeben. (Siehe [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63).)

   * Der AEM Forms-Dienst akzeptiert ein oder mehrere Dokumente als Eingabe.

1. **Der SOAP-Endpunkt des Dienstes ist nicht intelligent**. Das konfigurierte Protokoll bestimmt das Dokumentübertragungsprotokoll und die Daten werden im entsprechenden Feld `BLOB` zurückgegeben. Wenn der SOAP-Endpunkt beispielsweise auf DIME gesetzt ist, befindet sich der zurückgegebene Blob unabhängig vom Übertragungsprotokoll eines Eingabedokuments im Feld `blob.attachmentID` .
1. **Andernfalls**. Wenn ein Dienst den Dokumenttyp nicht als Eingabe verwendet, werden die Ausgabedokumente über das HTTP-Protokoll im Feld `BLOB.remoteURL` zurückgegeben.

Wie in der ersten Bedingung beschrieben, können Sie den Übertragungstyp für alle zurückgegebenen Dokumente sicherstellen, indem Sie die SOAP-Endpunkt-URL wie folgt mit einem Suffix erweitern:

```java
     https://<your_serverhost>:<your_port>/soap/services/<service
     name>?blob=base64|dime|mime|http|mtom|swaref
```

Im Folgenden finden Sie die Korrelation zwischen den Übertragungstypen und dem Feld, aus dem Sie die Daten abrufen:

* **Base64-Format**: Setzen Sie das  `blob` Suffix auf  `base64` , um die Daten im  `BLOB.binaryData` Feld zurückzugeben.
* **MIME- oder DIME-Anlage**: Setzen Sie das  `blob` Suffix auf  `DIME` oder ,  `MIME` um die Daten als entsprechenden Anlagentyp mit der im  `BLOB.attachmentID` Feld zurückgegebenen Anlagenkennung zurückzugeben. Verwenden Sie die proprietäre API des SOAP-Frameworks, um die Daten aus dem Anhang zu lesen.
* **Remote URL**: Setzen Sie das  `blob` Suffix auf ,  `http` um die Daten auf dem Anwendungsserver zu behalten und die URL zurückzugeben, die auf die Daten im  `BLOB.remoteURL` Feld verweist.
* **MTOM oder SwaRef**: Setzen Sie das  `blob` Suffix auf  `mtom` oder ,  `swaref` um die Daten als entsprechenden Anlagentyp mit der in den  `BLOB.MTOM` oder - `BLOB.swaRef` Feldern zurückgegebenen Anlagenkennung zurückzugeben. Verwenden Sie die native API des SOAP-Frameworks, um die Daten aus dem Anhang zu lesen.

>[!NOTE]
>
>Es wird empfohlen, beim Ausfüllen eines `BLOB` -Objekts durch Aufrufen der `setBinaryData` -Methode die Größe von 30 MB nicht zu überschreiten. Andernfalls besteht die Möglichkeit, dass eine `OutOfMemory` -Ausnahme auftritt.

>[!NOTE]
>
>JAX WS-basierte Anwendungen, die das MTOM-Übertragungsprotokoll verwenden, sind auf 25 MB an gesendeten und empfangenen Daten beschränkt. Diese Einschränkung ist auf einen Fehler in JAX-WS zurückzuführen. Wenn die kombinierte Größe Ihrer gesendeten und empfangenen Dateien 25 MB überschreitet, verwenden Sie das SwaRef-Übertragungsprotokoll anstelle des MTOM-Protokolls. Andernfalls besteht die Möglichkeit einer `OutOfMemory`-Ausnahme.

**MTOM-Übertragung von base64-kodierten Byte-Arrays**

Zusätzlich zum `BLOB`-Objekt unterstützt das MTOM-Protokoll alle Byte-Array-Parameter oder Byte-Array-Felder eines komplexen Typs. Dies bedeutet, dass Client-SOAP-Frameworks, die MTOM unterstützen, jedes `xsd:base64Binary`-Element als MTOM-Anhang senden können (anstelle eines base64-kodierten Texts). AEM Forms SOAP-Endpunkte können diesen Typ der Byte-Array-Kodierung lesen. Der AEM Forms-Dienst gibt jedoch immer einen Byte-Array-Typ als base64-kodierten Text zurück. Die Ausgabe-Byte-Array-Parameter unterstützen MTOM nicht.

AEM Forms-Dienste, die eine große Menge an Binärdaten zurückgeben, verwenden den Typ Dokument/BLOB anstelle des Byte-Array-Typs. Der Dokumenttyp ist bei der Übertragung großer Datenmengen viel effizienter.

## Webdienst-Datentypen {#web-service-data-types}

In der folgenden Tabelle sind die Java-Datentypen und der entsprechende Webdienst-Datentyp aufgeführt.

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
   <td><p>Der Typ <code>DATE</code> , der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;complexType name="DATE"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="date" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="calendar" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Wenn ein AEM Forms-Dienstvorgang den Wert <code>java.util.Date</code> als Eingabe verwendet, muss die SOAP-Clientanwendung das Datum im Feld <code>DATE.date</code> übergeben. Wenn Sie in diesem Fall das Feld <code>DATE.calendar</code> festlegen, wird eine Laufzeitausnahme ausgelöst. Wenn der Dienst einen Wert <code>java.util.Date</code> zurückgibt, wird das Datum im Feld <code>DATE.date</code> zurückgegeben.</p></td>
  </tr>
  <tr>
   <td><p><code>java.util.Calendar</code></p></td>
   <td><p>Der Typ <code>DATE</code> , der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;complexType name="DATE"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="date" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="calendar" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Wenn ein AEM Forms-Dienstvorgang den Wert <code>java.util.Calendar</code> als Eingabe verwendet, muss die SOAP-Clientanwendung das Datum im Feld <code>DATE.caledendar</code> übergeben. Wenn Sie in diesem Fall das Feld <code>DATE.date</code> festlegen, wird eine Laufzeitausnahme ausgelöst. Wenn der Dienst den Wert <code>java.util.Calendar</code> zurückgibt, wird das Datum im Feld <code>DATE.calendar</code> zurückgegeben. </p></td>
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
   <td><p>Der <code>apachesoap:Map</code>, der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;schema elementFormDefault="qualified" targetNamespace="https://xml.apache.org/xml-soap" xmlns="https://www.w3.org/2001/XMLSchema"&gt;</code></p><p><code>&lt;complexType name="mapItem"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element name="key" nillable="true" type="xsd:anyType"/&gt;</code></p><p><code>&lt;element name="value" nillable="true" type="xsd:anyType"/&gt;</code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p><code>&lt;complexType name="Map"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="unbounded" minOccurs="0" name="item" </code><code>type="apachesoap:mapItem"/&gt;</code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p><code>&lt;/schema&gt;</code></p><p>Die Zuordnung wird als Sequenz von Schlüssel/Wert-Paaren dargestellt.</p></td>
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
   <td><p>Der XML-Typ, der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;complexType name="XML"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="document" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="element" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Wenn ein AEM Forms-Dienstvorgang einen <code>org.w3c.dom.Document</code> -Wert akzeptiert, übergeben Sie die XML-Daten im Feld <code>XML.document</code> .</p><p>Das Festlegen des Felds <code>XML.element</code> verursacht eine Laufzeitausnahme. Wenn der Dienst ein <code>org.w3c.dom.Document</code> zurückgibt, werden die XML-Daten im Feld <code>XML.document</code> zurückgegeben.</p></td>
  </tr>
  <tr>
   <td><p><code>org.w3c.dom.Element</code></p></td>
   <td><p>Der XML-Typ, der in einer Dienst-WSDL wie folgt definiert ist:</p><p><code>&lt;complexType name="XML"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="document" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="element" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Wenn ein AEM Forms-Dienstvorgang einen <code>org.w3c.dom.Element</code> als Eingabe verwendet, übergeben Sie die XML-Daten im Feld <code>XML.element</code> .</p><p>Das Festlegen des Felds <code>XML.document</code> verursacht eine Laufzeitausnahme. Wenn der Dienst ein <code>org.w3c.dom.Element</code> zurückgibt, werden die XML-Daten im Feld <code>XML.element</code> zurückgegeben.</p></td>
  </tr>
 </tbody>
</table>

**Website für Adobe-Entwickler**

Die Adobe Developer-Website enthält den folgenden Artikel, der den Aufruf von AEM Forms-Diensten mithilfe der Webdienst-API behandelt:

[Erstellen von Formular-Rendering-ASP.NET-Anwendungen](https://www.adobe.com/devnet/livecycle/articles/asp_net.html)

[Aufrufen von Webdiensten mit benutzerdefinierten Komponenten](https://www.adobe.com/devnet/livecycle/articles/extend_webservices.html)

>[!NOTE]
>
>Unter Aufrufen von Webdiensten mit benutzerdefinierten Komponenten wird beschrieben, wie Sie eine AEM Forms-Komponente erstellen, die Webdienste von Drittanbietern aufruft.

## Erstellen von Java-Proxy-Klassen mithilfe von JAX-WS {#creating-java-proxy-classes-using-jax-ws}

Sie können JAX-WS verwenden, um eine Forms-Dienst-WSDL in Java-Proxyklassen zu konvertieren. Diese Klassen ermöglichen es Ihnen, AEM Forms-Dienstvorgänge aufzurufen. Mit Apache Ant können Sie ein Build-Skript erstellen, das Java-Proxy-Klassen generiert, indem Sie auf eine AEM Forms-Dienst-WSDL verweisen. Sie können JAX-WS-Proxy-Dateien generieren, indem Sie die folgenden Schritte ausführen:

1. Installieren Sie Apache Ant auf dem Clientcomputer. (Siehe [https://ant.apache.org/bindownload.cgi](https://ant.apache.org/bindownload.cgi).)

   * Fügen Sie den Ordner bin zu Ihrem Klassenpfad hinzu.
   * Legen Sie die Umgebungsvariable `ANT_HOME` auf den Ordner fest, in dem Sie Ant installiert haben.

1. Installieren Sie JDK 1.6 oder höher.

   * Fügen Sie den Ordner &quot;JDK bin&quot;zum Klassenpfad hinzu.
   * Fügen Sie den Ordner &quot;JRE bin&quot;zum Klassenpfad hinzu. Dieser bin befindet sich im Verzeichnis `[JDK_INSTALL_LOCATION]/jre` .
   * Legen Sie die Umgebungsvariable `JAVA_HOME` auf den Ordner fest, in dem Sie das JDK installiert haben.

   JDK 1.6 enthält das in der Datei &quot;build.xml&quot;verwendete Programm &quot;wsimport&quot;. JDK 1.5 enthält dieses Programm nicht.

1. Installieren Sie JAX-WS auf dem Clientcomputer. (Siehe [Java-API für XML Web Services](https://jax-ws.dev.java.net/jax-ws-ea3/docs/mtom-swaref.html).)
1. Verwenden Sie JAX-WS und Apache Ant, um Java-Proxyklassen zu generieren. Erstellen Sie ein Ant-Build-Skript, um diese Aufgabe durchzuführen. Das folgende Skript ist ein Beispiel für ein Ant-Build-Skript namens &quot;build.xml&quot;:

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

   Beachten Sie, dass die Eigenschaft `url` in diesem Ant-Build-Skript so eingestellt ist, dass sie auf die auf localhost ausgeführte Verschlüsselungsdienst-WSDL verweist. Die Eigenschaften `username` und `password` müssen auf einen gültigen AEM für den Benutzernamen und das Kennwort des Formulars festgelegt sein. Beachten Sie, dass die URL das Attribut `lc_version` enthält. Ohne Angabe der Option `lc_version` können Sie keine neuen AEM Forms-Dienstvorgänge aufrufen.

   >[!NOTE]
   >
   >Ersetzen Sie `EncryptionService`durch den AEM Forms-Dienstnamen, den Sie mithilfe von Java-Proxyklassen aufrufen möchten. Um beispielsweise Java-Proxy-Klassen für den Rights Management-Dienst zu erstellen, geben Sie Folgendes an:

   ```java
    http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1
   ```

1. Erstellen Sie eine BAT-Datei, um das Ant-Build-Skript auszuführen. Der folgende Befehl befindet sich in einer BAT-Datei, die für die Ausführung des Ant-Build-Skripts zuständig ist:

   ```java
    ant -buildfile "build.xml" wsdl
   ```

   Positionieren Sie das ANT-Build-Skript im Ordner C:\Program Files\Java\jaxws-ri\bin directory. Das Skript schreibt die JAVA-Dateien in .Ordner /classes . Das Skript generiert JAVA-Dateien, die den Dienst aufrufen können.

1. Verpacken Sie die JAVA-Dateien in einer JAR-Datei. Wenn Sie an Eclipse arbeiten, führen Sie die folgenden Schritte aus:

   * Erstellen Sie ein neues Java-Projekt, das zum Verpacken der JAVA-Proxy-Dateien in eine JAR-Datei verwendet wird.
   * Erstellen Sie einen Quellordner im Projekt.
   * Erstellen Sie ein `com.adobe.idp.services`-Paket im Ordner Quelle .
   * Wählen Sie das Paket `com.adobe.idp.services` aus und importieren Sie dann die JAVA-Dateien aus dem Ordner adobe/idp/services in das Paket.
   * Erstellen Sie bei Bedarf ein `org/apache/xml/xmlsoap`-Paket im Ordner Quelle .
   * Wählen Sie den Quellordner aus und importieren Sie dann die JAVA-Dateien aus dem Ordner org/apache/xml/xmlsoap .
   * Setzen Sie die Konformitätsstufe des Java-Compilers auf 5.0 oder höher.
   * Erstellen Sie das Projekt.
   * Exportieren Sie das Projekt als JAR-Datei.
   * Importieren Sie diese JAR-Datei in den Klassenpfad eines Client-Projekts. Importieren Sie außerdem alle JAR-Dateien, die sich im Ordner &lt;Installationsordner>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty befinden.

   >[!NOTE]
   >
   >Alle Schnellstarts des Java-Webdienstes (mit Ausnahme des Forms-Dienstes) unter Programmieren mit AEM Formularen erstellen Java-Proxy-Dateien mit JAX-WS. Darüber hinaus verwenden Sie SwaRef für alle Schnellstarts des Java-Webdienstes. (Siehe [AEM Forms mithilfe von SwaRef](#invoking-aem-forms-using-swaref) aufrufen.)

**Siehe auch**

[Erstellen von Java-Proxy-Klassen mit Apache Axis](#creating-java-proxy-classes-using-apache-axis)

[Aufrufen von AEM Forms mit der Base64-Kodierung](#invoking-aem-forms-using-base64-encoding)

[Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](#invoking-aem-forms-using-blob-data-over-http)

[Aufrufen von AEM Forms mithilfe von SwaRef](#invoking-aem-forms-using-swaref)

## Erstellen von Java-Proxy-Klassen mit Apache Axis {#creating-java-proxy-classes-using-apache-axis}

Sie können das Apache Axis WSDL2Java-Tool verwenden, um einen Forms-Dienst in Java-Proxyklassen zu konvertieren. Diese Klassen ermöglichen es Ihnen, Forms-Dienstvorgänge aufzurufen. Mit Apache Ant können Sie Bibliotheksdateien für Axis aus einer Dienst-WSDL generieren. Sie können die Apache-Achse unter der URL [https://ws.apache.org/axis/](https://ws.apache.org/axis/) herunterladen.

>[!NOTE]
>
>Die mit dem Forms-Dienst verknüpften Schnellstarts des Webdienstes verwenden Java-Proxyklassen, die mit Apache Axis erstellt wurden. Der Forms-Webdienst-Schnellstart verwendet auch Base64 als Kodierungstyp. (Siehe [Forms Service API-Schnellstarts](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts).)

Sie können Java-Bibliotheksdateien für Axis generieren, indem Sie die folgenden Schritte ausführen:

1. Installieren Sie Apache Ant auf dem Clientcomputer. Sie ist unter [https://ant.apache.org/bindownload.cgi](https://ant.apache.org/bindownload.cgi) verfügbar.

   * Fügen Sie den Ordner bin zu Ihrem Klassenpfad hinzu.
   * Legen Sie die Umgebungsvariable `ANT_HOME` auf den Ordner fest, in dem Sie Ant installiert haben.

1. Installieren Sie Apache Axis 1.4 auf dem Clientcomputer. Sie ist unter [https://ws.apache.org/axis/](https://ws.apache.org/axis/.md) verfügbar.
1. Richten Sie den Klassenpfad ein, um die Axis JAR-Dateien in Ihrem Webdienst-Client zu verwenden, wie in den Anweisungen zur Axis-Installation unter [https://ws.apache.org/axis/java/install.html](https://ws.apache.org/axis/java/install.html) beschrieben.
1. Verwenden Sie das Apache WSDL2Java-Tool in Axis, um Java-Proxy-Klassen zu generieren. Erstellen Sie ein Ant-Build-Skript, um diese Aufgabe durchzuführen. Das folgende Skript ist ein Beispiel für ein Ant-Build-Skript namens &quot;build.xml&quot;:

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

   Beachten Sie, dass die Eigenschaft `url` in diesem Ant-Build-Skript so eingestellt ist, dass sie auf die auf localhost ausgeführte Verschlüsselungsdienst-WSDL verweist. Die Eigenschaften `username` und `password` müssen auf einen gültigen AEM für den Benutzernamen und das Kennwort des Formulars festgelegt sein.

1. Erstellen Sie eine BAT-Datei, um das Ant-Build-Skript auszuführen. Der folgende Befehl befindet sich in einer BAT-Datei, die für die Ausführung des Ant-Build-Skripts zuständig ist:

   ```java
    ant -buildfile "build.xml" encryption-wsdl2java-client
   ```

   Die JAVA-Dateien werden in die Eigenschaft C:\JavaFiles folder as specified by the `output` geschrieben. Um den Forms-Dienst erfolgreich aufzurufen, importieren Sie diese JAVA-Dateien in Ihren Klassenpfad.

   Standardmäßig gehören diese Dateien zu einem Java-Paket mit dem Namen `com.adobe.idp.services`. Es wird empfohlen, diese JAVA-Dateien in einer JAR-Datei zu platzieren. Importieren Sie dann die JAR-Datei in den Klassenpfad Ihrer Client-Anwendung.

   >[!NOTE]
   >
   >Es gibt verschiedene Möglichkeiten, .JAVA-Dateien in eine JAR zu übertragen. Eine Möglichkeit ist die Verwendung einer Java IDE wie Eclipse. Erstellen Sie ein Java-Projekt und erstellen Sie ein `com.adobe.idp.services`Paket (alle .JAVA-Dateien gehören zu diesem Paket). Importieren Sie anschließend alle JAVA-Dateien in das Paket. Exportieren Sie das Projekt schließlich als JAR-Datei.

1. Ändern Sie die URL in der Klasse `EncryptionServiceLocator`, um den Kodierungstyp anzugeben. Um beispielsweise base64 zu verwenden, geben Sie `?blob=base64` an, um sicherzustellen, dass das `BLOB`-Objekt Binärdaten zurückgibt. Suchen Sie also in der Klasse `EncryptionServiceLocator` die folgende Codezeile:

   ```java
    http://localhost:8080/soap/services/EncryptionService;
   ```

   und ändern Sie sie in:

   ```java
    http://localhost:8080/soap/services/EncryptionService?blob=base64;
   ```

1. Fügen Sie die folgenden Axis JAR-Dateien zum Klassenpfad Ihres Java-Projekts hinzu:

   * activation.jar
   * achse.jar
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

   Diese JAR-Dateien befinden sich im Verzeichnis `[install directory]/Adobe/Adobe Experience Manager Forms/sdk/lib/thirdparty` .

**Siehe auch**

[Erstellen von Java-Proxyklassen mithilfe von JAX-WS](#creating-java-proxy-classes-using-jax-ws)

[Aufrufen von AEM Forms mit der Base64-Kodierung](#invoking-aem-forms-using-base64-encoding)

[Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP](#invoking-aem-forms-using-blob-data-over-http)

## Aufrufen von AEM Forms mit Base64-Kodierung {#invoking-aem-forms-using-base64-encoding}

Sie können einen AEM Forms-Dienst mit der Base64-Kodierung aufrufen. Base64-Kodierung kodiert Anlagen, die mit einer Webdienstaufrufanforderung gesendet werden. Das heißt, die `BLOB`-Daten sind Base64-kodiert, nicht die gesamte SOAP-Nachricht.

&quot;AEM Forms mit Base64-Kodierung aufrufen&quot;beschreibt den Aufruf des folgenden kurzlebigen AEM Forms-Prozesses namens `MyApplication/EncryptDocument` mithilfe der Base64-Kodierung.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

### Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung {#creating-a-net-client-assembly-that-uses-base64-encoding} verwendet

Sie können eine .NET-Client-Assembly erstellen, um einen Forms-Dienst aus einem Microsoft Visual Studio .NET-Projekt aufzurufen. Führen Sie die folgenden Schritte aus, um eine .NET-Client-Assembly zu erstellen, die die Base64-Kodierung verwendet:

1. Erstellen Sie eine Proxy-Klasse basierend auf einer AEM Forms-Aufruf-URL.
1. Erstellen Sie ein Microsoft Visual Studio .NET-Projekt, das die .NET-Client-Assembly erzeugt.

**Proxy-Klasse erstellen**

Sie können mithilfe eines Tools, das Microsoft Visual Studio begleitet, eine Proxyklasse erstellen, die zum Erstellen der .NET-Clientassembly verwendet wird. Der Name des Tools ist wsdl.exe und befindet sich im Installationsordner von Microsoft Visual Studio. Um eine Proxy-Klasse zu erstellen, öffnen Sie die Eingabeaufforderung und navigieren Sie zu dem Ordner, der die Datei wsdl.exe enthält. Weitere Informationen zum Tool wsdl.exe finden Sie in der *MSDN-Hilfe*.

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:

```java
 wsdl https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
```

Standardmäßig erstellt dieses Tool eine CS-Datei im selben Ordner, der auf dem Namen der WSDL basiert. In diesem Fall wird eine CS-Datei mit dem Namen *EncryptDocumentService.cs* erstellt. Mit dieser CSS-Datei erstellen Sie ein Proxy-Objekt, mit dem Sie den Dienst aufrufen können, der in der Aufruf-URL angegeben wurde.

Ändern Sie die URL in der Proxy-Klasse, um `?blob=base64` einzuschließen, um sicherzustellen, dass das `BLOB`-Objekt Binärdaten zurückgibt. Suchen Sie in der Proxy-Klasse die folgende Codezeile:

```java
 "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument";
```

und ändern Sie sie in:

```java
 "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64";
```

Im Abschnitt *AEM Forms mit Base64 Encoding* aufrufen wird `MyApplication/EncryptDocument` als Beispiel verwendet. Wenn Sie eine .NET-Clientassembly für einen anderen Forms-Dienst erstellen, stellen Sie sicher, dass Sie `MyApplication/EncryptDocument` durch den Namen des Dienstes ersetzen.

**Entwickeln der .NET-Clientassembly**

Erstellen Sie ein Visual Studio-Klassenbibliotheksprojekt, das eine .NET-Client-Assembly erzeugt. Die CS-Datei, die Sie mit wsdl.exe erstellt haben, kann in dieses Projekt importiert werden. Dieses Projekt erzeugt eine DLL-Datei (die .NET-Client-Assembly), die Sie in anderen Visual Studio .NET-Projekten zum Aufrufen eines Dienstes verwenden können.

1. Starten Sie Microsoft Visual Studio .NET.
1. Erstellen Sie ein Klassenbibliotheksprojekt und nennen Sie es DocumentService.
1. Importieren Sie die CS-Datei, die Sie mit wsdl.exe erstellt haben.
1. Wählen Sie im Menü **Projekt** **Referenz hinzufügen** aus.
1. Wählen Sie im Dialogfeld Verweis hinzufügen **System.Web.Services.dll** aus.
1. Klicken Sie auf **Wählen Sie** und klicken Sie dann auf **OK**.
1. Kompilieren und erstellen Sie das Projekt.

>[!NOTE]
>
>Durch dieses Verfahren wird eine .NET-Client-Assembly mit dem Namen DocumentService.dll erstellt, mit der Sie SOAP-Anforderungen an den Dienst `MyApplication/EncryptDocument` senden können.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie `?blob=base64` zur URL in der Proxyklasse hinzugefügt haben, die zum Erstellen der .NET-Client-Assembly verwendet wird. Andernfalls können Sie keine Binärdaten vom `BLOB`-Objekt abrufen.

**Referenzieren der .NET-Clientassembly**

Platzieren Sie die neu erstellte .NET-Clientassembly auf dem Computer, auf dem Sie Ihre Clientanwendung entwickeln. Nachdem Sie die .NET-Client-Assembly in einem Verzeichnis platziert haben, können Sie sie aus einem Projekt referenzieren. Verweisen Sie auch auf die Bibliothek `System.Web.Services` aus Ihrem Projekt. Wenn Sie diese Bibliothek nicht referenzieren, können Sie die .NET-Client-Assembly nicht zum Aufrufen eines Dienstes verwenden.

1. Wählen Sie im Menü **Projekt** **Referenz hinzufügen** aus.
1. Klicken Sie auf die Registerkarte **.NET** .
1. Klicken Sie auf **Browse** und suchen Sie die Datei &quot;DocumentService.dll&quot;.
1. Klicken Sie auf **Wählen Sie** und klicken Sie dann auf **OK**.

**Aufrufen eines Dienstes mit einer .NET-Client-Assembly, die die Base64-Kodierung verwendet**

Sie können den Dienst `MyApplication/EncryptDocument` (der in Workbench erstellt wurde) mithilfe einer .NET-Client-Assembly aufrufen, die die Base64-Kodierung verwendet. Um den Dienst `MyApplication/EncryptDocument` aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Dienst-WSDL `MyApplication/EncryptDocument` verwendet.
1. Erstellen Sie ein Microsoft .NET-Clientprojekt. Verweisen Sie im Clientprojekt auf die Microsoft .NET-Clientassembly. Siehe auch `System.Web.Services`.
1. Erstellen Sie mit der Microsoft .NET-Clientassembly ein `MyApplication_EncryptDocumentService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.
1. Legen Sie die `MyApplication_EncryptDocumentService` -Eigenschaft des Objekts `Credentials` mit einem `System.Net.NetworkCredential` -Objekt fest. Geben Sie im Konstruktor `System.Net.NetworkCredential` einen AEM Formular-Benutzernamen und das entsprechende Kennwort an. Legen Sie Authentifizierungswerte fest, damit Ihre .NET-Clientanwendung SOAP-Nachrichten erfolgreich mit AEM Forms austauschen kann.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das an den `MyApplication/EncryptDocument`-Prozess übergeben wird.
1. Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
1. Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
1. Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
1. Füllen Sie das `BLOB`-Objekt, indem Sie dessen `binaryData`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die `MyApplication_EncryptDocumentService` -Methode des Objekts `invoke` aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB` -Objekts zurück.
1. Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des kennwortverschlüsselten Dokuments darstellt.
1. Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `MyApplicationEncryptDocumentService` -Methode des Objekts `invoke` zurückgegeben wird. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `binaryData` abrufen.
1. Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
1. Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

### Aufrufen eines Dienstes mit Java-Proxy-Klassen und Base64-Kodierung {#invoking-a-service-using-java-proxy-classes-and-base64-encoding}

Sie können einen AEM Forms-Dienst mithilfe von Java-Proxyklassen und Base64 aufrufen. So rufen Sie den Dienst `MyApplication/EncryptDocument` mithilfe von Java-Proxyklassen auf:

1. Erstellen Sie Java-Proxyklassen mit JAX-WS, die die Service-WSDL `MyApplication/EncryptDocument` verwenden. Verwenden Sie den folgenden WSDL-Endpunkt:

   `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1`

   >[!NOTE]
   >
   >Ersetzen Sie `hiro-xp` *durch die IP-Adresse des J2EE-Anwendungsservers, der als Host für AEM Forms dient.*

1. Verpacken Sie die mit JAX-WS erstellten Java-Proxyklassen in eine JAR-Datei.
1. Schließen Sie die Java-Proxy-JAR-Datei und die JAR-Dateien im folgenden Pfad ein:

   &lt;install Directory=&quot;&quot;>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in den Klassenpfad Ihres Java-Client-Projekts.

1. Erstellen Sie ein Objekt `MyApplicationEncryptDocumentService`, indem Sie den Konstruktor verwenden.
1. Erstellen Sie ein `MyApplicationEncryptDocument` -Objekt, indem Sie die `getEncryptDocument` -Methode des Objekts `MyApplicationEncryptDocumentService` aufrufen.
1. Legen Sie die zum Aufrufen von AEM Forms erforderlichen Verbindungswerte fest, indem Sie den folgenden Datenmitgliedern Werte zuweisen:

   * Weisen Sie den WSDL-Endpunkt und den Kodierungstyp dem `javax.xml.ws.BindingProvider` -Feld des Objekts `ENDPOINT_ADDRESS_PROPERTY` zu. Um den Dienst `MyApplication/EncryptDocument` mit der Base64-Kodierung aufzurufen, geben Sie den folgenden URL-Wert an:

      `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64`

   * Weisen Sie den AEM forms-Benutzer dem `javax.xml.ws.BindingProvider` -Objektfeld `USERNAME_PROPERTY` zu.
   * Weisen Sie den entsprechenden Kennwortwert dem `javax.xml.ws.BindingProvider` -Feld des Objekts `PASSWORD_PROPERTY` zu.

   Das folgende Codebeispiel zeigt diese Anwendungslogik:

   ```java
    //Set connection values required to invoke AEM Forms
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64";
    String username = "administrator";
    String password = "password";
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Rufen Sie das PDF-Dokument ab, das an den `MyApplication/EncryptDocument`-Prozess gesendet werden soll, indem Sie ein `java.io.FileInputStream`-Objekt mit dessen Konstruktor erstellen. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
1. Erstellen Sie ein Byte-Array und füllen Sie es mit dem Inhalt des `java.io.FileInputStream` -Objekts.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
1. Füllen Sie das `BLOB`-Objekt, indem Sie seine `setBinaryData`-Methode aufrufen und das Byte-Array übergeben. Das `BLOB` -Objekt `setBinaryData` ist die Methode, die bei Verwendung der Base64-Kodierung aufgerufen wird. Siehe Bereitstellen von BLOB-Objekten in Dienstanforderungen.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die `invoke` -Methode des Objekts `MyApplicationEncryptDocument` aufrufen. Übergeben Sie das `BLOB`-Objekt, das das PDF-Dokument enthält. Die invoke -Methode gibt ein `BLOB` -Objekt zurück, das das verschlüsselte PDF-Dokument enthält.
1. Erstellen Sie ein Byte-Array, das das verschlüsselte PDF-Dokument enthält, indem Sie die `getBinaryData` -Methode des Objekts `BLOB` aufrufen.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei. Schreiben Sie das Byte-Array in eine Datei.

**Siehe auch**

[Schnellstart: Aufrufen eines Dienstes mit Java-Proxy-Dateien und Base64-Kodierung](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-java-proxy-files-and-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](#creating-a-net-client-assembly-that-uses-base64-encoding)

## Aufrufen von AEM Forms mithilfe von MTOM {#invoking-aem-forms-using-mtom}

Sie können AEM Forms-Dienste mithilfe des Webdienststandards MTOM aufrufen. Dieser Standard definiert, wie binäre Daten wie PDF-Dokumente über das Internet oder Intranet übertragen werden. Eine Funktion von MTOM ist die Verwendung des Elements `XOP:Include` . Dieses Element ist in der XML Binary Optimized Packaging (XOP)-Spezifikation definiert, um auf die binären Anhänge einer SOAP-Nachricht zu verweisen.

In der Diskussion geht es um die Verwendung von MTOM zum Aufrufen des folgenden kurzlebigen AEM Forms-Prozesses mit dem Namen `MyApplication/EncryptDocument`.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

>[!NOTE]
>
>MTOM-Unterstützung wurde in AEM Forms, Version 9 hinzugefügt.

>[!NOTE]
>
>JAX WS-basierte Anwendungen, die das MTOM-Übertragungsprotokoll verwenden, sind auf 25 MB an gesendeten und empfangenen Daten beschränkt. Diese Einschränkung ist auf einen Fehler in JAX-WS zurückzuführen. Wenn die kombinierte Größe Ihrer gesendeten und empfangenen Dateien 25 MB überschreitet, verwenden Sie das SwaRef-Übertragungsprotokoll anstelle des MTOM-Protokolls. Andernfalls besteht die Möglichkeit einer `OutOfMemory`-Ausnahme.

Hier geht es um die Verwendung von MTOM in einem Microsoft .NET-Projekt zum Aufrufen von AEM Forms-Diensten. Das verwendete .NET-Framework ist 3.5 und die Entwicklungsumgebung ist Visual Studio 2008. Wenn Sie auf Ihrem Entwicklungscomputer Web Service Enhancements (WSE) installiert haben, entfernen Sie es. Das .NET 3.5-Framework unterstützt ein SOAP-Framework namens Windows Communication Foundation (WCF). Beim Aufrufen von AEM Forms mithilfe von MTOM wird nur WCF (nicht WSE) unterstützt.

### Erstellen eines .NET-Projekts, das einen Dienst mit MTOM {#creating-a-net-project-that-invokes-a-service-using-mtom} aufruft

Sie können ein Microsoft .NET-Projekt erstellen, das einen AEM Forms-Dienst mithilfe von Webdiensten aufrufen kann. Erstellen Sie zunächst ein Microsoft .NET-Projekt mit Visual Studio 2008. Um einen AEM Forms-Dienst aufzurufen, erstellen Sie eine Dienstreferenz zum AEM Forms-Dienst, den Sie in Ihrem Projekt aufrufen möchten. Wenn Sie eine Dienstreferenz erstellen, geben Sie eine URL für den AEM Forms-Dienst an:

```java
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
```

Ersetzen Sie `localhost` durch die IP-Adresse des J2EE-Anwendungsservers, der als Host für AEM Forms dient. Ersetzen Sie `MyApplication/EncryptDocument` durch den Namen des aufzurufenden AEM Forms-Dienstes. Um beispielsweise einen Rights Management-Vorgang aufzurufen, geben Sie Folgendes an:

`http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`

Die Option `lc_version` stellt sicher, dass AEM Forms-Funktionen wie MTOM verfügbar sind. Ohne Angabe der Option `lc_version` können Sie AEM Forms nicht mit MTOM aufrufen.

Nachdem Sie eine Dienstreferenz erstellt haben, sind mit dem AEM Forms-Dienst verknüpfte Datentypen für die Verwendung in Ihrem .NET-Projekt verfügbar. Gehen Sie wie folgt vor, um ein .NET-Projekt zu erstellen, das einen AEM Forms-Dienst aufruft:

1. Erstellen Sie ein .NET-Projekt mit Microsoft Visual Studio 2008.
1. Wählen Sie im Menü **Projekt** **Dienstreferenz hinzufügen** aus.
1. Geben Sie im Dialogfeld **Adresse** die WSDL für den AEM Forms-Dienst an. Beispiel:

   ```java
    http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

1. Klicken Sie auf **Los** und dann auf **OK**.

### Aufrufen eines Dienstes mit MTOM in einem .NET-Projekt {#invoking-a-service-using-mtom-in-a-net-project}

Betrachten Sie den `MyApplication/EncryptDocument`-Prozess, der ein ungesichertes PDF-Dokument akzeptiert und ein kennwortverschlüsseltes PDF-Dokument zurückgibt. So rufen Sie den Prozess `MyApplication/EncryptDocument` (der in Workbench erstellt wurde) mithilfe von MTOM auf:

1. Erstellen Sie ein Microsoft .NET-Projekt.
1. Erstellen Sie ein `MyApplication_EncryptDocumentClient` -Objekt mithilfe des Standardkonstruktors.
1. Erstellen Sie ein `MyApplication_EncryptDocumentClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst und den Kodierungstyp angibt:

   ```java
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=mtom
   ```

   Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Stellen Sie jedoch sicher, dass Sie `?blob=mtom` angeben.

   >[!NOTE]
   >
   >Ersetzen Sie `hiro-xp` *durch die IP-Adresse des J2EE-Anwendungsservers, der als Host für AEM Forms dient.*

1. Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des `EncryptDocumentClient.Endpoint.Binding` -Datenelements abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
1. Setzen Sie das `System.ServiceModel.BasicHttpBinding`-Datenelement des `MessageEncoding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
1. Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

   * Weisen Sie dem Datenelement `MyApplication_EncryptDocumentClient.ClientCredentials.UserName.UserName` den Benutzernamen der AEM Formulare zu.
   * Weisen Sie dem Datenelement `MyApplication_EncryptDocumentClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
   * Weisen Sie den Konstantenwert `HttpClientCredentialType.Basic` dem Datenelement `BasicHttpBindingSecurity.Transport.ClientCredentialType` zu.
   * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` dem Datenelement `BasicHttpBindingSecurity.Security.Mode` zu.

   Das folgende Codebeispiel zeigt diese Aufgaben.

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

1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das an den `MyApplication/EncryptDocument`-Prozess übergeben wird.
1. Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
1. Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
1. Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
1. Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Datenelement mit dem Inhalt des Byte-Arrays zuweisen.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die `invoke` -Methode des Objekts `MyApplication_EncryptDocumentClient` aufrufen. Übergeben Sie das `BLOB`-Objekt, das das PDF-Dokument enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB` -Objekts zurück.
1. Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
1. Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `invoke` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
1. Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
1. Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

>[!NOTE]
>
>Die meisten AEM Forms-Dienstvorgänge haben einen MTOM-Schnellstart. Sie können diese Schnellstarts im entsprechenden Schnellstartabschnitt eines Dienstes anzeigen. Informationen zum Anzeigen des Schnellstartabschnitts &quot;Output&quot;finden Sie unter [Schnellstarts für Output Service-API für Output-Dienste](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap).

**Siehe auch**

[Schnellstart: Aufrufen eines Dienstes mit MTOM in einem .NET-Projekt](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-mtom-in-a-net-project)

[Zugreifen auf mehrere Dienste mithilfe von Webdiensten](#accessing-multiple-services-using-web-services)

[Erstellen einer ASP.NET-Webanwendung, die einen langlebigen, an Menschen orientierten Prozess aufruft](/help/forms/developing/invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

## Aufrufen von AEM Forms mithilfe von SwaRef {#invoking-aem-forms-using-swaref}

Sie können AEM Forms-Dienste mit SwaRef aufrufen. Der Inhalt des XML-Elements `wsi:swaRef` wird als Anhang innerhalb eines SOAP-Hauptteils gesendet, der den Verweis auf den Anhang speichert. Wenn Sie einen Forms-Dienst mithilfe von SwaRef aufrufen, erstellen Sie Java-Proxyklassen mithilfe der Java-API für XML Web Services (JAX-WS). (Siehe [Java-API für XML Web Services](https://jax-ws.dev.java.net/jax-ws-ea3/docs/mtom-swaref.html).)

In der Diskussion geht es um das Aufrufen des folgenden kurzlebigen Forms-Prozesses namens `MyApplication/EncryptDocument` mithilfe von SwaRef.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

>[!NOTE]
>
>SwaRef-Unterstützung in AEM Forms hinzugefügt

In der folgenden Diskussion wird beschrieben, wie Sie Forms-Dienste aufrufen, indem Sie SwaRef in einer Java-Clientanwendung verwenden. Die Java-Anwendung verwendet Proxy-Klassen, die mithilfe von JAX-WS erstellt wurden.

### Rufen Sie einen Dienst mit JAX-WS-Bibliotheksdateien auf, die SwaRef verwenden {#invoke-a-service-using-jax-ws-library-files-that-use-swaref}

Um den Prozess `MyApplication/EncryptDocument` mithilfe von Java-Proxy-Dateien aufzurufen, die mit JAX-WS und SwaRef erstellt wurden, führen Sie die folgenden Schritte aus:

1. Erstellen Sie Java-Proxyklassen mit JAX-WS, die die Service-WSDL `MyApplication/EncryptDocument` verwenden. Verwenden Sie den folgenden WSDL-Endpunkt:

   ```java
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

   Weitere Informationen finden Sie unter [Erstellen von Java-Proxy-Klassen mit JAX-WS](#creating-java-proxy-classes-using-jax-ws).

   >[!NOTE]
   >
   >Ersetzen Sie `hiro-xp` *durch die IP-Adresse des J2EE-Anwendungsservers, der als Host für AEM Forms dient.*

1. Verpacken Sie die mit JAX-WS erstellten Java-Proxyklassen in eine JAR-Datei.
1. Schließen Sie die Java-Proxy-JAR-Datei und die JAR-Dateien im folgenden Pfad ein:

   &lt;install Directory=&quot;&quot;>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in den Klassenpfad Ihres Java-Client-Projekts.

1. Erstellen Sie ein Objekt `MyApplicationEncryptDocumentService`, indem Sie den Konstruktor verwenden.
1. Erstellen Sie ein `MyApplicationEncryptDocument` -Objekt, indem Sie die `getEncryptDocument` -Methode des Objekts `MyApplicationEncryptDocumentService` aufrufen.
1. Legen Sie die zum Aufrufen von AEM Forms erforderlichen Verbindungswerte fest, indem Sie den folgenden Datenmitgliedern Werte zuweisen:

   * Weisen Sie den WSDL-Endpunkt und den Kodierungstyp dem `javax.xml.ws.BindingProvider` -Feld des Objekts `ENDPOINT_ADDRESS_PROPERTY` zu. Um den Dienst `MyApplication/EncryptDocument` mithilfe der SwaRef-Kodierung aufzurufen, geben Sie den folgenden URL-Wert an:

      ` https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=swaref`

   * Weisen Sie den AEM forms-Benutzer dem `javax.xml.ws.BindingProvider` -Objektfeld `USERNAME_PROPERTY` zu.
   * Weisen Sie den entsprechenden Kennwortwert dem `javax.xml.ws.BindingProvider` -Feld des Objekts `PASSWORD_PROPERTY` zu.

   Das folgende Codebeispiel zeigt diese Anwendungslogik:

   ```java
    //Set connection values required to invoke AEM Forms
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=swaref";
    String username = "administrator";
    String password = "password";
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Rufen Sie das PDF-Dokument ab, das an den `MyApplication/EncryptDocument`-Prozess gesendet werden soll, indem Sie ein `java.io.File`-Objekt mit dessen Konstruktor erstellen. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
1. Erstellen Sie ein `javax.activation.DataSource`-Objekt mit dem Konstruktor `FileDataSource` . Übergeben Sie das `java.io.File`-Objekt.
1. Erstellen Sie ein `javax.activation.DataHandler`-Objekt, indem Sie seinen Konstruktor verwenden und das `javax.activation.DataSource`-Objekt übergeben.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
1. Füllen Sie das `BLOB`-Objekt, indem Sie seine `setSwaRef`-Methode aufrufen und das `javax.activation.DataHandler`-Objekt übergeben.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die `MyApplicationEncryptDocument` -Methode des Objekts `invoke` aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument enthält. Die invoke -Methode gibt ein `BLOB` -Objekt zurück, das ein verschlüsseltes PDF-Dokument enthält.
1. Füllen Sie ein `javax.activation.DataHandler` -Objekt, indem Sie die `getSwaRef` -Methode des `BLOB` -Objekts aufrufen.
1. Konvertieren Sie das `javax.activation.DataHandler`-Objekt in eine `java.io.InputSteam`-Instanz, indem Sie die `javax.activation.DataHandler`-Methode des Objekts `getInputStream` aufrufen.
1. Schreiben Sie die `java.io.InputSteam`-Instanz in eine PDF-Datei, die das verschlüsselte PDF-Dokument darstellt.

>[!NOTE]
>
>Die meisten AEM Forms-Dienstvorgänge haben einen SwaRef-Schnellstart. Sie können diese Schnellstarts im entsprechenden Schnellstartabschnitt eines Dienstes anzeigen. Informationen zum Anzeigen des Schnellstartabschnitts &quot;Output&quot;finden Sie unter [Schnellstarts für Output Service-API für Output-Dienste](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap).

**Siehe auch**

[Schnellstart: Aufrufen eines Dienstes mit SwaRef in einem Java-Projekt](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-swaref-in-a-java-project)

## Aufrufen von AEM Forms mithilfe von BLOB-Daten über HTTP {#invoking-aem-forms-using-blob-data-over-http}

Sie können AEM Forms-Dienste über Webdienste aufrufen und BLOB-Daten über HTTP übergeben. Die Übergabe von BLOB-Daten über HTTP ist eine alternative Methode, anstatt die Base64-Kodierung, DIME oder MIME zu verwenden. Beispielsweise können Sie Daten über HTTP in einem Microsoft .NET-Projekt übergeben, das Web Service Enhancement 3.0 verwendet, das DIME oder MIME nicht unterstützt. Bei Verwendung von BLOB-Daten über HTTP werden Eingabedaten hochgeladen, bevor der AEM Forms-Dienst aufgerufen wird.

&quot;AEM Forms mithilfe von BLOB-Daten über HTTP aufrufen&quot;beschreibt den Aufruf des folgenden kurzlebigen AEM Forms-Prozesses namens `MyApplication/EncryptDocument` durch Übergabe von BLOB-Daten über HTTP.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

>[!NOTE]
>
>Es wird empfohlen, dass Sie mit dem Aufrufen von AEM Forms mithilfe von SOAP vertraut sind. (Siehe [Aufrufen von AEM Forms mithilfe von Web Services](#invoking-aem-forms-using-web-services).)

### Erstellen einer .NET-Client-Assembly, die Daten über HTTP {#creating-a-net-client-assembly-that-uses-data-over-http} verwendet

Um eine Client-Assembly zu erstellen, die Daten über HTTP verwendet, folgen Sie dem unter [AEM Forms mit Base64-Codierung](#invoking-aem-forms-using-base64-encoding) aufrufen angegebenen Prozess. Ändern Sie jedoch die URL in der Proxy-Klasse so, dass sie `?blob=http` anstelle von `?blob=base64` enthält. Diese Aktion stellt sicher, dass Daten über HTTP übergeben werden. Suchen Sie in der Proxy-Klasse die folgende Codezeile:

```java
 "http://localhost:8080/soap/services/MyApplication/EncryptDocument";
```

und ändern Sie sie in:

```java
 "http://localhost:8080/soap/services/MyApplication/EncryptDocument?blob=http";
```

**Referenzieren der .NET clienMyApplication/EncryptDocument-Assembly**

Platzieren Sie die neue .NET-Clientassembly auf dem Computer, auf dem Sie Ihre Clientanwendung entwickeln. Nachdem Sie die .NET-Client-Assembly in einem Verzeichnis platziert haben, können Sie sie aus einem Projekt referenzieren. Referenzieren Sie die Bibliothek `System.Web.Services` aus Ihrem Projekt. Wenn Sie diese Bibliothek nicht referenzieren, können Sie die .NET-Client-Assembly nicht zum Aufrufen eines Dienstes verwenden.

1. Wählen Sie im Menü **Projekt** **Referenz hinzufügen** aus.
1. Klicken Sie auf die Registerkarte **.NET** .
1. Klicken Sie auf **Browse** und suchen Sie die Datei &quot;DocumentService.dll&quot;.
1. Klicken Sie auf **Wählen Sie** und klicken Sie dann auf **OK**.

**Aufrufen eines Dienstes mit einer .NET-Client-Assembly, die BLOB-Daten über HTTP verwendet**

Sie können den Dienst `MyApplication/EncryptDocument` (der in Workbench erstellt wurde) mithilfe einer .NET-Client-Assembly aufrufen, die Daten über HTTP verwendet. Um den Dienst `MyApplication/EncryptDocument` aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie die .NET-Client-Assembly.
1. Verweisen Sie auf die Microsoft .NET-Clientassembly. Erstellen Sie ein Microsoft .NET-Clientprojekt. Verweisen Sie im Clientprojekt auf die Microsoft .NET-Clientassembly. Siehe auch `System.Web.Services`.
1. Erstellen Sie mit der Microsoft .NET-Clientassembly ein `MyApplication_EncryptDocumentService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.
1. Legen Sie die `MyApplication_EncryptDocumentService` -Eigenschaft des Objekts `Credentials` mit einem `System.Net.NetworkCredential` -Objekt fest. Geben Sie im Konstruktor `System.Net.NetworkCredential` einen AEM Formular-Benutzernamen und das entsprechende Kennwort an. Legen Sie Authentifizierungswerte fest, damit Ihre .NET-Clientanwendung SOAP-Nachrichten erfolgreich mit AEM Forms austauschen kann.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um Daten an den `MyApplication/EncryptDocument`-Prozess zu übergeben.
1. Weisen Sie dem `remoteURL`-Datenelement des `BLOB`-Objekts einen Zeichenfolgenwert zu, der den URI-Speicherort eines PDF-Dokuments angibt, das an den `MyApplication/EncryptDocument`Dienst übergeben werden soll.
1. Rufen Sie den `MyApplication/EncryptDocument`-Prozess auf, indem Sie die `invoke` -Methode des Objekts `MyApplication_EncryptDocumentService` aufrufen und das `BLOB` -Objekt übergeben. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB` -Objekts zurück.
1. Erstellen Sie ein `System.UriBuilder` -Objekt, indem Sie seinen Konstruktor verwenden und den Wert des `BLOB` -Datenelements des zurückgegebenen `remoteURL`-Objekts übergeben.
1. Konvertieren Sie das `System.UriBuilder`-Objekt in ein `System.IO.Stream`-Objekt. (Der auf diese Liste folgende C#-Schnellstart zeigt, wie diese Aufgabe ausgeführt wird.)
1. Erstellen Sie ein Byte-Array und füllen Sie es mit den Daten aus dem `System.IO.Stream` -Objekt.
1. Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
1. Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

### Aufrufen eines Dienstes mit Java-Proxy-Klassen und BLOB-Daten über HTTP {#invoking-a-service-using-java-proxy-classes-and-blob-data-over-http}

Sie können einen AEM Forms-Dienst über Java-Proxyklassen und BLOB-Daten über HTTP aufrufen. So rufen Sie den Dienst `MyApplication/EncryptDocument` mithilfe von Java-Proxyklassen auf:

1. Erstellen Sie Java-Proxyklassen mit JAX-WS, die die Service-WSDL `MyApplication/EncryptDocument` verwenden. Verwenden Sie den folgenden WSDL-Endpunkt:

   ```java
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

   Weitere Informationen finden Sie unter [Erstellen von Java-Proxy-Klassen mit JAX-WS](#creating-java-proxy-classes-using-jax-ws).

   >[!NOTE]
   >
   >Ersetzen Sie `hiro-xp` *durch die IP-Adresse des J2EE-Anwendungsservers, der als Host für AEM Forms dient.*

1. Verpacken Sie die mit JAX-WS erstellten Java-Proxyklassen in eine JAR-Datei.
1. Schließen Sie die Java-Proxy-JAR-Datei und die JAR-Dateien im folgenden Pfad ein:

   &lt;install Directory=&quot;&quot;>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in den Klassenpfad Ihres Java-Client-Projekts.

1. Erstellen Sie ein Objekt `MyApplicationEncryptDocumentService`, indem Sie den Konstruktor verwenden.
1. Erstellen Sie ein `MyApplicationEncryptDocument` -Objekt, indem Sie die `getEncryptDocument` -Methode des Objekts `MyApplicationEncryptDocumentService` aufrufen.
1. Legen Sie die zum Aufrufen von AEM Forms erforderlichen Verbindungswerte fest, indem Sie den folgenden Datenmitgliedern Werte zuweisen:

   * Weisen Sie den WSDL-Endpunkt und den Kodierungstyp dem `javax.xml.ws.BindingProvider` -Feld des Objekts `ENDPOINT_ADDRESS_PROPERTY` zu. Um den Dienst `MyApplication/EncryptDocument` über die HTTP-Kodierung mit BLOB aufzurufen, geben Sie den folgenden URL-Wert an:

      `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=http`

   * Weisen Sie den AEM forms-Benutzer dem `javax.xml.ws.BindingProvider` -Objektfeld `USERNAME_PROPERTY` zu.
   * Weisen Sie den entsprechenden Kennwortwert dem `javax.xml.ws.BindingProvider` -Feld des Objekts `PASSWORD_PROPERTY` zu.

   Das folgende Codebeispiel zeigt diese Anwendungslogik:

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
1. Füllen Sie das `BLOB`-Objekt, indem Sie dessen `setRemoteURL`-Methode aufrufen. Übergeben Sie einen string -Wert, der den URI-Speicherort eines PDF-Dokuments angibt, das an den `MyApplication/EncryptDocument`-Dienst übergeben werden soll.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die `MyApplicationEncryptDocument` -Methode des Objekts `invoke` aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB` -Objekts zurück.
1. Erstellen Sie ein Byte-Array, um den Datenstrom zu speichern, der das verschlüsselte PDF-Dokument darstellt. Rufen Sie die `getRemoteURL` -Methode des Objekts `BLOB` auf (verwenden Sie das `BLOB` -Objekt, das von der `invoke` -Methode zurückgegeben wird).
1. Erstellen Sie ein Objekt `java.io.File`, indem Sie den Konstruktor verwenden. Dieses Objekt stellt das verschlüsselte PDF-Dokument dar.
1. Erstellen Sie ein `java.io.FileOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.File`-Objekt übergeben.
1. Rufen Sie die `write` -Methode des Objekts `java.io.FileOutputStream` auf. Übergeben Sie das Byte-Array, das den Datenstrom enthält, der das verschlüsselte PDF-Dokument darstellt.

## AEM Forms mit DIME aufrufen {#invoking-aem-forms-using-dime}

Sie können AEM Forms-Dienste mithilfe von SOAP mit Anhängen aufrufen. AEM Forms unterstützt sowohl MIME- als auch DIME-Webdienststandards. Mit DIME können Sie binäre Anhänge, wie PDF-Dokumente, zusammen mit Aufrufanforderungen senden, anstatt den Anhang zu kodieren. Der Abschnitt *AEM Forms mit DIME* aufrufen beschreibt den Aufruf des folgenden kurzlebigen AEM Forms-Prozesses mit dem Namen `MyApplication/EncryptDocument` unter Verwendung von DIME.

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um den Codebeispielen zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` mithilfe von Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

>[!NOTE]
>
>Der Aufruf von AEM Forms-Dienstvorgängen mit DIME wird nicht mehr unterstützt. Es wird empfohlen, MTOM zu verwenden. (Siehe [AEM Forms mit MTOM](#invoking-aem-forms-using-mtom) aufrufen.)

### Erstellen eines .NET-Projekts, das DIME {#creating-a-net-project-that-uses-dime} verwendet

Führen Sie die folgenden Aufgaben aus, um ein .NET-Projekt zu erstellen, das einen Forms-Dienst mit DIME aufrufen kann:

* Installieren Sie Web Services Enhancements 2.0 auf Ihrem Entwicklungscomputer.
* Erstellen Sie in Ihrem .NET-Projekt eine Webreferenz zum FormsAEM Forms-Dienst.

**Web-Services-Verbesserungen 2.0 installieren**

Installieren Sie Web Services Enhancements 2.0 auf Ihrem Entwicklungscomputer und integrieren Sie es in Microsoft Visual Studio .NET. Sie können die Web Services-Verbesserungen 2.0 vom [Microsoft Download Center herunterladen.](https://www.microsoft.com/downloads/search.aspx)

Suchen Sie auf dieser Webseite nach Web Services Enhancements 2.0 und laden Sie es auf Ihren Entwicklungscomputer herunter. Durch diesen Download wird eine Datei mit dem Namen Microsoft WSE 2.0 SPI.msi auf Ihrem Computer platziert. Führen Sie das Installationsprogramm aus und folgen Sie den Online-Anweisungen.

>[!NOTE]
>
>Web Services Enhancements 2.0 unterstützt DIME. Die unterstützte Version von Microsoft Visual Studio ist 2003 bei der Arbeit mit Web Services Enhancements 2.0. Web Services Enhancements 3.0 unterstützt DIME nicht. unterstützt jedoch MTOM.

**Webverweis auf einen AEM Forms-Dienst erstellen**

Nachdem Sie Web Services Enhancements 2.0 auf Ihrem Entwicklungscomputer installiert und ein Microsoft .NET-Projekt erstellt haben, erstellen Sie eine Webreferenz zum Forms-Dienst. Um beispielsweise einen Webverweis auf den `MyApplication/EncryptDocument`-Prozess zu erstellen und vorausgesetzt, Forms ist auf dem lokalen Computer installiert, geben Sie die folgende URL an:

```java
     http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL
```

Nachdem Sie eine Webreferenz erstellt haben, stehen Ihnen die beiden folgenden Proxy-Datentypen zur Verfügung, die Sie in Ihrem .NET-Projekt verwenden können: `EncryptDocumentService` und `EncryptDocumentServiceWse`. Um den Prozess `MyApplication/EncryptDocument` mit DIME aufzurufen, verwenden Sie den Typ `EncryptDocumentServiceWse` .

>[!NOTE]
>
>Bevor Sie einen Webverweis für den Forms-Dienst erstellen, vergewissern Sie sich, dass Sie in Ihrem Projekt auf Web Services Enhancements 2.0 verweisen. (Siehe &quot;Web Services-Verbesserungen installieren 2.0&quot;.)

**Referenzieren der WSE-Bibliothek**

1. Wählen Sie im Menü Projekt die Option Verweis hinzufügen aus.
1. Wählen Sie im Dialogfeld Verweis hinzufügen die Option Microsoft.Web.Services2.dll aus.
1. Wählen Sie System.Web.Services.dll aus.
1. Klicken Sie auf Auswählen und dann auf OK.

**Webverweis auf einen Forms-Dienst erstellen**

1. Wählen Sie im Menü Projekt die Option Webverweis hinzufügen aus.
1. Geben Sie im Dialogfeld &quot;URL&quot;die URL zum Forms-Dienst an.
1. Klicken Sie auf Los und dann auf Verweis hinzufügen .

>[!NOTE]
>
>Stellen Sie sicher, dass Sie für Ihr .NET-Projekt die WSE-Bibliothek aktivieren. Klicken Sie im Projekt-Explorer mit der rechten Maustaste auf den Projektnamen und wählen Sie WSE 2.0 aktivieren. Stellen Sie sicher, dass das Kontrollkästchen im angezeigten Dialogfeld aktiviert ist.

**Aufrufen eines Dienstes mit DIME in einem .NET-Projekt**

Sie können einen Forms-Dienst mit DIME aufrufen. Betrachten Sie den `MyApplication/EncryptDocument`-Prozess, der ein ungesichertes PDF-Dokument akzeptiert und ein kennwortverschlüsseltes PDF-Dokument zurückgibt. Um den `MyApplication/EncryptDocument`-Prozess mit DIME aufzurufen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie ein Microsoft .NET-Projekt, mit dem Sie einen Forms-Dienst mit DIME aufrufen können. Stellen Sie sicher, dass Sie die Web-Services-Verbesserungen 2.0 einbeziehen und eine Webreferenz zum AEM Forms-Dienst erstellen.
1. Nachdem Sie einen Webverweis auf den `MyApplication/EncryptDocument`-Prozess gesetzt haben, erstellen Sie ein `EncryptDocumentServiceWse` -Objekt mithilfe des Standardkonstruktors.
1. Legen Sie das `EncryptDocumentServiceWse`-Datenelement des `Credentials`-Objekts mit einem `System.Net.NetworkCredential`-Wert fest, der den AEM für den Benutzernamen und das Kennwort angibt.
1. Erstellen Sie ein `Microsoft.Web.Services2.Dime.DimeAttachment` -Objekt, indem Sie dessen Konstruktor verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der einen GUID-Wert angibt. Sie können einen GUID-Wert abrufen, indem Sie die `System.Guid.NewGuid.ToString`-Methode aufrufen.
   * Ein string -Wert, der den Inhaltstyp angibt. Da dieser Prozess ein PDF-Dokument erfordert, geben Sie `application/pdf` an.
   * Ein Auflistungswert `TypeFormat` . Geben Sie `TypeFormat.MediaType`.
   * Ein string -Wert, der den Speicherort des PDF-Dokuments angibt, das an den AEM Forms-Prozess übergeben werden soll.

1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
1. Fügen Sie die DIME-Anlage zum `BLOB`-Objekt hinzu, indem Sie den `Id`-Datenelementwert des Objekts `Microsoft.Web.Services2.Dime.DimeAttachment` dem `BLOB`-Datenelement des Objekts `attachmentID` zuweisen.
1. Rufen Sie die `EncryptDocumentServiceWse.RequestSoapContext.Attachments.Add`-Methode auf und übergeben Sie das `Microsoft.Web.Services2.Dime.DimeAttachment`-Objekt.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die `EncryptDocumentServiceWse` -Methode des Objekts `invoke` aufrufen und das `BLOB` -Objekt übergeben, das die DIME-Anlage enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB` -Objekts zurück.
1. Rufen Sie den Wert der Anlagenkennung ab, indem Sie den Wert des `attachmentID` -Datenelements des zurückgegebenen `BLOB`-Objekts abrufen.
1. Iterieren Sie durch die Anlagen in `EncryptDocumentServiceWse.ResponseSoapContext.Attachments` und verwenden Sie den Wert für die Anlagenkennung, um das verschlüsselte PDF-Dokument abzurufen.
1. Rufen Sie ein `System.IO.Stream` -Objekt ab, indem Sie den Wert des `Stream` -Datenelements des `Attachment` -Objekts abrufen.
1. Erstellen Sie ein Byte-Array und übergeben Sie dieses Byte-Array an die `System.IO.Stream` -Methode des Objekts `Read`. Diese Methode füllt das Byte-Array mit einem Datenstrom, der das verschlüsselte PDF-Dokument darstellt.
1. Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen PDF-Dateispeicherort darstellt. Dieses Objekt stellt das verschlüsselte PDF-Dokument dar.
1. Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
1. Schreiben Sie den Inhalt des Byte-Arrays in die PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

### Erstellen von Java-Proxyklassen für Apache Axis, die DIME {#creating-apache-axis-java-proxy-classes-that-use-dime} verwenden

Sie können das Apache Axis WSDL2Java-Tool verwenden, um eine Dienst-WSDL in Java-Proxyklassen zu konvertieren, damit Sie Dienstvorgänge aufrufen können. Mithilfe von Apache Ant können Sie Bibliotheksdateien für Axis aus einer AEM Forms-Dienst-WSDL generieren, mit der Sie den Dienst aufrufen können. (Siehe [Erstellen von Java-Proxy-Klassen mit Apache Axis](#creating-java-proxy-classes-using-apache-axis).)

Das Apache Axis WSDL2Java-Tool generiert JAVA-Dateien, die Methoden enthalten, die zum Senden von SOAP-Anforderungen an einen Dienst verwendet werden. SOAP-Anforderungen, die von einem Dienst empfangen werden, werden von den von der Achse generierten Bibliotheken dekodiert und in die Methoden und Argumente zurückumgewandelt.

So rufen Sie den Dienst `MyApplication/EncryptDocument` (der in Workbench erstellt wurde) mit Axis-generierten Bibliotheksdateien und DIME auf:

1. Erstellen Sie Java-Proxyklassen, die die WSDL-Dienst-WSDL mit Apache Axis verwenden. `MyApplication/EncryptDocument` (Siehe [Erstellen von Java-Proxy-Klassen mit Apache Axis](#creating-java-proxy-classes-using-apache-axis).)
1. Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.
1. Erstellen Sie ein Objekt `MyApplicationEncryptDocumentServiceLocator`, indem Sie den Konstruktor verwenden.
1. Erstellen Sie ein `URL` -Objekt, indem Sie dessen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der die WSDL-Definition des AEM Forms-Dienstes angibt. Stellen Sie sicher, dass Sie `?blob=dime` am Ende der SOAP-Endpunkt-URL angeben. Beispiele

   ```java
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=dime.
   ```

1. Erstellen Sie ein `EncryptDocumentSoapBindingStub` -Objekt, indem Sie seinen Konstruktor aufrufen und das `MyApplicationEncryptDocumentServiceLocator`Objekt und das `URL` -Objekt übergeben.
1. Legen Sie den Wert für den Benutzernamen und das Kennwort für AEM Formulare fest, indem Sie die Methoden `setUsername` und `setPassword` des Objekts `EncryptDocumentSoapBindingStub` aufrufen.

   ```java
    encryptionClientStub.setUsername("administrator");
    encryptionClientStub.setPassword("password");
   ```

1. Rufen Sie das PDF-Dokument ab, das an den Dienst `MyApplication/EncryptDocument` gesendet werden soll, indem Sie ein `java.io.File` -Objekt erstellen. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
1. Erstellen Sie ein `javax.activation.DataHandler` -Objekt, indem Sie dessen Konstruktor verwenden und ein `javax.activation.FileDataSource` -Objekt übergeben. Das `javax.activation.FileDataSource`-Objekt kann mithilfe seines Konstruktors erstellt werden und das `java.io.File`-Objekt übergeben, das das PDF-Dokument darstellt.
1. Erstellen Sie ein `org.apache.axis.attachments.AttachmentPart` -Objekt, indem Sie dessen Konstruktor verwenden und das `javax.activation.DataHandler` -Objekt übergeben.
1. Hängen Sie die Anlage an, indem Sie die `addAttachment`-Methode des `EncryptDocumentSoapBindingStub`-Objekts aufrufen und das `org.apache.axis.attachments.AttachmentPart`-Objekt übergeben.
1. Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Füllen Sie das `BLOB`-Objekt mit dem Wert für die Anlagenkennung, indem Sie die `setAttachmentID`-Methode des Objekts `BLOB` aufrufen und den Wert für die Anlagenkennung übergeben. Dieser Wert kann durch Aufrufen der `getContentId` -Methode des Objekts `org.apache.axis.attachments.AttachmentPart` abgerufen werden.
1. Rufen Sie den Prozess `MyApplication/EncryptDocument` auf, indem Sie die `invoke` -Methode des Objekts `EncryptDocumentSoapBindingStub` aufrufen. Übergeben Sie das `BLOB`-Objekt, das die DIME-Anlage enthält. Dieser Prozess gibt ein verschlüsseltes PDF-Dokument innerhalb eines `BLOB` -Objekts zurück.
1. Rufen Sie den Wert der Anlagenkennung ab, indem Sie die `getAttachmentID` -Methode des zurückgegebenen `BLOB`-Objekts aufrufen. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Kennungswert des zurückgegebenen Anhangs darstellt.
1. Rufen Sie die Anlagen ab, indem Sie die `getAttachments` -Methode des Objekts `EncryptDocumentSoapBindingStub` aufrufen. Diese Methode gibt ein Array von `Objects` zurück, das die Anlagen darstellt.
1. Iterieren Sie durch die Anlagen (Array `Object`) und verwenden Sie den Wert für die Anlagenkennung, um das verschlüsselte PDF-Dokument abzurufen. Jedes Element ist ein `org.apache.axis.attachments.AttachmentPart` -Objekt.
1. Rufen Sie das mit der Anlage verknüpfte `javax.activation.DataHandler`-Objekt ab, indem Sie die `getDataHandler`-Methode des Objekts `org.apache.axis.attachments.AttachmentPart` aufrufen.
1. Rufen Sie ein `java.io.FileStream` -Objekt ab, indem Sie die `getInputStream` -Methode des Objekts `javax.activation.DataHandler` aufrufen.
1. Erstellen Sie ein Byte-Array und übergeben Sie dieses Byte-Array an die `java.io.FileStream` -Methode des Objekts `read`. Diese Methode füllt das Byte-Array mit einem Datenstrom, der das verschlüsselte PDF-Dokument darstellt.
1. Erstellen Sie ein Objekt `java.io.File`, indem Sie den Konstruktor verwenden. Dieses Objekt stellt das verschlüsselte PDF-Dokument dar.
1. Erstellen Sie ein `java.io.FileOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.File`-Objekt übergeben.
1. Rufen Sie die `write` -Methode des Objekts auf und übergeben Sie das Byte-Array, das den Datenstrom enthält, der das verschlüsselte PDF-Dokument darstellt.`java.io.FileOutputStream`

**Siehe auch**

[Schnellstart: Aufrufen eines Dienstes mit DIME in einem Java-Projekt](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-dime-in-a-java-project)

## Verwenden der SAML-basierten Authentifizierung {#using-saml-based-authentication}

AEM Forms unterstützt beim Aufrufen von Diensten verschiedene Webdienst-Authentifizierungsmodi. Ein Authentifizierungsmodus gibt sowohl einen Benutzernamen als auch einen Kennwortwert mithilfe eines einfachen Autorisierungsheaders im Webdienstaufruf an. AEM Forms unterstützt auch die SAML-Assertionsbasierte Authentifizierung. Wenn eine Clientanwendung einen AEM Forms-Dienst mithilfe eines Webdiensts aufruft, kann die Clientanwendung Authentifizierungsinformationen auf eine der folgenden Arten bereitstellen:

* Übergeben von Anmeldeinformationen als Teil der grundlegenden Autorisierung
* Übergeben des Benutzername-Tokens als Teil der WS-Security-Kopfzeile
* Übergeben einer SAML-Assertion als Teil der WS-Security-Kopfzeile
* Weitergeben des Kerberos-Tokens als Teil der WS-Security-Kopfzeile

AEM Forms unterstützt keine standardmäßige zertifikatbasierte Authentifizierung, unterstützt jedoch die zertifikatbasierte Authentifizierung in einer anderen Form.

>[!NOTE]
>
>Der Webdienst-Schnellstart beginnt in Programmieren mit AEM Forms und geben Sie die Werte für Benutzername und Kennwort an, um die Autorisierung durchzuführen.

Die Identität AEM Formularbenutzer kann durch eine SAML-Zusicherung dargestellt werden, die mithilfe eines geheimen Schlüssels signiert wurde. Der folgende XML-Code zeigt ein Beispiel für eine SAML-Assertion.

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

Diese Beispielassertion wird für einen Administrator ausgestellt. Diese Zusicherung enthält die folgenden merklichen Elemente:

* Sie gilt für eine bestimmte Dauer.
* Sie wird für einen bestimmten Benutzer ausgestellt.
* Es ist digital signiert. Jede daran vorgenommene Änderung würde also die Signatur beschädigen.
* Sie kann AEM Forms als Token der Benutzeridentität ähnlich dem Benutzernamen und Kennwort angezeigt werden.

Eine Clientanwendung kann die Zusicherung von jeder AEM Forms AuthenticationManager-API abrufen, die ein `AuthResult` -Objekt zurückgibt. Sie können eine `AuthResult`-Instanz abrufen, indem Sie eine der beiden folgenden Methoden ausführen:

* Authentifizieren des Benutzers mit einer der Authentifizierungsmethoden, die von der AuthenticationManager-API verfügbar gemacht werden. Normalerweise würden der Benutzername und das Kennwort verwendet. Sie können jedoch auch die Zertifikatauthentifizierung verwenden.
* Verwendung der `AuthenticationManager.getAuthResultOnBehalfOfUser`-Methode. Mit dieser Methode kann eine Clientanwendung ein `AuthResult` -Objekt für AEM Formularbenutzer abrufen.

Ein AEM Formularbenutzer kann mithilfe eines SAML-Tokens authentifiziert werden, das abgerufen wird. Diese SAML-Assertion (XML-Fragment) kann als Teil der WS-Security-Kopfzeile mit dem Webdienst-Aufruf zur Benutzerauthentifizierung gesendet werden. In der Regel hat eine Clientanwendung einen Benutzer authentifiziert, die Benutzeranmeldeinformationen jedoch nicht gespeichert. (Oder der Benutzer hat sich über einen anderen Mechanismus als die Verwendung eines Benutzernamens und Kennworts bei diesem Client angemeldet.) In diesem Fall muss die Client-Anwendung AEM Forms aufrufen und die Identität eines bestimmten Benutzers annehmen, der AEM Forms aufrufen darf.

Rufen Sie die `AuthenticationManager.getAuthResultOnBehalfOfUser`-Methode mithilfe eines Webdiensts auf, um sich als ein bestimmter Benutzer zu präsentieren. Diese Methode gibt eine `AuthResult`-Instanz zurück, die die SAML-Assertion für diesen Benutzer enthält.

Verwenden Sie anschließend diese SAML-Assertion, um alle Dienste aufzurufen, für die eine Authentifizierung erforderlich ist. Diese Aktion umfasst das Senden der Zusicherung als Teil der SOAP-Kopfzeile. Wenn mit dieser Assertion ein Webdienst-Aufruf erfolgt, identifiziert AEM Forms den Benutzer als den Benutzer, der durch diese Assertion dargestellt wird. Das heißt, der in der Assertion angegebene Benutzer ist der Benutzer, der den Dienst aufruft.

### Verwenden von Apache Axis-Klassen und SAML-basierter Authentifizierung {#using-apache-axis-classes-and-saml-based-authentication}

Sie können einen AEM Forms-Dienst über Java-Proxyklassen aufrufen, die mit der Axis-Bibliothek erstellt wurden. (Siehe [Erstellen von Java-Proxy-Klassen mit Apache Axis](#creating-java-proxy-classes-using-apache-axis).)

Wenn Sie AXIS verwenden, das SAML-basierte Authentifizierung verwendet, registrieren Sie den Anfrage- und Antwort-Handler bei Axis. Apache Axis ruft den Handler auf, bevor eine Aufrufanforderung an AEM Forms gesendet wird. Um einen Handler zu registrieren, erstellen Sie eine Java-Klasse, die `org.apache.axis.handlers.BasicHandler` erweitert.

**Erstellen eines AssertionHandlers mit Achse**

Die folgende Java-Klasse mit dem Namen `AssertionHandler.java` zeigt ein Beispiel für eine Java-Klasse, die `org.apache.axis.handlers.BasicHandler` erweitert.

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

**Handler registrieren**

Um einen Handler bei Axis zu registrieren, erstellen Sie eine Datei client-config.wsdd . Standardmäßig sucht Axis nach einer Datei mit diesem Namen. Der folgende XML-Code ist ein Beispiel für eine Datei client-config.wsdd. Weitere Informationen finden Sie in der Dokumentation zu Achsen .

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

**Aufrufen eines AEM Forms-Dienstes**

Im folgenden Codebeispiel wird ein AEM Forms-Dienst mit SAML-basierter Authentifizierung aufgerufen.

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

### Verwenden einer .NET-Client-Assembly und SAML-basierten Authentifizierung {#using-a-net-client-assembly-and-saml-based-authentication}

Sie können einen Forms-Dienst mithilfe einer .NET-Client-Assembly und einer SAML-basierten Authentifizierung aufrufen. Dazu müssen Sie die Webdienstverbesserungen 3.0 (WSE) verwenden. Informationen zum Erstellen einer .NET-Client-Assembly, die WSE verwendet, finden Sie unter [Erstellen eines .NET-Projekts, das DIME](#creating-a-net-project-that-uses-dime) verwendet.

>[!NOTE]
>
>Im Abschnitt DIME wird WSE 2.0 verwendet. Um SAML-basierte Authentifizierung zu verwenden, folgen Sie den Anweisungen, die im Abschnitt DIME angegeben sind. Ersetzen Sie jedoch WSE 2.0 durch WSE 3.0. Installieren Sie Web Services Enhancements 3.0 auf Ihrem Entwicklungscomputer und integrieren Sie es in Microsoft Visual Studio .NET. Sie können Web Services Enhancements 3.0 vom [Microsoft Download Center](https://www.microsoft.com/downloads/search.aspx) herunterladen.

Die WSE-Architektur verwendet die Datentypen Richtlinien, Zuordnungen und SecurityToken . Geben Sie kurz für einen Webdienstaufruf eine Richtlinie an. Eine Richtlinie kann über mehrere Assertionen verfügen. Jede Assertion kann Filter enthalten. Ein Filter wird in bestimmten Phasen eines Webdienstaufrufs aufgerufen und kann zu diesem Zeitpunkt die SOAP-Anforderung ändern. Ausführliche Informationen finden Sie in der Dokumentation zu Web Service-Verbesserungen 3.0 .

**Erstellen der Zusicherung und des Filters**

Im folgenden C#-Codebeispiel werden Filter- und Assertionsklassen erstellt. In diesem Codebeispiel wird ein SamlAssertionOutputFilter erstellt. Dieser Filter wird vom WSE-Framework aufgerufen, bevor die SOAP-Anforderung an AEM Forms gesendet wird.

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

**Aufrufen eines AEM Forms-Dienstes**

Im folgenden C#-Codebeispiel wird ein Forms-Dienst mithilfe der SAML-basierten Authentifizierung aufgerufen.

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

## Überlegungen zur Verwendung von Webdiensten {#related-considerations-when-using-web-services}

Manchmal treten Probleme beim Aufrufen bestimmter AEM Forms-Dienstvorgänge über Webdienste auf. Ziel dieser Diskussion ist es, diese Fragen zu ermitteln und eine Lösung zu finden, sofern eine Lösung verfügbar ist.

### Asynchrones Aufrufen von Dienstvorgängen {#invoking-service-operations-asynchronously}

Wenn Sie versuchen, einen AEM Forms-Dienstvorgang asynchron aufzurufen, z. B. den Vorgang `htmlToPDF` von Generate PDF , tritt ein `SoapFaultException` auf. Um dieses Problem zu beheben, erstellen Sie eine XML-Datei mit benutzerdefinierter Bindung, die das Element `ExportPDF_Result` und andere Elemente in verschiedene Klassen zuordnet. Die folgende XML-Datei stellt eine benutzerdefinierte Bindungsdatei dar.

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

Verwenden Sie diese XML-Datei beim Erstellen von Java-Proxy-Dateien mithilfe von JAX-WS. (Siehe [Erstellen von Java-Proxy-Klassen mit JAX-WS](#creating-java-proxy-classes-using-jax-ws).)

Referenzieren Sie diese XML-Datei beim Ausführen des JAX-WS-Tools (wsimport.exe) mithilfe der Befehlszeilenoption - `b` . Aktualisieren Sie das Element `wsdlLocation` in der Bindungs-XML-Datei, um die URL von AEM Forms anzugeben.

Um sicherzustellen, dass der asynchrone Aufruf funktioniert, ändern Sie den Endpunkt-URL-Wert und geben Sie `async=true` an. Geben Sie beispielsweise für Java-Proxy-Dateien, die mit JAX-WS erstellt werden, Folgendes für `BindingProvider.ENDPOINT_ADDRESS_PROPERTY` an.

`https://server:port/soap/services/ServiceName?wsdl&async=true&lc_version=9.0.0`

Die folgende Liste gibt andere Dienste an, die eine benutzerdefinierte Bindungsdatei benötigen, wenn sie asynchron aufgerufen werden:

* PDFG 3D
* Task Manager
* Anwendungs-Manager
* Directory Manager
* Distiller
* Rights Management
* Document Management

### Unterschiede bei J2EE-Anwendungsservern {#differences-in-j2ee-application-servers}

Manchmal ruft eine Proxy-Bibliothek, die mit einem bestimmten J2EE-Anwendungsserver erstellt wurde, nicht erfolgreich AEM Forms auf, das auf einem anderen J2EE-Anwendungsserver gehostet wird. Stellen Sie sich eine Proxy-Bibliothek vor, die mit AEM Forms generiert wird, das auf WebSphere bereitgestellt wird. Diese Proxy-Bibliothek kann AEM Forms-Dienste, die auf dem JBoss Application Server bereitgestellt werden, nicht erfolgreich aufrufen.

Einige komplexe AEM Forms-Datentypen, wie z. B. `PrincipalReference`, werden bei der Bereitstellung von AEM Forms auf WebSphere anders definiert als der JBoss Application Server. Unterschiede in den JDKs, die von den verschiedenen J2EE-Anwendungsdiensten verwendet werden, sind der Grund, warum es Unterschiede in WSDL-Definitionen gibt. Verwenden Sie daher Proxy-Bibliotheken, die vom selben J2EE-Anwendungsserver generiert werden.

### Zugreifen auf mehrere Dienste mithilfe von Webdiensten {#accessing-multiple-services-using-web-services}

Aufgrund von Namespace-Konflikten können Datenobjekte nicht für mehrere Service-WSDLs freigegeben werden. Verschiedene Dienste können Datentypen gemeinsam nutzen. Daher teilen sich die Dienste die Definition dieser Typen in den WSDLs. Sie können beispielsweise nicht zwei .NET-Clientassemblys, die einen `BLOB`-Datentyp enthalten, demselben .NET-Clientprojekt hinzufügen. Wenn Sie dies versuchen, tritt ein Kompilierungsfehler auf.

In der folgenden Liste sind Datentypen aufgeführt, die nicht von mehreren Service-WSDLs gemeinsam genutzt werden können:

* `User`
* `Principals`
* `PrincipalReference`
* `Groups`
* `Roles`
* `BLOB`

Um dieses Problem zu vermeiden, wird empfohlen, die Datentypen vollständig zu qualifizieren. Angenommen, eine .NET-Anwendung, die sowohl auf den Forms-Dienst als auch auf den Signature-Dienst verweist, verwendet eine Dienstreferenz. Beide Dienstverweise enthalten eine `BLOB` -Klasse. Um eine `BLOB`-Instanz zu verwenden, qualifizieren Sie das `BLOB`-Objekt vollständig, wenn Sie es deklarieren. Dieser Ansatz wird im folgenden Codebeispiel veranschaulicht. Weitere Informationen zu diesem Codebeispiel finden Sie unter [Digital Signing Interactive Forms](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-interactive-forms).

Das folgende C#-Codebeispiel signiert ein interaktives Formular, das vom Forms-Dienst wiedergegeben wird. Die Clientanwendung verfügt über zwei Dienstreferenzen. Die `BLOB`-Instanz, die mit dem Forms-Dienst verknüpft ist, gehört zum Namespace `SignInteractiveForm.ServiceReference2` . Ebenso gehört die `BLOB`-Instanz, die mit dem Signature-Dienst verknüpft ist, zum Namespace `SignInteractiveForm.ServiceReference1` . Das signierte interaktive Formular wird als PDF-Datei mit dem Namen *LoanXFASigned.pdf* gespeichert.

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
                    //it is necessary to fully-qualify the BLOB objects
 
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
 
                    //Specify a XML form data
                    string path = "C:\\Adobe\Loan.xml";
                    FileStream fs = new FileStream(path, FileMode.Open);
 
                    //Get the length of the file stream
                    int len = (int)fs.Length;
                    byte[] ByteArray = new byte[len];
 
                    fs.Read(ByteArray, 0, len);
                    formData.MTOM = ByteArray;
 
                    //Specify a XML form data
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

### Dienste, die mit dem Brief beginnen Ich produziere ungültige Proxy-Dateien {#services-starting-with-the-letter-i-produce-invalid-proxy-files}

Der Name einiger von AEM Forms generierter Proxyklassen ist bei Verwendung von Microsoft .Net 3.5 und WCF falsch. Dieses Problem tritt auf, wenn für den IBMFilenetContentRepositoryConnector, IDPSchedulerService oder einen anderen Dienst Proxyklassen erstellt werden, deren Name mit dem Buchstaben I beginnt. Beispielsweise lautet der Name des generierten Clients im Fall von IBMFileNetContentRepositoryConnector `BMFileNetContentRepositoryConnectorClient`. Der Brief, den ich habe, fehlt in der generierten Proxy-Klasse.
