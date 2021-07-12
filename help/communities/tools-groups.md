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
role: Admin
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 3%

---


# Gruppenvorlagen {#group-templates}

Die Konsole Gruppenvorlagen ähnelt der Konsole [Site-Vorlagen](/help/communities/sites.md) . Beide sind Blueprints für eine Reihe vorab verkabelter Seiten und Funktionen, die eine Community-Site bilden. Der Unterschied besteht darin, dass eine Site-Vorlage für die Hauptgemeinde und eine Gruppenvorlage für eine Community-Gruppe, eine Unter-Community, die in der Hauptgemeinde verschachtelt ist, bestimmt wird.

Eine Community-Gruppe wird in eine Site-Vorlage integriert, indem die [Gruppenfunktion](/help/communities/functions.md#groups-function) einbezogen wird (die nicht die erste und nicht nur die Funktion in der Vorlage ist).

Ab Communities [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack) können Gruppen verschachtelt werden, indem die Funktion Gruppen in eine Gruppenvorlage eingefügt wird.

Sobald eine Aktion zur Erstellung einer neuen Community-Gruppe durchgeführt wird, wird die Vorlage (Struktur) der Gruppe ausgewählt. Die Auswahl hängt davon ab, wie die Funktion Gruppen konfiguriert wurde, als sie der Site- oder Gruppenvorlage hinzugefügt wurde.

>[!NOTE]
>
>Die Konsolen zum Erstellen von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md) und [Community-Funktionen](/help/communities/functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Gruppenvorlagen-Konsole {#group-templates-console}

So greifen Sie auf die Gruppenvorlagen-Konsole in der AEM-Autorenumgebung zu:

* Wählen Sie **Tools | Communities | Gruppenvorlagen,** aus der globalen Navigation.

Diese Konsole zeigt die Vorlagen an, aus denen eine [Community-Site](/help/communities/sites-console.md) erstellt werden kann, und ermöglicht die Erstellung neuer Gruppenvorlagen.

![Vorlage für Community-Gruppen](assets/groups-template.png)

## Gruppenvorlage erstellen {#create-group-template}

Um mit der Erstellung einer neuen Gruppenvorlage zu beginnen, wählen Sie `Create` aus.

Dadurch wird der Site-Editor-Bereich angezeigt, der drei Unterbereiche enthält:

### Grundlegende Informationen {#basic-info}

![site-basic-info](assets/site-basic-info.png)

Im Bedienfeld &quot;Grundlegende Informationen&quot;werden ein Name, eine Beschreibung und die Frage, ob die Vorlage aktiviert oder deaktiviert ist, konfiguriert:

* **Neuer Name für Gruppenvorlage**

   Die Vorlagenname-ID.

* **Beschreibung**

   Die Vorlagenbeschreibung.

* **Deaktiviert/Aktiviert**

   Ein Umschalter steuert, ob die Vorlage referenzierbar ist.

#### Miniaturansicht {#thumbnail}

![site-thumbnail](assets/site-thumbnail.png)

(Optional) Wählen Sie das Symbol Bild hochladen aus, um eine Miniaturansicht zusammen mit dem Namen und der Beschreibung für Ersteller von Community-Sites anzuzeigen.

#### Struktur {#structure}

>[!CAUTION]
>
>Wenn Sie mit AEM 6.1 Communities FP4 oder früher arbeiten, fügen Sie einer Gruppenvorlage keine Gruppenfunktion hinzu.
>
>Die Funktion für verschachtelte Gruppen ist ab Communities [FP1](/help/communities/communities.md#latestfeaturepack) verfügbar.
>
>Es ist immer noch nicht zulässig, eine Gruppenfunktion als erste oder einzige Funktion in einer Vorlage hinzuzufügen.

![Gruppenvorlageneditor](assets/template-editor.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in die Reihenfolge, in der die Links zum Site-Menü angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise ein Forum wünschen, ziehen Sie die Forumsfunktion aus der Bibliothek und legen Sie sie unter dem Vorlagen-Builder ab. Dadurch wird das Dialogfeld für die Forenkonfiguration geöffnet. Informationen zu den Konfigurationsdialogen finden Sie in der [Funktionskonsole](/help/communities/functions.md) .

Setzen Sie die Drag &amp; Drop-Funktion anderer Community-Funktionen fort, die für eine auf dieser Vorlage basierende Unter-Community-Site (Gruppe) gewünscht werden.

![Drag-Funktionen](assets/dragfunctions.png)

Nachdem alle gewünschten Funktionen im Vorlagenerstellungsbereich abgelegt und konfiguriert wurden, wählen Sie **Speichern** in der oberen rechten Ecke aus.

## Gruppenvorlage bearbeiten {#edit-group-template}

Bei der Anzeige von Community-Gruppen in der Hauptkonsole [Gruppenvorlagen](#group-templates-console) ist es möglich, eine vorhandene Gruppenvorlage zur Bearbeitung auszuwählen.

Die Bearbeitung einer Gruppenvorlage hat keine Auswirkungen auf Community-Sites, die bereits aus der Vorlage erstellt wurden. Es ist möglich, stattdessen direkt die Struktur [einer Community-Site](/help/communities/sites-console.md#modify-structure) zu bearbeiten.

Dieser Prozess stellt dieselben Bedienfelder bereit wie [Erstellen einer Gruppenvorlage](#create-group-template).
