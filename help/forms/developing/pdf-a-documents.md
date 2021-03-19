---
title: Arbeiten mit PDF/A-Dokumenten
seo-title: Arbeiten mit PDF/A-Dokumenten
description: Mit dem DocConverter-Dienst können Sie ermitteln, ob ein PDF-Dokument ein PDF/A-Dokument ist, und PDF-Dokumente in PDF/A-Dokumente konvertieren.
seo-description: Mit dem DocConverter-Dienst können Sie ermitteln, ob ein PDF-Dokument ein PDF/A-Dokument ist, und PDF-Dokumente in PDF/A-Dokumente konvertieren.
uuid: c258d253-068a-4412-955a-21d8a4792d6f
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 1e6cc554-aef1-463c-906b-634b80a27917
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2387'
ht-degree: 7%

---


# Arbeiten mit PDF/A-Dokumenten {#working-with-pdf-a-documents}

**Informationen zum DocConverter-Dienst**

Der DocConverter-Dienst kann PDF-Dokumente in PDA/A-Dokumente konvertieren. Sie können diese Aufgaben mit diesem Dienst ausführen:

* Konvertieren von PDF-Dokumenten in PDF/A-Dokumente (Siehe [Konvertieren von Dokumenten in PDF/A-Dokumente](pdf-a-documents.md#converting-documents-to-pdf-a-documents).)
* Stellen Sie fest, ob PDF-Dokumente PDF/A-Dokumente sind. (Siehe [Programmatische Bestimmung der PDF/A-Kompatibilität](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von Dokumenten in PDF/A-Dokumente {#converting-documents-to-pdf-a-documents}

Mit dem DocConverter-Dienst können Sie ein PDF-Dokument in ein PDF/A-Dokument konvertieren. Da PDF/A ein Archivierungsformat für die langfristige Speicherung des Dokuments ist, werden alle Schriftarten eingebettet und die Datei nicht komprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte. Bevor Sie ein PDF-Dokument in ein PDF/A-Dokument konvertieren, stellen Sie sicher, dass das PDF-Dokument kein PDF/A-Dokument ist.

Die PDF/A-1-Spezifikation besteht aus zwei Stufen der Konformität, nämlich A und B. Der Hauptunterschied zwischen den beiden besteht in der Unterstützung der logischen Struktur (Zugänglichkeit), die für die Konformitätsstufe B nicht erforderlich ist. Unabhängig von der Konformitätsstufe schreibt PDF/A-1 vor, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind. Derzeit wird nur PDF/A-1b bei der Überprüfung (und Konvertierung) unterstützt.

PDF/A ist zwar der Standard für die Archivierung von PDF-Dokumenten, es ist jedoch nicht erforderlich, dass PDF/A für die Archivierung verwendet wird, wenn ein Standard-PDF-Dokument die Anforderungen Ihrer Firma erfüllt. Der PDF/A-Standard dient dazu, eine PDF-Datei zu erstellen, die für langfristige Archivierungs- und Dokument-Schutzbedürfnisse gedacht ist.

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So konvertieren Sie ein PDF-Dokument in ein PDF/A-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen eines DocConvert-Clients
1. Verweisen Sie auf ein PDF-Dokument, das in ein PDF/A-Dokument konvertiert werden soll.
1. Legen Sie Verfolgungsinformationen fest.
1. Konvertieren Sie das Dokument.
1. Speichern Sie das PDF/A-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DocConvert-Clients**

Bevor Sie einen DocConverter-Vorgang programmgesteuert ausführen können, müssen Sie einen DocConverter-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocConverterServiceClient`-Objekt. Wenn Sie die DocConverter-Webdienst-API verwenden, erstellen Sie ein `DocConverterServiceService`-Objekt.

**Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument**

Rufen Sie ein PDF-Dokument ab, das in ein PDF/A-Dokument konvertiert werden soll. Wenn Sie versuchen, ein PDF-Dokument, z. B. ein Acrobat-Formular, in ein PDF/A-Dokument zu konvertieren, wird eine Ausnahme ausgelöst.

**Festlegen von Verfolgungsinformationen**

Sie können eine Laufzeitoption festlegen, die bestimmt, wie viele Informationen während des Konvertierungsprozesses verfolgt werden. Das heißt, Sie können neun verschiedene Ebenen festlegen, die angeben, wie viele Informationen der DocConverter-Dienst verfolgt, wenn ein PDF-Dokument in ein PDF/A-Dokument konvertiert wird.

**Dokument konvertieren**

Nachdem Sie den DocConverter-Dienstclient erstellt haben, verweisen Sie auf das zu konvertierende PDF-Dokument und legen Sie die Laufzeitoption fest, die angibt, wie viele Informationen verfolgt werden, und Sie können das PDF-Dokument in ein PDF/A-Dokument konvertieren.

**PDF/A-Dokument speichern**

Sie können das PDF/A-Dokument als PDF-Datei speichern.

**Siehe auch**

[Konvertieren von Dokumenten in PDF/A-Dokumente mit der Java-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-java-api)

[Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Webdienst-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Bestimmen der PDF/A-Kompatibilität](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy)

### Konvertieren von Dokumenten in PDF/A-Dokumente mit der Java-API {#convert-documents-to-pdf-a-documents-using-the-java-api}

Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument mithilfe der Java-API:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-docconverter-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocConverterServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Verfolgungsinformationen

   * Erstellen Sie ein Objekt `PDFAConversionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Informationsverfolgungsebene fest, indem Sie die `PDFAConversionOptionSpec`-Methode des Objekts `setLogLevel` aufrufen und einen Zeichenfolgenwert übergeben, der die Verfolgungsstufe angibt. Geben Sie beispielsweise den Wert `FINE` an. Informationen zu den verschiedenen Werten finden Sie in der `setLogLevel`-Methode in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Dokument konvertieren

   Konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument, indem Sie die `toPDFA`-Methode des `DocConverterServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das zu konvertierende PDF-Dokument enthält
   * Das `PDFAConversionOptionSpec`-Objekt, das Verfolgungsinformationen angibt

   Die `toPDFA`-Methode gibt ein `PDFAConversionResult`-Objekt zurück, das das PDF/A-Dokument enthält.

1. PDF/A-Dokument speichern

   * Rufen Sie das PDF/A-Dokument ab, indem Sie die `PDFAConversionResult`-Objektmethode `getPDFA` aufrufen. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das PDF/A-Dokument darstellt.
   * Erstellen Sie ein `java.io.File`-Objekt, das die PDF/A-Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Füllen Sie die Datei mit PDF/A-Daten, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `copyToFile` aufrufen und das `java.io.File`-Objekt übergeben.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Quick Beginn (SOAP-Modus): Konvertieren eines Dokuments in ein PDF/A-Dokument mit der Java-API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Webdienst-API {#convert-documents-to-pdf-a-documents-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der DocConverter-API (Webdienst) in ein PDF/A-Dokument:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die DocConverter-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie mit der Microsoft .NET-Clientassembly ein `DocConverterServiceService`-Objekt, indem Sie dessen Standardkonstruktor aufrufen.
   * Legen Sie den Datenmember des Objekts `Credentials` mit dem Wert `System.Net.NetworkCredential` fest, der den Benutzernamen und den Kennwortwert angibt.`DocConverterServiceService`

1. Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das in ein PDF/A-Dokument konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `binaryData`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Verfolgungsinformationen

   * Erstellen Sie ein Objekt `PDFAConversionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Informationsverfolgungsebene fest, indem Sie dem `logLevel`-Datenmember des Objekts `PDFAConversionOptionSpec` einen Wert zuweisen, der die Verfolgungsstufe angibt. Weisen Sie diesem Datenmember beispielsweise den Wert `FINE` zu.

1. Dokument konvertieren

   Konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument, indem Sie die `toPDFA`-Methode des `DocConverterServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das zu konvertierende PDF-Dokument enthält
   * Das `PDFAConversionOptionSpec`-Objekt, das Verfolgungsinformationen angibt

   Die `toPDFA`-Methode gibt ein `PDFAConversionResult`-Objekt zurück, das das PDF/A-Dokument enthält.

1. PDF/A-Dokument speichern

   * Erstellen Sie ein `BLOB`-Objekt, das das PDF/A-Dokument speichert, indem Sie den Wert des `PDFAConversionResult`-Datenelements des `PDFADocument`-Objekts abrufen.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB`-Objekts speichert, das mit dem `PDFAConversionResult`-Objekt zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF/A-Dokuments darstellt.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Programmatische Bestimmung der PDF/A-Kompatibilität {#programmatically-determining-pdf-a-compliancy}

Mit dem DocConverter-Dienst können Sie ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist. Informationen zu einem PDF/A-Dokument und zum Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument finden Sie unter [Konvertieren von Dokumenten in PDF/A-Dokumente](pdf-a-documents.md#converting-documents-to-pdf-a-documents).

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So bestimmen Sie die PDF/A-Kompatibilität:

1. Schließen Sie Projektdateien ein.
1. Erstellen eines DocConvert-Clients
1. Verweisen Sie auf ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
1. Legen Sie Laufzeitoptionen fest.
1. Abrufen von Informationen zum PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DocConvert-Clients**

Bevor Sie einen DocConverter-Vorgang programmgesteuert ausführen können, müssen Sie einen DocConverter-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocConverterServiceClient`-Objekt. Wenn Sie die DocConverter-Webdienst-API verwenden, erstellen Sie ein `DocConverterServiceService`-Objekt.

**Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität**

Ein PDF-Dokument muss referenziert und an den DocConverter-Dienst übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Festlegen von Laufzeitoptionen**

Sie können eine Laufzeitoption festlegen, die bestimmt, wie viele Informationen während des Konvertierungsprozesses verfolgt werden. Das heißt, Sie können neun verschiedene Ebenen festlegen, die angeben, wie viele Informationen der DocConverter-Dienst verfolgt, wenn ein PDF-Dokument in ein PDF/A-Dokument konvertiert wird.

**Abrufen von Informationen zum PDF-Dokument**

Nachdem Sie den DocConverter-Dienstclient erstellt, auf das PDF-Dokument verwiesen und die Laufzeitoptionen festgelegt haben, können Sie festlegen, ob das PDF-Dokument ein PDF/A-kompatibles Dokument ist.

**Siehe auch**

[Bestimmen der PDF/A-Kompatibilität mithilfe der Java-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[Bestimmen der PDF/A-Kompatibilität mithilfe der Webdienst-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF/A-Kompatibilität mithilfe der Java-API {#determine-pdf-a-compliancy-using-the-java-api} ermitteln

Bestimmen der PDF/A-Kompatibilität mithilfe der Java-API:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-docconverter-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocConverterServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFAValidationOptionSpec`, indem Sie den Konstruktor verwenden.
   * Stellen Sie die Compliance-Stufe ein, indem Sie die `PDFAValidationOptionSpec`-Methode des Objekts `setCompliance` aufrufen und `PDFAValidationOptionSpec.Compliance.PDFA_1B` übergeben.
   * Legen Sie die Informationsverfolgungsebene fest, indem Sie die `PDFAValidationOptionSpec`-Methode des Objekts `setLogLevel` aufrufen und einen Zeichenfolgenwert übergeben, der die Verfolgungsstufe angibt. Geben Sie beispielsweise den Wert `FINE` an. Informationen zu den verschiedenen Werten finden Sie in der `setLogLevel`-Methode in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Abrufen von Informationen zum PDF-Dokument

   Bestimmen Sie die PDF/A-Kompatibilität, indem Sie die `DocConverterServiceClient`-Methode des Objekts `isPDFA` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält.
   * Das `PDFAValidationOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `isPDFA`-Methode gibt ein `PDFAValidationResult`-Objekt zurück, das die Ergebnisse dieses Vorgangs enthält.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Quick Beginn (SOAP-Modus): Bestimmen der PDF/A-Kompatibilität mithilfe der Java-API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bestimmen der PDF/A-Kompatibilität mithilfe der Webdienst-API {#determine-pdf-a-compliancy-using-the-web-service-api}

Bestimmen der PDF/A-Kompatibilität mithilfe der Webdienst-API:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die DocConverter-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie mit der Microsoft .NET-Clientassembly ein `DocConverterServiceService`-Objekt, indem Sie dessen Standardkonstruktor aufrufen.
   * Legen Sie den Datenmember des Objekts `Credentials` mit dem Wert `System.Net.NetworkCredential` fest, der den Benutzernamen und den Kennwortwert angibt.`DocConverterServiceService`

1. Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das in ein PDF/A-Dokument konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `binaryData`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFAValidationOptionSpec`, indem Sie den Konstruktor verwenden.
   * Stellen Sie die Compliance-Stufe ein, indem Sie dem `PDFAValidationOptionSpec`-Objekt das `compliance`-Datenelement mit dem Wert `PDFAConversionOptionSpec_Compliance.PDFA_1B` zuweisen.
   * Legen Sie die Informationsverfolgungsebene fest, indem Sie dem `PDFAValidationOptionSpec`-Objekt das `resultLevel`-Datenelement mit dem Wert `PDFAValidationOptionSpec_ResultLevel.DETAILED` zuweisen.

1. Abrufen von Informationen zum PDF-Dokument

   Bestimmen Sie die PDF/A-Kompatibilität, indem Sie die `DocConverterServiceService`-Methode des Objekts `isPDFA` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Dokument enthält.
   * Das `PDFAValidationOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die `isPDFA`-Methode gibt ein `PDFAValidationResult`-Objekt zurück, das die Ergebnisse dieses Vorgangs enthält.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
