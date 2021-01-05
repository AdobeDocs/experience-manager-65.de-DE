---
title: Komponenten-Sideloading
seo-title: Komponenten-Sideloading
description: Das Sideloading von Communities-Komponenten ist nützlich, wenn eine Webseite als einfache Einzelseitenanwendung entworfen wird, die dynamisch ändert, was angezeigt wird, je nachdem, was vom Site-Besucher ausgewählt wurde.
seo-description: Das Sideloading von Communities-Komponenten ist nützlich, wenn eine Webseite als einfache Einzelseitenanwendung entworfen wird, die dynamisch ändert, was angezeigt wird, je nachdem, was vom Site-Besucher ausgewählt wurde.
uuid: 8c9a5fde-26a3-4610-bc14-f8b665059015
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9cb5294-e5ab-445b-b7c2-ffeecda91c50
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# Komponenten-Sideloading {#component-sideloading}

## Überblick {#overview}

Das Sideloading von Communities-Komponenten ist nützlich, wenn eine Webseite als einfache Einzelseitenanwendung entworfen wird, die dynamisch ändert, was angezeigt wird, je nachdem, was vom Site-Besucher ausgewählt wird.

Dies geschieht, wenn Communities-Komponenten nicht in der Seitenvorlage vorhanden sind, sondern nach der Auswahl eines Site-Besuchers dynamisch hinzugefügt werden.

Da das Social-Komponenten-Framework (SCF) eine leichte Präsenz aufweist, werden nur SCF-Komponenten registriert, die zum Zeitpunkt des ersten Seitenladevorgangs vorhanden sind. Damit eine dynamisch hinzugefügte SCF-Komponente nach dem Laden der Seite registriert werden kann, muss SCF aufgerufen werden, um die Komponente zu &quot;sideload&quot;zu laden.

Wenn eine Seite zum Sideloading von Communities-Komponenten konzipiert ist, kann die gesamte Seite zwischengespeichert werden.

Die Schritte zum dynamischen Hinzufügen von SCF-Komponenten sind:

1. [hinzufügen der Komponente zum DOM](#dynamically-add-component-to-dom)

1. [Laden Sie die ](#sideload-by-invoking-scf) Komponente mit einer der beiden Methoden herunter:

* [Dynamische Inklusion](#dynamic-inclusion)
   * Alle dynamisch hinzugefügten Komponenten verstärken
* [Dynamisches Laden](#dynamic-loading)
   * hinzufügen einer bestimmten Komponente auf Abruf

>[!NOTE]
>
>Das Sideloading von [nicht vorhandenen Ressourcen](scf.md#add-or-include-a-communities-component) wird nicht unterstützt.

## Dynamische Hinzufügen der Komponente zu DOM {#dynamically-add-component-to-dom}

Unabhängig davon, ob die Komponente dynamisch eingeschlossen oder dynamisch geladen wird, muss sie zunächst dem DOM hinzugefügt werden.

Beim Hinzufügen der SCF-Komponente wird am häufigsten das DIV-Tag verwendet, es können aber auch andere Tags verwendet werden. Da SCF das DOM nur beim erstmaligen Laden der Seite prüft, wird diese Ergänzung zum DOM nicht bemerkt, bis SCF explizit aufgerufen wird.

Welches Tag verwendet wird, das Element muss mindestens dem normalen SCF-Stammelementmuster entsprechen, indem es die beiden folgenden Attribute enthält:

* **data-component-id**

   Der effektive Pfad zur hinzugefügten Komponente.

* **data-scf-component**

   Der resourceType der Komponente.

Im Folgenden finden Sie ein Beispiel für eine hinzugefügte Kommentarkomponente:

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

Die dynamische Integration verwendet eine Bootstrap-Anforderung, die dazu führt, dass SCF das DOM prüft und alle auf der Seite gefundenen SCF-Komponenten bootet.

Um SCF-Komponenten nach dem Laden der Seite zu initialisieren, starten Sie einfach ein JQuery-Ereignis wie folgt:

`$(document).trigger(SCF.events.BOOTSTRAP_REQUEST);`

### Dynamisches Laden {#dynamic-loading}

Dynamisches Laden bietet Kontrolle über das Laden von SCF-Komponenten.

Anstatt alle im DOM gefundenen SCF-Komponenten zu bootstrapping durchzuführen, können Sie eine bestimmte SCF-Komponente angeben, die mit dieser JavaScript-Methode geladen werden soll:

`SCF.addComponent(document.getElementById(*someId*));`

Dabei ist `someId` der Wert des Attributs `data-component-id`.
