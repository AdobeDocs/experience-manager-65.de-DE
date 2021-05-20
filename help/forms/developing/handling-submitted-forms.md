---
title: Umgang mit übermittelten Forms
seo-title: Umgang mit übermittelten Forms
description: Verwenden Sie den Forms-Dienst, um die gesendeten Daten abzurufen, die in ein interaktives Formular eingegeben wurden. Der Benutzer kann die Formulardaten in den Formaten XML, PDF und URL UTF-16 senden.
seo-description: Verwenden Sie den Forms-Dienst, um die gesendeten Daten abzurufen, die in ein interaktives Formular eingegeben wurden. Der Benutzer kann die Formulardaten in den Formaten XML, PDF und URL UTF-16 senden.
uuid: 673b28f1-f023-4da8-a6a0-c5ff921c5f5d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 3d838027-6bde-4a71-a428-4d5102f7d799
role: Developer
exl-id: 419335b2-2aae-4e83-98ff-18e61b7efa9c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2935'
ht-degree: 2%

---

# Umgang mit übermittelten Forms {#handling-submitted-forms}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Webbasierte Anwendungen, mit denen Benutzer interaktive Formulare ausfüllen können, erfordern, dass die Daten an den Server zurückgesendet werden. Mithilfe des Forms-Dienstes können Sie die Daten abrufen, die der Benutzer in ein interaktives Formular eingegeben hat. Nachdem Sie die Daten abgerufen haben, können Sie sie verarbeiten, um Ihre Geschäftsanforderungen zu erfüllen. Sie können beispielsweise die Daten in einer Datenbank speichern, an eine andere Anwendung senden, die Daten an einen anderen Dienst senden, die Daten in einem Formularentwurf zusammenführen, die Daten in einem Webbrowser anzeigen usw.

Formulardaten werden entweder als XML- oder PDF-Daten an den Forms-Dienst gesendet. Dies ist eine Option, die in Designer festgelegt ist. Ein Formular, das als XML gesendet wird, ermöglicht es Ihnen, einzelne Felddatenwerte zu extrahieren. Das heißt, Sie können den Wert jedes Formularfelds extrahieren, das der Benutzer in das Formular eingegeben hat. Ein Formular, das als PDF-Daten gesendet wird, sind Binärdaten, keine XML-Daten. Sie können das Formular als PDF-Datei speichern oder an einen anderen Dienst senden. Wenn Sie Daten aus einem als XML gesendeten Formular extrahieren und dann die Formulardaten zum Erstellen eines PDF-Dokuments verwenden möchten, rufen Sie einen weiteren AEM Forms-Vorgang auf. (Siehe [Erstellen von PDF-Dokumenten mit gesendeten XML-Daten](/help/forms/developing/creating-pdf-documents-submitted-xml.md))

Das folgende Diagramm zeigt Daten, die von einem interaktiven Formular in einem Webbrowser an ein Java-Servlet mit dem Namen `HandleData` gesendet werden.

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
   <td><p>Daten werden als XML-Daten an das Java-Servlet <code>HandleData</code> gesendet.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Das Java-Servlet <code>HandleData</code> enthält Anwendungslogik zum Abrufen der Daten.</p></td>
  </tr>
 </tbody>
</table>

## Verarbeiten gesendeter XML-Daten {#handling-submitted-xml-data}

Wenn Formulardaten als XML gesendet werden, können Sie XML-Daten abrufen, die die gesendeten Daten darstellen. Alle Formularfelder werden als Knoten in einem XML-Schema angezeigt. Die Knotenwerte entsprechen den vom Benutzer eingegebenen Werten. Betrachten Sie ein Kreditantrag, bei dem jedes Feld im Formular als Knoten in den XML-Daten angezeigt wird. Der Wert jedes Knotens entspricht dem Wert, den ein Benutzer ausfüllt. Angenommen, ein Benutzer füllt das Darlehensformular mit Daten, die im folgenden Formular angezeigt werden.

![hs_hs_loanformdata](assets/hs_hs_loanformdata.png)

Die folgende Abbildung zeigt die entsprechenden XML-Daten, die mithilfe der Forms-Dienst-Client-API abgerufen werden.

