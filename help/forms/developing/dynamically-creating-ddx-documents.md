---
title: Dynamisches Erstellen von DDX-Dokumenten
seo-title: Dynamically Creating DDX Documents
description: Erstellen Sie ein DDX-Dokument dynamisch mit der Java-API und der Web Service-API. Wenn Sie ein DDX-Dokument dynamisch erstellen, können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden.
seo-description: Create a DDX document dynamically using the Java API and Web Service API. Dynamically creating a DDX document enables you to use values in the DDX document that are obtained during run-time.
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
workflow-type: ht
source-wordcount: '2163'
ht-degree: 100%

---

# Dynamisches Erstellen von DDX-Dokumenten {#dynamically-creating-ddx-documents}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Sie können ein DDX-Dokument dynamisch erstellen, das zum Ausführen eines Assembler-Vorgangs verwendet werden kann. Wenn Sie ein DDX-Dokument dynamisch erstellen, können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden. Zum dynamischen Erstellen eines DDX-Dokuments verwenden Sie Klassen, die zu der von Ihnen verwendeten Programmiersprache gehören. Wenn Sie beispielsweise ein Client-Programm mit Java entwickeln, verwenden Sie Klassen aus dem `org.w3c.dom.*`-Paket. Analog verwenden Sie Klassen aus dem `System.Xml`-Namespace, wenn Sie Microsoft .NET verwenden.

Bevor Sie das DDX-Dokument an den Assembler-Service übergeben können, konvertieren Sie den XML-Code aus einer `org.w3c.dom.Document`-Instanz in eine `com.adobe.idp.Document`-Instanz. Wenn Sie Webservices verwenden, konvertieren Sie den XML-Code aus dem Datentyp, der zum Erstellen des XML-Codes verwendet wurde (z. B. `XmlDocument`) in eine `BLOB`-Instanz.

Für diese Diskussion nehmen wir an, dass das folgende DDX-Dokument dynamisch erstellt wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDFsFromBookmarks prefix="stmt">
     <PDF source="AssemblerResultPDF.pdf"/>
 </PDFsFromBookmarks>
 </DDX>
