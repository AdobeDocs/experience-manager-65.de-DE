---
title: Aufteilen eines PDF-Dokuments mithilfe der Webservice-API
seo-title: Disassemble a PDF document usingthe web service API
description: Aufteilen eines PDF-Dokuments mithilfe der Assembler-Service-API
seo-description: Disassemble a PDF document using the Assembler Service API
uuid: d6283dc5-e333-49d0-abde-1d390662f4fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/programmatically_disassembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 49584fb4-8c3a-4d73-acd6-0879a67f6093
role: Developer
exl-id: de2f90ad-5dea-40a0-8c6d-d6b08228310d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '718'
ht-degree: 100%

---

# Aufteilen eines PDF-Dokuments mithilfe der Webdienst-API {#disassemble-a-pdf-document-usingthe-web-service-api}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Aufteilen eines PDF-Dokuments mithilfe der Assembler-Service-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Service-Referenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt mithilfe von dessen Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Wertes des `AssemblerServiceClient.Endpoint.Binding`-Feldes. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem `AssemblerServiceClient.ClientCredentials.UserName.UserName`-Feld den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem `AssemblerServiceClient.ClientCredentials.UserName.Password`-Feld den entsprechenden Kennwortwert zu.
      * Weisen Sie den Konstantenwert `HttpClientCredentialType.Basic` zum `BasicHttpBindingSecurity.Transport.ClientCredentialType`-Feld zu.
      * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zum `BasicHttpBindingSecurity.Security.Mode`-Feld zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie dessen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert für den Dateispeicherort des DDX-Dokuments und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt durch Zuweisen des Inhalts des Byte-Arrays zu dessen `MTOM`-Eigenschaft.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB`-Objekt wird als Argument an `invokeOneDocument` übergeben.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen von dessen Konstruktor und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des Eingabedokuments und den PDF-Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt durch Zuweisen des Inhalts des Byte-Arrays zu dessen `MTOM`-Feld.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Sammlungsobjekt wird verwendet, um das aufzuteilende PDF-Dokument zu speichern.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie einen Zeichfolgenwert, der den Schlüsselnamen darstellt, zum `key`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, das das PDF-Dokument speichert, zum `value`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt zum `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die `Add`-Methode des `MyMapOf_xsd_string_To_xsd_anyType`-Objekts auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe von dessen Konstruktor speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einen Wert zu einem Datenelement zuweisen, das zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Vorgangs fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem `failOnError`-Feld des `AssemblerOptionSpec`-Objekts zu.

1. Zerlegen Sie das PDF-Dokument.

   Rufen Sie die `invokeDDX`-Methode des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt, das das PDF-Dokument aufteilt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das das aufzuteilende PDF-Dokument enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Vorgangsergebnisse und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die neu erstellten PDF-Dokumente abzurufen:

   * Greifen Sie auf das `documents`-Feld des `AssemblerResult`-Objekts zu, dies ein `Map`-Objekt, das die aufgeteilten PDF-Dokumente enthält.
   * Iterieren Sie durch das `Map`-Objekt, um alle Zieldokumente abzurufen. Wandeln Sie dann `value` des Array-Elements in `BLOB` um.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB`-Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Programmgesteuerte Aufteilung von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
