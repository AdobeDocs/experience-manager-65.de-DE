---
title: Erstellen der Komponenten
description: Erfahren Sie, wie Sie Komponenten mithilfe des Kommentarsystems erweitern, das aus Kommentaren und Kommentarkomponenten besteht.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 2e02db9f-294d-4d4a-92da-3ab1d38416ab
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 3%

---

# Erstellen der Komponenten  {#create-the-components}

Beim Beispiel der Erweiterung von Komponenten wird das Kommentarsystem verwendet, das aus zwei Komponenten besteht.

* Kommentare : Das umfassende Kommentarsystem, d. h. die Komponente, die auf einer Seite platziert wird.
* Kommentar - Die Komponente, die eine Instanz eines veröffentlichten Kommentars erfasst.

Beide Komponenten müssen eingerichtet werden, insbesondere beim Anpassen des Erscheinungsbilds eines geposteten Kommentars.

>[!NOTE]
>
>Pro Website-Seite ist nur ein Kommentarsystem zulässig.
>
>Viele Communities-Funktionen enthalten bereits ein Kommentarsystem, dessen resourceType geändert werden kann, um auf das erweiterte Kommentarsystem zu verweisen.

## Erstellen der Komponente Kommentare {#create-the-comments-component}

In diesen Richtungen wird ein **Gruppen**-Wert außer `.hidden` angegeben, sodass die Komponente über den Komponenten-Browser (Sidekick) verfügbar gemacht werden kann.

Das Löschen der automatisch erstellten JSP-Datei erfolgt, da stattdessen die Standard-HBS-Datei verwendet wird.

1. Navigieren Sie zu **CRXDE|Lite** ([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp))

1. Erstellen Sie einen Speicherort für benutzerdefinierte Programme:

   * `/apps` auswählen

      * **Ordner erstellen** mit dem Namen **[!UICONTROL custom]**

   * `/apps/custom` auswählen

      * **Ordner erstellen** mit dem Namen **[!UICONTROL components]**

1. `/apps/custom/components` auswählen

   * **[!UICONTROL Erstellen > Komponente…]**

      * **label**: *comments*
      * **Titel**: *ALT-Kommentare*
      * **Beschreibung**: *Alternative Kommentarstil*
      * **Supertyp**: *social/commons/components/hbs/comments*
      * **group**: *custom*

   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL OK]** aus.

1. Erweitern Sie den erstellten Knoten: `/apps/custom/components/comments`
1. Wählen Sie **[!UICONTROL Alle speichern]**
1. Rechtsklick auf `comments.jsp`
1. Wählen Sie **[!UICONTROL Löschen]** aus
1. Wählen Sie **[!UICONTROL Alle speichern]**

![create-component](assets/create-component.png)

### Erstellen der untergeordneten Kommentarkomponente {#create-the-child-comment-component}

Legen Sie **Gruppe** auf `.hidden` fest, da nur die übergeordnete Komponente in eine Seite aufgenommen werden soll.

Das Löschen der automatisch erstellten JSP-Datei erfolgt, da stattdessen die Standard-HBS-Datei verwendet wird.

1. Navigieren Sie zum Knoten `/apps/custom/components/comments` .
1. Rechtsklicken Sie auf den Knoten

   * Wählen **[!UICONTROL Erstellen]** > **[!UICONTROL Komponente…]**

      * **label**: *comment*
      * **Titel**: *ALT-Kommentar*
      * **Beschreibung**: *Alternative Kommentarstil*
      * **Supertyp**: *social/commons/components/hbs/comments/comment*
      * **Gruppe**: `*.hidden*`

   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL OK]** aus.

1. Erweitern Sie den erstellten Knoten: `/apps/custom/components/comments/comment`
1. Wählen Sie **[!UICONTROL Alle speichern]**
1. Rechtsklick auf `comment.jsp`
1. Wählen Sie **[!UICONTROL Löschen]** aus
1. Wählen Sie **[!UICONTROL Alle speichern]**

![create-child-component](assets/create-child-component.png)

![create-component-crxde](assets/create-component-crxde.png)

### Kopieren und Ändern der Standard-HBS-Skripte {#copy-and-modify-the-default-hbs-scripts}

