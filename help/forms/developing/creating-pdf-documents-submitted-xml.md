---
title: Erstellen von PDF-Dokumenten mit SubmittedXML-Daten
description: Verwenden Sie den Forms-Service, um die Formulardaten abzurufen, die der Benutzer in ein interaktives Formular eingegeben hat. Übergeben Sie die Formulardaten an einen anderen Service-Vorgang von AEM Forms und erstellen Sie mithilfe der Daten ein PDF-Dokument.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: d9d5b94a-9d10-4d90-9e10-5142f30ba4a3
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 100%

---

# Erstellen von PDF-Dokumenten mit gesendeten XML-Daten {#creating-pdf-documents-with-submittedxml-data}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Erstellen von PDF-Dokumenten mit gesendeten XML-Daten {#creating-pdf-documents-with-submitted-xml-data}

Web-basierte Programme, die es Benutzern ermöglichen, interaktive Formulare auszufüllen, erfordern, dass die Daten an den Server zurückgesendet werden. Mithilfe des Forms-Services können Sie die Formulardaten abrufen, die der Benutzer in ein interaktives Formular eingegeben hat. Anschließend können Sie die Formulardaten an einen anderen Service-Vorgang von AEM Forms übergeben und mithilfe der Daten ein PDF-Dokument erstellen.

>[!NOTE]
>
>Bevor Sie diesen Inhalt lesen, sollten Sie über fundierte Kenntnisse im Umgang mit gesendeten Formularen verfügen. Konzepte wie die Beziehung zwischen einem Formularentwurf und den übermittelten XML-Daten werden in „Umgang mit übermittelten Formularen“ behandelt.

Betrachten Sie den folgenden Workflow, der drei AEM Forms-Services umfasst:

* Ein Benutzer sendet XML-Daten von einem Web-basierten Programm an den Forms-Service.
* Der Forms-Service wird verwendet, um das gesendete Formular zu verarbeiten und Formularfelder zu extrahieren. Formulardaten können verarbeitet werden. Beispielsweise können die Daten an eine Unternehmensdatenbank gesendet werden.
* Formulardaten werden an den Ausgabe-Service gesendet, um ein nicht interaktives PDF-Dokument zu erstellen.
* Das nicht interaktive PDF-Dokument wird in Content Services (veraltet) gespeichert.

Das folgende Diagramm zeigt eine visuelle Darstellung dieses Workflows.

![cd_cd_finsrv_architecture_xml_pdf1](assets/cd_cd_finsrv_architecture_xml_pdf1.png)

Nachdem der Benutzer das Formular über den Client-Webbrowser gesendet hat, wird das nicht interaktive PDF-Dokument in Content Services (veraltet) gespeichert. Die folgende Abbildung zeigt ein in Content Services gespeichertes PDF-Dokument (veraltet).

![cd_cd_cs_gui](assets/cd_cd_cs_gui.png)

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein nicht interaktives PDF-Dokument mit gesendeten XML-Daten zu erstellen und im PDF-Dokument in Content Services (veraltet) zu speichern, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie Forms-, Ausgabe- und Document Management-Objekte.
1. Rufen Sie Formulardaten mithilfe des Forms-Services ab.
1. Erstellen Sie mithilfe des Ausgabe-Services ein nicht interaktives PDF-Dokument.
1. Speichern Sie das PDF-Formular mithilfe des Document Management-Services in Content Services (veraltet).

**Projektdateien einbeziehen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen von Forms-, Ausgabe- und Document Management-Objekten**

Bevor Sie einen Forms-Service-API-Vorgang programmgesteuert durchführen können, erstellen Sie ein Forms-Client-API-Objekt. Da dieser Workflow die Ausgabe- und Document Management-Services aufruft, erstellen Sie sowohl ein Client-API-Objekt für die Ausgabe als auch ein Client-API-Objekt für das Document Management.

**Abrufen von Formulardaten mithilfe des Forms-Services**

Rufen Sie Formulardaten ab, die an den Forms-Service gesendet wurden. Sie können gesendete Daten entsprechend Ihren Geschäftsanforderungen verarbeiten. Beispielsweise können Sie Formulardaten in einer Unternehmensdatenbank speichern. Um jedoch ein nicht interaktives PDF-Dokument zu erstellen, werden die Formulardaten an den Ausgabe-Service übergeben.

**Erstellen Sie ein nicht interaktives PDF-Dokument mithilfe des Ausgabe-Services.**

Verwenden Sie den Ausgabe-Service, um ein nicht interaktives PDF-Dokument zu erstellen, das auf einem Formularentwurf und XML-Formulardaten basiert. Im Workflow werden die Formulardaten vom Forms-Service abgerufen.

**Speichern des PDF-Formulars in Content Services (veraltet) mithilfe des Document Management-Services**

Verwenden Sie die Document Management-Service-API zum Speichern eines PDF-Dokuments in Content Services (veraltet).

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

### Erstellen eines PDF-Dokuments mit gesendeten XML-Daten mithilfe der Java-API {#create-a-pdf-document-with-submitted-xml-data-using-the-java-api}

