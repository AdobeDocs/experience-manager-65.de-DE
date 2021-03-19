---
title: Zusammenstellen von PDF-Portfolios
seo-title: Zusammenstellen von PDF-Portfolios
description: Stellen Sie ein PDF-Portfolio zusammen, um mehrere Dokumente verschiedener Typen zu kombinieren, darunter Textdateien, Bilddateien und PDF-Dokumente. Sie können ein PDF-Portfolio mit einer Java-API und einer Webdienst-API zusammenstellen.
seo-description: Stellen Sie ein PDF-Portfolio zusammen, um mehrere Dokumente verschiedener Typen zu kombinieren, darunter Textdateien, Bilddateien und PDF-Dokumente. Sie können ein PDF-Portfolio mit einer Java-API und einer Webdienst-API zusammenstellen.
uuid: 1778c90b-9d26-466b-a7c7-401d737395e0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 023f0d9e-bfde-4879-a839-085fadffb48e
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 3%

---


# Zusammenstellen von PDF-Portfolios {#assembling-pdf-portfolios}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Sie können ein PDF-Portfolio mit der Assembler Java- und Webdienst-API zusammenstellen. Ein Portfolio kann mehrere Dokumente verschiedener Typen kombinieren, darunter Textdateien, Bilddateien (z. B. eine JPEG-Datei) und PDF-Dokumente. Das Layout des Portfolios kann auf verschiedene Stile wie das *Raster mit Vorschau*, das *Auf einem Bild*-Layout oder sogar *Umdrehen* eingestellt werden.

Die folgende Abbildung zeigt einen Screenshot eines Portfolios mit dem Stil-Layout *Auf einem Bild*.

![ap_ap_portfolio](assets/ap_ap_portfolio.png)

Das Erstellen eines PDF-Portfolios ist eine papierlose Alternative zum Übergeben einer Sammlung von Dokumenten. Mit AEM Forms können Sie Portfolios erstellen, indem Sie den Assembler-Dienst mit einem strukturierten DDX-Dokument aufrufen. Das folgende DDX-Dokument ist ein Beispiel für ein DDX-Dokument, das ein PDF-Portfolio erstellt.

```xml
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
     <PDF result="portfolio1.pdf">
         <Portfolio>
             <Navigator source="myNavigator">
                 <Resource name="navigator/image.xxx" source="myImage.png"/>
             </Navigator>
         </Portfolio>
         <PackageFiles source="dog1"  >
              <FieldData name="X">72</FieldData>
             <FieldData name="Y">72</FieldData>
             <File filename="saint_bernard.jpg" mimetype="image/jpeg"/>
         </PackageFiles>
         <PackageFiles source="dog2"  >
             <FieldData name="X">120</FieldData>
             <FieldData name="Y">216</FieldData>
             <File filename="greyhound.pdf"/>
         </PackageFiles>
     </PDF>
 </DDX>
```

Das DXX-Dokument muss ein `Portfolio`-Tag mit einem verschachtelten `Navigator`-Tag enthalten. Beachten Sie, dass das Tag `<Resource name="navigator/image.xxx" source="myImage.png"/>` nur erforderlich ist, wenn `myNavigator` als onImage-Layoutnavigator zugewiesen ist: `AdobeOnImage.nav`. Mit diesem Tag kann der Assembler-Dienst das Bild auswählen, das als Portfoliohintergrund verwendet werden soll. Fügen Sie die Tags `PackageFiles` und `File` ein, um den Dateinamen und den MIME-Typ der gepackten Datei zu definieren.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So erstellen Sie ein PDF-Portfolio:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Verweisen Sie auf die erforderlichen Dokumente.
1. Legen Sie Laufzeitoptionen fest.
1. Assemblieren Sie das Portfolio.
1. Speichern Sie das assemblierte Portfolio.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, erstellen Sie einen Assembler-Dienstclient.

**Ein vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Portfolios muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss die Elemente `Portfolio`, `Navigator` und `PackageFiles` enthalten.

**Die erforderlichen Dokumente referenzieren**

Um ein PDF-Portfolio zusammenzustellen, verweisen Sie auf alle Dateien, die die zu assemblierenden Dokumente repräsentieren. Übergeben Sie beispielsweise alle im DDX-Dokument angegebenen Bilddateien an den Assembler-Dienst. Beachten Sie, dass auf diese Dateien im DDX-Dokument verwiesen wird, das in diesem Abschnitt angegeben ist: *myImage.png* und *saint_bernard.jpg*.

Übergeben Sie beim Zusammenstellen eines PDF-Portfolios eine NAV-Datei (eine Navigatordatei) an den Assembler-Dienst. Die an den Assembler-Dienst übergebene NAV-Datei hängt davon ab, welche Art von PDF-Portfolio erstellt werden soll. Um beispielsweise ein *Layout für ein Bild* zu erstellen, übergeben Sie die Datei &quot;AdobeOnImage.nav&quot;. Sie können NAV-Dateien im folgenden Ordner suchen:

