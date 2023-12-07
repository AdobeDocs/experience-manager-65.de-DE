---
title: Zusammenstellen von PDF-Dokumenten mit Lesezeichen
description: Mit dem Assembler-Service können Sie ein PDF-Dokument ändern, das Lesezeichen enthält, um Lesezeichen mithilfe der Java-API und der Webservice-API einzuschließen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 2b938410-f51b-420b-b5d4-2ed13ec29c5a
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '2519'
ht-degree: 85%

---

# Zusammenstellen von PDF-Dokumenten mit Lesezeichen {#assembling-pdf-documents-with-bookmarks}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Sie können ein PDF-Dokument zusammenstellen, das Lesezeichen enthält. Angenommen, Sie verfügen über ein PDF-Dokument, das keine Lesezeichen enthält, und Sie möchten es ändern, indem Sie Lesezeichen hinzufügen. Mithilfe des Assembler-Services können Sie ein PDF-Dokument übergeben, das keine Lesezeichen enthält, und ein PDF-Dokument mit Lesezeichen zurückerhalten.

Lesezeichen enthalten die folgenden Eigenschaften:

* Ein Titel, der als Text auf dem Bildschirm angezeigt wird.
* Eine Aktion, die angibt, was passiert, wenn ein Benutzer auf das Lesezeichen klickt. Die typische Aktion für ein Lesezeichen besteht darin, zu einem anderen Speicherort im aktuellen PDF-Dokument zu wechseln oder ein anderes Dokument zu öffnen, obwohl auch andere Aktionen angegeben werden können.

Nehmen Sie für dieses Thema bitte an, dass das folgende DDX-Dokument verwendet wird.

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

Beachten Sie, dass in diesem DDX-Dokument dem Quellattribut der Wert `Loan.pdf` zugewiesen ist. Dieses DDX-Dokument gibt an, dass ein einzelnes PDF-Dokument an den Assembler-Service übergeben wird. Beim Zusammenstellen eines PDF-Dokuments mit Lesezeichen müssen Sie ein XML-Lesezeichen-Dokument angeben, das die Lesezeichen im Ergebnisdokument beschreibt. Um ein XML-Dokument mit Lesezeichen anzugeben, stellen Sie sicher, dass in Ihrem DDX-Dokument das Element `Bookmarks` angegeben ist.

In diesem DDX-Beispieldokument gibt das Element `Bookmarks` den Wert `doc2` an. Dieser Wert gibt an, dass die an den Assembler-Service übergebene Eingabezuordnung einen Schlüssel namens `doc2` enthält. Der Wert des Schlüssels `doc2` ist ein `com.adobe.idp.Document`-Wert, der das XML-Lesezeichen-Dokument darstellt. (Siehe „Lesezeichensprache“ in der [Referenz zu Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).)

Hier wird die folgende XML-Lesezeichensprache verwendet, um ein PDF-Dokument mit Lesezeichen zusammenzustellen.

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

Beachten Sie in diesem XML-Lesezeichen-Dokument das Aktionselement, das die Aktion definiert, die ausgeführt wird, wenn ein Benutzer auf das Lesezeichen klickt. Unter dem Aktionselement befindet sich das Start-Element, das Programme wie NotePad startet und Dateien wie PDF-Dateien öffnet. Um eine PDF-Datei zu öffnen, müssen Sie das Dateielement verwenden, das die zu öffnende Datei angibt. In der in diesem Abschnitt angegebenen XML-Lesezeichen-Datei lautet der Name der geöffneten Datei beispielsweise „LoanDetails.pdf“.

>[!NOTE]
>
>Umfassende Informationen zu unterstützten Aktionen finden Sie unter „`Action`-Element“ in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

Wenn das in diesem Abschnitt angegebene DDX-Dokument und die XML-Lesezeichen-Datei als Eingabe angegeben werden, stellt der Assembler-Service ein PDF-Dokument zusammen, das die folgenden Lesezeichen enthält.

![aw_aw_bmark](assets/aw_aw_bmark.png)

