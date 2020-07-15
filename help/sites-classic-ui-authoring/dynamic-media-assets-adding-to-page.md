---
title: Hinzufügen von Dynamic Media-Assets zu Seiten
seo-title: Hinzufügen von Dynamic Media-Assets zu Seiten
description: Um die Funktionen für dynamische Medien zu Assets hinzuzufügen, die Sie auf Ihren Websites verwenden möchten, können Sie die Komponente „Dynamische Medien“ oder „Interaktive Medien“ direkt auf der Seite hinzufügen.
seo-description: Um die Funktionen für dynamische Medien zu Assets hinzuzufügen, die Sie auf Ihren Websites verwenden möchten, können Sie die Komponente „Dynamische Medien“ oder „Interaktive Medien“ direkt auf der Seite hinzufügen.
uuid: 650d0867-a079-4936-a466-55b7a30803a2
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 331f4980-5193-4546-a22e-f27e38bb8250
translation-type: tm+mt
source-git-commit: 23dfcc944a83dd683078cfe00f85c4cc734e7752
workflow-type: tm+mt
source-wordcount: '1723'
ht-degree: 57%

---


# Hinzufügen von Dynamic Media-Assets zu Seiten{#adding-dynamic-media-assets-to-pages}

To add the Dynamic Media functionality to assets you use on your websites, you can add the **[!UICONTROL Dynamic Media]** or **[!UICONTROL Interactive Media]** component directly on the page. You do this by entering [!UICONTROL Design] mode and enabling the dynamic media components. Anschließend können Sie der Seite diese Komponenten und der Komponente Assets hinzufügen. „Dynamische Medien“ und „Interaktive Medien“ sind intelligente Komponenten, die erkennen, ob Sie ein Bild oder ein Video hinzufügen. Die verfügbaren Optionen werden entsprechend angepasst.

Sie können dynamische Medienelemente direkt zur Seite hinzufügen, wenn Sie AEM als WCM verwenden.

>[!NOTE]
>
>Imagemaps sind für Karussellbanner umgehend verfügbar.

## Hinzufügen einer Dynamic Media-Komponente zu einer Seite         {#adding-a-dynamic-media-component-to-a-page}

Adding the [!UICONTROL Dynamic Media] or [!UICONTROL Interactive Media] component to a page is the same as adding a component to any page. The [!UICONTROL Dynamic Media] and [!UICONTROL Interactive Media] components are described in detail in the following sections.

So fügen Sie einer Seite eine Komponente bzw. einen Viewer vom Typ „Dynamische Medien“ hinzu:

1. Öffnen Sie in AEM die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. If no Dynamic Media component is available, click the ruler in the [!UICONTROL Sidekick] to enter **[!UICONTROL Design]** mode, click **[!UICONTROL Edit]** parsys, and select **[!UICONTROL Dynamic Media]** to make the Dynamic Media components available.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](/help/sites-authoring/default-components-designmode.md).

