---
title: Optimieren der Leistung des Forms-Service
seo-title: Optimizing the Performance of theForms Service
description: Legen Sie Laufzeitoptionen beim Rendern eines Formulars fest und speichern Sie XDP-Dateien im Repository, um die Leistung des Forms-Service zu optimieren.
seo-description: Set run-time options when rendering a form and store XDP files in the repository to optimize the performance of the Forms service.
uuid: 9040c09a-e5d0-432b-b1c5-ad46ab57c4fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f883483-b81e-42c6-a4a1-eb499dd112e7
role: Developer
exl-id: 5a746c6c-bf6e-4b25-ba7c-a35edb1f55f3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1431'
ht-degree: 100%

---

# Optimieren der Leistung des Forms-Service {#optimizing-the-performance-of-theforms-service}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Optimieren der Leistung des Forms-Service {#optimizing-the-performance-of-the-forms-service}

Beim Rendern eines Formulars können Sie Laufzeitoptionen festlegen, die die Leistung des Forms-Service optimieren. Eine weitere Möglichkeit zur Verbesserung der Leistung des Forms-Service ist das Speichern von XDP-Dateien im Repository. In diesem Abschnitt wird jedoch nicht beschrieben, wie diese Aufgabe ausgeführt wird. (Siehe [Aufrufen eines Service mithilfe einer Java-Client-Bibliothek](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)).

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um die Leistung des Forms-Service beim Rendern eines Formulars zu optimieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Legen Sie leistungsbezogene Laufzeitoptionen fest.
1. Geben Sie das Formular wieder.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einbeziehen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Objekts für die Forms Client API**

Bevor Sie einen Client-API-Vorgang für den Forms-Service programmgesteuert durchführen können, müssen Sie einen Client für den Forms-Service erstellen. Wenn Sie die Java API verwenden, erstellen Sie ein `FormsServiceClient`-Objekt. Wenn Sie die Web-Service-API für Forms verwenden, erstellen Sie ein `FormsService`-Objekt.

**Festlegen von leistungsbezogenen Laufzeitoptionen**

Sie können die folgenden leistungsbezogenen Laufzeitoptionen festlegen, um die Leistung des Forms-Service zu verbessern:

* **Formular-Caching**: Sie können ein Formular zwischenspeichern, das im Servercache als PDF gerendert wird. Jedes Formular wird zwischengespeichert, nachdem es zum ersten Mal generiert wurde. Wenn bei einem nachfolgenden Render-Vorgang das zwischengespeicherte Formular neuer ist als der Zeitstempel des Formularentwurfs, wird das Formular aus dem Cache abgerufen. Durch das Caching von Formularen verbessern Sie die Leistung des Forms-Service, da das Formular-Design nicht aus einem Repository abgerufen werden muss.
* Das Rendering von Formularleitfäden (veraltet) kann länger dauern als die Wiedergabe anderer Umwandlungstypen. Es wird empfohlen, Formularleitfäden (veraltet) zwischenzuspeichern, um die Leistung zu verbessern.
* **Option für eigenständige Formulare**: Wenn der Forms-Service keine serverseitigen Berechnungen durchführen muss, können Sie diese Option auf `true` setzen, wodurch Formulare ohne Statusinformationen wiedergegeben werden. Statusinformationen sind erforderlich, wenn Sie ein interaktives Formular an einen Endbenutzer rendern möchten, der dann Informationen in das Formular eingibt und das Formular an den Forms-Service zurücksendet. Der Forms-Dienst führt anschließend eine Berechnung durch und gibt das Formular mit im Formular angezeigten Ergebnissen an den Benutzer zurück. Wenn ein Formular ohne Statusinformationen an den Forms-Service zurückgesendet wird, sind nur die XML-Daten verfügbar und serverseitige Berechnungen werden nicht durchgeführt.
* **Linearisierte PDFs**: Ein linearisiertes PDF-Dokument ist so organisiert, dass es inkrementellen Zugriff in einer Netzwerkumgebung ermöglicht. Die PDF-Datei ist in jeder Hinsicht gültig und mit allen vorhandenen Viewern und anderen PDF-Anwendungen kompatibel. Das heißt, dass eine linearisierte PDF angezeigt werden kann, während sie noch heruntergeladen wird.
* Diese Option verbessert nicht die Leistung, wenn ein PDF-Formular auf dem Client wiedergegeben wird.
* **GuideRSL-Option**: Aktiviert die Erstellung von Formularleitfäden (veraltet) mithilfe von freigegebenen Laufzeitbibliotheken. Das bedeutet, dass die erste Anfrage eine kleinere SWF-Datei sowie größere gemeinsame Bibliotheken herunterlädt, die im Browsercache gespeichert sind. Weitere Informationen finden Sie unter RSL in der Flex-Dokumentation.
* Sie können die Leistung des Forms-Service auch verbessern, indem Sie ein Formular auf dem Client wiedergeben. (Siehe [Rendern von Formularen auf dem Client](/help/forms/developing/rendering-forms-client.md).)

