---
title: Site-Vorlagen
description: Erfahren Sie, wie Sie auf die Site-Vorlagenkonsole zugreifen, um eine Community-Site zu erstellen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 05a944a3-adb1-47b4-b4a5-15bac91c995e
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---

# Site-Vorlagen {#site-templates}

Die Site-Vorlagenkonsole ähnelt der [Gruppenvorlagen](tools-groups.md)-Konsole, die sich auf Funktionen konzentriert, die für Community-Gruppen von Interesse sind.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur für die Autorenumgebung vorgesehen.

## Site-Vorlagenkonsole {#site-templates-console}

Gehen Sie in der Autorenumgebung wie folgt vor, um zur Community-Sites-Konsole zu gelangen:

* Über die globale Navigation: **[!UICONTROL Tools > Communities > Site-Vorlagen]**

Diese Konsole zeigt die Vorlagen an, aus denen eine [Community-Site](sites-console.md) erstellt werden kann, und ermöglicht die Erstellung neuer Site-Vorlagen.

![site-template](assets/site-template.png)

## Site-Vorlage erstellen {#create-site-template}

Wählen Sie `Create` aus, um mit der Erstellung einer Site-Vorlage zu beginnen.

Dadurch wird das Site-Editor-Bedienfeld geöffnet, das drei Unterbedienfelder enthält:

### Grundlegende Informationen {#basic-info}

![site-template-basicinfo](assets/site-template-basicinfo.png)

Im Bereich Basic Info werden ein Name, eine Beschreibung und Angaben dazu konfiguriert, ob die Vorlage aktiviert oder deaktiviert ist:

* **[!UICONTROL Community-Site-Vorlagenname]**

  Die Vorlagenname-ID.

* **[!UICONTROL Beschreibung der Community-Site-Vorlage]**

  Die Vorlagenbeschreibung.

* **[!UICONTROL Deaktiviert/Aktiviert]**

  Ein Umschalter, der steuert, ob auf die Vorlage verwiesen werden kann.

### Miniaturansicht {#thumbnail}

![site-thumbnail](assets/site-thumbnail.png)

(Optional) Klicken Sie auf das Symbol Bild hochladen , um eine Miniaturansicht zusammen mit dem Namen und der Beschreibung für die Ersteller von Community-Sites anzuzeigen.

### Struktur {#structure}

![site-structure](assets/site-structure.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in der Reihenfolge, in der die Links im Site-Menü angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise eine Startseite möchten, ziehen Sie die Seitenfunktion aus der Bibliothek und legen Sie sie unter dem Vorlagen-Builder ab. Dadurch wird das Dialogfeld für die Seitenkonfiguration geöffnet. Siehe die [Funktionskonsole](functions.md) für Informationen zu den Konfigurationsdialogen.

Ziehen Sie weiterhin alle anderen Community-Funktionen, die für eine auf dieser Vorlage basierende Community-Site gewünscht werden, per Drag-and-Drop.

Die Seitenfunktion stellt eine leere Seite bereit. Mit der Funktion Gruppen können Sie innerhalb der Community-Site eine Gruppen-Site (Unter-Community) erstellen.

>[!CAUTION]
>
>Die Funktion Gruppen darf *weder die erste noch die einzige* Funktion in der Site-Struktur sein.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](functions.md#page-function), muss eingeschlossen und zuerst aufgeführt werden.

![site-editor](assets/site-editor.png)

### Gruppenvorlagen für die Gruppenfunktion {#group-templates-for-groups-function}

Wenn Sie eine Funktion „Gruppen“ in die Site-Vorlage aufnehmen, erfordert die Konfiguration die Angabe der Gruppenvorlagenoptionen, die zulässig sind, wenn eine neue Gruppe in der Veröffentlichungsumgebung erstellt wird.

>[!CAUTION]
>
>Die Funktion Gruppen darf *weder die erste noch die einzige* Funktion in der Site-Struktur sein.

![site-features](assets/site-functions.png)

Durch die Auswahl von zwei oder mehr Community-Gruppenvorlagen hat der Gruppenadministrator die Möglichkeit, eine Gruppe beim tatsächlichen Erstellen in der Community zu erstellen.

![site-function](assets/site-functions1.png)

## Site-Vorlage bearbeiten {#edit-site-template}

Beim Anzeigen von Site-Vorlagen in der [Site-Vorlagenkonsole](#site-templates-console) können Sie eine vorhandene Site-Vorlage zur Bearbeitung auswählen.

Dieser Prozess bietet dieselben Bedienfelder wie [Erstellen einer Site-Vorlage](#create-site-template).
