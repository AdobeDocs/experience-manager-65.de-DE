---
title: Verbinden von AEM Forms mit Adobe LiveCycle
description: Mit Adobe Experience Manager (AEM) LiveCycle Connector können Sie LiveCycle ES4-Acrobat-Dienste aus AEM-Apps und -Workflows starten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
role: Admin
exl-id: 562f8a22-cbab-4915-bc0d-da9bea7d18fa
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1026'
ht-degree: 100%

---

# Verbinden von AEM Forms mit Adobe LiveCycle {#connecting-aem-forms-with-adobe-livecycle}

Adobe Experience Manager (AEM) LiveCycle Connector ermöglicht einen unterbrechungsfreien Aufruf von Adobe LiveCycle ES4-Acrobat-Diensten aus AEM-Web-Apps und -Workflows. LiveCycle bietet ein reiches Client-SDK, das Client-Anwendungen ermöglicht, LiveCycle-Dienste mithilfe von Java™-APIs zu starten. AEM LiveCycle Connector vereinfacht die Verwendung dieser APIs innerhalb der OSGi-Umgebung.

## Verbinden des AEM-Servers mit Adobe LiveCycle {#connecting-aem-server-to-adobe-livecycle}

AEM LiveCycle Connector ist Teil des [AEM Forms-Add-On-Pakets](/help/forms/using/installing-configuring-aem-forms-osgi.md). Nachdem Sie das Add-on-Paket für AEM Forms installiert haben, führen Sie die folgenden Schritte aus, um Details des LiveCycle-Servers zur AEM-Web-Konsole hinzuzufügen.

1. Suchen Sie die Adobe LiveCycle Client SDK-Konfigurationskomponente im Konfigurations-Manager der AEM-Web-Konsole.
1. Klicken Sie auf die Komponente, um URL, Benutzernamen und Kennwort des Konfigurations-Servers zu bearbeiten.
1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

Auch wenn die Eigenschaften selbsterklärend sind, werden die wichtigsten im Folgenden erläutert:

* **Server URL** – gibt die URL für den LiveCycle-Server an. Wenn Sie möchten, dass LiveCycle und AEM über HTTPS kommunizieren, starten Sie AEM mit der folgenden JVM

  ```java
  argument
   -Djavax.net.ssl.trustStore=<<em>path to LC keystore</em>>
  ```

  Option.

* **Benutzername**: Gibt den Benutzernamen des Kontos an, das verwendet wird, um die Kommunikation zwischen AEM und LiveCycle herzustellen. Das Konto ist ein LiveCycle-Benutzerkonto, das zum Start von Acrobat-Diensten berechtigt ist.
* **Kennwort**: Gibt das Kennwort an.
* **Dienstname**: Gibt die Dienste an, die mit den in den Feldern für Benutzernamen und Kennwort angegebenen Benutzeranmeldeinformationen gestartet werden. Standardmäßig werden beim Starten von LiveCycle-Diensten keine Anmeldeinformationen weitergegeben.

## Starten von Dokumentendiensten {#starting-document-services}

Client-Anwendungen können LiveCycle-Dienste programmgesteuert über eine Java™-API, Web-Dienste, Remoting oder REST starten. Für Java™-Clients kann die Anwendung das LiveCycle SDK verwenden. Das LiveCycle SDK stellt eine Java™-API für den Remote-Start dieser Dienste zur Verfügung. Um beispielsweise ein Microsoft® Word-Dokument in das PDF-Format zu konvertieren, startet der Client den GeneratePDFService. Der Aufruf erfolgt mittels folgender Schritte:

1. Erstellen Sie eine ServiceClientFactory-Instanz.
1. Jeder Dienst stellt eine Client-Klasse zur Verfügung. Erstellen Sie zum Starten eines Dienstes eine Client-Instanz des Dienstes.
1. Starten Sie den Dienst und verarbeiten Sie das Ergebnis.

