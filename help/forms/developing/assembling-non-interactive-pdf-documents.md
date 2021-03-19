---
title: Zusammenstellen von nicht interaktiven PDF-Dokumenten
seo-title: Zusammenstellen von nicht interaktiven PDF-Dokumenten
description: Verwenden Sie ein nicht interaktives PDF-Formular als Eingabe, um ein nicht interaktives PDF-Dokument mit der Java-API und der Webdienst-API zusammenzustellen.
seo-description: Verwenden Sie ein nicht interaktives PDF-Formular als Eingabe, um ein nicht interaktives PDF-Dokument mit der Java-API und der Webdienst-API zusammenzustellen.
uuid: 0c7adeb4-9a3a-4ec5-ba33-c3642928d4ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8a75c201-bd88-4809-be08-69de94656489
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1801'
ht-degree: 2%

---


# Zusammenstellen von nicht interaktiven PDF-Dokumenten {#assembling-non-interactive-pdf-documents}

Sie können ein nicht interaktives PDF-Dokument zusammenstellen, wenn Sie ein interaktives PDF-Formular als Eingabe verwenden. Angenommen, Sie verfügen über ein Formular, mit dem Benutzer Daten in die Felder eingeben können. Sie können dieses Formular an den Assembler-Dienst weiterleiten, sodass der Assembler-Dienst ein PDF-Dokument zurückgibt, das die Eingabe von Daten durch Benutzer verhindert. Dieses Dokument ist ein nicht interaktives PDF-Formular. Die folgende Abbildung zeigt beispielsweise einen Hypothekenantrag, der ein interaktives Formular darstellt.

Für diese Diskussion nehmen Sie an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDF result="out.pdf">
        <PDF source="inDoc"/>
        <NoXFA/>
      </PDF>
 </DDX>
