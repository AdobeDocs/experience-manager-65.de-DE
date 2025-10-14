---
title: Verwenden eines Social Media-Diagramms
description: Erfahren Sie, wie Sie einer Seite eine folgende Komponente hinzufügen, mit der angemeldete Community-Mitglieder Aktivitäten verfolgen oder befolgt werden können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 2cd1436b-3727-4757-b28e-70756be78a4e
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# Verwenden eines Social Media-Diagramms {#using-social-graph}

## Einführung {#introduction}

Die Möglichkeit für ein Community-Mitglied, [Aktivitäten](activities.md) zu verfolgen, wird durch zwei Komponenten eingerichtet: `Follow` und `Following`.

Die `Follow`-Komponente muss einer anderen Ressource zugeordnet sein, und diese Zuordnung wurde bereits für Community-Mitglieder und -Funktionen eingerichtet.

Die `Following`-Komponente listet einfach die Elemente auf, die entweder auf das aktuelle Element folgen oder auf die das aktuelle Element folgt. Dieses soziale Diagramm der Beziehungen zwischen Mitgliedern ist im Benutzerprofil enthalten, das für eine [Community-Site](overview.md#communitiessites) eingerichtet wurde.

## Hinzufügen von Folgendem zu einer Seite {#adding-following-to-a-page}

Wenn Sie einer Seite im Autorenmodus eine `Following` Komponente hinzufügen möchten, suchen Sie die Komponente `Communities / Following` und ziehen Sie sie an die Position auf einer Seite, auf der das soziale Diagramm angezeigt werden soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](essentials-socialgraph.md#essentials-for-client-side) enthalten sind, wird die `Following` Komponente wie folgt angezeigt:

![folgende](assets/following.png)

## Konfigurieren von Folgendem {#configuring-following}

Derzeit muss die Eigenschaft festgelegt werden, um zu bestimmen, ob die Komponente die `follows` Beziehung oder die `following` Beziehung anzeigt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Social Graph Essentials](essentials-socialgraph.md) für Entwickler.
