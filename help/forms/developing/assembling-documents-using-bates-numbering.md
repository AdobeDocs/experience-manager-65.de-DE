---
title: Zusammenstellen von Dokumenten mithilfe der Bates-Nummerierung
description: Verwenden Sie die Bates-Nummerierung, um PDF-Dokumente mithilfe der Java- und Webservice-API zusammenzustellen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 2a4e21c4-f2f5-44cd-b8ed-7b572782a2f1
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 100%

---

# Zusammenstellen von Dokumenten mithilfe der Bates-Nummerierung {#assembling-documents-using-bates-numbering}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Mithilfe der Bates-Nummerierung können Sie PDF-Dokumente zusammenstellen, die eindeutige Seitenkennungen enthalten. *Bates-Nummerierung* ist eine Methode zur Anwendung von eindeutigen Identifikatoren auf einen Stapel verwandter Dokumente. Jede Seite im Dokument (oder in einer Gruppe von Dokumenten) erhält eine Bates-Nummer, mit der die Seite eindeutig identifiziert wird. Beispielsweise können Fertigungsdokumente, die Materialaufstellungsinformationen enthalten und mit der Herstellung einer Baugruppe verbunden sind, eine Kennung enthalten. Eine Bates-Nummer enthält einen numerischen Wert, der sequenziell inkrementiert wird, sowie ein optionales Präfix und Suffix. Das Präfix + numerisch + Suffix wird als *Bates-Muster* bezeichnet.

Die folgende Abbildung zeigt ein PDF-Dokument mit einer eindeutigen Kennung in der Kopfzeile des Dokuments.

![au_au_batesnumber](assets/au_au_batesnumber.png)

Für die Zwecke dieser Diskussion wird die eindeutige Seitenkennung in der Kopfzeile eines Dokuments platziert. Angenommen, das folgende DDX-Dokument wird verwendet.

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

Dieses DDX-Dokument führt zwei PDF-Dokumente mit dem Namen *map.pdf* und *instructions.pdf* in einem einzigen PDF-Dokument zusammen. Das PDF-Zieldokument enthält eine Kopfzeile, die aus einer eindeutigen Seitenkennung besteht. Das Dokument in der obigen Abbildung zeigt beispielsweise 000016.

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden die Konzepte nicht erläutert, wie z. B. das Erstellen eines Sammlungsobjekts, das Eingabedokumente enthält, oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Sammlungsobjekt. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Weitere Informationen zum Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument mit einer eindeutigen Seitenkennung (Bates-Nummerierung) zusammenzustellen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie die PDF-Eingabedokumente.
1. Legen Sie den Anfangswert der Bates-Nummer fest.
1. Stellen Sie die PDF-Eingabedokumente zusammen.
1. Extrahieren Sie die Ergebnisse.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Programm-Server bereitgestellt wird, bei dem es sich nicht um JBoss handelt, müssen Sie die Dateien „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Programm-Server sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines PDF-Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Referenzieren eines bestehenden DDX-Dokuments**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Um ein PDF-Dokument zusammenzustellen, das eindeutige Seitenkennungen enthält, muss das DDX-Dokument das Element `BatesNumber` enthalten.

**Referenzieren von PDF-Eingabedokumenten**

PDF-Eingabedokumente müssen referenziert werden, um ein PDF-Dokument zusammenzustellen. Beispielsweise müssen die Dokumente „map.pdf“ und „directions.pdf“ referenziert werden, um diese PDF-Dokumente in einem einzigen PDF-Dokument zusammenzustellen.

**Festlegen des anfänglichen Bates-Zahlenwerts**

Sie können den Anfangswert der Bates-Nummer so festlegen, dass er Ihre Geschäftsanforderungen erfüllt. Angenommen, der Ausgangswert muss auf 000100 gesetzt werden. Wenn Sie den Anfangswert nicht festlegen, lautet der Wert der ersten Seite 000000.

**Zusammenstellen der PDF-Eingabedokumente**

Nachdem Sie den Assembler-Service-Client erstellt haben, das DDX-Dokument referenziert haben, das Informationen zum Element `BatesNumber` enthält, ein PDF-Eingabedokument referenziert haben und Laufzeitoptionen festgelegt haben, können Sie den Vorgang `invokeDDX` aufrufen, der dazu führt, dass der Assembler-Service ein PDF-Dokument zusammenstellt, welches eindeutige Seitenkennungen enthält.

**Extrahieren der Ergebnisse**

Der Assembler-Service gibt ein Sammlungsobjekt zurück, das die Auftragsergebnisse enthält. Sie können das PDF-Zieldokument und alle ausgelösten Ausnahmen extrahieren. In diesem Fall befindet sich ein verschlüsseltes PDF-Dokument im Sammlungsobjekt.

