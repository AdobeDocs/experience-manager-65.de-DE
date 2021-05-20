---
title: Hinzufügen von Kommentaren zur Beispielseite
seo-title: Hinzufügen von Kommentaren zur Beispielseite
description: Hinzufügen benutzerdefinierter Kommentare zu einer Seite
seo-description: Hinzufügen benutzerdefinierter Kommentare zu einer Seite
uuid: ab258960-6de2-4943-80a7-e72904c0fd8e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a5040371-3bc2-43bc-a103-7175c4c6252d
docset: aem65
exl-id: d4295a77-b931-4bc8-b3b4-eec42fdcfc56
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Kommentar zur Beispielseite hinzufügen {#add-comment-to-sample-page}

Nachdem sich die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) befinden, kann die erweiterte Komponente verwendet werden. Die Instanz des Kommentarsystems auf einer Website, auf die sich die Auswirkungen auswirken sollen, muss ihren resourceType als benutzerdefiniertes Kommentarsystem festlegen und alle erforderlichen Client-Bibliotheken einschließen.

## Erforderliche Clientlibs identifizieren {#identify-required-clientlibs}

Die Client-Bibliotheken, die für den Stil und die Funktionsweise der Standardkommentare erforderlich sind, sind auch für erweiterte Kommentare erforderlich.

Im [Community Components Guide](/help/communities/components-guide.md) werden die erforderlichen Client-Bibliotheken identifiziert. Navigieren Sie zum Komponentenleitfaden und zeigen Sie die Komponente Kommentare an, z. B.:

[https://localhost:4502/content/community-components/en/comments.html](https://localhost:4502/content/community-components/en/comments.html)

Beachten Sie die drei Client-Bibliotheken, die erforderlich sind, damit Kommentare gerendert und ordnungsgemäß funktioniert. Diese müssen dort eingeschlossen sein, wo auf die erweiterten Kommentare verwiesen wird, sowie in der Client-Bibliothek [erweiterte Kommentare](/help/communities/extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![comments-component1](assets/comments-component1.png)

### Hinzufügen benutzerdefinierter Kommentare zu einer Seite {#add-custom-comments-to-a-page}

Da es pro Seite nur ein Kommentarsystem geben kann, ist es einfacher, eine Beispielseite zu erstellen, wie im kurzen Tutorial [Erstellen einer Beispielseite](/help/communities/create-sample-page.md) beschrieben.

Wechseln Sie nach der Erstellung in den Designmodus und stellen Sie die benutzerdefinierte Komponentengruppe bereit, damit die Komponente `Alt Comments` zur Seite hinzugefügt werden kann.

Damit der Kommentar angezeigt und ordnungsgemäß funktioniert, müssen die Client-Bibliotheken für Kommentare zur Clientlibsliste für die Seite hinzugefügt werden (siehe [Clientlibs für Communities-Komponenten](/help/communities/clientlibs.md)).

#### Kommentare zu Clientlibs auf Beispielseite {#comments-clientlibs-on-sample-page}

![comments-clientlibs-crxde](assets/comments-clientlibs-crxde.png)

#### Autor: Alt-Kommentar auf Beispielseite {#author-alt-comment-on-sample-page}

![alt-comment](assets/alt-comment.png)

#### Autor: Beispiel-Seiten-Kommentar-Knoten {#author-sample-page-comments-node}

Sie können den resourceType in CRXDE überprüfen, indem Sie die Eigenschaften des Kommentarknotens für die Beispielseite unter `/content/sites/sample/en/jcr:content/content/primary/comments` anzeigen.

![verify-comment-crxde](assets/verify-comment-crxde.png)

#### Beispielseite für Veröffentlichungen {#publish-sample-page}

Nachdem die benutzerdefinierte Komponente zur Seite hinzugefügt wurde, ist es auch erforderlich, die Seite [zu veröffentlichen](/help/communities/sites-console.md#publishing-the-site).

#### Veröffentlichen: Alt-Kommentar auf Beispielseite {#publish-alt-comment-on-sample-page}

Nach der Veröffentlichung des benutzerdefinierten Programms und der Beispielseite können Sie einen Kommentar eingeben. Nach der Anmeldung mit einem [Demobenutzer](/help/communities/tutorials.md#demo-users) oder Administrator ist es möglich, einen Kommentar zu posten.

Hier aaron.mcdonald@mailinator.com posten Sie einen Kommentar:

![publish-alt-comment](assets/publish-alt-comment.png)

![publish-alt-comment1](assets/publish-alt-comment1.png)

Nachdem sich herausstellt, dass die erweiterte Komponente ordnungsgemäß mit dem standardmäßigen Erscheinungsbild funktioniert, ist es an der Zeit, das Erscheinungsbild zu ändern.
