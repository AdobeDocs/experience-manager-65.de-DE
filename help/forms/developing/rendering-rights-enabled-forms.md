---
title: Wiedergabe von Formularen mit aktivierten Rechten
seo-title: Wiedergabe von Formularen mit aktivierten Rechten
description: 'null'
seo-description: 'null'
uuid: ce5e4be6-d9b0-4989-a0e1-a8c3b98aed77
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d4c2b2f0-613a-409d-b39b-8e37fdb96eea
translation-type: tm+mt
source-git-commit: 7cbe3e94eddb81925072f68388649befbb027e6d

---


# Wiedergabe von Formularen mit aktivierten Rechten {#rendering-rights-enabled-forms}

Der Forms-Dienst kann Formulare mit Verwendungsrechten wiedergeben. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. Formulare mit Verwendungsrechten werden als Formulare mit aktivierten Verwendungsrechten bezeichnet. Ein Benutzer, der ein Formular mit aktivierten Benutzerrechten in Adobe Reader öffnet, kann Vorgänge ausführen, die für dieses Formular aktiviert sind.

Um Verwendungsrechte auf ein Formular anzuwenden, muss der Acrobat Reader DC Extensions-Dienst Teil Ihrer AEM Forms-Installation sein. Darüber hinaus müssen Sie über eine gültige Berechtigung verfügen, mit der Sie Verwendungsrechte auf PDF-Dokumente anwenden können. Das heißt, Sie müssen den Acrobat Reader DC Extensions-Dienst ordnungsgemäß konfigurieren, bevor Sie ein Formular mit aktivierten Berechtigungen wiedergeben können. (Siehe [Info zum Acrobat Reader DC Extensions-Dienst](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).)

>[!NOTE]
>
>Um ein Formular mit Verwendungsrechten wiederzugeben, müssen Sie eine XDP-Datei als Eingabe und keine PDF-Datei verwenden. Wenn Sie eine PDF-Datei als Eingabe verwenden, wird das Formular weiterhin gerendert. Es handelt sich jedoch nicht um ein Formular mit aktivierten Rechten.

