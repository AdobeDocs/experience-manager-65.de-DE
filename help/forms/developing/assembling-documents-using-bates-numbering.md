---
title: Zusammenstellen von Dokumenten mit Bates-Nummerierung
seo-title: Zusammenstellen von Dokumenten mit Bates-Nummerierung
description: 'Verwenden Sie die Bates-Nummerierung, um PDF-Dokumente mit der Java- und Web Service API zusammenzustellen. '
seo-description: 'Verwenden Sie die Bates-Nummerierung, um PDF-Dokumente mit der Java- und Web Service API zusammenzustellen. '
uuid: 28d5faeb-6915-41a2-b6a0-78d255df024f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 77e9b895-1313-4a5b-a2d5-cdb65bdc1966
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1942'
ht-degree: 5%

---


# Zusammenstellen von Dokumenten mit Bates-Nummerierung {#assembling-documents-using-bates-numbering}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Mithilfe der Bates-Nummerierung können Sie PDF-Dokumente mit eindeutigen Seitenkennungen zusammenstellen. *Die Bates-* Nummerierung ist eine Methode, um eindeutige Identifikatoren auf einen Stapel verwandter Dokumente anzuwenden. Jeder Seite im Dokument (oder einer Reihe von Dokumenten) wird eine Bates-Nummer zugewiesen, die die Seite eindeutig identifiziert. Beispielsweise Produktionsdokumente, die Materialaufstellungsinformationen enthalten und der Herstellung einer Baugruppe zugeordnet sind, können einen Bezeichner enthalten. Eine Bates-Nummer enthält einen sequenziell erhöhten numerischen Wert sowie ein optionales Präfix und Suffix. Das Suffix &quot;Präfix + numerisch +&quot;wird als *Bates-Muster* bezeichnet.

Die folgende Illustration zeigt ein PDF-Dokument, das einen eindeutigen Bezeichner enthält, der sich in der Kopfzeile des Dokuments befindet.

![au_au_batesnumber](assets/au_au_batesnumber.png)

Im Rahmen dieser Diskussion wird die eindeutige Seitenkennung in der Kopfzeile eines Dokuments platziert. Angenommen, das folgende DDX-Dokument wird verwendet.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
        <PDF result="out.pdf">
        <Header>
         <Center>
             <StyledText>
                 <p font-size="20pt"><BatesNumber/></p>
             </StyledText>
         </Center>
     </Header>
           <PDF source="map.pdf" />
          <PDF source="directions.pdf" />
          </PDF>
 </DDX>
```

Dieses DDX-Dokument führt zwei PDF-Dokumente mit den Namen *map.pdf* und *directions.pdf* in einem PDF-Dokument zusammen. Das resultierende PDF-Dokument enthält eine Kopfzeile, die aus einer eindeutigen Seitenkennung besteht. Das Dokument in der obigen Abbildung zeigt beispielsweise 000016.

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden die Konzepte nicht erläutert, z. B. das Erstellen eines Sammlungsobjekts, das Eingabeergebnisse enthält, oder das Extrahieren der Dokumente aus dem zurückgegebenen Sammlungsobjekt. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So assemblieren Sie ein PDF-Dokument mit einer eindeutigen Seitenkennung (Bates-Nummerierung):

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Referenzieren von PDF-Dokumenten zur Eingabe.
1. Legen Sie den Wert für die Anfangszahl der Bates fest.
1. Stellen Sie die PDF-Eingabedateien zusammen.
1. Extrahieren Sie die Ergebnisse.

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

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Um ein PDF-Dokument mit eindeutigen Seitenkennungen zusammenzustellen, muss das DDX-Dokument das Element `BatesNumber` enthalten.

**PDF-Dokumente zur Referenzeingabe**

PDF-Eingabedokumente müssen referenziert werden, um ein PDF-Dokument zusammenzustellen. Beispielsweise müssen auf die Dokumente &quot;map.pdf&quot;und &quot;richtungen.pdf&quot;verwiesen werden, um diese PDF-Dokumente in einem einzigen PDF-Dokument zusammenzuführen.

**Wert für die Anfangszahl der Bates festlegen**

Sie können den Wert für die Bates-Anfangszahl so einstellen, dass er Ihren Geschäftsanforderungen entspricht. Angenommen, es ist eine Anforderung, den Ausgangswert auf 000100 festzulegen. Wenn Sie den Ausgangswert nicht festlegen, ist der Wert der ersten Seite 000000.

**PDF-Eingabedateien zusammenstellen**

Nachdem Sie den Assembler-Dienstclient erstellt haben, verweisen Sie auf das DDX-Dokument, das die Elementinformationen `BatesNumber` enthält, verweisen auf ein PDF-Eingabedokument und legen Laufzeitoptionen fest. Sie können den Vorgang `invokeDDX` aufrufen, der dazu führt, dass der Assembler-Dienst ein PDF-Dokument zusammenstellt, das eindeutige Seitenkennungen enthält.

**Ergebnisse extrahieren**

Der Assembler-Dienst gibt ein Collection-Objekt zurück, das die Auftragsergebnisse enthält. Sie können das resultierende PDF-Dokument und alle ausgelösten Ausnahmen extrahieren. In diesem Fall befindet sich ein verschlüsseltes PDF-Dokument im Collection-Objekt.

>[!NOTE]
>
>Ein Collection-Objekt wird zurückgegeben, wenn Sie den Vorgang `invokeDDX` aufrufen. Dieser Vorgang wird verwendet, wenn zwei oder mehr PDF-Eingabedateien an den Assembler-Dienst übergeben werden. Wenn Sie jedoch nur ein PDF-Eingabedokument an den Assembler-Dienst übergeben, sollten Sie den Vorgang `invokeOneDocument` aufrufen. Informationen zur Verwendung dieses Vorgangs finden Sie unter [Zusammenstellen verschlüsselter PDF-Dokumente](/help/forms/developing/assembling-encrypted-pdf-documents.md).

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenstellen von Dokumenten mit Bates-Nummerierung mithilfe der Java-API {#assemble-documents-with-bates-numbering-using-the-java-api}

Stellen Sie mithilfe der Assembler Service API (Java) ein PDF-Dokument zusammen, das eindeutige Seitenkennungen (Bates-Nummerierung) verwendet:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren von PDF-Dokumenten zur Eingabe.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von PDF-Eingabedokumenten mit einem `HashMap`-Konstruktor verwendet wird.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `java.io.FileInputStream`-Dokument, indem Sie den Konstruktor verwenden und die Position des PDF-Eingabedokuments übergeben. Übergeben Sie in diesem Fall den Speicherort eines ungesicherten PDF-Dokuments.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.
   * hinzufügen Sie einen Eintrag für das `java.util.Map`-Objekt, indem Sie die `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. Beispielsweise lautet der Name der PDF-Quelldatei, der im DDX-Dokument, das in diesem Abschnitt eingeführt wird, angegeben wird, Loan.pdf.
      * Ein `com.adobe.idp.Document`-Objekt, das das ungeschützte PDF-Dokument enthält.

