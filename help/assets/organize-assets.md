---
title: Digitale Assets organisieren
description: Organisieren Sie mithilfe von Experience Manager Ihre digitalen Assets, Bilder, Dateien, Ordner usw.
contentOwner: AG
role: User
feature: Asset Management,Search
exl-id: d6f815b5-e4fc-4f8c-a6c1-9e50035ab9f2
hide: true
source-git-commit: 681d1e6bd885b801b930e580d95645f160f17cea
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 75%

---

# Digitale Assets organisieren {#organize-digital-assets}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| Adobe Experience Manager (AEM) as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/organize-assets.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Alle digitalen Assets, Metadaten und Inhalte von Microsoft® Office- und PDF-Dokumenten werden extrahiert und für die Suche aufbereitet. Die Suche ermöglicht ein ausgefeiltes Filtern von Assets und respektiert vollständig die entsprechenden Berechtigungen. Metadaten werden in „Metadaten in Digital Asset Management“ ausführlich behandelt.

[!DNL Experience Manager Assets] unterstützt verschiedene Methoden zum Organisieren von Inhalten. Sie können sie hierarchisch mithilfe von Ordnern organisieren oder ungeordnet und ad hoc organisieren, beispielsweise mithilfe von Tags. Benutzer können Tags im DAM-Asset-Editor bearbeiten, in dem Teil-Assets, Ausgabedarstellungen und Metadaten angezeigt werden.

## Organisieren von Assets in Ordnern {#organize-using-folders}

Die einfachste Möglichkeit zum Organisieren von Assets besteht darin, sie in Ordnern zu speichern. Dies entspricht dem Organisieren von Dateien in Ordnern in Ihrem lokalen Dateisystem. Weitere Informationen zum Erstellen und Verwalten von Ordnern finden Sie unter [Verwalten von Assets](manage-assets.md). Wie Sie Ihre Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern handhaben, hat daher eine erhebliche Auswirkung darauf, wie diese Assets verarbeitet werden. Durch die Verwendung konsistenter und angemessener Strategien für die Datei- und Ordnernamen sowie guter Metadatenpraktiken können Sie das gesamte Repository für digitale Assets optimal nutzen.

* Normalerweise ist Ihr Repository für digitale Assets immer im Wachstum begriffen. Daher ist es wichtig, die Verwendung von Metadaten, die Ordnerstruktur und die Dateibenennung frühzeitig im Erstellungszyklus des Inhalts zu formalisieren.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Diese Konsistenz hilft Ihrem Prozess und bei der Verwaltung Ihrer Assets. Beispielsweise können Assets, die in den folgenden Ordnern abgelegt sind, bei der [Verwendung geeigneter Profile für die Asset-Verarbeitung](processing-profiles.md) helfen:

   * **Entwicklungsordner**: enthält digitale Assets, an denen Sie gerade arbeiten.
   * **Kundenordner**: enthalten digitale Assets basierend auf Kunden- oder Projektnamen.
   * **Primäre Ordner**: enthalten digitale Quell-Assets in ihrer Originalform.
   * **Ausgabedarstellungsordner**: enthalten Ausgabedarstellungen und Kopien der digitalen Quell-Assets in Originalform.
   * **Dateigrößenordner**: enthalten digitale Assets basierend auf kleinen, mittleren oder großen Dateigrößen.
   * **Staging-Ordner**: enthalten digitale Assets, die für die Veröffentlichung auf Ihrer Website bereit sind.
   * **MIME-Typ-Ordner**: enthalten digitale Assets entsprechend den MIME-Typen, z. B. Bilder, Dokumente und Multimedia.
   * **Archivordner**: enthalten nicht mehr verwendete digitale Assets.
   * **Datumsbasierte Ordner**: enthalten digitale Assets basierend auf einem Erstellungsdatum oder dem letzten Änderungsdatum.

