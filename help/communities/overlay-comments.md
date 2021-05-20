---
title: Überlagern von Communities-Komponenten
seo-title: Überlagern von Communities-Komponenten
description: Überlagern von Communities-Komponenten
seo-description: Überlagern von Communities-Komponenten
uuid: 872f7006-959a-49d2-b025-3a5abb7c6dca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 502c0916-6c54-440c-be8c-eae56001fa26
docset: aem65
exl-id: 18376805-c2ed-439a-abc7-e9657afe8baf
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Überlagern von Communities-Komponenten {#overlay-communities-components}

Die Absicht von [Überlagern](/help/communities/client-customize.md#overlays) einer Standardkomponente besteht darin, das Erscheinungsbild oder Verhalten einer Komponente global zu ändern, und zwar für alle relativen Verweise auf die Komponente. Es verlässt sich auf die Art von Sling, um zum Ordner /apps zu gelangen, bevor eine Suche im Ordner /libs durchgeführt wird. Daher ist der Pfad zur Komponente mit dem Pfad zur Standardkomponente identisch, allerdings befindet er sich im Ordner /apps und nicht im Ordner /libs .

## Beispiel {#example}

**Komponente für Überlagerungskommentare**

Angenommen, Sie möchten die Kommentarfunktion so ändern, dass sie mit dem Design Ihrer Website übereinstimmt, indem Sie den Kommentar-Header so ändern, dass er den Avatar nicht mehr für Kommentare anzeigt. Die Lösungen zum Ausblenden des Avatars verwenden entweder CSS oder, wie hier beschrieben, überlagern die Datei &quot;header.jsp&quot;im Apps-Ordner, sodass der HTML-Code, der den Avatar enthält, nie an den Client gesendet wird.

Um Kommentare zu überlagern, müssen Sie:

1. [Kommentarseite](/help/communities/overlay-create-comments-page.md)
1. [Erstellen von Knoten](/help/communities/overlay-create-nodes.md)
1. [Erscheinungsbild ändern](/help/communities/overlay-alter-appearance.md)

**Überlagerungsbenachrichtigungen - E-Mails**

Angenommen, Sie möchten die Nachricht von E-Mail-Benachrichtigungen anpassen, indem Sie [die Vorlagen ](/help/communities/client-customize.md#overlays) unter **/libs/settings/community/templates/email/html** überlagern.

Um beispielsweise die Benachrichtigungs-E-Mail-Erwähnungen zu ändern (für eine bestimmte Communities-Komponente, in der ugc erstellt wird), fügen Sie in den Vorlagen der Komponenten, für die Sie die Unterstützung **@mentions** aktiviert haben, eine **if**-Bedingung für Verb **mention** hinzu.

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

Um die E-Mail-Benachrichtigungsvorlage für @mention in Blogkommentaren zu ändern, müssen Sie die vordefinierte Vorlage unter folgender Adresse einfügen: `/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en`