So erstellen Sie mithilfe der Forms-, Ausgabe- und Document Management-API (Java) ein PDF-Dokument mit den gesendeten XML-Daten:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“, „adobe-output-client.jar“ und „adobe-contentservices-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen von Forms-, Ausgabe- und Document Management-Objekten

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen von Formulardaten mithilfe des Forms-Services

   * Rufen Sie die Methode `processFormSubmission` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

      * Das `com.adobe.idp.Document`-Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der Umgebungsvariablen angibt, einschließlich aller relevanten HTTP-Kopfzeilen. Geben Sie den zu verarbeitenden Inhaltstyp an, indem Sie einen oder mehrere Werte für die Umgebungsvariable `CONTENT_TYPE` angeben. Um beispielsweise XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`.
      * Ein Zeichenfolgenwert, der den Wert der `HTTP_USER_AGENT`-Kopfzeile angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen speichert.

     Die `processFormSubmission`-Methode gibt ein `FormsResult`-Objekt aus, das die Ergebnisse der Formularübermittlung enthält.

   * Stellen Sie fest, ob der Forms-Dienst die Verarbeitung der Formulardaten abgeschlossen hat, indem Sie die `getAction`-Methode des `FormsResult`-Objekts aufrufen. Wenn diese Methode den Wert `0` zurückgibt, können die Daten verarbeitet werden.
   * Abrufen von Formulardaten durch Erstellen eines `com.adobe.idp.Document`-Objekts durch Aufrufen der `getOutputContent`-Methode des `FormsResult`-Objekts. (Dieses Objekt enthält Formulardaten, die an den Output-Dienst gesendet werden können.)
   * Erstellen Sie ein `java.io.InputStream`-Objekt durch Aufrufen des `java.io.DataInputStream`-Konstruktor und Übergabe des `com.adobe.idp.Document`-Objekts.
   * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory`-Objekt, indem Sie die `newInstance`-Methode des statischen `org.w3c.dom.DocumentBuilderFactory`-Objekts aufrufen.
   * Erstellen Sie ein `org.w3c.dom.DocumentBuilder`-Objekt, indem Sie die `newDocumentBuilder`-Methode des `org.w3c.dom.DocumentBuilderFactory`-Objekts aufrufen.
   * Erstellen Sie ein `org.w3c.dom.Document`-Objekt, indem Sie die `parse`-Methode des `org.w3c.dom.DocumentBuilder`-Objekts aufrufen und das `java.io.InputStream`-Objekt übergeben.
   * Rufen Sie den Wert jedes Knotens im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document`-Objekt und den Namen des Knotens, dessen Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgewert aus, der den Wert des Knotens darstellt. Im folgenden Code-Beispiel wird diese benutzerdefinierte Methode `getNodeText` genannt. Der Hauptteil dieser Methode wird angezeigt.

1. Erstellen Sie ein nicht interaktives PDF-Dokument mit dem Output-Dienst.

   Erstellen Sie ein PDF-Dokument, indem Sie die Methode `generatePDFOutput` des Objekts `OutputClient` aufrufen und die folgenden Werte weitergeben:

   * Ein `TransformationFormat` Aufzählungs-Wert. Um ein PDF-Dokument zu generieren, legen Sie `TransformationFormat.PDF` fest.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt. Stellen Sie sicher, dass der Formularentwurf mit den vom Forms-Dienst abgerufenen Formulardaten kompatibel ist.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen. Stellen Sie sicher, dass dieses Objekt von der Methode `getOutputContent` des Objekts `FormsResult` zurückgegeben wurde.
   * Die `generatePDFOutput`-Methode gibt ein Objekt `OutputResult` zurück, das das Ergebnis der Authentifizierung enthält.
   * Rufen Sie das nicht interaktive PDF-Dokument ab, indem Sie die Methode `getGeneratedDoc` des Objekts `OutputResult` aufrufen. Diese Methode gibt eine `com.adobe.idp.Document`-Instanz zurück, die das nicht interaktive PDF-Dokument darstellt.

1. Speichern Sie das PDF-Formular in Content Services (nicht mehr unterstützt) mithilfe des Document Management-Dienstes.

   Fügen Sie den Inhalt hinzu, indem Sie die Methode `storeContent` des Objekts `DocumentManagementServiceClientImpl` verwenden und die folgenden Werte übergeben:

   * Ein Zeichenfolgewert, der den Speicher angibt, dem der Inhalt hinzugefügt wird. Der Standardspeicherort ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolge-Wert, der den vollständig qualifizierten Pfad des Bereichs angibt, in dem der Inhalt hinzugefügt wird (z. B. `/Company Home/Test Directory`). Dieser Wert ist ein obligatorischer Parameter.
   * Der Knotenname, der den neuen Inhalt darstellt (z. B. `MortgageForm.pdf`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolge-Wert, der den Knotentyp angibt. Um neuen Inhalt hinzuzufügen, z. B. eine PDF-Datei, legen Sie `{https://www.alfresco.org/model/content/1.0}content` fest. Dieser Wert ist ein obligatorischer Parameter.
   * Ein `com.adobe.idp.Document`-Objekt, das den Inhalt darstellt. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolge-Wert, der den Kodierungswert angibt (z. B. `UTF-8`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein `UpdateVersionType`-Auflistungs-Wert, der angibt, wie Versionsinformationen verarbeitet werden (z. B. `UpdateVersionType.INCREMENT_MAJOR_VERSION`, um die Inhaltsversion zu erhöhen. ) Dieser Wert ist ein obligatorischer Parameter.
   * Eine `java.util.List`-Instanz, die die mit dem Inhalt zusammenhängenden Aspekte angibt. Dieser Wert ist ein optionaler Parameter, und Sie können `null` festlegen.
   * Ein `java.util.Map`-Objekt, das Inhaltsattribute speichert.

   Die Methode `storeContent` gibt ein `CRCResult`-Objekt zurück, das den Inhalt beschreibt. Durch Verwenden eines `CRCResult`-Objekts, können Sie beispielsweise den eindeutigen Wert der eindeutigen Kennung des Inhalts abrufen. Rufen Sie zum Ausführen dieser Aufgabe die Methode `getNodeUuid` des `CRCResult`-Objekts auf.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
