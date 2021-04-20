---
title: Übergeben von Dokumenten an FormsService
seo-title: Übergeben von Dokumenten an FormsService
description: 'Übergeben Sie ein com.adobe.idp.Dokument-Objekt, das den Formularentwurf enthält, an den Forms-Dienst. Der Forms-Dienst rendert den Formularentwurf im Objekt com.adobe.idp.Dokument. '
seo-description: Übergeben Sie ein com.adobe.idp.Dokument-Objekt, das den Formularentwurf enthält, an den Forms-Dienst. Der Forms-Dienst rendert den Formularentwurf im Objekt com.adobe.idp.Dokument.
uuid: 841e97f3-ebb8-4340-81a9-b6db11f0ec82
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: e23de3c3-f8a0-459f-801e-a0942fb1c6aa
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 3%

---


# Weiterleiten von Dokumenten an den Forms-Dienst {#passing-documents-to-the-formsservice}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Der AEM Forms-Dienst rendert interaktive PDF forms auf Client-Geräte (in der Regel Webbrowser), um Benutzerdaten zu erfassen. Ein interaktives PDF-Formular basiert auf einem Formularentwurf, der normalerweise als XDP-Datei gespeichert und in Designer erstellt wird. Ab AEM Forms können Sie ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält, an den Forms-Dienst übergeben. Der Forms-Dienst rendert dann den Formularentwurf im `com.adobe.idp.Document`-Objekt.

Ein Vorteil der Übergabe eines `com.adobe.idp.Document`-Objekts an den Forms-Dienst besteht darin, dass andere Dienstvorgänge eine `com.adobe.idp.Document`-Instanz zurückgeben. Das heißt, Sie können eine `com.adobe.idp.Document`-Instanz von einem anderen Dienstvorgang abrufen und rendern. Nehmen Sie beispielsweise an, dass eine XDP-Datei in einem Content Services-Knoten (nicht mehr unterstützt) mit dem Namen `/Company Home/Form Designs` gespeichert wird, wie in der folgenden Abbildung dargestellt.

Sie können die Datei &quot;Loan.xdp&quot;programmgesteuert von Content Services (nicht mehr unterstützt) abrufen und die XDP-Datei an den Forms-Dienst in einem `com.adobe.idp.Document`-Objekt übergeben.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So übergeben Sie ein Dokument, das über Content Services (nicht mehr unterstützt) an den Forms-Dienst erhalten wurde (nicht mehr unterstützt):

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms und ein Dokument Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus Content Services (nicht mehr unterstützt) ab.
1. Rendern Sie das interaktive PDF-Formular.
1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Erstellen eines Forms und eines Dokument Management Client-API-Objekts**

Bevor Sie einen Forms-Dienst-API-Vorgang programmgesteuert durchführen können, erstellen Sie ein Forms Client-API-Objekt. Da dieser Workflow außerdem eine XDP-Datei aus Content Services (nicht mehr unterstützt) abruft, erstellen Sie ein Dokument Management API-Objekt.

**Formularentwurf aus Content Services abrufen (nicht mehr unterstützt)**

