---
title: Arbeiten mit PDF/A-Dokumenten
description: Verwenden Sie den DocConverter-Service, um zu ermitteln, ob ein PDF-Dokument ein PDF/A-Dokument ist, und um PDF-Dokumente in PDF/A-Dokumente zu konvertieren.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 966c3554-25df-4467-866e-11c43cc15b58
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '2331'
ht-degree: 100%

---

# Arbeiten mit PDF/A-Dokumenten {#working-with-pdf-a-documents}

**Über den DocConverter-Service**

Der DocConverter-Service kann PDF-Dokumente in PDA/A-Dokumente konvertieren. Sie können mit diesem Service folgende Aufgaben ausführen:

* Konvertieren von PDF-Dokumenten in PDF/A-Dokumente. (Siehe [Konvertieren von Dokumenten in PDF/A-Dokumente](pdf-a-documents.md#converting-documents-to-pdf-a-documents).)
* Feststellen, ob PDF-Dokumente PDF/A-Dokumente sind. (Siehe [Programmatische Bestimmung der PDF/A-Konformität](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von Dokumenten in PDF/A-Dokumente {#converting-documents-to-pdf-a-documents}

Sie können den DocConverter-Service verwenden, um ein PDF-Dokument in ein PDF/A-Dokument zu konvertieren. Da PDF/A ein Archivierungsformat für die langfristige Beibehaltung des Dokumentinhalts ist, werden alle Schriftarten eingebettet und die Datei nicht komprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte. Bevor Sie ein PDF-Dokument in ein PDF/A-Dokument konvertieren, stellen Sie sicher, dass das PDF-Dokument kein PDF/A-Dokument ist.

Die PDF/A-1-Spezifikation besteht aus den Konformitätsstufen A und B. Der Hauptunterschied zwischen den beiden besteht in Bezug auf die Unterstützung der logischen Struktur (Barrierefreiheit), die für Konformitätsstufe B nicht erforderlich ist. Unabhängig von der Konformitätsstufe bestimmt PDF/A-1, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind. Derzeit wird bei der Gültigkeitsprüfung (und Konvertierung) nur PDF/A-1b unterstützt.

PDF/A ist zwar der Standard für die Archivierung von PDF-Dokumenten, es ist jedoch nicht erforderlich, dass PDF/A zur Archivierung verwendet wird, wenn ein standardmäßiges PDF-Dokument den Anforderungen Ihrer Firma entspricht. Der PDF/A-Standard dient der Erstellung einer PDF-Datei, die für die langfristige Archivierung und Dokumentenerhaltung bestimmt ist.

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Scjritte aus, um ein PDF-Dokument in ein PDF/A-Dokument zu konvertieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen eines DocConvert-Clients
1. Referenzieren Sie das PDF-Dokument, welches in ein PDF/A-Dokument konvertiert werden soll.
1. Legen Sie die Tracking-Informationen fest.
1. Konvertieren Sie das Dokument.
1. Speichern Sie das PDF/A-Dokument.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Weitere Informationen über den Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DocConvert-Clients**

Bevor Sie einen DocConverter-Vorgang programmgesteuert ausführen können, müssen Sie einen DocConverter-Client erstellen. Erstellen Sie ein `DocConverterServiceClient`-Objekt, wenn Sie die Java-API verwenden. Wenn Sie die DocConverter-Webservice-API verwenden, erstellen Sie ein `DocConverterServiceService`-Objekt.

**Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument**

Rufen Sie das PDF-Dokument ab, welches in ein PDF/A-Dokument konvertiert werden soll. Wenn Sie versuchen, ein PDF-Dokument, z. B. ein Acrobat-Formular, in ein PDF/A-Dokument zu konvertieren, wird eine Ausnahme ausgelöst.

**Festlegen von Tracking-Informationen**

Sie können eine Laufzeitoption festlegen, die bestimmt, wie viele Informationen während des Konvertierungsprozesses nachverfolgt werden. Das heißt, Sie können neun verschiedene Ebenen festlegen, die angeben, wie viele Informationen der DocConverter-Service nachverfolgt, wenn ein PDF-Dokument in ein PDF/A-Dokument konvertiert wird.

**Konvertieren des Dokuments**

Nachdem Sie den DocConverter-Service-Client erstellt haben, referenzieren Sie das zu konvertierende PDF-Dokument und legen die Laufzeitoption fest, die angibt, wie viele Informationen nachverfolgt werden. Dann konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument.

**Speichern des PDF/A-Dokuments**

Sie können das PDF/A-Dokument als PDF-Datei speichern.

**Siehe auch**

[Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Java-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-java-api)

[Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Webservice-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatische Bestimmung der PDF/A-Konformität](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy)

### Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Java-API {#convert-documents-to-pdf-a-documents-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Java-API in ein PDF/A-Dokument:

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocConverterServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Tracking-Informationen

   * Erstellen Sie ein Objekt `PDFAConversionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Tracking-Ebene für Informationen fest, indem Sie die Methode `setLogLevel` des `PDFAConversionOptionSpec`-Objekt verwenden und einen Zeichenfolgenwert übergeben, der die Tracking-Ebene angibt. Beispielsweise können Sie den Wert `FINE` übergeben. Weitere Informationen zu den verschiedenen Werten finden Sie unter der Beschreibung der `setLogLevel`-Methode in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Dokument konvertieren

   Konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument, indem Sie die `toPDFA`-Methode des `DocConverterServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, in dem das zu konvertierende PDF-Dokument enthalten ist
   * Das `PDFAConversionOptionSpec`-Objekt, in dem Tracking-Daten enthalten sind

   Die `toPDFA`-Methode gibt ein `PDFAConversionResult`-Objekt zurück, in dem das PDF/A-Dokument enthalten ist.

1. PDF/A-Dokument speichern

   * Rufen Sie das PDF/A-Dokument ab, indem Sie die `getPDFA`-Methode des `PDFAConversionResult`-Objekts aufrufen. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, welches das PDF/A-Dokument darstellt.
   * Erstellen Sie ein `java.io.File`-Objekt, das die PDF/A-Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Füllen Sie die Datei mit PDF/A-Daten, indem Sie die `copyToFile`-Methode des `com.adobe.idp.Document`-Objekts aufrunfen und das `java.io.File`-Objekt übergeben.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Kurzanleitung (SOAP-Modus): Konvertieren eines Dokuments in ein PDF/A-Dokument mithilfe der Java-API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von Dokumenten in PDF/A-Dokumente mithilfe der Webservice-API {#convert-documents-to-pdf-a-documents-using-the-web-service-api}

Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument anhand der DocConverter-API (Webervice):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die DocConverter-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie mit Hilfe der Microsoft .NET-Client-Assembly ein `DocConverterServiceService`-Objekt, indem Sie dessen Standardkonstruktor aufrufen.
   * Setzen Sie das `Credentials`Datenelement des `DocConverterServiceService`-Elements auf einen `System.Net.NetworkCredential`-Wert, der den Benutzernamen und das Passwort enthät.

1. Referenzieren eines PDF-Dokuments zur Konvertierung in ein PDF/A-Dokument

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das in ein PDF/A-Dokument konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie die Inhalte des Byte-Arrays seiner `binaryData`-Eigenschaft zuweisen.

1. Festlegen von Tracking-Informationen

   * Erstellen Sie ein Objekt `PDFAConversionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Ebene der Informationsnachverfolgung fest, indem Sie dem `logLevel`-Datenelement des `PDFAConversionOptionSpec`-Objekts einen Wert zuweisen, welcher der Ebene der Nachverfolgung entspricht. Weisen Sie diesem Datenelement beispielsweise den Wert `FINE`.

1. Dokument konvertieren

   Konvertieren Sie das PDF-Dokument in ein PDF/A-Dokument, indem Sie die `toPDFA`-Methode des `DocConverterServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, in dem das zu konvertierende PDF-Dokument enthalten ist
   * Das `PDFAConversionOptionSpec`-Objekt, in dem Tracking-Daten enthalten sind

   Die `toPDFA`-Methode gibt ein `PDFAConversionResult`-Objekt zurück, in dem das PDF/A-Dokument enthalten ist.

1. PDF/A-Dokument speichern

   * Erstellen Sie ein `BLOB`-Objekt, in dem das PDF/A-Dokument gespeichert wird, indem Sie den Wert des `PDFADocument`-Datenelements des `PDFAConversionResult`-Objekts abrufen.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `BLOB`-Objekts gespeichert wird, das bei der Anwendung des `PDFAConversionResult`-Objekts zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `binaryData`-Datenelements des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF/A-Dokuments angibt.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Programmatische Bestimmung der PDF/A-Konformität {#programmatically-determining-pdf-a-compliancy}

Mit dem DocConverter-Service können Sie ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist. Informationen zu PDF/A-Dokumenten und zum Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument finden Sie unter [Konvertieren von Dokumenten in PDF/A-Dokumente](pdf-a-documents.md#converting-documents-to-pdf-a-documents).

>[!NOTE]
>
>Weitere Informationen zum DocConverter-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um die Kompatibilität mit dem PDF/A-Format zu ermitteln, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen eines DocConvert-Clients
1. Referenzieren Sie ein PDF-Dokument, das zum Bestimmen der PDF/A-Kompatibilität verwendet wird.
1. Legen Sie Laufzeitoptionen fest.
1. Rufen Sie Informationen zum PDF-Dokument ab.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

Weitere Informationen über den Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DocConvert-Clients**

Bevor Sie einen DocConverter-Vorgang programmgesteuert ausführen können, müssen Sie einen DocConverter-Client erstellen. Erstellen Sie ein `DocConverterServiceClient`-Objekt, wenn Sie die Java-API verwenden. Wenn Sie die Web-Service-API für DocConverter verwenden, erstellen Sie ein `DocConverterServiceService`-Objekt.

**Referenzieren eines PDF-Dokuments zur Bestimmung der PDF/A-Konformität**

Ein PDF-Dokument muss referenziert und an den DocConverter-Service übergeben werden, um festzustellen, ob das PDF-Dokument PDF/A-kompatibel ist.

**Festlegen von Laufzeitoptionen**

Sie können eine Laufzeitoption festlegen, die bestimmt, wie viele Informationen während des Konvertierungsprozesses nachverfolgt werden. Das heißt, Sie können neun verschiedene Stufen festlegen, die angeben, wie viele Informationen der DocConverter-Service beim Konvertieren eines PDF-Dokuments in ein PDF/A-Dokument nachverfolgt.

**Abrufen von Informationen zum PDF-Dokument**

Nachdem Sie den Client für den DocConverter-Service erstellt, das PDF-Dokument referenziert und die Laufzeitoptionen eingestellt haben, können Sie ermitteln, ob das PDF-Dokument ein PDF/A-konformes Dokument ist.

**Siehe auch**

[Ermitteln der PDF/A-Konformität mithilfe der Java-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[Ermitteln der PDF/A-Konformität mithilfe der Web-Service-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ermitteln der PDF/A-Konformität mithilfe der Java-API {#determine-pdf-a-compliancy-using-the-java-api}

Bestimmen Sie mithilfe der Java-API die Konformität mit PDF/A:

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocConverterServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Dokuments zur Ermittlung der PDF/A-Konformität

   * Erstellen Sie mithilfe des Konstruktors ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument darstellt und übergeben Sie einen Zeichenfolgenwert, der den Speicherort der PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFAValidationOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Konformitätsstufe fest, indem Sie die Methode `setCompliance` des `PDFAValidationOptionSpec`-Objekts aufrufen und `PDFAValidationOptionSpec.Compliance.PDFA_1B` übergeben.
   * Legen Sie die Tracking-Stufe für Informationen fest, indem Sie die Methode `setLogLevel` des `PDFAValidationOptionSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der die Tracking-Stufe angibt. Beispielsweise können Sie den Wert `FINE` übergeben. Weitere Informationen zu den verschiedenen Werten finden Sie unter „Methode `setLogLevel`“ in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Abrufen von Informationen zum PDF-Dokument

   Ermitteln Sie die PDF/A-Konformität, indem Sie die Methode `DocConverterServiceClient` des Objekts `isPDFA` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält.
   * Das `PDFAValidationOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die Methode `isPDFA` gibt ein `PDFAValidationResult`-Objekt zurück, das die Ergebnisse dieses Vorgangs enthält.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Kurzanleitung (SOAP-Modus): Bestimmen der PDF/A-Kompatibilität mithilfe der Java-API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ermitteln der PDF/A-Konformität mithilfe der Web-Service-API {#determine-pdf-a-compliancy-using-the-web-service-api}

Ermitteln der PDF/A-Konformität mithilfe der Web-Service-API:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die DocConverter-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen eines DocConvert-Clients

   * Erstellen Sie mit Hilfe der Microsoft .NET-Client-Assembly ein `DocConverterServiceService`-Objekt, indem Sie dessen Standardkonstruktor aufrufen.
   * Setzen Sie das Datenelement `DocConverterServiceService` des `Credentials`-Objekts auf einen `System.Net.NetworkCredential`-Wert, der den Benutzernamen und den Passwortwert angibt.

1. Referenzieren eines PDF-Dokuments zur Ermittlung der PDF/A-Konformität

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das in ein PDF/A-Dokument konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `binaryData`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFAValidationOptionSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Konformitätsstufe fest, indem Sie dem Datenelement `compliance` des `PDFAValidationOptionSpec`-Objekts den Wert `PDFAConversionOptionSpec_Compliance.PDFA_1B` zuweisen.
   * Legen Sie die Tracking-Stufe für Informationen fest, indem Sie dem Datenelement `resultLevel` des `PDFAValidationOptionSpec`-Objekts den Wert `PDFAValidationOptionSpec_ResultLevel.DETAILED` zuweisen.

1. Abrufen von Informationen zum PDF-Dokument

   Ermitteln Sie die PDF/A-Konformität, indem Sie die Methode `DocConverterServiceService` des Objekts `isPDFA` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Dokument enthält.
   * Das `PDFAValidationOptionSpec`-Objekt, das Laufzeitoptionen enthält.

   Die Methode `isPDFA` gibt ein `PDFAValidationResult`-Objekt zurück, das die Ergebnisse dieses Vorgangs enthält.

**Siehe auch**

[Arbeiten mit PDF/A-Dokumenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
