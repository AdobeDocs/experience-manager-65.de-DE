---
title: Social-Diagramm verwenden
description: Erfahren Sie, wie Sie einer Seite eine Komponente vom Typ Folgende hinzufügen, mit der angemeldete Community-Mitglieder Aktivitäten folgen oder folgen können.
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

# Social-Diagramm verwenden {#using-social-graph}

## Einführung {#introduction}

Die Fähigkeit eines Community-Mitglieds, [Aktivitäten](activities.md) zu folgen und ihnen zu folgen, wird durch zwei Komponenten festgelegt: `Follow` und `Following`.

Die Komponente `Follow` muss mit einer anderen Ressource verknüpft sein, und diese Zuordnung ist bereits für Community-Mitglieder und -Funktionen eingerichtet.

Die Komponente `Following` listet einfach die Mitglieder auf, die dem aktuellen Mitglied folgen oder dem aktuellen Mitglied folgen. Dieses soziale Diagramm der Beziehungen zwischen Mitgliedern ist in dem Benutzerprofil enthalten, das für eine [Community-Site](overview.md#communitiessites) festgelegt wurde.

## Hinzufügen von Folgenden zu einer Seite {#adding-following-to-a-page}

Wenn Sie im Autorenmodus einer Seite die Komponente `Following` hinzufügen möchten, suchen Sie die Komponente `Communities / Following` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der das Social-Diagramm angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-socialgraph.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Following` wie folgt angezeigt:

![following](assets/following.png)

## Konfigurieren der folgenden {#configuring-following}

Derzeit ist es erforderlich, die -Eigenschaft festzulegen, um zu bestimmen, ob die Komponente die `follows`-Beziehung oder die `following`-Beziehung anzeigt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Social-Diagrammgrundlagen](essentials-socialgraph.md) .
