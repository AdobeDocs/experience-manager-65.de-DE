---
title: Verwenden von Sozialdiagrammen
seo-title: Verwenden von Sozialdiagrammen
description: Hinzufügen einer folgenden Komponente zu einer Seite
seo-description: Hinzufügen einer folgenden Komponente zu einer Seite
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
translation-type: tm+mt
source-git-commit: 1429a099288f038510cb0a194fb55632297ef371
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 26%

---


# Verwenden von Sozialdiagrammen {#using-social-graph}

## Einführung {#introduction}

Die Fähigkeit eines Community-Mitglieds, [Aktivitäten](activities.md) zu befolgen, wird durch zwei Komponenten festgelegt: `Follow` und `Following`.

Die `Follow`-Komponente muss mit einer anderen Ressource verknüpft sein, und diese Zuordnung ist bereits für Community-Mitglieder und -Funktionen eingerichtet.

Die `Following`-Komponente Liste lediglich die Mitglieder, die dem aktuellen Member folgen oder denen das aktuelle Member folgt. Dieses Sozialdiagramm der Mitgliederbeziehungen untereinander ist Teil des Benutzerprofils, das für eine [Community-Site](overview.md#communitiessites) bereitgestellt wird.

## Hinzufügen von Folgenden zu einer Seite {#adding-following-to-a-page}

Wenn Sie eine `Following`-Komponente zu einer Seite im Autorenmodus hinzufügen möchten, suchen Sie die Komponente `Communities / Following` und ziehen Sie sie auf eine Seite, auf der das Social-Diagramm angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-socialgraph.md#essentials-for-client-side) einbezogen werden, wird die `Following`-Komponente wie folgt angezeigt:

![folgende](assets/following.png)

## Konfigurieren von Folgenden {#configuring-following}

Derzeit muss die Eigenschaft festgelegt werden, um zu bestimmen, ob die Komponente die `follows`-Beziehung oder die `following`-Beziehung anzeigt.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Sozialdiagrammgrundlagen](essentials-socialgraph.md).
