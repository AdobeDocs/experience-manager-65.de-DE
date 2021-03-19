---
title: ' [!DNL Assets] anpassen und erweitern'
description: Informieren Sie sich, wie Sie die Asset-Freigabe und den Asset-Editor anpassen und erweitern können, um Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung zu stellen.
contentOwner: AG
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 57%

---


# [!DNL Assets] {#customizing-and-extending-assets} anpassen und erweitern

Der Asset-Editor ist der Hauptzugriff, den Benutzer einer Adobe Enterprise Manager-Website zum Suchen, Ansichten und Manipulieren der digitalen Assets in Ihrem Repository verwenden.

Als [!DNL Experience Manager]-Entwickler können Sie den Asset-Editor auf verschiedene Weise anpassen und erweitern, indem Sie den Benutzern eine speziell angepasste Oberfläche und eine Reihe von Funktionen präsentieren.

Die folgenden Funktionen können angepasst bzw. verbessert werden:

* [Asset-Editor erweitern](asseteditorx.md)
* [Suche nach Assets erweitern](searchx.md)
* [Verarbeiten von Assets mithilfe von Media Handlers und Workflows](media-handlers.md)
* [Assets mit Aktivitäten-Stream integrieren](extending-activity-stream.md)
* [Asset Proxy-Entwicklung](proxy.md)
* [Empfohlene Vorgehensweisen zum Konfigurieren von ImageMagick](best-practices-for-imagemagick.md)

## Erscheinungsbild {#customizing-the-look-and-feel} anpassen

Die folgenden Aspekte des Erscheinungsbilds des Asset-Editors sind anpassbar:

* Logo: Sie können das Logo Ihrer Organisation zur Benutzeroberfläche hinzufügen.
* Farben und Schriftarten: Sie können die Farben und Schriftarten ändern, die in der Benutzeroberfläche verwendet werden.
* HTML-Code: Zur besseren Anpassung können Sie den zugrunde liegenden HTML-Code ändern, der die Benutzeroberflächen definiert.

## Darstellungen {#customizing-renditions} anpassen

In der [!DNL Experience Manager Assets]-Terminologie ist eine Darstellung das Formular, in dem ein Asset angezeigt wird. Im Allgemeinen kann ein Asset mehrere Ausgabeformate haben. Z. B. kann ein Farbbild in seiner Originalgröße ausgegeben, verkleinert oder verkleinert und in Graustufen konvertiert sein.

Die Ausgabeformate, in denen ein bestimmtes Asset verfügbar ist, können angepasst werden und es können neue Ausgaben erstellt haben.