1. Legen Sie den Wert für die Anfangszahl der Bates fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie die Anfangszahl der Bates fest, indem Sie das `AssemblerOptionSpec`-Objekt `setFirstBatesNumber` aufrufen und einen numerischen Wert übergeben, der den Ausgangswert angibt.

1. Stellen Sie die PDF-Eingabedateien zusammen.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden erforderlichen Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das DDX-Dokument darstellt.
   * Ein `java.util.Map`-Objekt, das die nicht gesicherte PDF-Eingabedatei enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen einschließlich der standardmäßigen Schriftart- und Auftragsprotokollebene angibt.

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Extrahieren Sie die Ergebnisse.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Rufen Sie die `AssemblerResult`-Methode des Objekts `getDocuments` auf. Diese Aktion gibt ein `java.util.Map`-Objekt zurück.
   * Durchlaufen Sie das `java.util.Map`-Objekt, bis Sie das `com.adobe.idp.Document`-Objekt gefunden haben.
   * Rufen Sie die `com.adobe.idp.Document`-Objektmethode `copyToFile` auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Zusammenstellen eines PDF-Dokuments mit Bates-Nummerierung mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenstellen von Dokumenten mit Bates-Nummerierung mithilfe der Webdienst-API {#assemble-documents-with-bates-numbering-using-the-web-service-api}

Stellen Sie mithilfe der Assembler Service API (Webdienst) ein PDF-Dokument zusammen, das eindeutige Seitenkennungen (Bates-Nummerierung) verwendet:

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
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren von PDF-Dokumenten zur Eingabe.

   * Erstellen Sie für jedes PDF-Eingabedokument ein `BLOB`-Dokument mit dessen Konstruktor. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Eingabedatums und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Collection-Objekt wird zum Speichern der PDF-Eingabedokumente verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt. Wenn beispielsweise zwei PDF-Eingabedokumente verwendet werden, erstellen Sie zwei `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekte.
   * Weisen Sie dem Feld `MyMapOf_xsd_string_To_xsd_anyType_Item` des Objekts einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. `key` Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Weisen Sie das `BLOB`-Objekt, in dem das PDF-Dokument gespeichert wird, dem `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objektfeld `value` zu. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * hinzufügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt mit dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType`-Methode des Objekts `Add` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie den Wert für die Anfangszahl der Bates fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie die Anfangszahl der Bates fest, indem Sie dem `firstBatesNumber`-Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen numerischen Wert zuweisen.

1. Stellen Sie die PDF-Eingabedateien zusammen.

   Rufen Sie die `invoke`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die PDF-Eingabedateien enthält. Seine Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und seine Werte müssen die `BLOB`-Objekte sein, die diesen Dateien entsprechen.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `invoke`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Greifen Sie auf das Feld `AssemblerResult` des Objekts zu, bei dem es sich um ein `Map`-Objekt handelt, das die PDF-Dokumente des Ergebnisses enthält.`documents`
   * Durchlaufen Sie das `Map`-Objekt, bis Sie den Schlüssel finden, der dem Namen des resultierenden Dokuments entspricht. Dann wird `value` des Array-Mitglieds in ein `BLOB` umgewandelt.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB`-Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
