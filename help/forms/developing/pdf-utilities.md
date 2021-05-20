---
title: Arbeiten mit PDF Utilities
seo-title: Arbeiten mit PDF Utilities
description: Verwenden Sie den PDF Utilities-Dienst, um zwischen PDF- und XDP-Dateiformaten zu konvertieren, PDF-Dokumenteigenschaften festzulegen und abzurufen und XMP Metadaten zu bearbeiten.
seo-description: Verwenden Sie den PDF Utilities-Dienst, um zwischen PDF- und XDP-Dateiformaten zu konvertieren, PDF-Dokumenteigenschaften festzulegen und abzurufen und XMP Metadaten zu bearbeiten.
uuid: a2ea2359-c547-4f1b-b6ca-f276f816e36a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d816bf2e-5236-4084-b7c4-c32b72cdff97
role: Developer
exl-id: e4b204ee-7261-42b8-8db8-a92aa9fd0a28
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2606'
ht-degree: 5%

---

# Arbeiten mit PDF Utilities {#working-with-pdf-utilities}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

**Über den PDF Utilities-Dienst**

Der PDF Utilities-Dienst kann zwischen PDF- und XDP-Dateiformaten konvertieren, PDF-Dokumenteigenschaften festlegen und abrufen und XMP Metadaten bearbeiten. Vor dem Konvertieren eines PDF-Dokuments in ein anderes Format ist es beispielsweise nützlich, seine Eigenschaften zu überprüfen, um zu ermitteln, welcher Dienstvorgang für die Konvertierung aufgerufen werden soll.

Sie können diese Aufgaben mithilfe des PDF Utilities-Dienstes ausführen:

