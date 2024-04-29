---
title: Verarbeiten von übermittelten Formularen
description: Verwenden Sie den Forms-Service, um die übermittelten Daten abzurufen, die in ein interaktives Formular eingegeben wurden. Der Benutzer kann die Formulardaten in den Formaten XML, PDF und URL UTF-16 übermitteln.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 419335b2-2aae-4e83-98ff-18e61b7efa9c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '2894'
ht-degree: 100%

---

# Verarbeiten von übermittelten Formularen {#handling-submitted-forms}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Bei Web-basierten Programmen, die es dem Benutzer ermöglichen, interaktive Formulare auszufüllen, müssen die Daten an den Server zurückgesendet werden. Mithilfe des Forms-Services können Sie die Daten abrufen, die der Benutzer in ein interaktives Formular eingegeben hat. Nachdem Sie die Daten abgerufen haben, können Sie sie verarbeiten, um Ihre Geschäftsanforderungen zu erfüllen. Sie können die Daten beispielsweise in einer Datenbank speichern, an ein anderes Programm senden, an einen anderen Service senden, in einem Formularentwurf zusammenführen, in einem Webbrowser anzeigen usw.

Formulardaten werden entweder als XML- oder als PDF-Daten an den Forms-Service übermittelt. Dies ist eine Option, die in Designer festgelegt ist. Bei einem Formular, das als XML übermittelt wird, haben Sie die Möglichkeit, einzelne Felddatenwerte zu extrahieren. Das heißt, Sie können den Wert jedes Formularfelds extrahieren, den der Benutzer in das Formular eingegeben hat. Bei einem Formular, das als PDF-Daten übermittelt wird, handelt es sich um Binärdaten, nicht um XML-Daten. Sie können das Formular als PDF-Datei speichern oder an einen anderen Service senden. Wenn Sie Daten aus einem als XML übermittelten Formular extrahieren und dann die Formulardaten zum Erstellen eines PDF-Dokuments verwenden möchten, rufen Sie einen weiteren AEM Forms-Vorgang auf. (Siehe [Erstellen von PDF-Dokumenten mit übermittelten XML-Daten](/help/forms/developing/creating-pdf-documents-submitted-xml.md))

Das folgende Diagramm zeigt, wie Daten von einem interaktiven Formular, das in einem Webbrowser angezeigt wird, an ein Java-Servlet namens `HandleData` übermittelt werden.

![hs_hs_handlesubmit](assets/hs_hs_handlesubmit.png)

In der folgenden Tabelle werden die Schritte im Diagramm erläutert.

<table>
 <thead>
  <tr>
   <th><p>Schritt</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Ein Benutzer füllt ein interaktives Formular aus und klickt auf die Senden-Schaltfläche des Formulars.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Die Daten werden als XML-Daten an das Java-Servlet <code>HandleData</code> übermittelt.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Das Java-Servlet <code>HandleData</code> enthält die Anwendungslogik zum Abrufen der Daten.</p></td>
  </tr>
 </tbody>
</table>

## Behandlung von übermittelten XML-Daten {#handling-submitted-xml-data}

Wenn Formulardaten als XML übermittelt werden, können Sie XML-Daten abrufen, die die übermittelten Daten darstellen. Alle Formularfelder werden als Knoten in einem XML-Schema angezeigt. Die Knotenwerte entsprechen den vom Benutzer eingegebenen Werten. Betrachten Sie ein Darlehensformular, bei dem jedes Feld im Formular als Knoten innerhalb der XML-Daten angezeigt wird. Der Wert jedes Knotens entspricht dem Wert, den ein Benutzer ausfüllt. Angenommen, ein Benutzer füllt im Darlehensformular die Daten aus, die im folgenden Formular angezeigt werden.

![hs_hs_loanformdata](assets/hs_hs_loanformdata.png)

Die folgende Abbildung zeigt die entsprechenden XML-Daten, die mithilfe der Forms-Service-Client-API abgerufen werden.

![hs_hs_loandata](assets/hs_hs_loandata.png)

Die Felder im Darlehensformular. Diese Werte können mithilfe von Java XML-Klassen abgerufen werden.

