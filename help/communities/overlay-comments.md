---
title: Komponenten für Überlagerungsgemeinschaften
seo-title: Komponenten für Überlagerungsgemeinschaften
description: Komponenten für Überlagerungsgemeinschaften
seo-description: Komponenten für Überlagerungsgemeinschaften
uuid: 872f7006-959a-49d2-b025-3a5abb7c6dca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 502c0916-6c54-440c-be8c-eae56001fa26
docset: aem65
translation-type: tm+mt
source-git-commit: 48afa2146d0dcbab4beaa1044645c269b49fd7ff
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Komponenten für Overlay Communities {#overlay-communities-components}

Die Absicht von [overlay](/help/communities/client-customize.md#overlays) einer Standardkomponente besteht darin, das Erscheinungsbild oder Verhalten einer Komponente global für alle relativen Verweise auf die Komponente zu ändern. Es beruht auf der Natur von sling, um in den Ordner /apps aufzulösen, bevor Sie im Ordner /libs suchen. Daher ist der Pfad zur Komponente identisch mit dem Pfad zur Standardkomponente, es sei denn, er befindet sich im Ordner &quot;/apps&quot;und nicht im Ordner &quot;/libs&quot;.

## Beispiel {#example}

**Komponente &quot;Überlagerungskommentare&quot;**

Angenommen, Sie möchten die Kommentarfunktion so ändern, dass sie mit dem Design Ihrer Website übereinstimmt, indem Sie die Kommentarkopfzeile ändern, sodass der Avatar für keinen Kommentar mehr angezeigt wird. Die Lösungen zum Ausblenden des Avatars verwenden entweder CSS oder überlagern, wie hier beschrieben, die Datei header.jsp im Anwendungsordner, damit der HTML-Code, der den Avatar enthält, nie an den Client gesendet wird.

Um Kommentare zu überlagern, müssen Sie:

1. [Kommentarseite](/help/communities/overlay-create-comments-page.md)
1. [Nodes erstellen](/help/communities/overlay-create-nodes.md)
1. [Erscheinungsbild ändern](/help/communities/overlay-alter-appearance.md)

**E-Mails zu Überlagerungsbenachrichtigungen**

Angenommen, Sie möchten die Nachricht von E-Mail-Benachrichtigungen anpassen, indem Sie [die Vorlagen unter **/libs/settings/community/templates/email/html** überlagern.](/help/communities/client-customize.md#overlays)

Um beispielsweise die Benachrichtigungen zu Erwähnungen-E-Mails zu ändern (für eine bestimmte Communities-Komponente, in der ugc erstellt wird), fügen Sie eine **if**-Bedingung für Verb **mentions** in die Vorlagen der Komponenten ein, für die Sie die Unterstützung **@mentions** aktiviert haben.

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

Um die E-Mail-Benachrichtigungsvorlage für &quot;@mension&quot;in Blog-Kommentaren zu ändern, platzieren Sie die Vorlage &quot;Out-of-the-Box&quot; unter: `/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en`
