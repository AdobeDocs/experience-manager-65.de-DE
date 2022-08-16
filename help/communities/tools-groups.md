---
title: Gruppenvorlagen
seo-title: Group Templates
description: Zugriff auf die Konsole Gruppenvorlagen
seo-description: How to access the Group Templates console
uuid: 4cf20c91-32b0-4051-a98d-44e4eb50a231
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e9bfbbce-93fc-455c-a2f7-4ee44e63c03f
docset: aem65
role: Admin
exl-id: aed2c3f2-1b5e-4065-8cec-433abb738ef5
source-git-commit: ed11891c27910154df1bfec6225aecd8a9245bff
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---

# Gruppenvorlagen {#group-templates}

Die Gruppenvorlagen-Konsole ähnelt der [Site-Vorlagen](/help/communities/sites.md) Konsole. Beide sind Blueprints für eine Reihe vorab verkabelter Seiten und Funktionen, die eine Community-Site bilden. Der Unterschied besteht darin, dass eine Site-Vorlage für die Hauptgemeinde und eine Gruppenvorlage für eine Community-Gruppe, eine Unter-Community, die in der Hauptgemeinde verschachtelt ist, bestimmt wird.

Eine Community-Gruppe wird in eine Site-Vorlage integriert, indem die Variable [Gruppenfunktion](/help/communities/functions.md#groups-function) (die nicht die erste und auch nicht die einzige Funktion in der Vorlage sein darf).

Als Communitys [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack)können Gruppen verschachtelt werden, indem die Funktion Gruppen in eine Gruppenvorlage eingefügt wird.

Sobald eine Aktion zur Erstellung einer neuen Community-Gruppe durchgeführt wird, wird die Vorlage (Struktur) der Gruppe ausgewählt. Die Auswahl hängt davon ab, wie die Funktion Gruppen konfiguriert wurde, als sie der Site- oder Gruppenvorlage hinzugefügt wurde.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md) und [Community-Funktionen](/help/communities/functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Gruppenvorlagen-Konsole {#group-templates-console}

So greifen Sie auf die Gruppenvorlagen-Konsole in der AEM-Autorenumgebung zu:

* Auswählen **Instrumente | Communities | Gruppenvorlagen,** von der globalen Navigation aus.

Diese Konsole zeigt die Vorlagen an, aus denen ein [Community-Site](/help/communities/sites-console.md) kann erstellt werden und die Erstellung neuer Gruppenvorlagen ermöglicht.

![Vorlage für Community-Gruppen](assets/groups-template.png)

## Gruppenvorlage erstellen {#create-group-template}

Um mit der Erstellung einer neuen Gruppenvorlage zu beginnen, wählen Sie `Create`.

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

Wenn Sie beispielsweise ein Forum wünschen, ziehen Sie die Forumsfunktion aus der Bibliothek und legen Sie sie unter dem Vorlagen-Builder ab. Dadurch wird das Dialogfeld für die Forenkonfiguration geöffnet. Siehe [Funktionskonsole](/help/communities/functions.md) für Informationen zu den Konfigurationsdialogfeldern.

Setzen Sie die Drag &amp; Drop-Funktion anderer Community-Funktionen fort, die für eine auf dieser Vorlage basierende Unter-Community-Site (Gruppe) gewünscht werden.

![Drag-Funktionen](assets/dragfunctions.png)

Nachdem alle gewünschten Funktionen im Vorlagenerstellungsbereich abgelegt und konfiguriert wurden, wählen Sie **Speichern** in der oberen rechten Ecke.

## Gruppenvorlage bearbeiten {#edit-group-template}

Beim Anzeigen von Community-Gruppen in der Hauptseite [Gruppenvorlagen-Konsole](#group-templates-console)können Sie eine vorhandene Gruppenvorlage zur Bearbeitung auswählen.

Die Bearbeitung einer Gruppenvorlage hat keine Auswirkungen auf Community-Sites, die bereits aus der Vorlage erstellt wurden. Es ist möglich, [Bearbeiten einer Community-Site](/help/communities/sites-console.md#modify-structure)-Struktur.

Dieser Prozess stellt dieselben Bedienfelder wie [Erstellen einer Gruppenvorlage](#create-group-template).
