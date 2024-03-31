---
title: Schützen von Dokumenten im Auftrag einer anderen Person
description: Erfahren Sie, wie AEM Forms Document Security Java™ SDK APIs bietet, mit denen ein Benutzerkonto ein Dokument im Namen einer anderen Person schützen kann.
geptopics: SG_AEMFORMS/categories/working_with_document_security
feature: Document Security
exl-id: e5c80569-d3c0-4358-9b91-b98a64d1c004
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 100%

---

# Schützen von Dokumenten im Auftrag einer anderen Person {#protect-a-document-on-behalf-of-another-user}

Das AEM Forms Document Security Java™ SDK bietet APIs, mit denen ein Benutzerkonto ein Dokument im Namen einer anderen Person schützen kann, ohne die Berechtigungen zum Bearbeiten des Dokuments zu erhalten. Sie können die APIs in einem Workflow-Prozess oder programmgesteuert als Dokumentdienst verwenden. Die neuen APIs sind:

* **protectDocumentUse** die ProtectDocument-API zum Anwenden einer Richtlinie auf ein Dokument im Namen eines

  anderen Benutzerkontos auf ein Dokument anzuwenden. Die Berechtigungen des Benutzerkontos, das zum Anwenden der Richtlinie verwendet wird, bleiben auf den Schutz des Dokuments beschränkt. Es erhält keine Rechte zum Öffnen und Anzeigen des Dokuments. RMSecureDocumentResult protectDocument(Document inDoc, String documentName, String policySetName, String policyName, RMLocale locale, boolean bExactMatchForNames)

* **createLicenseUse** die CreateLicense-API, damit Sie eine Lizenz für eine Richtlinie im Namen eines anderen Benutzerkontos erstellen können. PublishLicenseDTO createLicense(String policyId, String documentName, boolean logSecureDocEvent)
* **protectDocumentWithCoverPageUse** die ProtectDocumentWithCoverPage-API, damit Sie eine Richtlinie anwenden und im Namen einer anderen Person einem Dokument eine Titelseite hinzufügen können. Die Berechtigungen des Benutzerkontos, das zum Anwenden der Richtlinie verwendet wird, bleiben auf den Schutz des Dokuments beschränkt. Es erhält keine Rechte zum Öffnen und Anzeigen des Dokuments. RMSecureDocumentResult protectDocumentWithCoverPage(Document inDoc, String documentName, String policySetName, String policyName, Document coverDoc, boolean bExactMatchForNames)

## Verwenden der APIs zum Schützen von Dokumenten im Namen einer anderen Person {#using-the-apis-to-protect-a-document-on-behalf-of-another-user}

Führen Sie die folgenden Schritte aus, damit Sie ein Dokument im Namen einer anderen Person schützen können, ohne die Berechtigungen zum Bearbeiten des Dokuments zu erhalten:

1. Erstellen Sie einen Richtliniensatz. Beispiel: PolicySet1.
1. Erstellen Sie eine Richtlinie im neu erstellten Richtliniensatz. Beispiel: Policy1 in PolicySet1.
1. Erstellen Sie ein Benutzerkonto mit der Rolle „Rights Management-Endbenutzer“. Beispiel: User1. Legen Sie die Berechtigungen zum Anzeigen von Dokumenten, die mit Policy1 geschützt wurden, für den neu erstellten Benutzer fest.
1. Erstellen Sie eine Rolle. Beispiel: Role1. Geben Sie der neu erstellten Rolle die Berechtigung „Dienst aufrufen“. Erstellen Sie ein Benutzerkonto mit der neu erstellten Rolle. Beispiel: User2. Sie können User2 oder einen bzw. eine Admin verwenden, um eine SDK-Verbindung zu erstellen und den protectDocument-Dienst aufzurufen.

   Jetzt können Sie den folgenden Beispiel-Code ausführen, um ein Dokument zu schützen, ohne der Person, die das Dokument schützt, Berechtigungen zum Bearbeiten des Dokuments zu erteilen:

   ```java
   import java.io.File;
   import java.io.FileInputStream;
   import java.io.FileNotFoundException;
   import java.io.FileOutputStream;
   import java.io.IOException;
   import java.io.InputStream;
   import java.util.Properties;
   
   import com.adobe.edc.common.dto.PublishLicenseDTO;
   import com.adobe.edc.sdk.SDKException;
   import com.adobe.idp.Document;
   import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
   import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
   import com.adobe.livecycle.rightsmanagement.RMSecureDocumentResult;
   import com.adobe.livecycle.rightsmanagement.client.DocumentManager;
   import com.adobe.livecycle.rightsmanagement.client.RightsManagementClient;
   import com.adobe.livecycle.rightsmanagement.client.RightsManagementClient2;
   
   public class PublishAsProtectAPI {
   
   private static final String unprotectedFileName = "C:\\unprotected.pdf";
   private static final String protectedFileName = "C:\\protect.pdf";
   private static final String coverFileName = "C:\\CoverPage.pdf";
   private static final String POLICY_ID = "2EF66008-5E2D-1034-9B06-00000A292C18"; 
   
   public static void main(String[] args) {
   
   try {
   
   Properties connectionProps = new Properties();
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT,"http://localhost:8080");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME,"administrator");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD,"password");
   
   // Create a ServiceClientFactory instance
   ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
   testProtectDocument(factory);
   testProtectDocumentWithCoverPage(factory);
   testProtectDocumentJavaPPL(factory);
   
   } 
   catch (Exception ex) {
   ex.printStackTrace(); }
   }
   
   private static void testProtectDocument(ServiceClientFactory factory) throws FileNotFoundException, SDKException {
   // Create a RightsManagementClient object
   RightsManagementClient rmClient = new RightsManagementClient(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient.getDocumentManager();
   //Reference a policy-protected PDF document from which to remove a policy
   FileInputStream is = new FileInputStream(unprotectedFileName);
   Document inPDF = new Document(is);
   long startTime = System.currentTimeMillis();
   //Remove a policy from the policy-protected PDF document
   RMSecureDocumentResult securePDF = documentManager.protectDocument(inPDF, "test", "newPolicySet", "latest", "DefaultDom", "administrator", null, true);
   System.out.println("Total Time taken for protectDocument = " + (System.currentTimeMillis() - startTime));
   //Save the unsecured PDF document
   File myFile = new File(protectedFileName);
   securePDF.getProtectedDoc().copyToFile(myFile);
   }
   
   private static void testProtectDocumentWithCoverPage(ServiceClientFactory factory) throws FileNotFoundException, SDKException {
   // Create a RightsManagementClient object
   RightsManagementClient rmClient = new RightsManagementClient(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient.getDocumentManager();
   //Reference a policy-protected PDF document from which to remove a policy
   FileInputStream is = new FileInputStream(unprotectedFileName);
   Document inPDF = new Document(is);
   FileInputStream coverIS = new FileInputStream(coverFileName);
   Document inCoverPDF = new Document(coverIS);
   long startTime = System.currentTimeMillis();
   //Remove a policy from the policy-protected PDF document
   RMSecureDocumentResult securePDF = documentManager.protectDocumentWithCoverPage(inPDF, "test", "newPolicySet", "latestPolicy", inCoverPDF, true);
   System.out.println("Total Time taken for Page0ProtectDocument = " + (System.currentTimeMillis() - startTime));
   //Save the unsecured PDF document
   File myFile = new File(protectedFileName);
   securePDF.getProtectedDoc().copyToFile(myFile);
   }
   
   private static PublishLicenseDTO testProtectDocumentJavaPPL (ServiceClientFactory factory) throws SDKException, FileNotFoundException, IOException {
   // Create a RightsManagementClient object
   RightsManagementClient2 rmClient2 = new RightsManagementClient2(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient2.getDocumentManager();
   long startTime = System.currentTimeMillis();
   PublishLicenseDTO license = documentManager.createLicense(POLICY_ID, "Out.pdf", true);
   System.out.println("Create License totalTime = " + (System.currentTimeMillis() - startTime));
   startTime = System.currentTimeMillis();
   // Reference a PDF document to which a policy is applied
   InputStream inputFileStream = new FileInputStream(unprotectedFileName);
   // Apply a policy to the PDF document
   InputStream protectPDF = rmClient2.getRightsManagementEncryptionService().protectDocument(inputFileStream, license);
   // Save the policy-protected PDF document
   File myFile = new File(protectedFileName);
   // write the inputStream to a FileOutputStream
   FileOutputStream outputStream = new FileOutputStream(myFile);
   int read = 0;
   byte[] bytes = new byte[1024];
   while ((read = protectPDF.read(bytes)) != -1) {
   outputStream.write(bytes, 0, read);
   }
   System.out.println("protectPDFDocument totalTime = " + (System.currentTimeMillis() - startTime));
   outputStream.close();
   inputFileStream.close();
   System.out.println("Document Protected Successfully");
   return license;
   }
   }
   ```
