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
source-git-commit: 582b7e9f36d3b9599058b4cfbe83897822b26d05

---


# Intelligente Bildbearbeitung {#smart-imaging}

## What is &quot;Smart Imaging&quot;? {#what-is-smart-imaging}

Die Smart-Imaging-Technologie nutzt die AI-Funktionen von Adobe Sensei und arbeitet mit vorhandenen &quot;Bildvorgaben&quot;zusammen, um die Performance von Image-Versänden zu verbessern, indem Bildformat, -größe und -qualität automatisch auf der Grundlage der Browserfunktionen des Kunden optimiert werden.

Smart Imaging profitiert auch von der zusätzlichen Leistungssteigerung durch die vollständige Integration mit dem erstklassigen CDN-Premium-Dienst von Adobe. Dieser Dienst findet die optimale Internetverbindung zwischen Servern, Netzwerken und Peering Points, die eine niedrigste Latenzzeit und/oder Paketverlustrate als die Standardverbindung im Internet haben.

Die folgenden Beispiele für Bild-Asset-Beispiele zeigen die hinzugefügte Optimierung der intelligenten Bildbearbeitung:

| Image<br>(URL) | Miniatur | Größe<br> (JPEG) | Größe (WebP)<br> (mit ***Smart Imaging***) | % Reduktion |
|---|---|---|---|---|
| [Bild 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![picture1](/help/assets/assets-dm/picture1.png) | 73.75 KB | 45.92 KB | 38% |
| [Bild 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 191 KB | 70.66 KB | 63% |
| [Bild 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 96.64 KB | 39.44 KB | 59% |
| [Bild 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 315.80 KB | 178.19 KB | 44% |
|  |  |  |  | Durchschnitt = 51 % |

Ähnlich wie oben führte Adobe auch einen Test mit 7009 URLs von Live-Kunden durch und konnte aufgrund der Smart Imaging-Funktion eine durchschnittlich 38%ige weitere Dateigrößenoptimierung für JPEG und eine weitere Optimierung der Dateigröße für PNG mit WebP-Format erzielen.

## What are the key benefits of the latest Smart Imaging? {#what-are-the-key-benefits-of-smart-imaging}

Da Bilder den Großteil der Ladezeit einer Seite ausmachen, kann sich die Leistungsverbesserung grundlegend auf Geschäfts-KPIs auswirken, wie z. B. höhere Konversionen, Besuchszeit pro Site und niedrigere Absprungrate.

Verbesserungen der neuesten Version von Smart Imaging:

* Dient zum sofortigen Bereitstellen optimierter Inhalte (zur Laufzeit).
* Verwendet die Adobe Sensei-Technologie zur Konvertierung entsprechend der Qualität (qlt), die in der Bildanforderung angegeben ist.
* Smart Imaging kann mit dem URL-Parameter &quot;bfc&quot;deaktiviert werden.
* TTL (Time To Live) unabhängig. Bisher war eine TTL von mindestens 12 Stunden erforderlich, damit Smart Imaging arbeiten konnte.
* Zuvor wurden sowohl die Original- als auch die abgeleiteten Bilder zwischengespeichert, und es war ein zweistufiger Prozess, den Cache zu ungültigen. Bei der neuesten Smart Imaging-Version werden nur die Derivate zwischengespeichert, sodass ein Prozess zur Ungültigmachung des Cache-Speichers in einem Schritt möglich ist.
* Kunden, die benutzerdefinierte Header in ihrem Regelsatz verwenden (z. B. &quot;Timing Allow Herkunft&quot;, &quot;X-Robot&quot;, wie in [Hinzufügen eines benutzerdefinierten Header-Werts zu Bildantworten vorgeschlagen|Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html)), profitieren von der neuesten Smart Imaging-Version, da diese Header im Gegensatz zur vorherigen Version von Smart Imaging nicht blockiert werden.

## Ist intelligente Bildbearbeitung mit irgendwelchen Lizenzierungskosten verbunden? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nein. Smart Imaging ist im Lieferumfang Ihrer vorhandenen Lizenz von Dynamic Media Classic (Scene7) oder AEM Dynamic Media (On Prem, AMS und AEM als Cloud-Dienst) enthalten.

>[!NOTE]
>
>Smart Imaging ist nicht für Dynamic Media - Hybrid-Kunden verfügbar.


## Wie funktioniert intelligente Bildbearbeitung? {#how-does-smart-imaging-work}

Smart Imaging verwendet Adobe Sensei, um Bilder je nach Browserfunktionalität automatisch in das optimale Format, die optimale Größe und Qualität zu konvertieren:

* Konvertieren Sie Browser wie Chrome, Firefox, Microsoft Edge, Android und Opera automatisch in WebP.
* Konvertieren Sie das Programm für Browser wie Safari automatisch in JPEG2000.
* Konvertieren Sie für Browser wie Internet Explorer 9+ automatisch in JPEG.
* Bei Browsern, die diese Formate nicht unterstützen, wird das ursprünglich angeforderte Bildformat bereitgestellt.

Wenn die ursprüngliche Bildgröße kleiner ist als die von Smart Imaging produzierte, wird das Originalbild bereitgestellt.

## What image formats are supported? {#what-image-formats-are-supported}

Die folgenden Bildformate werden für Smart Imaging unterstützt:
* JPEG
* PNG

Bei allen anderen in einer URL genannten Formaten sollten Sie die Smart-Imaging-Funktion explizit deaktivieren.  Hängen Sie Modifikator `bfc=off` an die URL für andere Dateiformate als JPEG und PNG an. Sie können dies mit einer der folgenden Methoden erreichen:

* Verwenden Sie einen Regelsatz, wenn der `fmt` Modifikator in der URL erwähnt wird.
* Hängen Sie im Feld URL-Modifikatoren der betreffenden Vorgaben an.

Adobe arbeitet an einer dauerhaften Fehlerbehebung, bei der Sie nicht `bfc=off` für `fmt !=JPEG` oder `fmt !=PNG`anhängen müssen. Dieses Thema wird aktualisiert, nachdem die Fehlerbehebung abgeschlossen wurde.


## How does Smart Imaging work with our existing image presets that are already in use? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Smart Imaging funktioniert mit Ihren vorhandenen &quot;Bildvorgaben&quot; und beachtet alle Bildeinstellungen mit Ausnahme von Qualität (qlt) und Format (fmt), wenn das angeforderte Dateiformat JPEG oder PNG ist. Bei der Formatkonvertierung wird die vollständige visuelle Genauigkeit, wie von Ihren Bildvorgabeeinstellungen definiert, bei einer kleineren Dateigröße beibehalten. Wenn die ursprüngliche Bildgröße kleiner ist als die von Smart Imaging produzierte, wird das Originalbild bereitgestellt.

Wenn Ihre Bildvorgaben zum Zurückgeben verwendet werden `fmt !=JPEG` oder `fmt !=PNG`müssen Sie sicherstellen, dass Sie `bfc=off` im Feld &quot;Vorgabe-Modifikator&quot;das angeforderte Dateiformat zurückgeben.

## Will I have to change any URLs, image presets, or deploy any new code on my site for Smart Imaging? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Nein. Smart Imaging funktioniert nahtlos mit Ihren vorhandenen Bild-URLs und Bildvorgaben. Für Smart Imaging müssen Sie außerdem keinen Code auf Ihrer Website hinzufügen, um den Browser eines Benutzers zu erkennen. All dies wird automatisch verarbeitet.

Wie bereits erwähnt, unterstützt Smart Imaging nur JPEG- und PNG-Bildformate. Bei anderen Formaten müssen Sie den Modifikator an die `bfc=off` URL anhängen, wie oben beschrieben.

Also, see [Am I eligible to use Smart Imaging?](#am-i-eligible-to-use-smart-imaging) um die Voraussetzungen für Smart Imaging zu verstehen.

## Funktioniert Smart Mmaging mit HTTPS? How about HTTP/2? {#does-smart-imaging-working-with-https-how-about-http}

Smart Imaging funktioniert mit Bildern, die über HTTP oder HTTPS bereitgestellt werden. Darüber hinaus funktioniert es auch über HTTP/2.

## Bin ich zur Verwendung von intelligenter Bildbearbeitung berechtigt? {#am-i-eligible-to-use-smart-imaging}

Um Smart Imaging verwenden zu können, müssen die Dynamic Media Classic- oder Dynamic Media-Daten Ihrer Firma für AEM die folgenden Anforderungen erfüllen:

* Verwenden Sie das Adobe-gebündelte CDN (Content Versand Network) als Teil Ihrer Lizenz.
* Verwenden Sie eine dedizierte Domäne (z. B. `images.company.com` oder `mycompany.scene7.com`), keine generische Domäne (z. B. `s7d1.scene7.com`, `s7d2.scene7.com`oder `s7d13.scene7.com`).

 Um Ihre Domänen zu suchen, melden Sie sich bei dem Konto bzw. den Konten Ihres Unternehmens an. 

Tap **[!UICONTROL Setup > Application Setup > General Settings]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungsservername]**.  Wenn Sie derzeit eine generische Domäne verwenden, können Sie beim Senden eines Tickets für den technischen Support beantragen, dass Sie im Rahmen dieser Transition zu Ihrer eigenen benutzerdefinierten Domäne wechseln.

Ihre erste benutzerdefinierte Domäne ist mit einer Lizenz für dynamische Medien kostenfrei.

## What is the process for enabling Smart Imaging for my account? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

Intelligente Bildbearbeitung wird nicht automatisch aktiviert; Sie müssen eine entsprechende Anfrage stellen.

1. Initiate a Technical Support request (email: `s7support@adobe.com`).
1. In der Anfrage geben Sie folgende Informationen an:

   1. Name des Hauptansprechpartners, E-Mail, Telefon.
   1. All domains to be enabled for smart imaging (that is, `images.company.com` or `mycompany.scene7.com`).

       Um Ihre Domänen zu suchen, melden Sie sich bei dem Konto bzw. den Konten Ihres Unternehmens an. 

      Klicken Sie auf **[!UICONTROL Setup > Anwendungssetup > Allgemeine Einstellungen]**.

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungsservername]**.  
   1. Vergewissern Sie sich, dass Sie CDN über Adobe und nicht verwaltet mit einer direkten Beziehung nutzen. 
   1. Vergewissern Sie sich, dass Sie eine dedizierte Domäne wie `images.company.com` oder `mycompany.scene7.com`verwenden und keine generische Domäne wie `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

       Um Ihre Domänen zu suchen, melden Sie sich bei dem Konto bzw. den Konten Ihres Unternehmens an. 

      Klicken Sie auf **[!UICONTROL Setup > Anwendungssetup > Allgemeine Einstellungen]**.

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungsservername]**.  Wenn Sie derzeit eine allgemeine Dynamic Media Classic-Domäne verwenden, können Sie im Rahmen dieser Transition den Übergang zu Ihrer eigenen benutzerdefinierten Domäne anfordern.
   1. Geben Sie an, ob dies auch über HTTP/2 funktioniert.

1. Der technische Support fügt Sie je nach der Reihenfolge, in der Anfragen eingereicht wurden, zur Smart Imaging-Liste Wait hinzu.
1. Wenn Adobe Ihre Anfrage bearbeiten kann, setzt sich der Support mit Ihnen zwecks Koordinierung und Vereinbarung eines Zieldatums in Verbindung. 
1. **Optional**: Sie haben die Möglichkeit, intelligente Bildbearbeitung in Staging zu testen, bevor Adobe die neue Funktion in die Produktion einbringt.
1. Bei Abschluss werden Sie vom Support benachrichtigt. 
1. Zur Optimierung der Leistung von Smart Imaging empfiehlt Adobe die Einstellung der &quot;Time To Live&quot;(TTL) auf 24 Stunden oder länger. Die TTL definiert, wie lange Assets vom CDN zwischengespeichert werden. So ändern Sie diese Einstellung: 

   1. If you use Dynamic Media Classic, click **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**. Stellen Sie den Wert **[!UICONTROL Standardeinstellung für Time-To-Live des Client-Cache]** auf mindestens 24 ein.
   1. Wenn Sie dynamische Medien verwenden, befolgen Sie [diese Anweisungen](config-dynamic.md). Set the **[!UICONTROL Expiration]** value 24 hours or longer.

## When can I expect my account to be enabled with Smart Imaging? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

Die Anfragen werden in der Reihenfolge ihres Eingangs beim technischen Support gemäß Warteliste bearbeitet. 

>[!NOTE]
Es kann eine lange Vorlaufzeit geben, da bei der Aktivierung von Smart Imaging Adobe den Cache leeren muss. Daher kann nur jeweils eine geringe Anzahl von Kunden gleichzeitig umgestellt werden. 

## What are the risks with switching over to use Smart Imaging? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Eine Kundenwebseite ist nicht gefährdet. Sie sollten sich jedoch bewusst sein, dass die Transition zu Smart Imaging Ihren Cache im CDN löscht, da sie den Übergang zu einer neuen Konfiguration von Dynamic Media Classic oder Dynamic Media auf AEM beinhaltet.

Zu Beginn der Übergangsphase treffen die nicht im Cache gespeicherten Bilder direkt auf die Adobe-Ursprungsserver, bis der Cache neu erstellt wurde.  Aus diesem Grund führt Adobe nur wenige Umstellungen zugleich durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus unserer Quelle abgerufen werden. Bei den meisten Kunden ist der CDN-Cache innerhalb von 1 bis 2 Tagen vollständig neu aufgebaut.

## Wie kann ich feststellen, ob die intelligente Bildbearbeitung erwartungsgemäß funktioniert?  {#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Laden Sie nach der Konfiguration Ihres Kontos mit der intelligenten Bildbearbeitung eine URL für das Bild für dynamische Medien (Scene7)/Dynamische Medien in den Browser.
1. Öffnen Sie den Chrome-Entwicklerbereich, indem Sie im Browser auf **[!UICONTROL Anzeigen > Entwickler > Entwickler-Tools]** klicken.  Oder wählen Sie ein beliebiges Browser-Entwicklerwerkzeug Ihrer Wahl.

1. Stellen Sie sicher, dass der Cache deaktiviert ist, wenn die Entwickler-Tools geöffnet sind. 

   * On Windows – navigate to settings in the developer tool pane, then select **[!UICONTROL Disable cache (while devtools is open)]** checkbox.
   * On Mac – in the developer pane, under the **[!UICONTROL Network]** tab, select **[!UICONTROL disable cache]** .

1. Sie werden feststellen, dass der Inhaltstyp in das entsprechende Format umgewandelt wird.  Der folgende Screenshot zeigt, wie ein PNG-Bild dynamisch in WebP in Chrome konvertiert wird.
1. Wiederholen Sie diesen Test auf verschiedenen Browsern und bei unterschiedlichen Benutzerbedingungen. 

>[!NOTE]
Nicht alle Bilder werden konvertiert.  Smart Imaging entscheidet, ob die Konvertierung erforderlich ist, um die Leistung zu verbessern. In einigen Fällen, in denen keine Leistungssteigerung erwartet wird oder das Format nicht JPEG oder PNG ist, wird das Bild nicht konvertiert.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

## Kann Smart Imaging bei jeder Anforderung deaktiviert werden? {#turning-off-smart-imaging}

Ja. Sie können Smart Imaging deaktivieren, indem Sie den Modifikator `bfc=off` zur URL hinzufügen.

## Welche &quot;Abstimmung&quot;ist verfügbar? Gibt es Einstellungen oder Verhaltensweisen, die definiert werden können? (#tuning-settings)

Derzeit können Sie Smart Imaging optional aktivieren oder deaktivieren. Es gibt keine andere Abstimmung.

## Wenn Smart Imaging die Qualitätseinstellungen verwaltet, können wir dann Mindestwerte und Höchstwerte festlegen? Ist es zum Beispiel möglich, &quot;nicht kleiner als 60&quot;und &quot;nicht größer als 80 Qualität&quot;festzulegen? (#minimum-maximum)

Die aktuelle Smart Imaging-Funktion bietet keine solche Bereitstellbarkeit.

## In einigen Fällen wird ein JPEG-Bild anstelle eines WebP-Bildes an Chrome zurückgegeben. Warum passiert das? (#jpeg-webp)

Smart Imaging bestimmt, ob die Konversion vorteilhaft ist. Das neue Bild wird nur dann zurückgegeben, wenn die Konvertierung zu einer kleineren Dateigröße mit vergleichbarer Qualität führt.
