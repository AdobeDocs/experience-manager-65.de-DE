---
title: Konvertieren von PDF in PostScript- und Bilddateien
description: Verwenden Sie den Convert PDF-Service, um PDF-Dokumente mithilfe der Java-API und der Webservice-API in PostScript und verschiedene Bildformate (JPEG, JPEG 2000, PNG und TIFF) zu konvertieren.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 31730c24-46c3-4111-9391-ccd4342740e9
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '2774'
ht-degree: 100%

---

# Konvertieren von PDF in PostScript- und Grafikdateien {#converting-pdf-to-postscript-andimage-files}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den Convert PDF-Service**

Der Convert PDF-Dienst konvertiert PDF-Dokumente in PostScript sowie verschiedene Bildformate (JPEG, JPEG 2000, PNG und TIFF). Das Konvertieren eines PDF-Dokuments in PostScript ist nützlich für das unbeaufsichtigte, Server-basierte Drucken auf einem beliebigen PostScript-Drucker. Das Konvertieren eines PDF-Dokuments in eine mehrseitige TIFF-Datei ist beim Archivieren von Dokumenten in Content-Management-Systemen praktisch, die PDF-Dokumente nicht unterstützen.

Mithilfe des Convert PDF-Services können Sie die folgenden Aufgaben ausführen:

