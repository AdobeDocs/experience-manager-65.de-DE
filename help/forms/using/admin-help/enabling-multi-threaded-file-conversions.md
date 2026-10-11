---
title: Dateikonvertierungen mit mehreren Threads aktivieren
description: Erfahren Sie, wie Sie mehrprozessgestützte Dateikonvertierungen aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: 402c1fd4-c6c8-494e-b452-b56a91c4a397
solution: Experience Manager, Experience Manager Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: b26425d0-6fde-5e02-bfd6-e560e2fa86c9
    internal-label: PDF Generator
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%
---
# Dateikonvertierungen mit mehreren Threads aktivieren {#enabling-multi-threaded-file-conversions}

PDF Generator kann mehrere Dateikonvertierungen gleichzeitig ausführen, um den Konvertierungsdurchsatz zu verbessern. Wählen Sie den entsprechenden Konvertierungsmodus:

| Konvertierungsmodus | Anwendungen, die gleichzeitige Konvertierungen unterstützen | Benutzerkontomodell |
|---|---|---|
| Mehrbenutzermodus | OpenOffice | Jede OpenOffice-Instanz wird von einem separaten Benutzerkonto ausgeführt. |
| Einzelbenutzermodus | Microsoft® Word und Microsoft® Excel | Ein Benutzerkonto führt mehrere Word- und Excel-Instanzen aus. PowerPoint-Konversionen bleiben serialisiert. |

Bevor Sie einen der Modi aktivieren, schließen Sie die Vorinstallationskonfiguration für [PDF Generator &#x200B;](/help/forms/using/install-configure-document-services.md#preinstallationconfigurations) die von Ihnen verwendeten Programme und Betriebssysteme ab. Unterstützte Anwendungsversionen finden Sie unter [Software-Support für PDF Generator](/help/forms/using/aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator).

## Mehrbenutzermodus {#multi-user-mode}

Im Mehrbenutzermodus startet PDF Generator jede OpenOffice-Instanz unter einem separaten Benutzerkonto. Konfigurieren Sie genügend gültige Administratorbenutzerkonten für die Anzahl der erforderlichen gleichzeitigen Konversionen. Konfigurieren Sie in einem Cluster auf jedem Knoten dieselben Konten.

Stellen Sie unter Windows sicher, dass die PDF Generator-Benutzer über die Berechtigung [Ersetzen eines Tokens auf Prozessebene](/help/forms/using/install-configure-document-services.md#grant-the-replace-a-process-level-token-privilege) verfügen, und schließen Sie die entsprechende Konfiguration der Benutzerkontensteuerung ab, die unter [Konfigurieren von Dokumentendiensten“ beschrieben &#x200B;](/help/forms/using/install-configure-document-services.md#disable-user-account-control-uac).

### OpenOffice-Konversionen {#openoffice-conversions}

Konfigurieren Sie für jede OpenOffice-Instanz, die gleichzeitig ausgeführt werden kann, ein PDF Generator-Benutzerkonto. Installieren Sie OpenOffice an einem Speicherort, auf den jeder konfigurierte Benutzer zugreifen kann, und schließen Sie die ersten OpenOffice-Aktivierungsdialoge für jeden Benutzer.

Bei UNIX-basierten Systemen müssen Sie die Anforderungen an die OpenOffice-Installation und die Benutzerberechtigungen in &quot;[&#x200B; von Dokumenten-Services“ &#x200B;](/help/forms/using/install-configure-document-services.md#preinstallationconfigurations).

## Einzelbenutzermodus unter Windows {#single-user-mode-on-windows}

Im Einzelbenutzermodus kann PDF Generator gleichzeitige Konvertierungen unter einem konfigurierten Benutzerkonto ausführen.

In diesem Modus werden mehrere Instanzen von Microsoft® Word (DOC und DOCX) und Excel (XLS und XLSX) unter demselben Benutzer ausgeführt. Microsoft® PowerPoint (PPT und PPTX) unterstützt nicht den Einzelbenutzermodus. PDF Generator startet jeweils nur eine PowerPoint-Instanz, sodass PowerPoint-Konversionen serialisiert werden.

So aktivieren Sie den Einzelbenutzermodus für Word- und Excel-Konvertierungen:

1. Navigieren Sie in der Administration-Console zu **Startseite > Dienste > Anwendungen und Dienste > Dienstverwaltung**.
1. Filtern Sie nach **PDF Generator** und wählen Sie **GeneratePDFService** aus.
1. Konfigurieren Sie auf **Registerkarte** Konfiguration“ die folgenden Optionen:

   * Setzen **Einzelbenutzermodus für PDFMaker aktivieren** auf **true**.
   * Legen Sie **PDFMaker Pool Size** auf die maximale Anzahl von Word-Instanzen fest, die Konvertierungen gleichzeitig ausführen können.
   * Legen Sie **Einzelbenutzermodus für Native2PDF aktivieren** auf **true** fest.
   * Legen Sie **native2PDF Pool Size** auf die maximale Anzahl von Excel-Instanzen fest, die Konversionen gleichzeitig ausführen können.

1. Starten Sie den AEM Forms-Server neu.
