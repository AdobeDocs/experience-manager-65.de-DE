---
title: Erscheinungsbild ändern
description: Erfahren Sie, wie Sie das Skript comment.hbs bearbeiten, das für die Erstellung der gesamten HTML für jeden Kommentar in Adobe Experience Manager Communities verantwortlich ist.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: cb8f6967-216c-46d3-a7ba-068b0f5e3b94
source-git-commit: 62d4a8b3af5031ccc539d78f7d06a8cd1fec7af1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 1%

---

# Erscheinungsbild ändern {#alter-the-appearance}

## Skript ändern {#modify-the-script}

Die `comment.hbs` -Skript ist für die Erstellung der gesamten HTML für jeden Kommentar verantwortlich.

So zeigen Sie den Avatar nicht neben jedem veröffentlichten Kommentar an:

1. Kopieren `comment.hbs`von `libs`nach `apps`

   1. Klicken Sie auf `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Klicken Sie auf **[!UICONTROL Kopieren]**
   1. Klicken Sie auf `/apps/social/commons/components/hbs/comments/comment`
   1. Auswählen **[!UICONTROL Einfügen]**

1. Öffnen Sie die überlagerte `comment.hbs`

   * Doppelklick-Knoten `comment.hbs` in `/apps/social/commons/components/hbs/comments/comment folder`

1. Suchen Sie die folgenden Zeilen und löschen oder kommentieren Sie sie aus:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Löschen Sie die Zeilen oder umschließen Sie sie mit `<!--` und `-->` also kommentieren Sie sie aus. Außerdem werden die Zeichen &quot;xxx&quot;als visueller Indikator hinzugefügt, wo der Avatar gewesen wäre.

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
>Eine robustere Form der Replikation wäre, ein Paket in Package Manager zu erstellen und [Aktivieren](/help/sites-administering/package-manager.md#replicating-packages) es. Ein Package kann exportiert und archiviert werden.

Wählen Sie in der globalen Navigation die Option **[!UICONTROL Instrumente]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Replikation]** und klicken **[!UICONTROL Baum aktivieren]**.

Geben Sie für den Startpfad ein. `/apps/social/commons` und wählen **[!UICONTROL Aktivieren]**.

![verify-content-template](assets/verify-content-template.png)

### Ergebnisse anzeigen {#view-results}

Wenn Sie sich als Administrator bei der Veröffentlichungsinstanz anmelden, z. B. https://localhost:4503/crx/de als Administrator/Administrator, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden und sich dann als `aaron.mcdonald@mailinator.com/password` und aktualisieren Sie die Seite, stellen Sie fest, dass ein Avatar nicht mit dem veröffentlichten Kommentar angezeigt wird. Stattdessen wird eine einfache &quot;xxx&quot;angezeigt.

![create-template-component](assets/create-template-component.png)
