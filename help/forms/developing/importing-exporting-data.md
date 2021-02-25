---
title: Importieren und Exportieren von Daten
seo-title: Importieren und Exportieren von Daten
description: Verwenden Sie den Forms Data Integration-Dienst, um Daten in ein PDF-Formular zu importieren und Daten aus einem PDF-Formular mit der Java API und der Web Service API zu exportieren.
seo-description: Verwenden Sie den Forms Data Integration-Dienst, um Daten in ein PDF-Formular zu importieren und Daten aus einem PDF-Formular mit der Java API und der Web Service API zu exportieren.
uuid: 94ccb6f2-6e5f-43ea-a954-9a4402871a17
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 2e783745-c986-45ba-8e65-7437d114ca38
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '2810'
ht-degree: 5%

---


# Importieren und Exportieren von Daten {#importing-and-exporting-data}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

## Info zum Formulardatenintegrationsdienst {#about-the-form-data-integration-service}

Der Forms Data Integration-Dienst kann Daten in ein PDF-Formular importieren und Daten aus einem PDF-Formular exportieren. Die Ein- und Ausfuhrvorgänge unterstützen zwei Arten von PDF forms:

* Ein (in Acrobat erstelltes) Acrobat-Formular ist ein PDF-Dokument mit Formularfeldern.
* Ein (in Designer erstelltes) Adobe-XML-Formular ist ein PDF-Dokument, das der XML-Adobe-XML-Forms-Architektur (XFA) entspricht.

Formulardaten können je nach Typ des PDF-Formulars in einem der folgenden Formate vorhanden sein:

* Als XFDF-Datei, die eine XML-Version des Acrobat-Formulardatenformats darstellt.
* Als XDP-Datei, die eine XML-Datei mit Formularfelddefinitionen darstellt. Diese kann auch Formularfelddaten und eine eingebettete PDF-Datei enthalten. Eine von Designer generierte XDP-Datei kann nur verwendet werden, wenn sie ein eingebettetes Base-64-kodiertes PDF-Dokument enthält.

Sie können diese Aufgaben mithilfe des Formulardatenintegrationsdiensts ausführen:

* Daten in PDF forms importieren. Weitere Informationen finden Sie unter [Formulardaten importieren](importing-exporting-data.md#importing-form-data).
* Exportieren Sie Daten von PDF forms. Weitere Informationen finden Sie unter [Exportieren von Formulardaten](importing-exporting-data.md#exporting-form-data).

>[!NOTE]
>
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Formulardaten importieren {#importing-form-data}

Sie können Formulardaten mithilfe des Formulardatenintegrationsdiensts in interaktive PDF forms importieren. Ein interaktives PDF-Formular ist ein PDF-Dokument, das ein oder mehrere Felder zum Erfassen von Informationen eines Benutzers oder zum Anzeigen benutzerdefinierter Informationen enthält. Der Formulardatenintegrationsdienst unterstützt keine Formularberechnungen, Überprüfungen oder Skripten.

Um Daten in ein in Designer erstelltes Formular zu importieren, müssen Sie auf eine gültige XDP-XML-Datenquelle verweisen. Betrachten Sie das folgende Beispiel für ein Hypothekenantragsformular.

![ie_ie_loanformdata](assets/ie_ie_loanformdata.png)

Um Datenwerte in dieses Formular zu importieren, müssen Sie über eine gültige XDP-XML-Datenquelle verfügen, die dem Formular entspricht. Sie können keine beliebige XML-Datenquelle verwenden, um Daten mit dem Formulardatenintegrationsdienst in ein Formular zu importieren. Der Unterschied zwischen einer beliebigen XML-Datenquelle und einer XDP-XML-Datenquelle besteht darin, dass eine XDP-Datenquelle der XML Forms Architecture (XFA) entspricht. Die folgende XML-Datei stellt eine XDP-XML-Datenquelle dar, die dem Musterhypothekenantragsformular entspricht.

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
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So importieren Sie Formulardaten in ein PDF-Formular:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client des Service für die Formulardatenintegration.
1. Verweisen Sie auf ein PDF-Formular.
1. Verweisen Sie auf eine XML-Datenquelle.
1. Daten in das PDF-Formular importieren.
1. Speichern Sie das PDF-Formular als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Client des Dienstes &quot;Formulardatenintegration&quot;erstellen**

Bevor Sie Daten programmgesteuert in eine PDF-Formular-Client-API importieren können, müssen Sie einen Data Integration-Dienstclient erstellen. Beim Erstellen eines Dienstclients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Weitere Informationen finden Sie unter [Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren eines PDF-Formulars**

Um Daten in ein PDF-Formular zu importieren, müssen Sie entweder auf ein in Designer erstelltes XML-Formular oder auf ein in Acrobat erstelltes Acrobat-Formular verweisen.

**Referenzieren einer XML-Datenquelle**

Um Formulardaten zu importieren, müssen Sie auf eine gültige Datenquelle verweisen. Um Daten in ein XFA-XML-Formular zu importieren, das in Designer erstellt wurde, müssen Sie eine XDP-XML-Datenquelle verwenden. Wenn Sie auf ein Acrobat-Formular verweisen, müssen Sie eine XFDF-Datenquelle verwenden. Für jedes Feld, in das Sie Daten importieren möchten, muss ein Wert angegeben werden. Wenn ein Element in der XML-Datenquelle nicht mit einem Feld im Formular übereinstimmt, wird das Element ignoriert.

**Daten in das PDF-Formular importieren**

Nachdem Sie auf ein PDF-Formular und eine gültige XML-Datenquelle verwiesen haben, können Sie die Daten in das PDF-Formular importieren.

**PDF-Formular als PDF-Datei speichern**

Nachdem Sie Daten in ein Formular importiert haben, können Sie das Formular als PDF-Datei speichern. Nach dem Speichern als PDF-Datei kann ein Benutzer das Formular in Adobe Reader oder Acrobat öffnen und das Formular mit den importierten Daten anzeigen.

**Siehe auch**

[Formulardaten mit der Java-API importieren](importing-exporting-data.md#import-form-data-using-the-java-api)

[Formulardaten mit der Webdienst-API importieren](importing-exporting-data.md#import-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Data Integration Service API](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Exportieren von Formulardaten](importing-exporting-data.md#exporting-form-data)

### Formulardaten mit der Java-API {#import-form-data-using-the-java-api} importieren

Importieren Sie Formulardaten mit der Formular-Datenintegration-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-formdataintegration-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client des Service für die Formulardatenintegration.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein PDF-Formular.

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Formulars angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das das PDF-Formular mit dem Konstruktor `com.adobe.idp.Document` speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Formular enthält, an den Konstruktor.

1. Verweisen Sie auf eine XML-Datenquelle.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt mit dem Konstruktor und übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XML-Datei angibt, die Daten enthält, die in das Formular importiert werden sollen.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das mithilfe des Konstruktors `com.adobe.idp.Document` Formulardaten speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das Formulardaten enthält, an den Konstruktor.

1. Daten in das PDF-Formular importieren.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `importData`-Methode des Objekts aufrufen und die folgenden Werte übergeben:`FormDataIntegrationClient`

   * Das `com.adobe.idp.Document`-Objekt, in dem das PDF-Formular gespeichert wird.
   * Das `com.adobe.idp.Document`-Objekt, das Formulardaten speichert.

   Die `importData`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein PDF-Formular speichert, das die Daten in der XML-Datenquelle enthält.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung &quot;.PDF&quot;ist.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `importData`-Methode zurückgegeben wurde).`Document`

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Formulardaten mit der Java-API importieren](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formulardaten mit der Webdienst-API {#import-form-data-using-the-web-service-api} importieren

Importieren Sie Formulardaten mit der Formulardatenintegration-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client des Service für die Formulardatenintegration.

   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `FormDataIntegrationClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `FormDataIntegrationClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Verweisen Sie auf ein PDF-Formular.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern des PDF-Formulars verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Formulars und den Modus, in dem die Datei geöffnet werden soll, angibt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf eine XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Mit diesem `BLOB`-Objekt werden die in das Formular importierten Daten gespeichert.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XML-Datei angibt, die zu importierende Daten enthält, und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Daten in das PDF-Formular importieren.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `FormDataIntegrationClient`-Objektmethode `importData` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, in dem das PDF-Formular gespeichert wird.
   * Das `BLOB`-Objekt, das Formulardaten speichert.

   Die `importData`-Methode gibt ein `BLOB`-Objekt zurück, das ein PDF-Formular speichert, das die Daten in der XML-Datenquelle enthält.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort der PDF-Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `importData`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Exportieren von Formulardaten {#exporting-form-data}

Sie können Formulardaten aus einem interaktiven PDF-Formular mithilfe des Formulardatenintegrationsdiensts exportieren. Das Format der exportierten Daten hängt vom Formulartypen ab. Wenn der Formulartyp ein in Acrobat erstelltes Acrobat-Formular ist, dann sind die exportierten Daten XFDF. Wenn der Formulartyp ein XML-Formular ist, das in Designer erstellt wurde, sind die exportierten Daten XDP.

>[!NOTE]
>
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So exportieren Sie Formulardaten aus einem PDF-Formular:

1. Projektdateien einschließen
1. Erstellen Sie einen Client des Service für die Formulardatenintegration.
1. Verweisen Sie auf ein PDF-Formular.
1. Exportieren Sie Daten aus dem PDF-Formular.
1. Speichern Sie die exportierten Daten als XML-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

**Client des Dienstes &quot;Formulardatenintegration&quot;erstellen**

Bevor Sie Daten programmgesteuert in eine PDF formClient-API importieren können, müssen Sie einen Data Integration-Dienstclient erstellen. Beim Erstellen eines Dienstclients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Weitere Informationen finden Sie unter [Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren eines PDF-Formulars**

Um Daten aus einem PDF-Formular zu exportieren, müssen Sie auf ein PDF-Formular verweisen, das in Designer oder Acrobat erstellt wurde und Formulardaten enthält. Wenn Sie versuchen, Daten aus einem leeren PDF-Formular zu exportieren, erhalten Sie ein leeres XML-Schema.

**Daten aus dem PDF-Formular exportieren**

Nachdem Sie auf ein PDF-Formular mit Formulardaten verwiesen haben, können Sie die Daten aus dem Formular exportieren. Die Daten werden in ein XML-Schema exportiert, das auf dem Formular basiert.

**Formulardaten als XML-Datei speichern**

Nach dem Exportieren der Formulardaten können Sie die Daten als XML-Datei speichern. Nach dem Speichern als XML-Datei können Sie die XML-Datei in einem XML-Viewer öffnen, um die Formulardaten Ansicht.

**Siehe auch**

[Formulardaten mit der Java-API exportieren](importing-exporting-data.md#export-form-data-using-the-java-api)

[Exportieren von Formulardaten mit der Webdienst-API](importing-exporting-data.md#export-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Data Integration Service API](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Formulardaten importieren](importing-exporting-data.md#importing-form-data)

### Formulardaten mit der Java-API {#export-form-data-using-the-java-api} exportieren

Exportieren Sie Formulardaten mithilfe der Formular-Datenintegration-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-formdataintegration-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client des Service für die Formulardatenintegration.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein PDF-Formular.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt mit dem Konstruktor und übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Formulars angibt, das zu exportierende Daten enthält.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das das PDF-Formular mit dem Konstruktor `com.adobe.idp.Document` speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Formular enthält, an den Konstruktor.

1. Exportieren Sie Daten aus dem PDF-Formular.

   Exportieren Sie Formulardaten, indem Sie die `exportData`-Methode des Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, in dem das PDF-Formular gespeichert wird. `FormDataIntegrationClient` Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das Formulardaten als XML-Schema speichert.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `exportData`-Methode zurückgegeben wurde).`Document`

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Exportieren von Formulardaten mit der Java-API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportieren von Formulardaten mit der Webdienst-API {#export-form-data-using-the-web-service-api}

Exportieren Sie Formulardaten mithilfe der Formulardatenintegration-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   * Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client des Service für die Formulardatenintegration.

   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `FormDataIntegrationClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `FormDataIntegrationClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `FormDataIntegrationClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Verweisen Sie auf ein PDF-Formular.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern des PDF-Formulars verwendet, aus dem Daten exportiert werden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Formulars und den Modus, in dem die Datei geöffnet werden soll, angibt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Exportieren Sie Daten aus dem PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `FormDataIntegrationClient`-Methode des Objekts `exportData` aufrufen und das `BLOB`-Objekt übergeben, in dem das PDF-Formular gespeichert wird. Diese Methode gibt ein `BLOB`-Objekt zurück, das Formulardaten als XML-Schema speichert.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort der XML-Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `exportData`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine XML-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
