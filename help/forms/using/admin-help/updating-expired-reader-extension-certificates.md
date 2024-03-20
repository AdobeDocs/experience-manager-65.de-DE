---
title: Die Gültigkeit von Reader Extensions-Zertifikaten und ihre Auswirkungen
description: Die Gültigkeit von Reader Extensions-Zertifikaten und ihre Auswirkungen
exl-id: 4e14e0dc-f248-4f6e-a075-6012b6792d9d
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 96%

---


# Die Gültigkeit von Reader Extensions-Zertifikaten und ihre Auswirkungen {#expiration-of-reader-extensions-certificates-and-its-impact}

Kundinnen und Kunden von Adobe Experience Manager Forms (AEM Forms) mit einer Basislizenz für Adobe Managed Services oder On-Premise Enterprise sind berechtigt, den Service Acrobat Reader DC-Erweiterungen zu nutzen. Dieser Service ermöglicht einer Organisation das einfache Freigeben interaktiver PDF-Dokumente, indem er die Funktionalität von Acrobat Reader um zusätzliche Nutzungsrechte erweitert. Der Service fügt einem PDF-Dokument Nutzungsrechte hinzu und aktiviert Funktionen, die beim Öffnen eines PDF-Dokuments mit Adobe Acrobat Reader nicht zur Verfügung stehen, z. B. das Hinzufügen von Kommentaren zu einem Dokument, das Ausfüllen von Formularen und das Speichern des Dokuments. Externe Benutzer benötigen keine zusätzliche Software oder Plug-Ins für das Verwenden von Dokumenten mit aktivierten Benutzerrechten. PDF-Dokumente, für die zusätzlich Nutzungsrechte gelten, werden als Dokumente mit aktivierten Nutzungsrechten bezeichnet. Benutzende, die ein berechtigungsaktiviertes PDF-Dokument in Acrobat Reader öffnen, können Vorgänge durchführen, die für dieses Dokument aktiviert sind.

Adobe verwendet eine PKI (Public Key Infrastructure), um digitale Zertifikate zur Verwendung bei der Lizenzierung und Aktivierung von Funktionen auszustellen. Adobe hat Zertifikate unter der Zertifizierungsstelle **Adobe Root CA** ausgestellt, die am 7. Januar 2023 auslaufen wird. Die Gültigkeit des Zertifikats wirkt sich nicht auf PDF-Dokumente aus, die mit Produktionszertifikaten erweitert wurden, welche von den **Adobe Root CA** basierten Zertifikaten ausgestellt wurden (alte Zertifikate). Alle PDF-Dokumente, die mithilfe der alten Zertifikate vor dem 7. Januar 2023 Reader Extended wurden, einschließlich der von Kundenseite aus heruntergeladenen, funktionieren weiterhin mit allen Nutzungsrechten, die für sie gelten, und benötigen keine Updates.

