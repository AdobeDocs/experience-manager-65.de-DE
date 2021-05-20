---
title: Assemblieren von PDF-Dokumenten mit Lesezeichen
seo-title: Assemblieren von PDF-Dokumenten mit Lesezeichen
description: Mit dem Assembler-Dienst können Sie ein PDF-Dokument ändern, das Lesezeichen enthält, um Lesezeichen mit der Java-API und der Web Service-API einzuschließen.
seo-description: Mit dem Assembler-Dienst können Sie ein PDF-Dokument ändern, das Lesezeichen enthält, um Lesezeichen mit der Java-API und der Web Service-API einzuschließen.
uuid: a306d2a6-0b12-4eb3-bff4-968a33417486
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f4711a8-033c-4051-ab41-65a26838899b
role: Developer
exl-id: 2b938410-f51b-420b-b5d4-2ed13ec29c5a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2588'
ht-degree: 2%

---

# Zusammenstellen von PDF-Dokumenten mit Lesezeichen {#assembling-pdf-documents-with-bookmarks}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Sie können ein PDF-Dokument zusammenstellen, das Lesezeichen enthält. Angenommen, Sie verfügen über ein PDF-Dokument, das keine Lesezeichen enthält, und möchten es durch Festlegen von Lesezeichen ändern. Mit dem Assembler-Dienst können Sie ein PDF-Dokument übergeben, das keine Lesezeichen enthält, und ein PDF-Dokument zurückerhalten, das Lesezeichen enthält.

Lesezeichen enthalten die folgenden Eigenschaften:

* Ein Titel, der als Text auf dem Bildschirm angezeigt wird.
* Eine Aktion, die angibt, was passiert, wenn ein Benutzer auf das Lesezeichen klickt. Die typische Aktion für ein Lesezeichen besteht darin, zu einem anderen Speicherort im aktuellen Dokument zu wechseln oder ein anderes PDF-Dokument zu öffnen, obwohl andere Aktionen angegeben werden können.

Angenommen, für diese Diskussion wird das folgende DDX-Dokument verwendet.

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

Beachten Sie in diesem DDX-Dokument, dass dem Quellattribut der Wert `Loan.pdf` zugewiesen ist. Dieses DDX-Dokument gibt an, dass ein einzelnes PDF-Dokument an den Assembler-Dienst übergeben wird. Beim Zusammenstellen eines PDF-Dokuments mit Lesezeichen müssen Sie ein XML-Lesezeichen-Dokument angeben, das die Lesezeichen im Ergebnisdokument beschreibt. Um ein XML-Dokument mit Lesezeichen anzugeben, stellen Sie sicher, dass das Element `Bookmarks` in Ihrem DDX-Dokument angegeben ist.

In diesem Beispiel-DDX-Dokument gibt das Element `Bookmarks` `doc2` als Wert an. Dieser Wert gibt an, dass die an den Assembler-Dienst übergebene Eingabezuordnung einen Schlüssel mit dem Namen `doc2` enthält. Der Wert des Schlüssels `doc2` ist ein `com.adobe.idp.Document` -Wert, der das XML-Lesezeichen darstellt. (Siehe &quot;Lesezeichensprache&quot;in der [Assembler-Dienst- und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).)

Dieses Thema verwendet die folgende XML-Lesezeichensprache, um ein PDF-Dokument mit Lesezeichen zusammenzustellen.

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

Beachten Sie in diesem XML-Lesezeichen-Dokument das Aktionselement , das die Aktion definiert, die ausgeführt wird, wenn ein Benutzer auf das Lesezeichen klickt. Unter dem Element Aktion befindet sich das Launch-Element, das Anwendungen wie NotePad startet und Dateien wie PDF-Dateien öffnet. Um eine PDF-Datei zu öffnen, müssen Sie das File-Element verwenden, das die zu öffnende Datei angibt. In der in diesem Abschnitt angegebenen XML-Datei für Lesezeichen lautet der Name der geöffneten Datei beispielsweise LoanDetails.pdf.

