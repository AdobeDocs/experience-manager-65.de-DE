---
title: Importieren und Exportieren der PDF Generator-Konfigurationsdateien
description: Erfahren Sie, wie Sie PDF Generator-Konfigurationsdateien importieren und exportieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: b363b23a-29bb-4ea4-a8f2-5ba9fe3c7b27
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
source-wordcount: '390'
ht-degree: 100%
---
# Importieren und Exportieren der PDF Generator-Konfigurationsdateien {#importing-and-exporting-pdf-generator-configuration-files}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Die Konfigurationsdatei enthält die PDF Generator-Konvertierungsinformationen, einschließlich der PDF-, Dateityp- und Sicherheitseinstellungen.

>[!NOTE]
>
>Sie können die Zeitlimiteinstellung für PDF Generator nicht durch Importieren einer benutzerdefinierten Datei „native2pdfconfig.xml“ ändern. Die Zeitlimiteinstellung in dieser Datei dient nur zu Informationszwecken und zeigt die aktuelle Einstellung in PDF Generator an. Informationen zum Ändern der Zeitlimiteinstellung finden Sie unter „Festlegen von Leistungsparametern in PDF Generator“ unter [Installieren und Bereitstellen von AEM Forms](https://www.adobe.com/go/learn_aemforms_installJBoss_63_de).

## Exportieren der aktuellen Konfigurationsdatei {#export-your-current-configuration-file}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration exportieren“.
1. Um die Einstellungen zu exportieren, wählen Sie die passende Option aus:

   * Um alle benannten Einstellungen zu exportieren, wählen Sie „Gesamte Konfiguration herunterladen“ aus.
   * Um nur eine Adobe PDF-, Sicherheits- oder Dateitypeinstellung zu exportieren, wählen Sie „Mindestkonfiguration herunterladen“ aus.

     Wählen Sie beim Exportieren einer Mindestkonfiguration die zu exportierenden Adobe PDF-, Sicherheits- und Dateitypeinstellungen aus.

1. Klicken Sie auf „Herunterladen“ und speichern Sie die XML-Datei am gewünschten Speicherort.

## Importieren einer Konfigurationsdatei {#import-a-configuration-file}

>[!NOTE]
>
>Ihr System wird basierend auf den Informationen in der importierten Datei neu konfiguriert.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration importieren“.
1. Wählen Sie „Vorhandene Konfigurationsdatei importieren“ aus.
1. Um den Dateispeicherort im Feld „Konfigurationsdatei“ anzugeben, klicken Sie zuerst auf „Durchsuchen“, um die Datei zu lokalisieren und auszuwählen, und dann auf **Importieren**.

## Konvertieren aller Ebenen in AutoCAD-Dateien {#convert-all-layers-within-autocad-files}

Standardmäßig konvertiert PDF Generator nicht alle in AutoCAD-Dateien enthaltenen Ebenen in das PDF-Format, sondern nur die Standardebene der Datei. Gehen Sie wie folgt vor, um alle Ebenen zu konvertieren:

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration exportieren“.
1. Wählen Sie „Gesamte Konfiguration herunterladen“ aus und klicken Sie auf „Herunterladen“.
1. Öffnen Sie die heruntergeladene Datei in einem Texteditor und fügen Sie unterhalb des Tags `AutoCAD`, aber innerhalb des Tags `PDFMaker` den Text `convertAllPages="true"` hinzu.
1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration importieren“.
1. Wählen Sie „Vorhandene Konfigurationsdatei importieren“ aus, geben Sie die aktualisierte Datei an und klicken Sie auf „Importieren“.

   Bei allen AutoCAD-Dateien, die mit der geänderten Konfigurationsdatei konvertiert werden, werden alle Ebenen konvertiert.

## Zurücksetzen der Konfiguration auf die ursprünglichen, mit PDF Generator installierten Einstellungen {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration importieren“.
1. Wählen Sie „Konfiguration auf Standardeinstellungen zurücksetzen“ aus und klicken Sie auf „Importieren“.
