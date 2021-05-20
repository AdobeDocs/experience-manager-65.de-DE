---
title: Verschlüsseln und Entschlüsseln von PDF-Dokumenten
seo-title: Verschlüsseln und Entschlüsseln von PDF-Dokumenten
description: Verwenden Sie den Encryption-Dienst zum Verschlüsseln und Entschlüsseln von Dokumenten. Zu den Aufgaben des Verschlüsselungsdienstes gehören das Verschlüsseln eines PDF-Dokuments mit einem Kennwort, das Verschlüsseln eines PDF-Dokuments mit einem Zertifikat, das Entfernen der kennwortbasierten Verschlüsselung von einem PDF-Dokument, das Entfernen der zertifikatbasierten Verschlüsselung von einem PDF-Dokument, das Entsperren des PDF-Dokuments, sodass andere Dienstvorgänge ausgeführt werden können, und das Ermitteln des Verschlüsselungstyps eines gesicherten PDF-Dokuments.
seo-description: Verwenden Sie den Encryption-Dienst zum Verschlüsseln und Entschlüsseln von Dokumenten. Zu den Aufgaben des Verschlüsselungsdienstes gehören das Verschlüsseln eines PDF-Dokuments mit einem Kennwort, das Verschlüsseln eines PDF-Dokuments mit einem Zertifikat, das Entfernen der kennwortbasierten Verschlüsselung von einem PDF-Dokument, das Entfernen der zertifikatbasierten Verschlüsselung von einem PDF-Dokument, das Entsperren des PDF-Dokuments, sodass andere Dienstvorgänge ausgeführt werden können, und das Ermitteln des Verschlüsselungstyps eines gesicherten PDF-Dokuments.
uuid: 4e4e2716-c21f-4bfe-ae7a-7e91442414ef
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 5e4bda3a-5648-4c0f-b2f8-bdbebb88f537
role: Developer
exl-id: d3cbca7f-9277-4d61-b198-abf4bb008f15
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '8258'
ht-degree: 8%

---

# Verschlüsseln und Entschlüsseln von PDF-Dokumenten {#encrypting-and-decrypting-pdf-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

**Über den Encryption-Dienst**

Mit dem Encryption-Dienst können Sie Dokumente verschlüsseln und entschlüsseln. Wird ein Dokument verschlüsselt, ist sein Inhalt nicht mehr lesbar. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf den Inhalt zu erhalten. Wenn ein PDF-Dokument mit einem Kennwort verschlüsselt wird, muss der Benutzer das Kennwort zum Öffnen angeben, damit das Dokument in Adobe Reader oder Adobe angezeigt werden kann. Ähnlich muss der Benutzer, wenn ein PDF-Dokument mit einem Zertifikat verschlüsselt ist, das PDF-Dokument mithilfe des öffentlichen Schlüssels entschlüsseln, der dem Zertifikat (privater Schlüssel) entspricht, das zum Verschlüsseln des PDF-Dokuments verwendet wurde.

Sie können diese Aufgaben mithilfe des Encryption-Dienstes ausführen:

* Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)
* Verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat. (Siehe [Verschlüsseln von PDF-Dokumenten mit Zertifikaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).)
* Entfernen Sie die kennwortbasierte Verschlüsselung von einem PDF-Dokument. (Siehe [Entfernen der Kennwortverschlüsselung](encrypting-decrypting-pdf-documents.md#removing-password-encryption).)
* Entfernen Sie die zertifikatbasierte Verschlüsselung von einem PDF-Dokument. (Siehe [Entfernen der zertifikatbasierten Verschlüsselung](encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).)
* Entsperren Sie das PDF-Dokument, damit andere Dienstvorgänge ausgeführt werden können. Nachdem beispielsweise ein kennwortverschlüsseltes PDF-Dokument entsperrt wurde, können Sie eine digitale Signatur darauf anwenden. (Siehe [Entsperren verschlüsselter PDF-Dokumente](encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents).)
* Ermitteln Sie den Verschlüsselungstyp eines gesicherten PDF-Dokuments. (Siehe [Bestimmen des Verschlüsselungstyps](encrypting-decrypting-pdf-documents.md#determining-encryption-type).)

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Verschlüsseln von PDF-Dokumenten mit einem Kennwort {#encrypting-pdf-documents-with-a-password}

Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, muss ein Benutzer das Kennwort angeben, damit das Dokument in Adobe Reader oder Acrobat geöffnet werden kann. Bevor ein anderer AEM Forms-Vorgang wie das digitale Signieren des PDF-Dokuments für das Dokument ausgeführt werden kann, muss die Sperre eines kennwortverschlüsselten PDF-Dokuments aufgehoben werden.

>[!NOTE]
>
>Wenn Sie ein verschlüsseltes PDF-Dokument in das AEM Forms-Repository hochladen, kann es das PDF-Dokument nicht entschlüsseln und den XDP-Inhalt extrahieren. Es wird empfohlen, ein Dokument nicht vor dem Hochladen in das AEM Forms-Repository zu verschlüsseln. (Siehe [Schreibressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument mit einem Kennwort zu verschlüsseln, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Encryption Client-API-Objekt.
1. PDF-Dokument zum Verschlüsseln abrufen.
1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.
1. Fügen Sie das Kennwort hinzu.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Client-API-Objekts**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen.

**PDF-Dokument zum Verschlüsseln abrufen**

Sie müssen ein unverschlüsseltes PDF-Dokument abrufen, um das Dokument mit einem Kennwort zu verschlüsseln. Wenn Sie versuchen, ein bereits verschlüsseltes PDF-Dokument zu schützen, wird eine Ausnahme ausgelöst.

**Laufzeitoptionen für Verschlüsselung festlegen**

Um ein PDF-Dokument mit einem Kennwort zu verschlüsseln, geben Sie vier Werte an, darunter zwei Kennwortwerte. Der erste Kennwortwert wird zum Verschlüsseln des PDF-Dokuments verwendet und muss beim Öffnen des PDF-Dokuments angegeben werden. Der zweite Kennwortwert, der als Übergeordneter Kennwortwert bezeichnet wird, wird zum Entfernen der Verschlüsselung aus dem PDF-Dokument verwendet. Bei Kennwortwerten wird zwischen Groß- und Kleinschreibung unterschieden. Diese beiden Kennwortwerte dürfen nicht dieselben Werte sein.

Sie müssen die zu verschlüsselnden PDF-Dokumentressourcen angeben. Sie können das gesamte PDF-Dokument verschlüsseln, alles außer den Metadaten des Dokuments oder nur die Anlagen des Dokuments. Wenn Sie nur die Anlagen des Dokuments verschlüsseln, wird ein Benutzer beim Versuch, auf die Dateianlagen zuzugreifen, nach einem Kennwort aufgefordert.

Beim Verschlüsseln eines PDF-Dokuments können Sie Berechtigungen angeben, die mit dem gesicherten Dokument verknüpft sind. Durch Festlegen von Berechtigungen können Sie steuern, welche Aktionen ein Benutzer ausführen darf, der ein kennwortverschlüsseltes PDF-Dokument öffnet. Zum erfolgreichen Extrahieren von Formulardaten müssen Sie beispielsweise die folgenden Berechtigungen festlegen:

* PASSWORD_EDIT_ADD
* PASSWORD_EDIT_MODIFY

>[!NOTE]
>
>Berechtigungen werden als Auflistungswerte `PasswordEncryptionPermission` angegeben.

**Passwort hinzufügen**

Nachdem Sie ein ungesichertes PDF-Dokument abgerufen und die Verschlüsselungs-Laufzeitwerte festgelegt haben, können Sie dem PDF-Dokument ein Kennwort hinzufügen.

**Das verschlüsselte PDF-Dokument als PDF-Datei speichern**

Sie können das kennwortverschlüsselte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Verschlüsseln eines PDF-Dokuments mit der Java-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-using-the-java-api)

[Verschlüsseln eines PDF-Dokuments mit der Webdienst-API](encrypting-decrypting-pdf-documents.md#encrypting-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit Zertifikaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates)

### Verschlüsseln eines PDF-Dokuments mit der Java-API {#encrypt-a-pdf-document-using-the-java-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort mithilfe der Verschlüsselungs-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie eine Verschlüsselungs-Client-API.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. PDF-Dokument zum Verschlüsseln abrufen.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu verschlüsselnde PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein `PasswordEncryptionOptionSpec` -Objekt, indem Sie seinen Konstruktor aufrufen.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie die `setEncryptOption`-Methode des Objekts `PasswordEncryptionOptionSpec` aufrufen und einen `PasswordEncryptionOption`-Auflistungswert übergeben, der die zu verschlüsselnden Dokumentressourcen angibt. Um beispielsweise das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, geben Sie `PasswordEncryptionOption.ALL` an.
   * Erstellen Sie ein `java.util.List` -Objekt, das die Verschlüsselungsberechtigungen mithilfe des Konstruktors `ArrayList` speichert.
   * Geben Sie eine Berechtigung an, indem Sie die Methode `java.util.List` des Objekts &quot;s `add` aufrufen und einen Auflistungswert übergeben, der der gewünschten Berechtigung entspricht. Um beispielsweise die Berechtigung festzulegen, mit der ein Benutzer Daten im PDF-Dokument kopieren kann, geben Sie `PasswordEncryptionPermission.PASSWORD_EDIT_COPY` an. (Wiederholen Sie diesen Schritt für jede festzulegende Berechtigung.)
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie die `setCompatability` -Methode des Objekts `PasswordEncryptionOptionSpec` aufrufen und einen Auflistungswert übergeben, der die Acrobat-Kompatibilitätsstufe angibt. Sie können beispielsweise `PasswordEncryptionCompatability.ACRO_7` angeben.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer das verschlüsselte PDF-Dokument öffnen kann, indem die `setDocumentOpenPassword` -Methode des Objekts `PasswordEncryptionOptionSpec` aufgerufen und ein string -Wert übergeben wird, der das offene Kennwort darstellt.
   * Geben Sie den Übergeordneten Kennwortwert an, mit dem ein Benutzer die Verschlüsselung aus dem PDF-Dokument entfernen kann, indem er die `setPermissionPassword` -Methode des Objekts aufruft und einen string -Wert übergibt, der das Übergeordnete Kennwort darstellt.`PasswordEncryptionOptionSpec`

1. Fügen Sie das Kennwort hinzu.

   Verschlüsseln Sie das PDF-Dokument, indem Sie die `encryptPDFUsingPassword` -Methode des Objekts `EncryptionServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält, das mit dem Kennwort verschlüsselt werden soll.
   * Das `PasswordEncryptionOptionSpec`-Objekt, das Verschlüsselungs-Laufzeitoptionen enthält.

   Die `encryptPDFUsingPassword`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `encryptPDFUsingPassword`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verschlüsseln eines PDF-Dokuments mit der Webdienst-API {#encrypting-a-pdf-document-using-the-web-service-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie ein `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument zum Verschlüsseln abrufen.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines mit einem Kennwort verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB` -Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB` -Datenelement des `MTOM` -Objekts zuweisen.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein Objekt `PasswordEncryptionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie dem `encryptOption`-Datenelement des Objekts `PasswordEncryptionOptionSpec` einen `PasswordEncryptionOption`-Auflistungswert zuweisen. Um die gesamte PDF-Datei einschließlich der Metadaten und Anlagen zu verschlüsseln, weisen Sie `PasswordEncryptionOption.ALL` diesem Datenelement zu.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie dem `compatability`-Datenelement des `PasswordEncryptionOptionSpec`-Objekts einen Auflistungswert `PasswordEncryptionCompatability` zuweisen. Weisen Sie diesem Datenelement beispielsweise `PasswordEncryptionCompatability.ACRO_7` zu.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer das verschlüsselte PDF-Dokument öffnen kann, indem Sie dem `documentOpenPassword`-Datenelement des Objekts `PasswordEncryptionOptionSpec` einen string -Wert zuweisen, der das offene Kennwort darstellt.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer die Verschlüsselung aus dem PDF-Dokument entfernen kann, indem Sie dem `permissionPassword`-Datenelement des `PasswordEncryptionOptionSpec`-Objekts einen Zeichenfolgenwert zuweisen, der das Übergeordnete Kennwort darstellt.

1. Fügen Sie das Kennwort hinzu.

   Verschlüsseln Sie das PDF-Dokument, indem Sie die `encryptPDFUsingPassword` -Methode des Objekts `EncryptionServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Dokument enthält, das mit dem Kennwort verschlüsselt werden soll.
   * Das `PasswordEncryptionOptionSpec`-Objekt, das Verschlüsselungs-Laufzeitoptionen enthält.

   Die `encryptPDFUsingPassword`-Methode gibt ein `BLOB`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `encryptPDFUsingPassword` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Verschlüsseln von PDF-Dokumenten mit Zertifikaten {#encrypting-pdf-documents-with-certificates}

Zertifikatbasierte Verschlüsselung ermöglicht die Verschlüsselung eines Dokuments für bestimmte Empfänger mithilfe von Technologien mit öffentlichem Schlüssel. Verschiedene Empfänger können unterschiedliche Berechtigungen für das Dokument erhalten. Viele Aspekte der Verschlüsselung werden durch die Technologie öffentlicher Schlüssel möglich gemacht. Ein Algorithmus wird verwendet, um zwei große Zahlen zu generieren, die als *Schlüssel* bezeichnet werden und die die folgenden Eigenschaften aufweisen:

* Ein Schlüssel wird zum Verschlüsseln eines Satzes von Daten verwendet. Danach kann nur der andere Schlüssel zum Entschlüsseln der Daten verwendet werden.
* Es ist unmöglich, einen Schlüssel vom anderen zu unterscheiden.

Einer der Schlüssel dient als privater Schlüssel des Benutzers. Wichtig ist, dass nur der Benutzer Zugriff auf diesen Schlüssel hat. Der andere Schlüssel ist der öffentliche Schlüssel des Benutzers, der für andere freigegeben werden kann.

Ein Zertifikat mit öffentlichem Schlüssel enthält den öffentlichen Schlüssel eines Benutzers und Identifizierungsinformationen. Das X.509-Format dient zum Speichern von Zertifikaten. Zertifikate werden meist von einer Zertifizierungsstelle ausgestellt und digital signiert, bei der es sich um eine anerkannte Instanz handelt, die ein Maß an Vertrauen in die Gültigkeit des Zertifikats ermöglicht. Zertifikate haben ein Ablaufdatum, nach dem sie nicht mehr gültig sind. Darüber hinaus liefern Zertifikatsperrlisten Informationen zu Zertifikaten, die vor ihrem Ablaufdatum gesperrt wurden. Zertifikatsperrlisten werden regelmäßig von Zertifizierungsstellen veröffentlicht. Der Sperrstatus eines Zertifikats kann auch mittels des Online-Zertifikatstatusprotokolls (Online Certificate Status Protocol, OCSP) über das Netzwerk abgerufen werden.

>[!NOTE]
>
>Wenn Sie ein verschlüsseltes PDF-Dokument in das AEM Forms-Repository hochladen, kann es das PDF-Dokument nicht entschlüsseln und den XDP-Inhalt extrahieren. Es wird empfohlen, ein Dokument nicht vor dem Hochladen in das AEM Forms-Repository zu verschlüsseln. (Siehe [Schreibressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument mit einem Zertifikat verschlüsseln können, müssen Sie sicherstellen, dass Sie das Zertifikat zu AEM Forms hinzufügen. Ein Zertifikat wird über Administration Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Importing Credentials by using the Trust Manager API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um ein PDF-Dokument mit einem Zertifikat zu verschlüsseln, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Encryption Client-API-Objekt.
1. PDF-Dokument zum Verschlüsseln abrufen.
1. Referenzieren Sie das Zertifikat.
1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.
1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Client-API-Objekts**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient` -Objekt. Wenn Sie die Web Service Encryption Service-API verwenden, erstellen Sie ein `EncryptionServiceService` -Objekt.

**PDF-Dokument zum Verschlüsseln abrufen**

Sie müssen zum Verschlüsseln ein unverschlüsseltes PDF-Dokument abrufen. Wenn Sie versuchen, ein bereits verschlüsseltes PDF-Dokument zu schützen, wird eine Ausnahme ausgelöst.

**Referenzieren des Zertifikats**

Um ein PDF-Dokument mit einem Zertifikat zu verschlüsseln, verweisen Sie auf ein Zertifikat, das zum Verschlüsseln eines PDF-Dokuments verwendet wird. Das Zertifikat ist eine .cer-Datei, eine .crt-Datei oder eine .pem-Datei. Eine PKCS#12-Datei wird verwendet, um private Schlüssel mit entsprechenden Zertifikaten zu speichern.

Geben Sie beim Verschlüsseln eines PDF-Dokuments mit einem Zertifikat die Berechtigungen an, die mit dem gesicherten Dokument verknüpft sind. Durch Festlegen von Berechtigungen können Sie steuern, welche Aktionen ein Benutzer ausführen kann, der ein zertifikatverschlüsseltes PDF-Dokument öffnet.

**Laufzeitoptionen für Verschlüsselung festlegen**

Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an. Sie können das gesamte PDF-Dokument verschlüsseln, alles außer den Metadaten des Dokuments oder nur die Anlagen des Dokuments.

**Zertifikatverschlüsseltes PDF-Dokument erstellen**

Nachdem Sie ein ungesichertes PDF-Dokument abgerufen, auf das Zertifikat verwiesen und Laufzeitoptionen festgelegt haben, können Sie ein zertifikatverschlüsseltes PDF-Dokument erstellen. Nachdem das PDF-Dokument verschlüsselt wurde, benötigen Sie den entsprechenden öffentlichen Schlüssel zum Entschlüsseln.

**Das verschlüsselte PDF-Dokument als PDF-Datei speichern**

Sie können das verschlüsselte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-java-api)

[Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Webdienst-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API {#encrypt-a-pdf-document-with-a-certificate-using-the-java-api}

Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Verschlüsselungs-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. PDF-Dokument zum Verschlüsseln abrufen.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu verschlüsselnde PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie das Zertifikat.

   * Erstellen Sie ein `java.util.List` -Objekt, das Berechtigungsinformationen mithilfe des zugehörigen Konstruktors speichert.
   * Geben Sie die mit dem verschlüsselten Dokument verknüpfte Berechtigung an, indem Sie die `add` -Methode des Objekts `java.util.List` aufrufen und einen `CertificateEncryptionPermissions` -Auflistungswert übergeben, der die Berechtigungen darstellt, die dem Benutzer erteilt werden, der das geschützte PDF-Dokument öffnet. Um beispielsweise alle Berechtigungen anzugeben, übergeben Sie `CertificateEncryptionPermissions.PKI_ALL_PERM`.
   * Erstellen Sie ein Objekt `Recipient`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das Zertifikat darstellt, das zum Verschlüsseln des PDF-Dokuments verwendet wird, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des Zertifikats angibt.
   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream` -Objekt übergeben, das das Zertifikat darstellt.
   * Rufen Sie die `setX509Cert` -Methode des Objekts `Recipient` auf und übergeben Sie das `com.adobe.idp.Document` -Objekt, das das Zertifikat enthält. (Darüber hinaus kann das `Recipient`Objekt einen Truststore-Zertifikatalias oder eine LDAP-URL als Zertifikatquelle haben.)
   * Erstellen Sie ein `CertificateEncryptionIdentity` -Objekt, das Berechtigungen und Zertifikatinformationen mithilfe des zugehörigen Konstruktors speichert.
   * Rufen Sie die `setPerms` -Methode des Objekts `CertificateEncryptionIdentity` auf und übergeben Sie das `java.util.List` -Objekt, das Berechtigungsinformationen speichert.
   * Rufen Sie die `setRecipient` -Methode des Objekts `CertificateEncryptionIdentity` auf und übergeben Sie das `Recipient` -Objekt, das Zertifikatinformationen speichert.
   * Erstellen Sie ein `java.util.List` -Objekt, das Zertifikatinformationen mithilfe des zugehörigen Konstruktors speichert.
   * Rufen Sie die Methode add des Objekts `java.util.List` auf und übergeben Sie das Objekt `CertificateEncryptionIdentity` . (Dieses `java.util.List`-Objekt wird als Parameter an die `encryptPDFUsingCertificates`-Methode übergeben.)

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein `CertificateEncryptionOptionSpec` -Objekt, indem Sie seinen Konstruktor aufrufen.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie die `setOption`-Methode des Objekts `CertificateEncryptionOptionSpec` aufrufen und einen `CertificateEncryptionOption`-Auflistungswert übergeben, der die zu verschlüsselnden Dokumentressourcen angibt. Um beispielsweise das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, geben Sie `CertificateEncryptionOption.ALL` an.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie die `setCompat` -Methode des Objekts `CertificateEncryptionOptionSpec` aufrufen und einen `CertificateEncryptionCompatibility` -Auflistungswert übergeben, der die Acrobat-Kompatibilitätsstufe angibt. Sie können beispielsweise `CertificateEncryptionCompatibility.ACRO_7` angeben.

1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.

   Verschlüsseln Sie das PDF-Dokument mit einem Zertifikat, indem Sie die `encryptPDFUsingCertificates` -Methode des Objekts `EncryptionServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das zu verschlüsselnde PDF-Dokument enthält.
   * Das `java.util.List`-Objekt, das Zertifikatinformationen speichert.
   * Das `CertificateEncryptionOptionSpec`-Objekt, das Verschlüsselungs-Laufzeitoptionen enthält.

   Die `encryptPDFUsingCertificates`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein zertifikatverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `encryptPDFUsingCertificates`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Webdienst-API {#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie ein `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument zum Verschlüsseln abrufen.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines mit einem Zertifikat verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie das Zertifikat.

   * Erstellen Sie ein Objekt `Recipient`, indem Sie den Konstruktor verwenden. Dieses Objekt speichert Zertifikatinformationen.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt speichert das Zertifikat, das das PDF-Dokument verschlüsselt.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des Zertifikats und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB` -Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB` -Datenelement des `MTOM` -Objekts zuweisen.
   * Weisen Sie das `BLOB`-Objekt zu, das das Zertifikat speichert, dem `x509Cert`-Datenelement des `Recipient`-Objekts zu.
   * Erstellen Sie ein `CertificateEncryptionIdentity` -Objekt, das Zertifikatinformationen mithilfe des zugehörigen Konstruktors speichert.
   * Weisen Sie das `Recipient`-Objekt zu, das das Zertifikat speichert, dem Mitglied der Empfängerdaten des Objekts `CertificateEncryptionIdentity`zu.
   * Erstellen Sie ein `Object`-Array und weisen Sie das `CertificateEncryptionIdentity`-Objekt dem ersten Element des `Object`-Arrays zu. Dieses `Object`-Array wird als Parameter an die `encryptPDFUsingCertificates`-Methode übergeben.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein Objekt `CertificateEncryptionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie dem `option`-Datenelement des Objekts `CertificateEncryptionOptionSpec` einen `CertificateEncryptionOption`-Auflistungswert zuweisen. Um das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, weisen Sie diesem Datenelement `CertificateEncryptionOption.ALL` zu.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie dem `compat`-Datenelement des `CertificateEncryptionOptionSpec`-Objekts einen Auflistungswert `CertificateEncryptionCompatibility` zuweisen. Weisen Sie diesem Datenelement beispielsweise `CertificateEncryptionCompatibility.ACRO_7` zu.

1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.

   Verschlüsseln Sie das PDF-Dokument mit einem Zertifikat, indem Sie die `encryptPDFUsingCertificates` -Methode des Objekts `EncryptionServiceService` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das zu verschlüsselnde PDF-Dokument enthält.
   * Das `Object`-Array, das Zertifikatinformationen speichert.
   * Das `CertificateEncryptionOptionSpec`-Objekt, das Verschlüsselungs-Laufzeitoptionen enthält.

   Die `encryptPDFUsingCertificates`-Methode gibt ein `BLOB`-Objekt zurück, das ein zertifikatverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `encryptPDFUsingCertificates` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen der zertifikatbasierten Verschlüsselung {#removing-certificate-based-encryption}

Zertifikatbasierte Verschlüsselung kann aus einem PDF-Dokument entfernt werden, damit Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können. Um die Verschlüsselung von einem PDF-Dokument zu entfernen, das mit einem Zertifikat verschlüsselt ist, muss auf einen öffentlichen Schlüssel verwiesen werden. Nachdem die Verschlüsselung aus einem PDF-Dokument entfernt wurde, ist es nicht mehr sicher.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Schritte aus, um die zertifikatbasierte Verschlüsselung von einem PDF-Dokument zu entfernen:

1. Projektdateien einschließen.
1. Erstellen Sie einen Verschlüsselungsdienst-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entfernen Sie die Verschlüsselung.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient` -Objekt. Wenn Sie die Web Service Encryption Service-API verwenden, erstellen Sie ein `EncryptionServiceService` -Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um die zertifikatbasierte Verschlüsselung zu entfernen. Wenn Sie versuchen, die Verschlüsselung von einem nicht verschlüsselten PDF-Dokument zu entfernen, wird eine Ausnahme ausgelöst. Wenn Sie versuchen, die zertifikatbasierte Verschlüsselung aus einem kennwortverschlüsselten Dokument zu entfernen, wird eine Ausnahme ausgelöst.

**Verschlüsselung entfernen**

Zum Entfernen der zertifikatbasierten Verschlüsselung von einem verschlüsselten PDF-Dokument benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch den privaten Schlüssel, der dem Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wurde. Der Aliaswert des privaten Schlüssels wird beim Entfernen der zertifikatbasierten Verschlüsselung von einem verschlüsselten PDF-Dokument angegeben. Informationen zum öffentlichen Schlüssel finden Sie unter [Verschlüsseln von PDF-Dokumenten mit Zertifikaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).

>[!NOTE]
>
>Ein privater Schlüssel wird im AEM Forms Trust Store gespeichert. Wenn dort ein Zertifikat platziert wird, wird ein Alias-Wert angegeben.

**PDF-Dokument speichern**

Nachdem die zertifikatbasierte Verschlüsselung aus einem verschlüsselten PDF-Dokument entfernt wurde, können Sie das PDF-Dokument als PDF-Datei speichern. Benutzer können das PDF-Dokument in Adobe Reader oder Acrobat öffnen.

**Siehe auch**

[Zertifikatbasierte Verschlüsselung mit der Java-API entfernen](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-java-api)

[Zertifikatbasierte Verschlüsselung mithilfe der Webdienst-API entfernen](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Zertifikatbasierte Verschlüsselung mit der Java-API {#remove-certificate-based-encryption-using-the-java-api} entfernen

Entfernen Sie die zertifikatbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Java) aus einem PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des verschlüsselten PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie die Verschlüsselung.

   Entfernen Sie die zertifikatbasierte Verschlüsselung aus dem PDF-Dokument, indem Sie die `removePDFCertificateSecurity` -Methode des Objekts `EncryptionServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das verschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Aliasnamen des privaten Schlüssels angibt, der dem zum Verschlüsseln des PDF-Dokuments verwendeten Schlüssel entspricht.

   Die `removePDFCertificateSecurity`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein ungesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `removePDFCredentialSecurity`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Zertifikatbasierte Verschlüsselung mithilfe der Java-API entfernen](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zertifikatbasierte Verschlüsselung mithilfe der Webdienst-API {#remove-certificate-based-encryption-using-the-web-service-api} entfernen

Entfernen Sie die zertifikatbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB` -Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB` -Datenelement des `MTOM` -Objekts zuweisen.

1. Entfernen Sie die Verschlüsselung.

   Rufen Sie die `removePDFCertificateSecurity` -Methode des Objekts `EncryptionServiceClient` auf und übergeben Sie die folgenden Werte:

   * Das `BLOB`-Objekt, das Datei-Stream-Daten enthält, die ein verschlüsseltes PDF-Dokument darstellen.
   * Ein string -Wert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wird.

   Die `removePDFCredentialSecurity`-Methode gibt ein `BLOB`-Objekt zurück, das ein ungesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `removePDFPasswordSecurity` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen der Kennwortverschlüsselung {#removing-password-encryption}

Die kennwortbasierte Verschlüsselung kann aus einem PDF-Dokument entfernt werden, sodass Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können, ohne ein Kennwort angeben zu müssen. Nachdem die kennwortbasierte Verschlüsselung aus einem PDF-Dokument entfernt wurde, ist das Dokument nicht mehr sicher.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So entfernen Sie die kennwortbasierte Verschlüsselung von einem PDF-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie einen Verschlüsselungsdienst-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entfernen Sie das Kennwort.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient` -Objekt. Wenn Sie die Web Service Encryption Service-API verwenden, erstellen Sie ein `EncryptionServiceService` -Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um kennwortbasierte Verschlüsselung zu entfernen. Wenn Sie versuchen, die Verschlüsselung von einem nicht verschlüsselten PDF-Dokument zu entfernen, wird eine Ausnahme ausgelöst.

**Kennwort entfernen**

Zum Entfernen der kennwortbasierten Verschlüsselung von einem verschlüsselten PDF-Dokument benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch einen Übergeordneten Kennwortwert, der zum Entfernen der Verschlüsselung vom PDF-Dokument verwendet wird. Das Kennwort zum Öffnen eines kennwortverschlüsselten PDF-Dokuments kann nicht zum Entfernen der Verschlüsselung verwendet werden. Ein Übergeordnetes Kennwort wird angegeben, wenn das PDF-Dokument mit einem Kennwort verschlüsselt wird. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

**PDF-Dokument speichern**

Nachdem der Encryption-Dienst die kennwortbasierte Verschlüsselung von einem PDF-Dokument entfernt hat, können Sie das PDF-Dokument als PDF-Datei speichern. Benutzer können das PDF-Dokument in Adobe Reader oder Acrobat öffnen, ohne ein Kennwort anzugeben.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Kennwortbasierte Verschlüsselung mit der Java-API {#remove-password-based-encryption-using-the-java-api} entfernen

Entfernen Sie mithilfe der Verschlüsselungs-API (Java) die kennwortbasierte Verschlüsselung von einem PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-encryption-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie das Kennwort.

   Entfernen Sie die kennwortbasierte Verschlüsselung aus dem PDF-Dokument, indem Sie die `removePDFPasswordSecurity` -Methode des Objekts `EncryptionServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` -Objekt, das das verschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Übergeordneten Kennwortwert angibt, mit dem die Verschlüsselung aus dem PDF-Dokument entfernt wird.

   Die `removePDFPasswordSecurity`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein ungesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `removePDFPasswordSecurity`-Methode zurückgegeben wurde.

**Siehe auch**

[Schnellstart (SOAP-Modus): Kennwortbasierte Verschlüsselung mithilfe der Java-API entfernen](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

### Kennwortbasierte Verschlüsselung mithilfe der Webdienst-API {#remove-password-based-encryption-using-the-web-service-api} entfernen

Entfernen Sie die kennwortbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines kennwortverschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB` -Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB` -Datenelement des `MTOM` -Objekts zuweisen.

1. Entfernen Sie das Kennwort.

   Rufen Sie die `removePDFPasswordSecurity` -Methode des Objekts `EncryptionServiceService` auf und übergeben Sie die folgenden Werte:

   * Das `BLOB`-Objekt, das Datei-Stream-Daten enthält, die ein verschlüsseltes PDF-Dokument darstellen.
   * Ein string -Wert, der den Kennwortwert angibt, mit dem die Verschlüsselung aus dem PDF-Dokument entfernt wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Die `removePDFPasswordSecurity`-Methode gibt ein `BLOB`-Objekt zurück, das ein ungesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `removePDFPasswordSecurity` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entsperren verschlüsselter PDF-Dokumente {#unlocking-encrypted-pdf-documents}

Ein kennwortverschlüsseltes oder zertifikatverschlüsseltes PDF-Dokument muss entsperrt werden, bevor ein anderer AEM Forms-Vorgang ausgeführt werden kann. Wenn Sie versuchen, einen Vorgang für ein verschlüsseltes PDF-Dokument auszuführen, generieren Sie eine Ausnahme. Nachdem Sie ein verschlüsseltes PDF-Dokument entsperrt haben, können Sie einen oder mehrere Vorgänge daran durchführen. Diese Vorgänge können zu anderen Diensten gehören, z. B. zum Acrobat Reader DC Extensions-Dienst.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

So entsperren Sie ein verschlüsseltes PDF-Dokument:

1. Projektdateien einschließen.
1. Erstellen Sie einen Verschlüsselungsdienst-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entsperren Sie das Dokument.
1. Führen Sie einen AEM Forms-Vorgang aus.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient` -Objekt. Wenn Sie die Web Service Encryption Service-API verwenden, erstellen Sie ein `EncryptionServiceService` -Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um es zu entsperren. Wenn Sie versuchen, ein nicht verschlüsseltes PDF-Dokument zu entsperren, wird eine Ausnahme ausgelöst.

**Entsperren des Dokuments**

Zum Entsperren eines kennwortverschlüsselten PDF-Dokuments benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch einen Kennwortwert, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

Zum Entsperren eines zertifikatverschlüsselten PDF-Dokuments benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch den Aliaswert des öffentlichen Schlüssels, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wurde.

**Durchführen eines AEM Forms-Vorgangs**

Nachdem ein verschlüsseltes PDF-Dokument entsperrt wurde, können Sie einen weiteren Dienstvorgang ausführen, z. B. Verwendungsrechte darauf anwenden. Dieser Vorgang gehört zum Acrobat Reader DC Extensions-Dienst.

**Siehe auch**

[Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-java-api)

[Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Webdienst-API.](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Java-API {#unlock-an-encrypted-pdf-document-using-the-java-api}

Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Verschlüsselungs-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des verschlüsselten PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entsperren Sie das Dokument.

   Entsperren Sie ein verschlüsseltes PDF-Dokument, indem Sie die `unlockPDFUsingPassword`- oder `unlockPDFUsingCredential`-Methode des Objekts `EncryptionServiceClient` aufrufen.

   Um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die Methode `unlockPDFUsingPassword` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das kennwortverschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Kennwortwert angibt, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Um ein mit einem Zertifikat verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die Methode `unlockPDFUsingCredential` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das das zertifikatverschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem zum Verschlüsseln des PDF-Dokuments verwendeten privaten Schlüssel entspricht.

   Die Methoden `unlockPDFUsingPassword` und `unlockPDFUsingCredential` geben beide ein `com.adobe.idp.Document`-Objekt zurück, das Sie zur Ausführung eines Vorgangs an eine andere AEM Forms Java-Methode übergeben.

1. Führen Sie einen AEM Forms-Vorgang aus.

   Führen Sie einen AEM Forms-Vorgang für das entsperrte PDF-Dokument aus, um Ihre Geschäftsanforderungen zu erfüllen. Wenn Sie beispielsweise Verwendungsrechte auf ein entsperrtes PDF-Dokument anwenden möchten, übergeben Sie das `com.adobe.idp.Document` -Objekt, das von den Methoden `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` zurückgegeben wurde, an die `ReaderExtensionsServiceClient` -Methode des Objekts `applyUsageRights`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api)  (SOAP-Modus)

[Anwenden von Verwendungsrechten auf PDF-Dokumente](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Webdienst-API {#unlock-an-encrypted-pdf-document-using-the-web-service-api}

Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Ein verschlüsseltes PDF-Dokument abrufen.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB` -Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB` -Datenelement des `MTOM` -Objekts zuweisen.

1. Entsperren Sie das Dokument.

   Entsperren Sie ein verschlüsseltes PDF-Dokument, indem Sie die `unlockPDFUsingPassword`- oder `unlockPDFUsingCredential`-Methode des Objekts `EncryptionServiceClient` aufrufen.

   Um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die Methode `unlockPDFUsingPassword` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das kennwortverschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Kennwortwert angibt, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Um ein mit einem Zertifikat verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die Methode `unlockPDFUsingCredential` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das das zertifikatverschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wird.

   Die Methoden `unlockPDFUsingPassword` und `unlockPDFUsingCredential` geben beide ein `com.adobe.idp.Document`-Objekt zurück, das Sie zur Ausführung eines Vorgangs an eine andere AEM Forms-Methode übergeben.

1. Führen Sie einen AEM Forms-Vorgang aus.

   Führen Sie einen AEM Forms-Vorgang für das entsperrte PDF-Dokument aus, um Ihre Geschäftsanforderungen zu erfüllen. Wenn Sie beispielsweise Verwendungsrechte auf das entsperrte PDF-Dokument anwenden möchten, übergeben Sie das `BLOB` -Objekt, das von den Methoden `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` zurückgegeben wurde, an die `ReaderExtensionsServiceClient` -Methode des Objekts `applyUsageRights`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Bestimmen des Verschlüsselungstyps {#determining-encryption-type}

Sie können den Typ der Verschlüsselung zum Schutz eines PDF-Dokuments programmgesteuert mithilfe der Java Encryption Service-API oder der Web Service Encryption Service-API bestimmen. Manchmal ist es erforderlich, dynamisch zu bestimmen, ob ein PDF-Dokument verschlüsselt ist, und wenn ja, den Verschlüsselungstyp. Sie können beispielsweise bestimmen, ob ein PDF-Dokument mit kennwortbasierter Verschlüsselung oder einer Rights Management-Richtlinie geschützt ist.

Ein PDF-Dokument kann durch die folgenden Verschlüsselungstypen geschützt werden:

* Kennwortbasierte Verschlüsselung
* Zertifikatbasierte Verschlüsselung
* Eine Richtlinie, die vom Rights Management-Dienst erstellt wird
* Ein anderer Verschlüsselungstyp

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

So bestimmen Sie den Verschlüsselungstyp, der ein PDF-Dokument schützt:

1. Projektdateien einschließen.
1. Erstellen Sie einen Verschlüsselungsdienst-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Bestimmen Sie den Verschlüsselungstyp.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Dienstclient erstellen**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient` -Objekt. Wenn Sie die Web Service Encryption Service-API verwenden, erstellen Sie ein `EncryptionServiceService` -Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein PDF-Dokument abrufen, um den Verschlüsselungstyp zu ermitteln, der dieses Dokument schützt.

**Ermitteln des Verschlüsselungstyps**

Sie können den Verschlüsselungstyp bestimmen, der ein PDF-Dokument schützt. Wenn das PDF-Dokument nicht geschützt ist, werden Sie vom Encryption-Dienst darüber informiert, dass das PDF-Dokument nicht gesichert ist.

**Siehe auch**

[Ermitteln des Verschlüsselungstyps mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-java-api)

[Ermitteln des Verschlüsselungstyps mithilfe der Webdienst-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Schützen von Dokumenten mit Richtlinien](/help/forms/developing/protecting-documents-policies.md#protecting-documents-with-policies)

### Ermitteln Sie den Verschlüsselungstyp mit der Java-API {#determine-the-encryption-type-using-the-java-api}.

Bestimmen Sie mithilfe der Verschlüsselungs-API (Java) den Verschlüsselungstyp, durch den ein PDF-Dokument geschützt wird:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Service-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Bestimmen Sie den Verschlüsselungstyp.

   * Bestimmen Sie den Verschlüsselungstyp, indem Sie die `getPDFEncryption`-Methode des Objekts `EncryptionServiceClient` aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument enthält. Diese Methode gibt ein `EncryptionTypeResult` -Objekt zurück.
   * Rufen Sie die `getEncryptionType` -Methode des Objekts `EncryptionTypeResult` auf. Diese Methode gibt einen Enum-Wert `EncryptionType` zurück, der den Verschlüsselungstyp angibt. Wenn das PDF-Dokument beispielsweise mit kennwortbasierter Verschlüsselung geschützt ist, gibt diese Methode `EncryptionType.PASSWORD` zurück.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Bestimmen des Verschlüsselungstyps mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ermitteln Sie den Verschlüsselungstyp mithilfe der Webdienst-API {#determine-the-encryption-type-using-the-web-service-api}.

Bestimmen Sie mithilfe der Verschlüsselungs-API (Webdienst) den Verschlüsselungstyp, durch den ein PDF-Dokument geschützt wird:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Service-Client.

   * Erstellen Sie ein `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB` -Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB` -Datenelement des `MTOM` -Objekts zuweisen.

1. Bestimmen Sie den Verschlüsselungstyp.

   * Rufen Sie die `getPDFEncryption`-Methode des Objekts `EncryptionServiceClient` auf und übergeben Sie das `BLOB`-Objekt, das das PDF-Dokument enthält. Diese Methode gibt ein `EncryptionTypeResult` -Objekt zurück.
   * Rufen Sie den Wert der `EncryptionTypeResult` -Datenmethode des Objekts `encryptionType` ab. Wenn das PDF-Dokument beispielsweise mit kennwortbasierter Verschlüsselung geschützt ist, lautet der Wert dieses Datenelements `EncryptionType.PASSWORD`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
