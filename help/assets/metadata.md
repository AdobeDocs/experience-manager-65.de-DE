---
title: Verwalten Sie Metadaten Ihrer digitalen Assets in [!DNL Adobe Experience Manager].
description: Erfahren Sie mehr über die Metadatentypen und wie [!DNL Adobe Experience Manager Assets] beim Verwalten von Metadaten für Assets hilft, um die Kategorisierung und Organisation von Assets zu erleichtern. [!DNL Experience Manager] ermöglicht die automatische Organisation und Verarbeitung von Assets anhand ihrer Metadaten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f21e9dbb81f18e07a691b2470c1c5b1569876b17

---


# Verwalten von Metadaten für digitale Assets {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] speichert Metadaten für jedes Asset. Dies erleichtert die Kategorisierung und Organisation von Assets und hilft Menschen, die nach einem bestimmten Asset suchen. With the ability to extract metadata from files uploaded to [!DNL Experience Manager Assets], metadata management integrates with the creative workflow. With the ability to keep and manage metadata with your assets, [!DNL Experience Manager Assets] makes it possible to automatically organize and process assets based on their metadata.

* [XMP-Metadaten](xmp.md).
* [Anleitung zum Bearbeiten oder Hinzufügen von Metadaten](meta-edit.md).
* [Metadaten-Schemata-Referenz](meta-ref.md).

## Die Bedeutung von Metadaten {#why-we-need-metadata}

Metadaten sind Informationen über Daten. In dieser Hinsicht beziehen sich Daten auf Ihr digitales Asset, z. B. ein Bild. Metadaten sind für eine effiziente Asset-Verwaltung von entscheidender Bedeutung.

Metadaten sind alle für ein Asset verfügbaren Daten, die jedoch nicht unbedingt in diesem Bild enthalten sind. Beispiele für Metadaten:

* Name des Assets.
* Zeitpunkt und Datum der letzten Änderung.
* Größe des Assets, wie es im Repository gespeichert wurde.
* Name des Ordners, in dem er enthalten ist.
* Zugehörige Assets oder angewendete Tags.

These are the basic metadata properties that [!DNL Experience Manager] can manage for assets, which allows users to see all assets, for example, ordered by their last modification date - useful when trying to discover what assets have recently been added to the repository.

Sie können digitalen Assets auch Daten auf höherer Ebene hinzufügen – darunter:

* Asset-Typ (ist es ein Bild, ein Video, ein Audioclip oder ein Dokument?)
* Eigentümer des Assets.
* Titel des Assets.
* Beschreibung des Assets.
* Tags, die einem Asset zugewiesen sind.

Mit mehr Metadaten können Sie Assets genauer einteilen. Außerdem erweisen sie sich als nützlich, wenn die Menge digitaler Daten ansteigt. Es ist möglich, einige hundert Dateien zu verwalten, die nur auf den Dateinamen basieren. Dieser Ansatz ist jedoch nicht skalierbar und fällt schnell unter, wenn die Zahl der beteiligten Personen und die Zahl der verwalteten Assets steigt.

Durch Hinzufügen von Metadaten wächst der Wert eines digitalen Assets, da das Asset

* Mehr Zugänglichkeit - Systeme und Benutzer können es leicht finden.
* Einfachere Verwaltung - Sie können Assets mit demselben Satz Eigenschaften einfacher finden und Änderungen darauf anwenden.
* Vollständiger: Je mehr Metadaten Sie zu einem Asset hinzugefügt haben, desto mehr Informationen und Kontext werden mit dem Asset geliefert.

For these reasons, [!DNL Assets] provides you with the right means of creating, managing, and exchanging metadata for your digital assets.

## Metadatentypen {#types-of-metadata}

Die beiden grundlegenden Metadatentypen sind technische Metadaten und beschreibende Metadaten.

Technische Metadaten eignen sich für Software-Anwendungen, die mit digitalen Assets arbeiten und nicht manuell gepflegt werden sollen. [!DNL Experience Manager Assets] und andere Software bestimmen automatisch technische Metadaten und die Metadaten können sich ändern, wenn das Asset geändert wird. Welche technischen Metadaten für ein Asset verfügbar sind, hängt größtenteils vom Dateityp des Assets ab. Beispiele für technische Metadaten:

* Größe einer Datei.
* Abmessungen (Höhe und Breite) eines Bildes.
* Bitrate einer Audio- oder Videodatei.
* Auflösung (Detailstufe) eines Bildes.

