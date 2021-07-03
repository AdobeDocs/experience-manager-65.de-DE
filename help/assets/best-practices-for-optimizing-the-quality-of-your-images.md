---
title: Best Practices für die Optimierung der Bildqualität
description: Erfahren Sie mehr über die Best Practices für die Optimierung der Bildqualität in Dynamic Media.
uuid: b73f0918-c723-4a0d-a63f-4242223c2d47
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 12baf001-dfc9-410a-9821-a3bae1324392
feature: Asset-Management
role: User, Admin
exl-id: 7a568cae-e505-4b3a-abc5-8aae723460c3
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 89%

---

# Best Practices für die Optimierung der Bildqualität {#best-practices-for-optimizing-the-quality-of-your-images}

Die Optimierung der Bildqualität kann viel Zeit in Anspruch nehmen, da zahlreiche Faktoren dazu beitragen, angemessene Ergebnisse zu erzielen. Das Ergebnis ist teilweise subjektiv, da Einzelpersonen die Bildqualität unterschiedlich empfinden. Daher ist strukturiertes Experimentieren entscheidend.

Adobe Experience Manager umfasst mehr als 100 Bildbereitstellungsbefehle für Dynamic Media, mit denen Bilder angepasst und optimiert und Ergebnisse gerendert werden können. Mit den folgenden Richtlinien können Sie den Prozess anhand von einigen wesentlichen Befehlen und Best Practices optimieren und schnell angemessene Ergebnisse erzielen.

## Best Practices für das Bildformat (`&fmt=`) {#best-practices-for-image-format-fmt}

* JPG oder PNG ist die optimale Auswahl für die Bereitstellung von Bildern in guter Qualität und mit angemessener Größe.
* Wenn kein Formatsbefehl in der URL angegeben ist, wird standardmäßig JPG bei der Bildbereitstellung von Dynamic Media verwendet.
* JPG nutzt ein Komprimierungsverhältnis von 10:1 und erzeugt normalerweise kleinere Bilddateien. PNG komprimiert im Verhältnis von etwa 2:1, außer manchmal, wenn Bilder einen weißen Hintergrund enthalten. Normalerweise sind PNG-Dateien aber größer als JPG-Dateien.
* JPG nutzt verlustreiche Komprimierung. Das heißt, dass Bildelemente (Pixel) bei der Komprimierung verloren gehen. PNG verwendet dagegen die verlustfreie Komprimierung.
* JPG komprimiert Fotos oft mit größerer Wiedergabetreue als synthetische Bilder mit scharfen Kanten und Kontrast.
* Wenn Bilder transparent sind, verwenden Sie PNG, da JPG keine Transparenz unterstützt.

Als Best Practice in Bezug auf das Bildformat wird empfohlen, mit der gängigsten Einstellung `&fmt=JPG` zu beginnen.

## Best Practices für die Bildgröße {#best-practices-for-image-size}

Eine der häufigsten Aufgaben betrifft die dynamische Reduzierung der Bildgröße. Dabei wird die Größe angegeben sowie (optional) welcher Downsampling-Modus für die Verkleinerung des Bildes verwendet wird.

* Für die Bildgröße ist es am besten und einfachsten, `&wid=<value>` und `&hei=<value>,` oder nur `&hei=<value>` zu verwenden. Mit diesen Parametern wird die Bildbreite automatisch entsprechend dem Seitenverhältnis festgelegt.
* `&resMode=<value>` steuert den Algorithmus für das Downsampling. Beginnen Sie mit `&resMode=sharp2`. Mit diesem Wert erreichen Sie die beste Bildqualität. Der Downsampling-Wert `value =bilin` ist zwar schneller, führt aber auch oft zum Aliasing von Artefakten.

Verwenden Sie als Best Practice für die Bildgröße `&wid=<value>&hei=<value>&resMode=sharp2` oder `&hei=<value>&resMode=sharp2`.