>[!NOTE]
>
>Der Formularentwurf muss in Designer ordnungsgemäß konfiguriert sein, damit Daten als XML-Daten übermittelt werden können. Um den Formularentwurf ordnungsgemäß zum Übermitteln von XML-Daten zu konfigurieren, stellen Sie sicher, dass die Senden-Schaltfläche im Formularentwurf für das Übermitteln von XML-Daten eingestellt ist. Weitere Informationen darüber, wie Sie die Senden-Schaltfläche für das Übermitteln von XML-Daten einstellen, finden Sie unter [AEM Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de).

## Verarbeiten von übermittelten PDF-Daten {#handling-submitted-pdf-data}

Stellen Sie sich ein Web-Programm vor, das den Forms-Service aufruft. Nachdem der Forms-Service ein interaktives PDF-Formular in einem Client-Webbrowser erzeugt hat, füllt der Benutzer das Formular aus und übermittelt es als PDF-Daten zurück. Wenn der Forms-Service die PDF-Daten erhält, kann er die PDF-Daten an einen anderen Service senden oder als PDF-Datei speichern. Das folgende Diagramm zeigt den logischen Ablauf des Programms.

![hs_hs_savingforms](assets/hs_hs_savingforms.png)

Die folgende Tabelle beschreibt die Schritte in diesem Diagramm.

<table>
 <thead>
  <tr>
   <th><p>Schritt</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Eine Web-Seite enthält einen Link, der auf ein Java-Servlet zugreift, das den Forms-Service aufruft.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Der Forms-Service erzeugt ein interaktives PDF-Formular im Client-Webbrowser.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Der Benutzer füllt ein interaktives Formular aus und klickt auf eine Senden-Schaltfläche. Das Formular wird als PDF-Daten an den Forms-Service zurückgesendet. Diese Option wird in Designer festgelegt.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Der Forms-Service speichert die PDF-Daten als PDF-Datei. </p></td>
  </tr>
 </tbody>
</table>

## Verarbeiten von übermittelten URL-UTF-16-Daten {#handling-submitted-url-utf-16-data}

