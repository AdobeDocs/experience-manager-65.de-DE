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
source-git-commit: 3296db289b2e2f4ca0d1981597ada6ca1310bd46

---


# Verwenden von Sozialdiagrammen {#using-social-graph}

## Einführung {#introduction}

The ability for a community member to follow [activities](activities.md) as well as be followed is established through two components: `Follow` and `Following`.

The `Follow` component must be associated with another resource, and this association is already established for community members and features.

The `Following` component simply lists the members that are either following the current member or are being followed by the current member. Dieses Sozialdiagramm der Mitgliederbeziehungen untereinander ist Teil des Benutzerprofils, das für eine [Community-Site](overview.md#communitiessites) bereitgestellt wird.

## Hinzufügen von Folgenden zu einer Seite {#adding-following-to-a-page}

Wenn Sie eine `Following` Komponente im Autorenmodus zu einer Seite hinzufügen möchten, suchen Sie die Komponente `Communities / Following` und ziehen Sie sie auf eine Seite, auf der das Social-Diagramm angezeigt werden soll.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](essentials-socialgraph.md#essentials-for-client-side) are included, this is how the `Following` component will appear:

![chlimage_1-447](assets/chlimage_1-447.png)

## Konfigurieren von Folgenden {#configuring-following}

Currently, it is necessary to set the property to determine whether the component displays the `follows` relationship, or the `following` relationship.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Sozialdiagrammgrundlagen](essentials-socialgraph.md).
