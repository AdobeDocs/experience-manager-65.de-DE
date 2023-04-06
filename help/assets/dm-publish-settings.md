---
title: Konfigurieren der Dynamic Media-Veröffentlichungseinstellungen für Imageserver
description: Erfahren Sie, wie Sie Publishing in Dynamic Media einrichten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
exl-id: c86e79c4-e887-4ee3-bb54-eeffb34a33c2
source-git-commit: 25fe5e240fd7404cb07375325e1f7b6a32923bfd
workflow-type: tm+mt
source-wordcount: '3494'
ht-degree: 97%

---

# Konfigurieren der Dynamic Media-Veröffentlichungseinstellungen für Imageserver

Die Konfiguration der Veröffentlichungseinstellungen von Dynamic Media ist nur verfügbar, wenn:

* Sie führen Dynamic Media im Scene7-Modus aus. Siehe [Aktivieren von Dynamic Media im Scene7-Modus](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode).
* Sie haben eine *vorhandene* **[!UICONTROL Dynamic Media-Konfiguration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager 6.5.11 oder höher. Weitere Informationen finden Sie unter [Erstellen einer Dynamic Media-Konfiguration in Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services).
* Sie sind ein Experience Manager-Systemadministrator mit Administratorrechten.

Die Veröffentlichungseinstellungen von Dynamic Media sind für erfahrene Website-Entwickler und -Programmierer vorgesehen. Adobe Dynamic Media empfiehlt, dass Benutzer, die diese Veröffentlichungseinstellungen ändern, mit Adobe Dynamic Media, HTTP-Protokollstandards und -Konventionen und grundlegender Bildverarbeitungstechnologie vertraut sind.

Auf der Seite „Veröffentlichungseinstellungen von Dynamic Media“ werden Standardeinstellungen festgelegt, die festlegen, wie Assets von Adobe Dynamic Media-Servern für Websites oder Programme bereitgestellt werden. Wenn keine Einstellung festgelegt ist, stellt der Adobe Dynamic Media-Server ein Asset gemäß einer Standardeinstellung bereit, die auf der Seite „Veröffentlichungseinstellungen von Dynamic Media“ konfiguriert wurde.

Informationen zu weiteren optionalen Konfigurationsaufgaben finden Sie unter [Optional – Einrichtung und Konfiguration der Scene7-Modus-Einstellungen von Dynamic Media](/help/assets/config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings).

>[!NOTE]
>
>Sie möchten ein Upgrade von Dynamic Media Classic auf Dynamic Media auf Adobe Experience Manager durchführen? Die Seite [Allgemeine Einstellungen](/help/assets/dm-general-settings.md) und die Seite zu Veröffentlichungseinstellungen in Dynamic Media werden vorab mit den Werten ausgefüllt, die von Ihrem Dynamic Media Classic-Konto übernommen werden. Die Ausnahmen sind alle Werte, die im Bereich **[!UICONTROL Standardmäßige Upload-Optionen]** auf der Seite „Allgemeine Einstellungen“ angezeigt werden. Diese Werte befinden sich bereits in Experience Manager. Alle Änderungen, die Sie unter **[!UICONTROL Standardmäßige Upload-Optionen]** auf einer der fünf Registerkarten in der Experience Manager-Benutzeroberfläche vornehmen, werden in Dynamic Media, nicht jedoch in Dynamic Media Classic angezeigt. Alle anderen Einstellungen und Werte auf der Seite [Allgemeine Einstellungen](/help/assets/dm-general-settings.md) und der Seite „Veröffentlichungseinstellungen“ werden von Dynamic Media Classic und Dynamic Media in Experience Manager verwaltet.

**So konfigurieren Sie den Dynamic Media Publish Setup Image Server:**

1. Klicken Sie im Autorenmodus in Experience Manager auf das Experience Manager-Logo, um auf die Konsole für die globale Navigation zuzugreifen.
1. Wählen Sie in der linken Leiste das Symbol „Tools“ und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]**.
1. Legen Sie auf der Seite „Image-Server“ den Image-Server-Veröffentlichungskontext fest und konfigurieren Sie dann auf den fünf Registerkarten die standardmäßigen Veröffentlichungseinstellungen.

   * [Image-Server](#image-server)
   * Registerkarte [Sicherheit](#security-tab)
   * Registerkarte [Katalogverwaltung](#catalog-management-tab)
   * Registerkarte [Anfrage-Attribute](#request-attributes-tab)
   * Registerkarte [Allgemeine Attribute für Miniaturansichten](#common-thumbnail-attributes-tab)
   * Registerkarte [Farb-Management-Attribute](#color-management-attributes-tab)

   ![Seite mit den Dynamic Media-Veröffentlichungseinstellungen](/help/assets/assets-dm/dm-publish-setup.png)
   *Seite „Dynamic Media-Veröffentlichungseinstellungen“ mit ausgewählter Registerkarte **[!UICONTROL Anfrage-Attribute]**.*<br><br>

1. Wenn Sie fertig sind, wählen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Speichern]** aus. 

## Image-Server {#image-server}

Auf der Seite „Image-Server“ werden Standardeinstellungen für die Bereitstellung von Bildern von Image-Servern festgelegt. Einstellungen sind in fünf Kategorien verfügbar

| Veröffentlichungskontext | Beschreibung |
| --- | --- |
| Bereitstellung von Bildern | Gibt den Kontext für Veröffentlichungseinstellungen an. |
| Bereitstellung von Testbildern | Gibt den Kontext für das Testen von Veröffentlichungseinstellungen an.<br>Nur für neue Dynamic Media-Konten wird das Feld **[!UICONTROL Client-Adresse]** standardmäßig automatisch auf `127.0.0.1` gesetzt.<br>Siehe [Testen von Assets, bevor sie veröffentlicht werden](#test-assets-before-making-public). |

### Registerkarte „Sicherheit“ {#security-tab}

**[!UICONTROL Client-Adresse]**: Hier können Sie eine oder mehrere IP-Adressen oder IP-Adressbereiche angeben. Wenn diese Option angegeben ist, werden Anfragen an diesen Bildkatalog abgelehnt, wenn sie von einem Client stammen, der eine nicht aufgeführte IP-Adresse hat. Diese Regel gilt sowohl für die Bereitstellung von Bildern als auch für gerenderte Bilder.

![Registerkarte „Sicherheit“](/help/assets/assets-dm/dm-ipallowlist.png)<br>*Die Registerkarte „Sicherheit“ zeigt das Feld „IP zulassen“.*

### Registerkarte „Katalogverwaltung“ {#catalog-management-tab}

**[!UICONTROL Dateipfad für Definitionsregeln]**: Gibt die Datei an, die die Regelsatzdefinitionen für den Bildkatalog enthält.

Siehe auch [RuleSetFile](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-rulesetfile.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch.

>[!NOTE]
>
>Wenn für Ihr Dynamic Media Classic-Konto bereits ein **[!UICONTROL Dateipfad für Regelsatzdefinitionen]** ausgewählt ist (wie in der Gruppe **[!UICONTROL Katalogverwaltung]** unter **[!UICONTROL Einrichtung]** > **[!UICONTROL Anwendung]** > **[!UICONTROL Veröffentlichungseinstellungen]** festgelegt), ruft Ihr Dynamic Media-Konto in Experience Manager die Datei von Dynamic Media Classic ab. Die Datei wird dann gespeichert und in diesem Feld verfügbar gemacht, wenn Sie die **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]** zum ersten Mal öffnen.

### Registerkarte „Anfrage-Attribute“ {#request-attributes-tab}

Diese Einstellungen beziehen sich auf das standardmäßige Erscheinungsbild von Bildern.

| Einstellung | Beschreibung |
| --- | --- |
| **[!UICONTROL Maximale Größe des Antwortbildes]** | Erforderlich.<br>Nur für neue Dynamic Media-Konten wird die Standardgrößenbeschränkung automatisch auf „Breite: `3000`“ und „Höhe: `3000`“ sowohl für **[!UICONTROL Bildbereitstellung]** als auch für **[!UICONTROL Testbildbereitstellung]** festgelegt.<br>Gibt die maximale Breite und Höhe des Antwortbildes an, das an den Client zurückgegeben wird. Der Server gibt einen Fehler zurück, wenn eine Anfrage zu einem Antwortbild führt, dessen Breite und/oder Höhe größer als diese Einstellung ist.<br>Siehe auch den Parameter [MaxPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Verschleierungsmodus für Anfragen]** | Aktivieren Sie diese Option, wenn die base64-Codierung auf gültige Anfragen angewendet werden soll.<br>Siehe auch den Parameter [RequestObfuscation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestobfuscation.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Verschlüsselungsmodus für Anfragen]** | Aktivieren Sie diese Option, wenn in Anfragen eine einfache Hash-Sperre enthalten sein soll.<br>Siehe auch den Parameter [RequestLock](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestlock.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardattribute für Anfragen]** |  |
| **[!UICONTROL Standarderweiterung für Bilddatei]** | Erforderlich.<br>Standard-Datendateierweiterung, die an die Werte für Katalogpfad und Maskenpfad angehängt wird, wenn der Pfad keine Dateiendung enthält.<br>Siehe auch den Parameter [DefaultExt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultext.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Name der Standardschriftart]** | Gibt an, welche Schriftart verwendet wird, wenn keine Schriftart durch eine Textebenenanforderung bereitgestellt wird. Falls angegeben, muss es sich um einen gültigen Schriftnamenwert in der Schriftartenkarte dieses Bildkatalogs oder in der Schriftartenkarte des Standardkatalogs handeln.<br>Siehe auch den Parameter [DefaultFont](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultfont.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardbild]** | Legt fest, welches Standardbild angezeigt werden soll, wenn ein angefordertes Bild nicht gefunden werden kann.<br>Siehe auch den Parameter [DefaultImage](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-defaultimage.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch.<br>**HINWEIS**: Wenn für Ihr Dynamic Media Classic-Konto bereits ein **[!UICONTROL Standardbild]** ausgewählt ist (wie in der Gruppe **[!UICONTROL Standard-Anfrage-Attribute]** unter **[!UICONTROL Einrichtung]** > **[!UICONTROL Anwendung]** > **[!UICONTROL Veröffentlichungseinstellungen]** festgelegt), ruft Ihr Dynamic Media-Konto in Experience Manager die Datei von Dynamic Media Classic ab. Die Datei wird dann gespeichert und in diesem Feld verfügbar gemacht, wenn Sie die **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]** zum ersten Mal öffnen. |
| **[!UICONTROL Standardbildmodus]** | Wenn das Schiebereglerfeld aktiviert ist (Schieberegler auf der rechten Seite), ersetzt **[!UICONTROL Standardbild]** jede fehlende Ebene im Quellbild durch das Standardbild und gibt die Kombination wie gewohnt zurück. Wenn das Regler-Feld deaktiviert ist (Regler links), ersetzt das Standardbild das gesamte zusammengesetzte Bild, selbst wenn das fehlende Bild nur eine von mehreren Ebenen ist.<br>Siehe auch den Parameter [DefaultImageMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultimagemode.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Ansichtsgröße]** | Erforderlich.<br>Nur für neue Dynamic Media-Konten wird die standardmäßige Ansichtsgröße automatisch auf „Breite: `1280`“ und „Höhe: `1280`“ sowohl für **[!UICONTROL Bildbereitstellung]** als auch für **[!UICONTROL Testbildbereitstellung]** festgelegt.<br>Der Server schränkt Antwortbilder dahingehend ein, dass sie nicht größer sind als diese Breite und Höhe, wenn die Anfrage die Anzeigegröße nicht explizit mithilfe von `wid=`, `hei=` oder `scl=` angibt.<br>Siehe auch den Parameter [DefaultPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardgröße für Miniaturansichten]** | Erforderlich.<br>Wird anstelle des Attributs **[!UICONTROL Standardansichtsgröße]** für Miniaturanfragen (`req=tmb`) verwendet. Der Server schränkt Antwortbilder dahingehend ein, dass sie nicht größer sind als diese Breite und Höhe, wenn eine Miniaturbildanforderung (`req=tmb`) die Größe nicht explizit mithilfe von `wid=`, `hei=` oder `scl=` angibt.<br>Siehe auch den Parameter [DefaultThumbPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Hintergrundfarbe]** | Gibt den RGB-Wert an, mit dem alle Bereiche des Antwortbildes gefüllt werden, die keine Bilddaten enthalten.<br>Siehe auch den Parameter [BkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Attribute für JPEG-Codierung]** |  |
| **[!UICONTROL Qualität]** | <br>Legt die Standardattribute von JPEG-Antwortbildern fest.<br>Nur für neue Dynamic Media-Konten wird der Standardwert der **[!UICONTROL Qualität]** automatisch auf `80` sowohl für **[!UICONTROL Bildbereitstellung]** als auch für **[!UICONTROL Testbildbereitstellung]** festgelegt.<br>Dieses Feld wird im Bereich von 1 bis 100 definiert.<br>Siehe auch den Parameter [JpegQuality](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Chromatisches Downsampling]** | Aktiviert oder deaktiviert die Neuberechnung der Farbwiedergabe, die von JPEG-Codierern verwendet wird. |
| **[!UICONTROL Standard-Resampling-Modus]** | Gibt die standardmäßigen Resampling- und Interpolationsattribute an, die für die Skalierung von Bilddaten verwendet werden. Verwenden Sie dies, wenn `resMode` in einer Anforderung nicht angegeben wird.<br>Nur für neue Dynamic Media-Konten wird der standardmäßige Resampling-Modus automatisch auf `Sharp2` sowohl für **[!UICONTROL Bildbereitstellung]** als auch für **[!UICONTROL Testbildbereitstellung]** festgelegt.<br>Siehe auch den Parameter [ResMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |

### Registerkarte „Allgemeine Attribute für Miniaturansichten“ {#common-thumbnail-attributes-tab}

Diese Einstellungen beziehen sich auf die standardmäßige Darstellung und Ausrichtung von Miniaturansichten.

| Einstellung | Beschreibung |
| --- | --- |
| **[!UICONTROL Standardhintergrundfarbe für Miniaturansicht]** | Gibt den RGB-Wert an, der zum Ausfüllen des Bereichs eines Ausgabeminiaturbilds verwendet wird, das keine tatsächlichen Bilddaten enthält. Wird nur für Anforderungen von Miniaturansichten (`req=tmb`) verwendet und wenn der **[!UICONTROL Standardtyp für Miniaturansichten]** auf **[!UICONTROL Anpassen]** oder **[!UICONTROL Textur]** festgelegt ist.<br>Siehe auch den Parameter [ThumbBkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbbkgcolor.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Horizontale Ausrichtung]** | Gibt die horizontale Ausrichtung des Miniaturbilds im Rechteck des Antwortbilds an, angegeben durch die Werte `wid=` und `hei=`.<br>Wird nur für Anforderungen von Miniaturansichten (`req=tmb`) verwendet und wenn der **[!UICONTROL Standardtyp für Miniaturansichten]** auf **[!UICONTROL Anpassen]** festgelegt ist.<br>Es gibt drei horizontale Ausrichtungen zur Auswahl: **[!UICONTROL Ausrichtung zentriert]**, **[!UICONTROL Linksbündig]** und **[!UICONTROL Rechtsbündig]**.<br>Siehe auch den Parameter [ThumbHorizAlign](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbhorizalign.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Vertikale Ausrichtung]** | Gibt die vertikale Ausrichtung des Miniaturbilds im Rechteck des Antwortbilds an, angegeben durch die Werte `wid=` und `hei=`. Wird nur für Anforderungen von Miniaturansichten (`req=tmb`) verwendet und wenn der **[!UICONTROL Standardtyp für Miniaturansichten]** auf **[!UICONTROL Anpassen]** festgelegt ist.<br>Es gibt drei vertikale Ausrichtungen zur Auswahl: **[!UICONTROL Ausrichtung oben]**, **[!UICONTROL Ausrichtung zentriert]** und **[!UICONTROL Ausrichtung unten]**.<br>Siehe auch [ThumbVertAlign](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbvertalign.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standard-Gültigkeitsdauer für Cache]** | Bietet ein standardmäßiges Ablaufintervall in Stunden für den Fall, dass ein bestimmter Katalogdatensatz kein gültiges Katalogablaufdatum aufweist. Legen Sie die Einstellung auf `-1` fest, damit es keinen Ablauf gibt. <br>Siehe auch den Parameter [Ablauf](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardtyp für Miniaturansichten]** | Bietet einen Standard für den Typ von Miniaturansichten für den Fall, dass ein bestimmter Katalogdatensatz keinen gültigen ThumbType-Katalogwert aufweist. Wird nur für Anfragen von Miniaturansichten verwendet (`req=tmb`).<br>Es gibt drei Typen von Miniaturansichten, aus denen Sie wählen können: **[!UICONTROL Zuschneiden]**, **[!UICONTROL Anpassen]** und **[!UICONTROL Textur]**.<br>Siehe auch [ThumbType-Parameter](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbtype.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Standardauflösung für Miniaturansichten]** | Bietet einen Standard für die Objektauflösung für Miniaturansichten für den Fall, dass ein bestimmter Katalogdatensatz keinen gültigen ThumbRes-Katalogwert aufweist. Wird nur für Anfragen von Miniaturansichten verwendet (`req=tmb`) und wenn die Einstellung **[!UICONTROL Standardtyp für Miniaturansichten]** auf **[!UICONTROL Textur]** festgelegt ist.<br>Siehe auch [ThumbRes-Parameter](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbres.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |

### Registerkarte „Farbmanagement-Attribute“ {#color-management-attributes-tab}

Diese Einstellungen bestimmen, welche ICC-Farbprofile für Bilder verwendet werden.

**Rendering-Intent für Farbkonvertierung**
Ein Rendering-Intent für die Farbkonvertierung ermöglicht das Überschreiben des standardmäßigen Rendering-Intents der Arbeitsprofile, um zu bestimmen, wie die Quellfarben angepasst werden. Verwendung:

1. Eines der standardmäßigen ICC-Profile ist der Zielfarbraum einer Farbkonvertierung.
1. Ein Ausgabegerät (Drucker oder Monitor) ist durch dieses Profil gekennzeichnet.
1. Der angegebene Rendering-Intent ist für dieses Profil gültig.

Verschiedene Rendering-Intents verwenden unterschiedliche Regeln, um zu bestimmen, wie die Quellfarben angepasst werden.

Siehe auch [IccRenderIntent-Parameter](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch.

>[!NOTE]
>
>Im Allgemeinen ist es am besten, den standardmäßigen Rendering-Intent für die ausgewählte Farbeinstellung zu verwenden. Dieser wurde von Adobe auf die Einhaltung von Branchenstandards getestet. Wenn Sie beispielsweise eine Farbeinstellung für Nordamerika oder Europa auswählen, lautet der standardmäßige Rendering-Intent der Farbkonvertierung **[!UICONTROL Relativ farbmetrisch]**. Wenn Sie eine Farbeinstellung für Japan auswählen, lautet der standardmäßige Rendering-Intent der Farbkonvertierung **[!UICONTROL Wahrnehmungsoptimiert]**.

| Einstellung | Merkmale |
| --- | --- |
| **[!UICONTROL CMYK-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für CMYK-Daten verwendet werden soll. Wenn **[!UICONTROL Keine Angabe]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn CMYK-Quellbilder verwendet werden. Alle CMYK-Arbeitsbereiche sind geräteabhängig, sie basieren also auf tatsächlichen Tinten- und Papierkombinationen. Die von Adobe bereitgestellten CMYK-Arbeitsbereiche basieren auf den üblichen kommerziellen Druckbedingungen.<br> Siehe auch [IccProfileCMYK-Parameter](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Graustufen-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für Graustufendaten verwendet werden soll. Wenn **[!UICONTROL Keine Angabe]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn Quellbilder mit Graustufen verwendet werden.<br>Siehe auch [IccProfileGray-Parameter](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL RGB-Standardfarbraum]** | Gibt den Namen des ICC-Farbprofils an, das als Arbeitsprofil für RGB-Daten verwendet werden soll. Wenn **[!UICONTROL Keine Angabe]** ausgewählt ist, wird das Farbmanagement für diesen Bildkatalog deaktiviert, wenn RGB-Quellbilder verwendet werden. Im Allgemeinen ist es am besten, **[!UICONTROL Adobe RGB]** oder **[!UICONTROL sRGB]** statt des Profils für ein bestimmtes Gerät (z. B. ein Monitorprofil) auszuwählen. **[!UICONTROL sRGB]** wird empfohlen, wenn Sie Bilder für das Internet oder mobile Geräte vorbereiten, da dadurch der Farbraum des Standardmonitors definiert wird, der zum Anzeigen von Bildern im Internet verwendet wird. **[!UICONTROL sRGB]** ist auch eine gute Wahl, wenn Sie mit Bildern von handelsüblichen Digitalkameras arbeiten, da die meisten dieser Kameras sRGB als Standardfarbraum verwenden.<br>Siehe auch [IccProfileRGB-Parameter](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch. |
| **[!UICONTROL Rendering-Intent für Farbkonvertierung]** | **[!UICONTROL Wahrnehmungsorientiert]** - Ziel ist, die visuelle Beziehung zwischen Farben so zu erhalten, dass sie für das menschliche Auge als natürlich wahrgenommen werden, auch wenn die Farbwerte selbst sich ändern können. Dieser Intent eignet sich für fotografische Bilder mit vielen Farben, die außerhalb der Farbskala liegen. Diese Einstellung ist der standardmäßige Rendering-Intent für die japanische Druckindustrie. |
|  | **[!UICONTROL Relativ farbmetrisch]** – Vergleicht die extreme Hervorhebung des Quellfarbraums mit der des Zielfarbraums und verschiebt alle Farben entsprechend. Die Farben außerhalb der Farbskala werden zur nächstmöglichen reproduzierbaren Farbe im Zielfarbraum verschoben. Mit „Relativ farbmetrisch“ erhalten Sie mehr Originalfarben in einem Bild als mit „Wahrnehmungsoptimiert“. Diese Einstellung ist der standardmäßige Rendering-Intent beim Drucken in Nordamerika und Europa. |
|  | **[!UICONTROL Sättigung]** – Versucht, auf Kosten der Farbgenauigkeit lebendige Farben in einem Bild zu produzieren. Dieser Rendering-Intent eignet sich für Geschäftsgrafiken wie Diagrammen, bei denen helle gesättigte Farben wichtiger sind als die exakte Beziehung zwischen Farben. |
|  | **[!UICONTROL Absolut farbmetrisch]**: Lässt Farben, die sich im Zielfarbraum befinden, unverändert. Farben außerhalb des Farbraums werden abgeschnitten. Es wird keine Skalierung der Farben auf den Ziel-Weißpunkt durchgeführt. Diese Absicht dient der Einhaltung der Farbgenauigkeit auf Kosten der Beibehaltung von Beziehungen zwischen Farben und ist für Korrekturabzüge geeignet, die die Ausgabe eines bestimmten Geräts simulieren. Dieser Zweck ist nützlich für die Vorschau, wie die Papierfarbe sich auf die gedruckten Farben auswirkt. |

## Testen von Assets vor der Veröffentlichung {#test-assets-before-making-public}

Mit Secure Testing können Sie eine sichere Testumgebung definieren und eine robuste Business-to-Business-Lösung erstellen, die auf einem konfigurierbaren Satz von IP-Adressen und -Bereichen basiert. Mit dieser Funktion können Sie Ihre Adobe Dynamic Media-Implementierungen mit der Architektur Ihres Content-Management- und Business-Systems abgleichen.

Mit Secure Testing können Sie eine Vorschau der Staging-Version der Website mit unveröffentlichten Inhalten anzeigen.

Aus den folgenden Gründen sollten Sie bei Bedarf eine Staging-Umgebung erstellen, anstatt Assets öffentlich verfügbar zu machen:

* Vorschau von Websites vor dem öffentlichen Start (Staging-Website).
* Bereitstellen von Assets, die eingeschränkten Zugriff erfordern, wie z. B. E-Kataloge, die Preise in einer B2B-Web-Anwendung anzeigen.
* Verwenden von Assets hinter einer Firewall als Teil des Produktinformations-Management-Systems, der dem Kunden-Service-Programm, der Schulungs-Website usw.

>[!NOTE]
>
>Secure Testing hat keine Auswirkungen auf den Zugriff auf Adobe Dynamic Media Classic. Die Adobe Dynamic Media Classic-Sicherheit bleibt konsistent und erfordert die üblichen Anmeldeinformationen für den Zugriff auf Adobe Dynamic Media Classic und zugehörige Web-Services.

### Funktionsweise von Secure Testing {#how-test-assets-works}

Die meisten Unternehmen betreiben ihr Internet hinter einer Firewall. Der Zugang zum Internet ist über bestimmte Routen und in der Regel über eine begrenzte Anzahl öffentlicher IP-Adressen möglich.

Über Ihr Unternehmensnetzwerk können Sie mithilfe von Websites wie [https://www.whatismyip.com](https://www.whatismyip.com/de/) Ihre IP-Adresse in Erfahrung bringen oder Sie fordern diese Information einfach von Ihrem IT-Unternehmen an.

Mit Secure Testing richtet Adobe Dynamic Media einen dedizierten Image-Server für Staging-Umgebungen oder interne Programme ein. Mit einer beliebigen Anfrage an diesen Server wird die Ursprung-IP-Adresse geprüft. Wenn die eingehende Anfrage nicht in der Liste genehmigter IP-Adressen enthalten ist, erfolgt die Antwort mit einer Fehlermeldung. Der Dynamic Media-Unternehmensadministrator konfiguriert die Liste genehmigter IP-Adressen für die sichere Testumgebung seines Unternehmens.

Da der Ort der ursprünglichen Anfrage bestätigt werden muss, wird der Traffic des Secure Testing-Services nicht über ein Inhaltsverteilungsnetzwerk geleitet, wie der öffentliche Traffic des Dynamic Media Image Servers. Anfragen an den Secure Testing-Service weisen im Vergleich zu den öffentlichen Dynamic Media-Bild-Servern eine etwas höhere Latenz auf.

Nicht veröffentlichte Assets sind sofort über die Secure Testing-Services verfügbar, ohne dass sie veröffentlicht werden müssen. Auf diese Weise können Sie eine Vorschau ausführen, bevor Assets auf ihrem öffentlichen Bild-Server veröffentlicht werden.

>[!NOTE]
>
>Secure Testing-Services verwenden den Katalog-Server, der mit einem internen Veröffentlichungskontext konfiguriert ist. Wenn Ihr Unternehmen für die Veröffentlichung auf Secure Testing konfiguriert ist, werden daher hochgeladene Assets in Adobe Dynamic Media sofort in den Secure Testing-Services verfügbar. Diese Funktionen gelten unabhängig davon, ob die Assets beim Hochladen zur Veröffentlichung markiert sind.

Secure Testing-Services unterstützen derzeit die folgenden Asset-Typen und -Funktionen:

* Bilder.
* Vignetten (Rendering-Server-Anfragen).
* Rendering-Server-Anfragen (werden unterstützt, müssen aber explizit vom Kunden angefragt werden).
* Sets, einschließlich Bildsets, E-Katalog, Rendering-Sets und Mediensets.
* Standardmäßige Adobe Dynamic Media-Rich-Media-Viewer.
* Adobe Dynamic Media-On-Demand-JSP-Seiten.
* Statische Inhalte wie PDF-Dateien und progressiv bereitgestellte Videos.
* HTTP-Video-Streaming.
* Progressives Video-Streaming.

Die folgenden Asset-Typen und -Funktionen werden derzeit nicht unterstützt:

* Adobe Dynamic Media Classic-Info- oder E-Katalog-Suche
* RTMP-Video-Streaming
* Web-to-Print
* UGC-Services (benutzergenerierte Inhalte)

   >[!IMPORTANT]
   >
   >Ab dem 1. Mai 2023 stehen UGC-Assets in Dynamic Media bis zu 60 Tage ab dem Datum des Uploads zur Verfügung. Nach 60 Tagen werden die Assets entfernt.

   >[!NOTE]
   >
   >Die Unterstützung für neue oder vorhandene UGC-Vektorbild-Assets in Adobe Dynamic Media wurde am 30. September 2021 eingestellt.

### Testen des Secure Testing-Services {#test-secure-testing-service}

Gehen Sie wie folgt vor, um sicherzustellen, dass der Secure Testing-Service erwartungsgemäß funktioniert:

#### Bereiten Sie Ihr Konto vor

1. Wenden Sie sich an die Kundenunterstützung von Adobe und bitten Sie sie, Secure Testing für Ihr Konto zu aktivieren.
1. Wählen Sie in Adobe Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Veröffentlichungseinstellungen für Dynamic Media]**.
1. Wählen Sie auf der Seite „Image-Server“ in der Dropdown-Liste **[!UICONTROL Veröffentlichungskontext]** die Option **[!UICONTROL Image-Serving testen]** aus.
1. Wählen Sie die Registerkarte **[!UICONTROL Sicherheit]**.
1. Wählen Sie für den Filter **[!UICONTROL Client-Adresse]** die Option **[!UICONTROL Hinzufügen]**.
1. Geben Sie in das Feld **[!UICONTROL IP-Adresse]** eine IP-Adresse ein.
1. Geben Sie in das Feld **[!UICONTROL Maske]** eine Netzmaske ein.

   >[!NOTE]
   >
   >Wenn Sie mehr als eine IP-Adresse und Netzmaske hinzufügen, ermöglicht dies effektiv *allen* IP-Adressen, Asset-Aufrufe durchzuführen, und sie werden alle angezeigt.

1. Führen Sie einen der folgenden Schritte aus:

   * Um weitere IP-Adressen hinzuzufügen, wiederholen Sie die drei vorherigen Schritte.
   * Fahren Sie mit dem nächsten Schritt fort.

1. Klicken Sie in der rechten oberen Ecke der Seite „Image-Server“ auf **[!UICONTROL Speichern]**.
1. Laden Sie die gewünschten Bilder in Ihr Adobe Dynamic Media-Konto hoch.

<!--    See [Upload files](uploading-files.md#uploading_files). -->

1. Stellen Sie sicher, dass einige der Bilder zur Veröffentlichung markiert und andere nicht markiert sind, und senden Sie dann den Veröffentlichungsauftrag.

<!--    See [Publish files](publishing-files.md#publishing_files). -->

1. Bestimmen Sie den Namen Ihres Secure Testing-Services, indem Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Allgemeine Dynamic Media-Einstellungen]** gehen.
1. Suchen Sie auf der Seite **[!UICONTROL Server]** den Server-Namen rechts neben **[!UICONTROL Veröffentlichungs-Server-Name]**.

Wenden Sie sich an die Adobe-Kundenunterstützung, wenn der Servername fehlt oder die URL zum Server nicht funktioniert.

#### Vorbereiten von Website-Varianten

Sie benötigen zwei Varianten einer Website, auf der einmal die veröffentlichten und einmal die nicht veröffentlichten Assets verknüpft sind:

* Öffentliche Version: Verknüpfen Sie Assets mithilfe Ihrer üblichen URL-Syntax von Adobe Dynamic Media.
* Staging-Version: Verknüpfen Sie Assets mithilfe derselben Syntax, aber mit dem Namen der Secure Testing-Site.

#### Ausführen der Tests

Führen Sie die folgenden Tests durch:

1. Überprüfen Sie, ob Assets in Ihrem Unternehmensnetzwerk sichtbar sind.

   Innerhalb des Unternehmensnetzwerks, das durch den zuvor definierten IP-Adressbereich identifiziert wurde, zeigt die Staging-Version der Website alle Bilder an, unabhängig davon, ob sie zur Veröffentlichung markiert wurden oder nicht. Daher können Sie hier Tests durchführen, ohne Bilder versehentlich vor der Genehmigung der Vorschau oder dem Produktstart verfügbar zu machen.

   Vergewissern Sie sich, dass die öffentliche Version Ihrer Site veröffentlichte Assets anzeigt, wie Sie es bereits von Adobe Dynamic Media gewohnt sind.

1. Vergewissern Sie sich von außerhalb Ihres Unternehmensnetzwerks, dass nicht veröffentlichte (d. h. nicht zur Veröffentlichung markierte) Assets vor dem Zugriff Dritter geschützt sind.

   Greifen Sie dazu von außerhalb auf Ihr Netzwerk zu (z. B. von Ihrem privaten Computer oder über eine 4G/5G-Verbindung) und überzeugen Sie sich davon, dass in der öffentlichen Version der Site alle veröffentlichten Assets, aber keine unveröffentlichten Inhalte angezeigt werden.

   Vergewissern Sie sich, dass in der Staging-Version kein Asset angezeigt wird, da Sie von einer nicht genehmigten IP-Adresse aus auf den Secure Testing-Service zugreifen.
