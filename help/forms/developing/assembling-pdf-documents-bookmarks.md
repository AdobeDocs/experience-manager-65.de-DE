---
title: Zusammenstellen von PDF-Dokumenten mit Lesezeichen
seo-title: Zusammenstellen von PDF-Dokumenten mit Lesezeichen
description: Verwenden Sie den Assembler-Dienst, um ein PDF-Dokument, das Lesezeichen enthält, mithilfe der Java-API und der Web-Service-API zu ändern.
seo-description: Verwenden Sie den Assembler-Dienst, um ein PDF-Dokument, das Lesezeichen enthält, mithilfe der Java-API und der Web-Service-API zu ändern.
uuid: a306d2a6-0b12-4eb3-bff4-968a33417486
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f4711a8-033c-4051-ab41-65a26838899b
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '2588'
ht-degree: 2%

---


# Zusammenstellen von PDF-Dokumenten mit Lesezeichen {#assembling-pdf-documents-with-bookmarks}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Sie können ein PDF-Dokument zusammenstellen, das Lesezeichen enthält. Angenommen, Sie haben ein PDF-Dokument, das keine Lesezeichen enthält, und Sie möchten es mithilfe von Lesezeichen ändern. Mit dem Assembler-Dienst können Sie ein PDF-Dokument ohne Lesezeichen übergeben und ein PDF-Dokument mit Lesezeichen zurückerhalten.

Lesezeichen enthalten die folgenden Eigenschaften:

* Ein Titel, der als Text auf dem Bildschirm angezeigt wird.
* Eine Aktion, die angibt, was passiert, wenn ein Benutzer auf das Lesezeichen klickt. Normalerweise wird ein Lesezeichen an eine andere Stelle im aktuellen Dokument verschoben oder ein anderes PDF-Dokument geöffnet, es können jedoch auch andere Aktionen angegeben werden.

Für diese Diskussion nehmen Sie an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
       <PDF result="FinalDoc.pdf">
          <PDF source="Loan.pdf">
             <Bookmarks source="doc2" />
          </PDF>
       </PDF>
 </DDX>
```

Beachten Sie, dass dem Quellattribut in diesem DDX-Dokument der Wert `Loan.pdf` zugewiesen ist. Dieses DDX-Dokument gibt an, dass ein einzelnes PDF-Dokument an den Assembler-Dienst übergeben wird. Beim Zusammenstellen eines PDF-Dokuments mit Lesezeichen müssen Sie ein XML-Dokument für Lesezeichen angeben, das die Lesezeichen im Ergebnisdokument beschreibt. Um ein XML-Dokument für Lesezeichen anzugeben, stellen Sie sicher, dass das `Bookmarks`-Element im DDX-Dokument angegeben ist.

In diesem DDX-Dokument gibt das `Bookmarks`-Element `doc2` als Wert an. Dieser Wert gibt an, dass die an den Assembler-Dienst übergebene Eingabemap einen Schlüssel mit dem Namen `doc2` enthält. Der Wert des Schlüssels `doc2` ist ein `com.adobe.idp.Document`-Wert, der das XML-Lesezeichen darstellt. (Siehe &quot;Lesezeichensprache&quot;im [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).)

In diesem Thema wird die folgende Sprache für XML-Lesezeichen verwendet, um ein PDF-Dokument mit Lesezeichen zusammenzustellen.

```xml
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

Beachten Sie in diesem XML-Dokument für Lesezeichen das Aktionselement, das die Aktion definiert, die ausgeführt wird, wenn ein Benutzer auf das Lesezeichen klickt. Unter dem Element Aktion befindet sich das Element Launch, mit dem Anwendungen wie NotePad gestartet und Dateien wie PDF-Dateien geöffnet werden. Um eine PDF-Datei zu öffnen, müssen Sie das Dateielement verwenden, das die zu öffnende Datei angibt. In der in diesem Abschnitt angegebenen XML-Datei für Lesezeichen lautet der Name der geöffneten Datei beispielsweise LoanDetails.pdf.

