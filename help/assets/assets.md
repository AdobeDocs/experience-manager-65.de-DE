---
title: Info zu AEM Assets
description: Erfahren Sie mehr über das digitale Asset-Management, seine Anwendungsfälle und das AEM Asset-Angebot von Adobe
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Verwalten von Assets {#administering-assets}

Assets ist ein DAM-Tool (Digital Asset Management), das vollständig in die AEM-Plattform integriert ist und Ihrem Unternehmen die Freigabe und Verteilung digitaler Assets ermöglicht. Benutzer im gesamten Unternehmen können Bilder, Videos, Dokumente, Audioclips und Rich-Media wie Flash-Dateien für die Verwendung im Internet, zum Drucken und für die digitale Verteilung verwalten, speichern und darauf zugreifen.

## Was ist Digital Asset Management? {#what-is-digital-asset-management}

Assets ermöglicht die unternehmensweite Frei- und Weitergabe der wichtigsten digitalen Assets einer Organisation. Benutzer in einem Unternehmen können digitale Assets wie Bilder, Grafiken, Audio, Video und Dokumente über eine Webschnittstelle (oder einen CIFS- oder WebDAV-Ordner) speichern, verwalten und darauf zugreifen.

Mit AEM Assets, die gut in AEM integriert sind, haben Sie folgende Möglichkeiten:

* Hinzufügen und Freigeben von Bildern, Dokumenten, Audiodateien und Videodateien in einer Vielzahl von Dateiformaten.
* Verwalten Sie Assets, indem Sie sie nach Tags, Leuchtkästen oder Sternen (Ihren Favoriten) gruppieren. Hinzufügen von Anmerkungen zu Assets.
* Auffinden von Assets durch Durchsuchen von Dateinamen, des Volltextes von Dokumenten und durch Suchvorgänge nach Datum, Dokumenttyp und Tags.
* Hinzufügen oder Bearbeiten von Metadateninformationen für Assets. Metadaten werden automatisch mit dem entsprechenden Asset in einer Version zusammengefasst. Sie können Asset-Metadaten importieren und exportieren.
* Ausführen von Bildbearbeitungsvorgängen, beispielsweise Skalierung und Hinzufügen von Bildfiltern. Importieren und Exportieren mehrerer digitaler Assets gleichzeitig mithilfe eines WebDAV- oder CIFS-Ordners.
* Verwenden von Workflows und Benachrichtigungen, um die gemeinsame Verarbeitung und den gemeinsamen Download mehrerer Assets zu ermöglichen und Zugriffsrechte auf Assets zu verwalten.

### AEM Assets ist vollständig in CQ WCM integriert {#aem-assets-fully-integrated-in-cq-wcm}

AEM Assets ist vollständig in CQ WCM integriert und die Funktionen sind über das DAM-Symbol verfügbar:

![screen_shot_2012-04-17at15946pm](assets/screen_shot_2012-04-17at15946pm.png) ![screen_shot_2012-04-17at20100pm](assets/screen_shot_2012-04-17at20100pm.png)

In CQ DAM verwaltete Assets sind dann über die Inhaltssuche von WCM zugänglich:

![screen_shot_2012-04-17at20214pm](assets/screen_shot_2012-04-17at20214pm.png)

>[!NOTE]
>
>Die grundlegende GUI-Handhabung entspricht jener im Rest von WCM – umfassende Details finden Sie unter [Überblick über die GUI-Konsole](/help/sites-authoring/page-authoring.md).

### Digital Asset Management versus image component {#digital-asset-management-versus-image-component}

Berücksichtigen Sie bei der Entscheidung, ob Sie ein Bild in AEM Assets einfügen oder die AEM Image-Komponente verwenden, den Lebenszyklus des Bildes:

* Wenn das Bild denselben Lebenszyklus wie die Seite hat, verwenden Sie die Bildkomponente.
* Wenn das Bild einen eigenen Lebenszyklus hat – beispielsweise, wenn Sie das Bild zweimal oder außerhalb von WCM verwenden –, verwenden Sie AEM Assets.

## Was sind digitale Assets? {#what-are-digital-assets}

Ein Asset ist ein digitales Dokument, Bild, Video oder Audio (oder ein Teil davon), das mehrere Darstellungen aufweisen kann und Teilassets aufweisen kann (z. B. Ebenen in einer Fotoshop-Datei, Folien in einer PowerPoint-Datei, Seiten in einer PDF-Datei, Dateien in einer ZIP-Datei).

Bei einem Asset handelt es sich im Wesentlichen um eine binäre Datei mitsamt Metadaten, Wiedergabe und Unter-Assets. Ausführliche Informationen finden Sie im [DAM-Leistungshandbuch](/help/sites-deploying/assets-performance-sizing.md).

>[!CAUTION]
>
>Das Hochladen bzw. Bearbeiten von sehr vielen Assets (insbesondere von Bildern) kann sich auf die Leistung Ihrer CQ-Instanz auswirken.

### AEM Assets terminology {#aem-assets-terminology}

Bei der Arbeit mit digitalen Assets in AEM müssen Sie mit der folgenden Terminologie vertraut sein:

* **Sammlung** Eine Sammlung von Assets, entweder basierend auf dem physischen Speicherort (Ordner), allgemeinen Eigenschaften (gespeicherter Suchordner) oder der Benutzerauswahl (Leuchtkasten-Ordner).

* **Metadaten** -Assets enthalten Metadaten; zum Beispiel Autor, Ablaufdatum, DRM-Informationen (Digital Rights Management) usw. Metadaten sind unter der Zugangssteuerung zu finden. AEM Assets unterstützt standardmäßig die folgenden allgemeinen Metadaten-Schemata:

   * Dublin Core: einschließlich Autor, Beschreibung, Datum, Thema usw.
   * IPTC: einschließlich Ereignis, Modell, Ort usw.
   * WCM: einschließlich Seiteneigenschaften, [!UICONTROL On Time] und [!UICONTROL Off Time]usw.

* **Tagging** von Assets kann mit Tags versehen und klassifiziert werden. Weitere Informationen finden Sie in den Abschnitten über das Verwenden von Tags und das Bereitstellen von Tags.

* **Darstellungen** Eine Darstellung ist die binäre Darstellung eines Assets. Assets verfügen stets über eine primäre Darstellung, nämlich die der hochgeladenen Datei. Assets können über eine beliebige Anzahl an weiteren Darstellungen verfügen, die beispielsweise durch benutzerdefinierte Workflow-Schritte oder beim Hochladen eines Assets erstellt werden. Das Ausgabeformat kann verschieden sein, mit einer unterschiedlichen Auflösung, einem hinzugefügten Wasserzeichen oder anderen geänderten Merkmalen.

* **Versionen** -Versionierung erstellt einen Schnappschuss digitaler Assets zu einem bestimmten Zeitpunkt. Sie können frühere Versionen von Assets wiederherstellen. Siehe Versionierung in AEM Assets.

* **Unter-Assets** sind Teilassets, aus denen ein Asset besteht, z. B. Ebenen in einer Adobe Fotoshop-Datei oder Seiten in einer PDF-Datei. In AEM Assets lassen sich Unter-Assets genau so wie normale Assets verwalten.

### How to work with assets {#how-to-work-with-assets}

Sie können für Assets oder Sammlungen Aktionen durchführen. Mit Aktionen können Assets, Sammlungen und Darstellungen erstellt oder geändert werden. Viele der grundlegenden Aktionen, die Sie für Assets durchführen - Hochladen, Löschen, Aktualisieren, Speichern von Teilassets - lösen vorkonfigurierte Workflows aus. Diese werden automatisch in AEM Assets aktiviert und detailliert in den Medien-Handlern für AEM Assets beschrieben.

Die Aufgaben, die Sie mit diesen vorkonfigurierten Workflows ausführen können:

* Speichern von Assets in oder Löschen aus dem Repository.
* Extrahieren und Speichern von Metadaten der Assets. Die einzelnen Metadatenelemente werden als XMP gespeichert.
* Generieren von Darstellungen und Miniaturansichten der Assets, einschließlich automatischer Skalierung und Zuschnitt, wo erforderlich.
* Transcodieren der Assets, sofern erforderlich. Beispielsweise werden Videos für Mobilgeräte und Verwendung im Netz mit 24 Bildern pro Sekunde transcodiert, für Downloads vorgesehene Videos hingegen mit 30 Bildern pro Sekunde. Audio für Mobilgeräte und Verwendung im Netz wird mit 128 Kbit/s transcodiert, Audio für den Download mit 192 Kbit/s.

Sie können Workflows natürlich auch manuell anwenden. Eine Liste der Standard-Workflows finden Sie unter [Medien-Handler in AEM Assets](/help/assets/media-handlers.md).

## AEM Assets and AEM MediaLibrary {#cq-dam-vs-cq-medialibrary}

Informationen zu den Unterschieden finden Sie unter [AEM Assets und AEM MediaLibrary](/help/assets/medialibrary.md) .
