---
title: Komponenten-Seitenladevorgang
description: Das Laden von Communities-Komponenten ist nützlich, wenn eine Web-Seite als einfache Einzelseiten-App entworfen wurde, die die angezeigten Inhalte dynamisch ändert, je nachdem, was der Site-Besucher ausgewählt hat
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

# Komponenten-Seitenladevorgang {#component-sideloading}

## Überblick {#overview}

Das Laden von Communities-Komponenten ist nützlich, wenn eine Web-Seite als einfache Einzelseiten-App entworfen wurde, die die angezeigten Inhalte dynamisch ändert, je nachdem, was der Site-Besucher ausgewählt hat.

Dies wird erreicht, wenn in der Seitenvorlage keine Communities-Komponenten vorhanden sind, sondern nach der Auswahl durch einen Site-Besucher dynamisch hinzugefügt werden.

Da das Social Component Framework (SCF) nur sehr leicht vorhanden ist, werden nur SCF-Komponenten registriert, die zum Zeitpunkt des ersten Seitenladevorgangs vorhanden sind. Damit eine dynamisch hinzugefügte SCF-Komponente nach dem Laden der Seite registriert werden kann, muss SCF aufgerufen werden, um die Komponente zu „seitenladen“.

Wenn eine Seite so konzipiert ist, dass Communities-Komponenten seitlich geladen werden, ist es möglich, die gesamte Seite zwischenzuspeichern.

Die Schritte zum dynamischen Hinzufügen von SCF-Komponenten sind:

1. [Hinzufügen der Komponente zum DOM](#dynamically-add-component-to-dom)

1. [Laden Sie die Komponente ](#sideload-by-invoking-scf) einer von zwei Methoden:

* [Dynamische Einbindung](#dynamic-inclusion)
   * Bootstrapping aller dynamisch hinzugefügten Komponenten
* [Dynamisches Laden](#dynamic-loading)
   * Hinzufügen einer bestimmten Komponente bei Bedarf

>[!NOTE]
>
>Das Sideloading [nicht vorhandenen Ressourcen](scf.md#add-or-include-a-communities-component) wird nicht unterstützt.

## Dynamisches Hinzufügen einer Komponente zum DOM {#dynamically-add-component-to-dom}

Unabhängig davon, ob die Komponente dynamisch eingeschlossen oder dynamisch geladen wird, muss sie zuerst dem DOM hinzugefügt werden.

Beim Hinzufügen der SCF-Komponente wird meist das DIV-Tag verwendet. Es können aber auch andere Tags verwendet werden. Da SCF das DOM nur beim ersten Laden der Seite untersucht, wird dieses Hinzufügen zum DOM unbemerkt bleiben, bis SCF explizit aufgerufen wird.

Unabhängig davon, welches Tag verwendet wird, muss das Element mindestens dem normalen SCF-Stammelementmuster entsprechen, indem es diese beiden Attribute enthält:

* **data-component-id**

  Der effektive Pfad zur hinzugefügten Komponente.

* **data-scf-component**

  Der resourceType der Komponente.

Im Folgenden finden Sie ein Beispiel für eine hinzugefügte Komponente „Kommentare“:

```xml
<div
    class="scf-commentsystem scf translation-commentsystem"
    data-component-id="<%= currentPage.getPath()%>/jcr:content/content-left/comments"
    data-scf-component="social/commons/components/hbs/comments"
>
</div>
```

## Seitenladen durch Aufrufen von SCF {#sideload-by-invoking-scf}

### Dynamische Einbindung {#dynamic-inclusion}

Die dynamische Einbindung verwendet eine Bootstrap-Anfrage, die dazu führt, dass SCF das DOM untersucht und alle auf der Seite gefundenen SCF-Komponenten mit Bootstrapping durchführt.

Um SCF-Komponenten jederzeit nach dem Laden der Seite zu initialisieren, lösen Sie einfach ein JQuery-Ereignis wie das folgende aus:

`$(document).trigger(SCF.events.BOOTSTRAP_REQUEST);`

### Dynamisches Laden {#dynamic-loading}

Dynamisches Laden bietet Kontrolle über das Laden von SCF-Komponenten.

Anstatt alle im DOM gefundenen SCF-Komponenten per Bootstrapping zu aktivieren, können Sie mit dieser JavaScript-Methode eine bestimmte SCF-Komponente angeben, die geladen werden soll:

`SCF.addComponent(document.getElementById(*someId*));`

Dabei ist `someId` der Wert des `data-component-id`.
