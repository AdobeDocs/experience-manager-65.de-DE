---
title: Erstellen der Komponenten
seo-title: Erstellen der Komponenten
description: Erstellen der Komponente Kommentare
seo-description: Erstellen der Komponente Kommentare
uuid: ea6e00d4-1db7-40ef-ae49-9ec55df58adf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 83c4f18a-d7d6-4090-88c7-41a9075153b5
exl-id: 2e02db9f-294d-4d4a-92da-3ab1d38416ab
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 7%

---

# Erstellen der Komponenten {#create-the-components}

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

In diesen Anweisungen wird ein anderer **Group**-Wert als `.hidden` angegeben, sodass die Komponente über den Komponenten-Browser (Sidekick) verfügbar gemacht werden kann.

Das Löschen der automatisch erstellten JSP-Datei erfolgt dadurch, dass stattdessen die standardmäßige HBS-Datei verwendet wird.

1. Navigieren Sie zu **CRXDE|Lite** ([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)).

1. Erstellen Sie einen Speicherort für benutzerdefinierte Anwendungen:

   * Wählen Sie den Knoten `/apps` aus.

      * **Erstellen von** Ordnern mit  **[!UICONTROL benutzerdefiniertem Namen]**
   * Wählen Sie den Knoten `/apps/custom` aus.

      * **Erstellen** von ordnerspezifischen  **[!UICONTROL Komponenten]**


1. Wählen Sie den Knoten `/apps/custom/components` aus.

   * **[!UICONTROL Erstellen > Komponente..]**

      * **Titel**:  *Kommentare*
      * **Titel**:  *Alt-Kommentare*
      * **Beschreibung**:  *Alternativer Kommentar-Stil*
      * **Supertyp**:  *social/commons/components/hbs/comments*
      * **Gruppe**:  *Benutzerdefiniert*
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL OK]** aus


1. Erweitern Sie den soeben erstellten Knoten: `/apps/custom/components/comments`
1. Wählen Sie **[!UICONTROL Alle speichern]**
1. Klicken Sie mit der rechten Maustaste `comments.jsp`
1. Wählen Sie **[!UICONTROL Löschen]** aus
1. Wählen Sie **[!UICONTROL Alle speichern]**

![create-component](assets/create-component.png)

### Erstellen der untergeordneten Kommentarkomponente {#create-the-child-comment-component}

In diesen Anweisungen wird **Gruppe** auf `.hidden` gesetzt, da nur die übergeordnete Komponente in eine Seite eingefügt werden sollte.

Das Löschen der automatisch erstellten JSP-Datei erfolgt dadurch, dass stattdessen die standardmäßige HBS-Datei verwendet wird.

1. Navigieren Sie zum Knoten `/apps/custom/components/comments` .
1. Rechtsklick auf den Knoten

   * Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Komponente...]**

      * **Titel**:  *comment*
      * **Titel**:  *Alt-Kommentar*
      * **Beschreibung**:  *Alternativer Kommentarstil*
      * **Supertyp**:  *social/commons/components/hbs/comments/comment*
      * **Gruppe**: `*.hidden*`
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL Weiter]** aus
   * Wählen Sie **[!UICONTROL OK]** aus


1. Erweitern Sie den soeben erstellten Knoten: `/apps/custom/components/comments/comment`
1. Wählen Sie **[!UICONTROL Alle speichern]**
1. Klicken Sie mit der rechten Maustaste `comment.jsp`
1. Wählen Sie **[!UICONTROL Löschen]** aus
1. Wählen Sie **[!UICONTROL Alle speichern]**

![create-child-component](assets/create-child-component.png)

![create-component-crxde](assets/create-component-crxde.png)

### Kopieren und Ändern der standardmäßigen HBS-Skripte {#copy-and-modify-the-default-hbs-scripts}

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Kopieren `comments.hbs`

   * Von [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * Nach [/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* Bearbeiten Sie `comments.hbs`, bis:

   * Ändern Sie den Wert des Attributs `data-scf-component` (~line 20):

      * Von `social/commons/components/hbs/comments`
      * An `/apps/custom/components/comments`
   * Nehmen Sie die benutzerdefinierte Kommentarkomponente (~line 75) auf:

      * Ersetzen `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * mit `{{include this resourceType='/apps/custom/components/comments/comment'}}`


* Kopieren `comment.hbs`

   * Von [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * Nach [/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* Bearbeiten Sie `comment.hbs`, bis:

   * Ändern Sie den Wert des data-scf-component -Attributs (~ Zeile 19)

      * Von `social/commons/components/hbs/comments/comment`
      * An `/apps/custom/components/comments/comment`

* Knoten `/apps/custom` auswählen
* Wählen Sie **[!UICONTROL Alle speichern]**

## Erstellen eines Client-Bibliotheksordners {#create-a-client-library-folder}

Um zu vermeiden, dass diese Client-Bibliothek explizit einbezogen werden muss, könnte der Kategoriewert für die clientlib des Standard-Kommentarsystems verwendet werden ( `cq.social.author.hbs.comments`), aber dann würde diese clientlib auch für alle Instanzen der Standardkomponente enthalten sein.

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Knoten `/apps/custom/components/comments` auswählen
* Wählen Sie **[!UICONTROL Knoten erstellen]**

   * **Name**: `clientlibs`
   * **Typ**: `cq:ClientLibraryFolder`
   * Fügen Sie der Registerkarte **[!UICONTROL Eigenschaften]** hinzu:

      * **** `categories` **** `String` **NameTypeValue** `cq.social.author.hbs.comments` `Multi`
      * **** `dependencies` **** `String` **NameTypeValue** `cq.social.scf` `Multi`

* Wählen Sie **[!UICONTROL Alle speichern]**
* Erstellen Sie mit dem ausgewählten Knoten `/apps/custom/components/comments/clientlib`s drei Dateien:

   * **Name**:  `css.txt`
   * **Name**:  `js.txt`
   * **Name**: customkommentssystem.js

* Geben Sie &quot;customkommentssystem.js&quot;als Inhalt von `js.txt` ein.
* Wählen Sie **[!UICONTROL Alle speichern]**

![comments-clientlibs](assets/comments-clientlibs.png)

## Registrieren Sie das SCF-Modell und zeigen Sie {#register-the-scf-model-view}

Beim Erweitern (Überschreiben) einer SCF-Komponente ist der resourceType anders (das Überlagern nutzt den relativen Suchmechanismus, der `/apps` vor `/libs` durchsucht, sodass der resourceType gleich bleibt). Daher ist es erforderlich, JavaScript (in der Client-Bibliothek) zu schreiben, um das SCF-JS-Modell zu registrieren und für den benutzerdefinierten resourceType anzuzeigen.

Geben Sie folgenden Text als Inhalt von `customcommentsystem.js` ein:

### customommentssystem.js {#customcommentsystem-js}

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

## Veröffentlichen der App {#publish-the-app}

Um die erweiterte Komponente in der Veröffentlichungsumgebung zu erleben, muss die benutzerdefinierte Komponente repliziert werden.

Eine Möglichkeit hierfür ist:

* von der globalen Navigation aus,

   * Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**
   * Wählen Sie **[!UICONTROL Baum aktivieren]**
   * Setzen Sie `Start Path` auf `/apps/custom`
   * Deaktivieren Sie **[!UICONTROL Nur geändert]**
   * Wählen Sie die Schaltfläche **[!UICONTROL Aktivieren]** aus.
