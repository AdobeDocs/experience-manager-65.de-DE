---
title: Assemblieren von Dokumenten mit Bates-Nummerierung
seo-title: Assemblieren von Dokumenten mit Bates-Nummerierung
description: 'Verwenden Sie die Bates-Nummerierung, um PDF-Dokumente mithilfe der Java- und Web Service-API zusammenzustellen. '
seo-description: 'Verwenden Sie die Bates-Nummerierung, um PDF-Dokumente mithilfe der Java- und Web Service-API zusammenzustellen. '
uuid: 28d5faeb-6915-41a2-b6a0-78d255df024f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 77e9b895-1313-4a5b-a2d5-cdb65bdc1966
role: Developer
exl-id: 2a4e21c4-f2f5-44cd-b8ed-7b572782a2f1
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 5%

---

# Zusammenstellen von Dokumenten mit Bates-Nummerierung {#assembling-documents-using-bates-numbering}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Mithilfe der Bates-Nummerierung können Sie PDF-Dokumente zusammenstellen, die eindeutige Seitenkennungen enthalten. *Die Bates-* Nummerierung ist eine Methode zur Anwendung eindeutiger Identifikatoren auf einen Batch verwandter Dokumente. Jede Seite im Dokument (oder in einer Gruppe von Dokumenten) erhält eine Bates-Nummer, mit der die Seite eindeutig identifiziert wird. Beispielsweise Produktionsdokumente, die Materialaufstellungsinformationen enthalten und der Herstellung einer Baugruppe zugeordnet sind, können einen Bezeichner enthalten. Eine Bates-Nummer enthält einen sequenziell erhöhten numerischen Wert sowie ein optionales Präfix und Suffix. Das Präfix + numerisch + Suffix wird als *Bates-Muster* bezeichnet.

Die folgende Illustration zeigt ein PDF-Dokument, das einen eindeutigen Bezeichner enthält, der sich in der Kopfzeile des Dokuments befindet.

![au_au_batesnumber](assets/au_au_batesnumber.png)

Für diese Diskussion wird die eindeutige Seitenkennung in der Kopfzeile eines Dokuments platziert. Angenommen, das folgende DDX-Dokument wird verwendet.

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

