---
title: Intelligente Bildbearbeitung
description: 'Intelligente Bildbearbeitung nutzt die individuellen anzeigebezogenen Benutzermerkmale, um automatisch die richtigen Bilder für ein optimiertes individuelles Erlebnis zu präsentieren. Das Ergebnis: mehr Leistung und Interaktion.'
uuid: c11e52ba-8d64-4dc5-b30a-fc10c2b704e5
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: bf8c6bbd-847d-43d7-9ff4-7231bfd8d107
translation-type: tm+mt
source-git-commit: f786b35e77c6b862f7fc6e45d3d0af56a51e3e95
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 83%

---


# Intelligente Bildbearbeitung {#smart-imaging}

## Was ist die intelligente Bildbearbeitung? {#what-is-smart-imaging}

Die Technologie der intelligenten Bildbearbeitung nutzt die KI-Funktionen von Adobe Sensei und arbeitet mit vorhandenen „Bildvorgaben“ zusammen, um die Bereitstellung von Bildern zu verbessern, indem Bildformat, Größe und Qualität basierend auf den Funktionen des Clientbrowsers automatisch optimiert werden.

Die intelligente Bildbearbeitung profitiert auch von der zusätzlichen Leistungssteigerung durch die vollständige Integration mit dem erstklassigem Premium-CDN-Dienst von Adobe. Dieser Dienst ermittelt die optimale Internet-Route zwischen Servern, Netzwerken und Austauschpunkten mit niedrigster Latenz und/oder Paketverlustrate im Vergleich zur Standardroute im Internet.

Die folgenden Beispiele für Bild-Assets veranschaulichen die Optimierungen durch die intelligente Bildbearbeitung:

| Bild<br>(URL) | Miniaturansicht | Größe<br> (JPEG) | Größe (WebP)<br> (mit intelligenter Bildbearbeitung) | Reduzierung in % |
|---|---|---|---|---|
| [Bild 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture1](/help/assets/assets-dm/picture1.png) | 73,75 KB | 45,92 KB | 38 % |
| [Bild 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 191 KB | 70,66 KB | 63 % |
| [Bild 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 96,64 KB | 39,44 KB | 59 % |
| [Bild 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 315,80 KB | 178,19 KB | 44 % |
|  |  |  |  | Durchschnitt = 51 % |

Ähnlich wie oben führte Adobe auch einen Test mit 7009 URLs von Live-Kundenseiten durch und konnte aufgrund der intelligenten Bildbearbeitungsfunktion eine durchschnittliche Dateigrößenoptimierung von 38 % für JPEG und von 31 % für PNG mit WebP-Format erzielen.

## Was sind die Hauptvorteile der intelligenten Bildbearbeitung? {#what-are-the-key-benefits-of-smart-imaging}

Da Bilder einen Großteil der Seitenladezeit ausmachen, kann die Leistungssteigerung einen enormen Einfluss auf geschäftsbezogene KPIs wie höhere Konversionsraten, auf der Site verbrachte Zeit und niedrigere Website-Absprungraten haben.

Verbesserungen der neuesten Version der intelligenten Bildbearbeitung:

* Stellt optimierte Inhalte sofort (zur Laufzeit) bereit.
* Verwendet Adobe Sensei-Technologie zur Konvertierung gemäß der in der Bildanforderung angegebenen Qualität (qlt).
* Die intelligente Bildbearbeitung kann mithilfe des URL-Parameters „bfc“ deaktiviert werden.
* TTL (Time To Live)-unabhängig. Zuvor war eine TTL von mindestens 12 Stunden erforderlich, damit die intelligente Bildbearbeitung funktioniert.
* Zuvor wurden sowohl das Originalbild als auch abgeleitete Bilder zwischengespeichert. Ein zweistufiger Prozess war erforderlich, um den Cache ungültig zu machen. In der neusten Version der intelligenten Bildbearbeitung werden nur die Ableitungen zwischengespeichert, was einen einstufigen Cache-Invalidierungsprozess ermöglicht.
* Kunden, die in ihrem Regelsatz benutzerdefinierte Kopfzeilen verwenden (z. B. „Timing Allow Origin“, „X-Robot“, wie in [Einen benutzerdefinierten Kopfzeilenwert zu Bildantworten hinzufügen|Dynamic Media Classic](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html) vorgeschlagen), profitieren von der neuesten Version der intelligenten Bildbearbeitung, da diese Kopfzeilen im Gegensatz zur vorherigen Version nicht mehr blockiert.

## Ist intelligente Bildbearbeitung mit irgendwelchen Lizenzierungskosten verbunden? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nein. Smart Imaging ist in Ihrer bestehenden Lizenz von Dynamic Media Classic oder Adobe Experience Manager - Dynamic Media (On Prem, AMS und AEM als Cloud Service) enthalten.

>[!NOTE]
>
>Die intelligente Bildbearbeitung ist nicht für Dynamic Media – Hybrid-Kunden verfügbar.


## Wie funktioniert die intelligente Bildbearbeitung? {#how-does-smart-imaging-work}

Wenn ein Bild von einem Verbraucher angefordert wird, prüfen wir die Benutzereigenschaften und konvertieren es in das entsprechende Bildformat, je nach verwendetem Browser. Diese Formatkonvertierungen werden so durchgeführt, dass die visuelle Genauigkeit nicht beeinträchtigt wird. Mit der intelligenten Bildbearbeitung werden Bilder wie folgt je nach Browserfunktionalität automatisch in andere Formate konvertiert.

* Konvertieren Sie folgende Browser automatisch in WebP:
   * Chrome
   * Firefox
   * Microsoft Edge
   * Safari 14.0 +
      * Safari 14 nur mit iOS 14.0 und höher und macOS BigSur und höher
   * Android
   * Opera
* Unterstützung älterer Browser für Folgendes:

   | Browser | Browser/OS-Version | Format |
   | --- | --- | --- |
   | Safari | iOS 14.0 oder früher | JPEG2000 |
   | Edge | 18 oder früher | JPEGXR |
   | Internet Explorer | 9+ | JPEGXR |
* Bereitstellung des ursprünglich angeforderten Bildformats für Browser, die diese Formate nicht unterstützen.

Wenn die Originalbildgröße kleiner ist als die von der intelligente Bildbearbeitung erzeugte, wird das Originalbild bereitgestellt.

## Welche Bildformate werden unterstützt?        {#what-image-formats-are-supported}

Die folgenden Bildformate werden für die intelligente Bildbearbeitung unterstützt:
* JPEG
* PNG

<!-- For any other format mentioned in a URL, you should explicity turn off Smart Imaging.  Append modifier `bfc=off` to the URL for file formats other than JPEG and PNG. You can accomplish this by using either one of the following methods:

* Use a ruleset if the `fmt` modifier is mentioned in the URL. 
* Append in URL modifiers field of the presets concerned.

Adobe is working on a permanent fix that does not require you to append `bfc=off` for `fmt !=JPEG` or `fmt !=PNG`. This topic will be updated after the fix is delivered. -->

## Wie funktioniert die intelligente Bildbearbeitung bei vorhandenen und bereits verwendeten Bildvorgaben? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Die intelligente Bildbearbeitung funktioniert mit Ihren vorhandenen „Bildvorgaben“ und beachtet alle Bildeinstellungen mit Ausnahme von Qualität (qlt) und Format (fmt), wenn das angeforderte Dateiformat JPEG oder PNG ist. Bei der Formatkonvertierung bleibt die Wiedergabetreue vollständig erhalten, und zwar gemäß den von Ihnen für die Bildvorgabe gewählten Einstellungen – jedoch bei kleinerer Dateigröße. Wenn die Originalbildgröße kleiner ist als die von der intelligente Bildbearbeitung erzeugte, wird das Originalbild bereitgestellt.

<!-- In addition, if your image presets are used to return `fmt !=JPEG` or `fmt !=PNG`, be sure append `bfc=off` in the preset modifier field to return the requested file format. -->

## Muss ich für die intelligente Bildbearbeitung URLs und Bildvorgaben ändern oder neuen Code auf Websites bereitstellen? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Smart Imaging funktioniert nahtlos mit Ihren vorhandenen Bild-URLs und Bildvorgaben, wenn Sie Smart Imaging in Ihrer vorhandenen benutzerdefinierten Domäne konfigurieren. Darüber hinaus müssen Sie bei der intelligenten Bildbearbeitung keinen Code auf Ihrer Website hinzufügen, um den Browser eines Benutzers zu erkennen. All dies wird automatisch erledigt.

Falls Sie eine neue benutzerdefinierte Domäne für die Verwendung von Smart Imaging konfigurieren müssen, müssen die URLs aktualisiert werden, um diese benutzerdefinierte Domäne widerzuspiegeln.

Siehe auch [Bin ich zur Verwendung der intelligenten Bildbearbeitung berechtigt?](#am-i-eligible-to-use-smart-imaging), um die Voraussetzungen für die intelligente Bildbearbeitung zu verstehen.

<!-- No. Smart Imaging works seamlessly with your existing image URLs and image presets. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. All of this is handled automatically. -->

<!-- As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

## Funktioniert die intelligente Bildbearbeitung mit HTTPS? Und mit HTTP/2?         {#does-smart-imaging-working-with-https-how-about-http}

Die intelligente Bildbearbeitung funktioniert bei Bildern, die über HTTP, HTTPS oder HTTP/2 bereitgestellt wurden.

## Bin ich zur Verwendung der intelligenten Bildbearbeitung berechtigt? {#am-i-eligible-to-use-smart-imaging}

Um die intelligente Bildbearbeitung nutzen zu können, muss das Dynamic Media Classic- bzw. Dynamic Media-Konto Ihres Unternehmens die folgenden Voraussetzungen erfüllen:

* Sie verwenden das im Adobe-Bundle enthaltene CDN (Content Delivery Network) im Rahmen Ihrer Lizenz.
* Sie verwenden eine dedizierte Domäne (z. B. `images.company.com` oder `mycompany.scene7.com`), keine generische Domäne (z. B. `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com`).

Um Ihre Domänen zu finden, öffnen Sie die [Dynamic Media Classic Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann bei Ihrem Firmen-Konto oder Ihren Konten an.

Tippen Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen.]** Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name.]** Wenn Sie derzeit eine generische Domäne verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domäne beantragen. Reichen Sie dazu ein technisches Support-Ticket ein.

Für Ihre erste benutzerdefinierte Domäne fallen mit einer Dynamic Media-Lizenz keine zusätzlichen Kosten an.

## Wie kann ich die intelligente Bildbearbeitung für mein Konto aktivieren? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

Intelligente Bildbearbeitung wird nicht automatisch aktiviert; Sie müssen eine entsprechende Anfrage stellen.

1. [Verwenden Sie die Admin Console, um einen Supportfall zu erstellen.](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
1. Geben Sie im Supportfall die folgenden Informationen ein:

   1. Name des Hauptansprechpartners, E-Mail, Telefon.
   1. Geben Sie alle Domänen an, für die intelligente Bildbearbeitung aktiviert werden soll (also `images.company.com` oder `mycompany.scene7.com`).

      Um Ihre Domänen zu finden, öffnen Sie die [Dynamic Media Classic Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann bei Ihrem Firmen-Konto oder Ihren Konten an.

      Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen.]**

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name.]**
   1. Vergewissern Sie sich, dass Sie CDN über Adobe und nicht verwaltet mit einer direkten Beziehung nutzen.
   1. Vergewissern Sie sich, dass Sie eine dedizierte Domäne wie `images.company.com` oder `mycompany.scene7.com` und nicht eine generische Domäne wie `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com` verwenden.

      Um Ihre Domänen zu finden, öffnen Sie die [Dynamic Media Classic Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann bei Ihrem Firmen-Konto oder Ihren Konten an.

      Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen.]**

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name.]** Wenn Sie derzeit eine generische Dynamic Media Classic-Domäne verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domäne beantragen.
   1. Geben Sie an, ob Sie auch auf eine Nutzung über HTTP/2 angewiesen sind.

1. Der technische Support nimmt Sie in die Kunden-Warteliste für die intelligente Bildbearbeitung auf. Dies geschieht in der Reihenfolge der eingehenden Anfragen.
1. Wenn Adobe Ihre Anfrage bearbeiten kann, setzt sich der Support mit Ihnen zwecks Koordinierung und Vereinbarung eines Zieldatums in Verbindung. 
1. **Optional**: Sie haben die Möglichkeit, die intelligente Bildbearbeitung in der Staging-Phase zu testen, bevor Adobe die neue Funktion auf das Produktionssystem überträgt.
1. Sie werden nach Abschluss durch den Support benachrichtigt. 
1. Zur maximalen Leistungsverbesserung der intelligenten Bildbearbeitung empfiehlt Adobe eine Time-to-Live (TTL)-Einstellung von mindestens 24 Stunden. Die TTL-Einstellung definiert, wie lange Assets vom CDN-Dienst im Cache gespeichert werden. So ändern Sie diese Einstellung:

   1. Klicken Sie bei Verwendung von Dynamic Media Classic auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinstellungen > Image-Server.]** Stellen Sie den Wert **[!UICONTROL Standardeinstellung für Time-To-Live des Client-Cache]** auf mindestens 24 ein.
   1. Wenn Sie Dynamic Media verwenden, befolgen Sie [diese Anweisungen](config-dynamic.md). Stellen Sie den Wert **[!UICONTROL Gültigkeit]** auf mindestens 24 Stunden ein.

## Wann wird mein Konto voraussichtlich für die intelligente Bildbearbeitung aktiviert? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

Die Anfragen werden in der Reihenfolge ihres Eingangs beim technischen Support gemäß Warteliste bearbeitet.

>[!NOTE]
Die Vorlaufzeit kann lang sein, da zum Aktivieren der Funktion „Intelligente Bildbearbeitung“ der Cache von Adobe gelöscht werden muss. Daher kann nur jeweils eine geringe Anzahl von Kunden gleichzeitig umgestellt werden. 

## Welche Risiken bestehen bei der Umstellung auf die intelligente Bildbearbeitung? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Es besteht kein Risiko für eine Kunden-Web-Seite. Sie sollten sich jedoch bewusst sein, dass beim Umstellen auf die intelligente Bildbearbeitung der CDN-Cache gelöscht wird, da auf eine neue Konfiguration von Dynamic Media Classic oder Dynamic Media in AEM umgestellt werden muss.

Zu Beginn der Übergangsphase treffen die nicht im Cache gespeicherten Bilder direkt auf die Adobe-Ursprungsserver, bis der Cache neu erstellt wurde.  Aus diesem Grund führt Adobe nur wenige Umstellungen zugleich durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus unserer Quelle abgerufen werden. Bei den meisten Kunden ist der CDN-Cache innerhalb von 1 bis 2 Tagen vollständig neu aufgebaut.

## Wie kann ich feststellen, ob die intelligente Bildbearbeitung erwartungsgemäß funktioniert? {#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Laden Sie nach der Konfiguration Ihres Kontos mit Smart Imaging eine Dynamic Media Classic- oder Adobe Experience Manager - Dynamic Media-Bild-URL in den Browser.
1. Öffnen Sie den Chrome-Entwicklerbereich, indem Sie im Browser auf **[!UICONTROL Anzeigen > Entwickler > Entwickler-Tools]** klicken. Selbstverständlich können Sie auch ein anderes Browser-Entwickler-Tool Ihrer Wahl verwenden.

1. Stellen Sie sicher, dass der Cache deaktiviert ist, wenn die Entwickler-Tools geöffnet sind. 

   * Navigieren Sie unter Windows in den Bereich mit den Entwickler-Tools und aktivieren Sie dann das Kontrollkästchen **[!UICONTROL Cache deaktivieren]** (während DevTools geöffnet ist).
   * Navigieren Sie unter Mac im Entwicklerbereich zur Registerkarte **[!UICONTROL Netzwerk]** und wählen Sie die Option **[!UICONTROL Cache deaktivieren]** aus.

1. Sie werden feststellen, dass der Content-Typ in das entsprechende Format umgewandelt wird. Der folgende Screenshot zeigt ein PNG-Bild, das in Chrome dynamisch ins WebP-Format konvertiert wird.
1. Wiederholen Sie diesen Test auf verschiedenen Browsern und bei unterschiedlichen Benutzerbedingungen. 

>[!NOTE]
Nicht alle Bilder werden konvertiert.  Die intelligente Bildbearbeitung entscheidet, ob durch Konvertieren die Leistung gesteigert werden kann. In einigen Fällen, in denen kein Leistungsgewinn erwartet wird oder das Format nicht JPEG oder PNG ist, wird das Bild nicht konvertiert.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

## Kann die intelligente Bildbearbeitung für eine beliebige Anfrage deaktiviert werden? {#turning-off-smart-imaging}

Ja. Sie können die intelligente Bildbearbeitung deaktivieren, indem Sie den Modifikator `bfc=off` zur URL hinzufügen.

## Welche „Optimierungen“ sind verfügbar? Gibt es Einstellungen oder Verhaltensweisen, die definiert werden können? (#tuning-settings)

Derzeit können Sie die intelligente Bildbearbeitung optional aktivieren oder deaktivieren. Es stehen keine weiteren Optimierungen zur Verfügung.

## Wenn die intelligente Bildbearbeitung die Qualitätseinstellungen verwaltet, können wir dann Mindest- und Höchstwerte festlegen? Ist es zum Beispiel möglich, eine Qualität „nicht kleiner als 60“ und „nicht größer als 80“ festzulegen? (#minimum-maximum)

Diese Funktionalität gibt es in der aktuellen intelligenten Bildbearbeitung nicht.

## In einigen Fällen wird ein JPEG-Bild anstelle eines WebP-Bildes an Chrome zurückgegeben. Was ist der Grund dafür? (#jpeg-webp)

Die intelligente Bildbearbeitung entscheidet, ob die Konvertierung vorteilhaft ist. Das neue Bild wird nur dann zurückgegeben, wenn die Konvertierung zu einer kleineren Dateigröße mit vergleichbarer Qualität führt.
