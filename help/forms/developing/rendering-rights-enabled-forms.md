---
title: Wiedergabe von Rights-aktiviertem Forms
seo-title: Wiedergabe von Rights-aktiviertem Forms
description: Mit dem Forms-Dienst können Sie Formulare wiedergeben, für die Verwendungsrechte gelten. Sie können Formulare mit aktivierten Verwendungsrechten mit der Java-API und der Web-Service-API wiedergeben.
seo-description: Mit dem Forms-Dienst können Sie Formulare wiedergeben, für die Verwendungsrechte gelten. Sie können Formulare mit aktivierten Verwendungsrechten mit der Java-API und der Web-Service-API wiedergeben.
uuid: ce5e4be6-d9b0-4989-a0e1-a8c3b98aed77
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d4c2b2f0-613a-409d-b39b-8e37fdb96eea
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1494'
ht-degree: 5%

---


# Wiedergabe von Rights-Enabled Forms {#rendering-rights-enabled-forms}

Der Forms-Dienst kann Formulare mit Verwendungsrechten wiedergeben. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. Forms, auf das Verwendungsrechte angewendet wurden, werden als Formulare mit aktivierten Verwendungsrechten bezeichnet. Ein Benutzer, der ein Formular mit aktivierten Benutzerrechten in Adobe Reader öffnet, kann Vorgänge ausführen, die für dieses Formular aktiviert sind.

Um Verwendungsrechte auf ein Formular anzuwenden, muss der Acrobat Reader DC Extensions-Dienst Teil Ihrer AEM Forms-Installation sein. Darüber hinaus müssen Sie über eine gültige Berechtigung verfügen, mit der Sie Verwendungsrechte auf PDF-Dokumente anwenden können. Das heißt, Sie müssen den Acrobat Reader DC Extensions-Dienst ordnungsgemäß konfigurieren, bevor Sie ein Formular mit aktivierten Rechten wiedergeben können. (Siehe [Info zum Acrobat Reader DC Extensions-Dienst](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).)

>[!NOTE]
>
>Um ein Formular mit Verwendungsrechten wiederzugeben, müssen Sie eine XDP-Datei als Eingabe und keine PDF-Datei verwenden. Wenn Sie eine PDF-Datei als Eingabe verwenden, wird das Formular weiterhin gerendert. Es handelt sich jedoch nicht um ein Formular mit aktivierten Rechten.

>[!NOTE]
>
>Sie können ein Formular mit XML-Daten nicht im Voraus ausfüllen, wenn Sie die folgenden Verwendungsrechte angeben: `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles` oder `enableDigitalSignatures`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein Formular mit aktivierten Berechtigungen wiederzugeben:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie Laufzeitoptionen für Verwendungsrechte fest.
1. Wiedergabe eines Formulars mit aktivierten Benutzerrechten.
1. Schreiben Sie das Formular mit aktivierten Benutzerrechten in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Forms Client API-Objekt erstellen**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen.

**Laufzeitoptionen für Verwendungsrechte festlegen**

Sie müssen Laufzeitoptionen für Verwendungsrechte festlegen, um ein Formular mit aktivierten Verwendungsrechten wiederzugeben. Sie müssen auch den Alias der Berechtigung angeben, die zum Anwenden von Verwendungsrechten auf ein Formular verwendet wird. Nachdem Sie den Aliaswert angegeben haben, geben Sie jedes Verwendungsrecht an, das auf das Formular angewendet werden soll.

**Wiedergabe eines Formulars mit aktivierten Verwendungsrechten**

Zur Wiedergabe eines Formulars mit aktivierten Verwendungsrechten verwenden Sie dieselbe Anwendungslogik wie die Wiedergabe eines Formulars ohne Verwendungsrechte. Der einzige Unterschied besteht darin, dass Sie sicherstellen müssen, dass die Laufzeitoptionen für Verwendungsrechte in Ihrer Anwendungslogik enthalten sind.

>[!NOTE]
>
>Bei der Wiedergabe eines Formulars mit aktivierten Benutzerrechten mithilfe der Forms-Webdienst-API können Sie keine Dateien an das Formular anhängen.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular mit aktivierten Benutzerrechten wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Nach dem Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar. Ein Benutzer, der das Formular mit aktivierten Benutzerrechten in Adobe Reader anzeigt, kann Vorgänge ausführen, die für dieses Formular aktiviert sind.

**Siehe auch**

