---
title: Rendern von HTML-Formularen mit benutzerdefinierten CSS-Dateien
seo-title: Rendering HTML Forms Using Custom CSS Files
description: Verwenden Sie den Forms-Service, um auf benutzerdefinierte CSS-Dateien zu verweisen und so HTML-Formulare als Reaktion auf eine HTTP-Anfrage eines Webbrowsers zu rendern. Sie können ein HTML-Formular rendern, das eine CSS-Datei verwendet, indem Sie die Java-API und die Webservice-API nutzen.
seo-description: Use the Forms service to refer to custom CSS files to render HTML forms in response to an HTTP request from a web browser. You can render an HTML form that uses a CSS file using the Java API and Web Service API.
uuid: a44e96f1-001d-48a2-8c96-15cb9d0c71b3
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8fe7c072-7df0-44b7-92d0-bf39dc1e688a
role: Developer
exl-id: 5fa385a7-f030-4c0c-8938-0991d02ef361
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1688'
ht-degree: 100%

---

# Rendern von HTML-Formularen mit benutzerdefinierten CSS-Dateien {#rendering-html-forms-using-custom-css-files}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Der Forms-Service rendert HTML-Formulare als Reaktion auf eine HTTP-Anfrage eines Webbrowsers. Beim Rendern eines HTML-Formulars kann der Forms-Service auf eine benutzerdefinierte CSS-Datei verweisen. Sie können eine benutzerdefinierte CSS-Datei erstellen, um Ihre Geschäftsanforderungen zu erfüllen, und auf diese CSS-Datei verweisen, wenn Sie den Forms-Service zum Rendern von HTML-Formularen verwenden.

Der Forms-Service analysiert die benutzerdefinierte CSS-Datei im Hintergrund. Das heißt, der Forms-Service meldet keine Fehler, die auftreten können, wenn die benutzerdefinierte CSS-Datei nicht den CSS-Standards entspricht. In diesem Fall ignoriert der Forms-Service den Stil und fährt mit den übrigen Stilen fort, die sich in der CSS-Datei befinden.

Die folgende Liste enthält Stile, die in einer benutzerdefinierten CSS-Datei unterstützt werden:

* **Selektorstilpaare auf Klassenebene**: Wenn in einer benutzerdefinierten CSS-Datei vorhanden, werden Selektoren verwendet, die im HTML-Formular als Klassenstile verwendet werden. Nicht verwendete Klassenstile werden ignoriert.
* **Selektorstilpaare auf Kennungsebene**: Alle Kennungsstile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Selektorstilpaare auf Elementebene**: Alle Elementstile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Stilpriorität**: Stilpriorität (wie „wichtig“) wird unterstützt und kann in einer benutzerdefinierten CSS-Datei verwendet werden.
* **Medientyp**: Ein oder mehrere Selektorstilpaare können in den @media-Stil eingeschlossen werden, um den Medientyp zu definieren. Der Forms-Service überprüft nicht, ob der angegebene Medientyp unterstützt wird. Der in der benutzerdefinierten CSS-Datei angegebene Medientyp wird im HTML-Formular zusammengeführt.

Sie können eine CSS-Beispieldatei mit dem FormsIVS-Programm abrufen. Laden Sie das Formular hoch, wählen Sie es auf der Seite „Formularentwurf testen“ aus und klicken Sie auf „CSS generieren“. Es ist nicht erforderlich, den HTML-Transformationstyp festzulegen, bevor Sie auf die Schaltfläche klicken. Wählen Sie dann „Speichern“ aus. Sie können diese CSS-Datei bearbeiten, um Ihre Geschäftsanforderungen zu erfüllen.

>[!NOTE]
>
>Bevor Sie ein HTML-Formular rendern, das eine benutzerdefinierte CSS-Datei verwendet, müssen Sie über fundierte Kenntnisse in Bezug auf das Rendern von HTML-Formularen verfügen. (Siehe [Rendern von Formularen als HTML](/help/forms/developing/rendering-forms-html.md).)

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein HTML-Formular zu rendern, das eine CSS-Datei verwendet, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Java-API-Objekt.
1. Verweisen Sie auf die CSS-Datei.
1. Rendern Sie ein HTML-Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Schließen Sie Projektdateien ein**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms-Java-API-Objekts**

Bevor Sie einen vom Forms-Service unterstützten Vorgang programmgesteuert ausführen können, müssen Sie ein Forms-Client-Objekt erstellen.

**Verweisen auf die CSS-Datei**

Um ein HTML-Formular zu rendern, das eine benutzerdefinierte CSS-Datei verwendet, stellen Sie sicher, dass Sie auf eine vorhandene CSS-Datei verweisen.

