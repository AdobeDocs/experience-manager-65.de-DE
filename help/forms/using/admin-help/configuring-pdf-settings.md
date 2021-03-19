---
title: Konfigurieren von Adobe PDF
seo-title: Konfigurieren von Adobe PDF
description: Erfahren Sie, wie Sie die Adobe PDF-Einstellungen konfigurieren.
seo-description: Erfahren Sie, wie Sie die Adobe PDF-Einstellungen konfigurieren.
uuid: 980c9d6a-f75e-4e7d-b050-d2d07a10ef33
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ab018b6d-0233-4439-bb75-58c5421d769a
feature: PDF Generator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '7278'
ht-degree: 74%

---


# Konfigurieren von Adobe PDF{#configuring-adobe-pdf-settings}

Auf der Seite „Adobe PDF-Einstellungen“ werden die Konvertierungseinstellungen angezeigt, die Sie für die zu verwendenden Quellen angeben können. Sie können die vordefinierten PDF-Einstellungen verwenden oder eigene erstellen. Die PDF-Einstellungen bestimmen genau die Konvertierungsmethode und die sich ergebende PDF-Struktur und deren Eigenschaften. Adobe PDF-Einstellungen wurden bisher als Distiller®-Parameter oder Auftragsoptionen bezeichnet.

Auf der Seite „Adobe PDF-Einstellungen“ können Sie die folgenden Aufgaben durchführen:

* Anzeigen der vordefinierten PDF-Einstellungen. (Siehe [Informationen zu den vordefinierten PDF-Einstellungen](configuring-pdf-settings.md#about-the-predefined-pdf-settings).)
* Erstellen einer PDF-Einstellung oder Bearbeiten der zuvor erstellten Einstellung. (Siehe [PDF-Einstellungen hinzufügen und bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).)
* Angeben der PDF-Standardeinstellungen. (Siehe [Standardeinstellungen ändern](/help/forms/using/admin-help/configuring-file-type-settings.md#change-the-default-settings))
* Hochladen einer PDF-Einstellungsdatei auf den Server. (Siehe [PDF-Einstellungen hochladen](configuring-pdf-settings.md#upload-pdf-settings).)
* Löschen angepasster PDF-Einstellungen. (Siehe [PDF-Einstellungen löschen](configuring-pdf-settings.md#delete-pdf-settings).)
* Hochladen und Herunterladen von Prologue- und Epilogue-Dateien. (Siehe [Hochladen und Herunterladen von Prologue- und Epilogue-Dateien](configuring-pdf-settings.md#uploading-and-downloading-prologue-and-epilogue-files).)

Die Adobe PDF-Einstellungen gelten nur für PDFMaker-Konvertierungen. Dazu zählen die folgenden Konvertierungen:

* Microsoft Word-Dokument (DOC, DOCX, RTF, TXT)
* Microsoft Excel-Dokument (XLS, XLSX)
* Microsoft PowerPoint-Dokument (PPT, PPTX)
* Microsoft Project-Dokument (MPP)
* Microsoft Visio-Dokument (VSD)

>[!NOTE]
>
>Bei der Verwendung von OpenOffice-Formaten zur Konvertierung in die erwähnten Formate, werden die Adobe PDF-Einstellungen nicht angewendet.

## Informationen zu den vordefinierten PDF-Einstellungen {#about-the-predefined-pdf-settings}

PDF Generator bietet mehrere vordefinierte PDF-Einstellungen. Sie können diese vordefinierten Einstellungen nicht ändern, Sie können jedoch eine Einstellung auf Grundlage einer vorhandenen erstellen, indem Sie diese Einstellung bearbeiten und unter einem neuen Namen speichern.

**Drucken in hoher Qualität:** Erstellt PDF-Dateien für eine hochwertige Ausgabe. Diese Einstellung dient zum:

* Neuberechnen von Farb- und Graustufenbildern mit 300 dpi;
* Neuberechnen von Schwarzweißbildern mit 1200 dpi;
* Drucken mit einer höheren Bildauflösung;
* Verwenden anderer Einstellungen zum Erhalten eines Höchstmaßes an Informationen über das Originaldokument.

Diese PDF-Dateien können in Adobe Acrobat 5 und Adobe Acrobat Reader® 5 oder höher geöffnet werden.

**Übergroße Seiten:** Erstellt PDF-Dokumente, die für eine zuverlässige Anzeige und Druckausgabe technischer Zeichnungen mit einer Größe von mehr als 200 x 200 Zoll geeignet sind. Erstellte PDF-Dokumente können in Adobe Acrobat Professional und in Acrobat Standard Version 7 oder höher sowie Adobe Reader 7 oder höher geöffnet werden.

**PDF/A-1B 2005 CMYK / PDF/A-1B 2005 RGB:** Überprüft eingehende Aufträge auf Einhaltung des ISO-Standards für die langfristige Erhaltung (Archivierung) elektronischer Dokumente und erstellt PDF/A-Dateien nur, wenn sie konform sind. Diese Dateien dienen hauptsächlich zur Archivierung. Kompatible Dateien dürfen nur Text, Rasterbilder und Vektorobjekte und keine Verschlüsselung oder Skripte enthalten. Darüber hinaus müssen alle Schriftarten so eingebettet sein, dass die Dokumente ihrer Erstellung entsprechend geöffnet und angezeigt werden können. PDF/A 1b verwendet PDF 1.4 und konvertiert alle Farben je nach ausgewähltem Standard entweder in CMYK oder in RGB. Mithilfe dieser Einstellungsdatei erstellte PDF-Dateien können in Acrobat 5 und Acrobat Reader 5 und höher geöffnet werden. Weitere Informationen zu PDF/A finden Sie unter Adobe und Branchenstandards.

**PDF/X-1a 2001:** Überprüft eingehende Aufträge auf PDF/X-1a-Kompatibilität und erstellt PDF-Dateien nur, wenn sie konform sind. PDF/X-1a ist ein ISO-Standard für den Austausch grafischer Inhalte. PDF/X-1a erfordert, dass alle Schriftarten eingebettet, die entsprechenden PDF-Felder angegeben und Farben entweder als CMYK oder Volltonfarben angezeigt werden. PDF-Dateien, die die PDF/X-1a-Anforderungen erfüllen, werden für eine bestimmte Ausgabebedingung eingerichtet (z. B. für den Web-Offset-Druck gemäß Specifications Web Offset Publications [SWOP]). Weitere Informationen zu PDF/X finden Sie unter Adobe und Branchenstandards.

**PDF/X-3 2002:** Überprüft eingehende Aufträge auf PDF/X-3-Kompatibilität und erstellt PDF-Dateien nur, wenn sie konform sind. Ebenso wie PDF/X-1a ist PDF/X-3 ein ISO-Standard für den Austausch grafischer Inhalte. Der Hauptunterschied ist, dass PDF/X-3 geräteunabhängige Farben unterstützt.

**Druckqualität:** Erstellt PDF-Dateien für eine hochwertige Druckproduktion (z. B. auf einem Belichter oder einem Plattenbelichter). In diesem Fall spielt die Dateigröße keine Rolle. Ziel ist die Erhaltung sämtlicher Informationen in einer PDF-Datei, die ein Akzidenzdrucker oder Druckvorstufen-Dienstleister zum ordnungsgemäßen Drucken des Dokuments benötigt. Die dazugehörigen Optionen dienen zum:

* Neuberechnen von Farb- und Graustufenbildern mit 300 dpi;
* Neuberechnen von Schwarzweißbildern mit 1200 dpi;
* Einbetten aller im Dokument verwendeten Schriften;
* Drucken mit einer höheren Bildauflösung;
* Nicht automatischen Drehen von Seiten basierend auf der Ausrichtung des Textes oder von DSC-Kommentaren;
* Verwenden anderer Einstellungen zum Erhalten eines Höchstmaßes an Informationen über das Originaldokument.

Druckaufträge mit Schriftarten, die nicht eingebettet werden können, schlagen fehl. Diese PDF-Dateien können in Acrobat 5 und Acrobat Reader 5 (und höheren Versionen) geöffnet werden.

>[!NOTE]
>
>Ermitteln Sie vor dem Erstellen einer PDF-Datei, die an einen Akzidenzdrucker oder Druckvorstufen-Dienstleister gesendet werden soll, die benötigte Ausgabeauflösung und andere Einstellungen und fordern Sie eine „.joboptions“-Datei mit den empfohlenen Einstellungen an. Sie müssen ggf. die Adobe PDF-Einstellungen für einen bestimmten Dienstleister anpassen und anschließend eine eigene „.joboptions“-Datei bereitstellen.

**Kleinste Dateigröße:** Erstellt PDF-Dateien für die Anzeige im Internet oder Intranet oder für die Verteilung über ein E-Mail-System zur Anzeige auf dem Bildschirm. Bei dieser Gruppe von Optionen wird eine Komprimierung, Neuberechnung und relativ niedrige Bildauflösung verwendet. Alle Farben werden in sRGB konvertiert und Schriftarten werden nur eingebettet, wenn dies notwendig ist. Außerdem werden Dateien für das seitenweise Herunterladen von Dokumenten optimiert. Diese PDF-Dateien können in Acrobat 5 und Acrobat Reader 5.0 oder höher geöffnet werden.

**Standard:** Erstellt PDF-Dateien zum Drucken auf Desktop-Druckern oder digitalen Kopierern, zum Veröffentlichen auf einer CD oder zum Senden an einen Client als Veröffentlichungs-Testversand. Bei dieser Gruppe von Optionen werden Komprimierung und Neuberechnung verwendet, um die Dateigröße zu reduzieren. Es werden jedoch auch alle in der Datei verwendeten Teilmengen von Schriftarten eingebettet und alle Farben in sRGB konvertiert. Ferner erfolgt die Druckausgabe mit einer mittleren Auflösung, um eine ausreichend präzise Wiedergabe des Originaldokuments zu erstellen. Beachten Sie, dass Microsoft Windows-Schriftartenuntergruppen nicht standardmäßig eingebettet werden. Diese PDF-Dateien können in Acrobat 5 und Acrobat Reader 5.0 oder höher geöffnet werden.

## PDF-Einstellungen hinzufügen und bearbeiten  {#add-or-edit-pdf-settings}

Die PDF-Einstellungen bestimmen präzise die Konvertierungsmethode und die sich ergebende PDF-Struktur und deren Eigenschaften. Erstellen Sie eine neue PDF-Einstellung oder bearbeiten Sie die Einstellung, die Sie zuvor erstellt haben. Sie können diese vordefinierten Einstellungen nicht ändern, Sie können jedoch eine Einstellung auf Grundlage einer vorhandenen erstellen, indem Sie diese Einstellung bearbeiten und unter einem neuen Namen speichern.

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Adobe PDF-Einstellungen“.
1. Klicken Sie auf „Neu“ oder auf den Namen einer vorhandenen Einstellung.
1. Geben Sie auf der Seite „Adobe PDF-Einstellungen“ im Bereich „Neu/Bearbeiten“ in den folgenden Abschnitten die erforderlichen Informationen ein:

   [Allgemeine Optionen](configuring-pdf-settings.md#general-options)

   [Bildoptionen](configuring-pdf-settings.md#images-options)

   [Schriftartoptionen](configuring-pdf-settings.md#fonts-options)

   [Farboptionen](configuring-pdf-settings.md#color-options)

   [Erweiterte Optionen](configuring-pdf-settings.md#advanced-options)

   [Optionen für „Standards - Berichterstellung und Kompatibilität“](configuring-pdf-settings.md#standards-reporting-and-compliance-options)

   [Optionen für Ansicht beim Öffnen](configuring-pdf-settings.md#initial-view-options)

   Um zu einem anderen Abschnitt zu wechseln, klicken Sie auf dessen Link auf der Webseite oder auf eine der Schaltflächen Weiter oder Zurück.

1. Klicken Sie nach dem Eingeben der Informationen in alle Abschnitte auf „Speichern“ oder „Speichern unter“ und geben Sie einen Namen für die Einstellung ein.

## PDF-Einstellungen hochladen  {#upload-pdf-settings}

Sie können PDF-Einstellungen auf dem Server mit PDF Generator zur Verfügung stellen, indem Sie sie von einem lokalen Computer oder aus einem Netzwerkspeicherort hochladen.

1. Klicken Sie in Administration Console auf „Dienste“ > „ PDF Generator “ > „Adobe PDF-Einstellungen“.
1. Klicken Sie auf der Seite „Adobe PDF-Einstellung hochladen“ auf „Durchsuchen“, suchen Sie die PDF-Einstellungsdatei und klicken Sie auf „Öffnen“.
1. Klicken Sie auf „OK“ und dann erneut auf „OK“.

## PDF-Einstellungen löschen  {#delete-pdf-settings}

Sie können PDF-Einstellungen dauerhaft löschen, wenn sie nicht mehr benötigt werden.

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Adobe PDF-Einstellungen“.
1. Aktivieren Sie das Kontrollkästchen neben der zu löschenden Einstellung. Sie können mehrere Einstellungen auswählen.
1. Klicken Sie auf der Seite „Löschbestätigung“ auf „Löschen“ und dann erneut auf „Löschen“.

## Allgemeine Optionen {#general-options}

Verwenden Sie die allgemeinen Optionen, um die Version von Acrobat anzugeben, die zum Zweck der Dateikompatibilität und für andere Datei- und Geräteoptionen verwendet werden soll. Weitere Informationen über den Zugriff auf die allgemeinen Optionen finden Sie unter [PDF-Einstellungen hinzufügen und bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

### Dateioptionen {#file-options}

**Kompatibilität:** Die Kompatibilitätsstufe der PDF-Datei. Wählen Sie für Dokumente, die in großem Umfang verteilt werden sollen, Acrobat 4 (PDF 1.3) oder Acrobat 5 (PDF 1.4), um sicherzustellen, dass alle Benutzer das Dokument anzeigen und drucken können. Wenn Sie Dateien basierend auf der Kompatibilität mit Acrobat 5 oder höher erstellen, sind diese ggf. nicht mit früheren Versionen von Acrobat kompatibel. In den folgenden Unterabschnitten werden einige der Unterschiede zwischen PDF-Dateien erläutert, die mit verschiedenen Acrobat-Kompatibilitätsstufen erstellt wurden.

<table>
 <tbody>
  <tr>
   <th><p>Acrobat 4 (PDF 1.3)</p> </th>
   <th><p>Acrobat 5 (PDF 1.4)</p> </th>
   <th><p>Acrobat 6 (PDF 1.5)</p> </th>
   <th><p>Acrobat 7 (PDF 1.6) und Acrobat 8 (PDF 1.7)</p> </th>
  </tr>
  <tr>
   <td><p>Können mit Acrobat 3.0 und Acrobat Reader 3.0 (und höheren Versionen) geöffnet werden.</p> </td>
   <td><p>Können mit Acrobat 3.0 und Acrobat Reader 3.0 (und höheren Versionen) geöffnet werden. Funktionen, die für spätere Versionen spezifisch sind, werden ggf. nicht unterstützt oder sind nicht anzeigbar.</p> </td>
   <td><p>Die meisten Dateien können mit Acrobat 4 und Acrobat Reader 4.0 oder höher geöffnet werden. Funktionen, die für spätere Versionen spezifisch sind, werden ggf. nicht unterstützt oder sind nicht anzeigbar.</p> </td>
   <td><p>Die meisten Dateien können mit Acrobat 4 und Acrobat Reader 4.0 oder höher geöffnet werden. Funktionen, die für spätere Versionen spezifisch sind, werden ggf. nicht unterstützt oder sind nicht anzeigbar.</p> </td>
  </tr>
  <tr>
   <td><p>Darf keine Grafiken mit unverzögerten Transparenzeffekten enthalten. Vor der Konvertierung in PDF 1.3 müssen alle Transparenzen reduziert werden.</p> </td>
   <td><p>Unterstützt die Verwendung unverzögerter Transparenzeffekte in Grafiken. (Die Acrobat Distiller-Funktion reduziert die Transparenz.)</p> </td>
   <td><p>Unterstützt die Verwendung unverzögerter Transparenzeffekte in Grafiken. (Die Acrobat Distiller-Funktion reduziert die Transparenz.)</p> </td>
   <td><p>Unterstützt die Verwendung unverzögerter Transparenzeffekte in Grafiken. (Die Acrobat Distiller-Funktion reduziert die Transparenz.)</p> </td>
  </tr>
  <tr>
   <td><p>Ebenen werden nicht unterstützt.</p> </td>
   <td><p>Ebenen werden nicht unterstützt.</p> </td>
   <td><p>Behält Ebenen bei, wenn PDF-Dateien in Anwendungen erstellt werden, die die Generierung von PDF-Dokumenten mit Ebenen unterstützen, wie z. B. Adobe Illustrator® CS oder Adobe InDesign® CS und höher.</p> </td>
   <td><p>Behält Ebenen bei, wenn PDF-Dateien in Anwendungen erstellt werden, die die Generierung von PDF-Dokumenten mit Ebenen unterstützen, wie z. B. Illustrator CS oder InDesign CS und höher.</p> </td>
  </tr>
  <tr>
   <td><p>DeviceN-Farbraum mit 8 Farbmitteln wird unterstützt.</p> </td>
   <td><p>DeviceN-Farbraum mit 8 Farbmitteln wird unterstützt.</p> </td>
   <td><p>DeviceN-Farbraum mit 31 Farbmitteln wird unterstützt.</p> </td>
   <td><p>DeviceN-Farbraum mit 31 Farbmitteln wird unterstützt.</p> </td>
  </tr>
  <tr>
   <td><p>Multibyte-Schriften können eingebettet werden. (Distiller konvertiert die Schriften beim Einbetten.)</p> </td>
   <td><p>Multibyte-Schriften können eingebettet werden.</p> </td>
   <td><p>Multibyte-Schriften können eingebettet werden.</p> </td>
   <td><p>Multibyte-Schriften können eingebettet werden.</p> </td>
  </tr>
  <tr>
   <td><p>40-Bit-RC4-Sicherheit wird unterstützt.</p> </td>
   <td><p>128-Bit-RC4-Sicherheit wird unterstützt.</p> </td>
   <td><p>128-Bit-RC4-Sicherheit wird unterstützt.</p> </td>
   <td><p>128-Bit-RC4- und 128-Bit-AES-Sicherheit (Advanced Encryption Standard) wird unterstützt.</p> </td>
  </tr>
 </tbody>
</table>

**Komprimierung auf Objektebene:** Fasst kleine Objekte (die jeweils selbst nicht komprimierbar sind) in Streams zusammen, die dann effizient komprimiert werden können.

**Aus: Komprimiert** keine Strukturinformationen im PDF-Dokument. Wählen Sie diese Option aus, wenn Benutzer Lesezeichen und andere Strukturinformationen in Acrobat 5 oder höher anzeigen, durch diese navigieren und mit diesen interagieren können sollen.

**Nur Tags:** Komprimiert Strukturinformationen im PDF-Dokument. Diese Option resultiert in einer PDF-Datei, die in Acrobat 5 geöffnet und gedruckt werden kann. Die Benutzer können keine Eingabehilfe, Struktur- und PDF-Informationen in Tags in Acrobat 5 oder Acrobat Reader 5.0 anzeigen. In Acrobat 6 und Adobe Reader 6.0 können diese Informationen angezeigt werden.

**Seiten automatisch drehen:** Legt die automatische Drehung von Seiten basierend auf der Ausrichtung des Textes oder der DSC-Kommentare fest. Für einige Seiten (z. B. mit Tabellen) ist es ggf. erforderlich, dass sie seitlich gedreht werden, damit sie gelesen werden können. Wählen Sie „Einzeln“ aus, um jede Seite basierend auf der Ausrichtung des Textes auf der jeweiligen Seite zu drehen. Wählen Sie „Zusammen pro Datei“ aus, um alle Seiten im Dokument basierend auf der Ausrichtung des Großteils des Textes zu drehen.

>[!NOTE]
>
>Wenn „DSC-Kommentare verarbeiten“ in den Einstellungen unter „Erweiterte Einstellungen“ ausgewählt ist und Kommentare zur Anzeigeausrichtung enthalten sind, haben diese Kommentare beim Bestimmen der Seitenausrichtung Vorrang.

**Bindung:** Gibt an, ob eine PDF-Datei mit Bindung an der linken oder rechten Seite angezeigt werden soll. Diese Einstellung wirkt sich auf die Anzeige von Seiten im Layout „Fortlaufend - Doppelseiten“ aus und bewirkt, dass Kleinbilder nebeneinander angezeigt werden.

**Auflösung:** Legt die Emulation für die Auflösung eines Druckers für Eingabedateien fest, die ihr Verhalten an die Auflösung des Druckers anpassen, auf den sie gedruckt werden. Bei den meisten Eingabedateien führt eine höhere Auflösungseinstellung zu größeren PDF-Dateien mit hoher Qualität und eine niedrigere Einstellung zu kleineren PDF-Dateien mit geringerer Qualität. In der Regel bestimmt die Auflösung die Anzahl der Schritte in einem Verlauf. Sie können einen Wert von 72 bis 4000 eingeben. Sie sollten diese Einstellung als Standard beibehalten, es sei denn, Sie möchten die PDF-Datei auf einem bestimmten Drucker drucken und die für die ursprüngliche Eingabedatei festgelegte Auflösung emulieren.

>[!NOTE]
>
>Durch das Erhöhen der Auflösungseinstellung wird die Dateigröße erhöht und ggf. die Verarbeitungsdauer einiger Dateien verlängert.

**Alle Seiten oder Seiten von:** Gibt an, welche Seiten konvertiert werden sollen. Lassen Sie das Feld „Bis“ leer, um einen Bereich von der Seitennummer, die Sie in das Feld „Von“ eingeben, bis zum Ende der Datei zu erstellen.

**Optimieren für schnelle Web-Ansicht:** Strukturiert die Datei für das seitenweise Herunterladen (Byte-Serving) von Webservern um. Diese Option komprimiert Text und Strichgrafiken unabhängig von den auf der Registerkarte „Bilder“ ausgewählten Komprimierungseinstellungen. Die Komprimierung führt zu einer Beschleunigung von Zugriff und Anzeige, wenn die Datei aus dem Internet oder einem Netzwerk heruntergeladen wird. In der Standardeinstellung ist diese Option deaktiviert.

### Standardpapierformat  {#default-page-size}

Die Optionen unter „Standardpapierformat“ geben das zu verwendende Papierformat an, wenn in der Originaldatei keines angegeben ist. Adobe PostScript-Dateien enthalten in der Regel diese Informationen, mit Ausnahme von EPS-Dateien (Encapsulated PostScript), in denen die Größe eines Begrenzungsrahmens, jedoch kein Papierformat angegeben wird. Das maximal zulässige Papierformat ist 31.800.000 cm in beide Richtungen. Mit diesen Optionen wird das Standardpapierformat konfiguriert:

**Breite:** Breite der Seite

**Höhe:** Höhe der Seite

**Einheiten:** Einheiten für die Einstellungen für Breite und Höhe

## Bildoptionen {#images-options}

Die Bildoptionen dienen zum Angeben der Komprimierung und Neuberechnung für Bilder. Sie können nach Wunsch mit diesen Optionen experimentieren, um das gewünschte Gleichgewicht zwischen Dateigröße und Bildqualität zu finden. Weitere Informationen zum Zugriff auf die Bildeinstellungen finden Sie unter [PDF-Einstellungen hinzufügen und bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Mit diesen Optionen werden Farb-, Graustufen- und Schwarzweißbilder konfiguriert:

**Neuberechnung:** Legen Sie einen Wert für jeden Bildtyp fest. Um Farb-, Graustufen- und Schwarzweißbilder neu zu berechnen, kombiniert PDF Generator Pixel in einem Auswahlbereich und erstellt daraus ein größeres Pixel. Geben Sie die Auflösung Ihres Ausgabegeräts in dpi (Dots per Inch, Punkte pro Zoll) an und geben Sie in das Feld „Für Auflösungen über“ eine Auflösung in dpi ein. Für Bilder mit einer Auflösung über diesem Grenzwert kombiniert PDF Generator Pixel wie benötigt, um die Auflösung des Bildes (Pixel pro Zoll) auf die angegebene dpi-Einstellung zu reduzieren. Um die Neuberechnung zu deaktivieren, wählen Sie „Aus“ aus. Die Optionen lauten:

**Durchschnittliche Neuberechnung auf:** Durchschnittlich werden die Pixel in einem Beispielbereich angezeigt und der gesamte Bereich wird durch die durchschnittliche Pixelfarbe mit der angegebenen Auflösung ersetzt.

**Bikubische Neuberechnung zu:** Verwendet einen gewichteten Durchschnitt zur Bestimmung der Pixelfarbe und liefert in der Regel bessere Ergebnisse als die einfache Mittelungsmethode zum Neuberechnen. Die bikubische Methode ist die langsamste, jedoch präziseste Methode und führt zu den feinsten tonlichen Abstufungen.

**Subsampling zu:** Wählt ein Pixel in der Mitte des Beispielbereichs aus und ersetzt den gesamten Bereich mit diesem Pixel in der angegebenen Auflösung. Die Kurzberechnung verkürzt im Vergleich zur Neuberechnung die Konvertierungsdauer beträchtlich, führt jedoch zu weniger feinen bzw. regelmäßigen Bildern.

Die Auflösungseinstellung für Farben und Graustufen muss dem 1,5- bis 2-fachen der Rasterweitenlinierung entsprechen, mit der die Datei gedruckt wird. (Vorausgesetzt, Sie unterschreiten nicht diese empfohlene Auflösungseinstellung, sind Bilder ohne Geraden bzw. geometrische oder sich wiederholende Muster nicht von einer niedrigeren Auflösung betroffen.) Die Auflösung von Schwarzweißbildern muss derjenigen des Ausgabegeräts entsprechen. Beachten Sie jedoch, dass sich durch das Speichern eines Schwarzweißbildes mit einer höheren Auflösung als 1500 dpi die Dateigröße erhöht, ohne dass sich die Bildqualität spürbar verbessert.

Berücksichtigen Sie auch, ob Benutzer eine Seite vergrößern müssen. Wenn Sie beispielsweise ein PDF-Dokument einer Karte erstellen, sollten Sie eine höhere Bildauflösung erwägen, damit Benutzer einen Kartenausschnitt vergrößern können.

>[!NOTE]
>
>Das Neuberechnen von Schwarzweißbildern kann bei der Anzeige zu unerwarteten Ergebnissen führen, z. B. keiner Bildanzeige. Tritt dieses Problem auf, deaktivieren Sie die Neuberechnung und konvertieren Sie die Datei erneut. Dieses Problem tritt am ehesten bei der Kurzberechnung und am ehesten nicht bei der bikubischen Neuberechnung auf.

Diese Tabelle zeigt die Typen von Druckern und ihre in dpi gemessene Auflösung, ihre standardmäßige Rasterweite in lpi (Lines per Inch, Zeilen pro Zoll) und eine Neuberechnungsauflösung für Bilder gemessen in ppi (Pixel per Inch, Bildpunkte pro Zoll). Wenn die Druckausgabe beispielsweise auf einem 600-dpi-Laserdrucker erfolgt, müssen Sie 170 als die Auflösung eingeben, mit der Bilder neu berechnet werden sollen.

<table>
 <tbody>
  <tr>
   <th><p>Druckerauflösung</p> </th>
   <th><p>Standardrasterweite</p> </th>
   <th><p>Bildauflösung</p> </th>
  </tr>
  <tr>
   <td><p>300 dpi (Laserdrucker)</p> </td>
   <td><p>60 lpi</p> </td>
   <td><p>120 ppi</p> </td>
  </tr>
  <tr>
   <td><p>600 dpi (Laserdrucker)</p> </td>
   <td><p>85 lpi</p> </td>
   <td><p>170 ppi</p> </td>
  </tr>
  <tr>
   <td><p>1200 dpi (Filmbelichter)</p> </td>
   <td><p>120 lpi</p> </td>
   <td><p>240 ppi</p> </td>
  </tr>
  <tr>
   <td><p>2400 dpi (Filmbelichter)</p> </td>
   <td><p>150 lpi</p> </td>
   <td><p>300 ppi</p> </td>
  </tr>
 </tbody>
</table>

**Komprimierung:** Legen Sie einen Wert fest, der auf Farb-, Graustufen- und Schwarzweißbilder angewendet werden soll. Legen Sie für Farb- und Graustufenbilder auch die Bildqualität fest:

* Wählen Sie für Farb- und Graustufenbilder die Option „ZIP“ aus, um eine Komprimierung anzuwenden, die bei Bildern mit großen einfarbigen Bereichen oder sich wiederholenden Mustern gut funktioniert, z. B. bei Screenshots, einfachen mit Malprogrammen erstellten Bildern und Schwarzweißbildern mit sich wiederholenden Mustern. Wählen Sie „JPEG“ (Qualität: minimal bis maximal), um eine für Farb- und Graustufenbilder geeignete Komprimierung anzuwenden, z. B. für Halbtonfotos mit höherem Detailgrad, die auf dem Bildschirm oder gedruckt abgebildet werden können. Wählen Sie „Automatisch (JPEG)“ aus, um die für Farb- und Graustufenbilder die optimale Qualität automatisch bestimmen zu lassen.
* Wählen Sie für Schwarzweißbilder die Komprimierung „CCITT Gruppe 4“, „CCITT Gruppe 3“, „ZIP“, „JPEG200“, „Automatisch (JPEG2000)“ oder „Run Length“.

Stellen Sie sicher, dass Schwarzweißbilder nicht als Graustufenbilder gescannt werden. Gescannter Text wird mitunter standardmäßig als Graustufenbild gespeichert. Mit der JPEG-Komprimierung komprimierter Graustufentext ist unscharf und ggf. unleserlich.

**Bildqualität:** Konfiguriert die Bildqualität für Farb- und Graustufenbilder. Die Optionen lauten „Minimal“, „Niedrig“, „Mittel“, „Hoch“ und „Maximal“.

**Glätten: Glättet gezackte Kanten in Schwarzweißbildern.** Wählen Sie „2 Bit“, „4 Bit“ oder „8 Bit“, um 4, 16 oder 256 Graustufen anzugeben. (Dieses Verfahren kann bewirken, dass kleine Schriftgrade oder dünne Linien unklar aussehen.)

>[!NOTE]
>
>Die Komprimierung von Text und Strichgrafiken ist stets aktiviert.

**Bildrichtlinie:** Legen Sie eine Richtlinie für Farb-, Graustufen- und Schwarzweißbilder fest. Wenn die Bildauflösung unter der angegebenen Auflösung liegt, können Sie dennoch fortfahren (die Option „Ignorieren“ auswählen), eine Warnmeldung bereitstellen oder den Auftrag abbrechen.

## Schriftartoptionen  {#fonts-options}

Die Schriftartoptionen dienen dazu, anzugeben, welche Schriftarten in eine PDF-Datei eingebettet werden sollen und ob eine Teilmenge von in der PDF-Datei verwendeten Zeichen eingebettet werden soll. Weitere Informationen zum Zugriff auf die Schrifteinstellungen finden Sie unter [PDF-Einstellungen hinzufügen und bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

>[!NOTE]
>
>Wenn Sie PDF-Dateien mit derselben Schriftartteilmenge kombinieren, versucht PDF Generator, die Schriftartteilmengen zu kombinieren.

**Alle Schriften einbetten:** Bettet alle in der Datei verwendeten Schriften ein. Die Schrifteinbettung ist für die Erfüllung der PDF/X-Anforderungen erforderlich.

**Eingebettete Schriften, wenn der Prozentsatz der verwendeten Zeichen kleiner ist:** Wenn Sie diese Option wählen, geben Sie einen Schwellenwert-Prozentsatz an, um nur eine Untergruppe der Schriften einzubetten. Wenn beispielsweise der Schwellenwert 35 ist und weniger als 35 % der Zeichen verwendet werden, bettet PDF Generator nur diese Zeichen ein. Es werden nur Schriften mit entsprechenden Berechtigungsbits eingebettet.

**Bei Fehler beim Einbetten:** Gibt an, wie PDF Generator reagiert, wenn beim Verarbeiten einer Datei keine einzubettende Schrift gefunden wird. Die folgenden Möglichkeiten stehen zur Verfügung: PDF Generator kann entweder die Anforderung ignorieren und die Schrift ersetzen, Sie warnen und die Schrift ersetzen oder die Verarbeitung des aktuellen Auftrags abbrechen.

**Schriftquelle:** Der Speicherort der von PDF Generator verwendeten Schriftarten.

### Einzubettende Schriften angeben {#specify-which-fonts-to-embed}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Adobe PDF-Einstellungen“.
1. Klicken Sie auf „Neu“ oder auf den Namen einer Einstellung.
1. Klicken Sie auf „Schriften“ und deaktivieren Sie „Alle Schriften“ einbetten.
1. Wählen Sie in der Liste „Schriftquelle“ eine Quelle aus und klicken Sie auf „Los“, um die Liste der Schriften im Feld auf der linken Seite zu aktualisieren.
1. Klicken Sie auf eine Schrift im linken Feld. Klicken Sie dann auf „Hinzufügen“ neben dem entsprechenden Feld, um diese Schrift in die Liste „Immer einbetten“ oder „Nie einbetten“ zu verschieben. Wiederholen Sie diesen Schritt für jede Schrift. Halten Sie beim Klicken die Strg-Taste gedrückt, um mehrere zu verschiebende Schriften auszuwählen.
1. Um eine Schrift aus der Liste „Immer einbetten“ bzw. „Nie einbetten“ zu entfernen, wählen Sie sie aus und klicken Sie neben dem entsprechenden Feld auf „Entfernen“. Dadurch wird die Schrift nicht aus dem System, sondern nur der Verweis darauf aus der Liste entfernt.
1. Wenn die gewünschte Schrift nicht angezeigt wird, geben Sie ihren Namen in das Feld „Schrift hinzufügen“ ein und klicken Sie anschließend auf „Immer einbetten“ bzw. „Nie einbetten“. Schriftnamen dürfen keine numerischen Zeichen enthalten.

>[!NOTE]
>
>Eine TrueType-Schrift kann eine vom Entwickler der Schrift hinzugefügte Einstellung enthalten, die verhindert, dass die Schrift in PDF-Dateien eingebettet werden kann.

>[!NOTE]
>
>Schriftarten werden aus dem Windows-Systemschriftarten-Cache ausgewählt, und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.

## Farboptionen  {#color-options}

Die Farboptionen legen alle Informationen für das Farbmanagement für PDF Generator fest. Weitere Informationen zum Zugriff auf die Farboptionen finden Sie unter [PDF-Einstellungen hinzufügen und bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

### Adobe-Farbeinstellungen  {#adobe-color-settings}

**Einstellungsdatei:** Diese Liste enthält eine Liste von Farbeinstellungen, die auch in gängigen Grafikprogrammen wie Adobe Photoshop und Adobe Illustrator verwendet werden. Die ausgewählte Farbeinstellung bestimmt die anderen Adobe-Farbeinstellungen auf dieser Seite. Wenn Sie beispielsweise eine andere Einstellung als „Ohne“ auswählen, sind alle Optionen (außer für „Geräteabhängige Daten“) vordefiniert und abgeblendet. Sie können die Einstellungen „Farbmanagement“ und „Arbeitsfarbräume“ nur bearbeiten, wenn Sie für „Einstellungsdatei“ die Option „Ohne“ auswählen.

### Farbmanagement-Richtlinien {#color-management-policies}

Wenn Sie für „Einstellungsdatei“ die Option „Ohne“ ausgewählt haben, gibt der Bereich „Farbmanagement“ an, wie PDF Generator nicht verwaltete Farben in einer PostScript-Datei konvertiert.

**Farbe unverändert lassen:** Behält geräteabhängige Farben unverändert bei und behält geräteunabhängige Farben als nächstmögliche Entsprechung in PDF bei. Diese Option eignet sich für Druckereien, die alle ihre Geräte kalibriert haben, diese Informationen zum Angeben von Farben in der Datei genutzt haben und alle Druckaufträge nur auf diesen Geräten ausgeben.

**Alles für Farbmanagement kennzeichnen:** Bettet ein Profil des International Color Consortium ein, wenn Dateien destilliert werden, und kalibriert Farben in den Bildern, wodurch Farben in den resultierenden PDF-Dateien geräteunabhängig werden, wenn Sie die Kompatibilität mit Acrobat 4 (PDF 1.3) oder höher ausgewählt haben. Geräteabhängige Farbräume in Dateien (RGB, Grayscale und CMYK) werden jedoch in geräteunabhängige Farbräume (CalRGB, CalGray und LAB) konvertiert.

**Nur Bilder für Farbmanagement kennzeichnen:** Bettet ICC-Profile nur bei Auswahl der Acrobat 4 (PDF 1.3)-Kompatibilität in Bilder, nicht in Text oder Grafiken ein. Diese Option verhindert, dass schwarzer Text Farbverschiebungen unterzogen wird. Geräteabhängige Farbräume in Bildern (RGB, Grayscale und CMYK) werden jedoch in geräteunabhängige Farbräume (CalRGB, CalGray und LAB) konvertiert. Text und Grafiken werden nicht konvertiert.

**Alle Farben in sRGB konvertieren oder Alle Farben in CMYK konvertieren:** Kalibriert die Farbe in der Datei, wodurch die Farbe geräteunabhängig ist, ähnlich wie bei &quot;Alles für Farbmanagement kennzeichnen&quot;. Wenn Sie eine Kompatibilität mit Acrobat 4 (PDF 1.3) oder höher ausgewählt haben und eine Konvertierung in sRGB ausführen, werden CMYK- und RGB-Bilder in sRGB konvertiert.

Unabhängig von der ausgewählten Kompatibilitätsoption bleiben Graustufenbilder unverändert. Dadurch wird bei PDF-Dateien die Größe verringert und die Anzeige beschleunigt, da zum Beschreiben von RGB-Bilder weniger Informationen als zum Beschreiben von CMYK-Dateien benötigt werden. Da RGB der von Monitoren verwendete native Farbraum ist, muss während der Anzeige keine Farbkonvertierung erfolgen, wodurch die Online-Anzeige beschleunigt wird. Diese Option wird empfohlen, wenn die PDF-Datei online auf Druckern mit niedriger Auflösung verwendet wird.

**Dokument Rendering Intent:** Die Methode, mit der Farben zwischen Farbräumen zugeordnet werden. Das Ergebnis einer bestimmten Methode hängt von den Profilen der Farbräume ab. Einige Profile liefern beispielsweise bei unterschiedlichen Methoden identische Ergebnisse. Die folgenden Optionen stehen zur Auswahl:  

>[!NOTE]
>
>In allen Fällen können Bedingungen ggf. von Farbmanagementvorgängen ignoriert oder außer Kraft gesetzt werden, die im Anschluss an die Erstellung der PDF-Datei erfolgen.

**Beibehalten:** Das bedeutet, dass die Absicht im Ausgabegerät und nicht in der PDF-Datei angegeben wird. Bei vielen Ausgabegeräten ist „Relativ farbmetrisch“ die Standardbedingung.

**Perzeptiv:** Behält die relativen Farbwerte unter den Originalpixeln bei, während sie dem Zielfarbumfang zugeordnet werden. Bei dieser Methode bleibt die optische Beziehung zwischen Farben erhalten, obgleich die Farbwerte selbst sich ggf. ändern.

**Sättigung:** Behält die relativen Sättigungswerte der ursprünglichen Pixel bei. Diese Methode eignet sich für Geschäftsgrafiken, bei denen die exakte Beziehung zwischen Farben nicht so wichtig ist wie das Vorhandensein leuchtender gesättigter Farben.

**Relativ farbmetrisch:** Ordnet den weißen Punkt des Quellraums dem weißen Punkt des Zielraums zu.

**Absolut farbmetrisch:** Deaktiviert beim Konvertieren von Farben die Übereinstimmung von weißen und schwarzen Punkten. Diese Methode wird nicht empfohlen, es sei denn, Sie müssen Signaturfarben erhalten, z. B. in Warenzeichen oder Logos.

### Arbeitsfarbräume {#working-spaces}

Wählen Sie für alle Werte in der Liste unter „Farbmanagement“ außer „Farbe unverändert lassen“ Optionen in den Listen im Bereich „Arbeitsfarbraum“ aus, um anzugeben, welche ICC-Profile für die Definition und Kalibrierung der Graustufen-, RGB- und CMYK-Farbräume in untersuchten PDF-Dateien verwendet werden. Die folgenden Optionen stehen zur Auswahl:

**Grau:** Definiert den Farbraum aller Graustufenbilder in Dateien. Diese Option ist nur verfügbar, wenn Sie „Alles für Farbmanagement kennzeichnen“ oder „Nur Bilder für Farbmanagement kennzeichnen“ auswählen. Das standardmäßige ICC-Profil für Graustufenbilder ist Gray Gamma 2.2. Sie können auch „Ohne“ wählen, um die Konvertierung von Graustufenbildern zu verhindern.

**RGB:** Definiert den Farbraum aller RGB-Bilder in Dateien. Die Standardeinstellung „sRGB IEC61966-2.1“ ist meist eine gute Wahl, da diese Einstellung sich zum Industriestandard entwickelt, der von vielen Ausgabegeräten erkannt wird. Sie können auch „Ohne“ auswählen, um das Konvertieren von RGB-Bildern zu verhindern.

**CMYK:** Definiert den Farbraum aller CMYK-Bilder in Dateien. Die Standardeinstellung ist „U.S. Web Coated (SWOP) v2“. Sie können auch „Ohne“ auswählen, um das Konvertieren von CMYK-Bildern zu verhindern.

>[!NOTE]
>
>Die Auswahl von „Ohne“ für alle drei Arbeitsfarbräume hat dieselbe Auswirkung wie die Auswahl von „Farbe unverändert lassen“.

**CMYK-Werte für kalibrierte CMYK-Farbräume beibehalten:** Bei Auswahl dieser Option werden geräteunabhängige CMYK-Werte als geräteabhängige (DeviceCMYK-) Werte behandelt, geräteunabhängige Farbräume verworfen und PDF/X-1a-Dateien verwenden den Wert &quot;Alle Farben in CMYK konvertieren&quot;. Falls nicht ausgewählt, werden geräteunabhängige Farbräume in CMYK konvertiert, wenn das Farbmanagement auf „Alle Farben in CMYK konvertieren“ festgelegt ist.

### Geräteabhängige Daten  {#device-dependent-data}

Diese Einstellungen gelten, wenn Sie mit Dokumenten arbeiten, die mit professionellen Dokumentations- und Grafikanwendungen wie Adobe Illustrator oder Adobe InDesign erstellt wurden. Weitere Informationen finden Sie in der Dokumentation der jeweiligen Anwendung.

Übertragungsfunktionen werden für künstlerische Effekte und zum Anpassen an die technischen Bedingungen eines bestimmten Ausgabegeräts verwendet. Eine Datei, die auf einem bestimmten Filmbelichter ausgegeben werden soll, kann beispielsweise Übertragungsfunktionen aufweisen, welche den diesem Filmbelichter inhärenten Tonwertzuwachs ausgleichen.

**Unterfarbreduktion und Schwarzaufbau beibehalten:** Behält diese Einstellungen bei, wenn sie in der PostScript-Datei vorhanden sind. Der Schwarzaufbau berechnet die benötigte Menge an Schwarz, wenn versucht wird, eine bestimmte Farbe zu reproduzieren. Die Unterfarbreduktion reduziert die Menge an Zyan-, Magenta-, und Gelbkomponenten, um die Menge an Schwarz auszugleichen, die vom Schwarzaufbau hinzugefügt wurde. Da weniger Druckfarbe benötigt wird, wird die Unterfarbreduktion im Allgemeinen für Zeitungspapier und ungestrichenen Ganzstoff verwendet.

**Wenn Übertragungsfunktionen gefunden werden:** Legt fest, was zu tun ist, wenn Übertragungsfunktionen gefunden werden:

**Beibehalten:** Behält die Übertragungsfunktionen bei, die traditionell zum Ausgleich von Tonwertzuwachs oder Tonwertverlust verwendet werden, die beim Übertragen eines Bildes auf den Film auftreten können. Ein Tonwertzuwachs erfolgt, wenn die Druckfarbpunkte, die ein gedrucktes Bild bilden (z. B. aufgrund der Verteilung auf Papier) größer als im Halbtonraster sind. Zu einem Tonwertverlust kommt es, wenn die Punkte kleiner gedruckt werden. Bei dieser Option werden die Übertragungsfunktionen als Teil der Datei beibehalten und auf die Datei angewendet, sobald diese ausgegeben wird.

**Anwenden:** Die Übertragungsfunktion bleibt erhalten, wendet sie jedoch auf die Datei an, wodurch die Farben in der Datei geändert werden. Diese Option ist nützlich, um Farbeffekte in einer Datei zu erstellen. In der Standardeinstellung ist diese Option für neue Einstellungen aktiviert.

**Entfernen:** Entfernt alle angewendeten Übertragungsfunktionen. Entfernen Sie angewendete Übertragungsfunktionen, es sei denn, die PDF-Datei soll auf demselben Gerät ausgegeben werden, für das die PostScript-Quelldatei erstellt wurde.

**Halbtoninformationen beibehalten:** Behält alle Halbtoninformationen in Dateien bei. Halbtoninformationen bestehen aus Punkten, die steuern, wie viel Druckfarbe von Halbtongeräten an einer bestimmten Stelle auf dem Papier aufgebracht wird. Durch Variieren der Punktgröße und -dichte wird die Illusion von Variationen grauer bzw. einheitlicher Farbe erzeugt. Für ein CMYK-Bild werden vier Halbtonraster verwendet, eine für jede beim Druckvorgang verwendete Druckfarbe.

Bei einem herkömmlichen Druckvorgang wird ein Halbton produziert, indem ein Halbtonraster zwischen einem Stück Film und dem Bild platziert und der Film anschließend belichtet wird. Entsprechende elektronische Produkte, z. B. Adobe Photoshop, ermöglichen dem Benutzer die Angabe der Attribute des Halbtonrasters, bevor der Film oder die Papierausgabe produziert wird. Halbtoninformationen beschränken sich auf ein bestimmtes Ausgabegerät.

## Erweiterte Optionen  {#advanced-options}

Die erweiterten Optionen bestimmen, welche DSC-Kommentare (Document Structuring Conventions) in der PDF-Datei beibehalten werden sollen und wie andere Optionen festgelegt werden, die sich auf die Konvertierung aus PostScript auswirken. In einer PostScript-Datei enthalten DSC-Kommentare Informationen zur Datei (z. B. die Quellanwendung, das Erstellungsdatum und die Seitenausrichtung). Sie stellen außerdem eine Struktur für Seitenbeschreibungen in der Datei bereit (beispielsweise Anweisungen zum Anfang und Ende eines Vorwortabschnitts). DSC-Kommentare können nützlich sein, wenn ein Dokument in Druck gehen soll. Weitere Informationen zum Zugriff auf die erweiterten Optionen finden Sie unter [PDF-Einstellungen hinzufügen und bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Für das Arbeiten mit den erweiterten Optionen ist es hilfreich, mit der Sprache PostScript und ihrer Übersetzung in PDF vertraut zu sein. (Siehe [Adobe PostScript 3](https://www.adobe.com/products/postscript/main.html).)

**PostScript-Datei darf Adobe PDF-Einstellungen überschreiben:** Verwendet Einstellungen, die in einer PostScript-Datei gespeichert sind, anstelle der aktuellen Adobe PDF-Einstellungsdatei. Vor der Verarbeitung einer PostScript-Datei können Sie der Datei Parameter hinzufügen, um folgende Aspekte zu steuern:

* Komprimierung von Text und Grafiken
* Neuberechnung und Kodierung ausgewählter Bilder
* Einbetten von Type 1-Schriften und Vorkommen von Type 1 Multiple Master-Schriften

**PostScript XObjects zulassen:** PostScript XObjects speichern Informationen, die auf vielen Seiten der gleichen Datei angezeigt werden, wie ein Hintergrundbild oder Kopf- und Fußzeileninformationen. Das Verwenden von PostScript XObjects kann zu einem schnelleren Druck führen, belegt aber mehr Druckerspeicher. Um das Erstellen von PostScript XObjects zu verhindern, deaktivieren Sie diese Option, wenn Sie PDF-Dateien mit einer Kompatibilität mit Acrobat 5 (PDF 1.4) oder höher erstellen.

**Farbverläufe in Smooth-Schattierungen konvertieren:** Konvertiert Farbverläufe für Acrobat 4 und höher in glatte Schattierungen, wodurch PDF-Dateien kleiner werden und möglicherweise die Qualität der endgültigen Ausgabe verbessert wird. PDF Generator konvertiert Farbverläufe aus Adobe Illustrator, Adobe InDesign, Adobe Freehand MX, CorelDraw, Quark XPress und Microsoft PowerPoint.

**Smooth-Linien in Kurven konvertieren:** Reduziert die Anzahl der Steuerpunkte, die zum Erstellen von Kurven in CAD-Zeichnungen verwendet werden, was zu kleineren PDFs und einer schnelleren Bildschirmwiedergabe führt.

**Level 2 Copypage Semantics beibehalten:** Verwendet den Copypage-Operator, der in LanguageLevel 2 PostScript anstatt in LanguageLevel 3 PostScript definiert ist. Wenn Sie eine PostScript-Datei haben und diese Option aktivieren, kopiert ein Copypage-Operator die Seite. Ist diese Option nicht aktiviert, wird die Entsprechung eines Showpage-Vorgangs ausgeführt, ohne dass der Grafikstatus erneut initialisiert wird.

**Überdruckeinstellungen beibehalten:** Behält alle Überdruckeinstellungen in Dateien bei, die in PDF konvertiert werden. Überdruckte Farben sind zwei oder mehr übereinander gedruckte Druckfarben. Wenn beispielsweise die Druckfarbe Zyan über die Druckfarbe Gelb gedruckt wird, hat der resultierende Überdruck die Farbe Grün. Ohne Überdrucken würde das zugrunde liegende Gelb nicht, sondern nur die Farbe Zyan gedruckt.

**Überdruckstandard ist Nicht-Null-Überdrucken:** Verhindert, dass überdruckte Objekte mit 0 CMYK-Werten CMYK-Objekte, die sich darunter befinden, ausschließen. Dieser Effekt wird erreicht, indem der Grafikstatusparameter OPM 1 an den Stellen in die PDF-Datei eingefügt wird, an denen der Operator Setoverprint vorhanden ist.

**Adobe PDF-Einstellungen in PDF-Datei speichern:** Bettet die Einstellungsdatei ein, die zum Erstellen der PDF-Datei verwendet wird. Sie können die Einstellungsdatei (mit der Erweiterung „.joboptions“) im Dialogfeld „Dateianlagen“ in Acrobat öffnen und anzeigen. Die Adobe PDF-Einstellungsdatei wird zum Element der Struktur „EmbeddedFiles“ in der PDF-Datei.

**Ursprüngliche JPEG-Bilder nach Möglichkeit im PDF-Format speichern:** Verarbeitet komprimierte JPEG-Bilder (Bilder, die bereits mit der DCT-Kodierung komprimiert wurden), ohne sie erneut zu komprimieren. Ist diese Option aktiviert, dekomprimiert PDF GeneratorJPEG-Bilder, um sicherzustellen, dass sie fehlerfrei sind. Gültige Bilder werden dagegen nicht erneut komprimiert, weshalb bei der Verarbeitung das Originalbild unberührt bleibt. Wird diese Option aktiviert, verbessert sich die Leistung, da nur eine De- und keine Rekomprimierung erfolgt und die Bild- und Metadaten beibehalten bleiben.

**Portable Job Ticket in PDF-Datei speichern: Behält ein PostScript-Auftragsticket in einer PDF-Datei** bei. Das Job Ticket enthält Informationen zur PostScript-Datei, z. B. Papierformat, Auflösung und Überfüllungsinformationen, statt Informationen zum Inhalt. Diese Informationen können später in einem Workflow oder zum Drucken der PDF-Datei verwendet werden.

**Verwenden Sie Prologue.ps und Epilogue.ps:** Sendet für jeden Auftrag eine Prologue- und Epilogue-Datei. Diese Dateien haben vielfältige Zwecke. Prologue-Dateien können beispielsweise so bearbeitet werden, dass Umschlagseiten angegeben werden. Epilogue-Dateien können so bearbeitet werden, dass eine Folge von Prozeduren in einer PostScript-Datei aufgelöst wird. Die Dateien können hoch- und heruntergeladen werden. (Siehe Hochladen und Herunterladen von Prologue- und Epilogue-Dateien.)

**DSC-Kommentare verarbeiten: DSC-Informationen aus einer PostScript-Datei werden** beibehalten. Diese Unteroptionen lauten wie folgt:

**DSC-Warnungen protokollieren:** Zeigt Warnmeldungen zu problematischen DSC-Kommentaren während der Verarbeitung an und fügt sie einer Protokolldatei hinzu.

**EPS-Informationen von DSC beibehalten:** Behält Informationen wie die ursprüngliche Anwendung und das Erstellungsdatum einer EPS-Datei bei. Ist diese Option deaktiviert, werden die Größe und Mitte der Seite basierend auf der linken unteren Ecke des linken unteren Objekts und der rechten unteren Ecke des rechten unteren Objekts auf der Seite bestimmt.

**OPI-Kommentare beibehalten:** Behält Informationen bei, die erforderlich sind, um ein FPO-Bild (For Placement Only) oder einen Kommentar durch das hochauflösende Bild auf Servern zu ersetzen, die Open Prepress Interface (OPI)-Versionen 1.3 und 2.0 unterstützen.

**Informationen zum Dokument von DSC beibehalten:** Behält Informationen wie Titel, Erstellungsdatum und -zeit bei. Wenn Sie eine PDF-Datei in Acrobat öffnen, werden diese Informationen im Bereich „Dokumenteigenschaften“ unter „Beschreibung“ angezeigt.

**Größe der Seite ändern und Bildmaterial für EPS-Dateien zentrieren:** Zentriert ein EPS-Bild und passt die Größe der Seite an die Größe des Bildes an. Diese Option gilt nur für Aufträge, die aus einer einzelnen EPS-Datei bestehen.

## Optionen für „Standards - Berichterstellung und Kompatibilität“  {#standards-reporting-and-compliance-options}

PDF Generator kann den Dokumentinhalt in einer PostScript-Datei überprüfen, um sicherzustellen, dass diese vor dem Erstellen der PDF-Datei die PDF/X-1a-, PDF/X-3 oder PDF/A-Standardkriterien erfüllen. Für PDF/X-kompatible Dateien können Sie auch festlegen, dass die PostScript-Datei zusätzliche Kriterien erfüllt, indem Sie andere Optionen unter „Standards – Berichterstellung und Kompatibilität“ auswählen. Die Verfügbarkeit der Optionen hängt vom ausgewählten Standard ab.

PDF/X-konforme Dateien werden hauptsächlich als standardisiertes Format für den Austausch von PDF-Dateien verwendet, die mit hoher Auflösung gedruckt werden sollen. Wenn Sie ein PDF-Dokument erstellen, das nicht als Druckerzeugnis gedacht ist, können Sie die PDF/X-Standards ignorieren.

PDF/A-kompatible Dateien dienen hauptsächlich zur Archivierung. Da die langfristige Erhaltung das Ziel ist, muss das Dokument nur die Informationen enthalten, die für die geplante Nutzungsdauer des Dokument zum Öffnen und Anzeigen erforderlich sind. PDF/A-konforme Dateien dürfen beispielsweise nur Text, Rasterbilder und Vektorobjekte und keine Verschlüsselung oder Skripte enthalten. Darüber hinaus müssen alle Schriftarten so eingebettet sein, dass die Dokumente ihrer Erstellung entsprechend geöffnet und angezeigt werden können. PDF/A-konforme Dokumente sind daher *schlanker* als ihre PDF/X-Entsprechungen, die für die Herstellung von Druckerzeugnissen vorgesehen sind.

>[!NOTE]
>
>Wenn Sie einen überwachten Ordner für die Erstellung PDF/A-konformer Dateien einrichten, darf der Ordner nicht mit Sicherheitseinstellungen versehen werden, da der PDF/A-Standard keine Verschlüsselung zulässt.

Weitere Informationen zum Zugriff auf die Optionen zu „Standards - Berichterstellung und Kompatibilität“ finden Sie unter [PDF-Einstellungen hinzufügen und bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

**Kompatibilitätsstandard:** Wählen Sie einen Standard aus, um einen Bericht zu erstellen, der angibt, ob die Datei die Anforderungen erfüllt und, falls nicht, welche Probleme aufgetreten sind. Wenn „Kompatibilität“ auf der Seite „Allgemeine Einstellungen“ auf „Acrobat 4.0“ festgelegt ist, sind alle folgenden Optionen aktiviert. Wenn „Kompatibilität“ auf „Acrobat 5.0“ festgelegt ist, können nur die Acrobat 5.0-Optionen ausgewählt werden. Wenn „Kompatibilität“ auf eine andere Option festgelegt ist, sind die folgenden Optionen abgeblendet:

* PDF/X-1a (kompatibel mit Acrobat 4.0)
* PDF/X-3 (kompatibel mit Acrobat 4,0)
* PDF/X-1a (kompatibel mit Acrobat 5.0)
* PDF/X-3 (kompatibel mit Acrobat 5.0)
* PDF/A-1b (kompatibel mit Acrobat 5.0)

### Optionen für PDF/X-Standards  {#options-for-pdf-x-standards}

**Wenn nicht konform:** Gibt an, ob die PDF-Datei erstellt werden soll, wenn die PostScript-Datei die PDF/X-Anforderungen nicht erfüllt. Diese Option ist verfügbar, wenn auf der Seite „Standards - Berichterstellung und Kompatibilität“ die Option „Kompatibilitätsstandard“ auf eine andere Option als „Ohne“ festgelegt ist.

**Weiter:** Erstellt eine PDF-Datei.

**Auftrag abbrechen:** Erstellt eine PDF-Datei nur, wenn die PostScript-Datei die PDF/X-Anforderungen der ausgewählten Berichtoptionen erfüllt und ansonsten gültig ist. Wenn sowohl PDF/X-Berichtsoptionen ausgewählt sind und die PostScript-Datei nur eine Teilmenge der PDF/X-Kriterien erfüllt (z. B. PDF/X-3), erstellt PDF Generator > die konforme Datei.

**Wenn weder Endformatrahmen noch Objektrahmen angegeben sind:** Verfügbar, wenn auf der Seite &quot;Berichte und Kompatibilität&quot;die Option &quot;Kompatibilitätsstandard&quot;auf eine andere Option als &quot;Ohne&quot;eingestellt ist.

**Als Fehler melden:** Kennzeichnet die PostScript-Datei als nicht kompatibel, wenn eine der Optionen für den Berichte ausgewählt ist und auf jeder Seite ein Endformat- oder Objektrahmen fehlt.

**Endformatrahmen auf Medienrahmen mit Abständen festlegen:** Berechnet Werte in Punkten für den Endformatrahmen basierend auf den Abständen für den Medienrahmen der jeweiligen Seiten, wenn weder der Endformatrahmen noch der Objektrahmen angegeben sind. Der Endformatrahmen ist stets genau so klein wie oder kleiner als der umgehende Medienrahmen.

**Wenn Anschnittrahmen nicht angegeben ist:** Verfügbar, wenn auf der Seite &quot;Standards&quot;auf &quot;Berichte und Kompatibilität&quot;die Option &quot;Kompatibilitätsstandard&quot;auf eine andere Option als &quot;Ohne&quot;eingestellt ist.

**Anschnittrahmen auf Medienrahmen festlegen:** Verwendet die Medienfeldwerte für den Anschnittrahmen, wenn der Anschnittrahmen nicht angegeben ist.

**Anschnittrahmen auf Endformatrahmen mit Abständen festlegen:** Berechnet Werte in Punkten für den Anschnittrahmen basierend auf den Abständen für den Endformatrahmen der entsprechenden Seiten, wenn der Anschnittrahmen nicht angegeben ist. Der Anschnittrahmen ist stets genau so groß wie oder größer als der umgehende Endformatrahmen.

**Standardwerte, wenn im Dokument nicht angegeben:** Diese Option ist verfügbar, wenn auf der Seite &quot;Standards und Kompatibilität&quot;die Option &quot;Kompatibilitätsstandard&quot;auf eine andere Option als &quot;Ohne&quot;eingestellt ist.

**Name des Output Intent-Profils:** Gibt die gekennzeichnete Druckbedingung an, für die das Dokument vorbereitet wurde. Wenn in einem Dokument keine Ausgabebedingung angegeben ist, verwendet PDF Generator den in diesem Menü ausgewählten Wert. Sie können einen der angebotenen Namen auswählen oder in das vorgesehene Feld einen Namen eingeben. Wenn Ihr Workflow erfordert, dass das Dokument die Ausgabebedingung angibt, wählen Sie „Ohne“ aus. Dokumente, die nicht die Anforderung erfüllen, bestehen nicht die Kompatibilitätsprüfung.

**Ausgabebedingungs-ID:** Gibt den Referenznamen an, der in der Registrierung des Profils für die Ausgabebedingung angegeben ist.

**Ausgabebedingung:** Beschreibt die beabsichtigte Druckbedingung. Dieser Eintrag kann für den vorgesehenen Empfänger des PDF-Dokuments nützlich sein.

**Registrierungsname (URL):** Gibt die Webadresse für weitere Informationen zur Registrierung an. Der URL wird für ICC-Registrierungsnamen automatisch eingegeben.

**Überfüllung:** Gibt den Überfüllungsstatus im Dokument an. Für die PDF/X-Kompatibilität ist der Wert „Wahr“ oder „Falsch“ erforderlich. Wenn das Dokument nicht den Überfüllungsstatus angibt, wird der hier angegebene Wert verwendet. Wenn Ihr Workflow es erfordert, dass das Dokument den Überfüllungsstatus angibt, wählen Sie „Nicht definiert“ aus. Dokumente, die nicht die Anforderung erfüllen, bestehen nicht die Kompatibilitätsprüfung.

### Optionen für PDF/A-Standards  {#options-for-pdf-a-standard}

Diese Optionen sind aktiviert, wenn „Kompatibilität“ (im Bereich „Allgemein“) auf „Acrobat 4“ (PDF 1.3) oder auf „Acrobat 5“ (PDF 1.4) festgelegt ist.

**Wenn nicht konform:** Gibt an, ob die PDF-Datei erstellt werden soll, wenn die PostScript-Datei nicht den PDF/A-Anforderungen entspricht.

**Weiter:** Erstellt eine PDF-Datei, auch wenn die PostScript-Datei die Anforderungen des Standards nicht erfüllt.

**Auftrag abbrechen:** Erstellt eine PDF-Datei nur, wenn die PostScript-Datei die PDF/A-Anforderungen erfüllt und ansonsten gültig ist.

**Name des Output Intent-Profils:** Gibt die gekennzeichnete Druckbedingung an, für die das Dokument vorbereitet wurde, und ist für die PDF/A-Kompatibilität erforderlich. Wenn Ihr Workflow es erfordert, dass das Dokument die Ausgabebedingung angibt, wählen Sie „Ohne“ aus. Das Dokument wird bei der Kompatibilitätsüberprüfung fehlschlagen, wenn diese Informationen nicht bereitgestellt werden.

**Ausgabebedingung:** Beschreibt die beabsichtigte Druckbedingung. Dieser Eintrag ist nicht erforderlich, kann aber verwendet werden, um nützliche Informationen für den vorgesehenen Empfänger der PDF-Datei bereitzustellen.

## Optionen für Ansicht beim Öffnen  {#initial-view-options}

Diese Optionen sind in drei Bereiche unterteilt: Dokumentoptionen, Fensteroptionen und Benutzeroberflächenoptionen. Weitere Informationen zu den Optionen für die Ansicht beim Öffnen finden Sie unter [PDF-Einstellungen hinzufügen und bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Um die Optionen zu verwenden, wählen Sie die Option „Einstellungen für Ansicht beim Öffnen festlegen“ aus.

### Dokumentoptionen  {#document-options}

Die Dokumentoptionen steuern die Darstellung des Dokuments innerhalb des Dokumentfensters, z. B. den Vergrößerungsgrad und das Bildlaufverhalten.

**Anzeigen:** Legt fest, welche Bereiche und Registerkarten standardmäßig im Anwendungsfenster angezeigt werden. „Lesezeichenfenster und Seite“ öffnet den Dokumentbereich und die Registerkarte „Lesezeichen“.

**Seitenlayout:** Legt fest, ob das Dokument im einseitigen, seitenweisen, kontinuierlichen oder fortlaufenden Modus angezeigt wird.

**Vergrößerung:** Legt den Zoomgrad fest, mit dem das Dokument beim Öffnen angezeigt wird. Die Standardeinstellung verwendet den vom Benutzer in den Acrobat- oder Adobe Reader-Voreinstellungen festgelegten Vergrößerungswert.

**&quot;Auf Seitenzahl öffnen&quot;:** Legt die Seite fest, auf der das Dokument geöffnet wird (normalerweise Seite 1).

>[!NOTE]
>
>Wenn „Standard“ für die Vergrößerungs- und Seitenlayoutoptionen gewählt wird, werden die in den Voreinstellungen für die Seitenanzeige festgelegten Einstellungen der einzelnen Benutzer in Acrobat oder Adobe Reader verwendet.

### Fensteroptionen  {#window-options}

Die Fensteroptionen legen fest, wie das Fenster an den Bildschirmbereich angepasst wird, wenn ein Benutzer das Dokument öffnet. Diese Optionen haben allerdings keine Auswirkungen, wenn ein PDF-Dokument in einem Webbrowser angezeigt wird.

**Fenstergröße auf Anfangsseite ändern:** Passt das Dokument entsprechend den unter &quot;Dokument-Optionen&quot;ausgewählten Optionen an, dass es sich an die Anfangsseite anpasst.

**Fenster auf Bildschirm zentrieren:** Positioniert das Fenster in der Mitte des Bildschirmbereichs.

**Im Vollbildmodus öffnen:** Maximiert das Dokument-Fenster und zeigt das Dokument ohne Menüleiste, Symbolleiste oder Fenstersteuerelemente an.

**Anzeigen:** Dateiname zeigt den Dateinamen in der Titelleiste des Fensters an. „Dokumenttitel“ zeigt den Dokumenttitel in der Titelleiste des Fensters an.

### Benutzeroberflächenoptionen {#user-interface-options}

Die Benutzeroberflächenoptionen bestimmen, welche Steuerelemente nach dem Öffnen des Dokuments angezeigt oder ausgeblendet werden.

**Menüleiste ausblenden:** Wenn diese Option aktiviert ist, wird die Menüleiste ausgeblendet

**Werkzeugleisten ausblenden:** Wenn diese Option aktiviert ist, werden die Werkzeugleisten ausgeblendet

**Fenstersteuerelemente ausblenden:** Wenn diese Option aktiviert ist, werden die Fenstersteuerelemente ausgeblendet

>[!NOTE]
>
>Wenn Sie die Menü- und Symbolleiste ausblenden, können die Benutzer keine Befehle anwenden und Werkzeuge auswählen, es sei denn, sie kennen die Tastenkombinationen, wenn sie die Datei in Acrobat öffnen.

## Prologue- und Epilogue-Dateien hochladen und herunterladen  {#uploading-and-downloading-prologue-and-epilogue-files}

Prologue-Dateien werden verwendet, um benutzerdefinierten PostScript-Code hinzuzufügen, der am Anfang jedes untersuchten PostScript-Auftrags ausgeführt wird. Epilogue-Dateien dienen dazu, benutzerdefinierten PostScript-Code hinzuzufügen, der am Ende jedes PostScript-Auftrags ausgeführt wird. Prologue- und Epilogue-Dateien können vom Server zum lokalen Speichern heruntergeladen werden. Sie können die Dateien herunterladen, um sie unabhängig voneinander zu konfigurieren oder um sie an einen anderen Speicherort oder auf einen anderen Computer zu übertragen.

Diese Dateien haben vielfältige Zwecke. Prologue-Dateien können beispielsweise so bearbeitet werden, dass Umschlagseiten angegeben werden. Epilogue-Dateien können so bearbeitet werden, dass eine Folge von Prozeduren in einer PostScript-Datei aufgelöst wird. Sie können außerdem die mit jedem Auftrag zu sendenden Prologue- und Epilogue-Dateien auswählen und hochladen.

### Eine Prologue- oder Epilogue-Datei herunterladen  {#download-a-prologue-or-epilogue-file}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Adobe PDF-Einstellungen“.
1. Klicken Sie auf „Neu“ oder auf den Namen einer Einstellung.
1. Klicken Sie auf „Erweitert“ und dann neben der Option „Prologue.ps und Epilogue.ps verwenden“ auf „Herunterladen“.
1. Klicken Sie auf der Seite „Prologue- und Epilogue-Dateien herunterladen“ auf „Prologue.ps“ bzw. „Epilogue.ps“ und anschließend auf „Speichern“.

### Eine Prologue- oder Epilogue-Datei hochladen  {#upload-a-prologue-or-epilogue-file}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Adobe PDF-Einstellungen“.
1. Klicken Sie auf „Neu“ oder auf den Namen einer Einstellung.
1. Klicken Sie auf „Erweitert“ und dann neben der Option „Prologue.ps und Epilogue.ps verwenden“ auf „Hochladen“.
1. Klicken Sie auf der Seite „Prologue- und Epilogue-Dateien hochladen“ auf „Durchsuchen“, um eine Prologue- oder Epilogue-Datei auszuwählen.
1. Suchen Sie die Datei und klicken Sie auf „Öffnen“.
1. Um die Datei zu verwenden, stellen Sie sicher, dass auf der Seite „Adobe PDF-Einstellung“ im Bereich „Neu/Bearbeiten“ im Abschnitt „Erweitert“ Prologue.ps und Epilogue.ps verwenden ausgewählt ist.
1. Klicken Sie auf „Speichern“.

>[!NOTE]
>
>PDF Generator unterstützt nur Prologue- und Epilogue-Dateien für die Konvertierung von PostScript- und EPS-Dateien (Encapsulated PostScript) in PDF.

