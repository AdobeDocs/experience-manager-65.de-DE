---
title: Arbeiten mit Formularen mit Strichcode
seo-title: Arbeiten mit Formularen mit Strichcode
description: Dekodieren von Daten aus einem PDF-Formular oder einem Bild, das einen Barcode enthält, mithilfe der Java API und der Web Service API.
seo-description: Dekodieren von Daten aus einem PDF-Formular oder einem Bild, das einen Barcode enthält, mithilfe der Java API und der Web Service API.
uuid: e56c3c94-384d-401f-b418-dd34cdc57eda
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: eb28ac30-265c-4611-8247-1f4bc826f254
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1946'
ht-degree: 2%

---


# Arbeiten mit Barcoded Forms {#working-with-barcoded-forms}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

## Info zum Barcoded Forms-Dienst {#about-the-barcoded-forms-service}

Der Barcoded Forms-Dienst automatisiert die Erfassung von Daten aus Ausfüllungs- und Druckformularen und integriert erfasste Informationen in die IT-Kernsysteme eines Unternehmens.

Mithilfe des Barcoded Forms-Dienstes können Sie interaktiven PDF forms eindimensionale und zweidimensionale Barcodes hinzufügen. Sie können die mit Strichcode versehenen Formulare dann auf einer Website veröffentlichen oder per E-Mail oder CD verteilen. Wenn ein Benutzer ein mit Strichcode versehenes Formular mit Adobe Reader, Acrobat Professional oder Acrobat Standard ausfüllt, wird der Barcode automatisch aktualisiert, um die vom Benutzer eingegebenen Formulardaten zu kodieren. Der Benutzer kann das Formular elektronisch einreichen oder auf Papier ausdrucken und per Post, Fax oder Hand senden. Sie können die vom Benutzer bereitgestellten Daten später im Rahmen eines automatisierten Arbeitsablaufs extrahieren und die Daten zwischen Genehmigungsprozessen und Geschäftssystemen Routing geben.

