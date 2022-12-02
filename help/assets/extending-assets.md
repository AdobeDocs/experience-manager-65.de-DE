---
title: Anpassen und Erweitern von  [!DNL Assets]
description: Informieren Sie sich, wie Sie die Asset-Freigabe und den Asset-Editor anpassen und erweitern können, um Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung zu stellen.
contentOwner: AG
role: Developer
feature: Developer Tools
exl-id: 0271c528-23b0-4a3a-b5e8-5baf6cdeecc7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 100%

---

# Anpassen und Erweitern von [!DNL Assets] {#customizing-and-extending-assets}

Der Asset-Editor ist der primäre Zugangspunkt, den Benutzer einer Adobe Enterprise Manager-Website verwenden, um die digitalen Assets in Ihrem Repository zu suchen, anzuzeigen und zu bearbeiten.

Als [!DNL Experience Manager]-Entwickler können Sie den Asset-Editor auf mehrere Arten anpassen und erweitern und Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung stellen.

Die folgenden Funktionen können angepasst bzw. verbessert werden:

* [Erweitern des Asset-Editors](asseteditorx.md)
* [Erweitern der Asset-Suche](searchx.md)
* [Verarbeiten von Assets mithilfe von Medien-Handlern und Workflows](media-handlers.md)
* [Integrieren von Assets in den Aktivitäts-Stream](extending-activity-stream.md)
* [Entwicklung von Asset-Proxys](proxy.md)
* [Best Practices zum Konfigurieren von ImageMagick](best-practices-for-imagemagick.md)

## Anpassen des Erscheinungsbilds {#customizing-the-look-and-feel}

Die folgenden Aspekte des Erscheinungsbilds des Asset-Editors sind anpassbar:

* Logo: Sie können das Logo Ihrer Organisation zur Benutzeroberfläche hinzufügen.
* Farben und Schriftarten: Sie können die Farben und Schriftarten ändern, die in der Benutzeroberfläche verwendet werden.
* HTML-Code: Zur besseren Anpassung können Sie den zugrunde liegenden HTML-Code ändern, der die Benutzeroberflächen definiert.

## Anpassen von Ausgabedarstellungen {#customizing-renditions}

In der [!DNL Experience Manager Assets]-Terminologie ist ein Ausgabeformat die Form, in der ein Asset dargestellt wird. Im Allgemeinen kann ein Asset mehrere Ausgabeformate haben. Z. B. kann ein Farbbild in seiner Originalgröße ausgegeben, verkleinert oder verkleinert und in Graustufen konvertiert sein.

Die Ausgabeformate, in denen ein bestimmtes Asset verfügbar ist, können angepasst werden und es können neue Ausgaben erstellt haben.