**Rendern eines HTML-Formulars**

Um ein HTML-Formular zu rendern, müssen Sie einen Formularentwurf angeben, der in Designer erstellt und als XDP-Datei gespeichert wurde. Sie müssen auch einen HTML-Transformationstyp auswählen. Sie können beispielsweise den HTML-Transformationstyp angeben, der dynamische HTML für Internet Explorer 5.0 oder höher rendert.

Für das Rendern eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte, die zum Rendern anderer Formulartypen erforderlich sind.

**Schreiben des Formulardatenstroms in den Client-Webbrowser**

Wenn der Forms-Service ein HTML-Formular rendert, wird ein Formulardatenstrom zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen, damit das HTML-Formular für den Benutzer sichtbar wird.

**Siehe auch**

[Rendern eines HTML-Formulars, das eine CSS-Datei verwendet, mithilfe der Java-API](#render-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Formularen als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

## Rendern eines HTML-Formulars, das eine CSS-Datei verwendet, mithilfe der Java-API {#render-an-html-form-that-uses-a-css-file-using-the-java-api}

Rendern Sie ein HTML-Formular, das eine benutzerdefinierte CSS-Datei verwendet, mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms-Java-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen auf die CSS-Datei

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt, indem Sie dessen Konstruktor verwenden.
   * Rufen Sie zum Rendern des HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, die `setCustomCSSURI`-Methode des `HTMLRenderSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Speicherort und den Namen der CSS-Datei angibt.

1. Rendern Sie ein HTML-Formular

   Rufen Sie die `(Deprecated) (Deprecated) renderHTMLForm`-Methode des `FormsServiceClient`-Objekts auf und übergeben Sie ihr die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Aufzählungswert, der den HTML-Präferenztyp angibt. Um beispielsweise ein HTML-Formular zu rendern, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn keine Daten zusammengeführt werden sollen, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT`-Kopfzeilenwert angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `(Deprecated) renderHTMLForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `getOutputContent`-Methode des `FormsResult`-Objekts aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie seine `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp der `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstroms in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des `javax.servlet.h\ttp.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `getInputStream`-Methode des `com.adobe.idp.Document`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstrom, indem Sie die `read`-Methode des `InputStream`-Objekts aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die `write`-Methode des `javax.servlet.ServletOutputStream`-Objekts auf, indem Sie den Formulardatenstrom an den Client-Webbrowser senden. Übergeben Sie das Byte-Array der `write`-Methode.

**Siehe auch**

[Rendern von HTML-Formularen mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Schnellstart (SOAP-Modus): Rendern eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendern eines HTML-Formulars, das eine CSS-Datei verwendet, mithilfe der Web Service-API  {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Rendern Sie ein HTML-Formular, das eine benutzerdefinierte CSS-Datei verwendet, mithilfe der Forms-API (Web Service):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms-Java-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Verweisen auf die CSS-Datei

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt, indem Sie seinen Konstruktor verwenden.
   * Rufen Sie zum Rendern des HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, die `setCustomCSSURI`-Methode des `HTMLRenderSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort und den Namen der CSS-Datei angibt.

1. Rendern Sie ein HTML-Formular

   Rufen Sie die `(Deprecated) renderHTMLForm`-Methode des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Aufzählungswert, der den HTML-Präferenztyp angibt. Um beispielsweise ein HTML-Formular zu rendern, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn keine Daten zusammengeführt werden sollen, übergeben Sie `null`. (Weitere Informationen finden Sie unter [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT`-Kopfzeilenwert angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Wenn Sie diesen Wert nicht festlegen möchten, können Sie eine leere Zeichenfolge übergeben.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das über die `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieser Parameterwert speichert das gerenderte Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das über die `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das über die `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das über die `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das über die `(Deprecated) renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Rendering-Wert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `(Deprecated) renderHTMLForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert mit einem Formulardatenstrom übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Werts des `value`-Datenelements des `com.adobe.idp.services.holders.FormsResultHolder`-Objekts abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des `FormsResult`-Objekts aufrufen.
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts, ab, indem Sie seine `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine `setContentType`-Methode aufrufen und ihr den Inhaltstyp des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstroms in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es, indem Sie die `getBinaryData`-Methode des `BLOB`-Objekts aufrufen. Diese Aufgabe weist dem Byte-Array den Inhalt des `FormsResult`-Objekts hinzu.
   * Rufen Sie die `write`-Methode des `javax.servlet.http.HttpServletResponse`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array der `write`-Methode.

**Siehe auch**

[Rendern von HTML-Formularen mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
