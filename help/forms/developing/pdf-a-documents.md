---
title: Arbeiten mit PDF/A-Dokumenten
seo-title: Arbeiten mit PDF/A-Dokumenten
description: Verwenden Sie den DocConverter-Dienst, um zu ermitteln, ob ein PDF-Dokument ein PDF/A-Dokument ist, und um PDF-Dokumente in PDF/A-Dokumente zu konvertieren.
seo-description: Verwenden Sie den DocConverter-Dienst, um zu ermitteln, ob ein PDF-Dokument ein PDF/A-Dokument ist, und um PDF-Dokumente in PDF/A-Dokumente zu konvertieren.
uuid: c258d253-068a-4412-955a-21d8a4792d6f
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 1e6cc554-aef1-463c-906b-634b80a27917
role: Developer
exl-id: 966c3554-25df-4467-866e-11c43cc15b58
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2386'
ht-degree: 7%

---

# Arbeiten mit PDF/A-Dokumenten {#working-with-pdf-a-documents}

**Über den DocConverter-Dienst**

Der DocConverter-Dienst kann PDF-Dokumente in PDF/A-Dokumente konvertieren. Sie können diese Aufgaben mit diesem Dienst ausführen:

* Konvertieren von PDF-Dokumenten in PDF/A-Dokumente. (Siehe [Konvertieren von Dokumenten in PDF/A-Dokumente](pdf-a-documents.md#converting-documents-to-pdf-a-documents).)
* Bestimmen Sie, ob PDF-Dokumente PDF/A-Dokumente sind. (Siehe [Programmatische Bestimmung der PDF/A-Kompatibilität](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von Dokumenten in PDF/A-Dokumente {#converting-documents-to-pdf-a-documents}

Sie können den DocConverter-Dienst verwenden, um ein PDF-Dokument in ein PDF/A-Dokument zu konvertieren. Da PDF/A ein Archivierungsformat für die langfristige Beibehaltung des Dokumentinhalts ist, werden alle Schriftarten eingebettet und die Datei unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte. Bevor Sie ein PDF-Dokument in ein PDF/A-Dokument konvertieren, stellen Sie sicher, dass das PDF-Dokument kein PDF/A-Dokument ist.

Die PDF/A-1-Spezifikation besteht aus zwei Konformitätsstufen, nämlich A und B. Der Hauptunterschied zwischen den beiden besteht in der Unterstützung der logischen Struktur (Barrierefreiheit), die nicht für Konformitätsstufe B erforderlich ist. Unabhängig von der Konformitätsstufe bestimmt PDF/A-1, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind. Derzeit wird bei der Validierung (und Konvertierung) nur PDF/A-1b unterstützt.

Während PDF/A der Standard für die Archivierung von PDF-Dokumenten ist, ist es nicht erforderlich, PDF/A zur Archivierung zu verwenden, wenn ein standardmäßiges PDF-Dokument die Anforderungen Ihres Unternehmens erfüllt. Der PDF/A-Standard dient der Erstellung einer PDF-Datei, die für die langfristige Archivierung und Dokumentenerhaltung gedacht ist.

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So konvertieren Sie ein PDF-Dokument in ein PDF/A-Dokument:

1. Projektdateien einschließen.
1. Erstellen eines DocConvert-Clients
1. Referenzieren Sie ein PDF-Dokument, das in ein PDF/A-Dokument konvertiert werden soll.
1. Festlegen von Tracking-Informationen.
1. Konvertieren Sie das Dokument.
1. Speichern Sie das PDF/A-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DocConvert-Clients**

Bevor Sie einen DocConverter-Vorgang programmgesteuert ausführen können, müssen Sie einen DocConverter-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocConverterServiceClient` -Objekt. Wenn Sie die DocConverter-Webdienst-API verwenden, erstellen Sie ein `DocConverterServiceService` -Objekt.

**Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument**

Rufen Sie ein PDF-Dokument ab, das in ein PDF/A-Dokument konvertiert werden soll. Wenn Sie versuchen, ein PDF-Dokument, z. B. ein Acrobat-Formular, in ein PDF/A-Dokument zu konvertieren, wird eine Ausnahme verursacht.

**Tracking-Informationen festlegen**

Sie können eine Laufzeitoption festlegen, die bestimmt, wie viele Informationen während des Konvertierungsprozesses verfolgt werden. Das heißt, Sie können neun verschiedene Ebenen festlegen, die angeben, wie viele Informationen der DocConverter-Dienst beim Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument verfolgt.

**Dokument konvertieren**

Nachdem Sie den DocConverter-Dienst-Client erstellt haben, referenzieren Sie das zu konvertierende PDF-Dokument und legen Sie die Laufzeitoption fest, die angibt, wie viele Informationen verfolgt werden, und konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument.

**PDF/A-Dokument speichern**

Sie können das PDF/A-Dokument als PDF-Datei speichern.

**Siehe auch**

[Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Java-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-java-api)

[Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Webdienst-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuerte Bestimmung der PDF/A-Kompatibilität](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy)

### Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Java-API {#convert-documents-to-pdf-a-documents-using-the-java-api}

Konvertieren eines PDF-Dokuments mithilfe der Java-API in ein PDF/A-Dokument:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-docConverter-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocConverterServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument mithilfe des zugehörigen Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Tracking-Informationen festlegen

   * Erstellen Sie ein Objekt `PDFAConversionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie die `setLogLevel` -Methode des Objekts `PDFAConversionOptionSpec` aufrufen und einen Zeichenfolgenwert übergeben, der die Tracking-Ebene angibt. Übergeben Sie beispielsweise den Wert `FINE`. Informationen zu den verschiedenen Werten finden Sie in der `setLogLevel`-Methode in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Dokument konvertieren

   Konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument, indem Sie die `toPDFA` -Methode des Objekts `DocConverterServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das zu konvertierende PDF-Dokument enthält
   * Das `PDFAConversionOptionSpec`-Objekt, das Tracking-Informationen angibt

   Die `toPDFA`-Methode gibt ein `PDFAConversionResult`-Objekt zurück, das das PDF/A-Dokument enthält.

1. PDF/A-Dokument speichern

   * Rufen Sie das PDF/A-Dokument ab, indem Sie die `getPDFA` -Methode des Objekts `PDFAConversionResult` aufrufen. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das das PDF/A-Dokument darstellt.
   * Erstellen Sie ein `java.io.File`-Objekt, das die PDF/A-Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Füllen Sie die Datei mit PDF/A-Daten, indem Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` aufrufen und das `java.io.File` -Objekt übergeben.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Schnellstart (SOAP-Modus): Konvertieren eines Dokuments in ein PDF/A-Dokument mithilfe der Java-API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Webdienst-API {#convert-documents-to-pdf-a-documents-using-the-web-service-api}

Konvertieren eines PDF-Dokuments mithilfe der DocConverter-API (Webdienst) in ein PDF/A-Dokument:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die DocConverter-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie mit der Microsoft .NET-Clientassembly ein `DocConverterServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.
   * Legen Sie das `DocConverterServiceService`-Datenelement des `Credentials`-Objekts mit dem Wert `System.Net.NetworkCredential` fest, der den Benutzernamen und den Kennwortwert angibt.

1. Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das in ein PDF/A-Dokument konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `binaryData`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Tracking-Informationen festlegen

   * Erstellen Sie ein Objekt `PDFAConversionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie dem `logLevel` -Datenelement des Objekts `PDFAConversionOptionSpec` einen Wert zuweisen, der die Tracking-Ebene angibt. Weisen Sie diesem Datenelement beispielsweise den Wert `FINE` zu.

1. Dokument konvertieren

   Konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument, indem Sie die `toPDFA` -Methode des Objekts `DocConverterServiceService` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das zu konvertierende PDF-Dokument enthält
   * Das `PDFAConversionOptionSpec`-Objekt, das Tracking-Informationen angibt

   Die `toPDFA`-Methode gibt ein `PDFAConversionResult`-Objekt zurück, das das PDF/A-Dokument enthält.

1. PDF/A-Dokument speichern

   * Erstellen Sie ein `BLOB` -Objekt, das das PDF/A-Dokument speichert, indem Sie den Wert des `PDFAConversionResult` -Datenelements des `PDFADocument` -Objekts abrufen.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das mithilfe des `PDFAConversionResult` -Objekts zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF/A-Dokuments darstellt.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Programmgesteuerte Bestimmung der PDF/A-Kompatibilität {#programmatically-determining-pdf-a-compliancy}

Mit dem DocConverter-Dienst können Sie ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist. Informationen zu PDF/A-Dokumenten und zum Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument finden Sie unter [Konvertieren von Dokumenten in PDF/A-Dokumente](pdf-a-documents.md#converting-documents-to-pdf-a-documents).

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um die PDF/A-Kompatibilität zu ermitteln, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen eines DocConvert-Clients
1. Referenzieren Sie ein PDF-Dokument, das zur Bestimmung der PDF/A-Kompatibilität verwendet wird.
1. Legen Sie Laufzeitoptionen fest.
1. Rufen Sie Informationen zum PDF-Dokument ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DocConvert-Clients**

Bevor Sie einen DocConverter-Vorgang programmgesteuert ausführen können, müssen Sie einen DocConverter-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocConverterServiceClient` -Objekt. Wenn Sie die DocConverter-Webdienst-API verwenden, erstellen Sie ein `DocConverterServiceService` -Objekt.

**Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität**

Ein PDF-Dokument muss referenziert und an den DocConverter-Dienst übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Laufzeitoptionen festlegen**

Sie können eine Laufzeitoption festlegen, die bestimmt, wie viele Informationen während des Konvertierungsprozesses verfolgt werden. Das heißt, Sie können neun verschiedene Ebenen festlegen, die angeben, wie viele Informationen der DocConverter-Dienst beim Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument verfolgt.

**Abrufen von Informationen zum PDF-Dokument**

Nachdem Sie den DocConverter-Dienstclient erstellt, auf das PDF-Dokument verwiesen und die Laufzeitoptionen festgelegt haben, können Sie ermitteln, ob das PDF-Dokument ein PDF/A-kompatibles Dokument ist.

**Siehe auch**

[Bestimmen der PDF/A-Kompatibilität mithilfe der Java-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[Bestimmen der PDF/A-Kompatibilität mithilfe der Webdienst-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bestimmen der PDF/A-Kompatibilität mithilfe der Java-API {#determine-pdf-a-compliancy-using-the-java-api}

Bestimmen Sie mithilfe der Java-API die PDF/A-Kompatibilität:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-docConverter-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocConverterServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument mithilfe des zugehörigen Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PDFAValidationOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Konformitätsstufe fest, indem Sie die `setCompliance` -Methode des Objekts `PDFAValidationOptionSpec` aufrufen und `PDFAValidationOptionSpec.Compliance.PDFA_1B` übergeben.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie die `setLogLevel` -Methode des Objekts `PDFAValidationOptionSpec` aufrufen und einen Zeichenfolgenwert übergeben, der die Tracking-Ebene angibt. Übergeben Sie beispielsweise den Wert `FINE`. Informationen zu den verschiedenen Werten finden Sie in der `setLogLevel`-Methode in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Abrufen von Informationen zum PDF-Dokument

   Bestimmen Sie die PDF/A-Kompatibilität, indem Sie die `isPDFA` -Methode des Objekts `DocConverterServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält.
   * Das `PDFAValidationOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `isPDFA`-Methode gibt ein `PDFAValidationResult`-Objekt zurück, das die Ergebnisse dieses Vorgangs enthält.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Schnellstart (SOAP-Modus): Bestimmen der PDF/A-Kompatibilität mithilfe der Java-API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bestimmen der PDF/A-Kompatibilität mithilfe der Webdienst-API {#determine-pdf-a-compliancy-using-the-web-service-api}

Bestimmen der PDF/A-Kompatibilität mithilfe der Webdienst-API:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die DocConverter-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie mit der Microsoft .NET-Clientassembly ein `DocConverterServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.
   * Legen Sie das `DocConverterServiceService`-Datenelement des `Credentials`-Objekts mit dem Wert `System.Net.NetworkCredential` fest, der den Benutzernamen und den Kennwortwert angibt.

1. Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Kompatibilität

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das in ein PDF/A-Dokument konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `binaryData`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PDFAValidationOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Konformitätsstufe fest, indem Sie dem `compliance`-Datenelement des `PDFAValidationOptionSpec`-Objekts den Wert `PDFAConversionOptionSpec_Compliance.PDFA_1B` zuweisen.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie dem `resultLevel`-Datenelement des `PDFAValidationOptionSpec_ResultLevel.DETAILED`-Objekts den Wert `PDFAValidationOptionSpec` zuweisen.

1. Abrufen von Informationen zum PDF-Dokument

   Bestimmen Sie die PDF/A-Kompatibilität, indem Sie die `isPDFA` -Methode des Objekts `DocConverterServiceService` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Dokument enthält.
   * Das `PDFAValidationOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die `isPDFA`-Methode gibt ein `PDFAValidationResult`-Objekt zurück, das die Ergebnisse dieses Vorgangs enthält.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
