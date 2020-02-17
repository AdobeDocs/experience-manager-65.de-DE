---
title: Kommentar zur Beispielseite hinzufügen
seo-title: Kommentar zur Beispielseite hinzufügen
description: Hinzufügen benutzerdefinierter Kommentare zu einer Seite
seo-description: Hinzufügen benutzerdefinierter Kommentare zu einer Seite
uuid: ab258960-6de2-4943-80a7-e72904c0fd8e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a5040371-3bc2-43bc-a103-7175c4c6252d
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Kommentar zur Beispielseite hinzufügen {#add-comment-to-sample-page}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsordner (/apps) vorhanden sind, ist es möglich, die erweiterte Komponente zu verwenden. Die Instanz des Kommentarsystems auf einer Website, die betroffen sein soll, muss ihren resourceType als benutzerdefiniertes Kommentarsystem festlegen und alle erforderlichen Client-Bibliotheken einschließen.

## Erforderliche Clientlibs identifizieren {#identify-required-clientlibs}

Die für den Stil und die Funktionsweise der Standardkommentare erforderlichen Client-Bibliotheken sind auch für erweiterte Kommentare erforderlich.

Das Handbuch[ zu ](/help/communities/components-guide.md)Community-Komponenten identifiziert die erforderlichen Client-Bibliotheken. Navigieren Sie zum Komponentenhandbuch und sehen Sie sich die Komponente &quot;Kommentare&quot;an, z. B.:

[https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Beachten Sie die drei Clientbibliotheken, die für die ordnungsgemäße Wiedergabe und Funktionsweise von Kommentaren erforderlich sind. Diese müssen eingeschlossen werden, wenn auf die erweiterten Kommentare verwiesen wird, und die Client-Bibliothek[ der ](/help/communities/extend-create-components.md#create-a-client-library-folder)erweiterten Kommentare ( `apps.custom.comments`).

![chlimage_1-79](assets/chlimage_1-79.png)

### Hinzufügen benutzerdefinierter Kommentare zu einer Seite {#add-custom-comments-to-a-page}

Da pro Seite nur ein Kommentarsystem erstellt werden kann, ist es einfacher, eine Beispielseite zu erstellen, wie im kurzen Lernprogramm &quot;Beispielseite [erstellen&quot;beschrieben](/help/communities/create-sample-page.md) .

Nach der Erstellung wechseln Sie in den Designmodus und stellen Sie die benutzerspezifische Komponentengruppe bereit, damit die `Alt Comments` Komponente der Seite hinzugefügt werden kann.

Damit der Kommentar korrekt angezeigt und funktioniert, müssen die Client-Bibliotheken für Kommentare zur clientlibslist für die Seite hinzugefügt werden (siehe [Clientlibs für Communities-Komponenten](/help/communities/clientlibs.md)).

#### Kommentare zu Clientlibs auf der Beispielseite {#comments-clientlibs-on-sample-page}

![Kommentare zu Clientlibs auf der Beispielseite](assets/chlimage_1-80.png)

#### Autor: Alt-Kommentar auf Beispielseite {#author-alt-comment-on-sample-page}

![Alt-Kommentar auf Beispielseite](assets/chlimage_1-81.png)

#### Autor: Beispielknoten für Seitenkommentare {#author-sample-page-comments-node}

Sie können resourceType in CRXDE überprüfen, indem Sie die Eigenschaften des Knotens &quot;comments&quot;für die Beispielseite unter `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-82](assets/chlimage_1-82.png)

#### Beispielseite veröffentlichen {#publish-sample-page}

Nachdem die benutzerdefinierte Komponente der Seite hinzugefügt wurde, muss die Seite auch (erneut) [veröffentlicht werden](/help/communities/sites-console.md#publishing-the-site).

#### Veröffentlichen: Alt-Kommentar auf Beispielseite {#publish-alt-comment-on-sample-page}

Nach der Veröffentlichung der benutzerdefinierten Anwendung und der Beispielseite können Sie einen Kommentar eingeben. Bei der Anmeldung mit einem [Demo-Benutzer](/help/communities/tutorials.md#demo-users) oder Administrator ist es möglich, einen Kommentar zu posten.

Hier finden Sie aaron.mcdonald@mailinator.com zum Posten eines Kommentars:

![chlimage_1-83](assets/chlimage_1-83.png) ![chlimage_1-84](assets/chlimage_1-84.png)

Nun, da es so aussieht, als ob die erweiterte Komponente mit dem Standardaussehen korrekt funktioniert, ist es Zeit, das Erscheinungsbild zu ändern.