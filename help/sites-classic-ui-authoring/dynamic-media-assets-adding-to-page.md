---
title: Hinzufügen von Dynamic Media-Assets zu Seiten
description: Um die Dynamic Media-Funktion zu Assets hinzuzufügen, die Sie auf Ihren Websites verwenden, können Sie die Dynamic Media- oder interaktive Medienkomponente direkt auf der Seite hinzufügen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
exl-id: d2ebfca5-19f9-4fa5-b142-b978f46a912f
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '1668'
ht-degree: 47%

---

# Hinzufügen von Dynamic Media-Assets zu Seiten{#adding-dynamic-media-assets-to-pages}

Um die Dynamic Media-Funktion zu Assets hinzuzufügen, die Sie auf Ihren Websites verwenden, können Sie die **[!UICONTROL Dynamic Media]** oder **[!UICONTROL Interaktive Medien]** direkt auf der Seite. Eingabe **[!UICONTROL Design]** und die Aktivierung der Dynamic Media-Komponenten. Anschließend können Sie der Seite diese Komponenten und der Komponente Assets hinzufügen. Die Dynamic Media- und interaktiven Medienkomponenten sind intelligent. Sie wissen, ob Sie ein Bild oder Video hinzufügen. Die verfügbaren Optionen ändern sich entsprechend.

Sie fügen Dynamic Media-Assets direkt zur Seite hinzu, wenn Sie Adobe Experience Manager als WCM verwenden.

>[!NOTE]
>
>Imagemaps sind für Karussellbanner umgehend verfügbar.

## Hinzufügen einer Dynamic Media-Komponente zu einer Seite {#adding-a-dynamic-media-component-to-a-page}

Hinzufügen der [!UICONTROL Dynamic Media] oder [!UICONTROL Interaktive Medien] -Komponente zu einer Seite entspricht dem Hinzufügen einer Komponente zu einer beliebigen Seite. Die [!UICONTROL Dynamic Media] und [!UICONTROL Interaktive Medien] -Komponenten werden in den folgenden Abschnitten ausführlich beschrieben.

So fügen Sie einer Seite eine Komponente bzw. einen Viewer vom Typ „Dynamische Medien“ hinzu:

1. Öffnen Sie in Experience Manager die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Wenn keine Dynamic Media-Komponente verfügbar ist, wählen Sie das Lineal im [!UICONTROL Sidekick] eingeben **[!UICONTROL Design]** -Modus.
1. Auswählen **[!UICONTROL Bearbeiten]** parsys.
1. Auswählen **[!UICONTROL Dynamic Media]** damit Sie die Dynamic Media-Komponenten verfügbar machen können.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](/help/sites-authoring/default-components-designmode.md).

