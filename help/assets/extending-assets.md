---
title: Adobe Experience Manager-Assets anpassen und erweitern
description: Informieren Sie sich, wie Sie die Asset-Freigabe und den Asset-Editor anpassen und erweitern können, um Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung zu stellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 55%

---


# Anpassen und Erweitern von Assets {#customizing-and-extending-assets}

Der Asset-Editor ist der Hauptzugriff, den Benutzer einer Adobe Enterprise Manager-Website verwenden, um die digitalen Assets in Ihrem Repository zu finden, zu Ansicht und zu manipulieren.

Als Experience Manager-Entwickler können Sie den Asset-Editor auf verschiedene Weise anpassen und erweitern und Benutzern eine speziell angepasste Oberfläche und eine Reihe von Funktionen bieten.

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

In der Experience Manager Assets-Terminologie ist eine Darstellung das Formular, in dem ein Asset angezeigt wird. Im Allgemeinen kann ein Asset mehrere Ausgabeformate haben. Z. B. kann ein Farbbild in seiner Originalgröße ausgegeben, verkleinert oder verkleinert und in Graustufen konvertiert sein.

Die Ausgabeformate, in denen ein bestimmtes Asset verfügbar ist, können angepasst werden und es können neue Ausgaben erstellt haben.
