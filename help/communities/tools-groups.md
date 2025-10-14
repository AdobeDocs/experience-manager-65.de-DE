---
title: Gruppenvorlagen
description: Erfahren Sie, wie Sie auf die Konsole „Gruppenvorlagen“ für eine Reihe vorab verkabelter Seiten und Funktionen zugreifen können, die eine Community-Site bilden.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: aed2c3f2-1b5e-4065-8cec-433abb738ef5
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 2%

---

# Gruppenvorlagen {#group-templates}

Die Konsole „Gruppenvorlagen“ ähnelt der Konsole [Site-](/help/communities/sites.md)&quot;. Bei beiden handelt es sich um Blueprints für eine Reihe vorkonfigurierter Seiten und Funktionen, die eine Community-Site bilden. Der Unterschied besteht darin, dass eine Site-Vorlage für die Haupt-Community und eine Gruppenvorlage für eine Community-Gruppe ist, eine Untergemeinschaft, die innerhalb der Haupt-Community verschachtelt ist.

Eine Community-Gruppe wird in eine Site-Vorlage integriert, indem die Funktion [Gruppen](/help/communities/functions.md#groups-function) einbezogen wird (dies kann nicht die erste oder einzige Funktion in der Vorlage sein).

Ab Communities [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack) ist es möglich, Gruppen zu verschachteln, indem die Funktion „Gruppen“ in eine Gruppenvorlage aufgenommen wird.

In dem Moment, in dem eine Aktion zum Erstellen einer Community-Gruppe ausgeführt wird, wird die Vorlage (Struktur) der Gruppe ausgewählt. Die Auswahl hängt davon ab, wie die Gruppenfunktion konfiguriert wurde, als sie der Site- oder Gruppenvorlage hinzugefügt wurde.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md) und [Community-Funktionen](/help/communities/functions.md) sind nur für die Autorenumgebung vorgesehen.

## Konsole „Gruppenvorlagen“ {#group-templates-console}

So gelangen Sie in der AEM-Autorenumgebung zur Vorlagenkonsole für Gruppen:

* Wählen Sie **Tools | Communities | Gruppenvorlagen,** aus der globalen Navigation.

Diese Konsole zeigt die Vorlagen an, aus denen eine [Community-Site](/help/communities/sites-console.md) erstellt werden kann, und ermöglicht die Erstellung neuer Gruppenvorlagen.

![Vorlage für Community-Gruppen](assets/groups-template.png)

## Gruppenvorlage erstellen {#create-group-template}

Wählen Sie `Create` aus, um mit der Erstellung einer Gruppenvorlage zu beginnen.

Dadurch wird das Site-Editor-Bedienfeld angezeigt, das drei Unterbedienfelder enthält:

### Grundlegende Informationen {#basic-info}

![site-basic-info](assets/site-basic-info.png)

Im Bereich Basic Info werden ein Name, eine Beschreibung und Angaben dazu konfiguriert, ob die Vorlage aktiviert oder deaktiviert ist:

* **Name der neuen Gruppenvorlage**

  Die Vorlagenname-ID.

* **Beschreibung**

  Die Vorlagenbeschreibung.

* **Deaktiviert/Aktiviert**

  Ein Umschalter, der steuert, ob auf die Vorlage verwiesen werden kann.

#### Miniaturansicht {#thumbnail}

![site-thumbnail](assets/site-thumbnail.png)

(Optional) Klicken Sie auf das Symbol Bild hochladen , um eine Miniaturansicht zusammen mit dem Namen und der Beschreibung für die Ersteller von Community-Sites anzuzeigen.

#### Struktur {#structure}

>[!CAUTION]
>
>Wenn Sie mit AEM 6.1 Communities FP4 oder früher arbeiten, fügen Sie keiner Gruppenvorlage eine Gruppenfunktion hinzu.
>
>Die Funktion für verschachtelte Gruppen ist ab Communities (FP1[&#x200B; verfügbar](/help/communities/communities.md#latestfeaturepack).
>
>Es ist weiterhin nicht zulässig, eine Gruppenfunktion als erste oder einzige Funktion in einer Vorlage hinzuzufügen.

![Gruppenvorlagen-Editor](assets/template-editor.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in der Reihenfolge, in der die Links im Site-Menü angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie z. B. ein Forum möchten, ziehen Sie die Forenfunktion aus der Bibliothek und legen Sie sie unter dem Vorlagen-Builder ab. Daraufhin wird das Dialogfeld für die Forenkonfiguration geöffnet. Siehe die [Funktionskonsole](/help/communities/functions.md) für Informationen zu den Konfigurationsdialogen.

Ziehen Sie weiterhin alle anderen Community-Funktionen per Drag-and-Drop, die für eine Subcommunity-Site (Gruppe) basierend auf dieser Vorlage gewünscht sind.

![Funktionen ziehen](assets/dragfunctions.png)

Nachdem alle gewünschten Funktionen im Bereich des Vorlagen-Builders abgelegt und konfiguriert wurden, wählen Sie **Speichern** in der oberen rechten Ecke.

## Gruppenvorlage bearbeiten {#edit-group-template}

Wenn Sie Community-Gruppen in der Hauptkonsole [Gruppenvorlagen](#group-templates-console) anzeigen, können Sie eine vorhandene Gruppenvorlage zur Bearbeitung auswählen.

Das Bearbeiten einer Gruppenvorlage hat keine Auswirkungen auf Community-Sites, die bereits anhand der Vorlage erstellt wurden. Stattdessen kann die Struktur einer Community[Site direkt bearbeitet &#x200B;](/help/communities/sites-console.md#modify-structure).

Dieser Prozess bietet dieselben Bedienfelder wie [Erstellen einer &#x200B;](#create-group-template)).
