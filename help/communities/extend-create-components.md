---
title: Erstellen der Komponenten
seo-title: Create the Components
description: Erstellen der Komponente Kommentare
seo-description: Create the Comments component
uuid: ea6e00d4-1db7-40ef-ae49-9ec55df58adf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 83c4f18a-d7d6-4090-88c7-41a9075153b5
exl-id: 2e02db9f-294d-4d4a-92da-3ab1d38416ab
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 11%

---

# Erstellen der Komponenten  {#create-the-components}

Das Beispiel der Erweiterung von Komponenten verwendet das Kommentarsystem, das eigentlich aus zwei Komponenten besteht

* Kommentare - Das umfassende Kommentarsystem, bei dem es sich um die auf einer Seite platzierte Komponente handelt.
* Kommentar - Die Komponente, die eine Instanz eines veröffentlichten Kommentars erfasst.

Beide Komponenten müssen eingerichtet werden, insbesondere wenn das Erscheinungsbild eines veröffentlichten Kommentars angepasst wird.

>[!NOTE]
>
>Pro Site-Seite ist nur ein Kommentarsystem zulässig.
>
>Viele Communities-Funktionen enthalten bereits ein Kommentarsystem, dessen resourceType so geändert werden kann, dass er auf das erweiterte Kommentarsystem verweist.

## Erstellen der Kommentarkomponente {#create-the-comments-component}

Diese Anweisungen geben eine **Gruppe** Wert, der `.hidden` sodass die Komponente über den Komponenten-Browser (Sidekick) verfügbar gemacht werden kann.

Das Löschen der automatisch erstellten JSP-Datei erfolgt dadurch, dass stattdessen die standardmäßige HBS-Datei verwendet wird.

1. Navigieren Sie zu **CRXDE|Lite** ([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp))

1. Erstellen Sie einen Speicherort für benutzerdefinierte Anwendungen:

   * Wählen Sie die `/apps` Knoten

      * **Ordner erstellen** benannt **[!UICONTROL custom]**
   * Wählen Sie die `/apps/custom` Knoten

      * **Ordner erstellen** benannt **[!UICONTROL Komponenten]**


1. Wählen Sie die `/apps/custom/components` Knoten

   * **[!UICONTROL Erstellen > Komponente..]**

      * **Titel**: *Kommentare*
      * **Titel**: *Alt-Kommentare*
      * **Beschreibung**: *Alternativer Kommentar-Stil*
      * **Supertyp**: *social/commons/components/hbs/comments*
      * **Gruppe**: *Benutzerdefiniert*
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Klicken Sie auf **[!UICONTROL OK]**


1. Erweitern Sie den soeben erstellten Knoten: `/apps/custom/components/comments`
1. Wählen Sie **[!UICONTROL Alle speichern]** aus
1. Klicken Sie mit der rechten Maustaste `comments.jsp`
1. Wählen Sie **[!UICONTROL Löschen]** aus
1. Wählen Sie **[!UICONTROL Alle speichern]** aus

![create-component](assets/create-component.png)

### Erstellen der Komponente für untergeordnete Kommentare {#create-the-child-comment-component}

Diese Anweisungen **Gruppe** nach `.hidden` da nur die übergeordnete Komponente in eine Seite einbezogen werden sollte.

Das Löschen der automatisch erstellten JSP-Datei erfolgt dadurch, dass stattdessen die standardmäßige HBS-Datei verwendet wird.

1. Navigieren Sie zum `/apps/custom/components/comments` Knoten
1. Rechtsklick auf den Knoten

   * Auswählen **[!UICONTROL Erstellen]** > **[!UICONTROL Komponente...]**

      * **Titel**: *comment*
      * **Titel**: *Alt-Kommentar*
      * **Beschreibung**: *Alternativer Kommentarstil*
      * **Supertyp**: *social/commons/components/hbs/comments/comment*
      * **Gruppe**: `*.hidden*`
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Klicken Sie auf **[!UICONTROL OK]**


