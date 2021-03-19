---
title: Programmgesteuertes Zusammenstellen von PDF-Dokumenten
seo-title: Programmgesteuertes Zusammenstellen von PDF-Dokumenten
description: Verwenden Sie die Assembler-Dienst-API, um mehrere PDF-Dokumente mithilfe der Java-API und der Web-Service-API in einem einzigen PDF-Dokument zusammenzuführen.
seo-description: Verwenden Sie die Assembler-Dienst-API, um mehrere PDF-Dokumente mithilfe der Java-API und der Web-Service-API in einem einzigen PDF-Dokument zusammenzuführen.
uuid: aa3f8f39-1fbc-48d0-82ff-6caaadf125fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: ebe8136b-2a79-4035-b9d5-aa70a5bbd4af
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2153'
ht-degree: 2%

---


# Programmgesteuertes Zusammenstellen von PDF-Dokumenten {#programmatically-assembling-pdf-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Sie können die Assembler-Dienst-API verwenden, um mehrere PDF-Dokumente in einem einzigen PDF-Dokument zusammenzustellen. Die folgende Abbildung zeigt, wie drei PDF-Dokumente in einem einzigen PDF-Dokument zusammengeführt werden.

![pa_pa_Dokument_assembly](assets/pa_pa_document_assembly.png)

Um zwei oder mehr PDF-Dokumente in einem einzigen PDF-Dokument zusammenzuführen, benötigen Sie ein DDX-Dokument. Ein DDX-Dokument beschreibt das vom Assembler-Dienst erstellte PDF-Dokument. Das heißt, das DDX-Dokument weist den Assembler-Dienst an, welche Aktionen ausgeführt werden sollen.

Für diese Diskussion nehmen Sie an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
     <PDF result="out.pdf">
         <PDF source="map.pdf" />
         <PDF source="directions.pdf" />
     </PDF>
 </DDX>
