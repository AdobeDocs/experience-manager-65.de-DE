---
title: Erscheinungsbild ändern
description: Erfahren Sie, wie Sie das Skript comment.hbs bearbeiten, das für die Erstellung der gesamten HTML für jeden Kommentar in Adobe Experience Manager Communities verantwortlich ist.
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

Das Skript `comment.hbs` ist für die Erstellung der gesamten HTML für jeden Kommentar verantwortlich.

So zeigen Sie den Avatar nicht neben jedem veröffentlichten Kommentar an:

1. Kopieren Sie `comment.hbs`von `libs`in `apps`

   1. Klicken Sie auf `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Wählen Sie **[!UICONTROL Kopieren]**
   1. Klicken Sie auf `/apps/social/commons/components/hbs/comments/comment`
   1. Wählen Sie **[!UICONTROL Einfügen]** aus

1. Öffnen Sie die überlagerte `comment.hbs`

   * Doppelklicken Sie auf den Knoten `comment.hbs` in `/apps/social/commons/components/hbs/comments/comment folder`

1. Suchen Sie die folgenden Zeilen und löschen oder kommentieren Sie sie aus:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Löschen Sie entweder die Zeilen oder umschließen Sie sie mit `<!--` und `-->`, damit Sie sie auskommentieren. Außerdem werden die Zeichen &quot;xxx&quot;als visueller Indikator hinzugefügt, wo der Avatar gewesen wäre.

```xml
   xxx
   <!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

### Überlagerung replizieren {#replicate-the-overlay}

Pushen Sie die überlagerte Kommentar-Komponente mithilfe des Replikations-Tools an die Veröffentlichungsinstanz.

>[!NOTE]
>
>Eine zuverlässigere Form der Replikation wäre, ein Paket im Package Manager zu erstellen und es zu [aktivieren](/help/sites-administering/package-manager.md#replicating-packages). Ein Package kann exportiert und archiviert werden.

Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]** aus und klicken Sie auf **[!UICONTROL Tree aktivieren]**.

Geben Sie für den Startpfad &quot;`/apps/social/commons`&quot;ein und wählen Sie &quot;**[!UICONTROL Aktivieren]**&quot;.

![verify-content-template](assets/verify-content-template.png)

### Ergebnisse anzeigen {#view-results}

Wenn Sie sich als Administrator bei der Veröffentlichungsinstanz anmelden, z. B. https://localhost:4503/crx/de als Administrator/Administrator, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden und sich dann als `aaron.mcdonald@mailinator.com/password` anmelden und die Seite aktualisieren, stellen Sie fest, dass ein Avatar nicht mit dem veröffentlichten Kommentar angezeigt wird. Stattdessen wird eine einfache &quot;xxx&quot;angezeigt.

![create-template-component](assets/create-template-component.png)
