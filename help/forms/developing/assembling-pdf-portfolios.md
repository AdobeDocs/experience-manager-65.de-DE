---
title: Zusammenstellen von PDF-Portfolios
description: Stellen Sie ein PDF-Portfolio zusammen, in dem verschiedene Dokumente kombiniert sind, darunter Word-Dateien, Bilddateien und PDF-Dokumente. Sie können ein PDF-Portfolio mithilfe einer Java-API und einer Web Service-API zusammenstellen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: d2bd7c3e-4f75-4234-a7aa-ee8524430493
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1815'
ht-degree: 100%

---

# Zusammenstellen von PDF-Portfolios {#assembling-pdf-portfolios}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Ein PDF-Portfolio lässt sich mithilfe des Assemblers Java und der Web-Service-API zusammenstellen. In einem Portfolio können mehrere Dokumente verschiedener Typen kombiniert sein, darunter Word-Dateien, Bilddateien (zum Beispiel eine JPEG-Datei) und PDF-Dokumente. Für das Layout des Portfolios können verschiedene Stile wie *Raster mit Vorschau*, *In einem Bild* oder auch *Drehen* festgelegt werden.

Die folgende Abbildung zeigt einen Screenshot eines Portfolios mit dem Stil-Layout *In einem Bild*.

![ap_ap_portfolio](assets/ap_ap_portfolio.png)

Das Erstellen eines PDF-Portfolios dient als papierlose Alternative, um eine Sammlung von Dokumenten weiterzugeben. Mit AEM Forms können Sie Portfolios erstellen, indem Sie den Assembler-Service mit einem strukturierten DDX-Dokument aufrufen. Das folgende DDX-Dokument ist ein Beispiel für ein DDX-Dokument, das ein PDF-Portfolio erstellt.

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

Das DXX-Dokument muss ein `Portfolio`-Tag mit einem verschachtelten `Navigator`-Tag enthalten. Beachten Sie, dass das Tag `<Resource name="navigator/image.xxx" source="myImage.png"/>` nur dann erforderlich ist, wenn `myNavigator` als onImage-Layout-Navigator zugewiesen ist: `AdobeOnImage.nav`. Dieses Tag ermöglicht dem Assembler-Service das Bild auswählen, das als Portfoliohintergrund verwendet werden soll. Schließen Sie `PackageFiles`- und `File`-Tags zum Definieren des Dateinamens und MIME-Typs der gepackten Datei mit ein.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Referenz für Assembler-Service und DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Portfolio zu erstellen, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie die erforderlichen Dokumente.
1. Legen Sie Laufzeitoptionen fest.
1. Assemblieren Sie das Portfolio.
1. Speichern Sie das assemblierte Portfolio.

**Einschließen der Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Service-Client erstellen.

**Referenzieren eines vorhandenen DDX-Dokuments**

Zum Zusammenstellen eines PDF-Portfolios muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss Folgendes enthalten: `Portfolio`, `Navigator` und `PackageFiles`-Elemente.

**Referenzieren der erforderlichen Dokumente**

Referenzieren Sie zum Zusammenstellen eines PDF-Portfolios alle Dateien, die die zusammenzuführenden Dokumente darstellen. Übergeben Sie beispielsweise alle im DDX-Dokument angegebenen Bilddateien an den Assembler-Service. Beachten Sie, dass diese Dateien in dem DDX-Dokument referenziert werden, das in diesem Abschnitt angegeben ist: *myImage.png* und *saint_bernard.jpg*.

Übergeben Sie beim Zusammenstellen eines PDF-Portfolios eine NAV-Datei (eine Navigatordatei) an den Assembler-Service. Die NAV-Datei, die Sie an den Assembler-Service übergeben, hängt davon ab, welcher PDF-Portfolio-Typ erstellt werden soll. Um beispielsweise ein Layout *In einem Bild* zu erstellen, übergeben Sie die Datei AdobeOnImage.nav. NAV-Dateien befinden sich üblicherweise in folgendem Ordner:

`<Install folder>\Acrobat 9.0\Acrobat\Navigators`

Kopieren Sie die NAV-Datei aus dem Installationsverzeichnis von Acrobat 9 (oder höher). Fügen Sie die NAV-Datei an einem Speicherort ein, an dem Ihr Client-Programm darauf zugreifen kann. Alle Dateien werden in einem Map-Sammlungsobjekt an den Assembler-Service übergeben.

