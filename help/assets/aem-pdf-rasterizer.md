---
title: Verwenden von PDF Rasterizer zum Generieren von Ausgabeformaten
description: Generieren Sie mit der Adobe PDF Rasterizer-Bibliothek hochwertige Miniaturansichten und Ausgabeformate.
contentOwner: AG
role: Developer, Admin
feature: Developer Tools,Renditions
exl-id: 6f365d6b-3972-4885-8766-5889e24289f1
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 40%

---

# Verwenden von PDF Rasterizer {#using-pdf-rasterizer}

Wenn Sie große, inhaltsintensive PDF- oder AI-Dateien in [!DNL Adobe Experience Manager Assets], erzeugt die Standardbibliothek möglicherweise keine genaue Ausgabe. Die PDF Rasterizer-Bibliothek von Adobe kann eine zuverlässigere und genauere Ausgabe generieren, als die Ausgabe aus einer Standardbibliothek. Adobe empfiehlt die Verwendung der PDF Rasterizer-Bibliothek für die folgenden Szenarien:

Adobe empfiehlt die Verwendung der PDF Rasterizer-Bibliothek für folgende Dateien:

* Hohe, inhaltsintensive AI-Dateien oder PDF-Dateien.
* AI-Dateien und PDF-Dateien mit Miniaturansichten, die nicht standardmäßig generiert werden.
* AI-Dateien mit PMS-Farben (Pantone Matching System)

Mit PDF Rasterizer erstellte Miniaturansichten und Vorschauen weisen im Vergleich mit der standardmäßigen Ausgabe eine bessere Qualität auf und bieten daher eine konsistente Darstellung auf allen Geräten. Die Adobe PDF Rasterizer-Bibliothek unterstützt keine Farbraumkonvertierung. Die Ausgabe erfolgt unabhängig vom Farbraum der Quelldatei immer in RGB.

1. Installieren Sie das PDF Rasterizer-Paket auf Ihrem [!DNL Adobe Experience Manager] Bereitstellung von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/aem-assets-pdf-rasterizer-pkg-4.4.zip).

   >[!NOTE]
   >
   >Die PDF Rasterizer-Bibliothek ist nur für Windows und Linux verfügbar.

1. Zugriff auf [!DNL Assets] Workflow-Konsole unter `https://[aem_server]:[port]/workflow`. Öffnen [!UICONTROL DAM-Update-Asset] Arbeitsablauf.

1. Gehen Sie wie folgt vor, um die Generierung von Miniaturansichten und Web-Ausgabeformaten für PDF- und AI-Dateien mithilfe der Standardmethoden zu verhindern:

   * Öffnen Sie die **[!UICONTROL Prozessminiaturansichten]** Schritt und Hinzufügen `application/pdf` oder `application/postscript` im **[!UICONTROL MIME-Typen überspringen]** Feld unter **[!UICONTROL Miniaturen]** nach Bedarf.

   ![skip_mime_types-2](assets/skip_mime_types-2.png)

   * Im **[!UICONTROL Webfähiges Bild]** Registerkarte hinzufügen `application/pdf` oder `application/postscript` under **[!UICONTROL Liste überspringen]** je nach Ihren Anforderungen.

   ![Konfiguration zum Überspringen der Verarbeitung von Miniaturansichten für ein Bildformat](assets/web_enabled_imageskiplist.png)

1. Öffnen Sie die **[!UICONTROL Rastern von PDF/AI-Bildvorschau-Wiedergabe]** und entfernen Sie den MIME-Typ, für den Sie die standardmäßige Generierung von Vorschaubildarstellungen überspringen möchten. Entfernen Sie beispielsweise den MIME-Typ `application/pdf`, `application/postscript`oder `application/illustrator` von **[!UICONTROL MIME-Typen]** Liste.

   ![process_arguments](assets/process_arguments.png)

