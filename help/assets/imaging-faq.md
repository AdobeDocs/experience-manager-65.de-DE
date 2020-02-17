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
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Intelligente Bildbearbeitung {#smart-imaging}

## Was ist intelligente Bildbearbeitung? {#what-is-smart-imaging}

Intelligente Bildbearbeitung nutzt die individuellen anzeigebezogenen Benutzermerkmale, um automatisch die richtigen Bilder für ein optimiertes individuelles Erlebnis zu präsentieren. Das Ergebnis: mehr Leistung und Interaktion. Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert in der letzten Sekunde abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter.

Intelligente Bildbearbeitung profitiert von einer zusätzlichen Leistungssteigerung, die auf eine vollständige Integration in den erstklassigen Premium-CDN-Dienst zurückzuführen ist. Dieser Dienst findet die optimale Internetverbindung zwischen Servern, Netzwerken und Peering Points, die eine niedrigste Latenzrate und/oder Paketverlustrate als die Standardverbindung im Internet aufweisen.

## Was sind die Hauptvorteile von intelligenter Bildbearbeitung? {#what-are-the-key-benefits-of-smart-imaging}

Intelligente Bildbearbeitung sorgt durch eine automatische Optimierung der Bilddateigröße für eine bessere Bereitstellungsleistung. Grundlage dafür bilden die Benutzermerkmale. Da Bilder einen Großteil der Seitenladezeit ausmachen, kann die Leistungssteigerung einen enormen Einfluss auf geschäftsbezogene KPIs wie höhere Konversionsraten, Besuchszeit pro Site, niedrigere Website-Absprungraten usw. haben.  Adobe hat das Leistungsvermögen von einer standardmäßigen Bildbereitstellung und von intelligenter Bildbearbeitung in Bezug auf verschiedene Dateiformate, Browser und Qualitätseinstellungen (QLT) verglichen. Insgesamt können Sie je nach vorhandenen Einstellungen für die Bildvorgaben und abhängig von den jeweiligen Endbenutzermerkmalen von einer Leistungssteigerung zwischen 22 und 47 % ausgehen.  

![image2017-11-14_133226](assets/image2017-11-14_133226.png)

## Ist intelligente Bildbearbeitung mit irgendwelchen Lizenzierungskosten verbunden? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nein. Intelligente Bildbearbeitung ist Teil Ihrer vorhandenen Lizenz für Dynamic Media Classic (Scene7) oder Dynamic Media. Es entstehen keine zusätzlichen Kosten durch die Nutzung dieser neuen Funktion.  

## Wie funktioniert intelligente Bildbearbeitung? {#how-does-smart-imaging-work}

Wenn ein Bild erstmalig von einem Verbraucher angefordert wird, überprüfen wir die Benutzermerkmale und führen basierend auf dem Browser eine Konvertierung in das passende Bildformat durch.  Außerdem erstellen wir gleichzeitig sämtliche Formatkonvertierungen, die dann auf CDN-Seite im Cache gespeichert werden.  Wenn später Verbraucher mit verschiedenen Browsern dieses Bild anfordern, wird das richtige Bildformat automatisch und direkt vom CDN-Cache bereitgestellt.  Diese Formatkonvertierungen erfolgen verlustfrei, sodass die Wiedergabetreue nicht beeinträchtigt wird.  Intelligente Bildbearbeitung konvertiert Bilder automatisch in verschiedene, von den Browserfunktionen abhängige Formate:

* Automatische Konvertierung in verlustfreies WebP für Browser, die das WebP-Format unterstützen, z. B. Chrome, Android und Opera 
* Automatische Konvertierung in verlustfreies JPEGXR für Browser, die das JPEGXR-Format unterstützen, z. B. Internet Explorer 9 oder höher 
* Konvertieren Sie Browser, die das JPEG2000-Format unterstützen, z. B. Safari, automatisch in verlustfreies JPEG2000.
* Bereitstellung des ursprünglich angeforderten Bildformats für Browser, die diese Formate nicht unterstützen 

## Welche Bildformate werden unterstützt?  {#what-image-formats-are-supported}

Die folgenden Bildformate werden für intelligente Bildbearbeitung unterstützt:

* RGB JPEG 
* RGB PNG 
* RGB TIFF 
* CMYK JPEG 
* CMYK TIFF 

## Wie funktioniert intelligente Bildbearbeitung bei vorhandenen und bereits verwendeten Bildvorgaben? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Intelligente Bildbearbeitung kann für vorhandene Bildvorgaben verwendet werden. Praktisch alle Bildeinstellungen wie Größe, Qualität, Scharfzeichnen usw. werden dabei berücksichtigt. Was sich ändern wird, ist das Bildformat oder bei langsamer Netzwerkverbindung die Qualitätseinstellung. Bei der Formatkonvertierung wird die vollständige visuelle Genauigkeit, wie von Ihren Bildvorgabeeinstellungen definiert, bei einer kleineren Dateigröße beibehalten.

Angenommen, für eine Bildvorgabe ist etwa das JPEG-Format mit einer Größe von 500 x 500 sowie einer Qualitätseinstellung von „85“ und einem Unschärfenmasken-Wert von 0,1;1;5 definiert. Wenn wir erkennen, dass ein Benutzer Chrome als Browser verwendet, wird das Bild in ein verlustfreies WebP-Format mit einer Größe von 500 x 500, einer Qualitätseinstellung von 85 und einem Unschärfemasken-Wert von 0,1;1;5 konvertiert.

## Muss ich für intelligente Bildbearbeitung URLs und Bildvorgaben ändern oder neuen Code auf Websites bereitstellen? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Nein. Intelligente Bildbearbeitung funktioniert nahtlos mit Ihren vorhandenen Bild-URLs und Bildvorgaben. Für die intelligente Bildbearbeitung müssen Sie keinen Code auf Ihrer Website hinzufügen, um unterschiedliche Benutzereigenschaften (Browser, Bandbreite, Gerät usw.) zu ermitteln. All dies erledigt Adobe automatisch für Sie. 

The only change that may be required is to update the **[!UICONTROL Time To Live]** (TTL) setting. Diese Einstellung legt fest, wie lange Assets vom CDN zwischengespeichert werden. Zur maximalen Leistungsverbesserung von intelligenter Bildbearbeitung empfiehlt Adobe eine TTL-Einstellung von mindestens 24 Stunden. So ändern Sie diese Einstellung: 

* If you are using Dynamic Media Classic, tap **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**. Stellen Sie den Wert **[!UICONTROL Standardeinstellung für Time-To-Live des Client-Cache]** auf mindestens 24 ein.

* Wenn Sie dynamische Medien verwenden, befolgen Sie die Anweisungen zum [Konfigurieren der Bildeinstellungen](config-dynamic.md) für dynamische Medien Legen Sie den **[!UICONTROL Ablaufwert]** auf 24 Stunden oder länger fest.

>[!NOTE]
>
>Bei einem TTL-Wert von weniger als 1 Stunde funktioniert intelligente Bildbearbeitung nicht.

## Funktioniert intelligente Bildbearbeitung mit HTTPS? Und mit HTTP/2?  {#does-smart-imaging-working-with-https-how-about-http}

Intelligente Bildbearbeitung funktioniert bei Bildern, die über HTTP, HTTPS Darüber hinaus funktioniert es auch über HTTP/2.

## Bin ich zur Verwendung von intelligenter Bildbearbeitung berechtigt? {#am-i-eligible-to-use-smart-imaging}

Für die Verwendung der intelligenten Bildbearbeitung müssen die Konten &quot;Dynamic Media Classic&quot;oder &quot;Dynamic Media&quot;Ihres Unternehmens für AEM die folgenden Anforderungen erfüllen:

* Verwenden Sie das Adobe-gebündelte CDN (Content Delivery Network) als Teil Ihrer Lizenz.
* Verwenden Sie eine dedizierte Domäne (d. h. `images.company.com` oder `mycompany.scene7.com`), keine generische Domäne (d. h. `s7d1.scene7.com`, `s7d2.scene7.com`oder `s7d13.scene7.com`).

    Um Ihre Domänen zu suchen, melden Sie sich bei dem Konto bzw. den Konten Ihres Unternehmens an. 

   Tap **[!UICONTROL Setup > Application Setup > General Settings]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungsservername]**.  Wenn Sie derzeit eine generische -Domäne verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domäne beantragen.