**Rendern des Formulars**

Um das Formular nach dem Festlegen von Leistungsoptionen wiederzugeben, verwenden Sie dieselbe Anwendungslogik wie für die Wiedergabe eines Formulars ohne Leistungsoptionen.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Nachdem der Forms-Service ein Formular gerendert hat, wird ein Formulardaten-Stream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Sobald das Formular in den Client-Webbrowser geschrieben wurde, ist es für den Benutzer sichtbar.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Formularen als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Optimieren der Leistung mithilfe der Java API {#optimize-the-performance-using-the-java-api}

Rendern eines Formulars mit optimierter Leistung mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen von leistungsbezogenen Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Formular-Cache-Option fest, indem Sie die Methode `setCacheEnabled` des `PDFFormRenderSpec`-Objekts aufrufen und `true` übergeben.
   * Legen Sie die Option „linearisiert“ fest, indem Sie die Methode `PDFFormRenderSpec` des Objekts `setLinearizedPDF` aufrufen und `true.` übergeben.

1. Wiedergeben des Formulars

   Rufen Sie die `renderPDFForm`-Methode des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs angibt, einschließlich der Dateinamenerweiterung.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein Objekt vom Typ `PDFFormRenderSpec`, das Laufzeitoptionen speichert, um die Leistung zu verbessern.
   * Ein Objekt vom Typ `URLSpec`, das URI-Werte enthält, die für den Forms-Service erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Hierbei handelt es sich um einen optionalen Parameter, und Sie können `null` vorgeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Senden eines Formulardatenstroms an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt durch Aufrufen der `getOutputContent`-Methode des `FormsResult`-Objekts.
   * Erstellen Sie ein `java.io.InputStream`-Objekt durch Aufrufen der `getInputStream`-Methode des `com.adobe.idp.Document`-Objekts.
   * Erstellen Sie ein Byte-Array und befüllen Sie es mit dem Formulardatenstrom, indem Sie die `read`-Methode des `InputStream`-Objekts aufrufen und das Byte-Array als Argument übergeben.
   * Um den Formulardatenstrom an den Client-Webbrowser zu senden, rufen Sie die `write`-Methode des `javax.servlet.ServletOutputStream`-Objekts auf. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Optimieren der Leistung mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Optimieren der Leistung mithilfe der Web-Service-API {#optimize-the-performance-using-the-web-service-api}

Wiedergeben eines Formulars mit optimierter Leistung mithilfe der Forms-API (Web-Service):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Leistungsoptionen bezüglich der Laufzeit

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option „Formular-Cache“ fest, indem Sie die `setCacheEnabled`-Methode des `PDFFormRenderSpec`-Objekts aufrufen und „true“ übergeben.
   * Legen Sie die Option „eigenständig“ fest, indem Sie die `setStandAlone`-Methode des `PDFFormRenderSpec`-Objekts aufrufen und „true“ übergeben.
   * Legen Sie die Option „linearisiert“ fest, indem Sie die `setLinearizedPDF`-Methode des `PDFFormRenderSpec`-Objekts aufrufen und „true“ übergeben.

1. Wiedergeben des Formulars

   Rufen Sie die `renderPDFForm`-Methode des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs angibt, einschließlich der Dateinamenerweiterung.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Ein `PDFFormRenderSpecc`-Objekt, das Laufzeitoptionen speichert.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Service erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Hierbei handelt es sich um einen optionalen Parameter, und Sie können `null` vorgeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das durch die Methode befüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das durch die Methode befüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular).
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das durch die Methode befüllt wird. (Dieses Argument speichert den Gebietsschemawert).
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthalten wird.

   Durch die `renderPDFForm`-Methode wird das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt befüllt, das als letzter Argumentwert mit einem Formulardatenstrom übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt durch Abrufen des Werts des `value`-Daten-Members des `com.adobe.idp.services.holders.FormsResultHolder`-Objekts.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Senden eines Formulardatenstroms an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, durch Aufrufen der `getOutputContent`-Methode des `FormsResult`-Objekts.
   * Erstellen Sie ein Byte-Array und befüllen Sie es durch Aufrufen der `getBinaryData`-Methode des `BLOB`-Objekts. Diese Aufgabe weist den Inhalt des `FormsResult`-Objekts dem Byte-Array zu.
   * Um den Formulardatenstrom an den Client-Webbrowser zu senden, rufen Sie die `write`-Methode des `javax.servlet.http.HttpServletResponse`-Objekts auf. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