1. Ziehen Sie den Schritt **[!UICONTROL PDF Rasterizer-Handler]** aus dem Seitenbereich unter den Schritt **[!UICONTROL Miniaturansichten verarbeiten]**.
1. Konfigurieren Sie die folgenden Argumente für die **[!UICONTROL PDF Rasterizer-Handler]** step:

   * MIME-Typen: `application/pdf` oder `application/postscript`
   * Befehle: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Fügen Sie Größen für Miniaturansichten hinzu: 319:319, 140:100, 48:48. Fügen Sie ggf. eine benutzerdefinierte Konfiguration für Miniaturansichten hinzu.

   Die Befehlszeilenargumente für den `PDFRasterizer`-Befehl können Folgendes enthalten:

   * `-d`: Flag für ein reibungsloses Rendering von Text, Vektorgrafiken und Bildern. Erstellt Bilder mit besserer Qualität. Die Verwendung dieses Parameters führt allerdings zu einer langsamen Ausführung des Befehls und zu größeren Bildern.

   * `-s`: Maximale Bildgröße (Höhe oder Breite). Dieser Wert wird für jede Seite in DPI umgewandelt. Bei Seiten mit unterschiedlichen Größen wird u. U. jede Seite mit einem anderen Wert skaliert. Der Standardwert ist die tatsächliche Seitengröße.

   * `-t`: Ausgabebildtyp. Gültige Formate sind JPEG, PNG, GIF und BMP. Das Standardformat ist JPEG.

   * `-i`: Pfad für Eingabe-PDF. Dieser Parameter ist erforderlich.

   * `-h`: Hilfe


1. Um Zwischenausgabeformate zu löschen, wählen Sie **[!UICONTROL Erzeugte Ausgabe löschen]**.
1. Damit PDF Rasterizer Webausgabeformate generieren kann, wählen Sie **[!UICONTROL Webausgabe generieren]**.

   ![generate_web_renditions1](assets/generate_web_renditions1.png)

1. Geben Sie die Einstellungen in der **[!UICONTROL Webfähiges Bild]** Registerkarte.

   ![web_enabled_image1](assets/web_enabled_image1.png)

1. Speichern Sie den Workflow.
1. Damit PDF Rasterizer PDF-Seiten mit PDF-Bibliotheken verarbeiten kann, öffnen Sie die **[!UICONTROL DAM-Prozess-Unter-Asset]** -Modell aus [!UICONTROL Workflow] Konsole.
1. Ziehen Sie aus dem Seitenbereich den Schritt PDF Rasterizer-Handler unter den **[!UICONTROL Webfähiges Bildausgaben erstellen]** Schritt.
1. Konfigurieren Sie die folgenden Argumente für die **[!UICONTROL PDF Rasterizer-Handler]** step:

   * MIME-Typen: `application/pdf` oder `application/postscript`
   * Befehle: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Miniaturansichtsgrößen hinzufügen: `319:319`, `140:100`, `48:48`. Fügen Sie bei Bedarf benutzerdefinierte Konfigurationen für Miniaturansichten hinzu.

   Die Befehlszeilenargumente für den `PDFRasterizer`-Befehl können Folgendes enthalten:

   * `-d`: Flag für ein reibungsloses Rendering von Text, Vektorgrafiken und Bildern. Erstellt Bilder mit besserer Qualität. Die Verwendung dieses Parameters führt allerdings zu einer langsamen Ausführung des Befehls und zu größeren Bildern.

   * `-s`: Maximale Bildgröße (Höhe oder Breite). Dieser Wert wird für jede Seite in DPI umgewandelt. Bei Seiten mit unterschiedlichen Größen wird u. U. jede Seite mit einem anderen Wert skaliert. Der Standardwert ist die tatsächliche Seitengröße.

   * `-t`: Ausgabebildtyp. Gültige Formate sind JPEG, PNG, GIF und BMP. Das Standardformat ist JPEG.

   * `-i`: Pfad für Eingabe-PDF. Dieser Parameter ist erforderlich.

   * `-h`: Hilfe


1. Um Zwischenausgabeformate zu löschen, wählen Sie **[!UICONTROL Erzeugte Ausgabe löschen]**.
1. Damit PDF Rasterizer Webausgabeformate generieren kann, wählen Sie **[!UICONTROL Webausgabe generieren]**.

   ![generate_web_renditions](assets/generate_web_renditions.png)

1. Geben Sie die Einstellungen in der **[!UICONTROL Webfähiges Bild]** Registerkarte.

   ![web_enabled_image-1](assets/web_enabled_image-1.png)

1. Speichern Sie den Workflow.
1. Hochladen einer PDF- oder AI-Datei in [!DNL Experience Manager Assets]. PDF Rasterizer erstellt die Miniaturansichten und Webausgaben für die Datei.
