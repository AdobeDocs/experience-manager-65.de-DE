---
title: Wiedergabe von HTML-Formularen mit benutzerdefinierten CSS-Dateien
seo-title: Wiedergabe von HTML-Formularen mit benutzerdefinierten CSS-Dateien
description: 'null'
seo-description: 'null'
uuid: a44e96f1-001d-48a2-8c96-15cb9d0c71b3
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8fe7c072-7df0-44b7-92d0-bf39dc1e688a
translation-type: tm+mt
source-git-commit: fcbe1d860410e215cb7c438f94579e0b14d262a5

---


# Wiedergabe von HTML-Formularen mit benutzerdefinierten CSS-Dateien {#rendering-html-forms-using-custom-css-files}

Der Forms-Dienst gibt HTML-Formulare als Antwort auf eine HTTP-Anforderung eines Webbrowsers wieder. Beim Rendern eines HTML-Formulars kann der Forms-Dienst auf eine benutzerdefinierte CSS-Datei verweisen. Sie können eine benutzerdefinierte CSS-Datei erstellen, um Ihre Geschäftsanforderungen zu erfüllen und auf diese CSS-Datei zu verweisen, wenn Sie den Forms-Dienst zur Wiedergabe von HTML-Formularen verwenden.

Der Forms-Dienst analysiert die benutzerdefinierte CSS-Datei im Hintergrund. Das heißt, der Forms-Dienst meldet keine Fehler, die auftreten können, wenn die benutzerdefinierte CSS-Datei nicht den CSS-Standards entspricht. In diesem Fall ignoriert der Forms-Dienst den Stil und fährt mit den übrigen Stilen in der CSS-Datei fort.

Die folgende Liste gibt Stile an, die in einer benutzerdefinierten CSS-Datei unterstützt werden:

* **Selektor-Stil-Paare** auf Klassenebene: Wenn sie in einer benutzerdefinierten CSS-Datei vorhanden sind, werden Selektoren verwendet, die im HTML-Formular als Klassenstile verwendet werden. Nicht verwendete Klassenstile werden ignoriert.
* **Selektor-Stil-Paare** auf Identifizierungsebene: Alle ID-Stile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Selektor-Stil-Paare** auf Elementebene: Alle Elementstile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Stilpriorität**: Stilpriorität (wie wichtig) wird unterstützt und kann in einer benutzerdefinierten CSS-Datei verwendet werden.
* **Medientyp**: Ein oder mehrere Selektor-Stil-Paare können in den @media-Stil eingeschlossen werden, um den Medientyp zu definieren. Der Forms-Dienst überprüft nicht, ob der angegebene Medientyp unterstützt wird. Der in der benutzerdefinierten CSS-Datei angegebene Medientyp wird im HTML-Formular zusammengeführt.

Sie können eine CSS-Beispieldatei mit der FormsIVS-Anwendung abrufen. Laden Sie das Formular hoch, wählen Sie es auf der Seite &quot;Formularentwurf testen&quot;aus und klicken Sie auf &quot;CSS generieren&quot;. Sie müssen den HTML-Konvertierungstyp nicht festlegen, bevor Sie auf die Schaltfläche klicken. Wählen Sie Speichern. Sie können diese CSS-Datei bearbeiten, um Ihren Geschäftsanforderungen zu entsprechen.

>[!NOTE]
>
>Bevor Sie ein HTML-Formular wiedergeben, das eine benutzerdefinierte CSS-Datei verwendet, sollten Sie sich mit der Wiedergabe von HTML-Formularen vertraut machen. (Siehe [Wiedergabe von Formularen als HTML](/help/forms/developing/rendering-forms-html.md).)

>[!NOTE]
>
>For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein HTML-Formular mit einer CSS-Datei:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Java-API-Objekt für Forms.
1. Verweisen Sie auf die CSS-Datei.
1. Wiedergabe eines HTML-Formulars
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Java-API-Objekt für Forms erstellen**

Bevor Sie einen vom Forms-Dienst unterstützten Vorgang programmgesteuert ausführen können, müssen Sie ein Forms-Client-Objekt erstellen.

