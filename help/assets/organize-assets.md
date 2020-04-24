---
title: Digitale Assets organisieren
description: Organisieren Sie Ihre digitalen Assets, Bilder, Dateien, Ordner usw. mit Experience Manager.
contentOwner: AG
translation-type: tm+mt
source-git-commit: abc4821ec3720969bf1c2fb068744c07477aca46

---


# Digitale Assets organisieren {#organize-digital-assets}

Alle digitalen Assets, Metadaten und Inhalte von Microsoft Office- und PDF-Dokumenten werden extrahiert und für die Suche aufbereitet. Die Suche ermöglicht weitreichende Filtermöglichkeiten für Assets und hält dabei vollständig die korrekten Berechtigungen ein. Metadaten werden in den Metadaten in Digital Asset Management ausführlich behandelt.

AEM Assets unterstützt verschiedene Methoden zum Organisieren von Inhalten. Sie können sie hierarchisch organisieren, indem Sie Ordner verwenden oder sie auf ungeordnete, Ad-hoc-Weise organisieren, z. B. mithilfe von Tags. Benutzer können Tags im DAM Asset Editor bearbeiten, in dem Teil-Assets, Ausgabeformate und Metadaten angezeigt werden.

## Assets in Ordnern organisieren {#organize-using-folders}

Die einfachste Möglichkeit zum Organisieren von Assets besteht darin, diese in Ordnern zu speichern. Es entspricht dem Organisieren von Dateien in Ordnern in unserem lokalen Dateisystem. Weitere Informationen zum Erstellen und Verwalten von Ordnern finden Sie unter [Verwalten von Assets](managing-assets-touch-ui.md). Wie Sie Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie mit den Dateien in diesen Ordnern umgehen, kann erhebliche Auswirkungen auf die Verarbeitung dieser Assets haben. Durch die Verwendung konsistenter und geeigneter Strategien zur Datei- und Ordnerbenennung sowie einer bewährten Metadatenpraxis können Sie das Beste aus Ihrem digitalen Assets-Repository machen.

* In den meisten Fällen wächst Ihr Repository für digitale Assets immer. Daher ist es wichtig, die Verwendung von Metadaten, die Ordnerstruktur und die Dateibenennung zu einem frühen Zeitpunkt des Inhaltserstellungszyklus zu formalisieren.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Diese Konsistenz hilft Ihnen, Ihre Assets besser zu verwalten und zu verarbeiten. Beispielsweise können Sie mithilfe von Assets, die in den folgenden Ordnertypen platziert werden, geeignete [Profil für die Verarbeitung](processing-profiles.md)von Assets verwenden:

   * **Entwicklungsordner**: enthält digitale Assets, an denen Sie derzeit arbeiten.
   * **Clientordner**: enthält digitale Assets, die auf Clients oder Projektnamen basieren.
   * **Hauptordner**: enthält digitale Originalelemente aus der Quelle.
   * **Ausgabeordner**: enthält Darstellungen und Kopien der digitalen Originalelemente.
   * **Dateigrößenordner**: enthält digitale Assets, die auf kleinen, mittleren oder großen Dateigrößen basieren.
   * **Staging-Ordner**: enthält digitale Assets, die live auf Ihrer Website veröffentlicht werden können.
   * **MIME-Typordner**: enthält digitale Assets, die für MIME-Typen wie Bilder, Dokumente und Multimedia spezifisch sind.
   * **Archivieren von Ordnern**: enthält zurückgestellte digitale Assets.
   * **Datumsbasierte Ordner**: enthält digitale Assets, die auf einem Erstellungsdatum oder einem Datum der letzten Änderung basieren.

* Erstellen Sie einen Ordner mit Ordnern, die sich wahrscheinlich nicht ändern, sodass Anpassungen oder Automatisierungen weiterhin funktionieren. Beispielsweise funktionieren die zugewiesenen Profil weiterhin.
* If an asset is already published, then you use AEM to move the asset to another folder, and re-publish from its new location, the original published asset location is still available, along with the newly re-published asset. The original published asset, however, is *lost* to AEM and cannot be unpublished. Als Best Practice sollten Sie daher zunächst die Veröffentlichung eines Assets rückgängig machen und es dann in einen anderen Ordner verschieben.

## Organisieren von Assets mit Tags {#use-tags-to-organize-assets}

Mithilfe von Tags als Metadaten können Sie Assets mühelos suchen, Sammlungen mit den Suchergebnissen erstellen, die Suchrangliste für einige Assets verbessern und AI-Algorithmen von Adobe Sensei zur Ermittlung von Assets nutzen.

Adobe Experience Manager Assets verwendet einen Selbstlernalgorithmus, um hochgradig beschreibende Tags zu erstellen, mit denen Sie das richtige Asset in nur wenigen Klicks finden können. Beim intelligenten Tagging wird Adobe Sensei verwendet, unser Framework für künstliche Intelligenz und maschinelles Lernen, mit dem Standard- und unternehmensspezifische Tags erkannt und auf Bilder angewendet werden können. Intelligente Tags können auch Inhalte, einzelne Wörter oder Ausdrücke identifizieren und automatisch beschreibende Tags auf Assets anwenden

Weitere Informationen finden Sie in den folgenden Artikeln:

* [Informationen zu Tags in AEM](/help/sites-authoring/tags.md)
* [Bearbeiten von Asset-Metadaten](meta-edit.md)
* [Verbesserte intelligente Tags in Assets](enhanced-smart-tags.md)

## Als Sammlungen organisieren {#organize-as-collections}

Mit Asset-Sammlungen in Experience Manager Assets können Sie die Erstellung, Bearbeitung und Freigabe von Assets zwischen Benutzern optimieren. Erstellen Sie verschiedene Arten von Sammlungen basierend auf der Art und Weise, wie Sie sie verwenden, einschließlich Sammlungen, die eine statische Referenz-Liste von Assets, Ordnern und Sammlungen enthalten, sowie Sammlungen, die Assets basierend auf Suchkriterien abrufen.  Sie können auch Sammlungen mit Assets von verschiedenen Orten erstellen und sie für mehrere Benutzer mit unterschiedlichen Zugriffs-, Anzeige- und Bearbeitungsberechtigungen freigeben.

For more information, see [manage collections](managing-collections-touch-ui.md)

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Organisieren Sie Ihre Assets für die Verwendung von Profilen {#organize-to-use-profiles}

Ein verarbeitendes Profil enthält Verarbeitungsbefehle für Assets, die für Assets gelten, die in vordefinierte  hochgeladen werden. Mit Profilen wird die Verarbeitung von Ordnerinhalten oder neu hochgeladenen Assets automatisiert. Sie können Profil nutzen, um Ihre Assets besser zu organisieren.

Durch die Standardisierung der Metadaten-Nutzung, Dateibenennung und Ordnerstruktur wird sichergestellt, dass Sie mit zunehmender Anzahl digitaler Assets verarbeitende Profil präziser und konsistenter auf Ordner anwenden können.

Weitere Informationen zu den verschiedenen Profilen, die Sie zur Verarbeitung von Assets erstellen und verwalten können, finden Sie unter

* [Profile zur Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md)
* [Metadatenprofile](metadata-profiles.md)
* [Videoprofile](video-profiles.md)
* [Profile für dynamische Medienbilder](image-profiles.md)
