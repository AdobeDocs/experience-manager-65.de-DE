---
title: Zusammenstellen von PDF-Dokumenten mit Lesezeichen
seo-title: Zusammenstellen von PDF-Dokumenten mit Lesezeichen
description: 'null'
seo-description: 'null'
uuid: a306d2a6-0b12-4eb3-bff4-968a33417486
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f4711a8-033c-4051-ab41-65a26838899b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Zusammenstellen von PDF-Dokumenten mit Lesezeichen {#assembling-pdf-documents-with-bookmarks}

Sie können ein PDF-Dokument zusammenstellen, das Lesezeichen enthält. Angenommen, Sie haben ein PDF-Dokument, das keine Lesezeichen enthält, und Sie möchten es mithilfe von Lesezeichen ändern. Mit dem Assembler-Dienst können Sie ein PDF-Dokument ohne Lesezeichen übergeben und ein PDF-Dokument mit Lesezeichen zurückerhalten.

Lesezeichen enthalten die folgenden Eigenschaften:

* Ein Titel, der als Text auf dem Bildschirm angezeigt wird.
* Eine Aktion, die angibt, was passiert, wenn ein Benutzer auf das Lesezeichen klickt. Die typische Aktion für ein Lesezeichen besteht darin, zu einem anderen Speicherort im aktuellen Dokument zu wechseln oder ein anderes PDF-Dokument zu öffnen. Es können jedoch auch andere Aktionen angegeben werden.

Für diese Diskussion nehmen Sie an, dass das folgende DDX-Dokument verwendet wird.

```as3
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
       <PDF result="FinalDoc.pdf">
          <PDF source="Loan.pdf">
             <Bookmarks source="doc2" />
          </PDF>
       </PDF>
 </DDX>
```

Beachten Sie in diesem DDX-Dokument, dass dem Quellattribut der Wert zugewiesen wurde `Loan.pdf`. Dieses DDX-Dokument gibt an, dass ein einzelnes PDF-Dokument an den Assembler-Dienst übergeben wird. Beim Zusammenstellen eines PDF-Dokuments mit Lesezeichen müssen Sie ein XML-Lesezeichen-Dokument angeben, das die Lesezeichen im Ergebnisdokument beschreibt. Um ein XML-Lesezeichen-Dokument anzugeben, stellen Sie sicher, dass das `Bookmarks` Element in Ihrem DDX-Dokument angegeben ist.

In diesem Beispiel DDX-Dokument gibt das `Bookmarks` Element `doc2` als Wert an. Dieser Wert gibt an, dass die an den Assembler-Dienst übergebene Eingabemap einen Schlüssel mit dem Namen `doc2`enthält. Der Wert des `doc2` Schlüssels ist ein `com.adobe.idp.Document` Wert, der das XML-Lesezeichen darstellt. (Siehe &quot;Lesezeichensprache&quot;im [Assembler-Dienst und in der DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).)

In diesem Thema wird die folgende Sprache für XML-Lesezeichen verwendet, um ein PDF-Dokument mit Lesezeichen zusammenzustellen.

```as3
 <?xml version="1.0" encoding="UTF-8"?>
 <Bookmarks xmlns="https://ns.adobe.com/pdf/bookmarks" version="1.0">
       <Bookmark>
          <Action>
             <Launch NewWindow="true">
                <File Name="C:\Adobe\LoanDetails.pdf" />
             </Launch>
          </Action>
         <Title>Open the Loan document</Title>
       </Bookmark>
 <Bookmark>
          <Action>
             <Launch>
                <Win Name="C:\WINDOWS\notepad.exe" />
             </Launch>
          </Action>
     <Title>Launch NotePad</Title>
       </Bookmark>
 </Bookmarks>
```

Beachten Sie in diesem XML-Lesezeichen das Aktionselement, das die Aktion definiert, die ausgeführt wird, wenn ein Benutzer auf das Lesezeichen klickt. Unter dem Element Aktion befindet sich das Element Launch, mit dem Anwendungen wie NotePad gestartet und Dateien wie PDF-Dateien geöffnet werden. Um eine PDF-Datei zu öffnen, müssen Sie das Dateielement verwenden, das die zu öffnende Datei angibt. In der in diesem Abschnitt angegebenen XML-Datei für Lesezeichen lautet der Name der geöffneten Datei beispielsweise LoanDetails.pdf.

>[!NOTE]
>
>Ausführliche Informationen zu unterstützten Aktionen finden Sie unter &quot; `Action` element&quot;im [Assembler-Dienst und in der DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

Da das in diesem Abschnitt angegebene DDX-Dokument und die XML-Lesezeichendatei als Eingabe dienen, assembliert der Assembler-Dienst ein PDF-Dokument, das die folgenden Lesezeichen enthält.

![aw_aw_bmark](assets/aw_aw_bmark.png)

Wenn ein Benutzer auf das Lesezeichen *Öffnen der Kreditdetails* klickt, wird die Datei &quot;LoanDetails.pdf&quot;geöffnet. Wenn der Benutzer auf das Lesezeichen *StartnotizPad* klickt, wird NotizPad ebenfalls gestartet.

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden keine Konzepte beschrieben, wie z. B. das Erstellen eines Collection-Objekts, das Eingabedokumente enthält, oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Collection-Objekt. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents).)