* Konvertieren von PDF-Dokumenten in XDP-Dokumente.
* Konvertieren von XDP-Dokumenten in PDF-Dokumente. (Siehe [Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents).)
* PDF-Dokumenteigenschaften abrufen. (Siehe [Abrufen von PDF-Dokumenteigenschaften](pdf-utilities.md#retrieving-pdf-document-properties).)
* Speichern Sie ein PDF-Dokument und optimieren Sie es für eine schnelle Webanzeige. (Siehe [Festlegen von PDF Document Save Modes](pdf-utilities.md#setting-pdf-document-save-modes).)

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PDF-Dokumenten in XDP-Dokumente {#converting-pdf-documents-into-xdp-documents}

Sie können die Java- und Webdienst-APIs von PDF Utilities verwenden, um PDF-Dokumente programmgesteuert in XDP-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um ein PDF-Dokument in ein XDP-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Konvertierungsvorgang &quot;PDF in XDP&quot;auf.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert ausführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient` -Objekt erstellt wird. Mit der Webdienst-API wird dies durch die Verwendung eines `PDFUtilityServiceService` -Objekts erreicht.

**Konvertierungsvorgang &quot;PDF in XDP aufrufen&quot;**

Nachdem Sie den Dienst-Client erstellt haben, können Sie den Konvertierungsvorgang &quot;PDF in XDP&quot;aufrufen.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API {#convert-pdf-documents-into-xdp-documents-using-the-java-api}

Konvertieren Sie PDF-Dokumente mithilfe der PDF Utilities-API (Java) in XDP-Dokumente:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-pdfutility-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Konvertierungsvorgang &quot;PDF in XDP aufrufen&quot;

   Um die Konvertierung durchzuführen, rufen Sie die `convertPDFtoXDP` -Methode des Objekts auf und übergeben Sie ein `com.adobe.idp.Document` -Objekt, das die PDF-Datei darstellt. `PDFUtilityServiceClient` Die Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API {#convert-pdf-documents-into-xdp-documents-using-the-web-service-api}

Konvertieren Sie PDF-Dokumente mithilfe der PDF Utilities-API (Webdienst) in XDP-Dokumente:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceService` -Objekt mithilfe Ihres Proxy-Klassenkonstruktors.

1. Konvertierungsvorgang &quot;PDF in XDP aufrufen&quot;

   Rufen Sie die `convertPDFtoXDP`-Methode des Objekts `PDFUtilityServiceService` auf und übergeben Sie ein `BLOB`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `BLOB` -Objekt zurück, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Konvertieren von XDP-Dokumenten in PDF-Dokumente {#converting-xdp-documents-into-pdf-documents}

Sie können die Java- und Webdienst-APIs von PDF Utilities verwenden, um XDP-Dokumente programmgesteuert in PDF-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Schritte aus, um ein XDP-Dokument in ein PDF-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Vorgang &quot;XDP to PDF Conversion&quot;auf.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert ausführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient` -Objekt erstellt wird. Mit der Webdienst-API wird dies durch die Verwendung eines `PDFUtilityServiceService` -Objekts erreicht.

**Aufrufen des Konvertierungsvorgangs &quot;XDP in PDF&quot;**

Nachdem Sie den Dienst-Client erstellt haben, können Sie den Konvertierungsvorgang &quot;XDP in PDF&quot;aufrufen.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Java-API](pdf-utilities.md#convert-xdp-documents-into-pdf-documents-using-the-java-api)

[Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Web Service-API](pdf-utilities.md#converting-xdp-documents-into-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Java-API {#convert-xdp-documents-into-pdf-documents-using-the-java-api}

Konvertieren Sie XDP-Dokumente mithilfe der PDF Utilities-API (Java) in PDF-Dokumente:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-pdfutility-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Aufrufen des Konvertierungsvorgangs &quot;XDP in PDF&quot;

   Um die Konvertierung durchzuführen, rufen Sie die `convertXDPtoPDF` -Methode des Objekts auf und übergeben Sie ein `com.adobe.idp.Document` -Objekt, das die XDP-Datei darstellt. `PDFUtilityServiceClient` Die Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das die neu erstellte PDF-Datei darstellt.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Webdienst-API {#converting-xdp-documents-into-pdf-documents-using-the-web-service-api}

Konvertieren Sie XDP-Dokumente mithilfe der PDF Utilities-API (Web Service API) in PDF-Dokumente:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceService` -Objekt mithilfe Ihres Proxy-Klassenkonstruktors.

1. Aufrufen des Konvertierungsvorgangs &quot;XDP in PDF&quot;

   Um die Konvertierung durchzuführen, rufen Sie die `convertXDPtoPDF` -Methode des Objekts auf und übergeben Sie ein `BLOB` -Objekt, das die XDP-Datei darstellt. `PDFUtilityServiceService` Die Methode gibt ein `BLOB` -Objekt zurück, das die neu erstellte PDF-Datei darstellt.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Abrufen von PDF-Dokumenteigenschaften {#retrieving-pdf-document-properties}

Sie können die Java- und Webdienst-APIs von PDF Utilities verwenden, um PDF-Dokumenteigenschaften programmgesteuert abzurufen, z. B. ob es sich bei dem Dokument um ein ausfüllbares Formular oder um die zum Lesen des Dokuments erforderliche Mindestversion von Acrobat handelt.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um PDF-Dokumenteigenschaften abzurufen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Vorgang zum Abrufen der Eigenschaften auf.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert ausführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient` -Objekt erstellt wird. Mit der Webdienst-API wird dies mithilfe eines `PDFUtilityServiceService` -Objekts erreicht.

**Abrufen der Eigenschaften**

Nachdem Sie den Service-Client erstellt haben, können Sie den Vorgang zum Abrufen der Eigenschaften aufrufen.

**Siehe auch**

[Abrufen von PDF-Dokumenteigenschaften mithilfe der Java-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-java-api)

[Abrufen von PDF-Dokumenteigenschaften mithilfe der Webdienst-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von PDF-Dokumenteigenschaften mithilfe der Java-API {#retrieve-pdf-document-properties-using-the-java-api}

Abrufen von PDF-Dokumenteigenschaften mithilfe der PDF Utilities-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-pdfutility-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Abrufen der Eigenschaften

   Um die Konvertierung durchzuführen, rufen Sie die `getPDFProperties` -Methode des `PDFUtilityServiceClient` -Objekts auf und übergeben Sie Folgendes:

   * Ein `com.adobe.idp.Document` -Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFPropertiesOptionSpec` -Objekt, das die zu bewertenden Eigenschaften enthält.

   Die Methode gibt ein `PDFPropertiesResult` -Objekt zurück, das die Ergebnisse der Abfrage enthält.

**Siehe auch**

[Abrufen von PDF-Dokumenteigenschaften](pdf-utilities.md#retrieving-pdf-document-properties)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von PDF-Dokumenteigenschaften mithilfe der Webdienst-API {#retrieve-pdf-document-properties-using-the-web-service-api}

Rufen Sie PDF-Dokumenteigenschaften mithilfe der PDF Utilities-Webdienst-API ab:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceService` -Objekt mithilfe Ihres Proxy-Klassenkonstruktors.

1. Abrufen der Eigenschaften

   Um die Konvertierung durchzuführen, rufen Sie die `getPDFProperties` -Methode des `PDFUtilityServiceService` -Objekts auf und übergeben Sie Folgendes:

   * Ein `BLOB` -Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFPropertiesOptionSpec` -Objekt, das die zu bewertenden Eigenschaften enthält.

   Die Methode gibt ein `PDFPropertiesResult` -Objekt zurück, das die Ergebnisse der Abfrage enthält.

**Siehe auch**

[Abrufen von PDF-Dokumenteigenschaften](pdf-utilities.md#retrieving-pdf-document-properties)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Einstellen der PDF-Dokumentspeichermodi {#setting-pdf-document-save-modes}

Sie können die Java- und Webdienst-APIs des PDF Utilities-Dienstes verwenden, um programmgesteuert einen Speichermodus für ein PDF-Dokument festzulegen. Wenn der PDF Utilities-Dienst zum Festlegen eines Speichermodus verwendet wird, legt der PDF Utilities-Dienst nur den Speichermodus fest und speichert das PDF-Dokument nicht. Das PDF-Dokument wird gespeichert, wenn es an einen anderen Dienstvorgang übergeben wird. Beispielsweise können Sie den PDF Utilities-Dienst verwenden, um einen bestimmten Speichermodus festzulegen und ihn an den Encryption-Dienst zu übergeben, in dem das PDF-Dokument gespeichert und verschlüsselt wird.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So legen Sie die Speicheroption für PDF-Dokumente fest:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Legen Sie den Speichermodus fest.
1. Rufen Sie den Speichervorgang auf.
1. Übergeben Sie das PDF-Dokument an einen anderen Vorgang.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert ausführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient` -Objekt erstellt wird. Mit der Webdienst-API wird dies mithilfe eines `PDFUtilityServiceService` -Objekts erreicht.

**Speichern-Modus festlegen**

Sie können eine der folgenden Speicheroptionen auswählen:

* `INCREMENTAL`: So sparen Sie schrittweise, um die zum Speichern erforderliche Zeit zu verkürzen
* `FAST_WEB_VIEW`: Speichern für schnelle Webanzeige
* `FULL`: So speichern Sie mit einem vollständigen Speichern (ohne Optimierungen)

**Aufrufen des Vorgangs &quot;save style&quot;**

Nachdem Sie den Service-Client erstellt haben, können Sie den Vorgang zum Abrufen der Eigenschaften aufrufen.

**Übergeben des PDF-Dokuments an einen anderen AEM Forms-Vorgang**

Sobald der PDF Utilities-Dienst den angegebenen Speichermodus festgelegt hat, übergeben Sie das PDF-Dokument an einen anderen AEM Forms-Vorgang. Nach der Rückgabe dieses Vorgangs wird das PDF-Dokument im angegebenen Modus gespeichert. Wenn Sie beispielsweise den PDF Utilities-Dienst verwenden, um den Modus `FAST_WEB_VIEW` festzulegen und dann das PDF-Dokument an den Vorgang `encryptUsingPassword` des Verschlüsselungsdienstes zu übergeben, wird das zurückgegebene PDF-Dokument mit einem Kennwort verschlüsselt und im Modus `FAST_WEB_VIEW` gespeichert.

>[!NOTE]
>
>Der Schnellstart-Vorgang, der mit diesem Abschnitt verknüpft ist, legt den Modus `FAST_WEB_VIEW` fest und übergibt dann das PDF-Dokument an den Vorgang `encryptUsingPassword` des Encryption-Dienstes.

**Siehe auch**

[PDF-Dokumentspeicheroptionen mithilfe der Java-API festlegen](pdf-utilities.md#set-pdf-document-save-options-using-the-java-api)

[PDF-Dokumentspeicheroptionen mithilfe der Webdienst-API festlegen](pdf-utilities.md#set-pdf-document-save-options-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### PDF-Dokumentspeicheroptionen mithilfe der Java-API festlegen {#set-pdf-document-save-options-using-the-java-api}

Legen Sie die PDF-Dokumentspeicheroptionen mithilfe der PDF Utilities-API (Java) fest:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-pdfutility-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Speichern-Modus festlegen

   * Erstellen Sie ein Objekt `PDFUtilitySaveMode`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Speichermodus fest, indem Sie die `setSaveStyle` -Methode des Objekts `PDFUtilitySaveMode` aufrufen und einen Zeichenfolgenwert übergeben, der den Speichermodus angibt. Um beispielsweise für eine schnelle Webanzeige zu speichern, übergeben Sie `FAST_WEB_VIEW`.

1. Aufrufen des Vorgangs &quot;save style&quot;

   Rufen Sie die `setSaveMode` -Methode des Objekts `PDFUtilityServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFUtilitySaveMode` -Objekt, das den zu verwendenden Speicherstil enthält.
   * Ein boolescher Wert, der bestimmt, ob vorherige Einstellungen überschrieben werden sollen.

   Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das mit dem angegebenen Speicherstil formatiert wurde.

1. Übergeben des PDF-Dokuments an einen anderen AEM Forms-Vorgang

   * Übergeben Sie das zurückgegebene `com.adobe.idp.Document`-Objekt an einen anderen AEM Forms-Vorgang.

**Siehe auch**

[PDF-Dokumentspeichermodi festlegen](pdf-utilities.md#setting-pdf-document-save-modes)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-Dokumentspeicheroptionen mithilfe der Webdienst-API {#set-pdf-document-save-options-using-the-web-service-api} festlegen

Legen Sie die Speicheroptionen für PDF-Dokumente mit der PDF Utilities-API (Webdienst) fest:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceService` -Objekt mithilfe Ihres Proxy-Klassenkonstruktors.

1. Speichern-Modus festlegen

   * Erstellen Sie ein Objekt `PDFUtilitySaveMode`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Speichermodus fest, indem Sie der `saveStyle` -Methode des Objekts `PDFUtilitySaveMode`, die den Speichermodus angibt, einen Zeichenfolgenwert zuweisen. Um beispielsweise für eine schnelle Webanzeige zu speichern, geben Sie `FAST_WEB_VIEW` an.

1. Aufrufen des Vorgangs &quot;save style&quot;

   Rufen Sie die `setSaveMode` -Methode des Objekts `PDFUtilityServiceService` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFUtilitySaveMode` -Objekt, das den zu verwendenden Speicherstil enthält.
   * Ein boolescher Wert, der bestimmt, ob vorherige Einstellungen überschrieben werden sollen.

   Die Methode gibt ein `BLOB`-Objekt zurück, das mit dem angegebenen Speicherstil formatiert wurde. Sie können dieses Objekt dann als PDF-Dokument speichern.

1. Übergeben des PDF-Dokuments an einen anderen Forms-Vorgang

   * Übergeben Sie das zurückgegebene `BLOB`-Objekt an einen anderen AEM Forms-Vorgang.

**Siehe auch**

[PDF-Dokumentspeichermodi festlegen](pdf-utilities.md#setting-pdf-document-save-modes)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Bereinigen von PDF-Dokumenten {#sanitizing-pdf-documents}

Sie können die Java-APIs von PDF Utilities verwenden, um PDF-Dokumente programmgesteuert in XDP-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Um PDF-Dokumente zu bereinigen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Bereinigungsvorgang auf.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Schließen Sie die erforderlichen JAR-Dateien ein, um eine Client-Anwendung mit Java zu erstellen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie programmgesteuert einen Bereinigungsvorgang durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient` -Objekt erstellt wird.

**Konvertierungsvorgang &quot;PDF in XDP aufrufen&quot;**

Nachdem Sie den Service-Client erstellt haben, können Sie den Bereinigungsvorgang aufrufen.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bereinigen von PDF-Dokumenten mit der Java-API {#sanitize-pdf-documents-using-the-java-api}

Bereinigen von Dokumenten mithilfe der PDF Utilities-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-pdfutility-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie ein `PDFUtilityServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Konvertierungsvorgang &quot;PDF in XDP aufrufen&quot;

   Um die Konvertierung durchzuführen, rufen Sie die `convertPDFtoXDP` -Methode des Objekts auf und übergeben Sie ein `com.adobe.idp.Document` -Objekt, das die PDF-Datei darstellt. `PDFUtilityServiceClient` Die Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Bereinigen von PDF-Dokumenten](/help/forms/developing/pdf-utilities-service-java-api.md#quick-start-soap-mode-sanitizing-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
