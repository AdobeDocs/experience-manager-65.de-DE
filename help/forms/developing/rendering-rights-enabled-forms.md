---
title: Rendern von Formularen mit aktivierten Verwendungsrechten
description: Verwenden Sie den Forms-Service zum Rendern von Formularen, für die Nutzungsrechte angewendet wurden. Sie können Formulare mit aktivierten Rechten mithilfe der Java-API und der Web-Service-API rendern.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 012a3a9f-542c-4ed1-a092-572bfccbdf21
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 77%

---

# Rendern von Formularen mit aktivierten Verwendungsrechten {#rendering-rights-enabled-forms}

Der Forms-Service kann Formulare rendern, auf die Nutzungsrechte angewendet wurden. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. Formulare, auf die Nutzungsrechte angewandt wurden, werden als Formulare mit aktivierten Nutzungsrechten bezeichnet. Benutzer, die ein Formular mit aktivierten Nutzungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses spezifische Formular aktiviert sind.

Um Verwendungsrechte auf ein Formular anzuwenden, muss der Acrobat Reader DC Extensions-Dienst Teil Ihrer AEM Forms-Installation sein. Außerdem müssen Sie über gültige Anmeldeinformationen verfügen, mit denen Sie Nutzungsrechte auf PDF-Dokumente anwenden können. Das heißt, Sie müssen den Acrobat Reader DC-Erweiterungs-Service ordnungsgemäß konfigurieren, bevor Sie ein Formular mit aktivierten Nutzungsrechten rendern können. (Siehe [Informationen zum Acrobat Reader DC-Erweiterungs-Service](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).)

>[!NOTE]
>
>Um ein Formular zu rendern, das Nutzungsrechte enthält, müssen Sie eine XDP-Datei und keine PDF-Datei als Eingabe verwenden. Wenn Sie eine PDF-Datei als Eingabe verwenden, wird das Formular weiterhin gerendert. Es handelt sich dann jedoch nicht um ein Formular mit aktivierten Nutzungsrechten.