>[!NOTE]
>
>For more information about the Assembler service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So assemblieren Sie ein PDF-Dokument mit Lesezeichen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.
1. Verweisen Sie auf das XML-Lesezeichen.
1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen einer Map-Sammlung hinzu.
1. Legen Sie Laufzeitoptionen fest.
1. Stellen Sie das PDF-Dokument zusammen.
1. Speichern Sie das PDF-Dokument mit Lesezeichen.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. For information about the location of all AEM Forms JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss das `Bookmarks` Element enthalten, das den Assembler-Dienst anweist, eine PDF mit Lesezeichen zusammenzustellen. (Ein Beispiel finden Sie im DDX-Dokument, das weiter oben in diesem Abschnitt gezeigt wird.)

**Verweisen auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden**

Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden. Es spielt keine Rolle, ob das referenzierte PDF-Dokument bereits Lesezeichen enthält. Wenn das `Bookmarks` Element ein untergeordnetes Element des PDF-Quellelements ist, ersetzen die Lesezeichen die bereits in der PDF-Quelle vorhandenen Elemente. Wenn Sie jedoch die vorhandenen Lesezeichen beibehalten möchten, stellen Sie sicher, dass das PDF-Quellelement gleichrangig `Bookmarks` ist. Beispiel:

```as3
 <PDF result="foo">
      <PDF source="inDoc"/>
      <Bookmarks source="doc2"/>
 </PDF>
```

**Referenzieren des XML-Lesezeichendokuments**

Um eine PDF-Datei mit neuen Lesezeichen zusammenzustellen, müssen Sie auf ein XML-Lesezeichen verweisen. Das XML-Lesezeichen-Dokument wird innerhalb des Zuordnungsobjekts an den Assembler-Dienst übergeben. (Ein Beispiel finden Sie im XML-Dokument für Lesezeichen, das weiter oben in diesem Abschnitt gezeigt wird.)

