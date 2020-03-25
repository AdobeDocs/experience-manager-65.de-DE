---
title: Versionshinweise zu Adobe Experience Manager Assets
description: Die neuen Funktionen und Erweiterungen für Adobe Experience Manager 6.5 Assets.
translation-type: tm+mt
source-git-commit: 23f838b681d4d9eda55e287519f330addf7928aa

---


# Versionshinweise zu Adobe Experience Manager Assets {#aem-assets-release-notes}

Im Folgenden finden Sie die wichtigsten Funktionen und Highlights der Version Adobe Experience Manager 6.5 Assets.

## Integration with [!DNL Adobe Creative Cloud] and creative workflows {#integration-with-adobe-creative-cloud-and-creative-workflows}

[!DNL Adobe Experience Manager] bietet verschiedene Möglichkeiten, um zu integrieren und Assets für die Verwendung in Workflows freizugeben, in denen Kreativ-, Marketing- oder Businessteams eng zusammenarbeiten. [!DNL Adobe Creative Cloud] [!DNL Experience Manager] 6.5 ermöglicht eine noch bessere Integration und stärkere Optimierung. Das Ergebnis: mehr Chancen und die Verbesserung vorhandener Methoden.

Read on to know the specific capabilities and integrations of [!DNL Experience Manager] 6.5 that you can leverage to best support your content velocity use cases.

### Adobe Asset Link {#aal}

[!DNL Adobe Asset Link] stärkt die Zusammenarbeit zwischen Kreativen und Marketingexperten bei der Inhaltserstellung. Creatives can access content stored in [!DNL Experience Manager Assets], without leaving the apps that they are most familiar with. Creatives can seamlessly browse, search, check out, and check in assets using the in-app panel in [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], and [!DNL Adobe InDesign] apps.

