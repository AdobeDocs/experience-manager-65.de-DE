---
title: Konfigurieren von Dateitypeinstellungen
seo-title: Configuring file type settings
description: Erfahren Sie, wie Sie Dateitypeinstellungen konfigurieren.
seo-description: Learn how to configure file type settings.
uuid: d01f430b-9637-4a5f-b3a7-d5ef3e5ecbc5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: adbe8416-c8d7-4581-940b-df62eadf0e26
source-git-commit: e2a3470784beb04c2179958ac6cb98861acfaa71
workflow-type: tm+mt
source-wordcount: '6163'
ht-degree: 38%

---


# Konfigurieren von Dateitypeinstellungen {#configuring-file-type-settings}

In PDF Generator können Sie die Anwendungseinstellungen für unterstützte Dateitypen einrichten. Unter Windows können Sie die Anwendungseinstellungen für jeden unterstützten Dateityp einrichten. Unter UNIX und Linux können Sie die Anwendungseinstellungen für HTML-to-PDF und OpenOffice einrichten.

Auf der Seite &quot;Dateitypeinstellungen&quot;können Sie die folgenden Aufgaben ausführen:

* [Erstellen oder Bearbeiten einer Dateitypeinstellung](#create-or-edit-file-type-settings)
* Geben Sie an, welche Dateitypeinstellungen standardmäßig verwendet werden sollen (siehe [PDF Generator-Konfigurationsdateien importieren und exportieren](https://helpx.adobe.com/de/aem-forms/6-2/admin-help/importing-exporting-pdf-generator-configuration.html))
* [Standardeinstellungen ändern](/help/forms/using/admin-help/configuring-file-type-settings2.md#change-the-default-settings)
* [Aktivieren der PDF/A-Unterstützung](https://helpx.adobe.com/de/aem-forms/6-2/admin-help/enable-pdf-a-support.html)
* [Löschen einer Dateityp-Einstellung](https://helpx.adobe.com/de/aem-forms/6-2/admin-help/enable-pdf-a-support.html)

>[!NOTE]
>
>Die Dateitypeinstellungen sind nicht für die Fallback-Konvertierer wie Acrobat zum HTML auf PDF-Konvertierung, Microsoft PowerPoint, Microsoft Word und Microsoft Excel verfügbar.

## Dateitypeinstellungen erstellen oder bearbeiten {#create-or-edit-file-type-settings}

Erstellen oder bearbeiten Sie eine Dateitypeinstellung, um anzugeben, wie das Programm die Konvertierung unterstützter Dateitypen handhabt. Unter Windows können Sie die Anwendungseinstellungen für jeden unterstützten Dateityp einrichten. Unter UNIX und Linux können Sie die Anwendungseinstellungen für HTML-to-PDF und OpenOffice einrichten.

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste]** > **[!UICONTROL PDF Generator]** > **[!UICONTROL Dateitypeinstellungen]**.
1. Klicken Sie auf Neu oder auf den Namen einer Einstellung.
1. Geben Sie im Feld &quot;Dateinamenerweiterungen&quot;die Dateinamenerweiterungen (durch Kommas getrennt) für Dateitypen ein, die für diese Anwendung akzeptiert werden. Schließen Sie den Punkt vor oder einen Leerzeichen zwischen den Erweiterungen nicht ein. Der Standardwert lautet `bmp,gif,jpeg,jpg,tif,tiff,png`.
1. (Optional) Um die optische Zeichenerkennung (OCR) von Text in Grafiken oder Bildern zu aktivieren, wählen Sie „OCR verwenden“ aus und legen Sie die folgenden Optionen fest:

**Primäre OCR-Sprache:** Die Sprache, die die OCR-Engine zum Erkennen der Zeichen verwenden soll. Die Standardeinstellung ist Englisch (US).

**PDF Output Style:** Wählen Sie Durchsuchbares Bild aus, um ein Bitmap-Bild der Seiten im Vordergrund und den gescannten Text auf einer unsichtbaren Ebene darunter zu haben. Das Erscheinungsbild der Seite ändert sich nicht, aber der Text kann ausgewählt und gelesen werden. Wählen Sie Formatierter Text und Grafiken aus, um die Originalseite mithilfe von erkanntem Text, Schriftarten, Bildern und anderen grafischen Elementen zu rekonstruieren. Die Standardeinstellung ist Durchsuchbares Bild (exakt).

**Bilder neu berechnen:** Verringert die Anzahl der Pixel in Farb-, Graustufen- und Schwarzweißbildern. Die Neuberechnung gescannter Bilder erfolgt nach Abschluss des OCR. Die Standardeinstellung ist Niedrigste (600 dpi). Diese Option ist nicht verfügbar, wenn Sie den Ausgabestil der PDF auf &quot;Durchsuchbares Bild (exakt)&quot;festlegen.

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

Sie können den Standardwert für die Adobe PDF-Einstellungen, Sicherheitseinstellungen und Dateitypeinstellungen ändern, die für neu erstellte Quellen gelten. Eine Änderung der Standardeinstellungen hat keine Auswirkungen auf die Einstellungen vorhandener Quellen.

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste > PDF Generator]**.
1. Klicken Sie auf der Seite **[!UICONTROL Adobe PDF-Einstellungen]**, **[!UICONTROL Dateitypeinstellungen]** oder **[!UICONTROL Sicherheitseinstellungen]** auf **[!UICONTROL Standardeinstellungen festlegen]**.
1. Wählen Sie die gewünschten Standardeinstellungen aus. Eine oder mehrere der folgenden Einstellungen sind auf der Seite Standardeinstellungen festlegen verfügbar:

   **[!UICONTROL Adobe PDF Einstellung]**: Der ursprüngliche Standard ist „Standard“ (Acrobat 6).

   **[!UICONTROL Sicherheitseinstellungen]**: Der ursprüngliche Standard ist „Ohne Sicherheit“ (Acrobat 5).

   **[!UICONTROL Dateitypeinstellungen]**: Der ursprüngliche Standard ist „Standard“.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Löschen einer Dateitypeinstellung {#delete-a-file-type-setting}

Sie können eine nicht mehr verwendete Dateitypeinstellung löschen.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Dienste > PDF Generator > Dateitypeinstellungen]**.
1. Aktivieren Sie das Kontrollkästchen neben der zu löschenden Einstellung. Sie können mehrere Quellen auswählen. Einstellungen, für die kein Kontrollkästchen neben ihnen aktiviert ist, sind immer in PDF Generator enthalten und können nicht gelöscht werden.
1. Klicken Sie auf der Seite „Löschbestätigung“ auf **[!UICONTROL Löschen]** und dann nochmals auf **[!UICONTROL Löschen]**.

## PDF-Einstellungen für Bild {#image-to-pdf-settings}

Die folgenden Optionen bestimmen, wie Bilddateien in PDF konvertiert werden. Anweisungen zum Zugriff auf diese Einstellungen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Dateinamenerweiterungen:** Eine durch Kommas getrennte Liste von Dateinamenerweiterungen, die konvertiert werden können.

**Ersatzkonverter versuchen:** PDF Generator kann entweder Java™ oder Acrobat verwenden, um Bilddateien in PDF-Dateien zu konvertieren. Wenn diese Option aktiviert ist und eine Konvertierung fehlschlägt oder das angegebene Zeitlimit erreicht, versucht der PDF Generator die Konvertierung mithilfe der alternativen Methode. Wenn die alternative Methode fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

>[!NOTE]
>
>JPEG 2000 Dateien können nur mit Acrobat konvertiert werden.

**OCR verwenden:** Gibt an, ob die optische Zeichenerkennung (Optical Character Recognition, OCR) auf die PDF-Datei angewendet werden soll. Mit OCR-Software können Sie den Text in einer PDF-Datei durchsuchen, korrigieren und kopieren.

***Hinweis **: Die OCR PDF-Funktion (durchsuchbare PDF) wird nur unter Microsoft Windows unterstützt.*

**Primäre OCR-Sprache:** Die von der OCR-Engine zum Erkennen der Zeichen zu verwendende Sprache.

**Stil der PDF-Ausgabe:** Bestimmt den Typ des zu erstellenden PDF. Alle Formate wenden OCR und Schriftart- und Seitenerkennung auf die Bilder im Text an und konvertieren sie in normalen Text.

**Durchsuchbares Bild:** Stellt sicher, dass der Text durchsuchbar und auswählbar ist. Mit dieser Option wird das Originalbild beibehalten, nach Bedarf desketiert und eine unsichtbare Textebene darüber platziert. Die Option Bilder neu berechnen bestimmt, ob und in welchem Umfang das Bild neu berechnet wird.

**Durchsuchbares Bild (exakt):** Stellt sicher, dass der Text durchsuchbar und auswählbar ist. Diese Option behält das Originalbild bei und platziert eine unsichtbare Textebene darüber. Empfohlen für Fälle, in denen eine maximale Treue zum Originalbild erforderlich ist.

**ClearScan**: Synthetisiert eine neue Type-3-Schriftart, die dem Original sehr nahe kommt, und behält den Seitenhintergrund bei, indem eine Kopie mit niedriger Auflösung verwendet wird.

**Bilder neu berechnen**: Verringert die Anzahl der Pixel in Farb-, Graustufen- und Schwarzweißbildern nach Abschluss der optischen Zeichenerkennung (OCR). Wählen Sie den anzuwendenden Grad der Neuberechnung aus. Höhere Optionen führen zu weniger Neuberechnung, wodurch PDF mit höherer Auflösung generiert werden.

## Adobe PDF-Exporteinstellungen (nur Windows) {#adobe-pdf-export-settings-windows-only}

Die Einstellung &quot;Dateityp exportieren&quot;im Abschnitt mit den Exporteinstellungen für Adobe PDF wird zum Konvertieren einer PDF-Datei in ein anderes Format verwendet. Die Standardeinstellung ist HTML 4.01 mit Cascading Style Sheets (CSS) 1.0(*.htm, *.html).

Anweisungen zum Zugriff auf diese Einstellung finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

## „HTML in PDF“-Einstellungen {#html-to-pdf-settings}

Die folgenden Optionen bestimmen, wie HTML-Dateien in PDF konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Ersatzkonverter versuchen**: PDF Generator kann entweder Java™ oder Acrobat verwenden, um HTML-Dateien in PDF zu konvertieren. Wenn diese Option aktiviert ist und eine Konvertierung fehlschlägt oder das angegebene Zeitlimit erreicht, versucht der PDF Generator die Konvertierung mithilfe der alternativen Methode. Wenn die alternative Methode fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**Standardcodierung**: Legt die Eingabecodierung des Dateitexts über ein Menü mit Betriebssystemen und Alphabeten fest. Verwendet die Auswahl, die in der Option „Standardkodierung“ angezeigt wird, nur dann an, wenn die HTML-Quelldatei keinen Kodierungstyp angibt.

**Vom System ausgewählte Codierung**: Ignoriert jegliche Codierung, die in der HTML-Quelldatei angegeben ist, und verwendet die in der Option „Standardcodierung“ angezeigte Auswahl.

### Spidern-Einstellungen {#spidering-settings}

*Spidern* scannt Webseiten auf Links zu anderen Webseiten. Wenn ein Link zu einer anderen Webseite auftritt, wird die Zielseite abgerufen und in das generierte PDF-Dokument aufgenommen. Aktivieren Sie diese Optionen, um die Anzahl der Ebenen festzulegen, die abgerufen und in PDF konvertiert werden sollen:

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

Aktivieren Sie diese Optionen, um festzulegen, wie Inhalte angezeigt werden, wie Seiten im PDF-Dokument angezeigt werden und wie die Vergrößerungsstufe festgelegt wird:

**Anzeigen**: Wählen Sie die Bereiche aus, die in Acrobat geöffnet werden sollen, wenn das PDF-Dokument geöffnet wird.

**Seiten-Layout**: Wählen Sie die Art des Seiten-Layouts für das PDF-Dokument.

**Vergrößerung**: Wählen Sie die voreingestellte Vergrößerung für die Ansicht beim Öffnen des PDF-Dokuments oder wählen Sie einen benutzerdefinierten Wert. Wenn Sie eine Standardeinstellung auswählen, wird die standardmäßige Acrobat-Vergrößerung verwendet.

**Auf folgender Seite öffnen**: Geben Sie die Nummer der Seite an, auf der das PDF-Dokument geöffnet werden soll.

### Fensteroptionen {#window-options}

Aktivieren Sie diese Optionen, um festzulegen, wie die Fenstergröße und -anzeige dargestellt werden.

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

PDF Generator unterstützt die Möglichkeit, ein Video zum Adobe-Flash (SWF oder FLV-Datei) zu senden und eine PDF-Datei mit einem darin eingebetteten Adobe-Flash zu erstellen. Für diese Konvertierung muss keine Adobe-Flash Player auf dem Forms-Server installiert sein. Anweisungen zum Zugriff auf diese Option finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**Dateinamenerweiterungen:** Durch Kommas getrennte Liste von Dateinamenerweiterungen, die konvertiert werden können.

## „XPS in PDF“-Einstellungen {#xps-to-pdf-settings}

XML Paper Specification (XPS) wird in Windows Printing Machine verwendet. Dies ist ein Microsoft-Format und kann über eine beliebige Microsoft Office-Anwendung erstellt werden. AEM Formulare bieten die Möglichkeit, XPS-Dateien zu konvertieren PDF.

**Dateinamenerweiterungen:** Durch Kommas getrennte Liste aller XPS-Dateinamenerweiterungen, die konvertiert werden können. Derzeit ist nur ein Format verfügbar: .xps.

## PDF-Optimierungseinstellungen {#pdf-optimizer-settings}

PDF Generator unterstützt die Möglichkeit, die Größe von PDF-Dateien zu reduzieren. Ob Sie alle diese Einstellungen oder nur einige wenige verwenden, hängt davon ab, wie Sie die Dateien verwenden möchten, sowie von den wesentlichen Eigenschaften, die eine Datei aufweisen muss. In den meisten Fällen sind die Standardeinstellungen für maximale Effizienz geeignet. So sparen Sie Speicherplatz, indem Sie eingebettete Schriftarten entfernen, Bilder komprimieren und Elemente aus den nicht mehr benötigten Dateien entfernen.

>[!NOTE]
>
>Durch die Optimierung eines digital signierten Dokuments werden die digitalen Signaturen entfernt und ungültig gemacht.

Anweisungen zum Zugriff auf diese Einstellung finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](configuring-file-type-settings.md#create-or-edit-file-type-settings).

**PDF-Zielversion:** Gibt die Acrobat-Version an, mit der die PDF-Datei kompatibel ist.

### Schriften {#fonts}

1. Auswählen **Schriftarten.**
1. Wählen Sie eine der folgenden Optionen aus:

   **Einbettung für Zeichenformate aufheben:** Hebt die Einbettung für alle Schriftarten auf.

   **Einbettung für Zeichenformate nicht aufheben** Hebt die Einbettung für keine Schriftart auf.

   **Einbettung einiger Schriftarten aufheben:** Hebt die Einbettung nur für bestimmte Schriftarten auf. Führen Sie die folgenden Schritte aus, um die Schriftarten anzugeben, deren Einbettung Sie aufheben möchten:

   * Wählen Sie bei Bedarf einen anderen Schriftartenordner aus dem **Schriftquelle** Dropdown-Menü. In diesem Dropdown-Menü werden die Schriftartenordner aufgelistet, die in **Startseite > Einstellungen > Core-System > Core-Konfigurationen**.
   * Wählen Sie mindestens eine Schriftart aus dem **Verfügbare Schriftarten** Liste und klicken Sie auf **Hinzufügen**. Diese Schriftarten werden der **Einbettung für Schriftarten aufheben** Liste.
   * Wenn Sie die Einbettung für einige Schriftarten aufheben möchten, die nicht auf dem Forms-Server vorhanden sind, geben Sie die Namen dieser Schriftarten in die **Einbettung für Schriftarten aufheben** ankreuzen. Klicken Sie auf **Hinzufügen**.

   >[!NOTE]
   >
   >*Wenn Sie die Einbettung für einige Schriftarten aufheben möchten, von denen Untergruppen im Dokument eingebettet sind, setzen Sie das Symbol „+“ vor den Namen der Schriftart. Beispiel: „+Helvetica“.*

1. Wenn Sie lediglich die verwendeten Untergruppen der eingebetteten Schriftarten einbetten möchten, wählen Sie **Alle eingebetteten Schriftarten in Untergruppe zusammenfassen**.

   >[!NOTE]
   >
   >*Wenn Sie diese Option in Kombination mit **Einbettung für einige Schriftarten aufheben**, Schriftarten in der **Einbettung für Schriftarten aufheben**Die Einbettung von Listen ist noch vollständig aufgehoben.*

   >[!NOTE]
   >
   >*Schrifteinbettung in Untergruppen ist die Vorgehensweise, nur einen Teil einer Schriftart einzubetten. Eine Schriftartuntergruppe enthält nur die im Dokument verwendeten Zeichen.*

### Transparenz {#transparency}

Wenn Ihr PDF-Dokument Grafiken enthält, die Transparenz enthalten, können Sie die PDF Optimizer-Einstellungen verwenden, um die Transparenz zu reduzieren und die Dateigröße zu verringern.

>[!NOTE]
>
>Wenn Acrobat 4.0 und höher als Target-PDF-Version ausgewählt ist, werden alle transparenten Objekte reduziert. Bei anderen Target-PDF-Versionen wird Transparenz unterstützt und Sie können die Transparenzeinstellungen konfigurieren.

Auswählen **Transparenz** , um die Transparenzeinstellungen bei der Optimierung von PDF-Dokumenten zu konfigurieren.

**Transparenzstufe** Legt die Menge an Vektorinformationen fest, die beibehalten wird. Bei höheren Einstellungen werden mehr Vektorobjekte beibehalten, bei niedrigeren Einstellungen werden mehr Vektorobjekte gerastert. Bei Zwischeneinstellungen werden einfache Bereiche in Vektorform beibehalten und komplexe Bereiche werden gerastert. Wählen Sie die niedrigste Einstellung aus, um alle Grafiken zu rastern.

>[!NOTE]
>
>Der Umfang der Rastern hängt von der Komplexität der Seite und den Typen der überlappenden Objekte ab.

**Strichgrafiken und Text**: Auflösung, in der alle Objekte, einschließlich Bilder, Vektorgrafiken, Text und Verläufe, gerastert werden. Die unterstützten Werte sind 1 Pixel pro Zoll (ppi) bis 9600 ppi.

>[!NOTE]
>
>Die Auflösung von Strichgrafiken und Text sollte im Allgemeinen auf 600 bis 1200 ppi eingestellt werden, um eine hochwertige Rasterung zu gewährleisten, insbesondere bei Serifenschriften oder kleinen Schriftarten.

**Verlauf und Gitter**: Auflösung, auf die Verlauf und Gitter gerastert werden. Die unterstützten Werte sind 1 ppi bis 1200 ppi.

>[!NOTE]
>
>Die Auflösung für Verlauf und Gitter sollte im Allgemeinen auf 150 bis 300 ppi eingestellt werden, da sich die Qualität von Verläufen, Schlagschatten und weichen Kanten mit höheren Auflösungen nicht verbessert. Hingegen wird durch höhere Auflösungen die Druckzeit verlängert und die Datei unnötig vergrößert.

**Text in Pfade konvertieren**: Wandelt alle Textobjekte (Punkttext, Flächentext und Pfadtext) in Pfade um und ignoriert alle Textglyphen-Informationen auf Seiten mit Transparenz. Mit dieser Option wird sichergestellt, dass die Breite des Textes während der Reduzierung konsistent bleibt. Beachten Sie, dass die Aktivierung dieser Option dazu führt, dass kleine Schriften bei der Anzeige in Acrobat oder beim Drucken auf Desktop-Druckern mit niedriger Auflösung etwas dicker erscheinen. Sie wirkt sich nicht auf die Qualität des auf Druckern oder Bildträgern mit hoher Auflösung gedruckten Typs aus.

**Konturen in Pfade konvertieren** Wandelt auf Seiten mit Transparenz alle Konturen in einfache ausgefüllte Pfade um. Mit dieser Option wird sichergestellt, dass die Breite der Striche während der Reduzierung konsistent bleibt. Beachten Sie, dass die Aktivierung dieser Option dazu führt, dass dünne Striche etwas dicker erscheinen und die Leistung beim Reduzieren beeinträchtigen können.

**Komplexe Bereiche beschneiden**: Stellt sicher, dass die Grenzen zwischen Vektorgrafiken und gerasterten Grafiken entlang von Objektpfaden verlaufen. Mit dieser Option werden sichtbare Übergänge bei Grafiken vermieden, wenn ein Teil eines og

<!--
NOTE to WRITER: Unfinished sentence above.
-->

>[!NOTE]
>
>Einige Drucktreiber verarbeiten Raster- und Vektorgrafiken unterschiedlich, was manchmal zu Farbzuordnungen führt. Sie können Stitching-Probleme minimieren, indem Sie einige druckertreiberspezifische Farbmanagementeinstellungen deaktivieren. Diese Einstellungen variieren je nach Drucker. Weitere Informationen finden Sie in der Dokumentation zu Ihrem Drucker.

Überdruck beibehalten: Lässt die Farbe von transparentem Bildmaterial mit der Hintergrundfarbe verschmelzen, um einen Überdruckeffekt zu erzielen.

Die folgende Tabelle zeigt allgemeine Typen von Druckern und ihre in dpi gemessene Auflösung, ihre standardmäßige Bildschirmausrichtung, gemessen in lpi (Lines per Inch, Zeilen pro Zoll), und eine Neuberechnungsauflösung für Bilder, gemessen in Pixel pro Zoll (ppi). Wenn Sie beispielsweise auf einem 600-dpi-Laserdrucker drucken, geben Sie 170 für die Auflösung ein, mit der Bilder neu berechnet werden sollen.

**Bilder**: Wählen Sie diese Option, um Komprimierungs- und Neuberechnungsoptionen für Farb-, Graustufen- und Schwarzweißbilder festzulegen. Sie können mit diesen Optionen experimentieren, um einen guten Kompromiss zwischen Dateigröße und Bildqualität zu finden. Die Auflösungseinstellung für Farb- und Graustufenbilder sollte dem 1,5- bis 2-fachen der Rasterweitenlinierung entsprechen, mit der die Datei gedruckt wird. Die Auflösung für Schwarzweißbilder sollte mit der des Ausgabegeräts übereinstimmen. Durch das Speichern eines Schwarzweißbilds mit einer Auflösung von mehr als 1500 dpi wird die Dateigröße erhöht, ohne dass sich die Bildqualität spürbar verbessert. Bilder, die vergrößert werden, wie beispielsweise Karten, erfordern möglicherweise höhere Auflösungen.

>[!NOTE]
>
>Das Neuberechnen von Schwarzweißbildern kann zu unerwarteten Anzeigeergebnissen führen, z. B. zu keiner Bildanzeige. In diesem Fall deaktivieren Sie die Neuberechnung und konvertieren die Datei erneut. Dieses Problem tritt am wahrscheinlichsten bei der Teilberechnung und am wenigsten bei der bikubischen Neuberechnung auf.

<table>
 <tbody>
  <tr>
   <th><p><strong>Druckerauflösung</strong></p> </th>
   <th><p><strong>Standardzeilenbildschirm</strong></p> </th>
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

#### Objekte verwerfen {#discard-objects}

* Auswählen **Objekte verwerfen** um Objekte anzugeben, die aus dem PDF entfernt werden sollen, und um gekrümmte Linien in CAD-Zeichnungen zu optimieren.
* **Alle Formulareinsendungen verwerfen, Aktionen importieren und zurücksetzen**: Deaktiviert alle Aktionen im Zusammenhang mit dem Senden oder Importieren von Formulardaten und setzt Formularfelder zurück. Diese Option behält Formularobjekte bei, mit denen Aktionen verknüpft sind.
* **Alle JavaScript-Aktionen verwerfen**: Entfernt alle Aktionen aus dem PDF, die JavaScript verwenden.
* **Eingebettete Seitenminiaturen verwerfen**: Entfernt eingebettete Miniaturansichten von Seiten. Diese Option ist für große Dokumente nützlich, bei denen es lange dauern kann, bis Seitenminiaturansichten gezeichnet werden, nachdem Sie auf die Schaltfläche &quot;Seiten&quot;geklickt haben.
* **Glatte Linien in Kurven konvertieren**: Reduziert die Anzahl der Steuerpunkte, die zum Erstellen von Kurven in CAD-Zeichnungen verwendet werden, was zu kleineren PDF-Dateien und einer schnelleren Bildschirmwiedergabe führt.
* **Eingebettete Druckeinstellungen verwerfen**: Entfernt eingebettete Druckeinstellungen, z. B. Seitenskalierung und Duplexmodus, aus dem Dokument.
* **Lesezeichen verwerfen**: Entfernt alle Lesezeichen aus dem Dokument.
* **Formularfelder reduzieren**: Macht Formularfelder unbrauchbar, ohne ihr Aussehen zu ändern. Formulardaten werden mit der Seite zusammengeführt, um Seiteninhalt zu werden.
* **Alle alternativen Bilder verwerfen**: Entfernt alle Versionen eines Bildes mit Ausnahme der Version, die für die Anzeige auf dem Bildschirm vorgesehen ist. Einige PDF enthalten mehrere Versionen desselben Bildes für verschiedene Zwecke, z. B. niedrige Bildschirmauflösung und Druck mit hoher Auflösung.
* **Dokument-Tags verwerfen**: Entfernt Tags aus dem Dokument, wodurch auch die Barrierefreiheits- und Umfließen-Funktionen für den Text entfernt werden.
* **Bildfragmente erkennen und zusammenführen**: Sucht nach Bildern oder Masken, die in dünne Scheiben fragmentiert sind, und versucht, die Scheiben in einem Bild oder einer Maske zusammenzuführen.
* **Eingebetteten Suchindex verwerfen**: Entfernt eingebettete Suchindizes, wodurch die Dateigröße verringert wird.

#### Benutzerdaten verwerfen {#discard-user-data}

Auswählen **Benutzerdaten verwerfen** um alle persönlichen Informationen zu entfernen, die Sie nicht an andere Benutzer weitergeben oder für diese freigeben möchten.

* **Alle Kommentare, Forms und Multimedia verwerfen**: Entfernt alle Kommentare, Formulare, Formularfelder und Multimedia-Dateien aus der PDF.
* **Alle Objektdaten verwerfen**: Entfernt alle Objekte aus dem PDF.
* **Externe Querverweise verwerfen**: Entfernt Links zu anderen Dokumenten. Links, die zu anderen Stellen innerhalb der PDF springen, werden nicht entfernt.
* **Ausgeblendeten Ebeneninhalt verwerfen und sichtbare Ebenen reduzieren**: Verringert die Dateigröße. Das optimierte Dokument sieht wie das ursprüngliche PDF aus, enthält jedoch keine Ebeneninformationen.
* **Dokumentinformationen und Metadaten verwerfen**: Entfernt Informationen im Dokumentinformationswörterbuch und alle Metadaten-Streams. (Verwenden Sie den Befehl &quot;Speichern unter&quot;, um Metadaten-Streams in eine Kopie der PDF wiederherzustellen.)
* **Dateianlagen verwerfen**: Entfernt alle Dateianlagen, einschließlich der Anlagen, die als Kommentare der PDF-Datei hinzugefügt wurden. (PDF Optimizer optimiert keine angehängten Dateien.)
* **Private Daten anderer Anwendungen verwerfen**: Entfernt Informationen aus einem PDF-Dokument, das nur für die Anwendung nützlich ist, die das Dokument erstellt hat. Diese Einstellung wirkt sich nicht auf die Funktionalität des PDF aus, verringert jedoch die Dateigröße.

### Bereinigen {#clean-up}

Wählen Sie **Bereinigung**, um nicht erforderliche Elemente aus dem Dokument zu entfernen.
Diese Elemente umfassen Elemente, die veraltet sind oder für die beabsichtigte Verwendung des Dokuments nicht mehr erforderlich sind. Das Entfernen bestimmter Elemente kann die Funktionalität der PDF ernsthaft beeinträchtigen. Standardmäßig werden nur Elemente ausgewählt, die keine Auswirkungen auf die Funktionalität haben. Wenn Sie sich nicht sicher sind, welche Auswirkungen das Entfernen anderer Optionen hat, verwenden Sie die Standardauswahl.

**Komprimierung**

Wählen Sie eine der folgenden Flate-Komprimierungsoptionen aus dem Dropdown-Menü aus:

* Gesamte Datei komprimieren
* Dokumentstruktur komprimieren
* Komprimierung entfernen
* Komprimierung unverändert lassen

**Verwenden Sie Flate , um nicht kodierte Streams zu kodieren**: Wendet Flate-Komprimierung auf alle nicht kodierten Streams an.

**Ungültige Lesezeichen verwerfen**: Entfernt Lesezeichen, die auf gelöschte Seiten im Dokument verweisen.

**Nicht referenzierte benannte Ziele verwerfen**: Entfernt benannte Ziele, auf die nicht intern innerhalb des PDF-Dokuments verwiesen wird. Diese Option überprüft nicht auf Links von anderen PDF-Dateien oder Websites.

**PDF für schnelle Webanzeige optimieren**: Strukturiert ein PDF-Dokument für das seitenweise Herunterladen (Byte-Serving) von Webservern um.

**Verwenden Sie stattdessen Flate in Streams, die LZW-Kodierung verwenden**: Wendet Flate-Komprimierung auf alle Inhalts-Streams und Bilder an, die LZW-Kodierung verwenden.

**Ungültige Links verwerfen**: Entfernt Links, die zu ungültigen Zielen springen.

**Seiteninhalt optimieren**: Konvertiert alle Zeichen am Zeilenende in Leerzeichen, wodurch die Flate-Komprimierung verbessert wird.

## Microsoft Excel-Einstellungen (nur Windows) {#microsoft-excel-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Excel-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](#create-or-edit-file-type-settings).

**OpenOffice als Ersatzkonverter versuchen**: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft Excel fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mit OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**Dateinamenerweiterungen**: Gibt die Dateinamenerweiterungen für Dateitypen an, die durch Kommas getrennt sind und für diese Anwendung akzeptiert werden. Der Standardwert lautet `xls,xlsx`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

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

Diese Optionen bestimmen, wie Microsoft PowerPoint-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](/help/forms/using/admin-help/configuring-file-type-settings2.md#create-or-edit-file-type-settings).

**[!UICONTROL OpenOffice als Ersatzkonverter versuchen]**: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft PowerPoint fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mit OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**[!UICONTROL Dateinamenerweiterungen]**: Gibt die Dateinamenerweiterungen für Dateitypen an, die durch Kommas getrennt sind und für diese Anwendung akzeptiert werden. Die Standardeinstellung ist ppt,pptx. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Schlüsselwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen:]** Konvertiert PowerPoint-Arbeitsblattnamen in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Quelldatei an Adobe PDF anhängen]**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu. Diese Option ist standardmäßig deaktiviert.

**[!UICONTROL Barrierefreiheit und Reflow mit getaggten Adobe PDF aktivieren]**: Bettet Tags in die PDF-Datei ein. Diese Option ist standardmäßig deaktiviert.

**[!UICONTROL Multimedia in PDF Multimedia konvertieren]**: Konvertiert nach Möglichkeit Multimedia in PDF Multimedia. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Konvertieren von Lautsprecherhinweisen]**: Konvertiert Lautsprechernotizen in PDF.

**[!UICONTROL Makros automatisch ausführen]**: Führt vor dem Konvertieren des Dokuments alle Makros im PowerPoint-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

**[!UICONTROL PDF-Layout basierend auf PowerPoint-Druckereinstellungen]**: Verwendet PowerPoint-Druckereinstellungen zum Layout des PDF-Dokuments.

**[!UICONTROL Links zu Adobe PDF hinzufügen]**: Behält vorhandene Links bei, wenn die Datei konvertiert wird. Das Erscheinungsbild von Links bleibt im Allgemeinen unverändert. Links können nur erstellt werden, wenn die Option Barrierefreiheit aktivieren ebenfalls ausgewählt ist. Diese Option ist standardmäßig deaktiviert.

**[!UICONTROL Folienübergänge in Adobe PDF speichern]**: Konvertiert Folienübergänge. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Animationen in Adobe PDF speichern]**: Speichert konvertierte Animationen in der PDF-Datei.

