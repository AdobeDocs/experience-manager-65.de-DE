---
title: Überlagern von Communities-Komponenten
description: Erfahren Sie, wie Sie eine Standardkomponente überlagern, um das Erscheinungsbild oder Verhalten einer Komponente global für alle relativen Verweise auf die Komponente ändern zu können.
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

Die Absicht [Überlagerung](/help/communities/client-customize.md#overlays) einer Standardkomponente besteht darin, das Erscheinungsbild oder Verhalten einer Komponente global für alle relativen Verweise auf die Komponente zu ändern. Es liegt in der Natur von Sling, den Ordner &quot;/apps“ aufzulösen, bevor im Ordner &quot;/libs“ gesucht wird. Der Pfad zur Komponente entspricht daher dem Pfad zur Standardkomponente, mit der Ausnahme, dass er sich im Ordner &quot;/apps“ und nicht im Ordner &quot;/libs“ befindet.

## Beispiel {#example}

**Komponente „Kommentare überlagern“**

Angenommen, Sie möchten die Kommentarfunktion so ändern, dass sie dem Design Ihrer Website entspricht, indem Sie die Kopfzeile des Kommentars ändern, sodass der Avatar für keinen Kommentar mehr angezeigt wird. Die Lösungen zum Ausblenden des Avatars verwenden entweder CSS oder überlagern, wie hier beschrieben, die Datei header.jsp im Anwendungsordner, sodass die HTML mit dem Avatar nie an den Client gesendet wird.

Um Kommentare zu überlagern, müssen Sie:

1. [Seite „Kommentare erstellen“](/help/communities/overlay-create-comments-page.md)
1. [Erstellen von Knoten](/help/communities/overlay-create-nodes.md)
1. [Erscheinungsbild ändern](/help/communities/overlay-alter-appearance.md)

**Überlagern von Benachrichtigungs-E-Mails**

Angenommen, Sie möchten die Nachricht von E-Mail-Benachrichtigungen anpassen. Sie können dies tun, indem Sie [&#x200B; Vorlagen unter `/libs/settings/community/templates/email/html` &#x200B;](/help/communities/client-customize.md#overlays).

Angenommen, Sie möchten die Erwähnungen und E-Mail-Benachrichtigungen bearbeiten (für eine bestimmte Communities-Komponente, bei der benutzergenerierter Inhalt erstellt wird). Fügen Sie in solchen Fällen eine Wenn **&#x200B;**-Bedingung für **Erwähnung** in den Vorlagen der Komponenten hinzu, für die Sie die **@mentions**-Unterstützung aktiviert haben.

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

Um die Vorlage für E-Mail-Benachrichtigungen zur @mention in Blog-Kommentaren zu ändern, fügen Sie die vordefinierte Vorlage ein unter: `/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en`
