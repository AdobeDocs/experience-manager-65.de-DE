---
title: Verwalten von Zertifikaten
description: Erfahren Sie, wie Sie ein Zertifikat exportieren und importieren und die zugehörigen Vertrauenseinstellungen bearbeiten.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1fe0e7b4-6109-4f7a-8858-8237a1c5c93b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 100%
---
# Verwalten von Zertifikaten {#managing-certificates}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Mithilfe der Trust Store-Verwaltung können Sie Zertifikate importieren, bearbeiten und löschen, die Sie auf dem Server zur Überprüfung digitaler Signaturen und zur Zertifikatauthentifizierung als vertrauenswürdig einstufen. Sie können eine beliebige Anzahl von Zertifikaten importieren und exportieren. Nachdem ein Zertifikat importiert wurde, können Sie die Vertrauenseinstellungen und den Trust Store-Typ bearbeiten. Ziehen Sie beim Kombinieren von Trust Store-Typen die folgenden Optionen in Erwägung:

* **Trust für Zertifikatauthentifizierung mit CA:** Wählen Sie für die Prüfung der Zertifikatsperrliste auch die Option „Trust für Identität“.
* **Trust für Zertifikatauthentifizierung mit ICA:** Wählen Sie nur die Option „Trust für Identität“. Eine ICA sollte für die Zertifikatauthentifizierung nicht als vertrauenswürdig eingestuft werden. Wenn Sie die ICA für die Zertifikatauthentifizierung als vertrauenswürdig einstufen, wird die ICA eine Zertifizierungsstelle für die Pfaderzeugung. Wenn die ICA sowohl für die Zertifikatauthentifizierung als auch für die Identität als vertrauenswürdig eingestuft wird, wird das Herstellerzertifikat der Zertifizierungsstelle ignoriert, da die ICA zur Zertifizierungsstelle wird.
* **Trust für Online-Zertifikatstatusprotokoll-Server (OCSP) mit HTTPs:** Wenn sich der beim OCSP-Responder anfragende Server an einem HTTPs-Speicherort befindet, müssen Sie auch „Trust für SSL-Verbindungen“ auswählen. Ist für die bei OCSP anfragende Partei die Prüfung der Zertifikatsperrliste erforderlich, muss darüber hinaus „Trust für Identität“ ausgewählt werden.
* **Adobe-Stammzertifikat:** Wählen Sie nicht die Trust Store-Typen für SSL-Verbindungen und OCSP-Server. Den Adobe-Stammzertifikaten wird für SSL-Verbindungen und OCSP-Server nicht vertraut. Adobe stellt keine OCSP- und SSL-Zertifikate aus. Einem Adobe-Stammzertifikat wird implizit mit dem Aliasnamen „ADOBEROOT“ vertraut.

Es werden nur X509v3-Zertifikate unterstützt. Dieser Zertifikattyp kann in einer binären DER-kodierten Datei (.cer-Datei) oder Textdatei bereitgestellt werden, die eine Base64-kodierte Version desselben DER-kodierten Zertifikats (einschließlich X509-Zertifikaten im PEM(Privacy Enhanced Mail)-Format) enthält.

Zertifikate, die zum Abschließen der Signaturüberprüfung erforderlich sind, müssen sich im selben Speicher (HSM oder Datenbank) befinden.

Sie können Zertifikate mit der Trust Manager-API auch importieren und löschen. Einzelheiten finden Sie unter „Importieren von Zertifikaten mit der Trust Manager-API“ und „Löschen von Zertifikaten mit der Trust Manager-API“ in [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).

## Importieren eines Zertifikats {#import-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf „Importieren“ und wählen Sie unter „Trust Store-Typ“ eine der folgenden Optionen:

   * **Trust für SSL-Verbindungen:** Gibt an, dass AEM Forms Zertifikate verwenden kann, um über SSL Verbindungen zu externen Systemen herzustellen.
   * **Trust für Signaturzertifizierung:** Gibt an, dass Zertifikaten bei Dokumentsignierungsvorgängen für die Zertifizierung autorbezogener digitaler Signaturen vertraut wird.
   * **Trust für Signatur:** Gibt an, dass Zertifikaten bei Dokumentsignierungsvorgängen für die Zertifizierung nicht autorbezogener digitaler Signaturen vertraut wird.
   * **Trust für Zertifikatauthentifizierung:** Gibt an, dass AEM Forms Zertifikate zum Authentifizieren von Benutzern mit Zertifikat- oder Smart-Card-Authentifizierung verwendet.
   * **Trust für Online-Zertifikatstatusprotokoll-Server (OCSP):** Gibt an, dass AEM Forms Zertifikate verwenden kann, um Verbindungen zu externen OCSP-Respondern herzustellen.
   * **Trust für Identität:** Dieser Trust Store-Typ gibt an, dass Zertifikate verwendet werden können, um von den zuvor genannten Typen abweichenden Informationen zu vertrauen.

   >[!NOTE]
   >
   >Der Trust Store vertraut implizit einem Adobe-Stammzertifikat bei der Zertifikatauthentifizierung, der Signatur, dem Zertifizieren der Signatur und der Identität.

1. Geben Sie in das Feld „Alias“ den Bezeichner für das Zertifikat ein.
1. Klicken Sie auf **[!UICONTROL Durchsuchen]**, um das Zertifikat zu finden, und anschließend auf **[!UICONTROL OK]**.

## Zertifikat exportieren {#export-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf den Aliasnamen des Zertifikats, das exportiert werden soll. Die Seite **[!UICONTROL Zertifikatdetails]** wird angezeigt.
1. Klicken Sie auf **[!UICONTROL Exportieren]**, befolgen Sie die Anweisungen zum Exportieren des Zertifikats und klicken Sie anschließend auf **[!UICONTROL OK]**.

## Trust-Einstellungen und Trust Store-Typ eines Zertifikats bearbeiten {#edit-a-certificate-s-trust-settings-and-trust-store-type}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Zertifikate]**.
1. Klicken Sie auf den Aliasnamen des Zertifikats, das bearbeitet werden soll.
1. Klicken Sie auf **[!UICONTROL Zertifikat aktualisieren]**.
1. Geben Sie einen neuen Namen in das Feld „Alias“ ein, um den Aliasnamen des Zertifikats zu ändern.
1. Um den TrustStore-Typ für das Zertifikat zu aktualisieren, wählen Sie den entsprechenden TrustStore-Typ aus.
1. Um die Richtlinienbeschränkungen zu aktualisieren, geben Sie die Richtlinieninformationen in das Feld „Zertifikatrichtlinien“ ein und klicken Sie auf **[!UICONTROL OK]**.

## Zertifikat löschen {#delete-a-certificate}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Trust Store-Verwaltung > Berechtigungen]**.
1. Aktivieren Sie die Kontrollkästchen der zu löschenden Zertifikate und klicken Sie erst auf **[!UICONTROL Löschen]** und anschließend auf **[!UICONTROL OK]**.
