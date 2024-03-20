---
title: Anwenden der Reader Extension auf richtliniengeschützte PDF-Dokumente mit Portable Protection Library
description: Reader-Erweiterungen ermöglichen interaktive Funktionen in Adobe PDF-Dokumenten über Acrobat Reader. Sie können die Portable Protection Library (PPL) verwenden, um die DRM-geschützten PDF-Dokumente zu lesen.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Security
exl-id: fe5d83e8-5e36-4146-a20a-dab2213055e2
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 32%

---

# Reader-erweiternde richtliniengeschützte PDF-Dokumente mit der Portable Protection Library {#reader-extending-policy-protected-pdf-documents-using-portable-protection-library}

Machen Sie sich mit den Konzepten von Document Security, der Reader Extension und der Programmiersprache Java vertraut, um die richtliniengeschützten PDF-Dokumente für Document Security zu reader-erweitern.

Sie können Document Security verwenden, um den Zugriff auf bestimmte PDF-Dokumente auf autorisierte Benutzer zu beschränken. Sie können auch bestimmen, wie ein Empfänger ein geschütztes Dokument verwenden kann. Sie können beispielsweise angeben, ob Empfänger Text eines richtliniengeschützten Dokuments drucken, kopieren oder bearbeiten können. Weitere Informationen zu Document Security finden Sie unter [über Document Security](/help/forms/using/admin-help/document-security.md).

Sie können Reader Extensions verwenden, um interaktive Funktionen in Adobe PDF-Dokumenten über Acrobat Reader zu aktivieren. Diese interaktiven Funktionen sind normalerweise nur über Adobe Acrobat Professional und Standard verfügbar. Weitere Informationen zu den interaktiven Funktionen, die Readererweiterung aktivieren kann, finden Sie unter [DocAssurance-Dienst für Adobe Experience Manager Forms ](/help/forms/using/overview-aem-document-services.md)**.**

Sie können die Portable Protection Library verwenden, um Richtlinien auf das Dokument anzuwenden, ohne dass das Dokument über das Netzwerk gesendet werden muss.  Nur die Sicherheitsberechtigungen und Details der Schutzrichtlinie werden über das Netzwerk gesendet. Das eigentliche Dokument verlässt den Client nie und die Schutzrichtlinien werden lokal auf dem Client angewendet.

## Reader zum Erweitern von durch Document Security richtliniengeschützten PDF-Dokumenten {#reader-extending-document-security-policy-protected-pdf-documents}

Die richtliniengeschützten Dokumente sind verschlüsselte Dokumente. Sie können keine standardmäßigen Reader Extension-APIs verwenden, um Verwendungsrechte für richtliniengeschützte PDF-Dokumente anzuwenden, zu entfernen und abzurufen. Nur der Readererweiterungs-Dienst von Portable Protection Library bietet APIs, um Verwendungsrechte für durch Dokumentensicherheit richtliniengeschützte PDF-Dokumente anzuwenden, zu entfernen und abzurufen.

### Reader Extensions-Dienst {#reader-extensions-service}

Der Reader Extension-Dienst fügt einem richtliniengeschützten PDF-Dokument Verwendungsrechte hinzu und aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument mit Adobe Acrobat Reader geöffnet wird. Es verfügt auch über APIs zum Entfernen und Abrufen von Nutzungsrechten für ein richtliniengeschütztes Dokument.

Der Reader Extensions-Dienst unterstützt vollständig PDF-Dokumente auf der Basis von PDF Standard 1.6 und höher. Außer Acrobat Reader benötigen Drittbenutzer keine zusätzliche Software oder Plug-ins, um die richtliniengeschützten PDF-Dokumente verwenden zu können.

Mit dem Reader Extensions-Dienst können Sie die folgenden Aufgaben ausführen:

* Wenden Sie Verwendungsrechte auf ein richtliniengeschütztes PDF-Dokument an.
* Entfernen Sie die Verwendungsrechte eines richtliniengeschützten PDF-Dokuments.
* Abrufen von angewendeten Verwendungsrechten für ein richtliniengeschütztes PDF-Dokument

### Anwenden von Verwendungsrechten auf ein durch Dokumentensicherheit richtliniengeschütztes PDF-Dokument {#apply-usage-rights-to-a-document-security-policy-protected-pdf-document}

Mit der Java-API `applyUsageRights` können Sie Verwendungsrechte für richtliniengeschützte PDF-Dokumente aktivieren. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. PDF-Dokumente, auf die Verwendungsrechte angewendet wurden, werden als Dokumente mit aktivierten Benutzerrechten bezeichnet. Ein Benutzer, der ein Dokument mit aktivierten Benutzerrechten in Adobe Reader öffnet, kann Vorgänge durchführen, die für dieses spezifische Dokument aktiviert sind.

**Syntax:** `InputStream applyUsageRights(InputStream inputFile, File certFile, String credentialPassword, UsageRights usageRights)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>inputFile</p> </td>
   <td><p>Geben Sie den InputStream an, der das PDF-Dokument darstellt, auf das die Verwendungsrechte angewendet werden sollen. Sie können durch LiveCycle Rights Management oder AEM Forms Document Security geschützte Dokumente verwenden.</p> </td>
  </tr>
  <tr>
   <td><p>certFile</p> </td>
   <td><p>Geben Sie ein File -Objekt an, das eine JK-Datei darstellt. Die .jks-Datei ist eine Keystore-Datei. Er verweist auf ein Zertifikat, das Verwendungsrechte gewährt.</p> </td>
  </tr>
  <tr>
   <td><p>credentialPassword</p> </td>
   <td><p>Geben Sie das Kennwort des Keystore an. </p> </td>
  </tr>
  <tr>
   <td><p>usageRights</p> </td>
   <td><p>Gibt ein Objekt vom Typ an <a href="https://help.adobe.com/de_DE/livecycle/11.0/ProgramLC/javadoc/com/adobe/livecycle/readerextensions/client/UsageRights.html" target="_blank">UsageRights</a>. Das Objekt usageRights stellt individuelle Berechtigungen dar, die auf ein richtliniengeschütztes PDF-Dokument angewendet werden können.</p> </td>
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
   <td><p>Geben Sie den InputStream an, der das PDF-Dokument darstellt, aus dem die Verwendungsrechte abgerufen werden sollen. Sie können durch LiveCycle Rights Management oder AEM Forms Document Security geschützte Dokumente verwenden.</p> </td>
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

Mit der Java-API `removeUsageRights` können Sie Verwendungsrechte von einem richtliniengeschützten Dokument entfernen. Das Entfernen von Verwendungsrechten aus einem richtliniengeschützten PDF-Dokument ist erforderlich, um andere AEM Forms-Vorgänge für das Dokument durchzuführen. Sie müssen beispielsweise ein PDF-Dokument digital signieren (bzw. zertifizieren), bevor Sie Verwendungsrechte festlegen. Wenn Sie daher Vorgänge für ein richtliniengeschütztes Dokument durchführen möchten, müssen Sie die Verwendungsrechte aus dem PDF-Dokument entfernen, die anderen Vorgänge ausführen, z. B. das Dokument digital signieren, und dann erneut Verwendungsrechte auf das Dokument anwenden.

**Syntax:** `InputStream removeUsageRights(InputStream inputFile)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p> </p> <p>inputFile</p> </td>
   <td>Geben Sie den InputStream an, der das PDF-Dokument darstellt, von dem aus die Nutzung erfolgt<br /> -Berechtigungen entfernt werden. Sie können durch LiveCycle Rights Management oder AEM Forms Document Security geschützte Dokumente verwenden.</td>
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
