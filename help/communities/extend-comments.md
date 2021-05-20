---
title: Erweitern der Kommentarkomponente
seo-title: Erweitern der Kommentarkomponente
description: Erweitern Sie die Komponente Kommentare , um ihr Erscheinungsbild oder Verhalten für bestimmte Verwendungen zu ändern.
seo-description: Erweitern Sie die Komponente Kommentare , um ihr Erscheinungsbild oder Verhalten für bestimmte Verwendungen zu ändern.
uuid: 6f439097-b1d0-4e7d-afcf-01d8f43aa866
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a07a4690-0e47-4a76-84cb-96abdc70b835
exl-id: e57198cb-8fd9-43e2-b416-e40e462561c8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Kommentarkomponente erweitern {#extend-comments-component}

Die Absicht von [Erweiterung](client-customize.md#extensions) einer Standardkomponente besteht darin, das Erscheinungsbild oder Verhalten einer Komponente für bestimmte Verwendungen zu ändern.

Der Pfad zur Komponente ist eindeutig und verweist auf die Standardkomponente als Superressourcentyp. Das Risiko ist geringer, da der Umfang im Vergleich zum globalen Umfang einer Komponentenüberlagerung begrenzt ist.

>[!NOTE]
>
>Das Erweitern einer [überlagerten](client-customize.md#overlays)-Komponente wird nicht unterstützt.

## Beispiel {#example}

Angenommen, die Kopfzeile für die Kommentarkomponente muss auf einer Site der AEM-Instanz mit einem alternativen Erscheinungsbild angezeigt werden, während sie auf einer anderen Site mit der Standardanzeige angezeigt wird. Statt den Standardkommentar zu überlagern, wodurch die Kommentarkomponente für alle Instanzen geändert wird, ist eine bessere Lösung sicherzustellen, dass mehrere Kommentarkomponenten für die Verwendung auf verschiedenen Sites verfügbar sind.

Um diese Lösung zu implementieren, erstellen Sie eine neue Komponente, die die vorhandene Komponente erweitert (überschreibt) und das Handlebars-Skript ändert. Der Bereich der Site, der die neuen Kommentare verwendet, kann den erweiterten Bereich verwenden, während die Sites, die das standardmäßige Erscheinungsbild verwenden, davon nicht betroffen sind.

Die Kommentarkomponente ist tatsächlich eine von zwei Komponenten, die das Kommentarsystem enthalten. Daher müssen zwei Komponenten erweitert werden: *comments* und *comment*. Das zu bearbeitende Skript befindet sich in der Datei *comment* der Komponente `header.hbs`, während die übergeordnete Komponente *comments* (das Kommentarsystem) das ist, was ein Autor der Seite tatsächlich hinzufügt.

Um Kommentare zu erweitern, müssen Sie:

1. [Erstellen der Komponenten](extend-create-components.md)
1. [Hinzufügen von Kommentaren zur Beispielseite](extend-sample-page.md)
1. [Erscheinungsbild ändern](extend-alter-appearance.md)
