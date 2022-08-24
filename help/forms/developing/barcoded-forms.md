---
title: Arbeiten mit Barcode-Formularen
seo-title: Working with barcoded forms
description: Decodieren Sie Daten aus einem PDF-Formular oder einem Bild, das einen Barcode enthält, mithilfe der Java-API und der Webservice-API.
seo-description: Decode data from a PDF form or an image that contains a barcode using the Java API and Web Service API.
uuid: e56c3c94-384d-401f-b418-dd34cdc57eda
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: eb28ac30-265c-4611-8247-1f4bc826f254
role: Developer
exl-id: dd32808e-b773-48a2-90e1-7a277d349493
source-git-commit: 135f50cc80f8bb449b2f1621db5e2564f5075968
workflow-type: tm+mt
source-wordcount: '1920'
ht-degree: 99%

---

# Arbeiten mit Barcode-Formularen {#working-with-barcoded-forms}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Über den Barcode-Formular-Service {#about-the-barcoded-forms-service}

Der Barcode-Formular-Service automatisiert die Erfassung von Daten aus Formularen zum Ausfüllen und Ausdrucken und integriert die erfassten Informationen in die IT-Kernsysteme eines Unternehmens.

Mit dem Barcode-Formular-Service können Sie ein- und zweidimensionale Barcodes zu interaktiven PDF-Formularen hinzufügen. Sie können die Barcode-Formulare dann auf einer Website veröffentlichen oder per E-Mail oder CD verteilen. Wenn ein Benutzer ein Barcode-Formular mit Adobe Reader, Acrobat Professional oder Acrobat Standard ausfüllt, wird der Barcode automatisch aktualisiert, um die vom Benutzer eingegebenen Formulardaten zu codieren. Der Benutzer kann das Formular elektronisch übermitteln oder auf Papier drucken und per Post, Fax oder Hand einreichen. Sie können die vom Benutzer eingegebenen Daten später im Rahmen eines automatisierten Workflows extrahieren und die Daten zwischen Genehmigungsprozessen und Geschäftssystemen weiterleiten.

