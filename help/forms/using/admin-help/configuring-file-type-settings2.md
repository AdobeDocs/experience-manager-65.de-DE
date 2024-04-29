---
title: Konfigurieren von Dateitypeinstellungen
description: Erfahren Sie, wie Sie Dateitypeinstellungen konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: ht
source-wordcount: '6159'
ht-degree: 100%

---


# Konfigurieren von Dateitypeinstellungen {#configuring-file-type-settings}

In PDF Generator können Sie die Anwendungseinstellungen für unterstützte Dateitypen einrichten. Unter Windows können Sie die Anwendungseinstellungen für jeden unterstützten Dateityp einrichten. Unter UNIX und Linux können Sie die Anwendungseinstellungen für HTML-to-PDF und OpenOffice einrichten.

Auf der Seite „Dateitypeinstellungen“ können Sie die folgenden Aufgaben ausführen:

* [Erstellen oder Bearbeiten einer Dateitypeinstellung](#create-or-edit-file-type-settings)
* Geben Sie an, welche Dateitypeinstellungen standardmäßig verwendet werden sollen (siehe [PDF Generator-Konfigurationsdateien importieren und exportieren](https://helpx.adobe.com/de/aem-forms/6-2/admin-help/importing-exporting-pdf-generator-configuration.html))
* [Standardeinstellungen ändern](/help/forms/using/admin-help/configuring-file-type-settings2.md#change-the-default-settings)
* [Aktivieren der PDF/A-Unterstützung](https://helpx.adobe.com/de/aem-forms/6-2/admin-help/enable-pdf-a-support.html)
* [Löschen einer Dateityp-Einstellung](https://helpx.adobe.com/de/aem-forms/6-2/admin-help/enable-pdf-a-support.html)

>[!NOTE]
>
>Die Einstellungen für den Dateityp sind für die Fallback-Konverter wie Acrobat nicht für die Konvertierung von HTML in PDF, Microsoft PowerPoint, Microsoft Word und Microsoft Excel verfügbar.

## Erstellen oder Bearbeiten von Dateitypeinstellungen {#create-or-edit-file-type-settings}

Erstellen oder bearbeiten Sie eine Dateitypeinstellung, um anzugeben, wie das Programm die Konvertierung unterstützter Dateitypen handhabt. Unter Windows können Sie die Anwendungseinstellungen für jeden unterstützten Dateityp einrichten. Unter UNIX und Linux können Sie die Anwendungseinstellungen für HTML-to-PDF und OpenOffice einrichten.

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste]** > **[!UICONTROL PDF Generator]** > **[!UICONTROL Dateitypeinstellungen]**.
1. Klicken Sie auf „Neu“ oder auf den Namen einer Einstellung.
1. Geben Sie in das Feld „Dateinamenerweiterungen“ die durch Kommas getrennten Dateinamenerweiterungen für Dateitypen ein, die für diese Anwendung akzeptiert werden. Fügen Sie keinen Punkt vor oder ein Leerzeichen zwischen den Endungen ein. Der Standardwert lautet `bmp,gif,jpeg,jpg,tif,tiff,png`.
1. (Optional) Um die optische Zeichenerkennung (OCR) von Text in Grafiken oder Bildern zu aktivieren, wählen Sie „OCR verwenden“ aus und legen Sie die folgenden Optionen fest:

**Primäre OCR-Sprache:** Die Sprache, die die OCR-Engine zum Erkennen der Zeichen verwenden soll. Die Standardeinstellung ist Englisch (US).

**PDF-Ausgabestil:** Wählen Sie „Durchsuchbares Bild“ aus, um ein Bitmap-Bild der Seiten im Vordergrund und den gescannten Text auf einer unsichtbaren Ebene darunter zu haben. Die Darstellung der Seite wird nicht geändert, doch der Text wird auswählbar und lesbar. Wählen Sie „Formatierter Text und Grafiken“, um die Originalseite mithilfe von erkanntem Text, Schriftarten, Bildern und anderen grafischen Elementen zu rekonstruieren. Die Standardeinstellung ist „Durchsuchbares Bild (exakt)“.

**Bilder neu berechnen:** Verringert die Anzahl der Pixel in Farb-, Graustufen- und Schwarzweißbildern. Die Neuberechnung gescannter Bilder erfolgt nach Abschluss der OCR-Erkennung. Der Standardwert ist „Niedrigste (600 dpi)“. Diese Option ist nicht verfügbar, wenn der PDF-Ausgabestil auf „Durchsuchbares Bild (exakt)“ festgelegt ist.

1. Füllen Sie die erforderlichen Informationen in diesen Abschnitten aus:

   [Importieren und Exportieren von PDF Generator-Konfigurationsdateien](https://helpx.adobe.com/de/aem-forms/6-2/admin-help/importing-exporting-pdf-generator-configuration.html)

[Adobe PDF-Exporteinstellungen (nur Windows)](#adobe-pdf-export-settings-windows-only)

[„HTML in PDF“-Einstellungen](#html-to-pdf-settings)

[„Flashvideos in PDF“-Einstellungen](#flash-videos-to-pdf-settings)

[„XPS in PDF“-Einstellungen](#xps-to-pdf-settings)

[PDF-Optimierungseinstellungen](#pdf-optimizer-settings)

[Microsoft Excel-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings2.md#microsoft-excel-settings-windows-only)

[Microsoft PowerPoint-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings2.md#microsoft-powerpoint-settings-windows-only)

[Microsoft Project-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings2.md#microsoft-project-settings-windows-only)

[Microsoft Word-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings2.md#microsoft-word-settings-windows-only)

[Microsoft Visio-Einstellungen (nur Windows)](#visio)

[Microsoft Publisher-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings2.md#microsoft-publisher-settings-windows-only)

[AutoCAD-Einstellungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings2.md#autocad-settings-windows-only)

[OpenOffice-Einstellungen](/help/forms/using/admin-help/configuring-file-type-settings2.md#openoffice-settings)

[Einstellungen anderer Anwendungen (nur Windows)](/help/forms/using/admin-help/configuring-file-type-settings2.md#other-applications-settings-windows-only)

   Um zu einem anderen Abschnitt zu wechseln, klicken Sie auf dessen Link auf der Webseite oder auf eine der Schaltflächen **[!UICONTROL Weiter ]** oder **[!UICONTROL Zurück]**.

1. Klicken Sie nach dem Eingeben der Informationen in alle Abschnitte auf **[!UICONTROL Speichern]** oder **[!UICONTROL Speichern unter]** und geben Sie einen Namen für die Einstellung ein.

Die Unterstützung verschiedener Dateitypen kann angepasst werden. (Siehe [Hinzufügen der Unterstützung für weitere native Dateiformate](https://help.adobe.com/de_DE/AEMForms/6.1/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-7756.2.html) in [Programmieren mit AEM Forms).](https://www.adobe.com/go/learn_lc_programming_11_de)

## Ändern der Standardeinstellungen {#change-the-default-settings}

Sie können den Standardwert für die Adobe PDF-, Sicherheits- und Dateityp-Einstellungen ändern, die für neu erstellte Quellen gültig sind. Das Ändern der Standardwerte hat keine Auswirkungen auf die Einstellungen vorhandener Quellen.

1. Klicken Sie in der Administrationskonsole auf **[!UICONTROL Dienste > PDF Generator]**.
1. Klicken Sie auf der Seite **[!UICONTROL Adobe PDF-Einstellungen]**, **[!UICONTROL Dateitypeinstellungen]** oder **[!UICONTROL Sicherheitseinstellungen]** auf **[!UICONTROL Standardeinstellungen festlegen]**.
1. Wählen Sie die gewünschten Standardeinstellungen aus. Mindestens eine der folgenden Einstellungen ist auf der Seite „Standardeinstellungen festlegen“ verfügbar:

   **[!UICONTROL Adobe PDF Einstellung]**: Der ursprüngliche Standard ist „Standard“ (Acrobat 6).

   **[!UICONTROL Sicherheitseinstellungen]**: Der ursprüngliche Standard ist „Ohne Sicherheit“ (Acrobat 5).

   **[!UICONTROL Dateitypeinstellungen]**: Der ursprüngliche Standard ist „Standard“.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Löschen einer Dateitypeinstellung {#delete-a-file-type-setting}

Sie können eine nicht mehr verwendete Dateitypeinstellung löschen.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Dienste > PDF Generator > Dateitypeinstellungen]**.
1. Aktivieren Sie das Kontrollkästchen neben der zu löschenden Einstellung. Sie können mehrere Quellen auswählen. Einstellungen ohne Kontrollkästchen werden in PDF Generator immer berücksichtigt und können nicht gelöscht werden.
1. Klicken Sie auf der Seite „Löschbestätigung“ auf **[!UICONTROL Löschen]** und dann nochmals auf **[!UICONTROL Löschen]**.

## „Bild in PDF“-Einstellungen {#image-to-pdf-settings}

Die folgenden Optionen bestimmen, wie Bilddateien in PDF konvertiert werden. Anweisungen zum Zugriff auf diese Einstellungen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Dateinamenerweiterungen:** Eine durch Kommas getrennte Liste von Dateinamenerweiterungen, die konvertiert werden können.

**Ersatzkonverter versuchen:** PDF Generator kann entweder Java™ oder Acrobat verwenden, um Bilddateien in PDF-Dateien zu konvertieren. Wenn diese Option aktiviert ist und eine Konvertierung fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator die Konvertierung mithilfe der alternativen Methode. Wenn die alternative Methode fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

>[!NOTE]
>
>JPEG 2000-Dateien können nur mit Acrobat konvertiert werden.

**OCR verwenden:** Gibt an, ob die optische Zeichenerkennung (Optical Character Recognition, OCR) auf die PDF-Datei angewendet werden soll. Mit OCR-Software können Sie den Text in einer PDF-Datei durchsuchen, korrigieren und kopieren.

***Hinweis **: Die OCR PDF-Funktion (durchsuchbare PDF) wird nur unter Microsoft Windows unterstützt.*

**Primäre OCR-Sprache:** Die von der OCR-Engine zum Erkennen der Zeichen zu verwendende Sprache.

**Stil der PDF-Ausgabe:** Bestimmt den Typ des zu erstellenden PDF. Alle Formate wenden OCR und Schriftart- und Seitenerkennung auf die Bilder im Text an und konvertieren sie in normalen Text.

**Durchsuchbares Bild:** Stellt sicher, dass der Text durchsuchbar und auswählbar ist. Mit dieser Option wird das Originalbild beibehalten und ggf. geradegerückt, und es wird eine unsichtbare Textebene über das Bild platziert. Mit der Option „Bilder neu berechnen“ wird bestimmt, ob und in welchem Umfang das Bild neu berechnet wird.

**Durchsuchbares Bild (exakt):** Stellt sicher, dass der Text durchsuchbar und auswählbar ist. Mit dieser Option wird das Originalbild beibehalten und eine unsichtbare Textebene darüber platziert. Empfohlen für Fälle, in denen eine maximale Übereinstimmung mit dem Originalbild erforderlich ist.

**ClearScan**: Synthetisiert eine neue Type-3-Schriftart, die dem Original sehr nahe kommt, und behält den Seitenhintergrund bei, indem eine Kopie mit niedriger Auflösung verwendet wird.

**Bilder neu berechnen**: Verringert die Anzahl der Pixel in Farb-, Graustufen- und Schwarzweißbildern nach Abschluss der optischen Zeichenerkennung (OCR). Wählen Sie den Grad des Neuberechnens, der angewendet werden soll. Optionen mit höheren Nummern führen zu weniger Neuberechnung, wodurch PDFs mit höherer Auflösung generiert werden.

## Adobe PDF-Exporteinstellungen (nur Windows) {#adobe-pdf-export-settings-windows-only}

Die Einstellung „Dateityp exportieren“ im Abschnitt mit den Exporteinstellungen für Adobe PDF wird für die Konvertierung einer PDF-Datei in ein anderes Format verwendet. Die Standardeinstellung ist HTML 4.01 mit Cascading Style Sheets (CSS) 1.0(*.htm, *.html).

Anweisungen zum Zugriff auf diese Einstellung finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](configuring-file-type-settings.md#create-or-edit-file-type-settings).

## „HTML in PDF“-Einstellungen {#html-to-pdf-settings}

Die folgenden Optionen bestimmen, wie HTML-Dateien in PDF konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Ersatzkonverter versuchen**: PDF Generator kann entweder Java™ oder Acrobat verwenden, um HTML-Dateien in PDF zu konvertieren. Wenn diese Option aktiviert ist und eine Konvertierung fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator die Konvertierung mithilfe der alternativen Methode. Wenn die alternative Methode fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**Standardcodierung**: Legt die Eingabecodierung des Dateitexts über ein Menü mit Betriebssystemen und Alphabeten fest. Verwendet die Auswahl, die in der Option „Standardkodierung“ angezeigt wird, nur dann an, wenn die HTML-Quelldatei keinen Kodierungstyp angibt.

**Vom System ausgewählte Codierung**: Ignoriert jegliche Codierung, die in der HTML-Quelldatei angegeben ist, und verwendet die in der Option „Standardcodierung“ angezeigte Auswahl.

### Spider-Einstellungen {#spidering-settings}

Beim *Spidern* werden Web-Seiten auf Links zu anderen Web-Seiten untersucht. Wird ein Link zu einer anderen Web-Seite gefunden, wird die Zielseite abgerufen und in das generierte PDF-Dokument eingefügt. Aktivieren Sie diese Optionen, um die Anzahl der Ebenen festzulegen, die abgerufen und in PDF konvertiert werden sollen:

**Nur x Niveaus abrufen**: Durchsucht und konvertiert Seiten bis zu einer Tiefe der angegebenen Niveaus der Basisseiten-URL. Beim Wert 1 wird nur der angegebene URL konvertiert.

**Gesamte Site abrufen**: Konvertiert die gesamte Site ausgehend von der angegebenen URL.

**Auf demselben Pfad bleiben**: Alle Links, die auf Seiten verweisen, die nicht auf demselben relativen Pfad wie die Basis-URL liegen, werden beim Durchsuchen nicht konvertiert.

**Auf demselben Server bleiben**: Alle Links, die auf Seiten auf anderen Servern verweisen, werden beim Durchsuchen nicht konvertiert. Nur Links, die auf denselben Server verweisen wie die angegebene URL, werden konvertiert.

### Seitenkonvertierungseinstellungen {#page-conversion-settings}

Aktivieren Sie diese Optionen, um festzulegen, wie die HTML-Seiten konvertiert werden. Je nach Seitengröße werden die Werte für Breite, Höhe und Rand entsprechend angepasst.

**Seitengröße**: Wählen Sie sie benutzerdefiniert und geben Sie die Breite und Höhe an, oder nehmen Sie die vordefinierten Abmessungen.

**Orientierung**: Wählen Sie entweder Hoch- oder Querformat für das konvertierte PDF-Dokument.

**Ränder**: Legt die Ränder (oben, unten, links und rechts) im erzeugten PDF-Dokument fest.

**Lesezeichen zu PDF hinzufügen**: Fügt Lesezeichen zum PDF-Dokument hinzu.

**PDF mit Tags aktivieren**: Bettet Tags in das PDF-Dokument ein.

**Einstellungen für Ansicht beim Öffnen festlegen**: Ermöglicht die Konfiguration von Dokumentoptionen, Fensteroptionen und Benutzeroberflächenoptionen. Diese Einstellungen bestimmen, wie der Inhalt anfänglich angezeigt wird.

### Dokumentoptionen {#document-options}

Aktivieren Sie diese Optionen, um festzulegen, wie Inhalte angezeigt werden, wie Seiten im PDF-Dokument angezeigt werden und wie der Vergrößerungsgrad festgelegt wird:

**Anzeigen**: Wählen Sie die Bereiche aus, die in Acrobat geöffnet werden sollen, wenn das PDF-Dokument geöffnet wird.

**Seiten-Layout**: Wählen Sie die Art des Seiten-Layouts für das PDF-Dokument.

**Vergrößerung**: Wählen Sie die voreingestellte Vergrößerung für die Ansicht beim Öffnen des PDF-Dokuments oder wählen Sie einen benutzerdefinierten Wert. Das Übernehmen der Standardeinstellung bedeutet, dass die Standardvergrößerung von Acrobat verwendet werden soll.

**Auf folgender Seite öffnen**: Geben Sie die Nummer der Seite an, auf der das PDF-Dokument geöffnet werden soll.

### Fensteroptionen {#window-options}

Aktivieren Sie diese Optionen, um die Fenstergröße und -anzeige festzulegen.

**Größe des Fensters auf Anfangsseite ändern**: Passt die Größe des Acrobat-Fensters an die Anfangsseite an.

**Fenster auf Bildschirm zentrieren**: Öffnet das Fenster in der Mitte des Bildschirms.

**Im Vollbildmodus öffnen**: Öffnet das Fenster im Vollbildmodus.

**Anzeigen**: Zeigt den Titel des Dokuments oder den Dateinamen im Fenster an.

### Optionen der Benutzeroberfläche {#user-interface-options}

Aktivieren Sie diese Optionen, um das Erscheinungsbild des Fensters festzulegen:

**Menüleiste ausblenden:** Blendet die Menüleiste im PDF-Dokument aus.

**Symbolleisten ausblenden:** Blendet die Symbolleisten im PDF-Dokument aus.

**Fenstersteuerelemente ausblenden:** Blendet die Fenstersteuerelemente im PDF-Dokument aus.

## „Flashvideos in PDF“-Einstellungen {#flash-videos-to-pdf-settings}

PDF Generator unterstützt die Funktion zum Senden von Videos für Adobe Flash (SWF- oder FLV-Datei) und zum Erstellen einer PDF-Datei mit eingebettetem Video für Adobe Flash. Für diese Konversion braucht Adobe Flash Player nicht auf dem Formular-Server installiert zu sein. Anweisungen zum Zugriff auf diese Option finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Dateinamenerweiterungen:** Durch Kommas getrennte Liste von Dateinamenerweiterungen, die konvertiert werden können.

## „XPS in PDF“-Einstellungen {#xps-to-pdf-settings}

XML Paper Specification (XPS) wird in Windows Printing Machine verwendet. Dies ist ein Microsoft-Format, das von jeder Microsoft Office-Anwendung erstellt werden kann. AEM Forms ermöglicht die Konvertierung von XPS-Dateien in PDF.

**Dateinamenerweiterungen:** Durch Kommas getrennte Liste aller XPS-Dateinamenerweiterungen, die konvertiert werden können. Derzeit ist nur ein Format verfügbar: .xps.

## PDF-Optimierungseinstellungen {#pdf-optimizer-settings}

PDF Generator unterstützt die Funktion zum Reduzieren der Größe von PDF-Dateien. Ob Sie alle diese Einstellungen oder nur einige wenige verwenden, hängt davon ab, wie Sie die Dateien verwenden möchten, sowie von den wesentlichen Eigenschaften, die eine Datei aufweisen muss. In den meisten Fällen sind die Standardeinstellungen für maximale Effizienz ausgelegt – es wird Speicherplatz eingespart, indem eingebettete Schriftarten entfernt, Bilder komprimiert und nicht mehr benötigte Elemente aus den Dateien entfernt werden.

>[!NOTE]
>
>Durch die Optimierung eines digital signierten Dokuments werden die digitalen Signaturen entfernt und ungültig.

Anweisungen zum Zugriff auf diese Einstellung finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**PDF-Zielversion:** Gibt die Acrobat-Version an, mit der die PDF-Datei kompatibel ist.

### Schriften {#fonts}

1. Wählen Sie **Schriftarten**.
1. Wählen Sie eine der folgenden Optionen aus:

   **Einbettung für Zeichenformate aufheben:** Hebt die Einbettung für alle Schriftarten auf.

   **Einbettung für Zeichenformate nicht aufheben** Hebt die Einbettung für keine Schriftart auf.

   **Einbettung einiger Schriftarten aufheben:** Hebt die Einbettung nur für bestimmte Schriftarten auf. Führen Sie die folgenden Schritte aus, um die Schriftarten anzugeben, deren Einbettung Sie aufheben möchten:

   * Wählen Sie bei Bedarf einen anderen Schriftartenordner aus dem Dropdown-Menü **Schriftquelle**. In diesem Dropdown-Menü werden die Schriftartenordner aufgelistet, die in **Startseite > Einstellungen > Core-System > Core-Konfigurationen** angegeben wurden.
   * Wählen Sie eine oder mehrere Schriftarten aus der Liste **Verfügbare Schriftarten** und klicken Sie auf **Hinzufügen**. Diese Schriftarten werden der Liste **Einbettung für folgende Schriftarten aufheben** hinzugefügt.
   * Wenn Sie die Einbettung für einige Schriftarten aufheben möchten, die auf dem Formular-Server nicht vorhanden sind, geben Sie die Namen dieser Schriftarten in das Feld **Schriftarten für die Aufhebung der Einbettung hinzufügen** ein. Klicken Sie auf **Hinzufügen**.

   >[!NOTE]
   >
   >*Wenn Sie die Einbettung für einige Schriftarten aufheben möchten, von denen Untergruppen im Dokument eingebettet sind, setzen Sie das Symbol „+“ vor den Namen der Schriftart. Beispiel: „+Helvetica“.*

1. Wenn Sie lediglich die verwendeten Untergruppen der eingebetteten Schriftarten einbetten möchten, wählen Sie **Alle eingebetteten Schriftarten in Untergruppe zusammenfassen**.

   >[!NOTE]
   >
   >*Wenn Sie diese Option in Kombination mit **Einbettung für einige Schriftarten aufheben**verwenden, ist die Einbettung für die Schriftarten in der Liste **Schriftarten für die Aufhebung der Einbettung hinzufügen**weiterhin vollständig aufgehoben.*

   >[!NOTE]
   >
   >*Die Schrifteinbettung in Untergruppen ist eine Vorgehensweise für die Einbettung eines Teils einer Schriftart. Eine Schriftartuntergruppe enthält nur die im Dokument verwendeten Zeichen.*

### Transparenz {#transparency}

Wenn das PDF-Dokument Grafiken mit Transparenz enthält, können Sie die PDF-Optimierungseinstellungen verwenden, um die Transparenz und die Dateigröße zu reduzieren.

>[!NOTE]
>
>Wenn Acrobat 4.0 und höher als Ziel-PDF-Version ausgewählt ist, werden alle transparenten Objekte reduziert. Bei anderen Ziel-PDF-Versionen wird Transparenz unterstützt und Sie können die Transparenzeinstellungen konfigurieren.

Wählen Sie **Transparenz**, um die Transparenzeinstellungen beim Optimieren von PDF-Dokumenten zu konfigurieren.

**Transparenzstufe** Legt die Menge an Vektorinformationen fest, die beibehalten wird. Bei höheren Einstellungen werden mehr Vektorobjekte beibehalten, bei niedrigeren Einstellungen werden mehr Vektorobjekte gerastert. Bei mittleren Einstellungen werden einfache Bereiche in Vektorform beibehalten und komplexe Bereiche werden gerastert. Wählen Sie die niedrigste Einstellung aus, um alle Grafiken zu rastern.

>[!NOTE]
>
>Der Umfang der Rasterung hängt von der Komplexität der Seite und den Arten der überlappenden Objekte ab.

**Strichgrafiken und Text**: Auflösung, in der alle Objekte, einschließlich Bilder, Vektorgrafiken, Text und Verläufe, gerastert werden. Die unterstützten Werte sind 1 Pixel pro Zoll (ppi) bis 9600 ppi.

>[!NOTE]
>
>Die Auflösung von Strichgrafiken und Text sollte im Allgemeinen auf 600 bis 1200 ppi eingestellt werden, um eine hochwertige Rasterung zu gewährleisten, insbesondere bei Serifenschriften oder kleinen Schriftarten.

**Verlauf und Gitter**: Auflösung, auf die Verlauf und Gitter gerastert werden. Die unterstützten Werte sind 1 ppi bis 1200 ppi.

>[!NOTE]
>
>Die Auflösung für Verlauf und Gitter sollte im Allgemeinen auf 150 bis 300 ppi eingestellt werden, da sich die Qualität von Verläufen, Schlagschatten und weichen Kanten mit höheren Auflösungen nicht verbessert. Hingegen wird durch höhere Auflösungen die Druckzeit verlängert und die Datei unnötig vergrößert.

**Text in Pfade konvertieren**: Wandelt alle Textobjekte (Punkttext, Flächentext und Pfadtext) in Pfade um und ignoriert alle Textglyphen-Informationen auf Seiten mit Transparenz. Mit dieser Option wird sichergestellt, dass die Breite des Textes während der Reduzierung konsistent bleibt. Beachten Sie, dass die Aktivierung dieser Option dazu führt, dass kleine Schriften etwas dicker erscheinen, wenn sie in Acrobat angezeigt oder auf Desktop-Druckern mit niedriger Auflösung gedruckt werden. Sie hat keinen Einfluss auf die Textqualität, wenn die Datei auf Druckern mit hoher Auflösung oder Belichtern gedruckt wird.

**Konturen in Pfade konvertieren** Wandelt auf Seiten mit Transparenz alle Konturen in einfache ausgefüllte Pfade um. Mit dieser Option wird sichergestellt, dass die Breite von Konturen beim Reduzieren unverändert bleibt. Beachten Sie, dass dünne Konturen geringfügig dicker angezeigt werden und die Leistung des Reduzierens beeinträchtigen werden könnte, wenn Sie diese Option aktivieren.

**Komplexe Bereiche beschneiden**: Stellt sicher, dass die Grenzen zwischen Vektorgrafiken und gerasterten Grafiken entlang von Objektpfaden verlaufen. Mit dieser Option werden sichtbare Übergänge bei Grafiken vermieden, wenn ein Teil eines og

<!--
NOTE to WRITER: Unfinished sentence above.
-->

>[!NOTE]
>
>Einige Druckertreiber verarbeiten Raster- und Vektorgrafiken unterschiedlich, was manchmal zu Farbabweichungen führt. Sie können dieses Problem minimieren, indem Sie einige für den jeweiligen Druckertreiber spezifische Farbmanagement-Einstellungen deaktivieren. Diese Einstellungen variieren je nach Drucker. Weitere Informationen finden Sie in der Dokumentation zu Ihrem Drucker.

Überdruck beibehalten: Lässt die Farbe von transparentem Bildmaterial mit der Hintergrundfarbe verschmelzen, um einen Überdruckeffekt zu erzielen.

Die folgende Tabelle zeigt gängige Druckertypen und ihre Auflösung in dpi, ihre Standard-Rasterweite in Zeilen pro Zoll (lpi) und eine Resampling-Auflösung für Bilder in Pixel pro Zoll (ppi). Wenn Sie beispielsweise auf einem 600-dpi-Laserdrucker drucken, geben Sie 170 für die Auflösung ein, mit der Bilder neu berechnet werden sollen.

**Bilder**: Wählen Sie diese Option, um Komprimierungs- und Neuberechnungsoptionen für Farb-, Graustufen- und Schwarzweißbilder festzulegen. Sie können mit diesen Optionen experimentieren, um einen guten Kompromiss zwischen Dateigröße und Bildqualität zu finden. Die Auflösungseinstellung für Farb- und Graustufenbilder sollte dem 1,5- bis 2-fachen der Rasterweitenlinierung entsprechen, mit der die Datei gedruckt wird. Die Auflösung für Schwarzweißbilder sollte mit der des Ausgabegeräts übereinstimmen. Das Speichern eines Schwarzweißbilds mit einer Auflösung von mehr als 1500 dpi erhöht allerdings die Dateigröße, ohne die Bildqualität spürbar zu verbessern. Bilder, die vergrößert werden, wie beispielsweise Karten, erfordern möglicherweise höhere Auflösungen.

>[!NOTE]
>
>Das Neuberechnen von Schwarzweißbildern kann zu unerwarteten Anzeigeergebnissen führen, z. B. zu keiner Bildanzeige. In diesem Fall deaktivieren Sie die Neuberechnung und konvertieren die Datei erneut. Dieses Problem tritt am wahrscheinlichsten beim Subsampling und am wenigsten bei der bikubischen Neuberechnung auf.

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

#### Verwerfen von Objekten {#discard-objects}

* Wählen Sie **Objekte verwerfen**, um die Objekte anzugeben, die aus der PDF-Datei entfernt werden sollen, und um gekrümmte Linien in CAD-Zeichnungen zu optimieren.
* **Alle Sende-, Import- und Zurücksetzungsaktionen für Formulare verwerfen**: Deaktiviert alle Aktionen im Zusammenhang mit dem Senden oder Importieren von Formulardaten und setzt Formularfelder zurück. Mit dieser Option werden Formularobjekte, mit denen Aktionen verknüpft sind, beibehalten.
* **Alle JavaScript-Aktionen verwerfen**: Entfernt alle Aktionen aus der PDF-Datei, die JavaScript verwenden.
* **Eingebettete Seitenminiaturansichten verwerfen**: Entfernt eingebettete Miniaturansichten von Seiten. Diese Option ist für große Dokumente nützlich, bei denen es lange dauern kann, bis Seitenminiaturansichten gezeichnet worden sind, nachdem Sie auf die Schaltfläche „Seiten“ geklickt haben.
* **Geglättete Linien in Kurven konvertieren**: Verringert die Anzahl von Steuerpunkten zum Erstellen von Kurven in CAD-Zeichnungen, was zu kleineren PDF-Dateien und einer schnelleren Bildschirmwiedergabe führt.
* **Eingebettete Druckeinstellungen verwerfen**: Entfernt eingebettete Druckeinstellungen aus dem Dokument, z. B. Seitenskalierung und Duplexmodus.
* **Lesezeichen verwerfen**: Entfernt alle Lesezeichen aus dem Dokument.
* **Formularfelder reduzieren**: Macht Formularfelder unbrauchbar, ohne ihr Aussehen zu ändern. Formulardaten werden mit der Seite zusammengeführt und werden zu Seiteninhalt.
* **Alle alternativen Bilder verwerfen**: Entfernt alle Versionen eines Bildes mit Ausnahme der Version, die für die Anzeige auf dem Bildschirm vorgesehen ist. Einige PDF-Dateien enthalten mehrere Versionen desselben Bildes für verschiedene Zwecke, z. B. niedrige Bildschirmauflösung und Druck mit hoher Auflösung.
* **Dokument-Tags verwerfen**: Entfernt Tags aus dem Dokument, wodurch auch die Barrierefreiheits- und Reflow-Funktionen für den Text entfernt werden.
* **Bildfragmente erkennen und zusammenführen**: Sucht nach Bildern oder Masken, die in kleine Ausschnitte fragmentiert sind, um diese Ausschnitte in einem einzigen Bild oder einer einzigen Maske zusammenzuführen.
* **Eingebetteten Suchindex verwerfen**: Entfernt eingebettete Suchindizes, wodurch die Dateigröße verringert wird.

#### Benutzerdaten verwerfen {#discard-user-data}

Wählen Sie **Benutzerdaten verwerfen** aus, um alle persönlichen Informationen zu entfernen, die Sie nicht an andere Benutzende weitergeben oder für diese freigeben möchten.

* **Alle Kommentare, Formulare und Multimedia-Dateien verwerfen**: Entfernt alle Kommentare, Formulare, Formularfelder und Multimedia-Dateien aus der PDF-Datei.
* **Alle Objektdaten verwerfen**: Entfernt alle Objekte aus der PDF-Datei.
* **Externe Querverweise verwerfen**: Entfernt Links zu anderen Dokumenten. Links, die auf andere Stellen innerhalb der PDF-Datei verweisen, werden nicht entfernt.
* **Ausgeblendete Ebeneninhalte verwerfen und sichtbare Ebenen reduzieren**: Verringert die Dateigröße. Das optimierte Dokument sieht wie die ursprüngliche PDF-Datei aus, enthält jedoch keine Ebeneninformationen.
* **Dokumentinformationen und Metadaten verwerfen**: Entfernt Informationen im Dokumentinformationswörterbuch und alle Metadaten-Streams. (Verwenden Sie den Befehl „Speichern unter“, um Metadaten-Datenströme in einer Kopie der PDF-Datei wiederherzustellen.)
* **Dateianlagen verwerfen**: Entfernt alle Dateianlagen, einschließlich der Anlagen, die als Kommentare der PDF-Datei hinzugefügt wurden. (PDF Optimizer optimiert keine angehängten Dateien.)
* **Private Daten anderer Anwendungen verwerfen**: Entfernt Informationen aus einem PDF-Dokument, die nur für die Anwendung hilfreich sind, mit der das Dokument erstellt wurde. Diese Einstellung wirkt sich nicht auf die Funktionalität des PDF-Dokuments aus, verringert jedoch die Dateigröße.

### Bereinigen {#clean-up}

Wählen Sie **Bereinigung**, um nicht erforderliche Elemente aus dem Dokument zu entfernen.
Zu diesen Elementen gehören veraltete oder für den vorgesehenen Zweck des Dokuments unnötige Elemente. Wenn Sie bestimmte Elemente entfernen, kann dies schwerwiegende Auswirkungen auf die Funktionalität der PDF-Datei haben. Standardmäßig werden nur Elemente, die keinen Einfluss auf die Funktionalität haben, ausgewählt. Wenn Sie nicht sicher sind, welche Auswirkungen das Entfernen anderer Optionen hat, verwenden Sie die Standardauswahl.

**Komprimierung**

Wählen Sie eine der folgenden Flate-Komprimierungsoptionen aus dem Dropdown-Menü:

* Gesamte Datei komprimieren
* Dokumentstruktur komprimieren
* Komprimierung entfernen
* Komprimierung unverändert lassen

**Nicht kodierte Datenströme mit Flate kodieren**: Wendet Flate-Komprimierung auf alle nicht kodierten Datenströme an.

**Ungültige Lesezeichen verwerfen**: Entfernt alle Lesezeichen, die auf gelöschte Seiten im Dokument verweisen.

**Nicht referenzierte benannte Ziele verwerfen**: Entfernt benannte Ziele, auf die nicht intern innerhalb des PDF-Dokuments verwiesen wird. Diese Option überprüft keine Verknüpfungen von anderen PDF-Dateien oder Websites.

**PDF für schnelle Webanzeige optimieren**: Strukturiert ein PDF-Dokument für das seitenweise Herunterladen (Byte-Serving) von Webservern neu.

**In Datenströmen, die LZW-Kodierung verwenden, stattdessen Flate verwenden:**: Wendet Flate-Komprimierung auf alle Inhalts-Streams und Bilder an, die LZW-Kodierung verwenden.

**Ungültige Links verwerfen**: Entfernt Links, die zu ungültigen Zielen springen.

**Seiteninhalt optimieren**: Konvertiert alle Zeilenendezeichen in Leerzeichen, wodurch die Flate-Komprimierung verbessert wird.

## Microsoft Excel-Einstellungen (nur Windows) {#microsoft-excel-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Excel-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](#create-or-edit-file-type-settings).

**OpenOffice als Ersatzkonverter versuchen**: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft Excel fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mit OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**Dateinamenerweiterungen**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `xls,xlsx`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**PDF/A-1a-kompatible Datei erstellen**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005(RGB)“.

**Lesezeichen zu Adobe PDF hinzufügen**: Konvertiert Namen von Excel-Arbeitsblättern in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**Arbeitsblatt auf einzelne Seite anpassen**: Verkleinert die Schriftgröße, damit das Arbeitsblatt auf eine einzelne Seite passt.

**Gesamte Arbeitsmappe konvertieren**: Konvertiert alle Arbeitsmappen in der Excel-Datei. Falls diese Option nicht ausgewählt ist, wird nur die aktuelle Seite konvertiert.

**Makros automatisch ausführen**: Führt vor dem Konvertieren des Dokuments alle Makros im Excel-Dokument aus (z. B. als ein Makro, das die aktuelle Uhrzeit einfügt).

**Dokumentinformation konvertieren**: Fügt PDF-Dokumenteigenschaften auf der Basis der Dokumentinformationen in der Quelldatei hinzu. Dazu gehören Informationen wie der Dokumenttitel, Autor, Betreff und Schlüsselwörter.

**Verknüpfungen zu Adobe PDF hinzufügen:** Konvertiert Hyperlinks in der Quelldatei in Hyperlinks im PDF-Dokument.

**Quelldatei an Adobe PDF anfügen:**: Wenn diese Option ausgewählt ist, wird die ursprüngliche Excel-Tabelle als Anlage innerhalb des erstellten PDF-Dokuments eingefügt.

**Eingabehilfe und Umfließen mit Adobe PDF mit Tags aktivieren**: Bettet Tags in das PDF-Dokument ein, um Eingabehilfen und Umfließen zu aktivieren.

**Liste der zu ladenden Excel-Add-Ins**: Standardmäßig werden beim Konvertieren einer Excel-Datei in das PDF-Format aus Sicherheitsgründen keine Excel-Add-Ins ausgeführt. Wenn Sie zulassen möchten, dass bestimmte Excel-Add-Ins während der Konvertierung ausgeführt werden, stellen Sie eine durch Kommas getrennte Liste mit den Namen der Add-Ins bereit.

**Liste der zu konvertierenden Arbeitsmappen**: Wenn dieses Feld leer ist, sind alle Arbeitsmappen in der Excel-Tabelle in dem erstellten PDF-Dokument enthalten. Um eine Teilmenge der Arbeitsblätter selektiv zu konvertieren, geben Sie eine kommagetrennte Liste von Arbeitsblattnamen an.

## Microsoft PowerPoint-Einstellungen (nur Windows) {#microsoft-powerpoint-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft PowerPoint-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](/help/forms/using/admin-help/configuring-file-type-settings2.md#create-or-edit-file-type-settings).

**[!UICONTROL OpenOffice als Ersatzkonverter versuchen]**: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft PowerPoint fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mit OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Die Standardeinstellung ist ppt,pptx. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Schlüsselwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen:]** Konvertiert PowerPoint-Arbeitsblattnamen in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Quelldatei an Adobe PDF anfügen]**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu. Standardmäßig ist diese Option deaktiviert.

**[!UICONTROL Eingabehilfe und Umfließen mit Adobe PDF mit Tags aktivieren]**: Bettet Tags in die PDF-Datei ein. Standardmäßig ist diese Option deaktiviert.

**[!UICONTROL Multimedia in PDF-Multimedia konvertieren]**: Konvertiert, falls möglich, Multimedia in Multimedia-PDF. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Vortragsnotizen konvertieren]**: Konvertiert Vortragsnotizen in PDF.

**[!UICONTROL Makros automatisch ausführen]**: Führt vor dem Konvertieren des Dokuments alle Makros im PowerPoint-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

**[!UICONTROL PDF-Layout basierend auf PowerPoint-Druckereinstellungen]**: Verwendet PowerPoint-Druckereinstellungen für das Layout des PDF-Dokuments.

**[!UICONTROL Links zu Adobe PDF hinzufügen]**: Behält vorhandene Links bei, wenn die Datei konvertiert wird. Die Darstellung von Links bleibt grundsätzlich unverändert. Links können nur erstellt werden, wenn die Option „Barrierefreiheit aktivieren“ ebenfalls aktiviert ist. Standardmäßig ist diese Option deaktiviert.

**[!UICONTROL Folienübergänge in Adobe PDF speichern]**: Konvertiert Folienübergänge. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Animationen in Adobe PDF speichern]**: Speichert konvertierte Animationen in der PDF-Datei.

**[!UICONTROL Ausgeblendete Folien in PDF-Seiten konvertieren]**: Konvertiert ausgeblendete Folien.

**[!UICONTROL PDF/A-1a-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005 RGB“. Einige PowerPoint-Funktionen werden bei der Erstellung einer PDF-Datei nicht konvertiert. Wenn eine PowerPoint-Transition in Acrobat keine äquivalente Transition aufweist, wird eine ähnliche Transition ersetzt. Wenn sich mehrere Animationseffekte in derselben Folie befinden, wird ein einzelner Effekt verwendet. Seitenübergänge und Aufzählungszeichen werden konvertiert.

## Microsoft Project-Einstellungen (nur Windows) {#microsoft-project-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft-Projektdateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](#create-or-edit-file-type-settings).

1. **[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für dieses Programm akzeptiert werden. Der Standardwert lautet `mpp`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

1. **[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Schlüsselwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.
1. **[!UICONTROL Quelldatei an Adobe PDF anfügen]**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu.
1. **[!UICONTROL PDF/A-1a-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005(RGB)“.
1. **[!UICONTROL Makros automatisch ausführen]**: Führt vor dem Konvertieren des Dokuments alle Makros im Microsoft Project-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

## Microsoft Word-Einstellungen (nur Windows) {#microsoft-word-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Word-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](#create-or-edit-file-type-settings).

**[!UICONTROL OpenOffice als Ersatzkonverter versuchen]**: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft Word fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mit OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `doc,docx,rtf,txt`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Schlüsselwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen]**: Konvertiert Überschriften in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Quelldatei an Adobe PDF anfügen]**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**[!UICONTROL Querverweise und Inhaltsverzeichnisse in Links konvertieren]**: Konvertiert alle Querverweise und Inhaltsverzeichniseinträge in Links. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Eingabehilfe und Umfließen mit Adobe PDF mit Tags aktivieren]**: Bettet Tags in die PDF-Datei ein. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL PDF/A-1a-kompatible Datei erstellen]**: Erzwingt, falls ausgewählt, die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005(RGB)“.

**[!UICONTROL Makros automatisch ausführen]**: Führt vor dem Konvertieren des Dokuments alle Makros im Word-Dokument aus (z. B. als ein Makro, das die aktuelle Uhrzeit einfügt).

**[!UICONTROL Dokumentmarkierung in Adobe PDF beibehalten]**: Konvertiert das Markup im Word-Dokument in Anmerkungen in der PDF-Datei.

**[!UICONTROL Verknüpfungen zu Adobe PDF hinzufügen:]** Konvertiert Hyperlinks in der Quelldatei in Hyperlinks im PDF-Dokument.

**[!UICONTROL Fußnoten- und Endnoten-Links konvertieren]**: Erstellt Links aus den Zitaten der Fußnoten und Endnoten zu Anmerkungen im PDF-Dokument.

**[!UICONTROL Angezeigte Kommentare in Anmerkungen in Adobe PDF konvertieren]**: Konvertiert Kommentare im Word-Dokument zu Textanmerkungen im PDF-Dokument.

**[!UICONTROL Erweitertes Tagging aktivieren]**: Fügt erweiterte Tags für verbesserte Barrierefreiheit hinzu.

**[!UICONTROL Alle Stile in Lesezeichen konvertieren]**: Konvertiert alle Stile im Word-Dokument in Lesezeichen im PDF-Dokument.

**[!UICONTROL Stile mit Ebenen With Levels]** Gibt an, welche Stile im Word-Dokument zu Lesezeichen in der PDF-Datei konvertiert werden. Gibt auch die Ebene der Lesezeichen an. Um diese Funktion zu nutzen, deaktivieren Sie die Option **[!UICONTROL Alle Stile in Lesezeichen konvertieren]** und geben Sie die Namen der Stile im folgenden Format an:

styleName1=level1[,styleName2=level2...]

Wenn ein Microsoft Word-Formatvorlagenname ein Komma (,) oder ein Gleichheitszeichen (=) enthält, stellen Sie den Sonderzeichen das Escape-Zeichen („\“) voran. So müssten Sie z. B. für einen Stil mit dem Namen „Überschrift, 1“ den Wert „Überschrift\, 1“ angeben.

## Microsoft Visio-Einstellungen (nur Windows) {#visio}

**Dokumentinformationen konvertieren**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Stichwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert. Diese Option ist standardmäßig aktiviert.

**Verknüpfungen zu Adobe PDF hinzufügen**: Behält alle Links bei. Standardmäßig ist diese Option aktiviert.

**Lesezeichen zu Adobe PDF hinzufügen**: Konvertiert Überschriften in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**Quelldatei an Adobe PDF anfügen**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**Ebenen in Adobe PDF immer reduzieren**: Reduziert alle Visio-Ebenen.

**Alle Seiten konvertieren**: Konvertiert alle Seiten der Visio-Datei.

**Ebenenbedienfeld öffnen, wenn es in Adobe Acrobat angezeigt wird**: Öffnet, falls Visio-Ebenen nicht reduziert werden, ein Fenster, in dem Sie die Ebenen angeben können, die in der PDF-Dateien beibehalten werden, wenn sie mithilfe von Acrobat geöffnet werden. Standardmäßig ist diese Option aktiviert.

**PDF/A-1b-kompatible Datei erstellen**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005 (RGB)“.

**Kommentare in Adobe PDF-Kommentare konvertieren**: Konvertiert Visio-Notizen in PDF-Kommentare.

## Microsoft Publisher-Einstellungen (nur Windows) {#microsoft-publisher-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Publisher-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](#create-or-edit-file-type-settings).

**[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `pub`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

## AutoCAD-Einstellungen (nur Windows) {#autocad-settings-windows-only}

Diese Optionen bestimmen, wie AutoCAD-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](/help/forms/using/admin-help/configuring-file-type-settings2.md#create-or-edit-file-type-settings).

**[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `dwg`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Schlüsselwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen]**: Konvertiert Überschriften in Lesezeichen.

**[!UICONTROL Ebenen in Adobe PDF immer reduzieren]**: Reduziert alle AutoCAD-Ebenen.

**[!UICONTROL Ebenenfenster bei Anzeige in Adobe Acrobat öffnen]**: Zeigt die Ebenenstruktur an, wenn das PDF in Acrobat geöffnet wird.

**[!UICONTROL PDF/E-1-kompatible Datei erstellen]**: Erstellt eine Datei, die PDF/E-1-kompatibel ist. PDF/E ist ein ISO-Standard für den Austausch von ingenieurwissenschaftlichen und technischen Dokumentationen. Weitere Informationen zu PDF/E-1 finden Sie in [Adobe und Branchenstandards](https://www.adobe.com/de/enterprise/standards/index.html).

**[!UICONTROL Alle Layouts konvertieren]**: Nimmt alle Layouts in die PDF auf.

**[!UICONTROL Modellbereich in 3D konvertieren:]** Wenn diese Option aktiviert ist, wird das Modellbereich-Layout in eine 3D-Anmerkung in der PDF-Datei konvertiert.

**[!UICONTROL Verknüpfungen zu Adobe PDF hinzufügen]**: Behält alle Links bei, wenn ausgewählt.

**[!UICONTROL Quelldatei an Adobe PDF anfügen]**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**[!UICONTROL PDF/A-1b-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b“.

**[!UICONTROL Alle Ebenen konvertieren]**: Standardmäßig konvertiert PDF Generator nicht alle in AutoCAD-Dateien enthaltenen Ebenen, sondern nur die Standardebene der Datei in PDF. Wählen Sie diese Option, um alle Ebenen der Datei zu konvertieren.

**[!UICONTROL Skalierungsinformationen einbetten]**: Behält Skalierungsinformationen von Zeichnungen bei.

**[!UICONTROL Aktuelles Layout konvertieren]**: Nimmt nur das aktuelle Layout in die PDF auf.

**[!UICONTROL Liste der zu konvertierenden AutoCAD-Layouts]**: Eine AutoCAD-Zeichnung kann über mehrere Layouts verfügen. Wenn dieses Feld leer ist, sind alle Layouts in der AutoCAD-Zeichnung im generierten PDF-Dokument enthalten. Um eine Teilmenge der Layouts selektiv zu konvertieren, geben Sie eine kommagetrennte Liste mit Layout-Namen an.

## OpenOffice-Einstellungen {#openoffice-settings}

Diese Optionen bestimmen, wie OpenOffice-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](/help/forms/using/admin-help/configuring-file-type-settings2.md#create-or-edit-file-type-settings).

**PDFMaker als Ersatzkonvertierer versuchen**: Wenn diese Option aktiviert ist und eine Konvertierung mit OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von PDFMaker auszuführen. Wenn die Konvertierung mit PDFMaker fehlschlägt oder das angegebene Zeitlimit erreicht, wird ein Ausnahmefehler in die Protokolldatei aufgenommen.

**Dateinamenerweiterungen**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für diese Anwendung akzeptiert werden. Der Standardwert lautet `odt,odp,ods,odg,odf,sxw,sxi,sxd`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**Bereich:** Konvertieren Sie alle Seiten oder geben Sie bestimmte Seiten oder einen Seitenbereich an. Wenn kein Seitenbereich definiert ist, werden alle Seiten konvertiert. Um einen Seitenbereich zu exportieren, verwenden Sie das Format 3-6. Zum Exportieren einzelner Seiten verwenden Sie das Format 7;9;11. Sie können eine Kombination aus Seitenbereichen und einzelnen Seiten exportieren, indem Sie ein Format wie 3-6;8;10;12 verwenden.

**Seitenausrichtung**: Wählen Sie nur bei reinen Textdateien entweder Hoch- oder Querformat für das konvertierte PDF-Dokument aus.

**Bilder**: Konfigurieren Sie, wie Bilder konvertiert werden sollen. EPS-Bilder mit eingebetteter Vorschau werden nur als Vorschau exportiert. EPS-Bilder ohne eingebettete Vorschau werden als leere Platzhalter exportiert. Bei der verlustfreien Komprimierung von Bildern bleiben alle Pixel erhalten. Bei der JPEG-Komprimierung von Bildern und einer hohen Qualitätsstufe bleiben fast alle Pixel erhalten. Bei einer niedrigen Qualitätsstufe gehen einige Pixel verloren und Artefakte werden hinzugefügt. Die Dateigröße wird allerdings verringert.

**Allgemein**: Aktivieren Sie die Optionen, um eine PDF-Datei mit Tags zu konvertieren oder Writer- und FormCalc-Dokumentnotizen, Impress-Folienübergangseffekte oder leere Seiten in die PDF-Datei zu exportieren. Beim Export von Tags kann die Dateigröße drastisch zunehmen. Einige Tags, die exportiert werden, sind Inhaltsverzeichnisse, Hyperlinks und Steuerelemente.

Sie können auch angeben, wie Formulare gesendet werden. Verfügbar sind die Optionen XML, FDF, PDF oder HTML. Diese Einstellung setzt die URL-Eigenschaft des Steuerelements außer Kraft, die Sie im Dokument festgelegt haben. Nur eine allgemeine Einstellung kann für das PDF-Dokument ausgewählt werden:

* PDF (sendet das gesamte Dokument)
* FDF (sendet den Inhalt von Steuerelementen)
* HTML
* XML

**PDF mit Tags**: Aktiviert das Erstellen von PDF-Dateien mit Tags aus OpenOffice-Dokumenten. PDF-Dateien mit Tags enthalten Informationen über die Struktur der Dokumentinhalte. Dies kann beim Anzeigen des Dokuments auf Geräten mit verschiedenen Bildschirmen und beim Verwenden von Bildschirmlesehilfe-Software behilflich sein. PDF-Dateien mit Tags können auch Bildschirmlesehilfe-Software helfen, verschiedene nützliche Vorgänge mit dem PDF-Dokument auszuführen, z. B. lautes Vorlesen der Inhalte des PDF-Dokuments.

**Notizen exportieren**: Konvertiert die Notizen in OpenOffice-Dokumenten zu Anmerkungen im generierten PDF-Dokument.

**Übergangseffekte verwenden**: Konvertiert die Folienübergangseffekte in OpenOffice-Präsentationen in entsprechende PDF-Übergangseffekte.

**Formulare in Format senden**: Erstellt ein PDF-Formular, das vom Benutzenden des PDF-Dokuments ausgefüllt und gedruckt werden kann.

**Automatisch eingefügte leere Seiten exportieren**: Wenn diese Option aktiviert ist, sind alle automatisch eingefügten leeren Seiten im generierten PDF-Dokument enthalten. Dies ist nützlich, wenn Sie ein PDF-Dokument doppelseitig drucken möchten. Ein Buch kann beispielsweise so konfiguriert sein, dass die erste Seite eines Kapitels immer auf einer Seite mit ungerader Seitenzahl beginnt. Wenn das vorherige Kapitel auf einer Seite mit ungerader Seitenzahl endet, fügt OpenOffice eine leere Seite mit gerader Seitenzahl ein. Diese Option steuert, ob diese Seite mit gerader Seitenzahl in der generierten PDF-Datei enthalten ist.

## Andere Programmeinstellungen (nur Windows) {#other-applications-settings-windows-only}

Sie können die Einstellungen für andere Anwendungen nicht mithilfe der Administrationskonsole ändern. Sie zeigen die Dateinamenerweiterungen für die unterstützten Dateitypen an. Anweisungen zum Zugriff auf diese Einstellungen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](https://help.adobe.com/de_DE/AEMForms/6.1/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7e42.2.html).

* Corel WordPerfect: `wpd`
* Adobe PageMaker: `pmd, pm6, p65, pm`
* Adobe FrameMaker: `fm`
* Adobe Photoshop: `psd`

Die Unterstützung dieser Dateitypen muss ggf. angepasst werden. Weitere Informationen finden Sie unter „Hinzufügen von Unterstützung für zusätzliche native Dateiformate“ in [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_62).

Wenn Sie Hilfe bei der Konfiguration eines PDFG-Netzwerkdruckers benötigen, finden Sie weitere Informationen unter [Einrichten eines PDFG-Netzwerkdruckers (nur Windows)](/help/forms/using/admin-help/setting-pdfg-network-printer-windows.md).
