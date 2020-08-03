---
title: Nodes erstellen
seo-title: Nodes erstellen
description: Überlagern des Kommentarsystems
seo-description: Überlagern des Kommentarsystems
uuid: 802ae28b-9989-4c2c-b466-ab76a724efd3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cd4f53ee-537b-4f10-a64f-474ba2c44576
translation-type: tm+mt
source-git-commit: 9d6ec05fdc98e33a11303d189414c2c45c5e8b3c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 6%

---


# Nodes erstellen {#create-nodes}

Überlagern Sie das Kommentarsystem mit einer benutzerdefinierten Version, indem Sie die minimale Anzahl von Dateien kopieren, die erforderlich sind, `/libs` in `/apps` und ändern Sie sie in `/apps`.

>[!CAUTION]
>
>Der Inhalt des Ordners &quot;/libs&quot;wird nie bearbeitet, da bei einer Neuinstallation oder Aktualisierung der Ordner &quot;/libs&quot;gelöscht oder ersetzt werden kann, während der Inhalt des Ordners &quot;/apps&quot;unverändert bleibt.


Erstellen Sie zunächst mit der [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) auf einer Autoreninstanz einen Pfad im Ordner &quot;/apps&quot;, der mit dem Pfad zu den überlagerten Komponenten im Ordner &quot;/libs&quot;identisch ist.

Der zu duplizierende Pfad lautet:

* `/libs/social/commons/components/hbs/comments/comment`

Einige Knoten im Pfad sind Ordner und einige sind Komponenten.

1. Navigieren Sie zu [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Erstellen `/apps/social` (sofern nicht bereits vorhanden)
   * Knoten `/apps` auswählen
   * **[!UICONTROL Erstellen > Ordner ...]**
      * Namen eingeben: `social`
1. Knoten `social` auswählen
   * **[!UICONTROL Erstellen]** > **[!UICONTROL Ordner...]**
      * Namen eingeben: `commons`
1. Knoten `commons` auswählen
   * **[!UICONTROL Erstellen > Ordner...]**
      * Namen eingeben: `components`
1. Knoten `components` auswählen
   * **[!UICONTROL Erstellen > Ordner..]**.
      * Namen eingeben: `hbs`
1. Knoten `hbs` auswählen
   * **[!UICONTROL Erstellen]** > Komponente **[!UICONTROL erstellen...]**
      * Beschriftung eingeben: `comments`
      * Enter Title: `Comments`
      * Enter Description: `List of comments without showing avatars`
      * Super Type: `social/commons/components/comments`
      * Gruppe eingeben: `Communities`
      * Klicken Sie auf **[!UICONTROL Weiter]** , bis **[!UICONTROL OK]**
1. Knoten `comments` auswählen

   * **[!UICONTROL Erstellen]** > Komponente **[!UICONTROL erstellen...]**

      * Beschriftung eingeben: `comment`
      * Enter Title: `Comment`
      * Enter Description: `A comment instance without avatars`
      * Super Type: `social/commons/components/comments/comment`
      * Gruppe eingeben: `.hidden`
      * Klicken Sie auf **[!UICONTROL Weiter]** , bis **[!UICONTROL OK]**
   * Select **[!UICONTROL Save All]**
1. Standardeinstellung löschen `comments.jsp`
   * Knoten auswählen `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Löschen **[!UICONTROL auswählen]**
1. Löschen Sie die standardmäßige Datei &quot;comment.jsp&quot;
   * Knoten auswählen `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Löschen **[!UICONTROL auswählen]**
   * Select **[!UICONTROL Save All]**

>[!NOTE]
>
>Um die Vererbungskette beizubehalten, wird für die `Super Type` (Eigenschaft `sling:resourceSuperType`) der Überlagerungskomponenten der gleiche Wert wie `Super Type` der Wert der überlagerten Komponenten festgelegt, in diesem Fall:
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`

>



Die eigene Eigenschaft `Type`(Eigenschaft `sling:resourceType`) der Überlagerung muss eine relative Selbstreferenz sein, damit nicht in /apps gefundene Inhalte in /libs gesucht werden.
* Name: `sling:resourceType`
* Typ: `String`
* Wert: `social/commons/components/hbs/comments`

1. Grün auswählen `[+] Add`
   * Name: `sling:resourceType`
   * Typ: `String`
   * Wert: `social/commons/components/hbs/comments/comment`
1. Grün auswählen `[+] Add`
   * Select **[!UICONTROL Save All]**

![create-nodes](assets/create-nodes.png)

