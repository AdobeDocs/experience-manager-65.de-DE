---
title: Übergeben von Dokumenten an den Forms-Service
seo-title: Passing Documents to the FormsService
description: 'Übergeben Sie ein com.adobe.idp.Document-Objekt, das den Formularentwurf enthält, an den Forms-Service. Der Forms-Service gibt den Formularentwurf wieder, der sich im com.adobe.idp.Document-Objekt befindet. '
seo-description: Pass a com.adobe.idp.Document object that contains the form design to the Forms service. The Forms service renders the form design located in the com.adobe.idp.Document object.
uuid: 841e97f3-ebb8-4340-81a9-b6db11f0ec82
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: e23de3c3-f8a0-459f-801e-a0942fb1c6aa
role: Developer
exl-id: 29c7ebda-407a-464b-a9db-054163f5b737
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1684'
ht-degree: 100%

---

# Übergeben von Dokumenten an den Forms-Service {#passing-documents-to-the-formsservice}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Der AEM Forms-Service gibt interaktive PDF-Formulare an Client-Geräte aus, in der Regel Webbrowser, um Informationen von Benutzern zu erfassen. Ein interaktives PDF-Formular basiert auf einem Formularentwurf, der normalerweise in Designer erstellt und als XDP-Datei gespeichert wird. Was AEM Forms betrifft, können Sie ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält, an den Forms-Service übergeben. Der Forms-Service gibt dann den Formularentwurf wieder, der sich im `com.adobe.idp.Document`-Objekt befindet.

Ein Vorteil der Übergabe eines `com.adobe.idp.Document`-Objekts an den Forms-Service ist, dass andere Service-Vorgänge eine `com.adobe.idp.Document`-Instanz zurückgeben. Das heißt, Sie können eine `com.adobe.idp.Document`-Instanz von einem anderen Service-Vorgang erhalten und sie wiedergeben. Nehmen Sie zum Beispiel an, dass eine XDP-Datei in einem Knoten von Content Services (veraltet) mit dem Namen `/Company Home/Form Designs` gespeichert ist, wie in der folgenden Abbildung gezeigt.

Sie können Loan.xdp programmgesteuert von Content Services (veraltet) abrufen und die XDP-Datei in einem `com.adobe.idp.Document`-Objekt an den Forms-Service übergeben.

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein Dokument aus Content Services (veraltet) an den Forms-Service zu übergeben:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms- und ein Document Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus Content Services ab (veraltet).
1. Geben Sie das interaktive PDF-Formular wieder.
1. Führen Sie eine Aktion mit dem Formulardaten-Stream aus.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen eines Forms- und eines Document Management Client-API-Objekts**

Bevor Sie einen Forms-Service-API-Vorgang programmgesteuert durchführen können, erstellen Sie ein Forms-Client-API-Objekt. Da mit diesem Workflow eine XDP-Datei aus Content Services (veraltet) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus Content Services (veraltet)**

Rufen Sie die XDP-Datei aus Content Services (veraltet) ab, indem Sie die Java- oder Webservice-API verwenden. Die XDP-Datei wird in einer `com.adobe.idp.Document`-Instanz zurückgegeben (oder in einer `BLOB`-Instanz, wenn Sie Web-Services verwenden). Sie können dann die `com.adobe.idp.Document`-Instanz an den Forms-Service übergeben.

**Wiedergeben eines interaktiven PDF-Formulars**

Um ein interaktives Formular zu rendern, übergeben Sie die `com.adobe.idp.Document`-Instanz, die von Content Services (veraltet) an den Forms-Service zurückgegeben wurde.

>[!NOTE]
>
>Sie können ein `com.adobe.idp.Document`, das den Formularentwurf enthält, an den Forms-Service übergeben. Zwei neue Methoden namens `renderPDFForm2` und `renderHTMLForm2` akzeptieren ein `com.adobe.idp.Document`-Objekt, das einen Formularentwurf enthält.

**Ausführen einer Aktion mit dem Formulardaten-Stream**

Je nach Art des Client-Programms können Sie das Formular in einen Client-Webbrowser schreiben oder das Formular als PDF-Datei speichern. Bei einem Web-basierten Programm wird das Formular normalerweise in den Webbrowser geschrieben. Ein Desktop-Programm hingegen speichert das Formular in der Regel als PDF-Datei.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Übergeben von Dokumenten an den Forms-Service mithilfe der Java-API {#pass-documents-to-the-forms-service-using-the-java-api}

Übergeben Sie ein Dokument, das von Content Services (veraltet) mithilfe der Forms-Service- und Content Services-API (veraltet) erhalten wurde:

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ oder „adobe-contentservices-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms- und eines Document Management Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)

   Rufen Sie die Methode `retrieveContent` des `DocumentManagementServiceClientImpl`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgewert, der den Speicher angibt, dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der die Version angibt. Dieser Wert ist ein optionaler Parameter, und Sie können auch eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.

   Die Methode `retrieveContent` gibt ein `CRCResult`-Objekt zurück, das die XDP-Datei enthält. Sie können eine `com.adobe.idp.Document`-Instanz erhalten, indem Sie die Methode `getDocument` des `CRCResult`-Objekts aufrufen.

