---
title: Programmgesteuerte Aufteilung von PDF-Dokumenten
description: Verwenden Sie den Assembler-Service, um ein einzelnes PDF-Dokument mithilfe der Java-API und der Webservice-API in mehrere PDF-Dokumente aufzuteilen.
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: c5e712e0-5c3f-48cd-91cf-fd347222a6b2
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 99%

---

# Programmgesteuerte Aufteilung von PDF-Dokumenten {#programmatically-disassembling-pdf-documents}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Sie können ein PDF-Dokument aufteilen, indem Sie es an den Assembler-Service übergeben. Diese Aufgabe ist in der Regel hilfreich, wenn das PDF-Dokument ursprünglich aus vielen Einzeldokumenten erstellt wurde, wie z. B. einer Sammlung von Aussagen. In der folgenden Abbildung ist DocA in mehrere Zieldokumente unterteilt, wobei das Lesezeichen der Stufe 1 auf einer Seite den Beginn eines neuen resultierenden Dokuments angibt.

![pd_pd_pdfsfrombookmarks](assets/pd_pd_pdfsfrombookmarks.png)

Stellen Sie zum Aufteilen eines PDF-Dokuments sicher, dass die `PDFsFromBookmarks` -Element im DDX-Dokument. Das Element `PDFsFromBookmarks` ist ein resultierendes Element und kann nur ein untergeordnetes Element des Elements `DDX` sein. Es hat kein `result`-Attribut, da es zur Erzeugung mehrerer Dokumente führen kann.

Das `PDFsFromBookmarks`-Element bewirkt, dass für jedes Lesezeichen der Stufe 1 im Quelldokument ein einzelnes Dokument generiert wird.

Für die Zwecke dieser Erörterung nehmen wir an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDFsFromBookmarks prefix="stmt">
     <PDF source="AssemblerResultPDF.pdf"/>
 </PDFsFromBookmarks>
 </DDX>
```

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mithilfe des Assembler-Dienstes vertraut machen. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Wenn Sie ein einzelnes PDF-Dokument an den Assembler-Service übergeben und ein einzelnes Dokument zurückerhalten, können Sie den Vorgang `invokeOneDocument` aufrufen. Verwenden Sie jedoch zum Aufteilen eines PDF-Dokuments den Vorgang `invokeDDX`, da zwar ein Eingabedokument an den Assembler-Service übergeben wird, der Assembler-Service jedoch ein Sammlungsobjekt zurückgibt, das ein oder mehrere PDF-Dokumente enthält.

>[!NOTE]
>
>Weitere Informationen über den Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie zum Aufteilen eines PDF-Dokuments die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Zerlegen Sie das PDF-Dokument.
1. Speichern Sie die zerlegten PDF-Dokumente.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Programm-Server bereitgestellt wird, der nicht JBoss ist, müssen Sie „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Programm-Server sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines PDF-Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Referenzieren eines vorhandenen DDX-Dokuments**

Um ein PDF-Dokument aufzuteilen, muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss das Element `PDFsFromBookmarks` enthalten.

**Referenzieren eines aufzuteilenden PDF-Dokuments**

Um ein PDF-Dokument zu zerlegen, verweisen Sie auf eine PDF-Datei, die das zu zerlegende PDF-Dokument darstellt. Wenn es an den Assembler-Service übergeben wird, wird für jedes Lesezeichen der Stufe 1 im Dokument ein separates PDF-Dokument zurückgegeben.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Services während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Aufteilen des PDF-Dokuments**

Nachdem Sie den Assembler-Service-Client erstellt, das DDX-Dokument referenziert, ein aufzuteilendes PDF-Dokument referenziert und Laufzeitoptionen festgelegt haben, können Sie ein PDF-Dokument aufteilen, indem Sie die Methode `invokeDDX` aufrufen. Sofern das DDX-Dokument Anweisungen zum Aufteilen des PDF-Dokuments enthält, gibt der Assembler-Service aufgeteilte PDF-Dokumente innerhalb eines Sammlungsobjekts zurück.

**Speichern der aufgeteilten PDF-Dokumente**

Alle zerlegten PDF-Dokumente werden in einem Sammlungsobjekt zurückgegeben. Durchlaufen Sie das Sammlungsobjekt und speichern Sie jedes PDF-Dokument als PDF-Datei.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatisches Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Aufteilen eines PDF-Dokuments mithilfe der Java-API {#disassemble-a-pdf-document-using-the-java-api}

So teilen Sie ein PDF-Dokument mithilfe der Assembler Service-API (Java) auf:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von PDF-Eingabedokumenten verwendet wird, indem Sie einen `HashMap`-Konstruktor verwenden.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie dessen Konstruktor verwenden und den Speicherort des aufzuteilenden PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das aufzuteilende PDF-Dokument enthält.
   * Fügen Sie einen Eintrag zum `java.util.Map`-Objekt hinzu, indem Sie seine Methode `put` aufrufen und die folgenden Argumente übergeben:

      * Eine Zeichenfolge, die den Speichernamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document`-Objekt, das das aufzuteilende PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Vorgangs im Falle eines Fehlers fortzusetzen, rufen Sie die Methode `setFailOnError` des Objekts `AssemblerOptionSpec` auf und geben Sie `false` weiter.

