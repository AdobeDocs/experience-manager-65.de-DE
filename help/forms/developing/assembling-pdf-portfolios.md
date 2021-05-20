---
title: Zusammenstellen von PDF-Portfolios
seo-title: Zusammenstellen von PDF-Portfolios
description: Stellen Sie ein PDF-Portfolio zusammen, um mehrere Dokumente verschiedener Typen zu kombinieren, darunter Textdateien, Bilddateien und PDF-Dokumente. Sie können ein PDF-Portfolio mithilfe einer Java-API und einer Web Service-API zusammenstellen.
seo-description: Stellen Sie ein PDF-Portfolio zusammen, um mehrere Dokumente verschiedener Typen zu kombinieren, darunter Textdateien, Bilddateien und PDF-Dokumente. Sie können ein PDF-Portfolio mithilfe einer Java-API und einer Web Service-API zusammenstellen.
uuid: 1778c90b-9d26-466b-a7c7-401d737395e0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 023f0d9e-bfde-4879-a839-085fadffb48e
role: Developer
exl-id: d2bd7c3e-4f75-4234-a7aa-ee8524430493
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1865'
ht-degree: 3%

---

# Zusammenstellen von PDF-Portfolios {#assembling-pdf-portfolios}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Sie können ein PDF-Portfolio mit der Assembler-Java- und Webdienst-API zusammenstellen. Ein Portfolio kann mehrere Dokumente verschiedener Typen kombinieren, darunter Textdateien, Bilddateien (z. B. eine JPEG-Datei) und PDF-Dokumente. Das Layout des Portfolios kann auf verschiedene Stile wie das *Raster mit Vorschau*, das *Auf einem Bild*-Layout oder sogar *Revolve* festgelegt werden.

Die folgende Abbildung zeigt einen Screenshot eines Portfolios mit *In einem Bild*-Stillayout.

![ap_ap_portfolio](assets/ap_ap_portfolio.png)

Das Erstellen eines PDF-Portfolios dient als papierlose Alternative zur Übergabe einer Dokumentensammlung. Mit AEM Forms können Sie Portfolios erstellen, indem Sie den Assembler-Dienst mit einem strukturierten DDX-Dokument aufrufen. Das folgende DDX-Dokument ist ein Beispiel für ein DDX-Dokument, das ein PDF-Portfolio erstellt.

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

Das DXX-Dokument muss ein `Portfolio`-Tag mit einem verschachtelten `Navigator`-Tag enthalten. Beachten Sie, dass das Tag `<Resource name="navigator/image.xxx" source="myImage.png"/>` nur erforderlich ist, wenn `myNavigator` als onImage-Layout-Navigator zugewiesen ist: `AdobeOnImage.nav`. Mit diesem Tag kann der Assembler-Dienst das Bild auswählen, das als Portfoliohintergrund verwendet werden soll. Fügen Sie die Tags `PackageFiles` und `File` ein, um den Dateinamen und den MIME-Typ der gepackten Datei zu definieren.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Portfolio zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie die erforderlichen Dokumente.
1. Legen Sie Laufzeitoptionen fest.
1. Assemblieren des Portfolios.
1. Speichern Sie das assemblierte Portfolio.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, erstellen Sie einen Assembler-Dienst-Client.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Portfolios muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss die Elemente `Portfolio`, `Navigator` und `PackageFiles` enthalten.

**Referenzieren der erforderlichen Dokumente**

Referenzieren Sie zum Zusammenführen eines PDF-Portfolios alle Dateien, die die zu assemblierenden Dokumente darstellen. Übergeben Sie beispielsweise alle im DDX-Dokument angegebenen Bilddateien an den Assembler-Dienst. Beachten Sie, dass diese Dateien im DDX-Dokument referenziert werden, das in diesem Abschnitt angegeben ist: *myImage.png* und *saint_bernard.jpg*.

Übergeben Sie beim Assemblieren eines PDF-Portfolios eine NAV-Datei (eine Navigatordatei) an den Assembler-Dienst. Die NAV-Datei, die Sie an den Assembler-Dienst übergeben, hängt davon ab, welcher Typ von PDF-Portfolio erstellt werden soll. Um beispielsweise ein Layout *In einem Bild* zu erstellen, übergeben Sie die Datei &quot;AdobeOnImage.nav&quot;. NAV-Dateien befinden sich im folgenden Ordner:

`<Install folder>\Acrobat 9.0\Acrobat\Navigators`

