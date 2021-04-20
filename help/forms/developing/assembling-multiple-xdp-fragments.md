---
title: Zusammenstellen mehrerer XDP-Fragmente
seo-title: Zusammenstellen mehrerer XDP-Fragmente
description: Assemblieren mehrerer XDP-Fragmente in einem einzelnen XDP-Dokument mithilfe der Java API und der Web Service API.
seo-description: Assemblieren mehrerer XDP-Fragmente in einem einzelnen XDP-Dokument mithilfe der Java API und der Web Service API.
uuid: 0e35ff85-ff40-4878-ae31-aa8da75bd3ec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: c4706632-02e5-4510-ad9c-4f732d5fbdad
docset: aem65
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1909'
ht-degree: 2%

---


# Zusammenstellen mehrerer XDP-Fragmente{#assembling-multiple-xdp-fragments}

Sie können mehrere XDP-Fragmente in einem einzigen XDP-Dokument zusammenführen. Betrachten Sie beispielsweise XDP-Fragmente, bei denen jede XDP-Datei ein oder mehrere Teilformulare enthält, die zum Erstellen eines Gesundheitsformulars verwendet werden. Die folgende Abbildung zeigt die Ansicht &quot;Gliederung&quot;(entspricht der Datei &quot;tuc018_template_flow.xdp&quot;, die im Beginn *Zusammenstellen mehrerer XDP-Fragmente* verwendet wird):

![am_am_forma](assets/am_am_forma.png)

Die folgende Abbildung zeigt den Patientenabschnitt (entspricht der Datei &quot;tuc018_contact.xdp&quot;, die im Beginn *Zusammenstellen mehrerer XDP-Fragmente* verwendet wird) verwendet wird:

![am_am_formb](assets/am_am_formb.png)

Die folgende Abbildung zeigt den Abschnitt Patientengesundheit (entspricht der Datei &quot;tuc018_patient.xdp&quot;, die im Beginn *Zusammenstellen mehrerer XDP-Fragmente* verwendet wird) verwendet wird:

![am_am_formc](assets/am_am_formc.png)

Dieses Fragment enthält zwei Teilformulare mit den Namen *subPatientPhysical* und *subPatientHealth*. Beide Teilformulare werden im DDX-Dokument referenziert, das an den Assembler-Dienst übergeben wird. Mithilfe des Assembler-Dienstes können Sie alle diese XDP-Fragmente in einem einzigen XDP-Dokument kombinieren, wie in der folgenden Abbildung dargestellt.

![am_am_formd](assets/am_am_formd.png)

Im folgenden DDX-Dokument werden mehrere XDP-Fragmente in einem XDP-Dokument zusammengeführt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
         <XDP result="tuc018result.xdp">
            <XDP source="tuc018_template_flowed.xdp">
             <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/>
               <XDPContent insertionPoint="ddx_fragment" source="tuc018_patient.xdp" fragment="subPatientPhysical" required="false"/>
               <XDPContent insertionPoint="ddx_fragment" source="tuc018_patient.xdp" fragment="subPatientHealth" required="false"/>
            </XDP>
         </XDP>
 </DDX>
```

Das DDX-Dokument enthält ein XDP-Tag `result`, das den Ergebnisnamen angibt. In diesem Fall ist der Wert `tuc018result.xdp`. Dieser Wert wird in der Anwendungslogik referenziert, die zum Abrufen des XDP-Dokuments verwendet wird, nachdem der Assembler-Dienst das Ergebnis zurückgegeben hat. Betrachten Sie zum Beispiel die folgende Java-Anwendungslogik, die zum Abrufen des assemblierten XDP-Dokuments verwendet wird (beachten Sie, dass der Wert geteilt ist):

```java
 //Iterate through the map object to retrieve the result XDP document
 for (Iterator i = allDocs.entrySet().iterator(); i.hasNext();) {
     // Retrieve the Map object’s value
     Map.Entry e = (Map.Entry)i.next();
     //Get the key name as specified in the
     //DDX document
     String keyName = (String)e.getKey();
     if (keyName.equalsIgnoreCase("tuc018result.xdp"))
                 {
         Object o = e.getValue();
         outDoc = (Document)o;
         //Save the result PDF file
         File myOutFile = new File("C:\\AssemblerResultXDP.xdp");
         outDoc.copyToFile(myOutFile);
     }
 }
