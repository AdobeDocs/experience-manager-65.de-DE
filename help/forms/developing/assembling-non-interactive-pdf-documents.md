---
title: Zusammenstellen von nicht interaktiven PDF-Dokumenten
seo-title: Assembling Non-Interactive PDF Documents
description: Verwenden Sie ein nicht interaktives PDF-Formular als Eingabe, um ein nicht interaktives PDF-Dokument mithilfe der Java-API und der Web Service-API zusammenzustellen.
seo-description: Use a non-interactive PDF form as input to assemble a non-interactive PDF document using the Java API and Web Service API.
uuid: 0c7adeb4-9a3a-4ec5-ba33-c3642928d4ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8a75c201-bd88-4809-be08-69de94656489
role: Developer
exl-id: 4677b9e5-3811-4de3-b4f4-9574b5898486
source-git-commit: 135f50cc80f8bb449b2f1621db5e2564f5075968
workflow-type: ht
source-wordcount: '1775'
ht-degree: 100%

---

# Zusammenstellen von nicht interaktiven PDF-Dokumenten {#assembling-non-interactive-pdf-documents}

Sie können ein nicht interaktives PDF-Dokument zusammenstellen, wenn Sie ein interaktives PDF-Formular als Eingabe verwenden. Angenommen, Sie verfügen über ein Formular, mit dem Benutzer Daten in die Felder eingeben können. Sie können dieses Formular an den Assembler-Dienst übergeben, was dazu führt, dass der Assembler-Dienst ein PDF-Dokument zurückgibt, das die Eingabe von Daten durch Benutzer verhindert. Dieses Dokument ist ein nicht interaktives PDF-Formular. Die folgende Abbildung zeigt beispielsweise einen Hypothekenantrag, der ein interaktives Formular darstellt.

Nehmen Sie für dieses Thema bitte an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDF result="out.pdf">
        <PDF source="inDoc"/>
        <NoXFA/>
      </PDF>
 </DDX>