```

Beachten Sie, dass dem Quellattribut in diesem DDX-Dokument der Wert `inDoc` zugewiesen ist. Weisen Sie in Fällen, in denen nur ein PDF-Eingabedokument an den Assembler-Dienst und ein PDF-Dokument zurückgegeben wird und Sie den Vorgang `invokeOneDocument` aufrufen, dem PDF-Quellattribut den Wert `inDoc` zu. Beim Aufrufen des Vorgangs `invokeOneDocument` ist der Wert `inDoc` ein vordefinierter Schlüssel, der im DDX-Dokument angegeben werden muss.

Wenn Sie dagegen zwei oder mehr PDF-Eingabedateien an den Assembler-Dienst übergeben, können Sie den Vorgang `invokeDDX` aufrufen. Weisen Sie in diesem Fall dem Attribut `source` den Dateinamen des PDF-Eingabedokuments zu.

Dieses DDX-Dokument enthält das Element `NoXFA`, das den Assembler-Dienst anweist, ein nicht interaktives PDF-Dokument zurückzugeben.

Der Assembler-Dienst kann nicht interaktive PDF-Dokumente zusammenstellen, ohne dass der Output-Dienst in Ihrer AEM Forms-Installation enthalten ist, wenn das Eingabe-PDF-Dokument auf einem Acrobat-Formular oder einem statischen XFA-Formular basiert. Wenn es sich bei dem PDF-Dokument für die Eingabe jedoch um ein dynamisches XFA-Formular handelt, muss der Output-Dienst bei Ihrer AEM Forms-Installation enthalten sein. Wenn der Output-Dienst nicht Teil Ihrer AEM Forms-Installation ist, wenn ein dynamisches XFA-Formular assembliert wird, wird eine Ausnahme ausgelöst. Siehe [Erstellen von Dokument-Ausgabestreams](/help/forms/developing/creating-document-output-streams.md).

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden keine Konzepte beschrieben, wie z. B. das Erstellen eines Collection-Objekts, das Eingabedokumente enthält, oder das Extrahieren der Dokumente aus dem zurückgegebenen Collection-Objekt. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So assemblieren Sie ein nicht interaktives PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Verweisen Sie auf ein interaktives PDF-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Stellen Sie das PDF-Dokument zusammen.
1. Speichern Sie das nicht interaktive PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss das Element `NoXFA` enthalten, das den Assembler-Dienst anweist, ein nicht interaktives PDF-Dokument zurückzugeben.

**Referenzieren eines interaktiven PDF-Dokuments**

Ein interaktives PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um ein nicht interaktives PDF-Dokument zurückzuerhalten.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren.

**Zusammenstellen des PDF-Dokuments**

Nachdem Sie den Assembler-Dienstclient erstellt haben, auf das DDX-Dokument verweisen, ein interaktives PDF-Dokument referenzieren und Laufzeitoptionen festlegen, können Sie den Vorgang `invokeOneDocument` aufrufen. Da nur ein PDF-Eingabedokument an den Assembler-Dienst übergeben wird und ein einziges Dokument zurückgegeben wird, können Sie den Vorgang `invokeOneDocument` anstelle des Vorgangs `invokeDDX` verwenden.

**Nicht interaktives PDF-Dokument speichern**

Wenn nur ein einziges PDF-Dokument an den Assembler-Dienst übergeben wird, gibt der Assembler-Dienst ein einzelnes Dokument anstelle eines Collection-Objekts zurück. Das heißt, beim Aufrufen des Vorgangs `invokeOneDocument` wird ein einzelnes Dokument zurückgegeben. Da das in diesem Abschnitt referenzierte DDX-Dokument Anweisungen zum Erstellen eines nicht interaktiven PDF-Dokuments enthält, gibt der Assembler-Dienst ein nicht interaktives PDF-Dokument zurück, das als PDF-Datei gespeichert werden kann.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenstellen eines nicht interaktiven PDF-Dokuments mit der Java-API {#assemble-a-non-interactive-pdf-document-using-the-java-api}

Stellen Sie ein nicht interaktives PDF-Dokument mit der Assembler Service API (Java) zusammen:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf ein interaktives PDF-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie dessen Konstruktor verwenden und den Speicherort eines interaktiven PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält. Dieses `com.adobe.idp.Document`-Objekt wird an die `invokeOneDocument`-Methode übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `setFailOnError`-Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `invokeOneDocument`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das DDX-Dokument darstellt. Stellen Sie sicher, dass dieses DDX-Dokument den Wert `inDoc` für das PDF-Quellelement enthält.
   * Ein `com.adobe.idp.Document`-Objekt, das das interaktive PDF-Dokument enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen einschließlich der standardmäßigen Schriftart- und Auftragsprotokollebene angibt.

   Die `invokeOneDocument`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. `Document` Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `invokeOneDocument`-Methode zurückgegeben wurde.

* &quot;Quick Beginn (SOAP-Modus): Zusammenstellen eines nicht interaktiven PDF-Dokuments mit der Java-API&quot;

## Zusammenstellen eines nicht interaktiven PDF-Dokuments mit der Webdienst-API {#assemble-a-non-interactive-pdf-document-using-the-web-service-api}

Stellen Sie ein nicht interaktives PDF-Dokument mit der Assembler Service API (Webdienst) zusammen:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Assembler-Client.

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
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf ein interaktives PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB`-Objekt wird als Argument an das `invokeOneDocument`-Objekt übergeben.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedatums und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenmember, der zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie `false` dem `AssemblerOptionSpec`-Datenmember des Objekts `failOnError` zu.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `invokeOneDocument`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Ein `BLOB`-Objekt, das das interaktive PDF-Dokument darstellt
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeOneDocument`-Methode gibt ein `BLOB`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des nicht interaktiven PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB`-Objekts speichert, das von der `invokeOneDocument`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

* &quot;Quick Beginn (MTOM): Zusammenstellen eines nicht interaktiven PDF-Dokuments mit der Webdienst-API&quot;.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
