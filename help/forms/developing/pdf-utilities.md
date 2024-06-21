---
title: Arbeiten mit PDF Utilities
description: Verwenden Sie den PDF Utilities-Service, um zwischen PDF- und XDP-Dateiformaten zu konvertieren, PDF-Dokumenteigenschaften zu definieren und abzurufen und XMP-Metadaten zu bearbeiten.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: e4b204ee-7261-42b8-8db8-a92aa9fd0a28
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '2549'
ht-degree: 100%

---

# Arbeiten mit PDF Utilities {#working-with-pdf-utilities}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den PDF Utilities-Service**

Der PDF Utilities-Service erlaubt das Konvertieren zwischen PDF- und XDP-Dateiformaten, das Definieren und Abrufen von PDF-Dokumenteigenschaften und das Bearbeiten von XMP-Metadaten. Bevor Sie beispielsweise ein PDF-Dokument in ein anderes Format konvertieren, kann es hilfreich sein, die Dokumenteigenschaften zu überprüfen, um zu entscheiden, welcher Vorgang des Services sich für die Konvertierung anbietet.

Sie können dies mithilfe des PDF Utilities-Services erreichen:

* Konvertieren von PDF-Dokumenten in XDP-Dokumente.
* Konvertieren von XDP-Dokumenten in PDF-Dokumente. (Siehe [Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents).)
* Abrufen von PDF-Dokumenteigenschaften. (Siehe [Abrufen von PDF-Dokumenteigenschaften](pdf-utilities.md#retrieving-pdf-document-properties).)
* Speichern Sie ein PDF-Dokument und optimieren Sie es für ein schnelleres Anzeigen über das Internet. (Siehe [Speichermodi für PDF-Dokumente einstellen](pdf-utilities.md#setting-pdf-document-save-modes).)

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PDF-Dokumenten in XDP-Dokumente {#converting-pdf-documents-into-xdp-documents}

Sie können die Java- und Web-Service-APIs von PDF Utilities verwenden, um PDF-Dokumente programmgesteuert in XDP-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um ein PDF-Dokument in ein XDP-Dokument zu konvertieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Konvertierungsvorgang von PDF nach XDP auf.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Sie können dies mit der Java-API erreichen, indem Sie ein `PDFUtilityServiceClient`-Objekt erstellen. Mit der Web-Service-API wird dies durch die Verwendung eines `PDFUtilityServiceService`-Objekts erreicht.

**Aufrufen des Konvertierungsvorgangs von PDF nach XDP**

Nachdem Sie den Service-Client erstellt haben, können Sie den Konvertierungsvorgang von PDF nach XDP aufrufen.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Web-Service-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API {#convert-pdf-documents-into-xdp-documents-using-the-java-api}

Konvertieren von PDF-Dokumenten in XDP-Dokumente anhand der PDF Utilities-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-pdfutility-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt unter Verwendung seines Konstruktors und übergeben Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.

1. Aufrufen des Konvertierungsvorgangs PDF in XDP

   Rufen Sie zum Ausführen der Konvertierung die `convertPDFtoXDP`-Methode des `PDFUtilityServiceClient`-Objekts auf und übergeben Sie in ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Web-Service-API {#convert-pdf-documents-into-xdp-documents-using-the-web-service-api}

Konvertieren von PDF-Dokumenten in XDP-Dokumente anhand der PDF Utilities-API (Web-Service):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Services verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceService`-Objekt anhand des Klassenkonstruktors der Proxy.

1. Aufrufen des Konvertierungsvorgangs PDF in XDP

   Rufen Sie die `convertPDFtoXDP`-Methode des `PDFUtilityServiceService`-Objekts auf und übergeben Sie eine `BLOB`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `BLOB`-Objekt zurück, das die soeben erstellte XDP-Datei darstellt.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Konvertieren von XDP-Dokumenten in PDF-Dokumente {#converting-xdp-documents-into-pdf-documents}

Sie können die Java- und Web-Service-APIs von PDF Utilities verwenden, um XDP-Dokumente programmgesteuert in PDF-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Gehen Sie wie folgt vor, um ein XDP-Dokument in ein PDF-Dokument zu konvertieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Aufrufen des Konvertierungsvorgangs von XDP nach PDF.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Sie können dies mit der Java-API erreichen, indem Sie ein `PDFUtilityServiceClient`-Objekt erstellen. Falls Sie die Web-Service-API verwenden, erreichen Sie dies mit einem `PDFUtilityServiceService`-Objekt.

**Aufrufen des Konvertierungsvorgangs von XDP nach PDF**

Nachdem Sie den Service-Client erstellt haben, können Sie den Konvertierungsvorgang von XDP nach PDF aufrufen.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente anhand der Java-API](pdf-utilities.md#convert-xdp-documents-into-pdf-documents-using-the-java-api)

[Konvertieren von XDP-Dokumenten in PDF-Dokumente anhand der Web-Service-API](pdf-utilities.md#converting-xdp-documents-into-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von XDP-Dokumenten in PDF-Dokumente anhand der Java-API {#convert-xdp-documents-into-pdf-documents-using-the-java-api}

Konvertieren von XDP-Dokumenten in PDF-Dokumente anhand der PDF Utilities-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-pdfutility-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Aufrufen des Konvertierungsvorgangs von XDP nach PDF

   Um die Konvertierung durchzuführen, rufen Sie die `convertXDPtoPDF`-Methode des `PDFUtilityServiceClient`-Objekts auf und übergeben Sie ein `com.adobe.idp.Document`-Objekt, das die XDP-Datei darstellt. Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das die soeben erstellte PDF-Datei darstellt.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von XDP-Dokumenten in PDF-Dokumente anhand der Web-Service-API {#converting-xdp-documents-into-pdf-documents-using-the-web-service-api}

Konvertieren von XDP-Dokumenten in PDF-Dokumente anhand der PDF Utilities-API (Web-Service-API):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Services verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceService`-Objekt anhand des Klassenkonstruktors der Proxy.

1. Aufrufen des Konvertierungsvorgangs von XDP nach PDF

   Um die Konvertierung durchzuführen, rufen Sie die `convertXDPtoPDF`-Methode des `PDFUtilityServiceService`-Objekts auf und übergeben Sie ein `BLOB`-Objekt, das die XDP-Datei darstellt. Die Methode gibt ein `BLOB`-Objekt zurück, das die soeben erstellte PDF-Datei darstellt.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Abrufen von PDF-Dokumenteigenschaften {#retrieving-pdf-document-properties}

Sie können die Java- und Web-Service-APIs von PDF Utilities verwenden, um Eigenschaften von PDF-Dokumenten programmgesteuert abzurufen und damit z. B. die zum Lesen des Dokuments erforderliche Acrobat-Mindestversionzu erfahren oder feststellen, ob es sich bei dem Dokument um ein ausfüllbares Formular handelt.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um PDF-Dokumenteigenschaften abzurufen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Vorgang zum Abrufen der Eigenschaften auf.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java API wird dies durch die Erstellung eines `PDFUtilityServiceClient`-Objekts erreicht. Mit der Web-Service-API wird dies durch die Erstellung eines `PDFUtilityServiceService`-Objekts erreicht.

**Aufrufen des Vorgangs zum Abrufen von Eigenschaften**

Nachdem Sie den Service-Client erstellt haben, können Sie den Vorgang zum Abrufen der Eigenschaften aufrufen.

**Siehe auch**

[Abrufen von PDF-Dokumenteigenschaften mithilfe der Java API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-java-api)

[Abrufen von PDF-Dokumenteigenschaften mithilfe der Web-Service-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von PDF-Dokumenteigenschaften mithilfe der Java API {#retrieve-pdf-document-properties-using-the-java-api}

Abrufen von PDF-Dokumenteigenschaften mithilfe der PDF Utilities API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-pdfutility-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt mit den Verbindungseigenschaften übergeben.

1. Aufrufen des Vorgangs zum Abrufen von Eigenschaften

   Um die Konversion durchzuführen, rufen Sie die Methode `PDFUtilityServiceClient`-Methode des `getPDFProperties`-Objekts auf und übergeben Folgendes:

   * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFPropertiesOptionSpec`-Objekt mit den Eigenschaften, die ausgewertet werden sollen.

   Die Methode gibt ein `PDFPropertiesResult`-Objekt mit dem Ergebnis der Authentifizierung zurück.

**Siehe auch**

[Abrufen von PDF-Dokumenteigenschaften](pdf-utilities.md#retrieving-pdf-document-properties)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von PDF-Dokumenteigenschaften mithilfe der Web-Service-API {#retrieve-pdf-document-properties-using-the-web-service-api}

Abrufen von PDF-Dokumenteigenschaften mithilfe der PDF Utilities Web-Service-API:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Services verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie mithilfe Ihres Proxy-Klassenkonstruktors ein `PDFUtilityServiceService`-Objekt.

1. Aufrufen des Vorgangs zum Abrufen von Eigenschaften

   Um die Konversion durchzuführen, rufen Sie die Methode `PDFUtilityServiceService`-Methode des `getPDFProperties`-Objekts auf und übergeben Folgendes:

   * Ein `BLOB`-Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFPropertiesOptionSpec`-Objekt mit den Eigenschaften, die ausgewertet werden sollen.

   Die Methode gibt ein `PDFPropertiesResult`-Objekt mit dem Ergebnis der Authentifizierung zurück.

**Siehe auch**

[Abrufen von PDF-Dokumenteigenschaften](pdf-utilities.md#retrieving-pdf-document-properties)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Festlegen der Speichermodi für PDF-Dokumente {#setting-pdf-document-save-modes}

Sie können die Java- und Web-Service-APIs des PDF-Utilities-Service verwenden, um programmgesteuert einen Speichermodus für ein PDF-Dokument festzulegen. Wenn Sie den PDF-Utilities-Service zum Festlegen eines Speichermodus verwenden, legt der Service nur den Speichermodus fest und speichert das PDF-Dokument nicht tatsächlich. Das PDF-Dokument wird gespeichert, wenn es an einen anderen Service-Vorgang übergeben wird. Beispielsweise können Sie den PDF-Utilities-Service verwenden, um einen bestimmten Speichermodus festzulegen und ihn an den Verschlüsselungs-Service zu übergeben, der das PDF-Dokument speichert und verschlüsselt.

>[!NOTE]
>
>Weitere Informationen zum PDF-Utilities-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

Führen Sie folgende Schritte aus, um die Speicheroption für PDF-Dokumente festzulegen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Legen Sie den Speichermodus fest.
1. Rufen Sie den Speichervorgang auf.
1. Übergeben Sie das PDF-Dokument an einen anderen Vorgang.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java API wird dies durch die Erstellung eines `PDFUtilityServiceClient`-Objekts erreicht. Bei der Webservice-API wird dies mithilfe eines `PDFUtilityServiceService`-Objekts erreicht.

**Festlegen des Speichermodus**

Sie können eine der folgenden Speicheroptionen wählen:

* `INCREMENTAL`: Inkrementelles Speichern, um die für das Speichern benötigte Zeit zu reduzieren.
* `FAST_WEB_VIEW`: Speichern für schnelle Web-Anzeige
* `FULL`: Vollständiges Speichern (ohne Optimierungen)

**Aufrufen des Vorgangs für die Art der Speicherung**

Nachdem Sie den Service-Client erstellt haben, können Sie den Vorgang zum Abrufen der Eigenschaften aufrufen.

**Übergeben des PDF-Dokuments an einen anderen AEM Forms-Vorgang**

Sobald der PDF Utilities-Service den angegebenen Speichermodus festgelegt hat, übergeben Sie das PDF-Dokument an einen anderen AEM Forms-Vorgang. Nach der Rückgabe dieses Vorgangs wird das PDF-Dokument im angegebenen Modus gespeichert. Wenn Sie beispielsweise den PDF Utilities-Service verwenden, um den Modus `FAST_WEB_VIEW` festzulegen, und dann das PDF-Dokument an den Vorgang `encryptUsingPassword` des Verschlüsselungs-Services übergeben, wird das zurückgegebene PDF-Dokument mit einem Kennwort verschlüsselt und im Modus `FAST_WEB_VIEW` gespeichert.

>[!NOTE]
>
>In der diesem Abschnitt zugeordneten Kurzanleitung wird der Modus `FAST_WEB_VIEW` festgelegt und das PDF-Dokument dann an den Vorgang `encryptUsingPassword` des Verschlüsselungs-Services übergeben.

**Siehe auch**

[Festlegen von PDF-Dokumentspeicheroptionen mithilfe der Java-API](pdf-utilities.md#set-pdf-document-save-options-using-the-java-api)

[Festlegen von PDF-Dokumentspeicheroptionen mithilfe der Webservice-API](pdf-utilities.md#set-pdf-document-save-options-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Festlegen von PDF-Dokumentspeicheroptionen mithilfe der Java-API {#set-pdf-document-save-options-using-the-java-api}

So legen Sie die PDF-Dokumentspeicheroptionen mithilfe der PDF Utilities-API (Java) fest:

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-pdfutility-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Festlegen des Speichermodus

   * Erstellen Sie ein Objekt `PDFUtilitySaveMode`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Speichermodus fest, indem Sie die Methode `setSaveStyle` des `PDFUtilitySaveMode`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Speichermodus angibt. Um beispielsweise für eine schnelle Web-Anzeige zu speichern, übergeben Sie `FAST_WEB_VIEW`.

1. Aufrufen des Vorgangs für die Art der Speicherung

   Rufen Sie die `setSaveMode`-Methode des `PDFUtilityServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFUtilitySaveMode`-Objekt, das den zu verwendenden Speicherstil enthält.
   * Ein boolescher Wert, der bestimmt, ob vorherige Einstellungen überschrieben werden sollen.

   Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das mit dem angegebenen Speichermodus formatiert wurde.

1. Übergeben des PDF-Dokuments an einen anderen AEM Forms-Vorgang

   * Übergeben Sie die zurückgegebene `com.adobe.idp.Document`-Objekt an einen anderen AEM Forms-Vorgang.

**Siehe auch**

[Festlegen der Speichermodi für PDF-Dokumente](pdf-utilities.md#setting-pdf-document-save-modes)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Festlegen von PDF-Dokumentspeicheroptionen mithilfe der Webservice-API {#set-pdf-document-save-options-using-the-web-service-api}

So legen Sie die PDF-Dokumentspeicheroptionen mithilfe der PDF Utilities-API (Webservice) fest:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Services verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceService`-Objekt mithilfe des Konstruktors Ihrer Proxy-Klasse.

1. Festlegen des Speichermodus

   * Erstellen Sie ein Objekt `PDFUtilitySaveMode`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Speichermodus fest, indem Sie der Methode `saveStyle` des `PDFUtilitySaveMode`-Objekts einen Zeichenfolgenwert zuweisen, der den Speichermodus angibt. Um beispielsweise für eine schnelle Web-Anzeige zu speichern, geben Sie `FAST_WEB_VIEW` an.

1. Aufrufen des Speicherstilvorgangs

   Rufen Sie die `setSaveMode`-Methode des `PDFUtilityServiceService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFUtilitySaveMode`-Objekt, das den zu verwendenden Speicherstil enthält.
   * Ein boolescher Wert, der bestimmt, ob vorherige Einstellungen überschrieben werden sollen.

   Die Methode gibt ein `BLOB`-Objekt zurück, das unter Verwendung des angegebenen Speicherstils formatiert wurde. Sie können dieses Objekt dann als PDF-Dokument speichern.

1. Übergeben des PDF-Dokuments an einen anderen „Forms“-Vorgang

   * Übergeben Sie das zurückgegebene `BLOB`-Objekt an einen anderen AEM Forms-Vorgang.

**Siehe auch**

[Festlegen der Speichermodi für PDF-Dokumente](pdf-utilities.md#setting-pdf-document-save-modes)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Bereinigen von PDF-Dokumenten {#sanitizing-pdf-documents}

Sie können die Java-APIs von PDF Utilities verwenden, um PDF-Dokumente programmgesteuert in XDP-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Führen Sie die folgenden Schritte aus, um das PDF-Dokument zu bereinigen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Bereinigungsvorgang auf.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Schließen Sie die erforderlichen JAR-Dateien mit ein, wenn Sie eine Client-Anwendung mit Java erstellen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie programmgesteuert einen Bereinigungsvorgang durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Bei der Java-API wird dies erreicht, indem Sie ein `PDFUtilityServiceClient`-Objekt erstellen.

**Aufrufen des Vorgangs zur Konvertierung „PDF in XDP“**

Nachdem Sie den Service-Client erstellt haben, können Sie den Bereinigungsvorgang aufrufen.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Web-Service-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bereinigen von PDF-Dokumenten mithilfe der Java-API {#sanitize-pdf-documents-using-the-java-api}

Bereinigen von Dokumenten mithilfe der PDF Utilities-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie beispielsweise adobe-livecycle-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt unter Verwendung seines Konstruktors und übergeben Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.

1. Aufrufen des Konvertierungsvorgangs PDF in XDP

   Rufen Sie zum Ausführen der Konvertierung die `convertPDFtoXDP`-Methode des `PDFUtilityServiceClient`-Objekts auf und übergeben Sie in ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Bereinigen von PDF-Dokumenten](/help/forms/developing/pdf-utilities-service-java-api.md#quick-start-soap-mode-sanitizing-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