```

Das `XDP source`-Tag gibt die XDP-Datei an, die ein vollständiges XDP-Dokument darstellt, das als Container zum Hinzufügen von XDP-Fragmenten oder als eines von mehreren Dokumenten verwendet werden kann, die in der Reihenfolge angehängt werden. In diesem Fall wird das XDP-Dokument nur als Container verwendet (die erste Abbildung unter *Zusammenstellen mehrerer XDP-Fragmente*). Das heißt, die anderen XDP-Dateien werden innerhalb des XDP-Containers platziert.

Für jedes Teilformular können Sie ein `XDPContent`-Element hinzufügen (dieses Element ist optional). Beachten Sie im obigen Beispiel, dass es drei Teilformulare gibt: `subPatientContact`, `subPatientPhysical` und `subPatientHealth`. Sowohl das Teilformular `subPatientPhysical` als auch das Teilformular `subPatientHealth` befinden sich in derselben XDP-Datei, tuc018_patient.xdp. Das Fragment-Element gibt den Namen des Teilformulars an, wie in Designer definiert.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So assemblieren Sie mehrere XDP-Fragmente:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Verweisen Sie auf die XDP-Dokumente.
1. Legen Sie Laufzeitoptionen fest.
1. Assemblieren Sie mehrere XDP-Dokumente.
1. Abrufen des assemblierten XDP-Dokuments.

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

Ein DDX-Dokument muss referenziert werden, um mehrere XDP-Dokumente zusammenzuführen. Dieses DDX-Dokument muss die Elemente `XDP result`, `XDP source` und `XDPContent` enthalten.

**XDP-Dokumente referenzieren**

Um mehrere XDP-Dokumente zusammenzuführen, verweisen Sie auf alle XDP-Dateien, die zum Zusammenführen des XDP-Dokuments verwendet werden. Stellen Sie sicher, dass der Name des Teilformulars im XDP-Dokument, auf das das `source`-Attribut verweist, im `fragment`-Attribut angegeben ist. Ein Teilformular ist in Designer definiert. Betrachten Sie beispielsweise die folgende XML.

```xml
 <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/>
```

Das Teilformular *subPatientContact* muss sich in der XDP-Datei *tuc018_contact.xdp* befinden.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren.

**Mehrere XDP-Dokumente zusammenstellen**

Um mehrere XDP-Dateien zusammenzuführen, rufen Sie den Vorgang `invokeDDX` auf. Der Assembler-Dienst gibt das assemblierte XDP-Dokument innerhalb eines Collection-Objekts zurück.

**Abrufen des assemblierten XDP-Dokuments**

Ein assembliertes XDP-Dokument wird innerhalb eines Collection-Objekts zurückgegeben. Durchsuchen Sie das Sammlungsobjekt und speichern Sie das XDP-Dokument als XDP-Datei. Sie können das XDP-Dokument auch an einen anderen AEM Forms-Dienst, z. B. Output, übergeben.

**Siehe auch**

[Mehrere XDP-Fragmente mit der Java-API zusammenstellen](assembling-multiple-xdp-fragments.md#assemble-multiple-xdp-fragments-using-the-java-api)

[Mehrere XDP-Fragmente mithilfe der Web-Service-API zusammenstellen](assembling-multiple-xdp-fragments.md#assemble-multiple-xdp-fragments-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents)

[Erstellen von PDF-Dokumenten mit Fragmenten](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments)

## Assemblieren mehrerer XDP-Fragmente mit der Java-API {#assemble-multiple-xdp-fragments-using-the-java-api}

Stellen Sie mithilfe der Assembler Service API (Java) mehrere XDP-Fragmente zusammen:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `AssemblerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf die XDP-Dokumente.

   * Erstellen Sie ein `java.util.Map`-Objekt, das zum Speichern von Eingabe-XDP-Dokumenten mit einem `HashMap`-Konstruktor verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt und übergeben Sie das `java.io.FileInputStream`-Objekt, das die XDP-Eingabedatei enthält (wiederholen Sie diese Aufgabe für jede XDP-Datei).
   * hinzufügen Sie einen Eintrag für das `java.util.Map`-Objekt, indem Sie die `put`-Methode aufrufen und die folgenden Argumente übergeben:

      * Ein Zeichenfolgenwert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem im DDX-Dokument angegebenen Elementwert `source` übereinstimmen (Wiederholen Sie diese Aufgabe für jede XDP-Datei).
      * Ein `com.adobe.idp.Document`-Objekt, das das XDP-Dokument enthält, das dem `source`-Element entspricht (wiederholen Sie diese Aufgabe für jede XDP-Datei).

