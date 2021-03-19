---
title: Konvertieren von PDF-Dateien in PostScript- und Bilddateien
seo-title: Konvertieren von PDF-Dateien in PostScript- und Bilddateien
description: Verwenden Sie den Convert PDF-Dienst, um PDF-Dokumente mithilfe der Java API und der Web Service API in PostScript und eine Reihe von Bildformaten (JPEG, JPEG 2000, PNG und TIFF) zu konvertieren.
seo-description: Verwenden Sie den Convert PDF-Dienst, um PDF-Dokumente mithilfe der Java API und der Web Service API in PostScript und eine Reihe von Bildformaten (JPEG, JPEG 2000, PNG und TIFF) zu konvertieren.
uuid: 07da0391-7180-4197-aaa6-ae753d753b84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: f8707752-2c83-461a-b83d-708754b0f3f6
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2847'
ht-degree: 5%

---


# Konvertieren von PDF-Dateien in PostScript- und Bilddateien {#converting-pdf-to-postscript-andimage-files}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

**Informationen zum Convert PDF-Dienst**

Der Convert PDF-Dienst konvertiert PDF-Dokumente in PostScript und eine Reihe von Bildformaten (JPEG, JPEG 2000, PNG und TIFF). Das Konvertieren eines PDF-Dokuments in PostScript ist nützlich für die unbeaufsichtigte serverbasierte Druckausgabe auf PostScript-Druckern. Das Konvertieren eines PDF-Dokuments in eine mehrseitige TIFF-Datei ist beim Archivieren von Dokumenten in Content Management-Systemen praktisch, die PDF-Dokumente nicht unterstützen.

Sie können diese Aufgaben mithilfe des Convert PDF-Dienstes ausführen:

* Konvertieren von PDF-Dokumenten in PostScript – 
* Konvertieren von PDF-Dokumenten in Bildformate

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PDF-Dokumenten in PostScript {#converting-pdf-documents-to-postscript}

In diesem Thema wird beschrieben, wie Sie mit der Convert PDF Service API (Java und Webdienst) PDF-Dokumente programmgesteuert in PostScript-Dateien konvertieren können. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss ein nicht interaktives PDF-Dokument sein. Wenn Sie also versuchen, ein interaktives PDF-Dokument in eine PostScript-Datei zu konvertieren, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So konvertieren Sie ein PDF-Dokument in eine PostScript-Datei:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Convert PDF-Dienstclient.
1. Verweisen Sie auf das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.
1. Legen Sie Laufzeitoptionen für Konversionen fest.
1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.
1. Speichern Sie die PostScript-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Convert PDF-Clients**

Bevor Sie einen Convert PDF-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Convert PDF-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ConvertPdfServiceClient`-Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie ein `ConvertPDFServiceService`-Objekt.

Dieser Abschnitt verwendet Webdienst-Funktionen, die in AEM Forms eingeführt werden. Um auf neue Funktionen zugreifen zu können, müssen Sie Ihr Proxy-Objekt mit dem Attribut `lc_version` erstellen. (Siehe &quot;Zugriff auf neue Funktionen mithilfe von Webdiensten&quot;in [Aufrufen von AEM Forms mithilfe von Web-Services](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

**Verweisen Sie auf das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll**

Verweisen Sie auf das PDF-Dokument, das Sie in eine PostScript-Datei konvertieren möchten. Wie bereits in diesem Thema erwähnt, muss das PDF-Dokument ein nicht interaktives PDF-Dokument sein. Wenn Sie versuchen, ein interaktives PDF-Dokument in eine PostScript-Datei zu konvertieren, wird eine Ausnahme ausgelöst.

**Optionen für die Konvertierungslaufzeit festlegen**

Beim Konvertieren eines PDF-Dokuments in eine PostScript-Datei können Sie Laufzeitoptionen definieren, die den erstellten PostScript-Typ angeben. Sie können beispielsweise eine PostScript-Datei der Stufe 3 definieren.

Die generierte PostScript-Datei spiegelt in der Regel die Größe des PDF-Eingabedatums wider. Wenn Sie die Option `ShrinkToFit` auswählen (mit der die Ausgabe der PostScript-Datei an die Seitengröße angepasst wird), wird kein Unterschied zwischen dem PDF-Eingabedatum und der generierten PostScript-Dokument angezeigt. Die Option `ShrinkToFit` wird nur wirksam, wenn Sie die Option zum Drucken auf einer kleineren Seitengröße als das PDF-Dokument für die Eingabe auswählen. Um ein kleineres Seitenformat auszuwählen, definieren Sie die Option `PageSize`. Darüber hinaus wird empfohlen, die Option `RotateAndCenter` auf `true` einzustellen, um die richtige PostScript-Ausgabe zu erhalten.

Wenn Sie die Option `ExpandToFit` auswählen (mit der die Ausgabe der PostScript-Datei an die Seite angepasst wird), wird diese Option nur dann wirksam, wenn Sie die Druckausgabe auf einem größeren Seitenformat als das PDF-Dokument für die Eingabe vornehmen. Um ein größeres Seitenformat auszuwählen, definieren Sie die Option `PageSize`. Darüber hinaus wird empfohlen, die Option `RotateAndCenter` auf `true` einzustellen, um die richtige PostScript-Ausgabe zu erhalten.

>[!NOTE]
>
>Informationen zu den eingestellten Laufzeitwerten finden Sie in der `ToPSOptionsSpec`-Klassenreferenz in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**PDF-Dokument in eine PostScript-Datei konvertieren**

Nachdem Sie den Dienstclient erstellt und Laufzeitoptionen festgelegt haben, können Sie den PostScript-Konvertierungsvorgang aufrufen. Dieser Vorgang erfordert Informationen über das zu konvertierende Dokument, einschließlich der bevorzugten PostScript-Ebene für das Zielgruppe-Dokument.

**PostScript-Datei speichern**

Nachdem Sie das PDF-Dokument in PostScript konvertiert haben, können Sie die Ausgabe als PostScript-Datei speichern.

**Siehe auch**

[Konvertieren eines PDF-Dokuments mit der Java-API in PS](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Konvertieren eines PDF-Dokuments in PS mithilfe der Webdienst-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-Dienst-API-Beginn konvertieren](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in PS mit der Java-API {#convert-a-pdf-document-to-ps-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service API (Java) in PostScript:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-convertpdf-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt mit dem Konstruktor und übergeben Sie einen Zeichenfolgenwert, der den Speicherort des zu konvertierenden PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument mithilfe des Konstruktors `com.adobe.idp.Document` speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen für Konversionen fest.

   * Erstellen Sie ein `ToPSOptionsSpec`-Objekt, indem Sie den Konstruktor aufrufen.
   * Legen Sie Laufzeitoptionen fest, indem Sie eine geeignete Methode aufrufen, die zum `ToPSOptionsSpec`-Objekt gehört. Um beispielsweise die erstellte PostScript-Ebene zu definieren, rufen Sie die `ToPSOptionsSpec`-Auflistung des Objekts auf und übergeben Sie einen `PSLevel`-Wert, der die PostScript-Ebene angibt. `setPsLevel` Informationen zu allen verfügbaren Laufzeitwerten finden Sie in der `ToPSOptionsSpec`-Klassenreferenz in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.

   Rufen Sie die `ConvertPdfServiceClient`Methode des Objekts `toPS2` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument darstellt, das in eine PostScript-Datei konvertiert werden soll.
   * Ein `ToPSOptionsSpec`-Objekt, das PostScript-Laufzeitoptionen angibt.

   Die `toPS2`-Methode gibt ein `Document`-Objekt zurück, das das neue PostScript-Dokument enthält.

1. Speichern Sie die PostScript-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .ps lautet.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `toPS2`-Methode zurückgegeben wurde).`Document`

**Siehe auch**

[Zusammenfassung der Schritte](converting-pdf-postscript-image-files.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Konvertieren eines PDF-Dokuments in PostScript mit der Java-API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren eines PDF-Dokuments in PS mithilfe der Webdienst-API {#convert-a-pdf-document-to-ps-using-the-web-service-api}

Konvertieren eines PDF-Dokuments mithilfe der Convert PDF Service API (Webdienst) in PostScript:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `ConvertPdfServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `ConvertPdfServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Verweisen Sie auf das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das in eine PostScript-Datei konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu konvertierenden PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die Stream-Länge zum Lesen übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen für Konversionen fest.

   * Erstellen Sie ein `ToPSOptionsSpec`-Objekt, indem Sie den Konstruktor aufrufen.
   * Legen Sie Laufzeitoptionen fest, indem Sie dem Datenmember des Objekts `ToPSOptionsSpec` einen Wert zuweisen. Um beispielsweise die erstellte PostScript-Ebene zu definieren, weisen Sie dem `psLevel`-Datenelement des Objekts einen `PSLevel`-Auflistung-Wert zu.`ToPSOptionsSpec`

1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.

   Rufen Sie die `toPS2`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`GeneratePDFServiceService`

   * Ein `BLOB`-Objekt, das das zu konvertierende PDF-Dokument in eine PostScript-Datei darstellt
   * Ein `ToPSOptionsSpec`-Objekt, das Laufzeitoptionen angibt

   Nach Abschluss der Konvertierung extrahieren Sie die Binärdaten, die das PostScript-Dokument darstellen, indem Sie auf die `BLOB`-Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine PostScript-Datei schreiben können.

1. Speichern Sie die PostScript-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort der PS-Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `encryptPDFUsingPassword`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die PostScript-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Zusammenfassung der Schritte](converting-pdf-postscript-image-files.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Konvertieren von PDF-Dokumenten in Bildformate {#converting-pdf-documents-to-image-formats}

Mit dem Convert PDF-Dienst können Sie PDF-Dokumente programmgesteuert in Bildformate konvertieren, darunter JPEG, JPEG 2000, TIFF und PNG. Durch Konvertieren eines PDF-Dokuments in eine Bilddatei können Sie das PDF-Dokument als Bilddatei verwenden. Sie können das Content-Management beispielsweise zur Datenspeicherung in einem Unternehmenssystem ablegen.

Beim Konvertieren eines PDF-Dokuments in ein Bild erstellt der Convert PDF-Dienst für jede Seite im Dokument ein eigenes Bild. Das heißt, wenn das Dokument 20 Seiten umfasst, erstellt der Convert PDF-Dienst 20 Bilddateien. Beim Konvertieren eines PDF-Dokuments in ein Bildformat können Sie Einzelbilder für jede Seite im PDF-Dokument oder eine Bilddatei für das gesamte PDF-Dokument erstellen.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So konvertieren Sie ein PDF-Dokument in einen der unterstützten Typen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Convert PDF-Dienstclient.
1. Rufen Sie das zu konvertierende PDF-Dokument ab.
1. Legen Sie Laufzeitoptionen fest.
1. Konvertieren Sie die PDF-Datei in ein Bild.
1. Rufen Sie die Bilddateien aus einer Sammlung ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Convert PDF-Clients**

Bevor Sie einen Convert PDF-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Convert PDF-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ConvertPdfServiceClient`-Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie ein `ConvertPDFServiceService`-Objekt.

**Zu konvertierendes PDF-Dokument abrufen**

Sie müssen das PDF-Dokument abrufen, um es in ein Bild zu konvertieren. Sie können ein interaktives PDF-Dokument nicht in ein Bild konvertieren. Wenn Sie dies versuchen, wird eine Ausnahme ausgelöst. Um ein interaktives PDF-Dokument in eine Bilddatei zu konvertieren, müssen Sie das PDF-Dokument vor der Konvertierung reduzieren. (Siehe [Reduzieren von PDF-Dokumenten](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents).)

**Festlegen von Laufzeitoptionen**

Sie müssen Laufzeitoptionen wie das Bildformat und die Auflösungswerte festlegen. Informationen zu den Laufzeitwerten finden Sie in der Klassenreferenz `ToImageOptionsSpec` in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**PDF in ein Bild konvertieren**

Nachdem Sie den Dienstclient erstellt und Laufzeitoptionen festgelegt haben, können Sie das PDF-Dokument in ein Bild konvertieren. Ein Sammlungsobjekt, das die Bilder enthält, wird zurückgegeben.

**Abrufen der Bilddateien aus einer Sammlung**

Sie können Bilddateien von einem Sammlungsobjekt abrufen, das der Convert PDF-Dienst zurückgibt. Jedes Element in der Sammlung ist eine `com.adobe.idp.Document`-Instanz (oder eine `BLOB`-Instanz, wenn Sie Webdienste verwenden), die Sie als Bilddatei, z. B. als JPG-Datei, speichern können.

Das Format der Bilddatei hängt von der Laufzeitoption `ImageConvertFormat` ab. Wenn Sie also die Laufzeitoption `ImageConvertFormat` auf `ImageConvertFormat.JPEG` festlegen, können Sie Bilddateien als JPG-Dateien speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-Dienst-API-Beginn konvertieren](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in Bilddateien mit der Java-API {#convert-a-pdf-document-to-image-files-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF-Dienst-API (Java) in ein Bildformat:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-convertpdf-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `ToImageOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Rufen Sie nach Bedarf Methoden auf, die zu diesem Objekt gehören. Legen Sie beispielsweise den Bildtyp fest, indem Sie die `setImageConvertFormat`-Methode aufrufen und einen `ImageConvertFormat`-Enum-Wert übergeben, der den Formattyp angibt.

   >[!NOTE]
   >
   >Das Festlegen des Werts für die Auflistung `ImageConvertFormat` ist obligatorisch.

1. Konvertieren Sie die PDF-Datei in ein Bild.

   Rufen Sie die `toImage2`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`ConvertPdfServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das die zu konvertierende PDF-Datei darstellt.
   * Ein `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec`-Objekt, das die verschiedenen Voreinstellungen zum Bildformat der Zielgruppe enthält.

   Die `toImage2`-Methode gibt ein `java.util.List`-Objekt zurück, das Bilder enthält. Jedes Element in der Sammlung ist eine `com.adobe.idp.Document`-Instanz.

1. Rufen Sie die Bilddateien aus einer Sammlung ab.

   Durchlaufen Sie das `java.util.List`-Objekt, um zu ermitteln, ob Bilder vorhanden sind. Jedes Element ist eine `com.adobe.idp.Document`-Instanz. Speichern Sie das Bild, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `copyToFile` aufrufen und ein `java.io.File`-Objekt übergeben.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Konvertieren eines PDF-Dokuments in JPEG-Dateien mit der Java-API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Konvertieren eines PDF-Dokuments in Bilddateien mithilfe der Webdienst-API {#convert-a-pdf-document-to-image-files-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service API (Webdienst) in ein Bildformat:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF-Client zum Konvertieren.

   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `ConvertPdfServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `ConvertPdfServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern des PDF-Formulars verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Formulars und den Modus zum Öffnen der Datei angibt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Bestimmen Sie die Größe des Byte-Arrays, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `ToImageOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Rufen Sie nach Bedarf Methoden auf, die zu diesem Objekt gehören. Legen Sie beispielsweise den Bildtyp fest, indem Sie die `setImageConvertFormat`-Methode aufrufen und einen `ImageConvertFormat`-Auflistung-Wert übergeben, der den Formattyp angibt.

   >[!NOTE]
   >
   >Das Festlegen des Werts für die Auflistung `ImageConvertFormat` ist obligatorisch.

1. Konvertieren Sie die PDF-Datei in ein Bild.

   Rufen Sie die `toImage2`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`ConvertPDFServiceService`

   * Ein `BLOB`-Objekt, das die zu konvertierende Datei darstellt
   * Ein `ToImageOptionsSpec`-Objekt mit den verschiedenen Voreinstellungen zum Bildformat der Zielgruppe

   Die `toImage2`-Methode gibt ein `MyArrayOfBLOB`-Objekt zurück, das die neu erstellten Bilddateien enthält.

1. Rufen Sie die Bilddateien aus einer Sammlung ab.

   * Bestimmen Sie die Anzahl der Elemente im `MyArrayOfBLOB`-Objekt, indem Sie den Wert des Felds `Count` abrufen. Jedes Element ist ein `BLOB`-Objekt, das das Bild enthält.
   * Durchlaufen Sie das `MyArrayOfBLOB`-Objekt und speichern Sie jede Bilddatei.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
