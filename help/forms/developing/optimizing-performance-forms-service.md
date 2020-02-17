---
title: Optimieren der Leistung des Forms-Dienstes
seo-title: Optimieren der Leistung des Forms-Dienstes
description: 'null'
seo-description: 'null'
uuid: 9040c09a-e5d0-432b-b1c5-ad46ab57c4fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f883483-b81e-42c6-a4a1-eb499dd112e7
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Optimieren der Leistung des Forms-Dienstes {#optimizing-the-performance-of-theforms-service}

## Optimieren der Leistung des Forms-Dienstes {#optimizing-the-performance-of-the-forms-service}

Beim Rendern eines Formulars können Sie Laufzeitoptionen festlegen, die die Leistung des Forms-Dienstes optimieren. Eine weitere Aufgabe, die Sie zur Verbesserung der Leistung des Forms-Dienstes ausführen können, ist das Speichern von XDP-Dateien im Repository. In diesem Abschnitt wird jedoch nicht beschrieben, wie diese Aufgabe ausgeführt wird. (See [Invoking a service using a Java client library](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).)

>[!NOTE]
>
>For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So optimieren Sie die Leistung des Forms-Dienstes beim Rendern eines Formulars:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Leistungslaufzeitoptionen fest.
1. Formular wiedergeben.
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient` Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsService` Objekt.

**Festlegen von Leistungslaufzeitoptionen**

Sie können die folgenden Leistungslaufzeitoptionen festlegen, um die Leistung des Forms-Dienstes zu verbessern:

* **Formular-Zwischenspeicherung**: Sie können ein Formular zwischenspeichern, das als PDF im Server-Cache wiedergegeben wird. Jedes Formular wird zwischengespeichert, nachdem es zum ersten Mal generiert wurde. Wenn bei einem nachfolgenden Render-Vorgang das zwischengespeicherte Formular neuer ist als der Zeitstempel des Formularentwurfs, wird das Formular aus dem Cache abgerufen. Durch Zwischenspeichern von Formularen verbessern Sie die Leistung des Forms-Dienstes, da der Formularentwurf nicht aus einem Repository abgerufen werden muss.
* Die Wiedergabe von Formularleitfäden (nicht mehr unterstützt) kann länger dauern als bei anderen Transformationstypen. Es wird empfohlen, Formularleitfäden (nicht mehr unterstützt) im Cache zu speichern, um die Leistung zu verbessern.
* **Eigenständige Option**: Wenn der Forms-Dienst keine serverseitigen Berechnungen durchführen muss, können Sie die Option &quot;Eigenständig&quot;auf `true`einstellen, wodurch Formulare ohne Statusinformationen wiedergegeben werden. Statusinformationen sind erforderlich, wenn Sie ein interaktives Formular an einen Endbenutzer rendern möchten, der dann Informationen in das Formular eingibt und das Formular wieder an den Forms-Dienst sendet. Der Forms-Dienst führt anschließend eine Berechnung durch und gibt das Formular mit im Formular angezeigten Ergebnissen an den Benutzer zurück. Wenn ein Formular ohne Statusinformationen zurück an den Forms-Dienst gesendet wird, stehen nur die XML-Daten zur Verfügung und serverseitige Berechnungen werden nicht durchgeführt.
* **Linearisierte PDF**: Eine linearisierte PDF-Datei ist so strukturiert, dass ein effizienter inkrementeller Zugriff in einer Netzwerkumgebung möglich ist. Die PDF-Datei ist in jeder Hinsicht gültig und mit allen vorhandenen Viewern und anderen PDF-Anwendungen kompatibel. Das heißt, eine linearisierte PDF kann angezeigt werden, während sie noch heruntergeladen wird.
* Diese Option verbessert nicht die Leistung, wenn ein PDF-Formular auf dem Client wiedergegeben wird.
* **GuideRSL-Option**: Aktiviert die Generierung des Formularleitfadens (nicht mehr unterstützt) mit freigegebenen Laufzeitbibliotheken. Das bedeutet, dass die erste Anforderung eine kleinere SWF-Datei sowie größere gemeinsame Bibliotheken herunterlädt, die im Browsercache gespeichert sind. Weitere Informationen finden Sie unter RSL in der Flex-Dokumentation.
* Sie können auch die Leistung des Forms-Dienstes verbessern, indem Sie ein Formular auf dem Client wiedergeben. (Siehe [Wiedergabe von Formularen auf dem Client](/help/forms/developing/rendering-forms-client.md).)

**Formular wiedergeben**

Um das Formular nach dem Festlegen der Leistungsoptionen wiederzugeben, verwenden Sie dieselbe Anwendungslogik wie beim Rendern eines Formulars ohne Leistungsoptionen.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Nachdem der Forms-Dienst ein Formular wiedergegeben hat, wird ein Formulardatenstream zurückgegeben, den Sie an den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Wiedergeben interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Wiedergabe von Formularen als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Leistungsoptimierung mit der Java-API {#optimize-the-performance-using-the-java-api}

Rendern Sie ein Formular mit optimierter Leistung mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `FormsServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Festlegen von Leistungslaufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option zum Formular-Cache fest, indem Sie die `PDFFormRenderSpec` Methode des `setCacheEnabled` Objekts aufrufen und weitergeben `true`.
   * Festlegen der Option &quot;Linearisiert&quot;durch Aufrufen der `PDFFormRenderSpec` Objektmethode und Übergeben der `setLinearizedPDF` Methode `true.`

1. Formular wiedergeben

   Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * Ein `com.adobe.idp.Document` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` Objekt.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert, um die Leistung zu verbessern.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   Die `renderPDFForm` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` `read`Objektmethode aufrufen und das Bytearray als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Leistungsoptimierung mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Optimieren Sie die Leistung mithilfe der Webdienst-API. {#optimize-the-performance-using-the-web-service-api}

Rendern Sie ein Formular mit optimierter Leistung mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Leistungslaufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option für den Formular-Cache fest, indem Sie die `PDFFormRenderSpec` Objektmethode aufrufen und true `setCacheEnabled` übergeben.
   * Legen Sie die eigenständige Option fest, indem Sie die `PDFFormRenderSpec` Objektmethode aufrufen und &quot; `setStandAlone` true&quot;übergeben.
   * Legen Sie die Option &quot;Linearisiert&quot;fest, indem Sie die `PDFFormRenderSpec` Objektmethode aufrufen und &quot; `setLinearizedPDF` true&quot;übergeben.

1. Formular wiedergeben

   Rufen Sie die `FormsService` Objektmethode `renderPDFForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * Ein `BLOB` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Ein `PDFFormRenderSpecc` Objekt, das Laufzeitoptionen speichert.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das von der Methode gefüllt wird. Auf diese Weise wird das gerenderte PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das die Ergebnisse dieses Vorgangs enthält.
   Die `renderPDFForm` Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` Objektdatenelements abrufen `value` .
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB` Objektmethode `getBinaryData` . Diese Aufgabe weist den Inhalt des `FormsResult` Objekts dem Bytearray zu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