Verwendet [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Kopieren `comments.hbs`

   * Von [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * So [&#x200B; Sie/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* `comments.hbs` bearbeiten nach:

   * Ändern Sie den Wert des `data-scf-component` Attributs (~Zeile 20):

      * Von `social/commons/components/hbs/comments`
      * `/apps/custom/components/comments`

   * Ändern Sie , um die benutzerdefinierte Kommentarkomponente einzuschließen (~Zeile 75):

      * `{{include this resourceType='social/commons/components/hbs/comments/comment'}}` ersetzen
      * Mit `{{include this resourceType='/apps/custom/components/comments/comment'}}`

* Kopieren `comment.hbs`

   * Von [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * So [&#x200B; Sie/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* `comment.hbs` bearbeiten nach:

   * Ändern Sie den Wert des Attributs data-scf-component (~ Zeile 19)

      * Von `social/commons/components/hbs/comments/comment`
      * `/apps/custom/components/comments/comment`

* `/apps/custom` auswählen
* Wählen Sie **[!UICONTROL Alle speichern]**

## Erstellen eines Client-Bibliotheksordners {#create-a-client-library-folder}

Um zu vermeiden, dass diese Client-Bibliothek eingeschlossen werden muss, kann der Kategoriewert für die clientlib des Standard-Kommentarsystems verwendet werden ( `cq.social.author.hbs.comments`). Diese Client-Bibliothek muss dann jedoch auch für alle Instanzen der Standardkomponente eingeschlossen werden.

Verwendet [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* `/apps/custom/components/comments` auswählen
* Wählen Sie **[!UICONTROL Knoten erstellen]**

   * **Name**: `clientlibs`
   * **Typ**: `cq:ClientLibraryFolder`
   * Fügen Sie zur Registerkarte **[!UICONTROL Eigenschaften]** hinzu:

      * **name** `categories` **type** `String` **value** `cq.social.author.hbs.comments` `Multi`
      * **name** `dependencies` **type** `String` **value** `cq.social.scf` `Multi`

* Wählen Sie **[!UICONTROL Alle speichern]**
* Erstellen Sie bei ausgewähltem `/apps/custom/components/comments/clientlib`-Knoten drei Dateien:

   * **Name**: `css.txt`
   * **Name**: `js.txt`
   * **Name**: customcommentsSystem.js

* Geben Sie „customcommentsSystem.js“ als Inhalt der `js.txt` ein
* Wählen Sie **[!UICONTROL Alle speichern]**

![comments-clientlibs](assets/comments-clientlibs.png)

## SCF-Modell registrieren und anzeigen {#register-the-scf-model-view}

Beim Erweitern (Überschreiben) einer SCF-Komponente ist der resourceType anders (eine Überlagerung verwendet den relativen Suchmechanismus, der `/apps` durchsucht, bevor er `/libs` wird, damit der resourceType gleich bleibt). Daher müssen Sie JavaScript (in der Client-Bibliothek) schreiben, um das SCF-JS-Modell zu registrieren und für den benutzerdefinierten resourceType anzuzeigen.

Geben Sie den folgenden Text als Inhalt von `customcommentsystem.js` ein:

### customcommentsystem.js {#customcommentsystem-js}

```xml
(function($CQ, _, Backbone, SCF) {
    "use strict";

    var CustomComment = SCF.Components["social/commons/components/hbs/comments/comment"].Model;
    var CustomCommentView = SCF.Components["social/commons/components/hbs/comments/comment"].View;

    var CustomCommentSystem = SCF.Components["social/commons/components/hbs/comments"].Model;
    var CustomCommentSystemView = SCF.Components["social/commons/components/hbs/comments"].View;

    SCF.registerComponent('/apps/custom/components/comments/comment', CustomComment, CustomCommentView);
    SCF.registerComponent('/apps/custom/components/comments', CustomCommentSystem, CustomCommentSystemView);

})($CQ, _, Backbone, SCF);
```

* Wählen Sie **[!UICONTROL Alle speichern]**

## Publish - die App {#publish-the-app}

Um die erweiterte Komponente in der Veröffentlichungsumgebung nutzen zu können, muss die benutzerdefinierte Komponente repliziert werden.

Eine Möglichkeit, dies zu tun, ist:

* Über die globale Navigation,

   * Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**
   * Wählen Sie **[!UICONTROL Baum aktivieren]**
   * `Start Path` wird auf `/apps/custom` gesetzt
   * Deaktivieren Sie **[!UICONTROL Nur geändert]**
   * Schaltfläche **[!UICONTROL Aktivieren]** auswählen
