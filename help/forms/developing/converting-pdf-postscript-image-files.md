---
title: Konvertieren von PDF-Dateien in PostScript- und Bilddateien
seo-title: Konvertieren von PDF-Dateien in PostScript- und Bilddateien
description: Verwenden Sie den Dienst "Convert PDF", um PDF-Dokumente mithilfe der Java-API und der Web Service-API in PostScript und eine Reihe von Bildformaten (JPEG, JPEG 2000, PNG und TIFF) zu konvertieren.
seo-description: Verwenden Sie den Dienst "Convert PDF", um PDF-Dokumente mithilfe der Java-API und der Web Service-API in PostScript und eine Reihe von Bildformaten (JPEG, JPEG 2000, PNG und TIFF) zu konvertieren.
uuid: 07da0391-7180-4197-aaa6-ae753d753b84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: f8707752-2c83-461a-b83d-708754b0f3f6
role: Developer
exl-id: 31730c24-46c3-4111-9391-ccd4342740e9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2846'
ht-degree: 5%

---

# Konvertieren von PDF- in PostScript- und Bilddateien {#converting-pdf-to-postscript-andimage-files}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

**Über den Convert PDF-Dienst**

Der Convert PDF-Dienst konvertiert PDF-Dokumente in PostScript und eine Reihe von Bildformaten (JPEG, JPEG 2000, PNG und TIFF). Das Konvertieren eines PDF-Dokuments in PostScript ist nützlich für die unbeaufsichtigte serverbasierte Druckausgabe auf PostScript-Druckern. Das Konvertieren eines PDF-Dokuments in eine mehrseitige TIFF-Datei ist beim Archivieren von Dokumenten in Content Management-Systemen praktisch, die PDF-Dokumente nicht unterstützen.

Sie können diese Aufgaben mit dem Convert PDF-Dienst ausführen:

* Konvertieren von PDF-Dokumenten in PostScript – 
* Konvertieren von PDF-Dokumenten in Bildformate.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PDF-Dokumenten in PostScript {#converting-pdf-documents-to-postscript}

Hier wird beschrieben, wie Sie mit der Convert PDF Service API (Java- und Webdienst) PDF-Dokumente programmgesteuert in PostScript-Dateien konvertieren können. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss ein nicht interaktives PDF-Dokument sein. Wenn Sie also versuchen, ein interaktives PDF-Dokument in eine PostScript-Datei zu konvertieren, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um ein PDF-Dokument in eine PostScript-Datei zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Convert PDF-Dienst-Client.
1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.
1. Festlegen von Konversions-Laufzeitoptionen.
1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.
1. Speichern Sie die PostScript-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Convert PDF-Clients**

Bevor Sie einen Convert PDF-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Convert PDF-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ConvertPdfServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie ein `ConvertPDFServiceService` -Objekt.

In diesem Abschnitt werden Webdienstfunktionen verwendet, die in AEM Forms eingeführt wurden. Um auf neue Funktionen zugreifen zu können, müssen Sie Ihr Proxy-Objekt mithilfe des Attributs `lc_version` erstellen. (Siehe &quot;Zugriff auf neue Funktionen mithilfe von Webdiensten&quot;in [Aufrufen von AEM Forms mithilfe von Webdiensten](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

**Referenzieren des zu konvertierenden PDF-Dokuments in eine PostScript-Datei**

Referenzieren Sie das PDF-Dokument, das Sie in eine PostScript-Datei konvertieren möchten. Wie bereits zuvor in diesem Thema erwähnt, muss das PDF-Dokument ein nicht interaktives PDF-Dokument sein. Wenn Sie versuchen, ein interaktives PDF-Dokument in eine PostScript-Datei zu konvertieren, wird eine Ausnahme ausgelöst.

**Laufzeitoptionen für Konversionen festlegen**

Beim Konvertieren eines PDF-Dokuments in eine PostScript-Datei können Sie Laufzeitoptionen definieren, die den erstellten PostScript-Typ angeben. Sie können beispielsweise eine PostScript-Datei der Stufe 3 definieren.

In der Regel spiegelt die generierte PostScript-Datei die Größe des PDF-Eingabedokuments wider. Wenn Sie die Option `ShrinkToFit` auswählen (wodurch die Ausgabe der PostScript-Datei an die Seite angepasst wird), wird kein Unterschied zwischen dem PDF-Eingabedokument und der generierten PostScript-Datei angezeigt. Die Option `ShrinkToFit` wird nur wirksam, wenn Sie für den Druck eine kleinere Seitengröße als das PDF-Eingabedokument wählen. Um eine kleinere Seitengröße auszuwählen, definieren Sie die Option `PageSize` . Außerdem wird empfohlen, die `RotateAndCenter`-Option auf `true` festzulegen, um die richtige PostScript-Ausgabe zu erhalten.

Wenn Sie die Option `ExpandToFit` auswählen (wodurch die Ausgabe der PostScript-Datei an die Seite angepasst wird), wird sie nur wirksam, wenn Sie auf eine größere Seitengröße als das PDF-Eingabedokument klicken. Um eine größere Seitengröße auszuwählen, definieren Sie die Option `PageSize` . Außerdem wird empfohlen, die `RotateAndCenter`-Option auf `true` festzulegen, um die richtige PostScript-Ausgabe zu erhalten.

>[!NOTE]
>
>Informationen zu den Laufzeitwerten, die Sie festlegen können, finden Sie in der `ToPSOptionsSpec`-Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Konvertieren des PDF-Dokuments in eine PostScript-Datei**

Nachdem Sie den Service-Client erstellt und Laufzeitoptionen festgelegt haben, können Sie den PostScript-Konvertierungsvorgang aufrufen. Dieser Vorgang benötigt Informationen zum zu konvertierenden Dokument, einschließlich der bevorzugten PostScript-Ebene für das Zieldokument.

**PostScript-Datei speichern**

Nachdem Sie das PDF-Dokument in PostScript konvertiert haben, können Sie die Ausgabe als PostScript-Datei speichern.

**Siehe auch**

[Konvertieren eines PDF-Dokuments in PS mithilfe der Java-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Konvertieren eines PDF-Dokuments in PS mithilfe der Webdienst-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF Service API-Schnellstarts konvertieren](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in PS mithilfe der Java-API {#convert-a-pdf-document-to-ps-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service API (Java) in PostScript:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-convertpdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt mithilfe des zugehörigen Konstruktors und übergeben Sie einen string -Wert, der den Speicherort des zu konvertierenden PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument mithilfe des Konstruktors `com.adobe.idp.Document` speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.

1. Festlegen von Konversions-Laufzeitoptionen.

   * Erstellen Sie ein `ToPSOptionsSpec` -Objekt, indem Sie seinen Konstruktor aufrufen.
   * Legen Sie Laufzeitoptionen fest, indem Sie eine geeignete Methode aufrufen, die zum `ToPSOptionsSpec` -Objekt gehört. Um beispielsweise die erstellte PostScript-Ebene zu definieren, rufen Sie die `setPsLevel` -Methode des Objekts `ToPSOptionsSpec` auf und übergeben Sie einen `PSLevel` -Auflistungswert, der die PostScript-Ebene angibt. Informationen zu allen Laufzeitwerten, die Sie festlegen können, finden Sie in der `ToPSOptionsSpec`-Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.

   Rufen Sie die `toPS2`Methode des Objekts `ConvertPdfServiceClient`auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das PDF-Dokument darstellt, das in eine PostScript-Datei konvertiert werden soll.
   * Ein `ToPSOptionsSpec` -Objekt, das PostScript-Laufzeitoptionen angibt.

   Die `toPS2`-Methode gibt ein `Document`-Objekt zurück, das das neue PostScript-Dokument enthält.

1. Speichern Sie die PostScript-Datei.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .ps lautet.
   * Rufen Sie die `copyToFile` -Methode des `Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `toPS2` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](converting-pdf-postscript-image-files.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren eines PDF-Dokuments in PostScript mithilfe der Java-API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren eines PDF-Dokuments in PS mithilfe der Webdienst-API {#convert-a-pdf-document-to-ps-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service-API (Webdienst) in PostScript:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ConvertPdfServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `ConvertPdfServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `ConvertPdfServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das in eine PostScript-Datei konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu konvertierenden PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die Stream-Länge zum Lesen übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Konversions-Laufzeitoptionen.

   * Erstellen Sie ein `ToPSOptionsSpec` -Objekt, indem Sie seinen Konstruktor aufrufen.
   * Legen Sie Laufzeitoptionen fest, indem Sie dem Datenelement des Objekts `ToPSOptionsSpec` einen Wert zuweisen. Um beispielsweise die erstellte PostScript-Ebene zu definieren, weisen Sie dem `psLevel`-Datenelement des `ToPSOptionsSpec`-Objekts einen Auflistungswert `PSLevel` zu.

1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.

   Rufen Sie die `toPS2` -Methode des Objekts `GeneratePDFServiceService` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das PDF-Dokument darstellt, das in eine PostScript-Datei konvertiert werden soll
   * Ein `ToPSOptionsSpec` -Objekt, das Laufzeitoptionen angibt

   Extrahieren Sie nach Abschluss der Konvertierung die Binärdaten, die das PostScript-Dokument darstellen, indem Sie auf die `BLOB` -Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Byte-Array zurückgegeben, das Sie in eine PostScript-Datei schreiben können.

1. Speichern Sie die PostScript-Datei.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort der PS-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `encryptPDFUsingPassword` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die PostScript-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-pdf-postscript-image-files.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Konvertieren von PDF-Dokumenten in Bildformate {#converting-pdf-documents-to-image-formats}

Mit dem Convert PDF-Dienst können Sie PDF-Dokumente programmgesteuert in Bildformate konvertieren, darunter JPEG, JPEG 2000, TIFF und PNG. Durch Konvertieren eines PDF-Dokuments in eine Bilddatei können Sie das PDF-Dokument als Bilddatei verwenden. Sie können das Bild beispielsweise in einem Enterprise Content Management-System zur Speicherung platzieren.

Beim Konvertieren eines PDF-Dokuments in ein Bild erstellt der Convert PDF-Dienst für jede Seite im Dokument ein eigenes Bild. Das heißt, wenn das Dokument 20 Seiten umfasst, erstellt der Convert PDF-Dienst 20 Bilddateien. Beim Konvertieren eines PDF-Dokuments in ein Bildformat können Sie einzelne Bilder für jede Seite im PDF-Dokument oder eine einzelne Bilddatei für das gesamte PDF-Dokument erstellen.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Schritte aus, um ein PDF-Dokument in einen der unterstützten Typen zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Convert PDF-Dienst-Client.
1. Rufen Sie das zu konvertierende PDF-Dokument ab.
1. Legen Sie Laufzeitoptionen fest.
1. Konvertieren Sie die PDF-Datei in ein Bild.
1. Rufen Sie die Bilddateien aus einer Sammlung ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Convert PDF-Clients**

Bevor Sie einen Convert PDF-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Convert PDF-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ConvertPdfServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie ein `ConvertPDFServiceService` -Objekt.

**Abrufen des zu konvertierenden PDF-Dokuments**

Sie müssen das PDF-Dokument abrufen, um es in ein Bild zu konvertieren. Sie können ein interaktives PDF-Dokument nicht in ein Bild konvertieren. Wenn Sie dies versuchen, wird eine Ausnahme ausgelöst. Um ein interaktives PDF-Dokument in eine Bilddatei zu konvertieren, müssen Sie das PDF-Dokument vor dem Konvertieren reduzieren. (Siehe [Reduzieren von PDF-Dokumenten](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents).)

**Laufzeitoptionen festlegen**

Sie müssen Laufzeitoptionen festlegen, z. B. das Bildformat und die Auflösungswerte. Informationen zu den Laufzeitwerten finden Sie in der `ToImageOptionsSpec`-Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Konvertieren der PDF-Datei in ein Bild**

Nachdem Sie den Service-Client erstellt und Laufzeitoptionen festgelegt haben, können Sie das PDF-Dokument in ein Bild konvertieren. Ein Sammlungsobjekt, das die Bilder enthält, wird zurückgegeben.

**Abrufen der Bilddateien aus einer Sammlung**

Sie können Bilddateien von einem Sammlungsobjekt abrufen, das der Convert PDF-Dienst zurückgibt. Jedes Element in der Sammlung ist eine `com.adobe.idp.Document`-Instanz (oder eine `BLOB`-Instanz, wenn Sie Webdienste verwenden), die Sie als Bilddatei speichern können, z. B. als JPG-Datei.

Das Format der Bilddatei hängt von der Laufzeitoption `ImageConvertFormat` ab. Wenn Sie also die Laufzeitoption `ImageConvertFormat` auf `ImageConvertFormat.JPEG` festlegen, können Sie Bilddateien als JPG-Dateien speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF Service API-Schnellstarts konvertieren](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in Bilddateien mithilfe der Java-API {#convert-a-pdf-document-to-image-files-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF-Dienst-API (Java) in ein Bildformat:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-convertpdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das zu konvertierende PDF-Dokument mithilfe des zugehörigen Konstruktors darstellt und einen string -Wert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `ToImageOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Rufen Sie nach Bedarf Methoden auf, die zu diesem Objekt gehören. Legen Sie beispielsweise den Bildtyp fest, indem Sie die Methode `setImageConvertFormat` aufrufen und einen Enum-Wert `ImageConvertFormat` übergeben, der den Formattyp angibt.

   >[!NOTE]
   >
   >Das Festlegen des Auflistungswerts `ImageConvertFormat` ist obligatorisch.

1. Konvertieren Sie die PDF-Datei in ein Bild.

   Rufen Sie die `toImage2` -Methode des Objekts `ConvertPdfServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das die zu konvertierende PDF-Datei darstellt.
   * Ein `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec` -Objekt, das die verschiedenen Voreinstellungen zum Zielbildformat enthält.

   Die `toImage2`-Methode gibt ein `java.util.List`-Objekt zurück, das Bilder enthält. Jedes Element in der Sammlung ist eine `com.adobe.idp.Document`-Instanz.

1. Rufen Sie die Bilddateien aus einer Sammlung ab.

   Iterieren Sie durch das `java.util.List`-Objekt, um festzustellen, ob Bilder vorhanden sind. Jedes Element ist eine `com.adobe.idp.Document`-Instanz. Speichern Sie das Bild, indem Sie die `copyToFile`-Methode des `com.adobe.idp.Document`-Objekts aufrufen und ein `java.io.File`-Objekt übergeben.

**Siehe auch**

[Schnellstart (SOAP-Modus): Konvertieren eines PDF-Dokuments in JPEG-Dateien mithilfe der Java-API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Konvertieren eines PDF-Dokuments in Bilddateien mithilfe der Webdienst-API {#convert-a-pdf-document-to-image-files-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service-API (Webdienst) in ein Bildformat:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen konvertierten PDF-Client.

   * Erstellen Sie ein `ConvertPdfServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `ConvertPdfServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `ConvertPdfServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern des PDF-Formulars verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars und den Modus zum Öffnen der Datei angibt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Bestimmen Sie die Größe des Byte-Arrays, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `ToImageOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Rufen Sie nach Bedarf Methoden auf, die zu diesem Objekt gehören. Legen Sie beispielsweise den Bildtyp fest, indem Sie die Methode `setImageConvertFormat` aufrufen und einen Auflistungswert `ImageConvertFormat` übergeben, der den Formattyp angibt.

   >[!NOTE]
   >
   >Das Festlegen des Auflistungswerts `ImageConvertFormat` ist obligatorisch.

1. Konvertieren Sie die PDF-Datei in ein Bild.

   Rufen Sie die `toImage2` -Methode des Objekts `ConvertPDFServiceService` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das die zu konvertierende Datei darstellt
   * Ein `ToImageOptionsSpec` -Objekt, das die verschiedenen Voreinstellungen zum Zielbildformat enthält

   Die `toImage2`-Methode gibt ein `MyArrayOfBLOB`-Objekt zurück, das die neu erstellten Bilddateien enthält.

1. Rufen Sie die Bilddateien aus einer Sammlung ab.

   * Bestimmen Sie die Anzahl der Elemente im `MyArrayOfBLOB`-Objekt, indem Sie den Wert des Felds `Count` abrufen. Jedes Element ist ein `BLOB` -Objekt, das das Bild enthält.
   * Iterieren Sie durch das `MyArrayOfBLOB`-Objekt und speichern Sie jede Bilddatei.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
