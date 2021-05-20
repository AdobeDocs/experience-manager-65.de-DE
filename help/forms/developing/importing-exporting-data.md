---
title: Importieren und Exportieren von Daten
seo-title: Importieren und Exportieren von Daten
description: Verwenden Sie den Formulardatenintegrationsdienst, um Daten in ein PDF-Formular zu importieren und mithilfe der Java-API und der Web Service-API Daten aus einem PDF-Formular zu exportieren.
seo-description: Verwenden Sie den Formulardatenintegrationsdienst, um Daten in ein PDF-Formular zu importieren und mithilfe der Java-API und der Web Service-API Daten aus einem PDF-Formular zu exportieren.
uuid: 94ccb6f2-6e5f-43ea-a954-9a4402871a17
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 2e783745-c986-45ba-8e65-7437d114ca38
role: Developer
exl-id: 96310e0a-8e95-4a55-9508-5298b8d67f83
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2810'
ht-degree: 5%

---

# Importieren und Exportieren von Daten {#importing-and-exporting-data}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Über den Formulardatenintegrationsdienst {#about-the-form-data-integration-service}

Der Formulardatenintegrationsdienst kann Daten in ein PDF-Formular importieren und Daten aus einem PDF-Formular exportieren. Die Ein- und Ausfuhrvorgänge unterstützen zwei Arten von PDF forms:

* Ein (in Acrobat erstelltes) Acrobat-Formular ist ein PDF-Dokument mit Formularfeldern.
* Ein in Designer erstelltes Adobe XML-Formular ist ein PDF-Dokument, das der XML Adobe XML Forms Architecture (XFA) entspricht.

Je nach Typ des PDF-Formulars können Formulardaten in einem der folgenden Formate vorhanden sein:

* Als XFDF-Datei, die eine XML-Version des Acrobat-Formulardatenformats darstellt.
* Als XDP-Datei, die eine XML-Datei mit Formularfelddefinitionen darstellt. Diese kann auch Formularfelddaten und eine eingebettete PDF-Datei enthalten. Eine von Designer generierte XDP-Datei kann nur verwendet werden, wenn sie ein eingebettetes base-64-kodiertes PDF-Dokument enthält.

Sie können diese Aufgaben mit dem Formulardatenintegrationsdienst ausführen:

