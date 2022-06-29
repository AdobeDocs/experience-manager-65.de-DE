---
title: Grundlagen zum Verwalten von Zertifikaten und Berechtigungen
seo-title: Basics of managing certificates and credentials
description: Erfahren Sie mehr über die Grundlagen des Verwaltens von Zertifikaten und Berechtigungen.
seo-description: Learn about the basics of managing certificates and credentials.
uuid: f421e206-e7b5-416c-b9fb-974094f10a66
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 986d16fc-4c81-4785-b1f3-fe8bd7ff669e
exl-id: 74bf0e77-f47b-475a-b2a7-52cfb3baaa22
source-git-commit: 0c7dba43dad8608b4a5de271e1e44942c950fb16
workflow-type: ht
source-wordcount: '339'
ht-degree: 100%

---

# Grundlagen zum Verwalten von Zertifikaten und Berechtigungen {#basics-of-managing-certificates-and-credentials}

Eine *Berechtigung* enthält Informationen zu Ihrem privaten Schlüssel, der zum Signieren bzw. Identifizieren von Dokumenten benötigt wird. Ein *Zertifikat* enthält Informationen zum öffentlichen Schlüssel, den Sie für die Trust Store-Verwaltung konfigurieren. AEM Forms verwendet Zertifikate und Berechtigungen für mehrere Zwecke:

* Acrobat Reader DC Extensions verwendet eine Berechtigung zur Aktivierung von Adobe Reader-Verwendungsrechten in PDF-Dokumenten. (Siehe [Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).)
* Sie können Rights Management konfigurieren, um nur Berechtigungen vertrauenswürdiger Herausgeber für die Verwendung in Acrobat anzuzeigen. (Siehe [Anzeigeeinstellungen für Rights Management konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configure-document-security-display-settings).) Der CN (Common Name) muss im Zertifikat vorhanden sein.
* Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu. Weitere Informationen zum Signature-Dienst finden Sie unter [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_65_de).

**Generieren eines Schlüsselpaars**

AEM Forms verwendet Trust Store zur Speicherung und Verwaltung von Zertifikaten, Berechtigungen und Zertifikatsperrlisten (CRLs). Zusätzlich können Sie ein unabhängiges HSM-Gerät (Hardware Security Module, Hardwaresicherheitsmodul) zum Speichern privater Schlüssel verwenden.

AEM Forms bietet keine Möglichkeit, ein Schlüsselpaar zu generieren. Sie können ein Schlüsselpaar jedoch mithilfe der Werkzeuge, wie Java-Keytool, generieren und in AEM- Trust Store importieren. Weitere Informationen zu Java-Keytool finden Sie hier:

[https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html](https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html)

[https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html](https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html)

[https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL](https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL)

Folgende Signaturtypen werden unterstützt und können in AEM Forms importiert werden:

* XML-Signatur
* XMLTimeStampToken
* RFC 3161 TimeStampToken
* PKCS#7
* PKCS#1
* DSA-Signaturen

**Vorgehen bei verlorenem oder beschädigtem Schlüssel**

Wenn Sie vermuten, dass Ihr Schlüssel verloren gegangen ist oder beschädigt wurde, gehen Sie wie folgt vor:

1. Informieren Sie die Zertifizierungsstelle, damit der beschädigte Schlüssel auf die Zertifikatsperrliste gesetzt und gesperrt wird.
1. Beziehen Sie von der Zertifizierungsstelle einen neuen Schlüssel und das zugehörige Zertifikat.
1. Signieren Sie die Dokumente, die mit dem beschädigten Schlüssel signiert wurden, erneut mit dem neuen Schlüssel.
