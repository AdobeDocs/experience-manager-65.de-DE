---
title: Komponenten-Sideloading
description: Das Sideloading von Communities-Komponenten ist nützlich, wenn eine Webseite als einfache Einzelseitenanwendung konzipiert ist, die die Anzeige dynamisch ändert, je nachdem, was der Besucher der Site auswählt.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 960e132c-b370-43d1-bd8f-e7d0ded7c0b3
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Komponenten-Sideloading {#component-sideloading}

## Überblick {#overview}

Das Sideloading von Communities-Komponenten ist nützlich, wenn eine Webseite als einfache Einzelseitenanwendung konzipiert ist, die die Anzeige dynamisch ändert, je nachdem, was der Besucher der Site ausgewählt hat.

Dies wird erreicht, wenn Communities-Komponenten nicht in der Seitenvorlage vorhanden sind, sondern nach der Auswahl eines Site-Besuchers dynamisch hinzugefügt werden.

Da das Social-Komponenten-Framework (SCF) über eine leichte Präsenz verfügt, werden nur SCF-Komponenten registriert, die zum Zeitpunkt des ersten Seitenladevorgangs vorhanden sind. Damit eine dynamisch hinzugefügte SCF-Komponente nach dem Laden der Seite registriert werden kann, muss SCF aufgerufen werden, um die Komponente zu &quot;sideload&quot;zu laden.

Wenn eine Seite zum Sideloaden von Communities-Komponenten entwickelt wurde, kann die gesamte Seite zwischengespeichert werden.

Die Schritte zum dynamischen Hinzufügen von SCF-Komponenten sind:

1. [Komponente zum DOM hinzufügen](#dynamically-add-component-to-dom)

1. [Laden Sie die Komponente ](#sideload-by-invoking-scf) mit einer der beiden Methoden um:

* [Dynamische Integration](#dynamic-inclusion)
   * Alle dynamisch hinzugefügten Komponenten verstärken
* [Dynamisches Laden](#dynamic-loading)
   * Eine bestimmte Komponente bei Bedarf hinzufügen

>[!NOTE]
>
>Das Sideloading von [nicht vorhandenen Ressourcen](scf.md#add-or-include-a-communities-component) wird nicht unterstützt.

## Dynamisches Hinzufügen einer Komponente zu DOM {#dynamically-add-component-to-dom}

Unabhängig davon, ob die Komponente dynamisch eingeschlossen oder dynamisch geladen wird, muss sie zuerst zum DOM hinzugefügt werden.

Beim Hinzufügen der SCF-Komponente ist das am häufigsten zu verwendende Tag das DIV-Tag. Es können jedoch auch andere Tags verwendet werden. Da SCF das DOM nur beim erstmaligen Laden der Seite überprüft, wird dieses Hinzufügen zum DOM nicht bemerkt, bis SCF explizit aufgerufen wird.

Welches Tag verwendet wird, mindestens muss das Element dem normalen SCF-Stammelementmuster entsprechen, indem es die beiden folgenden Attribute enthält:

* **data-component-id**

  Der effektive Pfad zur hinzugefügten Komponente.

* **data-scf-component**

  Der resourceType der Komponente.

Im Folgenden finden Sie ein Beispiel einer hinzugefügten Kommentarkomponente:

```xml
<div
    class="scf-commentsystem scf translation-commentsystem"
    data-component-id="<%= currentPage.getPath()%>/jcr:content/content-left/comments"
    data-scf-component="social/commons/components/hbs/comments"
>
</div>
```

## Sideload durch Aufrufen von SCF {#sideload-by-invoking-scf}

### Dynamische Integration {#dynamic-inclusion}

Die dynamische Einbindung verwendet eine Bootstrap-Anfrage, die dazu führt, dass SCF das DOM prüft und alle auf der Seite vorhandenen SCF-Komponenten bootet.

Um SCF-Komponenten jederzeit nach dem Laden der Seite zu initialisieren, lösen Sie einfach ein JQuery-Ereignis wie folgt aus:

`$(document).trigger(SCF.events.BOOTSTRAP_REQUEST);`

### Dynamisches Laden {#dynamic-loading}

Dynamisches Laden bietet Kontrolle über das Laden von SCF-Komponenten.

Anstelle des Bootstrapping aller im DOM gefundenen SCF-Komponenten ist es möglich, eine bestimmte SCF-Komponente anzugeben, die mit dieser JavaScript-Methode geladen werden soll:

`SCF.addComponent(document.getElementById(*someId*));`

Wobei `someId` der Wert des Attributs `data-component-id` ist.
