---
title: Validieren von DDX-Dokumenten
seo-title: Validieren von DDX-Dokumenten
description: 'null'
seo-description: 'null'
uuid: da668170-d2e9-4fff-aef5-432a856bd0bd
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 693859b0-a0c3-43f1-95c0-be48a90d7d8d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Validieren von DDX-Dokumenten {#validating-ddx-documents}

Sie können ein DDX-Dokument, das vom Assembler-Dienst verwendet wird, programmgesteuert validieren. Mit der Assembler-Dienst-API können Sie also festlegen, ob ein DDX-Dokument gültig ist. Wenn Sie beispielsweise von einer früheren AEM Forms-Version aktualisiert haben und sicherstellen möchten, dass Ihr DDX-Dokument gültig ist, können Sie es mithilfe der Assembler-Dienst-API überprüfen.

>[!NOTE]
>
>For more information about the Assembler service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So validieren Sie ein DDX-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.
1. Führen Sie die Überprüfung durch.
1. Speichern Sie die Überprüfungsergebnisse in einer Protokolldatei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Zum Überprüfen eines DDX-Dokuments müssen Sie auf ein vorhandenes DDX-Dokument verweisen.

**Festlegen von Laufzeitoptionen zur Überprüfung des DDX-Dokuments**

Beim Überprüfen eines DDX-Dokuments müssen Sie bestimmte Laufzeitoptionen festlegen, die den Assembler-Dienst anweisen, das DDX-Dokument zu validieren, anstatt es auszuführen. Außerdem können Sie die Menge an Informationen erhöhen, die der Assembler-Dienst in die Protokolldatei schreibt.

**Validierung durchführen**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, auf das DDX-Dokument verweisen und Laufzeitoptionen festgelegt haben, können Sie den `invokeDDX` Vorgang zum Überprüfen des DDX-Dokuments aufrufen. Bei der Validierung des DDX-Dokuments können Sie `null` als Map-Parameter übergeben (dieser Parameter speichert normalerweise PDF-Dokumente, die der Assembler zur Durchführung der im DDX-Dokument angegebenen Vorgänge benötigt).

Wenn die Überprüfung fehlschlägt, wird eine Ausnahme ausgelöst und die Protokolldatei enthält Details, die erklären, warum das DDX-Dokument ungültig ist, kann von der `OperationException` Instanz abgerufen werden. Nach der grundlegenden XML-Analyse und Schemakonferenz wird die Validierung anhand der DDX-Spezifikation durchgeführt. Alle im DDX-Dokument enthaltenen Fehler werden im Protokoll angegeben.

**Die Prüfergebnisse in einer Protokolldatei speichern**

Der Assembler-Dienst gibt die Überprüfungsergebnisse zurück, die Sie in eine XML-Protokolldatei schreiben können. Die Menge der Details, die der Assembler-Dienst in die Protokolldatei schreibt, hängt von der von Ihnen festgelegten Laufzeitoption ab.

**Siehe auch**

[Validieren eines DDX-Dokuments mit der Java-API](#validate-a-ddx-document-using-the-java-api)

[Validieren eines DDX-Dokuments mithilfe der Webdienst-API](#validate-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Validieren eines DDX-Dokuments mit der Java-API {#validate-a-ddx-document-using-the-java-api}

Validieren eines DDX-Dokuments mithilfe der Assembler Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `AssemblerServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, mit der der Assembler-Dienst angewiesen wird, das DDX-Dokument zu überprüfen, indem die Methode setValidateOnly des `AssemblerOptionSpec` Objekts aufgerufen und weitergegeben wird `true`.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Dienst in die Protokolldatei schreibt, indem Sie die `AssemblerOptionSpec` `getLogLevel` Objektmethode aufrufen und einen Zeichenfolgenwert weitergeben, der Ihre Anforderungen erfüllt. Bei der Validierung eines DDX-Dokuments sollten weitere Informationen in die Protokolldatei geschrieben werden, die den Validierungsprozess unterstützen. Daher können Sie den Wert `FINE` oder `FINER`.

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeDDX` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das java.io.Map-Objekt, das normalerweise PDF-Dokumente speichert.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object that specifies the run-time options.
   Die `invokeDDX` Methode gibt ein `AssemblerResult` Objekt zurück, das Informationen darüber enthält, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Überprüfungsergebnisse in einer Protokolldatei.

   * Create a `java.io.File` object and ensure that the file name extension is .xml.
   * Rufen Sie die `AssemblerResult` Methode des `getJobLog` Objekts auf. Diese Methode gibt eine `com.adobe.idp.Document` Instanz mit Überprüfungsinformationen zurück.
   * Invoke the `com.adobe.idp.Document` object’s `copyToFile` method to copy the contents of the `com.adobe.idp.Document` object to the file.
   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird ein `OperationException` ausgegeben. Innerhalb der catch-Anweisung können Sie die `OperationException` Methode des `getJobLog` Objekts aufrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[Kurzanleitung (SOAP-Modus): Validieren von DDX-Dokumenten mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api) (SOAP-Modus)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Validieren eines DDX-Dokuments mithilfe der Webdienst-API {#validate-a-ddx-document-using-the-web-service-api}

Validieren eines DDX-Dokuments mithilfe der Assembler Service API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie localhost durch die IP-Adresse des Formularservers.

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
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seine `MTOM` Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, mit der der Assembler-Dienst angewiesen wird, das DDX-Dokument zu validieren, indem der Wert &quot;true&quot;dem `AssemblerOptionSpec` Datenmember des `validateOnly` Objekts zugewiesen wird.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Dienst in die Protokolldatei schreibt, indem Sie dem `AssemblerOptionSpec` Datenmember des Objekts einen Zeichenfolgenwert zuweisen `logLevel` . -Methode Bei der Validierung eines DDX-Dokuments sollten weitere Informationen in die Protokolldatei geschrieben werden, die den Validierungsprozess unterstützen. Daher können Sie den Wert `FINE` oder `FINER`die Variable angeben. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec` Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeDDX` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das `Map` Objekt, in dem normalerweise PDF-Dokumente gespeichert werden.
   * Ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen angibt.
   Die `invokeDDX` Methode gibt ein `AssemblerResult` Objekt zurück, das Informationen darüber enthält, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Überprüfungsergebnisse in einer Protokolldatei.

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort der Protokolldatei und den Modus zum Öffnen der Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein `BLOB` Objekt, das Protokollinformationen speichert, indem Sie den Wert des `AssemblerResult` Objektdatenelements abrufen `jobLog` .
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB` Objektfelds abrufen `MTOM` .
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.
   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird ein `OperationException` ausgegeben. Innerhalb der catch-Anweisung können Sie den Wert des `OperationException` Objektelements `jobLog` abrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
