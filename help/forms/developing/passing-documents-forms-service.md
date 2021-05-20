---
title: Übergeben von Dokumenten an den FormsService
seo-title: Übergeben von Dokumenten an den FormsService
description: 'Übergeben Sie ein com.adobe.idp.Document -Objekt, das den Formularentwurf enthält, an den Forms-Dienst. Der Forms-Dienst rendert den Formularentwurf im Objekt com.adobe.idp.Document . '
seo-description: Übergeben Sie ein com.adobe.idp.Document -Objekt, das den Formularentwurf enthält, an den Forms-Dienst. Der Forms-Dienst rendert den Formularentwurf im Objekt com.adobe.idp.Document .
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
workflow-type: tm+mt
source-wordcount: '1714'
ht-degree: 2%

---

# Übergeben von Dokumenten an den Forms-Dienst {#passing-documents-to-the-formsservice}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Der AEM Forms-Dienst rendert interaktive PDF forms an Client-Geräte, normalerweise Webbrowser, um Benutzerinformationen zu erfassen. Ein interaktives PDF-Formular basiert auf einem Formularentwurf, der normalerweise als XDP-Datei gespeichert und in Designer erstellt wird. Ab AEM Forms können Sie ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält, an den Forms-Dienst übergeben. Der Forms-Dienst rendert dann den Formularentwurf im Objekt `com.adobe.idp.Document` .

Ein Vorteil der Übergabe eines `com.adobe.idp.Document` -Objekts an den Forms-Dienst besteht darin, dass andere Dienstvorgänge eine `com.adobe.idp.Document` -Instanz zurückgeben. Das heißt, Sie können eine `com.adobe.idp.Document`-Instanz von einem anderen Dienstvorgang abrufen und rendern. Angenommen, eine XDP-Datei wird in einem Content Services-Knoten mit dem Namen `/Company Home/Form Designs` gespeichert, wie in der folgenden Abbildung dargestellt.

Sie können Loan.xdp programmgesteuert aus Content Services (nicht mehr unterstützt) abrufen und die XDP-Datei in einem `com.adobe.idp.Document`-Objekt an den Forms-Dienst übergeben.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein Dokument aus Content Services (nicht mehr unterstützt) an den Forms-Dienst zu übergeben:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms- und ein Document Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus Content Services ab (nicht mehr unterstützt).
1. Rendern Sie das interaktive PDF-Formular.
1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Forms und ein Client-API-Objekt für Document Management erstellen**

Bevor Sie einen Forms-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Forms Client-API-Objekt. Da mit diesem Workflow eine XDP-Datei aus Content Services (nicht mehr unterstützt) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)**

Rufen Sie die XDP-Datei über die Java- oder Webdienst-API von Content Services (nicht mehr unterstützt) ab. Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document`-Instanz (oder einer `BLOB`-Instanz zurückgegeben, wenn Sie Webdienste verwenden). Anschließend können Sie die `com.adobe.idp.Document`-Instanz an den Forms-Dienst übergeben.

**Rendern eines interaktiven PDF-Formulars**

Übergeben Sie zum Rendern eines interaktiven Formulars die `com.adobe.idp.Document`-Instanz, die von Content Services (nicht mehr unterstützt) zurückgegeben wurde, an den Forms-Dienst.

>[!NOTE]
>
>Sie können einen `com.adobe.idp.Document` übergeben, der den Formularentwurf enthält, an den Forms-Dienst. Zwei neue Methoden namens `renderPDFForm2` und `renderHTMLForm2` akzeptieren ein `com.adobe.idp.Document`-Objekt, das einen Formularentwurf enthält.

**Ausführen einer Aktion mit dem Formulardatenstream**

Je nach Typ der Clientanwendung können Sie das Formular in einen Client-Webbrowser schreiben oder es als PDF-Datei speichern. Eine webbasierte Anwendung schreibt das Formular normalerweise in den Webbrowser. Eine Desktop-Applikation speichert das Formular jedoch normalerweise als PDF-Datei.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java-API {#pass-documents-to-the-forms-service-using-the-java-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) mithilfe der Forms-Dienst- und Content Services-API (nicht mehr unterstützt) erhalten wurde:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar und adobe-contentservices-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Forms und ein Client-API-Objekt für Document Management erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `FormsServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)

   Rufen Sie die `retrieveContent` -Methode des Objekts `DocumentManagementServiceClientImpl` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.

   Die `retrieveContent`-Methode gibt ein `CRCResult`-Objekt zurück, das die XDP-Datei enthält. Rufen Sie eine `com.adobe.idp.Document` -Instanz ab, indem Sie die `getDocument` -Methode des Objekts `CRCResult` aufrufen.