```

Dieses DDX-Dokument führt zwei PDF-Dokumente mit den Namen *map.pdf* und *directions.pdf* in einem PDF-Dokument zusammen.

>[!NOTE]
>
>Informationen zum Anzeigen eines DDX-Dokuments, das ein PDF-Dokument disassembliert, finden Sie unter [Programmgesteuertes Disassemblieren von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents).

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Überlegungen beim Aufrufen des Assembler-Dienstes mit Webdiensten {#considerations-when-invoking-assembler-service-using-web-services}

Wenn Sie beim Zusammenstellen großer Dokumente Kopf- und Fußzeilen hinzufügen, tritt möglicherweise ein `OutOfMemory`-Fehler auf, und die Dateien werden nicht zusammengeführt. Um die Wahrscheinlichkeit zu verringern, dass dieses Problem auftritt, fügen Sie dem DDX-Dokument ein `DDXProcessorSetting`-Element hinzu, wie im folgenden Beispiel gezeigt.

`<DDXProcessorSetting name="checkpoint" value="2000" />`

Sie können dieses Element als untergeordnetes Element des Elements `DDX` oder als untergeordnetes Element eines Elements `PDF result` hinzufügen. Der Standardwert für diese Einstellung ist 0 (null), wodurch der Checkpoint deaktiviert wird und sich das DDX so verhält, als wäre das `DDXProcessorSetting`-Element nicht vorhanden. Wenn Sie einen `OutOfMemory`-Fehler gefunden haben, müssen Sie den Wert möglicherweise auf eine Ganzzahl einstellen, in der Regel zwischen 500 und 5000. Ein kleiner Checkpoint-Wert führt zu einem häufigeren Checkpoint.

## Zusammenfassung der Schritte {#summary-of-steps}

So assemblieren Sie ein einzelnes PDF-Dokument aus mehreren PDF-Dokumenten:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Referenzieren von PDF-Dokumenten zur Eingabe.
1. Legen Sie Laufzeitoptionen fest.
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

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Client erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Dieses DDX-Dokument weist den Assembler-Dienst an, zwei PDF-Dokumente in einem einzigen PDF-Dokument zusammenzuführen.

**PDF-Dokumente zur Referenzeingabe**

Verweisen Sie auf PDF-Eingabedateien, die Sie an den Assembler-Dienst übergeben möchten. Wenn Sie beispielsweise zwei PDF-Eingabedateien mit dem Namen &quot;Map&quot;und &quot;Directions&quot;übergeben möchten, müssen Sie die entsprechenden PDF-Dokumente weiterleiten.

Sowohl die Datei &quot;map.pdf&quot;als auch die Datei &quot;richtungen.pdf&quot;müssen in einem Sammlungsobjekt platziert werden. Der Name des Schlüssels muss mit dem Wert des PDF-Quellattributs im DDX-Dokument übereinstimmen. Es spielt keine Rolle, welchen Namen die PDF-Datei hat, wenn Schlüssel und Quellattribut im DDX-Dokument übereinstimmen.

>[!NOTE]
>
>Ein `AssemblerResult`-Objekt, das ein Collection-Objekt enthält, wird zurückgegeben, wenn Sie den `invokeDDX`-Vorgang aufrufen. Dieser Vorgang wird verwendet, wenn Sie zwei oder mehr PDF-Eingabedateien an den Assembler-Dienst übergeben. Wenn Sie jedoch nur eine PDF-Eingabedatei an den Assembler-Dienst übergeben und nur ein Dokument erwarten, rufen Sie den Vorgang `invokeOneDocument` auf. Beim Aufrufen dieses Vorgangs wird ein einzelnes Dokument zurückgegeben. Informationen zur Verwendung dieses Vorgangs finden Sie unter [Zusammenstellen verschlüsselter PDF-Dokumente](/help/forms/developing/assembling-encrypted-pdf-documents.md#assembling-encrypted-pdf-documents).

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren. Informationen zu den verfügbaren Laufzeitoptionen finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**PDF-Eingabedateien zusammenstellen**

Nachdem Sie den Dienstclient erstellt haben, auf eine DDX-Datei verweisen, ein Sammlungsobjekt erstellen, in dem PDF-Eingabedokumente gespeichert werden, und Laufzeitoptionen festlegen, können Sie den DDX-Vorgang aufrufen. Wenn Sie das in diesem Abschnitt angegebene DDX-Dokument verwenden, werden die Dateien map.pdf und directe.pdf in einem PDF-Dokument zusammengeführt.

**Ergebnisse extrahieren**

Der Assembler-Dienst gibt ein `java.util.Map`-Objekt zurück, das vom `AssemblerResult`-Objekt abgerufen werden kann und die Vorgangsergebnisse enthält. Das zurückgegebene `java.util.Map`-Objekt enthält die resultierenden Dokumente und alle Ausnahmen.

Die folgende Tabelle fasst einige der Schlüsselwerte und Objekttypen zusammen, die sich im zurückgegebenen `java.util.Map`-Objekt befinden können.

<table>
 <thead>
  <tr>
   <th><p>Schlüsselwert</p></th>
   <th><p>Objekttyp</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p><code><i>documentName</i></code></p></td>
   <td><p><code>com.adobe.idp.Document</code></p></td>
   <td><p>Enthält die resultierenden Dokumente, die in einem DDX-Ergebniselement angegeben sind</p></td>
  </tr>
  <tr>
   <td><p><code><i>documentName</i></code></p></td>
   <td><p><code>Exception</code></p></td>
   <td><p>Enthält eine Ausnahme für das Dokument</p></td>
  </tr>
  <tr>
   <td><p><code>OutputMapConstants.LOG_NAME</code></p></td>
   <td><p><code>com.adobe.idp.Documen</code></p></td>
   <td><p>Enthält das Auftragsprotokoll</p></td>
  </tr>
 </tbody>
</table>

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmatische Demontage von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## Zusammenstellen von PDF-Dokumenten mit der Java-API {#assemble-pdf-documents-using-the-java-api}

Stellen Sie ein PDF-Dokument mithilfe der Assembler Service API (Java) zusammen:

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
   * Erstellen Sie für jedes PDF-Eingabedokument ein `java.io.FileInputStream`-Dokument, indem Sie den Konstruktor verwenden und die Position des PDF-Eingabedokuments übergeben.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.
   * Fügen Sie für jedes Eingabemaske-Dokument dem `java.util.Map`-Objekt einen Eintrag hinzu, indem Sie die `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document`-Objekt (oder `java.util.List`-Objekt, das mehrere Dokumente angibt), das das Quell-PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `setFailOnError`-Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Stellen Sie die PDF-Eingabedateien zusammen.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden erforderlichen Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das die zu assemblierenden PDF-Eingabedateien enthält
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen einschließlich der standardmäßigen Schriftart- und Auftragsprotokollebene angibt

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Rufen Sie die `AssemblerResult`-Methode des Objekts `getDocuments` auf. Gibt ein `java.util.Map`-Objekt zurück.
   * Durchlaufen Sie das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden. (Sie können das im DDX-Dokument angegebene PDF-Ergebniselement verwenden, um das Dokument abzurufen.)
   * Rufen Sie die `com.adobe.idp.Document`-Objektmethode `copyToFile` auf, um das PDF-Dokument zu extrahieren.

   >[!NOTE]
   >
   >Wenn `LOG_LEVEL` so eingestellt wurde, dass ein Protokoll erstellt wird, können Sie das Protokoll mithilfe der `AssemblerResult`-Methode des Objekts `getJobLog` extrahieren.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Zusammenstellen eines PDF-Dokuments mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenstellen von PDF-Dokumenten mit der Webdienst-API {#assemble-pdf-documents-using-the-web-service-api}

Zusammenstellen von PDF-Dokumenten mit der Assembler-Dienst-API (Webdienst):

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
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren von PDF-Dokumenten zur Eingabe.

   * Erstellen Sie für jedes PDF-Eingabedokument ein `BLOB`-Dokument mit dessen Konstruktor. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedatums und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Collection-Objekt wird zum Speichern von PDF-Eingabedokumenten verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt. Wenn beispielsweise zwei PDF-Eingabedokumente verwendet werden, erstellen Sie zwei `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekte.
   * Weisen Sie dem Feld `MyMapOf_xsd_string_To_xsd_anyType_Item` des Objekts einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. `key` Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Weisen Sie das `BLOB`-Objekt, in dem das PDF-Dokument gespeichert wird, dem `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objektfeld `value` zu. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * hinzufügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt mit dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType`-Methode des Objekts `Add` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenmember, der zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie `false` dem `AssemblerOptionSpec`-Datenmember des Objekts `failOnError` zu.

1. Stellen Sie die PDF-Eingabedateien zusammen.

   Rufen Sie die `invoke`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * Das `mapItem`-Array, das die PDF-Eingabedateien enthält. Die Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen. Die Werte müssen die `BLOB`-Objekte sein, die diesen Dateien entsprechen.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die `invoke`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und eventuell auftretende Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Greifen Sie auf das Feld `AssemblerResult` des Objekts zu, bei dem es sich um ein `Map`-Objekt handelt, das die PDF-Dokumente des Ergebnisses enthält.`documents`
   * Durchlaufen Sie das `Map`-Objekt, bis Sie den Schlüssel finden, der dem Namen des resultierenden Dokuments entspricht. Dann wird `value` des Array-Mitglieds in ein `BLOB` umgewandelt.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB`-Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine PDF-Datei schreiben können.

   >[!NOTE]
   >
   >Wenn `LOG_LEVEL` so eingestellt wurde, dass ein Protokoll erstellt wird, können Sie das Protokoll extrahieren, indem Sie den Wert des `AssemblerResult`-Datenelements des `jobLog`-Objekts abrufen.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
