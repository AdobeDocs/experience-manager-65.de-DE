---
title: Arbeiten mit Barcoded Forms
seo-title: Arbeiten mit Barcoded Forms
description: Dekodieren Sie Daten aus einem PDF-Formular oder einem Bild, das einen Barcode enthält, mithilfe der Java-API und der Web Service-API.
seo-description: Dekodieren Sie Daten aus einem PDF-Formular oder einem Bild, das einen Barcode enthält, mithilfe der Java-API und der Web Service-API.
uuid: e56c3c94-384d-401f-b418-dd34cdc57eda
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: eb28ac30-265c-4611-8247-1f4bc826f254
role: Developer
exl-id: dd32808e-b773-48a2-90e1-7a277d349493
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1945'
ht-degree: 2%

---

# Arbeiten mit Barcoded Forms {#working-with-barcoded-forms}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Über den Barcoded Forms-Dienst {#about-the-barcoded-forms-service}

Der Barcoded Forms-Dienst automatisiert die Erfassung von Daten aus Ausfüllungs- und Druckformularen und integriert erfasste Informationen in die IT-Kernsysteme eines Unternehmens.

Mit dem Barcoded Forms-Dienst können Sie interaktiven PDF forms eindimensionale und zweidimensionale Barcodes hinzufügen. Sie können die mit Strichcode versehenen Formulare dann auf einer Website veröffentlichen oder per E-Mail oder CD verteilen. Wenn ein Benutzer ein mit Strichcode versehenes Formular mit Adobe Reader, Acrobat Professional oder Acrobat Standard ausfüllt, wird der Barcode automatisch aktualisiert, um die vom Benutzer eingegebenen Formulardaten zu kodieren. Der Benutzer kann das Formular elektronisch einreichen oder auf Papier drucken und per Post, Fax oder Hand versenden. Sie können die vom Benutzer eingegebenen Daten später im Rahmen eines automatisierten Workflows extrahieren und die Daten zwischen Genehmigungsprozessen und Geschäftssystemen weiterleiten.