1. Erweitern Sie den soeben erstellten Knoten: `/apps/custom/components/comments/comment`
1. Wählen Sie **[!UICONTROL Alle speichern]** aus
1. Klicken Sie mit der rechten Maustaste `comment.jsp`
1. Wählen Sie **[!UICONTROL Löschen]** aus
1. Wählen Sie **[!UICONTROL Alle speichern]** aus

![create-child-component](assets/create-child-component.png)

![create-component-crxde](assets/create-component-crxde.png)

### Kopieren und Ändern der standardmäßigen HBS-Skripte {#copy-and-modify-the-default-hbs-scripts}

Verwenden [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Kopieren `comments.hbs`

   * Von [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * nach [/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* Bearbeiten `comments.hbs` an:

   * Ändern Sie den Wert der `data-scf-component` Attribut (~line 20):

      * Von `social/commons/components/hbs/comments`
      * To `/apps/custom/components/comments`
   * Nehmen Sie die benutzerdefinierte Kommentarkomponente (~line 75) auf:

      * Ersetzen `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * mit `{{include this resourceType='/apps/custom/components/comments/comment'}}`


* Kopieren `comment.hbs`

   * Von [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * nach [/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* Bearbeiten `comment.hbs` an:

   * Ändern Sie den Wert des data-scf-component -Attributs (~ Zeile 19)

      * Von `social/commons/components/hbs/comments/comment`
      * nach `/apps/custom/components/comments/comment`

* Auswählen `/apps/custom` Knoten
* Wählen Sie **[!UICONTROL Alle speichern]** aus

## Erstellen eines Client-Bibliotheksordners {#create-a-client-library-folder}

Um zu vermeiden, dass diese Client-Bibliothek explizit einbezogen werden muss, kann der Kategoriewert für die clientlib des Standard-Kommentarsystems verwendet werden ( `cq.social.author.hbs.comments`), aber dann würde diese clientlib auch für alle Instanzen der Standardkomponente einbezogen.

Verwenden [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Auswählen `/apps/custom/components/comments` Knoten
* Auswählen **[!UICONTROL Knoten erstellen]**

   * **Name**: `clientlibs`
   * **Typ**: `cq:ClientLibraryFolder`
   * Hinzufügen zu **[!UICONTROL Eigenschaften]** tab:

      * **Name** `categories` **Typ** `String` **Wert** `cq.social.author.hbs.comments` `Multi`
      * **Name** `dependencies` **Typ** `String` **Wert** `cq.social.scf` `Multi`

* Wählen Sie **[!UICONTROL Alle speichern]** aus
* Mit `/apps/custom/components/comments/clientlib`Erstellen Sie als ausgewählten Knoten 3 Dateien:

   * **Name**: `css.txt`
   * **Name**: `js.txt`
   * **Name**: customkommentssystem.js

* Geben Sie &quot;customommentssystem.js&quot;als Inhalt von ein. `js.txt`
* Wählen Sie **[!UICONTROL Alle speichern]** aus

![comments-clientlibs](assets/comments-clientlibs.png)

## Registrieren des SCF-Modells und Anzeigen {#register-the-scf-model-view}

Beim Erweitern (Überschreiben) einer SCF-Komponente ist resourceType anders (Überlagern nutzt den relativen Suchmechanismus, der durchsucht wird) `/apps` before `/libs` sodass der resourceType gleich bleibt). Daher ist es erforderlich, JavaScript (in der Client-Bibliothek) zu schreiben, um das SCF-JS-Modell zu registrieren und für den benutzerdefinierten resourceType anzuzeigen.

Geben Sie folgenden Text als Inhalt von ein `customcommentsystem.js`:

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

* Wählen Sie **[!UICONTROL Alle speichern]** aus

## App veröffentlichen {#publish-the-app}

Um die erweiterte Komponente in der Veröffentlichungsumgebung zu erleben, muss die benutzerdefinierte Komponente repliziert werden.

Eine Möglichkeit hierfür ist:

* von der globalen Navigation aus,

   * Auswählen **[!UICONTROL Instrumente]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Replikation]**
   * Auswählen **[!UICONTROL Baum aktivieren]**
   * Setzen Sie `Start Path` auf `/apps/custom`
   * Deaktivieren **[!UICONTROL Nur geändert]**
   * Auswählen **[!UICONTROL Aktivieren]** button
