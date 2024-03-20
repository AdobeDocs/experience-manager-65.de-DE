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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 14%

---

# Importieren und Exportieren der PDF Generator-Konfigurationsdateien {#importing-and-exporting-pdf-generator-configuration-files}

Die Konfigurationsdatei enthält die Informationen zur Konvertierung des PDF Generators, einschließlich PDF, Dateityp und Sicherheitseinstellungen.

>[!NOTE]
>
>Sie können die Zeitlimiteinstellung für PDF Generator nicht ändern, indem Sie eine benutzerdefinierte Datei &quot;native2pdfconfig.xml&quot;importieren. Die Zeitlimiteinstellung in dieser Datei dient nur zu Informationszwecken und zeigt die aktuelle Einstellung in PDF Generator an. Informationen zum Ändern der Zeitlimiteinstellung finden Sie unter „Festlegen von Leistungsparametern in PDF Generator“ unter [Installieren und Bereitstellen von AEM Forms](https://www.adobe.com/go/learn_aemforms_installJBoss_63_de).

## Aktuelle Konfigurationsdatei exportieren {#export-your-current-configuration-file}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Exportkonfiguration&quot;.
1. Um die Einstellungen zu exportieren, wählen Sie die entsprechende Option aus:

   * Um alle benannten Einstellungen zu exportieren, wählen Sie Gesamte Konfiguration herunterladen aus.
   * Um nur eine Adobe PDF-Einstellung, Sicherheitseinstellung oder Dateitypeinstellung zu exportieren, wählen Sie &quot;Minimale Konfiguration herunterladen&quot;aus.

     Wenn Sie eine Mindestkonfiguration exportieren, wählen Sie die zu exportierenden Einstellungen für Adobe PDF, Sicherheit und Dateityp aus.

1. Klicken Sie auf Herunterladen und speichern Sie die XML-Datei an einem entsprechenden Speicherort.

## Importieren einer Konfigurationsdatei {#import-a-configuration-file}

>[!NOTE]
>
>Ihr System wird basierend auf den Informationen in der importierten Datei neu konfiguriert.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Importkonfiguration&quot;.
1. Wählen Sie &quot;Vorhandene Konfigurationsdatei importieren&quot;.
1. Um den Speicherort der Datei im Feld &quot;Konfigurationsdatei&quot;anzugeben, klicken Sie auf &quot;Durchsuchen&quot;, um die Datei zu suchen und auszuwählen, und klicken Sie dann auf **Import**.

## Alle Ebenen in AutoCAD-Dateien konvertieren {#convert-all-layers-within-autocad-files}

Standardmäßig konvertiert PDF Generator anstelle aller Ebenen in der Datei nur die Standardebene von AutoCAD-Dateien in PDF. Gehen Sie wie folgt vor, um alle Ebenen zu konvertieren.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Exportkonfiguration&quot;.
1. Wählen Sie Gesamte Konfiguration herunterladen und klicken Sie auf Herunterladen.
1. Öffnen Sie die heruntergeladene Datei in einem Texteditor und fügen Sie unterhalb des Tags `AutoCAD`, aber innerhalb des Tags `PDFMaker` den Text `convertAllPages="true"` hinzu.
1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Importkonfiguration&quot;.
1. Wählen Sie &quot;Vorhandene Konfigurationsdatei importieren&quot;aus, geben Sie die aktualisierte Datei an und klicken Sie auf &quot;Importieren&quot;.

   Bei allen AutoCAD-Dateien, die mithilfe der geänderten Konfigurationsdatei konvertiert werden, werden alle Ebenen konvertiert.

## Zurücksetzen der Konfiguration auf die ursprünglichen Einstellungen, die mit PDF Generator installiert wurden {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Importkonfiguration&quot;.
1. Wählen Sie Konfiguration auf Standardeinstellungen zurücksetzen und klicken Sie auf Importieren.
