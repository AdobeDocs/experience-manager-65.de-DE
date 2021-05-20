---
title: Bestimmen, ob Dokumente PDF/A-konform sind
seo-title: Bestimmen, ob Dokumente PDF/A-konform sind
description: Verwenden Sie den Assembler-Dienst, um mithilfe der Java-API und der Web Service-API zu ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist.
seo-description: Verwenden Sie den Assembler-Dienst, um mithilfe der Java-API und der Web Service-API zu ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist.
uuid: 4e9d8c8f-2153-411b-9c4b-2d14b3c8f4bb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: c429d6e1-7847-43c8-bf75-cb0078dbb9d5
role: Developer
exl-id: 096fd2ac-616f-484a-b093-9d98b2f87093
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2109'
ht-degree: 4%

---

# Bestimmen, ob Dokumente PDF/A-konform sind {#determining-whether-documents-are-pdf-a-compliant}

Sie können mithilfe des Assembler-Dienstes ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist. Ein PDF/A-Dokument existiert als Archivformat, das für die langfristige Speicherung des Dokumentinhalts vorgesehen ist. Die Schriftarten werden im Dokument eingebettet und die Datei bleibt unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte.

Die PDF/A-1-Spezifikation besteht aus zwei Konformitätsstufen, nämlich A und B. Der Hauptunterschied zwischen den beiden Ebenen ist die Unterstützung der logischen Struktur (Barrierefreiheit), die nicht für Konformitätsstufe B erforderlich ist. Unabhängig von der Konformitätsstufe bestimmt PDF/A-1, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind. Derzeit wird bei der Validierung (und Konvertierung) nur PDF/A-1b unterstützt.

Angenommen, für diese Diskussion wird das folgende DDX-Dokument verwendet.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
         <DocumentInformation source="Loan.pdf" result="Loan_result.xml">
         <PDFAValidation compliance="PDF/A-1b" resultLevel="Detailed"                       ignoreUnusedResources="true" allowCertificationSignatures="true" />
     </DocumentInformation>
 </DDX>
```

In diesem DDX-Dokument weist das Element `DocumentInformation` den Assembler-Dienst an, Informationen zum PDF-Eingabedokument zurückzugeben. Innerhalb des Elements `DocumentInformation` weist das Element `PDFAValidation` den Assembler-Dienst an, anzugeben, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

Der Assembler-Dienst gibt Informationen zurück, die angeben, ob das PDF-Eingabedokument in einem XML-Dokument, das ein `PDFAConformance` -Element enthält, PDF/A-kompatibel ist. Wenn das PDF-Eingabedokument PDF/A-kompatibel ist, lautet der Wert des `PDFAConformance`-Attributs `isCompliant` des Elements `true`. Wenn das PDF-Dokument nicht PDF/A-kompatibel ist, lautet der Wert des `PDFAConformance`-Attributs `isCompliant` des Elements `false`.

>[!NOTE]
>
>Da das in diesem Abschnitt angegebene DDX-Dokument ein `DocumentInformation`-Element enthält, gibt der Assembler-Dienst XML-Daten anstelle eines PDF-Dokuments zurück. Das heißt, der Assembler-Dienst assembliert oder zerlegt kein PDF-Dokument. Es werden Informationen zum PDF-Eingabedokument in einem XML-Dokument zurückgegeben.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um festzustellen, ob ein PDF-Dokument PDF/A-kompatibel ist, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
1. Legen Sie Laufzeitoptionen fest.
1. Rufen Sie Informationen zum PDF-Dokument ab.
1. Speichern Sie das zurückgegebene XML-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Es muss auf ein DDX-Dokument verwiesen werden, um einen Assembler-Dienstvorgang durchzuführen. Um festzustellen, ob ein PDF-Eingabedokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument das Element `PDFAValidation` innerhalb eines Elements `DocumentInformation` enthält. Das Element `PDFAValidation` weist den Assembler-Dienst an, ein XML-Dokument zurückzugeben, das angibt, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

**Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität**

Ein PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Abrufen von Informationen zum PDF-Dokument**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, auf das DDX-Dokument verweisen, auf ein interaktives PDF-Dokument verweisen und Laufzeitoptionen festgelegt haben, können Sie den Vorgang `invokeDDX` aufrufen. Da das DDX-Dokument das Element `DocumentInformation` enthält, gibt der Assembler-Dienst XML-Daten anstelle eines PDF-Dokuments zurück.

**Das zurückgegebene XML-Dokument speichern**

Das vom Assembler-Dienst zurückgegebene XML-Dokument gibt an, ob das PDF-Eingabedokument PDF/A-kompatibel ist. Wenn das PDF-Eingabedokument beispielsweise nicht PDF/A-kompatibel ist, gibt der Assembler-Dienst ein XML-Dokument zurück, das das folgende Element enthält:

```xml
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Speichern Sie das XML-Dokument als XML-Datei, damit Sie die Datei öffnen und die Ergebnisse anzeigen können.