>[!NOTE]
>
>Siehe &quot;Lesezeichensprache&quot;im [Assembler-Dienst und in der DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

**Hinzufügen des PDF-Dokuments und des XML-Lesezeichens zu einer Map-Sammlung**

Sie müssen sowohl das PDF-Dokument, dem Lesezeichen hinzugefügt werden, als auch das XML-Lesezeichen zur Map-Sammlung hinzufügen. Daher enthält das Map-Sammlungsobjekt zwei Elemente: ein PDF-Dokument und das XML-Lesezeichen.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec` Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Zusammenführen des PDF-Dokuments**

Verwenden Sie zum Zusammenführen eines PDF-Dokuments, das neue Lesezeichen enthält, den `invokeDDX` Vorgang des Assembler-Dienstes. Der Grund, warum Sie den `invokeDDX` Vorgang im Gegensatz zu anderen Assembler-Dienstvorgängen verwenden müssen, z. B. weil der Assembler-Dienst ein XML-Lesezeichen-Dokument benötigt, das innerhalb des Map-Sammlungsobjekts übergeben wird, `invokeOneDocument` ist der Grund dafür. Dieses Objekt ist ein Parameter des `invokeDDX` Vorgangs.

**Speichern des PDF-Dokuments mit Lesezeichen**

Sie müssen die Ergebnisse aus dem zurückgegebenen Map-Objekt extrahieren und das entsprechende PDF-Dokument speichern. (Siehe &quot;Ergebnisse extrahieren&quot;in [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenführen von PDF-Dokumenten mit Lesezeichen mithilfe der Java-API {#assemble-pdf-documents-with-bookmarks-using-the-java-api}

Assemblieren eines PDF-Dokuments mit Lesezeichen mithilfe der Assembler Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Create an `AssemblerServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, indem Sie dessen Konstruktor verwenden und den Speicherort des PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt mithilfe des Konstruktors und übergeben Sie das `java.io.FileInputStream` Objekt, das das PDF-Dokument enthält.

1. Verweisen Sie auf das XML-Lesezeichen.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, indem Sie dessen Konstruktor verwenden und den Speicherort der XML-Datei übergeben, die das Lesezeichen-XML-Dokument darstellt.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt und übergeben Sie das `java.io.FileInputStream` Objekt, das das PDF-Dokument enthält.

1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen einer Map-Sammlung hinzu.

   * Erstellen Sie ein `java.util.Map` Objekt, das sowohl das PDF-Eingabedokument als auch das XML-Lesezeichen speichert.
   * Fügen Sie das PDF-Eingabedokument hinzu, indem Sie die `java.util.Map` Methode des `put` Objekts aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document` Objekt, das das PDF-Eingabedokument enthält.
   * Fügen Sie das XML-Dokument für das Lesezeichen hinzu, indem Sie die `java.util.Map` Methode des `put` Objekts aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Lesezeichen-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document` Objekt, das das XML-Lesezeichen enthält.


1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `AssemblerOptionSpec` Methode des `setFailOnError` Objekts auf und übergeben Sie sie `false`.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeDDX` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document` Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map` Objekt, das sowohl das PDF-Eingabedokument als auch das XML-Lesezeichen enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` Objekt, das die Laufzeitoptionen angibt, einschließlich der standardmäßigen Schriftart- und Auftragsprotokollebene
   Die `invokeDDX` Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult` Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das PDF-Dokument mit Lesezeichen.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Rufen Sie die `AssemblerResult` Methode des `getDocuments` Objekts auf. Dadurch wird ein `java.util.Map` Objekt zurückgegeben.
   * Durchlaufen des `java.util.Map` Objekts, bis Sie das resultierende `com.adobe.idp.Document` Objekt gefunden haben. (Sie können das im DDX-Dokument angegebene PDF-Ergebniselement zum Abrufen des Dokuments verwenden.)
   * Rufen Sie die `com.adobe.idp.Document` Methode des `copyToFile` Objekts auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Zusammenstellen von PDF-Dokumenten mit Lesezeichen mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-documents-with-bookmarks-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenführen von PDF-Dokumenten mit Lesezeichen mithilfe der Web-Service-API {#assemble-pdf-documents-with-bookmarks-using-the-web-service-api}

Assembler eines PDF-Dokuments mit Lesezeichen mithilfe der Assembler Service API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient` Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` Objekt mithilfe des `System.ServiceModel.EndpointAddress` Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `AssemblerServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern der PDF-Eingabedatei verwendet.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf das XML-Lesezeichen.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des XML-Lesezeichendokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen einer Map-Sammlung hinzu.

   * Create a `MyMapOf_xsd_string_To_xsd_anyType` object. Dieses Collection-Objekt wird zum Speichern der PDF-Eingabedokumente und des XML-Lesezeichens verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument und für das XML-Lesezeichen ein `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekt.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Objektfeld einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt `key` . Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB` Objekt, in dem das PDF-Dokument gespeichert wird, dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Objektfeld `value` zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekt dem `MyMapOf_xsd_string_To_xsd_anyType` Objekt hinzu. Invoke the `MyMapOf_xsd_string_To_xsd_anyType` object&#39;s `Add` method and pass the `MyMapOf_xsd_string_To_xsd_anyType` object. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument und das XML-Lesezeichen aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem zum `AssemblerOptionSpec` Objekt gehörenden Datenmember einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie ihn `false` dem `AssemblerOptionSpec` Datenmember des `failOnError` Objekts zu.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeDDX` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType` Array, das die Eingabedokumente enthält
   * Ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen angibt
   Die `invokeDDX` Methode gibt ein `AssemblerResult` Objekt zurück, das die Ergebnisse des Auftrags sowie eventuell auftretende Ausnahmen enthält.

1. Speichern Sie das PDF-Dokument mit Lesezeichen.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Greifen Sie auf das `AssemblerResult` Feld des `documents` Objekts zu, das ein `Map` Objekt ist, das die PDF-Ergebnisdokumente enthält.
   * Durchlaufen Sie das `Map` Objekt, bis Sie den Schlüssel gefunden haben, der dem Namen des Zieldokuments entspricht. Dann wird das Array-Element `value` in eine `BLOB`umgewandelt.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf das `BLOB` Objektfeld `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
