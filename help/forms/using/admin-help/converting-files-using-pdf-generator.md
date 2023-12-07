---
title: Konvertieren von Dateien mit PDF Generator
description: Der PDF Generator-Dienst konvertiert native Dateiformate in PDF. Er kann außerdem PDF-Dokumente in andere Dateiformate konvertieren und die Größe von PDF-Dokumenten optimieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: 0e2c12b5-24c8-4aca-8826-cb661051ce4f
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 11%

---

# Konvertieren von Dateien mit PDF Generator{#converting-files-using-pdf-generator}

Sie können die PDF Generator-Webseiten verwenden, um Dateien zu konvertieren.

## Erstellen einer PDF-Datei {#create-a-pdf-file}

1. Klicken Sie in Administration Console auf Dienste > PDF Generator > PDF erstellen .
1. Klicken Sie auf Durchsuchen , um die Datei zu suchen und auszuwählen.

   >[!NOTE]
   >
   >PDF Generator kann den Dateityp von .doc-, .xls-, .ppt- und .rtf-Dateien automatisch erkennen, selbst wenn dem Dateinamen die Dateierweiterung fehlt. Diese Funktion funktioniert nicht mit DOCX-, XLSX- und PPTX-Dateien.

1. Wählen Sie unter &quot;Konfigurationseinstellungen&quot;Benutzerdefinierte Einstellungen verwenden oder Einstellungsdatei hochladen aus.

   * Wenn Sie benutzerdefinierte Einstellungen verwenden, wählen Sie eine Adobe PDF-Einstellung, Sicherheitseinstellung und Dateitypeinstellung aus und geben Sie eine Zeitüberschreitung an.

     Die Adobe PDF-Einstellungen gelten nur für PS-zu-PDF-, EPS-zu-PDF-, PRN-zu-PDF-, Bild-zu-PDF-Konvertierungen mit aktiviertem OCR und Native-zu-PDF-Konvertierungen. Die Zeitlimiteinstellung gibt die maximale Zeit an, die für den Abschluss der Konvertierung erforderlich ist. Der Standardwert ist 270 Sekunden. Diese Einstellungen werden bei der Bildkonvertierung in PDF und bei der OpenOffice-in-PDF-Konvertierung nicht verwendet.

   * Wenn Sie eine Einstellungsdatei hochladen, geben Sie deren Pfad und Namen in das Feld ein oder klicken Sie auf &quot;Durchsuchen&quot;, um die Datei zu suchen und auszuwählen.