Weitere Informationen zum Barcoded Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Dekodieren von Barcoded Form Data {#decoding-barcoded-form-data}

Sie können die Barcoded Forms-Dienst-API verwenden, um Daten aus einem PDF-Formular oder einem Bild zu dekodieren, das einen Barcode enthält. Das Dekodieren von Formulardaten bedeutet das Extrahieren von Daten, die sich im Barcode befinden. Bevor Daten aus einem PDF-Formular (oder Bild) dekodiert werden können, muss ein Benutzer das Formular mit Daten ausfüllen.

>[!NOTE]
>
>Weitere Informationen zum Barcoded Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So dekodieren Sie Daten aus einem PDF-Formular:

1. Projektdateien einschließen.
1. Erstellen Sie ein Barcoded formsClient-API-Objekt.
1. Rufen Sie ein PDF-Formular mit Barcodedaten ab.
1. Dekodieren Sie die Daten aus dem PDF-Formular.
1. Konvertieren Sie die Daten in eine XML-Datenquelle.
1. Verarbeiten Sie die dekodierten Daten.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* xercesImpl.jar (befindet sich im Ordner &lt;Installationsordner>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdparty)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBOSS ist, müssen Sie adobe-utilities.jar und jbossall-client.jar durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Client-API-Objekt für Barcoded forms erstellen**

Bevor Sie programmgesteuert einen Barcoded Forms-Dienstvorgang durchführen können, müssen Sie einen Barcoded Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `BarcodedFormsServiceClient` -Objekt. Wenn Sie die Barcoded Forms-Webdienst-API verwenden, erstellen Sie ein `BarcodedFormsServiceService`-Objekt.

**PDF-Formular mit Barcodedaten abrufen**

Sie müssen ein PDF-Formular mit einem Barcode abrufen, der mit Benutzerdaten ausgefüllt wurde.

**Daten aus dem PDF-Formular dekodieren**

Nachdem Sie ein PDF-Formular (oder ein Bild) mit einem Barcode erhalten haben, können Sie Daten dekodieren. Der Barcoded Forms-Dienst unterstützt die folgenden Barcodetypen:

* PDF417-Barcodes.
* Datenmatrix-Barcodes.
* QR-Code-Barcodes.
* Codabar-Barcodes.
* Code 128-Barcodes.
* Code 39-Barcodes.
* EAN-13-Barcodes.
* EAN-8-Barcodes.

Die als Hexadezimalwert in der Dekodierungs-API eingegebene Zeichensatzeingabe bedeutet, dass der Barcode-Inhalt als hexadezimale Zeichenfolge kodiert wird. Wenn beispielsweise UTF-8 als Zeichenkodierung im Formular angegeben ist und im Dekodierungsvorgang &quot;Hex&quot;angegeben ist, wird der Barcode-Inhalt als Hex-Zeichenfolge im Element &lt; `xb:content` in der dekodierten Ausgabe kodiert. Sie können diesen Hex-Wert konvertieren, um den ursprünglichen Inhalt zu erhalten, indem Sie eine Anwendungslogik in Ihrer Client-Anwendung erstellen.

**Daten in eine XML-Datenquelle konvertieren**

Nachdem Sie Formulardaten dekodiert haben, können Sie sie in XDP- oder XFDF-Daten konvertieren. Angenommen, Sie möchten die Daten in ein anderes Formular importieren. Um die Daten in ein XFA-Formular zu importieren, müssen Sie die Daten in XDP-Daten konvertieren. Weitere Informationen finden Sie unter [Importieren von Formulardaten](/help/forms/developing/importing-exporting-data.md#importing-form-data).

**Dekodierte Daten verarbeiten**

Sie können die konvertierten Daten verarbeiten, um Ihre Geschäftsanforderungen zu erfüllen. Nachdem Sie beispielsweise die Daten dekodiert und konvertiert haben, können Sie sie in einer Datei speichern, in einer Unternehmensdatenbank speichern, ein anderes Formular ausfüllen usw. In diesem Abschnitt wird beschrieben, wie Sie die konvertierten Daten als XML-Datei speichern.

>[!NOTE]
>
>Der Barcoded Forms-Dienst kann Strichcodedaten nicht dekodieren, wenn die Parameter für das Trennzeichen für Zeilen und Felder denselben Wert haben

**Siehe auch**

[Dekodieren von mit Strichcode versehenen Formulardaten mit der Java-API](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[Dekodieren von mit Strichcode versehenen Formulardaten mithilfe der Webdienst-API](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Dekodieren von mit Strichcode versehenen Formulardaten mit der Java-API {#decode-barcoded-form-data-using-the-java-api}

Dekodieren Sie Formulardaten mithilfe der Barcoded Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Client-API-Objekt für Barcoded forms erstellen

   Erstellen Sie ein `BarcodedFormsServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. PDF-Formular mit Barcodedaten abrufen

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Formular darstellt, das mit dem Barcoded Data enthält, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Daten aus dem PDF-Formular dekodieren

   Dekodieren Sie die Formulardaten, indem Sie die `decode` -Methode des Objekts `BarcodedFormsServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Formular enthält.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob ein PDF417-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob ein Datenmatrix-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob ein QR-Code-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob ein Codabar-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob ein Code-128-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob ein Code-39-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob ein EAN-13-Barcode dekodiert werden soll.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob ein EAN-8-Barcode dekodiert werden soll.
   * Ein `com.adobe.livecycle.barcodedforms.CharSet`-Auflistungswert, der den im Barcode verwendeten Kodierungswert für Zeichensätze angibt.

   Die `decode`-Methode gibt ein `org.w3c.dom.Document`-Objekt zurück, das dekodierte Formulardaten enthält.

1. Daten in eine XML-Datenquelle konvertieren

   Konvertieren Sie die dekodierten Daten in XDP- oder XFDF-Daten, indem Sie die `extractToXML` -Methode des Objekts `BarcodedFormsServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `org.w3c.dom.Document`-Objekt, das dekodierte Daten enthält (stellen Sie sicher, dass Sie den Rückgabewert der `decode`-Methode verwenden).
   * Ein `com.adobe.livecycle.barcodedforms.Delimiter` -Auflistungswert, der das Trennzeichen für die Zeile angibt. Es wird empfohlen, `Delimiter.Carriage_Return` anzugeben.
   * Ein `com.adobe.livecycle.barcodedforms.Delimiter` -Auflistungswert, der das Feldtrennzeichen angibt. Geben Sie beispielsweise `Delimiter.Tab` an.
   * Ein `com.adobe.livecycle.barcodedforms.XMLFormat`-Auflistungswert, der angibt, ob die Barcodedaten in XDP- oder XFDF-XML-Daten konvertiert werden sollen. Geben Sie beispielsweise `XMLFormat.XDP` an, um die Daten in XDP-Daten zu konvertieren.

   >[!NOTE]
   >
   >Geben Sie nicht dieselben Werte für die Parameter &quot;Zeilentrennzeichen&quot;und &quot;Feldtrennzeichen&quot;an.

   Die `extractToXML`-Methode gibt ein `java.util.List`-Objekt zurück, wobei jedes Element ein `org.w3c.dom.Document`-Objekt ist. Für jeden Barcode im Formular gibt es ein eigenes Element. Das heißt, wenn das Formular vier Barcodes enthält, sind vier Elemente im zurückgegebenen `java.util.List`-Objekt enthalten.

1. Dekodierte Daten verarbeiten

   * Durchsuchen Sie das `java.util.List`-Objekt, um jedes `org.w3c.dom.Document`-Objekt zu erhalten, das sich in der Liste befindet.
   * Konvertieren Sie für jedes Element in der Liste das `org.w3c.dom.Document`-Objekt in ein `com.adobe.idp.Document`-Objekt. (Die Anwendungslogik, die ein `org.w3c.dom.Document`-Objekt in ein `com.adobe.idp.Document`-Objekt konvertiert, wird unter Dekodieren von mit Strichcode versehenen Formulardaten mithilfe des Java-API-Beispiels angezeigt.)
   * Speichern Sie die XML-Daten als XML-Datei, indem Sie das `com.adobe.idp.Document`-Objekt `copyToFile` aufrufen und ein File-Objekt übergeben, das die XML-Datei darstellt.

**Siehe auch**

[Schnellstart (SOAP-Modus): Dekodieren von mit Strichcode versehenen Formulardaten mit der Java-API](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Dekodieren von mit Strichcode versehenen Formulardaten mithilfe der Webdienst-API {#decode-barcoded-form-data-using-the-web-service-api}

Dekodieren Sie Formulardaten mithilfe der Barcoded Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Barcoded Forms-Dienst-WSDL verwendet. Weitere Informationen finden Sie unter [AEM Forms mit Base64-Codierung aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. Weitere Informationen finden Sie unter &quot;Referenzieren der .NET-Clientassembly&quot;in [Aufrufen von AEM Forms mit Base64-Codierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Client-API-Objekt für Barcoded forms erstellen

   Erstellen Sie mit der Microsoft .NET-Client-Assembly, die die WSDL des Barcoded Forms-Dienstes verwendet, ein `BarcodedFormsServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.

1. PDF-Formular mit Barcodedaten abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das einen Barcode enthält.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `binaryData`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Daten aus dem PDF-Formular dekodieren

   Dekodieren Sie die Formulardaten, indem Sie die `decode` -Methode des Objekts `BarcodedFormsServiceService` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Formular enthält.
   * Ein `Boolean` -Objekt, das angibt, ob ein PDF417-Barcode dekodiert werden soll.
   * Ein `Boolean` -Objekt, das angibt, ob ein Datenmatrix-Barcode dekodiert werden soll.
   * Ein `Boolean` -Objekt, das angibt, ob ein QR-Code-Barcode dekodiert werden soll.
   * Ein `Boolean` -Objekt, das angibt, ob ein Codabar-Barcode dekodiert werden soll.
   * Ein `Boolean` -Objekt, das angibt, ob ein Code-128-Barcode dekodiert werden soll.
   * Ein `Bolean` -Objekt, das angibt, ob ein Code-39-Barcode dekodiert werden soll.
   * Ein `Boolean` -Objekt, das angibt, ob ein EAN-13-Barcode dekodiert werden soll.
   * Ein `Boolean` -Objekt, das angibt, ob ein EAN-8-Barcode dekodiert werden soll.
   * Ein `CharSet`-Auflistungswert, der den im Barcode verwendeten Kodierungswert für Zeichensätze angibt.

   Die `decode`-Methode gibt einen Zeichenfolgenwert zurück, der dekodierte Formulardaten enthält.

1. Daten in eine XML-Datenquelle konvertieren

   Konvertieren Sie die dekodierten Daten in XDP- oder XFDF-Daten, indem Sie die `extractToXML` -Methode des Objekts `BarcodedFormsServiceService` aufrufen und die folgenden Werte übergeben:

   * Ein string -Wert, der dekodierte Daten enthält (stellen Sie sicher, dass Sie den Rückgabewert der `decode`-Methode verwenden).
   * Ein `Delimiter` -Auflistungswert, der das Trennzeichen für die Zeile angibt. Es wird empfohlen, `Delimiter.Carriage_Return` anzugeben.
   * Ein `Delimiter` -Auflistungswert, der das Feldtrennzeichen angibt. Geben Sie beispielsweise `Delimiter.Tab` an.
   * Ein `XMLFormat`-Auflistungswert, der angibt, ob die Barcodedaten in XDP- oder XFDF-XML-Daten konvertiert werden sollen. Geben Sie beispielsweise `XMLFormat.XDP` an, um die Daten in XDP-Daten zu konvertieren.

   >[!NOTE]
   >
   >Geben Sie nicht dieselben Werte für die Parameter &quot;Zeilentrennzeichen&quot;und &quot;Feldtrennzeichen&quot;an.

   Die `extractToXML`-Methode gibt ein `Object`-Array zurück, wobei jedes Element eine `BLOB`-Instanz ist. Für jeden Barcode im Formular gibt es ein eigenes Element. Das heißt, wenn das Formular vier Barcodes enthält, sind vier Elemente im zurückgegebenen `Object`-Array enthalten.

1. Dekodierte Daten verarbeiten

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `encryptPDFUsingPassword` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
