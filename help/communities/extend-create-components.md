---
title: Komponenten erstellen
seo-title: Komponenten erstellen
description: Komponente "Kommentare"erstellen
seo-description: Komponente "Kommentare"erstellen
uuid: ea6e00d4-1db7-40ef-ae49-9ec55df58adf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 83c4f18a-d7d6-4090-88c7-41a9075153b5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Komponenten erstellen {#create-the-components}

Das Beispiel zum Erweitern von Komponenten verwendet das Kommentarsystem, das eigentlich aus zwei Komponenten besteht

* Kommentare - Das umgehende Kommentarsystem, bei dem es sich um die auf einer Seite platzierte Komponente handelt
* Kommentar - Die Komponente, die eine Instanz eines veröffentlichten Kommentars erfasst

Beide Komponenten müssen eingerichtet werden, insbesondere wenn das Erscheinungsbild eines geposteten Kommentars angepasst werden soll.

>[!NOTE]
>
>Pro Site-Seite ist nur ein Kommentarsystem zulässig.
>
>Viele Communities-Funktionen beinhalten bereits ein Kommentarsystem, dessen resourceType geändert werden kann, um auf das erweiterte Kommentarsystem zu verweisen.

## Create the Comments Component {#create-the-comments-component}

In diesen Anweisungen wird ein anderer **Gruppenwert** angegeben, `.hidden` damit die Komponente über den Komponenten-Browser (Sidekick) verfügbar gemacht werden kann.

Das Löschen der automatisch erstellten JSP-Datei erfolgt, weil stattdessen die Standard-HBS-Datei verwendet wird.

1. Browse to **CRXDE|Lite** ([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp))

1. Erstellen Sie einen Speicherort für benutzerdefinierte Anwendungen:

   * Wählen Sie den `/apps` Knoten

      * **Ordner** mit **[!UICONTROL benutzerdefiniertem Namen erstellen]**
   * Wählen Sie den `/apps/custom` Knoten

      * **Erstellen von** Komponenten mit Ordnernamen ****


1. Wählen Sie den `/apps/custom/components` Knoten

   * **[!UICONTROL Erstellen > Komponente...]**

      * **Beschriftung**: *Kommentare*
      * **Titel**: Alt- *Kommentare*
      * **Beschreibung**: Stil *für alternative Kommentare*
      * **Super Type**: *social/commons/components/hbs/comments*
      * **Gruppe**: *Benutzerdefiniert*
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL OK]** aus


1. Erweitern Sie den soeben erstellten Knoten: `/apps/custom/components/comments`
1. Select **[!UICONTROL Save All]**
1. Right-click `comments.jsp`
1. Löschen **[!UICONTROL auswählen]**
1. Select **[!UICONTROL Save All]**

![chlimage_1-70](assets/chlimage_1-70.png)

### Komponente für untergeordneten Kommentar erstellen {#create-the-child-comment-component}

Diese Anweisungen setzen **Gruppe** auf `.hidden` , da nur die übergeordnete Komponente in eine Seite einbezogen werden sollte.

Das Löschen der automatisch erstellten JSP-Datei erfolgt, weil stattdessen die Standard-HBS-Datei verwendet wird.

1. Navigieren zum `/apps/custom/components/comments` Knoten
1. Klicken Sie mit der rechten Maustaste auf den Knoten

   * Wählen Sie **[!UICONTROL Erstellen > Komponente...]**

      * **Beschriftung**: *Kommentar*
      * **Titel**: Kommentar *Alt*
      * **Beschreibung**: *Alternativer Kommentarstil*
      * **Super Type**: *social/commons/components/hbs/comments/comment*
      * **Gruppe**: `*.hidden*`
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL Weiter]**
   * Wählen Sie **[!UICONTROL OK]** aus


1. Erweitern Sie den soeben erstellten Knoten: `/apps/custom/components/comments/comment`
1. Select **[!UICONTROL Save All]**
1. Right-click `comment.jsp`
1. Löschen **[!UICONTROL auswählen]**
1. Select **[!UICONTROL Save All]**

