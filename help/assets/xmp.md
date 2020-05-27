---
title: Unterstützung für XMP-Metadaten in Adobe Experience Manager Assets.
description: Erfahren Sie mehr über den XMP-Metadatenstandard (Extensible Metadata Platform), der von Experience Manager Assets für die Metadatenverwaltung verwendet wird. XMP liefert ein Standardformat für die Erstellung, die Verarbeitung und den Austausch von Metadaten für eine Vielzahl an Anwendungen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 89%

---


# XMP-Metadaten {#xmp-metadata}

XMP (Extensible Metadata Platform) ist der Metadatenstandard, der von Adobe Experience Manager Assets für alle Metadatenverwaltung verwendet wird. XMP liefert ein Standardformat für die Erstellung, die Verarbeitung und den Austausch von Metadaten für eine Vielzahl an Anwendungen.

XMP bietet nicht nur universelle Metadatenkodierung, die in alle Dateiformate eingebettet werden kann, sondern auch ein [Rich-Content-Modell](xmp.md#xmp-core-concepts). Außerdem wird XMP [von Adobe](xmp.md#advantages-of-xmp) und anderen Unternehmen unterstützt, sodass Benutzer, die XMP in Kombination mit  Assets einsetzen, über eine leistungsstarke Plattform verfügen.

Die [XMP-Spezifikation](https://www.adobe.com/devnet/xmp.html) wird von Adobe zur Verfügung gestellt.

## Was ist XMP? {#what-is-xmp}

 Assets unterstützt nativ XMP (die Extensible Metadata Platform von Adobe). XMP ist ein Standard für die Verarbeitung und Speicherung von standardisierten und proprietären Metadaten in digitalen Assets. XMP ist als der gemeinsame Standard konzipiert, dank dem mehrere Anwendungen effektiv mit Metadaten arbeiten können.

Produktionsfachleute verwenden beispielsweise die integrierte XMP-Unterstützung in den Adobe-Anwendungen, um Informationen über mehrere Dateiformate weiterzugeben. Das Asset-Repository extrahiert die XMP-Metadaten und verwendet sie zur Verwaltung des Inhaltslebenszyklus und Angebote zur Erstellung von Workflows.

XMP standardisiert die Art, wie Metadaten definiert, erstellt und verarbeitet werden, indem ein Datenmodell, ein Speichermodell und Schemata bereitgestellt werden. Diese Grundlagen werden alle in diesem Abschnitt behandelt.

Alle Legacy-Metadaten aus EXIF, ID3 oder Microsoft Office werden automatisch in XMP übersetzt. Dies kann erweitert werden, um kundenspezifische Metadatenschemata wie Produktkataloge zu unterstützen.

Metadaten in XMP bestehen aus einer Reihe von Eigenschaften. Diese Eigenschaften sind stets mit einer
bestimmten Entität verknüpft, die als Ressource bezeichnet wird. Die Eigenschaften beziehen sich also auf die Ressource. Bei XMP ist die Ressource stets das Asset.

### Adobe {#adobe}

Adobe hat den XMP-Standard zunächst im Rahmen des Adobe Acrobat-Softwareprodukts eingeführt. Mittlerweile ist der XMP-Standard weit verbreitet.

### XMP ecosystem {#xmp-ecosystem}

XMP definiert ein [Metadatenmodell](https://de.wikipedia.org/wiki/Metadaten), das mit jedem definierten Satz von Metadatenelementen verwendet werden kann. XMP definiert außerdem bestimmte [Schemata](https://de.wikipedia.org/wiki/Schemasprache_(XML)) für Standardeigenschaften, die für die Aufzeichnung des Verlaufs einer Ressource nützlich sind, während sie mehrere Verarbeitungsschritte durchläuft – von der Aufnahme über [Scannen](https://de.wikipedia.org/wiki/Scanner_(Datenerfassung)) oder Verfassen als Text und Bildbearbeitungsschritte (wie [Zuschneiden](https://de.wikipedia.org/wiki/Cropping) oder Farbkorrektur) bis hin zur Zusammensetzung in das endgültige Bild. XMP ermöglicht es jedem Softwareprogramm oder Gerät, eigene Informationen zu einer digitalen Ressource hinzuzufügen, die dann in der endgültigen digitalen Datei gespeichert werden kann.

XMP wird am häufigsten mit einer Untergruppe des [W3C](https://de.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://de.wikipedia.org/wiki/Resource_Description_Framework) (RDF) serialisiert und gespeichert, das wiederum in [XML](https://de.wikipedia.org/wiki/Extensible_Markup_Language) ausgedrückt wird.

## Vorteile von XMP   {#advantages-of-xmp}

XMP bietet die folgenden Vorteile gegenüber anderen Kodierungsstandards und Schemata:

* XMP-basierte Metadaten sind sehr leistungsstark und fein granuliert.
* Mit XMP können Sie mehrere Werte für eine Eigenschaft festlegen.
* XMP verfügt über standardisierte Kodierung, wodurch Sie Metadaten einfach austauschen können.
* XMP ist erweiterbar. Sie können Assets zusätzliche Informationen hinzufügen.

### Erweiterbar {#extensible}

Das XMP-Standardformat ist erweiterbar, sodass Sie den XMP-Daten benutzerdefinierte Arten von Metadaten hinzufügen können. Bei EXIF ist dies dagegen nicht möglich. Die feste Liste der Eigenschaften kann nicht erweitert werden.

>[!NOTE]
>
>XMP lässt im Allgemeinen nicht zu, dass binäre Datentypen eingebettet werden. Um binäre Daten wie etwa Miniaturansichten in XMP zu übertragen, müssen diese in einem XML-kompatiblen Format wie beispielsweise `Base64` kodiert werden.

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
