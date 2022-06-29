---
title: Überprüfen eines DDX-Dokuments mithilfe der Web-Service-API
seo-title: Validate a DDX document using theweb service API
description: Verwenden Sie die Assembler-Service-API zum Überprüfen eines DDX-Dokuments.
seo-description: Use the Assembler Service API to validate a DDX document.
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
role: Developer
exl-id: 069e5b10-ab93-4492-a70d-6a0d462105a6
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '640'
ht-degree: 100%

---

# Validieren eines DDX-Dokuments mithilfe der Webservice-API {#validate-a-ddx-document-using-theweb-service-api}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

So validieren Sie ein DDX-Dokument mithilfe der Assembler Service-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie localhost durch die IP-Adresse des Formularservers.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt mithilfe seines Standardkonstruktors.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service festlegt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts im Feld `AssemblerServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld des `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt durch Zuweisen seiner `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, die den Assembler-Service anweist, das DDX-Dokument zu überprüfen, indem Sie dem `validateOnly`-Datenelement des `AssemblerOptionSpec`-Objekts den Wert „true“ zuweisen.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Service in die Protokolldatei schreibt, indem Sie dem `logLevel`-Datenelement des `AssemblerOptionSpec`-Objekts einen Zeichenfolgenwert zuweisen. Bei der Validierung eines DDX-Dokuments sollten mehr Informationen in die Protokolldatei geschrieben werden, um den Validierungsprozess zu unterstützen. Daher können Sie den Wert `FINE` oder `FINER` festlegen. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie unter der Klassenreferenz `AssemblerOptionSpec` in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `invokeDDX`-Methode des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das `Map`-Objekt, das normalerweise PDF-Dokumente speichert.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `invokeDDX`-Methode gibt eine `AssemblerResult`-Objekt mit Informationen zurück, die angeben, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort der Protokolldatei und den Modus zum Öffnen der Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein `BLOB`-Objekt, das Protokollinformationen speichert, indem es den Wert des `jobLog`-Datenelements des `AssemblerResult`-Objekts abruft.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert. Füllen Sie das Byte-Array, indem Sie den Wert des `MTOM`-Felds des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird eine `OperationException` ausgelöst. Innerhalb der catch-Anweisung können Sie den Wert des `jobLog`-Elements des `OperationException`-Objekts abrufen.

**Siehe auch**

[Validieren von DDX-Dokumenten](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
