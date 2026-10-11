---
title: Hinzufügen von Schriftarten für das Grafik-Rendering
description: Mit AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch aus Ihrem Inhalt übernommen wird.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 725c81d0-0258-4118-8b01-29fd7bcaf9b3
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 100%
---
# Hinzufügen von Schriftarten für das Grafik-Rendering{#adding-fonts-for-graphic-rendering}

Mit AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch aus Ihrem Inhalt übernommen wird.

Hierfür können Sie auch Ihre eigenen Schriftarten hochladen und verwenden.

Derzeit unterstützen alle Implementierungen der Java-Plattform [TrueType](https://de.wikipedia.org/wiki/TrueType)-Schriftarten.

1. Öffnen Sie CRXDE Lite und navigieren Sie zu Ihrem Projekt-Programmordner:

   `/apps/<your-project>/`

1. Erstellen Sie einen Knoten unter `/apps/<your-project>/`:

   * **Name**: `fonts`
   * **Typ**: `sling:Folder`

   Speichern Sie alle Änderungen.

1. Kopieren Sie die Schriftarten-Dateien in diesen Ordner, z. B. mit WebDAV.

   >[!NOTE]
   >
   >Die Schriftarten-Dateien im Repository müssen die Dateiendung `*.ttf` oder `*.TTF` aufweisen.

1. Aktualisieren Sie die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). Fügen Sie den Pfad zum Schriftarten-Ordner hinzu, d. h. `/apps/<your-project>/fonts`.

1. Kehren Sie zu CRXDE Lite zurück. Sie sollten jetzt in Ihrem Ordner einen Knoten namens `.fontlist` sehen, der den Namen der importierten Schriftarten enthält.

   Diese Schriftarten stehen jetzt für die Verwendung in der Java-API zur Verfügung.

Ausführliche Informationen zur Verwendung der Schriftarten in der Java-API finden Sie in der [Dokumentation zur Font-Klasse der Java-API](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