![chlimage_1-71](assets/chlimage_1-71.png) ![chlimage_1-72](assets/chlimage_1-72.png)

### Standardskripte für HBS kopieren und ändern {#copy-and-modify-the-default-hbs-scripts}

Using [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Kopieren `comments.hbs`

   * Von [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * To [/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* Bearbeiten `comments.hbs` in:

   * Ändern Sie den Wert des `data-scf-component` Attributs (~line 20):

      * Von `social/commons/components/hbs/comments`
      * An `/apps/custom/components/comments`
   * Ändern Sie die Aufnahme der benutzerdefinierten Kommentarkomponente (~line 75):

      * Ersetzen `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * mit `{{include this resourceType='/apps/custom/components/comments/comment'}}`


* Kopieren `comment.hbs`

   * Von [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * To [/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* Bearbeiten `comment.hbs` in:

   * Den Wert des Attributs data-scf-component (~ Zeile 19) ändern

      * Von `social/commons/components/hbs/comments/comment`
      * An `/apps/custom/components/comments/comment`

* Knoten `/apps/custom` auswählen
* Select **[!UICONTROL Save All]**

## Erstellen eines Client-Bibliotheksordners {#create-a-client-library-folder}

Um zu vermeiden, dass diese Client-Bibliothek explizit einbezogen werden muss, könnte der Kategoriewert für die clientlib des Standard-Kommentarsystems verwendet werden ( `cq.social.author.hbs.comments`), aber dann würde diese clientlib auch für alle Instanzen der Standardkomponente eingeschlossen.

Using [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Knoten `/apps/custom/components/comments` auswählen
* Knoten **[!UICONTROL erstellen auswählen]**

   * **Name**: `clientlibs`
   * **Typ**: `cq:ClientLibraryFolder`
   * Registerkarte &quot;Zu **[!UICONTROL Eigenschaften]** hinzufügen&quot;:

      * **Name** `categories` Typ ****`String`Wert **** `cq.social.author.hbs.comments``Multi`
      * **Name** `dependencies` Typ ****`String`Wert **** `cq.social.scf``Multi`

* Select **[!UICONTROL Save All]**
* Erstellen Sie `/apps/custom/components/comments/clientlib`bei ausgewählter Node 3 Dateien:

   * **Name**: `css.txt`
   * **Name**: `js.txt`
   * **Name**: customommentsystem.js

* Geben Sie als Inhalt &quot;customommentsystem.js&quot;ein `js.txt`
* Select **[!UICONTROL Save All]**

![chlimage_1-73](assets/chlimage_1-73.png)

## SCF-Modell und Ansicht registrieren {#register-the-scf-model-view}

Beim Erweitern (Überschreiben) einer SCF-Komponente ist resourceType anders (Überlagern verwendet den relativen Suchmechanismus, der `/apps` zuvor durchsucht wird, `/libs` sodass resourceType gleich bleibt). Daher ist es notwendig, JavaScript (in der Client-Bibliothek) zu schreiben, um das SCF JS-Modell zu registrieren und für den benutzerdefinierten resourceType anzuzeigen.

Geben Sie den folgenden Text als Inhalt von ein `customcommentsystem.js`:

### customommentsystem.js {#customcommentsystem-js}

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

* Select **[!UICONTROL Save All]**

## App veröffentlichen {#publish-the-app}

Um die erweiterte Komponente in der Veröffentlichungsumgebung zu nutzen, müssen Sie die benutzerdefinierte Komponente replizieren.

Eine Möglichkeit dazu ist

* Aus globaler Navigation

   * Wählen Sie **[!UICONTROL Werkzeuge > Bereitstellung > Replikation]**
   * Wählen Sie nun eine der folgenden Optionen aus `Activate Tree`
   * Festlegen `Start Path`: nach `/apps/custom`
   * Deaktivieren `Only Modified`
   * Schaltfläche `Activate`&quot;Auswählen&quot;

