---
title: Schnellstart (SOAP) für die Java™-API für den Verschlüsselungsdienst
description: Erfahren Sie, wie Sie Verschlüsselungen vornehmen, die kennwortbasierte/zertifikatsbasierte Verschlüsselung entfernen, Entsperrungen vornehmen und den Verschlüsselungstyp für PDF-Dokumente mithilfe der Java™-API im SOAP-Modus ermitteln.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
role: Developer
exl-id: e8b2aa43-ac27-410d-a809-56bfd1c2fcb1
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations,AEM Forms on JEE
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 100%

---

# Schnellstart (SOAP) für die Java™-API für den Verschlüsselungsdienst {#encryption-service-java-api-quickstart-soap}

[Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments unter Verwendung der Java™-API](encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Entfernen einer kennwortbasierten Verschlüsselung unter Verwendung der Java™-API](encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

[Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit einem Zertifikat unter Verwendung der Java™-API](encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Schnellstart (SOAP-Modus): Entfernen einer zertifikatsbasierten Verschlüsselung unter Verwendung der Java™-API](encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Schnellstart (SOAP-Modus): Entsperren eines verschlüsselten PDF-Dokuments unter Verwendung der Java™-API](encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Bestimmen des Verschlüsselungstyps unter Verwendung der Java™-API](encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

AEM Forms-Vorgänge können mit der stark typisierten AEM Forms-API ausgeführt werden, und der Verbindungsmodus sollte auf SOAP festgelegt werden.

>[!NOTE]
>
>Die Schnellstarts für die Programmierung mit AEM Forms basieren auf dem Forms Server, der auf dem JBoss® Application Server und dem Microsoft® Windows-Betriebssystem eingesetzt wird. Wenn Sie jedoch ein anderes Betriebssystem wie UNIX® verwenden, ersetzen Sie Windows-spezifische Pfade durch Pfade, die vom jeweiligen Betriebssystem unterstützt werden. Wenn Sie einen anderen J2EE-Anwendungs-Server verwenden, müssen Sie ebenfalls sicherstellen, dass Sie gültige Verbindungseigenschaften angeben. Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mithilfe der Java™-API {#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api}

Im folgenden Java™-Code-Beispiel wird ein PDF-Dokument namens *Loan.pdf* mit dem Kennwortwert `OpenPassword` verschlüsselt. Das primäre Kennwort lautet `PermissionPassword`. Das geschützte PDF-Dokument wird als PDF-Datei mit dem Namen *EncryptLoan.pdf* gespeichert. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-encryption-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.File;
 import java.io.FileInputStream;
 import java.util.ArrayList;
 import java.util.List;
 import java.util.Properties;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.encryption.client.*;
 
 public class PasswordEncryptPDFSoap{
 
     public static void main(String[] args) {
 
     try{
         //Set connection properties required to invoke AEM Forms using SOAP mode
         Properties connectionProps = new Properties();
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
         //Create a ServiceClientFactory instance
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
         //Create an EncryptionServiceClient object
         EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);
 
         //Specify the PDF document to encrypt with a password
         FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf");
         Document inDoc = new Document (fileInputStream);
 
         //Create a PasswordEncryptionOptionSpec object that stores encryption run-time values
         PasswordEncryptionOptionSpec passSpec = new PasswordEncryptionOptionSpec();
 
         //Specify the PDF document resource to encrypt
         passSpec.setEncryptOption(PasswordEncryptionOption.ALL);
 
         //Specify the permission associated with the password
         //These permissions enable data to be extracted from a password
         //protected PDF form
         List<PasswordEncryptionPermission> encrypPermissions = new ArrayList<PasswordEncryptionPermission>();
         encrypPermissions.add(PasswordEncryptionPermission.PASSWORD_EDIT_ADD);
         encrypPermissions.add(PasswordEncryptionPermission.PASSWORD_EDIT_MODIFY);
         passSpec.setPermissionsRequested(encrypPermissions);
 
         //Specify the Acrobat version
         passSpec.setCompatability(PasswordEncryptionCompatability.ACRO_7);
 
         //Specify the password values
         passSpec.setDocumentOpenPassword("OpenPassword");
         passSpec.setPermissionPassword("PermissionPassword");
 
         //Encrypt the PDF document
         Document encryptDoc = encryptClient.encryptPDFUsingPassword(inDoc,passSpec);
 
         //Save the password-encrypted PDF document
         File outFile = new File("C:\\Adobe\EncryptLoan.pdf");
         encryptDoc.copyToFile (outFile);
 
         }catch (Exception e) {
             e.printStackTrace();
         }
     }
 }
```

## Schnellstart (SOAP-Modus): Entfernen einer kennwortbasierten Verschlüsselung mithilfe der Java™-API {#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api}

Im folgenden Java™-Code-Beispiel wird eine kennwortbasierte Verschlüsselung von einem PDF-Dokument namens *EncryptLoan.pdf* entfernt. Der primäre Kennwortwert, der zum Entfernen der kennwortbasierten Verschlüsselung verwendet wird, lautet *PermissionPassword*. Das ungeschützte PDF-Dokument wird als PDF-Datei mit dem Namen *noEncryptionLoan.pdf* gespeichert. (Siehe [Entfernen der Kennwortverschlüsselung](/help/forms/developing/encrypting-decrypting-pdf-documents.md#removing-password-encryption).)

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-encryption-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.File;
 import java.io.FileInputStream;
 import java.util.Properties;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.encryption.client.*;
 
 public class RemovePasswordFromPDFSOAP {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create an EncryptionServiceClient object
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);
 
             //Get the encrypted PDF from which to remove password-based encryption
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\EncryptLoan.pdf");
             Document inDoc = new Document (fileInputStream);
 
             //Remove password-based encryption from the PDF document
             Document encryptDoc = encryptClient.removePDFPasswordSecurity(inDoc,"PermissionPassword");
 
             //Save the unsecured PDF document
             File outFile = new File("C:\\Adobe\noEncryptionLoan.pdf");
             encryptDoc.copyToFile (outFile);
 
         }catch (Exception e) {
             e.printStackTrace();
         }
     }
 }
```

## Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java™-API {#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api}

Im folgenden Java™-Code-Beispiel wird ein PDF-Dokument namens *Loan.pdf* mit einem Zertifikat namens *Encryption.cer* verschlüsselt. Das verschlüsselte PDF-Dokument wird als PDF-Datei mit dem Namen *EncryptLoanCert.pdf* gespeichert. (Siehe [Verschlüsseln von PDF-Dokumenten mit Zertifikaten](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).)

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-encryption-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.File;
 import java.io.FileInputStream;
 import java.util.ArrayList;
 import java.util.List;
 import java.util.Properties;
 
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.encryption.client.*;
 
 public class PKIEncryptPDFSoap {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory instance
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create an EncryptionServiceClient object
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);
 
             //Specify the PDF document to encrypt with a certificate
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf");
             Document inDoc = new Document (fileInputStream);
 
             //Set the List that stores PKI information
             List pkiIdentities = new ArrayList();
 
             //Set the Permission List
             List permList = new ArrayList();
             permList.add(CertificateEncryptionPermissions.PKI_ALL_PERM) ;
 
             //Create a Recipient object to store certificate information
             Recipient recipient = new Recipient();
 
             //Specify the private key that is used to encrypt the document
             FileInputStream fileInputStreamCert = new FileInputStream("C:\\Adobe\Encryption.cer");
             Document privateKey = new Document (fileInputStreamCert);
             recipient.setX509Cert(privateKey);
 
             //Create an EncryptionIdentity object
             CertificateEncryptionIdentity encryptionId = new CertificateEncryptionIdentity();
             encryptionId.setPerms(permList);
             encryptionId.setRecipient(recipient);
 
             //Add the EncryptionIdentity to the list
             pkiIdentities.add(encryptionId);
 
             //Set encryption run-time options
             CertificateEncryptionOptionSpec certOptionsSpec = new CertificateEncryptionOptionSpec();
             certOptionsSpec.setOption(CertificateEncryptionOption.ALL);
             certOptionsSpec.setCompat(CertificateEncryptionCompatibility.ACRO_7);
 
             //Encrypt the PDF document with a certificate
             Document encryptDoc = encryptClient.encryptPDFUsingCertificates(inDoc,pkiIdentities, certOptionsSpec);
 
             //Save the encrypted PDF document
             File outFile = new File("C:\\Adobe\EncryptLoanCert.pdf");
             encryptDoc.copyToFile (outFile);
 
             }catch (Exception e) {
                 e.printStackTrace();
             }
     }
 }
 
