---
title: Bestimmen, ob Dokumente PDF/A-konform sind
seo-title: Bestimmen, ob Dokumente PDF/A-konform sind
description: 'null'
seo-description: 'null'
uuid: 4e9d8c8f-2153-411b-9c4b-2d14b3c8f4bb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: c429d6e1-7847-43c8-bf75-cb0078dbb9d5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Determining Whether Documents Are PDF/A-Compliant {#determining-whether-documents-are-pdf-a-compliant}

Sie können mithilfe des Assembler-Dienstes ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist. Ein PDF/A-Dokument existiert als Archivformat, das für die langfristige Erhaltung des Dokumentinhalts vorgesehen ist. Die Schriftarten werden im Dokument eingebettet und die Datei bleibt unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte.

Die PDF/A-1-Spezifikation besteht aus zwei Konformitätsstufen, nämlich A und B. Der Hauptunterschied zwischen den beiden Ebenen ist die logische Unterstützung (Barrierefreiheit), die nicht für die Konformität Stufe B erforderlich ist. Unabhängig von der Konformitätsstufe schreibt PDF/A-1 vor, dass alle Schriftarten in das erstellte PDF/A-Dokument eingebettet sind. Derzeit wird nur PDF/A-1b bei der Überprüfung (und Konvertierung) unterstützt.

Für diese Diskussion nehmen Sie an, dass das folgende DDX-Dokument verwendet wird.

```as3
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
         <DocumentInformation source="Loan.pdf" result="Loan_result.xml">
         <PDFAValidation compliance="PDF/A-1b" resultLevel="Detailed"                       ignoreUnusedResources="true" allowCertificationSignatures="true" />
     </DocumentInformation>
 </DDX>
```

In diesem DDX-Dokument weist das `DocumentInformation` Element den Assembler-Dienst an, Informationen zum PDF-Eingabedokument zurückzugeben. Innerhalb des `DocumentInformation` Elements weist das `PDFAValidation` Element den Assembler-Dienst an, anzugeben, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

Der Assembler-Dienst gibt Informationen zurück, die angeben, ob das PDF-Eingabedokument in einem XML-Dokument, das ein `PDFAConformance` Element enthält, PDF/A-kompatibel ist. Wenn das PDF-Eingabedokument PDF/A-kompatibel ist, wird der Wert des `PDFAConformance` Elementattributs `isCompliant` verwendet `true`. Wenn das PDF-Dokument nicht PDF/A-kompatibel ist, wird der Wert des `PDFAConformance` Elementattributs `isCompliant` verwendet `false`.

>[!NOTE]
>
>Da das in diesem Abschnitt angegebene DDX-Dokument ein `DocumentInformation` Element enthält, gibt der Assembler-Dienst anstelle eines PDF-Dokuments XML-Daten zurück. Das heißt, der Assembler-Dienst assembliert oder zerlegt kein PDF-Dokument. Gibt Informationen zum PDF-Eingabedokument in einem XML-Dokument zurück.

>[!NOTE]
>
>For more information about the Assembler service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So prüfen Sie, ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Verweisen Sie auf ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
1. Legen Sie Laufzeitoptionen fest.
1. Abrufen von Informationen zum PDF-Dokument.
1. Speichern Sie das zurückgegebene XML-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. For information about the location of all AEM Forms JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Ein DDX-Dokument muss referenziert werden, um einen Assembler-Dienstvorgang durchzuführen. Um festzustellen, ob ein PDF-Eingabedokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument das `PDFAValidation` Element in einem `DocumentInformation` Element enthält. Das `PDFAValidation` Element weist den Assembler-Dienst an, ein XML-Dokument zurückzugeben, das angibt, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

**Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität**

Ein PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec` Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Abrufen von Informationen zum PDF-Dokument**

Nachdem Sie den Assembler-Dienstclient erstellt haben, auf das DDX-Dokument verweisen, auf ein interaktives PDF-Dokument verweisen und Laufzeitoptionen festgelegt haben, können Sie den `invokeDDX` Vorgang aufrufen. Da das DDX-Dokument das `DocumentInformation` Element enthält, gibt der Assembler-Dienst anstelle eines PDF-Dokuments XML-Daten zurück.

**Das zurückgegebene XML-Dokument speichern**

Das vom Assembler-Dienst zurückgegebene XML-Dokument gibt an, ob das PDF-Eingabedokument PDF/A-kompatibel ist. Wenn das PDF-Eingabedokument beispielsweise nicht PDF/A-kompatibel ist, gibt der Assembler-Dienst ein XML-Dokument zurück, das das folgende Element enthält:

```as3
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Speichern Sie das XML-Dokument als XML-Datei, damit Sie die Datei öffnen und die Ergebnisse anzeigen können.

**Siehe auch**

[Bestimmen Sie mithilfe der Java-API, ob ein Dokument PDF/A-kompatibel ist.](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api)

[Bestimmen Sie mithilfe der Webdienst-API, ob ein Dokument PDF/A-kompatibel ist.](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Bestimmen Sie mithilfe der Java-API, ob ein Dokument PDF/A-kompatibel ist. {#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api}

Bestimmen Sie mithilfe der Assembler Service API (Java), ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `AssemblerServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt. Um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument das `PDFAValidation` Element enthält, das in einem `DocumentInformation` Element enthalten ist.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, indem Sie dessen Konstruktor verwenden und den Speicherort eines PDF-Dokuments übergeben, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie den Konstruktor verwenden und das Objekt übergeben, das das PDF-Dokument `java.io.FileInputStream` enthält.
   * Erstellen Sie ein `java.util.Map` Objekt, das zum Speichern des PDF-Eingabedokuments mithilfe eines `HashMap` Konstruktors verwendet wird.
   * Fügen Sie dem `java.util.Map` Objekt einen Eintrag hinzu, indem Sie dessen `put` Methode aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. Der Wert des Quellelements im DDX-Dokument, der in diesem Abschnitt eingeführt wird, lautet z. B. Loan.pdf.
      * Ein `com.adobe.idp.Document` Objekt, das das PDF-Eingabedokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `AssemblerOptionSpec` Methode des `setFailOnError` Objekts auf und übergeben Sie sie `false`.

1. Abrufen von Informationen zum PDF-Dokument.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeDDX` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document` Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map` Objekt, das die PDF-Eingabedatei enthält, mit der die PDF/A-Kompatibilität ermittelt wird
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object that specifies the run-time options
   Die `invokeDDX` Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult` Objekt zurück, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist:

   * Rufen Sie die `AssemblerResult` Methode des `getDocuments` Objekts auf. Dadurch wird ein `java.util.Map` Objekt zurückgegeben.
   * Durchlaufen des `java.util.Map` Objekts, bis Sie das resultierende `com.adobe.idp.Document` Objekt gefunden haben.
   * Rufen Sie die `com.adobe.idp.Document` Methode des `copyToFile` Objekts auf, um das XML-Dokument zu extrahieren. Stellen Sie sicher, dass Sie die XML-Daten als XML-Datei speichern.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Bestimmen, ob ein Dokument PDF/A-kompatibel ist, mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api) (SOAP-Modus)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Bestimmen Sie mithilfe der Webdienst-API, ob ein Dokument PDF/A-kompatibel ist. {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}

Bestimmen Sie mithilfe der Assembler Service API (Webdienst), ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient` Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` Objekt mithilfe des `System.ServiceModel.EndpointAddress` Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `AssemblerServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seine `MTOM` Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.
   * Create a `MyMapOf_xsd_string_To_xsd_anyType` object. Dieses Collection-Objekt wird zum Speichern des PDF-Dokuments verwendet.
   * Create a `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Objektfeld einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt `key` . Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB` Objekt, in dem das PDF-Dokument gespeichert wird, dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Objektfeld `value` zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekt dem `MyMapOf_xsd_string_To_xsd_anyType` Objekt hinzu. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` Objektmethode auf `Add` und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType` Objekt.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem zum `AssemblerOptionSpec` Objekt gehörenden Datenmember einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie ihn `false` dem `AssemblerOptionSpec` Datenmember des `failOnError` Objekts zu.

1. Abrufen von Informationen zum PDF-Dokument.

   Rufen Sie die `AssemblerServiceService` Objektmethode `invoke` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` Objekt, das das DDX-Dokument darstellt.
   * Das `MyMapOf_xsd_string_To_xsd_anyType` Objekt, das das PDF-Eingabedokument enthält. Die Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und ihre Werte müssen das `BLOB` Objekt sein, das der PDF-Eingabedatei entspricht.
   * Ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen angibt.
   Die `invoke` Methode gibt ein `AssemblerResult` Objekt zurück, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist:

   * Greifen Sie auf das `AssemblerResult` Feld des `documents` Objekts zu, das ein `Map` Objekt mit den XML-Daten ist, das angibt, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.
   * Durchlaufen Sie das `Map` Objekt, um jedes Zieldokument abzurufen. Anschließend wird der Wert des Array-Mitglieds in eine `BLOB`umgewandelt.
   * Extrahieren Sie die Binärdaten, die die XML-Daten darstellen, indem Sie auf das `BLOB` Objektfeld `MTOM` zugreifen. Dieses Feld speichert ein Bytearray, in das Sie als XML-Datei schreiben können.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