**[!UICONTROL Ausgeblendete Folien in PDF-Seiten konvertieren]**: Konvertiert ausgeblendete Folien.

**[!UICONTROL PDF/A-1a-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005 RGB“. Einige PowerPoint-Funktionen werden bei der Erstellung einer PDF-Datei nicht konvertiert. Wenn eine PowerPoint-Transition in Acrobat keine äquivalente Transition aufweist, wird eine ähnliche Transition ersetzt. Wenn sich mehrere Animationseffekte in derselben Folie befinden, wird ein einzelner Effekt verwendet. Seitenübergänge und Aufzählungszeichen werden konvertiert.

## Microsoft Project-Einstellungen (nur Windows) {#microsoft-project-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft-Projektdateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](#create-or-edit-file-type-settings).

1. **[!UICONTROL Dateinamenerweiterungen]**: Legt die Dateinamenerweiterungen für Dateitypen fest (durch Kommas getrennt), die für dieses Programm akzeptiert werden. Der Standardwert lautet `mpp`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

1. **[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Schlüsselwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.
1. **[!UICONTROL Quelldatei an Adobe PDF anhängen]**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu.
1. **[!UICONTROL PDF/A-1a-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005(RGB)“.
1. **[!UICONTROL Makros automatisch ausführen]**: Führt vor dem Konvertieren des Dokuments alle Makros im Microsoft Project-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

## Microsoft Word-Einstellungen (nur Windows) {#microsoft-word-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Word-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](#create-or-edit-file-type-settings).

**[!UICONTROL OpenOffice als Ersatzkonverter versuchen]**: Wenn diese Option aktiviert ist und eine Konvertierung mit Microsoft Word fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator, die Konvertierung mithilfe von OpenOffice auszuführen. Wenn die Konvertierung mit OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**[!UICONTROL Dateinamenerweiterungen]**: Gibt die Dateinamenerweiterungen für Dateitypen an, die durch Kommas getrennt sind und für diese Anwendung akzeptiert werden. Der Standardwert lautet `doc,docx,rtf,txt`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Schlüsselwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen]**: Konvertiert Überschriften in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Quelldatei an Adobe PDF anhängen]**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**[!UICONTROL Querverweise und Inhaltsverzeichnisse in Links konvertieren]**: Konvertiert alle Querverweise und Inhaltsverzeichniseinträge in Links. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Barrierefreiheit und Reflow mit getaggten Adobe PDF aktivieren]**: Bettet Tags in die PDF-Datei ein. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL PDF/A-1a-kompatible Datei erstellen]**: Erzwingt bei Auswahl die Verwendung der Einstellung PDF/A-1b:2005 RGB Adobe PDF .