```

## Schnellstart (SOAP-Modus): Entfernen einer zertifikatsbasierten Verschlüsselung mithilfe der Java™-API {#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api}

Im folgenden Java™-Code-Beispiel wird eine zertifikatsbasierte Verschlüsselung von einem PDF-Dokument namens *EncryptLoanCert.pdf* entfernt. Der Alias des öffentlichen Schlüssels, der zum Entfernen der Verschlüsselung verwendet wird, lautet `Encryption`. Das ungeschützte PDF-Dokument wird als PDF-Datei mit dem Namen *noEncryptionLoan.pdf* gespeichert. (Siehe [Entfernen einer zertifikatbasierten Verschlüsselung](/help/forms/developing/encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).)

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-encryption-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.File;
 import java.io.FileInputStream;
 import java.util.Properties;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.encryption.client.*;
 
 public class RemovePKIFromPDFSOAP {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create an EncryptionServiceClient object
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);
 
             //Get the encrypted PDF document
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\EncryptLoanCert.pdf");
             Document inDoc = new Document (fileInputStream);
 
             //Remove certificate-based encryption from the PDF document
             Document encryptDoc = encryptClient.removePDFCertificateSecurity(inDoc, "Encryption");
 
             //Save the unsecured PDF document
             File outFile = new File("C:\\Adobe\noEncryptionLoan.pdf");
             encryptDoc.copyToFile (outFile);
 
         }catch (Exception e) {
                 e.printStackTrace();
             }
     }
 }
```

