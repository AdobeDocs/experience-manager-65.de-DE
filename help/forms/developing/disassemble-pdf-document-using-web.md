---
title: Aufteilen eines PDF-Dokuments mithilfe der Webservice-API
description: Aufteilen eines PDF-Dokuments mithilfe der Assembler-Dienst-API
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/programmatically_disassembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Developer
exl-id: de2f90ad-5dea-40a0-8c6d-d6b08228310d
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 516393bc-fa69-5e74-a04e-f7ec9ffe2c5e
    internal-label: APIs & Integrations
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
  - id: f19cff18-c8cc-4a4b-adad-85dd2fa3dbe2
    internal-label: Document Services
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 100%
---
# Aufteilen eines PDF-Dokuments mithilfe der Webdienst-API {#disassemble-a-pdf-document-usingthe-web-service-api}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Aufteilen eines PDF-Dokuments mithilfe der Assembler-Dienst-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Service-Referenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert mit der WSDL an den AEM Forms-Service (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `AssemblerServiceClient.Endpoint.Binding`-Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie das `MessageEncoding`-Feld des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom` fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

     * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
     * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
     * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
     * Weisen Sie den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert für den Dateispeicherort des DDX-Dokuments und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays belegen.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB`-Objekt wird an `invokeOneDocument` als Argument übergeben.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Eingabe-PDF-Dokuments und den Modus enthält, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld die Inhalte des Byte-Arrays zuweisen.
   * Erstellen eines `MyMapOf_xsd_string_To_xsd_anyType`-Objekts. Dieses Sammlungsobjekt wird verwendet, um das aufzuteilende PDF-Dokument zu speichern.
   * Erstellen Sie ein Objekt `MyMapOf_xsd_string_To_xsd_anyType_Item`.
   * Weisen Sie dem `key`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts einen Zeichenfolgewert zu, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, welches das PDF-Dokument speichert, dem `value`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` Objekt `Add`-Methode auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem `failOnError`-Feld des `AssemblerOptionSpec`-Objekts zu.

1. Zerlegen Sie das PDF-Dokument.

   Rufen Sie die `invokeDDX`-Methode des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, welches das DDX-Dokument darstellt, das das PDF-Dokument zerlegt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, welches das zu zerlegende PDF-Dokument enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Auftragsergebnisse und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die neu erstellten PDF-Dokumente abzurufen:

   * Greifen Sie auf das `documents`-Feld des `AssemblerResult`-Objekts zu. Dies ist ein `Map`-Objekt, das die zerlegten PDF-Dokumente enthält.
   * Iterieren Sie durch das `Map`-Objekt, um jedes resultierende Dokument zu erhalten. Wandeln Sie dann `value` der Array-Elemente in `BLOB` um.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `MTOM`-Eigenschaft des `BLOB`-Objekts zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Programmgesteuerte Aufteilung von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
