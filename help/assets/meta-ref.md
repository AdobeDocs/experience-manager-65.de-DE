---
title: Metadaten-Schemareferenz
description: 'Erfahren Sie mehr über die Standard-Konventionen für das Beschreiben von Asset-Metadaten, darunter Dublin Core, IPTC und weitere Metadatenschemen. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 88%

---


# Metadata schemata reference {#metadata-schemata-reference}

Die folgende Referenz enthält Informationen zu bestimmten Metadatenschemata (in alphabetischer Reihenfolge) sowie eine Liste mit Eigenschaften und den zugehörigen Definitionen.

## Dublin Core {#dublin-core}

Dublin Core-Metadaten bieten ein standardisiertes Set aus Konventionen für die Beschreibung von Assets, um die Suche nach ihnen zu erleichtern. In [!DNL Assets], the Dublin Core describes digital assets including video, sound, images, and documents.

Das einfache Dublin Core Metadata Element Set (DCMES) enthält 15 Metadatenelemente, die in der folgenden Tabelle aufgeführt werden. Jedes Dublin Core-Element ist optional und kann wiederholt werden. Sie können Dublin Core-Metadateninformationen genauso wie solche für medientypspezifische Metadaten hinzufügen oder löschen.

In addition to the DCMES, there are other metadata elements created by the Dublin Core Initiative. See the [Dublin Core initiative](https://dublincore.org/) for more information.

| Eigenschaft | Beschreibung |
| ----------- | ------------------------------------------------------------------------------------------------------------------------ |
| contributor | Die Personen oder das Unternehmen, diedafür verantwortlich sind, zum Inhalt beizutragen. |
| coverage | Der geografische Standort oder Zeitraum, den das Asset abdeckt. |
| creator | Die Personen oder das Unternehmen, die dafür verantwortlich sind, den Inhalt zu erstellen. |
| date | Datum oder Zeitraum, mit dem das Asset verknüpft ist. |
| description | Weitere Informationen zum Asset. |
| format | Das Dateiformat, das physische Medium oder die Dimensionen des Assets. [!DNL Experience Manager] verwendet `dc:format`, um den MIME-Typ des Assets zu kennzeichnen. |
| identifier | Eine eindeutige Referenz zum Asset. |
| language | Die Sprache des Assets (z. B. „en“ für Englisch). |
| publisher | Die Personen oder das Unternehmen, die dafür verantwortlich sind, das Asset verfügbar zu machen. |
| relation | Ein zugehöriges Asset. |
| rights | Informationen dazu, wer die Rechte für dieses Asset besitzt. |
| source | Ein zugehöriges Asset, aus dem das Asset abgeleitet wurde. |
| subject | Das Thema des Assets. |
| title | Ein Name für das Asset. |
| type | Die Art oder das Genre des Assets. |

## IPTC {#iptc}

Der International Press Telecommunications Council (IPTC) ist eine Arbeitsgemeinschaft aus Nachrichtenagenturen aus der ganzen Welt. Eines seiner Ziele ist die Entwicklung und Aufrechterhaltung technischer Standards. Der IPTC definiert ein Set aus Fotometadaten-Standards für Bilder, das fast universell von Fotografen anerkannt wird. Diese Metadatenstandards waren Bestandteil des umfassenderen Standards IPTC Information Interchange Model (IIM), der in den 1990er Jahren aufgestellt wurde.

Obwohl die IPTC-Kopfzeileninformationen größtenteils von XMP abgelöst wurden, sind ein IPTC-Kernschema und ein Erweiterungsschema für XMP verfügbar. In Bildprogrammen werden XMP- und IPTC-Eigenschaften synchronisiert.
