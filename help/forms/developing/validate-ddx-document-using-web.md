---
title: Überprüfen eines DDX-Dokuments mithilfe der Web-Service-API
description: Verwenden Sie die Assembler-Service-API zum Überprüfen eines DDX-Dokuments.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Developer
exl-id: 069e5b10-ab93-4492-a70d-6a0d462105a6
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '634'
ht-degree: 100%

---

# Validieren eines DDX-Dokuments mithilfe der Webservice-API {#validate-a-ddx-document-using-theweb-service-api}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

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

[Validieren von DDX-Dokumenten](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
