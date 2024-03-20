---
title: Programmatisches Zusammenstellen von PDF-Dokumenten
description: Verwenden Sie die Assembler Service-API, um mithilfe der Java-API und der Webservice-API mehrere PDF-Dokumente in einem PDF-Dokument zusammenzuführen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 7d6fd230-e477-4286-9fb3-18a3474e3e48
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2105'
ht-degree: 99%

---

# Programmatisches Zusammenstellen von PDF-Dokumenten {#programmatically-assembling-pdf-documents}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Sie können die Assembler Service-API verwenden, um mehrere PDF-Dokumente in einem PDF-Dokument zusammenzuführen. Die folgende Abbildung zeigt, wie drei PDF-Dokumente in ein einziges PDF-Dokument zusammengeführt werden.

![pa_pa_document_assembly](assets/pa_pa_document_assembly.png)

Zum Zusammenführen von zwei oder mehr PDF-Dokumenten in ein PDF-Dokument benötigen Sie ein DDX-Dokument. Ein DDX-Dokument beschreibt das PDF-Dokument, das der Assembler-Service erzeugt. Das heißt, das DDX-Dokument erteilt dem Assembler-Service Anweisungen, welche Aktionen er durchführen soll.

Nehmen Sie für dieses Thema bitte an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
     <PDF result="out.pdf">
         <PDF source="map.pdf" />
         <PDF source="directions.pdf" />
     </PDF>
 </DDX>