```

Beachten Sie, dass in diesem DDX-Dokument dem Quellattribut der Wert `inDoc` zugewiesen ist. In Fällen, in denen nur ein Eingabedokument an den Assembler-Dienst übergeben und ein PDF-Dokument zurückgegeben wird, und Sie den `invokeOneDocument`-Vorgang aufrugen, weisen Sie dem PDF-Quellattribut den Wert `inDoc` zu. Beim Aufrufen des `invokeOneDocument`-Vorgangs, ist der `inDoc`-Wert ein vordefinierter Schlüssel, der im DDX-Dokument angegeben werden muss.

Wenn Sie dagegen zwei oder mehr PDF-Eingabedokumente an den Assembler-Dienst übergeben, können Sie den `invokeDDX`-Vorgang aufrufen. Weisen Sie in diesem Fall den Dateinamen des PDF-Eingabedokuments dem `source`-Attribut zu.

Dieses DDX-Dokument enthält das `NoXFA`-Element, das den Assembler-Dienst anweist, ein nicht interaktives PDF-Dokument zurückzugeben.

Der Assembler-Dienst kann nicht interaktive PDF-Dokumente zusammenstellen, ohne dass der Output-Dienst Teil Ihrer AEM Forms-Installation ist, wenn das Eingabedokument auf einem Acrobat-Formular oder einem statischen XFA-Formular basiert. Wenn das PDF-Eingabedokument jedoch ein dynamisches XFA-PDF-Formular ist, muss der Output-Dienst Teil Ihrer AEM Forms-Installation sein. Wenn der Output-Dienst nicht Teil Ihrer AEM Forms-Installation ist, wenn ein dynamisches XFA-Formular assembliert wird, wird eine Ausnahme ausgelöst. Siehe [Erstellen von Document Output Streams](/help/forms/developing/creating-document-output-streams.md).

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden keine Konzepte besprochen, wie das Erstellen eines Sammlungsgegenstands mit Eingabedokumenten oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Sammlungsgegenstand. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie zum Zusammenführen eines nicht interaktiven PDF-Dokuments die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein interaktives PDF-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Stellen Sie das PDF-Dokument zusammen.
1. Speichern Sie das nicht interaktive PDF-Dokument.

**Schließen Sie Projektdateien ein**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien adobe-utilities.jar- und jbossall-client.jar-Dateien durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Referenzieren eines bestehenden DDX-Dokuments**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss Folgendes enthalten: `NoXFA`-Element, das den Assembler-Dienst anweist, ein nicht interaktives PDF-Dokument zurückzugeben.

**Referenzieren eines interaktiven PDF-Dokuments**

Ein interaktives PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um ein nicht interaktives PDF-Dokument wiederherzustellen.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Zusammenführen des PDF-Dokuments**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, auf das DDX-Dokument verweisen, auf ein interaktives PDF-Dokument verweisen und Laufzeitoptionen festlegen, können Sie den `invokeOneDocument`-Vorgang auslösen. Da nur ein PDF-Eingabedokument an den Assembler-Dienst übergeben und ein einziges Dokument zurückgegeben wird, können Sie den `invokeOneDocument`-Vorgang im Gegensatz zum `invokeDDX`-Vorgang verwenden.

**Speichern Sie das nicht interaktive PDF-Dokument**

Wenn nur ein einzelnes PDF-Dokument an den Assembler-Dienst übergeben wird, gibt der Assembler-Dienst anstelle eines Sammlungsobjekts ein einzelnes Dokument zurück. Das heißt, beim Aufrufen des `invokeOneDocument`-Vorgangs wird ein einzelnes Dokument zurückgegeben. Da das in diesem Abschnitt referenzierte DDX-Dokument Anweisungen zum Erstellen eines nicht interaktiven PDF-Dokuments enthält, gibt der Assembler-Dienst ein nicht interaktives PDF-Dokument zurück, das als PDF-Datei gespeichert werden kann.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatisches Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenführen eines nicht interaktiven PDF-Dokuments mithilfe der Java-API {#assemble-a-non-interactive-pdf-document-using-the-java-api}

Assemblieren eines nicht interaktiven PDF-Dokuments mithilfe der Assembler-Dienst-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein interaktives PDF-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort eines interaktiven PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält. Dieses `com.adobe.idp.Document`-Objekt wird der `invokeOneDocument`-Methode übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die Methode `setFailOnError` des `AssemblerOptionSpec`-Objekts auf und übergeben `false`.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `invokeOneDocument`-Methode des `AssemblerServiceClient`-Objekts auf und übergeben Sie ihr die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das DDX-Dokument darstellt. Stellen Sie sicher, dass dieses DDX-Dokument den Wert `inDoc` für das PDF-Quellelement enthält.
   * Ein `com.adobe.idp.Document`-Objekt, das das interaktive PDF-Dokument enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der standardmäßigen Schrift und Auftragsprotokollebene.

   Die `invokeOneDocument`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf lautet.
   * Rufen Sie die Methode `copyToFile` des `Document`-Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das die Methode `invokeOneDocument` zurückgegeben hat.

* „Schnellstartanleitung (SOAP-Modus): Zusammenstellen eines nicht interaktiven PDF-Dokuments mithilfe der Java-API“

## Zusammenführen eines nicht interaktiven PDF-Dokuments mithilfe der Webservice-API {#assemble-a-non-interactive-pdf-document-using-the-web-service-api}

Assemblieren eines nicht interaktiven PDF-Dokuments mithilfe der Assembler-Service-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt unter Verwendung seines Standardkonstruktors.
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
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays seinem `MTOM`-Feld zuweisen.

1. Referenzieren Sie ein interaktives PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB`-Objekt wird dem `invokeOneDocument` als Argument übergeben.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus zum Öffnen der Datei angibt.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen Feld `MTOM` mit dem Inhalt des Byte-Arrays belegen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem Datenelement `failOnError` des `AssemblerOptionSpec`-Objekts zu.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die Methode `invokeOneDocument` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Ein `BLOB`-Objekt, das das interaktive PDF-Dokument darstellt
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeOneDocument`-Methode gibt eine `BLOB`-Objekt zurück, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des nicht interaktiven PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des von der `invokeOneDocument`-Methode zurückgegebenen `BLOB`-Objekts gespeichert wird. Füllen Sie das Byte-Array, indem Sie den Wert aus dem `MTOM`-Feld des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

* „Schnellstartanleitung (MTOM): Zusammenstellen eines nicht interaktiven PDF-Dokuments mithilfe der Web-Service-API“.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
