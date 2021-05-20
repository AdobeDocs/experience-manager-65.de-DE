---
title: Rendern von Forms auf dem Client
seo-title: Rendern von Forms auf dem Client
description: Optimieren Sie die Bereitstellung von PDF-Inhalten und verbessern Sie die Fähigkeit des Forms-Dienstes, die Netzwerklast mithilfe der clientseitigen Rendering-Funktion von Acrobat oder Adobe Reader zu bewältigen.
seo-description: Optimieren Sie die Bereitstellung von PDF-Inhalten und verbessern Sie die Fähigkeit des Forms-Dienstes, die Netzwerklast mithilfe der clientseitigen Rendering-Funktion von Acrobat oder Adobe Reader zu bewältigen.
uuid: 09bcc23d-28b0-473a-87f1-bc17e87620f4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 08d36e9f-cafc-478e-9781-8fc29ac6262e
role: Developer
exl-id: e485980d-f200-46b7-9284-c9996003aa47
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1730'
ht-degree: 2%

---

# Rendern von Forms auf dem Client {#rendering-forms-at-the-client}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Rendern von Forms auf dem Client {#rendering-forms-at-the-client-inner}

Sie können die Bereitstellung von PDF-Inhalten optimieren und die Fähigkeit des Forms-Dienstes, die Netzwerklast zu bewältigen, verbessern, indem Sie die clientseitige Rendering-Funktion von Acrobat oder Adobe Reader verwenden. Dieser Prozess wird als Wiedergabe eines Formulars auf dem Client bezeichnet. Um ein Formular auf dem Client wiederzugeben, muss das Client-Gerät (normalerweise ein Webbrowser) Acrobat 7.0 oder Adobe Reader 7.0 oder höher verwenden.

