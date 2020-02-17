---
title: Unterstützung für XMP-Metadaten in AEM Assets
description: Erfahren Sie mehr über den XMP-Metadatenstandard (Extensible Metadata Platform), der von AEM Assets zur Metadatenverwaltung verwendet wird. XMP liefert ein Standardformat für die Erstellung, die Verarbeitung und den Austausch von Metadaten für eine Vielzahl an Anwendungen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# XMP metadata {#xmp-metadata}

XMP (Extensible Metadata Platform) ist der Metadatenstandard, der von AEM Assets für die gesamte Metadatenverwaltung eingesetzt wird. XMP liefert ein Standardformat für die Erstellung, die Verarbeitung und den Austausch von Metadaten für eine Vielzahl an Anwendungen.

Aside from offering universal metadata encoding that can be embedded into all file formats, XMP provides a rich [content model](xmp.md#xmp-core-concepts) and is [supported by Adobe](xmp.md#advantages-of-xmp) and other companies, so that users of XMP in combination with AEM Assets have a powerful platform to build upon.

Die [XMP-Spezifikation](https://www.adobe.com/devnet/xmp.html) wird von Adobe zur Verfügung gestellt.

## Was ist XMP? {#what-is-xmp}

AEM Assets unterstützt nativ XMP (die Extensible Metadata Platform von Adobe). XMP ist ein Standard für die Verarbeitung und Speicherung von standardisierten und proprietären Metadaten in digitalen Assets. XMP ist als der gemeinsame Standard konzipiert, dank dem mehrere Anwendungen effektiv mit Metadaten arbeiten können.

Produktionsexperten nutzen beispielsweise die integrierte XMP-Unterstützung innerhalb der Adobe-Anwendungen, um Informationen über mehrere Dateiformate hinweg zu übergeben. Das AEM Assets-Repository extrahiert die XMP-Metadaten und verwaltet damit den Inhaltslebenszyklus. Außerdem wird die Erstellung von Automatisierungs-Workflows ermöglicht.

XMP standardisiert die Art, wie Metadaten definiert, erstellt und verarbeitet werden, indem ein Datenmodell, ein Speichermodell und Schemata bereitgestellt werden. Diese Grundlagen werden alle in diesem Abschnitt behandelt.

Alle Legacy-Metadaten aus EXIF, ID3 oder Microsoft Office werden automatisch in XMP übersetzt. Dies kann erweitert werden, um kundenspezifische Metadatenschemata wie Produktkataloge zu unterstützen.

Metadaten in XMP bestehen aus einer Reihe von Eigenschaften. Diese Eigenschaften sind stets mit einer
bestimmten Entität verknüpft, die als Ressource bezeichnet wird. Die Eigenschaften beziehen sich also auf die Ressource. Bei XMP ist die Ressource stets das Asset.

### Adobe {#adobe}

Adobe hat den XMP-Standard zunächst im Rahmen des Adobe Acrobat-Softwareprodukts eingeführt. Mittlerweile ist der XMP-Standard weit verbreitet.

### XMP ecosystem {#xmp-ecosystem}

XMP definiert ein [Metadaten](https://en.wikipedia.org/wiki/Metadata)-Modell, das mit jedem definierten Set aus Metadatenelementen verwendet werden kann. XMP definiert außerdem bestimmte [Schemata](https://en.wikipedia.org/wiki/XML_schema) für grundlegende Eigenschaften, die zum Aufzeichnen des Verlaufs einer Ressource durch mehrere Verarbeitungsschritte nützlich sind – vom Fotografieren, [Scannen](https://en.wikipedia.org/wiki/Image_scanner) oder Verfassen als Text über Fotobearbeitungsschritte (wie [Beschneiden](https://en.wikipedia.org/wiki/Cropping_%28image%29) oder Farbanpassung) bis hin zur Zusammenstellung des endgültigen Bildes. Dank XMP kann jedes dabei verwendete Softwareprogramm oder Gerät eigene Informationen zu einer digitalen Ressource hinzufügen, die dann in der endgültigen digitalen Datei beibehalten werden kann.

XMP wird meist mit einer Teilmenge des [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF) serialisiert und gespeichert. Dies wird wiederum im [XML](https://en.wikipedia.org/wiki/XML) ausgedrückt.

## Vorteile von XMP {#advantages-of-xmp}

XMP bietet die folgenden Vorteile gegenüber anderen Kodierungsstandards und Schemata:

* XMP-basierte Metadaten sind sehr leistungsstark und fein granuliert.
* Mit XMP können Sie mehrere Werte für eine Eigenschaft festlegen.
* XMP verfügt über standardisierte Kodierung, wodurch Sie Metadaten einfach austauschen können.
* XMP ist erweiterbar. Sie können Ihren Assets weitere Informationen hinzufügen.

### Erweiterbar {#extensible}

Das XMP-Standardformat ist erweiterbar, sodass Sie den XMP-Daten benutzerdefinierte Arten von Metadaten hinzufügen können. Bei EXIF ist dies dagegen nicht möglich. Die feste Liste der Eigenschaften kann nicht erweitert werden.

>[!NOTE]
>
>XMP lässt im Allgemeinen nicht zu, dass binäre Datentypen eingebettet werden. To carry binary data in XMP, for example, thumbnail images, they must be encoded in an XML-friendly format such as `Base64`.

## Wesentliche XMP-Grundlagen {#xmp-core-concepts}

In den folgenden Abschnitten werden die wesentlichen Grundlagen von XMP beschrieben, einschließlich Namespaces und Schemata, Eigenschaften und Werten sowie Sprachalternativen.

### Namespaces und Schemata {#namespaces-and-schemata}

Ein XMP-Schema ist ein Set aus Eigenschaftsnamen in einem gemeinsamen XML-Namespace, der
den Datentyp und beschreibende Informationen umfasst. Ein XMP-Schema wird durch die zugehörige XML-Namespace-URI identifiziert. Durch Verwendung von Namespaces werden Konflikte zwischen Eigenschaften in verschiedenen Schemata verhindert, die denselben Namen, aber eine andere Bedeutung haben.

Beispiel: Die Eigenschaft `Creator` in zwei unabhängig voneinander entwickelten Schemata kann einerseits für die Person stehen, die das Asset erstellt hat, oder andererseits für die Anwendung, von der das Asset erstellt wurde (z. B. Adobe Photoshop).

### Eigenschaften und Werte {#properties-and-values}

XMP kann Eigenschaften von einem oder mehreren der Schemata umfassen.

Viele Adobe-Anwendungen verwenden beispielsweise Folgendes:

* Dublin Core-Schema: dc:title, dc:creator, dc:subject, dc:format, dc:rights
* XMP-Basisschema: xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* XMP-Rechteverwaltungsschema: xmpRights:WebStatement, xmpRights:Marked
* XMP-Medienmanagement-Schema: xmpMM:DocumentID

### Sprachalternativen {#language-alternatives}

Mit XMP können Sie die Eigenschaft `xml:lang` zu Texteigenschaften hinzufügen, um die Sprache des Textes anzugeben.
