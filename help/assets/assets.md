---
title: Einführung in  [!DNL Adobe Experience Manager Assets]
description: Erfahren Sie mehr über Digital Asset Management, die Nutzungsszenarios und das  [!DNL Adobe Experience Manager Asset] -Angebot.
contentOwner: AG
feature: Asset Management
role: Leader, Architect, User
exl-id: 68239634-a2e8-414e-a866-cd8082641ee8
source-git-commit: b00ed4ed146b89aece9af1d267c890a360a236e9
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 65%

---

# Über [!DNL Adobe Experience Manager Assets] als DAM-Lösung {#administering-assets}

AEM [!DNL Assets] ist ein DAM-Tool (Digital Asset Management), das Teil der [!DNL Experience Manager] und ermöglicht Ihrem Unternehmen die Verwaltung und Verteilung digitaler Assets. Benutzende im Unternehmen können viele Arten von digitalen Assets verwalten, speichern und darauf zugreifen, z. B. Bilder, Videos, Dokumente, Audio-Clips, 3D-Dateien und Rich-Media-Dateien, die im Web, in gedruckten Dokumenten und für die digitale Verteilung verwendet werden können.

## Was ist Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] bietet unternehmensweite Freigabe und Verteilung der wichtigsten digitalen Assets eines Unternehmens. Benutzende in einer Organisation können digitale Assets wie Bilder, Grafiken, Audio- und Videodateien sowie Dokumente über eine Webschnittstelle (oder einen CIFS- oder WebDAV-Ordner) speichern, verwalten und aufrufen.

Die [!DNL Assets]-Funktionen von [!DNL Experience Manager] bieten Ihnen folgende Möglichkeiten:

* Fügen Sie Bilder, Dokumente, Audiodateien und Videodateien in verschiedenen Dateiformaten hinzu und geben Sie sie frei.
* Verwalten von Assets durch Gruppierung nach Tags, Lightbox oder Bewertung (Favoriten). Hinzufügen von Anmerkungen zu Assets.
* Suchen Sie nach Assets, indem Sie nach Dateinamen, dem Volltext von Dokumenten und nach Daten, Dokumenttyp und Tags suchen.
* Hinzufügen oder Bearbeiten von Metadateninformationen für Assets. Metadaten werden automatisch mit dem entsprechenden Asset in einer Version zusammengefasst. Sie können Asset-Metadaten importieren und exportieren.
* Führen Sie Bildbearbeitungsfunktionen wie Skalierung und Hinzufügen von Bildfiltern durch. Importieren und exportieren Sie mehrere digitale Assets gleichzeitig mit einem WebDAV- oder CIFS-Ordner.
* Verwenden von Workflows und Benachrichtigungen, um die gemeinsame Verarbeitung und den gemeinsamen Download mehrerer Assets zu ermöglichen und Zugriffsrechte auf Assets zu verwalten.

### [!DNL Experience Manager Assets] ist mit [!DNL Experience Manager Sites] integriert {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] ist vollständig mit [!DNL Sites] integriert und funktioniert nahtlos für alle Anwendungsfälle. Wenn Sie z. B. Web-Seiten erstellen, können [!DNL Sites]-Autoren können die digitalen Assets über den Content Finder suchen und verwenden. Die Benutzeroberfläche von [!DNL Assets] entspricht der von [!DNL Sites]. Anzeigen einer [Übersicht über Sites](/help/sites-authoring/page-authoring.md) für ausführliche Informationen.

Die grundlegende Benutzeroberfläche entspricht der von [!DNL Sites]. Ausführliche Informationen finden Sie unter [Überblick über Sites](/help/sites-authoring/page-authoring.md).

### Digital Asset Management und Bildkomponente {#digital-asset-management-versus-image-component}

Berücksichtigen Sie bei der Entscheidung, ob ein Bild in das DAM-Repository eingefügt oder eine Bildkomponente verwendet werden soll, den Bildlebenszyklus:

* Wenn das Bild denselben Lebenszyklus hat wie die Seite, verwenden Sie die Bildkomponente.
* Wenn das Bild einen eigenen Lebenszyklus hat – beispielsweise, wenn Sie das Bild zweimal oder außerhalb von WCM verwenden –, verwenden Sie [!DNL Assets].

## Was sind digitale Assets? {#what-are-digital-assets}

Ein Asset ist ein digitales Dokument, Bild, Video oder eine digitale Audiodatei (oder ein Teil davon), das bzw. die mehrere Ausgabeformate aufweisen kann. Es kann auch Teil-Assets enthalten, z. B. Ebenen in einer Photoshop-Datei, Folien in einer PowerPoint-Datei, Seiten in einem PDF-Dokument, Dateien in einer ZIP-Datei.

Ein Asset ist im Wesentlichen eine Binärdatei sowie Metadaten, Ausgabeformate und Teil-Assets. Siehe [DAM-Leistungsleitfaden](/help/sites-deploying/assets-performance-sizing.md) für detaillierte Informationen.

