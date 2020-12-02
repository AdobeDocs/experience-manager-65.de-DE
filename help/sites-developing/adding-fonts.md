---
title: Hinzufügen von Schriftarten für das Grafik-Rendering
seo-title: Hinzufügen von Schriftarten für das Grafik-Rendering
description: In AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch Ihren Inhalten entnommen wird.
seo-description: In AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch Ihren Inhalten entnommen wird.
uuid: 67d9b10f-e986-4d29-bde2-10e08075fe17
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6af48ef5-75e6-4b66-bc0d-ecf254b1c4ef
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 63%

---


# Hinzufügen von Schriftarten für das Grafik-Rendering{#adding-fonts-for-graphic-rendering}

AEM ermöglicht Ihnen die Erstellung von Grafiken mit dynamisch aus Ihren Inhalten stammendem Text.

Hierfür können Sie auch Ihre eigenen Schriftarten hochladen und verwenden.

Derzeit unterstützen alle Implementierungen der Java-Plattform [TrueType](https://en.wikipedia.org/wiki/Truetype)-Schriftarten.

1. Öffnen Sie die CRXDE Lite und navigieren Sie zum Projektanwendungsordner:

   `/apps/<your-project>/`

1. Erstellen Sie unter `/apps/<your-project>/` einen neuen Knoten:

   * **Name**: `fonts`
   * **Typ**: `sling:Folder`

   Speichern Sie alle Änderungen.

1. Kopieren Sie die Schriftarten-Dateien in diesen Ordner, z. B. mit WebDAV.

   >[!NOTE]
   >
   >Schriftartdateien im Repository müssen das Suffix `*.ttf` oder `*.TTF` haben.

1. Aktualisieren Sie die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). hinzufügen Sie den Pfad zum Schriftartenordner an. d.h. `/apps/<your-project>/fonts`.

1. Kehren Sie zu CRXDE Lite zurück. Es sollte nun ein `.fontlist`-Knoten in Ihrem Ordner angezeigt werden, der den Namen der importierten Schriftarten enthält.

   Diese Schriftarten stehen jetzt für die Verwendung in der Java-API zur Verfügung.

Ausführliche Informationen zur Verwendung der Schriftarten in der Java-API finden Sie in der [Dokumentation zur Font-Klasse der Java-API](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).

