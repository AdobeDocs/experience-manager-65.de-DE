---
title: Erstellen von Knoten
description: Erfahren Sie, wie Sie das Kommentarsystem mit einer benutzerdefinierten Version überlagern, indem Sie die minimale Anzahl von Dateien aus /libs kopieren und in /apps bearbeiten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 3d72cbdf-5eb4-477d-aa61-035a846f7dcb
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 5%

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
   * **[!UICONTROL Erstellen > Ordner]**
      * Geben Sie den Namen ein: `social`
1. Knoten `social` auswählen
   * **[!UICONTROL Erstellen]** > **[!UICONTROL Ordner]**
      * Geben Sie den Namen ein: `commons`
1. Knoten `commons` auswählen
   * **[!UICONTROL Erstellen > Ordner]**
      * Geben Sie den Namen ein: `components`
1. Knoten `components` auswählen
   * **[!UICONTROL Erstellen > Ordner]**.
      * Geben Sie den Namen ein: `hbs`
1. Knoten `hbs` auswählen
   * **[!UICONTROL Erstellen]** > **[!UICONTROL Erstellen der Komponente]**
      * Titel eingeben: `comments`
      * Titel eingeben: `Comments`
      * Beschreibung eingeben: `List of comments without showing avatars`
      * Obertyp: `social/commons/components/comments`
      * Gruppe eingeben: `Communities`
      * Klicken Sie auf **[!UICONTROL Weiter]** bis **[!UICONTROL OK]**
1. Knoten `comments` auswählen

   * **[!UICONTROL Erstellen]** > **[!UICONTROL Erstellen der Komponente]**

      * Titel eingeben: `comment`
      * Titel eingeben: `Comment`
      * Beschreibung eingeben: `A comment instance without avatars`
      * Obertyp: `social/commons/components/comments/comment`
      * Gruppe eingeben: `.hidden`
      * Klicken Sie auf **[!UICONTROL Weiter]** bis **[!UICONTROL OK]**
   * Wählen Sie **[!UICONTROL Alle speichern]**
1. Löschen Sie den Standardwert `comments.jsp`
   * Knoten `/apps/social/commons/components/hbs/comments/comments.jsp` auswählen
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

Die eigene &quot;`Type`&quot;(Eigenschaft `sling:resourceType`) der Überlagerung muss eine relative Eigenschaftsreferenz sein, sodass alle Inhalte, die nicht in /apps gefunden werden, dann in /libs gesucht werden.
* Name: `sling:resourceType`
* Typ: `String`
* Wert: `social/commons/components/hbs/comments`

1. Grün `[+] Add` auswählen
   * Name: `sling:resourceType`
   * Typ: `String`
   * Wert: `social/commons/components/hbs/comments/comment`
1. Grün `[+] Add` auswählen
   * Wählen Sie **[!UICONTROL Alle speichern]**

![create-nodes](assets/create-nodes.png)
