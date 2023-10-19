---
title: Social-Diagramm verwenden
description: Erfahren Sie, wie Sie einer Seite eine Komponente vom Typ Folgende hinzufügen, mit der angemeldete Community-Mitglieder Aktivitäten folgen oder folgen können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 2cd1436b-3727-4757-b28e-70756be78a4e
source-git-commit: 62d4a8b3af5031ccc539d78f7d06a8cd1fec7af1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# Social-Diagramm verwenden {#using-social-graph}

## Einführung {#introduction}

Die Fähigkeit eines Community-Mitglieds zu folgen [activities](activities.md) und zu befolgen ist durch zwei Komponenten festgelegt: `Follow` und `Following`.

Die `Follow` -Komponente muss mit einer anderen Ressource verknüpft sein, und diese Zuordnung ist bereits für Community-Mitglieder und -Funktionen eingerichtet.

Die `Following` -Komponente werden lediglich die Mitglieder aufgelistet, die dem aktuellen Mitglied folgen oder dem aktuellen Mitglied folgen. Dieses soziale Diagramm der Beziehungen zwischen Mitgliedern ist in dem Benutzerprofil enthalten, das für eine [Community-Site](overview.md#communitiessites).

## Hinzufügen von Folgenden zu einer Seite {#adding-following-to-a-page}

Wenn Sie eine `Following` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente `Communities / Following` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der das Social-Diagramm erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](essentials-socialgraph.md#essentials-for-client-side) eingeschlossen sind, wird die `Following` -Komponente angezeigt:

![following](assets/following.png)

## Konfigurieren der folgenden {#configuring-following}

Derzeit ist es erforderlich, die -Eigenschaft festzulegen, um zu bestimmen, ob die Komponente die `follows` Beziehung oder `following` Beziehung.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen zu Social-Diagrammen](essentials-socialgraph.md) -Seite für Entwickler.
