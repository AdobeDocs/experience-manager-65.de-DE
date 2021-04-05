---
title: Dateitypeinstellungen konfigurieren
seo-title: Dateitypeinstellungen konfigurieren
description: Erfahren Sie, wie Sie Dateitypeinstellungen konfigurieren.
seo-description: Erfahren Sie, wie Sie Dateitypeinstellungen konfigurieren.
uuid: ab037659-c6ff-4de9-9417-f5a6fc8122cb
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
discoiquuid: ab19b248-8931-4cf6-b6a5-fb7b067c4a49
feature: PDF Generator
translation-type: tm+mt
source-git-commit: 3bb12f6323398971ec315f49611a39977bd548a2
workflow-type: tm+mt
source-wordcount: '6171'
ht-degree: 81%

---


# Dateitypeinstellungen konfigurieren {#configuring-file-type-settings}

In PDF Generator können Sie die Anwendungseinstellungen für unterstützte Dateitypen einrichten. Unter Windows können Sie die Anwendungseinstellungen für jeden unterstützten Dateityp einrichten. Unter UNIX und Linux können Sie die Anwendungseinstellungen für HTML-in-PDF und OpenOffice einrichten.

Auf der Seite „Dateitypeinstellungen“ können Sie die folgenden Aufgaben ausführen:

