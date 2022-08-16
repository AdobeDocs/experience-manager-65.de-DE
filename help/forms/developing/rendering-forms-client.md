---
title: Rendern von Formularen auf dem Client
seo-title: Rendering Forms at the Client
description: Optimieren Sie die Bereitstellung von PDF-Inhalten und verbessern Sie die Fähigkeit des Forms-Services, die Netzwerklast mithilfe der Client-seitigen Rendering-Funktion von Acrobat oder Adobe Reader zu bewältigen.
seo-description: Optimize the delivery of PDF content and improve the Forms service’s ability to handle network load by using the client-side rendering capability of Acrobat or Adobe Reader
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
source-wordcount: '1698'
ht-degree: 100%

---

# Rendern von Formularen auf dem Client {#rendering-forms-at-the-client}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Rendern von Formularen auf dem Client {#rendering-forms-at-the-client-inner}

Sie können die Bereitstellung von PDF-Inhalten optimieren und die Fähigkeit des Forms-Services die Netzwerklast zu bewältigen, verbessern, indem Sie die Client-seitige Rendering-Funktion von Acrobat oder Adobe Reader verwenden. Dieser Prozess wird als Rendering eines Formulars auf dem Client bezeichnet. Um ein Formular auf dem Client zu rendern, muss der Client (normalerweise ein Webbrowser) Acrobat 7.0 oder Adobe Reader 7.0 oder höher verwenden.

