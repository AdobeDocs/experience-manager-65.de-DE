---
title: Zusammenstellen verschlüsselter PDF-Dokumente
seo-title: Zusammenstellen verschlüsselter PDF-Dokumente
description: 'null'
seo-description: 'null'
uuid: d0948ec9-ab67-4fe4-9062-1c4938460b43
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 6d75c7b1-9c0e-47f3-bdb1-61acf16b97f9
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 6%

---


# Zusammenstellen verschlüsselter PDF-Dokumente {#assembling-encrypted-pdf-documents}

Sie können ein PDF-Dokument mit einem Kennwort verschlüsseln, indem Sie den Assembler-Dienst verwenden. Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, muss ein Benutzer das Kennwort angeben, damit das Dokument in Adobe Reader oder Acrobat angezeigt werden kann. Zum Verschlüsseln eines PDF-Dokuments mit einem Kennwort muss das DDX-Dokument encryption-Elementwerte enthalten, die für die Verschlüsselung eines PDF-Dokuments erforderlich sind.

Für diese Diskussion nehmen Sie an, dass das folgende DDX-Dokument verwendet wird.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
        <PDF result="EncryptLoan.pdf" encryption="userProtect">
         <PDF source="inDoc" />
     </PDF>
     <PasswordEncryptionProfile name="userProtect" compatibilityLevel="Acrobat7">
         <OpenPassword>AdobeOpen</OpenPassword>
        </PasswordEncryptionProfile>
 </DDX>
