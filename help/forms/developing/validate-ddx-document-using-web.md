---
title: Überprüfen eines DDX-Dokuments mithilfe der Webdienst-API
seo-title: Überprüfen eines DDX-Dokuments mithilfe der Webdienst-API
description: Verwenden Sie die Assembler-Dienst-API zum Überprüfen eines DDX-Dokuments.
seo-description: Verwenden Sie die Assembler-Dienst-API zum Überprüfen eines DDX-Dokuments.
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
role: Developer
exl-id: 069e5b10-ab93-4492-a70d-6a0d462105a6
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 2%

---

# Validieren eines DDX-Dokuments mithilfe der Webdienst-API {#validate-a-ddx-document-using-theweb-service-api}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

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

[Validieren von DDX-Dokumenten](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