1. Zerlegen Sie das PDF-Dokument.

   Rufen Sie die Methode `invokeDDX` des Objekts `AssemblerServiceClient` auf und geben Sie die folgenden erforderlichen Werte weiter:

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das das aufzuteilende PDF-Dokument enthält
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Auftragsprotokollebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die zerlegten PDF-Dokumente und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die zerlegten PDF-Dokumente abzurufen:

   * Rufen Sie die Methode `getDocuments` des Objekts `AssemblerResult` auf. Dadurch wird ein `java.util.Map`-Objekt zurückgegeben.
   * Gehen Sie schrittweise durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die Methode `copyToFile` des Objekts `com.adobe.idp.Document` auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Programmgesteuerte Aufteilung von PDF-Dokumenten](#programmatically-disassembling-pdf-documents)

[Schnellstart (SOAP-Modus): Aufteilen eines PDF-Dokuments mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-disassembling-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Aufteilen eines PDF-Dokuments mithilfe der Webdienst-API {#disassemble-a-pdf-document-using-the-web-service-api}

Aufteilen eines PDF-Dokuments mithilfe der Assembler-Service-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Service-Referenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert mit der WSDL an den AEM Forms-Service (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekr, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert für den Dateispeicherort des DDX-Dokuments und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB`-Objekt wird an `invokeOneDocument` als Argument weitergegeben.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgewert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld die Inhalte des Byte-Arrays zuweisen.
   * Erstellen eines `MyMapOf_xsd_string_To_xsd_anyType`-Objekts. Dieses Sammlungsobjekt wird verwendet, um das aufzuteilende PDF-Dokument zu speichern.
   * Erstellen Sie ein Objekt `MyMapOf_xsd_string_To_xsd_anyType_Item`.
   * Weisen Sie dem Feld `key` des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts einen String-Wert zu, der den Schlüsselnamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, in dem das PDF-Dokument gespeichert wird, dem `value`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die `Add`-Methode des `MyMapOf_xsd_string_To_xsd_anyType`-Objekts auf und übergeben Sie das Objekt `MyMapOf_xsd_string_To_xsd_anyType`.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Vorgangs im Falle eines Fehlers fortzusetzen, weisen Sie `false` dem Feld `failOnError` des Objekts `AssemblerOptionSpec` zu. 

1. Zerlegen Sie das PDF-Dokument.

   Rufen Sie die Methode `invokeDDX` des Objekts `AssemblerServiceClient` auf und geben Sie die folgenden Werte weiter:

   * Ein `BLOB`-Objekt, welches das DDX-Dokument darstellt, das das PDF-Dokument zerlegt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, welches das zu zerlegende PDF-Dokument enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Auftragsergebnisse und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die neu erstellten PDF-Dokumente abzurufen:

   * Greifen Sie auf das Feld `documents` des Objekts `AssemblerResult` zu. Hierbei handelt es sich um ein `Map`-Objekt, das die aufgeteilten PDF-Dokumente enthält.
   * Iterieren Sie durch das `Map`-Objekt, um alle Zieldokumente abzurufen. Wandeln Sie dann das Element `value` dieses Array-Elements in `BLOB` um.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die Eigenschaft `MTOM` des Objekts `BLOB` zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Programmgesteuerte Aufteilung von PDF-Dokumenten](#programmatically-disassembling-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