>[!NOTE]
>
>Sie können ein Formular nicht mit XML-Daten vorab ausfüllen, wenn Sie die folgenden Nutzungsrechte angeben: `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles` oder `enableDigitalSignatures`. (Siehe [Vorausfüllen von Formularen mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein Formular mit aktivierten Nutzungsrechten zu rendern, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Legen Sie Laufzeitoptionen für die Nutzungsrechte fest.
1. Rendern Sie ein Formular mit aktivierten Nutzungsrechten.
1. Schreiben Sie das Formular mit aktivierten Nutzungsrechten in den Client-Webbrowser.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms-Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Service programmgesteuert durchführen können, müssen Sie einen Client für den Forms-Service erstellen.

**Festlegen von Laufzeitoptionen für Nutzungsrechte**

Legen Sie Laufzeitoptionen für Verwendungsrechte fest, um ein Formular mit aktivierten Verwendungsrechten wiederzugeben. Geben Sie den Alias der Berechtigung an, mit der Verwendungsrechte auf ein Formular angewendet werden. Nachdem Sie den Alias-Wert angegeben haben, geben Sie jedes Nutzungsrecht an, das auf das Formular angewendet werden soll.

**Rendern eines Formulars mit aktivierten Nutzungsrechten**

Um ein Formular mit aktivierten Nutzungsrechten zu rendern, verwenden Sie dieselbe Anwendungslogik wie beim Rendern eines Formulars ohne Nutzungsrechte. Der einzige Unterschied besteht darin, dass Sie sicherstellen müssen, dass die Laufzeitoptionen für Nutzungsrechte in Ihrer Anwendungslogik enthalten sind.

>[!NOTE]
>
>Beim Rendern eines Formulars mit aktivierten Nutzungsrechten mithilfe der Forms-Web-Service-API können Sie keine Dateien an das Formular anhängen.

**Schreiben des Formulardaten-Streams in den Client-Webbrowser**

Wenn der Forms-Service ein Formular mit aktivierten Nutzungsrechten rendert, wird ein Formulardaten-Stream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Nach dem Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar. Ein Benutzer, der das Formular mit aktivierten Benutzerrechten in Adobe Reader anzeigt, kann Vorgänge ausführen, die für dieses Formular aktiviert sind.

**Siehe auch**

[Rendern von Formularen mit aktivierten Nutzungsrechten mithilfe der Java-API](#render-rights-enabled-forms-using-the-java-api)

[Rendering von rechteaktivierten Formularen über die Webservice-API](#render-rights-enabled-forms-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendern von Formularen mit aktivierten Nutzungsrechten mithilfe der Java-API {#render-rights-enabled-forms-using-the-java-api}

So rendern Sie ein Formular mit aktivierten Nutzungsrechten mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Optionen für Nutzungsrechte zur Laufzeit festlegen

   * Erstellen Sie ein Objekt `ReaderExtensionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Alias der Berechtigung an, indem Sie die `ReaderExtensionSpec` -Objekt `setReCredentialAlias` -Methode und geben Sie einen Zeichenfolgenwert an, der den Alias-Wert darstellt.
   * Legen Sie die einzelnen Nutzungsrechte fest, indem Sie die entsprechende Methode aufrufen, die zum `ReaderExtensionSpec`-Objekt gehört. Sie können jedoch nur dann ein Nutzungsrecht festlegen, wenn die von Ihnen referenzierte Berechtigung dies zulässt. Das heißt, Sie können keine Nutzungsrechte festlegen, wenn die Berechtigung Ihnen dies nicht erlaubt. Beispiel. Um die Verwendungsrechte festzulegen, mit denen ein Benutzer Formularfelder ausfüllen und das Formular speichern kann, rufen Sie die `ReaderExtensionSpec` -Objekt `setReFillIn` -Methode und -übergabe `true`.

   >[!NOTE]
   >
   >Die `ReaderExtensionSpec` -Objekt `setReCredentialPassword` -Methode. Diese Methode wird vom Forms-Service nicht verwendet.

1. Rendern eines Formulars mit aktivierten Nutzungsrechten

   Rufen Sie die Methode `renderPDFFormWithUsageRights` des Objekts `FormsServiceClient` auf und geben Sie die folgenden Werte weiter:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert.
   * Ein `ReaderExtensionSpec`-Objekt, das Laufzeitoptionen für Nutzungsrechte speichert.
   * A `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.

   Die `renderPDFFormWithUsageRights`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Ermitteln Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode verwenden und den Inhaltstyp der `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie ein Objekt vom Typ `java.io.InputStream`, indem Sie die Methode `getInputStream` des Objekts `com.adobe.idp.Document` aufrufen.
   * Erstellen Sie ein Byte-Array, das mit dem Formulardatenstream gefüllt wird, indem Sie die `InputStream` -Objekt `read` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardatenstreams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Rendern eines berechtigungsaktivierten Formulars mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Rendering von rechteaktivierten Formularen über die Webservice-API {#render-rights-enabled-forms-using-the-web-service-api}

Rendering eines Formulars mit aktivierten Rechten mithilfe der Forms API (Webservice):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Optionen für Nutzungsrechte zur Laufzeit festlegen

   * Erstellen Sie ein Objekt `ReaderExtensionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Alias der Berechtigung an, indem Sie die `ReaderExtensionSpec` -Objekt `setReCredentialAlias` -Methode und geben Sie einen Zeichenfolgenwert an, der den Alias-Wert darstellt.
   * Legen Sie die einzelnen Nutzungsrechte fest, indem Sie die entsprechende Methode aufrufen, die zum `ReaderExtensionSpec`-Objekt gehört. Sie können jedoch nur dann ein Nutzungsrecht festlegen, wenn die von Ihnen referenzierte Berechtigung dies zulässt. Das heißt, Sie können keine Nutzungsrechte festlegen, wenn die Berechtigung Ihnen dies nicht erlaubt. Rufen Sie die `ReaderExtensionSpec` -Objekt `setReFillIn` -Methode und -übergabe `true`.

1. Rendern eines Formulars mit aktivierten Nutzungsrechten

   Rufen Sie die Methode `renderPDFFormWithUsageRights` des Objekts `FormsService` auf und geben Sie die folgenden Werte weiter:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten mit dem Formular zusammenführen wollen, müssen Sie ein `BLOB`-Objekt übergeben, das auf einer leeren XML-Datenquelle basiert. Sie können kein `BLOB`-Objekt übergeben, das Null ist; andernfalls wird eine Ausnahme ausgelöst.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert.
   * Ein `ReaderExtensionSpec`-Objekt, das Laufzeitoptionen für Nutzungsrechte speichert.
   * A `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.

   Die `renderPDFFormWithUsageRights`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Ermitteln Sie den Inhaltstyp des `BLOB`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode verwenden und den Inhaltstyp der `BLOB` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Mit dieser Aufgabe wird dem Byte-Array der Inhalt des `FormsResult`-Objekts zugewiesen.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardatenstreams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Rendern von Formularen mit aktivierten Verwendungsrechten](#rendering-rights-enabled-forms)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
