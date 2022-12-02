---
title: Installieren und Konfigurieren von ImageMagick
description: Erfahren Sie mehr über die ImageMagick-Software, wie Sie diese installieren, den Befehlszeilenprozessschritt einrichten und damit Miniaturansichten von Bildern bearbeiten, zusammenstellen und generieren können.
contentOwner: AG
role: Admin
feature: Renditions,Developer Tools
exl-id: 6c149d31-1e64-4d29-a32a-58bd69e9fa98
source-git-commit: b2faf81983216bef9151548d90ae86f1c26a9f91
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 100%

---

# Installieren und konfigurieren Sie ImageMagick, um mit [!DNL Experience Manager Assets] arbeiten zu können. {#install-and-configure-imagemagick-to-work-with-aem-assets}

ImageMagick-Software ist ein Software-Plug-in zum Erstellen, Bearbeiten, Zusammenzusetzen oder Konvertieren von Bitmap-Bildern. Es kann Bilder in über 200 Formaten lesen und schreiben, darunter PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF und SVG. Verwenden Sie ImageMagick, um die Größe von Bildern zu ändern, Bilder zu kippen, zu spiegeln, zu drehen, zu verzerren, zuzuschneiden und umzuwandeln. Darüber hinaus können Sie mit ImageMagick die Bildfarben anpassen, verschiedene Spezialeffekte anwenden oder Text, Linien, Polygone, Ellipsen und Kurven zeichnen.

Verwenden Sie den Medien-Handler von [!DNL Adobe Experience Manager] über die Befehlszeile, um Bilder mithilfe von ImageMagick zu verarbeiten. Unter [Best Practices für Assets-Dateiformate](/help/assets/assets-file-format-best-practices.md) finden Sie weitere Informationen zur Verwendung verschiedener Dateiformate mit ImageMagick. Unter [Von Assets unterstützte Formate](/help/assets/assets-formats.md) erfahren Sie mehr zu allen unterstützten Dateiformaten.

Um große Dateien mit ImageMagick zu verarbeiten, sollten Sie höhere Speicheranforderungen, potenzielle Änderungen an IM-Richtlinien und die Gesamtauswirkung auf die Leistung berücksichtigen. Die Speicheranforderungen hängen von verschiedenen Faktoren wie Auflösung, Bittiefe, Farbprofil und Dateiformat ab. Wenn Sie sehr große Dateien mit ImageMagick verarbeiten möchten, müssen Sie ein ordnungsgemäßes [!DNL Experience Manager]-Server-Benchmark durchführen. Einige hilfreiche Ressourcen finden Sie weiter unten.

>[!NOTE]
>
>Wenn Sie [!DNL Experience Manager] in [!DNL Adobe Managed Services] (AMS) verwenden, wenden Sie sich an den Kunden-Support von Adobe, falls Sie viele PSD- oder PSB-Dateien mit hoher Auflösung verarbeiten möchten. [!DNL Experience Manager] kann keine PSB-Dateien mit sehr hoher Auflösung verarbeiten, die mehr als 30000 x 23000 Pixel groß sind.

## Installieren von ImageMagick {#installing-imagemagick}

Es sind mehrere ImageMagick-Installationsdateien für verschiedene Betriebssysteme verfügbar. Verwenden Sie die entsprechende Version für Ihr Betriebssystem.

