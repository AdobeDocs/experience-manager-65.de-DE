---
title: Erstellen von PDF-Dokumenten mit SubmittedXML-Daten
seo-title: Erstellen von PDF-Dokumenten mit SubmittedXML-Daten
description: Verwenden Sie den Forms-Dienst, um die Formulardaten abzurufen, die der Benutzer in ein interaktives Formular eingegeben hat. Übergeben Sie die Formulardaten an einen anderen AEM Forms-Dienstvorgang und erstellen Sie mithilfe der Daten ein PDF-Dokument.
seo-description: Verwenden Sie den Forms-Dienst, um die Formulardaten abzurufen, die der Benutzer in ein interaktives Formular eingegeben hat. Übergeben Sie die Formulardaten an einen anderen AEM Forms-Dienstvorgang und erstellen Sie mithilfe der Daten ein PDF-Dokument.
uuid: 2676c614-8988-451b-ac7c-bd07731a3f5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 62490230-a24e-419d-95bb-c0bb04a03f96
role: Developer
exl-id: d9d5b94a-9d10-4d90-9e10-5142f30ba4a3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1361'
ht-degree: 4%

---

# Erstellen von PDF-Dokumenten mit gesendeten XML-Daten {#creating-pdf-documents-with-submittedxml-data}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Erstellen von PDF-Dokumenten mit gesendeten XML-Daten {#creating-pdf-documents-with-submitted-xml-data}

Webbasierte Anwendungen, die es Benutzern ermöglichen, interaktive Formulare auszufüllen, erfordern, dass die Daten an den Server zurückgesendet werden. Mithilfe des Forms-Dienstes können Sie die Formulardaten abrufen, die der Benutzer in ein interaktives Formular eingegeben hat. Anschließend können Sie die Formulardaten an einen anderen AEM Forms-Dienstvorgang übergeben und mithilfe der Daten ein PDF-Dokument erstellen.

>[!NOTE]
>
>Bevor Sie diesen Inhalt lesen, sollten Sie über fundierte Kenntnisse im Umgang mit gesendeten Formularen verfügen. Konzepte wie die Beziehung zwischen einem Formularentwurf und gesendeten XML-Daten werden unter Verarbeiten gesendeter Forms behandelt.

Betrachten Sie den folgenden Workflow, der drei AEM Forms-Dienste umfasst:

* Ein Benutzer sendet XML-Daten von einer webbasierten Anwendung an den Forms-Dienst.
* Der Forms-Dienst wird verwendet, um das gesendete Formular zu verarbeiten und Formularfelder zu extrahieren. Formulardaten können verarbeitet werden. Beispielsweise können die Daten an eine Unternehmensdatenbank gesendet werden.
* Formulardaten werden an den Output-Dienst gesendet, um ein nicht interaktives PDF-Dokument zu erstellen.
* Das nicht interaktive PDF-Dokument wird in Content Services (nicht mehr unterstützt) gespeichert.

Das folgende Diagramm zeigt eine visuelle Darstellung dieses Workflows.

![cd_cd_finsrv_architecture_xml_pdf1](assets/cd_cd_finsrv_architecture_xml_pdf1.png)

Nachdem der Benutzer das Formular über den Client-Webbrowser gesendet hat, wird das nicht interaktive PDF-Dokument in Content Services (nicht mehr unterstützt) gespeichert. Die folgende Abbildung zeigt ein PDF-Dokument, das in Content Services (nicht mehr unterstützt) gespeichert ist.

![cd_cd_cs_gui](assets/cd_cd_cs_gui.png)

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein nicht interaktives PDF-Dokument mit gesendeten XML-Daten zu erstellen und in Content Services (nicht mehr unterstützt) im PDF-Dokument zu speichern, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie Forms-, Output- und Document Management-Objekte.
1. Rufen Sie Formulardaten mithilfe des Forms-Dienstes ab.
1. Erstellen Sie ein nicht interaktives PDF-Dokument mit dem Output-Dienst.
1. Speichern Sie das PDF-Formular mithilfe des Document Management-Dienstes in Content Services (nicht mehr unterstützt).

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen von Forms-, Output- und Document Management-Objekten**

Bevor Sie einen Forms-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Forms Client-API-Objekt. Da dieser Workflow die Output- und Document Management-Dienste aufruft, erstellen Sie sowohl ein Output Client-API-Objekt als auch ein Document Management Client-API-Objekt.

**Abrufen von Formulardaten mit dem Forms-Dienst**

Rufen Sie Formulardaten ab, die an den Forms-Dienst gesendet wurden. Sie können gesendete Daten entsprechend Ihren Geschäftsanforderungen verarbeiten. Beispielsweise können Sie Formulardaten in einer Unternehmensdatenbank speichern. Um jedoch ein nicht interaktives PDF-Dokument zu erstellen, werden die Formulardaten an den Output-Dienst übergeben.

**Erstellen Sie ein nicht interaktives PDF-Dokument mit dem Output-Dienst.**

Verwenden Sie den Output-Dienst, um ein nicht interaktives PDF-Dokument zu erstellen, das auf einem Formularentwurf und XML-Formulardaten basiert. Im Workflow werden die Formulardaten vom Forms-Dienst abgerufen.

**Speichern Sie das PDF-Formular in Content Services (nicht mehr unterstützt) mit dem Document Management-Dienst.**

Verwenden Sie die Document Management-Dienst-API zum Speichern eines PDF-Dokuments in Content Services (nicht mehr unterstützt).

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

