---
title: Validieren von DDX-Dokumenten
seo-title: Validieren von DDX-Dokumenten
description: Validieren Sie ein DDX-Dokument programmgesteuert mithilfe der Java-API und der Web Service-API.
seo-description: Validieren Sie ein DDX-Dokument programmgesteuert mithilfe der Java-API und der Web Service-API.
uuid: da668170-d2e9-4fff-aef5-432a856bd0bd
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 693859b0-a0c3-43f1-95c0-be48a90d7d8d
role: Developer
exl-id: 1f5a2cf3-ef6b-45b4-8fa8-b300e492fee1
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1543'
ht-degree: 3%

---

# Validieren von DDX-Dokumenten {#validating-ddx-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Sie können ein DDX-Dokument programmgesteuert validieren, das vom Assembler-Dienst verwendet wird. Mit der Assembler-Dienst-API können Sie also feststellen, ob ein DDX-Dokument gültig ist. Wenn Sie beispielsweise von einer früheren AEM Forms-Version aktualisiert haben und sicherstellen möchten, dass Ihr DDX-Dokument gültig ist, können Sie es mithilfe der Assembler-Dienst-API überprüfen.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein DDX-Dokument zu validieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.
1. Führen Sie die Überprüfung durch.
1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Um ein DDX-Dokument zu validieren, müssen Sie auf ein vorhandenes DDX-Dokument verweisen.

**Festlegen von Laufzeitoptionen zum Überprüfen des DDX-Dokuments**

Beim Validieren eines DDX-Dokuments müssen Sie bestimmte Laufzeitoptionen festlegen, die den Assembler-Dienst anweisen, das DDX-Dokument zu validieren, anstatt es auszuführen. Außerdem können Sie die Menge an Informationen erhöhen, die der Assembler-Dienst in die Protokolldatei schreibt.

**Validierung durchführen**

Nachdem Sie den Assembler-Dienst-Client erstellt, auf das DDX-Dokument verwiesen und Laufzeitoptionen festgelegt haben, können Sie den Vorgang `invokeDDX` aufrufen, um das DDX-Dokument zu validieren. Bei der Validierung des DDX-Dokuments können Sie `null` als map -Parameter übergeben (dieser Parameter speichert normalerweise PDF-Dokumente, die der Assembler benötigt, um die im DDX-Dokument angegebenen Vorgänge auszuführen).

Wenn die Validierung fehlschlägt, wird eine Ausnahme ausgelöst und die Protokolldatei enthält Details, die erklären, warum das DDX-Dokument ungültig ist, können von der `OperationException`-Instanz abgerufen werden. Nach der grundlegenden XML-Analyse und Schemakonferenz wird die Validierung anhand der DDX-Spezifikation durchgeführt. Alle im DDX-Dokument enthaltenen Fehler werden im Protokoll angegeben.

**Die Prüfergebnisse in einer Protokolldatei speichern**

Der Assembler-Dienst gibt die Überprüfungsergebnisse zurück, die Sie in eine XML-Protokolldatei schreiben können. Die Detailtiefe, die der Assembler-Dienst in die Protokolldatei schreibt, hängt von der von Ihnen festgelegten Laufzeitoption ab.

**Siehe auch**

[Überprüfen eines DDX-Dokuments mit der Java-API](#validate-a-ddx-document-using-the-java-api)

[Validieren eines DDX-Dokuments mithilfe der Webdienst-API](#validate-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Überprüfen eines DDX-Dokuments mit der Java-API {#validate-a-ddx-document-using-the-java-api}

Validieren Sie ein DDX-Dokument mithilfe der Assembler Service-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, die den Assembler-Dienst anweist, das DDX-Dokument zu überprüfen, indem Sie die setValidateOnly-Methode des Objekts `AssemblerOptionSpec` aufrufen und `true` übergeben.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Dienst in die Protokolldatei schreibt, indem Sie die `getLogLevel` -Methode des Objekts `AssemblerOptionSpec` aufrufen und einen Zeichenfolgenwert übergeben, der Ihre Anforderungen erfüllt. Beim Validieren eines DDX-Dokuments möchten Sie weitere Informationen in die Protokolldatei schreiben, die den Validierungsprozess unterstützen. Daher können Sie den Wert `FINE` oder `FINER` übergeben.

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das java.io.Map -Objekt, das normalerweise PDF-Dokumente speichert.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt.

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das Informationen enthält, die angeben, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `getJobLog` -Methode des Objekts `AssemblerResult` auf. Diese Methode gibt eine `com.adobe.idp.Document`-Instanz zurück, die Validierungsinformationen enthält.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren.

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird ein `OperationException` ausgegeben. Innerhalb der catch-Anweisung können Sie die `getJobLog` -Methode des Objekts `OperationException` aufrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[Schnellstart (SOAP-Modus): Validieren von DDX-Dokumenten mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api)  (SOAP-Modus)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Validieren eines DDX-Dokuments mithilfe der Webdienst-API {#validate-a-ddx-document-using-the-web-service-api}

Validieren Sie ein DDX-Dokument mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie localhost durch die IP-Adresse des Formularservers.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, mit der der Assembler-Dienst angewiesen wird, das DDX-Dokument zu validieren, indem der Wert true dem `validateOnly`-Datenelement des Objekts `AssemblerOptionSpec` zugewiesen wird.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Dienst in die Protokolldatei schreibt, indem Sie dem `logLevel`-Datenelement des Objekts `AssemblerOptionSpec` einen Zeichenfolgenwert zuweisen. -Methode Beim Validieren eines DDX-Dokuments möchten Sie weitere Informationen in die Protokolldatei schreiben, die den Validierungsprozess unterstützen. Daher können Sie den Wert `FINE` oder `FINER` angeben. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das `Map`-Objekt, das normalerweise PDF-Dokumente speichert.
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt.

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das Informationen enthält, die angeben, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der Protokolldatei und den Modus zum Öffnen der Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein `BLOB` -Objekt, das Protokollinformationen speichert, indem Sie den Wert des `jobLog` -Datenelements des Objekts `AssemblerResult` abrufen.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `BLOB` speichert. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird ein `OperationException` ausgegeben. Innerhalb der catch-Anweisung können Sie den Wert des `OperationException` -Objekts `jobLog` -Mitglieds abrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
