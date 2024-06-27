---
title: Ermitteln der PDF/A-Kompatibilität von Dokumenten
description: Verwenden Sie den Assembler-Service, um mithilfe der Java-API und der Web Service-API zu ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 096fd2ac-616f-484a-b093-9d98b2f87093
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '2065'
ht-degree: 100%

---

# Ermitteln der PDF/A-Kompatibilität von Dokumenten {#determining-whether-documents-are-pdf-a-compliant}

Mithilfe des Assembler-Services können Sie feststellen, ob ein PDF-Dokument PDF/A-kompatibel ist. Ein PDF/A-Dokument liegt als ein Archivierungsformat vor, das für die langfristige Speicherung von Dokumentinhalten vorgesehen ist. Die Schriftarten werden im Dokument eingebettet und die Datei bleibt unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte.

Die PDF/A-1-Spezifikation umfasst zwei Konformitätsstufen (Level), nämlich A und B. Der Hauptunterschied zwischen den beiden Stufen ist die Unterstützung der logischen Struktur (Barrierefreiheit), die für die Konformitätsstufe B nicht erforderlich ist. Unabhängig von der Konformitätsstufe schreibt PDF/A-1 vor, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind. Derzeit wird bei der Gültigkeitsprüfung (und Konvertierung) nur PDF/A-1b unterstützt.

Nehmen Sie für dieses Thema bitte an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
         <DocumentInformation source="Loan.pdf" result="Loan_result.xml">
         <PDFAValidation compliance="PDF/A-1b" resultLevel="Detailed"                       ignoreUnusedResources="true" allowCertificationSignatures="true" />
     </DocumentInformation>
 </DDX>
```

In diesem DDX-Dokument weist das Element `DocumentInformation` den Assembler-Dienst an, Informationen über das PDF-Eingabedokument zurückzugeben. Innerhalb des Elements `DocumentInformation` weist das Element `PDFAValidation` den Assembler-Service an anzugeben, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

Der Assembler-Service gibt Informationen zurück, die detailliert angeben, ob das PDF-Eingabedokument in einem XML-Dokument, das ein `PDFAConformance`-Element enthält, PDF/A-kompatibel ist. Wenn das PDF-Eingabedokument PDF/A-kompatibel ist, hat das Attribut `isCompliant` des `PDFAConformance`-Elements den Wert `true`. Wenn das PDF-Dokument nicht PDF/A-kompatibel ist, hat das Attribut `isCompliant` des `PDFAConformance`-Elements den Wert `false`.

>[!NOTE]
>
>Da das in diesem Abschnitt näher beschriebene DDX-Dokument ein `DocumentInformation`-Element enthält, gibt der Assembler-Service anstelle eines PDF-Dokuments XML-Daten zurück. Das heißt, durch den Assembler-Service erfolgt weder ein Zusammenfügen noch ein Aufteilen von PDF-Dokumenten. Es werden lediglich Informationen zu dem PDF-Eingabedokument in einem XML-Dokument zurückgegeben.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um festzustellen, ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein PDF-Dokument, das zum Bestimmen der PDF/A-Kompatibilität verwendet wird.
1. Legen Sie Laufzeitoptionen fest.
1. Rufen Sie Informationen zum PDF-Dokument ab.
1. Speichern Sie das zurückgegebene XML-Dokument.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt ist, der von JBoss verschieden ist, müssen Sie die Dateien „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die für den J2EE-Anwendungs-Server spezifisch sind, auf dem AEM Forms bereitgestellt ist. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines PDF-Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Referenzieren eines vorhandenen DDX-Dokuments**

Es muss auf ein DDX-Dokument verwiesen werden, um einen Assembler-Service-Vorgang auszuführen. Um festzustellen, ob ein PDF-Eingabedokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument das `PDFAValidation`-Element in einem `DocumentInformation`-Element enthält. Das `PDFAValidation`-Element weist den Assembler-Service an, ein XML-Dokument zurückzugeben, das angibt, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

**Referenzieren eines PDF-Dokuments zur Ermittlung der PDF/A-Kompatibilität**

Ein PDF-Dokument muss referenziert und an den Assembler-Service übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Services während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Service angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Informationen über die Laufzeitoptionen, die Sie festlegen können, finden Sie unter `AssemblerOptionSpec`-Klassenverweis in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Abrufen von Informationen über das PDF-Dokument**

Nachdem Sie den Assembler-Service-Client erstellt haben, auf das DDX-Dokument verwiesen haben, auf ein interaktives PDF-Dokument verwiesen haben und Laufzeitoptionen festgelegt haben, können Sie den `invokeDDX`-Vorgang aufrufen. Da das DDX-Dokument das `DocumentInformation`-Element enthält, gibt der Assembler-Service XML-Daten anstelle eines PDF-Dokuments zurück.

**Speichern des zurückgegebenen XML-Dokuments**

Das vom Assembler-Service zurückgegebene XML-Dokument gibt an, ob das PDF-Eingabedokument PDF/A-kompatibel ist. Wenn das PDF-Eingabedokument beispielsweise nicht PDF/A-kompatibel ist, gibt der Assembler-Service ein XML-Dokument zurück, das das folgende Element enthält:

```xml
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Speichern Sie das XML-Dokument als XML-Datei, damit Sie die Datei öffnen und die Ergebnisse anzeigen können.

**Siehe auch**

[Ermitteln Sie mithilfe der Java-API, ob ein Dokument PDF/A-kompatibel ist.](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api)

