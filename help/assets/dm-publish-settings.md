---
title: Konfigurieren der Dynamic Media-Veröffentlichungseinstellungen für Image-Server
description: Erfahren Sie, wie Sie Publishing in Dynamic Media einrichten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
hide: true
hidefromtoc: true
exl-id: null
source-git-commit: f76f02f97de477af80666ea76a499578c36fb09e
workflow-type: tm+mt
source-wordcount: '3450'
ht-degree: 5%

---


# Konfigurieren der Dynamic Media-Veröffentlichungseinstellungen für Image-Server

Die Konfiguration der Veröffentlichungseinstellungen von Dynamic Media ist nur verfügbar, wenn:

* Sie führen Dynamic Media im Scene7-Modus aus. Siehe [Aktivieren von Dynamic Media im Scene7-Modus](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode).
* Sie haben eine *vorhandene* **[!UICONTROL Dynamic Media-Konfiguration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager 6.5 oder höher.
* Sie sind ein Experience Manager-Systemadministrator mit Administratorrechten.

Die Veröffentlichungseinstellungen von Dynamic Media sind für erfahrene Website-Entwickler und -Programmierer vorgesehen. Adobe Dynamic Media empfiehlt, dass Benutzer, die diese Veröffentlichungseinstellungen ändern, mit Adobe Dynamic Media, HTTP-Protokollstandards und -Konventionen und grundlegender Bildverarbeitungstechnologie vertraut sind.

Auf der Seite &quot;Veröffentlichungseinstellungen von Dynamic Media&quot;werden Standardeinstellungen festgelegt, die festlegen, wie Assets von Adobe Dynamic Media-Servern an Websites oder Anwendungen bereitgestellt werden. Wenn keine Einstellung festgelegt ist, stellt der Adobe Dynamic Media-Server ein Asset gemäß einer Standardeinstellung bereit, die auf der Seite &quot;Veröffentlichungseinstellungen&quot;von Dynamic Media konfiguriert wurde.

Siehe auch [Optional - Einrichtung und Konfiguration von Dynamic Media - Einstellungen für den Scene7-Modus](/help/assets/option-b-config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings) für weitere optionale Konfigurationsaufgaben.

>[!NOTE]
>
>Upgrade von Dynamic Media Classic auf Dynamic Media auf Adobe Experience Manager? Die [Allgemeine Einstellungen](/help/assets/dm-general-settings.md) -Seite und -Seite zur Veröffentlichungseinstellungen in Dynamic Media werden vorab mit den Werten aus Ihrem Dynamic Media Classic-Konto gefüllt. Die Ausnahmen sind alle Werte, die unter dem **[!UICONTROL Standardmäßige Upload-Optionen]** auf der Seite &quot;Allgemeine Einstellungen&quot;angezeigt. Diese Werte befinden sich bereits im Experience Manager. Alle Änderungen, die Sie unter **[!UICONTROL Standardmäßige Upload-Optionen]** auf einer der fünf Registerkarten über die Experience Manager-Benutzeroberfläche angezeigt werden, spiegeln sich in Dynamic Media wider, nicht in Dynamic Media Classic. Alle anderen Einstellungen und Werte in [Allgemeine Einstellungen](/help/assets/dm-general-settings.md) und die Seite zur Veröffentlichungseinstellungen zwischen Dynamic Media Classic und Dynamic Media auf dem Experience Manager verwaltet.

**So konfigurieren Sie den Dynamic Media Publish Setup Image Server:**

1. Wählen Sie im Experience Manager-Autorenmodus das Experience Manager-Logo aus, um auf die globale Navigationskonsole zuzugreifen.
1. Wählen Sie in der linken Leiste das Symbol Tools und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]**.
1. Legen Sie auf der Seite &quot;Image-Server&quot;den Image-Server - Veröffentlichungskontext fest und konfigurieren Sie dann auf den fünf Registerkarten die standardmäßigen Veröffentlichungseinstellungen.

   * [Bild-Server ](#image-server)
   * [Sicherheit](#security-tab) tab
   * [Katalogverwaltung](#catalog-management-tab) tab
   * [Anforderungsattribute](#request-attributes-tab) tab
   * [Allgemeine Attribute für Miniaturansichten](#common-thumbnail-attributes-tab) tab
   * [Farbverwaltungsattribute](#color-management-attributes-tab) tab

   ![Dynamic Media-Veröffentlichungseinstellungen](/help/assets/assets-dm/dm-publish-setup.png)
   *Dynamic Media-Veröffentlichungseinstellungen mit der **[!UICONTROL Anforderungsattribute]**ausgewählt ist.*<br><br>

1. Wenn Sie fertig sind, wählen Sie rechts oben auf der Seite die Option **[!UICONTROL Speichern]**.

## Bild-Server  {#image-server}

Auf der Image-Server-Seite werden Standardeinstellungen für die Bereitstellung von Bildern von Image-Servern festgelegt. Einstellungen sind in fünf Kategorien verfügbar

| Veröffentlichungskontext | Beschreibung |
| --- | --- |
| Bereitstellung von Bildern | Gibt den Kontext für Veröffentlichungseinstellungen an. |
| Bereitstellung von Testbildern | Gibt den Kontext zum Testen der Veröffentlichungseinstellungen an.<br>Nur für neue Dynamic Media-Konten wird die Standardeinstellung **[!UICONTROL Kundenadresse]** -Feld auf `127.0.0.1` automatisch.<br>Siehe [Testen Sie Assets, bevor Sie sie veröffentlichen](#test-assets-before-making-public). |

### Registerkarte Sicherheit {#security-tab}

**[!UICONTROL Kundenadresse]** - Hier können Sie eine oder mehrere IP-Adressen oder IP-Adressbereiche angeben. Wenn diese Option spezifiziert ist, werden Anfragen an diesen Bildkatalog, die von einem Client stammen, der eine nicht aufgeführte IP-Adresse hat, abgelehnt. Diese Regel gilt sowohl für die Bereitstellung von Bildern als auch für gerenderte Bilder.

### Registerkarte &quot;Katalogverwaltung&quot; {#catalog-management-tab}

**[!UICONTROL Dateipfad für Definitionsregeln]** - Gibt die Datei an, die die Regelsatzdefinitionen für den Bildkatalog enthält.

Siehe auch [RuleSetFile](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-rulesetfile.html) im Dynamic Media Viewer-Referenzhandbuch.

>[!NOTE]
>
>Wenn Ihr Dynamic Media Classic-Konto bereits über eine **[!UICONTROL Dateipfad für Definitionsregeln]** ausgewählt (wie festgelegt unter **[!UICONTROL Einrichtung]** > **[!UICONTROL Anwendung]** > **[!UICONTROL Veröffentlichungseinstellungen]**, unter **[!UICONTROL Katalogverwaltung]** ), ruft Ihr Dynamic Media-Konto auf dem Experience Manager die Datei von Dynamic Media Classic ab. Die Datei wird dann gespeichert und in diesem Feld verfügbar gemacht, wenn Sie die **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]** zum ersten Mal.

### Registerkarte &quot;Anforderungsattribute&quot; {#request-attributes-tab}

Diese Einstellungen beziehen sich auf das standardmäßige Erscheinungsbild von Bildern.

| Einstellung | Beschreibung |
| --- | --- |
| **[!UICONTROL Maximale Größe des Antwortbildes]** | Erforderlich.<br>Nur für neue Dynamic Media-Konten wird die Standardgrößenbeschränkung automatisch auf Breite festgelegt: `3000` und Höhe: `3000` für beide **[!UICONTROL Image Serving]** und **[!UICONTROL Image-Serving testen]**.<br>Gibt die maximale Breite und Höhe des Antwortbilds an, das an den Client zurückgegeben wird. Der Server gibt einen Fehler zurück, wenn eine Anfrage ein Antwortbild verursacht, dessen Breite, Höhe oder beides größer als diese Einstellung ist.<br>Siehe auch [MaxPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Verschleierungsmodus für Anfragen]** | Aktivieren Sie diese Option, wenn die base64-Kodierung auf gültige Anforderungen angewendet werden soll.<br>Siehe auch [RequestObfuscation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestobfuscation.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Verschlüsselungsmodus für Anfragen]** | Aktivieren Sie diese Option, wenn in Anfragen eine einfache Hash-Sperre enthalten sein soll.<br>Siehe auch [RequestLock](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestlock.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardattribute für Anfragen]** |  |
| **[!UICONTROL Standarderweiterung für Bilddatei]** | Erforderlich.<br>Standardmäßige Datendateierweiterung, die an die Feldwerte &quot;Katalogpfad&quot;und &quot;MaskPath&quot;angehängt wird, wenn der Pfad kein Dateisuffix enthält.<br>Siehe auch [DefaultExt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultext.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Name der Standardschriftart]** | Gibt an, welche Schrift verwendet wird, wenn von einer Texteditoranforderung keine Schrift bereitgestellt wird. Falls angegeben, muss es sich um einen gültigen Schriftnamenwert in der Schriftartzuordnung dieses Bildkatalogs oder in der Schriftzuordnung des Standardkatalogs handeln.<br>Siehe auch [DefaultFont](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultfont.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardbild]** | Legt fest, welches Standardbild angezeigt werden soll, wenn ein angefordertes Bild nicht gefunden werden kann.<br>Siehe auch [DefaultImage](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-defaultimage.html) im Dynamic Media Viewer-Referenzhandbuch.<br>**NOTE**: Wenn Ihr Dynamic Media Classic-Konto bereits über eine **[!UICONTROL Standardbild]** ausgewählt (wie festgelegt unter **[!UICONTROL Einrichtung]** > **[!UICONTROL Anwendung]** > **[!UICONTROL Veröffentlichungseinstellungen]**, unter **[!UICONTROL Standardmäßige Anforderungsattribute]** ), ruft Ihr Dynamic Media-Konto auf dem Experience Manager die Datei von Dynamic Media Classic ab. Die Datei wird dann gespeichert und in diesem Feld verfügbar gemacht, wenn Sie die **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]** zum ersten Mal. |
| **[!UICONTROL Standardbildmodus]** | Wenn das Regler-Feld aktiviert ist (Regler rechts), wird die **[!UICONTROL Standardbild]** ersetzt jede fehlende Ebene im Quellbild durch das Standardbild und gibt den Verbund wie gewohnt zurück. Wenn das Regler-Feld deaktiviert ist (Regler links), ersetzt das Standardbild das gesamte Composite-Bild, selbst wenn das fehlende Bild nur eine von mehreren Ebenen ist.<br>Siehe auch [DefaultImageMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultimagemode.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Ansichtsgröße]** | Erforderlich.<br>Nur für neue Dynamic Media-Konten wird die standardmäßige Ansichtsgröße automatisch auf Breite eingestellt: `1280` und Höhe: `1280` für beide **[!UICONTROL Image Serving]** und **[!UICONTROL Image-Serving testen]**.<br>Der Server beschränkt die Größe der Antwortbilder auf diese Breite und Höhe, wenn die Anforderung die Anzeigegröße nicht explizit mithilfe von `wid=`, `hei=`oder `scl=`.<br>Siehe auch [DefaultPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardgröße für Miniaturansichten]** | Erforderlich.<br>Wird anstelle des Attributs verwendet **[!UICONTROL Standardansichtsgröße]** für Miniaturanfragen (`req=tmb`). Der Server beschränkt die Größe der Antwortbilder auf diese Breite und Höhe, wenn eine Miniaturanfrage (`req=tmb`) gibt die Größe nicht explizit an mit `wid=`, `hei=`oder `scl=`.<br>Siehe auch [DefaultThumbPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Hintergrundfarbe]** | Gibt den RGB-Wert an, der zum Ausfüllen eines Bereichs eines Antwortbilds verwendet wird, der keine tatsächlichen Bilddaten enthält.<br>Siehe auch [BkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Attribute für JPEG-Kodierung]** |  |
| **[!UICONTROL Qualität]** | <br>Legt die Standardattribute von JPEG-Antwortbildern fest.<br>Nur für neue Dynamic Media-Konten wird die Variable **[!UICONTROL Qualität]** Standardwert wird automatisch auf `80` für beide **[!UICONTROL Image Serving]** und **[!UICONTROL Image-Serving testen]**.<br>Dieses Feld wird im Bereich von 1 bis 100 definiert.<br>Siehe auch [JpegQuality](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Chromatisches Downsampling]** | Aktivieren oder deaktivieren Sie die chromatische Neuberechnung, die von JPEG-Kodierern verwendet wird. |
| **[!UICONTROL Standard-Resamplingmodus]** | Gibt die standardmäßigen Resampling- und Interpolationsattribute an, die für die Skalierung von Bilddaten verwendet werden. Verwenden Sie wann `resMode` in einer Anfrage nicht angegeben ist.<br>Nur für neue Dynamic Media-Konten wird der standardmäßige Resamplingmodus automatisch auf `Sharp2` für beide **[!UICONTROL Image Serving]** und **[!UICONTROL Image-Serving testen]**.<br>Siehe auch [ResMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html) im Dynamic Media Viewer-Referenzhandbuch. |

### Registerkarte &quot;Allgemeine Miniaturattribute&quot; {#common-thumbnail-attributes-tab}

Diese Einstellungen beziehen sich auf die standardmäßige Darstellung und Ausrichtung von Miniaturbildern.

| Einstellung | Beschreibung |
| --- | --- |
| **[!UICONTROL Standardhintergrundfarbe für Miniaturansicht]** | Gibt den RGB-Wert an, der zum Ausfüllen des Bereichs eines Ausgabeminiaturbilds verwendet wird, das keine tatsächlichen Bilddaten enthält. Wird nur für Miniaturansichten verwendet (`req=tmb`) und wann **[!UICONTROL Standardtyp für Miniaturansichten]** festgelegt ist auf **[!UICONTROL Anpassen]** oder **[!UICONTROL Textur]**.<br>Siehe auch [ThumbBkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbbkgcolor.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Horizontale Ausrichtung]** | Gibt die horizontale Ausrichtung des Miniaturbilds im Rechteck des Antwortbilds an, das durch `wid=` und `hei=` -Werte.<br>Wird nur für Miniaturansichten verwendet (`req=tmb`) und wann **[!UICONTROL Standardtyp für Miniaturansichten]** festgelegt ist auf **[!UICONTROL Anpassen]**.<br>Es gibt drei horizontale Ausrichtungen, aus denen Sie wählen können: **[!UICONTROL Zentrierte Ausrichtung]**, **[!UICONTROL Linksausrichtung]** und **[!UICONTROL Rechtsausrichtung]**.<br>Siehe auch [ThumbHorizAlign](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbhorizalign.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Vertikale Ausrichtung]** | Gibt die vertikale Ausrichtung des Miniaturbilds im Rechteck des Antwortbilds an, das durch `wid=` und `hei=` -Werte. Wird nur für Miniaturansichten verwendet (`req=tmb`) und wann **[!UICONTROL Standardtyp für Miniaturansichten]** festgelegt ist auf **[!UICONTROL Anpassen]**.<br>Es gibt drei vertikale Ausrichtungen zur Auswahl: **[!UICONTROL Ausrichtung oben]**, **[!UICONTROL Zentrierte Ausrichtung]** und **[!UICONTROL Untere Ausrichtung]**.<br>Siehe auch [ThumbVertAlign](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbvertalign.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Cache für Time-to-Live]** | Bietet ein standardmäßiges Ablaufintervall in Stunden für den Fall, dass ein bestimmter Katalogdatensatz kein gültiges Katalogablaufdatum aufweist. Legen Sie fest auf `-1` zum Markieren, dass nie abläuft. <br>Siehe auch [Ablauf](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardtyp für Miniaturansichten]** | Stellt eine Standardeinstellung für den Miniaturansichtstyp bereit, falls ein bestimmter Katalogdatensatz keinen gültigen ThumbType-Katalogwert enthält. Wird nur für Miniaturansichten verwendet (`req=tmb`).<br>Es gibt drei Arten von Miniaturansichten, aus denen Sie wählen können: **[!UICONTROL Zuschneiden]**, **[!UICONTROL Anpassen]** und **[!UICONTROL Textur]**.<br>Siehe auch [ThumbType](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbtype.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardauflösung für Miniaturansichten]** | Stellt eine Standardeinstellung für die Auflösung des Miniaturansichtsobjekts bereit, falls ein bestimmter Katalogdatensatz keinen gültigen ThumbRes-Katalogwert enthält. Wird nur für Miniaturansichten verwendet (`req=tmb`) und wenn die **[!UICONTROL Standardtyp für Miniaturansichten]** festgelegt ist auf **[!UICONTROL Textur]**.<br>Siehe auch [ThumbRes](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbres.html) im Dynamic Media Viewer-Referenzhandbuch. |

### Registerkarte &quot;Farbverwaltungsattribute&quot; {#color-management-attributes-tab}

Diese Einstellungen bestimmen, welche ICC-Farbprofile für Bilder verwendet werden.

**Rendering-Intent der Farbumwandlung**
Ein Rendering-Intent für die Farbkonvertierung ermöglicht das Überschreiben der standardmäßigen Rendering-Absicht der Arbeitsprofile, um zu bestimmen, wie die Quellfarben angepasst werden. Wird verwendet, wenn:

1. Eines der standardmäßigen ICC-Profile ist der Zielfarbraum einer Farbkonvertierung.
1. Ein Ausgabegerät (Drucker oder Monitor) ist durch dieses Profil gekennzeichnet.
1. Und der angegebene Rendering-Intent ist für dieses Profil gültig.

Verschiedene Rendering-Intents verwenden unterschiedliche Regeln, um zu bestimmen, wie die Quellfarben angepasst werden.

Siehe auch [IccRenderIntent](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html) im Dynamic Media Viewer-Referenzhandbuch.

>[!NOTE]
>
>Im Allgemeinen ist es am besten, den standardmäßigen Rendering-Intent für die ausgewählte Farbeinstellung zu verwenden, der von Adobe auf Einhaltung von Branchenstandards getestet wurde. Wenn Sie beispielsweise eine Farbeinstellung für Nordamerika oder Europa auswählen, lautet die standardmäßige Farbkonvertierungsabsichten . **[!UICONTROL Relativ farbmetrisch]**. Wenn Sie eine Farbeinstellung für Japan auswählen, lautet die standardmäßige Rendering-Absicht für die Farbkonvertierung **[!UICONTROL Wahrnehmungsorientiert]**.

| Einstellung | Eigenschaften |
| --- | --- |
| **[!UICONTROL CMYK-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für CMYK-Daten verwendet werden soll. Wenn **[!UICONTROL Keine angegeben]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn CMYK-Quellbilder beteiligt sind. Alle CMYK-Arbeitsbereiche sind geräteabhängig, d. h. sie basieren auf tatsächlichen Tinten- und Papierkombinationen. Die Adobe der CMYK-Arbeitsbereiche basiert auf den üblichen kommerziellen Druckbedingungen.<br> Siehe auch [IccProfileCMYK](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Graustufen-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für Graustufendaten verwendet werden soll. Wenn **[!UICONTROL Keine angegeben]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn Graustufen-Quellbilder beteiligt sind.<br>Siehe auch [IccProfileGray](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL RGB-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für RGB-Daten verwendet werden soll. Wenn **[!UICONTROL Keine angegeben]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn RGB-Quellbilder verwendet werden. Im Allgemeinen ist es am besten, **[!UICONTROL Adobe RGB]** oder **[!UICONTROL sRGB]**, anstatt des Profils für ein bestimmtes Gerät (z. B. ein Monitorprofil). **[!UICONTROL sRGB]** wird empfohlen, wenn Sie Bilder für das Web oder mobile Geräte vorbereiten, da dadurch der Farbraum des Standardbildschirms definiert wird, der zum Anzeigen von Bildern im Internet verwendet wird. **[!UICONTROL sRGB]** ist auch eine gute Wahl, wenn Sie mit Bildern von Digitalkameras auf Verbraucherebene arbeiten, da die meisten dieser Kameras sRGB als Standardfarbraum verwenden.<br>Siehe auch [IccProfileRBG](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Rendering Intent für Farbumwandlung]** | **[!UICONTROL Wahrnehmungsorientiert]** - Ziel ist es, die visuelle Beziehung zwischen Farben so zu erhalten, dass sie für das menschliche Auge als natürlich wahrgenommen werden, auch wenn sich die Farbwerte selbst ändern können. Dieser Intent eignet sich für fotografische Bilder mit vielen Farben, die außerhalb der Farbskala liegen. Diese Einstellung ist die standardmäßige Rendering-Absicht für die japanische Druckindustrie. |
|  | **[!UICONTROL Relativ farbmetrisch]** - Vergleicht die extreme Hervorhebung des Quellfarbraums mit der des Zielfarbraums und verschiebt alle Farben entsprechend. Die Farben außerhalb der Farbskala werden auf die nächstmögliche reproduzierbare Farbe im Zielfarbraum verschoben. Relativ farbmetrisch erhalten Sie mehr Originalfarben in einem Bild als Wahrnehmungswerte. Diese Einstellung ist die standardmäßige Rendering-Absicht für den Druck in Nordamerika und Europa. |
|  | **[!UICONTROL Sättigung]** - Versucht, visuelle Farben in einem Bild zu produzieren, auf Kosten der Farbgenauigkeit. Dieser Rendering-Intent eignet sich für Geschäftsgrafiken wie Grafiken oder Grafiken, bei denen helle gesättigte Farben wichtiger sind als die exakte Beziehung zwischen Farben. |
|  | **[!UICONTROL Absolut farbmetrisch]** - Lässt Farben, die in die Zielgruppe fallen, unverändert. Farben außerhalb der Farbskala werden abgeschnitten. Es wird keine Skalierung der Farben auf den Ziel-Weißpunkt durchgeführt. Dieser Zweck dient der Erhaltung der Farbgenauigkeit auf Kosten der Beibehaltung von Beziehungen zwischen Farben und ist für die Prüfung geeignet, die Ausgabe eines bestimmten Geräts zu simulieren. Dieser Zweck ist nützlich für die Vorschau, wie die Papierfarbe sich auf Druckfarben auswirkt. |

## Testen Sie Assets, bevor Sie sie veröffentlichen {#test-assets-before-making-public}

Mit Secure Testing können Sie eine sichere Testumgebung definieren und eine robuste Business-to-Business-Lösung erstellen, die auf einem konfigurierbaren Satz von IP-Adressen und -Bereichen basiert. Mit dieser Funktion können Sie Ihre Adobe Dynamic Media-Implementierungen mit der Architektur Ihres Content-Management- und Business-Systems abgleichen.

Mit Secure Testing können Sie eine Vorschau der Staging-Version der Website mit unveröffentlichtem Inhalt anzeigen.

Erstellen Sie bei Bedarf eine Staging-Umgebung, anstatt Assets aus folgenden Gründen öffentlich verfügbar zu machen:

* Vorschau von Websites vor dem öffentlichen Start (Staging-Website).
* Bereitstellen von Assets, die eingeschränkten Zugriff erfordern, wie z. B. E-Kataloge, die Preise in einer B2B-Webanwendung anzeigen.
* Verwenden Sie Assets hinter einer Firewall als Teil des Produktinformationsmanagementsystems, der Kundendienstanwendung, der Schulungs-Site usw.

>[!NOTE]
>
>Secure Testing hat keine Auswirkungen auf den Zugriff auf Adobe Dynamic Media Classic. Die Adobe Dynamic Media Classic-Sicherheit bleibt konsistent und erfordert die üblichen Anmeldeinformationen für den Zugriff auf Adobe Dynamic Media Classic und zugehörige Webdienste.

### Funktionsweise von Secure Testing {#how-test-assets-works}

Die meisten Unternehmen betreiben ihr Internet hinter einer Firewall. Der Zugang zum Internet ist über bestimmte Routen und in der Regel über eine begrenzte Anzahl öffentlicher IP-Adressen möglich.

Über Ihr Unternehmensnetzwerk können Sie mithilfe von Websites wie [https://www.whatismyip.com](https://www.whatismyip.com/) oder fordern Sie diese Informationen von Ihrem IT-Unternehmen an.

Mit Secure Testing richtet Adobe Dynamic Media einen dedizierten Image-Server für Staging-Umgebungen oder interne Anwendungen ein. Mit einer beliebigen Anforderung an diesen Server wird die IP-Ursprungsadresse geprüft. Wenn die eingehende Anforderung nicht in der Liste genehmigter IP-Adressen enthalten ist, wird eine Fehlerantwort zurückgegeben. Der Dynamic Media-Unternehmensadministrator konfiguriert die Liste genehmigter IP-Adressen für die sichere Testumgebung seines Unternehmens.

Da der Speicherort der ursprünglichen Anforderung bestätigt werden muss, wird der Traffic des Secure Testing-Dienstes nicht über ein Inhaltsverteilungsnetzwerk wie den öffentlichen Dynamic Media Image Server-Traffic geleitet. Anforderungen an den Secure Testing-Dienst weisen im Vergleich zu den öffentlichen Dynamic Media-Bildservern eine etwas höhere Latenz auf.

Nicht veröffentlichte Assets sind sofort über die Secure Testing Services verfügbar, ohne dass veröffentlicht werden muss. Auf diese Weise können Sie eine Vorschau ausführen, bevor Assets auf ihrem öffentlichen Bildserver veröffentlicht werden.

>[!NOTE]
>
>Sichere Testdienste verwenden den Katalogserver, der mit einem internen Veröffentlichungskontext konfiguriert ist. Wenn Ihr Unternehmen daher für die Veröffentlichung auf Secure Testing konfiguriert ist, werden hochgeladene Assets in Adobe Dynamic Media sofort in den Secure Testing Services verfügbar. Diese Funktion gilt unabhängig davon, ob die Assets beim Hochladen zur Veröffentlichung markiert sind.

Secure Testing Services unterstützen derzeit die folgenden Asset-Typen und -Funktionen:

* Bilder.
* Vignetten (Render Server-Anforderungen).
* Render Server-Anforderungen (unterstützt, aber explizit vom Kunden angefordert).
* Sets, einschließlich Bildsets, E-Katalog, Rendersets und Mediensets.
* Standard-Adobe Dynamic Media Rich-Media-Viewer.
* Adobe Dynamic Media OnDemand JSP-Seiten.
* Statische Inhalte wie PDF-Dateien und progressiv bereitgestellte Videos.
* HTTP-Video-Streaming.
* Progressives Video-Streaming.

Die folgenden Asset-Typen und -Funktionen werden derzeit nicht unterstützt:

* Adobe Dynamic Media Classic Info- oder eCatalog-Suche
* RTMP-Video-Streaming
* Web-to-Print
* UGC-Dienste (benutzergenerierte Inhalte)

>[!IMPORTANT]
>
>Die Unterstützung für neue oder vorhandene UGC-Vektorbild-Assets in Adobe Dynamic Media wurde am 30. September 2021 eingestellt.

### Testen des Secure Testing-Dienstes {#test-secure-testing-service}

Gehen Sie wie folgt vor, um sicherzustellen, dass der Secure Testing-Dienst erwartungsgemäß funktioniert:

#### Konto vorbereiten

1. Wenden Sie sich an die Kundenunterstützung von Adobe und fordern Sie sie auf, sichere Tests für Ihr Konto zu aktivieren.
1. Wählen Sie in Adobe Experience Manager **[!UICONTROL Instrumente]** > **[!UICONTROL Assets]** > **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]**.
1. Auf der Seite &quot;Image-Server&quot;im **[!UICONTROL Veröffentlichungskontext]** Dropdown-Liste auswählen **[!UICONTROL Image-Serving testen]**.
1. Wählen Sie die **[!UICONTROL Sicherheit]** Registerkarte.
1. Für **[!UICONTROL Kundenadresse]** filtern, wählen Sie **[!UICONTROL Hinzufügen]**.
1. Im **[!UICONTROL IP-Adresse]** -Feld eine IP-Adresse ein.
1. Im **[!UICONTROL Maskieren]** -Feld eine Netzmaske eingeben.

   >[!NOTE]
   >
   >Wenn Sie mehr als eine IP-Adresse und Netzmaske hinzufügen, ermöglicht dies effektiv *all* IP-Adressen, um Asset-Aufrufe durchzuführen, und sie werden alle angezeigt.

1. Führen Sie einen der folgenden Schritte aus:

   * Um weitere IP-Adressen hinzuzufügen, wiederholen Sie die drei vorherigen Schritte.
   * Fahren Sie mit dem nächsten Schritt fort.

1. Wählen Sie in der rechten oberen Ecke der Seite &quot;Image-Server&quot;die Option **[!UICONTROL Speichern]**.
1. Laden Sie die gewünschten Bilder in Ihr Adobe Dynamic Media-Konto hoch.

<!--    See [Upload files](uploading-files.md#uploading_files). -->

1. Vergewissern Sie sich, dass einige der Bilder zur Veröffentlichung markiert sind, andere nicht markiert sind, und senden Sie dann den Veröffentlichungsauftrag.

<!--    See [Publish files](publishing-files.md#publishing_files). -->

1. Bestimmen Sie den Namen Ihres Secure Testing-Dienstes, indem Sie **[!UICONTROL Instrumente]** > **[!UICONTROL Assets]** > **[!UICONTROL Allgemeine Dynamic Media-Einstellung]**.
1. Im **[!UICONTROL Server]** finden Sie den Servernamen rechts von **[!UICONTROL Veröffentlichter Servername]**.

Wenden Sie sich an Adobe Care , wenn der Servername fehlt oder die URL zum Server nicht funktioniert.

#### Vorbereiten von Website-Varianten

Sie benötigen zwei Varianten einer Website, auf der die veröffentlichten und nicht veröffentlichten Assets verknüpft sind:

* Öffentliche Version - Verknüpfen Sie Assets mit Ihrer herkömmlichen Adobe Dynamic Media URL-Syntax.
* Staging-Version - Verknüpfen Sie Assets mit derselben Syntax wie mit dem Namen der Secure Testing-Site.

#### Ausführen der Tests

Führen Sie die folgenden Tests durch:

1. Überprüfen Sie, ob Assets in Ihrem Unternehmensnetzwerk sichtbar sind.

   Innerhalb des Unternehmensnetzwerks, das durch den zuvor definierten IP-Adressbereich identifiziert wurde, zeigt die Staging-Version der Website alle Bilder an, unabhängig davon, ob sie zur Veröffentlichung markiert wurden oder nicht. Daher können Sie Tests durchführen, ohne Bilder versehentlich vor der Genehmigung der Vorschau oder dem Produktstart verfügbar zu machen.

   Vergewissern Sie sich, dass die öffentliche Version Ihrer Site veröffentlichte Assets anzeigt, wie sie zuvor mit Adobe Dynamic Media erlebt wurden.

1. Stellen Sie außerhalb Ihres Unternehmensnetzwerks sicher, dass nicht veröffentlichte Assets (d. h. nicht zur Veröffentlichung markiert) vor dem Zugriff durch Dritte geschützt sind.

   Greifen Sie von außerhalb auf Ihr Netzwerk zu (z. B. von Ihrem privaten Computer oder über eine 4G/5G-Verbindung) und überprüfen Sie dann, ob in der öffentlichen Version der Site alle veröffentlichten Assets, jedoch keine unveröffentlichten Inhalte angezeigt werden.

   Vergewissern Sie sich, dass in der Staging-Version kein Asset angezeigt wird, da Sie von einer nicht genehmigten IP-Adresse aus auf den Secure Testing-Dienst zugreifen.
