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
ht-degree: 49%

---

# Installieren und Konfigurieren von ImageMagick für die Verwendung mit [!DNL Experience Manager Assets] {#install-and-configure-imagemagick-to-work-with-aem-assets}

ImageMagick ist ein Software-Plug-in zum Erstellen, Bearbeiten, Zusammenstellen oder Konvertieren von Bitmap-Bildern. Es kann Bilder in verschiedenen Formaten (über 200) lesen und schreiben, darunter PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF und SVG. Verwenden Sie ImageMagick, um die Größe von Bildern zu ändern, Bilder zu kippen, zu spiegeln, zu drehen, zu verzerren, zuzuschneiden und umzuwandeln. Darüber hinaus können Sie mit ImageMagick die Bildfarben anpassen, verschiedene Spezialeffekte anwenden oder Text, Linien, Polygone, Ellipsen und Kurven zeichnen.

Verwenden Sie die [!DNL Adobe Experience Manager] Medien-Handler von der Befehlszeile, um Bilder über ImageMagick zu verarbeiten. Unter [Best Practices für Assets-Dateiformate](/help/assets/assets-file-format-best-practices.md) finden Sie weitere Informationen zur Verwendung verschiedener Dateiformate mit ImageMagick. Unter [Von Assets unterstützte Formate](/help/assets/assets-formats.md) erfahren Sie mehr zu allen unterstützten Dateiformaten.

Um große Dateien mit ImageMagick zu verarbeiten, sollten Sie höhere Speicheranforderungen, potenzielle Änderungen an IM-Richtlinien und die Gesamtauswirkung auf die Leistung berücksichtigen. Die Speicheranforderungen hängen von verschiedenen Faktoren wie Auflösung, Bittiefe, Farbprofil und Dateiformat ab. Wenn Sie sehr große Dateien mit ImageMagick verarbeiten möchten, sollten Sie die [!DNL Experience Manager] Server. Einige hilfreiche Ressourcen finden Sie weiter unten.

>[!NOTE]
>
>Wenn Sie [!DNL Experience Manager] on [!DNL Adobe Managed Services] (AMS) Wenden Sie sich an den Kundensupport von Adobe, wenn Sie viele hochauflösende PSD- oder PSB-Dateien verarbeiten möchten. [!DNL Experience Manager] kann keine sehr hochauflösenden PSB-Dateien verarbeiten, die mehr als 30000 x 23000 Pixel sind.

## Installieren von ImageMagick {#installing-imagemagick}

Es sind mehrere ImageMagick-Installationsdateien für verschiedene Betriebssysteme verfügbar. Verwenden Sie die entsprechende Version für Ihr Betriebssystem.

1. Herunterladen der entsprechenden [ImageMagick-Installationsdateien](https://www.imagemagick.org/script/download.php) für Ihr Betriebssystem.
1. So installieren Sie ImageMagick auf der Festplatte, auf der das [!DNL Experience Manager] -Server, starten Sie die Installationsdatei.

1. Legen Sie die Path-Umgebungsvariable auf das ImageMagick-Installationsverzeichnis fest.
1. Um zu überprüfen, ob die Installation erfolgreich war, führen Sie den Befehl `identify -version` aus.

## Einrichten des Befehlszeilenprozessschritts {#set-up-the-command-line-process-step}

Sie können den Befehlszeilenprozesssschritt für Ihren jeweiligen Anwendungsfall einrichten. Führen Sie diese Schritte aus, um jedes Mal, wenn Sie eine JPEG-Bilddatei zu einer `/content/dam` auf [!DNL Experience Manager] server:

1. Im [!DNL Experience Manager] Server, wechseln Sie zur Workflow-Konsole (`https://[aem_server]:[port]/workflow`) und öffnen Sie die **[!UICONTROL DAM-Update-Asset]** Workflow-Modell.
1. Aus dem **[!UICONTROL DAM-Update-Asset]** Workflow-Modell öffnen Sie die **[!UICONTROL EPS-Miniaturansichten (unterstützt von ImageMagick)]** Schritt.
1. Im **[!UICONTROL Registerkarte Argumente]**, hinzufügen `image/jpeg` der **[!UICONTROL MIME-Typen]** Liste.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. Geben Sie im Feld **[!UICONTROL Befehle]** folgenden Befehl ein:

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. Wählen Sie die **[!UICONTROL Generiertes Ausgabeformat löschen]** und **[!UICONTROL Webausgabe generieren]** Flags.

   ![select_flags](assets/select_flags.png)

1. Legen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** die Details für die Ausgabedarstellung mit 1280x1280 Pixel fest. Geben Sie außerdem `image/jpeg` im **[!UICONTROL Mimetype]** ankreuzen.

   ![web_enabled_image](assets/web_enabled_image.png)

1. Klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

   >[!NOTE]
   >
   >Die `convert` kann bei bestimmten Windows-Versionen nicht ausgeführt werden (z. B. Windows SE), da es im Konflikt mit dem nativen `convert` -Dienstprogramm, das Teil der Windows-Installation ist. Geben Sie in diesem Fall den vollständigen Pfad zum ImageMagick-Programm an. Geben Sie zum Beispiel Folgendes an:
   >
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. Öffnen Sie die **[!UICONTROL Prozessminiaturansichten]** und fügen Sie den MIME-Typ hinzu. `image/jpeg` under **[!UICONTROL MIME-Typen überspringen]**.

   ![skip_mime_types](assets/skip_mime_types.png)

1. Im **[!UICONTROL Webfähiges Bild]** Registerkarte, MIME-Typ hinzufügen `image/jpeg` unter **[!UICONTROL Liste überspringen]**. Klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

   ![web_enabled](assets/web_enabled.png)

1. Speichern Sie den Workflow.

1. Laden Sie zur Überprüfung der ordnungsgemäßen Verarbeitung ein JPG-Bild in [!DNL Assets]. Überprüfen Sie nach Abschluss der Verarbeitung, ob ein gespiegeltes Bild und die Ausgabeformate generiert wurden oder nicht.

## Minimieren von Sicherheitslücken {#mitigating-security-vulnerabilities}

Aus der Verwendung von ImageMagick für die Bearbeitung von Bildern resultieren mehrere Sicherheitslücken. Beispielsweise bringt die Verarbeitung von Bildern, die von Benutzern übermittelt wurden, das Risiko der Ferncodeausführung mit sich.

Außerdem ist eine Reihe von Bildverarbeitungs-Plug-ins von der ImageMagick-Bibliothek abhängig, darunter „imagick“ von PHP, „rmagick“ und „paperclip“ von Ruby sowie „imagemagick“ von Nodejs.

Wenn Sie ImageMagick oder eine betroffene Bibliothek verwenden, empfiehlt Adobe, die bekannten Sicherheitslücken zu minimieren, indem Sie mindestens eine der folgenden Aufgaben ausführen (vorzugsweise beide):

1. Stellen Sie sicher, dass alle Bilddateien mit dem erwarteten [&quot;magische Bytes&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures) entspricht den von Ihnen unterstützten Bilddateitypen, bevor sie zur Verarbeitung an ImageMagick gesendet werden.
1. Verwenden Sie eine Richtliniendatei, um die verwundbaren ImageMagick-Codes zu deaktivieren. Die globale Richtlinie für ImageMagick finden Sie unter `/etc/ImageMagick`.
