---
title: Arbeiten mit Berechtigungen
description: Importieren Sie Berechtigungen mithilfe der Trust Manager-API und der Java-API in AEM Forms. Erfahren Sie außerdem, wie Sie Berechtigungen mithilfe der Trust Manager-API und der Java-API löschen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 1101c85a-6a90-471d-a7be-8d25765e84bf
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 98%

---

# Arbeiten mit Berechtigungen {#working-with-credentials}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den Berechtigungs-Service**

Eine Berechtigung enthält Informationen zu Ihrem privaten Schlüssel, der zum Signieren bzw. Identifizieren von Dokumenten benötigt wird. Ein Zertifikat enthält Informationen zum öffentlichen Schlüssel, den Sie für die Trust Store-Verwaltung konfigurieren. AEM Forms verwendet Zertifikate und Berechtigungen für mehrere Zwecke:

* Acrobat Reader DC Extensions verwendet eine Berechtigung zur Aktivierung von Adobe Reader-Verwendungsrechten in PDF-Dokumenten. (Siehe [Anwenden von Verwendungsrechten auf PDF-Dokumente](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).)
* Der Signature-Service greift beim Ausführen von Vorgängen wie dem digitalen Signieren von PDF-Dokumenten auf Zertifikate und Berechtigungen zu. (Siehe [Digitales Signieren von PDF-Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

Mithilfe der Java-API von Trust Manager können Sie programmgesteuert mit dem Berechtigungs-Service interagieren. Sie können die folgenden Aufgaben ausführen:

* [Importieren von Berechtigungen mithilfe der Trust Manager-API](credentials.md#importing-credentials-by-using-the-trust-manager-api)
* [Löschen von Berechtigungen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

>[!NOTE]
>
>Sie können Zertifikate auch über Administration-Console importieren bzw. löschen. (Siehe [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63_de).)

## Importieren von Berechtigungen mithilfe der Trust Manager-API {#importing-credentials-by-using-the-trust-manager-api}

Mithilfe der Trust-Manager-API können Sie programmgesteuert eine Berechtigung in AEM Forms importieren. Sie können beispielsweise eine Berechtigung importieren, die zum Signieren eines PDF-Dokuments verwendet wird. (Siehe [Digitales Signieren von PDF-Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

Beim Importieren einer Berechtigung geben Sie einen Alias für die Berechtigung an. Der Alias wird verwendet, um einen Forms-Vorgang auszuführen, für den eine Berechtigung erforderlich ist. Nachdem sie importiert worden ist, kann eine Berechtigung in Administration-Console angezeigt werden, wie in der folgenden Abbildung dargestellt. Beachten Sie, dass der Alias für die Berechtigung *sicher* ist.

![ww_ww_truststore](assets/ww_ww_truststore.png)

>[!NOTE]
>
>Es ist nicht möglich, eine Berechtigung mithilfe von Web-Services in AEM Forms zu importieren.

### Zusammenfassung der Schritte {#summary-of-steps}

Um eine Berechtigung in AEM Forms zu importieren, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client für den Berechtigungs-Service.
1. Verweisen Sie auf die Berechtigung.
1. Führen Sie den Importvorgang durch.

**Schließen Sie Projektdateien ein**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-truststore-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Weitere Informationen über den Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Berechtigungs-Service-Clients**

Bevor Sie eine Berechtigung programmgesteuert in AEM Forms importieren können, müssen Sie einen Client für den Berechtigungs-Service erstellen. Weitere Informationen finden Sie unter [Festlegen von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren der Berechtigung**

Referenzieren Sie eine Berechtigung, die Sie in AEM Forms importieren möchten. Der Schnellstart für diesen Abschnitt verweist auf eine P12-Datei im Dateisystem.

**Durchführen des Importvorgangs**

Nachdem Sie auf die Berechtigung verwiesen haben, importieren Sie die Berechtigung in AEM Forms. Wenn die Berechtigung nicht erfolgreich importiert wurde, wird eine Ausnahme ausgelöst. Beim Importieren einer Berechtigung geben Sie einen Alias für die Berechtigung an.

**Siehe auch**

[Importieren von Berechtigungen mithilfe der Java-API](credentials.md#import-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Berechtigungs-Service-API – Schnellstarts](/help/forms/developing/credential-service-java-api-quick.md#credential-service-java-api-quick-start-soap)

[Löschen von Berechtigungen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

### Importieren von Berechtigungen mithilfe der Java-API {#import-credentials-using-the-java-api}

So importieren Sie eine Berechtigung mithilfe der Trust Manager-API (Java) in AEM Forms:

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie beispielsweise adobe-truststore-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Berechtigungs-Service-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `CredentialServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Angabe der Berechtigung

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der Berechtigung angibt.
   * Erstellen Sie mithilfe des `com.adobe.idp.Document`-Konstruktors ein `com.adobe.idp.Document`-Objekt, in dem die Berechtigung gespeichert wird. Übergeben Sie das `java.io.FileInputStream`-Objekt, das die Berechtigung enthält, an den Konstruktor enthält.

1. Ausführen des Importvorgangs

   * Erstellen Sie ein Zeichenfolgen-Array, das ein Element enthält. Weisen Sie den Wert `truststore.usage.type.sign` dem Element zu.
   * Rufen Sie die `importCredential`-Methode des `CredentialServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

      * Ein Zeichenfolgenwert, der den Alias für die Berechtigung angibt.
      * Die `com.adobe.idp.Document`-Instanz, in der die Berechtigung gespeichert ist.
      * Ein Zeichenfolgenwert, der das Passwort enthält, das mit der Berechtigung verknüpft ist.
      * Das Zeichenfolgen-Array, das den Wert enthält, der die Verwendung bezeichnet. Sie können beispielsweise den Wert `truststore.usage.type.sign` angeben. Um eine Reader Extension-Berechtigung zu importieren, geben Sie `truststore.usage.type.lcre` an.

**Siehe auch**

[Importieren von Berechtigungen mithilfe der Trust Manager-API](credentials.md#importing-credentials-by-using-the-trust-manager-api)

[Kurzanleitung (SOAP-Modus): Importieren von Berechtigungen mit der Java-API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-importing-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Löschen von Berechtigungen mithilfe der Trust Manager-API {#deleting-credentials-by-using-the-trust-manager-api}

Sie können eine Berechtigung programmgesteuert löschen, indem Sie die Trust Manager-API verwenden. Um eine Berechtigung zu löschen, müssen Sie den Alias der Berechtigung angeben. Nachdem eine Berechtigung gelöscht wurde, kann sie nicht mehr zum Ausführen eines Vorgangs verwendet werden.

>[!NOTE]
>
>Sie können eine Berechtigung für AEM Forms nicht mithilfe des Web-Services löschen.

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um eine Berechtigung zu löschen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Client für den Berechtigungs-Service.
1. Führen Sie den Löschvorgang durch.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-truststore-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Weitere Informationen über den Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Service-Clients für die Berechtigung**

Bevor Sie eine Berechtigung programmgesteuert löschen können, müssen Sie einen Client des Data Integration-Service erstellen. Beim Erstellen eines Service-Clients bestimmen Sie Verbindungseinstellungen, die zum Aufrufen eines Services erforderlich sind. Weitere Informationen finden Sie unter [Einrichten von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Ausführen des Löschvorgangs**

Um eine Berechtigung zu löschen, müssen Sie den Alias der Berechtigung angeben. Wenn Sie einen Alias angeben, der nicht existiert, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Importieren von Berechtigungen mithilfe der Java-API](credentials.md#import-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Importieren von Berechtigungen mithilfe der Java-API](credentials.md#import-credentials-using-the-java-api)

### Löschen von Berechtigungen mithilfe der Java-API {#deleting-credentials-using-the-java-api}

So löschen Sie mithilfe der Trust Manager-API (Java) eine Berechtigung aus AEM Forms:

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie beispielsweise adobe-truststore-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Berechtigungs-Service-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `CredentialServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Durchführen des Löschvorgangs

   Rufen Sie die `deleteCredential`-Methode des `CredentialServiceClient`-Objekt auf und übergeben Sie einen Zeichenfolgewert, der den Alias-Wert angibt.

**Siehe auch**

[Löschen von Berechtigungen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

[Schnellstart (SOAP-Modus): Löschen von Berechtigungen mithilfe der Java-API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-deleting-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
