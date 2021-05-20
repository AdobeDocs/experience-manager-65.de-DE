---
title: Siehe Reader Extending richtliniengeschützter PDF-Dokumente mit Portable Protection Library
seo-title: Siehe Reader Extending richtliniengeschützter PDF-Dokumente mit Portable Protection Library
description: Reader Extensions aktivieren interaktive Funktionen in Adobe PDF-Dokumenten über Acrobat Reader. Sie können die Portable Protection Library (PPL) zum Reader Extending von durch DRM geschützten PDF-Dokumenten verwenden.
seo-description: Reader Extensions aktivieren interaktive Funktionen in Adobe PDF-Dokumenten über Acrobat Reader. Sie können die Portable Protection Library (PPL) zum Reader Extending von durch DRM geschützten PDF-Dokumenten verwenden.
uuid: 0da17641-d24c-43c2-b918-8b5abe1e5473
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 83ca522e-d16e-4196-9aa7-84f85de8dee2
feature: Dokumentensicherheit
exl-id: fe5d83e8-5e36-4146-a20a-dab2213055e2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 94%

---

# Siehe Reader Extending richtliniengeschützter PDF-Dokumente mit Portable Protection Library {#reader-extending-policy-protected-pdf-documents-using-portable-protection-library}

Sie müssen mit den Konzepten von Document Security, der Reader Extension und der Programmiersprache Java vertraut sein, um ein Reader Extending für die die durch Document Security richtliniengeschützten PDF-Dokumente durchzuführen.

Sie können Document Security verwenden, um den Zugriff auf bestimmte PDF-Dokumenten nur auf autorisierte Benutzer zu beschränken. Sie können auch bestimmen, wie ein Empfänger ein geschütztes Dokument nutzen darf. Sie können beispielsweise angeben, ob Empfänger Text eines durch Document Security richtliniengeschützte Dokuments drucken, kopieren oder bearbeiten können. Weitere Informationen zu Document Security finden Sie unter [Informationen zu Document Security](/help/forms/using/admin-help/document-security.md).

Verwenden Sie Reader Extensions, um interaktive Funktionen in Adobe PDF-Dokumenten über Acrobat Reader zu aktivieren. Diese interaktiven Funktionen sind normalerweise nur über Adobe Acrobat Professional und Acrobat Standard verfügbar. Weitere Informationen zu den interaktiven Funktionen, die Reader Extension aktivieren kann, finden Sie unter [DocAssurance-Dienst für Adobe Experience Manager Forms ](/help/forms/using/overview-aem-document-services.md)**.**

Sie können die Portable Protection Library verwenden, um Richtlinien auf das Dokument anzuwenden, ohne dass das Dokument über das Netzwerk gesendet werden muss. Über das Netzwerk werden nur Sicherheitsberechtigungen und Details zu Schutzrichtlinien übertragen. Das Originaldokument verlässt den Client nicht und und die Schutzrichtlinien werden lokal auf dem Client angewendet.

## Reader Extending von durch Document Security richtliniengeschützten Dokumenten {#reader-extending-document-security-policy-protected-pdf-documents}

Die richtliniengeschützten Dokumente sind verschlüsselte Dokumente. Sie können keine standardmäßigen Reader Extension-APIs verwenden, um Verwendungsrechte für richtliniengeschützte PDF-Dokumente anzuwenden, zu entfernen und abzurufen. Nur der Reader Extensions-Dienst von Portable Protection Library bietet APIs, um Verwendungsrechte für durch Document Security richtliniengeschützte PDF-Dokumente anzuwenden, zu entfernen und abzurufen.

### Reader Extensions-Dienst {#reader-extensions-service}

Der Reader Extension-Dienst fügt einem richtliniengeschützten PDF-Dokument Verwendungsrechte hinzu und aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument in Adobe Acrobat Reader geöffnet wird. Er enthält außerdem APIs zum Entfernen und Abrufen der Verwendungsrechte eines richtliniengeschützten Dokuments.

Der Reader Extensions-Dienst unterstützt vollständig sämtliche PDF-Dokumente basierend auf PDF-Standard 1.6 und höher. Abgesehen von Acrobat Reader benötigen externe Benutzer benötigen keine zusätzliche Software oder Plug-Ins für das Verwenden der richtliniengeschützten PDF-Dokumente.

Sie können die folgenden Aufgaben mit dem Reader Extensions-Dienst ausführen:

* Anwenden von Verwendungsrechten auf ein richtliniengeschütztes PDF-Dokument
* Entfernen von Verwendungsrechten für ein richtliniengeschütztes PDF-Dokument
* Abrufen von angewendeten Verwendungsrechten für ein richtliniengeschütztes PDF-Dokument 