1. Zurück zu **[!UICONTROL Bearbeiten]** Modus durch Klicken auf das Stiftsymbol im [!UICONTROL Sidekick].
1. Ziehen Sie die **[!UICONTROL Dynamic Media]** oder **[!UICONTROL Interaktive Medien]** -Komponente aus **[!UICONTROL Sonstiges]** im Sidekick auf der Seite an der gewünschten Position.
1. Auswählen **[!UICONTROL Bearbeiten]** sodass die Komponente geöffnet wird.
1. [Bearbeiten der Komponente](#dynamic-media-component) nach Bedarf.
1. Auswählen **[!UICONTROL OK]** , damit Ihre Änderungen gespeichert werden.

## Komponenten vom Typ „Dynamische Medien“ {#dynamic-media-components}

[!UICONTROL Dynamic Media] und [!UICONTROL Interaktive Medien] finden Sie im Abschnitt [!UICONTROL Sidekick] under **[!UICONTROL Dynamic Media]**. Verwenden Sie die Komponente **[!UICONTROL Interaktive Medien]** für beliebige interaktive Assets wie interaktive Videos, interaktive Bilder oder Karussell-Sets. Verwenden Sie für alle anderen Dynamic Media-Komponenten den **[!UICONTROL Dynamic Media]** -Komponente.

![chlimage_1-71](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar und müssen vor der Verwendung im Designmodus ausgewählt werden. [Nachdem sie im Designmodus verfügbar gemacht wurden](/help/sites-authoring/default-components-designmode.md)können Sie die Komponenten wie jede andere Experience Manager-Komponente zu Ihrer Seite hinzufügen.

### Komponente „Dynamische Medien“ {#dynamic-media-component}

Die Dynamic Media-Komponente ist intelligent. Je nachdem, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, Sets für gemischte Medien und Videos. Darüber hinaus ist der Viewer responsiv. Das heißt, die Größe des Bildschirms ändert sich automatisch entsprechend der Bildschirmgröße. Alle Viewer sind HTML5-basierte Viewer.

>[!NOTE]
>
>Wenn Sie die [!UICONTROL Dynamic Media] und **[!UICONTROL Dynamic Media-Einstellungen]** leer ist oder Sie ein Asset nicht ordnungsgemäß hinzufügen können, überprüfen Sie Folgendes:
>
>* Sie [Dynamic Media aktiviert](/help/assets/config-dynamic.md) haben. Dynamic Media ist standardmäßig deaktiviert.
>* das Bild eine Pyramid TIFF-Datei aufweist. Bilder, die vor der Aktivierung von Dynamic Media importiert wurden, haben keine Pyramid TIFF-Datei.
>


#### Arbeiten mit Bildern {#when-working-with-images}

Die [!UICONTROL Dynamic Media] -Komponente können Sie dynamische Bilder hinzufügen, einschließlich Bildsets, Rotationssets und Sets für gemischte Medien. Sie können Vergrößerungen sowie Verkleinerungen vornehmen und (sofern zutreffend) ein Bild in einem Rotationsset drehen oder ein Bild aus einem anderen Set auswählen.

Sie können zudem die Viewer-Vorgabe, Bildvorgabe oder das Bildformat direkt in der Komponente konfigurieren. Um ein Bild dynamisch zu machen, können Sie die Breackpoints festlegen oder eine dynamische Bildvorgabe anwenden.

![chlimage_1-72](assets/chlimage_1-72a.png)

Sie können die folgenden Dynamic Media-Einstellungen bearbeiten, indem Sie auf **[!UICONTROL Bearbeiten]** in der Komponente ein und klicken Sie dann auf **[!UICONTROL Dynamic Media-Einstellungen]** Registerkarte.

![chlimage_1-73](assets/chlimage_1-73a.png)

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für Dynamic Media adaptiv. Wenn Sie eine feste Größe festlegen möchten, legen Sie sie in der Komponente im **[!UICONTROL Erweitert]** mit dem **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** Eigenschaften.

**[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

Diese Option ist nur verfügbar, wenn Sie Bildsets, Rotationssets oder Sets für gemischte Medien anzeigen. Die angezeigten Viewer-Vorgaben sind intelligent. Das heißt, es werden nur relevante Viewer-Vorgaben angezeigt.

**[!UICONTROL Bildvorgabe]** - Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Bild-Modifikatoren]** - Sie können Bildeffekte ändern, indem Sie zusätzliche Bildbefehle bereitstellen. Diese Befehle werden unter [Verwalten von Bildvorgaben](/help/assets/managing-viewer-presets.md) und [Befehlsreferenz](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=de).

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Haltepunkte]** - Wenn Sie dieses Asset auf einer responsiven Site verwenden, müssen Sie die Seitenhaltepunkte hinzufügen. Bildhaltepunkte werden durch Kommas (,) getrennt. Diese Option kann verwendet werden, wenn in einer Bildvorgabe keine Höhe oder Breite festgelegt ist.

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

Sie können Folgendes bearbeiten: [!UICONTROL Erweiterte Einstellungen] durch Klicken auf **[!UICONTROL Bearbeiten]** in der Komponente.

**[!UICONTROL Titel]**: Ändern Sie den Bildtitel.

**[!UICONTROL Alternativer Text]**: Geben Sie dem Bild einen Titel, für die Benutzer, deren Grafiken deaktiviert sind.

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL URL, Öffnen in]** - Sie können ein Asset in festlegen, um einen Link zu öffnen. Legen Sie die **[!UICONTROL URL]** und **[!UICONTROL Öffnen in]** um anzugeben, ob das Fenster im selben oder in einem neuen Fenster geöffnet werden soll.

Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

**[!UICONTROL Breite und Höhe]** - Geben Sie einen Wert in Pixel an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

#### Arbeiten mit Videos {#when-working-with-video}

Verwenden Sie die **[!UICONTROL Dynamic Media]** -Komponente, um Ihren Webseiten dynamische Videos hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

![chlimage_1-74](assets/chlimage_1-74a.png)

