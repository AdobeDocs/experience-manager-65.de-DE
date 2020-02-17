---
title: Übergeben von Dokumenten an den FormsService
seo-title: Übergeben von Dokumenten an den FormsService
description: 'null'
seo-description: 'null'
uuid: 841e97f3-ebb8-4340-81a9-b6db11f0ec82
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: e23de3c3-f8a0-459f-801e-a0942fb1c6aa
translation-type: tm+mt
source-git-commit: 7cbe3e94eddb81925072f68388649befbb027e6d

---


# Übergeben von Dokumenten an den Forms-Dienst {#passing-documents-to-the-formsservice}

Der AEM Forms-Dienst rendert interaktive PDF-Formulare auf Client-Geräten, üblicherweise Webbrowsern, um Informationen von Benutzern zu erfassen. Ein interaktives PDF-Formular basiert auf einem Formularentwurf, der normalerweise als XDP-Datei gespeichert und in Designer erstellt wird. Ab AEM Forms können Sie ein `com.adobe.idp.Document` Objekt, das den Formularentwurf enthält, an den Forms-Dienst übergeben. Der Forms-Dienst rendert dann den Formularentwurf im `com.adobe.idp.Document` Objekt.

Ein Vorteil der Übergabe eines `com.adobe.idp.Document` Objekts an den Forms-Dienst besteht darin, dass andere Dienstvorgänge eine `com.adobe.idp.Document` Instanz zurückgeben. Das heißt, Sie können eine `com.adobe.idp.Document` Instanz von einem anderen Dienstvorgang abrufen und wiedergeben. Nehmen wir beispielsweise an, dass eine XDP-Datei in einem Content Services-Knoten (nicht mehr unterstützt) mit dem Namen gespeichert wird `/Company Home/Form Designs`, wie in der folgenden Abbildung dargestellt.

Sie können die Datei &quot;Loan.xdp&quot;programmgesteuert aus Content Services (nicht mehr unterstützt) abrufen und die XDP-Datei an den Forms-Dienst innerhalb eines `com.adobe.idp.Document` Objekts weiterleiten.

>[!NOTE]
>
>For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um ein von Content Services (nicht mehr unterstützt) abgerufenes Dokument an den Forms-Dienst zu übergeben:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms- und ein Document Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus Content Services (nicht mehr unterstützt) ab.
1. Interaktives PDF-Formular wiedergeben
1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Erstellen von Formularen und einem Document Management Client-API-Objekt**

Bevor Sie einen Forms-Dienst-API-Vorgang programmgesteuert durchführen können, erstellen Sie ein Forms Client-API-Objekt. Da dieser Workflow außerdem eine XDP-Datei aus Content Services (nicht mehr unterstützt) abruft, erstellen Sie ein Document Management API-Objekt.

**Formularentwurf aus Content Services abrufen (nicht mehr unterstützt)**

