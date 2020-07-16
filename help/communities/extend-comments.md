---
title: Komponente "Kommentare erweitern"
seo-title: Komponente "Kommentare erweitern"
description: Erweitern Sie die Komponente "Kommentare", um ihr Aussehen oder Verhalten für bestimmte Zwecke zu ändern
seo-description: Erweitern Sie die Komponente "Kommentare", um ihr Aussehen oder Verhalten für bestimmte Zwecke zu ändern
uuid: 6f439097-b1d0-4e7d-afcf-01d8f43aa866
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a07a4690-0e47-4a76-84cb-96abdc70b835
translation-type: tm+mt
source-git-commit: 230c700d87d82d248b7d0bbc45c69c5c2b0e3ff8
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Komponente &quot;Kommentare erweitern&quot;  {#extend-comments-component}

Die Absicht, eine Standardkomponente zu [erweitern](client-customize.md#extensions) , besteht darin, das Aussehen oder Verhalten einer Komponente für bestimmte Zwecke zu ändern.

Der Pfad zur Komponente ist eindeutig und verweist auf die Standardkomponente als Superressourcentyp. Das Risiko ist geringer, da der Umfang im Vergleich zum globalen Umfang einer Komponentenüberlagerung begrenzt ist.

>[!NOTE]
>
>Das Erweitern einer [überlagerten](client-customize.md#overlays) Komponente wird nicht unterstützt.


## Beispiel {#example}

Angenommen, die Kopfzeile für die Kommentarkomponente muss auf einer Seite der AEM-Instanz mit einem alternativen Erscheinungsbild angezeigt werden, während sie auf einer anderen Site mit der Standardanzeige angezeigt wird. Statt den Standardkommentar zu überlagern, wodurch die Kommentarkomponente für alle Instanzen geändert wird, ist eine bessere Lösung sicherzustellen, dass auf verschiedenen Sites mehrere Kommentarkomponenten verfügbar sind.

Um diese Lösung zu implementieren, erstellen Sie eine neue Komponente, die die vorhandene Komponente erweitert (überschreibt) und das Handlebars-Skript ändert. Der Bereich der Site, der die neuen Kommentare verwendet, kann den erweiterten verwenden, während die Sites, die das Standardbild verwenden, unverändert bleiben.

Die Kommentarkomponente ist eigentlich eine von zwei Komponenten, die das Kommentarsystem umfassen. Es gibt also zwei Komponenten, die erweitert werden müssen: *Kommentare* und *Kommentare*. Das zu bearbeitende Skript befindet sich in der *-Datei der* Kommentarkomponente `header.hbs` , während die übergeordnete Komponente für *Kommentare* (das Kommentarsystem) dem entspricht, was ein Autor der Seite tatsächlich hinzufügt.

Um Kommentare zu erweitern, müssen Sie:

1. [Komponenten erstellen](extend-create-components.md)
1. [Hinzufügen auf Beispielseite](extend-sample-page.md)
1. [Erscheinungsbild ändern](extend-alter-appearance.md)