1. Return to **[!UICONTROL Edit]** mode by clicking the pencil icon in the [!UICONTROL Sidekick].
1. Drag the **[!UICONTROL Dynamic Media]** or **[!UICONTROL Interactive Media]** component from the **[!UICONTROL Other]** group in the sidekick onto the page in the desired location.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu öffnen.
1. [](#dynamic-media-component)Bearbeiten Sie die Komponente bei Bedarf und klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

## Komponenten vom Typ „Dynamische Medien“{#dynamic-media-components}

[!UICONTROL Dynamic Media] und [!UICONTROL interaktive Medien] sind im [!UICONTROL Sidekick] unter **[!UICONTROL Dynamic Media verfügbar.]** Verwenden Sie die Komponente **[!UICONTROL Interaktive Medien]** für beliebige interaktive Assets wie interaktive Videos, interaktive Bilder oder Karussell-Sets. Verwenden Sie für alle anderen Komponenten vom Typ „Dynamische Medien“ die Komponente **[!UICONTROL Dynamische Medien]**.

![chlimage_1-71](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar und müssen im Designmodus ausgewählt werden, bevor sie verwendet werden können. [Nachdem sie im Designmodus zur Verfügung gestellt wurden](/help/sites-authoring/default-components-designmode.md), können Sie die Komponenten wie jede andere AEM-Komponente Ihrer Seite hinzufügen.

### Komponente „Dynamische Medien“{#dynamic-media-component}

Die Komponente &quot;Dynamic Media&quot;ist intelligent. Je nachdem, ob Sie ein Bild oder ein Video hinzufügen, stehen Ihnen verschiedene Optionen zur Verfügung. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bild-Sets sowie Rotations-Sets, Sets für gemischte Medien und Videos. Darüber hinaus reagiert der Viewer. Das heißt, die Bildschirmgröße ändert sich automatisch je nach Bildschirmgröße. Alle Viewer sind HTML5-basierte Viewer.

>[!NOTE]
>
>When you add the [!UICONTROL Dynamic Media] component, and **[!UICONTROL Dynamic Media Settings]** is blank or you cannot add an asset properly, check the following:
>
>* Sie [Dynamic Media aktiviert](/help/assets/config-dynamic.md) haben. Dynamic Media ist standardmäßig deaktiviert.
>* das Bild eine Pyramid TIFF-Datei aufweist. Bilder, die vor der Aktivierung von dynamischen Medien importiert wurden, verfügen nicht über eine Pyramid TIFF-Datei.

>



#### Arbeiten mit Bildern         {#when-working-with-images}

The [!UICONTROL Dynamic Media] component lets you add dynamic images, including image sets, spin sets, and mixed media sets. Sie können Vergrößerungen sowie Verkleinerungen vornehmen und (sofern zutreffend) ein Bild in einem Rotations-Set drehen oder ein Bild aus einem anderen Set auswählen.

Sie können zudem die Viewer-Vorgabe, Bildvorgabe oder das Bildformat direkt in der Komponente konfigurieren. Um ein Bild dynamisch zu machen, können Sie die Haltepunkte festlegen oder eine dynamische Bildvorgabe anwenden.

![chlimage_1-72](assets/chlimage_1-72a.png)

You can edit the following Dynamic Media settings by clicking **[!UICONTROL Edit]** in the component and then clicking the **[!UICONTROL Dynamic Media Settings]** tab.

![chlimage_1-73](assets/chlimage_1-73a.png)

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für dynamische Medien adaptiv. If you want to make it a fixed size, set it in the component in the **[!UICONTROL Advanced]** tab with the **[!UICONTROL Width]** and **[!UICONTROL Height]** properties.

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

Dies ist die einzig verfügbare Option beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien. Die angezeigten Viewer-Vorgaben sind ebenfalls intelligent - es werden nur relevante Viewer-Vorgaben angezeigt.

**[!UICONTROL Bildvorgabe]** : Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Bildmodifikatoren]** : Sie können Bildeffekte ändern, indem Sie zusätzliche Bildbefehle bereitstellen. These are described in [Managing Image Presets](/help/assets/managing-viewer-presets.md) and the [Command reference](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Haltepunkte]** : Wenn Sie dieses Asset auf einer responsive Site verwenden, müssen Sie die Seitenumbruchpunkte hinzufügen. Bildhaltepunkte müssen durch Kommas (,) voneinander getrennt werden. Diese Option kann verwendet werden, wenn in einer Bildvorgabe keine Höhe oder Breite festgelegt ist.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

You can edit the following [!UICONTROL Advanced Settings] by clicking **[!UICONTROL Edit]** in the component.

**[!UICONTROL Titel]** : Ändern Sie den Titel des Bilds.

**[!UICONTROL Alt-Text]** - Hinzufügen ein Titel für die Benutzer, die Grafiken deaktiviert haben.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL URL, Öffnen in]** - Sie können ein Asset vom zum Öffnen eines Links festlegen. Set the **[!UICONTROL URL]** and **[!UICONTROL Open in]** to indicate whether you want it to open in the same window or a new window.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Breite und Höhe]** - Geben Sie den Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

#### When working with video {#when-working-with-video}

Use the [!UICONTROL Dynamic Media] component to add dynamic video to your web pages. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

![chlimage_1-74](assets/chlimage_1-74a.png)