>[!NOTE]
>
>Sie können ein Formular mit XML-Daten nicht im Voraus ausfüllen, wenn Sie die folgenden Verwendungsrechte angeben: `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles`oder `enableDigitalSignatures`. (Siehe [Vorausfüllen von Formularen mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)

>[!NOTE]
>
>For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein Formular mit aktivierten Berechtigungen wiederzugeben, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Laufzeitoptionen für Verwendungsrechte fest.
1. Wiedergabe eines Formulars mit aktivierten Benutzerrechten.
1. Schreiben Sie das Formular mit aktivierten Benutzerrechten in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen.

**Laufzeitoptionen für Verwendungsrechte festlegen**

Sie müssen Laufzeitoptionen für Verwendungsrechte festlegen, um ein Formular mit aktivierten Verwendungsrechten wiederzugeben. Sie müssen auch den Alias der Berechtigung angeben, die zum Anwenden von Verwendungsrechten auf ein Formular verwendet wird. Nachdem Sie den Aliaswert angegeben haben, geben Sie jedes Verwendungsrecht für das Formular an.

**Wiedergabe eines Formulars mit aktivierten Verwendungsrechten**

Zur Wiedergabe eines Formulars mit aktivierten Verwendungsrechten verwenden Sie dieselbe Anwendungslogik wie die Wiedergabe eines Formulars ohne Verwendungsrechte. Der einzige Unterschied besteht darin, dass Sie sicherstellen müssen, dass die Laufzeitoptionen für Verwendungsrechte in Ihrer Anwendungslogik enthalten sind.

>[!NOTE]
>
>Bei der Wiedergabe eines Formulars mit aktivierten Rechten mithilfe der Forms-Webdienst-API können Sie keine Dateien an das Formular anhängen.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular mit aktivierten Rechten wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Nach dem Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar. Ein Benutzer, der das Formular mit aktivierten Benutzerrechten in Adobe Reader anzeigt, kann Vorgänge ausführen, die für dieses Formular aktiviert sind.

**Siehe auch**

[Wiedergabe von Formularen mit aktivierten Verwendungsrechten mit der Java-API](#render-rights-enabled-forms-using-the-java-api)

[Wiedergabe von Formularen mit aktivierten Verwendungsrechten mithilfe der Webdienst-API](#render-rights-enabled-forms-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Wiedergeben interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Webanwendungen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Wiedergabe von Formularen mit aktivierten Verwendungsrechten mit der Java-API {#render-rights-enabled-forms-using-the-java-api}

Wiedergabe eines Formulars mit aktivierten Rechten mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `FormsServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Laufzeitoptionen für Verwendungsrechte festlegen

   * Erstellen Sie ein Objekt `ReaderExtensionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Alias der Berechtigung an, indem Sie die `ReaderExtensionSpec` Objektmethode aufrufen und einen Zeichenfolgenwert angeben, der den Aliaswert darstellt. `setReCredentialAlias`
   * Legen Sie die Verwendungsrechte fest, indem Sie die entsprechende Methode aufrufen, die zum `ReaderExtensionSpec` Objekt gehört. Sie können jedoch nur dann ein Verwendungsrecht festlegen, wenn die von Ihnen referenzierte Berechtigung dies zulässt. Das heißt, Sie können keine Verwendungsrechte festlegen, wenn die Berechtigung das Festlegen nicht zulässt. Beispiel. Um das Verwendungsrecht festzulegen, mit dem ein Benutzer Formularfelder ausfüllen und das Formular speichern kann, rufen Sie die `ReaderExtensionSpec` Methode des `setReFillIn` Objekts auf und übergeben Sie es `true`.
   >[!NOTE]
   >
   >Es ist nicht erforderlich, die `ReaderExtensionSpec` Objektmethode `setReCredentialPassword` aufzurufen. Diese Methode wird vom Forms-Dienst nicht verwendet.

1. Wiedergabe eines Formulars mit aktivierten Verwendungsrechten

   Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFFormWithUsageRights` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` Objekt.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert.
   * Ein `ReaderExtensionSpec` Objekt, das Laufzeitoptionen für Verwendungsrechte speichert.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   Die `renderPDFFormWithUsageRights` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Byte-Array, das mit dem Formulardatenstream gefüllt wird, indem Sie die `InputStream` Objektmethode aufrufen und das Bytearray als Argument übergeben `read` .
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Wiedergabe eines Formulars mit aktivierten Rechten mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe von Formularen mit aktivierten Verwendungsrechten mithilfe der Webdienst-API {#render-rights-enabled-forms-using-the-web-service-api}

Wiedergabe eines Formulars mit aktivierten Berechtigungen mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Laufzeitoptionen für Verwendungsrechte festlegen

   * Erstellen Sie ein Objekt `ReaderExtensionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Alias der Berechtigung an, indem Sie die `ReaderExtensionSpec` Objektmethode aufrufen und einen Zeichenfolgenwert angeben, der den Aliaswert darstellt. `setReCredentialAlias`
   * Legen Sie die Verwendungsrechte fest, indem Sie die entsprechende Methode aufrufen, die zum `ReaderExtensionSpec` Objekt gehört. Sie können jedoch nur dann ein Verwendungsrecht festlegen, wenn die von Ihnen referenzierte Berechtigung dies zulässt. Das heißt, Sie können keine Verwendungsrechte festlegen, wenn die Berechtigung das Festlegen nicht zulässt. Um das Verwendungsrecht festzulegen, mit dem ein Benutzer Formularfelder ausfüllen und das Formular speichern kann, rufen Sie die `ReaderExtensionSpec` Methode des `setReFillIn` Objekts auf und übergeben Sie es `true`.

1. Wiedergabe eines Formulars mit aktivierten Verwendungsrechten

   Rufen Sie die `FormsService` Objektmethode `renderPDFFormWithUsageRights` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten mit dem Formular zusammenführen möchten, müssen Sie ein `BLOB` Objekt übergeben, das auf einer leeren XML-Datenquelle basiert. Ein `BLOB` Objekt, das null ist, kann nicht übergeben werden. Andernfalls wird eine Ausnahme ausgelöst.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert.
   * Ein `ReaderExtensionSpec` Objekt, das Laufzeitoptionen für Verwendungsrechte speichert.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   Die `renderPDFFormWithUsageRights` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des `BLOB` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `BLOB` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB` Objektmethode `getBinaryData` . Diese Aufgabe weist den Inhalt des `FormsResult` Objekts dem Bytearray zu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Wiedergabe von Formularen mit aktivierten Rechten](#rendering-rights-enabled-forms)

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
