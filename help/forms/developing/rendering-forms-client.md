---
title: Rendern von Forms auf dem Client
seo-title: Rendern von Forms auf dem Client
description: Optimieren Sie den Versand von PDF-Inhalten und verbessern Sie die Fähigkeit des Forms-Dienstes, die Netzwerkbelastung mithilfe der clientseitigen Renderingfunktion von Acrobat oder Adobe Reader zu bewältigen.
seo-description: Optimieren Sie den Versand von PDF-Inhalten und verbessern Sie die Fähigkeit des Forms-Dienstes, die Netzwerkbelastung mithilfe der clientseitigen Renderingfunktion von Acrobat oder Adobe Reader zu bewältigen.
uuid: 09bcc23d-28b0-473a-87f1-bc17e87620f4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 08d36e9f-cafc-478e-9781-8fc29ac6262e
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1731'
ht-degree: 2%

---


# Rendern von Forms auf dem Client {#rendering-forms-at-the-client}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

## Rendern von Forms auf dem Client {#rendering-forms-at-the-client-inner}

Sie können den Versand von PDF-Inhalten optimieren und die Fähigkeit des Forms-Dienstes, Netzwerklasten zu bewältigen, verbessern, indem Sie die clientseitige Renderfunktion von Acrobat oder Adobe Reader verwenden. Dieser Prozess wird als Wiedergabe eines Formulars auf dem Client bezeichnet. Um ein Formular auf dem Client wiederzugeben, muss das Clientgerät (normalerweise ein Webbrowser) Acrobat 7.0 oder Adobe Reader 7.0 oder höher verwenden.

