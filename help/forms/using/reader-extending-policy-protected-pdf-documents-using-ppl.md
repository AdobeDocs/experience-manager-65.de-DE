---
title: Anwenden der Reader Extension auf richtliniengeschützte PDF-Dokumente mit Portable Protection Library
description: Reader-Erweiterungen ermöglichen über Acrobat Reader interaktive Funktionen in Adobe PDF-Dokumenten. Sie können die Portable Protection Library (PPL) verwenden, um DRM-geschützten PDF-Dokumenten Reader-Erweiterungen hinzuzufügen.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Security,Reader Extensions
exl-id: fe5d83e8-5e36-4146-a20a-dab2213055e2
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '783'
ht-degree: 100%

---

# Reader-erweiternde richtliniengeschützte PDF-Dokumente mit der Portable Protection Library {#reader-extending-policy-protected-pdf-documents-using-portable-protection-library}

Machen Sie sich mit den Konzepten der Dokumentensicherheit, der Reader-Erweiterung und der Programmiersprache Java vertraut, um eine Reader-Erweiterung für die durch die Dokumentensicherheit richtliniengeschützten PDF-Dokumente durchzuführen.

Mithilfe der Dokumentensicherheit können Sie den Zugriff auf bestimmte PDF-Dokumente auf autorisierte Benutzende beschränken. Sie können auch festlegen, wie eine Empfängerin oder ein Empfänger ein geschütztes Dokument verwenden kann. Sie können beispielsweise angeben, ob Empfängerinnen und Empfänger den Text eines durch die Dokumentensicherheit richtliniengeschützten Dokuments drucken, kopieren oder bearbeiten können. Weitere Informationen zur Dokumentensicherheit finden Sie unter [Informationen zur Dokumentensicherheit](/help/forms/using/admin-help/document-security.md).

Sie können Reader-Erweiterungen verwenden, um über Acrobat Reader interaktive Funktionen in Adobe PDF-Dokumenten zu aktivieren. Diese interaktiven Funktionen sind normalerweise nur über Adobe Acrobat Professional und Standard verfügbar. Weitere Informationen zu den interaktiven Funktionen, die Readererweiterung aktivieren kann, finden Sie unter [DocAssurance-Dienst für Adobe Experience Manager Forms ](/help/forms/using/overview-aem-document-services.md)**.**

Sie können die Portable Protection Library verwenden, um Richtlinien auf das Dokument anzuwenden, ohne dass das Dokument über das Netzwerk gesendet werden muss.  Nur die Sicherheitsberechtigungen und Details der Schutzrichtlinie werden über das Netzwerk gesendet. Das eigentliche Dokument verlässt nie den Client und die Schutzrichtlinien werden lokal auf dem Client angewendet.

## Reader-Erweiterungen für PDF-Dokumente, die durch die Dokumentensicherheit richtliniengeschützt sind {#reader-extending-document-security-policy-protected-pdf-documents}

Bei den richtliniengeschützten Dokumenten handelt es sich um verschlüsselte Dokumente. Sie können keine standardmäßigen Reader Extension-APIs verwenden, um Nutzungsrechte für richtliniengeschützte PDF-Dokumente anzuwenden, zu entfernen und abzurufen. Nur der Readererweiterungs-Dienst von Portable Protection Library bietet APIs, um Verwendungsrechte für durch Dokumentensicherheit richtliniengeschützte PDF-Dokumente anzuwenden, zu entfernen und abzurufen.

### Reader Extensions-Dienst {#reader-extensions-service}

Der Reader Extensions-Dienst fügt einem richtliniengeschützten PDF-Dokument Nutzungsrechte hinzu und aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument in Adobe Acrobat Reader geöffnet wird. Er verfügt außerdem über APIs zum Entfernen und Abrufen von Nutzungsrechten eines richtliniengeschützten Dokuments.