[!DNL Adobe Asset Link] ist Teil der [Creative Cloud für Unternehmen](https://www.adobe.com/creativecloud/business/enterprise.html) . For more information about it, including necessary configuration of your [!DNL Experience Manager] deployment, see [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).

![Suchen von Assets in Adobe Fotoshop](assets/asset_search_photoshop.png)

### [!DNL Adobe Stock] integration {#stock}

Your organization can use its [!DNL Adobe Stock] enterprise plan within [!DNL Experience Manager Assets] to ensure that licensed assets are broadly available for your creative and marketing projects. You can quickly find, preview, and license [!DNL Adobe Stock] assets that are saved in Experience Manager, using the powerful DAM capabilities of [!DNL Experience Manager].

[!DNL Adobe Stock] Der Dienst bietet Designern und Unternehmen Zugriff auf Millionen von hochwertigen, kuratierten, gebührenfreien Fotos, Vektoren, Illustrationen, Videos, Vorlagen und 3D-Assets für all ihre kreativen Projekte.

For more info, see [Use DNL Adobe Stock assets in Experience Manager Assets](/help/assets/aem-assets-adobe-stock.md).

![Vorschau des Adobe Stock-Images und der Lizenz aus Experience Manager Assets](assets/stock_image_preview_license_options.png)

*Abbildung: Vorschau[!DNL Adobe Stock]Image und Lizenz von innen[!DNL Experience Manager Assets].*

![Suchen und Filtern der lizenzierten Adobe Stock-Bilder in Experience Manager](assets/aem-search-filters2.jpg)

*Abbildung: Suchen und filtern Sie die lizenzierten[!DNL Adobe Stock]Bilder in[!DNL Experience Manager].*

### Dynamic references in [!DNL Adobe InDesign] {#dynamic-references-in-indesign}

[!DNL Experience Manager Assets] in [!DNL Adobe InDesign] Dateien verwendet werden dynamisch. Die Verweise werden automatisch aktualisiert, wenn die referenzierten Assets im Repository verschoben werden. Weitere Informationen finden Sie unter [Verwalten von zusammengesetzten Assets](/help/assets/managing-linked-subassets.md).

## Brand Portal-Funktionen {#brand-portal-capabilities}

[!DNL Experience Manager Assets Brand Portal]Mit können Sie problemlos genehmigte Assets abrufen, diese wirksam kontrollieren und sicher und geräteübergreifend an externe Anbieter/Agenturen und interne Geschäftsanwender verteilen. Brand Portal ermöglicht eine effizientere Asset-Freigabe sowie schnellere Time-to-Market für Assets und verringert das Risiko von Nicht-Compliance und unbefugtem Zugriff.

Weitere Informationen finden Sie unter [Neue Funktionen in AEM Assets Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/using/whats-new.html).

## Connected Assets {#connectedassets}

In großen Unternehmen kann die zur Erstellung von Websites erforderliche Infrastruktur verteilt werden. Manchmal befinden sich die Funktionen zur Website-Erstellung und die hierfür benötigten digitalen Assets in unterschiedlichen Silos.

[!DNL Experience Manager Sites] bietet Funktionen zum Erstellen von Webseiten, während das Digital Asset Management (DAM)-System ist, das die für Websites erforderlichen Assets bereitstellt. [!DNL Experience Manager Assets] [!DNL Experience Manager] unterstützt nun den oben genannten Anwendungsfall durch Integration [!DNL Sites] und [!DNL Assets]. Siehe [Konfigurieren und Verwenden der Funktion](/help/assets/use-assets-across-connected-assets-instances.md)&quot;Connected Assets&quot;.

![Ziehen eines Assets aus einer [!DNL Experience Manager] Bereitstellung auf einer [!DNL Sites] Seite einer anderen [!DNL Experience Manager] Bereitstellung](assets/connected-assets-drag-and-drop-only.gif)

*Abbildung: Ziehen Sie ein Asset aus einer[!DNL Experience Manager]Bereitstellung auf einer[!DNL Sites]Seite in eine andere[!DNL Experience Manager]Bereitstellung.*

## Dynamic Media {#dynamic-media}

[!DNL Dynamic Media] bietet erweiterte Rich-Media-Authoring- und Versände, [!DNL Experience Manager Assets] um innovative und personalisierte Erlebnisse zu fördern. Durch das Hochladen eines einzelnen hochwertigen Master-Assets und die Verwendung unseres erweiterten Cloud-Renderings und der Viewer können Sie jede beliebige Kombination von Darstellungen spontan bereitstellen, um die Medienstrategie Ihres Unternehmens zu unterstützen.

For more details on new [!DNL Dynamic Media] features see [Dynamic Media Release Notes](https://marketing.adobe.com/resources/help/en_US/s7/release_notes/).

### Unterstützung für 360°-Videos {#video-support}

Manage your 360-video files directly in [!DNL Experience Manager] using the cutting edge viewers to deliver VR-experiences to desktops, mobile and VR-headsets. Weitere Informationen finden Sie unter [Verwenden von 360°-Videos](/help/assets/360-video.md).

### Benutzerdefinierte Videominiaturen {#custom-video-thumbnails}

Sie können nun die Miniaturen für Ihre Video-Assets mithilfe von Frames aus dem Video selbst oder aus anderen im DAM gespeicherten Inhalten anpassen. Weitere Anweisungen finden Sie unter [Informationen zu Videominiaturen](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

### Verbesserte Barrierefreiheit {#accessibility-enhancements}

[!DNL Dynamic Media] Viewer unterstützen jetzt erweiterte Barrierefreiheitsfunktionen wie Aria-Unterstützung, Bildschirmlesehilfen und Alt-Text. Weitere Informationen finden Sie in den [Versionshinweisen zu Dynamic Media-Viewern](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/index.html).

## Verbessertes Sucherlebnis {#search-experience-enhancement}

[!DNL Experience Manager] Ab 6.5 können Marketingexperten die gewünschten Assets schneller von der Suchergebnisseite aus entdecken. Die Suchfacetten werden mit der Anzahl der Assets aktualisiert, noch bevor der Suchfilter angewendet wird. Durch Anzeige der erwarteten Anzahl im Filter können Benutzer effizient durch Suchergebnisse navigieren. For more information, see [Search assets in Experience Manager](../assets/search-assets.md).

![Anzeigen der Asset-Anzahl ohne Filterung der Suchergebnisse in Suchfacetten](/help/assets/assets/asset_search_results_in_facets_filters.png)

*Abbildung: Zeigen Sie die Anzahl der Assets ohne Filterung der Suchergebnisse in den Suchfacetten an.*

## Größere Anwenderfreundlichkeit {#usability-enhancement}

Sie können jetzt alle geladenen Assets in einem Ordner oder aus einem Suchergebnis in einem Schritt auswählen. Dies ermöglicht eine schnelle Verwaltung aller Assets. The check box selects all the assets that fits the scenario, say a search result and not just the assets that are visible in the [!DNL Experience Manager] interface.

![Mit der Option &quot;Alle auswählen&quot;können Sie alle geladenen Assets mit einem Klick auswählen.](assets/select-all-in-aem-assets.gif)

*Abbildung: Verwenden Sie die Option &quot;Alle auswählen&quot;, um alle geladenen Assets mit einem Klick auszuwählen.*

## Verbesserte Metadaten {#metadata-enhancements}

[!DNL Assets]Mit können Sie Metadatenschemata für Asset-Ordner erstellen, die die auf Ordnereigenschaften-Seiten angezeigten Layouts und Metadaten definieren. Sie können einem vorhandenen Ordner ein Ordner-Metadatenschema zu diesem Zeitpunkt oder beim Erstellen eines neuen Ordners zuweisen. Weitere Informationen finden Sie unter [Ordner-Metadatenschema](/help/assets/folder-metadata-schema.md).

Beim Festlegen kaskadierender Metadaten können die Optionen zur Laufzeit aus einer JSON-Datei geladen werden, anstatt sie manuell in das Formular einzugeben. Weitere Informationen finden Sie unter [Kaskadierende Metadaten](/help/assets/cascading-metadata.md).

## Verbessertes Reporting {#reporting-enhancements}

Die Inhaltsfragmente und die Linkfreigabe sind jetzt im heruntergeladenen Bericht enthalten. Weitere Informationen finden Sie unter [Asset-Berichte](/help/assets/asset-reports.md).