1. Legen Sie die Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec`-Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `setFailOnError`-Methode des Objekts auf und übergeben Sie `false`.`AssemblerOptionSpec`

1. Assemblieren Sie mehrere XDP-Dokumente.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden erforderlichen Werte:`AssemblerServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das zu verwendende DDX-Dokument darstellt
   * Ein `java.util.Map`-Objekt, das die XDP-Eingabedateien enthält
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschriftart und der Auftragsprotokollebene

   Die `invokeDDX`-Methode gibt ein `com.adobe.livecycle.assembler.client.AssemblerResult`-Objekt zurück, das das assemblierte XDP-Dokument enthält.

1. Abrufen des assemblierten XDP-Dokuments.

   So rufen Sie das assemblierte XDP-Dokument ab:

   * Rufen Sie die `AssemblerResult`-Methode des Objekts `getDocuments` auf. Diese Methode gibt ein `java.util.Map`-Objekt zurück.
   * Durchlaufen Sie das `java.util.Map`-Objekt, bis Sie das resultierende `com.adobe.idp.Document`-Objekt finden.
   * Rufen Sie die `com.adobe.idp.Document`-Objektmethode `copyToFile` auf, um das assemblierte XDP-Dokument zu extrahieren.

**Siehe auch**

[Assemblieren mehrerer XDP-](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)
[FragmenteQuick Beginn (SOAP-Modus): Zusammenstellen mehrerer XDP-Fragmente mit der Java ](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-multiple-xdp-fragments-using-the-java-api)
[API, einschließlich AEM Forms Java-BibliotheksdateienFestlegen ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[der Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblieren mehrerer XDP-Fragmente mit der Webdienst-API {#assemble-multiple-xdp-fragments-using-the-web-service-api}

Assemblieren mehrerer XDP-Fragmente mithilfe der Assembler Service API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden:

   ```java
    https://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst, z. B. `https://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `AssemblerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AssemblerServiceClient.ClientCredentials.UserName.Password`den entsprechenden Kennwortwert zu.
      * Weisen Sie den Konstantenwert `HttpClientCredentialType.Basic` dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`zu.
      * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode`zu.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die Stream-Länge zum Lesen.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf die XDP-Dokumente.

   * Erstellen Sie für jede Eingabe-XDP-Datei ein `BLOB`-Objekt mit dem Konstruktor. Das `BLOB`-Objekt wird zum Speichern der Eingabedatei verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort der Eingabedatei und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream`-Methode des Objekts `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die Stream-Länge zum Lesen.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Dieses Collection-Objekt wird zum Speichern von Eingabedateien verwendet, die zum Erstellen eines assemblierten XDP-Dokuments erforderlich sind.
   * Erstellen Sie für jede Eingabedatei ein `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie dem Feld `MyMapOf_xsd_string_To_xsd_anyType_Item` des Objekts einen Zeichenfolgenwert zu, der den Schlüsselnamen darstellt. `key` Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Elements übereinstimmen. (Führen Sie diese Aufgabe für jede Eingabe-XDP-Datei aus.)
   * Weisen Sie das `BLOB`-Objekt, das die Eingabedatei speichert, dem `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objektfeld `value` zu. (Führen Sie diese Aufgabe für jede Eingabe-XDP-Datei aus.)
   * hinzufügen Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt mit dem `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType`-Methode des Objekts `Add` auf und übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt. (Führen Sie diese Aufgabe für jedes Eingabe-XDP-Dokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenmember, der zum `AssemblerOptionSpec`-Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie `false` dem `AssemblerOptionSpec`-Datenmember des Objekts `failOnError` zu.

1. Assemblieren Sie mehrere XDP-Dokumente.

   Rufen Sie die `invokeDDX`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AssemblerServiceClient`

   * Ein `BLOB`-Objekt, das das DDX-Dokument darstellt
   * Das `MyMapOf_xsd_string_To_xsd_anyType`-Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec`-Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX`-Methode gibt ein `AssemblerResult`-Objekt zurück, das die Ergebnisse des Auftrags und alle aufgetretenen Ausnahmen enthält.

1. Abrufen des assemblierten XDP-Dokuments.

   So rufen Sie das neu erstellte XDP-Dokument ab:

   * Greifen Sie auf das Feld `AssemblerResult` des Objekts zu, bei dem es sich um ein `Map`-Objekt mit den resultierenden PDF-Dokumenten handelt.`documents`
   * Durchlaufen Sie das `Map`-Objekt, um jedes resultierende Dokument abzurufen. Anschließend können Sie die `value` des Array-Mitglieds in ein `BLOB`-Element umwandeln.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf die `BLOB`-Eigenschaft des Objekts `MTOM` zugreifen. Dadurch wird ein Bytearray zurückgegeben, das Sie in eine XDP-Datei schreiben können.

**Siehe auch**

[Assemblieren mehrerer XDP-](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)
[FragmenteAufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)