Wenn Formulardaten als URL-UTF-16-Daten übermittelt werden, erfordert der Client-Computer Adobe Reader oder Acrobat 8.1 oder höher. Enthält weiterhin der Formularentwurf eine Senden-Schaltfläche mit URL-codierten Daten (HTTP Post) und die Option zur Codierung der Daten ist UTF-16, muss der Formularentwurf in einem Texteditor wie Notepad geändert werden. Sie können die Codierungs-Option für die Senden-Schaltfläche entweder auf `UTF-16LE` oder auf `UTF-16BE` einstellen. Designer bietet diese Funktion nicht.

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um übermittelte Formulare zu verarbeiten:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Rufen Sie Formulardaten ab.
1. Ermitteln Sie, ob die Formularübermittlung Dateianlagen enthält.
1. Verarbeiten Sie die übermittelten Daten.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms-Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Service programmgesteuert durchführen können, müssen Sie einen Client für den Forms-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient`-Objekt. Wenn Sie die Forms-Webservice-API verwenden, erstellen Sie ein `FormsService`-Objekt.

**Abrufen von Formulardaten**

Um übermittelte Formulardaten abzurufen, rufen Sie die Methode `processFormSubmission` des `FormsServiceClient`-Objekts auf. Beim Aufrufen dieser Methode müssen Sie den Content-Typ des übermittelten Formulars angeben. Wenn Daten von einem Client-Webbrowser an den Forms-Service übermittelt werden, können sie entweder als XML- oder als PDF-Daten übermittelt werden. Um die in Formularfelder eingegebenen Daten abzurufen, können die Daten als XML-Daten übermittelt werden.

Sie können auch Formularfelder aus einem Formular abrufen, das als PDF-Daten übermittelt wurde, indem Sie die folgenden Laufzeitoptionen festlegen:

* Übergeben Sie den folgenden Wert an die Methode `processFormSubmission` als Parameter für den Content-Typ: `CONTENT_TYPE=application/pdf`.
* Setzen Sie den `PDFToXDP`-Wert des `RenderOptionsSpec`-Objekts auf `true`
* Setzen Sie den `ExportDataFormat`-Wert des `RenderOptionsSpec`-Objekts auf `XMLData`

Wenn Sie die Methode `processFormSubmission` aufrufen, geben Sie den Content-Typ des übermittelten Formulars an. In der folgenden Liste sind die anwendbaren Werte des Content-Typs aufgeführt:

* **text/xml**: Stellt den Content-Typ dar, der verwendet werden soll, wenn ein PDF-Formular Formulardaten als XML übermittelt.
* **application/x-www-form-urlencoded**: Stellt den Content-Typ dar, der verwendet werden soll, wenn ein HTML-Formular Daten als XML übermittelt.
* **application/pdf**: Stellt den Content-Typ dar, der verwendet werden soll, wenn ein PDF-Formular Daten als PDF übermittelt.

>[!NOTE]
>
>Sie werden feststellen, dass es im Abschnitt „Verarbeiten von übermittelten Formularen“ drei entsprechende Kurzanleitungen gibt. Die Kurzanleitung zur Verarbeitung von PDF-Formularen, die als PDF übermittelt wurden, mithilfe der Java-API zeigt, wie übermittelte PDF-Daten verarbeitet werden. Der in dieser Kurzanleitung angegebene Content-Typ lautet `application/pdf`. Die Kurzanleitung zur Verarbeitung von PDF-Formularen, die als XML übermittelt wurden, mithilfe der Java-API zeigt, wie übermittelte XML-Daten aus einem PDF-Formular verarbeitet werden. Der in dieser Kurzanleitung angegebene Content-Typ lautet `text/xml`. Ebenso zeigt die Kurzanleitung zur Verarbeitung von HTML-Formularen, die als XML übermittelt wurden, mithilfe der Java-API, wie übermittelte XML-Daten verarbeitet werden, die von einem HTML-Formular übermittelt wurden. Der in dieser Kurzanleitung angegebene Content-Typ ist application/x-www-form-urlencoded.

Sie rufen Formulardaten ab, die an den Forms-Service gesendet wurden, und ermitteln den Verarbeitungsstatus. Das heißt, wenn Daten an den Forms-Service übermittelt werden, bedeutet dies nicht unbedingt, dass der Forms-Service die Verarbeitung der Daten abgeschlossen hat und die Daten bereit zur Verarbeitung sind. Beispielsweise können Daten an den Forms-Service übermittelt werden, damit eine Berechnung durchgeführt werden kann. Nach Abschluss der Berechnung wird das Formular mit den angezeigten Berechnungsergebnissen an den Benutzer zurückgegeben. Bevor Sie übermittelte Daten verarbeiten, sollten Sie ermitteln, ob der Forms-Service die Verarbeitung der Daten abgeschlossen hat.

Der Forms-Service gibt die folgenden Werte zurück, um anzugeben, ob die Verarbeitung der Daten abgeschlossen ist:

* **0 (Übermitteln)**: Übermittelte Daten können verarbeitet werden.
* **1 (Berechnen)**: Der Forms-Service hat einen Berechnungsvorgang für die Daten durchgeführt, und die Ergebnisse müssen an den Benutzer zurückgegeben werden.
* **2 (Validieren)**: Der Forms-Service hat die Formulardaten validiert, und die Ergebnisse müssen an den Benutzer zurückgegeben werden.
* **3 (Weiter)**: Die aktuelle Seite hat sich mit Ergebnissen geändert, die in das Client-Programm geschrieben werden müssen.
* **4 (Zurück**): Die aktuelle Seite hat sich mit Ergebnissen geändert, die in das Client-Programm geschrieben werden müssen.

>[!NOTE]
>
>Berechnungen und Überprüfungen müssen an den Benutzer zurückgegeben werden. (Siehe [Berechnen von Formulardaten](/help/forms/developing/calculating-form-data.md#calculating-form-data).

**Ermitteln, ob die Formularübermittlung Dateianlagen enthält**

Formulare, die an den Forms-Service übermittelt werden, können Dateianhänge enthalten. Beispielsweise kann ein Benutzer mithilfe des integrierten Anlagenbereichs von Acrobat Dateianlagen auswählen, die zusammen mit dem Formular übermittelt werden sollen. Außerdem können Benutzer Dateianlagen auch über eine HTML-Symbolleiste auswählen, die mit einer HTML-Datei wiedergegeben wird.

Nachdem Sie festgestellt haben, ob ein Formular Dateianhänge enthält, können Sie die Daten verarbeiten. Sie können beispielsweise den Dateianhang im lokalen Dateisystem speichern.

>[!NOTE]
>
>Das Formular muss als PDF-Daten übermittelt werden, um Dateianhänge abzurufen. Wenn das Formular als XML-Daten übermittelt wird, werden keine Dateianlagen übermittelt.

**Verarbeiten der übermittelten Daten**

Je nach Content-Typ der übermittelten Daten können Sie die individuellen Formularfeldwerte aus den übermittelten XML-Daten extrahieren oder die übermittelten PDF-Daten als PDF-Datei speichern (oder an einen anderen Service übermitteln). Um einzelne Formularfelder zu extrahieren, konvertieren Sie übermittelte XML-Daten in eine XML-Datenquelle und rufen Sie dann XML-Datenquellenwerte mithilfe der `org.w3c.dom`-Klassen ab.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Service](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

## Verarbeiten von übermittelten Formularen mithilfe der Java-API {#handle-submitted-forms-using-the-java-api}

Verarbeiten eines übermittelten Formulars mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen von Formulardaten

   * Um Formulardaten abzurufen, die in einem Java-Servlet veröffentlicht wurden, erstellen Sie ein `com.adobe.idp.Document`-Objekt durch Verwenden seines Konstruktors und Aufrufen der Methode `getInputStream` des `javax.servlet.http.HttpServletResponse`-Objekts innerhalb des Konstruktors.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Legen Sie den Gebietsschema-Wert fest, indem Sie die Methode `setLocale` des `RenderOptionsSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschema-Wert angibt.

   >[!NOTE]
   >
   >Sie können den Forms-Service anweisen, XDP- oder XML-Daten aus übermittelten PDF-Inhalten zu erstellen, indem Sie die Methode `setPDF2XDP` des `RenderOptionsSpec`-Objekts aufrufen und `true` übergeben und außerdem `setXMLData` aufrufen und `true` übergeben. Sie können dann die Methode `getOutputXML` des `FormsResult`-Objekts aufrufen, um die XML-Daten abzurufen, die den XDP/XML-Daten entsprechen. (Das `FormsResult`-Objekt wird von der Methode `processFormSubmission` zurückgegeben, die im nächsten Unterschritt erläutert wird.)

   * Rufen Sie die Methode `processFormSubmission` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

      * Das `com.adobe.idp.Document`-Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Kopfzeilen angibt. Geben Sie den zu verarbeitenden Content-Typ an. Um XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`. Um PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/pdf`.
      * Ein Zeichenfolgenwert, der den Wert der `HTTP_USER_AGENT`-Kopfzeile angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Dieser Parameterwert ist optional.
      * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen speichert.

     Die `processFormSubmission`-Methode gibt ein `FormsResult`-Objekt aus, das die Ergebnisse der Formularübermittlung enthält.

   * Stellen Sie fest, ob der Forms-Dienst die Verarbeitung der Formulardaten abgeschlossen hat, indem Sie die `getAction`-Methode des `FormsResult`-Objekts aufrufen. Wenn diese Methode den Wert `0` zurückgibt, können die Daten verarbeitet werden.