Dieses DDX-Dokument führt zwei PDF-Dokumente mit den Namen *map.pdf* und *instructions.pdf* in einem einzelnen PDF-Dokument zusammen. Das erstellte PDF-Dokument enthält eine Kopfzeile, die aus einer eindeutigen Seitenkennung besteht. Das Dokument in der obigen Abbildung zeigt beispielsweise 000016.

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden die Konzepte nicht erläutert, z. B. das Erstellen eines Kollektionsobjekts, das Eingabedokumente enthält, oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Kollektionsobjekt. (Siehe [Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein PDF-Dokument mit einer eindeutigen Seitenkennung (Bates-Nummerierung) zusammenzuführen:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren von PDF-Eingabedokumenten.
1. Legen Sie den Anfangswert der Bates-Nummer fest.
1. Zusammenführen der PDF-Eingabedokumente.
1. Extrahieren Sie die Ergebnisse.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Um ein PDF-Dokument mit eindeutigen Seiten-IDs zusammenzuführen, muss das DDX-Dokument das Element `BatesNumber` enthalten.

**Referenzeingabe-PDF-Dokumente**

PDF-Eingabedokumente müssen referenziert werden, um ein PDF-Dokument zusammenzuführen. Beispielsweise müssen die Dokumente &quot;map.pdf&quot;und &quot;locations.pdf&quot;referenziert werden, um diese PDF-Dokumente in einem einzelnen PDF-Dokument zusammenführen zu können.

**Festlegen des anfänglichen Bates-Zahlenwerts**

Sie können den Anfangswert der Bates-Nummer festlegen, um Ihre Geschäftsanforderungen zu erfüllen. Angenommen, der Ausgangswert muss auf 000100 gesetzt werden. Wenn Sie den Anfangswert nicht festlegen, lautet der Wert der ersten Seite 00000.

**Zusammenführen der PDF-Eingabedokumente**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, auf das DDX-Dokument verweisen, das die Elementinformationen `BatesNumber` enthält, auf ein PDF-Eingabedokument verweisen und Laufzeitoptionen festlegen, können Sie den Vorgang `invokeDDX` aufrufen, der dazu führt, dass der Assembler-Dienst ein PDF-Dokument zusammenstellt, das eindeutige Seitenkennungen enthält.

**Ergebnisse extrahieren**

Der Assembler-Dienst gibt ein Collection-Objekt zurück, das die Auftragsergebnisse enthält. Sie können das erstellte PDF-Dokument und alle ausgelösten Ausnahmen extrahieren. In diesem Fall befindet sich ein verschlüsseltes PDF-Dokument im Sammlungsobjekt.

>[!NOTE]
>
>Wenn Sie den Vorgang `invokeDDX` aufrufen, wird ein Kollektionsobjekt zurückgegeben. Dieser Vorgang wird verwendet, wenn zwei oder mehr PDF-Eingabedokumente an den Assembler-Dienst übergeben werden. Wenn Sie jedoch nur ein PDF-Eingabedokument an den Assembler-Dienst übergeben, sollten Sie den Vorgang `invokeOneDocument` aufrufen. Weitere Informationen zur Verwendung dieses Vorgangs finden Sie unter [Assemblieren verschlüsselter PDF-Dokumente](/help/forms/developing/assembling-encrypted-pdf-documents.md).

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblieren von Dokumenten mit Bates-Nummerierung mithilfe der Java-API {#assemble-documents-with-bates-numbering-using-the-java-api}

Stellen Sie mithilfe der Assembler Service-API (Java) ein PDF-Dokument zusammen, das eindeutige Seitenkennungen (Bates-Nummerierung) verwendet:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren von PDF-Eingabedokumenten.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von PDF-Eingabedokumenten mithilfe eines `HashMap`-Konstruktors verwendet wird.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `java.io.FileInputStream` -Objekt, indem Sie dessen Konstruktor verwenden und den Speicherort des PDF-Eingabedokuments übergeben. Übergeben Sie in diesem Fall den Speicherort eines ungesicherten PDF-Dokuments.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.
   * Fügen Sie einen Eintrag zum `java.util.Map`-Objekt hinzu, indem Sie dessen `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. Beispielsweise lautet der Name der im DDX-Dokument angegebenen PDF-Quelldatei, der in diesen Abschnitt eingefügt wird, Loan.pdf.
      * Ein `com.adobe.idp.Document` -Objekt, das das ungesicherte PDF-Dokument enthält.

1. Legen Sie den Anfangswert der Bates-Nummer fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie die Anfangszahl der Bates fest, indem Sie das `setFirstBatesNumber`-Objekt `AssemblerOptionSpec` aufrufen und einen numerischen Wert übergeben, der den Anfangswert angibt.

1. Zusammenführen der PDF-Eingabedokumente.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das DDX-Dokument darstellt.
   * Ein `java.util.Map` -Objekt, das die ungesicherte Eingabedatei enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der standardmäßigen Schrift- und Auftragsprotokollebene.

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Extrahieren Sie die Ergebnisse.

   Um das neu erstellte PDF-Dokument abzurufen, führen Sie die folgenden Schritte aus:

   * Rufen Sie die `getDocuments` -Methode des Objekts `AssemblerResult` auf. Diese Aktion gibt ein `java.util.Map` -Objekt zurück.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): Assemblieren eines PDF-Dokuments mit Bates-Nummerierung mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblieren von Dokumenten mit Bates-Nummerierung mithilfe der Webdienst-API {#assemble-documents-with-bates-numbering-using-the-web-service-api}

Stellen Sie mithilfe der Assembler-Dienst-API (Webdienst) ein PDF-Dokument zusammen, das eindeutige Seitenkennungen (Bates-Nummerierung) verwendet:

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
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren von PDF-Eingabedokumenten.

   * Erstellen Sie für jedes PDF-Eingabedokument ein `BLOB` -Objekt mithilfe des zugehörigen Konstruktors. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Collection-Objekt wird zum Speichern der PDF-Eingabedokumente verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt. Wenn beispielsweise zwei PDF-Eingabedokumente verwendet werden, erstellen Sie zwei `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekte.
   * Weisen Sie dem `key` -Feld des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Weisen Sie das `BLOB`-Objekt, das das PDF-Dokument speichert, dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objektfeld `value` zu. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt zum `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die `Add` -Methode des Objekts `MyMapOf_xsd_string_To_xsd_anyType` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie den Anfangswert der Bates-Nummer fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie die Anfangszahl der Bates fest, indem Sie dem `firstBatesNumber`-Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen numerischen Wert zuweisen.

1. Zusammenführen der PDF-Eingabedokumente.

   Rufen Sie die `invoke` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das DDX-Dokument darstellt.
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die PDF-Eingabedokumente enthält. Die Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und ihre Werte müssen die `BLOB`-Objekte sein, die diesen Dateien entsprechen.
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt.

   Die `invoke`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   Um das neu erstellte PDF-Dokument abzurufen, führen Sie die folgenden Schritte aus:

   * Greifen Sie auf das `AssemblerResult`-Feld des Objekts `documents` zu, bei dem es sich um ein `Map`-Objekt handelt, das die PDF-Dokumente mit den Ergebnissen enthält.
   * Iterieren Sie durch das `Map`-Objekt, bis Sie den Schlüssel finden, der dem Namen des Zieldokuments entspricht. Dann das `value` des Array-Mitglieds in ein `BLOB`-Element umwandeln.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB` -Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
