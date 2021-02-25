---
title: Optimieren der Leistung des Forms-Dienstes
seo-title: Optimieren der Leistung des Forms-Dienstes
description: Legen Sie Laufzeitoptionen beim Rendern eines Formulars fest und speichern Sie XDP-Dateien im Repository, um die Leistung des Forms-Dienstes zu optimieren.
seo-description: Legen Sie Laufzeitoptionen beim Rendern eines Formulars fest und speichern Sie XDP-Dateien im Repository, um die Leistung des Forms-Dienstes zu optimieren.
uuid: 9040c09a-e5d0-432b-b1c5-ad46ab57c4fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f883483-b81e-42c6-a4a1-eb499dd112e7
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '1459'
ht-degree: 6%

---


# Leistungsoptimierung des Forms-Dienstes {#optimizing-the-performance-of-theforms-service}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

## Leistungsoptimierung des Forms-Dienstes {#optimizing-the-performance-of-the-forms-service}

Beim Rendern eines Formulars können Sie Laufzeitoptionen festlegen, die die Leistung des Forms-Dienstes optimieren. Eine weitere Aufgabe, die Sie zur Leistungsverbesserung des Forms-Dienstes ausführen können, ist das Speichern von XDP-Dateien im Repository. Dieser Abschnitt beschreibt jedoch nicht, wie diese Aufgabe durchgeführt werden soll. (Siehe [Aufrufen eines Dienstes mit einer Java-Client-Bibliothek](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So optimieren Sie die Leistung des Forms-Dienstes beim Rendern eines Formulars:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Leistungslaufzeitoptionen fest.
1. Formular wiedergeben.
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Forms Client API-Objekt erstellen**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient`-Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsService`-Objekt.

**Festlegen von Leistungslaufzeitoptionen**

Sie können die folgenden Leistungslaufzeitoptionen festlegen, um die Leistung des Forms-Dienstes zu verbessern:

* **Formular-Zwischenspeicherung**: Sie können ein Formular zwischenspeichern, das als PDF im Server-Cache wiedergegeben wird. Jedes Formular wird zwischengespeichert, nachdem es zum ersten Mal generiert wurde. Wenn bei einem nachfolgenden Render-Vorgang das zwischengespeicherte Formular neuer ist als der Zeitstempel des Formularentwurfs, wird das Formular aus dem Cache abgerufen. Durch Zwischenspeichern von Formularen verbessern Sie die Leistung des Forms-Dienstes, da der Formularentwurf nicht aus einem Repository abgerufen werden muss.
* Die Wiedergabe von Formularleitfäden (nicht mehr unterstützt) kann länger dauern als bei anderen Transformationstypen. Es wird empfohlen, Formularleitfäden (nicht mehr unterstützt) im Cache zu speichern, um die Leistung zu verbessern.
* **Eigenständige Option**: Wenn Sie keine serverseitigen Berechnungen vom Forms-Dienst durchführen müssen, können Sie die Option &quot;Eigenständig&quot;auf &quot; `true`einstellen&quot;, wodurch Formulare ohne Statusinformationen wiedergegeben werden. Statusinformationen sind erforderlich, wenn Sie ein interaktives Formular an einen Endbenutzer senden möchten, der dann Informationen in das Formular eingibt und das Formular an den Forms-Dienst zurücksendet. Der Forms-Dienst führt anschließend eine Berechnung durch und gibt das Formular mit im Formular angezeigten Ergebnissen an den Benutzer zurück. Wenn ein Formular ohne Statusinformationen an den Forms-Dienst zurückgesendet wird, stehen nur die XML-Daten zur Verfügung und serverseitige Berechnungen werden nicht durchgeführt.
* **Linearisierte PDF**: Eine linearisierte PDF-Datei ist so strukturiert, dass ein effizienter inkrementeller Zugriff in einer Netzwerk-Umgebung möglich ist. Die PDF-Datei ist in jeder Hinsicht gültig und mit allen vorhandenen Viewern und anderen PDF-Anwendungen kompatibel. Das heißt, eine linearisierte PDF kann angezeigt werden, während sie noch heruntergeladen wird.
* Diese Option verbessert nicht die Leistung, wenn ein PDF-Formular auf dem Client wiedergegeben wird.
* **GuideRSL-Option**: Aktiviert die Generierung des Formularleitfadens (nicht mehr unterstützt) mit freigegebenen Laufzeitbibliotheken. Das bedeutet, dass die erste Anforderung eine kleinere SWF-Datei sowie größere gemeinsame Bibliotheken herunterlädt, die im Browsercache gespeichert sind. Weitere Informationen finden Sie unter RSL in der Flex-Dokumentation.
* Sie können auch die Leistung des Forms-Dienstes verbessern, indem Sie ein Formular auf dem Client wiedergeben. (Siehe [Rendering Forms at the Client](/help/forms/developing/rendering-forms-client.md).)

**Formular wiedergeben**

Um das Formular nach dem Festlegen der Leistungsoptionen wiederzugeben, verwenden Sie dieselbe Anwendungslogik wie beim Rendern eines Formulars ohne Leistungsoptionen.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Nachdem der Forms-Dienst ein Formular wiedergegeben hat, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interaktive PDF forms wiedergeben](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Optimieren Sie die Leistung mit der Java-API {#optimize-the-performance-using-the-java-api}.

Rendern Sie ein Formular mit optimierter Leistung mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Client API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen von Leistungslaufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option für den Formularcache fest, indem Sie die `PDFFormRenderSpec`-Methode des Objekts `setCacheEnabled` aufrufen und `true` übergeben.
   * Festlegen der linearisierten Option durch Aufrufen der `PDFFormRenderSpec`-Objektmethode `setLinearizedPDF` und Übergeben von `true.`

1. Formular wiedergeben

   Rufen Sie die `renderPDFForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert, um die Leistung zu verbessern.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es mit dem Formulardatenstream, indem Sie die `read`-Methode des Objekts aufrufen und das Bytearray als Argument übergeben.`InputStream`
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Leistungsoptimierung mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Optimieren Sie die Leistung mithilfe der Webdienst-API {#optimize-the-performance-using-the-web-service-api}.

Rendern Sie ein Formular mit optimierter Leistung mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Client API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Leistungslaufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option für den Formular-Cache fest, indem Sie die `PDFFormRenderSpec`-Methode des Objekts `setCacheEnabled` aufrufen und true übergeben.
   * Legen Sie die eigenständige Option fest, indem Sie die `PDFFormRenderSpec`-Methode des Objekts `setStandAlone` aufrufen und true übergeben.
   * Legen Sie die Option &quot;Linearisiert&quot;fest, indem Sie die `PDFFormRenderSpec`-Methode des Objekts `setLinearizedPDF` aufrufen und true übergeben.

1. Formular wiedergeben

   Rufen Sie die `renderPDFForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Ein `PDFFormRenderSpecc`-Objekt, das Laufzeitoptionen speichert.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode gefüllt wird. Auf diese Weise wird das gerenderte PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder`-Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des Objekts aufrufen.`FormsResult`
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB`-Methode des Objekts `getBinaryData`. Diese Aufgabe weist dem Bytearray den Inhalt des Objekts `FormsResult` zu.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.http.HttpServletResponse` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