**[!UICONTROL Makros automatisch ausführen]**: Führt vor dem Konvertieren des Dokuments alle Makros im Word-Dokument aus (z. B. ein Makro, das die aktuelle Uhrzeit einfügt).

**[!UICONTROL Dokumentmarkierung in Adobe PDF beibehalten]**: Konvertiert das Markup im Word-Dokument in Anmerkungen in der PDF-Datei.

**[!UICONTROL Verknüpfungen zu Adobe PDF hinzufügen:]** Konvertiert Hyperlinks in der Quelldatei in Hyperlinks im PDF-Dokument.

**[!UICONTROL Fußnoten- und Endnotenlinks konvertieren]**: Erstellt Links aus den Zitaten der Fußnoten und Endnoten zu Anmerkungen im PDF-Dokument.

**[!UICONTROL Angezeigte Kommentare in Anmerkungen in Adobe PDF konvertieren]**: Konvertiert Kommentare im Word-Dokument in Textanmerkungen im PDF-Dokument.

**[!UICONTROL Erweitertes Tagging aktivieren]**: Fügt erweiterte Tags für verbesserte Barrierefreiheit hinzu.

**[!UICONTROL Alle Stile in Lesezeichen konvertieren]**: Konvertiert alle Stile im Word-Dokument in Lesezeichen im PDF-Dokument.