Weitere Informationen zum Barcoded Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Dekodieren von Barcoded Form Data {#decoding-barcoded-form-data}

Sie können die Barcoded Forms-Dienst-API verwenden, um Daten aus einem PDF-Formular oder einem Bild, das einen Barcode enthält, zu dekodieren. Das Dekodieren von Formulardaten bedeutet das Extrahieren von Daten, die sich im Barcode befinden. Bevor Daten aus einem PDF-Formular (oder Bild) dekodiert werden können, muss der Benutzer das Formular mit Daten füllen.

>[!NOTE]
>
>Weitere Informationen zum Barcoded Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So dekodieren Sie Daten aus einem PDF-Formular:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein mit Strichcode versehenes formsClient-API-Objekt.
1. Rufen Sie ein PDF-Formular ab, das mit Strichcode versehene Daten enthält.
1. Dekodieren Sie die Daten aus dem PDF-Formular.
1. Konvertieren Sie die Daten in eine XML-Datenquelle.
1. Verarbeiten Sie die dekodierten Daten.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utilities.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* xercesImpl.jar (im Ordner &quot;&lt;Installationsordner>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdparty&quot;)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBOSS ist, müssen Sie adobe-utilities.jar und jbossall-client.jar durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Client-API-Objekts mit Strichcode**

Bevor Sie einen Barcoded Forms-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Barcoded Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `BarcodedFormsServiceClient`-Objekt. Wenn Sie die Barcoded Forms-Webdienst-API verwenden, erstellen Sie ein `BarcodedFormsServiceService`-Objekt.

**PDF-Formular abrufen, das mit Strichcode versehene Daten enthält**

Sie müssen ein PDF-Formular abrufen, das einen Barcode enthält, der mit Benutzerdaten gefüllt wurde.

**Daten aus dem PDF-Formular dekodieren**

Nachdem Sie ein PDF-Formular (oder Bild) mit einem Barcode erhalten haben, können Sie Daten dekodieren. Der Barcoded Forms-Dienst unterstützt die folgenden Barcodetypen:

* PDF417-Barcodes.
* Datenmatrix-Barcodes.
* QR-Code-Barcodes.
* Codabar-Barcodes.
* Barcodes des Codes 128.
* Code 39-Barcodes.
* EAN-13-Barcodes.
* EAN-8-Barcodes.

Die als Hexadezimal eingegebene Zeichensatzeingabe in der Dekodierungs-API bedeutet, dass der Barcode-Inhalt als Hexadezimalzeichenfolge kodiert ist. Wenn beispielsweise UTF-8 als Zeichenkodierung im Formular angegeben ist und Hex im Dekodierungsvorgang angegeben ist, wird der Inhalt des Barcodes als Hex-Zeichenfolge im &lt; `xb:content`-Element in der dekodierten Ausgabe kodiert. Sie können diesen Hex-Wert konvertieren, um den ursprünglichen Inhalt abzurufen, indem Sie die Anwendungslogik in Ihrer Clientanwendung erstellen.

**Daten in eine XML-Datenquelle konvertieren**

Nachdem Sie Formulardaten dekodiert haben, können Sie sie in XDP- oder XFDF-Daten konvertieren. Nehmen Sie beispielsweise an, Sie möchten die Daten in ein anderes Formular importieren. Um die Daten in ein XFA-Formular zu importieren, müssen Sie die Daten in XDP-Daten konvertieren. Weitere Informationen finden Sie unter [Formulardaten importieren](/help/forms/developing/importing-exporting-data.md#importing-form-data).

**Die dekodierten Daten verarbeiten**

Sie können die konvertierten Daten entsprechend Ihren Geschäftsanforderungen verarbeiten. Nachdem Sie die Daten beispielsweise dekodiert und konvertiert haben, können Sie sie in einer Datei speichern, in einer Unternehmensdatenbank speichern, ein anderes Formular ausfüllen usw. In diesem Abschnitt wird beschrieben, wie Sie die konvertierten Daten als XML-Datei speichern.

>[!NOTE]
>
>Der Barcoded Forms-Dienst kann Strichcodedaten nicht dekodieren, wenn die Parameter für Trennzeichen und Feldtrennzeichen denselben Wert haben

**Siehe auch**

[Dekodieren von Formulardaten mit Strichcode mithilfe der Java-API](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[Dekodieren von Formulardaten mit Strichcode mithilfe der Webdienst-API](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Dekodieren von mit Strichcode versehenen Formulardaten mit der Java-API {#decode-barcoded-form-data-using-the-java-api}

Dekodieren von Formulardaten mithilfe der Barcoded Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie JAR-Clientdateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Client-API-Objekts mit Strichcode

   Erstellen Sie ein `BarcodedFormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. PDF-Formular abrufen, das mit Strichcode versehene Daten enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Formular darstellt, das mit Strichcode versehene Daten enthält, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Daten aus dem PDF-Formular dekodieren

   Dekodieren Sie die Formulardaten, indem Sie die `decode`-Methode des `BarcodedFormsServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Formular enthält.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein PDF417-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein Datenmatrix-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein QR-Code-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein Codabar-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein Code-128-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein Code 39-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein EAN-13-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein EAN-8-Barcode dekodiert werden soll.
   * Ein `com.adobe.livecycle.barcodedforms.CharSet`-Auflistung-Wert, der den im Barcode verwendeten Zeichensatzkodierungswert angibt.

   Die `decode`-Methode gibt ein `org.w3c.dom.Document`-Objekt zurück, das dekodierte Formulardaten enthält.

1. Daten in eine XML-Datenquelle konvertieren

   Konvertieren Sie die dekodierten Daten in XDP- oder XFDF-Daten, indem Sie die `BarcodedFormsServiceClient`-Methode des Objekts `extractToXML` aufrufen und die folgenden Werte übergeben:

   * Das `org.w3c.dom.Document`-Objekt, das dekodierte Daten enthält (stellen Sie sicher, dass Sie den Rückgabewert der `decode`-Methode verwenden).
   * Ein `com.adobe.livecycle.barcodedforms.Delimiter`-Auflistung-Wert, der das Trennzeichen angibt. Es wird empfohlen, `Delimiter.Carriage_Return` anzugeben.
   * Ein `com.adobe.livecycle.barcodedforms.Delimiter`-Auflistung-Wert, der das Feldtrennzeichen angibt. Geben Sie beispielsweise `Delimiter.Tab` an.
   * Ein `com.adobe.livecycle.barcodedforms.XMLFormat`-Auflistung-Wert, der angibt, ob die Barcodedaten in XDP- oder XFDF-XML-Daten konvertiert werden sollen. Geben Sie beispielsweise `XMLFormat.XDP` an, um die Daten in XDP-Daten zu konvertieren.

   >[!NOTE]
   >
   >Geben Sie nicht dieselben Werte für die Parameter für das Trennzeichen und das Feldtrennzeichen an.

   Die `extractToXML`-Methode gibt ein `java.util.List`-Objekt zurück, wobei jedes Element ein `org.w3c.dom.Document`-Objekt ist. Es gibt ein separates Element für jeden Barcode, der sich im Formular befindet. Das heißt, wenn das Formular vier Barcodes enthält, sind im zurückgegebenen `java.util.List`-Objekt vier Elemente enthalten.

1. Die dekodierten Daten verarbeiten

   * Durchlaufen Sie das `java.util.List`-Objekt, um jedes `org.w3c.dom.Document`-Objekt abzurufen, das sich in der Liste befindet.
   * Konvertieren Sie für jedes Element in der Liste das `org.w3c.dom.Document`-Objekt in ein `com.adobe.idp.Document`-Objekt. (Die Anwendungslogik, die ein `org.w3c.dom.Document`-Objekt in ein `com.adobe.idp.Document`-Objekt konvertiert, wird unter Verwendung des Java-API-Beispiels in den Formulardaten für die Dekodierung mit Strichcode angezeigt.)
   * Speichern Sie die XML-Daten als XML-Datei, indem Sie das `com.adobe.idp.Document`-Objekt `copyToFile` aufrufen und ein File-Objekt übergeben, das die XML-Datei darstellt.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Dekodieren von Formulardaten mit Strichcode mithilfe der Java-API](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Dekodieren von mit Strichcode versehenen Formulardaten mit der Webdienst-API {#decode-barcoded-form-data-using-the-web-service-api}

Dekodieren von Formulardaten mithilfe der Barcoded Forms API(Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL des Barcoded Forms-Dienstes verwendet. Weitere Informationen finden Sie unter [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. Weitere Informationen finden Sie unter &quot;Verweisen auf die .NET-Clientassembly&quot;in [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Erstellen eines Client-API-Objekts mit Strichcode

   Erstellen Sie mit der Microsoft .NET-Client-Assembly, die die WSDL des Barcoded Forms-Dienstes verwendet, ein `BarcodedFormsServiceService`-Objekt, indem Sie dessen Standardkonstruktor aufrufen.

1. PDF-Formular abrufen, das mit Strichcode versehene Daten enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das einen Barcode enthält.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `binaryData`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Daten aus dem PDF-Formular dekodieren

   Dekodieren Sie die Formulardaten, indem Sie die `decode`-Methode des `BarcodedFormsServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Formular enthält.
   * Ein `Boolean`-Objekt, das angibt, ob ein PDF417-Barcode dekodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein Datenmatrix-Barcode dekodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein QR-Code-Barcode dekodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein Codabar-Barcode dekodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein Code-128-Barcode dekodiert werden soll.
   * Ein `Bolean`-Objekt, das angibt, ob ein Code 39-Barcode dekodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein EAN-13-Barcode dekodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein EAN-8-Barcode dekodiert werden soll.
   * Ein `CharSet`-Auflistung-Wert, der den im Barcode verwendeten Zeichensatzkodierungswert angibt.

   Die `decode`-Methode gibt einen Zeichenfolgenwert zurück, der dekodierte Formulardaten enthält.

1. Daten in eine XML-Datenquelle konvertieren

   Konvertieren Sie die dekodierten Daten in XDP- oder XFDF-Daten, indem Sie die `BarcodedFormsServiceService`-Methode des Objekts `extractToXML` aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der dekodierte Daten enthält (stellen Sie sicher, dass Sie den Rückgabewert der `decode`-Methode verwenden).
   * Ein `Delimiter`-Auflistung-Wert, der das Trennzeichen angibt. Es wird empfohlen, `Delimiter.Carriage_Return` anzugeben.
   * Ein `Delimiter`-Auflistung-Wert, der das Feldtrennzeichen angibt. Geben Sie beispielsweise `Delimiter.Tab` an.
   * Ein `XMLFormat`-Auflistung-Wert, der angibt, ob die Barcodedaten in XDP- oder XFDF-XML-Daten konvertiert werden sollen. Geben Sie beispielsweise `XMLFormat.XDP` an, um die Daten in XDP-Daten zu konvertieren.

   >[!NOTE]
   >
   >Geben Sie nicht dieselben Werte für die Parameter für das Trennzeichen und das Feldtrennzeichen an.

   Die `extractToXML`-Methode gibt ein `Object`-Array zurück, wobei jedes Element eine `BLOB`-Instanz ist. Es gibt ein separates Element für jeden Barcode, der sich im Formular befindet. Das heißt, wenn sich im Formular vier Barcodes befinden, sind im zurückgegebenen `Object`-Array vier Elemente vorhanden.

1. Die dekodierten Daten verarbeiten

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des geschützten PDF-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `encryptPDFUsingPassword`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