```

Dieses DDX-Dokument zerlegt ein PDF-Dokument. Es wird empfohlen, dass Sie mit dem Zerlegen von PDF-Dokumenten vertraut sind.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument mithilfe eines dynamisch erstellten DDX-Dokuments zu zerlegen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Erstellen Sie das DDX-Dokument.
1. Konvertieren Sie das DDX-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Zerlegen Sie das PDF-Dokument.
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

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Service-Client erstellen.

**DDX-Dokument erstellen**

Erstellen Sie mit der von Ihnen verwendeten Programmiersprache ein DDX-Dokument. Beim Erstellen eines DDX-Dokuments, das ein PDF-Dokument zerlegt, müssen Sie sicherstellen, dass es das `PDFsFromBookmarks`-Element enthält. Konvertieren Sie den zum Erstellen des DDX-Dokuments verwendeten Datentyp in eine `com.adobe.idp.Document`-Instanz, wenn Sie die Java-API verwenden. Wenn Sie Webservices verwenden, konvertieren Sie den Datentyp in eine `BLOB`-Instanz.

**Das DDX-Dokument konvertieren**

Ein DDX-Dokument, das mithilfe von `org.w3c.dom`-Klassen erstellt wird, muss in ein `com.adobe.idp.Document`-Objekt konvertiert werden. Verwenden Sie Java XML-Transformation-Klassen, um diese Aufgabe bei Verwendung der Java-API auszuführen. Wenn Sie Webservices verwenden, konvertieren Sie das DDX-Dokument in ein `BLOB`-Objekt.

**Auf ein zu zerlegendes PDF-Dokument verweisen**

Um ein PDF-Dokument zu zerlegen, verweisen Sie auf eine PDF-Datei, die das zu zerlegende PDF-Dokument darstellt. Wenn es an den Assembler-Service übergeben wird, wird für jedes Lesezeichen der Stufe 1 im Dokument ein separates PDF-Dokument zurückgegeben.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Service angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Zum Festlegen von Laufzeitoptionen verwenden Sie ein `AssemblerOptionSpec`-Objekt.

**Das PDF-Dokument zerlegen**

Zerlegen Sie das PDF-Dokument durch Aufrufen des `invokeDDX`-Vorgangs. Übergeben Sie das dynamisch erstellte DDX-Dokument. Der Assembler-Service gibt zerlegte PDF-Dokumente in einem Sammlungsobjekt zurück.

**Die zerlegten PDF-Dokumente speichern**

Alle zerlegten PDF-Dokumente werden in einem Sammlungsobjekt zurückgegeben. Durchlaufen Sie das Sammlungsobjekt und speichern Sie jedes PDF-Dokument als PDF-Datei.

**Siehe auch**

[DDX-Dokument mithilfe der Java-API dynamisch erstellen](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-java-api)

[DDX-Dokument mithilfe der Webservice-API dynamisch erstellen](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuerte Aufteilung von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## DDX-Dokument mithilfe der Java-API dynamisch erstellen {#dynamically-create-a-ddx-document-using-the-java-api}

Erstellen Sie dynamisch ein DDX-Dokument und zerlegen Sie ein PDF-Dokument mithilfe der Assembler Service-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Erstellen Sie das DDX-Dokument.

   * Erstellen Sie ein Java-`DocumentBuilderFactory`-Objekt, indem Sie die Methode `newInstance` der Klasse `DocumentBuilderFactory` aufrufen.
   * Java erstellen `DocumentBuilder` -Objekt durch Aufruf der `DocumentBuilderFactory` -Objekt `newDocumentBuilder` -Methode.
   * Rufen Sie die Methode `newDocument` des `DocumentBuilder`-Objekts auf, um ein `org.w3c.dom.Document`-Objekt zu instanziieren.
   * Erstellen Sie das Stammelement des DDX-Dokuments, indem Sie die Methode `createElement` des `org.w3c.dom.Document`-Objekts aufrufen. Diese Methode erstellt ein `Element`-Objekt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die Methode `createElement`. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen Methode `setAttribute` aufrufen. Hängen Sie schließlich das Element an das Kopfzeilenelement an, indem Sie die Methode `appendChild` des Kopfzeilenelements aufrufen und das Objekt des untergeordneten Elements als Argument übergeben. Die folgenden Code-Zeilen zeigen diese Programmlogik:
      ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Erstellen Sie das Element `PDFsFromBookmarks`, indem Sie die Methode `createElement` des `Document`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die Methode `createElement`. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie einen Wert für das Element `PDFsFromBookmarks` fest, indem Sie seine `setAttribute`-Methode aufrufen. Hängen Sie das Element `PDFsFromBookmarks` an das `DDX`-Element an, indem Sie die Methode `appendChild` des DDX-Elements aufrufen. Übergeben Sie das Objekt des Elements `PDFsFromBookmarks` als Argument. Die folgenden Code-Zeilen zeigen diese Programmlogik:

      ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Erstellen Sie ein `PDF`-Element, indem Sie die Methode `createElement` des `Document`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie einen Wert für das `PDF`-Element fest, indem Sie seine `setAttribute`-Methode aufrufen. Hängen Sie das `PDF`-Element an das `PDFsFromBookmarks`-Element an, indem Sie die Methode `appendChild` des `PDFsFromBookmarks`-Elements aufrufen. Übergeben Sie das `PDF`-Elementobjekt als Argument. Die folgenden Code-Zeilen zeigen diese Programmlogik:

      ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Konvertieren Sie das DDX-Dokument.

   * Erstellen Sie ein `javax.xml.transform.Transformer`-Objekt, indem Sie die statische Methode `newInstance` des `javax.xml.transform.Transformer`-Objekts aufrufen.
   * Erstellen Sie ein `Transformer`-Objekt, indem Sie die Methode `newTransformer` des `TransformerFactory`-Objekts aufrufen.
   * Erstellen Sie ein Objekt `ByteArrayOutputStream`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein Objekt `javax.xml.transform.dom.DOMSource`, indem Sie den Konstruktor verwenden. Übergeben Sie das `org.w3c.dom.Document`-Objekt, das das DDX-Dokument darstellt.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource`-Objekt, indem Sie seinen Konstruktor verwenden und das `ByteArrayOutputStream`-Objekt übergeben.
   * Füllen Sie das Java-`ByteArrayOutputStream`-Objekt, indem Sie die Methode `transform` des `javax.xml.transform.Transformer`-Objekts aufrufen. Übergeben Sie das `javax.xml.transform.dom.DOMSource`- und das `javax.xml.transform.stream.StreamResult`-Objekt.
   * Erstellen Sie ein Byte-Array und weisen Sie ihm die Größe des `ByteArrayOutputStream`-Objekts zu.
   * Füllen Sie das Byte-Array, indem Sie die Methode `toByteArray` des `ByteArrayOutputStream`-Objekts aufrufen.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie dessen Konstruktor verwenden und das Byte-Array übergeben.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von PDF-Eingabedokumenten verwendet wird, indem Sie einen `HashMap`-Konstruktor verwenden.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des zu zerlegenden PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das zu zerlegende PDF-Dokument enthält.
   * Fügen Sie dem `java.util.Map`-Objekt einen Eintrag hinzu, indem Sie seine Methode `put` aufrufen und die folgenden Argumente übergeben:

      * Eine Zeichenfolge, die den Speichernamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Im dynamisch erstellten DDX-Dokument lautet der Wert `AssemblerResultPDF.pdf`.)
      * Ein `com.adobe.idp.Document`-Objekt, das das zu zerlegende PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die Methode `setFailOnError` des `AssemblerOptionSpec`-Objekts auf und übergeben `false`.