1. Rendern eines interaktiven PDF-Formulars

   Rufen Sie die `renderPDFForm2` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das den Formularentwurf enthält, der von Content Services abgerufen wurde (veraltet).
   * Ein `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` -Objekt.
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können `null` angeben.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Ausführen einer Aktion mit dem Formulardatenstream

   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `FormsResult` -Methode des Objekts &quot;s `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `com.adobe.idp.Document` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `com.adobe.idp.Document` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein `java.io.InputStream` -Objekt, indem Sie die `getInputStream` -Methode des Objekts `com.adobe.idp.Document` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `read` -Methode des Objekts `InputStream` aufrufen. Übergeben Sie das Byte-Array als Argument.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.ServletOutputStream` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Übergeben von Dokumenten an den Forms-Dienst mithilfe der Webdienst-API {#pass-documents-to-the-forms-service-using-the-web-service-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) mithilfe der Forms-Dienst- und Content Services-API (nicht mehr unterstützt) abgerufen wurde:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da diese Client-Anwendung zwei AEM Forms-Dienste aufruft, erstellen Sie zwei Dienstverweise. Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Forms-Dienst verknüpft ist: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Document Management-Dienst verknüpft ist: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Da der Datentyp `BLOB` für beide Dienstverweise gleich ist, müssen Sie den Datentyp `BLOB` bei Verwendung vollständig qualifizieren. Im entsprechenden Webdienst-Schnellstart sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost`durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Forms und ein Client-API-Objekt für Document Management erstellen

   * Erstellen Sie ein `FormsServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `FormsServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormsService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `FormsServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `FormsServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `FormsServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den Service-Client `DocumentManagementServiceClient`.

1. Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)

   Rufen Sie Inhalte ab, indem Sie die `retrieveContent` -Methode des Objekts `DocumentManagementServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   * Ein string -Ausgabeparameter, der den Wert des Durchsuchen-Links speichert.
   * Ein `BLOB`-Ausgabeparameter, der den Inhalt speichert. Sie können diesen Ausgabeparameter verwenden, um den Inhalt abzurufen.
   * Ein `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType`-Ausgabeparameter, der Inhaltsattribute speichert.
   * Ein `CRCResult`-Ausgabeparameter. Anstatt dieses Objekt zu verwenden, können Sie den Ausgabeparameter `BLOB` verwenden, um den Inhalt abzurufen.

1. Rendern eines interaktiven PDF-Formulars

   Rufen Sie die `renderPDFForm2` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das den Formularentwurf enthält, der von Content Services abgerufen wurde (veraltet).
   * Ein `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `BLOB` -Objekt.
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Laufzeitoptionen angeben möchten.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können `null` angeben.
   * Ein `Map` -Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein long -Ausgabeparameter, der zum Speichern der Seitenzahl verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des Gebietsschemawerts verwendet wird.
   * Ein `FormsResult`-Ausgabeparameter, der zum Speichern des interaktiven PDF-Formulars `.` verwendet wird

   Die `renderPDFForm2`-Methode gibt ein `FormsResult`-Objekt zurück, das das interaktive PDF-Formular enthält.

1. Ausführen einer Aktion mit dem Formulardatenstream

   * Erstellen Sie ein `BLOB` -Objekt, das Formulardaten enthält, indem Sie den Wert des `outputContent` -Felds des Objekts `FormsResult` abrufen.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert für den Dateispeicherort des interaktiven PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das vom `FormsResult`-Objekt abgerufen wird. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
