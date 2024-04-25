---
title: Erweitern der Kommentarkomponente
description: Erweitern Sie die Komponente Kommentare , um ihr Erscheinungsbild oder Verhalten für bestimmte Verwendungen zu ändern.
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

# Erweitern der Kommentarkomponente  {#extend-comments-component}

Die Absicht von [Erweiterung](client-customize.md#extensions) Eine Standardkomponente besteht darin, das Erscheinungsbild oder Verhalten einer Komponente für bestimmte Verwendungen zu ändern.

Der Pfad zur Komponente ist eindeutig und verweist auf die Standardkomponente als Superressourcentyp. Das Risiko ist geringer, da der Umfang im Vergleich zum globalen Umfang einer Komponentenüberlagerung begrenzt ist.

>[!NOTE]
>
>Erweitern einer [überlagert](client-customize.md#overlays) -Komponente wird nicht unterstützt.

## Beispiel {#example}

Angenommen, die Kopfzeile für die Kommentarkomponente muss auf einer Site der AEM-Instanz mit einem alternativen Erscheinungsbild angezeigt werden, während sie auf einer anderen Site mit der Standardanzeige angezeigt wird. Statt den Standardkommentar zu überlagern, wodurch die Kommentarkomponente für alle Instanzen geändert wird, ist eine bessere Lösung sicherzustellen, dass mehrere Kommentarkomponenten für die Verwendung auf verschiedenen Sites verfügbar sind.

Um diese Lösung zu implementieren, erstellen Sie eine Komponente, die die vorhandene Komponente erweitert (überschreibt) und ändern Sie das Handlebars-Skript. Der Bereich der Site, der die neuen Kommentare verwendet, kann den erweiterten Bereich verwenden, während die Sites, die das standardmäßige Erscheinungsbild verwenden, davon nicht betroffen sind.

Die Kommentarkomponente ist tatsächlich eine von zwei Komponenten, die das Kommentarsystem enthalten. Daher müssen zwei Komponenten erweitert werden: *Kommentare* und *comment*. Das zu bearbeitende Skript befindet sich im *comment* Komponenten `header.hbs` -Datei, während die übergeordnete *Kommentare* -Komponente (das Kommentarsystem) ist, was ein Autor der Seite tatsächlich hinzufügt.

Um Kommentare zu erweitern, müssen Sie:

1. [Erstellen der Komponenten](extend-create-components.md)
1. [Hinzufügen von Kommentaren zur Beispielseite](extend-sample-page.md)
1. [Erscheinungsbild ändern](extend-alter-appearance.md)