Rufen Sie die XDP-Datei über die Java- oder Webdienst-API von Content Services (nicht mehr unterstützt) ab. Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document` Instanz zurückgegeben (oder eine `BLOB` Instanz, wenn Sie Webdienste verwenden). Anschließend können Sie die `com.adobe.idp.Document` Instanz an den Forms-Dienst weiterleiten.

**Interaktives PDF-Formular wiedergeben**

Übergeben Sie zum Rendern eines interaktiven Formulars die `com.adobe.idp.Document` Instanz, die von Content Services (nicht mehr unterstützt) zurückgegeben wurde, an den Forms-Dienst.

>[!NOTE]
>
>Sie können einen Formularentwurf `com.adobe.idp.Document` an den Forms-Dienst übergeben. Zwei neue Methoden mit dem Namen `renderPDFForm2` und `renderHTMLForm2` der Annahme eines `com.adobe.idp.Document` Objekts, das einen Formularentwurf enthält.

**Durchführen einer Aktion mit dem Formulardatenstream**

Je nach Typ der Clientanwendung können Sie das Formular in einen Client-Webbrowser schreiben oder als PDF-Datei speichern. Eine webbasierte Anwendung schreibt das Formular in der Regel in einen Webbrowser. Eine Desktopanwendung speichert das Formular jedoch normalerweise als PDF-Datei.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java-API {#pass-documents-to-the-forms-service-using-the-java-api}

Übergeben eines von Content Services (nicht mehr unterstützt) erhaltenen Dokuments mithilfe der Forms-Dienst- und Content Services-API (nicht mehr unterstützt) (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;und &quot;adobe-contentservices-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen von Formularen und einem Document Management Client-API-Objekt

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Create an `FormsServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Formularentwurf aus Content Services abrufen (nicht mehr unterstützt)

   Rufen Sie die `DocumentManagementServiceClientImpl` Objektmethode `retrieveContent` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Store angibt, in dem der Inhalt hinzugefügt wird. The default store is `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   Die `retrieveContent` Methode gibt ein `CRCResult` Objekt zurück, das die XDP-Datei enthält. Rufen Sie eine `com.adobe.idp.Document` Instanz ab, indem Sie die `CRCResult` Objektmethode aufrufen `getDocument` .

1. Interaktives PDF-Formular wiedergeben

   Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFForm2` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` Objekt, das den Formularentwurf enthält, der aus Content Services abgerufen wurde (nicht mehr unterstützt).
   * Ein `com.adobe.idp.Document` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` Objekt.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter und Sie können angeben, `null` wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec` Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können ihn angeben `null`.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter. Sie können angeben, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   Die `renderPDFForm` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Durchführen einer Aktion mit dem Formulardatenstream

   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` Objektmethode `read` aufrufen. Übergeben Sie das Bytearray als Argument.
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Übergeben von Dokumenten an den Forms-Dienst mithilfe der Webdienst-API {#pass-documents-to-the-forms-service-using-the-web-service-api}

Übergeben eines von Content Services (nicht mehr unterstützt) erhaltenen Dokuments mithilfe der Forms-Dienst- und Content Services-API (nicht mehr unterstützt) (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da diese Clientanwendung zwei AEM Forms-Dienste aufruft, erstellen Sie zwei Dienstverweise. Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Forms-Dienst verknüpft ist: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Document Management-Dienst verknüpft ist: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Da der `BLOB` Datentyp für beide Dienstverweise gleich ist, müssen Sie den Datentyp bei der Verwendung vollständig qualifizieren `BLOB` . Im entsprechenden Webdienst-Schnellstart sind alle `BLOB` Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost`durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen von Formularen und einem Document Management Client-API-Objekt

   * Create a `FormsServiceClient` object by using its default constructor.
   * Create a `FormsServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/FormsService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `FormsServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `FormsServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `FormsServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.
   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den `DocumentManagementServiceClient`Dienstclient.

1. Formularentwurf aus Content Services abrufen (nicht mehr unterstützt)

   Abrufen von Inhalten durch Aufrufen der `DocumentManagementServiceClient` `retrieveContent` Objektmethode und Übergeben der folgenden Werte:

   * Ein Zeichenfolgenwert, der den Store angibt, in dem der Inhalt hinzugefügt wird. The default store is `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   * Ein Parameter für die Zeichenfolgenausgabe, der den Wert des Durchsuchen-Links speichert.
   * Ein `BLOB` Ausgabeparameter, der den Inhalt speichert. Mit diesem Ausgabeparameter können Sie den Inhalt abrufen.
   * Ein `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` Ausgabeparameter, der Inhaltsattribute speichert.
   * Ein `CRCResult` Ausgabeparameter. Anstatt dieses Objekt zu verwenden, können Sie den Inhalt mit dem `BLOB` Ausgabeparameter abrufen.

1. Interaktives PDF-Formular wiedergeben

   Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFForm2` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` Objekt, das den Formularentwurf enthält, der aus Content Services abgerufen wurde (nicht mehr unterstützt).
   * Ein `BLOB` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `BLOB` Objekt.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter und Sie können angeben, `null` wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec` Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können ihn angeben `null`.
   * Ein `Map` Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter. Sie können angeben, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein langer Ausgabeparameter, mit dem die Seitenanzahl gespeichert wird.
   * Ein Zeichenfolgenausgabeparameter, mit dem der Gebietsschemawert gespeichert wird.
   * Ein `FormsResult` Ausgabeparameter, mit dem das interaktive PDF-Formular gespeichert wird `.`
   Die `renderPDFForm2` Methode gibt ein `FormsResult` Objekt zurück, das das interaktive PDF-Formular enthält.

1. Durchführen einer Aktion mit dem Formulardatenstream

   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie den Wert des `FormsResult` Objektfelds abrufen `outputContent` .
   * Create a `System.IO.FileStream` object by invoking its constructor. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des interaktiven PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert, das vom `FormsResult` Objekt abgerufen wird. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