1. Wiedergeben eines interaktiven PDF-Formulars

   Rufen Sie die Methode `renderPDFForm2` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält, der von Content Services (veraltet) abgerufen wurde.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter, für den Sie auch `null` angeben können.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die Methode `renderPDFForm` gibt ein `FormsResult`-Objekt zurück, das einen Formulardaten-Stream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Ausführen einer Aktion mit dem Formulardaten-Stream

   * Sie können ein `com.adobe.idp.Document`-Objekt erstellen, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Content-Typ des `com.adobe.idp.Document`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `com.adobe.idp.Document`-Objekts übergeben.
   * Sie können ein `javax.servlet.ServletOutputStream`-Objekt erstellen, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Sie können ein `java.io.InputStream`-Objekt erstellen, indem Sie die Methode `getInputStream` des `com.adobe.idp.Document`-Objekts aufrufen.
   * Sie können ein Byte-Array erstellen und es mit dem Formulardaten-Stream füllen, indem Sie die Methode `read` des `InputStream`-Objekts aufrufen. Übergeben Sie das Byte-Array als Argument.
   * Rufen Sie die Methode `write` des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formulardaten-Stream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Übergeben von Dokumenten an den Forms-Service mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Übergeben von Dokumenten an den Forms-Service mithilfe der Webservice-API {#pass-documents-to-the-forms-service-using-the-web-service-api}

Übergeben Sie ein Dokument, das von Content Services (veraltet) mithilfe der Forms-Service- und Content Services-API (veraltet) abgerufen wurde:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da dieses Client-Programm zwei AEM Forms-Services aufruft, erstellen Sie zwei Service-Verweise. Verwenden Sie die folgende WSDL-Definition für den Service-Verweis, der mit dem Forms-Service verknüpft ist: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für den Service-Verweis, der mit dem Document Management-Service verknüpft ist: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Da der Datentyp `BLOB` für beide Service-Verweise verwendet wird, müssen Sie den Datentyp `BLOB` vollständig qualifizieren, wenn Sie ihn verwenden. In der entsprechenden Kurzanleitung für den Webservice sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, der AEM Forms hostet.

1. Erstellen eines Forms- und eines Document Management Client-API-Objekts

   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `FormsServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der dem AEM Forms-Service die WSDL angibt (z. B. `http://localhost:8080/soap/services/FormsService?WSDL`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `FormsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `FormsServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `FormsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie den Konstantenwert `HttpClientCredentialType.Basic` dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` zu.
   * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den `DocumentManagementServiceClient`Service-Client.

1. Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)

   Rufen Sie den Inhalt ab, indem Sie die `retrieveContent`-Methode des `DocumentManagementServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgewert, der den Speicher angibt, dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Kennzeichenfolgewert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der die Version angibt. Dieser Wert ist ein optionaler Parameter, und Sie können auch eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   * Der Ausgabeparameter einer Kennzeichenfolge, der den Wert des Browse-Links speichert.
   * Ein `BLOB`-Ausgabeparameter, der den Inhalt speichert. Sie können diesen Ausgabeparameter verwenden, um den Inhalt abzurufen.
   * Ein `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType`-Ausgabeparameter, der Inhaltsattribute speichert.
   * Ein `CRCResult`-Ausgabeparameter. Anstatt dieses Objekt zu verwenden, können Sie den `BLOB`-Ausgabeparameter zum Abrufen des Inhalts verwenden.

1. Wiedergeben eines interaktiven PDF-Formulars

   Rufen Sie die `renderPDFForm2`-Methode des `FormsServiceClient`-Objekts ab und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das den Formularentwurf enthält, der von Content Services abgerufen wurde (nicht mehr unterstützt).
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie eine leeres `BLOB`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Laufzeitoptionen festlegen möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können `null` angeben.
   * Ein `Map`-Objekt, das Dateianhänge speichert. Dieser Wert ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein langer Ausgabeparameter, der zum Speichern der Seitenzahl verwendet wird.
   * Ein Ausgabeparameter der Kennzeichenfolge, der zum Speichern des Gebietsschemawerts verwendet wird.
   * Ein `FormsResult`-Ausgabeparameter, der zum Speichern des interaktiven PDF-Formulars verwendet wird `.`

   Die `renderPDFForm2`-Methode gibt ein `FormsResult`-Objekt aus, das das interaktive PDF-Formular enthält.

1. Ausführen einer Aktion mit dem Formulardaten-Stream

   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie den Wert des `outputContent`-Feldes des `FormsResult`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Kennzeichenfolgewert, der den Dateispeicherort des interaktiven PDF-Dokuments und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das aus dem `FormsResult`-Objekt abgerufen wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des `System.IO.BinaryWriter`-Objekts verwenden und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