1. Stellen Sie fest, ob die Formularübermittlung Dateianhänge enthält

   * Rufen Sie die `getAttachments`-Methode des `FormsResult`-Objekts auf. Diese Methode gibt ein `java.util.List`-Objekt aus, das Dateien enthält, die mit dem Formular gesendet wurden.
   * Iteration durch das `java.util.List`-Objekt, um zu bestimmen, ob Dateianhänge vorhanden sind. Wenn Dateianhänge vorhanden sind, ist jedes Element eine `com.adobe.idp.Document`-Instanz. Sie können die Dateianhänge speichern, indem Sie die `copyToFile`-Methode des `com.adobe.idp.Document`-Objekts aufrufen und ein `java.io.File`-Objekt übergeben.

   >[!NOTE]
   >
   >Dieser Schritt ist nur anwendbar, wenn das Formular als PDF übermittelt wird.

1. Verarbeiten der gesendeten Daten

   * Wenn der Dateninhalt vom Typ `application/vnd.adobe.xdp+xml` oder `text/xml` ist, erstellen Sie eine Anwendungslogik, um XML-Datenwerte abzurufen.

      * Erstellen Sie ein `com.adobe.idp.Document`-Objekt durch Aufrufen der `getOutputContent`-Methode des `FormsResult`-Objekts.
      * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie den `java.io.DataInputStream`-Konstruktor aufrufen und das `com.adobe.idp.Document`-Objekt übergeben.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory`-Objekt, indem Sie die `newInstance`-Methode des statischen `org.w3c.dom.DocumentBuilderFactory`-Objekts aufrufen.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilder`-Objekt, indem Sie die `newDocumentBuilder`-Methode des `org.w3c.dom.DocumentBuilderFactory`-Objekts aufrufen.
      * Erstellen Sie ein `org.w3c.dom.Document`-Objekt, indem Sie die `parse`-Methode des `org.w3c.dom.DocumentBuilder`-Objekts aufrufen und das `java.io.InputStream`-Objekt übergeben.
      * Rufen Sie den Wert jedes Knotens im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document`-Objekt und den Namen des Knotens, dessen Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgewert aus, der den Wert des Knotens darstellt. Im folgenden Code-Beispiel wird diese benutzerdefinierte Methode `getNodeText` genannt. Der Hauptteil dieser Methode wird angezeigt.

   * Wenn der Dateninhalt vom Typ `application/pdf` ist, erstellen Sie eine Anwendungslogik, um die übermittelten PDF-Daten als PDF-Datei zu speichern.

      * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `getOutputContent`-Methode des `FormsResult`-Objekts aufrufen.
      * Erstellen Sie ein `java.io.File`-Objekt mithilfe seines öffentlichen Konstruktors. Stellen Sie sicher, dass Sie PDF als Dateinamenerweiterung angeben.
      * Füllen Sie die PDF-Datei, indem Sie die `copyToFile`-Methode des `com.adobe.idp.Document`-Objekts aufrufen und das `java.io.File`-Objekt übergeben.

**Siehe auch**

[Schnellstart (SOAP-Modus): Handhabung von PDF-Formularen, die als XML mit der Java-API übermittelt wurden](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api)

[Schnellstart (SOAP-Modus): Handhabung von HTML-Formularen, die als XML mit der Java-API übermittelt wurden](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api)

[Schnellstart (SOAP-Modus): Handhabung von PDF-Formularen, die als PDF mit der Java-API übermittelt wurden](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verarbeiten gesendeter PDF-Daten mit der Web-Dienst-API {#handle-submitted-pdf-data-using-the-web-service-api}

Verarbeiten Sie ein gesendetes Formular mit der Forms-API (Web-Dienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Abrufen von Formulardaten

   * Um Formulardaten abzurufen, die in einem Java-Servlet veröffentlicht wurden, erstellen Sie ein `BLOB`-Objekt mit Hilfe seines Konstruktors.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `getInputStream`-Methode des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.ByteArrayOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und die Länge des `java.io.InputStream`-Objekts übergeben.
   * Kopieren Sie den Inhalt des `java.io.InputStream`-Objekts in das `java.io.ByteArrayOutputStream`-Objekt.
   * Erstellen Sie ein Byte-Array, indem Sie die `toByteArray`-Methode des `java.io.ByteArrayOutputStream`-Objekts aufrufen.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `setBinaryData`-Methode aufrufen und das Byte-Array als Argument übergeben.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Legen Sie den Gebietsschemawert fest, indem Sie die `setLocale`-Methode des `RenderOptionsSpec`-Objekts aufrufen und einen Zeichenfolgewert übergeben, der den Gebietsschemawert angibt.
   * Rufen Sie die `processFormSubmission`-Methode des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

      * Das `BLOB`-Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Kopfzeilen angibt. Geben Sie den zu verarbeitenden Content-Typ an. Um XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`. Um PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/pdf`.
      * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT` Kopfzeilenwert angibt; Beispiel: `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * A `RenderOptionsSpec`-Objekt, das Laufzeitoptionen speichert.
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.ShortHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `MyArrayOf_xsd_anyTypeHolder`-Objekt, das von der Methode gefüllt wird. Dieser Parameter wird zum Speichern von Dateianhängen verwendet, die zusammen mit dem Formular gesendet werden.
      * Ein leeres `FormsResultHolder`-Objekt, das von der Methode mit dem gesendeten Formular gefüllt wird.

     Die `processFormSubmission`-Methode füllt den `FormsResultHolder`-Parameter mit den Ergebnissen der Formularübermittlung.

   * Stellen Sie fest, ob der Forms-Service die Verarbeitung der Formulardaten abgeschlossen hat, indem Sie die `getAction`-Methode des `FormsResult`-Objekts aufrufen. Wenn diese Methode den Wert `0` zurückgibt, sind die Formulardaten zur Verarbeitung bereit. Sie können ein `FormsResult`-Objekt erhalten, indem Sie den Wert des `value`-Datenelements des `FormsResultHolder`-Objekts abrufen.

1. Stellen Sie fest, ob die Formularübermittlung Dateianhänge enthält

   Rufen Sie den Wert des `value`-Datenelements des `MyArrayOf_xsd_anyTypeHolder`-Objekts ab (das `MyArrayOf_xsd_anyTypeHolder`-Objekt wurde an die `processFormSubmission`-Methode übergeben). Dieses Datenelement gibt ein Array von `Objects` zurück. Jedes Element innerhalb des `Object`-Arrays ist ein `Object`, das den Dateien entspricht, die zusammen mit dem Formular eingereicht wurden. Sie können jedes Element innerhalb des Arrays abrufen und es in ein `BLOB`-Objekt umwandeln.

1. Verarbeiten der gesendeten Daten

   * Wenn der Dateninhalt vom Typ `application/vnd.adobe.xdp+xml` oder `text/xml` ist, erstellen Sie eine Anwendungslogik, um XML-Datenwerte abzurufen.

      * Erstellen Sie ein `BLOB`-Objekt, indem Sie die `getOutputContent`-Methode des `FormsResult`-Objekts aufrufen.
      * Erstellen Sie ein Byte-Array, indem Sie die `getBinaryData`-Methode des `BLOB`-Objekts aufrufen.
      * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie den `java.io.ByteArrayInputStream`-Konstruktor aufrufen und das Byte-Array übergeben.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory`-Objekt, indem Sie die `newInstance`-Methode des statischen `org.w3c.dom.DocumentBuilderFactory`-Objekts aufrufen.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilder`-Objekt, indem Sie die `newDocumentBuilder`-Methode des `org.w3c.dom.DocumentBuilderFactory`-Objekts aufrufen.
      * Erstellen Sie ein `org.w3c.dom.Document`-Objekt, indem Sie die `parse`-Methode des `org.w3c.dom.DocumentBuilder`-Objekts aufrufen und das `java.io.InputStream`-Objekt übergeben.
      * Rufen Sie den Wert jedes Knotens im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document`-Objekt und den Namen des Knotens, dessen Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgewert aus, der den Wert des Knotens darstellt. Im folgenden Code-Beispiel wird diese benutzerdefinierte Methode `getNodeText` genannt. Der Hauptteil dieser Methode wird angezeigt.

   * Wenn der Dateninhalt vom Typ `application/pdf` ist, erstellen Sie eine Anwendungslogik, um die übermittelten PDF-Daten als PDF-Datei zu speichern.

      * Erstellen Sie ein `BLOB`-Objekt, indem Sie die `getOutputContent`-Methode des `FormsResult`-Objekts aufrufen.
      * Erstellen Sie ein Byte-Array, indem Sie die `getBinaryData`-Methode des `BLOB`-Objekts aufrufen.
      * Erstellen Sie ein `java.io.File`-Objekt, indem Sie seinen öffentlichen Konstruktor verwenden. Stellen Sie sicher, dass Sie PDF als Dateinamenerweiterung angeben.
      * Erstellen Sie ein `java.io.FileOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.File`-Objekt übergeben.
      * Füllen Sie die PDF-Datei, indem Sie die `write`-Methode des `java.io.FileOutputStream`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
