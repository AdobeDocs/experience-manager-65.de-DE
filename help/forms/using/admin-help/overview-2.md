---
title: Grundlagen zum Verwalten von Zertifikaten und Anmeldeinformationen
description: Erfahren Sie mehr über die Grundlagen des Verwaltens von Zertifikaten und Berechtigungen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 74bf0e77-f47b-475a-b2a7-52cfb3baaa22
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '301'
ht-degree: 100%

---

# Grundlagen zum Verwalten von Zertifikaten und Anmeldeinformationen {#basics-of-managing-certificates-and-credentials}

Eine *Berechtigung* enthält Informationen zu Ihrem privaten Schlüssel, der zum Signieren bzw. Identifizieren von Dokumenten benötigt wird. Ein *Zertifikat* enthält Informationen zum öffentlichen Schlüssel, den Sie für die Trust Store-Verwaltung konfigurieren. AEM Forms verwendet Zertifikate und Berechtigungen für mehrere Zwecke:

* Acrobat Reader DC Extensions verwendet Anmeldeinformationen zur Aktivierung von Adobe Reader-Verwendungsrechten in PDF-Dokumenten. (Siehe [Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC-Erweiterungen](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).)
* Sie können Rights Management konfigurieren, um nur Berechtigungen vertrauenswürdiger Herausgeberinnen und Herausgeber für die Verwendung in Acrobat anzuzeigen.  (Siehe [Konfigurieren der Anzeigeeinstellungen für Rights Management](/help/forms/using/admin-help/configuring-client-server-options.md#configure-document-security-display-settings).)  Der CN (Common Name) muss im Zertifikat vorhanden sein.
* Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu.  Weitere Informationen zum Signature-Dienst finden Sie in der [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_65_de).

**Generieren eines Schlüsselpaars**

AEM Forms verwendet den Trust Store zum Speichern und Verwalten von Zertifikaten, Berechtigungen und Zertifikatssperrlisten (CRLs).  Zusätzlich können Sie ein unabhängiges HSM-Gerät (Hardware-Sicherheitsmodul) zum Speichern privater Schlüssel verwenden.

AEM Forms bietet keine Möglichkeit, ein Schlüsselpaar zu generieren. Sie können jedoch eines mithilfe von Werkzeugen wie dem Java-Keytool generieren und in den Trust Store von AEM Forms importieren.  Weitere Informationen zum Java-Keytool finden Sie hier:

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

**Vorgehen bei verlorenem oder kompromittiertem Schlüssel**

Wenn Sie vermuten, dass Ihr Schlüssel verloren gegangen ist oder kompromittiert wurde, gehen Sie wie folgt vor:

1. Informieren Sie die Zertifizierungsstelle, damit der kompromittierte Schlüssel auf die Zertifikatssperrliste gesetzt und gesperrt wird.
1. Beziehen Sie von der Zertifizierungsstelle einen neuen Schlüssel und das zugehörige Zertifikat.
1. Signieren Sie die Dokumente, die mit dem kompromittierten Schlüssel signiert wurden, mit dem neuen Schlüssel erneut.
