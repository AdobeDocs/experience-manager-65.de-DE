---
title: Gruppenvorlagen
seo-title: Gruppenvorlagen
description: Zugriff auf die Konsole Gruppenvorlagen
seo-description: Zugriff auf die Konsole Gruppenvorlagen
uuid: 4cf20c91-32b0-4051-a98d-44e4eb50a231
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e9bfbbce-93fc-455c-a2f7-4ee44e63c03f
docset: aem65
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 4%

---


# Gruppenvorlagen {#group-templates}

Die Konsole &quot;Gruppenvorlagen&quot;ähnelt der Konsole [Site-Vorlagen](/help/communities/sites.md). Beide sind Entwürfe für eine Reihe vorab verkabelter Seiten und Funktionen, die eine Community-Site bilden. Der Unterschied besteht darin, dass eine Site-Vorlage für die Haupt-Community und eine Gruppenvorlage für eine Community-Gruppe, eine Unter-Community, die innerhalb der Haupt-Community verschachtelt ist, bestimmt ist.

Eine Community-Gruppe wird in eine Site-Vorlage integriert, indem die Funktion [Gruppen](/help/communities/functions.md#groups-function) einbezogen wird (die nicht die erste oder einzige Funktion in der Vorlage ist).

Ab Communities [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack) ist es möglich Gruppen zu verschachteln, indem die Funktion Gruppen in eine Gruppenvorlage aufgenommen wird.

Sobald eine Aktion durchgeführt wird, um eine neue Community-Gruppe zu erstellen, wird die Vorlage (Struktur) der Gruppe ausgewählt. Die Auswahl hängt davon ab, wie die Funktion Gruppen konfiguriert wurde, wenn sie der Site- oder Gruppenvorlage hinzugefügt wurde.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](/help/communities/sites-console.md), [Community-Sitevorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md) und [Community-Funktionen](/help/communities/functions.md) sind nur für die Verwendung in der Autor-Umgebung vorgesehen.

## Gruppenvorlagen-Konsole {#group-templates-console}

So erreichen Sie die Gruppenvorlagen-Konsole in der AEM Author-Umgebung:

* Wählen Sie **Tools | Communities | Gruppenvorlagen,** aus der globalen Navigation.

Diese Konsole zeigt die Vorlagen an, aus denen eine [Community-Site](/help/communities/sites-console.md) erstellt werden kann, und ermöglicht die Erstellung neuer Gruppenvorlagen.

![Community-Gruppen-Vorlage](assets/groups-template.png)

## Gruppenvorlage erstellen {#create-group-template}

Um eine neue Gruppenvorlage zu erstellen, wählen Sie `Create`.

Dadurch wird der Site-Editor-Bereich angezeigt, der drei Unterbereiche enthält:

### Grundlegende Informationen {#basic-info}

![site-basic-info](assets/site-basic-info.png)

Im Bedienfeld &quot;Grundlegende Informationen&quot;werden ein Name, eine Beschreibung und die Konfiguration der Vorlage, ob sie aktiviert oder deaktiviert ist, wie folgt konfiguriert:

* **Neuer Name für Gruppenvorlage**

   Die Vorlagenname-ID.

* **Beschreibung**

   Die Vorlagenbeschreibung.

* **Deaktiviert/aktiviert**

   Ein Umschalter steuert, ob die Vorlage referenzierbar ist.

#### Miniaturansicht  {#thumbnail}

![site-thumbnail](assets/site-thumbnail.png)

(Optional) Wählen Sie das Symbol Bild hochladen, um eine Miniaturansicht mit dem Namen und der Beschreibung für die Ersteller von Community-Sites anzuzeigen.

#### Struktur {#structure}

>[!CAUTION]
>
>Wenn Sie mit AEM 6.1 Communities FP4 oder früher arbeiten, sollten Sie einer Gruppenvorlage keine Gruppenfunktion hinzufügen.
>
>Die Funktion für verschachtelte Gruppen ist ab Communities [FP1](/help/communities/communities.md#latestfeaturepack) verfügbar.
>
>Es ist immer noch nicht zulässig, eine Funktion &quot;Gruppen&quot;als erste oder einzige Funktion in einer Vorlage hinzuzufügen.

![Gruppenvorlageneditor](assets/template-editor.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in der Reihenfolge, in der die Sitemenü-Links angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise ein Forum wünschen, ziehen Sie die Forumsfunktion aus der Bibliothek und legen Sie sie unter dem Vorlagenaufbau ab. Dadurch wird der Dialog zur Forumkonfiguration geöffnet. Informationen zu den Konfigurationsdialogen finden Sie in der Konsole [Funktionen](/help/communities/functions.md).

Ziehen Sie weitere Community-Funktionen per Drag &amp; Drop, die basierend auf dieser Vorlage für eine Subcommunity-Site (Gruppe) gewünscht werden.

![Drag-Funktionen](assets/dragfunctions.png)

Nachdem alle gewünschten Funktionen in den Bereich &quot;Vorlagenaufbau&quot;abgelegt und konfiguriert wurden, wählen Sie **Speichern** in der oberen rechten Ecke aus.

## Gruppenvorlage bearbeiten {#edit-group-template}

Bei der Anzeige von Community-Gruppen in der Haupt-Konsole [Gruppenvorlagen](#group-templates-console) ist es möglich, eine vorhandene Gruppenvorlage zur Bearbeitung auszuwählen.

Das Bearbeiten einer Gruppenvorlage hat keine Auswirkungen auf Community-Sites, die bereits aus der Vorlage erstellt wurden. Es ist möglich, stattdessen die Struktur einer Community-Site](/help/communities/sites-console.md#modify-structure) direkt zu bearbeiten.[

Dieser Prozess stellt dieselben Bereiche bereit wie [Erstellen einer Gruppenvorlage](#create-group-template).
