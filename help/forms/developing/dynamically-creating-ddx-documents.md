---
title: DDDX-Dokumente dynamisch erstellen
seo-title: DDDX-Dokumente dynamisch erstellen
description: DDX-Dokument dynamisch mit der Java-API und der Web-Service-API erstellen Durch das dynamische Erstellen eines DDX-Dokuments können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden.
seo-description: DDX-Dokument dynamisch mit der Java-API und der Web-Service-API erstellen Durch das dynamische Erstellen eines DDX-Dokuments können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden.
uuid: b73e8069-6c9f-4517-a0ae-f3d503191d2d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 2ad227de-68a8-446f-8c4f-a33a6f95bec8
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2200'
ht-degree: 4%

---


# Dynamisches Erstellen von DDX-Dokumenten {#dynamically-creating-ddx-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Sie können ein DDX-Dokument dynamisch erstellen, das zur Durchführung eines Assembler-Vorgangs verwendet werden kann. Durch das dynamische Erstellen eines DDX-Dokuments können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden. Um ein DDX-Dokument dynamisch zu erstellen, verwenden Sie Klassen, die zur verwendeten Programmiersprache gehören. Wenn Sie beispielsweise Ihre Clientanwendung mit Java entwickeln, verwenden Sie Klassen, die zum `org.w3c.dom.*`Paket gehören. Wenn Sie Microsoft .NET verwenden, verwenden Sie ebenfalls Klassen, die zum Namensraum `System.Xml` gehören.

Bevor Sie das DDX-Dokument an den Assembler-Dienst übergeben können, konvertieren Sie die XML-Datei von einer `org.w3c.dom.Document`-Instanz in eine `com.adobe.idp.Document`-Instanz. Wenn Sie Webdienste verwenden, konvertieren Sie die XML aus dem Datentyp, der zum Erstellen der XML verwendet wird (z. B. `XmlDocument`), in eine `BLOB`-Instanz.

Angenommen, das folgende DDX-Dokument wird dynamisch erstellt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDFsFromBookmarks prefix="stmt">
     <PDF source="AssemblerResultPDF.pdf"/>
 </PDFsFromBookmarks>
 </DDX>