Beschreibende Metadaten sind solche, die sich auf die Anwendungsdomäne beziehen – etwa das Unternehmen, aus dem ein Asset stammt. Beschreibende Metadaten können nicht automatisch bestimmt werden. Es wird manuell oder halbautomatisch erstellt. Beispielsweise kann eine GPS-fähige Kamera automatisch den Breiten- und Längengrad verfolgen und Geotag für das Bild hinzufügen.

Da der manuelle Aufwand für die Erstellung beschreibender Metadaten sehr kostspielig ist, wurden Standards aufgestellt, um den Austausch von Metadaten über Softwaresysteme und Organisationen hinweg zu erleichtern.

[!DNL Experience Manager Assets] unterstützt alle relevanten Standards für das Metadatenmanagement.

Aufgrund der Wichtigkeit von Metadaten und des hohen manuellen Arbeitsaufwands für ihre Erstellung wurden Standards aufgestellt, die den Austausch erleichtern.

## Kodierungsstandards {#encoding-standards}

Es gibt verschiedene Möglichkeiten, Metadaten in Dateien einzubetten. Dazu werden die folgenden Kodierungsstandards unterstützt:

* XMP: used by [!DNL Assets] to store the extracted metadata within the repository.
* ID3: für Audio- und Videodateien
* Exif: für Bilddateien.
* Other/Legacy: from [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], and so on.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) ist ein offener Standard, der [!DNL Experience Manager Assets] für alle Metadatenverwaltung verwendet wird. Die standardmäßige Angebot-Metadaten-Kodierung, die in alle Dateiformate eingebettet werden kann. Adobe und andere Firmen unterstützen den XMP-Standard, da er ein Rich-Content-Modell bietet. Benutzer des XMP-Standards und von [!DNL Experience Manager Assets] haben eine leistungsstarke Plattform, auf der sie aufbauen können. Weitere Informationen finden Sie unter [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

In diesen ID3-Tags gespeicherte Daten werden angezeigt, wenn Sie eine digitale Audiodatei auf dem Computer oder einem tragbaren MP3-Player abspielen.

ID3-Tags wurden für das MP3-Dateiformat entwickelt. Weitere Informationen zu Formaten:

* ID3-Tags funktionieren in MP3- und mp3PRO-Dateien.
* WAV weist keine Tags auf.
* WMA verfügt über proprietäre Tags, die keine Open-Source-Implementierung zulassen.
* Ogg Vorbis nutzt Xiph-Kommentare, die in den Ogg-Container eingebettet sind.
* AAC verwendet ein proprietäres Tagging-Format.

### Exif {#exif}

Das austauschbare Bilddateiformat (Exif) ist das beliebteste Metadatenformat für die Digitalfotografie. Es bietet eine Möglichkeit zum Einbetten eines festen Wortschatzes mit Metadateneigenschaften in viele Dateiformate wie JPEG, TIFF, RIFF und WAV. Exif stores metadata as pairs of a metadata name and a metadata value. These metadata name-value-pairs are also called tags, not to be confused with the tagging in [!DNL Experience Manager]. Da Exif automatisch von modernen Digitalkameras erstellt und durch moderne Grafiksoftware unterstützt wird, kann es als kleinster gemeinsamer Nenner für das Metadaten-Management angesehen werden.

Eine wichtige Einschränkung von Exif besteht darin, dass einige gängige Bilddateiformate wie BMP, GIF oder PNG diese nicht unterstützen.

Metadatenfelder, die normalerweise von Exif definiert werden, sind technischer Natur und werden nur in begrenztem Umfang für die Verwaltung beschreibender Metadaten verwendet. Aus diesem Grund werden [!DNL Experience Manager Assets] Angebote von Exif-Eigenschaften in [gängige Metadaten-Schemata](metadata-schemas.md) und in [XMP](xmp-writeback.md)zugeordnet.

### Other metadata {#other-metadata}

Andere Metadaten können aus Dateien von Microsoft Word, PowerPoint, Excel usw. eingebettet werden.

## Metadata schemata {#metadata-schemata}

Metadaten-Schema sind vordefinierte Sätze von Metadateneigenschaftsdefinitionen, die in verschiedenen Anwendungen verwendet werden können. Eigenschaften sind immer mit einem Asset verknüpft, d. h. die Eigenschaften beziehen sich auf die Ressource.

Sie können auch eigene Metadaten-Schemata entwerfen, wenn keine vorhanden ist, die Ihren Anforderungen entsprechen. Vorhandene Informationen nicht Duplikat. Das Trennen von Schemata innerhalb eines Unternehmens erleichtert die Freigabe von Metadaten. [!DNL Experience Manager] stellt eine standardmäßige Liste der beliebtesten Metadaten-Schemata bereit. Die Liste hilft Ihnen, Ihre Metadatenstrategie zu starten und schnell die benötigten Metadateneigenschaften auszuwählen.

Die unterstützten Metadaten-Schemata sind unten aufgeführt.

### Standard metadata {#standard-metadata}

* DC - [!DNL Dublin Core] ist ein wichtiger und häufig verwendeter Metadatensatz.
* DICOM – Digital Imaging and Communications in Medicine.
* Iptc4xmpCore &amp; iptc4xmpExt - International Press Communications Standard enthält viele themenspezifische Metadaten.
* rdf – Resource Description Framework: Für generische semantische Webmetadaten.
* XMP - [!DNL Extensible Metadata Platform].
* xmpBJ – Einfaches Auftrags-Ticketing.

### Application-specific metadata {#application-specific-metadata}

Die anwendungsspezifischen Metadaten enthalten technische und beschreibende Metadaten. Diese Metadaten können unter Umständen nicht von anderen Anwendungen verwendet werden. For example, if you have an asset with [!DNL Adobe Photoshop] metadata and another image-rendering application tries to access the metadata, it may not be able to access the metadata. Wenn Sie feststellen, dass Ihre Assets viele anwendungsspezifische Metadaten enthalten, können Sie einen Workflow-Schritt erstellen, der eine anwendungsspezifische Eigenschaft in eine Standardeigenschaft ändert.

* ACDSee - Metadata managed by the [!DNL ACDSee] program. Siehe [www.acdsee.com/](https://www.acdsee.com/).
* Album - [!DNL Adobe Photoshop Album].
* CQ - Used by [!DNL Experience Manager Assets].
* DAM - Used by [!DNL Experience Manager Assets].
* DEX - [Optima SC Description Explorer](http://www.optimasc.com/products/dex/index.html) ist eine Sammlung von Tools für Metadaten und Dateiverwaltung für Windows Betriebssysteme.
* CRS - [Adobe Photoshop Camera Raw](https://helpx.adobe.com/camera-raw/using/introduction-camera-raw.html).
* LR - [!DNL Adobe Lightroom].
* MediaPro - [iView MediaPro](https://en.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto und MP: Microsoft Photo.
* PDF &amp; PDF/X.
* Fotoshop und psAux - [!DNL Adobe Photoshop].

### Digital Rights Management metadata {#digital-rights-management-metadata}

* CC - [!DNL Creative Commons].
* [!DNL XMPRights].
* PLUS - [Picture Licensing Universal System](https://www.useplus.com).
* PRISM - [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata).
* PRL - PRISM Rights Language.
* PUR - PRISM-Nutzungsrechte.
* `xmpPlus` - Integration von PLUS in XMP.

### Photography-specific metadata {#photography-specific-metadata}

* Exif - Technische Informationen von der Kamera, einschließlich GPS-Position.
* CRS - [!DNL Camera Raw] Schema.
* `iptc4xmpCore` und `iptc4xmpExt`.
* TIFF: Bildmetadaten (nicht nur für TIFF-Bilder).

### Print-specific metadata {#print-specific-metadata}

* PDF und PDF/X - Adobe PDF- und Drittanbieteranwendungen.
* PRISM - [www.prismstandard.org](https://www.prismstandard.org) Publishing Requirements for Industry Standard Metadata.
* XMP.
* `xmpPG` - XMP-Metadaten für Seiten-Text.

### Multimedia-spezifische Metadaten {#multimedia-specific-metadata}

* `xmpDM` - [!DNL Dynamic Media].
* `xmpMM` - Medienverwaltung.

## Metadatengesteuerte Workflows {#metadata-driven-workflows}

Das Erstellen von durch Metadaten angetriebenen Workflows hilft Ihnen, einige Prozesse zu automatisieren, was die Effizienz verbessert. In einem metadatengesteuerten Workflow liest das Workflow-Managementsystem den Workflow und führt anschließend einige vordefinierte Aktionen aus. Im Folgenden finden Sie einige Beispiele für den Einsatz metadatengesteuerter Workflows:

* Der Workflow kann prüfen, ob ein Bild einen Titel hat oder nicht. Ist dies nicht der Fall, benachrichtigt das System, einen Titel hinzuzufügen.
* Der Arbeitsablauf kann prüfen, ob ein Copyright-Hinweis für ein Asset die Verteilung zulässt. Dementsprechend sendet das System das Asset an den einen oder anderen Server.
* Ein Workflow kann nach Assets ohne vordefinierte, obligatorische Metadaten oder Assets mit *ungültigen* Metadaten suchen.