Eine neue Zertifizierungsstelle, **Adobe Root CA G2**, und Zertifikate, die auf der neuen Zertifizierungsstelle basieren, sind jetzt verfügbar. Beginnen Sie am oder vor dem 7. Januar 2023 mit der Verwendung der neuen Zertifikate, die auf **Adobe Root CA G2** basieren, um die Reader Extension auf Ihre neuen PDF-Dokumente anzuwenden.  Sie können neue Zertifikate [von der Adobe-Lizenzierungs-Website](https://licensing.adobe.com/) oder vom Adobe-Support erhalten.

## Häufig gestellte Fragen

**F. Was ist der Unterschied zwischen einem Adobe-Stammzertifikat und einem Acrobat Reader Extensions-Zertifikat? Ist das Adobe-Stammzertifikat von einem Acrobat Reader Extensions-Zertifikat abhängig? Laufen diese beiden Zertifikate im Januar 2023 aus?**

A. Adobe Root CA ist die Zertifizierungsstelle, von der aus ein Acrobat Reader Extensions-Zertifikat ausgestellt wird. Am 7. Januar 2023 laufen „Adobe Root CA“ und alle von ihr ausgestellten Zertifikate aus

**F. Es gab eine frühere Mitteilung von Adobe über den Ablauf von Zertifikaten und dessen Auswirkungen auf die Verwendung/das Öffnen von PDF-Dokumenten. Sollte diese Mitteilung ignoriert werden?**

A. Nach der Neubewertung der Situation können wir davon ausgehen, dass alle PDF-Dokumente, die mit Produktionszertifikaten erweitert wurden, die von der alten „Adobe Root CA“ vor dem 7. Januar 2023 ausgestellt wurden, auch nach dem 7. Januar 2023 unverändert funktionieren. Wenn Sie Ihre PDF-Dokumente bereits aktualisiert haben, bleibt das Erlebnis das gleiche.

**F. An wen sollte ich mich wenden, wenn ich weitere Fragen habe?**

A. Sie können sich an den [Adobe-Support](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=de#support) wenden oder ein Support-Ticket erstellen.

**F. Was passiert, wenn ich mein Zertifikat nicht vor dem 7. Januar 2023 aktualisiere?**

A. Alle PDF-Dokumente, die mit Produktionszertifikaten erweitert wurden, welche von der alten „Adobe Root CA“ vor dem 7. Januar 2023 ausgestellt wurden, funktionieren auch nach dem 7. Januar 2023 unverändert. Mit Bewertungszertifikaten erweiterte PDFs werden nach dem Ablaufdatum nicht mehr funktionieren.

**F. Unterscheidet sich die Beschreibung neuer Zertifikate von alten Zertifikaten?**

A. In der Beschreibung der neuen Acrobat Reader Extensions-Zertifikate wird **G3-P24** als Programmname genannt. In der Beschreibung älterer Zertifikate (Zertifikate auf der Grundlage von &quot;Adobe Root CA&quot;) **P24** wird als Programmname angegeben.

**F. Wie erhalte ich die neuesten Zertifikate?**

A. Alle berechtigten Forms-Kunden (mit aktiver Lizenz) können die neuen Zertifikate (Zertifikate, die auf „Adobe Root CA G2“ basieren) von der [Adobe-Lizenzierungs-Website](https://licensing.adobe.com/) herunterladen. Wenn Sie das Zertifikat auf der Adobe-Lizenzierungs-Website nicht finden können, wenden Sie sich an den [Adobe-Support](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=de#support) oder erstellen Sie ein Support-Ticket.

**F. Funktionieren meine PDF-Dokumente, die mit Zertifikaten erweitert wurden, welche von „Adobe Root CA“ (der alten Zertifizierungsstelle) ausgestellt wurden, auch nach dem 7. Januar 2023?**

A. Ja, alle PDF-Dokumente, die mit Produktionszertifikaten erweitert wurden, welche von der „Adobe Root CA“ (der alten Zertifizierungsstelle) vor dem 7. Januar 2023 ausgestellt wurden, funktionieren auch nach dem 7. Januar 2023 ohne Änderungen. PDF-Dokumente, die mit Bewertungszertifikaten erweitert wurden, funktionieren nach dem Ablaufdatum nicht mehr.

**F. Welche Version von Adobe Acrobat Reader ist erforderlich, um PDF-Dokumente, die mit Zertifikaten der „Adobe Root CA“ (der alten Zertifizierungsstelle) erweitert wurden, weiterhin verwenden zu können?**

A. Adobe Acrobat Reader 2020 oder höher ist erforderlich, um PDF-Dokumente zu verwenden, die mit „Adobe Root CA“ (der alten Zertifizierungsstelle) erweitert wurden. Dies ist die unterstützte Version von Acrobat Reader zum Zeitpunkt der Veröffentlichung dieses Dokuments. Wenn Sie eine [nicht unterstützte Version von Adobe Acrobat](https://helpx.adobe.com/de/support/programs/eol-matrix.html) verwenden, empfiehlt Adobe, dass Sie [die neueste Version von Adobe Acrobat Reader herunterladen und installieren](https://get.adobe.com/de/reader/).

**F. Welche Version von Adobe Acrobat Reader ist erforderlich, um weiterhin PDF-Dokumente, die mit Zertifikaten von „Adobe Root CA 2“ (der neuen Zertifizierungsstelle) erweitert wurden, weiterhin verwenden zu können?**

A. Adobe Acrobat Reader 2020 oder höher ist erforderlich, um PDF-Dokumente zu verwenden, die mit „Adobe Root CA 2“ (der neuen Zertifizierungsstelle) erweitert wurden. Wenn Sie eine [nicht unterstützte Version von Adobe Acrobat Reader](https://helpx.adobe.com/de/support/programs/eol-matrix.html) verwenden, empfiehlt Adobe, dass Sie [die neueste Version von Adobe Acrobat Reader herunterladen und installieren](https://get.adobe.com/de/reader/).

**F. Kann ich ein altes Acrobat Reader Extensions-Zertifikat löschen und ein neues auf einem Adobe Experience Manager Forms Server hinzufügen, während ich den bestehenden Alias weiter verwende?**

A. Ja, Sie können ein altes Acrobat Reader Extensions-Zertifikat löschen und ein neues mit dem bestehenden Alias zu einem Adobe Experience Manager Forms-Server hinzufügen.

**F. Kann ich sowohl neue als auch alte Acrobat Reader Extensions-Zertifikate auf einem Adobe Experience Manager Forms-Server speichern?**

A. Ja, Sie können beide Zertifikate mit unterschiedlichen Aliasnamen auf einem Adobe Experience Manager Forms-Server speichern. Nach dem 7. Januar 2023 können Sie nur noch das neue Zertifikat verwenden, um die Reader Extension auf ein PDF-Dokument anzuwenden.

**F. Kann ich dasselbe Acrobat Reader Extensions-Zertifikat in alle Adobe Experience Manager Forms-Umgebungen importieren?**

A. Ja, dasselbe Acrobat Reader Extensions-Zertifikat kann in mehreren Umgebungen verwendet werden.

**F. Wie kann ich die auf ein PDF-Dokument angewendeten Verwendungsrechte überprüfen?**

A. Sie können die [getDocumentUsageRights](https://experienceleague.adobe.com/docs/experience-manager-65/forms/developer-reference/programming-aem-forms-jee/java-api-quick-start-code-examples/acrobat-reader-dc-extensions-service.html?lang=de#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)-API zum Abrufen der Informationen zu den auf ein PDF-Dokument angewendeten Nutzungsrechten verwenden.

**F. Wie ändere ich das Kennwort einer Acrobat Reader Extensions-Zertifikatdatei?**

A. Um unter Microsoft Windows das Zertifikatkennwort zu ändern, installieren Sie das Zertifikat mithilfe der Microsoft Management Console (MMC) und wählen Sie **Schlüssel als exportierbar markieren** aus. Exportieren Sie nach der Installation das Zertifikat mit einem privaten Schlüssel und verwenden Sie ein anderes Kennwort für die PFX-Datei.


<!-- 
## Applying the certificates {#obtaning-and-applying-the-certificates} 

You can choose one of the following paths to apply latest certificates:

* [Updating certificates for an AEM Forms on JEE environment](#Updating-and-Applying-certificates-for-an-AEM-Forms-on-JEE-environment) 
* [Updating certificates for an AEM Forms on OSGi environment](#Updating-and-applying-certificates-for-an-AEM-Forms-on-OSGi-environment)

>[!NOTE]
>
>The document uses the term certificates and credentials interchangeably.

### Pre-requisites {#Pre-requisites}

Updating the certificates requires using actions available on AEM Forms administrator console and Reader Extension APIs provided by AEM Forms. The document is intended for users and administrators with knowledge of using Adobe Experience Manger Forms APIs. Before you start, ensure that: 

* the user has administrator rights on underlying AEM Forms environment. 
* the user has setup the [development environment](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/howto-projects-eclipse.html) and has access to it.
* [obtain the certificates](#obtain-the-certificates).


### Obtain the certificates {#obtain-the-certificates}

The Rights credential is delivered as a digital certificate that contains the public key, the private key, and the password used to access the credential.

If your organization purchases a production version of Reader Extensions, the production Rights credential is delivered by Adobe Licensing Website (LWS). A production Rights credential is unique to your organization and can enable the specific usage rights that you require.

If you obtained Reader Extensions through a partner or software provider who integrated Reader Extensions into their software, the Rights credential is provided to you by that partner who, in turn, receives this credential from Adobe.

>[!NOTE]
>
>The Rights credential cannot be used for typical document signing or assertion of identity. For these applications, you can use a self-sign certificate or acquire an identity certificate from a Certificate Authority (CA).

The following types of Rights credentials are available:

**Customer Evaluation**: A credential with a short validity period that is provided to customers who want to evaluate Reader Extensions. Usage rights applied to documents using this credential expire when the credential expires. This type of credential is valid only for two to three months.

**Production**: A credential with a long validity period that is provided to customers who purchased the full product. Production credentials are unique to each customer but can be installed on multiple systems.

If you have already used certificates to reader extend PDF files, download a production certificate from [Adobe Licensing Website (LWS)](https://licensing.adobe.com/).

### Applying certificates for an AEM Forms on JEE environment {#Updating-and-Applying-certificates-for-an-AEM-Forms-on-JEE-environment} 

Applying new certificates on AEM Forms on JEE stack requires importing new credentials and applying usage rights. You can use admin console to import credentials and AEM Forms Reader Extension APIs to apply usage rights. 

#### Import and configure credentials 

You can use the Trust Store Management pages to import a new credential. The Trust Store may contain more than one Reader Extensions credential. Designate one of those credentials as the default Reader Extensions credential. The default credential is used when a Workbench user is unable to determine which credential to use during process creation. These rules apply to default credentials:

* If you import a Reader Extensions credential and the Trust Store contains no other Reader Extensions credentials, it is set as the default.
* If you import a Reader Extensions credential with the Default option selected, the default type is removed from an existing default credential. The imported credential becomes the default.
* You cannot delete a default Reader Extensions credential. To delete the default credential, first set another credential as the default. An exception to this rule is that if there is only one credential, you can delete it even though it is the default.
* You cannot update a default Reader Extensions credential.

To import the credentials: 

1. In administration console, click Settings > Trust Store Management > Local Credentials.
1. Click Import and, under Trust Store Type, select Acrobat Reader DC extensions Credential.
1. (Optional) To indicate that this credential is the default credential to use with Acrobat Reader DC extensions, select Default.
1. In the Alias box, type an identifier for the credential. This identifier is used as the display name for the credential in Acrobat Reader DC extensions. This alias is also used to access the credential programmatically using the AEM forms SDK.
1. Click Choose File to locate the credential, type the password of the credential, and then click OK.

If the error message "Failed to import credential due to either incorrect file format, or incorrect password" appears, verify that the password is valid.

You can also import and delete credentials programmatically. (See [Programming with AEM forms](../../developing/credentials.md).)

<!-- ### Remove usage rights from existing rights-enabled PDF documents

Remove usage rights from existing rights-enabled PDF documents before applying usage rights with latest credentials. AEM Forms on JEE provides APIs to remove usage rights. For detailed instructions, see [Removing Usage Rights from PDF Documents](../../developing/assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).

To remove usage rights for AEM Forms on JEE processes developed in Workbench, see [Workbench Help](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/WorkbenchHelp.pdf). 

#### Apply the usage rights to PDF documents 

After importing new credentials, you can apply usage rights to PDF documents using the Acrobat Reader DC extensions Java Client API and web service.  For details, see [Applying Usage Rights to PDF Documents](../../developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents). 


### Applying certificates for an AEM Forms on OSGi environment {#Updating-and-applying-certificates-for-an-AEM-Forms-on-OSGi-environment}

Applying new certificates on AEM Forms on OSGi stack requires importing new credentials and applying usage rights. You can use admin console to import credentials and AEM Forms Reader Extension APIs to apply usage rights. 

#### Import credentials {#Import-credentials}

In an AEM Forms on OSGi environment, a Reader Extension credential is associated with fd-service user. Before adding credentials for fd-user key store, perform the following steps to create a key store: 

1. Log in to your AEM Author instance as an Administrator.
1. Go to **[!UICONTROL Tools]**> **[!UICONTROL Security]**>**[!UICONTROL Users]**.
1. Scroll down the list of users until you find fd-service user account.
1. Click **[!UICONTROL fd-service]** user.
1. Click keystore tab.
1. Click **[!UICONTROL Create KeyStore]**.
1. Set the KeyStore Access Password and save your settings to create the KeyStore password.

After creating the key-store, add credentials to fd-service user. The following video explains the steps: 

>[!VIDEO](https://images-tv.adobe.com/mpcv3/5577/8db8e554-f04b-4fae-8108-b9b5e0eb03ad_1627925794.854x480at800_h264.mp4)

The following command list the details of the pfx file. Before running the command, navigate to the directory that contains the .pfx file.

`keytool -v -list -storetype pkcs12 -keystore [name of your .pfx file]`

For example, keytool -v -list -storetype pkcs12 -keystore 1005566.pfx where 1005566.pfx is the name of my pfx file

<!-- ### Remove usage rights from existing rights-enabled PDF documents

Remove usage rights from existing rights-enabled PDF documents before applying usage rights with latest credentials. You can remove the usage rights for a document by invoking the removeUsageRights API from within the docAssuranceServiceAPI. For detailed information, see [Remove Usage Rights](/help/forms/using/aem-document-services-programmatically.md#removing-usage-rights) document.

#### Apply the usage rights to PDF documents 

To apply usage rights in an AEM Forms on OSGi environment, Create custom OSGi service to usage rights to the documents. You can also create a servlet with a POST method to return the reader extended PDF to the user. For detailed instructions, see [Applying Reader Extensions](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/document-services/apply-reader-extension-rights-to-pdf.html).  -->