Wenn ein Benutzer auf das Lesezeichen *Öffnen der Darlehensdetails* klickt, wird die Datei „LoanDetails.pdf“ geöffnet. Wenn der Benutzer auf das Lesezeichen *NotePad starten* klickt, wird entsprechend das NotePad gestartet.

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie mit dem Zusammenstellen von PDF-Dokumenten mithilfe des Assembler-Dienstes vertraut sein. In diesem Abschnitt werden keine Konzepte besprochen, wie das Erstellen eines Sammlungsgegenstands mit Eingabedokumenten oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Sammlungsgegenstand. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument zusammenzustellen, das Lesezeichen enthält, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein PDF-Dokument, zu dem Lesezeichen hinzugefügt werden.
1. Referenzieren Sie das XML-Lesezeichen-Dokument.
1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen-Dokument zu einer Zuordnungssammlung hinzu.
1. Legen Sie Laufzeitoptionen fest.
1. Stellen Sie das PDF-Dokument zusammen.
1. Speichern Sie das PDF-Dokument, das Lesezeichen enthält.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungs-Server bereitgestellt ist, der von JBoss verschieden ist, müssen Sie die Dateien „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die für den J2EE-Anwendungs-Server spezifisch sind, auf dem AEM Forms bereitgestellt ist. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines PDF-Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Referenzieren eines bestehenden DDX-Dokuments**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss das `Bookmarks`-Element enthalten, das den Assembler-Service anweist, eine PDF mit Lesezeichen zusammenzustellen. (Ein Beispiel finden Sie im zuvor in diesem Abschnitt gezeigten DDX-Dokument.)

**Referenzieren eines PDF-Dokuments, zu dem Lesezeichen hinzugefügt werden**

Referenzieren Sie ein PDF-Dokument, zu dem Lesezeichen hinzugefügt werden. Es spielt keine Rolle, ob das referenzierte PDF-Dokument bereits Lesezeichen enthält. Wenn das Element `Bookmarks` ein untergeordnetes Element des PDF-Quellelements ist, ersetzen die Lesezeichen die bereits in der PDF-Quelle vorhandenen. Wenn Sie jedoch die schon vorhandenen Lesezeichen beibehalten möchten, stellen Sie sicher, dass `Bookmarks` ein gleichrangiges Element des PDF-Quellelements ist. Betrachten Sie etwa das folgende Beispiel:

```xml
 <PDF result="foo">
      <PDF source="inDoc"/>
      <Bookmarks source="doc2"/>
 </PDF>
```

**Referenzieren des XML-Lesezeichen-Dokuments**

Um eine PDF mit neuen Lesezeichen zusammenzustellen, müssen Sie auf ein XML-Lesezeichen-Dokument verweisen. Das XML-Lesezeichen-Dokument wird innerhalb des Zuordnungssammlungsobjekts an den Assembler-Service übergeben. (Ein Beispiel finden Sie im zuvor in diesem Abschnitt gezeigten XML-Lesezeichen-Dokument.)

