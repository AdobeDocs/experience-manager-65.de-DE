---
title: Erscheinungsbild ändern
description: Skript ändern
uuid: 30555b9f-da29-4115-9ed5-25f80a247bd6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c9d31ed8-c105-453b-bd3c-4660dfd81272
docset: aem65
exl-id: cb8f6967-216c-46d3-a7ba-068b0f5e3b94
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 1%

---

# Erscheinungsbild ändern {#alter-the-appearance}

## Skript ändern {#modify-the-script}

Das Skript comment.hbs ist für die Erstellung der gesamten HTML für jeden Kommentar verantwortlich.

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

Wählen Sie in der globalen Navigation die Option **[!UICONTROL Instrumente]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Replikation]** und klicken Sie auf **[!UICONTROL Baum aktivieren]**.

Geben Sie für den Startpfad ein. `/apps/social/commons` und wählen Sie **[!UICONTROL Aktivieren]**.

![verify-content-template](assets/verify-content-template.png)

### Ergebnisse anzeigen {#view-results}

Wenn Sie sich als Administrator bei der Veröffentlichungsinstanz anmelden, z. B. https://localhost:4503/crx/de als Administrator/Administrator, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden und sich dann als `aaron.mcdonald@mailinator.com/password` und aktualisieren Sie die Seite, stellen Sie fest, dass ein Avatar nicht mit dem veröffentlichten Kommentar angezeigt wird. Stattdessen wird eine einfache &quot;xxx&quot;angezeigt.

![create-template-component](assets/create-template-component.png)
