---
title: Arbeiten mit PDF Utilities
seo-title: Arbeiten mit PDF Utilities
description: Verwenden Sie den PDF Utilities-Dienst, um zwischen PDF- und XDP-Dateiformaten zu konvertieren, PDF-Dokument-Eigenschaften festzulegen und abzurufen sowie XMP Metadaten zu bearbeiten.
seo-description: Verwenden Sie den PDF Utilities-Dienst, um zwischen PDF- und XDP-Dateiformaten zu konvertieren, PDF-Dokument-Eigenschaften festzulegen und abzurufen sowie XMP Metadaten zu bearbeiten.
uuid: a2ea2359-c547-4f1b-b6ca-f276f816e36a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d816bf2e-5236-4084-b7c4-c32b72cdff97
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2607'
ht-degree: 5%

---


# Arbeiten mit PDF Utilities {#working-with-pdf-utilities}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

**Info zum PDF Utilities-Dienst**

Der PDF Utilities-Dienst kann zwischen PDF- und XDP-Dateiformaten konvertieren, PDF-Dokument-Eigenschaften festlegen und abrufen sowie XMP Metadaten bearbeiten. Vor der Konvertierung eines PDF-Dokuments in ein anderes Format ist es beispielsweise sinnvoll, seine Eigenschaften zu überprüfen, um zu bestimmen, welcher Dienstvorgang für die Konvertierung aufgerufen werden soll.

Sie können diese Aufgaben mithilfe des PDF Utilities-Dienstes ausführen:

* Konvertieren von PDF-Dokumenten in XDP-Dokumente
* Konvertieren von XDP-Dokumenten in PDF-Dokumente (Siehe [Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents).)
* PDF-Dokument-Eigenschaften abrufen (Siehe [PDF-Dokument-Eigenschaften abrufen](pdf-utilities.md#retrieving-pdf-document-properties).)
* Speichern Sie ein PDF-Dokument und optimieren Sie es für eine schnelle Webanzeige. (Siehe [Festlegen von PDF-Dokument Speichermodi](pdf-utilities.md#setting-pdf-document-save-modes).)

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PDF-Dokumenten in XDP-Dokumente {#converting-pdf-documents-into-xdp-documents}

Sie können die Java- und Webdienst-APIs von PDF Utilities verwenden, um PDF-Dokumente programmgesteuert in XDP-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So konvertieren Sie ein PDF-Dokument in ein XDP-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Konvertierungsvorgang &quot;PDF in XDP&quot;auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**PDFUtilityService-Client erstellen**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient`-Objekt erstellt wird. Mit der Webdienst-API wird dies mithilfe eines Objekts `PDFUtilityServiceService` erreicht.

**PDF in XDP-Konvertierungsvorgang aufrufen**

Nachdem Sie den Dienstclient erstellt haben, können Sie den Konvertierungsvorgang &quot;PDF in XDP&quot;aufrufen.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mit der Java-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von PDF-Dokumenten in XDP-Dokumente mit der Java-API {#convert-pdf-documents-into-xdp-documents-using-the-java-api}

Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der PDF Utilities API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-pdfutility-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. PDF in XDP-Konvertierungsvorgang aufrufen

   Um die Konvertierung durchzuführen, rufen Sie die `PDFUtilityServiceClient`-Methode des Objekts `convertPDFtoXDP` auf und übergeben Sie ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API {#convert-pdf-documents-into-xdp-documents-using-the-web-service-api}

Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der PDF Utilities API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceService`-Objekt mit Ihrem Proxyklassenkonstruktor.

1. PDF in XDP-Konvertierungsvorgang aufrufen

   Rufen Sie die `convertPDFtoXDP`-Methode des Objekts auf und übergeben Sie ein `BLOB`-Objekt, das die PDF-Datei darstellt. `PDFUtilityServiceService` Die Methode gibt ein `BLOB`-Objekt zurück, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Konvertieren von XDP-Dokumenten in PDF-Dokumente {#converting-xdp-documents-into-pdf-documents}

Sie können die Java- und Webdienst-APIs von PDF Utilities verwenden, um XDP-Dokumente programmgesteuert in PDF-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So konvertieren Sie ein XDP-Dokument in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. XDP-Konvertierungsvorgang in PDF aufrufen.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**PDFUtilityService-Client erstellen**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient`-Objekt erstellt wird. Mit der Webdienst-API wird dies mithilfe eines Objekts `PDFUtilityServiceService` erreicht.

**XDP-Konvertierungsvorgang in PDF aufrufen**

Nachdem Sie den Dienstclient erstellt haben, können Sie den Konvertierungsvorgang &quot;XDP in PDF&quot;aufrufen.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente mit der Java-API](pdf-utilities.md#convert-xdp-documents-into-pdf-documents-using-the-java-api)

[Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Webdienst-API](pdf-utilities.md#converting-xdp-documents-into-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von XDP-Dokumenten in PDF-Dokumente mit der Java-API {#convert-xdp-documents-into-pdf-documents-using-the-java-api}

Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der PDF Utilities API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-pdfutility-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. XDP-Konvertierungsvorgang in PDF aufrufen

   Um die Konvertierung durchzuführen, rufen Sie die `PDFUtilityServiceClient`-Objektmethode `convertXDPtoPDF` auf und übergeben Sie ein `com.adobe.idp.Document`-Objekt, das die XDP-Datei darstellt. Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das die neu erstellte PDF-Datei darstellt.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von XDP-Dokumenten in PDF-Dokumente mit der Webdienst-API {#converting-xdp-documents-into-pdf-documents-using-the-web-service-api}

Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der PDF Utilities API (Webdienst-API):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceService`-Objekt mit Ihrem Proxyklassenkonstruktor.

1. XDP-Konvertierungsvorgang in PDF aufrufen

   Um die Konvertierung durchzuführen, rufen Sie die `PDFUtilityServiceService`-Objektmethode `convertXDPtoPDF` auf und übergeben Sie ein `BLOB`-Objekt, das die XDP-Datei darstellt. Die Methode gibt ein `BLOB`-Objekt zurück, das die neu erstellte PDF-Datei darstellt.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## PDF-Dokument-Eigenschaften abrufen {#retrieving-pdf-document-properties}

Mit den Java- und Webdienst-APIs von PDF Utilities können Sie PDF-Dokument-Eigenschaften programmgesteuert abrufen, z. B. ob es sich bei dem Dokument um ein ausfüllbares Formular oder um die Acrobat-Mindestversion handelt, die zum Lesen des Dokuments erforderlich ist.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Zusammenfassung der Schritte {#summary_of_steps-2}

So rufen Sie PDF-Dokument-Eigenschaften ab:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Vorgang zum Abrufen der Eigenschaften auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**PDFUtilityService-Client erstellen**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient`-Objekt erstellt wird. Mit der Webdienst-API wird dies mithilfe eines `PDFUtilityServiceService`-Objekts erreicht.

**Abrufen der Eigenschaften aufrufen**

Nachdem Sie den Dienstclient erstellt haben, können Sie den Vorgang zum Abrufen der Eigenschaften aufrufen.

**Siehe auch**

[PDF-Dokument-Eigenschaften mit der Java-API abrufen](pdf-utilities.md#retrieve-pdf-document-properties-using-the-java-api)

[Abrufen von PDF-Dokument-Eigenschaften mithilfe der Webdienst-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-Dokument-Eigenschaften mit der Java-API abrufen {#retrieve-pdf-document-properties-using-the-java-api}

Rufen Sie PDF-Dokument-Eigenschaften mithilfe der PDF Utilities API (Java) ab:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-pdfutility-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Abrufen der Eigenschaften aufrufen

   Um die Konvertierung durchzuführen, rufen Sie die `getPDFProperties`-Methode des Objekts auf und geben Sie Folgendes ein:`PDFUtilityServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFPropertiesOptionSpec`-Objekt, das die zu evaluierenden Eigenschaften enthält.

   Die Methode gibt ein `PDFPropertiesResult`-Objekt zurück, das die Ergebnisse der Abfrage enthält.

**Siehe auch**

[PDF-Dokument-Eigenschaften abrufen](pdf-utilities.md#retrieving-pdf-document-properties)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von PDF-Dokument-Eigenschaften mithilfe der Webdienst-API {#retrieve-pdf-document-properties-using-the-web-service-api}

Rufen Sie PDF-Dokument-Eigenschaften mithilfe der PDF Utilities-Webdienst-API ab:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceService`-Objekt mit Ihrem Proxyklassenkonstruktor.

1. Abrufen der Eigenschaften aufrufen

   Um die Konvertierung durchzuführen, rufen Sie die `getPDFProperties`-Methode des Objekts auf und geben Sie Folgendes ein:`PDFUtilityServiceService`

   * Ein `BLOB`-Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFPropertiesOptionSpec`-Objekt, das die zu evaluierenden Eigenschaften enthält.

   Die Methode gibt ein `PDFPropertiesResult`-Objekt zurück, das die Ergebnisse der Abfrage enthält.

**Siehe auch**

[PDF-Dokument-Eigenschaften abrufen](pdf-utilities.md#retrieving-pdf-document-properties)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Einstellen der PDF-Dokument-Speichermodi {#setting-pdf-document-save-modes}

Mit den Java- und Webdienst-APIs des PDF Utilities-Dienstes können Sie programmgesteuert einen Speichermodus für ein PDF-Dokument festlegen. Wenn Sie mit dem PDF Utilities-Dienst einen Speichermodus festlegen, legt der PDF Utilities-Dienst nur den Speichermodus fest und speichert das PDF-Dokument nicht. Das PDF-Dokument wird gespeichert, wenn es an einen anderen Dienstvorgang weitergeleitet wird. Beispielsweise können Sie den PDF Utilities-Dienst verwenden, um einen bestimmten Speichermodus festzulegen und ihn an den Encryption-Dienst weiterzuleiten, wo das PDF-Dokument gespeichert und verschlüsselt wird.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So legen Sie die Speicheroption für PDF-Dokumente fest:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Legen Sie den Speichermodus fest.
1. Rufen Sie den Speichervorgang auf.
1. Übergeben Sie das PDF-Dokument an einen anderen Vorgang.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**PDFUtilityService-Client erstellen**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient`-Objekt erstellt wird. Mit der Webdienst-API wird dies mithilfe eines `PDFUtilityServiceService`-Objekts erreicht.

**Modus &quot;Speichern&quot;festlegen**

Sie können eine der folgenden Speicheroptionen wählen:

* `INCREMENTAL`: So sparen Sie inkrementell, um die zum Speichern erforderliche Zeit zu reduzieren
* `FAST_WEB_VIEW`: sparen für schnelle Webanzeige
* `FULL`: So speichern Sie mit einem vollständigen Speichern (ohne Optimierungen)

**Aufrufen des Vorgangs zum Speichern des Stils**

Nachdem Sie den Dienstclient erstellt haben, können Sie den Vorgang zum Abrufen der Eigenschaften aufrufen.

**PDF-Dokument an einen anderen AEM Forms-Vorgang übergeben**

Sobald der PDF Utilities-Dienst den angegebenen Speichermodus festgelegt hat, übergeben Sie das PDF-Dokument an einen anderen AEM Forms-Vorgang. Nach der Rückgabe aus diesem Vorgang wird das PDF-Dokument im angegebenen Modus gespeichert. Wenn Sie beispielsweise den PDF Utilities-Dienst verwenden, um den `FAST_WEB_VIEW`-Modus festzulegen und dann das PDF-Dokument an den `encryptUsingPassword`-Vorgang des Encryption-Dienstes zu übergeben, wird das zurückgegebene PDF-Dokument mit einem Kennwort verschlüsselt und im Modus `FAST_WEB_VIEW` gespeichert.

>[!NOTE]
>
>Der diesem Abschnitt zugeordnete Quick-Beginn stellt den `FAST_WEB_VIEW`-Modus ein und übergibt dann das PDF-Dokument an den `encryptUsingPassword`-Vorgang des Encryption-Dienstes.

**Siehe auch**

[Festlegen von PDF-Dokument-Speicheroptionen mit der Java-API](pdf-utilities.md#set-pdf-document-save-options-using-the-java-api)

[Festlegen von PDF-Dokument-Speicheroptionen mithilfe der Webdienst-API](pdf-utilities.md#set-pdf-document-save-options-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-Dokumente mit einem Kennwort verschlüsseln](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Festlegen der Speicheroptionen für PDF-Dokumente mit der Java-API {#set-pdf-document-save-options-using-the-java-api}

Legen Sie die Speicheroptionen für PDF-Dokumente mithilfe der PDF Utilities API (Java) fest:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-pdfutility-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Modus &quot;Speichern&quot;festlegen

   * Erstellen Sie ein Objekt `PDFUtilitySaveMode`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Speichermodus fest, indem Sie die `setSaveStyle`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Speichermodus angibt. `PDFUtilitySaveMode` Um beispielsweise für eine schnelle Webanzeige zu speichern, übergeben Sie `FAST_WEB_VIEW`.

1. Aufrufen des Vorgangs zum Speichern des Stils

   Rufen Sie die `setSaveMode`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`PDFUtilityServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFUtilitySaveMode`-Objekt, das den zu verwendenden Speicherstil enthält.
   * Ein boolescher Wert, der bestimmt, ob vorherige Einstellungen außer Kraft gesetzt werden sollen.

   Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das mit dem angegebenen Speicherstil formatiert wurde.

1. PDF-Dokument an einen anderen AEM Forms-Vorgang übergeben

   * Übergeben Sie das zurückgegebene `com.adobe.idp.Document`-Objekt an einen anderen AEM Forms-Vorgang.

**Siehe auch**

[Einstellen der PDF-Dokument-Speichermodi](pdf-utilities.md#setting-pdf-document-save-modes)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Festlegen der PDF-Dokument-Speicheroptionen mithilfe der Webdienst-API {#set-pdf-document-save-options-using-the-web-service-api}

Legen Sie mithilfe des PDF Utilities AP (Webdienst) die Speicheroptionen für das PDF-Dokument fest:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceService`-Objekt mit Ihrem Proxyklassenkonstruktor.

1. Modus &quot;Speichern&quot;festlegen

   * Erstellen Sie ein Objekt `PDFUtilitySaveMode`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Speichermodus fest, indem Sie der `PDFUtilitySaveMode`-Objektmethode `saveStyle`, die den Speichermodus angibt, einen Zeichenfolgenwert zuweisen. Um beispielsweise für eine schnelle Webanzeige zu speichern, geben Sie `FAST_WEB_VIEW` an.

1. Aufrufen des Vorgangs zum Speichern des Stils

   Rufen Sie die `setSaveMode`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`PDFUtilityServiceService`

   * Ein `BLOB`-Objekt, das das PDF-Dokument darstellt.
   * Ein `PDFUtilitySaveMode`-Objekt, das den zu verwendenden Speicherstil enthält.
   * Ein boolescher Wert, der bestimmt, ob vorherige Einstellungen außer Kraft gesetzt werden sollen.

   Die Methode gibt ein `BLOB`-Objekt zurück, das mit dem angegebenen Speicherstil formatiert wurde. Sie können dieses Objekt dann als PDF-Dokument speichern.

1. PDF-Dokument an einen anderen Forms-Vorgang übergeben

   * Übergeben Sie das zurückgegebene `BLOB`-Objekt an einen anderen AEM Forms-Vorgang.

**Siehe auch**

[Einstellen der PDF-Dokument-Speichermodi](pdf-utilities.md#setting-pdf-document-save-modes)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Bereinigen von PDF-Dokumenten {#sanitizing-pdf-documents}

Sie können die Java-APIs von PDF Utilities verwenden, um PDF-Dokumente programmgesteuert in XDP-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Um PDF Dokument zu bereinigen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Bereinigungsvorgang auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Um eine Clientanwendung mit Java zu erstellen, schließen Sie die erforderlichen JAR-Dateien ein.

**PDFUtilityService-Client erstellen**

Bevor Sie einen Bereinigungsvorgang programmatisch durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `PDFUtilityServiceClient`-Objekt erstellt wird.

**PDF in XDP-Konvertierungsvorgang aufrufen**

Nachdem Sie den Dienstclient erstellt haben, können Sie den Bereinigungsvorgang aufrufen.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mit der Java-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bereinigen von PDF-Dokumenten mit der Java-API {#sanitize-pdf-documents-using-the-java-api}

Bereinigen von Dokumenten mithilfe der PDF Utilities API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-pdfutility-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. PDFUtilityService-Client erstellen

   Erstellen Sie ein `PDFUtilityServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. PDF in XDP-Konvertierungsvorgang aufrufen

   Um die Konvertierung durchzuführen, rufen Sie die `PDFUtilityServiceClient`-Methode des Objekts `convertPDFtoXDP` auf und übergeben Sie ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Bereinigen von PDF-Dokumenten](/help/forms/developing/pdf-utilities-service-java-api.md#quick-start-soap-mode-sanitizing-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