* Erstellen Sie ein Verzeichnis mit Ordnern, die sich wahrscheinlich nicht ändern werden, damit Anpassungen oder Automatisierungen weiterhin funktionieren. Beispielsweise funktionieren die zugewiesenen Verarbeitungsprofile weiterhin.
* Wenn ein Asset bereits veröffentlicht wurde, verwenden Sie [!DNL Experience Manager] Um das Asset in einen anderen Ordner zu verschieben und von seinem neuen Speicherort zu veröffentlichen, ist der ursprünglich veröffentlichte Asset-Speicherort weiterhin verfügbar, zusammen mit dem neu veröffentlichten Asset. Das ursprünglich veröffentlichte Asset ist allerdings für [!DNL Experience Manager] *nicht mehr zugänglich*. Daher kann dessen Veröffentlichung nicht rückgängig gemacht werden. Daher empfiehlt es sich, zunächst die Veröffentlichung eines Assets rückgängig zu machen und es dann in einen anderen Ordner zu verschieben.

## Organisieren von Assets mit Tags {#use-tags-to-organize-assets}

Mithilfe von Tags als Metadaten können Sie mühelos nach Assets suchen, Sammlungen mithilfe der Suchergebnisse erstellen, die Suche nach einigen Assets optimieren und künstliche Intelligenzalgorithmen von Adobe Sensei für die Asset-Erkennung verwenden.

[!DNL Adobe Experience Manager Assets] verwendet einen selbstlernenden Algorithmus, um hochgradig beschreibende Tags zu erstellen, mit denen Sie das richtige Asset mit nur wenigen Klicks finden können. Smart-Tagging nutzt Adobe Sensei, das künstliche Intelligenz- und maschinelles Lernframework der Adobe, das trainiert werden kann, um Standard- und unternehmensspezifische Tags zu erkennen und auf Bilder anzuwenden. Smart-Tags können auch Inhalte, einzelne Wörter oder Ausdrücke identifizieren und automatisch beschreibende Tags auf Assets anwenden.

Weitere Informationen finden Sie in den folgenden Artikeln:

* [Über Tags in Experience Manager](/help/sites-authoring/tags.md)
* [Bearbeiten von Asset-Metadaten](metadata.md)
* [Erweiterte Smart-Tags in Assets](enhanced-smart-tags.md)

## Organisieren als Sammlungen {#organize-as-collections}

Mit Asset-Sammlungen in [!DNL Experience Manager Assets] können Sie die Möglichkeit optimieren, Assets zu erstellen, zu bearbeiten und zwischen Benutzern freizugeben. Erstellen Sie verschiedene Arten von Sammlungen basierend auf ihrer Verwendung, einschließlich Sammlungen, die eine statische Referenzliste von Assets, Ordnern und Sammlungen enthalten, und Sammlungen, die Assets basierend auf Suchkriterien abrufen. Sie können auch Sammlungen mit Assets aus verschiedenen Speicherorten erstellen und sie für mehrere Benutzer mit unterschiedlichen Zugriffs-, Anzeige- und Bearbeitungsberechtigungen freigeben.

Weitere Informationen finden Sie unter [Sammlungen verwalten](manage-collections.md).

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Organisieren von Assets, um Profile zu verwenden {#organize-to-use-profiles}

Ein Verarbeitungsprofil enthält [!DNL Assets]-Verarbeitungsbefehle, die für Assets gelten, die in vordefinierte Ordner hochgeladen werden. Profile werden verwendet, um die Verarbeitung von Inhalten eines Ordners oder von neu hochgeladenen Assets zu automatisieren. Sie können Profile verwenden, um Ihre Assets besser zu organisieren.

Indem Sie die Verwendung von Metadaten, die Benennung von Dateien und die Ordnerstruktur standardisieren, wird sichergestellt, dass Sie auch bei einem stets wachsenden Pool mit digitalen Assets Verarbeitungsprofile präziser und konsistenter auf Ordner anwenden können.

>[!MORELIKETHIS]
>
>* [Profile zur Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md).
>* [Metadatenprofile](/help/assets/metadata-config.md#metadata-profiles).
>* [Videoprofile](video-profiles.md).
>* [Dynamic Media-Bildprofile](image-profiles.md).