### Erstellen eines PDF-Dokuments mit gesendeten XML-Daten mithilfe der Java-API {#create-a-pdf-document-with-submitted-xml-data-using-the-java-api}

Erstellen Sie ein PDF-Dokument mit gesendeten XML-Daten mithilfe der Forms-, Output- und Document Management-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar, adobe-output-client.jar und adobe-contentservices-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen von Forms-, Output- und Document Management-Objekten

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen von Formulardaten mit dem Forms-Dienst

   * Rufen Sie die `processFormSubmission` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

      * Das `com.adobe.idp.Document`-Objekt, das die Formulardaten enthält.
      * Ein string -Wert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Header angibt. Geben Sie den Inhaltstyp an, der verarbeitet werden soll, indem Sie einen oder mehrere Werte für die Umgebungsvariable `CONTENT_TYPE` angeben. Um beispielsweise XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`.
      * Ein string -Wert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen speichert.

      Die `processFormSubmission`-Methode gibt ein `FormsResult`-Objekt zurück, das die Ergebnisse der Formularübermittlung enthält.

   * Stellen Sie fest, ob der Forms-Dienst die Verarbeitung der Formulardaten abgeschlossen hat, indem Sie die `getAction` -Methode des Objekts `FormsResult` aufrufen. Wenn diese Methode den Wert `0` zurückgibt, können die Daten verarbeitet werden.
   * Rufen Sie Formulardaten ab, indem Sie ein `com.adobe.idp.Document` -Objekt erstellen, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen. (Dieses Objekt enthält Formulardaten, die an den Output-Dienst gesendet werden können.)
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie den `java.io.DataInputStream`-Konstruktor aufrufen und das `com.adobe.idp.Document`-Objekt übergeben.
   * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory` -Objekt, indem Sie die `newInstance` -Methode des statischen `org.w3c.dom.DocumentBuilderFactory` -Objekts aufrufen.
   * Erstellen Sie ein `org.w3c.dom.DocumentBuilder` -Objekt, indem Sie die `newDocumentBuilder` -Methode des Objekts `org.w3c.dom.DocumentBuilderFactory` aufrufen.
   * Erstellen Sie ein `org.w3c.dom.Document` -Objekt, indem Sie die `org.w3c.dom.DocumentBuilder` -Methode des Objekts `parse` aufrufen und das `java.io.InputStream` -Objekt übergeben.
   * Rufen Sie den Wert jedes Knotens im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document` -Objekt und den Namen des Knotens, dessen Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert des Knotens darstellt. Im Codebeispiel, das diesem Prozess folgt, heißt diese benutzerdefinierte Methode `getNodeText`. Der Hauptteil dieser Methode wird angezeigt.


1. Erstellen Sie ein nicht interaktives PDF-Dokument mit dem Output-Dienst.

   Erstellen Sie ein PDF-Dokument, indem Sie die `generatePDFOutput` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein Enum-Wert `TransformationFormat`. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt. Stellen Sie sicher, dass der Formularentwurf mit den vom Forms-Dienst abgerufenen Formulardaten kompatibel ist.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen. Stellen Sie sicher, dass dieses Objekt von der `FormsResult` -Methode des Objekts `getOutputContent` zurückgegeben wurde.
   * Die `generatePDFOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.
   * Rufen Sie das nicht interaktive PDF-Dokument ab, indem Sie die `getGeneratedDoc` -Methode des Objekts `OutputResult` aufrufen. Diese Methode gibt eine `com.adobe.idp.Document`-Instanz zurück, die das nicht interaktive PDF-Dokument darstellt.

1. Speichern Sie das PDF-Formular in Content Services (nicht mehr unterstützt) mithilfe des Document Management-Dienstes.

   Fügen Sie den Inhalt hinzu, indem Sie die `storeContent` -Methode des Objekts `DocumentManagementServiceClientImpl` aufrufen und die folgenden Werte übergeben:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des Bereichs angibt, in dem der Inhalt hinzugefügt wird (z. B. `/Company Home/Test Directory`). Dieser Wert ist ein obligatorischer Parameter.
   * Der Knotenname, der den neuen Inhalt darstellt (z. B. `MortgageForm.pdf`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den Knotentyp angibt. Um neuen Inhalt hinzuzufügen, z. B. eine PDF-Datei, geben Sie `{https://www.alfresco.org/model/content/1.0}content` an. Dieser Wert ist ein obligatorischer Parameter.
   * Ein `com.adobe.idp.Document` -Objekt, das den Inhalt darstellt. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den Kodierungswert angibt (z. B. `UTF-8`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein `UpdateVersionType` -Auflistungswert, der angibt, wie Versionsinformationen verarbeitet werden (z. B. `UpdateVersionType.INCREMENT_MAJOR_VERSION`, um die Inhaltsversion zu inkrementieren. ) Dieser Wert ist ein obligatorischer Parameter.
   * Eine `java.util.List`-Instanz, die Aspekte angibt, die mit dem Inhalt zusammenhängen. Dieser Wert ist ein optionaler Parameter und Sie können `null` angeben.
   * Ein `java.util.Map` -Objekt, das Inhaltsattribute speichert.

   Die `storeContent`-Methode gibt ein `CRCResult`-Objekt zurück, das den Inhalt beschreibt. Mit einem `CRCResult` -Objekt können Sie beispielsweise den eindeutigen Bezeichnerwert des Inhalts abrufen. Rufen Sie dazu die `getNodeUuid` -Methode des Objekts `CRCResult` auf.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
