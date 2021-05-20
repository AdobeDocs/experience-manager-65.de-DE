---
title: Erstellen von Knoten
seo-title: Erstellen von Knoten
description: Überlagern des Kommentarsystems
seo-description: Überlagern des Kommentarsystems
uuid: 802ae28b-9989-4c2c-b466-ab76a724efd3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cd4f53ee-537b-4f10-a64f-474ba2c44576
exl-id: 3d72cbdf-5eb4-477d-aa61-035a846f7dcb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 8%

---

# Erstellen von Knoten {#create-nodes}

Überlagern Sie das Kommentarsystem mit einer benutzerdefinierten Version, indem Sie die minimale Anzahl von Dateien aus `/libs` in `/apps` kopieren und in `/apps` ändern.

>[!CAUTION]
>
>Der Inhalt des Ordners /libs wird nie bearbeitet, da eine Neuinstallation oder ein Upgrade den Ordner /libs löschen oder ersetzen kann, während der Inhalt des Ordners /apps unverändert bleibt.

Verwenden Sie [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) in einer Autoreninstanz, indem Sie einen Pfad im Ordner /apps erstellen, der mit dem Pfad zu den überlagerten Komponenten im Ordner /libs identisch ist.

Der duplizierte Pfad lautet:

* `/libs/social/commons/components/hbs/comments/comment`

Einige Knoten im Pfad sind Ordner und einige sind Komponenten.

1. Navigieren Sie zu [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Erstellen Sie `/apps/social` (falls noch nicht vorhanden).
   * Knoten `/apps` auswählen
   * **[!UICONTROL Erstellen > Ordner ...]**
      * Namen eingeben: `social`
1. Knoten `social` auswählen
   * **[!UICONTROL Erstellen]**  >  **[!UICONTROL Ordner...]**
      * Namen eingeben: `commons`
1. Knoten `commons` auswählen
   * **[!UICONTROL Erstellen > Ordner..]**
      * Namen eingeben: `components`
1. Knoten `components` auswählen
   * **[!UICONTROL Erstellen > Ordner..]**.
      * Namen eingeben: `hbs`
1. Knoten `hbs` auswählen
   * **[!UICONTROL Erstellen]**  > Komponente  **[!UICONTROL erstellen...]**
      * Titel eingeben: `comments`
      * Titel eingeben: `Comments`
      * Beschreibung eingeben: `List of comments without showing avatars`
      * Super Type: `social/commons/components/comments`
      * Gruppe eingeben: `Communities`
      * Klicken Sie auf **[!UICONTROL Weiter]** bis **[!UICONTROL OK]**
1. Knoten `comments` auswählen

   * **[!UICONTROL Erstellen]**  > Komponente  **[!UICONTROL erstellen...]**

      * Titel eingeben: `comment`
      * Titel eingeben: `Comment`
      * Beschreibung eingeben: `A comment instance without avatars`
      * Super Type: `social/commons/components/comments/comment`
      * Gruppe eingeben: `.hidden`
      * Klicken Sie auf **[!UICONTROL Weiter]** bis **[!UICONTROL OK]**
   * Wählen Sie **[!UICONTROL Alle speichern]**
1. Löschen Sie den Standardwert `comments.jsp`
   * Knoten auswählen `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Wählen Sie **[!UICONTROL Löschen]** aus
1. Löschen Sie die standardmäßige Datei comment.jsp .
   * select node `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Wählen Sie **[!UICONTROL Löschen]** aus
   * Wählen Sie **[!UICONTROL Alle speichern]**

>[!NOTE]
>
>Um die Vererbungskette beizubehalten, werden die `Super Type` (Eigenschaft `sling:resourceSuperType`) der Überlagerungskomponenten auf denselben Wert wie die `Super Type` der zu überlagernden Komponenten festgelegt, in diesem Fall:
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`


Die eigene Eigenschaft `Type` (Eigenschaft `sling:resourceType`) der Überlagerung muss eine relative Eigenschaftsreferenz sein, sodass alle Inhalte, die nicht in /apps gefunden werden, dann in /libs gesucht werden.
* Name: `sling:resourceType`
* Typ: `String`
* Wert: `social/commons/components/hbs/comments`

1. Wählen Sie das grüne `[+] Add`
   * Name: `sling:resourceType`
   * Typ: `String`
   * Wert: `social/commons/components/hbs/comments/comment`
1. Wählen Sie das grüne `[+] Add`
   * Wählen Sie **[!UICONTROL Alle speichern]**

![create-nodes](assets/create-nodes.png)