**Siehe auch**

[Bestimmen, ob ein Dokument mit der Java-API PDF/A-kompatibel ist](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api)

[Bestimmen, ob ein Dokument mithilfe der Webdienst-API PDF/A-kompatibel ist](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Bestimmen Sie mithilfe der Java-API {#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api}, ob ein Dokument PDF/A-kompatibel ist.

Stellen Sie mithilfe der Assembler Service API (Java) fest, ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort der DDX-Datei angibt. Um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument das Element `PDFAValidation` enthält, das in einem Element `DocumentInformation` enthalten ist.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort eines PDF-Dokuments übergeben, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie dessen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben, das das PDF-Dokument enthält.
   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern des PDF-Eingabedokuments mithilfe eines `HashMap`-Konstruktors verwendet wird.
   * Fügen Sie einen Eintrag zum `java.util.Map`-Objekt hinzu, indem Sie dessen `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. Beispielsweise lautet der Wert des Quellelements im DDX-Dokument, das in diesem Abschnitt eingeführt wird, Loan.pdf.
      * Ein `com.adobe.idp.Document` -Objekt, das das PDF-Eingabedokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `setFailOnError` -Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Rufen Sie Informationen zum PDF-Dokument ab.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das zu verwendende DX-Dokument darstellt
   * Ein `java.util.Map` -Objekt, das die PDF-Eingabedatei enthält, mit der die PDF/A-Kompatibilität ermittelt wird
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist:

   * Rufen Sie die `getDocuments` -Methode des Objekts `AssemblerResult` auf. Dadurch wird ein `java.util.Map` -Objekt zurückgegeben.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf, um das XML-Dokument zu extrahieren. Stellen Sie sicher, dass Sie die XML-Daten als XML-Datei speichern.

**Siehe auch**

[Schnellstart (SOAP-Modus): Bestimmen, ob ein Dokument mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api)  (SOAP-Modus) PDF/A-kompatibel ist

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Bestimmen Sie mithilfe der Webdienst-API {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}, ob ein Dokument PDF/A-kompatibel ist.

Stellen Sie mithilfe der Assembler-Dienst-API (Webdienst) fest, ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Collection-Objekt wird zum Speichern des PDF-Dokuments verwendet.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Weisen Sie dem `key` -Feld des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, das das PDF-Dokument speichert, dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objektfeld `value` zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt zum `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Methode des Objekts `Add` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType` -Objekt.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec` -Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem `AssemblerOptionSpec`-Datenelement des `failOnError`-Objekts zu.

1. Rufen Sie Informationen zum PDF-Dokument ab.

   Rufen Sie die `invoke` -Methode des Objekts `AssemblerServiceService` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das DDX-Dokument darstellt.
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das das PDF-Eingabedokument enthält. Die Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und ihre Werte müssen das `BLOB`-Objekt sein, das der PDF-Eingabedatei entspricht.
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt.

   Die `invoke`-Methode gibt ein `AssemblerResult`-Objekt zurück, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist:

   * Greifen Sie auf das `AssemblerResult` -Feld des Objekts zu, bei dem es sich um ein `Map` -Objekt handelt, das die XML-Daten enthält, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.`documents`
   * Durchsuchen Sie das `Map`-Objekt, um jedes Zieldokument abzurufen. Dann den Wert des Array-Mitglieds in `BLOB` umwandeln.
   * Extrahieren Sie die Binärdaten, die die XML-Daten darstellen, indem Sie auf das `BLOB` -Objektfeld `MTOM` zugreifen. Dieses Feld speichert ein Array von Bytes, in die Sie als XML-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
