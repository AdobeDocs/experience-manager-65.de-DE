---
title: Arbeiten mit Berechtigungen
seo-title: Arbeiten mit Berechtigungen
description: Importieren Sie Anmeldeinformationen mit der Trust Manager-API und der Java-API nach AEM Forms. Erfahren Sie außerdem, wie Sie Anmeldeinformationen mit der Trust Manager-API und der Java-API löschen.
seo-description: Importieren Sie Anmeldeinformationen mit der Trust Manager-API und der Java-API nach AEM Forms. Erfahren Sie außerdem, wie Sie Anmeldeinformationen mit der Trust Manager-API und der Java-API löschen.
uuid: b794428f-49bf-4a91-bc5f-d855881f4f38
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: bc06d9bd-af6c-47b1-b46f-aab990ef5816
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 11%

---


# Arbeiten mit Berechtigungen {#working-with-credentials}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

**Informationen zum Berechtigungsdienst**

Eine Berechtigung enthält Informationen zu Ihrem privaten Schlüssel, der zum Signieren bzw. Identifizieren von Dokumenten benötigt wird. Ein Zertifikat enthält Informationen zum öffentlichen Schlüssel, den Sie für die Trust Store-Verwaltung konfigurieren. AEM Forms verwendet Zertifikate und Berechtigungen für verschiedene Zwecke:

* Acrobat Reader DC Extensions verwendet eine Berechtigung zur Aktivierung von Adobe Reader-Verwendungsrechten in PDF-Dokumenten. (Siehe [Verwendungsrechte auf PDF-Dokumente anwenden](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).)
* Der Signature-Dienst greift beim Ausführen von Vorgängen wie dem digitalen Signieren von PDF-Dokumenten auf Zertifikate und Berechtigungen zu. (Siehe [Digitales Signieren von PDF-Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

Sie können mit der Trust Manager Java-API programmgesteuert mit dem Berechtigungsdienst interagieren. Sie können die folgenden Aufgaben durchführen:

* [Berechtigungen mithilfe der Trust Manager-API importieren](credentials.md#importing-credentials-by-using-the-trust-manager-api)
* [Löschen von Berechtigungen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

>[!NOTE]
>
>Sie können Zertifikate auch über Administration Console importieren und löschen. (Siehe [Administration-Hilfe.](https://www.adobe.com/go/learn_aemforms_admin_63))

## Berechtigungen mithilfe der Trust Manager-API {#importing-credentials-by-using-the-trust-manager-api} importieren

Sie können eine Berechtigung programmgesteuert mit der Trust Manager-API in AEM Forms importieren. Sie können beispielsweise eine Berechtigung importieren, mit der ein PDF-Dokument signiert wird. (Siehe [Digitales Signieren von PDF-Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)).

Beim Importieren einer Berechtigung geben Sie einen Alias für die Berechtigung an. Der Alias wird verwendet, um einen Forms-Vorgang durchzuführen, für den eine Berechtigung erforderlich ist. Nach dem Import kann eine Berechtigung in Administration Console angezeigt werden, wie in der folgenden Abbildung dargestellt. Beachten Sie, dass der Alias für die Berechtigung *Secure* lautet.

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
* adobe-utilities.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Berechtigungsdienstclient erstellen**

Bevor Sie eine Berechtigung programmgesteuert in AEM Forms importieren können, erstellen Sie einen Berechtigungsdienstclient. Weitere Informationen finden Sie unter [Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenz zur Berechtigung**

Referenzieren Sie eine Berechtigung, die Sie in AEM Forms importieren möchten. Der mit diesem Abschnitt verknüpfte Quick-Beginn verweist auf eine P12-Datei im Dateisystem.

**Durchführen des Importvorgangs**

Nachdem Sie auf die Berechtigung verwiesen haben, importieren Sie die Berechtigung in AEM Forms. Wenn die Berechtigung nicht erfolgreich importiert wurde, wird eine Ausnahme ausgelöst. Beim Importieren einer Berechtigung geben Sie einen Alias für die Berechtigung an.

**Siehe auch**

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API-Beginn für den Berechtigungsdienst](/help/forms/developing/credential-service-java-api-quick.md#credential-service-java-api-quick-start-soap)

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
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, das die Berechtigung mithilfe des Konstruktors `com.adobe.idp.Document` speichert. Übergeben Sie das `java.io.FileInputStream`-Objekt, das die Berechtigung enthält, an den Konstruktor.

1. Durchführen des Importvorgangs

   * Erstellen Sie ein String-Array, das ein Element enthält. Weisen Sie dem Element den Wert `truststore.usage.type.sign` zu.
   * Rufen Sie die `importCredential`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`CredentialServiceClient`

      * Ein Zeichenfolgenwert, der den Aliaswert der Berechtigung angibt.
      * Die `com.adobe.idp.Document`-Instanz, in der die Berechtigung gespeichert wird.
      * Ein Zeichenfolgenwert, der das mit der Berechtigung verknüpfte Kennwort angibt.
      * Das Zeichenfolgenarray, das den Nutzungswert enthält. Sie können diesen Wert beispielsweise `truststore.usage.type.sign` angeben. Um eine Reader Extension-Berechtigung zu importieren, geben Sie `truststore.usage.type.lcre` an.

**Siehe auch**

[Berechtigungen mithilfe der Trust Manager-API importieren](credentials.md#importing-credentials-by-using-the-trust-manager-api)

[Quick Beginn (SOAP-Modus): Importieren von Berechtigungen mit der Java-API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-importing-credentials-using-the-java-api)

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
* adobe-utilities.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Berechtigungsdienstclient erstellen**

Bevor Sie eine Berechtigung programmgesteuert löschen können, erstellen Sie einen Data Integration-Dienstclient. Beim Erstellen eines Dienstclients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Weitere Informationen finden Sie unter [Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Löschvorgang durchführen**

Um eine Berechtigung zu löschen, geben Sie den Alias an, der der Berechtigung entspricht. Wenn Sie einen Alias angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

### Löschen von Berechtigungen mit der Java-API {#deleting-credentials-using-the-java-api}

Eine Berechtigung aus AEM Forms mithilfe der Trust Manager-API (Java) löschen:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-truststore-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Berechtigungsdienstclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `CredentialServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Löschvorgang durchführen

   Rufen Sie die `deleteCredential`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Aliaswert angibt.`CredentialServiceClient`

**Siehe auch**

[Löschen von Berechtigungen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

[Quick Beginn (SOAP-Modus): Löschen von Berechtigungen mit der Java-API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-deleting-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
