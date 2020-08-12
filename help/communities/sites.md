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
source-git-commit: 6ab91667ad668abf80ccf1710966169b3a187928
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 4%

---


# Site-Vorlagen {#site-templates}

Die Konsole &quot;Site-Vorlagen&quot;ist der Konsole &quot; [Gruppenvorlagen](tools-groups.md) &quot;sehr ähnlich, die sich auf Funktionen konzentriert, die für Community-Gruppen von Interesse sind.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur zur Verwendung in der Autorendatei bestimmt.


## Site Templates Console {#site-templates-console}

In der Umgebung &quot;Autor&quot;zur Konsole der Community-Sites gelangen Sie wie folgt:

* Aus globaler Navigation: **[!UICONTROL Tools > Communities > Site-Vorlagen]**

This console displays the templates from which a [community site](sites-console.md) can be created and allows new site templates to be created.

![site-template](assets/site-template.png)

## Site-Vorlage erstellen {#create-site-template}

To get started creating a new site template, select `Create`.

This will bring up the Site Editor panel which contains 3 sub-panels:

### Basic info {#basic-info}

![site-template-basicinfo](assets/site-template-basicinfo.png)

On the Basic Info panel, a name, description and whether the template is enabled or disabled are configured:

* **[!UICONTROL Name der Community-Site-Vorlage]**

   The template name id.

* **[!UICONTROL Beschreibung der Community-Site-Vorlage]**

   The template description.

* **[!UICONTROL Disabled/Enabled]**

   A toggle switch controlling whether the template is referenceable.

### Miniaturansicht       {#thumbnail}

![site-thumbnail](assets/site-thumbnail.png)

(Optional) Select the Upload Image icon in order to display a thumbnail along with the name and description to creators of community sites.

### Struktur {#structure}

![site-structure](assets/site-structure.png)

To add community functions, drag from the right side to the left in the order the site menu links should appear. Stile werden während der Erstellung der Site auf die Vorlage angewendet.

Wenn Sie beispielsweise eine Startseite erstellen möchten, ziehen Sie die Funktion &quot;Seite&quot;aus der Bibliothek und legen Sie sie unter dem Vorlagenaufbau ab. Dadurch wird das Dialogfeld für die Seitenkonfiguration geöffnet. Informationen zu den Konfigurationsdialogen finden Sie in der [Funktionskonsole](functions.md) .

Ziehen Sie weitere Community-Funktionen, die basierend auf dieser Vorlage für eine Community-Site gewünscht werden, und legen Sie sie ab.

Die Seitenfunktion stellt eine leere Seite bereit. Die Funktion &quot;Gruppen&quot;bietet die Möglichkeit, innerhalb der Community-Site eine Gruppensite (Unter-Community) zu erstellen.

>[!CAUTION]
>
>Die Funktion groups darf *nicht* die *erste oder einzige* Funktion in der Site-Struktur sein.
>
>Jede andere Funktion, wie die [Seitenfunktion](functions.md#page-function), muss eingeschlossen und zuerst aufgeführt werden.


![site-editor](assets/site-editor.png)

### Gruppenvorlagen für die Funktion &quot;Gruppen&quot; {#group-templates-for-groups-function}

Wenn Sie eine Gruppenfunktion in die Site-Vorlage aufnehmen, müssen Sie die Gruppenvorlagenauswahl festlegen, die beim Erstellen einer neuen Umgebung in der Veröffentlichungsgruppe zulässig ist.

>[!CAUTION]
>
>Die Funktion Groups darf *nicht* die *erste oder einzige* Funktion in der Site-Struktur sein.


![site-function](assets/site-functions.png)

Wenn Sie zwei oder mehr Community-Gruppenvorlagen auswählen, wird dem Gruppenadministrator beim Erstellen einer neuen Gruppe in der Community eine Auswahl angezeigt.

![site-function](assets/site-functions1.png)

##  Site-Vorlage bearbeiten{#edit-site-template}

Bei der Anzeige von Site-Vorlagen in der Haupt- [Site-Vorlagenkonsole](#site-templates-console)ist es möglich, eine vorhandene Site-Vorlage zur Bearbeitung auszuwählen.

Dieser Prozess stellt dieselben Bereiche bereit wie das [Erstellen einer Sitevorlage](#create-site-template).