```

Beachten Sie in diesem DDX-Dokument, dass dem Quellattribut der Wert zugewiesen wurde `inDoc`. Weisen Sie in Fällen, in denen nur ein PDF-Eingabedokument an den Assembler-Dienst und ein PDF-Dokument zurückgegeben und Sie den `invokeOneDocument` Vorgang aufrufen, den Wert `inDoc` dem PDF-Quellattribut zu. Beim Aufrufen des `invokeOneDocument` Vorgangs ist der `inDoc` Wert ein vordefinierter Schlüssel, der im DDX-Dokument angegeben werden muss.

Wenn Sie dagegen zwei oder mehr PDF-Eingabedateien an den Assembler-Dienst übergeben, können Sie den `invokeDDX` Vorgang aufrufen. Weisen Sie in diesem Fall dem `source` Attribut den Dateinamen des PDF-Eingabedokuments zu.

Der Encryption-Dienst muss nicht Teil Ihrer AEM Forms-Installation sein, um ein PDF-Dokument mit einem Kennwort zu verschlüsseln. Siehe [Verschlüsseln und Entschlüsseln von PDF-Dokumenten](/help/forms/developing/encrypting-decrypting-pdf-documents.md).

>[!NOTE]
>
>For more information about the Assembler service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So assemblieren Sie ein verschlüsseltes PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen PDF Assembler-Client.
1. Verweisen Sie auf ein vorhandenes DDX-Dokument.
1. Verweisen Sie auf ein unbesichertes PDF-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Verschlüsseln Sie das Dokument.
1. Speichern Sie das verschlüsselte PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt werden, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt werden. For information about the location of all AEM Forms JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert durchführen können, müssen Sie einen Assembler-Dienstclient erstellen.

**Ein vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Zum Verschlüsseln eines PDF-Dokuments muss das DDX-Dokument das `PasswordEncryptionProfile` Element enthalten.

**Ein unbesichertes PDF-Dokument referenzieren**

Ein nicht geschütztes PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um es zu verschlüsseln. Wenn Sie auf ein bereits verschlüsseltes PDF-Dokument verweisen, wird eine Ausnahme ausgelöst.

**Festlegen von Laufzeitoptionen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, bei Auftreten eines Fehlers mit der Verarbeitung eines Auftrags fortzufahren. Informationen zu den Laufzeitoptionen, die Sie einstellen können, finden Sie in der `AssemblerOptionSpec` Klassenreferenz in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Dokument verschlüsseln**

Nachdem Sie den Assembler-Dienstclient erstellt haben, verweisen Sie auf das DDX-Dokument, das Verschlüsselungsinformationen enthält, auf ein nicht geschütztes PDF-Dokument verweisen und Laufzeitoptionen festlegen, können Sie den `invokeOneDocument` Vorgang aufrufen. Da nur ein PDF-Eingabedokument an den Assembler-Dienst übergeben wird (und ein Dokument zurückgegeben wird), können Sie den `invokeOneDocument` Vorgang anstelle des `invokeDDX` Vorgangs verwenden.

**Verschlüsseltes PDF-Dokument speichern**

Wenn nur ein einziges PDF-Dokument an den Assembler-Dienst übergeben wird, gibt der Assembler-Dienst ein einzelnes Dokument anstelle eines Collection-Objekts zurück. Das heißt, beim Aufrufen des `invokeOneDocument` Vorgangs wird ein einzelnes Dokument zurückgegeben. Da das in diesem Abschnitt referenzierte DDX-Dokument Verschlüsselungsinformationen enthält, gibt der Assembler-Dienst ein PDF-Dokument zurück, das mit einem Kennwort verschlüsselt ist.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenstellen eines verschlüsselten PDF-Dokuments mit der Java-API {#assemble-an-encrypted-pdf-document-using-the-java-api}

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-assembler-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `AssemblerServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das DDX-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf ein unbesichertes PDF-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, indem Sie den Konstruktor verwenden und die Position eines nicht geschützten PDF-Dokuments übergeben.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt und übergeben Sie das `java.io.FileInputStream` Objekt, das das PDF-Dokument enthält. Dieses `com.adobe.idp.Document` Objekt wird an die `invokeOneDocument` Methode übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` Objekt gehört. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, rufen Sie die `AssemblerOptionSpec` Methode des `setFailOnError` Objekts auf und übergeben Sie sie `false`.

1. Verschlüsseln Sie das Dokument.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeOneDocument` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` Objekt, das das DDX-Dokument darstellt. Stellen Sie sicher, dass dieses DDX-Dokument den Wert `inDoc` für das PDF-Quellelement enthält.
   * Ein `com.adobe.idp.Document` Objekt, das das ungeschützte PDF-Dokument enthält.
   * Ein `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` Objekt, das die Laufzeitoptionen einschließlich der standardmäßigen Schriftart- und Auftragsprotokollebene angibt.

   Die `invokeOneDocument` Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument.

   * Create a `java.io.File` object and ensure that the file name extension is .pdf.
   * Invoke the `Document` object’s `copyToFile` method to copy the contents of the `Document` object to the file. Stellen Sie sicher, dass Sie das `Document` Objekt verwenden, das von der `invokeOneDocument` Methode zurückgegeben wurde.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Zusammenstellen eines verschlüsselten PDF-Dokuments mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-an-encrypted-pdf-document-using-the-java-api)

## Zusammenstellen eines verschlüsselten PDF-Dokuments mit der Webdienst-API {#assemble-an-encrypted-pdf-document-using-the-web-service-api}

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `AssemblerServiceClient` Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AssemblerServiceClient.Endpoint.Address` Objekt mithilfe des `System.ServiceModel.EndpointAddress` Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `AssemblerServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. Verweisen Sie auf ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf ein unbesichertes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Dieses `BLOB` Objekt wird als `invokeOneDocument` Argument an das Objekt übergeben.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Eingabedatums und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen mithilfe des Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenmember, der zum `AssemblerOptionSpec` Objekt gehört, einen Wert zuweisen. Um beispielsweise den Assembler-Dienst anzuweisen, bei einem Fehler mit der Verarbeitung eines Auftrags fortzufahren, weisen Sie ihn `false` dem `AssemblerOptionSpec` Datenmember des `failOnError` Objekts zu.

1. Verschlüsseln Sie das Dokument.

   Rufen Sie die `AssemblerServiceClient` Objektmethode `invokeOneDocument` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` Objekt, das das DDX-Dokument darstellt
   * A `BLOB` object that represents the unsecured PDF document
   * Ein `AssemblerOptionSpec` Objekt, das Laufzeitoptionen angibt

   Die `invokeOneDocument` Methode gibt ein `BLOB` Objekt zurück, das ein verschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` Objekts speichert, das von der `invokeOneDocument` Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
