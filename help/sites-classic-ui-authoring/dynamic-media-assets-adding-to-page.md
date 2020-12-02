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
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '1722'
ht-degree: 60%

---


# Hinzufügen von Dynamic Media-Assets zu Seiten{#adding-dynamic-media-assets-to-pages}

Um die Funktion für dynamische Medien zu Assets hinzuzufügen, die Sie auf Ihren Websites verwenden, können Sie die Komponente **[!UICONTROL Dynamische Medien]** oder **[!UICONTROL Interaktive Medien]** direkt auf der Seite hinzufügen. Dazu geben Sie den Modus [!UICONTROL Design] ein und aktivieren die dynamischen Medienkomponenten. Anschließend können Sie der Seite diese Komponenten und der Komponente Assets hinzufügen. „Dynamische Medien“ und „Interaktive Medien“ sind intelligente Komponenten, die erkennen, ob Sie ein Bild oder ein Video hinzufügen. Die verfügbaren Optionen werden entsprechend angepasst.

Sie können dynamische Medienelemente direkt zur Seite hinzufügen, wenn Sie AEM als WCM verwenden.

>[!NOTE]
>
>Imagemaps sind für Karussellbanner umgehend verfügbar.

## Hinzufügen einer Dynamic Media-Komponente zu einer Seite         {#adding-a-dynamic-media-component-to-a-page}

Das Hinzufügen der Komponente [!UICONTROL Dynamische Medien] oder [!UICONTROL Interaktive Medien] zu einer Seite entspricht dem Hinzufügen einer Komponente zu einer beliebigen Seite. Die Komponenten [!UICONTROL Dynamische Medien] und [!UICONTROL Interaktive Medien] werden in den folgenden Abschnitten ausführlich beschrieben.

So fügen Sie einer Seite eine Komponente bzw. einen Viewer vom Typ „Dynamische Medien“ hinzu:

1. Öffnen Sie in AEM die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Wenn keine Komponente für dynamische Medien verfügbar ist, klicken Sie auf das Lineal im Modus [!UICONTROL Sidekick], um **[!UICONTROL Design]** aufzurufen, klicken Sie auf **[!UICONTROL Bearbeiten]** Parsys und wählen Sie **[!UICONTROL Dynamische Medien]** aus, um die Komponenten für dynamische Medien verfügbar zu machen.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](/help/sites-authoring/default-components-designmode.md).

