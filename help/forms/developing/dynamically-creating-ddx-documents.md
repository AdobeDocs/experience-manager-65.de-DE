---
title: DDX-Dokumente dynamisch erstellen
seo-title: DDX-Dokumente dynamisch erstellen
description: Erstellen Sie ein DDX-Dokument dynamisch mit der Java-API und der Web Service-API. Durch das dynamische Erstellen eines DDX-Dokuments können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden.
seo-description: Erstellen Sie ein DDX-Dokument dynamisch mit der Java-API und der Web Service-API. Durch das dynamische Erstellen eines DDX-Dokuments können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden.
uuid: b73e8069-6c9f-4517-a0ae-f3d503191d2d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 2ad227de-68a8-446f-8c4f-a33a6f95bec8
role: Developer
exl-id: b3c19c82-e26f-4dc8-b846-6aec705cee08
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2199'
ht-degree: 4%

---

# DDX-Dokumente dynamisch erstellen {#dynamically-creating-ddx-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Sie können ein DDX-Dokument dynamisch erstellen, das zum Ausführen eines Assembler-Vorgangs verwendet werden kann. Durch das dynamische Erstellen eines DDX-Dokuments können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden. Verwenden Sie zum dynamischen Erstellen eines DDX-Dokuments Klassen, die zur verwendeten Programmiersprache gehören. Wenn Sie beispielsweise Ihre Clientanwendung mit Java entwickeln, verwenden Sie Klassen, die zum `org.w3c.dom.*`Paket gehören. Wenn Sie Microsoft .NET verwenden, verwenden Sie ebenfalls Klassen, die zum Namespace `System.Xml` gehören.

Bevor Sie das DDX-Dokument an den Assembler-Dienst übergeben können, konvertieren Sie das XML von einer `org.w3c.dom.Document`-Instanz in eine `com.adobe.idp.Document`-Instanz. Wenn Sie Webdienste verwenden, konvertieren Sie die XML vom Datentyp, der zum Erstellen der XML verwendet wird (z. B. `XmlDocument`), in eine `BLOB`-Instanz.

Angenommen, das folgende DDX-Dokument wird dynamisch erstellt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDFsFromBookmarks prefix="stmt">
     <PDF source="AssemblerResultPDF.pdf"/>
 </PDFsFromBookmarks>
 </DDX>