![hs_hs_loandata](assets/hs_hs_loandata.png)

Die Felder im Darlehensformular. Diese Werte können abgerufen werden
Verwendung von Java-XML-Klassen.

>[!NOTE]
>
>Der Formularentwurf muss in Designer ordnungsgemäß konfiguriert sein, damit Daten als XML-Daten gesendet werden können. Um den Formularentwurf ordnungsgemäß zum Senden von XML-Daten zu konfigurieren, stellen Sie sicher, dass die Schaltfläche Senden im Formularentwurf auf Senden von XML-Daten eingestellt ist. Weitere Informationen zum Festlegen der Senden-Schaltfläche zum Senden von XML-Daten finden Sie unter [AEM Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

## Umgang mit gesendeten PDF-Daten {#handling-submitted-pdf-data}

Stellen Sie sich eine Webanwendung vor, die den Forms-Dienst aufruft. Nachdem der Forms-Dienst ein interaktives PDF-Formular an einen Client-Webbrowser wiedergibt, füllt der Benutzer das Formular aus und sendet es als PDF-Daten zurück. Wenn der Forms-Dienst die PDF-Daten erhält, kann er die PDF-Daten an einen anderen Dienst senden oder als PDF-Datei speichern. Das folgende Diagramm zeigt den Logikfluss der Anwendung.

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
   <td><p>Der Forms-Dienst rendert ein interaktives PDF-Formular an den Client-Webbrowser.</p></td>
  </tr>
  <tr>
   <td><p>1</p></td>
   <td><p>Der Benutzer füllt ein interaktives Formular aus und klickt auf eine Senden-Schaltfläche. Das Formular wird als PDF-Daten an den Forms-Dienst zurückgesendet. Diese Option wird in Designer festgelegt.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Der Forms-Dienst speichert die PDF-Daten als PDF-Datei. </p></td>
  </tr>
 </tbody>
</table>

## Umgang mit gesendeten URL-UTF-16-Daten {#handling-submitted-url-utf-16-data}

Wenn Formulardaten als URL-UTF-16-Daten gesendet werden, erfordert der Client-Computer Adobe Reader oder Acrobat 8.1 oder höher. Enthält der Formularentwurf außerdem eine Senden-Schaltfläche mit URL-kodierten Daten (HTTP Post) und die Datenkodierungsoption UTF-16, muss der Formularentwurf in einem Texteditor wie Notepad geändert werden. Sie können die Kodierungsoption für die Senden-Schaltfläche auf `UTF-16LE` oder `UTF-16BE` setzen. Designer bietet diese Funktion nicht.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um gesendete Formulare zu verarbeiten:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Rufen Sie Formulardaten ab.
1. Bestimmen Sie, ob die Formularübermittlung Dateianlagen enthält.
1. Verarbeiten Sie die gesendeten Daten.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient` -Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsService` -Objekt.

**Abrufen von Formulardaten**

Um die gesendeten Formulardaten abzurufen, rufen Sie die `processFormSubmission` -Methode des Objekts `FormsServiceClient` auf. Beim Aufrufen dieser Methode müssen Sie den Inhaltstyp des gesendeten Formulars angeben. Wenn Daten von einem Client-Webbrowser an den Forms-Dienst gesendet werden, können sie entweder als XML- oder PDF-Daten gesendet werden. Um die in Formularfelder eingegebenen Daten abzurufen, können die Daten als XML-Daten gesendet werden.

Sie können auch Formularfelder aus einem Formular abrufen, das als PDF-Daten gesendet wurde, indem Sie die folgenden Laufzeitoptionen festlegen:

* Übergeben Sie den folgenden Wert als Inhaltstyp-Parameter an die `processFormSubmission` -Methode: `CONTENT_TYPE=application/pdf`.
* Setzen Sie den `RenderOptionsSpec` -Wert des Objekts `PDFToXDP` auf `true`
* Setzen Sie den `RenderOptionsSpec` -Wert des Objekts `ExportDataFormat` auf `XMLData`

Sie geben den Inhaltstyp des gesendeten Formulars an, wenn Sie die `processFormSubmission`-Methode aufrufen. In der folgenden Liste sind die zutreffenden Inhaltstypwerte aufgeführt:

* **text/xml**: Stellt den Inhaltstyp dar, der verwendet werden soll, wenn ein PDF-Formular Formulardaten als XML sendet.
* **application/x-www-form-urlencoded**: Stellt den Inhaltstyp dar, der verwendet werden soll, wenn ein HTML-Formular Daten als XML sendet.
* **application/pdf**: Stellt den Inhaltstyp dar, der verwendet werden soll, wenn ein PDF-Formular Daten als PDF sendet.

>[!NOTE]
>
>Sie werden feststellen, dass dem Abschnitt Umgang mit gesendeten Forms drei entsprechende Schnellstarts zugeordnet sind. Der Schnellstart Umgang mit PDF forms, die als PDF mit der Java-API gesendet wurden, zeigt, wie gesendete PDF-Daten verarbeitet werden. Der in diesem Schnellstart angegebene Inhaltstyp ist `application/pdf`. Der Schnellstart Handling-PDF forms, die mit dem Java-API-Schnellstart als XML gesendet wurden, zeigt, wie gesendete XML-Daten verarbeitet werden, die von einem PDF-Formular gesendet werden. Der in diesem Schnellstart angegebene Inhaltstyp ist `text/xml`. Gleichermaßen zeigt der Schnellstart Umgang mit HTML-Formularen, die als XML mit dem Java-API-Schnellstart gesendet wurden, wie gesendete XML-Daten verarbeitet werden, die von einem HTML-Formular gesendet werden. Der in diesem Schnellstart angegebene Inhaltstyp ist application/x-www-form-urlencoded.

Sie rufen Formulardaten ab, die an den Forms-Dienst gesendet wurden, und bestimmen den Verarbeitungsstatus. Das heißt, wenn Daten an den Forms-Dienst gesendet werden, bedeutet dies nicht unbedingt, dass der Forms-Dienst die Verarbeitung der Daten abgeschlossen hat und die Daten bereit zur Verarbeitung sind. Beispielsweise können Daten an den Forms-Dienst gesendet werden, damit eine Berechnung durchgeführt werden kann. Nach Abschluss der Berechnung wird das Formular mit den angezeigten Berechnungsergebnissen an den Benutzer zurückgegeben. Bevor Sie gesendete Daten verarbeiten, sollten Sie ermitteln, ob der Forms-Dienst die Verarbeitung der Daten abgeschlossen hat.

Der Forms-Dienst gibt die folgenden Werte zurück, um anzugeben, ob die Verarbeitung der Daten abgeschlossen ist:

* **0 (Senden):** Die gesendeten Daten können verarbeitet werden.
* **1 (Berechnen):**  Der Forms-Dienst hat einen Berechnungsvorgang für die Daten durchgeführt und die Ergebnisse müssen an den Benutzer zurückgegeben werden.
* **2 (Validierung):** Der Forms-Dienst hat die Formulardaten validiert und die Ergebnisse müssen an den Benutzer zurückgegeben werden.
* **3 (Weiter):** Die aktuelle Seite hat sich mit Ergebnissen geändert, die in die Client-Anwendung geschrieben werden müssen.
* **4 (Zurück**): Die aktuelle Seite wurde mit Ergebnissen geändert, die in die Client-Anwendung geschrieben werden müssen.

>[!NOTE]
>
>Berechnungen und Überprüfungen müssen an den Benutzer zurückgegeben werden. (Siehe [Berechnen von Formulardaten](/help/forms/developing/calculating-form-data.md#calculating-form-data).

**Bestimmen, ob die Formularübermittlung Dateianlagen enthält**

Forms, das an den Forms-Dienst gesendet wird, kann Dateianlagen enthalten. Beispielsweise kann ein Benutzer mithilfe des integrierten Anlagenbereichs von Acrobat Dateianlagen auswählen, die zusammen mit dem Formular gesendet werden sollen. Außerdem können Benutzer Dateianlagen auch über eine HTML-Symbolleiste auswählen, die mit einer HTML-Datei gerendert wird.

Nachdem Sie festgestellt haben, ob ein Formular Dateianhänge enthält, können Sie die Daten verarbeiten. Sie können beispielsweise den Dateianhang im lokalen Dateisystem speichern.

>[!NOTE]
>
>Das Formular muss als PDF-Daten gesendet werden, damit Dateianlagen abgerufen werden können. Wenn das Formular als XML-Daten gesendet wird, werden keine Dateianlagen gesendet.

**Verarbeiten der gesendeten Daten**

Je nach Inhaltstyp der gesendeten Daten können Sie einzelne Formularfeldwerte aus den gesendeten XML-Daten extrahieren oder die gesendeten PDF-Daten als PDF-Datei speichern (oder an einen anderen Dienst senden). Um einzelne Formularfelder zu extrahieren, konvertieren Sie gesendete XML-Daten in eine XML-Datenquelle und rufen Sie dann XML-Datenquellenwerte mithilfe von `org.w3c.dom`-Klassen ab.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

## Verarbeiten gesendeter Formulare mit der Java-API {#handle-submitted-forms-using-the-java-api}

Verarbeiten Sie ein gesendetes Formular mit der Forms-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Abrufen von Formulardaten

   * Um Formulardaten abzurufen, die in einem Java-Servlet veröffentlicht wurden, erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie seinen Konstruktor verwenden und die `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getInputStream` aus dem Konstruktor aufrufen.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Legen Sie den Gebietsschemawert fest, indem Sie die `setLocale` -Methode des Objekts `RenderOptionsSpec` aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt.

   >[!NOTE]
   >
   >Sie können den Forms-Dienst anweisen, XDP- oder XML-Daten aus gesendeten PDF-Inhalten zu erstellen, indem Sie die `setPDF2XDP` -Methode des Objekts `RenderOptionsSpec` aufrufen und `true` übergeben sowie `setXMLData` aufrufen und `true` übergeben. Anschließend können Sie die `getOutputXML`-Methode des `FormsResult`-Objekts aufrufen, um die XML-Daten abzurufen, die den XDP-/XML-Daten entsprechen. (Das `FormsResult`-Objekt wird von der `processFormSubmission`-Methode zurückgegeben, die im nächsten Unterschritt erläutert wird.)

   * Rufen Sie die `processFormSubmission` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

      * Das `com.adobe.idp.Document`-Objekt, das die Formulardaten enthält.
      * Ein string -Wert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Header angibt. Geben Sie den zu verarbeitenden Inhaltstyp an. Um XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`. Um PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/pdf`.
      * Ein string -Wert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. . `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Dieser Parameterwert ist optional.
      * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen speichert.

      Die `processFormSubmission`-Methode gibt ein `FormsResult`-Objekt zurück, das die Ergebnisse der Formularübermittlung enthält.

   * Stellen Sie fest, ob der Forms-Dienst die Verarbeitung der Formulardaten abgeschlossen hat, indem Sie die `getAction` -Methode des Objekts `FormsResult` aufrufen. Wenn diese Methode den Wert `0` zurückgibt, können die Daten verarbeitet werden.



1. Bestimmen, ob die Formularübermittlung Dateianlagen enthält

   * Rufen Sie die `getAttachments` -Methode des Objekts `FormsResult` auf. Diese Methode gibt ein `java.util.List` -Objekt zurück, das Dateien enthält, die mit dem Formular gesendet wurden.
   * Durchsuchen Sie das `java.util.List`-Objekt, um festzustellen, ob Dateianlagen vorhanden sind. Wenn Dateianlagen vorhanden sind, ist jedes Element eine `com.adobe.idp.Document`-Instanz. Sie können die Dateianlagen speichern, indem Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` aufrufen und ein `java.io.File` -Objekt übergeben.

   >[!NOTE]
   >
   >Dieser Schritt gilt nur, wenn das Formular als PDF gesendet wird.

1. Verarbeiten der gesendeten Daten

   * Wenn der Datentyp `application/vnd.adobe.xdp+xml` oder `text/xml` ist, erstellen Sie eine Anwendungslogik, um XML-Datenwerte abzurufen.

      * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
      * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie den `java.io.DataInputStream`-Konstruktor aufrufen und das `com.adobe.idp.Document`-Objekt übergeben.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory` -Objekt, indem Sie die `newInstance` -Methode des statischen `org.w3c.dom.DocumentBuilderFactory` -Objekts aufrufen.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilder` -Objekt, indem Sie die `newDocumentBuilder` -Methode des Objekts `org.w3c.dom.DocumentBuilderFactory` aufrufen.
      * Erstellen Sie ein `org.w3c.dom.Document` -Objekt, indem Sie die `org.w3c.dom.DocumentBuilder` -Methode des Objekts `parse` aufrufen und das `java.io.InputStream` -Objekt übergeben.
      * Rufen Sie den Wert jedes Knotens im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document` -Objekt und den Namen des Knotens, dessen Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert des Knotens darstellt. Im Codebeispiel, das diesem Prozess folgt, heißt diese benutzerdefinierte Methode `getNodeText`. Der Hauptteil dieser Methode wird angezeigt.
   * Wenn der Datentyp `application/pdf` ist, erstellen Sie eine Anwendungslogik, um die gesendeten PDF-Daten als PDF-Datei zu speichern.

      * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
      * Erstellen Sie ein `java.io.File`-Objekt mithilfe des öffentlichen Konstruktors. Stellen Sie sicher, dass Sie PDF als Dateinamenerweiterung angeben.
      * Füllen Sie die PDF-Datei, indem Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` aufrufen und das `java.io.File` -Objekt übergeben.


**Siehe auch**

[Schnellstart (SOAP-Modus): Umgang mit als XML gesendeten PDF forms mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api)

[Schnellstart (SOAP-Modus): Umgang mit HTML-Formularen, die als XML mit der Java-API gesendet wurden](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api)

[Schnellstart (SOAP-Modus): Umgang mit als PDF gesendeten PDF forms mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verarbeiten gesendeter PDF-Daten mit der Webdienst-API {#handle-submitted-pdf-data-using-the-web-service-api}

Verarbeiten Sie ein gesendetes Formular mit der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` -Objekt und legen Sie Authentifizierungswerte fest.

1. Abrufen von Formulardaten

   * Um Formulardaten abzurufen, die in einem Java-Servlet veröffentlicht wurden, erstellen Sie ein `BLOB` -Objekt mithilfe seines Konstruktors.
   * Erstellen Sie ein `java.io.InputStream` -Objekt, indem Sie die `getInputStream` -Methode des Objekts `javax.servlet.http.HttpServletResponse` aufrufen.
   * Erstellen Sie ein `java.io.ByteArrayOutputStream` -Objekt, indem Sie dessen Konstruktor verwenden und die Länge des `java.io.InputStream` -Objekts übergeben.
   * Kopieren Sie den Inhalt des Objekts `java.io.InputStream` in das Objekt `java.io.ByteArrayOutputStream` .
   * Erstellen Sie ein Byte-Array, indem Sie die `toByteArray` -Methode des Objekts `java.io.ByteArrayOutputStream` aufrufen.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `setBinaryData`-Methode aufrufen und das Byte-Array als Argument übergeben.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Legen Sie den Gebietsschemawert fest, indem Sie die `setLocale` -Methode des Objekts `RenderOptionsSpec` aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt.
   * Rufen Sie die `processFormSubmission` -Methode des Objekts `FormsService` auf und übergeben Sie die folgenden Werte:

      * Das `BLOB`-Objekt, das die Formulardaten enthält.
      * Ein string -Wert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Header angibt. Geben Sie den zu verarbeitenden Inhaltstyp an. Um XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`. Um PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/pdf`.
      * Ein string -Wert, der den Header-Wert `HTTP_USER_AGENT` angibt; z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen speichert.
      * Ein leeres `BLOBHolder` -Objekt, das von der -Methode ausgefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode ausgefüllt wird.
      * Ein leeres `BLOBHolder` -Objekt, das von der -Methode ausgefüllt wird.
      * Ein leeres `BLOBHolder` -Objekt, das von der -Methode ausgefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.ShortHolder` -Objekt, das von der -Methode ausgefüllt wird.
      * Ein leeres `MyArrayOf_xsd_anyTypeHolder` -Objekt, das von der -Methode ausgefüllt wird. Dieser Parameter wird zum Speichern von Dateianlagen verwendet, die zusammen mit dem Formular gesendet werden.
      * Ein leeres `FormsResultHolder` -Objekt, das von der -Methode mit dem gesendeten Formular gefüllt wird.

      Die `processFormSubmission`-Methode füllt den Parameter `FormsResultHolder` mit den Ergebnissen der Formularübermittlung.

   * Stellen Sie fest, ob der Forms-Dienst die Verarbeitung der Formulardaten abgeschlossen hat, indem Sie die `getAction` -Methode des Objekts `FormsResult` aufrufen. Wenn diese Methode den Wert `0` zurückgibt, können die Formulardaten verarbeitet werden. Sie können ein `FormsResult` -Objekt abrufen, indem Sie den Wert des `FormsResultHolder` -Datenelements des `value` -Objekts abrufen.


1. Bestimmen, ob die Formularübermittlung Dateianlagen enthält

   Rufen Sie den Wert des `MyArrayOf_xsd_anyTypeHolder`-Datenelements des `value`-Objekts ab (das `MyArrayOf_xsd_anyTypeHolder`-Objekt wurde an die `processFormSubmission`-Methode übergeben). Dieses Datenelement gibt ein Array von `Objects` zurück. Jedes Element im Array `Object` ist ein `Object`Element, das den Dateien entspricht, die zusammen mit dem Formular gesendet wurden. Sie können jedes Element im Array abrufen und in ein `BLOB` -Objekt umwandeln.

1. Verarbeiten der gesendeten Daten

   * Wenn der Datentyp `application/vnd.adobe.xdp+xml` oder `text/xml` ist, erstellen Sie eine Anwendungslogik, um XML-Datenwerte abzurufen.

      * Erstellen Sie ein `BLOB` -Objekt, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
      * Erstellen Sie ein Byte-Array, indem Sie die `getBinaryData` -Methode des Objekts `BLOB` aufrufen.
      * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie den `java.io.ByteArrayInputStream`-Konstruktor aufrufen und das Byte-Array übergeben.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory` -Objekt, indem Sie die `newInstance` -Methode des statischen `org.w3c.dom.DocumentBuilderFactory` -Objekts aufrufen.
      * Erstellen Sie ein `org.w3c.dom.DocumentBuilder` -Objekt, indem Sie die `newDocumentBuilder` -Methode des Objekts `org.w3c.dom.DocumentBuilderFactory` aufrufen.
      * Erstellen Sie ein `org.w3c.dom.Document` -Objekt, indem Sie die `org.w3c.dom.DocumentBuilder` -Methode des Objekts `parse` aufrufen und das `java.io.InputStream` -Objekt übergeben.
      * Rufen Sie den Wert jedes Knotens im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document` -Objekt und den Namen des Knotens, dessen Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert des Knotens darstellt. Im Codebeispiel, das diesem Prozess folgt, heißt diese benutzerdefinierte Methode `getNodeText`. Der Hauptteil dieser Methode wird angezeigt.
   * Wenn der Datentyp `application/pdf` ist, erstellen Sie eine Anwendungslogik, um die gesendeten PDF-Daten als PDF-Datei zu speichern.

      * Erstellen Sie ein `BLOB` -Objekt, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
      * Erstellen Sie ein Byte-Array, indem Sie die `getBinaryData` -Methode des Objekts `BLOB` aufrufen.
      * Erstellen Sie ein `java.io.File`-Objekt mithilfe des öffentlichen Konstruktors. Stellen Sie sicher, dass Sie PDF als Dateinamenerweiterung angeben.
      * Erstellen Sie ein `java.io.FileOutputStream`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.File`-Objekt übergeben.
      * Füllen Sie die PDF-Datei, indem Sie die `write`-Methode des Objekts `java.io.FileOutputStream` aufrufen und das Byte-Array übergeben.


**Siehe auch**

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