You can edit the following [!UICONTROL Dynamic Media Settings] by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Die Videokomponente für Dynamic Media ist standardmäßig adaptiv. Wenn sie eine feste Größe aufweisen soll, müssen Sie dies in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** festlegen.

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie eine vorhandene Video-Viewer-Vorgabe aus dem Dropdown-Menü. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

You can edit the following [!UICONTROL Advanced] settings by clicking **[!UICONTROL Edit]** in the component.

**[!UICONTROL Titel]** - Ändern Sie den Titel des Videos.

**[!UICONTROL Breite und Höhe]** - Geben Sie den Wert in Pixel ein, wenn das Video eine feste Größe haben soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

#### Sichere Videowiedergabe {#how-to-delivery-secure-video}

Wenn Sie in AEM 6.2 [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480) installieren, können Sie festlegen, ob ein Video über eine sichere SSL-Verbindung (HTTPS) oder eine unsichere Verbindung (HTTP) wiedergegeben wird. Standardmäßig wird automatisch das Videowiedergabeprotokoll der Webseite übernommen, in die das Video eingebettet wird. Wenn die Webseite über HTTPS geladen wird, wird das Video ebenfalls über HTTPS wiedergegeben. Umgekehrt wird das Video über HTTP wiedergegeben, wenn die Webseite HTTP verwendet. In den meisten Fällen ist dieses Verhalten korrekt und es müssen keine Konfigurationsänderungen vorgenommen werden. Sie können dieses Standardverhalten jedoch außer Kraft setzen, indem Sie `VideoPlayer.ssl=on` am Ende des URL-Pfades oder zur Liste weiterer Viewer-Konfigurationsparameter in einem Embed-Code-Snippet hinzufügen, um eine sichere Videowiedergabe zu erzwingen.

Weitere Informationen zur sicheren Videowiedergabe sowie zur Verwendung des Konfigurationsattributs `VideoPlayer.ssl` in Ihrem URL-Pfad finden Sie im Referenzhandbuch zu den Viewern unter [Sichere Videowiedergabe](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html). Abgesehen vom Video-Viewer ist sicherer Video-Versand für den Viewer für gemischte Medien und den Viewer für interaktive Videos verfügbar.

### Komponente für interaktive Medien {#interactive-media-component}

Die Komponente „Interaktive Medien“ ist für Assets mit interaktiven Elementen wie Hotspots oder Imagemaps vorgesehen. Verwenden Sie bei interaktiven Bildern, interaktiven Videos oder Karussellbannern die Komponente **[!UICONTROL Interaktive Medien]**.

The [!UICONTROL Interactive Media] component is smart – depending on whether you add an image or a video, you have various options. Darüber hinaus reagiert der Viewer. Das heißt, die Bildschirmgröße ändert sich automatisch je nach Bildschirmgröße. Alle Viewer sind HTML5-basierte Viewer.

![chlimage_1-75](assets/chlimage_1-75a.png)

Sie können die folgenden allgemeinen Einstellungen **** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Viewer-Vorgaben müssen veröffentlicht werden, bevor sie verwendet werden können. Siehe „Verwalten von Viewer-Vorgaben“.

**[!UICONTROL Titel]** - Ändern Sie den Titel des Videos.

**[!UICONTROL Breite und Höhe]** - Geben Sie den Wert in Pixel ein, wenn das Video eine feste Größe haben soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

You can edit the following **[!UICONTROL Add To Cart** settings by clicking **[!UICONTROL Edit]** in the component.

**[!UICONTROL Produkt-Asset]** anzeigen: Standardmäßig ist dieser Wert ausgewählt. Das Produkt-Asset zeigt ein Bild des Produkts, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um das Produkt-Asset nicht anzuzeigen.

**[!UICONTROL Produktpreis]** anzeigen: Dieser Wert ist standardmäßig ausgewählt. Der Produktpreis gibt den Preis des Artikels an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um den Produktpreis nicht anzuzeigen.

**[!UICONTROL Produktformular]** anzeigen: Standardmäßig ist dieser Wert nicht ausgewählt. Das Produktformular beinhaltet jegliche Produktvarianten, etwa hinsichtlich der Größe und der Farbe. Deaktivieren Sie das Kontrollkästchen, um die Produktvarianten nicht anzuzeigen.