Kopieren Sie die NAV-Datei aus dem Installationsordner von Acrobat 9 (oder höher). Platzieren Sie die NAV-Datei an einem Speicherort, an dem Ihre Client-Anwendung darauf zugreifen kann. Alle Dateien werden in einem Map-Sammlungsobjekt an den Assembler-Dienst übergeben.

>[!NOTE]
>
>Die Schnellstarts, die mit Assembling PDF-Portfolios verknüpft sind, verwenden AdobeOnImage.nav.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Assemblieren des Portfolios**

Um ein PDF-Portfolio zusammenzuführen, rufen Sie den Vorgang `invokeDDX` auf. Der Assembler-Dienst gibt das PDF-Portfolio in einem Collection-Objekt zurück.

**Speichern des assemblierten Portfolios**

Ein PDF-Portfolio wird innerhalb eines Collection-Objekts zurückgegeben. Durchsuchen Sie das Sammlungsobjekt und speichern Sie PDF-Portfolio als PDF-Datei.

**Siehe auch**

[Zusammenführen eines PDF-Portfolios mit der Java-API](#assemble-a-pdf-portfolio-using-the-java-api)

[Zusammenführen eines PDF-Portfolios mithilfe der Webdienst-API](#assemble-a-pdf-portfolio-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Assemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenführen eines PDF-Portfolios mithilfe der Java-API {#assemble-a-pdf-portfolio-using-the-java-api}

Assemblieren eines PDF-Portfolios mithilfe der Assembler-Dienst-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie die erforderlichen Dokumente.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von PDF-Eingabedokumenten mit einem `HashMap`-Konstruktor verwendet wird.
   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie den Speicherort der erforderlichen NAV-Datei (wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das die NAV-Datei enthält (wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
   * Fügen Sie einen Eintrag zum `java.util.Map`-Objekt hinzu, indem Sie dessen `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. (Wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
      * Ein `com.adobe.idp.Document` -Objekt, das das PDF-Dokument enthält. (Wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `setFailOnError` -Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Assemblieren des Portfolios.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das zu verwendende DX-Dokument darstellt
   * Ein `java.util.Map` -Objekt, das die zum Erstellen eines PDF-Portfolios erforderlichen Dateien enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschriftart und der Auftragsprotokollebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das das assemblierte PDF-Portfolio und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das assemblierte Portfolio.

   Führen Sie die folgenden Schritte aus, um das PDF-Portfolio abzurufen:

   * Rufen Sie die `getDocuments` -Methode des Objekts `AssemblerResult` auf. Diese Methode gibt ein `java.util.Map` -Objekt zurück.
   * Iterieren Sie durch das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf, um das PDF-Portfolio zu extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): Assemblieren von PDF-Portfolios mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-portfolios-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblieren eines PDF-Portfolios mithilfe der Webdienst-API {#assemble-a-pdf-portfolio-using-the-web-service-api}

Assemblieren eines PDF-Portfolios mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie die erforderlichen Dokumente.

   * Erstellen Sie für jede Eingabedatei ein `BLOB` -Objekt mithilfe des zugehörigen Konstruktors. Das `BLOB`-Objekt wird zum Speichern der Eingabedatei verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der Eingabedatei und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Collection-Objekt wird zum Speichern von Eingabedateien verwendet, die zum Erstellen eines PDF-Portfolios erforderlich sind.
   * Erstellen Sie für jede Eingabedatei ein `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Weisen Sie dem `key` -Feld des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Elements übereinstimmen. (Führen Sie diese Aufgabe für jede Eingabedatei aus.)
   * Weisen Sie das `BLOB`-Objekt, das die Eingabedatei speichert, dem `value` -Feld des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` zu. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt zum `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die `Add` -Methode des Objekts `MyMapOf_xsd_string_To_xsd_anyType` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe des zugehörigen Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec` -Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` dem `AssemblerOptionSpec`-Datenelement des `failOnError`-Objekts zu.

1. Assemblieren des Portfolios.

   Rufen Sie die `invokeDDX` -Methode des Objekts `AssemblerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das assemblierte Portfolio.

   Um das neu erstellte PDF-Portfolio abzurufen, führen Sie die folgenden Schritte aus:

   * Greifen Sie auf das `AssemblerResult`-Feld des Objekts `documents` zu, bei dem es sich um ein `Map`-Objekt handelt, das die resultierenden PDF-Dokumente enthält.
   * Durchsuchen Sie das `Map`-Objekt, um jedes Zieldokument abzurufen. Dann das `value` des Array-Mitglieds in ein `BLOB`-Element umwandeln.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB` -Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
