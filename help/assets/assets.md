---
title: Einführung in [!DNL Adobe Experience Manager Assets].
description: Erfahren Sie mehr über das digitale Asset-Management, seine Anwendungsfälle [!DNL Adobe Experience Manager Asset] und Angebote.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d5b3a442756e95c15cb01c4117a83b761dc8367
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 38%

---


# Info [!DNL Adobe Experience Manager Assets] als DAM-Lösung {#administering-assets}

[!DNL Assets] ist ein DAM-Tool (Digital Asset Management), das ein integraler Bestandteil der [!DNL Experience Manager] Plattform ist und Ihrem Unternehmen die Verwaltung und Verteilung digitaler Assets ermöglicht. Benutzer in einem Unternehmen können viele Arten digitaler Assets wie Bilder, Videos, Dokumente, Audioclips, 3D-Dateien und Rich-Media-Daten verwalten, speichern und abrufen, um sie im Web, in Printmedien und für die digitale Verteilung zu verwenden.

## Was ist Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] ermöglicht die unternehmensweite Frei- und Weitergabe der wichtigsten digitalen Assets einer Organisation. Benutzer in einem Unternehmen können digitale Assets wie Bilder, Grafiken, Audio, Video und Dokumente über eine Webschnittstelle (oder einen CIFS- oder WebDAV-Ordner) speichern, verwalten und darauf zugreifen.

[!DNL Assets] können Sie Folgendes [!DNL Experience Manager] ausführen:

* Hinzufügen und Freigeben von Bildern, Dokumenten, Audiodateien und Videodateien in einer Vielzahl von Dateiformaten.
* Verwalten Sie Assets, indem Sie sie nach Tags, Leuchtkästen oder Sternen (Ihren Favoriten) gruppieren. Hinzufügen von Anmerkungen zu Assets.
* Auffinden von Assets durch Durchsuchen von Dateinamen, des Volltextes von Dokumenten und durch Suchvorgänge nach Datum, Dokumenttyp und Tags.
* Hinzufügen oder Bearbeiten von Metadateninformationen für Assets. Metadaten werden automatisch mit dem entsprechenden Asset in einer Version zusammengefasst. Sie können Asset-Metadaten importieren und exportieren.
* Ausführen von Bildbearbeitungsvorgängen, beispielsweise Skalierung und Hinzufügen von Bildfiltern. Importieren und Exportieren mehrerer digitaler Assets gleichzeitig mithilfe eines WebDAV- oder CIFS-Ordners.
* Verwenden von Workflows und Benachrichtigungen, um die gemeinsame Verarbeitung und den gemeinsamen Download mehrerer Assets zu ermöglichen und Zugriffsrechte auf Assets zu verwalten.

### [!DNL Experience Manager Assets] integriert ist mit [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] vollständig in alle Anwendungsfälle integriert [!DNL Sites] und funktioniert nahtlos. Beim Erstellen von Webseiten können die [!DNL Sites] Autoren beispielsweise die digitalen Assets über die Inhaltssuche suchen und verwenden. Die Benutzeroberfläche von [!DNL Assets] ist identisch mit der von [!DNL Sites]. Ausführliche Informationen finden Sie unter [Übersicht über Sites](/help/sites-authoring/page-authoring.md) .

Die Benutzeroberfläche ist die gleiche wie die [!DNL Sites]. Ausführliche Informationen finden Sie unter [Übersicht über die Sites](/help/sites-authoring/page-authoring.md) .

### Digital Asset Management versus image component {#digital-asset-management-versus-image-component}

Berücksichtigen Sie bei der Entscheidung, ob ein Bild in das DAM-Repository eingefügt oder eine Bildkomponente verwendet werden soll, den Lebenszyklus des Bilds:

* Wenn das Bild denselben Lebenszyklus wie die Seite hat, verwenden Sie die Bildkomponente.
* Wenn das Bild einen eigenen Lebenszyklus hat – beispielsweise, wenn Sie das Bild zweimal oder außerhalb von WCM verwenden –, verwenden Sie [!DNL Assets].

## Was sind digitale Assets? {#what-are-digital-assets}

Ein Asset ist ein digitales Dokument, Bild, Video oder Audio (oder ein Teil davon), das mehrere Darstellungen aufweisen kann und Teilassets aufweisen kann (z. B. Ebenen in einer Fotoshop-Datei, Folien in einer PowerPoint-Datei, Seiten in einer PDF-Datei, Dateien in einer ZIP-Datei).

