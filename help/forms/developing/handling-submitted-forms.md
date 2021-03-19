---
title: Bearbeitung von übermittelten Forms
seo-title: Bearbeitung von übermittelten Forms
description: Mit dem Forms-Dienst können Sie die gesendeten Daten abrufen, die in ein interaktives Formular eingegeben wurden. Der Benutzer kann die Formulardaten in den Formaten XML, PDF und URL UTF-16 senden.
seo-description: Mit dem Forms-Dienst können Sie die gesendeten Daten abrufen, die in ein interaktives Formular eingegeben wurden. Der Benutzer kann die Formulardaten in den Formaten XML, PDF und URL UTF-16 senden.
uuid: 673b28f1-f023-4da8-a6a0-c5ff921c5f5d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 3d838027-6bde-4a71-a428-4d5102f7d799
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2936'
ht-degree: 2%

---


# Bearbeitung von übermittelten Forms {#handling-submitted-forms}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Webbasierte Anwendungen, die es einem Benutzer ermöglichen, interaktive Formulare auszufüllen, erfordern, dass die Daten an den Server zurückgesendet werden. Mit dem Forms-Dienst können Sie die Daten abrufen, die der Benutzer in ein interaktives Formular eingegeben hat. Nachdem Sie die Daten abgerufen haben, können Sie die Daten entsprechend Ihren Geschäftsanforderungen verarbeiten. Sie können beispielsweise die Daten in einer Datenbank speichern, die Daten an eine andere Anwendung senden, die Daten an einen anderen Dienst senden, die Daten in einem Formularentwurf zusammenführen, die Daten in einem Webbrowser anzeigen usw.

Formulardaten werden entweder als XML- oder als PDF-Daten an den Forms-Dienst gesendet. Dies ist eine Option, die in Designer festgelegt ist. Mit einem als XML gesendeten Formular können Sie einzelne Felddatenwerte extrahieren. Das heißt, Sie können den Wert jedes Formularfelds extrahieren, das der Benutzer in das Formular eingegeben hat. Ein Formular, das als PDF-Daten übermittelt wird, sind Binärdaten, nicht XML-Daten. Sie können das Formular als PDF-Datei speichern oder an einen anderen Dienst senden. Wenn Sie Daten aus einem als XML gesendeten Formular extrahieren und dann mithilfe der Formulardaten ein PDF-Dokument erstellen möchten, rufen Sie einen anderen AEM Forms-Vorgang auf. (Siehe [Erstellen von PDF-Dokumenten mit übermittelten XML-Daten](/help/forms/developing/creating-pdf-documents-submitted-xml.md))

Das folgende Diagramm zeigt Daten, die von einem interaktiven Formular in einem Webbrowser an ein Java-Servlet mit dem Namen `HandleData` gesendet werden.

![hs_hs_handlesubmit](assets/hs_hs_handlesubmit.png)

Die folgende Tabelle beschreibt die Schritte im Diagramm.

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
   <td><p>Daten werden als XML-Daten an das Java-Servlet <code>HandleData</code> gesendet.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Das Java-Servlet <code>HandleData</code> enthält Anwendungslogik zum Abrufen der Daten.</p></td>
  </tr>
 </tbody>
</table>

## Verarbeiten gesendeter XML-Daten {#handling-submitted-xml-data}

Wenn Formulardaten als XML gesendet werden, können Sie XML-Daten abrufen, die die gesendeten Daten repräsentieren. Alle Formularfelder werden als Nodes in einem XML-Schema angezeigt. Die Knotenwerte entsprechen den Werten, die der Benutzer ausgefüllt hat. Angenommen, jedes Feld im Formular wird als Node in den XML-Daten angezeigt. Der Wert jeder Node entspricht dem Wert, den ein Benutzer ausfüllt. Angenommen, ein Benutzer füllt das Kreditformular mit Daten, die im folgenden Formular angezeigt werden.

![hs_hs_loanformdata](assets/hs_hs_loanformdata.png)

Die folgende Abbildung zeigt die entsprechenden XML-Daten, die mithilfe der Forms-Dienst-Client-API abgerufen werden.

