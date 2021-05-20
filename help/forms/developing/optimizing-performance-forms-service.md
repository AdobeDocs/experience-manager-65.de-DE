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
role: Developer
exl-id: 5a746c6c-bf6e-4b25-ba7c-a35edb1f55f3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1459'
ht-degree: 6%

---

# Leistungsoptimierung des Forms-Dienstes {#optimizing-the-performance-of-theforms-service}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Leistungsoptimierung des Forms-Dienstes {#optimizing-the-performance-of-the-forms-service}

Beim Rendern eines Formulars können Sie Laufzeitoptionen festlegen, die die Leistung des Forms-Dienstes optimieren. Eine weitere Aufgabe, die Sie zur Verbesserung der Leistung des Forms-Dienstes ausführen können, ist das Speichern von XDP-Dateien im Repository. In diesem Abschnitt wird jedoch nicht beschrieben, wie diese Aufgabe ausgeführt wird. (Siehe [Aufrufen eines Dienstes mit einer Java-Client-Bibliothek](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um die Leistung des Forms-Dienstes beim Rendern eines Formulars zu optimieren:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Festlegen von Leistungslaufzeitoptionen.
1. Rendern Sie das Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient` -Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsService` -Objekt.

**Festlegen von Leistungslaufzeitoptionen**

Sie können die folgenden Leistungslaufzeitoptionen festlegen, um die Leistung des Forms-Dienstes zu verbessern:

* **Formular-Zwischenspeicherung**: Sie können ein Formular zwischenspeichern, das als PDF im Server-Cache wiedergegeben wird. Jedes Formular wird zwischengespeichert, nachdem es zum ersten Mal generiert wurde. Wenn bei einem nachfolgenden Render-Vorgang das zwischengespeicherte Formular neuer ist als der Zeitstempel des Formularentwurfs, wird das Formular aus dem Cache abgerufen. Durch das Zwischenspeichern von Formularen verbessern Sie die Leistung des Forms-Dienstes, da der Formularentwurf nicht aus einem Repository abgerufen werden muss.
* Die Wiedergabe von Formularleitfäden (nicht mehr unterstützt) kann länger dauern als die Wiedergabe anderer Transformationstypen. Es wird empfohlen, Formular-Guides (nicht mehr unterstützt) zwischenzuspeichern, um die Leistung zu verbessern.
* **Eigenständige Option**: Wenn Sie nicht benötigen, dass der Forms-Dienst serverseitige Berechnungen durchführt, können Sie die Eigenschaftsoption auf  `true` setzen, was dazu führt, dass Formulare ohne Statusinformationen wiedergegeben werden. Statusinformationen sind erforderlich, wenn Sie ein interaktives Formular an einen Endbenutzer rendern möchten, der dann Informationen in das Formular eingibt und das Formular an den Forms-Dienst zurücksendet. Der Forms-Dienst führt anschließend eine Berechnung durch und gibt das Formular mit im Formular angezeigten Ergebnissen an den Benutzer zurück. Wenn ein Formular ohne Statusinformationen an den Forms-Dienst zurückgesendet wird, sind nur die XML-Daten verfügbar und serverseitige Berechnungen werden nicht durchgeführt.
* **Linearized PDF**: Eine linearisierte PDF-Datei ist so strukturiert, dass ein effizienter inkrementeller Zugriff in einer Netzwerkumgebung möglich ist. Die PDF-Datei ist in jeder Hinsicht eine gültige PDF-Datei und mit allen vorhandenen Viewern und anderen PDF-Anwendungen kompatibel. Das heißt, eine linearisierte PDF-Datei kann angezeigt werden, während sie noch heruntergeladen wird.
* Diese Option verbessert nicht die Leistung, wenn ein PDF-Formular auf dem Client wiedergegeben wird.
* **GuideRSL-Option**: Aktiviert die Erstellung des Formular-Guides (veraltet) mithilfe von freigegebenen Laufzeitbibliotheken. Das bedeutet, dass die erste Anfrage eine kleinere SWF-Datei sowie größere gemeinsame Bibliotheken herunterlädt, die im Browsercache gespeichert sind. Weitere Informationen finden Sie unter RSL in der Flex-Dokumentation.
* Sie können auch die Leistung des Forms-Dienstes verbessern, indem Sie ein Formular auf dem Client wiedergeben. (Siehe [Rendern von Forms am Client](/help/forms/developing/rendering-forms-client.md).)

**Formular wiedergeben**

Um das Formular nach dem Festlegen von Leistungsoptionen wiederzugeben, verwenden Sie dieselbe Anwendungslogik wie die Wiedergabe eines Formulars ohne Leistungsoptionen.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Nachdem der Forms-Dienst ein Formular wiedergegeben hat, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

### Optimieren Sie die Leistung mit der Java-API {#optimize-the-performance-using-the-java-api}.

Wiedergabe eines Formulars mit optimierter Leistung mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Festlegen von Leistungslaufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option für den Formular-Cache fest, indem Sie die `setCacheEnabled` -Methode des Objekts `PDFFormRenderSpec` aufrufen und `true` übergeben.
   * Legen Sie die Option für die Linearisierung fest, indem Sie die `setLinearizedPDF` -Methode des Objekts `PDFFormRenderSpec` aufrufen und `true.` übergeben.

1. Formular wiedergeben

   Rufen Sie die `renderPDFForm` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * Ein `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` -Objekt.
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert, um die Leistung zu verbessern.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `FormsResult` -Methode des Objekts &quot;s `getOutputContent` aufrufen.
   * Erstellen Sie ein `java.io.InputStream` -Objekt, indem Sie die `getInputStream` -Methode des Objekts `com.adobe.idp.Document` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `read` -Methode des Objekts `InputStream` aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.ServletOutputStream` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Leistungsoptimierung mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Optimieren Sie die Leistung mithilfe der Web-Service-API {#optimize-the-performance-using-the-web-service-api}.

Wiedergabe eines Formulars mit optimierter Leistung mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` -Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Leistungslaufzeitoptionen

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option für den Formular-Cache fest, indem Sie die Methode `setCacheEnabled` des Objekts `PDFFormRenderSpec` aufrufen und &quot;true&quot;übergeben.
   * Legen Sie die eigenständige Option fest, indem Sie die `setStandAlone` -Methode des Objekts `PDFFormRenderSpec` aufrufen und &quot;true&quot;übergeben.
   * Legen Sie die Option für die Linearisierung fest, indem Sie die `setLinearizedPDF` -Methode des Objekts `PDFFormRenderSpec` aufrufen und &quot;true&quot;übergeben.

1. Formular wiedergeben

   Rufen Sie die `renderPDFForm` -Methode des Objekts `FormsService` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * Ein `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Ein `PDFFormRenderSpecc` -Objekt, das Laufzeitoptionen speichert.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode ausgefüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode ausgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular).
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode ausgefüllt wird. (Dieses Argument speichert den Gebietsschemawert).
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` -Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` -Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `getBinaryData`-Methode des Objekts `BLOB`. Diese Aufgabe weist den Inhalt des Objekts `FormsResult` dem Byte-Array zu.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.http.HttpServletResponse` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