[Ermitteln Sie mithilfe der Web-Service-API, ob ein Dokument PDF/A-kompatibel ist.](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatisches Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Ermitteln Sie mithilfe der Java-API, ob ein Dokument PDF/A-kompatibel ist. {#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api}

So ermitteln Sie mithilfe der Assembler-Service-API (Java), ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergiben, der den Speicherort der DDX-Datei angibt. Um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist, stellen Sie sicher, dass das DDX-Dokument das `PDFAValidation`-Element enthält, das in einem `DocumentInformation`-Element enthalten ist.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Dokument, das zum Bestimmen der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort eines PDF-Dokuments übergeben, das zum Bestimmen der PDF/A-Kompatibilität verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben, das das PDF-Dokument enthält.
   * Erstellen Sie ein `java.util.Map`-Objekt, das mithilfe eines `HashMap`-Konstruktors zum Speichern des Eingabe-PDF-Dokuments verwendet wird.
   * Fügen Sie dem `java.util.Map`-Objekt durch Aufrufen seiner `put`-Methode und Übergeben der folgenden Argumente einen Eintrag hinzu:

      * Eine Zeichenfolge, die den Speichernamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. Beispielsweise lautet der Wert des Quellelements im DDX-Dokument, das in diesem Abschnitt eingeführt wird, „Loan.pdf“.
      * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Eingabedokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `setFailOnError`-Methode des `AssemblerOptionSpec`-Objekts auf und übergeben Sie `false`.

1. Rufen Sie Informationen zum PDF-Dokument ab.

   Rufen Sie die `invokeDDX`-Methode des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das die PDF-Eingabedatei enthält, mit der die PDF/A-Kompatibilität ermittelt wird.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Optionen für die Laufzeit angibt

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument PDF/A-kompatibel ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist:

   * Rufen Sie die `getDocuments`-Methode des `AssemblerResult`-Objekts auf. Dadurch wird ein `java.util.Map`-Objekt zurückgegeben.
   * Gehen Sie schrittweise durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `copyToFile`-Methode des `com.adobe.idp.Document`-Objekts auf, um das XML-Dokument zu extrahieren. Stellen Sie sicher, dass Sie die XML-Daten als XML-Datei speichern.

**Siehe auch**

[Schnellstart (SOAP-Modus): Mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api) (SOAP-Modus) bestimmen, ob ein Dokument PDF/A-kompatibel ist

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Ermitteln Sie mithilfe der Web-Service-API, ob ein Dokument PDF/A-kompatibel ist. {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}

Stellen Sie mithilfe der Assembler-Service-API (Webservice) fest, ob ein PDF-Dokument PDF/A-kompatibel ist:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert mit der WSDL an den AEM Forms-Service (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `AssemblerServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein Objekt `System.IO.FileStream`, indem Sie den Konstruktor aufrufen und einen String-Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus, in dem die Datei geöffnet werden soll, repräsentiert.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Datenstromdaten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und ihr das Byte-Array, die Startposition und die zu lesende Datenstromlänge übergeben.
   * Befüllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` die Inhalte des Byte-Arrays zuweisen.

1. Referenzieren Sie ein PDF-Dokument, das zum Bestimmen der PDF/A-Kompatibilität verwendet wird.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Befüllen Sie das `BLOB`-Objekt, indem Sie seiner Eigenschaft `MTOM` die Inhalte des Byte-Arrays zuweisen.
   * Erstellen Sie ein Objekt `MyMapOf_xsd_string_To_xsd_anyType`. Dieses Collection-Objekt wird zum Speichern des PDF-Dokuments verwendet.
   * Erstellen Sie ein Objekt `MyMapOf_xsd_string_To_xsd_anyType_Item`.
   * Weisen Sie dem Feld `key` des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts einen String-Wert zu, der den Schlüsselnamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, in dem das PDF-Dokument gespeichert wird, dem `value`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die `Add`-Methode des `MyMapOf_xsd_string_To_xsd_anyType`-Objekts auf und übergeben Sie das Objekt `MyMapOf_xsd_string_To_xsd_anyType`.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie dem `failOnError`-Daten-Member des `AssemblerOptionSpec`-Objekts `false` zu.

1. Rufen Sie Informationen zum PDF-Dokument ab.

   Rufen Sie die `invoke`-Methode des `AssemblerServiceService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das das PDF-Eingabedokument enthält. Die Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und ihre Werte müssen das `BLOB`-Objekt sein, das der PDF-Eingabedatei entspricht.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `invoke`-Methode gibt ein `AssemblerResult`-Objekt zurück, das XML-Daten enthält, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.

1. Speichern Sie das zurückgegebene XML-Dokument.

   So rufen Sie XML-Daten ab, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist:

   * Greifen Sie auf das Feld `documents` des `AssemblerResult`-Objekts zu, wobei es sich um ein `Map`-Objekt handelt, das die XML-Daten enthält, die angeben, ob das PDF-Eingabedokument ein PDF/A-Dokument ist.
   * Führen Sie eine Iteration über das `Map`-Objekt aus, um jedes Zieldokument zu erhalten. Anschließend ändern Sie den Wert dieses Array-Elements in `BLOB`.
   * Extrahieren Sie die Binärdaten, die die XML-Daten darstellen, indem Sie auf das Feld `MTOM` des `BLOB`-Objekts zugreifen. Dieses Feld speichert ein Array von Bytes, das sich als XML-Datei ausgeben lässt.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
