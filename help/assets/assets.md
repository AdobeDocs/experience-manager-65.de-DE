---
title: Einführung in [!DNL Adobe Experience Manager Assets]
description: Erfahren Sie, was Digital Asset Management, seine Anwendungsfälle und [!DNL Adobe Experience Manager Asset] Angebot sind.
contentOwner: AG
feature: Asset-Management
role: Leader, Architect, User
exl-id: 68239634-a2e8-414e-a866-cd8082641ee8
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 36%

---

# Über [!DNL Adobe Experience Manager Assets] als DAM-Lösung {#administering-assets}

[!DNL Assets] ist ein DAM-Tool (Digital Asset Management), das integraler Bestandteil der  [!DNL Experience Manager] Plattform ist und es Ihrem Unternehmen ermöglicht, digitale Assets zu verwalten und zu verteilen. Benutzer in einem Unternehmen können viele Arten digitaler Assets verwalten, speichern und darauf zugreifen, z. B. Bilder, Videos, Dokumente, Audioclips, 3D-Dateien und Rich-Media-Dateien, die im Web, in gedruckten Dokumenten und für die digitale Verteilung verwendet werden können.

## Was ist Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] ermöglicht die unternehmensweite Frei- und Weitergabe der wichtigsten digitalen Assets einer Organisation. Benutzer in einem Unternehmen können digitale Assets wie Bilder, Grafiken, Audio, Video und Dokumente über eine Web-Oberfläche (oder einen CIFS- oder WebDAV-Ordner) speichern, verwalten und aufrufen.

[!DNL Assets] -Funktion  [!DNL Experience Manager] ermöglicht Ihnen Folgendes:

* Hinzufügen und Freigeben von Bildern, Dokumenten, Audiodateien und Videodateien in einer Vielzahl von Dateiformaten.
* Verwalten Sie Assets, indem Sie sie nach Tags, Lightbox oder Sternen (Ihren Favoriten) gruppieren. Hinzufügen von Anmerkungen zu Assets.
* Auffinden von Assets durch Durchsuchen von Dateinamen, des Volltextes von Dokumenten und durch Suchvorgänge nach Datum, Dokumenttyp und Tags.
* Hinzufügen oder Bearbeiten von Metadateninformationen für Assets. Metadaten werden automatisch mit dem entsprechenden Asset in einer Version zusammengefasst. Sie können Asset-Metadaten importieren und exportieren.
* Ausführen von Bildbearbeitungsvorgängen, beispielsweise Skalierung und Hinzufügen von Bildfiltern. Importieren und Exportieren mehrerer digitaler Assets gleichzeitig mithilfe eines WebDAV- oder CIFS-Ordners.
* Verwenden von Workflows und Benachrichtigungen, um die gemeinsame Verarbeitung und den gemeinsamen Download mehrerer Assets zu ermöglichen und Zugriffsrechte auf Assets zu verwalten.

### [!DNL Experience Manager Assets] ist integriert in  [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] vollständig in integriert  [!DNL Sites] und funktioniert nahtlos für alle Anwendungsfälle. Wenn Sie beispielsweise Web-Seiten erstellen, können die [!DNL Sites]-Autoren die digitalen Assets über den Content Finder finden und verwenden. Die Benutzeroberfläche von [!DNL Assets] ist identisch mit der von [!DNL Sites]. Ausführliche Informationen finden Sie unter [Übersicht über Sites](/help/sites-authoring/page-authoring.md) .

Die grundlegende Benutzeroberfläche entspricht der von [!DNL Sites]. Ausführliche Informationen finden Sie unter [Übersicht der Sites](/help/sites-authoring/page-authoring.md) .

### Digital Asset Management im Vergleich zur Bildkomponente {#digital-asset-management-versus-image-component}

Berücksichtigen Sie bei der Entscheidung, ob ein Bild in das DAM-Repository eingefügt oder eine Bildkomponente verwendet werden soll, den Bildlebenszyklus:

* Wenn das Bild denselben Lebenszyklus wie die Seite hat, verwenden Sie die Bildkomponente .
* Wenn das Bild einen eigenen Lebenszyklus hat – beispielsweise, wenn Sie das Bild zweimal oder außerhalb von WCM verwenden –, verwenden Sie [!DNL Assets].

## Was sind digitale Assets? {#what-are-digital-assets}

Ein Asset ist ein digitales Dokument, Bild, Video oder eine digitale Audiodatei (oder ein Teil davon), das bzw. die mehrere Ausgabedarstellungen aufweisen und über Unter-Assets verfügen kann (z. B. Ebenen in einer Fotoshop-Datei, Folien in einer PowerPoint-Datei, Seiten in einem PDF-Dokument, Dateien in einer ZIP-Datei).

Bei einem Asset handelt es sich im Wesentlichen um eine binäre Datei mitsamt Metadaten, Wiedergabe und Unter-Assets. Ausführliche Informationen finden Sie im [DAM-Leistungshandbuch](/help/sites-deploying/assets-performance-sizing.md).

