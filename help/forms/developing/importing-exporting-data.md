---
title: Importieren und Exportieren von Daten
seo-title: Importing and Exporting Data
description: Verwenden Sie den Form Data Integration-Service, um Daten in ein PDF-Formular zu importieren, und die Java-API oder die Web-Service-API, um Daten aus einem PDF-Formular zu exportieren.
seo-description: Use the Form Data Integration service to import data into a PDF form and export data from a PDF form using the Java API and Web Service API.
uuid: 94ccb6f2-6e5f-43ea-a954-9a4402871a17
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 2e783745-c986-45ba-8e65-7437d114ca38
role: Developer
exl-id: 96310e0a-8e95-4a55-9508-5298b8d67f83
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '2778'
ht-degree: 100%

---

# Importieren und Exportieren von Daten {#importing-and-exporting-data}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Über den Form Data Integration-Service {#about-the-form-data-integration-service}

Der Form Data Integration-Service erlaubt sowohl das Importieren von Daten in ein PDF-Formular als auch das Exportieren von Daten aus einem PDF-Formular. Für das Importieren und Exportieren werden zwei PDF-Formulartypen unterstützt:

* Ein Acrobat-Formular (erstellt in Acrobat) ist ein PDF-Dokument mit Formularfeldern.
* Ein Adobe XML-Formular (erstellt in Designer) ist ein PDF-Dokument, das der Adobe XML Forms Architecture (XFA) (Architektur für XML-Formulare) entspricht.

Je nach PDF-Formulartyp können Formulardaten in einem der folgenden Formate vorliegen:

* Als XFDF-Datei, die eine XML-Version des Acrobat-Formulardatenformats darstellt.
* Als XDP-Datei, die eine XML-Datei mit Formularfelddefinitionen darstellt. Diese kann auch Formularfelddaten und eine eingebettete PDF-Datei enthalten. Eine von Designer generierte XDP-Datei kann nur verwendet werden, wenn in ihr ein Base-64-kodiertes PDF-Dokument eingebettet ist.

Sie können diese Aufgaben mit dem Form Data Integration-Service erledigen:

* Importieren von Daten in PDF-Formulare. Weitere Informationen finden Sie unter [Importieren von Formulardaten](importing-exporting-data.md#importing-form-data).
* Exportieren von Daten aus PDF-Formularen. Weitere Informationen finden Sie unter [Exportieren von Formulardaten](importing-exporting-data.md#exporting-form-data).

>[!NOTE]
>
>Weitere Informationen zum Form Data Integration-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Importieren von Formulardaten {#importing-form-data}

Sie können Formulardaten in interaktive PDF-Formulare importieren, indem Sie den Form Data Integration-Service verwenden. Ein interaktives PDF-Formular ist ein PDF-Dokument, das ein oder mehrere Felder zum Sammeln von Informationen von einem Benutzer oder zum Anzeigen von benutzerdefinierten Informationen enthält. Der Form Data Integration-Service unterstützt keine Berechnungen, Validierungen oder Skripts in Formularen.

Um Daten in ein Formular zu importieren, das in Designer erstellt wurde, müssen Sie eine gültige XDP-XML-Datenquelle angeben. Schauen wir uns einmal das folgende Formular für einen Kreditantrag als Beispiel an.

![ie_ie_loanformdata](assets/ie_ie_loanformdata.png)

Um Daten in dieses Formular zu importieren, müssen Sie über eine gültige XDP-XML-Datenquelle verfügen, die dem Formular entspricht. Sie können keine beliebige XML-Datenquelle verwenden, um Daten mithilfe des Form Data Integration-Services in ein Formular zu importieren. Der Unterschied zwischen einer beliebigen XML-Datenquelle und einer XDP-XML-Datenquelle besteht darin, dass eine XDP-Datenquelle der XML Forms Architecture (XFA) entspricht. Die folgende XML-Datei stellt eine XDP-XML-Datenquelle dar, die dem Beispielformular für einen Hypothekenantrag entspricht.

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

>[!NOTE]
>
>Weitere Informationen zum Form Data Integration-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um Daten in ein PDF-Formular zu importieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client für den Form Data Integration-Service.
1. Referenzieren Sie ein PDF-Formular.
1. Referenzieren Sie eine XML-Datenquelle.
1. Importieren von Daten in das PDF-Formular.
1. Speichern Sie das Formular als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Weitere Informationen über den Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Clients für den Form Data Integration-Service**

Bevor Sie Daten programmgesteuert in eine PDF-Formular-Client-API importieren können, müssen Sie einen Client für den Data Integration-Service erstellen. Beim Erstellen eines Service-Clients bestimmen Sie Verbindungseinstellungen, die zum Aufrufen eines Services erforderlich sind. Weitere Informationen finden Sie unter [Einrichten von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren eines PDF-Formulars**

Um Daten in ein PDF-Formular zu importieren, müssen Sie entweder auf ein in Designer erstelltes XML-Formular oder auf ein in Acrobat erstelltes Acrobat-Formular verweisen.

**Referenzieren einer XML-Datenquelle**

Um Formulardaten zu importieren, müssen Sie auf eine gültige Datenquelle verweisen. Um Daten in ein in Designer erstelltes XFA-XML-Formular zu importieren, müssen Sie eine XDP-XML-Datenquelle verwenden. Wenn Sie auf ein Acrobat-Formular verweisen, müssen Sie eine XFDF-Datenquelle verwenden. Sie müssen für jedes Feld, in das Sie Daten importieren möchten, einen Wert angeben. Falls ein Element in der XML-Datenquelle keinem Feld im Formular entspricht, wird das Element ignoriert.

**Importieren der Daten in das PDF-Formular**

Nachdem Sie ein PDF-Formular und eine gültige XML-Datenquelle angegeben haben, können Sie die Daten in das PDF-Formular importieren.

**Speichern des Formulars als PDF-Datei**

Nachdem Sie Daten in ein Formular importiert haben, können Sie das Formular als PDF-Datei speichern. Nachdem Sie das Formular als PDF-Datei gespeichert haben, kann ein Benutzer das Formular in Adobe Reader oder Acrobat öffnen, um die darin importierten Daten zu sehen.

**Siehe auch**

[Importieren von Formulardaten mit der Java-API](importing-exporting-data.md#import-form-data-using-the-java-api)

[Importieren von Formulardaten mit der Web-Service-API](importing-exporting-data.md#import-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Lernprogramme zur Form Data Integration-Service-API](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Exportieren von Formulardaten](importing-exporting-data.md#exporting-form-data)

### Importieren von Formulardaten mit der Java-API {#import-form-data-using-the-java-api}

Importieren von Formulardaten mit der Form Data Integration-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-formdataintegration-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client für den Form Data Integration-Service.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Formular.

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Ort angibt, an dem das PDF-Formular gespeichert ist.
   * Verwenden Sie den `com.adobe.idp.Document`-Konstruktor, um ein `com.adobe.idp.Document`-Objekt zu erstellen, in dem das PDF-Formular gespeichert wird. Übergeben Sie das `java.io.FileInputStream`-Objekt mit dem PDF-Formular an den Konstruktor.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XML-Datei angibt, die in das Formular zu importierende Daten enthält.
   * Verwenden Sie den `com.adobe.idp.Document`-Konstruktor, um ein `com.adobe.idp.Document`-Objekt zu erstellen, das Formulardaten speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt mit Formulardaten an den Konstruktor.

1. Importieren von Daten in das PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `importData`-Methode des `FormDataIntegrationClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, in dem das PDF-Formular gespeichert wird.
   * Das `com.adobe.idp.Document`-Objekt, in dem Formulardaten gespeichert werden.

   Die `importData`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, in dem ein PDF-Formular gespeichert ist, das die Daten aus der XML-Datenquelle enthält.

1. Speichern Sie das Formular als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung „.pdf“ ist.
   * Rufen Sie die `copyToFile`-Methode des `Document`-Objekts auf, um die Inhalte des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `importData`-Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Importieren von Formulardaten mit der Java-API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importieren von Formulardaten mit der Web-Service-API {#import-form-data-using-the-web-service-api}

Importieren von Formulardaten mithilfe der Form Data Integration-API (Web-Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client für den Form Data Integration-Service.

   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `FormDataIntegrationClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL zu dem AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`.) Sie brauchen das `lc_version`-Attribut nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `FormDataIntegrationClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.Password` das entsprechende Passwort zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein PDF-Formular.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. In diesem `BLOB`-Objekt wird das PDF-Formular gespeichert.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Formulars und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld die Inhalte des Byte-Arrays zuweisen.

1. Referenzieren Sie eine XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird verwendet, um die in das Formular importierten Daten zu speichern.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XML-Datei angibt, in der sich Daten befinden, die importiert werden sollen, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie auf die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts zugreifen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld die Inhalte des Byte-Arrays zuweisen.

1. Importieren von Daten in das PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `importData`-Methode des `FormDataIntegrationClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, in dem das PDF-Formular gespeichert wird.
   * Das `BLOB`-Objekt, in dem die Daten des Formulars gespeichert werden.

   Die `importData`-Methode gibt ein `BLOB`-Objekt zurück, in dem ein PDF-Formular gespeichert ist, das die Daten aus der XML-Datenquelle enthält.

1. Speichern Sie das Formular als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Ort angibt, an dem die PDF-Datei gespeichert ist.
   * Erstellen Sie ein Byte-Array, das die von der `importData`-Methode zurückgegebenen Daten aus dem `BLOB`-Objekt aufnimmt. Füllen Sie das Byte-Array, indem Sie den Wert des `MTOM`-Felds des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie die Inhalte des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Exportieren von Formulardaten {#exporting-form-data}

Sie können Formulardaten aus einem interaktiven PDF-Formular mithilfe des Form Data Integration-Services exportieren. Das Format der exportierten Daten hängt vom Formulartyp ab. Wenn das Formular ein in Acrobat erstelltes Acrobat-Formular ist, dann werden die Daten im XFDF-Format exportiert. Wenn das Formular ein in Designer erstelltes XML-Formular ist, dann werden die Daten im XDP-Format exportiert.

>[!NOTE]
>
>Weitere Informationen zum Form Data Integration-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Schritte aus, um Daten aus einem PDF-Formular zu exportieren:

1. Projektdateien einschließen
1. Erstellen Sie einen Client für den Form Data Integration-Service.
1. Referenzieren Sie ein PDF-Formular.
1. Exportieren Sie Daten aus dem PDF-Formular.
1. Speichern Sie die exportierten Daten als XML-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Clients für den Form Data Integration-Service**

Bevor Sie Daten programmgesteuert in eine PDF FormClient-API importieren können, müssen Sie einen Client für den Data Integration Service erstellen. Beim Erstellen eines Service-Clients bestimmen Sie Verbindungseinstellungen, die zum Aufrufen eines Services erforderlich sind. Für weitere Informationen: [Einrichten von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren eines PDF-Formulars**

Um Daten aus einem PDF-Formular zu exportieren, müssen Sie auf ein in Designer oder Acrobat erstelltes PDF-Formular verweisen, das die Formulardaten enthält. Wenn Sie versuchen, Daten aus einem leeren PDF-Formular zu exportieren, erhalten Sie ein leeres XML-Schema.

**Exportieren von Daten aus dem PDF-Formular**

Nachdem Sie auf ein PDF-Formular verwiesen haben, das Formulardaten enthält, können Sie diese exportieren. Die Daten werden in ein XML-Schema exportiert, das auf dem Formular basiert.

**Die Formulardaten als XML-Datei speichern**

Nach dem Exportieren von Formulardaten können Sie diese als XML-Datei speichern. Sobald Sie die Daten als XML-Datei gespeichert haben, können Sie diese in einem XML-Betrachter öffnen, um die Formulardaten anzuzeigen.

**Siehe auch**

[Exportieren von Formulardaten mit der Java-API](importing-exporting-data.md#export-form-data-using-the-java-api)

[Exportieren von Formulardaten mit der Web-Service-API](importing-exporting-data.md#export-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Lernprogramme zur Form Data Integration-Service-API](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Importieren von Formulardaten](importing-exporting-data.md#importing-form-data)

### Exportieren von Formulardaten mit der Java API {#export-form-data-using-the-java-api}

Exportieren Sie Formulardaten mithilfe der Form Data Integration API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-formdataintegration-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client für den Form Data Integration-Service.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Formular.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie dessen Konstruktor verwenden und übergeben Sie eine Zeichenfolge, die den Speicherort des zu exportierenden PDF-Formulars angibt.
   * Erstellen Sie anhand des `com.adobe.idp.Document`-Konstruktors ein `com.adobe.idp.Document`-Objekt, in dem das PDF-Formular gespeichert wird. Übergeben Sie an den Konstruktor das `java.io.FileInputStream`-Objekt, in dem das PDF-Formular enthalten ist.

1. Exportieren Sie Daten aus dem PDF-Formular.

   Exportieren Sie Formulardaten, indem Sie die `exportData`-Methode des `FormDataIntegrationClient`-Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, in dem das PDF-Formular gespeichert ist. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, in dem Formulardaten als XML-Schema gespeichert werden.

1. Speichern Sie das Formular als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .xml ist.
   * Rufen Sie die `copyToFile`-Methode des `Document`-Objekts auf, um die Inhalte des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `exportData`-Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Exportieren von Formulardaten mit der Java-API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportieren von Formulardaten mit der Web-Service-API {#export-form-data-using-the-web-service-api}

Exportieren von Formulardaten mithilfe der Form Data Integration-API (Web-Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   * Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client für den Form Data Integration-Service.

   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `FormDataIntegrationClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, in dem die WSDL an den AEM Forms-Service übergeben wird (z. B. `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`.) Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie eine Servicereferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `FormDataIntegrationClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.Password` das entsprechende Passwort zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein PDF-Formular.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird verwendet, um das PDF-Formular zu speichern, aus dem Daten exportiert werden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Formulars und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekt gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts aufrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts anwenden und dabei das Byte-Array, die Startposition und die Länge des zu lesenden Streams übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie die Inhalte des Byte-Arrays seinem `MTOM`-Feld zuweisen.

1. Exportieren Sie Daten aus dem PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `exportData`-Methode des `FormDataIntegrationClient`-Objekts aufrufen und das `BLOB`-Objekt übergeben, in dem das PDF-Formular gespeichert ist. Diese Methode gibt ein `BLOB`-Objekt zurück, in dem Formulardaten als XML-Schema gespeichert werden.

1. Speichern Sie das Formular als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort der XML-Datei darstellt.
   * Erstellen Sie ein Byte-Array, in dem der Dateninhalt des `BLOB`-Objekt gespeichert wird, das von der `exportData`-Methode zurückgegeben wird. Füllen Sie das Byte-Array, indem Sie den Wert des `MTOM`-Felds des `BLOB`-Objekt aufrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie die Inhalte des Byte-Arrays in eine XML-Datei, indem Sie die `Write`-Methode des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