Der Reader Extensions-Dienst unterstützt PDF-Dokumente, die auf dem PDF-Standard 1.6 und höher basieren, vollständig. Für die Nutzung der richtliniengeschützten PDF-Dokumente benötigen Drittanwender außer dem Acrobat Reader keine zusätzliche Software oder Plug-Ins.

Mit dem Reader Extensions-Dienst können Sie die folgenden Aufgaben ausführen:

* Anwenden von Nutzungsrechten auf ein richtliniengeschütztes PDF-Dokument.
* Entfernen von Nutzungsrechten für ein richtliniengeschütztes PDF-Dokument
* Abrufen von angewendeten Verwendungsrechten für ein richtliniengeschütztes PDF-Dokument

### Anwenden von Verwendungsrechten auf ein durch Dokumentensicherheit richtliniengeschütztes PDF-Dokument {#apply-usage-rights-to-a-document-security-policy-protected-pdf-document}

Mit der Java-API `applyUsageRights` können Sie Verwendungsrechte für richtliniengeschützte PDF-Dokumente aktivieren. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. PDF-Dokumente, auf die Verwendungsrechte angewandt wurden, werden als Dokumente mit aktivierten Verwendungsrechten bezeichnet. Benutzende, die ein Dokument mit aktivierten Verwendungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses spezifische Dokument aktiviert sind.

**Syntax:** `InputStream applyUsageRights(InputStream inputFile, File certFile, String credentialPassword, UsageRights usageRights)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>inputFile</p> </td>
   <td><p>Geben Sie den InputStream an, der das PDF-Dokument darstellt, auf das Nutzungsrechte angewendet werden sollen. Sie können Dokumente verwenden, die durch LiveCycle Rights Management oder AEM Forms Document Security geschützt sind.</p> </td>
  </tr>
  <tr>
   <td><p>certFile</p> </td>
   <td><p>Geben Sie ein Dateiobjekt an, das eine .jks-Datei darstellt. Die .jks-Datei ist eine Keystore-Datei. Sie verweist auf ein Zertifikat, das Nutzungsrechte gewährt.</p> </td>
  </tr>
  <tr>
   <td><p>credentialPassword</p> </td>
   <td><p>Geben Sie das Kennwort des Keystores an. </p> </td>
  </tr>
  <tr>
   <td><p>usageRights</p> </td>
   <td><p>Gibt ein Objekt des Typs <a href="https://help.adobe.com/de_DE/livecycle/11.0/ProgramLC/javadoc/com/adobe/livecycle/readerextensions/client/UsageRights.html" target="_blank"> Nutzungsrechte</a> an. Das useRights-Objekt stellt individuelle Rechte dar, die auf ein richtliniengeschütztes PDF-Dokument angewendet werden können.</p> </td>
  </tr>
 </tbody>
</table>

### Abrufen von angewendeten Verwendungsrechten für ein richtliniengeschütztes PDF-Dokument   {#retrieve-usage-rights-applied-to-a-policy-protected-pdf-document-nbsp}

Mit der Java-API `getDocumentUsageRights` können Sie die Readererweiterungs-Verwendungsrechte abrufen, die auf ein richtliniengeschütztes PDF-Dokument angewendet wurden. Durch Abrufen von Informationen zu Verwendungsrechten erfahren Sie, welche Funktionen die Readererweiterung für das richtliniengeschützte PDF-Dokument aktiviert hat.

**Syntax:** `public GetUsageRightsResult getDocumentUsageRights(InputStream inDoc)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>inDoc</p> </td>
   <td><p>Geben Sie den InputStream an, der das PDF-Dokument darstellt, von dem die Verwendungsrechte abgerufen werden sollen. Sie können Dokumente verwenden, die durch LiveCycle Rights Management oder AEM Forms Document Security geschützt sind.</p> </td>
  </tr>
 </tbody>
</table>

#### Codebeispiel {#code-sample}

