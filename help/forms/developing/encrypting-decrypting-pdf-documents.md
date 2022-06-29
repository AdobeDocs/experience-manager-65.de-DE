---
title: Verschlüsseln und Entschlüsseln von PDF-Dokumenten
seo-title: Encrypting and Decrypting PDF Documents
description: Verwenden Sie den Verschlüsselungsdienst, um Dokumente zu ver- und entschlüsseln. Zu den Aufgaben des Verschlüsselungsdienstes gehören das Verschlüsseln eines PDF-Dokuments mit einem Kennwort, das Verschlüsseln eines PDF-Dokuments mit einem Zertifikat, das Entfernen der kennwortbasierten Verschlüsselung von einem PDF-Dokument, das Entfernen der zertifikatbasierten Verschlüsselung von einem PDF-Dokument, das Entsperren des PDF-Dokuments, sodass andere Dienstvorgänge ausgeführt werden können, und das Ermitteln des Verschlüsselungstyps eines gesicherten PDF-Dokuments.
seo-description: Use the Encryption service to encrypt and decrypt documents. The Encryption service tasks include encrypting a PDF document with a password, encrypting a PDF document with a certificate, removing password-based encryption from a PDF document, removing certificate-based encryption from a PDF document, unlocking the PDF document so that other service operations can be performed, and determining the encryption type of a secured PDF document.
uuid: 4e4e2716-c21f-4bfe-ae7a-7e91442414ef
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 5e4bda3a-5648-4c0f-b2f8-bdbebb88f537
role: Developer
exl-id: d3cbca7f-9277-4d61-b198-abf4bb008f15
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '8189'
ht-degree: 100%

---

# Verschlüsseln und Entschlüsseln von PDF-Dokumenten {#encrypting-and-decrypting-pdf-documents}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den Verschlüsselungsdienst**

Mit dem Verschlüsselungsdienst können Sie Dokumente verschlüsseln und entschlüsseln. Wird ein Dokument verschlüsselt, ist sein Inhalt nicht mehr lesbar. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf den Inhalt zu erhalten. Wenn ein PDF-Dokument mit einem Kennwort verschlüsselt wird, muss der Benutzer das Kennwort zum Öffnen angeben, damit das Dokument in Adobe Reader oder Adobe Acrobat angezeigt werden kann. Ähnlich muss der Benutzer, wenn ein PDF-Dokument mit einem Zertifikat verschlüsselt ist, das PDF-Dokument mithilfe des öffentlichen Schlüssels entschlüsseln, der dem Zertifikat (privater Schlüssel) entspricht, das zum Verschlüsseln des PDF-Dokuments verwendet wurde.

Sie können diese Aufgaben mithilfe des Verschlüsselungsdienstes erledigen:

* Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)
* Verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat. (Siehe [Verschlüsseln von PDF-Dokumenten mit Zertifikaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).)
* Entfernen Sie die kennwortbasierte Verschlüsselung aus einem PDF-Dokument. (Siehe [Entfernen der Kennwortverschlüsselung](encrypting-decrypting-pdf-documents.md#removing-password-encryption).)
* Entfernen Sie die zertifikatbasierte Verschlüsselung aus einem PDF-Dokument. (Siehe [Zertifikatbasierte Verschlüsselung entfernen](encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).)
* Entsperren Sie das PDF-Dokument, damit andere Dienstvorgänge ausgeführt werden können. Nachdem beispielsweise ein kennwortverschlüsseltes PDF-Dokument entsperrt wurde, können Sie es mit einer digitalen Signatur versehen. (Siehe [Entsperren verschlüsselter PDF-Dokumente](encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents).)
* Bestimmen Sie den Verschlüsselungstyp eines geschützten PDF-Dokuments. (Siehe [Bestimmen des Verschlüsselungstyps](encrypting-decrypting-pdf-documents.md#determining-encryption-type).)

>[!NOTE]
>
>Weitere Informationen über den Verschlüsselungsdienst finden Sie unter [Dienstverweise für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Verschlüsseln von PDF-Dokumenten mit einem Kennwort {#encrypting-pdf-documents-with-a-password}

Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, muss ein Benutzer das Kennwort angeben, damit das Dokument in Adobe Reader oder Acrobat geöffnet werden kann. Außerdem muss ein kennwortverschlüsseltes PDF-Dokument entsperrt werden, bevor ein anderer AEM Forms-Vorgang, wie beispielsweise das digitale Signieren des PDF-Dokuments, mit dem Dokument durchgeführt werden kann.

>[!NOTE]
>
>Wenn Sie ein verschlüsseltes PDF-Dokument in das AEM Forms-Repository hochladen, kann es das PDF-Dokument nicht entschlüsseln und den XDP-Inhalt extrahieren. Es wird empfohlen, dass Sie ein Dokument nicht verschlüsseln, bevor Sie es in das AEM Forms-Repository hochladen. (Siehe [Schreiben von Ressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Weitere Informationen über den Verschlüsselungsdienst finden Sie unter [Dienstverweise für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument mit einem Kennwort zu verschlüsseln, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Verschlüsselungs-Client-API-Objekt.
1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.
1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.
1. Fügen Sie das Kennwort hinzu.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

**Projektdateien einbinden**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Client-API-Objekts**

Um programmgesteuert einen Vorgang des Verschlüsselungs-Dienstes durchzuführen, müssen Sie einen Verschlüsselungs-Dienst-Client erstellen.

**Abrufen eines zu verschlüsselnden PDF-Dokuments**

Sie müssen ein unverschlüsseltes PDF-Dokument abrufen, um das Dokument mit einem Kennwort zu verschlüsseln. Wenn Sie versuchen, ein bereits verschlüsseltes PDF-Dokument zu schützen, wird eine Ausnahme ausgelöst.

**Laufzeitoptionen für die Verschlüsselung festlegen**

Um ein PDF-Dokument mit einem Kennwort zu verschlüsseln, geben Sie vier Werte an, darunter zwei Kennwortwerte. Der erste Kennwortwert wird zum Verschlüsseln des PDF-Dokuments verwendet und muss beim Öffnen des PDF-Dokuments angegeben werden. Der zweite Kennwortwert, der sogenannte „Master-Kennwortwert“, wird zum Entfernen der Verschlüsselung vom PDF-Dokument verwendet. Bei Kennwortwerten wird zwischen Groß- und Kleinschreibung unterschieden und diese beiden Kennwortwerte dürfen nicht dieselben Werte enthalten.

Sie müssen die zu verschlüsselnden Ressourcen des PDF-Dokuments angeben. Sie können das gesamte PDF-Dokument, alles außer den Metadaten des Dokuments oder nur die Anlagen des Dokuments verschlüsseln. Wenn Sie nur die Anhänge des Dokuments verschlüsseln, wird ein Benutzer beim Versuch, auf die Dateianhänge zuzugreifen, zur Eingabe eines Kennworts aufgefordert.

Beim Verschlüsseln eines PDF-Dokuments können Sie Berechtigungen festlegen, die mit dem geschützten Dokument verknüpft sind. Durch Festlegen von Berechtigungen können Sie die Aktionen steuern, die ein Benutzer, der ein kennwortverschlüsseltes PDF-Dokument öffnet, durchführen darf. Um beispielsweise Formulardaten erfolgreich zu extrahieren, müssen Sie die folgenden Berechtigungen festlegen

* PASSWORD_EDIT_ADD
* PASSWORD_EDIT_MODIFY

>[!NOTE]
>
>Berechtigungen werden als `PasswordEncryptionPermission`-Auflistungswerte angegeben.

**Hinzufügen des Kennworts**

Nachdem Sie ein ungesichertes PDF-Dokument abgerufen und die Laufzeitwerte für die Verschlüsselung festgelegt haben, können Sie dem PDF-Dokument ein Kennwort hinzufügen.

**Speichern des verschlüsselten PDF-Dokuments als PDF-Datei**

Sie können das kennwortverschlüsselte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Verschlüsseln eines PDF-Dokuments mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-using-the-java-api)

[Verschlüsseln eines PDF-Dokuments mit der Webdienst-API](encrypting-decrypting-pdf-documents.md#encrypting-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitungen für die API des Verschlüsselungs-Services](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-Dokumente mit Zertifikaten verschlüsseln](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates)

### Verschlüsseln eines PDF-Dokuments mithilfe der Java-API {#encrypt-a-pdf-document-using-the-java-api}

So verschlüsseln Sie ein PDF-Dokument mit einem Kennwort mithilfe der Verschlüsselungs-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-encryption-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-API-Objekt für die Verschlüsselung.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu verschlüsselnde PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein `PasswordEncryptionOptionSpec`-Objekt, indem Sie seinen Konstruktor aufrufen.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie die Methode `setEncryptOption` des `PasswordEncryptionOptionSpec`-Objekts aufrufen und einen `PasswordEncryptionOption`-Auflistungswert übergeben, der die zu verschlüsselnden Dokumentressourcen angibt. Um beispielsweise das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, geben Sie `PasswordEncryptionOption.ALL` an.
   * Erstellen Sie ein `java.util.List`-Objekt, das die Verschlüsselungsberechtigungen speichert, indem Sie den `ArrayList`-Konstruktor verwenden.
   * Geben Sie eine Berechtigung an, indem Sie die Methode `add` des `java.util.List`-Objekts aufrufen und einen Auflistungswert übergeben, der der festzulegenden Berechtigung entspricht. Um zum Beispiel die Berechtigung festzulegen, die es einem Benutzer erlaubt, Daten im PDF-Dokument zu kopieren, geben Sie `PasswordEncryptionPermission.PASSWORD_EDIT_COPY` an. (Wiederholen Sie diesen Schritt für jede festzulegende Berechtigung.)
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie die Methode `setCompatability` des `PasswordEncryptionOptionSpec`-Objekts aufrufen und einen Auflistungswert übergeben, der die Acrobat-Kompatibilitätsstufe angibt. Sie können beispielsweise `PasswordEncryptionCompatability.ACRO_7` angeben.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer das verschlüsselte PDF-Dokument öffnen kann, indem Sie die Methode `setDocumentOpenPassword` des `PasswordEncryptionOptionSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der das Kennwort zum Öffnen darstellt.
   * Geben Sie den Wert des übergeordneten Kennworts an, mit dem ein Benutzer die Verschlüsselung des PDF-Dokuments aufheben kann, indem Sie die Methode `setPermissionPassword` des `PasswordEncryptionOptionSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der das übergeordnete Kennwort darstellt.

1. Fügen Sie das Kennwort hinzu.

   Verschlüsseln Sie das PDF-Dokument, indem Sie die Methode `EncryptionServiceClient` des `encryptPDFUsingPassword`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, welches das PDF-Dokument enthält, das mit dem Kennwort verschlüsselt werden soll.
   * Das `PasswordEncryptionOptionSpec`-Objekt, das Laufzeitoptionen für die Verschlüsselung enthält.

   Die Methode `encryptPDFUsingPassword` gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein passwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `encryptPDFUsingPassword`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments unter Verwendung der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verschlüsseln eines PDF-Dokuments mit der Webdienst-API {#encrypting-a-pdf-document-using-the-web-service-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort mithilfe der Verschlüsselungs-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Verschlüsselungs-Client-API-Objekt.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt mithilfe seines Standardkonstruktors.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgewert, der die WSDL für den AEM Forms-Dienst angibt (beispielsweise `http://localhost:8080/soap/services/EncryptionService?WSDL`.) Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des `EncryptionServiceClient.Endpoint.Binding`-Feldes abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie den AEM Forms-Benutzernamen dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` zu.
      * Weisen Sie den entsprechenden Kennwortwert dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` zu.
      * Weisen Sie den konstanten Wert `HttpClientCredentialType.Basic` dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` zu.
      * Weisen Sie den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu speichern.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgewert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem `MTOM`-Datenelement des `BLOB`-Objekts zuweisen.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein Objekt `PasswordEncryptionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie einen `PasswordEncryptionOption`-Auflistungswert dem `encryptOption`Datenelement des `PasswordEncryptionOptionSpec`-Objekts zuweisen. Um die gesamte PDF-Datei einschließlich ihrer Metadaten und Anhänge zu verschlüsseln, weisen Sie diesem Datenelement `PasswordEncryptionOption.ALL` zu.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie dem `compatability`-Datenelement des `PasswordEncryptionOptionSpec`-Objekts einen `PasswordEncryptionCompatability`-Aufzählungswert zuweisen. Weisen Sie beispielsweise `PasswordEncryptionCompatability.ACRO_7` diesem Datenelement zu.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer das verschlüsselte PDF-Dokument öffnen kann, indem Sie dem `documentOpenPassword`-Datenelement des `PasswordEncryptionOptionSpec`-Objekts einen Zeichenfolgewert zuweisen, der das Öffnungskennwort darstellt.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer die Verschlüsselung des PDF-Dokument entfernen kann, indem Sie dem `permissionPassword`-Datenelement des `PasswordEncryptionOptionSpec`-Objekts einen Zeichenfolgewert zuweisen, der das Hauptkennwort darstellt.

1. Fügen Sie das Kennwort hinzu.

   Verschlüsseln Sie das PDF-Dokument, indem Sie die Methode `encryptPDFUsingPassword` des `EncryptionServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, welches das mit dem Kennwort zu verschlüsselnde PDF-Dokument enthält.
   * Das `PasswordEncryptionOptionSpec`-Objekt, das Laufzeitoptionen für die Verschlüsselung enthält.

   Die `encryptPDFUsingPassword`-Methode gibt ein `BLOB`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie dessen Konstruktor aufrufen und einen Zeichenfolgewert übergeben, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, welches von der `encryptPDFUsingPassword`-Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `MTOM`-Datenelements des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor verwenden und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-Dokumente mit Zertifikaten verschlüsseln {#encrypting-pdf-documents-with-certificates}

Mit der zertifikatsbasierten Verschlüsselung können Sie ein Dokument für bestimmte Empfänger mithilfe der Öffentlichen-Schlüssel-Technologie verschlüsseln. Verschiedene Empfänger können unterschiedliche Berechtigungen für das Dokument erhalten. Viele Aspekte der Verschlüsselung werden durch die Technologie öffentlicher Schlüssel möglich gemacht. Es wird ein Algorithmus verwendet, um zwei große Zahlen, genannt *Schlüssel*, zu erzeugen, welche die folgenden Eigenschaften aufweisen:

* Ein Schlüssel wird zum Verschlüsseln eines Satzes von Daten verwendet. Danach kann nur der andere Schlüssel zum Entschlüsseln der Daten verwendet werden.
* Es ist unmöglich, einen Schlüssel vom anderen zu unterscheiden.

Einer der Schlüssel agiert als der private Schlüssel eines Benutzers. Wichtig ist, dass nur der Benutzer Zugriff auf diesen Schlüssel hat. Der andere Schlüssel ist der öffentliche Schlüssel des Benutzers, der mit Dritten geteilt werden kann.

Ein öffentliches Schlüsselzertifikat enthält den öffentlichen Schlüssel eines Benutzers sowie Identifizierungsinformationen. Das X.509-Format dient zum Speichern von Zertifikaten. Zertifikate werden meist von einer Zertifizierungsstelle ausgestellt und digital signiert, bei der es sich um eine anerkannte Instanz handelt, die ein Maß an Vertrauen in die Gültigkeit des Zertifikats ermöglicht. Zertifikate haben ein Ablaufdatum, nach dem sie nicht mehr gültig sind. Darüber hinaus liefern Zertifikatsperrlisten Informationen zu Zertifikaten, die vor ihrem Ablaufdatum gesperrt wurden. Zertifikatsperrlisten werden regelmäßig von Zertifizierungsstellen veröffentlicht. Der Sperrstatus eines Zertifikats kann auch mittels des Online-Zertifikatstatusprotokolls (Online Certificate Status Protocol, OCSP) über das Netzwerk abgerufen werden.

>[!NOTE]
>
>Wenn Sie ein verschlüsseltes PDF-Dokument in das AEM Forms-Repository hochladen, kann es das PDF-Dokument nicht entschlüsseln und den XDP-Inhalt extrahieren. Es wird empfohlen, dass Sie ein Dokument nicht verschlüsseln, bevor Sie es in das AEM Forms-Repository hochladen. (Siehe [Schreiben von Ressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument mit einem Zertifikat verschlüsseln können, müssen Sie sicherstellen, dass das Zertifikat zu AEM Forms hinzugefügt wird. Ein Zertifikat wird über die Administration-Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Importieren von Anmeldeinformationen mithilfe der Trust Manager-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

>[!NOTE]
>
>Weitere Informationen zum Verschlüsselungs-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um ein PDF-Dokument mit einem Zertifikat zu verschlüsseln, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Verschlüsselungs-Client-API-Objekt.
1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.
1. Referenzieren Sie das Zertifikat.
1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.
1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Client-API-Objekts für die Verschlüsselung**

Um einen Vorgang des Verschlüsselungs-Services programmgesteuert durchführen zu können, müssen Sie einen Verschlüsselungs-Service-Client erstellen. Wenn Sie die Java-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webservice-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Abrufen eines zu verschlüsselnden PDF-Dokuments**

Sie müssen zum Verschlüsseln ein unverschlüsseltes PDF-Dokument abrufen. Wenn Sie versuchen, ein bereits verschlüsseltes PDF-Dokument zu verschlüsseln, wird eine Ausnahme ausgelöst.

**Referenzieren des Zertifikats**

Um ein PDF-Dokument mit einem Zertifikat zu verschlüsseln, verweisen Sie auf ein Zertifikat, das zum Verschlüsseln eines PDF-Dokuments verwendet wird. Das Zertifikat ist eine .cer-Datei, eine .crt-Datei oder eine .pem-Datei. Eine PKCS#12-Datei wird verwendet, um private Schlüssel mit entsprechenden Zertifikaten zu speichern.

Geben Sie beim Verschlüsseln eines PDF-Dokuments mit einem Zertifikat die Berechtigungen an, die mit dem gesicherten Dokument verknüpft sind. Durch Festlegen von Berechtigungen können Sie steuern, welche Aktionen ein Benutzer ausführen kann, der ein zertifikatverschlüsseltes PDF-Dokument öffnet.

**Festlegen der Laufzeitoptionen für die Verschlüsselung**

Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an. Sie können das gesamte PDF-Dokument verschlüsseln, alles außer den Metadaten des Dokuments oder nur die Anlagen des Dokuments.

**Erstellen eines zertifikatsverschlüsselten PDF-Dokuments**

Nachdem Sie ein ungesichertes PDF-Dokument abgerufen, auf das Zertifikat verwiesen und Laufzeitoptionen festgelegt haben, können Sie ein zertifikatverschlüsseltes PDF-Dokument erstellen. Nachdem das PDF-Dokument verschlüsselt wurde, benötigen Sie den entsprechenden öffentlichen Schlüssel zum Entschlüsseln.

**Speichern des verschlüsselten PDF-Dokuments als PDF-Datei**

Sie können das verschlüsselte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-java-api)

[Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Webservice-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitungen für die API des Verschlüsselungs-Services](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API {#encrypt-a-pdf-document-with-a-certificate-using-the-java-api}

So verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat mithilfe der Verschlüsselungs-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-encryption-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Verschlüsselungs-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu verschlüsselnde PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie das Zertifikat.

   * Erstellen Sie ein `java.util.List`-Objekt, das Berechtigungsinformationen speichert, indem Sie seinen Konstruktor verwenden.
   * Geben Sie die mit dem verschlüsselten Dokument verbundenen Berechtigungen an, indem Sie die Methode `add` des `java.util.List`-Objekts aufrufen und einen `CertificateEncryptionPermissions`-Auflistungswert übergeben, der die Berechtigungen darstellt, welche dem Benutzer gewährt werden, der das gesicherte PDF-Dokument öffnet. Um beispielsweise alle Berechtigungen anzugeben, übergeben Sie `CertificateEncryptionPermissions.PKI_ALL_PERM`.
   * Erstellen Sie ein Objekt `Recipient`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das Zertifikat darstellt, das zur Verschlüsselung des PDF-Dokuments verwendet wird, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des Zertifikats angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie dessen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben, das das Zertifikat darstellt.
   * Rufen Sie die Methode `setX509Cert` des `Recipient`-Objekts auf und übergeben Sie das `com.adobe.idp.Document`-Objekt, das das Zertifikat enthält. (Darüber hinaus kann das `Recipient`-Objekt einen Truststore-Zertifikatalias oder eine LDAP-URL als Zertifikatquelle haben.)
   * Erstellen Sie ein `CertificateEncryptionIdentity`-Objekt, das Berechtigungs- und Zertifikatsinformationen speichert, indem Sie seinen Konstruktor verwenden.
   * Rufen Sie die Methode `setPerms` des `CertificateEncryptionIdentity`-Objekts auf und übergeben Sie das `java.util.List`-Objekt, das die Berechtigungsinformationen speichert.
   * Rufen Sie die Methode `setRecipient` des `CertificateEncryptionIdentity`-Objekts auf und übergeben Sie das `Recipient`-Objekt, das Zertifikatsinformationen speichert.
   * Erstellen Sie ein `java.util.List`-Objekt, das Zertifikatsinformationen speichert, indem Sie seinen Konstruktor verwenden.
   * Rufen Sie die Methode add des `java.util.List`-Objekts auf und übergeben Sie das `CertificateEncryptionIdentity`-Objekt. (Dieses `java.util.List`-Objekt wird als Parameter an die Methode `encryptPDFUsingCertificates` übergeben.)

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein `CertificateEncryptionOptionSpec`-Objekt, indem Sie seinen Konstruktor aufrufen.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentenressourcen an, indem Sie die Methode `setOption` des `CertificateEncryptionOptionSpec`-Objekts aufrufen und einen `CertificateEncryptionOption`-Auflistungswert übergeben, der die zu verschlüsselnden Dokumentenressourcen angibt. Um beispielsweise das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, geben Sie `CertificateEncryptionOption.ALL` an.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie die Methode `setCompat` des `CertificateEncryptionOptionSpec`-Objekts aufrufen und einen `CertificateEncryptionCompatibility`-Auflistungswert übergeben, der die Acrobat-Kompatibilitätsstufe angibt. Sie können beispielsweise `CertificateEncryptionCompatibility.ACRO_7` angeben.

1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.

   Verschlüsseln Sie das PDF-Dokument mit einem Zertifikat, indem Sie die Methode `encryptPDFUsingCertificates` des `EncryptionServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das zu verschlüsselnde PDF-Dokument enthält.
   * Das `java.util.List`-Objekt, das Zertifikatinformationen speichert.
   * Das `CertificateEncryptionOptionSpec`-Objekt, das Laufzeitoptionen für die Verschlüsselung enthält.

   Die Methode `encryptPDFUsingCertificates` gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein zertifikatverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `encryptPDFUsingCertificates`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit einem Zertifikat unter Verwendung der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Webservice-API {#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api}

So verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat mithilfe der Verschlüsselungs-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Verschlüsselungs-Client-API-Objekt.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der dem AEM Forms-Service die WSDL angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines mit einem PDF-Zertifikat verschlüsselten Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die Länge des zu lesenden Streams übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Referenzieren Sie das Zertifikat.

   * Erstellen Sie ein Objekt `Recipient`, indem Sie den Konstruktor verwenden. Dieses Objekt speichert Zertifikatinformationen.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt speichert das Zertifikat, das das PDF-Dokument verschlüsselt.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Zertifikats und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die Länge des zu lesenden Streams übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem Datenelement `MTOM` des `BLOB`-Objekts zuweisen.
   * Weisen Sie das `BLOB`-Objekt, das das Zertifikat speichert, dem Datenelement `x509Cert` des `Recipient`-Objekts zu.
   * Erstellen Sie ein `CertificateEncryptionIdentity`-Objekt, das Zertifikatsinformationen speichert, indem Sie seinen Konstruktor verwenden.
   * Weisen Sie das `Recipient`-Objekt, das das Zertifikat speichert, dem Empfängerdatenelement des `CertificateEncryptionIdentity`-Objekts zu.
   * Erstellen Sie ein `Object`-Array und weisen Sie das `CertificateEncryptionIdentity`-Objekt dem ersten Element des `Object`-Arrays zu. Dieses `Object`-Array wird als Parameter an die Methode `encryptPDFUsingCertificates` übergeben.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein Objekt `CertificateEncryptionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie dem Datenelement `option` des `CertificateEncryptionOptionSpec`-Objekts einen `CertificateEncryptionOption`-Auflistungswert zuweisen. Um das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, weisen Sie diesem Datenelement `CertificateEncryptionOption.ALL` zu.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie dem Datenelement `compat` des `CertificateEncryptionOptionSpec`-Objekts einen `CertificateEncryptionCompatibility`-Auflistungswert zuweisen. Weisen Sie diesem Datenelement zum Beispiel `CertificateEncryptionCompatibility.ACRO_7` zu.

1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.

   Verschlüsseln Sie das PDF-Dokument mit einem Zertifikat, indem Sie die Methode `encryptPDFUsingCertificates` des `EncryptionServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das zu verschlüsselende PDF-Dokument enthält.
   * Das `Object`-Array, das Zertifikatinformationen speichert.
   * Das `CertificateEncryptionOptionSpec`-Objekt, das Laufzeitoptionen für die Verschlüsselung enthält.

   Die Methode `encryptPDFUsingCertificates` gibt ein `BLOB`-Objekt zurück, das ein zertifikatverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `encryptPDFUsingCertificates` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `binaryData` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen der zertifikatbasierten Verschlüsselung {#removing-certificate-based-encryption}

Es ist möglich, die zertifikatbasierte Verschlüsselung aus einem PDF-Dokument zu entfernen, damit die Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können. Um die Verschlüsselung von einem PDF-Dokument zu entfernen, das mit einem Zertifikat verschlüsselt ist, muss auf einen öffentlichen Schlüssel verwiesen werden. Nachdem die Verschlüsselung von einem PDF-Dokument entfernt wurde, ist es nicht mehr geschützt.

>[!NOTE]
>
>Weitere Informationen zum Verschlüsselungs-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Schritte aus, um die zertifikatbasierte Verschlüsselung aus einem PDF-Dokument zu entfernen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Verschlüsselungs-Service-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entfernen Sie die Verschlüsselung.
1. Speichern Sie das Formular als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um einen Vorgang des Verschlüsselungs-Services programmgesteuert durchführen zu können, müssen Sie einen Verschlüsselungs-Service-Client erstellen. Wenn Sie die Java-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webservice-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Abrufen des verschlüsselten PDF-Dokuments**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um die zertifikatbasierte Verschlüsselung entfernen zu können. Wenn Sie versuchen, die Verschlüsselung von einem nicht verschlüsselten PDF-Dokument zu entfernen, wird eine Ausnahme ausgelöst. Wenn Sie versuchen, die zertifikatbasierte Verschlüsselung aus einem kennwortverschlüsselten Dokument zu entfernen, wird eine Ausnahme ausgelöst.

**Entfernen der Verschlüsselung**

Zum Entfernen der zertifikatbasierten Verschlüsselung von einem verschlüsselten PDF-Dokument benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch den privaten Schlüssel, der dem Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wurde. Der Aliaswert des privaten Schlüssels wird beim Entfernen der zertifikatbasierten Verschlüsselung aus einem verschlüsselten PDF-Dokument angegeben. Informationen zum öffentlichen Schlüssel finden Sie unter [Verschlüsseln von PDF-Dokumenten mit Zertifikaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).

>[!NOTE]
>
>Ein privater Schlüssel wird im Trust Store von AEM Forms gespeichert. Wenn dort ein Zertifikat platziert wird, wird ein Alias-Wert angegeben.

**Speichern des PDF-Dokuments**

Nachdem die zertifikatbasierte Verschlüsselung aus einem verschlüsselten PDF-Dokument entfernt wurde, können Sie das PDF-Dokument als PDF-Datei speichern. Benutzer können das PDF-Dokument jetzt in Adobe Reader oder Acrobat öffnen.

**Siehe auch**

[Entfernen der zertifikatbasierten Verschlüsselung mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-java-api)

[Entfernen der zertifikatbasierten Verschlüsselung mithilfe der Webservice-API](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitungen für die API des Verschlüsselungs-Services](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Entfernen der zertifikatbasierten Verschlüsselung mithilfe der Java-API {#remove-certificate-based-encryption-using-the-java-api}

So entfernen Sie die zertifikatbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Java) aus einem PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-encryption-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungs-Service-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des verschlüsselten PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie die Verschlüsselung.

   Entfernen Sie die zertifikatsbasierte Verschlüsselung aus dem PDF-Dokument, indem Sie die Methode `removePDFCertificateSecurity` des `EncryptionServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das verschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Aliasnamen des privaten Schlüssels angibt, der dem zum Verschlüsseln des PDF-Dokuments verwendeten Schlüssel entspricht.

   Die Methode `removePDFCertificateSecurity` gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein ungesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `removePDFCredentialSecurity`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Entfernen einer zertifikatbasierten Verschlüsselung unter Verwendung der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entfernen der zertifikatbasierten Verschlüsselung mithilfe der Webservice-API {#remove-certificate-based-encryption-using-the-web-service-api}

So entfernen Sie die zertifikatbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungs-Service-Client.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der dem AEM Forms-Service die WSDL angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die Länge des zu lesenden Streams übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem Datenelement `MTOM` des `BLOB`-Objekts zuweisen.

1. Entfernen Sie die Verschlüsselung.

   Rufen Sie die Methode `removePDFCertificateSecurity` des `EncryptionServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Das `BLOB`-Objekt, das Datei-Stream-Daten enthält, die ein verschlüsseltes PDF-Dokument darstellen.
   * Ein Zeichenfolgenwert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wird.

   Die Methode `removePDFCredentialSecurity` gibt ein `BLOB`-Objekt zurück, das ein ungesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der Methode `removePDFPasswordSecurity` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des Objekts `BLOB` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen der Kennwortverschlüsselung {#removing-password-encryption}

Es ist möglich, die kennwortbasierte Verschlüsselung aus einem PDF-Dokument zu entfernen, sodass Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können, ohne ein Kennwort angeben zu müssen. Nachdem die kennwortbasierte Verschlüsselung von einem PDF-Dokument entfernt wurde, ist es nicht mehr geschützt.

>[!NOTE]
>
>Weitere Informationen zum Verschlüsselungs-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So entfernen Sie die kennwortbasierte Verschlüsselung aus einem PDF-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie einen Verschlüsselungs-Service-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entfernen Sie das Kennwort.
1. Speichern Sie das Formular als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um einen Vorgang des Verschlüsselungs-Services programmgesteuert durchführen zu können, müssen Sie einen Verschlüsselungs-Service-Client erstellen. Wenn Sie die Java-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webservice-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Abrufen des verschlüsselten PDF-Dokuments**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um die kennwortbasierte Verschlüsselung entfernen zu können. Wenn Sie versuchen, die Verschlüsselung aus einem nicht verschlüsselten PDF-Dokument zu entfernen, wird eine Ausnahme ausgelöst.

**Entfernen des Kennworts**

Zum Entfernen der kennwortbasierten Verschlüsselung aus einem verschlüsselten PDF-Dokument benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch einen übergeordneten Kennwortwert, der zum Entfernen der Verschlüsselung aus dem PDF-Dokument verwendet wird. Das Kennwort zum Öffnen eines kennwortverschlüsselten PDF-Dokuments kann nicht selbst zum Entfernen der Verschlüsselung verwendet werden. Ein übergeordnetes Kennwort wird angegeben, wenn das PDF-Dokument mit einem Kennwort verschlüsselt wird. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

**Speichern des PDF-Dokuments**

Nachdem der Verschlüsselungs-Service die kennwortbasierte Verschlüsselung aus einem PDF-Dokument entfernt hat, können Sie das PDF-Dokument als PDF-Datei speichern. Benutzer können das PDF-Dokument dann in Adobe Reader oder Acrobat öffnen, ohne ein Kennwort anzugeben.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitungen für die API des Verschlüsselungs-Services](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Entfernen der kennwortbasierten Verschlüsselung mithilfe der Java-API {#remove-password-based-encryption-using-the-java-api}

So entfernen Sie mithilfe der Verschlüsselungs-API (Java) die kennwortbasierte Verschlüsselung aus einem PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-encryption-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungs-Service-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie das Kennwort.

   Entfernen Sie die kennwortbasierte Verschlüsselung aus dem PDF-Dokument, indem Sie die Methode `removePDFPasswordSecurity` des `EncryptionServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document`-Objekt, das das verschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den übergeordneten Kennwortwert angibt, der zum Entfernen der Verschlüsselung aus dem PDF-Dokument verwendet wird.

   Die Methode `removePDFPasswordSecurity` gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein ungesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `removePDFPasswordSecurity`-Methode zurückgegeben wurde.

**Siehe auch**

[Schnellstart (SOAP-Modus): Entfernen einer kennwortbasierten Verschlüsselung unter Verwendung der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

### Entfernen der kennwortbasierten Verschlüsselung mithilfe der Webservice-API {#remove-password-based-encryption-using-the-web-service-api}

So entfernen Sie die kennwortbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungs-Service-Client.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der dem AEM Forms-Service die WSDL angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines kennwortverschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die Länge des zu lesenden Streams übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem Datenelement `MTOM` des `BLOB`-Objekts zuweisen.

1. Entfernen Sie das Kennwort.

   Rufen Sie die Methode `removePDFPasswordSecurity` des `EncryptionServiceService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Das `BLOB`-Objekt, das Datei-Stream-Daten enthält, die ein verschlüsseltes PDF-Dokument darstellen.
   * Ein Zeichenfolgenwert, der den Kennwortwert angibt, der zum Entfernen der Verschlüsselung aus dem PDF-Dokument verwendet wird. Dieser Wert wird angegeben, wenn das PDF-Dokument mit einem Kennwort verschlüsselt wird.

   Die Methode `removePDFPasswordSecurity` gibt ein `BLOB`-Objekt zurück, das ein ungesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der Methode `removePDFPasswordSecurity` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `BLOB` des `MTOM`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entsperren verschlüsselter PDF-Dokumente {#unlocking-encrypted-pdf-documents}

Ein kennwortverschlüsseltes oder zertifikatverschlüsseltes PDF-Dokument muss entsperrt werden, bevor mit ihm ein anderer AEM Forms-Vorgang ausgeführt werden kann. Wenn Sie versuchen, einen Vorgang mit einem verschlüsselten PDF-Dokument durchzuführen, wird eine Ausnahme ausgelöst. Nachdem Sie ein verschlüsseltes PDF-Dokument entsperrt haben, können Sie mit ihm einen oder mehrere Vorgänge ausführen. Diese Vorgänge können zu anderen Services gehören, z. B. zum Acrobat Reader DC-Erweiterungen-Service.

>[!NOTE]
>
>Weitere Informationen zum Verschlüsselungs-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

So entsperren Sie ein verschlüsseltes PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Verschlüsselungs-Service-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entsperren Sie das Dokument.
1. Führen Sie einen AEM Forms-Vorgang aus.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um einen Vorgang des Verschlüsselungs-Services programmgesteuert durchführen zu können, müssen Sie einen Verschlüsselungs-Service-Client erstellen. Wenn Sie die Java-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webservice-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Abrufen des verschlüsselten PDF-Dokuments**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um es entsperren zu können. Wenn Sie versuchen, ein nicht verschlüsseltes PDF-Dokument zu entsperren, wird eine Ausnahme ausgelöst.

**Entsperren des Dokuments**

Zum Entsperren eines kennwortverschlüsselten PDF-Dokuments benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch einen Kennwortwert, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird angegeben, wenn das PDF-Dokument mit einem Kennwort verschlüsselt wird. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

Zum Entsperren eines zertifikatverschlüsselten PDF-Dokuments benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch den Aliaswert des öffentlichen Schlüssels, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wurde.

**Durchführen eines AEM Forms-Vorgangs**

Nachdem ein verschlüsseltes PDF-Dokument entsperrt wurde, können Sie einen weiteren Service-Vorgang durchführen, z. B. Verwendungsrechte darauf anwenden. Dieser Vorgang gehört zum Acrobat Reader DC-Erweiterungen-Service.

**Siehe auch**

[Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-java-api)

[Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Webservice-API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitungen für die API des Verschlüsselungs-Services](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API {#unlock-an-encrypted-pdf-document-using-the-java-api}

So entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Verschlüsselungs-API (Java):

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-encryption-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungs-Service-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des verschlüsselten PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entsperren Sie das Dokument.

   Entsperren Sie ein verschlüsseltes PDF-Dokument, indem Sie die Methode `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` des `EncryptionServiceClient`-Objekts aufrufen.

   Um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die Methode `unlockPDFUsingPassword` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das kennwortverschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Kennwortwert angibt, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird angegeben, wenn das PDF-Dokument mit einem Kennwort verschlüsselt wird.

   Um ein zertifikatverschlüsseltes PDF-Dokument zu entsperren, rufen Sie die Methode `unlockPDFUsingCredential` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das zertifikatverschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem zum Verschlüsseln des PDF-Dokuments verwendeten privaten Schlüssel entspricht.

   Die Methoden `unlockPDFUsingPassword` und `unlockPDFUsingCredential` geben beide ein `com.adobe.idp.Document`-Objekt zurück, das Sie an eine andere Java-Methode in AEM Forms übergeben können, um einen Vorgang auszuführen.

1. Führen Sie einen AEM Forms-Vorgang aus.

   Führen Sie einen AEM Forms-Vorgang mit dem entsperrten PDF-Dokument aus, um Ihre Geschäftsanforderungen zu erfüllen. Wenn Sie beispielsweise Nutzungsrechte auf ein ungesperrtes PDF-Dokument anwenden möchten, übergeben Sie das `com.adobe.idp.Document`-Objekt, das von den Methoden `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` zurückgegeben wurde, an die Methode `applyUsageRights` des `ReaderExtensionsServiceClient`-Objekts.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Kurzanleitung (SOAP-Modus): Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api) (SOAP-Modus)

[Anwenden von Verwendungsrechten auf PDF-Dokumente](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Webservice-API {#unlock-an-encrypted-pdf-document-using-the-web-service-api}

So entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Verschlüsselungs-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungs-Service-Client.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt, indem Sie den `System.ServiceModel.EndpointAddress`-Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der dem AEM Forms-Service die WSDL angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein verschlüsseltes PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die Länge des zu lesenden Streams übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem Datenelement `MTOM` des `BLOB`-Objekts zuweisen.

1. Entsperren Sie das Dokument.

   Entsperren Sie ein verschlüsseltes PDF-Dokument, indem Sie die Methode `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` des `EncryptionServiceClient`-Objekts aufrufen.

   Um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die Methode `unlockPDFUsingPassword` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das kennwortverschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Kennwortwert angibt, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird angegeben, wenn das PDF-Dokument mit einem Kennwort verschlüsselt wird.

   Um ein zertifikatverschlüsseltes PDF-Dokument zu entsperren, rufen Sie die Methode `unlockPDFUsingCredential` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das zertifikatverschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wird.

   Die Methoden `unlockPDFUsingPassword` und `unlockPDFUsingCredential` geben beide ein `com.adobe.idp.Document`-Objekt zurück, das Sie an eine andere AEM Forms-Methode übergeben können, um einen Vorgang auszuführen.

1. Führen Sie einen AEM Forms-Vorgang aus.

   Führen Sie einen AEM Forms-Vorgang mit dem entsperrten PDF-Dokument aus, um Ihre Geschäftsanforderungen zu erfüllen. Wenn Sie beispielsweise Nutzungsrechte auf das entsperrte PDF-Dokument anwenden möchten, übergeben Sie das `BLOB`-Objekt, das entweder von der Methode `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` zurückgegeben wurde, an die Methode `applyUsageRights` des `ReaderExtensionsServiceClient`-Objekts.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Bestimmen des Verschlüsselungstyps {#determining-encryption-type}

Sie können den Verschlüsselungstyp, der ein PDF-Dokument schützt, programmgesteuert mithilfe der Java-API des Verschlüsselungs-Services oder der Webservice-API des Verschlüsselungs-Services bestimmen. Manchmal ist es erforderlich, dynamisch zu bestimmen, ob ein PDF-Dokument verschlüsselt ist, und wenn ja, den Verschlüsselungstyp. Sie können beispielsweise bestimmen, ob ein PDF-Dokument mit kennwortbasierter Verschlüsselung oder einer Rights Management-Richtlinie geschützt ist.

Ein PDF-Dokument kann durch die folgenden Verschlüsselungstypen geschützt werden:

* Kennwortbasierte Verschlüsselung
* Zertifikatbasierte Verschlüsselung
* Eine Richtlinie, die vom Rights Management-Service erstellt wird
* Ein anderer Verschlüsselungstyp

>[!NOTE]
>
>Weitere Informationen zum Verschlüsselungs-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

So bestimmen Sie den Verschlüsselungstyp, der ein PDF-Dokument schützt:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Verschlüsselungs-Service-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Bestimmen Sie den Verschlüsselungstyp.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Service-Clients**

Um einen Vorgang des Verschlüsselungs-Services programmgesteuert durchführen zu können, müssen Sie einen Verschlüsselungs-Service-Client erstellen. Wenn Sie die Java-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webservice-API des Verschlüsselungs-Services verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Abrufen des verschlüsselten PDF-Dokuments**

Sie müssen ein PDF-Dokument abrufen, um die Art der Verschlüsselung zu bestimmen, durch die es geschützt wird.

**Ermitteln des Verschlüsselungstyps**

Sie können die Art der Verschlüsselung bestimmen, durch die ein PDF-Dokument geschützt wird. Wenn das PDF-Dokument nicht geschützt ist, werden Sie vom Verschlüsselungs-Service darüber informiert, dass das PDF-Dokument nicht gesichert ist.

**Siehe auch**

[Ermitteln des Verschlüsselungstyps mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-java-api)

[Ermitteln des Verschlüsselungstyps mithilfe der Webservice-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Kurzanleitungen für die API des Verschlüsselungs-Services](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Schützen von Dokumenten durch Richtlinien](/help/forms/developing/protecting-documents-policies.md#protecting-documents-with-policies)

### Ermitteln des Verschlüsselungstyps mithilfe der Java-API {#determine-the-encryption-type-using-the-java-api}

Bestimmen Sie mithilfe der Verschlüsselungs-API (Java) den Verschlüsselungstyp, der ein PDF-Dokument schützt:

1. Schließen Sie Projektdateien ein.

   Fügen Sie Client-JAR-Dateien wie „adobe-encryption-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Dienst-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, welches das PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Bestimmen Sie den Verschlüsselungstyp.

   * Bestimmen Sie den Verschlüsselungstyp, indem Sie die `getPDFEncryption`-Methode des `EncryptionServiceClient`-Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, welches das PDF-Dokument enthält. Diese Methode gibt eine `EncryptionTypeResult`-Objekt zurück.
   * Rufen Sie die `getEncryptionType`-Methode des `EncryptionTypeResult`-Objekts auf. Diese Methode gibt einen `EncryptionType`-Enum-Wert zurück, der den Verschlüsselungstyp angibt. Wenn das PDF-Dokument beispielsweise mit einer kennwortbasierter Verschlüsselung geschützt ist, gibt diese Methode `EncryptionType.PASSWORD` zurück.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Bestimmen des Verschlüsselungstyps unter Verwendung der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ermitteln des Verschlüsselungstyps mithilfe der Webservice-API {#determine-the-encryption-type-using-the-web-service-api}

Bestimmen Sie mithilfe der Verschlüsselungs-API (Webdienst) den Typ der Verschlüsselung, die ein PDF-Dokument schützt:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Dienst-Client.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt mithilfe seines Standardkonstruktors.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors. Übergeben Sie einen Zeichenfolgewert, der die WSDL für den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`.). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `MessageEncoding` des `System.ServiceModel.BasicHttpBinding`-Objekts auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie den AEM Forms-Benutzernamen dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` zu.
      * Weisen Sie den entsprechenden Kennwortwert dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` zu.
      * Weisen Sie den konstanten Wert `HttpClientCredentialType.Basic` dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` zu.
      * Weisen Sie den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgewert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die `Length`-Eigenschaft des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read`-Methode des `System.IO.FileStream`-Objekts aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem `MTOM`-Datenelement des `BLOB`-Objekts zuweisen.

1. Bestimmen Sie den Verschlüsselungstyp.

   * Rufen Sie die `getPDFEncryption`-Methode des `EncryptionServiceClient`-Objekts auf und übergeben Sie das `BLOB`-Objekt, welches das PDF-Dokument enthält. Diese Methode gibt ein `EncryptionTypeResult`-Objekt zurück.
   * Ermittelt den Wert der `encryptionType`-Datenmethode des `EncryptionTypeResult`Objekts. Wenn das PDF-Dokument beispielsweise mit kennwortbasierter Verschlüsselung geschützt ist, lautet der Wert dieses Datenelements `EncryptionType.PASSWORD`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
