---
title: Konfigurieren von Adobe PDF-Einstellungen
description: Erfahren Sie, wie Sie die Adobe PDF-Einstellungen konfigurieren, die auf der Seite "Adobe PDF-Einstellungen"angezeigt werden. Sie können eine der vordefinierten PDF-Einstellungen verwenden oder eigene erstellen.
uuid: 980c9d6a-f75e-4e7d-b050-d2d07a10ef33
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ab018b6d-0233-4439-bb75-58c5421d769a
feature: PDF Generator
exl-id: 1bcb8429-c06e-4bd3-b422-4c512084dd09
source-git-commit: e2a3470784beb04c2179958ac6cb98861acfaa71
workflow-type: tm+mt
source-wordcount: '7282'
ht-degree: 35%

---

# Konfigurieren von Adobe PDF-Einstellungen{#configuring-adobe-pdf-settings}

Auf der Seite Adobe PDF-Einstellungen werden die Konvertierungseinstellungen angezeigt, die Sie für die zu verwendenden Quellen festlegen können. Sie können eine der vordefinierten PDF-Einstellungen verwenden oder eigene erstellen. Die PDF-Einstellungen bestimmen genau, wie Dateien konvertiert werden, sowie ihre resultierende PDF-Struktur und -Funktionen. Adobe PDF-Einstellungen wurden zuvor als Distiller®-Parameter oder Auftragsoptionen bezeichnet.

Auf der Seite &quot;Adobe PDF-Einstellungen&quot;können Sie die folgenden Aufgaben ausführen:

* Zeigen Sie die vordefinierten PDF-Einstellungen an. (Siehe [Über vordefinierte PDF-Einstellungen](configuring-pdf-settings.md#about-the-predefined-pdf-settings).
* Erstellen Sie eine PDF-Einstellung oder bearbeiten Sie eine, die Sie zuvor erstellt haben. (Siehe [PDF-Einstellungen hinzufügen oder bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).
* Geben Sie die standardmäßigen PDF-Einstellungen an. (Siehe [Standardeinstellungen ändern](/help/forms/using/admin-help/configuring-file-type-settings.md#change-the-default-settings))
* Laden Sie eine PDF-Einstellungsdatei auf den Server hoch. (Siehe [Hochladen von PDF-Einstellungen](configuring-pdf-settings.md#upload-pdf-settings).
* Löschen Sie benutzerdefinierte PDF-Einstellungen. (Siehe [PDF-Einstellungen löschen](configuring-pdf-settings.md#delete-pdf-settings).
* Laden Sie Prologue- und Epilogue-Dateien hoch und laden Sie sie herunter. (Siehe [Hochladen und Herunterladen von Prologue- und Epilogue-Dateien](configuring-pdf-settings.md#uploading-and-downloading-prologue-and-epilogue-files).

Adobe PDF-Einstellungen gelten nur für PDFMaker-Konvertierungen. Dazu gehören die folgenden Konversionen:

* Microsoft Word-Dokument (DOC, DOCX, RTF, TXT)
* Microsoft Excel-Dokument (XLS, XLSX)
* Microsoft PowerPoint-Dokument (PPT, PPTX)
* Microsoft Project Document (MPP)
* Microsoft Visio-Dokument (VSD)

>[!NOTE]
>
>Bei Verwendung von OpenOffice zur Konvertierung der oben genannten Formate werden die Einstellungen von Adobe PDF nicht angewendet.

## Über vordefinierte PDF-Einstellungen {#about-the-predefined-pdf-settings}

PDF Generator bietet mehrere vordefinierte PDF-Einstellungen für Ihre Verwendung. Sie können diese vordefinierten Einstellungen nicht ändern. Sie können jedoch eine Einstellung basierend auf einer vorhandenen erstellen, indem Sie die Einstellung bearbeiten und unter einem neuen Namen speichern.

**Drucken in hoher Qualität**: Erstellt PDF-Dateien für eine hochwertige Ausgabe. Diese Einstellung:

* Neuberechnen von Farb- und Graustufenbildern mit 300 dpi
* Neuberechnen von Schwarzweißbildern mit 1200 dpi
* Drucken mit einer höheren Bildauflösung
* verwendet andere Einstellungen, um die maximale Menge an Informationen über das Originaldokument beizubehalten.

Diese PDF-Dateien können in Adobe Acrobat 5 und Adobe Acrobat Reader® 5 oder höher geöffnet werden.

**Seiten in Übergrößen**: Erstellt PDF-Dokumente, die für ein zuverlässiges Anzeigen und Drucken technischer Zeichnungen größer als 508 x 508 cm geeignet sind. Erstellte PDF-Dokumente können in Adobe Acrobat Professional und in Acrobat Standard Version 7 oder höher sowie Adobe Reader 7 oder höher geöffnet werden.

**PDF/A-1B 2005 CMYK/PDF/A-1B 2005 RGB**: Überprüft eingehende Aufträge auf Einhaltung des ISO-Standards für die Langzeitarchivierung (Archivierung) elektronischer Dokumente und erstellt PDF/A-Dateien nur bei Einhaltung. Diese Dateien werden hauptsächlich zur Archivierung verwendet. Kompatible Dateien dürfen nur Text, Rasterbilder und Vektorobjekte enthalten; sie dürfen keine Verschlüsselung und Skripte enthalten. Darüber hinaus müssen alle Schriftarten eingebettet werden, damit die Dokumente wie erstellt geöffnet und angezeigt werden können. PDF/A-1b verwendet PDF 1.4 und konvertiert alle Farben je nach gewähltem Standard entweder in CMYK oder in RGB. Mit dieser Einstellungsdatei erstellte PDF-Dateien können in Acrobat 5 und Acrobat Reader 5 und höher geöffnet werden. Weitere Informationen zu PDF/A finden Sie unter Adobe und Branchenstandards.

**PDF/X-1a 2001**: Überprüft eingehende Aufträge auf Kompatibilität mit PDF/X-1a und erstellt PDF-Dateien nur bei Kompatibilität. PDF/X-1a ist ein ISO-Standard für den Austausch grafischer Inhalte. Für PDF/X-1a müssen alle Schriftarten eingebettet, die entsprechenden PDF-Felder angegeben und die Farbe entweder als CMYK oder als Volltonfarben angezeigt werden. PDF-Dateien, die die PDF/X-1a-Anforderungen erfüllen, sind auf eine bestimmte Ausgabebedingung ausgerichtet, wie z. B. den Offset-Druck gemäß Specifications Web Offset Publications . Weitere Informationen zu PDF/X finden Sie unter Adobe und Branchenstandards.

**PDF/X-3 2002**: Überprüft eingehende Aufträge auf Kompatibilität mit PDF/X-3 und erstellt PDF-Dateien nur bei Kompatibilität. Wie PDF/X-1a ist PDF/X-3 ein ISO-Standard für den Austausch grafischer Inhalte. Der Hauptunterschied besteht darin, dass PDF/X-3 geräteunabhängige Farben unterstützt.

**Druckqualität**: Erstellt PDF-Dateien für eine hochwertige Druckproduktion (z. B. auf einem Film- oder Plattenbelichter). In diesem Fall ist die Dateigröße keine Überlegung. Ziel ist es, alle Informationen in einer PDF-Datei zu speichern, die ein Druckerei- oder Druckvorstufen-Dienstleister benötigt, um das Dokument korrekt zu drucken. Dieser Optionssatz:

* Neuberechnen von Farb- und Graustufenbildern mit 300 dpi
* Neuberechnen von Schwarzweißbildern mit 1200 dpi
* Bettet Teilmengen aller im Dokument verwendeten Schriftarten ein.
* Drucken mit einer höheren Bildauflösung,
* keine automatische Rotation von Seiten basierend auf der Ausrichtung der Text- oder DSC-Kommentare (Document Structure Conventionen)
* verwendet andere Einstellungen, um die maximale Menge an Informationen über das Originaldokument beizubehalten.

Druckaufträge schlagen fehl, wenn sie Schriftarten haben, die nicht eingebettet werden können. Diese PDF-Dateien können in Acrobat 5 und Acrobat Reader 5 und höher geöffnet werden.

>[!NOTE]
>
>Bevor Sie eine PDF-Datei erstellen, die an einen Drucker oder Druckvorstufen-Dienstleister gesendet werden soll, legen Sie die Ausgabeauflösung und andere Einstellungen fest oder fordern Sie eine .joboptions-Datei mit den empfohlenen Einstellungen an. Möglicherweise müssen Sie die Adobe PDF-Einstellungen für einen bestimmten Provider anpassen und dann eine eigene .joboptions-Datei bereitstellen.

**Kleinste Dateigröße**: Erstellt PDF-Dateien für die Anzeige im Web oder einem Intranet oder für die Verteilung über ein E-Mail-System zur Anzeige auf dem Bildschirm. Dieser Optionssatz verwendet Komprimierung, Neuberechnung und eine relativ niedrige Bildauflösung. Alle Farben werden in sRGB konvertiert und Schriftarten werden nur eingebettet, wenn dies erforderlich ist. Außerdem werden Dateien für die Byte-Bereitstellung optimiert. Diese PDF-Dateien können in Acrobat 5 und Acrobat Reader 5.0 und höher geöffnet werden.

**Standard**: Erstellt PDF-Dateien für die Ausgabe auf Desktop-Druckern und Digitalkopierern, die Veröffentlichung auf einer CD oder zum Übertragen an einen Kunden als Prüfdruck. Dieser Optionssatz verwendet Komprimierung und Neuberechnung, um die Dateigröße zu reduzieren. Außerdem werden darin Untergruppen aller Schriftarten eingebettet, alle Farben in sRGB konvertiert und auf eine mittlere Auflösung gedruckt, um eine ausreichend genaue Darstellung des Originaldokuments zu erhalten. Beachten Sie, dass Microsoft Windows-Schriftartuntergruppen nicht standardmäßig eingebettet sind. Diese PDF-Dateien können in Acrobat 5 und Acrobat Reader 5.0 und höher geöffnet werden.

## PDF-Einstellungen hinzufügen oder bearbeiten {#add-or-edit-pdf-settings}

PDF-Einstellungen bestimmen genau, wie Dateien konvertiert werden, sowie deren PDF-Struktur und -Funktionen. Definieren Sie eine neue PDF-Einstellung oder bearbeiten Sie eine, die Sie zuvor erstellt haben. Sie können vordefinierte Einstellungen nicht ändern. Sie können jedoch eine Einstellung basierend auf einer vorhandenen erstellen, indem Sie die Einstellung bearbeiten und unter einem neuen Namen speichern.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Adobe PDF-Einstellungen&quot;.
1. Klicken Sie entweder auf Neu oder auf den Namen einer vorhandenen Einstellung.
1. Füllen Sie auf der Seite &quot;Adobe PDF-Einstellung neu/bearbeiten&quot;die erforderlichen Informationen in diesen Abschnitten aus:

[Allgemeine Optionen](configuring-pdf-settings.md#general-options)

[Bildoptionen](configuring-pdf-settings.md#images-options)

[Schriftartoptionen](configuring-pdf-settings.md#fonts-options)

[Farboptionen](configuring-pdf-settings.md#color-options)

[Erweiterte Optionen](configuring-pdf-settings.md#advanced-options)

[Optionen für „Standards - Berichterstellung und Kompatibilität“](configuring-pdf-settings.md#standards-reporting-and-compliance-options)

[Optionen für Ansicht beim Öffnen](configuring-pdf-settings.md#initial-view-options)

   Um zu einem anderen Abschnitt zu gelangen, klicken Sie auf dessen Link auf der Webseite oder verwenden Sie die Schaltflächen Weiter und Zurück .

1. Nachdem Sie die Informationen in allen Abschnitten ausgefüllt haben, klicken Sie auf Speichern oder Speichern unter und geben Sie einen Namen für die Einstellung ein.

## Hochladen von PDF-Einstellungen {#upload-pdf-settings}

Sie können die PDF-Einstellungen auf dem PDF Generator-Server verfügbar machen, indem Sie sie von einem lokalen Computer oder von einem Netzwerkspeicherort hochladen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Adobe PDF-Einstellungen&quot;und dann auf &quot;Hochladen&quot;.
1. Klicken Sie auf der Seite &quot;Adobe PDF-Einstellung hochladen&quot;auf &quot;Durchsuchen&quot;, suchen Sie die PDF-Einstellungsdatei und klicken Sie auf &quot;Öffnen&quot;.
1. Klicken Sie auf OK und dann erneut auf OK .

## PDF-Einstellungen löschen {#delete-pdf-settings}

Sie können PDF-Einstellungen dauerhaft löschen, wenn sie nicht mehr benötigt werden.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Adobe PDF-Einstellungen&quot;.
1. Aktivieren Sie das Kontrollkästchen neben der zu löschenden Einstellung. Sie können mehrere Einstellungen auswählen.
1. Klicken Sie auf Löschen und dann erneut auf der Seite Löschbestätigung auf Löschen .

## Allgemeine Optionen {#general-options}

Verwenden Sie die allgemeinen Optionen, um die Version von Acrobat anzugeben, die für die Dateikompatibilität und andere Datei- und Geräteoptionen verwendet werden soll. Anweisungen zum Zugriff auf die allgemeinen Optionen finden Sie unter [PDF-Einstellungen hinzufügen oder bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

### Dateioptionen {#file-options}

**Kompatibilität**: Die Kompatibilitätsstufe der PDF-Datei. Bei Dokumenten, die auf breiter Basis verteilt werden sollen, sollten Sie Acrobat 4 (PDF 1.3) oder Acrobat 5 (PDF 1.4) auswählen, um sicherzustellen, dass alle Benutzer das Dokument anzeigen und drucken können. Wenn Sie Dateien mithilfe der Acrobat 5-Kompatibilität oder neuer erstellen, sind diese möglicherweise nicht mit früheren Versionen von Acrobat kompatibel. Die folgenden Unterabschnitte zeigen einige der Unterschiede zwischen PDF-Dateien, die mit verschiedenen Acrobat-Kompatibilitätsstufen erstellt werden.

<table>
 <tbody>
  <tr>
   <th><p>Acrobat 4 (PDF 1.3)</p> </th>
   <th><p>Acrobat 5 (PDF 1.4)</p> </th>
   <th><p>Acrobat 6 (PDF 1.5)</p> </th>
   <th><p>Acrobat 7 (PDF 1.6) und Acrobat 8 (PDF 1.7)</p> </th>
  </tr>
  <tr>
   <td><p>Kann mit Acrobat 3.0 und Acrobat Reader 3.0 und höher geöffnet werden.</p> </td>
   <td><p>Kann mit Acrobat 3.0 und Acrobat Reader 3.0 und höher geöffnet werden. Funktionen, die für spätere Versionen spezifisch sind, gehen möglicherweise verloren oder können nicht angezeigt werden.</p> </td>
   <td><p>Die meisten können mit Acrobat 4 und Acrobat Reader 4.0 und höher geöffnet werden. Funktionen, die für spätere Versionen spezifisch sind, gehen möglicherweise verloren oder können nicht angezeigt werden.</p> </td>
   <td><p>Die meisten können mit Acrobat 4 und Acrobat Reader 4.0 und höher geöffnet werden. Funktionen, die für spätere Versionen spezifisch sind, gehen möglicherweise verloren oder können nicht angezeigt werden.</p> </td>
  </tr>
  <tr>
   <td><p>Darf kein Bildmaterial enthalten, das Live-Transparenzeffekte verwendet. Jede Transparenz muss vor der Konvertierung in PDF 1.3 reduziert werden.</p> </td>
   <td><p>Unterstützt die Verwendung von Live-Transparenz in Grafiken. (Acrobat Distiller-Funktion reduziert Transparenz.)</p> </td>
   <td><p>Unterstützt die Verwendung von Live-Transparenz in Grafiken. (Acrobat Distiller-Funktion reduziert Transparenz.)</p> </td>
   <td><p>Unterstützt die Verwendung von Live-Transparenz in Grafiken. (Acrobat Distiller-Funktion reduziert Transparenz.)</p> </td>
  </tr>
  <tr>
   <td><p>Ebenen werden nicht unterstützt.</p> </td>
   <td><p>Ebenen werden nicht unterstützt.</p> </td>
   <td><p>Behält Ebenen bei, wenn Sie PDF-Dateien aus Anwendungen erstellen, die die Generierung von PDF-Dokumenten mit Ebenen unterstützen, z. B. Adobe Illustrator® CS oder Adobe InDesign® CS und höher.</p> </td>
   <td><p>Behält Ebenen bei, wenn Sie PDF-Dateien aus Anwendungen erstellen, die die Generierung von PDF-Dokumenten mit Ebenen unterstützen, z. B. Illustrator CS oder InDesign CS und höher.</p> </td>
  </tr>
  <tr>
   <td><p>DeviceN-Farbraum mit 8 Farbmitteln wird unterstützt.</p> </td>
   <td><p>DeviceN-Farbraum mit 8 Farbmitteln wird unterstützt.</p> </td>
   <td><p>DeviceN-Farbraum mit bis zu 31 Farbmitteln wird unterstützt.</p> </td>
   <td><p>DeviceN-Farbraum mit bis zu 31 Farbmitteln wird unterstützt.</p> </td>
  </tr>
  <tr>
   <td><p>Multibyte-Schriftarten können eingebettet werden. (Distiller konvertiert die Schriftarten beim Einbetten.)</p> </td>
   <td><p>Multibyte-Schriftarten können eingebettet werden.</p> </td>
   <td><p>Multibyte-Schriftarten können eingebettet werden.</p> </td>
   <td><p>Multibyte-Schriftarten können eingebettet werden.</p> </td>
  </tr>
  <tr>
   <td><p>Die 40-Bit-RC4-Sicherheit wird unterstützt.</p> </td>
   <td><p>Die 128-Bit-RC4-Sicherheit wird unterstützt.</p> </td>
   <td><p>Die 128-Bit-RC4-Sicherheit wird unterstützt.</p> </td>
   <td><p>Die 128-Bit-RC4- und 128-Bit-AES-Sicherheit (Advanced Encryption Standard) wird unterstützt.</p> </td>
  </tr>
 </tbody>
</table>

**Komprimierung auf Objektebene**: Fasst kleine Objekte (die selbst nicht komprimierbar sind) zu Streams zusammen, die effizient komprimiert werden können.

**Aus**: Komprimiert keine Strukturinformationen im PDF-Dokument. Wählen Sie diese Option aus, wenn Benutzer Lesezeichen und andere Strukturinformationen in Acrobat 5 oder höher anzeigen, durch diese navigieren und mit diesen interagieren können sollen.

**Nur Tags**: Komprimiert Strukturinformationen im PDF-Dokument. Mit dieser Option wird eine PDF-Datei erstellt, die mithilfe von Acrobat 5 geöffnet und gedruckt werden kann. Benutzer können keine Barrierefreiheit, Struktur oder getaggten PDF-Informationen in Acrobat 5 oder Acrobat Reader 5.0 anzeigen. Sie können diese Informationen jedoch in Acrobat 6 und Adobe Reader 6.0 anzeigen.

**Seiten automatisch drehen**: Legt die automatische Drehung von Seiten basierend auf der Ausrichtung des Textes oder von DSC-Kommentaren fest. Für einige Seiten (z. B. Seiten, die Tabellen enthalten) muss der Benutzer sie beispielsweise seitlich drehen, um sie zu lesen. Wählen Sie &quot;Einzeln&quot;aus, um die einzelnen Seiten je nach Richtung des Textes auf dieser Seite zu drehen. Wählen Sie &quot;Zusammengefasst nach Datei&quot;, um alle Seiten im Dokument basierend auf der Ausrichtung des Textes zu drehen.

>[!NOTE]
>
>Wenn DSC-Kommentare verarbeiten in den erweiterten Einstellungen ausgewählt ist und Kommentare zur Anzeigeausrichtung enthalten sind, haben diese Kommentare Vorrang bei der Bestimmung der Seitenausrichtung.

**Bindung**: Gibt an, ob eine PDF-Datei mit Bindung auf der linken oder rechten Seite angezeigt werden soll. Diese Einstellung wirkt sich auf die Anzeige von Seiten im Layout „Fortlaufend - Doppelseiten“ aus und bewirkt, dass Kleinbilder nebeneinander angezeigt werden.

**Auflösung**: Legt die Emulation für die Auflösung eines Druckers für Eingabedateien fest, die ihr Verhalten an die Auflösung des Druckers anpassen, auf dem sie gedruckt werden. Bei den meisten Eingabedateien führt eine höhere Auflösungseinstellung zu größeren, aber hochwertigeren PDF-Dateien und eine niedrigere Einstellung zu kleineren PDF-Dateien mit geringerer Qualität. Normalerweise bestimmt die Auflösung die Anzahl der Schritte in einem Verlauf oder einer Mischung. Sie können einen Wert zwischen 72 und 4000 eingeben. Behalten Sie diese Einstellung als Standard bei, es sei denn, Sie möchten die PDF-Datei auf einen bestimmten Drucker drucken und die in der ursprünglichen Eingabedatei definierte Auflösung emulieren.

>[!NOTE]
>
>Durch Erhöhen der Auflösungseinstellung wird die Dateigröße erhöht und die Verarbeitungszeit für einige Dateien kann geringfügig verlängert werden.

**Alle Seiten oder Seiten ab**: Gibt an, welche Seiten konvertiert werden sollen. Lassen Sie das Feld „Bis“ leer, um einen Bereich von der Seitennummer, die Sie in das Feld „Von“ eingeben, bis zum Ende der Datei zu erstellen.

**Für schnelle Web-Anzeige optimieren**: Strukturiert die Datei für das seitenweise Herunterladen (Byte Serving) von Webservern um. Diese Option komprimiert Text und Strichgrafiken, unabhängig davon, was Sie auf der Registerkarte &quot;Bilder&quot;als Komprimierungseinstellungen ausgewählt haben. Die Komprimierung führt zu einem schnelleren Zugriff und einer schnelleren Anzeige beim Herunterladen der Datei aus dem Internet oder einem Netzwerk. Standardmäßig ist diese Option nicht aktiviert.

### Standardseitengröße {#default-page-size}

Die Optionen &quot;Standardseitengröße&quot;geben die zu verwendende Seitengröße an, wenn in der Originaldatei keine angegeben ist. Normalerweise enthalten Adobe PostScript-Dateien diese Informationen, mit Ausnahme von Encapsulated PostScript (EPS)-Dateien, die eine Größe des Begrenzungsrahmens, aber keine Seitengröße ergeben. Die maximal zulässige Seitengröße beträgt 31.800.000 cm in beide Richtungen. Diese Optionen konfigurieren die standardmäßige Seitengröße:

**Breite**: Die Breite der Seite.

**Höhe**: Die Höhe der Seite.

**Einheiten**: Die für die Breiten- und Höheneinstellung zu verwendenden Einheiten.

## Bildoptionen {#images-options}

Die Bildoptionen geben die Komprimierung und Neuberechnung für Bilder an. Sie können mit diesen Optionen experimentieren, um ein angemessenes Gleichgewicht zwischen Dateigröße und Bildqualität zu finden. Anweisungen zum Zugriff auf die Bildeinstellungen finden Sie unter [PDF-Einstellungen hinzufügen oder bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Mit diesen Optionen werden Farb-, Graustufen- und Schwarzweißbilder konfiguriert:

**Neuberechnung**: Legen Sie einen Wert für jeden Bildtyp fest. Um Farb-, Graustufen- und Schwarzweißbilder neu zu berechnen, kombiniert PDF Generator Pixel in einem Auswahlbereich und erstellt daraus ein größeres Pixel. Geben Sie die Auflösung Ihres Ausgabegeräts in dpi (Dots per Inch, Punkte pro Zoll) an und geben Sie in das Feld „Für Auflösungen über“ eine Auflösung in dpi ein. Bei Bildern mit einer Auflösung über diesem Schwellenwert kombiniert PDF Generator Pixel nach Bedarf, um die Bildauflösung (Pixel pro Zoll) auf die angegebene dpi-Einstellung zu reduzieren. Um die Neuberechnung zu deaktivieren, wählen Sie Aus. Im Folgenden finden Sie die Optionen:

**Durchschnittliche Neuberechnung auf**: Ermittelt den Durchschnitt der Pixel in einem Auswahlbereich und ersetzt den gesamten Bereich durch die durchschnittliche Pixelfarbe mit der angegebenen Auflösung.

**Bikubische Neuberechnung auf**: Verwendet einen gewichteten Durchschnitt zum Bestimmen der Pixelfarbe und liefert meist bessere Ergebnisse als die einfache Durchschnittsbestimmungsmethode bei der Neuberechnung. Die bikubische Methode ist die langsamste, jedoch präziseste Methode und führt zu den feinsten tonlichen Abstufungen.

**Kurzberechnung auf**: Wählt ein Pixel in der Mitte des Auswahlbereichs aus und ersetzt den gesamten Bereich durch dieses Pixel mit der angegebenen Auflösung. Die Subsampling-Funktion verkürzt die Konvertierungsdauer im Vergleich zum Downsampling erheblich, führt jedoch zu weniger glatten und kontinuierlichen Bildern.

Die Auflösungseinstellung für Farb- und Graustufen sollte das 1,5- bis 2-fache der Rasterweitenlinierung betragen, mit der die Datei gedruckt wird. (Sofern Sie diese empfohlene Auflösungseinstellung nicht unterschreiten, sind Bilder ohne geraden Rand oder geometrische oder sich wiederholende Muster von einer niedrigeren Auflösung nicht betroffen.) Die Auflösung für Schwarzweißbilder sollte mit der des Ausgabegeräts identisch sein. Das Speichern eines Schwarzweißbilds mit einer höheren Auflösung als 1500 dpi erhöht jedoch die Dateigröße, ohne die Bildqualität spürbar zu verbessern.

Beachten Sie auch, ob Benutzer eine Seite vergrößern müssen. Wenn Sie beispielsweise ein PDF-Dokument einer Karte erstellen, sollten Sie eine höhere Bildauflösung verwenden, damit Benutzer die Karte vergrößern können.

>[!NOTE]
>
>Das Neuberechnen von Schwarzweißbildern kann zu unerwarteten Anzeigeergebnissen führen, z. B. zu keiner Bildanzeige. Wenn dieses Problem auftritt, deaktivieren Sie die Neuberechnung und konvertieren Sie die Datei erneut. Dieses Problem tritt am ehesten bei der Teilberechnung und am ehesten bei der bikubischen Neuberechnung auf.

Diese Tabelle zeigt die Typen von Druckern und ihre in dpi gemessene Auflösung, ihre standardmäßige Bildschirmausrichtung, gemessen in lpi (Lines per Inch, Zeilen pro Zoll), und eine Neuberechnungsauflösung für Bilder, die in ppi (Pixels per Inch) gemessen werden. Um beispielsweise auf einem 600-dpi-Laserdrucker zu drucken, geben Sie 170 für die Auflösung ein, bei der Bilder neu aufgenommen werden sollen.

<table>
 <tbody>
  <tr>
   <th><p>Druckerauflösung</p> </th>
   <th><p>Standardzeilenbildschirm</p> </th>
   <th><p>Bildauflösung</p> </th>
  </tr>
  <tr>
   <td><p>300 dpi (Laserdrucker)</p> </td>
   <td><p>60 lpi</p> </td>
   <td><p>120 ppi</p> </td>
  </tr>
  <tr>
   <td><p>600 dpi (Laserdrucker)</p> </td>
   <td><p>85 lpi</p> </td>
   <td><p>170 ppi</p> </td>
  </tr>
  <tr>
   <td><p>1200 dpi (Filmbelichter)</p> </td>
   <td><p>120 lpi</p> </td>
   <td><p>240 ppi</p> </td>
  </tr>
  <tr>
   <td><p>2400 dpi (Filmbelichter)</p> </td>
   <td><p>150 lpi</p> </td>
   <td><p>300 ppi</p> </td>
  </tr>
 </tbody>
</table>

**Komprimierung**: Legen Sie einen Wert fest, der auf Farb-, Graustufen- und Schwarzweißbilder angewendet werden soll. Legen Sie für Farb- und Graustufenbilder auch die Bildqualität fest:

* Wählen Sie für Farb- oder Graustufenbilder die Option ZIP aus, um eine Komprimierung anzuwenden, die sich gut auf Bilder mit großen Bereichen von Einzelfarben oder sich wiederholenden Mustern auswirkt. Beispiele sind Screenshots, einfache Bilder, die mit Farbprogrammen erstellt wurden, und Schwarzweißbilder, die sich wiederholende Muster enthalten. Wählen Sie JPEG, Qualität von Minimum bis Maximum, um eine für Graustufen- oder Farbbilder geeignete Komprimierung anzuwenden, z. B. durchgehende Tonaufnahmen, die mehr Details enthalten, als auf dem Bildschirm oder im Druck reproduziert werden können. Wählen Sie Automatisch (JPEG) aus, um automatisch die beste Farbqualität für Farb- und Graustufenbilder zu bestimmen.
* Wählen Sie für Schwarzweißbilder die Komprimierung &quot;CCITT Group 4&quot;, &quot;CCITT Group 3&quot;, &quot;ZIP&quot;, &quot;JPEG200&quot;, &quot;Automatic (JPEG2000)&quot;oder &quot;Run Length&quot;.

Stellen Sie sicher, dass Schwarzweißbilder nicht als Graustufen, sondern als Schwarzweißbilder gescannt werden. Gescannter Text wird manchmal standardmäßig als Graustufenbild gespeichert. Graustufentext, der mit der Komprimierungsmethode JPEG komprimiert wird, ist nicht klar und kann unlesbar sein.

**Bildqualität**: Konfiguriert die Bildqualität von Farb- und Graustufenbildern. Die Optionen lauten „Minimal“, „Niedrig“, „Mittel“, „Hoch“ und „Maximal“.

**Mit Graustufen glätten**: Glättet gezackte Ränder in Schwarzweißbildern. Wählen Sie 2 Bit, 4 Bit oder 8 Bit aus, um 4, 16 oder 256 Graustufen anzugeben. (Die Glättung kann kleine oder dünne Linien verwischen.)

>[!NOTE]
>
>Die Komprimierung von Text und Strichgrafiken ist immer aktiviert.

**Bildrichtlinie**: Legen Sie eine Richtlinie fest, die auf Farb-, Graustufen- und Schwarzweißbilder angewendet werden soll. Wenn die Bildauflösung unter die angegebene Auflösung fällt, können Sie weiterhin den Vorgang fortsetzen (Ignorieren), eine Warnmeldung bereitstellen oder den Auftrag abbrechen.

## Schriftartoptionen {#fonts-options}

Die Schriftartoptionen geben an, welche Schriftarten in eine PDF-Datei eingebettet werden sollen und ob eine Untergruppe von Zeichen eingebettet werden soll, die in der PDF-Datei verwendet werden. Anweisungen zum Zugriff auf die Schriftartoptionen finden Sie unter [PDF-Einstellungen hinzufügen oder bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

>[!NOTE]
>
>Wenn Sie PDF-Dateien mit derselben Schriftartuntergruppe kombinieren, versucht PDF Generator, die Schriftartuntergruppen zu kombinieren.

**Alle Schriftarten einbetten**: Bettet alle Schriftarten ein, die in der Datei verwendet werden. Die Schrifteinbettung ist für die Erfüllung der PDF/X-Anforderungen erforderlich.

**Untergruppe von eingebetteten Schriften, wenn Prozentsatz der verwendeten Zeichen kleiner ist als**: Wenn Sie diese Option auswählen, geben Sie einen Prozentsatz an, um nur eine Untergruppe der Schriftarten einzubetten. Wenn der Schwellenwert beispielsweise 35 beträgt und weniger als 35 % der Zeichen verwendet werden, bettet der PDF Generator nur diese Zeichen ein. Es werden nur Schriftarten mit entsprechenden Berechtigungsbits eingebettet.

**Bei fehlgeschlagenem Einbetten**: Gibt an, wie PDF Generator reagieren soll, wenn bei der Verarbeitung einer Datei eine einzubettende Schrift nicht gefunden wird. Die folgenden Möglichkeiten stehen zur Verfügung: PDF Generator kann entweder die Anforderung ignorieren und die Schrift ersetzen, Sie warnen und die Schrift ersetzen oder die Verarbeitung des aktuellen Auftrags abbrechen.

**Schriftquelle**: Der Speicherort der von PDF Generator verwendeten Schriften.

### Festlegen der einzubettenden Schriftarten {#specify-which-fonts-to-embed}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Adobe PDF-Einstellungen&quot;.
1. Klicken Sie auf Neu oder auf den Namen einer Einstellung.
1. Klicken Sie auf &quot;Schriftarten&quot;und deaktivieren Sie &quot;Alle Schriftarten einbetten&quot;.
1. Wählen Sie in der Liste &quot;Schriftquelle&quot;eine Schriftquelle aus und klicken Sie auf Los , um die Liste der Schriftarten im Feld auf der linken Seite zu aktualisieren.
1. Klicken Sie links im Feld auf eine Schriftart. Klicken Sie dann neben dem entsprechenden Feld auf Hinzufügen , um es in die Liste Immer einbetten oder Nie einbetten zu verschieben. Wiederholen Sie diese Schritte für jede Schriftart. Klicken Sie bei gedrückter Strg-Taste, um mehrere zu verschiebende Schriftarten auszuwählen.
1. Um eine Schrift aus der Liste &quot;Immer einbetten&quot;oder &quot;Nie einbetten&quot;zu entfernen, wählen Sie sie aus und klicken Sie neben dem entsprechenden Feld auf &quot;Entfernen&quot;. Durch diese Aktion wird die Schriftart nicht aus Ihrem System entfernt, sondern nur der Verweis darauf in der Liste.
1. Wenn die Schrift, die Sie angeben möchten, nicht angezeigt wird, geben Sie ihren Namen in das Feld &quot;Schrift hinzufügen&quot;ein und klicken Sie dann auf &quot;Immer einbetten&quot;oder &quot;Nie einbetten&quot;. Schriftnamen dürfen keine alphanumerischen Zeichen enthalten.

>[!NOTE]
>
>Eine TrueType-Schriftart kann eine Einstellung enthalten, die der Schriftdesigner hinzugefügt hat und die verhindert, dass die Schriftart in PDF-Dateien eingebettet wird.

>[!NOTE]
>
>Schriftarten werden aus dem Windows-Systemschriftarten-Cache ausgewählt und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.

## Farboptionen {#color-options}

Die Farboptionen legen alle Farbmanagement-Informationen für den PDF Generator fest. Anweisungen zum Zugriff auf die Farboptionen finden Sie unter [PDF-Einstellungen hinzufügen oder bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

### Adobe Color-Einstellungen {#adobe-color-settings}

**Einstellungsdatei**: Diese Liste enthält Farbeinstellungen, die auch in gängigen Grafikprogrammen wie Adobe Photoshop und Adobe Illustrator verwendet werden. Die ausgewählte Farbeinstellung bestimmt die anderen Adobe-Farbeinstellungen auf dieser Seite. Wenn Sie beispielsweise eine andere Einstellung als &quot;Ohne&quot;auswählen, sind alle anderen Optionen als die für geräteabhängige Daten vordefiniert und abgeblendet. Sie können die Einstellungen für Farbmanagement-Richtlinien und Arbeitsbereiche nur bearbeiten, wenn Sie für Einstellungsdatei &quot;Ohne&quot;auswählen.

### Farbmanagement-Richtlinien {#color-management-policies}

Wenn Sie für die Einstellungsdatei &quot;Ohne&quot;ausgewählt haben, gibt der Bereich &quot;Farbmanagement-Richtlinien&quot;an, wie PDF Generator nicht verwaltete Farben in eine PostScript-Datei konvertiert.

**Farbe unverändert lassen**: Belässt geräteabhängige Farben unverändert und erhält geräteunabhängige Farben mit der bestmöglichen Entsprechung in PDF. Diese Option eignet sich für Druckereien, die alle ihre Geräte kalibriert haben, diese Informationen zum Angeben von Farben in der Datei genutzt haben und alle Druckaufträge nur auf diesen Geräten ausgeben.

**Alles für Farb-Management kennzeichnen**: Bettet beim Untersuchen von Dateien das ICC-Profil (International Color Consortium) ein und kalibriert Farben in den Bildern, wodurch Farben in den resultierenden PDF-Dateien geräteunabhängig werden, wenn Sie die Kompatibilität mit Acrobat 4 (PDF 1.3) oder höher ausgewählt haben. Geräteabhängige Farbräume in Dateien (RGB, Grayscale und CMYK) werden jedoch in geräteunabhängige Farbräume (CalRGB, CalGray und LAB) konvertiert.

**Nur Bilder für Farb-Management kennzeichnen**: Bettet beim Untersuchen von Dateien ICC-Profile nur in Bilder, nicht jedoch in Text oder Grafiken ein, wenn Sie die Kompatibilität mit Acrobat 4 (PDF 1.3) ausgewählt haben. Diese Option verhindert, dass schwarzer Text eine Farbverschiebung durchläuft. Geräteabhängige Farbräume in Bildern (RGB, Graustufen und CMYK) werden jedoch in geräteunabhängige Farbräume (CalRGB, CalGray und LAB) konvertiert. Text und Grafiken werden nicht konvertiert.

**Alle Farben in sRGB konvertieren oder Alle Farben in CMYK konvertieren**: Kalibriert die Farben in der Datei, wodurch die Farben geräteunabhängig werden, ähnlich wie bei „Alles für Farb-Management kennzeichnen“. Wenn Sie die Kompatibilität mit Acrobat 4 (PDF 1.3) oder höher ausgewählt und eine Konvertierung in sRGB vorgenommen haben, werden die CMYK- und RGB-Bilder in sRGB konvertiert.

Unabhängig von der ausgewählten Kompatibilitätsoption bleiben Graustufenbilder unverändert. Dies reduziert in der Regel die Größe und erhöht die Anzeigegeschwindigkeit von PDF-Dateien, da weniger Informationen zur Beschreibung von RGB-Bildern als zur Beschreibung von CMYK--Dateien erforderlich sind. Da RGB der native Farbraum ist, der auf Monitoren verwendet wird, ist während der Anzeige keine Farbkonvertierung erforderlich, was zur schnellen Online-Anzeige beiträgt. Diese Option wird empfohlen, wenn die PDF-Datei online oder mit Druckern mit niedriger Auflösung verwendet werden soll.

**Bedingung für die Dokumentwiedergabe**: Die Methode zur Zuordnung von Farben zwischen Farbräumen. Das Ergebnis einer bestimmten Methode hängt von den Profilen der Farbräume ab. Einige Profile liefern beispielsweise bei verschiedenen Methoden identische Ergebnisse. Die folgenden Optionen stehen zur Auswahl:  

>[!NOTE]
>
>In allen Fällen können Bedingungen ggf. von Farbmanagementvorgängen ignoriert oder außer Kraft gesetzt werden, die im Anschluss an die Erstellung der PDF-Datei erfolgen.

**Beibehalten**: Bedeutet, dass die Bedingung im Ausgabegerät und nicht in der PDF-Datei angegeben wird. Bei vielen Ausgabegeräten ist „Relativ farbmetrisch“ die Standardbedingung.

**Perzeptiv**: Behält die relativen Farbwerte zwischen den Original-Pixeln bei, die der Zielfarbskala zugeordnet werden. Bei dieser Methode bleibt die optische Beziehung zwischen Farben erhalten, obgleich die Farbwerte selbst sich ggf. ändern.

**Sättigung**: Behält die relativen Sättigungswerte der Original-Pixel bei. Diese Methode eignet sich für Geschäftsgrafiken, bei denen die exakte Beziehung zwischen Farben nicht so wichtig ist wie das Vorhandensein leuchtender gesättigter Farben.

**Relativ farbmetrisch**: Ordnet den weißen Punkt des Quellraums dem weißen Punkt des Zielraums zu.

**Absolut farbmetrisch**: Deaktiviert beim Konvertieren von Farben den Abgleich weißer und schwarzer Punkte. Diese Methode wird nicht empfohlen, es sei denn, Sie müssen Signaturfarben erhalten, z. B. in Warenzeichen oder Logos.

### Arbeitsbereiche {#working-spaces}

Wählen Sie für alle Werte in der Liste unter &quot;Farbmanagement-Richtlinien&quot;außer &quot;Farbe unverändert lassen&quot;aus den Listen im Arbeitsbereich aus, um anzugeben, welche ICC-Profile zum Definieren und Kalibrieren der Graustufen-, RGB- und CMYK-Farbräume in destillierten PDF-Dateien verwendet werden. Die folgenden Optionen stehen zur Auswahl:  

**Grau**: Definiert den Farbraum aller Graustufenbilder in Dateien. Diese Option ist nur verfügbar, wenn Sie &quot;Alles für Farbmanagement kennzeichnen&quot;oder &quot;Nur Bilder für Farbmanagement kennzeichnen&quot;auswählen. Das standardmäßige ICC-Profil für graue Bilder ist Gray Gamma 2.2. Sie können auch &quot;Ohne&quot;auswählen, um zu verhindern, dass Graustufenbilder konvertiert werden.

**RGB**: Definiert den Farbraum aller RGB-Bilder in Dateien. Die Standardeinstellung sRGB IEC61966-2.1 ist im Allgemeinen eine gute Wahl, da sie zu einem Industriestandard wird und viele Ausgabegeräte sie erkennen. Sie können auch &quot;Ohne&quot;auswählen, um zu verhindern, dass RGB-Bilder konvertiert werden.

**CMYK**: Definiert den Farbraum aller CMYK-Bilder in Dateien. Die Standardeinstellung ist U.S. Web Coated (SWOP) v2. Sie können auch &quot;Ohne&quot;auswählen, um zu verhindern, dass CMYK-Bilder konvertiert werden.

>[!NOTE]
>
>Die Auswahl von &quot;Ohne&quot;für alle drei Arbeitsbereiche hat denselben Effekt wie die Auswahl von &quot;Farbe unverändert lassen&quot;.

**CMYK-Werte für kalibrierte CMYK-Farbräume beibehalten**: Falls ausgewählt, werden geräteunabhängige CMYK-Werte wie geräteabhängige (DeviceCMYK-) Werte behandelt. Geräteunabhängige Farbräume werden abgelehnt und PDF/X-1a-Dateien verwenden den Wert „Alle Farben in CMYK konvertieren“. Wenn diese Option deaktiviert ist, werden geräteunabhängige Farbräume in CMYK konvertiert, wenn die Farbmanagement-Richtlinie auf &quot;Alle Farben in CMYK konvertieren&quot;festgelegt ist.

### Geräteabhängige Daten {#device-dependent-data}

Diese Optionen gelten für Dokumente, die mit High-End-Dokumentations- und Grafikanwendungen wie Adobe Illustrator und Adobe InDesign erstellt werden. Weitere Informationen finden Sie in der Dokumentation zur Anwendung.

Übertragungsfunktionen werden für künstlerische Effekte und zur Anpassung an die Spezifikationen eines bestimmten Ausgabegeräts verwendet. Beispielsweise kann eine Datei, die für die Ausgabe auf einem bestimmten Bildbelichter vorgesehen ist, Übertragungsfunktionen enthalten, die den diesem Drucker innewohnenden Punktzuwachs kompensieren.

**Unterfarbreduktion und Schwarzaufbau beibehalten:** Behält diese Einstellungen bei, wenn sie in der PostScript-Datei vorhanden sind. Der Schwarzaufbau berechnet die Menge an Schwarz, die verwendet werden soll, wenn Sie versuchen, eine bestimmte Farbe zu reproduzieren. Die Unterfarbreduktion reduziert die Menge an Zyan-, Magenta- und Gelbkomponenten, um die Menge an Schwarz auszugleichen, die die schwarze Generation hinzugefügt hat. Da weniger Tinte verwendet wird, wird UCR in der Regel für Zeitungspapier und unbeschichtetes Material verwendet.

**Wenn Übertragungsfunktionen gefunden werden:** Legt fest, was zu tun ist, wenn Übertragungsfunktionen gefunden werden:

**Beibehalten:** Behält die Übertragungsfunktionen bei, die traditionell verwendet werden, um Punktzuwachs oder Punktverlust zu kompensieren, die bei der Übertragung eines Bildes auf Film auftreten können. Ein Tonwertzuwachs tritt auf, wenn die Druckfarbpunkte, aus denen ein gedrucktes Bild besteht, größer sind (z. B. aufgrund der Verbreitung auf Papier) als im Halbtonraster. Ein Punktverlust tritt auf, wenn die Punkte kleiner gedruckt werden. Bei dieser Option werden die Übertragungsfunktionen als Teil der Datei beibehalten und bei der Ausgabe der Datei auf die Datei angewendet.

**Anwenden:** Behält die Übertragungsfunktion bei, sondern wendet sie auf die Datei an, wodurch die Farben in der Datei geändert werden. Diese Option ist nützlich, um Farbeffekte in einer Datei zu erstellen. Standardmäßig ist diese Option für neue Einstellungen ausgewählt.

**Entfernen:** Entfernt alle angewendeten Übertragungsfunktionen. Entfernen Sie angewendete Übertragungsfunktionen, es sei denn, die PDF-Datei soll auf demselben Gerät ausgegeben werden, für das die PostScript-Quelldatei erstellt wurde.

**Halbtoninformationen beibehalten:** Behält alle Halbtoninformationen in Dateien bei. Halbtoninformationen bestehen aus Punkten, die steuern, wie viel Druckfarben-Halbtongeräte an einer bestimmten Stelle auf dem Papier ablagern. Die Variation der Punktgröße und -dichte erzeugt die Illusion von Variationen von grauen oder durchgehenden Farben. Für ein CMYK-Bild werden vier Halbtonbildschirme verwendet, eine für jede beim Drucken verwendete Tinte.

In der traditionellen Druckproduktion wird ein Halbton produziert, indem ein Halbtonraster zwischen einem Stück Film und dem Bild platziert wird und dann der Film belichtet wird. Elektronische Entsprechungen wie in Adobe Photoshop ermöglichen es Benutzern, die Attribute des Halbtonrasters anzugeben, bevor sie den Film oder die Papierausgabe produzieren. Halbtoninformationen sind für die Verwendung mit einem bestimmten Ausgabegerät vorgesehen.

## Erweiterte Optionen {#advanced-options}

Die erweiterten Optionen geben an, welche DSC-Kommentare (Document Structuring Conventions) in der PDF-Datei beibehalten werden sollen und wie andere Optionen festgelegt werden, die sich auf die Konvertierung aus PostScript auswirken. In einer PostScript-Datei enthalten DSC-Kommentare Informationen zur Datei (wie die Ausgangsanwendung, das Erstellungsdatum und die Seitenausrichtung). Sie bieten außerdem eine Struktur für Seitenbeschreibungen in der Datei (z. B. Anweisungen zum Anfang und Ende für einen Prologabschnitt). DSC-Kommentare können nützlich sein, wenn Ihr Dokument gedruckt oder gedruckt wird. Anweisungen zum Zugriff auf die erweiterten Optionen finden Sie unter [PDF-Einstellungen hinzufügen oder bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Bei der Arbeit mit den erweiterten Optionen ist es hilfreich, die PostScript-Sprache und die Übersetzung in PDF zu verstehen. (Siehe [ADOBE POSTSCRIPT 3](https://www.adobe.com/products/postscript/main.html).

**PostScript-Datei darf Adobe PDF-Einstellungen überschreiben:** Verwendet Einstellungen, die in einer PostScript-Datei gespeichert sind, anstelle der aktuellen Adobe PDF-Einstellungsdatei. Vor der Verarbeitung einer PostScript-Datei können Sie Parameter in die Datei einfügen, um die folgenden Aspekte zu steuern:

* Komprimierung von Text und Grafiken
* Neuberechnung und Kodierung gesampelter Bilder
* Einbetten von Type 1-Schriftarten und Instanzen von Type 1 Multiple Master-Schriftarten

**PostScript XObjects zulassen:** PostScript XObjects speichern Informationen, die auf vielen Seiten derselben Datei erscheinen, wie beispielsweise ein Hintergrundbild oder Kopf- und Fußzeileninformationen. Die Verwendung von PostScript XObjects kann zu einem schnelleren Drucken führen, erfordert jedoch mehr Druckerspeicher. Um zu verhindern, dass PostScript XObjects erstellt wird, deaktivieren Sie diese Option, wenn Sie PDF-Dateien mit Acrobat 5 (PDF 1.4) oder neuer Kompatibilität erstellen.

**Farbverläufe in glatte Schattierungen konvertieren:** Konvertiert Verläufe in glatte Schattierungen für Acrobat 4 und höher, wodurch PDF-Dateien kleiner werden und die Qualität der endgültigen Ausgabe möglicherweise verbessert wird. PDF Generator konvertiert Farbverläufe aus Adobe Illustrator, Adobe InDesign, Adobe Freehand MX, CorelDraw, Quark XPress und Microsoft PowerPoint.

**Geglättete Linien in Kurven konvertieren:** Verringert die Anzahl von Steuerpunkten zum Erstellen von Kurven in CAD-Zeichnungen, was zu kleineren PDF-Dateien und einer schnelleren Bildschirmwiedergabe führt.

**Level 2 Copypage-Semantik beibehalten:** Verwendet den Copypage-Operator, der in LanguageLevel 2 PostScript und nicht in LanguageLevel 3 PostScript definiert ist. Wenn Sie über eine PostScript-Datei verfügen und diese Option auswählen, kopiert ein Copypage-Operator die Seite. Wenn diese Option nicht ausgewählt ist, wird das Äquivalent eines Showpage-Vorgangs ausgeführt, der Grafikstatus wird jedoch nicht neu initialisiert.

**Überdrucken-Einstellungen beibehalten:** Behält alle Überdrucken-Einstellungen in Dateien bei, die in PDF konvertiert werden. Überdruckte Farben sind zwei oder mehr übereinander gedruckte Druckfarben. Wenn beispielsweise eine Zyan-Tinte über eine gelbe Tinte druckt, ist der resultierende Überdruck eine grüne Farbe. Ohne Überdrucken würde das zugrunde liegende Gelb nicht gedruckt, was zu einer Zyanfarbe führen würde.

**Überdrucken Standard ist Nicht-Null-Überdrucken:** Verhindert, dass überdruckte Objekte mit Null-CMYK-Werten darunter liegende CMYK-Objekte auslöschen. Dieser Effekt wird erreicht, indem der Grafikstatusparameter OPM 1 an den Stellen in die PDF-Datei eingefügt wird, an denen der Operator Setoverprint vorhanden ist.

**Adobe PDF-Einstellungen in PDF-Datei speichern:** Bettet die Einstellungsdatei ein, die zur Erstellung der PDF-Datei verwendet wird. Sie können die Einstellungsdatei (mit der Dateierweiterung .joboptions ) im Dialogfeld Dateianlagen in Acrobat öffnen und anzeigen. Die Adobe PDF-Einstellungsdatei wird zu einem Element in der Struktur EmbeddedFiles in der PDF-Datei.

**Original-JPEG-Bilder in PDF speichern, wenn möglich:** Verarbeitet alle komprimierten JPEG-Bilder (Bilder, die bereits mit DCT-Kodierung komprimiert wurden), ohne sie erneut zu komprimieren. Ist diese Option aktiviert, dekomprimiert PDF Generator JPEG-Bilder, um sicherzustellen, dass sie fehlerfrei sind. Gültige Bilder werden jedoch nicht erneut komprimiert, sodass das Originalbild unverändert verarbeitet wird. Wenn diese Option aktiviert ist, verbessert sich die Leistung, da nur eine Dekomprimierung (keine Neukomprimierung) erfolgt und Bilddaten und Metadaten beibehalten werden.

**Portable Job Ticket in PDF-Datei speichern**: Behält ein PostScript-Job-Ticket in einer PDF-Datei bei. Das Job Ticket enthält Informationen zur PostScript-Datei, wie Seitengröße, Auflösung und Überfüllungsinformationen, anstatt Informationen zum Inhalt zu erhalten. Diese Informationen können später in einem Workflow oder zum Drucken der PDF verwendet werden.

**Prologue.ps und Epilogue.ps verwenden**: Sendet mit jedem Auftrag eine Prologue- und Epilogue-Datei. Diese Dateien haben viele Zwecke. Beispielsweise können Prologue-Dateien bearbeitet werden, um Deckblätter anzugeben. Epilogue-Dateien können bearbeitet werden, um eine Reihe von Verfahren in einer PostScript-Datei aufzulösen. Sie können die Dateien hochladen oder herunterladen. (Siehe Hochladen und Herunterladen von Prologue- und Epilogue-Dateien.)

**DSC-Kommentare verarbeiten**: Behält DSC-Informationen aus einer PostScript-Datei bei. Diese Unteroptionen lauten wie folgt:

**DSC-Warnungen protokollieren**: Zeigt Warnmeldungen zu problematischen DSC-Kommentaren während der Verarbeitung an und fügt dieser einer Protokolldatei hinzu.

**EPS-Informationen von DSC beibehalten**: Behält Informationen wie das Ursprungsprogramm und das Erstellungsdatum für eine EPS-Datei bei. Ist diese Option deaktiviert, werden die Größe und Mitte der Seite basierend auf der linken unteren Ecke des linken unteren Objekts und der rechten unteren Ecke des rechten unteren Objekts auf der Seite bestimmt.

**OPI-Kommentare beibehalten**: Behält Informationen bei, die zum Ersetzen eines FPO-Bildes (For Placement Only) oder Kommentars durch das hochaufgelöste Bild auf Servern benötigt werden, die die OPI-Versionen (Open Prepress Interface) 1.3 und 2.0 unterstützen.

**Dokumentinformationen von DSC beibehalten**: Behält Informationen wie den Titel, das Erstellungsdatum und die Uhrzeit bei. Wenn Sie eine PDF-Datei in Acrobat öffnen, werden diese Informationen im Bereich „Dokumenteigenschaften“ unter „Beschreibung“ angezeigt.

**Größe der Seite ändern und Grafiken für EPS-Dateien zentrieren**: Zentriert ein EPS-Bild und ändert die Seitengröße, um sie besser an das Bild anzupassen. Diese Option gilt nur für Aufträge, die aus einer einzigen EPS-Datei bestehen.

## Optionen für Standards zur Berichterstellung und Kompatibilität {#standards-reporting-and-compliance-options}

PDF Generator können Dokumentinhalte in einer PostScript-Datei überprüfen, um sicherzustellen, dass sie die standardmäßigen PDF/X-1a-, PDF/X-3- oder PDF/A-Kriterien erfüllen, bevor sie die PDF-Datei erstellen. Für PDF/X-kompatible Dateien können Sie auch festlegen, dass die PostScript-Datei zusätzliche Kriterien erfüllt, indem Sie andere Optionen unter „Standards – Berichterstellung und Kompatibilität“ auswählen. Die Verfügbarkeit der Optionen hängt vom ausgewählten Standard ab.

PDF/X-kompatible Dateien werden hauptsächlich als standardisiertes Format für den Austausch von PDF-Dateien verwendet, die für die Druckproduktion mit hoher Auflösung vorgesehen sind. Wenn Sie kein PDF-Dokument für die Druckproduktion erstellen, können Sie die PDF/X-Compliance-Standards ignorieren.

PDF/A-kompatible Dateien werden hauptsächlich zur Archivierung verwendet. Da die langfristige Erhaltung das Ziel ist, darf das Dokument nur das enthalten, was für das Öffnen und Anzeigen während der gesamten vorgesehenen Lebensdauer des Dokuments erforderlich ist. PDF/A-kompatible Dateien können beispielsweise nur Text, Rasterbilder und Vektorobjekte enthalten, sie dürfen keine Verschlüsselung und Skripte enthalten. Darüber hinaus müssen alle Schriftarten eingebettet werden, damit die Dokumente wie erstellt geöffnet und angezeigt werden können. Mit anderen Worten: PDF/A-konforme Dokumente sind *dünner* als ihre PDF/X-Entsprechungen, die für die Herstellung von High-End-Anlagen bestimmt sind.

>[!NOTE]
>
>Wenn Sie einen überwachten Ordner zum Erstellen von PDF/A-kompatiblen Dateien einrichten, stellen Sie sicher, dass Sie dem Ordner keine Sicherheit hinzufügen. Der PDF/A-Standard lässt keine Verschlüsselung zu.

Anweisungen zum Zugriff auf die Optionen für die Standardberichterstellung und -konformität finden Sie unter [PDF-Einstellungen hinzufügen oder bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

**Kompatibilitätsstandard**: Wählen Sie einen Standard aus, um einen Bericht zu erstellen, der angibt, ob die Datei die Anforderungen erfüllt, und falls nicht, welche Probleme aufgetreten sind. Wenn die Kompatibilität auf der Seite &quot;Allgemeine Einstellungen&quot;auf Acrobat 4.0 festgelegt ist, sind die folgenden Optionen aktiviert. Wenn &quot;Kompatibilität&quot;auf Acrobat 5.0 festgelegt ist, können nur die Acrobat 5.0-Optionen ausgewählt werden. Wenn die Kompatibilität auf eine alternative Option festgelegt ist, werden die folgenden Optionen abgeblendet dargestellt:

* PDF/X-1a (Acrobat 4.0-kompatibel)
* PDF/X-3 (Acrobat 4.0-kompatibel)
* PDF/X-1a (Acrobat 5.0-kompatibel)
* PDF/X-3 (Acrobat 5.0-kompatibel)
* PDF/A-1b (kompatibel mit Acrobat 5.0)

### Optionen für PDF/X-Standards {#options-for-pdf-x-standards}

**Bei Nicht-Kompatibilität**: Gibt an, ob die PDF-Datei auch dann erstellt werden soll, wenn die PostScript-Datei nicht die PDF/X-Anforderungen erfüllt. Diese Option ist verfügbar, wenn auf der Seite „Standards - Berichterstellung und Kompatibilität“ die Option „Kompatibilitätsstandard“ auf eine andere Option als „Ohne“ festgelegt ist.

**Fortfahren**: Erstellt eine PDF-Datei.

**Auftrag abbrechen**: Erstellt nur dann eine PDF-Datei, wenn die PostScript-Datei die PDF/X-Anforderungen der ausgewählten Berichtsoptionen erfüllt und ansonsten gültig ist. Wenn sowohl PDF/X-Berichtsoptionen ausgewählt sind und die PostScript-Datei nur eine Teilmenge der PDF/X-Kriterien erfüllt (z. B. PDF/X-3), erstellt PDF Generator > die konforme Datei.

**Wenn kein Endformat- oder Objektrahmen festgelegt ist**: Verfügbar, wenn „Kompatibilitätsstandard“ auf der Seite „Standards – Berichterstellung und Kompatibilität“ auf eine andere Option als „Keine“ gesetzt ist.

**Als Fehler melden**: Kennzeichnet die PostScript-Datei als nicht kompatibel, wenn eine der Berichterstellungsoptionen ausgewählt ist und ein Endformat- oder Objektrahmen auf einer der Seiten fehlt.

**Endformatrahmen auf Medienrahmen mit Abständen festlegen**: Berechnet Werte in Punkten für den Endformatrahmen basierend auf den Abständen des Medienrahmens auf entsprechenden Seiten, wenn weder der Endformatrahmen noch der Objektrahmen angegeben ist. Der Endformatrahmen ist stets genau so klein wie oder kleiner als der umgehende Medienrahmen.

**Wenn kein Anschnittrahmen festgelegt ist**: Diese Option ist verfügbar, wenn auf der Seite „Standards – Berichterstellung und Kompatibilität“ die Option „Kompatibilitätsstandard“ auf eine andere Option als „Keine“ festgelegt ist.

**Anschnittrahmen auf Medienrahmen festlegen**: Verwendet die Medienrahmenwerte für den Anschnittrahmen, wenn der Anschnittrahmen nicht angegeben ist.

**Anschnittrahmen auf Endformatrahmen mit Abständen festlegen**: Berechnet Werte in Punkten für den Anschnittrahmen basierend auf den Abständen des Endformatrahmens auf entsprechenden Seiten, wenn der Anschnittrahmen nicht angegeben ist. Der Anschnittrahmen ist stets genau so groß wie oder größer als der umgehende Endformatrahmen.

**Standardwerte, sofern nicht im Dokument festgelegt**: Diese Option ist verfügbar, wenn „Kompatibilitätsstandard“ auf der Seite „Standards – Berichterstellung und Kompatibilität“ auf eine andere Option als „Keine“ gesetzt ist.

**Profilname der Ausgabebedingung**: Gibt die gekennzeichnete Druckbedingung an, für die das Dokument vorbereitet wurde. Wenn in einem Dokument kein OutputIntent-Name angegeben wird, verwendet PDF Generator den in diesem Menü ausgewählten Wert. Sie können einen der angegebenen Namen auswählen oder einen Namen in das Feld eingeben. Wenn Ihr Workflow erfordert, dass das Dokument die Ausgabebedingung angibt, wählen Sie &quot;Ohne&quot;aus. Jedes Dokument, das die Anforderung nicht erfüllt, schlägt bei der Kompatibilitätsprüfung fehl.

**Ausgabebedingungs-ID**: Gibt den Referenznamen an, der von der Registrierung des Profilnamens der Ausgabebedingung angegeben wird.

**Ausgabebedingung**: Beschreibt die beabsichtigte Druckbedingung. Dieser Eintrag kann für den vorgesehenen Empfänger des PDF-Dokuments nützlich sein.

**Registrierungsname (URL)**: Gibt die Internetadresse an, unter der weitere Informationen zur Registrierung bereitgestellt werden. Der URL wird für ICC-Registrierungsnamen automatisch eingegeben.

**Überfüllung**: Gibt den Überfüllungsstatus im Dokument an. Für die Einhaltung von PDF/X ist der Wert True oder False erforderlich. Wenn das Dokument nicht den Überfüllungsstatus angibt, wird der hier angegebene Wert verwendet. Wenn Ihr Workflow erfordert, dass das Dokument den Überfüllungsstatus angibt, wählen Sie &quot;Nicht definiert&quot;aus. Jedes Dokument, das die Anforderung nicht erfüllt, schlägt bei der Kompatibilitätsprüfung fehl.

### Optionen für PDF/A-Standard {#options-for-pdf-a-standard}

Diese Optionen sind aktiviert, wenn die Kompatibilität (im Bereich &quot;Allgemein&quot;) auf Acrobat 4 (PDF 1.3) oder Acrobat 5 (PDF 1.4) festgelegt ist.

**Bei Nicht-Kompatibilität**: Gibt an, ob die PDF-Datei auch dann erstellt werden soll, wenn die PostScript-Datei nicht die PDF/A-Anforderungen erfüllt.

**Fortfahren**: Erstellt eine PDF-Datei selbst dann, wenn die PostScript-Datei die Standardanforderungen nicht erfüllt.

**Auftrag abbrechen**: Erstellt eine PDF-Datei nur, wenn die PostScript-Datei PDF/A-Anforderungen erfüllt und ansonsten gültig ist.

**Profilname der Ausgabebedingung**: Gibt die gekennzeichnete Druckbedingung, für die das Dokument vorbereitet wurde, an und ist für PDF/A-Kompatibilität erforderlich. Wenn Ihr Workflow es erfordert, dass das Dokument die Ausgabebedingung angibt, wählen Sie „Keine“ aus. Das Dokument wird bei der Kompatibilitätsüberprüfung fehlschlagen, wenn diese Informationen nicht bereitgestellt werden.

**Ausgabebedingung**: Beschreibt die beabsichtigte Druckbedingung. Dieser Eintrag ist nicht erforderlich, kann aber verwendet werden, um nützliche Informationen für den vorgesehenen Empfänger des PDF-Dokuments bereitzustellen.

## Optionen für die Erstansicht {#initial-view-options}

Diese Optionen sind in drei Bereiche unterteilt: Dokumentoptionen, Fensteroptionen und Benutzeroberflächenoptionen. Anweisungen zum Zugriff auf die Optionen für die Ansicht beim Öffnen finden Sie unter [PDF-Einstellungen hinzufügen oder bearbeiten](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Um Optionen zu verwenden, wählen Sie &quot;Einstellungen für die Ansicht beim Öffnen festlegen&quot;aus.

### Dokumentoptionen {#document-options}

Die Dokumentoptionen steuern das Erscheinungsbild des Dokuments im Dokumentfenster, z. B. die Vergrößerung und den Bildlauf.

**Anzeigen**: Bestimmt, welche Bereiche und Registerkarten standardmäßig im Programmfenster angezeigt werden. „Lesezeichenfenster und Seite“ öffnet den Dokumentbereich und die Registerkarte „Lesezeichen“.

**Seiten-Layout**: Bestimmt, ob das Dokument im Modus „Einzelne Seite“, „Doppelseite“, „Fortlaufende Seite“ oder „Fortlaufend – Doppelseiten“ angezeigt wird.

**Vergrößerung**: Legt den Vergrößerungsgrad fest, mit dem das Dokument nach dem Öffnen angezeigt wird. Die Standardeinstellung verwendet den vom Benutzer in den Acrobat- oder Adobe Reader-Voreinstellungen festgelegten Vergrößerungswert.

**Auf folgender Seite öffnen**: Legt die Seite fest, auf der das Dokument geöffnet wird, normalerweise Seite 1.

>[!NOTE]
>
>Durch Festlegen von &quot;Standard&quot;für die Vergrößerungs- und Seitenlayoutoptionen werden die individuellen Benutzereinstellungen in den Seitenanzeigeeinstellungen in Acrobat oder Adobe Reader verwendet.

### Fensteroptionen {#window-options}

Die Fensteroptionen bestimmen, wie sich das Fenster im Bildschirmbereich anpasst, wenn ein Benutzer das Dokument öffnet. Die Optionen wirken sich jedoch nicht aus, wenn ein PDF-Dokument in einem Webbrowser angezeigt wird.

**Größe des Fensters auf Anfangsseite ändern**: Passt das Dokumentfenster gemäß den Optionen, die Sie unter „Dokumentoptionen“ ausgewählt haben, passgerecht an die Eröffnungsseite an.

**Fenster auf Bildschirm zentrieren**: Positioniert das Fenster in der Mitte des Bildschirmbereichs.

**Im Vollbildmodus öffnen**: Maximiert das Dokumentfenster und zeigt das Dokument ohne Menüleiste, Symbolleiste und Fenstersteuerelemente an.

**Anzeigen**: „Dateiname“ zeigt den Dateinamen in der Titelleiste des Fensters an. Der Dokumenttitel zeigt den Dokumenttitel in der Titelleiste des Fensters an.

### Optionen der Benutzeroberfläche {#user-interface-options}

Die Optionen der Benutzeroberfläche bestimmen, welche Steuerelemente beim Öffnen des Dokuments angezeigt oder ausgeblendet werden.

**Menüleiste ausblenden**: Blendet, falls ausgewählt, die Menüleiste aus.

**Symbolleisten ausblenden**: Blendet, falls ausgewählt, die Symbolleisten aus.

**Fenstersteuerelemente ausblenden**: Blendet, falls ausgewählt, die Fenstersteuerelemente aus.

>[!NOTE]
>
>Wenn Sie die Menüleiste und Symbolleiste ausblenden, können Benutzer keine Befehle anwenden und Tools auswählen, es sei denn, sie kennen die Tastaturbefehle, wenn sie die Datei in Acrobat öffnen.

## Hochladen und Herunterladen von Prologue- und Epilogue-Dateien {#uploading-and-downloading-prologue-and-epilogue-files}

Prologue-Dateien werden verwendet, um benutzerdefinierten PostScript-Code hinzuzufügen, der zu Beginn jedes zu destillierenden PostScript-Auftrags ausgeführt wird. Epilogue-Dateien werden verwendet, um benutzerdefinierten PostScript-Code hinzuzufügen, der am Ende jedes PostScript-Auftrags ausgeführt wird. Sie können Prologue- und Epilogue-Dateien vom Server herunterladen, um sie lokal zu speichern. Sie können die Dateien herunterladen, um sie unabhängig voneinander zu konfigurieren oder an einen anderen Speicherort oder auf einen anderen Computer hochzuladen.

Diese Dateien haben viele Zwecke. Beispielsweise können Prologue-Dateien so bearbeitet werden, dass sie Titelseiten angeben. Epilogue-Dateien können bearbeitet werden, um eine Reihe von Prozeduren in einer PostScript-Datei aufzulösen. Sie können auch die Prologue- und Epilogue-Dateien auswählen und hochladen, die mit jedem Auftrag gesendet werden sollen.

### Prologue- oder Epilogue-Datei herunterladen {#download-a-prologue-or-epilogue-file}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Adobe PDF-Einstellungen&quot;.
1. Klicken Sie auf Neu oder auf den Namen einer Einstellung.
1. Klicken Sie auf &quot;Erweitert&quot;und dann neben der Option Prologue.ps und Epilogue.ps verwenden auf &quot;Herunterladen&quot;.
1. Klicken Sie auf der Seite &quot;Prologue- und Epilogue-Dateien herunterladen&quot;auf Prologue.ps oder Epilogue.ps und klicken Sie auf Speichern.

### Eine Prologue- oder Epilogue-Datei hochladen {#upload-a-prologue-or-epilogue-file}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Adobe PDF-Einstellungen&quot;.
1. Klicken Sie auf Neu oder auf den Namen einer Einstellung.
1. Klicken Sie auf &quot;Erweitert&quot;und dann neben der Option &quot;Prologue.ps und Epilogue.ps verwenden&quot;auf &quot;Hochladen&quot;.
1. Klicken Sie auf der Seite &quot;Prologue- und Epilogue-Dateien hochladen&quot;auf Durchsuchen , um eine Prologue- oder Epilogue-Datei auszuwählen.
1. Suchen Sie die Datei und klicken Sie auf &quot;Öffnen&quot;.
1. Um die Datei zu verwenden, stellen Sie sicher, dass auf der Seite &quot;Adobe PDF-Einstellung - Neu/Bearbeiten&quot;im Bereich &quot;Erweitert&quot;die Option Prologue.ps und Epilogue.ps verwenden ausgewählt ist.
1. Klicken Sie auf „Speichern“.

>[!NOTE]
>
>PDF Generator unterstützt nur Prologue- und Epilogue-Dateien zur Konvertierung von PostScript- und Encapsulated PostScript-Dateien in PDF.