1. Kehren Sie zum Modus **[!UICONTROL Bearbeiten]** zurück, indem Sie auf das Stiftsymbol in [!UICONTROL Sidekick] klicken.
1. Ziehen Sie die Komponente **[!UICONTROL Dynamische Medien]** oder **[!UICONTROL Interaktive Medien]** aus der Gruppe **[!UICONTROL Andere]** im Sidekick auf die Seite an der gewünschten Position.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu öffnen.
1. [](#dynamic-media-component)Bearbeiten Sie die Komponente bei Bedarf und klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

## Komponenten vom Typ „Dynamische Medien“{#dynamic-media-components}

[!UICONTROL Dynamische ] Medien und  [!UICONTROL interaktive ] Medien sind im   Sidekickunder  **[!UICONTROL Dynamische Medien verfügbar.]** Verwenden Sie die Komponente **[!UICONTROL Interaktive Medien]** für beliebige interaktive Assets wie interaktive Videos, interaktive Bilder oder Karussell-Sets. Verwenden Sie für alle anderen Komponenten vom Typ „Dynamische Medien“ die Komponente **[!UICONTROL Dynamische Medien]**.

![chlimage_1-71](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar und müssen im Designmodus ausgewählt werden, bevor sie verwendet werden können. [Nachdem sie im Designmodus zur Verfügung gestellt wurden](/help/sites-authoring/default-components-designmode.md), können Sie die Komponenten wie jede andere AEM-Komponente Ihrer Seite hinzufügen.

### Komponente „Dynamische Medien“{#dynamic-media-component}

Die Komponente &quot;Dynamische Medien&quot;ist intelligent. Je nachdem, ob Sie ein Bild oder ein Video hinzufügen, stehen Ihnen verschiedene Optionen zur Verfügung. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bild-Sets sowie Rotations-Sets, Sets für gemischte Medien und Videos. Darüber hinaus reagiert der Viewer. Das heißt, die Bildschirmgröße ändert sich automatisch je nach Bildschirmgröße. Alle Viewer sind HTML5-basierte Viewer.

>[!NOTE]
>
>Wenn Sie die Komponente [!UICONTROL Dynamische Medien] hinzufügen und **[!UICONTROL Dynamische Medieneinstellungen]** leer sind oder ein Asset nicht ordnungsgemäß hinzugefügt werden kann, überprüfen Sie Folgendes:
>
>* Sie [Dynamic Media aktiviert](/help/assets/config-dynamic.md) haben. Dynamic Media ist standardmäßig deaktiviert.
>* das Bild eine Pyramid TIFF-Datei aufweist. Bilder, die vor der Aktivierung von dynamischen Medien importiert wurden, verfügen nicht über eine Pyramid TIFF-Datei.

>



#### Arbeiten mit Bildern          {#when-working-with-images}

Mit der Komponente [!UICONTROL Dynamische Medien] können Sie dynamische Bilder hinzufügen, einschließlich Bildsätze, Rotationssets und gemischten Mediensets. Sie können Vergrößerungen sowie Verkleinerungen vornehmen und (sofern zutreffend) ein Bild in einem Rotations-Set drehen oder ein Bild aus einem anderen Set auswählen.

Sie können zudem die Viewer-Vorgabe, Bildvorgabe oder das Bildformat direkt in der Komponente konfigurieren. Um ein Bild dynamisch zu machen, können Sie die Haltepunkte festlegen oder eine dynamische Bildvorgabe anwenden.

![chlimage_1-72](assets/chlimage_1-72a.png)

Sie können die folgenden Einstellungen für dynamische Medien bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken und dann auf die Registerkarte **[!UICONTROL Einstellungen für dynamische Medien]** klicken.

![chlimage_1-73](assets/chlimage_1-73a.png)

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für dynamische Medien adaptiv. Wenn Sie eine feste Größe festlegen möchten, legen Sie sie in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit den Eigenschaften **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

Dies ist die einzig verfügbare Option beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien. Die angezeigten Viewer-Vorgaben sind ebenfalls intelligent - es werden nur relevante Viewer-Vorgaben angezeigt.

**[!UICONTROL Bildvorgabe]** : Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Bildmodifikatoren]** : Sie können Bildeffekte ändern, indem Sie zusätzliche Bildbefehle bereitstellen. Diese werden unter [Verwalten von Bildvorgaben](/help/assets/managing-viewer-presets.md) und [Befehlsreferenz](https://docs.adobe.com/content/help/de-DE/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) beschrieben.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Haltepunkte]** : Wenn Sie dieses Asset auf einer responsiven Site verwenden, müssen Sie die Seitenumbruchpunkte hinzufügen. Bildhaltepunkte müssen durch Kommas (,) voneinander getrennt werden. Diese Option kann verwendet werden, wenn in einer Bildvorgabe keine Höhe oder Breite festgelegt ist.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

Sie können die folgenden [!UICONTROL Erweiterte Einstellungen] bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Titel]**  - Ändern Sie den Titel des Bildes.

**[!UICONTROL Alt-Text]** : Hinzufügen einen Titel für die Benutzer, die Grafiken deaktiviert haben.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL URL, Öffnen in]** : Sie können ein Asset vom zum Öffnen eines Links festlegen. Legen Sie die Optionen **[!UICONTROL URL]** und **[!UICONTROL In]** öffnen fest, um anzugeben, ob die Datei im selben Fenster oder in einem neuen Fenster geöffnet werden soll.

Diese Option ist beim Anzeigen von Bild-Sets, Rotations-Sets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Breite und Höhe]** : Geben Sie den Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

#### Beim Arbeiten mit Video {#when-working-with-video}

Verwenden Sie die Komponente [!UICONTROL Dynamische Medien], um Ihren Webseiten dynamische Videos hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

![chlimage_1-74](assets/chlimage_1-74a.png)

Sie können die folgenden [!UICONTROL Einstellungen für dynamische Medien] bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

