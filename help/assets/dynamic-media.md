---
title: Arbeiten mit Dynamic Media
description: Erfahren Sie, wie Sie mit der Software Assets für Web-, Mobile- und Social-Sites bereitstellen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: introduction
content-type: reference
role: User, Admin
exl-id: f8a80b22-b1a6-475f-b3f1-b2f47822f21d
feature: Collaboration,Asset Management
solution: Experience Manager, Experience Manager Assets
source-git-commit: d6b9dde5201198cb073293b2b8527a458836ff0b
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 51%

---

# Arbeiten mit Dynamic Media  {#working-with-dynamic-media}

Mit [Dynamic Media](https://business.adobe.com/de/products/experience-manager/assets/dynamic-media.html) können Sie visuell ansprechende Merchandising- und Marketing-Assets nach Bedarf bereitstellen, die automatisch für die Anzeige auf Web- sowie Mobile- und Social-Media-Sites skaliert werden. Mithilfe einer Reihe von Primärquellen-Assets generiert und liefert die Software mehrere Varianten ansprechender Inhalte in Echtzeit über ihr globales, skalierbares und leistungsoptimiertes Netzwerk.

Die Software bietet interaktive Anzeigeerlebnisse wie Zoom, Drehen um 360 Grad und Videos. Sie enthält die Workflows der Adobe Experience Manager Digital Asset Management (Assets)-Lösung, um den Digital-Campaign-Verwaltungsprozess zu vereinfachen und zu optimieren.

<!-- >ARTICLE IS MISSING. GIVES 404 [!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Was Sie mit der Software machen können {#what-you-can-do-with-dynamic-media}

Mit der Software können Sie Ihre Assets vor der Veröffentlichung verwalten. Eine ausführliche Beschreibung der allgemeinen Arbeit mit digitalen Assets finden Sie in [Arbeiten mit digitalen Assets](manage-assets.md). Die allgemeinen Themen umfassen das Hochladen, Herunterladen, Bearbeiten und Veröffentlichen von Assets, das Anzeigen und Bearbeiten von Eigenschaften und die Suche nach Assets.

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

Sie können anhand der folgenden Merkmale feststellen, ob die Software aktiviert ist:

* Dynamische Ausgabedarstellungen sind beim Herunterladen oder Anzeigen von Assets in der Vorschau verfügbar.
* Bildsets, Rotationssets und Sets für gemischte Medien sind verfügbar.
* PTIFF-Ausgabedarstellungen werden erstellt.

Wenn Sie ein Bild-Asset auswählen, unterscheidet sich die Ansicht des Assets von der Software [enabled](config-dynamic.md#enabling-dynamic-media). Es verwendet die On-Demand-HTML5-Viewer.

### Dynamische Ausgabedarstellungen {#dynamic-renditions}

Dynamische Ausgabeformate wie Bild- und Viewer-Vorgaben (unter **[!UICONTROL Dynamisch]**) sind verfügbar, wenn die Software aktiviert ist.

![chlimage_1-358](assets/chlimage_1-358.png)

### Bildsets, Rotationssets und Sets für gemischte Medien {#image-sets-spins-sets-mixed-media-sets}

Bildsets, Rotationssets und Sets für gemischte Medien sind verfügbar, wenn die Software aktiviert ist.

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF-Ausgabedarstellungen {#ptiff-renditions}

Für Dynamic Media aktivierte Assets enthalten `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### Änderung der Asset-Ansichten {#asset-views-change}

Wenn die Software aktiviert ist, können Sie durch Klicken auf die Schaltflächen `+` und `-` ein- und auszoomen. Sie können auch durch Klicken in einen bestimmten Bereich einzoomen. Durch „Wiederherstellen“ können Sie zur Originalansicht zurückkehren und durch Klicken auf die diagonalen Pfeile das Bild im Vollbildmodus anzeigen. Wenn die Software aktiviert ist, sieht sie wie folgt aus:

![chlimage_1-361](assets/chlimage_1-361.png)

Wenn die Software deaktiviert ist, können Sie ein- und auszoomen und die Originalgröße wiederherstellen:

![chlimage_1-362](assets/chlimage_1-362.png)