>[!NOTE]
>
>Ausführliche Informationen zu unterstützten Aktionen finden Sie unter &quot; `Action` element&quot;in der [Assembler-Dienst- und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

Bei dem in diesem Abschnitt angegebenen DDX-Dokument und der XML-Datei mit Lesezeichen als Eingabe stellt der Assembler-Dienst ein PDF-Dokument zusammen, das die folgenden Lesezeichen enthält.

![aw_aw_bmark](assets/aw_aw_bmark.png)

Wenn ein Benutzer auf das Lesezeichen *Öffnen Sie die Darlehensdetails* klickt, wird die Datei &quot;LoanDetails.pdf&quot;geöffnet. Wenn der Benutzer auf das Lesezeichen *Launch NotePad* klickt, wird NotizPad ebenfalls gestartet.

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden keine Konzepte besprochen, wie das Erstellen eines Kollektionsobjekts mit Eingabedokumenten oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Kollektionsobjekt. (Siehe [Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein PDF-Dokument mit Lesezeichen zusammenzuführen:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.
1. Referenzieren Sie das XML-Dokument für Lesezeichen.
1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen zu einer Map-Sammlung hinzu.
1. Legen Sie Laufzeitoptionen fest.
1. Assemblieren des PDF-Dokuments.
1. Speichern Sie das PDF-Dokument mit Lesezeichen.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss das Element `Bookmarks` enthalten, das den Assembler-Dienst anweist, eine PDF-Datei zusammenzustellen, die Lesezeichen enthält. (Ein Beispiel finden Sie im zuvor in diesem Abschnitt gezeigten DDX-Dokument.)

**Referenzieren eines PDF-Dokuments, dem Lesezeichen hinzugefügt werden**

Referenzieren Sie ein PDF-Dokument, dem Lesezeichen hinzugefügt werden. Es spielt keine Rolle, ob das referenzierte PDF-Dokument bereits Lesezeichen enthält. Wenn das Element `Bookmarks` ein untergeordnetes Element des PDF-Quellelements ist, ersetzen die Lesezeichen die bereits in der PDF-Quelle vorhandenen Elemente. Wenn Sie jedoch die vorhandenen Lesezeichen beibehalten möchten, stellen Sie sicher, dass `Bookmarks` gleichrangig mit dem PDF-Quellelement ist. Betrachten Sie beispielsweise das folgende Beispiel:

```xml
 <PDF result="foo">
      <PDF source="inDoc"/>
      <Bookmarks source="doc2"/>
 </PDF>
```

**Referenzieren des XML-Lesezeichen-Dokuments**

Um eine PDF-Datei zusammenzustellen, die neue Lesezeichen enthält, müssen Sie auf ein XML-Lesezeichen verweisen. Das XML-Lesezeichen-Dokument wird an den Assembler-Dienst innerhalb des Map-Sammlungsobjekts übergeben. (Ein Beispiel finden Sie im zuvor in diesem Abschnitt gezeigten XML-Dokument für Lesezeichen .)

>[!NOTE]
>
>Siehe &quot;Lesezeichensprache&quot;in der [Assembler-Dienst- und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

**Hinzufügen des PDF-Dokuments und des XML-Lesezeichens zu einer Map-Sammlung**

Sie müssen sowohl das PDF-Dokument, dem Lesezeichen hinzugefügt werden, als auch das XML-Lesezeichen zur Map-Sammlung hinzufügen. Daher enthält das Collection-Objekt Zuordnung zwei Elemente: ein PDF-Dokument und das XML-Lesezeichen-Dokument.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Zusammenführen des PDF-Dokuments**

Verwenden Sie zum Zusammenführen eines PDF-Dokuments, das neue Lesezeichen enthält, den Vorgang `invokeDDX` des Assembler-Dienstes. Der Grund, warum Sie den Vorgang `invokeDDX` im Gegensatz zu anderen Assembler-Dienstvorgängen wie `invokeOneDocument` verwenden müssen, ist, dass der Assembler-Dienst ein XML-Lesezeichen-Dokument erfordert, das innerhalb des Map-Sammlungsobjekts übergeben wird. Dieses Objekt ist ein Parameter des Vorgangs `invokeDDX` .

**Speichern Sie das PDF-Dokument mit Lesezeichen**

Sie müssen die Ergebnisse aus dem zurückgegebenen map -Objekt extrahieren und das entsprechende PDF-Dokument speichern. (Siehe &quot;Ergebnisse extrahieren&quot;in [Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenführen von PDF-Dokumenten mit Lesezeichen mithilfe der Java-API {#assemble-pdf-documents-with-bookmarks-using-the-java-api}

Assemblieren eines PDF-Dokuments mit Lesezeichen mithilfe der Assembler-Dienst-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `AssemblerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, indem Sie dessen Konstruktor verwenden und den Speicherort des PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt mithilfe des zugehörigen Konstruktors und übergeben Sie das `java.io.FileInputStream` -Objekt, das das PDF-Dokument enthält.

1. Referenzieren Sie das XML-Dokument für Lesezeichen.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort der XML-Datei übergeben, die das Lesezeichen-XML-Dokument darstellt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.

1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen zu einer Map-Sammlung hinzu.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern sowohl des PDF-Eingabedokuments als auch des XML-Lesezeichens verwendet wird.
   * Fügen Sie das PDF-Eingabedokument hinzu, indem Sie die `put` -Methode des Objekts `java.util.Map` aufrufen und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document` -Objekt, das das PDF-Eingabedokument enthält.
   * Fügen Sie das XML-Lesezeichen-Dokument hinzu, indem Sie die `put` -Methode des Objekts `java.util.Map` aufrufen und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements Lesezeichen übereinstimmen.
      * Ein `com.adobe.idp.Document` -Objekt, das das XML-Lesezeichen-Dokument enthält.


1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `setFailOnError` -Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Assemblieren des PDF-Dokuments.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das zu verwendende DX-Dokument darstellt
   * Ein `java.util.Map` -Objekt, das sowohl das PDF-Eingabedokument als auch das XML-Lesezeichen enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich standardmäßiger Schrift- und Auftragsprotokollebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das PDF-Dokument mit Lesezeichen.

   Um das neu erstellte PDF-Dokument abzurufen, führen Sie die folgenden Schritte aus:

   * Rufen Sie die `getDocuments` -Methode des Objekts `AssemblerResult` auf. Dadurch wird ein `java.util.Map` -Objekt zurückgegeben.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden. (Sie können das im DDX-Dokument angegebene PDF-Ergebniselement verwenden, um das Dokument abzurufen.)
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): Assemblieren von PDF-Dokumenten mit Lesezeichen mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-documents-with-bookmarks-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenführen von PDF-Dokumenten mit Lesezeichen mithilfe der Webdienst-API {#assemble-pdf-documents-with-bookmarks-using-the-web-service-api}

Assemblieren eines PDF-Dokuments mit Lesezeichen mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

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
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie ein PDF-Dokument, dem Lesezeichen hinzugefügt werden.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern der PDF-Eingabedatei verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie das XML-Dokument für Lesezeichen.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des XML-Lesezeichen-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen zu einer Map-Sammlung hinzu.

   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Collection-Objekt wird zum Speichern der PDF-Eingabedokumente und des XML-Lesezeichens verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument und das XML-Lesezeichen-Dokument ein `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Weisen Sie dem `key` -Feld des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, das das PDF-Dokument speichert, dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objektfeld `value` zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt zum `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die `Add` -Methode des Objekts `MyMapOf_xsd_string_To_xsd_anyType` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument und das XML-Lesezeichen-Dokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec` -Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem `AssemblerOptionSpec`-Datenelement des `failOnError`-Objekts zu.

1. Assemblieren des PDF-Dokuments.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Array, das die Eingabedokumente enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und eventuell aufgetretene Ausnahmen enthält.

1. Speichern Sie das PDF-Dokument mit Lesezeichen.

   Um das neu erstellte PDF-Dokument abzurufen, führen Sie die folgenden Schritte aus:

   * Greifen Sie auf das `AssemblerResult`-Feld des Objekts `documents` zu, bei dem es sich um ein `Map`-Objekt handelt, das die PDF-Dokumente mit den Ergebnissen enthält.
   * Iterieren Sie durch das `Map`-Objekt, bis Sie den Schlüssel finden, der dem Namen des Zieldokuments entspricht. Dann das `value` des Array-Mitglieds in ein `BLOB`-Element umwandeln.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf das `BLOB` -Objektfeld `MTOM` zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
