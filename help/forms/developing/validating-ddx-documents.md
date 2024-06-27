---
title: Validieren von DDX-Dokumenten
description: Validieren Sie ein DDX-Dokument programmgesteuert mithilfe der Java-API und der Web Service-API.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 1f5a2cf3-ef6b-45b4-8fa8-b300e492fee1
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '1507'
ht-degree: 100%

---

# Validieren von DDX-Dokumenten {#validating-ddx-documents}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Sie können ein DDX-Dokumen, das vom Assembler-Service verwendet wird, programmgesteuert validieren. Mit der Assembler-Service-API können Sie also feststellen, ob ein DDX-Dokument gültig ist. Wenn Sie beispielsweise ein Upgrade von einer früheren AEM Forms-Version durchgeführt haben und sicherstellen möchten, dass Ihr DDX-Dokument gültig ist, können Sie es mithilfe der Assembler-Service-API überprüfen.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein DDX-Dokument zu validieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.
1. Führen Sie die Überprüfung durch.
1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

**Projektdateien einbeziehen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien adobe-utilities.jar- und jbossall-client.jar-Dateien durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Um ein DDX-Dokument zu validieren, müssen Sie auf ein vorhandenes DDX-Dokument verweisen.

**Laufzeitoptionen zum Validieren des DDX-Dokuments festlegen**

Wenn Sie ein DDX-Dokument validieren möchten, müssen Sie bestimmte Laufzeitoptionen festlegen, die den Assembler-Service anweisen, das DDX-Dokument zu validieren, anstatt es auszuführen. Außerdem können Sie die Informationsmenge erhöhen, die der Assembler-Service in die Protokolldatei schreibt.

**Validierung durchführen**

Nachdem Sie den Assembler-Service-Client erstellt, auf das DDX-Dokument verwiesen und Laufzeitoptionen festgelegt haben, können Sie den `invokeDDX`-Vorgang zum Überprüfen des DDX-Dokuments aufrufen. Bei der Validierung des DDX-Dokuments können Sie `null` als map-Parameter übergeben (dieser Parameter speichert in der Regel PDF-Dokumente, die der Assembler benötigt, um die im DDX-Dokument angegebenen Vorgänge auszuführen).

Wenn die Validierung fehlschlägt, wird eine Ausnahme ausgelöst und die Protokolldatei enthält Details, die erklären, warum das DDX-Dokument ungültig ist. Diese Details können Sie von der `OperationException`-Instanz abgerufen werden. Nach der grundlegenden XML-Analyse und Schemaprüfung wird die Validierung anhand der DDX-Spezifikation durchgeführt. Alle im DDX-Dokument enthaltenen Fehler werden im Protokoll angegeben.

**Speichern der Prüfergebnisse in einer Protokolldatei**

Der Assembler-Dienst gibt die Validierungsergebnisse zurück, die Sie in eine XML-Protokolldatei schreiben können. Die Menge der Details, die der Assembler-Service in die Protokolldatei schreibt, hängt von der von Ihnen festgelegten Laufzeitoption ab.

**Siehe auch**

[Überprüfen eines DDX-Dokuments mit der Java-API](#validate-a-ddx-document-using-the-java-api)

[Validieren eines DDX-Dokuments mithilfe der Webservice-API](#validate-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatisches Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Überprüfen eines DDX-Dokuments mit der Java-API {#validate-a-ddx-document-using-the-java-api}

Validieren Sie ein DDX-Dokument mithilfe der Assembler Service-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie eine `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, mit der der Assembler-Service angewiesen wird, das DDX-Dokument zu validieren, indem Sie die setValidateOnly-Methode des `AssemblerOptionSpec`-Objekts aufrufen und `true` übergeben.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Service in die Protokolldatei schreibt, indem Sie der `getLogLevel`-Methode des `AssemblerOptionSpec`-Objekts und den Zeichenfolgenwert übergeben, der Ihre Anforderungen erfüllt. Beim Validieren eines DDX-Dokuments sollten weitere Informationen in die Protokolldatei geschrieben werden, die für den Validierungsprozess hilfreich sind. Folglich können Sie den Wert `FINE` oder `FINER` übergeben.

1. Führen Sie die Überprüfung durch.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das java.io.Map-Objekt, das normalerweise PDF-Dokumente speichert.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt.

   Die Methode `invokeDDX` gibt ein `AssemblerResult`-Objekt zurück, das Informationen darüber enthält, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die Methode `getJobLog` des `AssemblerResult`-Objekts auf. Diese Methode gibt eine `com.adobe.idp.Document`-Instanz zurück, die Validierungsinformationen enthält.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren.

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird eine `OperationException` ausgelöst. Innerhalb der catch-Anweisung können Sie die Methode `getJobLog` des `OperationException`-Objekts aufrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[Kurzanleitung (SOAP-Modus): Validieren von DDX-Dokumenten mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api) (SOAP-Modus)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Validieren eines DDX-Dokuments mithilfe der Webservice-API {#validate-a-ddx-document-using-the-web-service-api}

So validieren Sie ein DDX-Dokument mithilfe der Assembler Service-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie „localhost“ durch die IP-Adresse des Formular-Servers.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert mit der WSDL an den AEM Forms-Service (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekr, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein Objekt `System.IO.FileStream`, indem Sie den Konstruktor aufrufen und einen String-Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus, in dem die Datei geöffnet werden soll, repräsentiert.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie die Laufzeitoption fest, die den Assembler-Service anweist, das DDX-Dokument zu validieren, indem Sie dem Datenelement `validateOnly` des `AssemblerOptionSpec`-Objekts den Wert „true“ zuweisen.
   * Legen Sie die Menge der Informationen fest, die der Assembler-Service in die Protokolldatei schreibt, indem Sie dem Datenelement `logLevel` des `AssemblerOptionSpec`-Objekts einen Zeichenfolgenwert zuweisen. Bei der Validierung eines DDX-Dokuments sollten mehr Informationen in die Protokolldatei geschrieben werden, um den Validierungsprozess zu unterstützen. Daher können Sie den Wert `FINE` oder `FINER` angeben. Weitere Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Führen Sie die Überprüfung durch.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das `Map`-Objekt, das normalerweise PDF-Dokumente speichert.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das Informationen enthält, die angeben, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und ihm einen Zeichenfolgenwert übergeben, der den Dateispeicherort der Protokolldatei und den Modus zum Öffnen der Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein `BLOB`-Objekt, das Protokollinformationen speichert, indem Sie den Wert des `jobLog`-Datenelements des `AssemblerResult`-Objekts abrufen.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `BLOB`-Objekts gespeichert wird. Füllen Sie das Byte-Array, indem Sie den Wert aus dem `MTOM`-Feld des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des `System.IO.BinaryWriter`-Objekts aufrufen und ihr das Byte-Array übergeben.

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird eine `OperationException` ausgelöst. Innerhalb der catch-Anweisung können Sie den Wert des `jobLog`-Elements des `OperationException`-Objekts abrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
