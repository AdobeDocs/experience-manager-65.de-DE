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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
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

Angenommen, die Kopfzeile für die Kommentarkomponente muss auf einer Site der AEM-Instanz auf einer anderen Site angezeigt werden, während auf einer anderen Site die Standardanzeige erscheint. Anstatt den Standardkommentar zu überlagern, der die Kommentarkomponente für alle Instanzen ändert, ist eine bessere Lösung, sicherzustellen, dass mehrere Kommentarkomponenten für die Verwendung auf verschiedenen Sites verfügbar sind.

Um diese Lösung zu implementieren, erstellen Sie eine Komponente, die die vorhandene erweitert (überschreibt) und das Handlebars-Skript ändert. Der Bereich der Site, der die neuen Kommentare verwendet, kann den erweiterten verwenden, während die Sites, die das standardmäßige Erscheinungsbild verwenden, nicht betroffen sind.

Die Kommentarkomponente ist eigentlich eine von zwei Komponenten, die das Kommentarsystem bilden. Daher müssen zwei Komponenten erweitert werden: *Kommentare* und *Kommentar*. Das Skript, das bearbeitet werden soll, befindet sich in *`header.hbs` der*-Komponente, während die übergeordnete Komponente *Kommentare* (das Kommentarsystem) das ist, was ein Autor oder eine Autorin der Seite tatsächlich hinzufügt.

Um Kommentare zu erweitern, müssen Sie:

1. [Erstellen der Komponenten](extend-create-components.md)
1. [Kommentar zur Beispielseite hinzufügen](extend-sample-page.md)
1. [Erscheinungsbild ändern](extend-alter-appearance.md)
