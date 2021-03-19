---
title: Digitale Assets organisieren
description: Organisieren Sie Ihre digitalen Assets, Bilder, Dateien, Ordner usw. mit Experience Manager.
contentOwner: AG
role: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 8%

---


# Digitale Assets organisieren {#organize-digital-assets}

Alle digitalen Assets, Metadaten und Inhalte von Microsoft Office- und PDF-Dokumenten werden extrahiert und für die Suche aufbereitet. Die Suche ermöglicht weitreichende Filtermöglichkeiten für Assets und hält dabei vollständig die korrekten Berechtigungen ein. Metadaten werden in den Metadaten in Digital Asset Management ausführlich behandelt.

[!DNL Experience Manager Assets] unterstützt mehrere Möglichkeiten zum Organisieren von Inhalten. Sie können sie hierarchisch organisieren, indem Sie Ordner verwenden oder sie auf ungeordnete, Ad-hoc-Weise organisieren, z. B. mithilfe von Tags. Benutzer können Tags im DAM Asset Editor bearbeiten, in dem Teil-Assets, Ausgabeformate und Metadaten angezeigt werden.

## Organisieren von Assets in Ordnern {#organize-using-folders}

Die einfachste Möglichkeit zum Organisieren von Assets besteht darin, diese in Ordnern zu speichern. Es entspricht dem Organisieren von Dateien in Ordnern in unserem lokalen Dateisystem. Weitere Informationen zum Erstellen und Verwalten von Ordnern finden Sie unter [Verwalten von Assets](manage-assets.md). Wie Sie Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie mit den Dateien in diesen Ordnern umgehen, kann erhebliche Auswirkungen auf die Verarbeitung dieser Assets haben. Durch die Verwendung konsistenter und geeigneter Strategien zur Datei- und Ordnerbenennung sowie einer bewährten Metadatenpraxis können Sie das Beste aus Ihrem digitalen Assets-Repository machen.

* In den meisten Fällen wächst Ihr Repository für digitale Assets immer. Daher ist es wichtig, die Verwendung von Metadaten, die Ordnerstruktur und die Dateibenennung zu einem frühen Zeitpunkt des Inhaltserstellungszyklus zu formalisieren.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Diese Konsistenz hilft Ihnen, Ihre Assets besser zu verwalten und zu verarbeiten. Beispielsweise können Sie mithilfe von Assets, die in den folgenden Ordnertypen platziert werden, geeignete [Profil für die Verarbeitung von Assets](processing-profiles.md) verwenden:

   * **Entwicklungsordner**: enthält digitale Assets, an denen Sie derzeit arbeiten.
   * **Clientordner**: enthält digitale Assets, die auf Clients oder Projektnamen basieren.
   * **Primär Ordner**: enthält digitale Originalelemente aus der Quelle.
   * **Ausgabeordner**: enthält Darstellungen und Kopien der digitalen Originalelemente.
   * **Dateigrößenordner**: enthält digitale Assets, die auf kleinen, mittleren oder großen Dateigrößen basieren.
   * **Staging-Ordner**: enthält digitale Assets, die live auf Ihrer Website veröffentlicht werden können.
   * **MIME-Typordner**: enthält digitale Assets, die für MIME-Typen wie Bilder, Dokumente und Multimedia spezifisch sind.
   * **Archivieren von Ordnern**: enthält zurückgestellte digitale Assets.
   * **Datumsbasierte Ordner**: enthält digitale Assets, die auf einem Erstellungsdatum oder einem Datum der letzten Änderung basieren.

* Erstellen Sie einen Ordner mit Ordnern, die sich wahrscheinlich nicht ändern, sodass Anpassungen oder Automatisierungen weiterhin funktionieren. Beispielsweise funktionieren die zugewiesenen Profil weiterhin.
* Wenn ein Asset bereits veröffentlicht wurde und Sie dann mit [!DNL Experience Manager] das Asset in einen anderen Ordner verschieben und es erneut veröffentlichen, ist der ursprüngliche Speicherort des veröffentlichten Assets zusammen mit dem neu veröffentlichten Asset weiterhin verfügbar. Das ursprünglich veröffentlichte Asset ist jedoch *lost* bis [!DNL Experience Manager] und kann nicht rückgängig gemacht werden. Als Best Practice sollten Sie daher zunächst die Veröffentlichung eines Assets rückgängig machen und es dann in einen anderen Ordner verschieben.

## Organisieren von Assets mit den Tags {#use-tags-to-organize-assets}

Mithilfe von Tags als Metadaten können Sie mühelos Assets suchen, Sammlungen mit den Suchergebnissen erstellen, die Suchrangliste für einige Assets verbessern und AI-Algorithmen von Adobe Sensei zur Ermittlung von Assets nutzen.

[!DNL Adobe Experience Manager Assets] verwendet einen Selbstlernalgorithmus, um hochgradig beschreibende Tags zu erstellen, mit denen Sie das richtige Asset in nur wenigen Klicks finden können. Beim intelligenten Tagging werden Adobe Sensei, unser künstliches Intelligenz- und maschinelles Lernen-Framework, eingesetzt, das sowohl Standard- als auch unternehmensspezifische Tags erkennen und auf Bilder anwenden kann. Intelligente Tags können auch Inhalte, einzelne Wörter oder Ausdrücke identifizieren und automatisch beschreibende Tags auf Assets anwenden

Weitere Informationen finden Sie in den folgenden Artikeln:

* [Tags im Experience Manager](/help/sites-authoring/tags.md)
* [Bearbeiten von Asset-Metadaten](metadata.md)
* [Verbesserte intelligente Tags in Assets](enhanced-smart-tags.md)

## Als Sammlungen organisieren {#organize-as-collections}

Mit Asset-Sammlungen in [!DNL Experience Manager Assets] können Sie die Erstellung, Bearbeitung und Freigabe von Assets zwischen Benutzern optimieren. Erstellen Sie verschiedene Arten von Sammlungen basierend auf der Art und Weise, wie Sie sie verwenden, einschließlich Sammlungen, die eine statische Referenz-Liste von Assets, Ordnern und Sammlungen enthalten, sowie Sammlungen, die Assets basierend auf Suchkriterien abrufen.  Sie können auch Sammlungen mit Assets von verschiedenen Orten erstellen und sie für mehrere Benutzer mit unterschiedlichen Zugriffs-, Anzeige- und Bearbeitungsberechtigungen freigeben.

Weitere Informationen finden Sie unter [Sammlungen verwalten](manage-collections.md)

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Organisieren Sie Ihre Assets für die Verwendung von Profilen {#organize-to-use-profiles}

Ein verarbeitendes Profil enthält Verarbeitungsbefehle für Elemente, die in vordefinierte  hochgeladen werden. [!DNL Assets] Mit Profilen wird die Verarbeitung von Ordnerinhalten oder neu hochgeladenen Assets automatisiert. Sie können Profil nutzen, um Ihre Assets besser zu organisieren.

Durch die Standardisierung der Metadaten-Nutzung, Dateibenennung und Ordnerstruktur wird sichergestellt, dass Sie mit zunehmender Anzahl digitaler Assets verarbeitende Profil präziser und konsistenter auf Ordner anwenden können.

>[!MORELIKETHIS]
>
>* [Profile zum Verarbeiten von Metadaten, Bildern und Videos](processing-profiles.md).
>* [Metadatenprofile](/help/assets/metadata-config.md#metadata-profiles).
>* [Videoprofile](video-profiles.md).
>* [Dynamic Media Image Profils](image-profiles.md).

