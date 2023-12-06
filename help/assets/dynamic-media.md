---
title: Arbeiten mit Dynamic Media
description: Informationen zur Verwendung von Dynamic Media zum Bereitstellen von Assets für den Gebrauch in Web, Mobile und Social Media
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: introduction
content-type: reference
role: User, Admin
exl-id: f8a80b22-b1a6-475f-b3f1-b2f47822f21d
feature: Collaboration,Asset Management
source-git-commit: 04050f31742c926b45235595f6318929d3767bd8
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 88%

---

# Arbeiten mit Dynamic Media {#working-with-dynamic-media}

Mit [Dynamic Media](https://business.adobe.com/de/products/experience-manager/assets/dynamic-media.html) können Sie visuell ansprechende Merchandising- und Marketing-Assets nach Bedarf bereitstellen, die automatisch für die Anzeige auf Web- sowie Mobile- und Social-Media-Sites skaliert werden. Anhand eines Sets von Assets aus Primärquellen können Sie mit Dynamic Media mehrere Varianten ansprechender Inhalte in Echtzeit über das globale, skalierbare und leistungsoptimierte Netzwerk generieren und bereitstellen.

Dynamic Media ermöglicht interaktive Anzeigeerlebnisse, wie Zoom, Drehen um 360 Grad und Videos. Dynamic Media bindet die Workflows der Adobe Experience Manager-Lösung für die Verwaltung digitaler Assets (Assets) auf einzigartige Weise ein, um die Verwaltung digitaler Kampagnen zu vereinfachen und zu optimieren.

<!-- >ARTICLE IS MISSING. GIVES 404 [!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Einsatzmöglichkeiten für Dynamic Media {#what-you-can-do-with-dynamic-media}

Mit Dynamic Media können Sie Assets vor ihrer Veröffentlichung verwalten. Eine ausführliche Beschreibung der allgemeinen Arbeit mit digitalen Assets finden Sie in [Arbeiten mit digitalen Assets](manage-assets.md). Die allgemeinen Themen umfassen das Hochladen, Herunterladen, Bearbeiten und Veröffentlichen von Assets, das Anzeigen und Bearbeiten von Eigenschaften und die Suche nach Assets.

Funktionen, die nur für Dynamic Media vorgesehen sind:

* [Karussellbanner](carousel-banners.md)
* [Bildsets](image-sets.md)
* [Interaktive Bilder](interactive-images.md)
* [Interaktive Videos](interactive-videos.md)
* [Gemischte Mediensets](mixed-media-sets.md)
* [Panoramabilder](panoramic-images.md)

* [Rotationssets](spin-sets.md)
* [Video ](video.md)
* [Bereitstellen von Dynamic Media-Assets](delivering-dynamic-media-assets.md)
* [Verwalten von Assets](managing-assets.md)
* [Erstellen eines benutzerdefinierten Popup-Fensters mithilfe einer Schnellansicht](custom-pop-ups.md)

Siehe auch [Einrichten von Dynamic Media](administering-dynamic-media.md).

>[!NOTE]
>
>Informationen zu den Unterschieden zwischen der Verwendung von Dynamic Media und der Integration von Dynamic Media Classic in Adobe Experience Manager finden Sie unter [Dynamic Media Classic-Integration versus Dynamic Media](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media).

## Aktivierte und deaktivierte Dynamic Media-Funktion im Vergleich {#dynamic-media-on-versus-dynamic-media-off}

Anhand der folgenden Merkmale können Sie erkennen, ob Dynamic Media aktiviert ist:

* Dynamische Ausgabedarstellungen sind beim Herunterladen oder Anzeigen von Assets in der Vorschau verfügbar.
* Bildsets, Rotationssets und Sets für gemischte Medien sind verfügbar.
* PTIFF-Ausgabedarstellungen werden erstellt.

Wenn Sie ein Bild-Asset auswählen, sieht die Ansicht des Assets mit [aktivierter](config-dynamic.md#enabling-dynamic-media) Dynamic Media-Funktion anders aus. Dynamic Media nutzt die On-Demand-HTML5-Viewer.

### Dynamische Ausgabedarstellungen {#dynamic-renditions}

Dynamische Ausgabedarstellungen wie Bild- und Viewer-Vorgaben (unter **[!UICONTROL Dynamisch]**) sind verfügbar, wenn Dynamic Media aktiviert ist.

![chlimage_1-358](assets/chlimage_1-358.png)

### Bildsets, Rotationssets und Sets für gemischte Medien {#image-sets-spins-sets-mixed-media-sets}

Bildsets, Rotationssets und Sets für gemischte Medien sind verfügbar, wenn Dynamic Media aktiviert ist.

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF-Ausgabedarstellungen {#ptiff-renditions}

Für Dynamic Media aktivierte Assets enthalten `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### Änderung der Asset-Ansichten {#asset-views-change}

Wenn Dynamic Media aktiviert ist, können Sie durch Klicken auf die `+` und `-` Schaltflächen. Sie können auch auf klicken, um in einen bestimmten Bereich zu zoomen. Zurück bringt Sie zur Originalversion und Sie können das Bild im Vollbildmodus anzeigen, indem Sie auf die diagonalen Pfeile klicken. Dynamic Media enabled sieht wie folgt aus:

![chlimage_1-361](assets/chlimage_1-361.png)

Wenn Dynamic Media deaktiviert ist, können Sie die Ansicht vergrößern und verkleinern und die Originalgröße wiederherstellen:

![chlimage_1-362](assets/chlimage_1-362.png)
