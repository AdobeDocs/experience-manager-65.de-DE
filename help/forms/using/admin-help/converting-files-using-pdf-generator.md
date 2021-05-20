---
title: Dateien mithilfe von PDF Generator konvertieren
seo-title: Dateien mithilfe von PDF Generator konvertieren
description: Erfahren Sie, wie Sie Dateien mithilfe von PDF Generator konvertieren.
seo-description: Erfahren Sie, wie Sie Dateien mithilfe von PDF Generator konvertieren.
uuid: 295afb8f-130a-44f5-b0ab-e4c93c0c9e52
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 999ae2be-56ba-48c1-861b-8d4c991a0206
feature: PDF Generator
exl-id: 0e2c12b5-24c8-4aca-8826-cb661051ce4f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 94%

---

# Dateien mithilfe von PDF Generator konvertieren{#converting-files-using-pdf-generator}

Sie können die PDF Generator-Webseiten verwenden, um Dateien zu konvertieren.

## PDF-Datei erstellen {#create-a-pdf-file}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „PDF erstellen“.
1. Klicken Sie auf „Durchsuchen“, um die Datei zu suchen und auszuwählen.

   >[!NOTE]
   >
   >PDF Generator kann den Dateityp von „DOC“-, „XLS“-, „PPT“- und „RTF“-Dateien automatisch erkennen, selbst wenn die Dateierweiterung im Dateinamen fehlt. Diese Funktion funktioniert nicht mit „DOCX“-, „XLSX“- und „PPTX“-Dateien.

1. Wählen Sie unter „Konfigurationseinstellungen“ entweder „Benutzerdefinierte Einstellungen verwenden“ oder „Einstellungsdatei hochladen“ aus.

   * Wählen Sie, wenn Sie benutzerdefinierte Einstellungen verwenden, die gewünschten Adobe PDF-, Sicherheits-, Dateityp- und Zeitlimiteinstellungen aus.

      Die Adobe PDF-Einstellungen gelten nur für die folgenden Konvertierungen: „PS in PDF“, „EPS in PDF“, „PRN in PDF“, „Bild in PDF“ bei aktivierter optischer Zeichenerkennung (OCR) und „Nativ in PDF“. Die Zeitlimiteinstellung gibt die Maximaldauer der Konvertierung an. Der Standardwert ist 270 Sekunden. Diese Einstellungen werden für Bild-in-PDF- und OpenOffice-in-PDF-Konvertierungen nicht verwendet.

   * Wenn Sie eine Einstellungsdatei hochladen, geben Sie deren Pfad und Namen in das Feld ein oder klicken Sie auf „Durchsuchen“, um die Datei zu suchen und auszuwählen.

