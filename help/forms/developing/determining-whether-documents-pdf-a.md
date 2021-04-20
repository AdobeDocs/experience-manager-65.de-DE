---
title: Bestimmen, ob Dokumente PDF/A-konform sind
seo-title: Bestimmen, ob Dokumente PDF/A-konform sind
description: Verwenden Sie den Assembler-Dienst, um zu ermitteln, ob ein PDF-Dokument mit der Java-API und der Web-Service-API PDF/A-kompatibel ist.
seo-description: Verwenden Sie den Assembler-Dienst, um zu ermitteln, ob ein PDF-Dokument mit der Java-API und der Web-Service-API PDF/A-kompatibel ist.
uuid: 4e9d8c8f-2153-411b-9c4b-2d14b3c8f4bb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: c429d6e1-7847-43c8-bf75-cb0078dbb9d5
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2110'
ht-degree: 4%

---


# Bestimmen, ob Dokumente PDF/A-konform sind {#determining-whether-documents-are-pdf-a-compliant}

Sie können mithilfe des Assembler-Dienstes ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist. Ein PDF/A-Dokument existiert als Archivierungsformat, das für die langfristige Erhaltung der Inhalte des Dokuments gedacht ist. Die Schriftarten werden im Dokument eingebettet und die Datei bleibt unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte.

Die PDF/A-1-Spezifikation besteht aus zwei Stufen der Konformität, nämlich A und B. Der Hauptunterschied zwischen den beiden Ebenen ist die logische Unterstützung (Barrierefreiheit), die nicht für die Konformität Stufe B erforderlich ist. Unabhängig von der Konformitätsstufe schreibt PDF/A-1 vor, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind. Derzeit wird nur PDF/A-1b bei der Überprüfung (und Konvertierung) unterstützt.

Für diese Diskussion nehmen Sie an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
         <DocumentInformation source="Loan.pdf" result="Loan_result.xml">
         <PDFAValidation compliance="PDF/A-1b" resultLevel="Detailed"                       ignoreUnusedResources="true" allowCertificationSignatures="true" />
     </DocumentInformation>
 </DDX>
```

Innerhalb dieses DDX-Dokuments weist das `DocumentInformation`-Element den Assembler-Dienst an, Informationen zum PDF-Dokument für die Eingabe zurückzugeben. Innerhalb des Elements `DocumentInformation` weist das Element `PDFAValidation` den Assembler-Dienst an, anzugeben, ob das PDF-Dokument PDF/A-kompatibel ist.

Der Assembler-Dienst gibt Informationen zurück, die angeben, ob das Eingabe-PDF-Dokument in einem XML-Dokument, das ein `PDFAConformance`-Element enthält, PDF/A-kompatibel ist. Wenn das PDF-Dokument für die Eingabe PDF/A-kompatibel ist, ist der Wert des Attributs `PDFAConformance` des Elements `isCompliant` `true`. Wenn das PDF-Dokument nicht PDF/A-kompatibel ist, lautet der Wert des `PDFAConformance`-Elementattributs `isCompliant` `false`.

>[!NOTE]
>
>Da das in diesem Abschnitt angegebene DDX-Dokument ein `DocumentInformation`-Element enthält, gibt der Assembler-Dienst anstelle eines PDF-Dokuments XML-Daten zurück. Das heißt, der Assembler-Dienst assembliert oder zerlegt kein PDF-Dokument. Gibt Informationen zum PDF-Dokument der Eingabe in einem XML-Dokument zurück.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Ein DDX-Dokument muss referenziert werden, um einen Assembler-Dienstvorgang durchzuführen. Um festzustellen, ob ein PDF-Eingabedateielement PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument das `PDFAValidation`-Dokument in einem `DocumentInformation`-Element enthält. Das Element `PDFAValidation` weist den Assembler-Dienst an, ein XML-Dokument zurückzugeben, das angibt, ob das PDF-Eingabedateielement PDF/A-kompatibel ist.

**Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität**

Ein PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren. Informationen zu den verfügbaren Laufzeitoptionen finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Abrufen von Informationen zum PDF-Dokument**

Nachdem Sie den Assembler-Dienstclient erstellt haben, auf das DDX-Dokument verweisen, ein interaktives PDF-Dokument referenzieren und Laufzeitoptionen festlegen, können Sie den Vorgang `invokeDDX` aufrufen. Da das DDX-Dokument das Element `DocumentInformation` enthält, gibt der Assembler-Dienst anstelle eines PDF-Dokuments XML-Daten zurück.

**Das zurückgegebene XML-Dokument speichern**

Das vom Assembler-Dienst zurückgegebene XML-Dokument gibt an, ob das PDF-Eingabedokument PDF/A-kompatibel ist. Wenn das PDF-Dokument für die Eingabe beispielsweise nicht PDF/A-kompatibel ist, gibt der Assembler-Dienst ein XML-Dokument zurück, das das folgende Element enthält:

```xml
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Speichern Sie das XML-Dokument als XML-Datei, damit Sie die Datei öffnen und die Ansicht der Ergebnisse durchführen können.

