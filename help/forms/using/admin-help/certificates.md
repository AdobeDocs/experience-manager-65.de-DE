---
title: Zertifikate verwalten
seo-title: Zertifikate verwalten
description: Erfahren Sie, wie Sie ein Zertifikat exportieren und importieren und seine Vertrauenseinstellungen bearbeiten.
seo-description: Erfahren Sie, wie Sie ein Zertifikat exportieren und importieren und seine Vertrauenseinstellungen bearbeiten.
uuid: 46b1dbe5-517c-4294-bb52-cc6700a768e8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9fd531c0-5206-4be0-a450-13e0dc806068
exl-id: 1fe0e7b4-6109-4f7a-8858-8237a1c5c93b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 83%

---

# Zertifikate verwalten {#managing-certificates}

Mithilfe der Trust Store-Verwaltung können Sie Zertifikate importieren, bearbeiten und löschen, die Sie auf dem Server zur Überprüfung digitaler Signaturen und zur Zertifikatauthentifizierung als vertrauenswürdig einstufen. Sie können eine beliebige Anzahl von Zertifikaten im- und exportieren. Nachdem ein Zertifikat importiert wurde, können die Vertrauenseinstellungen und der Trust Store-Typ bearbeitet werden. Verwenden Sie beim Kombinieren von Trust Store-Typen die folgenden Optionen:

* **Trust für Zertifikatauthentifizierung mit CA:** Wählen Sie für die Prüfung der Zertifikatsperrliste auch die Option „Trust für Identität“.
* **Trust für Zertifikatauthentifizierung mit ICA:** Wählen Sie nur die Option „Trust für Identität“. Eine ICA sollte für die Zertifikatauthentifizierung nicht als vertrauenswürdig eingestuft werden. Stufen Sie die ICA für die Zertifikatauthentifizierung als vertrauenswürdig ein, wird die ICA eine Zertifizierungsstelle für die Pfaderzeugung. Stufen Sie die ICA sowohl für die Zertifikatauthentifizierung als auch für die Identität als vertrauenswürdig ein, wird das Herstellerzertifikat der Zertifizierungsstelle ignoriert, da die ICA zur Zertifizierungsstelle wird.
* **Trust für Online-Zertifikatstatusprotokoll-Server (OCSP) mit HTTPs:** Wenn sich der beim OCSP-Responder anfragende Server an einem HTTPs-Speicherort befindet, müssen Sie auch „Trust für SSL-Verbindungen“ auswählen. Ist für die bei OCSP anfragende Partei die Prüfung der Zertifikatsperrliste erforderlich, muss darüber hinaus „Trust für Identität“ ausgewählt werden.
* **Adobe-Stammzertifikat:** Wählen Sie nicht die Trust Store-Typen für SSL-Verbindungen und OCSP-Server. Adobe-Stammzertifikaten wird für SSL-Verbindungen und OCSP-Server nicht vertraut. Adobe stellt keine OCSP- und SSL-Zertifikate aus. Einem Adobe-Stammzertifikat wird implizit mit einem Aliasnamen=„ADOBEROOT“ vertraut.

Nur X509v3-Zertifikate werden unterstützt. Dieser Zertifikattyp kann in einer binären DER-kodierten Datei (.cer-Datei) oder Textdatei bereitgestellt werden, die eine Base64-kodierte Version desselben DER-kodierten Zertifikats (einschließlich X509-Zertifikaten im PEM-Format) enthält.

Bei Zertifikaten, die zum Abschließen der Signaturüberprüfung erforderlich sind, müssen sich diese Dateien im selben Speicher (HSM oder Datenbank) befinden.

Sie können Zertifikate mit der Trust Manager-API auch importieren und löschen. Weitere Informationen finden Sie in den Kapiteln zum Importieren von Zertifikaten mit der Trust Manager-API und Löschen von Zertifikaten mit der Trust Manager-API unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63).

## Zertifikat importieren {#import-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf „Importieren“ und wählen Sie unter „TrustStore-Typ“ eine der folgenden Optionen:

   * **Trust für SSL-Verbindungen:** Gibt an, dass AEM Forms Zertifikate verwenden kann, um über SSL Verbindungen zu externen Systemen herzustellen.
   * **Trust für Signaturzertifizierung:** Gibt an, dass Zertifikaten bei Dokumentsignierungsvorgängen für die Zertifizierung autorbezogener digitaler Signaturen vertraut wird.
   * **Trust für Signatur:** Gibt an, dass Zertifikaten bei Dokumentsignierungsvorgängen für die Zertifizierung nicht autorbezogener digitaler Signaturen vertraut wird.
   * **Trust für Zertifikatauthentifizierung:** Gibt an, dass AEM Forms Zertifikate zum Authentifizieren von Benutzern mit Zertifikat- oder Smartcard-Authentifizierung verwendet.
   * **Trust für Online-Zertifikatstatusprotokoll-Server (OCSP):** Gibt an, dass AEM Forms Zertifikate verwenden kann, um Verbindungen zu externen OCSP-Respondern herzustellen.
   * **Trust für Identität:** Dieser Trust Store-Typ gibt an, dass Zertifikate verwendet werden können, um von den zuvor genannten Typen abweichenden Informationen zu vertrauen.

   >[!NOTE]
   >
   >Der Trust Store vertraut implizit einen Adobe-Stammzertifikat bei der Zertifikatauthentifizierung, der Signatur, dem Prüfen der Signatur und der Identität.

1. Geben Sie in das Feld „Alias“ den Bezeichner für das Zertifikat ein.
1. Klicken Sie auf **[!UICONTROL Browse]**, um das Zertifikat zu suchen, und klicken Sie dann auf **[!UICONTROL OK]**.

## Zertifikat exportieren {#export-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf den Aliasnamen des Zertifikats, das exportiert werden soll. Die Seite **[!UICONTROL Zertifikatdetails]** wird angezeigt.
1. Klicken Sie auf **[!UICONTROL Export]**, befolgen Sie die Anweisungen zum Exportieren des Zertifikats und klicken Sie dann auf **[!UICONTROL OK]**.

## Trust-Einstellungen und Trust Store-Typ eines Zertifikats bearbeiten {#edit-a-certificate-s-trust-settings-and-trust-store-type}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf den Aliasnamen des Zertifikats, das bearbeitet werden soll.
1. Klicken Sie auf **[!UICONTROL Zertifikat aktualisieren]**.
1. Geben Sie einen neuen Namen in das Feld „Alias“ ein, um den Aliasnamen des Zertifikats zu ändern.
1. Um den Trust Store-Typ für das Zertifikat zu aktualisieren, wählen Sie den geeigneten Trust Store-Typ aus.
1. Um die Richtlinienbeschränkungen zu aktualisieren, geben Sie im Feld &quot;Certificate Policies&quot;die Richtlinieninformationen ein und klicken Sie auf **[!UICONTROL OK]**.

## Zertifikat löschen {#delete-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Aktivieren Sie die Kontrollkästchen der zu löschenden Zertifikate, klicken Sie auf **[!UICONTROL Löschen]** und dann auf **[!UICONTROL OK]**.
