---
title: Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien
seo-title: Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien
description: Verwenden Sie den Forms-Dienst, um auf benutzerdefinierte CSS-Dateien zu verweisen, um HTML-Formulare als Reaktion auf eine HTTP-Anforderung eines Webbrowsers wiederzugeben. Sie können ein HTML-Formular wiedergeben, das eine CSS-Datei verwendet, indem Sie die Java-API und die Web Service-API verwenden.
seo-description: Verwenden Sie den Forms-Dienst, um auf benutzerdefinierte CSS-Dateien zu verweisen, um HTML-Formulare als Reaktion auf eine HTTP-Anforderung eines Webbrowsers wiederzugeben. Sie können ein HTML-Formular wiedergeben, das eine CSS-Datei verwendet, indem Sie die Java-API und die Web Service-API verwenden.
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
workflow-type: tm+mt
source-wordcount: '1738'
ht-degree: 2%

---

# Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien {#rendering-html-forms-using-custom-css-files}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Der Forms-Dienst gibt HTML-Formulare als Reaktion auf eine HTTP-Anforderung eines Webbrowsers wieder. Beim Rendern eines HTML-Formulars kann der Forms-Dienst auf eine benutzerdefinierte CSS-Datei verweisen. Sie können eine benutzerdefinierte CSS-Datei erstellen, um Ihre Geschäftsanforderungen zu erfüllen und auf diese CSS-Datei zu verweisen, wenn Sie den Forms-Dienst zur Wiedergabe von HTML-Formularen verwenden.

Der Forms-Dienst analysiert die benutzerdefinierte CSS-Datei im Hintergrund. Das heißt, der Forms-Dienst meldet keine Fehler, die auftreten können, wenn die benutzerdefinierte CSS-Datei nicht den CSS-Standards entspricht. In diesem Fall ignoriert der Forms-Dienst den Stil und fährt mit den übrigen Stilen fort, die sich in der CSS-Datei befinden.

Die folgende Liste enthält Stile, die in einer benutzerdefinierten CSS-Datei unterstützt werden:

* **Selektorstil-Paare auf Klassenebene**: Wenn in einer benutzerdefinierten CSS-Datei vorhanden, werden Selektoren verwendet, die im HTML-Formular als Klassenstile verwendet werden. Nicht verwendete Klassenstile werden ignoriert.
* **Selektorstil-Paare** auf Identifizierungsebene: Alle Identifizierungsstile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Selektor-Stil-Paare auf Elementebene**: Alle Elementstile werden verwendet, wenn sie im HTML-Formular verwendet werden.
* **Stilpriorität**: Stilpriorität (wie wichtig) wird unterstützt und kann in einer benutzerdefinierten CSS-Datei verwendet werden.
* **Medientyp**: Ein oder mehrere Selektorstil-Paare können in den @media-Stil eingeschlossen werden, um den Medientyp zu definieren. Der Forms-Dienst überprüft nicht, ob der angegebene Medientyp unterstützt wird. Der in der benutzerdefinierten CSS-Datei angegebene Medientyp wird im HTML-Formular zusammengeführt.

Sie können eine CSS-Beispieldatei mit der FormsIVS-Anwendung abrufen. Laden Sie das Formular hoch, wählen Sie es auf der Seite &quot;Formularentwurf testen&quot;aus und klicken Sie auf &quot;CSS generieren&quot;. Sie müssen den HTML-Transformationstyp nicht festlegen, bevor Sie auf die Schaltfläche klicken. Wählen Sie dann Speichern aus. Sie können diese CSS-Datei bearbeiten, um Ihre Geschäftsanforderungen zu erfüllen.

>[!NOTE]
>
>Vor der Wiedergabe eines HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, ist es wichtig, dass Sie über fundierte Kenntnisse in der Wiedergabe von HTML-Formularen verfügen. (Siehe [Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md).)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein HTML-Formular wiederzugeben, das eine CSS-Datei verwendet:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Java API-Objekt.
1. Verweisen Sie auf die CSS-Datei.
1. Wiedergabe eines HTML-Formulars
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Java API-Objekts**

