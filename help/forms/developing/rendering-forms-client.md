---
title: Wiedergabe von Formularen auf dem Client
seo-title: Wiedergabe von Formularen auf dem Client
description: 'null'
seo-description: 'null'
uuid: 09bcc23d-28b0-473a-87f1-bc17e87620f4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 08d36e9f-cafc-478e-9781-8fc29ac6262e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Wiedergabe von Formularen auf dem Client {#rendering-forms-at-the-client}

## Wiedergabe von Formularen auf dem Client {#rendering-forms-at-the-client-inner}

Sie können die Bereitstellung von PDF-Inhalten optimieren und die Fähigkeit des Forms-Dienstes zur Handhabung der Netzwerkbelastung durch die clientseitige Wiedergabe von Acrobat oder Adobe Reader verbessern. Dieser Prozess wird als Wiedergabe eines Formulars auf dem Client bezeichnet. Um ein Formular auf dem Client wiederzugeben, muss das Client-Gerät (normalerweise ein Webbrowser) Acrobat 7.0 oder Adobe Reader 7.0 oder höher verwenden.

Änderungen an einem Formular, die sich aus der serverseitigen Skriptausführung ergeben, werden nicht in einem Formular wiedergegeben, das auf dem Client wiedergegeben wird, es sei denn, das Stammteilformular enthält das `restoreState` Attribut, auf das festgelegt ist `auto`. Weitere Informationen zu diesem Attribut finden Sie unter [Forms Designer.](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein Formular auf dem Client:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Clientrendering-Laufzeitoptionen fest.
1. Formular auf dem Client wiedergeben
1. Schreiben Sie das Formular in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient` Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsService` Objekt.

**Festlegen von Laufzeitoptionen für das Rendern von Clients**

Sie müssen die Client-Rendering-Laufzeitoption festlegen, um ein Formular auf dem Client wiederzugeben, indem Sie die `RenderAtClient` Laufzeitoption auf `true`. Dadurch wird das Formular an das Client-Gerät gesendet, auf dem es wiedergegeben wird. Wenn `RenderAtClient` dies der `auto` (Standardwert) ist, bestimmt der Formularentwurf, ob das Formular auf dem Client wiedergegeben wird. Der Formularentwurf muss ein Formularentwurf mit einem flexiblen Layout sein.

Eine optionale Laufzeitoption, die Sie einstellen können, ist die `SeedPDF` Option. Die `SeedPDF` Option kombiniert den PDF-Container (Seed PDF-Dokument) mit dem Formularentwurf und den XML-Daten. Sowohl der Formularentwurf als auch die XML-Daten werden an Acrobat oder Adobe Reader gesendet, wo das Formular wiedergegeben wird. Die `SeedPDF` Option kann verwendet werden, wenn der Clientcomputer keine im Formular verwendeten Schriften enthält, z. B. wenn ein Endbenutzer nicht für die Verwendung einer Schrift lizenziert ist, für die der Formularinhaber eine Lizenz besitzt.

Sie können Designer verwenden, um eine einfache dynamische PDF-Datei zu erstellen, die als Seed-PDF-Datei verwendet werden soll. Die folgenden Schritte sind erforderlich, um diese Aufgabe durchzuführen:

1. Legen Sie fest, ob Schriftarten in die Seed-PDF-Datei eingebettet werden müssen. Die Seed-PDF-Datei muss zusätzliche Schriftarten enthalten, die für das wiedergegebene Formular erforderlich sind. Wenn Sie Schriftarten in die Seed-PDF-Datei einbetten, stellen Sie sicher, dass Sie keine Schriftartlizenzvereinbarungen verletzen. In Designer können Sie festlegen, ob Schriftarten legal eingebettet werden können. Wenn beim Speichern keine Schriften in das Formular eingebettet werden können, zeigt Designer eine Meldung an, in der die Schriften aufgelistet werden, die nicht eingebettet werden können. Diese Meldung wird in Designer für statische PDF-Dokumente nicht angezeigt.
1. Wenn Sie die Seed-PDF-Datei in Designer erstellen, sollten Sie mindestens ein Textfeld mit einer Meldung hinzufügen. Die Meldung sollte an Benutzer früherer Versionen von Adobe Reader gerichtet werden und angeben, dass sie Acrobat 7.0 oder höher oder Adobe Reader 7.0 oder höher benötigen, um das Dokument anzuzeigen.
1. Speichern Sie die Seed-PDF-Datei als dynamische PDF-Datei mit der Erweiterung des PDF-Dateinamens.

>[!NOTE]
>
>Sie müssen die Laufzeitoption zum Wiedergeben eines Formulars auf dem Client nicht definieren. Wenn Sie keine Seed-PDF-Datei angeben, erstellt der Forms-Dienst eine Shell-PDF, die keine COS-Objekte enthält, aber einen PDF-Wrapper mit dem tatsächlichen XDP-Inhalt enthält, der in das Dokument eingebettet ist. Die Schritte in diesem Abschnitt legen die Option zum Starten der PDF-Laufzeitumgebung nicht fest. Informationen zu COS-Objekten finden Sie im Adobe PDF-Referenzhandbuch.

**Formular auf dem Client wiedergeben**

Um ein Formular auf dem Client wiederzugeben, müssen Sie sicherstellen, dass die Client-Rendering-Laufzeitoptionen in Ihrer Anwendungslogik enthalten sind, um ein Formular wiederzugeben.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Der Forms-Dienst erstellt einen Formulardatenstream, den Sie in den Client-Webbrowser schreiben müssen. Wenn das Formular in den Client-Webbrowser geschrieben wird, wird es von Acrobat 7.0 oder Adobe Reader 7.0 oder höher wiedergegeben und ist für den Benutzer sichtbar.

**Siehe auch**

[Formular mit der Java-API auf dem Client wiedergeben](#render-a-form-at-the-client-using-the-java-api)

[Formular mit der Webdienst-API auf dem Client wiedergeben](#render-a-form-at-the-client-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formular mit der Java-API auf dem Client wiedergeben {#render-a-form-at-the-client-using-the-java-api}

Wiedergabe eines Formulars auf dem Client mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `FormsServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Festlegen von Laufzeitoptionen für das Rendern von Clients

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die `RenderAtClient` Laufzeitoption fest, indem Sie die `PDFFormRenderSpec` Objektmethode aufrufen und den `setRenderAtClient` Enum-Wert übergeben `RenderAtClient.Yes`.

1. Formular auf dem Client wiedergeben

   Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer AEM Forms-Anwendung ist, müssen Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` Objekt.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst zum Rendern eines Formulars erforderlich sind.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   Die `renderPDFForm` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` `read` Objektmethode aufrufen und das Bytearray als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Wiedergabe eines Formulars auf dem Client mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formular mit der Webdienst-API auf dem Client wiedergeben {#render-a-form-at-the-client-using-the-web-service-api}

Wiedergabe eines Formulars auf dem Client mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Laufzeitoptionen für das Rendern von Clients

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die `RenderAtClient` Laufzeitoption fest, indem Sie die `PDFFormRenderSpec` Objektmethode aufrufen `setRenderAtClient` und den Zeichenfolgenwert übergeben `RenderAtClient.Yes`.

1. Formular auf dem Client wiedergeben

   Rufen Sie die `FormsService` Objektmethode `renderPDFForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Formularen mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md#prepopulating-forms-with-flowable-layouts).)
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das von der Methode gefüllt wird. Dieser Parameter wird zum Speichern des gerenderten PDF-Formulars verwendet.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das die Ergebnisse dieses Vorgangs enthält.
   Die `renderPDFForm` Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` Objektdatenelements abrufen `value` .
   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des `BLOB` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `BLOB` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB` Objektmethode `getBinaryData` . Diese Aufgabe weist den Inhalt des `FormsResult` Objekts dem Bytearray zu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Wiedergabe von Formularen auf dem Client](#rendering-forms-at-the-client)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
