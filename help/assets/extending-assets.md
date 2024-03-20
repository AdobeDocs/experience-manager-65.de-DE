---
title: Anpassen und Erweitern von  [!DNL Assets]
description: Informieren Sie sich, wie Sie die Asset-Freigabe und den Asset-Editor anpassen und erweitern können, um Benutzern eine maßgeschneiderte Oberfläche und passende Funktionen zur Verfügung zu stellen.
contentOwner: AG
role: Developer
feature: Developer Tools
exl-id: 0271c528-23b0-4a3a-b5e8-5baf6cdeecc7
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 40%

---

# Anpassen und Erweitern von [!DNL Assets] {#customizing-and-extending-assets}

Der Asset-Editor ist der primäre Zugriffspunkt, den Benutzer einer Adobe Enterprise Manager-Website verwenden, um die digitalen Assets in Ihrem Repository zu finden, anzuzeigen und zu bearbeiten.

Als [!DNL Experience Manager] Entwickler können Sie den Asset-Editor auf verschiedene Arten anpassen und erweitern, indem Sie Benutzern eine speziell auf sie zugeschnittene Benutzeroberfläche und eine Reihe von Funktionen präsentieren.

Die folgenden Funktionen können angepasst bzw. verbessert werden:

* [Erweitern des Asset-Editors](asseteditorx.md)
* [Erweitern der Asset-Suche](searchx.md)
* [Verarbeiten von Assets mithilfe von Medien-Handlern und Workflows](media-handlers.md)
* [Integrieren von Assets in den Aktivitäts-Stream](extending-activity-stream.md)
* [Entwicklung von Asset-Proxys](proxy.md)
* [Best Practices zum Konfigurieren von ImageMagick](best-practices-for-imagemagick.md)

## Anpassen des Erscheinungsbilds {#customizing-the-look-and-feel}

Die folgenden Aspekte des Erscheinungsbilds des Asset-Editors sind anpassbar:

* Logo: Sie können das Logo Ihrer eigenen Organisation zur Benutzeroberfläche hinzufügen.
* Farben und Schriftarten: Sie können die in der Benutzeroberfläche verwendeten Farben und Schriftarten ändern.
* HTML-Code: Für eine genauere Anpassung können Sie den zugrunde liegenden HTML-Code ändern, der die Schnittstellen definiert.

## Anpassen von Ausgabedarstellungen {#customizing-renditions}

In der [!DNL Experience Manager Assets]-Terminologie ist ein Ausgabeformat die Form, in der ein Asset dargestellt wird. Im Allgemeinen kann ein bestimmtes Asset mehrere Ausgabedarstellungen aufweisen. Beispielsweise kann ein Vollfarbbild eine Darstellung in der Originalgröße aufweisen, eine andere in einer herunterskalierten Größe und eine andere, die sowohl herunterskaliert als auch in Graustufen konvertiert wird.

Die Ausgabedarstellungen, in denen ein bestimmtes Asset verfügbar ist, können angepasst und neue Ausgabedarstellungen erstellt werden.
