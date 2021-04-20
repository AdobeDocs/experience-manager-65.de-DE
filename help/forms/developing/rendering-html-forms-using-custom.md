---
title: Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien
seo-title: Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien
description: Verwenden Sie den Forms-Dienst, um auf benutzerdefinierte CSS-Dateien zu verweisen, um HTML-Formulare als Antwort auf eine HTTP-Anforderung eines Webbrowsers wiederzugeben. Sie können ein HTML-Formular wiedergeben, das eine CSS-Datei verwendet, indem Sie die Java-API und die Web-Service-API verwenden.
seo-description: Verwenden Sie den Forms-Dienst, um auf benutzerdefinierte CSS-Dateien zu verweisen, um HTML-Formulare als Antwort auf eine HTTP-Anforderung eines Webbrowsers wiederzugeben. Sie können ein HTML-Formular wiedergeben, das eine CSS-Datei verwendet, indem Sie die Java-API und die Web-Service-API verwenden.
uuid: a44e96f1-001d-48a2-8c96-15cb9d0c71b3
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8fe7c072-7df0-44b7-92d0-bf39dc1e688a
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 2%

---


# Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien {#rendering-html-forms-using-custom-css-files}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Der Forms-Dienst gibt HTML-Formulare als Antwort auf eine HTTP-Anforderung eines Webbrowsers wieder. Beim Rendern eines HTML-Formulars kann der Forms-Dienst auf eine benutzerdefinierte CSS-Datei verweisen. Sie können eine benutzerdefinierte CSS-Datei erstellen, um Ihre Geschäftsanforderungen zu erfüllen und auf diese CSS-Datei zu verweisen, wenn Sie den Forms-Dienst zur Wiedergabe von HTML-Formularen verwenden.

Der Forms-Dienst analysiert die benutzerdefinierte CSS-Datei im Hintergrund. Das heißt, der Forms-Dienst meldet keine Fehler, die auftreten können, wenn die benutzerdefinierte CSS-Datei nicht den CSS-Standards entspricht. In diesem Fall ignoriert der Forms-Dienst den Stil und fährt mit den verbleibenden Stilen in der CSS-Datei fort.

Die folgende Liste gibt Stile an, die in einer benutzerdefinierten CSS-Datei unterstützt werden:

* **Selektor-Stil-Paare** auf Klassenebene: Wenn sie in einer benutzerdefinierten CSS-Datei vorhanden sind, werden Selektoren verwendet, die im HTML-Formular als Klassenstile verwendet werden. Nicht verwendete Klassenstile werden ignoriert.
* **Selektor-Stil-Paare** auf Identifizierungsebene: Alle ID-Stile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Selektor-Stil-Paare** auf Elementebene: Alle Elementstile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Stilpriorität**: Stilpriorität (wie wichtig) wird unterstützt und kann in einer benutzerdefinierten CSS-Datei verwendet werden.
* **Medientyp**: Ein oder mehrere Selektor-Stil-Paare können in den @media-Stil eingeschlossen werden, um den Medientyp zu definieren. Der Forms-Dienst überprüft nicht, ob der angegebene Medientyp unterstützt wird. Der in der benutzerdefinierten CSS-Datei angegebene Medientyp wird im HTML-Formular zusammengeführt.

Sie können eine CSS-Beispieldatei mit der FormsIVS-Anwendung abrufen. Laden Sie das Formular hoch, wählen Sie es auf der Seite &quot;Formularentwurf testen&quot;aus und klicken Sie auf &quot;CSS generieren&quot;. Sie müssen den HTML-Konvertierungstyp nicht festlegen, bevor Sie auf die Schaltfläche klicken. Wählen Sie Speichern. Sie können diese CSS-Datei bearbeiten, um Ihren Geschäftsanforderungen zu entsprechen.

>[!NOTE]
>
>Bevor Sie ein HTML-Formular wiedergeben, das eine benutzerdefinierte CSS-Datei verwendet, sollten Sie sich mit der Wiedergabe von HTML-Formularen vertraut machen. (Siehe [Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md).)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein HTML-Formular mit einer CSS-Datei:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Java API-Objekt.
1. Verweisen Sie auf die CSS-Datei.
1. Wiedergabe eines HTML-Formulars
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Forms Java API-Objekt erstellen**

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

[Interaktive PDF forms wiedergeben](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

## Wiedergabe eines HTML-Formulars, das eine CSS-Datei verwendet, mit der Java-API {#render-an-html-form-that-uses-a-css-file-using-the-java-api}

Wiedergabe eines HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, mit der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Java API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. CSS-Datei referenzieren

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt mit dem Konstruktor.
   * Um das HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, rufen Sie die `setCustomCSSURI`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Speicherort und den Namen der CSS-Datei angibt.`HTMLRenderSpec`

1. HTML-Formular wiedergeben

   Rufen Sie die `(Deprecated) (Deprecated) renderHTMLForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `(Deprecated) renderHTMLForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.h\ttp.HttpServletResponse`
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es mit dem Formulardatenstream, indem Sie die `read`-Methode des Objekts aufrufen und das Bytearray als Argument übergeben.`InputStream`
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Quick Beginn (SOAP-Modus): Wiedergabe eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe eines HTML-Formulars, das eine CSS-Datei verwendet, mit der Webdienst-API {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Wiedergabe eines HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, mit der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Java API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. CSS-Datei referenzieren

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt mit dem Konstruktor.
   * Um das HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, rufen Sie die `setCustomCSSURI`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Speicherort und den Namen der CSS-Datei angibt.`HTMLRenderSpec`

1. HTML-Formular wiedergeben

   Rufen Sie die `(Deprecated) renderHTMLForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Sie können eine leere Zeichenfolge übergeben, wenn Sie diesen Wert nicht festlegen möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das mit der `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das mit der `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das mit der `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das mit der `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das mit der `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Renderwert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `(Deprecated) renderHTMLForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder`-Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des Objekts aufrufen.`FormsResult`
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB`-Methode des Objekts `getBinaryData`. Diese Aufgabe weist dem Bytearray den Inhalt des Objekts `FormsResult` zu.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.http.HttpServletResponse` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
