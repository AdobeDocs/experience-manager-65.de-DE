---
title: Grundlagen zum Rich-Text-Editor
description: Lernen Sie die Grundlagen und Funktionen eines Rich-Text-Editors kennen, mit dem Sie Text mit Markup eingeben können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 821e32f4-da8d-4bbb-936a-0844b8a24cdd
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# Grundlagen zum Rich-Text-Editor {#rich-text-editor-essentials}

## Überblick {#overview}

Mit einem Rich-Text-Editor (RTE) können Sie Text mit Markup eingeben.

Bei Communities-Komponenten wirkt sich dies ähnlich wie [Rich-Text-Editor in der Autorenumgebung](../../help/sites-authoring/rich-text-editor.md) auf Text aus, der in der Veröffentlichungsumgebung eingegeben wird.

![rich-text-editor](assets/rich-text-editor.png)

## Aktivieren des Rich-Text-Editors {#enabling-rich-text-editor}

Communities-Komponenten, die benutzergenerierte Inhalte (User Generated Content, UGC) zulassen, können für den RTE aktiviert werden. Wenn die Komponente zu einer Seite hinzugefügt oder in eine [Funktion](functions.md) eingefügt wurde, kann RTE standardmäßig aktiviert sein oder nicht.

Wenn diese Option nicht aktiviert ist, [&#x200B; Sie einfach den &#x200B;](sites-console.md#authoring-site-content) „author edit mode“ ein, wählen Sie die Komponente aus, die bearbeitet werden soll, und aktivieren Sie das Kontrollkästchen `Rich Text Editor` .

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

Der Rich-Text-Editor kann angepasst werden, da die Implementierung auf [CKEditor](https://ckeditor.com/) basiert.

Die aktuelle Konfiguration für Communities-Komponenten befindet sich im `cq.social.  scf   clientlib`, im Repository unter .

`/libs/clientlibs/social/commons/scf/ckrte.js`

Das Ändern der Client-Bibliothek „cq.social.scf“ wird nicht empfohlen, da zukünftige Upgrades alle Änderungen überschreiben können.

### Beispielanpassung: Inline-Links {#example-customization-inline-links}

Aus Sicherheitsgründen sind die Hyperlink-Optionen nicht in dem Satz von Rich-Text-Symbolen enthalten, der Mitgliedern standardmäßig angezeigt wird. Die Fähigkeit, Unfug zu stiften, ist groß, wenn in benutzergenerierten Inhalten erlaubt sind.

So fügen Sie die Hyperlink-Optionen zur Symbolleiste hinzu:

* Hinzufügen einer Symbolleiste mit dem Namen &quot;`links`&quot;
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