>[!NOTE]
>
>Die Videokomponente für Dynamic Media ist standardmäßig adaptiv. Wenn sie eine feste Größe aufweisen soll, müssen Sie dies in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** festlegen.

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie im Dropdown-Menü eine vorhandene Video-Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

Sie können die folgenden [!UICONTROL Erweitert] Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Titel]**  - Ändern Sie den Titel des Videos.

**[!UICONTROL Breite und Höhe]** : Geben Sie den Wert in Pixel ein, wenn das Video eine feste Größe haben soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

#### Sichere Videowiedergabe {#how-to-delivery-secure-video}

Wenn Sie in AEM 6.2 [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480) installieren, können Sie festlegen, ob ein Video über eine sichere SSL-Verbindung (HTTPS) oder eine unsichere Verbindung (HTTP) wiedergegeben wird. Standardmäßig wird automatisch das Videowiedergabeprotokoll der Webseite übernommen, in die das Video eingebettet wird. Wenn die Webseite über HTTPS geladen wird, wird das Video ebenfalls über HTTPS wiedergegeben. Umgekehrt wird das Video über HTTP wiedergegeben, wenn die Webseite HTTP verwendet. In den meisten Fällen ist dieses Verhalten korrekt und es müssen keine Konfigurationsänderungen vorgenommen werden. Sie können dieses Standardverhalten jedoch außer Kraft setzen, indem Sie `VideoPlayer.ssl=on` am Ende des URL-Pfades oder zur Liste weiterer Viewer-Konfigurationsparameter in einem Embed-Code-Snippet hinzufügen, um eine sichere Videowiedergabe zu erzwingen.

Weitere Informationen zur sicheren Videowiedergabe sowie zur Verwendung des Konfigurationsattributs `VideoPlayer.ssl` in Ihrem URL-Pfad finden Sie im Referenzhandbuch zu den Viewern unter [Sichere Videowiedergabe](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html). Abgesehen vom Video-Viewer ist sicherer Video-Versand für den Viewer für gemischte Medien und den Viewer für interaktive Videos verfügbar.

### Komponente für interaktive Medien {#interactive-media-component}

Die Komponente „Interaktive Medien“ ist für Assets mit interaktiven Elementen wie Hotspots oder Imagemaps vorgesehen. Verwenden Sie bei interaktiven Bildern, interaktiven Videos oder Karussellbannern die Komponente **[!UICONTROL Interaktive Medien]**.

Die Komponente [!UICONTROL Interaktive Medien] ist intelligent - je nachdem, ob Sie ein Bild oder ein Video hinzufügen, haben Sie verschiedene Optionen. Darüber hinaus reagiert der Viewer. Das heißt, die Bildschirmgröße ändert sich automatisch je nach Bildschirmgröße. Alle Viewer sind HTML5-basierte Viewer.

![chlimage_1-75](assets/chlimage_1-75a.png)

Sie können die folgenden allgemeinen Einstellungen **** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Viewer-Vorgaben müssen veröffentlicht werden, bevor sie verwendet werden können. Siehe „Verwalten von Viewer-Vorgaben“.

**[!UICONTROL Titel]**  - Ändern Sie den Titel des Videos.

**[!UICONTROL Breite und Höhe]** : Geben Sie den Wert in Pixel ein, wenn das Video eine feste Größe haben soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

Sie können die folgenden Einstellungen von **[!UICONTROL Zu Warenkorb hinzufügen]** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Produktelement]**  anzeigen: Standardmäßig ist dieser Wert ausgewählt. Das Produkt-Asset zeigt ein Bild des Produkts, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um das Produkt-Asset nicht anzuzeigen.

**[!UICONTROL Produktpreis]**  anzeigen: Dieser Wert ist standardmäßig ausgewählt. Der Produktpreis gibt den Preis des Artikels an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um den Produktpreis nicht anzuzeigen.

**[!UICONTROL Produktformular]**  anzeigen: Standardmäßig ist dieser Wert nicht ausgewählt. Das Produktformular beinhaltet jegliche Produktvarianten, etwa hinsichtlich der Größe und der Farbe. Deaktivieren Sie das Kontrollkästchen, um die Produktvarianten nicht anzuzeigen.