```

Dieses DDX-Dokument demontiert ein PDF-Dokument. Es wird empfohlen, sich mit der Demontage von PDF-Dokumenten vertraut zu machen.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So zerlegen Sie ein PDF-Dokument mit einem dynamisch erstellten DDX-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Erstellen Sie das DDX-Dokument.
1. Konvertieren Sie das DDX-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Disassemblieren des PDF-Dokuments.
1. Speichern Sie die zerlegten PDF-Dokumente.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, erstellen Sie einen Assembler-Dienstclient.

**DDX-Dokument erstellen**

Erstellen Sie ein DDX-Dokument mit der verwendeten Programmiersprache. Um ein DDX-Dokument zu erstellen, das ein PDF-Dokument disassembliert, stellen Sie sicher, dass es das Element `PDFsFromBookmarks` enthält. Konvertieren Sie den zum Erstellen des DDX-Dokuments verwendeten Datentyp in eine `com.adobe.idp.Document`-Instanz, wenn Sie die Java-API verwenden. Wenn Sie Webdienste verwenden, konvertieren Sie den Datentyp in eine `BLOB`-Instanz.

**DDX-Dokument konvertieren**

Ein DDX-Dokument, das mithilfe von `org.w3c.dom`-Klassen erstellt wird, muss in ein `com.adobe.idp.Document`-Objekt konvertiert werden. Um diese Aufgabe bei Verwendung der Java-API auszuführen, verwenden Sie Java XML-Transformationsklassen. Wenn Sie Webdienste verwenden, konvertieren Sie das DDX-Dokument in ein `BLOB`-Objekt.

**Referenzieren eines zu trennenden PDF-Dokuments**

Um ein PDF-Dokument zu zerlegen, verweisen Sie auf eine PDF-Datei, die das zu zerlegende PDF-Dokument darstellt. Beim Übermitteln an den Assembler-Dienst wird für jedes Lesezeichen der Stufe 1 im Dokument ein separates PDF-Dokument zurückgegeben.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren. Um Laufzeitoptionen festzulegen, verwenden Sie ein `AssemblerOptionSpec`-Objekt.

**Auflösung des PDF-Dokuments**

Trennen Sie das PDF-Dokument, indem Sie den Vorgang `invokeDDX` aufrufen. Übergeben Sie das dynamisch erstellte DDX-Dokument. Der Assembler-Dienst gibt nicht zusammengesetzte PDF-Dokumente innerhalb eines Collection-Objekts zurück.

**Speichern Sie die zerlegten PDF-Dokumente**

Alle zerlegten PDF-Dokumente werden innerhalb eines Collection-Objekts zurückgegeben. Durchsuchen Sie das Sammlungsobjekt und speichern Sie jedes PDF-Dokument als PDF-Datei.

**Siehe auch**

[Dynamisches Erstellen eines DDX-Dokuments mit der Java-API](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-java-api)

[Dynamisches Erstellen eines DDX-Dokuments mit der Webdienst-API](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatische Demontage von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## Dynamisches Erstellen eines DDX-Dokuments mit der Java-API {#dynamically-create-a-ddx-document-using-the-java-api}

Dynamisches Erstellen eines DDX-Dokuments und Zerlegen eines PDF-Dokuments mithilfe der Assembler Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Erstellen Sie das DDX-Dokument.

   * Erstellen Sie ein Java `DocumentBuilderFactory`-Objekt, indem Sie die `DocumentBuilderFactory`-Klasse&quot;`newInstance`-Methode aufrufen.
   * Erstellen Sie ein Java `DocumentBuilder`-Objekt, indem Sie die `DocumentBuilderFactory`-Objektmethode `newDocumentBuilder` aufrufen.
   * Rufen Sie die `newDocument`-Methode des Objekts auf, um ein `org.w3c.dom.Document`-Objekt zu instanziieren.`DocumentBuilder`
   * Erstellen Sie das Stammelement des DDX-Dokuments, indem Sie die `createElement`-Methode des Objekts aufrufen. `org.w3c.dom.Document` Diese Methode erstellt ein `Element`-Objekt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement`-Methode. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie als Nächstes einen Wert für das untergeordnete Element fest, indem Sie die zugehörige `setAttribute`-Methode aufrufen. Hängen Sie das Element schließlich an das Header-Element an, indem Sie die `appendChild`-Methode des Header-Elements aufrufen und das untergeordnete Element-Objekt als Argument übergeben. Die folgenden Codezeilen zeigen diese Anwendungslogik:
      ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Erstellen Sie das Element `PDFsFromBookmarks`, indem Sie die `Document`-Methode des Objekts `createElement` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement`-Methode. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie einen Wert für das `PDFsFromBookmarks`-Element fest, indem Sie dessen `setAttribute`-Methode aufrufen. Hängen Sie das Element `PDFsFromBookmarks` an das Element `DDX` an, indem Sie die `appendChild`-Methode des DDX-Elements aufrufen. Übergeben Sie das Elementobjekt `PDFsFromBookmarks` als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Erstellen Sie ein `PDF`-Element, indem Sie die `Document`-Objektmethode `createElement` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie einen Wert für das `PDF`-Element fest, indem Sie dessen `setAttribute`-Methode aufrufen. Hängen Sie das Element `PDF` an das Element `PDFsFromBookmarks` an, indem Sie die `PDFsFromBookmarks`-Methode des Elements `appendChild` aufrufen. Übergeben Sie das Elementobjekt `PDF` als Argument. Die folgende Codezeile zeigt diese Anwendungslogik:

      ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Konvertieren Sie das DDX-Dokument.

   * Erstellen Sie ein `javax.xml.transform.Transformer`-Objekt, indem Sie die statische `javax.xml.transform.Transformer`-Methode des Objekts aufrufen.`newInstance`
   * Erstellen Sie ein `Transformer`-Objekt, indem Sie die `TransformerFactory`-Methode des Objekts `newTransformer` aufrufen.
   * Erstellen Sie ein Objekt `ByteArrayOutputStream`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein Objekt `javax.xml.transform.dom.DOMSource`, indem Sie den Konstruktor verwenden. Übergeben Sie das `org.w3c.dom.Document`-Objekt, das das DDX-Dokument darstellt.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource`-Objekt, indem Sie seinen Konstruktor verwenden und das `ByteArrayOutputStream`-Objekt übergeben.
   * Füllen Sie das Java `ByteArrayOutputStream`-Objekt, indem Sie die `javax.xml.transform.Transformer`-Methode des Objekts `transform` aufrufen. Übergeben Sie die Objekte `javax.xml.transform.dom.DOMSource` und `javax.xml.transform.stream.StreamResult`.
   * Erstellen Sie ein Bytearray und weisen Sie dem Bytearray die Größe des Objekts `ByteArrayOutputStream` zu.
   * Füllen Sie das Bytearray, indem Sie die `ByteArrayOutputStream`-Methode des Objekts `toByteArray` aufrufen.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie dessen Konstruktor verwenden und das Bytearray übergeben.