## Schnellstart (SOAP-Modus): Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java™-API {#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api}

Im folgenden Java™-Code-Beispiel wird ein kennwortverschlüsseltes PDF-Dokument namens *EncryptLoan.pdf* entsperrt. (Siehe [Entsperren verschlüsselter PDF-Dokumente](/help/forms/developing/encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents).)

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-encryption-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if Forms Server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.FileInputStream;
 import java.util.Properties;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.encryption.client.*;
 
 public class UnlockPDFSOAP {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create an EncryptionServiceClient object
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);
 
             //Get the password-encrypted PDF document to unlock
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\EncryptLoan.pdf");
             Document inDoc = new Document (fileInputStream);
 
             //Specify the password to open the password-encrypted PDF document
             String openPassword = "OpenPassword" ;
 
             //Unlock the password-encrypted PDF document
             Document unlockedDoc = encryptClient.unlockPDFUsingPassword(inDoc,openPassword);
 
         }catch (Exception e) {
                 System.out.println("The following error occurred during this operation " +e.getMessage());
         }
     }
 }
 
```

## Schnellstart (SOAP-Modus): Bestimmen des Verschlüsselungstyps mithilfe der Java™-API {#quick-start-soap-mode-determining-encryption-type-using-the-java-api}

Im folgenden Java™-Code-Beispiel wird der Verschlüsselungstyp bestimmt, mit dem ein PDF-Dokument namens *EncryptLoan.pdf* geschützt ist. (Siehe [Bestimmen des Verschlüsselungstyps](/help/forms/developing/encrypting-decrypting-pdf-documents.md#determining-encryption-type).)

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-encryption-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.FileInputStream;
 import java.util.Properties;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.encryption.client.*;
 
 public class GetEncryptionTypeSOAP {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a EncryptionServiceClient object
             EncryptionServiceClient encryptClient = new EncryptionServiceClient(myFactory);
 
             //Get the PDF document
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\EncryptLoan.pdf");
             Document inDoc = new Document (fileInputStream);
 
             //Determine the type of encryption of the PDF document
             EncryptionTypeResult encryptTypeResult = encryptClient.getPDFEncryption(inDoc);
 
             if (encryptTypeResult.getEncryptionType() == EncryptionType.PASSWORD)
                 System.out.println("The PDF document is protected with password-based encryption");
             else if (encryptTypeResult.getEncryptionType() == EncryptionType.POLICY_SERVER)
                 System.out.println("The PDF document is protected with policy");
             else if (encryptTypeResult.getEncryptionType() == EncryptionType.CERTIFICATE)
                 System.out.println("The PDF document is protected with certificate-based encryption");
             else if (encryptTypeResult.getEncryptionType() == EncryptionType.OTHER)
                 System.out.println("The PDF document is protected with another type of encryption");
             else if (encryptTypeResult.getEncryptionType() == EncryptionType.NONE)
                 System.out.println("The PDF document is not protected.");
         }catch (Exception e) {
                 e.printStackTrace();
         }
     }
 }
 
 
 
```