>[!CAUTION]
>
>Das Hochladen und/oder Bearbeiten einer großen Menge von Assets (insbesondere von Bildern) kann sich auf die Leistung Ihrer [!DNL Experience Manager]-Implementierung auswirken.

### [!DNL Experience Manager Assets] Terminologie {#aem-assets-terminology}

Beim Arbeiten mit digitalen Assets in [!DNL Experience Manager] müssen Sie die folgende Terminologie verstehen:

* **Sammlung**: Eine Sammlung von Assets, entweder basierend auf dem physischen Speicherort (Ordner), allgemeinen Eigenschaften (gespeicherter Suchordner) oder der Benutzerauswahl (Lightbox-Ordner).

* **** [!DNL Assets] Metadaten; z. B. Autor, Ablaufdatum, DRM-Informationen (Digital Rights Management) usw. Metadaten sind unter der Zugangssteuerung zu finden. [!DNL Assets] unterstützt standardmäßig die folgenden allgemeinen Metadaten-Schemata:

   * Dublin Core: einschließlich Autor, Beschreibung, Datum, Thema usw.
   * IPTC: einschließlich Ereignis, Modell, Ort usw.
   * WCM: einschließlich Seiteneigenschaften, [!UICONTROL Einschaltzeit] und [!UICONTROL Ausschaltzeit] usw.

* **Tagging**:  [!DNL Assets] kann mit Tags versehen und klassifiziert werden. Siehe [Organisieren von Assets](/help/assets/organize-assets.md).

* **Ausgabeformate**: Eine Ausgabedarstellung ist die binäre Darstellung eines Assets. [!DNL Assets] verfügen stets über eine primäre Darstellung, nämlich die der hochgeladenen Datei. Assets können über eine beliebige Anzahl an weiteren Darstellungen verfügen, die beispielsweise durch benutzerdefinierte Workflow-Schritte oder beim Hochladen eines Assets erstellt werden. Das Ausgabeformat kann verschieden sein, mit einer unterschiedlichen Auflösung, einem hinzugefügten Wasserzeichen oder anderen geänderten Merkmalen.

* **Versionen**: Durch die Versionierung wird ein Schnappschuss digitaler Assets zu einem bestimmten Zeitpunkt erstellt. Sie können frühere Versionen von Assets wiederherstellen. Siehe [Versionierung in [!DNL Assets]](manage-assets.md#asset-versioning).

* **Unter-Assets**: Unter-Assets sind Assets, aus denen ein Asset besteht, z. B. Ebenen in einer  [!DNL Adobe Photoshop] Datei oder Seiten in einer PDF-Datei. In [!DNL Assets] können Sie Unter-Assets genauso wie Assets verwalten.

### Arbeiten mit digitalen Assets {#how-to-work-with-assets}

Sie können für Assets oder Sammlungen Aktionen durchführen. Mit Aktionen können Assets, Sammlungen und Darstellungen erstellt oder geändert werden. Viele der grundlegenden Aktionen, die Sie für Assets ausführen - Hochladen, Löschen, Aktualisieren, Speichern von Unter-Assets - vorkonfigurierte Workflows für Trigger. Diese werden automatisch in [!DNL Assets] aktiviert und detailliert unter [!DNL Assets] Medien-Handler beschrieben.

Die Aufgaben, die Sie mit diesen vorkonfigurierten Workflows ausführen können:

* Speichern Sie das Asset im Repository oder löschen Sie es aus dem Repository.
* Extrahieren und Speichern von Metadaten für das Asset; werden die einzelnen Metadatenelemente als XMP gespeichert.
* Generieren von Ausgabeformaten und Miniaturansichten für das Asset; gegebenenfalls einschließlich automatischer Größenanpassung und Zuschneiden.
* Transkodieren Sie das Asset bei Bedarf. Beispielsweise werden Videos für Mobilgeräte und Verwendung im Netz mit 24 Bildern pro Sekunde transcodiert, für Downloads vorgesehene Videos hingegen mit 30 Bildern pro Sekunde. Audio für mobile und Web-Nutzung wird mit 128 kBit/s transkodiert, Audio für den Download mit 192 kBit/s.

Sie können Workflows natürlich auch manuell anwenden. Eine Liste der Standard-Workflows finden Sie unter [Medien-Handler in  Assets](media-handlers.md).

## [!DNL Experience Manager Assets] und [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Informationen zu den Unterschieden finden Sie unter [Assets und Media Library](medialibrary.md) .

>[!MORELIKETHIS]
>
>* [Videoeinführung - Experience Manager Assets as a modern DAM](https://www.youtube.com/watch?v=PBwQqZgC-yo)
>* [Grundlagen zu Metadatenkonzepten](/help/assets/metadata-concepts.md)