Änderungen an einem Formular, die sich aus der serverseitigen Skriptausführung ergeben, werden nicht in einem Formular übernommen, das auf dem Client wiedergegeben wird, es sei denn, das Stammteilformular enthält das `restoreState`-Attribut, das auf `auto` eingestellt ist. Weitere Informationen zu diesem Attribut finden Sie unter [Forms Designer.](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein Formular auf dem Client:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Clientrendering-Laufzeitoptionen fest.
1. Formular auf dem Client wiedergeben.
1. Schreiben Sie das Formular in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Forms Client API-Objekt erstellen**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient`-Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie ein `FormsService`-Objekt.

**Festlegen von Laufzeitoptionen für das Rendern von Clients**

Sie müssen die Client-Rendering-Laufzeitoption festlegen, um ein Formular auf dem Client wiederzugeben, indem Sie die Laufzeitoption `RenderAtClient` auf `true` festlegen. Dadurch wird das Formular an das Client-Gerät gesendet, auf dem es wiedergegeben wird. Ist `RenderAtClient` `auto` (Standardwert), bestimmt der Formularentwurf, ob das Formular auf dem Client wiedergegeben wird. Der Formularentwurf muss ein Formularentwurf mit einem flexiblen Layout sein.

Eine optionale Laufzeitoption, die Sie einstellen können, ist die Option `SeedPDF`. Die Option `SeedPDF` kombiniert den PDF-Container (Seed PDF-Dokument) mit dem Formularentwurf und den XML-Daten. Sowohl der Formularentwurf als auch die XML-Daten werden an Acrobat oder Adobe Reader gesendet, wo das Formular wiedergegeben wird. Die Option `SeedPDF` kann verwendet werden, wenn der Clientcomputer keine im Formular verwendeten Schriften enthält, z. B. wenn ein Endbenutzer nicht für die Verwendung einer Schrift lizenziert ist, für die der Formularinhaber eine Lizenz besitzt.

Sie können Designer verwenden, um eine einfache dynamische PDF-Datei zu erstellen, die als Seed-PDF-Datei verwendet werden soll. Die folgenden Schritte sind erforderlich, um diese Aufgabe durchzuführen:

1. Legen Sie fest, ob Schriftarten in die Seed-PDF-Datei eingebettet werden müssen. Die Seed-PDF-Datei muss zusätzliche Schriftarten enthalten, die für das wiedergegebene Formular erforderlich sind. Wenn Sie Schriftarten in die Seed-PDF-Datei einbetten, stellen Sie sicher, dass Sie keine Schriftartlizenzvereinbarungen verletzen. In Designer können Sie festlegen, ob Schriftarten legal eingebettet werden können. Wenn beim Speichern keine Schriften in das Formular eingebettet werden können, zeigt Designer eine Meldung an, in der die Schriften aufgelistet werden, die nicht eingebettet werden können. Diese Meldung wird in Designer für statische PDF-Dokumente nicht angezeigt.
1. Wenn Sie die Seed-PDF-Datei in Designer erstellen, sollten Sie mindestens ein Textfeld mit einer Meldung hinzufügen. Die Meldung sollte an Benutzer früherer Versionen von Adobe Reader gerichtet werden und darauf hinweisen, dass sie zur Ansicht des Dokuments Acrobat 7.0 oder höher oder Adobe Reader 7.0 oder höher benötigen.
1. Speichern Sie die Seed-PDF-Datei als dynamische PDF-Datei mit der Erweiterung des PDF-Dateinamens.

>[!NOTE]
>
>Sie müssen die Laufzeitoption &quot;Seed PDF&quot;nicht definieren, um ein Formular auf dem Client wiederzugeben. Wenn Sie keine Seed-PDF-Datei angeben, erstellt der Forms-Dienst eine Shell-PDF, die keine COS-Objekte enthält, aber einen PDF-Wrapper mit dem tatsächlichen XDP-Inhalt enthält, der in das Dokument eingebettet ist. Die Schritte in diesem Abschnitt legen die Option zum Starten der PDF-Laufzeitumgebung nicht fest. Weitere Informationen zu COS-Objekten finden Sie im Adobe PDF-Referenzhandbuch.

**Formular auf dem Client wiedergeben**

Um ein Formular auf dem Client wiederzugeben, müssen Sie sicherstellen, dass die Client-Rendering-Laufzeitoptionen in Ihrer Anwendungslogik enthalten sind, um ein Formular wiederzugeben.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Der Forms-Dienst erstellt einen Formulardatenstream, den Sie in den Client-Webbrowser schreiben müssen. Wenn das Formular in den Client-Webbrowser geschrieben wird, wird es von Acrobat 7.0 oder Adobe Reader 7.0 oder höher wiedergegeben und ist für den Benutzer sichtbar.

**Siehe auch**

[Formular mit der Java-API auf dem Client wiedergeben](#render-a-form-at-the-client-using-the-java-api)

[Formular mit der Webdienst-API auf dem Client wiedergeben](#render-a-form-at-the-client-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Weiterleiten von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formular mit der Java-API {#render-a-form-at-the-client-using-the-java-api} auf dem Client wiedergeben

Wiedergabe eines Formulars auf dem Client mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Client API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen von Laufzeitoptionen für das Rendern von Clients

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Laufzeitoption `RenderAtClient` fest, indem Sie die `setRenderAtClient`-Methode des Objekts aufrufen und den Enum-Wert `RenderAtClient.Yes` übergeben.`PDFFormRenderSpec`

1. Formular auf dem Client wiedergeben

   Rufen Sie die `renderPDFForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer AEM Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst zum Rendern eines Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es mit dem Formulardatenstream, indem Sie die `read`-Methode des Objekts aufrufen und das Bytearray als Argument übergeben.`InputStream`
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Wiedergabe eines Formulars auf dem Client mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formular mit der Webdienst-API {#render-a-form-at-the-client-using-the-web-service-api} auf dem Client wiedergeben

Wiedergabe eines Formulars auf dem Client mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Client API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Laufzeitoptionen für das Rendern von Clients

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Laufzeitoption `RenderAtClient` fest, indem Sie die `setRenderAtClient`-Methode des Objekts aufrufen und den Zeichenfolgenwert `RenderAtClient.Yes` übergeben.`PDFFormRenderSpec`

1. Formular auf dem Client wiedergeben

   Rufen Sie die `renderPDFForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode gefüllt wird. Dieser Parameter wird zum Speichern des gerenderten PDF-Formulars verwendet.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder`-Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des Objekts aufrufen.`FormsResult`
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB`-Methode des Objekts `getBinaryData`. Diese Aufgabe weist dem Bytearray den Inhalt des Objekts `FormsResult` zu.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.http.HttpServletResponse` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von Forms auf dem Client](#rendering-forms-at-the-client)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
