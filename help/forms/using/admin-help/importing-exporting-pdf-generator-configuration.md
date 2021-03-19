---
title: PDF Generator-Konfigurationsdateien importieren und exportieren
seo-title: PDF Generator-Konfigurationsdateien importieren und exportieren
description: Erfahren Sie, wie Sie PDF Generator-Konfigurationsdateien importieren und exportieren.
seo-description: Erfahren Sie, wie Sie PDF Generator-Konfigurationsdateien importieren und exportieren.
uuid: 3367253b-d222-4c5f-9455-a1810d96112e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e25c1b35-73eb-4353-8e39-a2d4cdccd101
feature: PDF Generator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 98%

---


# PDF Generator-Konfigurationsdateien importieren und exportieren {#importing-and-exporting-pdf-generator-configuration-files}

Die Konfigurationsdatei enthält die PDF Generator-Konvertierungsinformationen, einschließlich der PDF-, Dateityp- und Sicherheitseinstellungen.

>[!NOTE]
>
>Sie können die Zeitlimiteinstellung für PDF Generator nicht durch Importieren einer benutzerdefinierten Datei „native2pdfconfig.xml“ ändern. Die Zeitlimiteinstellung in dieser Datei dient nur zu Informationszwecken und zeigt die aktuelle Einstellung in PDF Generator an. Informationen zum Ändern der Zeitlimiteinstellung finden Sie unter „Festlegen von Leistungsparametern für überwachte Ordner in PDF Generator“ unter [deInstallieren und Bereitstellen von AEM Forms](https://www.adobe.com/go/learn_aemforms_installJBoss_63).

## Eine aktuelle Konfigurationsdatei exportieren {#export-your-current-configuration-file}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration exportieren“.
1. Wählen Sie zum Exportieren von Einstellungen die passende Option aus:

   * Um alle benannten Einstellungen zu exportieren, wählen Sie „Gesamte Konfiguration herunterladen“ aus.
   * Um nur eine Adobe PDF-, Sicherheits- oder Dateitypeinstellung zu exportieren, wählen Sie „Mindestkonfiguration herunterladen“ aus.

      Wählen Sie beim Exportieren einer Mindestkonfiguration die zu exportierenden Adobe PDF-, Sicherheits- und Dateitypeinstellungen aus.

1. Klicken Sie auf „Herunterladen“ und speichern Sie die XML-Datei am gewünschten Speicherort.

## Eine Konfigurationsdatei importieren  {#import-a-configuration-file}

>[!NOTE]
>
>Ihr System wird basierend auf den Informationen in der importierten Datei neu konfiguriert.

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration exportieren“.
1. Wählen Sie „Vorhandene Konfigurationsdatei importieren“ aus.
1. Um den Dateispeicherort im Feld „Konfigurationsdatei“ anzugeben, klicken Sie zuerst auf „Durchsuchen“, um die Datei zu lokalisieren und auszuwählen, und dann auf **Importieren**.

## Alle Ebenen in der AutoCAD-Datei konvertieren  {#convert-all-layers-within-autocad-files}

Standardmäßig konvertiert PDF Generator nicht alle in AutoCAD-Dateien enthaltenen Ebenen, sondern nur die Standardebene der Datei in PDF. Um alle Ebenen zu konvertieren, führen Sie folgendes Verfahren aus.

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration exportieren“.
1. Wählen Sie „Gesamte Konfiguration herunterladen“ aus und klicken Sie auf „Herunterladen“.
1. Öffnen Sie die heruntergeladene Datei in einem Texteditor und fügen Sie unterhalb des Tags `AutoCAD`, aber innerhalb des Tags `PDFMaker` den Text `convertAllPages="true"` &quot; hinzu.
1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration exportieren“.
1. Wählen Sie „Vorhandene Konfigurationsdatei importieren“ aus, geben Sie die aktualisierte Datei an und klicken Sie auf „Importieren“.

   Bei allen AutoCAD-Dateien, die mit der geänderten Konfigurationsdatei konvertiert werden, werden alle Ebenen konvertiert.

## Konfiguration auf die ursprünglichen, mit PDF Generator installierten Einstellungen zurücksetzen  {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Konfigurationsdateien“ > „Konfiguration exportieren“.
1. Wählen Sie „Konfiguration auf Standardeinstellungen zurücksetzen“ und klicken Sie auf „Importieren“.

