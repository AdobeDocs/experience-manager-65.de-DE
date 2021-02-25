---
title: PDF-Dokumente verschlüsseln und entschlüsseln
seo-title: PDF-Dokumente verschlüsseln und entschlüsseln
description: Verwenden Sie den Encryption-Dienst zum Verschlüsseln und Entschlüsseln von Dokumenten. Zu den Aufgaben des Encryption-Dienstes gehören das Verschlüsseln eines PDF-Dokuments mit einem Kennwort, das Verschlüsseln eines PDF-Dokuments mit einem Zertifikat, das Entfernen der kennwortbasierten Verschlüsselung aus einem PDF-Dokument, das Entfernen der zertifikatbasierten Verschlüsselung aus einem PDF-Dokument, das Entsperren des PDF-Dokuments, sodass andere Dienstvorgänge durchgeführt werden können, und das Ermitteln des Verschlüsselungstyps eines geschützten PDF-Dokuments.
seo-description: Verwenden Sie den Encryption-Dienst zum Verschlüsseln und Entschlüsseln von Dokumenten. Zu den Aufgaben des Encryption-Dienstes gehören das Verschlüsseln eines PDF-Dokuments mit einem Kennwort, das Verschlüsseln eines PDF-Dokuments mit einem Zertifikat, das Entfernen der kennwortbasierten Verschlüsselung aus einem PDF-Dokument, das Entfernen der zertifikatbasierten Verschlüsselung aus einem PDF-Dokument, das Entsperren des PDF-Dokuments, sodass andere Dienstvorgänge durchgeführt werden können, und das Ermitteln des Verschlüsselungstyps eines geschützten PDF-Dokuments.
uuid: 4e4e2716-c21f-4bfe-ae7a-7e91442414ef
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 5e4bda3a-5648-4c0f-b2f8-bdbebb88f537
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '8258'
ht-degree: 8%

---


# Verschlüsseln und Entschlüsseln von PDF-Dokumenten {#encrypting-and-decrypting-pdf-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

**Info zum Encryption-Dienst**

Mit dem Encryption-Dienst können Sie Dokumente verschlüsseln und entschlüsseln. Wird ein Dokument verschlüsselt, ist sein Inhalt nicht mehr lesbar. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf den Inhalt zu erhalten. Wenn ein PDF-Dokument mit einem Kennwort verschlüsselt wird, muss der Benutzer das Kennwort zum Öffnen angeben, damit das Dokument in Adobe Reader oder Adobe angezeigt werden kann. Ähnlich muss der Benutzer, wenn ein PDF-Dokument mit einem Zertifikat verschlüsselt ist, das PDF-Dokument mithilfe des öffentlichen Schlüssels entschlüsseln, der dem Zertifikat (privater Schlüssel) entspricht, das zum Verschlüsseln des PDF-Dokuments verwendet wurde.

Sie können diese Aufgaben mithilfe des Encryption-Dienstes ausführen:

