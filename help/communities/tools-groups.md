---
title: Gruppenvorlagen
description: Erfahren Sie, wie Sie auf die Konsole Gruppenvorlagen zugreifen können, um eine Reihe vorab verkabelter Seiten und Funktionen zu erhalten, die eine Community-Site bilden.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: aed2c3f2-1b5e-4065-8cec-433abb738ef5
source-git-commit: 00b6f2f03470aca7f87717818d0dfcd17ac16bed
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 3%

---

# Gruppenvorlagen {#group-templates}

Die Gruppenvorlagen-Konsole ähnelt der [Site-Vorlagen](/help/communities/sites.md) Konsole. Beide sind Blueprints für eine Reihe vorab verkabelter Seiten und Funktionen, die eine Community-Site bilden. Der Unterschied besteht darin, dass eine Site-Vorlage für die Hauptgemeinde und eine Gruppenvorlage für eine Community-Gruppe, eine Subgemeinschaft, die in der Hauptgemeinde verschachtelt ist, bestimmt ist.

Eine Community-Gruppe wird in eine Site-Vorlage integriert, indem die Variable [Gruppenfunktion](/help/communities/functions.md#groups-function) (die nicht die erste und auch nicht die einzige Funktion in der Vorlage sein darf).

Als Communitys [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack)können Gruppen verschachtelt werden, indem die Funktion Gruppen in eine Gruppenvorlage aufgenommen wird.

Sobald eine Aktion zum Erstellen einer Community-Gruppe durchgeführt wird, wird die Vorlage (Struktur) der Gruppe ausgewählt. Die Auswahl hängt davon ab, wie die Funktion Gruppen konfiguriert wurde, als sie der Site- oder Gruppenvorlage hinzugefügt wurde.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md), und [Community-Funktionen](/help/communities/functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Gruppenvorlagen-Konsole {#group-templates-console}

So greifen Sie auf die Gruppenvorlagen-Konsole in der AEM-Autorenumgebung zu:

* Auswählen **Instrumente | Communities | Gruppenvorlagen,** von der globalen Navigation aus.

Diese Konsole zeigt die Vorlagen an, aus denen ein [Community-Site](/help/communities/sites-console.md) kann erstellt werden und die Erstellung neuer Gruppenvorlagen ermöglicht.

![Vorlage für Community-Gruppen](assets/groups-template.png)

## Gruppenvorlage erstellen {#create-group-template}

Wählen Sie zunächst `Create`.

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
>Die Funktion für verschachtelte Gruppen ist ab Communities verfügbar [FP1](/help/communities/communities.md#latestfeaturepack).
>
>Es ist immer noch nicht zulässig, eine Gruppenfunktion als erste oder einzige Funktion in einer Vorlage hinzuzufügen.

![Gruppenvorlageneditor](assets/template-editor.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in die Reihenfolge, in der die Links zum Site-Menü angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise ein Forum wünschen, ziehen Sie die Forumsfunktion aus der Bibliothek und legen Sie sie unter dem Vorlagen-Builder ab. Dies führt zum Öffnen des Dialogfelds für die Forenkonfiguration. Siehe [Funktionenkonsole](/help/communities/functions.md) für Informationen zu den Konfigurationsdialogfeldern.

Setzen Sie die Drag-and-Drop-Funktion anderer Community-Funktionen fort, die basierend auf dieser Vorlage für eine Subcommunity-Site (Gruppe) gewünscht werden.

![Drag-Funktionen](assets/dragfunctions.png)

Nachdem alle gewünschten Funktionen im Vorlagenerstellungsbereich abgelegt und konfiguriert wurden, wählen Sie **Speichern** in der oberen rechten Ecke.

## Gruppenvorlage bearbeiten {#edit-group-template}

Beim Anzeigen von Community-Gruppen in der Hauptseite [Gruppenvorlagen-Konsole](#group-templates-console)können Sie eine vorhandene Gruppenvorlage zur Bearbeitung auswählen.

Die Bearbeitung einer Gruppenvorlage hat keine Auswirkungen auf Community-Sites, die bereits aus der Vorlage erstellt wurden. Es ist möglich [Bearbeiten einer Community-Site](/help/communities/sites-console.md#modify-structure)-Struktur.

Dieser Prozess stellt dieselben Bedienfelder wie [Erstellen einer Gruppenvorlage](#create-group-template).