* Konvertieren von PDF-Dokumenten in PostScript – 
* Konvertieren Sie PDF-Dokumente in Bildformate.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PDF-Dokumenten in PostScript {#converting-pdf-documents-to-postscript}

Hier wird beschrieben, wie Sie mit der Convert PDF-Service-API (Java und Webservice) PDF-Dokumente programmgesteuert in PostScript-Dateien konvertieren können. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss ein nicht interaktives PDF-Dokument sein. Das heißt, wenn Sie versuchen, ein interaktives PDF-Dokument in eine PostScript-Datei zu konvertieren, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument in eine PostScript-Datei zu konvertieren, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Convert PDF-Service-Client.
1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.
1. Legen Sie Laufzeitoptionen für die Konvertierung fest.
1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.
1. Speichern Sie die PostScript-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Convert PDF-Clients**

Bevor Sie einen Vorgang des Convert PDF-Services programmgesteuert ausführen können, müssen Sie einen Convert PDF-Service-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ConvertPdfServiceClient`-Objekt. Wenn Sie die Webservice-API verwenden, erstellen Sie ein `ConvertPDFServiceService`-Objekt.

In diesem Abschnitt werden Webservice-Funktionen verwendet, die in AEM Forms eingeführt wurden. Um auf neue Funktionen zugreifen zu können, müssen Sie Ihr Proxy-Objekt mithilfe des Attributs `lc_version` konstruieren. (Siehe „Zugriff auf neue Funktionen mithilfe von Web-Diensten“ in [Aufrufen von AEM Forms mithilfe von Web-Diensten](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)).

**Referenzieren des PDF-Dokuments zur Konvertierung in eine PostScript-Datei**

Referenzieren Sie das PDF-Dokument, das Sie in eine PostScript-Datei konvertieren möchten. Wie bereits in diesem Thema erwähnt, muss das PDF-Dokument ein nicht interaktives PDF-Dokument sein. Wenn Sie versuchen, ein interaktives PDF-Dokument in eine PostScript-Datei zu konvertieren, wird eine Ausnahme ausgelöst.

**Festlegen der Laufzeitoptionen für die Konvertierung**

Beim Konvertieren eines PDF-Dokuments in eine PostScript-Datei können Sie Laufzeitoptionen definieren, die den erstellten PostScript-Typ angeben. Sie können beispielsweise eine PostScript-Datei der Stufe 3 definieren.

In der Regel spiegelt die erzeugte PostScript-Datei die Größe des PDF-Eingabedokuments wider. Wenn Sie die Option `ShrinkToFit` wählen (wodurch die Ausgabe der PostScript-Datei so verkleinert wird, dass sie auf die Seite passt), werden Sie keinen Unterschied zwischen dem PDF-Eingabedokument und der erzeugten PostScript-Datei feststellen. Die Option `ShrinkToFit` wird nur wirksam, wenn Sie sich dafür entscheiden, auf einer kleineren Seitengröße als der des PDF-Eingabedokuments zu drucken. Um eine kleinere Seitengröße auszuwählen, definieren Sie die Option `PageSize`. Darüber hinaus wird empfohlen, die Option `RotateAndCenter` auf `true` zu setzen, um eine korrekte PostScript-Ausgabe zu erhalten.

Ebenso wird die Option `ExpandToFit` (wodurch die Ausgabe der PostScript-Datei so vergrößert wird, dass sie auf die Seite passt) nur wirksam, wenn Sie zum Drucken ein größeres Seitenformat als das des PDF-Eingabedokuments wählen. Um eine größere Seitengröße auszuwählen, definieren Sie die Option `PageSize`. Darüber hinaus wird empfohlen, die Option `RotateAndCenter` auf `true` zu setzen, um eine korrekte PostScript-Ausgabe zu erhalten.

>[!NOTE]
>
>Informationen zu den Laufzeitwerten, die Sie festlegen können, finden Sie in der `ToPSOptionsSpec`-Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Konvertieren des PDF-Dokuments in eine PostScript-Datei**

Nachdem Sie den Service-Client erstellt und Laufzeitoptionen festgelegt haben, können Sie den PostScript-Konvertierungsvorgang aufrufen. Dieser Vorgang benötigt Informationen über das zu konvertierende Dokument, einschließlich der bevorzugten PostScript-Ebene für das Zieldokument.

**Speichern der PostScript-Datei**

Nachdem Sie das PDF-Dokument in PostScript konvertiert haben, können Sie die Ausgabe als PostScript-Datei speichern.

**Siehe auch**

[Konvertieren eines PDF-Dokuments in PS mithilfe der Java-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Konvertieren eines PDF-Dokuments in PS mithilfe der Webservice-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitungen zur Convert PDF-Service-API](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in PS mithilfe der Java-API {#convert-a-pdf-document-to-ps-using-the-java-api}

So konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF-Service-API (Java) in PostScript:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-convertpdf-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des zu konvertierenden PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument speichert, indem Sie den `com.adobe.idp.Document`-Konstruktor verwenden. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen für die Konvertierung fest.

   * Erstellen Sie ein `ToPSOptionsSpec`-Objekt, indem Sie seinen Konstruktor aufrufen.
   * Legen Sie Laufzeitoptionen fest, indem Sie eine entsprechende Methode aufrufen, die zu dem `ToPSOptionsSpec`-Objekt gehört. Um beispielsweise die zu erstellende PostScript-Ebene zu definieren, rufen Sie die Methode `setPsLevel` des `ToPSOptionsSpec`-Objekts auf und übergeben einen `PSLevel`-Auflistungswert, der die PostScript-Ebene angibt. Informationen zu allen Laufzeitwerten, die Sie festlegen können, finden Sie in der `ToPSOptionsSpec`-Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.

   Rufen Sie die Methode `toPS2` des `ConvertPdfServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument darstellt, welches in eine PostScript-Datei konvertiert werden soll.
   * Ein `ToPSOptionsSpec`-Objekt, das PostScript-Laufzeitoptionen angibt.

   Die Methode `toPS2` gibt ein `Document`-Objekt zurück, das das neue PostScript-Dokument enthält.

1. Speichern Sie die PostScript-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .ps lautet.
   * Rufen Sie die Methode `copyToFile` des `Document`-Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der Methode `toPS2` zurückgegeben wird).

**Siehe auch**

