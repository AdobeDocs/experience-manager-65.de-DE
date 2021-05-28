---
title: Intelligente Bildbearbeitung
description: 'Die intelligente Bildbearbeitung wendet die individuellen anzeigebezogenen Benutzermerkmale an, um automatisch die richtigen Bilder für ein optimiertes individuelles Erlebnis zu präsentieren. Das Ergebnis: mehr Leistung und Interaktion.'
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: bf8c6bbd-847d-43d7-9ff4-7231bfd8d107
feature: Asset-Management,Ausgabeformate
role: Business Practitioner, Administrator
exl-id: e427d4ee-d5c8-421b-9739-f3cf2de36e41
source-git-commit: d407162e18f85f4fee0596581f004f8cf4c99458
workflow-type: tm+mt
source-wordcount: '1917'
ht-degree: 66%

---


# Intelligente Bildbearbeitung {#smart-imaging}

## Was ist die intelligente Bildbearbeitung? {#what-is-smart-imaging}

Die Technologie der intelligenten Bildbearbeitung nutzt die AI-Funktionen von Adobe Sensei und arbeitet mit vorhandenen &quot;Bildvorgaben&quot;zusammen, um die Leistung bei der Bildbereitstellung zu verbessern, indem Bildformat, -größe und -qualität basierend auf den Funktionen des Client-Browsers automatisch optimiert werden.

>[!NOTE]
>
>Für diese Funktion müssen Sie das vordefinierte CDN (Content Delivery Network) verwenden, das zum Lieferumfang von Adobe Experience Manager Dynamic Media gehört. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

Die intelligente Bildbearbeitung profitiert auch von der zusätzlichen Leistungssteigerung durch die vollständige Integration mit dem erstklassigem Premium-CDN-Dienst von Adobe. Dieser Dienst ermittelt die optimale Internet-Route zwischen Servern, Netzwerken und Peering-Punkten. Er findet eine Route mit der niedrigsten Latenz und der niedrigsten Paketverlustrate, anstatt die Standardroute im Internet zu verwenden.

Die folgenden Beispiele für Bild-Assets veranschaulichen die Optimierungen durch die intelligente Bildbearbeitung:

| Bild<br>(URL) | Miniaturansicht | Größe<br> (JPEG) | Größe (WebP)<br> (mit intelligenter Bildbearbeitung) | Reduzierung in % |
|---|---|---|---|---|
| [Bild 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture1](/help/assets/assets-dm/picture1.png) | 73,75 KB | 45,92 KB | 38 % |
| [Bild 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 191 KB | 70,66 KB | 63 % |
| [Bild 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 96,64 KB | 39,44 KB | 59 % |
| [Bild 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 315,80 KB | 178,19 KB | 44 % |
|  |  |  |  | Durchschnitt = 51 % |

Ähnlich wie oben führte Adobe auch einen Test mit 7009 URLs von Live-Kundensites durch. Die Dateigrößenoptimierung von JPEG-Bildern konnte im Durchschnitt um 38 % gesteigert werden. Durch die Konvertierung von PNG-Dateien in das WebP-Format konnte die Dateigrößenoptimierung durchschnittlich um 31 % gesteigert werden. Diese Optimierung ist dank der Funktionen der intelligenten Bildbearbeitung möglich.

<!-- CQDOC-17915 HIDDEN FOR NOW AS OF MAY 28 2021 On the mobile web, the challenges are compounded by two factors:

* Large variety of devices with different form factors and high-resolution displays.
* Constrained network bandwidth.

In terms of images, the goal is to serve the best quality images as efficiently as possible.

### About device pixel ratio optimization {#dpr}

Device pixel ratio (DPR) &ndash; also known as CSS pixel ratio &ndash; is the relation between a device’s physical pixels and logical pixels. Especially with the advent of retina screens, the pixel resolution of modern mobile devices is growing at a fast rate.

Enabling Device Pixel Ratio optimization renders the image at the native resolution of the screen which makes it look crisp.

Turning on Smart Imaging DPR configuration automatically adjusts the requested image based on pixel density of the display the request is being served from. Currently, the pixel density of the display comes from Akamai CDN header values.

| Permitted values in the URL of an image | Description |
|---|---|
| `dpr=off` | Turn off DPR optimization at an individual image URL level.| 
| `dpr=on,dprValue` | Override the DPR value detected by Smart Imaging, with a custom value (as detected by any client-side logic or other means). Permitted value for `dprValue` is any number greater than 0. Specified values of 1.5, 2, or 3 are typical. |

>[!NOTE]
>
>* You can use `dpr=on,dprValue` even if the company level DPR setting as off.
>* Owing to DPR optimization, when the resultant image is greater than the MaxPix Dynamic Media setting, MaxPix width is always recognized by maintaining the image's aspect ratio.

| Requested Image size | DPR value | Delivered image size |
|---|---|---|
| 816x500 | 1 | 816x500 |
| 816x500 | 2 | 1632x1000 |

See also [When working with images](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-images) and [When working with Smart Crop](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

### About network bandwidth optimization {#network-bandwidth-optimization}

Turning on Network Bandwidth automatically adjusts the image quality that is served based on actual network bandwidth. For poor network bandwidth, DPR optimization is automatically turned off, even if it is already on.

If desired, your company can opt out of network bandwidth optimization at the individual image level by appending `network=off` to the URL of the image.

| Permitted value in the URL of an image | Description |
|---|---|
| `network=off` | Turns off network optimization at an individual image URL level. |

>[!NOTE]
>
>DPR and network bandwidth values are based on the detected client-side values of the bundled CDN. These values are sometimes inaccurate. For example, iPhone5 with DPR=2 and iPhone12 with DPR=3, both show DPR=2. Still, for high-resolution devices, sending DPR=2 is better than sending DPR=1. Coming soon: Adobe is working on client-side code to accurately determine an end user's DPR. -->

## Was sind die Hauptvorteile der intelligenten Bildbearbeitung? {#what-are-the-key-benefits-of-smart-imaging}

Da Bilder den Großteil der Ladezeit einer Seite ausmachen, kann die Leistungsverbesserung erhebliche Auswirkungen auf ein Unternehmen haben, z. B. höhere Konversionen, Besuchszeiten pro Site und niedrigere Absprungraten der Site.

Verbesserungen der neuesten Version der intelligenten Bildbearbeitung:

* Das Google SEO-Ranking für Webseiten mit der neuesten intelligenten Bildbearbeitung wurde verbessert.
* Stellt optimierte Inhalte sofort (zur Laufzeit) bereit.
* Verwendet Adobe Sensei-Technologie zur Konvertierung gemäß der in der Bildanforderung angegebenen Qualität (qlt).
* Die intelligente Bildbearbeitung kann mithilfe des URL-Parameters „bfc“ deaktiviert werden.
* TTL (Time To Live)-unabhängig. Zuvor war eine TTL von mindestens 12 Stunden erforderlich, damit die intelligente Bildbearbeitung funktioniert.
* Zuvor wurden sowohl das Originalbild als auch abgeleitete Bilder zwischengespeichert. Ein zweistufiger Prozess war erforderlich, um den Cache ungültig zu machen. In der neusten Version der intelligenten Bildbearbeitung werden nur die Ableitungen zwischengespeichert, was einen einstufigen Cache-Invalidierungsprozess ermöglicht.
* Kunden, die benutzerdefinierte Kopfzeilen in ihrem Regelsatz verwenden, profitieren von der neuesten intelligenten Bildbearbeitung, da diese Kopfzeilen im Gegensatz zur vorherigen Version der intelligenten Bildbearbeitung nicht blockiert werden. Beispielsweise &quot;Timing Allow Origin&quot;, &quot;X-Robot&quot;, wie in [Hinzufügen eines benutzerdefinierten Header-Werts zu Bildantworten|Dynamic Media Classic](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html) empfohlen.

## Ist intelligente Bildbearbeitung mit irgendwelchen Lizenzierungskosten verbunden? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nein. Die intelligente Bildbearbeitung ist in Ihrer bestehenden Lizenz von Dynamic Media Classic oder Adobe Experience Manager - Dynamic Media (On-Premise, AMS und Adobe Experience Manager as a Cloud Service) enthalten.

>[!NOTE]
>
>Die intelligente Bildbearbeitung ist für Dynamic Media - Hybrid-Kunden nicht verfügbar.

## Wie funktioniert die intelligente Bildbearbeitung? {#how-does-smart-imaging-work}

Wenn ein Bild von einem Verbraucher angefordert wird, prüft die intelligente Bildbearbeitung die Benutzereigenschaften und konvertiert es je nach verwendetem Browser in das entsprechende Bildformat. Diese Formatkonvertierungen werden so durchgeführt, dass die visuelle Wiedergabetreue nicht beeinträchtigt wird. Die intelligente Bildbearbeitung konvertiert Bilder basierend auf den Browser-Funktionen auf folgende Weise automatisch in verschiedene Formate.

<!--   * Safari 14.0 +
    * Safari 14 only with iOS 14.0 and above and macOS BigSur and above -->

* Automatische Konvertierung in WebP für die folgenden Browser:
   * Chrome
   * Firefox
   * Microsoft® Edge
   * Safari (iOS, macOS, iPadOS), bereitgestellte Browser- und Betriebssystemversionen unterstützen WebP
   * Android™
   * Opera
* Unterstützung älterer Browser:

   | Browser | Browser/OS-Version | Format |
   | --- | --- | --- |
   | Safari | Früher als iOS/iPad 14.0 oder macOS BigSur | JPEG2000 |
   | Edge | früher als 18 | JPEGXR |
   | Internet Explorer | 9+ | JPEGXR |
* Bereitstellung des ursprünglich angeforderten Bildformats für Browser, die diese Formate nicht unterstützen.

Wenn die Originalbildgröße kleiner ist als die von der intelligente Bildbearbeitung erzeugte, wird das Originalbild bereitgestellt.

## Welche Bildformate werden unterstützt?  {#what-image-formats-are-supported}

Die folgenden Bildformate werden für die intelligente Bildbearbeitung unterstützt:

* JPEG
* PNG

<!-- CQDOC-15846 For any other format mentioned in a URL, you should explicity turn off Smart Imaging.  Append modifier `bfc=off` to the URL for file formats other than JPEG and PNG. You can accomplish this by using either one of the following methods:

* Use a ruleset if the `fmt` modifier is mentioned in the URL. 
* Append in URL modifiers field of the presets concerned.

Adobe is working on a permanent fix that does not require you to append `bfc=off` for `fmt !=JPEG` or `fmt !=PNG`. This topic will be updated after the fix is delivered. -->

## Wie funktioniert die intelligente Bildbearbeitung mit meinen vorhandenen, bereits verwendeten Bildvorgaben? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Die intelligente Bildbearbeitung funktioniert mit Ihren vorhandenen &quot;Bildvorgaben&quot;und beachtet alle Bildeinstellungen mit Ausnahme der Qualität (`qlt`) und des Formats (`fmt`), wenn das angeforderte Dateiformat JPEG oder PNG ist. Bei der Formatkonvertierung bleibt die Wiedergabetreue gemäß den von Ihnen für die Bildvorgabe gewählten Einstellungen vollständig erhalten – jedoch bei kleinerer Dateigröße. Wenn die Originalbildgröße kleiner ist als die von der intelligente Bildbearbeitung erzeugte, wird das Originalbild bereitgestellt.

<!-- CQDOC-15846 In addition, if your image presets are used to return `fmt !=JPEG` or `fmt !=PNG`, be sure append `bfc=off` in the preset modifier field to return the requested file format. -->

## Muss ich für die intelligente Bildbearbeitung URLs bzw. Bildvorgaben ändern oder neuen Code auf meiner Site bereitstellen? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Intelligente Bildbearbeitung funktioniert nahtlos mit Ihren vorhandenen Bild-URLs und Bildvorgaben, wenn Sie die intelligente Bildbearbeitung für Ihre vorhandenen benutzerdefinierten Domain konfigurieren. Darüber hinaus müssen Sie bei der intelligenten Bildbearbeitung keinen Code auf Ihrer Website hinzufügen, um den Browser eines Benutzers zu erkennen. Es wird alles automatisch verarbeitet.

Falls Sie eine neue benutzerdefinierte Domain für die Verwendung der intelligenten Bildbearbeitung konfigurieren müssen, müssen die URLs aktualisiert werden, um diese benutzerdefinierte Domain widerzuspiegeln.

Informationen zu den Voraussetzungen für die intelligente Bildbearbeitung finden Sie unter [Bin ich zur Verwendung der intelligenten Bildbearbeitung berechtigt?](#am-i-eligible-to-use-smart-imaging)

<!-- No. Smart Imaging works seamlessly with your existing image URLs and image presets. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. All of this is handled automatically. -->

<!-- As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

## Funktioniert die intelligente Bildbearbeitung mit HTTPS? Und mit HTTP/2?  {#does-smart-imaging-working-with-https-how-about-http}

Die intelligente Bildbearbeitung funktioniert bei Bildern, die über HTTP, HTTPS oder HTTP/2 bereitgestellt wurden.

## Bin ich zur Verwendung der intelligenten Bildbearbeitung berechtigt? {#am-i-eligible-to-use-smart-imaging}

Um die intelligente Bildbearbeitung nutzen zu können, muss Dynamic Media Classic bzw. Dynamic Media im Experience Manager-Account Ihres Unternehmens die folgenden Voraussetzungen erfüllen:

* Sie verwenden das im Adobe-Bundle enthaltene CDN (Content Delivery Network) im Rahmen Ihrer Lizenz.
* Sie verwenden eine dedizierte Domain (z. B. `images.company.com` oder `mycompany.scene7.com`), keine generische Domain (z. B. `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com`).

Um Ihre Domänen zu finden, öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich dann bei Ihrem Unternehmenskonto bzw. Ihren Unternehmenskonten an.

Tippen Sie auf **[!UICONTROL Setup]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]** Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichter Servername]**. Wenn Sie derzeit eine generische Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen. Reichen Sie dazu ein technisches Support-Ticket ein.

Für Ihre erste benutzerdefinierte Domain fallen mit einer Dynamic Media-Lizenz keine zusätzlichen Kosten an.

## Wie kann ich die intelligente Bildbearbeitung für mein Konto aktivieren? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

Die intelligente Bildbearbeitung wird nicht automatisch aktiviert. Sie müssen eine entsprechende Anfrage stellen.

<!-- CQDOC-17915 HIDDEN FOR NOW AS OF MAY 28 2021 By default, Smart Imaging DPR and network optimization is disabled (turned off) for a Dynamic Media company account. If you want to enable (turn on) one or both of these out-of-the-box enhancements, create a support case as described below.

The release schedule for Smart Imaging DPR and network optimization is as follows:

| Region | Target date |
|---|---|
| North America | 24 May 2021 | 
| Europe, Middle East, Africa | 25 Jun 2021 | 
| Asia-Pacific | 19 Jul 2021 | -->

1. [Verwenden Sie die Admin Console, um einen Support-Fall zu erstellen.](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   1. Name des Hauptansprechpartners, E-Mail, Telefon.
   1. Geben Sie alle Domains an, für die intelligente Bildbearbeitung aktiviert werden soll (also `images.company.com` oder `mycompany.scene7.com`).

      Um Ihre Domänen zu finden, öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann bei Ihrem Unternehmenskonto bzw. Ihren Unternehmenskonten an.

      Klicken Sie auf **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**. 

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name.]**
   1. Vergewissern Sie sich, dass Sie CDN über Adobe und nicht verwaltet mit einer direkten Beziehung nutzen.
   1. Vergewissern Sie sich, dass Sie eine dedizierte Domain wie `images.company.com` oder `mycompany.scene7.com` und nicht eine generische Domain wie `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com` verwenden.

      Um Ihre Domänen zu finden, öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann bei Ihrem Unternehmenskonto bzw. Ihren Unternehmenskonten an.

      Klicken Sie auf **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**. 

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**. Wenn Sie derzeit eine generische Dynamic Media Classic-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.
   1. Geben Sie an, ob Sie auch die intelligente Bildbearbeitung über HTTP/2 benötigen.

1. Die Kundenunterstützung von Adobe fügt Sie basierend auf der Reihenfolge, in der die Anfragen gesendet wurden, zur Warteliste für Kunden mit intelligenter Bildbearbeitung hinzu.
1. Wenn Adobe für die Bearbeitung Ihrer Anfrage bereit ist, unterstützen Sie Support-Mitarbeiter bei der Koordination und Festlegung eines Zieldatums.
1. **Optional**: Sie haben die Möglichkeit, die intelligente Bildbearbeitung in der Staging-Phase zu testen, bevor Adobe die neue Funktion an die Produktion weitergibt.
1. Sie werden nach Abschluss durch den Kundendienst benachrichtigt.
1. Zur maximalen Leistungsverbesserung der intelligenten Bildbearbeitung empfiehlt Adobe eine Time-to-Live (TTL)-Einstellung von mindestens 24 Stunden. Die TTL-Einstellung definiert, wie lange Assets vom CDN-Dienst im Cache gespeichert werden. So ändern Sie diese Einstellung:

   1. Klicken Sie bei Verwendung von Dynamic Media Classic auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinstellungen > Image-Server]**. Stellen Sie den Wert **[!UICONTROL Standardeinstellung für Time-To-Live des Client-Cache]** auf mindestens 24 ein.
   1. Wenn Sie Dynamic Media verwenden, befolgen Sie [diese Anweisungen](config-dynamic.md). Stellen Sie den Wert **[!UICONTROL Gültigkeit]** auf mindestens 24 Stunden ein.

## Wann wird mein Konto voraussichtlich für die intelligente Bildbearbeitung aktiviert? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

Anfragen werden in der Reihenfolge verarbeitet, in der sie von der Kundenunterstützung empfangen werden, gemäß der Warteliste.

>[!NOTE]
>
>Die Vorlaufzeit kann lang sein, da die Aktivierung der intelligenten Bildbearbeitung mit der Adobe des Cache verbunden ist. Daher kann nur jeweils eine geringe Anzahl von Kunden gleichzeitig umgestellt werden.

## Welche Risiken bestehen bei der Umstellung auf die intelligente Bildbearbeitung? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Es besteht kein Risiko für eine Kunden-Web-Seite. Durch die Umstellung auf intelligente Bildbearbeitung wird der Cache im CDN jedoch gelöscht, da auf eine neue Konfiguration von Dynamic Media Classic oder Dynamic Media on Experience Manager umgestellt werden muss.

Zu Beginn der Übergangsphase werden die nicht im Cache gespeicherten Bilder direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wurde. Daher plant Adobe, einige Kundenübergänge gleichzeitig zu verarbeiten, damit beim Abrufen von Anforderungen aus der Quelle eine annehmbare Leistung erzielt wird. Für die meisten Kunden ist der Cache innerhalb von 1 bis 2 Tagen vollständig im CDN neu aufgebaut.

## Wie kann ich feststellen, ob die intelligente Bildbearbeitung erwartungsgemäß funktioniert? {#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Laden Sie nach der Konfiguration Ihres Kontos mit intelligenter Bildbearbeitung eine Dynamic Media Classic- oder Adobe Experience Manager - Dynamic Media-Bild-URL in den Browser.
1. Öffnen Sie den Chrome-Entwicklerbereich, indem Sie im Browser auf **[!UICONTROL Anzeigen]** > **[!UICONTROL Entwickler]** > **[!UICONTROL Entwickler-Tools]** klicken.  Selbstverständlich können Sie auch ein anderes Browser-Entwickler-Tool Ihrer Wahl verwenden.

1. Stellen Sie sicher, dass der Cache deaktiviert ist, wenn die Entwicklertools geöffnet sind.

   * Navigieren Sie unter Windows® zum Bereich mit den Entwickler-Tools und aktivieren Sie dann das Kontrollkästchen **[!UICONTROL Cache deaktivieren (während DevTools geöffnet ist)]** .
   * Wählen Sie unter macOS im Entwicklerbereich auf der Registerkarte **[!UICONTROL Netzwerk]** die Option **[!UICONTROL Cache]** deaktivieren.

1. Sie werden feststellen, dass der Content-Typ in das entsprechende Format umgewandelt wird. Der folgende Screenshot zeigt ein PNG-Bild, das in Chrome dynamisch ins WebP-Format konvertiert wird.
1. Wiederholen Sie diesen Test auf verschiedenen Browsern und bei unterschiedlichen Benutzerbedingungen.

>[!NOTE]
>
>Nicht alle Bilder werden konvertiert. Die intelligente Bildbearbeitung entscheidet, ob die Konvertierung die Leistung verbessern kann. In einigen Fällen, in denen kein Leistungsgewinn erwartet wird oder das Format nicht JPEG oder PNG ist, wird das Bild nicht konvertiert.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

## Kann die intelligente Bildbearbeitung für eine beliebige Anfrage deaktiviert werden? {#turning-off-smart-imaging}

Ja. Sie können die intelligente Bildbearbeitung deaktivieren, indem Sie den Modifikator `bfc=off` zur URL hinzufügen.

<!-- CQDOC-17915 HIDDEN FOR NOW AS OF MAY 28 2021 ## Can I request DPR and network optimization to be turned off at the company level? {#dpr-companylevel-turnoff}

Yes. To disable DPR and network optimization at your company, create a support case as described earlier in this topic. -->

## Welche „Optimierungen“ sind verfügbar? Gibt es Einstellungen oder Verhaltensweisen, die definiert werden können? (#tuning-settings)

Derzeit können Sie die intelligente Bildbearbeitung optional aktivieren oder deaktivieren. Es stehen keine weiteren Optimierungen zur Verfügung.

## Wenn die intelligente Bildbearbeitung die Qualitätseinstellungen verwaltet, müssen dann Mindest- und Höchstwerte festgelegt werden? Ist es zum Beispiel möglich, eine Qualität „nicht kleiner als 60“ und „nicht größer als 80“ festzulegen? (#minimum-maximum)

Diese Funktionalität gibt es in der aktuellen intelligenten Bildbearbeitung nicht.

## Manchmal wird ein JPEG-Bild anstelle eines WebP-Bildes an Chrome zurückgegeben. Warum kommt es zu dieser Änderung? (#jpeg-webp)

Die intelligente Bildbearbeitung entscheidet, ob die Konvertierung vorteilhaft ist. Das neue Bild wird nur dann zurückgegeben, wenn die Konvertierung zu einer kleineren Dateigröße mit vergleichbarer Qualität führt.

<!-- CQDOC-17915 HIDDEN FOR NOW AS OF MAY 28 2021 ## How does Smart Imaging DPR optimization work with Adobe Experience Manager Sites components and Dynamic Media viewers?

* Experience Manager Sites Core Components are configured by default for DPR optimization. To avoid oversized images owing to server-side Smart Imaging DPR optimization, `dpr=off` is always added to Experience Manager Sites Core Components Dynamic Media images.
* Given Dynamic Media Foundation Component is configured by default for DPR optimization, to avoid oversized images owing to server-side Smart Imaging DPR optimization, `dpr=off` is always added to Dynamic Media Foundation Component images. Even if customer deselects DPR optimization in DM Foundation Component, server-side Smart Imaging DPR does not kick in. In summary, in the DM Foundation Component, DPR optimization comes into effect based on DM Foundation Component level setting only.
* Any viewer side DPR optimization works in tandem with server-side Smart Imaging DPR optimization, and does not result in over-sized images. In other words, wherever DPR is handled by the viewer, such as the main view only in a zoom-enabled viewer, the server-side Smart Imaging DPR values are not triggered. Likewise, wherever viewer elements, such as swatches and thumbnails, do not have DPR handling, the server-side Smart Imaging DPR value is triggered.

See also [When working with images](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-images) and [When working with Smart Crop](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop). -->
