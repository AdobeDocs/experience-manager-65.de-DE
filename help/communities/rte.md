---
title: Grundlagen des Rich-Text-Editors
seo-title: Grundlagen des Rich-Text-Editors
description: Rich-Text-Editor-Funktion - Übersicht
seo-description: Rich text Editor feature overview
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
translation-type: tm+mt
source-git-commit: 4b6311cbfe11a61b74f68bf5a25ad1f5faef5358
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 3%

---


# Rich Text Editor Essentials {#rich-text-editor-essentials}

## Übersicht {#overview}

Ein Rich Text Editor (RTE) bietet die Möglichkeit, Text mit Markup einzugeben.

Bei Communities-Komponenten wirkt sich dies ähnlich wie der [Rich-Text-Editor in der Autorendatei](../../help/sites-authoring/rich-text-editor.md)auf den in der Umgebung &quot;Veröffentlichen&quot;eingegebenen Text aus.

![rich-text-editor](assets/rich-text-editor.png)

## Rich-Text-Editor aktivieren {#enabling-rich-text-editor}

Communities components that allow user generated content (UGC) can be enabled to allow RTE. Depending on whether the component was added to a page or included within a [function](functions.md), RTE may or may not be enabled by default.

If not enabled, simply enter [author edit mode](sites-console.md#authoring-site-content), select the component for edit, and select the `Rich Text Editor` checkbox.

RTE ist für die folgenden Communities-Komponenten verfügbar:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Kommentare](comments.md)
* [Filelibrary](file-library.md)
* [Forum](forum.md)
* [Messaging](configure-messaging.md)
* [Frage und Antwort](working-with-qna.md)
* [Beurteilungen](reviews.md)

## Anpassung {#customization}

Die Anpassung des Rich-Text-Editors ist möglich, da die Implementierung auf [CKEditor](https://www.ckeditor.com/)basiert.

Die aktuelle Konfiguration für Communities-Komponenten befindet sich im `cq.social.  scf   clientlib`Repository unter

`/libs/clientlibs/social/commons/scf/ckrte.js`

Das Ändern der clientlib cq.social.scf wird nicht empfohlen, da zukünftige Upgrades Änderungen überschreiben können.

### Beispielanpassung: Inline-Links {#example-customization-inline-links}

Due to security concerns, the hyperlink options are not included in the set of rich text icons presented to members by default. Die Fähigkeit zur Unschädlichkeit ist umfassend, wenn href in UGC erlaubt sind.

So fügen Sie der Symbolleiste Hyperlink-Optionen hinzu:

* hinzufügen einer Werkzeugleiste mit dem Namen `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Select **[!UICONTROL Save All]**

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

