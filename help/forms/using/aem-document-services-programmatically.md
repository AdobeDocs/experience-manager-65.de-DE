---
title: AEM Document Services programmgesteuert verwenden
seo-title: AEM Document Services programmgesteuert verwenden
description: Erfahren Sie, wie Sie Document Services-APIs zum digitalen Signieren, Verschlüsseln und Generieren von PDF-Dokumenten verwenden können.
seo-description: Erfahren Sie, wie Sie Document Services-APIs zum digitalen Signieren, Verschlüsseln und Generieren von PDF-Dokumenten verwenden können.
uuid: bf5ee197-4daf-4a64-8b6d-2c0d1f232b1c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 32118d3b-54d0-4283-b489-780bdcbfc8d2
translation-type: tm+mt
source-git-commit: c3fddf28c0f2f5377fff7561d29f073cc847c3ca
workflow-type: tm+mt
source-wordcount: '6450'
ht-degree: 85%

---


# AEM Document Services programmgesteuert verwenden  {#using-aem-document-services-programmatically}

Beispiele und Beispiele in diesem Dokument helfen Ihnen, AEM Dokument Services auf einem AEM Forms auf OSGi-Umgebung zu verstehen und zu verwenden. Beispiele und Beispiele für die Umgebung von AEM Forms on JEE finden Sie unter

