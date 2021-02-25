---
title: Validieren von DDX-Dokumenten
seo-title: Validieren von DDX-Dokumenten
description: Validieren Sie ein DDX-Dokument programmgesteuert mithilfe der Java-API und der Web-Service-API.
seo-description: Validieren Sie ein DDX-Dokument programmgesteuert mithilfe der Java-API und der Web-Service-API.
uuid: da668170-d2e9-4fff-aef5-432a856bd0bd
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 693859b0-a0c3-43f1-95c0-be48a90d7d8d
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '1543'
ht-degree: 3%

---


# Validieren von DDX-Dokumenten {#validating-ddx-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Sie können ein DDX-Dokument, das vom Assembler-Dienst verwendet wird, programmgesteuert validieren. Mit der Assembler-Dienst-API können Sie also festlegen, ob ein DDX-Dokument gültig ist. Wenn Sie beispielsweise ein Upgrade von einer früheren AEM Forms-Version durchgeführt haben und sicherstellen möchten, dass Ihr DDX-Dokument gültig ist, können Sie es mithilfe der Assembler-Dienst-API überprüfen.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Um ein DDX-Dokument zu validieren, müssen Sie auf ein vorhandenes DDX-Dokument verweisen.

**Festlegen von Laufzeitoptionen zur Validierung des DDX-Dokuments**

Bei der Validierung eines DDX-Dokuments müssen Sie bestimmte Laufzeitoptionen festlegen, die den Assembler-Dienst anweisen, das DDX-Dokument zu validieren, anstatt es auszuführen. Außerdem können Sie die Menge an Informationen erhöhen, die der Assembler-Dienst in die Protokolldatei schreibt.

**Validierung durchführen**

Nachdem Sie den Assembler-Dienstclient erstellt haben, auf das DDX-Dokument verweisen und Laufzeitoptionen festgelegt haben, können Sie den Vorgang `invokeDDX` aufrufen, um das DDX-Dokument zu validieren. Bei der Validierung des DDX-Dokuments können Sie `null` als Map-Parameter übergeben (dieser Parameter speichert normalerweise PDF-Dokumente, die der Assembler zur Ausführung der im DDX-Dokument angegebenen Vorgänge benötigt).

Wenn die Überprüfung fehlschlägt, wird eine Ausnahme ausgelöst und die Protokolldatei enthält Details, die erklären, warum das DDX-Dokument ungültig ist, kann von der `OperationException`-Instanz abgerufen werden. Nach der grundlegenden XML-Parsing- und Schema-Prüfung wird die Validierung anhand der DDX-Spezifikation durchgeführt. Alle im DDX-Dokument enthaltenen Fehler werden im Protokoll angegeben.

**Die Prüfergebnisse in einer Protokolldatei speichern**

Der Assembler-Dienst gibt die Überprüfungsergebnisse zurück, die Sie in eine XML-Protokolldatei schreiben können. Die Menge der Details, die der Assembler-Dienst in die Protokolldatei schreibt, hängt von der von Ihnen festgelegten Laufzeitoption ab.

**Siehe auch**

[Validieren eines DDX-Dokuments mithilfe der Java-API](#validate-a-ddx-document-using-the-java-api)

[Validieren eines DDX-Dokuments mithilfe der Webdienst-API](#validate-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Validieren eines DDX-Dokuments mithilfe der Java-API {#validate-a-ddx-document-using-the-java-api}

Validieren eines DDX-Dokuments mithilfe der Assembler Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, die den Assembler-Dienst anweist, das DDX-Dokument zu validieren, indem Sie die setValidateOnly-Methode des Objekts aufrufen und `true` übergeben.`AssemblerOptionSpec`
   * Legen Sie die Menge an Informationen fest, die der Assembler-Dienst in die Protokolldatei schreibt, indem Sie die `getLogLevel`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der Ihre Anforderungen erfüllt. `AssemblerOptionSpec` Bei der Validierung eines DDX-Dokuments sollen weitere Informationen in die Protokolldatei geschrieben werden, die den Validierungsprozess unterstützen. Daher können Sie den Wert `FINE` oder `FINER` übergeben.

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das java.io.Map-Objekt, in dem PDF-Dokumente normalerweise gespeichert werden.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt.

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das Informationen darüber enthält, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Überprüfungsergebnisse in einer Protokolldatei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `AssemblerResult`-Methode des Objekts `getJobLog` auf. Diese Methode gibt eine `com.adobe.idp.Document`-Instanz zurück, die Überprüfungsinformationen enthält.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren.`com.adobe.idp.Document`

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird ein `OperationException` ausgelöst. Innerhalb der catch-Anweisung können Sie die `OperationException`-Methode des Objekts `getJobLog` aufrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[Quick Beginn (SOAP-Modus): Validieren von DDX-Dokumenten mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api) (SOAP-Modus)

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

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der den WSDL-Wert an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, mit der der Assembler-Dienst angewiesen wird, das DDX-Dokument zu validieren, indem der Wert &quot;true&quot;dem `AssemblerOptionSpec`-Datenmember des Objekts `validateOnly` zugewiesen wird.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Dienst in die Protokolldatei schreibt, indem Sie dem `AssemblerOptionSpec`-Datenmember des Objekts `logLevel` einen Zeichenfolgenwert zuweisen. -Methode Bei der Validierung eines DDX-Dokuments sollten weitere Informationen in die Protokolldatei geschrieben werden, die den Validierungsprozess unterstützen. Daher können Sie den Wert `FINE` oder `FINER` angeben. Informationen zu den verfügbaren Laufzeitoptionen finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das `Map`-Objekt, das normalerweise PDF-Dokumente speichert.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das Informationen darüber enthält, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Überprüfungsergebnisse in einer Protokolldatei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort der Protokolldatei und den Modus zum Öffnen der Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein `BLOB`-Objekt, das Protokollinformationen speichert, indem Sie den Wert des `AssemblerResult`-Datenelements des Objekts `jobLog` abrufen.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `BLOB` speichert. Füllen Sie das Bytearray, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird ein `OperationException` ausgelöst. Innerhalb der catch-Anweisung können Sie den Wert des `OperationException`-Objekts `jobLog`-Mitglieds abrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