1. (Optional) Geben Sie unter „XMP-Metadatendatei“ den Pfad und den Namen der XMP-Datei ein oder klicken Sie auf „Durchsuchen“, um die Datei zu suchen und auszuwählen. Eine XMP-Datei dient zum Hinzufügen standardmäßiger Metadateninformationen. (Siehe [Informationen zu XMP-Dateien](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Klicken Sie auf Erstellen. Nach der Erstellung wird ein Link zur Datei angezeigt. Tritt während der Konvertierung ein Fehler auf, wird eine Warnung angezeigt. Wenn Sie eine Postcript-Datei erstellen, enthält die Warnung auch einen Link zur Protokolldatei.
1. Klicken Sie auf den Link zur PDF-Datei. Die Datei wird in Acrobat geöffnet.

### Informationen zu XMP-Dateien  {#about-xmp-files}

PDF-Dokumente, die PDF Generator in Acrobat 5.0 oder höher erstellt, enthalten Dokumentmetadaten im XML-Format. *Metadaten sind Informationen zum Dokument und seinem Inhalt, z. B. der Name des Autors, Schlüsselwörter und Copyright-Informationen, die Suchprogramme verwenden können.*

Die Metadaten eines Dokuments enthalten u. a. Informationen, die auch in Acrobat im Dialogfeld „Dokumenteigenschaften“ auf der Registerkarte „Beschreibung“ angezeigt werden. Auf der Registerkarte „Beschreibung“ vorgenommene Änderungen werden von den Dokumentmetadaten übernommen. Dokumentmetadaten können mit Produkten anderer Anbieter erweitert und geändert werden.

Adobe Extensible Metadata Platform (XMP) stellt Adobe-Anwendungen eine allgemeine XML-Plattform zur Verfügung, die zur Standardisierung der Erstellung, Verarbeitung und des Austauschs von Dokumentmetadaten zwischen Veröffentlichungs-Workflows dient. Sie können den XML-Quellcode der Dokumentmetadaten im XMP-Format speichern und importieren, wodurch Metadaten von verschiedenen Dokumenten gemeinsam genutzt werden können. Weitere Informationen zu XMP-Dateien finden Sie unter[ Extensible Metadata Platform (XMP)](https://www.adobe.com/products/xmp/) und [Adobe XMP Developer Center](https://www.adobe.com/devnet/xmp.html).

Sie können XMP-Dateien in Acrobat erstellen.

## HTML- oder ZIP-Datei ins PDF-Format konvertieren  {#convert-an-html-file-or-zip-file-to-pdf}

Sie können mithilfe von PDF Generator die folgenden Dateitypen in das Adobe PDF-Format konvertieren:

* HTML-Dateien können konvertiert werden, indem Sie eine HTML-Datei hochladen oder die URL einer Webseite oder Website angeben.
* Archivdateien (ZIP), die HTML-Dateien, Bilddateien oder beides enthalten können.

Wenn die ZIP-Datei auf der untersten Ebene der Ordnerhierarchie mehr als eine HTML-Datei enthält, muss die ZIP-Datei ebenfalls eine Datei „index.htm“ oder „index.html“ enthalten.

>[!NOTE]
>
>* Für die Konvertierung von HTML in PDF müssen bestimmte Schriftarten im Schriftartensystemordner enthalten sein. Unter Linux-, Solaris- und AIX-Systemen muss der Schriftartensystemordner die Schriftart Courier enthalten. Unter Windows-Systemen muss der Schriftartensystemordner die Schriftart Times New Roman enthalten.
   >
   >
* (Nur UNIX-basiertes System) Eine der folgenden japanischen Schriftarten sollte auf dem AEM Forms-Server verfügbar sein, um eine Webseite mit japanischer Schriftart in ein PDF-Dokument zu konvertieren.
   >
   >  
* &quot;Sazanami Gothic&quot;
>  * &quot;Kozuka Gothic Pro-VI&quot;
>  * &quot;Kozuka Mincho Pro-VI&quot;
>  * &quot;Sazanami Gothic&quot;
>  * &quot;Kozuka Mincho Pr6N&quot;
>  * &quot;Sazanami Mincho&quot;
>  * &quot;Adobe Heiti Std.&quot;
>  * &quot;Adobe Song Std.&quot;

   >
   >
* Verwenden Sie die Option „Datei hochladen“ auf der Seite „HTML in PDF“, um eine Datei vom lokalen Dateisystem hochzuladen.


1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „HTML in PDF“.
1. Geben Sie die Datei an, die konvertiert werden soll, indem Sie eine der folgenden Aufgaben ausführen:

   * Geben Sie in „Datei hochladen“ den Pfad und den Namen der HTML- oder ZIP-Datei ein oder klicken Sie auf „Durchsuchen“, um die Datei zu suchen und auszuwählen.
   * Geben Sie in das Feld „URL angeben“ die URL der zu konvertierenden Seite oder Website ein.

   >[!NOTE]
   >
   >Die zu konvertierende Datei muss eine der Dateinamenerweiterungen „HTML“, „HTM“ oder „ZIP“ besitzen.

1. Legen Sie die Konfigurationseinstellungen fest:

   * Um benutzerdefinierte Einstellungen zu verwenden, wählen Sie „Benutzerdefinierte Einstellungen verwenden“ aus, geben Sie die Sicherheits- und Dateitypeinstellungen an und legen Sie einen Zeitlimitwert fest. Der Standardwert ist 270 Sekunden.
   >[!NOTE]
   >
   >Wenn der Generate PDF-Dienst für die Verwendung von Acrobat WebCapture konfiguriert ist, haben die auf dieser Seite gewählten Dateitypeinstellungen keine Auswirkungen auf die erzeugte PDF. Nehmen Sie stattdessen die geeigneten Änderungen an der auf dem Server installierten Version von Acrobat vor.

   * Um eine vorhandene Einstellungsdatei zu verwenden, wählen Sie „Einstellungsdatei hochladen“ aus und klicken Sie auf „Durchsuchen“, um zum Speicherort der Datei zu wechseln.


1. Um eine XMP-Datei hochzuladen, klicken Sie auf „Durchsuchen“ und wechseln Sie zum Speicherort der Datei. Eine XMP-Datei dient zum Hinzufügen standardmäßiger Metadateninformationen. (Siehe [Informationen zu XMP-Dateien](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Klicken Sie auf Erstellen. Nach der Erstellung wird ein Link zur PDF-Datei angezeigt.
1. Klicken Sie auf den Link, um die PDF-Datei in Acrobat anzuzeigen.

## Eine PDF-Datei in ein anderes Dateiformat (nur Windows) exportieren  {#export-a-pdf-file-to-another-file-format-windows-only}

Sie können PDF-Dateien in verschiedene Dateiformate exportieren, wie im Kapitel zum Generate PDF-Dienst in der [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63) beschrieben.

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „PDF exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die zu exportierende PDF-Datei zu suchen.
1. Geben Sie in der Liste „PDF-Datei exportieren in“ das Format an, in das Sie die PDF-Datei exportieren möchten.
1. Geben Sie im Feld „Timeout festlegen“ die Wartezeit bis zum Erreichen des Zeitlimits der Anwendung ein. Der Standardwert ist 270 Sekunden.

   Die Konvertierungsdauer, die bei der Konvertierung der Datei angezeigt wird, ist möglicherweise größer als der von Ihnen hier angegebene Wert. Die Konvertierungsdauer schließt die Wartezeit für den Prozess oder Vorgang, die Zeit zum Konvertieren der Datei und die Zeit des Ersatzkonverters (sofern erforderlich) ein. time. Der Wert „Timeout festlegen“ bezieht sich nur auf die Zeit, die zum Konvertieren der Datei erforderlich ist.

1. (Optional) Klicken Sie in der Option **Benutzerdefiniertes PreFlight-Profil angeben** auf „Durchsuchen“ und wählen Sie ein [benutzerdefiniertes PreFlight-Profil](https://helpx.adobe.com/acrobat/using/preflight-profiles-acrobat-pro.html) aus. PreFlight-Profile werden nur beim Konvertieren von Dokumenten in das PDF-Archivformat (PDF/A) verwendet.
1. Klicken Sie auf „Exportieren“. Nach der Konvertierung wird ein Link zur exportierten Datei angezeigt.
1. Klicken Sie auf den Link, um die konvertierte Datei anzuzeigen.

## PDF-Datei optimieren (Nur Windows) {#optimize-a-pdf}

PDF Generator unterstützt die Funktion zum Reduzieren der Größe von PDF-Dateien.

>[!NOTE]
>
>Durch die Optimierung eines digital signierten Dokuments werden die digitalen Signaturen entfernt und ungültig.

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „PDF optimieren“.
1. Klicken Sie auf „Durchsuchen“, um die zu optimierende PDF-Datei zu suchen.
1. Legen Sie die Konfigurationseinstellungen fest:

   * Um benutzerdefinierte Einstellungen zu verwenden, wählen Sie „Benutzerdefinierte Einstellungen verwenden“ aus, geben Sie die Dateitypeinstellungen an und legen Sie einen Zeitlimitwert fest. Der Standardwert ist 270 Sekunden.
   * Um eine vorhandene Einstellungsdatei zu verwenden, wählen Sie „Einstellungsdatei hochladen“ aus und klicken Sie auf „Durchsuchen“, um zum Speicherort der Datei zu wechseln.

1. Klicken Sie auf Erstellen.