AEM LiveCycle Connector vereinfacht den Ablauf, indem diese Client-Instanzen als OSGi-Dienste bereitgestellt werden, auf die über standardmäßige OSGi-Methoden zugegriffen werden kann. LiveCycle Connector umfasst die folgenden Funktionen:

* Client-Instanzen als OSGi-Dienst: Die als OSGI-Bundles zusammengestellten Clients sind im Abschnitt [Liste der Acrobat-Dienste](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p) aufgeführt. Jede Client-JAR-Datei registriert die Client-Instanz als OSGi-Dienst in der Registrierung des OSGi-Dienstes.
* Weitergabe von Benutzeranmeldeinformationen: Die erforderlichen Verbindungsdetails für die Verbindung mit dem LiveCycle-Server werden an einem zentralen Speicherort verwaltet.
* ServiceClientFactory-Dienst: Zum Starten der Prozesse kann die Client-Anwendung auf die ServiceClientFactory-Instanz zugreifen.

### Starten über Dienstverweise aus der Registrierung des OSGi-Dienstes {#starting-via-service-references-from-osgi-service-registry}

Um einen bereitgestellten Dienst in AEM zu starten, führen Sie folgende Schritte aus:

1. Legen Sie die Maven-Abhängigkeiten fest. Fügen Sie die Abhängigkeit der erforderlichen Client-JAR-Datei in der Maven-Datei „pom.xml“ hinzu. Fügen Sie die Abhängigkeit mindestens zu den JARs „adobe-livecycle-client“ und „adobe-usermanager-client“ hinzu.

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-livecycle-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-usermanager-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-cq-integration-api</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

   Um einen Dienst zu starten, fügen Sie für den Dienst die entsprechende Maven-Abhängigkeit hinzu. Eine Liste der Abhängigkeiten finden Sie in der [Liste der Acrobat-Dienste](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p). Fügen Sie beispielsweise zum Dienst für das Generieren von PDF-Dokumenten die folgende Abhängigkeit hinzu:

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-generatepdf-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

1. Rufen Sie den Dienstverweis ab. Besorgen Sie sich ein Handle auf die Dienstinstanz. Wenn Sie eine Java™-Klasse schreiben, können Sie die Anmerkungen für Declarative Services verwenden.

   ```java
   import com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient;
   import com.adobe.livecycle.generatepdf.client.CreatePDFResult;
   import com.adobe.idp.Document;
   
   @Reference
   GeneratePdfServiceClient generatePDF;
   ...
   
   Resource r = resourceResolver.getResource("/path/tp/docx");
   Document sourceDoc = new Document(r.adaptTo(InputStream.class));
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

   Im obigen Codesnippet wird die createPDF-API von GeneratePdfServiceClient gestartet, um ein Dokument in ein PDF zu konvertieren. Auf einer JSP-Seite können Sie einen ähnlichen Aufruf mithilfe des folgenden Codes durchführen. Der wesentliche Unterschied besteht darin, dass der folgende Code Sling ScriptHelper verwendet, um auf GeneratePdfServiceClient zuzugreifen.

   ```jsp
   <%@ page import="com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient" %>
   <%@ page import="com.adobe.livecycle.generatepdf.client.CreatePDFResult" %>
   <%@ page import="com.adobe.idp.Document" %>
   
   GeneratePdfServiceClient generatePDF = sling.getService(GeneratePdfServiceClient.class);
   Document sourceDoc = ...
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

### Starten über ServiceClientFactory {#starting-via-serviceclientfactory}

Manchmal ist die ServiceClientFactory-Klasse erforderlich. Beispielsweise benötigen Sie ServiceClientFactory, um Prozesse aufzurufen.

```java
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider;
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;

@Reference
ServiceClientFactoryProvider scfProvider;

...
ServiceClientFactory scf = scfProvider.getDefaultServiceClientFactory();
...
```

## RunAs-Unterstützung {#runas-support}

