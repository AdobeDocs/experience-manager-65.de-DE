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
source-git-commit: 418e7fad2d990f1a7cb3b69ab4c290ca1b7075ba
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 6%

---


# Erstellen Sie die Komponenten {#create-the-components}

Das Beispiel zum Erweitern von Komponenten verwendet das Kommentarsystem, das eigentlich aus zwei Komponenten besteht

* Kommentare - Das umfassende Kommentarsystem, bei dem es sich um die auf einer Seite platzierte Komponente handelt.
* Kommentar: Die Komponente, die eine Instanz eines geposteten Kommentars erfasst.

Beide Komponenten müssen eingerichtet werden, insbesondere wenn das Erscheinungsbild eines geposteten Kommentars angepasst werden soll.

>[!NOTE]
>
>Pro Site-Seite ist nur ein Kommentarsystem zulässig.
>
>Viele Communities-Funktionen beinhalten bereits ein Kommentarsystem, dessen resourceType geändert werden kann, um auf das erweiterte Kommentarsystem zu verweisen.

## Erstellen der Kommentarkomponente {#create-the-comments-component}

In diesen Anweisungen wird ein anderer **Group**-Wert als `.hidden` angegeben, damit die Komponente über den Komponenten-Browser (Sidekick) verfügbar gemacht werden kann.

Das Löschen der automatisch erstellten JSP-Datei erfolgt, weil stattdessen die Standard-HBS-Datei verwendet wird.

1. Gehen Sie zu **CRXDE|Lite** ([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp))

1. Erstellen Sie einen Speicherort für benutzerdefinierte Anwendungen:

   * Wählen Sie den Knoten `/apps`

      * **Erstellen von** Ordnern mit  **[!UICONTROL benutzerdefiniertem Namen]**
   * Wählen Sie den Knoten `/apps/custom`

      * **Erstellen** von  **[!UICONTROL Komponenten mit Ordnernamen]**


1. Wählen Sie den Knoten `/apps/custom/components`

   * **[!UICONTROL Erstellen > Komponente...]**

      * **Beschriftung**:  *Kommentare*
      * **Titel**:  *Alt-Kommentare*
      * **Beschreibung**:  *Alternativkommentar*
      * **Super Type**:  *social/commons/components/hbs/comments*
      * **Gruppe**:  *Benutzerdefiniert*
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL OK]** aus


1. Erweitern Sie den soeben erstellten Knoten: `/apps/custom/components/comments`
1. Wählen Sie **[!UICONTROL Alle speichern]**
1. Klicken Sie mit der rechten Maustaste auf `comments.jsp`
1. Wählen Sie **[!UICONTROL Löschen]**
1. Wählen Sie **[!UICONTROL Alle speichern]**

![create-component](assets/create-component.png)

### Erstellen der untergeordneten Kommentarkomponente {#create-the-child-comment-component}

Diese Anweisungen setzen **Gruppe** auf `.hidden`, da nur die übergeordnete Komponente in eine Seite einbezogen werden sollte.

Das Löschen der automatisch erstellten JSP-Datei erfolgt, weil stattdessen die Standard-HBS-Datei verwendet wird.

1. Navigieren Sie zum Knoten `/apps/custom/components/comments`
1. Klicken Sie mit der rechten Maustaste auf den Knoten

   * Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Komponente...]**

      * **Beschriftung**:  *Kommentar*
      * **Titel**:  *Alt-Kommentar*
      * **Beschreibung**:  *Alternativer Kommentarstil*
      * **Super Type**:  *social/commons/components/hbs/comments/comment*
      * **Gruppe**: `*.hidden*`
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL OK]** aus


1. Erweitern Sie den soeben erstellten Knoten: `/apps/custom/components/comments/comment`
1. Wählen Sie **[!UICONTROL Alle speichern]**
1. Klicken Sie mit der rechten Maustaste auf `comment.jsp`
1. Wählen Sie **[!UICONTROL Löschen]**
1. Wählen Sie **[!UICONTROL Alle speichern]**