Sie können Folgendes bearbeiten: [!UICONTROL Dynamic Media-Einstellungen] durch Klicken auf **[!UICONTROL Bearbeiten]** in der Komponente.

>[!NOTE]
>
>Die Videokomponente für Dynamic Media ist standardmäßig adaptiv. Wenn sie eine feste Größe aufweisen soll, müssen Sie dies in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** festlegen.

**[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Video-Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

Sie können Folgendes bearbeiten: [!UICONTROL Erweitert] Einstellungen durch Klicken auf **[!UICONTROL Bearbeiten]** in der Komponente.

**[!UICONTROL Titel]**: Ändern Sie den Videotitel.

**[!UICONTROL Breite und Höhe]** - Geben Sie einen Wert in Pixel an, wenn das Video eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

#### Sicheres Video bereitstellen {#how-to-delivery-secure-video}

In Experience Manager 6.2 bei der Installation [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480)können Sie steuern, ob ein Video über eine sichere SSL-Verbindung (HTTPS) oder eine unsichere Verbindung (HTTP) bereitgestellt wird. Standardmäßig wird automatisch das Videowiedergabeprotokoll der Webseite übernommen, in die das Video eingebettet wird. Wenn die Webseite über HTTPS geladen wird, wird das Video ebenfalls über HTTPS wiedergegeben. Umgekehrt wird das Video über HTTP bereitgestellt, wenn sich die Webseite auf HTTP befindet. Normalerweise ist dieses Standardverhalten in Ordnung und es müssen keine Konfigurationsänderungen vorgenommen werden. Sie können dieses Standardverhalten jedoch überschreiben. Anhängen `VideoPlayer.ssl=on` , um entweder das Ende eines URL-Pfads oder die Liste anderer Viewer-Konfigurationsparameter in einem Einbettungscode-Snippet anzuzeigen. Beide Aktionen erzwingen die sichere Videobereitstellung.

Weitere Informationen zur sicheren Videowiedergabe sowie zur Verwendung des Konfigurationsattributs `VideoPlayer.ssl` in Ihrem URL-Pfad finden Sie im Referenzhandbuch zu den Viewern unter [Sichere Videowiedergabe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html). Neben dem Video-Viewer ist die sichere Videobereitstellung für den Viewer für gemischte Medien und den Viewer für interaktive Videos verfügbar.

### Interaktive Medienkomponente {#interactive-media-component}

Die Komponente „Interaktive Medien“ ist für Assets mit interaktiven Elementen wie Hotspots oder Imagemaps vorgesehen. Verwenden Sie bei interaktiven Bildern, interaktiven Videos oder Karussellbannern die Komponente **[!UICONTROL Interaktive Medien]**.

Die [!UICONTROL Interaktive Medien] -Komponente intelligent ist - je nachdem, ob Sie ein Bild oder ein Video hinzufügen, haben Sie verschiedene Optionen. Darüber hinaus ist der Viewer responsiv. Das heißt, die Größe des Bildschirms ändert sich automatisch entsprechend der Bildschirmgröße. Alle Viewer sind HTML5-basierte Viewer.

![chlimage_1-75](assets/chlimage_1-75a.png)

Sie können die folgenden allgemeinen Einstellungen **** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Viewer-Vorgaben müssen veröffentlicht werden, bevor sie verwendet werden können. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

**[!UICONTROL Titel]**: Ändern Sie den Videotitel.

**[!UICONTROL Breite und Höhe]** - Geben Sie einen Wert in Pixel an, wenn das Video eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, wird es adaptiv.

Sie können die folgenden Einstellungen von **[!UICONTROL Zu Warenkorb hinzufügen]** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

**[!UICONTROL Produkt-Asset anzeigen]**: Dieser Wert ist standardmäßig ausgewählt. Das Produkt-Asset zeigt ein Bild des Produkts, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um das Produkt-Asset nicht anzuzeigen.

**[!UICONTROL Produktpreis anzeigen]**: Dieser Wert ist standardmäßig ausgewählt. Der Produktpreis gibt den Preis des Artikels an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um den Produktpreis nicht anzuzeigen.

**[!UICONTROL Produktformular anzeigen]**: Dieser Wert ist standardmäßig nicht ausgewählt. Das Produktformular beinhaltet jegliche Produktvarianten, etwa hinsichtlich der Größe und der Farbe. Deaktivieren Sie das Kontrollkästchen, um die Produktvarianten nicht anzuzeigen.
