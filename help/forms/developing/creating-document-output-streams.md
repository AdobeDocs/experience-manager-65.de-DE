---
title: Erstellen von Dokumentausgabe-Streams
description: Verwenden Sie den Ausgabeservice zum Konvertieren von Dokumenten in die Formate PDF (einschließlich PDF/A-Dokumente), PostScript, Printer Control Language (PCL) und Zebra – ZPL, Intermec – IPL, Datamax – DPL und TecToshiba – TPCL.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: a521bfac-f417-4002-9c5c-8d7794d3eec7
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '18860'
ht-degree: 100%

---

# Erstellen von Dokumentausgabe-Streams  {#creating-document-output-streams}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den Ausgabeservice**

Mit dem Ausgabeservice können Sie Dokumente in den Formaten PDF (einschließlich PDF/A-Dokumente), PostScript, Printer Control Language (PCL) und den folgenden Beschriftungsformaten ausgeben:

* Zebra (ZPL)
* Intermec (IPL)
* Datamax (DPL)
* TecToshiba (TPCL)

Mithilfe des Ausgabeservice können Sie XML-Formulardaten mit einem Formularentwurf zusammenführen und das Dokument an einen Netzwerkdrucker oder eine Datei ausgeben.

Es gibt zwei Möglichkeiten, einen Formularentwurf (eine XDP-Datei) an den Ausgabeservice zu übergeben. Sie können entweder eine `com.adobe.idp.Document`-Instanz, die einen Formularentwurf enthält, an den Ausgabeservice übergeben. Sie können auch einen URI-Wert übergeben, der den Speicherort des Formularentwurfs angibt. Beide Methoden werden in *Programmieren mit AEM Forms* erläutert.

>[!NOTE]
>
>Der Ausgabeservice unterstützt keine Acroform-PDF-Dokumente, die anwendungsobjektspezifische Skripte enthalten. Acroform-PDF-Dokumente, die anwendungsobjektspezifische Skripte enthalten, werden nicht gerendert.

Die folgenden Abschnitte zeigen, wie Sie einen Formularentwurf mithilfe eines URI-Werts an den Ausgabeservice übergeben:

* [Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)
* [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents)

Die folgenden Abschnitte zeigen, wie Sie einen Formularentwurf in eine `com.adobe.idp.Document`-Instanz übergeben:

* [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Ausgabe-Service](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Erstellen von PDF-Dokumenten mithilfe von Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

Bei der Entscheidung über die zu verwedende Technik sollten Sie den Formularentwurf, wenn Sie ihn von einem anderen AEM Forms-Service abrufen, innerhalb einer `com.adobe.idp.Document`-Instanz übergeben. Beide Abschnitte *Übergeben von Dokumenten an den Ausgabeservice* und *Erstellen von PDF-Dokumenten mithilfe von Fragmenten* zeigen, wie Sie einen Formularentwurf von einem anderen AEM Forms-Service abrufen. Im ersten Abschnitt wird der Formularentwurf aus Content Services (nicht mehr unterstützt) abgerufen. Im zweiten Abschnitt wird der Formularentwurf aus dem Assembler-Service abgerufen.

Wenn Sie den Formularentwurf aus einem festen Speicherort wie dem Dateisystem abrufen, können Sie beide Verfahren verwenden. Das heißt, Sie können den URI-Wert für eine XDP-Datei angeben oder eine `com.adobe.idp.Document`-Instanz verwenden.

Um beim Erstellen eines PDF-Dokuments einen URI-Wert zu übergeben, der den Speicherort des Formularentwurfs angibt, verwenden Sie die `generatePDFOutput`-Methode. Entsprechend müssen Sie beim Erstellen eines PDF-Dokuments zum Übergeben einer `com.adobe.idp.Document`-Instanz an den Ausgabeservice die `generatePDFOutput2`-Methode verwenden.

Wenn Sie einen Ausgabestream an einen Netzwerkdrucker senden, können Sie ebenfalls eine der beiden Methoden verwenden. Um einen Ausgabestream an einen Drucker durch Übergeben einer `com.adobe.idp.Document`-Instanz, die einen Formularentwurf enthält, zu senden, verwenden Sie die `sendToPrinter2`-Methode. Um einen Ausgabestream an einen Drucker durch Übergeben eines URI-Werts zu senden, verwenden Sie die `sendToPrinter`-Methode. Der Abschnitt *Senden von Druckstreams an Drucker* verwendet die `sendToPrinter`-Methode.

Sie können diese Aufgaben mithilfe des Ausgabeservice ausführen:

* [Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)
* [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents)
* [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Ausgabe-Service](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Erstellen von PDF-Dokumenten mithilfe von Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)
* [Drucken in Dateien](creating-document-output-streams.md#printing-to-files)
* [Senden von Druck-Streams an Drucker](creating-document-output-streams.md#sending-print-streams-to-printers)
* [Erstellen mehrerer Ausgabedateien](creating-document-output-streams.md#creating-multiple-output-files)
* [Erstellen von Suchregeln](creating-document-output-streams.md#creating-search-rules)
* [Reduzieren von PDF-Dokumenten](creating-document-output-streams.md#flattening-pdf-documents)

>[!NOTE]
>
>Weitere Informationen zum Ausgabeservice finden Sie in der [Servicesreferenz zu AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)..

## Erstellen von PDF-Dokumenten {#creating-pdf-documents}

Sie können den Ausgabeservice verwenden, um ein PDF-Dokument zu erstellen, das auf einem Formularentwurf und XML-Formulardaten basiert, die Sie bereitstellen. Das vom Ausgabeservice erstellte PDF-Dokument ist kein interaktives PDF-Dokument. Benutzer können keine Formulardaten eingeben oder ändern.

Wenn Sie ein PDF-Dokument für eine langfristige Speicherung erstellen möchten, wird empfohlen, ein PDF/A-Dokument zu erstellen. (Siehe [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents).)

Verwenden Sie den Forms-Service, um ein interaktives PDF-Formular zu erstellen, mit dem Benutzer Daten eingeben können. (Siehe [Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms).)

>[!NOTE]
>
>Weitere Informationen zum Output-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output-Client-Objekt.
1. Referenzieren Sie eine XML-Datenquelle.
1. Legen Sie PDF-Laufzeitoptionen fest.
1. Legen Sie Rendering-Laufzeitoptionen fest.
1. Generieren Sie ein PDF-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Einbinden von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt wird, der nicht JBOSS ist, müssen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungs-Server sind, auf dem AEM Forms bereitgestellt wird. 

**Erstellen eines Output-Client-Objekts**

Bevor Sie einen Output-Service-Vorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt für den Output-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient`-Objekt. Wenn Sie die Output-Webservice-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Referenzieren einer XML-Datenquelle**

Um Daten mit dem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle referenzieren, die Daten enthält. Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht übereinstimmen.

Beachten Sie das folgende Beispielformular für einen Kreditantrag.

![cp_cp_loanformdata](assets/cp_cp_loanformdata.png)

Um Daten in diesem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle erstellen, die dem Formular entspricht. Die folgende XML-Datei stellt eine XDP-XML-Datenquelle dar, die dem Beispielformular für einen Hypothekenantrag entspricht.

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

**Festlegen von PDF-Laufzeitoptionen**

Legen Sie die Datei-URI-Option beim Erstellen eines PDF-Dokuments fest. Diese Option gibt den Namen und den Speicherort der PDF-Datei an, die der Output-Service generiert.

>[!NOTE]
>
>Statt die Laufzeitoption für den Datei-URI festzulegen, können Sie das PDF-Dokument programmgesteuert vom komplexen Datentyp abrufen, der vom Output-Service zurückgegeben wird. Durch Festlegen der Laufzeitoption für den Datei-URI müssen Sie jedoch keine Programmlogik erstellen, die das PDF-Dokument programmgesteuert abruft.

**Festlegen von Rendering-Laufzeitoptionen**

Beim Erstellen eines PDF-Dokuments können Sie Rendering-Laufzeitoptionen festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu PDF-Laufzeitoptionen, die erforderlich sind), können Sie Aufgaben wie die Leistungsverbesserung des Output-Service ausführen. Beispielsweise können Sie das Formular-Design zwischenspeichern, das der Ausgabe-Service verwendet, um dessen Leistung zu verbessern.

Wenn Sie ein getaggtes Acrobat-Formular als Eingabe verwenden, können Sie die Java- oder die Webservice-API des Output-Service nicht verwenden, um die getaggte Einstellung zu deaktivieren. Wenn Sie versuchen, diese Option programmgesteuert auf `false` festzulegen, ist das PDF-Ergebnisdokument weiterhin getaggt.

>[!NOTE]
>
>Wenn Sie keine Rendering-Laufzeitoptionen angeben, werden Standardwerte verwendet. Informationen zu Rendering-Laufzeitoptionen finden Sie in der `RenderOptionsSpec`-Klassenreferenz. (Siehe [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

**Generieren eines PDF-Dokuments**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die Formulardaten enthält, und Laufzeitoptionen festgelegt haben, können Sie den Output-Service aufrufen. Dadurch wird ein PDF-Dokument generiert.

Beim Generieren eines PDF-Dokuments geben Sie URI-Werte an, die für den Output-Service zum Erstellen eines PDF-Dokuments erforderlich sind. Ein Formularentwurf kann in Speicherorten wie dem Serverdateisystem oder als Teil eines AEM Forms-Programms gespeichert werden. Ein Formularentwurf (oder andere Ressourcen wie eine Grafikdatei), der Teil eines Forms-Programms ist, kann mithilfe des Inhaltsstamm-URI-Werts `repository:///` referenziert werden. Betrachten Sie beispielsweise den folgenden Formularentwurf mit dem Namen *Loan.xdp*, der in einer Forms-Anwendung mit dem Namen *Applications/FormsApplication* enthalten ist:

![cp_cp_formrepository](assets/cp_cp_formrepository.png)

Um auf die in der vorherigen Abbildung dargestellte Datei „Loan.xdp“ zuzugreifen, geben Sie `repository:///Applications/FormsApplication/1.0/FormsFolder/` als dritten Parameter der Methode `generatePDFOutput` des `OutputClient`-Objekts an. Geben Sie den Namen des Formulars (*Loan.xdp*) als zweiten Parameter an, der an die Methode `generatePDFOutput` des `OutputClient`-Objekts übergeben wird.

Wenn die XDP-Datei Bilder (oder andere Ressourcen wie Fragmente) enthält, legen Sie die Ressourcen im gleichen Anwendungsordner wie die XDP-Datei ab. AEM Forms verwendet den Inhaltsstamm-URI als Basispfad, um Verweise auf Bilder aufzulösen. Wenn die Datei „Loan.xdp“ beispielsweise ein Bild enthält, stellen Sie sicher, dass Sie das Bild in `Applications/FormsApplication/1.0/FormsFolder/` ablegen.

>[!NOTE]
>
>Sie können bei Aufrufen der Methode `generatePDFOutput` oder `generatePrintedOutput` des `OutputClient`-Objekts auf den URI der Formularanwendung verweisen.

>[!NOTE]
>
>Einen vollständigen Schnellstart zum Erstellen eines PDF-Dokuments durch Referenzieren einer XDP-Datei in einer Formularanwendung finden Sie unter [Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments basierend auf einer Anwendungs-XDP-Datei mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api).

**Abrufen der Ergebnisse des Vorgangs**

Nachdem der Output-Service einen Vorgang ausgeführt hat, gibt er verschiedene Datenelemente zurück, z. B. Status-XML-Daten, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Erstellen eines PDF-Dokuments mit der Java-API](creating-document-output-streams.md#create-a-pdf-document-using-the-java-api)

[Erstellen eines PDF-Dokuments mit der Web Service-API](creating-document-output-streams.md#create-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen eines PDF-Dokuments mit der Java-API {#create-a-pdf-document-using-the-java-api}

Erstellen Sie ein PDF-Dokument mithilfe der Output-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des PDF-Dokuments verwendet wird, indem Sie seinem Konstruktor einen Zeichenfolgenwert übergeben, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein Objekt `com.adobe.idp.Document`, indem Sie den Konstruktor verwenden. Übergeben Sie das `java.io.FileInputStream`-Objekt.

1. Legen Sie PDF-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Datei-URI-Option fest, indem Sie die Methode `setFileURI` des `PDFOutputOptionsSpec`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der vom Output-Service generierten PDF-Datei angibt. Die Datei-URI-Option ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, nicht zum Clientcomputer.

1. Legen Sie Rendering-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Speichern Sie den Formularentwurf zwischen, um die Leistung des Ausgabe-Service zu verbessern, indem Sie `setCacheEnabled` des `RenderOptionsSpec`-Objekts aufrufen und `true` übergeben.

   >[!NOTE]
   >
   >Sie können die PDF-Dokumentversion nicht mithilfe der Methode `setPdfVersion` des `RenderOptionsSpec`-Objekts festlegen, wenn das Eingabedokument ein Acrobat-Formular (ein in Acrobat erstelltes Formular) oder XFA-Dokument ist, das signiert oder zertifiziert ist. Das PDF-Ausgabedokument behält die PDF-Originalversion bei. Ebenso können Sie die Option für Adobe PDF mit Tags nicht festlegen, indem Sie die Methode `setTaggedPDF` des `RenderOptionsSpec`-Objekts aufrufen, wenn das Eingabedokument ein signiertes oder zertifiziertes Acrobat-Formular oder XFA-Dokument ist.

   >[!NOTE]
   >
   >Sie können die Option „Linearisierte PDF“ nicht mithilfe der Methode `setLinearizedPDF` des `RenderOptionsSpec`-Objekts festlegen, wenn das PDF-Eingabedokument zertifiziert oder digital signiert ist. (Weitere Informationen finden Sie unter [PDF-Dokumente digital signieren ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Generieren Sie ein PDF-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die Methode `generatePDFOutput` des `OutputClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das das Ergebnis der Authentifizierung enthält.

   >[!NOTE]
   >
   >Beim Erzeugen eines PDF-Dokuments durch Aufrufen der Methode `generatePDFOutput` können Sie keine Daten mit einem XFA-PDF-Formular zusammenführen, das signiert oder zertifiziert ist. (Siehe [Digitales Signieren und Zertifizieren von Dokumenten ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >Die Methode `getRecordLevelMetaDataList` des `OutputResult`-Objekts gibt `null`*zurück.*

   >[!NOTE]
   >
   >Sie können auch ein PDF-Dokument erstellen, indem Sie die Methode `generatePDFOutput2` des `OutputClient`-Objekts aufrufen. (Weitere Informationen finden Sie unter [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Ausgabe-Service ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Rufen Sie ein `com.adobe.idp.Document`-Objekt ab, das den Status des Vorgangs `generatePDFOutput` darstellt, indem Sie die Methode `getStatusDoc` des `OutputResult`-Objekts aufrufen. Diese Methode gibt Status-XML-Daten zurück, die angeben, ob der Vorgang erfolgreich war.
   * Erstellen Sie ein `java.io.File`-Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um die Inhalte des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt benutzen, das von der Methode `getStatusDoc` zurückgegeben wurde).

   Obwohl der Ausgabe-Service das PDF-Dokument an den Speicherort schreibt, der in dem an die Methode `setFileURI` des `PDFOutputOptionsSpec`-Objekts übergebenen Argument angegeben wird, können Sie das PDF/A-Dokument programmgesteuert abrufen, indem Sie die Methode `getGeneratedDoc` des `OutputResult`-Objekts aufrufen.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen eines PDF-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen eines PDF-Dokuments mit der Web Service-API {#create-a-pdf-document-using-the-web-service-api}

Erstellen Sie ein PDF-Dokument mithilfe der Output API (Web Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie mithilfe des Standardkonstruktors ein `OutputServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `OutputServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `OutputServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt dient zum Speichern von XML-Daten, die mit dem PDF-Dokument zusammengeführt werden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und ihm einen Zeichenfolgenwert übergeben, der den Dateispeicherort der XML-Datei mit den Formulardaten darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld den Inhalt des Byte-Arrays zuweisen.

1. Festlegen von PDF-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Datei-URI-Option fest, indem Sie dem Datenelement `fileURI` des `PDFOutputOptionsSpec`-Objekts einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Ausgabe-Service generierten PDF-Datei angibt. Die Datei-URI-Option ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, nicht zum Clientcomputer.

1. Legen Sie Rendering-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Speichern Sie das Formular-Design zwischen, um die Leistung des Ausgabe-Services zu verbessern, indem Sie dem Datenelement `cacheEnabled` des `RenderOptionsSpec`-Objekts den Wert `true` zuweisen.

   >[!NOTE]
   >
   >Sie können die Version des PDF-Dokuments nicht festlegen, indem Sie die Methode `setPdfVersion` des `RenderOptionsSpec`-Objekts verwenden, falls das Eingabedokument ein Acrobat-Formular (ein in Acrobat erstelltes Formular) oder ein XFA-Dokument ist, das signiert oder zertifiziert ist. Das PDF-Ausgabedokument behält die PDF-Originalversion bei. Genauso wenig können Sie die Option für Adobe PDF mit Tags festlegen, indem Sie die Methode `setTaggedPDF` des `RenderOptionsSpec`-Objekts aufrufen, falls das Eingabedokument ein Acrobat-Formular oder ein signiertes oder zertifiziertes XFA-Dokument ist.*

   >[!NOTE]
   >
   >Sie können Option „Linearisiertes PDF“ nicht festlegen, indem Sie das Datenelement `linearizedPDF` des `RenderOptionsSpec`-Objekts verwenden, falls das die Eingabe-PDF-Datei zertifiziert oder digital signiert ist. (Weitere Informationen finden Sie unter [PDF-Dokumente digital signieren ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Generieren Sie ein PDF-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die Methode `generatePDFOutput` des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB`-Objekt, das von der `generatePDFOutput`-Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).
   * Ein `BLOB`-Objekt, das von der `generatePDFOutput`-Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).
   * Ein `OutputResult`-Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).

   >[!NOTE]
   >
   >Beim Erstellen eines PDF-Dokuments mithilfe des Aufrufs der Methode `generatePDFOutput` können Sie keine Daten mit einem XFA-PDF-Formular zusammenführen, das signiert oder zertifiziert ist. (Siehe [Digitales Signieren und Zertifizieren von Dokumenten ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >Sie können auf ein PDF-Dokument erstellen, indem Sie die Methode `generatePDFOutput2` des `OutputClient`-Objekts aufrufen. (Weitere Informationen finden Sie unter [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Ausgabe-Service ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der einen XML-Dateispeicherort darstellt, welcher Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das durch die Methode `generatePDFOutput` des `OutputServiceService`-Objekts mit Ergebnisdaten (dem achten Parameter) gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `MTOM`-`field` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein Objekt vom Typ `System.IO.BinaryWriter`, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts verwenden und das Byte-Array übergeben.

   Siehe auch

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

   >[!NOTE]
   >
   >Die Methode `generateOutput` des `OutputServiceService`-Objekts ist veraltet.

## Erstellen von PDF/A-Dokumenten {#creating-pdf-a-documents}

Sie können den Ausgabe-Service verwenden, um ein PDF/A-Dokument zu erstellen. Da PDF/A ein Archivierungsformat für die langfristige Beibehaltung des Dokumentinhalts ist, werden alle Schriftarten eingebettet und die Datei wird nicht komprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte. Wie auch bei anderen Ausgabe-Service-Aufgaben stellen Sie sowohl einen Formularentwurf als auch Daten bereit, die mit einem Formularentwurf zusammengeführt werden sollen, um ein PDF/A-Dokument zu erstellen.

Die PDF/A-1-Spezifikation besteht aus zwei Konformitätsstufen, nämlich a und b. Der wesentliche Unterschied zwischen den beiden besteht in der Unterstützung der logischen Struktur (Zugänglichkeit), die für die Konformitätsstufe b nicht erforderlich ist. Unabhängig von der Konformitätsstufe bestimmt PDF/A-1, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind.

Obwohl PDF/A der Standard für die Archivierung von PDF-Dokumenten ist, ist es nicht erforderlich, PDF/A für die Archivierung zu verwenden, wenn ein standardmäßiges PDF-Dokument den Anforderungen Ihrer Firma entspricht. Der PDF/A-Standard dient der Erstellung einer PDF-Datei, die über einen längeren Zeitraum gespeichert werden kann und die Anforderungen an die Dokumentenerhaltung erfüllt. Beispielsweise kann eine URL nicht in eine PDF/A eingebettet werden, da die URL im Laufe der Zeit ungültig werden kann.

Ihre Organisation muss ihre eigenen Bedürfnisse, die Dauer der Aufbewahrung des Dokuments und die Dateigröße berücksichtigen und ihre eigene Archivierungsstrategie festlegen. Mit dem DocConverter-Service können Sie programmgesteuert feststellen, ob ein PDF-Dokument PDF/A-konform ist. (Siehe [Programmgesteuerte Ermittlung der PDF/A-Konformität](/help/forms/developing/pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

Ein PDF/A-Dokument muss die im Formularentwurf angegebene Schriftart verwenden, und Schriftarten können nicht ersetzt werden. Wenn daher eine Schriftart, die sich in einem PDF-Dokument befindet, auf dem Host-Betriebssystem nicht verfügbar ist, tritt eine Ausnahme auf.

Wenn ein PDF/A-Dokument in Acrobat geöffnet wird, wird eine Meldung angezeigt, die bestätigt, dass es sich um ein PDF/A-Dokument handelt, wie in der folgenden Abbildung dargestellt.

![cp_cp_pdfamessage](assets/cp_cp_pdfamessage.png)

>[!NOTE]
>
>Auf der AIIM-Website finden Sie unter [https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml](https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml) einen Bereich mit häufig gestellten Fragen zu PDF/A.

>[!NOTE]
>
>Weitere Informationen zum Ausgabe-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_65_de).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um ein PDF/A-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output-Client-Objekt.
1. Referenzieren Sie eine XML-Datenquelle.
1. Legen Sie PDF/A-Laufzeitoptionen fest.
1. Legen Sie Rendering-Laufzeitoptionen fest.
1. Erstellen Sie ein PDF/A-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Einbinden von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein benutzerdefiniertes Programm mithilfe von Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt wird, der nicht JBOSS ist, müssen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungs-Server sind, auf dem AEM Forms bereitgestellt wird. 

**Erstellen eines Output-Client-Objekts**

Bevor Sie einen Output-Service-Vorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt für den Output-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient`-Objekt. Wenn Sie die Output-Webservice-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Referenzieren einer XML-Datenquelle**

Um Daten mit dem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle referenzieren, die Daten enthält. Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht übereinstimmen.

**Festlegen von PDF/A-Laufzeitoptionen**

Sie können die Option „Datei-URI“ beim Erstellen eines PDF/A-Dokuments festlegen. Der URI bezieht sich auf den J2EE-Programm-Server, der als Host für AEM Forms dient. Wenn Sie also C:\Adobe festlegen, wird die Datei in den Ordner auf dem Server geschrieben, nicht auf den Client-Computer. Der URI gibt den Namen und Speicherort der PDF/A-Datei an, die der Output-Service generiert.

**Festlegen von Rendering-Laufzeitoptionen**

Beim Erstellen von PDF/A-Dokumenten können Sie Laufzeitoptionen für das Rendern festlegen. Zwei PDF/A-Optionen, die Sie festlegen können, sind die Werte `PDFAConformance` und `PDFARevisionNumber`. Der Wert `PDFAConformance` gibt an, inwieweit ein PDF-Dokument den Anforderungen bezüglich der Langzeitarchivierung elektronischer Dokumente entspricht. Gültige Werte für diese Option sind `A` und `B`. Informationen zu Konformitätsstufe a und b finden Sie in der ISO-Spezifikation PDF/A-1 mit dem Titel *ISO 19005-1 Dokumentenmanagement*.

Die `PDFARevisionNumber`-Wert bezieht sich auf die Revisionsnummer eines PDF/A-Dokuments. Informationen zur Revisionsnummer eines PDF/A-Dokuments finden Sie in der ISO-Spezifikation PDF/A-1 mit dem Titel *ISO 19005-1 Dokumentenmanagement*.

>[!NOTE]
>
>Sie können die Option „Adobe PDF mit Tags“ beim Erstellen eines PDF/A 1A-Dokuments nicht auf `false` festlegen. PDF/A 1A ist immer ein PDF-Dokument mit Tags. Außerdem können Sie die Option „Adobe PDF mit Tags“ beim Erstellen eines PDF/A 1B-Dokuments nicht auf `true` festlegen. PDF/A 1B ist immer ein PDF-Dokument ohne Tags.

**Erstellen eines PDF/A-Dokuments**

Nachdem Sie auf eine gültige XML-Datenquelle, die Formulardaten enthält, verwiesen und Laufzeitoptionen festgelegt haben, können Sie den Output-Service aufrufen, der daraufhin ein PDF/A-Dokument generiert.

**Abrufen der Ergebnisse eines Vorgangs**

Nachdem der Output-Service einen Vorgang ausgeführt hat, gibt er verschiedene Datenelemente wie XML-Daten zurück, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Erstellen eines PDF/A-Dokuments mit der Java-API](creating-document-output-streams.md#create-a-pdf-a-document-using-the-java-api)

[Erstellen eines PDF/A-Dokuments mithilfe der Web Service-API](creating-document-output-streams.md#create-a-pdf-a-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen eines PDF/A-Dokuments mit der Java-API {#create-a-pdf-a-document-using-the-java-api}

Erstellen Sie ein PDF/A-Dokument mithilfe der Output-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des PDF/A-Dokuments verwendet wird, indem Sie seinen Konstruktor aufrufen und ihm einen Zeichenfolgenwert übergibt, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von PDF/A-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Datei-URI-Option fest, indem Sie die Methode `setFileURI` des `PDFOutputOptionsSpec`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der vom Output-Service generierten PDF-Datei angibt. Die Datei-URI-Option ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, nicht zum Clientcomputer.

1. Legen Sie Rendering-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie den `PDFAConformance`-Wert fest, indem Sie die Methode `setPDFAConformance` des `RenderOptionsSpec`-Objekts aufrufen und einen `PDFAConformance`-Auflistungswert übergeben, der die Konformitätsstufe angibt. Um beispielsweise Konformitätsstufe A anzugeben, übergeben Sie `PDFAConformance.A`.
   * Legen Sie den `PDFARevisionNumber`-Wert fest, indem Sie die Methode `setPDFARevisionNumber` des `RenderOptionsSpec`-Objekts aufrufen und `PDFARevisionNumber.Revision_1` übergeben.

   >[!NOTE]
   >
   >Die PDF-Version eines PDF/A-Dokuments ist 1.4, unabhängig davon, welchen Wert Sie für die Methode `setPdfVersion`*des `RenderOptionsSpec`-Objekts angeben.*

1. Erstellen Sie ein PDF/A-Dokument.

   Erstellen Sie ein PDF/A-Dokument, indem Sie die Methode `generatePDFOutput` des `OutputClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `TransformationFormat`-Aufzählungswert. Um ein PDF/A-Dokument zu generieren, geben Sie `TransformationFormat.PDFA` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das das Ergebnis der Authentifizierung enthält.

   >[!NOTE]
   >
   >Die Methode `getRecordLevelMetaDataList` des `OutputResult`-Objekts gibt `null` zurück.

   >[!NOTE]
   >
   >Sie können auch ein PDF/A-Dokument erstellen, indem Sie die Methode `generatePDFOutput` des `OutputClient`-Objekts aufrufen. (Siehe [Übergabe von Dokumenten in Content Services (nicht mehr unterstützt) an den Ausgabe-Service](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein Objekt vom Typ `com.adobe.idp.Document`, das den Status der Methode `generatePDFOutput` wiedergibt, indem Sie die Methode `getStatusDoc` des `OutputResult`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.File`-Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um die Inhalte des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt benutzen, das von der Methode `getStatusDoc` zurückgegeben wurde.)

   >[!NOTE]
   >
   >Obwohl der Ausgabe-Service das PDF/A-Dokument an den Speicherort geschrieben wird, den das Argument angibt, das an die Methode `setFileURI` des `PDFOutputOptionsSpec`-Objekts übergeben wird, können Sie das PDF/A-Dokument programmgesteuert abrufen, indem Sie die Methode `getGeneratedDoc` des `OutputResult`-Objekts aufrufen.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Kurzanleitung (SOAP-Modus): Erstellen eines PDF/A-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-a-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Erstellen eines PDF/A-Dokuments mithilfe der Web Service-API {#create-a-pdf-a-document-using-the-web-service-api}

So erstellen Sie ein PDF/A-Dokument mithilfe der Ausgabe-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie mithilfe des Standardkonstruktors ein `OutputServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `OutputServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `OutputServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Daten verwendet, die mit dem PDF/A-Dokument zusammengeführt werden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Legen Sie PDF/A-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Datei-URI-Option fest, indem Sie dem Datenelement `fileURI` des `PDFOutputOptionsSpec`-Objekts einen Zeichenfolgenwert zuweisen, der den Speicherort der PDF-Datei angibt, die der Ausgabe-Service generiert. Die Option „Datei-URI“ bezieht sich auf den J2EE-Programm-Server, der als Host für AEM Forms dient, nicht auf den Client-Computer.

1. Legen Sie Rendering-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie den `PDFAConformance`-Wert fest, indem Sie dem Datenelement `PDFAConformance` des `RenderOptionsSpec`-Objekts einen `PDFAConformance`-Auflistungswert zuweisen. Um beispielsweise Konformitätsstufe A anzugeben, weisen Sie diesem Datenelement `PDFAConformance.A` zu.
   * Legen Sie den Wert `PDFARevisionNumber` fest, indem Sie dem Datenelement `PDFARevisionNumber` des `RenderOptionsSpec`-Objekts einen `PDFARevisionNumber`-Auflistungswert zuweisen. Weisen Sie diesem Datenelement `PDFARevisionNumber.Revision_1` zu.

   >[!NOTE]
   >
   >Die PDF-Version eines PDF/A-Dokuments ist 1.4, unabhängig davon, welchen Wert Sie angeben.

1. Erstellen Sie ein PDF/A-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die Methode `generatePDFOutput` des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein TransformationFormat-Auflistungswert. Um ein PDF-Dokument zu erzeugen, geben Sie `TransformationFormat.PDFA` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB`-Objekt, das von der `generatePDFOutput`-Methode gefüllt wird. Die Methode `generatePDFOutput` füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)
   * Ein `BLOB`-Objekt, das von der Methode `generatePDFOutput` aufgefüllt wird. Die Methode `generatePDFOutput` füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)
   * Ein `OutputResult`-Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)

   >[!NOTE]
   >
   >Sie können auch ein PDF /A-Dokument erstellen, indem Sie die Methode `generatePDFOutput`2 des `OutputClient`-Objekts aufrufen. (Siehe [Übergabe von Dokumenten in Content Services (nicht mehr unterstützt) an den Ausgabe-Service](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der einen XML-Dateispeicherort darstellt, welcher Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `generatePDFOutput` des `OutputServiceService`-Objekts (der achte Parameter) mit Ergebnisdaten gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein Objekt vom Typ `System.IO.BinaryWriter`, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Ausgabe-Service {#passing-documents-located-in-content-services-deprecated-to-the-output-service}

Der Ausgabe-Service rendert ein nicht interaktives PDF-Formular, das auf einem Formularentwurf basiert, der normalerweise als XDP-Datei gespeichert und in Designer erstellt wird. Sie können ein `com.adobe.idp.Document`-Objekt übergeben, das den Formularentwurf für den Ausgabe-Service enthält. Der Ausgabe-Service rendert dann den Formularentwurf im `com.adobe.idp.Document`-Objekt.

Ein Vorteil der Übergabe eines `com.adobe.idp.Document`-Objekts an den Ausgabe-Service besteht darin, dass andere AEM Forms-Service-Vorgänge eine `com.adobe.idp.Document`-Instanz zurückgeben. Das heißt, Sie können eine `com.adobe.idp.Document`-Instanz aus einem anderen Service-Vorgang abrufen und rendern. Angenommen, eine XDP-Datei wird in einem Content Services-Knoten (veraltet) gespeichert, der `/Company Home/Form Designs` heißt, wie in der folgenden Illustration dargestellt.

Sie können Loan.xdp programmgesteuert aus Content Services (veraltet) abrufen und die XDP-Datei innerhalb eines `com.adobe.idp.Document`-Objekts an den Ausgabe-Service übergeben.

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Aufgaben aus, um ein von Content Services (veraltet) gespeichertes Dokument an den Ausgabe-Service zu übergeben:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output- und ein Document Management-Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus Content Services ab (veraltet).
1. Rendern Sie das nicht interaktive PDF-Formular.
1. Führen Sie eine Aktion mit dem Datenstrom aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen eines Ausgabe- und eines Document Management Client API-Objekts**

Bevor Sie einen Ablauf für die Ausgabe-Service-API programmgesteuert ausführen können, müssen Sie ein Ausgabe-Client-API-Objekt erstellen. Da mit diesem Workflow eine XDP-Datei aus Content Services (veraltet) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus Content Services (veraltet)**

Rufen Sie die XDP-Datei aus Content Services (veraltet) ab, indem Sie die Java- oder Webservice-API verwenden. Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document`-Instanz (oder `BLOB`-Instanz, wenn Sie Web-Services verwenden) zurückgegeben. Anschließend können Sie die `com.adobe.idp.Document`-Instanz an den Ausgabe-Service übergeben.

**Rendern des nicht interaktiven PDF-Formulars**

Übergeben Sie zum Rendern eines nicht interaktiven Formulars die `com.adobe.idp.Document`-Instanz, die von Content Services (veraltet) an den Ausgabe-Service zurückgegeben wurde.

>[!NOTE]
>
>Zwei neue Methoden namens `generatePDFOutput2` und `eneratePrintedOutput2` akzeptieren ein `com.adobe.idp.Document`-Objekt, das einen Formularentwurf enthält. Sie können auch `com.adobe.idp.Document` mit dem Formularentwurf beim Senden eines Printstreams an einen Netzwerkdrucker an den Ausgabe-Service übergeben.

**Ausführen einer Aktion mit dem Formulardaten-Stream**

Sie können das nicht interaktive Formular als PDF-Datei speichern. Das Formular kann in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Übergeben von Dokumenten an den Ausgabe-Service mithilfe der Java-API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-java-api)

[Übergeben von Dokumenten an den Output-Service mithilfe der Webservice-API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Erstellen von PDF-Dokumenten mithilfe von Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

### Übergeben von Dokumenten an den Ausgabe-Service mithilfe der Java-API {#pass-documents-to-the-output-service-using-the-java-api}

Übergeben Sie ein Dokument, das von Content Services (veraltet) abgerufen wurde, mithilfe der Ausgabe-Srvice- und Content Services-API (veraltet):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ und „adobe-contentservices-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output- und ein Document Management-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den Formularentwurf aus Content Services ab (veraltet).

   Rufen Sie die Methode `retrieveContent` des `DocumentManagementServiceClientImpl`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgewert, der den Speicher angibt, dem der Inhalt hinzugefügt wird. Der Standardspeicherort ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der die Version angibt. Dieser Wert ist ein optionaler Parameter, und Sie können auch eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.

   Die `retrieveContent`-Methode gibt ein `CRCResult`-Objekt zurück, das die XDP-Datei enthält. Rufen Sie eine `com.adobe.idp.Document`-Instanz durch Aufrufen der Methode `getDocument` des `CRCResult`-Objekts ab.

1. Rendern Sie das nicht interaktive PDF-Formular.

   Rufen Sie die Methode `generatePDFOutput2` des `OutputClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu erzeugen, geben Sie `TransformationFormat.PDF` an.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden.
   * Ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf darstellt (verwenden Sie die Instanz, die von der Methode `getDocument` des `CRCResult`-Objekts zurückgegeben wurde).
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die Methode `generatePDFOutput2` gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

1. Führen Sie eine Aktion mit dem Formulardaten-Stream aus.

   * Rufen Sie ein `com.adobe.idp.Document`-Objekt ab, das das nicht-interaktive Formular darstellt, indem Sie die Methode `getGeneratedDoc` des `OutputResult`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.File`-Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der Methode `getGeneratedDoc` zurückgegeben wird).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Übergeben von Dokumenten an den Output-Service mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Output-Service mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Übergeben von Dokumenten an den Output-Service mithilfe der Webservice-API {#pass-documents-to-the-output-service-using-the-web-service-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) abgerufen wurde, indem Sie den Output-Service und die Content Services-API (nicht mehr unterstützt) (Webservice) verwenden:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da dieses Client-Programm zwei AEM Forms-Services aufruft, erstellen Sie zwei Service-Verweise. Verwenden Sie die folgende WSDL-Definition für die Service-Referenz, die mit dem Output-Service verknüpft ist: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für die Service-Referenz, die mit dem Document Management-Service verknüpft ist: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Da der `BLOB`-Datentyp für beide Service-Referenzen verwendet wird, müssen Sie den `BLOB`-Datentyp vollständig qualifizieren, wenn Sie ihn verwenden. Im entsprechenden Webservice-Schnellstart sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output- und ein Document Management-Client-API-Objekt.

   * Erstellen Sie ein `OutputServiceClient`-Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `OutputServiceClient.Endpoint.Address`-Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `OutputServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode` zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den `DocumentManagementServiceClient`-Service-Client.

1. Rufen Sie den Formularentwurf aus Content Services ab (veraltet).

   Rufen Sie Inhalte ab, indem Sie die Methode `retrieveContent` des `DocumentManagementServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgewert, der den Speicher angibt, dem der Inhalt hinzugefügt wird. Der Standardspeicherort ist `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein Zeichenfolgenwert, der die Version angibt. Dieser Wert ist ein optionaler Parameter, und Sie können auch eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   * Der Ausgabeparameter einer Kennzeichenfolge, der den Wert des Browse-Links speichert.
   * Ein `BLOB`-Ausgabeparameter, der den Inhalt speichert. Sie können diesen Ausgabeparameter verwenden, um den Inhalt abzurufen.
   * Ein `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType`-Ausgabeparameter, der Inhaltsattribute speichert.
   * Ein `CRCResult`-Ausgabeparameter. Statt dieses Objekt zu verwenden, können Sie den `BLOB`-Ausgabeparameter zum Abrufen des Inhalts verwenden.

1. Rendern Sie das nicht interaktive PDF-Formular.

   Rufen Sie die Methode `generatePDFOutput2` des `OutputServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu erzeugen, geben Sie `TransformationFormat.PDF` an.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden.
   * Ein `BLOB`-Objekt, das den Formularentwurf darstellt (verwenden Sie die `BLOB`-Instanz, die von Content Services (nicht mehr unterstützt) zurückgegeben wird).
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB`-Ausgabeobjekt, das von der `generatePDFOutput2`-Methode gefüllt wird. Die `generatePDFOutput2`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).
   * Ein Ausgabe-`OutputResult`-Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).

   Die `generatePDFOutput2`-Methode gibt ein `BLOB`-Objekt zurück, das das nicht interaktive PDF-Formular enthält.

1. Führen Sie eine Aktion mit dem Formulardaten-Stream aus.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Kennzeichenfolgewert, der den Dateispeicherort des interaktiven PDF-Dokuments und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der Methode `generatePDFOutput2` abgerufen wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Übergeben von Dokumenten im Repository an den Ausgabe-Service {#passing-documents-located-in-the-repository-to-the-output-service}

Der Ausgabe-Service rendert ein nicht interaktives PDF-Formular, das auf einem Formularentwurf basiert, der normalerweise als XDP-Datei gespeichert und in Designer erstellt wird. Sie können ein `com.adobe.idp.Document`-Objekt übergeben, das den Formularentwurf für den Ausgabe-Service enthält. Der Ausgabe-Service rendert dann den Formularentwurf im `com.adobe.idp.Document`-Objekt.

Ein Vorteil der Übergabe eines `com.adobe.idp.Document`-Objekts an den Ausgabe-Service besteht darin, dass andere AEM Forms-Service-Vorgänge eine `com.adobe.idp.Document`-Instanz zurückgeben. Das heißt, Sie können eine `com.adobe.idp.Document`-Instanz von einem anderen Service-Vorgang erhalten und sie rendern. Angenommen, eine XDP-Datei wird im AEM Forms-Repository gespeichert, wie in der folgenden Abbildung dargestellt.

![pd_pd_formrepository](assets/pd_pd_formrepository.png)

Der Ordner *FormsFolder* ist ein benutzerdefinierter Speicherort im AEM Forms-Repository (dieser Speicherort ist nur ein Beispiel und standardmäßig nicht vorhanden). In diesem Beispiel befindet sich in diesem Ordner ein Formularentwurf mit dem Namen „Loan.xdp“. Neben dem Formularentwurf können an dieser Stelle auch andere Formularkomponenten wie Bilder gespeichert werden. Der Pfad zu einer Ressource im AEM Forms-Repository lautet:

`Applications/Application-name/Application-version/Folder.../Filename`

Sie können „Loan.xdp“ programmgesteuert aus dem AEM Forms-Repository abrufen und es in einem `com.adobe.idp.Document`-Objekt an den Ausgabe-Service übergeben.

Sie können eine PDF-Datei basierend auf einer XDP-Datei im Repository auf zwei Arten erstellen. Sie können den XDP-Speicherort als Referenz übergeben oder die XDP programmgesteuert aus dem Repository abrufen und innerhalb einer XDP-Datei an den Ausgabe-Service übergeben.

[Kurzanleitung (EJB-Modus): Erstellen eines PDF-Dokuments auf der Grundlage einer XDP-Programmdatei mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api) (hier wird gezeigt, wie Sie den Speicherort der XDP-Datei per Referenz übergeben).

[Schnellstart (EJB-Modus): Übergeben eines Dokuments aus dem AEM Forms-Repository an den Ausgabe-Service mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (hier wird gezeigt, wie Sie die XDP-Datei programmgesteuert aus dem AEM Forms-Repository abrufen und sie innerhalb einer `com.adobe.idp.Document`-Instanz an den Ausgabe-Service übergeben). (In diesem Abschnitt wird beschrieben, wie Sie diese Aufgabe durchführen.)

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

Führen Sie die folgenden Aufgaben aus, um ein vom AEM Forms-Repository abgerufenes Dokument an den Ausgabe-Service zu übergeben:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output- und ein Document Management-Client-API-Objekt. 
1. Rufen Sie den Formularentwurf aus dem AEM Forms-Repository ab.
1. Rendern Sie das nicht interaktive PDF-Formular.
1. Führen Sie eine Aktion mit dem Datenstrom aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen eines Ausgabe- und eines Document Management Client API-Objekts**

Bevor Sie einen Ablauf für die Ausgabe-Service-API programmgesteuert ausführen können, müssen Sie ein Ausgabe-Client-API-Objekt erstellen. Da mit diesem Workflow eine XDP-Datei aus Content Services (veraltet) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus dem AEM Forms-Repository**

Rufen Sie die XDP-Datei mithilfe der Repository-API aus dem AEM Forms-Repository ab. (Siehe [Lesen von Ressourcen](/help/forms/developing/aem-forms-repository.md#reading-resources).)

Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document`-Instanz zurückgegeben (oder einer `BLOB`-Instanz, wenn Sie Web-Services verwenden). Sie können dann die `com.adobe.idp.Document`-Instanz an den Ausgabe-Service übergeben.

**Rendern eines nicht-interaktiven PDF-Formulars**

Um ein nicht-interaktives Formular zu rendern, übergeben Sie die `com.adobe.idp.Document`-Instanz, die mithilfe der AEM Forms-Repository-API zurückgegeben wurde.

>[!NOTE]
>
>Zwei neue Methoden namens `generatePDFOutput2` und `generatePrintedOutput2` akzeptieren ein `com.adobe.idp.Document`-Objekt, das einen Formularentwurf enthält. Sie können auch ein `com.adobe.idp.Document`, das den Formularentwurf enthält, an den Ausgabe-Service übergeben, wenn Sie einen Druck-Stream an einen Netzwerkdrucker senden.

**Ausführen einer Aktion mit dem Formulardaten-Stream**

Sie können das nicht interaktive Formular als PDF-Datei speichern. Das Formular kann in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Übergeben von Dokumenten im Repository an den Ausgabe-Service mithilfe der Java-API](creating-document-output-streams.md#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

ResourceRepositoryClient

### Übergeben von Dokumenten im Repository an den Ausgabe-Service mithilfe der Java-API {#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api}

So übergeben Sie ein aus dem Repository abgerufenes Dokument mithilfe des Ausgabe-Services und der Repository-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ und „adobe-repository-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output- und ein Document Management-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den Formularentwurf aus dem AEM Forms-Repository ab.

   Rufen Sie die Methode `readResourceContent` des `ResourceRepositoryClient`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den URI-Speicherort der XDP-Datei angibt. Beispiel: `/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`. Dieser Wert ist erforderlich. Diese Methode gibt eine `com.adobe.idp.Document`-Instanz zurück, die die XDP-Datei darstellt.

1. Rendern Sie das nicht interaktive PDF-Formular.

   Rufen Sie die Methode `generatePDFOutput2` des `OutputClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu erzeugen, geben Sie `TransformationFormat.PDF` an.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden. Beispiel: `repository:///Applications/FormsApplication/1.0/FormsFolder/`.
   * Ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf darstellt (verwenden Sie die Instanz, die von der Methode `readResourceContent` des `ResourceRepositoryClient`-Objekts zurückgegeben wurde).
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die Methode `generatePDFOutput2` gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

1. Führen Sie eine Aktion mit dem Formulardaten-Stream aus.

   * Rufen Sie ein `com.adobe.idp.Document`-Objekt ab, das das nicht-interaktive Formular darstellt, indem Sie die Methode `getGeneratedDoc` des `OutputResult`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.File`-Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der Methode `getGeneratedDoc` zurückgegeben wird).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Ausgabe-Service mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Erstellen von PDF-Dokumenten mithilfe von Fragmenten {#creating-pdf-documents-using-fragments}

Sie können die Ausgabe- und Assembler-Services verwenden, um einen Ausgabe-Stream, z. B. ein PDF-Dokument, zu erstellen, der auf Fragmenten basiert. Der Assembler-Dienst stellt ein XDP-Dokument zusammen, das auf Fragmenten aus mehreren XDP-Dateien basiert. Das zusammengestellte XDP-Dokument wird an den Ausgabe-Service übergeben, der ein PDF-Dokument erstellt. Obwohl dieser Workflow zeigt, dass ein PDF-Dokument erzeugt wird, kann der Ausgabe-Service für diesen Arbeitsablauf auch andere Ausgabetypen wie ZPL erzeugen. Ein PDF-Dokument wird hier nur zu Demonstrationszwecken verwendet.

Die folgende Abbildung zeigt diesen Workflow.

![cp_cp_outputassemblefragments](assets/cp_cp_outputassemblefragments.png)

Bevor Sie *Erstellen von PDF-Dokumenten mithilfe von Fragmenten* lesen, sollten Sie sich mit der Verwendung des Assembler-Services zum Zusammenstellen mehrerer XDP-Dokumente vertraut machen. (Siehe [Zusammenstellen mehrerer XDP-Fragmente](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments).)

>[!NOTE]
>
>Sie können auch einen vom Assembler-Service zusammengestellten Formularentwurf an den Forms-Service anstelle des Ausgabe-Services übergeben. Der Hauptunterschied zwischen dem Ausgabe-Service und dem Forms-Service besteht darin, dass der Forms-Service interaktive PDF-Dokumente erzeugt, während der Ausgabe-Service nicht-interaktive PDF-Dokumente erzeugt. Außerdem kann der Forms-Service keine druckerbasierten Ausgabe-Streams wie ZPL erzeugen.

>[!NOTE]
>
>Weitere Informationen zum Ausgabe-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Um ein auf Fragmenten basierendes PDF-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output- und Assembler-Client-Objekt.
1. Verwenden Sie den Assembler-Service, um das Design des Formulars zu generieren.
1. Verwenden Sie den Output-Service, um das PDF-Dokument zu generieren.
1. Speichern Sie das Formular als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Ausgabe- und Assembler-Client-Objekts**

Bevor Sie einen Ablauf für die Ausgabe-Service-API programmgesteuert ausführen können, müssen Sie ein Ausgabe-Client-API-Objekt erstellen. Da dieser Workflow für die Erstellung des Formulardesigns den Assembler-Service aufruft, erstellen Sie außerdem ein Assembler-Client-API-Objekt.

**Verwenden des Assembler-Service für die Erstellung des Formulardesigns**

Verwenden Sie den Assembler-Service, um das Formulardesign mithilfe von Fragmenten zu generieren. Der Assembler-Serivce gibt eine `com.adobe.idp.Document`-Instanz zurück, die das Formulardesign enthält.

**Verwenden des Ausgabe-Service für die Erstellung des PDF-Dokuments**

Sie können den Ausgabe-Service verwenden, um ein PDF-Dokument mit dem von Assembler-Service erstellten Formulardesign zu generieren. Übergeben Sie die `com.adobe.idp.Document`-Instanz, die der Assembler-Service an den Ausgabe-Service zurückgegeben hat.

**PDF-Dokument als PDF-Datei speichern**

Nachdem der Ausgabe-Service ein PDF-Dokument generiert hat, können Sie es als PDF-Datei speichern.

**Siehe auch**

[Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-java-api)

[Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Web Service-API](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Assemblieren mehrerer XDP-Fragmente](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments)

[Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)

### Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API {#create-a-pdf-document-based-on-fragments-using-the-java-api}

Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Output Service API und der Assembler Service API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output- und Assembler-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verwenden Sie den Assembler-Service, um das Design des Formulars zu generieren.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt.
   * Ein `java.util.Map`-Objekt, das die XDP-Eingabedateien enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Vorgangsprotokollebene.

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, welches das assemblierte XDP-Dokument enthält. Um das assemblierte XDP-Dokument abzurufen, gehen Sie wie folgt vor:

   * Rufen Sie die Methode `getDocuments` des Objekts `AssemblerResult` auf. Diese Methode gibt ein `java.util.Map`-Objekt zurück.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um das zusammengesetzte XDP-Dokument zu extrahieren.

1. Verwenden Sie den Ausgabe-Service, um das PDF-Dokument zu generieren.

   Rufen Sie die Methode `generatePDFOutput2` des `OutputClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an
   * Einen Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen (z. B. Bilder) befinden
   * Ein `com.adobe.idp.Document`-Objekt, das den Formularentwurf darstellt (verwenden Sie die vom Assembler-Service zurückgegebene Instanz)
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen

   Die `generatePDFOutput2`-Methode gibt ein `OutputResult`-Objekt zurück, das das Ergebnis des Vorgangs enthält

1. Speichern Sie das Formular als PDF-Datei.

   * Rufen Sie ein `com.adobe.idp.Document`-Objekt ab, das das PDF-Dokument darstellt, indem Sie die Methode `getGeneratedDoc` des `OutputResult`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.File`-Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .PDF lautet.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. (Stellen Sie sicher, dass Sie das von der `getGeneratedDoc`-Methode zurückgegebene `com.adobe.idp.Document`-Objekt verwenden.)

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Web Service-API {#create-a-pdf-document-based-on-fragments-using-the-web-service-api}

Erstellen Sie ein PDF-Dokument basierend auf Fragmenten mithilfe der Output Service-API und der Assembler Service-API (Web Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Verwenden Sie die folgende WSDL-Definition für den Service-Verweis, der mit dem Output-Service verknüpft ist:

   ```java
    http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1.
   ```

   Verwenden Sie die folgende WSDL-Definition für die Service-Referenz, die mit dem Assembler-Service verknüpft ist:

   ```java
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   Da der Datentyp `BLOB` für beide Service-Verweise verwendet wird, müssen Sie den Datentyp `BLOB` qualifizieren, wenn Sie ihn verwenden. Im entsprechenden Webservice-Schnellstart sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output- und Assembler-Client-Objekt.

   * Erstellen Sie mithilfe seines Standardkonstruktors ein `OutputServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `OutputServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `OutputServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie den Wert der Konstante `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für das Objekt `AssemblerServiceClient`.

1. Verwenden Sie den Assembler-Service, um das Design des Formulars zu generieren.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * A `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die Methode `invokeDDX` gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Vorgangs sowie alle aufgetretenen Ausnahmen enthält. Um das neu erstellte XDP-Dokument abzurufen, führen Sie die folgenden Aktionen aus:

   * Greifen Sie auf das Feld `documents` des `AssemblerResult`-Objekts zu, welches ein `Map`-Objekt ist, das die resultierenden PDF-Dokumente enthält.
   * Durchlaufen Sie das `Map`-Objekt, um den zusammengesetzten Formularentwurf abzurufen. Wandeln Sie den `value` des Array-Elements in einen `BLOB` um. Übergeben Sie die Instanz dieses `BLOB`s an den Ausgabe-Service.

1. Verwenden Sie den Ausgabe-Service, um das PDF-Dokument zu generieren.

   Rufen Sie die Methode `generatePDFOutput2` des `OutputServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Eine Zeichenfolge, die den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen (z. B. Bilder) befinden.
   * Ein `BLOB`-Objekt, welches das Formulardesign darstellt (verwenden Sie die `BLOB`-Instanz, die vom Assembler-Service zurückgegeben wird).
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formulardesign zusammengeführt werden sollen.
   * Ein Ausgabe `BLOB`-Objekt, das die Methode `generatePDFOutput2` mit Werten füllt. Die Methode `generatePDFOutput2` befüllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).
   * Ein Ausgabe-`OutputResult`-Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).

   Die Methode `generatePDFOutput2` gibt ein `BLOB`-Objekt zurück, das das nicht-interaktive PDF-Formular enthält.

1. Speichern Sie das Formular als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Kennzeichenfolgewert, der den Dateispeicherort des interaktiven PDF-Dokuments und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der Methode `generatePDFOutput2` abgerufen wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Drucken in Dateien {#printing-to-files}

Mit dem Ausgabe-Service können Sie Streams wie PostScript, Printer Control Language (PCL) oder die folgenden Etikettenformate in eine Datei drucken:

* Zebra (ZPL)
* Intermec (IPL)
* Datamax (DPL)
* TecToshiba (TPCL)

Mit dem Ausgabe-Service können Sie XML-Daten mit einem Formularentwurf zusammenführen und das Formular in eine Datei drucken. Die folgende Abbildung zeigt, wie der Ausgabe-Service Laser- und Etikettendateien erstellt.

>[!NOTE]
>
>Informationen zum Senden von Druck-Streams an Drucker finden Sie unter [Senden von Druck-Streams an Drucker](creating-document-output-streams.md#sending-print-streams-to-printers).

>[!NOTE]
>
>Weitere Informationen zum Ausgabe-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Führen Sie die folgenden Schritte aus, um in eine Datei zu drucken:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output-Client-Objekt.
1. Referenzieren Sie eine XML-Datenquelle.
1. Legen Sie die zum Drucken in eine Datei erforderlichen Laufzeitoptionen für das Drucken fest.
1. Drucken Sie den Druck-Stream in eine Datei.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Einbinden von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt wird, der nicht JBOSS ist, müssen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungs-Server sind, auf dem AEM Forms bereitgestellt wird. (Siehe [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)

**Erstellen eines Client-Objekts für die Ausgabe**

Bevor Sie einen Output-Service-Vorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt für den Output-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient`-Objekt. Wenn Sie die Output-Webservice-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Referenzieren einer XML-Datenquelle**

Zum Drucken eines Dokuments, das Daten enthält, müssen Sie eine XML-Datenquelle referenzieren, die XML-Elemente für jedes Formularfeld enthält, das mit Daten gefüllt werden soll. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht übereinstimmen.

**Festlegen der zum Drucken in eine Datei erforderlichen Laufzeitoptionen für das Drucken**

Um in eine Datei zu drucken, müssen Sie die Laufzeitoption „Datei-URI“ festlegen, indem Sie den Speicherort und den Namen der Datei angeben, in die der Ausgabe-Service drucken soll. Um beispielsweise den Ausgabe-Service anzuweisen, eine PostScript-Datei mit dem Namen *MortgageForm.ps* auf C:\Adobe zu drucken, geben Sie C:\Adobe\MortgageForm.ps an.

>[!NOTE]
>
>Es gibt optionale Laufzeitoptionen, die Sie definieren können. Informationen zu allen Optionen, die Sie festlegen können, finden Sie in der `PrintedOutputOptionsSpec`-Klassenreferenz als Teil der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Drucken des Druck-Streams in eine Datei**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die Formulardaten enthält, und Laufzeitoptionen für das Drucken festgelegt haben, können Sie den Ausgabe-Service aufrufen, wodurch die Datei gedruckt wird.

**Abrufen der Ergebnisse des Vorgangs**

Nachdem der Ausgabe-Service einen Vorgang ausgeführt hat, gibt er verschiedene Datenelemente wie XML-Daten zurück, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Drucken in Dateien mithilfe der Java-API](creating-document-output-streams.md#print-to-files-using-the-java-api)

[Drucken in Dateien mithilfe der Webservice-API](creating-document-output-streams.md#print-to-files-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Drucken in Dateien mithilfe der Java-API {#print-to-files-using-the-java-api}

So drucken Sie mit der Ausgabe-API (Java) in eine Datei:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das die XML-Datenquelle darstellt, die zum Auffüllen des Dokuments verwendet wird, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie die zum Drucken in eine Datei erforderlichen Laufzeitoptionen für das Drucken fest.

   * Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die Datei an, indem Sie die Methode `setFileURI` des PrintedOutputOptionsSpec-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen und den Speicherort der Datei angibt. Wenn Sie beispielsweise möchten, dass der Ausgabe-Service in eine PostScript-Datei mit dem Namen „MortgageForm.ps“ unter C:\Adobe druckt, geben Sie „C:\\Adobe\MortgageForm.ps“ an.
   * Geben Sie die Anzahl der zu druckenden Kopien an, indem Sie die Methode `setCopies` des `PrintedOutputOptionsSpec`-Objekts verwenden und einen ganzzahligen Wert für die Anzahl der Exemplare übergeben.

1. Drucken Sie den Druck-Stream in eine Datei.

   Drucken Sie in eine Datei, indem Sie die Methode `generatePrintedOutput` des `OutputClient`-Objekts verwenden und die folgenden Werte übergeben:

   * Ein `PrintFormat`-Enumerationswert, der das zu erstellende Druckstream-Format angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Eine Zeichenfolge, die den Speicherort zugehöriger Begleitdateien wie Bilddateien angibt.
   * Eine Zeichenfolge, die den Speicherort der zu verwendenden XDC-Datei angibt (Sie können `null` übergeben, wenn Sie die XDC-Datei mit Hilfe des `PrintedOutputOptionsSpec`-Objekts festgelegt haben).
   * Das `PrintedOutputOptionsSpec`-Objekt, das die erforderlichen Laufzeitoptionen zum Drucken in eine Datei enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle mit Formulardaten enthält.

   Die Methode `generatePrintedOutput` gibt ein `OutputResult`-Objekt zurück, das das Ergebnis der Authentifizierung enthält.

   >[!NOTE]
   >
   >Die Methode `getRecordLevelMetaDataList` des `OutputResult`-Objekts gibt `null` zurück.

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein Objekt vom Typ `com.adobe.idp.Document`, das den Status der Methode `generatePrintedOutput` angibt, indem Sie die Methode `getStatusDoc` des `OutputResult`-Objekts aufrufen (das `OutputResult`-Objekt wurde von der Methode `generatePrintedOutput` zurückgegeben).
   * Erstellen Sie ein `java.io.File`-Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der Methode `getStatusDoc` zurückgegeben wird).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Drucken in eine Datei mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-printing-to-a-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Drucken in Dateien mithilfe der Webservice-API {#print-to-files-using-the-web-service-api}

Drucken Sie mit der Output API (Web-Service) in eine Datei:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie mithilfe des Standardkonstruktors ein `OutputServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `OutputServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `OutputServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Formulardaten verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und eine Zeichenfolge übergeben, die den Speicherort der XML-Datei mit den Formulardaten angibt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Befüllen Sie das `BLOB`-Objekt mit dem Inhalt des Byte-Arrays durch Zuweisen der Eigenschaft `binaryData`.

1. Legen Sie die zum Drucken in eine Datei erforderlichen Laufzeitoptionen für das Drucken fest.

   * Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die Datei an, indem Sie dem Datenelement `fileURI` des `PrintedOutputOptionsSpec`-Objekts einen Zeichenfolgenwert zuweisen, der den Speicherort und den Namen der Datei darstellt. Wenn der Ausgabe-Service beispielsweise in eine PostScript-Datei mit dem Namen *MortgageForm.ps* im Ordner „C:\Adobe“ drucken soll, geben Sie „C:\\Adobe\MortgageForm.ps“ an.
   * Geben Sie die Anzahl der zu druckenden Kopien an, indem Sie dem Datenelement `copies` des `PrintedOutputOptionsSpec`-Objekts einen ganzzahligen Wert zuweisen, der die Anzahl der Kopien darstellt.

1. Drucken Sie den Druck-Stream in eine Datei.

   Drucken Sie in eine Datei, indem Sie die Methode `generatePrintedOutput` des `OutputServiceService`-Objekts verwenden und die folgenden Werte übergeben:

   * Ein `PrintFormat`-Enumerationswert, der das zu erstellende Druckstream-Format angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Eine Zeichenfolge, die den Speicherort zugehöriger Begleitdateien wie Bilddateien angibt.
   * Ein Zeichenfolgenwert, der den Speicherort der zu verwendenden XDC-Datei angibt (Sie können `null` übergeben, wenn Sie die XDC-Datei angegeben haben, die mithilfe des `PrintedOutputOptionsSpec`-Objekts verwendet werden soll).
   * Das `PrintedOutputOptionsSpec`-Objekt, das zum Drucken in eine Datei erforderliche Drucklaufzeitoptionen enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle mit den Formulardaten enthält.
   * Ein `BLOB`-Objekt, das von der `generatePDFOutput`-Methode gefüllt wird. Die Methode `generatePDFOutput` füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)
   * Ein `BLOB`-Objekt, das von der Methode `generatePDFOutput` aufgefüllt wird. Die Methode `generatePDFOutput` füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)
   * Ein `OutputResult`-Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der einen XML-Dateispeicherort mit den Ergebnisdaten darstellt. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `generatePDFOutput` des `OutputServiceService`-Objekts (der achte Parameter) mit Ergebnisdaten gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein Objekt vom Typ `System.IO.BinaryWriter`, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Senden von Druck-Streams an Drucker {#sending-print-streams-to-printers}

Sie können den Ausgabe-Service verwenden, um Druck-Streams wie PostScript, Printer Control Language (PCL) oder die folgenden Etikettenformate an Netzwerkdrucker zu senden:

* Zebra (ZPL)
* Intermec (IPL)
* Datamax (DPL)
* TecToshiba (TPCL)

Mit dem Ausgabe-Service können Sie XML-Daten mit einem Formularentwurf zusammenführen und das Formular als Druck-Stream ausgeben. Sie können beispielsweise einen PostScript-Druck-Stream erstellen und an einen Netzwerkdrucker senden. Die folgende Abbildung zeigt, wie der Ausgabe-Service Druck-Streams an Netzwerkdrucker sendet.

>[!NOTE]
>
>Um zu demonstrieren, wie ein Druck-Stream an einen Netzwerkdrucker gesendet wird, wird in diesem Abschnitt ein PostScript-Druck-Stream mithilfe des SharedPrinter-Druckerprotokolls an einen Netzwerkdrucker gesendet.

>[!NOTE]
>
>Weitere Informationen zum Ausgabe-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Um einen Druck-Stream an einen Netzwerkdrucker zu senden, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output-Client-Objekt.
1. Referenzieren Sie eine XML-Datenquelle.
1. Festlegen von Laufzeitoptionen für das Drucken
1. Rufen Sie ein zu druckendes Dokument ab.
1. Senden Sie das Dokument an einen Netzwerkdrucker.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt wird, der nicht JBOSS ist, müssen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungs-Server sind, auf dem AEM Forms bereitgestellt wird. 

**Erstellen eines Client-Objekts für die Ausgabe**

Bevor Sie einen Ausgabe-Service-Vorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt für den Ausgabe-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient`-Objekt. Wenn Sie die Output-Webservice-API verwenden, erstellen Sie ein `OutputServiceClient`-Objekt.

**Referenzieren einer XML-Datenquelle**

Zum Drucken eines Dokuments, das Daten enthält, müssen Sie eine XML-Datenquelle referenzieren, die XML-Elemente für jedes Formularfeld enthält, das mit Daten gefüllt werden soll. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht übereinstimmen.

**Festlegen von Laufzeitoptionen für das Drucken**

Sie können die Laufzeitoptionen beim Senden eines Druck-Streams an einen Drucker festlegen, einschließlich der folgenden Optionen:

* **Kopien**: Gibt die Anzahl der an den Drucker zu sendenden Kopien an. Der Standardwert ist 1.
* **Heften**: Eine XCI-Option wird festgelegt, wenn ein Hefter verwendet wird. Diese Option kann im Konfigurationsmodell durch das Heftelement angegeben werden und wird nur für PS- und PCL-Drucker verwendet.
* **OutputJog**: Eine XCI-Option wird festgelegt, wenn die Ausgabeseiten verschoben werden sollen (physische Verschiebung im Ausgabefach). Diese Option ist nur für PS- und PCL-Drucker verfügbar.
* **OutputBin**: XCI-Wert, der verwendet wird, um dem Druckertreiber die Auswahl des geeigneten Ausgabefachs zu ermöglichen.

>[!NOTE]
>
>Informationen zu allen Laufzeitoptionen, die Sie festlegen können, finden Sie in der `PrintedOutputOptionsSpec`-Klassenreferenz.

**Abrufen eines zu druckenden Dokuments**

Rufen Sie einen Druck-Streams ab, der an einen Drucker gesendet werden soll. Sie können beispielsweise eine PostScript-Datei abrufen und an einen Drucker senden.

Sie können eine PDF-Datei senden, wenn Ihr Drucker PDF unterstützt. Ein Problem beim Senden eines PDF-Dokuments an einen Drucker besteht jedoch darin, dass jeder Druckerhersteller über eine andere Implementierung des PDF-Interpreters verfügt. Das heißt, einige Druckerhersteller verwenden die Adobe PDF-Interpretation, aber dies hängt vom Drucker ab. Andere Drucker haben einen eigenen PDF-Interpreter. Daher können die Druckergebnisse variieren.

Eine weitere Einschränkung beim Senden eines PDF-Dokuments an einen Drucker besteht darin, dass es nur gedruckt wird. Dabei kann nicht auf Duplex, Papierfachauswahl und Heften zugegriffen werden, außer durch Einstellungen am Drucker.

Um ein zu druckendes Dokument abzurufen, verwenden Sie die Methode `generatePrintedOutput`. In der folgenden Tabelle sind die Content-Typen aufgeführt, die für einen bestimmten Druck-Stream bei Verwendung der Methode `generatePrintedOutput` festgelegt werden.

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
   <td><p>Erstellt standardmäßig eine Datei „dpl203.xdc“ oder einen benutzerdefinierten xdc-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>DPL300DPI </p></td>
   <td><p>Erstellt einen DPL-Ausgabestream mit 300 DPI.</p></td>
  </tr>
  <tr>
   <td><p>DPL406DPI </p></td>
   <td><p>Erstellt einen DPL-Ausgabestream mit 400 DPI.</p></td>
  </tr>
  <tr>
   <td><p>DPL600DPI </p></td>
   <td><p>Erstellt einen DPL-Ausgabestream mit 600 DPI.</p></td>
  </tr>
  <tr>
   <td><p>GenericColorPCL </p></td>
   <td><p>Erstellt einen generischen Farb-PCL-Ausgabestream (5c).</p></td>
  </tr>
  <tr>
   <td><p>GenericPSLevel3 </p></td>
   <td><p>Erstellt einen generischen PostScript-Level-3-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>IPL </p></td>
   <td><p>Erstellt einen benutzerdefinierten IPL-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>IPL300DPI </p></td>
   <td><p>Erstellt einen IPL-Ausgabestream mit 300 DPI.</p></td>
  </tr>
  <tr>
   <td><p>IPL400DPI </p></td>
   <td><p>Erstellt einen IPL-Ausgabestream mit 400 DPI.</p></td>
  </tr>
  <tr>
   <td><p>PCL </p></td>
   <td><p>Erstellt einen generischen Monochrom-PCL-Ausgabestream (5e).</p></td>
  </tr>
  <tr>
   <td><p>PostScript </p></td>
   <td><p>Erstellt einen generischen PostScript-Level-2-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>TPCL </p></td>
   <td><p>Erstellt einen benutzerdefinierten TPCL-Ausgabestream.</p></td>
  </tr>
  <tr>
   <td><p>TPCL305DPI </p></td>
   <td><p>Erstellt einen TPCL-Ausgabestream mit 305 DPI.</p></td>
  </tr>
  <tr>
   <td><p>TPCL600DPI </p></td>
   <td><p>Erstellt einen TPCL-Ausgabestream mit 600 DPI.</p></td>
  </tr>
  <tr>
   <td><p>ZPL </p></td>
   <td><p>Erstellt einen ZPL-Ausgabestream mit 203 DPI.</p></td>
  </tr>
  <tr>
   <td><p>ZPL300DPI </p></td>
   <td><p>Erstellt einen ZPL-Ausgabestream mit 300 DPI.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Sie können auch einen Druckstream mithilfe der `generatePrintedOutput2`-Methode an einen Drucker senden. Die Schnellstarts, die mit dem Abschnitt zum Senden von Druckstreams an Drucker verknüpft sind, verwenden jedoch die `generatePrintedOutput`-Methode.

**Senden des Druckstroms an einen Netzwerkdrucker**

Nachdem Sie ein zu druckendes Dokument abgerufen haben, können Sie den Ausgabeservice aufrufen, wodurch ein Druckstream an einen Netzwerkdrucker gesendet wird. Damit der Ausgabeservice den Drucker erfolgreich finden kann, müssen Sie sowohl den Druckserver als auch den Druckernamen angeben. Darüber hinaus müssen Sie auch das Druckprotokoll angeben.

>[!NOTE]
>
>Wenn PDFG auf dem Formular-Server installiert ist und auf dem Server Windows Server 2008 ausgeführt wird, können Sie die SharedPrinter-Eigenschaft nicht verwenden. Verwenden Sie in diesem Fall ein anderes Druckerprotokoll.

>[!NOTE]
>
>Wenn Sie einen Netzwerkdrucker verwenden und der Zugriffsmechanismus SharedPrinter ist, müssen Sie den vollständigen Netzwerkpfad des Druckers angeben. Senden Sie einen Druck-Stream mithilfe der Java-API an einen Netzwerkdrucker.

Senden Sie mithilfe der Ausgabe API (Java) einen Druck-Stream an einen Netzwerkdrucker:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Client-Objekts für die Ausgabe

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren einer XML-Datenquelle

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das die XML-Datenquelle darstellt, die zum Auffüllen des Dokuments verwendet wird, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Laufzeitoptionen für das Drucken

   Erstellen Sie ein `PrintedOutputOptionsSpec`-Objekt, das Laufzeitoptionen für das Drucken darstellt. Sie können zum Beispiel die Anzahl der zu druckenden Kopien angeben, indem Sie die Methode `setCopies` des `PrintedOutputOptionsSpec`-Objekts aufrufen.

   >[!NOTE]
   >
   >Sie können den Paginierungswert nicht mit der Methode `setPagination` des `PrintedOutputOptionsSpec`-Objekts festlegen, wenn Sie einen ZPL-Druck-Stream erzeugen. Ebenso können Sie die folgenden Optionen für einen ZPL-Druckstream nicht festlegen: OutputJog, PageOffset und Staple. Die Methode `setPagination` ist für die Erzeugung von PostScript nicht gültig. Sie gilt nur für die Erzeugung von PCL.

1. Abrufen eines zu druckenden Dokuments

   * Rufen Sie ein zu druckendes Dokument ab, indem Sie die Methode `generatePrintedOutput` des `OutputClient`-Objekts aufrufen und die folgenden Werte übergeben:

      * Ein `PrintFormat`-Auflistungswert, der den Druck-Stream angibt. Um beispielsweise einen PostScript-Druck-Stream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
      * Ein string-Wert, der den Namen des Formularentwurfs angibt.
      * Ein Zeichenfolgenwert, der den Speicherort zugehöriger Begleitdateien (z. B. Grafikdateien) angibt.
      * Ein Zeichenfolgenwert, der den Speicherort der zu verwendenden XDC-Datei angibt.
      * Das `PrintedOutputOptionsSpec`-Objekt, das Laufzeitoptionen enthält, die zum Drucken in eine Datei erforderlich sind.
      * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle darstellt, welche die mit dem Formularentwurf zusammenzuführenden Formulardaten enthält.

     Diese Methode gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

   * Erstellen Sie ein Objekt vom Typ `com.adobe.idp.Document`, das an den Drucker gesendet werden soll, indem Sie die Methode `getGeneratedDoc` des `OutputResult`-Objekts aufrufen. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück.

1. Senden Sie den Druck-Stream an einen Netzwerkdrucker.

   Senden Sie den Druck-Stream an einen Netzwerkdrucker, indem Sie die Methode `sendToPrinter` des `OutputClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document`-Objekt, das den an den Drucker zu sendenden Druck-Stream darstellt.
   * Ein `PrinterProtocol`-Auflistungswert, der das zu verwendende Druckerprotokoll angibt. Um beispielsweise das SharedPrinter-Protokoll anzugeben, übergeben Sie `PrinterProtocol.SharedPrinter`.
   * Ein Zeichenfolgenwert, der den Namen des Druck-Servers angibt. Wenn beispielsweise der Name des Druck-Servers PrintSever1 lautet, übergeben Sie `\\\PrintSever1`.
   * Ein Zeichenfolgenwert, der den Namen des Druckers angibt. Wenn beispielsweise der Name des Druckers Printer1 lautet, übergeben Sie `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >Die Methode `sendToPrinter` wurde in Version 8.2.1 der AEM Forms-API hinzugefügt.

### Senden eines Druck-Streams an einen Drucker mithilfe der Webservice-API {#send-a-print-stream-to-a-printer-using-the-web-service-api}

So senden Sie einen Druck-Stream an einen Netzwerkdrucker, indem Sie die Ausgabe-API (Webservice) verwenden:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie mithilfe des Standardkonstruktors ein `OutputServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `OutputServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `OutputServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Formulardaten verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XML-Datei angibt, die Formulardaten enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Ermitteln Sie die Länge des Byte-Arrays, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Laufzeitoptionen für das Drucken.

   Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden. Sie können zum Beispiel die Anzahl der zu druckenden Kopien angeben, indem Sie dem Datenelement `copies` des `PrintedOutputOptionsSpec`-Objekts einen ganzzahligen Wert zuweisen, der die Anzahl der Kopien darstellt.

   >[!NOTE]
   >
   >Sie können den Seitenumbruchswert nicht mit dem Datenelement `pagination` des `PrintedOutputOptionsSpec`-Objekts festlegen, wenn Sie einen ZPL-Druck-Stream erzeugen. Ebenso können Sie die folgenden Optionen für einen ZPL-Druck-Stream nicht festlegen: OutputJog, PageOffset und Staple. Die Methode `pagination` ist für die Erzeugung von PostScript nicht gültig. Sie gilt nur für die Erzeugung von PCL.

1. Rufen Sie ein zu druckendes Dokument ab.

   * Rufen Sie ein zu druckendes Dokument ab, indem Sie die Methode `generatePrintedOutput` des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

      * Ein `PrintFormat`-Auflistungswert, der den Druck-Stream angibt. Um beispielsweise einen PostScript-Druck-Stream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
      * Ein string-Wert, der den Namen des Formularentwurfs angibt.
      * Ein Zeichenfolgenwert, der den Speicherort zugehöriger Begleitdateien (z. B. Grafikdateien) angibt.
      * Ein Zeichenfolgenwert, der den Speicherort der zu verwendenden XDC-Datei angibt.
      * Das `PrintedOutputOptionsSpec`-Objekt, das Laufzeitoptionen für das Drucken enthält, die beim Senden eines Druck-Streams an einen Netzwerkdrucker verwendet werden.
      * Das `BLOB`-Objekt, das die XML-Datenquelle enthält, die Formulardaten enthält.
      * Ein `BLOB`-Objekt, das von der `generatePrintedOutput`-Methode gefüllt wird. Die Methode `generatePrintedOutput` füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)
      * Ein `BLOB`-Objekt, das von der Methode `generatePrintedOutput` aufgefüllt wird. Die Methode `generatePrintedOutput` füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)
      * Ein `OutputResult`-Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)

   * Erstellen Sie ein Objekt vom Typ `BLOB`, das an den Drucker gesendet werden soll, indem Sie den Wert der Methode `generatedDoc` des `OutputResult`-Objekts abrufen. Diese Methode gibt ein `BLOB`-Objekt zurück, das PostScript-Daten enthält, die von der Methode `generatePrintedOutput` zurückgegeben werden.

1. Senden Sie den Druck-Stream an einen Netzwerkdrucker.

   Senden Sie den Druck-Stream an einen Netzwerkdrucker, indem Sie die Methode `sendToPrinter` des `OutputClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, das den an den Drucker zu sendenden Druck-Stream darstellt.
   * Ein `PrinterProtocol`-Auflistungswert, der das zu verwendende Druckerprotokoll angibt. Um beispielsweise das SharedPrinter-Protokoll anzugeben, übergeben Sie `PrinterProtocol.SharedPrinter`.
   * Ein `bool` Wert, der angibt, ob der vorherige Parameterwert verwendet werden soll. Übergeben Sie den Wert `true`. (Dieser Parameterwert ist nur für den Aufruf des Webservices erforderlich.)
   * Ein Zeichenfolgenwert, der den Namen des Druck-Servers angibt. Wenn beispielsweise der Name des Druckservers PrintSever1 lautet, übergeben Sie `\\\PrintSever1`.
   * Ein Zeichenfolgenwert, der den Namen des Druckers angibt. Wenn beispielsweise der Name des Druckers Printer1 lautet, übergeben Sie `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >Die Methode `sendToPrinter` wurde in Version 8.2.1 der AEM Forms-API hinzugefügt.

## Erstellen mehrerer Ausgabedateien {#creating-multiple-output-files}

Der Ausgabe-Service kann für jeden Datensatz in einer XML-Datenquelle oder in einer Datei, die alle Datensätze enthält, separate Dokumente erstellen (diese Funktion ist die Standardfunktion). Angenommen, zehn Datensätze befinden sich in einer XML-Datenquelle und Sie weisen den Ausgabe-Service an, mithilfe der Ausgabe-Service-API für jeden Datensatz separate PDF-Dokumente (oder andere Ausgabetypen) zu erstellen. Dann erzeugt der Ausgabe-Service zehn PDF-Dokumente. (Anstatt Dokumente zu erstellen, können Sie auch mehrere Druck-Streams an einen Drucker senden.)

Die folgende Abbildung zeigt auch, wie der Ausgabe-Service eine XML-Datendatei verarbeitet, die mehrere Datensätze enthält. Nehmen wir jedoch an, dass Sie den Ausgabe-Service anweisen, ein einziges PDF-Dokument zu erstellen, das alle Dateneinträge enthält. In diesem Fall erzeugt der Ausgabe-Service ein Dokument, das alle Einträge enthält.

Die folgende Abbildung zeigt, wie der Ausgabe-Service eine XML-Datendatei verarbeitet, die mehrere Datensätze enthält. Angenommen, Sie weisen den Ausgabe-Service an, für jeden Datensatz ein eigenes PDF-Dokument zu erstellen. In diesem Fall erzeugt der Ausgabe-Service für jeden Datensatz ein separates PDF-Dokument.

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

Beachten Sie, dass das XML-Element, das jeden Datensatz startet und beendet, `LoanRecord` ist. Dieses XML-Element wird durch die Anwendungslogik referenziert, die mehrere Dateien erzeugt.

>[!NOTE]
>
>Weitere Informationen zum Ausgabe-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

Um mehrere PDF-Dateien auf der Grundlage einer XML-Datenquelle zu erstellen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output-Client-Objekt.
1. Referenzieren Sie eine XML-Datenquelle.
1. Legen Sie PDF-Laufzeitoptionen fest.
1. Legen Sie Rendering-Laufzeitoptionen fest.
1. Generieren Sie mehrere PDF-Dateien.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Einbinden von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt wird, der nicht JBOSS ist, müssen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungs-Server sind, auf dem AEM Forms bereitgestellt wird. 

**Erstellen eines Output-Client-Objekts**

Bevor Sie einen Output-Service-Vorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt für den Output-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient`-Objekt. Wenn Sie die Output-Webservice-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Referenzieren einer XML-Datenquelle**

Referenzieren Sie eine XML-Datenquelle, die mehrere Datensätze enthält. Ein XML-Element muss verwendet werden, um die Datensätze zu trennen. In der Beispiel-XML-Datenquelle, die oben in diesem Abschnitt gezeigt wird, heißt beispielsweise das XML-Element, das Datensätze trennt, `LoanRecord`.

Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht übereinstimmen.

**Festlegen von PDF-Laufzeitoptionen**

Legen Sie die folgenden Laufzeitoptionen fest, damit der Ausgabe-Service erfolgreich mehrere Dateien erstellen kann, die auf einer XML-Datenquelle basieren:

* **Viele Dateien**: Gibt an, ob der Ausgabe-Service ein einzelnes Dokument oder mehrere Dokumente erstellt. Sie können „true“ oder „false“ angeben. Um ein separates Dokument für jeden Datensatz in der XML-Datenquelle zu erstellen, geben Sie „true“ an.
* **Datei-URI**: Gibt den Speicherort der Dateien an, die der Ausgabe-Service erzeugt. Angenommen, Sie geben C:\\Adobe\forms\Loan.pdf an. In diesem Fall erstellt der Ausgabe-Service eine Datei mit dem Namen „Loan.pdf“ und legt diese Datei im Ordner „C:\\Adobe\forms folder“ ab. Wenn mehrere Dateien vorliegen, lauten die Dateinamen „Loan0001.pdf“, „Loan0002.pdf“, „Loan0003.pdf“ usw. Wenn Sie einen Dateispeicherort angeben, werden die Dateien auf dem Server und nicht auf dem Client-Computer abgelegt.
* **Datensatzname**: Gibt den Namen des XML-Elements in der Datenquelle an, das die Datensätze trennt. In der Beispiel-XML-Datenquelle, die oben in diesem Abschnitt gezeigt wird, hat beispielsweise das XML-Element, das Datensätze trennt, den Namen `LoanRecord`. (Anstatt als Laufzeitoption den Datensatznamen festzulegen, können Sie auch die Datensatzebene festlegen, indem Sie ihr einen numerischen Wert zuweisen, der die Elementebene angibt, welche Datensätze enthält. Sie können jedoch nur entweder den Datensatznamen oder die Datensatzebene festlegen. Sie können nicht beide Werte festlegen.)

**Festlegen von Laufzeitoptionen für das Rendern**

Sie können beim Erstellen mehrerer Dateien Laufzeitoptionen für das Rendern festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu erforderlichen Laufzeitoptionen für die Ausgabe), können Sie damit Aufgaben wie die Verbesserung der Leistung des Ausgabe-Services ausführen. Beispielsweise können Sie die Leistung verbessern, indem Sie den Formularentwurf zwischenspeichern, den der Ausgabe-Service verwendet.

Wenn der Ausgabe-Service Batch-Datensätze verarbeitet, liest er inkrementell Daten, die mehrere Datensätze enthalten. Das heißt, der Ausgabe-Service liest die Daten in den Speicher ein und gibt sie im Laufe der Verarbeitung des Datensatz-Batches wieder frei. Der Ausgabe-Service lädt Daten inkrementell, wenn eine der zwei Laufzeitoptionen festgelegt ist. Wenn Sie für die Laufzeitoption den Datensatznamen festlegen, liest der Ausgabe-Service die Daten inkrementell. Wenn Sie für die Laufzeitoption die Datensatzebene auf 2 oder höher setzen, liest der Ausgabe-Service die Daten ebenfalls auf inkrementelle Weise.

Sie können steuern, ob der Ausgabe-Service das Laden inkrementell durchführen soll, indem Sie `PDFOutputOptionsSpec` oder die Methode `setLazyLoading` des `PrintedOutputOptionSpec`-Objekts verwenden. Sie können den Wert `false` an diese Methode übergeben, um das inkrementelle Laden zu deaktivieren.

**Erzeugen mehrerer PDF-Dateien**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die mehrere Datensätze enthält, und Laufzeitoptionen festgelegt haben, können Sie den Ausgabe-Service aufrufen, wodurch mehrere Dateien erzeugt werden. Bei der Erzeugung mehrerer Einträge gibt die Methode `getGeneratedDoc` des `OutputResult`-Objekts `null` zurück.

**Abrufen der Ergebnisse des Vorgangs**

Nachdem der Ausgabe-Service einen Vorgang ausgeführt hat, werden XML-Daten zurückgegeben, die angeben, ob der Vorgang erfolgreich war. Die folgende XML-Datei wird vom Ausgabe-Service zurückgegeben. In diesem Fall generiert der Ausgabe-Service 42 Dokumente.

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

1. Einschließen von Projektdateien&quot;

   Fügen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Client-Objekts für die Ausgabe

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren einer XML-Datenquelle

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das die XML-Datenquelle mit mehreren Datensätzen darstellt, indem es seinen Konstruktor verwendet und eine Zeichenfolge mit dem Speicherort der XML-Datei übergibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von PDF-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option „Viele Dateien“ fest, indem Sie die Methode `setGenerateManyFiles` des `PDFOutputOptionsSpec`-Objekts aufrufen. Übergeben Sie beispielsweise den Wert `true`, um den Ausgabe-Service anzuweisen, für jeden Datensatz in der XML-Datenquelle eine separate PDF-Datei zu erstellen. (Wenn Sie `false` übergeben, generiert der Output-Dienst ein einzelnes PDF-Dokument, das alle Datensätze enthält).
   * Legen Sie die Datei-URI-Option fest, indem Sie die Methode `setFileUri` des `PDFOutputOptionsSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort der Dateien angibt, die der Ausgabe-Service generiert. Die Option „Datei-URI“ ist bezieht sich auf den J2EE-Anwendungs-Server, auf dem AEM Forms gehostet wird, nicht zum Client-Computer. 
   * Legen Sie die Option „Name des Eintrags“ fest, indem Sie die Methode `setRecordName` des `OutputOptionsSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des XML-Elements in der Datenquelle angibt, das die Dateneinträge trennt. (Ein Beispiel für eine XML-Datenquelle finden Sie weiter oben in diesem Abschnitt. Der Name des XML-Elements, das die Datensätze trennt, ist LoanRecord).

1. Einstellen der Laufzeitoptionen für das Rendern

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Speichern Sie den Formularentwurf zwischen, um die Leistung des Ausgabe-Service zu verbessern, indem Sie `setCacheEnabled` für das `RenderOptionsSpec`-Objekt aufrufen und einen `Boolean`-Wert `true` übergeben.

1. Generieren mehrerer PDF-Dateien

   Generieren Sie mehrere PDF-Dateien, indem Sie die Methode `generatePDFOutput` des `OutputClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Einen `TransformationFormat` Enum-Wert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die Methode `generatePDFOutput` gibt ein `OutputResult`-Objekt zurück, das die Ergebnisse des Vorgangs enthält.

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie ein `java.io.File`-Objekt, das eine XML-Datei mit den Ergebnisse der `generatePDFOutput`-Methode darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der Methode `applyUsageRights` zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen mehrerer PDF-Dateien mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-multiple-pdf-files-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen mehrerer PDF-Dateien mithilfe der Web-Service-API {#create-multiple-pdf-files-using-the-web-service-api}

Erstellen mehrerer PDF-Dateien mithilfe der Output API (Web-Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie mithilfe des Standardkonstruktors ein `OutputServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `OutputServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `OutputServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB`-Objekt wird zum Speichern von Formulardaten verwendet, die mehrere Datensätze enthalten.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort der XML-Datei darstellt, die mehrere Datensätze enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt durch Zuweisen seines `MTOM`-Felds mit dem Inhalt des Byte-Arrays.

1. Legen Sie PDF-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option für viele Dateien fest, indem Sie dem Datenelement `generateManyFiles` des `OutputOptionsSpec`-Objekts einen booleschen Wert zuweisen. Weisen Sie beispielsweise den Wert `true` diesem Datenelement zu, um den Ausgabeservice anzuweisen, eine separate PDF-Datei für jeden Datensatz in der XML-Datenquelle zu erstellen. (Wenn Sie `false` diesem Datenelement zuweisen, generiert der Ausgabeservice eine einzelne PDF-Datei, die alle Datensätze enthält.)
   * Legen Sie die Datei-URI-Option fest, indem Sie dem Datenelement `fileURI` des `OutputOptionsSpec`-Objekts einen Zeichenfolgenwert zuweisen, der den Speicherort der PDF-Datei(en) angibt, die der Ausgabe-Service generiert. Die Option „Datei-URI“ ist bezieht sich auf den J2EE-Anwendungs-Server, auf dem AEM Forms gehostet wird, nicht zum Client-Computer. 
   * Legen Sie die Eintragsnamen-Option fest, indem Sie dem Datenelement `recordName` des `OutputOptionsSpec`-Objekts einen Zeichenfolgenwert zuweisen, der den Namen des XML-Elements in der Datenquelle angibt, das die Dateneinträge trennt.
   * Legen Sie die Kopien-Option fest, indem Sie dem Datenelement `copies` des `OutputOptionsSpec`-Objekts einen ganzzahligen Wert zuweisen, der die Anzahl der Kopien angibt, die der Ausgabe-Service generiert.

1. Legen Sie Rendering-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Speichern Sie den Formularentwurf zwischen, um die Leistung des Ausgabe-Service zu verbessern, indem Sie dem Datenelement `cacheEnabled` des `RenderOptionsSpec`-Objekts den Wert `true` zuweisen.

1. Generieren Sie mehrere PDF-Dateien.

   Erstellen Sie mehrere PDF-Dateien, indem Sie die Methode `generatePDFOutput` des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein TransformationFormat-Enum-Wert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB`-Objekt, das von der `generatePDFOutput`-Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben.
   * Ein `BLOB`-Objekt, das von der `generatePDFOutput`-Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit Ergebnisdaten.
   * Ein `OutputResult`-Objekt, das die Ergebnisse des Vorgangs enthält.

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `generatePDFOutput` des `OutputServiceService`-Objekts (der achte Parameter) mit Ergebnisdaten gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `binaryData` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein Objekt vom Typ `System.IO.BinaryWriter`, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Erstellen von Suchregeln {#creating-search-rules}

Sie können Suchregeln erstellen, die dazu führen, dass der Ausgabe-Service Eingabedaten prüft und verschiedene auf dem Dateninhalt basierende Formulardesigns verwendet, um die Ausgabe zu generieren. Wenn sich beispielsweise der Text *Hypothek* in den Eingabedaten befindet, kann der Ausgabe-Service einen Formularentwurf mit dem Namen Mortgage.xdp verwenden. Ähnlich kann der Ausgabe-Service einen Formularentwurf verwenden, der als „AutomobileLoan.xdp“ gespeichert wird, wenn sich der Text *automobile* in den Eingabedaten befindet. Auch wenn der Ausgabe-Service unterschiedliche Ausgabetypen erzeugen kann, wird in diesem Abschnitt davon ausgegangen, dass der Ausgabe-Service eine PDF-Datei erzeugt. Das folgende Diagramm zeigt, wie der Ausgabe-Service eine PDF-Datei erzeugt, indem er eine XML-Datendatei verarbeitet und einen von vielen Formularentwürfen verwendet.

Darüber hinaus kann der Ausgabe-Service Dokumentenpakete generieren, bei denen mehrere Datensätze im Datensatz bereitgestellt werden, jeder Datensatz einem Formularentwurf zugeordnet wird und ein einziges Dokument erzeugt wird, das aus mehreren Formularentwürfen besteht.

![cs_outputbatchmanyformdesigns2](assets/cs_outputbatchmanyformdesigns2.png)

>[!NOTE]
>
>Weitere Informationen zum Ausgabe-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Um den Ausgabe-Service anzuweisen, beim Erzeugen eines Dokuments Suchregeln zu verwenden, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output-Client-Objekt.
1. Referenzieren Sie eine XML-Datenquelle.
1. Definieren Sie Suchregeln.
1. Legen Sie PDF-Laufzeitoptionen fest.
1. Legen Sie Rendering-Laufzeitoptionen fest.
1. Generieren Sie ein PDF-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Einbinden von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt wird, der nicht JBOSS ist, müssen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungs-Server sind, auf dem AEM Forms bereitgestellt wird. 

**Erstellen eines Client-Objekts für die Ausgabe**

Bevor Sie einen Ausgabe-Service-Vorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt für den Ausgabe-Service erstellen.

**Referenzieren einer XML-Datenquelle**

Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Es ist nicht erforderlich, die Reihenfolge der Anzeige der XML-Elemente einzuhalten, solange alle XML-Elemente angegeben sind.

**Definieren von Suchregeln**

Um Suchregeln zu definieren, definieren Sie ein oder mehrere Textmuster, nach denen der Ausgabe-Service in den Eingabedaten suchen soll. Für jedes von Ihnen definierte Textmuster geben Sie einen entsprechenden Formularentwurf an, der verwendet wird, wenn das Textmuster gefunden wird. Wenn ein Textmuster gefunden wird, verwendet der Ausgabe-Service den entsprechenden Formularentwurf, um die Ausgabe zu erzeugen. Ein Beispiel für ein Textmuster ist *Hypothek*.

>[!NOTE]
>
>Wenn keine Textmuster gefunden werden, wird das Standardformular verwendet. Stellen Sie sicher, dass sich alle von Ihnen verwendeten Formularentwürfe im Inhaltsstamm befinden.

**Festlegen von PDF-Laufzeitoptionen**

Legen Sie die folgenden PDF-Laufzeitoptionen fest, damit der Ausgabe-Service erfolgreich ein PDF-Dokument erstellen kann, das auf mehreren Formularentwürfen basiert:

* **Datei-URI**: Gibt den Namen und Speicherort der PDF-Datei an, die der Ausgabe-Service erzeugt.
* **Regeln**: Gibt von Ihnen definierte Regeln an.
* **LookAHead**: Gibt die Anzahl der Bytes an, die ab dem Anfang der Eingabedatendatei verwendet werden sollen, um nach den definierten Textmustern zu suchen. Der Standardwert ist 500 Byte.

**Festlegen von Laufzeitoptionen für das Rendern**

Sie können beim Erstellen von PDF-Dateien Laufzeitoptionen für das Rendern festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu PDF-Laufzeitoptionen), können Sie damit Aufgaben wie die Verbesserung der Leistung des Ausgabe-Services ausführen. Beispielsweise können Sie die Leistung verbessern, indem Sie den Formularentwurf zwischenspeichern, den der Ausgabe-Service verwendet.

**Erzeugen eines PDF-Dokuments**

Nachdem Sie eine gültige XML-Datenquelle referenziert und Laufzeitoptionen festgelegt haben, können Sie den Ausgabe-Service aufrufen, um ein PDF-Dokument zu erzeugen. Wenn der Ausgabe-Service ein bestimmtes Textmuster in den Eingabedaten findet, verwendet er den entsprechenden Formularentwurf. Wenn kein Textmuster verwendet wird, verwendet der Ausgabe-Service den Standardformularentwurf.

**Abrufen der Ergebnisse des Vorgangs**

Nachdem der Ausgabe-Service einen Vorgang ausgeführt hat, gibt er XML-Daten zurück, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen von Suchregeln mithilfe der Java-API {#create-search-rules-using-the-java-api}

So erstellen Sie Suchregeln mithilfe der Ausgabe-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das die XML-Datenquelle darstellt, die zum Füllen des PDF-Dokuments verwendet wird, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Definieren Sie Suchregeln.

   * Erstellen Sie ein Objekt `Rule`, indem Sie den Konstruktor verwenden.
   * Definieren Sie ein Textmuster, indem Sie die Methode `setPattern` des `Rule`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der ein Textmuster angibt.
   * Definieren Sie den entsprechenden Formularentwurf, indem Sie die Methode `setForm` des `Rule`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Formularentwurfs angibt.

   >[!NOTE]
   >
   >Wiederholen Sie für jedes Textmuster, das Sie definieren möchten, die vorherigen drei Teilschritte.

   * Erstellen Sie ein `java.util.List`-Objekt mithilfe eines `java.util.ArrayList`-Konstruktors.
   * Rufen Sie für jedes `Rule`-Objekt, das Sie erstellt haben, die Methode `add` des `java.util.List`-Objekts auf und übergeben Sie das `Rule`-Objekt.

1. Legen Sie PDF-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Namen und den Speicherort der PDF-Datei an, die der Ausgabe-Sevice generiert, indem Sie die Methode `setFileURI` des `PDFOutputOptionsSpec`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der PDF-Datei angibt. Die Datei-URI-Option ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, nicht zum Clientcomputer.
   * Legen Sie die von Ihnen definierten Regeln fest, indem Sie die Methode `setRules` des `PDFOutputOptionsSpec`-Objekts aufrufen. Übergeben Sie das `java.util.List`-Objekt, das die `Rule`-Objekte enthält.
   * Legen Sie die Anzahl der Bytes fest, die nach den definierten Textmustern gescannt werden sollen, indem Sie die Methode `setLookAhead` des `PDFOutputOptionsSpec`-Objekts aufrufen. Übergeben Sie einen ganzzahligen Wert, der die Anzahl der Bytes darstellt.

1. Legen Sie Rendering-Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Speichern Sie den Formularentwurf zwischen, um die Leistung des Ausgabe-Service zu verbessern, indem Sie `setCacheEnabled` des `RenderOptionsSpec`-Objekts aufrufen und `true` übergeben.

1. Generieren Sie ein PDF-Dokument.

   Generieren Sie ein PDF-Dokument, das auf mehreren Formularentwürfen basiert, indem Sie die Methode `generatePDFOutput` des `OutputClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein Zeichenfolgenwert, der den Namen des Standardformularentwurfs angibt. Das heißt, der Formularentwurf, der verwendet wird, wenn ein Textmuster nicht gefunden wird.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich die Formularentwürfe befinden.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Rendering-Laufzeitoptionen enthält.
   * Das `com.adobe.idp.Document`-Objekt, das die Formulardaten enthält, die vom Ausgabe-Service nach den definierten Textmustern durchsucht werden.

   Die `generatePDFOutput`-Methode gibt ein `OutputResult`-Objekt zurück, das das Ergebnis der Authentifizierung enthält.

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie ein Objekt vom Typ `com.adobe.idp.Document`, das den Status der Methode `generatePDFOutput` wiedergibt, indem Sie die Methode `getStatusDoc` des `OutputResult`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.File`-Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateierweiterung .xml lautet.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der Methode `getStatusDoc` zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen von Suchregeln mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen von Suchregeln mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen von Suchregeln mithilfe der Web-Service-API {#create-search-rules-using-the-web-service-api}

Erstellen Sie Suchregeln mithilfe der Ausgabe-API (Web-Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie mithilfe des Standardkonstruktors ein `OutputServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `OutputServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `OutputServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Daten verwendet, die in das PDF-Dokument integriert werden sollen.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, in dem der Dateispeicherort des zu verschlüsselnden PDF-Dokuments und der Modus enthalten sind, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt mit den Inhalten des Byte-Arrays, indem Sie diese dem `MTOM`-Feld des Objekts zuweisen.

1. Definieren Sie Suchregeln.

   * Erstellen Sie ein Objekt `Rule`, indem Sie den Konstruktor verwenden.
   * Definieren Sie ein Textmuster, indem Sie dem Datenelement `pattern` des `Rule`-Objekts einen Zeichenfolgenwert zuweisen, der ein Textmuster festlegt.
   * Definieren Sie den entsprechenden Formularentwurf, indem Sie dem Datenelement `form` des `Rule`-Objekts einen Zeichenfolgenwert zuweisen, der den Formularentwurf festlegt.

   >[!NOTE]
   >
   >Wiederholen Sie für jedes Textmuster, das Sie definieren möchten, die vorherigen drei Teilschritte.

   * Erstellen Sie ein `MyArrayOf_xsd_anyType`-Objekt zum Abspeichern der Regeln.
   * Weisen Sie jedes `Rule`-Objekt einem Element des `MyArrayOf_xsd_anyType`-Arrays zu. Rufen Sie die Methode `Add` des `MyArrayOf_xsd_anyType`-Objekts für jedes `Rule`-Objekt auf.

1. Festlegen von PDF-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Datei-URI-Option fest, indem Sie dem Datenelement `fileURI` des `PDFOutputOptionsSpec`-Objekts einen Zeichenfolgenwert zuweisen, der den Speicherort der PDF-Datei angibt, die der Ausgabe-Service generiert. Die Option „Datei-URI“ ist bezieht sich auf den J2EE-Anwendungs-Server, auf dem AEM Forms gehostet wird, nicht zum Client-Computer. 
   * Legen Sie die Kopien-Option fest, indem Sie dem Datenelement `copies` des `PDFOutputOptionsSpec`-Objekts einen ganzzahligen Wert zuweisen, der die Anzahl der Kopien angibt, die der Ausgabe-Service generiert.
   * Legen Sie die von Ihnen definierten Regeln fest, indem Sie dem Datenelement `rules` des `PDFOutputOptionsSpec`-Objekts das `MyArrayOf_xsd_anyType`-Objekt zuweisen, das die Regeln enthält.
   * Legen Sie die Anzahl der Bytes fest, die nach den definierten Textmustern gescannt werden sollen, indem Sie der Datenmethode `lookAhead` des `PDFOutputOptionsSpec`-Objekts einen ganzzahligen Wert zuweisen, der die Anzahl der zu scannenden Bytes bestimmt.

1. Einstellen der Laufzeitoptionen für das Rendern

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Speichern Sie den Formularentwurf zwischen, um die Leistung des Ausgabe-Service zu verbessern, indem Sie dem Datenelement `cacheEnabled` des `RenderOptionsSpec`-Objekts den Wert `true` zuweisen.

   >[!NOTE]
   >
   >Sie können die Version des PDF-Dokuments nicht festlegen, indem Sie das Element `pdfVersion` des `RenderOptionsSpec`-Objekts verwenden, falls das Eingabedokument ein Acrobat-Formular ist. Für das PDF-Ausgabedokument wird dieselbe PDF-Version des Acrobat-Formulars verwendet. Ebenso können Sie die Option „PDF-Datei mit Tags“ nicht mithilfe der Methode `taggedPDF` des `RenderOptionsSpec`-Objekts festlegen, wenn das Eingabedokument ein Acrobat-Formular ist.

   >[!NOTE]
   >
   >Sie können die Option „Linearisiertes PDF“ nicht mithilfe des Datenelements `linearizedPDF` des `RenderOptionsSpec`-Objekts festlegen, wenn das PDF-Eingabedokument zertifiziert oder digital signiert ist. Weitere Informationen finden Sie unter [Digitales Signieren von PDF-Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).

1. Ein PDF-Dokument generieren

   Erstellen Sie ein PDF-Dokument, indem Sie die Methode `generatePDFOutput` des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Einen `TransformationFormat`-Aufzählungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein Zeichenfolgenwert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * Ein `PDFOutputOptionsSpec`-Objekt, das PDF-Laufzeitoptionen enthält.
   * Ein `RenderOptionsSpec`-Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Das `BLOB`-Objekt, das die XML-Datenquelle mit den Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ein `BLOB`-Objekt, das von der `generatePDFOutput`-Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).
   * Ein `BLOB`-Objekt, das von der `generatePDFOutput`-Methode gefüllt wird. Die `generatePDFOutput`-Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).
   * Ein `OutputResult`-Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).

   >[!NOTE]
   >
   >Beim Generieren eines PDF-Dokuments durch Aufrufen der Methode `generatePDFOutput` können Sie keine Daten mit einem XFA-PDF-Formular fusionieren, das signiert oder zertifiziert wurde oder Verwendungsrechte enthält. Weitere Informationen zu Verwendungsrechten finden Sie unter [Verwendungsrechte für PDF-Dokumente aktivieren](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort einer XML-Datei mit Ergebnisdaten darstellt. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `generatePDFOutput` des `OutputServiceService`-Objekts (der achte Parameter) mit Ergebnisdaten gefüllt wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein Objekt vom Typ `System.IO.BinaryWriter`, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Reduzieren von PDF-Dokumenten {#flattening-pdf-documents}

Sie können den Ausgabe-Service verwenden, um ein interaktives PDF-Dokument in ein nicht interaktives PDF-Dokument umzuwandeln. Interaktive PDF-Dokumente ermöglichen es dem Benutzer, Daten in die PDF-Dokumentfelder einzugeben bzw. darin zu ändern. Der Prozess der Umwandlung eines interaktiven PDF-Dokuments in ein nicht interaktives PDF-Dokument wird als *Reduzieren* bezeichnet. Wenn ein PDF-Dokument reduziert wird, kann ein Benutzer die in den Feldern des Dokuments enthaltenen Daten nicht ändern. Dies kann ein Grund dafür sein, PDF-Dokumente zu reduzieren.

Sie können die folgenden Arten von PDF-Dokumenten reduzieren:

* Interaktive XFA-PDF-Dokumente
* Acrobat Forms

Der Versuch, ein PDF-Dokument, bei dem es sich um ein nicht interaktives PDF-Dokument handelt, zu reduzieren, verursacht eine Ausnahme.

>[!NOTE]
>
>Weitere Informationen zum Ausgabe-Service finden Sie unter [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-9}

Führen Sie die folgenden Schritte aus, um ein interaktives PDF-Dokument in ein nicht interaktives PDF-Dokument zu reduzieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Output-Client-Objekt.
1. Rufen Sie ein interaktives PDF-Dokument ab.
1. Wandeln Sie das PDF-Dokument um.
1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt wird, der nicht JBOSS ist, müssen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungs-Server sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Ausgabe-Client-Objekts**

Bevor Sie einen Output-Service-Vorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt für den Output-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `OutputClient`-Objekt. Wenn Sie die Ausgabe-Web-Service-API verwenden, erstellen Sie ein `OutputServiceService`-Objekt.

**Abrufen eines interaktiven PDF-Dokuments**

Rufen Sie ein interaktives PDF-Dokument ab, das Sie in ein nicht interaktives PDF-Dokument umwandeln möchten. Der Versuch, ein nicht interaktives PDF-Dokument umzuwandeln, verursacht eine Ausnahme.

**Umwandeln des PDF-Dokuments**

Nachdem Sie ein interaktives PDF-Dokument abgerufen haben, können Sie es in ein nicht interaktives PDF-Dokument umwandeln. Der Ausgabe-Service gibt ein nicht interaktives PDF-Dokument zurück.

**Speichern des nicht interaktiven PDF-Dokuments als PDF-Datei**

Sie können das nicht interaktive PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Reduzieren eines PDF-Dokuments mithilfe der Java-API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-java-api)

[Reduzieren eines PDF-Dokuments mithilfe der Web-Service-API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Reduzieren eines PDF-Dokuments mithilfe der Java-API {#flatten-a-pdf-document-using-the-java-api}

Reduzieren Sie ein interaktives PDF-Dokument mithilfe der Ausgabe-API (Java) auf ein nicht interaktives PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-output-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `OutputClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein interaktives PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das umzuwandelnde interaktive PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der interaktiven PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Wandeln Sie das PDF-Dokument um.

   Wandeln Sie das interaktive PDF-Dokument in ein nicht interaktives PDF-Dokument um, indem Sie die Methode `transformPDF` des `OutputServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das interaktive PDF-Dokument enthält.
   * Ein `TransformationFormat`-Aufzählungswert. Um ein nicht interaktives PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein `PDFARevisionNumber`-Aufzählungswert, der die Revisionsnummer angibt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null` angeben.
   * Ein Zeichenfolgenwert, der die Änderungsnummer und das Jahr darstellt, getrennt durch einen Doppelpunkt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null` angeben.
   * Ein `PDFAConformance`-Aufzählungswert, der die PDF/A-Konformitätsstufe darstellt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null` angeben.

   Die `transformPDF`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf lautet.
   * Rufen Sie die Methode `copyToFile` des `Document`-Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der Methode `transformPDF` zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Umwandeln eines PDF-Dokuments mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Umwandeln eines PDF-Dokuments mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Reduzieren eines PDF-Dokuments mithilfe der Web-Service-API {#flatten-a-pdf-document-using-the-web-service-api}

Reduzieren Sie ein interaktives PDF-Dokument mithilfe der Ausgabe-API (Web-Service) auf ein nicht interaktives PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output-Client-Objekt.

   * Erstellen Sie mithilfe des Standardkonstruktors ein `OutputServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `OutputServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `OutputServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `OutputServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein interaktives PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um das interaktive PDF-Dokument zu speichern.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des interaktiven PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Wandeln Sie das PDF-Dokument um.

   Wandeln Sie das interaktive PDF-Dokument in ein nicht interaktives PDF-Dokument um, indem Sie die Methode `transformPDF` des `OutputClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, das das interaktive PDF-Dokument enthält.
   * Ein `TransformationFormat`-Aufzählungswert. Um ein nicht interaktives PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF` an.
   * Ein `PDFARevisionNumber`-Aufzählungswert, der die Revisionsnummer angibt.
   * Ein boolescher Wert, der angibt, ob der `PDFARevisionNumber`-Aufzählungswert verwendet wird. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `false` angeben.
   * Ein Zeichenfolgenwert, der die Änderungsnummer und das Jahr darstellt, getrennt durch einen Doppelpunkt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null` angeben.
   * Ein `PDFAConformance`-Aufzählungswert, der die PDF/A-Konformitätsstufe darstellt.
   * Boolescher Wert, der angibt, ob der `PDFAConformance`-Aufzählungswert verwendet wird. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `false` angeben.

   Die `transformPDF`-Methode gibt ein `BLOB`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen von dessen Konstruktor und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des nicht interaktiven PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `transformPDF`-Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