```java
//Create a ServiceClientFactory instance
ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
//Create a RightsManagementClient object
RightsManagementClient2 rmClient2= new RightsManagementClient2(factory);

String inputFileName = "C:\\Sample\\protected.pdf"; //Input file can be RM protected or unprotected pdf file
File certFile = new File("C:\\Sample\\cert.jks"); //RE certificate file
String password = "password"; //password for RE certificate
UsageRights usageRights = getUsageRights(true,true,false,false,true,true,false,false,false,false,true);

//RE rights to be applied on the file : FormFillIn, FormDataImportExport, SubmitStandalone, OnlineForms, DynamicFormField, DynamicFormPages, BarcodeDecoding, DigitalSignatures, Comments, CommentsOnline, EmbeddedFiles

InputStream inputFileStream = new FileInputStream(inputFileName);
InputStream output = rmClient2.getRightsManagementReaderExtensionService().applyUsageRights(inputFileStream, certFile, credentialPassword, rights);

String outputFileName = "C:\\Sample\\ReAdded.pdf";
//Save the PDF document
File myFile = new File(outputFileName);
FileOutputStream outputStream = new FileOutputStream(myFile);

int read = 0;
byte[] bytes = new byte[1024];

while ((read = output.read(bytes)) != -1) {

    outputStream.write(bytes, 0, read);
}

System.out.println("UsageRights applied successfully to the document. ");
 outputStream.close();
inputFileStream.close();

//Get Usage Rights for the output pdf document
InputStream fileWithRe = new FileInputStream(myFile);

GetUsageRightsResult usageRights = rmClient2.getRightsManagementReaderExtensionService().getDocumentUsageRights(fileWithRe);

UsageRights rights = usageRights.getRights();
String right1 = rights1.toString();
System.out.println("RE rights for the file are :\n"+right1);
 fileWithRe.close();
```

### Entfernen von Verwendungsrechten für ein richtliniengeschütztes PDF-Dokument {#remove-usage-rights-of-a-policy-protected-pdf-document}

Mit der Java-API `removeUsageRights` können Sie Verwendungsrechte von einem richtliniengeschützten Dokument entfernen. Verwendungsrechte müssen aus einem richtliniengeschützten PDF-Dokument entfernt werden, um andere AEM Forms-Vorgänge auf das Dokument anzuwenden. Sie müssen beispielsweise ein PDF-Dokument digital signieren (bzw. zertifizieren), bevor Sie Verwendungsrechte festlegen. Wenn Sie daher Vorgänge auf ein richtliniengeschütztes Dokument anwenden möchten, müssen Sie Verwendungsrechte von dem PDF-Dokument entfernen, andere Vorgänge anwenden, z. B. das Dokument digital signieren, und anschließend die Verwendungsrechte wieder für das Dokument aktivieren.

**Syntax:** `InputStream removeUsageRights(InputStream inputFile)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p> </p> <p>inputFile</p> </td>
   <td>Geben Sie den InputStream an, der das PDF-Dokument darstellt, von dem die Verwendungsrechte<br /> entfernt werden sollen. Sie können Dokumente verwenden, die durch LiveCycle Rights Management oder AEM Forms Document Security geschützt sind.</td>
  </tr>
 </tbody>
</table>

#### Codebeispiel {#code-sample-1}

```java
//Create a ServiceClientFactory instance
ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
//Create a RightsManagementClient object
RightsManagementClient2 rmClient2= new RightsManagementClient2(factory);

String inputFileName = "C:\\Sample\\fileWithRe.pdf"; //Input file can be RM protected or unprotected pdf file
InputStream inputFileStream = new FileInputStream(inputFileName);

InputStream fileStream = rmClient2.getRightsManagementReaderExtensionService().removeUsageRights(inputFileStream);

String outputFileName = "C:\\Sample\\ReRemoveded.pdf";
//Save the PDF document
File myFile = new File(outputFileName);
FileOutputStream outputStream = new FileOutputStream(myFile);

int read = 0;
byte[] bytes = new byte[1024];

while ((read = fileStream.read(bytes)) != -1) {

    outputStream.write(bytes, 0, read);
}
System.out.println("RE rights removed successfully from the document.");
outputStream.close();
inputFileStream.close();
```