>[!NOTE]
>
>Die Schnellstarts, die mit dem „Zusammenstellen von PDF-Portfolios“ verknüpft sind, verwenden AdobeOnImage.nav.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Zusammenstellen des Portfolios**

Um ein PDF-Portfolio zusammenzustellen, rufen Sie den Vorgang `invokeDDX` auf. Der Assembler-Service gibt das PDF-Portfolio in einem Sammlungsobjekt zurück.

**Speichern des zusammengestellten Portfolios**

Ein PDF-Portfolio wird in einem Sammlungsobjekt zurückgegeben. Navigieren Sie durch das Sammlungsobjekt und speichern Sie das PDF-Portfolio als PDF-Datei.

**Siehe auch**

[Assemblieren eines PDF-Portfolios mithilfe der Java-API](#assemble-a-pdf-portfolio-using-the-java-api)

[Assemblieren eines PDF-Portfolios mithilfe der Webservice-API](#assemble-a-pdf-portfolio-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatisches Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblieren eines PDF-Portfolios mithilfe der Java-API {#assemble-a-pdf-portfolio-using-the-java-api}

Assemblieren eines PDF-Portfolios mithilfe der Assembler-Service-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie die erforderlichen Dokumente.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von Eingabe-PDF-Dokumenten verwendet wird, indem Sie einen `HashMap`-Konstruktor verwenden.
   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie den Speicherort der erforderlichen NAV-Datei (wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das die NAV-Datei enthält (wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
   * Fügen Sie dem `java.util.Map`-Objekt einen Eintrag hinzu, indem Sie dessen `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Eine Zeichenfolge, die den Speichernamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. (Wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
      * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält. (Wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags im Falle eines Fehlers fortzusetzen, rufen Sie die Methode `setFailOnError` des `AssemblerOptionSpec`-Objekts auf und übergeben Sie `false`.

1. Assemblieren Sie das Portfolio.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das die Dateien enthält, die zum Erstellen eines PDF-Portfolios erforderlich sind.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschriftart und der Auftragsprotokollebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das das assemblierte PDF-Portfolio und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das assemblierte Portfolio.

   Führen Sie die folgenden Schritte aus, um das PDF-Portfolio abzurufen:

   * Rufen Sie die Methode `getDocuments` des `AssemblerResult`-Objekts auf. Diese Methode gibt ein `java.util.Map`-Objekt zurück.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `copyToFile`-Methode des `com.adobe.idp.Document`-Objekts auf, um das PDF-Portfolio zu extrahieren.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Zusammenstellen von PDF-Portfolios mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-portfolios-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblieren eines PDF-Portfolios mithilfe der Webservice-API {#assemble-a-pdf-portfolio-using-the-web-service-api}

Assemblieren eines PDF-Portfolios mithilfe der Assembler-Service-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Service-Referenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen standardmäßigen Konstruktor verwenden.
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
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus enthält, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekt gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Befüllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie die erforderlichen Dokumente.

   * Erstellen Sie für jede Eingabedatei ein `BLOB`-Objekt, indem Sie dessen Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern der Eingabedatei verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgewert übergeben, der den Dateispeicherort der Eingabedatei und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt mit den Inhalten des Byte-Arrays, indem Sie sein `MTOM`-Feld zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Sammlungsobjekt wird verwendet, um Eingabedateien zu speichern, die zur Erstellung eines PDF-Portfolios erforderlich sind.
   * Erstellen Sie für jede Eingabedatei ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie dem `key`-Feld des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts einen Zeichenfolgewert zu, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Elements übereinstimmen. (Führen Sie diese Aufgabe für jede Eingabedatei aus.)
   * Weisen Sie das `BLOB`-Objekt, das die Eingabedatei speichert, dem Feld `value` des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt zum `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die Methode `Add` des `MyMapOf_xsd_string_To_xsd_anyType`-Objekts auf, und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem Datenelement `failOnError` des `AssemblerOptionSpec`-Objekts zu.

1. Assemblieren Sie das Portfolio.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * A `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die Methode `invokeDDX` gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags sowie alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das assemblierte Portfolio.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Portfolio abzurufen:

   * Greifen Sie auf das Feld `documents` des `AssemblerResult`-Objekts zu, das ein `Map`-Objekt ist, welches die resultierenden PDF-Dokumente enthält.
   * Iterieren Sie durch das `Map`-Objekt, um jedes resultierende Dokument zu erhalten. Wandeln Sie dann `value` der Array-Elemente in `BLOB` um.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `MTOM`-Eigenschaft von dessen `BLOB`-Objekt zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
