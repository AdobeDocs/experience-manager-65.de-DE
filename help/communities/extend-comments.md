---
title: Komponente „Kommentare erweitern“
description: Erweitern der Komponente Kommentare , um ihr Aussehen oder Verhalten für bestimmte Verwendungszwecke zu ändern
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: e57198cb-8fd9-43e2-b416-e40e462561c8
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Komponente „Kommentare erweitern“  {#extend-comments-component}

Die Absicht [Erweiterung](client-customize.md#extensions) einer Standardkomponente besteht darin, das Aussehen oder Verhalten einer Komponente für bestimmte Verwendungszwecke zu ändern.

Der Pfad zur Komponente ist eindeutig und verweist auf die Standardkomponente als Superressourcentyp. Das Risiko ist geringer, da der Umfang im Vergleich zum globalen Umfang einer Komponentenüberlagerung begrenzt ist.

>[!NOTE]
>
>Das Erweitern einer [überlagerten](client-customize.md#overlays) Komponente wird nicht unterstützt.

## Beispiel {#example}

Angenommen, die Kopfzeile für die Kommentarkomponente muss auf einer Site der AEM-Instanz mit einer anderen Darstellung angezeigt werden, während sie auf einer anderen Site mit der Standardanzeige erscheint. Anstatt den Standardkommentar zu überlagern, der die Kommentarkomponente für alle Instanzen ändert, ist eine bessere Lösung, sicherzustellen, dass mehrere Kommentarkomponenten für die Verwendung auf verschiedenen Sites verfügbar sind.

Um diese Lösung zu implementieren, erstellen Sie eine Komponente, die die vorhandene erweitert (überschreibt) und das Handlebars-Skript ändert. Der Bereich der Site, der die neuen Kommentare verwendet, kann den erweiterten verwenden, während die Sites, die das standardmäßige Erscheinungsbild verwenden, nicht betroffen sind.

Die Kommentarkomponente ist eigentlich eine von zwei Komponenten, die das Kommentarsystem bilden. Daher müssen zwei Komponenten erweitert werden: *Kommentare* und *Kommentar*. Das Skript, das bearbeitet werden soll, befindet sich in *`header.hbs` der*-Komponente, während die übergeordnete Komponente *Kommentare* (das Kommentarsystem) das ist, was ein Autor oder eine Autorin der Seite tatsächlich hinzufügt.

Um Kommentare zu erweitern, müssen Sie:

1. [Erstellen der Komponenten](extend-create-components.md)
1. [Kommentar zur Beispielseite hinzufügen](extend-sample-page.md)
1. [Erscheinungsbild ändern](extend-alter-appearance.md)