```

In diesem DDX-Dokument werden zwei PDF-Dokumente mit den Namen *map.pdf* und *directions.pdf* zu einem einzigen PDF-Dokument zusammengeführt.

>[!NOTE]
>
>Ein DDX-Dokument, das ein PDF-Dokument zerlegt, finden Sie unter [Programmgesteuertes Zerlegen von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents).

>[!NOTE]
>
>Weitere Informationen zum Assembler-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie in der [Assembler-Service- und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Überlegungen beim Aufrufen des Assembler-Services mithilfe von Web-Services {#considerations-when-invoking-assembler-service-using-web-services}

Wenn Sie beim Zusammenstellen großer Dokumente Kopf- und Fußzeilen hinzufügen, kann ein `OutOfMemory`-Fehler auftreten, und die Dateien werden nicht zusammengestellt. Um die Wahrscheinlichkeit zu verringern, dass dieses Problem auftritt, fügen Sie ein `DDXProcessorSetting`-Element zu Ihrem DDX-Dokument hinzu, wie im folgenden Beispiel gezeigt.

`<DDXProcessorSetting name="checkpoint" value="2000" />`

Sie können dieses Element als untergeordnetes Element des `DDX`-Elements oder als untergeordnetes Element eines `PDF result`-Elements hinzufügen. Der Standardwert für diese Einstellung ist 0 (null), wodurch das Überprüfen deaktiviert wird und sich das DDX so verhält, als ob das Element `DDXProcessorSetting` nicht vorhanden ist. Wenn ein `OutOfMemory`-Fehler aufgetreten ist, müssen Sie den Wert möglicherweise auf eine Ganzzahl festlegen, normalerweise zwischen 500 und 5000. Ein kleiner Checkpoint-Wert führt zu einem häufigeren Überprüfen.

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein einzelnes PDF-Dokument aus mehreren PDF-Dokumenten zusammenzuführen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie die PDF-Eingabedokumente.
1. Legen Sie Laufzeitoptionen fest.
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

Wenn AEM Forms auf einem unterstützten J2EE-Programm-Server bereitgestellt wird, bei dem es sich nicht um JBoss handelt, müssen Sie die Dateien „adobe-utilities.jar“ und „jbossall-client.jar“ durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Programm-Server sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines PDF-Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Client erstellen.

**Referenzieren eines bestehenden DDX-Dokuments**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Dieses DDX-Dokument weist den Assembler-Service an, zwei PDF-Dokumente in ein PDF-Dokument zusammenzuführen.

**Referenzieren der PDF-Eingabedokumente**

Referenzieren Sie die PDF-Eingabedokumente, die Sie an den Assembler-Service übergeben möchten. Wenn Sie beispielsweise zwei Eingabedokumente mit den Namen „Map“ und „Directions“ übergeben möchten, müssen Sie die entsprechenden PDF-Dateien übergeben.

Sowohl die Datei „map.pdf“ als auch die Datei „directions.pdf“ müssen in einem Sammlungsobjekt platziert werden. Der Name des Schlüssels muss mit dem Wert des PDF-Quellattributs im DDX-Dokument übereinstimmen. Es spielt keine Rolle, wie der Name der PDF-Datei lautet, wenn der Schlüssel und das Quellattribut im DDX-Dokument übereinstimmen.

>[!NOTE]
>
>Ein `AssemblerResult`-Objekt, das ein Sammlungsobjekt enthält, wird zurückgegeben, wenn Sie den Vorgang `invokeDDX` aufrufen. Dieser Vorgang wird verwendet, wenn Sie zwei oder mehr PDF-Eingabedokumente an den Assembler-Service übergeben. Wenn Sie jedoch nur eine einzige Eingabe-PDF an den Assembler-Service übergeben und nur ein Rückgabedokument erwarten, rufen Sie den Vorgang `invokeOneDocument` auf. Beim Aufrufen dieses Vorgangs wird ein einzelnes Dokument zurückgegeben. Weitere Informationen zur Verwendung dieses Vorgangs finden Sie unter [Zusammenstellen verschlüsselter PDF-Dokumente](/help/forms/developing/assembling-encrypted-pdf-documents.md#assembling-encrypted-pdf-documents).

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Services während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Service angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Weitere Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie in der `AssemblerOptionSpec`-Klassenreferenz in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Zusammenstellen der PDF-Eingabedokumente**

Nachdem Sie den Service-Client erstellt, eine DDX-Datei referenziert, ein Auflistungsobjekt zum Speichern von Eingabe-PDF-Dokumenten erstellt und Laufzeitoptionen festgelegt haben, können Sie den DDX-Vorgang aufrufen. Wenn Sie das in diesem Abschnitt angegebene DDX-Dokument verwenden, werden die Dateien „map.pdf“ und „direction.pdf“ in einem PDF-Dokument zusammengeführt.

**Extrahieren der Ergebnisse**

Der Assembler-Service gibt ein `java.util.Map`-Objekt zurück, das vom `AssemblerResult`-Objekt abgerufen werden kann und Vorgangsergebnisse enthält. Das zurückgegebene `java.util.Map`-Objekt enthält die resultierenden Dokumente und alle Ausnahmen.

Die folgende Tabelle fasst einige der Schlüsselwerte und Objekttypen zusammen, die in der zurückgegebenen `java.util.Map` -Objekt.

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
   <td><p>Enthält alle Ausnahmen für das Dokument</p></td>
  </tr>
  <tr>
   <td><p><code>OutputMapConstants.LOG_NAME</code></p></td>
   <td><p><code>com.adobe.idp.Documen</code></p></td>
   <td><p>Enthält das Vorgangslog</p></td>
  </tr>
 </tbody>
</table>

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuerte Aufteilung von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## Zusammenführen von PDF-Dokumenten mithilfe der Java-API {#assemble-pdf-documents-using-the-java-api}

Zusammenführen eines PDF-Dokuments mithilfe der Assembler Service API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-assembler-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie die PDF-Eingabedokumente.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von Eingabe-PDF-Dokumenten mithilfe eines `HashMap`-Konstruktors verwendet wird.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `java.io.FileInputStream`-Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des PDF-Eingabedokuments übergeben.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das das PDF-Dokument enthält.
   * Fügen Sie für jedes Eingabedokument einen Eintrag zum `java.util.Map`-Objekt hinzu, indem Sie dessen `put`-Methode verwenden und die folgenden Argumente übergeben:

      * Eine Zeichenfolge, die den Speichernamen repräsentiert. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * Ein `com.adobe.idp.Document`-Objekt (oder `java.util.List`-Objekt, das mehrere Dokumente angibt), das das PDF-Quelldokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags im Falle eines Fehlers fortzusetzen, rufen Sie die Methode `setFailOnError` des `AssemblerOptionSpec`-Objekts auf und übergeben Sie `false`.

1. Stellen Sie die PDF-Eingabedokumente zusammen.

   Rufen Sie die Methode `invokeDDX` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden erforderlichen Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das die PDF-Eingabedateien enthält, die zusammengeführt werden sollen
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich standardmäßiger Schriftart und Vorgangslog-Ebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das die Ergebnisse des Vorgangs sowie alle aufgetretenen Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die `AssemblerResult`-Objekt`getDocuments`-Methode auf. Dadurch wird ein `java.util.Map`-Objekt zurückgegeben.
   * Durchsuchen Sie das `java.util.Map`-Objekt, bis Sie das entstandene `com.adobe.idp.Document`-Objekt gefunden haben. (Sie können das im DDX-Dokument angegebene PDF-Ergebniselement verwenden, um das Dokument abzurufen.)
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um das PDF-Dokument zu extrahieren.

   >[!NOTE]
   >
   >Wenn `LOG_LEVEL` eingestellt wurde, um ein Protokoll zu erstellen, können Sie das Protokoll mithilfe der Methode `getJobLog` des `AssemblerResult`-Objekts extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): Zusammenstellen eines PDF-Dokuments mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenführen von PDF-Dokumenten mithilfe der Web-Service-API {#assemble-pdf-documents-using-the-web-service-api}

Zusammenführen von PDF-Dokumenten mithilfe der Assembler Service API (Web-Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

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
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekt gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt mit den Inhalten des Byte-Arrays, indem Sie seine `MTOM`-Eigenschaft zuweisen.

1. Referenzieren Sie die PDF-Eingabedokumente.

   * Erstellen Sie für jedes PDF-Eingabedokument ein `BLOB`-Objekt, indem Sie seinen Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des PDF-Eingabedokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt mit den Inhalten des Byte-Arrays, indem Sie sein `MTOM`-Feld zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Sammlungsobjekt wird zum Speichern von PDF-Eingabedokumenten verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt. Wenn beispielsweise zwei PDF-Eingabedokumente verwendet werden, erstellen Sie zwei `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekte.
   * Weisen Sie dem Feld `key` des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Weisen Sie das `BLOB`-Objekt, das das PDF-Dokument speichert, dem Feld `value` des `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekts zu. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Fügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt zum `MyMapOf_xsd_string_To_xsd_anyType`-Objekt hinzu. Rufen Sie die Methode `Add` des `MyMapOf_xsd_string_To_xsd_anyType`-Objekts auf, und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen speichert, indem Sie seinen Konstruktor verwenden.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement, das zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Service anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie dem Datenelement `failOnError` des `AssemblerOptionSpec`-Objekts `false` zu.

1. Stellen Sie die PDF-Eingabedokumente zusammen.

   Rufen Sie die Methode `invoke` des `AssemblerServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt.
   * Das `mapItem`-Array, das die PDF-Eingabedokumente enthält. Seine Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und seine Werte müssen die `BLOB`-Objekte sein, die diesen Dateien entsprechen.
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt.

   Die Methode `invoke` gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Vorgangs und eventuell aufgetretene Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Greifen Sie auf das Feld `documents` des `AssemblerResult`-Objekts zu, das ein `Map`-Objekt ist, welches die PDF-Ergebnisdokumente enthält.
   * Iterieren Sie durch das `Map`-Objekt, bis Sie den Schlüssel finden, der dem Namen des Ergebnisdokuments entspricht. Dann wandeln Sie das `value` dieses Array-Elements in ein `BLOB` um.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `MTOM`-Eigenschaft seines `BLOB`-Objekts zugreifen. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

   >[!NOTE]
   >
   >Wenn `LOG_LEVEL` für die Erstellung eines Protokolls eingestellt wurde, können Sie das Protokoll extrahieren, indem Sie den Wert des Datenelements `jobLog` des `AssemblerResult`-Objekts abrufen.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