Änderungen an einem Formular, die aus der serverseitigen Skriptausführung resultieren, werden nicht in einem Formular wiedergegeben, das auf dem Client wiedergegeben wird, es sei denn, das Stammteilformular enthält das Attribut `restoreState` , das auf `auto` gesetzt ist. Weitere Informationen zu diesem Attribut finden Sie unter [Forms Designer.](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein Formular auf dem Client wiederzugeben:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Laufzeitoptionen für Client-Rendering fest.
1. Wiedergabe eines Formulars auf dem Client
1. Schreiben Sie das Formular in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient` -Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsService` -Objekt.

**Festlegen von Laufzeitoptionen für Client-Rendering**

Sie müssen die Client-Rendering-Laufzeitoption festlegen, um ein Formular auf dem Client wiederzugeben, indem Sie die Laufzeitoption `RenderAtClient` auf `true` setzen. Dadurch wird das Formular an das Client-Gerät gesendet, auf dem es wiedergegeben wird. Wenn `RenderAtClient` `auto` (Standardwert) ist, bestimmt der Formularentwurf, ob das Formular auf dem Client wiedergegeben wird. Der Formularentwurf muss ein Formularentwurf mit flexiblem Layout sein.

Eine optionale Laufzeitoption, die Sie festlegen können, ist die Option `SeedPDF` . Die Option `SeedPDF` kombiniert den PDF-Container (Seed-PDF-Dokument) mit dem Formularentwurf und den XML-Daten. Sowohl der Formularentwurf als auch die XML-Daten werden an Acrobat oder Adobe Reader übermittelt, wo das Formular wiedergegeben wird. Die Option `SeedPDF` kann verwendet werden, wenn der Clientcomputer über keine im Formular verwendeten Schriftarten verfügt, z. B. wenn ein Endbenutzer nicht für die Verwendung einer Schriftart lizenziert ist, für die der Formularinhaber lizenziert ist.

Sie können Designer verwenden, um eine einfache dynamische PDF-Datei zu erstellen, die als Seed-PDF-Datei verwendet werden kann. Die folgenden Schritte sind erforderlich, um diese Aufgabe durchzuführen:

1. Bestimmen Sie, ob Schriftarten in die Seed-PDF-Datei eingebettet werden müssen. Die Seed-PDF-Datei muss zusätzliche Schriftarten enthalten, die für das wiedergegebene Formular erforderlich sind. Stellen Sie beim Einbetten von Schriftarten in die Seed-PDF-Datei sicher, dass Sie keine Schriftartlizenzvereinbarungen verletzen. In Designer können Sie festlegen, ob Sie Schriftarten rechtmäßig einbetten können. Wenn Schriftarten gespeichert werden, die nicht in das Formular eingebettet werden können, zeigt Designer eine Meldung an, in der die Schriftarten aufgeführt werden, die nicht eingebettet werden können. Diese Meldung wird in Designer für statische PDF-Dokumente nicht angezeigt.
1. Wenn Sie die Seed-PDF-Datei in Designer erstellen, wird empfohlen, mindestens ein Textfeld hinzuzufügen, das eine Nachricht enthält. Die Meldung sollte an Benutzer früherer Versionen von Adobe Reader gerichtet werden, die darauf hinweisen, dass sie Acrobat 7.0 oder höher oder Adobe Reader 7.0 oder höher benötigen, um das Dokument anzuzeigen.
1. Speichern Sie die Seed-PDF-Datei als dynamische PDF-Datei mit der PDF-Dateinamenerweiterung.

>[!NOTE]
>
>Sie müssen die Option zur Laufzeit der Seed-PDF-Datei nicht definieren, um ein Formular auf dem Client wiederzugeben. Wenn Sie keine Seed-PDF angeben, erstellt der Forms-Dienst ein Shell-PDF-Dokument, das keine COS-Objekte enthält, aber einen PDF-Wrapper mit dem tatsächlichen XDP-Inhalt enthält, der in eingebettet ist. Die Schritte in diesem Abschnitt legen die Ausführungsoption für Seed-PDF nicht fest. Informationen zu COS-Objekten finden Sie im Adobe PDF-Referenzhandbuch.

**Formular auf dem Client wiedergeben**

Um ein Formular auf dem Client wiederzugeben, müssen Sie sicherstellen, dass die Client-Rendering-Laufzeitoptionen in Ihrer Anwendungslogik enthalten sind, um ein Formular wiederzugeben.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Der Forms-Dienst erstellt einen Formulardatenstream, den Sie in den Client-Webbrowser schreiben müssen. Wenn das Formular in den Client-Webbrowser geschrieben wird, wird es von Acrobat 7.0 oder Adobe Reader 7.0 oder höher wiedergegeben und ist für den Benutzer sichtbar.

**Siehe auch**

[Wiedergabe eines Formulars auf dem Client mithilfe der Java-API](#render-a-form-at-the-client-using-the-java-api)

[Wiedergabe eines Formulars auf dem Client mithilfe der Webdienst-API](#render-a-form-at-the-client-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

### Wiedergabe eines Formulars auf dem Client mithilfe der Java-API {#render-a-form-at-the-client-using-the-java-api}

Wiedergabe eines Formulars auf dem Client mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Festlegen von Laufzeitoptionen für Client-Rendering

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Laufzeitoption `RenderAtClient` fest, indem Sie die Methode `setRenderAtClient` des Objekts `PDFFormRenderSpec` aufrufen und den Enum-Wert `RenderAtClient.Yes` übergeben.

1. Formular auf dem Client wiedergeben

   Rufen Sie die `renderPDFForm` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer AEM Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` -Objekt.
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält, die der Forms-Dienst zum Rendern eines Formulars benötigt.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `FormsResult` -Methode des Objekts &quot;s `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `com.adobe.idp.Document` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `com.adobe.idp.Document` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein `java.io.InputStream` -Objekt, indem Sie die `getInputStream` -Methode des Objekts `com.adobe.idp.Document` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `read` -Methode des Objekts `InputStream` aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.ServletOutputStream` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Wiedergabe eines Formulars auf dem Client mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Wiedergabe eines Formulars auf dem Client mithilfe der Webdienst-API {#render-a-form-at-the-client-using-the-web-service-api}

Wiedergabe eines Formulars auf dem Client mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` -Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Laufzeitoptionen für Client-Rendering

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Laufzeitoption `RenderAtClient` fest, indem Sie die Methode `setRenderAtClient` des Objekts `PDFFormRenderSpec` aufrufen und den Zeichenfolgenwert `RenderAtClient.Yes` übergeben.

1. Formular auf dem Client wiedergeben

   Rufen Sie die `renderPDFForm` -Methode des Objekts `FormsService` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode ausgefüllt wird. Dieser Parameter wird zum Speichern des wiedergegebenen PDF-Formulars verwendet.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode ausgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular).
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode ausgefüllt wird. (Dieses Argument speichert den Gebietsschemawert).
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` -Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` -Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `BLOB` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `BLOB` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `getBinaryData`-Methode des Objekts `BLOB`. Diese Aufgabe weist den Inhalt des Objekts `FormsResult` dem Byte-Array zu.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.http.HttpServletResponse` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Rendern von Forms auf dem Client](#rendering-forms-at-the-client)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