Bevor Sie einen vom Forms-Dienst unterstützten Vorgang programmgesteuert ausführen können, müssen Sie ein Forms-Client-Objekt erstellen.

**Verweisen auf die CSS-Datei**

Um ein HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, stellen Sie sicher, dass Sie auf eine vorhandene CSS-Datei verweisen.

**HTML-Formular wiedergeben**

Um ein HTML-Formular wiederzugeben, müssen Sie einen in Designer erstellten und als XDP-Datei gespeicherten Formularentwurf angeben. Sie müssen auch einen HTML-Transformationstyp auswählen. Sie können beispielsweise den HTML-Transformationstyp angeben, der ein dynamisches HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte, die zum Rendern anderer Formulartypen erforderlich sind.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein HTML-Formular wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen, damit das HTML-Formular für den Benutzer sichtbar wird.

**Siehe auch**

[Wiedergabe eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet](#render-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

## Wiedergabe eines HTML-Formulars, das eine CSS-Datei mit der Java-API {#render-an-html-form-that-uses-a-css-file-using-the-java-api} verwendet

Wiedergabe eines HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Java API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen auf die CSS-Datei

   * Erstellen Sie ein `HTMLRenderSpec` -Objekt mithilfe des zugehörigen Konstruktors.
   * Um das HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, rufen Sie die `setCustomCSSURI` -Methode des Objekts `HTMLRenderSpec` auf und übergeben Sie einen string -Wert, der den Speicherort und den Namen der CSS-Datei angibt.

1. HTML-Formular wiedergeben

   Rufen Sie die `(Deprecated) (Deprecated) renderHTMLForm` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Präferenztyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` -Objekt.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein string -Wert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec` -Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `(Deprecated) renderHTMLForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `FormsResult` -Methode des Objekts &quot;s `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `com.adobe.idp.Document` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `com.adobe.idp.Document` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.h\ttp.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein `java.io.InputStream` -Objekt, indem Sie die `getInputStream` -Methode des Objekts `com.adobe.idp.Document` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `read` -Methode des Objekts `InputStream` aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.ServletOutputStream` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Schnellstart (SOAP-Modus): Wiedergabe eines HTML-Formulars, das eine CSS-Datei mit der Java-API verwendet](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe eines HTML-Formulars, das eine CSS-Datei verwendet, mithilfe der Webdienst-API {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Wiedergabe eines HTML-Formulars, das eine benutzerdefinierte CSS-Datei verwendet, mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Java API-Objekts

   Erstellen Sie ein `FormsService` -Objekt und legen Sie Authentifizierungswerte fest.

1. Verweisen auf die CSS-Datei

   * Erstellen Sie ein `HTMLRenderSpec` -Objekt mithilfe des zugehörigen Konstruktors.
   * Um das HTML-Formular wiederzugeben, das eine benutzerdefinierte CSS-Datei verwendet, rufen Sie die `setCustomCSSURI` -Methode des Objekts `HTMLRenderSpec` auf und übergeben Sie einen string -Wert, der den Speicherort und den Namen der CSS-Datei angibt.

1. HTML-Formular wiedergeben

   Rufen Sie die `(Deprecated) renderHTMLForm` -Methode des Objekts `FormsService` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Präferenztyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein string -Wert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Wenn Sie diesen Wert nicht festlegen möchten, können Sie eine leere Zeichenfolge übergeben.
   * Ein `URLSpec` -Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode gefüllt wird. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der `(Deprecated) renderHTMLForm` -Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Rendering-Wert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `(Deprecated) renderHTMLForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` -Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` -Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `BLOB` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `BLOB` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `getBinaryData`-Methode des Objekts `BLOB`. Diese Aufgabe weist den Inhalt des Objekts `FormsResult` dem Byte-Array zu.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.http.HttpServletResponse` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Rendern von HTML Forms mit benutzerdefinierten CSS-Dateien](#rendering-html-forms-using-custom-css-files)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