**[!UICONTROL Stile mit Ebenen With Levels]** Gibt an, welche Stile im Word-Dokument zu Lesezeichen in der PDF-Datei konvertiert werden. Gibt auch die Ebene der Lesezeichen an. Um diese Funktion zu verwenden, deaktivieren Sie die Option **[!UICONTROL Alle Stile in Lesezeichen konvertieren]** und geben Sie die Stilnamen im folgenden Format an:

styleName1=level1[,styleName2=level2...]

Wenn ein Microsoft Word-Formatvorlagenname ein Komma (,) oder ein Gleichheitszeichen (=) enthält, stellen Sie den Sonderzeichen das Escape-Zeichen („\“) voran. So müssten Sie z. B. für einen Stil mit dem Namen „Überschrift, 1“ den Wert „Überschrift\, 1“ angeben.

## Microsoft Visio-Einstellungen (nur Windows) {#visio}

**Dokumentinformationen konvertieren**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Stichwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert. Diese Option ist standardmäßig aktiviert.

**Verknüpfungen zu Adobe PDF hinzufügen**: Behält alle Links bei. Standardmäßig ist diese Option aktiviert.

**Lesezeichen zu Adobe PDF hinzufügen**: Konvertiert Überschriften in Lesezeichen. Standardmäßig ist diese Option aktiviert.

