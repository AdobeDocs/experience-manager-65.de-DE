---
title: Intelligente Bildbearbeitung
description: Die intelligente Bildbearbeitung wendet die individuellen Anzeigeeigenschaften eines jeden Benutzers an, um automatisch die richtigen Bilder bereitzustellen, die für sein Erlebnis optimiert sind, was zu einer besseren Leistung und Interaktion führt.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: bf8c6bbd-847d-43d7-9ff4-7231bfd8d107
feature: Asset Management,Renditions
role: User, Admin
exl-id: e427d4ee-d5c8-421b-9739-f3cf2de36e41
source-git-commit: bb42b5990993b0f8cea95cf1f6c033aed2713c1c
workflow-type: tm+mt
source-wordcount: '3519'
ht-degree: 46%

---

# Intelligente Bildbearbeitung {#smart-imaging}

## Was ist die intelligente Bildbearbeitung? {#what-is-smart-imaging}

Die intelligente Bildbearbeitung wendet KI-Funktionen von Adobe Sensei an und arbeitet mit vorhandenen „Bildvorgaben“. Sie optimiert auf Grundlage der Browserfunktionen automatisch das Format, die Größe und die Qualität eines Bildes und stellt so hochwertige Bilder bereit.

Und jetzt erhalten Sie eine bessere Google Core Web Vital-Bewertung für LCP (LCP) (Größter Inhaltsbereitschaft) mit verbesserter intelligenten Bildbearbeitung, die jetzt sowohl AVIF- als auch WebP-Unterstützung bietet.

>[!IMPORTANT]
>
>Für die intelligente Bildbearbeitung müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN (Content Delivery Network) verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

Die intelligente Bildbearbeitung profitiert von der zusätzlichen Leistungssteigerung durch die vollständige Integration in den erstklassigen Premium-CDN-Dienst (Content Delivery Network) von Adobe. Dieser Service ermittelt die optimale Internetroute zwischen Servern, Netzwerken und Austauschpunkten. Er findet die Route mit der niedrigsten Latenz und der niedrigsten Paketverlustrate, anstatt die Standardroute im Internet zu verwenden.

Die folgenden Beispiele für Bild-Assets veranschaulichen die Optimierungen durch die intelligente Bildbearbeitung:

| Bild(URL) | Miniaturansicht | Größe (JPEG) | Größe (WebP) mit intelligenter Bildbearbeitung | Größe (AVIF) mit intelligenter Bildbearbeitung | prozentuale Reduktion mit WebP | Reduktion um % mit AVIF |
|---|---|---|---|---|---|---|
| [Bild 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture1](/help/assets/assets-dm/picture1.png) | 145 KB | 106 KB | 90.2 KB | 26,89% | 37,79% |
| [Bild 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 412 KB | 346 KB | 113 KB | 16,01 % | 72,57% |
| [Bild 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 221 KB | 189 KB | 87.1 KB | 14,47% | 60,58% |
| [Bild 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 594 KB | 545 KB | 286 KB | 8,25 % | 51,85% |

Ähnlich wie oben führte Adobe auch einen Test mit einem größeren Stichprobensatz durch. Das Format AVIF ermöglichte eine 20%ige zusätzliche Größenreduzierung gegenüber WebP, was eine 27%ige Reduktion gegenüber JPEG ermöglichte. Alles in gleicher visueller Qualität. Insgesamt ermöglicht AVIF im Vergleich zu JPEG eine Reduzierung der durchschnittlichen Größe um bis zu 41 %.

Vergleichen Sie WebP und AVIF mit PNG, Sie können eine Reduzierung der Größe um 84 % mit WebP und 87 % mit AVIF feststellen. Da sowohl WebP- als auch AVIF-Formate Transparenz und mehrere Bildanimationen unterstützen, ist dies ein guter Ersatz für transparente PNG- und GIF-Dateien.

Siehe auch [Bildoptimierung mit Bildformaten der nächsten Generation (WebP und AVIF)](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4)

<!-- HIDDEN ON MAY 19, 2022 BASED ON CQDOC-19280 On the mobile web, the challenges are compounded by two factors:

* Large variety of devices with different form factors and high-resolution displays.
* Constrained network bandwidth.

In terms of images, the goal is to serve the best quality images as efficiently as possible. -->

## Was sind die Hauptvorteile der intelligenten Bildbearbeitung? {#what-are-the-key-benefits-of-smart-imaging}

Die intelligente Bildbearbeitung bietet eine bessere Leistung bei der Bildbereitstellung, indem die Größe der Bilddatei anhand des verwendeten Client-Browsers, der Geräteanzeige und der Netzwerkbedingungen automatisch optimiert wird. Da Bilder den Großteil der Ladezeit einer Seite ausmachen, kann jede Leistungsverbesserung erhebliche Auswirkungen auf geschäftsbezogene KPIs haben, z. B. höhere Konversionsraten, Besuchszeit auf einer Site und niedrigere Site-Absprungraten.

Die neuesten Hauptvorteile der neuesten intelligenten Bildbearbeitung sind:

* Unterstützt jetzt das AVIF-Format der nächsten Generation.
* PNG zu WebP und AVIF unterstützen jetzt verlustbehaftete Konvertierungen. Da PNG ein verlustfreies Format ist, waren frühere Bereitstellungen von WebP und AVIF verlustfrei.
* Browserformat-Konversion (`bfc`)
* Gerätepixelverhältnis (`dpr`)
* Netzwerkbandbreite (`network`)

### Über die Browserformatkonvertierung (bfc) {#bfc}

Aktivieren der Browser-Formatkonvertierung durch Anhängen `bfc=on` zur Bild-URL konvertiert JPEG und PNG automatisch in verlustbehaftetes AVIF, verlustbehaftetes WebP, verlustbehaftetes JPEGXR und verlustbehaftetes JPEG2000 für verschiedene Browser. Bei Browsern, die diese Formate nicht unterstützen, stellt die intelligente Bildbearbeitung weiterhin JPEG oder PNG bereit. Neben dem Format wird die Qualität des neuen Formats durch die intelligente Bildbearbeitung neu berechnet.

Die intelligente Bildbearbeitung kann auch durch Anhängen deaktiviert werden `bfc=off` zur URL des Bildes.

Siehe auch [bfc](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-bfc.html?lang=en) in der Dynamic Media Image Serving and Rendering API.

### Über die Optimierung der Gerätepixelrate (dpr) {#dpr}

Device Pixel Ratio (DPR) - auch als CSS-Pixelverhältnis bezeichnet - ist die Beziehung zwischen den physischen Pixeln und logischen Pixeln eines Geräts. Insbesondere mit dem Aufkommen von Retina-Bildschirmen nimmt die Pixelauflösung moderner Mobilgeräte stetig zu.

Durch Aktivierung der Optimierung des Gerätepixelverhältnisses wird das Bild in der nativen Bildschirmauflösung gerendert, wodurch es scharf erscheint.

Derzeit stammt die Display-Pixeldichte aus den CDN-Kopfzeilenwerten von Akamai.

| Zulässige Werte in der URL eines Bildes | Beschreibung |
|---|---|
| `dpr=off` | Deaktivieren Sie die DPR-Optimierung auf Ebene der einzelnen Bild-URLs. |
| `dpr=on,dprValue` | Überschreiben Sie den von der intelligenten Bildbearbeitung erkannten DPR-Wert mit einem benutzerdefinierten Wert (wie von einer beliebigen Client-seitigen Logik oder auf andere Weise erkannt). Der zulässige Wert für `dprValue` ist eine beliebige Zahl, die größer ist als 0. |

>[!NOTE]
>
>* Sie können `dpr=on,dprValue` auch dann verwenden, wenn die DPR-Einstellung auf Unternehmensebene deaktiviert ist.
>* Aufgrund der DPR-Optimierung wird die MaxPix-Breite immer erkannt, wenn das resultierende Bild größer ist als die Dynamic Media-Einstellung für MaxPix, indem das Seitenverhältnis des Bilds beibehalten wird.


| Angeforderte Bildgröße | Wert für Device Pixel Ratio (dpr) | Bereitgestellte Bildgröße |
|---|---|---|
| 816 x 500 | 1 | 816 x 500 |
| 816 x 500 | 2 | 1632 x 1000 |

Siehe auch [Arbeiten mit Bildern](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-images) und [Bei der Arbeit mit smartem Zuschneiden](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

### Über die Optimierung der Netzwerkbandbreite {#network}

Beim Aktivieren der Netzwerkbandbreite wird die Bildqualität automatisch an die tatsächliche Netzwerkbandbreite angepasst. Bei geringer Netzwerkbandbreite wird die Optimierung der DPR (Device Pixel Ratio) automatisch deaktiviert, auch wenn sie bereits aktiviert ist.

Falls gewünscht, kann Ihr Unternehmen die Optimierung der Netzwerkbandbreite auf individueller Bildebene deaktivieren, indem `network=off` an die URL des Bilds angehängt wird.

| Zulässiger Wert in der URL eines Bilds | Beschreibung |
|---|---|
| `network=off` | Deaktiviert die Netzwerkoptimierung auf Ebene der einzelnen Bild-URLs. |

Die Werte für das Gerätepixelverhältnis und die Netzwerkbandbreite basieren auf den erkannten Client-seitigen Werten des im Bundle enthaltene CDN. Diese Werte sind mitunter ungenau. Beispielsweise iPhone5 mit DPR=2 und iPhone12 mit `dpr=3`, beide zeigen `dpr=2`. Bei hochauflösenden Geräten wird jedoch das Senden von `dpr=2` ist besser als Senden `dpr=1`. Die beste Möglichkeit, diese Ungenauigkeit zu überwinden, besteht jedoch darin, die clientseitige DSGVO zu verwenden, um Ihnen 100 % genaue Werte zu geben. Und es funktioniert für jedes Gerät, ob es sich um Apple oder ein anderes Gerät handelt, das gestartet wurde. Siehe [Verwenden der intelligenten Bildbearbeitung mit dem clientseitigen Gerätepixelverhältnis](/help/assets/client-side-dpr.md).

### Zusätzliche wichtige Vorteile der intelligenten Bildbearbeitung

* Das Google SEO-Ranking für Web-Seiten mit der neuesten intelligenten Bildbearbeitung wurde verbessert.
* Stellt optimierte Inhalte sofort (zur Laufzeit) bereit.
* Verwendet Adobe Sensei-Technologie zur Konvertierung gemäß der in der Bildanfrage angegebenen Qualität (`qlt`).
* TTL (Time To Live)-unabhängig. Zuvor war eine TTL von mindestens 12 Stunden erforderlich, damit die intelligente Bildbearbeitung funktioniert.
* Zuvor wurden sowohl das Originalbild als auch abgeleitete Bilder zwischengespeichert. Ein zweistufiger Prozess war erforderlich, um den Cache ungültig zu machen. In der neusten Version der intelligenten Bildbearbeitung werden nur die Ableitungen zwischengespeichert, was einen einstufigen Cache-Invalidierungsprozess ermöglicht.
* Kunden, die benutzerdefinierte Kopfzeilen in ihrem Regelsatz verwenden, profitieren von der neuesten intelligenten Bildbearbeitung, da diese Kopfzeilen im Gegensatz zur vorherigen Version der intelligenten Bildbearbeitung nicht blockiert werden. Beispielsweise profitieren „Timing Allow Origin“ oder „X-Robot“, wie unter [Hinzufügen einer benutzerdefinierten Kopfzeile zu Bildantworten | Dynamic Media Classic](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html) vorgeschlagen, von der neuesten Version der intelligenten Bildbearbeitung.

## Ist die intelligente Bildbearbeitung mit Lizenzierungskosten verbunden? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nein. Sie sind berechtigt, die intelligente Bildbearbeitung mit Ihrer Lizenz zu nutzen. Dies gilt für Dynamic Media Classic oder Experience Manager Dynamic Media (On-Premise, AMS und Experience Manager as a Cloud Service).

>[!NOTE]
>
>Die intelligente Bildbearbeitung ist nicht für Dynamic Media-Hybrid-Kunden verfügbar.

## Wie funktioniert die intelligente Bildbearbeitung? {#how-does-smart-imaging-work}

Wenn ein Bild von einem Verbraucher angefordert wird, prüft die intelligente Bildbearbeitung die Benutzermerkmale und konvertiert es basierend auf dem verwendeten Browser in das gewünschte Bildformat. Diese Formatkonvertierungen werden so durchgeführt, dass die visuelle Wiedergabetreue nicht beeinträchtigt wird. Die intelligente Bildbearbeitung konvertiert Bilder basierend auf den Browser-Funktionen auf folgende Weise automatisch in verschiedene Formate.

* Automatische Konvertierung in AVIF, wenn der Browser das Format unterstützt
* Automatische Konvertierung in WebP, wenn die AVIF-Konvertierung nicht vorteilhaft war oder der Browser AVIF nicht unterstützt
* Automatische Konvertierung in JPEG2000, wenn Safari WebP nicht unterstützt
* Automatische Konvertierung in JPEGXR für IE 9+ oder wenn Edge WebP nicht unterstützt\
   | Bildformat | Unterstützte Browser | |—|—| | AVIF | [https://caniuse.com/avif](https://caniuse.com/avif) | | WebP | [https://caniuse.com/webp](https://caniuse.com/webp) | | JPEG 2000 | [https://caniuse.com/jpeg2000](https://caniuse.com/jpeg2000) | | JPEGXR | [https://caniuse.com/jpegxr](https://caniuse.com/jpegxr) |
* Bereitstellung des ursprünglich angeforderten Bildformats für Browser, die diese Formate nicht unterstützen.

Wenn die Originalbildgröße kleiner ist als die von der intelligente Bildbearbeitung erzeugte, wird das Originalbild bereitgestellt.

## Welche Bildformate werden unterstützt? {#what-image-formats-are-supported}

Die folgenden Bildformate werden für die intelligente Bildbearbeitung unterstützt:

* JPEG
* PNG

Für das JPEG-Bilddateiformat wird die Qualität des neuen Formats durch die intelligente Bildbearbeitung neu berechnet.

Für Bilddateiformate, die Transparenz unterstützen, wie PNG, können Sie die intelligente Bildbearbeitung so konfigurieren, dass verlustbehaftete AVIF- und WebP-Dateien bereitgestellt werden. Für die verlustreiche Formatkonvertierung verwendet die intelligente Bildbearbeitung die in der URL des Bildes erwähnte Qualität oder ansonsten die im Dynamic Media-Unternehmenskonto konfigurierte Qualität.

## Wie funktioniert die intelligente Bildbearbeitung mit meinen vorhandenen, bereits verwendeten Bildvorgaben? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Die intelligente Bildbearbeitung funktioniert mit vorhandenen Bildvorgaben und berücksichtigt alle Bildeinstellungen. Was sich ändert, ist das Bildformat, die Qualitätseinstellung oder beides. Bei der Formatkonvertierung bleibt die Wiedergabetreue gemäß den von Ihnen für die Bildvorgabe gewählten Einstellungen vollständig erhalten – jedoch bei kleinerer Dateigröße.

Angenommen, eine Bildvorgabe ist im JPEG-Format, in der Größe 500 x 500, in der Qualität = 85 und in der Unschärfemaske = 0,1,1,5 definiert. Wenn die intelligente Bildbearbeitung erkennt, dass sich ein Benutzer in einem Chrome-Browser befindet, wird das Bild in das WebP-Format mit einer Größe von 500 x 500 und einer Unschärfemaske von 0,1,1,5 in einer WebP-Qualität konvertiert, die einer JPEG-Qualität von 85 so nahe wie möglich entspricht. Der Platzbedarf dieser WebP-Konversion wird mit dem JPEG verglichen, und der kleinere von beiden wird zurückgegeben.

## Muss ich für die intelligente Bildbearbeitung URLs bzw. Bildvorgaben ändern oder neuen Code auf meiner Site bereitstellen? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Nein. Die intelligente Bildbearbeitung funktioniert nahtlos mit Ihren vorhandenen Bild-URLs und Bildvorgaben. Darüber hinaus erfordert die intelligente Bildbearbeitung nicht, dass Sie Code zu Ihrer Website hinzufügen, um den Browser eines Benutzers zu erkennen. All dies wird automatisch erledigt.

<!-- Smart Imaging works seamlessly with your existing image URLs and image presets if you configure Smart Imaging on your existing custom domain. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. It is all handled automatically.

In case you must configure a new custom domain to use Smart Imaging, the URLs must be updated to reflect this custom domain.

To understand pre-requisites for Smart Imaging, see [Am I eligible to use Smart Imaging?](#am-i-eligible-to-use-smart-imaging) -->

<!-- OLD As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

## Funktioniert die intelligente Bildbearbeitung mit HTTPS? Und mit HTTP/2? {#does-smart-imaging-working-with-https-how-about-http}

Die intelligente Bildbearbeitung funktioniert bei Bildern, die über HTTP, HTTPS oder HTTP/2 bereitgestellt wurden.

## Bin ich zur Verwendung der intelligenten Bildbearbeitung berechtigt? {#am-i-eligible-to-use-smart-imaging}

Um die intelligente Bildbearbeitung nutzen zu können, muss Dynamic Media Classic bzw. Dynamic Media im Experience Manager-Account Ihres Unternehmens die folgenden Voraussetzungen erfüllen:

* Sie verwenden das im Adobe-Bundle enthaltene CDN (Content Delivery Network) im Rahmen Ihrer Lizenz.
* Sie verwenden eine dedizierte Domain (z. B. `images.company.com` oder `mycompany.scene7.com`), keine generische Domain (z. B. `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com`).

Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Unternehmenskonto an, um Ihre Domains zu finden.

Wechseln Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**. Wenn Sie derzeit eine generische Domain verwenden, können Sie den Wechsel zu Ihrer eigenen benutzerdefinierten Domain anfordern. Stellen Sie diese Übergangsanfrage, wenn Sie einen Support-Fall einreichen.

Für Ihre erste anwenderdefinierte Domain fallen mit einer Dynamic Media-Lizenz keine zusätzlichen Kosten an.

## Wie kann ich die intelligente Bildbearbeitung für mein Konto aktivieren? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

Sie initiieren eine Anfrage zur Verwendung der intelligenten Bildbearbeitung. nicht automatisch aktiviert ist.

Erstellen Sie einen Support-Fall wie unten beschrieben. Stellen Sie in Ihrem Support-Fall sicher, dass Sie erwähnen, welche der folgenden Funktionen der intelligenten Bildbearbeitung (eine oder mehrere) für Ihr Konto aktiviert werden sollen:

* WebP
* AVIF
* DSGVO und Optimierung der Netzwerkbandbreite
* PNG in verlustbehaftetes AVIF oder verlustbehaftetes WebP

Wenn Sie die intelligente Bildbearbeitung bereits mit WebP aktiviert haben, aber andere neue Funktionen wie oben beschrieben wünschen, müssen Sie einen Support-Fall erstellen.

**So erstellen Sie einen Support-Fall, um die intelligente Bildbearbeitung in Ihrem Konto zu aktivieren:**

1. [Verwenden Sie die Admin Console, um mit der Erstellung eines neuen Support-Falles zu beginnen.](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   * Name des Hauptansprechpartners, E-Mail, Telefon.

   * Geben Sie an, welche der folgenden Funktionen der intelligenten Bildbearbeitung (eine oder mehrere) für Ihr Konto aktiviert werden sollen:
      * WebP
      * AVIF
      * DSGVO und Optimierung der Netzwerkbandbreite
      * PNG in verlustbehaftetes AVIF oder verlustbehaftetes WebP
   * Geben Sie alle Domains an, für die intelligente Bildbearbeitung aktiviert werden soll (also `images.company.com` oder `mycompany.scene7.com`).

      Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich bei Ihrem Unternehmenskonto an, um Ihre Domains zu finden.

      Wechseln Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**.

   * Vergewissern Sie sich, dass Sie CDN über Adobe und nicht verwaltet mit einer direkten Beziehung nutzen.

   * Vergewissern Sie sich, dass Sie eine dedizierte Domain wie `images.company.com` oder `mycompany.scene7.com` und nicht eine generische Domain wie `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com` verwenden.

      Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich bei Ihrem Unternehmenskonto an, um Ihre Domains zu finden.

      Wechseln Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**. Wenn Sie derzeit eine generische Dynamic Media Classic-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.

   * Geben Sie an, ob sie über HTTP/2 funktionieren soll.


1. Der Adobe-Support nimmt Sie in die Kunden-Warteliste für die intelligente Bildbearbeitung auf. Dies geschieht in der Reihenfolge der eingehenden Anfragen.
1. Wenn Adobe Ihre Anfrage bearbeiten kann, setzt sich der Support mit Ihnen zwecks Koordinierung und Vereinbarung eines Zieldatums in Verbindung.
1. **Optional**: Sie haben die Möglichkeit, die intelligente Bildbearbeitung in der Staging-Phase zu testen, bevor Adobe die neue Funktion an die Produktion weitergibt.
1. Nach Abschluss werden Sie durch den Support benachrichtigt.
1. Zur maximalen Leistungsverbesserung der intelligenten Bildbearbeitung empfiehlt Adobe eine Time-to-Live (TTL)-Einstellung von mindestens 24 Stunden. Die TTL-Einstellung definiert, wie lange Assets vom CDN-Service im Cache gespeichert werden. So ändern Sie diese Einstellung:

   1. Wechseln Sie bei Verwendung von Dynamic Media Classic zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Veröffentlichungseinstellungen]** > **[!UICONTROL Image-Server]**. Stellen Sie den Wert **[!UICONTROL Standardeinstellung für Time-To-Live des Client-Cache]** auf mindestens 24 ein.
   1. Wenn Sie Dynamic Media verwenden, befolgen Sie [diese Anweisungen](/help/assets/dm-publish-settings.md#common-thumbnail-attributes-tab). Stellen Sie den Wert **[!UICONTROL Gültigkeit]** auf mindestens 24 Stunden ein.

## Wann wird mein Konto voraussichtlich für die intelligente Bildbearbeitung aktiviert? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

Die Anfragen werden in der Reihenfolge ihres Eingangs beim Support gemäß Warteliste bearbeitet.

>[!NOTE]
>
>Die Vorlaufzeit kann lang sein, da zum Aktivieren der Funktion „Intelligente Bildbearbeitung“ der Cache von Adobe gelöscht werden muss. Daher kann nur jeweils eine geringe Anzahl von Kunden gleichzeitig umgestellt werden.

## Welche Risiken bestehen bei der Umstellung auf die intelligente Bildbearbeitung? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Es besteht kein Risiko für eine Kunden-Web-Seite. Die Umstellung auf die intelligente Bildbearbeitung löscht jedoch Ihren CDN-Cache. Dieser Vorgang umfasst die Umstellung auf eine neue Konfiguration von Dynamic Media Classic oder Dynamic Media in Experience Manager.

Zu Beginn der Übergangsphase werden die nicht im Cache gespeicherten Bilder direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wurde. Aus diesem Grund führt Adobe nur wenige Umstellungen gleichzeitig durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus der Quelle abgerufen werden. Bei den meisten Kunden ist der CDN-Cache innerhalb von 1 bis 2 Tagen vollständig neu aufgebaut.

## Wie kann ich feststellen, ob die intelligente Bildbearbeitung erwartungsgemäß funktioniert?{#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Laden Sie nach der Konfiguration Ihres Kontos mit der intelligenten Bildbearbeitung eine Dynamic Media-Bild-URL von Dynamic Media Classic oder Adobe Experience Manager in den Browser.
1. Öffnen Sie den Chrome-Entwicklerbereich, indem Sie im Browser zu **[!UICONTROL Anzeigen]** > **[!UICONTROL Entwickler]** > **[!UICONTROL Entwickler-Tools]** wechseln. Selbstverständlich können Sie auch ein anderes Browser-Entwickler-Tool Ihrer Wahl verwenden.

1. Stellen Sie sicher, dass der Cache deaktiviert ist, wenn die Entwicklertools geöffnet sind.

   * Gehen Sie unter Windows® im Bereich der Entwickler-Tools zu den Einstellungen und wählen Sie dann das Kontrollkästchen **[!UICONTROL Cache deaktivieren]** aus (während DevTools geöffnet ist).
   * Gehen Sie unter Mac im Entwicklerbereich zur Registerkarte **[!UICONTROL Netzwerk]** und wählen Sie die Option **[!UICONTROL Cache deaktivieren]** aus.

1. Sie werden feststellen, dass der Content-Typ in das entsprechende Format umgewandelt wird. Der folgende Screenshot zeigt ein PNG-Bild, das in Chrome dynamisch ins WebP-Format konvertiert wird. Wenn für Ihre Domäne AVIF aktiviert ist, wird AVIF auch im Inhaltstyp angezeigt.
1. Wiederholen Sie diesen Test auf verschiedenen Browsern und bei unterschiedlichen Benutzerbedingungen.

>[!NOTE]
>
>Nicht alle Bilder werden konvertiert. Die intelligente Bildbearbeitung entscheidet, ob die Konvertierung die Leistung verbessern kann. In einigen Fällen, in denen kein Leistungsgewinn erwartet wird oder das Format nicht JPEG oder PNG ist, wird das Bild nicht konvertiert.

![image2017-11-14_15398](/help/assets/assets/image2017-11-14_15398.png)

## Wie erkenne ich den Leistungsgewinn? Gibt es eine Möglichkeit, die Vorteile der intelligenten Bildbearbeitung zu erkennen? {#benefits}

Die intelligente Bildbearbeitungskopfzeile bestimmt die Vorteile der intelligenten Bildbearbeitung. Wenn die intelligente Bildbearbeitung aktiviert ist, können Sie nach der Anforderung eines Bildes unter der **[!UICONTROL Antwortheader]** -Überschrift, können Sie `-X-Adobe-Smart-Imaging` wie im folgenden hervorgehobenen Beispiel gezeigt:

![Intelligente Bildbearbeitung](/help/assets/assets-dm/smart-imaging-header2.png)

Dieser Header teilt Ihnen Folgendes mit:

* Die intelligente Bildbearbeitung funktioniert für das Unternehmen.
* Ein positiver Wert bedeutet, dass die Konvertierung erfolgreich war. In diesem Fall wird ein neues WebP-Bild zurückgegeben.
* Ein negativer Wert bedeutet, dass die Konvertierung nicht erfolgreich war. In diesem Fall wird das ursprünglich angeforderte Bild zurückgegeben (standardmäßig JPEG, falls nicht angegeben).
* Ein positiver Wert zeigt den Byte-Unterschied zwischen dem angeforderten Bild und dem neuen Bild an. Im obigen Beispiel werden die gespeicherten Bytes `75048` oder ca. 75 KB für ein Bild.
* Ein negativer Wert bedeutet, dass das angeforderte Bild kleiner als das neue Bild ist. Die negative Größendifferenz wird angezeigt, aber das bereitgestellte Bild ist nur das ursprünglich angeforderte Bild.

>[!NOTE]
>
>**X-Adobe-Smart-Imaging = -1 mit bereitgestelltem WebP**
>
>Wenn der Wert von `X-Adobe-Smart-Imaging` auf -1 gesetzt ist und WebP weiterhin bereitgestellt wird, bedeutet dies, dass die intelligente Bildbearbeitung funktioniert, die Größenvorteile jedoch aufgrund des alten Caches nicht berechnet wurden. Sie können `cache=update` (nur einmal) in der URL des Bildes, um dieses Problem zu beheben.
>Beispiel für die Verwendung des Modifikators:
>`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`
>Um den gesamten Cache ungültig zu machen, müssen Sie einen Support-Fall erstellen.

## Wie kann ich die AVIF-Optimierung in der intelligenten Bildbearbeitung deaktivieren?{#disable-avif}

Wenn Sie zur Bereitstellung von WebP zurückwechseln möchten, erstellen Sie einen Support-Fall für dasselbe. Wie üblich können Sie die intelligente Bildbearbeitung deaktivieren, indem Sie den Parameter hinzufügen `bfc=off` zur URL des Bildes. Sie können jedoch weder WebP noch AVIF im URL-Modifikator für die intelligente Bildbearbeitung auswählen. Diese Fähigkeit wird auf der Kontoebene Ihres Unternehmens beibehalten.

## Kann die intelligente Bildbearbeitung für eine beliebige Anfrage deaktiviert werden?{#turning-off-smart-imaging}

Ja. Sie können die intelligente Bildbearbeitung deaktivieren, indem Sie einen der folgenden Modifikatoren hinzufügen:

* `bfc=off` , um die Browserformatkonvertierung zu deaktivieren. Siehe auch [Browserformatkonvertierung](#bfc).
* `dpr=off` , um das Gerätepixelverhältnis zu deaktivieren. Siehe auch [Gerätepixelverhältnis](#dpr).
* `network=off` , um die Netzwerkbandbreite zu deaktivieren. Siehe auch [Netzwerkbandbreite](#network).

## Welche „Optimierungen“ sind verfügbar? Gibt es Einstellungen oder Verhaltensweisen, die definiert werden können? {#tuning-settings}

Die intelligente Bildbearbeitung bietet drei Optionen, die Sie aktivieren oder deaktivieren können.

* [Browserformatkonvertierung](#bfc)
* [Gerätepixelverhältnis](#dpr)
* [Netzwerkbandbreite](#network)

## Ich habe eine URL mit &quot;fmt=tif&quot;im Chrome-Webbrowser. Meine Anfrage schlägt jedoch mit einem ImageServer-Fehler fehl. Vorteile {#fmt-tif}

Dieser Fehler tritt nicht auf, wenn die intelligente Bildbearbeitung in Ihrem Konto nicht aktiviert ist. Die intelligente Bildbearbeitung funktioniert nur mit JPEG- oder PNG-Formaten.

Um diesen Fehler zu vermeiden, haben Sie folgende Möglichkeiten:

* JPEG oder PNG angeben oder
* Verwenden Sie nicht die `fmt` Modifikator überhaupt oder
* Verwenden Sie ein Browser-bevorzugtes Format, das von der intelligenten Bildbearbeitung definiert wird. Sie können beispielsweise WebP für den Chrome-Webbrowser verwenden.

## Ich möchte ein TIFF-Bild von der URL eines Bildes herunterladen. Wie mache ich das? {#download-tif}

Hinzufügen `fmt=tif` und `bfc=off` zum URL-Pfad des Bildes.

## Verwaltet die intelligente Bildbearbeitung nur das Bildformat oder verwaltet sie auch die Bildqualitätseinstellungen, um optimale Ergebnisse zu erzielen?

Die intelligente Bildbearbeitung verwendet sowohl Format als auch Qualität. Die übrigen Parameter bleiben unverändert, wenn sie in der URL des Bildes angefordert werden.

## Wenn die intelligente Bildbearbeitung die Qualitätseinstellungen verwaltet, kann ich dann Mindest- und Höchstwerte festlegen? Mit anderen Worten, eine Qualität, die nicht kleiner als 60 und nicht größer als 80 ist? {#quality-setting}

Derzeit gibt es keine solche Bereitstellung.

## Passt die intelligente Bildbearbeitung automatisch die Ausgabeeinstellung für die prozentuale Qualität an oder wird diese Einstellung manuell angepasst und gilt für alle Bilder? In welchem Bereich? {#percent-quality}

Die intelligente Bildbearbeitung passt den Qualitätsprozentsatz automatisch an. Dieser Qualitätsprozentsatz wird mithilfe eines maschinellen Lernalgorithmus ermittelt, der von Adobe entwickelt wurde. Dieser Prozentsatz ist nicht bereichsspezifisch.

## Welche Bildbereitstellungsbefehle werden bei der intelligenten Bildbearbeitung unterstützt oder ignoriert? {#support-ignore}

Die einzigen ignorierten Befehle werden `fmt` und `qlt`. Alle verbleibenden Befehle werden unterstützt.

## Werden nur JPEG-Bilder durch die intelligente Bildbearbeitung ersetzt? Was passiert, wenn ich ein WebP, PNG oder etwas Anderes anfrage? {#replace-request}

Diese Funktion funktioniert nur für JPEG und PNG.

## Warum wird ein JPEG-Bild manchmal an Chrome statt an WebP zurückgegeben? {#jpeg-returned}

Die intelligente Bildbearbeitung entscheidet, ob die Konvertierung vorteilhaft ist. Es wird nur das neue Bild der Konversion zurückgegeben, was vorteilhaft ist.

## Warum funktioniert die Funktion Device Pixel Ratio (dpr) bei Composite-Bildern nicht wie erwartet? {#composite-images}

Wenn ein zusammengesetztes Bild zu viele Ebenen umfasst, kann die dpr-Funktionalität bei Verwendung eines Positionsmodifikators beeinträchtigt sein. Dieses Problem ist bekannt und wird in künftigen Versionen der intelligenten Bildbearbeitung behoben. Wenn andere Funktionen der intelligenten Bildbearbeitung nicht wie erwartet funktionieren, können Sie einen Support-Fall erstellen, um das Problem zu melden.

## Warum wird PNG für die intelligente Bildbearbeitung weiterhin in verlustfreies WebP/AVIF konvertiert? {#convert-to-lossless}

Da PNG ein verlustfreies Format ist, wurden frühere WebP- und AVIF-Bereitstellungen verlustfrei durchgeführt, was zu einer höheren Größe als erwartet führte. Die intelligente Bildbearbeitung unterstützt jetzt verlustreiche Konvertierungen. Sie können den Modifikator verwenden `cache=update` (nur einmal) in einer Bildanforderung, um dieses Problem zu beheben. Ein Beispiel für die Verwendung dieses Modifikators:

`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`

Um den gesamten Cache ungültig zu machen, müssen Sie einen Support-Fall erstellen, der einen solchen Vorgang anfordert.

## Wie kann ich weiterhin PNG zur verlustfreien Konvertierung in die intelligente Bildbearbeitung verwenden? {#continue-using}

Die intelligente Bildbearbeitung unterstützt jetzt verlustreiche Konvertierungen basierend auf der Qualitätsstufe. Um weiterhin verlustfreie Konvertierungen zu verwenden, können Sie die 100-Qualität verwenden, die entweder über die Einstellung Ihres Unternehmens oder über die URL des Bildes mithilfe von `qlt=100` im Pfad.