**CSS-Datei referenzieren**

Um ein HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, verweisen Sie auf eine vorhandene CSS-Datei.

**HTML-Formular wiedergeben**

Zur Wiedergabe eines HTML-Formulars müssen Sie einen Formularentwurf angeben, der in Designer erstellt und als XDP-Datei gespeichert wurde. Sie müssen auch einen HTML-Konvertierungstyp auswählen. Sie können beispielsweise den HTML-Umwandlungstyp angeben, der ein dynamisches HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte, die zum Rendern anderer Formulartypen erforderlich sind.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Wenn der Forms-Dienst ein HTML-Formular wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie an den Client-Webbrowser schreiben müssen, damit das HTML-Formular für den Benutzer sichtbar wird.

**Siehe auch**

[Wiedergabe eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet](#render-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Wiedergeben interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Wiedergabe von Formularen als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

## Wiedergabe eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet {#render-an-html-form-that-uses-a-css-file-using-the-java-api}

Wiedergabe eines HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Java-API-Objekt für Forms erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. CSS-Datei referenzieren

   * Create an `HTMLRenderSpec` object by using its constructor.
   * Um das HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, rufen Sie die `HTMLRenderSpec` `setCustomCSSURI` Objektmethode auf und übergeben Sie einen Zeichenfolgenwert, der den Speicherort und den Namen der CSS-Datei angibt.

1. HTML-Formular wiedergeben

   Rufen Sie die `FormsServiceClient` Objektmethode `(Deprecated) (Deprecated) renderHTMLForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo` Enum-Wert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML`an.
   * Ein `com.adobe.idp.Document` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` Objekt.
   * Das `HTMLRenderSpec` Objekt, in dem HTML-Laufzeitoptionen gespeichert werden.
   * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT` Kopfzeilenwert angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec` Objekt, das zum Rendern eines HTML-Formulars erforderliche URI-Werte speichert.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   Die `(Deprecated) renderHTMLForm` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.h\ttp.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` `read` Objektmethode aufrufen und das Bytearray als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Wiedergabe von HTML-Formularen mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Quick Beginn (SOAP-Modus): Wiedergabe eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe eines HTML-Formulars, das eine CSS-Datei mit der Webdienst-API verwendet {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Wiedergabe eines HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Java-API-Objekt für Forms erstellen

   Erstellen Sie ein `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. CSS-Datei referenzieren

   * Create an `HTMLRenderSpec` object by using its constructor.
   * Um das HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, rufen Sie die `HTMLRenderSpec` `setCustomCSSURI` Objektmethode auf und übergeben Sie einen Zeichenfolgenwert, der den Speicherort und den Namen der CSS-Datei angibt.

1. HTML-Formular wiedergeben

   Rufen Sie die `FormsService` Objektmethode `(Deprecated) renderHTMLForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo` Enum-Wert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML`an.
   * Ein `BLOB` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Formularen mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Das `HTMLRenderSpec` Objekt, in dem HTML-Laufzeitoptionen gespeichert werden.
   * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT` Kopfzeilenwert angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Sie können eine leere Zeichenfolge übergeben, wenn Sie diesen Wert nicht festlegen möchten.
   * Ein `URLSpec` Objekt, das zum Rendern eines HTML-Formulars erforderliche URI-Werte speichert.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das durch die `(Deprecated) renderHTMLForm` Methode gefüllt wird. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das durch die `(Deprecated) renderHTMLForm` Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` Objekt, das durch die `(Deprecated) renderHTMLForm` Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das durch die `(Deprecated) renderHTMLForm` Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das durch die `(Deprecated) renderHTMLForm` Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Renderwert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das die Ergebnisse dieses Vorgangs enthält.
   Die `(Deprecated) renderHTMLForm` Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` Objektdatenelements abrufen `value` .
   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des `BLOB` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `BLOB` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB` Objektmethode `getBinaryData` . Diese Aufgabe weist den Inhalt des `FormsResult` Objekts dem Bytearray zu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Wiedergabe von HTML-Formularen mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