**Quelldatei an Adobe PDF anhängen**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**Ebenen in Adobe PDF immer reduzieren**: Reduziert alle Visio-Ebenen.

**Alle Seiten konvertieren**: Konvertiert alle Seiten der Visio-Datei.

**Ebenenbereich bei Anzeige in Adobe Acrobat öffnen**: Wenn Visio-Ebenen nicht reduziert werden, öffnet sich ein Fenster, in dem Sie die Ebenen angeben können, die in der PDF-Datei erhalten bleiben, wenn sie mit Acrobat geöffnet werden. Standardmäßig ist diese Option aktiviert.

**PDF/A-1b-kompatible Datei erstellen**: Erzwingt die Verwendung der Adobe PDF-Einstellung „PDF/A-1b:2005 (RGB)“.

**Kommentare in Adobe PDF-Kommentare konvertieren**: Konvertiert Visio-Notizen in PDF-Kommentare.

## Microsoft Publisher-Einstellungen (nur Windows) {#microsoft-publisher-settings-windows-only}

Diese Optionen bestimmen, wie Microsoft Publisher-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](#create-or-edit-file-type-settings).

**[!UICONTROL Dateinamenerweiterungen]**: Gibt die Dateinamenerweiterungen für Dateitypen an, die durch Kommas getrennt sind und für diese Anwendung akzeptiert werden. Der Standardwert lautet `pub`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

## AutoCAD-Einstellungen (nur Windows) {#autocad-settings-windows-only}

Diese Optionen bestimmen, wie AutoCAD-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](/help/forms/using/admin-help/configuring-file-type-settings2.md#create-or-edit-file-type-settings).

**[!UICONTROL Dateinamenerweiterungen]**: Gibt die Dateinamenerweiterungen für Dateitypen an, die durch Kommas getrennt sind und für diese Anwendung akzeptiert werden. Der Standardwert lautet `dwg`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**[!UICONTROL Dokumentinformationen konvertieren]**: Fügt Dokumentinformationen aus dem Dialogfeld „Eigenschaften“ der Quelldatei hinzu, einschließlich Titel, Thema, Autor, Schlüsselwörtern, Manager, Unternehmen, Kategorie und Kommentaren. Standardmäßig ist diese Option aktiviert.

**[!UICONTROL Lesezeichen zu Adobe PDF hinzufügen]**: Konvertiert Überschriften in Lesezeichen.

**[!UICONTROL Ebenen in Adobe PDF immer reduzieren]**: Reduziert alle AutoCAD-Ebenen.

**[!UICONTROL Ebenenfenster bei Anzeige in Adobe Acrobat öffnen]**: Zeigt die Ebenenstruktur an, wenn das PDF in Acrobat geöffnet wird.

**[!UICONTROL PDF/E-1-kompatible Datei erstellen]**: Erstellt eine Datei, die PDF/E-1-kompatibel ist. PDF/E ist ein ISO-Standard für den Austausch von Ingenieurwissenschaften und technischer Dokumentation. Weitere Informationen zu PDF/E-1 finden Sie unter [Adobe- und Industriestandards](https://www.adobe.com/de/enterprise/standards/index.html).

**[!UICONTROL Alle Layouts konvertieren]**: Umfasst alle Layouts im PDF.

**[!UICONTROL Modellbereich in 3D konvertieren]**: Wenn diese Option aktiviert ist, wird das Layout des Modellraums in eine 3D-Anmerkung auf der PDF konvertiert.

**[!UICONTROL Links zu Adobe PDF hinzufügen]**: Behält, falls ausgewählt, alle Links bei.

**[!UICONTROL Quelldatei an Adobe PDF anhängen]**: Fügt die Quelldatei der PDF-Datei als Anlage hinzu.

**[!UICONTROL PDF/A-1b-kompatible Datei erstellen]**: Erzwingt die Verwendung der Adobe PDF-Einstellung PDF/A-1b.

**[!UICONTROL Alle Ebenen konvertieren]**: Standardmäßig konvertiert PDF Generator nur die Standardebene von AutoCAD-Dateien in PDF und nicht alle Ebenen in der Datei. Wählen Sie diese Option, um alle Ebenen der Datei zu konvertieren.

**[!UICONTROL Skalierungsinformationen einbetten]**: Behält Informationen zur Zeichenskala bei.

**[!UICONTROL Aktuelles Layout konvertieren]**: Nimmt nur das aktuelle Layout in die PDF auf.

**[!UICONTROL Liste der zu konvertierenden AutoCAD-Layouts]**: Eine AutoCAD-Zeichnung kann mehrere Layouts haben. Wenn dieses Feld leer ist, sind alle Layouts in der AutoCAD-Zeichnung im generierten PDF-Dokument enthalten. Um eine Teilmenge der Layouts selektiv zu konvertieren, geben Sie eine kommagetrennte Liste mit Layoutnamen an.

## OpenOffice-Einstellungen {#openoffice-settings}

Diese Optionen bestimmen, wie OpenOffice-Dateien konvertiert werden. Anweisungen zum Zugriff auf diese Optionen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](/help/forms/using/admin-help/configuring-file-type-settings2.md#create-or-edit-file-type-settings).

**PDFMaker als Ersatzkonverter testen**: Wenn diese Option aktiviert ist und eine Konvertierung mit OpenOffice fehlschlägt oder das angegebene Zeitlimit erreicht, versucht PDF Generator die Konvertierung mithilfe von PDFMaker auszuführen. Wenn die Konvertierung mit PDFMaker fehlschlägt oder das angegebene Zeitlimit erreicht, wird eine Ausnahme in die Protokolldatei geschrieben.

**Dateinamenerweiterungen**: Geben Sie die Dateinamenerweiterungen für Dateitypen an, getrennt durch Kommas, die für diese Anwendung akzeptiert werden. Der Standardwert lautet `odt,odp,ods,odg,odf,sxw,sxi,sxd`. Setzen Sie keinen Punkt vor und kein Leerzeichen zwischen die Erweiterungen.

**Bereich:** Konvertieren Sie alle Seiten oder geben Sie bestimmte Seiten oder einen Seitenbereich an. Wenn kein Seitenbereich definiert ist, werden alle Seiten konvertiert. Um einen Seitenbereich zu exportieren, verwenden Sie das Format 3-6. Um einzelne Seiten zu exportieren, verwenden Sie das Format 7;9;11. Sie können eine Kombination aus Seitenbereichen und einzelnen Seiten mit einem Format wie 3-6;8;10;12 exportieren.

**Seitenausrichtung**: Wählen Sie nur für Textdateien für das konvertierte PDF-Dokument entweder Hochformat oder Querformat aus.

**Bilder**: Konfigurieren Sie, wie Bilder konvertiert werden. EPS-Bilder mit eingebetteter Vorschau werden nur als Vorschau exportiert. EPS-Bilder ohne integrierte Vorschau werden als leere Platzhalter exportiert. Bei verlustfreier Komprimierung von Bildern bleiben alle Pixel erhalten. Bei JPEG-Komprimierung von Bildern und einem hohen Qualitätsniveau bleiben fast alle Pixel erhalten. Bei einer niedrigen Qualität gehen einige Pixel verloren und Artefakte werden eingeführt, die Dateigröße wird jedoch reduziert.

**Allgemein**: Aktivieren Sie die Optionen, um eine PDF-Datei mit Tags zu konvertieren oder Writer- und FormCalc-Dokumentnotizen, Impress-Folienübergangseffekte oder leere Seiten in die PDF-Datei zu exportieren. Wenn Tags exportiert werden, kann die Dateigröße stark zunehmen. Einige Tags, die exportiert werden, sind Inhaltsverzeichnisse, Hyperlinks und Steuerelemente.

Sie können auch angeben, wie Formulare gesendet werden. Die Optionen sind XML, FDF, PDF oder HTML. Diese Einstellung setzt die URL-Eigenschaft des Steuerelements außer Kraft, die Sie im Dokument festgelegt haben. Für das PDF-Dokument kann nur eine gemeinsame Einstellung ausgewählt werden:

* PDF (sendet das gesamte Dokument)
* FDF (sendet den Kontrollinhalt)
* HTML
* XML

**Tagging-PDF**: Ermöglicht die Erstellung von getaggtem PDF aus OpenOffice-Dokumenten. Mit Tags versehene PDF enthält Informationen über die Struktur des Dokumentinhalts. Dies kann bei der Anzeige des Dokuments auf Geräten mit verschiedenen Bildschirmen und bei der Verwendung von Bildschirmlesehilfen-Software hilfreich sein. Es hilft auch Barrierefreiheitssoftware, verschiedene nützliche Vorgänge mit dem PDF-Dokument auszuführen, z. B. das Vorlesen des Inhalts des PDF-Dokuments.

**Exportieren von Anmerkungen**: Konvertiert die Notizen in OpenOffice-Dokumenten in Notizen im generierten PDF-Dokument.

**Übergangseffekte verwenden**: Konvertiert die Folienübergangseffekte in OpenOffice-Präsentationen in entsprechende PDF-Übergangseffekte.

**Forms im Format übermitteln**: Erstellt ein PDF-Formular, das vom PDF ausgefüllt und gedruckt werden kann.

**Automatisch eingefügte leere Seiten exportieren**: Wenn diese Option aktiviert ist, werden automatisch eingefügte leere Seiten in das generierte PDF-Dokument aufgenommen. Dies ist nützlich, wenn Sie ein PDF-Dokument zweiseitig drucken. Beispielsweise kann ein Buch so konfiguriert werden, dass die erste Seite eines Kapitels immer auf einer ungeraden Seite beginnt. Wenn das vorherige Kapitel auf einer ungeraden Seite endet, fügt OpenOffice eine leere Seite mit gerader Seitenzahl ein. Diese Option steuert, ob diese geraden Seiten in die generierte PDF aufgenommen werden sollen.

## Andere Programmeinstellungen (nur Windows) {#other-applications-settings-windows-only}

Sie können die Einstellungen für andere Anwendungen nicht über Administration Console ändern. Sie zeigen die Dateinamenerweiterungen für die unterstützten Dateitypen an. Anweisungen zum Zugriff auf diese Einstellungen finden Sie unter [Dateitypeinstellungen erstellen oder bearbeiten](https://help.adobe.com/de_DE/AEMForms/6.1/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7e42.2.html).

* Corel WordPerfect:  `wpd`
* Adobe PageMaker: `pmd, pm6, p65, pm`
* Adobe FrameMaker: `fm`
* Adobe Photoshop: `psd`

Die Unterstützung dieser Dateitypen muss ggf. angepasst werden. Weitere Informationen finden Sie unter „Hinzufügen von Unterstützung für zusätzliche native Dateiformate“ in [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_62).

Wenn Sie Hilfe bei der Konfiguration eines PDFG-Netzwerkdruckers benötigen, finden Sie weitere Informationen unter [Einrichten eines PDFG-Netzwerkdruckers (nur Windows)](/help/forms/using/admin-help/setting-pdfg-network-printer-windows.md).