>[!NOTE]
>
>Ausführliche Informationen zu unterstützten Aktionen finden Sie unter &quot; `Action` element&quot;im [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

Wenn das in diesem Abschnitt angegebene DDX-Dokument und die XML-Lesezeichendatei als Eingabe angegeben sind, assembliert der Assembler-Dienst ein PDF-Dokument, das die folgenden Lesezeichen enthält.

![aw_aw_bmark](assets/aw_aw_bmark.png)

Wenn ein Benutzer auf das Lesezeichen *Kreditinfo öffnen* klickt, wird die Datei &quot;LoanDetails.pdf&quot;geöffnet. Wenn der Benutzer auf das Lesezeichen *NotePad starten* klickt, wird NotizPad gestartet.

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden keine Konzepte beschrieben, wie z. B. das Erstellen eines Collection-Objekts, das Eingabedokumente enthält, oder das Extrahieren der Dokumente aus dem zurückgegebenen Collection-Objekt. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So assemblieren Sie ein PDF-Dokument mit Lesezeichen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.
1. Verweisen Sie auf das XML-Dokument des Lesezeichens.
1. hinzufügen das PDF-Dokument und das XML-Lesezeichen einer Map-Sammlung.
1. Legen Sie Laufzeitoptionen fest.
1. Stellen Sie das PDF-Dokument zusammen.
1. Speichern Sie das PDF-Dokument mit Lesezeichen.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss das Element `Bookmarks` enthalten, das den Assembler-Dienst anweist, eine PDF-Datei zusammenzustellen, die Lesezeichen enthält. (Ein Beispiel finden Sie im Dokument DDX, das weiter oben in diesem Abschnitt gezeigt wird.)

**Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden**

Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden. Es spielt keine Rolle, ob das referenzierte PDF-Dokument bereits Lesezeichen enthält. Wenn das `Bookmarks`-Element ein untergeordnetes Element des PDF-Quellelements ist, ersetzen die Lesezeichen die bereits in der PDF-Quelle vorhandenen Elemente. Wenn Sie jedoch die vorhandenen Lesezeichen beibehalten möchten, stellen Sie sicher, dass `Bookmarks` ein Geschwisterelement des PDF-Quellelements ist. Beispiel:

```xml
 <PDF result="foo">
      <PDF source="inDoc"/>
      <Bookmarks source="doc2"/>
 </PDF>
```

**Referenzieren des XML-Dokuments für Lesezeichen**

Um eine PDF-Datei mit neuen Lesezeichen zusammenzustellen, müssen Sie auf ein XML-Dokument für Lesezeichen verweisen. Das XML-Dokument für das Lesezeichen wird innerhalb des Zuordnungsobjekts an den Assembler-Dienst übergeben. (Ein Beispiel finden Sie im XML-Dokument zu Lesezeichen, das weiter oben in diesem Abschnitt gezeigt wird.)

>[!NOTE]
>
>Siehe &quot;Lesezeichensprache&quot;im [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

**hinzufügen des PDF-Dokuments und des XML-Lesezeichen-Dokuments zu einer Map-Sammlung**

Sie müssen sowohl das PDF-Dokument, dem Lesezeichen hinzugefügt werden, als auch das XML-Lesezeichen zur Map-Sammlung hinzufügen. Daher enthält das Map-Sammlungsobjekt zwei Elemente: ein PDF-Dokument und das XML-Dokument für das Lesezeichen.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren. Informationen zu den verfügbaren Laufzeitoptionen finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Zusammenstellen des PDF-Dokuments**

Verwenden Sie zum Zusammenführen eines PDF-Dokuments mit neuen Lesezeichen den Vorgang `invokeDDX` des Assembler-Dienstes. Der Grund, warum Sie den Vorgang `invokeDDX` im Gegensatz zu anderen Assembler-Dienstvorgängen wie `invokeOneDocument` verwenden müssen, ist, dass der Assembler-Dienst ein XML-Lesezeichen-Dokument erfordert, das im Map-Sammlungsobjekt übergeben wird. Dieses Objekt ist ein Parameter des Vorgangs `invokeDDX`.

**PDF-Dokument mit Lesezeichen speichern**

Sie müssen die Ergebnisse aus dem zurückgegebenen Map-Objekt extrahieren und das entsprechende PDF-Dokument speichern. (Siehe &quot;Ergebnisse extrahieren&quot;in [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenstellen von PDF-Dokumenten mit Lesezeichen mithilfe der Java-API {#assemble-pdf-documents-with-bookmarks-using-the-java-api}

Assemblieren eines PDF-Dokuments mit Lesezeichen mithilfe der Assembler Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie den Konstruktor verwenden und den Speicherort des PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt mit dem Konstruktor und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.

1. Verweisen Sie auf das XML-Dokument des Lesezeichens.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie den Konstruktor verwenden und den Speicherort der XML-Datei übergeben, die das Lesezeichen-XML-Dokument darstellt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.

1. hinzufügen das PDF-Dokument und das XML-Lesezeichen einer Map-Sammlung.

   * Erstellen Sie ein `java.util.Map`-Objekt, mit dem sowohl das PDF-Eingabedokument als auch das XML-Dokument für Lesezeichen gespeichert werden.
   * hinzufügen Sie das PDF-Dokument zur Eingabe, indem Sie die `java.util.Map`-Objektmethode `put` aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument für die Eingabe enthält.
   * hinzufügen Sie das XML-Dokument für das Lesezeichen, indem Sie die `java.util.Map`-Objektmethode `put` aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Lesezeichenquellenelements übereinstimmen.
      * Ein `com.adobe.idp.Document`-Objekt, das das XML-Dokument für das Lesezeichen enthält.


1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `setFailOnError`-Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden erforderlichen Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das sowohl das PDF-Eingabedokument als auch das XML-Dokument des Lesezeichens enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen einschließlich der standardmäßigen Schriftart- und Auftragsprotokollebene angibt

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das PDF-Dokument mit Lesezeichen.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Rufen Sie die `AssemblerResult`-Methode des Objekts `getDocuments` auf. Gibt ein `java.util.Map`-Objekt zurück.
   * Durchlaufen Sie das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden. (Sie können das im DDX-Dokument angegebene PDF-Ergebniselement verwenden, um das Dokument abzurufen.)
   * Rufen Sie die `com.adobe.idp.Document`-Objektmethode `copyToFile` auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Zusammenstellen von PDF-Dokumenten mit Lesezeichen mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-documents-with-bookmarks-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenstellen von PDF-Dokumenten mit Lesezeichen mithilfe der Webdienst-API {#assemble-pdf-documents-with-bookmarks-using-the-web-service-api}

Assemblieren eines PDF-Dokuments mit Lesezeichen mithilfe der Assembler-Dienst-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

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
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern der Eingabe-PDF verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedatums und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf das XML-Dokument des Lesezeichens.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des XML-Dokuments für Lesezeichen verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedatums und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. hinzufügen das PDF-Dokument und das XML-Lesezeichen einer Map-Sammlung.

   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Collection-Objekt wird zum Speichern der PDF-Eingabedokumente und des XML-Dokuments für Lesezeichen verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument und für das XML-Dokument des Lesezeichens ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie dem Feld `MyMapOf_xsd_string_To_xsd_anyType_Item` des Objekts einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. `key` Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, in dem das PDF-Dokument gespeichert wird, dem `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objektfeld `value` zu.
   * hinzufügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt mit dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType`-Methode des Objekts `Add` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument und das XML-Dokument für das Lesezeichen aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenmember, der zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie `false` dem `AssemblerOptionSpec`-Datenmember des Objekts `failOnError` zu.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Array mit den Eingabe-Dokumenten
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und eventuell auftretende Ausnahmen enthält.

1. Speichern Sie das PDF-Dokument mit Lesezeichen.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Greifen Sie auf das Feld `AssemblerResult` des Objekts zu, bei dem es sich um ein `Map`-Objekt handelt, das die PDF-Dokumente des Ergebnisses enthält.`documents`
   * Durchlaufen Sie das `Map`-Objekt, bis Sie den Schlüssel finden, der dem Namen des resultierenden Dokuments entspricht. Dann wird `value` des Array-Mitglieds in ein `BLOB` umgewandelt.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf das `BLOB`-Objektfeld `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
