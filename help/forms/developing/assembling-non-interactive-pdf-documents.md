---
title: Assemblieren nicht interaktiver PDF-Dokumente
seo-title: Assemblieren nicht interaktiver PDF-Dokumente
description: Verwenden Sie ein nicht interaktives PDF-Formular als Eingabe, um ein nicht interaktives PDF-Dokument mithilfe der Java-API und der Web Service-API zusammenzustellen.
seo-description: Verwenden Sie ein nicht interaktives PDF-Formular als Eingabe, um ein nicht interaktives PDF-Dokument mithilfe der Java-API und der Web Service-API zusammenzustellen.
uuid: 0c7adeb4-9a3a-4ec5-ba33-c3642928d4ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8a75c201-bd88-4809-be08-69de94656489
role: Developer
exl-id: 4677b9e5-3811-4de3-b4f4-9574b5898486
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1800'
ht-degree: 2%

---

# Zusammenstellen von nicht interaktiven PDF-Dokumenten {#assembling-non-interactive-pdf-documents}

Sie können ein nicht interaktives PDF-Dokument zusammenstellen, wenn Sie ein interaktives PDF-Formular als Eingabe verwenden. Angenommen, Sie verfügen über ein Formular, mit dem Benutzer Daten in die Felder eingeben können. Sie können dieses Formular an den Assembler-Dienst übergeben, was dazu führt, dass der Assembler-Dienst ein PDF-Dokument zurückgibt, das verhindert, dass Benutzer Daten in seine Felder eingeben. Dieses Dokument ist ein nicht interaktives PDF-Formular. Die folgende Abbildung zeigt beispielsweise einen Hypothekenantrag, der ein interaktives Formular darstellt.

Angenommen, für diese Diskussion wird das folgende DDX-Dokument verwendet.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDF result="out.pdf">
        <PDF source="inDoc"/>
        <NoXFA/>
      </PDF>
 </DDX>