1. (Optional) Geben Sie unter XMP Metadatendatei den Pfad und den Namen der XMP ein oder klicken Sie auf Durchsuchen , um die Datei zu suchen und auszuwählen. Eine XMP-Datei kann verwendet werden, um standardmäßige Metadateninformationen einzuschließen. (Siehe [Über XMP Dateien](converting-files-using-pdf-generator.md#about-xmp-files).
1. Klicken Sie auf „Erstellen“. Wenn die Datei erstellt wird, wird ein Link dazu angezeigt. Tritt während der Konvertierung ein Fehler auf, wird eine Warnung angezeigt. Wenn Sie eine Postscript-Datei erstellen, enthält die Warnung auch einen Link zur Protokolldatei.
1. Klicken Sie auf den Link für die PDF-Datei. Die Datei wird in Acrobat geöffnet.

### Über XMP Dateien {#about-xmp-files}

PDF-Dokumente, die PDF Generator in Acrobat 5.0 oder höher erstellt, enthalten Dokumentmetadaten im XML-Format. *Metadaten* enthält Informationen über das Dokument und seinen Inhalt, z. B. den Namen des Autors, Schlüsselwörter und Copyright-Informationen, die von Suchanwendungen verwendet werden können.

Die Dokumentmetadaten enthalten Informationen, die auch auf der Registerkarte &quot;Beschreibung&quot;des Dialogfelds &quot;Dokumenteigenschaften&quot;in Acrobat angezeigt werden. Änderungen, die auf der Registerkarte &quot;Beschreibung&quot;vorgenommen werden, werden in den Dokumentmetadaten angezeigt. Dokumentmetadaten können mithilfe von Drittanbieterprodukten erweitert und geändert werden.

Adobe Extensible Metadata Platform (XMP) bietet Adobe-Programmen ein gemeinsames XML-Framework, das die Erstellung, Verarbeitung und den Austausch von Dokumentmetadaten zwischen Veröffentlichungs-Workflows standardisiert. Sie können den XML-Quellcode der Dokumentmetadaten im XMP-Format speichern und importieren, um die Freigabe von Metadaten zwischen verschiedenen Dokumenten zu erleichtern. Weitere Informationen zu XMP finden Sie unter [Extensible Metadata Platform (XMP)](https://www.adobe.com/de/products/xmp/) und [Adobe XMP Developer Center](https://www.adobe.com/devnet/xmp.html).

Sie können XMP in Acrobat erstellen.

## Konvertieren einer HTML- oder ZIP-Datei in PDF {#convert-an-html-file-or-zip-file-to-pdf}

Sie können PDF Generator verwenden, um die folgenden Dateitypen in Adobe PDF zu konvertieren:

* HTML-Dateien, die Sie konvertieren können, indem Sie eine HTML-Datei hochladen oder die URL einer Webseite oder Website angeben.
* Archivierte Dateien (ZIP), die HTML-Dateien, Bilddateien oder beides enthalten können.

Wenn die ZIP-Datei mehr als eine HTML-Datei auf der untersten Ebene ihrer Ordnerhierarchie enthält, muss die ZIP-Datei auch eine Datei index.htm oder index.html enthalten.

>[!NOTE]
>
>* Für die Funktion HTML zum PDF sind bestimmte Schriftarten im Verzeichnis für Systemschriftarten erforderlich. Auf Linux-, Solaris- und AIX-Systemen muss der Schriftartenordner des Systems die Schriftart Courier enthalten. Auf Windows-Systemen muss der Schriftartenordner des Systems Times New Roman enthalten.
>
>* (Nur UNIX-basierte Systeme) Eine der folgenden japanischen Schriftarten sollte auf dem AEM Forms-Server verfügbar sein, um eine Webseite mit japanischer Schriftart in ein PDF-Dokument konvertieren zu können.
>
>  * &quot;Sazanami Gothic&quot;
>  * &quot;Kozuka Gothic Pro-VI&quot;
>  * &quot;Kozuka Mincho Pro-VI&quot;
>  * &quot;Sazanami Gothic&quot;
>  * &quot;Kozuka Mincho Pr6N&quot;
>  * &quot;Sazanami Mincho&quot;
>  * &quot;Adobe Heiti Std&quot;
>  * &quot;Adobe Song Std&quot;
>
>* Um eine Datei aus dem lokalen Dateisystem hochzuladen, verwenden Sie auf der HTML-PDF-Seite die Option Datei hochladen .

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;HTML zum PDF&quot;.
1. Geben Sie die zu konvertierende Datei an, indem Sie eine der folgenden Aufgaben ausführen:

   * Geben Sie in Datei hochladen den Pfad und den Dateinamen der HTML- oder ZIP-Datei ein oder klicken Sie auf Durchsuchen , um die Datei zu suchen und auszuwählen.
   * Geben Sie im Feld &quot;URL angeben&quot;die URL der zu konvertierenden Seite oder Website ein.

   >[!NOTE]
   >
   >Die zu konvertierende Datei muss die Dateinamenerweiterung .html, .htm oder .zip aufweisen.

1. Geben Sie die Konfigurationseinstellungen an:

   * Um benutzerdefinierte Einstellungen zu verwenden, wählen Sie &quot;Use Custom Settings&quot;, geben Sie die Sicherheits- und Dateitypeinstellungen an und geben Sie einen Zeitlimitwert an. Der Standardwert ist 270 Sekunden.

   >[!NOTE]
   >
   >Wenn Sie den Generate PDF-Dienst für die Verwendung von Acrobat WebCapture konfiguriert haben, wirken sich die auf dieser Seite ausgewählten Dateitypeinstellungen nicht auf die erzeugte PDF aus. Nehmen Sie stattdessen die entsprechenden Änderungen an der auf dem Server installierten Version von Acrobat vor.

   * Um eine vorhandene Einstellungsdatei zu verwenden, wählen Sie Einstellungsdatei hochladen und klicken Sie auf Durchsuchen , um zum Dateispeicherort zu wechseln.

1. Um eine XMP hochzuladen, klicken Sie auf Durchsuchen und navigieren Sie zum Dateispeicherort. Eine XMP-Datei kann verwendet werden, um standardmäßige Metadateninformationen einzuschließen. (Siehe [Über XMP Dateien](converting-files-using-pdf-generator.md#about-xmp-files).
1. Klicken Sie auf „Erstellen“. Bei der Erstellung der Datei wird ein Link zur PDF-Datei angezeigt.
1. Klicken Sie auf den Link, um das PDF-Dokument in Acrobat anzuzeigen.

## Exportieren einer PDF-Datei in ein anderes Dateiformat (nur Windows) {#export-a-pdf-file-to-another-file-format-windows-only}

Sie können PDF-Dateien in verschiedene Dateiformate exportieren, wie im Kapitel Generate PDF Service beschrieben. [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Export PDF&quot;.
1. Klicken Sie auf Durchsuchen , um die zu exportierende PDF-Datei zu suchen.
1. Wählen Sie in der aufzulistenden Export PDF-Datei das Format aus, in das die PDF-Datei exportiert werden soll.
1. Geben Sie in das Feld &quot;Timeout festlegen&quot;die Wartezeit ein, bis eine Zeitüberschreitung für die Anwendung eintritt. Der Standardwert ist 270 Sekunden.

   Die Konvertierungszeit, die bei der Konvertierung der Datei angezeigt wird, kann größer sein als der hier angegebene Wert. Die Konvertierungsdauer umfasst die Wartezeit auf den Thread oder Prozess, die Zeit, die zum Konvertieren der Datei benötigt wird, und die Zeit, die der Fallback-Konverter benötigt (falls zutreffend). Zeit. Der Wert &quot;Timeout angeben&quot;ist nur die Zeit, die zum Konvertieren der Datei benötigt wird.

1. (Optional) Klicken Sie in der Option **Benutzerdefiniertes PreFlight-Profil angeben** auf „Durchsuchen“ und wählen Sie ein [benutzerdefiniertes PreFlight-Profil](https://helpx.adobe.com/de/acrobat/using/preflight-profiles-acrobat-pro.html) aus. PreFlight-Profile werden nur beim Konvertieren von Dokumenten in das PDF-Archivformat (PDF/A) verwendet.
1. Klicken Sie auf Exportieren. Wenn die Konvertierung abgeschlossen ist, wird ein Link zur exportierten Datei angezeigt.
1. Klicken Sie auf den Link, um die konvertierte Datei anzuzeigen.

## PDF optimieren (nur Windows) {#optimize-a-pdf}

PDF Generator unterstützt die Reduzierung der Größe von PDF-Dateien.

>[!NOTE]
>
>Durch die Optimierung eines digital signierten Dokuments werden die digitalen Signaturen entfernt und ungültig gemacht.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Optimize PDF&quot;.
1. Klicken Sie auf Durchsuchen , um die zu optimierende PDF-Datei zu suchen.
1. Geben Sie die Konfigurationseinstellungen an:

   * Um benutzerdefinierte Einstellungen zu verwenden, wählen Sie &quot;Benutzerdefinierte Einstellungen verwenden&quot;, geben Sie die Dateitypeinstellungen an und geben Sie einen Zeitlimitwert an. Der Standardwert ist 270 Sekunden.
   * Um eine vorhandene Einstellungsdatei zu verwenden, wählen Sie Einstellungsdatei hochladen und klicken Sie auf Durchsuchen , um zum Dateispeicherort zu wechseln.

1. Klicken Sie auf „Erstellen“.
