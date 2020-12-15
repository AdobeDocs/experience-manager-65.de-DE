---
title: hinzufügen auf Beispielseite
seo-title: hinzufügen auf Beispielseite
description: hinzufügen benutzerdefinierter Kommentare auf einer Seite
seo-description: hinzufügen benutzerdefinierter Kommentare auf einer Seite
uuid: ab258960-6de2-4943-80a7-e72904c0fd8e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a5040371-3bc2-43bc-a103-7175c4c6252d
docset: aem65
translation-type: tm+mt
source-git-commit: d38395b8f845686492a26329bb732a41f79c85c4
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# hinzufügen auf Beispielseite {#add-comment-to-sample-page}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsordner (/apps) vorhanden sind, ist es möglich, die erweiterte Komponente zu verwenden. Die Instanz des Kommentarsystems auf einer Website, die betroffen sein soll, muss ihren resourceType als benutzerdefiniertes Kommentarsystem festlegen und alle erforderlichen Client-Bibliotheken einschließen.

## Erforderliche Clientlibs {#identify-required-clientlibs} identifizieren

Die für den Stil und die Funktionsweise der Standardkommentare erforderlichen Client-Bibliotheken sind auch für erweiterte Kommentare erforderlich.

Das [Handbuch zu Community-Komponenten](/help/communities/components-guide.md) identifiziert die erforderlichen Client-Bibliotheken. Navigieren Sie zum Komponentenhandbuch und Ansicht der Kommentarkomponente, z. B.:

[https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Beachten Sie die drei Clientbibliotheken, die für die ordnungsgemäße Wiedergabe und Funktionsweise von Kommentaren erforderlich sind. Diese müssen eingeschlossen werden, wenn auf erweiterte Kommentare verwiesen wird, und die Client-Bibliothek [extended Comments](/help/communities/extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![comments-component1](assets/comments-component1.png)

### hinzufügen benutzerspezifischer Kommentare auf einer Seite {#add-custom-comments-to-a-page}

Da pro Seite nur ein Kommentarsystem erstellt werden kann, ist es einfacher, eine Beispielseite zu erstellen, wie im kurzen Lernprogramm [Beispielseite erstellen](/help/communities/create-sample-page.md) beschrieben.

Nach der Erstellung wechseln Sie in den Designmodus und stellen Sie die benutzerspezifische Komponentengruppe bereit, damit die Komponente `Alt Comments` der Seite hinzugefügt werden kann.

Damit der Kommentar korrekt angezeigt und funktioniert, müssen die Client-Bibliotheken für Kommentare zur clientlibslist für die Seite hinzugefügt werden (siehe [clientlibs für Communities-Komponenten](/help/communities/clientlibs.md)).

#### Kommentare clientlibs auf Beispielseite {#comments-clientlibs-on-sample-page}

![comments-clientlibs-crxde](assets/comments-clientlibs-crxde.png)

#### Autor: Alt-Kommentar auf Beispielseite {#author-alt-comment-on-sample-page}

![alt-comment](assets/alt-comment.png)

#### Autor: Beispiel-Seiten-Kommentarknoten-Knoten {#author-sample-page-comments-node}

Sie können resourceType in CRXDE überprüfen, indem Sie die Eigenschaften des Knotens comments für die Beispielseite unter `/content/sites/sample/en/jcr:content/content/primary/comments` anzeigen.

![verify-comment-crxde](assets/verify-comment-crxde.png)

#### Beispielseite {#publish-sample-page} veröffentlichen

Nachdem die benutzerdefinierte Komponente der Seite hinzugefügt wurde, muss auch [die Seite ](/help/communities/sites-console.md#publishing-the-site) (erneut) veröffentlicht werden.

#### Veröffentlichen: Alt-Kommentar auf Beispielseite {#publish-alt-comment-on-sample-page}

Nach dem Veröffentlichen der benutzerdefinierten Anwendung und der Beispielseite können Sie einen Kommentar eingeben. Bei der Anmeldung mit einem [demo-Benutzer](/help/communities/tutorials.md#demo-users) oder Admin ist es möglich, einen Kommentar zu posten.

Hier finden Sie aaron.mcdonald@mailinator.com zum Posten eines Kommentars:

![publish-alt-comment](assets/publish-alt-comment.png)

![publish-alt-comment1](assets/publish-alt-comment1.png)

Nun, da es so aussieht, als ob die erweiterte Komponente mit dem Standardaussehen korrekt funktioniert, ist es an der Zeit, das Erscheinungsbild zu ändern.