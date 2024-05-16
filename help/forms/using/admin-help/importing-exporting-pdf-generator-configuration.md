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
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '372'
ht-degree: 100%

---

# Importieren und Exportieren der PDF Generator-Konfigurationsdateien {#importing-and-exporting-pdf-generator-configuration-files}

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