1. Verweisen Sie auf ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von PDF-Eingabedokumenten mit einem `HashMap`-Konstruktor verwendet wird.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie den Konstruktor verwenden und die Position des PDF-Dokuments zur Auflösung übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält, zur Auflösung.
   * hinzufügen Sie einen Eintrag für das `java.util.Map`-Objekt, indem Sie die `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Im dynamisch erstellten DDX-Dokument ist der Wert `AssemblerResultPDF.pdf`.)
      * Ein `com.adobe.idp.Document`-Objekt, das das zu zerlegende PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `setFailOnError`-Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Disassemblieren des PDF-Dokuments.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das dynamisch erstellte DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das das zu zerlegende PDF-Dokument enthält
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschriftart und der Auftragsprotokollebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die deassemblierten PDF-Dokumente und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   So rufen Sie die zerlegten PDF-Dokumente ab:

   * Rufen Sie die `AssemblerResult`-Methode des Objekts `getDocuments` auf. Diese Methode gibt ein `java.util.Map`-Objekt zurück.
   * Durchlaufen Sie das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `com.adobe.idp.Document`-Objektmethode `copyToFile` auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Dynamisches Erstellen eines DDX-Dokuments mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-dynamically-creating-a-ddx-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Dynamisches Erstellen eines DDX-Dokuments mit der Webdienst-API {#dynamically-create-a-ddx-document-using-the-web-service-api}

Dynamisches Erstellen eines DDX-Dokuments und Aufteilen eines PDF-Dokuments mithilfe der Assembler Service API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der den WSDL-Wert an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Erstellen Sie das DDX-Dokument.

   * Erstellen Sie ein Objekt `System.Xml.XmlElement`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie das Stammelement des DDX-Dokuments, indem Sie die `CreateElement`-Methode des Objekts aufrufen. `XmlElement` Diese Methode erstellt ein `Element`-Objekt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement`-Methode. Legen Sie einen Wert für das DDX-Element fest, indem Sie dessen `SetAttribute`-Methode aufrufen. Hängen Sie das Element schließlich an das DDX-Dokument an, indem Sie die `XmlElement`-Objektmethode `AppendChild` aufrufen. Übergeben Sie das DDX-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * Erstellen Sie das Element `PDFsFromBookmarks` des DDX-Dokuments, indem Sie die `CreateElement`-Methode des Objekts aufrufen. `XmlElement` Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement`-Methode. Legen Sie als Nächstes einen Wert für das Element fest, indem Sie dessen `SetAttribute`-Methode aufrufen. Hängen Sie das Element `PDFsFromBookmarks` an das Stammelement an, indem Sie die `DDX`-Methode des Elements `AppendChild` aufrufen. Übergeben Sie das Elementobjekt `PDFsFromBookmarks` als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * Erstellen Sie das Element `PDF` des DDX-Dokuments, indem Sie die `CreateElement`-Methode des Objekts aufrufen. `XmlElement` Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement`-Methode. Legen Sie als Nächstes einen Wert für das untergeordnete Element fest, indem Sie die zugehörige `SetAttribute`-Methode aufrufen. Hängen Sie das Element `PDF` an das Element `PDFsFromBookmarks` an, indem Sie die `PDFsFromBookmarks`-Methode des Elements `AppendChild` aufrufen. Übergeben Sie das Elementobjekt `PDF` als Argument. Die folgende Codezeile zeigt diese Anwendungslogik:

      ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Konvertieren Sie das DDX-Dokument.

   * Erstellen Sie ein Objekt `System.IO.MemoryStream`, indem Sie den Konstruktor verwenden.
   * Füllen Sie das `MemoryStream`-Objekt mit dem DDX-Dokument, indem Sie das `XmlElement`-Objekt verwenden, das das DDX-Dokument darstellt. Rufen Sie die `Save`-Methode des Objekts auf und übergeben Sie das `MemoryStream`-Objekt.`XmlElement`
   * Erstellen Sie ein Byte-Array und füllen Sie es mit Daten aus dem `MemoryStream`-Objekt. Der folgende Code zeigt diese Anwendungslogik:

      ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Erstellen Sie ein `BLOB`-Objekt. Weisen Sie das Bytearray dem `BLOB`-Objektfeld `MTOM` zu.

1. Verweisen Sie auf ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB`-Objekt wird als Argument an das `invokeOneDocument`-Objekt übergeben.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Eingabedatums und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenmember, der zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie `false` dem `AssemblerOptionSpec`-Datenmember des Objekts `failOnError` zu.

1. Disassemblieren des PDF-Dokuments.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `BLOB`-Objekt, das das dynamisch erstellte DDX-Dokument darstellt
   * Das `mapItem`-Array, das das PDF-Dokument für die Eingabe enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   So rufen Sie die neu erstellten PDF-Dokumente ab:

   * Greifen Sie auf das Feld `AssemblerResult` des Objekts zu, bei dem es sich um ein `Map`-Objekt handelt, das die zerlegten PDF-Dokumente enthält.`documents`
   * Durchlaufen Sie das `Map`-Objekt, um jedes resultierende Dokument abzurufen. Anschließend können Sie die `value` des Array-Mitglieds in ein `BLOB`-Element umwandeln.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB`-Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