### Anwenden von Verwendungsrechten auf ein durch Document Security richtliniengeschütztes PDF-Dokument {#apply-usage-rights-to-a-document-security-policy-protected-pdf-document}

Mit der Java-API `applyUsageRights` können Sie Verwendungsrechte für PDF-Dokumente aktivieren. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. PDF-Dokumente, auf die Verwendungsrechte angewandt wurden, werden als Dokumente mit aktivierten Verwendungsrechten bezeichnet. Benutzer, die ein Dokument mit aktivierten Verwendungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses spezifische Dokument aktiviert sind.

**Syntax:** `InputStream applyUsageRights(InputStream inputFile, File certFile, String credentialPassword, UsageRights usageRights)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>inputFile</p> </td>
   <td><p>Geben Sie den InputStream an, der das PDF-Dokument darstellt, auf das die Verwendungsrechte angewendet werden sollen. Sie können durch LiveCycle Rights Management oder durch AEM Forms Document Security geschützte Dokumente verwenden.</p> </td>
  </tr>
  <tr>
   <td><p>certFile</p> </td>
   <td><p>Geben Sie das Dateiobjekt an, das eine.jks-Datei darstellt. Die.jks-Datei ist eine Keystore-Datei. Sie verweist auf ein Zertifikat, das die Verwendungsrechte gewährt.</p> </td>
  </tr>
  <tr>
   <td><p>credentialPassword</p> </td>
   <td><p>Legen Sie das Kennwort des Keystore fest. </p> </td>
  </tr>
  <tr>
   <td><p>usageRights</p> </td>
   <td><p>Gibt ein Objekt vom Typ <a href="https://help.adobe.com/en_US/livecycle/11.0/ProgramLC/javadoc/com/adobe/livecycle/readerextensions/client/UsageRights.html" target="_blank">UsageRights</a> an. Das Objekt „UsageRights“ stellt individuelle Zugriffsrechte dar, die auf ein richtliniengeschütztes PDF-Dokument angewendet werden können.</p> </td>
  </tr>
 </tbody>
</table>

### Abrufen von angewendeten Verwendungsrechten für ein richtliniengeschütztes PDF-Dokument   {#retrieve-usage-rights-applied-to-a-policy-protected-pdf-document-nbsp}

Sie können die Java-API `getDocumentUsageRights`verwenden, um die auf ein richtliniengeschütztes PDF-Dokument angewendeten Verwendungsrechte für die Reader-Erweiterung abzurufen. Durch Abrufen von Informationen zu Verwendungsrechten erfahren Sie, welche Funktionen Reader Extension für das richtliniengeschützte PDF-Dokument aktiviert hat.

**Syntax:** `public GetUsageRightsResult getDocumentUsageRights(InputStream inDoc)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>inDoc</p> </td>
   <td><p>Geben Sie den InputStream an, der das PDF-Dokument darstellt, von dem die Verwendungsrechte abgerufen werden sollen. Sie können durch LiveCycle Rights Management oder durch AEM Forms Document Security geschützte Dokumente verwenden.</p> </td>
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

System.out.println("UsageRights applied successfully to the document. ”);
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

Mit der Java-API `removeUsageRights` können Sie Verwendungsrechte von einem richtliniengeschützten Dokument entfernen. Das Entfernen von Verwendungsrechten aus einem richtliniengeschützte PDF-Dokument ist notwendig, um andere AEM Forms-Vorgänge darauf anzuwenden. Sie müssen beispielsweise ein PDF-Dokument digital signieren (bzw. zertifizieren), bevor Sie Verwendungsrechte festlegen. Wenn Sie demnach Vorgänge auf ein richtliniengeschütztes Dokument anwenden möchten, müssen Sie Verwendungsrechte vom PDF-Dokument entfernen, andere Vorgänge anwenden, z. B. das Dokument digital signieren, und anschließend die Verwendungsrechte wieder für das Dokument aktivieren.

**Syntax:** `InputStream removeUsageRights(InputStream inputFile)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p> </p> <p>inputFile</p> </td>
   <td>Geben Sie den InputStream an, der das PDF-Dokument darstellt, von dem die Verwendungsrechte<br /> entfernt werden sollen. Sie können durch LiveCycle Rights Management oder durch AEM Forms Document Security geschützte Dokumente verwenden.</td>
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
System.out.println("RE rights removed successfully from the document.”);
outputStream.close();
inputFileStream.close();
```