![create-child-component](assets/create-child-component.png)

![create-component-crxde](assets/create-component-crxde.png)

### Kopieren und Ändern der Standard-HBS-Skripte {#copy-and-modify-the-default-hbs-scripts}

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Kopieren `comments.hbs`

   * Von [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * Nach [/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* Bearbeiten Sie `comments.hbs` nach:

   * Ändern Sie den Wert des Attributs `data-scf-component` (~line 20):

      * Von `social/commons/components/hbs/comments`
      * An `/apps/custom/components/comments`
   * Ändern Sie die Aufnahme der benutzerdefinierten Kommentarkomponente (~line 75):

      * Ersetzen `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * mit `{{include this resourceType='/apps/custom/components/comments/comment'}}`


* Kopieren `comment.hbs`

   * Von [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * Nach [/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* Bearbeiten Sie `comment.hbs` nach:

   * Den Wert des Attributs data-scf-component (~ Zeile 19) ändern

      * Von `social/commons/components/hbs/comments/comment`
      * An `/apps/custom/components/comments/comment`

* Knoten `/apps/custom` auswählen
* Wählen Sie **[!UICONTROL Alle speichern]**

## Erstellen eines Client-Bibliotheksordners {#create-a-client-library-folder}

Um zu vermeiden, dass diese Client-Bibliothek explizit einbezogen werden muss, könnte der Wert &quot;Kategorien&quot;für die clientlib des standardmäßigen Kommentarsystems verwendet werden ( `cq.social.author.hbs.comments`), aber dann würde diese clientlib auch für alle Instanzen der Standardkomponente enthalten sein.

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Knoten `/apps/custom/components/comments` auswählen
* Wählen Sie **[!UICONTROL Knoten erstellen]**

   * **Name**: `clientlibs`
   * **Typ**: `cq:ClientLibraryFolder`
   * hinzufügen auf die Registerkarte **[!UICONTROL Eigenschaften]**:

      * **** `categories` **** `String` **NameTypeValue** `cq.social.author.hbs.comments` `Multi`
      * **** `dependencies` **** `String` **NameTypeValue** `cq.social.scf` `Multi`

* Wählen Sie **[!UICONTROL Alle speichern]**
* Wenn der Knoten `/apps/custom/components/comments/clientlib`s ausgewählt ist, erstellen Sie 3 Dateien:

   * **Name**:  `css.txt`
   * **Name**:  `js.txt`
   * **Name**: customommentsystem.js

* Geben Sie als Inhalt von `js.txt` &quot;customommentsystem.js&quot;ein
* Wählen Sie **[!UICONTROL Alle speichern]**

![comments-clientlibs](assets/comments-clientlibs.png)

## SCF-Modell und -Ansicht {#register-the-scf-model-view} registrieren

Beim Erweitern (Überschreiben) einer SCF-Komponente ist resourceType anders (Überlagern verwendet den relativen Suchmechanismus, der `/apps` vor `/libs` durchsucht, sodass resourceType gleich bleibt). Daher müssen Sie JavaScript (in der Client-Bibliothek) schreiben, um das SCF JS-Modell und die Ansicht für den benutzerdefinierten resourceType zu registrieren.

Geben Sie den folgenden Text als Inhalt von `customcommentsystem.js` ein:

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

* Wählen Sie **[!UICONTROL Alle speichern]**

## App {#publish-the-app} veröffentlichen

Um die erweiterte Komponente in der Umgebung &quot;Veröffentlichen&quot;nutzen zu können, müssen Sie die benutzerdefinierte Komponente replizieren.

Eine Möglichkeit dazu ist:

* von der globalen Navigation,

   * Wählen Sie **[!UICONTROL Werkzeuge]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**
   * Wählen Sie **[!UICONTROL Baum aktivieren]**
   * `Start Path` auf `/apps/custom` setzen
   * Deaktivieren Sie **[!UICONTROL Nur geändert]**
   * Schaltfläche **[!UICONTROL Aktivieren]**