* [Java-API-Beginn für Signature-Dienst](https://experienceleague.adobe.com/docs/experience-manager-65/forms/developer-reference/programming-aem-forms-jee/java-api-quick-start-code-examples/signature-service-java-api-quick.html?#programming-aem-forms-jee)

* [Java-API-Beginn zum Encryption-Dienst](https://experienceleague.adobe.com/docs/experience-manager-65/forms/developer-reference/programming-aem-forms-jee/java-api-quick-start-code-examples/encryption-service-java-api-quick.html?#developer-reference)

* [Acrobat Reader Extensions Service Java API Quick Beginn](https://experienceleague.adobe.com/docs/experience-manager-65/forms/developer-reference/programming-aem-forms-jee/java-api-quick-start-code-examples/acrobat-reader-dc-extensions-service.html?#developer-reference)

## Voraussetzung {#prerequisite}

* Bevor Sie die DocAssurance-Dienst-APIs verwenden, konfigurieren Sie den DocAssurance-Dienst](/help/forms/using/install-configure-document-services.md).[

* Laden Sie [AEM Forms Client SDK](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) herunter und konfigurieren Sie es mit Ihrem AEM Projekt. Die zum Erstellen von Maven-Projekten mithilfe AEM Dokument-Services erforderlichen Clientklassen sind im [AEM Forms Client SDK](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) verfügbar.

* Lernen Sie [wie Sie Ihr AEM Projekt mit Maven](/help/sites-developing/ht-projects-maven.md) erstellen.

## DocAssurance-Dienst {#docassurance-service}

Der DocAssurance-Dienst umfasst die folgenden Dienste:

* Signature-Dienst
* Encryption-Dienst
* Reader Extension-Dienst

Sie können mithilfe des DocAssurance-Dienstes folgende Vorgänge durchführen:

* [Unsichtbare Signatur hinzufügen](/help/forms/using/aem-document-services-programmatically.md#p-adding-an-invisible-signature-field-p)

* [Signaturfeld hinzufügen](/help/forms/using/aem-document-services-programmatically.md#p-adding-a-signature-field-nbsp-p)
* [Dokumenten-Zeitstempel anwenden](/help/forms/using/aem-document-services-programmatically.md#apply-document-timestamp)

* [Signatur abrufen](/help/forms/using/aem-document-services-programmatically.md#p-getting-signature-p)
* [Signaturfeldliste abrufen](/help/forms/using/aem-document-services-programmatically.md#p-getting-signature-field-list-nbsp-p)
* [Signaturfelder ändern](/help/forms/using/aem-document-services-programmatically.md#p-modifying-signature-fields-nbsp-p)

* [Dokument absichern](/help/forms/using/aem-document-services-programmatically.md#p-securing-documents-p)

* [Verwendungsrechte für Berechtigung abrufen](/help/forms/using/aem-document-services-programmatically.md#p-getting-credential-usage-rights-p)

* [Verwendungsrechte für Dokument abrufen](/help/forms/using/aem-document-services-programmatically.md#p-getting-document-usage-rights-p)

* [Verwendungsrechte entfernen](/help/forms/using/aem-document-services-programmatically.md#p-removing-usage-rights-p)
* [Digitale Signaturen überprüfen](/help/forms/using/aem-document-services-programmatically.md#p-verifying-digital-signatures-p)
* [Mehrere digitale Signaturen überprüfen](/help/forms/using/aem-document-services-programmatically.md#p-verifying-multiple-digital-signatures-p)
* [Digitale Signaturen entfernen](/help/forms/using/aem-document-services-programmatically.md#p-removing-digital-signatures-p)

* [Zertifizierungssignaturfeld abrufen](/help/forms/using/aem-document-services-programmatically.md#p-getting-certifying-signature-field-p)
* [PDF-Verschlüsselungstyp abrufen](/help/forms/using/aem-document-services-programmatically.md#p-getting-pdf-encryption-type-p)
* [Kennwortverschlüsselung entfernen](/help/forms/using/aem-document-services-programmatically.md#p-removing-password-encryption-from-pdf-p)

* [Zertifikatverschlüsselung entfernen](/help/forms/using/aem-document-services-programmatically.md#p-removing-certificate-encryption-p)

>[!NOTE]
>
>Alle diese Dienste verwenden das Dokumentobjekt als  Eingabeparameter, für den das Javadoc unter der URL [https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/index.html](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/index.html) gefunden werden kann

### Unsichtbares Signaturfeld hinzufügen {#adding-an-invisible-signature-field}

Digitale Signaturen werden in Signaturfeldern angezeigt, die eine grafische Darstellung der Signatur enthaltende Formularfelder sind. Signaturfelder können sichtbar oder unsichtbar sein. Unterzeichnende können ein bereits vorhandenes Signaturfeld verwenden, oder ein Signaturfeld kann programmgesteuert hinzugefügt werden. In beiden Fällen muss das Signaturfeld vorhanden sein, bevor ein PDF-Dokument signiert werden kann. Sie können ein Signaturfeld programmgesteuert hinzufügen, indem Sie die Signature-Dienst-Java-API oder die Signature-Webdienst-API verwenden. Sie können einem PDF-Dokument mehr als eine Signatur hinzufügen. Jeder der Signaturfeldnamen muss jedoch eindeutig sein.

**Syntax**:  `addInvisibleSignatureField(Document inDoc, String signatureFieldName, FieldMDPOptionSpec fieldMDPOptionsSpec, PDFSeedValueOptionSpec seedValueOptionsSpec, UnlockOptions unlockOptions)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code></td>
   <td>Dokumentobjekt, das PDF enthält.<br /> </td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code> </td>
   <td>Der Name des Signaturfelds. Dieser Parameter ist obligatorisch und darf keine Null als Wert haben.<br /> </td>
  </tr>
  <tr>
   <td><code>fieldMDPOptionsSpec</code></td>
   <td>Ein <code>FieldMDPOptionSpec</code>-Objekt das die Felder des PDF-Dokuments angibt, die nach dem Signieren im Signaturfeld gesperrt werden. Dieser Parameter ist optional und kann einen Null-Wert akzeptieren.</td>
  </tr>
  <tr>
   <td><code>seedValueOptionsSpec</code></td>
   <td>Ein <code>SeedValueOptions</code>-Objekt, das die verschiedenen Seed-Werte für das Feld angibt. Dieser Parameter ist optional und kann einen Null-Wert akzeptieren.<span class="acrolinxCursorMarker"></span></td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Schließt die Parameter zum Entsperren einer verschlüsselten Datei ein. Dieser Parameter ist nur für die verschlüsselten Dateien erforderlich.</td>
  </tr>
 </tbody>
</table>

Im Folgenden finden Sie ein Beispiel für Java-Code, mit dem einem PDF-Dokument ein unsichtbares Unterschriftsfeld hinzugefügt wird.

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

import java.io.File;
import java.io.IOException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PositionRectangle;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * Digital signatures appear in signature fields, which are form fields that contain a graphic representation of the signature.
 * Signature fields can be visible or invisible. Signers can use a pre existing signature field, or a signature field can be
 * programmatically added. In either case, the signature field must exist before a PDF document can be signed.
 * You can programmatically add a signature field by using the Signature service Java API or Signature web service API.
 * You can add more than one signature field to a PDF document; however, each signature field name must be unique.
 *
 * The following Java code example adds an invisible signature field named SignatureField1 to a PDF document.
 */

@Component
@Service(value=AddInvisibleSignatureField.class)
public class AddInvisibleSignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to an pdf document stored at disk
  * @param outputFile - path where the output file has to be saved
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  *
  */
 public void addInvisibleSignatureField(String inputFile, String outputFile) throws InvalidArgumentException, PDFOperationException, PermissionsException, DuplicateSignatureFieldException, SignaturesBaseException, DocAssuranceException {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
  Document outDoc = null;

        //Specify the name of the signature field
        String fieldName = "SignatureField1";

        //Create a  PositionRectangle object that specifies
        //the signature fields location
        PositionRectangle post = new  PositionRectangle(193,47,133,12);

        //Specify the page number that will contain the signature field
        java.lang.Integer pageNum = new java.lang.Integer(1);

        //Add a signature field to the PDF document
        try {
   outDoc = docAssuranceService.addInvisibleSignatureField(
       inDoc,
       fieldName,
       null,
       null,
       null);
  } catch (Exception e1) {
   // TODO Auto-generated catch block
   e1.printStackTrace();
  } // for an encrypted PDF input, pass unlock options

        //save the outDoc
        try {
   outDoc.copyToFile(outFile);
  } catch (IOException e) {
   // TODO Auto-generated catch block
   e.printStackTrace();
  }
 }

 /**
  *
  * UnlockOptions to be passed to addSignatureField() API to add a signature field in an encrypted pdf document.
  */
 private UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }
}
```

Sie können auch [CAdES](https://de.wikipedia.org/wiki/CAdES)-Spezifikation für das Signieren von Dokumenten verwenden. Verwenden Sie den folgenden Beispielcode, um als Signaturformat [CAdES](https://en.wikipedia.org/wiki/CAdES_%28computing%29) festzulegen.

```java
SigningFormat signingFormat = SigningFormat.CAdES;
sigAppearence.setSigningFormat(signingFormat);
signOptions.setSigAppearence(sigAppearence);
```

### Signaturfeld hinzufügen  {#adding-a-signature-field-nbsp}

Sie können ein Signaturfeld programmgesteuert hinzufügen, indem Sie die Signature-Dienst-Java-API oder die Signature-Webdienst-API verwenden. Sie können einem PDF-Dokument mehrere Signaturfelder hinzufügen. Jeder der Signaturfeldnamen muss jedoch eindeutig sein.

**Syntax**:

```java
public Document addSignatureField(Document inDoc,
 String signatureFieldName,
 Integer pageNo,
 PositionRectangle positionRectangle,
 FieldMDPOptionSpec fieldMDPOptionsSpec,
 PDFSeedValueOptionSpec seedValueOptionsSpec, UnlockOptions unlockOptions)
```

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code></td>
   <td>Dokumentobjekt, das PDF enthält</td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code></td>
   <td>Name des Signaturfelds. Dieser Parameter ist obligatorisch und darf keinen Nullwert akzeptieren.</td>
  </tr>
  <tr>
   <td><code>pageNumber</code></td>
   <td>Die Seitenzahl, auf der das Signaturfeld hinzugefügt wird. Gültige Werte sind 1 bis zur Anzahl der Seiten im Dokument. Dieser Parameter ist obligatorisch und darf keinen Nullwert akzeptieren.<br /> </td>
  </tr>
  <tr>
   <td><code>positionRectangle</code></td>
   <td>Ein <code>PositionRectangle object</code>, das die Position des Signaturfelds angibt. Dieser Parameter ist obligatorisch und darf keinen Nullwert akzeptieren. Wenn das angegebene Rechteck nicht mindestens teilweise innerhalb des Zuschnittrandes der angegebenen Seite liegt, wird eine Ausnahme des Typs <code>InvalidArgumentException</code> ausgegeben. Weder Höhe noch Breite dürfen außerdem den Wert 0 oder einen negativen Wert haben. Der X-Koordinatenwert unten links und der Y-Koordinatenwert unten links dürfen 0 oder größer, jedoch nicht negativ sein und ist relativ zum Zuschnittrand der Seite.</td>
  </tr>
  <tr>
   <td><code>fieldMDPOptionsSpec</code></td>
   <td>Ein <code>FieldMDPOptionSpec</code>-Objekt das die Felder des PDF-Dokuments angibt, die nach dem Signieren im Signaturfeld gesperrt werden. Dies ist ein optionaler Parameter und darf null sein.</td>
  </tr>
  <tr>
   <td><code>seedValueOptionsSpec</code></td>
   <td>Ein <code>SeedValueOptions</code>-Objekt, das die verschiedenen Seed-Werte für das Feld angibt. Dies ist ein optionaler Parameter und darf null sein.</td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dieser Parameter ist nur für die verschlüsselten Dateien erforderlich.</td>
  </tr>
 </tbody>
</table>

Im Folgenden finden Sie ein Beispiel für Java-Code, mit dem einem PDF-Dokument ein Signaturfeld hinzufügt wird.

```java
/*************************************************************************
 *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PositionRectangle;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * Digital signatures appear in signature fields, which are form fields that contain a graphic representation of the signature.
 * Signature fields can be visible or invisible. Signers can use a pre existing signature field, or a signature field can be
 * programmatically added. In either case, the signature field must exist before a PDF document can be signed.
 * You can programmatically add a signature field by using the Signature service Java API or Signature web service API.
 * You can add more than one signature field to a PDF document; however, each signature field name must be unique.
 *
 * The following Java code example adds a signature field named SignatureField1 to a PDF document.
 */

@Component
@Service(value=AddSignatureField.class)
public class AddSignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to an pdf document stored at disk
  * @param outputFile - path where the output file has to be saved
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  *
  */
 public void addSignatureField(String inputFile, String outputFile) throws InvalidArgumentException, PDFOperationException, PermissionsException, DuplicateSignatureFieldException, SignaturesBaseException, DocAssuranceException {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
  Document outDoc = null;

        //Specify the name of the signature field
        String fieldName = "SignatureField1";

        //Create a  PositionRectangle object that specifies
        //the signature fields location
        PositionRectangle post = new  PositionRectangle(193,47,133,12);

        //Specify the page number that will contain the signature field
        java.lang.Integer pageNum = new java.lang.Integer(1);

        //Add a signature field to the PDF document
        try {
   outDoc = docAssuranceService.addSignatureField(
       inDoc,
       fieldName,
       pageNum,
       post,
       null,
       null,
       null);
  } catch (Exception e1) {
   // TODO Auto-generated catch block
   e1.printStackTrace();
  } // for an encrypted PDF input, pass unlock options

        //save the outDoc
        try {
   outDoc.copyToFile(outFile);
  } catch (IOException e) {
   // TODO Auto-generated catch block
   e.printStackTrace();
  }
 }

 /**
  *
  * UnlockOptions to be passed to addSignatureField() API to add a signature field in an encrypted pdf document.
  */
 private UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }
}
```

### Dokumenten-Zeitstempel anwenden  {#apply-document-timestamp}

Sie können ein Dokument programmatisch mit einem Zeitstempel gemäß [PAdES 4](https://de.wikipedia.org/wiki/PAdES) -Spezifikationen versehen. Sie können auch die Spezifikation [CAdES](https://en.wikipedia.org/wiki/CAdES_%28computing%29) für transaktionsbezogene Dokumente verwenden.

**Syntax**:  `applyDocumentTimeStamp(Document doc, VerificationTime verificationTime, ValidationPreferences dssPrefs, ResourceResolver resourceResolver, UnlockOptions unlockOptions)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>doc</code> </td>
   <td>Dokumentobjekt, das PDF enthält.<br /> </td>
  </tr>
  <tr>
   <td><code>VerificationTime</code></td>
   <td>Der Zeitpunkt, zu dem die Signatur überprüft werden muss<br /> </td>
  </tr>
  <tr>
   <td><code>ValidationPreferences</code> </td>
   <td>Präferenzen zum Steuern von Überprüfungskonfigurationen.</td>
  </tr>
  <tr>
   <td><code>ResourceResolver</code></td>
   <td>Ressourcen-Konfliktlöser zum Granite Trust Store.</td>
  </tr>
  <tr>
   <td><code>UnlockOptions</code></td>
   <td>Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist.</td>
  </tr>
 </tbody>
</table>

Die folgenden Codebeispiele fügen einem Dokument einen Zeitstempel gemäß [PAdES 4](https://en.wikipedia.org/wiki/PAdES) hinzu.

```java
package com.adobe.signatures.test;

import java.io.File;

import javax.jcr.Session;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.api.SlingRepository;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.VerificationTime;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferences;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.common.RevocationCheckStyle;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.OCSPPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.TSPPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.TSPPreferencesImpl;

 @Component
 @Service(value=Test.class)
 public class Test {

     @Reference
     private DocAssuranceService docAssuranceService;

     @Reference
     private SlingRepository slingRepository;

     @Reference
     private JcrResourceResolverFactory jcrResourceResolverFactory ;

     /**
      *
      * @param inputFile - path to the pdf document stored at disk
      * @param outputFile - path to the pdf document where the output needs to be stored
      * @throws Exception
      */
     public void TimeStamp(String inputFile, String outputFile) throws Exception{

         File inFile = new File(inputFile);
         Document inDoc = new Document(inFile);

         File outFile = new File(outputFile);
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

              VerificationTime verificationTime = getVerificationTimeForPades();
              ValidationPreferences dssPrefs = getValidationPreferences();

              //retrieve specifications for each of the services, you may pass null if you don't want to use that service
              //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
               outDoc = docAssuranceService.applyDocumentTimeStamp(inDoc, verificationTime, dssPrefs, resourceResolver, null);
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

         outDoc.copyToFile(outFile);

     }

  public  VerificationTime getVerificationTimeForPades(){

         return VerificationTime.SECURE_TIME_ELSE_CURRENT_TIME;

     }

 /**
       * sets ValidationPreferences
       */
      private static ValidationPreferences getValidationPreferences(){

         ValidationPreferencesImpl prefs = new ValidationPreferencesImpl();
         prefs.setPKIPreferences(getPKIPreferences());

         //set the unlock options for processing an encrypted pdf document, do not set if the input doc is unprotected

         return prefs;

     }

   /**
       * sets PKIPreferences
       */
     private static PKIPreferences getPKIPreferences(){
         PKIPreferences pkiPref = new PKIPreferencesImpl();
         pkiPref.setCRLPreferences(getCRLPreferences());
         pkiPref.setPathPreferences(getPathValidationPreferences());
         pkiPref.setOCSPPreferences(getOCSPPref());
         pkiPref.setTSPPreferences(getTspPref());
         return pkiPref;
     }

   /**
      * sets CRL Preferences
      */
     private static CRLPreferences getCRLPreferences(){

         CRLPreferencesImpl crlPrefs = new CRLPreferencesImpl();
         crlPrefs.setRevocationCheck(RevocationCheckStyle.BestEffort);
         crlPrefs.setGoOnline(true);
         return crlPrefs;
     }

     /**
      *
      * sets PathValidationPreferences
      */
     private static PathValidationPreferences getPathValidationPreferences(){
         PathValidationPreferencesImpl pathPref = new PathValidationPreferencesImpl();
         pathPref.setDoValidation(true);
         return pathPref;

     }

   public static TSPPreferences getTspPref(){
   TSPPreferencesImpl tspPrefs=new TSPPreferencesImpl();
   char pass[]=new char[9];

   tspPrefs.setTspServerURL("TSPPrefs_ServerURL");
   tspPrefs.setUsername("TSPPrefs_Username");
   tspPrefs.setPassword(pass);
   tspPrefs.setSize(10240);
   return tspPrefs;
   }

     private static OCSPPreferencesImpl getOCSPPref(){
         OCSPPreferencesImpl ocsp = new OCSPPreferencesImpl();
         ocsp.setRevocationCheck(RevocationCheckStyle.BestEffort);
         return ocsp;
     }

}
```

### Signatur abrufen  {#getting-signature}

Sie können die Namen aller Signaturfelder abrufen, die sich in einem zu signierenden und zertifizierenden PDF-Dokument befinden. Wenn Sie nicht sicher sind, wie die Signaturfeldnamen in einem PDF-Dokument lauten, oder die Namen prüfen möchten, können Sie diese programmgesteuert abrufen. Der Signature-Dienst gibt den vollständig qualifizierten Namen des Signaturfelds zurück, z. B. `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

**Syntax**:  `getSignature(Document doc, String signatureFieldName, UnlockOptions unlockOptions)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>doc</code> </td>
   <td>Dokumentobjekt, das PDF enthält.<br /> </td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code></td>
   <td>Der Name des Signaturfelds, das eine Signatur enthält. Geben Sie den vollqualifizierten Namen des Signaturfelds an. Wenn ein auf einem XFA-Formular basierendes PDF-Dokument verwendet wird, kann ein Teil des Namens des Signaturfelds verwendet werden. Beispielsweise kann <code>form1[0].#subform[1].SignatureField3[3]</code> als <code>SignatureField3[3]</code> angegeben werden.</td>
  </tr>
  <tr>
   <td><code>UnlockOptions</code></td>
   <td>Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden die Signaturinformationen für das angegebene Signaturfeld in einem PDF-Dokument abgerufen.

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

import java.io.File;
import java.util.Iterator;
import java.util.List;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PDFSignatureField;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.signatures.client.types.PDFSignature;

/**
 * You can retrieve the names of all signature fields that are located in a PDF document that you want to sign or certify.
 * If you are unsure of the signature field names that are located in a PDF document or you want to verify the names, you can
 * programmatically retrieve them. The Signature service returns the fully qualified name of the signature field, such as
 * form1[0].grantApplication[0].page1[0].SignatureField1[0].
 *
 * The following Java code example retrieves the Signature Info for the given signature field located in a PDF document.
 */

@Component
@Service(value=GetSignature.class)
public class GetSignature {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  *
  */
 public void GetSignature(String inputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Retrieve signature data for a given signature field.
  //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        PDFSignature pdfSignature = docAssuranceService.getSignature(inDoc,"fieldName",null);

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
}
```

### Signaturfeldliste abrufen   {#getting-signature-field-list-nbsp}

Sie können die Namen aller Signaturfelder abrufen, die sich in einem zu signierenden und zertifizierenden PDF-Dokument befinden. Wenn Sie nicht sicher sind, wie die Signaturfeldnamen in einem PDF-Dokument lauten, können Sie diese programmgesteuert abrufen und prüfen. Der Signature-Dienst gibt den vollständig qualifizierten Namen des Signaturfelds zurück, z. B. `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

**Syntax**:  `public List <PDFSignatureField> getSignatureFieldList (Document inDoc, UnlockOptions unlockOptions)`

**Eingabeparameter**

| Parameter | Beschreibung |
|---|---|
| `inDoc` | Dokumentobjekt, das PDF enthält |
| `unlockOptions` | Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist. |

Im folgenden Java-Codebeispiel werden die Namen von Signaturfeldern in einem PDF-Dokument abgerufen.

```java
/*************************************************************************
 *
 *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------
**************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.util.Iterator;
import java.util.List;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PDFSignatureField;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * You can retrieve the names of all signature fields that are located in a PDF document that you want to sign or certify.
 * If you are unsure of the signature field names that are located in a PDF document or you want to verify the names, you can
 * programmatically retrieve them. The Signature service returns the fully qualified name of the signature field, such as
 * form1[0].grantApplication[0].page1[0].SignatureField1[0].
 *
 * The following Java code example retrieves the names of signature fields located in a PDF document.
 */

@Component
@Service(value=GetSignatureFields.class)
public class GetSignatureFields {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  *
  */
 public void getSignatureFields(String inputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Retrieve the name of the document's signature fields
  //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        List fieldNames = docAssuranceService.getSignatureFieldList(inDoc,null);

        //Obtain the name of each signature field by iterating through the
        //List object
        Iterator iter = fieldNames.iterator();
        int i = 0 ;
        String fieldName="";
        while (iter.hasNext()) {
            PDFSignatureField signatureField = (PDFSignatureField)iter.next();
            fieldName = signatureField.getName();
            System.out.println("The name of the signature field is " +fieldName);
            i++;
        }
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
}
```

### Signaturfelder ändern   {#modifying-signature-fields-nbsp}

Sie können Signaturfelder in einem PDF-Dokument ändern. Das Ändern eines Signaturfelds umfasst das Manipulieren seiner Signaturfeldsperre- oder Seed-Wert-Lexikonwerte.

Ein Feldsperre-Lexikon gibt eine Liste von Feldern an, die gesperrt werden, wenn das Signaturfeld signiert wird. Ein gesperrtes Feld verhindert, dass Benutzer das Feld bearbeiten. Ein Seed-Wert-Lexikon enthält Einschränkungsinformationen, die zum Zeitpunkt der Anwendung der Signatur verwendet werden. Beispiel: Sie können die Berechtigungen ändern, die Aktionen steuern, die auftreten können, ohne dass eine Signatur ungültig wird.

Durch Ändern eines vorhandenen Unterschriftsfelds können Sie das PDF-Dokument entsprechend den sich ändernden Geschäftsanforderungen bearbeiten. Eine neue Geschäftsanforderung erfordert beispielsweise das Sperren aller Dokument-Felder, nachdem das Dokument signiert wurde.

**Syntax**:  `public Document modifySignatureField(Document inDoc, String signatureFieldName, PDFSignatureFieldProperties pdfSignatureFieldProperties, UnlockOptions unlockOptions)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code></td>
   <td>Dokumentobjekt, das PDF enthält</td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code></td>
   <td>Der Name des Signaturfelds. Dieser Parameter ist obligatorisch und darf keinen Nullwert akzeptieren.<br /> </td>
  </tr>
  <tr>
   <td><code>pdfSignatureFieldProperties</code></td>
   <td>Objekt, das Informationen zu den Werten <code>PDFSeedValueOptionSpec</code> und <code>FieldMDPOptionSpec</code> des Signaturfelds angibt.</td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird ein Signaturfeld geändert, indem alle Felder im Formular gesperrt werden, wenn eine Signatur auf das Signaturfeld angewendet wird.

```java
/*************************************************************************
 *

-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.FieldMDPAction;
import com.adobe.fd.signatures.client.types.FieldMDPOptionSpec;
import com.adobe.fd.signatures.client.types.MDPPermissions;
import com.adobe.fd.signatures.client.types.PDFSeedValueOptionSpec;
import com.adobe.fd.signatures.client.types.PDFSignatureFieldProperties;
import com.adobe.fd.signatures.client.types.PositionRectangle;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.MissingSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignatureFieldSignedException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesOtherException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * You can modify signature fields that are located in a PDF document by using the Java API and web service API. Modifying a signature field involves
 * manipulating its signature field lock dictionary values or seed value dictionary values.
 * A field lock dictionary specifies a list of fields that are locked when the signature field is signed. A locked field prevents users from making
 * changes to the field. A seed value dictionary contains constraining information that is used at the time the signature is applied.
 * For example, you can change permissions that control the actions that can occur without invalidating a signature.
 * By modifying an existing signature field, you can make changes to the PDF document to reflect changing business requirements. For example,
 * a new business requirement may require locking all document fields after the document is signed.
 * This section explains how to modify a signature field by amending both field lock dictionary and seed value dictionary values.
 * Changes made to the signature field lock dictionary result in all fields in the PDF document being locked when a signature field is signed.
 * Changes made to the seed value dictionary prohibit specific types of changes to the document.
 *
 * The following Java code example modifies a signature field named SignatureField1 by locking all fields in the form when a signature is applied to the signature field and ensuring that no changes are allowed.
 * After the Signature service returns the PDF document that contains the modified signature field
 */

@Component
@Service(value=ModifySignatureField.class)
public class ModifySignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @param outFile - path where the output file has to be saved
  *
  *
  */
 public void modifySignatureField(String inputFile, String outFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Specify the name of the signature field
        String fieldName = "SignatureField1";

        //Create a PDFSignatureFieldProperties
        PDFSignatureFieldProperties fieldProperties = new PDFSignatureFieldProperties();

         //Create a PDFSeedValueOptionSpec object that stores
         //seed value dictionary information.
         PDFSeedValueOptionSpec seedOptionsSpec = new PDFSeedValueOptionSpec();

         //Disallow changes to the PDF document. Any change to the document invalidates
         //the signature
         seedOptionsSpec.setMdpValue(MDPPermissions.NoChanges);

         //Create a FieldMDPOptionSpec object that stores
         //signature field lock dictionary information.
         FieldMDPOptionSpec fieldMDPOptionsSpec = new FieldMDPOptionSpec();

         //Lock all fields in the PDF document
         fieldMDPOptionsSpec.setAction(FieldMDPAction.ALL);

         //Set dictionary information
         fieldProperties.setSeedValue(seedOptionsSpec);
         fieldProperties.setFieldMDP(fieldMDPOptionsSpec);

         //Modify the signature field
         //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
         Document modSignatureField =  docAssuranceService.modifySignatureField(inDoc,fieldName,fieldProperties,null);

        //save the modSignatureField
         modSignatureField.copyToFile(new File(outFile));
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
}
```

### PDF-Dokumente zertifizieren  {#certifying-pdf-documents-nbsp}

Sie können ein PDF-Dokument absichern, indem Sie es mit einem bestimmten Signaturtyp (einer zertifizierten Signatur) zertifizieren. Eine zertifizierte Signatur entscheidet sich wie folgt von einer digitalen Signatur:

* Es muss die erste Signatur sein, die auf das PDF-Dokument angewendet wird. Anders ausgedrückt: Wenn die zertifizierte Signatur angewendet wird, müssen andere Signaturfelder im Dokument unsigniert sein. In einem PDF-Dokument ist nur eine zertifizierte Signatur zulässig. Wenn Sie ein PDF-Dokument signieren und zertifizieren möchten, zertifizieren Sie es, bevor Sie es signieren. Nach dem Zertifizieren eines PDF-Dokuments können Sie weitere Signaturfelder digital signieren.
* Der Autor oder Ersteller des Dokuments kann festlegen, dass das Dokument auf bestimmte Arten modifiziert werden kann, ohne dass die zertifizierte Signatur ungültig wird. Das Dokument kann beispielsweise das Ausfüllen von Formularen oder das Kommentieren zulassen. Wenn der Autor festlegt, dass eine bestimmte Änderung nicht zulässig ist, verhindert Acrobat, dass Benutzer das Dokument auf diese Weise ändern. Wenn solche Änderungen durchgeführt werden, wird die zertifizierte Signatur ungültig. Darüber hinaus gibt Acrobat eine Warnung aus, wenn ein Benutzer das Dokument öffnet. (Bei nicht zertifizierten Signaturen werden Änderungen nicht verhindert und Bearbeitungsvorgänge führen nicht dazu, dass die ursprüngliche Signatur ungültig wird.)
* Zum Zeitpunkt des Signierens wird das Dokument auf bestimmte Typen von Inhalt überprüft, durch die die Inhalte eines Dokuments mehrdeutig oder irreführend werden könnten. Beispiel: Eine Anmerkung kann Text auf einer Seite verdecken, der für das Verständnis dessen, was zertifiziert wird, wichtig ist. Eine Erläuterung (gültige Beglaubigung) zu solchen Inhalten kann bereitgestellt werden.

**Syntax**:

```java
secureDocument(Document inDoc, EncryptionOptions encryptionOptions,
 SignatureOptions signatureOptions, ReaderExtensionOptions readerExtensionOptions, UnlockOptions unlockOptions)
```

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>PDF-Dokument für die Dokumenteingabe<br /> </td>
  </tr>
  <tr>
   <td><code>encryptionOptions</code> </td>
   <td>Umfasst die zum Verschlüsseln eines PDF-Dokuments erforderlichen Argumente<br /> </td>
  </tr>
  <tr>
   <td><code>signatureOptions</code></td>
   <td>Umfasst die zum Signieren/Zertifizieren eines PDF-Dokuments erforderlichen Optionen</td>
  </tr>
  <tr>
   <td><code>readerExtensionOptions</code></td>
   <td>Umfasst für Reader Extending eines PDF-Dokuments erforderliche Optionen</td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist.<br /> </td>
  </tr>
 </tbody>
</table>

Mit dem folgenden Codebeispiel wird ein PDF-Dokument zertifiziert, das auf einer PDF-Datei basiert.

```java
/*************************************************************************

-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;

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
import com.adobe.fd.signatures.client.types.MDPPermissions;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.pdf.inputs.CredentialContext;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferences;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferencesImpl;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.PDFSignatureAppearanceType;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.TextDirection;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
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
 * You can secure a PDF document by certifying it with a particular type of signature called a certified signature.
 * A certified signature is distinguished from a digital signature in these ways:
 *
 * It must be the first signature applied to the PDF document; that is, at the time the certified signature is applied, any other signature fields in the document must be unsigned.
 * Only one certified signature is permitted in a PDF document. If you want to sign and certify a PDF document, you must certify it before signing it.
 * After you certify a PDF document, you can digitally sign additional signature fields.
 *
 * The author or originator of the document can specify that the document can be modified in certain ways without invalidating the certified signature. For example,
 * the document may permit filling in forms or commenting. If the author specifies that a certain modification is not permitted, Acrobat restricts users from modifying the document
 * in that way. If such modifications are made, such as by using another application, the certified signature is invalid and Acrobat issues a warning when a user opens the document.
 * (With non-certified signatures, modifications are not prevented, and normal editing operations do not invalidate the original signature.)
 *
 * At the time of signing, the document is scanned for specific types of content that could make the contents of a document ambiguous or misleading. For example, an annotation could
 * obscure some text on a page that is important for understanding what is being certified. An explanation (legal attestation) can be provided about such content.
 * You can programmatically certify PDF documents by using the Signature service Java API or the Signature web service API. When certifying a PDF document, you must reference a security
 * credential that exists in the Credential service.
 *
 * Note: When certifying and signing the same PDF document, if the certify signature is not trusted, a yellow triangle appears next to the first sign signature when you open the PDF document in Acrobat or Adobe Reader.
 * The certifying signature must be trusted to avoid this situation.
 *
 * The following Java code example certifies a PDF document that is based on a PDF file.
 *
 * PreRequisites - Digital certificate for certifying the document has to be uploaded on AEM Key Store.
 *
 */

@Component
@Service(value=Certify.class)
public class Certify {

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
 public void certify(String inputFile, String outputFile) throws IOException, RepositoryException, InvalidArgumentException, DocAssuranceException{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
  Document outDoc = null;

  Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try {

          /** resourceResolver to be passed to SignatureServiceAPI and Reader Extensions
          the resource resolver for signature options has to be corresponding to the user who has the signing certificate in his granite key store
          the resource resolver for signature options has to be corresponding to the user who has the credential for reader extension in his granite key store
          here we are using the same resource resolver
          */
          adminSession = slingRepository.loginAdministrative(null);
             resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

             //retrieve specifications for each of the services, you may pass null if you don't want to use that service
             //we are not extending the reader in this case, so passing null
             //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
    try {
    outDoc = docAssuranceService.secureDocument(inDoc, null, getCertificationOptions(resourceResolver), null,null);
   } catch (Exception e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
   }

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

        outDoc.copyToFile(outFile);

 }

 /**
  *
  * @param rr resource resolver corresponding to the user with the access to signing credential for the
  * given alias "allcertificatesanypolicytest11ee_new" in this case
  * @return SignatureOptions
  */
 private SignatureOptions getCertificationOptions(ResourceResolver rr){

  //create an instance of SignatureOptions
  SignatureOptions signatureOptions = SignatureOptions.getInstance();

  //set the operation you want to perform - SIGN/CERTIFY
  signatureOptions.setOperationType(DocAssuranceServiceOperationTypes.CERTIFY);

  //signature field to certify, pass null if invisible signature field
  String fieldName = "Signature1" ;

  //alias of the private credential uploaded on the Key Store
        String alias = "allcertificatesanypolicytest11ee_new";

        //Hash Algo to be used to compute digest the PDF document
        HashAlgorithm algo = HashAlgorithm.SHA256;

        //Reason for signing/certifying
        String reason = "Reason";

        //location of the signer
        String location = "Location";

        //contact info of the signer
        String contactInfo = "Contact Info";

        //DocMDP Permissions associated with certification
        MDPPermissions mdpPermissions = MDPPermissions.valueOf("FormChanges");

        //Create a PDFSignatureAppearanceOptions object
        //and show date information
        PDFSignatureAppearenceOptions appOptions = new PDFSignatureAppearenceOptions(
                PDFSignatureAppearanceType.NAME, null, 1.0d, null, true, true,
                true, true, false, true, true, TextDirection.AUTO);
        signatureOptions.setLockCertifyingField(true);
        signatureOptions.setSignatureFieldName(fieldName);
        signatureOptions.setAlgo(algo);
        signatureOptions.setContactInfo(contactInfo);
        signatureOptions.setLocation(location);
        signatureOptions.setSigAppearence(appOptions);
        signatureOptions.setReason(reason);
        signatureOptions.setDssPref(getDSSPreferences(rr));
        signatureOptions.setCredential(new CredentialContext(alias, rr));
        signatureOptions.setMdpPermissions(mdpPermissions);
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

}
```

### Dokumente absichern {#securing-documents}

secureDocument ermöglicht Ihnen, ein PDF-Dokument zu verschlüsseln, signieren/zertifizieren und Reader Extending dafür durchzuführen. Dies ist entweder einzeln oder in einer beliebigen Kombination in einer bestimmten Reihenfolge möglich. Übergeben Sie für den Zugriff auf eine beliebige dieser Funktionen das entsprechende Argument. Wenn der Wert null ist, wird angenommen, dass die bestimmte Verarbeitung nicht erforderlich ist.

**PDF-Dokumente mit Kennwort verschlüsseln**

Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, muss ein Benutzer das Kennwort angeben, damit das Dokument in Adobe Reader oder Acrobat geöffnet werden kann. Bevor außerdem ein anderer AEM Forms Document Services-Vorgang das Dokument verwendet, muss die Sperre eines kennwortverschlüsselten PDF-Dokuments zuerst aufgehoben werden.

**PDF-Dokumente mit Zertifikaten verschlüsseln**

Mit der zertifikatbasierten Verschlüsselung können Sie ein Dokument mithilfe der Technologie öffentlicher Schlüssel für bestimmte Empfänger verschlüsseln.

Verschiedene Empfänger können unterschiedliche Berechtigungen für das Dokument erhalten. Viele Aspekte der Verschlüsselung werden durch die Technologie öffentlicher Schlüssel möglich gemacht.

Ein Algorithmus wird zum Generieren zweier großer Nummern, die als Schlüssel bezeichnet werden, verwendet, die die folgenden Eigenschaften haben:

* Ein Schlüssel wird zum Verschlüsseln eines Satzes von Daten verwendet. Danach kann nur der andere Schlüssel zum Entschlüsseln der Daten verwendet werden.
* Es ist unmöglich, einen Schlüssel vom anderen zu unterscheiden.
* Einer der Schlüssel agiert als der private Schlüssel eines Benutzers. Wichtig ist, dass nur der Benutzer Zugriff auf diesen Schlüssel hat.
* Der andere Schlüssel ist der öffentliche Schlüssel des Benutzers, der mit Dritten gemeinsam genutzt werden kann.

Ein öffentliches Schlüsselzertifikat enthält den öffentlichen Schlüssel eines Benutzers sowie Identifizierungsinformationen. Das X.509-Format dient zum Speichern von Zertifikaten. Zertifikate werden meist von einer Zertifizierungsstelle ausgestellt und digital signiert, bei der es sich um eine anerkannte Instanz handelt, die ein Maß an Vertrauen in die Gültigkeit des Zertifikats ermöglicht. Zertifikate haben ein Ablaufdatum, nach dem sie nicht mehr gültig sind.

Darüber hinaus liefern Zertifikatsperrlisten Informationen zu Zertifikaten, die vor ihrem Ablaufdatum gesperrt wurden. Zertifikatsperrlisten werden regelmäßig von Zertifizierungsstellen veröffentlicht. Der Sperrstatus eines Zertifikats kann auch mittels des Online-Zertifikatstatusprotokolls (Online Certificate Status Protocol, OCSP) über das Netzwerk abgerufen werden.

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument mit einem Zertifikat verschlüsseln können, müssen Sie sicherstellen, dass das Zertifikat AEM Trust Store hinzugefügt wird.

**Verwendungsrechte für PDF-Dokumente aktivieren**

Mit der Java-Client-API des Reader Extensions-Dienstes und dem Webdienst können Sie Verwendungsrechte für PDF-Dokumente aktivieren. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. PDF-Dokumente, auf die Verwendungsrechte angewandt wurden, werden als Dokumente mit aktivierten Verwendungsrechten bezeichnet. Benutzer, die ein Dokument mit aktivierten Verwendungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses spezifische Dokument aktiviert sind.

Bevor Reader Extending für ein PDF-Dokument mit einem Zertifikat durchgeführt werden kann, müssen Sie sicherstellen, dass das Zertifikat zu AEM Key Store hinzugefügt wird.

**PDF-Dokumente digital signieren**

Digitale Signaturen können zu Sicherheitszwecken auf PDF-Dokumente angewendet werden. Digitale Signaturen bieten wie handschriftliche Signaturen ein Mittel, mit dem sich die Unterzeichner identifizieren und zum Dokument Stellung nehmen.

Die zum digitalen Signieren verwendete Technologie stellt sicher, dass sowohl der Unterzeichner als auch die Empfänger genau wissen, was signiert wurde und dass das Dokument nach dem Signieren nicht geändert wurde.

PDF-Dokumente werden mittels der Technologie öffentlicher Schlüssel signiert. Ein Unterzeichner hat zwei Schlüssel: einen öffentlichen Schlüssel und einen privaten Schlüssel. Der private Schlüssel wird in den Anmeldedaten eines Benutzers gespeichert, die zum Zeitpunkt des Signierens verfügbar sein müssen.

Der öffentliche Schlüssel wird im Zertifikat eines Benutzers gespeichert, das zum Überprüfen der Signatur verfügbar sein muss. Informationen zu gesperrten Zertifikaten finden Sie in den Zertifikatsperrlisten (CRLs) und den Antworten des Online-Zertifikatstatusprotokolls (OCSP), die von Zertifizierungsstellen (CAs) verteilt werden. Der Zeitpunkt der Signatur kann von einer vertrauenswürdigen Quelle, die als Zeitstempeldienst bezeichnet wird, erhalten werden.

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument digital signieren können, müssen Sie sicherstellen, dass die Berechtigung in AEM Keystore hinzugefügt wird. Die Anmeldedaten bestehen aus dem zum Signieren verwendeten privaten Schlüssel.

>[!NOTE]
>
>AEM Forms unterstützt auch die Spezifikation *[CAdES](https://en.wikipedia.org/wiki/CAdES_%28computing%29)* für das digitale Signieren von PDF-Dokumenten.

**PDF-Dokumente zertifizieren**

Sie können ein PDF-Dokument absichern, indem Sie es mit einem bestimmten Signaturtyp (einer zertifizierten Signatur) zertifizieren. Eine zertifizierte Signatur entscheidet sich wie folgt von einer digitalen Signatur:

Sie muss die erste, auf das PDF-Dokument angewendete Signatur sein. Das heißt, zum Zeitpunkt, zu dem die zertifizierte Signatur angewendet wird, müssen alle anderen Signaturfelder im Dokument unsigniert sein.

In einem PDF-Dokument ist nur eine zertifizierte Signatur zulässig. Wenn Sie ein PDF-Dokument signieren und zertifizieren möchten, müssen Sie es vor dem signieren zertifizieren.

Nach dem Zertifizieren eines PDF-Dokuments können Sie weitere Signaturfelder digital signieren.

Der Autor oder Ersteller des Dokuments kann festlegen, dass das Dokument auf bestimmte Arten modifiziert werden kann, ohne dass die zertifizierte Signatur ungültig wird.

Beispiel: Das Ausfüllen von Formularen oder Einfügen von Kommentaren im Dokument kann zulässig sein. Wenn der Autor festlegt, dass eine bestimmte Änderung nicht zulässig ist,

Acrobat verhindert, dass Benutzer das Dokument auf diese Weise ändern. Wenn solche Änderungen vorgenommen werden, etwa durch Verwenden einer anderen Anwendung, wird die zertifizierte Signatur ungültig und Acrobat gibt eine Warnung aus, wenn ein Benutzer das Dokument öffnet. (Bei nicht zertifizierten Signaturen werden Änderungen nicht verhindert und Bearbeitungsvorgänge führen nicht dazu, dass die ursprüngliche Signatur ungültig wird.)

Zum Zeitpunkt des Signierens wird das Dokument auf bestimmte Typen von Inhalt überprüft, durch die die Inhalte eines Dokuments mehrdeutig oder irreführend werden könnten.

Beispiel: Eine Anmerkung kann Text auf einer Seite verdecken, der für das Verständnis dessen, was zertifiziert wird, wichtig ist. Eine Erläuterung (gültige Beglaubigung) zu solchen Inhalten kann bereitgestellt werden.

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument digital signieren können, müssen Sie sicherstellen, dass die Berechtigung in AEM Keystore hinzugefügt wird. Die Anmeldedaten bestehen aus dem zum Signieren verwendeten privaten Schlüssel.

**Syntax**:

```java
secureDocument(Document inDoc,
 EncryptionOptions encryptionOptions,
 SignatureOptions signatureOptions,
 ReaderExtensionOptions readerExtensionOptions,
 UnlockOptions unlockOptions)
```

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>PDF-Dokument für die Dokumenteingabe<br /> </td>
  </tr>
  <tr>
   <td><code>encryptionOptions</code> </td>
   <td>Umfasst die zum Verschlüsseln eines PDF-Dokuments erforderlichen Argumente<br /> </td>
  </tr>
  <tr>
   <td><code>signatureOptions</code></td>
   <td>Umfasst die zum Signieren/Zertifizieren eines PDF-Dokuments erforderlichen Optionen</td>
  </tr>
  <tr>
   <td><code>readerExtensionOptions</code></td>
   <td>Umfasst für Reader Extending eines PDF-Dokuments erforderliche Optionen</td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist.<br /> </td>
  </tr>
 </tbody>
</table>

**Beispiel 1**: Dieses Beispiel wird zum Durchführen einer Kennwortverschlüsselung, Zertifizieren eines Signaturfelds und zum Reader Extending des PDF-Dokuments verwendet.

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

import java.io.File;
import java.util.ArrayList;
import java.util.List;

import javax.jcr.Session;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.api.SlingRepository;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.DocAssuranceServiceOperationTypes;
import com.adobe.fd.docassurance.client.api.EncryptionOptions;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.docassurance.client.api.SignatureOptions;
import com.adobe.fd.encryption.client.PasswordEncryptionCompatability;
import com.adobe.fd.encryption.client.PasswordEncryptionOption;
import com.adobe.fd.encryption.client.PasswordEncryptionOptionSpec;
import com.adobe.fd.encryption.client.PasswordEncryptionPermission;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
import com.adobe.fd.signatures.client.types.MDPPermissions;
import com.adobe.fd.signatures.pdf.inputs.CredentialContext;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferences;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferencesImpl;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.PDFSignatureAppearanceType;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.TextDirection;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
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
 *
 * This class provides a sample code to use {@code DocAssuranceService} to carry out
 * password encryption, certifying a signature field and reader extending the pdf document.
 *
 * PreRequisites - Digital certificate for signing the document has to be uploaded on Granite Key Store
 * Digital certificate for reader extending the document has to be uploaded on Granite Key Store
 */

@Component
@Service(value=PassEncryptCertifyExtend.class)
public class PassEncryptCertifyExtend {

 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @param outputFile - path to the pdf document where the output needs to be stored
  * @throws Exception
  */
 public void SecureDocument(String inputFile, String outputFile) throws Exception{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
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

             //retrieve specifications for each of the services, you may pass null if you don't want to use that service
             //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
    outDoc = docAssuranceService.secureDocument(inDoc, getPassEncryptionOptions(), getCertificationOptions(resourceResolver), getReaderExtensionOptions(resourceResolver),null);
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

        outDoc.copyToFile(outFile);

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
  * @return EncryptionOptions for password encrypting the document.
  *
  */
 private EncryptionOptions getPassEncryptionOptions(){

  //Create an instance of EncryptionOptions
  EncryptionOptions encryptionOptions = EncryptionOptions.getInstance();

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

        //Set the encryption type to Password Encryption
  encryptionOptions.setEncryptionType(DocAssuranceServiceOperationTypes.ENCRYPT_WITH_PASSWORD);
        encryptionOptions.setPasswordEncryptionOptionSpec(passSpec);

     return encryptionOptions;
 }

 /**
  *
  * @param resourceResolver corresponding to the user with the access to Reader Extension credential
  * for the given alias -"production" in this case
  * @return
  */
 private ReaderExtensionOptions getReaderExtensionOptions(ResourceResolver resourceResolver){

  //Create an instance of ReaderExtensionOptions
  ReaderExtensionOptions reOptions = ReaderExtensionOptions.getInstance();

  //Create instance for UsageRights to be enabled in the reader
  UsageRights uRights = new UsageRights();
  //enabling comments in the PDF Reader
  uRights.setEnabledComments(true);
  //setting ReaderExtensionsOptionSpec in the reOptions
  reOptions.setReOptions(new ReaderExtensionsOptionSpec(uRights, "Enable commenting in PDF"));
  //alias of the credential to be used for extending the PDF Reader
  reOptions.setCredentialAlias("production");
  //corresponding to the user with the access to Reader Extension credential
  reOptions.setResourceResolver(resourceResolver);

  return reOptions;
 }

 /**
  *
  * @param rr resource resolver corresponding to the user with the access to signing credential for the
  * given alias "allcertificatesanypolicytest11ee_new" in this case
  * @return SignatureOptions
  */
 private SignatureOptions getCertificationOptions(ResourceResolver rr){

  //create an instance of SignatureOptions
  SignatureOptions signatureOptions = SignatureOptions.getInstance();

  //set the operation you want to perform - SIGN/CERTIFY
  signatureOptions.setOperationType(DocAssuranceServiceOperationTypes.CERTIFY);

  //signature field to certify, pass null if invisible signature field
  String fieldName = "Signature1" ;

  //alias of the private credential uploaded on the Key Store
        String alias = "allcertificatesanypolicytest11ee_new";

        //Hash Algo to be used to compute digest the PDF document
        HashAlgorithm algo = HashAlgorithm.SHA384;

        //Reason for signing/certifying
        String reason = "Test Reason";

        //location of the signer
        String location = "Test Location";

        //contact info of the signer
        String contactInfo = "Test Contact";

        //DocMDP Permissions associated with certification
        MDPPermissions mdpPermissions = MDPPermissions.valueOf("FormChanges");

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
        signatureOptions.setCredential(new CredentialContext(alias, rr));
        signatureOptions.setMdpPermissions(mdpPermissions);
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

}
```

**Beispiel 2**: Dieses Beispiel wird zum Durchführen einer PKI-Verschlüsselung, Siegnieren eines Signaturfelds und zum Reader Extending des PDF-Dokuments verwendet.

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
import java.io.File;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.List;

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
import com.adobe.fd.docassurance.client.api.EncryptionOptions;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.docassurance.client.api.SignatureOptions;
import com.adobe.fd.encryption.client.CertificateEncryptionCompatibility;
import com.adobe.fd.encryption.client.CertificateEncryptionIdentity;
import com.adobe.fd.encryption.client.CertificateEncryptionOption;
import com.adobe.fd.encryption.client.CertificateEncryptionOptionSpec;
import com.adobe.fd.encryption.client.CertificateEncryptionPermissions;
import com.adobe.fd.encryption.client.Recipient;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
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
 *
 * This class provides a sample code to use {@code DocAssuranceService} to carry out
 * certificate encryption, signing a signature field and reader extending the pdf document.
 *
 * PreRequisites - Digital certificate for encrypting the document has to be uploaded on Granite Trust Store
       Digital certificate for signing the document has to be uploaded on Granite Key Store
 * Digital certificate for reader extending the document has to be uploaded on Granite Key Store
 */

@Component
@Service(value=PassEncryptSignExtend.class)
public class PassEncryptSignExtend {

 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @param outputFile - path to the pdf document where the output needs to be stored
  * @throws Exception
  */
 public void CertEncryptSignReaderExtend(String inputFile, String outputFile) throws Exception{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
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

             //retrieve specifications for each of the services, you may pass null if you don't want to use that service
             //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
    outDoc = docAssuranceService.secureDocument(inDoc, getCertEncryptionOptions(), getSignatureOptions(resourceResolver), getReaderExtensionOptions(resourceResolver),null);
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

        outDoc.copyToFile(outFile);

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
  * @return EncryptionOptions for password encrypting the document.
  *
  */
 private EncryptionOptions getCertEncryptionOptions(){

  //Create an instance of EncryptionOptions
  EncryptionOptions encryptionOptions = EncryptionOptions.getInstance();

        //Set the encryption type to Certificate Encryption
  encryptionOptions.setEncryptionType(DocAssuranceServiceOperationTypes.ENCRYPT_WITH_CERTIFCATE);

  //Set the List that stores PKI information
  List<CertificateEncryptionIdentity> pkiIdentities = new ArrayList<CertificateEncryptionIdentity>();

  //Set the Permission List
  List<CertificateEncryptionPermissions> permList = new ArrayList<CertificateEncryptionPermissions>();
  permList.add(CertificateEncryptionPermissions.PKI_ALL_PERM) ;

  //Create a Recipient object to store certificate information
  Recipient recipient = new Recipient();

  //Specify the alias of the public certificate present in the trust store that is used to encrypt the document
  recipient.setX509Cert("alias");
  /*
   * An alternative to add a certificate is by providing the alias
   * of the certificate stored in AEM trust store.
   * recipient.setAlias(alias);
   */

  //Create an EncryptionIdentity object
  CertificateEncryptionIdentity encryptionId = new CertificateEncryptionIdentity();
  encryptionId.setPerms(permList);
  encryptionId.setRecipient(recipient);

  //Add the EncryptionIdentity to the list
  pkiIdentities.add(encryptionId);

  //Set encryption run-time options
  CertificateEncryptionOptionSpec certOptionsSpec = new CertificateEncryptionOptionSpec();
  certOptionsSpec.setOption(CertificateEncryptionOption.ALL);
  certOptionsSpec.setCompat(CertificateEncryptionCompatibility.ACRO_9);

  //Set the certificate encryption option
  encryptionOptions.setCertOptionSpec(certOptionsSpec)

  //Set the PKI Identities in encryption Options
        encryptionOptions.setPkiIdentities(pkiIdentities);

     return encryptionOptions;
 }

 /**
  *
  * @param resourceResolver corresponding to the user with the access to Reader Extension credential
  * for the given alias -"production" in this case
  * @return
  */
 private ReaderExtensionOptions getReaderExtensionOptions(ResourceResolver resourceResolver){

  //Create an instance of ReaderExtensionOptions
  ReaderExtensionOptions reOptions = ReaderExtensionOptions.getInstance();

  //Create instance for UsageRights to be enabled in the reader
  UsageRights uRights = new UsageRights();
  //enabling comments in the PDF Reader
  uRights.setEnabledComments(true);
  //setting ReaderExtensionsOptionSpec in the reOptions
  reOptions.setReOptions(new ReaderExtensionsOptionSpec(uRights, "Enable commenting in PDF"));
  //alias of the credential to be used for extending the PDF Reader
  reOptions.setCredentialAlias("production");
  //corresponding to the user with the access to Reader Extension credential
  reOptions.setResourceResolver(resourceResolver);

  return reOptions;
 }

 /**
  *
  * @param rr resource resolver corresponding to the user with the access to signing credential for the
  * given alias "allcertificatesanypolicytest11ee_new" in this case
  * @return SignatureOptions
  */
 private SignatureOptions getSignatureOptions(ResourceResolver rr){

  //create an instance of SignatureOptions
  SignatureOptions signatureOptions = SignatureOptions.getInstance();

  //set the operation you want to perform - SIGN/CERTIFY
  signatureOptions.setOperationType(DocAssuranceServiceOperationTypes.SIGN);

  //field to sign
  String fieldName = "Signature1" ;

  //alias of the private credential uploaded on the Key Store
        String alias = "allcertificatesanypolicytest11ee_new";

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
        signatureOptions.setCredential(new CredentialContext(alias, rr));
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

}
```

Wenn beim Erweitern eines PDF-Dokuments die folgende Fehlermeldung angezeigt wird:

```javascript
org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.ThreadDeath: null at com.adobe.internal.pdftoolkit.services.javascript.GibsonContextFactory.observeInstructionCount(GibsonContextFactory.java:138)
```

Es bedeutet, dass der Reader Extension-Dienst die im Dokument verwendeten JavaScripts nicht innerhalb des definierten Zeitüberschreitungsintervalls ausführen kann.

Verwalten Sie das für die JavaScripts im PDF-Dokument definierte Zeitüberschreitungsintervall mithilfe:

```javascript
ReaderExtensionsOptionSpec optionSpec = new ReaderExtensionsOptionSpec(usageRights, message);
optionSpec.setJsScriptExecutionTimeoutInterval(100);
```

wobei 100 auf das Zeitüberschreitungsintervall verweist, das für die Ausführung von JavaScripts definiert wurde (in Sekunden). Legen Sie einen entsprechenden Wert für das Zeitüberschreitungsintervall fest.

### Verwendungsrechte für Berechtigung abrufen {#getting-credential-usage-rights}

Zum Abrufen von Informationen zu Verwendungsrechten der im entsprechenden `credentialAlias` angegebenen Anmeldedaten rufen Sie diese API aus der `SecureDocument`-API auf.

**Syntax**:  `getCredentialUsageRights(String credentialAlias, ResourceResolver resourceResolver)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>credentialAlias</code> </td>
   <td>Das <code>credentialAlias</code> zur Angabe der Anmeldedaten.<br /> </td>
  </tr>
  <tr>
   <td><code>credentialPassword</code> </td>
   <td>Das Kennwort der Anmeldedaten, wenn die Anmeldedaten verschlüsselt sind. Es muss „null“ verwendet werden, wenn die Anmeldedaten nicht verschlüsselt sind.<br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Beispiel werden Informationen zu den Verwendungsrechten für die angegebenen Anmeldedaten abgerufen.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2014 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and may be covered by U.S. and Foreign Patents,
 * patents in process, and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.adobe.fd.readerextensions.samples;

import java.io.File;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.readerextensions.client.GetUsageRightsResult;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 *
 */
@Component(metatype = true, immediate = true, label = "ReaderExtensionsSampleService")
@Service(value = ReaderExtensionsSampleService.class)
public class ReaderExtensionsSampleService {

 @Reference(referenceInterface=DocAssuranceService.class)
 private DocAssuranceService docAssuranceService;

 @Reference(referenceInterface=ResourceResolverFactory.class)
 private ResourceResolverFactory resourceResolverFactory;
public void getCredentialUsageRights() {
  try {

   GetUsageRightsResult usageRightsResult = docAssuranceService.getCredentialUsageRights("production",
     resourceResolverFactory.getAdministrativeResourceResolver(null));

   System.out.println("Credential usage Rights are as follows");
   System.out.println(usageRightsResult.toString());

  } catch (Exception e) {
   e.printStackTrace();
  }
 }
}
```

### Verwendungsrechte für Dokument abrufen  {#getting-document-usage-rights}

Zum Abrufen von Informationen zu Verwendungsrechten für ein bestimmtes Dokument rufen Sie diese API aus der `docAssuranceService`- -API.

**Syntax**:  `getDocumentUsageRights(Document inDocument, UnlockOptions unlockOptions)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDocument</code> </td>
   <td>Das Dokument, von dem die Informationen zu Verwendungsrechten abgerufen werden<br /> </td>
  </tr>
 </tbody>
</table>

Der folgende Beispielcode gibt die Informationen zu Verwendungsrechten für ein Dokument zurück.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2014 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and may be covered by U.S. and Foreign Patents,
 * patents in process, and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.adobe.fd.readerextensions.samples;

import java.io.File;
import java.util.HashMap;
import java.util.Map;

import javax.jcr.SimpleCredentials;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.LoginException;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.jcr.resource.JcrResourceConstants;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.readerextensions.client.GetUsageRightsResult;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

@Component(metatype = true, immediate = true, label = "ReaderExtensionsSampleService")
@Service(value = ReaderExtensionsSampleService.class)
public class ReaderExtensionsSampleService {

 @Reference(referenceInterface=DocAssuranceService.class)
 private DocAssuranceService docAssuranceService;

 @Reference(referenceInterface=ResourceResolverFactory.class)
private ResourceResolverFactory resourceResolverFactory;

public void getDocumentUsageRights() {
  Document inputDocument = null;
  try {
   //Name of the input file on which usage rights is to be applied.
   String inputFileName = "C:/RETest/input/GetUsageRightsInfo/02_fromAcrobat7.0.8_Acro700_UB8_BS_signed_commenting.pdf";

   //Document to be input to Doc Assurance Service
   inputDocument = new Document(new File(inputFileName));

   //Unlock options to unlock the document if some kind of security is set on it.
   //Currently set to null because input document has no security.
   UnlockOptions unlockOptions = null;

   GetUsageRightsResult usageRightsResult = docAssuranceService.getDocumentUsageRights(inputDocument, unlockOptions);

   System.out.println("Document usage Rights are as follows");
   System.out.println(usageRightsResult.toString());

  } catch (Exception e) {
   e.printStackTrace();
  } finally {
//   if (inputDocument != null) {
//    inputDocument.dispose(); //dispose off the document.
//   }
  }
}

/**
  * Resource resolver of the user in whose keystore Reader Extensions Certificate is installed.
  * @param resourceResolverFactory
  * @return
  * @throws LoginException
  */
 public ResourceResolver getResourceResolver() throws LoginException{
  Map<String,Object> authInfo = new HashMap<String,Object>();
  //Username and password of the user in whose keystore Reader Extensions Certificate is installed
  SimpleCredentials credentials = new SimpleCredentials("username"/*UserName*/, "password"/*Password*/.toCharArray());
  authInfo.put(JcrResourceConstants.AUTHENTICATION_INFO_CREDENTIALS,credentials);
  return resourceResolverFactory.getResourceResolver(authInfo);
}

}
```

### Verwendungsrechte entfernen  {#removing-usage-rights}

Sie können die Verwendungsrechte für ein Dokument entfernen, indem Sie die `removeUsageRights`- -API aus der `docAssuranceService`-API heraus aufrufen.

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDocument</code> </td>
   <td>Das Dokument, dessen Verwendungsrechte entfernt werden sollen.<br /> </td>
  </tr>
  <tr>
   <td><code>unlockOptions</code> </td>
   <td>Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist.<br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Beispiel werden die Verwendungsrechte eines Dokuments entfernt.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2014 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and may be covered by U.S. and Foreign Patents,
 * patents in process, and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.adobe.fd.readerextensions.samples;

import java.io.File;
import java.util.HashMap;
import java.util.Map;

import javax.jcr.SimpleCredentials;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.LoginException;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.jcr.resource.JcrResourceConstants;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.readerextensions.client.GetUsageRightsResult;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

@Component(metatype = true, immediate = true, label = "ReaderExtensionsSampleService")
@Service(value = ReaderExtensionsSampleService.class)
public class ReaderExtensionsSampleService {

 @Reference(referenceInterface=DocAssuranceService.class)
 private DocAssuranceService docAssuranceService;

 @Reference(referenceInterface=ResourceResolverFactory.class)
private ResourceResolverFactory resourceResolverFactory;

public void removeDocumentUsageRights() {
  Document inputDocument = null;
  Document outDocument = null;
  try {
   //Name of the input file on which usage rights is to be applied.
   String inputFileName = "C:/RETest/input/RemoveUsageRights/01_Ubiquitized_50-267_PDF1.5_UB2_Rights.pdf";

   //Name of the output file where result will be saved.
   String outputFileName = "C:/RETest/output/samples/removeUsageRightsOutput.pdf";

   //Document to be input to Doc Assurance Service
   inputDocument = new Document(new File(inputFileName));

   //Unlock options to unlock the document if some kind of security is set on it.
   //Currently set to null because input document has no security.
   UnlockOptions unlockOptions = null;

   //Specify null encryption options and signatures options.
   //If requirement is also to encrypt and sign the document then, corresponding options can also be specified.
   outDocument = docAssuranceService.removeUsageRights(inputDocument, unlockOptions);

   File outputdir = new File("C:/RETest/output/samples");
   outputdir.mkdirs();

   outDocument.copyToFile(new File(outputFileName));
  } catch (Exception e) {
   e.printStackTrace();
  }
}

/**
  * Resource resolver of the user in whose keystore Reader Extensions Certificate is installed.
  * @param resourceResolverFactory
  * @return
  * @throws LoginException
  */
 public ResourceResolver getResourceResolver() throws LoginException{
  Map<String,Object> authInfo = new HashMap<String,Object>();
  //Username and password of the user in whose keystore Reader Extensions Certificate is installed
  SimpleCredentials credentials = new SimpleCredentials("username"/*UserName*/, "password"/*Password*/.toCharArray());
  authInfo.put(JcrResourceConstants.AUTHENTICATION_INFO_CREDENTIALS,credentials);
  return resourceResolverFactory.getResourceResolver(authInfo);
}

}
```

#### Digitale Signaturen überprüfen  {#verifying-digital-signatures}

Digitale Signaturen können überprüft werden, um sicherzustellen, dass ein signiertes PDF-Dokument nicht geändert wurde und die digitale Signatur gültig ist. Beim Überprüfen einer digitalen Signatur können Sie den Signaturstatus und die Signatureigenschaften, wie etwa die Identität des Unterzeichners, prüfen. Bevor Sie einer digitalen Signatur vertrauen, sollten Sie sie überprüfen. Verwenden Sie beim Überprüfen einer digitalen Signatur ein PDF-Dokument, das eine digitale Signatur enthält.

**Syntax**:  `verify( inDoc, signatureFieldName, revocationCheckStyle, verificationTime, dssPrefs, ResourceResolver resourceResolver)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Dokumentobjekt, das PDF enthält<br /> </td>
  </tr>
  <tr>
   <td><code class="code">signatureField
      Name</code> </td>
   <td>Der Name des zu überprüfenden Signaturfelds. Es kann entweder der vollqualifizierte Name oder ein Teil des Namens angegeben werden.<br />  </td>
  </tr>
  <tr>
   <td><code>revocationCheckStyle</code></td>
   <td>Die Option, die die Prüfung von Sperren der während der Überprüfung gefundenen Zertifikate steuert</td>
  </tr>
  <tr>
   <td><code>verificationTime</code></td>
   <td>Der Zeitpunkt, zu dem die Signatur überprüft werden muss</td>
  </tr>
  <tr>
   <td><code>dssPrefs</code></td>
   <td>Präferenzen zum Steuern verschiedener Überprüfungskonfigurationen. Legen Sie für ein verschlüsseltes Dokument die Entsperroptionen mithilfe von  () fest. <code>setUnlockOptions()</code></td>
  </tr>
  <tr>
   <td><code>resourceResolver</code></td>
   <td>Ressourcen-Konfliktlöser zum Granite Trust Store</td>
  </tr>
 </tbody>
</table>

In diesem Beispielcode wird `DocAssuranceService` zum Überprüfen eines Signaturfelds in einem verschlüsselten PDF-Dokument verwendet.

```java
/*************************************************************************
 *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;

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
import com.adobe.fd.signatures.client.types.IdentityInformation;
import com.adobe.fd.signatures.client.types.IdentityStatus;
import com.adobe.fd.signatures.client.types.PDFSignatureType;
import com.adobe.fd.signatures.client.types.PDFSignatureVerificationInfo;
import com.adobe.fd.signatures.client.types.SignatureProperties;
import com.adobe.fd.signatures.client.types.SignatureStatus;
import com.adobe.fd.signatures.client.types.SignatureType;
import com.adobe.fd.signatures.client.types.VerificationTime;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferences;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.common.RevocationCheckStyle;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.OCSPPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.TSPPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.TSPPreferencesImpl;

/**
 *
 * This class provides a sample code to use {@code DocAssuranceService} to carry out
 * verification of a signature field in an already Encrypted PDF Document
 *
 * Digital signatures can be verified to ensure that a signed PDF document was not modified and that the digital signature is valid.
 * When verifying a digital signature, you can check the signature's status and the signature's properties, such as the signer's identity.
 * Before trusting a digital signature, it is recommended that you verify it. When verifying a digital signature, reference a PDF document
 * that contains a digital signature.
 *
 * For unprotected document, you are not required to set UnlockOptions in ValidationPreferences
 * PreRequisites - The certificate chain upto the Root Certificate should be uploaded on CQ trust Store
 */

@Component
@Service(value=VerifyFieldEncryptedPDF.class)
public class VerifyFieldEncryptedPDF {

 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to an encrypted pdf document stored at JCR node
  * @throws IOException
  * @throws RepositoryException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  */
 public void verifyFieldEncryptedPDF(String inputFile,String fieldName) throws IOException, RepositoryException, InvalidArgumentException, DocAssuranceException{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try {

         //the resource resolver has to be corresponding to the user who has access to CQ Trust Store
          adminSession = slingRepository.loginAdministrative(null);
             resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

           //Specify the name of the signature field

             RevocationCheckStyle revocationCheckStyle = RevocationCheckStyle.AlwaysCheck;
             VerificationTime verificationTime = VerificationTime.CURRENT_TIME;
             ValidationPreferences dssPrefs = getValidationPreferences();

             //Verify the digital signature
             PDFSignatureVerificationInfo  signInfo = docAssuranceService.verify(
                 inDoc,
                 fieldName,
                 revocationCheckStyle,
                 verificationTime,
                 dssPrefs,
                 resourceResolver);

             //Get the Signature Status
             SignatureStatus sigStatus = signInfo.getStatus();
             String myStatus="";

             //Determine the status of the signature
             if (sigStatus == SignatureStatus.DynamicFormSignatureUnknown)
                 myStatus = "The signatures located in the dynamic PDF form are unknown";
             else if (sigStatus == SignatureStatus.DocumentSignatureUnknown)
                 myStatus = "The signatures located in the PDF document are unknown";
             else if (sigStatus == SignatureStatus.CertifiedDynamicFormSignatureTamper)
                 myStatus = "The signatures located in a certified PDF form are valid";
             else if (sigStatus == SignatureStatus.SignedDynamicFormSignatureTamper)
                 myStatus = "The signatures located in a signed dynamic PDF form are valid";
             else if (sigStatus == SignatureStatus.CertifiedDocumentSignatureTamper)
                 myStatus = "The signatures located in a certified PDF document are valid";
             else if (sigStatus == SignatureStatus.SignedDocumentSignatureTamper)
                 myStatus = "The signatures located in a signed PDF document are valid";
             else if (sigStatus == SignatureStatus.SignatureFormatError)
                 myStatus = "The format of a signature in a signed document is invalid";
             else if (sigStatus == SignatureStatus.DynamicFormSigNoChanges)
                 myStatus = "No changes were made to the signed dynamic PDF form";
             else if (sigStatus == SignatureStatus.DocumentSigNoChanges)
                 myStatus = "No changes were made to the signed PDF document";
             else if (sigStatus == SignatureStatus.DynamicFormCertificationSigNoChanges)
                 myStatus = "No changes were made to the certified dynamic PDF form";
             else if (sigStatus == SignatureStatus.DocumentCertificationSigNoChanges)
                 myStatus = "No changes were made to the certified PDF document";
             else if (sigStatus == SignatureStatus.DocSigWithChanges)
                 myStatus = "There were changes to a signed PDF document";
            else if (sigStatus == SignatureStatus.CertificationSigWithChanges)
                 myStatus = "There were changes made to the PDF document.";

             //Get the signature type
             SignatureType sigType = signInfo.getSignatureType();
             String myType = "";

             if (sigType.getType() == PDFSignatureType.AUTHORSIG)
                    myType="Certification";
             else if(sigType.getType() == PDFSignatureType.RECIPIENTSIG)
                    myType="Recipient";

             //Get the identity of the signer
             IdentityInformation signerId = signInfo.getSigner();
             String signerMsg = "";

            if (signerId.getStatus() == IdentityStatus.UNKNOWN)
                signerMsg = "Identity Unknown";
            else if (signerId.getStatus() == IdentityStatus.TRUSTED)
                signerMsg = "Identity Trusted";
            else if (signerId.getStatus() == IdentityStatus.NOTTRUSTED)
                signerMsg = "Identity Not Trusted";

            //Get the Signature properties returned by the Signature service
            SignatureProperties sigProps = signInfo.getSignatureProps();
            String signerName =  sigProps.getSignerName();

           System.out.println("The status of the signature is: "+myStatus +". The signer identity is "+signerMsg +". The signature type is "+myType +". The name of the signer is "+signerName+".");
           }
           catch (Exception ee)
           {
               ee.printStackTrace();
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

 }

 /**
   * sets ValidationPreferences
   */
  private static ValidationPreferences getValidationPreferences(){

        ValidationPreferencesImpl prefs = new ValidationPreferencesImpl();
        prefs.setPKIPreferences(getPKIPreferences());

        //set the unlock options for processing an encrypted pdf document, do not set if the input doc is unprotected
        prefs.setUnlockOptions(getUnlockOptions());
        return prefs;

    }

  /**
   * sets PKIPreferences
   */
    private static PKIPreferences getPKIPreferences(){
        PKIPreferences pkiPref = new PKIPreferencesImpl();
        pkiPref.setCRLPreferences(getCRLPreferences());
        pkiPref.setPathPreferences(getPathValidationPreferences());
        pkiPref.setOCSPPreferences(getOCSPPref());
        pkiPref.setTSPPreferences(getTspPref());
        return pkiPref;
    }

    private static TSPPreferences getTspPref(){
     TSPPreferencesImpl tsp = new TSPPreferencesImpl();
     tsp.setRevocationCheck(RevocationCheckStyle.BestEffort);
     return tsp;
    }
    private static OCSPPreferencesImpl getOCSPPref(){
     OCSPPreferencesImpl ocsp = new OCSPPreferencesImpl();
     ocsp.setRevocationCheck(RevocationCheckStyle.BestEffort);
     return ocsp;
    }
    /**
     * sets CRL Preferences
     */
    private static CRLPreferences getCRLPreferences(){

        CRLPreferencesImpl crlPrefs = new CRLPreferencesImpl();
        crlPrefs.setRevocationCheck(RevocationCheckStyle.BestEffort);
        crlPrefs.setGoOnline(true);
        return crlPrefs;
    }

    /**
     *
     * sets PathValidationPreferences
     */
    private static PathValidationPreferences getPathValidationPreferences(){
        PathValidationPreferencesImpl pathPref = new PathValidationPreferencesImpl();
        pathPref.setDoValidation(true);
        return pathPref;

    }

    /**
     * sets Unlock Options for encrypted PDF
     */
    private static UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }

}
```

### Mehrere digitale Signaturen überprüfen {#verifying-multiple-digital-signatures}

Mit AEM können Sie digitale Signaturen in PDF-Dokumenten überprüfen. Ein PDF-Dokument kann mehrere digitale Signaturen enthalten, wenn es einem Geschäftsprozess unterzogen wird, für den mehrere Unterschriften erforderlich sind. Beispiel: Eine Finanztransaktion erfordert Signaturen sowohl vom Kreditsachbearbeiter, als auch vom Manager. Sie können die Signature-Dienst-API verwenden, um alle Signaturen im PDF-Dokument zu überprüfen. Beim Überprüfen mehrerer digitaler Signaturen können Sie den Status und die Eigenschaften jeder Signatur prüfen. Bevor Sie einer Signatur vertrauen, empfiehlt Adobe, dass Sie sie überprüfen.

**Syntax**:  `verifyDocument(Document doc, RevocationCheckStyle revocationCheckStyle, VerificationTime verificationTime, ValidationPreferences prefStore, ResourceResolver resourceResolver)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Dokumentobjekt, das PDF enthält<br /> </td>
  </tr>
  <tr>
   <td><code>revocationCheckStyle</code></td>
   <td>Die Option, die die Prüfung von Sperren der während der Überprüfung gefundenen Zertifikate steuert</td>
  </tr>
  <tr>
   <td><code>verificationTime</code></td>
   <td>Der Zeitpunkt, zu dem die Signatur überprüft werden muss</td>
  </tr>
  <tr>
   <td><code>dssPrefs</code></td>
   <td>Präferenzen zum Steuern verschiedener Überprüfungskonfigurationen. Legen Sie für ein verschlüsseltes Dokument die Entsperroptionen mithilfe von  () fest. <code>setUnlockOptions()</code></td>
  </tr>
  <tr>
   <td><code>resourceResolver</code></td>
   <td>Ressourcen-Konfliktlöser zum Granite Trust Store</td>
  </tr>
 </tbody>
</table>

In diesem Beispielcode wird „DocAssuranceService“ zum Überprüfen der Signaturfelder in einem bereits verschlüsselten PDF-Dokument verwendet.

```java
/*************************************************************************
 *
  *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;
import java.util.Iterator;
import java.util.List;

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
import com.adobe.fd.signatures.client.types.PDFDocumentVerificationInfo;
import com.adobe.fd.signatures.client.types.PDFSignatureType;
import com.adobe.fd.signatures.client.types.PDFSignatureVerificationInfo;
import com.adobe.fd.signatures.client.types.SignatureProperties;
import com.adobe.fd.signatures.client.types.SignatureStatus;
import com.adobe.fd.signatures.client.types.SignatureType;
import com.adobe.fd.signatures.client.types.VerificationTime;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferences;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.common.RevocationCheckStyle;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferencesImpl;

/**
 *
 * This class provides a sample code to use {@code DocAssuranceService} to carry out
 * verification of all the signature fields in an already Encrypted PDF Document
 *
 * Assume that a PDF document contains multiple digital signatures as a result of a business process that requires signatures from multiple
 * signers. For example, consider a financial transaction that requires both a loan officer's and a manager's signature. You can use the
 * Signature service Java API or web service API to verify all signatures within the PDF document. When verifying multiple digital signatures,
 * you can check the status and properties of each signature. Before you trust a digital signature, it is recommended that you verify it. It
 * is recommended that you are familiar with verifying a single digital signature.
 *
 * For unprotected document, you are not required to set UnlockOptions in ValidationPreferences
 * PreRequisites - The certificate chain upto the Root Certificate should be uploaded on CQ trust Store
 */

@Component
@Service(value=VerifyEncryptedPDFDoc.class)
public class VerifyEncryptedPDFDoc {

 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to an encrypted pdf document stored at JCR node
  * @throws IOException
  * @throws RepositoryException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  */
 public void verifyEncryptedPDFDoc(String inputFile) throws IOException, RepositoryException, InvalidArgumentException, DocAssuranceException{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try {

          //the resource resolver has to be corresponding to the user who has access to CQ Trust Store
          adminSession = slingRepository.loginAdministrative(null);
             resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

             RevocationCheckStyle revocationCheckStyle = RevocationCheckStyle.CheckIfAvailable;
             VerificationTime verificationTime = VerificationTime.CURRENT_TIME;
             ValidationPreferences dssPrefs = getValidationPreferences();

             //Verify the digital signature
             PDFDocumentVerificationInfo  docInfo = docAssuranceService.verifyDocument(
                 inDoc,
                 revocationCheckStyle,
                 verificationTime,
                 dssPrefs,
                 resourceResolver);

             //Get a list of all signatures that are located in the PDF document
             List allSignatures = docInfo.getVerificationInfos();

           //Create an Iterator object and iterate through
           //the List object
           Iterator<PDFSignatureVerificationInfo> iter = allSignatures.iterator();

           while (iter.hasNext()) {
                  PDFSignatureVerificationInfo signInfo = (PDFSignatureVerificationInfo)iter.next();

                  //Get the Signature Status
                     SignatureStatus sigStatus = signInfo.getStatus();
                     String myStatus="";

                   //Determine the status of the signature
                     if (sigStatus == SignatureStatus.DynamicFormSignatureUnknown)
                         myStatus = "The signatures located in the dynamic PDF form are unknown";
                     else if (sigStatus == SignatureStatus.DocumentSignatureUnknown)
                         myStatus = "The signatures located in the PDF document are unknown";
                     else if (sigStatus == SignatureStatus.CertifiedDynamicFormSignatureTamper)
                         myStatus = "The signatures located in a certified PDF form are valid";
                     else if (sigStatus == SignatureStatus.SignedDynamicFormSignatureTamper)
                         myStatus = "The signatures located in a signed dynamic PDF form are valid";
                     else if (sigStatus == SignatureStatus.CertifiedDocumentSignatureTamper)
                         myStatus = "The signatures located in a certified PDF document are valid";
                     else if (sigStatus == SignatureStatus.SignedDocumentSignatureTamper)
                         myStatus = "The signatures located in a signed PDF document are valid";
                     else if (sigStatus == SignatureStatus.SignatureFormatError)
                         myStatus = "The format of a signature in a signed document is invalid";
                     else if (sigStatus == SignatureStatus.DynamicFormSigNoChanges)
                         myStatus = "No changes were made to the signed dynamic PDF form";
                     else if (sigStatus == SignatureStatus.DocumentSigNoChanges)
                         myStatus = "No changes were made to the signed PDF document";
                     else if (sigStatus == SignatureStatus.DynamicFormCertificationSigNoChanges)
                         myStatus = "No changes were made to the certified dynamic PDF form";
                     else if (sigStatus == SignatureStatus.DocumentCertificationSigNoChanges)
                         myStatus = "No changes were made to the certified PDF document";
                     else if (sigStatus == SignatureStatus.DocSigWithChanges)
                         myStatus = "There were changes to a signed PDF document";
                    else if (sigStatus == SignatureStatus.CertificationSigWithChanges)
                         myStatus = "There were changes made to the PDF document.";

                     //Get the signature type
                    SignatureType sigType = signInfo.getSignatureType();
                    String myType = "";

                    if (sigType.getType() == PDFSignatureType.AUTHORSIG)
                        myType="Certification";
                    else if(sigType.getType() == PDFSignatureType.RECIPIENTSIG)
                        myType="Recipient";

                    //Get the Signature properties returned by the Signature service
                    SignatureProperties sigProps = signInfo.getSignatureProps();
                    String signerName =  sigProps.getSignerName();

                   System.out.println("The status of the signature is: "+myStatus +". The signature type is "+myType +". The name of the signer is "+signerName+".");
               }
           }
           catch (Exception ee)
           {
               ee.printStackTrace();
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

 }

 /**
   * sets ValidationPreferences
   */
  private static ValidationPreferences getValidationPreferences(){

        ValidationPreferencesImpl prefs = new ValidationPreferencesImpl();
        prefs.setPKIPreferences(getPKIPreferences());

        //set the unlock options for processing an encrypted pdf document, do not set if the document is unprotected
        prefs.setUnlockOptions(getUnlockOptions());
        return prefs;

    }

  /**
   * sets PKIPreferences
   */
    private static PKIPreferences getPKIPreferences(){
        PKIPreferences pkiPref = new PKIPreferencesImpl();
        pkiPref.setCRLPreferences(getCRLPreferences());
        pkiPref.setPathPreferences(getPathValidationPreferences());
        return pkiPref;
    }

    /**
     * sets CRL Preferences
     */
    private static CRLPreferences getCRLPreferences(){

        CRLPreferencesImpl crlPrefs = new CRLPreferencesImpl();
        crlPrefs.setRevocationCheck(RevocationCheckStyle.CheckIfAvailable);
        crlPrefs.setGoOnline(true);
        return crlPrefs;
    }

    /**
     *
     * sets PathValidationPreferences
     */
    private static PathValidationPreferences getPathValidationPreferences(){
        PathValidationPreferencesImpl pathPref = new PathValidationPreferencesImpl();
        pathPref.setDoValidation(false);
        return pathPref;

    }

    /**
     * sets Unlock Options for encrypted PDF
     */
    private static UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }

}
```

### Digitale Signaturen entfernen  {#removing-digital-signatures}

Sie können eine neue digitale Signatur erst auf ein Signaturfeld anwenden, nachdem Sie die vorherige digitale Signatur entfernt haben. Eine digitale Signatur kann nicht überschrieben werden. Wenn Sie versuchen, eine digitale Signatur auf ein Signaturfeld anzuwenden, das bereits eine Signatur enthält, tritt eine Ausnahme auf.

**Syntax**:  `clearSignatureField(Document inDoc, String signatureFieldName, UnlockOptions unlockOptions)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Dokumentobjekt, das PDF enthält<br /> </td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code></td>
   <td>Der Name des Signaturfelds.<br />  </td>
  </tr>
  <tr>
   <td><code>unlockOptions</code> </td>
   <td>Umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist<br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird eine digitale Signatur aus einem Signaturfeld entfernt.

```java
/*************************************************************************
 *
  *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file
*from a source other than Adobe, then your use, modification, or distribution of it requires
*the prior written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;

import javax.jcr.RepositoryException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesOtherException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * Digital signatures must be removed from a signature field before a newer digital signature can be applied.
 * A digital signature cannot be overwritten.
 * If you attempt to apply a digital signature to a signature field that contains a signature, an exception occurs
 *
 *The following Java code example removes a digital signature from a signature field named SignatureField1.
 *The name of the PDF file that contain the signature field is LoanSigned.pdf
 */

@Component
@Service(value=ClearSignatureField.class)
public class ClearSignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;
 /**
  *
  * @param inputFile - path to an encrypted pdf document stored at disk
  * @param outFile - path where the output file has to be saved
  * @throws Exception
  */
 public void clearSignatureField(String inputFile, String outFile) throws Exception{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

        //Specify the name of the signature field
        String fieldName = "SignatureField1";

        //Clear the signature field
        //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        Document outPDF = docAssuranceService.clearSignatureField(inDoc,fieldName,null);

        //save the outPDF
        outPDF.copyToFile(new File(outFile));
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
}
```

### Zertifizierungssignaturfeld abrufen  {#getting-certifying-signature-field}

Sie können die Namen aller Signaturfelder abrufen, die sich in einem zu signierenden und zertifizierenden PDF-Dokument befinden. Wenn Sie nicht sicher sind, wie die Signaturfeldnamen in einem PDF-Dokument lauten oder die Namen prüfen möchten, können Sie diese programmgesteuert abrufen. Der Signature-Dienst gibt den vollständig qualifizierten Namen des Signaturfelds zurück, z. B. `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

**Syntax**:  `getCertifyingSignatureField(Document inDoc, UnlockOptions unlockOptions)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Dokumentobjekt, das PDF enthält.<br /> </td>
  </tr>
  <tr>
   <td><code>UnlockOptions</code></td>
   <td>„UnlockOptions“ umfasst die zum Entsperren einer verschlüsselten Datei erforderlichen Parameter. Dies ist nur dann erforderlich, wenn die Datei verschlüsselt ist.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird das Signaturfeld abgerufen, das zum Zertifizieren des Dokuments verwendet wurde.

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

import java.io.File;
import java.util.Iterator;
import java.util.List;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PDFSignatureField;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * You can retrieve the names of all signature fields that are located in a PDF document that you want to sign or certify.
 * If you are unsure of the signature field names that are located in a PDF document or you want to verify the names, you can
 * programmatically retrieve them. The Signature service returns the fully qualified name of the signature field, such as
 * form1[0].grantApplication[0].page1[0].SignatureField1[0].
 *
 * The following Java code example retrieves the ignature field that was used to certify the document.
 */

@Component
@Service(value=GetCertifyingSignatureField.class)
public class GetCertifyingSignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  *
  */
 public void getCertifyingSignatureField(String inputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Retrieve signature data for a given signature field.
  //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        PDFSignatureField pdfSignature = docAssuranceService.getCertifyingSignatureField(inDoc,null);

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
}
```

### PDF-Verschlüsselungstyp abrufen  {#getting-pdf-encryption-type}

Sie können die Namen aller Signaturfelder abrufen, die sich in einem zu signierenden und zertifizierenden PDF-Dokument befinden. Wenn Sie nicht sicher sind, wie die Signaturfeldnamen in einem PDF-Dokument lauten oder die Namen prüfen möchten, können Sie diese programmgesteuert abrufen. Der Signature-Dienst gibt den vollständig qualifizierten Namen des Signaturfelds zurück, z. B. `asform1[0].grantApplication[0].page1[0].SignatureField1[0]`.

**Syntax**:  `void getPDFEncryption(Document inDoc)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Ein Dokument wird als Eingabe bereitgestellt. Es kann verschlüsselt sein, muss es aber nicht sein.<br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden die Signaturinformationen für das angegebene Signaturfeld in einem PDF-Dokument abgerufen.

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

import java.io.File;
import java.util.Iterator;
import java.util.List;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PDFSignatureField;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.encryption.client.EncryptionTypeResult;

/**
 * You can retrieve the names of all signature fields that are located in a PDF document that you want to sign or certify.
 * If you are unsure of the signature field names that are located in a PDF document or you want to verify the names, you can
 * programmatically retrieve them. The Signature service returns the fully qualified name of the signature field, such as
 * form1[0].grantApplication[0].page1[0].SignatureField1[0].
 *
 * The following Java code example retrieves the Signature Info for the given signature field located in a PDF document.
 */

@Component
@Service(value=GetPDFEncryption.class)
public class GetPDFEncryption {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  *
  */
 public void getPDFEncryption(String inputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Retrieve signature data for a given signature field.
  //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        EncryptionTypeResult encryptionTypeResult = docAssuranceService.getPDFEncryption(inDoc);

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
}
```

### Kennwortverschlüsselung von einem PDF-Dokument entfernen {#removing-password-encryption-from-pdf}

Entfernen Sie die kennwortbasierte Verschlüsselung aus einem PDF-Dokument, damit Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können, ohne ein Kennwort angeben zu müssen. Nachdem die kennwortbasierte Verschlüsselung von einem PDF-Dokument entfernt wurde, ist das Dokument nicht mehr geschützt.

**Syntax**:  `Document removePDFPasswordSecurity (Document inDoc,String password)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Ein Dokument wird als Eingabe bereitgestellt. Es muss kennwortgeschützt sein.<br /> </td>
  </tr>
  <tr>
   <td><code>password</code> </td>
   <td>Entweder ein Kennwort zum Öffnen eines Dokuments oder ein Berechtigungskennwort, das zum Entfernen des Sicherheitsschutzes von einem Dokument verwendet wird.<br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Codebeispiel wird eine kennwortbasierte Verschlüsselung von einem PDF-Dokument entfernt.

```java
    package com.adobe.docassurance.samples;

    import java.io.File;
    import java.io.FileNotFoundException;
    import org.apache.felix.scr.annotations.Component;
    import org.apache.felix.scr.annotations.Reference;
    import org.apache.felix.scr.annotations.Service;
    import org.apache.sling.jcr.api.SlingRepository;

    import com.adobe.aemfd.docmanager.Document;
    import com.adobe.fd.docassurance.client.api.DocAssuranceService;

    /**
    * The following Java code example removes password-based encryption from a PDF document.
    * The master password value used to remove password-based encryption is PermissionPassword
    *
    */
    @Component(enabled=true,immediate=true)
    @Service(value=RemovePasswordEncryption.class)
    public class RemovePasswordEncryption {

    // Create reference for DocAssuranceService
    @Reference
    private DocAssuranceService docAssuranceService;

    @Reference
        private SlingRepository slingRepository;

    /**
    * The below sample code demonstrates removing password encryption from a PDF using AEM EncryptionService.
    *
    * @param inFilePath  path of the input PDF File
    * Path Example for Files stored at hardDisk = "C:/temp/test.pdf"
    *
    * @param outFilePath path where the output PDF File needs to be saved
    * Path Example for Files stored at hardDisk = "C:/temp/test_out.pdf"
    * @throws Exception
    */
    public void removePasswordEncryption(String inputFile, String outputFile) throws Exception {

    File inFile = new File(inputFile);
    Document inDoc = new Document(inFile);

    File outFile = new File(outputFile);
    Document outDoc = null;

        try{

        String password = "PermissionPassword"; //master password with which the pdf was encrypted
                    //in case if the pdf is encrypted only with user password, specify the
                    //user password
        //Remove password-based encryption from the PDF document
        outDoc = docAssuranceService.removePDFPasswordSecurity(inDoc,password);

        }finally{
                    /**
                    * always close the PDFDocument object after your processing is done.
                    */
                    if(inDoc != null){
                        inDoc.close();
                    }

            }

            outDoc.copyToFile(outFile);

    }

    }
```

### Zertifikatverschlüsselung entfernen  {#removing-certificate-encryption}

Die zertifikatbasierte Verschlüsselung kann von einem PDF-Dokument entfernt werden, sodass Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können. Zum Entfernen der Verschlüsselung von einem PDF-Dokument, das mit einem Zertifikat verschlüsselt ist, referenzieren Sie einen privaten Schlüssel. Nachdem die Verschlüsselung von einem PDF-Dokument entfernt wurde, ist es nicht mehr geschützt.

**Syntax**:  `removePDFCertificateSecurity(Document inDoc, String alias, ResourceResolver resourceResolver)`

**Eingabeparameter**

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Ein Dokumentobjekt, das das zertifikatverschlüsselte PDF-Dokument darstellt.<br /> </td>
  </tr>
  <tr>
   <td><code>alias</code> </td>
   <td>Der Alias, der dem Schlüssel in Granite Trust Store entspricht, der zum Entfernen der zertifikatbasierten Verschlüsselung vom PDF-Dokument verwendet wird.<br /> </td>
  </tr>
  <tr>
   <td><code>ResourceResolver</code></td>
   <td>„ResourceResolver“ für den Zugriff auf den Key Store des jeweiligen Benutzers zum Abrufen der Anmeldedaten.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird eine zertifikatbasierte Verschlüsselung von einem PDF-Dokument entfernt.

```java
    package com.adobe.docassurance.samples;

    import java.io.File;

    import javax.jcr.Session;

    import org.apache.felix.scr.annotations.Component;
    import org.apache.felix.scr.annotations.Reference;
    import org.apache.felix.scr.annotations.Service;
    import org.apache.sling.api.resource.ResourceResolver;
    import org.apache.sling.jcr.api.SlingRepository;
    import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

    import com.adobe.aemfd.docmanager.Document;
    import com.adobe.fd.docassurance.client.api.DocAssuranceService;

    /**
    * The following Java code example removes certificate-based encryption from a PDF document
    *
    */
    @Component(enabled=true,immediate=true)
    @Service(value=RemovePKIEncryption.class)
    public class RemovePKIEncryption {

    // Create reference for docAssuranceServiceInterface
    @Reference
    private DocAssuranceService docAssuranceService;

    @Reference
        private SlingRepository slingRepository;

    @Reference
        private JcrResourceResolverFactory jcrResourceResolverFactory ;

    /**
    * The below sample code demonstrates encrypting PDF with Password using AEM docAssuranceService.
    *
    * @param inFilePath  path of the input PDF File
    * Path Example for Files stored at hardDisk = "C:/temp/test.pdf"
    *
    * @param outFilePath path where the output PDF File needs to be saved
    * Path Example for Files stored at hardDisk = "C:/temp/test_Encrypted.pdf"
    *
    * @throws Exception
    */
    public void removePKIEncryption(String inputFile, String outputFile) throws Exception {

    File inFile = new File(inputFile);
    Document inDoc = new Document(inFile);

    File outFile = new File(outputFile);
    Document outDoc = null;

            Session adminSession = null;
            ResourceResolver resourceResolver = null;
            try{
        adminSession = slingRepository.loginAdministrative(null);
        resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

        //Remove certificate-based encryption from the PDF document
        /**
        * Here the alias("encryption") of the private credential stored in the keystore of the
        * user has been provided with the user's resource resolver
        */
        outDoc = docAssuranceService.removePDFCertificateSecurity(inDoc, "encryption",resourceResolver);

            }catch(Exception e){

            // TODO Auto-generated catch block
            }finally{
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

            outDoc.copyToFile(outFile);
    }

    }
```

## Output Service {#output-service}

Der Output-Dienst stellt APIs zum Wiedergeben einer XDP-Datei in den Formaten .pdf, .pcl, .zpl und .ps bereit. Der Dienst unterstützt folgende APIs:

* **[generatePDFOutput](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutput-p):** Generiert ein PDF-Dokument, indem ein Formularentwurf mit auf einem Netzwerkspeicherort, lokalen Dateisystem oder HTTP-Speicherort als Literalwerte gespeicherten Daten zusammengeführt wird.

* **[generatePDFOutput](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutput-p):** Generiert ein PDF-Dokument, indem ein Formularentwurf mit in einer Anwendung gespeicherten Daten zusammengeführt wird.
* **[generatePDFOutputBatch](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutputbatch-p):** Führt einen Formularentwurf mit Daten zusammen, um ein PDF-Dokument zu erstellen. Optional wird für jeden Datensatz eine Metadatendatei generiert oder es wird die Ausgabe in einer PDF-Datei gespeichert.
* **[generatePrintedOutput](/help/forms/using/aem-document-services-programmatically.md#p-generateprintedoutput-p):** Generiert eine PCL-, PostScript- oder ZPL-Ausgabe aus einem Formularentwurf und einer Datendatei, die auf einem Netzwerkspeicherort, einem lokalen Dateisystem oder einem HTTP-Speicherort als Literalwerte gespeichert sind.

* **[generatePrintedOutput](/help/forms/using/aem-document-services-programmatically.md#p-generateprintedoutput-p):** Generiert eine PCL-, PostScript- und ZPL-Ausgabe aus einem Formularentwurf und einer Datendatei, die in einer Anwendung gespeichert sind.

### generatePDFOutput {#generatepdfoutput}

Die generatePDFOutput-API generiert ein PDF-Dokument, indem ein Formularentwurf mit Daten zusammengeführt wird. Optional wird für jeden Datensatz eine Metadatendatei generiert oder es wird die Ausgabe in einer PDF-Datei gespeichert. Verwenden Sie die generatePDFOutput-API für die Formularentwürfe oder Daten, die auf einem Netzwerkspeicherort, einem lokalen Dateisystem oder einem HTTP-Speicherort als Literalwerte gespeichert werden. Wenn der Formularentwurf und die XML-Daten in einer Anwendung gespeichert werden, verwenden Sie die [generatePDFOutput](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutput-p)-API.

**Syntax:** `Document generatePDFOutput(String uriOrFileName, Document data, PDFOutputOptions options);`

#### Eingabeparameter {#input-parameters}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>uriOrFileName</td>
   <td>Gibt den Pfad und den Namen der Eingabedatei an. Die Datei kann vom Typ „PDF“ oder „XDP“ sein. Wird nur der Dateiname angegeben, wird die Datei im Verhältnis zu contentRoot gelesen, das in den Optionen angegeben wird.</td>
  </tr>
  <tr>
   <td>data</td>
   <td>Eine XML-Datei mit den Daten, die mit dem PDF-Dokument zusammengeführt werden.<br /> </td>
  </tr>
  <tr>
   <td>options</td>
   <td>Gibt Werte von contentRoot-, locale-, AcrobatVersion-, linearizedPDF- und taggedPDF-Variablen an. Der options-Parameter akzeptiert ein Objekt vom Typ PDFOutputOptions. <br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird ein PDF-Dokument generiert, indem ein Formularentwurf mit Daten zusammengeführt wird, die in einer XML-Datei gespeichert sind.

```java
    @Reference private OutputService outputService;

    private File generatePDFOutput(String contentRoot,File inputXML,String templateStr,String acrobatVersion,String tagged,String linearized, String locale) {

    String outputFolder="C:/Output";

    Document doc=null;

    try {

            PDFOutputOptions option = new PDFOutputOptions();         option.setContentRoot(contentRoot);         if(acrobatVersion.equalsIgnoreCase("Acrobat_10"))

            {

                option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_10);

            } else if(acrobatVersion.equalsIgnoreCase("Acrobat_10_1")) {

                option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_10_1);

            } else if(acrobatVersion.equalsIgnoreCase("Acrobat_11")) {             option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_11);

            }

            if (tagged.equalsIgnoreCase("true") ) {

                option.setTaggedPDF(true );

            }

            if (linearized.equalsIgnoreCase("true") ) {

                option.setTaggedPDF(true );

            }

            if(locale!=null)

            {

                option.setLocale(locale);

            }

            InputStream in = new FileInputStream(inputXML);

            doc = outputService.generatePDFOutput(templateStr,new Document(in),option);         File toSave = new File(outputFolder+"Output.pdf");

            doc.copyToFile(toSave);

            return toSave;

        } catch (OutputServiceException e) {

            e.printStackTrace();

        }catch (FileNotFoundException e) {

            e.printStackTrace();

        } catch (IOException e) {

            e.printStackTrace();

        }finally{

                    doc.dispose();

        }

        return null;

    }
```

### generatePDFOutput  {#generatepdfoutput-1}

Die generatePDFOutput-API generiert ein PDF-Dokument, indem ein Formularentwurf mit Daten zusammengeführt wird. Generieren Sie optional eine Metadatendatei für jeden Datensatz oder speichern Sie die Ausgabe in einer PDF-Datei. Verwenden Sie die generatePrintedOutput-API für die Formularentwürfe oder Daten, die in einer Anwendung gespeichert sind. Wenn der Formularentwurf und die XML-Daten in einem Netzwerkspeicherort, lokal oder an einem HTTP-Speicherort als Literalwerte gespeichert werden, verwenden Sie die API [generatePDFOutput](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutput-p).

**Syntax:** `Document generatePDFOutput(Document inputdocument, Document data, PDFOutputOptions options)`

#### Eingabeparameter {#input-parameter}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Inputdocument<br /> </td>
   <td>Gibt den Pfad und den Namen der Eingabedatei an. Die Datei kann vom Typ „PDF“ oder „XDP“ sein. Wird nur der Dateiname angegeben, wird die Datei im Verhältnis zu contentRoot gelesen, das in den Optionen angegeben wird. <br /> </td>
  </tr>
  <tr>
   <td>data</td>
   <td>Eine XML-Datei mit den Daten, die mit dem PDF-Dokument zusammengeführt werden.<br /> </td>
  </tr>
  <tr>
   <td>options</td>
   <td>Gibt Werte von contentRoot-, locale-, AcrobatVersion-, linearizedPDF- und taggedPDF-Variablen an. Der options-Parameter akzeptiert ein Objekt vom Typ PDFOutputOptions.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird ein PDF-Dokument generiert, indem ein Formularentwurf mit Daten zusammengeführt wird, die in einer XML-Datei gespeichert sind.

```java
    @Reference private OutputService outputService;

    private File generatePDFOutput2(String contentRoot, File inputXML, File templateStr, String acrobatVersion, String tagged, String linearized, String locale) {

    String outputFolder="C:/Output";

    Document doc=null;

        try {

                PDFOutputOptions option = new PDFOutputOptions();             option.setContentRoot(contentRoot);
                if(locale!=null)

                {

                    option.setLocale(locale);

                }

                if(acrobatVersion.equalsIgnoreCase("Acrobat_10"))

                {

                    option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_10);

                } else if(acrobatVersion.equalsIgnoreCase("Acrobat_10_1")) {                 option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_10_1);

                } else if(acrobatVersion.equalsIgnoreCase("Acrobat_11")) {                 option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_11);

                }

                if (tagged.equalsIgnoreCase("true") ) {

                    option.setTaggedPDF(true );

                }

                if (linearized.equalsIgnoreCase("true") ) {

                    option.setTaggedPDF(true );

                }

                InputStream inputXMLStream = new FileInputStream(inputXML);

                InputStream templateStream = new FileInputStream(templateStr);;

                doc = outputService.generatePDFOutput(new Document(templateStream),new             Document(inputXMLStream),option);

                        File toSave = new File(outputFolder,"Output.pdf");

                        doc.copyToFile(toSave);

                        return toSave;

                    } catch (OutputServiceException e) {

                            e.printStackTrace();

                }catch (FileNotFoundException e) {

                            e.printStackTrace();

                } catch (IOException e) {

                            e.printStackTrace();

                }finally{

                                doc.dispose();

                }

                    return null;

    }
```

### generatePDFOutputBatch  {#generatepdfoutputbatch}

Führt einen Formularentwurf mit Daten zusammen, um ein PDF-Dokument zu erstellen. Optional wird für jeden Datensatz eine Metadatendatei generiert oder es wird die Ausgabe in einer PDF-Datei gespeichert. Verwenden Sie die generatePDFOutputBatch-API für die Formularentwürfe oder Daten, die auf einem Netzwerkspeicherort, einem lokalen Dateisystem oder HTTP-Speicherort als Literalwerte gespeichert sind.

**Syntax:** `BatchResult generatePDFOutputBatch(Map templates, Map data, PDFOutputOptions options, BatchOptions batchOptions);`

#### Eingabeparameter {#input-parameters-1}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>templates<br /> </td>
   <td>Gibt die Zuordnung des Schlüssels und den Dateinamen der Vorlage an.<br /> </td>
  </tr>
  <tr>
   <td>data</td>
   <td>Gibt die Zuordnung des Schlüssels und das Datendokument an. Wenn der Schlüssel nicht gleich null ist, wird das Datendokument mit der Vorlage für den in der Vorlagenzuordnung angegebenen entsprechenden Schlüssel wiedergegeben. </td>
  </tr>
  <tr>
   <td>options</td>
   <td>Gibt Werte von contentRoot-, locale-, AcrobatVersion-, linearizedPDF- und taggedPDF-Variablen an. Der options-Parameter akzeptiert ein Objekt vom Typ PDFOutputOptions. </td>
  </tr>
  <tr>
   <td>batchOptions</td>
   <td>Gibt den Wert der Variablen <code>generateManyFiles</code> an. Setzen Sie das Flag „generateManyFiles“, um mehrere Dateien zu generieren. Der „options“-Parameter akzeptiert ein Objekt vom Typ „BatchOptions“.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden PDF-Dokumente generiert, indem Formularentwürfe mit Daten zusammengeführt werden, die in einer XML-Datei gespeichert sind.

```java
private ArrayList generatePDFBatch(String contentRoot,String multipleFiles) {

String outputFolder="C:/Output";

    try {

        PDFOutputOptions option = new PDFOutputOptions();         option.setContentRoot(contentRoot);

        Map templates = new LinkedHashMap();

        Map data = new LinkedHashMap();

        String template1 = "PurchaseOrder.xdp"; String template2 = "CardApp.xdp";         templates.put(template1.substring(0, template1.indexOf(".xdp")),template1);         templates.put(template1.substring(0, template2.indexOf(".xdp")),template2);

        File inputXML1 = new File("c:/InputFolder/PurchaseOrder.xml");

        File inputXML2 = new File("c:/InputFolder/CardApp.xml");

        InputStream in1 = new FileInputStream(inputXML1);

        InputStream in2 = new FileInputStream(inputXML2);

        data.put(template1.substring(0, template1.indexOf(".xdp")),new         Document((in1))); data.put(template1.substring(0,         template1.indexOf(".xdp")),new Document((in2))); BatchOptions bo = new         BatchOptions(); BatchResult ret=null;         if(multipleFiles.equalsIgnoreCase("true"))

        {

            bo.setGenerateManyFiles(true);

            ret = outputService.generatePDFOutputBatch(templates, data, option, bo);

        } else {

            ret = outputService.generatePDFOutputBatch(templates, data, option, new             BatchOptions());

        }

        ArrayList outputs = new ArrayList();

        int counter=0;

        if(ret.getMetaDataDoc() !=null ){

        File toSave = new File(outputFolder+"Output.xml");

        ret.getMetaDataDoc().copyToFile(toSave);

        outputs.add(toSave);

        List<Document> list = ret.getGeneratedDocs();

        for(Document doc:list){

        File toSave = new File(outputFolder,"Output"+"_"+counter+".pdf");         doc.copyToFile(toSave);                    outputs.add(toSave);

        counter++;

        doc.dispose();

        }

        return outputs;

       } catch (OutputServiceException e) {

            e.printStackTrace();

       }catch (FileNotFoundException e) {

            e.printStackTrace();

       }catch (IOException e) {

            e.printStackTrace();

       }

       return null;

}
```

### generatePrintedOutput  {#generateprintedoutput}

Generiert eine PCL-, PostScript- und ZPL-Ausgabe aus einem Formularentwurf und einer Datendatei. Die Datendatei wird mit dem Formularentwurf zusammengeführt und für den Druck formatiert. Sie können die Ausgabe direkt an einen Drucker senden oder als Datei speichern. Verwenden Sie die generatePrintedOutput-API für die Formularentwürfe oder Daten, die in einer Anwendung gespeichert sind.

**Syntax:** `Document generatePrintedOutput(String uriOrFileName, Document data, PrintedOutputOptions);`

#### Eingabeparameter {#input-parameters-2}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>uriOrFileName<br /> </td>
   <td>Gibt den Pfad und den Namen der Eingabedatei an. Wird nur der Dateiname angegeben, wird die Datei im Verhältnis zu contentRoot gelesen, das in den Optionen angegeben wird. Die Datei kann vom Typ „PDF“ oder „XDP“ sein.<br /> </td>
  </tr>
  <tr>
   <td>data</td>
   <td>Eine XML-Datei mit Daten, die mit PDF-Dokumenten zusammengeführt werden.<br /> </td>
  </tr>
  <tr>
   <td>options</td>
   <td>Gibt Werte von contentRoot-, locale-, AcrobatVersion-, linearizedPDF- und taggedPDF-Variablen an. Der „options“-Parameter akzeptiert ein Objekt vom Typ „PrintedOutputOptions“.<br />  </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden eine PCL-, PostScript- und ZPL-Ausgabe aus einem Formularentwurf und Daten generiert. Der Ausgabetyp ist von dem Wert abhängig, der an den `printConfig`-Parameter übergeben wird.

```java
@Reference private OutputService outputService;

private File generatePrintedOutput(String contentRoot,File inputXML,String templateStr,String printConfig) {

String outputFolder="C:/Output";

Document doc=null;

    try {

            PrintedOutputOptions options = new PrintedOutputOptions();                           options.setContentRoot(contentRoot);

            if(printConfig.equalsIgnoreCase("ps"))

            {

                options.setPrintConfig(PrintConfig.PS_PLAIN);

            }else if(printConfig.equalsIgnoreCase("pcl")) {

                            options.setPrintConfig(PrintConfig.HP_PCL_5e);

                     }else if(printConfig.equalsIgnoreCase("zpl")) {                                                                       options.setPrintConfig(PrintConfig.ZPL300);

            }

            InputStream in = new FileInputStream(inputXML);

            doc = outputService.generatePrintedOutput(templateStr,new             Document(in),options);

            in.close();

            File toSave = new File(outputFolder,"Output"+"."+printConfig);             doc.copyToFile(toSave);

            return  toSave;

        } catch (OutputServiceException e) {

             e.printStackTrace();

        }catch (FileNotFoundException e) {

             e.printStackTrace();

        }catch (IOException e) {

             e.printStackTrace();

        }finally{

             doc.dispose();

        }

        return null;

}
```

### generatePrintedOutput {#generateprintedoutput-1}

Generiert eine PCL-, PostScript- und ZPL-Ausgabe aus einem Formularentwurf und einer Datendatei. Die Datendatei wird mit dem Formularentwurf zusammengeführt und für den Druck formatiert. Die Ausgabe kann direkt an einen Drucker gesendet oder als Datei gespeichert werden. Verwenden Sie die generatePrintedOutput-API für die Formularentwürfe oder für die Daten, die in einer Anwendung gespeichert sind.

**Syntax:** `Document generatePrintedOutput(Document inputdocument, Document data, PrintedOutputOptions);`

#### Eingabeparameter {#input-parameters-3}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>InputDocument<br /> </td>
   <td>Gibt den Pfad und den Namen der Eingabedatei an. Wird nur der Dateiname angegeben, wird die Datei im Verhältnis zu contentRoot gelesen, das in den Optionen angegeben wird. Die Datei kann vom Typ „XDP“ sein. </td>
  </tr>
  <tr>
   <td>data</td>
   <td>Eine XML-Datei mit Daten, die mit PDF-Dokumenten zusammengeführt werden.<br /> </td>
  </tr>
  <tr>
   <td>options</td>
   <td>Dieses Objekt wird verwendet, um die Werte von „contentRoot“, „locale“, „printConfig“, „copies“ und „paginationOverride“ festzulegen. Der „options“-Parameter akzeptiert ein Objekt vom Typ „PrintedOutputOptions“.<br />  </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden eine PCL-, PostScript- und ZPL-Ausgabe aus einem Formularentwurf und Daten generiert. Der Ausgabetyp ist von dem Wert abhängig, der an den `printConfig`-Parameter übergeben wird.

```java
@Reference private OutputService outputService;

private File generatePrintedOutput2(File  inputXML,File templateStr,String printConfig) {

String outputFolder="C:/Output";

Document doc=null;

       try {

            PrintedOutputOptions options = new PrintedOutputOptions();             if(printConfig.equalsIgnoreCase("ps"))

            {

                options.setPrintConfig(PrintConfig.PS_PLAIN);

            }else if(printConfig.equalsIgnoreCase("pcl")) {                                   options.setPrintConfig(PrintConfig.HP_PCL_5e);

            }else if(printConfig.equalsIgnoreCase("zpl")) {                                                                       options.setPrintConfig(PrintConfig.ZPL300);

                             }

            InputStream inputXMlStream = new FileInputStream(inputXML);

            InputStream templateStream = new FileInputStream(templateStr); doc =             outputService.generatePrintedOutput(new Document(templateStream),new             Document(inputXMlStream),options);

            File toSave = new File(outputFolder,"Output"+"."+printConfig);             doc.copyToFile(toSave);

            return toSave;

            } catch (OutputServiceException e) {

                e.printStackTrace();

            }catch (FileNotFoundException e) {

                e.printStackTrace();

            } catch (IOException e) {

                e.printStackTrace();

            }finally{

                doc.dispose();

            }

            return null;

}
```

### generatePrintedOutputBatch {#generateprintedoutputbatch}

Generiert ein Dokument im PS-, PCL- und ZPL-Format, indem ein Formularentwurf mit Daten zusammengeführt wird. Generieren Sie optional eine Metadatendatei für jeden Datensatz oder speichern Sie die Ausgabe in einer PDF-Datei. Verwenden Sie die generatePrintedOutputBatch-API für die Formularentwürfe oder Daten, die auf einem Netzwerkspeicherort, einem lokalen Dateisystem oder einem HTTP-Speicherort als Literalwerte gespeichert sind.

**Syntax`:`** `BatchResult generatePrintedOutputBatch(Map templates, Map data, PrintedOutputOptions options, BatchOptions batchOptions);`

#### Eingabeparameter {#input-parameters-4}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>templates<br /> </td>
   <td>Gibt die Zuordnung von Schlüssel- und Vorlagendateinamen an.<br /> </td>
  </tr>
  <tr>
   <td>data</td>
   <td>Gibt die Zuordnung des Schlüssels und das Datendokument an. Wenn der Schlüssel nicht gleich null ist, wird das Datendokument mit der Vorlage für den entsprechenden Schlüssel in der Vorlagenzuordnung wiedergegeben.<br /> </td>
  </tr>
  <tr>
   <td>options</td>
   <td>Gibt ein Objekt des Typs „PrintedOutputOptions“ an. Dieses Objekt wird verwendet, um die Werte von „contentRoot“, „locale“, printConfig“, „copies“ und „paginationOverride“ festzulegen.<br /> </td>
  </tr>
  <tr>
   <td>batchOptions</td>
   <td>Gibt den Wert der Variablen „generateManyFiles“ an. Setzen Sie das Flag „generateManyFiles“, um mehrere Dateien zu generieren. Der „options“-Parameter akzeptiert ein Objekt vom Typ „BatchOptions“.<br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden PCL-, PostScript-und ZPL-Ausgaben im Stapelverfahren aus mehreren Formularentwurfsvorlagen und Datendateien generiert. Der Ausgabetyp ist von dem Wert abhängig, der an den `printConfig`-Parameter übergeben wird.

```java
@Reference private OutputService outputService;

private ArrayList generatePrintedOutputBatch(String contentRoot,String multipleFiles,String printConfig) {

String outputFolder="C:/Output";

        try {

                PrintedOutputOptions option = new PrintedOutputOptions();                 option.setContentRoot(contentRoot);

                Map templates = new LinkedHashMap();

                Map data = new LinkedHashMap();

                String template1 = "PurchaseOrder.xdp";

                String template2 = "CardApp.xdp";

                templates.put(template1.substring(0,                 template1.indexOf(".xdp")),template1);                 templates.put(template1.substring(0,                 template2.indexOf(".xdp")),template2);

                File inputXML1 = new                                   File("c:/InputFolder/PurchaseOrder.xml");

                File inputXML2 = new File("c:/InputFolder/CardApp.xml");

                InputStream in1 = new FileInputStream(inputXML1);

                InputStream in2 = new FileInputStream(inputXML2);                  data.put(template1.substring(0,                     template1.indexOf(".xdp")),new Document((in1)));

                 data.put(template2.substring(0,                     template2.indexOf(".xdp")),new Document((in2)));

                 if(printConfig.equalsIgnoreCase("ps"))

                 {

                    option.setPrintConfig(PrintConfig.PS_PLAIN);

                 } else if(printConfig.equalsIgnoreCase("pcl"))

                 {

                    option.setPrintConfig(PrintConfig.HP_PCL_5e);

                 } else if(printConfig.equalsIgnoreCase("zpl")){

                                         option.setPrintConfig(PrintConfig.ZPL300);

                 }

                 option.setContentRoot(contentRoot);

                 BatchOptions bo = new BatchOptions();

                 BatchResult ret =                             outputService.generatePrintedOutputBatch(temp                                    lates, data, option, new                                                     BatchOptions());

                 ArrayList outputs = new ArrayList();

                 int counter=0;

                 if(ret.getMetaDataDoc() !=null ){

                 File toSave = new File(outputFolder,"Output"+".xml");                    ret.getMetaDataDoc().copyToFile(toSave);

                 outputs.add(toSave);

                 List<Document> list = ret.getGeneratedDocs();

                 for(Document doc:list){

                 File toSave = new                                                               File(outputFolder,"Output"+"_"+counter+".                                        "+printConfig);                                    doc.copyToFile(toSave);

                 outputs.add(toSave);

                 counter++;

                 doc.dispose();

                 }

                 return outputs;

          }

            catch (OutputServiceException e) {

                e.printStackTrace();

          }catch (FileNotFoundException e) {

                e.printStackTrace();

          } catch (IOException e) {

                e.printStackTrace();

          }

            return null;

  }
```

## Formularservice {#forms-service}

Der Forms-Dienst stellt APIs zur Verfügung, die den Import und Export von Daten in ein interaktives PDF-Formular und aus diesem ermöglichen. Ein interaktives PDF-Formular ist ein PDF-Dokument, das ein oder mehrere Felder enthält, mit denen Informationen der Benutzer angezeigt und gesammelt werden. Der Dienst unterstützt folgende APIs:

* **[exportData](/help/forms/using/aem-document-services-programmatically.md#p-exportdata-p):** exportiert Daten aus einem PDF-Formular.
* **[importData](/help/forms/using/aem-document-services-programmatically.md#p-importdata-p):** importiert Daten in ein interaktives PDF-Formular.

### exportData {#exportdata}

Exportiert Daten aus einem interaktiven PDF-Formular in XML- und XDP-Formate.

**Syntax:** `Document exportData(Document xdpOrPdf, DataFormat dataFormat)`

#### Eingabeparameter {#input-parameters-5}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>xdpOrPdf<br /> </td>
   <td>Gibt ein Dokumentobjekt an, das eine XDP- oder PDF-Datei enthält. </td>
  </tr>
  <tr>
   <td>dataFormat<br /> </td>
   <td>Gibt das Format an, in das Daten exportiert werden. Es akzeptiert Variablen des Typs „enum (XDP, XmlData, Auto)“.<br />  </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden Formulardaten aus einem interaktiven PDF-Formular in XML- und XDP-Formate exportiert.

#### Beispiel {#sample}

```java
@Reference private FormsService formsService;
private File exportData(String  dataFormat, File  inDoc) {

String outputFolder="C:/Output";

InputStream in; Document doc=null;

try {

        in = new FileInputStream(inDoc);

        if(dataFormat.equalsIgnoreCase("xml"))

        {

          doc=formsService.exportData(new Document(in),                                       DataFormat.XmlData);

        }

        else if(dataFormat.equalsIgnoreCase("xdp")) {

        doc =formsService.exportData(new Document(in),                       DataFormat.XDP);

        }

        File toSave = new File(outputFolder,"Output"+"."+dataFormat);

        doc.copyToFile(toSave);

        return toSave;

    } catch (FormsServiceException e) {

       e.printStackTrace();

    }catch (FileNotFoundException e) {

       e.printStackTrace();

    } catch (IOException e) {

       e.printStackTrace();

    }finally{

        doc.dispose();

    }

    return null;

 }
```

### importData {#importdata}

Importiert Formulardaten in ein interaktives PDF-Formular.

**Syntax:** `Document importData(Document PDF, Document data)`

#### Eingabeparameter {#input-parameters-6}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>PDF<br /> </td>
   <td>Gibt ein Dokumentobjekt an, das PDF-Dateien enthält. </td>
  </tr>
  <tr>
   <td>letzten 30 Tage<br /> </td>
   <td>Eine XML-Datei, die Daten im XML-Format enthält.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden Formulardaten in ein interaktives PDF-Formular importiert.

#### Beispiel {#sample-1}

```java
@Reference private FormsService formsService

private File importData(File inDoc, File inXML)

{

 String outputFolder="C:/Output";

 Document doc=null;

 try {

        InputStream in = new FileInputStream(inDoc);

        InputStream in2 = new FileInputStream(inXML);

        doc=formsService.importData(new Document(in), new Document(in2));

        File toSave = new File(outputFolder,"Output.pdf");

        doc.copyToFile(toSave);

    } catch (FormsServiceException e) {

         e.printStackTrace();

    }catch (FileNotFoundException e) {

         e.printStackTrace();

    } catch (IOException e) {

         e.printStackTrace();

    }finally{

        doc.dispose();

    }

    return null;

}
```

## PDF Generator-Dienst {#pdfgeneratorservice}

Der PDF Generator-Dienst stellt APIs zum Konvertieren nativer Dateiformate in PDF bereit. Er kann außerdem PDF-Dokumente in andere Dateiformate konvertieren und die Größe von PDF-Dokumenten optimieren.

### GeneratePDFService {#generatepdfservice}

GeneratePDFService stellt APIs zum Konvertieren verschiedener Dateiformate wie .doc, .docx, .ppt, .pptx, .xls, .xlsx, .odp, .odt, .ods, (veraltet).swf, .jpg, .bmp, .tif, .png, .html und vieler anderer Dateiformate in PDF bereit. Darüber hinaus stellt der Dienst APIs zum Exportieren von PDF-Dateien in verschiedene Dateiformate und zum Optimieren von PDFs bereit. Der Dienst unterstützt die folgenden APIs:

* **createPDF**: Konvertiert einen unterstützten Dateityp in ein PDF-Dokument. Unterstützt werden Dateiformate wie Microsoft Word, Microsoft PowerPoint, Microsoft Excel und Microsoft Project. Außer diesen Anwendungen können auch von anderen Anbietern bereitgestellte allgemeine Anwendungen zur PDF-Generierung mit der API verbunden werden.
* **exportPDF**: Konvertiert ein PDF-Dokument in einen unterstützten Dateityp. Die Methode akzeptiert eine PDF-Datei als Eingabe und exportiert den Inhalt des PDF-Dokuments im Format des angegebenen Dateityps. Sie können ein PDF-Dokument in Encapsulated PostScript( eps), HTML 3.2( htm, html), HTML 4.01 mit CSS 1.0( htm, html), JPEG( jpg, jpeg, jpe), JPEG2000( jpf, jpx, jp2, j2k, j2c, jpc), Microsoft Word Dokument( doc, docx) Microsoft Excel Workbook( xlsx), Microsoft PowerPoint Presentation( pptx), PNG( png), PostScript( ps), Rich Text Format( rtf), Text(Accessible)( txt), Text(Plain)( txt) TIFF( tif, tiff), XML 1.0( xml), PDF/A-1a(sRGB), PDF/A-1b, PDF/A-2a(sRGB), PDF/A-2b(sRGB), PDF/A-3a(sRGB), PDF/A-3b(sRGB) Formate. Sie können auch [benutzerdefinierte Preflight-Profile](https://helpx.adobe.com/acrobat/using/preflight-profiles-acrobat-pro.html) für die PDF-Ausgabe angeben.

* **optimizePDF**: Optimiert das PDF-Dokument und konvertiert ein PDF-Dokument aus einem Typ in einen anderen. Die Methode akzeptiert ein PDF-Dokument als Eingabe.
* **htmlToPdf2**: Konvertiert eine HTML-Seite in ein PDF-Dokument. Als Eingabe wird die URL der HTML-Seite akzeptiert.

>[!NOTE]
>
>Die HTMLtoPDF-API wird für AEM Forms-Server unter AIX-Betriebssystemen nicht mehr unterstützt.

#### PDF Generator API verfügbar unter Microsoft Windows und Linux  {#pdf-generator-api-available-on-microsoft-windows-and-linux}

<table>
 <tbody>
  <tr>
   <td><strong>API</strong></td>
   <td><p><strong>Microsoft Windows </strong></p> </td>
   <td><strong>Linux </strong></td>
  </tr>
  <tr>
   <td>createPDF</td>
   <td><strong>✓</strong></td>
   <td><strong>they</strong></td>
  </tr>
  <tr>
   <td>htmlToPDF</td>
   <td><strong>they</strong></td>
   <td><strong>they</strong></td>
  </tr>
   <td>optimizePDF</td>
   <td><strong>they</strong></td>
   <td>✖</td>
  </tr>
  <tr>
   <td>exportPDF</td>
   <td><strong>they</strong></td>
   <td>✖</td>
  </tr>
  <tr>
   <td>OCR PDF (durchsuchbares PDF)</td>
   <td><strong>they</strong></td>
   <td>✖</td>
  </tr>
 </tbody>
</table>

#### createPDF {#createpdf}

Die createPDF-API konvertiert einen unterstützten Dateityp in ein PDF-Dokument. Unterstützt werden verschiedene Dateiformate wie Microsoft Word, Microsoft PowerPoint, Microsoft Excel und Microsoft Project. Außer diesen Anwendungen können auch von anderen Anbietern bereitgestellte allgemeine Anwendungen zur PDF-Generierung mit der API verbunden werden.

Für die Konvertierung sind nur wenige Parameter obligatorisch. Das Eingabedokument ist ein obligatorischer Parameter. Sie können die Sicherheitsberechtigungen, die Einste für die PDF-Ausgabe sowie die Metadaten später auf das ausgegebene PDF-Dokument anwenden.

Der createPDF-Dienst gibt ein java.util.Map mit Ergebnissen zurück. Die Schlüssel der Zuordnung sind:

* ConvertedDoc: Enthält das neu erstellte PDF-Dokument.
* LogDoc: Enthält die Protokolldatei.

Der createPDF-Dienst gibt die folgenden Ausnahmen aus:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

**Syntax:** `Map createPDF(Document inputDoc, String inputFilename, String fileTypeSettings, String pdfSettings, String securitySettings, Document settingsDoc, Document xmpDoc) throws InvalidParameterException, ConversionException, FileFormatNotSupportedException;`

#### Eingabeparameter {#input-parameters-7}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Gibt ein Dokumentobjekt an. Das Dokumentobjekt enthält die Eingabedatei. Erstellt ein com.adobe.aemfd.docmanager.Document-Objekt für das Eingabedokument. Dieser Parameter ist erforderlich.</td>
  </tr>
  <tr>
   <td>inputFileName<br /> </td>
   <td>Name der Eingabedatei zusammen mit der Erweiterung. Dieser Parameter ist erforderlich.<br /> </td>
  </tr>
  <tr>
   <td>fileTypeSettings</td>
   <td>Dies ist ein optionaler Parameter.</td>
  </tr>
  <tr>
   <td>pdfSettings</td>
   <td><p>PDF-Ausgabe für das konvertierte Dokument. Sie können nur die folgenden Einstellungen anwerden:</p>
    <ul>
     <li>High_Quality_Print<br /> </li>
     <li>PDFA1b_2005_RGB<br /> </li>
     <li>PDFA1b_2005_CMYK<br /> </li>
     <li>PDFX1a_2001<br /> </li>
     <li>PDFX3_2002<br /> </li>
     <li>Press_Quality<br /> </li>
     <li>Smallest_File_Size</li>
    </ul> <p>Dies ist ein optionaler Parameter.<br /> </p> </td>
  </tr>
  <tr>
   <td>securitySettings</td>
   <td><p>Sicherheitseinstellungen für das konvertierte Dokument. Sie können die folgenden Einstellungen anwenden:</p>
    <ul>
     <li>Ohne Sicherheit</li>
     <li>Kennwortschutz<br /> </li>
     <li>Zertifikatsicherheit<br /> </li>
     <li>Adobe Policy Server</li>
    </ul> <p>Dies ist ein optionaler Parameter.</p> </td>
  </tr>
  <tr>
   <td>settingsDoc</td>
   <td>Die Datei enthält die Einstellungen, die beim Generieren des PDF-Dokuments übernommen werden (z. B. die Optimierung des PDF-Dokuments für die Webanzeige) sowie die Einstellungen, die angewendet werden, nachdem das PDF-Dokument erstellt wurde (z. B. Ansicht beim Öffnen und Sicherheit). Dies ist ein optionaler Parameter.<br /> </td>
  </tr>
  <tr>
   <td>xmpDoc </td>
   <td>Die Datei enthält Metadateninformationen, die auf das generierte PDF-Dokument angewendet werden. Dieser Parameter ist optional.<br /> </td>
  </tr>
 </tbody>
</table>

Mit dem folgenden Java-Code wird ein Dokument mit einem unterstützten Dateityp in ein PDF-Dokument konvertiert.

```java
@Reference GeneratePDFService generatePdfService;
File createPDF(File inputFile, String inputFilename, String fileTypeSettings, String pdfSettings, String securitySettings, File settingsFile, File xmpFile) throws Exception
{
 Transaction tx = OSGiUtils.getTransactionManager().getTransaction();
 // Begin transaction
 if (tx == null)
 OSGiUtils.getTransactionManager().begin();
 String outputFolder="C:/Output"
 Document convertedDoc = null;
 Document inDoc = null;
 Document settingsDoc = null;
 Document xmpDoc = null;
 try
 {
  inDoc = new Document(inputFile);
  if(inputFilename == null || inputFilename.trim().equals("")) {
   throw new Exception("Input file name cannot be null");
  }
  if(inputFileExtension.lastIndexOf('.') == -1) {
   throw new Exception("Input file should have an extension");
  }
  if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
  settingsDoc = new Document(settingsFile);
  if(xmpFile != null && xmpFile.exists() && xmpFile.isFile())
  xmpDoc = new Document(xmpFile);
  Map result = generatePdfService.createPDF(inDoc, inputFilename, fileTypeSettings, pdfSettings, securitySettings, settingsDoc, xmpDoc);
  convertedDoc = (Document)result.get("ConvertedDoc");
  OSGiUtils.getTransactionManager().commit();
  File outputFile = new File(outputFolder,"Output.pdf");
  doc.copyToFile(outputFile);
  return outputFile;
 }
 catch (Exception e)
 {
  if (OSGiUtils.getTransactionManager().getTransaction() != null)
  OSGiUtils.getTransactionManager().rollback();
  throw e;
 }
 finally {
  if (convertedDoc != null) {
   convertedDoc.dispose();
   convertedDoc = null;
  }
  if (inDoc != null) {
   inDoc.dispose();
   inDoc = null;
  }
  if (settingsDoc != null) {
   settingsDoc.dispose();
   settingsDoc = null;
  }
  if (xmpDoc != null) {
   xmpDoc.dispose();
   xmpDoc = null;
  }
 }
}
```

#### exportPDF  {#exportpdf}

Konvertiert ein PDF-Dokument in einen unterstützten Dateityp. Die Methode akzeptiert eine PDF-Datei als Eingabe und exportiert den Inhalt des PDF-Dokuments im Format des angegebenen Dateityps.

Der createPDF-Dienst gibt ein java.util.Map mit Ergebnissen zurück. Die Schlüssel der Zuordnung sind:

* ConvertedDoc: Enthält das Ausgabedokument.

Der createPDF-Dienst gibt die folgenden Ausnahmen aus:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

**Syntax:**

```java
Map exportPDF(Document inputDoc, String inputFileName, String formatType, Document settingsDoc) throws ConversionException, InvalidParameterException, FileFormatNotSupportedException;
```

#### Eingabeparameter {#input-parameters-8}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Gibt das zu konvertierende Dokument an. </td>
  </tr>
  <tr>
   <td>inputFileName<br /> </td>
   <td>Der Name der Datei mit der Erweiterung.<br /> </td>
  </tr>
  <tr>
   <td>formatType</td>
   <td>Das Ausgabeformat für die exportPDF-API.<br /> </td>
  </tr>
  <tr>
   <td>settingsDoc </td>
   <td>Die Datei enthält die bei der Generierung des Ausgabedokuments anzuwendenden Konfigurationen. In der Regel handelt es sich um eine XML-Datei.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird ein PDF-Dokument in den angegebenen Dateityp konvertiert.

```java
(tx == null)
OSGiUtils.getTransactionManager().begin();
String outputFolder="C:/Output"
Document convertedDoc = null;
Document inDoc = null;
Document settingsDoc = null;
try
{
 inDoc = new Document(inputFile);
 if(inputFileName == null || inputFileName.trim().equals("")) {
  throw new Exception("Input file name cannot be null");
 }
 if(inputFileExtension.lastIndexOf('.') == -1) {
  throw new Exception("Input file should have an extension");
 }
 if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
 settingsDoc = new Document(settingsFile);
 Map result = generatePdfService.exportPDF(inDoc, inputFileName, formatType, settingsDoc);
 convertedDoc = (Document)result.get("ConvertedDoc");
 OSGiUtils.getTransactionManager().commit();
 File outputFile = new File(outputFolder,"OutputFile");
 doc.copyToFile(outputFile);
 return outputFile;
}
catch (Exception e)
{
 if (OSGiUtils.getTransactionManager().getTransaction() != null)
 OSGiUtils.getTransactionManager().rollback();
 throw e;
}
finally {
 if (convertedDoc != null) {
  convertedDoc.dispose();
  convertedDoc = null;
 }
 if (inDoc != null) {
  inDoc.dispose();
  inDoc = null;
 }
 if (settingsDoc != null) {
  settingsDoc.dispose();
  settingsDoc = null;
 }
}
}
```

#### optimizePDF {#optimizepdf}

Die OptimizePDF-API optimiert PDF-Dateien durch Reduzierung ihrer Größe. Als Ergebnis dieser Konvertierung erhalten Sie PDF-Dateien, die eventuell kleiner sind als die Originalversionen. Bei diesem Vorgang werden außerdem PDF-Dokumente in die in den Optimierungsparametern angegebene PDF-Version konvertiert. Er gibt ein OptimizePDFResult-Objekt zurück, das die optimierte PDF-Datei enthält.

Der createPDF-Dienst gibt die folgenden Ausnahmen aus:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

**Syntax:**

```java
OptimizePDFResult optimizePDF(Document inputDoc, String fileTypeSettings, Document settingsDoc) throws ConversionException, InvalidParameterException, FileFormatNotSupportedException;
```

#### Eingabeparameter {#input-parameters-9}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Gibt das Eingabedokument an. Dieser Parameter ist erforderlich.</td>
  </tr>
  <tr>
   <td>fileTypeSettings<br /> </td>
   <td>Dies ist ein optionaler Parameter.<br /> </td>
  </tr>
  <tr>
   <td>settingsDoc </td>
   <td>Die Datei enthält die Einstellungen, die beim Generieren des PDF-Dokuments übernommen werden (z. B. die Optimierung des PDF-Dokuments für die Webanzeige) sowie die Einstellungen, die angewendet werden, nachdem das PDF-Dokument erstellt wurde (z. B. Ansicht beim Öffnen und Sicherheit). Dies ist ein optionaler Parameter.<br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird die PDF-Eingabedatei durch Reduzieren ihrer Größe optimiert.

```java
@Reference GeneratePDFService generatePdfService;
File optimizePDF(File inputFile, String fileTypeSettings, File settingsFile) throws Exception
{
 Transaction tx = OSGiUtils.getTransactionManager().getTransaction();
 // Begin transaction
 if (tx == null)
 OSGiUtils.getTransactionManager().begin();
 String outputFolder="C:/Output"
 Document convertedDoc = null;
 Document inDoc = null;
 Document settingsDoc = null;
 try
 {
  inDoc = new Document(inputFile);
  if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
  settingsDoc = new Document(settingsFile);
  OptimizePDFResult result = generatePdfService.optimizePDF(inDoc, fileTypeSettings, settingsDoc);
  convertedDoc = result.getConvertedDocument();
  OSGiUtils.getTransactionManager().commit();
  File outputFile = new File(outputFolder,"Output.pdf");
  doc.copyToFile(outputFile);
  return outputFile;
 }
 catch (Exception e)
 {
  if (OSGiUtils.getTransactionManager().getTransaction() != null)
  OSGiUtils.getTransactionManager().rollback();
  throw e;
 }
 finally {
  if (convertedDoc != null) {
   convertedDoc.dispose();
   convertedDoc = null;
  }
  if (inDoc != null) {
   inDoc.dispose();
   inDoc = null;
  }
  if (settingsDoc != null) {
   settingsDoc.dispose();
   settingsDoc = null;
  }
 }
}
```

#### htmlToPdf2 {#htmltopdf}

Konvertiert eine HTML-Seite in ein PDF-Dokument. Als Eingabe wird die URL der HTML-Seite akzeptiert.

Der htmlToPdf2-Dienst gibt ein HtmlToPdfResult-Objekt zurück. Sie können die konvertierte PDF-Datei über result.getConvertedDocument() abrufen.

Der htmlToPdf2-Dienst gibt die folgenden Ausnahmen aus:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

**Syntax:**

```java
HtmlToPdfResult htmlToPdf2(String inputUrl, String fileTypeSettingsName, String securitySettingsName, Document settingsDoc, Document xmpDoc) throws ConversionException, InvalidParameterException, FileFormatNotSupportedException;
```

#### Eingabeparameter {#input-parameters-10}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Gibt das Eingabedokument an. Dieser Parameter ist erforderlich.</td>
  </tr>
  <tr>
   <td>fileTypeSettings<br /> </td>
   <td>Dies ist ein optionaler Parameter.<br /> </td>
  </tr>
  <tr>
   <td>settingsDoc </td>
   <td>Die Datei enthält die Einstellungen, die beim Generieren des PDF-Dokuments übernommen werden (z. B. die Optimierung des PDF-Dokuments für die Webanzeige) sowie die Einstellungen, die angewendet werden, nachdem das PDF-Dokument erstellt wurde (z. B. Ansicht beim Öffnen und Sicherheit). Dies ist ein optionaler Parameter.<br /> </td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel wird eine HTML-Seite in ein PDF-Dokument konvertiert.

```java
Reference GeneratePDFService generatePdfService;
File htmlToPdf(String inputUrl, String fileTypeSettingsName, String securitySettingsName, File settingsFile, File xmpFile) throws Exception
{
 Transaction tx = OSGiUtils.getTransactionManager().getTransaction();
 // Begin transaction
 if (tx == null)
 OSGiUtils.getTransactionManager().begin();
 String outputFolder="C:/Output"
 Document convertedDoc = null;
 Document settingsDoc = null;
 Document xmpDoc = null;
 try
 {
  if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
  settingsDoc = new Document(settingsFile);
  if(xmpFile != null && xmpFile.exists() && xmpFile.isFile())
  xmpDoc = new Document(xmpFile);
  HtmlToPdfResult result = generatePdfService.htmlToPdf2(inputURL, fileTypeSettingsName, securitySettingsName, settingsDoc, xmpDoc);;
  convertedDoc = result.getConvertedDocument();
  OSGiUtils.getTransactionManager().commit();
  File outputFile = new File(outputFolder,"Output.pdf");
  doc.copyToFile(outputFile);
  return outputFile;
 }
 catch (Exception e)
 {
  if (OSGiUtils.getTransactionManager().getTransaction() != null)
  OSGiUtils.getTransactionManager().rollback();
  throw e;
 }
 finally {
  if (convertedDoc != null) {
   convertedDoc.dispose();
   convertedDoc = null;
  }
  if (xmpDoc != null) {
   xmpDoc.dispose();
   xmpDoc = null;
  }
  if (settingsDoc != null) {
   settingsDoc.dispose();
   settingsDoc = null;
  }
 }
}
```

### DistillerService {#distillerservice}

Der Distiller-Dienst konvertiert PostScript-, Encapsulated PostScript (EPS)- und PRN (Printer Text Files)-Dateien in PDF-Dateien. Der Distiller-Dienst dient häufig zum Konvertieren großen Mengen gedruckter Dokumente in elektronische Dokumente, z. B. Rechnungen und Belege. Das Konvertieren von Dokumenten in PDF ermöglicht Unternehmen auch, ihren Kunden eine Papier- und eine elektronische Version eines Dokuments zu senden. Die unterstützten Dateiformate sind .ps, .eps und .prn. Der Dienst unterstützt folgende APIs:

Der createPDF-Dienst gibt ein java.util.Map mit Ergebnissen zurück. Die Schlüssel der Zuordnung sind:

* ConvertedDoc: Enthält das neu erstellte PDF-Dokument.
* LogDoc: Enthält die Protokolldatei.

Der createPDF-Dienst gibt die folgenden Ausnahmen aus:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

#### createPDF  {#createpdf-1}

Konvertiert die Formate in PDF-Dokumente. Diese Methode akzeptiert die Dateiformate .ps, .eps, and .prn als Eingaben. Sie können bestimmte Sicherheitsberechtigungen, Ausgabeeinstellungen und Metadaten auf das PDF-Dokument anwenden.

**Syntax:**

```java
Map createPDF(Document inputDoc, String inputFileName, String pdfSettings, String securitySettings, Document settingsDoc, Document xmpDoc) throws ConversionException, InvalidParameterException, FileFormatNotSupportedException;
```

#### Eingabeparameter {#input-parameters-11}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Gibt das Eingabedokument an. Dieser Parameter ist erforderlich.</td>
  </tr>
  <tr>
   <td>inputFileName</td>
   <td>Gibt den vollständigen Namen der Eingabedatei zusammen mit deren Erweiterung an. Dieser Parameter ist erforderlich.</td>
  </tr>
  <tr>
   <td>pdfSettings</td>
   <td><p>PDF-Ausgabeeinstellungen für das konvertierte Dokument. Sie können nur die folgenden Einstellungen anwerden:</p>
    <ul>
     <li>High_Quality_Print<br /> </li>
     <li>PDFA1b_2005_RGB<br /> </li>
     <li>PDFA1b_2005_CMYK<br /> </li>
     <li>PDFX1a_2001<br /> </li>
     <li>PDFX3_2002<br /> </li>
     <li>Press_Quality<br /> </li>
     <li>Smallest_File_Size</li>
    </ul> <p>Dies ist ein optionaler Parameter.</p> </td>
  </tr>
  <tr>
   <td>securitySettings</td>
   <td><p>Sicherheitseinstellungen für das konvertierte Dokument. Sie können die folgenden Einstellungen anwenden:</p>
    <ul>
     <li>Ohne Sicherheit</li>
     <li>Kennwortschutz<br /> </li>
     <li>Zertifikatsicherheit<br /> </li>
     <li>Adobe Policy Server</li>
    </ul> <p>Dies ist ein optionaler Parameter.</p> </td>
  </tr>
  <tr>
   <td>settingsDoc </td>
   <td>Die Datei enthält die Einstellungen, die beim Generieren des PDF-Dokuments übernommen werden (z. B. die Optimierung des PDF-Dokuments für die Webanzeige) sowie die Einstellungen, die angewendet werden, nachdem das PDF-Dokument erstellt wurde (z. B. Ansicht beim Öffnen und Sicherheit). Dies ist ein optionaler Parameter.<br /> </td>
  </tr>
  <tr>
   <td>xmpDoc </td>
   <td>Die Datei enthält Metadaten für das erstellte PDF-Dokument. Dies ist ein optionaler Parameter.</td>
  </tr>
 </tbody>
</table>

Im folgenden Java-Codebeispiel werden Eingabedateien der Typen PostScript (PS), Encapsulated PostScript (EPS) und Printer Text Files (PRN) in PDF-Dateien.

```java
@Reference DistillerService distillerService;
File createPDF(File inputFile, String inputFilename, String pdfSettings, String securitySettings, File settingsFile, File xmpFile) throws Exception
{
 Transaction tx = OSGiUtils.getTransactionManager().getTransaction();
 // Begin transaction
 if (tx == null)
 OSGiUtils.getTransactionManager().begin();
 String outputFolder="C:/Output"
 Document convertedDoc = null;
 Document inDoc = null;
 Document settingsDoc = null;
 Document xmpDoc = null;
 try
 {
  inDoc = new Document(inputFile);
  if(inputFilename == null || inputFilename.trim().equals("")) {
   throw new Exception("Input file name cannot be null");
  }
  if(inputFileExtension.lastIndexOf('.') == -1) {
   throw new Exception("Input file should have an extension");
  }
  if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
  settingsDoc = new Document(settingsFile);
  if(xmpFile != null && xmpFile.exists() && xmpFile.isFile())
  xmpDoc = new Document(xmpFile);
  Map result = distillerService.createPDF(inDoc, inputFilename, pdfSettings, securitySettings, settingsDoc, xmpDoc);
  convertedDoc = (Document)result.get("ConvertedDoc");
  OSGiUtils.getTransactionManager().commit();
  File outputFile = new File(outputFolder,"Output.pdf");
  doc.copyToFile(outputFile);
  return outputFile;
 }
 catch (Exception e)
 {
  if (OSGiUtils.getTransactionManager().getTransaction() != null)
  OSGiUtils.getTransactionManager().rollback();
  throw e;
 }
 finally {
  if (convertedDoc != null) {
   convertedDoc.dispose();
   convertedDoc = null;
  }
  if (inDoc != null) {
   inDoc.dispose();
   inDoc = null;
  }
  if (settingsDoc != null) {
   settingsDoc.dispose();
   settingsDoc = null;
  }
  if (xmpDoc != null) {
   xmpDoc.dispose();
   xmpDoc = null;
  }
 }
}
```