* Importieren Sie Daten in PDF forms. Weitere Informationen finden Sie unter [Importieren von Formulardaten](importing-exporting-data.md#importing-form-data).
* Exportieren Sie Daten aus PDF forms. Weitere Informationen finden Sie unter [Exportieren von Formulardaten](importing-exporting-data.md#exporting-form-data).

>[!NOTE]
>
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Importieren von Formulardaten {#importing-form-data}

Sie können Formulardaten mit dem Formulardatenintegrationsdienst in interaktive PDF forms importieren. Ein interaktives PDF-Formular ist ein PDF-Dokument, das ein oder mehrere Felder zum Erfassen von Informationen eines Benutzers oder zum Anzeigen benutzerdefinierter Informationen enthält. Der Formulardatenintegrationsdienst unterstützt keine Formularberechnungen, Validierungen oder Skripten.

Um Daten in ein in Designer erstelltes Formular zu importieren, müssen Sie eine gültige XDP-XML-Datenquelle referenzieren. Betrachten Sie das folgende Beispielformular für einen Hypothekenantrag.

![ie_ie_loanformdata](assets/ie_ie_loanformdata.png)

Um Datenwerte in dieses Formular zu importieren, müssen Sie über eine gültige XDP XML-Datenquelle verfügen, die dem Formular entspricht. Sie können keine beliebige XML-Datenquelle verwenden, um Daten mithilfe des Formulardatenintegrationsdienstes in ein Formular zu importieren. Der Unterschied zwischen einer beliebigen XML-Datenquelle und einer XDP-XML-Datenquelle besteht darin, dass eine XDP-Datenquelle der XML Forms Architecture (XFA) entspricht. Die folgende XML-Datei stellt eine XDP-XML-Datenquelle dar, die dem Beispiel-Hypothekenantragsformular entspricht.

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
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So importieren Sie Formulardaten in ein PDF-Formular:

1. Projektdateien einschließen.
1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.
1. Referenzieren eines PDF-Formulars.
1. Referenzieren einer XML-Datenquelle.
1. Importieren Sie Daten in das PDF-Formular.
1. Speichern Sie das PDF-Formular als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Client für den Formulardatenintegrationsdienst**

Bevor Sie Daten programmgesteuert in eine Client-API für PDF-Formulare importieren können, müssen Sie einen Client für den Datenintegrationsdienst erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Weitere Informationen finden Sie unter [Festlegen von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren eines PDF-Formulars**

Um Daten in ein PDF-Formular zu importieren, müssen Sie entweder auf ein in Designer erstelltes XML-Formular oder auf ein in Acrobat erstelltes Acrobat-Formular verweisen.

**Referenzieren einer XML-Datenquelle**

Um Formulardaten zu importieren, müssen Sie auf eine gültige Datenquelle verweisen. Um Daten in ein in Designer erstelltes XFA-XML-Formular zu importieren, müssen Sie eine XDP-XML-Datenquelle verwenden. Wenn Sie auf ein Acrobat-Formular verweisen, müssen Sie eine XFDF-Datenquelle verwenden. Für jedes Feld, in das Sie Daten importieren möchten, muss ein Wert angegeben werden. Wenn ein Element in der XML-Datenquelle keinem Feld im Formular entspricht, wird das Element ignoriert.

**Importieren von Daten in das PDF-Formular**

Nachdem Sie ein PDF-Formular und eine gültige XML-Datenquelle referenziert haben, können Sie die Daten in das PDF-Formular importieren.

**PDF-Formular als PDF-Datei speichern**

Nachdem Sie Daten in ein Formular importiert haben, können Sie das Formular als PDF-Datei speichern. Nach dem Speichern als PDF-Datei kann ein Benutzer das Formular in Adobe Reader oder Acrobat öffnen und das Formular mit den importierten Daten anzeigen.

**Siehe auch**

[Importieren von Formulardaten mit der Java-API](importing-exporting-data.md#import-form-data-using-the-java-api)

[Importieren von Formulardaten mit der Webdienst-API](importing-exporting-data.md#import-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für den Formulardatenintegrationsdienst](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Exportieren von Formulardaten](importing-exporting-data.md#exporting-form-data)

### Importieren von Formulardaten mit der Java-API {#import-form-data-using-the-java-api}

Importieren Sie Formulardaten mit der Form Data Integration API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-formdataintegration-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Formulars.

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das das PDF-Formular mithilfe des Konstruktors `com.adobe.idp.Document` speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Formular enthält, an den Konstruktor.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt mithilfe des zugehörigen Konstruktors und übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt, die Daten enthält, die in das Formular importiert werden sollen.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das Formulardaten mithilfe des Konstruktors `com.adobe.idp.Document` speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das Formulardaten enthält, an den Konstruktor.

1. Importieren Sie Daten in das PDF-Formular.

   Importieren Sie Daten in ein PDF-Formular, indem Sie die `importData` -Methode des Objekts `FormDataIntegrationClient` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, in dem das PDF-Formular gespeichert wird.
   * Das `com.adobe.idp.Document`-Objekt, das Formulardaten speichert.

   Die `importData`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein PDF-Formular speichert, das die Daten in der XML-Datenquelle enthält.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateierweiterung &quot;.PDF&quot;ist.
   * Rufen Sie die `copyToFile` -Methode des `Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `importData` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Importieren von Formulardaten mit der Java-API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importieren von Formulardaten mit der Webdienst-API {#import-form-data-using-the-web-service-api}

Importieren Sie Formulardaten mithilfe der Form Data Integration API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.

   * Erstellen Sie ein `FormDataIntegrationClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `FormDataIntegrationClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `FormDataIntegrationClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren eines PDF-Formulars.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern des PDF-Formulars verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern der in das Formular importierten Daten verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt, die zu importierende Daten enthält, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Importieren Sie Daten in das PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `importData` -Methode des Objekts `FormDataIntegrationClient` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, in dem das PDF-Formular gespeichert wird.
   * Das `BLOB`-Objekt, das Formulardaten speichert.

   Die `importData`-Methode gibt ein `BLOB`-Objekt zurück, das ein PDF-Formular speichert, das die Daten in der XML-Datenquelle enthält.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der PDF-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `importData` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Exportieren von Formulardaten {#exporting-form-data}

Sie können Formulardaten aus einem interaktiven PDF-Formular mithilfe des Formulardatenintegrationsdienstes exportieren. Das Format der exportierten Daten hängt vom Formulartyp ab. Wenn der Formulartyp ein in Acrobat erstelltes Acrobat-Formular ist, sind die exportierten Daten XFDF. Wenn der Formulartyp ein XML-Formular ist, das in Designer erstellt wurde, sind die exportierten Daten XDP.

>[!NOTE]
>
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um Formulardaten aus einem PDF-Formular zu exportieren, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen
1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.
1. Referenzieren eines PDF-Formulars.
1. Exportieren Sie Daten aus dem PDF-Formular.
1. Speichern Sie die exportierten Daten als XML-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Client für den Formulardatenintegrationsdienst**

Bevor Sie Daten programmgesteuert in eine PDF FormClient-API importieren können, müssen Sie einen Client für den Datenintegrationsdienst erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Weitere Informationen finden Sie unter [Festlegen von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren eines PDF-Formulars**

Um Daten aus einem PDF-Formular zu exportieren, müssen Sie auf ein PDF-Formular verweisen, das in Designer oder Acrobat erstellt wurde und Formulardaten enthält. Wenn Sie versuchen, Daten aus einem leeren PDF-Formular zu exportieren, erhalten Sie ein leeres XML-Schema.

**Daten aus dem PDF-Formular exportieren**

Nachdem Sie ein PDF-Formular referenziert haben, das Formulardaten enthält, können Sie die Daten aus dem Formular exportieren. Die Daten werden in ein XML-Schema exportiert, das auf dem Formular basiert.

**Speichern Sie die Formulardaten als XML-Datei**

Nach dem Export von Formulardaten können Sie die Daten als XML-Datei speichern. Nach dem Speichern als XML-Datei können Sie die XML-Datei in einem XML-Viewer öffnen, um die Formulardaten anzuzeigen.

**Siehe auch**

[Exportieren von Formulardaten mit der Java-API](importing-exporting-data.md#export-form-data-using-the-java-api)

[Exportieren von Formulardaten mit der Webdienst-API](importing-exporting-data.md#export-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für den Formulardatenintegrationsdienst](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Importieren von Formulardaten](importing-exporting-data.md#importing-form-data)

### Exportieren von Formulardaten mit der Java-API {#export-form-data-using-the-java-api}

Exportieren Sie Formulardaten mithilfe der Form Data Integration API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-formdataintegration-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren eines PDF-Formulars.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt mithilfe des zugehörigen Konstruktors und übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars angibt, das zu exportierende Daten enthält.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das das PDF-Formular mithilfe des Konstruktors `com.adobe.idp.Document` speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Formular enthält, an den Konstruktor.

1. Exportieren Sie Daten aus dem PDF-Formular.

   Exportieren Sie Formulardaten, indem Sie die `exportData`-Methode des `FormDataIntegrationClient`-Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Formular speichert. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das Formulardaten als XML-Schema speichert.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Rufen Sie die `copyToFile` -Methode des `Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `exportData` -Methode zurückgegeben wurde).

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Exportieren von Formulardaten mit der Java-API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportieren von Formulardaten mithilfe der Webdienst-API {#export-form-data-using-the-web-service-api}

Exportieren Sie Formulardaten mithilfe der Form Data Integration API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   * Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.

   * Erstellen Sie ein `FormDataIntegrationClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `FormDataIntegrationClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `FormDataIntegrationClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren eines PDF-Formulars.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern des PDF-Formulars verwendet, aus dem Daten exportiert werden.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Exportieren Sie Daten aus dem PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `exportData`-Methode des Objekts `FormDataIntegrationClient` aufrufen und das `BLOB`-Objekt übergeben, das das PDF-Formular speichert. Diese Methode gibt ein `BLOB` -Objekt zurück, das Formulardaten als XML-Schema speichert.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Speicherort der XML-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `exportData` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine XML-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
