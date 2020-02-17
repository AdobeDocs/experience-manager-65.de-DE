---
title: Erstellen von PDF-Dokumenten mit übermittelten XML-Daten
seo-title: Erstellen von PDF-Dokumenten mit übermittelten XML-Daten
description: 'null'
seo-description: 'null'
uuid: 2676c614-8988-451b-ac7c-bd07731a3f5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 62490230-a24e-419d-95bb-c0bb04a03f96
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Erstellen von PDF-Dokumenten mit gesendeten XML-Daten {#creating-pdf-documents-with-submittedxml-data}

## Erstellen von PDF-Dokumenten mit gesendeten XML-Daten {#creating-pdf-documents-with-submitted-xml-data}

Webbasierte Anwendungen, die es Benutzern ermöglichen, interaktive Formulare auszufüllen, erfordern, dass die Daten an den Server zurückgesendet werden. Mit dem Forms-Dienst können Sie die Formulardaten abrufen, die der Benutzer in ein interaktives Formular eingegeben hat. Anschließend können Sie die Formulardaten an einen anderen AEM Forms-Dienstvorgang weiterleiten und ein PDF-Dokument mit den Daten erstellen.

>[!NOTE]
>
>Bevor Sie diesen Inhalt lesen, sollten Sie mit dem Umgang mit gesendeten Formularen vertraut sein. Konzepte wie die Beziehung zwischen einem Formularentwurf und gesendeten XML-Daten werden unter Verarbeiten gesendeter Formulare behandelt.

Betrachten Sie den folgenden Arbeitsablauf, der drei AEM Forms-Dienste umfasst:

* Ein Benutzer sendet XML-Daten von einer webbasierten Anwendung an den Forms-Dienst.
* Der Forms-Dienst wird zum Verarbeiten des gesendeten Formulars und zum Extrahieren von Formularfeldern verwendet. Formulardaten können verarbeitet werden. Die Daten können beispielsweise an eine Unternehmensdatenbank gesendet werden.
* Formulardaten werden an den Output-Dienst gesendet, um ein nicht interaktives PDF-Dokument zu erstellen.
* Das nicht interaktive PDF-Dokument wird in Content Services (nicht mehr unterstützt) gespeichert.

Das folgende Diagramm zeigt eine visuelle Darstellung dieses Workflows.

![cd_cd_finsrv_architecture_xml_pdf1](assets/cd_cd_finsrv_architecture_xml_pdf1.png)

Nachdem der Benutzer das Formular über den Client-Webbrowser gesendet hat, wird das nicht interaktive PDF-Dokument in Content Services (nicht mehr unterstützt) gespeichert. Die folgende Abbildung zeigt ein in Content Services gespeichertes PDF-Dokument (nicht mehr unterstützt).

![cd_cd_cs_gui](assets/cd_cd_cs_gui.png)

### Zusammenfassung der Schritte {#summary-of-steps}

So erstellen Sie ein nicht interaktives PDF-Dokument mit gesendeten XML-Daten und speichern es im PDF-Dokument in Content Services (nicht mehr unterstützt):

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie Forms-, Output- und Document Management-Objekte.
1. Rufen Sie Formulardaten mithilfe des Forms-Dienstes ab.
1. Erstellen Sie ein nicht interaktives PDF-Dokument mit dem Output-Dienst.
1. Speichern Sie das PDF-Formular mit dem Document Management-Dienst in Content Services (nicht mehr unterstützt).

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen von Forms-, Output- und Document Management-Objekten**

Bevor Sie einen Forms-Dienst-API-Vorgang programmgesteuert durchführen können, erstellen Sie ein Forms Client-API-Objekt. Da dieser Workflow die Output- und Document Management-Dienste aufruft, erstellen Sie auch ein Output Client-API-Objekt und ein Document Management Client-API-Objekt.

**Abrufen von Formulardaten mit dem Forms-Dienst**

Rufen Sie Formulardaten ab, die an den Forms-Dienst gesendet wurden. Sie können gesendete Daten entsprechend Ihren Geschäftsanforderungen verarbeiten. Sie können beispielsweise Formulardaten in einer Unternehmensdatenbank speichern. Um jedoch ein nicht interaktives PDF-Dokument zu erstellen, werden die Formulardaten an den Output-Dienst übergeben.

**Erstellen Sie ein nicht interaktives PDF-Dokument mit dem Output-Dienst.**

Verwenden Sie den Output-Dienst, um ein nicht interaktives PDF-Dokument zu erstellen, das auf einem Formularentwurf und XML-Formulardaten basiert. Im Arbeitsablauf werden die Formulardaten vom Forms-Dienst abgerufen.

**Speichern des PDF-Formulars in Content Services (nicht mehr unterstützt) mithilfe des Document Management-Dienstes**

Verwenden Sie die Document Management-Dienst-API, um ein PDF-Dokument in Content Services (nicht mehr unterstützt) zu speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

### Erstellen eines PDF-Dokuments mit gesendeten XML-Daten mithilfe der Java-API {#create-a-pdf-document-with-submitted-xml-data-using-the-java-api}

Erstellen Sie ein PDF-Dokument mit gesendeten XML-Daten mithilfe der Forms-, Output- und Document Management API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;, &quot;adobe-output-client.jar&quot;und &quot;adobe-contentservices-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen von Forms-, Output- und Document Management-Objekten

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Create an `OutputClient` object by using its constructor and passing the `ServiceClientFactory` object.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen von Formulardaten mit dem Forms-Dienst

   * Rufen Sie die `FormsServiceClient` Objektmethode `processFormSubmission` auf und übergeben Sie die folgenden Werte:

      * Das `com.adobe.idp.Document` Objekt, das die Formulardaten enthält.
      * Ein Zeichenfolgenwert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Header angibt. Geben Sie den zu verwaltenden Inhaltstyp an, indem Sie einen oder mehrere Werte für die `CONTENT_TYPE` Umgebungsvariable angeben. Um beispielsweise XML-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=text/xml`.
      * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT` Kopfzeilenwert angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Ein `RenderOptionsSpec` Objekt, das Laufzeitoptionen speichert.
      Die `processFormSubmission` Methode gibt ein `FormsResult` Objekt zurück, das die Ergebnisse der Formularübermittlung enthält.

   * Stellen Sie fest, ob die Verarbeitung der Formulardaten durch den Forms-Dienst abgeschlossen ist, indem Sie die `FormsResult` Objektmethode `getAction` aufrufen. Wenn diese Methode den Wert zurückgibt `0`, können die Daten verarbeitet werden.
   * Rufen Sie Formulardaten ab, indem Sie ein `com.adobe.idp.Document` Objekt erstellen, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen. (Dieses Objekt enthält Formulardaten, die an den Output-Dienst gesendet werden können.)
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie den `java.io.DataInputStream` Konstruktor aufrufen und das `com.adobe.idp.Document` Objekt übergeben.
   * Erstellen Sie ein `org.w3c.dom.DocumentBuilderFactory` Objekt, indem Sie die `org.w3c.dom.DocumentBuilderFactory` Methode des statischen `newInstance` Objekts aufrufen.
   * Erstellen Sie ein `org.w3c.dom.DocumentBuilder` Objekt, indem Sie die `org.w3c.dom.DocumentBuilderFactory` Objektmethode `newDocumentBuilder` aufrufen.
   * Create an `org.w3c.dom.Document` object by invoking the `org.w3c.dom.DocumentBuilder` object’s `parse` method and passing the `java.io.InputStream` object.
   * Rufen Sie den Wert jeder Node im XML-Dokument ab. Eine Möglichkeit, diese Aufgabe durchzuführen, besteht darin, eine benutzerdefinierte Methode zu erstellen, die zwei Parameter akzeptiert: das `org.w3c.dom.Document` Objekt und den Namen der Node, deren Wert Sie abrufen möchten. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert der Node darstellt. Im Codebeispiel, das diesem Prozess folgt, wird diese benutzerdefinierte Methode aufgerufen `getNodeText`. Der Hauptteil dieser Methode wird angezeigt.


1. Erstellen Sie ein nicht interaktives PDF-Dokument mit dem Output-Dienst.

   Create a PDF document by invoking the `OutputClient` object’s `generatePDFOutput` method and passing the following values:

   * Ein `TransformationFormat` Enumwert. Um ein PDF-Dokument zu erstellen, geben Sie `TransformationFormat.PDF`an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt. Stellen Sie sicher, dass der Formularentwurf mit den vom Forms-Dienst abgerufenen Formulardaten kompatibel ist.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, an dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document` Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen. Stellen Sie sicher, dass dieses Objekt von der `FormsResult` Objektmethode zurückgegeben `getOutputContent` wurde.
   * The `generatePDFOutput` method returns an `OutputResult` object that contains the results of the operation.
   * Rufen Sie das nicht interaktive PDF-Dokument ab, indem Sie die `OutputResult` Objektmethode `getGeneratedDoc` aufrufen. Diese Methode gibt eine `com.adobe.idp.Document` Instanz zurück, die das nicht interaktive PDF-Dokument darstellt.

1. Speichern des PDF-Formulars in Content Services (nicht mehr unterstützt) mithilfe des Document Management-Dienstes

   Fügen Sie den Inhalt hinzu, indem Sie die `DocumentManagementServiceClientImpl` Methode des `storeContent` Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Store angibt, in dem der Inhalt hinzugefügt wird. The default store is `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den vollständig qualifizierten Pfad des Bereichs angibt, in dem der Inhalt hinzugefügt wird (z. B. `/Company Home/Test Directory`). Dieser Wert ist ein obligatorischer Parameter.
   * Der Knotenname, der den neuen Inhalt darstellt (z. B. `MortgageForm.pdf`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den Knotentyp angibt. Um neue Inhalte hinzuzufügen, z. B. eine PDF-Datei, geben Sie an `{https://www.alfresco.org/model/content/1.0}content`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein `com.adobe.idp.Document` Objekt, das den Inhalt darstellt. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den Kodierungswert angibt (z. B. `UTF-8`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein `UpdateVersionType` Aufzählungswert, der angibt, wie Versionsinformationen verarbeitet werden (z. B. `UpdateVersionType.INCREMENT_MAJOR_VERSION` um die Inhaltsversion zu erhöhen). ) Dieser Wert ist ein obligatorischer Parameter.
   * Eine `java.util.List` Instanz, die inhaltliche Aspekte angibt. Dieser Wert ist ein optionaler Parameter und Sie können ihn angeben `null`.
   * Ein `java.util.Map` Objekt, das Inhaltsattribute speichert.
   Die `storeContent` Methode gibt ein `CRCResult` Objekt zurück, das den Inhalt beschreibt. Mithilfe eines `CRCResult` Objekts können Sie beispielsweise den eindeutigen Bezeichnerwert des Inhalts abrufen. Um diese Aufgabe auszuführen, rufen Sie die `CRCResult` Methode des `getNodeUuid` Objekts auf.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
