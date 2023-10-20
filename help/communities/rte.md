---
title: Grundlagen zum Rich-Text-Editor
description: Erfahren Sie mehr über die Grundlagen und Funktionen eines Rich-Text-Editors, mit dem Sie Text mit Markup eingeben können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 821e32f4-da8d-4bbb-936a-0844b8a24cdd
source-git-commit: f03d0ab9d0f491441378e16e1590d33651f064b5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 4%

---

# Grundlagen zum Rich-Text-Editor {#rich-text-editor-essentials}

## Übersicht {#overview}

Mit einem Rich-Text-Editor (RTE) können Sie Text mit Markup eingeben.

Bei Communities-Komponenten ähneln sie der [Rich-Text-Editor in der Autorenumgebung](../../help/sites-authoring/rich-text-editor.md), wirkt sich dies auf den in der Veröffentlichungsumgebung eingegebenen Text aus.

![Rich-Text-Editor](assets/rich-text-editor.png)

## Rich-Text-Editor aktivieren {#enabling-rich-text-editor}

Communities-Komponenten, die benutzergenerierte Inhalte (UGC) zulassen, können aktiviert werden, um den RTE zuzulassen. Wenn die Komponente zu einer Seite hinzugefügt oder in einer [function](functions.md), kann der RTE standardmäßig aktiviert sein oder nicht.

Wenn diese Option nicht aktiviert ist, geben Sie einfach ein [Bearbeitungsmodus des Autors](sites-console.md#authoring-site-content), wählen Sie die zu bearbeitende Komponente aus und wählen Sie die `Rich Text Editor` aktivieren.

RTE ist für die folgenden Communities-Komponenten verfügbar:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Kommentare](comments.md)
* [FileLibrary](file-library.md)
* [Forum](forum.md)
* [Messaging](configure-messaging.md)
* [Fragen und Antworten](working-with-qna.md)
* [Bewertungen](reviews.md)

## Anpassung {#customization}

Die Anpassung des Rich-Text-Editors ist möglich, da die Implementierung auf [CKEditor](https://ckeditor.com/).

Die aktuelle Konfiguration für Communities-Komponenten befindet sich im `cq.social.  scf   clientlib`im Repository unter

`/libs/clientlibs/social/commons/scf/ckrte.js`

Eine Änderung der clientlib cq.social.scf wird nicht empfohlen, da zukünftige Upgrades Änderungen überschreiben können.

### Beispielanpassung: Inline-Links {#example-customization-inline-links}

Aus Sicherheitsgründen sind die Hyperlink-Optionen nicht im Satz von Rich-Text-Symbolen enthalten, die Mitgliedern standardmäßig angezeigt werden. Die Fähigkeit, Unruhe zu stiften, ist groß, wenn href in UGC erlaubt sind.

So fügen Sie die Hyperlink-Optionen zur Symbolleiste hinzu:

* Symbolleiste mit dem Namen `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Klicken Sie auf **[!UICONTROL Alle speichern]**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links',
           items: [ 'Link','Unlink','Anchor' ]
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```