>[!CAUTION]
>
>Das Hochladen bzw. Bearbeiten von sehr vielen Assets (insbesondere von Bildern) kann die Leistung Ihrer [!DNL Experience Manager]-Bereitstellung beeinträchtigen.

### [!DNL Experience Manager Assets] – Terminologie {#aem-assets-terminology}

Beim Arbeiten mit digitalen Assets in [!DNL Experience Manager]ist es hilfreich, wenn Sie die folgende Terminologie verstehen:

* **Sammlung**: Eine Sammlung von Assets, entweder auf Grundlage ihres physischen Speicherorts (Ordner), allgemeinen Eigenschaften (gespeicherter Suchordner) oder Benutzerauswahl (Lightbox-Ordner).

* **Metadaten** [!DNL Assets] Metadaten haben, z. B. Autor, Ablaufdatum und DRM-Informationen (Digital Rights Management). Metadaten sind unter der Zugangssteuerung zu finden. [!DNL Assets] unterstützt standardmäßig die folgenden allgemeinen Metadaten-Schemata:

   * Dublin Core: einschließlich Autor, Beschreibung, Datum, Thema usw.
   * IPTC: einschließlich Ereignis, Modell, Standort usw.
   * WCM: einschließlich Seiteneigenschaften, [!UICONTROL Einschaltzeit] und [!UICONTROL Ausschaltzeit] usw.

* **Tagging**: [!DNL Assets] können mit Tags versehen und klassifiziert werden. Siehe [Organisieren von Assets](/help/assets/organize-assets.md).

* **Ausgabedarstellungen**: Eine Ausgabedarstellung ist die binäre Darstellung eines Assets. [!DNL Assets] verfügen stets über eine primäre Darstellung, nämlich die der hochgeladenen Datei. Sie können über eine beliebige Anzahl zusätzlicher Darstellungen verfügen, die erstellt werden, beispielsweise durch benutzerdefinierte Workflow-Schritte oder beim Hochladen eines Assets. Ausgabedarstellungen können eine andere Größe aufweisen, mit einer anderen Auflösung, mit einem hinzugefügten Wasserzeichen oder einem anderen geänderten Merkmal.

* **Versionen**: Bei der Versionierung wird eine Momentaufnahme von digitalen Assets zu einem bestimmten Zeitpunkt aufgezeichnet. Sie können frühere Versionen von Assets wiederherstellen. Siehe [Versionierung in  [!DNL Assets]](manage-assets.md#asset-versioning).

* **Unter-Assets**: Bei Unter-Assets handelt es sich um Assets, die zusammen ein Asset bilden, z. B. Ebenen in einer [!DNL Adobe Photoshop]-Datei oder Seiten in einer PDF-Datei. In [!DNL Assets] lassen sich Unter-Assets genau so wie normale Assets verwalten.

### Arbeiten mit digitalen Assets {#how-to-work-with-assets}

Sie führen eine Aktion für ein Asset oder eine Sammlung durch. Mit Aktionen können Assets, Sammlungen und Ausgabedarstellungen erstellt oder geändert werden. Viele der grundlegenden Aktionen, die Sie für Assets durchführen können – Hochladen, Löschen, Aktualisieren, Speichern von Unter-Assets –, lösen vorkonfigurierte Workflows aus. Diese sind in [!DNL Assets] automatisch aktiviert und werden in den Medien-Handlern für [!DNL Assets] detailliert beschrieben.

Folgende Aufgaben können Sie mit diesen vorkonfigurierten Workflows durchführen:

* Speichern von Assets in oder Löschen aus dem Repository.
* Extrahieren und Speichern von Metadaten der Assets. Die einzelnen Metadatenelemente werden als XMP gespeichert.
* Generieren von Ausgabedarstellungen und Miniaturansichten der Assets, einschließlich automatischer Skalierung und Zuschnitt, wo erforderlich.
* Transkodieren der Assets, sofern erforderlich. Beispielsweise werden Videos für Mobilgeräte und Verwendung im Netz mit 24 Bildern pro Sekunde transkodiert, für Downloads vorgesehene Videos hingegen mit 30 Bildern pro Sekunde. Audio für Mobilgeräte und Verwendung im Netz wird mit 128 Kbit/s transcodiert, Audio für den Download mit 192 Kbit/s.

Sie können Workflows auch manuell anwenden. Eine Liste der Standard-Workflows finden Sie unter [Medien-Handler in Assets](media-handlers.md).

## [!DNL Experience Manager Assets] und [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Informationen zu den Unterschieden finden Sie unter [Assets und Media Library](medialibrary.md).

>[!MORELIKETHIS]
>
>* [Videoeinführung: Experience Manager Assets als modernes DAM-System](https://www.youtube.com/watch?v=PBwQqZgC-yo)
>* [Grundlagen von Metadatenkonzepten](/help/assets/metadata-concepts.md)