Weitere Informationen zum Barcode-Formular-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Decodieren der Daten von Barcode-Formularen {#decoding-barcoded-form-data}

Sie können die Barcode-Formular-Service-API verwenden, um Daten aus einem PDF-Formular oder einem Bild mit einem Barcode zu decodieren. Das Decodieren von Formulardaten bedeutet das Extrahieren von Daten, die im Barcode enthalten sind. Bevor Daten aus einem PDF-Formular (oder Bild) decodiert werden können, muss ein Benutzer das Formular mit Daten ausfüllen.

>[!NOTE]
>
>Weitere Informationen zum Barcode-Formular-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um Daten aus einem PDF-Formular zu decodieren, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Client-API-Objekt für Barcode-Formulare.
1. Rufen Sie ein PDF-Formular ab, das mit Barcodes versehene Daten enthält.
1. Decodieren Sie die Daten aus dem PDF-Formular.
1. Konvertieren Sie die Daten in eine XML-Datenquelle.
1. Verarbeiten Sie die decodierten Daten.

**Projektdateien einbeziehen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* xercesImpl.jar (unter &lt;Installationsverzeichnis>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdparty)

Wenn AEM Forms auf einem unterstützten J2EE-Programm-Server bereitgestellt wird, bei dem es sich nicht um JBoss handelt, müssen Sie die Dateien „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Programm-Server sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Client-API-Objekts für Barcode-Formulare**

Bevor Sie einen Barcode-Formular-Service-Vorgang programmgesteuert durchführen können, müssen Sie einen Client für den Barcode-Formular-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `BarcodedFormsServiceClient`-Objekt. Wenn Sie die Barcode-Formular-Webservice-API verwenden, erstellen Sie ein `BarcodedFormsServiceService`-Objekt.

**Abrufen eines PDF-Formulars, das mit Barcodes versehene Daten enthält**

Sie müssen ein PDF-Formular mit einem Barcode abrufen, der mit Benutzerdaten ausgefüllt wurde.

**Decodieren der Daten aus dem PDF-Formular**

Nachdem Sie ein PDF-Formular (oder ein Bild) mit einem Barcode erhalten haben, können Sie Daten decodieren. Der Barcode-Formular-Service unterstützt die folgenden Barcode-Typen:

* PDF417-Barcodes.
* Datenmatrix-Barcodes.
* QR-Code-Barcodes.
* Codabar-Barcodes.
* Code 128-Barcodes.
* Code 39-Barcodes.
* EAN-13-Barcodes.
* EAN-8-Barcodes.

Die Eingabe des Zeichensatzes als Hexadezimalwert in der Decodierungs-API bedeutet, dass der Inhalt des Barcodes als hexadezimale Zeichenfolge codiert wird. Wenn beispielsweise UTF-8 als Codierung der Zeichen im Formular und Hex im Decodierungsvorgang angegeben ist, wird der Inhalt des Barcodes als hexadezimale Zeichenfolge im Element &lt;`xb:content`> in der decodierten Ausgabe codiert. Sie können diesen Hexadezimalwert konvertieren, um den ursprünglichen Inhalt zu erhalten, indem Sie eine Anwendungslogik in Ihrem Client-Programm erstellen.

**Konvertieren der Daten in eine XML-Datenquelle**

Nachdem Sie Formulardaten decodiert haben, können Sie sie in XDP- oder XFDF-Daten konvertieren. Angenommen, Sie möchten die Daten in ein anderes Formular importieren. Um die Daten in ein XFA-Formular zu importieren, müssen Sie die Daten in XDP-Daten konvertieren. Weitere Informationen finden Sie unter [Importieren von Formulardaten](/help/forms/developing/importing-exporting-data.md#importing-form-data).

**Verarbeiten der dekodierten Daten**

Sie können die konvertierten Daten verarbeiten, um Ihre Geschäftsanforderungen zu erfüllen. Nachdem Sie beispielsweise die Daten decodiert und konvertiert haben, können Sie sie in einer Datei speichern, in einer Unternehmensdatenbank speichern, ein anderes Formular ausfüllen usw. In diesem Abschnitt wird beschrieben, wie Sie die konvertierten Daten als XML-Datei speichern.

>[!NOTE]
>
>Der Barcode-Formular-Service kann Barcode-Daten nicht decodieren, wenn die Parameter der Trennzeichen für Zeilen und Felder denselben Wert haben

**Siehe auch**

[Decodieren von mit Barcode versehenen Formulardaten mit der Java-API](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[Dekodieren von mit Barcode versehenen Formulardaten mithilfe der Webservice-API](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Decodieren von mit Barcode versehenen Formulardaten mit der Java-API {#decode-barcoded-form-data-using-the-java-api}

So decodieren Sie Formulardaten mithilfe der Barcode-Formulare-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Client-API-Objekts für Barcode-Formulare

   Erstellen Sie ein `BarcodedFormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Abrufen eines PDF-Formulars mit Barcode-Daten

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Formular darstellt, welches Barcode-Daten enthält, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Decodieren der Daten aus dem PDF-Formular

   Decodieren Sie die Formulardaten, indem Sie die Methode `decode` des `BarcodedFormsServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Formular enthält.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein PDF417-Barcode decodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das, das angibt, ob ein Datenmatrix-Barcode decodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein QR-Code-Barcode decodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein Codabar-Barcode decodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein Code-128-Barcode decodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein Code-39-Barcode decodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein EAN-13-Barcode decodiert werden soll.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob ein EAN-8-Barcode decodiert werden soll.
   * Ein `com.adobe.livecycle.barcodedforms.CharSet`-Auflistungswert, der den im Barcode verwendeten Wert für die Codierung des Zeichensatzes angibt.

   Die Methode `decode` gibt ein `org.w3c.dom.Document`-Objekt zurück, das decodierte Formulardaten enthält.

1. Konvertieren der Daten in eine XML-Datenquelle

   Konvertieren Sie die decodierten Daten entweder in XDP- oder in XFDF-Daten, indem Sie die Methode `extractToXML` des `BarcodedFormsServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `org.w3c.dom.Document`-Objekt, das die decodierten Daten enthält (stellen Sie sicher, dass Sie den Rückgabewert der Methode `decode` verwenden).
   * Ein `com.adobe.livecycle.barcodedforms.Delimiter`-Auflistungswert, der das Trennzeichen für die Zeile angibt. Es wird empfohlen, `Delimiter.Carriage_Return` anzugeben.
   * Ein `com.adobe.livecycle.barcodedforms.Delimiter`-Auflistungswert, der das Feldtrennzeichen angibt. Geben Sie zum Beispiel `Delimiter.Tab` an.
   * Ein `com.adobe.livecycle.barcodedforms.XMLFormat`-Auflistungswert, der angibt, ob die Barcode-Daten in XDP- oder XFDF-XML-Daten konvertiert werden sollen. Geben Sie beispielsweise `XMLFormat.XDP` an, um die Daten in XDP-Daten zu konvertieren.

   >[!NOTE]
   >
   >Geben Sie nicht dieselben Werte für die Parameter „Zeilentrennzeichen“ und „Feldtrennzeichen“ an.

   Die Methode `extractToXML` gibt ein `java.util.List`-Objekt zurück, bei dem jedes Element ein `org.w3c.dom.Document`-Objekt ist. Für jeden Barcode im Formular gibt es ein eigenes Element. Das heißt, wenn das Formular vier Barcodes enthält, gibt es vier Elemente im zurückgegebenen `java.util.List`-Objekt.

1. Verarbeiten der decodierten Daten

   * Iterieren Sie durch das `java.util.List`-Objekt, um jedes `org.w3c.dom.Document`-Objekt zu erhalten, das sich in der Liste befindet.
   * Konvertieren Sie für jedes Element in der Liste das `org.w3c.dom.Document`-Objekt in ein `com.adobe.idp.Document`-Objekt. (Die Anwendungslogik, die ein `org.w3c.dom.Document`-Objekt in ein `com.adobe.idp.Document`-Objekt umwandelt, wird im Beispiel zum Dekodieren von Barcode-Formulardaten mithilfe der Java-API gezeigt).
   * Speichern Sie die XML-Daten als XML-Datei, indem Sie `copyToFile` des `com.adobe.idp.Document`-Objekts aufrufen und ein Dateiobjekt übergeben, das die XML-Datei darstellt.

**Siehe auch**

[Schnellstart (SOAP-Modus): Dekodieren von Barcode-Formulardaten mithilfe der Java-API](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Dekodieren von mit Barcode versehenen Formulardaten mithilfe der Webservice-API {#decode-barcoded-form-data-using-the-web-service-api}

Dekodieren Sie Formulardaten mithilfe der Barcode-Formulare-API (Web-Service):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Barcode-Fomulare-Service-WSDL verwendet. Weitere Informationen finden Sie unter [Aufrufen von AEM Forms mithilfe von Base64-Codierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).
   * Referenzieren Sie die Microsoft .NET-Client-Assembly. Weitere Informationen finden Sie unter &quot;Referenzieren der .NET-Clientassembly&quot;in [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Erstellen eines Client-API-Objekts für Barcode-Formulare

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly, die die WSDL des Barcode-Formular-Services verwendet, ein `BarcodedFormsServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.

1. Abrufen eines PDF-Formulars mit Barcode-Daten

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das einen Barcode enthält.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `binaryData`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Decodieren der Daten aus dem PDF-Formular

   Decodieren Sie die Formulardaten, indem Sie die Methode `decode` des `BarcodedFormsServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Formular enthält.
   * Ein `Boolean`-Objekt, das angibt, ob ein PDF417-Barcode decodiert werden soll.
   * Ein `Boolean`-Objekt, das, das angibt, ob ein Datenmatrix-Barcode decodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein QR-Code-Barcode decodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein Codabar-Barcode decodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein Code-128-Barcode decodiert werden soll.
   * Ein `Bolean`-Objekt, das angibt, ob ein Code-39-Barcode decodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein EAN-13-Barcode decodiert werden soll.
   * Ein `Boolean`-Objekt, das angibt, ob ein EAN-8-Barcode decodiert werden soll.
   * Ein `CharSet`-Auflistungswert, der den im Barcode verwendeten Wert für die Codierung des Zeichensatzes angibt.

   Die Methode `decode` gibt einen Zeichenfolgenwert zurück, der decodierte Formulardaten enthält.

1. Konvertieren der Daten in eine XML-Datenquelle

   Konvertieren Sie die decodierten Daten entweder in XDP- oder in XFDF-Daten, indem Sie die Methode `extractToXML` des `BarcodedFormsServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der decodierte Daten enthält (stellen Sie sicher, dass Sie den Rückgabewert der Methode `decode` verwenden).
   * Ein `Delimiter`-Auflistungswert, der das Trennzeichen für die Zeile angibt. Es wird empfohlen, `Delimiter.Carriage_Return` anzugeben.
   * Ein `Delimiter`-Auflistungswert, der das Feldtrennzeichen angibt. Geben Sie zum Beispiel `Delimiter.Tab` an.
   * Ein `XMLFormat`-Auflistungswert, der angibt, ob die Barcode-Daten in XDP- oder XFDF-XML-Daten konvertiert werden sollen. Geben Sie beispielsweise `XMLFormat.XDP` an, um die Daten in XDP-Daten zu konvertieren.

   >[!NOTE]
   >
   >Geben Sie nicht dieselben Werte für die Parameter „Zeilentrennzeichen“ und „Feldtrennzeichen“ an.

   Die Methode `extractToXML` gibt ein `Object`-Array zurück, bei dem jedes Element eine `BLOB`-Instanz ist. Für jeden Barcode im Formular gibt es ein eigenes Element. Das heißt, wenn es vier Barcodes auf dem Formular gibt, dann befinden sich vier Elemente in dem zurückgegebenen `Object`-Array.

1. Verarbeiten der decodierten Daten

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `encryptPDFUsingPassword` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `binaryData`-Datenelements des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
