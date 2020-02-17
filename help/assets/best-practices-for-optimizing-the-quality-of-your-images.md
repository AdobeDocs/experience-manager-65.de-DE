---
title: Best Practices für die Optimierung der Bildqualität
description: Bewährte Verfahren zur Optimierung der Bildqualität in dynamischen Medien
uuid: b73f0918-c723-4a0d-a63f-4242223c2d47
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 12baf001-dfc9-410a-9821-a3bae1324392
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Best Practices für die Optimierung der Bildqualität {#best-practices-for-optimizing-the-quality-of-your-images}

Die Optimierung der Bildqualität kann viel Zeit in Anspruch nehmen, da zahlreiche Faktoren dazu beitragen, angemessene Ergebnisse zu erzielen. Das Ergebnis ist teilweise subjektiv, da Einzelpersonen die Bildqualität unterschiedlich empfinden. Daher ist strukturiertes Experimentieren entscheidend.

AEM umfasst mehr als 100 Befehle zur Bildbereitstellung für dynamische Medien zum Optimieren von Bildern und zum Rendern von Ergebnissen. Die folgenden Richtlinien helfen Ihnen, den Prozess zu optimieren und mithilfe einiger wichtiger Befehle und Best Practices schnell gute Ergebnisse zu erzielen.

## Best Practices für Bildformat (`&fmt=`) {#best-practices-for-image-format-fmt}

* JPG oder PNG ist die optimale Auswahl für die Bereitstellung von Bildern in guter Qualität und mit angemessener Größe.
* Wenn kein Formatsbefehl in der URL angegeben ist, wird standardmäßig JPG bei der Bildbereitstellung von dynamischen Medien verwendet.
* JPG nutzt ein Komprimierungsverhältnis von 10:1 und erzeugt normalerweise kleinere Bilddateien. PNG nutzt ein Komprimierungsverhältnis von 2:1, außer in einigen Fällen, z. B. wenn Bilder einen weißen Hintergrund aufweisen. Normalerweise sind PNG-Dateien aber größer als JPG-Dateien.
* JPG nutzt verlustreiche Komprimierung. Das heißt, dass Bildelemente (Pixel) bei der Komprimierung verloren gehen. PNG verwendet dagegen die verlustfreie Komprimierung.
* JPG komprimiert Fotos oft mit größerer Wiedergabetreue als synthetische Bilder mit scharfen Kanten und Kontrast.
* Wenn Bilder transparent sind, verwenden Sie PNG, da JPG keine Transparenz unterstützt.

As a best practice for image format, start with the most common setting `&fmt=JPG`.

## Best Practices für Bildgröße {#best-practices-for-image-size}

Eine der häufigsten Aufgaben betrifft die dynamische Reduzierung der Bildgröße. Dabei wird die Größe angegeben sowie (optional) welcher Downsampling-Modus für die Verkleinerung des Bildes verwendet wird.

* For image sizing, the best and most straightforward approach is to use `&wid=<value>` and `&hei=<value>,`or just `&hei=<value>`. Mit diesen Parametern wird die Bildbreite automatisch entsprechend dem Seitenverhältnis festgelegt.
* `&resMode=<value>`steuert den für die Neuberechnung verwendeten Algorithmus. Beginnen Sie mit `&resMode=sharp2`. Mit diesem Wert erreichen Sie die beste Bildqualität. While using the downsampling `value =bilin` is faster, it often results in the aliasing of artifacts.

Als Best Practice für die Bildgrößenänderung verwenden Sie `&wid=<value>&hei=<value>&resMode=sharp2` oder `&hei=<value>&resMode=sharp2`

## Best Practices für Bild-Scharfzeichnung {#best-practices-for-image-sharpening}

Die Bild-Scharfzeichnung stellt den komplexesten Aspekt bei der Kontrolle von Bildern auf Websites dar. Hier werden viele Fehler gemacht. Nehmen Sie sich die Zeit und machen Sie sich mit der Funktionsweise von Scharfzeichnung und Unschärfemaske in AEM vertraut, indem Sie die folgenden nützlichen Ressourcen lesen:

Best practices white paper [Sharpening images in Adobe Scene7 Publishing System and on Image Server](/help/assets/assets/s7_sharpening_images.pdf) applies to AEM as well.

Siehe auch [Scharfzeichnen eines Bildes mit einer Unschärfemaske](https://helpx.adobe.com/photoshop/atv/cs6-tutorials/sharpening-an-image-with-unsharp-mask.html).

In AEM können Sie Bilder bei der Aufnahme, bei der Bereitstellung oder an beiden Zeitpunkten scharfzeichnen. In den meisten Fällen sollten Sie Bilder aber nur mit einer Methode, nicht mit beiden scharfzeichnen. Normalerweise erhalten Sie die besten Ergebnisse beim Scharfzeichnen von Bildern bei der Bereitstellung mit einer URL.

Sie können zwei Methoden zur Bild-Scharfzeichnung verwenden:

* Simple sharpening ( `&op_sharpen`) – Similar to the sharpen filter used in Photoshop, simple sharpening applies basic sharpening to the final view of the image following dynamic resizing. Diese Methode kann aber nicht vom Benutzer konfiguriert werden. Es empfiehlt sich, &amp;op_sharpen nur dann zu verwenden, wenn dies erforderlich ist.
* Unsharp masking ( `&op_USM`) – Unsharp masking is an industry standard sharpening filter. Als Best Practice wird empfohlen, Bilder anhand der folgenden Richtlinien mit der Unschärfemaske scharfzuzeichnen. Bei Verwendung der Unschärfemaske können Sie die folgenden drei Parameter steuern:

   * `&op_sharpen=`Betrag,Radius,Schwellenwert

      * **[!UICONTROL Stärke]** (0-5, Stärke des Effekts)
      * **[!UICONTROL Radius]** (0-250, Breite der &quot;Scharfzeichnungslinien&quot;, die um das scharfgezeichnete Objekt gezogen werden, gemessen in Pixel)

         Beachten Sie, dass die Parameter Radius und Betrag gegeneinander arbeiten. Eine Verringerung des Radius kann durch eine Erhöhung des Betrags kompensiert werden. Radius ermöglicht eine bessere Steuerung, da ein niedrigerer Wert nur die Kantenpixel scharfzeichnet, während ein höherer Wert einen breiteren Pixelbereich scharfzeichnet.

      * **[!UICONTROL Schwellenwert]** (0-255, Empfindlichkeit der Wirkung).

         Dieser Parameter bestimmt, wie stark sich die scharfgezeichneten Pixel vom Umgebungsbereich unterscheiden müssen, damit sie als Kantenpixel eingestuft und vom Filter scharfgezeichnet werden. The **[!UICONTROL threshold]** parameter helps to avoid over-sharpening areas with similar colors, such as skin tones. Beispiel: Mit einem Schwellenwert von 12 werden geringfügige Abweichungen in der Hauttonhelligkeit ignoriert, um „Bildrauschen“ zu vermeiden, während dennoch Kantenkontrast zu kontrastreichen Bereichen hinzugefügt wird, z. B. wo Wimpern auf Haut treffen.
      Weitere Informationen zum Festlegen dieser drei Parameter, einschließlich Best Practices für den Filter, finden Sie in den folgenden Ressourcen:

      AEM-Hilfethema zum Scharfzeichnen eines Bildes.

      Best practices white paper [Sharpening images in Adobe Scene7 Publishing System and on Image Server](/help/assets/assets/s7_sharpening_images.pdf).

   * Mit AEM können Sie auch einen vierten Parameter steuern: Monochrom (0,1). Dieser Parameter bestimmt, ob die Unschärfemaske separat mit dem Wert 0 oder mit dem Wert 1 auf die Bildhelligkeit/Intensität angewendet wird.


Es wird empfohlen, mit dem Unschärfemasken-Parameter für den Radius zu beginnen. Sie können zu Beginn die folgenden Radiuseinstellungen verwenden:

* **[!UICONTROL Website]**: 0,2-0,3 Pixel
* **[!UICONTROL Fotografischer Druck (250 bis 300 ppi)]**: 0,3-0,5 Pixel
* **[!UICONTROL Offsetdruck (266 bis 300 ppi)]**: 0,7-1,0 Pixel
* **[!UICONTROL Leinwanddruck (150 ppi)]**: 1,5-2,0 Pixel

Erhöhen Sie den Wert schrittweise von 1,75 auf maximal 4. Wenn die Scharfzeichnung noch immer nicht Ihren Wünschen entspricht, erhöhen Sie den Radius um eine Dezimalstelle und erhöhen Sie den Wert erneut von 1,75 auf 4. Wiederholen Sie diesen Vorgang nach Bedarf.

Belassen Sie die Einstellung des Parameters „monochrome“ auf 0.

### Bewährte Verfahren für die JPEG-Komprimierung (`&qlt=`) {#best-practices-for-jpeg-compression-qlt}

* Dieser Parameter steuert die JPG-Kodierungsqualität. Ein höherer Wert führt zu einer höheren Bildqualität, aber auch zu einer größeren Datei. Ein niedrigerer Wert dagegen bedeutet eine niedrigere Bildqualität, aber auch eine kleinere Datei. Der Bereich für diesen Parameter beträgt 0–100.
* Um die Qualität zu optimieren, setzen Sie den Parameterwert nicht auf 100. Die Unterschiede zwischen einer Einstellung von 90 oder 95 und 100 sind fast nicht wahrnehmbar, aber die Einstellung 100 erhöht die Größe der Bilddatei unnötigerweise. Therefore, to optimize for quality but avoid image files becoming too large, set the `qlt= value` to 90 or 95.
* To optimize for a small image file size but keep image quality at an acceptable level, set the `qlt= value` to 80. Werte unter 70 bis 75 führen zu einer erheblichen Verschlechterung der Bildqualität.
* As a best practice, to stay in the middle, set the `qlt= value` to 85 to stay in the middle.
* Using the chroma flag in `qlt=`

   * The `qlt=` parameter has a second setting that lets you turn on RGB chromaticity downsampling using the value `,1` or off using the value `,0`.
   * To keep it simple, start with RGB chromaticity downsampling turned off (`,0`). This setting usually results in better image quality, especially for synthetic images with lots of sharp edges and contrast.

Verwenden Sie als Best Practice für die JPG-Komprimierung `&qlt=85,0`.

## Best Practices für JPEG-Skalierung (`&jpegSize=`) {#best-practices-for-jpeg-sizing-jpegsize}

jpegSize ist ein nützlicher Parameter, wenn Sie sicherstellen möchten, dass ein Bild eine bestimmte Größe für die Bereitstellung auf Geräten mit begrenztem Speicher nicht überschreitet.

* This parameter is set in kilobytes (`jpegSize=&lt;size_in_kilobytes&gt;`). It defines the maximum allowed size for image delivery.
* `&jpegSize=` interagiert mit dem JPG-Komprimierungsparameter `&qlt=`. If the JPG response with the specified JPG compression parameter (`&qlt=`) does not exceed the jpegSize value, the image is returned with `&qlt=` as defined. Otherwise, `&qlt=` is gradually decreased until the image fits in the maximum allowed size, or until the system determines it cannot fit and returns an error.

As a best practice, set `&jpegSize=` and add the parameter `&qlt=` if you are delivering JPG images to devices with limited memory.

## Zusammenfassung der Best Practices {#best-practices-summary}

Um eine hohe Bildqualität und kleine Dateien zu erreichen, wird als Best Practice empfohlen, mit der folgenden Kombination aus Parametern zu beginnen:

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

Diese Einstellungskombination sorgt in den meisten Fällen für hervorragende Ergebnisse.

Wenn das Bild weiter optimiert werden muss, passen Sie die Parameter für die Scharfzeichnung (Unschärfemaske) schrittweise an, beginnend mit einem Radius von 0,2 oder 0,3. Erhöhen Sie dann schrittweise den Betrag von 1,75 auf maximal 4 (entspricht 400 % in Photoshop). Prüfen Sie, ob das gewünschte Ergebnis erzielt wurde.

Wenn die Scharfzeichnungsergebnisse noch immer nicht den Erwartungen entsprechen, erhöhen Sie den Radius in Dezimalschritten. Beginnen Sie den Wert bei jedem Dezimalschritt bei 1,75 und erhöhen Sie diesen schrittweise auf 4. Wiederholen Sie diesen Vorgang, bis Sie das gewünschte Ergebnis erzielen. Die oben genannten Werte stellen zwar einen von Kreativstudios anerkannten Ansatz dar, Sie können aber auch mit anderen Werten beginnen und andere Strategien verfolgen. Sie entscheiden subjektiv, wann die Ergebnisse zufriedenstellend sind. Daher ist das strukturierte Experimentieren entscheidend.

Beim Experimentieren können auch die folgenden allgemeinen Empfehlungen nützlich sein, um Ihren Workflow zu optimieren:

* Testen Sie verschiedene Parameter in Echtzeit, entweder direkt über eine URL oder mithilfe der Bildanpassungsfunktion des Scene7 Publishing Systems, die eine Echtzeitvorschau für Anpassungsvorgänge bietet.
* Denken Sie daran, dass Sie Dynamic Media Image Serving-Befehle zu einer Bildvorgabe gruppieren können. An image preset is basically URL command macros with custom preset names such as `$thumb_low$` and `&product_high$`. Der benutzerspezifische Vorgabename in einem URL-Pfad ruft diese Vorgaben auf. Mit dieser Funktion können Sie Befehle und Qualitätseinstellungen für verschiedene Nutzungsmuster von Bildern auf Ihrer Website verwalten und die Gesamtlänge von URLs reduzieren.
* AEM bietet außerdem erweiterte Funktionen für die Optimierung der Bildqualität, wie das Scharfzeichnen von Bildern bei der Aufnahme. For advanced use cases where this may be an option to further tune and optimize rendering results, [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html) can help you with customized insight and best practices.

