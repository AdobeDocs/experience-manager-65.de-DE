---
title: Überlagern von Communities-Komponenten
description: Erfahren Sie, wie Sie eine Standardkomponente überlagern, damit Sie das Erscheinungsbild oder Verhalten einer Komponente global ändern können, und zwar für alle relativen Verweise auf die Komponente.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 18376805-c2ed-439a-abc7-e9657afe8baf
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Überlagern von Communities-Komponenten {#overlay-communities-components}

Die Absicht von [Überlagerung](/help/communities/client-customize.md#overlays) Eine Standardkomponente besteht darin, das Erscheinungsbild oder Verhalten einer Komponente global für alle relativen Verweise auf die Komponente zu ändern. Es verlässt sich auf die Art von Sling, um zum Ordner /apps zu gelangen, bevor eine Suche im Ordner /libs durchgeführt wird. Daher ist der Pfad zur Komponente mit dem Pfad zur Standardkomponente identisch, allerdings befindet er sich im Ordner /apps und nicht im Ordner /libs .

## Beispiel {#example}

**Komponente für Überlagerungskommentare**

Angenommen, Sie möchten die Kommentarfunktion so ändern, dass sie mit dem Design Ihrer Website übereinstimmt, indem Sie den Kommentar-Header so ändern, dass er den Avatar nicht mehr für Kommentare anzeigt. Die Lösungen zum Ausblenden des Avatars verwenden entweder CSS oder, wie hier beschrieben, überlagern die Datei &quot;header.jsp&quot;im Apps-Ordner, sodass die HTML mit dem Avatar nie an den Client gesendet wird.

Um Kommentare zu überlagern, müssen Sie:

1. [Seite &quot;Kommentare erstellen&quot;](/help/communities/overlay-create-comments-page.md)
1. [Erstellen von Knoten](/help/communities/overlay-create-nodes.md)
1. [Erscheinungsbild ändern](/help/communities/overlay-alter-appearance.md)

**Überlagerungsbenachrichtigungen - E-Mails**

Angenommen, Sie möchten die Nachricht von E-Mail-Benachrichtigungen anpassen, können Sie dies tun durch [Überlagerung](/help/communities/client-customize.md#overlays) die Vorlagen unter `/libs/settings/community/templates/email/html`.

Angenommen, Sie möchten die Benachrichtigungsinhalte zu Erwähnungen bearbeiten (für eine bestimmte Communities-Komponente, in der UGC erstellt wird). Fügen Sie in diesem Fall eine **if** Bedingung für Verb **mention** in den Vorlagen der Komponenten, für die Sie die **@mentions** unterstützen.

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

Um die E-Mail-Benachrichtigungsvorlage für @mention in Blogkommentaren zu ändern, müssen Sie die vordefinierte Vorlage unter folgender Adresse einfügen: `/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en`