**Siehe auch**

[Bestimmen Sie mithilfe der Java-API, ob ein Dokument PDF/A-konform ist.](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api)

[Bestimmen Sie mithilfe der Webdienst-API, ob ein Dokument PDF/A-konform ist.](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Bestimmen Sie mithilfe der Java-API {#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api}, ob ein Dokument PDF/A-konform ist.

Bestimmen Sie mithilfe der Assembler Service API (Java), ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt. Um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument das `PDFAValidation`-Element enthält, das in einem `DocumentInformation`-Element enthalten ist.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie den Konstruktor verwenden und den Speicherort eines PDF-Dokuments übergeben, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie den Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben, das das PDF-Dokument enthält.
   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern des PDF-Eingabedokuments mit einem `HashMap`-Konstruktor verwendet wird.
   * hinzufügen Sie einen Eintrag für das `java.util.Map`-Objekt, indem Sie die `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. Der Wert des Quellelements im DDX-Dokument, der in diesem Abschnitt eingeführt wird, lautet z. B. &quot;Loan.pdf&quot;.
      * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument für die Eingabe enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `setFailOnError`-Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Abrufen von Informationen zum PDF-Dokument.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden erforderlichen Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das die PDF-Eingabedatei enthält, mit der die PDF/A-Kompatibilität ermittelt wird
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das XML-Daten enthält, die angeben, ob das PDF-Dokument PDF/A-kompatibel ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob es sich bei dem PDF-Dokument um ein PDF/A-Dokument handelt:

   * Rufen Sie die `AssemblerResult`-Methode des Objekts `getDocuments` auf. Gibt ein `java.util.Map`-Objekt zurück.
   * Durchlaufen Sie das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `com.adobe.idp.Document`-Objektmethode `copyToFile` auf, um das XML-Dokument zu extrahieren. Stellen Sie sicher, dass Sie die XML-Daten als XML-Datei speichern.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Bestimmen, ob ein Dokument PDF/A-kompatibel ist, mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api) (SOAP-Modus)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Bestimmen Sie mithilfe der Webdienst-API {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}, ob ein Dokument PDF/A-kompatibel ist.

Bestimmen Sie mithilfe der Assembler Service API (Webdienst), ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der den WSDL-Wert an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedatums und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Collection-Objekt wird zum Speichern des PDF-Dokuments verwendet.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie dem Feld `MyMapOf_xsd_string_To_xsd_anyType_Item` des Objekts einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. `key` Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, in dem das PDF-Dokument gespeichert wird, dem `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objektfeld `value` zu.
   * hinzufügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt mit dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType`-Methode des Objekts&#39; `Add` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenmember, der zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie `false` dem `AssemblerOptionSpec`-Datenmember des Objekts `failOnError` zu.

1. Abrufen von Informationen zum PDF-Dokument.

   Rufen Sie die `invoke`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceService`

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das das PDF-Dokument für die Eingabe enthält. Seine Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und seine Werte müssen das `BLOB`-Objekt sein, das der PDF-Eingabedatei entspricht.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `invoke`-Methode gibt ein `AssemblerResult`-Objekt zurück, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob es sich bei dem PDF-Dokument um ein PDF/A-Dokument handelt:

   * Greifen Sie auf das Feld `AssemblerResult` des Objekts zu, bei dem es sich um ein `Map`-Objekt handelt, das die XML-Daten enthält, die angeben, ob das PDF-Dokument ein PDF/A-Dokument ist.`documents`
   * Durchlaufen Sie das `Map`-Objekt, um jedes resultierende Dokument abzurufen. Anschließend können Sie den Wert des Array-Mitglieds in ein `BLOB` umwandeln.
   * Extrahieren Sie die Binärdaten, die die XML-Daten darstellen, indem Sie auf das `BLOB`-Objektfeld `MTOM` zugreifen. Dieses Feld speichert ein Bytearray, in das Sie als XML-Datei schreiben können.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