* PDF-Dokumente mit einem Kennwort verschlüsseln (Siehe [PDF-Dokumente mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password) verschlüsseln.)
* PDF-Dokumente mit einem Zertifikat verschlüsseln (Siehe [PDF-Dokumente mit Zertifikaten verschlüsseln](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).)
* Entfernen Sie die kennwortbasierte Verschlüsselung aus einem PDF-Dokument. (Siehe [Kennwortverschlüsselung entfernen](encrypting-decrypting-pdf-documents.md#removing-password-encryption).)
* Zertifikatbasierte Verschlüsselung aus einem PDF-Dokument entfernen. (Siehe [Zertifikatbasierte Verschlüsselung entfernen](encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).)
* Entsperren Sie das PDF-Dokument, damit andere Dienstvorgänge ausgeführt werden können. Wenn beispielsweise ein kennwortverschlüsseltes PDF-Dokument entsperrt ist, können Sie eine digitale Unterschrift darauf anwenden. (Siehe [Encryption Encrypted PDF Dokumente](encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents) entsperren.)
* Ermitteln Sie den Verschlüsselungstyp eines geschützten PDF-Dokuments. (Siehe [Ermitteln des Verschlüsselungstyps](encrypting-decrypting-pdf-documents.md#determining-encryption-type).)

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## PDF-Dokumente mit einem Kennwort {#encrypting-pdf-documents-with-a-password} verschlüsseln

Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, muss ein Benutzer das Kennwort angeben, damit das Dokument in Adobe Reader oder Acrobat geöffnet werden kann. Bevor ein anderer AEM Forms-Vorgang wie das digitale Signieren des PDF-Dokuments auf dem Dokument ausgeführt werden kann, muss die Sperre eines kennwortverschlüsselten PDF-Dokuments aufgehoben werden.

>[!NOTE]
>
>Wenn Sie ein verschlüsseltes PDF-Dokument in das AEM Forms-Repository hochladen, kann es das PDF-Dokument nicht entschlüsseln und den XDP-Inhalt extrahieren. Es wird empfohlen, ein Dokument vor dem Hochladen in das AEM Forms-Repository nicht zu verschlüsseln. (Siehe [Schreibressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So verschlüsseln Sie ein PDF-Dokument mit einem Kennwort:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Encryption Client-API-Objekt.
1. PDF-Dokument verschlüsseln
1. Legen Sie Optionen für die Verschlüsselungslaufzeit fest.
1. hinzufügen das Kennwort.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Client-API-Objekts**

Um einen Encryption-Dienstvorgang programmgesteuert durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen.

**PDF-Dokument zum Verschlüsseln abrufen**

Sie müssen ein unverschlüsseltes PDF-Dokument abrufen, um das Dokument mit einem Kennwort zu verschlüsseln. Wenn Sie versuchen, ein bereits verschlüsseltes PDF-Dokument zu schützen, wird eine Ausnahme ausgelöst.

**Festlegen von Optionen für die Verschlüsselungslaufzeit**

Um ein PDF-Dokument mit einem Kennwort zu verschlüsseln, geben Sie vier Werte ein, darunter zwei Kennwortwerte. Der erste Kennwortwert wird zum Verschlüsseln des PDF-Dokuments verwendet und muss beim Öffnen des PDF-Dokuments angegeben werden. Der zweite Kennwortwert mit dem Namen &quot;Übergeordnet password value&quot;wird zum Entfernen der Verschlüsselung aus dem PDF-Dokument verwendet. Bei Kennwortwerten wird die Groß-/Kleinschreibung beachtet, und diese beiden Kennwortwerte dürfen nicht mit den gleichen Werten übereinstimmen.

Sie müssen die zu verschlüsselnden PDF-Dokument-Ressourcen angeben. Sie können das gesamte PDF-Dokument verschlüsseln, mit Ausnahme der Metadaten des Dokuments oder nur der Anlagen des Dokuments. Wenn Sie nur die Anlagen des Dokuments verschlüsseln, wird ein Benutzer beim Versuch, auf die Dateianlagen zuzugreifen, zur Eingabe eines Kennworts aufgefordert.

Beim Verschlüsseln eines PDF-Dokuments können Sie Berechtigungen angeben, die mit dem geschützten Dokument verknüpft sind. Durch Angabe von Berechtigungen können Sie steuern, welche Aktionen Benutzer ausführen dürfen, die ein kennwortverschlüsseltes PDF-Dokument öffnen. Um beispielsweise Formulardaten erfolgreich extrahieren zu können, müssen Sie die folgenden Berechtigungen festlegen:

* PASSWORD_EDIT_ADD
* PASSWORD_EDIT_MODIFY

>[!NOTE]
>
>Berechtigungen werden als `PasswordEncryptionPermission`-Auflistung angegeben.

**Kennwort Hinzufügen**

Nachdem Sie ein nicht geschütztes PDF-Dokument abgerufen und Verschlüsselungslaufzeitwerte festgelegt haben, können Sie dem PDF-Dokument ein Kennwort hinzufügen.

**Verschlüsseltes PDF-Dokument als PDF-Datei speichern**

Sie können das kennwortverschlüsselte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[PDF-Dokumente mit der Java-API verschlüsseln](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-using-the-java-api)

[Verschlüsseln eines PDF-Dokuments mit der Webdienst-API](encrypting-decrypting-pdf-documents.md#encrypting-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-Dokumente mit Zertifikaten verschlüsseln](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates)

### Verschlüsseln eines PDF-Dokuments mit der Java-API {#encrypt-a-pdf-document-using-the-java-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort mithilfe der Verschlüsselungs-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien, wie z. B. &quot;adobe-cryption-client.jar&quot;, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie eine Verschlüsselungs-Client-API.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument verschlüsseln

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu verschlüsselnde PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Optionen für die Verschlüsselungslaufzeit fest.

   * Erstellen Sie ein `PasswordEncryptionOptionSpec`-Objekt, indem Sie den Konstruktor aufrufen.
   * Geben Sie die zu verschlüsselnden PDF-Dokument-Ressourcen an, indem Sie die `setEncryptOption`-Methode des Objekts aufrufen und einen `PasswordEncryptionOption`-Auflistung-Wert übergeben, der die zu verschlüsselnden Dokumente angibt. `PasswordEncryptionOptionSpec` Um beispielsweise das gesamte PDF-Dokument einschließlich der zugehörigen Metadaten und Anlagen zu verschlüsseln, geben Sie `PasswordEncryptionOption.ALL` an.
   * Erstellen Sie ein `java.util.List`-Objekt, das die Verschlüsselungsberechtigungen mithilfe des Konstruktors `ArrayList` speichert.
   * Geben Sie eine Berechtigung an, indem Sie die Methode `java.util.List` des Objekts &quot;s `add` aufrufen und einen Auflistung-Wert übergeben, der der gewünschten Berechtigung entspricht. Um beispielsweise die Berechtigung zum Kopieren von Daten im PDF-Dokument festzulegen, geben Sie `PasswordEncryptionPermission.PASSWORD_EDIT_COPY` an. (Wiederholen Sie diesen Schritt für jede festzulegende Berechtigung.)
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie die `PasswordEncryptionOptionSpec`-Objektmethode `setCompatability` aufrufen und einen Auflistung-Wert übergeben, der die Acrobat-Kompatibilitätsstufe angibt. Sie können beispielsweise `PasswordEncryptionCompatability.ACRO_7` angeben.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer das verschlüsselte PDF-Dokument öffnen kann, indem er die `setDocumentOpenPassword`-Methode des Objekts aufruft und einen Zeichenfolgenwert übergibt, der das offene Kennwort darstellt.`PasswordEncryptionOptionSpec`
   * Geben Sie den Wert für das Übergeordnet-Kennwort an, mit dem ein Benutzer die Verschlüsselung aus dem PDF-Dokument entfernen kann, indem er die `setPermissionPassword`-Methode des Objekts aufruft und einen Zeichenfolgenwert übergibt, der das Übergeordnet-Kennwort darstellt.`PasswordEncryptionOptionSpec`

1. hinzufügen das Kennwort.

   Verschlüsseln Sie das PDF-Dokument, indem Sie die `EncryptionServiceClient`-Objektmethode `encryptPDFUsingPassword` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält, das mit dem Kennwort verschlüsselt werden soll.
   * Das `PasswordEncryptionOptionSpec`-Objekt, das Verschlüsselungslaufzeitoptionen enthält.

   Die `encryptPDFUsingPassword`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. `com.adobe.idp.Document` Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `encryptPDFUsingPassword`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verschlüsseln eines PDF-Dokuments mit der Webdienst-API {#encrypting-a-pdf-document-using-the-web-service-api}

Verschlüsseln eines PDF-Dokuments mit einem Kennwort mithilfe der Verschlüsselungs-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument verschlüsseln

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines mit einem Kennwort verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB`-Datenmember des Objekts `MTOM` zuweisen.

1. Legen Sie Optionen für die Verschlüsselungslaufzeit fest.

   * Erstellen Sie ein Objekt `PasswordEncryptionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die zu verschlüsselnden PDF-Dokument-Ressourcen an, indem Sie dem `PasswordEncryptionOptionSpec`-Datenmember des Objekts `encryptOption` einen `PasswordEncryptionOption`-Auflistung-Wert zuweisen. Um die gesamte PDF-Datei einschließlich der zugehörigen Metadaten und Anlagen zu verschlüsseln, weisen Sie `PasswordEncryptionOption.ALL` diesem Datenmember zu.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie dem `PasswordEncryptionOptionSpec`-Datenmember des Objekts `compatability` den Wert `PasswordEncryptionCompatability` der Auflistung zuweisen. Weisen Sie diesem Datenmember beispielsweise `PasswordEncryptionCompatability.ACRO_7` zu.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer das verschlüsselte PDF-Dokument öffnen kann, indem Sie dem `PasswordEncryptionOptionSpec`-Datenmember des Objekts `documentOpenPassword` einen Zeichenfolgenwert zuweisen, der das Kennwort &quot;open&quot;darstellt.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer die Verschlüsselung aus dem PDF-Dokument entfernen kann, indem er dem `PasswordEncryptionOptionSpec`-Datenmember des Objekts `permissionPassword` einen Zeichenfolgenwert zuweist, der das Übergeordnet-Kennwort darstellt.

1. hinzufügen das Kennwort.

   Verschlüsseln Sie das PDF-Dokument, indem Sie die `EncryptionServiceClient`-Objektmethode `encryptPDFUsingPassword` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Dokument enthält, das mit dem Kennwort verschlüsselt werden soll.
   * Das `PasswordEncryptionOptionSpec`-Objekt, das Verschlüsselungslaufzeitoptionen enthält.

   Die `encryptPDFUsingPassword`-Methode gibt ein `BLOB`-Objekt zurück, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des geschützten PDF-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `encryptPDFUsingPassword`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-Dokumente mit Zertifikaten {#encrypting-pdf-documents-with-certificates} verschlüsseln

Zertifikatbasierte Verschlüsselung ermöglicht die Verschlüsselung eines Dokuments für bestimmte Empfänger mithilfe öffentlicher Schlüsseltechnologien. Verschiedene Empfänger können unterschiedliche Berechtigungen für das Dokument erhalten. Viele Aspekte der Verschlüsselung werden durch die Technologie öffentlicher Schlüssel möglich gemacht. Ein Algorithmus wird verwendet, um zwei große Zahlen, die die folgenden Eigenschaften aufweisen, zu generieren, die als *Schlüssel* bezeichnet werden:

* Ein Schlüssel wird zum Verschlüsseln eines Satzes von Daten verwendet. Danach kann nur der andere Schlüssel zum Entschlüsseln der Daten verwendet werden.
* Es ist unmöglich, einen Schlüssel vom anderen zu unterscheiden.

Einer der Schlüssel dient als privater Schlüssel des Benutzers. Wichtig ist, dass nur der Benutzer Zugriff auf diesen Schlüssel hat. Der andere Schlüssel ist der öffentliche Schlüssel des Benutzers, der für andere freigegeben werden kann.

Ein Zertifikat mit öffentlichem Schlüssel enthält den öffentlichen Schlüssel eines Benutzers und Identifizierungsinformationen. Das X.509-Format dient zum Speichern von Zertifikaten. Zertifikate werden meist von einer Zertifizierungsstelle ausgestellt und digital signiert, bei der es sich um eine anerkannte Instanz handelt, die ein Maß an Vertrauen in die Gültigkeit des Zertifikats ermöglicht. Zertifikate haben ein Ablaufdatum, nach dem sie nicht mehr gültig sind. Darüber hinaus liefern Zertifikatsperrlisten Informationen zu Zertifikaten, die vor ihrem Ablaufdatum gesperrt wurden. Zertifikatsperrlisten werden regelmäßig von Zertifizierungsstellen veröffentlicht. Der Sperrstatus eines Zertifikats kann auch mittels des Online-Zertifikatstatusprotokolls (Online Certificate Status Protocol, OCSP) über das Netzwerk abgerufen werden.

>[!NOTE]
>
>Wenn Sie ein verschlüsseltes PDF-Dokument in das AEM Forms-Repository hochladen, kann es das PDF-Dokument nicht entschlüsseln und den XDP-Inhalt extrahieren. Es wird empfohlen, ein Dokument vor dem Hochladen in das AEM Forms-Repository nicht zu verschlüsseln. (Siehe [Schreibressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument mit einem Zertifikat verschlüsseln können, müssen Sie sicherstellen, dass das Zertifikat AEM Forms hinzugefügt wird. Ein Zertifikat wird mithilfe von Administration Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Berechtigungen mithilfe der Trust Manager-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api) importieren.)

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Encryption Client-API-Objekt.
1. PDF-Dokument verschlüsseln
1. Verweisen Sie auf das Zertifikat.
1. Legen Sie Optionen für die Verschlüsselungslaufzeit fest.
1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Client-API-Objekts**

Um einen Encryption-Dienstvorgang programmgesteuert durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**PDF-Dokument zum Verschlüsseln abrufen**

Zum Verschlüsseln müssen Sie ein unverschlüsseltes PDF-Dokument abrufen. Wenn Sie versuchen, ein bereits verschlüsseltes PDF-Dokument zu schützen, wird eine Ausnahme ausgelöst.

**Referenz des Zertifikats**

Um ein PDF-Dokument mit einem Zertifikat zu verschlüsseln, verweisen Sie auf ein Zertifikat, das zum Verschlüsseln eines PDF-Dokuments verwendet wird. Das Zertifikat ist eine .cer-Datei, eine .crt-Datei oder eine .pem-Datei. Eine PKCS#12-Datei wird verwendet, um private Schlüssel mit entsprechenden Zertifikaten zu speichern.

Geben Sie beim Verschlüsseln eines PDF-Dokuments mit einem Zertifikat die Berechtigungen an, die mit dem gesicherten Dokument verknüpft sind. Durch Angabe von Berechtigungen können Sie steuern, welche Aktionen ein Benutzer ausführen kann, der ein zertifikatverschlüsseltes PDF-Dokument öffnet.

**Festlegen von Optionen für die Verschlüsselungslaufzeit**

Geben Sie die zu verschlüsselnden PDF-Dokument-Ressourcen an. Sie können das gesamte PDF-Dokument, alles außer den Metadaten des Dokuments oder nur die Anlagen des Dokuments verschlüsseln.

**Erstellen eines zertifikatverschlüsselten PDF-Dokuments**

Nachdem Sie ein nicht geschütztes PDF-Dokument abgerufen, auf das Zertifikat verwiesen und Laufzeitoptionen festgelegt haben, können Sie ein zertifikatverschlüsseltes PDF-Dokument erstellen. Nachdem das PDF-Dokument verschlüsselt wurde, benötigen Sie den entsprechenden öffentlichen Schlüssel zum Entschlüsseln.

**Verschlüsseltes PDF-Dokument als PDF-Datei speichern**

Sie können das verschlüsselte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-java-api)

[Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Webdienst-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-Dokumente mit einem Kennwort verschlüsseln](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API {#encrypt-a-pdf-document-with-a-certificate-using-the-java-api}

Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Verschlüsselungs-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien, wie z. B. &quot;adobe-cryption-client.jar&quot;, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument verschlüsseln

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu verschlüsselnde PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Verweisen Sie auf das Zertifikat.

   * Erstellen Sie ein `java.util.List`-Objekt, das Berechtigungsinformationen mithilfe seines Konstruktors speichert.
   * Geben Sie die mit dem verschlüsselten Dokument verknüpfte Berechtigung an, indem Sie die `add`-Methode des Objekts aufrufen und einen `CertificateEncryptionPermissions`-Auflistung-Wert übergeben, der die Berechtigungen darstellt, die dem Benutzer erteilt werden, der das geschützte PDF-Dokument öffnet. `java.util.List` Um beispielsweise alle Berechtigungen anzugeben, übergeben Sie `CertificateEncryptionPermissions.PKI_ALL_PERM`.
   * Erstellen Sie ein Objekt `Recipient`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das Zertifikat darstellt, mit dem das PDF-Dokument mithilfe des Konstruktors verschlüsselt wird, und übergeben Sie einen Zeichenfolgenwert, der den Speicherort des Zertifikats angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie den Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben, das das Zertifikat darstellt.
   * Rufen Sie die `setX509Cert`-Methode des Objekts auf und übergeben Sie das `com.adobe.idp.Document`-Objekt, das das Zertifikat enthält. `Recipient` (Darüber hinaus kann das `Recipient`Objekt einen TrustStore-Zertifikatalias oder eine LDAP-URL als Zertifikatquelle haben.)
   * Erstellen Sie ein `CertificateEncryptionIdentity`-Objekt, das Berechtigungs- und Zertifikatinformationen mithilfe seines Konstruktors speichert.
   * Rufen Sie die `setPerms`-Methode des Objekts auf und übergeben Sie das `java.util.List`-Objekt, das Berechtigungsinformationen speichert.`CertificateEncryptionIdentity`
   * Rufen Sie die `setRecipient`-Methode des Objekts auf und übergeben Sie das `Recipient`-Objekt, das Zertifikatsinformationen speichert.`CertificateEncryptionIdentity`
   * Erstellen Sie ein `java.util.List`-Objekt, das Zertifikatinformationen mithilfe des Konstruktors speichert.
   * Rufen Sie die add-Methode des Objekts `java.util.List` auf und übergeben Sie das `CertificateEncryptionIdentity`-Objekt. (Dieses `java.util.List`-Objekt wird als Parameter an die `encryptPDFUsingCertificates`-Methode übergeben.)

1. Legen Sie Optionen für die Verschlüsselungslaufzeit fest.

   * Erstellen Sie ein `CertificateEncryptionOptionSpec`-Objekt, indem Sie den Konstruktor aufrufen.
   * Geben Sie die zu verschlüsselnden PDF-Dokument-Ressourcen an, indem Sie die `setOption`-Methode des Objekts aufrufen und einen `CertificateEncryptionOption`-Auflistung-Wert übergeben, der die zu verschlüsselnden Dokumente angibt. `CertificateEncryptionOptionSpec` Um beispielsweise das gesamte PDF-Dokument einschließlich der zugehörigen Metadaten und Anlagen zu verschlüsseln, geben Sie `CertificateEncryptionOption.ALL` an.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie die `CertificateEncryptionOptionSpec`-Objektmethode `setCompat` aufrufen und einen `CertificateEncryptionCompatibility`-Auflistung-Wert übergeben, der die Acrobat-Kompatibilitätsstufe angibt. Sie können beispielsweise `CertificateEncryptionCompatibility.ACRO_7` angeben.

1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.

   Verschlüsseln Sie das PDF-Dokument mit einem Zertifikat, indem Sie die `encryptPDFUsingCertificates`-Methode des `EncryptionServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das zu verschlüsselnde PDF-Dokument enthält.
   * Das `java.util.List`-Objekt, das Zertifikatinformationen speichert.
   * Das `CertificateEncryptionOptionSpec`-Objekt, das Verschlüsselungslaufzeitoptionen enthält.

   Die `encryptPDFUsingCertificates`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein zertifikatverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. `com.adobe.idp.Document` Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `encryptPDFUsingCertificates`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Webdienst-API {#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api}

Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Verschlüsselungs-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument verschlüsseln

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das mit einem Zertifikat verschlüsselt ist.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie seine `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Verweisen Sie auf das Zertifikat.

   * Erstellen Sie ein Objekt `Recipient`, indem Sie den Konstruktor verwenden. Dieses Objekt speichert Zertifikatsinformationen.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt speichert das Zertifikat, das das PDF-Dokument verschlüsselt.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Zertifikats und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB`-Datenmember des Objekts `MTOM` zuweisen.
   * Weisen Sie das `BLOB`-Objekt, das das Zertifikat speichert, dem `Recipient`-Datenmember des Objekts `x509Cert` zu.
   * Erstellen Sie ein `CertificateEncryptionIdentity`-Objekt, das Zertifikatinformationen mithilfe des Konstruktors speichert.
   * Weisen Sie das `Recipient`-Objekt, das das Zertifikat speichert, dem Empfänger-Datenmember des Objekts `CertificateEncryptionIdentity`zu.
   * Erstellen Sie ein `Object`-Array und weisen Sie das `CertificateEncryptionIdentity`-Objekt dem ersten Element des `Object`-Arrays zu. Dieses `Object`-Array wird als Parameter an die `encryptPDFUsingCertificates`-Methode übergeben.

1. Legen Sie Optionen für die Verschlüsselungslaufzeit fest.

   * Erstellen Sie ein Objekt `CertificateEncryptionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die zu verschlüsselnden PDF-Dokument-Ressourcen an, indem Sie dem `CertificateEncryptionOptionSpec`-Datenmember des Objekts `option` einen `CertificateEncryptionOption`-Auflistung-Wert zuweisen. Um das gesamte PDF-Dokument einschließlich seiner Metadaten und Anlagen zu verschlüsseln, weisen Sie diesem Datenmember `CertificateEncryptionOption.ALL` zu.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie dem `CertificateEncryptionOptionSpec`-Datenmember des Objekts `compat` den Wert `CertificateEncryptionCompatibility` der Auflistung zuweisen. Weisen Sie diesem Datenmember beispielsweise `CertificateEncryptionCompatibility.ACRO_7` zu.

1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.

   Verschlüsseln Sie das PDF-Dokument mit einem Zertifikat, indem Sie die `encryptPDFUsingCertificates`-Methode des `EncryptionServiceService`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das zu verschlüsselnde PDF-Dokument enthält.
   * Das `Object`-Array, das Zertifikatinformationen speichert.
   * Das `CertificateEncryptionOptionSpec`-Objekt, das Verschlüsselungslaufzeitoptionen enthält.

   Die `encryptPDFUsingCertificates`-Methode gibt ein `BLOB`-Objekt zurück, das ein zertifikatverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des geschützten PDF-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB`-Objekts speichert, das von der `encryptPDFUsingCertificates`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Zertifikatbasierte Verschlüsselung {#removing-certificate-based-encryption} entfernen

Zertifikatbasierte Verschlüsselung kann aus einem PDF-Dokument entfernt werden, damit Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können. Zum Entfernen der Verschlüsselung aus einem PDF-Dokument, das mit einem Zertifikat verschlüsselt ist, muss auf einen öffentlichen Schlüssel verwiesen werden. Nachdem die Verschlüsselung aus einem PDF-Dokument entfernt wurde, ist sie nicht mehr sicher.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

So entfernen Sie die zertifikatbasierte Verschlüsselung aus einem PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Verschlüsselungsdienstclient.
1. Verschlüsseln Sie das PDF-Dokument.
1. Entfernen Sie die Verschlüsselung.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungsdienstclients**

Um einen Encryption-Dienstvorgang programmgesteuert durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Zum Entfernen der zertifikatbasierten Verschlüsselung benötigen Sie ein verschlüsseltes PDF-Dokument. Wenn Sie versuchen, eine Verschlüsselung aus einem nicht verschlüsselten PDF-Dokument zu entfernen, wird eine Ausnahme ausgelöst. Wenn Sie versuchen, die zertifikatbasierte Verschlüsselung aus einem kennwortverschlüsselten Dokument zu entfernen, wird eine Ausnahme ausgelöst.

**Verschlüsselung entfernen**

Zum Entfernen der zertifikatbasierten Verschlüsselung aus einem verschlüsselten PDF-Dokument benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch den privaten Schlüssel, der dem zum Verschlüsseln des PDF-Dokuments verwendeten Schlüssel entspricht. Der Aliaswert des privaten Schlüssels wird beim Entfernen der zertifikatbasierten Verschlüsselung aus einem verschlüsselten PDF-Dokument angegeben. Informationen zum öffentlichen Schlüssel finden Sie unter [PDF-Dokumente mit Zertifikaten verschlüsseln](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).

>[!NOTE]
>
>Ein privater Schlüssel wird im AEM Forms Trust Store gespeichert. Wenn dort ein Zertifikat platziert wird, wird ein Aliaswert angegeben.

**PDF-Dokument speichern**

Nachdem die zertifikatbasierte Verschlüsselung aus einem verschlüsselten PDF-Dokument entfernt wurde, können Sie das PDF-Dokument als PDF-Datei speichern. Benutzer können das PDF-Dokument in Adobe Reader oder Acrobat öffnen.

**Siehe auch**

[Zertifikatbasierte Verschlüsselung mit der Java-API entfernen](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-java-api)

[Zertifikatbasierte Verschlüsselung mithilfe der Webdienst-API entfernen](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Zertifikatbasierte Verschlüsselung mit der Java-API {#remove-certificate-based-encryption-using-the-java-api} entfernen

Zertifikatbasierte Verschlüsselung aus einem PDF-Dokument mithilfe der Verschlüsselungs-API (Java) entfernen:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien, wie z. B. &quot;adobe-cryption-client.jar&quot;, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienstclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verschlüsseln Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des verschlüsselten PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie die Verschlüsselung.

   Entfernen Sie die zertifikatbasierte Verschlüsselung aus dem PDF-Dokument, indem Sie die `removePDFCertificateSecurity`-Methode des Objekts aufrufen und die folgenden Werte übergeben:`EncryptionServiceClient`

   * Das `com.adobe.idp.Document`-Objekt, das das verschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Aliasnamen des privaten Schlüssels angibt, der dem zum Verschlüsseln des PDFf-Dokuments verwendeten Schlüssel entspricht.

   Die `removePDFCertificateSecurity`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein ungeschütztes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. `com.adobe.idp.Document` Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `removePDFCredentialSecurity`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Zertifikatbasierte Verschlüsselung mit der Java-API entfernen](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zertifikatbasierte Verschlüsselung mithilfe der Webdienst-API {#remove-certificate-based-encryption-using-the-web-service-api} entfernen

Zertifikatbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Webdienst) entfernen:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienstclient.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Verschlüsseln Sie das PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB`-Datenmember des Objekts `MTOM` zuweisen.

1. Entfernen Sie die Verschlüsselung.

   Rufen Sie die `removePDFCertificateSecurity`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`EncryptionServiceClient`

   * Das `BLOB`-Objekt, das Dateistream-Daten enthält, die ein verschlüsseltes PDF-Dokument darstellen.
   * Ein Zeichenfolgenwert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem zum Verschlüsseln des PDFf-Dokuments verwendeten privaten Schlüssel entspricht.

   Die `removePDFCredentialSecurity`-Methode gibt ein `BLOB`-Objekt zurück, das ein ungeschütztes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB`-Objekts speichert, das von der `removePDFPasswordSecurity`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Kennwortverschlüsselung {#removing-password-encryption} entfernen

Die kennwortbasierte Verschlüsselung kann aus einem PDF-Dokument entfernt werden, sodass Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können, ohne ein Kennwort angeben zu müssen. Nachdem die kennwortbasierte Verschlüsselung aus einem PDF-Dokument entfernt wurde, ist das Dokument nicht mehr sicher.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So entfernen Sie die kennwortbasierte Verschlüsselung aus einem PDF-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie einen Verschlüsselungsdienstclient.
1. Verschlüsseln Sie das PDF-Dokument.
1. Entfernen Sie das Kennwort.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

**Erstellen eines Verschlüsselungsdienstclients**

Um einen Encryption-Dienstvorgang programmgesteuert durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Zum Entfernen der kennwortbasierten Verschlüsselung benötigen Sie ein verschlüsseltes PDF-Dokument. Wenn Sie versuchen, eine Verschlüsselung aus einem nicht verschlüsselten PDF-Dokument zu entfernen, wird eine Ausnahme ausgelöst.

**Kennwort entfernen**

Zum Entfernen der kennwortbasierten Verschlüsselung aus einem verschlüsselten PDF-Dokument benötigen Sie ein verschlüsseltes PDF-Dokument und einen Übergeordnet-Kennwortwert, mit dem die Verschlüsselung aus dem PDF-Dokument entfernt wird. Das Kennwort zum Öffnen eines kennwortverschlüsselten PDF-Dokuments kann nicht zum Entfernen der Verschlüsselung verwendet werden. Wenn das PDF-Dokument mit einem Kennwort verschlüsselt ist, wird ein Übergeordnet-Kennwort angegeben. (Siehe [PDF-Dokumente mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password) verschlüsseln.)

**PDF-Dokument speichern**

Nachdem der Encryption-Dienst die kennwortbasierte Verschlüsselung aus einem PDF-Dokument entfernt hat, können Sie das PDF-Dokument als PDF-Datei speichern. Benutzer können das PDF-Dokument in Adobe Reader oder Acrobat öffnen, ohne ein Kennwort anzugeben.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-Dokumente mit einem Kennwort verschlüsseln](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Kennwortbasierte Verschlüsselung mit der Java-API {#remove-password-based-encryption-using-the-java-api} entfernen

Entfernen Sie die kennwortbasierte Verschlüsselung aus einem PDF-Dokument mithilfe der Verschlüsselungs-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien, wie z. B. &quot;adobe-cryption-client.jar&quot;, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienstclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verschlüsseln Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie das Kennwort.

   Entfernen Sie die kennwortbasierte Verschlüsselung aus dem PDF-Dokument, indem Sie die `removePDFPasswordSecurity`-Methode des Objekts aufrufen und die folgenden Werte übergeben:`EncryptionServiceClient`

   * Ein `com.adobe.idp.Document`-Objekt, das das verschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Übergeordnet-Kennwortwert angibt, der zum Entfernen der Verschlüsselung aus dem PDF-Dokument verwendet wird.

   Die `removePDFPasswordSecurity`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein ungeschütztes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. `com.adobe.idp.Document` Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `removePDFPasswordSecurity`-Methode zurückgegeben wurde.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Kennwortbasierte Verschlüsselung mit der Java-API entfernen](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

### Entfernen Sie die kennwortbasierte Verschlüsselung mithilfe der Webdienst-API {#remove-password-based-encryption-using-the-web-service-api}

Entfernen Sie die kennwortbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienstclient.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Verschlüsseln Sie das PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines kennwortverschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB`-Datenmember des Objekts `MTOM` zuweisen.

1. Entfernen Sie das Kennwort.

   Rufen Sie die `removePDFPasswordSecurity`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`EncryptionServiceService`

   * Das `BLOB`-Objekt, das Dateistream-Daten enthält, die ein verschlüsseltes PDF-Dokument darstellen.
   * Ein Zeichenfolgenwert, der den Kennwortwert angibt, der zum Entfernen der Verschlüsselung aus dem PDF-Dokument verwendet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Die `removePDFPasswordSecurity`-Methode gibt ein `BLOB`-Objekt zurück, das ein ungeschütztes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB`-Objekts speichert, das von der `removePDFPasswordSecurity`-Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB`-Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie den Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write`-Methode des Objekts aufrufen und das Bytearray übergeben.`System.IO.BinaryWriter`

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entsperren verschlüsselter PDF-Dokumente {#unlocking-encrypted-pdf-documents}

Ein kennwortverschlüsseltes oder zertifikatverschlüsseltes PDF-Dokument muss entsperrt werden, bevor ein anderer AEM Forms-Vorgang darauf ausgeführt werden kann. Wenn Sie versuchen, einen Vorgang mit einem verschlüsselten PDF-Dokument auszuführen, wird eine Ausnahme generiert. Nachdem Sie ein verschlüsseltes PDF-Dokument entsperrt haben, können Sie einen oder mehrere Vorgänge daran durchführen. Diese Vorgänge können zu anderen Diensten gehören, z. B. dem Acrobat Reader DC Extensions-Dienst.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

So entsperren Sie ein verschlüsseltes PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Verschlüsselungsdienstclient.
1. Verschlüsseln Sie das PDF-Dokument.
1. Entsperren Sie das Dokument.
1. Führen Sie einen AEM Forms-Vorgang durch.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungsdienstclients**

Um einen Encryption-Dienstvorgang programmgesteuert durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um die Sperre aufzuheben. Wenn Sie versuchen, ein nicht verschlüsseltes PDF-Dokument zu entsperren, wird eine Ausnahme ausgelöst.

**Entsperren des Dokuments**

Zum Entsperren eines kennwortverschlüsselten PDF-Dokuments benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch einen Kennwortwert, mit dem ein kennwortverschlüsseltes PDF-Dokument geöffnet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben. (Siehe [PDF-Dokumente mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password) verschlüsseln.)

Zum Entsperren eines zertifikatverschlüsselten PDF-Dokuments benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch den Aliaswert des öffentlichen Schlüssels, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wurde.

**Durchführen eines AEM Forms-Vorgangs**

Nachdem ein verschlüsseltes PDF-Dokument entsperrt wurde, können Sie einen anderen Dienstvorgang durchführen, z. B. Verwendungsrechte darauf anwenden. Dieser Vorgang gehört zum Acrobat Reader DC Extensions-Dienst.

**Siehe auch**

[Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-java-api)

[Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Webdienst-API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API {#unlock-an-encrypted-pdf-document-using-the-java-api}

Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Verschlüsselungs-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien, wie z. B. &quot;adobe-cryption-client.jar&quot;, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienstclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verschlüsseln Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das verschlüsselte PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des verschlüsselten PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entsperren Sie das Dokument.

   Entsperren Sie ein verschlüsseltes PDF-Dokument, indem Sie die `EncryptionServiceClient`- oder `unlockPDFUsingCredential`-Objektmethode aufrufen.`unlockPDFUsingPassword`

   Um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die `unlockPDFUsingPassword`-Methode auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das kennwortverschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Kennwortwert angibt, mit dem ein kennwortverschlüsseltes PDF-Dokument geöffnet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Um ein mit einem Zertifikat verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die `unlockPDFUsingCredential`-Methode auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das das zertifikatverschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem zum Verschlüsseln des PDF-Dokuments verwendeten privaten Schlüssel entspricht.

   Die Methoden `unlockPDFUsingPassword` und `unlockPDFUsingCredential` geben jeweils ein `com.adobe.idp.Document`-Objekt zurück, das Sie zur Durchführung eines Vorgangs an eine andere AEM Forms Java-Methode übergeben.

1. Führen Sie einen AEM Forms-Vorgang durch.

   Führen Sie einen AEM Forms-Vorgang für das entsperrte PDF-Dokument aus, um Ihre Geschäftsanforderungen zu erfüllen. Wenn Sie beispielsweise Verwendungsrechte auf ein nicht gesperrtes PDF-Dokument anwenden möchten, übergeben Sie das `com.adobe.idp.Document`-Objekt, das von der `unlockPDFUsingPassword`- oder `unlockPDFUsingCredential`-Methode zurückgegeben wurde, an die `ReaderExtensionsServiceClient`-Objektmethode `applyUsageRights`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api) (SOAP-Modus)

[Verwendungsrechte auf PDF-Dokumente anwenden](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Webdienst-API {#unlock-an-encrypted-pdf-document-using-the-web-service-api}

Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Verschlüsselungs-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienstclient.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Erstellen Sie ein verschlüsseltes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB`-Datenmember des Objekts `MTOM` zuweisen.

1. Entsperren Sie das Dokument.

   Entsperren Sie ein verschlüsseltes PDF-Dokument, indem Sie die `EncryptionServiceClient`- oder `unlockPDFUsingCredential`-Objektmethode aufrufen.`unlockPDFUsingPassword`

   Um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die `unlockPDFUsingPassword`-Methode auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das kennwortverschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Kennwortwert angibt, mit dem ein kennwortverschlüsseltes PDF-Dokument geöffnet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Um ein mit einem Zertifikat verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die `unlockPDFUsingCredential`-Methode auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das das zertifikatverschlüsselte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem zum Verschlüsseln des PDFf-Dokuments verwendeten privaten Schlüssel entspricht.

   Die Methoden `unlockPDFUsingPassword` und `unlockPDFUsingCredential` geben jeweils ein `com.adobe.idp.Document`-Objekt zurück, das Sie zur Durchführung eines Vorgangs an eine andere AEM Forms-Methode übergeben.

1. Führen Sie einen AEM Forms-Vorgang durch.

   Führen Sie einen AEM Forms-Vorgang für das entsperrte PDF-Dokument aus, um Ihre Geschäftsanforderungen zu erfüllen. Wenn Sie beispielsweise Verwendungsrechte auf das nicht gesperrte PDF-Dokument anwenden möchten, übergeben Sie das `BLOB`-Objekt, das von der `unlockPDFUsingPassword`- oder `unlockPDFUsingCredential`-Methode zurückgegeben wurde, an die `ReaderExtensionsServiceClient`-Objektmethode `applyUsageRights`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Ermitteln des Verschlüsselungstyps {#determining-encryption-type}

Sie können den Verschlüsselungstyp, der ein PDF-Dokument schützt, mithilfe der Java Encryption Service API oder der Web Service Encryption Service API programmgesteuert bestimmen. Manchmal ist es notwendig, dynamisch zu bestimmen, ob ein PDF-Dokument verschlüsselt ist und, falls ja, der Verschlüsselungstyp. Sie können beispielsweise festlegen, ob ein PDF-Dokument mit einer kennwortbasierten Verschlüsselung oder einer Rights Management-Richtlinie geschützt ist.

Ein PDF-Dokument kann durch die folgenden Verschlüsselungstypen geschützt werden:

* Kennwortbasierte Verschlüsselung
* Zertifikatbasierte Verschlüsselung
* Eine Richtlinie, die vom Rights Management-Dienst erstellt wird
* Anderer Verschlüsselungstyp

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

So bestimmen Sie den Verschlüsselungstyp, der ein PDF-Dokument schützt:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Verschlüsselungsdienstclient.
1. Verschlüsseln Sie das PDF-Dokument.
1. Ermitteln Sie den Verschlüsselungstyp.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Dienstclient erstellen**

Um einen Encryption-Dienstvorgang programmgesteuert durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service API verwenden, erstellen Sie ein `EncrytionServiceClient`-Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie ein `EncryptionServiceService`-Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein PDF-Dokument abrufen, um den Verschlüsselungstyp zu ermitteln, der ihn schützt.

**Ermitteln des Verschlüsselungstyps**

Sie können den Verschlüsselungstyp bestimmen, der zum Schutz eines PDF-Dokuments dient. Wenn das PDF-Dokument nicht geschützt ist, informiert Sie der Encryption-Dienst darüber, dass das PDF-Dokument nicht geschützt ist.

**Siehe auch**

[Ermitteln des Verschlüsselungstyps mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-java-api)

[Ermitteln des Verschlüsselungstyps mithilfe der Webdienst-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Schutz von Dokumenten mit Richtlinien](/help/forms/developing/protecting-documents-policies.md#protecting-documents-with-policies)

### Ermitteln des Verschlüsselungstyps mithilfe der Java-API {#determine-the-encryption-type-using-the-java-api}

Bestimmen Sie mithilfe der Verschlüsselungs-API (Java) den Verschlüsselungstyp, der ein PDF-Dokument schützt:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien, wie z. B. &quot;adobe-cryption-client.jar&quot;, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Dienstclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `EncryptionServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verschlüsseln Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Ermitteln Sie den Verschlüsselungstyp.

   * Ermitteln Sie den Verschlüsselungstyp, indem Sie die `EncryptionServiceClient`-Objektmethode `getPDFEncryption` aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument enthält. Diese Methode gibt ein `EncryptionTypeResult`-Objekt zurück.
   * Rufen Sie die `EncryptionTypeResult`-Methode des Objekts `getEncryptionType` auf. Diese Methode gibt einen Enum-Wert von `EncryptionType` zurück, der den Verschlüsselungstyp angibt. Wenn das PDF-Dokument beispielsweise mit einer kennwortbasierten Verschlüsselung geschützt ist, gibt diese Methode `EncryptionType.PASSWORD` zurück.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Ermitteln des Verschlüsselungstyps mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ermitteln des Verschlüsselungstyps mithilfe der Webdienst-API {#determine-the-encryption-type-using-the-web-service-api}

Bestimmen Sie mithilfe der Verschlüsselungs-API (Webdienst) den Verschlüsselungstyp, der ein PDF-Dokument schützt:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Dienstclient.

   * Erstellen Sie ein `EncryptionServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `EncryptionServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `EncryptionServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `EncryptionServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Verschlüsseln Sie das PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream`-Eigenschaft des Objekts `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `Read`-Methode des Objekts aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben.`System.IO.FileStream`
   * Füllen Sie das `BLOB`-Objekt, indem Sie den Inhalt des Byte-Arrays dem `BLOB`-Datenmember des Objekts `MTOM` zuweisen.

1. Ermitteln Sie den Verschlüsselungstyp.

   * Rufen Sie die `getPDFEncryption`-Methode des Objekts auf und übergeben Sie das `BLOB`-Objekt, das das PDF-Dokument enthält. `EncryptionServiceClient` Diese Methode gibt ein `EncryptionTypeResult`-Objekt zurück.
   * Rufen Sie den Wert der Datenmethode `EncryptionTypeResult` des Objekts ab. `encryptionType` Wenn das PDF-Dokument beispielsweise mit einer kennwortbasierten Verschlüsselung geschützt ist, lautet der Wert dieses Datenelements `EncryptionType.PASSWORD`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)