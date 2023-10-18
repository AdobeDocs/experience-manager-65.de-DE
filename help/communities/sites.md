---
title: Site-Vorlagen
description: Erfahren Sie, wie Sie auf die Konsole "Site-Vorlagen"zugreifen können, um eine Community-Site zu erstellen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 05a944a3-adb1-47b4-b4a5-15bac91c995e
source-git-commit: 00b6f2f03470aca7f87717818d0dfcd17ac16bed
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 4%

---

# Site-Vorlagen {#site-templates}

Die Site-Vorlagenkonsole ähnelt der [Gruppenvorlagen](tools-groups.md) -Konsole, die sich auf Funktionen konzentriert, die für Community-Gruppen von Interesse sind.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md), und [Community-Funktionen](functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Site-Vorlagenkonsole {#site-templates-console}

In der Autorenumgebung, um die Community-Sites-Konsole zu erreichen:

* Über die globale Navigation: **[!UICONTROL Tools > Communities > Site-Vorlagen]**

Diese Konsole zeigt die Vorlagen an, aus denen ein [Community-Site](sites-console.md) kann erstellt werden und die Erstellung neuer Site-Vorlagen ermöglicht.

![site-template](assets/site-template.png)

## Site-Vorlage erstellen {#create-site-template}

Wählen Sie zunächst `Create`.

Dadurch wird der Site-Editor-Bereich geöffnet, der drei Unterbereiche enthält:

### Basisinformationen {#basic-info}

![site-template-basicinfo](assets/site-template-basicinfo.png)

Im Bedienfeld &quot;Grundlegende Informationen&quot;werden ein Name, eine Beschreibung und die Frage, ob die Vorlage aktiviert oder deaktiviert ist, konfiguriert:

* **[!UICONTROL Name der Community-Site-Vorlage]**

  Die Vorlagenname-ID.

* **[!UICONTROL Beschreibung der Community-Site-Vorlage]**

  Die Vorlagenbeschreibung.

* **[!UICONTROL Deaktiviert/Aktiviert]**

  Ein Umschalter steuert, ob die Vorlage referenzierbar ist.

### Miniaturansicht {#thumbnail}

![site-thumbnail](assets/site-thumbnail.png)

(Optional) Wählen Sie das Symbol Bild hochladen aus, um eine Miniaturansicht zusammen mit dem Namen und der Beschreibung für Ersteller von Community-Sites anzuzeigen.

### Struktur {#structure}

![site-structure](assets/site-structure.png)

Um Community-Funktionen hinzuzufügen, ziehen Sie von der rechten Seite nach links in die Reihenfolge, in der die Links zum Site-Menü angezeigt werden sollen. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise eine Homepage wünschen, ziehen Sie die Funktion Seite aus der Bibliothek und legen Sie sie unter dem Vorlagenaufbau ab. Dadurch wird das Dialogfeld für die Seitenkonfiguration geöffnet. Siehe [Funktionenkonsole](functions.md) für Informationen zu den Konfigurationsdialogfeldern.

Ziehen Sie weiterhin alle anderen Community-Funktionen, die für eine auf dieser Vorlage basierende Community-Site gewünscht werden, per Drag-and-Drop.

Die Seitenfunktion stellt eine leere Seite bereit. Mit der Funktion Gruppen können Sie innerhalb der Community-Site eine Gruppensite (Subcommunity) erstellen.

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;muss *darf nicht die erste sein und die einzige* -Funktion in der Site-Struktur.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](functions.md#page-function), muss zuerst eingeschlossen und aufgelistet werden.

![site-editor](assets/site-editor.png)

### Gruppenvorlagen für Gruppenfunktionen {#group-templates-for-groups-function}

Wenn Sie eine Gruppenfunktion in die Site-Vorlage aufnehmen, erfordert die Konfiguration die Angabe der Gruppenvorlagenoptionen, die zulässig sind, wenn eine neue Gruppe in der Veröffentlichungsumgebung erstellt wird.

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;muss *darf nicht die erste sein und die einzige* -Funktion in der Site-Struktur.

![site-features](assets/site-functions.png)

Wenn Sie zwei oder mehr Community-Gruppenvorlagen auswählen, können Sie den Gruppenadministrator beim Erstellen einer Gruppe in der Community auswählen.

![site-function](assets/site-functions1.png)

## Site-Vorlage bearbeiten {#edit-site-template}

Beim Anzeigen von Site-Vorlagen in der Hauptseite [Site-Vorlagen-Konsole](#site-templates-console)können Sie eine vorhandene Site-Vorlage zur Bearbeitung auswählen.

Dieser Prozess stellt dieselben Bedienfelder wie [Erstellen einer Site-Vorlage](#create-site-template).