[Zusammenfassung der Schritte](converting-pdf-postscript-image-files.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren eines PDF-Dokuments in PostScript mithilfe der Java-API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren eines PDF-Dokuments in PS mithilfe der Webservice-API {#convert-a-pdf-document-to-ps-using-the-web-service-api}

So konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF-Service-API (Webservice) in PostScript:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `ConvertPdfServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `ConvertPdfServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das in eine PostScript-Datei konvertiert wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu konvertierenden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die Länge des zu lesenden Streams übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen für die Konvertierung fest.

   * Erstellen Sie ein `ToPSOptionsSpec`-Objekt, indem Sie seinen Konstruktor aufrufen.
   * Legen Sie Laufzeitoptionen fest, indem Sie dem Datenelement des `ToPSOptionsSpec`-Objekts einen Wert zuweisen. Um beispielsweise die zu erstellende PostScript-Ebene zu definieren, weisen Sie dem Datenelement `psLevel` des `ToPSOptionsSpec`-Objekts einen `PSLevel`-Auflistungswert zu.

1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.

   Rufen Sie die Methode `toPS2` des `GeneratePDFServiceService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das PDF-Dokument darstellt, welches in eine PostScript-Datei konvertiert werden soll
   * Ein `ToPSOptionsSpec`-Objekt, das Laufzeitoptionen angibt

   Extrahieren Sie nach Abschluss der Konvertierung die Binärdaten, die das PostScript-Dokument darstellen, indem Sie auf die Eigenschaft `MTOM` des `BLOB`-Objekts zugreifen. Dadurch wird ein Byte-Array zurückgegeben, das Sie in eine PostScript-Datei schreiben können.

1. Speichern Sie die PostScript-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort der PS-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `encryptPDFUsingPassword` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die PostScript-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-pdf-postscript-image-files.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Konvertieren von PDF-Dokumenten in Bildformate {#converting-pdf-documents-to-image-formats}

Sie können den Convert PDF-Service verwenden, um PDF-Dokumente programmgesteuert in Bildformate zu konvertieren, darunter JPEG, JPEG 2000, TIFF und PNG. Durch Konvertieren eines PDF-Dokuments in eine Grafikdatei können Sie das PDF-Dokument als Grafikdatei verwenden. Sie können das Bild beispielsweise in einem Enterprise Content Management-System zur Speicherung platzieren.

Beim Konvertieren eines PDF-Dokuments in ein Bild erstellt der Convert PDF-Service für jede-Seite im Dokument ein eigenes Bild. Das heißt, wenn das Dokument 20 Seiten umfasst, erstellt der Convert PDF-Service 20 Grafikdateien. Beim Konvertieren eines PDF-Dokuments in ein Bildformat können Sie für jede Seite innerhalb des PDF-Dokuments Einzelbilder erstellen oder für das gesamte PDF-Dokument eine Grafikdatei erstellen.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Schritte aus, um ein PDF-Dokument in einen der unterstützten Typen zu konvertieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Convert PDF-Service-Client.
1. Rufen Sie das zu konvertierende PDF-Dokument ab.
1. Legen Sie Laufzeitoptionen fest.
1. Konvertieren Sie die PDF in ein Bild.
1. Rufen Sie die Grafikdateien aus einer Sammlung ab.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Convert PDF-Clients**

Bevor Sie einen Vorgang des Convert PDF-Services programmgesteuert ausführen können, müssen Sie einen Convert PDF-Service-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `ConvertPdfServiceClient`-Objekt. Wenn Sie die Webservice-API verwenden, erstellen Sie ein `ConvertPDFServiceService`-Objekt.

**Abrufen des zu konvertierenden PDF-Dokuments**

Rufen Sie das PDF-Dokument ab, um es in ein Bild konvertieren zu können. Sie können ein interaktives PDF-Dokument nicht in ein Bild konvertieren. Wenn Sie dies versuchen, wird eine Ausnahme ausgelöst. Um ein interaktives PDF-Dokument in eine Grafikdatei zu konvertieren, müssen Sie das PDF-Dokument vor dem Konvertieren reduzieren. (Siehe [Reduzieren von PDF-Dokumenten](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents).)

**Festlegen von Laufzeitoptionen**

Legen Sie Laufzeitoptionen fest, z. B. das Bildformat und die Auflösungswerte. Informationen zu den Laufzeitwerten finden Sie in der `ToImageOptionsSpec`-Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Konvertieren der PDF in ein Bild**

Nachdem Sie den Service-Client erstellt und Laufzeitoptionen festgelegt haben, können Sie das PDF-Dokument in ein Bild konvertieren. Ein Sammlungsobjekt, das die Bilder enthält, wird zurückgegeben.

**Abrufen der Grafikdateien aus einer Sammlung**

Sie können Grafikdateien von einem Sammlungsobjekt abrufen, das der Convert PDF-Service zurückgibt. Jedes Element in der Sammlung ist eine `com.adobe.idp.Document`-Instanz (oder eine `BLOB`-Instanz, wenn Sie Web-Services verwenden), die Sie als Grafikdatei speichern können, z. B. als JPG-Datei.

Das Format der Grafikdatei hängt von der Laufzeitoption `ImageConvertFormat` ab. Das heißt, wenn Sie die Laufzeitoption `ImageConvertFormat` auf `ImageConvertFormat.JPEG` setzen, können Sie Grafikdateien als JPG-Dateien speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitungen zur Convert PDF-Service-API](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in Grafikdateien mithilfe der Java-API {#convert-a-pdf-document-to-image-files-using-the-java-api}

So konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF-Service API (Java) in ein Bildformat:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-convertpdf-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `ToImageOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Rufen Sie nach Bedarf Methoden auf, die zu diesem Objekt gehören. Legen Sie zum Beispiel den Bildtyp fest, indem Sie die Methode `setImageConvertFormat` aufrufen und einen Aufzählungswert `ImageConvertFormat` übergeben, der den Formattyp festlegt.

   >[!NOTE]
   >
   >Das Angeben des `ImageConvertFormat`-Auflistungswertes ist obligatorisch.

1. Konvertieren Sie die PDF in ein Bild.

   Rufen Sie die Methode `toImage2` des `ConvertPdfServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das die zu konvertierende PDF-Datei darstellt.
   * Ein `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec`-Objekt, das die verschiedenen Voreinstellungen zum Zielbildformat enthält.

   Die Methode `toImage2` gibt ein `java.util.List`-Objekt zurück, das Bilder enthält. Jedes Element in der Sammlung ist eine `com.adobe.idp.Document`-Instanz.

1. Rufen Sie die Grafikdateien aus einer Sammlung ab.

   Iterieren Sie durch das `java.util.List`-Objekt, um festzustellen, ob Bilder vorhanden sind. Jedes Element ist eine `com.adobe.idp.Document`-Instanz. Speichern Sie das Bild, indem Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts aufrufen und ein `java.io.File`-Objekt übergeben.

**Siehe auch**

[Schnellstart (SOAP-Modus): Konvertieren eines PDF-Dokuments in JPEG-Dateien mithilfe der Java-API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Konvertieren eines PDF-Dokuments in Grafikdateien mithilfe der Webservice-API {#convert-a-pdf-document-to-image-files-using-the-web-service-api}

So konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF-Service API (Webservice) in ein Bildformat:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Convert PDF-Client.

   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `ConvertPdfServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `ConvertPdfServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `ConvertPdfServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern des PDF-Formulars verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Formulars und den Modus zum Öffnen der Datei angibt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Ermitteln Sie die Größe des Byte-Arrays, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen Feld `MTOM` mit dem Inhalt des Byte-Arrays belegen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `ToImageOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Rufen Sie nach Bedarf Methoden auf, die zu diesem Objekt gehören. Legen Sie zum Beispiel den Bildtyp fest, indem Sie die Methode `setImageConvertFormat` aufrufen und einen `ImageConvertFormat`-Auflistungswert übergeben, der den Formattyp angibt.

   >[!NOTE]
   >
   >Das Angeben des `ImageConvertFormat`-Auflistungswertes ist obligatorisch.

1. Konvertieren Sie die PDF in ein Bild.

   Rufen Sie die Methode `toImage2` des `ConvertPDFServiceService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das die zu konvertierende Datei darstellt
   * Ein `ToImageOptionsSpec`-Objekt, das die verschiedenen Voreinstellungen zum Zielbildformat enthält

   Die Methode `toImage2` gibt ein `MyArrayOfBLOB`-Objekt zurück, das die neu erstellten Grafikdateien enthält.

1. Rufen Sie die Grafikdateien aus einer Sammlung ab.

   * Ermitteln Sie die Anzahl der Elemente im `MyArrayOfBLOB`-Objekt, indem Sie den Wert des Feldes `Count` abrufen. Jedes Element ist ein `BLOB`-Objekt, das das Bild enthält.
   * Iterieren Sie durch das `MyArrayOfBLOB`-Objekt und speichern Sie jede Grafikdatei.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
