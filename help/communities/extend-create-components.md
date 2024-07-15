---
title: Erstellen der Komponenten
description: Erfahren Sie, wie Sie Komponenten mithilfe des Kommentarsystems erweitern, das aus Kommentar- und Kommentarkomponenten besteht.
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

Das Beispiel der Erweiterung von Komponenten verwendet das Kommentarsystem, das aus zwei Komponenten besteht.

* Kommentare - Das umfassende Kommentarsystem, bei dem es sich um die auf einer Seite platzierte Komponente handelt.
* Kommentar - Die Komponente, die eine Instanz eines veröffentlichten Kommentars erfasst.

Beide Komponenten müssen eingerichtet werden, insbesondere bei der Anpassung des Erscheinungsbilds eines veröffentlichten Kommentars.

>[!NOTE]
>
>Pro Site-Seite ist nur ein Kommentarsystem zulässig.
>
>Viele Communities-Funktionen enthalten bereits ein Kommentarsystem, dessen resourceType so geändert werden kann, dass er auf das erweiterte Kommentarsystem verweist.

## Erstellen der Kommentarkomponente {#create-the-comments-component}

In diesen Anweisungen wird ein anderer **Group** -Wert als `.hidden` angegeben, damit die Komponente über den Komponenten-Browser (Sidekick) verfügbar gemacht werden kann.

Das Löschen der automatisch erstellten JSP-Datei erfolgt dadurch, dass stattdessen die standardmäßige HBS-Datei verwendet wird.

1. Navigieren Sie zu **CRXDE|Lite** ([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)).

1. Erstellen Sie einen Speicherort für benutzerdefinierte Anwendungen:

   * Wählen Sie den Knoten `/apps` aus

      * **Ordner** mit dem Namen **[!UICONTROL custom]** erstellen

   * Wählen Sie den Knoten `/apps/custom` aus

      * **Ordner** mit dem Namen **[!UICONTROL Komponenten]** erstellen

1. Wählen Sie den Knoten `/apps/custom/components` aus

   * **[!UICONTROL Erstellen > Komponente..]**

      * **Beschriftung**: *Kommentare*
      * **Titel**: *ALT-Kommentare*
      * **Beschreibung**: *Alternativer Kommentar-Stil*
      * **Supertyp**: *social/commons/components/hbs/comments*
      * **Gruppe**: *Benutzerdefiniert*

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

### Erstellen der Komponente für untergeordnete Kommentare {#create-the-child-comment-component}

In diesen Anweisungen wird **Gruppe** auf `.hidden` gesetzt, da nur die übergeordnete Komponente in eine Seite einbezogen werden sollte.

Das Löschen der automatisch erstellten JSP-Datei erfolgt dadurch, dass stattdessen die standardmäßige HBS-Datei verwendet wird.

1. Navigieren Sie zum Knoten `/apps/custom/components/comments` .
1. Rechtsklick auf den Knoten

   * Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Komponente...]** aus.

      * **Beschriftung**: *Kommentar*
      * **Titel**: *ALT-Kommentar*
      * **Beschreibung**: *Alternativer Kommentarstil*
      * **Super Type**: *social/commons/components/hbs/comments/comment*
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

### Kopieren und Ändern der standardmäßigen HBS-Skripte {#copy-and-modify-the-default-hbs-scripts}

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Kopieren `comments.hbs`

   * Von [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * Nach [/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* Bearbeiten Sie `comments.hbs` zu:

   * Ändern Sie den Wert des Attributs `data-scf-component` (~line 20):

      * Von `social/commons/components/hbs/comments`
      * Bis `/apps/custom/components/comments`

   * Nehmen Sie die benutzerdefinierte Kommentarkomponente (~line 75) auf:

      * Ersetzen Sie `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * Mit `{{include this resourceType='/apps/custom/components/comments/comment'}}`

* Kopieren `comment.hbs`

   * Von [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * Nach [/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* Bearbeiten Sie `comment.hbs` zu:

   * Ändern Sie den Wert des data-scf-component -Attributs (~ Zeile 19)

      * Von `social/commons/components/hbs/comments/comment`
      * Bis `/apps/custom/components/comments/comment`

* Knoten `/apps/custom` auswählen
* Wählen Sie **[!UICONTROL Alle speichern]**

## Erstellen eines Client-Bibliotheksordners {#create-a-client-library-folder}

Um zu vermeiden, dass diese Client-Bibliothek einbezogen werden muss, kann der Kategoriewert für die clientlib des standardmäßigen Kommentarsystems verwendet werden ( `cq.social.author.hbs.comments`). Diese clientlib muss dann jedoch auch für alle Instanzen der Standardkomponente eingeschlossen werden.

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Knoten `/apps/custom/components/comments` auswählen
* Wählen Sie **[!UICONTROL Knoten erstellen]** aus

   * **Name**: `clientlibs`
   * **Typ**: `cq:ClientLibraryFolder`
   * Fügen Sie der Registerkarte **[!UICONTROL Eigenschaften]** hinzu:

      * **Name** `categories` **Typ** `String` **Wert** `cq.social.author.hbs.comments` `Multi`
      * **Name** `dependencies` **Typ** `String` **Wert** `cq.social.scf` `Multi`

* Wählen Sie **[!UICONTROL Alle speichern]**
* Erstellen Sie bei ausgewähltem Knoten `/apps/custom/components/comments/clientlib`drei Dateien:

   * **Name**: `css.txt`
   * **Name**: `js.txt`
   * **Name**: customkommentssystem.js

* Geben Sie &quot;customkommentssystem.js&quot;als Inhalt von `js.txt` ein.
* Wählen Sie **[!UICONTROL Alle speichern]**

![comments-clientlibs](assets/comments-clientlibs.png)

## Registrieren des SCF-Modells und Anzeigen {#register-the-scf-model-view}

Beim Erweitern (Überschreiben) einer SCF-Komponente ist der resourceType anders (Überlagern verwendet den relativen Suchmechanismus, der durch `/apps` vor `/libs` sucht, sodass der resourceType gleich bleibt). Daher ist es erforderlich, JavaScript (in der Client-Bibliothek) zu schreiben, um das SCF-JS-Modell zu registrieren und für den benutzerdefinierten resourceType anzuzeigen.

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

## Publish the App {#publish-the-app}

Um die erweiterte Komponente in der Veröffentlichungsumgebung zu erleben, muss die benutzerdefinierte Komponente repliziert werden.

Eine Möglichkeit hierfür ist:

* von der globalen Navigation aus,

   * Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]** aus.
   * Wählen Sie **[!UICONTROL Baum aktivieren]**
   * `Start Path` wird auf `/apps/custom` gesetzt
   * Deaktivieren Sie **[!UICONTROL Nur geändert]** .
   * Schaltfläche **[!UICONTROL Aktivieren]** auswählen