* [Erstellen oder Bearbeiten einer Dateitypeinstellung](#create-or-edit-file-type-settings)
* Geben Sie an, welche Dateitypeinstellungen standardmäßig verwendet werden sollen (siehe [PDF Generator-Konfigurationsdateien importieren und exportieren](/help/forms/using/admin-help/importing-exporting-pdf-generator-configuration.md))
* [Standardeinstellungen ändern](/help/forms/using/admin-help/configuring-file-type-settings.md#change-the-default-settings)
* [PDF/A-Unterstützung aktivieren](/help/forms/using/admin-help/enable-pdf-a-support.md)
* [Eine Dateitypeinstellung löschen](/help/forms/using/admin-help/enable-pdf-a-support.md)

>[!NOTE]
>
>Die Dateitypeinstellungen sind nicht für die Ersatzkonverter wie Acrobat für HTML in PDF-Konvertierungen, Microsoft PowerPoint, Microsoft Word und Microsoft Excel verfügbar.

## Dateitypeinstellungen erstellen und bearbeiten {#create-or-edit-file-type-settings}

Sie erstellen oder bearbeiten eine Dateitypeinstellung, um anzugeben, wie die Anwendung die Konvertierung unterstützter Dateitypen durchführen soll. Unter Windows können Sie die Anwendungseinstellungen für jeden unterstützten Dateityp einrichten. Unter UNIX und Linux können Sie die Anwendungseinstellungen für HTML-in-PDF und OpenOffice einrichten.

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste]** > **[!UICONTROL PDF Generator]** > **[!UICONTROL Dateitypeinstellungen]**.
1. Klicken Sie auf „Neu“ oder auf den Namen einer Einstellung.
1. Geben Sie in das Feld „Dateinamenerweiterungen“ die Dateinamenerweiterungen (getrennt durch Kommas) für von dieser Anwendung akzeptierte Dateitypen ein. Setzen Sie vor die Erweiterungen kein Komma und kein Leerzeichen zwischen die Erweiterungen. Der Standardwert lautet `bmp,gif,jpeg,jpg,tif,tiff,png`.
1. (Optional) Um die optische Zeichenerkennung (OCR) von Text in Grafiken oder Bildern zu aktivieren, wählen Sie „OCR verwenden“ aus und legen Sie die folgenden Optionen fest:

**Primäre OCR-Sprache:** Die Sprache, die die OCR-Engine zum Erkennen der Zeichen verwenden soll. Die Standardeinstellung ist „Deutsch (Deutschland)“.

**Stil der PDF-Ausgabe:** Wählen Sie „Durchsuchbares Bild“ aus, um ein Bitmapbild der Seiten im Vordergrund und den gescannten Text auf einer unsichtbaren Ebene darunter zu erhalten. Die Darstellung der Seite wird nicht geändert, doch der Text wird auswählbar und lesbar. Wählen Sie Formatierter Text &amp; Grafiken aus, um die Originalseite anhand von erkanntem Text, Schriften, Bildern und anderen grafischen Elementen zu rekonstruieren. Die Standardeinstellung ist „Durchsuchbares Bild (exakt)“.

**Bilder neu berechnen:** Reduziert bei Farb-, Graustufen- und Schwarzweißbildern die Anzahl der Pixel. Die Neuberechnung gescannter Bilder erfolgt nach Abschluss der optischen Zeichenerkennung (OCR). Der Standardwert ist „Niedrigste (600 dpi)“. Diese Option ist nicht verfügbar, wenn der „Stil der PDF-Ausgabe“ auf „Durchsuchbares Bild (exakt)“ festgelegt ist.

1. Geben Sie in den folgenden Abschnitten die benötigten Informationen ein:

   [PDF Generator-Konfigurationsdateien importieren und exportieren](/help/forms/using/admin-help/importing-exporting-pdf-generator-configuration.md)

   [Adobe PDF-Exporteinstellungen (nur Windows)](#adobe-pdf-export-settings-windows-only)

   [„HTML in PDF“ -Einstellungen](#html-to-pdf-settings)

   [„Flashvideos in PDF“-Einstellungen](#flash-videos-to-pdf-settings)

   [„XPS in PDF“-Einstellungen](#xps-to-pdf-settings)

   [PDF-Optimierungseinstellungen](/help/forms/using/admin-help/configuring-file-type-settings.md)

   [Microsoft Excel-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-excel-settings-windows-only)

   [Microsoft PowerPoint-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-powerpoint-settings-windows-only)

   [Microsoft Project-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-project-settings-windows-only)

   [Microsoft Word-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-word-settings-windows-only)

   [Microsoft Visio-Einstellungen (nur Windows)](#visio)

   [Microsoft Publisher-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#microsoft-publisher-settings-windows-only)

   [AutoCAD-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#autocad-settings-windows-only)

   [OpenOffice-Einstellungen](/help/forms/using/admin-help/configuring-file-type-settings.md#openoffice-settings)

   [Einstellungen anderer Anwendungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings.md#other-applications-settings-windows-only)

   Um zu einem anderen Abschnitt zu wechseln, klicken Sie auf dessen Link auf der Webseite oder auf eine der Schaltflächen **[!UICONTROL Weiter]** oder **[!UICONTROL Zurück]**.

1. Klicken Sie nach dem Eingeben der Informationen in alle Abschnitte auf **[!UICONTROL Speichern]** oder **[!UICONTROL Speichern unter]** und geben Sie einen Namen für die Einstellung ein.

Die Unterstützung verschiedener Dateitypen kann angepasst werden. (Siehe [Hinzufügen der Unterstützung für weitere native Dateiformate](https://help.adobe.com/en_US/AEMForms/6.1/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-7756.2.html) in [Programmieren mit AEM Forms).](https://www.adobe.com/go/learn_lc_programming_11)

## Standardeinstellungen ändern {#change-the-default-settings}

Sie können die Standardwerte für die Adobe PDF-, Sicherheits- und Dateitypeinstellungen ändern, die für neu erstellte Quellen gültig sind. Das Ändern der Standardwerte hat keine Auswirkung auf die Einstellungen vorhandener Quellen.

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste > PDF Generator]**.
1. Klicken Sie auf der Seite **[!UICONTROL Adobe PDF-Einstellungen]**, **[!UICONTROL Dateitypeinstellungen]** oder **[!UICONTROL Sicherheitseinstellungen]**  auf **[!UICONTROL Standardeinstellungen festlegen]**.
1. Wählen Sie Ihre bevorzugten Standardeinstellungen. Mindestens eine der folgenden Einstellungen ist auf der Seite „Standardeinstellungen festlegen“ verfügbar:

   **[!UICONTROL Adobe PDF-Einstellung]**: Die ursprüngliche Standardeinstellung ist &quot;Standard (Acrobat 6)&quot;.

   **[!UICONTROL Sicherheitseinstellungen]**: Die ursprüngliche Standardeinstellung ist &quot;Keine Sicherheit (Acrobat 5)&quot;.

   **[!UICONTROL Dateitypeinstellungen]**: Die ursprüngliche Standardeinstellung ist Standard.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Einstellung „Dateityp löschen“  {#delete-a-file-type-setting}

Eine nicht mehr benötigte Dateitypeinstellung kann gelöscht werden.

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste > PDF Generator > Dateitypeinstellungen]**.
1. Aktivieren Sie das Kontrollkästchen neben der zu löschenden Einstellung. Sie können mehrere Quellen auswählen. Einstellungen ohne Kontrollkästchen werden in PDF Generator immer berücksichtigt und können nicht gelöscht werden.
1. Klicken Sie auf der Seite „Löschbestätigung“ auf **[!UICONTROL Löschen]**  und dann nochmals auf **[!UICONTROL Löschen]**.

## „Bild in PDF“-Einstellungen  {#image-to-pdf-settings}

Die folgenden Optionen bestimmen, wie Bilddateien in PDF konvertiert werden. Weitere Informationen zum Zugriff auf diese Einstellungen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Dateinamenerweiterungen:** Kommagetrennte Liste von Dateinamenerweiterungen, die konvertiert werden können.

**Ersatzkonverter versuchen:** PDF Generator kann entweder Java™ oder Acrobat verwenden, um Bilddateien in PDF zu konvertieren. Wenn diese Option aktiviert ist und eine Konvertierung fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mit der anderen Methode auszuführen. Wenn die andere Methode fehlschlägt oder das angegebene Zeitlimit erreicht, wird ein Ausnahmefehler in die Protokolldatei aufgenommen.

>[!NOTE]
>
>JPEG 2000-Dateien können nur mithilfe von Acrobat konvertiert werden.

**OCR verwenden:** Gibt an, ob OCR (optische Zeichenerkennung) auf die PDF-Datei angewendet werden soll. Mit OCR-Software können Sie den Text in einer PDF-Datei durchsuchen, korrigieren und kopieren.

***Hinweis **: Die OCR PDF-Funktion (durchsuchbare PDF) wird nur unter Microsoft Windows unterstützt.*

**Primär OCR Language:** Gibt die Sprache an, in der die OCR-Engine die Zeichen identifizieren soll.

**Stil der PDF-Ausgabe:** Legt den Typ der zu erstellenden PDF-Datei fest. Alle Formate wenden OCR und Schriftart- und Seitenerkennung auf die Bilder im Text an und konvertieren sie in normalen Text.

**Durchsuchbares Bild:** Stellt sicher, dass der Text durchsuchbar und auswählbar ist. Diese Option behält das Originalbild bei, stellt es bei Bedarf gerade und platziert eine unsichtbare Textebene darüber. Die Option „Bilder neu berechnen“ bestimmt, ob und in welchem Umfang das Bild neu berechnet wird.

**Durchsuchbares Bild (exakt):** Stellt sicher, dass der Text durchsuchbar und auswählbar ist. Diese Option behält das Originalbild bei und platziert eine unsichtbare Textebene darüber. Empfohlen für Fälle, in denen maximale Übereinstimmung mit dem Originalbild erforderlich ist.

**ClearScan:** Führt eine neue Type 3-Schrift zusammen, die dem Original sehr nahe kommt und den Seitenhintergrund mithilfe einer Kopie mit niedriger Auflösung beibehält.

**Bilder neu berechnen:** Reduziert die Anzahl der Pixel in Farb-, Graustufen- und Schwarzweißbildern, nachdem der OCR-Vorgang abgeschlossen ist. Wählen Sie den anzuwendenden Grad der Neuberechnung aus. Bei Optionen mit einem höheren Wert werden weniger Neuberechnungen ausgeführt. Dadurch werden PDF-Dateien mit höherer Auflösung erstellt.

## Adobe PDF-Exporteinstellungen (nur Windows)  {#adobe-pdf-export-settings-windows-only}

Die Einstellung „Exportdateityp“ im Abschnitt mit den Einstellungen für „Adobe PDF-Export“ wird zum Konvertieren einer PDF-Datei in ein anderes Format verwendet. Die Standardeinstellung ist HTML 4.01 mit Cascading Style Sheets (CSS) 1.0(*.htm, *.html).

Weitere Informationen zum Zugriff auf diese Einstellung finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

## „HTML in PDF“-Einstellungen  {#html-to-pdf-settings}

Die folgenden Optionen bestimmen, wie HTML-Dateien in PDF konvertiert werden. Informationen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen und bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Fallback-Konverter versuchen:** PDF Generator kann entweder Java™ oder Acrobat verwenden, um HTML-Dateien in PDF zu konvertieren. Wenn diese Option aktiviert ist und eine Konvertierung fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mit der anderen Methode auszuführen. Wenn die andere Methode fehlschlägt oder das angegebene Zeitlimit erreicht, wird ein Ausnahmefehler in die Protokolldatei aufgenommen.

**Standardkodierung:** Legt die Eingabekodierung des Dateitextes aus einem Menü mit Betriebssystemen und Alphabeten fest. Verwendet die Auswahl, die in der Option „Standardkodierung“ angezeigt wird, nur dann an, wenn die HTML-Quelldatei keinen Kodierungstyp angibt.

**Erzwingen der ausgewählten Kodierung:** Ignoriert alle Kodierungen, die in der HTML-Quelldatei angegeben sind, und verwendet die Auswahl, die in der Option &quot;Standardkodierung&quot;angezeigt wird.

### Einstellungen für Spidern {#spidering-settings}

*Beim Spidern werden Webseiten auf Links zu anderen Webseiten untersucht.* Wird ein Link zu einer anderen Webseite gefunden, wird die Zielseite abgerufen und in das generierte PDF-Dokument eingefügt. Aktivieren Sie diese Optionen, um die Anzahl der Ebenen festzulegen, die abgerufen und in PDF konvertiert werden sollen:

**Nur X-Stufen abrufen:** Spiders und Konvertiert Seiten bis zu einer Tiefe der angegebenen Ebene aus der Basis-Seiten-URL. Beim Wert 1 wird nur der angegebene URL konvertiert.

**Gesamte Site abrufen:** Konvertiert die gesamte Site, ausgehend von der bereitgestellten URL.

**Auf demselben Pfad beibehalten:** Links, die auf Seiten verweisen, die sich nicht im selben relativen Pfad wie die Basis-URL befinden, werden beim Spidern nicht konvertiert.

**Server beibehalten:** Links, die auf Seiten auf verschiedenen Servern verweisen, werden beim Spidern nicht konvertiert. Nur Links, die auf denselben Server wie die angegebene URL verweisen, werden konvertiert.

### Seitenkonvertierungseinstellungen  {#page-conversion-settings}

Aktivieren Sie diese Optionen, um anzugeben, wie HTML-Seiten konvertiert werden. Basierend auf der Seitengröße werden die Werte für Breite, Höhe und Rand entsprechend angepasst.

**Seitenformat:** Wählen Sie &quot;Benutzerdefiniert&quot;und geben Sie die Breite und Höhe an oder wählen Sie vordefinierte Dimensionen aus.

**Ausrichtung:** Wählen Sie für das konvertierte PDF-Dokument entweder Hochformat oder Querformat aus.

**Ränder:** Gibt die Ränder (oben, unten, links und rechts) im erstellten PDF-Dokument an.

**hinzufügen Lesezeichen in PDF:** Fügt dem PDF-Dokument Lesezeichen hinzu.

**Tagged PDF aktivieren:** Bettet Tags in das PDF-Dokument ein.

**Einstellungen für die anfängliche Ansicht festlegen:** Hiermit können Sie Dokument-Optionen, Fensteroptionen und Benutzeroberflächenoptionen konfigurieren. Diese Einstellungen bestimmen, wie der Inhalt anfänglich angezeigt wird.

### Dokumentoptionen  {#document-options}

Aktivieren Sie diese Optionen, um festzulegen, wie Inhalte und Seiten im PDF-Dokument angezeigt werden sollen, und den Vergrößerungsgrad anzugeben:

**Anzeigen:** Wählen Sie die Bereiche aus, die beim Öffnen des PDF-Dokuments in Acrobat geöffnet werden sollen.

**Seitenlayout:** Wählen Sie den Typ des Seitenlayouts für das PDF-Dokument aus.

**Vergrößerung:** Wählen Sie die voreingestellte Vergrößerung für die anfängliche Ansicht des PDF-Dokuments oder wählen Sie einen benutzerdefinierten Wert aus. Das Übernehmen der Standardeinstellung bedeutet, dass die Standardvergrößerung von Acrobat verwendet werden soll.

**Auf Seitenzahl öffnen:** Geben Sie die Seitenzahl an, mit der die PDF-Datei geöffnet werden soll.

### Fensteroptionen {#window-options}

Aktivieren Sie diese Optionen, um die Fenstergröße und -anzeige anzugeben.

**Fenstergröße auf Anfangsseite ändern:** Ändert die Größe des Acrobat-Fensters auf die Größe der Anfangsseite.

**Fenster auf Bildschirm zentrieren:** Öffnet das Fenster in der Mitte des Bildschirms.

**Im Vollbildmodus öffnen:** Öffnet das Fenster im Vollbildmodus.

**Anzeigen:** Zeigt den Dokument- oder Dateinamen im Fenster an.

### Benutzeroberflächenoptionen {#user-interface-options}

Aktivieren Sie diese Optionen, um die Fensteranzeige anzugeben.

**Menüleiste ausblenden:** Blendet die Menüleiste im PDF-Dokument aus.

**Werkzeugleisten ausblenden:** Blendet die Werkzeugleisten im PDF-Dokument aus.

**Fenstersteuerelemente ausblenden:** Blendet die Fenstersteuerelemente im PDF-Dokument aus.

## „Flashvideos in PDF“-Einstellungen{#flash-videos-to-pdf-settings}

PDF Generator unterstützt die Funktion zum Senden von Videos für Adobe Flash (SWF- oder FLV-Datei) und zum Erstellen einer PDF-Datei mit eingebettetem Video für Adobe Flash. Bei dieser Konvertierung muss Adobe Flash Player nicht auf dem Formularserver installiert sein. Weitere Informationen zum Zugriff auf diese Option finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Dateinamenerweiterungen:** Kommagetrennte Liste von Dateinamenerweiterungen, die konvertiert werden können.

## „XPS in PDF“-Einstellungen{#xps-to-pdf-settings}

XML Paper Specification (XPS) wird in Windows Printing Machine verwendet. Dies ist ein Microsoft-Format und kann von jeder Microsoft Office-Anwendung erstellt werden. AEM Forms ermöglicht die Konvertierung von XPS-Dateien in PDF.

**Dateinamenerweiterungen:** Eine kommagetrennte Liste aller XPS-Dateinamenerweiterungen, die konvertiert werden können. Derzeit ist nur ein Format verfügbar: .xps.

## PDF-Optimierungseinstellungen {#pdf-optimizer-settings}

PDF Generator unterstützt die Funktion zum Reduzieren der Größe von PDF-Dateien. Ob Sie alle Einstellungen oder nur einige davon verwenden, hängt davon ab, wie Sie die Dateien verwenden möchten, und von den wesentlichen Eigenschaften, über die eine Datei verfügen muss. In den meisten Fällen sind die Standardeinstellungen geeignet zum maximalen Einsparen von Speicherplatz durch das Entfernen von eingebetteten Schriften, das Komprimieren von Bildern und das Entfernen von nicht mehr benötigten Elementen aus den Dateien.

>[!NOTE]
>
>Durch die Optimierung eines digital signierten Dokuments werden die digitalen Signaturen entfernt und ungültig.

Weitere Informationen zum Zugriff auf diese Einstellung finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Zielgruppe PDF-Version:** Gibt die Version von Acrobat an, mit der die PDF-Datei kompatibel ist.

### Schriften {#fonts}

1. Wählen Sie **Schriftarten**.
1. Wählen Sie eine der folgenden Optionen aus:

   **Einbettung für alle Schriftarten aufheben:** Die Einbettung für alle eingebetteten Schriftarten wird aufgehoben.

   **Einbettung für Schriftarten nicht aufheben: Einbettung für Schriftarten** wird nicht aufgehoben.

   **Einbettung für einige Schriftarten aufheben:** Die Einbettung wird nur für die angegebenen Schriftarten aufgehoben. Führen Sie diese Schritte aus, um die Einbettung für die gewünschten Schriftarten aufzuheben:

   * Wählen Sie bei Bedarf einen anderen Schriftartenordner aus dem Dropdownmenü **Schriftquelle**. Dieses Dropdownmenü enthält Schriftartenordner, die in **Startseite > Einstellungen > Core-System > Core-Konfigurationen** angegeben wurden.
   * Wählen Sie mindestens eine Schriftart aus der Liste **Verfügbare Schriftarten** und klicken Sie auf **Hinzufügen**. Diese Schriftarten werden der Liste **Einbettung für folgende Schriftarten aufheben** hinzugefügt.
   * Wenn Sie die Einbettung für einige Schriftarten aufheben möchten, die auf dem Formularserver nicht vorhanden sind, geben Sie die Namen dieser Schriftarten in das Feld **Schriftarten für die Aufhebung der Einbettung hinzufügen** ein. Klicken Sie auf **Hinzufügen**.

   >[!NOTE]
   >
   >*Wenn Sie die Einbettung für einige Schriftarten aufheben möchten, deren Untergruppen im Dokument eingebettet sind, setzen Sie das Symbol „+“ vor den Namen der Schriftart. Beispiel: „+Helvetica“.*

1. Wenn Sie lediglich die verwendeten Untergruppen der eingebetteten Schriftarten einbetten möchten, wählen Sie **Alle eingebetteten Schriftarten in Untergruppe zusammenfassen**.

   >[!NOTE]
   >
   >*Wenn Sie diese Option zusammen mit **Einbettung für einige Schriftarten**aufheben verwenden, sind die Schriftarten in den **Hinzufügen, die**nicht eingebettet werden sollen, weiterhin vollständig nicht eingebettet.*

   >[!NOTE]
   >
   >*Schrifteinbettung in Untergruppen ist eine Vorgehensweise für die Einbettung eines Teils einer Schriftart. Eine Schriftartuntergruppe enthält nur die im Dokument verwendeten Zeichen.*

### Transparenz  {#transparency}

Wenn das PDF-Dokument Grafiken mit Transparenz enthält, können Sie die PDF-Optimierungseinstellungen verwenden, um die Transparenz und die Dateigröße zu reduzieren.

>[!NOTE]
>
>Wenn Acrobat 4.0 und höher als Ziel-PDF-Version ausgewählt wird, werden alle transparenten Objekte reduziert. Für andere Ziel-PDF-Versionen wird Transparenz unterstützt und Sie können die Transparenzeinstellungen konfigurieren.

Wählen Sie die **Transparenz**, um die Transparenzeinstellungen beim Optimieren der PDF-Dokumente zu konfigurierenden 

**Transparenzstufe** Gibt die Menge der Vektorinformationen an, die beibehalten werden. Bei einer höheren Einstellung werden mehr Vektorobjekte beibehalten, bei einer niedrigeren Einstellung werden mehr Vektorobjekte gerastert. Mittlere Einstellungen behalten einfache Bereiche im Vektorformat bei und rastern komplexe Bereiche. Wählen Sie die niedrigste Einstellung aus, um alle mit Transparenz versehenen Grafiken zu rastern.

>[!NOTE]
>
>Die vorgenommene Umwandlung in Pixelbilder hängt von der Komplexität der Seite und den Arten der überlappenden Objekte ab.

**Strichgrafiken und** TextAuflösung, auf die alle Objekte, einschließlich Bilder, Vektorgrafiken, Text und Verläufe, gerastert werden. Die unterstützten Werte sind 1 Pixel pro Inch (ppi, Bildpunkte pro Zoll) bis 9600 ppi.

>[!NOTE]
>
>Die Auflösung von Strichgrafiken und Text sollte grundsätzlich auf einen Bereich von 600 bis 1200 ppi eingestellt werden, um eine hochwertige Rasterung zu erzielen, insbesondere bei Serifenschriften und kleinen Schriftarten.

**Verlauf und** GitterAuflösung, auf die Verlauf und Gitter gerastert werden. Die unterstützten Werte sind 1 ppi bis 1200 ppi.

>[!NOTE]
>
>Die Auflösung für Verlauf und Gitter sollte im Allgemeinen auf 150 bis 300 ppi eingestellt werden, da sich die Qualität von Verläufen, Schlagschatten und weichen Kanten mit höheren Auflösungen nicht verbessert. Hingegen wird durch höhere Auflösungen die Druckzeit verlängert und die Datei unnötig vergrößert.

**Alle Text in** Umrisse konvertierenKonvertiert alle Textobjekte (Punkttyp, Flächentext und Pfadtyp) in Umrisse und verwirft alle Textglyphen-Informationen auf Seiten, die Transparenz enthalten. Mit dieser Option wird sichergestellt, dass die Breite von Text beim Reduzieren unverändert bleibt. Bitte beachten Sie, dass bei dieser Option kleine Schriften etwas breiter wirken, wenn die Datei in Acrobat geöffnet oder auf Desktop-Druckern mit niedriger Auflösung gedruckt wird. Sie hat keinen Einfluss auf die Textqualität, wenn die Datei auf Druckern mit hoher Auflösung oder Belichtern gedruckt wird.

**Alle Konturen in** Pfade konvertierenKonvertiert alle Konturen auf Seiten mit Transparenz in einfache ausgefüllte Pfade. Mit dieser Option wird sichergestellt, dass die Breite von Konturen beim Reduzieren unverändert bleibt. Beachten Sie, dass dünne Konturen geringfügig dicker angezeigt werden und die Leistung des Reduzierens beeinträchtigen werden könnte, wenn Sie diese Option aktivieren.

**Komplexe** Bereiche beschneidenStellt sicher, dass die Begrenzungen zwischen Vektorgrafiken und gerasterten Grafiken entlang von Objektpfaden verlaufen. Mit dieser Option werden sichtbare Übergänge bei Grafiken vermieden, wenn ein Teil eines og

<!--
NOTE to WRITER: Unfinished sentence above.
-->

>[!NOTE]
>
>Die Verarbeitungsweise von Vektor- und Rasterbildern unterscheidet sich je nach verwendetem Druckertreiber und es kann manchmal zu sichtbaren Farbübergängen kommen. Sie können dieses Problem minimieren, indem Sie einige für den jeweiligen Druckertreiber spezifische Farbmanagement-Einstellungen deaktivieren. Da diese Einstellungen bei jedem Drucker anders sind, lesen Sie bitte für weitere Informationen die Dokumentation zu Ihrem Drucker.

Überdruck beibehalten: Lässt die Farbe von transparentem Bildmaterial mit der Hintergrundfarbe verschmelzen, um einen Überdruckeffekt zu erzielen.

Die folgende Tabelle zeigt die gängigsten Typen von Druckern und ihre in dpi gemessene Auflösung, ihre standardmäßige Rasterweite in lpi (Lines per Inch, Zeilen pro Zoll) und eine Neuberechnungsauflösung für Bilder gemessen in ppi (Pixel per Inch, Bildpunkte pro Zoll). Wenn die Druckausgabe beispielsweise auf einem 600-dpi-Laserdrucker erfolgt, müssen Sie 170 als Auflösung eingeben, mit der Bilder neu berechnet werden sollen.

**Bilder** Wählen Sie Bilder aus, um Komprimierungs- und Neuberechnungsoptionen für Farb-, Graustufen- und Schwarzweißbilder festzulegen. Sie können mit diesen Optionen experimentieren, um einen angemessenen Ausgleich zwischen Dateigröße und Bildqualität zu finden. Die Auflösungseinstellung für Farb- und Graustufenbilder sollte das 1,5- bis 2-fache der Rasterweite betragen, mit der die Datei gedruckt wird. Die Auflösung von Schwarzweißbildern muss derjenigen des Ausgabegeräts entsprechen. Beachten Sie jedoch, dass sich durch das Speichern eines Schwarzweißbildes mit einer höheren Auflösung als 1500 dpi die Datengröße erhöht, ohne dass sich die Bildqualität spürbar verbessert. Bilder, die vergrößert werden, wie z. B. Landkarten, erfordern möglicherweise eine höhere Auflösung.

>[!NOTE]
>
>Das Neuberechnen von Schwarzweißbildern kann bei der Anzeige zu unerwarteten Ergebnissen führen, z. B. keiner Bildanzeige. Tritt dies ein, deaktivieren Sie die Neuberechnung und konvertieren Sie die Datei nochmals. Dieses Problem tritt am ehesten bei der Kurzberechnung und am ehesten nicht bei der bikubischen Neuberechnung auf.

<table>
 <tbody>
  <tr>
   <th><p><strong>Druckerauflösung</strong></p> </th>
   <th><p><strong>Standardrasterweite</strong></p> </th>
   <th><p><strong>Bildauflösung</strong></p> </th>
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

#### Objekte verwerfen  {#discard-objects}

* Wählen Sie die Option **Objekte verwerfen**, um die Objekte anzugeben, die aus der PDF-Datei entfernt werden sollen, und um die gekrümmten Linien in CAD-Zeichnungen zu optimieren.
* **Alle Sende-, Import- und Zurücksetzungsaktionen für Formulare verwerfen**: Deaktiviert alle Aktionen im Zusammenhang mit dem Senden oder Importieren von Formulardaten und setzt Formularfelder zurück. Diese Option behält Formularobjekte, die mit Aktionen verknüpft sind, bei.
* **Alle JavaScript-Aktionen verwerfen**: Entfernt alle Aktionen aus der PDF-Datei, die JavaScript verwenden.
* **Eingebettete Kleinbilder der Seiten verwerfen:** Eingebettete Seitenminiaturansichten verwerfen. Diese Option bietet sich für große Dokumente an, bei denen das Zeichnen der Kleinbilder der Seiten nach dem Klicken auf die Schaltfläche „Seiten“ sehr lange dauern kann.
* **Geglättete Linien in Kurven konvertieren:** Verringert die Anzahl von Steuerpunkten zum Erstellen von Kurven in CAD-Zeichnungen, was zu kleineren PDF-Dateien und einer schnelleren Bildschirmwiedergabe führt.
* **Eingebettete Druckeinstellungen verwerfen**: Entfernt eingebettete Druckeinstellungen aus dem Dokument, z. B. Seitenskalierung und Duplexmodus.
* **Lesezeichen verwerfen**: Entfernt alle Lesezeichen aus dem Dokument.
* **Formularfelder reduzieren**: Macht Formularfelder unbrauchbar, ohne ihr Aussehen zu ändern. Formulardaten werden mit der Seite zusammengeführt und in den Seiteninhalt aufgenommen.
* **Alle alternativen Bilder verwerfen**: Entfernt alle Versionen eines Bildes mit Ausnahme der Version, die für die Anzeige auf dem Bildschirm vorgesehen ist. Einige PDF-Dateien enthalten mehrere Versionen desselben Bildes für verschiedene Zwecke, z. B. niedrige Auflösung für die Anzeige auf dem Bildschirm und hohe Auflösung zum Drucken.
* **Dokument-Tags verwerfen**: Entfernt Tags aus dem Dokument, dadurch werden auch die Eingabehilfe- und die Umfließen-Funktion für den Text entfernt.
* **Bildfragmente erkennen und zusammenführen**: Sucht nach Bildern oder Masken, die in kleine Ausschnitte fragmentiert sind, um diese Ausschnitte in einem einzigen Bild oder einer einzigen Maske zusammenzuführen.
* **Eingebetteten Suchindex verwerfen**: Entfernt eingebettete Suchindizes, dadurch wird die Dateigröße reduziert.

#### Benutzerdaten verwerfen  {#discard-user-data}

Wählen Sie die Option **Benutzerdaten verwerfen**, um alle persönlichen Informationen, die Sie nicht für andere Benutzer freigeben möchten, zu entfernen.

* **Alle Kommentare, Formulare und Multimedia-Dateien verwerfen**: Entfernt alle Kommentare, Formulare, Formularfelder und Multimedia-Dateien aus der PDF-Datei.
* **Alle Objektdaten verwerfen:** Entfernt alle Objekte aus der PDF-Datei.
* **Externe Querverweise verwerfen:** Entfernt Verknüpfungen zu anderen Dokumenten. Verknüpfungen, die an eine andere Stelle innerhalb der PDF-Datei springen, werden nicht entfernt.
* **Ausgeblendeten Inhalt der Ebene verwerfen und sichtbare Ebenen reduzieren:** Reduziert die Dateigröße. Das optimierte Dokument sieht aus wie die ursprüngliche PDF-Datei, enthält jedoch keine Ebeneninformationen.
* **Dokumentinformationen und Metadaten verwerfen:** Entfernt Informationen im Dokumentinformationsordner und alle Metadaten-Datenströme. (Verwenden Sie den Befehl „Speichern unter“, um Metadaten-Datenströme in einer Kopie der PDF-Datei wiederherzustellen.)
* **Dateianlagen verwerfen**: Entfernt alle Dateianlagen, einschließlich der Anlagen, die als Kommentare der PDF-Datei hinzugefügt wurden. (PDF Optimizer optimiert keine angehängten Dateien.)
* **Private Daten anderer Anwendungen verwerfen:** Entfernt Informationen aus einem PDF-Dokument, die nur für die Anwendung hilfreich sind, mit der das Dokument erstellt wurde. Diese Einstellung hat keinen Einfluss auf die Funktionalität der PDF-Datei, aber sie verringert die Dateigröße.

### Bereinigung  {#clean-up}

Wählen Sie **Bereinigung**, um nicht erforderliche Elemente aus dem Dokument zu entfernen.
Zu diesen Elementen gehören veraltete oder für den vorgesehenen Zweck des Dokuments unnötige Elemente. Wenn Sie bestimmte Elemente entfernen, kann dies schwerwiegende Auswirkungen auf die Funktionalität der PDF-Datei haben. Standardmäßig werden nur Elemente, die keinen Einfluss auf die Funktionalität haben, ausgewählt. Wenn Sie nicht sicher sind, welche Auswirkungen das Entfernen anderer Optionen hat, verwenden Sie die Standardauswahl.

**Komprimierung**

Wählen Sie eine der folgenden Flate-Komprimierungsoptionen aus dem Dropdownmenü:

* Gesamte Datei komprimieren
* Dokumentstruktur komprimieren
* Komprimierung entfernen
* Komprimierung unverändert lassen

**Flate-Komprimierung zum Kodieren von nicht kodierten Streams:** Wendet Flate-Komprimierung auf alle nicht kodierten Streams an.

**Ungültige Lesezeichen verwerfen**: Entfernt alle Lesezeichen, die auf gelöschte Seiten im Dokument verweisen.

**Nicht referenzierte benannte Ziele verwerfen**: Entfernt benannte Ziele, auf die nicht intern innerhalb des PDF-Dokuments verwiesen wird. Diese Option überprüft keine Verknüpfungen von anderen PDF-Dateien oder Webseiten.

**PDF-Datei für schnelle Webanzeige optimieren:** Strukturiert das PDF-Dokument für ein seitenweises Herunterladen von Webservern um.

**In Daten-Streams, die LZW-Kodierung verwenden, stattdessen Flate verwenden:** Wendet Flate-Komprimierung auf alle Inhalts-Streams und -Bilder an, die LZW-Kodierung verwenden.

**Ungültige Verknüpfungen verwerfen:** Entfernt Verknüpfungen zu ungültigen Zielen.

**Seiteninhalt optimieren**: Konvertiert alle Zeichen am Ende einer Zeile in Leerzeichen, dadurch wird die Flate-Komprimierung verbessert.

## Microsoft Excel-Einstellungen (nur Windows) {#microsoft-excel-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Excel-Dateien konvertiert werden. Informationen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen und bearbeiten](#create-or-edit-file-type-settings).

**OpenOffice als Ersatzkonverter** versuchen: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft Excel fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mithilfe von OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird ein Ausnahmefehler in die Protokolldatei aufgenommen.

**Dateinamenerweiterungen**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `xls,xlsx`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**PDF/A-1a-kompatible Datei erstellen**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005(RGB)“.

**hinzufügen Lesezeichen auf Adobe PDF**: Konvertiert Excel-Arbeitsblattnamen in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**Arbeitsblatt an eine einzelne Seite** anpassen: Reduziert die Größe des Textes, sodass er auf eine einzelne Seite passt.

**Gesamte Arbeitsmappe** konvertieren: Konvertiert alle Arbeitsblätter in der Excel-Datei. Falls diese Option nicht ausgewählt ist, wird nur die aktuelle Seite konvertiert.

**Makros automatisch** ausführen: Führt vor der Konvertierung des Dokuments alle Makros im Excel-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

**Dokument-Informationen** konvertieren: Fügt PDF-Dokument-Eigenschaften basierend auf den Dokument-Informationen in der Quelldatei hinzu. Dazu gehören Informationen wie der Dokumenttitel, Autor, Betreff und Schlüsselwörter.

**Verknüpfungen zu Adobe PDF hinzufügen:** Konvertiert Hyperlinks in der Quelldatei in Hyperlinks im PDF-Dokument.

**Quelldatei an Adobe PDF** anhängen: Wenn diese Option aktiviert ist, wird die ursprüngliche Excel-Tabelle als Anlage in das generierte PDF-Dokument eingefügt.

**Barrierefreiheit und Reflow mit Tagged Adobe PDF** aktivieren: Bettet Tags in das PDF-Dokument ein, um Barrierefreiheit und Umfließen zu aktivieren.

**Liste der zu ladenden** Excel-Add-Ins: Standardmäßig werden (aus Sicherheitsgründen) keine Excel-Add-Ins ausgeführt, wenn eine Excel-Datei in PDF konvertiert wird. Wenn Sie zulassen möchten, dass bestimmte Excel-Add-Ins während der Konvertierung ausgeführt werden, stellen Sie eine durch Kommas getrennte Liste mit den Namen der Add-Ins bereit.

**Liste der zu konvertierenden** Arbeitsblätter: Wenn dieses Feld leer ist, werden alle Arbeitsblätter in der Excel-Tabelle in die erstellte PDF-Datei aufgenommen. Wenn Sie wahlweise eine Teilmenge der Arbeitsmappen konvertieren möchten, stellen Sie eine durch Kommas getrennte Liste mit den Namen der Arbeitsmappen bereit.

## Microsoft PowerPoint-Einstellungen (nur Windows)  {#microsoft-powerpoint-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft PowerPoint-Dateien konvertiert werden: Informationen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen und bearbeiten](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings).

**[!UICONTROL OpenOffice als Ersatzkonverter versuchen]**: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft PowerPoint fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mithilfe von OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird ein Ausnahmefehler in die Protokolldatei aufgenommen.

**[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Die Standardeinstellung ist ppt,pptx. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Stichwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen:]** Konvertiert PowerPoint-Arbeitsblattnamen in Lesezeichen.  Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Quelldatei an Adobe PDF anfügen:]** Fügt die Quelldatei der PDF-Datei als Anlage hinzu. Standardmäßig ist diese Option deaktiviert.

**[!UICONTROL Eingabehilfe und Umfließen mit Adobe PDF mit Tags aktivieren:]** Bettet Tags in die PDF-Datei ein. Standardmäßig ist diese Option deaktiviert.

**[!UICONTROL Multimedia-Datei in Multimedia-PDF konvertieren:]** Konvertiert, falls möglich, Multimedia in Multimedia-PDF. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Vortragsnotizen konvertieren:]** Konvertiert Vortragsnotizen in PDF.

**[!UICONTROL Makros automatisch ausführen:]** Führt vor dem Konvertieren des Dokuments alle Makros im PowerPoint-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

**[!UICONTROL PDF-Layout auf Druckereinstellungen von PowerPoint basierend:]** Verwendet PowerPoint-Druckereinstellungen für das Layout des PDF-Dokuments.

**[!UICONTROL Verknüpfungen zu Adobe PDF hinzufügen:]** Behält vorhandene Links bei, wenn die Datei konvertiert wurde. Die Darstellung von Links bleibt grundsätzlich unverändert. Links können nur erstellt werden, wenn die Option „Barrierefreiheit aktivieren“ ebenfalls aktiviert ist. Standardmäßig ist diese Option deaktiviert.

**[!UICONTROL Folienübergänge in Adobe PDF speichern:]** Konvertiert Folienübergänge. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Animationen in Adobe PDF speichern:]** Speichert konvertierte Animationen in der PDF-Datei.

**[!UICONTROL Ausgeblendete Folien in PDF-Seiten konvertieren:]** Konvertiert ausgeblendete Folien.

**[!UICONTROL PDF/A-1a-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005(RGB)“. Einige PowerPoint-Funktionen werden beim Erstellen einer PDF-Datei nicht konvertiert. Wenn in für einen PowerPoint-Übergang kein entsprechender Übergang in Acrobat vorhanden ist, wird dieser durch einen ähnlichen Übergang ersetzt. Enthält eine Folie mehrere Animationseffekte, wird nur ein einziger Effekt verwendet. Seitenübergänge und eingeflogene Aufzählungszeichen werden konvertiert.

## Microsoft Project-Einstellungen (nur Windows)  {#microsoft-project-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Project-Dateien konvertiert werden. Informationen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen und bearbeiten](#create-or-edit-file-type-settings).

1. **[!UICONTROL Dateinamenerweiterungen:]** Gibt die Dateinamenerweiterungen für Dateitypen an, die durch Kommas getrennt sind und für diese Anwendung akzeptiert werden. Der Standardwert lautet `mpp`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

1. **[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Stichwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.
1. **[!UICONTROL Quelldatei an Adobe PDF anfügen:]** Fügt die Quelldatei der PDF-Datei als Anlage hinzu.
1. **[!UICONTROL PDF/A-1a-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005(RGB)“.
1. **[!UICONTROL Makros automatisch]** ausführen: Führt vor dem Konvertieren des Dokuments alle Makros im Microsoft Project-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

## Microsoft Word-Einstellungen (nur Windows) {#microsoft-word-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Word-Dateien konvertiert werden. Informationen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen und bearbeiten](#create-or-edit-file-type-settings).

**[!UICONTROL OpenOffice als Ersatzkonverter versuchen]**: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft Word fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mithilfe von OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird ein Ausnahmefehler in die Protokolldatei aufgenommen.

**[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `doc,docx,rtf,txt`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Stichwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen:]** Konvertiert Überschriften in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Quelldatei an Adobe PDF anfügen:]** Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**[!UICONTROL Querverweise und Inhaltsverzeichnisse in Links konvertieren:]** Konvertiert alle Querverweise und Inhaltsverzeichnisse in Links. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Eingabehilfe und Umfließen mit Adobe PDF mit Tags aktivieren:]** Bettet Tags in die PDF-Datei ein. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL PDF/A-1a-kompatible Datei erstellen:]** Erzwingt, falls ausgewählt, die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005(RGB)“.

**[!UICONTROL Makros automatisch ausführen:]** Führt vor dem Konvertieren des Dokuments alle Makros im Word-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

**[!UICONTROL Dokumentmarkierung in Adobe PDF beibehalten:]** Konvertiert die Markierung im Word-Dokument in Anmerkungen in der PDF-Datei.

**[!UICONTROL Verknüpfungen zu Adobe PDF hinzufügen:]** Konvertiert Hyperlinks in der Quelldatei in Hyperlinks im PDF-Dokument.

**[!UICONTROL Fußnoten- und Endnotenlinks konvertieren:]** Erstellt Links von den Anführungen der Fuß- und Endnoten in Anmerkungen im PDF-Dokument.

**[!UICONTROL Angezeigte Kommentare in Notizen in Adobe PDF konvertieren:]** Konvertiert die Kommentare im Word-Dokument zu Textanmerkungen in der PDF-Datei.

**[!UICONTROL Erweiterte Tags aktivieren:]** Fügt erweiterte Tags für erweiterte Eingabehilfen hinzu.

**[!UICONTROL Alle Stile in Lesezeichen konvertieren:]** Konvertiert alle Stile im Word-Dokument zu Lesezeichen in der PDF-Datei.

**[!UICONTROL Bestimmte Stile in Lesezeichen]** konvertieren: Konvertiert die Stile, die Sie im Feld &quot; **[!UICONTROL Stile mit]** Ebenen&quot;definieren, in Lesezeichen im PDF-Dokument.

**[!UICONTROL Stile mit Ebenen With Levels]** Gibt an, welche Stile im Word-Dokument zu Lesezeichen in der PDF-Datei konvertiert werden. Gibt auch die Ebene der Lesezeichen an. Deaktivieren Sie zum Verwenden dieser Funktion die Option **[!UICONTROL Alle Stile in Lesezeichen konvertieren]** und geben Sie die Namen der Stile im folgenden Format an:

**styleName1=level1[,styleName2=level2...]**

Wenn der Name eines Microsoft Word-Stils ein Komma (,) oder Gleichheitszeichen (=) enthält, müssen Sie den Sonderzeichen ein Escape-Zeichen („\_) voranstellen. So müssten Sie z. B. für einen Stil mit dem Namen „Überschrift, 1“ den Wert Überschrift\, 1 angeben.

**Acrobat PDFMaker-Codierung:** Gibt den Codierungstyp der eingegebenen Textdateien für Acrobat PDFMaker an. Wenn Sie beispielsweise eine UTF-8-kodierte Datei verwenden, wählen Sie UTF-8, um optimale Ergebnisse zu erzielen.

## Microsoft Visio-Einstellungen (nur Windows) {#visio}

**Dokumentinformationen konvertieren**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Stichwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert. Diese Option ist standardmäßig aktiviert.

**hinzufügen Links zu Adobe PDF**: Behält alle Links bei. Standardmäßig ist diese Option aktiviert.

**Lesezeichen zu Adobe PDF hinzufügen:** Konvertiert Überschriften in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**Quelldatei an Adobe PDF anfügen:** Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**Ebenen in Adobe PDF** immer reduzieren: Reduziert alle Visio-Ebenen.

**Alle Seiten** konvertieren: Konvertiert alle Seiten der Visio-Datei.

**Ebenenbedienfeld öffnen, wenn es in Adobe Acrobat angezeigt wird**: Öffnet, falls Visio-Ebenen nicht reduziert werden, ein Fenster, in dem Sie die Ebenen angeben können, die in der PDF-Dateien beibehalten werden, wenn sie mithilfe von Acrobat geöffnet werden. Standardmäßig ist diese Option aktiviert.

**PDF/A-1b-kompatible Datei** erstellen: Erzwingt die Verwendung der Adobe PDF-Einstellung PDF/A-1b:2005 (RGB).

**Kommentare in Adobe PDF-Kommentare** konvertieren: Konvertiert Visio-Notizen in PDF-Kommentare.

## Microsoft Publisher-Einstellungen (nur Windows) {#microsoft-publisher-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Publisher-Dateien konvertiert werden. Informationen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen und bearbeiten](#create-or-edit-file-type-settings).

**[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `pub`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

## AutoCAD-Einstellungen (nur Windows)  {#autocad-settings-windows-only}

Diese Optionen bestimmen, wie AutoCAD-Dateien konvertiert werden. Informationen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen und bearbeiten](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings).

**[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `dwg`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Stichwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen:]** Konvertiert Überschriften in Lesezeichen.

**[!UICONTROL Ebenen in Adobe PDF immer reduzieren:]** Reduziert alle AutoCAD-Ebenen.

**[!UICONTROL Ebenenfenster bei Anzeige in Adobe Acrobat öffnen]**:Zeigt die Ebenenstruktur an, wenn die PDF-Datei in Acrobat geöffnet wird.

**[!UICONTROL Alle Layouts konvertieren:]** Nimmt alle Layouts in die PDF auf.

**[!UICONTROL Modellbereich in 3D konvertieren:]** Wenn diese Option aktiviert ist, wird das Modellbereich-Layout in eine 3D-Anmerkung in der PDF-Datei konvertiert.

**[!UICONTROL Verknüpfungen zu Adobe PDF hinzufügen:]** Behält, falls ausgewählt, alle Links bei.

**[!UICONTROL Quelldatei an Adobe PDF anfügen:]** Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**[!UICONTROL PDF/A-1b-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b“.

**[!UICONTROL Alle Ebenen konvertieren]**: Standardmäßig konvertiert PDF Generator nicht alle in AutoCAD-Dateien enthaltenen Ebenen, sondern nur die Standardebene der Datei in PDF. Aktivieren Sie diese Option, um alle Ebenen der Datei zu konvertieren.

**[!UICONTROL Skalierungsinformationen einbetten:]** Behält Skalierungsinformationen von Zeichnungen bei.

**[!UICONTROL Aktuelles Layout zur konvertieren:]** Nimmt nur das aktuelle Layout in die PDF auf.

**[!UICONTROL Liste der zu konvertierenden AutoCAD-Layouts:]** Eine AutoCAD-Zeichnung kann über mehrere Layouts verfügen. Wenn dieses Feld leer ist, sind alle Layouts in der AutoCAD-Zeichnung in dem erstellten PDF-Dokument enthalten. Wenn Sie wahlweise eine Teilmenge der Layouts konvertieren möchten, stellen Sie eine durch Kommas getrennte Liste mit den Namen der Layouts bereit.

## OpenOffice-Einstellungen {#openoffice-settings}

Diese Optionen bestimmen, wie OpenOffice-Dateien konvertiert werden. Informationen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen und bearbeiten](/help/forms/using/admin-help/configuring-file-type-settings.md#create-or-edit-file-type-settings).

**PDFMaker als Ersatzkonverter versuchen**: Wenn diese Option aktiviert ist und eine Konvertierung mit Open Office fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator die Konvertierung mithilfe von PDFMaker auszuführen. Wenn die Konvertierung mithilfe von PDFMaker fehlschlägt oder das angegebene Zeitlimit erreicht, wird ein Ausnahmefehler in die Protokolldatei aufgenommen.

**Dateinamenerweiterungen**: Legen Sie die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `odt,odp,ods,odg,odf,sxw,sxi,sxd`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**Bereich:** Konvertieren Sie alle Seiten oder geben Sie bestimmte Seiten oder einen Seitenbereich an. Wird kein Seitenbereich angegeben, werden alle Seiten konvertiert. Um einen Seitenbereich zu exportieren, wählen Sie das Format 3-6. Um einzelne Seiten zu exportieren, wählen Sie das Format 7;9;11. Mithilfe des Formats 3-6;8;10;12 können Sie eine Kombination aus Seitenbereichen und einzelnen Seiten exportieren.

**Seitenausrichtung**: Nur für einfache Textdateien, wählen Sie für das konvertierte PDF-Dokument entweder „Hochformat“ oder „Querformat“ aus.

**Bilder**: Geben Sie an, wie Bilder konvertiert werden sollen. EPS-Bilder mit eingebetteter Vorschau werden nur als Vorschau exportiert. EPS-Bilder ohne eingebettete Vorschau werden als leere Platzhalter exportiert. Bei der verlustfreien Komprimierung von Bildern bleiben alle Pixel erhalten. Bei der JPEG-Komprimierung in von Bildern und einer hohen Qualitätsstufe bleiben alle Pixel erhalten. Bei einer niedrigen Qualitätsstufe gehen einige Pixel verloren und Artefakte werden hinzugefügt. Die Dateigröße wird allerdings verringert.

**Allgemein**: Aktivieren Sie die Optionen, um eine PDF-Datei mit Tags zu konvertieren oder Writer- und FormCalc-Dokumentnotizen, Impress-Folienübergangseffekte oder leere Seiten in die PDF-Datei zu exportieren. Beim Export von Tags kann die Dateigröße drastisch zunehmen. Einige Tags, die exportiert werden, sind Inhaltsverzeichnisse, Hyperlinks und Steuerelemente.

Sie können auch angeben, wie Formulare gesendet werden. Die Optionen sind XML, FDF, PDF oder HTML. Diese Einstellung setzt die URL-Eigenschaft des Steuerelements außer Kraft, die Sie im Dokument festgelegt haben. Nur eine allgemein Einstellung kann für das PDF-Dokument ausgewählt werden:

* PDF (sendet das gesamte Dokument)
* FDF (sendet den Inhalt von Steuerelementen)
* HTML
* XML

**PDF mit Tags**: Aktiviert das Erstellen von PDF-Dateien mit Tags aus OpenOffice-Dokumenten. PDF-Dateien mit Tags enthalten Informationen über die Struktur der Dokumentinhalte. Dies kann beim Anzeigen des Dokuments auf Geräten mit verschiedenen Bildschirmen und beim Verwenden von Bildschirmlesehilfe-Software behilflich sein. PDF-Dateien mit Tags können auch Bildschirmlesehilfe-Software helfen, verschiedene nützliche Vorgänge mit dem PDF-Dokument auszuführen, z. B. lautes Vorlesen der Inhalte des PDF-Dokuments.

**Hinweise exportieren**: Konvertiert die Hinweise in OpenOffice-Dokumenten zu Anmerkungen im generierten PDF-Dokument.

**Übergangseffekte verwenden:** Konvertiert die Folienübergangseffekte in OpenOffice-Präsentationen in entsprechende PDF-Übergangseffekte.

**Formulare in Format senden**: Erstellt ein PDF-Formular, das von dem Benutzer des PDF-Dokuments ausgefüllt und gedruckt werden kann.

**Automatisch eingefügte leere Seiten exportieren**: Wenn diese Option aktiviert ist, sind alle automatisch eingefügten leeren Seiten in dem generierten PDF-Dokument enthalten. Dies ist nützlich, wenn Sie ein PDF-Dokument doppelseitig drucken möchten. So kann beispielsweise ein Buch so konfiguriert sein, dass die erste Seite eines Kapitels immer auf einer Seite mit ungerader Seitenzahl beginnt. Wenn das vorherige Kapitel auf einer Seite mit ungerader Seitenzahl endet, fügt OpenOffice eine leere Seite mit gerader Seitenzahl ein. Diese Option kontrolliert, ob diese Seite mit gerader Seitenzahl in der generierten PDF-Datei enthalten ist.

## Andere Anwendungseinstellungen (nur Windows) {#other-applications-settings-windows-only}

Sie können die Einstellungen für andere Anwendungen nicht mithilfe von Administration Console ändern, sie zeigen die Dateinamenerweiterungen für die unterstützten Dateitypen an. Weitere Informationen zum Zugriff auf diese Einstellungen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](https://help.adobe.com/en_US/AEMForms/6.1/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7e42.2.html).

* Corel WordPerfect:  `wpd`
* Adobe PageMaker: `pmd, pm6, p65, pm`
* Adobe FrameMaker: `fm`
* Adobe Photoshop: `psd`

Die Unterstützung dieser Dateitypen muss ggf. angepasst werden. Weitere Informationen finden Sie unter &quot;Hinzufügen der Unterstützung für weitere native Dateiformate&quot;in [Programmieren mit AEM Formularen](https://www.adobe.com/go/learn_aemforms_programming_62).

Wenn Sie Hilfe bei der Konfiguration eines PDFG-Netzdruckers benötigen, finden Sie weiter Informationen unter[ Einrichten eines PDFG-Netzdruckers (nur Windows)](/help/forms/using/admin-help/setting-pdfg-network-printer-windows.md).
