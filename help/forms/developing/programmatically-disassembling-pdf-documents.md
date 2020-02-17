---
title: Programmgesteuertes Disassemblieren von PDF-Dokumenten
seo-title: Programmgesteuertes Disassemblieren von PDF-Dokumenten
description: 'null'
seo-description: 'null'
uuid: d71cc044-e948-4b7a-b598-b041723b69e9
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8e38a597-5d22-4d83-95fe-4494fb04e4a3
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Programmgesteuertes Disassemblieren von PDF-Dokumenten {#programmatically-disassembling-pdf-documents}

Sie können ein PDF-Dokument auflösen, indem Sie es an den Assembler-Dienst übergeben. Normalerweise ist diese Aufgabe nützlich, wenn das PDF-Dokument ursprünglich aus vielen einzelnen Dokumenten erstellt wurde, z. B. einer Sammlung von Anweisungen. In der folgenden Abbildung wird DocA in mehrere Zieldokumente unterteilt, wobei das erste Lesezeichen der Stufe 1 auf einer Seite den Beginn eines neuen Zieldokuments angibt.

![pd_pd_pdfsformbookmarks](assets/pd_pd_pdfsfrombookmarks.png)

Um ein PDF-Dokument zu deassemblieren, stellen Sie sicher, dass sich das `PDFsFromBookmarks` -Element im DDX-Dokument befindet. Das `PDFsFromBookmarks` Element ist ein resultierendes Element und kann nur ein untergeordnetes Element des `DDX` Elements sein. Es hat kein `result` Attribut, da es zur Generierung mehrerer Dokumente führen kann.

Das `PDFsFromBookmarks` Element bewirkt, dass für jedes Lesezeichen der Stufe 1 im Quelldokument ein einzelnes Dokument generiert wird.

Angenommen, das folgende DDX-Dokument wird für diese Diskussion verwendet.

```as3
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDFsFromBookmarks prefix="stmt">
     <PDF source="AssemblerResultPDF.pdf"/>
 </PDFsFromBookmarks>
 </DDX>
```

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie mit dem Zusammenstellen von PDF-Dokumenten mithilfe des Assembler-Dienstes vertraut sein. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Wenn Sie ein einzelnes PDF-Dokument an den Assembler-Dienst weiterleiten und ein einzelnes Dokument zurückerhalten, können Sie den `invokeOneDocument` Vorgang aufrufen. Um ein PDF-Dokument zu zerlegen, verwenden Sie den `invokeDDX` Vorgang jedoch, da zwar ein PDF-Eingabedokument an den Assembler-Dienst übergeben wird, der Assembler-Dienst jedoch ein Collection-Objekt zurückgibt, das eines oder mehrere Dokumente enthält.

>[!NOTE]
>
>For more information about the Assembler service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um ein PDF-Dokument zu zerlegen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Referenzieren eines zu zerlegenden PDF-Dokuments
1. Legen Sie Laufzeitoptionen fest.
1. Auflösung des PDF-Dokuments.
1. Speichern Sie die zerlegten PDF-Dokumente.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie adobe-utilities.jar und jbossall-client.jar durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Zum Aufteilen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss das `PDFsFromBookmarks` Element enthalten.

**Zu zerlegendes PDF-Dokument referenzieren**

Um ein PDF-Dokument zu zerlegen, verweisen Sie auf eine PDF-Datei, die das zu zerlegende PDF-Dokument darstellt. Beim Übermitteln an den Assembler-Dienst wird für jedes Lesezeichen der Stufe 1 im Dokument ein separates PDF-Dokument zurückgegeben.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren.

**Auflösung des PDF-Dokuments**

Nachdem Sie den Assembler-Dienstclient erstellt haben, auf das DDX-Dokument verweisen, auf ein zu disassemblierendes PDF-Dokument verweisen und Laufzeitoptionen festlegen, können Sie ein PDF-Dokument durch Aufrufen der `invokeDDX` Methode disassemblieren. Sofern das DDX-Dokument Anweisungen zum Aufteilen des PDF-Dokuments enthält, gibt der Assembler-Dienst nicht zusammengesetzte PDF-Dokumente innerhalb eines Collection-Objekts zurück.

**Speichern der demontierten PDF-Dokumente**

Alle demontierten PDF-Dokumente werden innerhalb eines Collection-Objekts zurückgegeben. Durchsuchen Sie das Sammlungsobjekt und speichern Sie jedes PDF-Dokument als PDF-Datei.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Aufteilen eines PDF-Dokuments mit der Java-API {#disassemble-a-pdf-document-using-the-java-api}

Disassemblieren eines PDF-Dokuments mit der Assembler Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `AssemblerServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren eines zu zerlegenden PDF-Dokuments

   * Erstellen Sie ein `java.util.Map` Objekt, das zum Speichern von PDF-Eingabedokumenten mithilfe eines `HashMap` Konstruktors verwendet wird.
   * Erstellen Sie ein `java.io.FileInputStream` Objekt, indem Sie dessen Konstruktor verwenden und die Position des PDF-Dokuments zur Auflösung übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt und übergeben Sie das `java.io.FileInputStream` Objekt, das das PDF-Dokument enthält, zur Auflösung.
   * Fügen Sie dem `java.util.Map` Objekt einen Eintrag hinzu, indem Sie dessen `put` Methode aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document` Objekt, das das zu zerlegende PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `AssemblerOptionSpec` Methode des `setFailOnError` Objekts auf und übergeben Sie sie `false`.

1. Auflösung des PDF-Dokuments.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeDDX` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document` Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map` Objekt, das das zu zerlegende PDF-Dokument enthält
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Auftragsprotokollebene
   Die `invokeDDX` Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult` Objekt zurück, das die deassemblierten PDF-Dokumente und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie zum Abrufen der demontierten PDF-Dokumente die folgenden Schritte aus:

   * Rufen Sie die `AssemblerResult` Methode des `getDocuments` Objekts auf. Dadurch wird ein `java.util.Map` Objekt zurückgegeben.
   * Durchlaufen des `java.util.Map` Objekts, bis Sie das resultierende `com.adobe.idp.Document` Objekt gefunden haben.
   * Rufen Sie die `com.adobe.idp.Document` Methode des `copyToFile` Objekts auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Programmgesteuertes Disassemblieren von PDF-Dokumenten](#programmatically-disassembling-pdf-documents)

[Kurzanleitung (SOAP-Modus): Demontieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-disassembling-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Aufteilen eines PDF-Dokuments mit der Webdienst-API {#disassemble-a-pdf-document-using-the-web-service-api}

Disassemblieren eines PDF-Dokuments mit der Assembler Service API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient` Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` Objekt mithilfe des `System.ServiceModel.EndpointAddress` Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `AssemblerServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Create a `System.IO.FileStream` object by invoking its constructor. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des DDX-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seine `MTOM` Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren eines zu zerlegenden PDF-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB` Objekt wird als `invokeOneDocument` Argument an das Objekt übergeben.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.
   * Create a `MyMapOf_xsd_string_To_xsd_anyType` object. Dieses Collection-Objekt wird zum Speichern der PDF-Datei für die Auflösung verwendet.
   * Create a `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Objektfeld einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt `key` . Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB` Objekt, in dem das PDF-Dokument gespeichert wird, dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Objektfeld `value` zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekt dem `MyMapOf_xsd_string_To_xsd_anyType` Objekt hinzu. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` Objektmethode `Add` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType` Objekt.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem zum `AssemblerOptionSpec` Objekt gehörenden Datenmember einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie `false` dem `AssemblerOptionSpec` Objektfeld `failOnError` zu.

1. Auflösung des PDF-Dokuments.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeDDX` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` Objekt, das das DDX-Dokument darstellt, das das PDF-Dokument deassassassembliert
   * Das `MyMapOf_xsd_string_To_xsd_anyType` Objekt, das das zu trennende PDF-Dokument enthält
   * Ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen angibt
   Die `invokeDDX` Methode gibt ein `AssemblerResult` Objekt zurück, das die Auftragsergebnisse und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   So rufen Sie die neu erstellten PDF-Dokumente ab:

   * Greifen Sie auf das `AssemblerResult` Feld des `documents` Objekts zu, bei dem es sich um ein `Map` Objekt mit den zerlegten PDF-Dokumenten handelt.
   * Durchlaufen Sie das `Map` Objekt, um jedes Zieldokument abzurufen. Anschließend können Sie das Array-Element `value` in eine `BLOB`umwandeln.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB` Objekteigenschaft `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Programmgesteuertes Disassemblieren von PDF-Dokumenten](#programmatically-disassembling-pdf-documents)

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
