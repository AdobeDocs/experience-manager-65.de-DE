---
title: Grundlagen des Rich-Text-Editors
seo-title: Grundlagen des Rich-Text-Editors
description: Rich-Text-Editor-Funktion - Übersicht
seo-description: Rich-Text-Editor-Funktion - Übersicht
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

## Überblick {#overview}

Ein Rich Text Editor (RTE) bietet die Möglichkeit, Text mit Markup einzugeben.

Bei Communities-Komponenten wirkt sich dies ähnlich wie beim Rich-Text-Editor in der Authoring-Umgebung[ auf den in der Veröffentlichungs-Umgebung eingegebenen Text aus.](../../help/sites-authoring/rich-text-editor.md)

![Rich-Text-Editor](assets/rich-text-editor.png)

## Rich-Text-Editor {#enabling-rich-text-editor} aktivieren

Communities-Komponenten, die benutzergenerierte Inhalte (UGC) zulassen, können aktiviert werden, um RTE zuzulassen. Je nachdem, ob die Komponente einer Seite hinzugefügt oder in einer [Funktion](functions.md) enthalten ist, kann RTE standardmäßig aktiviert werden.

Wenn dies nicht aktiviert ist, geben Sie einfach den Bearbeitungsmodus [Autor](sites-console.md#authoring-site-content) ein, wählen Sie die zu bearbeitende Komponente aus und aktivieren Sie das Kontrollkästchen `Rich Text Editor`.

RTE ist für die folgenden Communities-Komponenten verfügbar:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Kommentare](comments.md)
* [Bibliothek](file-library.md)
* [Forum](forum.md)
* [Messaging](configure-messaging.md)
* [Frage und Antwort](working-with-qna.md)
* [Beurteilungen](reviews.md)

## Anpassung {#customization}

Die Anpassung des Rich-Text-Editors ist möglich, da die Implementierung auf [CKEditor](https://www.ckeditor.com/) basiert.

Die aktuelle Konfiguration für Communities-Komponenten befindet sich im Ordner `cq.social.  scf   clientlib` im Repository unter

`/libs/clientlibs/social/commons/scf/ckrte.js`

Das Ändern der clientlib cq.social.scf wird nicht empfohlen, da zukünftige Upgrades Änderungen überschreiben können.

### Beispielanpassung: Inline-Links {#example-customization-inline-links}

Aus Sicherheitsgründen sind die Hyperlink-Optionen nicht in den Rich-Text-Symbolen enthalten, die den Mitgliedern standardmäßig angezeigt werden. Die Fähigkeit zur Unschädlichkeit ist umfassend, wenn href in UGC erlaubt sind.

So fügen Sie der Symbolleiste Hyperlink-Optionen hinzu:

* hinzufügen einer Symbolleiste mit dem Namen &quot;`links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Wählen Sie **[!UICONTROL Alle speichern]**

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