`<Install folder>\Acrobat 9.0\Acrobat\Navigators`

Kopieren Sie die NAV-Datei aus dem Installationsordner von Acrobat 9 (oder höher). Platzieren Sie die NAV-Datei an einem Speicherort, an dem die Clientanwendung darauf zugreifen kann. Alle Dateien werden innerhalb eines Map-Sammlungsobjekts an den Assembler-Dienst übergeben.

>[!NOTE]
>
>Die schnellen Beginn, die mit Assembling PDF-Portfolios verknüpft sind, verwenden AdobeOnImage.nav.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren.

**Assemblieren des Portfolios**

Zum Zusammenführen eines PDF-Portfolios rufen Sie den Vorgang `invokeDDX` auf. Der Assembler-Dienst gibt das PDF-Portfolio in einem Collection-Objekt zurück.

**Speichern des assemblierten Portfolios**

Ein PDF-Portfolio wird innerhalb eines Collection-Objekts zurückgegeben. Durchsuchen Sie das Sammlungsobjekt und speichern Sie PDF-Portfolio als PDF-Datei.

**Siehe auch**

[Zusammenstellen eines PDF-Portfolios mit der Java-API](#assemble-a-pdf-portfolio-using-the-java-api)

[Zusammenstellen eines PDF-Portfolios mit der Webdienst-API](#assemble-a-pdf-portfolio-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenstellen eines PDF-Portfolios mit der Java-API {#assemble-a-pdf-portfolio-using-the-java-api}

Stellen Sie ein PDF-Portfolio mithilfe der Assembler Service API (Java) zusammen:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf die erforderlichen Dokumente.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von PDF-Eingabedokumenten mit einem `HashMap`-Konstruktor verwendet wird.
   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Geben Sie den Speicherort der erforderlichen NAV-Datei an (wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das die NAV-Datei enthält (wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
   * hinzufügen Sie einen Eintrag für das `java.util.Map`-Objekt, indem Sie die `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. (Wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
      * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält. (Wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `setFailOnError`-Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Assemblieren Sie das Portfolio.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden erforderlichen Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das die zum Erstellen eines PDF-Portfolios erforderlichen Dateien enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Protokollierungsstufe des Auftrags

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das das assemblierte PDF-Portfolio und alle auftretenden Ausnahmen enthält.

1. Speichern Sie das assemblierte Portfolio.

   So rufen Sie das PDF-Portfolio ab:

   * Rufen Sie die `AssemblerResult`-Methode des Objekts `getDocuments` auf. Diese Methode gibt ein `java.util.Map`-Objekt zurück.
   * Durchlaufen Sie das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `com.adobe.idp.Document`-Objektmethode `copyToFile` auf, um das PDF-Portfolio zu extrahieren.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Zusammenstellen von PDF-Portfolios mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-portfolios-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenstellen eines PDF-Portfolios mit der Webdienst-API {#assemble-a-pdf-portfolio-using-the-web-service-api}

Assemblieren eines PDF-Portfolios mit der Assembler-Dienst-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf die erforderlichen Dokumente.

   * Erstellen Sie für jede Eingabedatei ein `BLOB`-Objekt mit dessen Konstruktor. Das `BLOB`-Objekt wird zum Speichern der Eingabedatei verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort der Eingabedatei und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Collection-Objekt wird zum Speichern von Eingabedateien verwendet, die zum Erstellen eines PDF-Portfolios erforderlich sind.
   * Erstellen Sie für jede Eingabedatei ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie dem Feld `MyMapOf_xsd_string_To_xsd_anyType_Item` des Objekts einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. `key` Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Elements übereinstimmen. (Führen Sie diese Aufgabe für jede Eingabedatei aus.)
   * Weisen Sie das `BLOB`-Objekt, das die Eingabedatei speichert, dem `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objektfeld `value` zu. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * hinzufügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt mit dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType`-Methode des Objekts `Add` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenmember, der zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie `false` dem `AssemblerOptionSpec`-Datenmember des Objekts `failOnError` zu.

1. Assemblieren Sie das Portfolio.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das assemblierte Portfolio.

   So rufen Sie das neu erstellte PDF-Portfolio ab:

   * Greifen Sie auf das Feld `AssemblerResult` des Objekts zu, bei dem es sich um ein `Map`-Objekt mit den resultierenden PDF-Dokumenten handelt.`documents`
   * Durchlaufen Sie das `Map`-Objekt, um jedes resultierende Dokument abzurufen. Anschließend können Sie die `value` des Array-Mitglieds in ein `BLOB`-Element umwandeln.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB`-Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
