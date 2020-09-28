---
title: Anpassen und Erweitern [!DNL Assets]
description: Informieren Sie sich, wie Sie die Asset-Freigabe und den Asset-Editor anpassen und erweitern können, um Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung zu stellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5069c2cd26e84866d72a61d36de085dadd556cdd
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 57%

---


# Anpassen und Erweitern [!DNL Assets] {#customizing-and-extending-assets}

Der Asset-Editor ist der Hauptzugriff, den Benutzer einer Adobe Enterprise Manager-Website zum Suchen, Ansichten und Manipulieren der digitalen Assets in Ihrem Repository verwenden.

As an [!DNL Experience Manager] developer, you can customize and extend the Asset Editor in a number of ways, presenting users with a specifically tailored interface and set of functionality.

Die folgenden Funktionen können angepasst bzw. verbessert werden:

* [Asset-Editor erweitern](asseteditorx.md)
* [Suche nach Assets erweitern](searchx.md)
* [Verarbeiten von Assets mithilfe von Media Handlers und Workflows](media-handlers.md)
* [Assets mit Aktivitäten-Stream integrieren](extending-activity-stream.md)
* [Asset Proxy-Entwicklung](proxy.md)
* [Empfohlene Vorgehensweisen zum Konfigurieren von ImageMagick](best-practices-for-imagemagick.md)

## Erscheinungsbild anpassen {#customizing-the-look-and-feel}

Die folgenden Aspekte des Erscheinungsbilds des Asset-Editors sind anpassbar:

* Logo: Sie können das Logo Ihrer Organisation zur Benutzeroberfläche hinzufügen.
* Farben und Schriftarten: Sie können die Farben und Schriftarten ändern, die in der Benutzeroberfläche verwendet werden.
* HTML-Code: Zur besseren Anpassung können Sie den zugrunde liegenden HTML-Code ändern, der die Benutzeroberflächen definiert.

## Darstellungen anpassen {#customizing-renditions}

In [!DNL Experience Manager Assets] terminology a rendition is the form in which an asset is presented. Im Allgemeinen kann ein Asset mehrere Ausgabeformate haben. Z. B. kann ein Farbbild in seiner Originalgröße ausgegeben, verkleinert oder verkleinert und in Graustufen konvertiert sein.

Die Ausgabeformate, in denen ein bestimmtes Asset verfügbar ist, können angepasst werden und es können neue Ausgaben erstellt haben.