>[!NOTE]
>
>Siehe „Lesezeichensprache“ in der [Referenz zu Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

**Hinzufügen des PDF-Dokuments und des XML-Lesezeichen-Dokuments zu einer Zuordnungssammlung**

Fügen Sie sowohl das PDF-Dokument, dem Lesezeichen hinzugefügt werden, als auch das Lesezeichen-XML-Dokument zur Map-Sammlung hinzu. Daher enthält das Zuordnungssammlungsobjekt zwei Elemente: ein PDF-Dokument und das XML-Lesezeichen-Dokument.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Service angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Zusammenführen des PDF-Dokuments**

Verwenden Sie zum Zusammenführen eines PDF-Dokuments, das neue Lesezeichen enthält, die Funktion des Assembler-Dienstes `invokeDDX` Vorgang. Der Grund, warum Sie die Operation `invokeDDX` im Gegensatz zu anderen Operationen des Assembler-Services, wie z. B. `invokeOneDocument`, verwenden müssen, ist, dass der Assembler-Service ein XML-Lesezeichen-Dokument benötigt, das innerhalb des Zuordnungssammlungsobjekts übergeben wird. Dieses Objekt ist ein Parameter des Vorgangs `invokeDDX`.

**Speichern des PDF-Dokuments, das Lesezeichen enthält**

Extrahieren Sie die Ergebnisse aus dem zurückgegebenen map -Objekt und speichern Sie das entsprechende PDF-Dokument. (Siehe „Extrahieren der Ergebnisse“ in [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatisches Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenstellen von PDF-Dokumenten mit Lesezeichen mithilfe der Java-API {#assemble-pdf-documents-with-bookmarks-using-the-java-api}

So stellen Sie ein PDF-Dokument mit Lesezeichen mithilfe der Assembler-Service-API (Java) zusammen:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Dokument, zu dem Lesezeichen hinzugefügt werden.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie dessen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben, das das PDF-Dokument enthält.

1. Referenzieren Sie das XML-Lesezeichen-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort der XML-Datei übergeben, die das XML-Lesezeichen-Dokument darstellt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.

1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen-Dokument zu einer Zuordnungssammlung hinzu.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern sowohl des PDF-Eingabedokuments als auch des XML-Lesezeichen-Dokuments verwendet wird.
   * Fügen Sie das PDF-Eingabedokument hinzu, indem Sie die `java.util.Map` -Objekt `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Eine Zeichenfolge, die den Speichernamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Eingabedokument enthält.

   * Fügen Sie das XML-Lesezeichen-Dokument hinzu, indem Sie die `java.util.Map` -Objekt `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Eine Zeichenfolge, die den Speichernamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements für Lesezeichen übereinstimmen.
      * Ein `com.adobe.idp.Document`-Objekt, das das XML-Lesezeichen-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das sowohl das PDF-Eingabedokument als auch das XML-Lesezeichen-Dokument enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich standardmäßiger Schrift- und Auftragsprotokollebene

   Die Methode `invokeDDX` gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und eventuell aufgetretene Ausnahmen enthält.

1. Speichern Sie das PDF-Dokument, das Lesezeichen enthält.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Dadurch wird ein `java.util.Map`-Objekt zurückgegeben.
   * Durchsuchen Sie das `java.util.Map`-Objekt, bis Sie das entstandene `com.adobe.idp.Document`-Objekt gefunden haben. (Sie können das im DDX-Dokument angegebene PDF-Ergebniselement verwenden, um das Dokument abzurufen.)
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Zusammenstellen von PDF-Dokumenten mit Lesezeichen mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-documents-with-bookmarks-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Erstellen von PDF-Dokumenten mit Lesezeichen mithilfe der Web-Service-API {#assemble-pdf-documents-with-bookmarks-using-the-web-service-api}

Erstellen Sie ein PDF-Dokument mit Lesezeichen mithilfe der Assembler-Service-API (Web-Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert mit der WSDL an den AEM Forms-Service (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekr, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus enthält, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekt gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld die Inhalte des Byte-Arrays zuweisen.

1. Referenzieren Sie ein PDF-Dokument, zu dem Lesezeichen hinzugefügt werden.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des Eingabe-PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Eingabe-PDF-Dokuments und den Modus enthält, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld die Inhalte des Byte-Arrays zuweisen.

1. Referenzieren Sie das XML-Lesezeichen-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des XML-Dokuments mit Lesezeichen verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Eingabe-PDF-Dokuments und den Modus enthält, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld die Inhalte des Byte-Arrays zuweisen.

1. Fügen Sie das PDF-Dokument und das XML-Lesezeichen-Dokument zu einer Zuordnungssammlung hinzu.

   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Sammlungsobjekt wird zum Speichern der Eingabe-PDF-Dokumente und des XML-Dokuments mit Lesezeichen verwendet.
   * Erstellen Sie für jedes Eingabe-PDF-Dokument und das XML-Dokument mit Lesezeichen ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie dem `key`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts einen Zeichenfolgenwert zu, der den Namen des Schlüssels enthält. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Weisen Sie das `BLOB`-Objekt, in dem das PDF-Dokument gespeichert wird, dem `value`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu.
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die Methode `Add` des `MyMapOf_xsd_string_To_xsd_anyType`-Objekts auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument und das XML-Lesezeichen-Dokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` Datenelement.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Array, das die Eingabedokumente enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die Methode `invokeDDX` gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Vorgangs und alle eventuell aufgetretenen Ausnahmen enthält.

1. Speichern Sie das PDF-Dokument, das Lesezeichen enthält.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die PDF-Ergebnisdokumente enthält.
   * Iterieren Sie durch das `Map`-Objekt, bis Sie den Schlüssel finden, der dem Namen des Ergebnisdokuments entspricht. Dann das Array-Element `value` zu `BLOB`.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf dessen `BLOB` -Objekt `MTOM` -Feld. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