1. Laden Sie die entsprechenden [ImageMagick-Installationsdateien](https://www.imagemagick.org/script/download.php) für Ihr Betriebssystem herunter.
1. Um ImageMagick auf der Festplatte zu installieren, auf der der [!DNL Experience Manager]-Server gehostet wird, starten Sie die Installationsdatei.

1. Legen Sie die Path-Umgebungsvariable auf das ImageMagick-Installationsverzeichnis fest.
1. Um zu überprüfen, ob die Installation erfolgreich war, führen Sie den Befehl `identify -version` aus.

## Einrichten des Befehlszeilenprozessschritts {#set-up-the-command-line-process-step}

Sie können den Befehlszeilenprozessschritt für Ihren jeweiligen Anwendungsfall einrichten. Führen Sie diese Schritte aus, um jedes Mal eine gespiegelte Version von Bildern und Miniaturansichten (140x100, 48x48, 319x319 und 1280x1280) zu erstellen, wenn Sie eine JPEG-Bilddatei zum Verzeichnis `/content/dam` auf dem [!DNL Experience Manager]-Server hinzufügen:

1. Wechseln Sie auf dem [!DNL Experience Manager]-Server zur Workflow-Konsole (`https://[aem_server]:[port]/workflow`) und öffnen Sie das Workflow-Modell **[!UICONTROL DAM-Update-Asset]**.
1. Öffnen Sie über das Workflow-Modell **[!UICONTROL DAM-Update-Asset]** den Schritt **[!UICONTROL EPS-Miniaturansichten (unterstützt von ImageMagick)]**.
1. Fügen Sie in der **[!UICONTROL Registerkarte „Argumente“]** `image/jpeg` zur Liste **[!UICONTROL MIME-Typen]** hinzu.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. Geben Sie im Feld **[!UICONTROL Befehle]** folgenden Befehl ein:

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. Aktivieren Sie die Flags **[!UICONTROL Erzeugte Ausgabedarstellung löschen]** und **[!UICONTROL Webausgabe erstellen]**.

   ![select_flags](assets/select_flags.png)

1. Legen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** die Details für die Ausgabedarstellung mit 1280x1280 Pixel fest. Geben Sie außerdem `image/jpeg` im Feld **[!UICONTROL Mimetype]** an.

   ![web_enabled_image](assets/web_enabled_image.png)

1. Klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

   >[!NOTE]
   >
   >In manchen Versionen von Windows (z. B. Windows SE) kann der Befehl `convert` fehlschlagen, da er in Konflikt mit dem nativen Dienstprogramm `convert` steht, das Teil der Windows-Installation ist. Geben Sie in diesem Fall den vollständigen Pfad zum ImageMagick-Programm an. Geben Sie zum Beispiel Folgendes an:
   >
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. Öffnen Sie den Schritt **[!UICONTROL Miniaturansichten verarbeiten]** und fügen Sie den MIME-Typ `image/jpeg` unter **[!UICONTROL MIME-Typen überspringen]** hinzu.

   ![skip_mime_types](assets/skip_mime_types.png)

1. Fügen Sie in der Registerkarte **[!UICONTROL Webfähiges Bild]** den MIME-Typ `image/jpeg` unter **[!UICONTROL Liste zum Überspringen]** hinzu. Klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

   ![web_enabled](assets/web_enabled.png)

1. Speichern Sie den Workflow.

1. Laden Sie zur Überprüfung der ordnungsgemäßen Verarbeitung ein JPG-Bild in [!DNL Assets] hoch. Überprüfen Sie nach Abschluss der Verarbeitung, ob ein gespiegeltes Bild und die Ausgabedarstellungen generiert wurden oder nicht.

## Minimieren von Sicherheitslücken {#mitigating-security-vulnerabilities}

Aus der Verwendung von ImageMagick für die Bearbeitung von Bildern resultieren mehrere Sicherheitslücken. Beispielsweise bringt die Verarbeitung von Bildern, die von Benutzern übermittelt wurden, das Risiko der Ferncodeausführung mit sich.

Außerdem ist eine Reihe von Bildverarbeitungs-Plug-ins von der ImageMagick-Bibliothek abhängig, darunter „imagick“ von PHP, „rmagick“ und „paperclip“ von Ruby sowie „imagemagick“ von Nodejs.

Wenn Sie ImageMagick oder eine betroffene Bibliothek verwenden, empfiehlt Adobe, die bekannten Sicherheitslücken zu minimieren, indem Sie mindestens eine der folgenden Aufgaben ausführen (vorzugsweise beide):

1. Vergewissern Sie sich, dass alle Bilddateien in Übereinstimmung mit den von Ihnen unterstützten Bilddateitypen mit den erwarteten [„magischen Bytes“](https://en.wikipedia.org/wiki/List_of_file_signatures) beginnen, bevor Sie sie zur Verarbeitung an ImageMagick senden.
1. Verwenden Sie eine Richtliniendatei, um die anfälligen ImageMagick-Codierer zu deaktivieren. Die globale Richtlinie für ImageMagick ist in `/etc/ImageMagick` zu finden.
