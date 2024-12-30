---
title: Kommentar zur Beispielseite hinzufügen
description: Erfahren Sie, wie eine Instanz des Kommentarsystems einer Website ihren resourceType als benutzerdefiniertes Kommentarsystem festlegen und alle erforderlichen Client-Bibliotheken einschließen muss.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: d4295a77-b931-4bc8-b3b4-eec42fdcfc56
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Kommentar zur Beispielseite hinzufügen  {#add-comment-to-sample-page}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem nun im Anwendungsverzeichnis (/apps) vorhanden sind, kann die erweiterte Komponente verwendet werden. Die Instanz des Kommentarsystems in einer betroffenen Website muss ihren resourceType als benutzerdefiniertes Kommentarsystem festlegen und alle erforderlichen Client-Bibliotheken einschließen.

## Erforderliche Clientlibs identifizieren {#identify-required-clientlibs}

Die Client-Bibliotheken, die für den Stil und die Funktionsweise der Standardkommentare erforderlich sind, sind auch für erweiterte Kommentare erforderlich.

Im [Community-Komponentenhandbuch](/help/communities/components-guide.md) werden die erforderlichen Client-Bibliotheken angegeben. Navigieren Sie zum Komponentenhandbuch und zeigen Sie die Komponente Kommentare an, z. B.:

[https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Beachten Sie die drei Client-Bibliotheken, die für Kommentare erforderlich sind, damit sie ordnungsgemäß gerendert werden und funktionieren. Diese müssen dort eingefügt werden, wo auf die erweiterten Kommentare verwiesen wird, und in der [Client-Bibliothek der erweiterten Kommentare](/help/communities/extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![comments-component1](assets/comments-component1.png)

### Hinzufügen benutzerdefinierter Kommentare zu einer Seite {#add-custom-comments-to-a-page}

Da pro Seite nur ein Kommentarsystem vorhanden sein kann, ist es einfacher, eine Beispielseite zu erstellen, wie im kurzen Tutorial [Erstellen einer Beispielseite](/help/communities/create-sample-page.md) beschrieben.

Wechseln Sie nach der Erstellung in den Designmodus und stellen Sie die benutzerdefinierte Komponentengruppe zur Verfügung, damit die `Alt Comments` Komponente zur Seite hinzugefügt werden kann.

Damit der Kommentar angezeigt wird und ordnungsgemäß funktioniert, müssen die Client-Bibliotheken für Kommentare zur clientlibs-Liste für die Seite hinzugefügt werden (siehe [Clientlibs für Communities-Komponenten](/help/communities/clientlibs.md)).

#### Kommentare zu Clientlibs auf Beispielseite {#comments-clientlibs-on-sample-page}

![comments-clientlibs-crxde](assets/comments-clientlibs-crxde.png)

#### Autor: ALT-Kommentar auf Beispielseite {#author-alt-comment-on-sample-page}

![Alt-Kommentar](assets/alt-comment.png)

#### Autor: Beispielseitenkommentarknoten {#author-sample-page-comments-node}

Sie können resourceType in CRXDE überprüfen, indem Sie die Eigenschaften des Kommentarknotens für die Beispielseite unter `/content/sites/sample/en/jcr:content/content/primary/comments` anzeigen.

![verify-comment-crxde](assets/verify-comment-crxde.png)

#### Publish-Beispielseite {#publish-sample-page}

Nachdem die benutzerdefinierte Komponente zur Seite hinzugefügt wurde, müssen Sie auch die Seite (erneut) [veröffentlichen](/help/communities/sites-console.md#publishing-the-site).

#### Publish: ALT-Kommentar auf Beispielseite {#publish-alt-comment-on-sample-page}

Nach dem Veröffentlichen sowohl des benutzerdefinierten Programms als auch der Beispielseite ist es möglich, einen Kommentar einzugeben. Wenn Sie angemeldet sind, entweder mit einem [Demo-Benutzer](/help/communities/tutorials.md#demo-users) oder Administrator, ist es möglich, einen Kommentar zu posten.

Hier ist aaron.mcdonald@mailinator.com, das einen Kommentar postet:

![publish-alt-comment](assets/publish-alt-comment.png)

![publish-alt-comment1](assets/publish-alt-comment1.png)

Jetzt, da die erweiterte Komponente mit dem standardmäßigen Erscheinungsbild korrekt funktioniert, ist es an der Zeit, das Erscheinungsbild zu ändern.