Änderungen an einem Formular, die aus der serverseitigen Skriptausführung resultieren, werden in ein Formular, das auf dem Client gerendert wird, nicht aufgenommen, es sei denn, das Stammteilformular enthält das `restoreState`-Attribut, das auf `auto` definiert ist. Weitere Informationen zu diesem Attribut finden Sie unter [Forms Designer.](https://www.adobe.com/go/learn_aemforms_designer_63_de)

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte durch, um ein Formular auf dem Client zu rendern:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Legen Sie beim Client die Laufzeitoptionen für das Rendering fest.
1. Rendern eines Formulars auf dem Client.
1. Senden Sie das Formular an den Client-Webbrowser.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms-Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Service programmgesteuert durchführen können, müssen Sie einen Client für den Forms-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `FormsServiceClient`-Objekt. Wenn Sie die Forms-Web-Service-API verwenden, müssen Sie ein `FormsService`-Objekt erstellen.

**Einstellen der Laufzeitoptionen beim Client für das Rendering**

Sie müssen die Laufzeitoption zum Rendern eines Formulars auf dem Client aktivieren, indem Sie die `RenderAtClient`-Laufzeitoption auf `true` einstellen. Dadurch wird das Formular an den Client übertragen, auf dem es dann gerendert wird. Wenn `RenderAtClient` `auto` beträgt (Standardwert), kann anhand des Formulardesigns bestimmt werden, ob das Formular auf dem Client gerendert werden soll. Bei dem Formulardesign muss beachtet werden, dass dieses ein flexibles Layout haben muss.

Optional können Sie die Laufzeitoption `SeedPDF` aktivieren. Die `SeedPDF`-Option kombiniert den PDF-Container (Seed-PDF-Dokument) mit dem Formulardesign und den XML-Daten. Sowohl das Formulardesign als auch die XML-Daten werden an Acrobat oder Adobe Reader übermittelt, die das Formular rendern. Die `SeedPDF`-Option kann verwendet werden, wenn der Client nicht über die Schriftarten verfügt, die im Formular verwendet werden, z. B. wenn ein Endbenutzer nicht über die Lizenzen für die Verwendung einer bestimmten Schriftart verfügt, die der Formularinhaber verwenden darf.

Sie können Designer verwenden, um eine einfache dynamische PDF-Datei zur Verwendung als Seed-PDF-Datei zu erstellen. Die folgenden Schritte sind erforderlich, um dieses zu erreichen:

1. Prüfen Sie, ob Sie Schriftarten in die Seed-PDF-Datei einbetten müssen. Die Seed-PDF-Datei muss alle zusätzlichen Schriftarten enthalten, die für das Formular, das gerendert werden soll, erforderlich sind. Stellen Sie beim Einbetten von Schriftarten in die Seed-PDF-Datei sicher, dass Sie keine Lizenzvereinbarungen für die Schriftarten verletzen. In Designer können Sie erkennen, ob Sie eine bestimmte Schriftart rechtmäßig einbetten dürfen. Wenn es beim Speichern Schriftarten geben sollte, die nicht in das Formular eingebettet werden können, zeigt Designer eine Meldung an, in der die Schriftarten aufgeführt werden, die nicht eingebettet werden können. Diese Meldung wird in Designer bei statischen PDF-Dokumenten nicht angezeigt.
1. Wenn Sie die Seed-PDF-Datei in Designer erstellen, wird empfohlen, mindestens ein Textfeld mit einer Nachricht hinzuzufügen. Die Nachricht richtet sich an Benutzer früherer Versionen von Adobe Reader und sollte darauf hinweisen, dass sie Acrobat 7.0 oder höher oder Adobe Reader 7.0 oder höher benötigen, um das Dokument anzeigen zu können.
1. Speichern Sie die Seed-PDF-Datei als dynamische PDF-Datei mit der Dateinamenerweiterung PDF ab.

>[!NOTE]
>
>Sie müssen die Laufzeitoption Seed-PDF nicht definieren, um ein Formular auf dem Client zu rendern. Wenn Sie keine Seed-PDF angeben, erstellt der Forms-Service ein Shell-PDF-Dokument, das keine COS-Objekte enthält, jedoch einen PDF-Wrapper, in dem der eigentliche XDP-Inhalt eingebettet ist. In den in diesem Abschnitt aufgeführten Schritten wird die Laufzeitoption Seed-PDF nicht aktiviert. Informationen zu COS-Objekten finden Sie im Adobe PDF-Referenzhandbuch.

**Rendern eines Formulars auf dem Client**

Um ein Formular auf dem Client zu rendern, müssen Sie sicherstellen, dass die Laufzeitoptionen für das Rendern auf dem Client in Ihrer Anwendungslogik für das Rendern des Formulars enthalten sind.

**Senden des Formular-Datenstreams an den Client-Webbrowser**

Der Forms-Service erstellt einen Formular-Datenstream, den Sie an den Client-Webbrowser senden müssen. Nachdem das Formular an den Client-Webbrowser gesendet wurde, wird es von Acrobat 7.0 oder Adobe Reader 7.0 oder höher gerendert und den Benutzern angezeigt.

**Siehe auch**

[Rendern eines Formulars auf dem Client mithilfe der Java-API](#render-a-form-at-the-client-using-the-java-api)

[Rendern eines Formulars auf dem Client mithilfe der Webservice-API](#render-a-form-at-the-client-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Übergeben von Dokumenten an den Forms-Service](/help/forms/developing/passing-documents-forms-service.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendern eines Formulars auf dem Client mithilfe der Java-API {#render-a-form-at-the-client-using-the-java-api}

So rendern Sie ein Formular auf dem Client mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen von Laufzeitoptionen für das Client-Rendering

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Laufzeitoption `RenderAtClient` fest, indem Sie die Methode `setRenderAtClient` des `PDFFormRenderSpec`-Objekts aufrufen und den Aufzählungswert `RenderAtClient.Yes` übergeben.

1. Rendern eines Formulars auf dem Client

   Rufen Sie die Methode `renderPDFForm` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines AEM Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die der Forms-Service zum Rendern eines Formulars benötigt.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die Methode `renderPDFForm` gibt ein `FormsResult`-Objekt zurück, das einen Formulardaten-Stream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Content-Typ des `com.adobe.idp.Document`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die Methode `getInputStream` des `com.adobe.idp.Document`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardaten-Stream, indem Sie die Methode `read` des `InputStream`-Objekts aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die Methode `write` des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formulardaten-Stream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Rendern eines Formulars auf dem Client mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rendern eines Formulars auf dem Client mithilfe der Webservice-API {#render-a-form-at-the-client-using-the-web-service-api}

Rendern eines Formulars auf dem Client mithilfe der Forms-API (Webservice):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von Laufzeitoptionen für das Client-Rendering

   * Erstellen Sie ein Objekt `PDFFormRenderSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Laufzeitoption `RenderAtClient` fest, indem Sie die Methode `setRenderAtClient` des `PDFFormRenderSpec`-Objekts aufrufen und den Zeichenfolgenwert `RenderAtClient.Yes` übergeben.

1. Rendern eines Formulars auf dem Client

   Rufen Sie die Methode `renderPDFForm` des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Formularen mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert, die zum Rendern eines Formulars auf dem Client erforderlich sind.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Service erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, in dem Dateianlagen gespeichert werden. Dies ist ein optionaler Parameter. Sie können `null` festlegen, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode aufgefüllt wird. Dieser Parameter wird zum Speichern des wiedergegebenen PDF-Formulars verwendet.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode aufgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular).
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert den Gebietsschemawert).
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die Methode `renderPDFForm` füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardaten-Stream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des Datenelements `value` des `com.adobe.idp.services.holders.FormsResultHolder`-Objekts abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Inhaltstyp des `BLOB`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardaten-Stream in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es auf, indem Sie die Methode `getBinaryData` des `BLOB`-Objekts aufrufen. Mit dieser Aufgabe wird dem Byte-Array der Inhalt des `FormsResult`-Objekts zugewiesen.
   * Rufen Sie die Methode `write` des `javax.servlet.http.HttpServletResponse`-Objekts auf, um den Formulardaten-Stream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Rendern von Formularen auf dem Client](#rendering-forms-at-the-client)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
