---
title: Site-Vorlagen
seo-title: Site-Vorlagen
description: Zugriff auf die Konsole "Site-Vorlagen"
seo-description: Zugriff auf die Konsole "Site-Vorlagen"
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Site-Vorlagen {#site-templates}

Die Konsole &quot;Site-Vorlagen&quot;ist der Konsole &quot; [Gruppenvorlagen](tools-groups.md) &quot;sehr ähnlich, die sich auf Funktionen konzentriert, die für Community-Gruppen von Interesse sind.

>[!NOTE]
>
>Die Konsolen zum Erstellen von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur für die Verwendung in der Autorenumgebung vorgesehen.

## Site-Vorlagenkonsole {#site-templates-console}

In der Autorenumgebung, um die Community-Sites-Konsole zu erreichen

* Aus globaler Navigation: **[!UICONTROL Tools > Communities > Site-Vorlagen]**

Diese Konsole zeigt die Vorlagen an, aus denen eine [Community-Site](sites-console.md) erstellt werden kann, und ermöglicht die Erstellung neuer Site-Vorlagen.

![chlimage_1-18](assets/chlimage_1-18.png)

## Site-Vorlage erstellen {#create-site-template}

Um eine neue Site-Vorlage zu erstellen, wählen Sie `Create`.

Dadurch wird der Site-Editor-Bereich angezeigt, der drei Unterbereiche enthält:

### Basic info {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

Im Bedienfeld &quot;Grundlegende Informationen&quot;werden ein Name, eine Beschreibung und die Konfiguration der Vorlage, ob sie aktiviert oder deaktiviert ist, wie folgt konfiguriert:

* **[!UICONTROL Community-Site-Vorlagenname]** Die Vorlagenname-ID

* **[!UICONTROL Community-Site-Vorlagenbeschreibung]** Die Vorlagenbeschreibung

* **[!UICONTROL Deaktiviert/Aktiviert]** Ein Umschalter, der steuert, ob die Vorlage referenzierbar ist

### Miniatur {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

(Optional) Wählen Sie das Symbol Bild hochladen, um eine Miniaturansicht mit dem Namen und der Beschreibung für Ersteller von Community-Sites anzuzeigen.

### Struktur {#structure}

![chlimage_1-21](assets/chlimage_1-21.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in der Reihenfolge, in der die Sitemenü-Links angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise eine Homepage wünschen, ziehen Sie die Funktion &quot;Seite&quot;aus der Bibliothek und legen Sie sie unter dem Vorlagenaufbau ab. Dadurch wird das Dialogfeld für die Seitenkonfiguration geöffnet. Informationen zu den Konfigurationsdialogen finden Sie in der [Funktionskonsole](functions.md) .

Ziehen Sie weitere Community-Funktionen, die basierend auf dieser Vorlage für eine Community-Site gewünscht werden, und legen Sie sie ab.

Die Seitenfunktion stellt eine leere Seite bereit. Die Funktion &quot;Gruppen&quot;bietet die Möglichkeit, innerhalb der Community-Site eine Gruppensite (Unter-Community) zu erstellen.

>[!CAUTION]
>
>Die Funktion groups darf *nicht* die *erste oder einzige* Funktion in der Site-Struktur sein.
>
>Jede andere Funktion, wie die [Seitenfunktion](functions.md#page-function), muss eingeschlossen und zuerst aufgeführt werden.

![chlimage_1-22](assets/chlimage_1-22.png)

### Gruppenvorlagen für die Funktion &quot;Gruppen&quot; {#group-templates-for-groups-function}

Wenn Sie eine Gruppenfunktion in die Sitevorlage aufnehmen, erfordert die Konfiguration die Angabe der Gruppenvorlagenauswahl, die zulässig ist, wenn eine neue Gruppe in der Veröffentlichungsumgebung erstellt wird.

>[!CAUTION]
>
>Die Funktion Groups darf *nicht* die *erste oder einzige* Funktion in der Site-Struktur sein.

![chlimage_1-23](assets/chlimage_1-23.png)

Wenn Sie zwei oder mehr Community-Gruppenvorlagen auswählen, wird dem Gruppenadministrator beim Erstellen einer neuen Gruppe in der Community eine Auswahl angezeigt.

![chlimage_1-24](assets/chlimage_1-24.png)

##  Site-Vorlage bearbeiten{#edit-site-template}

Bei der Anzeige von Site-Vorlagen in der Haupt- [Site-Vorlagenkonsole](#site-templates-console)ist es möglich, eine vorhandene Site-Vorlage zur Bearbeitung auszuwählen.

Dieser Prozess stellt dieselben Bereiche bereit wie das [Erstellen einer Sitevorlage](#create-site-template).