Für nahezu jeden Acrobat-Dienst in LiveCycle ist eine Authentifizierung erforderlich. Sie können eine der folgenden Optionen verwenden, um diese Dienste zu starten, ohne explizite Anmeldeinformationen im Code anzugeben:

### Konfiguration der Zulassungsliste {#allowlist-configuration}

Die LiveCycle Client SDK-Konfiguration enthält eine Einstellung für Dienstnamen. Diese Konfiguration ist eine Liste der Dienste, für die die Aufruflogik standardmäßig Admin-Anmeldeinformationen verwendet. Wenn Sie beispielsweise DirectoryManager-Dienste (Teil der User Management-API) zu dieser Liste hinzufügen, kann der Dienst von jedem Clientcode direkt verwendet werden. Darüber hinaus gibt die Aufrufebene die konfigurierten Anmeldeinformationen automatisch als Teil der an den LiveCycle-Server gesendeten Anfrage weiter.

### RunAsManager {#runasmanager}

Im Rahmen der Integration wird ein neuer RunAsManager-Dienst zur Verfügung gestellt. Dieser ermöglicht es Ihnen, die zu verwendenden Anmeldedaten programmgesteuert zu kontrollieren, wenn ein Aufruf an den LiveCycle-Server erfolgt.

```java
import com.adobe.livecycle.dsc.clientsdk.security.PasswordCredential;
import com.adobe.livecycle.dsc.clientsdk.security.PrivilegedAction;
import com.adobe.livecycle.dsc.clientsdk.security.RunAsManager;
import com.adobe.idp.dsc.registry.component.ComponentRegistry;

@Reference
private RunAsManager runAsManager;

List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
            public List<Component> run() {
                return componentRegistry.getComponents();
            }
        });
assertNotNull(components);
```

Wenn Sie andere Anmeldeinformationen weitergeben möchten, können Sie die überladene Methode verwenden, die eine PasswordCredential-Instanz in Anspruch nimmt.

```java
PasswordCredential credential = new PasswordCredential("administrator","password");
List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
    public List<Component> run() {
        return componentRegistry.getComponents();
    }
},credential);
```

### InvocationRequest-Eigenschaft {#invocationrequest-property}

Wenn Sie einen Prozess aufrufen oder die ServiceClientFactory-Klasse direkt verwenden und eine InvocationRequest erstellen, können Sie eine Eigenschaft festlegen, um anzugeben, dass die Aufrufebene konfigurierte Benutzeranmeldeinformationen verwenden soll.

```java
import com.adobe.idp.dsc.InvocationResponse
import com.adobe.idp.dsc.InvocationRequest
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory
import com.adobe.livecycle.dsc.clientsdk.InvocationProperties

ServiceClientFactoryProvider scfp = sling.getService(ServiceClientFactoryProvider.class)
ServiceClientFactory serviceClientFactory = scfp.getDefaultServiceClientFactory()
InvocationRequest ir = serviceClientFactory.createInvocationRequest("sample/LetterSubmissionProcess", "invoke", new HashMap(), true);

//Here we are invoking the request with system user
ir.setProperty(InvocationProperties.INVOKER_TYPE,InvocationProperties.INVOKER_TYPE_SYSTEM)

InvocationResponse response = serviceClientFactory.getServiceClient().invoke(ir);
```

## Liste der Acrobat-Dienste {#document-services-list}

### Adobe LiveCycle Client SDK API Bundle {#adobe-livecycle-client-sdk-api-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.idp.um.api.AuthenticationManager
* com.adobe.idp.um.api.DirectoryManager
* com.adobe.idp.um.api.AuthorizationManager
* com.adobe.idp.dsc.registry.service.ServiceRegistry
* com.adobe.idp.dsc.registry.component.ComponentRegistry

#### Maven-Abhängigkeiten {#maven-dependencies}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-client</artifactId>
  <version>11.0.0</version>