* Stellen Sie keine Anfragen zu CMYK JPEG-Bildern. Im Rahmen der Verarbeitung wandelt die intelligente Bildbearbeitung CMYK JPEG-Bilder in das RGB-Format um. Wenn Sie CMYK JPEG-Bilder benötigen, können Sie die intelligente Bildbearbeitung nicht verwenden.

## Wie kann ich intelligente Bildbearbeitung für mein Konto aktivieren? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

Intelligente Bildbearbeitung wird nicht automatisch aktiviert; Sie müssen eine entsprechende Anfrage stellen.

1. Richten Sie eine Anfrage an den technischen Support (E-Mail: s7support@adobe.com). 
1. In der Anfrage geben Sie folgende Informationen an:

   1. Name des Hauptansprechpartners, E-Mail, Telefon.
   1. Geben Sie alle Domänen an, für die intelligente Bildbearbeitung aktiviert werden soll (also bilder.unternehmen.com oder meinunternehmen.scene7.com).

       Um Ihre Domänen zu suchen, melden Sie sich bei dem Konto bzw. den Konten Ihres Unternehmens an. 

       Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungsservername]**.  
   1. Vergewissern Sie sich, dass Sie CDN über Adobe und nicht verwaltet mit einer direkten Beziehung nutzen. 
   1. Vergewissern Sie sich, dass Sie eine dedizierte Domäne wie `images.company.com` oder `mycompany.scene7.com`verwenden und keine generische Domäne wie `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

       Um Ihre Domänen zu suchen, melden Sie sich bei dem Konto bzw. den Konten Ihres Unternehmens an. 

       Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungsservername]**.  Wenn Sie derzeit eine allgemeine Dynamic Media Classic-Domäne verwenden, können Sie im Rahmen dieses Übergangs den Übergang zu Ihrer eigenen benutzerdefinierten Domäne anfordern.
   1. Geben Sie an, ob Sie auch auf eine Nutzung über HTTP/2 angewiesen sind. 

1. Der technische Support nimmt Sie in die Kunden-Warteliste für die intelligente Bildbearbeitung auf. Dies geschieht in der Reihenfolge der eingehenden Anfragen.
1. Wenn Adobe Ihre Anfrage bearbeiten kann, setzt sich der Support mit Ihnen zwecks Koordinierung und Vereinbarung eines Zieldatums in Verbindung. 
1. Optional: Sie haben die Möglichkeit, intelligente Bildbearbeitung in der Stagingphase zu testen, bevor Adobe die neue Funktion auf das Produktionssystem überträgt.
1. Bei Abschluss werden Sie vom Support benachrichtigt. 
1. Um die Leistung der intelligenten Bildbearbeitung zu optimieren, empfiehlt Adobe, die &quot;Time To Live&quot;(TTL) auf 24 Stunden oder länger festzulegen. Die TTL definiert, wie lange Assets vom CDN zwischengespeichert werden. So ändern Sie diese Einstellung: 

   1. If you use Dynamic Media Classic, click **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**. Stellen Sie den Wert **[!UICONTROL Standardeinstellung für Time-To-Live des Client-Cache]** auf mindestens 24 ein.
   1. Wenn Sie dynamische Medien verwenden, befolgen Sie [diese Anweisungen](config-dynamic.md). Set the **[!UICONTROL Expiration]** value 24 hours or longer.

## Wann wird mein Konto voraussichtlich für intelligente Bildbearbeitung aktiviert sein? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

Die Anfragen werden in der Reihenfolge ihres Eingangs beim technischen Support gemäß Warteliste bearbeitet. 

>[!NOTE]
Die Vorlaufzeit kann lang sein, da der Cache zum Aktivieren der Funktion „Intelligente Bildbearbeitung “ gelöscht werden muss. Daher kann nur jeweils eine geringe Anzahl von Kunden gleichzeitig umgestellt werden. 

## Worin bestehen die Risiken bei einem Wechsel zur intelligenten Bildbearbeitung? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Durch den Übergang zu intelligenter Bildbearbeitung wird der Cache im CDN gelöscht, da auf eine neue Konfiguration von Dynamic Media Classic oder Dynamic Media auf AEM umgestellt wird.

Zu Beginn der Übergangsphase treffen die nicht im Cache gespeicherten Bilder direkt auf die Adobe-Ursprungsserver, bis der Cache neu erstellt wurde.  Aus diesem Grund führt Adobe nur wenige Umstellungen zugleich durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus unserer Quelle abgerufen werden. Bei den meisten Kunden ist der CDN-Cache innerhalb von 1 bis 2 Tagen vollständig neu aufgebaut.

## Wie kann ich feststellen, ob die intelligente Bildbearbeitung erwartungsgemäß funktioniert?  {#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Laden Sie, nachdem Ihr Konto mit intelligenter Bildbearbeitung konfiguriert wurde, eine Dynamic Media Classic (S7)-/Dynamic Media-Bild-URL in den Browser.
1. Öffnen Sie den Chrome-Entwicklerbereich, indem Sie im Browser auf **[!UICONTROL Anzeigen > Entwickler > Entwickler-Tools]** klicken.  Selbstverständlich können Sie auch ein anderes Browser-Entwickler-Tool Ihrer Wahl verwenden. 

1. Stellen Sie sicher, dass der Cache deaktiviert ist, wenn die Entwickler-Tools geöffnet sind. 

   1. Navigieren Sie unter Windows in den Bereich mit den Entwickler-Tools und aktivieren Sie dann das Kontrollkästchen **[!UICONTROL Cache deaktivieren (während DevTools geöffnet ist)]**. 
   1. On Mac, in the developer pane, under the **[!UICONTROL Network]** tab, select **[!UICONTROL disable cache]** .

1. Bei der ersten Anforderung wird das Bild nicht optimiert.  Normalerweise dauert es ca. 15 Minuten, bis das optimierte Bild zurückgegeben wird, wenn es sich nicht im CDN-Cache befindet. 
1. Sie werden feststellen, dass der Inhaltstyp in das entsprechende Format umgewandelt wird.  Der folgende Screenshot zeigt ein PNG-Bild, das in Chrome dynamisch ins WebP-Format konvertiert wird. 
1. Wiederholen Sie diesen Test auf verschiedenen Browsern und bei unterschiedlichen Benutzerbedingungen. 

>[!NOTE]
Nicht alle Bilder werden konvertiert.  Intelligente Bildbearbeitung entscheidet, ob durch Konvertieren die Leistung gesteigert werden kann. In bestimmten Fällen, in denen kein Leistungszuwachs zu erwarten ist, erfolgt keine Bildkonvertierung.  

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