[Wiedergabe von Formularen mit aktivierten Verwendungsrechten mit der Java-API](#render-rights-enabled-forms-using-the-java-api)

[Wiedergabe von Formularen mit aktivierten Verwendungsrechten mithilfe der Webdienst-API](#render-rights-enabled-forms-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interaktive PDF forms wiedergeben](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Wiedergeben von Formularen mit aktivierten Verwendungsrechten mithilfe der Java-API {#render-rights-enabled-forms-using-the-java-api}

Wiedergabe eines Formulars mit aktivierten Berechtigungen mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Client API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Laufzeitoptionen für Verwendungsrechte festlegen

   * Erstellen Sie ein Objekt `ReaderExtensionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Alias der Berechtigung an, indem Sie die `ReaderExtensionSpec`-Methode des Objekts `setReCredentialAlias` aufrufen und einen Zeichenfolgenwert angeben, der den Aliaswert darstellt.
   * Legen Sie die Verwendungsrechte fest, indem Sie die entsprechende Methode aufrufen, die zum `ReaderExtensionSpec`-Objekt gehört. Sie können jedoch nur dann ein Verwendungsrecht festlegen, wenn die von Ihnen referenzierte Berechtigung dies zulässt. Das heißt, Sie können keine Verwendungsrechte festlegen, wenn die Berechtigung das Festlegen nicht zulässt. Beispiel. Um das Verwendungsrecht festzulegen, mit dem ein Benutzer Formularfelder ausfüllen und das Formular speichern kann, rufen Sie die `setReFillIn`-Methode des Objekts auf und übergeben Sie `true`.`ReaderExtensionSpec`

   >[!NOTE]
   >
   >Es ist nicht erforderlich, die `ReaderExtensionSpec`-Methode des Objekts `setReCredentialPassword` aufzurufen. Diese Methode wird vom Forms-Dienst nicht verwendet.

1. Wiedergabe eines Formulars mit aktivierten Verwendungsrechten

   Rufen Sie die `renderPDFFormWithUsageRights`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert.
   * Ein `ReaderExtensionSpec`-Objekt, das Verwendungsrechte-Laufzeitoptionen speichert.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.

   Die `renderPDFFormWithUsageRights`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray, das mit dem Formulardatenstream gefüllt wird, indem Sie die `read`-Methode des Objekts aufrufen und das Bytearray als Argument übergeben.`InputStream`
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Wiedergabe eines Formulars mit aktivierten Rechten mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe von Formularen mit aktivierten Verwendungsrechten mithilfe der Webdienst-API {#render-rights-enabled-forms-using-the-web-service-api}

Wiedergabe eines Formulars mit aktivierten Berechtigungen mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Client API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Laufzeitoptionen für Verwendungsrechte festlegen

   * Erstellen Sie ein Objekt `ReaderExtensionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Alias der Berechtigung an, indem Sie die `ReaderExtensionSpec`-Methode des Objekts `setReCredentialAlias` aufrufen und einen Zeichenfolgenwert angeben, der den Aliaswert darstellt.
   * Legen Sie die Verwendungsrechte fest, indem Sie die entsprechende Methode aufrufen, die zum `ReaderExtensionSpec`-Objekt gehört. Sie können jedoch nur dann ein Verwendungsrecht festlegen, wenn die von Ihnen referenzierte Berechtigung dies zulässt. Das heißt, Sie können keine Verwendungsrechte festlegen, wenn die Berechtigung das Festlegen nicht zulässt. Um das Verwendungsrecht festzulegen, mit dem ein Benutzer Formularfelder ausfüllen und das Formular speichern kann, rufen Sie die `setReFillIn`-Methode des Objekts auf und übergeben Sie `true`.`ReaderExtensionSpec`

1. Wiedergabe eines Formulars mit aktivierten Verwendungsrechten

   Rufen Sie die `renderPDFFormWithUsageRights`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten mit dem Formular zusammenführen möchten, müssen Sie ein `BLOB`-Objekt übergeben, das auf einer leeren XML-Datenquelle basiert. Ein `BLOB`-Objekt, das null ist, kann nicht übergeben werden. Andernfalls wird eine Ausnahme ausgelöst.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert.
   * Ein `ReaderExtensionSpec`-Objekt, das Verwendungsrechte-Laufzeitoptionen speichert.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.

   Die `renderPDFFormWithUsageRights`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des Objekts aufrufen.`FormsResult`
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB`-Methode des Objekts `getBinaryData`. Diese Aufgabe weist dem Bytearray den Inhalt des Objekts `FormsResult` zu.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.http.HttpServletResponse` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Wiedergabe von Rights-aktiviertem Forms](#rendering-rights-enabled-forms)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