```

Beachten Sie in diesem DDX-Dokument, dass dem Quellattribut der Wert `inDoc` zugewiesen ist. Weisen Sie in Situationen, in denen nur ein PDF-Eingabedokument an den Assembler-Dienst übergeben und ein PDF-Dokument zurückgegeben wird und Sie den Vorgang `invokeOneDocument` aufrufen, den Wert `inDoc` dem PDF-Quellattribut zu. Beim Aufrufen des Vorgangs `invokeOneDocument` ist der Wert `inDoc` ein vordefinierter Schlüssel, der im DDX-Dokument angegeben werden muss.

Wenn Sie hingegen zwei oder mehr PDF-Eingabedokumente an den Assembler-Dienst übergeben, können Sie den Vorgang `invokeDDX` aufrufen. Weisen Sie in diesem Fall den Dateinamen des PDF-Eingabedokuments dem Attribut `source` zu.

Dieses DDX-Dokument enthält das Element `NoXFA` , das den Assembler-Dienst anweist, ein nicht interaktives PDF-Dokument zurückzugeben.

Der Assembler-Dienst kann nicht interaktive PDF-Dokumente zusammenführen, ohne dass der Output-Dienst Teil Ihrer AEM-Formularinstallation ist, wenn das PDF-Eingabedokument auf einem Acrobat-Formular oder einem statischen XFA-Formular basiert. Wenn das PDF-Eingabedokument jedoch ein dynamisches XFA-Formular ist, muss der Output-Dienst Teil Ihrer AEM Forms-Installation sein. Wenn der Output-Dienst nicht Teil Ihrer AEM Forms-Installation ist, wenn ein dynamisches XFA-Formular assembliert wird, wird eine Ausnahme ausgelöst. Siehe [Erstellen von Document Output Streams](/help/forms/developing/creating-document-output-streams.md).

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden keine Konzepte besprochen, wie das Erstellen eines Kollektionsobjekts mit Eingabedokumenten oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Kollektionsobjekt. (Siehe [Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein nicht interaktives PDF-Dokument zusammenzuführen:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren eines interaktiven PDF-Dokuments.
1. Legen Sie Laufzeitoptionen fest.
1. Assemblieren des PDF-Dokuments.
1. Speichern Sie das nicht interaktive PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss das Element `NoXFA` enthalten, das den Assembler-Dienst anweist, ein nicht interaktives PDF-Dokument zurückzugeben.

**Referenzieren eines interaktiven PDF-Dokuments**

Ein interaktives PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um ein nicht interaktives PDF-Dokument wiederherzustellen.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Zusammenführen des PDF-Dokuments**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, auf das DDX-Dokument verweisen, auf ein interaktives PDF-Dokument verweisen und Laufzeitoptionen festgelegt haben, können Sie den Vorgang `invokeOneDocument` aufrufen. Da nur ein PDF-Eingabedokument an den Assembler-Dienst übergeben und ein einzelnes Dokument zurückgegeben wird, können Sie den Vorgang `invokeOneDocument` im Gegensatz zum Vorgang `invokeDDX` verwenden.

**Speichern Sie das nicht interaktive PDF-Dokument**

Wenn nur ein einziges PDF-Dokument an den Assembler-Dienst übergeben wird, gibt der Assembler-Dienst ein einzelnes Dokument anstelle eines Collection-Objekts zurück. Das heißt, beim Aufrufen des Vorgangs `invokeOneDocument` wird ein einzelnes Dokument zurückgegeben. Da das in diesem Abschnitt referenzierte DDX-Dokument Anweisungen zum Erstellen eines nicht interaktiven PDF-Dokuments enthält, gibt der Assembler-Dienst ein nicht interaktives PDF-Dokument zurück, das als PDF-Datei gespeichert werden kann.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenführen eines nicht interaktiven PDF-Dokuments mit der Java-API {#assemble-a-non-interactive-pdf-document-using-the-java-api}

Assemblieren eines nicht interaktiven PDF-Dokuments mithilfe der Assembler-Dienst-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren eines interaktiven PDF-Dokuments.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie dessen Konstruktor verwenden und den Speicherort eines interaktiven PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält. Dieses `com.adobe.idp.Document`-Objekt wird an die `invokeOneDocument`-Methode übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `setFailOnError` -Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Assemblieren des PDF-Dokuments.

   Rufen Sie die `invokeOneDocument` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das DDX-Dokument darstellt. Stellen Sie sicher, dass dieses DDX-Dokument den Wert `inDoc` für das PDF-Quellelement enthält.
   * Ein `com.adobe.idp.Document` -Objekt, das das interaktive PDF-Dokument enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der standardmäßigen Schrift- und Auftragsprotokollebene.

   Die `invokeOneDocument`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile` -Methode des Objekts `Document` auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `invokeOneDocument`-Methode zurückgegeben wurde.

* &quot;Schnellstart (SOAP-Modus): Assemblieren eines nicht interaktiven PDF-Dokuments mit der Java-API&quot;

## Zusammenführen eines nicht interaktiven PDF-Dokuments mithilfe der Webdienst-API {#assemble-a-non-interactive-pdf-document-using-the-web-service-api}

Assemblieren eines nicht interaktiven PDF-Dokuments mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Assembler-Client.

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
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren eines interaktiven PDF-Dokuments.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB` -Objekt wird als Argument an `invokeOneDocument` übergeben.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec` -Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem `AssemblerOptionSpec`-Datenelement des `failOnError`-Objekts zu.

1. Assemblieren des PDF-Dokuments.

   Rufen Sie die `invokeOneDocument` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das DDX-Dokument darstellt
   * Ein `BLOB` -Objekt, das das interaktive PDF-Dokument darstellt
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeOneDocument`-Methode gibt ein `BLOB`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des nicht interaktiven PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `invokeOneDocument` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

* &quot;Schnellstart (MTOM): Assemblieren eines nicht interaktiven PDF-Dokuments mithilfe der Webdienst-API&quot;.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
