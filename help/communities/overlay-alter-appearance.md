---
title: Erscheinungsbild ändern
description: Erfahren Sie, wie Sie das Skript „comment.hbs“ bearbeiten, das für die Erstellung der gesamten HTML für jeden Kommentar in Adobe Experience Manager Communities verantwortlich ist.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: cb8f6967-216c-46d3-a7ba-068b0f5e3b94
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Erscheinungsbild ändern {#alter-the-appearance}

## Skript ändern {#modify-the-script}

Das `comment.hbs` Skript ist für die Erstellung der gesamten HTML für jeden Kommentar verantwortlich.

Um den Avatar nicht neben jedem geposteten Kommentar anzuzeigen:

1. Kopieren `comment.hbs`von `libs`nach `apps`

   1. Klicken Sie auf `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Wählen Sie **[!UICONTROL Kopieren]**
   1. Klicken Sie auf `/apps/social/commons/components/hbs/comments/comment`
   1. Wählen Sie **[!UICONTROL Einfügen]** aus

1. Öffnen der überlagerten `comment.hbs`

   * Doppelklicken Sie auf `comment.hbs` in `/apps/social/commons/components/hbs/comments/comment folder`

1. Suchen Sie die folgenden Zeilen und löschen oder kommentieren Sie sie aus:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Löschen Sie die Zeilen oder umgeben Sie sie mit `<!--` und `-->`, damit Sie sie auskommentieren. Außerdem werden die Zeichen „xxx“ als visueller Indikator dafür hinzugefügt, wo der Avatar gewesen wäre.

```xml
   xxx
   <!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

### Replizieren der Überlagerung {#replicate-the-overlay}

Pushen Sie die Komponente Überlagerte Kommentare mithilfe des Replikations-Tools in die Veröffentlichungsinstanz.

>[!NOTE]
>
>Eine robustere Form der Replikation wäre die Erstellung eines Pakets in Package Manager und [Aktivierung](/help/sites-administering/package-manager.md#replicating-packages). Ein Paket kann exportiert und archiviert werden.

Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]** und klicken Sie auf **[!UICONTROL Tree aktivieren]**.

Geben Sie als Startpfad `/apps/social/commons` ein und wählen Sie **[!UICONTROL Aktivieren]** aus.

![verify-content-template](assets/verify-content-template.png)

### Ergebnisse anzeigen {#view-results}

Wenn Sie sich bei der Veröffentlichungsinstanz als Administrator anmelden, z. B. https://localhost:4503/crx/de als admin/admin, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden und dann als `aaron.mcdonald@mailinator.com/password` anmelden und die Seite aktualisieren, stellen Sie fest, dass mit dem geposteten Kommentar kein Avatar angezeigt wird. Stattdessen wird ein einfaches „xxx“ angezeigt.

![create-template-component](assets/create-template-component.png)