</dependency>
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-usermanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Client SDK Bundle {#adobe-livecycle-client-sdk-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.livecycle.dsc.clientsdk.security.RunAsManager
* com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider

#### Maven-Abhängigkeiten {#maven-dependencies-1}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-cq-integration-api</artifactId>
  <version>1.1.10</version>
</dependency>
```

### Adobe LiveCycle TaskManager Client Bundle {#adobe-livecycle-taskmanager-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.idp.taskmanager.dsc.client.task.TaskManager
* com.adobe.idp.taskmanager.dsc.client.TaskManagerQueryService
* com.adobe.idp.taskmanager.dsc.client.queuemanager.QueueManager
* com.adobe.idp.taskmanager.dsc.client.emailsettings.EmailSettingService
* com.adobe.idp.taskmanager.dsc.client.endpoint.TaskManagerEndpointClient
* com.adobe.idp.taskmanager.dsc.client.userlist.UserlistService

#### Maven-Abhängigkeiten {#maven-dependencies-2}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-taskmanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Workflow Client Bundle {#adobe-livecycle-workflow-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.idp.workflow.client.WorkflowServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-3}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-workflow-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle PDF Generator Client Bundle {#adobe-livecycle-pdf-generator-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-4}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-generatepdf-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Application Manager Client Bundle {#adobe-livecycle-application-manager-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.idp.applicationmanager.service.ApplicationManager
* com.adobe.livecycle.applicationmanager.client.ApplicationManager
* com.adobe.livecycle.design.service.DesigntimeService

#### Maven-Abhängigkeiten {#maven-dependencies-5}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-applicationmanager-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Assembler Client Bundle {#adobe-livecycle-assembler-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.assembler.client.AssemblerServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-6}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-assembler-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Form Data Integration Client Bundle {#adobe-livecycle-form-data-integration-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.formdataintegration.client.FormDataIntegrationClient

#### Maven-Abhängigkeiten {#maven-dependencies-7}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-formdataintegration-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Forms Client Bundle {#adobe-livecycle-forms-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.formsservice.client.FormsServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-8}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-forms-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Output Client Bundle {#adobe-livecycle-output-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.output.client.OutputClient

#### Maven-Abhängigkeiten {#maven-dependencies-9}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-output-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Reader Extensions Client Bundle {#adobe-livecycle-reader-extensions-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.readerextensions.client.ReaderExtensionsServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-10}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-reader-extensions-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Rights Manager Client Bundle {#adobe-livecycle-rights-manager-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.livecycle.rightsmanagement.client.DocumentManager
* com.adobe.livecycle.rightsmanagement.client.EventManager
* com.adobe.livecycle.rightsmanagement.client.ExternalUserManager
* com.adobe.livecycle.rightsmanagement.client.LicenseManager
* com.adobe.livecycle.rightsmanagement.client.WatermarkManager
* com.adobe.livecycle.rightsmanagement.client.PolicyManager
* com.adobe.livecycle.rightsmanagement.client.AbstractPolicyManager

#### Maven-Abhängigkeiten {#maven-dependencies-11}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-rightsmanagement-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Signatures Client Bundle {#adobe-livecycle-signatures-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.signatures.client.SignatureServiceClientInterface

#### Maven-Abhängigkeiten {#maven-dependencies-12}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-signatures-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Truststore Client Bundle {#adobe-livecycle-truststore-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.truststore.dsc.TrustConfigurationService
* com.adobe.truststore.dsc.CRLService
* com.adobe.truststore.dsc.CredentialService
* com.adobe.truststore.dsc.CertificateService

#### Maven-Abhängigkeiten {#maven-dependencies-13}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-truststore-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Repository Client Bundle {#adobe-livecycle-repository-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.repository.bindings.ResourceRepository
* com.adobe.repository.bindings.ResourceSynchronizer

#### Maven-Abhängigkeiten {#maven-dependencies-14}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-repository-client</artifactId>
  <version>11.0.0</version>
</dependency>
```
