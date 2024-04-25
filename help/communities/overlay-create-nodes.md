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

Überlagern Sie das Kommentarsystem mit einer benutzerdefinierten Version, indem Sie die minimale Anzahl von Dateien aus `/libs` in `/apps` und ändern Sie sie in `/apps`.

>[!CAUTION]
>
>Der Inhalt des Ordners /libs wird nie bearbeitet, da eine Neuinstallation oder ein Upgrade den Ordner /libs löschen oder ersetzen kann, während der Inhalt des Ordners /apps unverändert bleibt.

Verwenden [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) Erstellen Sie in einer Autoreninstanz zunächst einen Pfad im Ordner /apps , der mit dem Pfad zu den überlagerten Komponenten im Ordner /libs identisch ist.

Der duplizierte Pfad lautet:

* `/libs/social/commons/components/hbs/comments/comment`

Einige Knoten im Pfad sind Ordner und einige sind Komponenten.

1. Navigieren Sie zu [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Erstellen `/apps/social` (falls noch nicht vorhanden)
   * Auswählen `/apps` Knoten
   * **[!UICONTROL Erstellen > Ordner]**
      * Name eingeben: `social`
1. Auswählen `social` Knoten
   * **[!UICONTROL Erstellen]** > **[!UICONTROL Ordner]**
      * Name eingeben: `commons`
1. Auswählen `commons` Knoten
   * **[!UICONTROL Erstellen > Ordner]**
      * Name eingeben: `components`
1. Auswählen `components` Knoten
   * **[!UICONTROL Erstellen > Ordner]**.
      * Name eingeben: `hbs`
1. Auswählen `hbs` Knoten
   * **[!UICONTROL Erstellen]** > **[!UICONTROL Komponente erstellen]**
      * Titel eingeben: `comments`
      * Titel eingeben: `Comments`
      * Beschreibung eingeben: `List of comments without showing avatars`
      * Obertyp: `social/commons/components/comments`
      * Gruppe eingeben: `Communities`
      * Klicks **[!UICONTROL Nächste]** bis **[!UICONTROL OK]**
1. Auswählen `comments` Knoten

   * **[!UICONTROL Erstellen]** > **[!UICONTROL Komponente erstellen]**

      * Titel eingeben: `comment`
      * Titel eingeben: `Comment`
      * Beschreibung eingeben: `A comment instance without avatars`
      * Obertyp: `social/commons/components/comments/comment`
      * Gruppe eingeben: `.hidden`
      * Klicks **[!UICONTROL Nächste]** bis **[!UICONTROL OK]**
   * Auswählen **[!UICONTROL Alle speichern]**
1. Standard löschen `comments.jsp`
   * Knoten auswählen `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Wählen Sie **[!UICONTROL Löschen]** aus
1. Löschen Sie die standardmäßige Datei comment.jsp .
   * Knoten auswählen `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Wählen Sie **[!UICONTROL Löschen]** aus
   * Auswählen **[!UICONTROL Alle speichern]**

>[!NOTE]
>
>Um die Vererbungskette beizubehalten, muss die `Super Type` (Eigenschaft `sling:resourceSuperType`) der Überlagerungskomponenten auf denselben Wert wie der `Super Type` der zu überlagernden Komponenten, in diesem Fall:
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`

Die Überlagerung selbst `Type`(Eigenschaft `sling:resourceType`) muss eine relative Eigenschaftsreferenz sein, sodass alle Inhalte, die nicht in /apps gefunden werden, dann in /libs gesucht werden.
* Name: `sling:resourceType`
* Typ: `String`
* Wert: `social/commons/components/hbs/comments`

1. Grün auswählen `[+] Add`
   * Name: `sling:resourceType`
   * Typ: `String`
   * Wert: `social/commons/components/hbs/comments/comment`
1. Grün auswählen `[+] Add`
   * Auswählen **[!UICONTROL Alle speichern]**

![create-nodes](assets/create-nodes.png)