Bei einem Asset handelt es sich im Wesentlichen um eine binäre Datei mitsamt Metadaten, Wiedergabe und Unter-Assets. Ausführliche Informationen finden Sie im [DAM-Leistungshandbuch](/help/sites-deploying/assets-performance-sizing.md).

>[!CAUTION]
>
>Uploading and/or editing a large volume of assets (particularly images) can impact the performance of your [!DNL Experience Manager] instance.

### [!DNL Experience Manager Assets] Terminologie {#aem-assets-terminology}

When working with digital assets in [!DNL Experience Manager], you need to understand the following terminology:

* **Sammlung**: Eine Sammlung von Assets, entweder basierend auf dem physischen Speicherort (Ordner), allgemeinen Eigenschaften (gespeicherter Suchordner) oder der Benutzerauswahl (Leuchtkasten-Ordner).

* **Metadaten** enthalten Metadaten [!DNL Assets] ; zum Beispiel Autor, Ablaufdatum, DRM-Informationen (Digital Rights Management) usw. Metadaten sind unter der Zugangssteuerung zu finden. [!DNL Assets] unterstützt standardmäßig die folgenden allgemeinen Metadaten-Schemata:

   * Dublin Core: einschließlich Autor, Beschreibung, Datum, Thema usw.
   * IPTC: einschließlich Ereignis, Modell, Ort usw.
   * WCM: einschließlich Seiteneigenschaften, [!UICONTROL On Time] und [!UICONTROL Off Time]usw.

* **Tagging**: [!DNL Assets] können mit Tags versehen und klassifiziert werden. Siehe [Organisieren von Assets](/help/assets/organize-assets.md).

* **Darstellungen**: Eine Darstellung ist die binäre Darstellung eines Assets. [!DNL Assets] verfügen stets über eine primäre Darstellung, nämlich die der hochgeladenen Datei. Assets können über eine beliebige Anzahl an weiteren Darstellungen verfügen, die beispielsweise durch benutzerdefinierte Workflow-Schritte oder beim Hochladen eines Assets erstellt werden. Das Ausgabeformat kann verschieden sein, mit einer unterschiedlichen Auflösung, einem hinzugefügten Wasserzeichen oder anderen geänderten Merkmalen.

* **Versionen**: Bei der Versionierung wird ein Schnappschuss digitaler Assets zu einem bestimmten Zeitpunkt erstellt. Sie können frühere Versionen von Assets wiederherstellen. See [versioning in Assets](managing-assets-touch-ui.md#asset-versioning).

* **Teilassets**: Unter-Assets sind Assets, aus denen ein Asset besteht, z. B. Ebenen in einer [!DNL Adobe Photoshop] Datei oder Seiten in einer PDF-Datei. In [!DNL Assets], you can manage sub-assets as you would assets.

### How to work with assets {#how-to-work-with-assets}

Sie können für Assets oder Sammlungen Aktionen durchführen. Mit Aktionen können Assets, Sammlungen und Darstellungen erstellt oder geändert werden. Viele der grundlegenden Aktionen, die Sie für Assets durchführen - Hochladen, Löschen, Aktualisieren, Speichern von Teilassets - lösen vorkonfigurierte Workflows aus. These are automatically turned on in [!DNL Assets] and are described in detail in [!DNL Assets] media handlers.

Die Aufgaben, die mit den vorkonfigurierten Workflows ausgeführt werden können:

* Speichern Sie das Asset im Repository oder löschen Sie es aus dem Repository.
* Extrahieren und Speichern von Metadaten für das Asset; Die einzelnen Metadatenelemente werden als XMP gespeichert.
* Ausgabeformate und Miniaturansichten für das Asset erstellen; gegebenenfalls einschließlich automatischer Größenanpassung und Zuschneiden.
* Transkodieren Sie das Asset bei Bedarf. Beispielsweise werden Videos für Mobilgeräte und Verwendung im Netz mit 24 Bildern pro Sekunde transcodiert, für Downloads vorgesehene Videos hingegen mit 30 Bildern pro Sekunde. Audio für die mobile und die Web-Nutzung wird mit 128 Kbit/s transkodiert, Audio zum Download mit 192 Kbit/s.

Sie können Workflows natürlich auch manuell anwenden. Eine Liste der Standard-Workflows finden Sie unter [Medien-Handler in  Assets](/help/assets/media-handlers.md).

## [!DNL Experience Manager Assets] und [!DNL MediaLibrary] {#cq-dam-vs-cq-medialibrary}

Informationen zu den Unterschieden finden Sie unter [Assets und MediaLibrary](/help/assets/medialibrary.md) .