![hs_hs_loandata](assets/hs_hs_loandata.png)

Die Felder im Kreditformular. Diese Werte können abgerufen werden
Java XML-Klassen verwenden.

>[!NOTE]
>
>Der Formularentwurf muss in Designer korrekt konfiguriert sein, damit Daten als XML-Daten gesendet werden. Um den Formularentwurf für die Übermittlung von XML-Daten ordnungsgemäß zu konfigurieren, stellen Sie sicher, dass die Senden-Schaltfläche im Formularentwurf auf Senden von XML-Daten eingestellt ist. Informationen zum Festlegen der Senden-Schaltfläche zum Senden von XML-Daten finden Sie unter [AEM Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

## Verarbeiten gesendeter PDF-Daten {#handling-submitted-pdf-data}

Betrachten Sie eine Webanwendung, die den Forms-Dienst aufruft. Nachdem der Forms-Dienst ein interaktives PDF-Formular an einen Client-Webbrowser gerendert hat, füllt der Benutzer das Formular aus und sendet es als PDF-Daten zurück. Wenn der Forms-Dienst die PDF-Daten empfängt, kann er die PDF-Daten an einen anderen Dienst senden oder als PDF-Datei speichern. Das folgende Diagramm zeigt den logischen Ablauf der Anwendung.

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
   <td><p>Eine Webseite enthält einen Link, der auf ein Java-Servlet zugreift, das den Forms-Dienst aufruft.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Der Forms-Dienst rendert ein interaktives PDF-Formular im Client-Webbrowser.</p></td>
  </tr>
  <tr>
   <td><p>1</p></td>
   <td><p>Der Benutzer füllt ein interaktives Formular aus und klickt auf eine Senden-Schaltfläche. Das Formular wird als PDF-Daten an den Forms-Dienst zurückgesendet. Diese Option ist in Designer festgelegt.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Der Forms-Dienst speichert die PDF-Daten als PDF-Datei. </p></td>
  </tr>
 </tbody>
</table>

## Verarbeiten gesendeter URL UTF-16-Daten {#handling-submitted-url-utf-16-data}

Wenn Formulardaten als URL-UTF-16-Daten übermittelt werden, erfordert der Clientcomputer Adobe Reader oder Acrobat 8.1 oder höher. Enthält der Formularentwurf eine Senden-Schaltfläche mit URL-kodierten Daten (HTTP Post) und die Datenkodierungsoption UTF-16, muss der Formularentwurf in einem Texteditor wie Notepad geändert werden. Sie können die Kodierungsoption für die Senden-Schaltfläche entweder auf `UTF-16LE` oder auf `UTF-16BE` setzen. Designer bietet diese Funktion nicht.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So verarbeiten Sie gesendete Formulare:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Formulardaten abrufen.
1. Stellen Sie fest, ob die Formularübermittlung Dateianlagen enthält.
1. Verarbeiten Sie die gesendeten Daten.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Forms Client API-Objekt erstellen**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient`-Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsService`-Objekt.

**Formulardaten abrufen**

Um gesendete Formulardaten abzurufen, rufen Sie die `FormsServiceClient`-Methode des Objekts `processFormSubmission` auf. Beim Aufrufen dieser Methode müssen Sie den Inhaltstyp des gesendeten Formulars angeben. Wenn Daten von einem Client-Webbrowser an den Forms-Dienst gesendet werden, können sie als XML- oder PDF-Daten übermittelt werden. Zum Abrufen der in Formularfelder eingegebenen Daten können die Daten als XML-Daten gesendet werden.

Sie können Formularfelder auch aus einem als PDF-Daten gesendeten Formular abrufen, indem Sie die folgenden Laufzeitoptionen festlegen:

* Übergeben Sie den folgenden Wert als Parameter für den Inhaltstyp an die `processFormSubmission`-Methode: `CONTENT_TYPE=application/pdf`.
* Setzen Sie den Wert des Objekts `PDFToXDP` auf `true``RenderOptionsSpec`
* Setzen Sie den Wert des Objekts `ExportDataFormat` auf `XMLData``RenderOptionsSpec`

Sie geben den Inhaltstyp des gesendeten Formulars an, wenn Sie die `processFormSubmission`-Methode aufrufen. In der folgenden Liste werden die entsprechenden Inhaltstypwerte angegeben:

* **text/xml**: Stellt den Inhaltstyp dar, der verwendet wird, wenn ein PDF-Formular Formulardaten als XML sendet.
* **application/x-www-form-urlencoded**: Stellt den Inhaltstyp dar, der verwendet wird, wenn ein HTML-Formular Daten als XML sendet.
* **application/pdf**: Stellt den Inhaltstyp dar, der verwendet wird, wenn ein PDF-Formular Daten als PDF sendet.

>[!NOTE]
>
>Sie werden feststellen, dass dem Abschnitt &quot;Bearbeitung gesendet am Forms&quot;drei entsprechende schnelle Beginn zugeordnet sind. Die als PDF gesendeten PDF forms mit dem Java-API-Quick-Beginn zeigen, wie gesendete PDF-Daten verarbeitet werden. Der in diesem Quick-Beginn angegebene Inhaltstyp ist `application/pdf`. Die PDF forms, die mit dem Java-API-Quick-Beginn als XML gesendet wurden, zeigen, wie gesendete XML-Daten, die von einem PDF-Formular gesendet wurden, verarbeitet werden. Der in diesem Quick-Beginn angegebene Inhaltstyp ist `text/xml`. Gleichermaßen zeigt der Handling-HTML-Formulare, die mit dem Java-API-Quick-Beginn als XML gesendet wurden, wie gesendete XML-Daten, die von einem HTML-Formular gesendet wurden, verarbeitet werden. Der in diesem Quick-Beginn angegebene Inhaltstyp lautet application/x-www-form-urlencoded.

Sie rufen Formulardaten ab, die an den Forms-Dienst gesendet wurden, und bestimmen den Verarbeitungsstatus. Das heißt, wenn Daten an den Forms-Dienst übermittelt werden, bedeutet dies nicht unbedingt, dass der Forms-Dienst die Verarbeitung der Daten abgeschlossen hat und die Daten verarbeitet werden können. Beispielsweise können Daten an den Forms-Dienst gesendet werden, damit eine Berechnung durchgeführt werden kann. Nach Abschluss der Berechnung wird das Formular mit den angezeigten Berechnungsergebnissen an den Benutzer zurückgegeben. Bevor Sie gesendete Daten verarbeiten, sollten Sie ermitteln, ob der Forms-Dienst die Verarbeitung der Daten abgeschlossen hat.

Der Forms-Dienst gibt die folgenden Werte zurück, um anzugeben, ob die Verarbeitung der Daten abgeschlossen ist:

* **0 (Senden):** Gesendete Daten können verarbeitet werden.
* **1 (Berechnen):** Der Forms-Dienst hat einen Berechnungsvorgang für die Daten durchgeführt und die Ergebnisse müssen dem Benutzer wiedergegeben werden.
* **2 (Validieren):** Die vom Forms-Dienst validierten Formulardaten und die Ergebnisse müssen dem Benutzer wiedergegeben werden.
* **3 (Weiter):** Die aktuelle Seite hat sich mit Ergebnissen geändert, die in die Clientanwendung geschrieben werden müssen.
* **4 (Vorherige**): Die aktuelle Seite wurde geändert, und die Ergebnisse müssen in die Clientanwendung geschrieben werden.

>[!NOTE]
>
>Berechnungen und Überprüfungen müssen dem Benutzer wiedergegeben werden. (Siehe [Berechnen von Formulardaten](/help/forms/developing/calculating-form-data.md#calculating-form-data).

**Stellen Sie fest, ob die Formularübermittlung Dateianlagen enthält.**

Forms, das an den Forms-Dienst gesendet wird, kann Dateianlagen enthalten. Beispielsweise kann ein Benutzer im integrierten Anlagenbereich von Acrobat Dateianlagen auswählen, die zusammen mit dem Formular gesendet werden sollen. Außerdem kann ein Benutzer Dateianlagen auch über eine HTML-Symbolleiste auswählen, die mit einer HTML-Datei wiedergegeben wird.

Nachdem Sie festgestellt haben, ob ein Formular Dateianhänge enthält, können Sie die Daten verarbeiten. Sie können die Dateianlage beispielsweise im lokalen Dateisystem speichern.

>[!NOTE]
>
>Das Formular muss als PDF-Daten gesendet werden, um Dateianlagen abrufen zu können. Wenn das Formular als XML-Daten gesendet wird, werden keine Dateianlagen gesendet.

**Verarbeiten der gesendeten Daten**

Je nach Inhaltstyp der gesendeten Daten können Sie einzelne Formularfeldwerte aus den gesendeten XML-Daten extrahieren oder die gesendeten PDF-Daten als PDF-Datei speichern (oder an einen anderen Dienst senden). Um einzelne Formularfelder zu extrahieren, konvertieren Sie gesendete XML-Daten in eine XML-Datenquelle und rufen dann XML-Datenquellenwerte mithilfe von `org.w3c.dom`-Klassen ab.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Weiterleiten von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

## Verarbeiten gesendeter Formulare mit der Java-API {#handle-submitted-forms-using-the-java-api}

Verarbeiten Sie ein gesendetes Formular mit der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Client API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Formulardaten abrufen

   * Um Formulardaten abzurufen, die an ein Java-Servlet gesendet wurden, erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie den Konstruktor verwenden und die `javax.servlet.http.HttpServletResponse`-Objektmethode `getInputStream` aus dem Konstruktor aufrufen.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Legen Sie den Gebietsschemawert fest, indem Sie die `RenderOptionsSpec`-Methode des Objekts `setLocale` aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt.

   >[!NOTE]
   >
   >Sie können den Forms-Dienst anweisen, XDP- oder XML-Daten aus gesendeten PDF-Inhalten zu erstellen, indem Sie die `setPDF2XDP`-Methode des Objekts aufrufen und `true` übergeben und auch `setXMLData` aufrufen und `true` übergeben. `RenderOptionsSpec` Sie können dann die `FormsResult`-Methode des Objekts aufrufen, um die XML-Daten abzurufen, die den XDP-/XML-Daten entsprechen. `getOutputXML` (Das `FormsResult`-Objekt wird von der `processFormSubmission`-Methode zurückgegeben, die im nächsten Unterschritt beschrieben wird.)

   * Rufen Sie die `processFormSubmission`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

      * Das `com.adobe.idp.Document`-Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der die Umgebung einschließlich aller relevanten HTTP-Header angibt. Geben Sie den zu verwaltenden Inhaltstyp an. Um XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`. Um PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/pdf`.
      * Ein Zeichenfolgenwert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. . `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Dieser Parameterwert ist optional.
      * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen speichert.

      Die `processFormSubmission`-Methode gibt ein `FormsResult`-Objekt zurück, das die Ergebnisse der Formularübermittlung enthält.

   * Stellen Sie fest, ob die Verarbeitung der Formulardaten durch den Forms-Dienst abgeschlossen ist, indem Sie die `getAction`-Methode des Objekts aufrufen. `FormsResult` Wenn diese Methode den Wert `0` zurückgibt, können die Daten verarbeitet werden.



1. Stellen Sie fest, ob die Formularübermittlung Dateianlagen enthält.

   * Rufen Sie die `FormsResult`-Methode des Objekts `getAttachments` auf. Diese Methode gibt ein `java.util.List`-Objekt zurück, das Dateien enthält, die mit dem Formular gesendet wurden.
   * Durchlaufen Sie das `java.util.List`-Objekt, um festzustellen, ob Dateianlagen vorhanden sind. Wenn Dateianlagen vorhanden sind, ist jedes Element eine `com.adobe.idp.Document`-Instanz. Sie können die Dateianlagen speichern, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `copyToFile` aufrufen und ein `java.io.File`-Objekt übergeben.

   >[!NOTE]
   >
   >Dieser Schritt ist nur relevant, wenn das Formular als PDF gesendet wird.

1. Verarbeiten der gesendeten Daten

   * Wenn der Datentyp `application/vnd.adobe.xdp+xml` oder `text/xml` lautet, erstellen Sie eine Anwendungslogik zum Abrufen von XML-Datenwerten.

      * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode des Objekts `getOutputContent` aufrufen.
      * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie den `java.io.DataInputStream`-Konstruktor aufrufen und das `com.adobe.idp.Document`-Objekt übergeben.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory`-Objekt, indem Sie die `newInstance`-Methode des statischen `org.w3c.dom.DocumentBuilderFactory`-Objekts aufrufen.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilder`-Objekt, indem Sie die `org.w3c.dom.DocumentBuilderFactory`-Methode des Objekts `newDocumentBuilder` aufrufen.
      * Erstellen Sie ein `org.w3c.dom.Document`-Objekt, indem Sie die `org.w3c.dom.DocumentBuilder`-Methode des Objekts `parse` aufrufen und das `java.io.InputStream`-Objekt übergeben.
      * Rufen Sie den Wert jeder Node im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document`-Objekt und den Namen der Node, deren Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert der Node darstellt. Im Codebeispiel, das diesem Prozess folgt, heißt diese benutzerdefinierte Methode `getNodeText`. Der Hauptteil dieser Methode wird angezeigt.
   * Wenn der Datentyp `application/pdf` lautet, erstellen Sie eine Anwendungslogik, um die gesendeten PDF-Daten als PDF-Datei zu speichern.

      * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode des Objekts `getOutputContent` aufrufen.
      * Erstellen Sie ein `java.io.File`-Objekt mit dem öffentlichen Konstruktor. Achten Sie darauf, PDF als Dateinamenerweiterung anzugeben.
      * Füllen Sie die PDF-Datei, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `copyToFile` aufrufen und das `java.io.File`-Objekt übergeben.


**Siehe auch**

[Quick Beginn (SOAP-Modus): Umgang mit PDF forms, die als XML mit der Java-API gesendet werden](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api)

[Quick Beginn (SOAP-Modus): Verarbeiten von HTML-Formularen, die als XML gesendet werden, mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api)

[Quick Beginn (SOAP-Modus): Umgang mit PDF forms, die als PDF mit der Java-API gesendet wurden](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verarbeiten gesendeter PDF-Daten mit der Webdienst-API {#handle-submitted-pdf-data-using-the-web-service-api}

Verarbeiten Sie ein gesendetes Formular mit der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Client API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Formulardaten abrufen

   * Um Formulardaten abzurufen, die auf einem Java-Servlet veröffentlicht wurden, erstellen Sie ein `BLOB`-Objekt mit dessen Konstruktor.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `javax.servlet.http.HttpServletResponse`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein `java.io.ByteArrayOutputStream`-Objekt, indem Sie den Konstruktor verwenden und die Länge des `java.io.InputStream`-Objekts übergeben.
   * Kopieren Sie den Inhalt des Objekts `java.io.InputStream` in das Objekt `java.io.ByteArrayOutputStream`.
   * Erstellen Sie ein Bytearray, indem Sie die `java.io.ByteArrayOutputStream`-Methode des Objekts `toByteArray` aufrufen.
   * Füllen Sie das `BLOB`-Objekt, indem Sie die `setBinaryData`-Methode aufrufen und das Bytearray als Argument übergeben.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Legen Sie den Gebietsschemawert fest, indem Sie die `RenderOptionsSpec`-Methode des Objekts `setLocale` aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt.
   * Rufen Sie die `processFormSubmission`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

      * Das `BLOB`-Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der die Umgebung einschließlich aller relevanten HTTP-Header angibt. Geben Sie den zu verwaltenden Inhaltstyp an. Um XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`. Um PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/pdf`.
      * Ein Zeichenfolgenwert, der den Header-Wert `HTTP_USER_AGENT` angibt; zum Beispiel `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen speichert.
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `BLOBHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.ShortHolder`-Objekt, das von der Methode gefüllt wird.
      * Ein leeres `MyArrayOf_xsd_anyTypeHolder`-Objekt, das von der Methode gefüllt wird. Dieser Parameter wird zum Speichern von Dateianlagen verwendet, die zusammen mit dem Formular gesendet werden.
      * Ein leeres `FormsResultHolder`-Objekt, das von der Methode mit dem gesendeten Formular gefüllt wird.

      Die `processFormSubmission`-Methode füllt den Parameter `FormsResultHolder` mit den Ergebnissen der Formularübermittlung.

   * Stellen Sie fest, ob die Verarbeitung der Formulardaten durch den Forms-Dienst abgeschlossen ist, indem Sie die `getAction`-Methode des Objekts aufrufen. `FormsResult` Wenn diese Methode den Wert `0` zurückgibt, können die Formulardaten verarbeitet werden. Sie können ein `FormsResult`-Objekt abrufen, indem Sie den Wert des `FormsResultHolder`-Datenelements des Objekts `value` abrufen.


1. Stellen Sie fest, ob die Formularübermittlung Dateianlagen enthält.

   Rufen Sie den Wert des `MyArrayOf_xsd_anyTypeHolder`-Datenelements des `value`-Objekts ab (das `MyArrayOf_xsd_anyTypeHolder`-Objekt wurde an die `processFormSubmission`-Methode übergeben). Dieser Datenmember gibt ein Array von `Objects` zurück. Jedes Element im Array `Object` ist ein `Object`Element, das den Dateien entspricht, die zusammen mit dem Formular gesendet wurden. Sie können jedes Element im Array abrufen und in ein `BLOB`-Objekt umwandeln.

1. Verarbeiten der gesendeten Daten

   * Wenn der Datentyp `application/vnd.adobe.xdp+xml` oder `text/xml` lautet, erstellen Sie eine Anwendungslogik zum Abrufen von XML-Datenwerten.

      * Erstellen Sie ein `BLOB`-Objekt, indem Sie die `FormsResult`-Methode des Objekts `getOutputContent` aufrufen.
      * Erstellen Sie ein Bytearray, indem Sie die `BLOB`-Methode des Objekts `getBinaryData` aufrufen.
      * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie den `java.io.ByteArrayInputStream`-Konstruktor aufrufen und das Bytearray übergeben.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory`-Objekt, indem Sie die `newInstance`-Methode des statischen `org.w3c.dom.DocumentBuilderFactory`-Objekts aufrufen.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilder`-Objekt, indem Sie die `org.w3c.dom.DocumentBuilderFactory`-Methode des Objekts `newDocumentBuilder` aufrufen.
      * Erstellen Sie ein `org.w3c.dom.Document`-Objekt, indem Sie die `org.w3c.dom.DocumentBuilder`-Methode des Objekts `parse` aufrufen und das `java.io.InputStream`-Objekt übergeben.
      * Rufen Sie den Wert jeder Node im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document`-Objekt und den Namen der Node, deren Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert der Node darstellt. Im Codebeispiel, das diesem Prozess folgt, heißt diese benutzerdefinierte Methode `getNodeText`. Der Hauptteil dieser Methode wird angezeigt.
   * Wenn der Datentyp `application/pdf` lautet, erstellen Sie eine Anwendungslogik, um die gesendeten PDF-Daten als PDF-Datei zu speichern.

      * Erstellen Sie ein `BLOB`-Objekt, indem Sie die `FormsResult`-Methode des Objekts `getOutputContent` aufrufen.
      * Erstellen Sie ein Bytearray, indem Sie die `BLOB`-Methode des Objekts `getBinaryData` aufrufen.
      * Erstellen Sie ein `java.io.File`-Objekt mit dem öffentlichen Konstruktor. Achten Sie darauf, PDF als Dateinamenerweiterung anzugeben.
      * Erstellen Sie ein `java.io.FileOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.File`-Objekt übergeben.
      * Füllen Sie die PDF-Datei, indem Sie die `java.io.FileOutputStream`-Methode des Objekts `write` aufrufen und das Bytearray übergeben.


**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)