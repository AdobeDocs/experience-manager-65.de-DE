---
title: Formulardaten berechnen
seo-title: Formulardaten berechnen
description: 'null'
seo-description: 'null'
uuid: ccd85bc7-8ccc-44d9-9424-dfc1f603e688
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: b4f57e42-60a6-407d-9764-15a11615827d
translation-type: tm+mt
source-git-commit: 4b9e2ceafc301db9337868b78bcae87c0f07e14b

---


# Formulardaten berechnen {#calculating-form-data}

Der Forms-Dienst kann die Werte berechnen, die ein Benutzer in ein Formular eingibt, und die Ergebnisse anzeigen. Zur Berechnung der Formulardaten müssen Sie zwei Aufgaben ausführen. Zunächst erstellen Sie ein Formularentwurfsskript, das die Formulardaten berechnet. Ein Formularentwurf unterstützt drei Skripttypen. Ein Skripttyp wird auf dem Client ausgeführt, ein anderer auf dem Server und der dritte auf dem Server und dem Client. Der in diesem Thema beschriebene Skripttyp wird auf dem Server ausgeführt. Serverseitige Berechnungen werden für HTML-, PDF- und Formularleitfadentransformationen (nicht mehr unterstützt) unterstützt.

Im Rahmen des Formularentwurfsprozesses können Sie Berechnungen und Skripten verwenden, um eine bessere Benutzerfreundlichkeit zu gewährleisten. Berechnungen und Skripten können den meisten Formularfeldern und -objekten hinzugefügt werden. Sie müssen ein Formularentwurfsskript erstellen, um Berechnungsvorgänge für Daten durchzuführen, die ein Benutzer in ein interaktives Formular eingibt.

Der Benutzer gibt Werte in das Formular ein und klickt auf die Schaltfläche Berechnen, um die Ergebnisse anzuzeigen. Der folgende Vorgang beschreibt eine Beispielanwendung, mit der ein Benutzer Daten berechnen kann:

* Der Benutzer greift auf eine HTML-Seite mit dem Namen StartLoan.html zu, die als Startseite der Webanwendung fungiert. Diese Seite ruft ein Java-Servlet mit dem Namen `GetLoanForm`auf.
* Das `GetLoanForm` Servlet rendert ein Darlehensformular. Dieses Formular enthält ein Skript, interaktive Felder, eine Berechnungsschaltfläche und eine Senden-Schaltfläche.
* Der Benutzer gibt Werte in die Felder des Formulars ein und klickt auf die Schaltfläche &quot;Berechnen&quot;. Das Formular wird an das `CalculateData` Java-Servlet gesendet, wo das Skript ausgeführt wird. Das Formular wird mit den im Formular angezeigten Berechnungsergebnissen an den Benutzer zurückgesendet.
* Der Benutzer fährt mit der Eingabe und Berechnung der Werte fort, bis ein zufriedenstellendes Ergebnis angezeigt wird. Wenn der Benutzer zufrieden ist, klickt er auf die Schaltfläche &quot;Senden&quot;, um das Formular zu verarbeiten. Das Formular wird an ein anderes Java-Servlet mit dem Namen `ProcessForm` gesendet, das für das Abrufen der gesendeten Daten zuständig ist. (Siehe [Verarbeiten gesendeter Formulare](/help/forms/developing/rendering-forms.md#handling-submitted-forms).)


Das folgende Diagramm zeigt den logischen Ablauf der Anwendung.

![cf_cf_finsrv_loancalcapp_v1](assets/cf_cf_finsrv_loancalcapp_v1.png)

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
   <td><p>Das <code>GetLoanForm</code> Java-Servlet wird von der HTML-Startseite aufgerufen. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Das <code>GetLoanForm</code> Java-Servlet verwendet die Forms-Dienst-Client-API, um das Darlehensformular an den Client-Webbrowser zu rendern. Der Unterschied zwischen der Wiedergabe eines Formulars, das ein Skript enthält, das für die Ausführung auf dem Server konfiguriert ist, und der Wiedergabe eines Formulars, das kein Skript enthält, besteht darin, dass Sie den Zielspeicherort angeben müssen, der zum Ausführen des Skripts verwendet wird. Wenn kein Zielort angegeben ist, wird kein Skript ausgeführt, das für die Ausführung auf dem Server konfiguriert ist. Betrachten Sie zum Beispiel die Anwendung, die in diesem Abschnitt eingeführt wurde. Das <code>CalculateData</code> Java-Servlet ist der Zielort, an dem das Skript ausgeführt wird.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Der Benutzer gibt Daten in interaktive Felder ein und klickt auf die Schaltfläche Berechnen. Das Formular wird an das <code>CalculateData</code> Java-Servlet gesendet, wo das Skript ausgeführt wird. </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Das Formular wird mit den im Formular angezeigten Berechnungsergebnissen an den Webbrowser zurückgegeben. </p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Der Benutzer klickt auf die Senden-Schaltfläche, wenn die Werte zufriedenstellend sind. Das Formular wird an ein anderes Java-Servlet namens <code>ProcessForm</code>.</p></td>
  </tr>
 </tbody>
</table>

In der Regel enthält ein Formular, das als PDF-Inhalt übermittelt wird, Skripten, die auf dem Client ausgeführt werden. Serverseitige Berechnungen können jedoch auch ausgeführt werden. Skripten können nicht mit einer Senden-Schaltfläche berechnet werden. In diesem Fall werden keine Berechnungen ausgeführt, da der Forms-Dienst die Interaktion für abgeschlossen hält.

Um die Verwendung eines Formularentwurfsskripts zu veranschaulichen, wird in diesem Abschnitt ein einfaches interaktives Formular mit einem Skript untersucht, das für die Ausführung auf dem Server konfiguriert ist. Das folgende Diagramm zeigt einen Formularentwurf mit einem Skript, das Werte hinzufügt, die ein Benutzer in die ersten beiden Felder eingibt, und das Ergebnis im dritten Feld anzeigt.

![cf_cf_caldata](assets/cf_cf_caldata.png)

******A. Ein Feld mit dem Namen NumericField1** B. Ein Feld mit dem Namen NumericField2 **C.** Ein Feld mit dem Namen NumericField3

Die Syntax des Skripts in diesem Formularentwurf lautet wie folgt:

```as3
     NumericField3 = NumericField2 + NumericField1
```

In diesem Formularentwurf ist die Schaltfläche &quot;Berechnen&quot;eine Befehlsschaltfläche und das Skript befindet sich im `Click` Ereignis dieser Schaltfläche. Wenn ein Benutzer Werte in die ersten beiden Felder (NumericField1 und NumericField2) eingibt und auf die Schaltfläche Berechnen klickt, wird das Formular an den Forms-Dienst gesendet, wo das Skript ausgeführt wird. Der Forms-Dienst rendert das Formular wieder auf das Clientgerät, wobei die Ergebnisse der Berechnung im Feld NumericField3 angezeigt werden.

>[!NOTE]
>
>Informationen zum Erstellen eines Formularentwurfsskripts finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

>[!NOTE]
>
>For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So berechnen Sie Formulardaten:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Rufen Sie ein Formular mit einem Berechnungsskript ab.
1. Den Formulardatenstream zurück in den Client-Webbrowser schreiben

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient` Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsServiceService` Objekt.

**Abrufen eines Formulars mit einem Berechnungsskript**

Mit der Forms-Dienst-Client-API können Sie eine Anwendungslogik erstellen, die ein Formular verarbeitet, das ein Skript enthält, das für die Ausführung auf dem Server konfiguriert wurde. Der Prozess ähnelt der Bearbeitung eines gesendeten Formulars. (Siehe [Verarbeiten von gesendeten Formularen](/help/forms/developing/handling-submitted-forms.md#handling-submitted-forms).)

Vergewissern Sie sich, dass der mit dem gesendeten Formular verknüpfte Verarbeitungsstatus `1` `(Calculate)`ist. Das bedeutet, dass der Forms-Dienst eine Berechnung der Formulardaten durchführt und die Ergebnisse an den Benutzer zurückgeschrieben werden müssen. In diesem Fall wird automatisch ein Skript ausgeführt, das für die Ausführung auf dem Server konfiguriert ist.

**Den Formulardatenstream zurück in den Client-Webbrowser schreiben**

Nachdem Sie überprüft haben, ob der Verarbeitungsstatus, der mit einem gesendeten Formular verknüpft ist, `1`vorliegt, müssen Sie die Ergebnisse zurück in den Client-Webbrowser schreiben. Wenn das Formular angezeigt wird, wird der berechnete Wert in den entsprechenden Feldern angezeigt.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
Formulardaten[mithilfe der Java-API](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-java-api)[Berechnen von Formulardaten mithilfe der Web-Service-API](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-web-service-api)Festlegen der Verbindungseigenschaften[](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)Forms-Dienst-API - Schnellstarts[Wiedergeben interaktiver PDF-Formulare](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)[](/help/forms/developing/rendering-interactive-pdf-forms.md)[Erstellen von Webanwendungen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

## Formulardaten mit der Java-API berechnen {#calculate-form-data-using-the-java-api}

Berechnen von Formulardaten mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `FormsServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Abrufen eines Formulars mit einem Berechnungsskript

   * Um Formulardaten abzurufen, die ein Berechnungsskript enthalten, erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie den Konstruktor des Objekts verwenden und die `javax.servlet.http.HttpServletResponse` Methode des `getInputStream` Objekts im Konstruktor aufrufen.
   * Rufen Sie die `FormsServiceClient` Objektmethode `processFormSubmission` auf und übergeben Sie die folgenden Werte:

      * Das `com.adobe.idp.Document` Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Header angibt. Sie müssen den zu verarbeitenden Inhaltstyp angeben, indem Sie einen oder mehrere Werte für die `CONTENT_TYPE` Umgebungsvariable angeben. Um beispielsweise XML- und PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/xml&CONTENT_TYPE=application/pdf`
      * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT` Kopfzeilenwert angibt; zum Beispiel `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Ein `RenderOptionsSpec` Objekt, das Laufzeitoptionen speichert.
      Die `processFormSubmission` Methode gibt ein `FormsResult` Objekt zurück, das die Ergebnisse der Formularübermittlung enthält.

   * Vergewissern Sie sich, dass der Verarbeitungsstatus, der mit einem gesendeten Formular verknüpft ist, `1` durch Aufrufen der `FormsResult` Objektmethode `getAction` erreicht wird. Wenn diese Methode den Wert zurückgibt, `1`wurde die Berechnung durchgeführt und die Daten können an den Client-Webbrowser zurückgeschrieben werden.


1. Den Formulardatenstream zurück in den Client-Webbrowser schreiben

   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` `read` Objektmethode aufrufen und das Bytearray als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**


[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formulardaten mithilfe der Webdienst-API berechnen {#calculate-form-data-using-the-web-service-api}

Berechnen von Formulardaten mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Abrufen eines Formulars mit einem Berechnungsskript

   * Um Formulardaten abzurufen, die an ein Java-Servlet gesendet wurden, erstellen Sie ein `BLOB` Objekt mit dessen Konstruktor.
   * Erstellen Sie ein `java.io.InputStream` Objekt mithilfe der `javax.servlet.http.HttpServletResponse` Objektmethode `getInputStream` .
   * Create a `java.io.ByteArrayOutputStream` object by using its constructor and passing the length of the `java.io.InputStream` object.
   * Kopieren Sie den Inhalt des `java.io.InputStream` Objekts in das `java.io.ByteArrayOutputStream` Objekt.
   * Erstellen Sie ein Bytearray, indem Sie die `java.io.ByteArrayOutputStream` Objektmethode `toByteArray` aufrufen.
   * Füllen Sie das `BLOB` Objekt, indem Sie seine `setBinaryData` Methode aufrufen und das Bytearray als Argument übergeben.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Legen Sie den Wert für das Gebietsschema fest, indem Sie die `RenderOptionsSpec` Methode des `setLocale` Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt.
   * Rufen Sie die `FormsServiceClient` Objektmethode `processFormSubmission` auf und übergeben Sie die folgenden Werte:

      * Das `BLOB` Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der Umgebungsvariablen angibt, die alle relevanten HTTP-Header enthalten. Sie können beispielsweise den folgenden Zeichenfolgenwert angeben: `HTTP_REFERER=referrer&HTTP_CONNECTION=keep-alive&CONTENT_TYPE=application/xml`
      * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT` Kopfzeilenwert angibt; zum Beispiel `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Ein `RenderOptionsSpec` Objekt, das Laufzeitoptionen speichert. Für weitere Informationen, .
      * Ein leeres `BLOBHolder` Objekt, das von der Methode gefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das von der Methode gefüllt wird.
      * Ein leeres `BLOBHolder` Objekt, das von der Methode gefüllt wird.
      * Ein leeres `BLOBHolder` Objekt, das von der Methode gefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.ShortHolder` Objekt, das von der Methode gefüllt wird.
      * Ein leeres `MyArrayOf_xsd_anyTypeHolder` Objekt, das von der Methode gefüllt wird. Dieser Parameter wird zum Speichern von Dateianlagen verwendet, die zusammen mit dem Formular gesendet werden.
      * Ein leeres `FormsResultHolder` Objekt, das von der Methode mit dem gesendeten Formular gefüllt wird.
      Die `processFormSubmission` Methode füllt den `FormsResultHolder` Parameter mit den Ergebnissen der Formularübermittlung. Die `processFormSubmission` Methode gibt ein `FormsResult` Objekt zurück, das die Ergebnisse der Formularübermittlung enthält.

   * Vergewissern Sie sich, dass der Verarbeitungsstatus, der mit einem gesendeten Formular verknüpft ist, `1` durch Aufrufen der `FormsResult` Objektmethode `getAction` erreicht wird. Wenn diese Methode den Wert zurückgibt, `1`wurde die Berechnung durchgeführt und die Daten können an den Client-Webbrowser zurückgeschrieben werden.


1. Den Formulardatenstream zurück in den Client-Webbrowser schreiben

   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB` Objektmethode `getBinaryData` . Diese Aufgabe weist den Inhalt des `FormsResult` Objekts dem Bytearray zu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch** Aufrufen[von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
