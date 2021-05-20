---
title: Erstellen von Document Output Streams
seo-title: Erstellen von Document Output Streams
description: Verwenden Sie den Output-Dienst zum Konvertieren von Dokumenten in die Beschriftungsformate PDF (einschließlich PDF/A-Dokumente), PostScript, Printer Control Language (PCL) und Zebra - ZPL, Intermec - IPL, Datamax - DPL und TecToshiba - TPCL .
seo-description: Verwenden Sie den Output-Dienst zum Konvertieren von Dokumenten in die Beschriftungsformate PDF (einschließlich PDF/A-Dokumente), PostScript, Printer Control Language (PCL) und Zebra - ZPL, Intermec - IPL, Datamax - DPL und TecToshiba - TPCL .
uuid: 80c28efa-35ce-4073-9ca6-2d93bcd67fdd
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: de527d50-991b-4ca3-a8ac-44d5cab988e9
role: Developer
exl-id: a521bfac-f417-4002-9c5c-8d7794d3eec7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '19044'
ht-degree: 4%

---

# Erstellen von Document Output Streams {#creating-document-output-streams}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

**Über den Output-Dienst**

Mit dem Output-Dienst können Sie Dokumente als PDF (einschließlich PDF/A-Dokumente), PostScript, Printer Control Language (PCL) und die folgenden Beschriftungsformate ausgeben:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Mithilfe des Output-Dienstes können Sie XML-Formulardaten mit einem Formularentwurf zusammenführen und das Dokument an einen Netzwerkdrucker oder eine Datei ausgeben.

Es gibt zwei Möglichkeiten, einen Formularentwurf (eine XDP-Datei) an den Output-Dienst zu übergeben. Sie können entweder eine `com.adobe.idp.Document`-Instanz übergeben, die einen Formularentwurf enthält, an den Output-Dienst. Sie können auch einen URI-Wert übergeben, der den Speicherort des Formularentwurfs angibt. Beide Methoden werden unter *Programmieren mit AEM Formularen* erläutert.

>[!NOTE]
>
>Der Output-Dienst unterstützt keine Acroform PDF-Dokumente, die anwendungsobjektspezifische Skripte enthalten. Acroform PDF-Dokumente, die anwendungsobjektspezifische Skripte enthalten, werden nicht gerendert.

Die folgenden Abschnitte zeigen, wie Sie einen Formularentwurf mithilfe eines URI-Werts an den Output-Dienst übergeben:

* [Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)
* [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents)

Die folgenden Abschnitte zeigen, wie Sie einen Formularentwurf in einer `com.adobe.idp.Document`-Instanz übergeben:

* [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Erstellen von PDF-Dokumenten mit Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

Eine Überlegung bei der Entscheidung, welche Technik verwendet werden soll, besteht darin, den Formularentwurf von einem anderen AEM Forms-Dienst zu erhalten und ihn dann in einer `com.adobe.idp.Document`-Instanz zu übergeben. Sowohl in den Abschnitten *Übergeben von Dokumenten an den Output-Dienst* als auch *Erstellen von PDF-Dokumenten mit Fragmenten* wird gezeigt, wie ein Formularentwurf von einem anderen AEM Forms-Dienst abgerufen wird. Im ersten Abschnitt wird der Formularentwurf aus Content Services (nicht mehr unterstützt) abgerufen. Der zweite Abschnitt ruft den Formularentwurf vom Assembler-Dienst ab.

Wenn Sie den Formularentwurf von einem festen Speicherort wie dem Dateisystem erhalten, können Sie beide Verfahren verwenden. Das heißt, Sie können den URI-Wert in eine XDP-Datei angeben oder eine `com.adobe.idp.Document`-Instanz verwenden.

Um einen URI-Wert zu übergeben, der den Speicherort des Formularentwurfs beim Erstellen eines PDF-Dokuments angibt, verwenden Sie die Methode `generatePDFOutput` . Um beim Erstellen eines PDF-Dokuments eine `com.adobe.idp.Document`-Instanz an den Output-Dienst zu übergeben, verwenden Sie die `generatePDFOutput2`-Methode.

Wenn Sie einen Ausgabestream an einen Netzwerkdrucker senden, können Sie auch eine der beiden Methoden verwenden. Um einen Ausgabestream an einen Drucker zu senden, indem eine `com.adobe.idp.Document`-Instanz übergeben wird, die einen Formularentwurf enthält, verwenden Sie die `sendToPrinter2`Methode. Um einen Ausgabestream an einen Drucker zu senden, indem ein URI-Wert übergeben wird, verwenden Sie die Methode `sendToPrinter`. Der Abschnitt *Senden von Druckströmen an Drucker* verwendet die `sendToPrinter`-Methode.

Sie können diese Aufgaben mithilfe des Output-Dienstes ausführen:

* [Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)
* [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents)
* [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Erstellen von PDF-Dokumenten mit Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)
* [Drucken in Dateien](creating-document-output-streams.md#printing-to-files)
* [Senden von Druck-Streams an Drucker](creating-document-output-streams.md#sending-print-streams-to-printers)
* [Erstellen mehrerer Ausgabedateien](creating-document-output-streams.md#creating-multiple-output-files)
* [Erstellen von Suchregeln](creating-document-output-streams.md#creating-search-rules)
* [Reduzieren von PDF-Dokumenten](creating-document-output-streams.md#flattening-pdf-documents)

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Erstellen von PDF-Dokumenten {#creating-pdf-documents}

Sie können den Output-Dienst verwenden, um ein PDF-Dokument zu erstellen, das auf einem Formularentwurf und den von Ihnen bereitgestellten XML-Formulardaten basiert. Das vom Output-Dienst erstellte PDF-Dokument ist kein interaktives PDF-Dokument. Benutzer können keine Formulardaten eingeben oder ändern.

Wenn Sie ein PDF-Dokument für die langfristige Speicherung erstellen möchten, wird empfohlen, ein PDF/A-Dokument zu erstellen. (Siehe [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents).)

Verwenden Sie den Forms-Dienst, um ein interaktives PDF-Formular zu erstellen, mit dem Benutzer Daten eingeben können. (Siehe [Rendern interaktiver PDF forms](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms).)

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Festlegen von PDF-Laufzeitoptionen.
1. Festlegen von Rendering-Laufzeitoptionen.
1. Generieren Sie ein PDF-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Referenzieren einer XML-Datenquelle**

Um Daten mit dem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle referenzieren, die Daten enthält. Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

Betrachten Sie das folgende Beispielformular für einen Kreditantrag.

![cp_cp_loanformdata](assets/cp_cp_loanformdata.png)

Um Daten in diesem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle erstellen, die dem Formular entspricht. Die folgende XML-Datei stellt eine XDP-XML-Datenquelle dar, die dem Beispiel-Hypothekenantragsformular entspricht.

```xml
 <?xml version="1.0" encoding="UTF-8" ?>
 - <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
 - <xfa:data>
 - <data>
     - <Layer>
         <closeDate>1/26/2007</closeDate>
         <lastName>Johnson</lastName>
         <firstName>Jerry</firstName>
         <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
         <city>New York</city>
         <zipCode>00501</zipCode>
         <state>NY</state>
         <dateBirth>26/08/1973</dateBirth>
         <middleInitials>D</middleInitials>
         <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
         <phoneNumber>5555550000</phoneNumber>
     </Layer>
     - <Mortgage>
         <mortgageAmount>295000.00</mortgageAmount>
         <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
         <purchasePrice>300000</purchasePrice>
         <downPayment>5000</downPayment>
         <term>25</term>
         <interestRate>5.00</interestRate>
     </Mortgage>
 </data>
 </xfa:data>
 </xfa:datasets>
```

**PDF-Laufzeitoptionen festlegen**

Legen Sie die Datei-URI-Option beim Erstellen eines PDF-Dokuments fest. Diese Option gibt den Namen und Speicherort der PDF-Datei an, die der Output-Dienst generiert.

>[!NOTE]
>
>Anstatt die Laufzeitoption für den Datei-URI festzulegen, können Sie das PDF-Dokument programmgesteuert aus dem komplexen Datentyp abrufen, der vom Output-Dienst zurückgegeben wird. Durch Festlegen der Laufzeitoption für den Datei-URI müssen Sie jedoch keine Anwendungslogik erstellen, die das PDF-Dokument programmgesteuert abruft.

**Festlegen von Rendering-Laufzeitoptionen**

Beim Erstellen eines PDF-Dokuments können Sie Laufzeitoptionen für die Wiedergabe festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu PDF-Laufzeitoptionen, die erforderlich sind), können Sie Aufgaben wie die Verbesserung der Leistung des Output-Dienstes ausführen. Beispielsweise können Sie den Formularentwurf zwischenspeichern, den der Output-Dienst verwendet, um seine Leistung zu verbessern.

Wenn Sie ein getaggtes Acrobat-Formular als Eingabe verwenden, können Sie die Java- oder Webdienst-API des Output-Dienstes nicht verwenden, um die getaggte Einstellung zu deaktivieren. Wenn Sie versuchen, diese Option programmatisch auf `false` festzulegen, wird das PDF-Ergebnisdokument weiterhin mit Tags versehen.

>[!NOTE]
>
>Wenn Sie keine Rendering-Laufzeitoptionen festlegen, werden Standardwerte verwendet. Informationen zum Rendern von Laufzeitoptionen finden Sie in der `RenderOptionsSpec`-Klassenreferenz. (Siehe [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

**Generieren eines PDF-Dokuments**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die Formulardaten enthält, und Laufzeitoptionen festgelegt haben, können Sie den Output-Dienst aufrufen, wodurch ein PDF-Dokument generiert wird.

Beim Generieren eines PDF-Dokuments geben Sie URI-Werte an, die vom Output-Dienst zum Erstellen eines PDF-Dokuments erforderlich sind. Ein Formularentwurf kann in Speicherorten wie dem Serverdateisystem oder im Rahmen einer AEM Forms-Anwendung gespeichert werden. Ein Formularentwurf (oder andere Ressourcen wie eine Bilddatei), der Teil einer Forms-Anwendung ist, kann mithilfe des Inhaltsstamm-URI-Werts `repository:///` referenziert werden. Betrachten Sie beispielsweise den folgenden Formularentwurf mit dem Namen *Loan.xdp* in einer Forms-Anwendung mit dem Namen *Applications/FormsApplication*:

![cp_cp_formrepository](assets/cp_cp_formrepository.png)

Um auf die in der vorherigen Abbildung dargestellte Datei &quot;Loan.xdp&quot;zuzugreifen, geben Sie `repository:///Applications/FormsApplication/1.0/FormsFolder/` als dritten Parameter an, der an die `OutputClient` -Methode des Objekts `generatePDFOutput` übergeben wird. Geben Sie den Formularnamen (*Loan.xdp*) als zweiten Parameter an, der an die `OutputClient` -Methode des Objekts `generatePDFOutput` übergeben wird.

Wenn die XDP-Datei Bilder (oder andere Ressourcen wie Fragmente) enthält, platzieren Sie die Ressourcen im selben Anwendungsordner wie die XDP-Datei. AEM Forms verwendet den Inhaltsstamm-URI als Basispfad, um Verweise auf Bilder aufzulösen. Wenn die Datei &quot;Loan.xdp&quot;beispielsweise ein Bild enthält, stellen Sie sicher, dass Sie das Bild in `Applications/FormsApplication/1.0/FormsFolder/` platzieren.

>[!NOTE]
>
>Sie können auf einen Forms-Anwendungs-URI verweisen, wenn Sie die `generatePDFOutput`- oder `generatePrintedOutput`-Methoden des Objekts `OutputClient` aufrufen.

>[!NOTE]
>
>Einen vollständigen Schnellstart zum Erstellen eines PDF-Dokuments durch Referenzieren einer XDP-Datei in einer Forms-Anwendung finden Sie unter [Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments basierend auf einer Anwendungs-XDP-Datei mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api).

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, gibt er verschiedene Datenelemente zurück, z. B. Status-XML-Daten, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Erstellen eines PDF-Dokuments mit der Java-API](creating-document-output-streams.md#create-a-pdf-document-using-the-java-api)

[Erstellen eines PDF-Dokuments mit der Webdienst-API](creating-document-output-streams.md#create-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen eines PDF-Dokuments mit der Java-API {#create-a-pdf-document-using-the-java-api}

Erstellen Sie ein PDF-Dokument mithilfe der Ausgabe-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des PDF-Dokuments mithilfe des zugehörigen Konstruktors verwendet wird, und übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein Objekt `com.adobe.idp.Document`, indem Sie den Konstruktor verwenden. Übergeben Sie das `java.io.FileInputStream`-Objekt.

1. Festlegen von PDF-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Datei-URI fest, indem Sie die `setFileURI` -Methode des Objekts `PDFOutputOptionsSpec` aufrufen. Übergeben Sie einen string -Wert, der den Speicherort der vom Output-Dienst generierten PDF-Datei angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie die `setCacheEnabled`-Objektgruppe `RenderOptionsSpec` aufrufen und `true` übergeben.

   >[!NOTE]
   >
   >Sie können die Version des PDF-Dokuments nicht mithilfe der `RenderOptionsSpec`-Methode des Objekts `setPdfVersion` festlegen, wenn es sich bei dem Eingabedokument um ein Acrobat-Formular (ein in Acrobat erstelltes Formular) oder ein XFA-Dokument handelt, das signiert oder zertifiziert ist. Das PDF-Ausgabedokument behält die ursprüngliche PDF-Version bei. Ebenso können Sie die getaggte Adobe PDF-Option nicht festlegen, indem Sie die `setTaggedPDF` -Methode des Objekts `RenderOptionsSpec` aufrufen, wenn das Eingabedokument ein Acrobat-Formular oder ein signiertes oder zertifiziertes XFA-Dokument ist.

   >[!NOTE]
   >
   >Sie können die Option für linearisierte PDF nicht mithilfe der `RenderOptionsSpec` -Methode des Objekts `setLinearizedPDF` festlegen, wenn das PDF-Eingabedokument zertifiziert oder digital signiert ist. (Siehe [Digital Signing PDF Documents ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Generieren Sie ein PDF-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die `generatePDFOutput` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

   >[!NOTE]
   >
   >Beachten Sie beim Generieren eines PDF-Dokuments durch Aufrufen der `generatePDFOutput`-Methode, dass Sie keine Daten mit einem signierten oder zertifizierten XFA-PDF-Formular zusammenführen können. (Siehe [Digitales Signieren und Zertifizieren von Dokumenten ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >Die `OutputResult`-Methode des Objekts `getRecordLevelMetaDataList` gibt `null`*zurück.*

   >[!NOTE]
   >
   >Sie können ein PDF-Dokument auch erstellen, indem Sie die `generatePDFOutput2` -Methode des Objekts `OutputClient` aufrufen. (Siehe [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Rufen Sie ein `com.adobe.idp.Document` -Objekt ab, das den Status des Vorgangs `generatePDFOutput` darstellt, indem Sie die `OutputResult` -Methode des Objekts `getStatusDoc` aufrufen. Diese Methode gibt Status-XML-Daten zurück, die angeben, ob der Vorgang erfolgreich war.
   * Erstellen Sie ein `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document` -Objekt verwenden, das von der `getStatusDoc` -Methode zurückgegeben wurde).

   Obwohl der Output-Dienst das PDF-Dokument an den Speicherort schreibt, der durch das an die `setFileURI` -Methode des `PDFOutputOptionsSpec` -Objekts übergebene Argument angegeben ist, können Sie das PDF/A-Dokument programmgesteuert abrufen, indem Sie die `OutputResult` -Methode des Objekts `getGeneratedDoc` aufrufen.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen eines PDF-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen Sie ein PDF-Dokument mithilfe der Webdienst-API {#create-a-pdf-document-using-the-web-service-api}

Erstellen Sie ein PDF-Dokument mithilfe der Output API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von XML-Daten verwendet, die mit dem PDF-Dokument zusammengeführt werden.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der XML-Datei darstellt, die Formulardaten enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. PDF-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Datei-URI fest, indem Sie einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Output-Dienst generierten PDF-Datei an das `fileURI`-Datenelement des Objekts `PDFOutputOptionsSpec` angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie den Wert `true` dem `RenderOptionsSpec`-Datenelement des `cacheEnabled`-Objekts zuweisen.

   >[!NOTE]
   >
   >Sie können die Version des PDF-Dokuments nicht mithilfe der `RenderOptionsSpec`-Methode des Objekts `setPdfVersion` festlegen, wenn es sich bei dem Eingabedokument um ein Acrobat-Formular (ein in Acrobat erstelltes Formular) oder ein XFA-Dokument handelt, das signiert oder zertifiziert ist. Das PDF-Ausgabedokument behält die ursprüngliche PDF-Version bei. Ebenso können Sie die getaggte Adobe PDF-Option nicht festlegen, indem Sie die `setTaggedPDF`-Methode des Objekts `RenderOptionsSpec` aufrufen, wenn es sich bei dem Eingabedokument um ein Acrobat-Formular oder ein signiertes oder zertifiziertes XFA-Dokument handelt.*

   >[!NOTE]
   >
   >Sie können die Option für linearisierte PDF nicht mithilfe des Elements `RenderOptionsSpec` des Objekts `linearizedPDF` festlegen, wenn das PDF-Eingabedokument zertifiziert oder digital signiert ist. (Siehe [Digital Signing PDF Documents ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Generieren Sie ein PDF-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die `generatePDFOutput`Methode des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

   >[!NOTE]
   >
   >Beachten Sie beim Generieren eines PDF-Dokuments durch Aufrufen der `generatePDFOutput`-Methode, dass Sie keine Daten mit einem signierten oder zertifizierten XFA-PDF-Formular zusammenführen können. (Siehe [Digitales Signieren und Zertifizieren von Dokumenten ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >Sie können ein PDF-Dokument auch erstellen, indem Sie die `generatePDFOutput2` -Methode des Objekts `OutputClient` aufrufen. (Siehe [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des Objekts `BLOB` speichert, das mit Ergebnisdaten aus der `OutputServiceService` -Methode des Objekts `generatePDFOutput` (dem achten Parameter) gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Objekts `MTOM` `field` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

   Siehe auch

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

   >[!NOTE]
   >
   >Die `generateOutput`-Methode des `OutputServiceService`-Objekts wird nicht mehr unterstützt.

## Erstellen von PDF/A-Dokumenten {#creating-pdf-a-documents}

Sie können den Output-Dienst verwenden, um ein PDF/A-Dokument zu erstellen. Da PDF/A ein Archivierungsformat für die langfristige Beibehaltung des Dokumentinhalts ist, werden alle Schriftarten eingebettet und die Datei unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Darüber hinaus enthält ein PDF/A-Dokument keine Audio- und Videoinhalte. Wie andere Output-Dienstaufgaben stellen Sie sowohl einen Formularentwurf als auch Daten bereit, die mit einem Formularentwurf zusammengeführt werden sollen, um ein PDF/A-Dokument zu erstellen.

Die PDF/A-1-Spezifikation besteht aus zwei Konformitätsstufen: a und b. Der wesentliche Unterschied zwischen den beiden besteht in der Unterstützung der logischen Struktur (Zugänglichkeit), die für die Konformitätsstufe b nicht erforderlich ist. Unabhängig von der Konformitätsstufe bestimmt PDF/A-1, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind.

Obwohl PDF/A der Standard für die Archivierung von PDF-Dokumenten ist, ist es nicht erforderlich, PDF/A zur Archivierung zu verwenden, wenn ein standardmäßiges PDF-Dokument den Anforderungen Ihres Unternehmens entspricht. Mit dem PDF/A-Standard wird eine PDF-Datei erstellt, die über einen langen Zeitraum gespeichert werden kann und die Anforderungen an die Dokumentenerhaltung erfüllt. Beispielsweise kann eine URL nicht in ein PDF/A-Dokument eingebettet werden, da die URL im Laufe der Zeit ungültig werden kann.

Ihr Unternehmen muss seine eigenen Anforderungen, die Zeitdauer, in der Sie das Dokument aufbewahren möchten, Überlegungen zur Dateigröße und Ihre eigene Archivierungsstrategie beurteilen. Mit dem DocConverter-Dienst können Sie programmatisch feststellen, ob ein PDF-Dokument PDF/A-kompatibel ist. (Siehe [Programmatische Bestimmung der PDF/A-Kompatibilität](/help/forms/developing/pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

Ein PDF/A-Dokument muss die im Formularentwurf angegebene Schriftart verwenden und Schriftarten können nicht ersetzt werden. Wenn daher eine Schriftart, die sich in einem PDF-Dokument befindet, auf dem Host-Betriebssystem (OS) nicht verfügbar ist, tritt eine Ausnahme auf.

Wenn ein PDF/A-Dokument in Acrobat geöffnet wird, wird eine Meldung angezeigt, die bestätigt, dass es sich um ein PDF/A-Dokument handelt, wie in der folgenden Abbildung dargestellt.

![cp_cp_pdfamessage](assets/cp_cp_pdfamessage.png)

>[!NOTE]
>
>Die AIIM-Website verfügt über einen Abschnitt mit häufig gestellten Fragen zu PDF/A, auf den Sie unter [https://www.aiim.org/documents/standards/19005-1_FAQ.pdf](https://www.aiim.org/documents/standards/19005-1_FAQ.pdf) zugreifen können.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um ein PDF/A-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Festlegen von PDF/A-Laufzeitoptionen.
1. Festlegen von Rendering-Laufzeitoptionen.
1. Generieren Sie ein PDF/A-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein benutzerdefiniertes Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Referenzieren einer XML-Datenquelle**

Um Daten mit dem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle referenzieren, die Daten enthält. Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

**Festlegen von PDF/A-Laufzeitoptionen**

Sie können die Option Datei-URI beim Erstellen eines PDF/A-Dokuments festlegen. Der URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient. Wenn Sie also C:\Adobe festlegen, wird die Datei in den Ordner auf dem Server geschrieben, nicht in den Client-Computer. Der URI gibt den Namen und Speicherort der PDF/A-Datei an, die der Output-Dienst generiert.

**Festlegen von Rendering-Laufzeitoptionen**

Beim Erstellen von PDF/A-Dokumenten können Sie Laufzeitoptionen für die Wiedergabe festlegen. Zwei PDF/A-bezogene Optionen, die Sie festlegen können, sind die Werte `PDFAConformance` und `PDFARevisionNumber` . Der Wert `PDFAConformance` gibt an, wie ein PDF-Dokument Anforderungen erfüllt, die angeben, wie langfristige elektronische Dokumente beibehalten werden. Gültige Werte für diese Option sind `A` und `B`. Informationen zur Konformität von Level a und B finden Sie in der PDF/A-1 ISO-Spezifikation mit dem Titel *ISO 19005-1 Document Management*.

Der Wert `PDFARevisionNumber` bezieht sich auf die Revisionsnummer eines PDF/A-Dokuments. Informationen zur Revisionsnummer eines PDF/A-Dokuments finden Sie in der PDF/A-1-ISO-Spezifikation mit dem Titel *ISO 19005-1 Document Management*.

>[!NOTE]
>
>Sie können die getaggte Adobe PDF-Option beim Erstellen eines PDF/A 1A-Dokuments nicht auf `false` setzen. PDF/A 1A ist immer ein PDF-Dokument mit Tags. Außerdem können Sie die getaggte Adobe PDF-Option beim Erstellen eines PDF/A 1B-Dokuments nicht auf `true` setzen. PDF/A 1B ist immer ein PDF-Dokument ohne Tags.

**Generieren eines PDF/A-Dokuments**

Nachdem Sie auf eine gültige XML-Datenquelle verweisen, die Formulardaten enthält, und Laufzeitoptionen festgelegt haben, können Sie den Output-Dienst aufrufen, wodurch ein PDF/A-Dokument generiert wird.

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, gibt er verschiedene Datenelemente wie XML-Daten zurück, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Erstellen eines PDF/A-Dokuments mit der Java-API](creating-document-output-streams.md#create-a-pdf-a-document-using-the-java-api)

[Erstellen eines PDF/A-Dokuments mithilfe der Webdienst-API](creating-document-output-streams.md#create-a-pdf-a-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen eines PDF/A-Dokuments mit der Java-API {#create-a-pdf-a-document-using-the-java-api}

Erstellen Sie ein PDF/A-Dokument mithilfe der Ausgabe-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des PDF/A-Dokuments mithilfe des zugehörigen Konstruktors verwendet wird, und übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von PDF/A-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Datei-URI fest, indem Sie die `setFileURI` -Methode des Objekts `PDFOutputOptionsSpec` aufrufen. Übergeben Sie einen string -Wert, der den Speicherort der vom Output-Dienst generierten PDF-Datei angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Wert `PDFAConformance` fest, indem Sie die `RenderOptionsSpec`-Methode des Objekts `setPDFAConformance` aufrufen und einen `PDFAConformance`-Enum-Wert übergeben, der die Konformitätsstufe angibt. Um beispielsweise Konformitätsstufe A anzugeben, übergeben Sie `PDFAConformance.A`.
   * Legen Sie den Wert `PDFARevisionNumber` fest, indem Sie die `setPDFARevisionNumber` -Methode des Objekts `RenderOptionsSpec` aufrufen und `PDFARevisionNumber.Revision_1` übergeben.

   >[!NOTE]
   >
   >Die PDF-Version eines PDF/A-Dokuments ist 1.4, unabhängig davon, welchen Wert Sie für die `RenderOptionsSpec` -Methode des Objekts `setPdfVersion`*angeben.*

1. Generieren Sie ein PDF/A-Dokument.

   Erstellen Sie ein PDF/A-Dokument, indem Sie die `generatePDFOutput` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF/A-Dokument zu generieren, geben Sie `TransformationFormat.PDFA` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

   >[!NOTE]
   >
   >Die `OutputResult` -Methode des Objekts `getRecordLevelMetaDataList` gibt `null` zurück.

   >[!NOTE]
   >
   >Sie können auch ein PDF/A-Dokument erstellen, indem Sie die `generatePDFOutput`2-Methode des `OutputClient`-Objekts aufrufen. (Siehe [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das den Status der `generatePDFOutput`-Methode darstellt, indem Sie die `OutputResult`-Methode des Objekts `getStatusDoc` aufrufen.
   * Erstellen Sie ein `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document` -Objekt verwenden, das von der `getStatusDoc` -Methode zurückgegeben wurde).

   >[!NOTE]
   >
   >Obwohl der Output-Dienst das PDF/A-Dokument an den Speicherort schreibt, der durch das an die `setFileURI` -Methode des `PDFOutputOptionsSpec` -Objekts übergebene Argument angegeben wird, können Sie das PDF/A-Dokument programmgesteuert abrufen, indem Sie die `OutputResult` -Methode des Objekts `getGeneratedDoc` aufrufen.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Erstellen eines PDF/A-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-a-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Erstellen Sie ein PDF/A-Dokument mithilfe der Webdienst-API {#create-a-pdf-a-document-using-the-web-service-api}

Erstellen Sie ein PDF/A-Dokument mithilfe der Output API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Daten verwendet, die mit dem PDF/A-Dokument zusammengeführt werden.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Festlegen von PDF/A-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Datei-URI fest, indem Sie einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Output-Dienst generierten PDF-Datei an das `fileURI`-Datenelement des Objekts `PDFOutputOptionsSpec` angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, nicht zum Clientcomputer

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Wert `PDFAConformance` fest, indem Sie dem `PDFAConformance`-Datenelement des `RenderOptionsSpec`-Objekts einen `PDFAConformance`-Enum-Wert zuweisen. Um beispielsweise Konformitätsstufe A anzugeben, weisen Sie diesem Datenelement `PDFAConformance.A` zu.
   * Legen Sie den Wert `PDFARevisionNumber` fest, indem Sie dem `PDFARevisionNumber`-Datenelement des `RenderOptionsSpec`-Objekts einen `PDFARevisionNumber`-Enum-Wert zuweisen. Weisen Sie diesem Datenelement `PDFARevisionNumber.Revision_1` zu.

   >[!NOTE]
   >
   >Die PDF-Version eines PDF/A-Dokuments ist 1.4, unabhängig vom angegebenen Wert.

1. Generieren Sie ein PDF/A-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die `generatePDFOutput`Methode des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Enumerationswert TransformationFormat . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDFA` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)

   >[!NOTE]
   >
   >Sie können auch ein PDF/A-Dokument erstellen, indem Sie die `generatePDFOutput`2-Methode des `OutputClient`-Objekts aufrufen. (Siehe [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des Objekts `BLOB` speichert, das mit Ergebnisdaten aus der `OutputServiceService` -Methode des Objekts `generatePDFOutput` (dem achten Parameter) gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst {#passing-documents-located-in-content-services-deprecated-to-the-output-service}

Der Output-Dienst rendert ein nicht interaktives PDF-Formular, das auf einem Formularentwurf basiert, der normalerweise als XDP-Datei gespeichert und in Designer erstellt wird. Sie können ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält, an den Output-Dienst übergeben. Der Output-Dienst rendert dann den Formularentwurf im `com.adobe.idp.Document`-Objekt.

Ein Vorteil der Übergabe eines `com.adobe.idp.Document` -Objekts an den Output-Dienst besteht darin, dass andere AEM Forms-Dienstvorgänge eine `com.adobe.idp.Document` -Instanz zurückgeben. Das heißt, Sie können eine `com.adobe.idp.Document`-Instanz von einem anderen Dienstvorgang abrufen und rendern. Angenommen, eine XDP-Datei wird in einem Content Services-Knoten mit dem Namen `/Company Home/Form Designs` gespeichert, wie in der folgenden Abbildung dargestellt.

Sie können &quot;Loan.xdp&quot;programmgesteuert aus Content Services (nicht mehr unterstützt) abrufen und die XDP-Datei in einem `com.adobe.idp.Document`-Objekt an den Output-Dienst übergeben.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Aufgaben aus, um ein von Content Services (nicht mehr unterstützt) gespeichertes Dokument an den Output-Dienst zu übergeben:

1. Projektdateien einschließen.
1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus Content Services ab (nicht mehr unterstützt).
1. Wiedergabe des nicht interaktiven PDF-Formulars
1. Führen Sie eine Aktion mit dem Datenstrom aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen einer Ausgabe und eines Document Management Client-API-Objekts**

Bevor Sie einen Output-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Output Client-API-Objekt. Da mit diesem Workflow eine XDP-Datei aus Content Services (nicht mehr unterstützt) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)**

Rufen Sie die XDP-Datei über die Java- oder Webdienst-API von Content Services (nicht mehr unterstützt) ab. Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document`-Instanz (oder einer `BLOB`-Instanz zurückgegeben, wenn Sie Webdienste verwenden). Anschließend können Sie die `com.adobe.idp.Document`-Instanz an den Output-Dienst übergeben.

**Nicht interaktives PDF-Formular wiedergeben**

Um ein nicht interaktives Formular wiederzugeben, übergeben Sie die `com.adobe.idp.Document`-Instanz, die von Content Services (nicht mehr unterstützt) zurückgegeben wurde, an den Output-Dienst.

>[!NOTE]
>
>Zwei neue Methoden namens `generatePDFOutput2`und g `eneratePrintedOutput2`akzeptieren ein `com.adobe.idp.Document`-Objekt, das einen Formularentwurf enthält. Sie können auch einen `com.adobe.idp.Document`übergeben, der den Formularentwurf enthält, wenn Sie einen Druckstream an einen Netzwerkdrucker senden.

**Ausführen einer Aktion mit dem Formulardatenstream**

Sie können das nicht interaktive Formular als PDF-Datei speichern. Das Formular kann in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-java-api)

[Übergeben von Dokumenten an den Output-Dienst mithilfe der Webdienst-API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Erstellen von PDF-Dokumenten mit Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

### Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API {#pass-documents-to-the-output-service-using-the-java-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) mithilfe der Output-Dienst- und Content Services-API (nicht mehr unterstützt) abgerufen wurde:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar und adobe-contentservices-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den Formularentwurf aus Content Services ab (nicht mehr unterstützt).

   Rufen Sie die `retrieveContent` -Methode des Objekts `DocumentManagementServiceClientImpl` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.

   Die `retrieveContent`-Methode gibt ein `CRCResult`-Objekt zurück, das die XDP-Datei enthält. Rufen Sie eine `com.adobe.idp.Document` -Instanz ab, indem Sie die `getDocument` -Methode des Objekts `CRCResult` aufrufen.

1. Wiedergabe des nicht interaktiven PDF-Formulars

   Rufen Sie die `generatePDFOutput2` -Methode des Objekts `OutputClient` auf und übergeben Sie die folgenden Werte:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden.
   * Ein `com.adobe.idp.Document` -Objekt, das den Formularentwurf darstellt (verwenden Sie die von der `CRCResult` -Methode des Objekts `getDocument` zurückgegebene Instanz).
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput2`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

   * Rufen Sie ein `com.adobe.idp.Document` -Objekt ab, das das nicht interaktive Formular darstellt, indem Sie die `getGeneratedDoc` -Methode des Objekts `OutputResult` aufrufen.
   * Erstellen Sie ein `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document` -Objekt verwenden, das von der `getGeneratedDoc` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Übergeben von Dokumenten an den Output-Dienst mithilfe der Webdienst-API {#pass-documents-to-the-output-service-using-the-web-service-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) mithilfe der Output-Dienst- und Content Services-API (nicht mehr unterstützt) abgerufen wurde (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da diese Client-Anwendung zwei AEM Forms-Dienste aufruft, erstellen Sie zwei Dienstverweise. Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Output-Dienst verknüpft ist: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Document Management-Dienst verknüpft ist: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Da der Datentyp `BLOB` für beide Dienstverweise gleich ist, müssen Sie den Datentyp `BLOB` bei Verwendung vollständig qualifizieren. Im entsprechenden Webdienst-Schnellstart sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den Service-Client `DocumentManagementServiceClient`.

1. Rufen Sie den Formularentwurf aus Content Services ab (nicht mehr unterstützt).

   Rufen Sie Inhalte ab, indem Sie die `retrieveContent` -Methode des Objekts `DocumentManagementServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   * Ein string -Ausgabeparameter, der den Wert des Durchsuchen-Links speichert.
   * Ein `BLOB`-Ausgabeparameter, der den Inhalt speichert. Sie können diesen Ausgabeparameter verwenden, um den Inhalt abzurufen.
   * Ein `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType`-Ausgabeparameter, der Inhaltsattribute speichert.
   * Ein `CRCResult`-Ausgabeparameter. Statt dieses Objekt zu verwenden, können Sie den Ausgabeparameter `BLOB` verwenden, um den Inhalt abzurufen.

1. Wiedergabe des nicht interaktiven PDF-Formulars

   Rufen Sie die `generatePDFOutput2` -Methode des Objekts `OutputServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden.
   * Ein `BLOB` -Objekt, das den Formularentwurf darstellt (verwenden Sie die `BLOB`-Instanz, die von Content Services zurückgegeben wird (veraltet)).
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein output `BLOB` -Objekt, das von der `generatePDFOutput2` -Methode aufgefüllt wird. Die `generatePDFOutput2`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein output `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

   Die `generatePDFOutput2`-Methode gibt ein `BLOB`-Objekt zurück, das das nicht interaktive PDF-Formular enthält.

1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert für den Dateispeicherort des interaktiven PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `generatePDFOutput2` -Methode abgerufen wird. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Übergeben von Dokumenten im Repository an den Output-Dienst {#passing-documents-located-in-the-repository-to-the-output-service}

Der Output-Dienst rendert ein nicht interaktives PDF-Formular, das auf einem Formularentwurf basiert, der normalerweise als XDP-Datei gespeichert und in Designer erstellt wird. Sie können ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf enthält, an den Output-Dienst übergeben. Der Output-Dienst rendert dann den Formularentwurf im `com.adobe.idp.Document`-Objekt.

Ein Vorteil der Übergabe eines `com.adobe.idp.Document` -Objekts an den Output-Dienst besteht darin, dass andere AEM Forms-Dienstvorgänge eine `com.adobe.idp.Document` -Instanz zurückgeben. Das heißt, Sie können eine `com.adobe.idp.Document`-Instanz von einem anderen Dienstvorgang abrufen und rendern. Angenommen, eine XDP-Datei wird im AEM Forms-Repository gespeichert, wie in der folgenden Abbildung dargestellt.

![pd_pd_formrepository](assets/pd_pd_formrepository.png)

Der Ordner *FormsFolder* ist ein benutzerdefinierter Speicherort im AEM Forms-Repository (dieser Speicherort ist ein Beispiel und ist standardmäßig nicht vorhanden). In diesem Beispiel befindet sich ein Formularentwurf namens &quot;Loan.xdp&quot;in diesem Ordner. Neben dem Formularentwurf können auch andere Formularkomponenten wie Bilder an dieser Stelle gespeichert werden. Der Pfad zu einer Ressource im AEM Forms-Repository lautet:

`Applications/Application-name/Application-version/Folder.../Filename`

Sie können Loan.xdp programmgesteuert aus dem AEM Forms-Repository abrufen und an den Output-Dienst innerhalb eines `com.adobe.idp.Document`-Objekts übergeben.

Sie können eine PDF-Datei basierend auf einer XDP-Datei im Repository auf zwei Arten erstellen. Sie können den XDP-Speicherort als Referenz übergeben oder Sie können die XDP programmgesteuert aus dem Repository abrufen und an den Output-Dienst in einer XDP-Datei übergeben.

[Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments basierend auf einer Anwendungs-XDP-Datei mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api)  (zeigt, wie der Speicherort der XDP-Datei als Referenz übergeben wird).

[Schnellstart (EJB-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api)  (zeigt, wie die XDP-Datei programmgesteuert aus dem AEM Forms-Repository abgerufen und in einer  `com.adobe.idp.Document` Instanz an den Output-Dienst übergeben wird). (In diesem Abschnitt wird beschrieben, wie Sie diese Aufgabe durchführen.)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

Führen Sie die folgenden Aufgaben aus, um ein vom AEM Forms-Repository abgerufenes Dokument an den Output-Dienst zu übergeben:

1. Projektdateien einschließen.
1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus dem AEM Forms-Repository ab.
1. Wiedergabe des nicht interaktiven PDF-Formulars
1. Führen Sie eine Aktion mit dem Datenstrom aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen einer Ausgabe und eines Document Management Client-API-Objekts**

Bevor Sie einen Output-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Output Client-API-Objekt. Da mit diesem Workflow eine XDP-Datei aus Content Services (nicht mehr unterstützt) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus dem AEM Forms-Repository**

Rufen Sie die XDP-Datei mithilfe der Repository-API aus dem AEM Forms-Repository ab. (Siehe [Lesen von Ressourcen](/help/forms/developing/aem-forms-repository.md#reading-resources).)

Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document`-Instanz (oder einer `BLOB`-Instanz zurückgegeben, wenn Sie Webdienste verwenden). Anschließend können Sie die `com.adobe.idp.Document`-Instanz an den Output-Dienst übergeben.

**Nicht interaktives PDF-Formular wiedergeben**

Um ein nicht interaktives Formular wiederzugeben, übergeben Sie die `com.adobe.idp.Document`-Instanz, die mit der AEM Forms Repository-API zurückgegeben wurde.

>[!NOTE]
>
>Zwei neue Methoden namens `generatePDFOutput2`und `generatePrintedOutput2`akzeptieren ein `com.adobe.idp.Document`Objekt, das einen Formularentwurf enthält. Sie können beim Senden eines Druckstreams an einen Netzwerkdrucker auch ein `com.adobe.idp.Document` übergeben, das den Formularentwurf enthält.

**Ausführen einer Aktion mit dem Formulardatenstream**

Sie können das nicht interaktive Formular als PDF-Datei speichern. Das Formular kann in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Übergeben von Dokumenten im Repository an den Output-Dienst mithilfe der Java-API](creating-document-output-streams.md#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

ResourceRepositoryClient

### Übergeben von Dokumenten im Repository an den Output-Dienst mithilfe der Java-API {#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api}

Übergeben Sie ein aus dem Repository abgerufenes Dokument mithilfe des Output-Dienstes und der Repository-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar und adobe-repository-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den Formularentwurf aus dem AEM Forms-Repository ab.

   Rufen Sie die `readResourceContent` -Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den URI-Speicherort an die XDP-Datei angibt. `ResourceRepositoryClient` Beispiel: `/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`. Dieser Wert ist ein Pflichtwert. Diese Methode gibt eine `com.adobe.idp.Document` -Instanz zurück, die die XDP-Datei darstellt.

1. Wiedergabe des nicht interaktiven PDF-Formulars

   Rufen Sie die `generatePDFOutput2` -Methode des Objekts `OutputClient` auf und übergeben Sie die folgenden Werte:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden. Beispiel: `repository:///Applications/FormsApplication/1.0/FormsFolder/`.
   * Ein `com.adobe.idp.Document` -Objekt, das den Formularentwurf darstellt (verwenden Sie die von der `ResourceRepositoryClient` -Methode des Objekts `readResourceContent` zurückgegebene Instanz).
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput2`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

   * Rufen Sie ein `com.adobe.idp.Document` -Objekt ab, das das nicht interaktive Formular darstellt, indem Sie die `getGeneratedDoc` -Methode des Objekts `OutputResult` aufrufen.
   * Erstellen Sie ein `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document` -Objekt verwenden, das von der `getGeneratedDoc` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Erstellen von PDF-Dokumenten mit Fragmenten {#creating-pdf-documents-using-fragments}

Sie können die Output- und Assembler-Dienste verwenden, um einen Ausgabestream, z. B. ein PDF-Dokument, zu erstellen, der auf Fragmenten basiert. Der Assembler-Dienst stellt ein XDP-Dokument zusammen, das auf Fragmenten in mehreren XDP-Dateien basiert. Das assemblierte XDP-Dokument wird an den Output-Dienst übergeben, der ein PDF-Dokument erstellt. Obwohl dieser Workflow zeigt, dass ein PDF-Dokument generiert wird, kann der Output-Dienst für diesen Workflow andere Ausgabetypen wie ZPL generieren. Ein PDF-Dokument dient nur zu Diskussionszwecken.

Die folgende Abbildung zeigt diesen Workflow.

![cp_cp_outputassemblefragments](assets/cp_cp_outputassemblefragments.png)

Bevor Sie *PDF-Dokumente mit Fragmenten erstellen* lesen, sollten Sie sich mit der Verwendung des Assembler-Dienstes für das Zusammenführen mehrerer XDP-Dokumente vertraut machen. (Siehe [Assemblieren mehrerer XDP-Fragmente](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments).)

>[!NOTE]
>
>Sie können auch einen vom Assembler-Dienst zusammengestellten Formularentwurf an den Forms-Dienst anstelle des Output-Dienstes übergeben. Der Hauptunterschied zwischen dem Output-Dienst und dem Forms-Dienst besteht darin, dass der Forms-Dienst interaktive PDF-Dokumente generiert und der Output-Dienst nicht interaktive PDF-Dokumente erzeugt. Außerdem kann der Forms-Dienst keine druckerbasierten Ausgabestreams wie ZPL generieren.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Um ein auf Fragmenten basierendes PDF-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output- und Assembler-Client-Objekt.
1. Verwenden Sie den Assembler-Dienst, um den Formularentwurf zu generieren.
1. Verwenden Sie den Output-Dienst, um das PDF-Dokument zu generieren.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Output- und Assembler-Client-Objekts**

Bevor Sie einen Output-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Output Client-API-Objekt. Da dieser Workflow den Assembler-Dienst aufruft, um den Formularentwurf zu erstellen, erstellen Sie außerdem ein Assembler-Client-API-Objekt.

**Verwenden des Assembler-Dienstes zum Generieren des Formularentwurfs**

Verwenden Sie den Assembler-Dienst, um den Formularentwurf mithilfe von Fragmenten zu generieren. Der Assembler-Dienst gibt eine `com.adobe.idp.Document`-Instanz zurück, die den Formularentwurf enthält.

**Verwenden des Output-Dienstes zum Generieren des PDF-Dokuments**

Sie können den Output-Dienst verwenden, um ein PDF-Dokument mit dem Formularentwurf zu generieren, den der Assembler-Dienst erstellt hat. Übergeben Sie die `com.adobe.idp.Document`-Instanz, die der Assembler-Dienst an den Output-Dienst zurückgegeben hat.

**PDF-Dokument als PDF-Datei speichern**

Nachdem der Output-Dienst ein PDF-Dokument generiert hat, können Sie es als PDF-Datei speichern.

**Siehe auch**

[Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-java-api)

[Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Webdienst-API](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Assemblieren mehrerer XDP-Fragmente](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments)

[Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)

### Erstellen eines auf Fragmenten basierenden PDF-Dokuments mithilfe der Java-API {#create-a-pdf-document-based-on-fragments-using-the-java-api}

Erstellen Sie ein PDF-Dokument basierend auf Fragmenten mithilfe der Output Service-API und der Assembler-Dienst-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output- und Assembler-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.
   * Erstellen Sie ein `AssemblerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Verwenden Sie den Assembler-Dienst, um den Formularentwurf zu generieren.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das zu verwendende DX-Dokument darstellt.
   * Ein `java.util.Map` -Objekt, das die XDP-Eingabedateien enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschriftart und der Auftragsprotokollebene.

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das das assemblierte XDP-Dokument enthält. Um das assemblierte XDP-Dokument abzurufen, führen Sie die folgenden Aktionen aus:

   * Rufen Sie die `getDocuments` -Methode des Objekts `AssemblerResult` auf. Diese Methode gibt ein `java.util.Map` -Objekt zurück.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf, um das assemblierte XDP-Dokument zu extrahieren.


1. Verwenden Sie den Output-Dienst, um das PDF-Dokument zu generieren.

   Rufen Sie die `generatePDFOutput2` -Methode des Objekts `OutputClient` auf und übergeben Sie die folgenden Werte:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen (z. B. Bilder) befinden
   * Ein `com.adobe.idp.Document` -Objekt, das den Formularentwurf darstellt (verwenden Sie die vom Assembler-Dienst zurückgegebene Instanz)
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen

   Die `generatePDFOutput2`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält

1. Speichern Sie das PDF-Dokument als PDF-Datei.

   * Rufen Sie ein `com.adobe.idp.Document` -Objekt ab, das das PDF-Dokument darstellt, indem Sie die `getGeneratedDoc` -Methode des Objekts `OutputResult` aufrufen.
   * Erstellen Sie ein `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren. (Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `getGeneratedDoc`-Methode zurückgegeben wurde.)

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Webdienst-API {#create-a-pdf-document-based-on-fragments-using-the-web-service-api}

Erstellen Sie ein PDF-Dokument basierend auf Fragmenten mithilfe der Output Service-API und der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Output-Dienst verknüpft ist:

   ```java
    http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1.
   ```

   Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Assembler-Dienst verknüpft ist:

   ```java
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   Da der Datentyp `BLOB` für beide Dienstverweise gleich ist, müssen Sie den Datentyp `BLOB` bei Verwendung vollständig qualifizieren. Im entsprechenden Webdienst-Schnellstart sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output- und Assembler-Client-Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName`den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password`den entsprechenden Kennwortwert zu.
      * Weisen Sie den Konstantenwert `HttpClientCredentialType.Basic` dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`zu.
   * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode`zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für das `AssemblerServiceClient`Objekt.

1. Verwenden Sie den Assembler-Dienst, um den Formularentwurf zu generieren.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält. Um das neu erstellte XDP-Dokument abzurufen, führen Sie die folgenden Aktionen aus:

   * Greifen Sie auf das `AssemblerResult`-Feld des Objekts `documents` zu, bei dem es sich um ein `Map`-Objekt handelt, das die resultierenden PDF-Dokumente enthält.
   * Durchsuchen Sie das `Map`-Objekt, um den assemblierten Formularentwurf abzurufen. Wandeln Sie die `value` des Array-Mitglieds in `BLOB` um. Übergeben Sie diese `BLOB`-Instanz an den Output-Dienst.


1. Verwenden Sie den Output-Dienst, um das PDF-Dokument zu generieren.

   Rufen Sie die `generatePDFOutput2` -Methode des Objekts `OutputServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen (z. B. Bilder) befinden.
   * Ein `BLOB` -Objekt, das den Formularentwurf darstellt (verwenden Sie die vom Assembler-Dienst zurückgegebene `BLOB`-Instanz).
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein Output `BLOB` -Objekt, das von der `generatePDFOutput2` -Methode ausgefüllt wird. Die `generatePDFOutput2`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein output `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

   Die `generatePDFOutput2`-Methode gibt ein `BLOB`-Objekt zurück, das das nicht interaktive PDF-Formular enthält.

1. Speichern Sie das PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert für den Dateispeicherort des interaktiven PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `generatePDFOutput2` -Methode abgerufen wird. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Drucken in Dateien {#printing-to-files}

Mit dem Output-Dienst können Sie Streams wie PostScript, Printer Control Language (PCL) oder die folgenden Beschriftungsformate in eine Datei drucken:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Mit dem Output-Dienst können Sie XML-Daten mit einem Formularentwurf zusammenführen und das Formular in eine Datei drucken. Die folgende Abbildung zeigt den Output-Dienst zum Erstellen von Laser- und Beschriftungsdateien.

>[!NOTE]
>
>Informationen zum Senden von Druckstreams an Drucker finden Sie unter [Senden von Druckströmen an Drucker](creating-document-output-streams.md#sending-print-streams-to-printers).

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Führen Sie die folgenden Schritte aus, um in eine Datei zu drucken:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Legen Sie die zum Drucken in eine Datei erforderlichen Drucklaufzeitoptionen fest.
1. Drucken Sie den Druckdatenstrom in eine Datei.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. (Siehe [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Referenzieren einer XML-Datenquelle**

Zum Drucken eines Dokuments, das Daten enthält, müssen Sie eine XML-Datenquelle referenzieren, die XML-Elemente für jedes Formularfeld enthält, das mit Daten gefüllt werden soll. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

**Festlegen der zum Drucken in einer Datei erforderlichen Drucklaufzeitoptionen**

Um in eine Datei zu drucken, müssen Sie die Laufzeitoption Datei-URI festlegen, indem Sie den Speicherort und den Namen der Datei angeben, in die der Output-Dienst druckt. Um beispielsweise den Output-Dienst anzuweisen, eine PostScript-Datei mit dem Namen *MortgageForm.ps* zu C:\Adobe zu drucken, geben Sie C:\Adobe\MortgageForm.ps an.

>[!NOTE]
>
>Es gibt optionale Laufzeitoptionen, die Sie definieren können. Informationen zu allen Optionen, die Sie festlegen können, finden Sie in der `PrintedOutputOptionsSpec`-Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Druckdatenstrom in eine Datei drucken**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die Formulardaten enthält, und Drucklaufzeitoptionen festgelegt haben, können Sie den Output-Dienst aufrufen, wodurch eine Datei gedruckt wird.

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, werden verschiedene Datenelemente wie XML-Daten zurückgegeben, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Drucken in Dateien mithilfe der Java-API](creating-document-output-streams.md#print-to-files-using-the-java-api)

[Drucken in Dateien mithilfe der Webdienst-API](creating-document-output-streams.md#print-to-files-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Drucken in Dateien mit der Java-API {#print-to-files-using-the-java-api}

Drucken Sie mit der Output API (Java) in eine Datei:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-output-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des Dokuments mithilfe des zugehörigen Konstruktors verwendet wird, und übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie die zum Drucken in eine Datei erforderlichen Drucklaufzeitoptionen fest.

   * Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die Datei an, indem Sie die `setFileURI`-Methode des PrintedOutputOptionsSpec-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen und den Speicherort der Datei darstellt. Wenn Sie beispielsweise möchten, dass der Output-Dienst in eine PostScript-Datei namens MortgageForm.ps unter C:\Adobe druckt, geben Sie C:\\Adobe\MortgageForm.ps an.
   * Geben Sie die Anzahl der zu druckenden Kopien an, indem Sie die `setCopies`-Methode des Objekts `PrintedOutputOptionsSpec` aufrufen und einen ganzzahligen Wert übergeben, der die Anzahl der Exemplare darstellt.

1. Drucken Sie den Druckdatenstrom in eine Datei.

   Drucken Sie in eine Datei, indem Sie die `generatePrintedOutput` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein `PrintFormat`-Auflistungswert, der das zu erstellende Druckstream-Format angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Speicherort zugehöriger Begleitdateien wie Bilddateien angibt.
   * Ein string -Wert, der den Speicherort der zu verwendenden XDC-Datei angibt (Sie können `null` übergeben, wenn Sie die zu verwendende XDC-Datei mit dem `PrintedOutputOptionsSpec`-Objekt angegeben haben).
   * Das `PrintedOutputOptionsSpec`-Objekt, das Laufzeitoptionen enthält, die zum Drucken in eine Datei erforderlich sind.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Formulardaten enthält.

   Die `generatePrintedOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

   >[!NOTE]
   >
   >Die `OutputResult` -Methode des Objekts `getRecordLevelMetaDataList` gibt `null` zurück.

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das den Status der `generatePrintedOutput`-Methode darstellt, indem Sie die `OutputResult`-Methode des Objekts `getStatusDoc` aufrufen (das `OutputResult`-Objekt wurde von der `generatePrintedOutput`-Methode zurückgegeben).
   * Erstellen Sie ein `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document` -Objekt verwenden, das von der `getStatusDoc` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Drucken in einer Datei mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-printing-to-a-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Drucken in Dateien mithilfe der Webdienst-API {#print-to-files-using-the-web-service-api}

Drucken Sie mit der Output API (Webdienst) in eine Datei:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Formulardaten verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Speicherort der XML-Datei angibt, die Formulardaten enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `binaryData`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie die zum Drucken in eine Datei erforderlichen Drucklaufzeitoptionen fest.

   * Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die Datei an, indem Sie dem `fileURI` -Datenelement des Objekts `PrintedOutputOptionsSpec` einen Zeichenfolgenwert zuweisen, der den Speicherort und den Namen der Datei darstellt. Wenn Sie beispielsweise möchten, dass der Output-Dienst in eine PostScript-Datei mit dem Namen *MortgageForm.ps* unter C:\Adobe druckt, geben Sie C:\\Adobe\MortgageForm.ps an.
   * Geben Sie die Anzahl der zu druckenden Kopien an, indem Sie den `copies`-Datenelementen des Objekts `PrintedOutputOptionsSpec` einen ganzzahligen Wert zuweisen, der die Anzahl der Exemplare darstellt.

1. Drucken Sie den Druckdatenstrom in eine Datei.

   Drucken Sie in eine Datei, indem Sie die `generatePrintedOutput` -Methode des Objekts `OutputServiceService` aufrufen und die folgenden Werte übergeben:

   * Ein `PrintFormat`-Auflistungswert, der das zu erstellende Druckstream-Format angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Speicherort zugehöriger Begleitdateien wie Bilddateien angibt.
   * Ein string -Wert, der den Speicherort der zu verwendenden XDC-Datei angibt (Sie können `null` übergeben, wenn Sie die zu verwendende XDC-Datei mit dem `PrintedOutputOptionsSpec`-Objekt angegeben haben).
   * Das `PrintedOutputOptionsSpec`-Objekt, das zum Drucken in eine Datei erforderliche Drucklaufzeitoptionen enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Formulardaten enthält.
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des Objekts `BLOB` speichert, das mit Ergebnisdaten aus der `OutputServiceService` -Methode des Objekts `generatePDFOutput` (dem achten Parameter) gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Senden von Druckströmen an Drucker {#sending-print-streams-to-printers}

Sie können den Output-Dienst verwenden, um Druckstreams wie PostScript, Printer Control Language (PCL) oder die folgenden Beschriftungsformate an Netzwerkdrucker zu senden:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Mit dem Output-Dienst können Sie XML-Daten mit einem Formularentwurf zusammenführen und das Formular als Druckstream ausgeben. Sie können beispielsweise einen PostScript-Druckstream erstellen und an einen Netzwerkdrucker senden. Die folgende Abbildung zeigt den Output-Dienst, der Druckstreams an Netzwerkdrucker sendet.

>[!NOTE]
>
>Um zu demonstrieren, wie ein Druckstrom an einen Netzwerkdrucker gesendet wird, sendet dieser Abschnitt einen PostScript-Druckstrom mithilfe des SharedPrinter-Druckerprotokolls an einen Netzwerkdrucker.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

So senden Sie einen Druckstream an einen Netzwerkdrucker:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Festlegen von Drucklaufzeitoptionen
1. Abrufen eines zu druckenden Dokuments.
1. Senden Sie das Dokument an einen Netzwerkdrucker.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, erstellen Sie ein Output-Dienst-Client-Objekt. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie ein `OutputServiceClient`-Objekt.

**Referenzieren einer XML-Datenquelle**

Zum Drucken eines Dokuments, das Daten enthält, müssen Sie eine XML-Datenquelle referenzieren, die XML-Elemente für jedes Formularfeld enthält, das mit Daten gefüllt werden soll. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

**Festlegen von Drucklaufzeitoptionen**

Sie können die Laufzeitoptionen beim Senden eines Druckstreams an einen Drucker festlegen, einschließlich der folgenden Optionen:

* **Kopien**: Gibt die Anzahl der an den Drucker zu sendenden Kopien an. Der Standardwert ist 1.
* **Staple**: Eine XCI-Option wird festgelegt, wenn ein Hefter verwendet wird. Diese Option kann im Konfigurationsmodell durch das Heftelement angegeben werden und wird nur für PS- und PCL-Drucker verwendet.
* **OutputJog**: Eine XCI-Option wird festgelegt, wenn Ausgabeseiten gejoggt werden sollen (physisch in der Ausgabenablage verschoben). Diese Option ist nur für PS- und PCL-Drucker verfügbar.
* **OutputBin**: XCI-Wert, der verwendet wird, um dem Druckertreiber die Auswahl der entsprechenden Ausgabenablage zu ermöglichen.

>[!NOTE]
>
>Informationen zu allen Laufzeitoptionen, die Sie festlegen können, finden Sie in der `PrintedOutputOptionsSpec`-Klassenreferenz.

**Abrufen eines zu druckenden Dokuments**

Rufen Sie einen Druckstream ab, der an einen Drucker gesendet werden soll. Sie können beispielsweise eine PostScript-Datei abrufen und an einen Drucker senden.

Sie können eine PDF-Datei senden, wenn Ihr Drucker PDF unterstützt. Ein Problem beim Senden eines PDF-Dokuments an einen Drucker besteht jedoch darin, dass jeder Druckerhersteller über eine andere Implementierung des PDF-Interpreters verfügt. Das heißt, einige Druckereien verwenden die Adobe PDF-Interpretation, aber es hängt vom Drucker ab. Andere Drucker haben einen eigenen PDF-Interpreter. Daher können die Druckergebnisse variieren.

Eine weitere Einschränkung beim Senden eines PDF-Dokuments an einen Drucker besteht darin, dass es nur gedruckt wird. Es kann nicht auf Duplex, Papierfachauswahl und Stapeln zugreifen, außer durch Einstellungen am Drucker.

Um ein zu druckendes Dokument abzurufen, verwenden Sie die `generatePrintedOutput`-Methode. In der folgenden Tabelle sind die Inhaltstypen aufgeführt, die für einen bestimmten Druckstream festgelegt werden, wenn die `generatePrintedOutput`-Methode verwendet wird.

<table>
 <thead>
  <tr>
   <th><p>Druckformat </p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>DPL </p></td>
   <td><p>Erstellt einen standardmäßigen oder benutzerdefinierten xdc-Ausgabestream dpl203.xdc.</p></td>
  </tr>
  <tr>
   <td><p>DPL300DPI </p></td>
   <td><p>Erstellt einen DPL-Ausgabe-Stream mit 300 DPI.</p></td>
  </tr>
  <tr>
   <td><p>DPL406DPI </p></td>
   <td><p>Erstellt einen DPL-Ausgabe-Stream mit 400 DPI.</p></td>
  </tr>
  <tr>
   <td><p>DPL600DPI </p></td>
   <td><p>Erstellt einen DPL-Ausgabe-Stream mit 600 DPI.</p></td>
  </tr>
  <tr>
   <td><p>GenericColorPCL </p></td>
   <td><p>Erstellt einen generischen Farb-PCL (5c)-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>GenericPSLevel3 </p></td>
   <td><p>Erstellt einen generischen PostScript Level 3-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>IPL </p></td>
   <td><p>Erstellt einen benutzerdefinierten IPL-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>IPL 300 DPI </p></td>
   <td><p>Erstellt einen IPL-Ausgabe-Stream mit 300 DPI.</p></td>
  </tr>
  <tr>
   <td><p>IPL 400 DPI </p></td>
   <td><p>Erstellt einen IPL-Ausgabe-Stream mit 400 DPI.</p></td>
  </tr>
  <tr>
   <td><p>PCL </p></td>
   <td><p>Erstellt einen generischen monochrome PCL (5e)-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>PostScript </p></td>
   <td><p>Erstellt einen generischen PostScript Level 2-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>TPCL </p></td>
   <td><p>Erstellt einen benutzerdefinierten TPCL-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>TPCL305DPI </p></td>
   <td><p>Erstellt einen TPCL 305-DPI-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>TPCL600DPI </p></td>
   <td><p>Erstellt einen TPCL-Ausgabe-Stream mit 600 DPI.</p></td>
  </tr>
  <tr>
   <td><p>ZPL </p></td>
   <td><p>Erstellt einen ZPL-Ausgabe-Stream mit 203 DPI.</p></td>
  </tr>
  <tr>
   <td><p>ZPL 300 DPI </p></td>
   <td><p>Erstellt einen ZPL-Ausgabestream mit 300 DPI.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Sie können auch einen Druckstream mit der `generatePrintedOutput2`-Methode an einen Drucker senden. Die Schnellstarts, die mit dem Abschnitt Senden von Druckstreams an Drucker verknüpft sind, verwenden jedoch die Methode `generatePrintedOutput` .

**Senden Sie den Druckstrom an einen Netzwerkdrucker.**

Nachdem Sie ein zu druckendes Dokument abgerufen haben, können Sie den Output-Dienst aufrufen, wodurch ein Druckstream an einen Netzwerkdrucker gesendet wird. Damit der Output-Dienst den Drucker erfolgreich finden kann, müssen Sie sowohl den Druckserver als auch den Druckernamen angeben. Darüber hinaus müssen Sie auch das Druckprotokoll angeben.

>[!NOTE]
>
>Wenn PDFG auf dem Formularserver installiert ist und der Server unter Windows Server 2008 ausgeführt wird, können Sie die SharedPrinter-Eigenschaft nicht verwenden. Verwenden Sie in diesem Fall ein anderes Druckerprotokoll.

>[!NOTE]
>
>Wenn Sie einen Netzwerkdrucker verwenden und der Zugriffsmechanismus SharedPrinter lautet, müssen Sie den vollständigen Netzwerkpfad des Druckers angeben. Senden Sie einen Druckstrom mithilfe der Java-API an einen Netzwerkdrucker.

Senden Sie mithilfe der Output API (Java) einen Druckstream an einen Netzwerkdrucker:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-output-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Output Client-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren einer XML-Datenquelle

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des Dokuments mithilfe des zugehörigen Konstruktors verwendet wird, und übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Drucklaufzeitoptionen

   Erstellen Sie ein `PrintedOutputOptionsSpec`-Objekt, das die Optionen für die Drucklaufzeit darstellt. Sie können beispielsweise die Anzahl der zu druckenden Kopien angeben, indem Sie die `setCopies` -Methode des Objekts `PrintedOutputOptionsSpec` aufrufen.

   >[!NOTE]
   >
   >Sie können den Paginierungswert nicht mithilfe der `PrintedOutputOptionsSpec` -Methode des Objekts `setPagination` festlegen, wenn Sie einen ZPL-Druckstream generieren. Ebenso können Sie die folgenden Optionen für einen ZPL-Druckstream nicht festlegen: OutputJog, PageOffset und Staple. Die `setPagination`-Methode ist für die PostScript-Generierung nicht gültig. Sie gilt nur für die PCL-Generierung.

1. Abrufen eines zu druckenden Dokuments

   * Rufen Sie ein zu druckendes Dokument ab, indem Sie die `generatePrintedOutput` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

      * Ein `PrintFormat`-Auflistungswert, der den Druckstrom angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
      * Ein string-Wert, der den Namen des Formularentwurfs angibt.
      * Ein string -Wert, der den Speicherort zugehöriger Begleitdateien (z. B. Bilddateien) angibt.
      * Ein string -Wert, der den Speicherort der zu verwendenden XDC-Datei angibt.
      * Das `PrintedOutputOptionsSpec`-Objekt, das Laufzeitoptionen enthält, die zum Drucken in eine Datei erforderlich sind.
      * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle darstellt, die Formulardaten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

      Diese Methode gibt ein `OutputResult` -Objekt zurück, das die Ergebnisse des Vorgangs enthält.

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das an den Drucker gesendet werden soll, indem Sie die `OutputResult` -Methode des Objekts `getGeneratedDoc` aufrufen. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück.


1. Senden Sie den Druckstrom an einen Netzwerkdrucker.

   Senden Sie den Druckstrom an einen Netzwerkdrucker, indem Sie die `sendToPrinter` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` -Objekt, das den an den Drucker zu sendenden Druckstrom darstellt.
   * Ein `PrinterProtocol`-Auflistungswert, der das zu verwendende Druckerprotokoll angibt. Um beispielsweise das SharedPrinter-Protokoll anzugeben, übergeben Sie `PrinterProtocol.SharedPrinter`.
   * Ein string -Wert, der den Namen des Druckservers angibt. Wenn der Name des Druckservers beispielsweise PrintServer1 lautet, übergeben Sie `\\\PrintSever1`.
   * Ein string -Wert, der den Namen des Druckers angibt. Wenn beispielsweise der Name des Druckers Printer1 lautet, übergeben Sie `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >Die `sendToPrinter`-Methode wurde der AEM Forms-API in Version 8.2.1 hinzugefügt.

### Druckdatenstrom über die Webdienst-API {#send-a-print-stream-to-a-printer-using-the-web-service-api} an einen Drucker senden

Senden Sie mithilfe der Output-API (Webdienst) einen Druckdatenstrom an einen Netzwerkdrucker:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Formulardaten verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt, die Formulardaten enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Bestimmen Sie die Byte-Array-Länge, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Drucklaufzeitoptionen.

   Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden. Sie können beispielsweise die Anzahl der zu druckenden Kopien angeben, indem Sie dem `copies`-Datenelement des Objekts `PrintedOutputOptionsSpec` einen ganzzahligen Wert zuweisen, der die Anzahl der Exemplare darstellt.

   >[!NOTE]
   >
   >Sie können den Paginierungswert nicht mithilfe des `PrintedOutputOptionsSpec` -Datenelements des Objekts `pagination` festlegen, wenn Sie einen ZPL-Druckstream generieren. Ebenso können Sie die folgenden Optionen für einen ZPL-Druckstream nicht festlegen: OutputJog, PageOffset und Staple. Das `pagination`-Datenelement ist für die PostScript-Generierung nicht gültig. Sie gilt nur für die PCL-Generierung.

1. Abrufen eines zu druckenden Dokuments.

   * Rufen Sie ein zu druckendes Dokument ab, indem Sie die `generatePrintedOutput` -Methode des Objekts `OutputServiceService` aufrufen und die folgenden Werte übergeben:

      * Ein `PrintFormat`-Auflistungswert, der den Druckstrom angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
      * Ein string-Wert, der den Namen des Formularentwurfs angibt.
      * Ein string -Wert, der den Speicherort zugehöriger Begleitdateien (z. B. Bilddateien) angibt.
      * Ein string -Wert, der den Speicherort der zu verwendenden XDC-Datei angibt.
      * Das `PrintedOutputOptionsSpec`-Objekt, das Drucklaufzeitoptionen enthält, die beim Senden eines Druckstreams an einen Netzwerkdrucker verwendet werden.
      * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Formulardaten enthält.
      * Ein `BLOB` -Objekt, das von der `generatePrintedOutput` -Methode gefüllt wird. Die `generatePrintedOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
      * Ein `BLOB` -Objekt, das von der `generatePrintedOutput` -Methode gefüllt wird. Die `generatePrintedOutput`-Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
      * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Erstellen Sie ein `BLOB` -Objekt, das an den Drucker gesendet werden soll, indem Sie den Wert der `OutputResult` -Methode des Objekts `generatedDoc` abrufen. Diese Methode gibt ein `BLOB` -Objekt zurück, das PostScript-Daten enthält, die von der `generatePrintedOutput` -Methode zurückgegeben werden.


1. Senden Sie den Druckstrom an einen Netzwerkdrucker.

   Senden Sie den Druckstrom an einen Netzwerkdrucker, indem Sie die `sendToPrinter` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB` -Objekt, das den an den Drucker zu sendenden Druckstrom darstellt.
   * Ein `PrinterProtocol`-Auflistungswert, der das zu verwendende Druckerprotokoll angibt. Um beispielsweise das SharedPrinter-Protokoll anzugeben, übergeben Sie `PrinterProtocol.SharedPrinter`.
   * Ein `bool` -Wert, der angibt, ob der vorherige Parameterwert verwendet werden soll. Übergeben Sie den Wert `true`. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Ein string -Wert, der den Namen des Druckservers angibt. Wenn beispielsweise der Name des Druckservers PrintServer1 lautet, übergeben Sie `\\\PrintSever1`.
   * Ein string -Wert, der den Namen des Druckers angibt. Wenn beispielsweise der Name des Druckers Printer1 lautet, übergeben Sie `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >Die `sendToPrinter`-Methode wurde der AEM Forms-API in Version 8.2.1 hinzugefügt.

## Erstellen mehrerer Ausgabedateien {#creating-multiple-output-files}

Der Output-Dienst kann für jeden Datensatz in einer XML-Datenquelle oder in einer Datei, die alle Datensätze enthält, separate Dokumente erstellen (diese Funktion ist die Standardfunktion). Angenommen, zehn Datensätze befinden sich in einer XML-Datenquelle, und Sie weisen den Output-Dienst an, mithilfe der Output Service-API für jeden Datensatz separate PDF-Dokumente (oder andere Ausgabetypen) zu erstellen. Daher generiert der Output-Dienst zehn PDF-Dokumente. (Anstatt Dokumente zu erstellen, können Sie mehrere Druck-Streams an einen Drucker senden.)

Die folgende Abbildung zeigt auch den Output-Dienst, der eine XML-Datendatei verarbeitet, die mehrere Datensätze enthält. Es wird jedoch davon ausgegangen, dass Sie den Output-Dienst anweisen, ein einzelnes PDF-Dokument zu erstellen, das alle Datensätze enthält. In diesem Fall generiert der Output-Dienst ein Dokument, das alle Datensätze enthält.

Die folgende Abbildung zeigt den Output-Dienst, der eine XML-Datendatei verarbeitet, die mehrere Datensätze enthält. Angenommen, Sie weisen den Output-Dienst an, für jeden Datensatz ein separates PDF-Dokument zu erstellen. In diesem Fall generiert der Output-Dienst für jeden Datensatz ein separates PDF-Dokument.

![cm_outputbatchmany](assets/cm_outputbatchmany.png)

Die folgenden XML-Daten zeigen ein Beispiel einer Datendatei, die drei Datensätze enthält.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <batch>
 <LoanRecord>
     <mortgageAmount>500000</mortgageAmount>
     <lastName>Blue</lastName>
     <firstName>Tony</firstName>
     <SSN>555666777</SSN>
     <PositionTitle>Product Manager</PositionTitle>
     <Address>555 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>TBlue@NoMailServer.com</Email>
     <PhoneNum>555-7418</PhoneNum>
     <FaxNum>555-9981</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 <LoanRecord>
     <mortgageAmount>300000</mortgageAmount>
     <lastName>White</lastName>
     <firstName>Sam</firstName>
     <SSN>555666222</SSN>
     <PositionTitle>Program Manager</PositionTitle>
     <Address>557 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>SWhite@NoMailServer.com</Email>
     <PhoneNum>555-7445</PhoneNum>
     <FaxNum>555-9986</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 <LoanRecord>
     <mortgageAmount>700000</mortgageAmount>
     <lastName>Green</lastName>
     <firstName>Steve</firstName>
     <SSN>55566688</SSN>
     <PositionTitle>Project Manager</PositionTitle>
     <Address>445 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>SGreeb@NoMailServer.com</Email>
     <PhoneNum>555-2211</PhoneNum>
     <FaxNum>555-2221</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 </batch>
```

Beachten Sie, dass das XML-Element, das jeden Datensatz startet und beendet, `LoanRecord` ist. Dieses XML-Element wird durch die Anwendungslogik referenziert, die mehrere Dateien generiert.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

So erstellen Sie mehrere PDF-Dateien basierend auf einer XML-Datenquelle:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Festlegen von PDF-Laufzeitoptionen.
1. Festlegen von Rendering-Laufzeitoptionen.
1. Generieren Sie mehrere PDF-Dateien.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Referenzieren einer XML-Datenquelle**

Referenzieren Sie eine XML-Datenquelle, die mehrere Datensätze enthält. Ein XML-Element muss verwendet werden, um die Datensätze zu trennen. In der Beispiel-XML-Datenquelle, die zuvor in diesem Abschnitt gezeigt wurde, trägt das XML-Element, das Datensätze trennt, den Namen `LoanRecord`.

Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

**PDF-Laufzeitoptionen festlegen**

Sie müssen die folgenden Laufzeitoptionen festlegen, damit der Output-Dienst erfolgreich mehrere Dateien basierend auf einer XML-Datenquelle erstellt:

* **Viele Dateien**: Gibt an, ob der Output-Dienst ein einzelnes Dokument oder mehrere Dokumente erstellt. Sie können &quot;true&quot;oder &quot;false&quot;angeben. Um ein separates Dokument für jeden Datensatz in der XML-Datenquelle zu erstellen, geben Sie &quot;true&quot;an.
* **Datei-URI**: Gibt den Speicherort der Dateien an, die der Output-Dienst generiert. Angenommen, Sie geben C:\\Adobe\forms\Loan.pdf an. In diesem Fall erstellt der Output-Dienst eine Datei mit dem Namen &quot;Loan.pdf&quot;und legt die Datei im Ordner &quot;C:\\Adobe\forms folder&quot;ab. Wenn mehrere Dateien vorliegen, lauten die Dateinamen &quot;Loan001.pdf&quot;, &quot;Loan0002.pdf&quot;, &quot;Loan003.pdf&quot;usw. Wenn Sie einen Dateispeicherort angeben, werden die Dateien auf dem Server und nicht auf dem Clientcomputer abgelegt.
* **Record Name**: Gibt den XML-Elementnamen in der Datenquelle an, der die Datensätze trennt. In der Beispiel-XML-Datenquelle, die oben in diesem Abschnitt gezeigt wird, heißt beispielsweise das XML-Element, das Datensätze trennt, `LoanRecord`. (Anstatt die Laufzeitoption &quot;Record Name&quot;festzulegen, können Sie die Datensatzebene festlegen, indem Sie ihr einen numerischen Wert zuweisen, der die Elementebene angibt, die Datensätze enthält. Sie können jedoch nur den Datensatznamen oder die Datensatzebene festlegen. Sie können nicht beide Werte festlegen.)

**Festlegen von Rendering-Laufzeitoptionen**

Sie können Laufzeitoptionen beim Rendern mehrerer Dateien festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu erforderlichen Ausgabelaufzeitoptionen), können Sie Aufgaben wie die Verbesserung der Leistung des Output-Dienstes ausführen. Beispielsweise können Sie den Formularentwurf zwischenspeichern, den der Output-Dienst verwendet, um die Leistung zu verbessern.

Wenn der Output-Dienst Batch-Datensätze verarbeitet, liest er inkrementell Daten, die mehrere Datensätze enthalten. Das heißt, der Output-Dienst liest die Daten in den Speicher und gibt die Daten frei, während der Datensatz-Batch verarbeitet wird. Der Output-Dienst lädt Daten inkrementell, wenn eine von zwei Laufzeitoptionen festgelegt ist. Wenn Sie die Laufzeitoption &quot;Record Name&quot;festlegen, liest der Output-Dienst die Daten inkrementell. Wenn Sie die Laufzeitoption &quot;Record Level&quot;auf 2 oder höher setzen, liest der Output-Dienst die Daten auf inkrementelle Weise.

Sie können mithilfe der `PDFOutputOptionsSpec` - oder `PrintedOutputOptionSpec` -Methode des Objekts `setLazyLoading` steuern, ob der Output-Dienst das inkrementelle Laden durchführt. Sie können den Wert `false` an diese Methode übergeben, wodurch das inkrementelle Laden deaktiviert wird.

**Generieren mehrerer PDF-Dateien**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die mehrere Datensätze enthält und Laufzeitoptionen festgelegt hat, können Sie den Output-Dienst aufrufen, wodurch mehrere Dateien generiert werden. Beim Generieren mehrerer Datensätze gibt die `getGeneratedDoc`-Methode des `OutputResult`-Objekts `null` zurück.

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, werden XML-Daten zurückgegeben, die angeben, ob der Vorgang erfolgreich war. Die folgende XML-Datei wird vom Output-Dienst zurückgegeben. In diesem Fall generiert der Output-Dienst 42 Dokumente.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <printResult>
 <status>0</status>
 <requestId>4ad85f9e2</requestId>
 <context/>
 <messages>
 <message>Printed all 42 records successfully.</message>
 </messages>
 <printSpec>
 <input>
 <validated>true</validated>
 <dataFile recordIdField="" recordLevel="0" recordName="LoanRecord"/>
 <sniffRules lookAhead="300"/>
 <formDesign>Loan.xdp</formDesign>
 <contentRoot>C:\Adobe</contentRoot>
 <metadata-spec record="false"/>
 </input>
 <output>
 <format>PDF</format>
 <fileURI>C:\Adobe\forms\Loan.pdf</fileURI>
 <optionString>cacheenabled=true&padebug=false&linearpdf=false&pdfarevisionnumber=1&pdfaconformance=A&taggedpdf=false&TransactionTimeOut=180</optionString>
 <waitForResponse>true</waitForResponse>
 <outputStream>multiple</outputStream>
 </output>
 </printSpec>
 </printResult>
```

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen mehrerer PDF-Dateien mit der Java-API {#create-multiple-pdf-files-using-the-java-api}

Erstellen Sie mehrere PDF-Dateien mithilfe der Ausgabe-API (Java):

1. Projektdateien einschließen&quot;

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein. .

1. Erstellen eines Output Client-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren einer XML-Datenquelle

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die mehrere Datensätze enthält, indem Sie den zugehörigen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. PDF-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Viele Dateien fest, indem Sie die `setGenerateManyFiles` -Methode des Objekts `PDFOutputOptionsSpec` aufrufen. Übergeben Sie beispielsweise den Wert `true`, um den Output-Dienst anzuweisen, für jeden Datensatz in der XML-Datenquelle eine separate PDF-Datei zu erstellen. (Wenn Sie `false` übergeben, generiert der Output-Dienst ein einzelnes PDF-Dokument, das alle Datensätze enthält).
   * Legen Sie die Option Datei-URI fest, indem Sie die Methode `setFileUri` des Objekts `PDFOutputOptionsSpec` aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort der Dateien angibt, die der Output-Dienst generiert. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.
   * Legen Sie die Option &quot;Record Name&quot;fest, indem Sie die `setRecordName` -Methode des Objekts `OutputOptionsSpec` aufrufen und einen string -Wert übergeben, der den XML-Elementnamen in der Datenquelle angibt, der die Datensätze trennt. (Betrachten Sie beispielsweise die zuvor in diesem Abschnitt gezeigte XML-Datenquelle. Der Name des XML-Elements, das die Datensätze trennt, ist LoanRecord).

1. Festlegen von Rendering-Laufzeitoptionen

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie die `setCacheEnabled` des Objekts `RenderOptionsSpec` aufrufen und den `Boolean`-Wert `true` übergeben.

1. Generieren mehrerer PDF-Dateien

   Generieren Sie mehrere PDF-Dateien, indem Sie die `generatePDFOutput` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein Enum-Wert `TransformationFormat`. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie ein `java.io.File` -Objekt, das eine XML-Datei darstellt, die die Ergebnisse der `generatePDFOutput` -Methode enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document` -Objekt verwenden, das von der `applyUsageRights` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen mehrerer PDF-Dateien mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-multiple-pdf-files-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen mehrerer PDF-Dateien mit der Webdienst-API {#create-multiple-pdf-files-using-the-web-service-api}

Erstellen Sie mehrere PDF-Dateien mithilfe der Output API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Formulardaten verwendet, die mehrere Datensätze enthalten.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort der XML-Datei darstellt, die mehrere Datensätze enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Festlegen von PDF-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Viele Dateien fest, indem Sie dem `generateManyFiles` -Datenelement des Objekts `OutputOptionsSpec` einen booleschen Wert zuweisen. Weisen Sie diesem Datenelement beispielsweise den Wert `true` zu, um den Output-Dienst anzuweisen, für jeden Datensatz in der XML-Datenquelle eine separate PDF-Datei zu erstellen. (Wenn Sie diesem Datenelement `false` zuweisen, generiert der Output-Dienst eine einzelne PDF-Datei, die alle Datensätze enthält).
   * Legen Sie die Datei-URI-Option fest, indem Sie einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Output-Dienst generierten Dateien angibt, dem `fileURI`-Datenelement des Objekts `OutputOptionsSpec`. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.
   * Legen Sie die Option für den Datensatznamen fest, indem Sie einen string -Wert zuweisen, der den XML-Elementnamen in der Datenquelle angibt, der die Datensätze vom `OutputOptionsSpec` -Datenelement des `recordName` -Objekts trennt.
   * Legen Sie die Option &quot;Copies&quot;fest, indem Sie einen ganzzahligen Wert zuweisen, der die Anzahl der vom Output-Dienst generierten Kopien an das `copies`-Datenelement des Objekts `OutputOptionsSpec` angibt.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie den Wert `true` dem `RenderOptionsSpec`-Datenelement des `cacheEnabled`-Objekts zuweisen.

1. Generieren Sie mehrere PDF-Dateien.

   Erstellen Sie mehrere PDF-Dateien, indem Sie die `generatePDFOutput`Methode des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Enum-Wert TransformationFormat . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben.
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit Ergebnisdaten.
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des Objekts `BLOB` speichert, das mit Ergebnisdaten aus der `OutputServiceService` -Methode des Objekts `generatePDFOutput` (dem achten Parameter) gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Erstellen von Suchregeln {#creating-search-rules}

Sie können Suchregeln erstellen, die dazu führen, dass der Output-Dienst Eingabedaten prüft und verschiedene Formularentwürfe verwendet, die auf dem Dateninhalt basieren, um die Ausgabe zu generieren. Wenn sich beispielsweise der Text *mortgage* in den Eingabedaten befindet, kann der Output-Dienst einen Formularentwurf namens Mortgage.xdp verwenden. Wenn sich der Text *automobile* in den Eingabedaten befindet, kann der Output-Dienst einen Formularentwurf verwenden, der als &quot;AutomobileLoan.xdp&quot;gespeichert ist. Der Output-Dienst kann zwar verschiedene Ausgabetypen generieren, geht aber in diesem Abschnitt davon aus, dass der Output-Dienst eine PDF-Datei generiert. Das folgende Diagramm zeigt den Output-Dienst, der eine PDF-Datei generiert, indem eine XML-Datendatei verarbeitet und einen von vielen Formularentwürfen verwendet wird.

Darüber hinaus kann der Output-Dienst Dokumentpakete generieren, in denen mehrere Datensätze im Datensatz bereitgestellt werden und jeder Datensatz mit einem Formularentwurf übereinstimmt und ein einzelnes Dokument aus mehreren Formularentwürfen generiert wird.

![cs_outputbatchmanyformdesigns2](assets/cs_outputbatchmanyformdesigns2.png)

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

So weisen Sie den Output-Dienst an, beim Generieren eines Dokuments Suchregeln zu verwenden:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Definieren Sie Suchregeln.
1. Festlegen von PDF-Laufzeitoptionen.
1. Festlegen von Rendering-Laufzeitoptionen.
1. Generieren Sie ein PDF-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie adobe-utilities.jar und jbossall-client.jar durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen.

**Referenzieren einer XML-Datenquelle**

Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Es ist nicht erforderlich, die Reihenfolge der Anzeige der XML-Elemente einzuhalten, solange alle XML-Elemente angegeben sind.

**Suchregeln definieren**

Um Suchregeln zu definieren, definieren Sie ein oder mehrere Textmuster, nach denen der Output-Dienst in den Eingabedaten sucht. Für jedes von Ihnen definierte Textmuster geben Sie einen entsprechenden Formularentwurf an, der verwendet wird, wenn sich das Textmuster befindet. Wenn sich ein Textmuster befindet, verwendet der Output-Dienst den entsprechenden Formularentwurf, um die Ausgabe zu generieren. Ein Beispiel für ein Textmuster ist *Hypothek*.

>[!NOTE]
>
>Wenn sich keine Textmuster befinden, wird das Standardformular verwendet. Stellen Sie sicher, dass sich alle von Ihnen verwendeten Formularentwürfe im Inhaltsstamm befinden.

**PDF-Laufzeitoptionen festlegen**

Legen Sie die folgenden PDF-Laufzeitoptionen fest, damit der Output-Dienst erfolgreich ein PDF-Dokument basierend auf mehreren Formularentwürfen erstellen kann:

* **Datei-URI**: Gibt den Namen und Speicherort der PDF-Datei an, die der Output-Dienst generiert.
* **Regeln**: Gibt von Ihnen definierte Regeln an.
* **LookAHead**: Gibt die Anzahl der Bytes an, die vom Anfang der Eingabedatendatei verwendet werden sollen, um nach den definierten Textmustern zu suchen. Der Standardwert ist 500 Byte.

**Festlegen von Rendering-Laufzeitoptionen**

Sie können beim Erstellen von PDF-Dateien Laufzeitoptionen für die Wiedergabe festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu PDF-Laufzeitoptionen), können Sie Aufgaben wie die Verbesserung der Leistung des Output-Dienstes ausführen. Beispielsweise können Sie den Formularentwurf zwischenspeichern, den der Output-Dienst verwendet, um die Leistung zu verbessern.

**Generieren eines PDF-Dokuments**

Nachdem Sie eine gültige XML-Datenquelle referenziert und Laufzeitoptionen festgelegt haben, können Sie den Output-Dienst aufrufen, der ein PDF-Dokument generiert. Wenn der Output-Dienst ein bestimmtes Textmuster in den Eingabedaten findet, verwendet er den entsprechenden Formularentwurf. Wenn kein Textmuster verwendet wird, verwendet der Output-Dienst den Standardformularentwurf.

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, werden XML-Daten zurückgegeben, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen Sie Suchregeln mit der Java-API {#create-search-rules-using-the-java-api}

Erstellen Sie Suchregeln mithilfe der Ausgabe-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des PDF-Dokuments mithilfe des zugehörigen Konstruktors verwendet wird, und übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Definieren Sie Suchregeln.

   * Erstellen Sie ein Objekt `Rule`, indem Sie den Konstruktor verwenden.
   * Definieren Sie ein Textmuster, indem Sie die `setPattern` -Methode des Objekts `Rule` aufrufen und einen Zeichenfolgenwert übergeben, der ein Textmuster angibt.
   * Definieren Sie den entsprechenden Formularentwurf, indem Sie die `setForm` -Methode des Objekts `Rule` aufrufen. Übergeben Sie einen string -Wert, der den Namen des Formularentwurfs angibt.

   >[!NOTE]
   >
   >Wiederholen Sie für jedes zu definierende Textmuster die vorherigen drei Unterschritte.

   * Erstellen Sie ein `java.util.List`-Objekt mithilfe eines `java.util.ArrayList`-Konstruktors.
   * Rufen Sie für jedes von Ihnen erstellte `Rule`-Objekt die `java.util.List` -Methode des Objekts `add` auf und übergeben Sie das `Rule` -Objekt.


1. Festlegen von PDF-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Namen und Speicherort der vom Output-Dienst generierten PDF-Datei an, indem Sie die `setFileURI` -Methode des Objekts `PDFOutputOptionsSpec` aufrufen. Übergeben Sie einen string -Wert, der den Speicherort der PDF-Datei angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.
   * Legen Sie die Regeln fest, die Sie definiert haben, indem Sie die `setRules` -Methode des Objekts `PDFOutputOptionsSpec` aufrufen. Übergeben Sie das `java.util.List`-Objekt, das die `Rule`-Objekte enthält.
   * Legen Sie die Anzahl der Bytes fest, die auf die definierten Textmuster gescannt werden sollen, indem Sie die `setLookAhead` -Methode des Objekts `PDFOutputOptionsSpec` aufrufen. Übergeben Sie einen ganzzahligen Wert, der die Anzahl der Bytes darstellt.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie die `setCacheEnabled`-Objektgruppe `RenderOptionsSpec` aufrufen und `true` übergeben.

1. Generieren Sie ein PDF-Dokument.

   Generieren Sie ein PDF-Dokument, das auf mehreren Formularentwürfen basiert, indem Sie die `generatePDFOutput` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string -Wert, der den Namen des Standardformularentwurfs angibt. Das heißt, der Formularentwurf, der verwendet wird, wenn sich ein Textmuster nicht befindet.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die Formularentwürfe befinden.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die Formulardaten enthält, die vom Output-Dienst nach den definierten Textmustern durchsucht werden.

   Die `generatePDFOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das den Status der `generatePDFOutput`-Methode darstellt, indem Sie die `OutputResult`-Methode des Objekts `getStatusDoc` aufrufen.
   * Erstellen Sie ein `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateierweiterung .xml lautet.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document` -Objekt verwenden, das von der `getStatusDoc` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen von Suchregeln mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen von Suchregeln mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen Sie Suchregeln mithilfe der Webdienst-API {#create-search-rules-using-the-web-service-api}.

Erstellen Sie Suchregeln mithilfe der Output-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Daten verwendet, die mit dem PDF-Dokument zusammengeführt werden.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Definieren Sie Suchregeln.

   * Erstellen Sie ein Objekt `Rule`, indem Sie den Konstruktor verwenden.
   * Definieren Sie ein Textmuster, indem Sie dem `pattern` -Datenelement des Objekts `Rule` einen Zeichenfolgenwert zuweisen, der ein Textmuster angibt.
   * Definieren Sie den entsprechenden Formularentwurf, indem Sie einen Zeichenfolgenwert zuweisen, der den Formularentwurf dem `Rule` -Datenelement des Objekts `form` angibt.

   >[!NOTE]
   >
   >Wiederholen Sie für jedes zu definierende Textmuster die vorherigen drei Unterschritte.

   * Erstellen Sie ein `MyArrayOf_xsd_anyType` -Objekt, das die Regeln speichert.
   * Weisen Sie jedes `Rule`-Objekt einem Element des `MyArrayOf_xsd_anyType`-Arrays zu. Rufen Sie für jedes `Rule`-Objekt die `Add`-Methode des Objekts auf.`MyArrayOf_xsd_anyType`


1. PDF-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Datei-URI-Option fest, indem Sie einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Output-Dienst generierten PDF-Datei an das `fileURI`-Datenelement des Objekts `PDFOutputOptionsSpec` angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.
   * Legen Sie die Option &quot;Copies&quot;fest, indem Sie einen ganzzahligen Wert zuweisen, der die Anzahl der vom Output-Dienst generierten Kopien an das `copies`-Datenelement des Objekts `PDFOutputOptionsSpec` angibt.
   * Legen Sie die von Ihnen definierten Regeln fest, indem Sie das `MyArrayOf_xsd_anyType`-Objekt, das die Regeln speichert, dem `PDFOutputOptionsSpec`-Datenelement des `rules`-Objekts zuweisen.
   * Legen Sie die Anzahl der Bytes fest, die auf die definierten Textmuster gescannt werden sollen, indem Sie einen ganzzahligen Wert für die Anzahl der zu scannenden Bytes an die `lookAhead` -Datenmethode des Objekts `PDFOutputOptionsSpec` zuweisen.

1. Festlegen von Rendering-Laufzeitoptionen

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie den Wert `true` dem `RenderOptionsSpec`-Datenelement des `cacheEnabled`-Objekts zuweisen.

   >[!NOTE]
   >
   >Sie können die Version des PDF-Dokuments nicht mithilfe des Elements `RenderOptionsSpec` des Objekts `pdfVersion` festlegen, wenn das Eingabedokument ein Acrobat-Formular ist. Das PDF-Ausgabedokument behält die PDF-Version des Acrobat-Formulars bei. Ebenso können Sie die getaggte PDF-Option nicht mithilfe der `RenderOptionsSpec` -Methode des Objekts `taggedPDF` festlegen, wenn das Eingabedokument ein Acrobat-Formular ist.

   >[!NOTE]
   >
   >Sie können die Option für linearisierte PDF nicht mithilfe des Elements `RenderOptionsSpec` des Objekts `linearizedPDF` festlegen, wenn das PDF-Eingabedokument zertifiziert oder digital signiert ist. Weitere Informationen finden Sie unter [PDF-Dokumente digital signieren](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).

1. Generieren eines PDF-Dokuments

   Erstellen Sie ein PDF-Dokument, indem Sie die `generatePDFOutput`Methode des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Auflistungswert `TransformationFormat` . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein `BLOB` -Objekt, das von der `generatePDFOutput` -Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

   >[!NOTE]
   >
   >Beachten Sie beim Generieren eines PDF-Dokuments durch Aufrufen der `generatePDFOutput`-Methode, dass Sie keine Daten mit einem XFA-PDF-Formular zusammenführen können, das signiert, zertifiziert oder Verwendungsrechte enthält. Weitere Informationen zu Verwendungsrechten finden Sie unter [Anwenden von Verwendungsrechten auf PDF-Dokumente](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des Objekts `BLOB` speichert, das mit Ergebnisdaten aus der `OutputServiceService` -Methode des Objekts `generatePDFOutput` (dem achten Parameter) gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Reduzieren von PDF-Dokumenten {#flattening-pdf-documents}

Sie können den Output-Dienst verwenden, um ein interaktives PDF-Dokument in eine nicht interaktive PDF-Datei umzuwandeln. Mit einem interaktiven PDF-Dokument können Benutzer Daten in die Felder des PDF-Dokuments eingeben oder ändern. Der Prozess der Umwandlung eines interaktiven PDF-Dokuments in ein nicht interaktives PDF-Dokument wird als *Reduzieren* bezeichnet. Wenn ein PDF-Dokument reduziert wird, kann ein Benutzer die Daten in den Dokumentfeldern nicht ändern. Dies kann ein Grund dafür sein, PDF-Dokumente zu reduzieren.

Sie können die folgenden Arten von PDF-Dokumenten reduzieren:

* Interaktive XFA-PDF-Dokumente
* Acrobat Forms

Beim Versuch, ein PDF-Dokument zu reduzieren, das kein interaktives PDF-Dokument ist, wird eine Ausnahme verursacht.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-9}

So reduzieren Sie ein interaktives PDF-Dokument auf ein nicht interaktives PDF-Dokument:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Rufen Sie ein interaktives PDF-Dokument ab.
1. Konvertieren Sie das PDF-Dokument.
1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Abrufen eines interaktiven PDF-Dokuments**

Rufen Sie ein interaktives PDF-Dokument ab, das Sie in ein nicht interaktives PDF-Dokument umwandeln möchten. Der Versuch, ein nicht interaktives PDF-Dokument umzuwandeln, verursacht eine Ausnahme.

**PDF-Dokument transformieren**

Nachdem Sie ein interaktives PDF-Dokument abgerufen haben, können Sie es in ein nicht interaktives PDF-Dokument umwandeln. Der Output-Dienst gibt ein nicht interaktives PDF-Dokument zurück.

**Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei**

Sie können das nicht interaktive PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Reduzieren eines PDF-Dokuments mithilfe der Java-API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-java-api)

[Reduzieren eines PDF-Dokuments mithilfe der Webdienst-API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Reduzieren eines PDF-Dokuments mithilfe der Java-API {#flatten-a-pdf-document-using-the-java-api}

Reduzieren Sie ein interaktives PDF-Dokument mithilfe der Output API (Java) in ein nicht interaktives PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Rufen Sie ein interaktives PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu transformierende interaktive PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der interaktiven PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Konvertieren Sie das PDF-Dokument.

   Wandeln Sie das interaktive PDF-Dokument in ein nicht interaktives PDF-Dokument um, indem Sie die `transformPDF` -Methode des Objekts `OutputServiceService` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das interaktive PDF-Dokument enthält.
   * Ein Enum-Wert `TransformationFormat`. Um ein nicht interaktives PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein `PDFARevisionNumber`-Enum-Wert, der die Revisionsnummer angibt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null` angeben.
   * Ein string -Wert, der die Änderungsnummer und das Jahr darstellt, getrennt durch einen Doppelpunkt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null` angeben.
   * Ein `PDFAConformance`-Enum-Wert, der die PDF/A-Konformitätsstufe darstellt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null` angeben.

   Die `transformPDF`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile` -Methode des `Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `transformPDF` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): PDF-Dokument mit der Java-API transformieren](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): PDF-Dokument mit der Java-API transformieren](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Reduzieren eines PDF-Dokuments mithilfe der Webdienst-API {#flatten-a-pdf-document-using-the-web-service-api}

Reduzieren Sie ein interaktives PDF-Dokument mithilfe der Output API (Webdienst) in ein nicht interaktives PDF-Dokument:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `OutputServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein interaktives PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des interaktiven PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des interaktiven PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Konvertieren Sie das PDF-Dokument.

   Wandeln Sie das interaktive PDF-Dokument in ein nicht interaktives PDF-Dokument um, indem Sie die `transformPDF` -Methode des Objekts `OutputClient` aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB` -Objekt, das das interaktive PDF-Dokument enthält.
   * Ein Auflistungswert `TransformationFormat` . Um ein nicht interaktives PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein `PDFARevisionNumber`-Enum-Wert, der die Revisionsnummer angibt.
   * Ein boolescher Wert, der angibt, ob der Enum-Wert `PDFARevisionNumber` verwendet wird. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `false` angeben.
   * Ein string -Wert, der die Änderungsnummer und das Jahr darstellt, getrennt durch einen Doppelpunkt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null` angeben.
   * Ein `PDFAConformance`-Enum-Wert, der die PDF/A-Konformitätsstufe darstellt.
   * Boolescher Wert, der angibt, ob der Enum-Wert `PDFAConformance` verwendet wird. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `false` angeben.

   Die `transformPDF`-Methode gibt ein `BLOB`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des nicht interaktiven PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `transformPDF` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