>[!NOTE]
>
>Ein Sammlungsobjekt wird zurückgegeben, wenn Sie den Vorgang `invokeDDX` aufrufen. Dieser Vorgang wird verwendet, wenn zwei oder mehr PDF-Eingabedokumente an den Assembler-Service übergeben werden. Wenn Sie jedoch nur ein PDF-Eingabedokument an den Assembler-Service übergeben, sollten Sie den Vorgang `invokeOneDocument` aufrufen. Weitere Informationen zur Verwendung dieses Vorgangs finden Sie unter [Zusammenstellen verschlüsselter PDF-Dokumente](/help/forms/developing/assembling-encrypted-pdf-documents.md).

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatisches Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenstellen von Dokumenten mit Bates-Nummerierung mithilfe der Java-API {#assemble-documents-with-bates-numbering-using-the-java-api}

So stellen Sie mithilfe der Assembler Service-API (Java) ein PDF-Dokument zusammen, das eindeutige Seitenkennungen (Bates-Nummerierung) verwendet:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie die PDF-Eingabedokumente.

   * Erstellen Sie mithilfe eines `HashMap`-Konstruktors ein `java.util.Map`-Objekt zum Speichern von Eingabe-PDF-Dokumenten.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des PDF-Eingabedokuments übergeben. Übergeben Sie in diesem Fall den Speicherort eines ungesicherten PDF-Dokuments.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.
   * Fügen Sie dem `java.util.Map`-Objekt durch Aufrufen seiner `put`-Methode und Übergeben der folgenden Argumente einen Eintrag hinzu:

      * Eine Zeichenfolge, die den Speichernamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. Der Name der PDF-Quelldatei im DDX-Dokument, das in diesem Abschnitt vorgestellt wird, lautet beispielsweise Loan.pdf.
      * Ein `com.adobe.idp.Document`-Objekt, das das ungesicherte PDF-Dokument enthält.

1. Legen Sie den Anfangswert der Bates-Nummer fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie die anfängliche Bates-Nummer fest, indem Sie die `setFirstBatesNumber` des `AssemblerOptionSpec`-Objekts aufrufen und einen numerischen Wert übergeben, der den Anfangswert angibt.

1. Stellen Sie die PDF-Eingabedokumente zusammen.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das DDX-Dokument darstellt.
   * Ein `java.util.Map`-Objekt, das die ungesicherte PDF-Eingabedatei enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Vorgangslogebene.

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Extrahieren Sie die Ergebnisse.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die Methode `getDocuments` des `AssemblerResult`-Objekts auf. Diese Aktion gibt ein `java.util.Map`-Objekt zurück.
   * Gehen Sie schrittweise durch das `java.util.Map`-Objekt, bis Sie das `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): Zusammenstellen eines PDF-Dokuments mit Bates-Nummerierung mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenstellen von Dokumenten mit Bates-Nummerierung unter Verwendung der Webservice-API {#assemble-documents-with-bates-numbering-using-the-web-service-api}

Stellen Sie mithilfe der Assembler-Service-API (Web-Service) ein PDF-Dokument zusammen, das eindeutige Seitenkennungen (Bates-Nummerierung) verwendet:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgenwert mit der WSDL an den AEM Forms-Service (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekr, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein Objekt `System.IO.FileStream`, indem Sie den Konstruktor aufrufen und einen String-Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus, in dem die Datei geöffnet werden soll, repräsentiert.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld den Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie die PDF-Eingabedokumente.

   * Erstellen Sie für jedes PDF-Eingabedokument ein `BLOB`-Objekt, indem Sie seinen Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Sammlungsobjekt wird zum Speichern der PDF-Eingabedokumente verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt. Wenn beispielsweise zwei PDF-Eingabedokumente verwendet werden, erstellen Sie zwei `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekte.
   * Weisen Sie dem Feld `key` des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Weisen Sie das `BLOB`-Objekt, das das PDF-Dokument speichert, dem Feld `value` des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt zum `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die Methode `Add` des `MyMapOf_xsd_string_To_xsd_anyType`-Objekts auf, und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie den Anfangswert der Bates-Nummer fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie die anfängliche Bates-Nummer fest, indem Sie dem Datenelement `firstBatesNumber`, das zum `AssemblerOptionSpec`-Objekt gehört, einen numerischen Wert zuweisen.

1. Stellen Sie die PDF-Eingabedokumente zusammen.

   Rufen Sie die Methode `invoke` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die PDF-Eingabedokumente enthält. Seine Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und seine Werte müssen die `BLOB`-Objekte sein, die diesen Dateien entsprechen.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die Methode `invoke` gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und eventuell aufgetretene Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Greifen Sie auf das Feld `documents` des `AssemblerResult`-Objekts zu, das ein `Map`-Objekt ist, das die PDF-Ergebnisdokumente enthält.
   * Iterieren Sie durch das `Map`-Objekt, bis Sie den Schlüssel finden, der dem Namen des Ergebnisdokuments entspricht. Anschließend wandeln Sie den `value` dieses Array-Mitglieds in ein `BLOB` um.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `MTOM`-Eigenschaft des `BLOB`-Objekts zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