Rufen Sie die XDP-Datei über die Java- oder Webdienst-API von Content Services (nicht mehr unterstützt) ab. Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document`-Instanz (oder einer `BLOB`-Instanz, wenn Sie Webdienste verwenden) zurückgegeben. Anschließend können Sie die `com.adobe.idp.Document`-Instanz an den Forms-Dienst übergeben.

**Interaktives PDF-Formular wiedergeben**

Um ein interaktives Formular wiederzugeben, übergeben Sie die `com.adobe.idp.Document`-Instanz, die von Content Services (nicht mehr unterstützt) zurückgegeben wurde, an den Forms-Dienst.

>[!NOTE]
>
>Sie können ein `com.adobe.idp.Document` übergeben, das den Formularentwurf enthält, an den Forms-Dienst. Zwei neue Methoden mit den Namen `renderPDFForm2` und `renderHTMLForm2` akzeptieren ein `com.adobe.idp.Document`-Objekt, das einen Formularentwurf enthält.

**Durchführen einer Aktion mit dem Formulardatenstream**

Je nach Typ der Clientanwendung können Sie das Formular in einen Client-Webbrowser schreiben oder als PDF-Datei speichern. Eine webbasierte Anwendung schreibt das Formular in der Regel in einen Webbrowser. Eine Desktopanwendung speichert das Formular jedoch normalerweise als PDF-Datei.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Übergeben von Dokumenten an den Forms-Dienst mit der Java-API {#pass-documents-to-the-forms-service-using-the-java-api}

Übergeben Sie ein Dokument, das Sie über Content Services (nicht mehr unterstützt) erhalten haben, mithilfe der Forms-Dienst- und Content Services-API (nicht mehr unterstützt) (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;und &quot;adobe-contentservices-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms und eines Dokument Management Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Formularentwurf aus Content Services abrufen (nicht mehr unterstützt)

   Rufen Sie die `retrieveContent`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`DocumentManagementServiceClientImpl`

   * Ein Zeichenfolgenwert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.

   Die `retrieveContent`-Methode gibt ein `CRCResult`-Objekt zurück, das die XDP-Datei enthält. Rufen Sie eine `com.adobe.idp.Document`-Instanz ab, indem Sie die `getDocument`-Methode des Objekts aufrufen.`CRCResult`

1. Interaktives PDF-Formular wiedergeben

   Rufen Sie die `renderPDFForm2`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält, der aus Content Services abgerufen wurde (nicht mehr unterstützt).
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können `null` angeben.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Durchführen einer Aktion mit dem Formulardatenstream

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es mit dem Formulardatenstream, indem Sie die `read`-Methode des Objekts aufrufen. `InputStream` Übergeben Sie das Bytearray als Argument.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Übermitteln von Dokumenten an den Forms-Dienst mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Übergeben von Dokumenten an den Forms-Dienst mithilfe der Webdienst-API {#pass-documents-to-the-forms-service-using-the-web-service-api}

Übergeben Sie ein Dokument, das Sie über Content Services (nicht mehr unterstützt) erhalten haben, mithilfe der Forms-Dienst- und Content Services-API (nicht mehr unterstützt) (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da diese Clientanwendung zwei AEM Forms-Dienste aufruft, erstellen Sie zwei Dienstverweise. Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Forms-Dienst verknüpft ist: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Dokument Management-Dienst verknüpft ist: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Da der Datentyp `BLOB` für beide Dienstverweise gleich ist, müssen Sie den Datentyp `BLOB` bei Verwendung vollständig qualifizieren. Im entsprechenden Web-Service-Schnellmodus-Beginn sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost`durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Forms und eines Dokument Management Client-API-Objekts

   * Erstellen Sie ein `FormsServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `FormsServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der den WSDL-Wert an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormsService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `FormsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `FormsServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `FormsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den `DocumentManagementServiceClient`Dienstclient.

1. Formularentwurf aus Content Services abrufen (nicht mehr unterstützt)

   Abrufen von Inhalten durch Aufrufen der `DocumentManagementServiceClient`-Methode des Objekts `retrieveContent` und Übergeben der folgenden Werte:

   * Ein Zeichenfolgenwert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   * Ein Parameter für die Zeichenfolgenausgabe, der den Wert des Durchsuchen-Links speichert.
   * Ein `BLOB`-Ausgabeparameter, der den Inhalt speichert. Mit diesem Ausgabeparameter können Sie den Inhalt abrufen.
   * Ein `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType`-Ausgabeparameter, der Inhaltsattribute speichert.
   * Ein Ausgabeparameter `CRCResult`. Anstelle dieses Objekts können Sie den Ausgabeparameter `BLOB` verwenden, um den Inhalt abzurufen.

1. Interaktives PDF-Formular wiedergeben

   Rufen Sie die `renderPDFForm2`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein `BLOB`-Objekt, das den Formularentwurf enthält, der aus Content Services abgerufen wurde (nicht mehr unterstützt).
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `BLOB`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können `null` angeben.
   * Ein `Map`-Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein langer Ausgabeparameter, mit dem die Seitenanzahl gespeichert wird.
   * Ein Zeichenfolgenausgabeparameter, mit dem der Gebietsschemawert gespeichert wird.
   * Ein Ausgabeparameter `FormsResult`, der zum Speichern des interaktiven PDF-Formulars `.` verwendet wird

   Die `renderPDFForm2`-Methode gibt ein `FormsResult`-Objekt zurück, das das interaktive PDF-Formular enthält.

1. Durchführen einer Aktion mit dem Formulardatenstream

   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie den Wert des Felds `outputContent` des Objekts abrufen.`FormsResult`
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des interaktiven PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB`-Objekts speichert, das vom `FormsResult`-Objekt abgerufen wird. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
