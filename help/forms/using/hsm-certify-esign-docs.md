---
title: Verwenden von HSM, um Dokumente digital zu signieren oder zertifizieren
description: Verwenden eines HSM-Servers oder E-Token-Geräts zum Signieren/Zertifizieren von PDF-Dokumenten.
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Services
exl-id: 62adca19-8ed0-48b3-b7eb-9dbc3d8f96c6
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 100%

---

# Verwenden von HSM, um Dokumente digital zu signieren oder zertifizieren {#use-hsm-to-digitally-sign-or-certify-documents}

Hardware-Sicherheitsmodule (HSM) und E-Token sind dedizierte, extrasichere und manipulationsgeschützte Computer-Geräte zum sicheren Verwalten, Verarbeiten und Speichern digitaler Schlüssel. Diese Geräte werden direkt an einen Computer oder Netzwerk-Server angeschlossen.

Adobe Experience Manager Forms kann in einem HSM oder E-Token gespeicherte Berechtigungen verwenden, um E-Signaturen oder Server-seitige digitale Signaturen auf ein Dokument anzuwenden. So verwenden Sie ein HSM- oder E-Token-Gerät mit AEM Forms:

1. [Aktivieren Sie den DocAssurance-Dienst.](#configuredocassurance)
1. [Erstellen Sie einen Aliasnamen für das HSM- oder E-Token-Gerät in der AEM-Web-Konsole.](#configuredeviceinaemconsole)
1. [Verwenden Sie die DocAssurance-Dienst-APIs, um Dokumente mit den auf dem Gerät gespeicherten digitalen Schlüsseln zu signieren oder zu zertifizieren.](#programatically)

## Bevor Sie die HSM- oder E-Token-Geräte mit AEM Forms konfigurieren {#configurehsmetoken}

* Installieren Sie das [AEM Forms-Add-on](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html)-Paket.
* Installieren und konfigurieren Sie die HSM- oder E-Token-Client-Software auf demselben Computer wie den AEM-Server. Die Client-Software ist für die Kommunikation mit den HSM- und E-Token-Geräten erforderlich.

## Aktivieren des DocAssurance-Dienstes {#configuredocassurance}

Standardmäßig ist der DocAssurance-Dienst nicht aktiviert. Führen Sie zum Aktivieren des Dienstes folgende Schritte durch:

1. Beenden Sie die Autoreninstanz Ihrer AEM Forms-Umgebung.

1. Öffnen Sie die Datei „[AEM_root]\crx-quickstart\conf\sling.properties“ zur Bearbeitung.

   >[!NOTE]
   >
   >Wenn Sie die Datei „[AEM_root]\crx-quickstart\bin\start.bat“ zum Starten der AEM-Instanz verwendet haben, öffnen Sie die Datei „[AEM_root]\crx-quickstart\sling.properties“ zur Bearbeitung.

1. Fügen Sie der Datei „sling.properties“ die folgenden Eigenschaften hinzu oder ersetzen Sie sie:

   ```shell
   sling.bootdelegation.sun=sun.*,com.sun.*,sun.misc.*
   sling.bootdelegation.ibm=com.ibm.xml.*,com.ibm.*
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Speichern und schließen Sie die Datei „sling.properties“.
1. Starten Sie die AEM-Instanz neu.

>[!NOTE]
>
> Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

<!--

## Set up certificates for Reader extensions {#set-up-certificates-for-reader-extensions}

Perform the following steps to setup certificates:

1. Log in to AEM Author instance as an administrator.

1. Click **Adobe Experience Manager** on Global Navigation Bar. Go to **Tools** &gt;  **Security** &gt;  **Users**.
1. Click the **name** field of the user account. The **Edit User Settings** page opens.
1. On the AEM Author instance, certificates reside in a KeyStore. If you have not created a KeyStore earlier, click **Create KeyStore** and set a new password for the KeyStore. If the server already contains a KeyStore, skip this step.

1. On the **Edit User Settings** page, click **Manage KeyStore**.

1. On KeyStore Management dialog, expand the **Add Private Key from Key Store file** option and provide an alias. The alias is used to perform the Reader Extensions operation.
1. To upload the certificate file, click **Select Key Store File** and upload a `.pfx` file.
1. Add the **Key Store Password**,**Private Key Password**, and **Private Key Alias** that is associated with the certificate to the respective fields. Click **Submit**.

   >[!NOTE]
   >
   >To determine the **Private Key Alias** of a certificate, you can use the Java keytool command: `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

   >[!NOTE]
   >
   >In the **Key Store Password** and **Private Key Password** fields, specify the password provided with the certificate file.

>[!NOTE]
>
>For AEM Forms on OSGi, to verify the signed PDF, the root certificate installed in the Trust Store.

>[!NOTE]
>
>On moving to production environment, replace your evaluation credentials with production credentials. Ensure that you delete your old Reader Extensions credentials, before updating an expired or evaluations credential.

-->


## Erstellen eines Aliasnamens für das Gerät {#configuredeviceinaemconsole}

Der Aliasname enthält alle Parameter, die ein HSM oder E-Token erfordert. Befolgen Sie die nachstehenden Anweisungen, um einen Aliasnamen für jede HSM- oder E-Token-Berechtigung zu erstellen, mit der E-Signaturen oder digitale Signaturen verwendet werden:

1. Öffnen Sie die AEM-Konsole. Die Standard-URL der AEM-Konsole lautet „https://&lt;Host>:&lt;Port>/system/console/configMgr“.
1. Öffnen Sie den **HSM Credentials Configuration Service** und geben Sie Werte in die folgenden Felder ein:

   * **Berechtigungsalias**: Geben Sie eine Zeichenfolge ein, die verwendet wird, um den Aliasnamen zu identifizieren. Dieser Wert wird als Eigenschaft für einige Digital Signatures-Vorgänge wie etwa das Signieren eines Signaturfelds verwendet.
   * **DLL Path** (DLL-Pfad): Geben Sie den Pfad Ihrer HSM- oder E-Token-Client-Bibliothek auf dem Server an. Beispiel: `C:\Program Files\LunaSA\cryptoki.dll`. In einer Cluster-Umgebung müssen Sie sicherstellen, dass alle Server im Cluster denselben Pfad verwenden.
   * **HSM-Pin**: Legen Sie ein Kennwort fest, das benötigt wird, um auf den Geräteschlüssel zuzugreifen.
   * **HSM Slot ID** (HSM-Steckplatz-ID): Geben Sie eine Steckplatz-ID als Ganzzahl an. Die Steckplatz-ID wird für jeden Client einzeln festgelegt. Sie wird verwendet, um den Steckplatz im HSM zu identifizieren, das den privaten Schlüssel zum Signieren/Zertifizieren enthält.

   >[!NOTE]
   >
   >Geben Sie beim Konfigurieren von eToken einen numerischen Wert für das HSM-Steckplatz-ID-Feld an. Ein numerischer Wert ist erforderlich, um Signaturen-Vorgänge zu ermöglichen.

   * **Certificate SHA1** (SHA1-Zertifikat): Geben Sie den SHA1-Wert (Fingerabdruck) der öffentlichen Schlüsseldatei (.cer) für die verwendete Berechtigung an. Stellen Sie sicher, dass in dem SHA1-Wert keine Leerzeichen verwendet werden.
   * **HSM-Gerätetyp**: Wählen Sie den HSM- oder eToken-Gerätehersteller aus (Luna oder anderer). 

   Klicken Sie auf **Speichern**. Das Hardware-Sicherheitsmodul ist für AEM Forms konfiguriert. Jetzt können Sie das Hardware-Sicherheitsmodul mit AEM Forms verwenden, um Dokumente zu signieren oder zu zertifizieren.

## Verwenden der DocAssurance-Dienst-APIs zum Signieren oder Zertifizieren eines Dokuments mit auf dem Gerät gespeicherten digitalen Schlüsseln  {#programatically}

Der folgende Beispiel-Code verwendet ein HSM oder E-Token, um ein Dokument zu signieren oder zertifizieren.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * ___________________
 *
 * Copyright 2014 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.ByteArrayInputStream;
import java.io.IOException;
import java.io.InputStream;

import javax.jcr.Binary;
import javax.jcr.Node;
import javax.jcr.RepositoryException;
import javax.jcr.Session;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.api.SlingRepository;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.DocAssuranceServiceOperationTypes;
import com.adobe.fd.docassurance.client.api.SignatureOptions;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.pdf.inputs.CredentialContext;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferences;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferencesImpl;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.PDFSignatureAppearanceType;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.TextDirection;
import com.adobe.fd.signatures.pki.client.types.common.HashAlgorithm;
import com.adobe.fd.signatures.pki.client.types.common.RevocationCheckStyle;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.GeneralPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferencesImpl;

/**
 * Digital signatures can be applied to PDF documents to provide a level of security. Digital signatures, like handwritten signatures, provide a means by which signers
 * identify themselves and make statements about a document. The technology used to digitally sign documents helps to ensure that both the signer and recipients are clear
 * about what was signed and confident that the document was not altered since it was signed.
 *
 * PDF documents are signed by means of public-key technology. A signer has two keys: a public key and a private key. The private key is stored in a user's credential that
 * must be available at the time of signing. The public key is stored in the user's certificate that must be available to recipients to validate the signature. Information
 * about revoked certificates is found in certificate revocation lists (CRLs) and Online Certificate Status Protocol (OCSP) responses distributed by Certificate Authorities (CAs).
 * The time of signing can be obtained from a trusted source known as a Timestamping Authority.
 *
 * The following Java code example digitally signs a PDF document that is based on a PDF file.
 * The alias that is specified for the security credential is secure, and revocation checking is performed.
 * Because no CRL or OCSP server information is specified, the server information is obtained from the certificate used to
 * digitally sign the PDF document
 *
 * PreRequisites - Digital certificate for signing the document has to be uploaded on Granite Key Store
 */

@Component
@Service(value=Sign.class)
public class Sign{
 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to the pdf document stored at JCR node
  * @param outputFile - path to the pdf document where the output needs to be stored
  * @throws IOException
  * @throws RepositoryException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  */
 public void signExtend(String inputFile, String outputFile, String alias) throws IOException, RepositoryException, InvalidArgumentException, DocAssuranceException{

  Document inDoc = new Document(inputFile);
  Document outDoc = null;

  Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try {

          /** resourceResolver with admin privileges to be passed to SignatureServiceAPI and Reader Extensions
          the resource resolver for signature options has to be corresponding to the user who has the signing certificate in his granite key store
          the resource resolver for signature options has to be corresponding to the user who has the credential for reader extension in his granite key store
          here we are using the same resource resolver
          */
          adminSession = slingRepository.loginAdministrative(null);
             resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

             //retrieve specifications for each of the services, you may pass null if you do not want to use that service
             //as we do not want encryption in this case, passing null for Encryption Options
             //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
    outDoc = docAssuranceService.secureDocument(inDoc, null, getSignatureOptions(alias,resourceResolver),null,null);
        }
  catch(Exception e){
   e.printStackTrace();
  }
        finally{
            /**
             * always close the PDFDocument object after your processing is done.
             */
            if(inDoc != null){
                inDoc.close();
            }
            if(adminSession != null && adminSession.isLive()){
                if(resourceResolver != null){
                    resourceResolver.close();
                }
                adminSession.logout();
            }
        }

        //flush the output document contents to JCR Node
  flush(outDoc, outputFile);

 }

 /**
  *
  * @param rr resource resolver corresponding to the user with the access to signing credential for the
  * given alias "allcertificatesanypolicytest11ee_new" in this case
  * @return SignatureOptions
  */
 private SignatureOptions getSignatureOptions(String alias, ResourceResolver rr){

  //create an instance of SignatureOptions
  SignatureOptions signatureOptions = SignatureOptions.getInstance();

  //set the operation you want to perform - SIGN/CERTIFY
  signatureOptions.setOperationType(DocAssuranceServiceOperationTypes.SIGN);

  //field to sign
  String fieldName = "Signature1" ;

        //Hash Algo to be used to compute digest the PDF document
        HashAlgorithm algo = HashAlgorithm.SHA384;

        //Reason for signing/certifying
        String reason = "Test Reason";

        //location of the signer
        String location = "Test Location";

        //contact info of the signer
        String contactInfo = "Test Contact";

        //Create a PDFSignatureAppearanceOptions object
        //and show date information
        PDFSignatureAppearenceOptions appOptions = new PDFSignatureAppearenceOptions(
                PDFSignatureAppearanceType.NAME, null, 1.0d, null, true, true,
                true, true, true, true, true, TextDirection.AUTO);

        signatureOptions.setSignatureFieldName(fieldName);
        signatureOptions.setAlgo(algo);
        signatureOptions.setContactInfo(contactInfo);
        signatureOptions.setLocation(location);
        signatureOptions.setSigAppearence(appOptions);
        signatureOptions.setReason(reason);
        signatureOptions.setDssPref(getDSSPreferences(rr));
        signatureOptions.setCredential(new CredentialContext(alias, rr, true));
  return signatureOptions;
 }

 private DSSPreferences getDSSPreferences(ResourceResolver rr){
  //sets the DSS Preferences
        DSSPreferencesImpl prefs = DSSPreferencesImpl.getInstance();
        prefs.setPKIPreferences(getPKIPreferences());
        GeneralPreferencesImpl gp = (GeneralPreferencesImpl) prefs.getPKIPreferences().getGeneralPreferences();
        gp.setDisableCache(true);
        return prefs;
    }

    private PKIPreferences getPKIPreferences(){
     //sets the PKI Preferences
        PKIPreferences pkiPref = new PKIPreferencesImpl();
        pkiPref.setCRLPreferences(getCRLPreferences());
        pkiPref.setPathPreferences(getPathValidationPreferences());
        return pkiPref;
    }

    private CRLPreferences getCRLPreferences(){
        //specifies the CRL Preferences
        CRLPreferencesImpl crlPrefs = new CRLPreferencesImpl();
        crlPrefs.setRevocationCheck(RevocationCheckStyle.CheckIfAvailable);
        crlPrefs.setGoOnline(true);
        return crlPrefs;
    }

    private PathValidationPreferences getPathValidationPreferences(){
     //sets the path validation preferences
        PathValidationPreferencesImpl pathPref = new PathValidationPreferencesImpl();
        pathPref.setDoValidation(false);
        return pathPref;

    }

    /**
     * sets Unlock Options for encrypted PDF
     */
    private UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }
    /**
     * This method copies the data from {@code Document}, to the specified file at the given resourcePath.
     * @param doc
     * @param resourcePath
     * @throws IOException
     */
    private void flush(Document doc, String resourcePath) throws IOException {
   //extracts the byte data from Document
   byte[] output = doc.getInlineData();
   Binary opBin;
   Session adminSession = null;
      try {
         adminSession = slingRepository.loginAdministrative(null);

         //get access to the specific node
         //here we are assuming that node exists
           Node node = adminSession.getNode(resourcePath);

           //convert byte[] to Binary
           opBin = adminSession.getValueFactory().createBinary((InputStream)new ByteArrayInputStream(output));

           //set the Binary data value to node's jcr:data
           node.getNode("jcr:content").getProperty("jcr:data").setValue(opBin);
      } catch (RepositoryException e) {

      }
      finally{

       if(adminSession != null && adminSession.isLive()){
        try {
      adminSession.save();
      adminSession.logout();
     } catch (RepositoryException e) {

     }

             }
      }

  }
}
```

Wenn Sie ein Upgrade von AEM 6.0 Forms oder AEM 6.1 Forms durchgeführt haben und in der vorherigen Version den DocAssurance-Dienst verwendet haben:

* Wenn Sie den DocAssurance-Dienst ohne HSM oder E-Token-Gerät nutzen möchten, verwenden Sie weiterhin den vorhandenen Code.
* Um den DocAssurance-Dienst mit einem HSM oder E-Token-Gerät zu verwenden, ersetzen Sie den vorhandenen CredentialContext-Objekt-Code durch die unten aufgeführte API.

```java
/**
  *
  * @param credentialAlias alias of the PKI Credential stored in CQ Key Store or
  * the alias of the HSM Credential configured using HSM Credentials Configuration Service.
  * @param resourceResolver corresponding to the user with the access to the key store and trust store.
  * @param isHSMCredential if the alias is corresponding to HSM Credential.
  */
 public CredentialContext(String credentialAlias, ResourceResolver resourceResolver, boolean isHSMCredential);
```

Ausführliche Informationen zu APIs und Beispiel-Code des DocAssurance-Dienstes finden Sie unter [Programmgesteuerte Verwendung von AEM-Dokumentendiensten](/help/forms/using/aem-document-services-programmatically.md).