## Best Practices für Bild-Scharfzeichnung {#best-practices-for-image-sharpening}

Die Bild-Scharfzeichnung stellt den komplexesten Aspekt bei der Kontrolle von Bildern auf Websites dar. Hier werden viele Fehler gemacht. Nehmen Sie sich die Zeit und machen Sie sich mit der Funktionsweise von Scharfzeichnung und Unschärfemaske in Experience Manager vertraut, indem Sie die folgenden nützlichen Ressourcen lesen:

Whitepaper zu Best Practices [Scharfzeichnen von Bildern in Adobe Dynamic Media Classic](/help/assets/assets/sharpening_images.pdf) , das auch für Experience Manager gilt.

<!-- To be reviewed and updated: Broken link.
See also [Sharpening an image with unsharp mask](https://helpx.adobe.com/photoshop/atv/cs6-tutorials/sharpening-an-image-with-unsharp-mask.html). -->

Mit Experience Manager können Sie Bilder bei der Aufnahme, bei der Ausgabe oder bei beidem scharfzeichnen. In der Regel werden Bilder jedoch nur mit der einen oder der anderen Methode scharfgezeichnet, jedoch nicht mit beiden. Normalerweise erhalten Sie die besten Ergebnisse beim Scharfzeichnen von Bildern bei der Bereitstellung mit einer URL.

Sie können zwei Methoden zur Bild-Scharfzeichnung verwenden:

* Einfache Scharfzeichnung (`&op_sharpen`): Dies ähnelt dem in Photoshop verwendeten Scharfzeichnungsfilter und wendet einfache Scharfzeichnung auf die endgültige Ansicht des Bildes nach der dynamischen Skalierung an. Diese Methode kann aber nicht vom Benutzer konfiguriert werden. Es wird empfohlen, &amp;op_sharpen nur zu verwenden, wenn es unbedingt erforderlich ist.
* Unschärfemaske (`&op_USM`): Die Unschärfemaske ist ein dem Branchenstandard entsprechender Scharfzeichnungsfilter. Als Best Practice wird empfohlen, Bilder anhand der folgenden Richtlinien mit der Unschärfemaske scharfzuzeichnen. Bei Verwendung der Unschärfemaske können Sie die folgenden drei Parameter steuern:

   * `&op_sharpen=`amount,radius,threshold

      * **[!UICONTROL amount]** (0-5, Stärke des Effekts)
      * **[!UICONTROL radius]** (0-250, Breite der „Scharfzeichnungslinien“ um das scharfgezeichnete Objekt, in Pixel gemessen)

      Denken Sie daran, dass die Parameter „radius“und „amount“ sich gegenseitig beeinflussen. Wenn Sie „radius“ reduzieren, können Sie dies durch eine Erhöhung von „amount“ kompensieren. Der Radius ermöglicht eine genauere Kontrolle, da mit einem niedrigeren Wert nur die Kantenpixel scharfgezeichnet werden, während mit einem höheren Wert mehr Pixel scharfgezeichnet werden.

      * **[!UICONTROL threshold]** (0-255, Sensitivität des Effekts)

             Dieser Parameter bestimmt, wie stark sich die scharfgezeichneten Pixel vom Umgebungsbereich unterscheiden müssen, damit sie als Kantenpixel eingestuft und vom Filter scharfgezeichnet werden. Mit dem Parameter **[!UICONTROL Schwellenwert]** können Sie übermäßiges Scharfzeichnen von Bereichen mit ähnlichen Farben, z. B. Hauttönen, vermeiden. Bei einem Schwellenwert von 12 werden beispielsweise leichte Variationen der Hauttonhelligkeit ignoriert, um kein „Rauschen“ zu erzeugen, trotzdem wird kontrastreichen Bereichen, z. B. wo Wimpern auf die Haut treffen, Kantenkontrast hinzugefügt.
         
         Weitere Informationen zum Festlegen dieser drei Parameter, einschließlich Best Practices für den Filter, finden Sie in den folgenden Ressourcen:

         Experience Manager-Hilfethema zum Scharfzeichnen eines Bildes.

         Whitepaper zu Best Practices [Scharfzeichnen von Bildern in Adobe Dynamic Media Classic](/help/assets/assets/sharpening_images.pdf).

      * In Experience Manager können Sie auch einen vierten Parameter steuern: monochrome (0,1). Dieser Parameter bestimmt, ob eine Unschärfemaske auf jede Farbkomponente separat (mit dem Wert 0) oder auf die Bildhelligkeit/-intensität (mit dem Wert 1) angewendet wird.


Es wird empfohlen, mit dem Unschärfemasken-Parameter für den Radius zu beginnen. Sie können zu Beginn die folgenden Radiuseinstellungen verwenden:

* **[!UICONTROL Website]** : 0,2-0,3 Pixel
* **[!UICONTROL Fotodruck (250-300 ppi)]**  - 0,3-0,5 Pixel
* **[!UICONTROL Offset-Druck (266-300 ppi)]**  - 0,7-1,0 Pixel
* **[!UICONTROL Leinwanddruck (150 ppi)]**  - 1,5-2,0 Pixel

Erhöhen Sie den Wert schrittweise von 1,75 auf maximal 4. Wenn die Scharfzeichnung noch immer nicht Ihren Wünschen entspricht, erhöhen Sie den Radius um eine Dezimalstelle und erhöhen Sie den Wert erneut von 1,75 auf 4. Wiederholen Sie diesen Vorgang nach Bedarf.

Belassen Sie die Einstellung des Parameters „monochrome“ auf 0.

### Best Practices für die JPEG-Komprimierung (`&qlt=`) {#best-practices-for-jpeg-compression-qlt}

* Dieser Parameter steuert die JPG-Kodierungsqualität. Ein höherer Wert führt zu einer höheren Bildqualität, aber auch zu einer größeren Datei. Ein niedrigerer Wert dagegen bedeutet eine niedrigere Bildqualität, aber auch eine kleinere Datei. Der Bereich für diesen Parameter beträgt 0–100.
* Um die Qualität zu optimieren, setzen Sie den Parameterwert nicht auf 100. Die Unterschiede zwischen einer Einstellung von 90 oder 95 und 100 sind fast nicht wahrnehmbar, aber die Einstellung 100 erhöht die Größe der Bilddatei unnötigerweise. Um die Qualität zu optimieren, aber zu vermeiden, dass Bilddateien zu groß werden, setzen Sie daher den Wert von `qlt= value` auf 90 oder 95.
* Erstellen Sie eine Bilddatei mit geringer Dateigröße bei akzeptabler Bildqualität, indem Sie `qlt= value` auf 80 setzen. Werte unter 70 bis 75 führen zu einer erheblichen Verschlechterung der Bildqualität.
* Als Best Practice wird empfohlen, einen Kompromiss zu wählen: Setzen Sie `qlt= value` dazu auf 85.
* Verwendung der Chroma-Markierung in `qlt=`

   * Der Parameter `qlt=` verfügt über eine zweite Einstellung, mit der Sie das RGB-Chromatizitäts-Downsampling aktivieren (mit dem Wert `,1`) oder deaktivieren (mit dem Wert `,0`) können.
   * Beginnen Sie der Einfachheit halber mit ausgeschaltetem RGB-Chromatizitäts-Downsampling (`,0`). Diese Einstellung führt normalerweise zu einer höheren Bildqualität, insbesondere bei synthetischen Bildern mit vielen scharfen Kanten und Kontrasten.

Verwenden Sie als Best Practice für die JPG-Komprimierung `&qlt=85,0`.

## Best Practices für die JPEG-Skalierung (`&jpegSize=`) {#best-practices-for-jpeg-sizing-jpegsize}

jpegSize ist ein nützlicher Parameter, wenn Sie garantieren möchten, dass ein Bild eine bestimmte Größe für die Bereitstellung an Geräten mit begrenztem Speicher nicht übersteigt.

* Dieser Parameter wird in Kilobyte festgelegt (`jpegSize=&lt;size_in_kilobytes&gt;`). Damit wird die maximal zulässige Größe für die Bildbereitstellung definiert.
* `&jpegSize=` interagiert mit dem JPG-Komprimierungsparameter `&qlt=`. Wenn die JPG-Antwort mit dem angegebenen JPG-Komprimierungsparameter (`&qlt=`) den Wert von jpegSize nicht überschreitet, wird das Bild mit `&qlt=` wie definiert zurückgegeben. Andernfalls wird `&qlt=` nach und nach reduziert, bis das Bild der maximal zulässigen Größe entspricht oder bis das System bestimmt, dass die Bildgröße nicht erreicht werden kann, und einen Fehler zurückgibt.

Legen Sie als Best Practice `&jpegSize=` fest und fügen Sie den Parameter `&qlt=` hinzu, wenn Sie JPG-Bilder an Geräte mit begrenztem Speicher bereitstellen.

## Zusammenfassung der Best Practices {#best-practices-summary}

Um eine hohe Bildqualität und kleine Dateien zu erreichen, wird als Best Practice empfohlen, mit der folgenden Kombination aus Parametern zu beginnen:

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

Diese Einstellungskombination sorgt in den meisten Fällen für hervorragende Ergebnisse.

Wenn das Bild weiter optimiert werden muss, passen Sie die Parameter für die Scharfzeichnung (Unschärfemaske) schrittweise an, beginnend mit einem Radius von 0,2 oder 0,3. Erhöhen Sie dann schrittweise den Betrag von 1,75 auf maximal 4 (entspricht 400 % in Photoshop). Prüfen Sie, ob das gewünschte Ergebnis erzielt wurde.

Wenn die Scharfzeichnungsergebnisse noch immer nicht den Erwartungen entsprechen, erhöhen Sie den Radius in Dezimalschritten. Beginnen Sie den Wert bei jedem Dezimalschritt bei 1,75 und erhöhen Sie diesen schrittweise auf 4. Wiederholen Sie diesen Vorgang, bis Sie das gewünschte Ergebnis erzielen. Die oben genannten Werte stellen zwar einen von Kreativstudios anerkannten Ansatz dar, Sie können aber auch mit anderen Werten beginnen und andere Strategien verfolgen. Sie entscheiden subjektiv, wann die Ergebnisse zufriedenstellend sind. Daher ist das strukturierte Experimentieren entscheidend.

Beim Experimentieren können die folgenden allgemeinen Vorschläge hilfreich sein, um Ihren Workflow weiter zu optimieren:

* Testen Sie verschiedene Parameter in Echtzeit direkt auf einer URL.
* Denken Sie daran, dass Sie Dynamic Media-Bildverarbeitungsbefehle in einer Bildvorgabe zusammenfassen können. Eine Bildvorgabe besteht im Grunde aus URL-Befehlsmakros mit benutzerspezifischen Vorgabenamen (wie `$thumb_low$` und `&product_high$`). Der benutzerdefinierte Vorgabenname in einem URL-Pfad ruft diese Vorgaben auf. Mit dieser Funktion können Sie Befehle und Qualitätseinstellungen für verschiedene Nutzungsmuster von Bildern auf Ihrer Website verwalten und die Gesamtlänge von URLs reduzieren.
* Experience Manager bietet außerdem erweiterte Funktionen für die Optimierung der Bildqualität, wie das Scharfzeichnen von Bildern bei der Aufnahme. Für erweiterte Anwendungsfälle, in denen Optionen zur Abstimmung und Optimierung von Rendering-Ergebnissen zur Verfügung stehen, kann [Adobe Professional Services](https://business.adobe.com/de/customers/consulting-services/main.html) Ihnen mit benutzerdefinierten Einblicken und Best Practices helfen.
