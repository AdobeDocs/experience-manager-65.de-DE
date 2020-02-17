---
title: Arbeiten mit Berechtigungen
seo-title: Arbeiten mit Berechtigungen
description: 'null'
seo-description: 'null'
uuid: b794428f-49bf-4a91-bc5f-d855881f4f38
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: bc06d9bd-af6c-47b1-b46f-aab990ef5816
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Arbeiten mit Berechtigungen {#working-with-credentials}

**Informationen zum Berechtigungsdienst**

Eine Berechtigung enthält Informationen zu Ihrem privaten Schlüssel, der zum Signieren bzw. Identifizieren von Dokumenten benötigt wird. Ein Zertifikat enthält Informationen zum öffentlichen Schlüssel, den Sie für die Trust Store-Verwaltung konfigurieren. AEM Forms verwendet Zertifikate und Berechtigungen für verschiedene Zwecke:

* Acrobat Reader DC Extensions verwendet eine Berechtigung zur Aktivierung von Adobe Reader-Verwendungsrechten in PDF-Dokumenten. (See [Applying Usage Rights to PDF Documents](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).)
* Der Signature-Dienst greift beim Ausführen von Vorgängen wie dem digitalen Signieren von PDF-Dokumenten auf Zertifikate und Berechtigungen zu. (See [Digitally Signing PDF Documents](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

Sie können mit der Trust Manager Java-API programmgesteuert mit dem Berechtigungsdienst interagieren. Sie können die folgenden Aufgaben ausführen:

* [Berechtigungen mithilfe der Trust Manager-API importieren](credentials.md#importing-credentials-by-using-the-trust-manager-api)
* [Löschen von Berechtigungen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

>[!NOTE]
>
>Sie können Zertifikate auch über Administration Console importieren und löschen. (Siehe [Administration-Hilfe.](https://www.adobe.com/go/learn_aemforms_admin_63))

## Berechtigungen mithilfe der Trust Manager-API importieren {#importing-credentials-by-using-the-trust-manager-api}

Sie können eine Berechtigung programmgesteuert mit der Trust Manager-API in AEM Forms importieren. Sie können beispielsweise eine Berechtigung importieren, mit der ein PDF-Dokument signiert wird. (See [Digitally Signing PDF Documents](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)).

Beim Importieren einer Berechtigung geben Sie einen Alias für die Berechtigung an. Der Alias wird verwendet, um einen Forms-Vorgang durchzuführen, für den eine Berechtigung erforderlich ist. Nach dem Import kann eine Berechtigung in Administration Console angezeigt werden, wie in der folgenden Abbildung dargestellt. Beachten Sie, dass der Alias für die Berechtigung *Secure* ist.

![ww_ww_truststore](assets/ww_ww_truststore.png)

>[!NOTE]
>
>Sie können eine Berechtigung nicht mit Webdiensten in AEM Forms importieren.

### Zusammenfassung der Schritte {#summary-of-steps}

So importieren Sie eine Berechtigung in AEM Forms:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Berechtigungsdienstclient.
1. Verweisen Sie auf die Berechtigung.
1. Führen Sie den Importvorgang durch.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-truststore-client.jar
* adobe-utilities.jar (Erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (Erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Berechtigungsdienstclient erstellen**

Bevor Sie eine Berechtigung programmgesteuert in AEM Forms importieren können, erstellen Sie einen Berechtigungsdienstclient. Weitere Informationen finden Sie unter [Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)festlegen.

**Referenz zur Berechtigung**

Verweisen Sie auf eine Berechtigung, die Sie in AEM Forms importieren möchten. Der Schnellstart in diesem Abschnitt verweist auf eine P12-Datei im Dateisystem.

**Durchführen des Importvorgangs**

Nachdem Sie auf die Berechtigung verwiesen haben, importieren Sie die Berechtigung in AEM Forms. Wenn die Berechtigung nicht erfolgreich importiert wurde, wird eine Ausnahme ausgelöst. Beim Importieren einer Berechtigung geben Sie einen Alias für die Berechtigung an.

**Siehe auch**

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API für den Berechtigungsdienst - Schnellstarts](/help/forms/developing/credential-service-java-api-quick.md#credential-service-java-api-quick-start-soap)

[Löschen von Berechtigungen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

### Importieren von Anmeldeinformationen mit der Java-API {#import-credentials-using-the-java-api}

Importieren Sie eine Berechtigung mit der Trust Manager-API (Java) in AEM Forms:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-truststore-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Berechtigungsdienstclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `CredentialServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenz zur Berechtigung

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der Berechtigung angibt.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, das die Berechtigung mithilfe des `com.adobe.idp.Document` Konstruktors speichert. Übergeben Sie das `java.io.FileInputStream` Objekt, das die Berechtigung enthält, an den Konstruktor.

1. Durchführen des Importvorgangs

   * Erstellen Sie ein String-Array, das ein Element enthält. Weisen Sie dem Element den Wert `truststore.usage.type.sign` zu.
   * Rufen Sie die `CredentialServiceClient` Objektmethode `importCredential` auf und übergeben Sie die folgenden Werte:

      * Ein Zeichenfolgenwert, der den Aliaswert der Berechtigung angibt.
      * Die `com.adobe.idp.Document` Instanz, in der die Berechtigung gespeichert wird.
      * Ein Zeichenfolgenwert, der das mit der Berechtigung verknüpfte Kennwort angibt.
      * Das Zeichenfolgenarray, das den Nutzungswert enthält. Sie können diesen Wert beispielsweise angeben `truststore.usage.type.sign`. Um eine Reader Extension-Berechtigung zu importieren, geben Sie an `truststore.usage.type.lcre`.

**Siehe auch**

[Berechtigungen mithilfe der Trust Manager-API importieren](credentials.md#importing-credentials-by-using-the-trust-manager-api)

[Kurzanleitung (SOAP-Modus): Importieren von Berechtigungen mit der Java-API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-importing-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Löschen von Berechtigungen mithilfe der Trust Manager-API {#deleting-credentials-by-using-the-trust-manager-api}

Sie können eine Berechtigung programmgesteuert mithilfe der Trust Manager-API löschen. Beim Löschen einer Berechtigung geben Sie einen Alias an, der der Berechtigung entspricht. Nach dem Löschen kann eine Berechtigung nicht für einen Vorgang verwendet werden.

>[!NOTE]
>
>Sie können eine Berechtigung nicht mit Webdiensten in AEM Forms löschen.

### Zusammenfassung der Schritte {#summary_of_steps-1}

So löschen Sie eine Berechtigung:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Berechtigungsdienstclient.
1. Führen Sie den Löschvorgang durch.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-truststore-client.jar
* adobe-utilities.jar (Erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (Erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Berechtigungsdienstclient erstellen**

Bevor Sie eine Berechtigung programmgesteuert löschen können, erstellen Sie einen Data Integration-Dienstclient. Beim Erstellen eines Dienstclients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Weitere Informationen finden Sie unter [Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)festlegen.

**Löschvorgang durchführen**

Um eine Berechtigung zu löschen, geben Sie den Alias an, der der Berechtigung entspricht. Wenn Sie einen Alias angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

###  Löschen von Berechtigungen mit der Java-API {#deleting-credentials-using-the-java-api}

Löschen Sie eine Berechtigung aus AEM Forms mithilfe der Trust Manager-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-truststore-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Berechtigungsdienstclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `CredentialServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Löschvorgang durchführen

   Rufen Sie die `CredentialServiceClient` Methode des `deleteCredential` Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Aliaswert angibt.

**Siehe auch**

[Löschen von Berechtigungen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

[Kurzanleitung (SOAP-Modus): Löschen von Berechtigungen mit der Java-API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-deleting-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
