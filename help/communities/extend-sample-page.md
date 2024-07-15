---
title: Hinzufügen von Kommentaren zur Beispielseite
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

# Hinzufügen von Kommentaren zur Beispielseite  {#add-comment-to-sample-page}

Nachdem sich die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) befinden, kann die erweiterte Komponente verwendet werden. Die Instanz des Kommentarsystems auf einer Website, auf die sich die Auswirkungen auswirken sollen, muss ihren resourceType als benutzerdefiniertes Kommentarsystem festlegen und alle erforderlichen Client-Bibliotheken einschließen.

## Erforderliche Clientlibs identifizieren {#identify-required-clientlibs}

Die Client-Bibliotheken, die für den Stil und die Funktionsweise der Standardkommentare erforderlich sind, sind auch für erweiterte Kommentare erforderlich.

Im [Community Components Guide](/help/communities/components-guide.md) werden die erforderlichen Client-Bibliotheken identifiziert. Navigieren Sie zum Komponentenleitfaden und zeigen Sie die Komponente Kommentare an, z. B.:

[https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Beachten Sie die drei Client-Bibliotheken, die erforderlich sind, damit Kommentare gerendert und ordnungsgemäß funktioniert. Diese müssen enthalten sein, wenn auf die erweiterten Kommentare und die Client-Bibliothek ](/help/communities/extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`) der [erweiterten Kommentare verwiesen wird.

![comments-component1](assets/comments-component1.png)

### Hinzufügen benutzerdefinierter Kommentare zu einer Seite {#add-custom-comments-to-a-page}

Da pro Seite nur ein Kommentarsystem erstellt werden kann, ist es einfacher, eine Beispielseite zu erstellen, wie im kurzen Tutorial [Erstellen einer Beispielseite](/help/communities/create-sample-page.md) beschrieben.

Wechseln Sie nach der Erstellung in den Designmodus und stellen Sie die benutzerdefinierte Komponentengruppe bereit, damit die Komponente `Alt Comments` zur Seite hinzugefügt werden kann.

Damit der Kommentar angezeigt wird und ordnungsgemäß funktioniert, müssen die Client-Bibliotheken für Kommentare der Clientlibsliste für die Seite hinzugefügt werden (siehe [Clientlibs für Communities-Komponenten](/help/communities/clientlibs.md)).

#### Kommentare zu Clientlibs auf Beispielseite {#comments-clientlibs-on-sample-page}

![comments-clientlibs-crxde](assets/comments-clientlibs-crxde.png)

#### Autor: Alt-Kommentar auf Beispielseite {#author-alt-comment-on-sample-page}

![alt-comment](assets/alt-comment.png)

#### Autor: Knoten für Beispielseitenkommentare {#author-sample-page-comments-node}

Sie können den resourceType in CRXDE überprüfen, indem Sie die Eigenschaften des Kommentarknotens für die Beispielseite unter `/content/sites/sample/en/jcr:content/content/primary/comments` anzeigen.

![verify-comment-crxde](assets/verify-comment-crxde.png)

#### Publish-Beispielseite {#publish-sample-page}

Nachdem die benutzerdefinierte Komponente der Seite hinzugefügt wurde, müssen Sie die Seite auch (erneut) [veröffentlichen](/help/communities/sites-console.md#publishing-the-site).

#### Publish: Alt-Kommentar auf Beispielseite {#publish-alt-comment-on-sample-page}

Nach der Veröffentlichung des benutzerdefinierten Programms und der Beispielseite können Sie einen Kommentar eingeben. Wenn Sie angemeldet sind, entweder mit einem [Demobenutzer](/help/communities/tutorials.md#demo-users) oder Administrator, können Sie einen Kommentar posten.

Hier aaron.mcdonald@mailinator.com posten Sie einen Kommentar:

![publish-alt-comment](assets/publish-alt-comment.png)

![publish-alt-comment1](assets/publish-alt-comment1.png)

Nachdem sich herausstellt, dass die erweiterte Komponente ordnungsgemäß mit dem standardmäßigen Erscheinungsbild funktioniert, ist es an der Zeit, das Erscheinungsbild zu ändern.