1. Zerlegen Sie das PDF-Dokument.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das dynamisch erstellte DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das das zu zerlegende PDF-Dokument enthält
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Auftragsprotokollebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die zerlegten PDF-Dokumente und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die zerlegten PDF-Dokumente abzurufen:

   * Rufen Sie die `getDocuments`-Methode des `AssemblerResult`-Objekts auf. Diese Methode gibt ein `java.util.Map`-Objekt zurück.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `copyToFile`-Methode des `com.adobe.idp.Document`-Objekts auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Dynamisches Erstellen eines DDX-Dokuments mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-dynamically-creating-a-ddx-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## DDX-Dokument mithilfe der Webservice-API dynamisch erstellen {#dynamically-create-a-ddx-document-using-the-web-service-api}

Erstellen Sie ein DDX-Dokument dynamisch und zerlegen Sie ein PDF-Dokument mithilfe der Assembler-Service-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Service-Referenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert mit der WSDL an den AEM Forms-Service (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekr, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zum `BasicHttpBindingSecurity.Security.Mode`-Feld zu.

1. Erstellen Sie das DDX-Dokument.

   * Erstellen Sie ein Objekt `System.Xml.XmlElement`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie das Stammelement des DDX-Dokuments, indem Sie die `CreateElement`-Methode des `XmlElement`-Objekts aufrufen. Diese Methode erstellt ein `Element`-Objekt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement`-Methode. Legen Sie einen Wert für das DDX-Element fest, indem Sie dessen `SetAttribute`-Methode aufrufen. Fügen Sie abschließend das Element an das DDX-Dokument an, indem Sie die `AppendChild`-Methode des `XmlElement`-Objekts aufrufen. Übergeben Sie das DDX-Objekt als Argument. Die folgenden Code-Zeilen zeigen diese Programmlogik:

      ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * Erstellen Sie das `PDFsFromBookmarks`-Element des DDX-Dokuments, indem Sie die `CreateElement`-Methode des `XmlElement`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement`-Methode. Legen Sie anschließend einen Wert für das Element fest, indem Sie dessen `SetAttribute`-Methode aufrufen. Fügen Sie das `PDFsFromBookmarks`-Element an das Stammelement an, indem Sie die `AppendChild`-Methode des `DDX`-Elements aufrufen. Übergeben Sie das `PDFsFromBookmarks`-Elementobjekt als Argument. Die folgenden Code-Zeilen zeigen diese Programmlogik:

      ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * Erstellen Sie das `PDF`-Element des DDX-Dokuments, indem Sie die `CreateElement`-Methode des `XmlElement`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement`-Methode. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `SetAttribute`-Methode aufrufen. Fügen Sie das `PDF`-Element an das `PDFsFromBookmarks`-Element an, indem Sie die `AppendChild`-Methode des `PDFsFromBookmarks`-Elements aufrufen. Übergeben Sie das `PDF`-Elementobjekt als Argument. Die folgenden Code-Zeilen zeigen diese Programmlogik:

      ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Konvertieren Sie das DDX-Dokument.

   * Erstellen Sie ein Objekt `System.IO.MemoryStream`, indem Sie den Konstruktor verwenden.
   * Füllen Sie das `MemoryStream`-Objekt mit dem DDX-Dokument, indem Sie das `XmlElement`-Objekt verwenden, das das DDX-Dokument darstellt. Rufen Sie die `Save`-Methode des `XmlElement`-Objekts auf, und übergeben Sie das `MemoryStream`-Objekt.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit den Daten im `MemoryStream`-Objekt. Der folgende Code zeigt diese Programmlogik:

      ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Erstellen Sie ein `BLOB`-Objekt. Weisen Sie das Byte-Array dem Feld `MTOM` des `BLOB`-Objekts zu.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB`-Objekt wird an `invokeOneDocument` als Argument übergeben.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie dessen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die Länge des zu lesenden Streams übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem `failOnError`-Datenelement des `AssemblerOptionSpec`-Objekts zu.

1. Zerlegen Sie das PDF-Dokument.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das dynamisch erstellte DDX-Dokument darstellt
   * Das `mapItem`-Array, das das PDF-Eingabedokument enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags sowie alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die neu erstellten PDF-Dokumente abzurufen:

   * Greifen Sie auf das `documents`-Feld des `AssemblerResult`-Objekts zu. Dies ist ein `Map`-Objekt, das die zerlegten PDF-Dokumente enthält.
   * Iterieren Sie durch das `Map`-Objekt, um alle Zieldokumente abzurufen. Wandeln Sie dann `value` der Array-Elemente in `BLOB` um.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `MTOM`-Eigenschaft von dessen `BLOB`-Objekt zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