```

Dieses DDX-Dokument zerlegt ein PDF-Dokument. Es wird empfohlen, sich mit dem Zerlegen von PDF-Dokumenten vertraut zu machen.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein PDF-Dokument mithilfe eines dynamisch erstellten DDX-Dokuments aufzuteilen:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Erstellen Sie das DDX-Dokument.
1. Konvertieren Sie das DDX-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Aufteilen des PDF-Dokuments.
1. Speichern Sie die zerlegten PDF-Dokumente.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, erstellen Sie einen Assembler-Dienst-Client.

**DDX-Dokument erstellen**

Erstellen Sie ein DDX-Dokument mit der verwendeten Programmiersprache. Um ein DDX-Dokument zu erstellen, das ein PDF-Dokument aufteilt, stellen Sie sicher, dass es das Element `PDFsFromBookmarks` enthält. Konvertieren Sie den zum Erstellen des DDX-Dokuments verwendeten Datentyp in eine `com.adobe.idp.Document`-Instanz, wenn Sie die Java-API verwenden. Wenn Sie Webdienste verwenden, konvertieren Sie den Datentyp in eine `BLOB`-Instanz.

**Konvertieren des DDX-Dokuments**

Ein DDX-Dokument, das mithilfe von `org.w3c.dom`-Klassen erstellt wird, muss in ein `com.adobe.idp.Document`-Objekt konvertiert werden. Verwenden Sie Java XML Transformation-Klassen, um diese Aufgabe bei Verwendung der Java-API auszuführen. Wenn Sie Webdienste verwenden, konvertieren Sie das DDX-Dokument in ein `BLOB`-Objekt.

**Referenzieren eines zu zerlegenden PDF-Dokuments**

Referenzieren Sie zum Aufteilen eines PDF-Dokuments eine PDF-Datei, die das zu zerlegende PDF-Dokument darstellt. Wenn an den Assembler-Dienst übergeben wird, wird für jedes Lesezeichen der Stufe 1 im Dokument ein separates PDF-Dokument zurückgegeben.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Zum Festlegen von Laufzeitoptionen verwenden Sie ein `AssemblerOptionSpec` -Objekt.

**Aufteilen des PDF-Dokuments**

Lösen Sie das PDF-Dokument aus, indem Sie den Vorgang `invokeDDX` aufrufen. Übergeben Sie das dynamisch erstellte DDX-Dokument. Der Assembler-Dienst gibt ausgeblendete PDF-Dokumente innerhalb eines Sammlungsobjekts zurück.

**Speichern Sie die zerlegten PDF-Dokumente**

Alle zerlegten PDF-Dokumente werden innerhalb eines Sammlungsobjekts zurückgegeben. Durchsuchen Sie das Sammlungsobjekt und speichern Sie jedes PDF-Dokument als PDF-Datei.

**Siehe auch**

[DDX-Dokument mithilfe der Java-API dynamisch erstellen](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-java-api)

[DDX-Dokument mithilfe der Webdienst-API dynamisch erstellen](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuerte Demontage von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## DDX-Dokument dynamisch mit der Java-API {#dynamically-create-a-ddx-document-using-the-java-api} erstellen

Dynamisches Erstellen eines DDX-Dokuments und Aufteilen eines PDF-Dokuments mithilfe der Assembler Service-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Erstellen Sie das DDX-Dokument.

   * Erstellen Sie ein Java `DocumentBuilderFactory` -Objekt, indem Sie die `DocumentBuilderFactory` -Klasse aufrufen.&quot;`newInstance`-Methode.
   * Erstellen Sie ein Java `DocumentBuilder` -Objekt, indem Sie die `newDocumentBuilder` -Methode des Objekts `DocumentBuilderFactory` aufrufen.
   * Rufen Sie die `newDocument`-Methode des `DocumentBuilder`-Objekts auf, um ein `org.w3c.dom.Document`-Objekt zu instanziieren.
   * Erstellen Sie das Stammelement des DDX-Dokuments, indem Sie die `createElement` -Methode des Objekts `org.w3c.dom.Document` aufrufen. Diese Methode erstellt ein `Element` -Objekt, das das Stammelement darstellt. Übergeben Sie einen string -Wert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `setAttribute`-Methode aufrufen. Hängen Sie abschließend das Element an das Kopfzeilenelement an, indem Sie die `appendChild` -Methode des Kopfzeilenelements aufrufen und das untergeordnete Elementobjekt als Argument übergeben. Die folgenden Codezeilen zeigen diese Anwendungslogik:
      ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Erstellen Sie das Element `PDFsFromBookmarks`, indem Sie die `createElement` -Methode des Objekts `Document` aufrufen. Übergeben Sie einen string -Wert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie einen Wert für das Element `PDFsFromBookmarks` fest, indem Sie dessen Methode `setAttribute` aufrufen. Hängen Sie das Element `PDFsFromBookmarks` an das Element `DDX` an, indem Sie die Methode `appendChild` des DDX-Elements aufrufen. Übergeben Sie das Elementobjekt `PDFsFromBookmarks` als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Erstellen Sie ein `PDF` -Element, indem Sie die `createElement` -Methode des Objekts `Document` aufrufen. Übergeben Sie einen string -Wert, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie einen Wert für das Element `PDF` fest, indem Sie dessen Methode `setAttribute` aufrufen. Hängen Sie das Element `PDF` an das Element `PDFsFromBookmarks` an, indem Sie die Methode `PDFsFromBookmarks` des Elements `appendChild` aufrufen. Übergeben Sie das Elementobjekt `PDF` als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Konvertieren Sie das DDX-Dokument.

   * Erstellen Sie ein `javax.xml.transform.Transformer` -Objekt, indem Sie die statische `newInstance` -Methode des `javax.xml.transform.Transformer` -Objekts aufrufen.
   * Erstellen Sie ein `Transformer` -Objekt, indem Sie die `newTransformer` -Methode des Objekts `TransformerFactory` aufrufen.
   * Erstellen Sie ein Objekt `ByteArrayOutputStream`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein Objekt `javax.xml.transform.dom.DOMSource`, indem Sie den Konstruktor verwenden. Übergeben Sie das `org.w3c.dom.Document`-Objekt, das das DDX-Dokument darstellt.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource`-Objekt, indem Sie seinen Konstruktor verwenden und das `ByteArrayOutputStream`-Objekt übergeben.
   * Füllen Sie das Java `ByteArrayOutputStream`-Objekt, indem Sie die `transform` -Methode des Objekts `javax.xml.transform.Transformer` aufrufen. Übergeben Sie die Objekte `javax.xml.transform.dom.DOMSource` und `javax.xml.transform.stream.StreamResult`.
   * Erstellen Sie ein Byte-Array und weisen Sie die Größe des `ByteArrayOutputStream`-Objekts dem Byte-Array zu.
   * Füllen Sie das Byte-Array, indem Sie die `toByteArray` -Methode des Objekts `ByteArrayOutputStream` aufrufen.
   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie dessen Konstruktor verwenden und das Byte-Array übergeben.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von PDF-Eingabedokumenten mit einem `HashMap`-Konstruktor verwendet wird.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des PDF-Dokuments an die Aufspaltung übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält, das zerlegt werden soll.
   * Fügen Sie einen Eintrag zum `java.util.Map`-Objekt hinzu, indem Sie dessen `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Im dynamisch erstellten DDX-Dokument ist der Wert `AssemblerResultPDF.pdf`.)
      * Ein `com.adobe.idp.Document` -Objekt, das das zu zerlegende PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `setFailOnError` -Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Aufteilen des PDF-Dokuments.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das dynamisch erstellte DDX-Dokument darstellt
   * Ein `java.util.Map` -Objekt, das das zu zerlegende PDF-Dokument enthält
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschriftart und der Auftragsprotokollebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die zerlegten PDF-Dokumente und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die disassemblierten PDF-Dokumente abzurufen:

   * Rufen Sie die `getDocuments` -Methode des Objekts `AssemblerResult` auf. Diese Methode gibt ein `java.util.Map` -Objekt zurück.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): DDX-Dokument mithilfe der Java-API dynamisch erstellen](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-dynamically-creating-a-ddx-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Dynamisches Erstellen eines DDX-Dokuments mithilfe der Webdienst-API {#dynamically-create-a-ddx-document-using-the-web-service-api}

Dynamisches Erstellen eines DDX-Dokuments und Aufteilen eines PDF-Dokuments mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Erstellen Sie das DDX-Dokument.

   * Erstellen Sie ein Objekt `System.Xml.XmlElement`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie das Stammelement des DDX-Dokuments, indem Sie die `CreateElement` -Methode des Objekts `XmlElement` aufrufen. Diese Methode erstellt ein `Element` -Objekt, das das Stammelement darstellt. Übergeben Sie einen string -Wert, der den Namen des Elements darstellt, an die `CreateElement` -Methode. Legen Sie einen Wert für das DDX-Element fest, indem Sie dessen `SetAttribute`-Methode aufrufen. Hängen Sie abschließend das Element an das DDX-Dokument an, indem Sie die `AppendChild` -Methode des Objekts `XmlElement` aufrufen. Übergeben Sie das DDX-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * Erstellen Sie das Element `PDFsFromBookmarks` des DDX-Dokuments, indem Sie die Methode `CreateElement` des Objekts `XmlElement` aufrufen. Übergeben Sie einen string -Wert, der den Namen des Elements darstellt, an die `CreateElement` -Methode. Legen Sie anschließend einen Wert für das Element fest, indem Sie dessen `SetAttribute`-Methode aufrufen. Hängen Sie das Element `PDFsFromBookmarks` an das Stammelement an, indem Sie die Methode `AppendChild` des Elements `DDX` aufrufen. Übergeben Sie das Elementobjekt `PDFsFromBookmarks` als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * Erstellen Sie das Element `PDF` des DDX-Dokuments, indem Sie die Methode `CreateElement` des Objekts `XmlElement` aufrufen. Übergeben Sie einen string -Wert, der den Namen des Elements darstellt, an die `CreateElement` -Methode. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `SetAttribute`-Methode aufrufen. Hängen Sie das Element `PDF` an das Element `PDFsFromBookmarks` an, indem Sie die Methode `PDFsFromBookmarks` des Elements `AppendChild` aufrufen. Übergeben Sie das Elementobjekt `PDF` als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Konvertieren Sie das DDX-Dokument.

   * Erstellen Sie ein Objekt `System.IO.MemoryStream`, indem Sie den Konstruktor verwenden.
   * Füllen Sie das `MemoryStream`-Objekt mit dem DDX-Dokument, indem Sie das `XmlElement`-Objekt verwenden, das das DDX-Dokument darstellt. Rufen Sie die `Save` -Methode des Objekts `XmlElement` auf und übergeben Sie das `MemoryStream` -Objekt.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit Daten aus dem `MemoryStream` -Objekt. Der folgende Code zeigt diese Anwendungslogik:

      ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Erstellen Sie ein `BLOB` -Objekt. Weisen Sie das Byte-Array dem `BLOB` -Feld des Objekts `MTOM` zu.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB` -Objekt wird als Argument an `invokeOneDocument` übergeben.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec` -Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem `AssemblerOptionSpec`-Datenelement des `failOnError`-Objekts zu.

1. Aufteilen des PDF-Dokuments.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das dynamisch erstellte DDX-Dokument darstellt
   * Das `mapItem`-Array, das das PDF-Eingabedokument enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die neu erstellten PDF-Dokumente abzurufen:

   * Greifen Sie auf das `AssemblerResult` -Feld des Objekts `documents` zu, bei dem es sich um ein `Map` -Objekt handelt, das die zerlegten PDF-Dokumente enthält.
   * Durchsuchen Sie das `Map`-Objekt, um jedes Zieldokument abzurufen. Dann das `value` des Array-Mitglieds in ein `BLOB`-Element umwandeln.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB` -Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
